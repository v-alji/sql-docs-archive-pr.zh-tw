---
title: For 迴圈容器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.forloopcontainerdetails.f1
helpviewer_keywords:
- repeating control flow
- containers [Integration Services], For Loop
- For Loop containers
ms.assetid: 44cf7355-992b-4bbf-a28c-bfb012de06f6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a6c864779237fdbf4dd249f87b7c06655293c047
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584691"
---
# <a name="for-loop-container"></a><span data-ttu-id="2308e-102">For 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="2308e-102">For Loop Container</span></span>
  <span data-ttu-id="2308e-103">「For 迴圈」容器定義封裝中重複的控制流程。</span><span class="sxs-lookup"><span data-stu-id="2308e-103">The For Loop container defines a repeating control flow in a package.</span></span> <span data-ttu-id="2308e-104">迴圈實作與程式設計語言中 **For** 迴圈的結構類似。</span><span class="sxs-lookup"><span data-stu-id="2308e-104">The loop implementation is similar to the **For** looping structure in programming languages.</span></span> <span data-ttu-id="2308e-105">在每次迴圈重複中，「For 迴圈」容器都會評估運算式並重複其工作流程，直到運算式評估為 `False` 為止。</span><span class="sxs-lookup"><span data-stu-id="2308e-105">In each repeat of the loop, the For Loop container evaluates an expression and repeats its workflow until the expression evaluates to `False`.</span></span>  
  
 <span data-ttu-id="2308e-106">「For 迴圈」容器使用下列元素定義迴圈：</span><span class="sxs-lookup"><span data-stu-id="2308e-106">The For Loop container usesthe following elements to define the loop:</span></span>  
  
-   <span data-ttu-id="2308e-107">選擇性初始化運算式，會指派值給迴圈計數器。</span><span class="sxs-lookup"><span data-stu-id="2308e-107">An optional initialization expression that assigns values to the loop counters.</span></span>  
  
-   <span data-ttu-id="2308e-108">評估運算式，其中含有用來測試迴圈應停止或繼續的運算式。</span><span class="sxs-lookup"><span data-stu-id="2308e-108">An evaluation expression that contains the expression used to test whether the loop should stop or continue.</span></span>  
  
