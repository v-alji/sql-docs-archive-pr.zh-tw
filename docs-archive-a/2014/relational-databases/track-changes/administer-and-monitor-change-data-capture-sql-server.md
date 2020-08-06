---
title: 管理和監視異動資料擷取 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- change data capture [SQL Server], monitoring
- change data capture [SQL Server], administering
- change data capture [SQL Server], jobs
ms.assetid: 23bda497-67b2-4e7b-8e4d-f1f9a2236685
author: rothja
ms.author: jroth
ms.openlocfilehash: 8d97929ead145d1b0de1a1f83becb15ade397683
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597689"
---
# <a name="administer-and-monitor-change-data-capture-sql-server"></a><span data-ttu-id="0738d-102">管理和監視異動資料擷取 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="0738d-102">Administer and Monitor Change Data Capture (SQL Server)</span></span>
  <span data-ttu-id="0738d-103">此主題描述如何管理及監視異動資料擷取。</span><span class="sxs-lookup"><span data-stu-id="0738d-103">This topic describes how to administer and monitor change data capture.</span></span>  
  
##  <a name="capture-job"></a><a name="Capture"></a> <span data-ttu-id="0738d-104">擷取作業</span><span class="sxs-lookup"><span data-stu-id="0738d-104">Capture Job</span></span>  
 <span data-ttu-id="0738d-105">擷取作業是透過執行無參數的預存程序 `sp_MScdc_capture_job` 起始的。</span><span class="sxs-lookup"><span data-stu-id="0738d-105">The capture job is initiated by running the parameterless stored procedure `sp_MScdc_capture_job`.</span></span> <span data-ttu-id="0738d-106">這個預存程序一開始會從 msdb.dbo.cdc_jobs 中擷取作業之 *maxtrans*、 *maxscans*、 *continuous*和 *pollinginterval* 的設定值。</span><span class="sxs-lookup"><span data-stu-id="0738d-106">This stored procedure starts by extracting the configured values for *maxtrans*, *maxscans*, *continuous*, and *pollinginterval* for the capture job from msdb.dbo.cdc_jobs.</span></span> <span data-ttu-id="0738d-107">然後，這些設定值會當做參數傳遞給 `sp_cdc_scan` 預存程序。</span><span class="sxs-lookup"><span data-stu-id="0738d-107">These configured values are then passed as parameters to the stored procedure `sp_cdc_scan`.</span></span> <span data-ttu-id="0738d-108">這個預存程序是用來叫用 `sp_replcmds`，以便執行記錄檔掃描。</span><span class="sxs-lookup"><span data-stu-id="0738d-108">This is used to invoke `sp_replcmds` to perform the log scan.</span></span>  
  
### <a name="capture-job-parameters"></a><span data-ttu-id="0738d-109">擷取作業參數</span><span class="sxs-lookup"><span data-stu-id="0738d-109">Capture Job Parameters</span></span>  
 <span data-ttu-id="0738d-110">若要了解擷取作業行為，您必須了解 `sp_cdc_scan` 如何使用可設定的參數。</span><span class="sxs-lookup"><span data-stu-id="0738d-110">To understand capture job behavior, you must understand how the configurable parameters are used by `sp_cdc_scan`.</span></span>  
  
#### <a name="maxtrans-parameter"></a><span data-ttu-id="0738d-111">maxtrans 參數</span><span class="sxs-lookup"><span data-stu-id="0738d-111">maxtrans Parameter</span></span>  
 <span data-ttu-id="0738d-112">*maxtrans* 參數會指定可以在記錄檔之單一掃描循環中處理的最大交易數目。</span><span class="sxs-lookup"><span data-stu-id="0738d-112">The *maxtrans* parameter specifies the maximum number of transactions that can be processed in a single scan cycle of the log.</span></span> <span data-ttu-id="0738d-113">在掃描期間，如果要處理的交易數目達到這個限制，目前的掃描就不會加入其他任何交易。</span><span class="sxs-lookup"><span data-stu-id="0738d-113">If, during the scan, the number of transactions to be processed reaches this limit, no additional transactions are included in the current scan.</span></span> <span data-ttu-id="0738d-114">在掃描循環完成之後，已處理的交易數目一定會小於或等於 *maxtrans*。</span><span class="sxs-lookup"><span data-stu-id="0738d-114">After a scan cycle is complete, the number of transactions that were processed will always be less than or equal to *maxtrans*.</span></span>  
  
