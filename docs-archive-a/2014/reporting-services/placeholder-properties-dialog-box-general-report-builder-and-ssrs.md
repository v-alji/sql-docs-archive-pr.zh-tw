---
title: 預留位置屬性對話方塊、一般 (報表產生器和 SSRS) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10131"
- sql12.rtp.rptdesigner.placeholderproperties.general.f1
ms.assetid: 7a867736-a3b0-4b5a-b3e5-fe7c8d7618a8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: e561f08206deae383ceb4c1b74d373aa3bcee6fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707242"
---
# <a name="placeholder-properties-dialog-box-general-report-builder-and-ssrs"></a><span data-ttu-id="6aef5-102">預留位置屬性對話方塊、一般 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="6aef5-102">Placeholder Properties Dialog Box, General (Report Builder and SSRS)</span></span>
  <span data-ttu-id="6aef5-103">使用 **[預留位置屬性]** 對話方塊可變更文字方塊內某個預留位置的值、工具提示和標記選項。</span><span class="sxs-lookup"><span data-stu-id="6aef5-103">Use the **Placeholder Properties** dialog box to change the value, ToolTip, and markup options of a placeholder in a text box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="6aef5-104">選項</span><span class="sxs-lookup"><span data-stu-id="6aef5-104">Options</span></span>  
 <span data-ttu-id="6aef5-105">**標籤**</span><span class="sxs-lookup"><span data-stu-id="6aef5-105">**Label**</span></span>  
 <span data-ttu-id="6aef5-106">輸入預留位置的標籤。</span><span class="sxs-lookup"><span data-stu-id="6aef5-106">Type a label for the placeholder.</span></span> <span data-ttu-id="6aef5-107">此標籤只會在設計介面上顯示。</span><span class="sxs-lookup"><span data-stu-id="6aef5-107">The label is displayed on the design surface only.</span></span>  
  
 <span data-ttu-id="6aef5-108">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="6aef5-108">**Value**</span></span>  
 <span data-ttu-id="6aef5-109">輸入文字方塊的值。</span><span class="sxs-lookup"><span data-stu-id="6aef5-109">Type the value of the text box.</span></span> <span data-ttu-id="6aef5-110">這應該是欄位運算式、其他運算式或標籤。</span><span class="sxs-lookup"><span data-stu-id="6aef5-110">This should be a field expression, other expression, or a label.</span></span> <span data-ttu-id="6aef5-111">按一下**運算式** (*Fx*) ] 按鈕，即可編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="6aef5-111">Click the **Expression** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="6aef5-112">**工具提示**</span><span class="sxs-lookup"><span data-stu-id="6aef5-112">**Tooltip**</span></span>  
 <span data-ttu-id="6aef5-113">輸入文字或評估為工具提示的運算式。</span><span class="sxs-lookup"><span data-stu-id="6aef5-113">Type text or an expression that evaluates to a ToolTip.</span></span> <span data-ttu-id="6aef5-114">按一下**運算式** (*Fx*) ] 按鈕，即可編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="6aef5-114">Click the **Expression** (*fx*) button to edit the expression.</span></span> <span data-ttu-id="6aef5-115">當使用者在轉譯報表中將指標暫停在項目上時，便會顯示工具提示。</span><span class="sxs-lookup"><span data-stu-id="6aef5-115">The ToolTip appears when the user pauses the pointer over the item in the rendered report.</span></span>  
  
 <span data-ttu-id="6aef5-116">**標記類型**</span><span class="sxs-lookup"><span data-stu-id="6aef5-116">**Markup type**</span></span>  
 <span data-ttu-id="6aef5-117">選取選項，指出如何轉譯預留位置。</span><span class="sxs-lookup"><span data-stu-id="6aef5-117">Select an option to indicate how the placeholder is rendered.</span></span>  
  
-   <span data-ttu-id="6aef5-118">**純文字** ：將預留位置顯示為簡單的文字。</span><span class="sxs-lookup"><span data-stu-id="6aef5-118">**Plain Text** Display the placeholder as simple text.</span></span> <span data-ttu-id="6aef5-119">HTML 會視為常值文字。</span><span class="sxs-lookup"><span data-stu-id="6aef5-119">HTML is treated as literal text.</span></span>  
  
-   <span data-ttu-id="6aef5-120">**HTML**  ：將預留位置顯示為 HTML。</span><span class="sxs-lookup"><span data-stu-id="6aef5-120">**HTML**  Display the placeholder as HTML.</span></span> <span data-ttu-id="6aef5-121">如果預留位置的運算式值包含有效的 HTML 標記，則這些標記會轉譯為 HTML。</span><span class="sxs-lookup"><span data-stu-id="6aef5-121">If the expression value of the placeholder contains valid HTML tags, these tags are rendered as HTML.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6aef5-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6aef5-122">See Also</span></span>  
 <span data-ttu-id="6aef5-123">[將文字方塊中的文字格式化 &#40;報表產生器及 SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6aef5-123">[Format Text in a Text Box &#40;Report Builder and SSRS&#41;](report-design/format-text-in-a-text-box-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6aef5-124">[將 HTML 新增至報表 &#40;報表產生器和 SSRS&#41;](report-design/add-html-into-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6aef5-124">[Add HTML into a Report &#40;Report Builder and SSRS&#41;](report-design/add-html-into-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6aef5-125">[運算式範例 &#40;報表產生器及 SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6aef5-125">[Expression Examples &#40;Report Builder and SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6aef5-126">[文字方塊 &#40;報表產生器和 SSRS&#41;](report-design/text-boxes-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6aef5-126">[Text Boxes &#40;Report Builder and SSRS&#41;](report-design/text-boxes-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6aef5-127">[將報表專案的格式設定 &#40;報表產生器和 SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6aef5-127">[Formatting Report Items &#40;Report Builder and SSRS&#41;](report-design/formatting-report-items-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="6aef5-128">[&#40;報表產生器和 SSRS 設定文字和預留位置的格式&#41;](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="6aef5-128">[Formatting Text and Placeholders &#40;Report Builder and SSRS&#41;](report-design/formatting-text-and-placeholders-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="6aef5-129">將 HTML 匯入至報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="6aef5-129">Importing HTML into a Report &#40;Report Builder and SSRS&#41;</span></span>](report-design/importing-html-into-a-report-report-builder-and-ssrs.md)  
  
  
