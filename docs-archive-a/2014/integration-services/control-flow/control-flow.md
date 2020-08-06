---
title: 控制流程 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- control flow [Integration Services], elements
- SSIS control flow elements
- SQL Server Integration Services control flow elements
ms.assetid: 0cc042a9-1a7f-49ed-9f47-091653d5ef6e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 81ace5d285a67c6fee8a3a568ed89bc564193c42
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595224"
---
# <a name="control-flow"></a><span data-ttu-id="e0e1a-102">控制流程</span><span class="sxs-lookup"><span data-stu-id="e0e1a-102">Control Flow</span></span>
  <span data-ttu-id="e0e1a-103">封裝由控制流程及選擇性的一個或多個資料流程所組成。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-103">A package consists of a control flow and, optionally, one or more data flows.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e0e1a-104">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 提供三種不同類型的控制流程項目，分別是提供套件中結構的容器、提供功能的工作，以及將可執行檔、容器與工作連線成一個排序控制流程的優先順序條件約束。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-104">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] provides three different types of control flow elements: containers that provide structures in packages, tasks that provide functionality, and precedence constraints that connect the executables, containers, and tasks into an ordered control flow.</span></span>

 <span data-ttu-id="e0e1a-105">如需相關資訊，請參閱 [Precedence Constraints](precedence-constraints.md)、 [Integration Services Containers](integration-services-containers.md)及 [Integration Services Tasks](integration-services-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-105">For more information, see [Precedence Constraints](precedence-constraints.md), [Integration Services Containers](integration-services-containers.md), and [Integration Services Tasks](integration-services-tasks.md).</span></span>

 <span data-ttu-id="e0e1a-106">下圖顯示具有一個容器和六個工作的控制流程。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-106">The following diagram shows a control flow that has one container and six tasks.</span></span> <span data-ttu-id="e0e1a-107">其中五個工作是在封裝層級定義，另外有一個工作是在容器層級定義，</span><span class="sxs-lookup"><span data-stu-id="e0e1a-107">Five of the tasks are defined at the package level, and one task is defined at the container level.</span></span> <span data-ttu-id="e0e1a-108">該工作會位在容器內。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-108">The task is inside a container.</span></span>

 <span data-ttu-id="e0e1a-109">![具有六個工作和一個容器的控制流程](../media/ssis-controlflowelmt.gif "具有六個工作和一個容器的控制流程")</span><span class="sxs-lookup"><span data-stu-id="e0e1a-109">![Control flow with six tasks and a container](../media/ssis-controlflowelmt.gif "Control flow with six tasks and a container")</span></span>

 <span data-ttu-id="e0e1a-110">[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 架構支援巢狀容器，且控制流程中可包含多個層級的巢狀容器。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-110">The [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] architecture supports the nesting of containers, and a control flow can include multiple levels of nested containers.</span></span> <span data-ttu-id="e0e1a-111">例如，封裝中可以包含諸如「Foreach 迴圈」容器，而該容器中可再包含另一個「Foreach 迴圈」容器，依此類推。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-111">For example, a package could contain a container such as a Foreach Loop container, which in turn could contain another Foreach Loop container and so on.</span></span>

 <span data-ttu-id="e0e1a-112">事件處理常式也有控制流程，而且是使用相同類型的控制流程元素來建立。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-112">Event handlers also have control flows, which are built using the same kinds of control flow elements.</span></span>

## <a name="control-flow-implementation"></a><span data-ttu-id="e0e1a-113">控制流程實作</span><span class="sxs-lookup"><span data-stu-id="e0e1a-113">Control Flow Implementation</span></span>
 <span data-ttu-id="e0e1a-114">您可以使用 **設計師的** [控制流程] [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 索引標籤，在封裝中建立控制流程。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-114">You create the control flow in a package by using the **Control Flow** tab in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="e0e1a-115">當 **[控制流程]** 索引標籤作用中時，工具箱內會包含可加入控制流程的工作和容器。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-115">When the **Control Flow** tab is active, the Toolbox lists the tasks and containers that you can add to the control flow.</span></span>

 <span data-ttu-id="e0e1a-116">下圖顯示控制流程設計師中某個簡單封裝的控制流程。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-116">The following diagram shows the control flow of a simple package in the control flow designer.</span></span> <span data-ttu-id="e0e1a-117">圖中顯示的控制流程由三個封裝層級的工作，和包含這三個工作的一個封裝層級容器組成。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-117">The control flow shown in the diagram is made up of three package-level tasks and one package-level container that contains three tasks.</span></span> <span data-ttu-id="e0e1a-118">使用優先順序條件約束連接工作與容器。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-118">The tasks and container are connected by using precedence constraints.</span></span>

 <span data-ttu-id="e0e1a-119">![具有套件的控制流程設計師螢幕擷取畫面](../media/samplecontrolflow.gif "具有套件的控制流程設計師螢幕擷取畫面")</span><span class="sxs-lookup"><span data-stu-id="e0e1a-119">![Screenshot of control flow designer with package](../media/samplecontrolflow.gif "Screenshot of control flow designer with package")</span></span>

 <span data-ttu-id="e0e1a-120">建立控制流程包括下列工作：</span><span class="sxs-lookup"><span data-stu-id="e0e1a-120">Creating a control flow includes the following tasks:</span></span>

-   <span data-ttu-id="e0e1a-121">加入容器，該容器可以實作封裝中重複的工作流程，或將一個控制流程分割成幾個子集。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-121">Adding containers that implement repeating workflows in a package or divide a control flow into subsets.</span></span>

-   <span data-ttu-id="e0e1a-122">加入工作，該工作可支援資料流程、準備資料、執行工作流程和商業智慧功能，以及實作指令碼。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-122">Adding tasks that support data flow, prepare data, perform workflow and business intelligence functions, and implement script.</span></span>

     [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="e0e1a-123">包括各種工作，您可使用這些工作建立滿足封裝商務需求的控制流程。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-123">includes a variety of tasks that you can use to create control flow that meets the business requirements of the package.</span></span> <span data-ttu-id="e0e1a-124">如果封裝必須使用資料，則控制流程必須至少包含一個「資料流程」工作。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-124">If the package has to work with data, the control flow must include at least one Data Flow task.</span></span> <span data-ttu-id="e0e1a-125">例如，封裝可能必須擷取資料、彙總資料值，然後將結果寫入資料來源。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-125">For example, a package might have to extract data, aggregate data values, and then write the results to a data source.</span></span>  <span data-ttu-id="e0e1a-126">如需詳細資訊，請參閱 [Integration Services 工作](integration-services-tasks.md) 和 [在控制流程中加入或刪除工作或容器](add-or-delete-a-task-or-a-container-in-a-control-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-126">For more information, see [Integration Services Tasks](integration-services-tasks.md) and [Add or Delete a Task or a Container in a Control Flow](add-or-delete-a-task-or-a-container-in-a-control-flow.md).</span></span>

-   <span data-ttu-id="e0e1a-127">使用優先順序條件約束將容器與工作連接成一個排序控制流程。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-127">Connecting containers and tasks into an ordered control flow by using precedence constraints.</span></span>

     <span data-ttu-id="e0e1a-128">將工作或容器加入 **[控制流程]** 索引標籤的設計介面後， [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師會自動將連接子加入該項目。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-128">After you add a task or container to the design surface of the **Control Flow** tab, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer automatically adds a connector to the item.</span></span> <span data-ttu-id="e0e1a-129">如果封裝包括兩個以上的項目、工作或容器，則您可透過將它們的連接子從一個項目拖曳至另一個項目，來將其聯結到控制流程中。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-129">If a package includes two or more items, tasks or containers, you can join them into a control flow by dragging their connectors from one item to another.</span></span>

     <span data-ttu-id="e0e1a-130">兩個項目之間的連接子代表一個優先順序條件約束。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-130">The connector between two items represents a precedence constraint.</span></span> <span data-ttu-id="e0e1a-131">優先順序條件約束定義兩個已連接項目之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-131">A precedence constraint defines the relationship between the two connected items.</span></span> <span data-ttu-id="e0e1a-132">它指定在執行階段工作與容器的執行順序，以及執行工作與容器的條件約束。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-132">It specifies the order in which tasks and containers are executed at run time and the conditions under which tasks and containers run.</span></span> <span data-ttu-id="e0e1a-133">例如，優先順序條件約束可以指定某個工作必須成功，然後才可以執行控制流程中的下一個工作。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-133">For example, a precedence constraint can specify that a task must succeed for the next task in the control flow to run.</span></span> <span data-ttu-id="e0e1a-134">如需詳細資訊，請參閱 [優先順序條件約束](precedence-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-134">For more information, see [Precedence Constraints](precedence-constraints.md).</span></span>

-   <span data-ttu-id="e0e1a-135">加入連接管理員。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-135">Adding connection managers.</span></span>

     <span data-ttu-id="e0e1a-136">許多工作都需要連接到資料來源，因此您必須將工作所需的連接管理員加入封裝。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-136">Many tasks require a connection to a data source, and you have to add the connection managers that the task requires to the package.</span></span> <span data-ttu-id="e0e1a-137">視其使用的列舉值類型而定，「Foreach 迴圈」容器也可能需要連接管理員。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-137">Depending on the enumerator type it uses, the Foreach Loop container may also require a connection manager.</span></span> <span data-ttu-id="e0e1a-138">您可以在逐項建構控制流程時，或在開始建構控制流程之前加入連接管理員。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-138">You can add the connection managers as you construct the control flow item by item or before you start to construct the control flow.</span></span> <span data-ttu-id="e0e1a-139">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 連接](../connection-manager/integration-services-ssis-connections.md)和[建立連接管理員](../create-connection-managers.md)。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-139">For more information, see [Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md) and [Create Connection Managers](../create-connection-managers.md).</span></span>

 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="e0e1a-140">設計工具還包括許多設計階段功能，您可以使用這些功能管理設計介面，並使控制流程可以自我記錄。</span><span class="sxs-lookup"><span data-stu-id="e0e1a-140">Designer also includes many design-time features that you can use to manage the design surface and make the control flow self-documenting.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="e0e1a-141">相關工作</span><span class="sxs-lookup"><span data-stu-id="e0e1a-141">Related Tasks</span></span>

-   [<span data-ttu-id="e0e1a-142">在控制流程中新增或刪除工作或容器</span><span class="sxs-lookup"><span data-stu-id="e0e1a-142">Add or Delete a Task or a Container in a Control Flow</span></span>](add-or-delete-a-task-or-a-container-in-a-control-flow.md)

-   [<span data-ttu-id="e0e1a-143">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="e0e1a-143">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)

-   [<span data-ttu-id="e0e1a-144">建立或取消元件的群組</span><span class="sxs-lookup"><span data-stu-id="e0e1a-144">Group or Ungroup Components</span></span>](../group-or-ungroup-components.md)


