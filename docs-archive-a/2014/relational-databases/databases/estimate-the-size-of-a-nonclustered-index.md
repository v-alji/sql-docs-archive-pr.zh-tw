---
title: 估計非叢集索引的大小 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], index size
- size [SQL Server], tables
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- clustered indexes, table size
- designing databases [SQL Server], estimating size
- calculating table size
ms.assetid: c183b0e4-ef4c-4bfc-8575-5ac219c25b0a
author: stevestein
ms.author: sstein
ms.openlocfilehash: 097c0e5568ba17b12f83d09e347eb3bf8b0bd7da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705161"
---
# <a name="estimate-the-size-of-a-nonclustered-index"></a><span data-ttu-id="dba81-102">估計非叢集索引的大小</span><span class="sxs-lookup"><span data-stu-id="dba81-102">Estimate the Size of a Nonclustered Index</span></span>
  <span data-ttu-id="dba81-103">請遵循下列步驟來估計儲存非叢集索引所需的空間量：</span><span class="sxs-lookup"><span data-stu-id="dba81-103">Follow these steps to estimate the amount of space that is required to store a nonclustered index:</span></span>  
  
1.  <span data-ttu-id="dba81-104">計算步驟 2 和 3 中所使用的變數。</span><span class="sxs-lookup"><span data-stu-id="dba81-104">Calculate variables for use in steps 2 and 3.</span></span>  
  
2.  <span data-ttu-id="dba81-105">計算在非叢集索引的分葉層級中儲存索引資訊的空間。</span><span class="sxs-lookup"><span data-stu-id="dba81-105">Calculate the space used to store index information in the leaf level of the nonclustered index.</span></span>  
  
3.  <span data-ttu-id="dba81-106">計算在非叢集索引的非分葉層級中儲存索引資訊的空間。</span><span class="sxs-lookup"><span data-stu-id="dba81-106">Calculate the space used to store index information in the non-leaf levels of the nonclustered index.</span></span>  
  
4.  <span data-ttu-id="dba81-107">加總計算的值。</span><span class="sxs-lookup"><span data-stu-id="dba81-107">Total the calculated values.</span></span>  
  
## <a name="step-1-calculate-variables-for-use-in-steps-2-and-3"></a><span data-ttu-id="dba81-108">步驟 1：</span><span class="sxs-lookup"><span data-stu-id="dba81-108">Step 1.</span></span> <span data-ttu-id="dba81-109">計算步驟 2 和 3 中所使用的變數</span><span class="sxs-lookup"><span data-stu-id="dba81-109">Calculate Variables for Use in Steps 2 and 3</span></span>  
 <span data-ttu-id="dba81-110">您可以使用下列步驟來計算變數，以便用於估計儲存索引較高層級所需的空間量。</span><span class="sxs-lookup"><span data-stu-id="dba81-110">You can use the following steps to calculate variables that are used to estimate the amount of space that is required to store the upper levels of the index.</span></span>  
  
1.  <span data-ttu-id="dba81-111">指定資料表中將會有的資料列數目：</span><span class="sxs-lookup"><span data-stu-id="dba81-111">Specify the number of rows that will be present in the table:</span></span>  
  
     <span data-ttu-id="dba81-112">***Num_Rows***  = 資料表中的資料列數目</span><span class="sxs-lookup"><span data-stu-id="dba81-112">***Num_Rows***  = number of rows in the table</span></span>  
  
2.  <span data-ttu-id="dba81-113">指定索引鍵中固定長度和可變長度資料行的數目，並計算儲存它們所需的空間：</span><span class="sxs-lookup"><span data-stu-id="dba81-113">Specify the number of fixed-length and variable-length columns in the index key and calculate the space that is required for their storage:</span></span>  
  
     <span data-ttu-id="dba81-114">索引的索引鍵資料行可以包含固定長度和可變長度的資料行。</span><span class="sxs-lookup"><span data-stu-id="dba81-114">The key columns of an index can include fixed-length and variable-length columns.</span></span> <span data-ttu-id="dba81-115">若要估計內部層級的索引資料列大小，請計算這些資料行群組在索引資料列中佔用的空間。</span><span class="sxs-lookup"><span data-stu-id="dba81-115">To estimate the interior level index row size, calculate the space that each of these groups of columns occupies within the index row.</span></span> <span data-ttu-id="dba81-116">資料行的大小取決於資料類型和長度規格。</span><span class="sxs-lookup"><span data-stu-id="dba81-116">The size of a column depends on the data type and length specification.</span></span>  
  
     <span data-ttu-id="dba81-117">***Num_Key_Cols***  = 索引鍵資料行 (固定長度和可變長度) 總數</span><span class="sxs-lookup"><span data-stu-id="dba81-117">***Num_Key_Cols***  = total number of key columns (fixed-length and variable-length)</span></span>  
  
     <span data-ttu-id="dba81-118">***Num_Key_Cols***  = 所有固定長度索引鍵資料行的總位元組大小</span><span class="sxs-lookup"><span data-stu-id="dba81-118">***Fixed_Key_Size***  = total byte size of all fixed-length key columns</span></span>  
  
     <span data-ttu-id="dba81-119">***Num_Variable_Key_Cols***  = 可變長度索引鍵資料行的數目</span><span class="sxs-lookup"><span data-stu-id="dba81-119">***Num_Variable_Key_Cols***  = number of variable-length key columns</span></span>  
  
     <span data-ttu-id="dba81-120">***Max_Var_Key_Size***  = 所有可變長度索引鍵資料行的最大位元組大小</span><span class="sxs-lookup"><span data-stu-id="dba81-120">***Max_Var_Key_Size***  = maximum byte size of all variable-length key columns</span></span>  
  
