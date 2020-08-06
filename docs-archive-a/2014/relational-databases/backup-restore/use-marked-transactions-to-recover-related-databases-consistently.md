---
title: 使用標示的交易以一致的方式復原相關資料庫， (完整復原模式) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- transaction marks [SQL Server]
- marked transactions [SQL Server]
- database restores [SQL Server], inserting transaction marks for
- recovery [SQL Server], related databases
- restoring databases [SQL Server], related database recovery
- database restores [SQL Server], related databases
- marked transactions [SQL Server], creating
- BEGIN TRAN...WITH MARK statement
- two-phase commit
ms.assetid: 50a73574-1a69-448e-83dd-9abcc7cb7e1a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8dd368ad14f6e521fb8d504bdea774e3088c2522
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705190"
---
# <a name="use-marked-transactions-to-recover-related-databases-consistently-full-recovery-model"></a><span data-ttu-id="b40e4-102">使用標示的異動以一致的方式復原相關資料庫 (完整復原模式)</span><span class="sxs-lookup"><span data-stu-id="b40e4-102">Use Marked Transactions to Recover Related Databases Consistently (Full Recovery Model)</span></span>
  <span data-ttu-id="b40e4-103">本主題只與使用完整或大量記錄復原模式的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫有關。</span><span class="sxs-lookup"><span data-stu-id="b40e4-103">This topic is relevant only for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that are using the full or bulk-logged recovery models.</span></span>  
  
 <span data-ttu-id="b40e4-104">當您對兩個以上的資料庫 (「相關資料庫」  ) 進行相關的更新時，您可以使用交易標示將它們復原到邏輯上一致的時間點。</span><span class="sxs-lookup"><span data-stu-id="b40e4-104">When you make related updates to two or more databases, *related databases*, you can use transaction marks to recover them to a logically consistent point.</span></span> <span data-ttu-id="b40e4-105">不過，這種復原會遺失任何在復原點標示之後所認可的交易。</span><span class="sxs-lookup"><span data-stu-id="b40e4-105">However, this recovery loses any transaction that is committed after the mark that was used as the recovery point.</span></span> <span data-ttu-id="b40e4-106">只有當您要測試相關資料庫，或是願意遺失最近認可的交易時，才適合標示交易。</span><span class="sxs-lookup"><span data-stu-id="b40e4-106">Marking transactions is suitable only when you are testing related databases or when you are willing to lose recently committed transactions.</span></span>  
  
 <span data-ttu-id="b40e4-107">例行性標示每個相關資料庫中的相關交易會在資料庫中建立一系列通用的復原點。</span><span class="sxs-lookup"><span data-stu-id="b40e4-107">Routinely marking related transactions in every related database establishes a series of common recovery points in the databases.</span></span> <span data-ttu-id="b40e4-108">交易標示將記錄於交易記錄，並且包含在記錄備份中。</span><span class="sxs-lookup"><span data-stu-id="b40e4-108">The transaction marks are recorded in the transaction log and included in log backups.</span></span> <span data-ttu-id="b40e4-109">如果發生損毀，即可將每個資料庫還原到相同的交易標示，進而復原至一致的時間點。</span><span class="sxs-lookup"><span data-stu-id="b40e4-109">In the event of a disaster, you can restore each of the databases to the same transaction mark to recover them to a consistent point.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b40e4-110">不同的資料庫上的記錄備份可以各自建立，互不影響，而且也不必同時進行。</span><span class="sxs-lookup"><span data-stu-id="b40e4-110">Log backups on the different databases can be created independently of each other and do not have to be simultaneous.</span></span>  
  
 <span data-ttu-id="b40e4-111">在下列狀況中復原相關資料庫時，您必須先在每個相關資料庫中標示過交易：</span><span class="sxs-lookup"><span data-stu-id="b40e4-111">Recovering related databases in the following scenarios requires that you have already marked transactions in every related database:</span></span>  
  
