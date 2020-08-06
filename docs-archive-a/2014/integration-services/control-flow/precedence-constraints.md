---
title: 優先順序條件約束 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- control flow [Integration Services], precedence constraints
- precedence constraints [Integration Services]
- constraints [Integration Services]
- sequence execution options [Integration Services]
- containers [Integration Services], precedence constraints
ms.assetid: c5ce5435-fd89-4156-a11f-68470a69aa9f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7a08fd1d66e43ede4c54284518bab191be8997a4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597262"
---
# <a name="precedence-constraints"></a><span data-ttu-id="7ed7f-102">優先順序條件約束</span><span class="sxs-lookup"><span data-stu-id="7ed7f-102">Precedence Constraints</span></span>
  <span data-ttu-id="7ed7f-103">優先順序條件約束可在控制流程中，連結封裝中的可執行檔、容器和工作，並指定判斷可執行檔是否執行的條件。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-103">Precedence constraints link executables, containers, and tasks in packages in a control flow, and specify conditions that determine whether executables run.</span></span> <span data-ttu-id="7ed7f-104">可執行檔可以是「For 迴圈」容器、「Foreach 迴圈」容器、「時序」容器、工作或事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-104">An executable can be a For Loop, Foreach Loop, or Sequence container; a task; or an event handler.</span></span> <span data-ttu-id="7ed7f-105">事件處理常式也可使用優先順序條件約束，以將其可執行檔連結至控制流程。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-105">Event handlers also use precedence constraints to link their executables into a control flow.</span></span>

 <span data-ttu-id="7ed7f-106">優先順序條件約束會連結兩個可執行檔：優先順序可執行檔和受條件約束的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-106">A precedence constraint links two executables: the precedence executable and the constrained executable.</span></span> <span data-ttu-id="7ed7f-107">優先順序可執行檔在條件約束可執行檔之前執行，且優先順序可執行檔的執行結果可以決定條件約束可執行檔是否執行。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-107">The precedence executable runs before the constrained executable, and the execution result of the precedence executable may determine whether the constrained executable runs.</span></span> <span data-ttu-id="7ed7f-108">下圖顯示了由優先順序條件約束連結的兩個可執行檔。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-108">The following diagram shows two executables linked by a precedence constraint.</span></span>

 <span data-ttu-id="7ed7f-109">![以優先順序條件約束連線的可執行檔](../media/ssis-pcsimple.gif "以優先順序條件約束連線的可執行檔")</span><span class="sxs-lookup"><span data-stu-id="7ed7f-109">![Executables connected by a precedence constraint](../media/ssis-pcsimple.gif "Executables connected by a precedence constraint")</span></span>

 <span data-ttu-id="7ed7f-110">在線性控制流程 (即沒有分支的控制流程) 中，優先順序條件約束單獨管理工作執行的順序。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-110">In a linear control flow, that is, one without branching, precedence constraints alone govern the sequence in which tasks run.</span></span> <span data-ttu-id="7ed7f-111">在控制流程分支中， [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 執行階段引擎決定直接跟隨在分支後面的工作和容器之執行順序。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-111">If a control flow branches, the [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] run-time engine determines the execution order among the tasks and containers that immediately follow the branching.</span></span> <span data-ttu-id="7ed7f-112">執行階段引擎也決定控制流程中未連接的工作流程之執行順序。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-112">The run-time engine also determines execution order among unconnected workflows in a control flow.</span></span>

 <span data-ttu-id="7ed7f-113">除僅封裝單一工作的工作主機容器之外， [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 的巢狀容器架構會啟用所有容器，用以包含每個都具有其各自控制流程的其他容器。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-113">The nested-container architecture of [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] enables all containers, except for the task host container that encapsulates only a single task, to include other containers, each with its own control flow.</span></span> <span data-ttu-id="7ed7f-114">「For 迴圈」容器、「Foreach 迴圈」容器和「時序」容器可以包含多個工作和其他容器，而工作和其他容器進而可以包含多個工作和容器。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-114">The For Loop, Foreach Loop, and Sequence containers can include multiple tasks and other containers, which in turn can include multiple tasks and containers.</span></span> <span data-ttu-id="7ed7f-115">例如，具有「指令碼」工作和「時序」容器的封裝具有連結「指令碼」工作和「時序」容器的優先順序條件約束。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-115">For example, a package with a Script task and a Sequence container has a precedence constraint that links the Script task and the Sequence container.</span></span> <span data-ttu-id="7ed7f-116">「時序」容器包括三個「指令碼」工作，且其優先順序條件約束會將這三個「指令碼」工作連結至一個控制流程。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-116">The Sequence container includes three Script tasks, and its precedence constraints link the three Script tasks into a control flow.</span></span> <span data-ttu-id="7ed7f-117">下圖顯示具有兩個巢狀層級之封裝中的優先順序條件約束。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-117">The following diagram shows the precedence constraints in a package with two levels of nesting.</span></span>

 <span data-ttu-id="7ed7f-118">![套件中的優先順序條件約束](../media/mw-dts-12.gif "套件中的優先順序條件約束")</span><span class="sxs-lookup"><span data-stu-id="7ed7f-118">![Precedence contraints in a package](../media/mw-dts-12.gif "Precedence contraints in a package")</span></span>

 <span data-ttu-id="7ed7f-119">因為封裝位於 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 容器架構的最上層，所以優先順序條件約束無法連結多個封裝；但是，您可以將「執行封裝」工作加入封裝，然後間接地將其他封裝連結至控制流程。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-119">Because the package is at the top of the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] container hierarchy, multiple packages cannot be linked by precedence constraints; however, you can add an Execute Package task to a package and indirectly link another package into the control flow.</span></span>

 <span data-ttu-id="7ed7f-120">您可以利用下列方式設定優先順序條件約束：</span><span class="sxs-lookup"><span data-stu-id="7ed7f-120">You can configure precedence constraints in the following ways:</span></span>

-   <span data-ttu-id="7ed7f-121">指定評估作業。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-121">Specify an evaluation operation.</span></span> <span data-ttu-id="7ed7f-122">優先順序條件約束同時使用條件約束值和運算式，或使用其中之一，來決定條件約束可執行檔是否執行。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-122">The precedence constraint uses a constraint value, an expression, both, or either to determine whether the constrained executable runs.</span></span>

-   <span data-ttu-id="7ed7f-123">如果優先順序條件約束使用執行結果，則您可以將執行結果指定為成功、失敗或完成。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-123">If the precedence constraint uses an execution result, you can specify the execution result to be success, failure, or completion.</span></span>

-   <span data-ttu-id="7ed7f-124">如果優先順序條件約束使用評估結果，則您可以提供評估為布林的運算式。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-124">If the precedence constraint uses an evaluation result, you can provide an expression that evaluates to a Boolean.</span></span>

-   <span data-ttu-id="7ed7f-125">指定只評估優先順序條件約束，還是同時評估套用至條件約束可執行檔的其他條件約束。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-125">Specify whether the precedence constraint is evaluated singly or together with other constraints that apply to the constrained executable.</span></span>

## <a name="evaluation-operations"></a><span data-ttu-id="7ed7f-126">評估作業</span><span class="sxs-lookup"><span data-stu-id="7ed7f-126">Evaluation Operations</span></span>
 [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] <span data-ttu-id="7ed7f-127">提供下列評估作業：</span><span class="sxs-lookup"><span data-stu-id="7ed7f-127">provides the following evaluation operations:</span></span>

-   <span data-ttu-id="7ed7f-128">僅使用優先順序可執行檔之執行結果的條件約束，以決定條件約束可執行檔是否執行。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-128">A constraint that uses only the execution result of the precedence executable to determine whether the constrained executable runs.</span></span> <span data-ttu-id="7ed7f-129">優先順序可執行檔的執行結果可以是完成、成功或失敗。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-129">The execution result of the precedence executable can be completion, success, or failure.</span></span> <span data-ttu-id="7ed7f-130">這是預設作業。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-130">This is the default operation.</span></span>

-   <span data-ttu-id="7ed7f-131">運算式，對其進行評估以決定條件約束可執行檔是否執行。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-131">An expression that is evaluated to determine whether the constrained executable runs.</span></span> <span data-ttu-id="7ed7f-132">如果運算式評估為 true，則條件約束可執行檔會執行。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-132">If the expression evaluates to true, the constrained executable runs.</span></span>

-   <span data-ttu-id="7ed7f-133">運算式與條件約束，此條件約束會組合優先順序可執行檔之執行結果與評估運算式之傳回結果兩者的需求。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-133">An expression and a constraint that combines the requirements of execution results of the precedence executable and the return results of evaluating the expression.</span></span>

-   <span data-ttu-id="7ed7f-134">運算式或條件約束，此條件約束會使用優先順序可執行檔的執行結果或評估運算式的傳回結果。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-134">An expression or a constraint that uses either the execution results of the precedence executable or the return results of evaluating the expression.</span></span>

 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] <span data-ttu-id="7ed7f-135">設計師使用色彩識別優先順序條件約束的類型。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-135">Designer uses color to identify the type of precedence constraint.</span></span> <span data-ttu-id="7ed7f-136">「成功」條件約束為綠色，「失敗」條件約束為紅色，而「完成」條件約束則為藍色。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-136">The Success constraint is green, the Failure constraint is red, and the Completion constraint is blue.</span></span> <span data-ttu-id="7ed7f-137">若要在顯示條件約束類型的 [ [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師] 中顯示文字標籤，則必須設定 [ [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師] 的協助工具功能。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-137">To display text labels in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] designer that show the type of the constraint, you must configure the accessibility features of [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer.</span></span>

 <span data-ttu-id="7ed7f-138">運算式必須為有效的 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 運算式，並且它可以包括函數、運算子、系統和自訂變數。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-138">The expression must be a valid [!INCLUDE[ssIS](../../../includes/ssis-md.md)] expression, and it can include functions, operators, and system and custom variables.</span></span> <span data-ttu-id="7ed7f-139">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](../expressions/integration-services-ssis-expressions.md)和 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-139">For more information, see [Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>

## <a name="execution-results"></a><span data-ttu-id="7ed7f-140">執行結果</span><span class="sxs-lookup"><span data-stu-id="7ed7f-140">Execution Results</span></span>
 <span data-ttu-id="7ed7f-141">優先順序條件約束可以只使用下列執行結果，或與運算式一起使用。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-141">The precedence constraint can use the following execution results alone or in combination with an expression.</span></span>

-   <span data-ttu-id="7ed7f-142">完成，只要求優先順序可執行檔完成 (無須考慮結果)，就可執行條件約束可執行檔。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-142">Completion requires only that the precedence executable has completed, without regard to outcome, in order for the constrained executable to run.</span></span>

-   <span data-ttu-id="7ed7f-143">成功，要求優先順序可執行檔必須成功完成，才可執行條件約束可執行檔。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-143">Success requires that the precedence executable must complete successfully for the constrained executable to run.</span></span>

-   <span data-ttu-id="7ed7f-144">失敗，要求優先順序可執行檔失敗時，才可執行條件約束可執行檔。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-144">Failure requires that the precedence executable fail for the constrained executable to run.</span></span>

> [!NOTE]
>  <span data-ttu-id="7ed7f-145">只有是同一 `Precedence Constraint` 集合之成員的優先順序條件約束，才可以使用邏輯 AND 條件將其分組。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-145">Only precedence constraints that are members of the same `Precedence Constraint` collection can be grouped in a logical AND condition.</span></span> <span data-ttu-id="7ed7f-146">例如，您無法結合來自兩個「Foreach 迴圈」容器的優先順序條件約束。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-146">For example, you cannot combine precedence constraints from two Foreach Loop containers.</span></span>

## <a name="configuration-of-the-precedence-constraint"></a><span data-ttu-id="7ed7f-147">優先順序條件約束的組態</span><span class="sxs-lookup"><span data-stu-id="7ed7f-147">Configuration of the Precedence Constraint</span></span>
 <span data-ttu-id="7ed7f-148">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-148">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>

 <span data-ttu-id="7ed7f-149">如需可在 [ [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師] 中設定之屬性的詳細資訊，請參閱 [優先順序條件約束編輯器](../precedence-constraint-editor.md)。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-149">For information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, see [Precedence Constraint Editor](../precedence-constraint-editor.md).</span></span>

 <span data-ttu-id="7ed7f-150">如需以程式設計方式設定這些屬性的詳細資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-150">For information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Runtime.PrecedenceConstraint>.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="7ed7f-151">相關工作</span><span class="sxs-lookup"><span data-stu-id="7ed7f-151">Related Tasks</span></span>
 <span data-ttu-id="7ed7f-152">如需有關如何在 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師中設定這些屬性的詳細資訊，請按下列主題之一：</span><span class="sxs-lookup"><span data-stu-id="7ed7f-152">For details about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>

-   [<span data-ttu-id="7ed7f-153">設定優先順序條件約束的屬性</span><span class="sxs-lookup"><span data-stu-id="7ed7f-153">Set the Properties of a Precedence Constraint</span></span>](../set-the-properties-of-a-precedence-constraint.md)

-   [<span data-ttu-id="7ed7f-154">使用捷徑功能表來設定優先順序條件約束的值</span><span class="sxs-lookup"><span data-stu-id="7ed7f-154">Set the Value of a Precedence Constraint by Using the Shortcut Menu</span></span>](../set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)

-   [<span data-ttu-id="7ed7f-155">使用預設的優先順序條件約束來連接工作和容器</span><span class="sxs-lookup"><span data-stu-id="7ed7f-155">Connect Tasks and Containers by Using a Default Precedence Constraint</span></span>](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)

     <span data-ttu-id="7ed7f-156">本主題會提供有關如何設定優先順序條件約束的預設行為，以及如何使用預設的優先順序條件約束來連接可執行檔的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="7ed7f-156">This topic provides information on how to set the default behavior for precedence constraints, and how to connect executables using the default precedence constraints, see.</span></span>

## <a name="related-content"></a><span data-ttu-id="7ed7f-157">相關內容</span><span class="sxs-lookup"><span data-stu-id="7ed7f-157">Related Content</span></span>
 <span data-ttu-id="7ed7f-158">social.technet.microsoft.com 上的技術文件： [SSIS 運算式範例](https://go.microsoft.com/fwlink/?LinkId=220761)</span><span class="sxs-lookup"><span data-stu-id="7ed7f-158">Technical article, [SSIS Expression Examples](https://go.microsoft.com/fwlink/?LinkId=220761), on social.technet.microsoft.com</span></span>

## <a name="see-also"></a><span data-ttu-id="7ed7f-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ed7f-159">See Also</span></span>
 <span data-ttu-id="7ed7f-160">[將運算式加入優先順序條件約束](../add-expressions-to-precedence-constraints.md)[多個優先順序條件約束](../multiple-precedence-constraints.md)</span><span class="sxs-lookup"><span data-stu-id="7ed7f-160">[Add Expressions to Precedence Constraints](../add-expressions-to-precedence-constraints.md) [Multiple Precedence Constraints](../multiple-precedence-constraints.md)</span></span>


