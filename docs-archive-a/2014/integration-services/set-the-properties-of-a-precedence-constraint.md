---
title: 設定優先順序條件約束的屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Precedence Constraint Editor dialog box
- precedence constraints [Integration Services], properties
ms.assetid: d990f600-5c09-4cd5-8528-0a58d79dc9f2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 55b95bdb79d801156bef6198bc0f57accb5d9517
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599574"
---
# <a name="set-the-properties-of-a-precedence-constraint"></a><span data-ttu-id="87062-102">設定優先順序條件約束的屬性</span><span class="sxs-lookup"><span data-stu-id="87062-102">Set the Properties of a Precedence Constraint</span></span>
  <span data-ttu-id="87062-103">若要設定優先順序條件約束的屬性，您可以使用下列其中一項工具：</span><span class="sxs-lookup"><span data-stu-id="87062-103">To set properties on precedence constraints, you can use one of these tools:</span></span>  
  
-   <span data-ttu-id="87062-104">您可以使用 [優先順序條件約束編輯器]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="87062-104">You can use the **Precedence Constraint Editor** dialog box.</span></span>  
  
-   <span data-ttu-id="87062-105">您可以使用 [屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="87062-105">You can use the Properties window.</span></span> <span data-ttu-id="87062-106">[屬性] 視窗會列出屬性，以供您設定在 [優先順序條件約束編輯器]\*\*\*\* 視窗中無法取得的優先順序條件約束。</span><span class="sxs-lookup"><span data-stu-id="87062-106">The Properties window lists properties for configuring precedence constraints that are not available in the **Precedence Constraint Editor** dialog box.</span></span> <span data-ttu-id="87062-107">在 [屬性] 視窗中，您可以提供優先順序條件約束的描述和名稱，並且設定要在設計介面上顯示的優先順序條件約束註解。</span><span class="sxs-lookup"><span data-stu-id="87062-107">In the Properties window, you can provide a description and name of the precedence constraint, and configure the annotation to display for the precedence constraint on the design surface.</span></span>  
  
 <span data-ttu-id="87062-108">下列程序將描述如何使用其中一項工具來設定優先順序條件約束的屬性。</span><span class="sxs-lookup"><span data-stu-id="87062-108">The following procedures describe how to set properties on precedence constraints by using each of these tools.</span></span>  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-precedence-constraint-editor"></a><span data-ttu-id="87062-109">使用優先順序條件約束編輯器來設定優先順序條件約束的屬性</span><span class="sxs-lookup"><span data-stu-id="87062-109">To set the properties of a precedence constraint by using the Precedence Constraint Editor</span></span>  
  
1.  <span data-ttu-id="87062-110">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="87062-110">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="87062-111">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="87062-111">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="87062-112">按一下 **[控制流程]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="87062-112">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="87062-113">按兩下優先順序條件約束，</span><span class="sxs-lookup"><span data-stu-id="87062-113">Double-click the precedence constraint.</span></span>  
  
     <span data-ttu-id="87062-114">[優先順序條件約束編輯器]\*\*\*\* 隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="87062-114">The **Precedence Constraint Editor** opens.</span></span>  
  
5.  <span data-ttu-id="87062-115">在 [評估作業]\*\*\*\* 下拉式清單中，選取評估作業。</span><span class="sxs-lookup"><span data-stu-id="87062-115">In the **Evaluation operation** drop-down list, select an evaluation operation.</span></span>  
  
6.  <span data-ttu-id="87062-116">在 `Value` 下拉式清單中，選取優先順序可執行檔的執行結果。</span><span class="sxs-lookup"><span data-stu-id="87062-116">In the `Value` drop-down list, select the execution result of the precedence executable.</span></span>  
  
7.  <span data-ttu-id="87062-117">如果評估作業使用運算式，請在方塊中 `Expression` 輸入運算式，然後按一下 [**測試**] 來評估運算式。</span><span class="sxs-lookup"><span data-stu-id="87062-117">If the evaluation operation uses an expression, in the `Expression` box, type an expression, and click **Test** to evaluate the expression.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="87062-118">變數名稱會區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="87062-118">Variable names are case-sensitive.</span></span>  
  
8.  <span data-ttu-id="87062-119">如果有多個工作或容器連接到受條件約束的可執行檔，請選取 [**邏輯 AND** ]，以指定所有先前可執行檔的執行結果都必須評估為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="87062-119">If multiple tasks or containers are connected to the constrained executable, select **Logical AND** to specify that the execution results of all preceding executables must evaluate to `true`.</span></span> <span data-ttu-id="87062-120">選取 [**邏輯 OR** ]，以指定只有一個執行結果必須評估為 `true` 。</span><span class="sxs-lookup"><span data-stu-id="87062-120">Select **Logical OR** to specify that only one execution result must evaluate to `true`.</span></span>  
  
9. <span data-ttu-id="87062-121">按一下 [確定]\*\*\*\*，以關閉 [優先順序條件約束編輯器]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="87062-121">Click **OK** to close the **Precedence Constraint Editor**.</span></span>  
  
10. <span data-ttu-id="87062-122">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="87062-122">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-properties-window"></a><span data-ttu-id="87062-123">使用屬性視窗來設定優先順序條件約束的屬性</span><span class="sxs-lookup"><span data-stu-id="87062-123">To set the properties of a precedence constraint by using the Properties window</span></span>  
  
1.  <span data-ttu-id="87062-124">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含要修改之封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="87062-124">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want to modify.</span></span>  
  
2.  <span data-ttu-id="87062-125">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="87062-125">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="87062-126">按一下 [**控制流程**] 索引標籤。在 [**控制流程**] 索引標籤的設計介面上，以滑鼠右鍵按一下優先順序條件約束，然後按一下 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="87062-126">Click the **Control Flow** tab. On the design surface of the **Control Flow** tab, right-click the precedence constraint, and then click **Properties**.</span></span> <span data-ttu-id="87062-127">在 [屬性] 視窗中，修改屬性值。</span><span class="sxs-lookup"><span data-stu-id="87062-127">In the Properties window, modify the property values.</span></span>  
  
4.  <span data-ttu-id="87062-128">在 [屬性]\*\*\*\* 視窗中，設定優先順序條件約束的下列讀取/寫入屬性：</span><span class="sxs-lookup"><span data-stu-id="87062-128">In the **Properties** window, set the following read/write properties of precedence constraints:</span></span>  
  
    |<span data-ttu-id="87062-129">讀取/寫入屬性</span><span class="sxs-lookup"><span data-stu-id="87062-129">Read/write property</span></span>|<span data-ttu-id="87062-130">組態動作</span><span class="sxs-lookup"><span data-stu-id="87062-130">Configuration action</span></span>|  
    |--------------------------|--------------------------|  
    |<span data-ttu-id="87062-131">描述</span><span class="sxs-lookup"><span data-stu-id="87062-131">Description</span></span>|<span data-ttu-id="87062-132">提供描述。</span><span class="sxs-lookup"><span data-stu-id="87062-132">Provide a description.</span></span>|  
    |<span data-ttu-id="87062-133">EvalOp</span><span class="sxs-lookup"><span data-stu-id="87062-133">EvalOp</span></span>|<span data-ttu-id="87062-134">選取評估作業。</span><span class="sxs-lookup"><span data-stu-id="87062-134">Select an evaluation operation.</span></span> <span data-ttu-id="87062-135">如果 `Expression` 已選取、 **[Expressionandconstant]** 或 **[expressionorconstant**作業，您可以指定運算式。</span><span class="sxs-lookup"><span data-stu-id="87062-135">If the `Expression`, **ExpressionAndConstant**, or **ExpressionOrConstant** operation is selected, you can specify an expression.</span></span>|  
    |<span data-ttu-id="87062-136">運算是</span><span class="sxs-lookup"><span data-stu-id="87062-136">Expression</span></span>|<span data-ttu-id="87062-137">如果評估作業包含運算式，請提供一個運算式。</span><span class="sxs-lookup"><span data-stu-id="87062-137">If the evaluation operation includes and expression, provide an expression.</span></span> <span data-ttu-id="87062-138">運算式必須評估為布林。</span><span class="sxs-lookup"><span data-stu-id="87062-138">The expression must evaluate to a Boolean.</span></span> <span data-ttu-id="87062-139">如需運算式語言的詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 運算式](expressions/integration-services-ssis-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="87062-139">For more information about the expression language, see [Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md).</span></span>|  
    |<span data-ttu-id="87062-140">LogicalAnd</span><span class="sxs-lookup"><span data-stu-id="87062-140">LogicalAnd</span></span>|<span data-ttu-id="87062-141">設定 `LogicalAnd` 為指定當多個可執行檔在和連結到受條件約束的可執行檔時，是否要與其他優先順序條件約束一起評估優先順序條件約束</span><span class="sxs-lookup"><span data-stu-id="87062-141">Set `LogicalAnd` to specify whether the precedence constraint is evaluated in concert with other precedence constraints, when multiple executables precede and are linked to the constrained executable</span></span>|  
    |<span data-ttu-id="87062-142">名稱</span><span class="sxs-lookup"><span data-stu-id="87062-142">Name</span></span>|<span data-ttu-id="87062-143">更新優先順序條件約束的名稱。</span><span class="sxs-lookup"><span data-stu-id="87062-143">Update the name of the precedence constraint.</span></span>|  
    |<span data-ttu-id="87062-144">ShowAnnotation</span><span class="sxs-lookup"><span data-stu-id="87062-144">ShowAnnotation</span></span>|<span data-ttu-id="87062-145">指定要使用之註解的類型。</span><span class="sxs-lookup"><span data-stu-id="87062-145">Specify the type of annotation to use.</span></span> <span data-ttu-id="87062-146">選擇 [Never]\*\*\*\* 以停用註解，選擇 [AsNeeded]\*\*\*\* 以視需要啟用註解，選擇 [ConstraintName]\*\*\*\* 以使用 Name 屬性的值來自動註解，選擇 [ConstraintDescription]\*\*\*\* 以使用 Description 屬性的值來自動註解，以及選擇 [ConstraintOptions]\*\*\*\* 以使用 Value 和 Expression 屬性的值來自動註解。</span><span class="sxs-lookup"><span data-stu-id="87062-146">Choose **Never** to disable annotations, **AsNeeded** to enable annotation on demand, **ConstraintName** to automatically annotate using the value of the Name property, **ConstraintDescription** to automatically annotate using the value of the Description property, and **ConstraintOptions** to automatically annotate using the values of the Value and Expression properties.</span></span>|  
    |<span data-ttu-id="87062-147">值</span><span class="sxs-lookup"><span data-stu-id="87062-147">Value</span></span>|<span data-ttu-id="87062-148">如果 EvalOP 屬性中指定的評估作業包含條件約束，請選取具有條件約束之可執行檔的執行結果。</span><span class="sxs-lookup"><span data-stu-id="87062-148">If the evaluation operation specified in the EvalOP property includes a constraint, select the execution result of the constraining executable.</span></span>|  
  
5.  <span data-ttu-id="87062-149">關閉 [屬性] 視窗。</span><span class="sxs-lookup"><span data-stu-id="87062-149">Close the Properties window.</span></span>  
  
6.  <span data-ttu-id="87062-150">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="87062-150">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87062-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="87062-151">See Also</span></span>  
 <span data-ttu-id="87062-152">[優先順序條件約束](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="87062-152">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="87062-153">[使用預設的優先順序條件約束來連接工作和容器](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="87062-153">[Connect Tasks and Containers by Using a Default Precedence Constraint](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span></span>  
 <span data-ttu-id="87062-154">[使用快捷方式功能表來設定優先順序條件約束的值](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span><span class="sxs-lookup"><span data-stu-id="87062-154">[Set the Value of a Precedence Constraint by Using the Shortcut Menu](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span></span>  
 [<span data-ttu-id="87062-155">在優先順序條件約束中使用運算式</span><span class="sxs-lookup"><span data-stu-id="87062-155">Use an Expression in a Precedence Constraint</span></span>](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  
