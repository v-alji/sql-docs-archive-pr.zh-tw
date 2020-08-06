---
title: 啟用遠端錯誤 (Reporting Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- remote data source [Reporting Services]
- EnableRemoteError server property
ms.assetid: 5f05022b-d557-43e0-b50a-f5e2a1846b83
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9d2a7e7e0b38b38bf563dfc2a8cff65c897c5293
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597578"
---
# <a name="enable-remote-errors-reporting-services"></a><span data-ttu-id="d3416-102">啟用遠端錯誤 (Reporting Services)</span><span class="sxs-lookup"><span data-stu-id="d3416-102">Enable Remote Errors (Reporting Services)</span></span>
  <span data-ttu-id="d3416-103">您可以在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 報表伺服器上設定伺服器屬性，以便傳回有關遠端伺服器上發生之錯誤狀況的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="d3416-103">You can set server properties on a [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] report server to return additional information about error conditions that occur on remote servers.</span></span> <span data-ttu-id="d3416-104">如果錯誤訊息包含「如需有關此錯誤的詳細資料，請導覽至本機伺服器電腦上的報表伺服器，或啟用遠端錯誤」這段文字，您可以設定 `EnableRemoteErrors` 屬性來存取可幫助您排解疑難問題的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="d3416-104">If an error message contains the text "For more information about this error, navigate to the report server on the local server machine, or enable remote errors", you can set the `EnableRemoteErrors` property to access additional information that can help you troubleshoot the problem.</span></span> <span data-ttu-id="d3416-105">如需詳細資訊，請參閱《 [線上叢書》中的](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md) 報表伺服器系統屬性 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d3416-105">For more information, see [Report Server System Properties](../report-server-web-service/net-framework/reporting-services-properties-report-server-system-properties.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
 <span data-ttu-id="d3416-106">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="d3416-106">**In this topic:**</span></span>  
  
-   [<span data-ttu-id="d3416-107">啟用 SharePoint 模式的遠端錯誤</span><span class="sxs-lookup"><span data-stu-id="d3416-107">Enable Remote Errors for SharePoint Mode</span></span>](#bkmk_sharepoint)  
  
-   [<span data-ttu-id="d3416-108">透過 SQL Server Management Studio 啟用遠端錯誤 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="d3416-108">Enable remote errors through SQL Server Management Studio (Native Mode)</span></span>](#bkmk_mgtStudio)  
  
-   [<span data-ttu-id="d3416-109">透過指令碼啟用遠端錯誤 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="d3416-109">Enable remote errors through script (Native Mode)</span></span>](#bkmk_script)  
  
-   [<span data-ttu-id="d3416-110">修改 ConfigurationInfo 資料表 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="d3416-110">Modifying the ConfigurationInfo table (Native Mode)</span></span>](#bkmk_ConfigurationInfo)  
  
##  <a name="enable-remote-errors-for-sharepoint-mode"></a><a name="bkmk_sharepoint"></a> <span data-ttu-id="d3416-111">啟用 SharePoint 模式的遠端錯誤</span><span class="sxs-lookup"><span data-stu-id="d3416-111">Enable Remote Errors for SharePoint Mode</span></span>  
 <span data-ttu-id="d3416-112">您可以透過兩種不同的程序啟用 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint 模式的遠端錯誤。</span><span class="sxs-lookup"><span data-stu-id="d3416-112">There are two different procedures for enabling remote errors for [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] SharePoint mode.</span></span> <span data-ttu-id="d3416-113">兩種不同的報表伺服器架構會採用不同的程序。</span><span class="sxs-lookup"><span data-stu-id="d3416-113">The procedure is different for the two different report server architectures.</span></span> <span data-ttu-id="d3416-114">[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 版本中導入的較新 SharePoint 服務架構會使用可針對每個 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式進行的設定。</span><span class="sxs-lookup"><span data-stu-id="d3416-114">The newer SharePoint service based architecture that was introduced in the [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] release, utilizes a setting that can be configured for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="d3416-115">較舊的架構則使用單一網站層級設定。</span><span class="sxs-lookup"><span data-stu-id="d3416-115">The older architecture utilizes a single site level setting.</span></span>  
  
#### <a name="enable-remote-errors-for-a-reporting-services-service-application"></a><span data-ttu-id="d3416-116">啟用 Reporting Services 服務應用程式的遠端錯誤</span><span class="sxs-lookup"><span data-stu-id="d3416-116">Enable Remote errors for a Reporting Services Service Application</span></span>  
  
1.  <span data-ttu-id="d3416-117">針對隨 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 或較新版本 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]一併安裝的 SharePoint 模式報表伺服器，請啟用服務應用程式設定 **[啟用遠端錯誤]** 。</span><span class="sxs-lookup"><span data-stu-id="d3416-117">For a SharePoint mode report server installed with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] or a newer version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], enable the service application setting **Enable remote errors**.</span></span> <span data-ttu-id="d3416-118">此設定可針對每個 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式設定。</span><span class="sxs-lookup"><span data-stu-id="d3416-118">The setting can be configured for each [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application.</span></span>  
  
2.  <span data-ttu-id="d3416-119">在 [SharePoint 管理中心] 的 **[應用程式管理]** 群組中，按一下 **[管理服務應用程式]** 。</span><span class="sxs-lookup"><span data-stu-id="d3416-119">In SharePoint Central Administration, click **Manage service applications** in the **Application Management** group.</span></span>  
  
3.  <span data-ttu-id="d3416-120">尋找您的 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務應用程式，然後按一下服務應用程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="d3416-120">Find your [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service application and click the name of your service application.</span></span>  
  
4.  <span data-ttu-id="d3416-121">按一下 **[系統設定]** 。</span><span class="sxs-lookup"><span data-stu-id="d3416-121">Click **System Settings**.</span></span>  
  
5.  <span data-ttu-id="d3416-122">按一下 **[安全性]** 區段中的 **[啟用遠端錯誤]** 。</span><span class="sxs-lookup"><span data-stu-id="d3416-122">Click **Enable Remote Errors** in the **Security** section.</span></span>  
  
6.  <span data-ttu-id="d3416-123">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d3416-123">Click **OK**.</span></span>  
  
#### <a name="enable-remote-errors-for-a-sharepoint-site"></a><span data-ttu-id="d3416-124">啟用 SharePoint 網站的遠端錯誤</span><span class="sxs-lookup"><span data-stu-id="d3416-124">Enable Remote Errors for a SharePoint Site</span></span>  
  
1.  <span data-ttu-id="d3416-125">針對隨 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 之前的 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]版本一併安裝的 SharePoint 模式報表伺服器，請啟用網站設定 **[在本機模式中啟用遠端錯誤]** 。</span><span class="sxs-lookup"><span data-stu-id="d3416-125">For a SharePoint mode report server installed with a version of [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] prior to [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], enable the site setting **Enable remote errors in local mode**.</span></span>  
  
2.  <span data-ttu-id="d3416-126">在 **[網站動作]** 中，按一下您要修改之網站的 **[網站設定]** 。</span><span class="sxs-lookup"><span data-stu-id="d3416-126">In **Site Actions** click **Site Settings** for the site you want to modify.</span></span>  
  
3.  <span data-ttu-id="d3416-127">按一下 **[Reporting Services]** 群組中的 **[Reporting Services 網站設定]** 。</span><span class="sxs-lookup"><span data-stu-id="d3416-127">Click **Reporting Services Site Settings** in the **Reporting Services** group.</span></span>  
  
4.  <span data-ttu-id="d3416-128">按一下 **[在本機模式中啟用遠端錯誤]** 。</span><span class="sxs-lookup"><span data-stu-id="d3416-128">Click **Enable remote errors in local mode**.</span></span>  
  
5.  <span data-ttu-id="d3416-129">按一下 [檔案] &gt; [新增] &gt; [專案] </span><span class="sxs-lookup"><span data-stu-id="d3416-129">Click **OK**</span></span>  
  
##  <a name="enable-remote-errors-through-sql-server-management-studio-native-mode"></a><a name="bkmk_mgtStudio"></a> <span data-ttu-id="d3416-130">透過 SQL Server Management Studio 啟用遠端錯誤 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="d3416-130">Enable remote errors through SQL Server Management Studio (Native Mode)</span></span>  
  
1.  <span data-ttu-id="d3416-131">啟動 Management Studio，然後連接到報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="d3416-131">Start Management Studio and connect to a report server instance.</span></span> <span data-ttu-id="d3416-132">如需詳細資訊，請參閱《 [線上叢書》中的](../tools/connect-to-a-report-server-in-management-studio.md) 連接至 Management Studio 中的報表伺服器 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d3416-132">For more information, see [Connect to a Report Server in Management Studio](../tools/connect-to-a-report-server-in-management-studio.md) in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
2.  <span data-ttu-id="d3416-133">以滑鼠右鍵按一下報表伺服器節點，然後選取 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="d3416-133">Right-click the report server node, and select **Properties**.</span></span>  
  
3.  <span data-ttu-id="d3416-134">按一下 **[進階]** ，即可開啟屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="d3416-134">Click **Advanced** to open the properties page.</span></span> <span data-ttu-id="d3416-135">如需詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中的[伺服器屬性 &#40;進階頁面&#41; - Reporting Services](../tools/server-properties-advanced-page-reporting-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d3416-135">For more information, see [Server Properties &#40;Advanced Page&#41; - Reporting Services](../tools/server-properties-advanced-page-reporting-services.md)in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
4.  <span data-ttu-id="d3416-136">在中 `EnableRemoteErrors` ，選取 `True` 。</span><span class="sxs-lookup"><span data-stu-id="d3416-136">In `EnableRemoteErrors`, select `True`.</span></span>  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="enable-remote-errors-through-script-native-mode"></a><a name="bkmk_script"></a> <span data-ttu-id="d3416-137">透過指令碼啟用遠端錯誤 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="d3416-137">Enable remote errors through script (Native Mode)</span></span>  
  
1.  <span data-ttu-id="d3416-138">建立一個文字檔案，然後將下列指令碼複製到這個檔案中。</span><span class="sxs-lookup"><span data-stu-id="d3416-138">Create a text file and copy the following script into the file.</span></span>  
  
    ```  
    Public Sub Main()  
      Dim P As New [Property]()  
      P.Name = "EnableRemoteErrors"  
      P.Value = True  
      Dim Properties(0) As [Property]  
      Properties(0) = P  
      Try  
        rs.SetSystemProperties(Properties)  
        Console.WriteLine("Remote errors enabled.")  
      Catch SE As SoapException  
        Console.WriteLine(SE.Detail.OuterXml)  
      End Try  
    End Sub  
    ```  
  
2.  <span data-ttu-id="d3416-139">請這個檔案儲存為 EnableRemoteErrors.rss。</span><span class="sxs-lookup"><span data-stu-id="d3416-139">Save the file as EnableRemoteErrors.rss.</span></span>  
  
3.  <span data-ttu-id="d3416-140">按一下 **[開始]** ，然後指向 **[執行]** ，再輸入 **cmd**，並按一下 **[確定]** ，開啟命令提示字元視窗。</span><span class="sxs-lookup"><span data-stu-id="d3416-140">Click **Start**, point to **Run**, type **cmd**, and click **OK** to open a command prompt window.</span></span>  
  
4.  <span data-ttu-id="d3416-141">瀏覽至包含您剛剛建立之 .rss 檔案的目錄。</span><span class="sxs-lookup"><span data-stu-id="d3416-141">Navigate to the directory that contains the .rss file you just created.</span></span>  
  
5.  <span data-ttu-id="d3416-142">輸入下列命令列，以伺服器的實際名稱來取代 *servername* 。</span><span class="sxs-lookup"><span data-stu-id="d3416-142">Type the following command line, replacing *servername* with the actual name of your server:</span></span>  
  
    ```  
    rs -i EnableRemoteErrors.rss -s http://servername/ReportServer  
    ```  
  
6.  <span data-ttu-id="d3416-143">如需詳細資訊，請參閱 [RS.exe 公用程式 &#40;SSRS&#41;](../tools/rs-exe-utility-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="d3416-143">For more information, see [RS.exe Utility &#40;SSRS&#41;](../tools/rs-exe-utility-ssrs.md)</span></span>  
  
##  <a name="modifying-the-configurationinfo-table-native-mode"></a><a name="bkmk_ConfigurationInfo"></a> <span data-ttu-id="d3416-144">修改 ConfigurationInfo 資料表 (原生模式)</span><span class="sxs-lookup"><span data-stu-id="d3416-144">Modifying the ConfigurationInfo table (Native Mode)</span></span>  
  
1.  > [!NOTE]  
    >  <span data-ttu-id="d3416-145">您可以編輯報表伺服器資料庫中的**ConfigurationInfo**資料表，將設定 `EnableRemoteErrors` 為 `True` ，但如果報表伺服器是主動使用的，您應該使用 SQL Server Management Studio 或腳本來修改設定。</span><span class="sxs-lookup"><span data-stu-id="d3416-145">You can edit the **ConfigurationInfo** table in the report server database to set `EnableRemoteErrors` to `True`, but if the report server is actively used, you should use SQL Server Management Studio or script to modify the settings.</span></span> <span data-ttu-id="d3416-146">如果您修改資料庫中的設定，則須先重新啟動 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 服務，變更才會生效。</span><span class="sxs-lookup"><span data-stu-id="d3416-146">If you modify the setting in the database, you need to restart the [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] service before the changes take effect.</span></span>  
  
  
