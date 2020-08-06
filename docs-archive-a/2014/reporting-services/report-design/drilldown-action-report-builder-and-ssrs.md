---
title: 向下鑽研動作 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10249"
- "10186"
- sql12.rtp.rptdesigner.calculatedseriesproperties.visibility.f1
- sql12.rtp.rptdesigner.seriesproperties.visibility.f1
- sql12.rtp.rptdesigner.chartareaproperties.visibility.f1
- "10092"
- sql12.rtp.rptdesigner.textboxproperties.visibility.f1
- sql12.rtp.rptdesigner.charttitleproperties.visibility.f1
- "10167"
- sql12.rtp.rptdesigner.rectangleproperties.visibility.f1
- "10174"
- sql12.rtp.rptdesigner.majorgridlineproperties.visibility.f1
- "10155"
- "10123"
- sql12.rtp.rptdesigner.subreportproperties.visibility.f1
- "10425"
- sql12.rtp.rptdesigner.minorgridlineproperties.visibility.f1
- "10217"
- sql12.rtp.rptdesigner.axisproperties.visibility.f1
- sql12.rtp.rptdesigner.serieslabelproperties.visibility.f1
- "10161"
- sql12.rtp.rptdesigner.chartproperties.visibility.f1
- sql12.rtp.rptdesigner.legendproperties.visibility.f1
- sql12.rtp.rptdesigner.pictureproperties.visibility.f1
- "10215"
- "10258"
- "10144"
- "10062"
- "10053"
ms.assetid: 1f8d1ef2-0daf-40c6-9ba7-3b391249bcd4
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2fe3d55dc70a606df759c049b7b147820f0e3110
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599358"
---
# <a name="drilldown-action-report-builder-and-ssrs"></a><span data-ttu-id="a5838-102">向下鑽研動作 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="a5838-102">Drilldown Action (Report Builder and SSRS)</span></span>
  <span data-ttu-id="a5838-103">透過在文字方塊上提供加號和減號圖示，您就可以讓使用者以互動方式隱藏和顯示項目。</span><span class="sxs-lookup"><span data-stu-id="a5838-103">B providing plus and minus icons on a text box, you can enable users to hide and display items interactively.</span></span> <span data-ttu-id="a5838-104">這稱為 *「向下鑽研」* (Drilldown) 動作。</span><span class="sxs-lookup"><span data-stu-id="a5838-104">This is called a *drilldown* action.</span></span> <span data-ttu-id="a5838-105">對於資料表或矩陣，您可以顯示或隱藏靜態資料列和資料行，或者顯示或隱藏與群組相關聯的資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="a5838-105">For a table or matrix, you can show or hide static rows and columns, or rows and columns that are associated with groups.</span></span>  
  
 <span data-ttu-id="a5838-106">![rs_drilldown](../media/rs-drilldown.gif "rs_drilldown")</span><span class="sxs-lookup"><span data-stu-id="a5838-106">![rs_drilldown](../media/rs-drilldown.gif "rs_drilldown")</span></span>  
  
 <span data-ttu-id="a5838-107">在此圖中，使用者可以按一下報表中的加號 (+) 來顯示詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a5838-107">In this illustration, the user clicks the plus signs (+) in the report to show detail data.</span></span>  
  
 <span data-ttu-id="a5838-108">例如，除了包含資料列群組之資料表的外部群組摘要資料列之外，您可以一開始隱藏所有資料列。</span><span class="sxs-lookup"><span data-stu-id="a5838-108">For example, you can initially hide all the rows except the outer group summary row for a table with row groups.</span></span> <span data-ttu-id="a5838-109">為每個內部群組 (包括詳細資料群組) 之包含群組的群組資料格，加入展開/摺疊圖示。</span><span class="sxs-lookup"><span data-stu-id="a5838-109">For each inner group (including the details group), add an expand/collapse icon to the grouping cell of the containing group.</span></span> <span data-ttu-id="a5838-110">轉譯報表時，使用者可以按一下文字方塊，以展開和摺疊詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a5838-110">When the report is rendered, the user can click the text box to expand and collapse the detail data.</span></span> <span data-ttu-id="a5838-111">如需詳細資訊，請參閱[資料表 &#40;報表產生器及 SSRS&#41;](tables-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a5838-111">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="a5838-112">若要讓使用者展開或摺疊項目，您可以設定該項目的可見性屬性。</span><span class="sxs-lookup"><span data-stu-id="a5838-112">To allow users to expand or collapse an item, you set the visibility properties for that item.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a5838-113">當您建立具有向下鑽研動作的報表時，您必須設定您要隱藏之群組、資料行或資料列的可見性資訊，而不只是資料列或資料行中之單一文字方塊的可見性資訊。</span><span class="sxs-lookup"><span data-stu-id="a5838-113">When you create a report with a drilldown action, the visibility information must be set on the group, column, or row that you want to hide, not just a single text box in the row or column.</span></span> <span data-ttu-id="a5838-114">此外，您用於切換的文字方塊必須位於可控制您要顯示或隱藏之項目的包含範圍內。</span><span class="sxs-lookup"><span data-stu-id="a5838-114">In addition, the text box that you use for the toggle must be in a containing scope that controls the item that you want to show or hide.</span></span>  
