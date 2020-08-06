---
title: 估計堆積的大小 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- disk space [SQL Server], indexes
- estimating heap size
- size [SQL Server], heap
- space [SQL Server], indexes
- heaps
ms.assetid: 81fd5ec9-ce0f-4c2c-8ba0-6c483cea6c75
author: stevestein
ms.author: sstein
ms.openlocfilehash: f32432d07a9731d849ceb793daf209cfc505b0ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606868"
---
# <a name="estimate-the-size-of-a-heap"></a><span data-ttu-id="18e83-102">估計堆積的大小</span><span class="sxs-lookup"><span data-stu-id="18e83-102">Estimate the Size of a Heap</span></span>
  <span data-ttu-id="18e83-103">您可以使用下列步驟，估計儲存堆積中的資料所需的空間量：</span><span class="sxs-lookup"><span data-stu-id="18e83-103">You can use the following steps to estimate the amount of space that is required to store data in a heap:</span></span>  
  
1.  <span data-ttu-id="18e83-104">指定資料表中將會有的資料列數目：</span><span class="sxs-lookup"><span data-stu-id="18e83-104">Specify the number of rows that will be present in the table:</span></span>  
  
     <span data-ttu-id="18e83-105">***Num_Rows***  = 資料表中的資料列數目</span><span class="sxs-lookup"><span data-stu-id="18e83-105">***Num_Rows***  = number of rows in the table</span></span>  
  
2.  <span data-ttu-id="18e83-106">指定固定長度與可變長度資料行的數目，並計算儲存這些資料行所需的空間：</span><span class="sxs-lookup"><span data-stu-id="18e83-106">Specify the number of fixed-length and variable-length columns and calculate the space that is required for their storage:</span></span>  
  
     <span data-ttu-id="18e83-107">計算這兩組資料行在資料列內各佔多少空間。</span><span class="sxs-lookup"><span data-stu-id="18e83-107">Calculate the space that each of these groups of columns occupies within the data row.</span></span> <span data-ttu-id="18e83-108">資料行的大小取決於資料類型和長度規格。</span><span class="sxs-lookup"><span data-stu-id="18e83-108">The size of a column depends on the data type and length specification.</span></span>  
  
     <span data-ttu-id="18e83-109">***Num_Cols***  = 資料行 (固定長度和可變長度) 總數</span><span class="sxs-lookup"><span data-stu-id="18e83-109">***Num_Cols***  = total number of columns (fixed-length and variable-length)</span></span>  
  
     <span data-ttu-id="18e83-110">***Fixed_Data_Size***  = 所有固定長度資料行的總位元組大小</span><span class="sxs-lookup"><span data-stu-id="18e83-110">***Fixed_Data_Size***  = total byte size of all fixed-length columns</span></span>  
  
     <span data-ttu-id="18e83-111">***Num_Variable_Cols***  = 可變長度資料行的數目</span><span class="sxs-lookup"><span data-stu-id="18e83-111">***Num_Variable_Cols***  = number of variable-length columns</span></span>  
  
     <span data-ttu-id="18e83-112">***Max_Var_Size***  = 所有可變長度資料行的總位元組大小上限</span><span class="sxs-lookup"><span data-stu-id="18e83-112">***Max_Var_Size***  = maximum total byte size of all variable-length columns</span></span>  
  
3.  <span data-ttu-id="18e83-113">資料列中有一部分 (稱為 Null 點陣圖) 是保留的空間，用來管理資料行的 Null 屬性。</span><span class="sxs-lookup"><span data-stu-id="18e83-113">Part of the row, known as the null bitmap, is reserved to manage column nullability.</span></span> <span data-ttu-id="18e83-114">計算它的大小：</span><span class="sxs-lookup"><span data-stu-id="18e83-114">Calculate its size:</span></span>  
  
     <span data-ttu-id="18e83-115">***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)</span><span class="sxs-lookup"><span data-stu-id="18e83-115">***Null_Bitmap***  = 2 + ((***Num_Cols*** + 7) / 8)</span></span>  
  
     <span data-ttu-id="18e83-116">您應該僅使用這個運算式的整數部分。</span><span class="sxs-lookup"><span data-stu-id="18e83-116">Only the integer part of this expression should be used.</span></span> <span data-ttu-id="18e83-117">請捨去任何餘數。</span><span class="sxs-lookup"><span data-stu-id="18e83-117">Discard any remainder.</span></span>  
  