#### <a name="maxscans-parameter"></a><span data-ttu-id="0738d-115">maxscans 參數</span><span class="sxs-lookup"><span data-stu-id="0738d-115">maxscans Parameter</span></span>  
 <span data-ttu-id="0738d-116">*maxscans* 參數會指定傳回 (continuous = 0) 或執行 Waitfor (continuous = 1) 之前嘗試清空記錄檔的最大掃描循環數目。</span><span class="sxs-lookup"><span data-stu-id="0738d-116">The *maxscans* parameter specifies the maximum number of scan cycles that are attempted to drain the log before either returning (continuous = 0) or executing a waitfor (continuous = 1).</span></span>  
  
#### <a name="continuous-parameter"></a><span data-ttu-id="0738d-117">continuous 參數</span><span class="sxs-lookup"><span data-stu-id="0738d-117">continuous Parameter</span></span>  
 <span data-ttu-id="0738d-118">*連續*參數會控制 `sp_cdc_scan` 在清空記錄檔或執行最大掃描迴圈數目 (一次模式) 之後，中的讓出控制項是否為。</span><span class="sxs-lookup"><span data-stu-id="0738d-118">The *continuous* parameter controls whether `sp_cdc_scan` relinquishes control in after either draining the log or executing the maximum number of scan cycles (one shot mode).</span></span> <span data-ttu-id="0738d-119">它也會控制 `sp_cdc_scan` 是否繼續執行，直到明確停止為止 (連續模式)。</span><span class="sxs-lookup"><span data-stu-id="0738d-119">It also controles whether `sp_cdc_scan` continues to run until explicitly stopped (continuous mode).</span></span>  
  
##### <a name="one-shot-mode"></a><span data-ttu-id="0738d-120">一次模式</span><span class="sxs-lookup"><span data-stu-id="0738d-120">One Shot Mode</span></span>  
 <span data-ttu-id="0738d-121">在一次模式中，capture 作業會要求 `sp_cdc_scan` 執行最多*maxtrans*掃描，以嘗試清空記錄檔並傳回。</span><span class="sxs-lookup"><span data-stu-id="0738d-121">In one shot mode, the capture job requests `sp_cdc_scan` to perform up to *maxtrans* scans to try to drain the log and return.</span></span> <span data-ttu-id="0738d-122">存在記錄檔中 *maxtrans* 以外的任何交易將在後續掃描中處理。</span><span class="sxs-lookup"><span data-stu-id="0738d-122">Any transactions in addition to *maxtrans* that are present in the log will be processed in later scans.</span></span>  
  
 <span data-ttu-id="0738d-123">一次模式會用於受到控制的測試中，因為已知要處理的交易數量，而且作業完成時自動關閉具有一些優點。</span><span class="sxs-lookup"><span data-stu-id="0738d-123">One shot mode is used in controlled tests, where the volume of transactions to be processed is known, and there are advantages to the fact that the job closes automatically on when it is finished.</span></span> <span data-ttu-id="0738d-124">不建議您在實際執行環境中使用一次模式。</span><span class="sxs-lookup"><span data-stu-id="0738d-124">One shot mode is not recommended for production use.</span></span> <span data-ttu-id="0738d-125">這是因為它會仰賴作業排程來管理執行掃描循環的頻率。</span><span class="sxs-lookup"><span data-stu-id="0738d-125">This is because t relies on the job schedule to manage how frequently the scan cycle is run.</span></span>  
  
 <span data-ttu-id="0738d-126">在一次模式中執行時，您可以使用下列計算來計算擷取作業之預期輸送量的上限 (以每秒交易數表示)：</span><span class="sxs-lookup"><span data-stu-id="0738d-126">When running in one shot mode, you can compute an upper bound on expected throughput of the capture job, expressed in transactions per second by using the following computation:</span></span>  
  
 `(maxtrans * maxscans) / number of seconds between scans`  
  
 <span data-ttu-id="0738d-127">即使掃描記錄檔和擴展變更資料表所需的時間並未與 0 完全不同，此作業的平均輸送量仍無法超過將單一掃描允許的最大交易數乘以允許的最大掃描數再除以分隔記錄檔處理的秒數所取得的值。</span><span class="sxs-lookup"><span data-stu-id="0738d-127">Even if the time that is required to scan the log and populate the change tables were not significantly different from 0, the average throughput of the job could not exceed the value obtained by dividing the maximum allowed transactions for a single scan multiplied by the maximum allowed scans by the number of seconds separating log processing.</span></span>  
  
 <span data-ttu-id="0738d-128">如果您使用一次模式來管理記錄檔掃描，記錄檔處理之間的秒數就必須受到作業排程的管制。</span><span class="sxs-lookup"><span data-stu-id="0738d-128">If one shot mode were to be used to regulate log scanning, the number of seconds between log processing would have to be governed by the job schedule.</span></span> <span data-ttu-id="0738d-129">需要這種行為時，在連續模式中執行擷取作業是管理重新排程記錄檔掃描的較佳方式。</span><span class="sxs-lookup"><span data-stu-id="0738d-129">When this kind of behavior is desired, running the capture job in continuous mode is a better way to manage rescheduling the log scan.</span></span>  
  
