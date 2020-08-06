---
title: 在資料流程元件中使用運算式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- components [Integration Services], data flow
- expressions [Integration Services], data flow components
ms.assetid: 9181b998-d24a-41fb-bb3c-14eee34f910d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 653bf468d0af6d44c5abe7344fcc13f93f86b430
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703093"
---
# <a name="use-an-expression-in-a-data-flow-component"></a><span data-ttu-id="20a50-102">在資料流程元件中使用運算式</span><span class="sxs-lookup"><span data-stu-id="20a50-102">Use an Expression in a Data Flow Component</span></span>
  <span data-ttu-id="20a50-103">此程序描述如何將運算式加入「條件式分割」轉換或「衍生的資料行」轉換。</span><span class="sxs-lookup"><span data-stu-id="20a50-103">This procedure describes how to add an expression to the Conditional Split transformation or to the Derived Column transformation.</span></span> <span data-ttu-id="20a50-104">「條件式分割」轉換會使用運算式，定義將資料列導向轉換輸出的條件，而「衍生的資料行」轉換則使用運算式，定義指派給資料行的值。</span><span class="sxs-lookup"><span data-stu-id="20a50-104">The Conditional Split transformation uses expressions to define the conditions that direct data rows to a transformation output, and the Derived Column transformation uses expressions to define values assigned to columns.</span></span>  
  
 <span data-ttu-id="20a50-105">若要在轉換中實作運算式，封裝必須至少包括一個「資料流程」工作和一個來源。</span><span class="sxs-lookup"><span data-stu-id="20a50-105">To implement an expression in a transformation, the package must already include at least one Data Flow task and a source.</span></span> <span data-ttu-id="20a50-106">如需有關將項目加入封裝的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="20a50-106">For information about adding items to packages, see the following topics:</span></span>  
  
