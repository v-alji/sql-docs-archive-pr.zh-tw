---
title: SSIS 設計師 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Integration Services, SSIS Designer
- Business Intelligence Development Studio, Integration Services in
- tools [Integration Services], SSIS Designer
- SSIS, SSIS Designer
- SSIS Designer, about SSIS Designer
- Integration Services, SSIS Designer
ms.assetid: 006d68ea-1b5c-4c1e-8079-3910288e012c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a54a3b445317c59582b8dedcb162e244fda1b58d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703157"
---
# <a name="ssis-designer"></a><span data-ttu-id="26d5e-102">SSIS 設計師</span><span class="sxs-lookup"><span data-stu-id="26d5e-102">SSIS Designer</span></span>
  [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="26d5e-103">設計師是可以用於建立及維護 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝的圖形工具。</span><span class="sxs-lookup"><span data-stu-id="26d5e-103">Designer is a graphical tool that you can use to create and maintain [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] packages.</span></span> [!INCLUDE[ssIS](../includes/ssis-md.md)]<span data-ttu-id="26d5e-104">[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 提供的設計師是 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案的一部分。</span><span class="sxs-lookup"><span data-stu-id="26d5e-104">Designer is available in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] as part of an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project.</span></span>

 <span data-ttu-id="26d5e-105">您可以使用「 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師」執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="26d5e-105">You can use [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to perform the following tasks:</span></span>

-   <span data-ttu-id="26d5e-106">建構封裝中的控制流程。</span><span class="sxs-lookup"><span data-stu-id="26d5e-106">Constructing the control flow in a package.</span></span>

-   <span data-ttu-id="26d5e-107">建構封裝中的資料流程。</span><span class="sxs-lookup"><span data-stu-id="26d5e-107">Constructing the data flows in a package.</span></span>

-   <span data-ttu-id="26d5e-108">將事件處理常式加入封裝和封裝物件。</span><span class="sxs-lookup"><span data-stu-id="26d5e-108">Adding event handlers to the package and package objects.</span></span>

-   <span data-ttu-id="26d5e-109">檢視封裝內容。</span><span class="sxs-lookup"><span data-stu-id="26d5e-109">Viewing the package content.</span></span>

-   <span data-ttu-id="26d5e-110">在執行階段，檢視封裝的執行進度。</span><span class="sxs-lookup"><span data-stu-id="26d5e-110">At run time, viewing the execution progress of the package.</span></span>

 <span data-ttu-id="26d5e-111">下圖顯示 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師與 [工具箱]  視窗。</span><span class="sxs-lookup"><span data-stu-id="26d5e-111">The following diagram shows [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer and the **Toolbox** window.</span></span>

 <span data-ttu-id="26d5e-112">![SSIS 設計師與工具箱的螢幕擷取畫面](media/denali-designerandtoolbox.gif "SSIS 設計師與工具箱的螢幕擷取畫面")</span><span class="sxs-lookup"><span data-stu-id="26d5e-112">![Screenshot of SSIS Designer and Toolbox](media/denali-designerandtoolbox.gif "Screenshot of SSIS Designer and Toolbox")</span></span>

 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="26d5e-113">包含用來在封裝中加入功能的其他對話方塊和視窗， [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 則提供用於設定開發環境及使用封裝的視窗和對話方塊。</span><span class="sxs-lookup"><span data-stu-id="26d5e-113">includes additional dialog boxes and windows for adding functionality to packages, and [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] provides windows and dialog boxes for configuring the development environment and working with packages.</span></span> <span data-ttu-id="26d5e-114">如需詳細資訊，請參閱 [Integration Services User Interface](integration-services-user-interface.md)(Integration Services 使用者介面)。</span><span class="sxs-lookup"><span data-stu-id="26d5e-114">For more information, see [Integration Services User Interface](integration-services-user-interface.md).</span></span>

 [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="26d5e-115">設計師不具有對 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 服務 (管理和監視封裝的服務) 的相依性，且不需要執行該服務即可在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師中建立或修改封裝。</span><span class="sxs-lookup"><span data-stu-id="26d5e-115">Designer has no dependency on the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] service, the service that manages and monitors packages, and it is not required that the service be running to create or modify packages in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="26d5e-116">不過，如果在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師處於開啟狀態時停止該服務，則將無法再開啟 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師所提供的對話方塊，同時您可能會接收到「RPC 伺服器無法使用」這樣的錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="26d5e-116">However, if you stop the service while [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer is open, you can no longer open the dialog boxes that [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer provides and you may receive the error message "RPC server is unavailable."</span></span> <span data-ttu-id="26d5e-117">若要重設 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師並繼續使用封裝，必須關閉設計師，結束 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]，然後重新開啟 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ([!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案) 和封裝。</span><span class="sxs-lookup"><span data-stu-id="26d5e-117">To reset [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer and continue working with the package, you must close the designer, exit [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], and then reopen [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project, and the package.</span></span>

## <a name="undo-and-redo"></a><span data-ttu-id="26d5e-118">復原和取消復原</span><span class="sxs-lookup"><span data-stu-id="26d5e-118">Undo and Redo</span></span>
 <span data-ttu-id="26d5e-119">您可以在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師中復原和取消復原最多可達 20 個動作。</span><span class="sxs-lookup"><span data-stu-id="26d5e-119">You can undo and redo up to 20 actions in the [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span> <span data-ttu-id="26d5e-120">針對封裝，[控制流程]  、[資料流程]  、[事件處理常式]  及 [參數]  索引標籤，以及 [變數]  視窗中可以進行復原/取消復原。</span><span class="sxs-lookup"><span data-stu-id="26d5e-120">For a package, undo /redo is available in the **Control Flow**, **Data Flow**, **Event Handlers**, and **Parameters** tabs, and in the **Variables** window.</span></span> <span data-ttu-id="26d5e-121">針對專案，則可以在 [專案參數]  視窗中進行復原/取消復原。</span><span class="sxs-lookup"><span data-stu-id="26d5e-121">For a project, undo/redo is available in the **Project Parameters** window.</span></span>

 <span data-ttu-id="26d5e-122">您無法復原和取消復原針對新 [SSIS 工具箱]  所做的變更。</span><span class="sxs-lookup"><span data-stu-id="26d5e-122">You can't undo/redo changes to the new **SSIS Toolbox**.</span></span>

 <span data-ttu-id="26d5e-123">使用元件編輯器針對元件進行變更時，您可以將變更做為一個組進行復原和取消復原，而不是針對個別變更進行復原和取消復原。</span><span class="sxs-lookup"><span data-stu-id="26d5e-123">When you make changes to a component using the component editor, you undo and redo the changes as a set rather than undoing and redoing individual changes.</span></span> <span data-ttu-id="26d5e-124">變更組在復原與取消復原下拉式清單中顯示為單一動作。</span><span class="sxs-lookup"><span data-stu-id="26d5e-124">The set of changes appears as a single action in the undo and redo drop-down list.</span></span>

 <span data-ttu-id="26d5e-125">若要復原某個動作，按一下 [復原] 工具列按鈕、[編輯/復原]  功能表項目，或按 CTRL + Z。</span><span class="sxs-lookup"><span data-stu-id="26d5e-125">To undo an action, click the undo toolbar button, **Edit/Undo** menu item, or press CTRL+Z.</span></span> <span data-ttu-id="26d5e-126">若要復原某個動作，請按一下 [復原] 工具列按鈕、[編輯/復原]  功能表項目，或按 CTRL + Y。按一下工具列按鈕旁的箭頭、反白顯示下拉式清單中的多個動作，然後在清單中按一下，可以復原和取消復原多個動作。</span><span class="sxs-lookup"><span data-stu-id="26d5e-126">To redo an action, click the redo toolbar button, **Edit/Redo** menu item or press CTRL + Y. You can undo and redo multiple actions, by clicking the arrow next to the toolbar button, highlighting multiple actions in the drop-down list, and then clicking in the list.</span></span>

## <a name="parts-of-the-ssis-designer"></a><span data-ttu-id="26d5e-127">SSIS 設計師的組件</span><span class="sxs-lookup"><span data-stu-id="26d5e-127">Parts of the SSIS Designer</span></span>
 [!INCLUDE[ssIS](../includes/ssis-md.md)] <span data-ttu-id="26d5e-128">設計師有五個永久的索引標籤：各有一個索引標籤用於建立封裝控制流程、資料流程、參數和事件處理常式，還有一個索引標籤用於檢視封裝的內容。</span><span class="sxs-lookup"><span data-stu-id="26d5e-128">Designer has five permanent tabs: one each for building package control flow, data flows, parameters, and event handlers, and one tab for viewing the contents of a package.</span></span> <span data-ttu-id="26d5e-129">在執行階段會出現第六個索引標籤，它會在封裝執行中顯示執行進度，並在完成時顯示執行結果。</span><span class="sxs-lookup"><span data-stu-id="26d5e-129">At run time a sixth tab appears that shows the execution progress of a package while it is running and the execution results after it finishes.</span></span>

 <span data-ttu-id="26d5e-130">此外， [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師還包含「連接管理員」區域，用於加入和設定由封裝用來連接到資料的連接管理員。</span><span class="sxs-lookup"><span data-stu-id="26d5e-130">In addition, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer includes the Connection Managers area for adding and configuring the connection managers that a package uses to connect to data.</span></span>

### <a name="control-flow-tab"></a><span data-ttu-id="26d5e-131">控制流程索引標籤</span><span class="sxs-lookup"><span data-stu-id="26d5e-131">Control Flow Tab</span></span>
 <span data-ttu-id="26d5e-132">您可以在 [控制流程]  索引標籤的設計介面上，建構封裝中的控制流程。請從 [工具箱]  將項目拖曳至設計介面，並透過按一下項目的圖示將其連接到控制流程中，然後從一個項目拖曳箭頭到另一個項目。</span><span class="sxs-lookup"><span data-stu-id="26d5e-132">You construct the control flow in a package on the design surface of the **Control Flow** tab. Drag items from **Toolbox** to the design surface and connect them into a control flow by clicking the icon for the item, and then dragging the arrow from one item to another.</span></span>

 <span data-ttu-id="26d5e-133">如需詳細資訊，請參閱 [控制流程](control-flow/control-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="26d5e-133">For more information, see [Control Flow](control-flow/control-flow.md).</span></span>

### <a name="data-flow-tab"></a><span data-ttu-id="26d5e-134">資料流程索引標籤</span><span class="sxs-lookup"><span data-stu-id="26d5e-134">Data Flow Tab</span></span>
 <span data-ttu-id="26d5e-135">如果封裝包含資料流程工作，您可以將資料流程加入封裝中。</span><span class="sxs-lookup"><span data-stu-id="26d5e-135">If a package contains a Data flow task, you can add data flows to the package.</span></span> <span data-ttu-id="26d5e-136">您可以在 [資料流程]  索引標籤的設計介面上，建構封裝中的資料流程。請從 [工具箱]  將項目拖曳至設計介面，並透過按一下項目的圖示將其連接到資料流程中，然後從一個項目拖曳箭頭到另一個項目。</span><span class="sxs-lookup"><span data-stu-id="26d5e-136">You construct the data flows in a package on the design surface of the **Data Flow** tab. Drag items from **Toolbox** to the design surface and connect them into a data flow by clicking the icon for the item, and then dragging the arrow from one item to another.</span></span>

 <span data-ttu-id="26d5e-137">如需詳細資訊，請參閱 [資料流程](data-flow/data-flow.md)。</span><span class="sxs-lookup"><span data-stu-id="26d5e-137">For more information, see [Data Flow](data-flow/data-flow.md).</span></span>

### <a name="parameters-tab"></a><span data-ttu-id="26d5e-138">參數索引標籤</span><span class="sxs-lookup"><span data-stu-id="26d5e-138">Parameters Tab</span></span>
 <span data-ttu-id="26d5e-139">Integration Services (SSIS) 參數可讓您在封裝執行時，將值指派給封裝內的屬性。</span><span class="sxs-lookup"><span data-stu-id="26d5e-139">Integration Services (SSIS) parameters allow you to assign values to properties within packages at the time of package execution.</span></span> <span data-ttu-id="26d5e-140">您可以在專案層級建立專案參數，並在封裝層級建立封裝參數。</span><span class="sxs-lookup"><span data-stu-id="26d5e-140">You can create project parameters at the project level and package parameters at the package level.</span></span> <span data-ttu-id="26d5e-141">專案參數可用於向專案中的一個或多個封裝提供專案接收的任何外部輸入。</span><span class="sxs-lookup"><span data-stu-id="26d5e-141">Project parameters are used to supply any external input the project receives to one or more packages in the project.</span></span> <span data-ttu-id="26d5e-142">封裝參數可讓您修改封裝執行，而不需要編輯和重新部署封裝。</span><span class="sxs-lookup"><span data-stu-id="26d5e-142">Package parameters allow you to modify package execution without having to edit and redeploy the package.</span></span> <span data-ttu-id="26d5e-143">此索引標籤可讓您管理封裝參數。</span><span class="sxs-lookup"><span data-stu-id="26d5e-143">This tab allows you to manage package parameters.</span></span>

 <span data-ttu-id="26d5e-144">如需參數的詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 參數](integration-services-ssis-package-and-project-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="26d5e-144">For more information about parameters, see [Integration Services &#40;SSIS&#41; Parameters](integration-services-ssis-package-and-project-parameters.md).</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="26d5e-145">參數只能用於針對專案部署模型而開發的專案。</span><span class="sxs-lookup"><span data-stu-id="26d5e-145">Parameters are available only to projects developed for the project deployment model.</span></span> <span data-ttu-id="26d5e-146">因此，僅對於屬於設定為使用專案部署模型之專案一部分的封裝，您才會看到 [參數] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="26d5e-146">Therefore, you will see the Parameters tab only for packages that are part of a project configured to use the project deployment model.</span></span>

### <a name="event-handlers-tab"></a><span data-ttu-id="26d5e-147">事件處理常式索引標籤</span><span class="sxs-lookup"><span data-stu-id="26d5e-147">Event Handlers Tab</span></span>
 <span data-ttu-id="26d5e-148">您可以在 [事件處理常式]  索引標籤的設計介面上，建構封裝中的事件。請在 [事件處理常式]  索引標籤上，選取要建立事件處理常式的封裝或封裝物件，然後選取要與事件處理常式產生關聯的事件。</span><span class="sxs-lookup"><span data-stu-id="26d5e-148">You construct the events in a package on the design surface of the **Event Handlers** tab. On the **Event Handlers** tab, you select the package or package object that you want to create an event handler for, and then select the event to associate with the event handler.</span></span> <span data-ttu-id="26d5e-149">事件處理常式具有控制流程和選擇性的資料流程。</span><span class="sxs-lookup"><span data-stu-id="26d5e-149">An event handler has a control flow and optional data flows.</span></span>

 <span data-ttu-id="26d5e-150">如需詳細資訊，請參閱 [Add an Event Handler to a Package](../../2014/integration-services/add-an-event-handler-to-a-package.md)(將事件處理常式加入封裝中)。</span><span class="sxs-lookup"><span data-stu-id="26d5e-150">For more information, see [Add an Event Handler to a Package](../../2014/integration-services/add-an-event-handler-to-a-package.md).</span></span>

### <a name="package-explorer-tab"></a><span data-ttu-id="26d5e-151">封裝總管索引標籤</span><span class="sxs-lookup"><span data-stu-id="26d5e-151">Package Explorer Tab</span></span>
 <span data-ttu-id="26d5e-152">封裝可能相當複雜，其中包括許多工作、連接管理員、變數和其他元素等。</span><span class="sxs-lookup"><span data-stu-id="26d5e-152">Packages can be complex, including many tasks, connection managers, variables, and other elements.</span></span> <span data-ttu-id="26d5e-153">封裝總管檢視可讓您查看封裝元素的完整清單。</span><span class="sxs-lookup"><span data-stu-id="26d5e-153">The explorer view of the package lets you see a complete list of package elements.</span></span>

 <span data-ttu-id="26d5e-154">如需詳細資訊，請參閱 [View Package Objects](view-package-objects.md)(檢視封裝物件)。</span><span class="sxs-lookup"><span data-stu-id="26d5e-154">For more information, see [View Package Objects](view-package-objects.md).</span></span>

#### <a name="progressexecution-result-tab"></a><span data-ttu-id="26d5e-155">進度/執行結果索引標籤</span><span class="sxs-lookup"><span data-stu-id="26d5e-155">Progress/Execution Result Tab</span></span>
 <span data-ttu-id="26d5e-156">當封裝正在執行時，[進度]  索引標籤會顯示封裝的執行進度。</span><span class="sxs-lookup"><span data-stu-id="26d5e-156">While a package is running, the **Progress** tab shows the execution progress of the package.</span></span> <span data-ttu-id="26d5e-157">在完成執行封裝後，執行結果會在 [執行結果]  索引標籤上保持可用。</span><span class="sxs-lookup"><span data-stu-id="26d5e-157">After the package has finished running, the execution results remain available on the **Execution Result** tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="26d5e-158">若要啟用或停用 **[進度]** 索引標籤上的訊息顯示，請在 **[SSIS]** 功能表上切換 **[偵錯進度報表]** 選項。</span><span class="sxs-lookup"><span data-stu-id="26d5e-158">To enable or disable the display of messages on the **Progress** tab, toggle the **Debug Progress Reporting** option on the **SSIS** menu.</span></span>

##### <a name="connection-managers-area"></a><span data-ttu-id="26d5e-159">連接管理員區域</span><span class="sxs-lookup"><span data-stu-id="26d5e-159">Connection Managers Area</span></span>
 <span data-ttu-id="26d5e-160">您可以在 [連線管理員]  區域中，加入及修改封裝所使用的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="26d5e-160">You add and modify the connection managers that a package uses in the **Connection Managers** area.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="26d5e-161">包含可以連接到各種不同的資料來源 (例如文字檔、OLE DB 資料庫及 .NET 提供者) 的連線管理員。</span><span class="sxs-lookup"><span data-stu-id="26d5e-161">includes connection managers to connect to a variety of data sources, such as text files, OLE DB databases, and .NET providers.</span></span>

 <span data-ttu-id="26d5e-162">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 連接](connection-manager/integration-services-ssis-connections.md)和[建立連接管理員](../../2014/integration-services/create-connection-managers.md)。</span><span class="sxs-lookup"><span data-stu-id="26d5e-162">For more information, see [Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md) and [Create Connection Managers](../../2014/integration-services/create-connection-managers.md).</span></span>

## <a name="related-tasks"></a><span data-ttu-id="26d5e-163">相關工作</span><span class="sxs-lookup"><span data-stu-id="26d5e-163">Related Tasks</span></span>

-   [<span data-ttu-id="26d5e-164">在 SQL Server Data Tools 中建立套件</span><span class="sxs-lookup"><span data-stu-id="26d5e-164">Create Packages in SQL Server Data Tools</span></span>](create-packages-in-sql-server-data-tools.md)

## <a name="see-also"></a><span data-ttu-id="26d5e-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="26d5e-165">See Also</span></span>
 [<span data-ttu-id="26d5e-166">Integration Services 使用者介面</span><span class="sxs-lookup"><span data-stu-id="26d5e-166">Integration Services User Interface</span></span>](integration-services-user-interface.md)


