---
title: 管理執行中的處理序 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- report processing [Reporting Services], status information
- jobs [Reporting Services]
- viewing jobs
- canceling jobs
- user jobs [Reporting Services]
- system jobs [Reporting Services]
- report processing [Reporting Services], managing running processes
- processes [Reporting Services]
- scanning processes [Reporting Services]
- status information [Reporting Services]
- report processing [Reporting Services]
- canceling subscriptions
- report servers [Reporting Services], jobs
- data-driven subscriptions
- displaying jobs
- subscriptions [Reporting Services], running processes
ms.assetid: 473e574e-f1ff-4ef9-bda6-7028b357ac42
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 002dda5a9708b68c6bbf978fb00e85f27b493da2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606056"
---
# <a name="manage-a-running-process"></a><span data-ttu-id="19914-102">管理執行中的處理序</span><span class="sxs-lookup"><span data-stu-id="19914-102">Manage a Running Process</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="19914-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 會監視作業在報表伺服器上執行的狀態。</span><span class="sxs-lookup"><span data-stu-id="19914-103">[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] monitors the status of jobs that are running on the report server.</span></span> <span data-ttu-id="19914-104">報表伺服器會以固定間隔執行進行中作業的掃描，並將狀態資訊寫入報表伺服器資料庫或服務應用程式資料庫 (如果是 SharePoint 模式)。</span><span class="sxs-lookup"><span data-stu-id="19914-104">At regular intervals, the report server does a scan of in-progress jobs and writes the status information to the report server database or the service application databases for SharePoint mode.</span></span> <span data-ttu-id="19914-105">如果下列任一個處理序進行中，作業就是進行中：在遠端或本機資料庫伺服器上的查詢執行、報表處理，以及報表轉譯。</span><span class="sxs-lookup"><span data-stu-id="19914-105">A job is in progress if any of the following processes are underway: query execution on a remote or local database server, report processing, and report rendering.</span></span>  
  
 <span data-ttu-id="19914-106">您可以管理 *使用者作業* 和 *系統作業*。</span><span class="sxs-lookup"><span data-stu-id="19914-106">You can manage both *user jobs* and *system jobs*.</span></span>  
  
-   <span data-ttu-id="19914-107">使用者作業是由個別使用者或訂閱起始。</span><span class="sxs-lookup"><span data-stu-id="19914-107">User jobs are initiated by an individual user or subscription.</span></span> <span data-ttu-id="19914-108">這包括視需要執行報表、要求報表記錄快照集、手動建立報表快照集，以及處理標準訂閱。</span><span class="sxs-lookup"><span data-stu-id="19914-108">This includes running a report on demand, requesting a report history snapshot, manually creating a report snapshot, and processing a standard subscription.</span></span>  
  
-   <span data-ttu-id="19914-109">系統作業不會由報表伺服器起始。</span><span class="sxs-lookup"><span data-stu-id="19914-109">System jobs are initiated by the report server.</span></span> <span data-ttu-id="19914-110">系統作業包括排程的報表執行快照集、排程的報表記錄快照集，以及資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="19914-110">System jobs include scheduled report execution snapshots, scheduled report history snapshots, and data-driven subscriptions.</span></span>  
  
 <span data-ttu-id="19914-111">報表處理時間與資源的使用，會依報表、查詢複雜度、資料量，以及針對報表所指定的轉譯格式而大有不同。</span><span class="sxs-lookup"><span data-stu-id="19914-111">Report processing time and resource use varies considerably depending on the report, the query complexity, the amount of data, and the rendering format that is specified for the report.</span></span> <span data-ttu-id="19914-112">針對本機資料來源進行簡單查詢的報表，通常會在幾毫秒內完成，並且不需要管理或微調。</span><span class="sxs-lookup"><span data-stu-id="19914-112">Reports that have simple queries against a local data source will often complete in milliseconds and never require management or tuning.</span></span> <span data-ttu-id="19914-113">相對地，以 PDF 或 Excel 轉譯的大型報表，則會依硬體資源、傳遞選項和是否同時執行其他處理序，而可能需要很長的處理時間。</span><span class="sxs-lookup"><span data-stu-id="19914-113">In contrast, a large report that is rendered in PDF or Excel might require significant processing time depending on hardware resources, delivery options, and whether other processes are running concurrently.</span></span> <span data-ttu-id="19914-114">在報表伺服器上，大多數長時間執行中的處理序，是等候查詢處理結束的報表轉譯作業和處理序。</span><span class="sxs-lookup"><span data-stu-id="19914-114">On a report server, most long-running processes are report rendering operations and processes that are waiting for query processing to conclude.</span></span> <span data-ttu-id="19914-115">偶爾您會因為要將電腦離線，或者停止要花太長時間完成的執行中作業，而必須取消報表處理序。</span><span class="sxs-lookup"><span data-stu-id="19914-115">Occasionally, you might need to cancel a report process if you want to take a computer offline, or stop a running job that is taking too long to complete.</span></span>  
  
 <span data-ttu-id="19914-116">您可以取消下列處理序：</span><span class="sxs-lookup"><span data-stu-id="19914-116">The following processes can be cancelled:</span></span>  
  