##### <a name="continuous-mode-and-the-polling-interval"></a><span data-ttu-id="0738d-130">連續模式和輪詢間隔</span><span class="sxs-lookup"><span data-stu-id="0738d-130">Continuous Mode and the Polling Interval</span></span>  
 <span data-ttu-id="0738d-131">在連續模式中，擷取作業會要求 `sp_cdc_scan` 連續執行。</span><span class="sxs-lookup"><span data-stu-id="0738d-131">In continuous mode, the capture job requests that `sp_cdc_scan` run continuously.</span></span> <span data-ttu-id="0738d-132">這會透過提供 maxtrans 和 maxscans，以及記錄檔處理之間秒數的值 (輪詢間隔)，讓此預存程序管理自己的等候迴圈。</span><span class="sxs-lookup"><span data-stu-id="0738d-132">This lets the stored procedure manage its own wait loop by providing not only for maxtrans and maxscans but also a value for the number of seconds between log processing (the polling interval).</span></span> <span data-ttu-id="0738d-133">在這種模式中執行時，擷取作業會維持使用中，並且在記錄檔掃描之間執行 `WAITFOR`。</span><span class="sxs-lookup"><span data-stu-id="0738d-133">Running in this mode, the capture job remains active, executing a `WAITFOR` between log scanning.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0738d-134">當輪詢間隔的值大於 0 時，重複執行一次作業之輸送量的相同上限也會套用至連續模式中的作業。</span><span class="sxs-lookup"><span data-stu-id="0738d-134">When the value of the polling interval is greater than 0, the same upper limit on throughput for the recurring one shot job also applies to the job operation in continuous mode.</span></span> <span data-ttu-id="0738d-135">也就是說，(*maxtrans* \* *maxscans*) 除以非零的輪詢間隔會針對擷取作業可以處理的平均交易數目放置上限。</span><span class="sxs-lookup"><span data-stu-id="0738d-135">That is, (*maxtrans* \* *maxscans*) divided by a nonzero polling interval will put an upper bound on the average number of transactions that can be processed by the capture job.</span></span>  
  
### <a name="capture-job-customization"></a><span data-ttu-id="0738d-136">擷取作業自訂</span><span class="sxs-lookup"><span data-stu-id="0738d-136">Capture Job Customization</span></span>  
 <span data-ttu-id="0738d-137">您可以針對擷取作業套用其他邏輯，以便決定新的掃描是否會立即開始，或者在啟動新的掃描之前是否加上休眠，而非仰賴固定的輪詢間隔。</span><span class="sxs-lookup"><span data-stu-id="0738d-137">For the capture job, you can apply additional logic to determine whether a new scan begins immediately or whether a sleep is imposed before it starts a new scan instead of rely on a fixed polling interval.</span></span> <span data-ttu-id="0738d-138">這項選擇可能僅僅依據當天時間，或許在尖峰活動時段強制執行非常長的休眠，甚至在當天結束時移至輪詢間隔 0 (如果完成日間處理和準備夜間執行很重要的話)。</span><span class="sxs-lookup"><span data-stu-id="0738d-138">The choice could be based merely on time of the day, perhaps enforcing very long sleeps during peak activity times, and even moving to a polling interval of 0 at close of day when it is important to complete the days processing and prepare for nightly runs.</span></span> <span data-ttu-id="0738d-139">您也可以監視擷取處理序進度，以便判斷午夜之前認可之所有交易已經掃描並儲放在變更資料表中的時間。</span><span class="sxs-lookup"><span data-stu-id="0738d-139">Capture process progress could also be monitored to determine when all transactions committed by mid-night had been scanned and deposited in change tables.</span></span> <span data-ttu-id="0738d-140">這會讓擷取作業結束，以便依據排程的每日重新啟動時間重新啟動。</span><span class="sxs-lookup"><span data-stu-id="0738d-140">This lets the capture job end, to be restarted by a scheduled daily restart.</span></span> <span data-ttu-id="0738d-141">透過將呼叫 `sp_cdc_scan` 的傳遞作業步驟取代成 `sp_cdc_scan` 之使用者撰寫包裝函式的呼叫，您只要進行少數額外步驟就可以取得高度自訂的行為。</span><span class="sxs-lookup"><span data-stu-id="0738d-141">By replacing the delivered job step calling `sp_cdc_scan` with a call to a user written wrapper for `sp_cdc_scan`, highly customized behavior can be obtained with little additional effort.</span></span>  
  
