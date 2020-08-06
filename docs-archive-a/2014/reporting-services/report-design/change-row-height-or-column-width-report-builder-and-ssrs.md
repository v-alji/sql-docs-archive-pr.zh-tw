---
title: 變更資料列高度或資料行寬度 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: f061c204-5cd5-4467-9a9c-8a12803d93ba
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b5d75a8101d07d7d6e81c624d08cd951277936eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598216"
---
# <a name="change-row-height-or-column-width-report-builder-and-ssrs"></a><span data-ttu-id="01035-102">變更資料列高度或資料行寬度 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="01035-102">Change Row Height or Column Width (Report Builder and SSRS)</span></span>
  <span data-ttu-id="01035-103">當您設定資料列高度時，就是針對轉譯報表中的資料列指定最大高度。</span><span class="sxs-lookup"><span data-stu-id="01035-103">When you set a row height, you are specifying the maximum height for the row in the rendered report.</span></span> <span data-ttu-id="01035-104">不過，根據預設，資料列中的文字方塊會設定為垂直成長，以便在執行階段容納其資料，而且這可能會導致資料列擴展超過您所指定的高度。</span><span class="sxs-lookup"><span data-stu-id="01035-104">However, by default, text boxes in the row are set to grow vertically to accommodate their data at run-time, and this can cause a row to expand beyond the height that you specify.</span></span> <span data-ttu-id="01035-105">若要設定固定的資料列高度，您必須變更文字方塊屬性，讓它們不會自動擴展。</span><span class="sxs-lookup"><span data-stu-id="01035-105">To set a fixed row height, you must change the text box properties so they do not automatically expand.</span></span>  
  
 <span data-ttu-id="01035-106">當您設定資料行寬度時，就是針對轉譯報表中的資料行指定最大寬度。</span><span class="sxs-lookup"><span data-stu-id="01035-106">When you set a column width, you are specifying the maximum width for the column in the rendered report.</span></span> <span data-ttu-id="01035-107">資料行不會自動水平調整來容納文字。</span><span class="sxs-lookup"><span data-stu-id="01035-107">Columns do not automatically adjust horizontally to accommodate text.</span></span>  
  
 <span data-ttu-id="01035-108">如果資料列或資料行中的資料格包含矩形或資料區，則資料格的最小高度和寬度就是由包含項目的高度和寬度所決定。</span><span class="sxs-lookup"><span data-stu-id="01035-108">If a cell in a row or column contains a rectangle or data region, the minimum height and width of the cell is determined by the height and width of the contained item.</span></span> <span data-ttu-id="01035-109">如需詳細資訊，請參閱[轉譯行為 &#40;報表產生器及 SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="01035-109">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-row-height-by-moving-row-handles"></a><span data-ttu-id="01035-110">移動資料列控制代碼以變更資料列高度</span><span class="sxs-lookup"><span data-stu-id="01035-110">To change row height by moving row handles</span></span>  
  
1.  <span data-ttu-id="01035-111">在 [設計] 檢視中，按一下 Tablix 資料區中的任何位置，即可選取它。</span><span class="sxs-lookup"><span data-stu-id="01035-111">In Design view, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="01035-112">灰色的資料列控制代碼會顯示在 Tablix 資料區的外框線上。</span><span class="sxs-lookup"><span data-stu-id="01035-112">Gray row handles appear on the outside border of the tablix data region.</span></span>  
  
2.  <span data-ttu-id="01035-113">將滑鼠指標停留在您想要擴展的資料列控制代碼邊緣。</span><span class="sxs-lookup"><span data-stu-id="01035-113">Hover over the row handle edge that you want to expand.</span></span> <span data-ttu-id="01035-114">此時就會出現雙向箭頭。</span><span class="sxs-lookup"><span data-stu-id="01035-114">A double-headed arrow appears.</span></span>  
  
3.  <span data-ttu-id="01035-115">按一下以抓取資料列的邊緣，然後向上或向下移動，以便調整資料列高度。</span><span class="sxs-lookup"><span data-stu-id="01035-115">Click to grab the edge of the row and move it higher or lower to adjust the row height.</span></span>  
  
### <a name="to-change-row-height-by-setting-cell-properties"></a><span data-ttu-id="01035-116">設定儲存格屬性以變更資料列高度</span><span class="sxs-lookup"><span data-stu-id="01035-116">To change row height by setting cell properties</span></span>  
  
1.  <span data-ttu-id="01035-117">在 [設計] 檢視中，按一下資料表資料列中的儲存格。</span><span class="sxs-lookup"><span data-stu-id="01035-117">In Design view, click a cell in the table row.</span></span>  
  
     <span data-ttu-id="01035-118">![資料表中選取的資料格](../media/table-selectcell.png "資料表中選取的資料格")</span><span class="sxs-lookup"><span data-stu-id="01035-118">![Selected Cell in a Table](../media/table-selectcell.png "Selected Cell in a Table")</span></span>  
  
2.  <span data-ttu-id="01035-119">在顯示的 **[屬性]** 窗格中，修改 **[高度]** 屬性，然後按一下 **[屬性]** 窗格外的任何位置。</span><span class="sxs-lookup"><span data-stu-id="01035-119">In the **Properties** pane that displays, modify the **Height** property, and then click anywhere outside the **Properties** pane.</span></span>  
  
     <span data-ttu-id="01035-120">![適用於所選取資料表資料格的 [屬性] 窗格](../media/cell-propertiespane.png "適用於所選取資料表資料格的 [屬性] 窗格")</span><span class="sxs-lookup"><span data-stu-id="01035-120">![Properties Pane for selected table cell](../media/cell-propertiespane.png "Properties Pane for selected table cell")</span></span>  
  
### <a name="to-prevent-a-row-from-automatically-expanding-vertically"></a><span data-ttu-id="01035-121">防止資料列自動垂直擴展</span><span class="sxs-lookup"><span data-stu-id="01035-121">To prevent a row from automatically expanding vertically</span></span>  
  
1.  <span data-ttu-id="01035-122">在 [設計] 檢視中，按一下 Tablix 資料區中的任何位置，即可選取它。</span><span class="sxs-lookup"><span data-stu-id="01035-122">In Design view, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="01035-123">灰色的資料列控制代碼會顯示在 Tablix 資料區的外框線上。</span><span class="sxs-lookup"><span data-stu-id="01035-123">Gray row handles appear on the outside border of the tablix data region.</span></span>  
  
2.  <span data-ttu-id="01035-124">按一下資料列控制代碼，即可選取此資料列。</span><span class="sxs-lookup"><span data-stu-id="01035-124">Click the row handle to select the row.</span></span>  
  
3.  <span data-ttu-id="01035-125">在 [屬性] 窗格中，將 CanGrow 設為 [False]  。</span><span class="sxs-lookup"><span data-stu-id="01035-125">In the Properties pane, set CanGrow to **False**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="01035-126">如果您看不到 [屬性] 窗格，請按一下 **[檢視]** 功能表上的 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="01035-126">If you cannot see the Properties pane, from the **View** menu, click **Properties**.</span></span>  
  
### <a name="to-change-column-width"></a><span data-ttu-id="01035-127">若要變更資料行寬度</span><span class="sxs-lookup"><span data-stu-id="01035-127">To change column width</span></span>  
  
1.  <span data-ttu-id="01035-128">在 [設計] 檢視中，按一下 Tablix 資料區中的任何位置，即可選取它。</span><span class="sxs-lookup"><span data-stu-id="01035-128">In Design view, click anywhere in the tablix data region to select it.</span></span> <span data-ttu-id="01035-129">灰色的資料行控制代碼會顯示在 Tablix 資料區的外框線上。</span><span class="sxs-lookup"><span data-stu-id="01035-129">Gray column handles appear on the outside border of the tablix data region.</span></span>  
  
2.  <span data-ttu-id="01035-130">將滑鼠指標停留在您想要擴展的資料行控制代碼邊緣上方，</span><span class="sxs-lookup"><span data-stu-id="01035-130">Hover over the column handle edge that you want to expand.</span></span> <span data-ttu-id="01035-131">此時就會出現雙向箭頭。</span><span class="sxs-lookup"><span data-stu-id="01035-131">A double-headed arrow appears.</span></span>  
  
3.  <span data-ttu-id="01035-132">按一下以抓取資料行的邊緣，然後向左或向右移動，以便調整資料行寬度。</span><span class="sxs-lookup"><span data-stu-id="01035-132">Click to grab the edge of the column and move it left or right to adjust the column width.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01035-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01035-133">See Also</span></span>  
 <span data-ttu-id="01035-134">[Tablix 資料區 &#40;報表產生器和 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="01035-134">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="01035-135">[Tablix 資料區域儲存格、資料列和資料行 &#40;報表產生器&#41; 和 SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="01035-135">[Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="01035-136">[資料表 &#40;報表產生器和 SSRS&#41;](tables-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="01035-136">[Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="01035-137">[&#40;報表產生器和 SSRS&#41;的矩陣](create-a-matrix-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="01035-137">[Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="01035-138">[列出 &#40;報表產生器和 SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="01035-138">[Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="01035-139">資料表、矩陣和清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="01035-139">Tables, Matrices, and Lists &#40;Report Builder and SSRS&#41;</span></span>](tables-matrices-and-lists-report-builder-and-ssrs.md)  
  
  
