---
title: 估計叢集索引的大小 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- space allocation [SQL Server], index size
- size [SQL Server], tables
- disk space [SQL Server], indexes
- predicting table size [SQL Server]
- table size [SQL Server]
- estimating table size
- space [SQL Server], indexes
- clustered indexes, table size
- nonclustered indexes [SQL Server], table size
- designing databases [SQL Server], estimating size
- calculating table size
ms.assetid: 2b5137f8-98ad-46b5-9aae-4c980259bf8d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4d224c5ae55cc5ec7690ca0962cbc2130bac22e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709550"
---
# <a name="estimate-the-size-of-a-clustered-index"></a><span data-ttu-id="e6bc8-102">估計叢集索引的大小</span><span class="sxs-lookup"><span data-stu-id="e6bc8-102">Estimate the Size of a Clustered Index</span></span>
  <span data-ttu-id="e6bc8-103">您可以使用下列步驟，估計在叢集索引中儲存資料所需的空間量：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-103">You can use the following steps to estimate the amount of space that is required to store data in a clustered index:</span></span>  
  
1.  <span data-ttu-id="e6bc8-104">計算用來在叢集索引的分葉層級中儲存資料的空間。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-104">Calculate the space used to store data in the leaf level of the clustered index.</span></span>  
  
2.  <span data-ttu-id="e6bc8-105">計算用來儲存叢集索引之索引資訊的空間。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-105">Calculate the space used to store index information for the clustered index.</span></span>  
  
3.  <span data-ttu-id="e6bc8-106">加總計算的值。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-106">Total the calculated values.</span></span>  
  
## <a name="step-1-calculate-the-space-used-to-store-data-in-the-leaf-level"></a><span data-ttu-id="e6bc8-107">步驟 1：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-107">Step 1.</span></span> <span data-ttu-id="e6bc8-108">計算用來在分葉層級中儲存資料的空間</span><span class="sxs-lookup"><span data-stu-id="e6bc8-108">Calculate the Space Used to Store Data in the Leaf Level</span></span>  
  
1.  <span data-ttu-id="e6bc8-109">指定資料表中將會有的資料列數目：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-109">Specify the number of rows that will be present in the table:</span></span>  
  
     <span data-ttu-id="e6bc8-110">***Num_Rows***  = 資料表中的資料列數目</span><span class="sxs-lookup"><span data-stu-id="e6bc8-110">***Num_Rows***  = number of rows in the table</span></span>  
  
2.  <span data-ttu-id="e6bc8-111">指定固定長度與可變長度資料行的數目，並計算儲存這些資料行所需的空間：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-111">Specify the number of fixed-length and variable-length columns and calculate the space that is required for their storage:</span></span>  
  
     <span data-ttu-id="e6bc8-112">計算這兩組資料行在資料列內各佔多少空間。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-112">Calculate the space that each of these groups of columns occupies within the data row.</span></span> <span data-ttu-id="e6bc8-113">資料行的大小取決於資料類型和長度規格。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-113">The size of a column depends on the data type and length specification.</span></span>  
  
     <span data-ttu-id="e6bc8-114">***Num_Cols***  = 資料行 (固定長度和可變長度) 總數</span><span class="sxs-lookup"><span data-stu-id="e6bc8-114">***Num_Cols***  = total number of columns (fixed-length and variable-length)</span></span>  
  
     <span data-ttu-id="e6bc8-115">***Fixed_Data_Size***  = 所有固定長度資料行的總位元組大小</span><span class="sxs-lookup"><span data-stu-id="e6bc8-115">***Fixed_Data_Size***  = total byte size of all fixed-length columns</span></span>  
  
     <span data-ttu-id="e6bc8-116">***Num_Variable_Cols***  = 可變長度資料行的數目</span><span class="sxs-lookup"><span data-stu-id="e6bc8-116">***Num_Variable_Cols***  = number of variable-length columns</span></span>  
  
     <span data-ttu-id="e6bc8-117">***Max_Var_Size***  = 所有可變長度資料行的位元組大小上限</span><span class="sxs-lookup"><span data-stu-id="e6bc8-117">***Max_Var_Size***  = maximum byte size of all variable-length columns</span></span>  
  