-   [<span data-ttu-id="20a50-107">在控制流程中加入或刪除工作或容器</span><span class="sxs-lookup"><span data-stu-id="20a50-107">Add or Delete a Task or a Container in a Control Flow</span></span>](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
    
  
-   [<span data-ttu-id="20a50-108">在資料流程中加入或刪除元件</span><span class="sxs-lookup"><span data-stu-id="20a50-108">Add or Delete a Component in a Data Flow</span></span>](data-flow/add-or-delete-a-component-in-a-data-flow.md)  
  
-   [<span data-ttu-id="20a50-109">連接資料流程中的元件</span><span class="sxs-lookup"><span data-stu-id="20a50-109">Connect Components in a Data Flow</span></span>](data-flow/connect-components-in-a-data-flow.md)  
  
### <a name="to-create-an-expression"></a><span data-ttu-id="20a50-110">若要建立運算式</span><span class="sxs-lookup"><span data-stu-id="20a50-110">To create an expression</span></span>  
  
1.  <span data-ttu-id="20a50-111">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="20a50-111">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="20a50-112">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="20a50-112">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="20a50-113">在 [[!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師] 中，按一下 [控制流程]\*\*\*\* 索引標籤，然後再按包含要在其中實作運算式之資料流程的「資料流程」工作。</span><span class="sxs-lookup"><span data-stu-id="20a50-113">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Control Flow** tab, and then click the Data Flow task that contains the data flow in which you want to implement an expression.</span></span>  
  
4.  <span data-ttu-id="20a50-114">按一下 [資料流程]\*\*\*\* 索引標籤，然後將「條件式分割」或「衍生的資料行」轉換，從 [工具箱]\*\*\*\* 拖曳至設計介面。</span><span class="sxs-lookup"><span data-stu-id="20a50-114">Click the **Data Flow** tab, and drag either a Conditional Split or Derived Column transformation from the **Toolbox** to the design surface.</span></span>  
  
5.  <span data-ttu-id="20a50-115">將綠色連接子從來源或轉換拖曳至「條件式分割」或「衍生的資料行」轉換。</span><span class="sxs-lookup"><span data-stu-id="20a50-115">Drag the green connector from the source or a transformation to the Conditional Split or Derived Column transformation.</span></span>  
  
6.  <span data-ttu-id="20a50-116">按兩下轉換，以開啟其對話方塊。</span><span class="sxs-lookup"><span data-stu-id="20a50-116">Double-click the transformation to open its dialog box.</span></span>  
  
7.  <span data-ttu-id="20a50-117">在左窗格中，展開 [變數]\*\*\*\*，以顯示系統變數和使用者自訂變數，並展開 [資料行]\*\*\*\*，以顯示轉換輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="20a50-117">In the left pane, expand **Variables** to display system and user-defined variables, and expand **Columns** to display the transformation input columns.</span></span>  
  
8.  <span data-ttu-id="20a50-118">在右窗格中，展開 [數學函數]\*\*\*\*、[字串函數]\*\*\*\*、[日期/時間函數]\*\*\*\*、[NULL 函數]\*\*\*\*、[類型轉換]\*\*\*\* 和 [運算子]\*\*\*\*，以存取運算式文法所提供的函數、轉換和運算子。</span><span class="sxs-lookup"><span data-stu-id="20a50-118">In the right pane, expand **Mathematical Functions**, **String Functions**, **Date/Time Functions**, **NULL Functions**, **Type Casts**, and **Operators** to access the functions, the casts, and the operators that the expression grammar provides.</span></span>  
  
9. <span data-ttu-id="20a50-119">因轉換的不同，請執行下列其中之一，以建立運算式：</span><span class="sxs-lookup"><span data-stu-id="20a50-119">Depending on the transformation, do one of the following to build an expression:</span></span>  
  
    -   <span data-ttu-id="20a50-120">在 [條件式分割轉換編輯器]\*\*\*\* 對話方塊中，將變數、資料行、函數、運算子和轉換拖曳至 [條件]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="20a50-120">In the **Conditional Split Transformation Editor** dialog box, drag variables, columns, functions, operators, and casts to the **Condition** column.</span></span> <span data-ttu-id="20a50-121">您也可以在 [條件]\*\*\*\* 資料行中直接鍵入運算式。</span><span class="sxs-lookup"><span data-stu-id="20a50-121">Alternatively, you can type an expression directly in the **Condition** column.</span></span>  
  
    -   <span data-ttu-id="20a50-122">在 [衍生的資料行轉換編輯器]\*\*\*\* 對話方塊中，將變數、資料行、函數、運算子和轉換拖曳至 [運算式]\*\*\*\* 資料行。</span><span class="sxs-lookup"><span data-stu-id="20a50-122">In the **Derived Column Transformation Editor** dialog box, drag variables, columns, functions, operators, and casts to the **Expression** column.</span></span> <span data-ttu-id="20a50-123">您也可以在 [運算式]\*\*\*\* 資料行中直接鍵入運算式。</span><span class="sxs-lookup"><span data-stu-id="20a50-123">Alternatively, you can type an expression directly in the **Expression** column.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="20a50-124">從 [條件]\*\*\*\* 資料行或 [運算式]\*\*\*\* 資料行移除焦點時，運算式文字可能會反白顯示，指示運算式語法不正確。</span><span class="sxs-lookup"><span data-stu-id="20a50-124">When you remove the focus from the **Condition** column or the **Expression** column, the expression text might be highlighted to indicate that the expression syntax is incorrect.</span></span>  
  
10. <span data-ttu-id="20a50-125">按一下 **[確定]**，結束對話方塊。</span><span class="sxs-lookup"><span data-stu-id="20a50-125">Click **OK** to exit the dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="20a50-126">如果運算式無效，則會出現警示，描述運算式中的語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="20a50-126">If the expression is not valid, an alert appears describing the syntax errors in the expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20a50-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20a50-127">See Also</span></span>  
 <span data-ttu-id="20a50-128">[Integration Services &#40;SSIS&#41; 運算式](expressions/integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="20a50-128">[Integration Services &#40;SSIS&#41; Expressions](expressions/integration-services-ssis-expressions.md) </span></span>  
 <span data-ttu-id="20a50-129">[條件式分割轉換](data-flow/transformations/conditional-split-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="20a50-129">[Conditional Split Transformation](data-flow/transformations/conditional-split-transformation.md) </span></span>  
 <span data-ttu-id="20a50-130">[Derived Column Transformation](data-flow/transformations/derived-column-transformation.md) </span><span class="sxs-lookup"><span data-stu-id="20a50-130">[Derived Column Transformation](data-flow/transformations/derived-column-transformation.md) </span></span>  
 <span data-ttu-id="20a50-131">[資料流程工作](control-flow/data-flow-task.md) </span><span class="sxs-lookup"><span data-stu-id="20a50-131">[Data Flow Task](control-flow/data-flow-task.md) </span></span>  
 [<span data-ttu-id="20a50-132">資料流程</span><span class="sxs-lookup"><span data-stu-id="20a50-132">Data Flow</span></span>](data-flow/data-flow.md)  
  
  
