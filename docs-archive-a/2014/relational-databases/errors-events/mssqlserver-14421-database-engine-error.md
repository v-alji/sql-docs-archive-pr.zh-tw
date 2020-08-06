---
title: MSSQLSERVER_14421 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 14421 (Database Engine error)
ms.assetid: 03e76d4a-d463-4673-8843-08e4ecaefe27
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d6bc793911797c334d87238ec46531f7afbf63ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598957"
---
# <a name="mssqlserver_14421"></a><span data-ttu-id="0b0af-102">MSSQLSERVER_14421</span><span class="sxs-lookup"><span data-stu-id="0b0af-102">MSSQLSERVER_14421</span></span>
    
## <a name="details"></a><span data-ttu-id="0b0af-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="0b0af-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="0b0af-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="0b0af-104">Product Name</span></span>|<span data-ttu-id="0b0af-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="0b0af-105">SQL Server</span></span>|  
|<span data-ttu-id="0b0af-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="0b0af-106">Event ID</span></span>|<span data-ttu-id="0b0af-107">14421</span><span class="sxs-lookup"><span data-stu-id="0b0af-107">14421</span></span>|  
|<span data-ttu-id="0b0af-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="0b0af-108">Event Source</span></span>|<span data-ttu-id="0b0af-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="0b0af-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="0b0af-110">元件</span><span class="sxs-lookup"><span data-stu-id="0b0af-110">Component</span></span>|<span data-ttu-id="0b0af-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="0b0af-111">SQLEngine</span></span>|  
|<span data-ttu-id="0b0af-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="0b0af-112">Symbolic Name</span></span>|<span data-ttu-id="0b0af-113">SQLErrorNum14421</span><span class="sxs-lookup"><span data-stu-id="0b0af-113">SQLErrorNum14421</span></span>|  
|<span data-ttu-id="0b0af-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="0b0af-114">Message Text</span></span>|<span data-ttu-id="0b0af-115">記錄傳送次要資料庫 %s.%s 的還原臨界值為 %d 分鐘，而且未同步。已經有 %d 分鐘未執行還原。</span><span class="sxs-lookup"><span data-stu-id="0b0af-115">The log shipping secondary database %s.%s has restore threshold of %d minutes and is out of sync. No restore was performed for %d minutes.</span></span> <span data-ttu-id="0b0af-116">還原的延遲為 %d 分鐘。</span><span class="sxs-lookup"><span data-stu-id="0b0af-116">Restored latency is %d minutes.</span></span> <span data-ttu-id="0b0af-117">檢查代理程式記錄和記錄傳送監視器資訊。</span><span class="sxs-lookup"><span data-stu-id="0b0af-117">Check agent log and logshipping monitor information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="0b0af-118">說明</span><span class="sxs-lookup"><span data-stu-id="0b0af-118">Explanation</span></span>  
 <span data-ttu-id="0b0af-119">此訊息表示記錄傳送未同步，而且超過還原臨界值。</span><span class="sxs-lookup"><span data-stu-id="0b0af-119">This message indicates that log shipping is out of synchronization beyond the restore threshold.</span></span> <span data-ttu-id="0b0af-120">還原臨界值是指產生訊息之前，還原作業之間經歷的分鐘數。</span><span class="sxs-lookup"><span data-stu-id="0b0af-120">The restore threshold is the number of minutes that can elapse between restore operations before a message is generated.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="0b0af-121">可能的原因</span><span class="sxs-lookup"><span data-stu-id="0b0af-121">Possible Causes</span></span>  
 <span data-ttu-id="0b0af-122">此訊息不一定會指出記錄傳送發生問題。</span><span class="sxs-lookup"><span data-stu-id="0b0af-122">This message does not necessarily indicate a problem with log shipping.</span></span> <span data-ttu-id="0b0af-123">不過，此訊息可能表示發生下列其中一個問題︰</span><span class="sxs-lookup"><span data-stu-id="0b0af-123">Instead, this message might indicate one of the following problems:</span></span>  
  
-   <span data-ttu-id="0b0af-124">還原作業並未執行。</span><span class="sxs-lookup"><span data-stu-id="0b0af-124">The restore job is not running.</span></span>  
  
     <span data-ttu-id="0b0af-125">作業未執行的可能原因如下︰次要伺服器執行個體上的 SQL Server Agent 服務未執行、作業已停用，或是作業的排程已變更。</span><span class="sxs-lookup"><span data-stu-id="0b0af-125">Possible causes of the job not running include the following: the SQL Server Agent service on the secondary server instance is not running, the job is disabled, or the schedule of the job has been changed.</span></span>  
  
-   <span data-ttu-id="0b0af-126">還原作業將失敗。</span><span class="sxs-lookup"><span data-stu-id="0b0af-126">The restore job is failing.</span></span>  
  
     <span data-ttu-id="0b0af-127">作業失敗的可能原因如下︰還原資料夾路徑無效、磁碟已滿，或是 RESTORE 陳述式可能失敗等任何其他原因。</span><span class="sxs-lookup"><span data-stu-id="0b0af-127">Possible causes of the job failing include the following: the restore folder path is not valid, the disk is full, or any other reason that the RESTORE statement could fail.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="0b0af-128">使用者動作</span><span class="sxs-lookup"><span data-stu-id="0b0af-128">User Action</span></span>  
 <span data-ttu-id="0b0af-129">若要對此訊息進行疑難排解︰</span><span class="sxs-lookup"><span data-stu-id="0b0af-129">To troubleshoot this message:</span></span>  
  
