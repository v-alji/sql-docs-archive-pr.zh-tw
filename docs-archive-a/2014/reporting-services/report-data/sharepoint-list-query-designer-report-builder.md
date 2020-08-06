---
title: SharePoint 清單查詢設計工具 (報表產生器) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10016"
ms.assetid: b8a3122c-8008-4950-b515-937636d7967f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a35efb926b8f729874cff42afc53fb5820c920f0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710218"
---
# <a name="sharepoint-list-query-designer-report-builder"></a><span data-ttu-id="7a622-102">SharePoint 清單查詢設計工具 (報表產生器)</span><span class="sxs-lookup"><span data-stu-id="7a622-102">SharePoint List Query Designer (Report Builder)</span></span>
  <span data-ttu-id="7a622-103">報表產生器同時提供了圖形化查詢設計工具和以文字為基礎的查詢設計工具，可協助您建立查詢，以便指定要從 SharePoint 網站中針對報表資料集擷取的資料。</span><span class="sxs-lookup"><span data-stu-id="7a622-103">Report Builder provides both a graphical query designer and a text-based query designer to help you create a query that specifies the data to retrieve from a SharePoint site for a report dataset.</span></span> <span data-ttu-id="7a622-104">您可以使用圖形化查詢設計工具來瀏覽 SharePoint 清單中繼資料、以互動方式建立查詢以及檢視查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="7a622-104">Use the graphical query designer to explore the SharePoint list metadata, interactively build a query, and view the results of your query.</span></span> <span data-ttu-id="7a622-105">您可以使用以文字為基礎的查詢設計工具來檢視圖形化查詢設計工具所建立的查詢、修改查詢，或輸入查詢命令。</span><span class="sxs-lookup"><span data-stu-id="7a622-105">Use the text-based query designer to view the query that was built by the graphical query designer, modify a query, or type the query commands.</span></span> <span data-ttu-id="7a622-106">您也可以從檔案或報表匯入現有的查詢。</span><span class="sxs-lookup"><span data-stu-id="7a622-106">You can also import an existing query from a file or report.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="7a622-107">當使用者建立與執行查詢時，可以存取資料來源。</span><span class="sxs-lookup"><span data-stu-id="7a622-107">Users access data sources when they create and run queries.</span></span> <span data-ttu-id="7a622-108">您應該授與資料來源的最小權限，例如唯讀權限。</span><span class="sxs-lookup"><span data-stu-id="7a622-108">You should grant minimal permissions on the data sources, such as read-only permissions.</span></span>  
  
## <a name="graphical-query-designer"></a><span data-ttu-id="7a622-109">圖形化查詢設計工具</span><span class="sxs-lookup"><span data-stu-id="7a622-109">Graphical Query Designer</span></span>  
 <span data-ttu-id="7a622-110">在圖形化查詢設計工具中，您可以瀏覽 SharePoint 網站、以互動方式建立擷取資料集的 SharePoint 網站清單資料的命令。</span><span class="sxs-lookup"><span data-stu-id="7a622-110">In the graphical query designer you can explorer the SharePoint site, interactively build the command that retrieve SharePoint list data for a dataset.</span></span> <span data-ttu-id="7a622-111">您可以選擇要包含在資料集中的欄位，並選擇性地指定限制資料集中之資料的篩選。</span><span class="sxs-lookup"><span data-stu-id="7a622-111">You choose the fields to include in the dataset and optionally, specify filters that limit the data in the dataset.</span></span> <span data-ttu-id="7a622-112">您可以指定將篩選當做參數使用，並在執行階段提供篩選的值。</span><span class="sxs-lookup"><span data-stu-id="7a622-112">You can specify that filters are used as parameters and provide the value of the filter at run-time.</span></span>  
  
 <span data-ttu-id="7a622-113">SharePoint 清單包含大量的 SharePoint 專屬欄位，在報表中不一定實用。</span><span class="sxs-lookup"><span data-stu-id="7a622-113">SharePoint lists include a large number of SharePoint specific fields that might not be useful to include in reports.</span></span> <span data-ttu-id="7a622-114">查詢設計工具提供隱藏這些欄位的選項，方便您更快速地決定要使用的欄位。</span><span class="sxs-lookup"><span data-stu-id="7a622-114">The query designer provides an option to hide these fields to make it easier and quicker to determine the fields to use.</span></span>  
  
 <span data-ttu-id="7a622-115">圖形化查詢設計工具分成三個區域</span><span class="sxs-lookup"><span data-stu-id="7a622-115">The graphical query designer is divided into three areas</span></span>  
  
