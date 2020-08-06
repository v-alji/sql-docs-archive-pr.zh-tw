---
title: 將資料行新增至 (SSAS 表格式) 的資料表 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5974a3cc-caf8-4558-8836-6e3c24b1ee23
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5f329150e3b679e67ee65570efbca904a0570786
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594227"
---
# <a name="add-columns-to-a-table-ssas-tabular"></a><span data-ttu-id="0f822-102">將資料行加入至資料表 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="0f822-102">Add Columns to a Table (SSAS Tabular)</span></span>
  <span data-ttu-id="0f822-103">本主題描述如何將資料行加入現有資料表。</span><span class="sxs-lookup"><span data-stu-id="0f822-103">This topic describes how to add columns to an existing table.</span></span>  
  
## <a name="add-columns-from-the-data-source"></a><span data-ttu-id="0f822-104">從資料來源加入資料行</span><span class="sxs-lookup"><span data-stu-id="0f822-104">Add Columns from the Data Source</span></span>  
 <span data-ttu-id="0f822-105">當您使用 [資料表匯入精靈] 從資料來源資料表匯入資料時，系統會在模型中建立新的資料表，此模型包含來源資料表中的所有資料行；或者如果您選擇使用 [預覽和篩選] 功能來篩選出某些資料行，則只會包含您選取的資料行及篩選的資料。</span><span class="sxs-lookup"><span data-stu-id="0f822-105">When using the Table Import Wizard to import data from a data source table, a new table is created in the model which includes all of the columns in the source table, or if you choose to filter out certain columns by using the Preview and Filter feature, only those columns and filtered data you select.</span></span> <span data-ttu-id="0f822-106">您也可以撰寫 SQL 查詢來指定只匯入某些資料行。</span><span class="sxs-lookup"><span data-stu-id="0f822-106">You can also write a SQL Query that specifies only certain columns to import.</span></span> <span data-ttu-id="0f822-107">但是，您之後可決定來源資料表擁有您想要加入至模型資料表的其他資料行，或者您必須加入所包含的值衍生自 DAX 公式的導出資料行。</span><span class="sxs-lookup"><span data-stu-id="0f822-107">You may, however, later determine a source table has additional columns that you want to add to the model table, or you need to add a calculated column with values derived from a DAX formula.</span></span>  
  
 <span data-ttu-id="0f822-108">例如，當您一開始從資料來源匯入時，您可以使用 [資料表匯入精靈] 的 [預覽和篩選] 功能，從來源資料表選取有限數目的資料行，稍後您可以決定是否需要從來源資料表加入模型資料表中尚不存在的其他資料行。</span><span class="sxs-lookup"><span data-stu-id="0f822-108">If, for example, when you initially imported from a data source, you used the Preview and Filter feature in the Table Import Wizard to select a limited number of columns from the source table, you later determine that you need to add another column that exists at the source table, but does not yet exist in the model table.</span></span> <span data-ttu-id="0f822-109">又如，新的 AdjustedProfit 資料行已加入至資料來源的 FactSales 資料表，您現在想將相同的 AdjustedProfit 資料行和資料加入至模型中的 Sales 資料表。</span><span class="sxs-lookup"><span data-stu-id="0f822-109">Or, for example, a new AdjustedProfit column was added to the FactSales table at the data source, and you now want to add the same AdjustedProfit column and data to the Sales table in the model.</span></span>  
  
 <span data-ttu-id="0f822-110">在此情況下，您可以使用 [編輯資料表屬性] 對話方塊從來源資料表中選取資料行，再將其加入至模型資料表。</span><span class="sxs-lookup"><span data-stu-id="0f822-110">In these cases, you can use the Edit Table Properties dialog box to select columns from the source table and add them to the model table.</span></span> <span data-ttu-id="0f822-111">[編輯資料表屬性] 對話方塊包含 [資料表預覽] 視窗。</span><span class="sxs-lookup"><span data-stu-id="0f822-111">The Edit Table Properties dialog box includes the table preview window.</span></span> <span data-ttu-id="0f822-112">[資料表預覽] 視窗會顯示來源端的資料表。</span><span class="sxs-lookup"><span data-stu-id="0f822-112">The table preview window displays the table at the source.</span></span> <span data-ttu-id="0f822-113">目前包含在模型資料表定義中的資料行已經過檢查。</span><span class="sxs-lookup"><span data-stu-id="0f822-113">Columns that are already included in the model table definition are already checked.</span></span> <span data-ttu-id="0f822-114">尚未包含在模型資料表定義中的資料行則不會予以檢查。</span><span class="sxs-lookup"><span data-stu-id="0f822-114">Those columns that are not already included in the model table definition are not checked.</span></span> <span data-ttu-id="0f822-115">您可以從來源中選取資料行，然後按一下 [確定]，將資料行加入至模型資料表定義。</span><span class="sxs-lookup"><span data-stu-id="0f822-115">You can add columns from the source to the model table definition by selecting the column and clicking OK.</span></span> <span data-ttu-id="0f822-116">[編輯資料表屬性] 對話方塊的 [資料表預覽] 視窗，提供與 [資料表匯入精靈] 之 [預覽和篩選] 頁面中的 [資料表預覽] 視窗相同的檢視和功能。</span><span class="sxs-lookup"><span data-stu-id="0f822-116">The table preview window in the Edit Table Properties dialog box provides the same view and features as the table preview window in the Preview and Filter page of the Table Import Wizard.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="0f822-117">將資料行加入至包含兩個 (含) 以上之資料分割的資料表時，您必須先使用資料分割管理員將資料行加入至所有已定義的資料分割，再使用 [編輯資料表屬性] 對話方塊將資料行加入至資料表定義。</span><span class="sxs-lookup"><span data-stu-id="0f822-117">When adding a column to a table that contains two or more partitions, before adding the column to the table definition by using the Edit Table Properties dialog box, you must first use Partition Manager to add the column to all defined partitions.</span></span> <span data-ttu-id="0f822-118">將資料行加入至已定義的資料分割之後，即可接著使用 [編輯資料表屬性] 對話方塊，將相同的資料行加入至資料表定義。</span><span class="sxs-lookup"><span data-stu-id="0f822-118">After you have added the column to the defined partitions, you can then add the same column to the table definition by using the Edit Table Properties dialog box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f822-119">如果在一開始使用 [資料表匯入精靈] 匯入資料時，使用 SQL 查詢選取資料表和資料行，則必須在 [編輯資料表屬性] 對話方塊中，再次使用 SQL 查詢將資料行加入至模型資料表。</span><span class="sxs-lookup"><span data-stu-id="0f822-119">If you used a SQL Query to select tables and columns when you initially used the Table Import Wizard to import data, you must again use a SQL Query in the Edit Table Properties dialog box to add columns to the model table.</span></span>  
  
