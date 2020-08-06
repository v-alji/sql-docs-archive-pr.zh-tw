---
title: 從命令提示字元安裝 PowerPivot |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 7f1f2b28-c9f5-49ad-934b-02f2fa6b9328
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 54f30142cdc2e39b3ec565d4f965fdad675405e4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606028"
---
# <a name="install-powerpivot-from-the-command-prompt"></a><span data-ttu-id="d24f5-102">從命令提示字元安裝 PowerPivot</span><span class="sxs-lookup"><span data-stu-id="d24f5-102">Install PowerPivot from the Command Prompt</span></span>
  <span data-ttu-id="d24f5-103">您可以從命令列執行安裝程式來安裝 SQL Server PowerPivot for SharePoint。</span><span class="sxs-lookup"><span data-stu-id="d24f5-103">You can run Setup from the command line to install SQL Server PowerPivot for SharePoint.</span></span> <span data-ttu-id="d24f5-104">您可以在命令中包含 `/ROLE` 參數並排除 `/FEATURES` 參數。</span><span class="sxs-lookup"><span data-stu-id="d24f5-104">You must include the `/ROLE` parameter in your command and exclude the `/FEATURES` parameter.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d24f5-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="d24f5-105">Prerequisites</span></span>  
 <span data-ttu-id="d24f5-106">您必須安裝 SharePoint Server 2010 Enterprise Edition Service Pack 1 (SP1)。</span><span class="sxs-lookup"><span data-stu-id="d24f5-106">SharePoint Server 2010 enterprise edition with Service Pack 1 (SP1) must be installed.</span></span>  
  
 <span data-ttu-id="d24f5-107">您必須使用網域帳戶佈建 Analysis Services。</span><span class="sxs-lookup"><span data-stu-id="d24f5-107">You must use domain accounts to provision Analysis Services.</span></span>  
  
 <span data-ttu-id="d24f5-108">電腦必須聯結至與 SharePoint 伺服器陣列相同的網域。</span><span class="sxs-lookup"><span data-stu-id="d24f5-108">The computer must be joined to the same domain as the SharePoint farm.</span></span>  
  
##  <a name="role-based-installation-options"></a><a name="Commands"></a><span data-ttu-id="d24f5-109">以/ROLE 為基礎的安裝選項</span><span class="sxs-lookup"><span data-stu-id="d24f5-109">/ROLE based installation options</span></span>  
 <span data-ttu-id="d24f5-110">在 PowerPivot for SharePoint 部署中，會使用 `/ROLE` 參數取代 `/FEATURES` 參數。</span><span class="sxs-lookup"><span data-stu-id="d24f5-110">For PowerPivot for SharePoint deployments, the `/ROLE` parameter is used in place of the `/FEATURES` parameter.</span></span> <span data-ttu-id="d24f5-111">有效值包括：</span><span class="sxs-lookup"><span data-stu-id="d24f5-111">Valid values include:</span></span>  
  
-   `SPI_AS_ExistingFarm`  
  
-   `SPI_AS_NewFarm`  
  
 <span data-ttu-id="d24f5-112">兩個角色都會安裝應用程式、組態和部署檔案，好讓 PowerPivot for SharePoint 在 SharePoint 伺服器陣列中執行。</span><span class="sxs-lookup"><span data-stu-id="d24f5-112">Both roles install application, configuration, and deployment files that enable a PowerPivot for SharePoint to run in a SharePoint farm.</span></span> <span data-ttu-id="d24f5-113">指定任一個角色將會使得安裝程式檢查 SharePoint 整合所需的硬體和軟體需求。</span><span class="sxs-lookup"><span data-stu-id="d24f5-113">Specifying either role will cause Setup to check for hardware and software requirements necessary for SharePoint integration.</span></span>  
  
 <span data-ttu-id="d24f5-114">現有的伺服器陣列選項假設已具有 SharePoint 伺服器陣列。</span><span class="sxs-lookup"><span data-stu-id="d24f5-114">The existing farm option assumes that a SharePoint farm is already in place.</span></span> <span data-ttu-id="d24f5-115">[新增伺服器陣列] 選項會假設您將建立新的伺服器陣列;它支援在命令列語法中加入資料庫引擎實例，讓您可以使用資料庫引擎實例作為伺服器陣列的資料庫伺服器。</span><span class="sxs-lookup"><span data-stu-id="d24f5-115">The new farm option assumes that you will create a new farm; it supports the addition of a Database Engine instance in the command line syntax so that you can use the Database Engine instance as the farm's database server.</span></span>  
  
 <span data-ttu-id="d24f5-116">相對於舊版，所有伺服器組態工作會以後續安裝工作來執行。</span><span class="sxs-lookup"><span data-stu-id="d24f5-116">In contrast with the previous releases, all server configuration tasks are performed as post-installation tasks.</span></span> <span data-ttu-id="d24f5-117">如果您想自動化安裝和組態步驟，您可以使用 PowerShell 設定伺服器。</span><span class="sxs-lookup"><span data-stu-id="d24f5-117">If you are automating installation and configuration steps, you can use PowerShell to configure the server.</span></span> <span data-ttu-id="d24f5-118">如需詳細資訊，請參閱[使用 Windows PowerShell 的 PowerPivot](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell)設定。</span><span class="sxs-lookup"><span data-stu-id="d24f5-118">For more information, see [PowerPivot Configuration using Windows PowerShell](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-configuration-using-windows-powershell).</span></span>  
  
