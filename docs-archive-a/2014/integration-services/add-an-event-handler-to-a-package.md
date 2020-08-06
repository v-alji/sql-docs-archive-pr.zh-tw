---
title: 將事件處理常式新增至封裝 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- event handlers [Integration Services], creating
ms.assetid: 5e56885d-8658-480a-bed9-3f2f8003fd78
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 007d81a395e06ac5a97210cd3e3ed6eea91aee57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595261"
---
# <a name="add-an-event-handler-to-a-package"></a><span data-ttu-id="633d2-102">將事件處理常式加入封裝中</span><span class="sxs-lookup"><span data-stu-id="633d2-102">Add an Event Handler to a Package</span></span>
  <span data-ttu-id="633d2-103">在執行階段，容器及工作會引發事件。</span><span class="sxs-lookup"><span data-stu-id="633d2-103">At run time, containers and tasks raise events.</span></span> <span data-ttu-id="633d2-104">藉由在引發事件時執行工作流程，您可以建立自訂事件處理常式，以回應這些事件。</span><span class="sxs-lookup"><span data-stu-id="633d2-104">You can create custom event handlers that respond to these events by running a workflow when the event is raised.</span></span> <span data-ttu-id="633d2-105">例如，您可以建立在工作失敗時傳送電子郵件訊息的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="633d2-105">For example, you can create an event handler that sends an e-mail message when a task fails.</span></span>  
  
 <span data-ttu-id="633d2-106">事件處理常式與封裝相似。</span><span class="sxs-lookup"><span data-stu-id="633d2-106">An event handler is similar to a package.</span></span> <span data-ttu-id="633d2-107">事件處理常式與封裝相似，可提供變數的範圍，並包括控制流程和選擇性的資料流程。</span><span class="sxs-lookup"><span data-stu-id="633d2-107">Like a package, an event handler can provide scope for variables, and includes a control flow and optional data flows.</span></span> <span data-ttu-id="633d2-108">您可以為封裝、「Foreach 迴圈」容器、「For 迴圈」容器、「時序」容器及所有工作建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="633d2-108">You can build event handlers for packages, the Foreach Loop container, the For Loop container, the Sequence container, and all tasks.</span></span>  
  
 <span data-ttu-id="633d2-109">您可以使用 [!INCLUDE[ssIS](../includes/ssis-md.md)]設計師中 [事件處理常式]\*\*\*\* 索引標籤的設計介面，來建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="633d2-109">You create event handlers by using the design surface of the **Event Handlers** tab in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>  
  
 <span data-ttu-id="633d2-110">當 [事件處理常式]\*\*\*\* 索引標籤為使用中時，[!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師中 [工具箱] 的 [控制流程項目]\*\*\*\* 和 [維護計畫工作]\*\*\*\* 節點，會包含用於在事件處理常式中建立控制流程的工作及容器。</span><span class="sxs-lookup"><span data-stu-id="633d2-110">When the **Event Handlers** tab is active, the **Control Flow Items** and **Maintenance Plan Tasks** nodes of the Toolbox in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer contain the task and containers for building the control flow in the event handler.</span></span> <span data-ttu-id="633d2-111">[資料流程來源]\*\*\*\*、[轉換]\*\*\*\* 及 [資料流程目的地]\*\*\*\* 節點包含用於在事件處理常式中建立資料流程的資料來源、轉換及目的地。</span><span class="sxs-lookup"><span data-stu-id="633d2-111">The **Data Flow Sources**, **Transformations**, **and Data Flow Destinations** nodes contain the data sources, transformations, and destinations for building the data flows in the event handler.</span></span> <span data-ttu-id="633d2-112">如需詳細資訊，請參閱[控制流程](control-flow/control-flow.md)和[資料流程](data-flow/data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="633d2-112">For more information, see [Control Flow](control-flow/control-flow.md) and [Data Flow](data-flow/data-flow.md).</span></span>  
  
 <span data-ttu-id="633d2-113">[事件處理常式]\*\*\*\* 索引標籤還包含 [連線管理員]\*\*\*\* 區域，在此區域中，您可以建立並修改事件處理常式用於連接到伺服器和資料來源的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="633d2-113">The **Event Handlers** tab also includes the **Connections** Managers area where you can create and modify the connection managers that event handlers use to connect to servers and data sources.</span></span> <span data-ttu-id="633d2-114">如需詳細資訊，請參閱[建立連線管理員](../../2014/integration-services/create-connection-managers.md)。</span><span class="sxs-lookup"><span data-stu-id="633d2-114">For more information, see [Create Connection Managers](../../2014/integration-services/create-connection-managers.md).</span></span>  
  
### <a name="to-create-an-event-handler"></a><span data-ttu-id="633d2-115">建立事件處理常式</span><span class="sxs-lookup"><span data-stu-id="633d2-115">To create an event handler</span></span>  
  
1.  <span data-ttu-id="633d2-116">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="633d2-116">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="633d2-117">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="633d2-117">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="633d2-118">按一下 [事件處理常式]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="633d2-118">Click the **Event Handlers** tab.</span></span>  
  
     <span data-ttu-id="633d2-119">![含事件處理常式的設計介面螢幕擷取畫面](media/eventhandlers.gif "含事件處理常式的設計介面螢幕擷取畫面")</span><span class="sxs-lookup"><span data-stu-id="633d2-119">![Screenshot of design surface with event handler](media/eventhandlers.gif "Screenshot of design surface with event handler")</span></span>  
  
     <span data-ttu-id="633d2-120">在事件處理常式中建立控制流程和資料流程，與在封裝中建立控制流程和資料流程相似。</span><span class="sxs-lookup"><span data-stu-id="633d2-120">Creating the control flow and data flows in an event handler is similar to creating the control flow and data flows in a package.</span></span> <span data-ttu-id="633d2-121">如需詳細資訊，請參閱[控制流程](control-flow/control-flow.md)和[資料流程](data-flow/data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="633d2-121">For more information, see [Control Flow](control-flow/control-flow.md) and [Data Flow](data-flow/data-flow.md).</span></span>  
  
4.  <span data-ttu-id="633d2-122">在 [可執行檔]\*\*\*\* 清單中，選取要為其建立事件處理常式的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="633d2-122">In the **Executable** list, select the executable for which you want to create an event handler.</span></span>  
  
5.  <span data-ttu-id="633d2-123">在 [事件處理常式]\*\*\*\* 清單中，選取要建立的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="633d2-123">In the **Event handler** list, select the event handler you want to build.</span></span>  
  
6.  <span data-ttu-id="633d2-124">按一下 [事件處理常式]\*\*\*\* 索引標籤之設計介面上的連結。</span><span class="sxs-lookup"><span data-stu-id="633d2-124">Click the link on the design surface of the **Event Handler** tab.</span></span>  
  
7.  <span data-ttu-id="633d2-125">將控制流程項目加入事件處理常式，並使用優先順序條件約束連接項目，方法是將條件約束從一個控制流程項目拖曳到另一個控制流程項目。</span><span class="sxs-lookup"><span data-stu-id="633d2-125">Add control flow items to the event handler, and connect items using a precedence constraint by dragging the constraint from one control flow item to another.</span></span> <span data-ttu-id="633d2-126">如需詳細資訊，請參閱 [控制流程](control-flow/control-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="633d2-126">For more information, see [Control Flow](control-flow/control-flow.md).</span></span>  
  
8.  <span data-ttu-id="633d2-127">選擇性地加入「資料流程」工作，並在 [資料流程]\*\*\*\* 索引標籤的設計介面上，為事件處理常式建立資料流程。</span><span class="sxs-lookup"><span data-stu-id="633d2-127">Optionally, add a Data Flow task, and on the design surface of the **Data Flow** tab, create a data flow for the event handler.</span></span> <span data-ttu-id="633d2-128">如需詳細資訊，請參閱 [資料流程](data-flow/data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="633d2-128">For more information, see [Data Flow](data-flow/data-flow.md).</span></span>  
  
9. <span data-ttu-id="633d2-129">在 [檔案]\*\*\*\* 功能表上，按一下 [儲存選取項目]\*\*\*\*，以儲存封裝。</span><span class="sxs-lookup"><span data-stu-id="633d2-129">On the **File** menu, click **Save Selected Items** to save the package.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="633d2-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="633d2-130">See Also</span></span>  
 <span data-ttu-id="633d2-131">[SQL Server Integration Services](../../2014/integration-services/sql-server-integration-services.md) </span><span class="sxs-lookup"><span data-stu-id="633d2-131">[SQL Server Integration Services](../../2014/integration-services/sql-server-integration-services.md) </span></span>  
 [<span data-ttu-id="633d2-132">Integration Services &#40;SSIS&#41; 記錄</span><span class="sxs-lookup"><span data-stu-id="633d2-132">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
