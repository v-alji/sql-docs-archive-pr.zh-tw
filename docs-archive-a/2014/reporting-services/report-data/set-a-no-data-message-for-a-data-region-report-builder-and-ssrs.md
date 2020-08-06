---
title: 在資料區域中設定沒有資料的訊息 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4b194714-46f7-4f0e-9632-7f89d9600762
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9ed38ef14eb8f89753b4b3d7af3324ef0e88fa52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688590"
---
# <a name="set-a-no-data-message-for-a-data-region-report-builder-and-ssrs"></a><span data-ttu-id="cd591-102">在資料區域中設定沒有資料的訊息 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="cd591-102">Set a No Data Message for a Data Region (Report Builder and SSRS)</span></span>
  <span data-ttu-id="cd591-103">當您想要指定要在轉譯報表中顯示的文字來取代沒有資料的資料區時，請為資料表、矩陣或清單資料區域設定 NoRowsMessage 屬性，為圖表資料區設定 NoDataMessage，並為地圖的色階設定 NoDataText。</span><span class="sxs-lookup"><span data-stu-id="cd591-103">When you want to specify text to show in the rendered report in place of a data region that has no data, set the NoRowsMessage property for a table, matrix, or list data region, the NoDataMessage for a chart data region, and the NoDataText for the color scale for a map.</span></span> <span data-ttu-id="cd591-104">在執行階段，報表處理器會針對報表中的每一個資料集來執行查詢，而且資料集查詢可能不會產生任何結果集。</span><span class="sxs-lookup"><span data-stu-id="cd591-104">At run time, the report processor runs the query for each dataset in a report and the dataset query may produce no result set.</span></span> <span data-ttu-id="cd591-105">如果是繫結至空資料集的資料區，您可以指定要顯示的文字，而不是顯示空的資料區。</span><span class="sxs-lookup"><span data-stu-id="cd591-105">For a data region bound to an empty dataset, you can specify text to display instead of displaying an empty data region.</span></span> <span data-ttu-id="cd591-106">執行階段時如果子報表中的資料集都沒有資料，您也可以為子報表設定 NoRowsMessage 屬性。</span><span class="sxs-lookup"><span data-stu-id="cd591-106">You can also set the NoRowsMessage property for a subreport when no datasets in the subreport have data at run time.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-the-norowsmessage-property-for-a-table-matrix-or-list"></a><span data-ttu-id="cd591-107">為資料表、矩陣或清單設定 NoRowsMessage 屬性</span><span class="sxs-lookup"><span data-stu-id="cd591-107">To set the NoRowsMessage property for a table, matrix, or list</span></span>  
  
1.  <span data-ttu-id="cd591-108">在 [設計] 檢視中，按一下設計介面上的資料表、矩陣或清單資料區或子報表來加以選取。</span><span class="sxs-lookup"><span data-stu-id="cd591-108">In Design view, click the table, matrix, or list data region or subreport on the design surface to select it.</span></span> <span data-ttu-id="cd591-109">[屬性] 窗格會顯示所選取項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="cd591-109">The Properties pane displays the properties for the selected item.</span></span>  
  
2.  <span data-ttu-id="cd591-110">在 [屬性] 窗格中，輸入您想要在 [屬性] 欄位中顯示為訊息的文字 `NoRowsMessage` 。</span><span class="sxs-lookup"><span data-stu-id="cd591-110">In the Properties pane, type the text that you want to display as a message in `NoRowsMessage` property field.</span></span>  
  
     <span data-ttu-id="cd591-111">另外，您也可以從下拉式清單按一下 [運算式]  ，開啟 [運算式]  對話方塊，然後建立運算式。</span><span class="sxs-lookup"><span data-stu-id="cd591-111">Alternatively, from the drop-down list, click **Expression** to open the **Expression** dialog box and create an expression.</span></span>  
  
### <a name="to-set-the-nodatamessage-property-for-a-chart"></a><span data-ttu-id="cd591-112">為圖表設定 NoDataMessage 屬性</span><span class="sxs-lookup"><span data-stu-id="cd591-112">To set the NoDataMessage property for a chart</span></span>  
  
1.  <span data-ttu-id="cd591-113">在 [設計] 檢視中，按一下設計介面上的圖表加以選取。</span><span class="sxs-lookup"><span data-stu-id="cd591-113">In Design view, click the chart on the design surface to select it.</span></span> <span data-ttu-id="cd591-114">[屬性] 窗格會顯示所選取項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="cd591-114">The Properties pane displays the properties for the selected item.</span></span>  
  
2.  <span data-ttu-id="cd591-115">在 [屬性] 窗格中，展開的節點 `NoDataMessage` 。</span><span class="sxs-lookup"><span data-stu-id="cd591-115">In the Properties pane, expand the node for `NoDataMessage`.</span></span>  
  
