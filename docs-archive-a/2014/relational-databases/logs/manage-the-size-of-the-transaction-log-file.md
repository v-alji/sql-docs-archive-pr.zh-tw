---
title: 管理交易記錄檔的大小 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- transaction logs [SQL Server], size management
ms.assetid: 3a70e606-303f-47a8-96d4-2456a18d4297
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 219ba0605d60bab0b13675f7f9f7ff01cace5755
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594537"
---
# <a name="manage-the-size-of-the-transaction-log-file"></a><span data-ttu-id="c7337-102">管理交易記錄檔的大小</span><span class="sxs-lookup"><span data-stu-id="c7337-102">Manage the Size of the Transaction Log File</span></span>
  <span data-ttu-id="c7337-103">在部分情況下，實際壓縮或擴充 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料庫之交易記錄的實體記錄檔十分有用。</span><span class="sxs-lookup"><span data-stu-id="c7337-103">In some cases, it can be useful to physically shrink or expand the physical log file of the transaction log of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] database.</span></span> <span data-ttu-id="c7337-104">本主題包含下列作業的資訊：如何監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 交易記錄大小、壓縮交易記錄、加入或加大交易記錄檔、最佳化 **tempdb** 交易記錄成長率，以及控制交易記錄檔的成長。</span><span class="sxs-lookup"><span data-stu-id="c7337-104">This topic contains information about how to monitor the size of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] transaction log, shrink the transaction log, add or enlarge a transaction log file, optimize the **tempdb** transaction log growth rate, and control the growth of a transaction log file.</span></span>  
  
  
