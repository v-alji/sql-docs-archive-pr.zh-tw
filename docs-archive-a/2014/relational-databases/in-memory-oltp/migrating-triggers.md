---
title: 移轉觸發程序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: ad5385c5-5a50-40ca-a319-97d5606b8511
author: rothja
ms.author: jroth
ms.openlocfilehash: 25965e7cce84b0dcfcd3b6ce6176e8ad3ddabc6a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709446"
---
# <a name="migrating-triggers"></a><span data-ttu-id="ec2ac-102">移轉觸發程序</span><span class="sxs-lookup"><span data-stu-id="ec2ac-102">Migrating Triggers</span></span>
  <span data-ttu-id="ec2ac-103">本主題討論 DDL 和 DML 觸發程序以及記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-103">This topic discusses DDL and DML triggers and memory-optimized tables.</span></span>  
  
 <span data-ttu-id="ec2ac-104">LOGON 觸發程序是定義成發生 LOGON 事件時引發。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-104">LOGON triggers are triggers defined to fire on LOGON events.</span></span> <span data-ttu-id="ec2ac-105">LOGON 觸發程序不會影響記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-105">LOGON triggers do not affect memory-optimized tables.</span></span>  
  
## <a name="ddl-triggers"></a><span data-ttu-id="ec2ac-106">DDL 觸發程序</span><span class="sxs-lookup"><span data-stu-id="ec2ac-106">DDL Triggers</span></span>  
 <span data-ttu-id="ec2ac-107">DDL 觸發程序是定義成對其定義所在的資料庫或伺服器執行 CREATE、ALTER、DROP、GRANT、DENY、REVOKE 或 UPDATE STATISTICS 陳述式時引發的觸發程序。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-107">DDL triggers are triggers defined to fire when a CREATE, ALTER, DROP, GRANT, DENY, REVOKE, or UPDATE STATISTICS statement is executed on the database or server on which it is defined.</span></span>  
  
 <span data-ttu-id="ec2ac-108">如果資料庫或伺服器有一個或多個 DDL 觸發程序定義於 CREATE_TABLE 或包含該等觸發程序的任何事件群組，您便無法建立記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-108">You cannot create memory-optimized tables if the database or server has one or more DDL trigger defined on CREATE_TABLE or any event group that includes it.</span></span> <span data-ttu-id="ec2ac-109">如果資料庫或伺服器有一個或多個 DDL 觸發程序定義於 DROP_TABLE 或包含該等觸發程序的任何事件群組，您便無法卸除記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-109">You cannot drop a memory-optimized table if the database or server has one or more DDL trigger defined on DROP_TABLE or any event group that includes it.</span></span>  
  
 <span data-ttu-id="ec2ac-110">如果有一個或多個 DDL 觸發程序位於 CREATE_PROCEDURE、DROP_PROCEDURE 或包含這些事件的任何事件群組，您便無法建立原生編譯預存程序。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-110">You cannot create natively compiled stored procedures if there are one or more DDL triggers on CREATE_PROCEDURE, DROP_PROCEDURE, or any event group that includes those events.</span></span>  
  