3.  <span data-ttu-id="e6bc8-118">如果叢集索引為非唯一的索引，請將 *uniqueifier* 資料行列入考慮：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-118">If the clustered index is nonunique, account for the *uniqueifier* column:</span></span>  
  
     <span data-ttu-id="e6bc8-119">uniqueifier 是可為 Null 的可變長度資料行。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-119">The uniqueifier is a nullable, variable-length column.</span></span> <span data-ttu-id="e6bc8-120">在具有非唯一索引鍵值的資料列中，它將會是非 Null 並且為 4 個位元組大小。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-120">It will be nonnull and 4 bytes in size in rows that have nonunique key values.</span></span> <span data-ttu-id="e6bc8-121">此值是索引鍵的一部分，必須用來確定每個資料列都有唯一的索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-121">This value is part of the index key and is required to make sure that every row has a unique key value.</span></span>  
  
     <span data-ttu-id="e6bc8-122">***Num_Cols***  = ***Num_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="e6bc8-122">***Num_Cols***  = ***Num_Cols*** + 1</span></span>  
  
     <span data-ttu-id="e6bc8-123">***Num_Variable_Cols***  = ***Num_Variable_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="e6bc8-123">***Num_Variable_Cols***  = ***Num_Variable_Cols*** + 1</span></span>  
  
     <span data-ttu-id="e6bc8-124">***Max_Var_Size***  = ***Max_Var_Size*** + 4</span><span class="sxs-lookup"><span data-stu-id="e6bc8-124">***Max_Var_Size***  = ***Max_Var_Size*** + 4</span></span>  
  
     <span data-ttu-id="e6bc8-125">這些修改假設所有值均為非唯一的值。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-125">These modifications assume that all values will be nonunique.</span></span>  
  
4.  <span data-ttu-id="e6bc8-126">資料列中有一部分 (稱為 Null 點陣圖) 是保留的空間，用來管理資料行的 Null 屬性。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-126">Part of the row, known as the null bitmap, is reserved to manage column nullability.</span></span> <span data-ttu-id="e6bc8-127">計算它的大小：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-127">Calculate its size:</span></span>  
  
     <span data-ttu-id="e6bc8-128">***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="e6bc8-128">***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)</span></span>  
  
     <span data-ttu-id="e6bc8-129">上述運算式中只有整數部分應該使用，請捨棄餘數。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-129">Only the integer part of the previous expression should be used; discard any remainder.</span></span>  
  
5.  <span data-ttu-id="e6bc8-130">計算可變長度資料的大小：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-130">Calculate the variable-length data size:</span></span>  
  
     <span data-ttu-id="e6bc8-131">如果在索引中有可變長度的資料行，請決定將資料行儲存到索引列中所需的空間大小。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-131">If there are variable-length columns in the table, determine how much space is used to store the columns within the row:</span></span>  
  
     <span data-ttu-id="e6bc8-132">***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***</span><span class="sxs-lookup"><span data-stu-id="e6bc8-132">***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***</span></span>  
  
     <span data-ttu-id="e6bc8-133">加入 ***Max_Var_Size*** 的位元組是用於追蹤每個可變資料行。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-133">The bytes added to ***Max_Var_Size*** are for tracking each variable column.</span></span> <span data-ttu-id="e6bc8-134">這個公式假設所有可變長度的資料行是 100% 填滿的。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-134">This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="e6bc8-135">如果您預期可變長度資料行儲存所佔空間的百分比會比較低，您可以經由調整百分比所得的 ***Max_Var_Size*** 值，取得更精確的整體資料表大小。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-135">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e6bc8-136">您可以結合使定義的資料表總寬度超過 8,060 個位元組的 `varchar`、`nvarchar`、`varbinary` 或 `sql_variant` 資料行。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-136">You can combine `varchar`, `nvarchar`, `varbinary`, or `sql_variant` columns that cause the total defined table width to exceed 8,060 bytes.</span></span> <span data-ttu-id="e6bc8-137">這些資料行的每個長度必須仍然在 `varchar`、`varbinary` 或 `sql_variant` 資料行的 8,000 個位元組限制內，以及 `nvarchar` 資料行的 4,000 個位元組限制。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-137">The length of each one of these columns must still fall within the limit of 8,000 bytes for a `varchar`, `varbinary`, or `sql_variant` column, and 4,000 bytes for `nvarchar` columns.</span></span> <span data-ttu-id="e6bc8-138">然而，結合的寬度可能超過資料表中 8,060 位元組的限制。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-138">However, their combined widths may exceed the 8,060 byte limit in a table.</span></span>  
  
     <span data-ttu-id="e6bc8-139">如果沒有可變長度資料行，請將 ***Variable_Data_Size*** 設成 0。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-139">If there are no variable-length columns, set ***Variable_Data_Size*** to 0.</span></span>  
  
