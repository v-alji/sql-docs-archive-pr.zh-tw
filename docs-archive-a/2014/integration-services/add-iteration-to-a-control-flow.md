---
title: 將反復專案加入至控制流程 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- repeating workflows
- adding iterations
- control flow [Integration Services], iterations
- expressions [Integration Services], control flow
- iterations [Integration Services]
- For Loop containers
ms.assetid: eb3a7494-88ae-4165-9d0f-58715eb1734a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2b576ab080c541ef96987d3375215185f5cadb46
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595243"
---
# <a name="add-iteration-to-a-control-flow"></a><span data-ttu-id="08139-102">將反覆運算加入控制流程</span><span class="sxs-lookup"><span data-stu-id="08139-102">Add Iteration to a Control Flow</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="08139-103">包括 For 迴圈容器，該容器為控制流程項目，可簡化在套件中包括有條件地重複控制流程的迴圈。</span><span class="sxs-lookup"><span data-stu-id="08139-103">includes the For Loop container, a control flow element that makes it simple to include looping that conditionally repeats a control flow in a package.</span></span> <span data-ttu-id="08139-104">如需詳細資訊，請參閱 [For 迴圈容器](control-flow/for-loop-container.md)為止。</span><span class="sxs-lookup"><span data-stu-id="08139-104">For more information, see [For Loop Container](control-flow/for-loop-container.md).</span></span>  
  
 <span data-ttu-id="08139-105">「For 迴圈」容器會評估迴圈中每個反覆運算的條件，並在條件評估為 False 時停止。</span><span class="sxs-lookup"><span data-stu-id="08139-105">The For Loop container evaluates a condition on each iteration of the loop, and stops when the condition evaluates to false.</span></span> <span data-ttu-id="08139-106">「For 迴圈」容器包括許多運算式，可用於初始化迴圈，指定停止執行重複控制流程的評估條件，以及為更新評估條件之比較值的運算式指派值。</span><span class="sxs-lookup"><span data-stu-id="08139-106">The For Loop container includes expressions for initializing the loop, specifying the evaluation condition that stops execution of the repeating control flow, and assigning a value to an expression that updates the value against which the evaluation condition is compared.</span></span> <span data-ttu-id="08139-107">您必須提供評估條件，但初始化及指派運算式是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="08139-107">You must provide an evaluation condition, but initialization and assignment expressions are optional.</span></span>  
  
 <span data-ttu-id="08139-108">「For 迴圈」容器不提供功能，它僅提供可在其中建立可重複控制流程的結構。</span><span class="sxs-lookup"><span data-stu-id="08139-108">The For Loop container provides no functionality; it provides only the structure in which you build the repeatable control flow.</span></span> <span data-ttu-id="08139-109">若要提供容器功能，「For 迴圈」容器中必須至少包括一個工作。</span><span class="sxs-lookup"><span data-stu-id="08139-109">To provide container functionality, you must include at least one task in the For Loop container.</span></span> <span data-ttu-id="08139-110">如需詳細資訊，請參閱 [Integration Services Tasks](control-flow/integration-services-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="08139-110">For more information, see [Integration Services Tasks](control-flow/integration-services-tasks.md).</span></span>  
  
 <span data-ttu-id="08139-111">「For 迴圈」容器可以包括具有多個工作的控制流程，還可以包括其他容器。</span><span class="sxs-lookup"><span data-stu-id="08139-111">The For Loop container can include a control flow with multiple tasks, and can include other containers.</span></span> <span data-ttu-id="08139-112">將工作及容器加入「For 迴圈」容器與將它們加入封裝類似，不同之處在於，您要將工作及容器拖曳至「For 迴圈」容器而不是封裝。</span><span class="sxs-lookup"><span data-stu-id="08139-112">Adding tasks and containers to a For Loop container is similar to adding them to a package, except you drag the tasks and containers to the For Loop container instead of to the package.</span></span> <span data-ttu-id="08139-113">如果「For 迴圈」容器包含一個以上的工作或容器，則您可以如同在封裝中所做的一樣，使用優先順序條件約束來連接它們。</span><span class="sxs-lookup"><span data-stu-id="08139-113">If the For Loop container includes more than one task or container, you can connect them using precedence constraints just as you do in a package.</span></span> <span data-ttu-id="08139-114">如需詳細資訊，請參閱 [優先順序條件約束](control-flow/precedence-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="08139-114">For more information, see [Precedence Constraints](control-flow/precedence-constraints.md).</span></span>  
  
## <a name="using-expressions-in-for-loop-configuration"></a><span data-ttu-id="08139-115">在 For 迴圈組態中使用運算式</span><span class="sxs-lookup"><span data-stu-id="08139-115">Using Expressions in For Loop Configuration</span></span>  
 <span data-ttu-id="08139-116">藉由指定評估條件、初始化值或指派值來設定「For 迴圈」容器時，您可以使用常值或運算式。</span><span class="sxs-lookup"><span data-stu-id="08139-116">When you configure the For Loop container by specifying an evaluation condition, initialization value, or assignment value, you can use either literals or expressions.</span></span>  
  
 <span data-ttu-id="08139-117">運算式可以包含變數。</span><span class="sxs-lookup"><span data-stu-id="08139-117">The expressions can include variables.</span></span> <span data-ttu-id="08139-118">使用變數的優點是，可以在執行階段對它們進行更新，使封裝更為靈活也易於管理。</span><span class="sxs-lookup"><span data-stu-id="08139-118">The advantage of using variables is that they can be updated at run time, making the packages more flexible and easier to manage.</span></span> <span data-ttu-id="08139-119">運算式的最大長度為 4000 個字元。</span><span class="sxs-lookup"><span data-stu-id="08139-119">The maximum length of an expression is 4000 characters.</span></span>  
  
 <span data-ttu-id="08139-120">在運算式中指定變數時，必須在變數名稱之前加上 at 符號 (@)。</span><span class="sxs-lookup"><span data-stu-id="08139-120">When you specify a variable in an expression, you must preface the variable name with the at sign (@).</span></span> <span data-ttu-id="08139-121">例如，針對名為的變數 `Counter` ，請 @Counter 在「for 迴圈」容器所使用的運算式中輸入。</span><span class="sxs-lookup"><span data-stu-id="08139-121">For example, for a variable named `Counter`, enter @Counter in the expression that the For Loop container uses.</span></span> <span data-ttu-id="08139-122">如果您在變數中包括命名空間屬性，則您必須使用括號將變數與命名空間括起來。</span><span class="sxs-lookup"><span data-stu-id="08139-122">If you include the namespace property on the variable, you must enclose the variable and namespace in brackets.</span></span> <span data-ttu-id="08139-123">例如，針對 `Counter` 命名空間中的變數 `MyNamespace` ，請輸入 [ @MyNamespace::Counter ]。</span><span class="sxs-lookup"><span data-stu-id="08139-123">For example, for a `Counter` variable in the `MyNamespace` namespace, type [@MyNamespace::Counter].</span></span>  
  
 <span data-ttu-id="08139-124">「For 迴圈」容器使用的變數必須定義在「For 迴圈」容器的範圍內，或封裝容器階層中任何更高容器的範圍內。</span><span class="sxs-lookup"><span data-stu-id="08139-124">The variables that the For Loop container uses must be defined in the scope of the For Loop container or in the scope of any container that is higher in the package container hierarchy.</span></span> <span data-ttu-id="08139-125">例如，「For 迴圈」容器可以使用其範圍內定義的變數，也可以使用封裝範圍內定義的變數。</span><span class="sxs-lookup"><span data-stu-id="08139-125">For example, a For Loop container can use variables defined in its scope and also variables defined in package scope.</span></span> <span data-ttu-id="08139-126">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 變數](integration-services-ssis-variables.md)和[在封裝中使用變數](../../2014/integration-services/use-variables-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="08139-126">For more information, see [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) and [Use Variables in Packages](../../2014/integration-services/use-variables-in-packages.md).</span></span>  
  
 <span data-ttu-id="08139-127">[!INCLUDE[ssIS](../includes/ssis-md.md)] 運算式文法提供完整的運算子及函數集合，以實作評估、初始化或指派所使用的複雜運算式。</span><span class="sxs-lookup"><span data-stu-id="08139-127">The [!INCLUDE[ssIS](../includes/ssis-md.md)] expression grammar provides a complete set of operators and functions for implementing complex expressions used for evaluation, initialization, or assignment.</span></span> <span data-ttu-id="08139-128">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](expressions/integration-services-ssis-expressions.md)為止。</span><span class="sxs-lookup"><span data-stu-id="08139-128">For more information, see [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>  
  
### <a name="to-implement-a-for-loop-container-in-a-control-flow"></a><span data-ttu-id="08139-129">在控制流程中實作 For 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="08139-129">To implement a For Loop container in a control flow</span></span>  
  
1.  <span data-ttu-id="08139-130">將「For 迴圈」容器加入封裝。</span><span class="sxs-lookup"><span data-stu-id="08139-130">Add the For Loop container to the package.</span></span> <span data-ttu-id="08139-131">如需詳細資訊，請參閱[在控制流程中加入或刪除工作或容器](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span><span class="sxs-lookup"><span data-stu-id="08139-131">For more information, see [Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span></span>  
  <span data-ttu-id="08139-132">.</span><span class="sxs-lookup"><span data-stu-id="08139-132">.</span></span>  
  
2.  <span data-ttu-id="08139-133">將工作和容器加入「For 迴圈」容器。</span><span class="sxs-lookup"><span data-stu-id="08139-133">Add tasks and containers to the For Loop container.</span></span> <span data-ttu-id="08139-134">如需詳細資訊，請參閱[在控制流程中加入或刪除工作或容器](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span><span class="sxs-lookup"><span data-stu-id="08139-134">For more information, see [Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span></span>  
  <span data-ttu-id="08139-135">.</span><span class="sxs-lookup"><span data-stu-id="08139-135">.</span></span>  
  
3.  <span data-ttu-id="08139-136">使用優先順序條件約束連接「For 迴圈」容器中的工作和容器。</span><span class="sxs-lookup"><span data-stu-id="08139-136">Connect tasks and containers in the For Loop container using precedence constraints.</span></span> <span data-ttu-id="08139-137">如需詳細資訊，請參閱 [使用預設的優先順序條件約束來連接工作和容器](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)。</span><span class="sxs-lookup"><span data-stu-id="08139-137">For more information, see [Connect Tasks and Containers by Using a Default Precedence Constraint](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md).</span></span>  
  
4.  <span data-ttu-id="08139-138">設定「For 迴圈」容器。</span><span class="sxs-lookup"><span data-stu-id="08139-138">Configure the For Loop container.</span></span> <span data-ttu-id="08139-139">如需詳細資訊，請參閱 [設定 For 迴圈容器](../../2014/integration-services/configure-a-for-loop-container.md)為止。</span><span class="sxs-lookup"><span data-stu-id="08139-139">For more information, see [Configure a For Loop Container](../../2014/integration-services/configure-a-for-loop-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08139-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="08139-140">See Also</span></span>  
 <span data-ttu-id="08139-141">[在控制流程中加入或刪除工作或容器](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="08139-141">[Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span></span>  
 <span data-ttu-id="08139-142">[將元件分組或取消群組](group-or-ungroup-components.md) </span><span class="sxs-lookup"><span data-stu-id="08139-142">[Group or Ungroup Components](group-or-ungroup-components.md) </span></span>  
 <span data-ttu-id="08139-143">[使用預設的優先順序條件約束來連接工作和容器](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="08139-143">[Connect Tasks and Containers by Using a Default Precedence Constraint](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span></span>  
 <span data-ttu-id="08139-144">[將列舉新增至控制流程](../../2014/integration-services/add-enumeration-to-a-control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="08139-144">[Add Enumeration to a Control Flow](../../2014/integration-services/add-enumeration-to-a-control-flow.md) </span></span>  
 [<span data-ttu-id="08139-145">控制流程</span><span class="sxs-lookup"><span data-stu-id="08139-145">Control Flow</span></span>](control-flow/control-flow.md)  
  
  