##  <a name="monitor-log-space-use"></a><a name="MonitorSpaceUse"></a><span data-ttu-id="c7337-105">監視記錄空間的使用</span><span class="sxs-lookup"><span data-stu-id="c7337-105">Monitor Log Space Use</span></span>  
 <span data-ttu-id="c7337-106">您可以使用 DBCC SQLPERF (LOGSPACE) 來監視記錄空間的使用。</span><span class="sxs-lookup"><span data-stu-id="c7337-106">You can monitor log space use by using DBCC SQLPERF (LOGSPACE).</span></span> <span data-ttu-id="c7337-107">這個命令會傳回目前使用之記錄空間量的相關資訊，並指出交易記錄需要截斷的時機。</span><span class="sxs-lookup"><span data-stu-id="c7337-107">This command returns information about the amount of log space currently used and indicates when the transaction log is in need of truncation.</span></span> <span data-ttu-id="c7337-108">如需詳細資訊，請參閱 [DBCC SQLPERF &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c7337-108">For more information, see [DBCC SQLPERF &#40;Transact-SQL&#41;](/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql).</span></span> <span data-ttu-id="c7337-109">如需記錄檔的目前大小、大小上限及檔案的自動成長選項等相關資訊，您也可以在 **sys.database_files** 中使用該記錄檔的 **size**、**max_size** 和 **growth** 資料行。</span><span class="sxs-lookup"><span data-stu-id="c7337-109">For information about the current size of a log file, its maximum size, and the autogrow option for the file, you can also use the **size**, **max_size**, and **growth** columns for that log file in **sys.database_files**.</span></span> <span data-ttu-id="c7337-110">如需詳細資訊，請參閱 [sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c7337-110">For more information, see [sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql).</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="c7337-111">我們建議您應避免讓記錄磁碟超過負載。</span><span class="sxs-lookup"><span data-stu-id="c7337-111">We recommend that you avoid overloading the log disk.</span></span>  
  
  
##  <a name="shrink-the-size-of-the-log-file"></a><a name="ShrinkSize"></a><span data-ttu-id="c7337-112">壓縮記錄檔的大小</span><span class="sxs-lookup"><span data-stu-id="c7337-112">Shrink the Size of the Log File</span></span>  
 <span data-ttu-id="c7337-113">若要減少實體記錄檔的實體大小，則必須壓縮記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c7337-113">To reduce the physical size of a physical log file, you must shrink the log file.</span></span> <span data-ttu-id="c7337-114">如果您知道交易記錄檔包含不再需要的未使用空間，則這十分有用。</span><span class="sxs-lookup"><span data-stu-id="c7337-114">This is useful if you know that a transaction log file contains unused space that you will not be needing.</span></span> <span data-ttu-id="c7337-115">只有當資料庫已上線，而且至少有一個虛擬記錄檔可用時，才會壓縮記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c7337-115">Shrinking a log file can occur only while the database is online and, also, at least one virtual log file is free.</span></span> <span data-ttu-id="c7337-116">在某些情況下，壓縮記錄可能要等到下一個記錄截斷之後才能進行。</span><span class="sxs-lookup"><span data-stu-id="c7337-116">In some cases, shrinking the log may not be possible until after the next log truncation.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c7337-117">像長時間執行的交易之類的因素，使虛擬記錄檔保持作用中一段很長的時間，可能限制記錄檔壓縮，甚至完全阻止記錄檔壓縮。</span><span class="sxs-lookup"><span data-stu-id="c7337-117">Factors, such as a long-running transaction, that keep virtual log files active for an extended period can restrict log shrinkage or even prevent the log from shrinking at all.</span></span> <span data-ttu-id="c7337-118">如需延遲記錄截斷可能因素的相關資訊，請參閱[交易記錄 &#40;SQL Server&#41;](the-transaction-log-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="c7337-118">For information about factors that can delay log truncation, see [The Transaction Log &#40;SQL Server&#41;](the-transaction-log-sql-server.md).</span></span>  
  
 <span data-ttu-id="c7337-119">壓縮記錄檔時，會移除一個或多個未保留邏輯記錄任何部分的虛擬記錄檔 (即 *「非使用中虛擬記錄檔」*(Inactive virtual log file))。</span><span class="sxs-lookup"><span data-stu-id="c7337-119">Shrinking a log file removes one or more virtual log files that do not hold any part of the logical log (that is, *inactive virtual log files*).</span></span> <span data-ttu-id="c7337-120">當交易記錄檔壓縮之後，就會從記錄檔的結尾移除將記錄縮減至大約目標大小所需的非使用中虛擬記錄檔。</span><span class="sxs-lookup"><span data-stu-id="c7337-120">When a transaction log file is shrunk, enough inactive virtual log files are removed from the end of the log file to reduce the log to approximately the target size.</span></span>  
  
 <span data-ttu-id="c7337-121">**若要壓縮記錄檔 (但不壓縮資料庫檔案)**</span><span class="sxs-lookup"><span data-stu-id="c7337-121">**To shrink a log file (without shrinking database files)**</span></span>  
  
-   [<span data-ttu-id="c7337-122">DBCC SHRINKFILE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c7337-122">DBCC SHRINKFILE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-shrinkfile-transact-sql)  
  
-   [<span data-ttu-id="c7337-123">壓縮檔案</span><span class="sxs-lookup"><span data-stu-id="c7337-123">Shrink a File</span></span>](../databases/shrink-a-file.md)  
  
 <span data-ttu-id="c7337-124">**若要監視記錄檔壓縮事件**</span><span class="sxs-lookup"><span data-stu-id="c7337-124">**To monitor log-file shrink events**</span></span>  
  
-   <span data-ttu-id="c7337-125">[Log File Auto Shrink Event Class](../event-classes/log-file-auto-shrink-event-class.md)。</span><span class="sxs-lookup"><span data-stu-id="c7337-125">[Log File Auto Shrink Event Class](../event-classes/log-file-auto-shrink-event-class.md).</span></span>  
  
 `To monitor log space`  
  
-   [<span data-ttu-id="c7337-126">DBCC SQLPERF &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c7337-126">DBCC SQLPERF &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-sqlperf-transact-sql)  
  
-   <span data-ttu-id="c7337-127">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) (請參閱一或多個記錄檔的 **size**、**max_size** 和 **growth** 資料行。)</span><span class="sxs-lookup"><span data-stu-id="c7337-127">[sys.database_files &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-database-files-transact-sql) (See the **size**, **max_size**, and **growth** columns for the log file or files.)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c7337-128">壓縮資料庫和記錄檔的作業可設定為自動進行。</span><span class="sxs-lookup"><span data-stu-id="c7337-128">Shrinking database and log files can be set to occur automatically.</span></span> <span data-ttu-id="c7337-129">不過，我們建議您不要進行自動壓縮，而且 `autoshrink` 資料庫屬性預設為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="c7337-129">However, we recommend against automatic shrinking, and the `autoshrink` database property is set to FALSE by default.</span></span> <span data-ttu-id="c7337-130">如果 `autoshrink` 設定為 TRUE，只有當超過 25% 的空間未使用時，自動壓縮才會減少檔案的大小。</span><span class="sxs-lookup"><span data-stu-id="c7337-130">If `autoshrink` is set to TRUE, automatic shrinking reduces the size of a file only when more than 25 percent of its space is unused.</span></span> <span data-ttu-id="c7337-131">此時，檔案會壓縮成只有 25% 的檔案是未使用空間的大小，或檔案的原始大小，以較大者為準。</span><span class="sxs-lookup"><span data-stu-id="c7337-131">The file is shrunk either to the size at which only 25 percent of the file is unused space or to the original size of the file, whichever is larger.</span></span> <span data-ttu-id="c7337-132">如需變更屬性之設定的詳細資訊 `autoshrink` ，請參閱[View or Change a Database Properties](../databases/view-or-change-the-properties-of-a-database.md)-使用 [**選項**] 頁面上的 [**自動壓縮**] 屬性，或 [ [ALTER database SET Options] &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)-使用 [AUTO_SHRINK] 選項。</span><span class="sxs-lookup"><span data-stu-id="c7337-132">For information about changing the setting of the `autoshrink` property, see [View or Change the Properties of a Database](../databases/view-or-change-the-properties-of-a-database.md)-use the **Auto Shrink** property on the **Options** page-or [ALTER DATABASE SET Options &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-set-options)-use the AUTO_SHRINK option.</span></span>  
  
  
##  <a name="add-or-enlarge-a-log-file"></a><a name="AddOrEnlarge"></a><span data-ttu-id="c7337-133">新增或加大記錄檔</span><span class="sxs-lookup"><span data-stu-id="c7337-133">Add or Enlarge a Log File</span></span>  
 <span data-ttu-id="c7337-134">或者，您可以加大現有的記錄檔 (如果磁碟空間允許的話)，或是將記錄檔加入資料庫 (通常是在不同的磁碟上)，來取得空間。</span><span class="sxs-lookup"><span data-stu-id="c7337-134">Alternatively, you can gain space by enlarging the existing log file (if disk space permits) or by adding a log file to the database, typically on a different disk.</span></span>  
  
-   <span data-ttu-id="c7337-135">若要對資料庫新增一個記錄檔，請使用 ALTER DATABASE 陳述式的 ADD LOG FILE 子句。</span><span class="sxs-lookup"><span data-stu-id="c7337-135">To add a log file to the database, use the ADD LOG FILE clause of the ALTER DATABASE statement.</span></span> <span data-ttu-id="c7337-136">新增記錄檔可讓記錄檔增大。</span><span class="sxs-lookup"><span data-stu-id="c7337-136">Adding a log file allows the log to grow.</span></span>  
  
-   <span data-ttu-id="c7337-137">若要加大記錄檔，可以使用 ALTER DATABASE 陳述式的 MODIFY FILE 子句，並指定 SIZE 與 MAXSIZE 語法。</span><span class="sxs-lookup"><span data-stu-id="c7337-137">To enlarge the log file, use the MODIFY FILE clause of the ALTER DATABASE statement, specifying the SIZE and MAXSIZE syntax.</span></span> <span data-ttu-id="c7337-138">如需詳細資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c7337-138">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
  
##  <a name="optimize-the-size-of-the-tempdb-transaction-log"></a><a name="tempdbOptimize"></a><span data-ttu-id="c7337-139">優化 tempdb 交易記錄檔的大小</span><span class="sxs-lookup"><span data-stu-id="c7337-139">Optimize the Size of the tempdb Transaction Log</span></span>  
 <span data-ttu-id="c7337-140">重新啟動伺服器執行個體時，就會將 **tempdb** 資料庫的交易記錄大小重新調整為自動成長之前的原始大小。</span><span class="sxs-lookup"><span data-stu-id="c7337-140">Restarting a server instance resizes the transaction log of the **tempdb** database to its original, pre-autogrow size.</span></span> <span data-ttu-id="c7337-141">這樣會降低 **tempdb** 交易記錄的效能。</span><span class="sxs-lookup"><span data-stu-id="c7337-141">This can reduce the performance of the **tempdb** transaction log.</span></span> <span data-ttu-id="c7337-142">您可以在啟動或重新啟動伺服器執行個體後，增加 **tempdb** 交易記錄的大小，藉以避免這項負擔。</span><span class="sxs-lookup"><span data-stu-id="c7337-142">You can avoid this overhead by increasing the size of the **tempdb** transaction log after starting or restarting the server instance.</span></span> <span data-ttu-id="c7337-143">如需詳細資訊，請參閱 [tempdb Database](../databases/tempdb-database.md)。</span><span class="sxs-lookup"><span data-stu-id="c7337-143">For more information, see [tempdb Database](../databases/tempdb-database.md).</span></span>  
  
  
##  <a name="control-the-growth-of-a-transaction-log-file"></a><a name="ControlGrowth"></a><span data-ttu-id="c7337-144">控制交易記錄檔的成長</span><span class="sxs-lookup"><span data-stu-id="c7337-144">Control the Growth of a Transaction Log File</span></span>  
 <span data-ttu-id="c7337-145">您可以使用 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) 陳述式來管理交易記錄檔的成長。</span><span class="sxs-lookup"><span data-stu-id="c7337-145">You can use the [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) statement to manage the growth of a transaction log file.</span></span> <span data-ttu-id="c7337-146">請注意：</span><span class="sxs-lookup"><span data-stu-id="c7337-146">Note the following:</span></span>  
  
-   <span data-ttu-id="c7337-147">若要變更目前的檔案大小 (單位為 KB、MB、GB 和 TB)，請使用 SIZE 選項。</span><span class="sxs-lookup"><span data-stu-id="c7337-147">To change the current file size in KB, MB, GB, and TB units, use the SIZE option.</span></span>  
  
-   <span data-ttu-id="c7337-148">若要變更成長的增量，請使用 FILEGROWTH 選項。</span><span class="sxs-lookup"><span data-stu-id="c7337-148">To change the growth increment, use the FILEGROWTH option.</span></span> <span data-ttu-id="c7337-149">0 的值表示將自動成長設為關閉，而且不允許任何其他空間。</span><span class="sxs-lookup"><span data-stu-id="c7337-149">A value of 0 indicates that automatic growth is set to off and no additional space is permitted.</span></span> <span data-ttu-id="c7337-150">記錄檔的少量自動成長增量可能會降低效能。</span><span class="sxs-lookup"><span data-stu-id="c7337-150">A small autogrowth increment on a log file can reduce performance.</span></span> <span data-ttu-id="c7337-151">記錄檔的檔案成長量應夠大，才不用經常進行擴充。</span><span class="sxs-lookup"><span data-stu-id="c7337-151">The file growth increment on a log file should be sufficiently large to avoid frequent expansion.</span></span> <span data-ttu-id="c7337-152">通常適當的預設成長量為 10%。</span><span class="sxs-lookup"><span data-stu-id="c7337-152">The default growth increment of 10 percent is generally suitable.</span></span>  
  
     <span data-ttu-id="c7337-153">如需在記錄檔上變更檔案成長屬性的詳細資訊，請參閱[ALTER database &#40;transact-sql&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="c7337-153">For information on changing the file-growth property on a log file, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="c7337-154">若要控制記錄檔大小的最大值 (單位為 KB、MB、GB 和 TB) 或是將成長設定為 UNLIMITED，請使用 MAXSIZE 選項。</span><span class="sxs-lookup"><span data-stu-id="c7337-154">To control the maximum the size of a log file in KB, MB, GB, and TB units or to set growth to UNLIMITED, use the MAXSIZE option.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="c7337-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c7337-155">See Also</span></span>  
 <span data-ttu-id="c7337-156">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c7337-156">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 [<span data-ttu-id="c7337-157">寫滿交易記錄疑難排解 &#40;SQL Server 錯誤 9002&#41;</span><span class="sxs-lookup"><span data-stu-id="c7337-157">Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;</span></span>](troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
  