-   <span data-ttu-id="7a622-116">瀏覽窗格，可在其中選取要使用的清單項目及其欄位。</span><span class="sxs-lookup"><span data-stu-id="7a622-116">Explore pane in which you select the list items and their fields to use.</span></span>  
  
-   <span data-ttu-id="7a622-117">設計區域，可建立查詢。</span><span class="sxs-lookup"><span data-stu-id="7a622-117">Design area in which you build the query.</span></span>  
  
-   <span data-ttu-id="7a622-118">可以檢視查詢結果的結果窗格。</span><span class="sxs-lookup"><span data-stu-id="7a622-118">Results pane in which you view the query results.</span></span>  
  
 <span data-ttu-id="7a622-119">下圖顯示搭配 SharePoint 清單使用時的圖形化查詢設計工具。</span><span class="sxs-lookup"><span data-stu-id="7a622-119">The following figure shows the graphical query designer when it is used with SharePoint lists.</span></span>  
  
 <span data-ttu-id="7a622-120">![rsQD_Relational_Graphical_SharePoint](../media/rsqd-relational-graphical-sharepoint.gif "rsQD_Relational_Graphical_SharePoint")</span><span class="sxs-lookup"><span data-stu-id="7a622-120">![rsQD_Relational_Graphical_SharePoint](../media/rsqd-relational-graphical-sharepoint.gif "rsQD_Relational_Graphical_SharePoint")</span></span>  
  
 <span data-ttu-id="7a622-121">下表會描述各個窗格的功能。</span><span class="sxs-lookup"><span data-stu-id="7a622-121">The following table describes the function of each pane.</span></span>  
  
 [<span data-ttu-id="7a622-122">SharePoint 清單</span><span class="sxs-lookup"><span data-stu-id="7a622-122">SharePoint Lists</span></span>](#DatabaseView)  
 <span data-ttu-id="7a622-123">顯示 SharePoint 清單和清單中每個項目內的欄位。</span><span class="sxs-lookup"><span data-stu-id="7a622-123">Displays SharePoint lists and the fields within each item in the list.</span></span>  
  
 [<span data-ttu-id="7a622-124">選取的欄位</span><span class="sxs-lookup"><span data-stu-id="7a622-124">Selected fields</span></span>](#SelectedFields)  
 <span data-ttu-id="7a622-125">顯示來自 [SharePoint 清單] 窗格中所選取項目的 SharePoint 清單欄位名稱清單。</span><span class="sxs-lookup"><span data-stu-id="7a622-125">Displays the list of SharePoint list field names from the selected items in the SharePoint Lists pane.</span></span> <span data-ttu-id="7a622-126">這些欄位會成為報表資料集的欄位集合。</span><span class="sxs-lookup"><span data-stu-id="7a622-126">These fields become the field collection for the report dataset.</span></span>  
  
 [<span data-ttu-id="7a622-127">套用的篩選</span><span class="sxs-lookup"><span data-stu-id="7a622-127">Applied filters</span></span>](#AppliedFilters)  
 <span data-ttu-id="7a622-128">針對 [資料庫檢視] 窗格中的資料表或檢視表顯示欄位和篩選準則的清單。</span><span class="sxs-lookup"><span data-stu-id="7a622-128">Displays a list of fields and filter criteria for tables or views in the Database view.</span></span>  
  
 [<span data-ttu-id="7a622-129">查詢結果</span><span class="sxs-lookup"><span data-stu-id="7a622-129">Query results</span></span>](#QueryResults)  
 <span data-ttu-id="7a622-130">針對自動產生的查詢顯示結果集的範例資料。</span><span class="sxs-lookup"><span data-stu-id="7a622-130">Displays sample data for the result set for the automatically generated query.</span></span>  
  
###  <a name="sharepoint-lists-pane"></a><a name="DatabaseView"></a> <span data-ttu-id="7a622-131">SharePoint 清單窗格</span><span class="sxs-lookup"><span data-stu-id="7a622-131">SharePoint Lists Pane</span></span>  
 <span data-ttu-id="7a622-132">[SharePoint 清單] 窗格會顯示您有權檢視之資料庫物件的中繼資料，而這個權限是由資料來源連接和認證所決定。</span><span class="sxs-lookup"><span data-stu-id="7a622-132">The SharePoint Lists pane displays the metadata for database objects that you have the permissions to view, which is determined by the data source connection and credentials.</span></span> <span data-ttu-id="7a622-133">階層式檢視會檢視依照資料庫結構描述所組織的資料庫物件。</span><span class="sxs-lookup"><span data-stu-id="7a622-133">The hierarchical view displays database objects organized by database schema.</span></span> <span data-ttu-id="7a622-134">您可以展開每個結構描述的節點，以便檢視資料表、檢視表、預存程序和資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="7a622-134">Expand the node for each schema to view tables, views, stored procedures, and table-valued functions.</span></span> <span data-ttu-id="7a622-135">您可以展開資料表或檢視表來顯示資料行。</span><span class="sxs-lookup"><span data-stu-id="7a622-135">Expand a table or view to display the columns.</span></span>  
  
###  <a name="selected-fields-pane"></a><a name="SelectedFields"></a> <span data-ttu-id="7a622-136">選取的欄位窗格</span><span class="sxs-lookup"><span data-stu-id="7a622-136">Selected Fields Pane</span></span>  
 <span data-ttu-id="7a622-137">[選取的欄位] 窗格會顯示您為 SharePoint 清單項目選取的清單項目欄位。</span><span class="sxs-lookup"><span data-stu-id="7a622-137">The Selected Fields pane displays the list item fields that you select for SharePoint list items.</span></span> <span data-ttu-id="7a622-138">顯示在這個窗格中的欄位會成為報表資料集的欄位集合。</span><span class="sxs-lookup"><span data-stu-id="7a622-138">The fields that are displayed in this pane become the field collection for the report dataset.</span></span> <span data-ttu-id="7a622-139">在您建立資料集和查詢之後，請使用 [報表資料] 窗格來檢視報表資料集的欄位集合。</span><span class="sxs-lookup"><span data-stu-id="7a622-139">After you create a dataset and a query, use the Report Data pane to view the field collection for a report dataset.</span></span> <span data-ttu-id="7a622-140">這些欄位代表檢視報表時，您可以在資料表、圖表和其他報表項目中顯示的資料。</span><span class="sxs-lookup"><span data-stu-id="7a622-140">These fields represent the data you can display in tables, charts, and other report items when you view a report.</span></span>  
  
 <span data-ttu-id="7a622-141">若要在這個窗格中加入或移除欄位，請在 [SharePoint 清單] 窗格中選取或清除資料表或檢視欄位的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="7a622-141">To add or remove fields to this pane, select or clear check boxes for the table or view fields in the SharePoint Lists pane.</span></span>  
  
###  <a name="applied-filters-pane"></a><a name="AppliedFilters"></a> <span data-ttu-id="7a622-142">套用的篩選窗格</span><span class="sxs-lookup"><span data-stu-id="7a622-142">Applied Filters Pane</span></span>  
 <span data-ttu-id="7a622-143">[套用的篩選] 窗格會顯示用來限制在執行階段擷取之資料列數目的準則。</span><span class="sxs-lookup"><span data-stu-id="7a622-143">The Applied Filters pane displays the criteria that are used to limit the number of rows of data that are retrieved at run-time.</span></span> <span data-ttu-id="7a622-144">在這個窗格中指定的準則會用來產生 [!INCLUDE[tsql](../../includes/tsql-md.md)] WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="7a622-144">Criteria specified in this pane are used to generate a [!INCLUDE[tsql](../../includes/tsql-md.md)] WHERE clause.</span></span> <span data-ttu-id="7a622-145">當您選取參數選項時，就會自動建立報表參數。</span><span class="sxs-lookup"><span data-stu-id="7a622-145">When you select the parameter option, a report parameter is automatically created.</span></span> <span data-ttu-id="7a622-146">以查詢參數為基礎的報表參數可讓使用者指定查詢的值，以便控制報表中的資料。</span><span class="sxs-lookup"><span data-stu-id="7a622-146">Report parameters that are based on query parameters enable a user to specify values for the query to control the data in the report.</span></span>  
  
 <span data-ttu-id="7a622-147">系統會顯示下列資料行：</span><span class="sxs-lookup"><span data-stu-id="7a622-147">The following columns are displayed:</span></span>  
  
-   <span data-ttu-id="7a622-148">**欄位名稱** ：顯示要套用準則的欄位名稱。</span><span class="sxs-lookup"><span data-stu-id="7a622-148">**Field Name** Displays the name of the field to apply the criteria to.</span></span>  
  
-   <span data-ttu-id="7a622-149">**運算子** ：顯示要在篩選運算式中使用的運算。</span><span class="sxs-lookup"><span data-stu-id="7a622-149">**Operator** Displays the operation to use in the filter expression.</span></span>  
  
-   <span data-ttu-id="7a622-150">**值** ：顯示要在篩選運算式中使用的值。</span><span class="sxs-lookup"><span data-stu-id="7a622-150">**Value** Displays the value to use in the filter expression.</span></span>  
  
-   <span data-ttu-id="7a622-151">**參數** ：顯示要將查詢參數加入至查詢的選項。</span><span class="sxs-lookup"><span data-stu-id="7a622-151">**Parameter** Displays the option to add a query parameter to the query.</span></span> <span data-ttu-id="7a622-152">您可以使用資料集屬性來檢視查詢參數與報表參數之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="7a622-152">Use the Dataset properties to view the relationship between query parameter and report parameter.</span></span>  
  
###  <a name="query-results-pane"></a><a name="QueryResults"></a> <span data-ttu-id="7a622-153">查詢結果窗格</span><span class="sxs-lookup"><span data-stu-id="7a622-153">Query Results Pane</span></span>  
 <span data-ttu-id="7a622-154">[查詢結果] 窗格會針對其他窗格中之選取項目所指定的自動產生查詢顯示結果。</span><span class="sxs-lookup"><span data-stu-id="7a622-154">The Query results pane displays the results for the automatically generated query that is specified by selections in the other panes.</span></span> <span data-ttu-id="7a622-155">結果集中的資料行就是您在 [選取的欄位] 窗格中指定的欄位，而且資料列資料是由您在 [套用的篩選] 窗格中指定的篩選所限制。</span><span class="sxs-lookup"><span data-stu-id="7a622-155">The columns in the result set are the fields that you specify in the Selected Fields pane and the row data is limited by the filters that you specify in the Applied Filters pane.</span></span>  
  
 <span data-ttu-id="7a622-156">這項資料代表您執行查詢時來自資料來源的值。</span><span class="sxs-lookup"><span data-stu-id="7a622-156">This data represents values from the data source at the time that you run the query.</span></span> <span data-ttu-id="7a622-157">這項資料不會儲存在報表定義中。報表中的實際資料是在處理報表時擷取的。</span><span class="sxs-lookup"><span data-stu-id="7a622-157">The data is not saved in the report definition .The actual data in the report is retrieved when the report is processed.</span></span>  
  
 <span data-ttu-id="7a622-158">從資料來源中擷取資料的順序會決定結果集中的排序次序。</span><span class="sxs-lookup"><span data-stu-id="7a622-158">Sort order in the result set is determined by the order the data is retrieved from the data source.</span></span> <span data-ttu-id="7a622-159">不過，您可以透過修改查詢，或在擷取報表的資料之後，變更排序次序。</span><span class="sxs-lookup"><span data-stu-id="7a622-159">Sort order can be changed by modifying the query or after the data is retrieved for the report.</span></span>  
  
### <a name="graphical-query-designer-toolbar"></a><span data-ttu-id="7a622-160">圖形化查詢設計工具工具列</span><span class="sxs-lookup"><span data-stu-id="7a622-160">Graphical Query Designer Toolbar</span></span>  
 <span data-ttu-id="7a622-161">關聯式查詢設計工具的工具列會提供下列按鈕來協助您指定或檢視查詢的結果。</span><span class="sxs-lookup"><span data-stu-id="7a622-161">The relational query designer toolbar provides the following buttons to help you specify or view the results of a query.</span></span>  
  
|<span data-ttu-id="7a622-162">按鈕</span><span class="sxs-lookup"><span data-stu-id="7a622-162">Button</span></span>|<span data-ttu-id="7a622-163">描述</span><span class="sxs-lookup"><span data-stu-id="7a622-163">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7a622-164">**當成文字編輯**</span><span class="sxs-lookup"><span data-stu-id="7a622-164">**Edit As Text**</span></span>|<span data-ttu-id="7a622-165">切換至以文字為基礎的查詢設計工具，以便檢視自動產生的查詢，或是修改查詢。</span><span class="sxs-lookup"><span data-stu-id="7a622-165">Toggle to the text-based query designer to view the automatically generated query or to modify the query.</span></span>|  
|<span data-ttu-id="7a622-166">**匯入**</span><span class="sxs-lookup"><span data-stu-id="7a622-166">**Import**</span></span>|<span data-ttu-id="7a622-167">從檔案或報表匯入現有的查詢。</span><span class="sxs-lookup"><span data-stu-id="7a622-167">Import an existing query from a file or report.</span></span> <span data-ttu-id="7a622-168">支援 .sql 和 .rdl 檔案類型。</span><span class="sxs-lookup"><span data-stu-id="7a622-168">File types .sql and .rdl are supported.</span></span>|  
|<span data-ttu-id="7a622-169">**執行查詢**</span><span class="sxs-lookup"><span data-stu-id="7a622-169">**Run Query**</span></span>|<span data-ttu-id="7a622-170">執行查詢。</span><span class="sxs-lookup"><span data-stu-id="7a622-170">Run the query.</span></span> <span data-ttu-id="7a622-171">[查詢結果] 窗格會顯示結果集。</span><span class="sxs-lookup"><span data-stu-id="7a622-171">The Query results pane displays the result set.</span></span>|  
|<span data-ttu-id="7a622-172">**顯示隱藏的欄位**</span><span class="sxs-lookup"><span data-stu-id="7a622-172">**Show Hidden Fields**</span></span>|<span data-ttu-id="7a622-173">切換顯示或隱藏 SharePoint 自動產生，但通常不會在報表中使用的欄位，例如 SharePoint 連結項目的 [ProgId] 和 [Level]。</span><span class="sxs-lookup"><span data-stu-id="7a622-173">Toggle to show or hide the fields that were automatically generated by SharePoint such as the ProgId and Level for SharePoint link items, but are typically not used in reports..</span></span> <span data-ttu-id="7a622-174">隱藏這些欄位會縮短欄位清單，且更方便使用。</span><span class="sxs-lookup"><span data-stu-id="7a622-174">Hiding these fields makes the field list shorter and easier to use.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7a622-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a622-175">See Also</span></span>  
 [<span data-ttu-id="7a622-176">查詢設計工具 &#40;報表產生器&#41;</span><span class="sxs-lookup"><span data-stu-id="7a622-176">Query Designers &#40;Report Builder&#41;</span></span>](../query-designers-report-builder.md)  
  
  
