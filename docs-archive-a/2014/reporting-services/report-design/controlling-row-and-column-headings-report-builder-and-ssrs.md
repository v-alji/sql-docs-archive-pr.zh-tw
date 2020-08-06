---
title: 控制資料列和資料行標題 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 4be6e836-158e-4bc9-8870-7f394d7c7e11
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 19d0deb86bfeea70c92ffb17ec79966788102748
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595767"
---
# <a name="controlling-row-and-column-headings-report-builder-and-ssrs"></a><span data-ttu-id="9544a-102">控制資料列和資料行標題 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="9544a-102">Controlling Row and Column Headings (Report Builder and SSRS)</span></span>
  <span data-ttu-id="9544a-103">資料表、矩陣或清單資料區可以用垂直或水平方式跨越多個頁面。</span><span class="sxs-lookup"><span data-stu-id="9544a-103">A table, matrix, or list data region can span multiple pages horizontally or vertically.</span></span> <span data-ttu-id="9544a-104">您可以指定是否要在每一頁重複資料列標題或資料行標題。</span><span class="sxs-lookup"><span data-stu-id="9544a-104">You can specify whether to repeat row or column headings on each page.</span></span> <span data-ttu-id="9544a-105">在報表管理員或報表預覽等互動式轉譯器中，您也可以指定是否要凍結資料列或資料行標題，以便在橫向捲動或向下捲動報表時讓它們保持可見狀態。</span><span class="sxs-lookup"><span data-stu-id="9544a-105">In an interactive renderer such as Report Manager or report preview, you can also specify whether to freeze row or column headings to keep them in view when you scroll across or down a report.</span></span> <span data-ttu-id="9544a-106">在資料表或矩陣中，第一個資料列通常包含標示每個資料行中之資料的資料行標題；第一個資料行通常包含標示每個資料列中之資料的資料列標題。</span><span class="sxs-lookup"><span data-stu-id="9544a-106">In a table or matrix, the first row usually contains column headings that label data in each column; the first column usually contains row headings that label the data in each row.</span></span> <span data-ttu-id="9544a-107">對於巢狀群組，您可能會想要重複包含群組標籤的初始資料列和資料行標題集合。</span><span class="sxs-lookup"><span data-stu-id="9544a-107">For nested groups, you might want to repeat the initial set of row and column headings that contain group labels.</span></span> <span data-ttu-id="9544a-108">根據預設，清單資料區域並不包含標題。</span><span class="sxs-lookup"><span data-stu-id="9544a-108">By default, a list data region does not include headings.</span></span>

 <span data-ttu-id="9544a-109">您控制標題為重複還是要凍結的方式視下列事項而定：</span><span class="sxs-lookup"><span data-stu-id="9544a-109">How you control whether headings repeat or freeze depends on the following:</span></span>

-   <span data-ttu-id="9544a-110">針對在每個頁面頂端重複的資料行標題：</span><span class="sxs-lookup"><span data-stu-id="9544a-110">For column headings that repeat at the top of each page:</span></span>

    -   <span data-ttu-id="9544a-111">資料表或矩陣是否擁有水平展開的資料行群組區域。</span><span class="sxs-lookup"><span data-stu-id="9544a-111">Whether the table or matrix has a column group area that expands horizontally.</span></span>

    -   <span data-ttu-id="9544a-112">您是否要以一整個單位的方式控制與資料行群組相關聯的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="9544a-112">Whether you want to control all rows that are associated with column groups as a unit.</span></span>

-   <span data-ttu-id="9544a-113">針對沿著每個頁面側邊重複的資料列標題：</span><span class="sxs-lookup"><span data-stu-id="9544a-113">For row headings that repeat along the side of each page:</span></span>

    -   <span data-ttu-id="9544a-114">資料表或矩陣是否擁有垂直展開的資料列群組區域。</span><span class="sxs-lookup"><span data-stu-id="9544a-114">Whether the table or matrix has a row group area that expands vertically.</span></span> <span data-ttu-id="9544a-115">只有包含資料列群組標頭的資料列群組支援使用資料列標題。</span><span class="sxs-lookup"><span data-stu-id="9544a-115">Row headings are supported only for row groups with a row group header.</span></span>

> [!NOTE]
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]

