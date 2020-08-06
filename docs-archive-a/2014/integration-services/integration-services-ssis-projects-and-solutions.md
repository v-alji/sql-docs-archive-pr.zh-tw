---
title: Integration Services (SSIS) 專案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Integration Services], creating
- folders [Integration Services], projects
- files [Integration Services], projects
- folders [Integration Services]
- projects [Integration Services], about projects
ms.assetid: 28ea8120-0a79-4029-93f0-07d521b32bee
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f71555a5339412bd0b79492607769d744c0d1a89
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596164"
---
# <a name="integration-services-ssis-projects"></a><span data-ttu-id="f2e66-102">Integration Services (SSIS) 專案</span><span class="sxs-lookup"><span data-stu-id="f2e66-102">Integration Services (SSIS) Projects</span></span>
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="f2e66-103">提供 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 以用於開發 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝。</span><span class="sxs-lookup"><span data-stu-id="f2e66-103">provides [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] for the development of [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>

 <span data-ttu-id="f2e66-104">當您將封裝部署到 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 資料庫或 [!INCLUDE[ssIS](../includes/ssis-md.md)] 封裝存放區時，您會使用此 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務來管理封裝。</span><span class="sxs-lookup"><span data-stu-id="f2e66-104">When you deploy packages to a [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] database or the [!INCLUDE[ssIS](../includes/ssis-md.md)] Package Store, you use the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service to manage the packages.</span></span> <span data-ttu-id="f2e66-105">[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務只可以在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中使用。</span><span class="sxs-lookup"><span data-stu-id="f2e66-105">The [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service is available only in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="f2e66-106">如需服務的詳細資訊，請參閱 [Integration Services 服務 &#40;SSIS 服務&#41;](service/integration-services-service-ssis-service.md)。</span><span class="sxs-lookup"><span data-stu-id="f2e66-106">For more information about the service, see [Integration Services Service &#40;SSIS Service&#41;](service/integration-services-service-ssis-service.md).</span></span> <span data-ttu-id="f2e66-107">如需套件部署的詳細資訊，請參閱[&#40;SSIS&#41;的套件部署](packages/legacy-package-deployment-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="f2e66-107">For more information about package deployment, see [Package Deployment &#40;SSIS&#41;](packages/legacy-package-deployment-ssis.md).</span></span>

 <span data-ttu-id="f2e66-108">當您將 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案部署到 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器時，則是在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中使用 Transact-SQL 檢視和預存程序來管理專案。</span><span class="sxs-lookup"><span data-stu-id="f2e66-108">When you deploy [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects to the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, you use Transact-SQL views and stored procedures in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to manage the projects.</span></span> <span data-ttu-id="f2e66-109">如需專案部署的詳細資訊，請參閱[部署 Integration Services (SSIS) 專案和封裝](packages/deploy-integration-services-ssis-projects-and-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="f2e66-109">For more information about project deployment, see [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).</span></span> <span data-ttu-id="f2e66-110">如需 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 伺服器的詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 伺服器](catalog/integration-services-ssis-server-and-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="f2e66-110">For more information about the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] server, see [Integration Services &#40;SSIS&#41; Server](catalog/integration-services-ssis-server-and-catalog.md).</span></span>

 <span data-ttu-id="f2e66-111">如需 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 和 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 的概觀，請參閱 [Integration Services &#40;SSIS&#41; 和 Studio 環境](integration-services-ssis-development-and-management-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="f2e66-111">For an overview of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], see [Integration Services &#40;SSIS&#41; and Studio Environments](integration-services-ssis-development-and-management-tools.md).</span></span>

## <a name="understanding-integration-services-projects"></a><span data-ttu-id="f2e66-112">了解 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="f2e66-112">Understanding Integration Services Projects</span></span>
 <span data-ttu-id="f2e66-113">專案是讓您開發 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝的容器。</span><span class="sxs-lookup"><span data-stu-id="f2e66-113">A project is a container in which you develop [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span>

 <span data-ttu-id="f2e66-114">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中， [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案會儲存及分組與此封裝有關的檔案。</span><span class="sxs-lookup"><span data-stu-id="f2e66-114">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project stores and groups the files that are related to the package.</span></span> <span data-ttu-id="f2e66-115">例如，專案會包含建立特定擷取、轉送和載入 (ETL) 方案時所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="f2e66-115">For example, a project includes the files that are required to create a specific extract, transfer, and load (ETL) solution.</span></span>

 <span data-ttu-id="f2e66-116">在您建立 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案之前，您應該先熟悉這一種專案的基本內容。</span><span class="sxs-lookup"><span data-stu-id="f2e66-116">Before you create an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, you should become familiar with the basic contents of this kind of project.</span></span> <span data-ttu-id="f2e66-117">在您了解專案所包含的內容之後，您可以開始建立及使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="f2e66-117">After you understand what a project contains, you can begin creating and working with an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>

### <a name="folders-in-integration-services-projects"></a><span data-ttu-id="f2e66-118">Integration Services 專案中的資料夾</span><span class="sxs-lookup"><span data-stu-id="f2e66-118">Folders in Integration Services Projects</span></span>
 <span data-ttu-id="f2e66-119">下圖顯示 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 中位於 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]專案內的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f2e66-119">The following diagram shows the folders in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>

 <span data-ttu-id="f2e66-120">![Integration Services 專案中的資料夾](media/solutionexplorer.gif "Integration Services 專案中的資料夾")</span><span class="sxs-lookup"><span data-stu-id="f2e66-120">![Folders in an Integration Services project](media/solutionexplorer.gif "Folders in an Integration Services project")</span></span>

 <span data-ttu-id="f2e66-121">下表描述顯示在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案中的資料夾。</span><span class="sxs-lookup"><span data-stu-id="f2e66-121">The following table describes the folders that appear in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>

|<span data-ttu-id="f2e66-122">資料夾</span><span class="sxs-lookup"><span data-stu-id="f2e66-122">Folder</span></span>|<span data-ttu-id="f2e66-123">描述</span><span class="sxs-lookup"><span data-stu-id="f2e66-123">Description</span></span>|
|------------|-----------------|
|[!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="f2e66-124">Packages</span><span class="sxs-lookup"><span data-stu-id="f2e66-124">Packages</span></span>|<span data-ttu-id="f2e66-125">包含封裝。</span><span class="sxs-lookup"><span data-stu-id="f2e66-125">Contains packages.</span></span> <span data-ttu-id="f2e66-126">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 封裝](../../2014/integration-services/integration-services-ssis-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="f2e66-126">For more information, see [Integration Services &#40;SSIS&#41; Packages](../../2014/integration-services/integration-services-ssis-packages.md).</span></span>|
|<span data-ttu-id="f2e66-127">其他</span><span class="sxs-lookup"><span data-stu-id="f2e66-127">Miscellaneous</span></span>|<span data-ttu-id="f2e66-128">包含封裝檔案之外的檔案。</span><span class="sxs-lookup"><span data-stu-id="f2e66-128">Contains files other than package files.</span></span>|

### <a name="files-in-integration-services-projects"></a><span data-ttu-id="f2e66-129">Integration Services 專案中的檔案</span><span class="sxs-lookup"><span data-stu-id="f2e66-129">Files in Integration Services Projects</span></span>
 <span data-ttu-id="f2e66-130">當您將新的或現有的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案加入方案時， [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 會建立副檔名為 .dtproj、.dtproj.user 和 .database 的專案檔案。</span><span class="sxs-lookup"><span data-stu-id="f2e66-130">When you add a new or an existing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to a solution, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] creates project files that have the extensions .dtproj and .dtproj.user and .database.</span></span>

-   <span data-ttu-id="f2e66-131">\*.dtproj 檔案包含有關專案組態以及封裝之類項目的資訊。</span><span class="sxs-lookup"><span data-stu-id="f2e66-131">The \*.dtproj file contains information about project configurations and items such as packages.</span></span>

-   <span data-ttu-id="f2e66-132">\*.dtproj.user 檔案包含有關您在使用專案時的偏好設定之資訊。</span><span class="sxs-lookup"><span data-stu-id="f2e66-132">The \*.dtproj.user file contains information about your preferences for working with the project.</span></span>

-   <span data-ttu-id="f2e66-133">\*.database 檔案包含 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 在開啟 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案時所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="f2e66-133">The \*.database file contains information that [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] requires to open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>

## <a name="understanding-solutions"></a><span data-ttu-id="f2e66-134">了解方案</span><span class="sxs-lookup"><span data-stu-id="f2e66-134">Understanding Solutions</span></span>
 <span data-ttu-id="f2e66-135">方案是將您在開發端對端商務方案時所使用的專案分組，並對其進行管理的一個容器。</span><span class="sxs-lookup"><span data-stu-id="f2e66-135">A solution is a container that groups and manages the projects that you use when you develop end-to-end business solutions.</span></span> <span data-ttu-id="f2e66-136">方案可讓您將多個專案當做一個單位來處理，並將對商務方案有幫助的一個或多個相關專案集合在一起。</span><span class="sxs-lookup"><span data-stu-id="f2e66-136">A solution lets you handle multiple projects as one unit and to bring together one or more related projects that contribute to a business solution.</span></span>

 <span data-ttu-id="f2e66-137">方案可包含不同類型的專案。</span><span class="sxs-lookup"><span data-stu-id="f2e66-137">Solutions can include different types of projects.</span></span> <span data-ttu-id="f2e66-138">若要使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師建立 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝，請在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 所提供的解決方案中利用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]專案來進行。</span><span class="sxs-lookup"><span data-stu-id="f2e66-138">If you want to use [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to create an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package, you work in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in a solution provided by [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>

 <span data-ttu-id="f2e66-139">當您建立新的解決方案時， [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 會將 [解決方案] 資料夾加入方案總管中，並建立副檔名為 .sln 和 .suo 的檔案：</span><span class="sxs-lookup"><span data-stu-id="f2e66-139">When you create a new solution, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] adds a Solution folder to Solution Explorer, and creates files that have the extensions, .sln and .suo:</span></span>

-   <span data-ttu-id="f2e66-140">\*.sln 檔案包含方案組態的相關資訊，並列出方案中的專案。</span><span class="sxs-lookup"><span data-stu-id="f2e66-140">The \*.sln file contains information about the solution configuration and lists the projects in the solution.</span></span>

-   <span data-ttu-id="f2e66-141">\*.suo 檔案包含關於使用方案之喜好設定的資訊。</span><span class="sxs-lookup"><span data-stu-id="f2e66-141">The \*.suo file contains information about your preferences for working with the solution.</span></span>

 <span data-ttu-id="f2e66-142">雖然 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 會在您新建專案時自動建立解決方案，但是您也可以建立空白的解決方案，並在稍後加入專案。</span><span class="sxs-lookup"><span data-stu-id="f2e66-142">While [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] automatically creates a solution when you create a new project, you can also create a blank solution, and then add projects later.</span></span>

> [!NOTE]
>  <span data-ttu-id="f2e66-143">依預設，當您在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中建立新的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案時，此解決方案不會顯示在 [專案總管]\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="f2e66-143">By default, when you create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the solution is not shown in the **Project Explorer** pane.</span></span> <span data-ttu-id="f2e66-144">若要變更這個預設行為，請按一下 [工具]\*\*\*\* 功能表上的 [選項]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2e66-144">To change this default behavior, on the **Tools** menus, click **Options**.</span></span> <span data-ttu-id="f2e66-145">在 [選項]\*\*\*\* 對話方塊中，展開 [專案和方案]\*\*\*\*，然後按一下 [一般]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2e66-145">In the **Options** dialog box, expand **Projects and Solutions**, and then click **General**.</span></span> <span data-ttu-id="f2e66-146">在 [一般]\*\*\*\* 頁面上，選取 [永遠顯示方案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f2e66-146">On the **General** page, select **Always show solution**.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="f2e66-147">相關工作</span><span class="sxs-lookup"><span data-stu-id="f2e66-147">Related Tasks</span></span>
 [<span data-ttu-id="f2e66-148">在方案中加入或移除 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="f2e66-148">Add or Remove an Integration Services Project in a Solution</span></span>](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)

 [<span data-ttu-id="f2e66-149">建立新的 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="f2e66-149">Create a New Integration Services Project</span></span>](../../2014/integration-services/create-a-new-integration-services-project.md)

 [<span data-ttu-id="f2e66-150">將項目加入 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="f2e66-150">Add an Item to an Integration Services Project</span></span>](../../2014/integration-services/add-an-item-to-an-integration-services-project.md)

 [<span data-ttu-id="f2e66-151">複製專案項目</span><span class="sxs-lookup"><span data-stu-id="f2e66-151">Copy Project Items</span></span>](../../2014/integration-services/copy-project-items.md)

## <a name="related-content"></a><span data-ttu-id="f2e66-152">相關內容</span><span class="sxs-lookup"><span data-stu-id="f2e66-152">Related Content</span></span>
 [<span data-ttu-id="f2e66-153">部署 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="f2e66-153">Development of an Integration Services Project</span></span>](../../2014/integration-services/development-of-an-integration-services-project.md)


