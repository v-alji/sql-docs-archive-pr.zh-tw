---
title: 在控制流程中新增或刪除工作或容器 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], adding
- adding tasks
- adding containers
- tasks [Integration Services], adding
ms.assetid: 653084c6-87a3-45d5-b458-914ecf24d56a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8338a4143358d732a974287e587f482dc5c36a22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596860"
---
# <a name="add-or-delete-a-task-or-a-container-in-a-control-flow"></a><span data-ttu-id="1cbc1-102">在控制流程中加入或刪除工作或容器</span><span class="sxs-lookup"><span data-stu-id="1cbc1-102">Add or Delete a Task or a Container in a Control Flow</span></span>
  <span data-ttu-id="1cbc1-103">當您在控制流程設計師中工作時，[ [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師] 中的 [工具箱] 會列出 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 提供用於在封裝中建立控制流程的工作。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-103">When you are working in the control flow designer, the Toolbox in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer lists the tasks that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides for building control flow in a package.</span></span> <span data-ttu-id="1cbc1-104">如需工具箱的詳細資訊，請參閱 [SSIS 工具箱](../ssis-toolbox.md)。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-104">For more information about the Toolbox, see [SSIS Toolbox](../ssis-toolbox.md).</span></span>  
  
 <span data-ttu-id="1cbc1-105">封裝可以包含同一工作的多個執行個體。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-105">A package can include multiple instances of the same task.</span></span> <span data-ttu-id="1cbc1-106">工作的每個執行個體都在封裝中唯一識別，且您可以對每個執行個體進行不同的設定。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-106">Each instance of a task is uniquely identified in the package, and you can configure each instance differently.</span></span>  
  
 <span data-ttu-id="1cbc1-107">如果您刪除工作，則亦會刪除將工作連接到控制流程中其他工作及容器的優先順序條件約束。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-107">If you delete a task, the precedence constraints that connect the task to other tasks and containers in the control flow are also deleted.</span></span>  
  
 <span data-ttu-id="1cbc1-108">下列程序將描述如何在封裝的控制流程中加入或刪除工作或容器。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-108">The following procedures describe how to add or delete a task or container in the control flow of a package.</span></span>  
  
### <a name="to-add-a-task-or-a-container-to-a-control-flow"></a><span data-ttu-id="1cbc1-109">將工作或容器加入控制流程</span><span class="sxs-lookup"><span data-stu-id="1cbc1-109">To add a task or a container to a control flow</span></span>  
  
1.  <span data-ttu-id="1cbc1-110">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-110">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="1cbc1-111">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-111">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="1cbc1-112">按一下 **[控制流程]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-112">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="1cbc1-113">若要開啟 [工具箱]，請按一下 [檢視] 功能表上的 [工具箱]。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-113">To open the **Toolbox**, click **Toolbox** on the **View** menu.</span></span>  
  
5.  <span data-ttu-id="1cbc1-114">展開 [控制流程項目]  和 [維護工作]  。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-114">Expand **Control Flow Items** and **Maintenance Tasks**.</span></span>  
  
6.  <span data-ttu-id="1cbc1-115">將工作和容器從 [工具箱]  拖曳至 [控制流程]  索引標籤的設計介面。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-115">Drag tasks and containers from the **Toolbox** to the design surface of the **Control Flow** tab.</span></span>  
  
7.  <span data-ttu-id="1cbc1-116">透過將其連接子拖曳至控制流程中的另一元件，連接封裝控制流程內的工作或容器。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-116">Connect a task or container within the package control flow by dragging its connector to another component in the control flow.</span></span>  
  
8.  <span data-ttu-id="1cbc1-117">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-117">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-delete-a-task-or-a-container-from-a-control-flow"></a><span data-ttu-id="1cbc1-118">從控制流程中刪除工作或容器</span><span class="sxs-lookup"><span data-stu-id="1cbc1-118">To delete a task or a container from a control flow</span></span>  
  
1.  <span data-ttu-id="1cbc1-119">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-119">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="1cbc1-120">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-120">In Solution Explorer, double-click the package to open it.</span></span> <span data-ttu-id="1cbc1-121">執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="1cbc1-121">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="1cbc1-122">按一下 [控制流程]  索引標籤，以滑鼠右鍵按一下您要移除的工作或容器，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-122">Click the **Control Flow** tab, right-click the task or container that you want to remove, and then click **Delete**.</span></span>  
  
    -   <span data-ttu-id="1cbc1-123">開啟 [封裝總管]  。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-123">Open **Package Explorer**.</span></span> <span data-ttu-id="1cbc1-124">從 [可執行檔]  資料夾，以滑鼠右鍵按一下您要移除的工作或容器，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-124">From the **Executables** folder, right-click the task or container that you want to remove, and then click **Delete**.</span></span>  
  
3.  <span data-ttu-id="1cbc1-125">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="1cbc1-125">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cbc1-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1cbc1-126">See Also</span></span>  
 <span data-ttu-id="1cbc1-127">[Integration Services 工作](integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="1cbc1-127">[Integration Services Tasks](integration-services-tasks.md) </span></span>  
 <span data-ttu-id="1cbc1-128">[Integration Services 容器](integration-services-containers.md) </span><span class="sxs-lookup"><span data-stu-id="1cbc1-128">[Integration Services Containers](integration-services-containers.md) </span></span>  
 [<span data-ttu-id="1cbc1-129">控制流程</span><span class="sxs-lookup"><span data-stu-id="1cbc1-129">Control Flow</span></span>](control-flow.md)  
  
  
