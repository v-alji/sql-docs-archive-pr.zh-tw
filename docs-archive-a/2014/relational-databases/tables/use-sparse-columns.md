---
title: 使用疏鬆資料行 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- sparse columns, described
- null columns
- sparse columns
ms.assetid: ea7ddb87-f50b-46b6-9f5a-acab222a2ede
author: stevestein
ms.author: sstein
ms.openlocfilehash: b3068ac7a3094605bb809ac84c63766b64fda486
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595865"
---
# <a name="use-sparse-columns"></a><span data-ttu-id="0cb8a-102">使用疏鬆資料行</span><span class="sxs-lookup"><span data-stu-id="0cb8a-102">Use Sparse Columns</span></span>
  <span data-ttu-id="0cb8a-103">疏鬆資料行為已最佳化儲存位置來保存 Null 值的一般資料行。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-103">Sparse columns are ordinary columns that have an optimized storage for null values.</span></span> <span data-ttu-id="0cb8a-104">疏鬆資料行會減少 Null 值的空間需求，但要付出擷取非 Null 值的更多成本負擔。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-104">Sparse columns reduce the space requirements for null values at the cost of more overhead to retrieve nonnull values.</span></span> <span data-ttu-id="0cb8a-105">當空間至少節省了百分之 20 到 40 時，請考慮使用疏鬆資料行。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-105">Consider using sparse columns when the space saved is at least 20 percent to 40 percent.</span></span> <span data-ttu-id="0cb8a-106">疏鬆資料行和資料行集是使用 [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) 或 [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) 陳述式所定義。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-106">Sparse columns and column sets are defined by using the [CREATE TABLE](/sql/t-sql/statements/create-table-transact-sql) or [ALTER TABLE](/sql/t-sql/statements/alter-table-transact-sql) statements.</span></span>  
  
 <span data-ttu-id="0cb8a-107">疏鬆資料行可以搭配資料行集和篩選的索引使用：</span><span class="sxs-lookup"><span data-stu-id="0cb8a-107">Sparse columns can be used with column sets and filtered indexes:</span></span>  
  
-   <span data-ttu-id="0cb8a-108">資料行集</span><span class="sxs-lookup"><span data-stu-id="0cb8a-108">Column sets</span></span>  
  
     <span data-ttu-id="0cb8a-109">INSERT、UPDATE 和 DELETE 陳述式可以依名稱參考疏鬆資料行。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-109">INSERT, UPDATE, and DELETE statements can reference the sparse columns by name.</span></span> <span data-ttu-id="0cb8a-110">但是，您也可以檢視及處理資料表中結合至單一 XML 資料行的所有疏鬆資料行。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-110">However, you can also view and work with all the sparse columns of a table that are combined into a single XML column.</span></span> <span data-ttu-id="0cb8a-111">這個資料行稱為資料行集。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-111">This column is called a column set.</span></span> <span data-ttu-id="0cb8a-112">如需資料行集的詳細資訊，請參閱 [使用資料行集](../tables/use-column-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-112">For more information about column sets, see [Use Column Sets](../tables/use-column-sets.md).</span></span>  
  
-   <span data-ttu-id="0cb8a-113">篩選的索引</span><span class="sxs-lookup"><span data-stu-id="0cb8a-113">Filtered indexes</span></span>  
  
     <span data-ttu-id="0cb8a-114">由於疏鬆資料行有許多 Null 值的資料列，所以它們特別適用於篩選的索引。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-114">Because sparse columns have many null-valued rows, they are especially appropriate for filtered indexes.</span></span> <span data-ttu-id="0cb8a-115">疏鬆資料行上篩選的索引只能針對已填入值的資料列來建立索引，</span><span class="sxs-lookup"><span data-stu-id="0cb8a-115">A filtered index on a sparse column can index only the rows that have populated values.</span></span> <span data-ttu-id="0cb8a-116">這樣會建立更小且更有效率的索引。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-116">This creates a smaller and more efficient index.</span></span> <span data-ttu-id="0cb8a-117">如需詳細資訊，請參閱 [Create Filtered Indexes](../indexes/indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-117">For more information, see [Create Filtered Indexes](../indexes/indexes.md).</span></span>  
  
 <span data-ttu-id="0cb8a-118">疏鬆資料行和篩選的索引會啟用應用程式 (如 [!INCLUDE[winSPServ](../../includes/winspserv-md.md)])，以便利用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]來有效率地儲存及存取使用者定義的大量屬性。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-118">Sparse columns and filtered indexes enable applications, such as [!INCLUDE[winSPServ](../../includes/winspserv-md.md)], to efficiently store and access a large number of user-defined properties by using [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)].</span></span>  
  
## <a name="properties-of-sparse-columns"></a><span data-ttu-id="0cb8a-119">疏鬆資料行的屬性</span><span class="sxs-lookup"><span data-stu-id="0cb8a-119">Properties of Sparse Columns</span></span>  
 <span data-ttu-id="0cb8a-120">疏鬆資料行具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="0cb8a-120">Sparse columns have the following characteristics:</span></span>  
  