-   <span data-ttu-id="0b0af-130">請確定次要伺服器執行個體正在執行 SQL Server Agent 服務、此次要資料庫的還原作業已啟用，並且會依照排程以適當的頻率執行。</span><span class="sxs-lookup"><span data-stu-id="0b0af-130">Make sure that the SQL Server Agent service is running for the secondary server instance and that the restore job for this secondary database is enabled and is scheduled to run at the appropriate frequency.</span></span>  
  
-   <span data-ttu-id="0b0af-131">次要伺服器上的還原作業可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="0b0af-131">The restore job on the secondary server might be failing.</span></span> <span data-ttu-id="0b0af-132">在此情況下，請檢查還原作業的作業記錄以找出原因。</span><span class="sxs-lookup"><span data-stu-id="0b0af-132">In this case, check the job history for the restore job to look for the cause.</span></span>  
  
-   <span data-ttu-id="0b0af-133">次要伺服器執行個體上執行的記錄傳送還原作業，可能無法連接到監視伺服器執行個體以更新 **log_shipping_monitor_secondary** 資料表。</span><span class="sxs-lookup"><span data-stu-id="0b0af-133">The log shipping restore job, which runs on the secondary server instance, might not be able to connect to the monitor server instance to update the **log_shipping_monitor_secondary** table.</span></span> <span data-ttu-id="0b0af-134">這可能是監視伺服器執行個體與次要伺服器執行個體之間的驗證問題所引起的。</span><span class="sxs-lookup"><span data-stu-id="0b0af-134">This might be caused by an authentication problem between the monitor server instance and the secondary server instance.</span></span>  
  
-   <span data-ttu-id="0b0af-135">備份警示臨界值的值可能不正確。</span><span class="sxs-lookup"><span data-stu-id="0b0af-135">The backup alert threshold might have an incorrect value.</span></span> <span data-ttu-id="0b0af-136">這個值最好是設定為還原作業頻率的三倍以上。</span><span class="sxs-lookup"><span data-stu-id="0b0af-136">Ideally, this value is set to at least three times the frequency of the restore job.</span></span> <span data-ttu-id="0b0af-137">如果您在設定並執行記錄傳送之後變更還原作業的頻率，則必須跟著更新備份警示臨界值的值。</span><span class="sxs-lookup"><span data-stu-id="0b0af-137">If you change the frequency of the restore job after log shipping is configured and functional, you must update the value of the backup alert threshold accordingly.</span></span>  
  
-   <span data-ttu-id="0b0af-138">當監視伺服器執行個體離線之後又再度連線時，**log_shipping_monitor_secondary** 資料表會在警示訊息作業執行之後才更新為最新的值。</span><span class="sxs-lookup"><span data-stu-id="0b0af-138">When the monitor server instance goes offline and then comes back online, the **log_shipping_monitor_secondary** table is not updated with the current values before the alert message job runs.</span></span> <span data-ttu-id="0b0af-139">若還原作業成功但顯示「找不到可套用至次要資料庫的記錄備份檔案」，可能會發生錯誤 14421。</span><span class="sxs-lookup"><span data-stu-id="0b0af-139">Error 14421 can be raised when a restore job succeeds with, "Could not find a log backup file that could be applied to secondary database."</span></span> <span data-ttu-id="0b0af-140">發生此錯誤時，還原時間便不會更新。</span><span class="sxs-lookup"><span data-stu-id="0b0af-140">When this occurs, the restore time is not updated.</span></span> <span data-ttu-id="0b0af-141">這個情況的錯誤原因可能是複製作業發生問題。</span><span class="sxs-lookup"><span data-stu-id="0b0af-141">The cause of the error in this case might be an issue with the copy job.</span></span>  
  
     <span data-ttu-id="0b0af-142">若要以次要資料庫的最新資料更新監視資料表，請在次要伺服器執行個體上執行 **sp_refresh_log_shipping_monitor**。</span><span class="sxs-lookup"><span data-stu-id="0b0af-142">To update the monitor tables with the latest data for the secondary database, run **sp_refresh_log_shipping_monitor** on the secondary server instance.</span></span>  
  
-   <span data-ttu-id="0b0af-143">次要或監視伺服器執行個體上的日期或時間不正確。</span><span class="sxs-lookup"><span data-stu-id="0b0af-143">On the secondary or monitor server instance, the date or time is incorrect.</span></span> <span data-ttu-id="0b0af-144">這可能也會產生警示訊息。</span><span class="sxs-lookup"><span data-stu-id="0b0af-144">This may also generate alert messages.</span></span> <span data-ttu-id="0b0af-145">可能是其中一個執行個體上的系統日期或時間經過修改所引起的。</span><span class="sxs-lookup"><span data-stu-id="0b0af-145">Possibly the system date or time was modified on the one of them.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0b0af-146">兩個伺服器執行個體上使用不同時區，應不致產生問題。</span><span class="sxs-lookup"><span data-stu-id="0b0af-146">Different time zones for the two server instances should not cause a problem.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b0af-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b0af-147">See Also</span></span>  
 <span data-ttu-id="0b0af-148">[log_shipping_monitor_secondary &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0b0af-148">[log_shipping_monitor_secondary &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-secondary-transact-sql) </span></span>  
 <span data-ttu-id="0b0af-149">[關於記錄傳送 &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="0b0af-149">[About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md) </span></span>  
 <span data-ttu-id="0b0af-150">[sp_help_log_shipping_monitor_secondary &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0b0af-150">[sp_help_log_shipping_monitor_secondary &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-secondary-transact-sql) </span></span>  
 <span data-ttu-id="0b0af-151">[sp_refresh_log_shipping_monitor &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0b0af-151">[sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql) </span></span>  
 [<span data-ttu-id="0b0af-152">關於記錄傳送 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="0b0af-152">About Log Shipping &#40;SQL Server&#41;</span></span>](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