## <a name="understanding-rows-and-columns-in-a-tablix-data-region"></a><span data-ttu-id="9544a-116">了解 Tablix 資料區中的資料列及資料行</span><span class="sxs-lookup"><span data-stu-id="9544a-116">Understanding Rows and Columns in a Tablix Data Region</span></span>
 <span data-ttu-id="9544a-117">資料表或矩陣是基礎 Tablix 資料區的範本。</span><span class="sxs-lookup"><span data-stu-id="9544a-117">A table or matrix is a template for the underlying tablix data region.</span></span> <span data-ttu-id="9544a-118">Tablix 資料區具有四個可能的區域：控制向下展開報表之資料列的資料列群組區域、控制橫向展開報表之資料行的資料行群組區域、顯示資料的主體，以及邊角。</span><span class="sxs-lookup"><span data-stu-id="9544a-118">A tablix data region has four possible areas: the row group area that controls rows that expand down a report, the column group area that controls columns that expand across a report, the body that displays data, and the corner.</span></span> <span data-ttu-id="9544a-119">若要了解在哪裡設定屬性以控制重複或凍結標頭，了解 Tablix 資料區的兩種表示法相當有協助：</span><span class="sxs-lookup"><span data-stu-id="9544a-119">To understand where to set properties to control repeating or freezing headers, it helps to understand that there are two representations for a tablix data region:</span></span>

-   <span data-ttu-id="9544a-120">**在報表定義中** ：在 Tablix 資料區定義中的每個資料列或資料行都是特定資料列或資料行群組的一個 Tablix 成員。</span><span class="sxs-lookup"><span data-stu-id="9544a-120">**In the report definition** Each row or column in a tablix data region definition is a tablix member of a specific row or column group.</span></span> <span data-ttu-id="9544a-121">Tablix 成員是靜態或動態的。</span><span class="sxs-lookup"><span data-stu-id="9544a-121">A tablix member is static or dynamic.</span></span> <span data-ttu-id="9544a-122">靜態 Tablix 成員都包含標籤或小計，而且會針對每個群組重複一次。</span><span class="sxs-lookup"><span data-stu-id="9544a-122">A static tablix member contains labels or subtotals and repeats once per group.</span></span> <span data-ttu-id="9544a-123">動態 Tablix 成員包含群組值，而且會針對群組的每個唯一值重複一次，也稱為群組執行個體。</span><span class="sxs-lookup"><span data-stu-id="9544a-123">A dynamic tablix member contains group values and repeats once per unique value of a group, also known as a group instance.</span></span>

