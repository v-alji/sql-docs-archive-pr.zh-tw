---
title: 瞭解記憶體優化資料表上的交易 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 06075248-705e-4563-9371-b64cd609793c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0671bba8b7a0bda27ea27cf059cb9e3b1bb87b2b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701524"
---
# <a name="understanding-transactions-on-memory-optimized-tables"></a><span data-ttu-id="51347-102">了解記憶體最佳化資料表上的交易</span><span class="sxs-lookup"><span data-stu-id="51347-102">Understanding Transactions on Memory-Optimized Tables</span></span>
  <span data-ttu-id="51347-103">交易會使用一種開放式多重版本並行控制的形式，存取記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="51347-103">Transactions access memory-optimized tables using a form of optimistic, multi-version concurrency control.</span></span> <span data-ttu-id="51347-104">這表示有不同版本的資料。</span><span class="sxs-lookup"><span data-stu-id="51347-104">This means that there are different versions of the data.</span></span> <span data-ttu-id="51347-105">每一筆交易都會在它自己的交易一致性資料庫版本上運作，與其他並行執行的交易無關。</span><span class="sxs-lookup"><span data-stu-id="51347-105">Each transaction operates on its own transactionally consistent version of the database, independent from other concurrently running transactions.</span></span> <span data-ttu-id="51347-106">此外，交易會在開放式假設下運作，並不會與其他並行交易發生衝突。</span><span class="sxs-lookup"><span data-stu-id="51347-106">In addition, transactions operate under the optimistic assumption that there will be no conflicts with other, concurrent, transactions.</span></span> <span data-ttu-id="51347-107">如此就不需要使用鎖定，不過需要系統偵測衝突，並終止其中一個衝突的交易。</span><span class="sxs-lookup"><span data-stu-id="51347-107">This avoids the need to use locks, but does require the system to detect conflicts and terminate one of the conflicting transactions.</span></span> <span data-ttu-id="51347-108">只有寫入-寫入交易和讀取-寫入交易會發生衝突。</span><span class="sxs-lookup"><span data-stu-id="51347-108">Conflicts can occur only for write-write transactions and for read-write transactions.</span></span> <span data-ttu-id="51347-109">如果發生寫入-寫入衝突，其中一個寫入交易會終止。</span><span class="sxs-lookup"><span data-stu-id="51347-109">If there is a write-write conflict, one write transaction is terminated.</span></span>  
  
 <span data-ttu-id="51347-110">就 READ_COMMITTED_SNAPSHOT 和 SNAPSHOT 交易隔離等級而言，記憶體最佳化資料表的並行存取控制與以磁碟為基礎的資料表的並行存取控制之間有相似之處。</span><span class="sxs-lookup"><span data-stu-id="51347-110">There are similarities between the concurrency control for memory-optimized tables and the concurrency control for disk-based tables for the READ_COMMITTED_SNAPSHOT and SNAPSHOT transaction isolation levels.</span></span> <span data-ttu-id="51347-111"> (需以磁片為基礎之資料表的詳細資訊，請參閱[資料庫引擎中以資料列版本設定為基礎的隔離等級](https://msdn.microsoft.com/library/ms177404\(v=sql.100\).aspx)。 ) </span><span class="sxs-lookup"><span data-stu-id="51347-111">(For more information about disk-based tables, see [Row Versioning-based Isolation Levels in the Database Engine](https://msdn.microsoft.com/library/ms177404\(v=sql.100\).aspx).)</span></span>  
  
## <a name="topics-in-this-section"></a><span data-ttu-id="51347-112">本節主題</span><span class="sxs-lookup"><span data-stu-id="51347-112">Topics in This Section</span></span>  
 <span data-ttu-id="51347-113">本節中有關記憶體最佳化資料表交易的說明，涵蓋下列主題：</span><span class="sxs-lookup"><span data-stu-id="51347-113">This section on transactions in memory-optimized tables includes the following topics:</span></span>  
  
-   [<span data-ttu-id="51347-114">搭配記憶體最佳化的資料表使用交易隔離等級的方針</span><span class="sxs-lookup"><span data-stu-id="51347-114">Guidelines for Transaction Isolation Levels with Memory-Optimized Tables</span></span>](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
-   [<span data-ttu-id="51347-115">記憶體最佳化資料表交易的重試邏輯方針</span><span class="sxs-lookup"><span data-stu-id="51347-115">Guidelines for Retry Logic for Transactions on Memory-Optimized Tables</span></span>](guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)  
  
-   [<span data-ttu-id="51347-116">經記憶體最佳化的資料表中的交易</span><span class="sxs-lookup"><span data-stu-id="51347-116">Transactions in Memory-Optimized Tables</span></span>](transactions-in-memory-optimized-tables.md)  
  
-   [<span data-ttu-id="51347-117">交易隔離等級</span><span class="sxs-lookup"><span data-stu-id="51347-117">Transaction Isolation Levels</span></span>](transaction-isolation-levels.md)  
  
-   [<span data-ttu-id="51347-118">跨容器交易</span><span class="sxs-lookup"><span data-stu-id="51347-118">Cross-Container Transactions</span></span>](cross-container-transactions.md)  
  
 <span data-ttu-id="51347-119">如需詳細資訊，請參閱[控制交易持久性](../relational-databases/logs/control-transaction-durability.md)。</span><span class="sxs-lookup"><span data-stu-id="51347-119">For more information, see [Control Transaction Durability](../relational-databases/logs/control-transaction-durability.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51347-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51347-120">See Also</span></span>  
 [<span data-ttu-id="51347-121">記憶體最佳化資料表</span><span class="sxs-lookup"><span data-stu-id="51347-121">Memory-Optimized Tables</span></span>](../relational-databases/in-memory-oltp/memory-optimized-tables.md)  
  
  