-   <span data-ttu-id="19914-117">視需要報表處理。</span><span class="sxs-lookup"><span data-stu-id="19914-117">On-demand report processing.</span></span>  
  
-   <span data-ttu-id="19914-118">排程報表處理。</span><span class="sxs-lookup"><span data-stu-id="19914-118">Scheduled report processing.</span></span>  
  
-   <span data-ttu-id="19914-119">個別使用者所擁有的標準訂閱。</span><span class="sxs-lookup"><span data-stu-id="19914-119">Standard subscriptions owned by individual users.</span></span>  
  
 <span data-ttu-id="19914-120">取消作業只會取消在報表伺服器上執行的處理序。</span><span class="sxs-lookup"><span data-stu-id="19914-120">Canceling a job only cancels the processes that are running on the report server.</span></span> <span data-ttu-id="19914-121">由於報表伺服器不會管理在其他電腦上進行的資料處理，因此您必須手動取消隨後在其他系統上遺棄的查詢處理序。</span><span class="sxs-lookup"><span data-stu-id="19914-121">Because the report server does not manage data processing that occurs on other computers, you must manually cancel query processes that are subsequently orphaned on other systems.</span></span> <span data-ttu-id="19914-122">請考慮指定查詢逾時值，以自動關閉花太長時間執行的查詢。</span><span class="sxs-lookup"><span data-stu-id="19914-122">Consider specifying query time-out values to automatically shut down queries that are taking too long to execute.</span></span> <span data-ttu-id="19914-123">如需詳細資訊，請參閱[設定報表和共用資料集處理的逾時值 &#40;SSRS&#41;](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="19914-123">For more information, see [Setting Time-out Values for Report and Shared Dataset Processing &#40;SSRS&#41;](../report-server/setting-time-out-values-for-report-and-shared-dataset-processing-ssrs.md).</span></span> <span data-ttu-id="19914-124">如需暫時暫停報表的詳細資訊，請參閱[暫停報表和訂閱處理](disable-or-pause-report-and-subscription-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="19914-124">For more information about temporarily pausing a report, see [Pause Report and Subscription Processing](disable-or-pause-report-and-subscription-processing.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="19914-125">很少數的情況下，您可能需要重新啟動伺服器才能取消處理序。</span><span class="sxs-lookup"><span data-stu-id="19914-125">In rare circumstances, you may need to restart the server to cancel a process.</span></span> <span data-ttu-id="19914-126">如果是 SharePoint 模式，您可能需要重新啟動裝載 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式的應用程式集區。</span><span class="sxs-lookup"><span data-stu-id="19914-126">For SharePoint mode, you may need to restart the application pool hosting the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="19914-127">如需詳細資訊，請參閱 [啟動與停止報表伺服器服務](../report-server/start-and-stop-the-report-server-service.md)。</span><span class="sxs-lookup"><span data-stu-id="19914-127">For more information, see [Start and Stop the Report Server Service](../report-server/start-and-stop-the-report-server-service.md).</span></span>  
  
 <span data-ttu-id="19914-128">本主題內容：</span><span class="sxs-lookup"><span data-stu-id="19914-128">In this Topic:</span></span>  
  
-   [<span data-ttu-id="19914-129">檢視和取消作業 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="19914-129">View and Cancel Jobs (Native Mode)</span></span>](#bkmk_native)  
  
-   [<span data-ttu-id="19914-130">檢視和取消作業 (SharePoint 模式)</span><span class="sxs-lookup"><span data-stu-id="19914-130">View and Cancel Jobs (SharePoint Mode)</span></span>](#bkmk_sharepoint)  
  
-   [<span data-ttu-id="19914-131">以程式設計方式管理作業</span><span class="sxs-lookup"><span data-stu-id="19914-131">Managing Jobs Programmatically</span></span>](#bkmk_programmatically)  
  
##  <a name="view-and-cancel-jobs-native-mode"></a><a name="bkmk_native"></a> <span data-ttu-id="19914-132">檢視和取消作業 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="19914-132">View and Cancel Jobs (Native Mode)</span></span>  
 <span data-ttu-id="19914-133">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 來檢視或取消在報表伺服器上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="19914-133">You can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to view or cancel a job that is running on the report server.</span></span> <span data-ttu-id="19914-134">您必須重新整理頁面，以便擷取目前正在執行之作業的清單，或從報表伺服器資料庫取得最新的作業狀態。</span><span class="sxs-lookup"><span data-stu-id="19914-134">You must refresh the page to retrieve a list of jobs that are currently running or to get up-to-date job status from the report server database.</span></span> <span data-ttu-id="19914-135">當您在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中連接至報表伺服器時，可以開啟 [作業] 資料夾來檢視報表伺服器電腦上目前正在處理之報表的清單。</span><span class="sxs-lookup"><span data-stu-id="19914-135">When you connect to a report server in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can open a Jobs folder to view a list of reports that are currently processing on the report server computer.</span></span> <span data-ttu-id="19914-136">每項作業的狀態資訊都會顯示在 [作業屬性] 頁面中。</span><span class="sxs-lookup"><span data-stu-id="19914-136">Status information for each job is displayed in the Job Properties page.</span></span> <span data-ttu-id="19914-137">您可以透過開啟 [取消報表伺服器作業] 對話方塊，檢視所有作業的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="19914-137">You can view status information for all jobs by opening the Cancel Report Server Jobs dialog box.</span></span>  
  
 <span data-ttu-id="19914-138">您可以使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 來檢視或取消在報表伺服器上執行的作業。</span><span class="sxs-lookup"><span data-stu-id="19914-138">You can use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to view or cancel a job that is running on the report server.</span></span> <span data-ttu-id="19914-139">您必須重新整理頁面，以便擷取目前正在執行之作業的清單，或從報表伺服器資料庫取得最新的作業狀態。</span><span class="sxs-lookup"><span data-stu-id="19914-139">You must refresh the page to retrieve a list of jobs that are currently running or to get up-to-date job status from the report server database.</span></span> <span data-ttu-id="19914-140">當您在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中連接至報表伺服器時，可以開啟 [作業] 資料夾來檢視報表伺服器電腦上目前正在處理之報表的清單。</span><span class="sxs-lookup"><span data-stu-id="19914-140">When you connect to a report server in [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], you can open a Jobs folder to view a list of reports that are currently processing on the report server computer.</span></span> <span data-ttu-id="19914-141">每項作業的狀態資訊都會顯示在 [作業屬性] 頁面中。</span><span class="sxs-lookup"><span data-stu-id="19914-141">Status information for each job is displayed in the Job Properties page.</span></span> <span data-ttu-id="19914-142">您可以透過開啟 [取消報表伺服器作業] 對話方塊，檢視所有作業的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="19914-142">You can view status information for all jobs by opening the Cancel Report Server Jobs dialog box.</span></span>  
  
 <span data-ttu-id="19914-143">您無法使用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 來列出或取消模型產生、模型處理或資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="19914-143">You cannot use [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to list or cancel model generation, model processing, or data-driven subscriptions.</span></span> <span data-ttu-id="19914-144">Reporting Services 不會提供取消模型產生或處理的方式。</span><span class="sxs-lookup"><span data-stu-id="19914-144">Reporting a Services does not provide a way to cancel model generation or processing.</span></span> <span data-ttu-id="19914-145">不過，您可以使用本主題所提供的指示來取消資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="19914-145">However, you can cancel data-driven subscriptions using the instructions provided in this topic.</span></span>  
  
### <a name="how-to-cancel-report-processing-or-subscription"></a><span data-ttu-id="19914-146">如何取消報表處理或訂閱</span><span class="sxs-lookup"><span data-stu-id="19914-146">How to Cancel Report Processing or Subscription</span></span>  
  
1.  <span data-ttu-id="19914-147">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]中，連接至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="19914-147">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], connect to the report server.</span></span> <span data-ttu-id="19914-148">如需指示，請參閱 [連接到 Management Studio 中的報表伺服器](../tools/connect-to-a-report-server-in-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="19914-148">For instructions, see [Connect to a Report Server in Management Studio](../tools/connect-to-a-report-server-in-management-studio.md).</span></span>  
  
2.  <span data-ttu-id="19914-149">開啟 **[作業]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="19914-149">Open the **Jobs** folder.</span></span>  
  
3.  <span data-ttu-id="19914-150">以滑鼠右鍵按一下報表，然後按一下 [取消作業]  。</span><span class="sxs-lookup"><span data-stu-id="19914-150">Right-click the report and then click **Cancel Jobs**.</span></span>  
  
### <a name="how-to-cancel-a-data-driven-subscription"></a><span data-ttu-id="19914-151">如何取消資料驅動訂閱</span><span class="sxs-lookup"><span data-stu-id="19914-151">How to Cancel a Data-driven Subscription</span></span>  
  
1.  <span data-ttu-id="19914-152">在文字編輯器中開啟 RSReportServer.config 檔。</span><span class="sxs-lookup"><span data-stu-id="19914-152">Open the RSReportServer.config file in a text editor.</span></span>  
  
2.  <span data-ttu-id="19914-153">尋找 `IsNotificationService`。</span><span class="sxs-lookup"><span data-stu-id="19914-153">Find `IsNotificationService`.</span></span>  
  
3.  <span data-ttu-id="19914-154">將它設為 `False`。</span><span class="sxs-lookup"><span data-stu-id="19914-154">Set it to `False`.</span></span>  
  
4.  <span data-ttu-id="19914-155">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="19914-155">Save the file.</span></span>  
  
5.  <span data-ttu-id="19914-156">在報表管理員中，從報表的 [訂閱] 索引標籤或 [我的訂閱]  中刪除資料驅動訂閱。</span><span class="sxs-lookup"><span data-stu-id="19914-156">In Report Manager, delete the data-driven subscription from the Subscriptions tab of the report or from **My Subscriptions**.</span></span>  
  
6.  <span data-ttu-id="19914-157">刪除訂閱之後，請在 RSReportServer.config 檔中，尋找 `IsNotificationService`，然後將它設為 `True`。</span><span class="sxs-lookup"><span data-stu-id="19914-157">After you delete the subscription, in the RSReportServer.config file, find `IsNotificationService` and set it to `True`.</span></span>  
  
7.  <span data-ttu-id="19914-158">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="19914-158">Save the file.</span></span>  
  
### <a name="configuring-frequency-settings-for-retrieving-job-status"></a><span data-ttu-id="19914-159">設定擷取作業狀態的頻率設定</span><span class="sxs-lookup"><span data-stu-id="19914-159">Configuring Frequency Settings for Retrieving Job Status</span></span>  
 <span data-ttu-id="19914-160">執行中的作業會儲存在報表伺服器的暫存資料庫中。</span><span class="sxs-lookup"><span data-stu-id="19914-160">A running job is stored in the report server temporary database.</span></span> <span data-ttu-id="19914-161">您可以修改 RSReportServer.config 檔案中的組態設定，以控制報表伺服器掃描進行中作業的頻率，和執行中作業的狀態要等候多久才會從新的變更為執行中。</span><span class="sxs-lookup"><span data-stu-id="19914-161">You can modify configuration settings in the RSReportServer.config file to control how often the report server scans for in-progress jobs and the interval after which the status of a running job changes from new to running.</span></span> <span data-ttu-id="19914-162">`RunningRequestsDbCycle` 設定會指定報表伺服器掃描執行中處理序的頻率。</span><span class="sxs-lookup"><span data-stu-id="19914-162">The `RunningRequestsDbCycle` setting specifies how often the report server scans for running processes.</span></span> <span data-ttu-id="19914-163">依預設，每 60 秒就會記錄狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="19914-163">By default, status information is recorded every 60 seconds.</span></span> <span data-ttu-id="19914-164">`RunningRequestsAge` 設定會指定作業從新的轉換為執行中的間隔。</span><span class="sxs-lookup"><span data-stu-id="19914-164">The `RunningRequestsAge` setting specifies the interval at which a job is transitioned from new to running.</span></span>  
  
##  <a name="view-and-cancel-jobs-sharepoint-mode"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="19914-165">檢視和取消作業 (SharePoint 模式)</span><span class="sxs-lookup"><span data-stu-id="19914-165">View and Cancel Jobs (SharePoint Mode)</span></span>  
 <span data-ttu-id="19914-166">使用 SharePoint 管理中心，為每個 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式完成 SharePoint 模式部署中的作業管理。</span><span class="sxs-lookup"><span data-stu-id="19914-166">Management of jobs in a SharePoint mode deployment is completed using SharePoint Central Administration, for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
#### <a name="to-manage-jobs-in-sharepoint-mode"></a><span data-ttu-id="19914-167">若要管理 SharePoint 模式下的作業</span><span class="sxs-lookup"><span data-stu-id="19914-167">To manage jobs in SharePoint mode</span></span>  
  
1.  <span data-ttu-id="19914-168">在 SharePoint 管理中心中，按一下 **[管理服務應用程式]** 。</span><span class="sxs-lookup"><span data-stu-id="19914-168">In SharePoint Central Administration, click **Manage service applications**.</span></span>  
  
2.  <span data-ttu-id="19914-169">找出並按一下 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式的名稱，以開啟 [管理應用程式] 頁面。</span><span class="sxs-lookup"><span data-stu-id="19914-169">Find and click the name of your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application to open the manage application page.</span></span>  
  
3.  <span data-ttu-id="19914-170">按一下 **[管理作業]**</span><span class="sxs-lookup"><span data-stu-id="19914-170">Click **Manage Jobs**</span></span>  
  
4.  <span data-ttu-id="19914-171">按一下 **[作業識別碼]** 以查看作業的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="19914-171">Click the **Job Id** to see the details of the job.</span></span>  
  
5.  <span data-ttu-id="19914-172">或按一下適用於您作業的方塊，然後按一下 **[刪除]** 以取消作業。</span><span class="sxs-lookup"><span data-stu-id="19914-172">Or click the box for your job and click **Delete** to cancel the job.</span></span> <span data-ttu-id="19914-173">刪除作業並不會刪除訂閱。</span><span class="sxs-lookup"><span data-stu-id="19914-173">Deleting the job does not delete the subscription.</span></span>  
  
##  <a name="managing-jobs-programmatically"></a><a name="bkmk_programmatically"></a> <span data-ttu-id="19914-174">以程式設計方式管理作業</span><span class="sxs-lookup"><span data-stu-id="19914-174">Managing Jobs Programmatically</span></span>  
 <span data-ttu-id="19914-175">您可以用程式設計方式或利用指令碼來管理作業。</span><span class="sxs-lookup"><span data-stu-id="19914-175">You can manage jobs programmatically or by using a script.</span></span> <span data-ttu-id="19914-176">如需詳細資訊，請參閱 <xref:ReportService2010.ReportingService2010.ListJobs%2A>和 <xref:ReportService2010.ReportingService2010.CancelJob%2A>。</span><span class="sxs-lookup"><span data-stu-id="19914-176">For more information, see <xref:ReportService2010.ReportingService2010.ListJobs%2A>, <xref:ReportService2010.ReportingService2010.CancelJob%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19914-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="19914-177">See Also</span></span>  
 <span data-ttu-id="19914-178">[取消報表伺服器作業 &#40;Management Studio&#41;](../tools/cancel-report-server-jobs-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="19914-178">[Cancel Report Server Jobs &#40;Management Studio&#41;](../tools/cancel-report-server-jobs-management-studio.md) </span></span>  
 <span data-ttu-id="19914-179">[作業屬性 &#40;Management Studio&#41;](../tools/job-properties-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="19914-179">[Job Properties &#40;Management Studio&#41;](../tools/job-properties-management-studio.md) </span></span>  
 <span data-ttu-id="19914-180">[修改 Reporting Services 組態檔 &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) </span><span class="sxs-lookup"><span data-stu-id="19914-180">[Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](../report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md) </span></span>  
 <span data-ttu-id="19914-181">[Rsreportserver.config 設定檔](../report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="19914-181">[RSReportServer Configuration File](../report-server/rsreportserver-config-configuration-file.md) </span></span>  
 <span data-ttu-id="19914-182">[報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="19914-182">[Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md) </span></span>  
 [<span data-ttu-id="19914-183">監視報表伺服器效能</span><span class="sxs-lookup"><span data-stu-id="19914-183">Monitoring Report Server Performance</span></span>](../report-server/monitoring-report-server-performance.md)  
  
  
