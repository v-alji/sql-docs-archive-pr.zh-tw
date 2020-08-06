---
title: 驗證 Reporting Services 安裝 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- checking report server installations
- verifying report server installations
- Report Designer [Reporting Services], verifying installations
- installing Reporting Services, verifying installations
- Report Manager [Reporting Services], verifying installations
- report servers [Reporting Services], verifying installations
- Setup [Reporting Services], verifying installations
ms.assetid: 82a51a99-66f0-4b0c-b05b-07d22387adb0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 5b90f997f99cfc9d3f8625eb4e08d193af52d7f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585130"
---
# <a name="verify-a-reporting-services-installation"></a><span data-ttu-id="e1c3c-102">Verify a Reporting Services Installation</span><span class="sxs-lookup"><span data-stu-id="e1c3c-102">Verify a Reporting Services Installation</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="e1c3c-103">報表伺服器：原生或 SharePoint。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-103">report servers can be installed in one of two modes, Native or SharePoint.</span></span> <span data-ttu-id="e1c3c-104">確認安裝所應遵循的步驟會視報表伺服器模式而定。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-104">The steps you should follow for verifying the installation depend on the report server mode.</span></span>  
  
 <span data-ttu-id="e1c3c-105">本主題包含下列資訊：</span><span class="sxs-lookup"><span data-stu-id="e1c3c-105">This topic contains the following information:</span></span>  
  