-   <span data-ttu-id="b40e4-112">一或多個交易記錄檔被毀。</span><span class="sxs-lookup"><span data-stu-id="b40e4-112">One or more transaction logs are destroyed.</span></span> <span data-ttu-id="b40e4-113">您必須將一組資料庫還原到最後一次記錄備份時的一致狀態。</span><span class="sxs-lookup"><span data-stu-id="b40e4-113">You have to restore the set of databases to a consistent state at the time of your last log backup.</span></span>  
  
-   <span data-ttu-id="b40e4-114">您必須將整個資料庫集合還原到某個較早時間點的共同一致狀態。</span><span class="sxs-lookup"><span data-stu-id="b40e4-114">You have to restore the entire set of databases to a mutually consistent state at some earlier point in time.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="b40e4-115">您只能將相關資料庫復原到已標示的交易，而不能復原到特定的時間點。</span><span class="sxs-lookup"><span data-stu-id="b40e4-115">You can recover related databases only to a marked transaction, not to a specific point in time.</span></span>  
  
 <span data-ttu-id="b40e4-116">如需有關如何建立標示交易的詳細資訊，請參閱本主題稍後的「建立標示的交易」。</span><span class="sxs-lookup"><span data-stu-id="b40e4-116">For information about how to create marking transactions, see "Creating the Marked Transactions," later in this topic.</span></span>  
  
## <a name="typical-scenario-for-using-marked-transactions"></a><span data-ttu-id="b40e4-117">使用標示的交易的一般狀況</span><span class="sxs-lookup"><span data-stu-id="b40e4-117">Typical Scenario for Using Marked Transactions</span></span>  
 <span data-ttu-id="b40e4-118">使用標示的交易的一般狀況包括下列步驟：</span><span class="sxs-lookup"><span data-stu-id="b40e4-118">A typical scenario for using marked transactions includes the following steps:</span></span>  
  
1.  <span data-ttu-id="b40e4-119">建立每個相關資料庫的完整或差異資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="b40e4-119">Create a full or differential database backup of each of the related databases.</span></span>  
  
2.  <span data-ttu-id="b40e4-120">在所有資料庫中標示交易區塊。</span><span class="sxs-lookup"><span data-stu-id="b40e4-120">Mark a transaction block in all the databases.</span></span>  
  
3.  <span data-ttu-id="b40e4-121">備份所有資料庫的交易記錄。</span><span class="sxs-lookup"><span data-stu-id="b40e4-121">Back up the transaction log for all the databases.</span></span>  
  
4.  <span data-ttu-id="b40e4-122">使用 WITH NORECOVERY 還原資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="b40e4-122">Restore database backups WITH NORECOVERY.</span></span>  
  
5.  <span data-ttu-id="b40e4-123">使用 WITH STOPATMARK 還原記錄。</span><span class="sxs-lookup"><span data-stu-id="b40e4-123">Restore logs WITH STOPATMARK.</span></span>  
  
## <a name="considerations-for-using-marked-transactions"></a><span data-ttu-id="b40e4-124">使用標示的交易的考量</span><span class="sxs-lookup"><span data-stu-id="b40e4-124">Considerations for Using Marked Transactions</span></span>  
 <span data-ttu-id="b40e4-125">將具名標示插入交易記錄之前，請考慮以下幾點：</span><span class="sxs-lookup"><span data-stu-id="b40e4-125">Before inserting named marks into the transaction log, consider the following:</span></span>  
  
-   <span data-ttu-id="b40e4-126">因為交易標示須耗用記錄空間，所以除非它們在資料庫復原策略中扮演重要的角色，否則不應使用交易標示。</span><span class="sxs-lookup"><span data-stu-id="b40e4-126">Because transaction marks consume log space, use them only for transactions that play a significant role in the database recovery strategy.</span></span>  
  
-   <span data-ttu-id="b40e4-127">標示的交易認可之後，會在 [msdb](/sql/relational-databases/system-tables/logmarkhistory-transact-sql) 的 **logmarkhistory**資料表中插入一個資料列。</span><span class="sxs-lookup"><span data-stu-id="b40e4-127">After a marked transaction commits, a row is inserted in the [logmarkhistory](/sql/relational-databases/system-tables/logmarkhistory-transact-sql) table in **msdb**.</span></span>  
  
