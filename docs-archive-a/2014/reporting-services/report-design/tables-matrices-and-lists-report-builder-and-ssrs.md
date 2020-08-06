---
title: 資料表、矩陣和清單 (報表產生器及 SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.tablix.visibility.f1
- sql12.rtp.rptdesigner.groupproperties.advanced.f1
- "10045"
- sql12.rtp.rptdesigner.groupproperties.filters.f1
- "10039"
- "10104"
- sql12.rtp.rptdesigner.tablixgroup.f1
- sql12.rtp.rptdesigner.tablix.general.f1
- "10047"
- "10044"
- "10046"
- sql12.rtp.rptdesigner.groupproperties.visibility.f1
- "10101"
- sql12.rtp.rptdesigner.groupproperties.sort.f1
- sql12.rtp.rptdesigner.groupproperties.variables.f1
- sql12.rtp.rptdesigner.groupproperties.general.f1
- "10042"
- sql12.rtp.rptdesigner.tablix.sort.f1
- "10041"
- sql12.rtp.rptdesigner.groupproperties.pagebreaks.f1
- "10102"
- "10103"
- "10043"
- sql12.rtp.rptdesigner.tablix.filter.f1
ms.assetid: 9dcf3fc8-bf9c-4a14-a03d-e78254aa4098
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 03384009b0e51c081f0906ef0a768dafa180be7e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595676"
---
# <a name="tables-matrices-and-lists-report-builder-and-ssrs"></a><span data-ttu-id="1ea6c-102">資料表、矩陣和清單 (報表產生器及 SSRS)</span><span class="sxs-lookup"><span data-stu-id="1ea6c-102">Tables, Matrices, and Lists (Report Builder and SSRS)</span></span>
  <span data-ttu-id="1ea6c-103">資料表、矩陣和清單都是資料區，這些資料區會將報表資料顯示在分為資料列與資料行的資料格中。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-103">Tables, matrices, and lists are data regions that display report data in cells that are organized into rows and columns.</span></span> <span data-ttu-id="1ea6c-104">資料格通常包含文字資料 (例如文字、日期和數字)，但也可以包含量測計、圖表或報表項目 (例如影像)。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-104">The cells typically contain text data such as text, dates, and numbers but they can also contain gauges, charts, or report items such as images.</span></span> <span data-ttu-id="1ea6c-105">資料表、矩陣和清單經常統稱為 Tablix 資料區。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-105">Collectively, tables, matrices, and lists are frequently referred to as tablix data regions.</span></span>  
  
 <span data-ttu-id="1ea6c-106">資料表、矩陣和清單範本建立於 Tablix 資料區之上，是一個可以在資料格中顯示資料的彈性方格。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-106">The table, matrix, and list templates are built on the tablix data region, which is a flexible grid that can display data in cells.</span></span> <span data-ttu-id="1ea6c-107">在資料表和矩陣範本中，資料格會組織成資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-107">In the table and matrix templates, cells are organized into rows and columns.</span></span> <span data-ttu-id="1ea6c-108">範本是基礎之泛型 Tablix 資料區的變化，因此您可以結合範本格式顯示資料，並變更資料表、矩陣或清單，以便在開發報表時，加入其他資料區的功能。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-108">Because templates are variations of the underlying generic tablix data region, you can display can display data in combination of template formats and change the table, matrix, or list on to include the features of another data region as you develop your report.</span></span> <span data-ttu-id="1ea6c-109">例如，如果您加入一個資料表之後，發現該資料表不符合您的需要，您可以加入資料行群組，讓該資料表變成矩陣。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-109">For example, if you add a table and find it does not serve your needs, you can add column groups to make the table a matrix.</span></span>  
  
 <span data-ttu-id="1ea6c-110">資料表和矩陣資料區可以加入巢狀資料表、矩陣、清單、圖表和量測計，以顯示複雜的資料關聯性。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-110">The table and matrix data regions can display complex data relationships by including nested tables, matrices, lists, charts and gauges.</span></span> <span data-ttu-id="1ea6c-111">資料表和矩陣具有表格式配置，且其資料來自單一資料來源上建立的單一資料集。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-111">Tables and matrices have a tabular layout and their data comes from a single dataset, built on a single data source.</span></span> <span data-ttu-id="1ea6c-112">資料表和矩陣之間的主要差異在於資料表可以只包含資料列群組，而矩陣則包含資料列群組和資料行群組。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-112">The key difference between tables and matrices is that tables can include only row groups, where as matrices have row groups and column groups.</span></span>  
  
 <span data-ttu-id="1ea6c-113">清單則稍有不同。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-113">Lists are a little different.</span></span> <span data-ttu-id="1ea6c-114">它們支援自由形式的配置，而且可以包含多個對等的資料表或矩陣，每個都使用來自不同資料集的資料。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-114">They support a free-layout that and can include multiple peer tables or matrices, each using data from a different dataset.</span></span> <span data-ttu-id="1ea6c-115">清單也可以用於表單，例如發票。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-115">Lists can also be used for forms, such as invoices.</span></span>  
  
 <span data-ttu-id="1ea6c-116">下圖顯示包含資料表、矩陣或清單的簡單報表。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-116">The following pictures show simple reports with a table, matrix, or list.</span></span>  
  
 <span data-ttu-id="1ea6c-117">![RS_TableMatrixList](../media/rs-tablematrixlist.gif "RS_TableMatrixList")</span><span class="sxs-lookup"><span data-stu-id="1ea6c-117">![RS_TableMatrixList](../media/rs-tablematrixlist.gif "RS_TableMatrixList")</span></span>  
  
 <span data-ttu-id="1ea6c-118">若要快速地開始使用資料表、矩陣和清單，請參閱[教學課程：建立基本資料表報表 &#40;報表產生器&#41;](../tutorial-creating-a-basic-table-report-report-builder.md)、[教學課程：建立矩陣報表 &#40;報表產生器&#41;](../tutorial-creating-a-matrix-report-report-builder.md) 及[教學課程：建立自由格式報表 &#40;報表產生器&#41;](../tutorial-creating-a-free-form-report-report-builder.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-118">To quickly get started with tables, matrices, and lists, see [Tutorial: Creating a Basic Table Report &#40;Report Builder&#41;](../tutorial-creating-a-basic-table-report-report-builder.md), [Tutorial: Creating a Matrix Report &#40;Report Builder&#41;](../tutorial-creating-a-matrix-report-report-builder.md), and [Tutorial: Creating a Free Form Report &#40;Report Builder&#41;](../tutorial-creating-a-free-form-report-report-builder.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1ea6c-119">您可以將資料表、矩陣和清單當做報表組件，與報表分開發行。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-119">You can publish tables, matrices, and lists separately from a report as report parts.</span></span> [!INCLUDE[ssRBrptparts](../../includes/ssrbrptparts-md.md)]  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="table"></a><a name="Table"></a><span data-ttu-id="1ea6c-120">目錄</span><span class="sxs-lookup"><span data-stu-id="1ea6c-120">Table</span></span>  
 <span data-ttu-id="1ea6c-121">使用資料表顯示詳細資料、在資料列群組中組織資料，或兩者。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-121">Use a table to display detail data, organize the data in row groups, or both.</span></span> <span data-ttu-id="1ea6c-122">「資料表」範本包含三個資料行，其中有一個資料的資料表頁首資料列和一個詳細資料資料列。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-122">The Table template contains three columns with a table header row and a details row for data.</span></span> <span data-ttu-id="1ea6c-123">下圖顯示在設計介面上選取的初始資料表範本：</span><span class="sxs-lookup"><span data-stu-id="1ea6c-123">The following figure shows the initial table template, selected on the design surface:</span></span>  
  
 <span data-ttu-id="1ea6c-124">![在設計介面上選取的資料表範本](../media/rs-tabletemplatenewselected.gif "在設計介面上選取的資料表範本")</span><span class="sxs-lookup"><span data-stu-id="1ea6c-124">![Table template on design surface, selected](../media/rs-tabletemplatenewselected.gif "Table template on design surface, selected")</span></span>  
  
 <span data-ttu-id="1ea6c-125">您可以依單一欄位、多個欄位或透過撰寫自己的運算式來分組資料。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-125">You can group data by a single field, by multiple fields, or by writing your own expression.</span></span> <span data-ttu-id="1ea6c-126">您可以建立巢狀群組或獨立的相鄰群組，以及顯示群組資料的彙總值，或將總計加入至群組。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-126">You can create nested groups or independent, adjacent groups and display aggregated values for grouped data, or add totals to groups.</span></span> <span data-ttu-id="1ea6c-127">例如，如果您的資料表有一個稱為 [Category] 的資料列群組，您可以加入每個群組的小計，以及報表的總計。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-127">For example, if your table has a row group called [Category], you can add a subtotal for each group as well as a grand total for the report.</span></span> <span data-ttu-id="1ea6c-128">若要改善資料表的外觀，並反白顯示您想要強調的資料，您可以合併資料格，並將格式套用至資料和資料表標題。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-128">To improve the appearance of the table and highlight data you want to emphasize, you can merge cells and apply formatting to data and table headings.</span></span>  
  
 <span data-ttu-id="1ea6c-129">您可以一開始隱藏詳細資料或群組資料並加入向下鑽研切換，以便讓使用者以互動方式選擇要顯示多少資料。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-129">You can initially hide detail or grouped data, and include drilldown toggles to enable a user to interactively choose how much data to show.</span></span>  
  
 <span data-ttu-id="1ea6c-130">如需詳細資訊，請參閱[資料表 &#40;報表產生器及 SSRS&#41;](tables-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-130">For more information, see [Tables &#40;Report Builder  and SSRS&#41;](tables-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="matrix"></a><a name="Matrix"></a><span data-ttu-id="1ea6c-131">核准</span><span class="sxs-lookup"><span data-stu-id="1ea6c-131">Matrix</span></span>  
 <span data-ttu-id="1ea6c-132">使用矩陣顯示在資料列與資料行中群組的彙總資料摘要，類似於樞紐分析表或交叉資料表。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-132">Use a matrix to display aggregated data summaries, grouped in rows and columns, similar to a PivotTable or crosstab.</span></span> <span data-ttu-id="1ea6c-133">群組的資料列數和資料行數，取決於每個資料列和資料行群組的唯一組數目。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-133">The number of rows and columns for groups is determined by the number of unique values for each row and column groups.</span></span> <span data-ttu-id="1ea6c-134">下圖顯示在設計介面上選取的初始矩陣範本：</span><span class="sxs-lookup"><span data-stu-id="1ea6c-134">The following figure shows the initial matrix template, selected on the design surface:</span></span>  
  
 <span data-ttu-id="1ea6c-135">![從工具箱新增選取的矩陣](../media/rs-matrixtemplatenewselected.gif "從工具箱新增選取的矩陣")</span><span class="sxs-lookup"><span data-stu-id="1ea6c-135">![New Matrix added from Toolbox, selected](../media/rs-matrixtemplatenewselected.gif "New Matrix added from Toolbox, selected")</span></span>  
  
 <span data-ttu-id="1ea6c-136">您可以依資料列和資料行群組中的多個欄位或運算式群組資料。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-136">You can group data by multiple fields or expressions in row and column groups.</span></span> <span data-ttu-id="1ea6c-137">當報表資料和資料區在執行階段結合時，如果為資料行群組加入資料行，並為資料列群組加入資料列，則矩陣會在頁面上以水平和垂直方式成長。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-137">At run time, when the report data and data regions are combined, a matrix grows horizontally and vertically on the page as columns for column groups and rows for row groups are added.</span></span> <span data-ttu-id="1ea6c-138">矩陣資料格會顯示資料格所屬資料列與資料行群組交集範圍內的彙總值。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-138">The matrix cells display aggregate values that are scoped to the intersection of the row and column groups to which the cell belongs.</span></span> <span data-ttu-id="1ea6c-139">例如，如果您的矩陣有一個資料列群組 (Category) 和兩個資料行群組 (Territory 和 Year) 顯示銷售量的總和，報表會針對 Category 群組中的每個值，顯示包含銷售量總和的兩個資料格。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-139">For example, if your matrix has a row group (Category) and two column groups (Territory and Year) that display the sum of sales, the report displays two cells with sums of sales for each value in the Category group.</span></span> <span data-ttu-id="1ea6c-140">資料格範圍的兩個交集是：Category 和 Territory，以及 Category 和 Year。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-140">The scope of the cells are the two intersections are: Category and Territory and Category and Year.</span></span> <span data-ttu-id="1ea6c-141">矩陣可以包含巢狀群組與相鄰的群組。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-141">The matrix can include nested and adjacent groups.</span></span> <span data-ttu-id="1ea6c-142">巢狀群組擁有父子式關聯性，而相鄰的群組則擁有對等關聯性。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-142">Nested groups have a parent-child relationship and adjacent groups a peer relationship.</span></span> <span data-ttu-id="1ea6c-143">您可以針對矩陣內的任何和所有層級的巢狀資料列和資料行群組加入小計。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-143">You can add subtotals for any and all levels of nested row and column groups within the matrix.</span></span>  
  
 <span data-ttu-id="1ea6c-144">若要讓矩陣資料更容易讀取，並反白顯示您想要強調的資料，您可以合併資料格，或以水平和垂直方式分割，然後將格式套用至資料和群組標題。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-144">To make the matrix data more readable and highlight the data you want to emphasize, you can merge cells or split horizontally and vertically and apply formatting to data and group headings.</span></span>  
  
 <span data-ttu-id="1ea6c-145">您也可以加入一開始隱藏詳細資料的向下鑽研切換，使用者就可以在需要時，按一下切換來顯示更多或更少的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-145">You can also include drilldown toggles that initially hide detail data; the user can then click the toggles to display more or less detail as needed.</span></span>  
  
 <span data-ttu-id="1ea6c-146">如需詳細資訊，請參閱[&#40;報表產生器和 SSRS&#41;的矩陣](create-a-matrix-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-146">For more information, see [Matrices &#40;Report Builder and SSRS&#41;](create-a-matrix-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="list"></a><a name="List"></a><span data-ttu-id="1ea6c-147">名單</span><span class="sxs-lookup"><span data-stu-id="1ea6c-147">List</span></span>  
 <span data-ttu-id="1ea6c-148">使用清單來建立自由形式配置。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-148">Use a list to create a free-form layout.</span></span> <span data-ttu-id="1ea6c-149">您不會受限於格線配置，但是可以將欄位任意放在清單內。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-149">You are not limited to a grid layout, but can place fields freely inside the list.</span></span> <span data-ttu-id="1ea6c-150">您可以使用清單來設計顯示許多資料集欄位的表單，或將表單設計為容器來並排顯示群組資料的多個資料區域。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-150">You can use a list to design a form for displaying many dataset fields or as a container to display multiple data regions side by side for grouped data.</span></span> <span data-ttu-id="1ea6c-151">例如，您可以定義清單的群組；加入資料表、圖表與影像；以及以資料表和圖形形式顯示每個群組值的值，如同您針對員工或病患記錄所進行的處理。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-151">For example, you can define a group for a list; add a table, chart, and image; and display values in table and graphic form for each group value, as you might for an employee or patient record.</span></span>  
  
 <span data-ttu-id="1ea6c-152">![從工具箱新增選取的新清單](../media/rs-listtemplatenewselected.gif "從工具箱新增選取的新清單")</span><span class="sxs-lookup"><span data-stu-id="1ea6c-152">![New List added from Toolbox, selected](../media/rs-listtemplatenewselected.gif "New List added from Toolbox, selected")</span></span>  
  
 <span data-ttu-id="1ea6c-153">如需詳細資訊，請參閱[&#40;報表產生器和 SSRS&#41;清單](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-153">For more information, see [Lists &#40;Report Builder and SSRS&#41;](create-invoices-and-forms-with-lists-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="preparing-data"></a><a name="PreparingData"></a><span data-ttu-id="1ea6c-154">準備資料</span><span class="sxs-lookup"><span data-stu-id="1ea6c-154">Preparing Data</span></span>  
 <span data-ttu-id="1ea6c-155">資料表、矩陣和清單資料區都會顯示資料集中的資料。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-155">A table, matrix, and list data regions display data from a dataset.</span></span> <span data-ttu-id="1ea6c-156">您可以在擷取資料集之資料的查詢中準備資料，也可以透過設定資料表、矩陣或清單中的屬性來準備資料。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-156">You can prepare the data in the query that retrieves the data for the dataset or by setting properties in the table, matrix, or list.</span></span>  
  
 <span data-ttu-id="1ea6c-157">您用來擷取報表資料集之資料的查詢語言 (例如 [!INCLUDE[tsql](../../includes/tsql-md.md)]) 可以透過套用篩選以便只包含資料的子集、以使報表更容易讀取的常數取代 Null 值或空白，以及排序和分組資料，來準備資料。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-157">The query languages such as [!INCLUDE[tsql](../../includes/tsql-md.md)], that you use to retrieve the data for the report datasets can prepare the data by applying filters to include only a subset of the data, replacing null values or blanks with constants that make the report more readable, and sorting and grouping data.</span></span>  
  
 <span data-ttu-id="1ea6c-158">如果您選擇在報表的資料表、矩陣或清單資料區中準備資料，您要在資料區上或資料區內的資料格上設定屬性。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-158">If you choose to prepare the data in the table, matrix, or list data region of a report, you set properties on the data region or cells within the data region.</span></span> <span data-ttu-id="1ea6c-159">如果您想要篩選或排序資料，請在資料區上設定屬性。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-159">If you want to filter or sort the data, set the properties on the data region.</span></span> <span data-ttu-id="1ea6c-160">例如，若要排序資料，您要指定排序所依據的資料行和排序方向。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-160">For example, to sort the data you specify the columns to sort on and the sort direction.</span></span> <span data-ttu-id="1ea6c-161">如果您想要為某個欄位提供一個替代值，您要設定顯示該欄位之資料格文字的值。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-161">If you want to provide an alternative value for a field, you set the values of the cell text that displays the field.</span></span> <span data-ttu-id="1ea6c-162">例如，若要在欄位空白或 Null 時顯示空白，您要使用運算式來設定值。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-162">For example, to display Blank when a field is empty or null, you use an expression to set the value.</span></span>  
  
 <span data-ttu-id="1ea6c-163">如需詳細資訊，請參閱[準備要在 Tablix 資料區中顯示的資料 &#40;報表產生器及 SSRS&#41;](preparing-data-for-display-in-a-tablix-data-region-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-163">For more information, see [Preparing Data for Display in a Tablix Data Region &#40;Report Builder and SSRS&#41;](preparing-data-for-display-in-a-tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  

  
##  <a name="building-and-configuring-a-table-matrix-or-list"></a><a name="BuildingConfiguringTableMatrixList"></a><span data-ttu-id="1ea6c-164">建立和設定資料表、矩陣或清單</span><span class="sxs-lookup"><span data-stu-id="1ea6c-164">Building and Configuring a Table, Matrix, or List</span></span>  
 <span data-ttu-id="1ea6c-165">當您將資料表或矩陣加入至報表時，可以使用「資料表和矩陣精靈」或從報表產生器和報表設計師所提供的範本手動建立它們。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-165">When you add tables or matrices to your report, you can use the Table and Matrix Wizard or build them manually from the templates that Report Builder and Report Designer provide.</span></span> <span data-ttu-id="1ea6c-166">清單是從清單範本手動建立。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-166">Lists are built manually from the list template.</span></span>  
  
 <span data-ttu-id="1ea6c-167">此精靈會引導您進行快速建立和設定資料表或矩陣的步驟。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-167">The wizard guides you through the steps to quickly build and configure a table or matrix.</span></span> <span data-ttu-id="1ea6c-168">完成精靈之後，或者如果您要從頭開始建立 Tablix 資料區，您可以進一步設定並精簡它們。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-168">After you complete the wizard or if you build the tablix data regions from scratch, you can further configure and refine them.</span></span> <span data-ttu-id="1ea6c-169">可從資料區的滑鼠右鍵功能表取得的對話方塊可讓您輕鬆設定常用的分頁符號屬性、頁首與頁尾的重複性和可見性、顯示選項、篩選，以及排序。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-169">The dialog boxes, available from the right-click menus on the data regions, make it easy to set the most commonly used properties for page breaks, repeatability and visibility of headers and footers, display options, filters, and sorting.</span></span> <span data-ttu-id="1ea6c-170">但是，Tablix 資料區會提供其他豐富的屬性，這些屬性只能在報表產生器的 [屬性] 窗格中設定。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-170">But the tablix data region provides a wealth of additional properties, which you can set only in the Properties pane of Report Builder.</span></span> <span data-ttu-id="1ea6c-171">例如，如果您要在資料表、矩陣或清單的資料集空白時顯示訊息，您要在 [屬性] 窗格的 NoRowsMessage Tablix 屬性中指定訊息文字。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-171">For example, if you want to display a message when the dataset for a table, matrix, or list is empty, you specify the message text in the NoRowsMessage tablix property in the Properties pane.</span></span>  
  

  
##  <a name="changing-between-tablix-templates"></a><a name="ChangingBetweenTablixTemplates"></a><span data-ttu-id="1ea6c-172">在 Tablix 範本之間變更</span><span class="sxs-lookup"><span data-stu-id="1ea6c-172">Changing Between Tablix Templates</span></span>  
 <span data-ttu-id="1ea6c-173">您不會受到一開始選擇的 Tablix 範本所限制。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-173">You are not limited by your initial tablix template choice.</span></span> <span data-ttu-id="1ea6c-174">當您加入群組、總計與標籤時，可以修改您的 Tablix 設計。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-174">As you add groups, totals, and labels, you might want to modify your tablix design.</span></span> <span data-ttu-id="1ea6c-175">例如，您可以從資料表開始，然後刪除詳細資料資料列並加入資料行群組。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-175">For example, you might start with a table and then delete the details row and add column groups.</span></span> <span data-ttu-id="1ea6c-176">如需詳細資訊，請參閱[探索 Tablix 資料區的彈性 &#40;報表產生器及 SSRS&#41;](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-176">For more information, see [Exploring the Flexibility of a Tablix Data Region &#40;Report Builder and SSRS&#41;](exploring-the-flexibility-of-a-tablix-data-region-report-builder-and-ssrs.md).</span></span>  
  
 <span data-ttu-id="1ea6c-177">您可以加入任何 Tablix 功能以便繼續開發資料表、矩陣或清單。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-177">You can continue to develop a table, matrix, or list by adding any tablix feature.</span></span> <span data-ttu-id="1ea6c-178">Tablix 功能包括在資料列和資料行上顯示群組資料的詳細資料或彙總。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-178">Tablix features include displaying detail data or aggregates for grouped data on rows and columns.</span></span> <span data-ttu-id="1ea6c-179">您可以建立巢狀群組、獨立的相鄰群組或遞迴群組。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-179">You can create nested groups, independent adjacent groups, or recursive groups.</span></span> <span data-ttu-id="1ea6c-180">您可以在群組定義中加入多個群組運算式，藉以篩選與排序群組資料，並輕鬆地結合群組。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-180">You can filter and sort grouped data, and easily combine groups by including multiple group expressions in a group definition</span></span>  
  
 <span data-ttu-id="1ea6c-181">您也可以加入群組的總計或資料區的總計。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-181">You can also add totals for a group or grand totals for the data region.</span></span> <span data-ttu-id="1ea6c-182">您可以隱藏資料列或資料行來簡化報表，並讓使用者切換隱藏資料的顯示，如同在向下鑽研報表中一樣。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-182">You can hide rows or columns to simplify a report and enable the user to toggle the display of the hidden data, as in a drilldown report.</span></span> <span data-ttu-id="1ea6c-183">如需詳細資訊，請參閱 [控制報表頁面上的 Tablix 資料區顯示 &#40;報表產生器及 SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md)。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-183">For more information, see [Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;](controlling-the-tablix-data-region-display-on-a-report-page.md).</span></span>  
  

  
##  <a name="how-to-topics"></a><a name="HowTo"></a><span data-ttu-id="1ea6c-184">How To 主題</span><span class="sxs-lookup"><span data-stu-id="1ea6c-184">How-To Topics</span></span>  
 <span data-ttu-id="1ea6c-185">本節列出向您逐步示範如何在報表中使用資料表、矩陣和清單；如何顯示資料列和資料行中的資料、加入和刪除資料行、合併資料格，以及加入資料列和資料行群組之小計的程序。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-185">This section lists procedures that show you, step by step, how to work with work with tables, matrices and lists in your reports; how to display data in rows and columns, add and delete columns, merge cells, and include subtotals for row and column groups.</span></span>  
  
-   [<span data-ttu-id="1ea6c-186">加入詳細資料群組 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-186">Add a Details Group &#40;Report Builder and SSRS&#41;</span></span>](add-a-details-group-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="1ea6c-187">將總計新增至群組或 Tablix 資料區 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-187">Add a Total to a Group or Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](add-a-total-to-a-group-or-tablix-data-region-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="1ea6c-188">變更資料格內的項目 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-188">Change an Item Within a Cell &#40;Report Builder and SSRS&#41;</span></span>](change-an-item-within-a-cell-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="1ea6c-189">變更資料列高度或資料行寬度 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-189">Change Row Height or Column Width &#40;Report Builder and SSRS&#41;</span></span>](change-row-height-or-column-width-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="1ea6c-190">插入或刪除資料行 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-190">Insert or Delete a Column &#40;Report Builder and SSRS&#41;</span></span>](insert-or-delete-a-column-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="1ea6c-191">插入或刪除資料列 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-191">Insert or Delete a Row &#40;Report Builder and SSRS&#41;</span></span>](insert-or-delete-a-row-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="1ea6c-192">在資料區中合併資料格 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-192">Merge Cells in a Data Region &#40;Report Builder and SSRS&#41;</span></span>](merge-cells-in-a-data-region-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="1ea6c-193">建立遞迴階層群組 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-193">Create a Recursive Hierarchy Group &#40;Report Builder and SSRS&#41;</span></span>](create-a-recursive-hierarchy-group-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="1ea6c-194">在資料區中加入或刪除群組 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-194">Add or Delete a Group in a Data Region &#40;Report Builder and SSRS&#41;</span></span>](add-or-delete-a-group-in-a-data-region-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="1ea6c-195">與群組一起顯示頁首和頁尾 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-195">Display Headers and Footers with a Group &#40;Report Builder and SSRS&#41;</span></span>](display-headers-and-footers-with-a-group-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="1ea6c-196">建立階梯狀報表 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-196">Create a Stepped Report &#40;Report Builder and SSRS&#41;</span></span>](create-a-stepped-report-report-builder-and-ssrs.md)  
  
-   [<span data-ttu-id="1ea6c-197">加入、移動或刪除資料表、矩陣或清單 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-197">Add, Move, or Delete a Table, Matrix, or List &#40;Report Builder and SSRS&#41;</span></span>](add-move-or-delete-a-table-matrix-or-list-report-builder-and-ssrs.md)  
  

  
##  <a name="in-this-section"></a><a name="InThisSection"></a> <span data-ttu-id="1ea6c-198">本節內容</span><span class="sxs-lookup"><span data-stu-id="1ea6c-198">In This Section</span></span>  
 <span data-ttu-id="1ea6c-199">下列主題提供有關使用 Tablix 資料區的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-199">The following topics provide additional information about working with the tablix data region.</span></span>  
  
 [<span data-ttu-id="1ea6c-200">Tablix 資料區 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-200">Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](../tablix-data-region-report-builder-and-ssrs.md)  
 <span data-ttu-id="1ea6c-201">說明與 Tablix 資料區相關的主要概念，例如 Tablix 的區域、詳細資料和群組資料、資料行和資料列群組，以及靜態與動態資料列和資料行。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-201">Explains key concepts related to the tablix data region such as areas of the tablix, detail and grouped data, column and row groups, and static and dynamic rows and columns.</span></span>  
  
 [<span data-ttu-id="1ea6c-202">將資料加入至 Tablix 資料區 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-202">Adding Data to a Tablix Data Region &#40;Report Builder and SSRS&#41;</span></span>](adding-data-to-a-tablix-data-region-report-builder-and-ssrs.md)  
 <span data-ttu-id="1ea6c-203">提供有關將詳細資料和群組資料、小計和總計，以及標籤加入至 Tablix 資料區的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-203">Provides detailed information about adding detail and grouped data, subtotals and totals, and labels to a tablix data region.</span></span>  
  
 [<span data-ttu-id="1ea6c-204">控制報表頁面上的 Tablix 資料區顯示 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-204">Controlling the Tablix Data Region Display on a Report Page &#40;Report Builder and SSRS&#41;</span></span>](controlling-the-tablix-data-region-display-on-a-report-page.md)  
 <span data-ttu-id="1ea6c-205">描述 Tablix 資料區的屬性，您可以修改這些屬性來變更您在報表中檢視時 Tablix 資料區顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-205">Describes properties for a tablix data region that you can modify to change the way a tablix data region appears when you view it in a report.</span></span>  
  
 [<span data-ttu-id="1ea6c-206">控制資料列和資料行標題 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-206">Controlling Row and Column Headings &#40;Report Builder and SSRS&#41;</span></span>](controlling-row-and-column-headings-report-builder-and-ssrs.md)  
 <span data-ttu-id="1ea6c-207">描述資料表、矩陣或清單資料區以水平或垂直方式跨越多個頁面時，如何控制資料列和資料行標題。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-207">Describes how to control row and column headings when a table, matrix, or list data region cans span multiple pages horizontally or vertically.</span></span>  
  
 [<span data-ttu-id="1ea6c-208">建立遞迴階層群組 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-208">Creating Recursive Hierarchy Groups &#40;Report Builder and SSRS&#41;</span></span>](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md)  
 <span data-ttu-id="1ea6c-209">描述如何顯示父系和子系之關聯性由資料集中之欄位表示的遞迴資料。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-209">Describes how to display recursive data where the relationship between parent and child is represented by fields in the dataset.</span></span>  
  
 [<span data-ttu-id="1ea6c-210">了解群組 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-210">Understanding Groups &#40;Report Builder and SSRS&#41;</span></span>](understanding-groups-report-builder-and-ssrs.md)  
 <span data-ttu-id="1ea6c-211">說明群組的定義和使用時機，並描述可用於不同 Tablix 資料區的群組。</span><span class="sxs-lookup"><span data-stu-id="1ea6c-211">Explains what groups are and when you use them and describes the groups available for the different tablix data regions.</span></span>  
  

  
## <a name="see-also"></a><span data-ttu-id="1ea6c-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ea6c-212">See Also</span></span>  
 <span data-ttu-id="1ea6c-213">[新增資料集篩選、資料區域篩選和群組篩選 &#40;報表產生器和 SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span><span class="sxs-lookup"><span data-stu-id="1ea6c-213">[Add Dataset Filters, Data Region Filters, and Group Filters &#40;Report Builder and SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md) </span></span>  
 <span data-ttu-id="1ea6c-214">[&#40;報表產生器和 SSRS 的嵌套資料區域&#41;](nested-data-regions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ea6c-214">[Nested Data Regions &#40;Report Builder and SSRS&#41;](nested-data-regions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1ea6c-215">[將多個資料區域連結至相同的資料集 &#40;報表產生器和 SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ea6c-215">[Linking Multiple Data Regions to the Same Dataset &#40;Report Builder and SSRS&#41;](linking-multiple-data-regions-to-the-same-dataset-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1ea6c-216">[運算式 &#40;報表產生器及 SSRS&#41;](expressions-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ea6c-216">[Expressions &#40;Report Builder and SSRS&#41;](expressions-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1ea6c-217">[篩選、分組和排序資料 &#40;報表產生器和 SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ea6c-217">[Filter, Group, and Sort Data &#40;Report Builder and SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md) </span></span>  
 <span data-ttu-id="1ea6c-218">[報表參數 &#40;報表產生器和報表設計師&#41;](report-parameters-report-builder-and-report-designer.md) </span><span class="sxs-lookup"><span data-stu-id="1ea6c-218">[Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md) </span></span>  
 <span data-ttu-id="1ea6c-219">[圖表 &#40;報表產生器和 SSRS&#41;](charts-report-builder-and-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="1ea6c-219">[Charts &#40;Report Builder and SSRS&#41;](charts-report-builder-and-ssrs.md) </span></span>  
 [<span data-ttu-id="1ea6c-220">量測計 &#40;報表產生器及 SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="1ea6c-220">Gauges &#40;Report Builder and SSRS&#41;</span></span>](gauges-report-builder-and-ssrs.md)  
  
  
