---
title: 資料行可見度對話方塊 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.columnvisibility.f1
- "10127"
ms.assetid: ca59d1cd-d782-4298-aa61-4f312c32eb50
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1c2e5f4124f987b87f02968282367817d61c3211
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596554"
---
# <a name="column-visibility-dialog-box"></a><span data-ttu-id="27e74-102">資料行可見性對話方塊</span><span class="sxs-lookup"><span data-stu-id="27e74-102">Column Visibility Dialog Box</span></span>
  <span data-ttu-id="27e74-103">使用 **[資料行可見性]** 對話方塊在報表第一次執行時顯示或隱藏選取的資料行，或使用其他報表項目來切換資料行的可見性。</span><span class="sxs-lookup"><span data-stu-id="27e74-103">Use the **Column Visibility** dialog box to show or hide the selected column when the report is first run or to use another report item to toggle the visibility of the column.</span></span>  
  
## <a name="options"></a><span data-ttu-id="27e74-104">選項</span><span class="sxs-lookup"><span data-stu-id="27e74-104">Options</span></span>  
 <span data-ttu-id="27e74-105">**一開始執行報表時**</span><span class="sxs-lookup"><span data-stu-id="27e74-105">**When the report is initially run**</span></span>  
 <span data-ttu-id="27e74-106">選擇一個選項以指出報表項目最初顯示在報表中的方式。</span><span class="sxs-lookup"><span data-stu-id="27e74-106">Select an option to indicate how the report item is initially displayed in the report.</span></span>  
  
 <span data-ttu-id="27e74-107">**顯示**</span><span class="sxs-lookup"><span data-stu-id="27e74-107">**Show**</span></span>  
 <span data-ttu-id="27e74-108">選擇此選項，以顯示報表項目。</span><span class="sxs-lookup"><span data-stu-id="27e74-108">Choose this option to show the report item.</span></span>  
  
 <span data-ttu-id="27e74-109">**隱藏**</span><span class="sxs-lookup"><span data-stu-id="27e74-109">**Hide**</span></span>  
 <span data-ttu-id="27e74-110">選擇此選項，以隱藏報表項目。</span><span class="sxs-lookup"><span data-stu-id="27e74-110">Choose this option to hide the report item.</span></span>  
  
 <span data-ttu-id="27e74-111">**依據運算式顯示或隱藏**</span><span class="sxs-lookup"><span data-stu-id="27e74-111">**Show or hide based on an expression**</span></span>  
 <span data-ttu-id="27e74-112">選擇此選項即可使用運算式改變初始可見性。</span><span class="sxs-lookup"><span data-stu-id="27e74-112">Choose this option to vary the initial visibility using an expression.</span></span>  
  
 <span data-ttu-id="27e74-113">輸入會評估為 `Boolean` 值的運算式，`True` 會隱藏項目，`False` 會顯示項目。</span><span class="sxs-lookup"><span data-stu-id="27e74-113">Type an expression that evaluates to a `Boolean` value of `True` to hide the item and `False` to show the item.</span></span> <span data-ttu-id="27e74-114">按一下運算式 (*fx*) ] 按鈕，即可編輯運算式。</span><span class="sxs-lookup"><span data-stu-id="27e74-114">Click the Expression (*fx*) button to edit the expression.</span></span>  
  
 <span data-ttu-id="27e74-115">**此報表項目可以切換顯示**</span><span class="sxs-lookup"><span data-stu-id="27e74-115">**Display can be toggled by this report item**</span></span>  
 <span data-ttu-id="27e74-116">選擇這個選項可顯示一個切換影像，好讓使用者在 HTML 報表檢視器中顯示或隱藏這個報表項目。</span><span class="sxs-lookup"><span data-stu-id="27e74-116">Choose this option to display a toggle image that enables the user to show or hide this report item in an HTML report viewer.</span></span>  
  
 <span data-ttu-id="27e74-117">輸入或選取您想要顯示切換影像之報表中的文字方塊名稱，例如 Textbox1。</span><span class="sxs-lookup"><span data-stu-id="27e74-117">Type or select the name of a text box in the report in which to display a toggle image; for example, Textbox1.</span></span> <span data-ttu-id="27e74-118">您所選的文字方塊必須位於這個報表項目的目前範圍或涵蓋範圍中。</span><span class="sxs-lookup"><span data-stu-id="27e74-118">The text box that you choose must be in the current or containing scope for this report item.</span></span> <span data-ttu-id="27e74-119">例如，若要切換與子群組相關之資料列的可見性，請選取與父群組有關之資料列中的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="27e74-119">For example, to toggle visibility of rows associated with a child group, select a text box in a row associated with the parent group.</span></span> <span data-ttu-id="27e74-120">若要切換圖表的可見性，請選取與圖表位於相同涵蓋範圍的文字方塊，例如，報表主體或矩形。</span><span class="sxs-lookup"><span data-stu-id="27e74-120">To toggle visibility of a chart, select a text box that is in the same containing scope as the chart; for example, the report body or a rectangle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27e74-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27e74-121">See Also</span></span>  
 <span data-ttu-id="27e74-122">[運算式範例 &#40;報表產生器及 SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="27e74-122">[Expression Examples &#40;Report Builder and SSRS&#41;](report-design/expression-examples-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="27e74-123">[將展開或折迭動作新增至 &#40;報表產生器和 SSRS 的專案&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="27e74-123">[Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](report-design/add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="27e74-124">[&#40;報表產生器和 SSRS&#41;的影像](report-design/images-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="27e74-124">[Images &#40;Report Builder and SSRS&#41;](report-design/images-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="27e74-125">報表設計師 F1 說明</span><span class="sxs-lookup"><span data-stu-id="27e74-125">Report Designer F1 Help</span></span>](tools/report-designer-f1-help.md)  
  
  