-   <span data-ttu-id="b40e4-128">如果標示交易跨越同一資料庫伺服器或不同伺服器上的多個資料庫，則標示會記錄在所有受影響的資料庫之記錄中。</span><span class="sxs-lookup"><span data-stu-id="b40e4-128">If a marked transaction spans multiple databases on the same database server or on different servers, the marks must be recorded in the logs of all the affected databases.</span></span>  
  
## <a name="creating-the-marked-transactions"></a><span data-ttu-id="b40e4-129">建立標示的交易</span><span class="sxs-lookup"><span data-stu-id="b40e4-129">Creating the Marked Transactions</span></span>  
 <span data-ttu-id="b40e4-130">若要建立標示的交易，請使用 [BEGIN TRANSACTION](/sql/t-sql/language-elements/begin-transaction-transact-sql) 陳述式和 WITH MARK [描述  ] 子句。</span><span class="sxs-lookup"><span data-stu-id="b40e4-130">To create a marked transaction, use the [BEGIN TRANSACTION](/sql/t-sql/language-elements/begin-transaction-transact-sql) statement and the WITH MARK [*description*] clause.</span></span> <span data-ttu-id="b40e4-131">選擇性的「描述」  是標示的文字說明。</span><span class="sxs-lookup"><span data-stu-id="b40e4-131">The optional *description* is a textual description of the mark.</span></span> <span data-ttu-id="b40e4-132">標示名稱對於交易而言是必要的。</span><span class="sxs-lookup"><span data-stu-id="b40e4-132">A mark name for the transaction is required.</span></span> <span data-ttu-id="b40e4-133">標示名稱可以重複使用。</span><span class="sxs-lookup"><span data-stu-id="b40e4-133">A mark name can be reused.</span></span> <span data-ttu-id="b40e4-134">交易記錄中會記錄標示名稱、描述、資料庫、使用者、日期時間資訊與記錄序號 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="b40e4-134">The transaction log records the mark name, description, database, user, datetime information, and the log sequence number (LSN).</span></span> <span data-ttu-id="b40e4-135">日期時間資訊要連同標示名稱一起使用，才能唯一識別標示。</span><span class="sxs-lookup"><span data-stu-id="b40e4-135">The datetime information is used along with the mark name to uniquely identify the mark.</span></span>  
  
 <span data-ttu-id="b40e4-136">**若要在一組資料庫中建立標示的交易：**</span><span class="sxs-lookup"><span data-stu-id="b40e4-136">**To create marked transactions in a set of databases:**</span></span>  
  
1.  <span data-ttu-id="b40e4-137">在 BEGIN TRAN 陳述式中指定交易名稱，並使用 WITH MARK 子句</span><span class="sxs-lookup"><span data-stu-id="b40e4-137">Name the transaction in the BEGIN TRAN statement and use the WITH MARK clause</span></span>  
  
     <span data-ttu-id="b40e4-138">您可以在現有的交易中使用巢狀陳述式 BEGIN TRAN *new_mark_name* WITH MARK。</span><span class="sxs-lookup"><span data-stu-id="b40e4-138">You can nest the statement BEGIN TRAN *new_mark_name* WITH MARK within an existing transaction.</span></span> <span data-ttu-id="b40e4-139">即使交易已經有交易名稱， *new_mark_name* 的值仍是交易的標示名稱。</span><span class="sxs-lookup"><span data-stu-id="b40e4-139">The value of *new_mark_name* is the mark name for the transaction, even if the transaction possesses a transaction name.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b40e4-140">如果您發出第二個巢狀的 BEGIN TRAN...WITH MARK，則會略過該陳述式，但會出現警告訊息。</span><span class="sxs-lookup"><span data-stu-id="b40e4-140">If you issue a second nested BEGIN TRAN...WITH MARK, that statement is skipped but causes a warning message.</span></span>  
  
