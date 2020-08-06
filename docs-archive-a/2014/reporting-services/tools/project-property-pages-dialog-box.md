---
title: 專案屬性頁對話方塊 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rpt.rptdesigner.projectpropertypages.general.f1
helpviewer_keywords:
- Project Property Pages dialog box
ms.assetid: 209d9e22-37fc-418f-8739-83adcf447d3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6ae5ab7c68c9a95759d27ca2785f99377c98942a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700678"
---
# <a name="project-property-pages-dialog-box"></a><span data-ttu-id="8e350-102">專案屬性頁對話方塊</span><span class="sxs-lookup"><span data-stu-id="8e350-102">Project Property Pages Dialog Box</span></span>
  <span data-ttu-id="8e350-103">使用專案屬性頁，即可設定報表伺服器專案的部署屬性。</span><span class="sxs-lookup"><span data-stu-id="8e350-103">Use the project property pages to configure deployment properties for a Report Server project.</span></span> <span data-ttu-id="8e350-104">若要開啟此對話方塊，請在 [**專案**] 功能表中，按一下 [ _\<Report Project Name>_ **屬性**]。</span><span class="sxs-lookup"><span data-stu-id="8e350-104">To open this dialog box, from the **Project** menu, click _\<Report Project Name>_**Properties**.</span></span>  
  
 <span data-ttu-id="8e350-105">在您定義組態屬性之後，可以從工具列的 [方案組態] 下拉式清單中選取組態。</span><span class="sxs-lookup"><span data-stu-id="8e350-105">After you define configuration properties, you can select a configuration from the **Solution Configurations** drop-down list on the toolbar.</span></span>  
  
