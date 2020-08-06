---
title: 跨容器交易 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 5d84b51a-ec17-4c5c-b80e-9e994fc8ae80
author: stevestein
ms.author: sstein
ms.openlocfilehash: 28437f0903459616a574e713c0f138e8bb459870
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596252"
---
# <a name="cross-container-transactions"></a><span data-ttu-id="d4b77-102">跨容器交易</span><span class="sxs-lookup"><span data-stu-id="d4b77-102">Cross-Container Transactions</span></span>
  <span data-ttu-id="d4b77-103">跨容器交易是隱含或明確的使用者交易，其包含對原生編譯的預存程序或記憶體最佳化的資料表作業的呼叫。</span><span class="sxs-lookup"><span data-stu-id="d4b77-103">Cross-container transactions are either implicit or explicit user transactions that include calls to natively-compiled stored procedures or operations on memory-optimized tables.</span></span>  
  
 <span data-ttu-id="d4b77-104">在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中，預存程序的呼叫不會起始交易。</span><span class="sxs-lookup"><span data-stu-id="d4b77-104">In [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], calls to stored procedures do not initiate a transaction.</span></span> <span data-ttu-id="d4b77-105">在自動認可模式中執行原生編譯的程序時 (不在使用者交易的內容中)，將不會視為跨容器交易。</span><span class="sxs-lookup"><span data-stu-id="d4b77-105">Executions of natively compiled procedures in autocommit mode (not in the context of a user transaction) are not considered cross-container transactions.</span></span>  
  
 <span data-ttu-id="d4b77-106">參考記憶體最佳化的資料表的任何解譯的查詢都視為跨容器交易的一部分，不論是從明確或隱含交易執行還是在自動認可模式中執行。</span><span class="sxs-lookup"><span data-stu-id="d4b77-106">Any interpreted query that references memory-optimized tables is considered a part of a cross-container transaction, whether executed from an explicit or implicit transaction or in auto-commit mode.</span></span>  
  