6.  <span data-ttu-id="e6bc8-140">計算資料列總大小：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-140">Calculate the total row size:</span></span>  
  
     <span data-ttu-id="e6bc8-141">***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4</span><span class="sxs-lookup"><span data-stu-id="e6bc8-141">***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4</span></span>  
  
     <span data-ttu-id="e6bc8-142">4 這個值是資料列的資料列標頭負擔。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-142">The value 4 is the row header overhead of a data row.</span></span>  
  
7.  <span data-ttu-id="e6bc8-143">計算每個分頁的資料列數目 (每個分頁包含 8096 個可用位元組)：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-143">Calculate the number of rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="e6bc8-144">***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="e6bc8-144">***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="e6bc8-145">因為資料列不能跨頁，每個分頁的資料列數目必須無條件捨去小數，而取最接近的整數資料列。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-145">Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="e6bc8-146">公式中的 2 這個值是給分頁位置陣列中的該資料列項目。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-146">The value 2 in the formula is for the row's entry in the slot array of the page.</span></span>  
  
8.  <span data-ttu-id="e6bc8-147">根據指定的 [填滿因數](../indexes/specify-fill-factor-for-an-index.md) ，計算每個分頁所保留的可用資料列數目：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-147">Calculate the number of reserved free rows per page, based on the [fill factor](../indexes/specify-fill-factor-for-an-index.md) specified:</span></span>  
  
     <span data-ttu-id="e6bc8-148">***Free_Rows_Per_Page***  = 8096 x ((100 - ***Fill_Factor***) / 100) / (***Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="e6bc8-148">***Free_Rows_Per_Page***  = 8096 x ((100 - ***Fill_Factor***) / 100) / (***Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="e6bc8-149">計算中所使用的填滿因數是整數值而不是百分比。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-149">The fill factor used in the calculation is an integer value instead of a percentage.</span></span> <span data-ttu-id="e6bc8-150">因為資料列不能跨頁，每個分頁的資料列數目必須無條件捨去小數，而取最接近的整數資料列。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-150">Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="e6bc8-151">當填滿因數變大時，每個分頁上會儲存更多資料，分頁也會比較少。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-151">As the fill factor grows, more data will be stored on each page and there will be fewer pages.</span></span> <span data-ttu-id="e6bc8-152">公式中的 2 這個值是給分頁位置陣列中的該資料列項目。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-152">The value 2 in the formula is for the row's entry in the slot array of the page.</span></span>  
  
9. <span data-ttu-id="e6bc8-153">計算儲存所有資料列所需的分頁數目：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-153">Calculate the number of pages required to store all the rows:</span></span>  
  
     <span data-ttu-id="e6bc8-154">***Num_Leaf_Pages***  = ***Num_Rows*** / (***Rows_Per_Page*** - ***Free_Rows_Per_Page***)</span><span class="sxs-lookup"><span data-stu-id="e6bc8-154">***Num_Leaf_Pages***  = ***Num_Rows*** / (***Rows_Per_Page*** - ***Free_Rows_Per_Page***)</span></span>  
  
     <span data-ttu-id="e6bc8-155">估計的分頁數目應該要將小數進位到最接近的整分頁數。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-155">The number of pages estimated should be rounded up to the nearest whole page.</span></span>  
  
10. <span data-ttu-id="e6bc8-156">計算在分葉層級中儲存資料所需的空間量 (每個分頁共有 8192 個位元組)：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-156">Calculate the amount of space that is required to store the data in the leaf level (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="e6bc8-157">***Leaf_space_used***  = 8192 x ***Num_Leaf_Pages***</span><span class="sxs-lookup"><span data-stu-id="e6bc8-157">***Leaf_space_used***  = 8192 x ***Num_Leaf_Pages***</span></span>  
  
## <a name="step-2-calculate-the-space-used-to-store-index-information"></a><span data-ttu-id="e6bc8-158">步驟 2：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-158">Step 2.</span></span> <span data-ttu-id="e6bc8-159">計算用來儲存索引資訊的空間</span><span class="sxs-lookup"><span data-stu-id="e6bc8-159">Calculate the Space Used to Store Index Information</span></span>  
 <span data-ttu-id="e6bc8-160">您可以使用下列步驟，估計儲存較高索引層級所需的空間量：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-160">You can use the following steps to estimate the amount of space that is required to store the upper levels of the index:</span></span>  
  
1.  <span data-ttu-id="e6bc8-161">指定索引鍵中固定長度和可變長度資料行的數目，並計算儲存它們所需的空間：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-161">Specify the number of fixed-length and variable-length columns in the index key and calculate the space that is required for their storage:</span></span>  
  
     <span data-ttu-id="e6bc8-162">索引的索引鍵資料行可以包含固定長度和可變長度的資料行。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-162">The key columns of an index can include fixed-length and variable-length columns.</span></span> <span data-ttu-id="e6bc8-163">若要估計內部層級的索引資料列大小，請計算這些資料行群組在索引資料列中佔用的空間。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-163">To estimate the interior level index row size, calculate the space that each of these groups of columns occupies within the index row.</span></span> <span data-ttu-id="e6bc8-164">資料行的大小取決於資料類型和長度規格。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-164">The size of a column depends on the data type and length specification.</span></span>  
  
     <span data-ttu-id="e6bc8-165">***Num_Key_Cols***  = 索引鍵資料行 (固定長度和可變長度) 總數</span><span class="sxs-lookup"><span data-stu-id="e6bc8-165">***Num_Key_Cols***  = total number of key columns (fixed-length and variable-length)</span></span>  
  
     <span data-ttu-id="e6bc8-166">***Num_Key_Cols***  = 所有固定長度索引鍵資料行的總位元組大小</span><span class="sxs-lookup"><span data-stu-id="e6bc8-166">***Fixed_Key_Size***  = total byte size of all fixed-length key columns</span></span>  
  
     <span data-ttu-id="e6bc8-167">***Num_Variable_Key_Cols***  = 可變長度索引鍵資料行的數目</span><span class="sxs-lookup"><span data-stu-id="e6bc8-167">***Num_Variable_Key_Cols***  = number of variable-length key columns</span></span>  
  
     <span data-ttu-id="e6bc8-168">***Max_Var_Key_Size***  = 所有可變長度索引鍵資料行的最大位元組大小</span><span class="sxs-lookup"><span data-stu-id="e6bc8-168">***Max_Var_Key_Size***  = maximum byte size of all variable-length key columns</span></span>  
  
2.  <span data-ttu-id="e6bc8-169">如果索引為非唯一的索引，請將任何所需的 uniqueifier 列入考慮：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-169">Account for any uniqueifier needed if the index is nonunique:</span></span>  
  
     <span data-ttu-id="e6bc8-170">uniqueifier 是可為 Null 的可變長度資料行。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-170">The uniqueifier is a nullable, variable-length column.</span></span> <span data-ttu-id="e6bc8-171">在具有非唯一索引鍵值的資料列中，它將會是非 Null 並且為 4 個位元組大小。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-171">It will be nonnull and 4 bytes in size in rows that have nonunique index key values.</span></span> <span data-ttu-id="e6bc8-172">此值是索引鍵的一部分，必須用來確定每個資料列都有唯一的索引鍵值。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-172">This value is part of the index key and is required to make sure that every row has a unique key value.</span></span>  
  
     <span data-ttu-id="e6bc8-173">***Num_Key_Cols***  = ***Num_Key_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="e6bc8-173">***Num_Key_Cols***  = ***Num_Key_Cols*** + 1</span></span>  
  
     <span data-ttu-id="e6bc8-174">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 1</span><span class="sxs-lookup"><span data-stu-id="e6bc8-174">***Num_Variable_Key_Cols***  = ***Num_Variable_Key_Cols*** + 1</span></span>  
  
     <span data-ttu-id="e6bc8-175">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 4</span><span class="sxs-lookup"><span data-stu-id="e6bc8-175">***Max_Var_Key_Size***  = ***Max_Var_Key_Size*** + 4</span></span>  
  
     <span data-ttu-id="e6bc8-176">這些修改假設所有值均為非唯一的值。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-176">These modifications assume that all values will be nonunique.</span></span>  
  
3.  <span data-ttu-id="e6bc8-177">計算 Null 點陣圖大小：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-177">Calculate the null bitmap size:</span></span>  
  
     <span data-ttu-id="e6bc8-178">若索引鍵中有可為 Null 的資料行，索引資料列的一部分會保留給 Null 點陣圖。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-178">If there are nullable columns in the index key, part of the index row is reserved for the null bitmap.</span></span> <span data-ttu-id="e6bc8-179">計算它的大小：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-179">Calculate its size:</span></span>  
  
     <span data-ttu-id="e6bc8-180">***Index_Null_Bitmap***  = 2 + ((索引資料列中的資料行數目 + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="e6bc8-180">***Index_Null_Bitmap***  = 2 + ((number of columns in the index row + 7) / 8)</span></span>  
  
     <span data-ttu-id="e6bc8-181">您應該僅使用先前運算式的整數部分。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-181">Only the integer part of the previous expression should be used.</span></span> <span data-ttu-id="e6bc8-182">請捨去任何餘數。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-182">Discard any remainder.</span></span>  
  
     <span data-ttu-id="e6bc8-183">如果沒有可為 Null 的索引鍵資料行，請將 ***Index_Null_Bitmap*** 設成 0。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-183">If there are no nullable key columns, set ***Index_Null_Bitmap*** to 0.</span></span>  
  
4.  <span data-ttu-id="e6bc8-184">計算可變長度資料的大小：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-184">Calculate the variable-length data size:</span></span>  
  
     <span data-ttu-id="e6bc8-185">如果在索引中有可變長度的資料行，請決定要在索引資料列中儲存資料行的空間。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-185">If there are variable-length columns in the index, determine how much space is used to store the columns within the index row:</span></span>  
  
     <span data-ttu-id="e6bc8-186">***Variable_Key_Size***  = 2 + (***Num_Variable_Key_Cols*** x 2) + ***Max_Var_Key_Size***</span><span class="sxs-lookup"><span data-stu-id="e6bc8-186">***Variable_Key_Size***  = 2 + (***Num_Variable_Key_Cols*** x 2) + ***Max_Var_Key_Size***</span></span>  
  
     <span data-ttu-id="e6bc8-187">加入 ***Max_Var_Key_Size*** 的位元組是用於追蹤每個可變長度資料行。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-187">The bytes added to ***Max_Var_Key_Size*** are for tracking each variable-length column.</span></span> <span data-ttu-id="e6bc8-188">這個公式假設所有可變長度的資料行是 100% 填滿的。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-188">This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="e6bc8-189">如果您預期可變長度資料行所使用的儲存空間百分比會比較小，您可以經由調整百分比所得的 ***Max_Var_Key_Size*** 值，產生更精確的整體資料表大小之估計。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-189">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Key_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
     <span data-ttu-id="e6bc8-190">若沒有可變長度的資料行，請將 ***Variable_Key_Size*** 設成 0。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-190">If there are no variable-length columns, set ***Variable_Key_Size*** to 0.</span></span>  
  
5.  <span data-ttu-id="e6bc8-191">計算索引資料列的大小：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-191">Calculate the index row size:</span></span>  
  
     <span data-ttu-id="e6bc8-192">***Index_Row_Size***  = ***Fixed_Key_Size*** + ***Variable_Key_Size*** + ***Index_Null_Bitmap*** + 1 (索引資料列的資料列標頭上方) + 6 (子頁面識別碼指標)</span><span class="sxs-lookup"><span data-stu-id="e6bc8-192">***Index_Row_Size***  = ***Fixed_Key_Size*** + ***Variable_Key_Size*** + ***Index_Null_Bitmap*** + 1 (for row header overhead of an index row) + 6 (for the child page ID pointer)</span></span>  
  
6.  <span data-ttu-id="e6bc8-193">計算每個分頁的索引資料列數目 (每個分頁包含 8096 個可用位元組)：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-193">Calculate the number of index rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="e6bc8-194">***Index_Rows_Per_Page***  = 8096 / (***Index_Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="e6bc8-194">***Index_Rows_Per_Page***  = 8096 / (***Index_Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="e6bc8-195">由於索引資料列並不會跨越分頁，因此每個分頁索引資料列的數目應該捨去小數，而取最接近的整數列數。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-195">Because index rows do not span pages, the number of index rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="e6bc8-196">公式中的 2 是給分頁位置陣列中的該資料列項目。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-196">The 2 in the formula is for the row's entry in the page's slot array.</span></span>  
  
7.  <span data-ttu-id="e6bc8-197">計算索引中的層級數目：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-197">Calculate the number of levels in the index:</span></span>  
  
     <span data-ttu-id="e6bc8-198">***非 leaf_Levels*** = 1 + log Index_Rows_Per_Page (***Num_Leaf_Pages***  /  ***Index_Rows_Per_Page***) </span><span class="sxs-lookup"><span data-stu-id="e6bc8-198">***Non-leaf_Levels***  = 1 + log Index_Rows_Per_Page (***Num_Leaf_Pages*** / ***Index_Rows_Per_Page***)</span></span>  
  
     <span data-ttu-id="e6bc8-199">將這個值無條件向上進位到最近的整數。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-199">Round this value up to the nearest whole number.</span></span> <span data-ttu-id="e6bc8-200">此值不包含叢集索引的分葉層級。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-200">This value does not include the leaf level of the clustered index.</span></span>  
  
8.  <span data-ttu-id="e6bc8-201">計算索引中的非分葉頁面數目：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-201">Calculate the number of non-leaf pages in the index:</span></span>  
  
     <span data-ttu-id="e6bc8-202">***Num_Index_Pages =*** ∑層級\*\*\* (Num_Leaf_Pages/ (Index_Rows_Per_Page***<sup>層級</sup>***) # B3\*\*\*</span><span class="sxs-lookup"><span data-stu-id="e6bc8-202">***Num_Index_Pages =*** ∑Level ***(Num_Leaf_Pages / (Index_Rows_Per_Page***<sup>Level</sup>***))***</span></span>  
  
     <span data-ttu-id="e6bc8-203">其中 1 <= Level <= ***Non-leaf_Levels***</span><span class="sxs-lookup"><span data-stu-id="e6bc8-203">where 1 <= Level <= ***Non-leaf_Levels***</span></span>  
  
     <span data-ttu-id="e6bc8-204">將每個被加數無條件向上進位到最近的整數。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-204">Round each summand up to the nearest whole number.</span></span> <span data-ttu-id="e6bc8-205">簡單舉例說明，假設有個索引，其中 ***Num_Leaf_Pages*** = 1000 和 ***Index_Rows_Per_Page*** = 25。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-205">As a simple example, consider an index where ***Num_Leaf_Pages*** = 1000 and ***Index_Rows_Per_Page*** = 25.</span></span> <span data-ttu-id="e6bc8-206">分葉層級上方的第一個索引層級會儲存 1000 個索引資料列，這是每個分葉頁面的一個索引資料列，而且每個頁面可以容納 25 個索引資料列。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-206">The first index level above the leaf level stores 1000 index rows, which is one index row per leaf page, and 25 index rows can fit per page.</span></span> <span data-ttu-id="e6bc8-207">這表示儲存這 1000 個索引資料列需要 40 頁。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-207">This means that 40 pages are required to store those 1000 index rows.</span></span> <span data-ttu-id="e6bc8-208">索引的下一個層級必須儲存 40 個資料列，</span><span class="sxs-lookup"><span data-stu-id="e6bc8-208">The next level of the index has to store 40 rows.</span></span> <span data-ttu-id="e6bc8-209">這表示它需要 2 頁。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-209">This means it requires 2 pages.</span></span> <span data-ttu-id="e6bc8-210">索引的最後一個層級必須儲存 2 個資料列。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-210">The final level of the index has to store 2 rows.</span></span> <span data-ttu-id="e6bc8-211">這表示它需要 1 頁。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-211">This means it requires 1 page.</span></span> <span data-ttu-id="e6bc8-212">這會提供 43 個非分葉索引頁面。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-212">This gives 43 non-leaf index pages.</span></span> <span data-ttu-id="e6bc8-213">在上述公式中使用這些數字時，結果如下：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-213">When these numbers are used in the previous formulas, the outcome is as follows:</span></span>  
  
     <span data-ttu-id="e6bc8-214">***非 leaf_Levels*** = 1 + log25 (1000/25) = 3</span><span class="sxs-lookup"><span data-stu-id="e6bc8-214">***Non-leaf_Levels***  = 1 + log25 (1000 / 25) = 3</span></span>  
  
     <span data-ttu-id="e6bc8-215">***Num_Index_Pages*** = 1000/ (25<sup>3</sup>) + 1000/ (25<sup>2</sup>) + 1000/ (25<sup>1</sup>) = 1 + 2 + 40 = 43，這是範例中所描述的頁面數目。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-215">***Num_Index_Pages*** = 1000/(25<sup>3</sup>)+ 1000/(25<sup>2</sup>) + 1000/(25<sup>1</sup>) = 1 + 2 + 40 = 43, which is the number of pages described in the example.</span></span>  
  
9. <span data-ttu-id="e6bc8-216">計算索引的大小 (每個分頁共有 8192 個位元組)：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-216">Calculate the size of the index (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="e6bc8-217">***Index_Space_Used***  = 8192 x ***Num_Index_Pages***</span><span class="sxs-lookup"><span data-stu-id="e6bc8-217">***Index_Space_Used***  = 8192 x ***Num_Index_Pages***</span></span>  
  
## <a name="step-3-total-the-calculated-values"></a><span data-ttu-id="e6bc8-218">步驟 3：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-218">Step 3.</span></span> <span data-ttu-id="e6bc8-219">加總計算的值</span><span class="sxs-lookup"><span data-stu-id="e6bc8-219">Total the Calculated Values</span></span>  
 <span data-ttu-id="e6bc8-220">將前兩個步驟所取得的值加總：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-220">Total the values obtained from the previous two steps:</span></span>  
  
 <span data-ttu-id="e6bc8-221">叢集索引大小 (位元組) = ***Leaf_Space_Used*** + ***Index_Space_used***</span><span class="sxs-lookup"><span data-stu-id="e6bc8-221">Clustered index size (bytes) = ***Leaf_Space_Used*** + ***Index_Space_used***</span></span>  
  
 <span data-ttu-id="e6bc8-222">上述計算未考慮下列項目：</span><span class="sxs-lookup"><span data-stu-id="e6bc8-222">This calculation does not consider the following:</span></span>  
  
-   <span data-ttu-id="e6bc8-223">資料分割</span><span class="sxs-lookup"><span data-stu-id="e6bc8-223">Partitioning</span></span>  
  
     <span data-ttu-id="e6bc8-224">從資料分割而來的空間負擔非常小，但是計算起來很複雜。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-224">The space overhead from partitioning is minimal, but complex to calculate.</span></span> <span data-ttu-id="e6bc8-225">不一定要包含它。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-225">It is not important to include.</span></span>  
  
-   <span data-ttu-id="e6bc8-226">配置頁面</span><span class="sxs-lookup"><span data-stu-id="e6bc8-226">Allocation pages</span></span>  
  
     <span data-ttu-id="e6bc8-227">至少有一個 IAM 頁面用以追蹤配置到堆積的頁面，但是空間負擔非常小，而且沒有演算法來決定性地計算要使用多少 IAM 頁面。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-227">There is at least one IAM page used to track the pages allocated to a heap, but the space overhead is minimal and there is no algorithm to deterministically calculate exactly how many IAM pages will be used.</span></span>  
  
-   <span data-ttu-id="e6bc8-228">大型物件 (LOB) 值</span><span class="sxs-lookup"><span data-stu-id="e6bc8-228">Large object (LOB) values</span></span>  
  
     <span data-ttu-id="e6bc8-229">決定到底要使用多少空間來儲存 LOB 資料類型 `varchar(max)`、`varbinary(max)`、`nvarchar(max)`、`text`、`ntext`、`xml` 以及 `image` 值的演算法是很複雜的。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-229">The algorithm to determine exactly how much space will be used to store the LOB data types `varchar(max)`, `varbinary(max)`, `nvarchar(max)`, `text`, `ntext`, `xml`, and `image` values is complex.</span></span> <span data-ttu-id="e6bc8-230">只要加上預期的 LOB 值平均大小，乘以 ***Num_Rows***，再將此值加上叢集索引總大小，這就足夠。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-230">It is sufficient to just add the average size of the LOB values that are expected, multiply by ***Num_Rows***, and add that to the total clustered index size.</span></span>  
  
-   <span data-ttu-id="e6bc8-231">壓縮</span><span class="sxs-lookup"><span data-stu-id="e6bc8-231">Compression</span></span>  
  
     <span data-ttu-id="e6bc8-232">您無法預先計算壓縮索引的大小。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-232">You cannot pre-calculate the size of a compressed index.</span></span>  
  
-   <span data-ttu-id="e6bc8-233">疏鬆資料行</span><span class="sxs-lookup"><span data-stu-id="e6bc8-233">Sparse columns</span></span>  
  
     <span data-ttu-id="e6bc8-234">如需有關疏鬆資料行空間需求的詳細資訊，請參閱＜ [Use Sparse Columns](../tables/use-sparse-columns.md)＞。</span><span class="sxs-lookup"><span data-stu-id="e6bc8-234">For information about the space requirements of sparse columns, see [Use Sparse Columns](../tables/use-sparse-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6bc8-235">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e6bc8-235">See Also</span></span>  
 <span data-ttu-id="e6bc8-236">[叢集與非叢集索引說明](../indexes/clustered-and-nonclustered-indexes-described.md) </span><span class="sxs-lookup"><span data-stu-id="e6bc8-236">[Clustered and Nonclustered Indexes Described](../indexes/clustered-and-nonclustered-indexes-described.md) </span></span>  
 <span data-ttu-id="e6bc8-237">[估計資料表的大小](estimate-the-size-of-a-table.md) </span><span class="sxs-lookup"><span data-stu-id="e6bc8-237">[Estimate the Size of a Table](estimate-the-size-of-a-table.md) </span></span>  
 <span data-ttu-id="e6bc8-238">[建立叢集索引](../indexes/create-clustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="e6bc8-238">[Create Clustered Indexes](../indexes/create-clustered-indexes.md) </span></span>  
 <span data-ttu-id="e6bc8-239">[建立非叢集索引](../indexes/create-nonclustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="e6bc8-239">[Create Nonclustered Indexes](../indexes/create-nonclustered-indexes.md) </span></span>  
 <span data-ttu-id="e6bc8-240">[估計非叢集索引的大小](estimate-the-size-of-a-nonclustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="e6bc8-240">[Estimate the Size of a Nonclustered Index](estimate-the-size-of-a-nonclustered-index.md) </span></span>  
 <span data-ttu-id="e6bc8-241">[估計堆積的大小](estimate-the-size-of-a-heap.md) </span><span class="sxs-lookup"><span data-stu-id="e6bc8-241">[Estimate the Size of a Heap](estimate-the-size-of-a-heap.md) </span></span>  
 [<span data-ttu-id="e6bc8-242">估計資料庫的大小</span><span class="sxs-lookup"><span data-stu-id="e6bc8-242">Estimate the Size of a Database</span></span>](estimate-the-size-of-a-database.md)  
  
  
