---
title: 運算式中的常數 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: b8ae650b-0f46-4848-b62b-15f8a40751b8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d95005a04482cb03d3bb3860aea695c7e7969255
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594447"
---
# <a name="constants-in-expressions-report-builder-and-ssrs"></a><span data-ttu-id="6cf81-102">運算式中的常數 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6cf81-102">Constants in Expressions (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6cf81-103">常數是由常值文字或預先定義的文字所組成。</span><span class="sxs-lookup"><span data-stu-id="6cf81-103">A constant consists of literal text or predefined text.</span></span> <span data-ttu-id="6cf81-104">報表處理器可以存取預先定義的常數，讓您在運算式中納入這些常數時，在系統評估運算式之前，就會將常數以其代表的值來取代。</span><span class="sxs-lookup"><span data-stu-id="6cf81-104">The report processor has access to predefined constants so that when you include them in an expression, the values they represent are substituted in the expression before it is evaluated.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="literal-text"></a><span data-ttu-id="6cf81-105">常值文字</span><span class="sxs-lookup"><span data-stu-id="6cf81-105">Literal Text</span></span>  
 <span data-ttu-id="6cf81-106">在運算式中，常值文字是置於雙引號之間的文字。</span><span class="sxs-lookup"><span data-stu-id="6cf81-106">In an expression, literal text is text that is in double quotation marks.</span></span> <span data-ttu-id="6cf81-107">如果文字是運算式的一部分，則您也可以直接在文字方塊中輸入文字，而不加上雙引號。</span><span class="sxs-lookup"><span data-stu-id="6cf81-107">You can also type text directly into a text box without double quotation marks if it is not part of an expression.</span></span> <span data-ttu-id="6cf81-108">如果文字方塊的值不是以等號 (=) 開頭，就會將該文字當做常值文字。</span><span class="sxs-lookup"><span data-stu-id="6cf81-108">If the text box value does not begin with an equal sign (=), the text is treated as literal text.</span></span> <span data-ttu-id="6cf81-109">下表顯示若干運算式中的常值文字範例。</span><span class="sxs-lookup"><span data-stu-id="6cf81-109">The following table shows several examples of literal text in an expression.</span></span>  
  
|<span data-ttu-id="6cf81-110">持續性</span><span class="sxs-lookup"><span data-stu-id="6cf81-110">Constant</span></span>|<span data-ttu-id="6cf81-111">顯示文字</span><span class="sxs-lookup"><span data-stu-id="6cf81-111">Display text</span></span>|<span data-ttu-id="6cf81-112">運算式文字</span><span class="sxs-lookup"><span data-stu-id="6cf81-112">Expression text</span></span>|  
|--------------|------------------|---------------------|  
|<span data-ttu-id="6cf81-113">報表執行於：</span><span class="sxs-lookup"><span data-stu-id="6cf81-113">Report run at:</span></span>|<\<Expr>>|`="Report run at: " & Globals!ExecutionTime`|  
|<span data-ttu-id="6cf81-114">Adventure Works Cycles</span><span class="sxs-lookup"><span data-stu-id="6cf81-114">Adventure Works Cycles</span></span>|<span data-ttu-id="6cf81-115">Adventure Works Cycles</span><span class="sxs-lookup"><span data-stu-id="6cf81-115">Adventure Works Cycles</span></span>|<span data-ttu-id="6cf81-116">Adventure Works Cycles</span><span class="sxs-lookup"><span data-stu-id="6cf81-116">Adventure Works Cycles</span></span>|  
|<span data-ttu-id="6cf81-117">[加上括號的顯示文字]</span><span class="sxs-lookup"><span data-stu-id="6cf81-117">[Bracketed display text]</span></span>|<span data-ttu-id="6cf81-118">\\[加上括號的顯示文字\\]</span><span class="sxs-lookup"><span data-stu-id="6cf81-118">\\[Bracketed display text\\]</span></span>|<span data-ttu-id="6cf81-119">[加上括號的顯示文字]</span><span class="sxs-lookup"><span data-stu-id="6cf81-119">[Bracketed display text]</span></span>|  
  
## <a name="rdl-constants"></a><span data-ttu-id="6cf81-120">RDL 常數</span><span class="sxs-lookup"><span data-stu-id="6cf81-120">RDL Constants</span></span>  
 <span data-ttu-id="6cf81-121">您可以在運算式中使用以報表定義語言 (RDL) 所定義的常數。</span><span class="sxs-lookup"><span data-stu-id="6cf81-121">You can use constants defined in Report Definition Language (RDL) in an expression.</span></span> <span data-ttu-id="6cf81-122">當您為報表屬性建立只接受特定有效的運算式時，常數就會顯示在 **[運算式]** 對話方塊中 (也稱為列舉型別)。</span><span class="sxs-lookup"><span data-stu-id="6cf81-122">In the **Expression** dialog box, constants appear when you create an expression for a report property that only accepts certain valid values, also known as enumerated types.</span></span> <span data-ttu-id="6cf81-123">下表顯示兩個範例。</span><span class="sxs-lookup"><span data-stu-id="6cf81-123">The following table shows two examples.</span></span>  
  