##  <a name="cleanup-job"></a><a name="Cleanup"></a> <span data-ttu-id="0738d-142">清除作業</span><span class="sxs-lookup"><span data-stu-id="0738d-142">Cleanup Job</span></span>  
 <span data-ttu-id="0738d-143">本節提供有關異動資料擷取清除作業如何運作的資訊。</span><span class="sxs-lookup"><span data-stu-id="0738d-143">This section provides information about how the change data capture cleanup job works.</span></span>  
  
### <a name="structure-of-the-cleanup-job"></a><span data-ttu-id="0738d-144">清除作業的結構</span><span class="sxs-lookup"><span data-stu-id="0738d-144">Structure of the Cleanup Job</span></span>  
 <span data-ttu-id="0738d-145">異動資料擷取會使用保留性清除策略來管理變更資料表大小。</span><span class="sxs-lookup"><span data-stu-id="0738d-145">Change data capture uses a retention based cleanup strategy to manage change table size.</span></span> <span data-ttu-id="0738d-146">此清除機制包含啟用第一個資料庫資料表時建立的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent [!INCLUDE[tsql](../../includes/tsql-md.md)] 作業。</span><span class="sxs-lookup"><span data-stu-id="0738d-146">The cleanup mechanism consists of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent [!INCLUDE[tsql](../../includes/tsql-md.md)] job that is created when the first database table is enabled.</span></span> <span data-ttu-id="0738d-147">單一清除作業會處理所有資料庫變更資料表的清除，並且將相同的保留值套用至所有定義的擷取執行個體。</span><span class="sxs-lookup"><span data-stu-id="0738d-147">A single cleanup job handles cleanup for all database change tables and applies the same retention value to all defined capture instances.</span></span>  
  
 <span data-ttu-id="0738d-148">清除作業是透過執行無參數的預存程序 `sp_MScdc_cleanup_job` 起始的。</span><span class="sxs-lookup"><span data-stu-id="0738d-148">The cleanup job is initiated by running the parameterless stored procedure `sp_MScdc_cleanup_job`.</span></span> <span data-ttu-id="0738d-149">這個預存程序一開始會從 `msdb.dbo.cdc_jobs` 中擷取清除作業的設定保留和臨界值。</span><span class="sxs-lookup"><span data-stu-id="0738d-149">This stored procedure starts by extracting the configured retention and threshold values for the cleanup job from `msdb.dbo.cdc_jobs`.</span></span> <span data-ttu-id="0738d-150">此保留值會用來計算變更資料表的新下限標準。</span><span class="sxs-lookup"><span data-stu-id="0738d-150">The retention value is used to compute a new low watermark for the change tables.</span></span> <span data-ttu-id="0738d-151">從資料表的最大*tran_end_time*值減去指定的分鐘數， `cdc.lsn_time_mapping` 以取得以日期時間值表示的新下限標準。</span><span class="sxs-lookup"><span data-stu-id="0738d-151">The specified number of minutes is subtracted from the maximum *tran_end_time* value from the `cdc.lsn_time_mapping` table to obtain the new low water mark expressed as a datetime value.</span></span> <span data-ttu-id="0738d-152">然後，使用 CDC.lsn_time_mapping 資料表來將這個日期時間值轉換成對應的 `lsn` 值。</span><span class="sxs-lookup"><span data-stu-id="0738d-152">The CDC.lsn_time_mapping table is then used to convert this datetime value to a corresponding `lsn` value.</span></span> <span data-ttu-id="0738d-153">如果資料表中的多個項目共用相同的認可時間，就會選擇對應至具有最小 `lsn` 之項目的 `lsn` 成為新的下限標準。</span><span class="sxs-lookup"><span data-stu-id="0738d-153">If the same commit time is shared by multiple entries in the table, the `lsn` that corresponds to the entry that has the smallest `lsn` is chosen as the new low watermark.</span></span> <span data-ttu-id="0738d-154">這個 `lsn` 值會傳遞給 `sp_cdc_cleanup_change_tables`，以便從資料庫變更資料表中移除變更資料表項目。</span><span class="sxs-lookup"><span data-stu-id="0738d-154">This `lsn` value is passed to `sp_cdc_cleanup_change_tables` to remove change table entries from the database change tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0738d-155">使用最近交易之認可時間當做計算新下限標準之基礎的優點在於，它會在指定的時間內讓變更保留在變更資料表中。</span><span class="sxs-lookup"><span data-stu-id="0738d-155">The advantage of using the commit time of the recent transaction as the base for computing the new low watermark is that it lets the changes remain in change tables for the specified time.</span></span> <span data-ttu-id="0738d-156">即使擷取處理序正在後方執行，也會發生這種情況。</span><span class="sxs-lookup"><span data-stu-id="0738d-156">This happens even when the capture process is running behind.</span></span> <span data-ttu-id="0738d-157">具有相同認可時間當做目前下限標準的所有項目會透過選擇具有實際下限標準之共用認可時間的最小 `lsn`，繼續在變更資料表內部表示。</span><span class="sxs-lookup"><span data-stu-id="0738d-157">All entries that have the same commit time as the current low watermark continue to be represented within the change tables by choosing the smallest `lsn` that has the shared commit time for the actual low watermark.</span></span>  
  
 <span data-ttu-id="0738d-158">執行清除時，所有擷取執行個體的下限標準一開始是在單一交易中更新。</span><span class="sxs-lookup"><span data-stu-id="0738d-158">When a cleanup is performed, the low watermark for all capture instances is initially updated in a single transaction.</span></span> <span data-ttu-id="0738d-159">然後，它會嘗試從變更資料表和 cdc.lsn_time_mapping 資料表中移除已過時的項目。</span><span class="sxs-lookup"><span data-stu-id="0738d-159">It then tries to remove obsolete entries from the change tables and the cdc.lsn_time_mapping table.</span></span> <span data-ttu-id="0738d-160">可設定的臨界值會限制在任何單一陳述式中刪除的項目數。</span><span class="sxs-lookup"><span data-stu-id="0738d-160">The configurable threshold value limits how many entries are deleted in any single statement.</span></span> <span data-ttu-id="0738d-161">如果無法針對任何個別的資料表執行刪除，將無法防止針對其餘資料表嘗試進行此作業。</span><span class="sxs-lookup"><span data-stu-id="0738d-161">Failure to perform the delete on any individual table will not prevent the operation from being attempted on the remaining tables.</span></span>  
  