2.  <span data-ttu-id="b40e4-141">針對集合中的所有資料庫執行更新。</span><span class="sxs-lookup"><span data-stu-id="b40e4-141">Run an update against all of the databases in the set.</span></span>  
  
     <span data-ttu-id="b40e4-142">只有在執行 BEGIN TRAN...WITH MARK 陳述式的伺服器執行個體上，特定交易的標示才會插入交易記錄中。</span><span class="sxs-lookup"><span data-stu-id="b40e4-142">The mark for a specific transaction is inserted into transaction logs only on the server instance where the BEGIN TRAN...WITH MARK statement is executed.</span></span> <span data-ttu-id="b40e4-143">交易標示會置於該伺服器執行個體上每個由標示的交易所更新之資料庫的交易記錄中。</span><span class="sxs-lookup"><span data-stu-id="b40e4-143">The transaction mark is placed in the transaction log of every database updated by the marked transaction on that server instance.</span></span> <span data-ttu-id="b40e4-144">如果資料庫位於不同的伺服器執行個體，則必須在每個伺服器執行個體上建立完全相同的標示。</span><span class="sxs-lookup"><span data-stu-id="b40e4-144">If the databases reside on different server instances, identical marks must be created on each of the server instances.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="b40e4-145">範例</span><span class="sxs-lookup"><span data-stu-id="b40e4-145">Examples</span></span>  
 <span data-ttu-id="b40e4-146">下列範例會將交易記錄還原到名為 `ListPriceUpdate`的標示交易中之標示。</span><span class="sxs-lookup"><span data-stu-id="b40e4-146">The following example restores the transaction log to the mark in the marked transaction named `ListPriceUpdate`.</span></span>  
  
```sql  
USE AdventureWorks  
GO  
BEGIN TRANSACTION ListPriceUpdate  
   WITH MARK 'UPDATE Product list prices';  
GO  
  
UPDATE Production.Product  
   SET ListPrice = ListPrice * 1.10  
   WHERE ProductNumber LIKE 'BK-%';  
GO  
  
COMMIT TRANSACTION ListPriceUpdate;  
GO  
  
-- Time passes. Regular database   
-- and log backups are taken.  
-- An error occurs in the database.  
USE master  
GO  
  
RESTORE DATABASE AdventureWorks  
FROM AdventureWorksBackups  
WITH FILE = 3, NORECOVERY;  
GO  
  
RESTORE LOG AdventureWorks  
   FROM AdventureWorksBackups   
   WITH FILE = 4,  
   RECOVERY,   
   STOPATMARK = 'ListPriceUpdate';  
```  
  
## <a name="forcing-a-mark-to-spread-to-other-servers"></a><span data-ttu-id="b40e4-147">強制將標示散佈到其他伺服器</span><span class="sxs-lookup"><span data-stu-id="b40e4-147">Forcing a Mark to Spread to Other Servers</span></span>  
 <span data-ttu-id="b40e4-148">散佈交易時，交易標示名稱並不會自動散發到另一個伺服器。</span><span class="sxs-lookup"><span data-stu-id="b40e4-148">A transaction mark name is not automatically distributed to another server as the transaction spreads there.</span></span> <span data-ttu-id="b40e4-149">若要強制將標示散佈到其他伺服器，必須撰寫一個包含 BEGIN TRAN *name* WITH MARK 陳述式的預存程序。</span><span class="sxs-lookup"><span data-stu-id="b40e4-149">To force the mark to spread to the other servers, a stored procedure must be written that contains a BEGIN TRAN *name* WITH MARK statement.</span></span> <span data-ttu-id="b40e4-150">然後必須在遠端伺服器上原始伺服器的交易範圍內執行這個預存程序。</span><span class="sxs-lookup"><span data-stu-id="b40e4-150">That stored procedure must then be executed on the remote server under the scope of the transaction in the originating server.</span></span>  
  
 <span data-ttu-id="b40e4-151">例如，假設有一個資料分割資料庫存在於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的多個執行個體上。</span><span class="sxs-lookup"><span data-stu-id="b40e4-151">For example, consider a partitioned database that exists on multiple instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="b40e4-152">每一個執行個體上都有一個名為 `coyote`的資料庫。</span><span class="sxs-lookup"><span data-stu-id="b40e4-152">On each instance is a database named `coyote`.</span></span> <span data-ttu-id="b40e4-153">首先，在每個資料庫中建立預存程序，例如 `sp_SetMark`。</span><span class="sxs-lookup"><span data-stu-id="b40e4-153">First, in every database, create a stored procedure, for example, `sp_SetMark`.</span></span>  
  