## <a name="options"></a><span data-ttu-id="8e350-106">選項</span><span class="sxs-lookup"><span data-stu-id="8e350-106">Options</span></span>  
 <span data-ttu-id="8e350-107">**組態**</span><span class="sxs-lookup"><span data-stu-id="8e350-107">**Configuration**</span></span>  
 <span data-ttu-id="8e350-108">選取要編輯的組態。</span><span class="sxs-lookup"><span data-stu-id="8e350-108">Select the configuration to edit.</span></span> <span data-ttu-id="8e350-109">一開始會有下列的組態可用： **Debug**、 **DebugLocal**和 **Release**。</span><span class="sxs-lookup"><span data-stu-id="8e350-109">Initially, the following configurations are available: **Debug**, **DebugLocal**, and **Release**.</span></span> <span data-ttu-id="8e350-110">使用中組態會先出現，例如 **Active(Debug)**。</span><span class="sxs-lookup"><span data-stu-id="8e350-110">The active configuration appears first, for example, **Active(Debug)**.</span></span>  
  
 <span data-ttu-id="8e350-111">若要同時查看多個組態的屬性，請選取 **[所有組態]** 或 **[多重組態]**。</span><span class="sxs-lookup"><span data-stu-id="8e350-111">To see properties for more than one configuration at the same time, select **All Configurations** or **Multiple Configurations**.</span></span>  
  
 <span data-ttu-id="8e350-112">若要建立其他組態，請按一下工具列上的 **[組態管理員]** 。</span><span class="sxs-lookup"><span data-stu-id="8e350-112">To create additional configurations, click **Configuration Manager** on the toolbar.</span></span>  
  
 <span data-ttu-id="8e350-113">**Configuration Manager**</span><span class="sxs-lookup"><span data-stu-id="8e350-113">**Configuration Manager**</span></span>  
 <span data-ttu-id="8e350-114">針對整個方案管理組態或是加入其他組態。</span><span class="sxs-lookup"><span data-stu-id="8e350-114">Manage configurations for the entire solution or to add additional configurations.</span></span> <span data-ttu-id="8e350-115">如需詳細資訊，請參閱 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 檔集。</span><span class="sxs-lookup"><span data-stu-id="8e350-115">For more information, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] documentation.</span></span>  
  
 <span data-ttu-id="8e350-116">**OutputPath**</span><span class="sxs-lookup"><span data-stu-id="8e350-116">**OutputPath**</span></span>  
 <span data-ttu-id="8e350-117">輸入或貼上路徑來儲存報表之建立驗證、部署與預覽時所使用的報表定義。</span><span class="sxs-lookup"><span data-stu-id="8e350-117">Type or paste the path to store the report definition used in build verification, deployment, and preview of reports.</span></span> <span data-ttu-id="8e350-118">此路徑必須不同於專案所使用的路徑以及位於專案路徑下之子資料夾的相對路徑。</span><span class="sxs-lookup"><span data-stu-id="8e350-118">The path must be different than the path that you use for the project and a relative path that is a child folder under the path of the project.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="8e350-119">您可以使用多個組態，以便根據您執行的工作，在路徑之間切換。</span><span class="sxs-lookup"><span data-stu-id="8e350-119">You can use multiple configurations to switch among paths depending on the task you perform.</span></span>  
  
 <span data-ttu-id="8e350-120">**ErrorLevel**</span><span class="sxs-lookup"><span data-stu-id="8e350-120">**ErrorLevel**</span></span>  
 <span data-ttu-id="8e350-121">輸入回報為錯誤之建立問題的嚴重性。</span><span class="sxs-lookup"><span data-stu-id="8e350-121">Type the severity of the build issues that are reported as errors.</span></span> <span data-ttu-id="8e350-122">嚴重性層級小於或等於 **ErrorLevel** 值的問題會回報為錯誤；否則，會將這些問題回報為警告。</span><span class="sxs-lookup"><span data-stu-id="8e350-122">Issues with severity levels less than or equal to the value of **ErrorLevel** are reported as errors; otherwise, the issues are reported as warnings.</span></span> <span data-ttu-id="8e350-123">任何錯誤都會導致建立工作失敗。</span><span class="sxs-lookup"><span data-stu-id="8e350-123">Any error will cause the build task to fail.</span></span> <span data-ttu-id="8e350-124">有效的嚴重性層級為 0 到 4 (包含)。</span><span class="sxs-lookup"><span data-stu-id="8e350-124">The valid severity levels are 0 through 4 inclusively.</span></span> <span data-ttu-id="8e350-125">預設值為 2。</span><span class="sxs-lookup"><span data-stu-id="8e350-125">The default value is 2.</span></span>  
  
 <span data-ttu-id="8e350-126">**StartItem**</span><span class="sxs-lookup"><span data-stu-id="8e350-126">**StartItem**</span></span>  
 <span data-ttu-id="8e350-127">選取當專案發行到報表伺服器之後，要顯示在網頁瀏覽器中的報表；或當專案在本機執行時，要顯示在預覽視窗中的報表。</span><span class="sxs-lookup"><span data-stu-id="8e350-127">Select the report that is displayed in the Web browser after the project is published to the report server or in the preview window when the project is run locally.</span></span> <span data-ttu-id="8e350-128">建置但不部署專案的設定及 [偵錯]\*\*\*\* 命令 (**F5**) 的使用都需要開始項目。</span><span class="sxs-lookup"><span data-stu-id="8e350-128">A start item is required for configurations that build but do not deploy the project and for using the **Debug** command (**F5**).</span></span> <span data-ttu-id="8e350-129">部署專案的組態需要它。</span><span class="sxs-lookup"><span data-stu-id="8e350-129">It is required for configurations that deploy the project.</span></span>  
  
 <span data-ttu-id="8e350-130">**OverwriteDataSources**</span><span class="sxs-lookup"><span data-stu-id="8e350-130">**OverwriteDataSources**</span></span>  
 <span data-ttu-id="8e350-131">選取 **True** ，即可在發行報表時，以專案中的資料來源覆寫伺服器上的資料來源。</span><span class="sxs-lookup"><span data-stu-id="8e350-131">Select **True** to overwrite the data source on the server with the data source in the project when the reports are published.</span></span> <span data-ttu-id="8e350-132">選取 **False** ，即可保留伺服器上現有的資料來源。</span><span class="sxs-lookup"><span data-stu-id="8e350-132">Select **False** to leave the existing data source on the server.</span></span>  
  
 <span data-ttu-id="8e350-133">**TargetServerVersion**</span><span class="sxs-lookup"><span data-stu-id="8e350-133">**TargetServerVersion**</span></span>  
 <span data-ttu-id="8e350-134">選取 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 或 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 版本的， [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 或選取 [偵測**版本**]，以自動判斷安裝在**TargetServer URL**屬性所識別之伺服器上的版本。</span><span class="sxs-lookup"><span data-stu-id="8e350-134">Select either the [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] or [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] or select **Detect Version** to automatically determine the version installed on the server identified by the **TargetServer URL** property.</span></span> <span data-ttu-id="8e350-135">伺服器預設值是 **SQL Server 2008 R2**。</span><span class="sxs-lookup"><span data-stu-id="8e350-135">The default value is **SQL Server 2008 R2**.</span></span>  
  
 <span data-ttu-id="8e350-136">**TargetDataSourceFolder**</span><span class="sxs-lookup"><span data-stu-id="8e350-136">**TargetDataSourceFolder**</span></span>  
 <span data-ttu-id="8e350-137">用來儲存已發行共用資料來源的資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="8e350-137">The name of the folder in which to store the published shared data sources.</span></span> <span data-ttu-id="8e350-138">如果您未指定資料夾，資料來源就會發行到與報表相同的資料夾。</span><span class="sxs-lookup"><span data-stu-id="8e350-138">If you do not specify a folder, the data source is published to the same folder as the report.</span></span> <span data-ttu-id="8e350-139">如果報表伺服器上沒有此資料夾，報表設計師會在發行報表時建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="8e350-139">If the folder does not exist on the report server, Report Designer creates the folder when the reports are published.</span></span>  
  
 <span data-ttu-id="8e350-140">發行至以原生模式執行的報表伺服器時，請從根目錄開始指定資料夾階層的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="8e350-140">When publishing to a report server running in native mode, specify the full path of the folder hierarchy starting at the root.</span></span> <span data-ttu-id="8e350-141">例如，Folder1/Folder2/Folder3。</span><span class="sxs-lookup"><span data-stu-id="8e350-141">For example, Folder1/Folder2/Folder3.</span></span>  
  
 <span data-ttu-id="8e350-142">發行至以 SharePoint 整合模式執行的報表伺服器時，請使用 SharePoint 文件庫的 URL。</span><span class="sxs-lookup"><span data-stu-id="8e350-142">When publishing to a report server running in SharePoint integrated mode, use a URL to the SharePoint library.</span></span> <span data-ttu-id="8e350-143">例如，HTTP:// *\<servername>/\<site>* //documents/myfolder。</span><span class="sxs-lookup"><span data-stu-id="8e350-143">For example, http://*\<servername>/\<site>*/Documents/MyFolder.</span></span>  
  
 <span data-ttu-id="8e350-144">**TargetReportFolder**</span><span class="sxs-lookup"><span data-stu-id="8e350-144">**TargetReportFolder**</span></span>  
 <span data-ttu-id="8e350-145">用來儲存已發行報表的資料夾名稱。</span><span class="sxs-lookup"><span data-stu-id="8e350-145">The name of the folder in which to store the published reports.</span></span> <span data-ttu-id="8e350-146">依預設，此為報表專案的名稱。</span><span class="sxs-lookup"><span data-stu-id="8e350-146">By default, this is the name of the report project.</span></span> <span data-ttu-id="8e350-147">如果報表伺服器上沒有此資料夾，報表設計師會在發行報表時建立資料夾。</span><span class="sxs-lookup"><span data-stu-id="8e350-147">If the folder does not exist on the report server, Report Designer creates the folder when the reports are published.</span></span>  
  
 <span data-ttu-id="8e350-148">發行至以原生模式執行的報表伺服器時，請從根目錄開始指定資料夾階層的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="8e350-148">When publishing to a report server running in native mode, specify the full path of the folder hierarchy starting at the root.</span></span> <span data-ttu-id="8e350-149">如果某個資料夾位於另一個資料夾內，請從根目錄開始加入資料夾的路徑，例如 Folder1/Folder2/Folder3。</span><span class="sxs-lookup"><span data-stu-id="8e350-149">If a folder is located within another folder, include a path to the folder starting at the root, such as Folder1/Folder2/Folder3.</span></span>  
  
 <span data-ttu-id="8e350-150">發行至以 SharePoint 整合模式執行的報表伺服器時，請使用 SharePoint 文件庫的 URL。</span><span class="sxs-lookup"><span data-stu-id="8e350-150">When publishing to a report server running in SharePoint integrated mode, use a URL to SharePoint library.</span></span> <span data-ttu-id="8e350-151">例如，HTTP:// *\<servername>* / *\<site>* //documents/myfolder。</span><span class="sxs-lookup"><span data-stu-id="8e350-151">For example, http://*\<servername>*/*\<site>*/Documents/MyFolder.</span></span>  
  
 <span data-ttu-id="8e350-152">**TargetServerURL**</span><span class="sxs-lookup"><span data-stu-id="8e350-152">**TargetServerURL**</span></span>  
 <span data-ttu-id="8e350-153">目標報表伺服器的 URL。</span><span class="sxs-lookup"><span data-stu-id="8e350-153">The URL of the target report server.</span></span> <span data-ttu-id="8e350-154">在發行報表之前，您必須設定此屬性為有效的報表伺服器 URL。</span><span class="sxs-lookup"><span data-stu-id="8e350-154">Before you publish a report, you must set this property to a valid report server URL.</span></span>  
  
 <span data-ttu-id="8e350-155">發行到以原生模式執行的報表伺服器時，請使用報表伺服器虛擬目錄的 URL。</span><span class="sxs-lookup"><span data-stu-id="8e350-155">When publishing to a report server running in native mode, use the URL of the virtual directory of the report server.</span></span> <span data-ttu-id="8e350-156">例如，HTTP:// \<server> /reportserver。</span><span class="sxs-lookup"><span data-stu-id="8e350-156">For example, http://\<server>/reportserver.</span></span> <span data-ttu-id="8e350-157">這是報表伺服器的虛擬目錄，而非報表管理員。</span><span class="sxs-lookup"><span data-stu-id="8e350-157">This is the virtual directory of the report server, not Report Manager.</span></span> <span data-ttu-id="8e350-158">依預設，報表伺服器會安裝在名稱為 [reportserver] 的虛擬目錄中。</span><span class="sxs-lookup"><span data-stu-id="8e350-158">By default, the report server is installed in a virtual directory named "reportserver".</span></span>  
  
 <span data-ttu-id="8e350-159">發行至以 SharePoint 整合模式執行的報表伺服器時，請使用 SharePoint 頂層網站或子網站的 URL。</span><span class="sxs-lookup"><span data-stu-id="8e350-159">When publishing to a report server running in SharePoint integrated mode, use a URL to a SharePoint top-level site or subsite.</span></span> <span data-ttu-id="8e350-160">若未指定網站，則會使用預設的最上層網站。</span><span class="sxs-lookup"><span data-stu-id="8e350-160">If you do not specify a site, the default top-level site is used.</span></span> <span data-ttu-id="8e350-161">例如，HTTP:// \<*servername> *、HTTP://<* servername */\<*site>* 或 HTTP:// \<*servername> */\<*site>* / \<*subsite> \*。</span><span class="sxs-lookup"><span data-stu-id="8e350-161">For example, http://\<*servername>*, http://<* servername*/\<*site>* or http://\<*servername>*/\<*site>*/\<*subsite>\*.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e350-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e350-162">See Also</span></span>  
 <span data-ttu-id="8e350-163">[發行報表](../publish-reports.md) </span><span class="sxs-lookup"><span data-stu-id="8e350-163">[Publish Reports](../publish-reports.md) </span></span>  
 <span data-ttu-id="8e350-164">[將報表發行至 SharePoint 文件庫](../reports/publish-a-report-to-a-sharepoint-library.md) </span><span class="sxs-lookup"><span data-stu-id="8e350-164">[Publish a Report to a SharePoint Library](../reports/publish-a-report-to-a-sharepoint-library.md) </span></span>  
 <span data-ttu-id="8e350-165">[將部署屬性設定 &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="8e350-165">[Set Deployment Properties &#40;Reporting Services&#41;](set-deployment-properties-reporting-services.md) </span></span>  
 [<span data-ttu-id="8e350-166">報表設計師 F1 說明</span><span class="sxs-lookup"><span data-stu-id="8e350-166">Report Designer F1 Help</span></span>](report-designer-f1-help.md)  
  
  
