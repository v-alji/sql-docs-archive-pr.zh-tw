---
title: 具有記憶體優化資料表的交易隔離等級方針 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e365e9ca-c34b-44ae-840c-10e599fa614f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 834c5950a8f8b0ddf8854d06c6fb1073a264fc22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701566"
---
# <a name="guidelines-for-transaction-isolation-levels-with-memory-optimized-tables"></a><span data-ttu-id="8a096-102">搭配記憶體最佳化的資料表使用交易隔離等級的方針</span><span class="sxs-lookup"><span data-stu-id="8a096-102">Guidelines for Transaction Isolation Levels with Memory-Optimized Tables</span></span>
  <span data-ttu-id="8a096-103">在許多情況下，您必須指定交易隔離等級。</span><span class="sxs-lookup"><span data-stu-id="8a096-103">In many scenarios, you must specify the transaction isolation level.</span></span> <span data-ttu-id="8a096-104">記憶體最佳化資料表的交易隔離不同於磁碟基礎的資料表。</span><span class="sxs-lookup"><span data-stu-id="8a096-104">Transaction isolation for memory-optimized tables differs from disk-based tables.</span></span>  
  
 <span data-ttu-id="8a096-105">指定交易隔離等級的需求：</span><span class="sxs-lookup"><span data-stu-id="8a096-105">Requirements for specifying transaction isolation level:</span></span>  
  
-   <span data-ttu-id="8a096-106">TRANSACTION ISOLATION LEVEL 是包含原生編譯預存程序內容之 ATOMIC 區塊的必要選項。</span><span class="sxs-lookup"><span data-stu-id="8a096-106">TRANSACTION ISOLATION LEVEL is a required option for the ATOMIC block comprising the content of a natively compiled stored procedure.</span></span>  
  
-   <span data-ttu-id="8a096-107">由於隔離等級在跨容器交易的使用限制，解譯的 [!INCLUDE[tsql](../includes/tsql-md.md)] 中記憶體最佳化資料表的使用，通常必須伴隨著資料表提示，指定用來存取資料表之隔離等級。</span><span class="sxs-lookup"><span data-stu-id="8a096-107">Because of restrictions on isolation level use in cross-container transactions, uses of memory-optimized tables in interpreted [!INCLUDE[tsql](../includes/tsql-md.md)] must often be accompanied by a table hint specifying the isolation level used to access the table.</span></span> <span data-ttu-id="8a096-108">如需隔離等級提示和跨容器交易的詳細資訊，請參閱[交易隔離等級](../../2014/database-engine/transaction-isolation-levels.md)。</span><span class="sxs-lookup"><span data-stu-id="8a096-108">For more information about isolation level hints and cross-container transactions, see [Transaction Isolation Levels](../../2014/database-engine/transaction-isolation-levels.md).</span></span>  
  
-   <span data-ttu-id="8a096-109">所需的交易隔離等級必須明確宣告。</span><span class="sxs-lookup"><span data-stu-id="8a096-109">The desired transaction isolation level must be explicitly declared.</span></span> <span data-ttu-id="8a096-110">無法使用鎖定提示 (例如 XLOCK) 來保證交易中某些資料列或資料表的隔離。</span><span class="sxs-lookup"><span data-stu-id="8a096-110">It is not possible to use locking hints (such as XLOCK) to guarantee the isolation of certain rows or tables in the transaction.</span></span>  
  
-   <span data-ttu-id="8a096-111">存取資料庫的應用程式應該實作重試邏輯，以處理毀滅交易之衝突、驗證失敗和認可相依性失敗所產生的錯誤。</span><span class="sxs-lookup"><span data-stu-id="8a096-111">The application accessing the database should implement retry logic to deal with errors resulting from transaction-dooming conflicts, validation failures, and commit-dependency failures.</span></span> <span data-ttu-id="8a096-112">請注意，即使是唯讀交易也會發生認可相依性失敗。</span><span class="sxs-lookup"><span data-stu-id="8a096-112">Note that commit dependency failures can occur even with read-only transactions.</span></span>  
  