```sql  
CREATE PROCEDURE sp_SetMark  
@name nvarchar (128)  
AS  
BEGIN TRANSACTION @name WITH MARK  
UPDATE coyote.dbo.Marks SET one = 1  
COMMIT TRANSACTION;  
GO  
```  
  
 <span data-ttu-id="b40e4-154">接下來，建立包含交易的預存程序 `sp_MarkAll` ，它會在每一個資料庫中放入標示。</span><span class="sxs-lookup"><span data-stu-id="b40e4-154">Next, create stored procedure `sp_MarkAll` containing a transaction that places a mark in every database.</span></span> <span data-ttu-id="b40e4-155">`sp_MarkAll` 可以從任何執行個體來執行。</span><span class="sxs-lookup"><span data-stu-id="b40e4-155">`sp_MarkAll` can be run from any of the instances.</span></span>  
  
```sql  
CREATE PROCEDURE sp_MarkAll  
@name nvarchar (128)  
AS  
BEGIN TRANSACTION  
EXEC instance0.coyote.dbo.sp_SetMark @name  
EXEC instance1.coyote.dbo.sp_SetMark @name  
EXEC instance2.coyote.dbo.sp_SetMark @name  
COMMIT TRANSACTION;  
GO  
```  
  
### <a name="two-phase-commit"></a><span data-ttu-id="b40e4-156">兩階段認可</span><span class="sxs-lookup"><span data-stu-id="b40e4-156">Two-Phase Commit</span></span>  
 <span data-ttu-id="b40e4-157">認可分散式交易分為兩階段進行：準備和認可。</span><span class="sxs-lookup"><span data-stu-id="b40e4-157">Committing a distributed transaction occurs in two phases: prepare and commit.</span></span> <span data-ttu-id="b40e4-158">認可標示的交易時，若任何記錄檔中都沒有值得懷疑的交易，就會將標示交易中每個資料庫的認可記錄放在記錄中。</span><span class="sxs-lookup"><span data-stu-id="b40e4-158">When a marked transaction is committed, the commit log record for each database in the marked transaction is placed in the log at a point where there are no in-doubt transactions in any of the logs.</span></span> <span data-ttu-id="b40e4-159">這時候，可以保證不會有任何交易會在一個記錄中出現為已認可，而在另一個記錄中是未認可。</span><span class="sxs-lookup"><span data-stu-id="b40e4-159">At this point, it is guaranteed that there are no transactions that appear as committed in one log, but not committed in another log.</span></span>  
  
 <span data-ttu-id="b40e4-160">以下步驟會在認可標示的交易過程中完成這一點：</span><span class="sxs-lookup"><span data-stu-id="b40e4-160">The following steps accomplish this during the commit of a marked transaction:</span></span>  
  
1.  <span data-ttu-id="b40e4-161">標示交易的準備階段會拖延所有新的準備和認可。</span><span class="sxs-lookup"><span data-stu-id="b40e4-161">Prepare phase of a marking transaction stalls all new prepares and commits.</span></span>  
  
2.  <span data-ttu-id="b40e4-162">只有已完成準備的交易認可才能繼續。</span><span class="sxs-lookup"><span data-stu-id="b40e4-162">Only commits of already prepared transactions are allowed to continue.</span></span>  
  
3.  <span data-ttu-id="b40e4-163">接著標示交易等候所有完成準備的交易逐步完成 (有逾時限制)。</span><span class="sxs-lookup"><span data-stu-id="b40e4-163">Marking transaction then waits for all prepared transactions to drain (with time-out).</span></span>  
  
4.  <span data-ttu-id="b40e4-164">標示的交易完成準備並已認可。</span><span class="sxs-lookup"><span data-stu-id="b40e4-164">Marked transaction is prepared and committed.</span></span>  
  