>   
>  <span data-ttu-id="a5838-115">例如，若要隱藏與巢狀群組相關聯的資料列，文字方塊必須位於與父群組相關聯的資料列中，或是位於內含項目階層中更高的位置。</span><span class="sxs-lookup"><span data-stu-id="a5838-115">For example, to hide a row associated with a nested group, the text box must be in a row associated with the parent group or higher in the containment hierarchy.</span></span>  
>   
>  <span data-ttu-id="a5838-116">如需設定群組、資料行或資料列之可見度資訊的資訊，請參閱[將展開或摺疊動作新增項目中 &#40;報表產生器及 SSRS&#41;](add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)</span><span class="sxs-lookup"><span data-stu-id="a5838-116">For information on setting visibility information on the group, column or row, see [Add an Expand or Collapse Action to an Item &#40;Report Builder and SSRS&#41;](add-an-expand-or-collapse-action-to-an-item-report-builder-and-ssrs.md)</span></span>  
  
 <span data-ttu-id="a5838-117">如需隱藏報表項目的詳細資訊，請參閱[隱藏項目 &#40;報表產生器及 SSRS&#41;](../report-builder/hide-an-item-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a5838-117">For more information about hiding report items, see [Hide an Item &#40;Report Builder and SSRS&#41;](../report-builder/hide-an-item-report-builder-and-ssrs.md).</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="comparing-drilldown-and-drillthrough-reports"></a><span data-ttu-id="a5838-118">比較向下鑽研和鑽研報表</span><span class="sxs-lookup"><span data-stu-id="a5838-118">Comparing Drilldown and Drillthrough Reports</span></span>  
 <span data-ttu-id="a5838-119">在向下鑽研報表中，使用者可按一下加號或減號按鈕來展開或摺疊報表區段，以就地顯示詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a5838-119">In a drilldown report, a user clicks a plus or minus button to expand or collapse a section of a report to show detail data in place.</span></span> <span data-ttu-id="a5838-120">在鑽研報表中，使用者則會按一下摘要值的連結，這會開啟相關的個別報表來顯示詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a5838-120">In a drillthrough report, the user clicks a link for a summary value, and this opens a separate, related report to show detail data.</span></span> <span data-ttu-id="a5838-121">只有在詳細資料報表執行時，才會擷取詳細資料。</span><span class="sxs-lookup"><span data-stu-id="a5838-121">The detail data is only retrieved when the detail report runs.</span></span> <span data-ttu-id="a5838-122">鑽研報表需要的資源通常比向下鑽研報表更少。</span><span class="sxs-lookup"><span data-stu-id="a5838-122">Drillthrough reports typically require fewer resources than drilldown reports.</span></span> <span data-ttu-id="a5838-123">如需詳細資訊，請參閱 [鑽研、向下鑽研、子報表和巢狀資料區 &#40;報表產生器及 SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md)。</span><span class="sxs-lookup"><span data-stu-id="a5838-123">For more information, see [Drillthrough, Drilldown, Subreports, and Nested Data Regions &#40;Report Builder and SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md).</span></span>  
  
## <a name="rendering-extension-support-for-hidden-report-items"></a><span data-ttu-id="a5838-124">隱藏報表項目的轉譯延伸模組支援</span><span class="sxs-lookup"><span data-stu-id="a5838-124">Rendering Extension Support for Hidden Report Items</span></span>  
 <span data-ttu-id="a5838-125">只有支援使用者互動性的轉譯延伸模組 (例如在報表產生器和報表管理員中執行報表時使用的 HTML 轉譯延伸模組)，才支援報表項目的顯示與隱藏切換。</span><span class="sxs-lookup"><span data-stu-id="a5838-125">The show-and-hide toggle on report items is supported only by rendering extensions that support user interactivity, such as the HTML rendering extension that is used when you run a report in Report Builder and in Report Manager, for example.</span></span> <span data-ttu-id="a5838-126">其他轉譯延伸模組會顯示隱藏的項目。</span><span class="sxs-lookup"><span data-stu-id="a5838-126">Other rendering extensions display hidden items.</span></span> <span data-ttu-id="a5838-127">下列清單描述包含條件式可見性之報表項目的支援：</span><span class="sxs-lookup"><span data-stu-id="a5838-127">The following list describes support for report items with conditional visibility:</span></span>  
  
-   <span data-ttu-id="a5838-128">在 HTML 中，如果項目是隱藏的，則在 HTML 原始檔中看不到它們。</span><span class="sxs-lookup"><span data-stu-id="a5838-128">In HTML, if items are hidden, they are not visible in the HTML source.</span></span>  
  
-   <span data-ttu-id="a5838-129">XML 轉譯延伸模組會顯示所有的報表項目 (不論它們是否為隱藏)。</span><span class="sxs-lookup"><span data-stu-id="a5838-129">The XML rendering extension displays all report items, regardless of whether they are hidden.</span></span>  
  
-   <span data-ttu-id="a5838-130">Excel 轉譯延伸模組會顯示並展開資料表、矩陣或清單的隱藏資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="a5838-130">The Excel rendering extension displays and expands hidden rows and columns for a table, matrix, or list.</span></span> <span data-ttu-id="a5838-131">所有的資料列和資料行都是可見的。</span><span class="sxs-lookup"><span data-stu-id="a5838-131">All rows and columns are visible.</span></span>  
  
 <span data-ttu-id="a5838-132">如需詳細資訊，請參閱[轉譯行為 &#40;報表產生器及 SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="a5838-132">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5838-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5838-133">See Also</span></span>  
 <span data-ttu-id="a5838-134">[鑽研、向下鑽研、子報表和巢狀資料區 &#40;報表產生器及 SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md) </span><span class="sxs-lookup"><span data-stu-id="a5838-134">[Drillthrough, Drilldown, Subreports, and Nested Data Regions &#40;Report Builder and SSRS&#41;](drillthrough-drilldown-subreports-and-nested-data-regions.md) </span></span>  
 <span data-ttu-id="a5838-135">[互動式排序、文件引導模式及連結 &#40;報表產生器及 SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="a5838-135">[Interactive Sort, Document Maps, and Links &#40;Report Builder and SSRS&#41;](interactive-sort-document-maps-and-links-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="a5838-136">運算式範例 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="a5838-136">Expression Examples &#40;Report Builder and SSRS&#41;</span></span>](expression-examples-report-builder-and-ssrs.md)  
  
  
