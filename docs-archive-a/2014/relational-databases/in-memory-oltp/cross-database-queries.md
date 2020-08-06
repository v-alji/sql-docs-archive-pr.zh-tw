---
title: 跨資料庫查詢 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a0305f5b-91bd-4d18-a2fc-ec235b062fd3
author: rothja
ms.author: jroth
ms.openlocfilehash: 4afbb580a55273ec241005493fd37f99e98ec0e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593389"
---
# <a name="cross-database-queries"></a><span data-ttu-id="7a7b4-102">跨資料庫查詢</span><span class="sxs-lookup"><span data-stu-id="7a7b4-102">Cross-Database Queries</span></span>
  <span data-ttu-id="7a7b4-103">在 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 中，記憶體最佳化資料表不支援跨資料庫的交易。</span><span class="sxs-lookup"><span data-stu-id="7a7b4-103">In [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)], memory-optimized tables do not support cross-database transactions.</span></span> <span data-ttu-id="7a7b4-104">您無法在同時存取記憶體最佳化資料表的相同交易或相同查詢中存取另一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="7a7b4-104">You cannot access another database from the same transaction or the same query that also accesses a memory-optimized table.</span></span> <span data-ttu-id="7a7b4-105">您無法輕鬆地從某一個資料庫的資料表中，將資料複製到另一個資料庫中的記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="7a7b4-105">You cannot easily copy data from a table in one database, to a memory-optimized table in another database.</span></span>  
  
 <span data-ttu-id="7a7b4-106">資料表變數並非交易式。</span><span class="sxs-lookup"><span data-stu-id="7a7b4-106">Table variables are not transactional.</span></span> <span data-ttu-id="7a7b4-107">因此，記憶體最佳化資料表變數可以在跨資料庫查詢中使用，也因而有助於將某個資料庫中的資料移至另一個資料庫的記憶體最佳化資料表中。</span><span class="sxs-lookup"><span data-stu-id="7a7b4-107">Therefore, memory-optimized table variables can be used in cross-database queries, and can thus facilitate moving data from one database into memory-optimized tables in another.</span></span> <span data-ttu-id="7a7b4-108">您可以使用兩筆交易。</span><span class="sxs-lookup"><span data-stu-id="7a7b4-108">You can use two transactions.</span></span> <span data-ttu-id="7a7b4-109">在第一筆交易中，將資料從遠端資料表插入變數中。</span><span class="sxs-lookup"><span data-stu-id="7a7b4-109">In the first transaction, insert the data from the remote table into the variable.</span></span> <span data-ttu-id="7a7b4-110">在第二筆交易中，從變數中將資料插入本機記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="7a7b4-110">In the second transaction, insert the data into the local memory-optimized table from the variable.</span></span>  
  
 <span data-ttu-id="7a7b4-111">例如，若要從資料庫 db1 中的資料表 t1，將資料列複製到 db2 中的資料表 t2，請使用 @v1 tt1 類型的變數，您可以使用類似下列的專案：</span><span class="sxs-lookup"><span data-stu-id="7a7b4-111">For example, to copy the row from table t1 in database db1 to table t2 in db2, using variable @v1 of type dbo.tt1, you can use something like:</span></span>  
  
```sql  
USE db2   
GO   
DECLARE @v1 dbo.tt1   
INSERT @v1 SELECT * FROM db1.dbo.t1   
INSERT dbo.t2 SELECT * FROM @v1   
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="7a7b4-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a7b4-112">See Also</span></span>  
 [<span data-ttu-id="7a7b4-113">移轉至 In-Memory OLTP</span><span class="sxs-lookup"><span data-stu-id="7a7b4-113">Migrating to In-Memory OLTP</span></span>](migrating-to-in-memory-oltp.md)  
  
  