5.  <span data-ttu-id="b40e4-165">移除新準備與認可的拖延。</span><span class="sxs-lookup"><span data-stu-id="b40e4-165">The stall of new prepares and commits is removed.</span></span>  
  
 <span data-ttu-id="b40e4-166">跨越多個資料庫的標示交易所產生的拖延可能降低伺服器的交易處理效能。</span><span class="sxs-lookup"><span data-stu-id="b40e4-166">The stalls generated by marked transactions that span multiple databases can reduce the transaction processing performance of the server.</span></span>  
  
 <span data-ttu-id="b40e4-167">我們建議您不要執行並行的標示的交易。</span><span class="sxs-lookup"><span data-stu-id="b40e4-167">We recommend that you do not run concurrent marked transactions.</span></span> <span data-ttu-id="b40e4-168">分散式標示交易的認可能因為另一個分散式標示交易同時間認可而產生死結，這是罕見但有可能發生的情況。</span><span class="sxs-lookup"><span data-stu-id="b40e4-168">It is rare but possible for the commit of a distributed marked transaction to deadlock with other distributed marked transactions that are committing at the same time.</span></span> <span data-ttu-id="b40e4-169">如果發生這種狀況，會選擇標示交易作為死結犧牲者，並將它回復。</span><span class="sxs-lookup"><span data-stu-id="b40e4-169">When this happens, the marking transaction is chosen as the deadlock victim and is rolled back.</span></span> <span data-ttu-id="b40e4-170">發生這種錯誤時，應用程式可以重試標示的交易。</span><span class="sxs-lookup"><span data-stu-id="b40e4-170">When this error occurs, the application can retry the marked transaction.</span></span> <span data-ttu-id="b40e4-171">當多個標示的交易同時嘗試認可時，發生死結的可能性就比較高。</span><span class="sxs-lookup"><span data-stu-id="b40e4-171">When multiple marked transactions try to commit concurrently, there is a higher probability of deadlock.</span></span>  
  
## <a name="recovering-to-a-marked-transaction"></a><span data-ttu-id="b40e4-172">復原到標示的交易</span><span class="sxs-lookup"><span data-stu-id="b40e4-172">Recovering to a Marked Transaction</span></span>  
 <span data-ttu-id="b40e4-173">如需如何將包含標示之交易的資料庫復原成特定標示或該標示之前的相關資訊，請參閱 [復原包含標記之異動的相關資料庫](recovery-of-related-databases-that-contain-marked-transaction.md)。</span><span class="sxs-lookup"><span data-stu-id="b40e4-173">For information about how to recover a database that contains marked transactions to or just before a particular mark, see [Recovery of Related  Databases That Contain Marked Transaction](recovery-of-related-databases-that-contain-marked-transaction.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b40e4-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b40e4-174">See Also</span></span>  
 <span data-ttu-id="b40e4-175">[BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-distributed-transaction-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b40e4-175">[BEGIN DISTRIBUTED TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-distributed-transaction-transact-sql) </span></span>  
 <span data-ttu-id="b40e4-176">[系統資料庫的備份與還原 &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b40e4-176">[Back Up and Restore of System Databases &#40;SQL Server&#41;](back-up-and-restore-of-system-databases-sql-server.md) </span></span>  
 <span data-ttu-id="b40e4-177">[BEGIN TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-transaction-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b40e4-177">[BEGIN TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-transaction-transact-sql) </span></span>  
 <span data-ttu-id="b40e4-178">[套用交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b40e4-178">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="b40e4-179">[完整資料庫備份 &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b40e4-179">[Full Database Backups &#40;SQL Server&#41;](full-database-backups-sql-server.md) </span></span>  
 <span data-ttu-id="b40e4-180">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="b40e4-180">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="b40e4-181">復原包含標示之交易的相關資料庫</span><span class="sxs-lookup"><span data-stu-id="b40e4-181">Recovery of Related  Databases That Contain Marked Transaction</span></span>](recovery-of-related-databases-that-contain-marked-transaction.md)  
  
  
