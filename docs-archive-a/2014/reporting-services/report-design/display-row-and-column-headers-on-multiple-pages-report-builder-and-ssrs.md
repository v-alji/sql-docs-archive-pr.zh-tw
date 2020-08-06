---
title: 在多個頁面上顯示資料列和資料行標頭 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2422b1e2-822f-4379-9d7f-9afebb350e3f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2e3b38aa0faab267a0cd71feafe600829237b55c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704922"
---
# <a name="display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs"></a><span data-ttu-id="81586-102">在多個頁面上顯示資料列和資料行標頭 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="81586-102">Display Row and Column Headers on Multiple Pages (Report Builder and SSRS)</span></span>
  <span data-ttu-id="81586-103">您可以控制是否要針對跨多個頁面的 Tablix 資料區，在每個頁面上重複資料列和資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="81586-103">You can control whether to repeat row and column headers on every page for a tablix data region that spans multiple pages.</span></span> <span data-ttu-id="81586-104">Tablix 資料區可以是資料表、矩陣或清單。</span><span class="sxs-lookup"><span data-stu-id="81586-104">A tablix data region can be a table, matrix, or list.</span></span>  
  
 <span data-ttu-id="81586-105">控制資料列和資料行的方式，是根據 Tablix 資料區是否具有群組標題而定。</span><span class="sxs-lookup"><span data-stu-id="81586-105">How you control the rows and columns depends on whether the tablix data region has group headers.</span></span> <span data-ttu-id="81586-106">當您在具有群組標題的 Tablix 資料區內按一下時，虛線會顯示 Tablix 區域，如下圖中所示：</span><span class="sxs-lookup"><span data-stu-id="81586-106">When you click in a tablix data region that has group headers, a dotted line shows the tablix areas, as shown in the following figure:</span></span>  
  
 <span data-ttu-id="81586-107">![Tablix 資料區的區域](../media/rs-tablixareas.gif "Tablix 資料區的區域")</span><span class="sxs-lookup"><span data-stu-id="81586-107">![Tablix data region areas](../media/rs-tablixareas.gif "Tablix data region areas")</span></span>  
  
 <span data-ttu-id="81586-108">當您藉由使用 [新增資料表] 或 [矩陣精靈] 或 [新增圖表精靈]、在 [群組] 窗格中新增欄位或使用內容選單來新增群組時，會自動建立資料列和資料行的群組標頭。</span><span class="sxs-lookup"><span data-stu-id="81586-108">Row and column group headers are created automatically when you add groups by using the New Table or Matrix wizard or the New Chart wizard, by adding fields to the Grouping pane, or by using context menus.</span></span> <span data-ttu-id="81586-109">如果 Tablix 資料區只有 Tablix 主體而沒有群組頁首，則資料行和資料列就是 Tablix 成員。</span><span class="sxs-lookup"><span data-stu-id="81586-109">If the tablix data region has only a tablix body area and no group headers, the rows and columns are tablix members.</span></span>  
  
 <span data-ttu-id="81586-110">對靜態成員而言，您可以在多個頁面上顯示頂端相鄰的資料列或側邊相鄰的資料行。</span><span class="sxs-lookup"><span data-stu-id="81586-110">For static members, you can display the top adjacent rows or the side adjacent columns on multiple pages.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-display-row-headers-on-multiple-pages"></a><span data-ttu-id="81586-111">若要在多個頁面上顯示資料列標頭</span><span class="sxs-lookup"><span data-stu-id="81586-111">To display row headers on multiple pages</span></span>  
  
