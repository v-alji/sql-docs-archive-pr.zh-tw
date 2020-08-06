---
title: 在方案中新增或移除 Integration Services 專案 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding projects
- Integration Services projects, adding
- SQL Server Integration Services projects, adding
- SSIS projects, adding
- projects [Integration Services], adding
ms.assetid: f01f6475-b63c-41dc-82ac-b62162b3adf7
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 49984c61047a6b716015bd72e518b73cb08b3226
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584703"
---
# <a name="add-or-remove-an-integration-services-project-in-a-solution"></a><span data-ttu-id="44c0a-102">在方案中加入或移除 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="44c0a-102">Add or Remove an Integration Services Project in a Solution</span></span>
  <span data-ttu-id="44c0a-103">下列程序將描述如何在方案中加入或移除 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="44c0a-103">The following procedures descibe how to add or remove an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project in a solution.</span></span>  
  
 <span data-ttu-id="44c0a-104">只有當您可以在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中看到方案時，才能將專案加入至現有的方案，或從方案中移除專案。</span><span class="sxs-lookup"><span data-stu-id="44c0a-104">You can only add a project to an existing solution, or remove a project from a solution, when the solution is visible in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="44c0a-105">如果您已在中選取 [**永遠顯示方案**] 選項 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] ， [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 則會顯示方案，即使該方案僅包含一個專案也一樣。</span><span class="sxs-lookup"><span data-stu-id="44c0a-105">If you have selected the **Always show solution** option in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] will display a solution even when that solution contains only one project.</span></span> <span data-ttu-id="44c0a-106">否則，只有當方案包含多個專案時，[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 才會顯示該方案。</span><span class="sxs-lookup"><span data-stu-id="44c0a-106">Otherwise, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] will display a solution only when that solution contains more than one project.</span></span> <span data-ttu-id="44c0a-107">其他專案可以是 [!INCLUDE[ssIS](../includes/ssis-md.md)] 專案或其他類型的專案。</span><span class="sxs-lookup"><span data-stu-id="44c0a-107">The additional projects can be either [!INCLUDE[ssIS](../includes/ssis-md.md)] projects or projects of other types.</span></span>  
  
## <a name="adding-an-integration-services-project"></a><span data-ttu-id="44c0a-108">加入 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="44c0a-108">Adding an Integration Services Project</span></span>  
 <span data-ttu-id="44c0a-109">當您加入專案時，可以讓 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 建立全新的空白專案，也可以加入已經針對不同方案建立的專案。</span><span class="sxs-lookup"><span data-stu-id="44c0a-109">When you add a project, you can have [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] create a new, blank project, or you can add a project that you have already created for a different solution.</span></span> <span data-ttu-id="44c0a-110">只有當您可以在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中看到方案時，才能將專案加入至現有的方案。</span><span class="sxs-lookup"><span data-stu-id="44c0a-110">You can only add a project to an existing solution when the solution is visible in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
#### <a name="to-add-a-new-integration-services-project-to-a-solution"></a><span data-ttu-id="44c0a-111">將新的 Integration Services 專案加入至方案</span><span class="sxs-lookup"><span data-stu-id="44c0a-111">To add a new Integration Services project to a solution</span></span>  
  