-   [<span data-ttu-id="e1c3c-106">確認 SharePoint 模式安裝</span><span class="sxs-lookup"><span data-stu-id="e1c3c-106">Verify SharePoint Mode Installation</span></span>](#bkmk_sharepointmode)  
  
-   [<span data-ttu-id="e1c3c-107">確認原生模式安裝</span><span class="sxs-lookup"><span data-stu-id="e1c3c-107">Verify a Native Mode Installation</span></span>](#bkmk_nativemode)  
  
##  <a name="verify-sharepoint-mode-installation"></a><a name="bkmk_sharepointmode"></a> <span data-ttu-id="e1c3c-108">確認 SharePoint 模式安裝</span><span class="sxs-lookup"><span data-stu-id="e1c3c-108">Verify SharePoint Mode Installation</span></span>  
  
#### <a name="to-verify-the-reporting-services-service"></a><span data-ttu-id="e1c3c-109">確認 Reporting Services 服務</span><span class="sxs-lookup"><span data-stu-id="e1c3c-109">To verify the Reporting Services Service</span></span>  
  
1.  <span data-ttu-id="e1c3c-110">從 SharePoint 管理中心，按一下 **[系統設定]** 群組中的 **[管理伺服器上的服務]** 。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-110">From SharePoint central administration, click **Manage services on server** in the **System Settings** group.</span></span>  
  
2.  <span data-ttu-id="e1c3c-111">確認已安裝 **[SQL Server Reporting Services 服務]** ，且該服務處於 **[執行中]** 狀態。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-111">Verify the **SQL Server Reporting Services Service** is installed and in the **Running** state.</span></span>  
  
     <span data-ttu-id="e1c3c-112">如果您在清單中未看到 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務，請確認是否已安裝此服務。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-112">If you do not see the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service in the list, verify the service is installed.</span></span> <span data-ttu-id="e1c3c-113">如需詳細資訊，請參閱[安裝適用于 sharepoint 2010 的 Reporting Services Sharepoint 模式](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md)中的「安裝並啟動 Reporting Services SharePoint 服務」一節。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-113">For more information, see the "Install and start the Reporting Services SharePoint Service" section of [Install Reporting Services SharePoint Mode for SharePoint 2010](../../sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2010.md).</span></span>  
  
#### <a name="to-verify-the-service-application"></a><span data-ttu-id="e1c3c-114">確認服務應用程式</span><span class="sxs-lookup"><span data-stu-id="e1c3c-114">To verify the Service Application</span></span>  
  
1.  <span data-ttu-id="e1c3c-115">若要從管理中心確認您至少具有一個 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式，請按一下 **[應用程式管理]** 群組中的 **[管理服務應用程式]** 。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-115">To verify from Central Administration you have at least one [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application, click **Manage Service Applications** in the **Application Management** group.</span></span>  
  
2.  <span data-ttu-id="e1c3c-116">確認 **[SQL Server Reporting Services 服務應用程式]** 類型的服務應用程式確實存在，而且有對應的應用程式 Proxy。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-116">Verify there is a service application of type **SQL Server Reporting Services Service Application** and a corresponding application proxy.</span></span>  
  
3.  <span data-ttu-id="e1c3c-117">在服務應用程式名稱 **附近** 按一下，然後在 SharePoint 工具列中按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-117">Click **near** the name of the service application and then click **Properties** in the SharePoint toolbar.</span></span>  <span data-ttu-id="e1c3c-118">如果您按一下服務應用程式的名稱，即會開啟服務應用程式的 [管理] 頁面，而不是屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-118">If you click the name of the service application it will open the Management pages of the service application, not the properties page.</span></span>  
  
4.  <span data-ttu-id="e1c3c-119">確認 **[Web 應用程式關聯]** 設定為指向所需的 Web 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-119">Verify the **Web Application Association** is configured to point to the desired web application.</span></span>  
  
#### <a name="to-verify-the-site-collection-feature"></a><span data-ttu-id="e1c3c-120">確認網站集合功能</span><span class="sxs-lookup"><span data-stu-id="e1c3c-120">To verify the Site collection Feature</span></span>  
  
1.  <span data-ttu-id="e1c3c-121">在網站設定中，按一下 **[網站集合管理]** 群組中的 **[網站集合功能]** 。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-121">In site settings, click **Site collection Features** in the **Site Collection Administration** group.</span></span>  
  
2.  <span data-ttu-id="e1c3c-122">確認已啟用 **[報表伺服器整合功能]** 。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-122">Verify the **Report Server Integration Feature** is active.</span></span>  
  
#### <a name="to-verify-reporting-server-content-types"></a><span data-ttu-id="e1c3c-123">確認報表伺服器內容類型</span><span class="sxs-lookup"><span data-stu-id="e1c3c-123">To Verify Reporting Server content types</span></span>  
  
1.  <span data-ttu-id="e1c3c-124">若要確認或加入 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表伺服器內容類型，請參閱[將報表伺服器內容類型加入至程式庫 &#40;Reporting Services SharePoint 整合模式中的&#41;](../add-reporting-services-content-types-to-a-sharepoint-library.md)。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-124">To verify or add [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server content types, see [Add Report Server Content Types to a Library &#40;Reporting Services in SharePoint Integrated Mode&#41;](../add-reporting-services-content-types-to-a-sharepoint-library.md).</span></span>  
  
#### <a name="to-verify-you-can-launch-report-builder"></a><span data-ttu-id="e1c3c-125">確認您可以啟動報表產生器</span><span class="sxs-lookup"><span data-stu-id="e1c3c-125">To verify you can launch Report Builder</span></span>  
  
1.  <span data-ttu-id="e1c3c-126">從文件庫中，按一下 SharePoint 功能區中的 **[文件]** 。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-126">From a document library, click **Documents** in the SharePoint ribbon.</span></span>  
  
2.  <span data-ttu-id="e1c3c-127">按一下 **[新增文件]** ，然後再按一下 **[報表產生器報表]**。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-127">Click **New Document** and click **Report Builder Report**.</span></span> <span data-ttu-id="e1c3c-128">如果您看不到這個選項，請檢閱有關將報表伺服器內容類型加入文件庫的先前程序。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-128">If you do not see this option, review the previous procedure on adding the report server content types to a library.</span></span>  
  
#### <a name="create-a-basic-report"></a><span data-ttu-id="e1c3c-129">建立基本報告</span><span class="sxs-lookup"><span data-stu-id="e1c3c-129">Create a basic report</span></span>  
  
1.  <span data-ttu-id="e1c3c-130">在 SharePoint 文件庫中，建立只包含一個文字方塊 (例如標題) 的基本 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-130">In a SharePoint document library, create a basic [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report that only contains a text box, for example a title.</span></span> <span data-ttu-id="e1c3c-131">此報表不包含任何資料來源或資料集。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-131">The report does not contain any data sources or datasets.</span></span> <span data-ttu-id="e1c3c-132">其目的是要確認您可以開啟報表產生器，而且基本報表將會進行預覽。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-132">The goal is to verify you can open Report Builder and a basic report will preview.</span></span>  
  
2.  <span data-ttu-id="e1c3c-133">將報表儲存至文件庫，然後從文件庫中執行報表。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-133">Save the report to the document library and the run the report from the library.</span></span> <span data-ttu-id="e1c3c-134">如需使用報表產生器建立報表的詳細資訊，請參閱 [啟動報表產生器 (報表產生器)](https://technet.microsoft.com/library/ms159221.aspx)。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-134">For more information on creating reports with Report Builder, see [Start Report Builder (Report Builder)](https://technet.microsoft.com/library/ms159221.aspx).</span></span>  
  
#### <a name="reporting-services-samples"></a><span data-ttu-id="e1c3c-135">Reporting Services 範例</span><span class="sxs-lookup"><span data-stu-id="e1c3c-135">Reporting Services samples</span></span>  
  
1.  <span data-ttu-id="e1c3c-136">完成其中一個 Reporting Services 教學課程。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-136">Complete one of the Reporting Services tutorials.</span></span> <span data-ttu-id="e1c3c-137">如需詳細資訊，請參閱 [Reporting Services 教學課程 &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-137">For more information, see [Reporting Services Tutorials &#40;SSRS&#41;](../reporting-services-tutorials-ssrs.md).</span></span>  
  
2.  <span data-ttu-id="e1c3c-138">從 CodePlex 下載 Adventure Works 範例資料庫和 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 範例報表。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-138">Download the Adventure works sample database and the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] sample reports from CodePlex.</span></span> <span data-ttu-id="e1c3c-139">如需詳細資訊，請參閱＜ [AdventureWorks 報表範例](https://msftrsprodsamples.codeplex.com/wikipage?title=SS2012!AdventureWorks2012%20Report%20Samples&referringTitle=Home)＞。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-139">For more information, see [AdventureWorks Report Samples](https://msftrsprodsamples.codeplex.com/wikipage?title=SS2012!AdventureWorks2012%20Report%20Samples&referringTitle=Home).</span></span>  
  
##  <a name="verify-a-native-mode-installation"></a><a name="bkmk_nativemode"></a> <span data-ttu-id="e1c3c-140">驗證原生模式安裝</span><span class="sxs-lookup"><span data-stu-id="e1c3c-140">Verify a Native Mode Installation</span></span>  
 <span data-ttu-id="e1c3c-141">當您使用預設組態安裝原生模式報表伺服器時，安裝程式會安裝和部署該伺服器。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-141">When you install a Native mode report server using the default configuration, Setup installs and deploys the server.</span></span> <span data-ttu-id="e1c3c-142">您可以執行一些簡單的測試，來確認安裝程式是否部署報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-142">You can verify whether Setup deployed the report server by performing a few simple tests.</span></span> <span data-ttu-id="e1c3c-143">您必須是本機管理員才能執行這些步驟。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-143">You must be a local administrator to perform these steps.</span></span> <span data-ttu-id="e1c3c-144">若要讓其他使用者能夠執行測試，您必須為那些使用者設定報表伺服器存取權。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-144">To enable other users to perform testing, you must configure report server access for those users.</span></span>  
  
#### <a name="to-verify-that-the-report-server-is-installed-and-running"></a><span data-ttu-id="e1c3c-145">確認報表伺服器已安裝及執行</span><span class="sxs-lookup"><span data-stu-id="e1c3c-145">To verify that the report server is installed and running</span></span>  
  
1.  <span data-ttu-id="e1c3c-146">執行 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 組態工具，並連接到您剛安裝的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-146">Run the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Configuration tool and connect to the report server instance you just installed.</span></span> <span data-ttu-id="e1c3c-147">[Web 服務 URL] 頁面包含報表伺服器 Web 服務的連結。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-147">The Web Service URL page includes a link to the Report Server Web service.</span></span> <span data-ttu-id="e1c3c-148">請按一下此連結，確認您可以存取伺服器。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-148">Click the link to verify you can access the server.</span></span> <span data-ttu-id="e1c3c-149">如果報表伺服器資料庫並未設定，請在按一下連結之前先行設定。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-149">If the report server database is not configured, do that first before clicking the link.</span></span>  
  
2.  <span data-ttu-id="e1c3c-150">開啟 [服務] 主控台應用程式，並確認報表伺服器服務正在執行中。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-150">Open the Services console applications and verify that the Report Server service is running.</span></span> <span data-ttu-id="e1c3c-151">若要檢視報表伺服器服務的狀態，請按一下 [開始]\*\*\*\*，指向 [控制台]\*\*\*\*，並按兩下 [系統管理工具]\*\*\*\*，然後按兩下 [服務]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-151">To view the status of the Report Server service, click **Start**, point to **Control Panel**, double-click **Administrative Tools**, and then double-click **Services**.</span></span> <span data-ttu-id="e1c3c-152">當服務清單出現時，請捲動至 [報表伺服器 (MSSQLSERVER)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-152">When the list of services appears, scroll to **Report Server (MSSQLSERVER)**.</span></span> <span data-ttu-id="e1c3c-153">其狀態應該是 **[已啟動]**。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-153">The status should be **Started**.</span></span>  
  
3.  <span data-ttu-id="e1c3c-154">開啟瀏覽器，並在位址列輸入報表伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-154">Open a browser and type the report server URL in the address bar.</span></span> <span data-ttu-id="e1c3c-155">位址是由您在安裝期間對報表伺服器指定的伺服器名稱和虛擬目錄名稱所組成。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-155">The address consists of the server name and the virtual directory name that you specified for the report server during setup.</span></span> <span data-ttu-id="e1c3c-156">報表伺服器虛擬目錄的預設名稱為 **ReportServer**。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-156">By default, the report server virtual directory is named **ReportServer**.</span></span> <span data-ttu-id="e1c3c-157">您可以使用下列 URL 來確認報表伺服器的安裝： HTTP:// *\<computer name>* /ReportServer *\<_instance name>* 。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-157">You can use the following URL to verify report server installation: http://*\<computer name>*/ReportServer*\<_instance name>*.</span></span> <span data-ttu-id="e1c3c-158">如果您將報表伺服器安裝成具名執行個體，則需使用不同的 URL。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-158">The URL will be different if you installed the report server as a named instance.</span></span> <span data-ttu-id="e1c3c-159">如需 URL 格式的詳細資訊，請參閱[設定報表伺服器 URL &#40;SSRS 設定管理員&#41;](configure-report-server-urls-ssrs-configuration-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-159">For more information about the URL format, see [Configure Report Server URLs  &#40;SSRS Configuration Manager&#41;](configure-report-server-urls-ssrs-configuration-manager.md).</span></span> <span data-ttu-id="e1c3c-160">如果您是 Windows Vista 或 Windows Server 2008 的本機系統管理員，請參閱[設定原生模式報表伺服器進行本機管理 &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-160">If you are a local administrator on Windows Vista or Windows Server 2008, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
4.  <span data-ttu-id="e1c3c-161">執行報表來測試報表伺服器作業。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-161">Run reports to test report server operations.</span></span> <span data-ttu-id="e1c3c-162">在此步驟中，您可以根據教學課程建立範例報表。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-162">For this step, you can create a sample report from a tutorial.</span></span> <span data-ttu-id="e1c3c-163">如需詳細資訊，請參閱[建立基本資料表報表 &#40;SSRS 教學課程&#41;](../create-a-basic-table-report-ssrs-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-163">For more information, see [Create a Basic Table Report &#40;SSRS Tutorial&#41;](../create-a-basic-table-report-ssrs-tutorial.md).</span></span>  
  
#### <a name="to-verify-that-report-manager-is-installed-and-running"></a><span data-ttu-id="e1c3c-164">確認報表管理員已安裝及執行</span><span class="sxs-lookup"><span data-stu-id="e1c3c-164">To verify that Report Manager is installed and running</span></span>  
  
1.  <span data-ttu-id="e1c3c-165">開啟瀏覽器，並在位址列輸入報表管理員 URL。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-165">Open a browser and type the Report Manager URL in the address bar.</span></span> <span data-ttu-id="e1c3c-166">此位址是由伺服器名稱和虛擬目錄名稱所組成，此目錄名稱是安裝期間針對報表管理員所指定，或是在 Reporting Services 組態工具的 [報表管理員 URL] 頁面中指定。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-166">The address consists of the server name and the virtual directory name that you specified for the Report Manager during setup or in the Report Manager URL page in the Reporting Services Configuration tool.</span></span> <span data-ttu-id="e1c3c-167">依預設，報表管理員虛擬目錄的名稱為 **Reports**。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-167">By default, the Report Manager virtual directory is **Reports**.</span></span> <span data-ttu-id="e1c3c-168">您可以使用下列 URL 確認報表管理員的安裝：</span><span class="sxs-lookup"><span data-stu-id="e1c3c-168">You can use the following URL to verify Report Manager installation:</span></span>  
  
     <span data-ttu-id="e1c3c-169">HTTP:// *\<computer name>* /Reports *\<_instance name>* 。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-169">http://*\<computer name>*/Reports*\<_instance name>*.</span></span>  
  
2.  <span data-ttu-id="e1c3c-170">使用報表管理員來建立新資料夾，或上傳檔案來測試定義是否傳回至報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-170">Use Report Manager to create a new folder or upload a file to test whether definitions are passed back to the report server database.</span></span> <span data-ttu-id="e1c3c-171">如果這些作業都成功，表示連接可運作。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-171">If these operations are successful, the connection is functional.</span></span>  
  
     <span data-ttu-id="e1c3c-172">如需詳細資訊，請參閱[報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-172">For more information, see [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
#### <a name="to-verify-that-report-designer-is-installed-and-running"></a><span data-ttu-id="e1c3c-173">確認報表設計師已安裝及執行</span><span class="sxs-lookup"><span data-stu-id="e1c3c-173">To verify that Report Designer is installed and running</span></span>  
  
1.  <span data-ttu-id="e1c3c-174">開啟 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]，並根據報表伺服器專案類型來建立新的專案。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-174">Open [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], and create a new project based on a Report Server project type.</span></span> <span data-ttu-id="e1c3c-175">如需使用 [報表伺服器專案精靈] 的詳細資訊，請參閱《SQL Server 線上叢書》中的 [SQL Server 資料工具中的 Reporting Services &#40;SSDT&#41;](../tools/reporting-services-in-sql-server-data-tools-ssdt.md)。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-175">For more information on using the Report Server Project Wizard, see [Reporting Services in SQL Server Data Tools &#40;SSDT&#41;](../tools/reporting-services-in-sql-server-data-tools-ssdt.md) in SQL Server Books Online.</span></span>  
  
2.  <span data-ttu-id="e1c3c-176">如果您已安裝報表範例，請開啟範例報表專案檔，並將報表發行至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="e1c3c-176">If you installed report samples, open the sample report project files and publish the reports to a report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1c3c-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1c3c-177">See Also</span></span>  
 <span data-ttu-id="e1c3c-178">[針對 Reporting Services 安裝進行疑難排解](troubleshoot-a-reporting-services-installation.md) </span><span class="sxs-lookup"><span data-stu-id="e1c3c-178">[Troubleshoot a Reporting Services Installation](troubleshoot-a-reporting-services-installation.md) </span></span>  
 [<span data-ttu-id="e1c3c-179">Reporting Services 錯誤的原因和解決方案</span><span class="sxs-lookup"><span data-stu-id="e1c3c-179">Cause and Resolution of Reporting Services Errors</span></span>](../troubleshooting/cause-and-resolution-of-reporting-services-errors.md)  
  
  
