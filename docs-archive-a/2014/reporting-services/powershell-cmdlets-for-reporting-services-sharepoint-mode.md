---
title: 適用于 Reporting Services SharePoint 模式的 PowerShell Cmdlet |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 7835bc97-2827-4215-b0dd-52f692ce5e02
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2b20ad870fd8a9cd7f220eebb2b954d7a88a10c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710257"
---
# <a name="powershell-cmdlets-for-reporting-services-sharepoint-mode"></a><span data-ttu-id="1360f-102">Reporting Services SharePoint 模式的 PowerShell Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1360f-102">PowerShell cmdlets for Reporting Services SharePoint Mode</span></span>
  <span data-ttu-id="1360f-103">當您安裝 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] sharepoint 模式時，系統會安裝 PowerShell Cmdlet，以支援 SharePoint 模式的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="1360f-103">When you install [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint mode, PowerShell cmdlets are installed to support report Servers in SharePoint mode.</span></span> <span data-ttu-id="1360f-104">這些指令程式涵蓋三個功能類別。</span><span class="sxs-lookup"><span data-stu-id="1360f-104">The cmdlets cover three categories of functionality.</span></span>  
  
-   <span data-ttu-id="1360f-105">安裝 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 共用服務和 Proxy。</span><span class="sxs-lookup"><span data-stu-id="1360f-105">Installation of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint shared service and proxy.</span></span>  
  
-   <span data-ttu-id="1360f-106">佈建和管理 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式和相關聯 Proxy。</span><span class="sxs-lookup"><span data-stu-id="1360f-106">Provisioning and management of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service applications and associated proxies.</span></span>  
  
-   <span data-ttu-id="1360f-107">管理 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 功能，例如擴充功能和加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="1360f-107">Management of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] features, for example extensions and encryption keys.</span></span>  
  