##  <a name="isolation-of-individual-operations"></a><a name="isolation"></a><span data-ttu-id="d4b77-107">隔離個別作業</span><span class="sxs-lookup"><span data-stu-id="d4b77-107">Isolation of Individual Operations</span></span>  
 <span data-ttu-id="d4b77-108">每一筆 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 交易都有隔離等級。</span><span class="sxs-lookup"><span data-stu-id="d4b77-108">Each [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] transaction has an isolation level.</span></span> <span data-ttu-id="d4b77-109">預設隔離等級為 Read Committed。</span><span class="sxs-lookup"><span data-stu-id="d4b77-109">The default isolation level is Read Committed.</span></span> <span data-ttu-id="d4b77-110">若要使用不同的隔離等級，您可以使用[SET TRANSACTION 隔離等級 &#40;transact-sql&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)設定隔離等級。</span><span class="sxs-lookup"><span data-stu-id="d4b77-110">To use a different isolation level, you can set the isolation level using [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span>  
  
 <span data-ttu-id="d4b77-111">相較於以磁碟為基礎的資料表作業，在記憶體最佳化的資料表上執行作業通常更需要在不同的隔離等級。</span><span class="sxs-lookup"><span data-stu-id="d4b77-111">It is often necessary to perform operations on memory-optimized tables at a different isolation level than operations on disk-based tables.</span></span> <span data-ttu-id="d4b77-112">在交易中，為陳述式集合或個別讀取作業設定不同隔離等級是可行的。</span><span class="sxs-lookup"><span data-stu-id="d4b77-112">In a transaction, it is possible to set a different isolation level for a collection of statements or for an individual read operation.</span></span>  
  
### <a name="specifying-the-isolation-level-of-individual-operations"></a><span data-ttu-id="d4b77-113">指定個別作業的隔離等級</span><span class="sxs-lookup"><span data-stu-id="d4b77-113">Specifying the Isolation Level of Individual Operations</span></span>  
 <span data-ttu-id="d4b77-114">若要為交易中的一組陳述式設定不同的隔離等級，您可以使用 `SET TRANSACTION ISOLATION LEVEL`。</span><span class="sxs-lookup"><span data-stu-id="d4b77-114">To set a different isolation level for a set of statements in a transaction, you can use `SET TRANSACTION ISOLATION LEVEL`.</span></span> <span data-ttu-id="d4b77-115">以下的交易範例會使用 serializable 的隔離等級當做預設值。</span><span class="sxs-lookup"><span data-stu-id="d4b77-115">The following example of a transaction uses the serializable isolation level as default.</span></span> <span data-ttu-id="d4b77-116">位於 t3、t2 和 t1 的插入和選取作業會在 repeatable read 的隔離之下執行。</span><span class="sxs-lookup"><span data-stu-id="d4b77-116">The insert and select operations on t3, t2, and t1 are executed under repeatable read isolation.</span></span>  
  
```sql  
set transaction isolation level serializable  
go  
  
begin transaction  
 ......  
  set transaction isolation level repeatable read  
  
  insert t3 select * from t1 join t2 on t1.id=t2.id  
  
  set transaction isolation level serializable  
 ......  
commit  
```  
  
 <span data-ttu-id="d4b77-117">若要為個別讀取作業設定不同於交易預設值的隔離等級，您可以使用資料表提示 (例如，可序列化)。</span><span class="sxs-lookup"><span data-stu-id="d4b77-117">To set an isolation level for individual read operations that is different from the transaction default, you can use a table hint (for example, serializable).</span></span> <span data-ttu-id="d4b77-118">每個選取都會對應到讀取作業，而每個更新和每個刪除都會對應到讀取，因為在可以更新和刪除資料列之前永遠都必須先讀取它。</span><span class="sxs-lookup"><span data-stu-id="d4b77-118">Every select corresponds to a read operation and every update and every delete corresponds to a read, because the row always needs to be read before it can be updated or deleted.</span></span> <span data-ttu-id="d4b77-119">插入作業沒有隔離等級，因為寫入在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中永遠都是隔離的。</span><span class="sxs-lookup"><span data-stu-id="d4b77-119">Insert operations do not have an isolation level, because writes are always isolated in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="d4b77-120">在下列範例中，交易的預設隔離等級為 read committed，不過，資料表 t1 會在 serializable 隔離之下存取，而 t2 會在 snapshot 隔離之下存取。</span><span class="sxs-lookup"><span data-stu-id="d4b77-120">In the following example, the default isolation level for the transaction is read committed, but table t1 is accessed under serializable and t2 under snapshot isolation.</span></span>  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
 ......  
  
  insert t3 select * from t1 (serializable) join t2 (snapshot) on t1.id=t2.id  
  
  ......  
commit  
```  
  
### <a name="isolation-semantics-for-individual-operations"></a><span data-ttu-id="d4b77-121">個別作業的隔離語意</span><span class="sxs-lookup"><span data-stu-id="d4b77-121">Isolation Semantics for Individual Operations</span></span>  
 <span data-ttu-id="d4b77-122">可序列化交易 T 會在完全隔離的情況下執行。</span><span class="sxs-lookup"><span data-stu-id="d4b77-122">A serializable transaction T is executed in complete isolation.</span></span> <span data-ttu-id="d4b77-123">就像是其他每一筆交易在 T 開始之前已經認可，或者在 T 認可之後開始一樣。</span><span class="sxs-lookup"><span data-stu-id="d4b77-123">It is as if every other transaction has either committed before T started, or is started after T committed.</span></span> <span data-ttu-id="d4b77-124">當交易中有不同的作業具有不同隔離等級時，它會變得更複雜。</span><span class="sxs-lookup"><span data-stu-id="d4b77-124">It becomes more complex when different operations in a transaction have different isolation levels.</span></span>  
  
 <span data-ttu-id="d4b77-125">中的交易隔離等級的一般語義 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 以及對鎖定的影響，會在[&#40;transact-sql&#41;的設定交易隔離等級](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql)中說明。</span><span class="sxs-lookup"><span data-stu-id="d4b77-125">The general semantics of the transaction isolation levels in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], along with the implications on locking, is explained in [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).</span></span>  
  
 <span data-ttu-id="d4b77-126">如果是不同作業可能會有不同隔離等級的跨容器交易，您必須了解個別讀取作業的隔離語意。</span><span class="sxs-lookup"><span data-stu-id="d4b77-126">For cross-container transactions where different operations may have different isolation levels, you need to understand the semantics of isolation of individual read operations.</span></span> <span data-ttu-id="d4b77-127">寫入作業永遠都會隔離。</span><span class="sxs-lookup"><span data-stu-id="d4b77-127">Write operations are always isolated.</span></span> <span data-ttu-id="d4b77-128">不同交易中的寫入無法影響彼此。</span><span class="sxs-lookup"><span data-stu-id="d4b77-128">Writes in different transactions cannot impact each other.</span></span>  
  
 <span data-ttu-id="d4b77-129">資料讀取作業會傳回滿足篩選條件的許多資料列。</span><span class="sxs-lookup"><span data-stu-id="d4b77-129">A data read operation returns a number of rows that satisfy a filter condition.</span></span>  
  
 <span data-ttu-id="d4b77-130">讀取會做為交易 T 的一部分來執行。讀取作業的隔離等級可以根據來理解，</span><span class="sxs-lookup"><span data-stu-id="d4b77-130">Reads are performed as part of a transaction T. Isolation levels for read operations can be understood in terms of,</span></span>  
  
 <span data-ttu-id="d4b77-131">認可狀態</span><span class="sxs-lookup"><span data-stu-id="d4b77-131">Commit Status</span></span>  
 <span data-ttu-id="d4b77-132">認可狀態指的是，是否可以保證資料讀取為已認可狀態。</span><span class="sxs-lookup"><span data-stu-id="d4b77-132">Commit status refers to whether the data read is guaranteed to be committed.</span></span>  
  
 <span data-ttu-id="d4b77-133">(交易) 一致性</span><span class="sxs-lookup"><span data-stu-id="d4b77-133">(Transactional) Consistency</span></span>  
 <span data-ttu-id="d4b77-134">一組讀取的交易一致性指的是，是否保證所有資料列版本讀取都精確包含來自相同一組交易的更新。</span><span class="sxs-lookup"><span data-stu-id="d4b77-134">Transactional consistency for a set of reads refers to whether the row versions read are all guaranteed to include updates from precisely the same set of transactions.</span></span>  
  
 <span data-ttu-id="d4b77-135">穩定性會保證系統給出有關資料讀取的資訊給交易 T。</span><span class="sxs-lookup"><span data-stu-id="d4b77-135">Stability guarantees the system gives to transaction T about the data read.</span></span>  
 <span data-ttu-id="d4b77-136">穩定性指的是交易的讀取是否可重複。</span><span class="sxs-lookup"><span data-stu-id="d4b77-136">Stability refers to whether the transaction's reads are repeatable.</span></span> <span data-ttu-id="d4b77-137">也就是說，如果讀取已重複，它們是否會傳回相同的資料列和資料列版本？</span><span class="sxs-lookup"><span data-stu-id="d4b77-137">That is, if the reads were repeated would they return the same rows and row versions?</span></span>  
  
 <span data-ttu-id="d4b77-138">特定保證指的是交易的邏輯結束時間。</span><span class="sxs-lookup"><span data-stu-id="d4b77-138">Certain guarantees refer to the logical end time of the transaction.</span></span> <span data-ttu-id="d4b77-139">一般而言，邏輯結束時間是資料庫認可交易的時間。</span><span class="sxs-lookup"><span data-stu-id="d4b77-139">In general, the logical end time is the time the transaction is committed to the database.</span></span> <span data-ttu-id="d4b77-140">如果記憶體最佳化的資料表是由交易所存取，則邏輯結束時間在技術上為驗證階段的開始 </span><span class="sxs-lookup"><span data-stu-id="d4b77-140">If memory-optimized tables are accessed by the transaction, the logical end time is technically the beginning of the validation phase.</span></span> <span data-ttu-id="d4b77-141"> (需詳細資訊，請參閱[記憶體優化資料表中交易](../relational-databases/in-memory-oltp/memory-optimized-tables.md)的交易存留期討論。</span><span class="sxs-lookup"><span data-stu-id="d4b77-141">(For more information, see the transaction lifetime discussion in [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="d4b77-142">不論隔離等級為何，交易 (T) 永遠都會看到自己的更新：</span><span class="sxs-lookup"><span data-stu-id="d4b77-142">Regardless of isolation level, a transaction (T) always sees its own updates:</span></span>  
  
 <span data-ttu-id="d4b77-143">READ UNCOMMITTED</span><span class="sxs-lookup"><span data-stu-id="d4b77-143">READ UNCOMMITTED</span></span>  
 <span data-ttu-id="d4b77-144">資料讀取可能不會處於已認可、一致或穩定狀態。</span><span class="sxs-lookup"><span data-stu-id="d4b77-144">The data read may neither be committed, consistent, or stable.</span></span> <span data-ttu-id="d4b77-145">不過，它將會包含 T 稍早完成的寫入作業。</span><span class="sxs-lookup"><span data-stu-id="d4b77-145">However, it will include earlier write operations done by T.</span></span>  
  
 <span data-ttu-id="d4b77-146">READ COMMITTED</span><span class="sxs-lookup"><span data-stu-id="d4b77-146">READ COMMITTED</span></span>  
 <span data-ttu-id="d4b77-147">將會認可資料讀取。</span><span class="sxs-lookup"><span data-stu-id="d4b77-147">The data read will be committed.</span></span>  
  
 <span data-ttu-id="d4b77-148">SNAPSHOT</span><span class="sxs-lookup"><span data-stu-id="d4b77-148">SNAPSHOT</span></span>  
 <span data-ttu-id="d4b77-149">snapshot 隔離之下由 T 執行的所有讀取作業都有相同的邏輯讀取時間，也就是交易的開始時間。</span><span class="sxs-lookup"><span data-stu-id="d4b77-149">All read operations performed by T under snapshot isolation have the same logical read time, which is the beginning of the transaction.</span></span> <span data-ttu-id="d4b77-150">將會保證資料讀取為已認可狀態，而且在邏輯讀取時間維持一致性。</span><span class="sxs-lookup"><span data-stu-id="d4b77-150">The data read is guaranteed to be committed and consistent as of the logical read time.</span></span> <span data-ttu-id="d4b77-151">也會保證重複原始讀取時間的讀取會傳回相同的結果。</span><span class="sxs-lookup"><span data-stu-id="d4b77-151">Repeating a read as of the original read time is guaranteed to return the same result.</span></span>  
  
 <span data-ttu-id="d4b77-152">REPEATABLE READ</span><span class="sxs-lookup"><span data-stu-id="d4b77-152">REPEATABLE READ</span></span>  
 <span data-ttu-id="d4b77-153">保證資料讀取為已認可狀態，而且一直到交易的邏輯結束時間為止都很穩定。</span><span class="sxs-lookup"><span data-stu-id="d4b77-153">The data read is guaranteed to be committed and stable up to the logical end time of the transaction.</span></span>  
  
 <span data-ttu-id="d4b77-154">SERIALIZABLE</span><span class="sxs-lookup"><span data-stu-id="d4b77-154">SERIALIZABLE</span></span>  
 <span data-ttu-id="d4b77-155">可重複讀取的所有保證，以及與 T 所執行之所有可序列化讀取作業相關的交易一致性。虛設避免表示掃描工作只能傳回 T 所寫入的其他資料列，但沒有其他交易寫入的資料列。</span><span class="sxs-lookup"><span data-stu-id="d4b77-155">All guarantees of REPEATABLE READ plus phantom avoidance and transactional consistency with respect to all serializable read operations performed by T. Phantom avoidance means that the scan operation can only return additional rows that were written by T, but no rows that were written by other transactions.</span></span>  
  
 <span data-ttu-id="d4b77-156">以下列交易為例：</span><span class="sxs-lookup"><span data-stu-id="d4b77-156">Consider the following transaction,</span></span>  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
  -- remove all rows from t3; the related read operation is performed under read committed   
  -- isolation, as this is the default for the transaction  
  delete from t3  
  
  -- copy the contents from t1 to t3; the read on t1 is performed under the serializable   
  -- isolation level  
  insert t3 select * from t1 (serializable)  
  
  -- compare t3 and t1; note: the result set may not be empty, as rows may have been added   
  -- by other transaction before this select, due to the read committed isolation level  
  select * from t3 except t1  
  
  -- compare t1 and t3; note: the result set is empty, as no rows have been added to t1   
  -- since its contents were copied to t1, due to the serializable isolation level  
  select * from t1 except t3  
commit  
```  
  
 <span data-ttu-id="d4b77-157">此交易會從 t3 刪除 read committed 隔離之下的所有資料列、複製 t1 到 t3 中在 serializable 隔離之下的所有資料列，然後比較 t1 和 t3。</span><span class="sxs-lookup"><span data-stu-id="d4b77-157">This transaction deletes all rows from t3 under read committed isolation, copies all rows from t1 to t3 under serializable isolation, and then compares t1 and t3.</span></span> <span data-ttu-id="d4b77-158">部分資料列 [不在 t1 中] 可能已加入到 t3，因為此資料表已清空。</span><span class="sxs-lookup"><span data-stu-id="d4b77-158">Some rows [not in t1] may have been added to t3 since the table was emptied.</span></span> <span data-ttu-id="d4b77-159">沒有任何資料列已加入至 t1，因為複製為 serializable。</span><span class="sxs-lookup"><span data-stu-id="d4b77-159">No rows were added to t1 as the copy was serializable.</span></span>  
  
 <span data-ttu-id="d4b77-160">雖然在交易結束時從 t1 讀取的語意為 read committed，但是它實際上為 serializable，因為之前在交易中的 serializable 隔離之下已執行相同的讀取：可序列化保證如果在之後的任何交易時間點執行讀取，將會傳回相同的資料列。</span><span class="sxs-lookup"><span data-stu-id="d4b77-160">Although the read from t1 at the end of the transaction is syntactically read committed, it is effectively serializable, because the same read was performed earlier in the transaction under serializable isolation: serializability guarantees that if the read is performed at any later point in the transaction, the same rows are returned.</span></span>  
  
## <a name="cross-container-transactions-and-isolation-levels"></a><span data-ttu-id="d4b77-161">跨容器交易和隔離等級</span><span class="sxs-lookup"><span data-stu-id="d4b77-161">Cross-Container Transactions and Isolation Levels</span></span>  
 <span data-ttu-id="d4b77-162">跨容器交易可視為具有兩端：以磁碟為基礎的那一端 (適用於以磁碟為基礎資料表的作業) 和記憶體最佳化的那一端 (適用於記憶體最佳化資料表的作業)。</span><span class="sxs-lookup"><span data-stu-id="d4b77-162">A cross-container transaction can be seen as having two sides: a disk-based side (for operations on disk-based tables) and a memory-optimized side (for operations on memory-optimized tables).</span></span> <span data-ttu-id="d4b77-163">這兩端可能會有不同的隔離等級。</span><span class="sxs-lookup"><span data-stu-id="d4b77-163">These two sides may have different isolation levels.</span></span> <span data-ttu-id="d4b77-164">事實上，每一端的個別讀取作業可能會有不同的隔離等級。</span><span class="sxs-lookup"><span data-stu-id="d4b77-164">In fact, individual read operations on each side may have different isolation levels.</span></span>  
  
 <span data-ttu-id="d4b77-165">如果符合下列其中一個條件，給定交易 T 的磁碟端會到達某個隔離等級 X：</span><span class="sxs-lookup"><span data-stu-id="d4b77-165">The disk-based side of a given transaction T reaches a certain isolation level X if one of the following conditions is met:</span></span>  
  
-   <span data-ttu-id="d4b77-166">它會從 X 開始。也就是說，會話預設值是 X，因為您執行了 `SET TRANSACTION ISOLATION LEVEL` ，或者它是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 預設值。</span><span class="sxs-lookup"><span data-stu-id="d4b77-166">It starts in X. That is, the session default was X, either because you executed `SET TRANSACTION ISOLATION LEVEL`, or it is the [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] default.</span></span>  
  
-   <span data-ttu-id="d4b77-167">在交易期間，使用 `SET TRANSACTION ISOLATION LEVEL` 將預設隔離等級變更為 X。</span><span class="sxs-lookup"><span data-stu-id="d4b77-167">During the transaction, the default isolation level is changed to X using `SET TRANSACTION ISOLATION LEVEL`.</span></span>  
  
-   <span data-ttu-id="d4b77-168">以磁碟為基礎的資料表讀取作業會使用 `WITH (X)` 語法在隔離等級 X 之下執行。</span><span class="sxs-lookup"><span data-stu-id="d4b77-168">A read operation on a disk-based table is executed under isolation level X, using the syntax `WITH (X)`.</span></span>  
  
 <span data-ttu-id="d4b77-169">如果在 T 的執行期間，記憶體最佳化資料表的任何讀取作業或是任何原生方式編譯的預存程序在隔離等級 Y 之下執行，T 的記憶體最佳化那一端會到達隔離等級 Y。</span><span class="sxs-lookup"><span data-stu-id="d4b77-169">The memory-optimized side of T reaches an isolation level Y if during execution of T, any read operation on a memory-optimized table or any natively compiled stored procedure is executed under isolation level Y.</span></span>  
  
 <span data-ttu-id="d4b77-170">以下列交易為例。</span><span class="sxs-lookup"><span data-stu-id="d4b77-170">Consider the following transaction as an example.</span></span> <span data-ttu-id="d4b77-171">此處，t1 和 t2 是以磁碟為基礎的資料表，而 t3 和 t4 是記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="d4b77-171">Here, t1 and t2 are disk-based tables and t3 and t4 are memory-optimized tables.</span></span>  
  
 <span data-ttu-id="d4b77-172">交易的磁碟端會到達 read committed 隔離等級，因為它是從這個等級開始。</span><span class="sxs-lookup"><span data-stu-id="d4b77-172">The disk-based side of the transaction reaches the isolation level read committed, because it starts in that level.</span></span> <span data-ttu-id="d4b77-173">磁碟端也會到達 repeatable read 隔離等級，因為第一個讀取作業是在這個隔離等級之下執行。</span><span class="sxs-lookup"><span data-stu-id="d4b77-173">The disk-based side also reaches repeatable read, because the first read operation is executed under that isolation level.</span></span> <span data-ttu-id="d4b77-174">交易結束時的刪除作業會在 read committed 隔離等級之下執行，因此不會引進新的隔離等級。</span><span class="sxs-lookup"><span data-stu-id="d4b77-174">The delete at the end of the transaction is executed under read committed isolation level, and so does not introduce a new isolation level.</span></span>  
  
 <span data-ttu-id="d4b77-175">交易的記憶體最佳化那一端可以到達兩個等級的其中一個：如果 condition1 為 true，它會到達可序列化隔離，而如果為 false，則記憶體最佳化那一端只會到達快照集隔離。</span><span class="sxs-lookup"><span data-stu-id="d4b77-175">The memory-optimized side of the transaction can reach one of two levels: if condition1 is true, it reaches serializable, while if it is false, the memory-optimized side reaches only snapshot isolation.</span></span>  
  
```sql  
set transaction isolation level read committed  
go  
  
begin transaction  
  select * from t1 (repeatableread)  
  
  if condition1 begin  
    insert t3 select * from t4 (serializable)  
  end  
  else begin  
    insert t3 select * from t4 (snapshot)  
  end  
  
  delete from t1  
commit  
```  
  
### <a name="supported-isolation-levels-for-cross-container-transactions"></a><span data-ttu-id="d4b77-176">跨容器交易支援的隔離等級</span><span class="sxs-lookup"><span data-stu-id="d4b77-176">Supported Isolation Levels for Cross-Container Transactions</span></span>  
 <span data-ttu-id="d4b77-177">在跨容器交易中，搭配記憶體最佳化的資料表作業使用的隔離等級有一些限制。</span><span class="sxs-lookup"><span data-stu-id="d4b77-177">There are limitations on the isolation levels used with operations on memory-optimized tables in cross-container transactions.</span></span>  
  
 <span data-ttu-id="d4b77-178">記憶體最佳化的資料表可支援 SNAPSHOT、REPEATABLE READ 和 SERIALIZABLE 隔離等級。</span><span class="sxs-lookup"><span data-stu-id="d4b77-178">Memory-optimized tables support the isolation levels SNAPSHOT, REPEATABLE READ, and SERIALIZABLE.</span></span> <span data-ttu-id="d4b77-179">如果是自動認可交易，記憶體最佳化的資料表可支援 READ COMMITTED 隔離等級。</span><span class="sxs-lookup"><span data-stu-id="d4b77-179">For autocommit transactions, memory-optimized tables support the isolation level READ COMMITTED.</span></span>  
  
 <span data-ttu-id="d4b77-180">以下是支援的案例：</span><span class="sxs-lookup"><span data-stu-id="d4b77-180">The following scenarios are supported:</span></span>  
  
-   <span data-ttu-id="d4b77-181">READ UNCOMMITTED、READ COMMITTED 和 READ_COMMITTED_SNAPSHOT 跨容器交易可以在 SNAPSHOT、REPEATABLE READ 和 SERIALIZABLE 隔離之下存取記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="d4b77-181">READ UNCOMMITTED, READ COMMITTED, and READ_COMMITTED_SNAPSHOT cross-container transactions can access memory-optimized tables under SNAPSHOT, REPEATABLE READ, and SERIALIZABLE isolation.</span></span> <span data-ttu-id="d4b77-182">交易的 READ COMMITTED 保證依然存在；資料庫已認可此交易讀取的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="d4b77-182">The READ COMMITTED guarantee holds for the transaction; all rows read by the transaction have been committed to the database.</span></span>  
  
-   <span data-ttu-id="d4b77-183">REPEATABLE READ 和 SERIALIZABLE 交易可以在 SNAPSHOT 隔離之下存取記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="d4b77-183">REPEATABLE READ and SERIALIZABLE transactions can access memory-optimized tables under SNAPSHOT isolation.</span></span>  
  
## <a name="read-only-cross-container-transactions"></a><span data-ttu-id="d4b77-184">唯讀的跨容器交易</span><span class="sxs-lookup"><span data-stu-id="d4b77-184">Read-only Cross-Container Transactions</span></span>  
 <span data-ttu-id="d4b77-185">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中的大部分唯讀交易都會在認可時間回復。</span><span class="sxs-lookup"><span data-stu-id="d4b77-185">Most read-only transactions in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] are rolled back at commit time.</span></span> <span data-ttu-id="d4b77-186">因為資料庫不需認可任何變更，所以系統會釋出交易所使用的資源。</span><span class="sxs-lookup"><span data-stu-id="d4b77-186">Because there are no changes to commit to the database, the system simply frees the resources used by the transaction.</span></span> <span data-ttu-id="d4b77-187">如果是唯讀的磁碟交易，交易所做的所有鎖定都會在此時釋放。</span><span class="sxs-lookup"><span data-stu-id="d4b77-187">For read-only disk-based transactions, all locks taken by the transaction are released at this time.</span></span> <span data-ttu-id="d4b77-188">如果是跨越單一原生編譯程序執行的唯讀記憶體最佳化交易，則不會執行驗證。</span><span class="sxs-lookup"><span data-stu-id="d4b77-188">For read-only memory-optimized transactions that span a single natively compiled procedure execution, no validation is performed.</span></span>  
  
 <span data-ttu-id="d4b77-189">自動認可模式中的跨容器唯讀交易會在交易結束時回復。</span><span class="sxs-lookup"><span data-stu-id="d4b77-189">Cross-container, read-only transactions in autocommit mode are simply rolled back at the end of the transaction.</span></span> <span data-ttu-id="d4b77-190">未執行任何驗證。</span><span class="sxs-lookup"><span data-stu-id="d4b77-190">No validation is performed.</span></span>  
  
 <span data-ttu-id="d4b77-191">如果交易在 REPEATABLE READ 或 SERIALIZABLE 隔離之下存取記憶體最佳化資料表，則明確或隱含的跨容器唯讀交易會在認可時間執行驗證。</span><span class="sxs-lookup"><span data-stu-id="d4b77-191">Explicit or implicit cross-container, read-only transactions perform validation at commit time if the transaction accesses memory-optimized tables under REPEATABLE READ or SERIALIZABLE isolation.</span></span> <span data-ttu-id="d4b77-192">如需驗證的詳細資訊，請參閱[記憶體優化資料表中交易](../relational-databases/in-memory-oltp/memory-optimized-tables.md)的衝突偵測、驗證和認可相依性檢查一節。</span><span class="sxs-lookup"><span data-stu-id="d4b77-192">For details about validation see the section on Conflict Detection, Validation, and Commit Dependency Checks in [Transactions in Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4b77-193">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4b77-193">See Also</span></span>  
 <span data-ttu-id="d4b77-194">[瞭解記憶體優化資料表上的交易](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="d4b77-194">[Understanding Transactions on Memory-Optimized Tables](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md) </span></span>  
 <span data-ttu-id="d4b77-195">[具有記憶體優化資料表的交易隔離等級方針](../../2014/database-engine/guidelines-for-transaction-isolation-levels-with-memory-optimized-tables.md) </span><span class="sxs-lookup"><span data-stu-id="d4b77-195">[Guidelines for Transaction Isolation Levels with Memory-Optimized Tables](../../2014/database-engine/guidelines-for-transaction-isolation-levels-with-memory-optimized-tables.md) </span></span>  
 [<span data-ttu-id="d4b77-196">記憶體最佳化資料表交易的重試邏輯方針</span><span class="sxs-lookup"><span data-stu-id="d4b77-196">Guidelines for Retry Logic for Transactions on Memory-Optimized Tables</span></span>](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)  
  
  
