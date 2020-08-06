---
title: 建立及管理記憶體最佳化物件的儲存體 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 622aabe6-95c7-42cc-8768-ac2e679c5089
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 118e5e582a284023dd8e5cc71629d635e79fb989
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594567"
---
# <a name="creating-and-managing-storage-for-memory-optimized-objects"></a><span data-ttu-id="800c1-102">建立及管理記憶體最佳化物件的儲存體</span><span class="sxs-lookup"><span data-stu-id="800c1-102">Creating and Managing Storage for Memory-Optimized Objects</span></span>
  <span data-ttu-id="800c1-103">[!INCLUDE[hek_2](../../includes/hek-2-md.md)] 引擎已整合到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]，讓您在同一資料庫中可擁有記憶體最佳化資料表和 (傳統) 磁碟資料表。</span><span class="sxs-lookup"><span data-stu-id="800c1-103">The [!INCLUDE[hek_2](../../includes/hek-2-md.md)] engine is integrated into [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], which lets you have both memory-optimized tables and (traditional) disk-based tables in the same database.</span></span> <span data-ttu-id="800c1-104">不過，記憶體最佳化資料表的儲存體結構和磁碟資料表不同。</span><span class="sxs-lookup"><span data-stu-id="800c1-104">However, the storage structure for memory-optimized tables is different from disk-based tables.</span></span>  
  
 <span data-ttu-id="800c1-105">磁碟資料表的儲存體有下列索引鍵屬性︰</span><span class="sxs-lookup"><span data-stu-id="800c1-105">Storage for disk-based table has following key attributes:</span></span>  
  
-   <span data-ttu-id="800c1-106">對應至檔案群組，且檔案群組包含一或多個檔案。</span><span class="sxs-lookup"><span data-stu-id="800c1-106">Mapped to a filegroup and the filegroup contains one or more files.</span></span>  
  
-   <span data-ttu-id="800c1-107">每個檔案會分成 8 頁的範圍，每頁大小為 8K 位元組。</span><span class="sxs-lookup"><span data-stu-id="800c1-107">Each file is divided into extents of 8 pages and each page is of size 8K bytes.</span></span>  
  
-   <span data-ttu-id="800c1-108">範圍可以跨多個資料表共用，但配置的頁面和資料表或索引之間有 1 對 1 的對應。</span><span class="sxs-lookup"><span data-stu-id="800c1-108">An extent can be shared across multiple tables, but a there is 1-to-1 mapping between an allocated page and the table or index.</span></span> <span data-ttu-id="800c1-109">換句話說，一頁中的資料列不能來自兩個或多個資料表或索引。</span><span class="sxs-lookup"><span data-stu-id="800c1-109">In other words, a page can't have rows from two or more tables or index.</span></span>  
  
-   <span data-ttu-id="800c1-110">資料會依需要移入記憶體 (緩衝集區)，已修改或新建的頁面則非同步寫入大部分產生隨機 IO 的磁碟。</span><span class="sxs-lookup"><span data-stu-id="800c1-110">The data is moved into memory (the buffer pool) as needed and the modified or newly created pages are asynchronously written to the disk generating mostly random IO.</span></span>  
  
 <span data-ttu-id="800c1-111">記憶體最佳化資料表的儲存體有下列索引鍵屬性︰</span><span class="sxs-lookup"><span data-stu-id="800c1-111">Storage for memory-optimized tables has following key attributes:</span></span>  
  
-   <span data-ttu-id="800c1-112">所有記憶體優化資料表都會對應到記憶體優化的檔案群組。</span><span class="sxs-lookup"><span data-stu-id="800c1-112">All memory-optimized tables are mapped to a memory-optimized filegroup.</span></span> <span data-ttu-id="800c1-113">這個檔案群組是使用 filestream 檔案群組所建立。</span><span class="sxs-lookup"><span data-stu-id="800c1-113">This filegroup is built using the filestream filegroup.</span></span>  
  
-   <span data-ttu-id="800c1-114">沒有頁面，且資料以資料列保存。</span><span class="sxs-lookup"><span data-stu-id="800c1-114">There are no pages and the data is persisted as a row.</span></span>  
  
-   <span data-ttu-id="800c1-115">記憶體最佳化資料表的所有變更，都會以附加至使用中的檔案方式儲存。</span><span class="sxs-lookup"><span data-stu-id="800c1-115">All changes to memory-optimized tables are stored by appending to active files.</span></span> <span data-ttu-id="800c1-116">讀取和寫入檔案都會循序進行。</span><span class="sxs-lookup"><span data-stu-id="800c1-116">Both reading and writing to files is sequential.</span></span>  
  
