---
title: '[資料列可見度] 對話方塊 (報表產生器) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10126"
ms.assetid: 117fb20c-2fda-437e-bcc5-9010d6d4b53b
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 748cf1612f04e02a90a5d8579b56d3856dea0388
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593281"
---
# <a name="row-visibility-dialog-box-report-builder"></a><span data-ttu-id="28959-102">資料列可見性對話方塊 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="28959-102">Row Visibility Dialog Box (Report Builder)</span></span>
  <span data-ttu-id="28959-103">使用 **[資料列可見性]** 對話方塊在報表第一次執行時顯示或隱藏選取的資料列，或使用其他報表項目來切換資料列的可見性。</span><span class="sxs-lookup"><span data-stu-id="28959-103">Use the **Row Visibility** dialog box to show or hide the selected row when the report is first run or to use another report item to toggle the visibility of the row.</span></span>  
  
## <a name="options"></a><span data-ttu-id="28959-104">選項</span><span class="sxs-lookup"><span data-stu-id="28959-104">Options</span></span>  
 <span data-ttu-id="28959-105">**一開始執行報表時**</span><span class="sxs-lookup"><span data-stu-id="28959-105">**When the report is initially run**</span></span>  
 <span data-ttu-id="28959-106">選擇一個選項以指出資料列最初顯示在報表中的方式。</span><span class="sxs-lookup"><span data-stu-id="28959-106">Select an option to indicate how the row is initially displayed in the report.</span></span>  
  
 <span data-ttu-id="28959-107">**顯示**</span><span class="sxs-lookup"><span data-stu-id="28959-107">**Show**</span></span>  
 <span data-ttu-id="28959-108">選取此選項，以顯示資料列。</span><span class="sxs-lookup"><span data-stu-id="28959-108">Select this option to show the row.</span></span>  
  
 <span data-ttu-id="28959-109">**隱藏**</span><span class="sxs-lookup"><span data-stu-id="28959-109">**Hide**</span></span>  
 <span data-ttu-id="28959-110">選取此選項，以隱藏資料列。</span><span class="sxs-lookup"><span data-stu-id="28959-110">Select this option to hide the row.</span></span>  
  
 <span data-ttu-id="28959-111">**依據運算式顯示或隱藏**</span><span class="sxs-lookup"><span data-stu-id="28959-111">**Show or hide based on an expression**</span></span>  
 <span data-ttu-id="28959-112">選取此選項即可使用運算式改變初始可見性。</span><span class="sxs-lookup"><span data-stu-id="28959-112">Select this option to vary the initial visibility using an expression.</span></span>  
  
 <span data-ttu-id="28959-113">輸入會評估為 `Boolean` 值的運算式，`True` 會隱藏項目，`False` 會顯示項目。</span><span class="sxs-lookup"><span data-stu-id="28959-113">Type an expression that evaluates to a `Boolean` value of `True` to hide the item and `False` to show the item.</span></span> <span data-ttu-id="28959-114">按一下**運算式** (*Fx*) ] 按鈕，即可編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="28959-114">Click the **Expression** (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="28959-115">**此報表項目可以切換顯示**</span><span class="sxs-lookup"><span data-stu-id="28959-115">**Display can be toggled by this report item**</span></span>  
 <span data-ttu-id="28959-116">選擇這個選項可顯示一個切換影像，讓使用者在 HTML 報表檢視器中顯示或隱藏這個資料列。</span><span class="sxs-lookup"><span data-stu-id="28959-116">Choose this option to display a toggle image that enables the user to show or hide this row in an HTML report viewer.</span></span>  
  
 <span data-ttu-id="28959-117">輸入或選取您想要顯示切換影像之報表中的文字方塊名稱，例如 Textbox1。</span><span class="sxs-lookup"><span data-stu-id="28959-117">Type or select the name of a text box in the report in which to display a toggle image; for example, Textbox1.</span></span> <span data-ttu-id="28959-118">您所選的文字方塊必須位於這個報表項目的目前範圍或涵蓋範圍中。</span><span class="sxs-lookup"><span data-stu-id="28959-118">The text box that you choose must be in the current or containing scope for this report item.</span></span> <span data-ttu-id="28959-119">例如，若要切換與子群組相關之資料列的可見性，請選取與父群組有關之資料列中的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="28959-119">For example, to toggle visibility of rows associated with a child group, select a text box in a row associated with the parent group.</span></span> <span data-ttu-id="28959-120">若要切換圖表的可見性，請選取與圖表位於相同涵蓋範圍的文字方塊，例如，報表主體或矩形。</span><span class="sxs-lookup"><span data-stu-id="28959-120">To toggle visibility of a chart, select a text box that is in the same containing scope as the chart; for example, the report body or a rectangle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28959-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="28959-121">See Also</span></span>  
 <span data-ttu-id="28959-122">[運算式範例 &#40;報表產生器及 SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="28959-122">[Expression Examples &#40;Report Builder and SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="28959-123">[將展開或折迭動作新增至 &#40;報表產生器和 SSRS 的專案&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="28959-123">[Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="28959-124">[&#40;報表產生器和 SSRS&#41;的影像](report-design/images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="28959-124">[Images &#40;Report Builder and SSRS&#41;](report-design/images-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="28959-125">[對話方塊、窗格和嚮導的報表產生器說明](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="28959-125">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 [<span data-ttu-id="28959-126">影像屬性對話方塊、一般 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="28959-126">Image Properties Dialog Box, General &#40;Report Builder and SSRS&#41;</span></span>](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md)  
  
  
