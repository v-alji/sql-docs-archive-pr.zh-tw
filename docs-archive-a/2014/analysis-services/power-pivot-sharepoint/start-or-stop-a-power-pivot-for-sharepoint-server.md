---
title: 啟動或停止 PowerPivot for SharePoint 伺服器 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e38e6366-9f20-4db0-b2a8-da7d5adf00eb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 41c38f8f96fcbc9175cf0f52dafd8b28a83e5497
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596313"
---
# <a name="start-or-stop-a-powerpivot-for-sharepoint-server"></a><span data-ttu-id="1af7b-102">啟動或停止 PowerPivot for SharePoint 伺服器</span><span class="sxs-lookup"><span data-stu-id="1af7b-102">Start or Stop a PowerPivot for SharePoint Server</span></span>
  <span data-ttu-id="1af7b-103">PowerPivot 系統服務和 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 實例會在相同的本機應用程式伺服器上一起運作，以支援 SharePoint 伺服器陣列中的協調要求和資料處理。</span><span class="sxs-lookup"><span data-stu-id="1af7b-103">PowerPivot System Service and an [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance operate together on the same local application server to support coordinated request and data processing in a SharePoint farm.</span></span>  
  
 <span data-ttu-id="1af7b-104">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="1af7b-104">This topic contains the following sections:</span></span>  
  
 [<span data-ttu-id="1af7b-105">服務相依性</span><span class="sxs-lookup"><span data-stu-id="1af7b-105">Service Dependencies</span></span>](#dependencies)  
  
 [<span data-ttu-id="1af7b-106">啟動或停止服務</span><span class="sxs-lookup"><span data-stu-id="1af7b-106">Start or Stop the Services</span></span>](#startstop)  
  
 [<span data-ttu-id="1af7b-107">停止 PowerPivot 伺服器的影響</span><span class="sxs-lookup"><span data-stu-id="1af7b-107">Effects of Stopping a PowerPivot Server</span></span>](#effects)  
  
##  <a name="service-dependencies"></a><a name="dependencies"></a><span data-ttu-id="1af7b-108">服務相依性</span><span class="sxs-lookup"><span data-stu-id="1af7b-108">Service Dependencies</span></span>  
 <span data-ttu-id="1af7b-109">PowerPivot 系統服務與隨其一起安裝在相同實體伺服器上的本機 Analysis Services 伺服器執行個體具有相依性。</span><span class="sxs-lookup"><span data-stu-id="1af7b-109">The PowerPivot System Service has a dependency on the local Analysis Services server instance that is installed with it on the same physical server.</span></span> <span data-ttu-id="1af7b-110">如果您停止 PowerPivot 系統服務，也必須手動停止本機 Analysis Services 伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1af7b-110">If you stop the PowerPivot System Service, you must also manually stop the local Analysis Services server instance.</span></span> <span data-ttu-id="1af7b-111">如果某個服務執行中，但另一個服務並未執行，您將會遇到 PowerPivot 資料處理的要求配置錯誤。</span><span class="sxs-lookup"><span data-stu-id="1af7b-111">If one service is running without the other, you will encounter request allocation errors for PowerPivot data processing.</span></span>  
  
 <span data-ttu-id="1af7b-112">只有當您要診斷或疑難排解問題時，Analysis Services 伺服器才應該獨自執行。</span><span class="sxs-lookup"><span data-stu-id="1af7b-112">The Analysis Services server should only be run by itself if you are diagnosing or troubleshooting a problem.</span></span> <span data-ttu-id="1af7b-113">但是在所有其他情況下，此伺服器則需要在相同的伺服器上於本機執行的 PowerPivot 系統服務。</span><span class="sxs-lookup"><span data-stu-id="1af7b-113">In all other cases, the server requires the PowerPivot System Service that runs locally on the same server.</span></span>  
  
##  <a name="start-or-stop-the-services"></a><a name="startstop"></a><span data-ttu-id="1af7b-114">啟動或停止服務</span><span class="sxs-lookup"><span data-stu-id="1af7b-114">Start or Stop the Services</span></span>  
 <span data-ttu-id="1af7b-115">請務必使用管理中心來啟動或停止 PowerPivot 系統服務或 Analysis Services 伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1af7b-115">Always use Central Administration to start or stop the PowerPivot System Service or Analysis Services server instance.</span></span> <span data-ttu-id="1af7b-116">管理中心可讓您從相同的頁面一起啟動或停止服務。</span><span class="sxs-lookup"><span data-stu-id="1af7b-116">Central Administration allows you to start or stop the services together from the same page.</span></span> <span data-ttu-id="1af7b-117">此外，管理中心也會使用稱為 **一個或多個服務已經啟動或停止** 的計時器工作，以重新啟動它認為應該執行的服務。</span><span class="sxs-lookup"><span data-stu-id="1af7b-117">In addition, Central Administration uses a timer job called **One or more services have started or stopped** to restart services that it thinks should be running.</span></span> <span data-ttu-id="1af7b-118">如果您使用非 SharePoint 工具停止 PowerPivot 系統服務或 Analysis Services，此服務會在計時器工作執行時重新啟動。</span><span class="sxs-lookup"><span data-stu-id="1af7b-118">If you stop the PowerPivot System Service or Analysis Services using a non-SharePoint tool, the services will be restarted when the timer job runs.</span></span>  
  
 <span data-ttu-id="1af7b-119">啟動和停止服務是套用至實體服務執行個體的動作。</span><span class="sxs-lookup"><span data-stu-id="1af7b-119">Starting and stopping services is an action that applies to a physical service instance.</span></span> <span data-ttu-id="1af7b-120">如果伺服陣列中有其他 PowerPivot for SharePoint 伺服器，在伺服陣列中的其他伺服器會繼續接受 PowerPivot 資料的要求。</span><span class="sxs-lookup"><span data-stu-id="1af7b-120">If you have additional PowerPivot for SharePoint servers in the farm, the other servers within the farm will continue to accept requests for PowerPivot data.</span></span>  
  
 <span data-ttu-id="1af7b-121">您無法同時啟動或停止在伺服陣列的所有實體服務。</span><span class="sxs-lookup"><span data-stu-id="1af7b-121">You cannot start or stop all physical services simultaneously across the farm.</span></span> <span data-ttu-id="1af7b-122">您必須選取每部伺服器，然後啟動或停止特定服務。</span><span class="sxs-lookup"><span data-stu-id="1af7b-122">You must select each server and then start or stop a particular service.</span></span>  
  
 <span data-ttu-id="1af7b-123">您無法啟動、暫停或停止特定 Web 應用程式的 PowerPivot 系統服務，但是您可以從預設連接清單移除服務，使其無法使用。</span><span class="sxs-lookup"><span data-stu-id="1af7b-123">You cannot start, pause, or stop a PowerPivot System Service for a specific Web application, but you can remove a service from the default connection list to make it unavailable.</span></span> <span data-ttu-id="1af7b-124">如需詳細資訊，請參閱[在管理中心將 PowerPivot 服務應用程式連接到 SharePoint Web 應用程式](connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md)。</span><span class="sxs-lookup"><span data-stu-id="1af7b-124">For more information, see [Connect a PowerPivot Service Application to a SharePoint Web Application in Central Administration](connect-power-pivot-service-app-to-sharepoint-web-app-in-ca.md).</span></span>  
  
1.  <span data-ttu-id="1af7b-125">在管理中心的 [系統設定]\*\*\*\* 中，按一下 [管理伺服器上的服務]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1af7b-125">In Central Administration, in **System Settings**, click **Manage services on server**.</span></span>  
  
2.  <span data-ttu-id="1af7b-126">在 [伺服器] 頁面的頂端，按一下向下箭頭，然後按一下 [變更伺服器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="1af7b-126">At the top of the page, in Server, click the down arrow, and then click **Change Server**.</span></span>  
  
3.  <span data-ttu-id="1af7b-127">選取具有您要啟動或停止的 PowerPivot 系統服務或 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 執行個體的 SharePoint 伺服器。</span><span class="sxs-lookup"><span data-stu-id="1af7b-127">Select the SharePoint server that has the PowerPivot System Service or [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance that you want to start or stop.</span></span>  
  
4.  <span data-ttu-id="1af7b-128">選取服務，然後按一下動作。</span><span class="sxs-lookup"><span data-stu-id="1af7b-128">Select the service, and then click the action.</span></span> <span data-ttu-id="1af7b-129">請記得要以成對的方式啟動或停止服務。</span><span class="sxs-lookup"><span data-stu-id="1af7b-129">Remember to start or stop the services as a pair.</span></span> <span data-ttu-id="1af7b-130">如果您啟動或停止 PowerPivot 系統服務，請務必也啟動或停止在相同電腦上執行的 Analysis Services 伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1af7b-130">If you start or stop the PowerPivot System Service, be sure to also start or stop the Analysis Services server instance that runs on the same computer.</span></span>  
  
##  <a name="effects-of-stopping-a-powerpivot-server"></a><a name="effects"></a><span data-ttu-id="1af7b-131">停止 PowerPivot 服務器的影響</span><span class="sxs-lookup"><span data-stu-id="1af7b-131">Effects of Stopping a PowerPivot Server</span></span>  
 <span data-ttu-id="1af7b-132">下表描述在 SharePoint 伺服器上停止 PowerPivot 系統服務及 Analysis Services 服務的影響。</span><span class="sxs-lookup"><span data-stu-id="1af7b-132">The following table describes the effects of stopping the PowerPivot System Service and Analysis Services service on a SharePoint server.</span></span>  
  
|<span data-ttu-id="1af7b-133">影響的項目</span><span class="sxs-lookup"><span data-stu-id="1af7b-133">Effect on</span></span>|<span data-ttu-id="1af7b-134">描述</span><span class="sxs-lookup"><span data-stu-id="1af7b-134">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1af7b-135">現有的查詢</span><span class="sxs-lookup"><span data-stu-id="1af7b-135">Existing queries</span></span>|<span data-ttu-id="1af7b-136">在 Analysis Services 伺服器上進行中的查詢將會立即停止。</span><span class="sxs-lookup"><span data-stu-id="1af7b-136">Queries that are in progress on an Analysis Services server will stop immediately.</span></span> <span data-ttu-id="1af7b-137">使用者將會收到找不到資料或找不到資料來源連接的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1af7b-137">The user will get a data not found or data source connection not found error.</span></span>|  
|<span data-ttu-id="1af7b-138">目前正在處理的現有資料重新整理工作</span><span class="sxs-lookup"><span data-stu-id="1af7b-138">Existing data refresh jobs that are currently processing</span></span>|<span data-ttu-id="1af7b-139">在目前的 Analysis Services 伺服器上進行中的作業將會立即停止。</span><span class="sxs-lookup"><span data-stu-id="1af7b-139">Jobs that are in progress on the current Analysis Services server will stop immediately.</span></span> <span data-ttu-id="1af7b-140">資料重新整理將會失敗，而且會將錯誤記錄至資料重新整理記錄。</span><span class="sxs-lookup"><span data-stu-id="1af7b-140">Data refresh will fail and an error will be logged to data refresh history.</span></span><br /><br /> <span data-ttu-id="1af7b-141">在您使用 [SharePoint 管理中心] 中的 [檢查工作狀態] 頁面停止服務之前，您可以檢視目前工作的狀態。</span><span class="sxs-lookup"><span data-stu-id="1af7b-141">You can view the status of current jobs before you stop the service by using the Check job status page in SharePoint Central Administration.</span></span><br /><br /> <span data-ttu-id="1af7b-142">雖然要知道哪些作業目前正在處理是可能的，但是並沒有任何方法可檢視佇列本身是否有其他作業即將開始。</span><span class="sxs-lookup"><span data-stu-id="1af7b-142">While it is possible to know which jobs are currently processing, there is no way to view the queue itself to see whether other jobs are about to start.</span></span>|  
|<span data-ttu-id="1af7b-143">佇列中現有的資料重新整理要求</span><span class="sxs-lookup"><span data-stu-id="1af7b-143">Existing data refresh requests in the queue</span></span>|<span data-ttu-id="1af7b-144">已排程的資料重新整理要求，仍然會在處理佇列中，以等待排程的完整循環 (也就是在下一個開始時間之前，它會一直待在佇列中)。</span><span class="sxs-lookup"><span data-stu-id="1af7b-144">Scheduled data refresh requests will remain in the processing queue for a complete cycle of the schedule (that is, it stays in the queue until the next start time).</span></span> <span data-ttu-id="1af7b-145">如果到時仍未重新啟動 PowerPivot 系統服務，則會卸除資料重新整理要求並記錄錯誤。</span><span class="sxs-lookup"><span data-stu-id="1af7b-145">If the PowerPivot System Service is not restarted by then, the data refresh request will be dropped and an error will be logged.</span></span>|  
|<span data-ttu-id="1af7b-146">對於查詢或資料重新整理的新要求</span><span class="sxs-lookup"><span data-stu-id="1af7b-146">New requests for queries or data refresh</span></span>|<span data-ttu-id="1af7b-147">如果您停止伺服陣列中的唯一 PowerPivot for SharePoint 伺服器，將不會處理對 PowerPivot 資料的新要求，而且對於資料的要求將會導致找不到資料的錯誤。</span><span class="sxs-lookup"><span data-stu-id="1af7b-147">If you are stopping the only PowerPivot for SharePoint server in the farm, new requests for PowerPivot data will not be handled and a request for data will result in a data not found error.</span></span><br /><br /> <span data-ttu-id="1af7b-148">如果您有額外的 PowerPivot for SharePoint 伺服器，要求將會前往其中一個可用的伺服器。</span><span class="sxs-lookup"><span data-stu-id="1af7b-148">If you have additional PowerPivot for SharePoint servers, the request will go to one of the available servers.</span></span>|  
|<span data-ttu-id="1af7b-149">使用量資料</span><span class="sxs-lookup"><span data-stu-id="1af7b-149">Usage data</span></span>|<span data-ttu-id="1af7b-150">停止服務時將不會收集使用量資料。</span><span class="sxs-lookup"><span data-stu-id="1af7b-150">Usage data will not be collected while the services are stopped.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1af7b-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1af7b-151">See Also</span></span>  
 [<span data-ttu-id="1af7b-152">設定 PowerPivot 服務帳戶</span><span class="sxs-lookup"><span data-stu-id="1af7b-152">Configure PowerPivot Service Accounts</span></span>](configure-power-pivot-service-accounts.md)  
  
  