## <a name="example-commands"></a><span data-ttu-id="d24f5-119">範例命令</span><span class="sxs-lookup"><span data-stu-id="d24f5-119">Example Commands</span></span>  
 <span data-ttu-id="d24f5-120">下列範例說明每個選項的用法。</span><span class="sxs-lookup"><span data-stu-id="d24f5-120">The following examples illustrate the usage of each option.</span></span> <span data-ttu-id="d24f5-121">範例1顯示 `SPI_AS_ExistingFarm` 。</span><span class="sxs-lookup"><span data-stu-id="d24f5-121">Example 1 shows `SPI_AS_ExistingFarm`.</span></span>  
  
```cmd
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
 <span data-ttu-id="d24f5-122">範例 2 顯示 `SPI_AS_NewFarm`。</span><span class="sxs-lookup"><span data-stu-id="d24f5-122">Example 2 shows `SPI_AS_NewFarm`.</span></span> <span data-ttu-id="d24f5-123">請注意，此範例包含佈建 Database Engine 的參數。</span><span class="sxs-lookup"><span data-stu-id="d24f5-123">Notice that it includes parameters for provisioning the Database Engine.</span></span>  
  
```cmd
Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_NewFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/SQLSVCACCOUNT=<DomainName\UserName> /SQLSVCPASSWORD=<StrongPassword> /SQLSYSADMINACCOUNTS=<DomainName\UserName> /AGTSVCACCOUNT=<DomainName\UserName> /AGTSVCPASSWORD=<StrongPassword> /ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
```  
  
##  <a name="modifying-the-command-syntax"></a><a name="Join"></a><span data-ttu-id="d24f5-124">修改命令語法</span><span class="sxs-lookup"><span data-stu-id="d24f5-124">Modifying the command syntax</span></span>  
 <span data-ttu-id="d24f5-125">使用下列步驟可修改範例命令語法。</span><span class="sxs-lookup"><span data-stu-id="d24f5-125">Use the following steps to modify the example command syntax.</span></span>  
  
1.  <span data-ttu-id="d24f5-126">將下列命令複製到 [記事本] 中：</span><span class="sxs-lookup"><span data-stu-id="d24f5-126">Copy the following command into Notepad:</span></span>  
  
    ```cmd
    Setup.exe /q /IAcceptSQLServerLicenseTerms /ACTION=install /ROLE=SPI_AS_ExistingFarm /INSTANCENAME=PowerPivot /INDICATEPROGRESS/ASSVCACCOUNT=<DomainName\UserName> /ASSVCPASSWORD=<StrongPassword> /ASSYSADMINACCOUNTS=<DomainName\UserName>   
    ```  
  
     <span data-ttu-id="d24f5-127">`/q` 參數會以無訊息模式執行安裝程式，這樣會隱藏使用者介面。</span><span class="sxs-lookup"><span data-stu-id="d24f5-127">The `/q` parameter runs Setup in quiet mode, which suppresses the user interface.</span></span>  
  
     <span data-ttu-id="d24f5-128">當針對自動安裝指定了 `/IAcceptSQLServerLicenseTerms` 或 `/q` 參數時，將需要 `/qs`。</span><span class="sxs-lookup"><span data-stu-id="d24f5-128">The `/IAcceptSQLServerLicenseTerms` is required when the `/q` or `/qs` parameter is specified for un-attended installations.</span></span>  
  
     <span data-ttu-id="d24f5-129">`/action` 參數會指示安裝程式執行安裝。</span><span class="sxs-lookup"><span data-stu-id="d24f5-129">The `/action` parameter instructs Setup to perform an installation.</span></span>  
  
     <span data-ttu-id="d24f5-130">`/role` 參數會指示安裝程式安裝 PowerPivot for SharePoint 所需的 Analysis Services 程式和組態檔。</span><span class="sxs-lookup"><span data-stu-id="d24f5-130">The `/role` parameter instructs Setup to install the Analysis Services program and configuration files required for PowerPivot for SharePoint.</span></span> <span data-ttu-id="d24f5-131">這個角色也會偵測及使用現有的伺服器陣列連接資訊，以存取 SharePoint 組態資料庫。</span><span class="sxs-lookup"><span data-stu-id="d24f5-131">This role also detects and uses the existing farm connectivity information to access the SharePoint configuration database.</span></span> <span data-ttu-id="d24f5-132">此為必要參數。</span><span class="sxs-lookup"><span data-stu-id="d24f5-132">This parameter is required.</span></span> <span data-ttu-id="d24f5-133">若要指定要安裝的元件，請使用這個參數，而非 `/features` 參數。</span><span class="sxs-lookup"><span data-stu-id="d24f5-133">Use it instead of the `/features` parameter to specify the components to install.</span></span>  
  
     <span data-ttu-id="d24f5-134">`/instancename` 參數會將 'PowerPivot' 指定為具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="d24f5-134">The `/instancename` parameter specifies 'PowerPivot' as a named instance.</span></span> <span data-ttu-id="d24f5-135">這個值為硬式編碼，無法變更。</span><span class="sxs-lookup"><span data-stu-id="d24f5-135">This value is hard-coded and cannot be changed.</span></span> <span data-ttu-id="d24f5-136">在命令中指定這個值是為了教育使用者，好讓使用者知道如何安裝此服務。</span><span class="sxs-lookup"><span data-stu-id="d24f5-136">It is specified in the command for educational purposes so that you know how the service is installed.</span></span>  
  
     <span data-ttu-id="d24f5-137">`/indicateprogress` 參數可讓您在命令提示字元視窗中監視進度。</span><span class="sxs-lookup"><span data-stu-id="d24f5-137">The `/indicateprogress` parameter allows you to monitor progress in the command prompt window.</span></span>  
  
2.  <span data-ttu-id="d24f5-138">此命令會略過 `PID` 參數，這樣會造成 Evaluation Edition 的安裝。</span><span class="sxs-lookup"><span data-stu-id="d24f5-138">The `PID` parameter is omitted from the command, which causes the Evaluation edition to be installed.</span></span> <span data-ttu-id="d24f5-139">如果您想要安裝 Enterprise Edition，請將 PID 加入至安裝程式命令，並提供有效的產品金鑰。</span><span class="sxs-lookup"><span data-stu-id="d24f5-139">If you want to install the Enterprise edition, add the PID to your Setup command and provide a valid product key.</span></span>  
  
    ```  
    /PID=<product key for an Enterprise installation>  
    ```  
  
3.  <span data-ttu-id="d24f5-140">\<domain\username> \<StrongPassword> 以有效的使用者帳戶和密碼取代和的預留位置。</span><span class="sxs-lookup"><span data-stu-id="d24f5-140">Replace the placeholders for \<domain\username> and \<StrongPassword>with valid user accounts and passwords.</span></span>  
  
     <span data-ttu-id="d24f5-141">`/assvaccount`和 **/assvcpassword**參數是用來設定 [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] 應用程式伺服器上的實例。</span><span class="sxs-lookup"><span data-stu-id="d24f5-141">The `/assvaccount` and **/assvcpassword** parameters are used to configure the [!INCLUDE[ssGeminiSrv](../../includes/ssgeminisrv-md.md)] instance on the application server.</span></span> <span data-ttu-id="d24f5-142">請以有效的帳戶資訊取代這些預留位置。</span><span class="sxs-lookup"><span data-stu-id="d24f5-142">Replace these placeholders with valid account information.</span></span>  
  
     <span data-ttu-id="d24f5-143">**/Assysadminaccounts**參數必須設定為正在執行 SQL Server 安裝程式之使用者的身分識別。</span><span class="sxs-lookup"><span data-stu-id="d24f5-143">The **/assysadminaccounts** parameter must be set to the identity of the user who is running SQL Server Setup.</span></span> <span data-ttu-id="d24f5-144">您至少必須指定一個系統管理員。</span><span class="sxs-lookup"><span data-stu-id="d24f5-144">You must specify at least one system administrator.</span></span> <span data-ttu-id="d24f5-145">請注意，SQL Server 安裝程式不再授與自動系統管理員 (sysadmin) 權限給內建系統管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="d24f5-145">Note that SQL Server Setup no long grants automatic sysadmin permissions to members of the built-in Administrators group.</span></span>  
  
4.  <span data-ttu-id="d24f5-146">移除分行符號。</span><span class="sxs-lookup"><span data-stu-id="d24f5-146">Remove line breaks.</span></span>  
  
5.  <span data-ttu-id="d24f5-147">選取整個命令，然後按一下 [編輯] 功能表上的 [**複製**]。</span><span class="sxs-lookup"><span data-stu-id="d24f5-147">Select the entire command and then click **Copy** on the Edit menu.</span></span>  
  
6.  <span data-ttu-id="d24f5-148">開啟系統管理員命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="d24f5-148">Open an administrator command prompt.</span></span> <span data-ttu-id="d24f5-149">若要這樣做，請按一下 [**開始**]，以滑鼠右鍵按一下命令提示字元，然後選取 [以**系統管理員身分執行**]。</span><span class="sxs-lookup"><span data-stu-id="d24f5-149">To do this, click **Start**, right-click the command prompt, and select **Run as administrator**.</span></span>  
  
7.  <span data-ttu-id="d24f5-150">導覽至包含 SQL Server 安裝媒體的磁碟機或共用資料夾。</span><span class="sxs-lookup"><span data-stu-id="d24f5-150">Navigate to the drive or shared folder that contains the SQL Server installation media.</span></span>  
  
8.  <span data-ttu-id="d24f5-151">將修改過的命令貼到命令列。</span><span class="sxs-lookup"><span data-stu-id="d24f5-151">Paste the revised command into the command line.</span></span> <span data-ttu-id="d24f5-152">若要這麼做，請按一下 [命令提示字元] 視窗左上角的圖示，指向 [**編輯**]，然後按一下 [**貼**上]。</span><span class="sxs-lookup"><span data-stu-id="d24f5-152">To do this, click the icon in the top left corner of the command prompt window, point to **Edit**, and then click **Paste**.</span></span>  
  
9. <span data-ttu-id="d24f5-153">按**enter**鍵以執行命令。</span><span class="sxs-lookup"><span data-stu-id="d24f5-153">Press **Enter** to run the command.</span></span> <span data-ttu-id="d24f5-154">等候安裝程式完成。</span><span class="sxs-lookup"><span data-stu-id="d24f5-154">Wait for setup to complete.</span></span> <span data-ttu-id="d24f5-155">您可以在命令提示字元視窗中監視安裝程式的進度。</span><span class="sxs-lookup"><span data-stu-id="d24f5-155">You can monitor Setup's progress in the command prompt window.</span></span>  
  
10. <span data-ttu-id="d24f5-156">若要驗證安裝，請檢查位於 \Program Files\SQL Server\120\Setup Bootstrap\Log 的 summary.txt 檔。</span><span class="sxs-lookup"><span data-stu-id="d24f5-156">To verify installation, check the summary.txt file at \Program Files\SQL Server\120\Setup Bootstrap\Log.</span></span> <span data-ttu-id="d24f5-157">如果伺服器安裝成功而沒有任何錯誤，最終的結果應該是 "Passed"。</span><span class="sxs-lookup"><span data-stu-id="d24f5-157">Final result should say "Passed" if the server installed without errors.</span></span>  
  
11. <span data-ttu-id="d24f5-158">設定伺服器。</span><span class="sxs-lookup"><span data-stu-id="d24f5-158">Configure the server.</span></span> <span data-ttu-id="d24f5-159">您至少必須要部署方案、建立服務應用程式，並針對每一個網站集合啟用此功能。</span><span class="sxs-lookup"><span data-stu-id="d24f5-159">At a minimum, you must deploy solutions, create a service application, and enable the feature for each site collection.</span></span> <span data-ttu-id="d24f5-160">如需詳細資訊，請參閱[設定或修復 PowerPivot for SharePoint 2010 &#40;PowerPivot 設定工具&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md)或 [[管理中心] 中的 powerpivot 伺服器管理和](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration)設定。</span><span class="sxs-lookup"><span data-stu-id="d24f5-160">For more information, see [Configure or Repair PowerPivot for SharePoint 2010 &#40;PowerPivot Configuration Tool&#41;](../../../2014/analysis-services/configure-repair-powerpivot-sharepoint-2010.md) or [PowerPivot Server Administration and Configuration in Central Administration](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/power-pivot-server-administration-and-configuration-in-central-administration).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d24f5-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d24f5-161">See Also</span></span>  
 <span data-ttu-id="d24f5-162">[設定 PowerPivot 服務帳戶](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts) </span><span class="sxs-lookup"><span data-stu-id="d24f5-162">[Configure PowerPivot Service Accounts](https://docs.microsoft.com/analysis-services/power-pivot-sharepoint/configure-power-pivot-service-accounts) </span></span>  
 [<span data-ttu-id="d24f5-163">PowerPivot for SharePoint 2010 安裝</span><span class="sxs-lookup"><span data-stu-id="d24f5-163">PowerPivot for SharePoint 2010 Installation</span></span>](../../../2014/sql-server/install/powerpivot-for-sharepoint-2010-installation.md)  