|<span data-ttu-id="6cf81-124">屬性</span><span class="sxs-lookup"><span data-stu-id="6cf81-124">Property</span></span>|<span data-ttu-id="6cf81-125">說明</span><span class="sxs-lookup"><span data-stu-id="6cf81-125">Description</span></span>|<span data-ttu-id="6cf81-126">值</span><span class="sxs-lookup"><span data-stu-id="6cf81-126">Values</span></span>|  
|--------------|-----------------|------------|  
|<span data-ttu-id="6cf81-127">TextAlign</span><span class="sxs-lookup"><span data-stu-id="6cf81-127">TextAlign</span></span>|<span data-ttu-id="6cf81-128">用來對齊文字方塊中文字的有效。</span><span class="sxs-lookup"><span data-stu-id="6cf81-128">Valid values for aligning text in a text box.</span></span>|<span data-ttu-id="6cf81-129">一般、靠左、置中、靠右</span><span class="sxs-lookup"><span data-stu-id="6cf81-129">General, Left, Center, Right</span></span>|  
|<span data-ttu-id="6cf81-130">BorderStyle</span><span class="sxs-lookup"><span data-stu-id="6cf81-130">BorderStyle</span></span>|<span data-ttu-id="6cf81-131">加入至報表的線條有效。</span><span class="sxs-lookup"><span data-stu-id="6cf81-131">Valid values for a line added to a report.</span></span>|<span data-ttu-id="6cf81-132">預設值、無、點線、虛線、實線、雙線、虛線點、虛線點點</span><span class="sxs-lookup"><span data-stu-id="6cf81-132">Default, None, Dotted, Dashed, Solid, Double, DashDot, DashDotdot</span></span>|  
  
## <a name="visual-basic-constants"></a><span data-ttu-id="6cf81-133">Visual Basic 常數</span><span class="sxs-lookup"><span data-stu-id="6cf81-133">Visual Basic Constants</span></span>  
 <span data-ttu-id="6cf81-134">您可以在運算式中使用以 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] 執行階段程式庫所定義的常數。</span><span class="sxs-lookup"><span data-stu-id="6cf81-134">You can use constants defined in the [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] run-time library in an expression.</span></span> <span data-ttu-id="6cf81-135">例如，您可以使用常數 `DateInterval.Day`。</span><span class="sxs-lookup"><span data-stu-id="6cf81-135">For example, you can use the constant `DateInterval.Day`.</span></span> <span data-ttu-id="6cf81-136">如果日期為 2008 年 1 月 10 日，則下列運算式會傳回數字 10：</span><span class="sxs-lookup"><span data-stu-id="6cf81-136">The following expression for the date January 10, 2008 returns the number 10:</span></span>  
  
 `=DatePart("d",Globals!ExecutionTime)`  
  
## <a name="clr-constants"></a><span data-ttu-id="6cf81-137">CLR 常數</span><span class="sxs-lookup"><span data-stu-id="6cf81-137">CLR Constants</span></span>  
 <span data-ttu-id="6cf81-138">您可以在運算式中使用以 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] Common Language Runtime (CLR) 類別所定義的常數。</span><span class="sxs-lookup"><span data-stu-id="6cf81-138">You can use constants defined in [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] common language run-time (CLR) classes in an expression.</span></span> <span data-ttu-id="6cf81-139">下表顯示系統定義色彩的範例。</span><span class="sxs-lookup"><span data-stu-id="6cf81-139">The following table shows an example of a system-defined color.</span></span>  
  
|<span data-ttu-id="6cf81-140">持續性</span><span class="sxs-lookup"><span data-stu-id="6cf81-140">Constant</span></span>|<span data-ttu-id="6cf81-141">描述</span><span class="sxs-lookup"><span data-stu-id="6cf81-141">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="6cf81-142">MistyRose</span><span class="sxs-lookup"><span data-stu-id="6cf81-142">MistyRose</span></span>|<span data-ttu-id="6cf81-143">當您為以背景色彩為基礎的報表屬性建立運算式時，可以依名稱指定色彩。</span><span class="sxs-lookup"><span data-stu-id="6cf81-143">When you create an expression for a report property that is based on background color, you can specify a color by name.</span></span> <span data-ttu-id="6cf81-144">有效的名稱會列在 **[運算式]** 對話方塊中。</span><span class="sxs-lookup"><span data-stu-id="6cf81-144">Valid names are listed in the **Expression** dialog box.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6cf81-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6cf81-145">See Also</span></span>  
 <span data-ttu-id="6cf81-146">[運算式對話方塊](../expression-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="6cf81-146">[Expression Dialog Box](../expression-dialog-box.md) </span></span>  
 <span data-ttu-id="6cf81-147">[運算式 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6cf81-147">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6cf81-148">[運算式範例 &#40;報表產生器及 SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6cf81-148">[Expression Examples &#40;Report Builder and SSRS&#41;](expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6cf81-149">[運算式中的資料類型 &#40;報表產生器和 SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6cf81-149">[Data Types in Expressions &#40;Report Builder and SSRS&#41;](data-types-in-expressions-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6cf81-150">運算式對話方塊 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="6cf81-150">Expression Dialog Box &#40;Report Builder&#41;</span></span>](../expression-dialog-box-report-builder.md)  
  
  