3.  <span data-ttu-id="cd591-116">在 [**標題**] 中，輸入您想要在 [屬性] 欄位中顯示為訊息的文字 `NoDataMessage` 。</span><span class="sxs-lookup"><span data-stu-id="cd591-116">In **Caption**, type the text that you want to display as a message in `NoDataMessage` property field.</span></span>  
  
     <span data-ttu-id="cd591-117">另外，您也可以從下拉式清單按一下 [運算式]  ，開啟 [運算式]  對話方塊，然後建立運算式。</span><span class="sxs-lookup"><span data-stu-id="cd591-117">Alternatively, from the drop-down list, click **Expression** to open the **Expression** dialog box and create an expression.</span></span>  
  
### <a name="to-set-the-norowsmessage-for-a-subreport"></a><span data-ttu-id="cd591-118">為子報表設定 NoRowsMessage</span><span class="sxs-lookup"><span data-stu-id="cd591-118">To set the NoRowsMessage for a subreport</span></span>  
  
1.  <span data-ttu-id="cd591-119">在 [設計] 檢視中，按一下設計介面上的子報表加以選取。</span><span class="sxs-lookup"><span data-stu-id="cd591-119">In Design view, click the subreport on the design surface to select it.</span></span> <span data-ttu-id="cd591-120">[屬性] 窗格會顯示所選取項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="cd591-120">The Properties pane displays the properties for the selected item.</span></span>  
  
2.  <span data-ttu-id="cd591-121">在 [屬性] 窗格中，輸入您想要在 [屬性] 欄位中顯示為訊息的文字 `NoRowsMessage` 。</span><span class="sxs-lookup"><span data-stu-id="cd591-121">In the Properties pane, type the text that you want to display as a message in `NoRowsMessage` property field.</span></span>  
  
     <span data-ttu-id="cd591-122">另外，您也可以從下拉式清單按一下 [運算式]  ，開啟 [運算式]  對話方塊，然後建立運算式。</span><span class="sxs-lookup"><span data-stu-id="cd591-122">Alternatively, from the drop-down list, click **Expression** to open the **Expression** dialog box and create an expression.</span></span>  
  
### <a name="to-set-the-nodatatext-property-for-a-color-scale-for-a-map"></a><span data-ttu-id="cd591-123">若要為地圖的色階設定 NoDataText 屬性</span><span class="sxs-lookup"><span data-stu-id="cd591-123">To set the NoDataText property for a color scale for a map</span></span>  
  
1.  <span data-ttu-id="cd591-124">在 [設計] 檢視中，按一下地圖上的色階加以選取。</span><span class="sxs-lookup"><span data-stu-id="cd591-124">In Design view, click the color scale on the map to select it.</span></span> <span data-ttu-id="cd591-125">[屬性] 窗格會顯示所選取項目的屬性。</span><span class="sxs-lookup"><span data-stu-id="cd591-125">The Properties pane displays the properties for the selected item.</span></span>  
  
2.  <span data-ttu-id="cd591-126">在 [屬性] 窗格的 [] 中， `NoDataText` 輸入您要顯示成色彩標籤的文字（不含資料值）。</span><span class="sxs-lookup"><span data-stu-id="cd591-126">In the Properties pane, in `NoDataText`, type the text that you want to display as a label for colors with no data value.</span></span>  
  
     <span data-ttu-id="cd591-127">另外，您也可以從下拉式清單按一下 [運算式]  ，開啟 [運算式]  對話方塊，然後建立運算式。</span><span class="sxs-lookup"><span data-stu-id="cd591-127">Alternatively, from the drop-down list, click **Expression** to open the **Expression** dialog box and create an expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd591-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd591-128">See Also</span></span>  
 <span data-ttu-id="cd591-129">[子報表 &#40;報表產生器及 SSRS&#41;](../report-design/subreports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cd591-129">[Subreports &#40;Report Builder and SSRS&#41;](../report-design/subreports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="cd591-130">[資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cd591-130">[Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;](../report-design/create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="cd591-131">[圖表 &#40;報表產生器及 SSRS&#41;](../report-design/charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cd591-131">[Charts &#40;Report Builder and SSRS&#41;](../report-design/charts-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="cd591-132">[地圖 &#40;報表產生器及 SSRS&#41;](../report-design/maps-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="cd591-132">[Maps &#40;Report Builder and SSRS&#41;](../report-design/maps-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="cd591-133">子報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="cd591-133">Subreports &#40;Report Builder and SSRS&#41;</span></span>](../report-design/subreports-report-builder-and-ssrs.md)  
  
  
