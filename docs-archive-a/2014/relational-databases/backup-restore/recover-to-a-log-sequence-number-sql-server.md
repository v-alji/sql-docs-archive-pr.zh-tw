---
title: 復原到記錄序號 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- log sequence numbers [SQL Server]
- STOPBEFOREMARK option [RESTORE statement]
- STOPATMARK option [RESTORE statement]
- point in time recovery [SQL Server]
- restoring databases [SQL Server], point in time
- recovery [SQL Server], databases
- restoring [SQL Server], point in time
- LSNs
- database recovery [SQL Server]
- database restores [SQL Server], point in time
ms.assetid: f7b3de5b-198d-448d-8c71-1cdd9239676c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 4df55c3468fc009d86cffd58a837d6935f5ce14b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598474"
---
# <a name="recover-to-a-log-sequence-number-sql-server"></a><span data-ttu-id="29825-102">復原到記錄序號 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="29825-102">Recover to a Log Sequence Number (SQL Server)</span></span>
  <span data-ttu-id="29825-103">本主題僅與使用完整或大量記錄復原模式的資料庫相關。</span><span class="sxs-lookup"><span data-stu-id="29825-103">This topic is relevant only for databases that are using the full or bulk-logged recovery models.</span></span>  
  
 <span data-ttu-id="29825-104">您可使用記錄序號 (LSN) 定義還原作業的復原點。</span><span class="sxs-lookup"><span data-stu-id="29825-104">You can use a log sequence number (LSN) to define the recovery point for a restore operation.</span></span> <span data-ttu-id="29825-105">但是，這是為工具供應商所提供的特定功能，未必普遍適用。</span><span class="sxs-lookup"><span data-stu-id="29825-105">However, this is a specialized feature that is intended for tools vendors and is unlikely to be generally useful.</span></span>  
  
##  <a name="overview-of-log-sequence-numbers"></a><a name="LSNs"></a> <span data-ttu-id="29825-106">記錄序號概觀</span><span class="sxs-lookup"><span data-stu-id="29825-106">Overview of Log Sequence Numbers</span></span>  
 <span data-ttu-id="29825-107">執行 RESTORE 順序期間，在內部會使用 LSN 追蹤已還原之資料的時間點。</span><span class="sxs-lookup"><span data-stu-id="29825-107">LSNs are used internally during a RESTORE sequence to track the point in time to which data has been restored.</span></span> <span data-ttu-id="29825-108">還原備份時，資料會還原到備份執行時間點所對應的 LSN；</span><span class="sxs-lookup"><span data-stu-id="29825-108">When a backup is restored, the data is restored to the LSN corresponding to the point in time at which the backup was taken.</span></span> <span data-ttu-id="29825-109">差異與記錄備份則可將已還原的資料庫推往更後面的時間點，因為它們對應到較高的 LSN。</span><span class="sxs-lookup"><span data-stu-id="29825-109">Differential and log backups advance the restored database to a later time, which corresponds to a higher LSN.</span></span>  
  
 <span data-ttu-id="29825-110">交易記錄中的每一筆記錄都由記錄序號 (LSN) 加以唯一識別。</span><span class="sxs-lookup"><span data-stu-id="29825-110">Every record in the transaction log is uniquely identified by a log sequence number (LSN).</span></span> <span data-ttu-id="29825-111">LSN 是經過排序的，因此如果 LSN2 大於 LSN1，表示 LSN2 所參考記錄中描述的變更，發生在記錄 LSN1 所描述的變更之後。</span><span class="sxs-lookup"><span data-stu-id="29825-111">LSNs are ordered such that if LSN2 is greater than LSN1, the change described by the log record referred to by LSN2 occurred after the change described by the log record LSN.</span></span>  
  
 <span data-ttu-id="29825-112">發生重大事件時的記錄 LSN，有助於建構正確的還原順序。</span><span class="sxs-lookup"><span data-stu-id="29825-112">The LSN of a log record at which a significant event occurred can be useful for constructing correct restore sequences.</span></span> <span data-ttu-id="29825-113">因為 Lsn 經過排序，所以可以進行相等和不相等的比較 (也就是、、 **\<**, **>** **=** **\<=**, **>=**) 。</span><span class="sxs-lookup"><span data-stu-id="29825-113">Because LSNs are ordered, they can be compared for equality and inequality (that is, **\<**, **>**, **=**, **\<=**, **>=**).</span></span> <span data-ttu-id="29825-114">要建構還原順序時，這種比較很有用。</span><span class="sxs-lookup"><span data-stu-id="29825-114">Such comparisons are useful when constructing restore sequences.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="29825-115">LSN 是資料類型 `numeric`(25,0) 的值。</span><span class="sxs-lookup"><span data-stu-id="29825-115">LSNs are values of data type `numeric`(25,0).</span></span> <span data-ttu-id="29825-116">數學運算 (例如：加、減) 在此沒有意義，且絕不能搭配 LSN 使用。</span><span class="sxs-lookup"><span data-stu-id="29825-116">Arithmetic operations (for example, addition or subtraction) are not meaningful and must not be used with LSNs.</span></span>  
  

  
## <a name="viewing-lsns-used-by-backup-and-restore"></a><span data-ttu-id="29825-117">檢視備份與還原所使用的 LSN</span><span class="sxs-lookup"><span data-stu-id="29825-117">Viewing LSNs Used by Backup and Restore</span></span>  
 <span data-ttu-id="29825-118">特定備份與還原事件發生時的記錄 LSN，可透過下列一種或多種方式進行檢視：</span><span class="sxs-lookup"><span data-stu-id="29825-118">The LSN of a log record at which a given backup and restore event occurred is viewable using one or more of the following:</span></span>  
  