4.  <span data-ttu-id="18e83-118">計算可變長度資料的大小：</span><span class="sxs-lookup"><span data-stu-id="18e83-118">Calculate the variable-length data size:</span></span>  
  
     <span data-ttu-id="18e83-119">如果在索引中有可變長度的資料行，請決定將資料行儲存到索引列中所需的空間大小。</span><span class="sxs-lookup"><span data-stu-id="18e83-119">If there are variable-length columns in the table, determine how much space is used to store the columns within the row:</span></span>  
  
     <span data-ttu-id="18e83-120">***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***</span><span class="sxs-lookup"><span data-stu-id="18e83-120">***Variable_Data_Size***  = 2 + (***Num_Variable_Cols*** x 2) + ***Max_Var_Size***</span></span>  
  
     <span data-ttu-id="18e83-121">新增到 ***Max_Var_Size*** 之位元組是用於追蹤每個可變長度的資料行。</span><span class="sxs-lookup"><span data-stu-id="18e83-121">The bytes added to ***Max_Var_Size*** are for tracking each variable-length column.</span></span> <span data-ttu-id="18e83-122">這個公式假設所有可變長度的資料行是 100% 填滿的。</span><span class="sxs-lookup"><span data-stu-id="18e83-122">This formula assumes that all variable-length columns are 100 percent full.</span></span> <span data-ttu-id="18e83-123">如果您預期可變長度資料行儲存所佔空間的百分比會比較低，您可以經由調整百分比所得的 ***Max_Var_Size*** 值，取得更精確的整體資料表大小。</span><span class="sxs-lookup"><span data-stu-id="18e83-123">If you anticipate that a smaller percentage of the variable-length column storage space will be used, you can adjust the ***Max_Var_Size*** value by that percentage to yield a more accurate estimate of the overall table size.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="18e83-124">您可以結合使定義的資料表總寬度超過 8,060 個位元組的 `varchar`、`nvarchar`、`varbinary` 或 `sql_variant` 資料行。</span><span class="sxs-lookup"><span data-stu-id="18e83-124">You can combine `varchar`, `nvarchar`, `varbinary`, or `sql_variant` columns that cause the total defined table width to exceed 8,060 bytes.</span></span> <span data-ttu-id="18e83-125">這些資料行的每個長度仍然必須落在、或資料行的8000位元組限制 `varchar` 內 `nvarchar,``varbinary` `sql_variant` 。</span><span class="sxs-lookup"><span data-stu-id="18e83-125">The length of each one of these columns must still fall within the limit of 8,000 bytes for a `varchar`, `nvarchar,``varbinary`, or `sql_variant` column.</span></span> <span data-ttu-id="18e83-126">然而，結合的寬度可能超過資料表中 8,060 位元組的限制。</span><span class="sxs-lookup"><span data-stu-id="18e83-126">However, their combined widths may exceed the 8,060 byte limit in a table.</span></span>  
  
     <span data-ttu-id="18e83-127">如果沒有可變長度資料行，請將 ***Variable_Data_Size*** 設成 0。</span><span class="sxs-lookup"><span data-stu-id="18e83-127">If there are no variable-length columns, set ***Variable_Data_Size*** to 0.</span></span>  
  
5.  <span data-ttu-id="18e83-128">計算資料列總大小：</span><span class="sxs-lookup"><span data-stu-id="18e83-128">Calculate the total row size:</span></span>  
  
     <span data-ttu-id="18e83-129">***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4</span><span class="sxs-lookup"><span data-stu-id="18e83-129">***Row_Size***  = ***Fixed_Data_Size*** + ***Variable_Data_Size*** + ***Null_Bitmap*** + 4</span></span>  
  
     <span data-ttu-id="18e83-130">公式中 4 這個值是資料列的資料列標頭負擔。</span><span class="sxs-lookup"><span data-stu-id="18e83-130">The value 4 in the formula is the row header overhead of the data row.</span></span>  
  
