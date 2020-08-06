---
title: MSSQLSERVER_14420 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 14420 (Database Engine error)
ms.assetid: 4a1d72b1-ab1b-4119-a11b-a8a05c6fdb45
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 7a17ab1e2281530b06c9ad27ac2a31672de0681e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594098"
---
# <a name="mssqlserver_14420"></a><span data-ttu-id="ccca4-102">MSSQLSERVER_14420</span><span class="sxs-lookup"><span data-stu-id="ccca4-102">MSSQLSERVER_14420</span></span>
    
## <a name="details"></a><span data-ttu-id="ccca4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ccca4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ccca4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ccca4-104">Product Name</span></span>|<span data-ttu-id="ccca4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ccca4-105">SQL Server</span></span>|  
|<span data-ttu-id="ccca4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ccca4-106">Event ID</span></span>|<span data-ttu-id="ccca4-107">14420</span><span class="sxs-lookup"><span data-stu-id="ccca4-107">14420</span></span>|  
|<span data-ttu-id="ccca4-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="ccca4-108">Event Source</span></span>|<span data-ttu-id="ccca4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ccca4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ccca4-110">元件</span><span class="sxs-lookup"><span data-stu-id="ccca4-110">Component</span></span>|<span data-ttu-id="ccca4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ccca4-111">SQLEngine</span></span>|  
|<span data-ttu-id="ccca4-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ccca4-112">Symbolic Name</span></span>|<span data-ttu-id="ccca4-113">SQLErrorNum14420</span><span class="sxs-lookup"><span data-stu-id="ccca4-113">SQLErrorNum14420</span></span>|  
|<span data-ttu-id="ccca4-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ccca4-114">Message Text</span></span>|<span data-ttu-id="ccca4-115">記錄傳送主要資料庫 %s.%s 的備份臨界值為 %d 分鐘，且已經有 %d 分鐘未執行備份記錄檔作業。</span><span class="sxs-lookup"><span data-stu-id="ccca4-115">The log shipping primary database %s.%s has backup threshold of %d minutes and has not performed a backup log operation for %d minutes.</span></span> <span data-ttu-id="ccca4-116">檢查代理程式記錄和記錄傳送監視器資訊。</span><span class="sxs-lookup"><span data-stu-id="ccca4-116">Check agent log and logshipping monitor information.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ccca4-117">說明</span><span class="sxs-lookup"><span data-stu-id="ccca4-117">Explanation</span></span>  
 <span data-ttu-id="ccca4-118">記錄傳送已經超過備份臨界值未執行同步處理。</span><span class="sxs-lookup"><span data-stu-id="ccca4-118">Log shipping is out of synchronization beyond the backup threshold.</span></span> <span data-ttu-id="ccca4-119">備份臨界值是指產生警示之前，記錄傳送備份作業之間所能經歷的分鐘數。</span><span class="sxs-lookup"><span data-stu-id="ccca4-119">The backup threshold is the number of minutes that are allowed to elapse between log-shipping backup jobs before an alert is generated.</span></span> <span data-ttu-id="ccca4-120">此訊息不一定會指出記錄傳送發生問題。</span><span class="sxs-lookup"><span data-stu-id="ccca4-120">This message does not necessarily indicate a problem with log shipping.</span></span> <span data-ttu-id="ccca4-121">不過，此訊息可能表示發生下列其中一個問題︰</span><span class="sxs-lookup"><span data-stu-id="ccca4-121">Instead, this message might indicate one of the following problems:</span></span>  
  
-   <span data-ttu-id="ccca4-122">備份作業並未執行。</span><span class="sxs-lookup"><span data-stu-id="ccca4-122">The backup job is not running.</span></span> <span data-ttu-id="ccca4-123">可能原因如下：主要伺服器執行個體上的 SQL Server Agent 服務未執行、作業已停用，或是作業的排程已變更。</span><span class="sxs-lookup"><span data-stu-id="ccca4-123">Possible causes for this include the following: the SQL Server Agent service on the primary server instance is not running, the job is disabled, or the job's schedule has been changed.</span></span>  
  
-   <span data-ttu-id="ccca4-124">備份作業將失敗。</span><span class="sxs-lookup"><span data-stu-id="ccca4-124">The backup job is failing.</span></span> <span data-ttu-id="ccca4-125">可能的原因如下：備份資料夾路徑無效、磁碟已滿，或是 BACKUP 陳述式可能失敗等任何其他原因。</span><span class="sxs-lookup"><span data-stu-id="ccca4-125">Possible causes for this include the following: the backup folder path is not valid, the disk is full, or any other reason that the BACKUP statement could fail.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ccca4-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ccca4-126">User Action</span></span>  
 <span data-ttu-id="ccca4-127">若要對此訊息進行疑難排解︰</span><span class="sxs-lookup"><span data-stu-id="ccca4-127">To troubleshoot this message:</span></span>  
  