3.  <span data-ttu-id="dba81-121">如果索引不是唯一的，就需說明資料列定位器：</span><span class="sxs-lookup"><span data-stu-id="dba81-121">Account for the data row locator that is required if the index is nonunique:</span></span>  
  
     <span data-ttu-id="dba81-122">如果非叢集索引不是唯一的，資料列定位器就會結合非叢集索引鍵，以便針對每個資料列產生唯一的索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="dba81-122">If the nonclustered index is nonunique, the data row locator is combined with the nonclustered index key to produce a unique key value for every row.</span></span>  
  
     <span data-ttu-id="dba81-123">如果非叢集索引是在堆積上，資料列定位器就是堆積 RID。</span><span class="sxs-lookup"><span data-stu-id="dba81-123">If the nonclustered index is over a heap, the data row locator is the heap RID.</span></span> <span data-ttu-id="dba81-124">這是 8 位元組的大小。</span><span class="sxs-lookup"><span data-stu-id="dba81-124">This is a size of 8 bytes.</span></span>  
  
     <span data-ttu-id="dba81-125">***Num_Key_Cols***  = ***Num_Key_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="dba81-125">***Num_Key_Cols***  = ***Num_Key_Cols*** + 1</span></span>  
  
     <span data-ttu-id="dba81-126">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="dba81-126">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 1</span></span>  
  
     <span data-ttu-id="dba81-127">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 8</span><span class="sxs-lookup"><span data-stu-id="dba81-127">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 8</span></span>  
  
     <span data-ttu-id="dba81-128">如果非叢集索引是在叢集索引上，資料列定位器就是叢集索引鍵。</span><span class="sxs-lookup"><span data-stu-id="dba81-128">If the nonclustered index is over a clustered index, the data row locator is the clustering key.</span></span> <span data-ttu-id="dba81-129">必須與非叢集索引鍵結合的資料行是那些在叢集索引鍵中的資料行，這些資料行並未存在於非叢集索引鍵資料行集中。</span><span class="sxs-lookup"><span data-stu-id="dba81-129">The columns that must be combined with the nonclustered index key are those columns in the clustering key that are not already present in the set of nonclustered index key columns.</span></span>  
  
     <span data-ttu-id="dba81-130">***Num_Key_Cols***  = ***Num_Key_Cols*** + 不是位於非叢集索引鍵資料行集中之叢集索引鍵資料行的數目 (如果叢集索引不是唯一的，則 + 1)</span><span class="sxs-lookup"><span data-stu-id="dba81-130">***Num_Key_Cols***  = ***Num_Key_Cols*** + number of clustering key columns not in the set of nonclustered index key columns (+ 1 if the clustered index is nonunique)</span></span>  
  
     <span data-ttu-id="dba81-131">***Fixed_Key_Size***  = ***Fixed_Key_Size*** + 不是位於非叢集索引鍵資料行集中之固定長度叢集索引鍵資料行的總位元組大小</span><span class="sxs-lookup"><span data-stu-id="dba81-131">***Fixed_Key_Size***  = ***Fixed_Key_Size*** + total byte size of fixed-length clustering key columns not in the set of nonclustered index key columns</span></span>  
  
     <span data-ttu-id="dba81-132">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 不是位於非叢集索引鍵資料行集中之可變長度叢集索引鍵資料行的數目 (如果叢集索引不是唯一的，則 + 1)</span><span class="sxs-lookup"><span data-stu-id="dba81-132">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + number of variable-length clustering key columns not in the set of nonclustered index key columns (+ 1 if the clustered index is nonunique)</span></span>  
  
     <span data-ttu-id="dba81-133">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 不是位於非叢集索引鍵資料行集中之可變長度叢集索引鍵資料行的最大位元組大小 (如果叢集索引不是唯一的，則 + 4)</span><span class="sxs-lookup"><span data-stu-id="dba81-133">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + maximum byte size of variable-length clustering key columns not in the set of nonclustered index key columns (+ 4 if the clustered index is nonunique)</span></span>  
  