6.  <span data-ttu-id="18e83-131">計算每個分頁的資料列數目 (每個分頁包含 8096 個可用位元組)：</span><span class="sxs-lookup"><span data-stu-id="18e83-131">Calculate the number of rows per page (8096 free bytes per page):</span></span>  
  
     <span data-ttu-id="18e83-132">***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)</span><span class="sxs-lookup"><span data-stu-id="18e83-132">***Rows_Per_Page***  = 8096 / (***Row_Size*** + 2)</span></span>  
  
     <span data-ttu-id="18e83-133">因為資料列不能跨頁，每個分頁的資料列數目必須無條件捨去小數，而取最接近的整數資料列。</span><span class="sxs-lookup"><span data-stu-id="18e83-133">Because rows do not span pages, the number of rows per page should be rounded down to the nearest whole row.</span></span> <span data-ttu-id="18e83-134">公式中的 2 這個值是給分頁位置陣列中的該資料列項目。</span><span class="sxs-lookup"><span data-stu-id="18e83-134">The value 2 in the formula is for the row's entry in the slot array of the page.</span></span>  
  
7.  <span data-ttu-id="18e83-135">計算儲存所有資料列所需的分頁數目：</span><span class="sxs-lookup"><span data-stu-id="18e83-135">Calculate the number of pages required to store all the rows:</span></span>  
  
     <span data-ttu-id="18e83-136">***Num_Pages***  = ***Num_Rows*** / ***Rows_Per_Page***</span><span class="sxs-lookup"><span data-stu-id="18e83-136">***Num_Pages***  = ***Num_Rows*** / ***Rows_Per_Page***</span></span>  
  
     <span data-ttu-id="18e83-137">估計的分頁數目應該要將小數進位到最接近的整分頁數。</span><span class="sxs-lookup"><span data-stu-id="18e83-137">The number of pages estimated should be rounded up to the nearest whole page.</span></span>  
  
8.  <span data-ttu-id="18e83-138">計算儲存堆積內的資料所需的空間 (每個頁面共有 8192 個位元組)：</span><span class="sxs-lookup"><span data-stu-id="18e83-138">Calculate the amount of space that is required to store the data in the heap (8192 total bytes per page):</span></span>  
  
     <span data-ttu-id="18e83-139">堆積大小 (位元組) = 8192 x ***Num_Pages***</span><span class="sxs-lookup"><span data-stu-id="18e83-139">Heap size (bytes) = 8192 x ***Num_Pages***</span></span>  
  
 <span data-ttu-id="18e83-140">上述計算未考慮下列項目：</span><span class="sxs-lookup"><span data-stu-id="18e83-140">This calculation does not consider the following:</span></span>  
  
-   <span data-ttu-id="18e83-141">資料分割</span><span class="sxs-lookup"><span data-stu-id="18e83-141">Partitioning</span></span>  
  
     <span data-ttu-id="18e83-142">從資料分割而來的空間負擔非常小，但是計算起來很複雜。</span><span class="sxs-lookup"><span data-stu-id="18e83-142">The space overhead from partitioning is minimal, but complex to calculate.</span></span> <span data-ttu-id="18e83-143">不一定要包含它。</span><span class="sxs-lookup"><span data-stu-id="18e83-143">It is not important to include.</span></span>  
  
-   <span data-ttu-id="18e83-144">配置頁面</span><span class="sxs-lookup"><span data-stu-id="18e83-144">Allocation pages</span></span>  
  
     <span data-ttu-id="18e83-145">至少有一個 IAM 頁面用以追蹤配置到堆積的頁面，但是空間負擔非常小，而且沒有演算法來決定性地計算要使用多少 IAM 頁面。</span><span class="sxs-lookup"><span data-stu-id="18e83-145">There is at least one IAM page used to track the pages allocated to a heap, but the space overhead is minimal and there is no algorithm to deterministically calculate exactly how many IAM pages will be used.</span></span>  
  