-   <span data-ttu-id="ccca4-128">請確定主要伺服器執行個體正在執行 SQL Server Agent 服務，以及此主要資料庫的備份作業已啟用，並且已排程為根據適當的頻率執行。</span><span class="sxs-lookup"><span data-stu-id="ccca4-128">Make sure that the SQL Server Agent service is running for the primary server instance and that the backup job for this primary database is enabled and is scheduled to run at the appropriate frequency.</span></span>  
  
-   <span data-ttu-id="ccca4-129">主要伺服器上的備份作業可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="ccca4-129">The backup job on the primary server might be failing.</span></span> <span data-ttu-id="ccca4-130">在此情況下，請檢查備份作業的作業記錄以找出原因。</span><span class="sxs-lookup"><span data-stu-id="ccca4-130">In this case, examine the job history for the backup job to look for the cause.</span></span>  
  
-   <span data-ttu-id="ccca4-131">主要伺服器執行個體上執行的記錄傳送備份作業，可能無法連接到監視伺服器執行個體以更新 **log_shipping_monitor_primary** 資料表。</span><span class="sxs-lookup"><span data-stu-id="ccca4-131">The log shipping backup job, which runs on the primary server instance, might not be able to connect to the monitor server instance to update the **log_shipping_monitor_primary** table.</span></span> <span data-ttu-id="ccca4-132">這可能是監視伺服器執行個體與主要伺服器執行個體之間的驗證問題所引起的。</span><span class="sxs-lookup"><span data-stu-id="ccca4-132">This could be caused by an authentication problem between the monitor server instance and the primary server instance.</span></span>  
  
-   <span data-ttu-id="ccca4-133">備份警示臨界值的值可能不正確。</span><span class="sxs-lookup"><span data-stu-id="ccca4-133">The backup alert threshold might have an incorrect value.</span></span> <span data-ttu-id="ccca4-134">最好至少將這個值設定為備份作業頻率的三倍。</span><span class="sxs-lookup"><span data-stu-id="ccca4-134">Ideally, this value is set to at least three times the frequency of the backup job.</span></span> <span data-ttu-id="ccca4-135">如果您在設定並執行記錄傳送之後變更備份作業的頻率，則必須跟著更新備份警示臨界值的值。</span><span class="sxs-lookup"><span data-stu-id="ccca4-135">If you change the frequency of the backup job after log shipping is configured and functional, you must update the value of the backup alert threshold accordingly.</span></span>  
  
-   <span data-ttu-id="ccca4-136">當監視伺服器執行個體離線之後又再次連線時，**log_shipping_monitor_primary** 資料表會在警示訊息作業執行之後才更新為最新的值。</span><span class="sxs-lookup"><span data-stu-id="ccca4-136">When the monitor server instance goes offline and then comes back online, the **log_shipping_monitor_primary** table is not updated with the current values before the alert message job runs.</span></span> <span data-ttu-id="ccca4-137">若要以主要資料庫的最新資料更新監視資料表，請在主要伺服器執行個體上執行 **sp_refresh_log_shipping_monitor**。</span><span class="sxs-lookup"><span data-stu-id="ccca4-137">To update the monitor tables with the latest data for the primary database, run **sp_refresh_log_shipping_monitor** on the primary server instance.</span></span>  
  
-   <span data-ttu-id="ccca4-138">主要或監視伺服器執行個體上的日期或時間不正確。</span><span class="sxs-lookup"><span data-stu-id="ccca4-138">On the primary or monitor server instance, the date or time is incorrect.</span></span> <span data-ttu-id="ccca4-139">這可能也會產生警示訊息。</span><span class="sxs-lookup"><span data-stu-id="ccca4-139">This may also generate alert messages.</span></span> <span data-ttu-id="ccca4-140">可能是其中一個執行個體上的系統日期或時間經過修改所引起的。</span><span class="sxs-lookup"><span data-stu-id="ccca4-140">Possibly the system date or time was modified on the one of them.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ccca4-141">兩個伺服器執行個體上使用不同時區，應不致產生問題。</span><span class="sxs-lookup"><span data-stu-id="ccca4-141">Different time zones for the two server instances should not cause a problem.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ccca4-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ccca4-142">See Also</span></span>  
 <span data-ttu-id="ccca4-143">[log_shipping_monitor_primary &#40;Transact-sql&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccca4-143">[log_shipping_monitor_primary &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/log-shipping-monitor-primary-transact-sql) </span></span>  
 <span data-ttu-id="ccca4-144">[關於記錄傳送 &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ccca4-144">[About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md) </span></span>  
 <span data-ttu-id="ccca4-145">[sp_help_log_shipping_monitor_primary &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccca4-145">[sp_help_log_shipping_monitor_primary &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-help-log-shipping-monitor-primary-transact-sql) </span></span>  
 <span data-ttu-id="ccca4-146">[sp_refresh_log_shipping_monitor &#40;Transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="ccca4-146">[sp_refresh_log_shipping_monitor &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-refresh-log-shipping-monitor-transact-sql) </span></span>  
 [<span data-ttu-id="ccca4-147">關於記錄傳送 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ccca4-147">About Log Shipping &#40;SQL Server&#41;</span></span>](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