-   <span data-ttu-id="8a096-113">記憶體最佳化的資料表應該避免長時間執行的交易。</span><span class="sxs-lookup"><span data-stu-id="8a096-113">Long-running transactions should be avoided with memory-optimized tables.</span></span> <span data-ttu-id="8a096-114">這類交易會增加衝突及後續交易終止的可能性。</span><span class="sxs-lookup"><span data-stu-id="8a096-114">Such transactions increase the likelihood of conflicts and subsequent transaction terminations.</span></span> <span data-ttu-id="8a096-115">長時間執行的交易也可能會延緩記憶體回收。</span><span class="sxs-lookup"><span data-stu-id="8a096-115">A long-running transaction also defers garbage collection.</span></span> <span data-ttu-id="8a096-116">交易執行的時間愈久，記憶體中 OLTP 就會將最近刪除的資料列版本保留得愈久，這會減少新交易的查閱效能。</span><span class="sxs-lookup"><span data-stu-id="8a096-116">The longer a transaction runs, the longer In-Memory OLTP keeps recently deleted row versions, which can decrease lookup performance for new transactions.</span></span>  
  
 <span data-ttu-id="8a096-117">磁碟基礎的資料表通常依賴鎖定及封鎖進行交易隔離。</span><span class="sxs-lookup"><span data-stu-id="8a096-117">Disk-based tables typically rely on locking and blocking for transaction isolation.</span></span> <span data-ttu-id="8a096-118">記憶體最佳化的資料表依賴多重版本設定和衝突偵測以保證隔離。</span><span class="sxs-lookup"><span data-stu-id="8a096-118">Memory-optimized tables rely on multi-versioning and conflict detection to guarantee isolation.</span></span> <span data-ttu-id="8a096-119">如需詳細資訊，請參閱[記憶體優化資料表中交易](../relational-databases/in-memory-oltp/memory-optimized-tables.md)的衝突偵測、驗證和認可相依性檢查一節。</span><span class="sxs-lookup"><span data-stu-id="8a096-119">For details, see the section on Conflict Detection, Validation, and Commit Dependency Checks in [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="8a096-120">磁碟基礎的資料表允許多重版本設定與隔離等級 SNAPSHOT 和 READ_COMMITTED_SNAPSHOT。</span><span class="sxs-lookup"><span data-stu-id="8a096-120">Disk-based tables do allow multi-versioning with the isolation levels SNAPSHOT and READ_COMMITTED_SNAPSHOT.</span></span> <span data-ttu-id="8a096-121">對於記憶體最佳化的資料表，所有隔離等級都是根據多個版本，包括 REPEATABLE READ 和 SERIALIZABLE。</span><span class="sxs-lookup"><span data-stu-id="8a096-121">For memory-optimized tables all isolation levels are multi-version based, including REPEATABLE READ and SERIALIZABLE.</span></span>  
  
## <a name="types-of-transactions"></a><span data-ttu-id="8a096-122">交易的類型</span><span class="sxs-lookup"><span data-stu-id="8a096-122">Types of Transactions</span></span>  
 <span data-ttu-id="8a096-123">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的每一個查詢都是在交易的內容中執行。</span><span class="sxs-lookup"><span data-stu-id="8a096-123">Every query in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] runs in the context of a transaction.</span></span>  
  
 <span data-ttu-id="8a096-124">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的交易有三種類型：</span><span class="sxs-lookup"><span data-stu-id="8a096-124">There are three types of transactions in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]:</span></span>  
  
-   <span data-ttu-id="8a096-125">自動認可交易：</span><span class="sxs-lookup"><span data-stu-id="8a096-125">Autocommit transactions.</span></span> <span data-ttu-id="8a096-126">如果沒有使用中交易內容，而且在工作階段中隱含交易未設為 ON，每個查詢都有自己的交易內容。</span><span class="sxs-lookup"><span data-stu-id="8a096-126">If there is no active transaction context and implicit transactions are not set to ON in the session, each query has its own transaction context.</span></span> <span data-ttu-id="8a096-127">交易在陳述式開始執行時開始，在陳述式完成時完成。</span><span class="sxs-lookup"><span data-stu-id="8a096-127">The transaction starts when the statement starts execution, and completes when the statement finishes.</span></span>  
  
-   <span data-ttu-id="8a096-128">明確交易：</span><span class="sxs-lookup"><span data-stu-id="8a096-128">Explicit transactions.</span></span> <span data-ttu-id="8a096-129">使用者透過明確 BEGIN TRAN 或 BEGIN ATOMIC 啟動交易。</span><span class="sxs-lookup"><span data-stu-id="8a096-129">The user starts the transaction through an explicit BEGIN TRAN or BEGIN ATOMIC.</span></span> <span data-ttu-id="8a096-130">交易在對應 COMMIT 和 ROLLBACK 或 END 之後完成 (在 ATOMIC 區塊的情況下)。</span><span class="sxs-lookup"><span data-stu-id="8a096-130">The transaction is completed following the corresponding COMMIT and ROLLBACK or END (in the case of an atomic block).</span></span>  
  
