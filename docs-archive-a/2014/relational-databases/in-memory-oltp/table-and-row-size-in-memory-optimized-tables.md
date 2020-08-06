---
title: 記憶體最佳化資料表中的資料表和資料列大小 | Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: b0a248a4-4488-4cc8-89fc-46906a8c24a1
author: rothja
ms.author: jroth
ms.openlocfilehash: 74cc40b7d1f2d0132d79d1e9ae15c2321ac9b74a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709409"
---
# <a name="table-and-row-size-in-memory-optimized-tables"></a><span data-ttu-id="7cb61-102">記憶體最佳化資料表中的資料表和資料列大小</span><span class="sxs-lookup"><span data-stu-id="7cb61-102">Table and Row Size in Memory-Optimized Tables</span></span>
  <span data-ttu-id="7cb61-103">記憶體最佳化的表格由資料列與索引 (包含資料列的指標) 的集合組成。</span><span class="sxs-lookup"><span data-stu-id="7cb61-103">A memory-optimized table consists of a collection of rows and indexes that contain pointers to rows.</span></span> <span data-ttu-id="7cb61-104">在記憶體最佳化的資料表中，資料列的長度不得超過 8,060 個位元組。</span><span class="sxs-lookup"><span data-stu-id="7cb61-104">In a memory-optimized table, rows cannot be longer than 8,060 bytes.</span></span> <span data-ttu-id="7cb61-105">了解記憶體最佳化的資料表大小將有助於您了解電腦是否有足夠的記憶體。</span><span class="sxs-lookup"><span data-stu-id="7cb61-105">Understanding the size of a memory-optimized table will help you understand if your computer has enough memory.</span></span>  
  
 <span data-ttu-id="7cb61-106">計算資料表和資料列大小有兩個原因：</span><span class="sxs-lookup"><span data-stu-id="7cb61-106">There are two reasons for computing table and row size:</span></span>  
  
-   <span data-ttu-id="7cb61-107">資料表使用多少記憶體？</span><span class="sxs-lookup"><span data-stu-id="7cb61-107">How much memory does a table use?</span></span>  
  
    -   <span data-ttu-id="7cb61-108">資料表所使用的記憶體數量無法精確計算。</span><span class="sxs-lookup"><span data-stu-id="7cb61-108">The amount of memory used by the table cannot be calculated exactly.</span></span> <span data-ttu-id="7cb61-109">許多因素都會影響使用的記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="7cb61-109">Many factors affect the amount of memory used.</span></span> <span data-ttu-id="7cb61-110">這些因素包括像是以頁面為基礎的記憶體配置、位置、快取和填補。</span><span class="sxs-lookup"><span data-stu-id="7cb61-110">Factors such as page-based memory allocation, locality, caching, and padding.</span></span> <span data-ttu-id="7cb61-111">另外還包括擁有相關聯的作用中交易或等待記憶體回收的多個資料列版本。</span><span class="sxs-lookup"><span data-stu-id="7cb61-111">Also, multiple versions of rows that either have active transactions associated or that are waiting for garbage collection.</span></span>  
  
    -   <span data-ttu-id="7cb61-112">資料表中的資料和索引所需的大小下限是由 [資料表大小] 的計算提供，討論如下。</span><span class="sxs-lookup"><span data-stu-id="7cb61-112">The minimum size required for the data and indexes in the table is given by the calculation for [table size], discussed below.</span></span>  
  
    -   <span data-ttu-id="7cb61-113">計算記憶體用量是使用最佳近似值，而且建議您在部署計畫中納入容量規劃。</span><span class="sxs-lookup"><span data-stu-id="7cb61-113">Calculating memory use is at best an approximation and you are advised to include capacity planning in your deployment plans.</span></span>  
  
-   <span data-ttu-id="7cb61-114">資料列的資料大小，以及它是否符合 8,060 個位元組的資料列大小限制？</span><span class="sxs-lookup"><span data-stu-id="7cb61-114">The data size of a row, and does it fit in the 8,060 byte row size limitation?</span></span> <span data-ttu-id="7cb61-115">若要回答這些問題，請使用 [資料列主體大小] 的計算，討論如下。</span><span class="sxs-lookup"><span data-stu-id="7cb61-115">To answer these questions, use the computation for [row body size], discussed below.</span></span>  
  
 <span data-ttu-id="7cb61-116">下圖說明包含索引和資料列的資料表，這些索引和資料列各自擁有資料列標頭和主體：</span><span class="sxs-lookup"><span data-stu-id="7cb61-116">The following figure illustrates a table with indexes and rows, which in turn have row headers and bodies:</span></span>  
  
 <span data-ttu-id="7cb61-117">![記憶體最佳化資料表。](../../database-engine/media/hekaton-guide-1.gif "記憶體最佳化資料表。")</span><span class="sxs-lookup"><span data-stu-id="7cb61-117">![Memory optimized table.](../../database-engine/media/hekaton-guide-1.gif "Memory optimized table.")</span></span>  
<span data-ttu-id="7cb61-118">由索引和資料列組成之記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="7cb61-118">Memory-optimized table, consisting of indexes and rows.</span></span>  
  
 <span data-ttu-id="7cb61-119">資料表的記憶體中大小 (以位元組為單位) 計算如下：</span><span class="sxs-lookup"><span data-stu-id="7cb61-119">The in-memory size of a table, in bytes, is computed as follows:</span></span>  
  