||  
|-|  
|[!INCLUDE[applies](../includes/applies-md.md)]<span data-ttu-id="1360f-108">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="1360f-108">[!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint Mode</span></span>|  
  
 <span data-ttu-id="1360f-109">**本主題包含下列內容：**</span><span class="sxs-lookup"><span data-stu-id="1360f-109">**This topic contains the following:**</span></span>  
  
-   [<span data-ttu-id="1360f-110">Cmdlet 摘要</span><span class="sxs-lookup"><span data-stu-id="1360f-110">Cmdlet Summary</span></span>](#bkmk_cmdlet_sum)  
  
-   [<span data-ttu-id="1360f-111">共用服務和 Proxy Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1360f-111">Shared Service and Proxy Cmdlets</span></span>](#bkmk_sharedservice_cmdlets)  
  
-   [<span data-ttu-id="1360f-112">服務應用程式和 Proxy Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1360f-112">Service Application and Proxy Cmdlets</span></span>](#bkmk_serviceapp_cmdlets)  
  
-   [<span data-ttu-id="1360f-113">Reporting Services 自訂功能 Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1360f-113">Reporting Services Custom Functionality Cmdlets</span></span>](#bkmk_ssrsfeatures_cmdlets)  
  
-   [<span data-ttu-id="1360f-114">基本範例</span><span class="sxs-lookup"><span data-stu-id="1360f-114">Basic Samples</span></span>](#bkmk_basic_samples)  
  
-   [<span data-ttu-id="1360f-115">詳細範例</span><span class="sxs-lookup"><span data-stu-id="1360f-115">Detailed Samples</span></span>](#bkmk_detailedsamples)  
  
    -   [<span data-ttu-id="1360f-116">建立 Reporting Services 服務應用程式和 proxy</span><span class="sxs-lookup"><span data-stu-id="1360f-116">Create a Reporting Services service application and proxy</span></span>](#bkmk_example_create_service_application)  
  
    -   [<span data-ttu-id="1360f-117">檢閱及更新 Reporting Services 傳遞延伸模組</span><span class="sxs-lookup"><span data-stu-id="1360f-117">Review and update a Reporting Services delivery extension</span></span>](#bkmk_example_delivery_extension)  
  
    -   [<span data-ttu-id="1360f-118">取得並設定 Reporting Services 應用程式資料庫的屬性，例如資料庫逾時</span><span class="sxs-lookup"><span data-stu-id="1360f-118">Get and set properties of the Reporting Servicea application database, for example database timeout</span></span>](#bkmk_example_db_properties)  
  
    -   [<span data-ttu-id="1360f-119">列出 reporting services 資料延伸模組-SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="1360f-119">List reporting services data extensions - SharePoint mode</span></span>](#bkmk_example_list_data_extensions)  
  
    -   [<span data-ttu-id="1360f-120">變更並列出訂閱擁有者</span><span class="sxs-lookup"><span data-stu-id="1360f-120">Change and list subscription owners</span></span>](#bkmk_change_subscription_owner)  
  
##  <a name="cmdlet-summary"></a><a name="bkmk_cmdlet_sum"></a><span data-ttu-id="1360f-121">Cmdlet 摘要</span><span class="sxs-lookup"><span data-stu-id="1360f-121">Cmdlet Summary</span></span>  

 <span data-ttu-id="1360f-122">若要執行指令程式，您需要開啟 SharePoint 管理命令介面。</span><span class="sxs-lookup"><span data-stu-id="1360f-122">To run the cmdlets you need to open the SharePoint Management Shell.</span></span> <span data-ttu-id="1360f-123">您也可以使用 Microsoft Windows 隨附的圖形化使用者介面編輯器 **Windows PowerShell 整合式指令碼環境 (ISE)**。</span><span class="sxs-lookup"><span data-stu-id="1360f-123">You can also use the graphical user interface editor that is included with Microsoft Windows, **Windows PowerShell Integrated Scripting Environment (ISE)**.</span></span> <span data-ttu-id="1360f-124">如需詳細資訊，請參閱 [Starting Windows PowerShell on Windows Server](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell)。</span><span class="sxs-lookup"><span data-stu-id="1360f-124">For more information, see [Starting Windows PowerShell on Windows Server](https://docs.microsoft.com/powershell/scripting/getting-started/starting-windows-powershell).</span></span> <span data-ttu-id="1360f-125">在下列 Cmdlet 摘要中，服務應用程式「資料庫」的參考是指服務應用程式所建立和使用的所有資料庫 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="1360f-125">In the following cmdlet summaries, the references to service application 'databases', refer to all of the databases created and used by a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="1360f-126">其中包括組態、警示和暫時資料庫。</span><span class="sxs-lookup"><span data-stu-id="1360f-126">This includes the configuration, alerting, and temp databases.</span></span>  

  
 <span data-ttu-id="1360f-127">當您輸入 PowerShell 範例時，將會看到類似下面的錯誤訊息：</span><span class="sxs-lookup"><span data-stu-id="1360f-127">If you see an error message similar to the following when you type the PowerShell examples:</span></span>  
  
-   <span data-ttu-id="1360f-128">Install-SPRSService: 無法辨識 'Install-SPRSService' 詞彙是否為</span><span class="sxs-lookup"><span data-stu-id="1360f-128">Install-SPRSService : The term 'Install-SPRSService' is not recognized as the</span></span>  
    <span data-ttu-id="1360f-129">Cmdlet、函數、指令檔或可執行程式的名稱。</span><span class="sxs-lookup"><span data-stu-id="1360f-129">name of a cmdlet, function, script file, or operable program.</span></span> <span data-ttu-id="1360f-130">請檢查名稱拼字，如果名稱含有路徑，請確認路徑正確，然後再試一次。</span><span class="sxs-lookup"><span data-stu-id="1360f-130">Check the spelling of the name, or if a path was included, verify that the path is correct and try again.</span></span>  
  
 <span data-ttu-id="1360f-131">發生以下其中一個問題：</span><span class="sxs-lookup"><span data-stu-id="1360f-131">One of the following issues is occurring:</span></span>  
  
-   [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="1360f-132">SharePoint 模式未安裝，因此 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 指令程式也未安裝。</span><span class="sxs-lookup"><span data-stu-id="1360f-132">SharePoint mode is not installed and therefore the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] cmdlets are not installed.</span></span>  
  
-   <span data-ttu-id="1360f-133">您已在 Windows PowerShell 或 Windows PowerShell ISE 中執行 PowerShell 命令，而不是在 SharePoint 管理命令介面中執行。</span><span class="sxs-lookup"><span data-stu-id="1360f-133">You ran the PowerShell command in Windows PowerShell or Windows PowerShell ISE instead of the SharePoint Management Shell.</span></span> <span data-ttu-id="1360f-134">使用 SharePoint 管理命令介面，或是透過以下命令將 SharePoint 嵌入式管理單元加入至 Windows PowerShell 視窗：</span><span class="sxs-lookup"><span data-stu-id="1360f-134">Use the SharePoint Management shell or add the SharePoint Snap-in to the Windows PowerShell window with the following command:</span></span>  
  
    ```powershell
    Add-PSSnapin Microsoft.SharePoint.PowerShell  
    ```  
  
 <span data-ttu-id="1360f-135">如需詳細資訊，請參閱[使用 Windows PowerShell 來管理 SharePoint 2013](https://technet.microsoft.com/library/ee806878.aspx) (https://technet.microsoft.com/library/ee806878.aspx) 。</span><span class="sxs-lookup"><span data-stu-id="1360f-135">For more information see [Use Windows PowerShell to administer SharePoint 2013](https://technet.microsoft.com/library/ee806878.aspx) (https://technet.microsoft.com/library/ee806878.aspx).</span></span>  
  
#### <a name="to-open-the-sharepoint-management-shell-and-run-cmdlets"></a><span data-ttu-id="1360f-136">若要開啟 SharePoint 管理命令介面並執行指令程式</span><span class="sxs-lookup"><span data-stu-id="1360f-136">To Open the SharePoint Management Shell and run cmdlets</span></span>  
  
1.  <span data-ttu-id="1360f-137">按一下 [**開始**] 按鈕</span><span class="sxs-lookup"><span data-stu-id="1360f-137">Click the **Start** button</span></span>  
  
2.  <span data-ttu-id="1360f-138">按一下 **[Microsoft SharePoint 產品]** 群組。</span><span class="sxs-lookup"><span data-stu-id="1360f-138">Click the **Microsoft SharePoint Products** group.</span></span>  
  
3.  <span data-ttu-id="1360f-139">按一下 **[SharePoint 管理命令介面]**。</span><span class="sxs-lookup"><span data-stu-id="1360f-139">Click the **SharePoint Management Shell**.</span></span>  
  
 <span data-ttu-id="1360f-140">若要檢視 Cmdlet 的命令列說明，請在 PowerShell 命令提示字元中使用 PowerShell 'Get-Help' 命令。</span><span class="sxs-lookup"><span data-stu-id="1360f-140">To view command line help for a cmdlet use the PowerShell 'Get-Help' command at the PowerShell command prompt.</span></span> <span data-ttu-id="1360f-141">例如：</span><span class="sxs-lookup"><span data-stu-id="1360f-141">For example:</span></span>  
  
 `Get-Help Get-SPRSServiceApplicationServers`  
  
###  <a name="shared-service-and-proxy-cmdlets"></a><a name="bkmk_sharedservice_cmdlets"></a> <span data-ttu-id="1360f-142">共用服務和 Proxy 指令程式</span><span class="sxs-lookup"><span data-stu-id="1360f-142">Shared Service and Proxy Cmdlets</span></span>  
 <span data-ttu-id="1360f-143">下表包含用於 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 共用服務的 PowerShell 指令程式。</span><span class="sxs-lookup"><span data-stu-id="1360f-143">The following table contains the PowerShell cmdlets for the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint shared service.</span></span>  
  
|<span data-ttu-id="1360f-144">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1360f-144">Cmdlet</span></span>|<span data-ttu-id="1360f-145">描述</span><span class="sxs-lookup"><span data-stu-id="1360f-145">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1360f-146">Install-SPRSService</span><span class="sxs-lookup"><span data-stu-id="1360f-146">Install-SPRSService</span></span>|<span data-ttu-id="1360f-147">安裝及註冊或是解除安裝 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 共用服務。</span><span class="sxs-lookup"><span data-stu-id="1360f-147">Installs and registers, or uninstalls, the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] shared service.</span></span> <span data-ttu-id="1360f-148">只有在安裝了 SharePoint 模式之 SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 的電腦上才可以執行這項作業。</span><span class="sxs-lookup"><span data-stu-id="1360f-148">This can be done only on the machine that has an installation of SQL Server [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] in SharePoint mode.</span></span> <span data-ttu-id="1360f-149">針對安裝會進行兩項作業：</span><span class="sxs-lookup"><span data-stu-id="1360f-149">For installation, two operations occur:</span></span><br /><br /> <span data-ttu-id="1360f-150">1) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務已安裝在伺服器陣列中。</span><span class="sxs-lookup"><span data-stu-id="1360f-150">1) The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service is installed in the farm.</span></span><br /><br /> <span data-ttu-id="1360f-151">2) 將 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務實例安裝到目前的電腦上。</span><span class="sxs-lookup"><span data-stu-id="1360f-151">2) The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service instance is installed to the current machine.</span></span><br /><br /> <span data-ttu-id="1360f-152">針對解除安裝會進行兩項作業：</span><span class="sxs-lookup"><span data-stu-id="1360f-152">For Uninstallation, two operations occur:</span></span><br /><span data-ttu-id="1360f-153">1) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務會從目前的電腦卸載。</span><span class="sxs-lookup"><span data-stu-id="1360f-153">1) The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service is uninstalled from the current machine.</span></span><br /><span data-ttu-id="1360f-154">2) [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務會從伺服器陣列卸載。</span><span class="sxs-lookup"><span data-stu-id="1360f-154">2) The [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service is uninstalled from the farm.</span></span><br /><br /> <br /><br /> <span data-ttu-id="1360f-155">注意：如果伺服器陣列中有任何其他電腦已安裝 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務，或者伺服器陣列中仍有執行中的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式，則會顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="1360f-155">NOTE: If there are any other machines in the farm that have the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service installed, or if there are still [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service applications running in the farm, a warning message is displayed.</span></span>|  
|<span data-ttu-id="1360f-156">Install-SPRSServiceProxy</span><span class="sxs-lookup"><span data-stu-id="1360f-156">Install-SPRSServiceProxy</span></span>|<span data-ttu-id="1360f-157">在 SharePoint 伺服器陣列中安裝及註冊或是解除安裝 Reporting Services 服務 Proxy。</span><span class="sxs-lookup"><span data-stu-id="1360f-157">Installs and registers, or uninstalls, the Reporting Services service proxy in the SharePoint farm.</span></span>|  
|<span data-ttu-id="1360f-158">Get-SPRSProxyUrl</span><span class="sxs-lookup"><span data-stu-id="1360f-158">Get-SPRSProxyUrl</span></span>|<span data-ttu-id="1360f-159">取得存取 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務的 URL。</span><span class="sxs-lookup"><span data-stu-id="1360f-159">Gets the URL(s) for accessing the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service.</span></span>|  
|<span data-ttu-id="1360f-160">Get-SPRSServiceApplicationServers</span><span class="sxs-lookup"><span data-stu-id="1360f-160">Get-SPRSServiceApplicationServers</span></span>|<span data-ttu-id="1360f-161">在包含 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 共用服務安裝的本機 SharePoint 伺服器陣列中取得所有伺服器。</span><span class="sxs-lookup"><span data-stu-id="1360f-161">Gets all servers in the local SharePoint farm that contain an installation of the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] shared service.</span></span> <span data-ttu-id="1360f-162">這個指令程式對於 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 升級很有用，可判斷哪些伺服器執行共用服務因此需要升級。</span><span class="sxs-lookup"><span data-stu-id="1360f-162">This cmdlet is useful for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] upgrades, to determine which servers run the shared service and therefore need to be upgraded.</span></span>|  
  
###  <a name="service-application-and-proxy-cmdlets"></a><a name="bkmk_serviceapp_cmdlets"></a> <span data-ttu-id="1360f-163">服務應用程式和 Proxy 指令程式</span><span class="sxs-lookup"><span data-stu-id="1360f-163">Service Application and Proxy Cmdlets</span></span>  
 <span data-ttu-id="1360f-164">下表包含用於 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式及其相關聯 Proxy 的 PowerShell 指令程式。</span><span class="sxs-lookup"><span data-stu-id="1360f-164">The following table contains the PowerShell cmdlets for [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service applications and their associated proxies.</span></span>  
  
|<span data-ttu-id="1360f-165">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1360f-165">cmdlet</span></span>|<span data-ttu-id="1360f-166">描述</span><span class="sxs-lookup"><span data-stu-id="1360f-166">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1360f-167">Get-SPRSServiceApplication</span><span class="sxs-lookup"><span data-stu-id="1360f-167">Get-SPRSServiceApplication</span></span>|<span data-ttu-id="1360f-168">取得一或多個 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式物件。</span><span class="sxs-lookup"><span data-stu-id="1360f-168">Gets one or more [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application objects.</span></span>|  
|<span data-ttu-id="1360f-169">New-SPRSServiceApplication</span><span class="sxs-lookup"><span data-stu-id="1360f-169">New-SPRSServiceApplication</span></span>|<span data-ttu-id="1360f-170">建立新的 Reporting Services 服務應用程式與相關聯的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1360f-170">Create a new Reporting Services service application and associated databases.</span></span><br /><br /> <span data-ttu-id="1360f-171">LogonType 參數：指定報表伺服器會使用 SSRS 應用程式集區帳戶或是 SQL Server 登入來存取報表伺服器資料庫。</span><span class="sxs-lookup"><span data-stu-id="1360f-171">LogonType Parameter: Specifies if the report server uses the SSRS Application Pool account or a SQL Server login to access the report server database.</span></span> <span data-ttu-id="1360f-172">可以是下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="1360f-172">It can be one of the following:</span></span><br /><br /> <span data-ttu-id="1360f-173">0 Windows 驗證</span><span class="sxs-lookup"><span data-stu-id="1360f-173">0 Windows Authentication</span></span><br /><br /> <span data-ttu-id="1360f-174">1 SQL Server</span><span class="sxs-lookup"><span data-stu-id="1360f-174">1 SQL Server</span></span><br /><br /> <span data-ttu-id="1360f-175">2 應用程式集區帳戶 (預設)</span><span class="sxs-lookup"><span data-stu-id="1360f-175">2 Application Pool Account (default)</span></span>|  
|<span data-ttu-id="1360f-176">Remove-SPRSServiceApplication</span><span class="sxs-lookup"><span data-stu-id="1360f-176">Remove-SPRSServiceApplication</span></span>|<span data-ttu-id="1360f-177">移除指定的 Reporting Services 服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="1360f-177">Removes the specified Reporting Services service application.</span></span> <span data-ttu-id="1360f-178">這項操作也會移除相關聯的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1360f-178">This will also remove the associated databases.</span></span>|  
|<span data-ttu-id="1360f-179">Set-SPRSServiceApplication</span><span class="sxs-lookup"><span data-stu-id="1360f-179">Set-SPRSServiceApplication</span></span>|<span data-ttu-id="1360f-180">編輯現有 Reporting Services 服務應用程式的屬性。</span><span class="sxs-lookup"><span data-stu-id="1360f-180">Edits the properties of an existing Reporting Services service application.</span></span>|  
|<span data-ttu-id="1360f-181">New-SPRSServiceApplicationProxy</span><span class="sxs-lookup"><span data-stu-id="1360f-181">New-SPRSServiceApplicationProxy</span></span>|<span data-ttu-id="1360f-182">建立新的 Reporting Services 服務應用程式 Proxy。</span><span class="sxs-lookup"><span data-stu-id="1360f-182">Creates a new Reporting Services service application proxy.</span></span>|  
|<span data-ttu-id="1360f-183">Get-SPRSServiceApplicationProxy</span><span class="sxs-lookup"><span data-stu-id="1360f-183">Get-SPRSServiceApplicationProxy</span></span>|<span data-ttu-id="1360f-184">取得一個或多個 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式 Proxy。</span><span class="sxs-lookup"><span data-stu-id="1360f-184">Gets one or more [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application proxies.</span></span>|  
|<span data-ttu-id="1360f-185">Dismount-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="1360f-185">Dismount-SPRSDatabase</span></span>|<span data-ttu-id="1360f-186">卸載 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式的服務應用程式資料庫。</span><span class="sxs-lookup"><span data-stu-id="1360f-186">Dismounts the service application databases for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="1360f-187">Remove-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="1360f-187">Remove-SPRSDatabase</span></span>|<span data-ttu-id="1360f-188">移除 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式的服務應用程式資料庫。</span><span class="sxs-lookup"><span data-stu-id="1360f-188">Remove the service application databases for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="1360f-189">Set-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="1360f-189">Set-SPRSDatabase</span></span>|<span data-ttu-id="1360f-190">設定與 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式相關聯之資料庫的屬性。</span><span class="sxs-lookup"><span data-stu-id="1360f-190">Sets the properties of the databases associated to a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="1360f-191">Mount-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="1360f-191">Mount-SPRSDatabase</span></span>|<span data-ttu-id="1360f-192">掛接 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1360f-192">Mounts databases for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="1360f-193">New-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="1360f-193">New-SPRSDatabase</span></span>|<span data-ttu-id="1360f-194">為指定的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式建立新的服務應用程式資料庫。</span><span class="sxs-lookup"><span data-stu-id="1360f-194">Create new service application databases for the specified [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span>|  
|<span data-ttu-id="1360f-195">Get-SPRSDatabaseCreationScript</span><span class="sxs-lookup"><span data-stu-id="1360f-195">Get-SPRSDatabaseCreationScript</span></span>|<span data-ttu-id="1360f-196">針對 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式將資料庫建立指令碼輸出到畫面。</span><span class="sxs-lookup"><span data-stu-id="1360f-196">Outputs the database creation script to the screen for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="1360f-197">然後您就可以在 SQL Server Management Studio 中執行指令碼。</span><span class="sxs-lookup"><span data-stu-id="1360f-197">You can then run the script in SQL Server Management Studio.</span></span>|  
|<span data-ttu-id="1360f-198">Get-SPRSDatabase</span><span class="sxs-lookup"><span data-stu-id="1360f-198">Get-SPRSDatabase</span></span>|<span data-ttu-id="1360f-199">取得一個或多個 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式資料庫。</span><span class="sxs-lookup"><span data-stu-id="1360f-199">Gets one or more [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application databases.</span></span> <span data-ttu-id="1360f-200">使用命令來取得服務應用程式資料庫的識別碼，以便使用 Set-SPRSDatabase Cmdlet 來修改屬性，例如 `querytimeout`。</span><span class="sxs-lookup"><span data-stu-id="1360f-200">Use the command to get the ID of service application database so you can use the Set-SPRSDatabase comdlet to modify properties, for example the `querytimeout`.</span></span> <span data-ttu-id="1360f-201">請參閱本主題中的範例，[取得並設定 Reporting Servicea 應用程式資料庫的屬性，例如資料庫超時](#bkmk_example_db_properties)。</span><span class="sxs-lookup"><span data-stu-id="1360f-201">See the example in this topic, [Get and set properties of the Reporting Servicea application database, for example database timeout](#bkmk_example_db_properties).</span></span>|  
|<span data-ttu-id="1360f-202">Get-SPRSDatabaseRightsScript</span><span class="sxs-lookup"><span data-stu-id="1360f-202">Get-SPRSDatabaseRightsScript</span></span>|<span data-ttu-id="1360f-203">針對 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式將資料庫權限指令碼輸出到畫面。</span><span class="sxs-lookup"><span data-stu-id="1360f-203">Outputs the database rights script to the screen for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span> <span data-ttu-id="1360f-204">它會提示您提供所需的使用者和資料庫，然後傳回您可執行以修改權限的 Transact SQL。</span><span class="sxs-lookup"><span data-stu-id="1360f-204">It will prompt for desired user and database then returns transact SQL you can run to modify permissions.</span></span> <span data-ttu-id="1360f-205">然後您就可以在 SQL Server Management Studio 中執行這個指令碼。</span><span class="sxs-lookup"><span data-stu-id="1360f-205">You can then run this script in SQL Server Management Studio.</span></span>|  
|<span data-ttu-id="1360f-206">Get-SPRSDatabaseUpgradeScript</span><span class="sxs-lookup"><span data-stu-id="1360f-206">Get-SPRSDatabaseUpgradeScript</span></span>|<span data-ttu-id="1360f-207">將資料庫升級指令碼輸出至畫面。</span><span class="sxs-lookup"><span data-stu-id="1360f-207">Outputs a database upgrade script to the screen.</span></span> <span data-ttu-id="1360f-208">指令碼會將 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式資料庫升級至目前 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 安裝的資料庫版本。</span><span class="sxs-lookup"><span data-stu-id="1360f-208">The script will upgrade [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application databases to the database version of the current [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] installation.</span></span>|  
  
###  <a name="reporting-services-custom-functionality-cmdlets"></a><a name="bkmk_ssrsfeatures_cmdlets"></a> <span data-ttu-id="1360f-209">Reporting Services 自訂功能指令程式</span><span class="sxs-lookup"><span data-stu-id="1360f-209">Reporting Services Custom Functionality Cmdlets</span></span>  
  
|<span data-ttu-id="1360f-210">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="1360f-210">Cmdlet</span></span>|<span data-ttu-id="1360f-211">描述</span><span class="sxs-lookup"><span data-stu-id="1360f-211">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1360f-212">Update-SPRSEncryptionKey</span><span class="sxs-lookup"><span data-stu-id="1360f-212">Update-SPRSEncryptionKey</span></span>|<span data-ttu-id="1360f-213">為指定的 Reporting Services 服務應用程式更新加密金鑰，並重新加密其資料。</span><span class="sxs-lookup"><span data-stu-id="1360f-213">Updates the encryption key for the specified Reporting Services service application and re-encrypts its data.</span></span>|  
|<span data-ttu-id="1360f-214">Restore-SPRSEncryptionKey</span><span class="sxs-lookup"><span data-stu-id="1360f-214">Restore-SPRSEncryptionKey</span></span>|<span data-ttu-id="1360f-215">為 Reporting Services 服務應用程式還原之前備份的加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="1360f-215">Restores a previously backed up encryption key for a Reporting Services service application.</span></span>|  
|<span data-ttu-id="1360f-216">Remove-SPRSEncryptedData</span><span class="sxs-lookup"><span data-stu-id="1360f-216">Remove-SPRSEncryptedData</span></span>|<span data-ttu-id="1360f-217">為指定的 Reporting Services 服務應用程式刪除加密的資料。</span><span class="sxs-lookup"><span data-stu-id="1360f-217">Delete the encrypted data for the specified Reporting Services service application.</span></span>|  
|<span data-ttu-id="1360f-218">Backup-SPRSEncryptionKey</span><span class="sxs-lookup"><span data-stu-id="1360f-218">Backup-SPRSEncryptionKey</span></span>|<span data-ttu-id="1360f-219">為指定的 Reporting Services 服務應用程式備份加密金鑰。</span><span class="sxs-lookup"><span data-stu-id="1360f-219">Backs up the encryption key for the specified Reporting Services service application.</span></span>|  
|<span data-ttu-id="1360f-220">New-SPRSExtension</span><span class="sxs-lookup"><span data-stu-id="1360f-220">New-SPRSExtension</span></span>|<span data-ttu-id="1360f-221">向 Reporting Services 服務應用程式註冊新的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1360f-221">Registers a new extension with a Reporting Services service application.</span></span>|  
|<span data-ttu-id="1360f-222">Set-SPRSExtension</span><span class="sxs-lookup"><span data-stu-id="1360f-222">Set-SPRSExtension</span></span>|<span data-ttu-id="1360f-223">設定現有 Reporting Services 延伸模組的屬性。</span><span class="sxs-lookup"><span data-stu-id="1360f-223">Sets the properties of an existing Reporting Services extension.</span></span>|  
|<span data-ttu-id="1360f-224">Remove-SPRSExtension</span><span class="sxs-lookup"><span data-stu-id="1360f-224">Remove-SPRSExtension</span></span>|<span data-ttu-id="1360f-225">從 Reporting Services 服務應用程式中移除延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1360f-225">Removes an extension from a Reporting Services service application.</span></span>|  
|<span data-ttu-id="1360f-226">Get-SPRSExtension</span><span class="sxs-lookup"><span data-stu-id="1360f-226">Get-SPRSExtension</span></span>|<span data-ttu-id="1360f-227">獲取一個或多個用於 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1360f-227">Gets one or more [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] extensions for a [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application.</span></span><br /><br /> <span data-ttu-id="1360f-228">有效值為：</span><span class="sxs-lookup"><span data-stu-id="1360f-228">Valid values are:</span></span><br /><br /> <span data-ttu-id="1360f-229">**傳遞**</span><span class="sxs-lookup"><span data-stu-id="1360f-229">**Delivery**</span></span><br /><br /> <span data-ttu-id="1360f-230">**DeliveryUI**</span><span class="sxs-lookup"><span data-stu-id="1360f-230">**DeliveryUI**</span></span><br /><br /> <span data-ttu-id="1360f-231">**轉譯**</span><span class="sxs-lookup"><span data-stu-id="1360f-231">**Render**</span></span><br /><br /> <span data-ttu-id="1360f-232">**Data**</span><span class="sxs-lookup"><span data-stu-id="1360f-232">**Data**</span></span><br /><br /> <span data-ttu-id="1360f-233">**安全性**</span><span class="sxs-lookup"><span data-stu-id="1360f-233">**Security**</span></span><br /><br /> <span data-ttu-id="1360f-234">**驗證**</span><span class="sxs-lookup"><span data-stu-id="1360f-234">**Authentication**</span></span><br /><br /> <span data-ttu-id="1360f-235">**EventProcessing**</span><span class="sxs-lookup"><span data-stu-id="1360f-235">**EventProcessing**</span></span><br /><br /> <span data-ttu-id="1360f-236">**ReportItems**</span><span class="sxs-lookup"><span data-stu-id="1360f-236">**ReportItems**</span></span><br /><br /> <span data-ttu-id="1360f-237">**Designer**</span><span class="sxs-lookup"><span data-stu-id="1360f-237">**Designer**</span></span><br /><br /> <span data-ttu-id="1360f-238">**ReportItemDesigner**</span><span class="sxs-lookup"><span data-stu-id="1360f-238">**ReportItemDesigner**</span></span><br /><br /> <span data-ttu-id="1360f-239">**ReportItemConverter**</span><span class="sxs-lookup"><span data-stu-id="1360f-239">**ReportItemConverter**</span></span><br /><br /> <span data-ttu-id="1360f-240">**ReportDefinitionCustomization**</span><span class="sxs-lookup"><span data-stu-id="1360f-240">**ReportDefinitionCustomization**</span></span>|  
|<span data-ttu-id="1360f-241">Get-SPRSSite</span><span class="sxs-lookup"><span data-stu-id="1360f-241">Get-SPRSSite</span></span>|<span data-ttu-id="1360f-242">根據是否啟用 "ReportingService" 功能取得 SharePoint 網站。</span><span class="sxs-lookup"><span data-stu-id="1360f-242">Gets the SharePoint sites based on whether the "ReportingService" feature is enabled.</span></span> <span data-ttu-id="1360f-243">根據預設，將會傳回啟用 "ReportingService" 功能的網站。</span><span class="sxs-lookup"><span data-stu-id="1360f-243">By default, sites that enable the "ReportingService" feature are returned.</span></span>|  
  
##  <a name="basic-samples"></a><a name="bkmk_basic_samples"></a><span data-ttu-id="1360f-244">基本範例</span><span class="sxs-lookup"><span data-stu-id="1360f-244">Basic Samples</span></span>  
 <span data-ttu-id="1360f-245">傳回名稱中包含 'SPRS' 的 Cmdlet 清單。</span><span class="sxs-lookup"><span data-stu-id="1360f-245">Return a list of cmdlets that contain 'SPRS' in the name.</span></span> <span data-ttu-id="1360f-246">這項操作將傳回完整的 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 指令程式清單。</span><span class="sxs-lookup"><span data-stu-id="1360f-246">This will be the full list of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] cmdlets.</span></span>  
  
```powershell
Get-command -noun *SPRS*  
```  
  
 <span data-ttu-id="1360f-247">或者透過更詳細的資訊，傳送到名為 commandlist.txt 的文字檔</span><span class="sxs-lookup"><span data-stu-id="1360f-247">Or with a little more detail, piped to a text file named commandlist.txt</span></span>  
  
```powershell
Get-Command -Noun *SPRS* | Select name, definition | Format-List | Out-File c:\commandlist.txt  
```  
  
 <span data-ttu-id="1360f-248">安裝 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint 服務和服務 Proxy。</span><span class="sxs-lookup"><span data-stu-id="1360f-248">Install the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] SharePoint service and service proxy.</span></span>  
  
```powershell
Install-SPRSService  
```  
  
```powershell
Install-SPRSServiceProxy  
```  
  
 <span data-ttu-id="1360f-249">啟動 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務</span><span class="sxs-lookup"><span data-stu-id="1360f-249">Start the [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service</span></span>  
  
```powershell
Get-SPServiceInstance -all | where {$_.TypeName -like "SQL Server Reporting*"} | Start-SPServiceInstance  
```  
  
 <span data-ttu-id="1360f-250">在 SharePoint 管理命令介面中輸入下列命令，即可從記錄檔傳回已篩選過的資料列清單。</span><span class="sxs-lookup"><span data-stu-id="1360f-250">Type the following command from the SharePoint Management Shell to return a filtered list of rows from the a log file.</span></span> <span data-ttu-id="1360f-251">此命令將會篩選包含 "ssrscustomactionerror" 的行。</span><span class="sxs-lookup"><span data-stu-id="1360f-251">The command will filter for lines that contain "ssrscustomactionerror".</span></span> <span data-ttu-id="1360f-252">這個範例會查看安裝 rssharepoint.msi 時建立的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="1360f-252">This example is looking at the log file created when the rssharepoint.msi was installed.</span></span>  
  
```powershell
Get-Content -Path C:\Users\testuser\AppData\Local\Temp\rs_sp_0.log | Select-String "ssrscustomactionerror"  
```  
  
##  <a name="detailed-samples"></a><a name="bkmk_detailedsamples"></a><span data-ttu-id="1360f-253">詳細範例</span><span class="sxs-lookup"><span data-stu-id="1360f-253">Detailed Samples</span></span>  
 <span data-ttu-id="1360f-254">除了下列範例之外，請參閱[適用于步驟1-4 的 Windows powershell 腳本](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_full_script)主題中的「Windows powershell 腳本」一節。</span><span class="sxs-lookup"><span data-stu-id="1360f-254">In addition to the following samples, see the section "Windows PowerShell Script" in the topic [Windows PowerShell script for Steps 1-4](../../2014/sql-server/install/install-reporting-services-sharepoint-mode-for-sharepoint-2013.md#bkmk_full_script).</span></span>  
  
###  <a name="create-a-reporting-services-service-application-and-proxy"></a><a name="bkmk_example_create_service_application"></a><span data-ttu-id="1360f-255">建立 Reporting Services 服務應用程式和 proxy</span><span class="sxs-lookup"><span data-stu-id="1360f-255">Create a Reporting Services service application and proxy</span></span>  
 <span data-ttu-id="1360f-256">這個範例指令碼會完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="1360f-256">This sample script completes the following tasks:</span></span>  
  
1.  <span data-ttu-id="1360f-257">建立 Reporting Services 服務應用程式和 Proxy。</span><span class="sxs-lookup"><span data-stu-id="1360f-257">Create a Reporting Services service application and proxy.</span></span> <span data-ttu-id="1360f-258">此指令碼會假設應用程式集區 "My App Pool" 已存在。</span><span class="sxs-lookup"><span data-stu-id="1360f-258">The script assumes the application pool "My App Pool" already exists.</span></span>  
  
2.  <span data-ttu-id="1360f-259">將 Proxy 加入至預設 Proxy 群組。</span><span class="sxs-lookup"><span data-stu-id="1360f-259">Add the proxy to the default proxy group</span></span>  
  
3.  <span data-ttu-id="1360f-260">將服務應用程式存取權授與連接埠 80 Web 應用程式的內容資料庫。</span><span class="sxs-lookup"><span data-stu-id="1360f-260">Grant the service app access to the port 80 web app's content database.</span></span> <span data-ttu-id="1360f-261">腳本假設網站 " http://sitename " 已經存在。</span><span class="sxs-lookup"><span data-stu-id="1360f-261">The script assumes site "http://sitename" already exists.</span></span>  
  
```powershell
# Create service application and service application proxy  
$appPool = Get-SPServiceApplicationPool "My App Pool"  
$serviceApp = New-SPRSServiceApplication "My RS Service App" -ApplicationPool $appPool  
$serviceAppProxy = New-SPRSServiceApplicationProxy -Name "My RS Service App Proxy" -ServiceApplication $serviceApp  
  
# Add service application proxy to default proxy group.  Any web application that uses the default proxy group will now be able to use this service application.  
Get-SPServiceApplicationProxyGroup -default | Add-SPServiceApplicationProxyGroupMember -Member $serviceAppProxy  
  
# Grant application pool account access to the port 80 web application's content database.  
$webApp = Get-SPWebApplication "http://sitename"  
$appPoolAccountName = $appPool.ProcessAccount.LookupName()  
$webApp.GrantAccessToProcessIdentity($appPoolAccountName)
```  
  
###  <a name="review-and-update-a-reporting-services-delivery-extension"></a><a name="bkmk_example_delivery_extension"></a><span data-ttu-id="1360f-262">審查和更新 Reporting Services 傳遞延伸模組</span><span class="sxs-lookup"><span data-stu-id="1360f-262">Review and update a Reporting Services delivery extension</span></span>  
 <span data-ttu-id="1360f-263">下列 PowerShell 指令碼範例會更新服務應用程式 `My RS Service App`之報表伺服器電子郵件傳遞延伸模組的組態。</span><span class="sxs-lookup"><span data-stu-id="1360f-263">The following PowerShell script example, updates the configuration for the report server e-mail delivery extension for the service application named `My RS Service App`.</span></span> <span data-ttu-id="1360f-264">更新 SMTP 伺服器 (`<email server name>`) 和 FROM 電子郵件別名 (`<your FROM email address>`) 的值。</span><span class="sxs-lookup"><span data-stu-id="1360f-264">Update the values for the SMTP server (`<email server name>`) and the FROM email alias (`<your FROM email address>`).</span></span>  
  
```powershell
$app = Get-SPRSServiceApplication -Name "My RS Service App"  
$emailCfg = Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml
$emailXml = [xml]$emailCfg
$emailXml.SelectSingleNode("//SMTPServer").InnerText = "<email server name>"  
$emailXml.SelectSingleNode("//SendUsing").InnerText = "2"  
$emailXml.SelectSingleNode("//SMTPAuthenticate").InnerText = "2"  
$emailXml.SelectSingleNode("//From").InnerText = '<your FROM email address>'  
Set-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" -ExtensionConfiguration $emailXml.OuterXml  
```  
  
 <span data-ttu-id="1360f-265">在上述範例中，如果您不知道服務應用程式的確實名稱，可以重新撰寫第一個陳述式，依據搜尋部分名稱的結果取得服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="1360f-265">In the above example if you did not know the exact name of the service application, you could rewrite the first statement to get the service application based on a search of the partial name.</span></span> <span data-ttu-id="1360f-266">例如：</span><span class="sxs-lookup"><span data-stu-id="1360f-266">For example:</span></span>  
  
```powershell
$app = Get-SPRSServiceApplication | Where {$_.name -like " ssrs_testapp *"}  
```  
  
 <span data-ttu-id="1360f-267">下列指令碼將針對服務應用程式「Reporting Services 應用程式」傳回報表伺服器電子郵件傳遞延伸模組的目前設定值。</span><span class="sxs-lookup"><span data-stu-id="1360f-267">The following script will return the current configuration values for the report server e-mail delivery extension for the service application named "Reporting Services Application".</span></span> <span data-ttu-id="1360f-268">第一個步驟是將變數 $app 的值設定為名稱為 "My RS Service App" 之服務應用程式的物件。</span><span class="sxs-lookup"><span data-stu-id="1360f-268">The first step sets the value of the variable $app to the object of the service application that has a name of " My RS Service App "</span></span>  
  
 <span data-ttu-id="1360f-269">第二個陳述式將取得變數 $app 中服務應用程式物件的「報表伺服器電子郵件」傳遞延伸模組，並且選取 configurationXML</span><span class="sxs-lookup"><span data-stu-id="1360f-269">The second statement will Get the 'Report Server Email' delivery extension for the service application object in variable $app, and select the configurationXML</span></span>  
  
```powershell
$app = Get-SPRSServiceapplication -Name "Reporting Services Application"  
Get-SPRSExtension -Identity $app -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
```  
  
 <span data-ttu-id="1360f-270">您也可以將上述兩個陳述式重新撰寫成一個：</span><span class="sxs-lookup"><span data-stu-id="1360f-270">You can also rewrite the above two statements as one:</span></span>  
  
```powershell
Get-SPRSServiceApplication -Name "Reporting Services Application" | Get-SPRSExtension -ExtensionType "Delivery" -Name "Report Server Email" | Select -ExpandProperty ConfigurationXml  
```  
  
###  <a name="get-and-set-properties-of-the-reporting-servicea-application-database-for-example-database-timeout"></a><a name="bkmk_example_db_properties"></a><span data-ttu-id="1360f-271">取得和設定 Reporting Servicea 應用程式資料庫的屬性，例如資料庫超時</span><span class="sxs-lookup"><span data-stu-id="1360f-271">Get and set properties of the Reporting Servicea application database, for example database timeout</span></span>  
 <span data-ttu-id="1360f-272">下列範例一開始傳回資料庫與屬性的清單，您可以用來決定之後提供給 set 命令的資料庫 GUID (識別碼)。</span><span class="sxs-lookup"><span data-stu-id="1360f-272">The following example first returns a list of the databases and properties so you can determine the database guid (ID) that you then supply to the set command.</span></span> <span data-ttu-id="1360f-273">如需屬性的完整清單，請使用 `Get-SPRSDatabase | format-list`。</span><span class="sxs-lookup"><span data-stu-id="1360f-273">For a full list of the properties, use `Get-SPRSDatabase | format-list`.</span></span>  
  
```powershell
Get-SPRSDatabase | Select id, querytimeout,connectiontimeout, status, server, ServiceInstance
```  
  
 <span data-ttu-id="1360f-274">以下是輸出的範例。</span><span class="sxs-lookup"><span data-stu-id="1360f-274">The following is an example of the output.</span></span> <span data-ttu-id="1360f-275">決定您要修改之資料庫的識別碼，並在 SET Cmdlet 中使用該識別碼。</span><span class="sxs-lookup"><span data-stu-id="1360f-275">Determine the ID for the database you want to modify and use the ID in the SET cmdlet.</span></span>  
  
-   `Id                : 56f8d1bc-cb04-44cf-bd41-a873643c5a14`  
  
     `QueryTimeout      : 120`  
  
     `ConnectionTimeout : 15`  
  
     `Status            : Online`  
  
     `Server            : SPServer Name=uetestb01`  
  
     `ServiceInstance   : SPDatabaseServiceInstance`  
  
```powershell
Set-SPRSDatabase -Identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 -QueryTimeout 300  
```  
  
 <span data-ttu-id="1360f-276">若要確認是否已設定值，請再執行一次 GET Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="1360f-276">To verify the value is set, run the GET cmdlet again.</span></span>  
  
```powershell
Get-SPRSDatabase -Identity 56f8d1bc-cb04-44cf-bd41-a873643c5a14 | Select id, querytimeout,connectiontimeout, status, server, ServiceInstance  
```  
  
###  <a name="list-reporting-services-data-extensions---sharepoint-mode"></a><a name="bkmk_example_list_data_extensions"></a><span data-ttu-id="1360f-277">列出 reporting services 資料延伸模組-SharePoint 模式</span><span class="sxs-lookup"><span data-stu-id="1360f-277">List reporting services data extensions - SharePoint mode</span></span>  
 <span data-ttu-id="1360f-278">下列範例會在每一個 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] 服務應用程式中執行迴圈，並列出每一個應用程式目前的資料延伸模組。</span><span class="sxs-lookup"><span data-stu-id="1360f-278">The following example loops through each [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] service application and lists the current data extensions for each.</span></span>  
  
```powershell
$apps = Get-SPRSServiceApplication  
foreach ($app in $apps)
{  
Write-host -ForegroundColor "yellow" Service App Name $app.Name  
Get-SPRSExtension -identity $app -ExtensionType "Data" | select name, extensiontype | Format-Table -AutoSize  
}  
```  
  
 <span data-ttu-id="1360f-279">**範例輸出︰**</span><span class="sxs-lookup"><span data-stu-id="1360f-279">**Example output:**</span></span>  
  
-   `Name           ExtensionType`  
  
     `----           -------------`  
  
     `SQL                     Data`  
  
     `SQLAZURE                Data`  
  
     `SQLPDW                  Data`  
  
     `OLEDB                   Data`  
  
     `OLEDB-MD                Data`  
  
     `ORACLE                  Data`  
  
     `ODBC                    Data`  
  
     `XML                     Data`  
  
     `SHAREPOINTLIST          Data`  
  
###  <a name="change-and-list-subscription-owners"></a><a name="bkmk_change_subscription_owner"></a><span data-ttu-id="1360f-280">變更和列出訂用帳戶擁有者</span><span class="sxs-lookup"><span data-stu-id="1360f-280">Change and list subscription owners</span></span>  
 <span data-ttu-id="1360f-281">請參閱 [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="1360f-281">See [Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1360f-282">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1360f-282">See Also</span></span>  
 <span data-ttu-id="1360f-283">[使用 PowerShell 來變更和列出 Reporting Services 訂用帳戶擁有者並執行訂用帳戶](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md) </span><span class="sxs-lookup"><span data-stu-id="1360f-283">[Use PowerShell to Change and List Reporting Services Subscription Owners and Run a Subscription](subscriptions/manage-subscription-owners-and-run-subscription-powershell.md) </span></span>  
 <span data-ttu-id="1360f-284">[檢查清單：使用 PowerShell 驗證 PowerPivot for SharePoint](https://docs.microsoft.com/analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint) </span><span class="sxs-lookup"><span data-stu-id="1360f-284">[CheckList: Use PowerShell to Verify PowerPivot for SharePoint](https://docs.microsoft.com/analysis-services/instances/install-windows/checklist-use-powershell-to-verify-power-pivot-for-sharepoint) </span></span>  
 [<span data-ttu-id="1360f-285">CodePlex SharePoint Management PowerShell 指令碼</span><span class="sxs-lookup"><span data-stu-id="1360f-285">CodePlex SharePoint Management PowerShell scripts</span></span>](https://sharepointpsscripts.codeplex.com/)   
