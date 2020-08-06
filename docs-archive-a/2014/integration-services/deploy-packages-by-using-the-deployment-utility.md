---
title: 使用部署公用程式來部署封裝 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- packages [Integration Services], installing
- installing packages
- dependencies [Integration Services]
- deploying packages [Integration Services], installing
ms.assetid: eaf4b56e-2023-4d17-971c-703031da758c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a09ad307dc0215fca679cfb1ef5a37031f951caf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703222"
---
# <a name="deploy-packages-by-using-the-deployment-utility"></a><span data-ttu-id="1e861-102">Deploy Packages by Using the Deployment Utility</span><span class="sxs-lookup"><span data-stu-id="1e861-102">Deploy Packages by Using the Deployment Utility</span></span>
  <span data-ttu-id="1e861-103">當已建立部署公用程式，以從建立部署公用程式之電腦以外電腦上的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案安裝封裝時，必須首先將部署資料夾複製到目的地電腦。</span><span class="sxs-lookup"><span data-stu-id="1e861-103">When you have built a deployment utility to install packages from an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project on a different computer than the one on which the deployment utility was built, you must first copy the deployment folder to the destination computer.</span></span>  
  
 <span data-ttu-id="1e861-104">部署資料夾的路徑是在為其建立部署公用程式之 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案的 DeploymentOutputPath 屬性中指定的。</span><span class="sxs-lookup"><span data-stu-id="1e861-104">The path of the deployment folder is specified in the DeploymentOutputPath property of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project for which you created the deployment utility.</span></span> <span data-ttu-id="1e861-105">預設路徑為 bin\Deployment (相對於 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案)。</span><span class="sxs-lookup"><span data-stu-id="1e861-105">The default path is bin\Deployment, relative to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span> <span data-ttu-id="1e861-106">如需詳細資訊，請參閱 [建立部署公用程式](../../2014/integration-services/create-a-deployment-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="1e861-106">For more information, see [Create a Deployment Utility](../../2014/integration-services/create-a-deployment-utility.md).</span></span>  
  
 <span data-ttu-id="1e861-107">請使用「封裝安裝精靈」來安裝封裝。</span><span class="sxs-lookup"><span data-stu-id="1e861-107">You use the Package Installation Wizard to install the packages.</span></span> <span data-ttu-id="1e861-108">若要啟動此精靈，請在將部署資料夾複製到伺服器後按兩下部署公用程式檔案。</span><span class="sxs-lookup"><span data-stu-id="1e861-108">To launch the wizard, double-click the deployment utility file after you have copied the deployment folder to the server.</span></span> <span data-ttu-id="1e861-109">此檔案名為 \<project name>.SSISDeploymentManifest，您可在目的地電腦的部署資料夾中找到這個檔案。</span><span class="sxs-lookup"><span data-stu-id="1e861-109">This file is named \<project name>.SSISDeploymentManifest, and can be found in the deployment folder on the destination computer.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1e861-110">根據所部署的封裝版本，如果有不同版本的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 並存安裝，可能會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="1e861-110">Depending on the version of the package that you are deploying, you might encounter an error if you have different versions of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] installed side-by-side.</span></span> <span data-ttu-id="1e861-111">因為 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]所有版本的 .SSISDeploymentManifest 副檔名都相同，所以可能會發生這項錯誤。</span><span class="sxs-lookup"><span data-stu-id="1e861-111">This error can occur because the .SSISDeploymentManifest file name extension is the same for all versions of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="1e861-112">按兩下此檔案就會針對最近安裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]版本 (可能與部署公用程式檔案的版本不同) 呼叫安裝程式 (dtsinstall.exe)。</span><span class="sxs-lookup"><span data-stu-id="1e861-112">Double-clicking the file calls the installer (dtsinstall.exe) for the most recently installed version of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], which might not be the same version as the deployment utility file.</span></span> <span data-ttu-id="1e861-113">若要解決此問題，請從命令列執行正確的 dtsinstall.exe 版本，並且提供部署公用程式檔案的路徑。</span><span class="sxs-lookup"><span data-stu-id="1e861-113">To work around this problem, run the correct version of dtsinstall.exe from the command line, and provide the path of the deployment utility file.</span></span>  
  
 <span data-ttu-id="1e861-114">[封裝安裝精靈] 會逐步引導您將封裝安裝到檔案系統或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="1e861-114">The Package Installation Wizard guides you through the steps to install packages to the file system or to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="1e861-115">您可以利用下列方式來設定安裝：</span><span class="sxs-lookup"><span data-stu-id="1e861-115">You can configure the installation in the following ways:</span></span>  
  
-   <span data-ttu-id="1e861-116">選擇用來安裝封裝的位置類型和位置。</span><span class="sxs-lookup"><span data-stu-id="1e861-116">Choosing the location type and location to install the packages.</span></span>  
  
-   <span data-ttu-id="1e861-117">選擇用來安裝封裝相依性的位置。</span><span class="sxs-lookup"><span data-stu-id="1e861-117">Choosing location to install package dependencies.</span></span>  
  
-   <span data-ttu-id="1e861-118">在封裝安裝在目標伺服器之後驗證封裝。</span><span class="sxs-lookup"><span data-stu-id="1e861-118">Validating the packages after they are installed on the target server.</span></span>  
  
 <span data-ttu-id="1e861-119">封裝之以檔案作為基礎的相依性總是安裝到檔案系統。</span><span class="sxs-lookup"><span data-stu-id="1e861-119">The file-based dependencies for packages are always installed to the file system.</span></span> <span data-ttu-id="1e861-120">如果您將封裝安裝到檔案系統，則會將相依性安裝到為封裝指定的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1e861-120">If you install a package to the file system, the dependencies are installed in the same folder as the one that you specify for the package.</span></span> <span data-ttu-id="1e861-121">如果您將封裝安裝到 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]，則可指定要儲存以檔案基礎之相依性的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1e861-121">If you install a package to [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], you can specify the folder in which to store the file-based dependencies.</span></span>  
  
 <span data-ttu-id="1e861-122">如果封裝包含您要修改以用於目的地電腦的組態，則可使用精靈更新屬性的值。</span><span class="sxs-lookup"><span data-stu-id="1e861-122">If the package includes configurations that you want to modify for use on the destination computer, you can update the values of the properties by using the wizard.</span></span>  
  
 <span data-ttu-id="1e861-123">除了使用 [封裝安裝精靈] 安裝封裝之外，還可以使用 **dtutil** 命令提示字元公用程式來複製和移動封裝。</span><span class="sxs-lookup"><span data-stu-id="1e861-123">In addition to installing packages by using the Package Installation Wizard, you can copy and move packages by using the **dtutil** command prompt utility.</span></span> <span data-ttu-id="1e861-124">如需詳細資訊，請參閱 [dtutil Utility](dtutil-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="1e861-124">For more information, see [dtutil Utility](dtutil-utility.md).</span></span>  
  
### <a name="to-deploy-packages-to-an-instance-of-sql-server"></a><span data-ttu-id="1e861-125">將封裝部署至 SQL Server 的執行個體</span><span class="sxs-lookup"><span data-stu-id="1e861-125">To deploy packages to an instance of SQL Server</span></span>  
  
1.  <span data-ttu-id="1e861-126">開啟目標電腦上的部署資料夾。</span><span class="sxs-lookup"><span data-stu-id="1e861-126">Open the deployment folder on the target computer.</span></span>  
  
2.  <span data-ttu-id="1e861-127">按兩下資訊清單檔 \<project name>.SSISDeploymentManifest，以啟動 [套件安裝精靈]。</span><span class="sxs-lookup"><span data-stu-id="1e861-127">Double-click the manifest file, \<project name>.SSISDeploymentManifest, to start the Package Installation Wizard.</span></span>  
  
3.  <span data-ttu-id="1e861-128">在 [部署 SSIS 封裝]  頁面上，選取 [SQL Server 部署]  選項。</span><span class="sxs-lookup"><span data-stu-id="1e861-128">On the **Deploy SSIS Packages** page, select the **SQL Server deployment** option.</span></span>  
  
4.  <span data-ttu-id="1e861-129">選擇性地選取 [安裝之後驗證封裝]  ，以在將封裝安裝到目標伺服器後對其進行驗證。</span><span class="sxs-lookup"><span data-stu-id="1e861-129">Optionally, select **Validate packages after installation** to validate packages after they are installed on the target server.</span></span>  
  
5.  <span data-ttu-id="1e861-130">在 [指定目標 SQL Server]  頁面上，指定要安裝封裝的 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 的執行個體，並選取驗證模式。</span><span class="sxs-lookup"><span data-stu-id="1e861-130">On the **Specify Target SQL Server** page, specify the instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] to install the packages to and select an authentication mode.</span></span> <span data-ttu-id="1e861-131">如果選取「 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 驗證」，則您必須提供使用者名稱和密碼。</span><span class="sxs-lookup"><span data-stu-id="1e861-131">If you select [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Authentication, you must provide a user name and a password.</span></span>  
  
6.  <span data-ttu-id="1e861-132">在 [選取安裝資料夾]  頁面上，為要安裝的封裝相依性指定檔案系統中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="1e861-132">On the **Select Installation Folder** page, specify the folder in the file system for the package dependencies that will be installed.</span></span>  
  
7.  <span data-ttu-id="1e861-133">如果封裝包括組態，則可透過更新 [設定封裝] 頁面上 [值]  清單中的值來編輯組態。</span><span class="sxs-lookup"><span data-stu-id="1e861-133">If the package includes configurations, you can edit configurations by updating values in the **Value** list on the Configure Packages page.</span></span>  
  
8.  <span data-ttu-id="1e861-134">如果選擇在安裝後驗證封裝，請檢視已部署封裝的驗證結果。</span><span class="sxs-lookup"><span data-stu-id="1e861-134">If you elected to validate packages after installation, view the validation results of the deployed packages.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e861-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e861-135">See Also</span></span>  
 [<span data-ttu-id="1e861-136">&#40;SSIS&#41;的套件部署</span><span class="sxs-lookup"><span data-stu-id="1e861-136">Package Deployment &#40;SSIS&#41;</span></span>](packages/legacy-package-deployment-ssis.md)  
  
  
