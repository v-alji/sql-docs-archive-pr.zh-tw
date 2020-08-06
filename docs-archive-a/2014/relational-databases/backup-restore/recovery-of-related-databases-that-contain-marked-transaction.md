---
title: 復原包含標記之異動的相關資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- transaction logs [SQL Server], marks
- STOPBEFOREMARK option [RESTORE statement]
- STOPATMARK option [RESTORE statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
- recovery [SQL Server], databases
- restoring [SQL Server], point in time
- transactions [SQL Server], recovering to a mark
- database recovery [SQL Server]
- marked transactions [SQL Server], restoring
- database restores [SQL Server], point in time
ms.assetid: 77a0d9c0-978a-4891-8b0d-a4256c81c3f8
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: b968322f92c7a135adb5fd0733b5774e7562bc39
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705201"
---
# <a name="recovery-of-related--databases-that-contain-marked-transaction"></a><span data-ttu-id="8d79e-102">復原包含標記之異動的相關資料庫</span><span class="sxs-lookup"><span data-stu-id="8d79e-102">Recovery of Related  Databases That Contain Marked Transaction</span></span>
  <span data-ttu-id="8d79e-103">這個主題僅與包含標示的交易，且使用完整模式或大量記錄復原模式的資料庫有關。</span><span class="sxs-lookup"><span data-stu-id="8d79e-103">This topic is relevant only for databases that contain marked transactions and that use the full or bulk-logged recovery models.</span></span>  
  
 <span data-ttu-id="8d79e-104">如需還原至特定復原點之需求的相關資訊，請參閱 [將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)。</span><span class="sxs-lookup"><span data-stu-id="8d79e-104">For information about the requirements for restoring to a specific recovery point, see [Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8d79e-105">支援將具名標示插入交易記錄，以允許復原至特定的標示。</span><span class="sxs-lookup"><span data-stu-id="8d79e-105">supports inserting named marks into the transaction log to allow recovery to that specific mark.</span></span> <span data-ttu-id="8d79e-106">記錄標示是針對交易而設，並且只有在其相關的交易認可時才會插入。</span><span class="sxs-lookup"><span data-stu-id="8d79e-106">Log marks are transaction specific and are inserted only if their associated transaction commits.</span></span> <span data-ttu-id="8d79e-107">如此一來，標示可以結合特定工作，您也就可以復原至包含或排除此工作的某一點。</span><span class="sxs-lookup"><span data-stu-id="8d79e-107">As a result, marks can be tied to specific work, and you can recover to a point that includes or excludes this work.</span></span>  
  
 <span data-ttu-id="8d79e-108">將具名標示插入交易記錄之前，請考慮以下幾點：</span><span class="sxs-lookup"><span data-stu-id="8d79e-108">Before you insert named marks into the transaction log, consider the following:</span></span>  
  
-   <span data-ttu-id="8d79e-109">因為交易標示須耗用記錄空間，所以除非它們在資料庫復原策略中扮演重要的角色，否則不應使用交易標示。</span><span class="sxs-lookup"><span data-stu-id="8d79e-109">Because transaction marks consume log space, use them only for transactions that play a significant role in the database recovery strategy.</span></span>  
  
-   <span data-ttu-id="8d79e-110">標示的交易認可之後，會在 [msdb](/sql/relational-databases/system-tables/logmarkhistory-transact-sql) 的 **logmarkhistory**資料表中插入一個資料列。</span><span class="sxs-lookup"><span data-stu-id="8d79e-110">After a marked transaction commits, a row is inserted in the [logmarkhistory](/sql/relational-databases/system-tables/logmarkhistory-transact-sql) table in **msdb**.</span></span>  
  
-   <span data-ttu-id="8d79e-111">如果標示交易跨越同一資料庫伺服器或不同伺服器上的多個資料庫，則標示會記錄在所有受影響的資料庫之記錄中。</span><span class="sxs-lookup"><span data-stu-id="8d79e-111">If a marked transaction spans multiple databases on the same database server or on different servers, the marks must be recorded in the logs of all the affected databases.</span></span> <span data-ttu-id="8d79e-112">如需詳細資訊，請參閱 [使用標示的異動以一致的方式復原相關資料庫 &#40;完整復原模式&#41;](use-marked-transactions-to-recover-related-databases-consistently.md)。</span><span class="sxs-lookup"><span data-stu-id="8d79e-112">For more information, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8d79e-113">如需詳細資訊，請參閱 [使用標示的異動以一致的方式復原相關資料庫 &#40;完整復原模式&#41;](use-marked-transactions-to-recover-related-databases-consistently.md)。</span><span class="sxs-lookup"><span data-stu-id="8d79e-113">For information about how to mark transactions, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
## <a name="transact-sql-syntax-for-inserting-named-marks-into-a-transaction-log"></a><span data-ttu-id="8d79e-114">將具名標示插入交易記錄檔中的 Transact-SQL 語法</span><span class="sxs-lookup"><span data-stu-id="8d79e-114">Transact-SQL Syntax for Inserting Named Marks into a Transaction Log</span></span>  
 <span data-ttu-id="8d79e-115">若要將標示插入交易記錄，請使用 [BEGIN TRANSACTION](/sql/t-sql/language-elements/begin-transaction-transact-sql) 陳述式和 WITH MARK [*description*] 子句。</span><span class="sxs-lookup"><span data-stu-id="8d79e-115">To insert marks into the transaction logs, use the [BEGIN TRANSACTION](/sql/t-sql/language-elements/begin-transaction-transact-sql) statement and the WITH MARK [*description*] clause.</span></span> <span data-ttu-id="8d79e-116">標示和交易的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="8d79e-116">The mark is named the same as the transaction.</span></span> <span data-ttu-id="8d79e-117">選擇性的 *description* 是標示的文字描述，而不是標示名稱。</span><span class="sxs-lookup"><span data-stu-id="8d79e-117">The optional *description* is a textual description of the mark, not the mark name.</span></span> <span data-ttu-id="8d79e-118">例如，在下列 `BEGIN TRANSACTION` 陳述式中建立的交易及標示名稱為 `Tx1`：</span><span class="sxs-lookup"><span data-stu-id="8d79e-118">For example, the name of both the transaction and the mark that is created in the following `BEGIN TRANSACTION` statement is `Tx1`:</span></span>  
  
```wmimof  
BEGIN TRANSACTION Tx1 WITH MARK 'not the mark name, just a description'    
```  
  
 <span data-ttu-id="8d79e-119">交易記錄檔中會記錄標示名稱 (交易名稱)、描述、資料庫、使用者、`datetime` 資訊與記錄序號 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="8d79e-119">The transaction log records the mark name (transaction name), description, database, user, `datetime` information, and the log sequence number (LSN).</span></span> <span data-ttu-id="8d79e-120">`datetime` 資訊要與標示名稱一起使用，才能唯一識別標示。</span><span class="sxs-lookup"><span data-stu-id="8d79e-120">The `datetime` information is used with the mark name to uniquely identify the mark.</span></span>  
  
 <span data-ttu-id="8d79e-121">如需如何將標示插入跨越多個資料庫之交易的相關資訊，請參閱 [使用標示的異動以一致的方式復原相關資料庫 &#40;完整復原模式&#41;](use-marked-transactions-to-recover-related-databases-consistently.md)。</span><span class="sxs-lookup"><span data-stu-id="8d79e-121">For information about how to insert a mark into a transaction that spans multiple databases, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
## <a name="transact-sql-syntax-for-recovering-to-a-mark"></a><span data-ttu-id="8d79e-122">復原標示的 Transact-SQL 語法</span><span class="sxs-lookup"><span data-stu-id="8d79e-122">Transact-SQL Syntax for Recovering to a Mark</span></span>  
 <span data-ttu-id="8d79e-123">針對標示的交易使用[RESTORE LOG](/sql/t-sql/statements/restore-statements-transact-sql)陳述式時，您可以使用下列其中一個子句，以在標示上或標示當前停止：</span><span class="sxs-lookup"><span data-stu-id="8d79e-123">When you target a marked transaction by using a[RESTORE LOG](/sql/t-sql/statements/restore-statements-transact-sql)statement, you can use one the following clauses to stop at or immediately before the mark:</span></span>  
  
-   <span data-ttu-id="8d79e-124">使用 WITH STOPATMARK = **' *`<mark_name>`* '** 子句，以指定標示的交易為復原點。</span><span class="sxs-lookup"><span data-stu-id="8d79e-124">Use the WITH STOPATMARK = **'*`<mark_name>`*'** clause to specify that the marked transaction is the recovery point.</span></span>  
  
     <span data-ttu-id="8d79e-125">STOPATMARK 可向前復原標示，並將已標示的交易納入向前復原。</span><span class="sxs-lookup"><span data-stu-id="8d79e-125">STOPATMARK rolls forward to the mark and includes the marked transaction in the roll forward.</span></span>  
  
-   <span data-ttu-id="8d79e-126">使用 WITH STOPBEFOREMARK = **' *`<mark_name>`* '** 子句，以指定在標記之前的記錄檔記錄是復原點。</span><span class="sxs-lookup"><span data-stu-id="8d79e-126">Use the WITH STOPBEFOREMARK = **'*`<mark_name>`*'** clause to specify that the log record that is immediately before the mark is the recovery point.</span></span>  
  
     <span data-ttu-id="8d79e-127">STOPBEFOREMARK 可向前復原標示，並從向前復原中排除已標示的交易。</span><span class="sxs-lookup"><span data-stu-id="8d79e-127">STOPBEFOREMARK rolls forward to the mark and excludes marked the transaction from the roll forward.</span></span>  
  
 <span data-ttu-id="8d79e-128">STOPATMARK 與 STOPBEFOREMARK 選項都支援選擇性的 AFTER *datetime* 子句。</span><span class="sxs-lookup"><span data-stu-id="8d79e-128">The STOPATMARK and STOPBEFOREMARK options both support an optional AFTER *datetime* clause.</span></span> <span data-ttu-id="8d79e-129">使用 *datetime* 時，標示名稱不必是唯一的。</span><span class="sxs-lookup"><span data-stu-id="8d79e-129">When *datetime* is used, mark names do not have to be unique.</span></span>  
  
 <span data-ttu-id="8d79e-130">如果省略 AFTER *datetime* ，向前復原會停在具有指定名稱的第一個標示。</span><span class="sxs-lookup"><span data-stu-id="8d79e-130">If AFTER *datetime* is omitted, roll forward stops at the first mark that has the specified name.</span></span> <span data-ttu-id="8d79e-131">如果指定 AFTER *datetime* ，向前復原會在 *datetime*時或之後，停止於具有指定名稱的第一個標示。</span><span class="sxs-lookup"><span data-stu-id="8d79e-131">If AFTER *datetime* is specified, roll forward stops at the first mark that has the specified name, exactly at or after *datetime*.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8d79e-132">如同所有的時間點還原作業，當資料庫進行大量記錄的作業時，不允許其復原至標示。</span><span class="sxs-lookup"><span data-stu-id="8d79e-132">As in all point-in-time restore operations, recovering to a mark is disallowed when the database is undergoing operations that are bulk-logged.</span></span>  
  
 <span data-ttu-id="8d79e-133">**若要還原標示的交易**</span><span class="sxs-lookup"><span data-stu-id="8d79e-133">**To restore to a marked transaction**</span></span>  
  
 [<span data-ttu-id="8d79e-134">還原資料庫至標示的交易 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="8d79e-134">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
 [<span data-ttu-id="8d79e-135">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="8d79e-135">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
### <a name="preparing-the-log-backups"></a><span data-ttu-id="8d79e-136">準備記錄備份</span><span class="sxs-lookup"><span data-stu-id="8d79e-136">Preparing the Log Backups</span></span>  
 <span data-ttu-id="8d79e-137">就此範例而言，這些相關資料庫的適當備份策略如下：</span><span class="sxs-lookup"><span data-stu-id="8d79e-137">For this example, an appropriate backup strategy for these related databases would be the following:</span></span>  
  
1.  <span data-ttu-id="8d79e-138">兩個資料庫均使用完整復原模式。</span><span class="sxs-lookup"><span data-stu-id="8d79e-138">Use the full recovery model for both databases.</span></span>  
  
2.  <span data-ttu-id="8d79e-139">建立每一個資料庫的完整備份。</span><span class="sxs-lookup"><span data-stu-id="8d79e-139">Create a full backup of each database.</span></span>  
  
     <span data-ttu-id="8d79e-140">可循序或同時備份這些資料庫。</span><span class="sxs-lookup"><span data-stu-id="8d79e-140">The databases can be backed up sequentially or simultaneously.</span></span>  
  
3.  <span data-ttu-id="8d79e-141">在備份交易記錄之前，先標示要在所有資料庫中執行的交易。</span><span class="sxs-lookup"><span data-stu-id="8d79e-141">Before backing up the transaction log, mark a transaction that executes in all databases.</span></span> <span data-ttu-id="8d79e-142">如需如何建立標示的異動的相關資訊，請參閱 [使用標示的異動以一致的方式復原相關資料庫 &#40;完整復原模式&#41;](use-marked-transactions-to-recover-related-databases-consistently.md)。</span><span class="sxs-lookup"><span data-stu-id="8d79e-142">For information about how to create the marked transactions, see [Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md).</span></span>  
  
4.  <span data-ttu-id="8d79e-143">備份每個資料庫的交易記錄。</span><span class="sxs-lookup"><span data-stu-id="8d79e-143">Back up the transaction log on each database.</span></span>  
  
### <a name="recovering-the-database-to-a-marked-transaction"></a><span data-ttu-id="8d79e-144">將資料庫復原至標示的交易</span><span class="sxs-lookup"><span data-stu-id="8d79e-144">Recovering the Database to a Marked Transaction</span></span>  
 <span data-ttu-id="8d79e-145">**若要還原備份**</span><span class="sxs-lookup"><span data-stu-id="8d79e-145">**To restore the backup**</span></span>  
  
1.  <span data-ttu-id="8d79e-146">盡可能建立未受損資料庫的 [結尾記錄備份](tail-log-backups-sql-server.md) 。</span><span class="sxs-lookup"><span data-stu-id="8d79e-146">Create [tail-log backups](tail-log-backups-sql-server.md) of the undamaged databases, if possible.</span></span>  
  
2.  <span data-ttu-id="8d79e-147">還原每個資料庫的最新完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="8d79e-147">Restore the most recent full database backup of each database.</span></span>  
  
3.  <span data-ttu-id="8d79e-148">識別所有交易記錄備份中可用的最新標示交易。</span><span class="sxs-lookup"><span data-stu-id="8d79e-148">Identify the most recent marked transaction that is available in all of the transaction log backups.</span></span> <span data-ttu-id="8d79e-149">此資訊是儲存在每一個伺服器上 **msdb** 資料庫的 **logmarkhistory** 資料表中。</span><span class="sxs-lookup"><span data-stu-id="8d79e-149">This information is stored in the **logmarkhistory** table in the **msdb** database on each server.</span></span>  
  
4.  <span data-ttu-id="8d79e-150">識別所有包含此標示之相關資料庫的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="8d79e-150">Identify the log backups for all related databases that contain this mark.</span></span>  
  
5.  <span data-ttu-id="8d79e-151">還原每個記錄檔備份，停在標示的交易。</span><span class="sxs-lookup"><span data-stu-id="8d79e-151">Restore each log backup, stopping at the marked transaction.</span></span>  
  
6.  <span data-ttu-id="8d79e-152">復原每個資料庫。</span><span class="sxs-lookup"><span data-stu-id="8d79e-152">Recover each database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d79e-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8d79e-153">See Also</span></span>  
 <span data-ttu-id="8d79e-154">[BEGIN TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-transaction-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d79e-154">[BEGIN TRANSACTION &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/begin-transaction-transact-sql) </span></span>  
 <span data-ttu-id="8d79e-155">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="8d79e-155">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="8d79e-156">[套用交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8d79e-156">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="8d79e-157">[使用標示的異動以一致的方式復原相關資料庫 &#40;完整復原模式&#41;](use-marked-transactions-to-recover-related-databases-consistently.md) </span><span class="sxs-lookup"><span data-stu-id="8d79e-157">[Use Marked Transactions to Recover Related Databases Consistently &#40;Full Recovery Model&#41;](use-marked-transactions-to-recover-related-databases-consistently.md) </span></span>  
 <span data-ttu-id="8d79e-158">[還原和復原概觀 &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="8d79e-158">[Restore and Recovery Overview &#40;SQL Server&#41;](restore-and-recovery-overview-sql-server.md) </span></span>  
 <span data-ttu-id="8d79e-159">[將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="8d79e-159">[Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span></span>  
 [<span data-ttu-id="8d79e-160">規劃和執行還原順序 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="8d79e-160">Plan and Perform Restore Sequences &#40;Full Recovery Model&#41;</span></span>](plan-and-perform-restore-sequences-full-recovery-model.md)  
  
  