```  
[table size] = [size of index 1] + ... + [size of index n] + ([row size] * [row count])  
```  
  
 <span data-ttu-id="7cb61-120">雜湊索引的大小在資料表建立時就已固定，並且取決於實際值區計數。</span><span class="sxs-lookup"><span data-stu-id="7cb61-120">The size of a hash index is fixed at table creation time and depends on the actual bucket count.</span></span> <span data-ttu-id="7cb61-121">使用索引規格指定的 bucket_count 會無條件進位到最接近的二乘冪，以取得 [實際值區計數]。</span><span class="sxs-lookup"><span data-stu-id="7cb61-121">The bucket_count specified with the index specification is rounded up to the nearest power of 2 to obtain the [actual bucket count].</span></span> <span data-ttu-id="7cb61-122">例如，如果指定的 bucket_count 是 100000，則索引的 [實際值區計數] 為 131072。</span><span class="sxs-lookup"><span data-stu-id="7cb61-122">For example, if the specified bucket_count is 100000, the [actual bucket count] for the index is 131072.</span></span>  
  
```  
[hash index size] = 8 * [actual bucket count]  
```  
  
 <span data-ttu-id="7cb61-123">資料列大小的計算方式是加入標頭和主體：</span><span class="sxs-lookup"><span data-stu-id="7cb61-123">The row size is computed by adding the header and the body:</span></span>  
  
```  
[row size] = [row header size] + [actual row body size]  
[row header size] = 24 + 8 * [number of indices]  
```  
  
 <span data-ttu-id="7cb61-124">**資料列主體大小**</span><span class="sxs-lookup"><span data-stu-id="7cb61-124">**Row body size**</span></span>  
  
 <span data-ttu-id="7cb61-125">下表中討論 [資料列主體大小] 的計算。</span><span class="sxs-lookup"><span data-stu-id="7cb61-125">The calculation of [row body size] is discussed in the following table.</span></span>  
  
 <span data-ttu-id="7cb61-126">資料列主體大小有兩種不同的計算方式，也就是計算的大小和實際大小：</span><span class="sxs-lookup"><span data-stu-id="7cb61-126">There are two different computations for row body size: computed size and the actual size:</span></span>  
  
-   <span data-ttu-id="7cb61-127">計算的大小以 [計算的資料列主體大小] 表示，用於判斷是否超過 8,060 個位元組的資料列大小限制。</span><span class="sxs-lookup"><span data-stu-id="7cb61-127">The computed size, denoted with [computed row body size], is used to determine if the row size limitation of 8,060 bytes is exceeded.</span></span>  
  
-   <span data-ttu-id="7cb61-128">實際大小以 [實際資料列主體大小] 表示，是資料列主體在記憶體中和檢查點檔案中的實際儲存體大小。</span><span class="sxs-lookup"><span data-stu-id="7cb61-128">The actual size, denoted with [actual row body size], is the actual storage size of the row body in memory and in the checkpoint files.</span></span>  
  
 <span data-ttu-id="7cb61-129">[計算的資料列主體大小] 和 [實際資料列主體大小] 兩者的計算方式十分類似。</span><span class="sxs-lookup"><span data-stu-id="7cb61-129">Both [computed row body size] and [actual row body size] are calculated similarly.</span></span> <span data-ttu-id="7cb61-130">唯一的差異在於 (n)varchar(i) 和 varbinary(i) 資料行大小的計算，如下列資料表底部所反映。</span><span class="sxs-lookup"><span data-stu-id="7cb61-130">The only difference is the calculation of the size of (n)varchar(i) and varbinary(i) columns, as reflected at the bottom of the following table.</span></span> <span data-ttu-id="7cb61-131">計算的資料列主體大小使用宣告的大小 *i* 作為資料行的大小，而實際的資料列主體大小使用實際的資料大小。</span><span class="sxs-lookup"><span data-stu-id="7cb61-131">The computed row body size uses the declared size *i* as the size of the column, while the actual row body size uses the actual size of the data.</span></span>  
  
 <span data-ttu-id="7cb61-132">下表描述資料列主體大小的計算，指定為 [實際資料列主體大小] = SUM([淺層類型的大小]) + 2 + 2 \* [深層類型資料行數目]。</span><span class="sxs-lookup"><span data-stu-id="7cb61-132">The following table describes the calculation of the row body size, given as [actual row body size] = SUM([size of shallow types]) + 2 + 2 \* [number of deep type columns].</span></span>  
  
