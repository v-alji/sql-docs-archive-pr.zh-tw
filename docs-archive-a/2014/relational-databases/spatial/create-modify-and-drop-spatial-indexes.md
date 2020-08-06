---
title: 建立、修改及卸除空間索引 | Microsoft Docs
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- indexes [SQL Server], creating
- spatial indexes [SQL Server], dropping
- spatial indexes [SQL Server], creating
- indexes [SQL Server], dropping
- indexes [SQL Server], modifying
- spatial indexes [SQL Server], modifying
ms.assetid: 00c1b927-8ec5-44cf-87c2-c8de59745735
author: MladjoA
ms.author: mlandzic
ms.openlocfilehash: 88de17e8c487d9a965f2e236edac064dc2fe4c7c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585804"
---
# <a name="create-modify-and-drop-spatial-indexes"></a><span data-ttu-id="9ce2f-102">建立、修改及卸除空間索引</span><span class="sxs-lookup"><span data-stu-id="9ce2f-102">Create, Modify, and Drop Spatial Indexes</span></span>
  <span data-ttu-id="9ce2f-103">空間索引可以更有效率地在或資料類型的資料行上執行某些作業， `geometry` `geography` (*空間資料行*) 。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-103">A spatial index can more efficiently perform certain operations on a column of the `geometry` or `geography` data type (a *spatial column*).</span></span> <span data-ttu-id="9ce2f-104">可以在空間資料行上指定一個以上的空間索引。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-104">More than one spatial index can be specified on a spatial column.</span></span> <span data-ttu-id="9ce2f-105">這對於類似在單一資料行上為不同鑲嵌式參數建立索引會很有用處。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-105">This is useful, for example, for indexing different tessellation parameters in a single column.</span></span>  
  
 <span data-ttu-id="9ce2f-106">建立空間索引有一些限制。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-106">There are a number of restrictions on creating spatial indexes.</span></span> <span data-ttu-id="9ce2f-107">如需詳細資訊，請參閱本主題中的 [空間索引的限制](#restrictions) 。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-107">For more information, see [Restrictions on Spatial Indexes](#restrictions) in this topic.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9ce2f-108">如需空間索引與分割區和檔案群組之關聯性的資訊，請參閱 [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql)中的＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-108">For information about the relationship of spatial indexes to partition and to filegroups, see the "Remarks" section in [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql).</span></span>  
  
##  <a name="creating-modifying-and-dropping-spatial-indexes"></a><a name="creating"></a> <span data-ttu-id="9ce2f-109">建立、修改和卸除空間索引</span><span class="sxs-lookup"><span data-stu-id="9ce2f-109">Creating, Modifying, and Dropping Spatial Indexes</span></span>  
  
###  <a name="to-create-a-spatial-index"></a><a name="create"></a> <span data-ttu-id="9ce2f-110">建立空間索引</span><span class="sxs-lookup"><span data-stu-id="9ce2f-110">To create a spatial index</span></span>  
 <span data-ttu-id="9ce2f-111">**使用 Transact-SQL 建立空間索引**</span><span class="sxs-lookup"><span data-stu-id="9ce2f-111">**To create a spatial index by using Transact-SQL**</span></span>  
 [<span data-ttu-id="9ce2f-112">CREATE SPATIAL INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce2f-112">CREATE SPATIAL INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-spatial-index-transact-sql)  
  
 <span data-ttu-id="9ce2f-113">**使用 Management Studio 的 [新增索引] 對話方塊建立空間索引**</span><span class="sxs-lookup"><span data-stu-id="9ce2f-113">**To create a spatial index by using the New Index dialog box in Management Studio**</span></span>  
 ##### <a name="to-create-a-spatial-index-in-management-studio"></a><span data-ttu-id="9ce2f-114">若要在 Management Studio 中建立空間索引</span><span class="sxs-lookup"><span data-stu-id="9ce2f-114">To create a spatial index in Management Studio</span></span>  
  
1.  <span data-ttu-id="9ce2f-115">在 [物件總管] 中，連接到 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 的執行個體，然後展開該執行個體。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-115">In Object Explorer, connect to an instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] and then expand that instance.</span></span>  
  
2.  <span data-ttu-id="9ce2f-116">展開 [資料庫]，再展開含有指定索引之資料表所在的資料庫，然後展開 [資料表]。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-116">Expand **Databases**, expand the database that contains the table with the specified index, and then expand **Tables**.</span></span>  
  
3.  <span data-ttu-id="9ce2f-117">展開您想要建立索引的資料表。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-117">Expand the table for which you want to create the index.</span></span>  
  
4.  <span data-ttu-id="9ce2f-118">以滑鼠右鍵按一下 [索引]，然後選取 [新增索引]。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-118">Right-click **Indexes** and select **New Index**.</span></span>  
  
5.  <span data-ttu-id="9ce2f-119">在 [索引名稱] 欄位中，輸入索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-119">In the **Index name** field, enter a name for the index.</span></span>  
  
6.  <span data-ttu-id="9ce2f-120">在 [索引類型] 下拉式清單中，選取 [空間]。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-120">In the **Index type** drop-down list, select **Spatial**.</span></span>  
  
7.  <span data-ttu-id="9ce2f-121">若要指定您要建立索引的空間資料行，請按一下 [加入]。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-121">To specify the spatial column that you want to index, click **Add**.</span></span>  
  
8.  <span data-ttu-id="9ce2f-122">在 [**從選取資料行** *\<table name>* ] 對話方塊中，選取對應的 `geometry` `geography` 核取方塊來選取或類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-122">In the **Select Columns from** *\<table name>* dialog box, select a column of type `geometry` or `geography` by selecting the corresponding check box.</span></span> <span data-ttu-id="9ce2f-123">任何其他的空間資料行就會變成無法編輯。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-123">Any other spatial columns then become uneditable.</span></span> <span data-ttu-id="9ce2f-124">如果您想要選取不同的空間資料行，就必須先清除目前選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-124">If you want to select a different spatial column, you must first clear the currently selected column.</span></span> <span data-ttu-id="9ce2f-125">完成後，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-125">When finished, click **OK**.</span></span>  
  
9. <span data-ttu-id="9ce2f-126">在 [索引鍵資料行] 方格中確認您的資料行選取。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-126">Verify your column selection in the **Index key columns** grid.</span></span>  
  
10. <span data-ttu-id="9ce2f-127">在 [索引屬性] 對話方塊的 [選取頁面] 窗格中，按一下 [空間]。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-127">In the **Select a page** pane of the **Index Properties** dialog box, click **Spatial**.</span></span>  
  
11. <span data-ttu-id="9ce2f-128">在 [空間] 頁面上，指定您想要用於索引之空間屬性的值。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-128">On the **Spatial** page, specify the values that you want to use for the spatial properties of the index.</span></span>  
  
     <span data-ttu-id="9ce2f-129">在類型資料行上建立索引時 `geometry` ，您必須指定周框方塊的 [ \*\* (]、[ *`X-min`* *`Y-min`*) \*\* ] 和 [ \*\* (] *`X-max`* *`Y-max`*) \*\*座標。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-129">When creating an index on a `geometry` type column, you must specify the **(*`X-min`*,*`Y-min`*)** and **(*`X-max`*,*`Y-max`*)** coordinates of the bounding box.</span></span> <span data-ttu-id="9ce2f-130">若為類型資料行上的索引 `geography` ，在您指定**地理方格**鑲嵌式配置之後，周框方塊欄位會變成隻讀，因為地理方格鑲嵌不會使用周框方塊。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-130">For an index on a `geography` type column, the bounding-box fields become read-only after you specify the **Geography grid** tessellation scheme, because geography grid tessellation does not use a bounding box.</span></span>  
  
     <span data-ttu-id="9ce2f-131">您可以選擇性地針對 [每一物件的資料格] 欄位及鑲嵌式配置的任何方格密度等級指定非預設值。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-131">Optionally, you can specify nondefault values for the **Cells Per Object** field and for the grid density at any level of the tessellation scheme.</span></span> <span data-ttu-id="9ce2f-132">每一物件的資料格預設數目為 16 ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]) 或 8 ([!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)]) 或更高，而預設方格密度是 [中] ([!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)])。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-132">The default number of cells per object is 16 for [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] or 8 for [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] or higher, and the default grid density is **Medium** for [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].</span></span>  
  
     <span data-ttu-id="9ce2f-133">您可以針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]中的鑲嵌式配置選取 GEOMETRY_AUTO_GRID 或 GEOGRAPHY_AUTO_GRID。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-133">You can select GEOMETRY_AUTO_GRID or GEOGRAPHY_AUTO_GRID for tessellation scheme in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="9ce2f-134">當您選取 GEOMETRY_AUTO_GRID 或 GEOGRAPHY_AUTO_GRID 時，就會停用 [層級 1]、[層級 2]、[層級 3] 和 [層級 4] 方格密度選項。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-134">When GEOMETRY_AUTO_GRID or GEOGRAPHY_AUTO_GRID is selected, then Level 1, Level 2, Level 3, and Level 4 grid density options are disabled.</span></span>  
  
     <span data-ttu-id="9ce2f-135">如需這些屬性的詳細資訊，請參閱 [索引屬性 F1 說明](../indexes/index-properties-f1-help.md)。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-135">For more information about these properties, see [Index Properties F1 Help](../indexes/index-properties-f1-help.md).</span></span>  
  
12. <span data-ttu-id="9ce2f-136">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-136">Click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9ce2f-137">若要在相同或不同空間資料行上建立另一個空間索引，請重複上述步驟。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-137">To create another spatial index on the same or a different spatial column, repeat the preceding steps.</span></span>  
  
  
 <span data-ttu-id="9ce2f-138">**使用 Management Studio 的資料表設計工具建立空間索引**</span><span class="sxs-lookup"><span data-stu-id="9ce2f-138">**To create a spatial index by using Table Designer in Management Studio**</span></span>  
 ##### <a name="to-create-a-spatial-index-in-table-designer"></a><span data-ttu-id="9ce2f-139">在資料表設計工具中建立空間索引</span><span class="sxs-lookup"><span data-stu-id="9ce2f-139">To create a spatial index in Table Designer</span></span>  
  
1.  <span data-ttu-id="9ce2f-140">在物件總管中，以滑鼠右鍵按一下要建立空間索引的資料表，然後按一下 [設計]。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-140">In Object Explorer, right-click the table for which you want to create a spatial index, and then click **Design**.</span></span>  
  
     <span data-ttu-id="9ce2f-141">資料表會在 [資料表設計工具] 中開啟。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-141">The table opens in Table Designer.</span></span>  
  
2.  <span data-ttu-id="9ce2f-142">為此索引選取 `geometry` 或 `geography` 資料行。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-142">Select a `geometry` or `geography` column for the index.</span></span>  
  
3.  <span data-ttu-id="9ce2f-143">從 [資料表設計工具] 功能表中，按一下 [空間索引]。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-143">On the **Table Designer** menu, click **Spatial Index**.</span></span>  
  
4.  <span data-ttu-id="9ce2f-144">在 [空間索引] 對話方塊中，按一下 [加入]。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-144">In the **Spatial Indexes** dialog box, click **Add**.</span></span>  
  
5.  <span data-ttu-id="9ce2f-145">在 [Selected Spatial Index (選取的空間索引)] 清單中選取新的索引，並在右邊方格中設定此空間索引的屬性。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-145">Select the new index in the **Selected Spatial Index** list, and in the grid to the right, set the properties for the spatial index.</span></span> <span data-ttu-id="9ce2f-146">如需這些屬性的資訊，請參閱[空間索引對話方塊 &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-146">For information about the properties, see [Spatial Indexes Dialog Box &#40;Visual Database Tools&#41;](../../ssms/visual-db-tools/visual-database-tools.md).</span></span>  
  
  
###  <a name="to-alter-a-spatial-index"></a><a name="alter"></a> <span data-ttu-id="9ce2f-147">改變空間索引</span><span class="sxs-lookup"><span data-stu-id="9ce2f-147">To alter a spatial index</span></span>  
  
-   [<span data-ttu-id="9ce2f-148">ALTER INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce2f-148">ALTER INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-index-transact-sql)  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="9ce2f-149">若要變更空間索引特定的選項 (例如 BOUNDING_BOX 或 GRID)，您可以使用指定 DROP_EXISTING = ON 的 CREATE SPATIAL INDEX 陳述式，或是卸除此空間索引並建立新的索引。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-149">To change options that are specific to a spatial index, such as BOUNDING_BOX or GRID, you can either use a CREATE SPATIAL INDEX statement that specifies DROP_EXISTING = ON, or drop the spatial index and create a new one.</span></span> <span data-ttu-id="9ce2f-150">如需範例，請參閱 [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql)中的＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-150">For an example, see [CREATE SPATIAL INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-spatial-index-transact-sql).</span></span>  
  
-   [<span data-ttu-id="9ce2f-151">修改索引</span><span class="sxs-lookup"><span data-stu-id="9ce2f-151">Modify an Index</span></span>](../indexes/modify-an-index.md)  
  
-   [<span data-ttu-id="9ce2f-152">將現有的索引移至不同的檔案群組</span><span class="sxs-lookup"><span data-stu-id="9ce2f-152">Move an Existing Index to a Different Filegroup</span></span>](../indexes/move-an-existing-index-to-a-different-filegroup.md)  
  
  
###  <a name="to-drop-a-spatial-index"></a><a name="drop"></a> <span data-ttu-id="9ce2f-153">卸除空間索引</span><span class="sxs-lookup"><span data-stu-id="9ce2f-153">To drop a spatial index</span></span>  
 <span data-ttu-id="9ce2f-154">**使用 Transact-SQL 卸除空間索引**</span><span class="sxs-lookup"><span data-stu-id="9ce2f-154">**To drop a spatial index by using Transact-SQL**</span></span>  
 [<span data-ttu-id="9ce2f-155">DROP INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="9ce2f-155">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)  
  
 <span data-ttu-id="9ce2f-156">**若要使用 Management Studio 卸除索引**</span><span class="sxs-lookup"><span data-stu-id="9ce2f-156">**To drop an index by using Management Studio**</span></span>  
 [<span data-ttu-id="9ce2f-157">刪除索引</span><span class="sxs-lookup"><span data-stu-id="9ce2f-157">Delete an Index</span></span>](../indexes/delete-an-index.md)  
  
 <span data-ttu-id="9ce2f-158">**使用 Management Studio 的資料表設計工具卸除空間索引**</span><span class="sxs-lookup"><span data-stu-id="9ce2f-158">**To drop a spatial index by using Table Designer in Management Studio**</span></span>  
 ##### <a name="to-drop-a-spatial-index-in-table-designer"></a><span data-ttu-id="9ce2f-159">在資料表設計工具中卸除空間索引</span><span class="sxs-lookup"><span data-stu-id="9ce2f-159">To drop a spatial index in Table Designer</span></span>  
  
1.  <span data-ttu-id="9ce2f-160">在物件總管中，以滑鼠右鍵按一下具有您要刪除之空間索引的資料表，然後按一下 [設計]。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-160">In Object Explorer, right-click the table with the spatial index you want to delete and click **Design**.</span></span>  
  
     <span data-ttu-id="9ce2f-161">資料表會在 [資料表設計工具] 中開啟。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-161">The table opens in Table Designer.</span></span>  
  
2.  <span data-ttu-id="9ce2f-162">從 [資料表設計工具] 功能表中，按一下 [空間索引]。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-162">On the **Table Designer** menu, click **Spatial Index**.</span></span>  
  
     <span data-ttu-id="9ce2f-163">[空間索引] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-163">The **Spatial Index** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="9ce2f-164">在 [Selected Spatial Index (選取的空間索引)] 資料行中，按一下要刪除的索引。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-164">Click the index you want to delete in the **Selected Spatial Index** column.</span></span>  
  
4.  <span data-ttu-id="9ce2f-165">按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-165">Click **Delete**.</span></span>  
  
  
##  <a name="restrictions-on-spatial-indexes"></a><a name="restrictions"></a> <span data-ttu-id="9ce2f-166">空間索引的限制</span><span class="sxs-lookup"><span data-stu-id="9ce2f-166">Restrictions on Spatial Indexes</span></span>  
 <span data-ttu-id="9ce2f-167">空間索引只能建立在 `geometry` 或 `geography` 類型的資料行上。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-167">A spatial index can be created only on a column of type `geometry` or `geography`.</span></span>  
  
### <a name="table-and-view-restrictions"></a><span data-ttu-id="9ce2f-168">資料表和檢視表限制</span><span class="sxs-lookup"><span data-stu-id="9ce2f-168">Table and View Restrictions</span></span>  
 <span data-ttu-id="9ce2f-169">空間索引只能定義在具有主索引鍵的資料表上。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-169">Spatial indexes can be defined only on a table that has a primary key.</span></span> <span data-ttu-id="9ce2f-170">資料表上主索引鍵資料行的最大數目是 15。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-170">The maximum number of primary key columns on the table is 15.</span></span>  
  
 <span data-ttu-id="9ce2f-171">索引鍵記錄大小的最大值是 895 個位元組。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-171">The maximum size of index key records is 895 bytes.</span></span> <span data-ttu-id="9ce2f-172">較大的值會引發錯誤。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-172">Larger sizes raise an error.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9ce2f-173">當空間索引定義於資料表上時，將無法變更主索引鍵中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-173">Primary key metadata cannot be changed while a spatial index is defined on a table.</span></span>  
  
 <span data-ttu-id="9ce2f-174">不能在索引檢視表上指定空間索引。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-174">Spatial indexes cannot be specified on indexed views.</span></span>  
  
### <a name="multiple-spatial-index-restrictions"></a><span data-ttu-id="9ce2f-175">多個空間索引的限制</span><span class="sxs-lookup"><span data-stu-id="9ce2f-175">Multiple Spatial Index Restrictions</span></span>  
 <span data-ttu-id="9ce2f-176">在支援之資料表的任何空間資料行上最多可以建立 249 個空間索引。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-176">You can create up to 249 spatial indexes on any of the spatial columns in a supported table.</span></span> <span data-ttu-id="9ce2f-177">例如，要針對單一資料行中的不同鑲嵌式參數建立索引時，在相同空間資料行上建立一個以上的空間索引可能會很有用處。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-177">Creating more than one spatial index on the same spatial column can be useful, for example, to index different tessellation parameters in a single column.</span></span>  
  
 <span data-ttu-id="9ce2f-178">您一次只能建立一個空間索引。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-178">You can create only one spatial index at a time.</span></span>  
  
### <a name="spatial-indexes-and-process-parallelism"></a><span data-ttu-id="9ce2f-179">空間索引和處理序平行處理原則</span><span class="sxs-lookup"><span data-stu-id="9ce2f-179">Spatial Indexes and Process Parallelism</span></span>  
 <span data-ttu-id="9ce2f-180">索引建立可以使用可用的處理序平行處理原則。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-180">An index build can use available process parallelism.</span></span>  
  
### <a name="version-restrictions"></a><span data-ttu-id="9ce2f-181">版本限制</span><span class="sxs-lookup"><span data-stu-id="9ce2f-181">Version Restrictions</span></span>  
 <span data-ttu-id="9ce2f-182">[!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中所導入的空間鑲嵌無法複寫至 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-182">Spatial tessellations introduced in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] cannot be replicated to [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)].</span></span> <span data-ttu-id="9ce2f-183">您必須在需要與 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 資料庫進行回溯相容性時，使用空間索引的 [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] 或 [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] 空間鑲嵌式。</span><span class="sxs-lookup"><span data-stu-id="9ce2f-183">You must use [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] spatial tessellations for spatial indexes when backward compatibility with [!INCLUDE[ssKilimanjaro](../../../includes/sskilimanjaro-md.md)] or [!INCLUDE[ssKatmai](../../../includes/sskatmai-md.md)] databases is a requirement.</span></span>  
  
  
## <a name="see-also"></a><span data-ttu-id="9ce2f-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9ce2f-184">See Also</span></span>  
 [<span data-ttu-id="9ce2f-185">空間索引概觀</span><span class="sxs-lookup"><span data-stu-id="9ce2f-185">Spatial Indexes Overview</span></span>](spatial-indexes-overview.md)  
  
  
