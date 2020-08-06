---
title: 步驟 2：執行套件安裝精靈 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: f91fbb89-4626-4c47-b96d-56052dc45861
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9492f9ecc843ef475a3c5d32cde2952e0ff498fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687051"
---
# <a name="step-2-running-the-package-installation-wizard"></a><span data-ttu-id="2d747-102">步驟 2:執行封裝安裝精靈</span><span class="sxs-lookup"><span data-stu-id="2d747-102">Step 2: Running the Package Installation Wizard</span></span>
  <span data-ttu-id="2d747-103">在這項工作中，您會執行「封裝安裝精靈」，將「部署教學課程」專案中的封裝部署到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的執行個體上。</span><span class="sxs-lookup"><span data-stu-id="2d747-103">In this task, you will run the Package Installation Wizard to deploy the packages from the Deployment Tutorial project to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="2d747-104">只有封裝可以安裝在 msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫的 sysssispackages 資料表中，部署配套所包含的支援檔案則會部署到檔案系統中。</span><span class="sxs-lookup"><span data-stu-id="2d747-104">Only packages can be installed in the sysssispackages table in the msdb [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database, the supporting files that the deployment bundle includes will be deployed to the file system.</span></span>  
  
 <span data-ttu-id="2d747-105">「封裝安裝精靈」會引導您完成安裝和設定封裝的步驟。</span><span class="sxs-lookup"><span data-stu-id="2d747-105">The Package Installation Wizard will guide you through the steps to install and configure the packages.</span></span> <span data-ttu-id="2d747-106">您會將封裝安裝到目的地電腦 (即複製部署配套所使用的電腦) 上的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體中。</span><span class="sxs-lookup"><span data-stu-id="2d747-106">You will install the packages to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] on the destination computer (the computer to which you copied the deployment bundle.</span></span> <span data-ttu-id="2d747-107">此外，您還會建立一個 C:\DeploymentTutorialInstall 資料夾，讓精靈用來安裝非封裝檔案。</span><span class="sxs-lookup"><span data-stu-id="2d747-107">You will also create a folder, C:\DeploymentTutorialInstall, in which the wizard will install the non-package files.</span></span>  
  
 <span data-ttu-id="2d747-108">在先前的課程中，您已將教學課程中的封裝修改為使用組態。</span><span class="sxs-lookup"><span data-stu-id="2d747-108">In an earlier lesson, you modified the packages in the tutorial to use configurations.</span></span> <span data-ttu-id="2d747-109">因此，您將會使用「封裝安裝精靈」編輯這些組態，讓封裝能夠在安裝的目標環境中順利執行。</span><span class="sxs-lookup"><span data-stu-id="2d747-109">Using the Package Installation Wizard, you will edit these configurations to enable packages to run successfully in the installed-to environment.</span></span>  
  
### <a name="to-install-the-packages"></a><span data-ttu-id="2d747-110">若要安裝封裝</span><span class="sxs-lookup"><span data-stu-id="2d747-110">To install the packages</span></span>  
  
1.  <span data-ttu-id="2d747-111">在目的地電腦上，找到部署配套。</span><span class="sxs-lookup"><span data-stu-id="2d747-111">On the destination computer, locate the deployment bundle.</span></span>  
  
     <span data-ttu-id="2d747-112">如果您使用預設值 (bin\Deployment) 作為部署公用程式的位置，則部署配套就是「部署教學課程」專案中的 [Deployment] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="2d747-112">If you used the default value-bin\Deployment-as the location of the deployment utility, the deployment bundle is the Deployment folder in the Deployment Tutorial project.</span></span>  
  
2.  <span data-ttu-id="2d747-113">在 [Deployment] 資料夾中，按兩下資訊清單檔 Deployment Tutorial.SSISDeploymentManifest。</span><span class="sxs-lookup"><span data-stu-id="2d747-113">In the Deployment folder, double-click the manifest file, Deployment Tutorial.SSISDeploymentManifest.</span></span>  
  
3.  <span data-ttu-id="2d747-114">在 [封裝安裝精靈] 的 [歡迎使用] 頁面上，按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="2d747-114">On the Welcome page of the Package Installation Wizard, click **Next**.</span></span>  
  
4.  <span data-ttu-id="2d747-115">在 [部署 SSIS 封裝] 頁面上，選取 [SQL Server 部署]  選項，再選取 [安裝之後驗證封裝]  核取方塊，然後按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="2d747-115">On the Deploy SSIS Packages page, select the **SQL Server deployment** option, select the **Validate packages after installation** check box, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="2d747-116">在 [指定目標 SQL Server] 頁面上的 [伺服器名稱] 方塊中，指定 **(local)** 。</span><span class="sxs-lookup"><span data-stu-id="2d747-116">On the Specify Target SQL Server page, specify **(local**), in the **Server name** box.</span></span>  
  
6.  <span data-ttu-id="2d747-117">如果 SQL Server 的執行個體支援 Windows 驗證，請選取 [使用 Windows 驗證]  ，否則請選取 [使用 SQL Server 驗證]  並提供使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="2d747-117">If the instance of SQL Server supports Windows Authentication, select **Use Windows Authentication**; otherwise, select **Use SQL Server Authentication** and provide a user name and a password.</span></span>  
  
7.  <span data-ttu-id="2d747-118">確認已清除 [依賴伺服器儲存體進行加密]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="2d747-118">Verify that the **Rely on server storage for encryption** check box is cleared.</span></span>  
  
8.  <span data-ttu-id="2d747-119">按 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="2d747-119">Click **Next.**</span></span>  
  
9. <span data-ttu-id="2d747-120">在 [選取安裝資料夾] 頁面上，按一下 [瀏覽]  。</span><span class="sxs-lookup"><span data-stu-id="2d747-120">On the Select Installation Folder page, click **Browse.**</span></span>  
  
10. <span data-ttu-id="2d747-121">在 [瀏覽資料夾]  對話方塊中，展開 [我的電腦]  ，然後按一下 [本機磁碟 (C:)]  。</span><span class="sxs-lookup"><span data-stu-id="2d747-121">In the **Browse For Folder** dialog box, expand **My Computer** and then click **Local Disk (C:)**.</span></span>  
  
11. <span data-ttu-id="2d747-122">按一下 [建立新資料夾]，並且以 **DeploymentTutorialInstall** 取代新資料夾的**新增資料夾**預設名稱。</span><span class="sxs-lookup"><span data-stu-id="2d747-122">Click **Make New Folder** and replace the default name of the new folder, **New Folder**, with **DeploymentTutorialInstall**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="2d747-123">在組態使用的環境變數值中會參考這個名稱，</span><span class="sxs-lookup"><span data-stu-id="2d747-123">This name is referenced in the value of the environment variables that configurations use.</span></span> <span data-ttu-id="2d747-124">因此資料夾和參考的名稱必須相符，否則封裝無法執行。</span><span class="sxs-lookup"><span data-stu-id="2d747-124">The name of the folder and the reference must match or the package cannot run.</span></span>  
  
12. <span data-ttu-id="2d747-125">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="2d747-125">Click **OK**.</span></span>  
  
13. <span data-ttu-id="2d747-126">在 [選取安裝資料夾] 頁面上，確認 [資料夾] 方塊中包含的是 **C:\DeploymentTutorialInstall**，然後按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="2d747-126">On the Select Installation Folder page, verify that the Folder box contains **C:\DeploymentTutorialInstall** and then click **Next**.</span></span>  
  
14. <span data-ttu-id="2d747-127">在 [確認安裝] 頁面上，按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="2d747-127">On the Confirm Installation page, click **Next**.</span></span>  
  
     <span data-ttu-id="2d747-128">精靈便會安裝封裝。</span><span class="sxs-lookup"><span data-stu-id="2d747-128">The wizard installs the packages.</span></span> <span data-ttu-id="2d747-129">當安裝完成之後，[設定封裝] 頁面隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="2d747-129">After installation is completed, the Configure Packages page opens.</span></span>  
  
15. <span data-ttu-id="2d747-130">在 [設定封裝] 頁面上，確認 [設定檔]  方塊中有列出 datatransferconfig.dtsconfig 和 loadxmldataconfig.dtsconfig。</span><span class="sxs-lookup"><span data-stu-id="2d747-130">On the Configure Packages page, verify that the **Configuration file** box lists datatransferconfig.dtsconfig and loadxmldataconfig.dtsconfig.</span></span>  
  
16. <span data-ttu-id="2d747-131">在 [設定檔]  清單中，按一下 **datatransferconfig.dtsconfig**、展開 [設定]  方塊中 [路徑]  資料行的 [屬性]，並以下列值更新 [值]  資料行：</span><span class="sxs-lookup"><span data-stu-id="2d747-131">In the **Configuration file** list, click **datatransferconfig.dtsconfig**, expand Property in the **Path** column of the **Configurations** box, and update the **Value** column with the following values:</span></span>  
  
    |<span data-ttu-id="2d747-132">屬性</span><span class="sxs-lookup"><span data-stu-id="2d747-132">Property</span></span>|<span data-ttu-id="2d747-133">值</span><span class="sxs-lookup"><span data-stu-id="2d747-133">Value</span></span>|<span data-ttu-id="2d747-134">更新的值</span><span class="sxs-lookup"><span data-stu-id="2d747-134">Updated Value</span></span>|  
    |--------------|-----------|-------------------|  
    |<span data-ttu-id="2d747-135">\Package.Connections[Deployment Tutorial Log].Properties[ConnectionString]</span><span class="sxs-lookup"><span data-stu-id="2d747-135">\Package.Connections[Deployment Tutorial Log].Properties[ConnectionString]</span></span>|<span data-ttu-id="2d747-136">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages\Deployment Tutorial Log</span><span class="sxs-lookup"><span data-stu-id="2d747-136">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Completed Packages\Deployment Tutorial Log</span></span>|<span data-ttu-id="2d747-137">C:\DeploymentTutorialInstall\Deployment Tutorial Log</span><span class="sxs-lookup"><span data-stu-id="2d747-137">C:\DeploymentTutorialInstall\Deployment Tutorial Log</span></span>|  
    |<span data-ttu-id="2d747-138">\Package.Connections[NewCustomers].Properties[ConnectionString]</span><span class="sxs-lookup"><span data-stu-id="2d747-138">\Package.Connections[NewCustomers].Properties[ConnectionString]</span></span>|<span data-ttu-id="2d747-139">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\NewCustomers.txt</span><span class="sxs-lookup"><span data-stu-id="2d747-139">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\NewCustomers.txt</span></span>|<span data-ttu-id="2d747-140">C:\DeploymentTutorialInstall\NewCustomers.txt</span><span class="sxs-lookup"><span data-stu-id="2d747-140">C:\DeploymentTutorialInstall\NewCustomers.txt</span></span>|  
  
17. <span data-ttu-id="2d747-141">在 [設定檔]  清單中，按一下 loadxmldataconfig.dtsconfig、展開 [設定]  方塊中 [路徑]  資料行的 [屬性]，並以下列值更新 [值]  資料行：</span><span class="sxs-lookup"><span data-stu-id="2d747-141">In the **Configuration file** list, click loadxmldataconfig.dtsconfig, expand Property in the **Path** column of the **Configurations** box, and update the **Value** column with the following values:</span></span>  
  
    |<span data-ttu-id="2d747-142">屬性</span><span class="sxs-lookup"><span data-stu-id="2d747-142">Property</span></span>|<span data-ttu-id="2d747-143">值</span><span class="sxs-lookup"><span data-stu-id="2d747-143">Value</span></span>|<span data-ttu-id="2d747-144">更新的值</span><span class="sxs-lookup"><span data-stu-id="2d747-144">Updated Value</span></span>|  
    |--------------|-----------|-------------------|  
    |<span data-ttu-id="2d747-145">\Package.LoadXMLData.Properties[[XML Source].[XMLData]]</span><span class="sxs-lookup"><span data-stu-id="2d747-145">\Package.LoadXMLData.Properties[[XML Source].[XMLData]]</span></span>|<span data-ttu-id="2d747-146">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xml</span><span class="sxs-lookup"><span data-stu-id="2d747-146">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xml</span></span>|<span data-ttu-id="2d747-147">C:\DeploymentTutorialInstall\orders.xml</span><span class="sxs-lookup"><span data-stu-id="2d747-147">C:\DeploymentTutorialInstall\orders.xml</span></span>|  
    |<span data-ttu-id="2d747-148">\Package.LoadXMLData.Properties[[XML Source].[XMLSchemaDefinition]]</span><span class="sxs-lookup"><span data-stu-id="2d747-148">\Package.LoadXMLData.Properties[[XML Source].[XMLSchemaDefinition]]</span></span>|<span data-ttu-id="2d747-149">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xsd</span><span class="sxs-lookup"><span data-stu-id="2d747-149">C:\Program Files\Microsoft SQL Server\100\Samples\Integration Services\Tutorial\Deploying Packages\Sample Data\orders.xsd</span></span>|<span data-ttu-id="2d747-150">C:\DeploymentTutorialInstall\orders.xsd</span><span class="sxs-lookup"><span data-stu-id="2d747-150">C:\DeploymentTutorialInstall\orders.xsd</span></span>|  
  
18. <span data-ttu-id="2d747-151">在 [封裝驗證] 頁面上，檢視所安裝之各個封裝的驗證結果，然後按一下 [下一步]  。</span><span class="sxs-lookup"><span data-stu-id="2d747-151">On the Package Validation page, view the validation results of each package installed and then click **Next**.</span></span>  
  
     <span data-ttu-id="2d747-152">由於目的地電腦上的環境變數值與開發電腦上的環境變數值不同，因此 [封裝驗證] 頁面上會出現一些警告。</span><span class="sxs-lookup"><span data-stu-id="2d747-152">Because the values of the environment variables on the destination computer differ from the values of the environment variables on the development computer, several warnings appear on the Package Validation page.</span></span> <span data-ttu-id="2d747-153">您應該會看到下列這四個警告：</span><span class="sxs-lookup"><span data-stu-id="2d747-153">You should expect four warnings:</span></span>  
  
    -   <span data-ttu-id="2d747-154">組態檔名稱 "C:\DeploymentTutorial\DataTransferConfig.dtsConfig" 無效。</span><span class="sxs-lookup"><span data-stu-id="2d747-154">The configuration file: "C:\DeploymentTutorial\DataTransferConfig.dtsConfig" is not valid.</span></span> <span data-ttu-id="2d747-155">請檢查組態檔名稱。</span><span class="sxs-lookup"><span data-stu-id="2d747-155">Check the configuration file name.</span></span>  
  
    -   <span data-ttu-id="2d747-156">無法載入封裝至少其中一個組態項目。</span><span class="sxs-lookup"><span data-stu-id="2d747-156">Failed to load at least one of the configuration entries in the package.</span></span> <span data-ttu-id="2d747-157">請檢查組態項目和之前的警告，查看哪個組態失敗的描述。</span><span class="sxs-lookup"><span data-stu-id="2d747-157">Check configuration entries and previous warnings to see description of which configuration failed.</span></span>  
  
    -   <span data-ttu-id="2d747-158">組態檔名稱 "C:\DeploymentTutorial\LoadXMLDataConfig.dtsConfig" 無效。</span><span class="sxs-lookup"><span data-stu-id="2d747-158">The configuration file: "C:\DeploymentTutorial\LoadXMLDataConfig.dtsConfig is not valid.</span></span> <span data-ttu-id="2d747-159">請檢查組態檔名稱。</span><span class="sxs-lookup"><span data-stu-id="2d747-159">Check the configuration file name.</span></span>  
  
    -   <span data-ttu-id="2d747-160">無法載入封裝至少其中一個組態項目。</span><span class="sxs-lookup"><span data-stu-id="2d747-160">Failed to load at least one of the configuration entries in the package.</span></span> <span data-ttu-id="2d747-161">請檢查組態項目和之前的警告，查看哪個組態失敗的描述。</span><span class="sxs-lookup"><span data-stu-id="2d747-161">Check configuration entries and previous warnings to see description of which configuration failed.</span></span>  
  
     <span data-ttu-id="2d747-162">這些警告並不會影響封裝安裝。</span><span class="sxs-lookup"><span data-stu-id="2d747-162">These warnings do not affect package installation.</span></span>  
  
     <span data-ttu-id="2d747-163">如果未選取 [部署 SSIS 封裝] 頁面上的 [安裝之後驗證封裝]  選項，則 [封裝驗證] 頁面就不會開啟，而且精靈不會顯示有關驗證的後續安裝資訊。</span><span class="sxs-lookup"><span data-stu-id="2d747-163">If you did not select the **Validate packages after installation** option on the Deploy SSIS Packages page, the Package Validation pages does not open and the wizard does not display post-installation information about validation.</span></span>  
  
19. <span data-ttu-id="2d747-164">閱讀 [完成封裝安裝精靈] 頁面上的安裝摘要，然後按一下 [完成]  。</span><span class="sxs-lookup"><span data-stu-id="2d747-164">On the Finish the Package Installation Wizard page, read the installation summary and then click **Finish**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2d747-165">暫存記錄檔是為了在封裝驗證中使用而建立的，</span><span class="sxs-lookup"><span data-stu-id="2d747-165">A temporary log file is created to use in the package validation.</span></span> <span data-ttu-id="2d747-166">執行封裝時，並不會使用這個檔案。</span><span class="sxs-lookup"><span data-stu-id="2d747-166">This file is not used when the package runs.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2d747-167">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="2d747-167">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2d747-168">步驟 3：測試部署的套件</span><span class="sxs-lookup"><span data-stu-id="2d747-168">Step 3: Testing the Deployed Packages</span></span>](../integration-services/lesson-3-3-testing-the-deployed-packages.md)  
  
<span data-ttu-id="2d747-169">![Integration Services 圖示 (小型) ](media/dts-16.gif "Integration Services 圖示 (小)")會**保持最**新狀態 Integration Services  </span><span class="sxs-lookup"><span data-stu-id="2d747-169">![Integration Services icon (small)](media/dts-16.gif "Integration Services icon (small)")  **Stay Up to Date with Integration Services**</span></span><br /> <span data-ttu-id="2d747-170">若要取得 Microsoft 的最新下載、文件、範例和影片以及社群中的精選解決方案，請瀏覽 MSDN 上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 頁面：</span><span class="sxs-lookup"><span data-stu-id="2d747-170">For the latest downloads, articles, samples, and videos from Microsoft, as well as selected solutions from the community, visit the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] page on MSDN:</span></span><br /><br /> [<span data-ttu-id="2d747-171">瀏覽 MSDN 上的 Integration Services 頁面</span><span class="sxs-lookup"><span data-stu-id="2d747-171">Visit the Integration Services page on MSDN</span></span>](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> <span data-ttu-id="2d747-172">若要得到這些更新的自動通知，請訂閱該頁面上所提供的 RSS 摘要。</span><span class="sxs-lookup"><span data-stu-id="2d747-172">For automatic notification of these updates, subscribe to the RSS feeds available on the page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d747-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d747-173">See Also</span></span>  
 <span data-ttu-id="2d747-174">[Integration Services 服務 &#40;SSIS 服務&#41;](service/integration-services-service-ssis-service.md) </span><span class="sxs-lookup"><span data-stu-id="2d747-174">[Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md) </span></span>  
 [<span data-ttu-id="2d747-175">管理 Integration Services 服務</span><span class="sxs-lookup"><span data-stu-id="2d747-175">Manage the Integration Services Service</span></span>](../../2014/integration-services/manage-the-integration-services-service.md)  
  
  
