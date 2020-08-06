---
title: 索引屬性 F1 說明 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
f1_keywords:
- sql12.swb.indexproperties.storage.f1
- sql12.swb.indexproperties.columns.f1
- sql12.swb.indexproperties.partitions.f1
- sql12.swb.indexproperties.general.f1
- sql12.swb.indexproperties.filter.f1
- sql12.swb.indexproperties.options.f1
- sql12.swb.indexproperties.spatial.f1
ms.assetid: 45efd81a-3796-4b04-b0cc-f3deec94c733
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 390a63d21dc72e052017f2d30b061d71de863bc1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709402"
---
# <a name="index-properties-f1-help"></a><span data-ttu-id="f5e3a-102">索引屬性 F1 說明</span><span class="sxs-lookup"><span data-stu-id="f5e3a-102">Index Properties F1 Help</span></span>
  <span data-ttu-id="f5e3a-103">本主題中的章節參考使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 對話方塊提供的各種不同索引屬性。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-103">The sections in this topic refer to various index properties that are available by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] dialogs.</span></span>  
  
 <span data-ttu-id="f5e3a-104">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-104">**In This Topic:**</span></span>  
  
 [<span data-ttu-id="f5e3a-105">索引屬性一般頁面</span><span class="sxs-lookup"><span data-stu-id="f5e3a-105">Index Properties General Page</span></span>](#General)  
  
 [<span data-ttu-id="f5e3a-106">選取 (索引) 資料行對話方塊</span><span class="sxs-lookup"><span data-stu-id="f5e3a-106">Select (Index) Columns Dialog Box</span></span>](#Columns)  
  
 [<span data-ttu-id="f5e3a-107">索引屬性儲存頁面</span><span class="sxs-lookup"><span data-stu-id="f5e3a-107">Index Properties Storage Page</span></span>](#Storage)  
  
 [<span data-ttu-id="f5e3a-108">索引屬性空間頁面</span><span class="sxs-lookup"><span data-stu-id="f5e3a-108">Index Properties Spatial Page</span></span>](#Spatial)  
  
 [<span data-ttu-id="f5e3a-109">索引屬性篩選頁面</span><span class="sxs-lookup"><span data-stu-id="f5e3a-109">Index Properties Filter Page</span></span>](#Filter)  
  
##  <a name="index-properties-general-page"></a><a name="General"></a> <span data-ttu-id="f5e3a-110">索引屬性一般頁面</span><span class="sxs-lookup"><span data-stu-id="f5e3a-110">Index Properties General Page</span></span>  
 <span data-ttu-id="f5e3a-111">使用 [一般] 頁面可檢視或修改所選取資料表或檢視的索引屬性。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-111">Use the General page to view or modify index properties for the selected table or view.</span></span> <span data-ttu-id="f5e3a-112">每一個頁面的選項可能會因為選取的索引類型而不同。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-112">The options for each page may change based on the type of index selected.</span></span>  
  
 <span data-ttu-id="f5e3a-113">**資料表名稱**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-113">**Table name**</span></span>  
 <span data-ttu-id="f5e3a-114">顯示建立索引的資料表名稱或檢視名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-114">Displays the name of the table or view that the index was created on.</span></span> <span data-ttu-id="f5e3a-115">此欄位是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-115">This field is read-only.</span></span> <span data-ttu-id="f5e3a-116">若要選取不同的資料表，請關閉 [索引屬性] 頁面，選取正確的資料表，然後再次開啟 [索引屬性] 頁面。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-116">To select a different table, close the Index Properties page, select the correct table, and then open the Index Properties page again.</span></span>  
  
 <span data-ttu-id="f5e3a-117">不能在索引檢視表上指定空間索引。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-117">Spatial indexes cannot be specified on indexed views.</span></span> <span data-ttu-id="f5e3a-118">空間索引只能定義在具有主索引鍵的資料表上。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-118">Spatial indexes can be defined only for a table that has a primary key.</span></span> <span data-ttu-id="f5e3a-119">資料表上主索引鍵資料行的最大數目是 15。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-119">The maximum number of primary key columns on the table is 15.</span></span> <span data-ttu-id="f5e3a-120">主索引鍵資料行的每列合併大小上限是 895 個位元組。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-120">The combined per-row size of the primary-key columns is limited to a maximum of 895 bytes.</span></span>  
  
 <span data-ttu-id="f5e3a-121">**索引名稱**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-121">**Index name**</span></span>  
 <span data-ttu-id="f5e3a-122">顯示索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-122">Displays the name of the index.</span></span> <span data-ttu-id="f5e3a-123">這個檔案對現有的索引而言是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-123">This field is read-only for an existing index.</span></span> <span data-ttu-id="f5e3a-124">建立新的索引時，請輸入索引的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-124">When creating a new index, type the name of the index.</span></span>  
  
 <span data-ttu-id="f5e3a-125">**索引類型**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-125">**Index type**</span></span>  
 <span data-ttu-id="f5e3a-126">表示索引的類型。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-126">Indicates the type of index.</span></span> <span data-ttu-id="f5e3a-127">如果是新的索引，則表示開啟此對話方塊時所選取的索引類型。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-127">For new indexes, indicates the type of index selected when opening the dialog box.</span></span> <span data-ttu-id="f5e3a-128">索引可以是：[叢集]、[非叢集]、[主要 XML]、[次要 XML]、[空間]、[叢集資料行存放區] 或 [非叢集資料行存放區]。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-128">Indexes can be: **Clustered**, **Nonclustered**, **Primary XML**, **Secondary XML**, **Spatial**, **Clustered columnstore**, or **Nonclustered Columnstore**.</span></span>  
  
 <span data-ttu-id="f5e3a-129">**注意** ：每個資料表只允許有一個叢集索引。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-129">**Note** Only one clustered index is allowed for each table.</span></span> <span data-ttu-id="f5e3a-130">每個資料表只允許有一個 xVelocity 記憶體最佳化的資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-130">Only one xVelocity memory optimized columnstore index is allowed for each table.</span></span>  
  
 <span data-ttu-id="f5e3a-131">**唯一**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-131">**Unique**</span></span>  
 <span data-ttu-id="f5e3a-132">選取此核取方塊使索引成為唯一的。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-132">Selecting this check box makes the index unique.</span></span> <span data-ttu-id="f5e3a-133">任何兩個資料列都不允許有相同索引值。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-133">No two rows are permitted to have the same index value.</span></span> <span data-ttu-id="f5e3a-134">依預設，不會勾選此核取方塊。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-134">By default, this check box is cleared.</span></span> <span data-ttu-id="f5e3a-135">修改現有的索引時，如果兩個資料列有相同的值，索引建立將會失敗。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-135">When modifying an existing index, index creation will fail if two rows have the same value.</span></span> <span data-ttu-id="f5e3a-136">針對允許 NULL 的資料行，唯一索引允許一個 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-136">For columns where NULL is permitted, a unique index permits one NULL value.</span></span>  
  
 <span data-ttu-id="f5e3a-137">如果您在 **[索引類型]** 欄位中選取 **[空間]** ， **[唯一]** 核取方塊會呈暗灰色。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-137">If you select **Spatial** in the **Index type** field, the **Unique** check box is dimmed.</span></span>  
  
 <span data-ttu-id="f5e3a-138">**索引鍵資料行**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-138">**Index key columns**</span></span>  
 <span data-ttu-id="f5e3a-139">將想要的資料行加入 **[索引鍵資料行]** 方格。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-139">Add the desired columns to the **Index key columns** grid.</span></span> <span data-ttu-id="f5e3a-140">加入多個資料行時，必須以想要的順序列出資料行。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-140">When more than one column is added, the columns must be listed in the order desired.</span></span> <span data-ttu-id="f5e3a-141">索引中的資料行順序對索引效能有很大的影響。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-141">The column order in an index can have a great impact on the index performance.</span></span>  
  
 <span data-ttu-id="f5e3a-142">單一複合索引中參與的資料行不能超過 16 個。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-142">No more than 16 columns can participate in a single composite index.</span></span> <span data-ttu-id="f5e3a-143">如果超過 16 個資料行，請參閱本主題結尾的＜包含的資料行＞。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-143">For greater than 16 columns, see included columns at the end of this topic.</span></span>  
  
 <span data-ttu-id="f5e3a-144">空間索引只能定義在包含空間資料類型的單一資料行上 ( *「空間資料行」* (Spatial Column))。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-144">A spatial index can be defined only on a single column that contains a spatial data type (a *spatial column*).</span></span>  
  
 <span data-ttu-id="f5e3a-145">**名稱**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-145">**Name**</span></span>  
 <span data-ttu-id="f5e3a-146">顯示參與索引鍵的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-146">Displays the name of the column that participates in the index key.</span></span>  
  
 <span data-ttu-id="f5e3a-147">**排序次序**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-147">**Sort Order**</span></span>  
 <span data-ttu-id="f5e3a-148">指定所選取索引資料行的排序方向為 **[遞增]** 或 **[遞減]** 。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-148">Specifies the sort direction of the selected index column, either **Ascending** or **Descending**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f5e3a-149">如果索引類型為 **[主要 XML]** 或 **[空間]** ，此資料行不會出現在資料表中。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-149">If the index type is **Primary XML** or **Spatial**, this column does not appear in the table.</span></span>  
  
 <span data-ttu-id="f5e3a-150">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-150">**Data Type**</span></span>  
 <span data-ttu-id="f5e3a-151">顯示資料類型資訊。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-151">Displays the data type information.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f5e3a-152">如果資料表資料行是計算資料行， **[資料類型]** 就會顯示「計算資料行」。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-152">If the table column is a computed column, **Data type** displays "computed column."</span></span>  
  
 <span data-ttu-id="f5e3a-153">**大小**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-153">**Size**</span></span>  
 <span data-ttu-id="f5e3a-154">顯示儲存資料行資料類型所需的最大位元組數。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-154">Displays the maximum number of bytes required to store the column data type.</span></span> <span data-ttu-id="f5e3a-155">針對空間或 XML 資料行顯示零 (0)。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-155">Displays zero (0) for a spatial or XML column.</span></span>  
  
 <span data-ttu-id="f5e3a-156">**身分識別**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-156">**Identity**</span></span>  
 <span data-ttu-id="f5e3a-157">顯示參與索引鍵的資料行是否為識別欄位。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-157">Displays whether the column participating in the index key is an identity column.</span></span>  
  
 <span data-ttu-id="f5e3a-158">**允許 NULL**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-158">**Allow NULLs**</span></span>  
 <span data-ttu-id="f5e3a-159">顯示參與索引鍵的資料行是否允許在資料表或檢視資料行中儲存 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-159">Displays whether the column participating in the index key allows NULL values to be stored in the table or view column.</span></span>  
  
 <span data-ttu-id="f5e3a-160">**加入**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-160">**Add**</span></span>  
 <span data-ttu-id="f5e3a-161">將資料行加入索引鍵。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-161">Adds a column to the index key.</span></span> <span data-ttu-id="f5e3a-162">從您按一下 [加入] 時所出現的 [從 *\<table name>* 選取資料行] 對話方塊中，選取資料表資料行。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-162">Select table columns from the **Select Columns from** *\<table name>* dialog box that appears when you click **Add**.</span></span> <span data-ttu-id="f5e3a-163">如果是空間索引，在您選取一個資料行之後，此按鈕會呈暗灰色。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-163">For a spatial index, after you select one column, this button is dimmed.</span></span>  
  
 <span data-ttu-id="f5e3a-164">**移除**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-164">**Remove**</span></span>  
 <span data-ttu-id="f5e3a-165">從索引鍵中的參與裡移除選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-165">Removes the selected column from participation in the index key.</span></span>  
  
 <span data-ttu-id="f5e3a-166">**上移**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-166">**Move Up**</span></span>  
 <span data-ttu-id="f5e3a-167">在索引鍵方格中將選取的資料行向上移動。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-167">Moves the selected column up in the index key grid.</span></span>  
  
 <span data-ttu-id="f5e3a-168">**下移**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-168">**Move Down**</span></span>  
 <span data-ttu-id="f5e3a-169">在索引鍵方格中將選取的資料行向下移動。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-169">Moves the selected column down in the index key grid.</span></span>  
  
 <span data-ttu-id="f5e3a-170">**資料行存放區資料行**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-170">**Columnstore columns**</span></span>  
 <span data-ttu-id="f5e3a-171">按一下 [加入]，選取資料行存放區索引的資料行。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-171">Click **Add** to select columns for the columnstore index.</span></span> <span data-ttu-id="f5e3a-172">如需資料行存放區索引的限制，請參閱 [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-172">For limitations on a columnstore index, see [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).</span></span>  
  
 <span data-ttu-id="f5e3a-173">**包含的資料行**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-173">**Included columns**</span></span>  
 <span data-ttu-id="f5e3a-174">在非叢集索引中包含非索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-174">Include nonkey columns in the nonclustered index.</span></span> <span data-ttu-id="f5e3a-175">此選項可藉由在非叢集索引的分葉層級中加入資料行當做非索引鍵資料行，以略過索引鍵大小總計的目前索引限制，以及參與索引鍵的最大資料行數目。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-175">This option allows you to bypass the current index limits on the total size of an index key and the maximum number of columns participating in an index key by adding columns as nonkey columns in the leaf level of the nonclustered index.</span></span> <span data-ttu-id="f5e3a-176">如需詳細資訊，請參閱 [建立內含資料行的索引](create-indexes-with-included-columns.md)</span><span class="sxs-lookup"><span data-stu-id="f5e3a-176">For more information, see [Create Indexes with Included Columns](create-indexes-with-included-columns.md)</span></span>  
  
##  <a name="select-index-columns-dialog-box"></a><a name="Columns"></a> <span data-ttu-id="f5e3a-177">選取 (索引) 資料行對話方塊</span><span class="sxs-lookup"><span data-stu-id="f5e3a-177">Select (Index) Columns Dialog Box</span></span>  
 <span data-ttu-id="f5e3a-178">建立或修改索引時，請使用此頁面來將資料行加入 **[索引屬性一般]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-178">Use this page to add columns to the **Index Properties General** page when creating or modifying an index.</span></span>  
  
 <span data-ttu-id="f5e3a-179">**核取方塊**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-179">**Check box**</span></span>  
 <span data-ttu-id="f5e3a-180">選取以加入資料行。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-180">Select to add columns.</span></span>  
  
 <span data-ttu-id="f5e3a-181">**名稱**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-181">**Name**</span></span>  
 <span data-ttu-id="f5e3a-182">資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-182">Name of the column.</span></span>  
  
 <span data-ttu-id="f5e3a-183">**資料類型**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-183">**Data Type**</span></span>  
 <span data-ttu-id="f5e3a-184">資料行的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-184">The data type of the column.</span></span>  
  
 <span data-ttu-id="f5e3a-185">**Bytes**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-185">**Bytes**</span></span>  
 <span data-ttu-id="f5e3a-186">資料行的大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-186">The size of the column in bytes.</span></span>  
  
 <span data-ttu-id="f5e3a-187">**身分識別**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-187">**Identity**</span></span>  
 <span data-ttu-id="f5e3a-188">針對識別欄位顯示 **[是]** ，若資料行不是識別欄位，就顯示 **[否]** 。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-188">Displays **Yes** for identity columns, and **No** when the column is not an identity column.</span></span>  
  
 <span data-ttu-id="f5e3a-189">**允許 Null**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-189">**Allow Nulls**</span></span>  
 <span data-ttu-id="f5e3a-190">如果資料表定義對於資料行允許 Null 值，就會顯示 **[是]** 。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-190">Displays **Yes** when the table definition allows null values for the column.</span></span> <span data-ttu-id="f5e3a-191">如果資料表定義對於資料行不允許 Null 值，就會顯示 **[否]** 。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-191">Displays **No** when the table definition does not allow nulls for the column.</span></span>  
  
##  <a name="storage-page-options"></a><a name="Storage"></a> <span data-ttu-id="f5e3a-192">儲存頁面選項</span><span class="sxs-lookup"><span data-stu-id="f5e3a-192">Storage Page Options</span></span>  
 <span data-ttu-id="f5e3a-193">使用此頁面來檢視或修改選取之索引的檔案群組或資料分割結構描述屬性。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-193">Use this page to view or modify filegroup or partition scheme properties for the selected index.</span></span> <span data-ttu-id="f5e3a-194">僅顯示與索引類型相關的選項。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-194">Only shows options related to the type of index.</span></span>  
  
 <span data-ttu-id="f5e3a-195">**檔案群組**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-195">**Filegroup**</span></span>  
 <span data-ttu-id="f5e3a-196">在指定的檔案群組中儲存索引。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-196">Stores the index in the specified filegroup.</span></span> <span data-ttu-id="f5e3a-197">清單僅顯示標準 (資料列) 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-197">The list only displays standard (row) filegroups.</span></span> <span data-ttu-id="f5e3a-198">預設清單選取項目為資料庫的 PRIMARY 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-198">The default list selection is the PRIMARY filegroup of the database.</span></span> <span data-ttu-id="f5e3a-199">如需相關資訊，請參閱 [Database Files and Filegroups](../databases/database-files-and-filegroups.md)。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-199">For more information, see [Database Files and Filegroups](../databases/database-files-and-filegroups.md).</span></span>  
  
 <span data-ttu-id="f5e3a-200">**檔案資料流檔案群組**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-200">**Filestream filegroup**</span></span>  
 <span data-ttu-id="f5e3a-201">為 FILESTREAM 資料指定檔案群組。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-201">Specifies the filegroup for FILESTREAM data.</span></span> <span data-ttu-id="f5e3a-202">此清單只會顯示 FILESTREAM 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-202">This list displays only FILESTREAM filegroups.</span></span> <span data-ttu-id="f5e3a-203">預設清單選取項目為資料庫的 PRIMARY FILESTREAM 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-203">The default list selection is the PRIMARY FILESTREAM filegroup.</span></span> <span data-ttu-id="f5e3a-204">如需詳細資訊，請參閱 [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-204">For more information, see [FILESTREAM &#40;SQL Server&#41;](../blob/filestream-sql-server.md).</span></span>  
  
 <span data-ttu-id="f5e3a-205">**分割區配置**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-205">**Partition scheme**</span></span>  
 <span data-ttu-id="f5e3a-206">在資料分割結構描述中儲存索引。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-206">Stores the index in a partition scheme.</span></span> <span data-ttu-id="f5e3a-207">按一下 **[資料分割配置]** 以啟用下列方格。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-207">Clicking **Partition Scheme** enables the grid below.</span></span> <span data-ttu-id="f5e3a-208">預設清單選取項目是用來儲存資料表資料的資料分割配置。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-208">The default list selection is the partition scheme that is used for storing the table data.</span></span> <span data-ttu-id="f5e3a-209">當您在清單中選取不同的資料分割配置時，會更新方格中的資訊。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-209">When you select a different partition scheme in the list, the information in the grid is updated.</span></span> <span data-ttu-id="f5e3a-210">如需詳細資訊，請參閱＜ [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-210">For more information, see [Partitioned Tables and Indexes](../partitions/partitioned-tables-and-indexes.md).</span></span>  
  
 <span data-ttu-id="f5e3a-211">如果資料庫中沒有資料分割結構描述，則無法使用資料分割結構描述選項。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-211">The partition scheme option is unavailable if there are no partition schemes in the database.</span></span>  
  
 <span data-ttu-id="f5e3a-212">**檔案資料流資料分割配置**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-212">**Filestream partition scheme**</span></span>  
 <span data-ttu-id="f5e3a-213">指定資料分割配置的 FILESTREAM 資料。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-213">Specifies the partition scheme for FILESTREAM data.</span></span> <span data-ttu-id="f5e3a-214">資料分割配置必須對稱於在 **[資料分割配置]** 選項中所指定的配置。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-214">The partition scheme must be symmetric with the scheme that is specified in the **Partition scheme** option.</span></span>  
  
 <span data-ttu-id="f5e3a-215">如果資料表不是資料分割，則此欄位空白。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-215">If the table is not partitioned, the field is blank.</span></span>  
  
 <span data-ttu-id="f5e3a-216">**資料分割結構描述參數**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-216">**Partition Scheme Parameter**</span></span>  
 <span data-ttu-id="f5e3a-217">顯示參與資料分割結構描述的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-217">Displays the name of the column that participates in the partition scheme.</span></span>  
  
 <span data-ttu-id="f5e3a-218">**資料表資料行**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-218">**Table Column**</span></span>  
 <span data-ttu-id="f5e3a-219">選取資料表或檢視以對應至資料分割結構描述。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-219">Select the table or view to map to the partition scheme.</span></span>  
  
 <span data-ttu-id="f5e3a-220">**資料行資料類型**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-220">**Column Data Type**</span></span>  
 <span data-ttu-id="f5e3a-221">顯示有關資料行的資料類型資訊。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-221">Displays data type information about the column.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f5e3a-222">如果資料表資料行是計算資料行， **[資料行資料類型]** 就會顯示「計算資料行」。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-222">If the table column is a computed column, **Column Data Type** displays "computed column."</span></span>  
  
 <span data-ttu-id="f5e3a-223">**移動索引時，允許線上處理 DML 陳述式**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-223">**Allow online processing of DML statements while moving the index**</span></span>  
 <span data-ttu-id="f5e3a-224">允許使用者在索引作業期間存取基礎資料表或叢集索引資料，以及與非叢集索引相關聯的任何項目。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-224">Allows users to access the underlying table or clustered index data and any associated nonclustered indexes during the index operation.</span></span> <span data-ttu-id="f5e3a-225">如需詳細資訊，請參閱 [Perform Index Operations Online](perform-index-operations-online.md)。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-225">For more information, see [Perform Index Operations Online](perform-index-operations-online.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f5e3a-226">此選項不適用於 XML 索引，或索引為已停用的叢集索引時亦不適用。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-226">This option is not available for XML indexes, or if the index is a disabled clustered index.</span></span>  
  
 <span data-ttu-id="f5e3a-227">**設定最大平行程度**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-227">**Set maximum degree of parallelism**</span></span>  
 <span data-ttu-id="f5e3a-228">限制平行計畫執行期間要使用的處理器數目。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-228">Limits the number of processors to use during parallel plan execution.</span></span> <span data-ttu-id="f5e3a-229">預設值 (0) 會使用實際可用的 CPU 數目。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-229">The default value, 0, uses the actual number of available CPUs.</span></span> <span data-ttu-id="f5e3a-230">將值設定為 1 會抑制平行計畫的產生；將值設定為大於 1 的數字則會限制單一查詢執行所使用的處理器最大數目。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-230">Setting the value to 1 suppresses parallel plan generation; setting the value to a number greater than 1 restricts the maximum number of processors used by a single query execution.</span></span> <span data-ttu-id="f5e3a-231">此選項僅會在對話方塊處於 **[重建]** 或 **[重新建立]** 狀態時可用。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-231">This option only becomes available if the dialog box is in the **Rebuild** or **Recreate** state.</span></span> <span data-ttu-id="f5e3a-232">如需詳細資訊，請參閱 [設定平行處理原則的最大程度選項來取得最佳效能](../policy-based-management/set-the-max-degree-of-parallelism-option-for-optimal-performance.md)。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-232">For more information, see [Set the Max Degree of Parallelism Option for Optimal Performance](../policy-based-management/set-the-max-degree-of-parallelism-option-for-optimal-performance.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f5e3a-233">如果指定的數值大於可用的 CPU 數目，就會使用可用 CPU 的實際數目。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-233">If a value greater than the number of available CPUs is specified, the actual number of available CPUs is used.</span></span>  
  
##  <a name="spatial-page-index-options"></a><a name="Spatial"></a> <span data-ttu-id="f5e3a-234">空間頁面索引選項</span><span class="sxs-lookup"><span data-stu-id="f5e3a-234">Spatial Page Index Options</span></span>  
 <span data-ttu-id="f5e3a-235">使用 **[空間]** 頁面可檢視或指定空間屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-235">Use the **Spatial** page to view or specify the values of the spatial properties.</span></span> <span data-ttu-id="f5e3a-236">如需詳細資訊，請參閱[空間資料 &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-236">For more information, see [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md).</span></span>  
  
### <a name="bounding-box"></a><span data-ttu-id="f5e3a-237">週框方塊</span><span class="sxs-lookup"><span data-stu-id="f5e3a-237">Bounding Box</span></span>  
 <span data-ttu-id="f5e3a-238">*「週框方塊」* (Bounding Box) 是幾何平面最上層方格的周邊。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-238">The *bounding box* is the perimeter of the top-level grid of a geometric plane.</span></span> <span data-ttu-id="f5e3a-239">週框方塊參數只存在於幾何方格鑲嵌內。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-239">The bounding-box parameters exist only in the geometry grid tessellation.</span></span> <span data-ttu-id="f5e3a-240">如果 **[鑲嵌式配置]** 為 **[地理方格]** ，就無法使用這些參數。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-240">These parameters are unavailable if the **Tessellation Scheme** is **Geography grid**.</span></span>  
  
 <span data-ttu-id="f5e3a-241">此面板會顯示周框方塊的 [ \*\* (] *`X-min`* 、[ *`Y-min`*) \*\* ] 和 [ \*\* (] *`X-max`* *`Y-max`*) \*\*座標。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-241">The panel displays the **(*`X-min`*,*`Y-min`*)** and **(*`X-max`*,*`Y-max`*)** coordinates of the bounding box.</span></span> <span data-ttu-id="f5e3a-242">沒有預設座標值。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-242">There are no default coordinate values.</span></span> <span data-ttu-id="f5e3a-243">因此，當您在 `geometry` 類型資料行上建立新的空間索引時，您必須指定座標值。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-243">Therefore, when you are creating a new spatial index on a `geometry` type column, you must specify the coordinate values.</span></span>  
  
 `X-min`  
 <span data-ttu-id="f5e3a-244">週框方塊左下角的 X 座標。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-244">The X-coordinate of the lower-left corner of the bounding box.</span></span>  
  
 `Y-min`  
 <span data-ttu-id="f5e3a-245">週框方塊左下角的 Y 座標。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-245">The Y-coordinate of the lower-left corner of the bounding box.</span></span>  
  
 `X-max`  
 <span data-ttu-id="f5e3a-246">週框方塊右上角的 X 座標。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-246">The X-coordinate of the upper-right corner of the bounding box.</span></span>  
  
 `Y-max`  
 <span data-ttu-id="f5e3a-247">週框方塊右上角的 Y 座標。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-247">The Y-coordinate of upper-right corner of the bounding box.</span></span>  
  
### <a name="general"></a><span data-ttu-id="f5e3a-248">一般</span><span class="sxs-lookup"><span data-stu-id="f5e3a-248">General</span></span>  
 <span data-ttu-id="f5e3a-249">**鑲嵌式配置**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-249">**Tessellation Scheme**</span></span>  
 <span data-ttu-id="f5e3a-250">表示索引的鑲嵌式配置。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-250">Indicates the tessellation scheme of the index.</span></span> <span data-ttu-id="f5e3a-251">支援的鑲嵌式配置如下所示。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-251">The supported tessellation schemes are as follows.</span></span>  
  
 <span data-ttu-id="f5e3a-252">**幾何方格**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-252">**Geometry grid**</span></span>  
 <span data-ttu-id="f5e3a-253">指定幾何方格鑲嵌式配置，這會套用到 `geometry` 資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-253">Specifies the geometry grid tessellation scheme, which applies to a column of the `geometry` data type.</span></span>  
  
 <span data-ttu-id="f5e3a-254">**幾何自動方格**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-254">**Geometry Auto grid**</span></span>  
 <span data-ttu-id="f5e3a-255">當資料庫相容性層級設定為 110 或更高時， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會啟用這個選項。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-255">This option is enabled for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when database compatibility level is set to 110 or higher.</span></span>  
  
 <span data-ttu-id="f5e3a-256">**[地理方格]**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-256">**Geography grid**</span></span>  
 <span data-ttu-id="f5e3a-257">指定地理方格鑲嵌式配置，這會套用到 **geography** 資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-257">Specifies the geography grid tessellation scheme, which applies to a column of the **geography** data type.</span></span>  
  
 <span data-ttu-id="f5e3a-258">**地理自動方格**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-258">**Geography Auto grid**</span></span>  
 <span data-ttu-id="f5e3a-259">當資料庫相容性層級設定為 110 或更高時， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會啟用這個選項。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-259">This option is enabled for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when database compatibility level is set to 110 or higher.</span></span>  
  
 <span data-ttu-id="f5e3a-260">如需 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 如何實作鑲嵌的資訊，請參閱[空間資料 &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-260">For information about how [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] implements tessellation, see [Spatial Data &#40;SQL Server&#41;](../spatial/spatial-data-sql-server.md).</span></span>  
  
 <span data-ttu-id="f5e3a-261">**每一物件的資料格**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-261">**Cells Per Object**</span></span>  
 <span data-ttu-id="f5e3a-262">指示可用於索引內單一空間物件的鑲嵌式每一物件的資料格數目。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-262">Indicates the number of tessellation cells-per-object that can be used for a single spatial object in the index.</span></span> <span data-ttu-id="f5e3a-263">這個數目可以是 1 和 8192 之間 (含) 的任何整數。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-263">This number can be any integer between 1 and 8192, inclusive.</span></span> <span data-ttu-id="f5e3a-264">當資料庫相容性層級設定為 110 或更高時，舊版的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中的預設值為 16 和 8。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-264">The default is 16, and 8 for earlier versions of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] when database compatibility level is set to 110 or higher.</span></span>  
  
 <span data-ttu-id="f5e3a-265">在最上層，如果物件涵蓋的資料格數目要比 *n*指定的數目還要多，則索引會盡量使用所需的資料格數目來提供完整的最上層鑲嵌。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-265">At the top level, if an object covers more cells than specified by *n*, the indexing uses as many cells as necessary to provide a complete top-level tessellation.</span></span> <span data-ttu-id="f5e3a-266">在這類情況下，物件可能會收到比指定之資料格數目還要多的資料格。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-266">In such cases, an object might receive more than the specified number of cells.</span></span> <span data-ttu-id="f5e3a-267">在此情況下，最大數目就是最上層方格產生的資料格數目，該數目取決於 **[層級 1]** 密度。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-267">In this case, the maximum number is the number of cells generated by the top-level grid, which depends on the **Level 1** density.</span></span>  
  
### <a name="grids"></a><span data-ttu-id="f5e3a-268">方格</span><span class="sxs-lookup"><span data-stu-id="f5e3a-268">Grids</span></span>  
 <span data-ttu-id="f5e3a-269">此面板會顯示鑲嵌式配置之每一個層級上的方格密度。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-269">This panel shows the density of the grid at each level of the tessellation scheme.</span></span> <span data-ttu-id="f5e3a-270">密度會指定為 **[低]** 、 **[中]** 或 **[高]** 。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-270">Density is specified as **Low**, **Medium**, or **High**.</span></span> <span data-ttu-id="f5e3a-271">預設值是 **[中]** 。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-271">The default is **Medium**.</span></span> <span data-ttu-id="f5e3a-272">**[低]** 代表 4x4 個方格 (16 個方格)、 **[中]** 代表 8x8 個方格 (64 個方格)，而 **[高]** 則代表 16x16 個方格 (256 個方格)。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-272">**Low** represents a 4x4 grid (16 cells), **Medium** represents an 8x8 grid (64 cells), and **High** represents a 16x16 grid (256 cells).</span></span> <span data-ttu-id="f5e3a-273">當選擇了 **[幾何自動方格]** 或 **[地理自動方格]** 鑲嵌選項時，就無法使用這些選項。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-273">These options are not available when the **Geometry Auto grid** or **Geography Auto grid** tessellation options are chosen.</span></span>  
  
 <span data-ttu-id="f5e3a-274">**層級 1**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-274">**Level 1**</span></span>  
 <span data-ttu-id="f5e3a-275">第一層 (上層) 方格的密度。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-275">The density of the first-level (top) grid.</span></span>  
  
 <span data-ttu-id="f5e3a-276">**層級 2**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-276">**Level 2**</span></span>  
 <span data-ttu-id="f5e3a-277">第二層方格的密度。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-277">The density of the second-level grid.</span></span>  
  
 <span data-ttu-id="f5e3a-278">**層級 3**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-278">**Level 3**</span></span>  
 <span data-ttu-id="f5e3a-279">第三層方格的密度。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-279">The density of the third-level grid.</span></span>  
  
 <span data-ttu-id="f5e3a-280">**層級 4**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-280">**Level 4**</span></span>  
 <span data-ttu-id="f5e3a-281">第四層方格的密度。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-281">The density of the fourth-level grid.</span></span>  
  
##  <a name="filter-page"></a><a name="Filter"></a> <span data-ttu-id="f5e3a-282">篩選頁面</span><span class="sxs-lookup"><span data-stu-id="f5e3a-282">Filter Page</span></span>  
 <span data-ttu-id="f5e3a-283">使用此頁可輸入篩選索引的篩選述詞。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-283">Use this page to enter the filter predicate for a filtered index.</span></span> <span data-ttu-id="f5e3a-284">如需詳細資訊，請參閱 [Create Filtered Indexes](create-filtered-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-284">For more information, see [Create Filtered Indexes](create-filtered-indexes.md).</span></span>  
  
 <span data-ttu-id="f5e3a-285">**篩選運算式**</span><span class="sxs-lookup"><span data-stu-id="f5e3a-285">**Filter Expression**</span></span>  
 <span data-ttu-id="f5e3a-286">定義要在篩選索引中包含什麼資料列。</span><span class="sxs-lookup"><span data-stu-id="f5e3a-286">Defines which data rows to include in the filtered index.</span></span> <span data-ttu-id="f5e3a-287">例如， `StartDate > '20000101' AND EndDate IS NOT NULL'.`</span><span class="sxs-lookup"><span data-stu-id="f5e3a-287">For example, `StartDate > '20000101' AND EndDate IS NOT NULL'.`</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5e3a-288">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5e3a-288">See Also</span></span>  
 <span data-ttu-id="f5e3a-289">[設定索引選項](set-index-options.md) </span><span class="sxs-lookup"><span data-stu-id="f5e3a-289">[Set Index Options](set-index-options.md) </span></span>  
 <span data-ttu-id="f5e3a-290">[INDEXPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f5e3a-290">[INDEXPROPERTY &#40;Transact-SQL&#41;](/sql/t-sql/functions/indexproperty-transact-sql) </span></span>  
 [<span data-ttu-id="f5e3a-291">sys.indexes &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f5e3a-291">sys.indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)  
  
  