|<span data-ttu-id="7cb61-133">區段</span><span class="sxs-lookup"><span data-stu-id="7cb61-133">Section</span></span>|<span data-ttu-id="7cb61-134">大小</span><span class="sxs-lookup"><span data-stu-id="7cb61-134">Size</span></span>|<span data-ttu-id="7cb61-135">註解</span><span class="sxs-lookup"><span data-stu-id="7cb61-135">Comments</span></span>|  
|-------------|----------|--------------|  
|<span data-ttu-id="7cb61-136">淺層類型資料行</span><span class="sxs-lookup"><span data-stu-id="7cb61-136">Shallow type columns</span></span>|<span data-ttu-id="7cb61-137">SUM([淺層類型的大小])</span><span class="sxs-lookup"><span data-stu-id="7cb61-137">SUM([size of shallow types])</span></span><br /><br /> <span data-ttu-id="7cb61-138">**個別類型的大小如下所示：**</span><span class="sxs-lookup"><span data-stu-id="7cb61-138">**Size of the individual types is as follows:**</span></span><br /><br /> <span data-ttu-id="7cb61-139">Bit &#124; 1</span><span class="sxs-lookup"><span data-stu-id="7cb61-139">Bit &#124; 1</span></span><br /><br /> <span data-ttu-id="7cb61-140">Tinyint &#124; 1</span><span class="sxs-lookup"><span data-stu-id="7cb61-140">Tinyint &#124; 1</span></span><br /><br /> <span data-ttu-id="7cb61-141">Smallint &#124; 2</span><span class="sxs-lookup"><span data-stu-id="7cb61-141">Smallint &#124; 2</span></span><br /><br /> <span data-ttu-id="7cb61-142">Int &#124; 4</span><span class="sxs-lookup"><span data-stu-id="7cb61-142">Int &#124; 4</span></span><br /><br /> <span data-ttu-id="7cb61-143">Real &#124; 4</span><span class="sxs-lookup"><span data-stu-id="7cb61-143">Real &#124; 4</span></span><br /><br /> <span data-ttu-id="7cb61-144">Smalldatetime &#124; 4</span><span class="sxs-lookup"><span data-stu-id="7cb61-144">Smalldatetime &#124; 4</span></span><br /><br /> <span data-ttu-id="7cb61-145">Smallmoney &#124; 4</span><span class="sxs-lookup"><span data-stu-id="7cb61-145">Smallmoney &#124; 4</span></span><br /><br /> <span data-ttu-id="7cb61-146">Bigint &#124; 8</span><span class="sxs-lookup"><span data-stu-id="7cb61-146">Bigint &#124; 8</span></span><br /><br /> <span data-ttu-id="7cb61-147">Datetime &#124; 8</span><span class="sxs-lookup"><span data-stu-id="7cb61-147">Datetime &#124; 8</span></span><br /><br /> <span data-ttu-id="7cb61-148">Datetime2 &#124; 8</span><span class="sxs-lookup"><span data-stu-id="7cb61-148">Datetime2 &#124; 8</span></span><br /><br /> <span data-ttu-id="7cb61-149">Float 8</span><span class="sxs-lookup"><span data-stu-id="7cb61-149">Float 8</span></span><br /><br /> <span data-ttu-id="7cb61-150">Money 8</span><span class="sxs-lookup"><span data-stu-id="7cb61-150">Money 8</span></span><br /><br /> <span data-ttu-id="7cb61-151">數值 (有效位數 <= 18) &#124; 8</span><span class="sxs-lookup"><span data-stu-id="7cb61-151">Numeric (precision <=18) &#124; 8</span></span><br /><br /> <span data-ttu-id="7cb61-152">Time &#124; 8</span><span class="sxs-lookup"><span data-stu-id="7cb61-152">Time &#124; 8</span></span><br /><br /> <span data-ttu-id="7cb61-153">數值 (有效位數>18) &#124; 16</span><span class="sxs-lookup"><span data-stu-id="7cb61-153">Numeric(precision>18) &#124; 16</span></span><br /><br /> <span data-ttu-id="7cb61-154">Uniqueidentifier &#124; 16</span><span class="sxs-lookup"><span data-stu-id="7cb61-154">Uniqueidentifier &#124; 16</span></span>||  
|<span data-ttu-id="7cb61-155">淺層資料行填補</span><span class="sxs-lookup"><span data-stu-id="7cb61-155">Shallow column padding</span></span>|<span data-ttu-id="7cb61-156">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="7cb61-156">Possible values are:</span></span><br /><br /> <span data-ttu-id="7cb61-157">如果有深層類型資料行且淺層資料行的資料大小總計為奇數，則為 1。</span><span class="sxs-lookup"><span data-stu-id="7cb61-157">1 if there are deep type columns and the total data size of the shallow columns is as odd number.</span></span><br /><br /> <span data-ttu-id="7cb61-158">否則為 0</span><span class="sxs-lookup"><span data-stu-id="7cb61-158">0 otherwise</span></span>|<span data-ttu-id="7cb61-159">深層類型是指 (var)binary 和 (n)(var)char 類型。</span><span class="sxs-lookup"><span data-stu-id="7cb61-159">Deep types are the types (var)binary and (n)(var)char.</span></span>|  
|<span data-ttu-id="7cb61-160">深層類型資料行的位移陣列</span><span class="sxs-lookup"><span data-stu-id="7cb61-160">Offset array for deep type columns</span></span>|<span data-ttu-id="7cb61-161">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="7cb61-161">Possible values are:</span></span><br /><br /> <span data-ttu-id="7cb61-162">如果沒有深層類型資料行則為 0</span><span class="sxs-lookup"><span data-stu-id="7cb61-162">0 if there are no deep type columns</span></span><br /><br /> <span data-ttu-id="7cb61-163">否則為 2 + 2 \* [深層類型資料行數目]</span><span class="sxs-lookup"><span data-stu-id="7cb61-163">2 + 2 \* [number of deep type columns] otherwise</span></span>|<span data-ttu-id="7cb61-164">深層類型是指 (var)binary 和 (n)(var)char 類型。</span><span class="sxs-lookup"><span data-stu-id="7cb61-164">Deep types are the types (var)binary and (n)(var)char.</span></span>|  
|<span data-ttu-id="7cb61-165">NULL 陣列</span><span class="sxs-lookup"><span data-stu-id="7cb61-165">NULL array</span></span>|<span data-ttu-id="7cb61-166">[可為 null 的資料行數目] / 8，無條件進位到完整的位元組。</span><span class="sxs-lookup"><span data-stu-id="7cb61-166">[number of nullable columns] / 8, rounded up to full bytes.</span></span>|<span data-ttu-id="7cb61-167">陣列中每個可為 null 的資料行都有一個位元。</span><span class="sxs-lookup"><span data-stu-id="7cb61-167">The array has one bit per nullable column.</span></span> <span data-ttu-id="7cb61-168">這個位元會無條件進位到完整的位元組。</span><span class="sxs-lookup"><span data-stu-id="7cb61-168">This is rounded up to full bytes.</span></span>|  
|<span data-ttu-id="7cb61-169">NULL 陣列填補</span><span class="sxs-lookup"><span data-stu-id="7cb61-169">NULL array padding</span></span>|<span data-ttu-id="7cb61-170">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="7cb61-170">Possible values are:</span></span><br /><br /> <span data-ttu-id="7cb61-171">如果有深層類型資料行且 NULL 陣列的大小為奇數個位元組，則為 1。</span><span class="sxs-lookup"><span data-stu-id="7cb61-171">1 if there are deep type columns and the size of the NULL array is an odd number of bytes.</span></span><br /><br /> <span data-ttu-id="7cb61-172">否則為 0</span><span class="sxs-lookup"><span data-stu-id="7cb61-172">0 otherwise</span></span>|<span data-ttu-id="7cb61-173">深層類型是指 (var)binary 和 (n)(var)char 類型。</span><span class="sxs-lookup"><span data-stu-id="7cb61-173">Deep types are the types (var)binary and (n)(var)char.</span></span>|  
|<span data-ttu-id="7cb61-174">填補</span><span class="sxs-lookup"><span data-stu-id="7cb61-174">Padding</span></span>|<span data-ttu-id="7cb61-175">如果沒有深層類型資料行：0</span><span class="sxs-lookup"><span data-stu-id="7cb61-175">If there are no deep type columns: 0</span></span><br /><br /> <span data-ttu-id="7cb61-176">如果有深層類型資料行，則會根據淺層資料行所需的最大對齊加入 0-7 個位元組填補。</span><span class="sxs-lookup"><span data-stu-id="7cb61-176">If there are deep type columns, 0-7 bytes of padding is added, based on the largest alignment required by a shallow column.</span></span> <span data-ttu-id="7cb61-177">每個淺層資料行的對齊都需等於其大小 (如上面所記載)，除了 GUID 資料行需要 1 個位元組 (非 16) 的對齊，而數值資料行一律需要 8 個位元組 (絕不是 16) 的對齊。</span><span class="sxs-lookup"><span data-stu-id="7cb61-177">Each shallow column requires alignment equal to its size as documented above, except that GUID columns need alignment of 1 byte (not 16) and numeric columns always need alignment of 8 bytes (never 16).</span></span> <span data-ttu-id="7cb61-178">所有淺層資料行之間都會使用最大對齊需求，並且加入 0-7 個位元組填補，使得目前為止的大小總計 (不包括深層類型資料行) 為所需對齊的倍數。</span><span class="sxs-lookup"><span data-stu-id="7cb61-178">The largest alignment requirement among all shallow columns is used, and 0-7 bytes of padding is added in such a way that the total size so far (without the deep type columns) is a multiple of the required alignment.</span></span>|<span data-ttu-id="7cb61-179">深層類型是指 (var)binary 和 (n)(var)char 類型。</span><span class="sxs-lookup"><span data-stu-id="7cb61-179">Deep types are the types (var)binary and (n)(var)char.</span></span>|  
|<span data-ttu-id="7cb61-180">固定長度的深層類型資料行</span><span class="sxs-lookup"><span data-stu-id="7cb61-180">Fixed-length deep type columns</span></span>|<span data-ttu-id="7cb61-181">SUM([固定長度的深層類型資料行大小])</span><span class="sxs-lookup"><span data-stu-id="7cb61-181">SUM([size of fixed length deep type columns])</span></span><br /><br /> <span data-ttu-id="7cb61-182">每個資料行的大小如下所示：</span><span class="sxs-lookup"><span data-stu-id="7cb61-182">The size of each column is as follows:</span></span><br /><br /> <span data-ttu-id="7cb61-183">i 代表 char(i) 和 binary(i)。</span><span class="sxs-lookup"><span data-stu-id="7cb61-183">i for char(i) and binary(i).</span></span><br /><br /> <span data-ttu-id="7cb61-184">2 \* i 代表 nchar(i)</span><span class="sxs-lookup"><span data-stu-id="7cb61-184">2 \* i for nchar(i)</span></span>|<span data-ttu-id="7cb61-185">固定長度的深層類型資料行為 char(i)、nchar(i) 或 binary(i) 類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="7cb61-185">Fixed-length deep type columns are columns of type char(i), nchar(i), or binary(i).</span></span>|  
|<span data-ttu-id="7cb61-186">可變長度的深層類型資料行 [計算的大小]</span><span class="sxs-lookup"><span data-stu-id="7cb61-186">Variable length deep type columns [computed size]</span></span>|<span data-ttu-id="7cb61-187">SUM([可變長度的深層類型資料行計算的大小])</span><span class="sxs-lookup"><span data-stu-id="7cb61-187">SUM([computed size of variable length deep type columns])</span></span><br /><br /> <span data-ttu-id="7cb61-188">每個資料行計算的大小如下所示：</span><span class="sxs-lookup"><span data-stu-id="7cb61-188">The computed size of each column is as follows:</span></span><br /><br /> <span data-ttu-id="7cb61-189">i 代表 varchar(i) 和 varbinary(i)</span><span class="sxs-lookup"><span data-stu-id="7cb61-189">i for varchar(i) and varbinary(i)</span></span><br /><br /> <span data-ttu-id="7cb61-190">2 \* i 代表 nvarchar(i)</span><span class="sxs-lookup"><span data-stu-id="7cb61-190">2 \* i for nvarchar(i)</span></span>|<span data-ttu-id="7cb61-191">這個資料列只會套用至 [計算的資料列主體大小]。</span><span class="sxs-lookup"><span data-stu-id="7cb61-191">This row only applied to [computed row body size].</span></span><br /><br /> <span data-ttu-id="7cb61-192">可變長度的深層類型資料行為 varchar(i)、nvarchar(i) 或 varbinary(i) 類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="7cb61-192">Variable-length deep type columns are columns of type varchar(i), nvarchar(i), or varbinary(i).</span></span> <span data-ttu-id="7cb61-193">計算的大小是由資料行的最大長度 (i) 所決定。</span><span class="sxs-lookup"><span data-stu-id="7cb61-193">The computed size is determined by the max length (i) of the column.</span></span>|  
|<span data-ttu-id="7cb61-194">可變長度的深層類型資料行 [實際大小]</span><span class="sxs-lookup"><span data-stu-id="7cb61-194">Variable length deep type columns [actual size]</span></span>|<span data-ttu-id="7cb61-195">SUM([可變長度的深層類型資料行的實際大小])</span><span class="sxs-lookup"><span data-stu-id="7cb61-195">SUM([actual size of variable length deep type columns])</span></span><br /><br /> <span data-ttu-id="7cb61-196">每個資料行的實際大小如下所示：</span><span class="sxs-lookup"><span data-stu-id="7cb61-196">The actual size of each column is as follows:</span></span><br /><br /> <span data-ttu-id="7cb61-197">n (n 是儲存在資料行中的字元數) 代表 varchar(i)。</span><span class="sxs-lookup"><span data-stu-id="7cb61-197">n, where n is the number of characters stored in the column, for varchar(i).</span></span><br /><br /> <span data-ttu-id="7cb61-198">2 \* n (n 是儲存在資料行中的字元數) 代表 nvarchar(i)。</span><span class="sxs-lookup"><span data-stu-id="7cb61-198">2 \* n, where n is the number of characters stored in the column, for nvarchar(i).</span></span><br /><br /> <span data-ttu-id="7cb61-199">n (n 是儲存在資料行中的位元組數) 代表 varbinary(i)。</span><span class="sxs-lookup"><span data-stu-id="7cb61-199">n, where n is the number of bytes stored in the column, for varbinary(i).</span></span>|<span data-ttu-id="7cb61-200">這個資料列只會套用至 [實際資料列主體大小]。</span><span class="sxs-lookup"><span data-stu-id="7cb61-200">This row only applied to [actual row body size].</span></span><br /><br /> <span data-ttu-id="7cb61-201">實際大小是由儲存在資料列的資料行中的資料所決定。</span><span class="sxs-lookup"><span data-stu-id="7cb61-201">The actual size is determined by the data stored in the columns in the row.</span></span>|  
  