-   <span data-ttu-id="8a096-131">隱含交易：</span><span class="sxs-lookup"><span data-stu-id="8a096-131">Implicit transactions.</span></span> <span data-ttu-id="8a096-132">當 IMPLICIT_TRANSACTIONS 選項設為 ON 時，只要使用者執行陳述式，而且沒有使用中交易內容時，交易就會隱含啟動。</span><span class="sxs-lookup"><span data-stu-id="8a096-132">When the option IMPLICIT_TRANSACTIONS is set to ON, a transaction is started implicitly whenever the user executes a statement and there is no active transaction context.</span></span> <span data-ttu-id="8a096-133">交易是透過明確 COMMIT 和 ROLLBACK 完成的。</span><span class="sxs-lookup"><span data-stu-id="8a096-133">The transaction is completed through an explicit COMMIT and ROLLBACK.</span></span>  
  
## <a name="baseline-read-committed-isolation"></a><span data-ttu-id="8a096-134">基準 READ COMMITTED 隔離</span><span class="sxs-lookup"><span data-stu-id="8a096-134">Baseline READ COMMITTED Isolation</span></span>  
 <span data-ttu-id="8a096-135">READ COMMITTED 是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的預設隔離等級。</span><span class="sxs-lookup"><span data-stu-id="8a096-135">READ COMMITTED is the default isolation level in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="8a096-136">READ COMMITTED 隔離等級可確保交易無視於在目前交易之外變更的任何未認可的資料。</span><span class="sxs-lookup"><span data-stu-id="8a096-136">The isolation level READ COMMITTED guarantees that transactions do not see any uncommitted data from changes outside the current transaction.</span></span> <span data-ttu-id="8a096-137">換句話說，交易只會讀取資料庫已經認可的資料，或是由目前交易所變更的資料。</span><span class="sxs-lookup"><span data-stu-id="8a096-137">In other words, the transaction only reads data which has either been committed to the database, or has been changed by the current transaction.</span></span>  
  
 <span data-ttu-id="8a096-138">記憶體最佳化的資料表支援的所有隔離等級都提供讀取認可保證。</span><span class="sxs-lookup"><span data-stu-id="8a096-138">All isolation levels supported for memory-optimized tables provide the read committed guarantee.</span></span> <span data-ttu-id="8a096-139">因此，如果交易不需要更強大的保證，您可以使用記憶體最佳化資料表支援的任何隔離等級。</span><span class="sxs-lookup"><span data-stu-id="8a096-139">Therefore, if the transaction does not require stronger guarantees, you can use any of the isolation levels supported for memory-optimized tables.</span></span> <span data-ttu-id="8a096-140">相較於其他隔離等級，SNAPSHOT 使用最少的系統資源。</span><span class="sxs-lookup"><span data-stu-id="8a096-140">SNAPSHOT uses the fewest system resources, compared to other isolation levels.</span></span>  
  
 <span data-ttu-id="8a096-141">SNAPSHOT 隔離等級提供的保證 (記憶體最佳化資料表支援的最低隔離等級) 包含 READ COMMITTED 保證。</span><span class="sxs-lookup"><span data-stu-id="8a096-141">The guarantee provided by the SNAPSHOT isolation level (the lowest level of isolation supported for memory-optimized tables) includes the guarantees of READ COMMITTED.</span></span> <span data-ttu-id="8a096-142">交易中的每個陳述式都會讀取資料庫的相同一致版本。</span><span class="sxs-lookup"><span data-stu-id="8a096-142">Every statement in the transaction reads the same, consistent version of the database.</span></span> <span data-ttu-id="8a096-143">不只是交易所讀取的所有資料列都會認可至資料庫，所有讀取作業也會看到同一組交易所做的同一組變更。</span><span class="sxs-lookup"><span data-stu-id="8a096-143">Not only are all the rows read by the transaction committed to the database, also all the read operations see the set of changes made by the same set of transactions.</span></span>  
  
 <span data-ttu-id="8a096-144">**指導**方針：如果只需要讀取認可的隔離保證，請搭配原生編譯的預存程式使用快照集隔離，並透過解讀來存取記憶體優化的資料表 [!INCLUDE[tsql](../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8a096-144">**Guideline**: If only the READ COMMITTED isolation guarantee is required, use SNAPSHOT isolation with natively compiled stored procedures and for accessing memory-optimized tables through interpreted [!INCLUDE[tsql](../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="8a096-145">對於自動認可交易，READ COMMITTED 隔離等級隱含對應到記憶體最佳化資料表的 SNAPSHOT 隔離。</span><span class="sxs-lookup"><span data-stu-id="8a096-145">For autocommit transactions, the isolation level READ COMMITTED is implicitly mapped to SNAPSHOT for memory-optimized tables.</span></span> <span data-ttu-id="8a096-146">因此，如果 TRANSACTION ISOLATION LEVEL 工作階段設定為 READ COMMITTED，當存取記憶體最佳化的資料表時，不需要透過資料表提示指定隔離等級。</span><span class="sxs-lookup"><span data-stu-id="8a096-146">Therefore, if the TRANSACTION ISOLATION LEVEL session setting is set to READ COMMITTED, it is not necessary to specify the isolation level through a table hint when accessing memory-optimized tables.</span></span>  
  
 <span data-ttu-id="8a096-147">下列自動認可交易範例示範記憶體最佳化資料表 Customers 和正規資料表 [Order History] 之間的聯結，當做特定批次的一部分：</span><span class="sxs-lookup"><span data-stu-id="8a096-147">The following autocommit transaction example shows a join between a memory-optimized table Customers and a regular table [Order History], as part of an ad hoc batch:</span></span>  
  
```sql  
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;  
GO  
SELECT *   
FROM dbo.Customers AS c   
LEFT JOIN dbo.[Order History] AS oh   
    ON c.customer_id = oh.customer_id;  
```  
  
 <span data-ttu-id="8a096-148">下列明確或隱含交易範例示範相同聯結，但是這次是在明確的使用者交易中。</span><span class="sxs-lookup"><span data-stu-id="8a096-148">The following explicit or implicit transactions example shows the same join, but this time in an explicit user transaction.</span></span> <span data-ttu-id="8a096-149">記憶體最佳化的資料表 Customers 是在快照隔離下存取，透過資料表提示 WITH (SNAPSHOT) 所指示，而正規資料表 [Order History] 則是在讀取認可隔離下存取：</span><span class="sxs-lookup"><span data-stu-id="8a096-149">The memory-optimized table Customers is accessed under snapshot isolation, as indicated through the table hint WITH (SNAPSHOT), and the regular table [Order History] is accessed under read committed isolation:</span></span>  
  
```sql  
SET TRANSACTION ISOLATION LEVEL READ COMMITTED  
GO  
BEGIN TRAN  
SELECT * FROM dbo.Customers c with (SNAPSHOT)   
LEFT JOIN dbo.[Order History] oh   
    ON c.customer_id=oh.customer_id  
...  
COMMIT  
```  
  
### <a name="operational-differences"></a><span data-ttu-id="8a096-150">操作差異</span><span class="sxs-lookup"><span data-stu-id="8a096-150">Operational Differences</span></span>  
 <span data-ttu-id="8a096-151">除了讀取認可保證以外，使用磁碟基礎之資料表的應用程式可能還依賴兩個重要實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="8a096-151">Besides the read committed guarantee, there are also two key implementation details that applications using disk-based tables may rely on.</span></span> <span data-ttu-id="8a096-152">將磁碟基礎的資料表 (使用 READ COMMITTED 隔離進行存取) 轉換為記憶體最佳化的資料表 (使用 SNAPSHOT 隔離進行存取) 時，請注意下列事項：</span><span class="sxs-lookup"><span data-stu-id="8a096-152">Be aware of the following when converting a disk-based table that is accessed using READ COMMITTED isolation to a memory-optimized table that is accessed using SNAPSHOT isolation:</span></span>  
  
-   <span data-ttu-id="8a096-153">磁碟基礎之資料表的 READ COMMITTED 隔離等級實作 (假設 READ_COMMITTED_SNAPSHOT 為 OFF) 使用鎖定來防止讀取器和寫入器之間的衝突。</span><span class="sxs-lookup"><span data-stu-id="8a096-153">The implementation of the READ COMMITTED isolation level for disk-based tables (assuming READ_COMMITTED_SNAPSHOT is OFF) uses locks to prevent conflicts between readers and writers.</span></span> <span data-ttu-id="8a096-154">當寫入器開始更新資料列時，它會取得鎖定，直到交易認可時才釋放鎖定。</span><span class="sxs-lookup"><span data-stu-id="8a096-154">When a writer starts updating a row, it takes a lock and does not release the lock until the transaction is committed.</span></span> <span data-ttu-id="8a096-155">任何讀取作業都會被封鎖，並等待寫入交易認可。</span><span class="sxs-lookup"><span data-stu-id="8a096-155">Any read operations are blocked and will wait for the write transaction to commit.</span></span>  
  
     <span data-ttu-id="8a096-156">有些應用程式可能會假設讀取器一定會等候寫入器認可，特別是在應用程式層中兩筆交易之間有任何同步處理時。</span><span class="sxs-lookup"><span data-stu-id="8a096-156">Some applications may assume readers always wait for writers to commit, particularly if there is any synchronization between the two transactions in the application tier.</span></span>  
  
     <span data-ttu-id="8a096-157">**指導方針：** 應用程式不能依賴封鎖行為。</span><span class="sxs-lookup"><span data-stu-id="8a096-157">**Guideline:** Applications cannot rely on blocking behavior.</span></span> <span data-ttu-id="8a096-158">如果應用程式需要在並行交易之間進行同步處理，則可以透過[sp_getapplock &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-getapplock-transact-sql)，在應用層或資料庫層中執行這類邏輯。</span><span class="sxs-lookup"><span data-stu-id="8a096-158">If an application needs synchronization between concurrent transactions, such logic can be implemented in the application tier or in the database tier, through [sp_getapplock &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getapplock-transact-sql).</span></span>  
  
-   <span data-ttu-id="8a096-159">在使用 READ COMMITTED 隔離的交易，每個陳述式都會看到資料庫中最新版本的資料列。</span><span class="sxs-lookup"><span data-stu-id="8a096-159">In transactions that use READ COMMITTED isolation, each statement sees the most recent version of the rows in the database.</span></span> <span data-ttu-id="8a096-160">因此，後續陳述式會看到資料庫狀態變更。</span><span class="sxs-lookup"><span data-stu-id="8a096-160">Therefore, subsequent statements see changes in the state of the database.</span></span>  
  
     <span data-ttu-id="8a096-161">使用 WHILE 迴圈輪詢資料表，直到找到新資料列為止，就是使用這個假設的應用程式模式範例。</span><span class="sxs-lookup"><span data-stu-id="8a096-161">Polling a table using a WHILE loop until a new row has been found is an example of an application pattern that uses this assumption.</span></span> <span data-ttu-id="8a096-162">在迴圈的每個反覆運算，查詢會看到資料庫的最新更新。</span><span class="sxs-lookup"><span data-stu-id="8a096-162">With each iteration of the loop, the query will see the latest updates in the database.</span></span>  
  
     <span data-ttu-id="8a096-163">**指導方針：** 如果應用程式需要輪詢記憶體優化資料表，以取得寫入資料表的最新資料列，請將輪詢迴圈移至交易範圍外。</span><span class="sxs-lookup"><span data-stu-id="8a096-163">**Guideline:** If an application needs to poll a memory-optimized table to obtain the most recent rows written to the table, move the polling loop outside the scope of the transaction.</span></span>  
  
     <span data-ttu-id="8a096-164">下列是使用這個假設的範例應用程式模式。</span><span class="sxs-lookup"><span data-stu-id="8a096-164">The following is an example application pattern that uses this assumption.</span></span> <span data-ttu-id="8a096-165">使用 WHILE 迴圈輪詢資料表，直到找到新資料列為止。</span><span class="sxs-lookup"><span data-stu-id="8a096-165">Polling a table using a WHILE loop until a new row is found.</span></span> <span data-ttu-id="8a096-166">在每個迴圈反覆運算，查詢會存取資料庫的最新更新。</span><span class="sxs-lookup"><span data-stu-id="8a096-166">In each loop iteration, the query will access the latest updates in the database.</span></span>  
  
 <span data-ttu-id="8a096-167">下列範例指令碼會輪詢資料表 t1，直到它具有資料列。</span><span class="sxs-lookup"><span data-stu-id="8a096-167">The following example script polls a table t1 until it has a row.</span></span> <span data-ttu-id="8a096-168">接著從資料表移除單一資料列，進一步處理。</span><span class="sxs-lookup"><span data-stu-id="8a096-168">It then removes a single row from the table for further processing.</span></span>  
  
 <span data-ttu-id="8a096-169">請注意，輪詢邏輯必須在交易範圍之外，因為它使用快照隔離來存取資料表 t1。</span><span class="sxs-lookup"><span data-stu-id="8a096-169">Notice that the polling logic needs to be outside the scope of the transaction, as it is using snapshot isolation to access table t1.</span></span> <span data-ttu-id="8a096-170">在交易範圍內使用輪詢邏輯，會建立長時間執行的交易，這是不良作法。</span><span class="sxs-lookup"><span data-stu-id="8a096-170">Using polling logic inside the scope of a transaction would create a long-running transaction, which is a bad practice.</span></span>  
  
```sql  
-- poll table  
WHILE NOT EXISTS (SELECT 1 FROM dbo.t1)  
BEGIN   
  -- if empty, wait and poll again  
  WAITFOR DELAY '00:00:01'  
END  
  
BEGIN TRANSACTION  
  DECLARE @id int  
  SELECT TOP 1 @id=id FROM dbo.t1 WITH (SNAPSHOT)  
  DELETE FROM dbo.t1 WITH (SNAPSHOT) WHERE id=@id  
  
  -- insert processing based on @id  
COMMIT  
```  
  
## <a name="locking-table-hints"></a><span data-ttu-id="8a096-171">鎖定資料表提示</span><span class="sxs-lookup"><span data-stu-id="8a096-171">Locking Table Hints</span></span>  
 <span data-ttu-id="8a096-172">鎖定提示 ([資料表提示 &#40;transact-sql&#41;](/sql/t-sql/queries/hints-transact-sql-table)) （例如 HOLDLOCK 和 XLOCK）可與磁片資料表搭配使用，以 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 取得比所指定隔離等級所需更多的鎖定。</span><span class="sxs-lookup"><span data-stu-id="8a096-172">Locking hints ([Table Hints &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)) such as HOLDLOCK and XLOCK can be used with disk-based tables to have [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] take more locks than are required for the specified isolation level.</span></span>  
  
 <span data-ttu-id="8a096-173">記憶體最佳化的資料表不使用鎖定。</span><span class="sxs-lookup"><span data-stu-id="8a096-173">Memory-optimized tables do not use locks.</span></span> <span data-ttu-id="8a096-174">可使用較高的隔離等級，例如 REPEATABLE READ 和 SERIALIZABLE，來宣告所需的保證。</span><span class="sxs-lookup"><span data-stu-id="8a096-174">Higher isolation levels such as REPEATABLE READ and SERIALIZABLE can be used to declare the desired guarantees.</span></span>  
  
 <span data-ttu-id="8a096-175">不支援鎖定提示。</span><span class="sxs-lookup"><span data-stu-id="8a096-175">Locking hints are not supported.</span></span> <span data-ttu-id="8a096-176">請改為透過交易隔離等級宣告所需的保證。</span><span class="sxs-lookup"><span data-stu-id="8a096-176">Instead, declare the required guarantees through the transaction isolation levels.</span></span> <span data-ttu-id="8a096-177">(支援 NOLOCK，因為 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 沒有在記憶體最佳化的資料表上鎖定。</span><span class="sxs-lookup"><span data-stu-id="8a096-177">(NOLOCK is supported because [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] does not take locks on memory-optimized tables.</span></span> <span data-ttu-id="8a096-178">請注意，與磁碟基礎的資料表相反，NOLOCK 不表示記憶體最佳化資料表的 READ UNCOMMITTED 行為)。</span><span class="sxs-lookup"><span data-stu-id="8a096-178">Note that, in contrast to disk-based tables, NOLOCK does not imply READ UNCOMMITTED behavior for memory-optimized tables.)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a096-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8a096-179">See Also</span></span>  
 <span data-ttu-id="8a096-180">[瞭解記憶體優化資料表上的交易](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="8a096-180">[Understanding Transactions on Memory-Optimized Tables](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="8a096-181">[記憶體優化資料表上交易的重試邏輯指導方針](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="8a096-181">[Guidelines for Retry Logic for Transactions on Memory-Optimized Tables](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="8a096-182">交易隔離等級</span><span class="sxs-lookup"><span data-stu-id="8a096-182">Transaction Isolation Levels</span></span>](../../2014/database-engine/transaction-isolation-levels.md)  
  
  
