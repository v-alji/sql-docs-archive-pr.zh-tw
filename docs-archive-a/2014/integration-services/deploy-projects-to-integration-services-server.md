---
title: 將專案部署到 Integration Services Server |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 6e9402f4-4d50-49ff-820d-65a77829c4a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 944dff3531fa24344c5157a1ac90e0109c6d0387
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599612"
---
# <a name="deploy-projects-to-integration-services-server"></a><span data-ttu-id="fe260-102">將專案部署至 Integration Services 伺服器</span><span class="sxs-lookup"><span data-stu-id="fe260-102">Deploy Projects to Integration Services Server</span></span>
  <span data-ttu-id="fe260-103">在目前版本的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]中，您可以將專案部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="fe260-103">In the current release of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], you can deploy your projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="fe260-104">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器可讓您管理封裝、執行封裝，以及利用環境設定封裝的執行值。</span><span class="sxs-lookup"><span data-stu-id="fe260-104">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server enables you to manage packages, run packages, and configure runtime values for packages by using environments.</span></span>  
  
 <span data-ttu-id="fe260-105">如需環境的詳細資訊，請參閱 [建立和對應伺服器環境](../../2014/integration-services/create-and-map-a-server-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="fe260-105">For more information about environments, see [Create and Map a Server Environment](../../2014/integration-services/create-and-map-a-server-environment.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fe260-106">與舊版 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]相同，在目前版本中，您也可以將封裝部署至 SQL Server 的執行個體，以及使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務來執行和管理封裝。</span><span class="sxs-lookup"><span data-stu-id="fe260-106">As in earlier versions of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], in the current release you can also deploy your packages to an instance of SQL Server and use [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service to run and manage the packages.</span></span> <span data-ttu-id="fe260-107">您會使用封裝部署模型。</span><span class="sxs-lookup"><span data-stu-id="fe260-107">You use the package deployment model.</span></span> <span data-ttu-id="fe260-108">如需詳細資訊，請參閱[&#40;SSIS&#41;的封裝部署](packages/legacy-package-deployment-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="fe260-108">For more information, see [Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md).</span></span>  
  
 <span data-ttu-id="fe260-109">如果要將專案部署至 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器，請完成下列工作：</span><span class="sxs-lookup"><span data-stu-id="fe260-109">To deploy a project to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, complete the following tasks:</span></span>  
  
1.  <span data-ttu-id="fe260-110">建立 SSISDB 目錄 (如果尚未建立)。</span><span class="sxs-lookup"><span data-stu-id="fe260-110">Create an SSISDB catalog, if you haven't already.</span></span> <span data-ttu-id="fe260-111">如需詳細資訊，請參閱 [建立 SSIS 目錄](catalog/ssis-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="fe260-111">For more information, see [Create the SSIS Catalog](catalog/ssis-catalog.md).</span></span>  
  
2.  <span data-ttu-id="fe260-112">請執行 [Integration Services 專案轉換精靈]\*\*\*\* 將專案轉換為專案部署模型。</span><span class="sxs-lookup"><span data-stu-id="fe260-112">Convert the project to the project deployment model by running the **Integration Services Project Conversion Wizard** .</span></span> <span data-ttu-id="fe260-113">如需詳細資訊，請參閱底下指示： [將專案轉換為專案部署模型](#convert)</span><span class="sxs-lookup"><span data-stu-id="fe260-113">For more information, see the instructions below: [To convert a project to the project deployment model](#convert)</span></span>  
  
    -   <span data-ttu-id="fe260-114">若您將專案建立在 [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)]中，則專案會根據預設使用專案部署模型。</span><span class="sxs-lookup"><span data-stu-id="fe260-114">If you created the project in [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)], by default the project uses the project deployment model.</span></span>  
  
    -   <span data-ttu-id="fe260-115">若是在舊版 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]中建立專案，在您於 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]中開啟專案檔案後，請將專案轉換為專案部署模型。</span><span class="sxs-lookup"><span data-stu-id="fe260-115">If you created the project in an earlier release of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)], after you open the project file in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], convert the project to the project deployment model.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="fe260-116">如果專案包含一個或多個資料來源，則在完成專案轉換時，會移除資料來源。</span><span class="sxs-lookup"><span data-stu-id="fe260-116">If the project contains one or more datasources, the datasources are removed when the project conversion is completed.</span></span> <span data-ttu-id="fe260-117">若要建立專案中的封裝可以共用的資料來源連接，請在專案層級加入連接管理員。</span><span class="sxs-lookup"><span data-stu-id="fe260-117">To create a connection to a data source that the packages in the project can share, add a connection manager at the project level.</span></span> <span data-ttu-id="fe260-118">如需詳細資訊，請參閱 [加入、刪除或共用封裝中的連線管理員](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md)。</span><span class="sxs-lookup"><span data-stu-id="fe260-118">For more information, see [Add, Delete, or Share a Connection Manager in a Package](../../2014/integration-services/add-delete-or-share-a-connection-manager-in-a-package.md).</span></span>  
  
         <span data-ttu-id="fe260-119">根據您是從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 還是從 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 執行 [Integration Services 專案轉換精靈]\*\*\*\*，此精靈會執行不同的轉換工作。</span><span class="sxs-lookup"><span data-stu-id="fe260-119">Depending on whether you run the **Integration Services Project Conversion Wizard** from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] or from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], the wizard performs different conversion tasks.</span></span>  
  
        -   <span data-ttu-id="fe260-120">如果您是從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]執行此精靈，則專案中包含的封裝會從 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 2005、2008 或 2008 R2 轉換為目前版本的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]使用的格式。</span><span class="sxs-lookup"><span data-stu-id="fe260-120">If you run the wizard from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], the packages contained in the project are converted from [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 2005, 2008, or 2008 R2 to the format that is used by the current version of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)].</span></span> <span data-ttu-id="fe260-121">系統將會升級原始專案 (.dtproj) 和封裝 (.dtsx) 檔。</span><span class="sxs-lookup"><span data-stu-id="fe260-121">The original project (.dtproj) and package (.dtsx) files are upgraded.</span></span>  
  
        -   <span data-ttu-id="fe260-122">如果您是從 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]執行此精靈，此精靈將會從專案中包含的封裝和組態產生專案部署檔案 (.ispac)。</span><span class="sxs-lookup"><span data-stu-id="fe260-122">If you run the wizard from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], the wizard generates a project deployment file (.ispac) from the packages and configurations contained in the project.</span></span> <span data-ttu-id="fe260-123">系統將不會升級原始封裝 (.dtsx) 檔。</span><span class="sxs-lookup"><span data-stu-id="fe260-123">The original package (.dtsx) files are not upgraded.</span></span>  
  
             <span data-ttu-id="fe260-124">您可以在精靈的 [選取目的地]\*\*\*\* 頁面中選取現有的檔案，或建立一個新檔案。</span><span class="sxs-lookup"><span data-stu-id="fe260-124">You can select an existing file or create a new file, in the **Selection Destination** page of the wizard.</span></span>  
  
             <span data-ttu-id="fe260-125">若要在轉換專案時升級封裝檔，請從 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 執行 [Integration Services 專案轉換精靈]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe260-125">To upgrade package files when a project is converted, run the **Integration Services Project Conversion Wizard** from [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="fe260-126">若要從專案轉換個別升級封裝檔案，請從 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 執行 [Integration Services 專案轉換精靈]\*\*\*\*，然後執行 [SSIS 封裝升級精靈]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe260-126">To upgrade package files separately from a project conversion, run the **Integration Services Project Conversion Wizard** from [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] and then run the **SSIS Package Upgrade Wizard**.</span></span> <span data-ttu-id="fe260-127">若您個別升級封裝檔，請確認是否儲存變更。</span><span class="sxs-lookup"><span data-stu-id="fe260-127">If you upgrade the package files separately, ensure that you save the changes.</span></span> <span data-ttu-id="fe260-128">否則，當您將專案轉換成專案部署模型時，所有未儲存的封裝變更將不予轉換。</span><span class="sxs-lookup"><span data-stu-id="fe260-128">Otherwise, when you convert the project to the project deployment model, any unsaved changes to the package are not converted.</span></span>  
  
     <span data-ttu-id="fe260-129">如需封裝升級的詳細資訊，請參閱 [升級 Integration Services 封裝](install-windows/upgrade-integration-services-packages.md) 和 [使用 SSIS 封裝升級精靈來升級 Integration Services 封裝](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="fe260-129">For more information on package upgrade, see [Upgrade Integration Services Packages](install-windows/upgrade-integration-services-packages.md) and [Upgrade Integration Services Packages Using the SSIS Package Upgrade Wizard](install-windows/upgrade-integration-services-packages-using-the-ssis-package-upgrade-wizard.md).</span></span>  
  
3.  <span data-ttu-id="fe260-130">將專案部署至 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="fe260-130">Deploy the project to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server.</span></span> <span data-ttu-id="fe260-131">如需詳細資訊，請參閱底下指示： [將專案部署至 Integration Services 伺服器](#deploy)。</span><span class="sxs-lookup"><span data-stu-id="fe260-131">For more information, see the instructions below: [To deploy a project to the Integration Services Server](#deploy).</span></span>  
  
4.  <span data-ttu-id="fe260-132">(選擇性) 建立部署專案的環境。</span><span class="sxs-lookup"><span data-stu-id="fe260-132">(Optional) Create an environment for the deployed project.</span></span> <span data-ttu-id="fe260-133">如需詳細資訊，請參閱 [建立和對應伺服器環境](../../2014/integration-services/create-and-map-a-server-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="fe260-133">For more information, see [Create and Map a Server Environment](../../2014/integration-services/create-and-map-a-server-environment.md).</span></span>  
  
##  <a name="to-convert-a-project-to-the-project-deployment-model"></a><a name="convert"></a><span data-ttu-id="fe260-134">若要將專案轉換為專案部署模型</span><span class="sxs-lookup"><span data-stu-id="fe260-134">To convert a project to the project deployment model</span></span>  
  
1.  <span data-ttu-id="fe260-135">開啟 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中的專案，然後在方案總管中，以滑鼠右鍵按一下該專案，並按一下 [轉換為專案部署模型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe260-135">Open the project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], and then in Solution Explorer, right-click the project and click **Convert to Project Deployment Model**.</span></span>  
  
     <span data-ttu-id="fe260-136">-或-</span><span class="sxs-lookup"><span data-stu-id="fe260-136">-or-</span></span>  
  
     <span data-ttu-id="fe260-137">從 [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 的物件總管中，以滑鼠右鍵按一下 [專案]\*\*\*\* 節點，然後選取 [匯入封裝]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe260-137">From Object Explorer in [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)], right-click the **Projects** node and select **Import Packages**.</span></span>  
  
2.  <span data-ttu-id="fe260-138">完成精靈。</span><span class="sxs-lookup"><span data-stu-id="fe260-138">Complete the wizard.</span></span> <span data-ttu-id="fe260-139">如需相關資訊，請參閱 [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="fe260-139">For more information, see [Integration Services Project Conversion Wizard](../../2014/integration-services/integration-services-project-conversion-wizard.md).</span></span>  
  
##  <a name="to-deploy-a-project-to-the-integration-services-server"></a><a name="deploy"></a><span data-ttu-id="fe260-140">若要將專案部署至 Integration Services 伺服器</span><span class="sxs-lookup"><span data-stu-id="fe260-140">To deploy a project to the Integration Services Server</span></span>  
  
1.  <span data-ttu-id="fe260-141">開啟 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] 中的專案，然後從 [專案]\*\*\*\* 功能表中選取 [部署]\*\*\*\*，以啟動 [Integration Services 部署精靈]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe260-141">Open the project in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], and then From the **Project** menu, select **Deploy** to launch the **Integration Services Deployment Wizard**.</span></span>  
  
     <span data-ttu-id="fe260-142">-或-</span><span class="sxs-lookup"><span data-stu-id="fe260-142">-or-</span></span>  
  
     <span data-ttu-id="fe260-143">在中 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ，展開 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]  >  物件總管中的 [ **SSISDB** ] 節點，然後找出您要部署之專案的 [專案] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="fe260-143">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], expand the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] > **SSISDB** node in Object Explorer, and locate the Projects folder for the project you want to deploy.</span></span> <span data-ttu-id="fe260-144">以滑鼠右鍵按一下 [專案]\*\*\*\* 資料夾，然後按一下 [部署專案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fe260-144">Right-click the **Projects** folder, and then click **Deploy Project**.</span></span>  
  
     <span data-ttu-id="fe260-145">-或-</span><span class="sxs-lookup"><span data-stu-id="fe260-145">-or-</span></span>  
  
     <span data-ttu-id="fe260-146">在命令提示字元中，從 **%ProgramFiles%\Microsoft SQL Server\110\DTS\Binn** 執行 **isdeploymentwizard.exe**。</span><span class="sxs-lookup"><span data-stu-id="fe260-146">From the command prompt, run **isdeploymentwizard.exe** from **%ProgramFiles%\Microsoft SQL Server\110\DTS\Binn**.</span></span> <span data-ttu-id="fe260-147">64 位元的電腦上的 **%ProgramFiles(x86)%\Microsoft SQL Server\100\DTS\Binn**也有提供 32 位元版本的工具。</span><span class="sxs-lookup"><span data-stu-id="fe260-147">On 64-bit computers, there is also a 32-bit version of the tool in **%ProgramFiles(x86)%\Microsoft SQL Server\100\DTS\Binn**.</span></span>  
  
2.  <span data-ttu-id="fe260-148">在 [選取來源]\*\*\*\* 頁面上，按一下 [專案部署檔案]\*\*\*\* 以選取專案的部署檔案。</span><span class="sxs-lookup"><span data-stu-id="fe260-148">On the **Select Source** page, click **Project deployment file** to select the deployment file for the project.</span></span>  
  
     <span data-ttu-id="fe260-149">-或-</span><span class="sxs-lookup"><span data-stu-id="fe260-149">-OR-</span></span>  
  
     <span data-ttu-id="fe260-150">按一下 [Integration Services 目錄]\*\*\*\*，選取已經部署至 SSISDB 目錄的專案。</span><span class="sxs-lookup"><span data-stu-id="fe260-150">Click **Integration Services catalog** to select a project that has already been deployed to the SSISDB catalog.</span></span>  
  
3.  <span data-ttu-id="fe260-151">完成精靈。</span><span class="sxs-lookup"><span data-stu-id="fe260-151">Complete the wizard.</span></span> <span data-ttu-id="fe260-152">如需詳細資訊，請參閱 [Integration Services 部署精靈](../../2014/integration-services/integration-services-deployment-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="fe260-152">For more information, see [Integration Services Deployment Wizard](../../2014/integration-services/integration-services-deployment-wizard.md).</span></span>  
  
  
