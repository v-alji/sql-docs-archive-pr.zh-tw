---
title: 偵錯控制流程 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- progress reporting [Integration Services]
- breakpoints [Integration Services]
- debugging [Integration Services], control flow
- control flow [Integration Services], debugging
- color-coded progress reporting [Integration Services]
- Set Breakpoints dialog box
ms.assetid: 54a458cc-9f4f-4b48-8cf2-db2e0fa7756c
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f2e2feff6723a510cb773131cb6452bdc7a77cc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703105"
---
# <a name="debugging-control-flow"></a><span data-ttu-id="a90cc-102">偵錯控制流程</span><span class="sxs-lookup"><span data-stu-id="a90cc-102">Debugging Control Flow</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="a90cc-103">和 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 包含許多功能和工具，可讓您用來對 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 套件中的控制流程進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="a90cc-103">and [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] include features and tools that you can use to troubleshoot the control flow in an [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] package.</span></span>

-   [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="a90cc-104">支援容器及工作上的中斷點。</span><span class="sxs-lookup"><span data-stu-id="a90cc-104">supports breakpoints on containers and tasks.</span></span>

-   [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="a90cc-105">設計師」提供執行階段的進度報表。</span><span class="sxs-lookup"><span data-stu-id="a90cc-105">Designer provides progress reporting at run time.</span></span>

-   [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="a90cc-106">提供偵錯視窗。</span><span class="sxs-lookup"><span data-stu-id="a90cc-106">provides debug windows.</span></span>

## <a name="breakpoints"></a><span data-ttu-id="a90cc-107">中斷點</span><span class="sxs-lookup"><span data-stu-id="a90cc-107">Breakpoints</span></span>
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="a90cc-108">設計工具提供 [設定中斷點]  對話方塊，您可以啟用中斷條件，並指定套件的執行暫停之前中斷點可以出現的次數，在此設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="a90cc-108">Designer provides the **Set Breakpoints** dialog box, in which you can set breakpoints by enabling break conditions and specifying the number of times a breakpoint can occur before the execution of the package is suspended.</span></span> <span data-ttu-id="a90cc-109">中斷點可以在封裝層級啟用，也可以在個別元件層級啟用。</span><span class="sxs-lookup"><span data-stu-id="a90cc-109">Breakpoints can be enabled at the package level, or at the level of the individual component.</span></span> <span data-ttu-id="a90cc-110">如果中斷條件在工作或容器層級啟用，則中斷點圖示會顯示在 [控制流程]  索引標籤之設計介面的工作或容器旁。如果中斷條件在封裝上啟用，則中斷點圖示會顯示在 [控制流程]  索引標籤的標籤上。</span><span class="sxs-lookup"><span data-stu-id="a90cc-110">If break conditions are enabled at the task or container level, the breakpoint icon appears next to the task or container on the design surface of the **Control Flow** tab. If the break conditions are enabled on the package, the breakpoint icon appears on the label of the **Control Flow** tab.</span></span>

 <span data-ttu-id="a90cc-111">當叫用中斷點時，中斷點圖示會變更，以協助您識別中斷點的來源。</span><span class="sxs-lookup"><span data-stu-id="a90cc-111">When a breakpoint is hit, the breakpoint icon changes to help you identify the source of the breakpoint.</span></span> <span data-ttu-id="a90cc-112">您可以在封裝執行時加入、刪除及變更中斷點。</span><span class="sxs-lookup"><span data-stu-id="a90cc-112">You can add, delete, and change breakpoints when the package is running.</span></span>

 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="a90cc-113">提供您可以在所有工作及容器上啟用的十個中斷條件。</span><span class="sxs-lookup"><span data-stu-id="a90cc-113">provides ten break conditions that you can enable on all tasks and containers.</span></span> <span data-ttu-id="a90cc-114">在 [設定中斷點]  對話方塊中，您可以在滿足下列條件時啟用中斷點：</span><span class="sxs-lookup"><span data-stu-id="a90cc-114">In the **Set Breakpoints** dialog box, you can enable breakpoints on the following conditions:</span></span>

|<span data-ttu-id="a90cc-115">中斷條件</span><span class="sxs-lookup"><span data-stu-id="a90cc-115">Break condition</span></span>|<span data-ttu-id="a90cc-116">描述</span><span class="sxs-lookup"><span data-stu-id="a90cc-116">Description</span></span>|
|---------------------|-----------------|
|<span data-ttu-id="a90cc-117">工作或容器接收到 `OnPreExecute` 事件時。</span><span class="sxs-lookup"><span data-stu-id="a90cc-117">When the task or container receives the `OnPreExecute` event.</span></span>|<span data-ttu-id="a90cc-118">即將執行工作時呼叫。</span><span class="sxs-lookup"><span data-stu-id="a90cc-118">Called when a task is about to execute.</span></span> <span data-ttu-id="a90cc-119">工作或容器會在即將執行之前引發此事件。</span><span class="sxs-lookup"><span data-stu-id="a90cc-119">This event is raised by a task or a container immediately before it runs.</span></span>|
|<span data-ttu-id="a90cc-120">工作或容器接收到 `OnPostExecute` 事件時。</span><span class="sxs-lookup"><span data-stu-id="a90cc-120">When the task or container receives the `OnPostExecute` event.</span></span>|<span data-ttu-id="a90cc-121">在工作的執行邏輯完成之後立即呼叫。</span><span class="sxs-lookup"><span data-stu-id="a90cc-121">Called immediately after the execution logic of the task finishes.</span></span> <span data-ttu-id="a90cc-122">工作或容器會在執行之後立即引發此事件。</span><span class="sxs-lookup"><span data-stu-id="a90cc-122">This event is raised by a task or container immediately after it runs.</span></span>|
|<span data-ttu-id="a90cc-123">工作或容器接收到 `OnError` 事件時。</span><span class="sxs-lookup"><span data-stu-id="a90cc-123">When the task or container receives the `OnError` event.</span></span>|<span data-ttu-id="a90cc-124">發生錯誤時由工作或容器呼叫。</span><span class="sxs-lookup"><span data-stu-id="a90cc-124">Called by a task or container when an error occurs.</span></span>|
|<span data-ttu-id="a90cc-125">工作或容器接收到 `OnWarning` 事件時。</span><span class="sxs-lookup"><span data-stu-id="a90cc-125">When the task or container receives the `OnWarning` event.</span></span>|<span data-ttu-id="a90cc-126">當工作處於還不是錯誤但需要警告的狀態時呼叫。</span><span class="sxs-lookup"><span data-stu-id="a90cc-126">Called when the task is in a state that does not justify an error, but does warrant a warning.</span></span>|
|<span data-ttu-id="a90cc-127">工作或容器接收到 `OnInformation` 事件時。</span><span class="sxs-lookup"><span data-stu-id="a90cc-127">When the task or container receives the `OnInformation` event.</span></span>|<span data-ttu-id="a90cc-128">需要工作提供資訊時呼叫。</span><span class="sxs-lookup"><span data-stu-id="a90cc-128">Called when the task is required to provide information.</span></span>|
|<span data-ttu-id="a90cc-129">工作或容器接收到 `OnTaskFailed` 事件時。</span><span class="sxs-lookup"><span data-stu-id="a90cc-129">When the task or container receives the `OnTaskFailed` event.</span></span>|<span data-ttu-id="a90cc-130">由工作主機在失敗時呼叫。</span><span class="sxs-lookup"><span data-stu-id="a90cc-130">Called by the task host when it fails.</span></span>|
|<span data-ttu-id="a90cc-131">工作或容器接收到 `OnProgress` 事件時。</span><span class="sxs-lookup"><span data-stu-id="a90cc-131">When the task or container receives the `OnProgress` event.</span></span>|<span data-ttu-id="a90cc-132">呼叫以更新工作執行相關的進度。</span><span class="sxs-lookup"><span data-stu-id="a90cc-132">Called to update progress about task execution.</span></span>|
|<span data-ttu-id="a90cc-133">工作或容器接收到 `OnQueryCancel` 事件時。</span><span class="sxs-lookup"><span data-stu-id="a90cc-133">When the task or container receives the `OnQueryCancel` event.</span></span>|<span data-ttu-id="a90cc-134">在可取消執行之工作處理期間的任何時間呼叫。</span><span class="sxs-lookup"><span data-stu-id="a90cc-134">Called at any time in task processing when you can cancel execution.</span></span>|
|<span data-ttu-id="a90cc-135">工作或容器接收到 `OnVariableValueChanged` 事件時。</span><span class="sxs-lookup"><span data-stu-id="a90cc-135">When the task or container receives the `OnVariableValueChanged` event.</span></span>|<span data-ttu-id="a90cc-136">當變數的值變更時由 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 執行階段呼叫。</span><span class="sxs-lookup"><span data-stu-id="a90cc-136">Called by the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] runtime when the value of a variable changes.</span></span> <span data-ttu-id="a90cc-137">變數的 RaiseChangeEvent 必須設定為， `true` 才能引發這個事件。</span><span class="sxs-lookup"><span data-stu-id="a90cc-137">The RaiseChangeEvent of the variable must be set to `true` to raise this event.</span></span><br /><br /> <span data-ttu-id="a90cc-138">**&#42;&#42; 警告 &#42;&#42;** 與此中斷點相關聯的變數必須在**容器**範圍定義。</span><span class="sxs-lookup"><span data-stu-id="a90cc-138">**&#42;&#42; Warning &#42;&#42;** The variable associated with this breakpoint must be defined at the **container** scope.</span></span> <span data-ttu-id="a90cc-139">如果變數在封裝範圍定義，則中斷點不會出現。</span><span class="sxs-lookup"><span data-stu-id="a90cc-139">If the variable is defined at the package scope, the breakpoint does not get hit.</span></span>|
|<span data-ttu-id="a90cc-140">工作或容器接收到 `OnCustomEvent` 事件時。</span><span class="sxs-lookup"><span data-stu-id="a90cc-140">When the task or container receives the `OnCustomEvent` event.</span></span>|<span data-ttu-id="a90cc-141">由工作呼叫，以引發自訂工作定義的事件。</span><span class="sxs-lookup"><span data-stu-id="a90cc-141">Called by tasks to raise custom task-defined events.</span></span>|

 <span data-ttu-id="a90cc-142">除可用於所有工作及容器的中斷條件之外，部份工作及容器還包含用於設定中斷點的特殊中斷條件。</span><span class="sxs-lookup"><span data-stu-id="a90cc-142">In addition to the break conditions available to all tasks and containers, some tasks and containers include special break conditions for setting breakpoints.</span></span> <span data-ttu-id="a90cc-143">例如，您可以在「For 迴圈」容器上啟用中斷條件，以設定在迴圈的每個反覆運算開始時暫停執行的中斷點。</span><span class="sxs-lookup"><span data-stu-id="a90cc-143">For example, you can enable a break condition on the For Loop container that sets a breakpoint that suspends execution at the start of each iteration of the loop.</span></span>

 <span data-ttu-id="a90cc-144">若要加強中斷點的彈性及能力，您可以藉由指定下列選項來修改中斷點的行為：</span><span class="sxs-lookup"><span data-stu-id="a90cc-144">To add flexibility and power to a breakpoint, you can modify the behavior of a breakpoint by specifying the following options:</span></span>

-   <span data-ttu-id="a90cc-145">叫用計數，或執行暫停之前中斷條件出現的最大次數。</span><span class="sxs-lookup"><span data-stu-id="a90cc-145">The hit count, or the maximum number of times that a break condition occurs before the execution is suspended.</span></span>

-   <span data-ttu-id="a90cc-146">叫用計數類型，或指定中斷條件何時觸發中斷點的規則。</span><span class="sxs-lookup"><span data-stu-id="a90cc-146">The hit count type, or the rule that specifies when the break condition triggers the breakpoint.</span></span>

 <span data-ttu-id="a90cc-147">叫用計數會進一步限定「永遠」類型以外的叫用計數類型。</span><span class="sxs-lookup"><span data-stu-id="a90cc-147">The hit count types, except for the Always type, are further qualified by the hit count.</span></span> <span data-ttu-id="a90cc-148">例如，如果類型為「叫用計數等於」而叫用計數為 5 的話，便會在第六次出現中斷條件時暫停執行。</span><span class="sxs-lookup"><span data-stu-id="a90cc-148">For example, if the type is "Hit count equals" and the hit count is 5, execution is suspended on the sixth occurrence of the break condition.</span></span>

 <span data-ttu-id="a90cc-149">下表描述叫用計數類型。</span><span class="sxs-lookup"><span data-stu-id="a90cc-149">The following table describes the hit count types.</span></span>

|<span data-ttu-id="a90cc-150">叫用計數類型</span><span class="sxs-lookup"><span data-stu-id="a90cc-150">Hit count type</span></span>|<span data-ttu-id="a90cc-151">描述</span><span class="sxs-lookup"><span data-stu-id="a90cc-151">Description</span></span>|
|--------------------|-----------------|
|<span data-ttu-id="a90cc-152">一律</span><span class="sxs-lookup"><span data-stu-id="a90cc-152">Always</span></span>|<span data-ttu-id="a90cc-153">叫用中斷點時，一律暫停執行。</span><span class="sxs-lookup"><span data-stu-id="a90cc-153">Execution is always suspended when the breakpoint is hit.</span></span>|
|<span data-ttu-id="a90cc-154">叫用計數等於</span><span class="sxs-lookup"><span data-stu-id="a90cc-154">Hit count equals</span></span>|<span data-ttu-id="a90cc-155">當中斷點發生的次數等於叫用計數時，暫停執行。</span><span class="sxs-lookup"><span data-stu-id="a90cc-155">Execution is suspended when the number of times the breakpoint has occurred is equal to the hit count.</span></span>|
|<span data-ttu-id="a90cc-156">叫用次數大於或等於</span><span class="sxs-lookup"><span data-stu-id="a90cc-156">Hit count greater than or equal to</span></span>|<span data-ttu-id="a90cc-157">當中斷點發生的次數大於或等於叫用計數時，暫停執行。</span><span class="sxs-lookup"><span data-stu-id="a90cc-157">Execution is suspended when the number of times the breakpoint has occurred is equal to or greater than the hit count.</span></span>|
|<span data-ttu-id="a90cc-158">叫用計數倍數</span><span class="sxs-lookup"><span data-stu-id="a90cc-158">Hit count multiple</span></span>|<span data-ttu-id="a90cc-159">每當到達叫用計數的倍數時，暫停執行。</span><span class="sxs-lookup"><span data-stu-id="a90cc-159">Execution is suspended when a multiple of the hit count occurs.</span></span> <span data-ttu-id="a90cc-160">例如，若您將此選項設定為 5，則每到達五次叫用便會暫停執行。</span><span class="sxs-lookup"><span data-stu-id="a90cc-160">For example, if you set this option to 5, execution is suspended every fifth time.</span></span>|

#### <a name="to-set-breakpoints"></a><span data-ttu-id="a90cc-161">設定中斷點</span><span class="sxs-lookup"><span data-stu-id="a90cc-161">To set breakpoints</span></span>

-   [<span data-ttu-id="a90cc-162">在工作或容器設定中斷點以對套件偵錯</span><span class="sxs-lookup"><span data-stu-id="a90cc-162">Debug a Package by Setting Breakpoints on a Task or a Container</span></span>](../debug-a-package-by-setting-breakpoints-on-a-task-or-a-container.md)

## <a name="progress-reporting"></a><span data-ttu-id="a90cc-163">進度報表</span><span class="sxs-lookup"><span data-stu-id="a90cc-163">Progress Reporting</span></span>
 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="a90cc-164">設計工具包含兩種類型的進度報告：[控制流程]  索引標籤之設計介面上的色彩編碼，以及 [進度]  索引標籤上的進度訊息。</span><span class="sxs-lookup"><span data-stu-id="a90cc-164">Designer includes two types of progress reporting: color-coding on the design surface of the **Control Flow** tab, and progress messages on the **Progress** tab.</span></span>

 <span data-ttu-id="a90cc-165">當您執行封裝時，「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」會使用指示執行狀態的色彩來顯示每個工作或容器，以描述執行進度。</span><span class="sxs-lookup"><span data-stu-id="a90cc-165">When you run a package, [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer depicts execution progress by displaying each task or container using a color that indicates execution status.</span></span> <span data-ttu-id="a90cc-166">您可以根據元素的色彩判斷它是在等候執行、執行中、已順利完成，還是未成功結束。</span><span class="sxs-lookup"><span data-stu-id="a90cc-166">You can tell by its color whether the element is waiting to run, currently running, has completed successfully, or has ended unsuccessfully.</span></span> <span data-ttu-id="a90cc-167">在您停止封裝執行之後，色彩編碼會消失。</span><span class="sxs-lookup"><span data-stu-id="a90cc-167">After you stop package execution, the color-coding disappears.</span></span>

 <span data-ttu-id="a90cc-168">下表描述用於描述執行狀態的色彩。</span><span class="sxs-lookup"><span data-stu-id="a90cc-168">The following table describes the colors that are used to depict execution status.</span></span>

|<span data-ttu-id="a90cc-169">Color</span><span class="sxs-lookup"><span data-stu-id="a90cc-169">Color</span></span>|<span data-ttu-id="a90cc-170">執行狀態</span><span class="sxs-lookup"><span data-stu-id="a90cc-170">Execution status</span></span>|
|-----------|----------------------|
|<span data-ttu-id="a90cc-171">灰色</span><span class="sxs-lookup"><span data-stu-id="a90cc-171">Gray</span></span>|<span data-ttu-id="a90cc-172">等候執行</span><span class="sxs-lookup"><span data-stu-id="a90cc-172">Waiting to run</span></span>|
|<span data-ttu-id="a90cc-173">黃色</span><span class="sxs-lookup"><span data-stu-id="a90cc-173">Yellow</span></span>|<span data-ttu-id="a90cc-174">執行中</span><span class="sxs-lookup"><span data-stu-id="a90cc-174">Running</span></span>|
|<span data-ttu-id="a90cc-175">綠色</span><span class="sxs-lookup"><span data-stu-id="a90cc-175">Green</span></span>|<span data-ttu-id="a90cc-176">執行成功</span><span class="sxs-lookup"><span data-stu-id="a90cc-176">Ran successfully</span></span>|
|<span data-ttu-id="a90cc-177">反白顯示</span><span class="sxs-lookup"><span data-stu-id="a90cc-177">highlighted</span></span>|<span data-ttu-id="a90cc-178">執行發生錯誤</span><span class="sxs-lookup"><span data-stu-id="a90cc-178">Ran with errors</span></span>|

 <span data-ttu-id="a90cc-179">[進度]  索引標籤會以執行順序列出工作及容器，並包含開始與完成時間、警告及錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="a90cc-179">The **Progress** tab lists tasks and containers in execution order and includes the start and finish times, warnings, and error messages.</span></span> <span data-ttu-id="a90cc-180">在您停止封裝執行之後，進度資訊在 [執行結果]  索引標籤上仍然可用。</span><span class="sxs-lookup"><span data-stu-id="a90cc-180">After you stop package execution, the progress information remains available on the **Execution Results** tab.</span></span>

> [!NOTE]
>  <span data-ttu-id="a90cc-181">若要啟用或停用 **[進度]** 索引標籤上的訊息顯示，請在 **[SSIS]** 功能表上切換 **[偵錯進度報表]** 選項。</span><span class="sxs-lookup"><span data-stu-id="a90cc-181">To enable or disable the display of messages on the **Progress** tab, toggle the **Debug Progress Reporting** option on the **SSIS** menu.</span></span>

 <span data-ttu-id="a90cc-182">下圖顯示 [進度]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="a90cc-182">The following diagram shows the **Progress** tab.</span></span>

 <span data-ttu-id="a90cc-183">![SSIS 設計師的 [進度] 索引標籤](../media/mw-dtsflow04.gif "SSIS 設計師的 [進度] 索引標籤")</span><span class="sxs-lookup"><span data-stu-id="a90cc-183">![Progress tab of SSIS Designer](../media/mw-dtsflow04.gif "Progress tab of SSIS Designer")</span></span>

## <a name="debug-windows"></a><span data-ttu-id="a90cc-184">偵錯視窗</span><span class="sxs-lookup"><span data-stu-id="a90cc-184">Debug Windows</span></span>
 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="a90cc-185">包含許多視窗，您可將其用於處理中斷點及偵錯包含中斷點的封裝。</span><span class="sxs-lookup"><span data-stu-id="a90cc-185">includes many windows that you can use to work with breakpoints, and to debug packages that contain breakpoints.</span></span> <span data-ttu-id="a90cc-186">若要了解每個視窗的詳細資訊，請開啟該視窗並按 F1，以顯示視窗的 [說明]。</span><span class="sxs-lookup"><span data-stu-id="a90cc-186">To learn more about each window, open the window, and then press F1 to display Help for the window.</span></span>

 <span data-ttu-id="a90cc-187">若要在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)] 中開啟這些視窗，請按一下 [偵錯]  功能表，指向 [視窗]  ，然後按一下 [中斷點]  、[輸出]  或 [立即]  。</span><span class="sxs-lookup"><span data-stu-id="a90cc-187">To open these windows in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)], click the **Debug** menu, point to **Windows**, and then click **Breakpoints**, **Output**, or **Immediate**.</span></span>

 <span data-ttu-id="a90cc-188">下表描述這些視窗。</span><span class="sxs-lookup"><span data-stu-id="a90cc-188">The following table describes the windows.</span></span>