## <a name="dml-triggers"></a><span data-ttu-id="ec2ac-111">DML 觸發程序</span><span class="sxs-lookup"><span data-stu-id="ec2ac-111">DML Triggers</span></span>  
 <span data-ttu-id="ec2ac-112">記憶體最佳化的資料表不能定義 DML 觸發程序。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-112">DML triggers cannot be defined on memory-optimized tables.</span></span> <span data-ttu-id="ec2ac-113">不過，如果您明確地使用預存程序插入、更新或刪除資料，記憶體中的 OLTP 便能讓您達到類似於 DML 觸發程序的效果。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-113">However, In-Memory OLTP allows you to achieve an effect similar to DML triggers if you explicitly use stored procedures to insert, update, or delete data.</span></span> <span data-ttu-id="ec2ac-114">若您的系統包含特定查詢，請將其轉換為改用這些預存程序來模擬 DML 觸發程序的效果。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-114">If your system contains ad-hoc queries, convert them to use these stored procedures instead to simulate the effect of DML triggers.</span></span>  
  
 <span data-ttu-id="ec2ac-115">視觸發程序事件 (FOR/AFTER 或 INSTEAD OF) 而定，您也許可將觸發程序的內容納入到對該資料表執行 INSERT、UPDATE 或 DELETE 的適當預存程序。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-115">Depending on the trigger event (FOR/AFTER or INSTEAD OF), you may include the content of the trigger in the appropriate stored procedure that performs INSERT, UPDATE, or DELETE on that table.</span></span> <span data-ttu-id="ec2ac-116">例如，在移轉 AFTER INSERT 觸發程序時，您可以將此觸發程序的內容納入到適當的 INSERT 陳述式後面，藉此更改執行插入作業的預存程序。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-116">For example, when migrating an AFTER INSERT trigger, you could alter the stored procedure that performs the insert operation by including the content of the trigger after the appropriate INSERT statement.</span></span>  
  
 <span data-ttu-id="ec2ac-117">您可以使用解譯的預存程序或原生編譯預存程序。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-117">You can use an interpreted stored procedure or a natively compiled stored procedure.</span></span> <span data-ttu-id="ec2ac-118">解譯的預存程序中大多數的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 建構皆可對記憶體最佳化的資料表執行。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-118">Most [!INCLUDE[tsql](../../includes/tsql-md.md)] constructs in an interpreted stored procedure can execute on a memory-optimized table.</span></span> <span data-ttu-id="ec2ac-119">不過，原生編譯預存程序僅支援 [!INCLUDE[tsql](../../includes/tsql-md.md)] 建構的子集。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-119">However, only a subset of [!INCLUDE[tsql](../../includes/tsql-md.md)] constructs are supported in natively compiled stored procedures.</span></span> <span data-ttu-id="ec2ac-120">如需 [!INCLUDE[tsql](../../includes/tsql-md.md)] 記憶體優化資料表支援的詳細資訊，請參閱[使用已解讀的 Transact-sql 存取記憶體優化資料表](accessing-memory-optimized-tables-using-interpreted-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-120">For information on [!INCLUDE[tsql](../../includes/tsql-md.md)] support on memory-optimized tables, see [Accessing Memory-Optimized Tables Using Interpreted Transact-SQL](accessing-memory-optimized-tables-using-interpreted-transact-sql.md).</span></span> <span data-ttu-id="ec2ac-121">如需原生 [!INCLUDE[tsql](../../includes/tsql-md.md)] 編譯預存程式中支援的詳細資訊，請參閱[記憶體內部 OLTP 不支援的 transact-sql 結構](transact-sql-constructs-not-supported-by-in-memory-oltp.md)。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-121">For information on [!INCLUDE[tsql](../../includes/tsql-md.md)] support in natively compiled stored procedures, see [Transact-SQL Constructs Not Supported by In-Memory OLTP](transact-sql-constructs-not-supported-by-in-memory-oltp.md).</span></span>  
  
 <span data-ttu-id="ec2ac-122">以下是針對記憶體最佳化的資料表模擬 DML 觸發程序行為的簡單範例。</span><span class="sxs-lookup"><span data-stu-id="ec2ac-122">The following is a simple example of simulating DML trigger behavior on a memory-optimized table.</span></span>  
  
 <span data-ttu-id="ec2ac-123">資料庫包含下列物件，編寫成 CREATE TABLE、CREATE TRIGGER 和 CREATE PROCEDURE 陳述式：</span><span class="sxs-lookup"><span data-stu-id="ec2ac-123">The database contains the following objects, scripted as CREATE TABLE, CREATE TRIGGER, and CREATE PROCEDURE statements:</span></span>  
  