### <a name="cleanup-job-customization"></a><span data-ttu-id="0738d-162">清除作業自訂</span><span class="sxs-lookup"><span data-stu-id="0738d-162">Cleanup Job Customization</span></span>  
 <span data-ttu-id="0738d-163">對於清除作業而言，自訂的可能性在於用來決定哪些變更資料表項目要捨棄的策略。</span><span class="sxs-lookup"><span data-stu-id="0738d-163">For the cleanup job, the possibility for customization is in the strategy used to determine which change table entries are to be discarded.</span></span> <span data-ttu-id="0738d-164">在傳遞的清除作業中，唯一支援的策略是以時間為基礎的策略。</span><span class="sxs-lookup"><span data-stu-id="0738d-164">The only supported strategy in the delivered cleanup job is a time-based one.</span></span> <span data-ttu-id="0738d-165">在該情況下，新下限標準的計算方式是從上次處理之交易的認可時間中減去允許的保留週期。</span><span class="sxs-lookup"><span data-stu-id="0738d-165">In that situation, the new low watermark is computed by subtracting the allowed retention period from the commit time of the last transaction processed.</span></span> <span data-ttu-id="0738d-166">由於基礎清除程序是以 `lsn` 而非時間為基礎，所以您可以使用任何數目之策略來決定要保留在變更資料表中的最小 `lsn`。</span><span class="sxs-lookup"><span data-stu-id="0738d-166">Because the underlying cleanup procedures are based on `lsn` instead of time, any number of strategies can be used to determine the smallest `lsn` to keep in the change tables.</span></span> <span data-ttu-id="0738d-167">其中只有某些策略是嚴格地以時間為基礎。</span><span class="sxs-lookup"><span data-stu-id="0738d-167">Only some of these are strictly time-based.</span></span> <span data-ttu-id="0738d-168">例如，如果需要存取變更資料表的下游處理序無法執行，用戶端的相關知識就可用來提供保全。</span><span class="sxs-lookup"><span data-stu-id="0738d-168">Knowledge about the clients, for example, could be used to provide a failsafe if downstream processes that require access to the change tables cannot run.</span></span> <span data-ttu-id="0738d-169">此外，雖然預設策略會套用相同 `lsn` 來清除所有資料庫的變更資料表，但是您也可以呼叫基礎清除程序，以便在擷取執行個體層級進行清除。</span><span class="sxs-lookup"><span data-stu-id="0738d-169">Also, although the default strategy applies the same `lsn` to clean up all the databases' change tables, the underlying cleanup procedure, can also be called to clean up at the capture instance level.</span></span>  
  