#### <a name="to-add-a-column-from-the-data-source-by-using-the-edit-table-properties-dialog-box"></a><span data-ttu-id="0f822-120">使用 [編輯資料表屬性] 對話方塊從資料來源加入資料行</span><span class="sxs-lookup"><span data-stu-id="0f822-120">To add a column from the data source by using the Edit Table Properties dialog box</span></span>  
  
1.  <span data-ttu-id="0f822-121">在模型設計師中，按一下您要加入資料行的資料表，然後按一下 **[資料表]** 功能表，再按一下  **[資料表屬性]**。</span><span class="sxs-lookup"><span data-stu-id="0f822-121">In the model designer, click on the table you want to add a column to, then click the **Table** menu, and then click  **Table Properties**.</span></span>  
  
2.  <span data-ttu-id="0f822-122">在 **[編輯資料表屬性]** 對話方塊的 [資料表預覽] 視窗中，選取您要加入的來源資料行，再按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="0f822-122">In the **Edit Table Properties** dialog box, in the table preview window, select the source column you want to add, and then click OK.</span></span> <span data-ttu-id="0f822-123">目前包含在資料表定義中的資料行已經過檢查。</span><span class="sxs-lookup"><span data-stu-id="0f822-123">Columns already included in the table definition will already be checked.</span></span>  
  