4.  <span data-ttu-id="dba81-134">資料列的一部分，又稱為 Null 點陣圖，可用以管理資料行的 Null 屬性。</span><span class="sxs-lookup"><span data-stu-id="dba81-134">Part of the row, known as the null bitmap, may be reserved to manage column nullability.</span></span> <span data-ttu-id="dba81-135">計算它的大小：</span><span class="sxs-lookup"><span data-stu-id="dba81-135">Calculate its size:</span></span>  
  
     <span data-ttu-id="dba81-136">如果索引鍵中有可為 Null 資料行，包含步驟 1、3 中所描述的任何所需叢集索引鍵資料行，一部分的索引資料列將保留做為 Null 點陣圖。</span><span class="sxs-lookup"><span data-stu-id="dba81-136">If there are nullable columns in the index key, including any necessary clustering key columns as described in Step 1.3, part of the index row is reserved for the null bitmap.</span></span>  
  
     <span data-ttu-id="dba81-137">***Index_Null_Bitmap***  = 2 + ((索引資料列中的資料行數目 + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="dba81-137">***Index_Null_Bitmap***  = 2 + ((number of columns in the index row + 7) / 8)</span></span>  
  
     <span data-ttu-id="dba81-138">您應該僅使用先前運算式的整數部分。</span><span class="sxs-lookup"><span data-stu-id="dba81-138">Only the integer part of the previous expression should be used.</span></span> <span data-ttu-id="dba81-139">請捨去任何餘數。</span><span class="sxs-lookup"><span data-stu-id="dba81-139">Discard any remainder.</span></span>  
  
     <span data-ttu-id="dba81-140">如果沒有可為 Null 的索引鍵資料行，請將 ***Index_Null_Bitmap*** 設成 0。</span><span class="sxs-lookup"><span data-stu-id="dba81-140">If there are no nullable key columns, set ***Index_Null_Bitmap*** to 0.</span></span>  
  
5.  <span data-ttu-id="dba81-141">計算可變長度的資料大小：</span><span class="sxs-lookup"><span data-stu-id="dba81-141">Calculate the variable length data size:</span></span>  
  
     <span data-ttu-id="dba81-142">如果在索引鍵中有可變長度的資料行，包含任何所需的叢集索引鍵資料行，請決定在索引資料列中儲存資料行所需的空間。</span><span class="sxs-lookup"><span data-stu-id="dba81-142">If there are variable-length columns in the index key, including any necessary clustered index key columns, determine how much space is used to store the columns within the index row:</span></span>  
  
     <span data-ttu-id="dba81-143">***Variable_Key_Size***  = 2 + (***Num_Variable_Key_Cols*** x 2) + ***Max_Var_Key_Size***</span><span class="sxs-lookup"><span data-stu-id="dba81-143">***Variable_Key_Size***  = 2 + (***Num_Variable_Key_Cols*** x 2) + ***Max_Var_Key_Size***</span></span>  
  
     <span data-ttu-id="dba81-144">加入 ***Max_Var_Key_Size*** 的位元組是用於追蹤每個變數資料行。這個公式假設所有可變長度的資料行是 100% 填滿的。</span><span class="sxs-lookup"><span data-stu-id="dba81-144">The bytes added to ***Max_Var_Key_Size*** are for tracking each variable column.This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="dba81-145">如果您預期可變長度資料行所使用的儲存空間百分比會比較小，您可以經由調整百分比所得的 ***Max_Var_Key_Size*** 值，產生更精確的整體資料表大小之估計。</span><span class="sxs-lookup"><span data-stu-id="dba81-145">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Key_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
     <span data-ttu-id="dba81-146">若沒有可變長度的資料行，請將 ***Variable_Key_Size*** 設成 0。</span><span class="sxs-lookup"><span data-stu-id="dba81-146">If there are no variable-length columns, set ***Variable_Key_Size*** to 0.</span></span>  
  
6.  <span data-ttu-id="dba81-147">計算索引資料列的大小：</span><span class="sxs-lookup"><span data-stu-id="dba81-147">Calculate the index row size:</span></span>  
  
     <span data-ttu-id="dba81-148">***Index_Row_Size***  = ***Fixed_Key_Size*** + ***Variable_Key_Size*** + ***Index_Null_Bitmap*** + 1 (索引資料列的資料列標頭上方) + 6 (子頁面識別碼指標)</span><span class="sxs-lookup"><span data-stu-id="dba81-148">***Index_Row_Size***  = ***Fixed_Key_Size*** + ***Variable_Key_Size*** + ***Index_Null_Bitmap*** + 1 (for row header overhead of an index row) + 6 (for the child page ID pointer)</span></span>  
  
7.  <span data-ttu-id="dba81-149">計算每個分頁的索引資料列數目 (每個分頁包含 8096 個可用位元組)：</span><span class="sxs-lookup"><span data-stu-id="dba81-149">Calculate the number of index rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="dba81-150">***Index_Rows_Per_Page***  = 8096 / (***Index_Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="dba81-150">***Index_Rows_Per_Page***  = 8096 / (***Index_Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="dba81-151">由於索引資料列並不會跨越分頁，因此每個分頁索引資料列的數目應該捨去小數，而取最接近的整數列數。</span><span class="sxs-lookup"><span data-stu-id="dba81-151">Because index rows do not span pages, the number of index rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="dba81-152">公式中的 2 是給分頁位置陣列中的該資料列項目。</span><span class="sxs-lookup"><span data-stu-id="dba81-152">The 2 in the formula is for the row's entry in the page's slot array.</span></span>  
  
## <a name="step-2-calculate-the-space-used-to-store-index-information-in-the-leaf-level"></a><span data-ttu-id="dba81-153">步驟 2：</span><span class="sxs-lookup"><span data-stu-id="dba81-153">Step 2.</span></span> <span data-ttu-id="dba81-154">計算在分葉層級中儲存索引資訊所用的空間</span><span class="sxs-lookup"><span data-stu-id="dba81-154">Calculate the Space Used to Store Index Information in the Leaf Level</span></span>  
 <span data-ttu-id="dba81-155">您可以使用下列步驟來估計儲存索引分葉層級所需的空間量。</span><span class="sxs-lookup"><span data-stu-id="dba81-155">You can use the following steps to estimate the amount of space that is required to store the leaf level of the index.</span></span> <span data-ttu-id="dba81-156">您將需要步驟 1 中所保留的值以計算此步驟。</span><span class="sxs-lookup"><span data-stu-id="dba81-156">You will need the values preserved from Step 1 to complete this step.</span></span>  
  
1.  <span data-ttu-id="dba81-157">指定在分葉層級的固定長度和可變長度的資料行數目，並計算儲存它們所需的空間：</span><span class="sxs-lookup"><span data-stu-id="dba81-157">Specify the number of fixed-length and variable-length columns at the leaf level and calculate the space that is required for their storage:</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dba81-158">除了索引鍵資料行之外，包含非索引鍵資料行將可擴充非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="dba81-158">You can extend a nonclustered index by including nonkey columns in addition to the index key columns.</span></span> <span data-ttu-id="dba81-159">這些額外的資料行只會儲存在非叢集索引的分葉層級。</span><span class="sxs-lookup"><span data-stu-id="dba81-159">These additional columns are only stored at the leaf level of the nonclustered index.</span></span> <span data-ttu-id="dba81-160">如需詳細資訊，請參閱 [建立內含資料行的索引](../indexes/create-indexes-with-included-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="dba81-160">For more information, see [Create Indexes with Included Columns](../indexes/create-indexes-with-included-columns.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="dba81-161">您可以結合使定義的資料表總寬度超過 8,060 個位元組的 `varchar`、`nvarchar`、`varbinary` 或 `sql_variant` 資料行。</span><span class="sxs-lookup"><span data-stu-id="dba81-161">You can combine `varchar`, `nvarchar`, `varbinary`, or `sql_variant` columns that cause the total defined table width to exceed 8,060 bytes.</span></span> <span data-ttu-id="dba81-162">這些資料行的每個長度必須仍然在 `varchar`、`varbinary` 或 `sql_variant` 資料行的 8,000 個位元組限制內，以及 `nvarchar` 資料行的 4,000 個位元組限制。</span><span class="sxs-lookup"><span data-stu-id="dba81-162">The length of each one of these columns must still fall within the limit of 8,000 bytes for a `varchar`, `varbinary`, or `sql_variant` column, and 4,000 bytes for `nvarchar` columns.</span></span> <span data-ttu-id="dba81-163">然而，結合的寬度可能超過資料表中 8,060 位元組的限制。</span><span class="sxs-lookup"><span data-stu-id="dba81-163">However, their combined widths may exceed the 8,060 byte limit in a table.</span></span> <span data-ttu-id="dba81-164">這也適用於已包含資料行的非叢集索引分葉資料列。</span><span class="sxs-lookup"><span data-stu-id="dba81-164">This also applies to nonclustered index leaf rows that have included columns.</span></span>  
  
     <span data-ttu-id="dba81-165">如果非叢集索引沒有任何內含的資料行，請使用步驟 1 的值，包含步驟 1、3 中所決定的任何修改：</span><span class="sxs-lookup"><span data-stu-id="dba81-165">If the nonclustered index does not have any included columns, use the values from Step 1, including any modifications determined in Step 1.3:</span></span>  
  
     <span data-ttu-id="dba81-166">***Num_Leaf_Cols***  = ***Num_Key_Cols***</span><span class="sxs-lookup"><span data-stu-id="dba81-166">***Num_Leaf_Cols***  = ***Num_Key_Cols***</span></span>  
  
     <span data-ttu-id="dba81-167">***Fixed_Leaf_Size***  = ***Fixed_Key_Size***</span><span class="sxs-lookup"><span data-stu-id="dba81-167">***Fixed_Leaf_Size***  = ***Fixed_Key_Size***</span></span>  
  
     <span data-ttu-id="dba81-168">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Key_Cols***</span><span class="sxs-lookup"><span data-stu-id="dba81-168">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Key_Cols***</span></span>  
  
     <span data-ttu-id="dba81-169">***Max_Var_Leaf_Size***  = ***Max_Var_Key_Size***</span><span class="sxs-lookup"><span data-stu-id="dba81-169">***Max_Var_Leaf_Size***  = ***Max_Var_Key_Size***</span></span>  
  
     <span data-ttu-id="dba81-170">如果非叢集索引沒有任何內含的資料行，請加入適當的值至步驟 1 的值中，包含在步驟 1、3 中所做的任何修改。</span><span class="sxs-lookup"><span data-stu-id="dba81-170">If the nonclustered index does have included columns, add the appropriate values to the values from Step 1, including any modifications in Step 1.3.</span></span> <span data-ttu-id="dba81-171">資料行的大小取決於資料類型和長度規格。</span><span class="sxs-lookup"><span data-stu-id="dba81-171">The size of a column depends on the data type and length specification.</span></span> <span data-ttu-id="dba81-172">如需詳細資訊，請參閱[資料類型 &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="dba81-172">For more information, see [Data Types &#40;Transact-SQL&#41;](/sql/t-sql/data-types/data-types-transact-sql).</span></span>  
  
     <span data-ttu-id="dba81-173">***Num_Leaf_Cols***  = ***Num_Key_Cols*** + 內含資料行的數目</span><span class="sxs-lookup"><span data-stu-id="dba81-173">***Num_Leaf_Cols***  = ***Num_Key_Cols*** + number of included columns</span></span>  
  
     <span data-ttu-id="dba81-174">***Fixed_Leaf_Size***  = ***Fixed_Key_Size*** + 固定長度內含資料行的總位元組大小</span><span class="sxs-lookup"><span data-stu-id="dba81-174">***Fixed_Leaf_Size***  = ***Fixed_Key_Size*** + total byte size of fixed-length included columns</span></span>  
  
     <span data-ttu-id="dba81-175">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Key_Cols*** + 可變長度內含資料行的數目</span><span class="sxs-lookup"><span data-stu-id="dba81-175">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Key_Cols*** + number of variable-length included columns</span></span>  
  
     <span data-ttu-id="dba81-176">***Max_Var_Leaf_Size***  = ***Max_Var_Key_Size*** + 可變長度內含資料行的最大位元組大小</span><span class="sxs-lookup"><span data-stu-id="dba81-176">***Max_Var_Leaf_Size***  = ***Max_Var_Key_Size*** + maximum byte size of variable-length included columns</span></span>  
  
2.  <span data-ttu-id="dba81-177">說明資料列定位器：</span><span class="sxs-lookup"><span data-stu-id="dba81-177">Account for the data row locator:</span></span>  
  
     <span data-ttu-id="dba81-178">如果非叢集索引不是唯一的，由於資料列定位器的負擔在步驟 1、3 中已經考慮進去，因此不需要再做其他的修改。</span><span class="sxs-lookup"><span data-stu-id="dba81-178">If the nonclustered index is nonunique, the overhead for the data row locator has already been considered in Step 1.3 and no additional modifications are required.</span></span> <span data-ttu-id="dba81-179">到下一個步驟。</span><span class="sxs-lookup"><span data-stu-id="dba81-179">Go to the next step.</span></span>  
  
     <span data-ttu-id="dba81-180">如果非叢集索引是唯一的，在分葉層級的所有資料列中必須說明資料列定位器。</span><span class="sxs-lookup"><span data-stu-id="dba81-180">If the nonclustered index is unique, the data row locator must be accounted for in all rows at the leaf level.</span></span>  
  
     <span data-ttu-id="dba81-181">如果非叢集索引是在堆積上，資料列定位器就是堆積 RID (大小是 8 位元組)。</span><span class="sxs-lookup"><span data-stu-id="dba81-181">If the nonclustered index is over a heap, the data row locator is the heap RID (size 8 bytes).</span></span>  
  
     <span data-ttu-id="dba81-182">***Num_Leaf_Cols***  = ***Num_Leaf_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="dba81-182">***Num_Leaf_Cols***  = ***Num_Leaf_Cols*** + 1</span></span>  
  
     <span data-ttu-id="dba81-183">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Leaf_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="dba81-183">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Leaf_Cols*** + 1</span></span>  
  
     <span data-ttu-id="dba81-184">***Max_Var_Leaf_Size***  = ***Max_Var_Leaf_Size*** + 8</span><span class="sxs-lookup"><span data-stu-id="dba81-184">***Max_Var_Leaf_Size***  = ***Max_Var_Leaf_Size*** + 8</span></span>  
  
     <span data-ttu-id="dba81-185">如果非叢集索引是在叢集索引上，資料列定位器就是叢集索引鍵。</span><span class="sxs-lookup"><span data-stu-id="dba81-185">If the nonclustered index is over a clustered index, the data row locator is the clustering key.</span></span> <span data-ttu-id="dba81-186">必須與非叢集索引鍵結合的資料行是那些在叢集索引鍵中的資料行，這些資料行並未存在於非叢集索引鍵資料行集中。</span><span class="sxs-lookup"><span data-stu-id="dba81-186">The columns that must be combined with the nonclustered index key are those columns in the clustering key that are not already present in the set of nonclustered index key columns.</span></span>  
  
     <span data-ttu-id="dba81-187">***Num_Leaf_Cols***  = ***Num_Leaf_Cols*** + 不是位於非叢集索引鍵資料行集中之叢集索引鍵資料行的數目 (如果叢集索引不是唯一的，則 + 1)</span><span class="sxs-lookup"><span data-stu-id="dba81-187">***Num_Leaf_Cols***  = ***Num_Leaf_Cols*** + number of clustering key columns not in the set of nonclustered index key columns (+ 1 if the clustered index is nonunique)</span></span>  
  
     <span data-ttu-id="dba81-188">***Fixed_Leaf_Size***  = ***Fixed_Leaf_Size*** + 不是位於非叢集索引鍵資料行集中之固定長度叢集索引鍵資料行的數目</span><span class="sxs-lookup"><span data-stu-id="dba81-188">***Fixed_Leaf_Size***  = ***Fixed_Leaf_Size*** + number of fixed-length clustering key columns not in the set of nonclustered index key columns</span></span>  
  
     <span data-ttu-id="dba81-189">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Leaf_Cols*** + 不是位於非叢集索引鍵資料行集中之可變長度叢集索引鍵資料行的數目 (如果叢集索引不是唯一的，則 + 1)</span><span class="sxs-lookup"><span data-stu-id="dba81-189">***Num_Variable_Leaf_Cols***  = ***Num_Variable_Leaf_Cols*** + number of variable-length clustering key columns not in the set of nonclustered index key columns (+ 1 if the clustered index is nonunique)</span></span>  
  
     <span data-ttu-id="dba81-190">***Max_Var_Leaf_Size***  = ***Max_Var_Leaf_Size*** + 不是位於非叢集索引鍵資料行集中之可變長度叢集索引鍵資料行的位元組大小 (如果叢集索引不是唯一的，則 + 4)</span><span class="sxs-lookup"><span data-stu-id="dba81-190">***Max_Var_Leaf_Size***  = ***Max_Var_Leaf_Size*** + size in bytes of the variable-length clustering key columns not in the set of nonclustered index key columns (+ 4 if the clustered index is nonunique)</span></span>  
  
3.  <span data-ttu-id="dba81-191">計算 Null 點陣圖大小：</span><span class="sxs-lookup"><span data-stu-id="dba81-191">Calculate the null bitmap size:</span></span>  
  
     <span data-ttu-id="dba81-192">***Leaf_Null_Bitmap***  = 2 + ((***Num_Leaf_Cols*** + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="dba81-192">***Leaf_Null_Bitmap***  = 2 + ((***Num_Leaf_Cols*** + 7) / 8)</span></span>  
  
     <span data-ttu-id="dba81-193">您應該僅使用先前運算式的整數部分。</span><span class="sxs-lookup"><span data-stu-id="dba81-193">Only the integer part of the previous expression should be used.</span></span> <span data-ttu-id="dba81-194">請捨去任何餘數。</span><span class="sxs-lookup"><span data-stu-id="dba81-194">Discard any remainder.</span></span>  
  
4.  <span data-ttu-id="dba81-195">計算可變長度的資料大小：</span><span class="sxs-lookup"><span data-stu-id="dba81-195">Calculate the variable length data size:</span></span>  
  
     <span data-ttu-id="dba81-196">如果在索引鍵中有可變長度的資料行，包含先前步驟 2.2 中所描述的任何所需叢集索引鍵資料行，請決定在索引資料列中儲存資料行所需的空間。</span><span class="sxs-lookup"><span data-stu-id="dba81-196">If there are variable-length columns in the index key, including any necessary clustering key columns as described previously in Step 2.2, determine how much space is used to store the columns within the index row:</span></span>  
  
     <span data-ttu-id="dba81-197">***Variable_Leaf_Size***  = 2 + (***Num_Variable_Leaf_Cols*** x 2) + ***Max_Var_Leaf_Size***</span><span class="sxs-lookup"><span data-stu-id="dba81-197">***Variable_Leaf_Size***  = 2 + (***Num_Variable_Leaf_Cols*** x 2) + ***Max_Var_Leaf_Size***</span></span>  
  
     <span data-ttu-id="dba81-198">加入 ***Max_Var_Key_Size*** 的位元組是用於追蹤每個變數資料行。這個公式假設所有可變長度的資料行是 100% 填滿的。</span><span class="sxs-lookup"><span data-stu-id="dba81-198">The bytes added to ***Max_Var_Key_Size*** are for tracking each variable column.This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="dba81-199">如果您預期可變長度資料行所使用的儲存空間百分比會比較小，您可以經由調整百分比所得的 ***Max_Var_Leaf_Size*** 值，產生更精確的整體資料表大小之估計。</span><span class="sxs-lookup"><span data-stu-id="dba81-199">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Leaf_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
     <span data-ttu-id="dba81-200">如果沒有可變長度的資料行，請將 ***Variable_Leaf_Size*** 設成 0。</span><span class="sxs-lookup"><span data-stu-id="dba81-200">If there are no variable-length columns, set ***Variable_Leaf_Size*** to 0.</span></span>  
  
5.  <span data-ttu-id="dba81-201">計算索引資料列的大小：</span><span class="sxs-lookup"><span data-stu-id="dba81-201">Calculate the index row size:</span></span>  
  
     <span data-ttu-id="dba81-202">***Leaf_Row_Size***   = ***Fixed_Leaf_Size***  + ***Variable_Leaf_Size***  + ***Leaf_Null_Bitmap*** + 1 (索引資料列的資料列行首的額外負荷) + 6 (子頁面識別碼指標) </span><span class="sxs-lookup"><span data-stu-id="dba81-202">***Leaf_Row_Size***  = ***Fixed_Leaf_Size*** + ***Variable_Leaf_Size*** + ***Leaf_Null_Bitmap*** + 1 (for row header overhead of an index row) + 6 (for the child page ID pointer)</span></span>  
  
6.  <span data-ttu-id="dba81-203">計算每個分頁的索引資料列數目 (每個分頁包含 8096 個可用位元組)：</span><span class="sxs-lookup"><span data-stu-id="dba81-203">Calculate the number of index rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="dba81-204">***Leaf_Rows_Per_Page***  = 8096 / (***Leaf_Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="dba81-204">***Leaf_Rows_Per_Page***  = 8096 / (***Leaf_Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="dba81-205">由於索引資料列並不會跨越分頁，因此每個分頁索引資料列的數目應該捨去小數，而取最接近的整數列數。</span><span class="sxs-lookup"><span data-stu-id="dba81-205">Because index rows do not span pages, the number of index rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="dba81-206">公式中的 2 是給分頁位置陣列中的該資料列項目。</span><span class="sxs-lookup"><span data-stu-id="dba81-206">The 2 in the formula is for the row's entry in the page's slot array.</span></span>  
  
7.  <span data-ttu-id="dba81-207">根據指定的 [填滿因數](../indexes/specify-fill-factor-for-an-index.md) ，計算每個分頁所保留的可用資料列數目：</span><span class="sxs-lookup"><span data-stu-id="dba81-207">Calculate the number of reserved free rows per page, based on the [fill factor](../indexes/specify-fill-factor-for-an-index.md) specified:</span></span>  
  
     <span data-ttu-id="dba81-208">***Free_Rows_Per_Page***  = 8096 x ((100 - ***Fill_Factor***) / 100) / (***Leaf_Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="dba81-208">***Free_Rows_Per_Page***  = 8096 x ((100 - ***Fill_Factor***) / 100) / (***Leaf_Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="dba81-209">計算中所使用的填滿因數是整數值而不是百分比。</span><span class="sxs-lookup"><span data-stu-id="dba81-209">The fill factor used in the calculation is an integer value instead of a percentage.</span></span> <span data-ttu-id="dba81-210">因為資料列不能跨頁，每個分頁的資料列數目必須無條件捨去小數，而取最接近的整數資料列。</span><span class="sxs-lookup"><span data-stu-id="dba81-210">Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="dba81-211">當填滿因數變大時，每個分頁上會儲存更多資料，分頁也會比較少。</span><span class="sxs-lookup"><span data-stu-id="dba81-211">As the fill factor grows, more data will be stored on each page and there will be fewer pages.</span></span> <span data-ttu-id="dba81-212">公式中的 2 是給分頁位置陣列中的該資料列項目。</span><span class="sxs-lookup"><span data-stu-id="dba81-212">The 2 in the formula is for the row's entry in the page's slot array.</span></span>  
  
8.  <span data-ttu-id="dba81-213">計算儲存所有資料列所需的分頁數目：</span><span class="sxs-lookup"><span data-stu-id="dba81-213">Calculate the number of pages required to store all the rows:</span></span>  
  
     <span data-ttu-id="dba81-214">***Num_Leaf_Pages***  = ***Num_Rows*** / (***Leaf_Rows_Per_Page*** - ***Free_Rows_Per_Page***)</span><span class="sxs-lookup"><span data-stu-id="dba81-214">***Num_Leaf_Pages***  = ***Num_Rows*** / (***Leaf_Rows_Per_Page*** - ***Free_Rows_Per_Page***)</span></span>  
  
     <span data-ttu-id="dba81-215">估計的分頁數目應該要將小數進位到最接近的整分頁數。</span><span class="sxs-lookup"><span data-stu-id="dba81-215">The number of pages estimated should be rounded up to the nearest whole page.</span></span>  
  
9. <span data-ttu-id="dba81-216">計算索引的大小 (每個分頁共有 8192 個位元組)：</span><span class="sxs-lookup"><span data-stu-id="dba81-216">Calculate the size of the index (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="dba81-217">***Leaf_Space_Used***  = 8192 x ***Num_Leaf_Pages***</span><span class="sxs-lookup"><span data-stu-id="dba81-217">***Leaf_Space_Used***  = 8192 x ***Num_Leaf_Pages***</span></span>  
  
## <a name="step-3-calculate-the-space-used-to-store-index-information-in-the-non-leaf-levels"></a><span data-ttu-id="dba81-218">步驟 3：</span><span class="sxs-lookup"><span data-stu-id="dba81-218">Step 3.</span></span> <span data-ttu-id="dba81-219">計算在非分葉層級中儲存索引資訊所用的空間</span><span class="sxs-lookup"><span data-stu-id="dba81-219">Calculate the Space Used to Store Index Information in the Non-leaf Levels</span></span>  
 <span data-ttu-id="dba81-220">請遵循下列步驟來估計儲存索引之中繼和根層級所需的空間量。</span><span class="sxs-lookup"><span data-stu-id="dba81-220">Follow these steps to estimate the amount of space that is required to store the intermediate and root levels of the index.</span></span> <span data-ttu-id="dba81-221">您將需要步驟 2 和 3 中所保留的值來完成此步驟。</span><span class="sxs-lookup"><span data-stu-id="dba81-221">You will need the values preserved from steps 2 and 3 to complete this step.</span></span>  
  
1.  <span data-ttu-id="dba81-222">計算索引中的非分葉層級數目：</span><span class="sxs-lookup"><span data-stu-id="dba81-222">Calculate the number of non-leaf levels in the index:</span></span>  
  
     <span data-ttu-id="dba81-223">***非分葉層級***= 1 + log Index_Rows_Per_Page (***Num_Leaf_Pages***  /  ***Index_Rows_Per_Page***) </span><span class="sxs-lookup"><span data-stu-id="dba81-223">***Non-leaf Levels***  = 1 + log Index_Rows_Per_Page (***Num_Leaf_Pages*** / ***Index_Rows_Per_Page***)</span></span>  
  
     <span data-ttu-id="dba81-224">將這個值無條件向上進位到最近的整數。</span><span class="sxs-lookup"><span data-stu-id="dba81-224">Round this value up to the nearest whole number.</span></span> <span data-ttu-id="dba81-225">此值不包含非叢集索引的分葉層級。</span><span class="sxs-lookup"><span data-stu-id="dba81-225">This value does not include the leaf level of the nonclustered index.</span></span>  
  
2.  <span data-ttu-id="dba81-226">計算索引中的非分葉頁面數目：</span><span class="sxs-lookup"><span data-stu-id="dba81-226">Calculate the number of non-leaf pages in the index:</span></span>  
  
     <span data-ttu-id="dba81-227">***Num_Index_Pages*** = ∑層級 (***Num_Leaf_Pages/Index_Rows_Per_Page***<sup>層級</sup>) 其中 1 <= 層級 <=***層***級</span><span class="sxs-lookup"><span data-stu-id="dba81-227">***Num_Index_Pages***  = ∑Level (***Num_Leaf_Pages/Index_Rows_Per_Page***<sup>Level</sup>)where 1 <= Level <= ***Levels***</span></span>  
  
     <span data-ttu-id="dba81-228">將每個被加數無條件向上進位到最近的整數。</span><span class="sxs-lookup"><span data-stu-id="dba81-228">Round each summand up to the nearest whole number.</span></span> <span data-ttu-id="dba81-229">簡單舉例說明，假設有個索引，其中 ***Num_Leaf_Pages*** = 1000 和 ***Index_Rows_Per_Page*** = 25。</span><span class="sxs-lookup"><span data-stu-id="dba81-229">As a simple example, consider an index where ***Num_Leaf_Pages*** = 1000 and ***Index_Rows_Per_Page*** = 25.</span></span> <span data-ttu-id="dba81-230">分葉層級上方的第一個索引層級會儲存 1000 個索引資料列，這是每個分葉頁面的一個索引資料列，而且每個頁面可以容納 25 個索引資料列。</span><span class="sxs-lookup"><span data-stu-id="dba81-230">The first index level above the leaf level stores 1000 index rows, which is one index row per leaf page, and 25 index rows can fit per page.</span></span> <span data-ttu-id="dba81-231">這表示儲存這 1000 個索引資料列需要 40 頁。</span><span class="sxs-lookup"><span data-stu-id="dba81-231">This means that 40 pages are required to store those 1000 index rows.</span></span> <span data-ttu-id="dba81-232">索引的下一個層級必須儲存 40 個資料列，</span><span class="sxs-lookup"><span data-stu-id="dba81-232">The next level of the index has to store 40 rows.</span></span> <span data-ttu-id="dba81-233">這表示它需要 2 頁。</span><span class="sxs-lookup"><span data-stu-id="dba81-233">This means that it requires 2 pages.</span></span> <span data-ttu-id="dba81-234">索引的最後一個層級必須儲存 2 個資料列。</span><span class="sxs-lookup"><span data-stu-id="dba81-234">The final level of the index has to store 2 rows.</span></span> <span data-ttu-id="dba81-235">這表示它需要 1 頁。</span><span class="sxs-lookup"><span data-stu-id="dba81-235">This means that it requires 1 page.</span></span> <span data-ttu-id="dba81-236">這會產生 43 個非分葉索引頁面。</span><span class="sxs-lookup"><span data-stu-id="dba81-236">This yields 43 non-leaf index pages.</span></span> <span data-ttu-id="dba81-237">在上述公式中使用這些數字時，結果如下：</span><span class="sxs-lookup"><span data-stu-id="dba81-237">When these numbers are used in the previous formulas, the result is as follows:</span></span>  
  
     <span data-ttu-id="dba81-238">***非 leaf_Levels*** = 1 + log25 (1000/25) = 3</span><span class="sxs-lookup"><span data-stu-id="dba81-238">***Non-leaf_Levels***  = 1 + log25 (1000 / 25) = 3</span></span>  
  
     <span data-ttu-id="dba81-239">***Num_Index_Pages*** = 1000/ (25<sup>3</sup>) + 1000/ (25<sup>2</sup>) + 1000/ (25<sup>1</sup>) = 1 + 2 + 40 = 43，這是範例中所描述的頁面數目。</span><span class="sxs-lookup"><span data-stu-id="dba81-239">***Num_Index_Pages*** = 1000/(25<sup>3</sup>)+ 1000/(25<sup>2</sup>) + 1000/(25<sup>1</sup>) = 1 + 2 + 40 = 43, which is the number of pages described in the example.</span></span>  
  
3.  <span data-ttu-id="dba81-240">計算索引的大小 (每個分頁共有 8192 個位元組)：</span><span class="sxs-lookup"><span data-stu-id="dba81-240">Calculate the size of the index (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="dba81-241">***Index_Space_Used***  = 8192 x ***Num_Index_Pages***</span><span class="sxs-lookup"><span data-stu-id="dba81-241">***Index_Space_Used***  = 8192 x ***Num_Index_Pages***</span></span>  
  
## <a name="step-4-total-the-calculated-values"></a><span data-ttu-id="dba81-242">步驟 4：</span><span class="sxs-lookup"><span data-stu-id="dba81-242">Step 4.</span></span> <span data-ttu-id="dba81-243">加總計算的值</span><span class="sxs-lookup"><span data-stu-id="dba81-243">Total the Calculated Values</span></span>  
 <span data-ttu-id="dba81-244">將前兩個步驟所取得的值加總：</span><span class="sxs-lookup"><span data-stu-id="dba81-244">Total the values obtained from the previous two steps:</span></span>  
  
 <span data-ttu-id="dba81-245">非叢集索引大小 (位元組) = ***Leaf_Space_Used*** + ***Index_Space_used***</span><span class="sxs-lookup"><span data-stu-id="dba81-245">Nonclustered index size (bytes) = ***Leaf_Space_Used*** + ***Index_Space_used***</span></span>  
  
 <span data-ttu-id="dba81-246">上述計算未考慮下列項目：</span><span class="sxs-lookup"><span data-stu-id="dba81-246">This calculation does not consider the following:</span></span>  
  
-   <span data-ttu-id="dba81-247">資料分割</span><span class="sxs-lookup"><span data-stu-id="dba81-247">Partitioning</span></span>  
  
     <span data-ttu-id="dba81-248">從資料分割而來的空間負擔非常小，但是計算起來很複雜。</span><span class="sxs-lookup"><span data-stu-id="dba81-248">The space overhead from partitioning is minimal, but complex to calculate.</span></span> <span data-ttu-id="dba81-249">不一定要包含它。</span><span class="sxs-lookup"><span data-stu-id="dba81-249">It is not important to include.</span></span>  
  
-   <span data-ttu-id="dba81-250">配置頁面</span><span class="sxs-lookup"><span data-stu-id="dba81-250">Allocation pages</span></span>  
  
     <span data-ttu-id="dba81-251">至少有一個 IAM 頁面用以追蹤配置到堆積的頁面，但是空間負擔非常小，而且沒有演算法來決定性地計算要使用多少 IAM 頁面。</span><span class="sxs-lookup"><span data-stu-id="dba81-251">There is at least one IAM page used to track the pages allocated to a heap, but the space overhead is minimal and there is no algorithm to deterministically calculate exactly how many IAM pages will be used.</span></span>  
  
-   <span data-ttu-id="dba81-252">大型物件 (LOB) 值</span><span class="sxs-lookup"><span data-stu-id="dba81-252">Large object (LOB) values</span></span>  
  
     <span data-ttu-id="dba81-253">決定到底要使用多少空間來儲存 LOB 資料類型 `varchar(max)`、`varbinary(max)`、`nvarchar(max)`、`text`、`ntext`、`xml` 以及 `image` 值的演算法是很複雜的。</span><span class="sxs-lookup"><span data-stu-id="dba81-253">The algorithm to determine exactly how much space will be used to store the LOB data types `varchar(max)`, `varbinary(max)`, `nvarchar(max)`, `text`, `ntext`, `xml`, and `image` values is complex.</span></span> <span data-ttu-id="dba81-254">只要加上預期的 LOB 值平均大小，乘以 ***Num_Rows***，再將此值加上非叢集索引總大小，這就足夠。</span><span class="sxs-lookup"><span data-stu-id="dba81-254">It is sufficient to just add the average size of the LOB values expected, multiply by ***Num_Rows***, and add that to the total nonclustered index size.</span></span>  
  
-   <span data-ttu-id="dba81-255">壓縮</span><span class="sxs-lookup"><span data-stu-id="dba81-255">Compression</span></span>  
  
     <span data-ttu-id="dba81-256">您無法預先計算壓縮索引的大小。</span><span class="sxs-lookup"><span data-stu-id="dba81-256">You cannot pre-calculate the size of a compressed index.</span></span>  
  
-   <span data-ttu-id="dba81-257">疏鬆資料行</span><span class="sxs-lookup"><span data-stu-id="dba81-257">Sparse columns</span></span>  
  
     <span data-ttu-id="dba81-258">如需有關疏鬆資料行空間需求的詳細資訊，請參閱＜ [Use Sparse Columns](../tables/use-sparse-columns.md)＞。</span><span class="sxs-lookup"><span data-stu-id="dba81-258">For information about the space requirements of sparse columns, see [Use Sparse Columns](../tables/use-sparse-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dba81-259">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dba81-259">See Also</span></span>  
 <span data-ttu-id="dba81-260">[叢集與非叢集索引說明](../indexes/clustered-and-nonclustered-indexes-described.md) </span><span class="sxs-lookup"><span data-stu-id="dba81-260">[Clustered and Nonclustered Indexes Described](../indexes/clustered-and-nonclustered-indexes-described.md) </span></span>  
 <span data-ttu-id="dba81-261">[建立非叢集索引](../indexes/create-nonclustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="dba81-261">[Create Nonclustered Indexes](../indexes/create-nonclustered-indexes.md) </span></span>  
 <span data-ttu-id="dba81-262">[建立叢集索引](../indexes/create-clustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="dba81-262">[Create Clustered Indexes](../indexes/create-clustered-indexes.md) </span></span>  
 <span data-ttu-id="dba81-263">[估計資料表的大小](estimate-the-size-of-a-table.md) </span><span class="sxs-lookup"><span data-stu-id="dba81-263">[Estimate the Size of a Table](estimate-the-size-of-a-table.md) </span></span>  
 <span data-ttu-id="dba81-264">[估計叢集索引的大小](estimate-the-size-of-a-clustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="dba81-264">[Estimate the Size of a Clustered Index](estimate-the-size-of-a-clustered-index.md) </span></span>  
 <span data-ttu-id="dba81-265">[估計堆積的大小](estimate-the-size-of-a-heap.md) </span><span class="sxs-lookup"><span data-stu-id="dba81-265">[Estimate the Size of a Heap](estimate-the-size-of-a-heap.md) </span></span>  
 [<span data-ttu-id="dba81-266">估計資料庫的大小</span><span class="sxs-lookup"><span data-stu-id="dba81-266">Estimate the Size of a Database</span></span>](estimate-the-size-of-a-database.md)  
  
  
