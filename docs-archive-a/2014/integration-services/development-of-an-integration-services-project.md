---
title: Integration Services 專案的開發 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- projects [Integration Services], creating
- Integration Services projects, creating
- SQL Server Integration Services projects, creating
- SSIS projects, creating
ms.assetid: 6e90b016-36a5-415e-9440-a20199fffff0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: da648b3b09b25fa2a7b1cf886ad1bf770296f5ef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599607"
---
# <a name="development-of-an-integration-services-project"></a><span data-ttu-id="48269-102">部署 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="48269-102">Development of an Integration Services Project</span></span>
  <span data-ttu-id="48269-103">您可以將 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝加入專案。</span><span class="sxs-lookup"><span data-stu-id="48269-103">You add [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages to projects.</span></span> <span data-ttu-id="48269-104">若要建立及使用 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案，您必須安裝 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 環境。</span><span class="sxs-lookup"><span data-stu-id="48269-104">To create and work with [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] projects, you must install the [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] environment.</span></span> <span data-ttu-id="48269-105">如需詳細資訊，請參閱[安裝 Integration Services](install-windows/install-integration-services.md)。</span><span class="sxs-lookup"><span data-stu-id="48269-105">For more information, see [Install Integration Services](install-windows/install-integration-services.md).</span></span>  
  
 <span data-ttu-id="48269-106">當您在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中建立新的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案時，[新增專案]\*\*\*\* 對話方塊將包含 [Integration Services 專案]\*\*\*\* 範本。</span><span class="sxs-lookup"><span data-stu-id="48269-106">When you create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the **New Project** dialog box includes an **Integration Services Project** template.</span></span> <span data-ttu-id="48269-107">此專案範本會建立包含單一封裝的新專案。</span><span class="sxs-lookup"><span data-stu-id="48269-107">This project template creates a new project that contains a single package.</span></span>  
  
## <a name="projects-and-solutions"></a><span data-ttu-id="48269-108">專案和方案</span><span class="sxs-lookup"><span data-stu-id="48269-108">Projects and Solutions</span></span>  
 <span data-ttu-id="48269-109">專案會儲存在方案中。</span><span class="sxs-lookup"><span data-stu-id="48269-109">Projects are stored in solutions.</span></span> <span data-ttu-id="48269-110">您可以先建立方案，然後將 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案加入方案。</span><span class="sxs-lookup"><span data-stu-id="48269-110">You can create a solution first and then add an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project to the solution.</span></span> <span data-ttu-id="48269-111">如果沒有方案存在， [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 會在您第一次建立專案時自動為您建立一個方案。</span><span class="sxs-lookup"><span data-stu-id="48269-111">If no solution exists, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] automatically creates one for you when you first create the project.</span></span> <span data-ttu-id="48269-112">方案可以包含多個不同類型的專案。</span><span class="sxs-lookup"><span data-stu-id="48269-112">A solution can contain multiple projects of different types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="48269-113">依預設，當您在 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 中建立新的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案時，方案不會顯示在方案總管\*\*\*\* 窗格中。</span><span class="sxs-lookup"><span data-stu-id="48269-113">By default, when you create a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], the solution is not shown in the **Solution Explorer** pane.</span></span> <span data-ttu-id="48269-114">若要變更這個預設行為，請按一下 [工具]\*\*\*\* 功能表上的 [選項]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="48269-114">To change this default behavior, on the **Tools** menus, click **Options**.</span></span> <span data-ttu-id="48269-115">在 [選項]\*\*\*\* 對話方塊中，展開 [專案和方案]\*\*\*\*，然後按一下 [一般]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="48269-115">In the **Options** dialog box, expand **Projects and Solutions**, and then click **General**.</span></span> <span data-ttu-id="48269-116">在 [一般]\*\*\*\* 頁面上，選取 [永遠顯示方案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="48269-116">On the **General** page, select **Always show solution**.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="48269-117">相關工作</span><span class="sxs-lookup"><span data-stu-id="48269-117">Related Tasks</span></span>  
  
-   [<span data-ttu-id="48269-118">建立新的 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="48269-118">Create a New Integration Services Project</span></span>](../../2014/integration-services/create-a-new-integration-services-project.md)  
  
-   [<span data-ttu-id="48269-119">將項目加入 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="48269-119">Add an Item to an Integration Services Project</span></span>](../../2014/integration-services/add-an-item-to-an-integration-services-project.md)  
  
-   [<span data-ttu-id="48269-120">在方案中加入或移除 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="48269-120">Add or Remove an Integration Services Project in a Solution</span></span>](../../2014/integration-services/add-or-remove-an-integration-services-project-in-a-solution.md)  
  
  