-   <span data-ttu-id="800c1-117">更新的實作方式為先插入再刪除。</span><span class="sxs-lookup"><span data-stu-id="800c1-117">An update is implemented as a delete followed by an insert.</span></span> <span data-ttu-id="800c1-118">刪除的資料列不會立即從儲存體移除。</span><span class="sxs-lookup"><span data-stu-id="800c1-118">The deleted rows are not immediately removed from the storage.</span></span> <span data-ttu-id="800c1-119">刪除的資料列是根據 [記憶體最佳化資料表的持久性](memory-optimized-tables.md)中所述的原則，由背景處理序 MERGE 移除。</span><span class="sxs-lookup"><span data-stu-id="800c1-119">The deleted rows are removed by a background process, called MERGE, based on a policy as described in [Durability for Memory-Optimized Tables](memory-optimized-tables.md).</span></span>  
  
-   <span data-ttu-id="800c1-120">和磁碟資料表不同，記憶體最佳化資料表的儲存體不壓縮。</span><span class="sxs-lookup"><span data-stu-id="800c1-120">Unlike disk-based tables, storage for memory-optimized tables is not compressed.</span></span> <span data-ttu-id="800c1-121">將壓縮的 (資料列或頁面) 磁碟資料表移轉至記憶體最佳化資料表時，您必須考量大小的變更。</span><span class="sxs-lookup"><span data-stu-id="800c1-121">When migrating a compressed (ROW or PAGE) disk-based table to memory-optimized table, you will need to account for the change in size.</span></span>  
  
-   <span data-ttu-id="800c1-122">記憶體最佳化資料表可以是耐久的，也可以是非耐久的。</span><span class="sxs-lookup"><span data-stu-id="800c1-122">A memory-optimized table can be durable or can be non-durable.</span></span> <span data-ttu-id="800c1-123">您只需要設定持久性記憶體優化資料表的儲存體。</span><span class="sxs-lookup"><span data-stu-id="800c1-123">You only need to configure storage for durable memory-optimize tables.</span></span>  
  
 <span data-ttu-id="800c1-124">本節將描述檢查點檔案組，以及有關記憶體最佳化資料表中資料的儲存方式等其他方面。</span><span class="sxs-lookup"><span data-stu-id="800c1-124">This section describes checkpoint file pairs and other aspects of how data in memory-optimized tables is stored.</span></span>  
  
 <span data-ttu-id="800c1-125">本節主題：</span><span class="sxs-lookup"><span data-stu-id="800c1-125">Topics in this section:</span></span>  
  
-   [<span data-ttu-id="800c1-126">設定記憶體最佳化資料表的儲存體</span><span class="sxs-lookup"><span data-stu-id="800c1-126">Configuring Storage for Memory-Optimized Tables</span></span>](configuring-storage-for-memory-optimized-tables.md)  
  
-   [<span data-ttu-id="800c1-127">記憶體最佳化檔案群組</span><span class="sxs-lookup"><span data-stu-id="800c1-127">The Memory Optimized Filegroup</span></span>](the-memory-optimized-filegroup.md)  
  
-   [<span data-ttu-id="800c1-128">記憶體最佳化資料表的持久性</span><span class="sxs-lookup"><span data-stu-id="800c1-128">Durability for Memory-Optimized Tables</span></span>](memory-optimized-tables.md)  
  
-   [<span data-ttu-id="800c1-129">記憶體最佳化的資料表的檢查點作業</span><span class="sxs-lookup"><span data-stu-id="800c1-129">Checkpoint Operation for Memory-Optimized Tables</span></span>](checkpoint-operation-for-memory-optimized-tables.md)  
  
-   [<span data-ttu-id="800c1-130">為記憶體最佳化的物件定義持久性</span><span class="sxs-lookup"><span data-stu-id="800c1-130">Defining Durability for Memory-Optimized Objects</span></span>](defining-durability-for-memory-optimized-objects.md)  
  
-   [<span data-ttu-id="800c1-131">比較以磁碟為基礎的資料表儲存體和記憶體最佳化資料表儲存體</span><span class="sxs-lookup"><span data-stu-id="800c1-131">Comparing Disk-Based Table Storage to Memory-Optimized Table Storage</span></span>](comparing-disk-based-table-storage-to-memory-optimized-table-storage.md)  
  
-   [<span data-ttu-id="800c1-132">針對資料檔案和差異檔案組的合併進行監視和疑難排解</span><span class="sxs-lookup"><span data-stu-id="800c1-132">Monitoring and Troubleshooting Merge for Data and Delta File Pairs</span></span>](../../database-engine/monitoring-and-troubleshooting-merge-for-data-and-delta-file-pairs.md)  
  
## <a name="see-also"></a><span data-ttu-id="800c1-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="800c1-133">See Also</span></span>  
 [<span data-ttu-id="800c1-134">記憶體內部 OLTP &#40;記憶體內部最佳化&#41;</span><span class="sxs-lookup"><span data-stu-id="800c1-134">In-Memory OLTP &#40;In-Memory Optimization&#41;</span></span>](in-memory-oltp-in-memory-optimization.md)  
  
  