-   <span data-ttu-id="9544a-124">**在設計介面上** ：在設計介面上，虛線將 Tablix 資料區分為四個區域。</span><span class="sxs-lookup"><span data-stu-id="9544a-124">**On the design surface** On the design surface, dotted lines divide a tablix data region into the four areas.</span></span> <span data-ttu-id="9544a-125">Tablix 資料區中的每個資料格都組織成資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="9544a-125">Each cell in a tablix data region area is organized into rows and columns.</span></span> <span data-ttu-id="9544a-126">資料列和資料行與群組 (包括詳細資料群組) 相關聯。</span><span class="sxs-lookup"><span data-stu-id="9544a-126">Rows and columns are associated with groups, including the details group.</span></span> <span data-ttu-id="9544a-127">若是選取的 Tablix 資料區，資料列和資料行控點與反白橫條表示群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="9544a-127">For a selected tablix data region, row and column handles and highlight bars indicate group membership.</span></span> <span data-ttu-id="9544a-128">資料列群組或資料行群組區域中的資料格代表 Tablix 成員的群組標頭。</span><span class="sxs-lookup"><span data-stu-id="9544a-128">Cells in the row group or column group area represent group headers for tablix members.</span></span> <span data-ttu-id="9544a-129">單一資料列或資料行可以與多個群組產生關聯。</span><span class="sxs-lookup"><span data-stu-id="9544a-129">A single row or column can be associated with multiple groups.</span></span>

     <span data-ttu-id="9544a-130">如需詳細資訊，請參閱 [Tablix 資料區 &#40;報表產生器及 SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) 和 [Tablix 資料區資料格、資料列及資料行 &#40;報表產生器&#41; 及 SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9544a-130">For more information, see [Tablix Data Region &#40;Report Builder and SSRS&#41;](../tablix-data-region-report-builder-and-ssrs.md) and [Tablix Data Region Cells, Rows, and Columns &#40;Report Builder&#41; and SSRS](tablix-data-region-cells-rows-and-columns-report-builder-and-ssrs.md).</span></span>

 <span data-ttu-id="9544a-131">針對包含資料列群組或資料行群組區域的 Tablix 資料區，請設定 Tablix 資料區上的屬性以控制相關聯的資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="9544a-131">For tablix data regions with row group or column group areas, control the associated rows and columns by setting properties on tablix data region.</span></span> <span data-ttu-id="9544a-132">針對其他所有案例，在 [屬性] 窗格中設定所選 Tablix 成員的屬性，藉以控制資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="9544a-132">For all other cases, control the rows and columns by setting properties in the Properties pane for the selected tablix member.</span></span> <span data-ttu-id="9544a-133">如需逐步指示，請參閱[在多個頁面上顯示資料列和資料行標頭 &#40;報表產生器及 SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) 和[在報表中捲動時將標頭保持可見 &#40;報表產生器及 SSRS&#41;](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9544a-133">For step-by-step instructions, see [Display Row and Column Headers on Multiple Pages &#40;Report Builder and SSRS&#41;](display-row-and-column-headers-on-multiple-pages-report-builder-and-ssrs.md) and [Keep Headers Visible When Scrolling Through a Report &#40;Report Builder and SSRS&#41;](keep-headers-visible-when-scrolling-through-a-report-report-builder-and-ssrs.md).</span></span>

##  <a name="examples"></a><a name="Top"></a> <span data-ttu-id="9544a-134">範例</span><span class="sxs-lookup"><span data-stu-id="9544a-134">Examples</span></span>
 <span data-ttu-id="9544a-135">Tablix 資料區最常見的範例為用於矩陣、不含群組的資料表、包含資料列群組和資料列群組標頭的資料表，以及包含資料列群組但不含資料列群組標頭的資料表。</span><span class="sxs-lookup"><span data-stu-id="9544a-135">The most common examples of tablix data regions are for a matrix, a table with no groups, and a table with a row group and a row group header, and a table with a row group but no row group header.</span></span> <span data-ttu-id="9544a-136">若要控制重複或凍結標頭的方式，您必須判斷您要控制的資料列或資料行是與資料列群組區域中的群組標頭相關聯，還是與資料行群組區域中的群組標頭相關聯。</span><span class="sxs-lookup"><span data-stu-id="9544a-136">To control how to repeat or freeze headers, you must determine if the rows or columns that you want to control are associated with a group header in the row groups or column groups area.</span></span>

 <span data-ttu-id="9544a-137">下列章節提供用於 Tablix 資料區之一般配置的範例：</span><span class="sxs-lookup"><span data-stu-id="9544a-137">The following sections provide examples for common layouts for a tablix data region:</span></span>

-   [<span data-ttu-id="9544a-138">Matrix</span><span class="sxs-lookup"><span data-stu-id="9544a-138">Matrix</span></span>](#Matrix)

-   [<span data-ttu-id="9544a-139">不含群組的資料表</span><span class="sxs-lookup"><span data-stu-id="9544a-139">Table with no groups</span></span>](#TableNoGroups)

-   [<span data-ttu-id="9544a-140">包含資料列群組和資料列群組區域的資料表</span><span class="sxs-lookup"><span data-stu-id="9544a-140">Table with row groups and row group area</span></span>](#TableRowGroupsGroupHeader)

-   [<span data-ttu-id="9544a-141">包含資料列群組但不含資料列群組區域的資料表</span><span class="sxs-lookup"><span data-stu-id="9544a-141">Table with row groups but no row group area</span></span>](#TableRowGroupsNoGroupHeader)

###  <a name="matrix"></a><a name="Matrix"></a><span data-ttu-id="9544a-142">核准</span><span class="sxs-lookup"><span data-stu-id="9544a-142">Matrix</span></span>
 <span data-ttu-id="9544a-143">根據預設，一個簡單的矩陣有一個資料列群組和一個資料行群組。</span><span class="sxs-lookup"><span data-stu-id="9544a-143">By default, a simple matrix has one row group and one column group.</span></span> <span data-ttu-id="9544a-144">下圖顯示包含以 Category 為基礎之資料列群組，以及以 Geography 為基礎之資料行群組的矩陣：</span><span class="sxs-lookup"><span data-stu-id="9544a-144">The following figure shows a matrix with a row group that is based on Category and a column group that is based on Geography:</span></span>

 <span data-ttu-id="9544a-145">![含目錄資料列和地理位置資料行群組的矩陣](../media/rs-basicmatrixdesign.gif "含目錄資料列和地理位置資料行群組的矩陣")</span><span class="sxs-lookup"><span data-stu-id="9544a-145">![Matrix, Category row and Geography column group](../media/rs-basicmatrixdesign.gif "Matrix, Category row and Geography column group")</span></span>

 <span data-ttu-id="9544a-146">虛線表示四個 Tablix 區域。</span><span class="sxs-lookup"><span data-stu-id="9544a-146">The dotted lines show the four tablix areas.</span></span> <span data-ttu-id="9544a-147">資料列群組區域所擁有的資料列群組標頭可控制第一個資料行中的類別標籤。</span><span class="sxs-lookup"><span data-stu-id="9544a-147">The row group area has a row group header that controls the category labels in the first column.</span></span> <span data-ttu-id="9544a-148">同樣地，資料行群組區域所擁有的資料行群組標頭可控制第一個資料列中的地理位置標籤。</span><span class="sxs-lookup"><span data-stu-id="9544a-148">Similarly, the column group area has a column group header that controls the geography labels in the first row.</span></span> <span data-ttu-id="9544a-149">在預覽中，由於矩陣會橫跨頁面展開，第一個資料列會顯示資料行標題，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="9544a-149">In preview, as the matrix expands across the page, the first row displays the column headings, as shown in the following figure:</span></span>

 <span data-ttu-id="9544a-150">![將群組展開的轉譯矩陣預覽](../media/rs-basicmatrixpreview.gif "將群組展開的轉譯矩陣預覽")</span><span class="sxs-lookup"><span data-stu-id="9544a-150">![Preview for rendered matrix with expanded groups](../media/rs-basicmatrixpreview.gif "Preview for rendered matrix with expanded groups")</span></span>

 <span data-ttu-id="9544a-151">若要在第一個資料列中重複或凍結資料行標題，請在 Tablix 資料區上設定資料行標頭的屬性。</span><span class="sxs-lookup"><span data-stu-id="9544a-151">To repeat or freeze column headings in the first row, set properties for column headers on the tablix data region.</span></span> <span data-ttu-id="9544a-152">巢狀資料行群組的資料行標頭會自動加入。</span><span class="sxs-lookup"><span data-stu-id="9544a-152">Column headers for nested column groups are automatically included.</span></span>

 <span data-ttu-id="9544a-153">若要在第一個資料行中重複或凍結資料列標題，請在 Tablix 資料區上設定資料列標頭的屬性。</span><span class="sxs-lookup"><span data-stu-id="9544a-153">To repeat or freeze row headings in the first column, set properties for row headers on the tablix data region.</span></span> <span data-ttu-id="9544a-154">巢狀資料列群組的資料列標頭會自動加入。</span><span class="sxs-lookup"><span data-stu-id="9544a-154">Row headers for nested row groups are automatically included.</span></span>

 [<span data-ttu-id="9544a-155">回頁首</span><span class="sxs-lookup"><span data-stu-id="9544a-155">Return to top</span></span>](#Top)

###  <a name="table-with-no-row-groups"></a><a name="TableNoGroups"></a><span data-ttu-id="9544a-156">沒有資料列群組的資料表</span><span class="sxs-lookup"><span data-stu-id="9544a-156">Table with no row groups</span></span>
 <span data-ttu-id="9544a-157">根據預設，不含群組的簡單資料表包含詳細資料群組。</span><span class="sxs-lookup"><span data-stu-id="9544a-157">By default, a simple table with no groups does include the details group.</span></span> <span data-ttu-id="9544a-158">下圖的資料表顯示類別、訂單號碼，以及銷售資料：</span><span class="sxs-lookup"><span data-stu-id="9544a-158">The following figure shows a table that displays category, order number, and sales data:</span></span>

 <span data-ttu-id="9544a-159">![含一個靜態及動態資料列的資料表設計](../media/rs-tableheaderstaticdesign.gif "含一個靜態及動態資料列的資料表設計")</span><span class="sxs-lookup"><span data-stu-id="9544a-159">![Design, table with one static, one dynamic row](../media/rs-tableheaderstaticdesign.gif "Design, table with one static, one dynamic row")</span></span>

 <span data-ttu-id="9544a-160">資料表僅包含 Tablix 主體區域，因此沒有虛線。</span><span class="sxs-lookup"><span data-stu-id="9544a-160">There are no dotted lines because the table consists only of the tablix body area.</span></span> <span data-ttu-id="9544a-161">第一個資料列顯示資料行標頭，並代表與群組沒有關聯的靜態 Tablix 成員。</span><span class="sxs-lookup"><span data-stu-id="9544a-161">The first row displays column headers, and represents a static tablix member that is not associated with a group.</span></span> <span data-ttu-id="9544a-162">第二個資料列顯示詳細資料，並代表與詳細資料群組相關聯的動態 Tablix 成員。</span><span class="sxs-lookup"><span data-stu-id="9544a-162">The second row displays detail data, and represents a dynamic tablix member that is associated with the details group.</span></span> <span data-ttu-id="9544a-163">下圖顯示預覽中的資料表：</span><span class="sxs-lookup"><span data-stu-id="9544a-163">The following figure shows the table in preview:</span></span>

 <span data-ttu-id="9544a-164">![含一個靜態及動態資料列的資料表預覽](../media/rs-tableheaderstaticpreview.gif "含一個靜態及動態資料列的資料表預覽")</span><span class="sxs-lookup"><span data-stu-id="9544a-164">![Preview, table with one static, one dynamic row](../media/rs-tableheaderstaticpreview.gif "Preview, table with one static, one dynamic row")</span></span>

 <span data-ttu-id="9544a-165">若要重複或凍結資料行標題，請在 Tablix 成員上設定屬於 Tablix 資料區定義之靜態資料列的屬性。</span><span class="sxs-lookup"><span data-stu-id="9544a-165">To repeat or freeze column headings, set properties on the tablix member for static row that is part of the tablix data region definition.</span></span> <span data-ttu-id="9544a-166">若要選取靜態資料列，您必須使用 [群組] 窗格的 [進階] 模式。</span><span class="sxs-lookup"><span data-stu-id="9544a-166">To select the static row, you must use the Advanced mode of the Grouping pane.</span></span> <span data-ttu-id="9544a-167">下圖顯示 [資料列群組] 窗格：</span><span class="sxs-lookup"><span data-stu-id="9544a-167">The following figure shows the Row Groups pane:</span></span>

 <span data-ttu-id="9544a-168">![資料列群組；具有一個靜態及動態資料列的資料表](../media/rs-tableheaderstaticgroupingpanedefault.gif "資料列群組；具有一個靜態及動態資料列的資料表")</span><span class="sxs-lookup"><span data-stu-id="9544a-168">![Row Groups, table with 1 static, 1 dynamic row](../media/rs-tableheaderstaticgroupingpanedefault.gif "Row Groups, table with 1 static, 1 dynamic row")</span></span>

 <span data-ttu-id="9544a-169">在 [進階] 模式中，下圖顯示資料表中資料列群組的靜態和動態 Tablix 成員：</span><span class="sxs-lookup"><span data-stu-id="9544a-169">In Advanced mode, the following figure shows the static and dynamic tablix members for the row groups in the table:</span></span>

 <span data-ttu-id="9544a-170">![資料列群組；預設資料表的進階模式](../media/rs-tableheaderstaticgroupingpaneadvanced.gif "資料列群組；預設資料表的進階模式")</span><span class="sxs-lookup"><span data-stu-id="9544a-170">![Row Groups, Advanced for default table](../media/rs-tableheaderstaticgroupingpaneadvanced.gif "Row Groups, Advanced for default table")</span></span>

 <span data-ttu-id="9544a-171">若要重複或凍結 Tablix 成員的資料行標題，請選取標示的靜態資料列 (**Static**)。</span><span class="sxs-lookup"><span data-stu-id="9544a-171">To repeat or freeze column headings for the tablix member, select the static row that is labeled (**Static**).</span></span> <span data-ttu-id="9544a-172">[屬性] 窗格會顯示所選 Tablix 成員的屬性。</span><span class="sxs-lookup"><span data-stu-id="9544a-172">The properties pane displays the properties for the selected tablix member.</span></span> <span data-ttu-id="9544a-173">您可以設定此 Tablix 成員的屬性，藉以控制第一個資料列如何在檢視中重複，或保留在檢視中。</span><span class="sxs-lookup"><span data-stu-id="9544a-173">By setting properties for this tablix member, you can control how the first row repeats or stays in view.</span></span>

 [<span data-ttu-id="9544a-174">回頁首</span><span class="sxs-lookup"><span data-stu-id="9544a-174">Return to top</span></span>](#Top)

###  <a name="table-with-row-groups-and-a-row-group-area"></a><a name="TableRowGroupsGroupHeader"></a><span data-ttu-id="9544a-175">包含資料列群組和資料列群組區域的資料表</span><span class="sxs-lookup"><span data-stu-id="9544a-175">Table with row groups and a row group area</span></span>
 <span data-ttu-id="9544a-176">如果您將資料列群組加入到簡單的資料表中，資料列群組區域就會加入到設計介面上的資料表中。</span><span class="sxs-lookup"><span data-stu-id="9544a-176">If you add a row group to a simple table, a row group area is added to the table on the design surface.</span></span> <span data-ttu-id="9544a-177">下圖顯示包含以 Category 為基礎之資料列群組的資料表：</span><span class="sxs-lookup"><span data-stu-id="9544a-177">The following figure shows a table with a row group that is based on Category:</span></span>

 <span data-ttu-id="9544a-178">![含一個資料列群組及詳細資料的資料表設計](../media/rs-tableheaderdynamicwithgroupheadercelldesign.gif "含一個資料列群組及詳細資料的資料表設計")</span><span class="sxs-lookup"><span data-stu-id="9544a-178">![Design, table with one row group and details](../media/rs-tableheaderdynamicwithgroupheadercelldesign.gif "Design, table with one row group and details")</span></span>

 <span data-ttu-id="9544a-179">虛線表示 Tablix 資料列群組區域以及 Tablix 主體區域。</span><span class="sxs-lookup"><span data-stu-id="9544a-179">The dotted lines show the tablix row groups area and the tablix body area.</span></span> <span data-ttu-id="9544a-180">資料列群組區域擁有資料列群組標頭，但是沒有資料行群組標頭。</span><span class="sxs-lookup"><span data-stu-id="9544a-180">The row group area has a row group header but no column group header.</span></span> <span data-ttu-id="9544a-181">下圖顯示預覽中的這個資料表：</span><span class="sxs-lookup"><span data-stu-id="9544a-181">The following figure shows this table in preview:</span></span>

 <span data-ttu-id="9544a-182">![含一個資料列群組及詳細資料的資料表預覽](../media/rs-tableheaderdynamicwithgroupheadercellpreview.gif "含一個資料列群組及詳細資料的資料表預覽")</span><span class="sxs-lookup"><span data-stu-id="9544a-182">![Preview, table with one row group and details](../media/rs-tableheaderdynamicwithgroupheadercellpreview.gif "Preview, table with one row group and details")</span></span>

 <span data-ttu-id="9544a-183">若要重複或凍結資料行標題，請使用與上述範例相同的方法。</span><span class="sxs-lookup"><span data-stu-id="9544a-183">To repeat or freeze column headings, use the same approach as the previous example.</span></span> <span data-ttu-id="9544a-184">下圖顯示 [資料列群組] 窗格的預設檢視：</span><span class="sxs-lookup"><span data-stu-id="9544a-184">The following figure shows the default view of the Row Groups pane:</span></span>

 <span data-ttu-id="9544a-185">![資料列群組；動態成員的預設模式](../media/rs-tableheaderdynamicgroupingpanedefault.gif "資料列群組；動態成員的預設模式")</span><span class="sxs-lookup"><span data-stu-id="9544a-185">![Row Groups, Default with dynamic members](../media/rs-tableheaderdynamicgroupingpanedefault.gif "Row Groups, Default with dynamic members")</span></span>

 <span data-ttu-id="9544a-186">使用 [資料列群組] 窗格的 **[進階]** 模式顯示 Tablix 成員，如下圖所示：</span><span class="sxs-lookup"><span data-stu-id="9544a-186">Use the **Advanced** mode of the Row Groups pane to display the tablix members, as shown in the following figure:</span></span>

 <span data-ttu-id="9544a-187">![資料列群組；靜態成員的進階模式](../media/rs-tableheaderdynamicwithgroupheadercelladvanced.gif "資料列群組；靜態成員的進階模式")</span><span class="sxs-lookup"><span data-stu-id="9544a-187">![Row Groups, Advanced mode with static members](../media/rs-tableheaderdynamicwithgroupheadercelladvanced.gif "Row Groups, Advanced mode with static members")</span></span>

 <span data-ttu-id="9544a-188">列出的 Tablix 成員： **Static**、(**Static**)、Category 和 (**Details**)。</span><span class="sxs-lookup"><span data-stu-id="9544a-188">For tablix members are listed: **Static**, (**Static**), Category, and (**Details**).</span></span> <span data-ttu-id="9544a-189">包含括號 () 的 Tablix 成員表示沒有對應的群組標頭。</span><span class="sxs-lookup"><span data-stu-id="9544a-189">A tablix member that includes parentheses () indicates that there is no corresponding group header.</span></span> <span data-ttu-id="9544a-190">若要重複或凍結資料行標題，請選取最上方的 Static Tablix 成員，然後在 [屬性] 窗格中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="9544a-190">To repeat or freeze column headings, select the top Static tablix member, and set properties in the Properties pane.</span></span>

 [<span data-ttu-id="9544a-191">回頁首</span><span class="sxs-lookup"><span data-stu-id="9544a-191">Return to top</span></span>](#Top)

###  <a name="table-with-row-groups-and-no-row-group-area"></a><a name="TableRowGroupsNoGroupHeader"></a><span data-ttu-id="9544a-192">包含資料列群組和沒有資料列群組區域的資料表</span><span class="sxs-lookup"><span data-stu-id="9544a-192">Table with row groups and no row group area</span></span>
 <span data-ttu-id="9544a-193">資料表可以使用數種方式包含資料列群組，但不含資料列群組區域。</span><span class="sxs-lookup"><span data-stu-id="9544a-193">A table can have row groups but no row groups area in several ways.</span></span> <span data-ttu-id="9544a-194">兩個可能的方式包括：</span><span class="sxs-lookup"><span data-stu-id="9544a-194">Two possible ways for this to happen include:</span></span>

-   <span data-ttu-id="9544a-195">從包含資料列群組和資料列群組區域的資料表開始，然後刪除資料列群組區域的資料行。</span><span class="sxs-lookup"><span data-stu-id="9544a-195">Start with a table with row groups and a row group area and delete the columns for the row group area.</span></span> <span data-ttu-id="9544a-196">僅刪除資料行，但不刪除群組。</span><span class="sxs-lookup"><span data-stu-id="9544a-196">Delete the columns only and not the groups.</span></span> <span data-ttu-id="9544a-197">例如，您可能想要將資料表格式控制為一個簡單的方格。</span><span class="sxs-lookup"><span data-stu-id="9544a-197">For example, you might want to control the table format to be a simple grid.</span></span>

-   <span data-ttu-id="9544a-198">升級針對上一個 RDL 版本所建立的報表，然後再導入 Tablix 資料區。</span><span class="sxs-lookup"><span data-stu-id="9544a-198">Upgrade a report that was created for a previous RDL version, before tablix data regions were introduced.</span></span>

 <span data-ttu-id="9544a-199">下圖顯示在設計介面上包含資料列群組，但不含資料列群組區域的資料表：</span><span class="sxs-lookup"><span data-stu-id="9544a-199">The following figure shows a table with a row group but no row group area on the design surface:</span></span>

 <span data-ttu-id="9544a-200">![含資料列群組但沒有群組標頭的資料表設計](../media/rs-tableheaderdynamicwithnogroupheadercelldesign.gif "含資料列群組但沒有群組標頭的資料表設計")</span><span class="sxs-lookup"><span data-stu-id="9544a-200">![Design, table has row group but no group header](../media/rs-tableheaderdynamicwithnogroupheadercelldesign.gif "Design, table has row group but no group header")</span></span>

 <span data-ttu-id="9544a-201">資料表有三個資料列。</span><span class="sxs-lookup"><span data-stu-id="9544a-201">The table has three rows.</span></span> <span data-ttu-id="9544a-202">第一個資料列包含資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="9544a-202">The first row contains column headers.</span></span> <span data-ttu-id="9544a-203">第二個資料列包含群組值和小計。</span><span class="sxs-lookup"><span data-stu-id="9544a-203">The second row contains the group value and subtotals.</span></span> <span data-ttu-id="9544a-204">第三個資料列包含詳細資料。</span><span class="sxs-lookup"><span data-stu-id="9544a-204">The third row contains the detail data.</span></span> <span data-ttu-id="9544a-205">因為只有一個 Tablix 主體區域，因此沒有虛線。</span><span class="sxs-lookup"><span data-stu-id="9544a-205">There are no dotted lines because there is only a tablix body area.</span></span> <span data-ttu-id="9544a-206">下圖顯示預覽中的這個資料表：</span><span class="sxs-lookup"><span data-stu-id="9544a-206">The following figure shows this table in preview:</span></span>

 <span data-ttu-id="9544a-207">![含資料列群組但沒有群組標頭的資料表預覽](../media/rs-tableheaderdynamicwithnogroupheadercellpreview.gif "含資料列群組但沒有群組標頭的資料表預覽")</span><span class="sxs-lookup"><span data-stu-id="9544a-207">![Preview, table has row group but no group header](../media/rs-tableheaderdynamicwithnogroupheadercellpreview.gif "Preview, table has row group but no group header")</span></span>

 <span data-ttu-id="9544a-208">若要控制資料列如何在檢視中重複，或保留在檢視中，您必須在 Tablix 成員上設定每個資料列的屬性。</span><span class="sxs-lookup"><span data-stu-id="9544a-208">To control how the rows repeat or stay in view, you must set properties on the tablix member for each row.</span></span> <span data-ttu-id="9544a-209">在預設模式下，這個範例與包含資料列群組和群組標頭之資料表的上一個範例沒有什麼不同。</span><span class="sxs-lookup"><span data-stu-id="9544a-209">In default mode, there is no difference between this example and the previous example for a table with a row group and a group header.</span></span> <span data-ttu-id="9544a-210">下圖顯示此資料表在預設模式下的 [群組] 窗格：</span><span class="sxs-lookup"><span data-stu-id="9544a-210">The following figure shows the Grouping pane in default mode for this table:</span></span>

 <span data-ttu-id="9544a-211">![資料列群組；動態成員的預設模式](../media/rs-tableheaderdynamicgroupingpanedefault.gif "資料列群組；動態成員的預設模式")</span><span class="sxs-lookup"><span data-stu-id="9544a-211">![Row Groups, Default with dynamic members](../media/rs-tableheaderdynamicgroupingpanedefault.gif "Row Groups, Default with dynamic members")</span></span>

 <span data-ttu-id="9544a-212">不過，在進階模式下，此配置結構會顯示一組不同的 Tablix 成員。</span><span class="sxs-lookup"><span data-stu-id="9544a-212">However, in advanced mode, this layout structure shows a different set of tablix members.</span></span> <span data-ttu-id="9544a-213">下圖顯示此資料表在進階模式下的 [群組] 窗格：</span><span class="sxs-lookup"><span data-stu-id="9544a-213">The following figure shows the Grouping pane in advanced mode for this table:</span></span>

 <span data-ttu-id="9544a-214">![資料列群組；進階；無群組標頭。](../media/rs-tableheaderdynamicwithnogroupheadercelladvanced.gif "資料列群組；進階；無群組標頭。")</span><span class="sxs-lookup"><span data-stu-id="9544a-214">![Row Groups, Advanced, no group header.](../media/rs-tableheaderdynamicwithnogroupheadercelladvanced.gif "Row Groups, Advanced, no group header.")</span></span>

 <span data-ttu-id="9544a-215">在 [資料列群組] 窗格中，會列出下列 Tablix 成員： (**Static**)、(Category)、(**Static**) 和 (**Details**)。</span><span class="sxs-lookup"><span data-stu-id="9544a-215">In the Row Groups pane, the following tablix members are listed: (**Static**), (Category), (**Static**), and (**Details**).</span></span> <span data-ttu-id="9544a-216">若要重複或凍結資料行標題，請選取最上方的 (**Static**) Tablix 成員，然後在 [屬性] 窗格中設定屬性。</span><span class="sxs-lookup"><span data-stu-id="9544a-216">To repeat or freeze column headings, select the top (**Static**) tablix member, and set properties in the Properties pane.</span></span>

 [<span data-ttu-id="9544a-217">回頁首</span><span class="sxs-lookup"><span data-stu-id="9544a-217">Return to top</span></span>](#Top)

## <a name="renderer-support-for-repeating-or-freezing-headers"></a><span data-ttu-id="9544a-218">重複或凍結標頭的轉譯器支援</span><span class="sxs-lookup"><span data-stu-id="9544a-218">Renderer Support for Repeating or Freezing Headers</span></span>
 <span data-ttu-id="9544a-219">轉譯器對於重複或凍結標頭的支援不同。</span><span class="sxs-lookup"><span data-stu-id="9544a-219">Renderers vary in support for repeating or freezing headers.</span></span>

 <span data-ttu-id="9544a-220">使用實體頁面 (PDF、影像、列印) 的轉譯器支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="9544a-220">Renderers that use physical pages (PDF, Image, Print) support the following features:</span></span>

-   <span data-ttu-id="9544a-221">當 Tablix 資料區以水平方式橫向擴展到多個頁面時，重複資料列標頭。</span><span class="sxs-lookup"><span data-stu-id="9544a-221">Repeat row headers when a tablix data region expands horizontally across multiple pages.</span></span>

-   <span data-ttu-id="9544a-222">當 Tablix 資料區以垂直方式向下擴展到多個頁面時，重複資料行標頭。</span><span class="sxs-lookup"><span data-stu-id="9544a-222">Repeat column headers when a tablix data region expands vertically down multiple pages.</span></span>

 <span data-ttu-id="9544a-223">此外，使用軟分頁符號的轉譯器 (報表管理員、報表預覽，或報表檢視器控制項) 支援下列功能：</span><span class="sxs-lookup"><span data-stu-id="9544a-223">In addition, renderers that use soft page breaks (Report Manager, report preview, or the report viewer control) support the following features:</span></span>

-   <span data-ttu-id="9544a-224">當您以水平方式橫向捲動報表時，保持資料列標頭可見狀態。</span><span class="sxs-lookup"><span data-stu-id="9544a-224">Keep row headers in view when you scroll horizontally across a report.</span></span>

-   <span data-ttu-id="9544a-225">當您以垂直方式向下捲動報表時，保持資料行標頭可見狀態。</span><span class="sxs-lookup"><span data-stu-id="9544a-225">Keep column headers in view when you scroll vertically down a report.</span></span>

 <span data-ttu-id="9544a-226">如需詳細資訊，請參閱[轉譯行為 &#40;報表產生器及 SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="9544a-226">For more information, see [Rendering Behaviors &#40;Report Builder  and SSRS&#41;](rendering-behaviors-report-builder-and-ssrs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9544a-227">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9544a-227">See Also</span></span>
 <span data-ttu-id="9544a-228">[篩選、分組和排序資料 &#40;報表產生器和 ssrs&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) [清單 &#40;報表產生器和 ssrs&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) Reporting Services &#40;[和 ssrs 報表產生器](pagination-in-reporting-services-report-builder-and-ssrs.md)將[報表匯出&#41;&#40;和 ssrs](../report-builder/export-reports-report-builder-and-ssrs.md)報表產生器</span><span class="sxs-lookup"><span data-stu-id="9544a-228">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) [Lists &#40;Report Builder and SSRS&#41;](tables-matrices-and-lists-report-builder-and-ssrs.md) [Pagination in Reporting Services &#40;Report Builder  and SSRS&#41;](pagination-in-reporting-services-report-builder-and-ssrs.md) [Exporting Reports &#40;Report Builder and SSRS&#41;](../report-builder/export-reports-report-builder-and-ssrs.md)</span></span>


