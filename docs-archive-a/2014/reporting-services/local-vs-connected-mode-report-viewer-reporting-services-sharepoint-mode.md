---
title: 在報表檢視器中的原生模式與連接模式報表 (在 SharePoint 模式中 Reporting Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a230a9bb-6046-401f-b5e5-53ff6edf2264
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 805be8722a38252a9a44797b5e59d2136bc83d6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704961"
---
# <a name="local-mode-vs-connected-mode-reports-in-the-report-viewer-reporting-services-in-sharepoint-mode"></a><span data-ttu-id="ca34b-102">比較報表檢視器中的本機模式與連接模式報表 (SharePoint 模式的 Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="ca34b-102">Local Mode vs. Connected Mode Reports in the Report Viewer (Reporting Services in SharePoint Mode)</span></span>
  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]<span data-ttu-id="ca34b-103">您可以將報表設定為以*原生模式*或*連接模式*執行，以運用 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ca34b-103">reports can be configure to run in either *local mode* or *connected mode*, which leverages a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="ca34b-104">而是，當資料延伸模組支援本機模式報表時，您可以使用報表檢視器直接從 SharePoint 轉譯報表。</span><span class="sxs-lookup"><span data-stu-id="ca34b-104">Instead, you can use the Report Viewer to directly render reports from SharePoint when the data extension supports local mode reporting.</span></span> <span data-ttu-id="ca34b-105">這種方法稱為 *「本機模式」*(Local Mode)。</span><span class="sxs-lookup"><span data-stu-id="ca34b-105">This approach is called *local mode*.</span></span> <span data-ttu-id="ca34b-106">在舊版 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]中，SharePoint 伺服器陣列需要連接到 SharePoint 模式中所設定的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表伺服器，以便讓報表檢視器控制項能夠呈現報表。</span><span class="sxs-lookup"><span data-stu-id="ca34b-106">In previous versions of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)], the SharePoint farm was required to be connected to a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server configured in SharePoint mode so the Report Viewer control could render reports.</span></span> <span data-ttu-id="ca34b-107">此方法稱為 *「遠端模式」* (Remote Mode) 或 *「連接模式」*(Connected Mode)。</span><span class="sxs-lookup"><span data-stu-id="ca34b-107">This approach is called *remote mode* or *connected mode*.</span></span>  
  
 <span data-ttu-id="ca34b-108">在 *本機模式* 中，沒有 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ca34b-108">In *local mode* there is no [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="ca34b-109">您必須安裝 SharePoint 產品的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 增益集，但不需要 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ca34b-109">You must install the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint products, but no [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server is required.</span></span> <span data-ttu-id="ca34b-110">在本機模式中，使用者可以檢視報表，但是無法存取伺服器端的功能 (例如訂閱和資料警示)。</span><span class="sxs-lookup"><span data-stu-id="ca34b-110">With Local mode, users can view reports but will not have access to server side features such as subscriptions and data alerts.</span></span>  
  
||  
|-|  
|<span data-ttu-id="ca34b-111">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="ca34b-111">**[!INCLUDE[applies](../includes/applies-md.md)]**  [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode</span></span>|  
  
 <span data-ttu-id="ca34b-112">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="ca34b-112">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="ca34b-113">本機模式與連接模式及支援的延伸模組</span><span class="sxs-lookup"><span data-stu-id="ca34b-113">Local mode vs connected mode and supported extensions</span></span>](#bkmk_local_vs_connected)  
  
-   [<span data-ttu-id="ca34b-114">使用 SharePoint 2013 設定原生模式和存取服務</span><span class="sxs-lookup"><span data-stu-id="ca34b-114">Configure Local Mode and Access Services with SharePoint 2013</span></span>](#bkmk_local_mode_sharepoint2013)  
  
-   [<span data-ttu-id="ca34b-115">使用 SharePoint 2010 設定原生模式報告</span><span class="sxs-lookup"><span data-stu-id="ca34b-115">Configure Local Mode Reporting with SharePoint 2010</span></span>](#bkmk_local_mode_sharepoint2010)  
  
##  <a name="local-mode-vs-connected-mode-and-supported-extensions"></a><a name="bkmk_local_vs_connected"></a><span data-ttu-id="ca34b-116">原生模式與連接模式及支援的延伸模組</span><span class="sxs-lookup"><span data-stu-id="ca34b-116">Local mode vs connected mode and supported extensions</span></span>  
 <span data-ttu-id="ca34b-117">**本機模式：** 當您具有支援本機模式的資料延伸模組時，報表檢視器會直接從 SharePoint 呈現報表。</span><span class="sxs-lookup"><span data-stu-id="ca34b-117">**Local mode:** When you have a data extension that supports local mode, the Report Viewer directly renders reports from SharePoint.</span></span> <span data-ttu-id="ca34b-118">在 *本機模式* 中，沒有 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ca34b-118">In *local mode* there is no [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server.</span></span> <span data-ttu-id="ca34b-119">您必須安裝 SharePoint 產品的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 增益集，但不需要 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="ca34b-119">You must install the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] add-in for SharePoint products, but no [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server is required.</span></span> <span data-ttu-id="ca34b-120">在原生模式中，使用者可以查看報表，但**不**會存取伺服器端功能，例如訂閱和資料警示。</span><span class="sxs-lookup"><span data-stu-id="ca34b-120">With Local mode, users can view reports but will **not** have access to server side features such as subscriptions and data alerts.</span></span>  
  
 <span data-ttu-id="ca34b-121">**連接模式**也稱為 *「遠端模式」* ，會要求 SharePoint 模式下的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 報表伺服器，連接到 SharePoint 伺服器陣列，讓報表檢視器控制項可以呈現報表。</span><span class="sxs-lookup"><span data-stu-id="ca34b-121">**Connected mode**, also called *remote mode* requires a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] report server in SharePoint mode, connected to the SharePoint farm so the Report Viewer control could render reports..</span></span>  
  
 <span data-ttu-id="ca34b-122">下面是支援本機模式報表的資料處理延伸模組清單：</span><span class="sxs-lookup"><span data-stu-id="ca34b-122">The following is a list of the data processing extensions that support local mode reporting:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="ca34b-123">Access 2010 報表延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ca34b-123">Access 2010 reporting extension.</span></span> <span data-ttu-id="ca34b-124">如需 Access Services 的詳細資訊，請參閱 [將 Access Services 與 SQL Reporting Services 配合使用：安裝 SQL Server 2008 R2 Reporting Services 增益集 (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=192686)。</span><span class="sxs-lookup"><span data-stu-id="ca34b-124">For more information on Access Services, see [Use Access Services with SQL Reporting Services: Installing SQL Server 2008 R2 Reporting Services Add-In (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=192686).</span></span>  
  
-   <span data-ttu-id="ca34b-125">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 清單資料延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ca34b-125">The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint list data extension.</span></span> <span data-ttu-id="ca34b-126">如需 SharePoint 清單資料延伸模組的詳細資訊，請參閱 [Reporting Services &#40;SSRS&#41; 支援的資料來源](create-deploy-and-manage-mobile-and-paginated-reports.md)</span><span class="sxs-lookup"><span data-stu-id="ca34b-126">For more information on the SharePoint List Data Extension, see [Data Sources Supported by Reporting Services &#40;SSRS&#41;](create-deploy-and-manage-mobile-and-paginated-reports.md)</span></span>  
  
 <span data-ttu-id="ca34b-127">您也可以部署自訂資料處理延伸模組來支援本機模式。</span><span class="sxs-lookup"><span data-stu-id="ca34b-127">Custom data processing extensions can also be developed to support local mode.</span></span> <span data-ttu-id="ca34b-128">如需詳細資訊，請參閱＜ [Implementing a Data Processing Extension](extensions/data-processing/implementing-a-data-processing-extension.md)＞。</span><span class="sxs-lookup"><span data-stu-id="ca34b-128">For more information, see [Implementing a Data Processing Extension](extensions/data-processing/implementing-a-data-processing-extension.md).</span></span>  
  
 <span data-ttu-id="ca34b-129">本機模式支援轉譯具有 .rsds 檔案中之內嵌資料來源或共用資料來源的報表。</span><span class="sxs-lookup"><span data-stu-id="ca34b-129">Local mode supports rendering reports that have an embedded data source or a shared data source from an .rsds file.</span></span> <span data-ttu-id="ca34b-130">不過，您無法管理報表或其相關聯的資料來源。</span><span class="sxs-lookup"><span data-stu-id="ca34b-130">However, you cannot manage the report or its associated data source.</span></span> <span data-ttu-id="ca34b-131">如果您嘗試這樣做，將會收到在本機模式不支援這項動作的錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca34b-131">If you try to do this, you will receive an error that this is not supported in local mode.</span></span> <span data-ttu-id="ca34b-132">在 SharePoint 網站中管理資料來源，只有在連接模式下才支援。</span><span class="sxs-lookup"><span data-stu-id="ca34b-132">Managing data sources in the SharePoint site is supported in only connected mode.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ca34b-133">就如同舊版一樣，您無法在 .rsds 檔案中內嵌使用者名稱及密碼。</span><span class="sxs-lookup"><span data-stu-id="ca34b-133">As with previous versions, you cannot embed user names and passwords in the .rsds file.</span></span>  
  
##  <a name="configure-local-mode-and-access-services-with-sharepoint-2013"></a><a name="bkmk_local_mode_sharepoint2013"></a><span data-ttu-id="ca34b-134">使用 SharePoint 2013 設定原生模式和存取服務</span><span class="sxs-lookup"><span data-stu-id="ca34b-134">Configure Local Mode and Access Services with SharePoint 2013</span></span>  
 <span data-ttu-id="ca34b-135">您可以設定 SharePoint 2013 伺服器陣列支援現有 Access 2010 Web 資料庫和 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 本機模式。</span><span class="sxs-lookup"><span data-stu-id="ca34b-135">You can configure your SharePoint 2013 farm to support existing Access 2010 web databases and [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] local mode.</span></span> <span data-ttu-id="ca34b-136">如需詳細資訊，請參閱 [安裝及設定 SharePoint Server 2013 中 Web 資料庫的 Access Services 2010](https://technet.microsoft.com/library/ee748653\(office.15\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="ca34b-136">For more information, see [Set up and configure Access Services 2010 for web databases in SharePoint Server 2013](https://technet.microsoft.com/library/ee748653\(office.15\).aspx).</span></span>  
  
 <span data-ttu-id="ca34b-137">您無法為 SharePoint 2013 建立新的 Access Web 資料庫。</span><span class="sxs-lookup"><span data-stu-id="ca34b-137">It is not possible to create new Access web databases for SharePoint 2013.</span></span> <span data-ttu-id="ca34b-138">Access 2013 會使用您在 Access 中建立的新資料庫類型 *Access Web App* ，然後在 Web 瀏覽器中做為 SharePoint 應用程式使用並與其他人共用。</span><span class="sxs-lookup"><span data-stu-id="ca34b-138">Access 2013 uses a new type of database, *Access web app* that you build in Access, then use and share with others as a SharePoint app in a web browser.</span></span>  
  
 <span data-ttu-id="ca34b-139">如需詳細資訊，請參閱下列內容。</span><span class="sxs-lookup"><span data-stu-id="ca34b-139">For more information, see the following.</span></span>  
  
-   <span data-ttu-id="ca34b-140">[Access 2013 (的新功能](https://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx) https://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="ca34b-140">[What's new in Access 2013](https://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx) (https://office.microsoft.com/access-help/what-s-new-in-access-2013-HA102809500.aspx).</span></span>  
  
-   <span data-ttu-id="ca34b-141">[存取應用程式](https://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500) (的基本工作 https://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500) 。</span><span class="sxs-lookup"><span data-stu-id="ca34b-141">[Basic tasks for an Access app](https://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500) (https://office.microsoft.com/access-help/basic-tasks-for-an-access-app-HA102840210.aspx?CTT=5&origin=HA102809500).</span></span>  
  
##  <a name="configure-local-mode-reporting-with-sharepoint-2010"></a><a name="bkmk_local_mode_sharepoint2010"></a><span data-ttu-id="ca34b-142">使用 SharePoint 2010 設定原生模式報告</span><span class="sxs-lookup"><span data-stu-id="ca34b-142">Configure Local Mode Reporting with SharePoint 2010</span></span>  
 <span data-ttu-id="ca34b-143">本機模式需要 ASP.NET 工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="ca34b-143">Local mode requires ASP.NET session state.</span></span> <span data-ttu-id="ca34b-144">安裝 Access Services 就會啟用 ASP.Net 工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="ca34b-144">The installation of Access services will enable ASP.Net sessions state.</span></span> <span data-ttu-id="ca34b-145">您也可以使用 PowerShell 來啟用。</span><span class="sxs-lookup"><span data-stu-id="ca34b-145">You can also enable using PowerShell.</span></span>  
  
1.  <span data-ttu-id="ca34b-146">開啟 SharePoint 2010 管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="ca34b-146">Open the SharePoint 2010 Management Shell.</span></span>  
  
2.  <span data-ttu-id="ca34b-147">輸入下列命令：</span><span class="sxs-lookup"><span data-stu-id="ca34b-147">Type the following command:</span></span>  
  
    ```  
    - Enable-SPSessionStateService  
    ```  
  
3.  <span data-ttu-id="ca34b-148">出現提示時，請輸入資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="ca34b-148">When prompted, type the name of your database.</span></span>  
  
4.  <span data-ttu-id="ca34b-149">執行 IIS 重設。</span><span class="sxs-lookup"><span data-stu-id="ca34b-149">Perform an IIS reset.</span></span>  
  
 <span data-ttu-id="ca34b-150">如需詳細資訊，請參閱 [將 Access Services 與 SQL Reporting Services 配合使用：安裝 SQL Server 2008 R2 Reporting Services 增益集 (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=192686) 和 [Enable-SPSessionStateService](https://technet.microsoft.com/library/ff607857\(v=office.15\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="ca34b-150">For more information, see [Use Access Services with SQL Reporting Services: Installing SQL Server 2008 R2 Reporting Services Add-In (SharePoint Server 2010)](https://go.microsoft.com/fwlink/?LinkId=192686) and [Enable-SPSessionStateService](https://technet.microsoft.com/library/ff607857\(v=office.15\).aspx).</span></span>  
  
## <a name="connected-mode"></a><span data-ttu-id="ca34b-151">連線模式</span><span class="sxs-lookup"><span data-stu-id="ca34b-151">Connected mode</span></span>  
 <span data-ttu-id="ca34b-152">如需搭配連線模式使用 ADS 擴充功能的最新資訊 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] ，請參閱[SharePoint 網站中的 Access Services 報表顯示資料延伸模組 ' ADS '](https://social.technet.microsoft.com/wiki/contents/articles/25298.access-services-report-in-sharepoint-site-shows-error-in-data-extension-ads.aspx)中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="ca34b-152">For the latest information on using ADS extension with [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] connected mode, see [Access Services Report in SharePoint Site shows error in data extension 'ADS'](https://social.technet.microsoft.com/wiki/contents/articles/25298.access-services-report-in-sharepoint-site-shows-error-in-data-extension-ads.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca34b-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca34b-153">See Also</span></span>  
 [<span data-ttu-id="ca34b-154">Reporting Services 支援的資料來源 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="ca34b-154">Data Sources Supported by Reporting Services &#40;SSRS&#41;</span></span>](create-deploy-and-manage-mobile-and-paginated-reports.md)  
  