1.  <span data-ttu-id="44c0a-112">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，開啟您要在其中加入新 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案的方案，並執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="44c0a-112">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution to which you want to add a new [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="44c0a-113">以滑鼠右鍵按一下方案，再按一下 [加入]\*\*\*\*，然後按一下 [新增專案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="44c0a-113">Right-click the solution, click **Add**, and then click **New Project**.</span></span>  
  
    -   <span data-ttu-id="44c0a-114">在 [檔案]\*\*\*\* 功能表上，指向 [加入]\*\*\*\*，然後按一下 [新增專案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="44c0a-114">On the **File** menu, point to **Add**, and then click **New Project**.</span></span>  
  
2.  <span data-ttu-id="44c0a-115">在 [加入新專案]\*\*\*\* 對話方塊中，按一下 [範本]\*\*\*\* 窗格內的 [Integration Services 專案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="44c0a-115">In the **Add New Project** dialog box, click **Integration Services Project** in the **Templates** pane.</span></span>  
  
3.  <span data-ttu-id="44c0a-116">(選擇性) 編輯專案名稱及位置。</span><span class="sxs-lookup"><span data-stu-id="44c0a-116">Optionally, edit the project name and location.</span></span>  
  
4.  <span data-ttu-id="44c0a-117">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="44c0a-117">Click **OK**.</span></span>  
  
#### <a name="to-add-an-existing-integration-services-project-to-a-solution"></a><span data-ttu-id="44c0a-118">將現有的 Integration Services 專案加入方案</span><span class="sxs-lookup"><span data-stu-id="44c0a-118">To add an existing Integration Services project to a solution</span></span>  
  
1.  <span data-ttu-id="44c0a-119">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，開啟您要在其中加入現有 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案的方案，並執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="44c0a-119">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution to which you want to add an existing [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, and do one of the following:</span></span>  
  
    -   <span data-ttu-id="44c0a-120">以滑鼠右鍵按一下方案，指向 [加入]\*\*\*\*，然後按一下 [現有專案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="44c0a-120">Right-click the solution, point to **Add**, and then click **Existing Project**.</span></span>  
  
    -   <span data-ttu-id="44c0a-121">在 [檔案]\*\*\*\* 功能表上，按一下 [加入]\*\*\*\*，然後按一下 [現有專案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="44c0a-121">On the **File** menu, click **Add**, and then click **Existing Project**.</span></span>  
  
2.  <span data-ttu-id="44c0a-122">在 [加入現有專案]\*\*\*\* 對話方塊中，瀏覽以找出您要加入的專案，然後按一下 [開啟]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="44c0a-122">In the **Add Existing Project** dialog box, browse to locate the project you want to add, and then click **Open**.</span></span>  
  
3.  <span data-ttu-id="44c0a-123">專案會加入方案總管\*\*\*\* 中的方案資料夾。</span><span class="sxs-lookup"><span data-stu-id="44c0a-123">The project is added to the solution folder in **Solution Explorer**.</span></span>  
  
## <a name="removing-an-integration-services-project"></a><span data-ttu-id="44c0a-124">移除 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="44c0a-124">Removing an Integration Services Project</span></span>  
 <span data-ttu-id="44c0a-125">只有當您可以在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中看到方案時，才能從方案中移除專案。</span><span class="sxs-lookup"><span data-stu-id="44c0a-125">You can only remove a project from a solution when the solution is visible in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="44c0a-126">看見方案之後，您就可以只保留一個專案，並移除其他所有專案。</span><span class="sxs-lookup"><span data-stu-id="44c0a-126">After the solution is visible, you can remove all except one project.</span></span> <span data-ttu-id="44c0a-127">等到只剩下一個專案之後，[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 就不會再顯示方案資料夾，而且您也不能移除最後一個專案。</span><span class="sxs-lookup"><span data-stu-id="44c0a-127">As soon as only one project remains, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] no longer displays the solution folder and you cannot remove the last project.</span></span>  
  
#### <a name="to-remove-an-integration-services-project-from-a-solution"></a><span data-ttu-id="44c0a-128">從方案中移除 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="44c0a-128">To remove an Integration Services project from a solution</span></span>  
  
1.  <span data-ttu-id="44c0a-129">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，開啟您要從中移除 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案的方案。</span><span class="sxs-lookup"><span data-stu-id="44c0a-129">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution from which you want to remove an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="44c0a-130">在方案總管中，以滑鼠右鍵按一下專案，然後按一下 [卸載專案]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="44c0a-130">In Solution Explorer, right-click the project, and then click **Unload Project**.</span></span>  
  
3.  <span data-ttu-id="44c0a-131">按一下 [確定]\*\*\*\* 以確認移除。</span><span class="sxs-lookup"><span data-stu-id="44c0a-131">Click **OK** to confirm the removal.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44c0a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44c0a-132">See Also</span></span>  
 <span data-ttu-id="44c0a-133">[Integration Services &#40;SSIS&#41; 專案](integration-services-ssis-projects-and-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="44c0a-133">[Integration Services &#40;SSIS&#41; Projects](integration-services-ssis-projects-and-solutions.md) </span></span>  
 [<span data-ttu-id="44c0a-134">建立新的 Integration Services 專案</span><span class="sxs-lookup"><span data-stu-id="44c0a-134">Create a New Integration Services Project</span></span>](../../2014/integration-services/create-a-new-integration-services-project.md)  
  
  
