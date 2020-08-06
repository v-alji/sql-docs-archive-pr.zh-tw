---
title: 新增運算式 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: a60ee091-b4ed-41e1-9b6a-032c316cd03f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 16f414bfad47ae92681de50eb576a6ac2cb3f5fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687457"
---
# <a name="add-an-expression-report-builder-and-ssrs"></a><span data-ttu-id="e809a-102">加入運算式 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="e809a-102">Add an Expression (Report Builder and SSRS)</span></span>
  <span data-ttu-id="e809a-103">運算式會在整個報表中用來定義報表項目屬性、篩選、群組、排序次序、連接字串和參數值。</span><span class="sxs-lookup"><span data-stu-id="e809a-103">Expressions are used throughout a report for defining report item properties, filters, groups, sort order, connection strings, and parameter values.</span></span> <span data-ttu-id="e809a-104">運算式是以等號 (=) 作為開頭，且是以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 撰寫。</span><span class="sxs-lookup"><span data-stu-id="e809a-104">Expressions begin with an equal sign (=) and are written in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].</span></span> <span data-ttu-id="e809a-105">運算式是由報表處理器在執行階段加以評估，這樣會將評估結果與報表配置元素結合。</span><span class="sxs-lookup"><span data-stu-id="e809a-105">They are evaluated at run time by the report processor, which combines the evaluation result with report layout elements.</span></span>  
  
 <span data-ttu-id="e809a-106">運算式可能很簡單或很複雜。</span><span class="sxs-lookup"><span data-stu-id="e809a-106">Expressions can be simple or complex.</span></span> <span data-ttu-id="e809a-107">簡單運算式會參考內建集合中的單一項目。</span><span class="sxs-lookup"><span data-stu-id="e809a-107">Simple expression refer to a single item in a built-in collection.</span></span> <span data-ttu-id="e809a-108">複雜運算式可包含常數、運算子、全域收集項和函數呼叫。</span><span class="sxs-lookup"><span data-stu-id="e809a-108">Complex expressions can contain constants, operators, global collection items, and function calls.</span></span> <span data-ttu-id="e809a-109">如需詳細資訊，請參閱[運算式 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="e809a-109">For more information, see [Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-an-expression-to-a-text-box"></a><span data-ttu-id="e809a-110">將運算式加入文字方塊</span><span class="sxs-lookup"><span data-stu-id="e809a-110">To add an expression to a text box</span></span>  
  
-   <span data-ttu-id="e809a-111">在 **[設計]** 檢視中，按一下設計介面上要在其中加入運算式的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="e809a-111">In **Design** view, click the text box on the design surface to which you want to add an expression.</span></span>  
  
    -   <span data-ttu-id="e809a-112">如果是簡單運算式，請將運算式的顯示文字輸入文字方塊內。</span><span class="sxs-lookup"><span data-stu-id="e809a-112">For a simple expression, type the display text for the expression in the text box.</span></span> <span data-ttu-id="e809a-113">例如，在資料集欄位 Sales 中輸入 `[Sales]`。</span><span class="sxs-lookup"><span data-stu-id="e809a-113">For example, for the dataset field Sales, type `[Sales]`.</span></span>  
  
    -   <span data-ttu-id="e809a-114">如果是複雜運算式，請以滑鼠右鍵按一下文字方塊，然後選取 **[運算式]** 。</span><span class="sxs-lookup"><span data-stu-id="e809a-114">For a complex expression, right-click the text box, and select **Expression**.</span></span> <span data-ttu-id="e809a-115">**[運算式]** 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="e809a-115">The **Expression** dialog box opens.</span></span> <span data-ttu-id="e809a-116">在運算式窗格內的 '=' 後面輸入您的運算式或是以互動方式建立運算式，然後按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="e809a-116">Type or interactively create your expression after the '=' in the expression pane, and then click OK.</span></span>  
  
         <span data-ttu-id="e809a-117">此運算式會以 `<<Expr>>`形式出現在設計介面上。</span><span class="sxs-lookup"><span data-stu-id="e809a-117">The expression appears on the design surface as `<<Expr>>`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e809a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e809a-118">See Also</span></span>  
 <span data-ttu-id="e809a-119">[格式化文字和預留位置 &#40;報表產生器及 SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e809a-119">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e809a-120">[文字方塊 &#40;報表產生器及 SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e809a-120">[Text Boxes &#40;Report Builder and SSRS&#41;](text-boxes-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e809a-121">[報表中的運算式用法 &#40;報表產生器及 SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e809a-121">[Expression Uses in Reports &#40;Report Builder and SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e809a-122">[篩選方程式範例 &#40;報表產生器及 SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e809a-122">[Filter Equation Examples &#40;Report Builder and SSRS&#41;](filter-equation-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e809a-123">[群組運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e809a-123">[Group Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="e809a-124">[運算式對話方塊 &#40;報表產生器&#41;](../expression-dialog-box-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="e809a-124">[Expression Dialog Box &#40;Report Builder&#41;](../expression-dialog-box-report-builder.md) </span></span>  
 <span data-ttu-id="e809a-125">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="e809a-125">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="e809a-126">將程式碼新增至報表 &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="e809a-126">Add Code to a Report &#40;SSRS&#41;</span></span>](add-code-to-a-report-ssrs.md)  
  
  