-   <span data-ttu-id="18e83-146">大型物件 (LOB) 值</span><span class="sxs-lookup"><span data-stu-id="18e83-146">Large object (LOB) values</span></span>  
  
     <span data-ttu-id="18e83-147">判斷要使用多少空間來儲存 LOB 資料類型 `varchar(max)` 、、 `varbinary(max)` `nvarchar(max)` 、 `text` 、 **Ntextxml**和值的演算法 `image` 是很複雜的。</span><span class="sxs-lookup"><span data-stu-id="18e83-147">The algorithm to determine exactly how much space will be used to store the LOB data types `varchar(max)`, `varbinary(max)`, `nvarchar(max)`, `text`, **ntextxml**, and `image` values is complex.</span></span> <span data-ttu-id="18e83-148">只要加入預期的 LOB 值平均大小，並將此值加入堆積大小總計，這樣就已足夠。</span><span class="sxs-lookup"><span data-stu-id="18e83-148">It is sufficient to just add the average size of the LOB values that are expected and add that to the total heap size.</span></span>  
  
-   <span data-ttu-id="18e83-149">壓縮</span><span class="sxs-lookup"><span data-stu-id="18e83-149">Compression</span></span>  
  
     <span data-ttu-id="18e83-150">您無法預先計算壓縮堆積的大小。</span><span class="sxs-lookup"><span data-stu-id="18e83-150">You cannot pre-calculate the size of a compressed heap.</span></span>  
  
-   <span data-ttu-id="18e83-151">疏鬆資料行</span><span class="sxs-lookup"><span data-stu-id="18e83-151">Sparse columns</span></span>  
  
     <span data-ttu-id="18e83-152">如需有關疏鬆資料行空間需求的詳細資訊，請參閱＜ [Use Sparse Columns](../tables/use-sparse-columns.md)＞。</span><span class="sxs-lookup"><span data-stu-id="18e83-152">For information about the space requirements of sparse columns, see [Use Sparse Columns](../tables/use-sparse-columns.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18e83-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18e83-153">See Also</span></span>  
 <span data-ttu-id="18e83-154">[堆積 &#40;無叢集索引的資料表&#41;](../indexes/heaps-tables-without-clustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="18e83-154">[Heaps &#40;Tables without Clustered Indexes&#41;](../indexes/heaps-tables-without-clustered-indexes.md) </span></span>  
 <span data-ttu-id="18e83-155">[叢集與非叢集索引說明](../indexes/clustered-and-nonclustered-indexes-described.md) </span><span class="sxs-lookup"><span data-stu-id="18e83-155">[Clustered and Nonclustered Indexes Described](../indexes/clustered-and-nonclustered-indexes-described.md) </span></span>  
 <span data-ttu-id="18e83-156">[建立叢集索引](../indexes/create-clustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="18e83-156">[Create Clustered Indexes](../indexes/create-clustered-indexes.md) </span></span>  
 <span data-ttu-id="18e83-157">[建立非叢集索引](../indexes/create-nonclustered-indexes.md) </span><span class="sxs-lookup"><span data-stu-id="18e83-157">[Create Nonclustered Indexes](../indexes/create-nonclustered-indexes.md) </span></span>  
 <span data-ttu-id="18e83-158">[估計資料表的大小](estimate-the-size-of-a-table.md) </span><span class="sxs-lookup"><span data-stu-id="18e83-158">[Estimate the Size of a Table](estimate-the-size-of-a-table.md) </span></span>  
 <span data-ttu-id="18e83-159">[估計叢集索引的大小](estimate-the-size-of-a-clustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="18e83-159">[Estimate the Size of a Clustered Index](estimate-the-size-of-a-clustered-index.md) </span></span>  
 <span data-ttu-id="18e83-160">[估計非叢集索引的大小](estimate-the-size-of-a-nonclustered-index.md) </span><span class="sxs-lookup"><span data-stu-id="18e83-160">[Estimate the Size of a Nonclustered Index](estimate-the-size-of-a-nonclustered-index.md) </span></span>  
 [<span data-ttu-id="18e83-161">估計資料庫的大小</span><span class="sxs-lookup"><span data-stu-id="18e83-161">Estimate the Size of a Database</span></span>](estimate-the-size-of-a-database.md)  
  
  