-   <span data-ttu-id="2308e-109">選擇性反覆運算的運算式，會累加或遞減迴圈計數器。</span><span class="sxs-lookup"><span data-stu-id="2308e-109">An optional iteration expression that increments or decrements the loop counter.</span></span>  
  
 <span data-ttu-id="2308e-110">下列圖表顯示含有傳送郵件工作的「For 迴圈」容器。</span><span class="sxs-lookup"><span data-stu-id="2308e-110">The following diagram shows a For Loop container with a Send Mail task.</span></span> <span data-ttu-id="2308e-111">如果初始化運算式為 `@Counter = 0`、評估運算式為 `@Counter < 4`，且反覆運算的運算式為 `@Counter = @Counter + 1`，則迴圈會重複四次並傳送四則電子郵件訊息。</span><span class="sxs-lookup"><span data-stu-id="2308e-111">If the initialization expression is `@Counter = 0`, the evaluation expression is `@Counter < 4`, and the iteration expression is `@Counter = @Counter + 1`, the loop repeats four times and sends four e-mail messages.</span></span>  
  
 <span data-ttu-id="2308e-112">![For 迴圈容器會重複工作四次](../media/ssis-forloop.gif "For 迴圈容器會重複工作四次")</span><span class="sxs-lookup"><span data-stu-id="2308e-112">![A For Loop container repeats a task four times](../media/ssis-forloop.gif "A For Loop container repeats a task four times")</span></span>  
  
 <span data-ttu-id="2308e-113">運算式必須是有效的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 運算式。</span><span class="sxs-lookup"><span data-stu-id="2308e-113">The expressions must be valid [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expressions.</span></span>  
  
 <span data-ttu-id="2308e-114">若要建立初始化和指派運算式，可使用指派運算子 (=)。</span><span class="sxs-lookup"><span data-stu-id="2308e-114">To create the initialization and assignment expressions, you can use the assignment operator (=).</span></span> <span data-ttu-id="2308e-115">除了「For 迴圈」容器中的初始化和指派運算式類型可使用此運算子外，Integration Services 運算式文法不另外支援此運算子。</span><span class="sxs-lookup"><span data-stu-id="2308e-115">This operator is not otherwise supported by the Integration Services expression grammar and can only be used by the initialization and assignment expression types in the For Loop container.</span></span> <span data-ttu-id="2308e-116">任何使用指派運算子的運算式都必須使用此語法 `@Var = <expression>`，其中 **Var** 是執行階段變數，而 \<expression> 是遵循 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 運算式語法規則的運算式。</span><span class="sxs-lookup"><span data-stu-id="2308e-116">Any expression that uses the assignment operator must have the syntax `@Var = <expression>`, where **Var** is a run-time variable and \<expression> is an expression that follows the rules of the [!INCLUDE[ssIS](../../../includes/ssis-md.md)] expression syntax.</span></span> <span data-ttu-id="2308e-117">運算式可包含變數、常值，以及任何 SSIS 運算式文法支援的運算子和函數。</span><span class="sxs-lookup"><span data-stu-id="2308e-117">The expression can include the variables, literals, and any operators and functions that the SSIS expression grammar supports.</span></span> <span data-ttu-id="2308e-118">運算式必須評估為可轉換成變數資料類型的資料類型。</span><span class="sxs-lookup"><span data-stu-id="2308e-118">The expression must evaluate to a data type that can be cast to the data type of the variable.</span></span>  
  
 <span data-ttu-id="2308e-119">「For 迴圈」容器只能有一個評估運算式。</span><span class="sxs-lookup"><span data-stu-id="2308e-119">A For Loop container can have only one evaluation expression.</span></span> <span data-ttu-id="2308e-120">這表示「For 迴圈」容器執行其所有控制流程元素的次數皆相同。</span><span class="sxs-lookup"><span data-stu-id="2308e-120">This means that the For Loop container runs all its control flow elements the same number of times.</span></span> <span data-ttu-id="2308e-121">由於「For 迴圈」容器可包含其他「For 迴圈」容器，因此您可以在封裝中建立巢狀迴圈並實作複雜的迴圈。</span><span class="sxs-lookup"><span data-stu-id="2308e-121">Because the For Loop container can include other For Loop containers, you can build nested loops and implement complex looping in packages.</span></span>  
  
 <span data-ttu-id="2308e-122">您可以在「For 迴圈」容器上設定交易屬性，用來定義封裝控制流程子集的交易。</span><span class="sxs-lookup"><span data-stu-id="2308e-122">You can set a transaction property on the For Loop container to define a transaction for a subset of the package control flow.</span></span> <span data-ttu-id="2308e-123">使用這種方式，可以以更細微的層級管理交易。</span><span class="sxs-lookup"><span data-stu-id="2308e-123">In this way, you can manage transactions at a more granular level.</span></span> <span data-ttu-id="2308e-124">例如，如果「For 迴圈」容器多次重複更新資料表中資料的控制流程，您可設定讓「For 迴圈」容器及其控制流程使用交易，以確保若非所有資料都成功更新，則不更新任何資料。</span><span class="sxs-lookup"><span data-stu-id="2308e-124">For example, if a For Loop container repeats a control flow that updates data in a table multiple times, you can configure the For Loop and its control flow to use a transaction to ensure that if not all data is updated successfully, no data is updated.</span></span> <span data-ttu-id="2308e-125">如需詳細資訊，請參閱 [Integration Services 交易](../integration-services-transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="2308e-125">For more information, see [Integration Services Transactions](../integration-services-transactions.md).</span></span>  
  
## <a name="configuration-of-the-for-loop-container"></a><span data-ttu-id="2308e-126">設定 For 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="2308e-126">Configuration of the For Loop Container</span></span>  
 <span data-ttu-id="2308e-127">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="2308e-127">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="2308e-128">如需有關可以在「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="2308e-128">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="2308e-129">For 迴圈編輯器</span><span class="sxs-lookup"><span data-stu-id="2308e-129">For Loop Editor</span></span>](../for-loop-editor.md)  
  
-   [<span data-ttu-id="2308e-130">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="2308e-130">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="2308e-131">如需有關以程式設計方式設定這些屬性的詳細資訊，請參閱《開發人員指南》中 **T:Microsoft.SqlServer.Dts.Runtime.ForLoop** 類別的文件。</span><span class="sxs-lookup"><span data-stu-id="2308e-131">For more information about programmatically setting these properties, see documentation for the **T:Microsoft.SqlServer.Dts.Runtime.ForLoop** class in the Developer Guide.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="2308e-132">相關工作</span><span class="sxs-lookup"><span data-stu-id="2308e-132">Related Tasks</span></span>  
 <span data-ttu-id="2308e-133">如需有關如何設定「For 迴圈」容器的詳細資訊，請參閱下列主題。</span><span class="sxs-lookup"><span data-stu-id="2308e-133">For information about how to configure a For Loop Container, see the following topics.</span></span>  
  
-   [<span data-ttu-id="2308e-134">設定 For 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="2308e-134">Configure a For Loop Container</span></span>](for-loop-container.md)  
  
-   [<span data-ttu-id="2308e-135">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="2308e-135">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="2308e-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2308e-136">See Also</span></span>  
 <span data-ttu-id="2308e-137">[控制流程](control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="2308e-137">[Control Flow](control-flow.md) </span></span>  
 [<span data-ttu-id="2308e-138">Integration Services &#40;SSIS&#41; 運算式</span><span class="sxs-lookup"><span data-stu-id="2308e-138">Integration Services &#40;SSIS&#41; Expressions</span></span>](../expressions/integration-services-ssis-expressions.md)  
  
  