```sql  
CREATE TABLE OrderDetails  
(  
   OrderId int not null primary key,  
   ProductId int not null,  
   SalePrice money not null,  
   Quantity int not null,  
   Total money not null,  
   IsDeleted bit not null DEFAULT (0)  
)  
GO  
  
CREATE TRIGGER tr_order_details_insteadof_insert  
ON OrderDetails  
INSTEAD OF INSERT AS  
BEGIN  
   DECLARE @pid int, @qty_buy int, @qty_remain int  
   SELECT @pid = ProductId, @qty_buy = Quantity FROM inserted  
   SELECT @qty_remain = Quantity FROM Inventory WHERE ProductId = @pid  
   IF (@qty_remain <= @qty_buy)  
      THROW 51000, N'Insufficient inventory!', 1  
   ELSE  
   BEGIN  
      INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)   
      SELECT OrderId, ProductId, SalePrice, Quantity, Total FROM inserted  
      UPDATE Inventory SET Quantity = Quantity - @qty_buy WHERE ProductId = @pid  
   END  
END  
GO  
  
CREATE TRIGGER tr_order_details_after_update  
ON OrderDetails  
AFTER UPDATE AS  
BEGIN  
   INSERT INTO UpdateNotifications (OrderId, UpdateTime) SELECT OrderId, GETDATE() FROM inserted     
END  
GO  
  
CREATE PROCEDURE sp_insert_order_details   
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @total money  
AS BEGIN  
   INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)  
   VALUES (@OrderId, @ProductId, @SalePrice, @Quantity, @total)  
END  
GO  
  
CREATE PROCEDURE sp_update_order_details_by_id  
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @Total money  
AS BEGIN  
   UPDATE dbo.OrderDetails   
   SET ProductId = @ProductId, SalePrice = @SalePrice, Quantity = @Quantity, Total = @total  
   WHERE OrderId = @OrderId  
END  
GO  
```  
  
 <span data-ttu-id="ec2ac-124">下列物件的功能等同於移轉之前的狀態：</span><span class="sxs-lookup"><span data-stu-id="ec2ac-124">The following objects are functionally equivalent to the pre-migration state:</span></span>  
  
```sql  
CREATE TABLE OrderDetails  
(  
   OrderId int not null PRIMARY KEY NONCLUSTERED HASH WITH (BUCKET_COUNT = 1048576),  
   ProductId int not null,  
   SalePrice money not null,  
   Quantity int not null,  
   Total money not null,  
   IsDeleted bit not null DEFAULT (0)  
) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
GO  
  
CREATE TABLE Inventory  
(  
   ProductId int not null PRIMARY KEY NONCLUSTERED,  
   Quantity int not null  
) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
GO  
  
CREATE TABLE UpdateNotifications  
(  
   OrderId int not null,  
   UpdateTime datetime2 not null  
   CONSTRAINT pk_updateNotifications PRIMARY KEY NONCLUSTERED (OrderId, UpdateTime)  
) WITH (MEMORY_OPTIMIZED = ON, DURABILITY = SCHEMA_AND_DATA)  
GO  
  
CREATE PROCEDURE sp_insert_order_details   
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @total money  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'English')  
   DECLARE @qty_remain int  
   SELECT @qty_remain = Quantity FROM dbo.Inventory WHERE ProductId = @ProductId  
   IF (@qty_remain <= @Quantity)  
      THROW 51000, N'Insufficient inventory!', 1  
   ELSE  
   BEGIN  
      INSERT INTO dbo.OrderDetails (OrderId, ProductId, SalePrice, Quantity, Total)   
      VALUES (@OrderId, @ProductId, @SalePrice, @Quantity, @total)  
      UPDATE dbo.Inventory SET Quantity = Quantity - @Quantity WHERE ProductId = @ProductId  
   END  
END  
GO  
  
CREATE PROCEDURE sp_update_order_details_by_id  
   @OrderId int, @ProductId int, @SalePrice money, @Quantity int, @Total money  
WITH NATIVE_COMPILATION, SCHEMABINDING, EXECUTE AS OWNER  
AS BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'English')  
   UPDATE dbo.OrderDetails   
   SET ProductId = @ProductId, SalePrice = @SalePrice, Quantity = @Quantity, Total = @total  
   WHERE OrderId = @OrderId  
   INSERT INTO dbo.UpdateNotifications (OrderId, UpdateTime) VALUES (@OrderId, GETDATE())  
END  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec2ac-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ec2ac-125">See Also</span></span>  
 [<span data-ttu-id="ec2ac-126">移轉至 In-Memory OLTP</span><span class="sxs-lookup"><span data-stu-id="ec2ac-126">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
