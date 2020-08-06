---
title: 變更報表參數的順序 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: abd61e19-dba3-423c-a26c-e8bc43197d3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ad9dd25be7a87fee089a48849fcc716e682e4c64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706198"
---
# <a name="change-the-order-of-a-report-parameter-report-builder-and-ssrs"></a><span data-ttu-id="dad8a-102">變更報表參數的順序 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="dad8a-102">Change the Order of a Report Parameter (Report Builder and SSRS)</span></span>
  <span data-ttu-id="dad8a-103">當您的相依參數列在它所相依的參數之前時，請變更報表參數的順序。</span><span class="sxs-lookup"><span data-stu-id="dad8a-103">Change the order of report parameters when you have a dependent parameter that is listed before the parameter it is dependent on.</span></span> <span data-ttu-id="dad8a-104">當您具有串聯參數，或是當您想要為使用者顯示一個參數的預設值，然後使用者才可選擇其他參數值時，參數順序會很重要。</span><span class="sxs-lookup"><span data-stu-id="dad8a-104">Parameter order is important when you have cascading parameters, or when you want to show users the default value for one parameter before they choose values for other parameters.</span></span> <span data-ttu-id="dad8a-105">相依報表參數包含了查詢參數的參考 (在它的預設值查詢或是有效值查詢中)，該查詢參數會指向 [報表資料] 窗格中參數清單內列在它後面的報表參數。</span><span class="sxs-lookup"><span data-stu-id="dad8a-105">A dependent report parameter contains a reference, in either its default values query or valid values query, to a query parameter that points to a report parameter that is after it in the parameter list in the Report Data pane.</span></span>  
  
 <span data-ttu-id="dad8a-106">您在報表檢視器工具列上看到的參數顯示順序是由 [報表資料] 窗格內的參數順序所決定。</span><span class="sxs-lookup"><span data-stu-id="dad8a-106">The order that you see parameters display on the report viewer toolbar is determined by the order of the parameters in the Report Data pane.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-order-of-report-parameters"></a><span data-ttu-id="dad8a-107">變更報表參數的順序</span><span class="sxs-lookup"><span data-stu-id="dad8a-107">To change the order of report parameters</span></span>  
  
1.  <span data-ttu-id="dad8a-108">在 [報表資料] 窗格中，展開 [參數] 節點。</span><span class="sxs-lookup"><span data-stu-id="dad8a-108">In the Report Data pane, expand the Parameters node.</span></span>  
  
2.  <span data-ttu-id="dad8a-109">按一下參數，並使用 [報表資料] 窗格工具列上的向上箭頭和向下箭頭按鈕，在清單中將參數上移或下移。</span><span class="sxs-lookup"><span data-stu-id="dad8a-109">Click a parameter and use the up and down arrow buttons on the Report Data pane toolbar to move the parameter higher or lower in the list.</span></span> <span data-ttu-id="dad8a-110">下圖顯示報表產生器中的 [報表資料] 窗格。</span><span class="sxs-lookup"><span data-stu-id="dad8a-110">The following image shows the Report Data pane in Report Builder.</span></span>  
  
     <span data-ttu-id="dad8a-111">![報表資料窗格](../media/reportdatapane.png "報表資料窗格")</span><span class="sxs-lookup"><span data-stu-id="dad8a-111">![Report Data Pane](../media/reportdatapane.png "Report Data Pane")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad8a-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dad8a-112">See Also</span></span>  
 <span data-ttu-id="dad8a-113">[報表參數 &#40;報表產生器和報表設計師&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="dad8a-113">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="dad8a-114">[對話方塊、窗格和嚮導的報表產生器說明](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span><span class="sxs-lookup"><span data-stu-id="dad8a-114">[Report Builder Help for Dialog Boxes, Panes, and Wizards](../report-builder-help-for-dialog-boxes-panes-and-wizards.md) </span></span>  
 <span data-ttu-id="dad8a-115">[將串聯參數加入至報表 &#40;報表產生器和 SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="dad8a-115">[Add Cascading Parameters to a Report &#40;Report Builder and SSRS&#41;](add-cascading-parameters-to-a-report-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="dad8a-116">[教學課程：將參數加入至您的報表 &#40;報表產生器&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span><span class="sxs-lookup"><span data-stu-id="dad8a-116">[Tutorial: Add a Parameter to Your Report &#40;Report Builder&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md) </span></span>  
 <span data-ttu-id="dad8a-117">[新增資料集篩選、資料區域篩選和群組篩選 &#40;報表產生器和 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="dad8a-117">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 [<span data-ttu-id="dad8a-118">參數集合參考 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="dad8a-118">Parameters Collection References &#40;Report Builder and SSRS&#41;</span></span>](built-in-collections-parameters-collection-references-report-builder.md)  
  
  
