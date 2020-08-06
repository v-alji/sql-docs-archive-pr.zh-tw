---
title: 加入或變更屬性運算式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- expressions [Integration Services], creating
- expressions [Integration Services], property expressions
ms.assetid: cb5da499-065f-4fa6-9f6d-5bc5f385241e
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d6d12fbe46930818af2b47b59620963d39616e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597979"
---
# <a name="add-or-change-a-property-expression"></a><span data-ttu-id="5ac06-102">加入或變更屬性運算式</span><span class="sxs-lookup"><span data-stu-id="5ac06-102">Add or Change a Property Expression</span></span>
  <span data-ttu-id="5ac06-103">您可以為封裝、工作、「Foreach 迴圈」容器、「For 迴圈」容器、「時序」容器、事件處理常式、封裝和專案層級的連接管理員和記錄提供者建立屬性運算式。</span><span class="sxs-lookup"><span data-stu-id="5ac06-103">You can create property expressions for packages, tasks, Foreach Loop containers, For Loop containers, Sequence containers, event handlers, package and project level connection managers, and log providers.</span></span>  
  
 <span data-ttu-id="5ac06-104">若要建立或變更屬性運算式，您可以使用 [屬性運算式編輯器]  或 [運算式產生器]  。</span><span class="sxs-lookup"><span data-stu-id="5ac06-104">To create or change property expressions, you can use either the **Property Expressions Editor** or **Expression Builder**.</span></span> <span data-ttu-id="5ac06-105">您可以從適用於工作的自訂編輯器或 [屬性] 視窗存取 [屬性運算式編輯器]。</span><span class="sxs-lookup"><span data-stu-id="5ac06-105">The **Property Expressions Editor** can be accessed from either the custom editors that are available for tasks and containers, or from the **Properties** window.</span></span> <span data-ttu-id="5ac06-106">您可以從 [屬性運算式編輯器] 內部存取 [運算式產生器]。</span><span class="sxs-lookup"><span data-stu-id="5ac06-106">**Expression Builder** can be accessed from inside the **Property Expressions Editor**.</span></span> <span data-ttu-id="5ac06-107">雖然您可以在 [屬性運算式編輯器]  或 [運算式產生器]  中撰寫運算式，但是 [運算式產生器]  會提供一組圖形工具，讓您輕鬆地建立複雜運算式。</span><span class="sxs-lookup"><span data-stu-id="5ac06-107">While you can write expressions in either the **Property Expressions Editor** or **Expression Builder**, **Expression Builder** provides a graphical set of tools that makes it simple to build complex expressions.</span></span>  
  
 <span data-ttu-id="5ac06-108">如需深入了解 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 提供的語法、運算子和函數，請參閱[運算子 &#40;SSIS 運算式&#41;](operators-ssis-expression.md) 和[函數 &#40;SSIS 運算式&#41;](functions-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="5ac06-108">To learn more about the syntax, operators, and functions that [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] provides, see [Operators &#40;SSIS Expression&#41;](operators-ssis-expression.md) and [Functions &#40;SSIS Expression&#41;](functions-ssis-expression.md).</span></span> <span data-ttu-id="5ac06-109">每個運算子或函數的主題都包含了在運算式中使用該運算子或函數的範例。</span><span class="sxs-lookup"><span data-stu-id="5ac06-109">The topic for each operator or function includes examples of using that operator or function in an expression.</span></span> <span data-ttu-id="5ac06-110">如需更複雜之運算式的相關範例，請參閱 [在封裝中使用屬性運算式](use-property-expressions-in-packages.md)。</span><span class="sxs-lookup"><span data-stu-id="5ac06-110">For examples of more complex expressions, see [Use Property Expressions in Packages](use-property-expressions-in-packages.md).</span></span>  
  
### <a name="to-create-or-change-a-property-expression"></a><span data-ttu-id="5ac06-111">建立或變更屬性運算式</span><span class="sxs-lookup"><span data-stu-id="5ac06-111">To create or change a property expression</span></span>  
  
1.  <span data-ttu-id="5ac06-112">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="5ac06-112">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open the project that contains the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package you want.</span></span>  
  
2.  <span data-ttu-id="5ac06-113">在 [方案總管] 中，按兩下封裝將其開啟，然後執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="5ac06-113">In Solution Explorer, double-click the package to open it, and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="5ac06-114">如果項目是工作或容器，請按兩下該項目，然後按一下編輯器中的 [運算式]  。</span><span class="sxs-lookup"><span data-stu-id="5ac06-114">If the item is a task or a container, double-click the item, and then click **Expressions** in the editor.</span></span>  
  
    -   <span data-ttu-id="5ac06-115">以滑鼠右鍵按一下項目，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="5ac06-115">Right-click the item and then click **Properties**.</span></span>  
  
3.  <span data-ttu-id="5ac06-116">在 [運算式]  方塊中按一下，然後按一下省略符號 (...)。</span><span class="sxs-lookup"><span data-stu-id="5ac06-116">Click in the **Expressions** box and then click the ellipsis (...).</span></span>  
  
4.  <span data-ttu-id="5ac06-117">在 [屬性運算式編輯器]  中，選取 [屬性]  清單中的屬性，然後執行下列其中之一：</span><span class="sxs-lookup"><span data-stu-id="5ac06-117">In the **Property Expressions Editor**, select a property in the **Property** list, and then do one of the following:</span></span>  
  
    -   <span data-ttu-id="5ac06-118">直接在 [運算式]  資料行中輸入或變更屬性運算式，然後按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="5ac06-118">Type or change the property expression directly in the **Expression** column, and then click **OK**.</span></span>  
  
         <span data-ttu-id="5ac06-119">-或-</span><span class="sxs-lookup"><span data-stu-id="5ac06-119">-or-</span></span>  
  
    -   <span data-ttu-id="5ac06-120">在屬性的運算式資料列中，按一下省略符號 (...) 開啟 [運算式產生器]  。</span><span class="sxs-lookup"><span data-stu-id="5ac06-120">Click the ellipsis (...) in the expression row of the property to open the **Expression Builder**.</span></span>  
  
5.  <span data-ttu-id="5ac06-121">(選擇性) 在 [運算式產生器]  中，進行下列任何一項工作：</span><span class="sxs-lookup"><span data-stu-id="5ac06-121">(Optional) In the **Expression Builder**, do any of the following tasks:</span></span>  
  
    -   <span data-ttu-id="5ac06-122">若要存取系統和使用者定義的變數，請展開 [變數]  。</span><span class="sxs-lookup"><span data-stu-id="5ac06-122">To access system and user-defined variables, expand **Variables**.</span></span>  
  
    -   <span data-ttu-id="5ac06-123">若要存取 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 運算式語言所提供的函數、轉換和運算子，請展開 [數學函數]  、[字串函數]  、[日期/時間函數]  、[NULL 函數]  、[類型轉換]  和 [運算子]  。</span><span class="sxs-lookup"><span data-stu-id="5ac06-123">To access the functions, the casts, and the operators that the [!INCLUDE[ssIS](../../includes/ssis-md.md)] expression language provides, expand **Mathematical Functions**, **String Functions**, **Date/Time Functions**, **NULL Functions**, **Type Casts**, and **Operators**.</span></span>  
  
    -   <span data-ttu-id="5ac06-124">若要在 [運算式產生器]  中建立或變更運算式，請將變數、資料行、函數、運算子和轉換拖曳至 [運算式]  方塊，或者直接在方塊中輸入運算式。</span><span class="sxs-lookup"><span data-stu-id="5ac06-124">To build or change an expression in the **Expression Builder**, drag variables, columns, functions, operators, and casts to the **Expression** box, or type the expression in the box.</span></span>  
  
    -   <span data-ttu-id="5ac06-125">若要檢視運算式的評估結果，請在 [運算式產生器]  中按一下 [評估運算式]  。</span><span class="sxs-lookup"><span data-stu-id="5ac06-125">To view the evaluation result of the expression, click **Evaluate Expression** in the **Expression Builder**.</span></span>  
  
         <span data-ttu-id="5ac06-126">如果運算式無效，則會出現警示，描述運算式中的語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="5ac06-126">If the expression is not valid, an alert appears that describes the syntax errors in the expression.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="5ac06-127">評估運算式不會將評估結果指派給屬性。</span><span class="sxs-lookup"><span data-stu-id="5ac06-127">Evaluating an expression does not assign the evaluation result to the property.</span></span>  
  
6.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5ac06-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5ac06-128">See Also</span></span>  
 <span data-ttu-id="5ac06-129">[Integration Services &#40;SSIS&#41; 運算式](integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="5ac06-129">[Integration Services &#40;SSIS&#41; Expressions](integration-services-ssis-expressions.md) </span></span>  
 <span data-ttu-id="5ac06-130">[在封裝中使用屬性運算式](use-property-expressions-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="5ac06-130">[Use Property Expressions in Packages](use-property-expressions-in-packages.md) </span></span>  
 <span data-ttu-id="5ac06-131">[Integration Services &#40;SSIS&#41; 封裝](../integration-services-ssis-packages.md) </span><span class="sxs-lookup"><span data-stu-id="5ac06-131">[Integration Services &#40;SSIS&#41; Packages](../integration-services-ssis-packages.md) </span></span>  
 <span data-ttu-id="5ac06-132">[Integration Services 容器](../control-flow/integration-services-containers.md) </span><span class="sxs-lookup"><span data-stu-id="5ac06-132">[Integration Services Containers](../control-flow/integration-services-containers.md) </span></span>  
 <span data-ttu-id="5ac06-133">[Integration Services 工作](../control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="5ac06-133">[Integration Services Tasks](../control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="5ac06-134">[Integration Services &#40;SSIS&#41; 事件處理常式](../integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="5ac06-134">[Integration Services &#40;SSIS&#41; Event Handlers](../integration-services-ssis-event-handlers.md) </span></span>  
 <span data-ttu-id="5ac06-135">[Integration Services &#40;SSIS&#41; 連線](../connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="5ac06-135">[Integration Services &#40;SSIS&#41; Connections](../connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="5ac06-136">Integration Services &#40;SSIS&#41; 記錄</span><span class="sxs-lookup"><span data-stu-id="5ac06-136">Integration Services &#40;SSIS&#41; Logging</span></span>](../performance/integration-services-ssis-logging.md)  
  
  