## <a name="add-a-calculated-column"></a><span data-ttu-id="0f822-124">加入導出資料行</span><span class="sxs-lookup"><span data-stu-id="0f822-124">Add a Calculated Column</span></span>  
 <span data-ttu-id="0f822-125">在導出資料行中，您可以使用 DAX 公式定義每個資料列的值。</span><span class="sxs-lookup"><span data-stu-id="0f822-125">In a calculated column, a DAX formula is used to define a value for each row.</span></span> <span data-ttu-id="0f822-126">例如，您可以使用簡單的公式 (=1)，將值 1 加入至每個資料列，以建立導出資料行。</span><span class="sxs-lookup"><span data-stu-id="0f822-126">For example, you can create a calculated column with a simple formula (=1) that adds a value of 1 to each row.</span></span> <span data-ttu-id="0f822-127">導出資料行也可以使用更複雜的公式，根據模型中的其他資料計算值。</span><span class="sxs-lookup"><span data-stu-id="0f822-127">Calculated columns can also have more complex formulas that calculate values based on other data in the model.</span></span> <span data-ttu-id="0f822-128">其他主題將涵蓋有關導出資料行的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="0f822-128">Calculated columns are covered in more detail in other topics.</span></span> <span data-ttu-id="0f822-129">如需詳細資訊，請參閱 [導出資料行 &#40;SSAS 表格式&#41;](ssas-calculated-columns.md)中撰寫的表格式模型專案。</span><span class="sxs-lookup"><span data-stu-id="0f822-129">For more information, see [Calculated Columns &#40;SSAS Tabular&#41;](ssas-calculated-columns.md).</span></span>  
  
#### <a name="to-create-a-calculated-column"></a><span data-ttu-id="0f822-130">若要建立導出資料行</span><span class="sxs-lookup"><span data-stu-id="0f822-130">To create a calculated column</span></span>  
  
1.  <span data-ttu-id="0f822-131">在模型設計師的 [資料檢視] 中，選取您要加入新的空白導出資料行的資料表，然後捲動至最右側資料行，或按一下 [資料行]\*\*\*\* 功能表，再按一下 [加入資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0f822-131">In the model designer, in Data View, select the table to which you want to add a new, blank calculated column, scroll to the right-most column, or click the **Column** menu, and then click **Add Column**.</span></span>  
  
     <span data-ttu-id="0f822-132">若要在兩個現有的資料行之間建立新資料行，請以滑鼠右鍵按一下現有的資料行，然後按一下 [插入資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0f822-132">To create a new column between two existing columns, right-click on an existing column, and then click **Insert Column**.</span></span>  
  
2.  <span data-ttu-id="0f822-133">在公式列中輸入 DAX 公式，以便為每個資料列加入屬性。</span><span class="sxs-lookup"><span data-stu-id="0f822-133">In the formula bar, type a DAX formula to add attributes for each row.</span></span>  
  
## <a name="add-a-blank-column"></a><span data-ttu-id="0f822-134">加入空白資料行</span><span class="sxs-lookup"><span data-stu-id="0f822-134">Add a Blank Column</span></span>  
 <span data-ttu-id="0f822-135">您可以在模型資料表中建立空白的具名資料行。</span><span class="sxs-lookup"><span data-stu-id="0f822-135">You can create a named, blank column in a model table.</span></span> <span data-ttu-id="0f822-136">如果您想從其他來源貼上資料，空白資料行會很有用。</span><span class="sxs-lookup"><span data-stu-id="0f822-136">Blank columns can be useful if you want to paste data from another source.</span></span> <span data-ttu-id="0f822-137">請記住，貼上的資料之儲存方式與匯入的資料之儲存方式不同。</span><span class="sxs-lookup"><span data-stu-id="0f822-137">Keep in-mind that pasted data is stored differently than imported data.</span></span> <span data-ttu-id="0f822-138">如需詳細資訊，請參閱[複製及貼上資料 &#40;SSAS 表格式&#41;](../copy-and-paste-data-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="0f822-138">For more information, see [Copy and Paste Data &#40;SSAS Tabular&#41;](../copy-and-paste-data-ssas-tabular.md).</span></span>  
  
#### <a name="to-create-a-named-blank-column"></a><span data-ttu-id="0f822-139">建立空白的具名資料行</span><span class="sxs-lookup"><span data-stu-id="0f822-139">To create a named, blank column</span></span>  
  
1.  <span data-ttu-id="0f822-140">在模型設計師的 [資料檢視] 中，選取您要加入空白資料行的資料表，然後捲動至最右側資料行，或按一下 [資料行]\*\*\*\* 功能表，再按一下 [加入資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0f822-140">In the model designer, in Data View, select the table to which you want to add a blank column, scroll to the right-most column, or click the **Column** menu, and then click **Add Column**.</span></span>  
  
     <span data-ttu-id="0f822-141">若要在兩個現有的資料行之間建立新資料行，請以滑鼠右鍵按一下現有的資料行，然後按一下 [插入資料行]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="0f822-141">To create a new column between two existing columns, right-click an existing column, and then click **Insert Column**.</span></span>  
  
2.  <span data-ttu-id="0f822-142">按一下頂端資料格，然後輸入名稱，再按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="0f822-142">Click on the top cell, then type a name, and then press ENTER.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f822-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f822-143">See Also</span></span>  
 <span data-ttu-id="0f822-144">[&#40;SSAS&#41;的 [編輯資料表屬性] 對話方塊](../edit-table-properties-dialog-box-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="0f822-144">[Edit Table Properties Dialog Box &#40;SSAS&#41;](../edit-table-properties-dialog-box-ssas.md) </span></span>  
 [<span data-ttu-id="0f822-145">變更資料表、資料行或資料列篩選對應 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="0f822-145">Change table, column, or row filter mappings &#40;SSAS Tabular&#41;</span></span>](change-table-column-or-row-filter-mappings-ssas-tabular.md)  
  
  