##  <a name="monitor-the-change-data-capture-process"></a><a name="Monitor"></a> <span data-ttu-id="0738d-170">監視異動資料擷取程序</span><span class="sxs-lookup"><span data-stu-id="0738d-170">Monitor the Change Data Capture Process</span></span>  
 <span data-ttu-id="0738d-171">監視異動資料擷取程序可讓您判斷變更是否正確地並且以合理的延遲寫入變更資料表。</span><span class="sxs-lookup"><span data-stu-id="0738d-171">Monitoring the change data capture process lets you determine if changes are being written correctly and with a reasonable latency to the change tables.</span></span> <span data-ttu-id="0738d-172">監視也可以協助您識別可能發生的任何錯誤。</span><span class="sxs-lookup"><span data-stu-id="0738d-172">Monitoring can also help you to identify any errors that might occur.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0738d-173">包含兩個動態管理檢視，可協助您監視異動資料擷取： [sys.dm_cdc_log_scan_sessions](../native-client-ole-db-data-source-objects/sessions.md) 和 [sys.dm_cdc_errors](../native-client-ole-db-errors/errors.md)。</span><span class="sxs-lookup"><span data-stu-id="0738d-173">includes two dynamic management views to help you monitor change data capture: [sys.dm_cdc_log_scan_sessions](../native-client-ole-db-data-source-objects/sessions.md) and [sys.dm_cdc_errors](../native-client-ole-db-errors/errors.md).</span></span>  
  