1.  <span data-ttu-id="81586-112">以滑鼠右鍵按一下 Tablix 資料區的資料列、資料行或角控點，然後按一下 **[Tablix 屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="81586-112">Right-click the row, column, or corner handle of a tablix data region, and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="81586-113">在 **[資料列標頭]** 中，選取 **[在每一頁重複標頭資料列]** 。</span><span class="sxs-lookup"><span data-stu-id="81586-113">In **Row Headers**, select **Repeat header rows on each page**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-display-column-headers-on-multiple-pages"></a><span data-ttu-id="81586-114">在多個頁面上顯示資料行標頭</span><span class="sxs-lookup"><span data-stu-id="81586-114">To display column headers on multiple pages</span></span>  
  
1.  <span data-ttu-id="81586-115">以滑鼠右鍵按一下 Tablix 資料區的資料列、資料行或角控點，然後按一下 **[Tablix 屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="81586-115">Right-click the row, column, or corner handle of a tablix data region, and then click **Tablix Properties**.</span></span>  
  
2.  <span data-ttu-id="81586-116">在 **[資料行標頭]** 中，選取 **[在每一頁重複標頭資料行]** 。</span><span class="sxs-lookup"><span data-stu-id="81586-116">In **Column Headers**, select **Repeat header columns on each page**.</span></span>  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### <a name="to-display-a-static-tablix-member-row-or-column-on-multiple-pages"></a><span data-ttu-id="81586-117">若要在多個頁面上顯示靜態 Tablix 成員 (資料列或資料行)</span><span class="sxs-lookup"><span data-stu-id="81586-117">To display a static tablix member (row or column) on multiple pages</span></span>  
  
1.  <span data-ttu-id="81586-118">在設計介面上，按一下 Tablix 資料區的資料列或資料行控點來選取它。</span><span class="sxs-lookup"><span data-stu-id="81586-118">On the design surface, click the row or column handle of the tablix data region to select it.</span></span> <span data-ttu-id="81586-119">[群組] 窗格會顯示資料列和資料行群組。</span><span class="sxs-lookup"><span data-stu-id="81586-119">The Grouping pane displays the row and column groups.</span></span>  
  
2.  <span data-ttu-id="81586-120">在 [群組] 窗格的右邊按一下向下箭頭，然後按一下 **[進階模式]** 。</span><span class="sxs-lookup"><span data-stu-id="81586-120">On the right side of the Grouping pane, click the down arrow, and then click **Advanced Mode**.</span></span> <span data-ttu-id="81586-121">[資料列群組] 窗格會顯示資料列群組階層的階層式靜態及動態成員，[資料行群組] 窗格則會為資料行群組階層顯示類似的內容。</span><span class="sxs-lookup"><span data-stu-id="81586-121">The Row Groups pane displays the hierarchical static and dynamic members for the row groups hierarchy and the Column groups pane shows a similar display for the column groups hierarchy.</span></span>  
  
3.  <span data-ttu-id="81586-122">按一下對應至要在捲動時保持可見之靜態成員 (資料列或資料行) 的靜態成員。</span><span class="sxs-lookup"><span data-stu-id="81586-122">Click the static member that corresponds to the static member (row or column) that you want to remain visible while scrolling.</span></span> <span data-ttu-id="81586-123">[屬性] 窗格會顯示 **[Tablix 成員]** 屬性。</span><span class="sxs-lookup"><span data-stu-id="81586-123">The Properties pane displays the **Tablix Member** properties.</span></span>  
  
     <span data-ttu-id="81586-124">如果看不到 [屬性] 窗格，請按一下報表產生器視窗最上方的 [檢視]  索引標籤，然後按一下 [屬性]  。</span><span class="sxs-lookup"><span data-stu-id="81586-124">If you don't see the Properties pane, click the **View** tab at the top of the Report Builder window and then click **Properties**.</span></span>  
  
4.  <span data-ttu-id="81586-125">在 [屬性] 窗格中，將 **[RepeatOnNewPage]** 設定為 [True]。</span><span class="sxs-lookup"><span data-stu-id="81586-125">In the Properties pane, set **RepeatOnNewPage** to True.</span></span>  
  
5.  <span data-ttu-id="81586-126">將 **[KeepWithGroup]** 設定為 [After]。</span><span class="sxs-lookup"><span data-stu-id="81586-126">Set **KeepWithGroup** to After.</span></span>  
  
6.  <span data-ttu-id="81586-127">針對您要重複的相鄰成員重複這個步驟。</span><span class="sxs-lookup"><span data-stu-id="81586-127">Repeat this for as many adjacent members as you want to repeat.</span></span>  
  
7.  <span data-ttu-id="81586-128">預覽報表。</span><span class="sxs-lookup"><span data-stu-id="81586-128">Preview the report.</span></span>  
  
 <span data-ttu-id="81586-129">當您檢視 Tablix 資料區所跨越之報表的每個頁面時，靜態 Tablix 成員就會在每個頁面上重複。</span><span class="sxs-lookup"><span data-stu-id="81586-129">As you view each page of the report that the tablix data region spans, the static tablix members repeat on each page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81586-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81586-130">See Also</span></span>  
 <span data-ttu-id="81586-131">[尋找、檢視和管理報表 &#40;報表產生器及 SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="81586-131">[Finding, Viewing, and Managing Reports &#40;Report Builder and SSRS &#41;](../report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="81586-132">[匯出報表 &#40;報表產生器和 SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="81586-132">[Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="81586-133">[控制分頁符號、標題、資料行和資料列 &#40;報表產生器及 SSRS&#41;](controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="81586-133">[Controlling Page Breaks, Headings, Columns, and Rows &#40;Report Builder and SSRS&#41;](controlling-page-breaks-headings-columns-and-rows-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="81586-134">[與群組一起顯示頁首和頁尾 &#40;報表產生器及 SSRS&#41;](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="81586-134">[Display Headers and Footers with a Group &#40;Report Builder and SSRS&#41;](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="81586-135">在報表中捲動時將標頭保持可見 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="81586-135">Keep Headers Visible When Scrolling Through a Report &#40;Report Builder and SSRS&#41;</span></span>](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md)  
  
  