-   <span data-ttu-id="0cb8a-121">[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 會使用資料行定義中的 SPARSE 關鍵字，最佳化該資料行中值的儲存方式。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-121">The [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] uses the SPARSE keyword in a column definition to optimize the storage of values in that column.</span></span> <span data-ttu-id="0cb8a-122">因此，當資料表中任何資料列的資料行值是 NULL 時，這些值就不需要儲存位置。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-122">Therefore, when the column value is NULL for any row in the table, the values require no storage.</span></span>  
  
-   <span data-ttu-id="0cb8a-123">具有疏鬆資料行之資料表的目錄檢視與一般資料表相同。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-123">Catalog views for a table that has sparse columns are the same as for a typical table.</span></span> <span data-ttu-id="0cb8a-124">sys.columns 目錄檢視包含資料表中每一個資料行的資料列，而且也包含資料行集 (如果有定義的話)。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-124">The sys.columns catalog view contains a row for each column in the table and includes a column set if one is defined.</span></span>  
  
-   <span data-ttu-id="0cb8a-125">疏鬆資料行是儲存層而非邏輯資料表的屬性。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-125">Sparse columns are a property of the storage layer, rather than the logical table.</span></span> <span data-ttu-id="0cb8a-126">因此，SELECT...INTO 陳述式不會將疏鬆資料行屬性複製到新資料表中。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-126">Therefore a SELECT...INTO statement does not copy over the sparse column property into a new table.</span></span>  
  
-   <span data-ttu-id="0cb8a-127">COLUMNS_UPDATED 函數會傳回 `varbinary` 值，指示 DML 動作期間已更新所有資料行。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-127">The COLUMNS_UPDATED function returns a `varbinary` value to indicate all the columns that were updated during a DML action.</span></span> <span data-ttu-id="0cb8a-128">COLUMNS_UPDATED 函數傳回的位元如下：</span><span class="sxs-lookup"><span data-stu-id="0cb8a-128">The bits that are returned by the COLUMNS_UPDATED function are as follows:</span></span>  
  
    -   <span data-ttu-id="0cb8a-129">當明確更新疏鬆資料行時，該疏鬆資料行的對應位元會設定為 1，而資料行集的位元也會設定為 1。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-129">When a sparse column is explicitly updated, the corresponding bit for that sparse column is set to 1, and the bit for the column set is set to 1.</span></span>  
  
    -   <span data-ttu-id="0cb8a-130">當明確更新資料行集時，此資料行集的位元會設定為 1，而該資料表中所有疏鬆資料行的位元也會設定為 1。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-130">When a column set is explicitly updated, the bit for the column set is set to 1, and the bits for all the sparse columns in that table are set to 1.</span></span>  
  
    -   <span data-ttu-id="0cb8a-131">若為插入作業，所有位元都會設定為 1。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-131">For insert operations, all bits are set to 1.</span></span>  
  
     <span data-ttu-id="0cb8a-132">如需資料行集的詳細資訊，請參閱 [使用資料行集](../tables/use-column-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-132">For more information about columns sets, see [Use Column Sets](../tables/use-column-sets.md).</span></span>  
  
 <span data-ttu-id="0cb8a-133">下列資料類型無法指定為 SPARSE：</span><span class="sxs-lookup"><span data-stu-id="0cb8a-133">The following data types cannot be specified as SPARSE:</span></span>  
  
|||  
|-|-|  
|`geography`|`text`|  
|`geometry`|`timestamp`|  
|`image`|`user-defined data types`|  
|`ntext`||  
  
## <a name="estimated-space-savings-by-data-type"></a><span data-ttu-id="0cb8a-134">資料類型預計節省的空間</span><span class="sxs-lookup"><span data-stu-id="0cb8a-134">Estimated Space Savings by Data Type</span></span>  
 <span data-ttu-id="0cb8a-135">相較於未標示為 SPARSE 之相同資料所需的空間，疏鬆資料行需要更多的儲存空間來儲存非 Null 值。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-135">Sparse columns require more storage space for nonnull values than the space required for identical data that is not marked SPARSE.</span></span> <span data-ttu-id="0cb8a-136">下表顯示每一個資料類型的空間使用。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-136">The following tables show the space usage for each data type.</span></span> <span data-ttu-id="0cb8a-137">**NULL 百分比** 資料行指出資料必須有多少百分比為 NULL，空間的淨節省才會是百分之 40。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-137">The **NULL Percentage** column indicates what percent of the data must be NULL for a net space savings of 40 percent.</span></span>  
  
 <span data-ttu-id="0cb8a-138">**固定長度資料類型**</span><span class="sxs-lookup"><span data-stu-id="0cb8a-138">**Fixed-Length Data Types**</span></span>  
  
|<span data-ttu-id="0cb8a-139">資料類型</span><span class="sxs-lookup"><span data-stu-id="0cb8a-139">Data type</span></span>|<span data-ttu-id="0cb8a-140">非疏鬆位元組</span><span class="sxs-lookup"><span data-stu-id="0cb8a-140">Nonsparse bytes</span></span>|<span data-ttu-id="0cb8a-141">疏鬆位元組</span><span class="sxs-lookup"><span data-stu-id="0cb8a-141">Sparse bytes</span></span>|<span data-ttu-id="0cb8a-142">NULL 百分比</span><span class="sxs-lookup"><span data-stu-id="0cb8a-142">NULL percentage</span></span>|  
|---------------|---------------------|------------------|---------------------|  
|`bit`|<span data-ttu-id="0cb8a-143">0.125</span><span class="sxs-lookup"><span data-stu-id="0cb8a-143">0.125</span></span>|<span data-ttu-id="0cb8a-144">5</span><span class="sxs-lookup"><span data-stu-id="0cb8a-144">5</span></span>|<span data-ttu-id="0cb8a-145">98%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-145">98%</span></span>|  
|`tinyint`|<span data-ttu-id="0cb8a-146">1</span><span class="sxs-lookup"><span data-stu-id="0cb8a-146">1</span></span>|<span data-ttu-id="0cb8a-147">5</span><span class="sxs-lookup"><span data-stu-id="0cb8a-147">5</span></span>|<span data-ttu-id="0cb8a-148">86%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-148">86%</span></span>|  
|`smallint`|<span data-ttu-id="0cb8a-149">2</span><span class="sxs-lookup"><span data-stu-id="0cb8a-149">2</span></span>|<span data-ttu-id="0cb8a-150">6</span><span class="sxs-lookup"><span data-stu-id="0cb8a-150">6</span></span>|<span data-ttu-id="0cb8a-151">76%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-151">76%</span></span>|  
|`int`|<span data-ttu-id="0cb8a-152">4</span><span class="sxs-lookup"><span data-stu-id="0cb8a-152">4</span></span>|<span data-ttu-id="0cb8a-153">8</span><span class="sxs-lookup"><span data-stu-id="0cb8a-153">8</span></span>|<span data-ttu-id="0cb8a-154">64%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-154">64%</span></span>|  
|`bigint`|<span data-ttu-id="0cb8a-155">8</span><span class="sxs-lookup"><span data-stu-id="0cb8a-155">8</span></span>|<span data-ttu-id="0cb8a-156">12</span><span class="sxs-lookup"><span data-stu-id="0cb8a-156">12</span></span>|<span data-ttu-id="0cb8a-157">52%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-157">52%</span></span>|  
|`real`|<span data-ttu-id="0cb8a-158">4</span><span class="sxs-lookup"><span data-stu-id="0cb8a-158">4</span></span>|<span data-ttu-id="0cb8a-159">8</span><span class="sxs-lookup"><span data-stu-id="0cb8a-159">8</span></span>|<span data-ttu-id="0cb8a-160">64%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-160">64%</span></span>|  
|`float`|<span data-ttu-id="0cb8a-161">8</span><span class="sxs-lookup"><span data-stu-id="0cb8a-161">8</span></span>|<span data-ttu-id="0cb8a-162">12</span><span class="sxs-lookup"><span data-stu-id="0cb8a-162">12</span></span>|<span data-ttu-id="0cb8a-163">52%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-163">52%</span></span>|  
|`smallmoney`|<span data-ttu-id="0cb8a-164">4</span><span class="sxs-lookup"><span data-stu-id="0cb8a-164">4</span></span>|<span data-ttu-id="0cb8a-165">8</span><span class="sxs-lookup"><span data-stu-id="0cb8a-165">8</span></span>|<span data-ttu-id="0cb8a-166">64%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-166">64%</span></span>|  
|`money`|<span data-ttu-id="0cb8a-167">8</span><span class="sxs-lookup"><span data-stu-id="0cb8a-167">8</span></span>|<span data-ttu-id="0cb8a-168">12</span><span class="sxs-lookup"><span data-stu-id="0cb8a-168">12</span></span>|<span data-ttu-id="0cb8a-169">52%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-169">52%</span></span>|  
|`smalldatetime`|<span data-ttu-id="0cb8a-170">4</span><span class="sxs-lookup"><span data-stu-id="0cb8a-170">4</span></span>|<span data-ttu-id="0cb8a-171">8</span><span class="sxs-lookup"><span data-stu-id="0cb8a-171">8</span></span>|<span data-ttu-id="0cb8a-172">64%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-172">64%</span></span>|  
|`datetime`|<span data-ttu-id="0cb8a-173">8</span><span class="sxs-lookup"><span data-stu-id="0cb8a-173">8</span></span>|<span data-ttu-id="0cb8a-174">12</span><span class="sxs-lookup"><span data-stu-id="0cb8a-174">12</span></span>|<span data-ttu-id="0cb8a-175">52%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-175">52%</span></span>|  
|`uniqueidentifier`|<span data-ttu-id="0cb8a-176">16</span><span class="sxs-lookup"><span data-stu-id="0cb8a-176">16</span></span>|<span data-ttu-id="0cb8a-177">20</span><span class="sxs-lookup"><span data-stu-id="0cb8a-177">20</span></span>|<span data-ttu-id="0cb8a-178">43%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-178">43%</span></span>|  
|`date`|<span data-ttu-id="0cb8a-179">3</span><span class="sxs-lookup"><span data-stu-id="0cb8a-179">3</span></span>|<span data-ttu-id="0cb8a-180">7</span><span class="sxs-lookup"><span data-stu-id="0cb8a-180">7</span></span>|<span data-ttu-id="0cb8a-181">69%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-181">69%</span></span>|  
  
 <span data-ttu-id="0cb8a-182">**精確度相依長度資料類型**</span><span class="sxs-lookup"><span data-stu-id="0cb8a-182">**Precision-Dependent-Length Data Types**</span></span>  
  
|<span data-ttu-id="0cb8a-183">資料類型</span><span class="sxs-lookup"><span data-stu-id="0cb8a-183">Data type</span></span>|<span data-ttu-id="0cb8a-184">非疏鬆位元組</span><span class="sxs-lookup"><span data-stu-id="0cb8a-184">Nonsparse bytes</span></span>|<span data-ttu-id="0cb8a-185">疏鬆位元組</span><span class="sxs-lookup"><span data-stu-id="0cb8a-185">Sparse bytes</span></span>|<span data-ttu-id="0cb8a-186">NULL 百分比</span><span class="sxs-lookup"><span data-stu-id="0cb8a-186">NULL percentage</span></span>|  
|---------------|---------------------|------------------|---------------------|  
|`datetime2(0)`|<span data-ttu-id="0cb8a-187">6</span><span class="sxs-lookup"><span data-stu-id="0cb8a-187">6</span></span>|<span data-ttu-id="0cb8a-188">10</span><span class="sxs-lookup"><span data-stu-id="0cb8a-188">10</span></span>|<span data-ttu-id="0cb8a-189">57%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-189">57%</span></span>|  
|`datetime2(7)`|<span data-ttu-id="0cb8a-190">8</span><span class="sxs-lookup"><span data-stu-id="0cb8a-190">8</span></span>|<span data-ttu-id="0cb8a-191">12</span><span class="sxs-lookup"><span data-stu-id="0cb8a-191">12</span></span>|<span data-ttu-id="0cb8a-192">52%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-192">52%</span></span>|  
|`time(0)`|<span data-ttu-id="0cb8a-193">3</span><span class="sxs-lookup"><span data-stu-id="0cb8a-193">3</span></span>|<span data-ttu-id="0cb8a-194">7</span><span class="sxs-lookup"><span data-stu-id="0cb8a-194">7</span></span>|<span data-ttu-id="0cb8a-195">69%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-195">69%</span></span>|  
|`time(7)`|<span data-ttu-id="0cb8a-196">5</span><span class="sxs-lookup"><span data-stu-id="0cb8a-196">5</span></span>|<span data-ttu-id="0cb8a-197">9</span><span class="sxs-lookup"><span data-stu-id="0cb8a-197">9</span></span>|<span data-ttu-id="0cb8a-198">60%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-198">60%</span></span>|  
|`datetimetoffset(0)`|<span data-ttu-id="0cb8a-199">8</span><span class="sxs-lookup"><span data-stu-id="0cb8a-199">8</span></span>|<span data-ttu-id="0cb8a-200">12</span><span class="sxs-lookup"><span data-stu-id="0cb8a-200">12</span></span>|<span data-ttu-id="0cb8a-201">52%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-201">52%</span></span>|  
|`datetimetoffset (7)`|<span data-ttu-id="0cb8a-202">10</span><span class="sxs-lookup"><span data-stu-id="0cb8a-202">10</span></span>|<span data-ttu-id="0cb8a-203">14</span><span class="sxs-lookup"><span data-stu-id="0cb8a-203">14</span></span>|<span data-ttu-id="0cb8a-204">49%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-204">49%</span></span>|  
|`decimal/numeric(1,s)`|<span data-ttu-id="0cb8a-205">5</span><span class="sxs-lookup"><span data-stu-id="0cb8a-205">5</span></span>|<span data-ttu-id="0cb8a-206">9</span><span class="sxs-lookup"><span data-stu-id="0cb8a-206">9</span></span>|<span data-ttu-id="0cb8a-207">60%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-207">60%</span></span>|  
|`decimal/numeric(38,s)`|<span data-ttu-id="0cb8a-208">17</span><span class="sxs-lookup"><span data-stu-id="0cb8a-208">17</span></span>|<span data-ttu-id="0cb8a-209">21</span><span class="sxs-lookup"><span data-stu-id="0cb8a-209">21</span></span>|<span data-ttu-id="0cb8a-210">42%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-210">42%</span></span>|  
|`vardecimal(p,s)`|<span data-ttu-id="0cb8a-211">使用 `decimal` 類型做為保守估計。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-211">Use the `decimal` type as a conservative estimate.</span></span>|||  
  
 <span data-ttu-id="0cb8a-212">**資料相依長度資料類型**</span><span class="sxs-lookup"><span data-stu-id="0cb8a-212">**Data-Dependent-Length Data Types**</span></span>  
  
|<span data-ttu-id="0cb8a-213">資料類型</span><span class="sxs-lookup"><span data-stu-id="0cb8a-213">Data type</span></span>|<span data-ttu-id="0cb8a-214">非疏鬆位元組</span><span class="sxs-lookup"><span data-stu-id="0cb8a-214">Nonsparse bytes</span></span>|<span data-ttu-id="0cb8a-215">疏鬆位元組</span><span class="sxs-lookup"><span data-stu-id="0cb8a-215">Sparse bytes</span></span>|<span data-ttu-id="0cb8a-216">NULL 百分比</span><span class="sxs-lookup"><span data-stu-id="0cb8a-216">NULL percentage</span></span>|  
|---------------|---------------------|------------------|---------------------|  
|`sql_variant`|<span data-ttu-id="0cb8a-217">隨著基礎資料類型而不同</span><span class="sxs-lookup"><span data-stu-id="0cb8a-217">Varies with the underlying data type</span></span>|||  
|<span data-ttu-id="0cb8a-218">`varchar` 或 `char`</span><span class="sxs-lookup"><span data-stu-id="0cb8a-218">`varchar` or `char`</span></span>|<span data-ttu-id="0cb8a-219">2\*</span><span class="sxs-lookup"><span data-stu-id="0cb8a-219">2\*</span></span>|<span data-ttu-id="0cb8a-220">4\*</span><span class="sxs-lookup"><span data-stu-id="0cb8a-220">4\*</span></span>|<span data-ttu-id="0cb8a-221">60%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-221">60%</span></span>|  
|<span data-ttu-id="0cb8a-222">`nvarchar` 或 `nchar`</span><span class="sxs-lookup"><span data-stu-id="0cb8a-222">`nvarchar` or `nchar`</span></span>|<span data-ttu-id="0cb8a-223">2\*</span><span class="sxs-lookup"><span data-stu-id="0cb8a-223">2\*</span></span>|<span data-ttu-id="0cb8a-224">4\*+</span><span class="sxs-lookup"><span data-stu-id="0cb8a-224">4\*+</span></span>|<span data-ttu-id="0cb8a-225">60%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-225">60%</span></span>|  
|<span data-ttu-id="0cb8a-226">`varbinary` 或 `binary`</span><span class="sxs-lookup"><span data-stu-id="0cb8a-226">`varbinary` or `binary`</span></span>|<span data-ttu-id="0cb8a-227">2\*</span><span class="sxs-lookup"><span data-stu-id="0cb8a-227">2\*</span></span>|<span data-ttu-id="0cb8a-228">4\*</span><span class="sxs-lookup"><span data-stu-id="0cb8a-228">4\*</span></span>|<span data-ttu-id="0cb8a-229">60%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-229">60%</span></span>|  
|`xml`|<span data-ttu-id="0cb8a-230">2\*</span><span class="sxs-lookup"><span data-stu-id="0cb8a-230">2\*</span></span>|<span data-ttu-id="0cb8a-231">4\*</span><span class="sxs-lookup"><span data-stu-id="0cb8a-231">4\*</span></span>|<span data-ttu-id="0cb8a-232">60%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-232">60%</span></span>|  
|`hierarchyid`|<span data-ttu-id="0cb8a-233">2\*</span><span class="sxs-lookup"><span data-stu-id="0cb8a-233">2\*</span></span>|<span data-ttu-id="0cb8a-234">4\*</span><span class="sxs-lookup"><span data-stu-id="0cb8a-234">4\*</span></span>|<span data-ttu-id="0cb8a-235">60%</span><span class="sxs-lookup"><span data-stu-id="0cb8a-235">60%</span></span>|  
  
 <span data-ttu-id="0cb8a-236">\*長度等於該類型所包含之資料的平均值，加上 2 或 4 個位元組。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-236">\*The length is equal to the average of the data that is contained in the type, plus 2 or 4 bytes.</span></span>  
  
## <a name="in-memory-overhead-required-for-updates-to-sparse-columns"></a><span data-ttu-id="0cb8a-237">疏鬆資料行之更新所需的記憶體中負擔</span><span class="sxs-lookup"><span data-stu-id="0cb8a-237">In-Memory Overhead Required for Updates to Sparse Columns</span></span>  
 <span data-ttu-id="0cb8a-238">設計具有疏鬆資料行的資料表時，請記住，如果要更新資料列，則資料表中的每個非 Null 疏鬆資料行都需要額外 2 個位元組的負擔。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-238">When designing tables with sparse columns, keep in mind that an additional 2 bytes of overhead are required for each non-null sparse column in the table when a row is being updated.</span></span> <span data-ttu-id="0cb8a-239">由於存在這項額外記憶體需求，因此當資料列大小總計 (包括這個記憶體負擔) 超過 8019，而且無法從資料列發送任何資料行時，更新可能會非預期地失敗並發生錯誤 576。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-239">As a result of this additional memory requirement, updates can fail unexpectedly with error 576 when the total row size, including this memory overhead, exceeds 8019, and no columns can be pushed off the row.</span></span>  
  
 <span data-ttu-id="0cb8a-240">假設某個資料表具有 600 個 bigint 類型的疏鬆資料行。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-240">Consider the example of a table that has 600 sparse columns of type bigint.</span></span> <span data-ttu-id="0cb8a-241">如果共有 571 個非 Null 資料行，則磁碟的大小總計就是 571 \* 12 = 6852 個位元組。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-241">If there are 571 non-null columns, then the total size on disk is 571 \* 12 = 6852 bytes.</span></span> <span data-ttu-id="0cb8a-242">加入額外資料列負擔和疏鬆資料行標頭之後，這個大小會增加至大約 6895 個位元組。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-242">After including additional row overhead and the sparse column header, this increases to around 6895 bytes.</span></span> <span data-ttu-id="0cb8a-243">此頁面仍然具有大約 1124 個位元組的可用磁碟。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-243">The page still has around 1124 bytes available on disk.</span></span> <span data-ttu-id="0cb8a-244">這可能會讓您以為其他資料行都可順利更新。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-244">This can give the impression that additional columns can be updated successfully.</span></span> <span data-ttu-id="0cb8a-245">不過，在更新期間，記憶體中存在額外負擔，也就是 2\*(非 Null 疏鬆資料行的數目)。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-245">However, during the update, there is additional overhead in memory which is 2\*(number of non-null sparse columns).</span></span> <span data-ttu-id="0cb8a-246">在此範例中，新增額外負荷 (2 \* 571 = 1142 個位元組) 會將磁碟的資料列大小增加至大約 8037 個位元組。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-246">In this example, including the additional overhead - 2 \* 571 = 1142 bytes - increases the row size on disk to around 8037 bytes.</span></span> <span data-ttu-id="0cb8a-247">這個大小超過了允許的大小上限：8019 個位元組。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-247">This size exceeds the maximum allowed size of 8019 bytes.</span></span> <span data-ttu-id="0cb8a-248">因為所有資料行都是固定長度資料類型，所以無法從資料列發送資料行。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-248">Since all the columns are fixed-length data types, they cannot be pushed off the row.</span></span> <span data-ttu-id="0cb8a-249">因此，更新就會失敗並發生 576 錯誤。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-249">As a result, the update fails with the 576 error.</span></span>  
  
## <a name="restrictions-for-using-sparse-columns"></a><span data-ttu-id="0cb8a-250">使用疏鬆資料行的限制</span><span class="sxs-lookup"><span data-stu-id="0cb8a-250">Restrictions for Using Sparse Columns</span></span>  
 <span data-ttu-id="0cb8a-251">疏鬆資料行可具有任何 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型，而且其行為就像其他任何資料行一樣，但是有下列限制：</span><span class="sxs-lookup"><span data-stu-id="0cb8a-251">Sparse columns can be of any [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type and behave like any other column with the following restrictions:</span></span>  
  
-   <span data-ttu-id="0cb8a-252">疏鬆資料行必須可為 Null，而且不能有 ROWGUIDCOL 或 IDENTITY 屬性。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-252">A sparse column must be nullable and cannot have the ROWGUIDCOL or IDENTITY properties.</span></span> <span data-ttu-id="0cb8a-253">疏鬆資料行不能是以下資料類型：`text`、`ntext`、`image`、`timestamp`、使用者定義資料類型、`geometry` 或 `geography`，也不能有 FILESTREAM 屬性。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-253">A sparse column cannot be of the following data types: `text`, `ntext`, `image`, `timestamp`, user-defined data type, `geometry`, or `geography`; or have the FILESTREAM attribute.</span></span>  
  
-   <span data-ttu-id="0cb8a-254">疏鬆資料行不能有預設值。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-254">A sparse column cannot have a default value.</span></span>  
  
-   <span data-ttu-id="0cb8a-255">疏鬆資料行無法繫結至規則。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-255">A sparse column cannot be bound to a rule.</span></span>  
  
-   <span data-ttu-id="0cb8a-256">雖然計算資料行可以包含疏鬆資料行，但是計算資料行不能標示為 SPARSE。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-256">Although a computed column can contain a sparse column, a computed column cannot be marked as SPARSE.</span></span>  
  
-   <span data-ttu-id="0cb8a-257">疏鬆資料行不能為叢集索引或唯一主索引鍵索引的一部分。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-257">A sparse column cannot be part of a clustered index or a unique primary key index.</span></span> <span data-ttu-id="0cb8a-258">但是，定義於疏鬆資料行上的保存和非保存的計算資料行都可以是叢集索引鍵的一部分。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-258">However, both persisted and nonpersisted computed columns that are defined on sparse columns can be part of a clustered key.</span></span>  
  
-   <span data-ttu-id="0cb8a-259">疏鬆資料行不能當做叢集索引或堆積的資料分割索引鍵使用；</span><span class="sxs-lookup"><span data-stu-id="0cb8a-259">A sparse column cannot be used as a partition key of a clustered index or heap.</span></span> <span data-ttu-id="0cb8a-260">但是，疏鬆資料行可以當做非叢集索引的資料分割索引鍵使用。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-260">However, a sparse column can be used as the partition key of a nonclustered index.</span></span>  
  
-   <span data-ttu-id="0cb8a-261">疏鬆資料行不能是使用者定義資料表類型的一部分，該類型會用於資料表變數和資料表值參數中。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-261">A sparse column cannot be part of a user-defined table type, which are used in table variables and table-valued parameters.</span></span>  
  
-   <span data-ttu-id="0cb8a-262">疏鬆資料行與資料壓縮不相容。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-262">Sparse columns are incompatible with data compression.</span></span> <span data-ttu-id="0cb8a-263">因此，您無法將疏鬆資料行加入至壓縮的資料表，也無法壓縮包含疏鬆資料行的任何資料表。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-263">Therefore sparse columns cannot be added to compressed tables, nor can any tables containing sparse columns be compressed.</span></span>  
  
-   <span data-ttu-id="0cb8a-264">將資料行從疏鬆變更為非疏鬆 (或相反) 需要變更資料行的儲存格式。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-264">Changing a column from sparse to nonsparse or nonsparse to sparse requires changing the storage format of the column.</span></span> <span data-ttu-id="0cb8a-265">SQL Server Database Engine 會使用下列程序來達成這項變更：</span><span class="sxs-lookup"><span data-stu-id="0cb8a-265">The SQL Server Database Engine uses the following procedure to accomplish this change:</span></span>  
  
    1.  <span data-ttu-id="0cb8a-266">以新的儲存大小和格式，將新的資料行加入至資料表。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-266">Adds a new column to the table in the new storage size and format.</span></span>  
  
    2.  <span data-ttu-id="0cb8a-267">針對資料表中的每個資料列，將儲存在舊資料行中的值更新並複製到新的資料行。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-267">For each row in the table, updates and copies the value stored in the old column to the new column.</span></span>  
  
    3.  <span data-ttu-id="0cb8a-268">從資料表結構描述中移除舊的資料行。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-268">Removes the old column from the table schema.</span></span>  
  
    4.  <span data-ttu-id="0cb8a-269">重建資料表 (如果沒有叢集索引)，或重建叢集索引以回收舊資料行使用的空間。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-269">Rebuilds the table (if there is no clustered index) or rebuilds the clustered index to reclaim space used by the old column.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0cb8a-270">當資料列中的資料大小超過允許的資料列大小上限時，步驟 2 可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-270">Step 2 can fail when the size of the data in the row exceeds the maximum allowable row size.</span></span> <span data-ttu-id="0cb8a-271">這個大小包括儲存在舊資料行中的資料大小以及儲存在新資料行中的更新資料大小。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-271">This size includes the size of the data stored in the old column and the updated data stored in the new column.</span></span> <span data-ttu-id="0cb8a-272">對於不包含任何疏鬆資料行的資料表而言，這個限制為 8060 個位元組。對於包含疏鬆資料行的資料表而言，這個限制為 8018 個位元組。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-272">This limit is 8060 bytes for tables that do not contain any sparse columns or 8018 bytes for tables that contain sparse columns.</span></span> <span data-ttu-id="0cb8a-273">即使所有適合的資料行都已經從資料列發送，還是可能會發生這項錯誤。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-273">This error can occur even if all eligible columns have been pushed off-row.</span></span>  
  
-   <span data-ttu-id="0cb8a-274">當您將非疏鬆資料行變更為疏鬆資料行時，此疏鬆資料行將會耗用更多的空間來儲存非 Null 值。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-274">When you change a non-sparse column to a sparse column, the sparse column will consume more space for non-null values.</span></span> <span data-ttu-id="0cb8a-275">當資料列很接近資料列大小的上限時，此作業可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-275">When a row is close to the maximum row size limit, the operation can fail.</span></span>  
  
## <a name="sql-server-technologies-that-support-sparse-columns"></a><span data-ttu-id="0cb8a-276">支援疏鬆資料行的 SQL Server 技術</span><span class="sxs-lookup"><span data-stu-id="0cb8a-276">SQL Server Technologies That Support Sparse Columns</span></span>  
 <span data-ttu-id="0cb8a-277">本章節說明下列 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術如何支援疏鬆資料行：</span><span class="sxs-lookup"><span data-stu-id="0cb8a-277">This section describes how sparse columns are supported in the following [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technologies:</span></span>  
  
-   <span data-ttu-id="0cb8a-278">異動複寫</span><span class="sxs-lookup"><span data-stu-id="0cb8a-278">Transactional replication</span></span>  
  
     <span data-ttu-id="0cb8a-279">異動複寫支援疏鬆資料行，但是不支援資料行集，資料行集可搭配疏鬆資料行使用。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-279">Transactional replication supports sparse columns, but it does not support column sets, which can be used with sparse columns.</span></span> <span data-ttu-id="0cb8a-280">如需資料行集的詳細資訊，請參閱 [使用資料行集](../tables/use-column-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-280">For more information about column sets, see [Use Column Sets](../tables/use-column-sets.md).</span></span>  
  
     <span data-ttu-id="0cb8a-281">SPARSE 屬性的複寫是由使用 [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) 或使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中 [發行項屬性]\*\*\*\* 對話方塊所指定的結構描述選項所決定。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-281">The replication of the SPARSE attribute is determined by a schema option that is specified by using [sp_addarticle](/sql/relational-databases/system-stored-procedures/sp-addarticle-transact-sql) or by using the **Article Properties** dialog box in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="0cb8a-282">舊版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不支援疏鬆資料行。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-282">Earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] do not support sparse columns.</span></span> <span data-ttu-id="0cb8a-283">如果您必須將資料複寫到舊版，請指定不應該複寫 SPARSE 屬性。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-283">If you must replicate data to an earlier version, specify that the SPARSE attribute should not be replicated.</span></span>  
  
     <span data-ttu-id="0cb8a-284">如果是發行的資料表，您不能將任何新的疏鬆資料行加入資料表，或是變更現有資料行的疏鬆屬性。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-284">For tables that are published, you cannot add any new sparse columns to a table or change the sparse property of an existing column.</span></span> <span data-ttu-id="0cb8a-285">如果需要進行這類作業，請卸除發行集再重新建立。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-285">If such an operation is required, drop and re-create the publication.</span></span>  
  
-   <span data-ttu-id="0cb8a-286">合併式複寫</span><span class="sxs-lookup"><span data-stu-id="0cb8a-286">Merge replication</span></span>  
  
     <span data-ttu-id="0cb8a-287">合併式複寫不支援疏鬆資料行或資料行集。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-287">Merge replication does not support sparse columns or column sets.</span></span>  
  
-   <span data-ttu-id="0cb8a-288">Change tracking</span><span class="sxs-lookup"><span data-stu-id="0cb8a-288">Change tracking</span></span>  
  
     <span data-ttu-id="0cb8a-289">變更追蹤可支援疏鬆資料行和資料行集。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-289">Change tracking supports sparse columns and column sets.</span></span> <span data-ttu-id="0cb8a-290">在資料表中更新資料行集時，變更追蹤會將此動作視為整個資料列的更新。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-290">When a column set is updated in a table, change tracking treats this as an update to the whole row.</span></span> <span data-ttu-id="0cb8a-291">不會提供任何詳細的變更追蹤來取得透過資料行集更新作業所更新的明確疏鬆資料行集合。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-291">No detailed change tracking is provided to obtain the exact set of sparse columns that are updated through the column set update operation.</span></span> <span data-ttu-id="0cb8a-292">如果透過 DML 陳述式明確更新疏鬆資料行，其上的變更追蹤將會正常運作，而且可以識別明確的已變更資料行集合。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-292">If the sparse columns are updated explicitly through a DML statement, change tracking on them will work ordinarily and can identify the exact set of changed columns.</span></span>  
  
-   <span data-ttu-id="0cb8a-293">變更資料擷取</span><span class="sxs-lookup"><span data-stu-id="0cb8a-293">Change data capture</span></span>  
  
     <span data-ttu-id="0cb8a-294">異動資料擷取可支援疏鬆資料行，但是不支援資料行集。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-294">Change data capture supports sparse columns, but it does not support column sets.</span></span>  
  
-   <span data-ttu-id="0cb8a-295">複製資料表時，不會保留資料行的疏鬆屬性。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-295">The sparse property of a column is not preserved when the table is copied.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0cb8a-296">範例</span><span class="sxs-lookup"><span data-stu-id="0cb8a-296">Examples</span></span>  
 <span data-ttu-id="0cb8a-297">在此範例中，文件資料表包含常用的一組 `DocID` 和 `Title`資料行。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-297">In this example, a document table contains a common set that has the columns `DocID` and `Title`.</span></span> <span data-ttu-id="0cb8a-298">生產小組想要所有生產文件的 `ProductionSpecification` 和 `ProductionLocation` 資料行。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-298">The Production group wants a `ProductionSpecification` and `ProductionLocation` column for all production documents.</span></span> <span data-ttu-id="0cb8a-299">行銷小組想要行銷文件的 `MarketingSurveyGroup` 資料行。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-299">The Marketing group wants a `MarketingSurveyGroup` column for marketing documents.</span></span> <span data-ttu-id="0cb8a-300">此範例的程式碼會建立一個使用疏鬆資料行的資料表，並將兩個資料列插入資料表中，然後選取資料表中的資料。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-300">The code in this example creates a table that uses sparse columns, inserts two rows into the table, and then selects data from the table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0cb8a-301">此資料表只有五個資料行，以方便顯示及閱讀。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-301">This table has only five columns to make it easier to display and read.</span></span> <span data-ttu-id="0cb8a-302">如果設定了 ANSI_NULL_DFLT_ON 選項，則將疏鬆資料行宣告為可為 Null 是選擇性的作業。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-302">Declaring the sparse columns to be nullable is optional if the ANSI_NULL_DFLT_ON option is set.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE TABLE DocumentStore  
    (DocID int PRIMARY KEY,  
     Title varchar(200) NOT NULL,  
     ProductionSpecification varchar(20) SPARSE NULL,  
     ProductionLocation smallint SPARSE NULL,  
     MarketingSurveyGroup varchar(20) SPARSE NULL ) ;  
GO  
  
INSERT DocumentStore(DocID, Title, ProductionSpecification, ProductionLocation)  
VALUES (1, 'Tire Spec 1', 'AXZZ217', 27);  
GO  
  
INSERT DocumentStore(DocID, Title, MarketingSurveyGroup)  
VALUES (2, 'Survey 2142', 'Men 25 - 35');  
GO  
```  
  
 <span data-ttu-id="0cb8a-303">從資料表中選取所有資料行將會傳回一般的結果集。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-303">To select all the columns from the table returns an ordinary result set.</span></span>  
  
```  
SELECT * FROM DocumentStore ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID  Title        ProductionSpecification  ProductionLocation  MarketingSurveyGroup`  
  
 `1      Tire Spec 1  AXZZ217                  27                  NULL`  
  
 `2      Survey 2142  NULL                     NULL                Men 25-35`  
  
 <span data-ttu-id="0cb8a-304">由於生產部門對於行銷資料不感興趣，而且他們想要使用一個只會傳回感興趣之資料行的資料行清單，如下列查詢所示。</span><span class="sxs-lookup"><span data-stu-id="0cb8a-304">Because the Production department is not interested in the marketing data, they want to use a column list that returns only columns of interest, as shown in the following query.</span></span>  
  
```  
SELECT DocID, Title, ProductionSpecification, ProductionLocation   
FROM DocumentStore   
WHERE ProductionSpecification IS NOT NULL ;  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `DocID  Title        ProductionSpecification  ProductionLocation`  
  
 `1      Tire Spec 1  AXZZ217                  27`  
  
## <a name="see-also"></a><span data-ttu-id="0cb8a-305">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cb8a-305">See Also</span></span>  
 <span data-ttu-id="0cb8a-306">[使用資料行集](../tables/use-column-sets.md) </span><span class="sxs-lookup"><span data-stu-id="0cb8a-306">[Use Column Sets](../tables/use-column-sets.md) </span></span>  
 <span data-ttu-id="0cb8a-307">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0cb8a-307">[CREATE TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-table-transact-sql) </span></span>  
 <span data-ttu-id="0cb8a-308">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0cb8a-308">[ALTER TABLE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-table-transact-sql) </span></span>  
 [<span data-ttu-id="0cb8a-309">sys.columns &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0cb8a-309">sys.columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-columns-transact-sql)  
  
  