-   [<span data-ttu-id="29825-119">backupset</span><span class="sxs-lookup"><span data-stu-id="29825-119">backupset</span></span>](/sql/relational-databases/system-tables/backupset-transact-sql)  
  
-   [<span data-ttu-id="29825-120">backupfile</span><span class="sxs-lookup"><span data-stu-id="29825-120">backupfile</span></span>](/sql/relational-databases/system-tables/backupfile-transact-sql)  
  
-   <span data-ttu-id="29825-121">[sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)； [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="29825-121">[sys.database_files](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql); [sys.master_files](/sql/relational-databases/system-catalog-views/sys-master-files-transact-sql)</span></span>  
  
-   [<span data-ttu-id="29825-122">RESTORE HEADERONLY</span><span class="sxs-lookup"><span data-stu-id="29825-122">RESTORE HEADERONLY</span></span>](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)  
  
-   [<span data-ttu-id="29825-123">RESTORE FILELISTONLY</span><span class="sxs-lookup"><span data-stu-id="29825-123">RESTORE FILELISTONLY</span></span>](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)  
  
> [!NOTE]  
>  <span data-ttu-id="29825-124">LSN 也會出現在某些訊息文字中。</span><span class="sxs-lookup"><span data-stu-id="29825-124">LSNs also appear in some message texts.</span></span>  
  
## <a name="transact-sql-syntax-for-restoring-to-an-lsn"></a><span data-ttu-id="29825-125">還原至 LSN 所用的 Transact-SQL 語法</span><span class="sxs-lookup"><span data-stu-id="29825-125">Transact-SQL Syntax for Restoring to an LSN</span></span>  
 <span data-ttu-id="29825-126">使用 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 陳述式，您可以在 LSN 上或剛好就在它之前停止，如下所述：</span><span class="sxs-lookup"><span data-stu-id="29825-126">By using a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, you can stop at or immediately before the LSN, as follows:</span></span>  
  
-   <span data-ttu-id="29825-127">使用 WITH STOPATMARK **='** lsn: _<lsn_number>_ **'** 子句，其中 lsn: *\<lsnNumber>* 是會指定包含所指定的 LSN 的記錄檔記錄為復原點的字串。</span><span class="sxs-lookup"><span data-stu-id="29825-127">Use the WITH STOPATMARK **='** lsn:_<lsn_number>_**'** clause, where lsn:*\<lsnNumber>* is a string that specifies that the log record that contains the specified LSN is the recovery point.</span></span>  
  
     <span data-ttu-id="29825-128">STOPATMARK 會向前復原到 LSN，並且將該筆記錄納入向前復原中。</span><span class="sxs-lookup"><span data-stu-id="29825-128">STOPATMARK roll forwards to the LSN and includes that log record in the roll forward.</span></span>  
  
-   <span data-ttu-id="29825-129">使用 WITH STOPBEFOREMARK **='** lsn: _<lsn_number>_ **'** 子句，其中 lsn: *\<lsnNumber>* 是會指定緊接在包含指定的 LSN 號碼的記錄檔記錄之前的記錄檔記錄為復原點的字串。</span><span class="sxs-lookup"><span data-stu-id="29825-129">Use the WITH STOPBEFOREMARK **='** lsn:_<lsn_number>_**'** clause, where lsn:*\<lsnNumber>* is a string that specifies that the log record immediately before the log record that contains the specified LSN number is the recovery point.</span></span>  
  
     <span data-ttu-id="29825-130">STOPBEFOREMARK 會向前復原到 LSN，並且從向前復原中排除該筆記錄。</span><span class="sxs-lookup"><span data-stu-id="29825-130">STOPBEFOREMARK rolls forward to the LSN and excludes that log record from the roll forward.</span></span>  
  
 <span data-ttu-id="29825-131">通常會選取要納入或排除的特定交易。</span><span class="sxs-lookup"><span data-stu-id="29825-131">Typically, a specific transaction is selected to be included or excluded.</span></span> <span data-ttu-id="29825-132">實際上雖不需要這麼做，但指定的記錄是交易認可記錄。</span><span class="sxs-lookup"><span data-stu-id="29825-132">Although not required, in practice, the specified log record is a transaction-commit record.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="29825-133">範例</span><span class="sxs-lookup"><span data-stu-id="29825-133">Examples</span></span>  
 <span data-ttu-id="29825-134">下列範例假設 `AdventureWorks` 資料庫已變更為使用完整復原模式。</span><span class="sxs-lookup"><span data-stu-id="29825-134">The following example assumes that the `AdventureWorks` database has been changed to use the full recovery model.</span></span>  
  
```  
RESTORE LOG AdventureWorks FROM DISK = 'c:\adventureworks_log.bak'   
WITH STOPATMARK = 'lsn:15000000040000037'  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="29825-135">相關工作</span><span class="sxs-lookup"><span data-stu-id="29825-135">Related Tasks</span></span>  
  
-   [<span data-ttu-id="29825-136">還原資料庫備份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="29825-136">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="29825-137">備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="29825-137">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="29825-138">還原交易記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="29825-138">Restore a Transaction Log Backup &#40;SQL Server&#41;</span></span>](restore-a-transaction-log-backup-sql-server.md)  
  
-   [<span data-ttu-id="29825-139">在完整復原模式下將資料庫還原至失敗點 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="29825-139">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="29825-140">還原資料庫至標示的交易 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="29825-140">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="29825-141">將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="29825-141">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="29825-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29825-142">See Also</span></span>  
 <span data-ttu-id="29825-143">[套用交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="29825-143">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 <span data-ttu-id="29825-144">[交易記錄 &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="29825-144">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="29825-145">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="29825-145">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
  
