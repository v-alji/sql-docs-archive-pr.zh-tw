---
title: 在報表中捲動時將標頭保持可見 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 6d9192a4-fd5c-41ad-b9ef-f88f9496afed
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d37fcd38a402dc0f88ac002c679c1046d5b0b583
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707097"
---
# <a name="keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs"></a><span data-ttu-id="1da4f-102">在報表中捲動時將標頭保持可見 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="1da4f-102">Keep Headers Visible When Scrolling Through a Report (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1da4f-103">若要避免資料列和資料行的標籤在轉譯報表之後捲動到檢視畫面以外，可以將資料列或資料行的標題凍結。</span><span class="sxs-lookup"><span data-stu-id="1da4f-103">To prevent row and column labels from scrolling out of view after rendering a report, you can freeze the row or column headings.</span></span>  
  
 <span data-ttu-id="1da4f-104">如何控制資料列和資料行取決於您擁有資料表還是矩陣。</span><span class="sxs-lookup"><span data-stu-id="1da4f-104">How you control the rows and columns depends on whether you have a table or a matrix.</span></span> <span data-ttu-id="1da4f-105">如果您有資料表，請設定靜態成員 (資料列和資料行標題) 來維持可見度。</span><span class="sxs-lookup"><span data-stu-id="1da4f-105">If you have a table, you configure static members (row and column headings) to remain visible.</span></span> <span data-ttu-id="1da4f-106">如果您有矩陣，請設定資料列和資料行群組標頭來維持可見度。</span><span class="sxs-lookup"><span data-stu-id="1da4f-106">If you have a matrix, you configure row and column group headers to remain visible.</span></span>  
  
 <span data-ttu-id="1da4f-107">如果您將報表匯出到 Excel，標頭將不會自動凍結。</span><span class="sxs-lookup"><span data-stu-id="1da4f-107">If you export the report to Excel, the header will not be frozen automatically.</span></span> <span data-ttu-id="1da4f-108">您可以在 Excel 中凍結窗格。</span><span class="sxs-lookup"><span data-stu-id="1da4f-108">You can freeze the pane in Excel.</span></span> <span data-ttu-id="1da4f-109">如需詳細資訊，請參閱[匯出至 Microsoft Excel &#40;報表產生器及 SSRS&#41;](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md)的**頁首和頁尾**一節。</span><span class="sxs-lookup"><span data-stu-id="1da4f-109">For more information see the **Page Headers and Footers** section of [Exporting to Microsoft Excel &#40;Report Builder and SSRS&#41;](../report-builder/exporting-to-microsoft-excel-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1da4f-110">即使資料表包含資料列和資料行群組，您還是無法在捲動時維持這些群組標頭的可見度</span><span class="sxs-lookup"><span data-stu-id="1da4f-110">Even if a table has row and column groups, you cannot keep those group headers visible while scrolling</span></span>  
  
 <span data-ttu-id="1da4f-111">下圖顯示一個資料表。</span><span class="sxs-lookup"><span data-stu-id="1da4f-111">The following image shows a table.</span></span>  
  
 <span data-ttu-id="1da4f-112">![Table](../media/table.png "Table")</span><span class="sxs-lookup"><span data-stu-id="1da4f-112">![Table](../media/table.png "Table")</span></span>  
  
 <span data-ttu-id="1da4f-113">下圖顯示一個矩陣。</span><span class="sxs-lookup"><span data-stu-id="1da4f-113">The following image shows a matrix.</span></span>  
  
 <span data-ttu-id="1da4f-114">![矩陣](../media/matrix.png "矩陣")</span><span class="sxs-lookup"><span data-stu-id="1da4f-114">![Matrix](../media/matrix.png "Matrix")</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-keep-matrix-group-headers-visible-while-scrolling"></a><span data-ttu-id="1da4f-115">若要在捲動時維持矩陣群組標頭的可見度</span><span class="sxs-lookup"><span data-stu-id="1da4f-115">To keep matrix group headers visible while scrolling</span></span>  
  
1.  <span data-ttu-id="1da4f-116">以滑鼠右鍵按一下 Tablix 資料區的資料列、資料行或角控點，然後按一下 **[Tablix 屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="1da4f-116">Right-click the row, column, or corner handle of a tablix data region, and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="1da4f-117">在 **[一般]** 索引標籤的 **[資料列標頭]** 或 **[資料行標頭]** 下方選取 **[捲動時，標頭應保持可見]** 。</span><span class="sxs-lookup"><span data-stu-id="1da4f-117">On the **General** tab, under **Row Headers** or **Column Headers**, select **Header should remain visible while scrolling**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-keep-a-static-tablix-member-row-or-column-visible-while-scrolling"></a><span data-ttu-id="1da4f-118">若要在捲動時將靜態 Tablix 成員 (資料列或資料行) 保持可見</span><span class="sxs-lookup"><span data-stu-id="1da4f-118">To keep a static tablix member (row or column) visible while scrolling</span></span>  
  
1.  <span data-ttu-id="1da4f-119">在設計介面上，按一下資料表中的任何地方即可在群組窗格中顯示靜態成員以及群組。</span><span class="sxs-lookup"><span data-stu-id="1da4f-119">On the design surface, click anywhere in the table to display static members, as well as groups, in the grouping pane.</span></span>  
  
     <span data-ttu-id="1da4f-120">![群組窗格](../media/grouppane-updated.png "群組窗格")</span><span class="sxs-lookup"><span data-stu-id="1da4f-120">![Grouping pane](../media/grouppane-updated.png "Grouping pane")</span></span>  
  
     <span data-ttu-id="1da4f-121">[資料列群組] 窗格會顯示資料列群組階層的階層式靜態及動態成員，[資料行群組] 窗格則會為資料行群組階層顯示類似的內容。</span><span class="sxs-lookup"><span data-stu-id="1da4f-121">The Row Groups pane displays the hierarchical static and dynamic members for the row groups hierarchy, and the Column groups pane shows a similar display for the column groups hierarchy.</span></span>  
  
2.  <span data-ttu-id="1da4f-122">在 [群組] 窗格的右邊按一下向下箭頭，然後按一下 **[進階模式]** 。</span><span class="sxs-lookup"><span data-stu-id="1da4f-122">On the right side of the grouping pane, click the down arrow, and then click **Advanced Mode**.</span></span>  
  
3.  <span data-ttu-id="1da4f-123">在捲動時按一下您要保持可見的靜態成員 (資料列或資料行)。</span><span class="sxs-lookup"><span data-stu-id="1da4f-123">Click the static member (row or column) that you want to remain visible while scrolling.</span></span> <span data-ttu-id="1da4f-124">[屬性] 窗格會顯示 **[Tablix 成員]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="1da4f-124">The Properties pane displays the **Tablix Member** properties.</span></span>  
  
     <span data-ttu-id="1da4f-125">![Tablix 成員屬性](../media/grouppane-tablixmember-updated.png "Tablix 成員屬性")</span><span class="sxs-lookup"><span data-stu-id="1da4f-125">![Tablix Member properties](../media/grouppane-tablixmember-updated.png "Tablix Member properties")</span></span>  
  
4.  <span data-ttu-id="1da4f-126">在 [屬性] 窗格中，將**FixedData**設定為 `True` 。</span><span class="sxs-lookup"><span data-stu-id="1da4f-126">In the Properties pane, set **FixedData** to `True`.</span></span>  
  
5.  <span data-ttu-id="1da4f-127">針對您要在捲動時保持可見的相鄰成員重複這個步驟。</span><span class="sxs-lookup"><span data-stu-id="1da4f-127">Repeat this for as many adjacent members as you want to keep visible while scrolling.</span></span>  
  
6.  <span data-ttu-id="1da4f-128">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="1da4f-128">Preview the report.</span></span>  
  
 <span data-ttu-id="1da4f-129">當您向下或向側邊捲動一頁時，靜態的 Tablix 成員仍會維持在檢視中。</span><span class="sxs-lookup"><span data-stu-id="1da4f-129">As you page down or across the report, the static tablix members remain in view.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1da4f-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1da4f-130">See Also</span></span>  
 <span data-ttu-id="1da4f-131">[Tablix 資料區 &#40;報表產生器及 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1da4f-131">[Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1da4f-132">[尋找、檢視和管理報表 &#40;報表產生器及 SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1da4f-132">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1da4f-133">[匯出報表 &#40;報表產生器和 SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1da4f-133">[Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1da4f-134">[與群組一起顯示頁首和頁尾 &#40;報表產生器及 SSRS&#41;](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1da4f-134">[Display Headers and Footers with a Group &#40;Report Builder and SSRS&#41;](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1da4f-135">[在多個頁面上顯示資料列和資料行標頭 &#40;報表產生器及 SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1da4f-135">[Display Row and Column Headers on Multiple Pages &#40;Report Builder and SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1da4f-136">群組窗格 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="1da4f-136">Grouping Pane &#40;Report Builder&#41;</span></span>](grouping-pane-report-builder.md)  
  
  
