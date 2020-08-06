---
title: Integration Services (SSIS) 事件處理常式 | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, events
- run-time [Integration Services]
- SQL Server Integration Services packages, events
- event handlers [Integration Services], about event handlers
- events [Integration Services]
- packages [Integration Services], events
- event handlers [Integration Services]
- SSIS packages, events
- containers [Integration Services], events
- events [Integration Services], about events
ms.assetid: 6f60cf93-35dc-431c-908d-2049c4ab66ba
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 78bcd6579aa8306c89fd9530fad3557ac57f102a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596169"
---
# <a name="integration-services-ssis-event-handlers"></a><span data-ttu-id="92607-102">Integration Services (SSIS) 事件處理常式</span><span class="sxs-lookup"><span data-stu-id="92607-102">Integration Services (SSIS) Event Handlers</span></span>
  <span data-ttu-id="92607-103">在執行階段，可執行檔 (封裝和「Foreach 迴圈」、「For 迴圈」、「時序」，以及工作主機容器) 會引發事件。</span><span class="sxs-lookup"><span data-stu-id="92607-103">At run time, executables (packages and Foreach Loop, For Loop, Sequence, and task host containers) raise events.</span></span> <span data-ttu-id="92607-104">例如，當發生錯誤時，會引發 OnError 事件。</span><span class="sxs-lookup"><span data-stu-id="92607-104">For example, an OnError event is raised when an error occurs.</span></span> <span data-ttu-id="92607-105">您可以建立這些事件的自訂事件處理常式，以擴充封裝功能，並使封裝在執行階段易於管理。</span><span class="sxs-lookup"><span data-stu-id="92607-105">You can create custom event handlers for these events to extend package functionality and make packages easier to manage at run time.</span></span> <span data-ttu-id="92607-106">事件處理常式可以執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="92607-106">Event handlers can perform tasks such as the following:</span></span>

-   <span data-ttu-id="92607-107">封裝或工作完成執行後，清除暫存資料儲存。</span><span class="sxs-lookup"><span data-stu-id="92607-107">Clean up temporary data storage when a package or task finishes running.</span></span>

-   <span data-ttu-id="92607-108">擷取系統資訊，以在封裝執行之前評估資源可用性。</span><span class="sxs-lookup"><span data-stu-id="92607-108">Retrieve system information to assess resource availability before a package runs.</span></span>

-   <span data-ttu-id="92607-109">當查閱參考資料表失敗時，重新整理資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="92607-109">Refresh data in a table when a lookup in a reference table fails.</span></span>

