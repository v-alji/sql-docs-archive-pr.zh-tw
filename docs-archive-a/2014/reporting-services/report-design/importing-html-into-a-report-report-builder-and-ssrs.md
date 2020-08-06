---
title: 將 HTML 匯入至報表 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: dd0410ea-8839-4e8c-9944-8cdfe5465591
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 4f978e67c67556184012db6b809e4f5754f2374c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688577"
---
# <a name="importing-html-into-a-report-report-builder-and-ssrs"></a><span data-ttu-id="f48ba-102">將 HTML 匯入至報表 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="f48ba-102">Importing HTML into a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="f48ba-103">您可以使用文字方塊來將從資料集的欄位所擷取的 HTML 格式文字插入至報表。</span><span class="sxs-lookup"><span data-stu-id="f48ba-103">You can use a text box to insert HTML-formatted text that you have retrieved from a field in your dataset into a report.</span></span> <span data-ttu-id="f48ba-104">文字可以來自任何評估為正確格式之 HTML 的簡單或複雜運算式。</span><span class="sxs-lookup"><span data-stu-id="f48ba-104">The text can come from any simple or complex expression that evaluates to correctly formatted HTML.</span></span> <span data-ttu-id="f48ba-105">格式化的文字可以轉譯為所有受支援的輸出格式，包括 PDF 在內。</span><span class="sxs-lookup"><span data-stu-id="f48ba-105">Formatted text can be rendered to all supported output formats, including PDF.</span></span>  
  
 <span data-ttu-id="f48ba-106">![rs_HTMLFormatting](../media/rs-htmlformatting.gif "rs_HTMLFormatting")</span><span class="sxs-lookup"><span data-stu-id="f48ba-106">![rs_HTMLFormatting](../media/rs-htmlformatting.gif "rs_HTMLFormatting")</span></span>  
  
 <span data-ttu-id="f48ba-107">下圖顯示報表設計檢視中具有 HTML 格式的文字，以及相同文件在報表執行時所呈現的樣式。</span><span class="sxs-lookup"><span data-stu-id="f48ba-107">This illustration shows text with HTML formatting in report design view, and the same text as it is rendered when the report is run.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f48ba-108">當您匯入包含 HTML 標記的文字時，資料一定要先由文字方塊進行剖析。</span><span class="sxs-lookup"><span data-stu-id="f48ba-108">When you import text that contains HTML markup, the data must always be parsed by the text box first.</span></span> <span data-ttu-id="f48ba-109">因為只支援一部分的 HTML 標記，所以顯示在轉譯報表中的 HTML 可能會與原始的 HTML 不同。</span><span class="sxs-lookup"><span data-stu-id="f48ba-109">Because only a subset of HTML tags is supported, the HTML that is shown in the rendered report may differ from your original HTML.</span></span>  
  
 <span data-ttu-id="f48ba-110">若要快速開始使用，請參閱[教學課程：格式化文字 &#40;報表產生器&#41;](../tutorial-format-text-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="f48ba-110">To quickly get started, see [Tutorial: Format Text &#40;Report Builder&#41;](../tutorial-format-text-report-builder.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="supported-html-tags"></a><span data-ttu-id="f48ba-111">支援的 HTML 標籤</span><span class="sxs-lookup"><span data-stu-id="f48ba-111">Supported HTML Tags</span></span>  
 <span data-ttu-id="f48ba-112">下列是在定義為預留位置文字時，會轉譯為 HTML 的標記完整清單：</span><span class="sxs-lookup"><span data-stu-id="f48ba-112">The following is a complete list of tags that will render as HTML when defined as placeholder text:</span></span>  
  
-   <span data-ttu-id="f48ba-113">標頭、樣式和區塊元素： \<H{n}> 、 \<DIV> 、 \<SPAN> 、 \<P> 、\<LI></span><span class="sxs-lookup"><span data-stu-id="f48ba-113">Header, style and block elements: \<H{n}>, \<DIV>, \<SPAN>,\<P>, \<LI></span></span>  
  
 <span data-ttu-id="f48ba-114">所以其他的 HTML 標記都會在處理報表時遭到忽略。</span><span class="sxs-lookup"><span data-stu-id="f48ba-114">Any other HTML markup tags will be ignored during report processing.</span></span> <span data-ttu-id="f48ba-115">如果預留位置文字中的運算式所代表的 HTML 沒有採用正確格式，則預留位置會轉譯為純文字。</span><span class="sxs-lookup"><span data-stu-id="f48ba-115">If the HTML represented by the expression in the placeholder text is not well formed, the placeholder is rendered as plain text.</span></span> <span data-ttu-id="f48ba-116">所有 HTML 標記都不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="f48ba-116">All HTML tags are case-insensitive.</span></span>  
  
 <span data-ttu-id="f48ba-117">如果文字方塊中的文字只包含一個文字區塊，則預留位置中任何定義區塊元素的 HTML 都會正確轉譯。</span><span class="sxs-lookup"><span data-stu-id="f48ba-117">If the text in your text box contains only one block of text, any HTML in the placeholder that defines block elements will render correctly.</span></span> <span data-ttu-id="f48ba-118">不過，如果文字方塊具有多個文字區塊，則 HTML 標記會遭到忽略，而文字的結構會由文字區塊定義。</span><span class="sxs-lookup"><span data-stu-id="f48ba-118">However, if the text box has multiple blocks of text, the HTML tags are ignored and the structure of the text is defined by the blocks of text.</span></span>  
  
 <span data-ttu-id="f48ba-119">如果針對文字定義了一個以上的標記，而 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 在 HTML 和現有的報表條件約束之間偵測到衝突，則只會將最內層的 HTML 標記視為 HTML。</span><span class="sxs-lookup"><span data-stu-id="f48ba-119">If more than one tag is defined for text, and [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] detects a conflict between the HTML and existing report constraints, only the innermost HTML tag will be treated as HTML.</span></span>  
  
 <span data-ttu-id="f48ba-120">使用處理標記的清單時，所有項目符號及編號首碼的字型和樣式會固定使用新細明體黑色。</span><span class="sxs-lookup"><span data-stu-id="f48ba-120">When using the list handling tags, the font and style of all bullets and number prefixes will be fixed to Arial black.</span></span>  
  
 <span data-ttu-id="f48ba-121">如需詳細資訊，請參閱[將 HTML 新增至報表 &#40;報表產生器及 SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="f48ba-121">For more information, see [Add HTML into a Report &#40;Report Builder and SSRS&#41;](add-html-into-a-report-report-builder-and-ssrs.md).</span></span>  
  
## <a name="limitations-of-cascading-style-sheet-attributes"></a><span data-ttu-id="f48ba-122">階層式樣式表屬性的限制</span><span class="sxs-lookup"><span data-stu-id="f48ba-122">Limitations of Cascading Style Sheet Attributes</span></span>  
 <span data-ttu-id="f48ba-123">在使用階層式樣式表 (CSS) 屬性時，只會定義基本的標記集合。</span><span class="sxs-lookup"><span data-stu-id="f48ba-123">When using cascading style sheet (CSS) attributes, only a basic set of tags are defined.</span></span> <span data-ttu-id="f48ba-124">下列是受支援的屬性清單：</span><span class="sxs-lookup"><span data-stu-id="f48ba-124">The following is a list of attributes that are supported:</span></span>  
  
-   <span data-ttu-id="f48ba-125">text-align, text-indent</span><span class="sxs-lookup"><span data-stu-id="f48ba-125">text-align, text-indent</span></span>  
  
-   <span data-ttu-id="f48ba-126">font-family</span><span class="sxs-lookup"><span data-stu-id="f48ba-126">font-family</span></span>  
  
-   <span data-ttu-id="f48ba-127">字型大小</span><span class="sxs-lookup"><span data-stu-id="f48ba-127">font-size</span></span>  
  
    -   <span data-ttu-id="f48ba-128">只有以絕對 CSS 長度單位計算的有效 RDL 大小值才受到支援。</span><span class="sxs-lookup"><span data-stu-id="f48ba-128">Only valid RDL size values, in absolute CSS length units are supported.</span></span> <span data-ttu-id="f48ba-129">支援的單位包括：in、cm、mm、pt、pc。</span><span class="sxs-lookup"><span data-stu-id="f48ba-129">Supported units are: in, cm, mm, pt, pc.</span></span>  
  
    -   <span data-ttu-id="f48ba-130">相對 CSS 長度單位會被忽略，而且不受支援。</span><span class="sxs-lookup"><span data-stu-id="f48ba-130">Relative CSS length units are ignored and not supported.</span></span> <span data-ttu-id="f48ba-131">不支援的單位包括 em、ex、px、%、rem。</span><span class="sxs-lookup"><span data-stu-id="f48ba-131">Unsupported units include em, ex, px,%,rem.</span></span>  
  
-   <span data-ttu-id="f48ba-132">color</span><span class="sxs-lookup"><span data-stu-id="f48ba-132">color</span></span>  
  
-   <span data-ttu-id="f48ba-133">padding, padding-bottom, padding-top, padding-right, padding-left</span><span class="sxs-lookup"><span data-stu-id="f48ba-133">padding, padding-bottom, padding-top, padding-right, padding-left</span></span>  
  
-   <span data-ttu-id="f48ba-134">font-weight</span><span class="sxs-lookup"><span data-stu-id="f48ba-134">font-weight</span></span>  
  
 <span data-ttu-id="f48ba-135">以下是使用 CSS 的一些考量：</span><span class="sxs-lookup"><span data-stu-id="f48ba-135">Here are some considerations for using CSS:</span></span>  
  
-   <span data-ttu-id="f48ba-136">格式不正確的 CSS 值會像格式不正確的 HTML 一樣遭到忽略。</span><span class="sxs-lookup"><span data-stu-id="f48ba-136">Malformed CSS values are ignored in the same way as malformed HTML.</span></span>  
  
-   <span data-ttu-id="f48ba-137">同一標記中同時存在屬性和 CSS 樣式屬性時，CSS 屬性擁有較高的優先權。</span><span class="sxs-lookup"><span data-stu-id="f48ba-137">When both attribute and CSS style attributes exist in the same tag, the CSS property has a higher precedence.</span></span> <span data-ttu-id="f48ba-138">例如，如果您的文字是 **\<p style="text-align: right" align="left">** ，則只會套用文字對齊屬性，而文字會靠右對齊。</span><span class="sxs-lookup"><span data-stu-id="f48ba-138">For example, if your text is **\<p style="text-align: right" align="left">**, only the text-align attribute will be applied and the text will be right-aligned.</span></span>  
  
-   <span data-ttu-id="f48ba-139">對於屬性和 CSS 樣式來說，如果某屬性指定了一次以上，則只會套用該屬性的最後一個執行個體。</span><span class="sxs-lookup"><span data-stu-id="f48ba-139">For attributes and CSS styles, if a property is specified more than once, only the last instance of the property is applied.</span></span> <span data-ttu-id="f48ba-140">例如，如果您的文字為 **\<p align="left" align="right">** ，則文字會靠右對齊。</span><span class="sxs-lookup"><span data-stu-id="f48ba-140">For example, if your text is **\<p align="left" align="right">**, the text will be right-aligned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f48ba-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f48ba-141">See Also</span></span>  
 [<span data-ttu-id="f48ba-142">轉譯為 HTML &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="f48ba-142">Rendering to HTML &#40;Report Builder and SSRS&#41;</span></span>](../report-builder/rendering-to-html-report-builder-and-ssrs.md)  
  
  