### <a name="identify-sessions-with-empty-result-sets"></a><span data-ttu-id="0738d-174">識別含有空白結果集的工作階段</span><span class="sxs-lookup"><span data-stu-id="0738d-174">Identify Sessions with Empty Result Sets</span></span>  
 <span data-ttu-id="0738d-175">sys.dm_cdc_log_scan_sessions 中的每個資料列都代表記錄檔掃描工作階段 (除了識別碼為 0 的資料列以外)。</span><span class="sxs-lookup"><span data-stu-id="0738d-175">Every row in sys.dm_cdc_log_scan_sessions represents a log scan session (except the row with an ID of 0).</span></span> <span data-ttu-id="0738d-176">記錄檔掃描工作階段相當於執行一次 [sp_cdc_scan](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0738d-176">A log scan session is equivalent to one execution of [sp_cdc_scan](/sql/relational-databases/system-stored-procedures/sys-sp-cdc-scan-transact-sql).</span></span> <span data-ttu-id="0738d-177">在工作階段期間，掃描可能會傳回變更或傳回空的結果。</span><span class="sxs-lookup"><span data-stu-id="0738d-177">During a session, the scan can either return changes or return an empty result.</span></span> <span data-ttu-id="0738d-178">如果結果集是空的，sys.dm_cdc_log_scan_sessions 中的 empty_scan_count 資料行就會設定為 1。</span><span class="sxs-lookup"><span data-stu-id="0738d-178">If the result set is empty, the empty_scan_count column in sys.dm_cdc_log_scan_sessions is set to 1.</span></span> <span data-ttu-id="0738d-179">如果含有連續的空結果集 (例如擷取作業連續執行)，最後一個現有資料列中的 empty_scan_count 就會遞增。</span><span class="sxs-lookup"><span data-stu-id="0738d-179">If there are consecutive empty result sets, such as if the capture job is running continuously, the empty_scan_count in the last existing row is incremented.</span></span> <span data-ttu-id="0738d-180">例如，如果 sys.dm_cdc_log_scan_sessions 已經針對傳回變更的掃描包含 10 個資料列，而且資料列中含有五個空的結果，表示檢視包含 11 個資料列。</span><span class="sxs-lookup"><span data-stu-id="0738d-180">For example, if sys.dm_cdc_log_scan_sessions already contains 10 rows for scans that returned changes and there are five empty results in a row, the view contains 11 rows.</span></span> <span data-ttu-id="0738d-181">在 empty_scan_count 資料行中，最後一個資料列的值為 5。</span><span class="sxs-lookup"><span data-stu-id="0738d-181">The last row has a value of 5 in the empty_scan_count column.</span></span> <span data-ttu-id="0738d-182">若要判斷具有空白掃描的工作階段，請執行下列查詢：</span><span class="sxs-lookup"><span data-stu-id="0738d-182">To determine sessions that had an empty scan, run the following query:</span></span>  
  
```sql
SELECT * from sys.dm_cdc_log_scan_sessions where empty_scan_count <> 0
```
  
### <a name="determine-latency"></a><span data-ttu-id="0738d-183">判斷延遲</span><span class="sxs-lookup"><span data-stu-id="0738d-183">Determine Latency</span></span>  
 <span data-ttu-id="0738d-184">sys.dm_cdc_log_scan_sessions 管理檢視含有記錄每個擷取工作階段之延遲的資料行。</span><span class="sxs-lookup"><span data-stu-id="0738d-184">The sys.dm_cdc_log_scan_sessions management view includes a column that records the latency for each capture session.</span></span> <span data-ttu-id="0738d-185">延遲會定義成在來源資料表上認可交易與在變更資料表上認可最後一個擷取交易之間經過的時間。</span><span class="sxs-lookup"><span data-stu-id="0738d-185">Latency is defined as the elapsed time between a transaction being committed on a source table and the last captured transaction being committed on the change table.</span></span> <span data-ttu-id="0738d-186">系統只會針對使用中工作階段填入 latency 資料行。</span><span class="sxs-lookup"><span data-stu-id="0738d-186">The latency column is populated only for active sessions.</span></span> <span data-ttu-id="0738d-187">若為 empty_scan_count 資料行中的值大於 0 的工作階段，latency 資料行就會設定為 0。</span><span class="sxs-lookup"><span data-stu-id="0738d-187">For sessions with a value greater than 0 in the empty_scan_count column, the latency column is set to 0.</span></span> <span data-ttu-id="0738d-188">下列查詢會針對最近的工作階段傳回平均延遲：</span><span class="sxs-lookup"><span data-stu-id="0738d-188">The following query returns the average latency for the most recent sessions:</span></span>  
  
```sql
SELECT latency FROM sys.dm_cdc_log_scan_sessions WHERE session_id = 0
```
  
 <span data-ttu-id="0738d-189">您可以使用延遲資料來判斷擷取程序處理交易的速度快慢。</span><span class="sxs-lookup"><span data-stu-id="0738d-189">You can use latency data to determine how fast or slow the capture process is processing transactions.</span></span> <span data-ttu-id="0738d-190">當擷取程序連續執行時，這項資料便最有用。</span><span class="sxs-lookup"><span data-stu-id="0738d-190">This data is most useful when the capture process is running continuously.</span></span> <span data-ttu-id="0738d-191">如果擷取程序正按照排程執行，延遲可能會很高，因為在來源資料表上認可交易與按照排程時間執行的擷取程序之間存在延遲。</span><span class="sxs-lookup"><span data-stu-id="0738d-191">If the capture process is running on a schedule, latency can be high because of the lag between transactions being committed on the source table and the capture process running at its scheduled time.</span></span>  
  
 <span data-ttu-id="0738d-192">擷取程序效率的另一個重要量值是輸送量。</span><span class="sxs-lookup"><span data-stu-id="0738d-192">Another important measure of capture process efficiency is throughput.</span></span> <span data-ttu-id="0738d-193">這是指每個工作階段期間每秒處理的平均命令數目。</span><span class="sxs-lookup"><span data-stu-id="0738d-193">This is the average number of commands per second that are processed during each session.</span></span> <span data-ttu-id="0738d-194">若要判斷某個工作階段的輸送量，請將 command_count 資料行中的值除以 duration 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="0738d-194">To determine the throughput of a session, divide the value in the command_count column by the value in the duration column.</span></span> <span data-ttu-id="0738d-195">下列查詢會針對最近的工作階段傳回平均輸送量：</span><span class="sxs-lookup"><span data-stu-id="0738d-195">The following query returns the average throughput for the most recent sessions:</span></span>  
  
```sql
SELECT command_count/duration AS [Throughput] FROM sys.dm_cdc_log_scan_sessions WHERE session_id = 0
```
  
### <a name="use-data-collector-to-collect-sampling-data"></a><span data-ttu-id="0738d-196">使用資料收集器來收集取樣資料</span><span class="sxs-lookup"><span data-stu-id="0738d-196">Use Data Collector to Collect Sampling Data</span></span>  
 <span data-ttu-id="0738d-197">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料收集器可讓您從任何資料表或動態管理檢視中收集資料的快照集，然後建立效能資料倉儲。</span><span class="sxs-lookup"><span data-stu-id="0738d-197">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data collector lets you collect snapshots of data from any table or dynamic management view and build a performance data warehouse.</span></span> <span data-ttu-id="0738d-198">當資料庫啟用異動資料擷取時，以固定間隔建立 sys.dm_cdc_log_scan_sessions 檢視和 sys.dm_cdc_errors 檢視的快照集以便之後分析會很有用。</span><span class="sxs-lookup"><span data-stu-id="0738d-198">When change data capture is enabled on a database, it is useful to take snapshots of the sys.dm_cdc_log_scan_sessions view and the sys.dm_cdc_errors view at regular intervals for later analysis.</span></span> <span data-ttu-id="0738d-199">下列程序會設定從 sys.dm_cdc_log_scan_sessions 管理檢視中收集取樣資料的資料收集器。</span><span class="sxs-lookup"><span data-stu-id="0738d-199">The following procedure sets up a data collector for collecting sample data from the sys.dm_cdc_log_scan_sessions management view.</span></span>  
  
 <span data-ttu-id="0738d-200">**正在設定資料收集**</span><span class="sxs-lookup"><span data-stu-id="0738d-200">**Configuring Data Collection**</span></span>  
  
1.  <span data-ttu-id="0738d-201">啟用資料收集器並設定管理資料倉儲。</span><span class="sxs-lookup"><span data-stu-id="0738d-201">Enable data collector and configure a management data warehouse.</span></span> <span data-ttu-id="0738d-202">如需詳細資訊，請參閱 [管理資料收集](../data-collection/data-collection.md)。</span><span class="sxs-lookup"><span data-stu-id="0738d-202">For more information, see [Manage Data Collection](../data-collection/data-collection.md).</span></span>  
  
2.  <span data-ttu-id="0738d-203">執行下列程式碼來建立異動資料擷取的自訂收集器。</span><span class="sxs-lookup"><span data-stu-id="0738d-203">Execute the following code to create a custom collector for change data capture.</span></span>  
  
    ```sql  
    USE msdb;  
  
    DECLARE @schedule_uid uniqueidentifier;  
  
    -- Collect and upload data every 5 minutes  
    SELECT @schedule_uid = (  
    SELECT schedule_uid from sysschedules_localserver_view   
    WHERE name = N'CollectorSchedule_Every_5min')  
  
    DECLARE @collection_set_id int;  
  
    EXEC dbo.sp_syscollector_create_collection_set  
    @name = N' CDC Performance Data Collector',  
    @schedule_uid = @schedule_uid,          
    @collection_mode = 0,                   
    @days_until_expiration = 30,                
    @description = N'This collection set collects CDC metadata',  
    @collection_set_id = @collection_set_id output;  
  
    -- Create a collection item using statistics from   
    -- the change data capture dynamic management view.  
    DECLARE @parameters xml;  
    DECLARE @collection_item_id int;  
  
    SELECT @parameters = CONVERT(xml,   
        N'<TSQLQueryCollector>  
            <Query>  
              <Value>SELECT * FROM sys.dm_cdc_log_scan_sessions</Value>  
              <OutputTable>cdc_log_scan_data</OutputTable>  
            </Query>  
          </TSQLQueryCollector>');  
  
    EXEC dbo.sp_syscollector_create_collection_item  
    @collection_set_id = @collection_set_id,  
    @collector_type_uid = N'302E93D1-3424-4BE7-AA8E-84813ECF2419',  
    @name = ' CDC Performance Data Collector',  
    @frequency = 5,   
    @parameters = @parameters,  
    @collection_item_id = @collection_item_id output;  
  
    GO  
    ```  
  
3.  <span data-ttu-id="0738d-204">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，展開 **[管理]** ，然後展開 **[資料收集]** 。</span><span class="sxs-lookup"><span data-stu-id="0738d-204">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], expand **Management**, and then expand **Data Collection**.</span></span> <span data-ttu-id="0738d-205">以滑鼠右鍵按一下 **[CDC 效能資料收集器]**，然後按一下 **[啟動資料收集組]**。</span><span class="sxs-lookup"><span data-stu-id="0738d-205">Right click **CDC Performance Data Collector**, and then click **Start Data Collection Set**.</span></span>  
  
