---
title: 雜湊索引 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f4bdc9c1-7922-4fac-8183-d11ec58fec4e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 05b8d1e3a5d92078cc2ec3fe7cd5b6d3fb5b47c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708589"
---
# <a name="hash-indexes"></a><span data-ttu-id="b8d86-102">雜湊索引</span><span class="sxs-lookup"><span data-stu-id="b8d86-102">Hash Indexes</span></span>
  <span data-ttu-id="b8d86-103">索引做為記憶體最佳化資料表的進入點。</span><span class="sxs-lookup"><span data-stu-id="b8d86-103">Indexes are used as entry points for memory-optimized tables.</span></span> <span data-ttu-id="b8d86-104">讀取資料表的資料列需要索引，以找出記憶體中的資料。</span><span class="sxs-lookup"><span data-stu-id="b8d86-104">Reading rows from a table requires an index to locate the data in memory.</span></span>  
  
 <span data-ttu-id="b8d86-105">雜湊索引包含以陣列方式組織的貯體集合。</span><span class="sxs-lookup"><span data-stu-id="b8d86-105">A hash index consists of a collection of buckets organized in an array.</span></span> <span data-ttu-id="b8d86-106">雜湊函數會將索引鍵對應到雜湊索引中的對應貯體。</span><span class="sxs-lookup"><span data-stu-id="b8d86-106">A hash function maps index keys to corresponding buckets in the hash index.</span></span> <span data-ttu-id="b8d86-107">下圖顯示三個索引鍵對應到雜湊索引中的三個不同貯體。</span><span class="sxs-lookup"><span data-stu-id="b8d86-107">The following figure shows three index keys that are mapped to three different buckets in the hash index.</span></span> <span data-ttu-id="b8d86-108">為了提供說明，雜湊函數名稱為 f(x)。</span><span class="sxs-lookup"><span data-stu-id="b8d86-108">For illustration purposes the hash function name is f(x).</span></span>  
  
 <span data-ttu-id="b8d86-109">![對應到不同貯體的索引鍵。](../../2014/database-engine/media/hekaton-tables-2.gif "對應到不同貯體的索引鍵。")</span><span class="sxs-lookup"><span data-stu-id="b8d86-109">![Index keys mapped to different buckets.](../../2014/database-engine/media/hekaton-tables-2.gif "Index keys mapped to different buckets.")</span></span>  
  
 <span data-ttu-id="b8d86-110">用於雜湊索引的雜湊函數具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="b8d86-110">The hashing function used for hash indexes has the following characteristics:</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="b8d86-111">有一個雜湊函數可用於所有雜湊索引。</span><span class="sxs-lookup"><span data-stu-id="b8d86-111">has one hash function that is used for all hash indexes.</span></span>  
  
-   <span data-ttu-id="b8d86-112">該雜湊函數具決定性。</span><span class="sxs-lookup"><span data-stu-id="b8d86-112">The hash function is deterministic.</span></span> <span data-ttu-id="b8d86-113">相同索引鍵永遠對應到雜湊索引中的相同貯體。</span><span class="sxs-lookup"><span data-stu-id="b8d86-113">The same index key is always mapped to the same bucket in the hash index.</span></span>  
  
-   <span data-ttu-id="b8d86-114">多個索引鍵可能對應至相同的雜湊值區。</span><span class="sxs-lookup"><span data-stu-id="b8d86-114">Multiple index keys may be mapped to the same hash bucket.</span></span>  
  
