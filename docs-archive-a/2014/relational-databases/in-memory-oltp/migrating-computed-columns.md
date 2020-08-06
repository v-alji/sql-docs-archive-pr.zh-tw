---
title: 移轉計算資料行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 64a9eade-22c3-4a9d-ab50-956219e08df1
author: rothja
ms.author: jroth
ms.openlocfilehash: feb50ef64f42d95913ad4e13f9a79e6e0e4ecad3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709457"
---
# <a name="migrating-computed-columns"></a><span data-ttu-id="db5cf-102">移轉計算資料行</span><span class="sxs-lookup"><span data-stu-id="db5cf-102">Migrating Computed Columns</span></span>
  <span data-ttu-id="db5cf-103">記憶體最佳化資料表中不支援計算資料行。</span><span class="sxs-lookup"><span data-stu-id="db5cf-103">Computed columns are not supported in memory-optimized tables.</span></span> <span data-ttu-id="db5cf-104">但是，您可以模擬計算資料行。</span><span class="sxs-lookup"><span data-stu-id="db5cf-104">However, you can simulate a computed column.</span></span>  
  
 <span data-ttu-id="db5cf-105">當您將以磁碟為基礎的資料表移轉至記憶體最佳化資料表時，必須考慮保存計算資料行的需求。</span><span class="sxs-lookup"><span data-stu-id="db5cf-105">You should consider the need to persist your computed columns when you migrate your disk-based tables to memory-optimized tables.</span></span> <span data-ttu-id="db5cf-106">記憶體最佳化資料表和原生編譯預存程序之間的不同效能特性可能會消除保存資料行的需求。</span><span class="sxs-lookup"><span data-stu-id="db5cf-106">The different performance characteristics of memory-optimized tables and natively compiled stored procedures may negate the need for persistence.</span></span>  
  
## <a name="non-persisted-computed-columns"></a><span data-ttu-id="db5cf-107">非保存計算資料行</span><span class="sxs-lookup"><span data-stu-id="db5cf-107">Non-Persisted Computed Columns</span></span>  
 <span data-ttu-id="db5cf-108">若要模擬非保存計算資料行的影響，請在記憶體最佳化的資料表上建立檢視表。</span><span class="sxs-lookup"><span data-stu-id="db5cf-108">To simulate the effects of a non-persisted computed column, create a view on the memory-optimized table.</span></span> <span data-ttu-id="db5cf-109">在定義檢視的 SELECT 陳述式中，將計算資料行定義加入檢視。</span><span class="sxs-lookup"><span data-stu-id="db5cf-109">In the SELECT statement that defines the view, add the computed column definition into the view.</span></span> <span data-ttu-id="db5cf-110">除了在原生編譯預存程序中，使用源自這個計算資料行的值所進行的查詢必須從檢視讀取。</span><span class="sxs-lookup"><span data-stu-id="db5cf-110">Except in a natively compiled stored procedure, queries that use values from the computed column should read from the view.</span></span> <span data-ttu-id="db5cf-111">在原生編譯預存程序中，您應該依據計算資料行的定義更新任何 SELECT、UPDATE 或 DELETE 陳述式。</span><span class="sxs-lookup"><span data-stu-id="db5cf-111">Inside natively compiled stored procedures, you should update any select, update, or delete statement according to your computed column definition.</span></span>  
  
```sql  
-- Schema for the table dbo.OrderDetails:  
-- OrderId int not null primary key,  
-- ProductId int not null,  
-- SalePrice money not null,  
-- Quantity int not null,  
-- Total money not null  
--  
-- Total is computed as SalePrice * Quantity and is not persisted.  
CREATE VIEW dbo.v_order_details AS  
   SELECT  
      OrderId,  
      ProductId,  
      SalePrice,  
      Quantity,  
      Quantity * SalePrice AS Total  
   FROM dbo.order_details  
```  
  
## <a name="persisted-computed-columns"></a><span data-ttu-id="db5cf-112">保存計算資料行</span><span class="sxs-lookup"><span data-stu-id="db5cf-112">Persisted Computed Columns</span></span>  
 <span data-ttu-id="db5cf-113">若要模擬保存計算資料行的影響，請建立預存程序以插入資料表，再建立另一個預存程序以更新資料表。</span><span class="sxs-lookup"><span data-stu-id="db5cf-113">To simulate the effects of a persisted computed column, create a stored procedure for inserting into the table and another stored procedure for updating the table.</span></span> <span data-ttu-id="db5cf-114">在插入或更新資料表時，請叫用這些預存程序以執行這些工作。</span><span class="sxs-lookup"><span data-stu-id="db5cf-114">When inserting or updating the table, invoke these stored procedures to perform these tasks.</span></span> <span data-ttu-id="db5cf-115">在預存程序中，可根據輸入計算位於計算欄位中的值，這與計算資料行在原始以磁碟為基礎之資料表的定義十分類似。</span><span class="sxs-lookup"><span data-stu-id="db5cf-115">Inside the stored procedures, calculate the value for the computed field according to the inputs, much like how the computed column is defined on the original disk-based table.</span></span> <span data-ttu-id="db5cf-116">然後，插入或更新預存程序內所需的資料表。</span><span class="sxs-lookup"><span data-stu-id="db5cf-116">Then, insert or update the table as needed inside the stored procedure.</span></span>  
  
```sql  
-- Schema for the table dbo.OrderDetails:  
-- OrderId int not null primary key,  
-- ProductId int not null,  
-- SalePrice money not null,  
-- Quantity int not null,  
-- Total money not null  
--  
-- Total is computed as SalePrice * Quantity and is persisted.  
-- we need to create insert and update procedures to calculate Total.  
CREATE PROCEDURE sp_insert_order_details   
@OrderId int, @ProductId int, @SalePrice money, @Quantity int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (LANGUAGE = N'english', TRANSACTION ISOLATION LEVEL = SNAPSHOT)  
-- compute the value here.   
-- this stored procedure works with single rows only.  
-- for bulk inserts, accept a table-valued parameter into the stored procedure  
-- and use an INSERT INTO SELECT statement.  
DECLARE @total money = @SalePrice * @Quantity  
INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)  
VALUES (@OrderId, @ProductId, @SalePrice, @Quantity, @total)  
END  
GO  
  
CREATE PROCEDURE sp_update_order_details_by_id  
@OrderId int, @ProductId int, @SalePrice money, @Quantity int  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (LANGUAGE = N'english', TRANSACTION ISOLATION LEVEL = SNAPSHOT)  
-- compute the value here.   
-- this stored procedure works with single rows only.  
DECLARE @total money = @SalePrice * @Quantity  
UPDATE dbo.OrderDetails   
SET ProductId = @ProductId, SalePrice = @SalePrice, Quantity = @Quantity, Total = @total  
WHERE OrderId = @OrderId  
END  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="db5cf-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db5cf-117">See Also</span></span>  
 [<span data-ttu-id="db5cf-118">移轉至 In-Memory OLTP</span><span class="sxs-lookup"><span data-stu-id="db5cf-118">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