-   <span data-ttu-id="92607-110">當發生錯誤或警告時，或工作失敗時，傳送電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="92607-110">Send an e-mail message when an error or a warning occurs or when a task fails.</span></span>

 <span data-ttu-id="92607-111">如果事件不具有事件處理常式，則該事件會被提升到封裝中容器階層上的下一個容器。</span><span class="sxs-lookup"><span data-stu-id="92607-111">If an event has no event handler, the event is raised to the next container up the container hierarchy in a package.</span></span> <span data-ttu-id="92607-112">如果此容器具有事件處理常式，則會執行事件處理常式，以回應該事件。</span><span class="sxs-lookup"><span data-stu-id="92607-112">If this container has an event handler, the event handler runs in response to the event.</span></span> <span data-ttu-id="92607-113">若否，則該事件會被提升到容器階層上的下一個容器。</span><span class="sxs-lookup"><span data-stu-id="92607-113">If not, the event is raised to the next container up the container hierarchy.</span></span>

 <span data-ttu-id="92607-114">下圖顯示一個具有「For 迴圈」容器的簡單封裝，該容器包含一個「執行 SQL」工作。</span><span class="sxs-lookup"><span data-stu-id="92607-114">The following diagram shows a simple package that has a For Loop container that contains one Execute SQL task.</span></span>

 <span data-ttu-id="92607-115">![套件、For 迴圈、工作主機和執行 SQL 工作](media/mw-dts-eventhandlerpkg.gif "套件、For 迴圈、工作主機和執行 SQL 工作")</span><span class="sxs-lookup"><span data-stu-id="92607-115">![Package, For Loop, task host, and Execute SQL task](media/mw-dts-eventhandlerpkg.gif "Package, For Loop, task host, and Execute SQL task")</span></span>

 <span data-ttu-id="92607-116">針對其 `OnError` 事件，僅封裝具有事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="92607-116">Only the package has an event handler, for its `OnError` event.</span></span> <span data-ttu-id="92607-117">如果在「執行 SQL」工作執行時發生錯誤，則會執行封裝的 `OnError` 事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="92607-117">If an error occurs when the Execute SQL task runs, the `OnError` event handler for the package runs.</span></span> <span data-ttu-id="92607-118">下圖顯示引發封裝執行 `OnError` 事件處理常式的呼叫順序。</span><span class="sxs-lookup"><span data-stu-id="92607-118">The following diagram shows the sequence of calls that causes the `OnError` event handler for the package to execute.</span></span>

 <span data-ttu-id="92607-119">![事件處理常式流程](media/mw-dts-eventhandlers.gif "事件處理常式流程")</span><span class="sxs-lookup"><span data-stu-id="92607-119">![Event handler flow](media/mw-dts-eventhandlers.gif "Event handler flow")</span></span>

 <span data-ttu-id="92607-120">事件處理常式是事件處理常式集合的成員，所有容器都包含此集合。</span><span class="sxs-lookup"><span data-stu-id="92607-120">Event handlers are members of an event handler collection, and all containers include this collection.</span></span> <span data-ttu-id="92607-121">如果使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師建立封裝，則您可以在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師之 [封裝總管] 索引標籤上的 [事件處理常式] 資料夾中，查看事件處理常式集合的成員。</span><span class="sxs-lookup"><span data-stu-id="92607-121">If you create the package using [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, you can see the members of the event handler collections in the **Event Handlers** folders on the **Package Explorer** tab of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="92607-122">您可以利用下列方式設定事件處理常式容器：</span><span class="sxs-lookup"><span data-stu-id="92607-122">You can configure the event handler container in the following ways:</span></span>

-   <span data-ttu-id="92607-123">指定事件處理常式的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="92607-123">Specify a name and description for the event handler.</span></span>

-   <span data-ttu-id="92607-124">指出是否執行事件處理常式，如果事件處理常式失敗則封裝是否也將失敗，以及事件處理常式失敗之前可發生錯誤的數目。</span><span class="sxs-lookup"><span data-stu-id="92607-124">Indicate whether the event handler runs, whether the package fails if the event handler fails, and the number of errors that can occur before the event handler fails.</span></span>

-   <span data-ttu-id="92607-125">指定要傳回的執行結果，而非事件處理常式在執行階段傳回的實際執行結果。</span><span class="sxs-lookup"><span data-stu-id="92607-125">Specify an execution result to return instead of the actual execution result that the event handler returns at run time.</span></span>

-   <span data-ttu-id="92607-126">指定事件處理常式的交易選項。</span><span class="sxs-lookup"><span data-stu-id="92607-126">Specify the transaction option for the event handler.</span></span>

-   <span data-ttu-id="92607-127">指定事件處理常式使用的記錄模式。</span><span class="sxs-lookup"><span data-stu-id="92607-127">Specify the logging mode that the event handler uses.</span></span>

## <a name="event-handler-content"></a><span data-ttu-id="92607-128">事件處理常式內容</span><span class="sxs-lookup"><span data-stu-id="92607-128">Event Handler Content</span></span>
 <span data-ttu-id="92607-129">建立事件處理常式與建立封裝相似；事件處理常式具有工作和容器，它們會循序進入控制流程，並且事件處理常式還可以包含資料流程。</span><span class="sxs-lookup"><span data-stu-id="92607-129">Creating an event handler is similar to building a package; an event handler has tasks and containers, which are sequenced into a control flow, and an event handler can also include data flows.</span></span> <span data-ttu-id="92607-130">[!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師包含 [事件處理常式]  索引標籤，用以建立自訂事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="92607-130">The [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer includes the **Event Handlers** tab for creating custom event handlers.</span></span> <span data-ttu-id="92607-131">如需詳細資訊，請參閱[SSIS 封裝事件處理常式](integration-services-ssis-event-handlers.md)。</span><span class="sxs-lookup"><span data-stu-id="92607-131">For more information, see [SSIS Package Event Handlers](integration-services-ssis-event-handlers.md).</span></span>

 <span data-ttu-id="92607-132">您還可以程式設計方式建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="92607-132">You can also create event handlers programmatically.</span></span> <span data-ttu-id="92607-133">如需詳細資訊，請參閱 [以程式設計方式處理事件](building-packages-programmatically/handling-events-programmatically.md)。</span><span class="sxs-lookup"><span data-stu-id="92607-133">For more information, see [Handling Events Programmatically](building-packages-programmatically/handling-events-programmatically.md).</span></span>

## <a name="run-time-events"></a><span data-ttu-id="92607-134">執行階段事件</span><span class="sxs-lookup"><span data-stu-id="92607-134">Run-Time Events</span></span>
 <span data-ttu-id="92607-135">下表列出 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 所提供的事件處理常式，並描述引發事件處理常式執行的執行階段事件。</span><span class="sxs-lookup"><span data-stu-id="92607-135">The following table lists the event handlers that [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] provides, and describes the run-time events that cause the event handler to run.</span></span>

|<span data-ttu-id="92607-136">事件處理常式</span><span class="sxs-lookup"><span data-stu-id="92607-136">Event handler</span></span>|<span data-ttu-id="92607-137">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="92607-137">Event</span></span>|
|-------------------|-----------|
|`OnError`|<span data-ttu-id="92607-138">`OnError` 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="92607-138">The event handler for the `OnError` event.</span></span> <span data-ttu-id="92607-139">當發生錯誤時，可執行檔會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="92607-139">This event is raised by an executable when an error occurs.</span></span>|
|<span data-ttu-id="92607-140">**OnExecStatusChanged**</span><span class="sxs-lookup"><span data-stu-id="92607-140">**OnExecStatusChanged**</span></span>|<span data-ttu-id="92607-141">**OnExecStatusChanged** 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="92607-141">The event handler for the **OnExecStatusChanged** event.</span></span> <span data-ttu-id="92607-142">當可執行檔的執行狀態變更時，它會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="92607-142">This event is raised by an executable when its execution status changes.</span></span>|
|<span data-ttu-id="92607-143">**OnInformation**</span><span class="sxs-lookup"><span data-stu-id="92607-143">**OnInformation**</span></span>|<span data-ttu-id="92607-144">**OnInformation** 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="92607-144">The event handler for the **OnInformation** event.</span></span> <span data-ttu-id="92607-145">在驗證和執行可執行檔以報告資訊期間，會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="92607-145">This event is raised during the validation and execution of an executable to report information.</span></span> <span data-ttu-id="92607-146">此事件僅傳遞資訊，而不傳遞錯誤或警告。</span><span class="sxs-lookup"><span data-stu-id="92607-146">This event conveys information only, no errors or warnings.</span></span>|
|<span data-ttu-id="92607-147">**OnPostExecute**</span><span class="sxs-lookup"><span data-stu-id="92607-147">**OnPostExecute**</span></span>|<span data-ttu-id="92607-148">**OnPostExecute** 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="92607-148">The event handler for the **OnPostExecute** event.</span></span> <span data-ttu-id="92607-149">可執行檔完成執行後，它會立即引發此事件。</span><span class="sxs-lookup"><span data-stu-id="92607-149">This event is raised by an executable immediately after it has finished running.</span></span>|
|<span data-ttu-id="92607-150">**OnPostValidate**</span><span class="sxs-lookup"><span data-stu-id="92607-150">**OnPostValidate**</span></span>|<span data-ttu-id="92607-151">**OnPostValidate** 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="92607-151">The event handler for the **OnPostValidate** event.</span></span> <span data-ttu-id="92607-152">可執行檔的驗證完成後，它會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="92607-152">This event is raised by an executable when its validation is finished.</span></span>|
|<span data-ttu-id="92607-153">**OnPreExecute**</span><span class="sxs-lookup"><span data-stu-id="92607-153">**OnPreExecute**</span></span>|<span data-ttu-id="92607-154">**OnPreExecute** 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="92607-154">The event handler for the **OnPreExecute** event.</span></span> <span data-ttu-id="92607-155">可執行檔執行之前，它會立即引發此事件。</span><span class="sxs-lookup"><span data-stu-id="92607-155">This event is raised by an executable immediately before it runs.</span></span>|
|<span data-ttu-id="92607-156">**OnPreValidate**</span><span class="sxs-lookup"><span data-stu-id="92607-156">**OnPreValidate**</span></span>|<span data-ttu-id="92607-157">**OnPreValidate** 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="92607-157">The event handler for the **OnPreValidate** event.</span></span> <span data-ttu-id="92607-158">可執行檔驗證開始時，它會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="92607-158">This event is raised by an executable when its validation starts.</span></span>|
|<span data-ttu-id="92607-159">**OnProgress**</span><span class="sxs-lookup"><span data-stu-id="92607-159">**OnProgress**</span></span>|<span data-ttu-id="92607-160">**OnProgress** 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="92607-160">The event handler for the **OnProgress** event.</span></span> <span data-ttu-id="92607-161">可執行檔的進度可測量時，它會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="92607-161">This event is raised by an executable when measurable progress is made by the executable.</span></span>|
|<span data-ttu-id="92607-162">**OnQueryCancel**</span><span class="sxs-lookup"><span data-stu-id="92607-162">**OnQueryCancel**</span></span>|<span data-ttu-id="92607-163">**OnQueryCancel** 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="92607-163">The event handler for the **OnQueryCancel** event.</span></span> <span data-ttu-id="92607-164">可執行檔會引發此事件，以判斷其是否應停止執行。</span><span class="sxs-lookup"><span data-stu-id="92607-164">This event is raised by an executable to determine whether it should stop running.</span></span>|
|<span data-ttu-id="92607-165">**OnTaskFailed**</span><span class="sxs-lookup"><span data-stu-id="92607-165">**OnTaskFailed**</span></span>|<span data-ttu-id="92607-166">**OnTaskFailed** 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="92607-166">The event handler for the **OnTaskFailed** event.</span></span> <span data-ttu-id="92607-167">工作失敗時，它引發此事件。</span><span class="sxs-lookup"><span data-stu-id="92607-167">This event is raised by a task when it fails.</span></span>|
|<span data-ttu-id="92607-168">**OnVariableValueChanged**</span><span class="sxs-lookup"><span data-stu-id="92607-168">**OnVariableValueChanged**</span></span>|<span data-ttu-id="92607-169">**OnVariableValueChanged** 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="92607-169">The event handler for the **OnVariableValueChanged** event.</span></span> <span data-ttu-id="92607-170">當變數變更時，可執行檔會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="92607-170">This event is raised by an executable when the value of a variable changes.</span></span> <span data-ttu-id="92607-171">定義變數所在的可執行檔會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="92607-171">The event is raised by the executable on which the variable is defined.</span></span> <span data-ttu-id="92607-172">如果您將變數的**RaiseChangeEvent**屬性設定為，則不會引發這個事件 `False` 。</span><span class="sxs-lookup"><span data-stu-id="92607-172">This event is not raised if you set the **RaiseChangeEvent** property for the variable to `False`.</span></span> <span data-ttu-id="92607-173">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="92607-173">For more information, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md).</span></span>|
|<span data-ttu-id="92607-174">**OnWarning**</span><span class="sxs-lookup"><span data-stu-id="92607-174">**OnWarning**</span></span>|<span data-ttu-id="92607-175">**OnWarning** 事件的事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="92607-175">The event handler for the **OnWarning** event.</span></span> <span data-ttu-id="92607-176">當發生警告時，可執行檔會引發此事件。</span><span class="sxs-lookup"><span data-stu-id="92607-176">This event is raised by an executable when a warning occurs.</span></span>|

## <a name="configuration-of-an-event-handler"></a><span data-ttu-id="92607-177">設定事件處理常式</span><span class="sxs-lookup"><span data-stu-id="92607-177">Configuration of an Event Handler</span></span>
 <span data-ttu-id="92607-178">您可以在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的 [屬性]\*\*\*\* 視窗中，或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="92607-178">You can set properties in the **Properties** window of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] or programmatically.</span></span>

 <span data-ttu-id="92607-179">如需如何在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中設定這些屬性的相關資訊，請參閱 [設定工作或容器的屬性](../../2014/integration-services/set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="92607-179">For information about how to set these properties in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], see [Set the Properties of a Task or Container](../../2014/integration-services/set-the-properties-of-a-task-or-container.md).</span></span>

 <span data-ttu-id="92607-180">如需以程式設計方式設定這些屬性的詳細資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>。</span><span class="sxs-lookup"><span data-stu-id="92607-180">For information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Runtime.DtsEventHandler>.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="92607-181">相關工作</span><span class="sxs-lookup"><span data-stu-id="92607-181">Related Tasks</span></span>
 <span data-ttu-id="92607-182">如需如何將事件處理常式加入封裝的相關資訊，請參閱 [將事件處理常式加入封裝中](../../2014/integration-services/add-an-event-handler-to-a-package.md)。</span><span class="sxs-lookup"><span data-stu-id="92607-182">For information about how to add an event handler to a package, see [Add an Event Handler to a Package](../../2014/integration-services/add-an-event-handler-to-a-package.md).</span></span>