4.  <span data-ttu-id="0738d-206">在步驟 1 中設定的資料倉儲內，找出資料表 custom_snapshots.cdc_log_scan_data。</span><span class="sxs-lookup"><span data-stu-id="0738d-206">In the data warehouse you configured in step 1, locate the table custom_snapshots.cdc_log_scan_data.</span></span> <span data-ttu-id="0738d-207">這份資料表會提供記錄檔掃描工作階段之資料的歷程記錄快照集。</span><span class="sxs-lookup"><span data-stu-id="0738d-207">This table provides a historical snapshot of data from log scan sessions.</span></span> <span data-ttu-id="0738d-208">這份資料表可用於分析經過一段時間的延遲、輸送量和其他效能量值。</span><span class="sxs-lookup"><span data-stu-id="0738d-208">This data can be used to analyze latency, throughput, and other performance measures over time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0738d-209">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0738d-209">See Also</span></span>  
 <span data-ttu-id="0738d-210">[追蹤資料變更 &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0738d-210">[Track Data Changes &#40;SQL Server&#41;](track-data-changes-sql-server.md) </span></span>  
 <span data-ttu-id="0738d-211">[關於異動資料擷取 &#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0738d-211">[About Change Data Capture &#40;SQL Server&#41;](../track-changes/about-change-data-capture-sql-server.md) </span></span>  
 <span data-ttu-id="0738d-212">[啟用和停用異動資料擷取 &#40;SQL Server&#41;](enable-and-disable-change-data-capture-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0738d-212">[Enable and Disable Change Data Capture &#40;SQL Server&#41;](enable-and-disable-change-data-capture-sql-server.md) </span></span>  
 [<span data-ttu-id="0738d-213">使用異動資料 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0738d-213">Work with Change Data &#40;SQL Server&#41;</span></span>](work-with-change-data-sql-server.md)  
  
  
