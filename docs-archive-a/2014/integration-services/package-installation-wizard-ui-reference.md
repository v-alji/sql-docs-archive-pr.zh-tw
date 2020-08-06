---
title: 套件安裝精靈 UI 參考 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.deploymentwizard.confirminstallation.f1
- sql12.dts.deploymentwizard.deploydtspackages.f1
- sql12.dts.deploymentwizard.selectinstfolder.f1
- sql12.dts.deploymentwizard.specifytargetsqlserver.f1
- sql12.dts.deploymentwizard.welcome.f1
- sql12.dts.deploymentwizard.finish.f1
- sql12.dts.deploymentwizard.configurepackages.f1
- sql12.dts.deploymentwizard.packagevalidation.f1
helpviewer_keywords:
- Package Installer Wizard
ms.assetid: 6fca44d9-5001-4644-bcf3-c2d10a674b97
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c15b423c66891e799f7f8dcd27682036dce6d8de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688002"
---
# <a name="package-installation-wizard-ui-reference"></a><span data-ttu-id="62793-102">封裝安裝精靈 UI 參考</span><span class="sxs-lookup"><span data-stu-id="62793-102">Package Installation Wizard UI Reference</span></span>
  <span data-ttu-id="62793-103">使用 [封裝安裝精靈]  來部署 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案，包括其內含的封裝和其他檔案，以及任何封裝的相依性。</span><span class="sxs-lookup"><span data-stu-id="62793-103">Use the **Package Installation Wizard** to deploy a [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, including the packages and miscellaneous files it contains and any package dependencies.</span></span>  
  
 <span data-ttu-id="62793-104">在部署封裝之前，可以建立組態，然後將其隨封裝部署。</span><span class="sxs-lookup"><span data-stu-id="62793-104">Before you deploy packages, you can create configurations and then deploy them with the packages.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="62793-105">會使用組態，在執行階段以動態方式更新封裝及封裝物件的屬性。</span><span class="sxs-lookup"><span data-stu-id="62793-105">uses configurations to dynamically update properties of packages and package objects at run time.</span></span> <span data-ttu-id="62793-106">例如，OLE DB 連接的連接字串可提供對應值與包含連接字串屬性的組態，藉此於執行階段進行動態設定。</span><span class="sxs-lookup"><span data-stu-id="62793-106">For example, the connection string of an OLE DB connection can be set dynamically at run time by providing a configuration that maps a value to the property that contains the connection string.</span></span>  
  
 <span data-ttu-id="62793-107">您必須先建置 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案並建立部署公用程式，才能執行 [封裝安裝精靈]。</span><span class="sxs-lookup"><span data-stu-id="62793-107">You cannot run the Package Installation Wizard until you build an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project and create a deployment utility.</span></span> <span data-ttu-id="62793-108">如需詳細資訊，請參閱 [使用部署公用程式來部署封裝](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="62793-108">For more information, see [Deploy Packages by Using the Deployment Utility](../../2014/integration-services/deploy-packages-by-using-the-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="62793-109">下列章節描述精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="62793-109">The following sections describe pages of the wizard.</span></span>  
  
## <a name="welcome-to-the-package-installation-wizard-page"></a><span data-ttu-id="62793-110">歡迎使用封裝安裝精靈頁面</span><span class="sxs-lookup"><span data-stu-id="62793-110">Welcome to the Package Installation Wizard Page</span></span>  
 <span data-ttu-id="62793-111">使用 [封裝安裝精靈]  ，即可部署建立了封裝部署公用程式的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="62793-111">Use the **Package Installation Wizard** to deploy an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project for which you built a package deployment utility.</span></span>  
  
 <span data-ttu-id="62793-112">**不要再顯示此開始頁面**</span><span class="sxs-lookup"><span data-stu-id="62793-112">**Do not show this starting page again**</span></span>  
 <span data-ttu-id="62793-113">選取再次執行精靈時要略過開始頁面。</span><span class="sxs-lookup"><span data-stu-id="62793-113">Select to skip the starting page when you run the wizard again.</span></span>  
  
 <span data-ttu-id="62793-114">**下一個**</span><span class="sxs-lookup"><span data-stu-id="62793-114">**Next**</span></span>  
 <span data-ttu-id="62793-115">移至精靈的下一頁。</span><span class="sxs-lookup"><span data-stu-id="62793-115">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="62793-116">**[完成]**</span><span class="sxs-lookup"><span data-stu-id="62793-116">**Finish**</span></span>  
 <span data-ttu-id="62793-117">跳到 [完成封裝安裝精靈] 頁面。</span><span class="sxs-lookup"><span data-stu-id="62793-117">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="62793-118">如果您依序返回精靈的頁面以修訂您的選擇，並且指定了所有必要的選項，則請使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="62793-118">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all of the required options.</span></span>  
  
## <a name="configure-packages-page"></a><span data-ttu-id="62793-119">設定封裝頁面</span><span class="sxs-lookup"><span data-stu-id="62793-119">Configure Packages Page</span></span>  
 <span data-ttu-id="62793-120">使用 [設定封裝]  頁面即可編輯封裝組態。</span><span class="sxs-lookup"><span data-stu-id="62793-120">Use the **Configure Packages** page to edit package configurations.</span></span>  
  
### <a name="options"></a><span data-ttu-id="62793-121">選項。</span><span class="sxs-lookup"><span data-stu-id="62793-121">Options</span></span>  
 <span data-ttu-id="62793-122">**組態檔**</span><span class="sxs-lookup"><span data-stu-id="62793-122">**Configuration file**</span></span>  
 <span data-ttu-id="62793-123">從清單中選取檔案來編輯組態檔的內容。</span><span class="sxs-lookup"><span data-stu-id="62793-123">Edit the contents of a configuration file by selecting the file from the list.</span></span>  
  
 <span data-ttu-id="62793-124">**相關主題：** [建立套件設定](../../2014/integration-services/create-package-configurations.md)</span><span class="sxs-lookup"><span data-stu-id="62793-124">**Related Topics:** [Create Package Configurations](../../2014/integration-services/create-package-configurations.md)</span></span>  
  
 <span data-ttu-id="62793-125">**路徑**</span><span class="sxs-lookup"><span data-stu-id="62793-125">**Path**</span></span>  
 <span data-ttu-id="62793-126">檢視要設定之屬性的路徑。</span><span class="sxs-lookup"><span data-stu-id="62793-126">View the path of the property to be configured.</span></span>  
  
 <span data-ttu-id="62793-127">**型別**</span><span class="sxs-lookup"><span data-stu-id="62793-127">**Type**</span></span>  
 <span data-ttu-id="62793-128">檢視屬性的資料類型。</span><span class="sxs-lookup"><span data-stu-id="62793-128">View the data type of the property.</span></span>  
  
 <span data-ttu-id="62793-129">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="62793-129">**Value**</span></span>  
 <span data-ttu-id="62793-130">指定組態的值。</span><span class="sxs-lookup"><span data-stu-id="62793-130">Specify the value of the configuration.</span></span>  
  
 <span data-ttu-id="62793-131">**下一個**</span><span class="sxs-lookup"><span data-stu-id="62793-131">**Next**</span></span>  
 <span data-ttu-id="62793-132">移至精靈的下一頁。</span><span class="sxs-lookup"><span data-stu-id="62793-132">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="62793-133">**[完成]**</span><span class="sxs-lookup"><span data-stu-id="62793-133">**Finish**</span></span>  
 <span data-ttu-id="62793-134">跳到 [完成封裝安裝精靈] 頁面。</span><span class="sxs-lookup"><span data-stu-id="62793-134">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="62793-135">如果您依序返回精靈的頁面以修訂您的選擇，並且指定了所有必要的選項，則請使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="62793-135">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all of the required options.</span></span>  
  
## <a name="confirm-installation-page"></a><span data-ttu-id="62793-136">確認安裝頁面</span><span class="sxs-lookup"><span data-stu-id="62793-136">Confirm Installation Page</span></span>  
 <span data-ttu-id="62793-137">使用 [確認安裝]  頁面，即可開始安裝封裝、檢視狀態，以及檢視精靈用以從指定專案中安裝檔案的資訊。</span><span class="sxs-lookup"><span data-stu-id="62793-137">Use the **Confirm Installation** page to start the installation of packages, to view the status, and to view the information that the wizard will use to install files from the specified project.</span></span>  
  
 <span data-ttu-id="62793-138">**下一個**</span><span class="sxs-lookup"><span data-stu-id="62793-138">**Next**</span></span>  
 <span data-ttu-id="62793-139">安裝封裝及其相依檔案，並在安裝完成時移到下一個精靈頁面。</span><span class="sxs-lookup"><span data-stu-id="62793-139">Install the packages and their dependencies and go to the next wizard page when installation is completed.</span></span>  
  
 <span data-ttu-id="62793-140">**狀態**</span><span class="sxs-lookup"><span data-stu-id="62793-140">**Status**</span></span>  
 <span data-ttu-id="62793-141">顯示封裝安裝的進度。</span><span class="sxs-lookup"><span data-stu-id="62793-141">Shows the progress of the package installation.</span></span>  
  
 <span data-ttu-id="62793-142">**[完成]**</span><span class="sxs-lookup"><span data-stu-id="62793-142">**Finish**</span></span>  
 <span data-ttu-id="62793-143">移至 [完成封裝安裝精靈] 頁面。</span><span class="sxs-lookup"><span data-stu-id="62793-143">Go to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="62793-144">如果您有回到先前的精靈頁面來修改選擇，並且指定了所有必要的選項，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="62793-144">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all the required options.</span></span>  
  
## <a name="deploy-ssis-packages-page"></a><span data-ttu-id="62793-145">部署 SSIS 封裝頁面</span><span class="sxs-lookup"><span data-stu-id="62793-145">Deploy SSIS Packages Page</span></span>  
 <span data-ttu-id="62793-146">使用 [部署 SSIS 封裝]  頁面，來指定安裝 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝及其相依性的位置。</span><span class="sxs-lookup"><span data-stu-id="62793-146">Use the **Deploy SSIS Packages** page to specify where to install [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages and their dependencies.</span></span>  
  
### <a name="options"></a><span data-ttu-id="62793-147">選項。</span><span class="sxs-lookup"><span data-stu-id="62793-147">Options</span></span>  
 <span data-ttu-id="62793-148">**檔案系統部署**</span><span class="sxs-lookup"><span data-stu-id="62793-148">**File system deployment**</span></span>  
 <span data-ttu-id="62793-149">將封裝及相依性部署到檔案系統的指定資料夾中。</span><span class="sxs-lookup"><span data-stu-id="62793-149">Deploy packages and dependencies in a specified folder in the file system.</span></span>  
  
 <span data-ttu-id="62793-150">**SQL Server 部署**</span><span class="sxs-lookup"><span data-stu-id="62793-150">**SQL Server deployment**</span></span>  
 <span data-ttu-id="62793-151">將封裝及相依性部署到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]的執行個體中。</span><span class="sxs-lookup"><span data-stu-id="62793-151">Deploy packages and dependencies in an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="62793-152">如果 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 在伺服器之間共用封裝，請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="62793-152">Use this option if [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] shares packages between servers.</span></span> <span data-ttu-id="62793-153">所有的封裝相依性都會安裝到檔案系統的指定資料夾中。</span><span class="sxs-lookup"><span data-stu-id="62793-153">Any package dependencies are installed in the specified folder in the file system.</span></span>  
  
 <span data-ttu-id="62793-154">**安裝之後驗證封裝**</span><span class="sxs-lookup"><span data-stu-id="62793-154">**Validate packages after installation**</span></span>  
 <span data-ttu-id="62793-155">指出是否在安裝之後驗證封裝。</span><span class="sxs-lookup"><span data-stu-id="62793-155">Indicate whether to validate packages after installation.</span></span>  
  
 <span data-ttu-id="62793-156">**下一個**</span><span class="sxs-lookup"><span data-stu-id="62793-156">**Next**</span></span>  
 <span data-ttu-id="62793-157">移至精靈的下一頁。</span><span class="sxs-lookup"><span data-stu-id="62793-157">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="62793-158">**[完成]**</span><span class="sxs-lookup"><span data-stu-id="62793-158">**Finish**</span></span>  
 <span data-ttu-id="62793-159">跳到 [完成封裝安裝精靈] 頁面。</span><span class="sxs-lookup"><span data-stu-id="62793-159">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="62793-160">如果您依序返回精靈的頁面以修訂您的選擇，並且指定了所有必要的選項，則請使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="62793-160">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all of the required options.</span></span>  
  
## <a name="packages-validation-page"></a><span data-ttu-id="62793-161">封裝驗證頁面</span><span class="sxs-lookup"><span data-stu-id="62793-161">Packages Validation Page</span></span>  
 <span data-ttu-id="62793-162">使用 [封裝驗證]  頁面，即可檢視封裝驗證的進度與結果。</span><span class="sxs-lookup"><span data-stu-id="62793-162">Use the **Packages Validation** page to view the progress and results of the package validation.</span></span>  
  
 <span data-ttu-id="62793-163">**下一個**</span><span class="sxs-lookup"><span data-stu-id="62793-163">**Next**</span></span>  
 <span data-ttu-id="62793-164">移至精靈的下一頁。</span><span class="sxs-lookup"><span data-stu-id="62793-164">Go to the next page in the wizard.</span></span>  
  
## <a name="select-installation-folder-page"></a><span data-ttu-id="62793-165">選取安裝資料夾頁面</span><span class="sxs-lookup"><span data-stu-id="62793-165">Select Installation Folder Page</span></span>  
 <span data-ttu-id="62793-166">使用 [選取安裝資料夾]  頁面，即可指定安裝封裝及其相依性的檔案系統資料夾。</span><span class="sxs-lookup"><span data-stu-id="62793-166">Use the **Select Installation Folder** page to specify the file system folder in which to install the packages and their dependencies.</span></span>  
  
### <a name="options"></a><span data-ttu-id="62793-167">選項。</span><span class="sxs-lookup"><span data-stu-id="62793-167">Options</span></span>  
 <span data-ttu-id="62793-168">**資料夾**</span><span class="sxs-lookup"><span data-stu-id="62793-168">**Folder**</span></span>  
 <span data-ttu-id="62793-169">指定複製封裝及其相依性的路徑和資料夾。</span><span class="sxs-lookup"><span data-stu-id="62793-169">Specify the path and folder in which to copy the package and its dependencies.</span></span>  
  
 <span data-ttu-id="62793-170">**瀏覽**</span><span class="sxs-lookup"><span data-stu-id="62793-170">**Browse**</span></span>  
 <span data-ttu-id="62793-171">使用 [瀏覽資料夾]  對話方塊，即可瀏覽至目標資料夾。</span><span class="sxs-lookup"><span data-stu-id="62793-171">Browse to the target folder by using the **Browse For Folder** dialog box.</span></span>  
  
 <span data-ttu-id="62793-172">**下一個**</span><span class="sxs-lookup"><span data-stu-id="62793-172">**Next**</span></span>  
 <span data-ttu-id="62793-173">移至精靈的下一頁。</span><span class="sxs-lookup"><span data-stu-id="62793-173">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="62793-174">**[完成]**</span><span class="sxs-lookup"><span data-stu-id="62793-174">**Finish**</span></span>  
 <span data-ttu-id="62793-175">跳到 [完成封裝安裝精靈] 頁面。</span><span class="sxs-lookup"><span data-stu-id="62793-175">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="62793-176">如果您有依序返回精靈的其他頁面以修訂選擇，並且已指定了所有必要的選項，則請使用此選項。</span><span class="sxs-lookup"><span data-stu-id="62793-176">Use this option if you have backtracked through the wizard pages to revise your choices and if have specified all of the required options.</span></span>  
  
## <a name="specify-target-sql-server-page"></a><span data-ttu-id="62793-177">指定目標 SQL Server 頁面</span><span class="sxs-lookup"><span data-stu-id="62793-177">Specify Target SQL Server Page</span></span>  
 <span data-ttu-id="62793-178">使用 [指定目標 SQL Server]  頁面，即可指定將封裝部署至 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 執行個體的選項。</span><span class="sxs-lookup"><span data-stu-id="62793-178">Use the **Specify Target SQL Server** page to specify options for deploying the package to an instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span>  
  
### <a name="options"></a><span data-ttu-id="62793-179">選項。</span><span class="sxs-lookup"><span data-stu-id="62793-179">Options</span></span>  
 <span data-ttu-id="62793-180">**伺服器名稱**</span><span class="sxs-lookup"><span data-stu-id="62793-180">**Server name**</span></span>  
 <span data-ttu-id="62793-181">指定部署封裝目的地之伺服器的名稱。</span><span class="sxs-lookup"><span data-stu-id="62793-181">Specify the name of the server to deploy the packages to.</span></span>  
  
 <span data-ttu-id="62793-182">**[使用 Windows 驗證]**</span><span class="sxs-lookup"><span data-stu-id="62793-182">**Use Windows Authentication**</span></span>  
 <span data-ttu-id="62793-183">指定是否使用 Windows 驗證來登入伺服器。</span><span class="sxs-lookup"><span data-stu-id="62793-183">Specify whether to use Windows Authentication to log on to the server.</span></span> <span data-ttu-id="62793-184">建議使用 Windows 驗證，以獲得較佳的安全性。</span><span class="sxs-lookup"><span data-stu-id="62793-184">Windows Authentication is recommended for better security.</span></span>  
  
 <span data-ttu-id="62793-185">**[使用 SQL Server 驗證]**</span><span class="sxs-lookup"><span data-stu-id="62793-185">**Use SQL Server Authentication**</span></span>  
 <span data-ttu-id="62793-186">指定封裝是否應使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證來登入伺服器。</span><span class="sxs-lookup"><span data-stu-id="62793-186">Specify whether the package should use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication to log on to the server.</span></span> <span data-ttu-id="62793-187">如果您使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證，就必須提供使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="62793-187">If you use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, you must provide a user name and password.</span></span>  
  
 <span data-ttu-id="62793-188">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="62793-188">**User name**</span></span>  
 <span data-ttu-id="62793-189">指定使用者名稱。</span><span class="sxs-lookup"><span data-stu-id="62793-189">Specify a user name.</span></span>  
  
 <span data-ttu-id="62793-190">**密碼**</span><span class="sxs-lookup"><span data-stu-id="62793-190">**Password**</span></span>  
 <span data-ttu-id="62793-191">指定密碼。</span><span class="sxs-lookup"><span data-stu-id="62793-191">Specify a password.</span></span>  
  
 <span data-ttu-id="62793-192">**封裝路徑**</span><span class="sxs-lookup"><span data-stu-id="62793-192">**Package path**</span></span>  
 <span data-ttu-id="62793-193">指定邏輯資料夾名稱，或輸入 "/" 代表預設資料夾。</span><span class="sxs-lookup"><span data-stu-id="62793-193">Specify the name of the logical folder, or enter "/" for the default folder.</span></span>  
  
 <span data-ttu-id="62793-194">若要在 [SSIS 封裝]  對話方塊中選取資料夾，請按一下 [瀏覽 (...)]。不過，此對話方塊並不能用來選取預設資料夾。</span><span class="sxs-lookup"><span data-stu-id="62793-194">To select the folder in the **SSIS Package** dialog box, click browse (...). However, the dialog box does not provide a means to select the default folder.</span></span> <span data-ttu-id="62793-195">如果想要使用預設資料夾，必須在文字方塊中輸入 "/"。</span><span class="sxs-lookup"><span data-stu-id="62793-195">If you want to use the default folder, you have to enter "/" in the text box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="62793-196">如果未輸入有效的套件路徑，則會出現下列錯誤訊息：「一或多個引數無效。」</span><span class="sxs-lookup"><span data-stu-id="62793-196">If you do not enter a valid package path, the following error message appears: "One or more arguments are invalid."</span></span>  
  
 <span data-ttu-id="62793-197">**依賴伺服器儲存體進行加密**</span><span class="sxs-lookup"><span data-stu-id="62793-197">**Rely on server storage for encryption**</span></span>  
 <span data-ttu-id="62793-198">選取即可使用 [!INCLUDE[ssDE](../includes/ssde-md.md)] 的安全性功能來保護封裝的安全。</span><span class="sxs-lookup"><span data-stu-id="62793-198">Select to use security features of the [!INCLUDE[ssDE](../includes/ssde-md.md)] to help secure the packages.</span></span>  
  
 <span data-ttu-id="62793-199">**下一個**</span><span class="sxs-lookup"><span data-stu-id="62793-199">**Next**</span></span>  
 <span data-ttu-id="62793-200">移至精靈的下一頁。</span><span class="sxs-lookup"><span data-stu-id="62793-200">Go to the next page in the wizard.</span></span>  
  
 <span data-ttu-id="62793-201">**[完成]**</span><span class="sxs-lookup"><span data-stu-id="62793-201">**Finish**</span></span>  
 <span data-ttu-id="62793-202">跳到 [完成封裝安裝精靈] 頁面。</span><span class="sxs-lookup"><span data-stu-id="62793-202">Skip to the Finish the Package Installation Wizard page.</span></span> <span data-ttu-id="62793-203">如果您依序返回精靈的頁面以修訂您的選擇，並且指定了所有必要的選項，則請使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="62793-203">Use this option if you have backtracked through the wizard pages to revise your choices and have specified all of the required options.</span></span>  
  
## <a name="finish-the-package-installation-page"></a><span data-ttu-id="62793-204">完成封裝安裝頁面</span><span class="sxs-lookup"><span data-stu-id="62793-204">Finish the Package Installation Page</span></span>  
 <span data-ttu-id="62793-205">使用 [完成封裝安裝精靈]  頁面，即可檢視封裝安裝結果的摘要。</span><span class="sxs-lookup"><span data-stu-id="62793-205">Use the **Finish the Package Installation Wizard** page to view a summary of the package installation results.</span></span> <span data-ttu-id="62793-206">此頁面提供詳細資料，例如已部署的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案、已安裝的封裝、組態檔以及安裝位置。</span><span class="sxs-lookup"><span data-stu-id="62793-206">This page provides details such as the name of the deployed [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, the packages that were installed, the configuration files, and the installation location.</span></span>  
  
 <span data-ttu-id="62793-207">**[完成]**</span><span class="sxs-lookup"><span data-stu-id="62793-207">**Finish**</span></span>  
 <span data-ttu-id="62793-208">按一下 [完成]  以結束精靈。</span><span class="sxs-lookup"><span data-stu-id="62793-208">Exit the wizard by clicking **Finish**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62793-209">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62793-209">See Also</span></span>  
 [<span data-ttu-id="62793-210">&#40;SSIS&#41;的套件部署</span><span class="sxs-lookup"><span data-stu-id="62793-210">Package Deployment &#40;SSIS&#41;</span></span>](packages/legacy-package-deployment-ssis.md)  
  
  
