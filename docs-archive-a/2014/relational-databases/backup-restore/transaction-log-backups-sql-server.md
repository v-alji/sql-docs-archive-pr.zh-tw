---
title: 交易記錄備份 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up [SQL Server], transaction logs
- transaction log backups [SQL Server], creating
- log backups [SQL Server[
- transaction log backups [SQL Server], sequencing
ms.assetid: f4a44a35-0f44-4a42-91d5-d73ac658a3b0
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 752447d6c38a2df0fcbdce72fbba12edd7a9eeb3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703018"
---
# <a name="transaction-log-backups-sql-server"></a><span data-ttu-id="b8943-102">交易記錄備份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="b8943-102">Transaction Log Backups (SQL Server)</span></span>
  <span data-ttu-id="b8943-103">本主題只與使用完整或大量記錄復原模式的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫有關。</span><span class="sxs-lookup"><span data-stu-id="b8943-103">This topic is relevant only for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] databases that are using the full or bulk-logged recovery models.</span></span> <span data-ttu-id="b8943-104">本主題討論 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫的交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="b8943-104">This topic discusses backing up the transaction log of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="b8943-105">您至少要在建立任何記錄備份之前，必須建立一個完整備份。</span><span class="sxs-lookup"><span data-stu-id="b8943-105">Minimally, you must have created at least one full backup before you can create any log backups.</span></span> <span data-ttu-id="b8943-106">之後，除非交易記錄已正在備份中，否則任何時候皆可以備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="b8943-106">After that, the transaction log can be backed up at any time unless the log is already being backed up.</span></span> <span data-ttu-id="b8943-107">建議您時常進行記錄備份，以將工作損失風險降至最低，同時也讓記錄能夠截斷。</span><span class="sxs-lookup"><span data-stu-id="b8943-107">We recommend that you take log backups frequently, both to minimize work loss exposure and to truncate the transaction log.</span></span> <span data-ttu-id="b8943-108">一般而言，資料庫管理員有時會建立完整資料庫備份，例如每週一次；並且會選擇性地於較短的間隔建立一系列差異資料庫備份，例如每日一次。</span><span class="sxs-lookup"><span data-stu-id="b8943-108">Typically, a database administrator creates a full database backup occasionally, such as weekly, and, optionally, creates a series of differential database backup at a shorter interval, such as daily.</span></span> <span data-ttu-id="b8943-109">另外在資料庫備份之中，資料庫管理員會為交易記錄採取高頻率備份，例如每 10 分鐘一次。</span><span class="sxs-lookup"><span data-stu-id="b8943-109">Independently of the database backups, the database administrator backs up the transaction log at frequent intervals, such as every 10 minutes.</span></span> <span data-ttu-id="b8943-110">每種備份類型的最佳間隔取決於幾項因素，如資料的重要性、資料庫大小及伺服器負載。</span><span class="sxs-lookup"><span data-stu-id="b8943-110">For a given type of backup, the optimal interval depends on factors such as the importance of the data, the size of the database, and the workload of the server.</span></span>  
  
 <span data-ttu-id="b8943-111">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="b8943-111">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="b8943-112">記錄備份順序的運作方式</span><span class="sxs-lookup"><span data-stu-id="b8943-112">How a Sequence of Log Backups Works</span></span>](#LogBackupSequence)  
  
-   [<span data-ttu-id="b8943-113">建議</span><span class="sxs-lookup"><span data-stu-id="b8943-113">Recommendations</span></span>](#Recommendations)  
  
-   [<span data-ttu-id="b8943-114">相關工作</span><span class="sxs-lookup"><span data-stu-id="b8943-114">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="b8943-115">相關內容</span><span class="sxs-lookup"><span data-stu-id="b8943-115">Related Content</span></span>](#RelatedContent)  
  
##  <a name="how-a-sequence-of-log-backups-works"></a><a name="LogBackupSequence"></a><span data-ttu-id="b8943-116">記錄備份順序的運作方式</span><span class="sxs-lookup"><span data-stu-id="b8943-116">How a Sequence of Log Backups Works</span></span>  
 <span data-ttu-id="b8943-117">交易記錄備份 *「記錄檔鏈結」* (Log chain) 的順序與資料備份無關。</span><span class="sxs-lookup"><span data-stu-id="b8943-117">The sequence of transaction log backups *log chain* is independent of data backups.</span></span> <span data-ttu-id="b8943-118">例如，假設發生以下一連串事件：</span><span class="sxs-lookup"><span data-stu-id="b8943-118">For example, assume the following sequence of events.</span></span>  
  
|<span data-ttu-id="b8943-119">Time</span><span class="sxs-lookup"><span data-stu-id="b8943-119">Time</span></span>|<span data-ttu-id="b8943-120">事件</span><span class="sxs-lookup"><span data-stu-id="b8943-120">Event</span></span>|  
|----------|-----------|  
|<span data-ttu-id="b8943-121">上午 8:00</span><span class="sxs-lookup"><span data-stu-id="b8943-121">8:00 A.M.</span></span>|<span data-ttu-id="b8943-122">備份資料庫。</span><span class="sxs-lookup"><span data-stu-id="b8943-122">Back up database.</span></span>|  
|<span data-ttu-id="b8943-123">中午</span><span class="sxs-lookup"><span data-stu-id="b8943-123">Noon</span></span>|<span data-ttu-id="b8943-124">備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="b8943-124">Back up transaction log.</span></span>|  
|<span data-ttu-id="b8943-125">下午 4:00</span><span class="sxs-lookup"><span data-stu-id="b8943-125">4:00 P.M.</span></span>|<span data-ttu-id="b8943-126">備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="b8943-126">Back up transaction log.</span></span>|  
|<span data-ttu-id="b8943-127">下午 6:00</span><span class="sxs-lookup"><span data-stu-id="b8943-127">6:00 P.M.</span></span>|<span data-ttu-id="b8943-128">備份資料庫。</span><span class="sxs-lookup"><span data-stu-id="b8943-128">Back up database.</span></span>|  
|<span data-ttu-id="b8943-129">下午 8:00</span><span class="sxs-lookup"><span data-stu-id="b8943-129">8:00 P.M.</span></span>|<span data-ttu-id="b8943-130">備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="b8943-130">Back up transaction log.</span></span>|  
  
 <span data-ttu-id="b8943-131">此交易記錄備份建立於下午 8:00。</span><span class="sxs-lookup"><span data-stu-id="b8943-131">The transaction log backup created at 8:00 P.M.</span></span> <span data-ttu-id="b8943-132">其交易記錄自下午 4:00 起</span><span class="sxs-lookup"><span data-stu-id="b8943-132">contains transaction log records from 4:00 P.M.</span></span> <span data-ttu-id="b8943-133">至下午 8:00 止，涵蓋整個建立於下午 6:00 之資料庫備份的時間。</span><span class="sxs-lookup"><span data-stu-id="b8943-133">through 8:00 P.M., spanning the time when the full database backup was created at 6:00 P.M.</span></span> <span data-ttu-id="b8943-134">異動記錄備份的順序是連續的，從建立於上午 8:00 的初始完整資料庫備份開始，</span><span class="sxs-lookup"><span data-stu-id="b8943-134">The sequence of transaction log backups is continuous from the initial full database backup created at 8:00 A.M.</span></span> <span data-ttu-id="b8943-135">至最後一份建立於下午 8:00 的異動記錄備份為止。</span><span class="sxs-lookup"><span data-stu-id="b8943-135">to the last transaction log backup created at 8:00 P.M.</span></span> <span data-ttu-id="b8943-136">如需有關如何套用這些記錄備份的資訊，請參閱 [套用交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md)中的範例。</span><span class="sxs-lookup"><span data-stu-id="b8943-136">For information about how to apply these log backups, see the example in [Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md).</span></span>  
  
##  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="b8943-137">建議</span><span class="sxs-lookup"><span data-stu-id="b8943-137">Recommendations</span></span>  
  
-   <span data-ttu-id="b8943-138">如果異動記錄損毀，則最近一次有效備份之後所執行的工作都會遺失。</span><span class="sxs-lookup"><span data-stu-id="b8943-138">If a transaction log is damaged, work that is performed since the most recent valid backup is lost.</span></span> <span data-ttu-id="b8943-139">因此，我們強烈建議您將記錄檔存放於容錯的儲存體中。</span><span class="sxs-lookup"><span data-stu-id="b8943-139">Therefore we strongly recommend that you put your log files on fault-tolerant storage.</span></span>  
  
-   <span data-ttu-id="b8943-140">若資料庫損毀或您準備還原資料庫時，建議您建立 [結尾記錄備份](tail-log-backups-sql-server.md) ，使您可以將資料庫還原至目前的時間點。</span><span class="sxs-lookup"><span data-stu-id="b8943-140">If a database is damaged or you are about to restore the database, we recommend that you create a [tail-log backup](tail-log-backups-sql-server.md) to enable you to restore the database to the current point in time.</span></span>  
  
-   <span data-ttu-id="b8943-141">根據預設，每項成功的備份作業都會在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔與系統事件記錄檔中，加入一個項目。</span><span class="sxs-lookup"><span data-stu-id="b8943-141">By default, every successful backup operation adds an entry in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log and in the system event log.</span></span> <span data-ttu-id="b8943-142">如果您經常備份記錄檔，這些成功訊息可能會快速累積，因而產生龐大的錯誤記錄檔，讓您難以尋找其他訊息。</span><span class="sxs-lookup"><span data-stu-id="b8943-142">If back up the log very frequently, these success messages accumulate quickly, resulting in huge error logs that can make finding other messages difficult.</span></span> <span data-ttu-id="b8943-143">在這類情況下，如果沒有任何指令碼相依於這些記錄項目，您就可以使用追蹤旗標 3226 來隱藏這些記錄項目。</span><span class="sxs-lookup"><span data-stu-id="b8943-143">In such cases you can suppress these log entries by using trace flag 3226 if none of your scripts depend on those entries.</span></span> <span data-ttu-id="b8943-144">如需詳細資訊，請參閱[追蹤旗標 &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="b8943-144">For more information, see [Trace Flags &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="b8943-145">相關工作</span><span class="sxs-lookup"><span data-stu-id="b8943-145">Related Tasks</span></span>  
 <span data-ttu-id="b8943-146">**若要建立交易記錄備份**</span><span class="sxs-lookup"><span data-stu-id="b8943-146">**To create a transaction log backup**</span></span>  
  
-   [<span data-ttu-id="b8943-147">備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b8943-147">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   <span data-ttu-id="b8943-148"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span><span class="sxs-lookup"><span data-stu-id="b8943-148"><xref:Microsoft.SqlServer.Management.Smo.Backup.SqlBackup%2A> (SMO)</span></span>  
  
 <span data-ttu-id="b8943-149">若要排程備份作業，請參閱＜ [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md)＞。</span><span class="sxs-lookup"><span data-stu-id="b8943-149">To schedule backup jobs, see [Use the Maintenance Plan Wizard](../maintenance-plans/use-the-maintenance-plan-wizard.md).</span></span>  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="b8943-150">相關內容</span><span class="sxs-lookup"><span data-stu-id="b8943-150">Related Content</span></span>  
 <span data-ttu-id="b8943-151">無。</span><span class="sxs-lookup"><span data-stu-id="b8943-151">None.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8943-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8943-152">See Also</span></span>  
 <span data-ttu-id="b8943-153">[交易記錄 &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b8943-153">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="b8943-154">[SQL Server 資料庫的備份與還原](back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="b8943-154">[Back Up and Restore of SQL Server Databases](back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="b8943-155">[結尾記錄備份 &#40;SQL Server&#41;](tail-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="b8943-155">[Tail-Log Backups &#40;SQL Server&#41;](tail-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="b8943-156">套用交易記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="b8943-156">Apply Transaction Log Backups &#40;SQL Server&#41;</span></span>](transaction-log-backups-sql-server.md)  
  
  
