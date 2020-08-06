---
title: " (SSAS 表格式) 的資料表和資料行 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c428d717-05de-436c-b9dc-e8c1925a60ca
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3f23b21ce492fd3160df727c1562ee706848fa99
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706785"
---
# <a name="tables-and-columns-ssas-tabular"></a><span data-ttu-id="5c065-102">資料表與資料行 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="5c065-102">Tables and Columns (SSAS Tabular)</span></span>
  <span data-ttu-id="5c065-103">在您使用 [資料表匯入精靈] 將資料表和資料加入模型之後，即可開始使用資料表，包括加入新資料行、建立資料表之間的關聯性、定義可擴充資料的計算，以及在資料表中篩選及排序資料以便於檢視。</span><span class="sxs-lookup"><span data-stu-id="5c065-103">After you have added tables and data into a model by using the Table Import Wizard, you can begin working with the tables by adding new columns of data, creating relationships between tables, defining calculations that extend the data, and filtering and sorting data in the tables for easier viewing.</span></span>  
  
 <span data-ttu-id="5c065-104">本主題的章節：</span><span class="sxs-lookup"><span data-stu-id="5c065-104">Sections in this topic:</span></span>  
  
-   [<span data-ttu-id="5c065-105">優點</span><span class="sxs-lookup"><span data-stu-id="5c065-105">Benefits</span></span>](#bkmk_benefits)  
  
-   [<span data-ttu-id="5c065-106">使用資料表和資料行</span><span class="sxs-lookup"><span data-stu-id="5c065-106">Working with tables and columns</span></span>](#bkmk_working)  
  
-   [<span data-ttu-id="5c065-107">相關工作</span><span class="sxs-lookup"><span data-stu-id="5c065-107">Related Tasks</span></span>](#bkmk_related_tasks)  
  
##  <a name="benefits"></a><a name="bkmk_benefits"></a> <span data-ttu-id="5c065-108">優點</span><span class="sxs-lookup"><span data-stu-id="5c065-108">Benefits</span></span>  
 <span data-ttu-id="5c065-109">表格式模型中的資料表提供定義資料行及其他中繼資料的架構。</span><span class="sxs-lookup"><span data-stu-id="5c065-109">Tables, in tabular models, provide the framework in which columns and other metadata are defined.</span></span> <span data-ttu-id="5c065-110">資料表包括：</span><span class="sxs-lookup"><span data-stu-id="5c065-110">Tables include:</span></span>  
  
 <span data-ttu-id="5c065-111">**資料表定義**</span><span class="sxs-lookup"><span data-stu-id="5c065-111">**Table Definition**</span></span>  
 <span data-ttu-id="5c065-112">資料表定義包含一組資料行。</span><span class="sxs-lookup"><span data-stu-id="5c065-112">The table definition includes the set of columns.</span></span> <span data-ttu-id="5c065-113">可從資料來源匯入或手動加入資料行，例如導出資料行。</span><span class="sxs-lookup"><span data-stu-id="5c065-113">Columns can be imported from a data source or added manually, such as with calculated columns.</span></span>  
  
 <span data-ttu-id="5c065-114">**資料表中繼資料**</span><span class="sxs-lookup"><span data-stu-id="5c065-114">**Table Metadata**</span></span>  
 <span data-ttu-id="5c065-115">關聯性、量值、角色、檢視方塊及貼上的資料，都是定義資料表內容中之物件的所有中繼資料。</span><span class="sxs-lookup"><span data-stu-id="5c065-115">Relationships, measures, roles, perspectives, and pasted data are all metadata the define objects within the context of a table.</span></span>  
  
 <span data-ttu-id="5c065-116">**Data**</span><span class="sxs-lookup"><span data-stu-id="5c065-116">**Data**</span></span>  
 <span data-ttu-id="5c065-117">當您透過 [資料表匯入精靈] 或在導出資料行中建立新資料，第一次匯入資料表時，會在資料表資料行中擴展資料。</span><span class="sxs-lookup"><span data-stu-id="5c065-117">Data is populated in table columns when you first import tables by using the Table Import Wizard or by creating new data in calculated columns.</span></span> <span data-ttu-id="5c065-118">變更來源中的資料，或從記憶體中移除模型時，您必須執行處理作業將資料重新擴展到資料表中。</span><span class="sxs-lookup"><span data-stu-id="5c065-118">When data changes at the source, or when a model is removed from memory, you must run a process operation to re-populate the data into the tables.</span></span>  
  
##  <a name="working-with-tables-and-columns"></a><a name="bkmk_working"></a><span data-ttu-id="5c065-119">使用資料表和資料行</span><span class="sxs-lookup"><span data-stu-id="5c065-119">Working with tables and columns</span></span>  
 <span data-ttu-id="5c065-120">在模型設計師中，您不會直接建立新的模型資料表。</span><span class="sxs-lookup"><span data-stu-id="5c065-120">In the model designer, you do not create new model tables directly.</span></span> <span data-ttu-id="5c065-121">每當從其他資料來源匯入或複製資料時，都會為您自動建立新的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="5c065-121">A new tab is created automatically for you whenever data is imported or copied from another data source.</span></span> <span data-ttu-id="5c065-122">模型設計師中的每個索引標籤都包含一個資料表，其中可以包括以下項目：</span><span class="sxs-lookup"><span data-stu-id="5c065-122">Each tab (in the model designer) contains one table of data, which can include the following:</span></span>  
  
-   <span data-ttu-id="5c065-123">來自關聯式資料庫或其他非關聯式來源 (如 Analysis Services Cube) 的單一資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="5c065-123">A single table or view from a relational database, or from other non-relational sources, such as an Analysis Services cube.</span></span>  
  
-   <span data-ttu-id="5c065-124">從摘要或文字檔匯入的一組表格式資料。</span><span class="sxs-lookup"><span data-stu-id="5c065-124">A tabular set of data imported from a feed or text file.</span></span>  
  
-   <span data-ttu-id="5c065-125">關聯式資料和表格式 (HTML) 資料的組合會複製並貼到資料表中。</span><span class="sxs-lookup"><span data-stu-id="5c065-125">A combination of both relational data and tabular (HTML) data copy and pasted into the table.</span></span>  
  
 <span data-ttu-id="5c065-126">當您匯入資料時，每一個資料表或檢視表、工作表或資料檔都會當做資料表加入至模型設計師。</span><span class="sxs-lookup"><span data-stu-id="5c065-126">When you import data, each table or view, sheet, or file of data is added as a table in the model designer.</span></span> <span data-ttu-id="5c065-127">您通常會從各種來源將資料加入到個別的索引標籤上，但是您可以使用 **[貼上]** 和 **[貼上新增]** 來合併單一資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="5c065-127">You typically add data from various sources onto separate tabs, but you can combine data in a single table by using **Paste** and **Paste Append**.</span></span> <span data-ttu-id="5c065-128">如需詳細資訊，請參閱[複製及貼上資料 &#40;SSAS 表格式&#41;](../copy-and-paste-data-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="5c065-128">For more information, see [Copy and Paste Data &#40;SSAS Tabular&#41;](../copy-and-paste-data-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="5c065-129">在您加入所需的資料之後，您可以建立資料表之間的其他關聯性、在其他資料表中查閱或參考相關的值，或者加入新的導出資料行來建立衍生的值。</span><span class="sxs-lookup"><span data-stu-id="5c065-129">After you have added the data that you need, you can create additional relationships between the tables, look up or reference related values in other tables, or create derived values by adding new calculated columns.</span></span>  
  
 <span data-ttu-id="5c065-130">如果您使用非常大型的資料集，您可能需要篩選而不顯示特定資料。</span><span class="sxs-lookup"><span data-stu-id="5c065-130">If you are working very large data sets, you may want to filter out certain data so it is not visible.</span></span> <span data-ttu-id="5c065-131">您可能也需要依不同順序排序資料。</span><span class="sxs-lookup"><span data-stu-id="5c065-131">You may also want to sort data in a different order.</span></span> <span data-ttu-id="5c065-132">透過模型設計師，您可以使用篩選、排序及隱藏功能顯示或隱藏整個資料行或特定資料。</span><span class="sxs-lookup"><span data-stu-id="5c065-132">By using the model designer, you can use the filter, sort, and hide features to display, or not display, entire columns or certain data.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_related_tasks"></a> <span data-ttu-id="5c065-133">相關工作</span><span class="sxs-lookup"><span data-stu-id="5c065-133">Related Tasks</span></span>  
  
|<span data-ttu-id="5c065-134">主題</span><span class="sxs-lookup"><span data-stu-id="5c065-134">Topic</span></span>|<span data-ttu-id="5c065-135">描述</span><span class="sxs-lookup"><span data-stu-id="5c065-135">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5c065-136">將資料行加入至資料表 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="5c065-136">Add Columns to a Table &#40;SSAS Tabular&#41;</span></span>](add-columns-to-a-table-ssas-tabular.md)|<span data-ttu-id="5c065-137">描述如何將來源資料行加入至資料表定義。</span><span class="sxs-lookup"><span data-stu-id="5c065-137">Describes how to add a source column to a table definition.</span></span>|  
|[<span data-ttu-id="5c065-138">刪除資料行 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="5c065-138">Delete a Column &#40;SSAS Tabular&#41;</span></span>](delete-a-column-ssas-tabular.md)|<span data-ttu-id="5c065-139">描述如何使用模型設計師或 [資料表屬性] 對話方塊，刪除模型資料表資料行。</span><span class="sxs-lookup"><span data-stu-id="5c065-139">Describes how to delete a model table column by using the model designer or by using the Table Properties dialog box.</span></span>|  
|[<span data-ttu-id="5c065-140">變更資料表、資料行或資料列篩選對應 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="5c065-140">Change table, column, or row filter mappings &#40;SSAS Tabular&#41;</span></span>](change-table-column-or-row-filter-mappings-ssas-tabular.md)|<span data-ttu-id="5c065-141">描述如何使用資料表預覽或 [編輯資料表屬性] 對話方塊中的 SQL 查詢編輯器，變更資料表、資料行或資料列篩選對應。</span><span class="sxs-lookup"><span data-stu-id="5c065-141">Describes how to change table, column, or row filter mappings by using the table preview or SQL query editor in the Edit Table Properties dialog box.</span></span>|  
|[<span data-ttu-id="5c065-142">指定標記為日期資料表以搭配時間智慧使用 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="5c065-142">Specify Mark as Date Table for use with Time Intelligence &#40;SSAS Tabular&#41;</span></span>](specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular.md)|<span data-ttu-id="5c065-143">描述如何使用 [標記為日期資料表] 對話方塊來指定日期資料表和唯一識別碼資料行。</span><span class="sxs-lookup"><span data-stu-id="5c065-143">Describes how to use the Mark as Date Table dialog box to specify a date table and unique identifier column.</span></span> <span data-ttu-id="5c065-144">DAX 公式中使用時間智慧函數時，必須指定日期資料表和唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="5c065-144">Specifying a date table and unique identifier is necessary when using time intelligence functions in DAX formulas.</span></span>|  
|[<span data-ttu-id="5c065-145">加入資料表 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="5c065-145">Add a Table &#40;SSAS Tabular&#41;</span></span>](add-a-table-ssas-tabular.md)|<span data-ttu-id="5c065-146">描述如何透過使用現有的資料來源連接，從資料來源中加入資料表。</span><span class="sxs-lookup"><span data-stu-id="5c065-146">Describes how to add a table from a data source by using an existing data source connection.</span></span>|  
|[<span data-ttu-id="5c065-147">刪除資料表 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="5c065-147">Delete a Table &#40;SSAS Tabular&#41;</span></span>](delete-a-table-ssas-tabular.md)|<span data-ttu-id="5c065-148">描述如何刪除模型工作空間資料庫中不再需要的資料表。</span><span class="sxs-lookup"><span data-stu-id="5c065-148">Describes how to delete tables in your model workspace database that you no longer need.</span></span>|  
|[<span data-ttu-id="5c065-149">重新命名資料表或資料行 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="5c065-149">Rename a Table or Column &#40;SSAS Tabular&#41;</span></span>](rename-a-table-or-column-ssas-tabular.md)|<span data-ttu-id="5c065-150">描述如何重新命名資料表或資料行，以在模型中更容易識別。</span><span class="sxs-lookup"><span data-stu-id="5c065-150">Describes how to rename a table or column to make it more identifiable in your model.</span></span>|  
|[<span data-ttu-id="5c065-151">設定資料行的資料類型 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="5c065-151">Set the Data Type of a Column &#40;SSAS Tabular&#41;</span></span>](set-the-data-type-of-a-column-ssas-tabular.md)|<span data-ttu-id="5c065-152">描述如何變更資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="5c065-152">Describes how to change the data type of a column.</span></span> <span data-ttu-id="5c065-153">資料類型定義資料行中資料的儲存及呈現方式。</span><span class="sxs-lookup"><span data-stu-id="5c065-153">The data type defines how data in the column is stored and presented.</span></span>|  
|[<span data-ttu-id="5c065-154">隱藏或凍結資料行 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="5c065-154">Hide or Freeze Columns &#40;SSAS Tabular&#41;</span></span>](hide-or-freeze-columns-ssas-tabular.md)|<span data-ttu-id="5c065-155">描述如何隱藏您不想要顯示的資料行，以及當您在某個區域中凍結) 特定資料行的 (鎖定時，如何保持模型區域的可見度。</span><span class="sxs-lookup"><span data-stu-id="5c065-155">Describes how to hide columns that you don't want to display and how to keep an area of a model visible while you scroll to another area of the model by freezing (locking) specific columns in one area.</span></span>|  
|[<span data-ttu-id="5c065-156">導出資料行 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="5c065-156">Calculated Columns &#40;SSAS Tabular&#41;</span></span>](ssas-calculated-columns.md)|<span data-ttu-id="5c065-157">本節中的主題描述如何使用導出資料行將彙總資料加入至模型。</span><span class="sxs-lookup"><span data-stu-id="5c065-157">Topics in this section describe how you can use calculated columns to add aggregated data to your model.</span></span>|  
|[<span data-ttu-id="5c065-158">篩選與排序資料 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="5c065-158">Filter and Sort Data &#40;SSAS Tabular&#41;</span></span>](../filter-and-sort-data-ssas-tabular.md)|<span data-ttu-id="5c065-159">本節中的主題描述如何使用模型設計師中的控制項篩選或排序資料。</span><span class="sxs-lookup"><span data-stu-id="5c065-159">Topics in this section describe how you can filter or sort data by using controls in the model designer.</span></span>|  
  
  