|<span data-ttu-id="a90cc-189">時間範圍</span><span class="sxs-lookup"><span data-stu-id="a90cc-189">Window</span></span>|<span data-ttu-id="a90cc-190">描述</span><span class="sxs-lookup"><span data-stu-id="a90cc-190">Description</span></span>|
|------------|-----------------|
|<span data-ttu-id="a90cc-191">中斷點</span><span class="sxs-lookup"><span data-stu-id="a90cc-191">Breakpoints</span></span>|<span data-ttu-id="a90cc-192">列出封裝中的中斷點，並提供啟用及刪除中斷點的選項。</span><span class="sxs-lookup"><span data-stu-id="a90cc-192">Lists the breakpoints in a package and provides options to enable and delete breakpoints.</span></span>|
|<span data-ttu-id="a90cc-193">輸出</span><span class="sxs-lookup"><span data-stu-id="a90cc-193">Output</span></span>|<span data-ttu-id="a90cc-194">在 [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)]中顯示各功能的狀態訊息。</span><span class="sxs-lookup"><span data-stu-id="a90cc-194">Displays status messages for features in [!INCLUDE[ssBIDevStudioFull](../../../includes/ssbidevstudiofull-md.md)].</span></span>|
|<span data-ttu-id="a90cc-195">立即</span><span class="sxs-lookup"><span data-stu-id="a90cc-195">Immediate</span></span>|<span data-ttu-id="a90cc-196">用於偵錯及評估運算式並列印變數值。</span><span class="sxs-lookup"><span data-stu-id="a90cc-196">Used to debug and evaluate expressions and print variable values.</span></span>|

## <a name="see-also"></a><span data-ttu-id="a90cc-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a90cc-197">See Also</span></span>
 [<span data-ttu-id="a90cc-198">套件開發的疑難排解工具</span><span class="sxs-lookup"><span data-stu-id="a90cc-198">Troubleshooting Tools for Package Development</span></span>](troubleshooting-tools-for-package-development.md)