##  <a name="row-structure"></a><a name="bkmk_RowStructure"></a><span data-ttu-id="7cb61-202">資料列結構</span><span class="sxs-lookup"><span data-stu-id="7cb61-202">Row Structure</span></span>  
 <span data-ttu-id="7cb61-203">記憶體最佳化資料表中的資料列具有下列元件：</span><span class="sxs-lookup"><span data-stu-id="7cb61-203">The rows in a memory-optimized table have the following components:</span></span>  
  
-   <span data-ttu-id="7cb61-204">資料列標頭包含實作資料列版本設定所需的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="7cb61-204">The row header contains the timestamp necessary to implement row versioning.</span></span> <span data-ttu-id="7cb61-205">資料列標頭也包含索引指標，用來實作雜湊值區的資料列鏈結 (如上文所述)。</span><span class="sxs-lookup"><span data-stu-id="7cb61-205">The row header also contains the index pointer to implement the row chaining in the hash buckets (described above).</span></span>  
  
-   <span data-ttu-id="7cb61-206">資料列主體包含實際資料行資料，包括一些輔助資訊，如可為 Null 的資料行的 null 陣列以及可變長度資料類型的位移陣列。</span><span class="sxs-lookup"><span data-stu-id="7cb61-206">The row body contains the actual column data, which includes some auxiliary information like the null array for nullable columns and the offset array for variable-length data types.</span></span>  
  
 <span data-ttu-id="7cb61-207">下圖說明有兩個索引的資料表之資料列結構：</span><span class="sxs-lookup"><span data-stu-id="7cb61-207">The following figure illustrates the row structure for a table that has two indexes:</span></span>  
  
 <span data-ttu-id="7cb61-208">![包含兩個索引的資料表資料列結構。](../../database-engine/media/hekaton-tables-4.gif "包含兩個索引的資料表資料列結構。")</span><span class="sxs-lookup"><span data-stu-id="7cb61-208">![Row structure for a table that has two indexes.](../../database-engine/media/hekaton-tables-4.gif "Row structure for a table that has two indexes.")</span></span>  
  
 <span data-ttu-id="7cb61-209">開始和結束時間戳記表示特定資料列版本有效的期間。</span><span class="sxs-lookup"><span data-stu-id="7cb61-209">The begin and end timestamps indicate the period in which a particular row version is valid.</span></span> <span data-ttu-id="7cb61-210">在這個間隔中啟動的交易可以看到這個資料列版本。</span><span class="sxs-lookup"><span data-stu-id="7cb61-210">Transactions that start in this interval can see this row version.</span></span> <span data-ttu-id="7cb61-211">如需詳細資料，請參閱 [Transactions in Memory-Optimized Tables](memory-optimized-tables.md) (記憶體最佳化的資料表中的交易)。</span><span class="sxs-lookup"><span data-stu-id="7cb61-211">For more details see [Transactions in Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
 <span data-ttu-id="7cb61-212">索引指標指向屬於雜湊值區之鏈結中的下一個資料列。</span><span class="sxs-lookup"><span data-stu-id="7cb61-212">The index pointers point to the next row in the chain belonging to the hash bucket.</span></span> <span data-ttu-id="7cb61-213">下圖說明有兩個資料行 (姓名、城市) 之資料表的結構，其中包含兩個索引，一個是姓名資料行的索引，另一個是城市資料行的索引。</span><span class="sxs-lookup"><span data-stu-id="7cb61-213">The following figure illustrates the structure of a table with two columns (name, city), and with two indexes, one on the column name, and one on the column city.</span></span>  
  
 <span data-ttu-id="7cb61-214">![包含兩個資料行和索引的資料表結構。](../../database-engine/media/hekaton-tables-5.gif "包含兩個資料行和索引的資料表結構。")</span><span class="sxs-lookup"><span data-stu-id="7cb61-214">![Structure of a table with two columns and indexes.](../../database-engine/media/hekaton-tables-5.gif "Structure of a table with two columns and indexes.")</span></span>  
  
 <span data-ttu-id="7cb61-215">在此圖中，John 和 Jane 名稱已雜湊到第一個貯體。</span><span class="sxs-lookup"><span data-stu-id="7cb61-215">In this figure, the names John and Jane are hashed to the first bucket.</span></span> <span data-ttu-id="7cb61-216">Susan 已雜湊到第二個貯體。</span><span class="sxs-lookup"><span data-stu-id="7cb61-216">Susan is hashed to the second bucket.</span></span> <span data-ttu-id="7cb61-217">Beijing 和 Bogota 城市已雜湊到第一個貯體。</span><span class="sxs-lookup"><span data-stu-id="7cb61-217">The cities Beijing and Bogota are hashed to the first bucket.</span></span> <span data-ttu-id="7cb61-218">Paris 和 Prague 已雜湊到第二個貯體。</span><span class="sxs-lookup"><span data-stu-id="7cb61-218">Paris and Prague are hashed to the second bucket.</span></span>  
  
 <span data-ttu-id="7cb61-219">因此，名稱雜湊索引的鏈結如下：</span><span class="sxs-lookup"><span data-stu-id="7cb61-219">Thus, the chains for the hash index on name are as follows:</span></span>  
  
-   <span data-ttu-id="7cb61-220">第一個貯體：(John, Beijing)；(John, Paris)；(Jane, Prague)</span><span class="sxs-lookup"><span data-stu-id="7cb61-220">First bucket: (John, Beijing); (John, Paris); (Jane, Prague)</span></span>  
  
-   <span data-ttu-id="7cb61-221">第二個貯體：(Susan, Bogota)</span><span class="sxs-lookup"><span data-stu-id="7cb61-221">Second bucket: (Susan, Bogota)</span></span>  
  
 <span data-ttu-id="7cb61-222">城市索引的鏈結如下：</span><span class="sxs-lookup"><span data-stu-id="7cb61-222">The chains for the index on city are as follows:</span></span>  
  
-   <span data-ttu-id="7cb61-223">第一個貯體：(John, Beijing)，(Susan, Bogota)</span><span class="sxs-lookup"><span data-stu-id="7cb61-223">First bucket: (John, Beijing), (Susan, Bogota)</span></span>  
  
-   <span data-ttu-id="7cb61-224">第二個貯體：(John, Paris)，(Jane, Prague)</span><span class="sxs-lookup"><span data-stu-id="7cb61-224">Second bucket: (John, Paris), (Jane, Prague)</span></span>  
  
 <span data-ttu-id="7cb61-225">結束時間戳記 &#x221e; (無限大) 表示這是目前有效的資料列版本。</span><span class="sxs-lookup"><span data-stu-id="7cb61-225">An end timestamp &#x221e; (infinity) indicates that this is the currently valid version of the row.</span></span> <span data-ttu-id="7cb61-226">自從這個資料列版本寫入後，資料列尚未更新或刪除。</span><span class="sxs-lookup"><span data-stu-id="7cb61-226">The row has not been updated or deleted since this row version was written.</span></span>  
  
 <span data-ttu-id="7cb61-227">對於大於 200 的時間，資料表包含下列資料列：</span><span class="sxs-lookup"><span data-stu-id="7cb61-227">For a time greater than 200, the table contains the following rows:</span></span>  
  
|<span data-ttu-id="7cb61-228">名稱</span><span class="sxs-lookup"><span data-stu-id="7cb61-228">Name</span></span>|<span data-ttu-id="7cb61-229">City</span><span class="sxs-lookup"><span data-stu-id="7cb61-229">City</span></span>|  
|----------|----------|  
|<span data-ttu-id="7cb61-230">John</span><span class="sxs-lookup"><span data-stu-id="7cb61-230">John</span></span>|<span data-ttu-id="7cb61-231">北京</span><span class="sxs-lookup"><span data-stu-id="7cb61-231">Beijing</span></span>|  
|<span data-ttu-id="7cb61-232">Jane</span><span class="sxs-lookup"><span data-stu-id="7cb61-232">Jane</span></span>|<span data-ttu-id="7cb61-233">Prague</span><span class="sxs-lookup"><span data-stu-id="7cb61-233">Prague</span></span>|  
  
 <span data-ttu-id="7cb61-234">不過，開始時間為 100 的任何使用中交易都會看到下列版本的資料表：</span><span class="sxs-lookup"><span data-stu-id="7cb61-234">However, any active transaction with begin time 100 will see the following version of the table:</span></span>  
  
|<span data-ttu-id="7cb61-235">名稱</span><span class="sxs-lookup"><span data-stu-id="7cb61-235">Name</span></span>|<span data-ttu-id="7cb61-236">City</span><span class="sxs-lookup"><span data-stu-id="7cb61-236">City</span></span>|  
|----------|----------|  
|<span data-ttu-id="7cb61-237">John</span><span class="sxs-lookup"><span data-stu-id="7cb61-237">John</span></span>|<span data-ttu-id="7cb61-238">Paris</span><span class="sxs-lookup"><span data-stu-id="7cb61-238">Paris</span></span>|  
|<span data-ttu-id="7cb61-239">Jane</span><span class="sxs-lookup"><span data-stu-id="7cb61-239">Jane</span></span>|<span data-ttu-id="7cb61-240">Prague</span><span class="sxs-lookup"><span data-stu-id="7cb61-240">Prague</span></span>|  
|<span data-ttu-id="7cb61-241">Susan</span><span class="sxs-lookup"><span data-stu-id="7cb61-241">Susan</span></span>|<span data-ttu-id="7cb61-242">Bogata</span><span class="sxs-lookup"><span data-stu-id="7cb61-242">Bogata</span></span>|  
  
##  <a name="example-table-and-row-size-computation"></a><a name="bkmk_ExampleComputation"></a> <span data-ttu-id="7cb61-243">範例：資料表和資料列大小計算</span><span class="sxs-lookup"><span data-stu-id="7cb61-243">Example: Table and Row Size Computation</span></span>  
 <span data-ttu-id="7cb61-244">若是雜湊索引，實際值區計數會無條件進位到最接近的二乘冪。</span><span class="sxs-lookup"><span data-stu-id="7cb61-244">For hash indexes, the actual bucket count is rounded up to the nearest power of 2.</span></span> <span data-ttu-id="7cb61-245">例如，如果指定的 bucket_count 是 100000，則索引的實際值區計數為 131072。</span><span class="sxs-lookup"><span data-stu-id="7cb61-245">For example, if the specified bucket_count is 100000, the actual bucket count for the index is 131072.</span></span>  
  
 <span data-ttu-id="7cb61-246">假設 Orders 資料表具有下列定義：</span><span class="sxs-lookup"><span data-stu-id="7cb61-246">Consider an Orders table with the following definition:</span></span>  
  
```sql  
CREATE TABLE dbo.Orders (  
     OrderID int NOT NULL   
           PRIMARY KEY NONCLUSTERED,  
     CustomerID int NOT NULL   
           INDEX IX_CustomerID HASH WITH (BUCKET_COUNT=10000),  
     OrderDate datetime NOT NULL,  
     OrderDescription nvarchar(1000)  
) WITH (MEMORY_OPTIMIZED=ON)  
GO  
```  
  
 <span data-ttu-id="7cb61-247">請注意，此資料表具有一個雜湊索引與一個非叢集索引 (主索引鍵)。</span><span class="sxs-lookup"><span data-stu-id="7cb61-247">Notice that this table has one hash index and a nonclustered index (the primary key).</span></span> <span data-ttu-id="7cb61-248">它還有三個固定長度資料行和一個可變長度資料行，且其中一個資料行可為 NULL (OrderDescription)。</span><span class="sxs-lookup"><span data-stu-id="7cb61-248">It also has three fixed-length columns and one variable-length column, with one of the columns being NULLable (OrderDescription).</span></span> <span data-ttu-id="7cb61-249">假設 Orders 資料表有8379個數據列，而 OrderDescription 資料行中值的平均長度為78個字元。</span><span class="sxs-lookup"><span data-stu-id="7cb61-249">Let's assume the Orders table has 8379 rows, and the average length of the values in the OrderDescription column is 78 characters.</span></span>  
  
 <span data-ttu-id="7cb61-250">若要判斷資料表大小，請先判斷索引的大小。</span><span class="sxs-lookup"><span data-stu-id="7cb61-250">To determine the table size, first determine the size of the indexes.</span></span> <span data-ttu-id="7cb61-251">這兩個索引的 bucket_count 都指定為 10000。</span><span class="sxs-lookup"><span data-stu-id="7cb61-251">The bucket_count for both indexes is specified as 10000.</span></span> <span data-ttu-id="7cb61-252">這會無條件進位到最接近的二乘冪：16384。</span><span class="sxs-lookup"><span data-stu-id="7cb61-252">This is rounded up to the nearest power of 2: 16384.</span></span> <span data-ttu-id="7cb61-253">因此，Orders 資料表的索引大小總計為：</span><span class="sxs-lookup"><span data-stu-id="7cb61-253">Therefore, the total size of the indexes for the Orders table is:</span></span>  
  
```  
8 * 16384 = 131072 bytes  
```  
  
 <span data-ttu-id="7cb61-254">剩下的是資料表資料大小，也就是</span><span class="sxs-lookup"><span data-stu-id="7cb61-254">What remains is the table data size, which is,</span></span>  
  
```  
[row size] * [row count] = [row size] * 8379  
```  
  
 <span data-ttu-id="7cb61-255">(範例資料表有 8379 個資料列)。現在我們有：</span><span class="sxs-lookup"><span data-stu-id="7cb61-255">(The example table has 8379 rows.) Now, we have:</span></span>  
  
```  
[row size] = [row header size] + [actual row body size]  
[row header size] = 24 + 8 * [number of indices] = 24 + 8 * 1 = 32 bytes  
```  
  
 <span data-ttu-id="7cb61-256">接著就來計算 [實際資料列主體大小]：</span><span class="sxs-lookup"><span data-stu-id="7cb61-256">Next, let's calculate [actual row body size]:</span></span>  
  
-   <span data-ttu-id="7cb61-257">淺層類型資料行：</span><span class="sxs-lookup"><span data-stu-id="7cb61-257">Shallow type columns:</span></span>  
  
    ```  
    SUM([size of shallow types]) = 4 [int] + 4 [int] + 8 [datetime] = 16  
    ```  
  
-   <span data-ttu-id="7cb61-258">淺層資料行填補為 0，因為淺層資料行大小總計為偶數。</span><span class="sxs-lookup"><span data-stu-id="7cb61-258">Shallow column padding is 0, as the total shallow column size is even.</span></span>  
  
-   <span data-ttu-id="7cb61-259">深層類型資料行的位移陣列：</span><span class="sxs-lookup"><span data-stu-id="7cb61-259">Offset array for deep type columns:</span></span>  
  
    ```  
    2 + 2 * [number of deep type columns] = 2 + 2 * 1 = 4  
    ```  
  
-   <span data-ttu-id="7cb61-260">NULL 陣列 = 1</span><span class="sxs-lookup"><span data-stu-id="7cb61-260">NULL array = 1</span></span>  
  
-   <span data-ttu-id="7cb61-261">NULL 陣列填補 = 1，因為 NULL 陣列大小為奇數，而且有深層類型資料行。</span><span class="sxs-lookup"><span data-stu-id="7cb61-261">NULL array padding = 1, as the NULL array size is odd and there is a deep type column.</span></span>  
  
-   <span data-ttu-id="7cb61-262">填補</span><span class="sxs-lookup"><span data-stu-id="7cb61-262">Padding</span></span>  
  
    -   <span data-ttu-id="7cb61-263">8 是最大對齊需求。</span><span class="sxs-lookup"><span data-stu-id="7cb61-263">8 is the largest alignment requirement.</span></span>  
  
    -   <span data-ttu-id="7cb61-264">目前為止的大小為 16 + 0 + 4 + 1 + 1 = 22。</span><span class="sxs-lookup"><span data-stu-id="7cb61-264">Size so far is 16 + 0 + 4 + 1 + 1 = 22.</span></span>  
  
    -   <span data-ttu-id="7cb61-265">最接近的 8 倍數是 24。</span><span class="sxs-lookup"><span data-stu-id="7cb61-265">Nearest multiple of 8 is 24.</span></span>  
  
    -   <span data-ttu-id="7cb61-266">總填補為 24 - 22 = 2 個位元組。</span><span class="sxs-lookup"><span data-stu-id="7cb61-266">Total padding is 24 - 22 = 2 bytes.</span></span>  
  
-   <span data-ttu-id="7cb61-267">沒有固定長度的深層類型資料行 (固定長度的深層類型資料行：0。)。</span><span class="sxs-lookup"><span data-stu-id="7cb61-267">There are no fixed-length deep type columns (Fixed-length deep type columns: 0.).</span></span>  
  
-   <span data-ttu-id="7cb61-268">深層類型資料行的實際大小為 2 \* 78 = 156。</span><span class="sxs-lookup"><span data-stu-id="7cb61-268">The actual size of deep type column is 2 \* 78 = 156.</span></span> <span data-ttu-id="7cb61-269">單一深層類型資料行 OrderDescription 的類型為 nvarchar。</span><span class="sxs-lookup"><span data-stu-id="7cb61-269">The single deep type column OrderDescription has type nvarchar.</span></span>  
  
```  
[actual row body size] = 24 + 156 = 180 bytes  
```  
  
 <span data-ttu-id="7cb61-270">若要完成計算：</span><span class="sxs-lookup"><span data-stu-id="7cb61-270">To complete the calculation:</span></span>  
  
```  
[row size] = 32 + 180 = 212 bytes  
[table size] = 8 * 16384 + 212 * 8379 = 131072 + 1776348 = 1907420  
```  
  
 <span data-ttu-id="7cb61-271">因此，記憶體中的總資料表大小約為 2 MB。</span><span class="sxs-lookup"><span data-stu-id="7cb61-271">Total table size in memory is thus approximately 2 megabytes.</span></span> <span data-ttu-id="7cb61-272">這並未涵蓋記憶體配置可能造成的負擔，以及存取這個資料表的交易所需的任何資料列版本設定。</span><span class="sxs-lookup"><span data-stu-id="7cb61-272">This does not account for potential overhead incurred by memory allocation as well as any row versioning required for the transactions accessing this table.</span></span>  
  
 <span data-ttu-id="7cb61-273">這個資料表及其索引實際配置和使用的記憶體可透過下列查詢取得：</span><span class="sxs-lookup"><span data-stu-id="7cb61-273">The actual memory allocated for and used by this table and its indexes can be obtained through the following query:</span></span>  
  
```sql  
select * from sys.dm_db_xtp_table_memory_stats  
where object_id = object_id('dbo.Orders')  
```  
  
## <a name="see-also"></a><span data-ttu-id="7cb61-274">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7cb61-274">See Also</span></span>  
 [<span data-ttu-id="7cb61-275">記憶體最佳化資料表</span><span class="sxs-lookup"><span data-stu-id="7cb61-275">Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
  