-   <span data-ttu-id="b8d86-115">平衡雜湊函數，表示索引鍵值在雜湊值區上的分配通常會遵循波氏分配。</span><span class="sxs-lookup"><span data-stu-id="b8d86-115">The hash function is balanced, meaning that the distribution of index key values over hash buckets typically follows a Poisson distribution.</span></span>  
  
     <span data-ttu-id="b8d86-116">波氏分配不是平均分配。</span><span class="sxs-lookup"><span data-stu-id="b8d86-116">Poisson distribution is not an even distribution.</span></span> <span data-ttu-id="b8d86-117">索引鍵值不會平均分佈在雜湊值區中。</span><span class="sxs-lookup"><span data-stu-id="b8d86-117">Index key values are not evenly distributed in the hash buckets.</span></span> <span data-ttu-id="b8d86-118">例如，在*n*個雜湊值區的*n*個相異索引鍵的波氏分佈，會產生大約一個第三個空值區，其中第一個包含一個索引鍵的值區，另一個則包含兩個索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b8d86-118">For example, a Poisson distribution of *n* distinct index keys over *n* hash buckets results in approximately one third empty buckets, one third of the buckets containing one index key, and the other third containing two index keys.</span></span> <span data-ttu-id="b8d86-119">少數貯體會包含兩個以上的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="b8d86-119">A small number of buckets will contain more than two keys.</span></span>  
  
 <span data-ttu-id="b8d86-120">如果兩個索引鍵對應到相同雜湊值區，就會發生雜湊衝突。</span><span class="sxs-lookup"><span data-stu-id="b8d86-120">If two index keys are mapped to the same hash bucket, there is a hash collision.</span></span> <span data-ttu-id="b8d86-121">大量的雜湊衝突可能會對讀取作業產生效能影響。</span><span class="sxs-lookup"><span data-stu-id="b8d86-121">A large number of hash collisions can have a performance impact on read operations.</span></span>  
  
 <span data-ttu-id="b8d86-122">記憶體中雜湊索引包含記憶體指標陣列。</span><span class="sxs-lookup"><span data-stu-id="b8d86-122">The in-memory hash index structure consists of an array of memory pointers.</span></span> <span data-ttu-id="b8d86-123">每個貯體對應到這個陣列中的位移。</span><span class="sxs-lookup"><span data-stu-id="b8d86-123">Each bucket maps to an offset in this array.</span></span> <span data-ttu-id="b8d86-124">陣列中的每個貯體指向該雜湊值區的第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="b8d86-124">Each bucket in the array points to the first row in that hash bucket.</span></span> <span data-ttu-id="b8d86-125">貯體中的每個資料列指向下一個資料列，因而造成每個雜湊值區的資料列鏈結，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="b8d86-125">Each row in the bucket points to the next row, thus resulting in a chain of rows for each hash bucket, as illustrated in the following figure.</span></span>  
  
 <span data-ttu-id="b8d86-126">![記憶體中的雜湊索引結構。](../../2014/database-engine/media/hekaton-tables-3.gif "記憶體中的雜湊索引結構。")</span><span class="sxs-lookup"><span data-stu-id="b8d86-126">![The in-memory hash index structure.](../../2014/database-engine/media/hekaton-tables-3.gif "The in-memory hash index structure.")</span></span>  
  
 <span data-ttu-id="b8d86-127">此圖中有三個貯體包含資料列。</span><span class="sxs-lookup"><span data-stu-id="b8d86-127">The figure has three buckets with rows.</span></span> <span data-ttu-id="b8d86-128">最上方第二個貯體包含三個紅色資料列。</span><span class="sxs-lookup"><span data-stu-id="b8d86-128">The second bucket from the top contains the three red rows.</span></span> <span data-ttu-id="b8d86-129">第四個貯體包含單一藍色資料列。</span><span class="sxs-lookup"><span data-stu-id="b8d86-129">The fourth bucket contains the single blue row.</span></span> <span data-ttu-id="b8d86-130">最下方的貯體包含兩個綠色資料列。</span><span class="sxs-lookup"><span data-stu-id="b8d86-130">The bottom bucket contains the two green rows.</span></span> <span data-ttu-id="b8d86-131">這些可能是相同資料列的不同版本。</span><span class="sxs-lookup"><span data-stu-id="b8d86-131">These could be different versions of the same row.</span></span>  
  
 <span data-ttu-id="b8d86-132">如需記憶體優化資料表之索引的詳細資訊，請參閱[在記憶體優化資料表上使用索引的指導方針](../relational-databases/in-memory-oltp/memory-optimized-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="b8d86-132">For more information about indexes for memory-optimized tables, see [Guidelines for Using Indexes on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8d86-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8d86-133">See Also</span></span>  
 [<span data-ttu-id="b8d86-134">記憶體最佳化資料表上的索引</span><span class="sxs-lookup"><span data-stu-id="b8d86-134">Indexes on Memory-Optimized Tables</span></span>](../../2014/database-engine/indexes-on-memory-optimized-tables.md)  
  
  
