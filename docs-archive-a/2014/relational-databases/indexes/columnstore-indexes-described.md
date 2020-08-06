---
title: 描述的資料行存放區索引 |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- indexes creation, columnstore
- indexes [SQL Server], columnstore
- columnstore index
- columnstore index, described
- xVelocity, columnstore indexes
ms.assetid: f98af4a5-4523-43b1-be8d-1b03c3217839
author: mikeraymsft
ms.author: mikeray
ms.openlocfilehash: 80a29b8e8cc5b53c09369156a5cf5f717e9447a0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708321"
---
# <a name="columnstore-indexes-described"></a><span data-ttu-id="674d3-102">Columnstore Indexes Described</span><span class="sxs-lookup"><span data-stu-id="674d3-102">Columnstore Indexes Described</span></span>
  <span data-ttu-id="674d3-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]*記憶體*內部資料行存放區索引會使用以資料行為基礎的資料儲存和資料行為基礎的查詢處理來儲存和管理資料。</span><span class="sxs-lookup"><span data-stu-id="674d3-103">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] *in-memory columnstore index* stores and manages data by using column-based data storage and column-based query processing.</span></span> <span data-ttu-id="674d3-104">資料行存放區索引可在主要執行大量載入和唯讀查詢的資料倉儲工作負載中順利運作。</span><span class="sxs-lookup"><span data-stu-id="674d3-104">Columnstore indexes work well for data warehousing workloads that primarily perform bulk loads and read-only queries.</span></span> <span data-ttu-id="674d3-105">與傳統的資料列導向儲存相較之下，使用資料行存放區索引最高可達到 **10 倍查詢效能** 改善，與未壓縮資料大小相較之下，最高可達到 **7 倍資料壓縮** 。</span><span class="sxs-lookup"><span data-stu-id="674d3-105">Use the columnstore index to achieve up to **10x query performance** gains over traditional row-oriented storage, and up to **7x data compression** over the uncompressed data size.</span></span>

> [!NOTE]
>  <span data-ttu-id="674d3-106">我們將叢集資料行存放區索引視為儲存大型資料倉儲事實資料表的標準，並期望它能廣泛用於資料倉儲案例中。</span><span class="sxs-lookup"><span data-stu-id="674d3-106">We view the clustered columnstore index as the standard for storing large data warehousing fact tables, and expect it will be used in most data warehousing scenarios.</span></span> <span data-ttu-id="674d3-107">由於叢集資料行存放區索引可更新，工作負載可以執行大量的插入、更新和刪除作業。</span><span class="sxs-lookup"><span data-stu-id="674d3-107">Since the clustered columnstore index is updateable, your workload can perform a large number of insert, update, and delete operations.</span></span>

## <a name="contents"></a><span data-ttu-id="674d3-108">目錄</span><span class="sxs-lookup"><span data-stu-id="674d3-108">Contents</span></span>

-   [<span data-ttu-id="674d3-109">基本概念</span><span class="sxs-lookup"><span data-stu-id="674d3-109">Basics</span></span>](#basics)

-   [<span data-ttu-id="674d3-110">載入資料</span><span class="sxs-lookup"><span data-stu-id="674d3-110">Loading Data</span></span>](#dataload)

-   [<span data-ttu-id="674d3-111">效能秘訣</span><span class="sxs-lookup"><span data-stu-id="674d3-111">Performance Tips</span></span>](#performance)

-   [<span data-ttu-id="674d3-112">相關工作和主題</span><span class="sxs-lookup"><span data-stu-id="674d3-112">Related Tasks and Topics</span></span>](#related)

##  <a name="basics"></a><a name="basics"></a><span data-ttu-id="674d3-113">操作</span><span class="sxs-lookup"><span data-stu-id="674d3-113">Basics</span></span>
 <span data-ttu-id="674d3-114">*columnstore index* 是使用單欄式資料格式 (稱為「資料行存放區」) 來儲存、擷取及管理資料的一項技術。</span><span class="sxs-lookup"><span data-stu-id="674d3-114">A *columnstore index* is a technology for storing, retrieving and managing data by using a columnar data format, called a columnstore.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="674d3-115">同時支援叢集和非叢集資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="674d3-115">supports both clustered and nonclustered columnstore indexes.</span></span> <span data-ttu-id="674d3-116">此兩者所用記憶體中的資料行存放區技術相同，但在用途和支援的功能上有所差異。</span><span class="sxs-lookup"><span data-stu-id="674d3-116">Both use the same in-memory columnstore technology, but they do have differences in purpose and in features they support.</span></span>

###  <a name="benefits"></a><a name="benefits"></a> <span data-ttu-id="674d3-117">優點</span><span class="sxs-lookup"><span data-stu-id="674d3-117">Benefits</span></span>
 <span data-ttu-id="674d3-118">資料行存放區索引可在大部分對大型資料集執行分析的唯讀查詢中順利運作。</span><span class="sxs-lookup"><span data-stu-id="674d3-118">Columnstore indexes work well for mostly read-only queries that perform analysis on large data sets.</span></span> <span data-ttu-id="674d3-119">這一類通常是資料倉儲工作負載所使用的查詢。</span><span class="sxs-lookup"><span data-stu-id="674d3-119">Often, these are queries for data warehousing workloads.</span></span> <span data-ttu-id="674d3-120">資料行存放區索引對於使用完整資料表掃描的查詢可帶來極高的效能增益，但若查詢是要查找資料搜尋特定的值則不適用。</span><span class="sxs-lookup"><span data-stu-id="674d3-120">Columnstore indexes give high performance gains for queries that use full table scans, and are not well-suited for queries that seek into the data, searching for a particular value.</span></span>

 <span data-ttu-id="674d3-121">資料行存放區索引的優點：</span><span class="sxs-lookup"><span data-stu-id="674d3-121">Columnstore Index benefits:</span></span>

-   <span data-ttu-id="674d3-122">資料行經常擁有類似的資料，而導致高壓縮率。</span><span class="sxs-lookup"><span data-stu-id="674d3-122">Columns often have similar data, which results in high compression rates.</span></span>

-   <span data-ttu-id="674d3-123">高壓縮率會透過使用較小的記憶體中耗用量改善查詢效能。</span><span class="sxs-lookup"><span data-stu-id="674d3-123">High compression rates improve query performance by using a smaller in-memory footprint.</span></span> <span data-ttu-id="674d3-124">而查詢效能可獲得改善是因為 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 能夠執行更多記憶體中查詢及資料作業。</span><span class="sxs-lookup"><span data-stu-id="674d3-124">In turn, query performance can improve because [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] can perform more query and data operations in-memory.</span></span>

-   <span data-ttu-id="674d3-125">SQL Server 加入了新的查詢執行機制，稱為批次模式執行，能夠大量地降低 CPU 使用率。</span><span class="sxs-lookup"><span data-stu-id="674d3-125">A new query execution mechanism called batch-mode execution has been added to SQL Server that reduces CPU usage by a large amount.</span></span> <span data-ttu-id="674d3-126">批次模式執行已針對資料行存放區儲存格式最佳化並與其密切整合。</span><span class="sxs-lookup"><span data-stu-id="674d3-126">Batch-mode execution is closely integrated with, and optimized around, the columnstore storage format.</span></span> <span data-ttu-id="674d3-127">批次模式執行有時又稱為向量式或向量化執行。</span><span class="sxs-lookup"><span data-stu-id="674d3-127">Batch-mode execution is sometimes known as vector-based or vectorized execution.</span></span>

-   <span data-ttu-id="674d3-128">查詢通常只會選取資料表中的少數資料行，如此可降低讀取實體媒體的總 I/O 量。</span><span class="sxs-lookup"><span data-stu-id="674d3-128">Queries often select only a few columns from a table, which reduces total I/O from the physical media.</span></span>

### <a name="columnstore-versions"></a><span data-ttu-id="674d3-129">資料行存放區版本</span><span class="sxs-lookup"><span data-stu-id="674d3-129">Columnstore Versions</span></span>
 <span data-ttu-id="674d3-130">SQL Server 2012、SQL Server 2012 Parallel Data Warehouse 和 SQL Server 2014 都是使用資料行存放區索引以加速常用的資料倉儲查詢。</span><span class="sxs-lookup"><span data-stu-id="674d3-130">SQL Server 2012, SQL Server 2012 Parallel Data Warehouse, and SQL Server 2014 all use columnstore indexes to accelerate common data warehouse queries.</span></span> <span data-ttu-id="674d3-131">SQL Server 2012 導入了兩項新功能：非叢集資料行存放區索引，還有以所謂的「批次」為單位來處理資料的向量式查詢執行功能。</span><span class="sxs-lookup"><span data-stu-id="674d3-131">SQL Server 2012 introduced two new features: a nonclustered columnstore index and a vector-based query execution capability that processes data in units called "batches."</span></span> <span data-ttu-id="674d3-132">SQL Server 2014 除了有 SQL Server 2012 的功能外，另又導入可更新的叢集資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="674d3-132">SQL Server 2014 has the features of SQL Server 2012 plus updateable clustered columnstore indexes.</span></span>

### <a name="key-characteristics"></a><span data-ttu-id="674d3-133">主要特性</span><span class="sxs-lookup"><span data-stu-id="674d3-133">Key Characteristics</span></span>

||
|-|
|<span data-ttu-id="674d3-134">**適用於**： [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] 至 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="674d3-134">**Applies to**: [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] through [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>|

 <span data-ttu-id="674d3-135">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中，叢集資料行存放區索引：</span><span class="sxs-lookup"><span data-stu-id="674d3-135">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a clustered columnstore index:</span></span>

-   <span data-ttu-id="674d3-136">由 Enterprise、Developer 及 Evaluation Edition 提供。</span><span class="sxs-lookup"><span data-stu-id="674d3-136">Is available in Enterprise, Developer, and Evaluation editions.</span></span>

-   <span data-ttu-id="674d3-137">可更新。</span><span class="sxs-lookup"><span data-stu-id="674d3-137">Is updateable.</span></span>

-   <span data-ttu-id="674d3-138">是整個資料表的主要儲存方法。</span><span class="sxs-lookup"><span data-stu-id="674d3-138">Is the primary storage method for the entire table.</span></span>

-   <span data-ttu-id="674d3-139">沒有索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="674d3-139">Has no key columns.</span></span> <span data-ttu-id="674d3-140">所有資料行都是內含資料行。</span><span class="sxs-lookup"><span data-stu-id="674d3-140">All columns are included columns.</span></span>

-   <span data-ttu-id="674d3-141">這是資料表上唯一的索引。</span><span class="sxs-lookup"><span data-stu-id="674d3-141">Is the only index on the table.</span></span> <span data-ttu-id="674d3-142">不可與任何其他索引合併。</span><span class="sxs-lookup"><span data-stu-id="674d3-142">It cannot be combined with any other indexes.</span></span>

-   <span data-ttu-id="674d3-143">可設定為使用資料行存放區或資料行存放區封存壓縮。</span><span class="sxs-lookup"><span data-stu-id="674d3-143">Can be configured to use columnstore or columnstore archival compression.</span></span>

-   <span data-ttu-id="674d3-144">不會實際以排序順序儲存資料行。</span><span class="sxs-lookup"><span data-stu-id="674d3-144">Does not physically store columns in a sorted order.</span></span> <span data-ttu-id="674d3-145">而是儲存資料以改善壓縮和效能。</span><span class="sxs-lookup"><span data-stu-id="674d3-145">Instead, it stores data to improve compression and performance.</span></span>

||
|-|
|<span data-ttu-id="674d3-146">**適用於**： [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 至 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="674d3-146">**Applies to**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] through [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>|

 <span data-ttu-id="674d3-147">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]中，非叢集資料行存放區索引：</span><span class="sxs-lookup"><span data-stu-id="674d3-147">In [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], a nonclustered columnstore index:</span></span>

-   <span data-ttu-id="674d3-148">可對叢集索引或堆積中的資料行子集建立索引。</span><span class="sxs-lookup"><span data-stu-id="674d3-148">Can index a subset of columns in the clustered index or heap.</span></span> <span data-ttu-id="674d3-149">例如，可以對常用的資料行建立索引。</span><span class="sxs-lookup"><span data-stu-id="674d3-149">For example, it can index the frequently used columns.</span></span>

-   <span data-ttu-id="674d3-150">需要額外的儲存體將資料行的副本儲存到索引中。</span><span class="sxs-lookup"><span data-stu-id="674d3-150">Requires extra storage to store a copy of the columns in the index.</span></span>

-   <span data-ttu-id="674d3-151">會藉由重建索引或將資料分割切換入和移出來進行更新。它無法使用 DML 作業（例如 insert、update 和 delete）進行更新。</span><span class="sxs-lookup"><span data-stu-id="674d3-151">Is updated by rebuilding the index or switching partitions in and out. It is not updateable by using the DML operations such as insert, update, and delete.</span></span>

-   <span data-ttu-id="674d3-152">可與資料表上的其他索引合併。</span><span class="sxs-lookup"><span data-stu-id="674d3-152">Can be combined with other indexes on the table.</span></span>

-   <span data-ttu-id="674d3-153">可設定為使用資料行存放區或資料行存放區封存壓縮。</span><span class="sxs-lookup"><span data-stu-id="674d3-153">Can be configured to use columnstore or columnstore archival compression.</span></span>

-   <span data-ttu-id="674d3-154">不會實際以排序順序儲存資料行。</span><span class="sxs-lookup"><span data-stu-id="674d3-154">Does not physically store columns in a sorted order.</span></span> <span data-ttu-id="674d3-155">而是儲存資料以改善壓縮和效能。</span><span class="sxs-lookup"><span data-stu-id="674d3-155">Instead, it stores data to improve compression and performance.</span></span> <span data-ttu-id="674d3-156">建立資料行存放區索引之前不需要預先排序資料，但可改善資料行存放區壓縮。</span><span class="sxs-lookup"><span data-stu-id="674d3-156">Pre-sorting the data before creating the columnstore index is not required, but can improve columnstore compression.</span></span>

###  <a name="key-concepts-and-terms"></a><a name="Concepts"></a><span data-ttu-id="674d3-157">重要概念和詞彙</span><span class="sxs-lookup"><span data-stu-id="674d3-157">Key Concepts and Terms</span></span>
 <span data-ttu-id="674d3-158">以下是與資料行存放區索引相關聯的主要詞彙和概念。</span><span class="sxs-lookup"><span data-stu-id="674d3-158">The following key terms and concepts are associated with columnstore indexes.</span></span>

 <span data-ttu-id="674d3-159">資料行存放區索引資料行存放區*索引*是一項技術，可使用單欄式資料格式（稱為「資料行存放區」）來儲存、抓取和管理</span><span class="sxs-lookup"><span data-stu-id="674d3-159">columnstore index A *columnstore index* is a technology for storing, retrieving and managing data by using a columnar data format, called a columnstore.</span></span> [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="674d3-160">同時支援叢集和非叢集資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="674d3-160">supports both clustered and nonclustered columnstore indexes.</span></span> <span data-ttu-id="674d3-161">此兩者所用記憶體中的資料行存放區技術相同，但在用途和支援的功能上有所差異。</span><span class="sxs-lookup"><span data-stu-id="674d3-161">Both use the same in-memory columnstore technology, but they do have differences in purpose and in features they support.</span></span>

 <span data-ttu-id="674d3-162">資料行存放*區是以*邏輯方式組織成具有資料列和資料行的資料表，並實際儲存成資料行取向的資料格式。</span><span class="sxs-lookup"><span data-stu-id="674d3-162">columnstore A *columnstore* is data that is logically organized as a table with rows and columns, and physically stored in a column-wise data format.</span></span>

 <span data-ttu-id="674d3-163">rowstore *rowstore*是以邏輯方式組織成具有資料列和資料行的資料表，然後實際儲存為數據列取向資料格式的資料。</span><span class="sxs-lookup"><span data-stu-id="674d3-163">rowstore A *rowstore* is data that is logically organized as a table with rows and columns, and then physically stored in a row-wise data format.</span></span> <span data-ttu-id="674d3-164">這是傳統儲存關聯式資料表資料的方式。</span><span class="sxs-lookup"><span data-stu-id="674d3-164">This has been the traditional way to store relational table data.</span></span>

 <span data-ttu-id="674d3-165">資料列群組和資料行區段：若要取得高效能和高壓縮率，資料行存放區索引會將資料表配量為數據列群組（稱為資料列群組），然後以資料行取向的方式壓縮每個資料列群組。</span><span class="sxs-lookup"><span data-stu-id="674d3-165">rowgroups and column segments For high performance and high compression rates, the columnstore index slices the table into groups of rows, called row groups, and then compresses each row group in a column-wise manner.</span></span> <span data-ttu-id="674d3-166">資料列群組中的資料列數目必須多到足以改善壓縮率，並且少到足以獲益於記憶體中作業。</span><span class="sxs-lookup"><span data-stu-id="674d3-166">The number of rows in the row group must be large enough to improve compression rates, and small enough to benefit from in-memory operations.</span></span>

 <span data-ttu-id="674d3-167">資料列群組*a 資料*列群組是一組會同時壓縮成資料行存放區格式的資料列。</span><span class="sxs-lookup"><span data-stu-id="674d3-167">row group A *rowgroup* is a group of rows that are compressed into columnstore format at the same time.</span></span>

 <span data-ttu-id="674d3-168">資料行區段：資料*行區段*是資料列群組內的資料行。</span><span class="sxs-lookup"><span data-stu-id="674d3-168">column segment A *column segment* is a column of data from within the rowgroup.</span></span>

-   <span data-ttu-id="674d3-169">資料列群組通常包含了每一資料列群組的資料列數目上限，即 1,048,576 個資料列。</span><span class="sxs-lookup"><span data-stu-id="674d3-169">A rowgroup usually contains the maximum number of rows per rowgroup which is 1,048,576 rows.</span></span>

-   <span data-ttu-id="674d3-170">每一個資料列群組會針對資料表中的每一個資料行包含一個資料行區段。</span><span class="sxs-lookup"><span data-stu-id="674d3-170">Each rowgroup contains one column segment for every column in the table.</span></span>

-   <span data-ttu-id="674d3-171">每個資料行區段會各自壓縮成一體並且儲存到實體媒體上。</span><span class="sxs-lookup"><span data-stu-id="674d3-171">Each column segment is compressed together and stored on physical media.</span></span>

 <span data-ttu-id="674d3-172">![資料行區段](../../database-engine/media/sql-server-pdw-columnstore-columnsegment.gif "資料行區段")</span><span class="sxs-lookup"><span data-stu-id="674d3-172">![Column segment](../../database-engine/media/sql-server-pdw-columnstore-columnsegment.gif "Column segment")</span></span>

 <span data-ttu-id="674d3-173">非叢集資料行存放區索引：非叢集資料行存放區*索引*是在現有叢集索引或堆積資料表上建立的唯讀索引。</span><span class="sxs-lookup"><span data-stu-id="674d3-173">nonclustered columnstore index A *nonclustered columnstore index* is a read-only index created on an existing clustered index or heap table.</span></span> <span data-ttu-id="674d3-174">其包含了資料行子集的副本，截至包括資料表中的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="674d3-174">It contains a copy of a subset of columns, up to and including all of the columns in the table..</span></span> <span data-ttu-id="674d3-175">當資料表包含非叢集資料行存放區索引時，這是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="674d3-175">The table is read-only while it contains a nonclustered columnstore index.</span></span>

 <span data-ttu-id="674d3-176">非叢集資料行存放區索引讓您單憑資料行存放區索引既可執行分析查詢，同時又能對原始資料表執行唯讀作業。</span><span class="sxs-lookup"><span data-stu-id="674d3-176">A nonclustered columnstore index provides a way to have a columnstore index for running analysis queries while at the same time performing read-only operations on the original table.</span></span>

 <span data-ttu-id="674d3-177">![非叢集資料行存放區索引](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage-nonclustered.gif "非叢集資料行存放區索引")</span><span class="sxs-lookup"><span data-stu-id="674d3-177">![Nonclustered columnstore index](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage-nonclustered.gif "Nonclustered columnstore index")</span></span>

 <span data-ttu-id="674d3-178">叢集資料行存放區索引叢集資料行存放區*索引*是整個資料表的實體儲存體，而且是資料表的唯一索引。</span><span class="sxs-lookup"><span data-stu-id="674d3-178">clustered columnstore index A *clustered columnstore index* is the physical storage for the entire table and is the only index for the table.</span></span> <span data-ttu-id="674d3-179">叢集索引可更新。</span><span class="sxs-lookup"><span data-stu-id="674d3-179">The clustered index is updateable.</span></span> <span data-ttu-id="674d3-180">您可以對索引執行插入、刪除和更新作業，還可將資料大量載入索引。</span><span class="sxs-lookup"><span data-stu-id="674d3-180">You can perform insert, delete, and update operations on the index and you can bulk load data into the index.</span></span>

 <span data-ttu-id="674d3-181">![叢集資料行存放區索引](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage.gif "叢集資料行存放區索引")</span><span class="sxs-lookup"><span data-stu-id="674d3-181">![Clustered Columnstore Index](../../database-engine/media/sql-server-pdw-columnstore-physicalstorage.gif "Clustered Columnstore Index")</span></span>

 <span data-ttu-id="674d3-182">為了減少資料行區段的片段化情況並改善效能，資料行存放區索引可能會暫時將一些資料儲存到資料列存放區資料表 (稱為差異存放區)，加上 B 型樹狀目錄含有已刪除之資料列的識別碼。</span><span class="sxs-lookup"><span data-stu-id="674d3-182">To reduce fragmentation of the column segments and improve performance, the columnstore index might store some data temporarily into a rowstore table, called a deltastore, plus a B-Tree of IDs for deleted rows.</span></span> <span data-ttu-id="674d3-183">差異存放區作業將由幕後處理。</span><span class="sxs-lookup"><span data-stu-id="674d3-183">The deltastore operations are handled behind the scenes.</span></span> <span data-ttu-id="674d3-184">為了能傳回正確的查詢結果，叢集資料行存放區索引會結合資料行存放區和差異存放區兩方面的查詢結果。</span><span class="sxs-lookup"><span data-stu-id="674d3-184">To return the correct query results, the clustered columnstore index combines query results from both the columnstore and the deltastore.</span></span>

 <span data-ttu-id="674d3-185">差異存放區僅搭配叢集資料行存放區索引使用，*差異存放區*是儲存資料列的 rowstore 資料表，直到資料列數目夠大，才能移入資料行存放區。</span><span class="sxs-lookup"><span data-stu-id="674d3-185">deltastore Used with clustered columnstore indexes only, a *deltastore* is a rowstore table that stores rows until the number of rows is large enough to be moved into the columnstore.</span></span> <span data-ttu-id="674d3-186">差異存放區搭配叢集資料行存放區索引使用，可改善載入作業及其他 DML 作業的效能。</span><span class="sxs-lookup"><span data-stu-id="674d3-186">A deltastore is used with clustered columnstore indexes to improve performance for loading and other DML operations.</span></span>

 <span data-ttu-id="674d3-187">在大規模的大量載入過程中，大多數資料列會直接進入資料行存放區，而不經過差異存放區。</span><span class="sxs-lookup"><span data-stu-id="674d3-187">During a large bulk load, most of the rows go directly to the columnstore without passing through the deltastore.</span></span> <span data-ttu-id="674d3-188">大量載入結束時，某些資料列可能因為數量太少，而不符合資料列群組 102,400 個資料列的大小下限。</span><span class="sxs-lookup"><span data-stu-id="674d3-188">Some rows at the end of the bulk load might be too few in number to meet the minimum size of a rowgroup which is 102,400 rows.</span></span> <span data-ttu-id="674d3-189">發生這種情況時，最後這些資料列就會進入差異存放區，而不是資料行存放區。</span><span class="sxs-lookup"><span data-stu-id="674d3-189">When this happens, the final rows go to the deltastore instead of the columnstore.</span></span> <span data-ttu-id="674d3-190">若是少於 102,400 個資料列的小規模大量載入，則所有資料列都將直接進入差異存放區。</span><span class="sxs-lookup"><span data-stu-id="674d3-190">For small bulk loads with less than 102,400 rows, all of the rows go directly to the deltastore.</span></span>

 <span data-ttu-id="674d3-191">差異存放區一旦達到資料列數目上限，就會隨即關閉。</span><span class="sxs-lookup"><span data-stu-id="674d3-191">When the deltastore reaches the maximum number of rows, it becomes closed.</span></span> <span data-ttu-id="674d3-192">Tuple 移動處理序將檢查是否有資料列群組已關閉。</span><span class="sxs-lookup"><span data-stu-id="674d3-192">A tuple-move process checks for closed row groups.</span></span> <span data-ttu-id="674d3-193">只要一發現已關閉的資料列群組，處理序便會予以壓縮並儲存至資料行存放區。</span><span class="sxs-lookup"><span data-stu-id="674d3-193">When it finds the closed rowgroup, it compresses it and stores it into the columnstore.</span></span>

##  <a name="loading-data"></a><a name="dataload"></a><span data-ttu-id="674d3-194">載入資料</span><span class="sxs-lookup"><span data-stu-id="674d3-194">Loading Data</span></span>

###  <a name="loading-data-into-a-nonclustered-columnstore-index"></a><a name="dataload_nci"></a><span data-ttu-id="674d3-195">將資料載入非叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="674d3-195">Loading Data into a Nonclustered Columnstore Index</span></span>
 <span data-ttu-id="674d3-196">若要將資料載入非叢集資料行存放區索引，請先將資料載入至儲存為堆積或叢集索引的傳統 rowstore 資料表，然後再建立具有 Create 資料行存放區索引[&#40;transact-sql&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql)的非叢集資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="674d3-196">To load data into a nonclustered columnstore index, first load data into a traditional rowstore table stored as a heap or clustered index, and then create the nonclustered columnstore index with [CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-columnstore-index-transact-sql).</span></span>

 <span data-ttu-id="674d3-197">![將資料載入資料行存放區索引](../../database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "將資料載入資料行存放區索引")</span><span class="sxs-lookup"><span data-stu-id="674d3-197">![Loading data into a columnstore index](../../database-engine/media/sql-server-pdw-columnstore-loadprocess-nonclustered.gif "Loading data into a columnstore index")</span></span>

 <span data-ttu-id="674d3-198">凡是具有非叢集資料行存放區索引的資料表，直到卸除或停用索引之前都是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="674d3-198">A table with a nonclustered columnstore index is read-only until the index is dropped or disabled.</span></span> <span data-ttu-id="674d3-199">若要更新資料表和非叢集資料行存放區索引，您可以將資料分割切換入和移出。您也可以停用索引、更新資料表，然後重建索引。</span><span class="sxs-lookup"><span data-stu-id="674d3-199">To update the table and the nonclustered columnstore index you can switch partitions in and out. You can also disable the index, update the table, and then rebuild the index.</span></span>

 <span data-ttu-id="674d3-200">如需詳細資訊，請參閱＜ [Using Nonclustered Columnstore Indexes](indexes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="674d3-200">For more information see [Using Nonclustered Columnstore Indexes](indexes.md)</span></span>

###  <a name="loading-data-into-a-clustered-columnstore-index"></a><a name="dataload_cci"></a><span data-ttu-id="674d3-201">將資料載入叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="674d3-201">Loading Data into a Clustered Columnstore Index</span></span>
 <span data-ttu-id="674d3-202">![載入叢集資料行存放區索引](../../database-engine/media/sql-server-pdw-columnstore-loadprocess.gif "載入叢集資料行存放區索引")</span><span class="sxs-lookup"><span data-stu-id="674d3-202">![Loading into a clustered columnstore index](../../database-engine/media/sql-server-pdw-columnstore-loadprocess.gif "Loading into a clustered columnstore index")</span></span>

 <span data-ttu-id="674d3-203">如圖中所示，若要將資料載入叢集資料行存放區索引中， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="674d3-203">As the diagram suggests, to load data into a clustered columnstore index, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>

1.  <span data-ttu-id="674d3-204">將最大大小的資料列群組直接插入資料行存放區中。</span><span class="sxs-lookup"><span data-stu-id="674d3-204">Inserts maximum-size rowgroups directly into the columnstore.</span></span> <span data-ttu-id="674d3-205">資料載入時，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 會依先到先處理的順序將資料列指派至開放的資料列群組中。</span><span class="sxs-lookup"><span data-stu-id="674d3-205">As the data is loaded, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] assigns the data rows in a first-come first-serve order into an open rowgroup.</span></span>

2.  <span data-ttu-id="674d3-206">每個資料列群組達到其大小的上限後， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="674d3-206">For each rowgroup, after it reaches the maximum size, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]:</span></span>

    1.  <span data-ttu-id="674d3-207">將資料列群組標示為 CLOSED。</span><span class="sxs-lookup"><span data-stu-id="674d3-207">Marks the rowgroup as CLOSED.</span></span>

    2.  <span data-ttu-id="674d3-208">略過差異存放區。</span><span class="sxs-lookup"><span data-stu-id="674d3-208">Bypasses the deltastore.</span></span>

    3.  <span data-ttu-id="674d3-209">利用資料行存放區壓縮對每個含有資料列群組的資料行區段進行壓縮。</span><span class="sxs-lookup"><span data-stu-id="674d3-209">Compresses each column segment with the rowgroup with columnstore compression.</span></span>

    4.  <span data-ttu-id="674d3-210">實際將每個壓縮的資料行區段儲存到資料行存放區。</span><span class="sxs-lookup"><span data-stu-id="674d3-210">Physically stores each compressed column segment into the columnstore.</span></span>

3.  <span data-ttu-id="674d3-211">將其餘資料列插入資料行存放區或差異存放區，如下所示：</span><span class="sxs-lookup"><span data-stu-id="674d3-211">Inserts the remaining rows into the columnstore or the deltastore as follows:</span></span>

    1.  <span data-ttu-id="674d3-212">如果資料列數符合每個資料列群組的資料列數下限需求，則會將資料列加入至資料行存放區。</span><span class="sxs-lookup"><span data-stu-id="674d3-212">If the number of rows meets the minimum rows per rowgroup requirement, the rows are added to the columnstore.</span></span>

    2.  <span data-ttu-id="674d3-213">如果資料列數低於每個資料列群組的資料列數下限，則會將資料列加入至差異存放區。</span><span class="sxs-lookup"><span data-stu-id="674d3-213">If the number of rows is less than the minimum rows per rowgroup, the rows are added to the deltastore.</span></span>

 <span data-ttu-id="674d3-214">如需有關差異存放區各項工作和程序的詳細資訊，請參閱＜ [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="674d3-214">For more information about deltastore tasks and processes, see [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md)</span></span>

##  <a name="performance-tips"></a><a name="performance"></a><span data-ttu-id="674d3-215">效能秘訣</span><span class="sxs-lookup"><span data-stu-id="674d3-215">Performance Tips</span></span>

### <a name="plan-for-enough-memory-to-create-columnstore-indexes-in-parallel"></a><span data-ttu-id="674d3-216">規劃足夠的記憶體以平行建立資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="674d3-216">Plan for enough memory to create columnstore indexes in parallel</span></span>
 <span data-ttu-id="674d3-217">除非記憶體受到限制，資料行存放區索引的建立預設都是平行作業。</span><span class="sxs-lookup"><span data-stu-id="674d3-217">Creating a columnstore index is by default a parallel operation unless memory is constrained.</span></span> <span data-ttu-id="674d3-218">平行建立索引比循序建立索引需要更多的記憶體。</span><span class="sxs-lookup"><span data-stu-id="674d3-218">Creating the index in parallel requires more memory than creating the index serially.</span></span> <span data-ttu-id="674d3-219">在記憶體很寬裕的情況下，建立資料行存放區索引花費的時間大約是根據相同的資料行建構 B 型樹狀目錄的 1.5 倍。</span><span class="sxs-lookup"><span data-stu-id="674d3-219">When there is ample memory, creating a columnstore index takes on the order of 1.5 times as long as building a B-tree on the same columns.</span></span>

 <span data-ttu-id="674d3-220">建立資料行存放區索引所需的記憶體取決於資料行數目、字串資料行的數目、平行處理原則的程度 (DOP) 和資料的特性。</span><span class="sxs-lookup"><span data-stu-id="674d3-220">The memory required for creating a columnstore index depends on the number of columns, the number of string columns, the degree of parallelism (DOP), and the characteristics of the data.</span></span> <span data-ttu-id="674d3-221">例如，假設您的資料表少於一百萬個資料列，SQL Server 便只會使用單一執行緒來建立資料行存放區索引。</span><span class="sxs-lookup"><span data-stu-id="674d3-221">For example, if your table has fewer than one million rows, SQL Server will use only one thread to create the columnstore index.</span></span>

 <span data-ttu-id="674d3-222">如果資料表的資料列數目超過一百萬個，但是 SQL Server 無法取得足夠的記憶體授權可使用 MAXDOP 建立索引，SQL Server 則會視需要自動降低 MAXDOP 以符合所提供的記憶體授權。</span><span class="sxs-lookup"><span data-stu-id="674d3-222">If your table has more than one million rows, but SQL Server cannot get a large enough memory grant to create the index using MAXDOP, SQL Server will automatically decrease MAXDOP as needed to fit into the available memory grant.</span></span>  <span data-ttu-id="674d3-223">在某些情況下若記憶體受到限制，DOP 就必須降至 1 才能建立索引。</span><span class="sxs-lookup"><span data-stu-id="674d3-223">In some cases, DOP must be decreased to one in order to build the index under constrained memory.</span></span>

##  <a name="related-tasks-and-topics"></a><a name="related"></a><span data-ttu-id="674d3-224">相關工作與主題</span><span class="sxs-lookup"><span data-stu-id="674d3-224">Related Tasks and Topics</span></span>

### <a name="nonclustered-columnstore-indexes"></a><span data-ttu-id="674d3-225">非叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="674d3-225">Nonclustered Columnstore Indexes</span></span>
 <span data-ttu-id="674d3-226">如需相關的一般工作，請參閱＜ [Using Nonclustered Columnstore Indexes](../../database-engine/using-nonclustered-columnstore-indexes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="674d3-226">For common tasks, see [Using Nonclustered Columnstore Indexes](../../database-engine/using-nonclustered-columnstore-indexes.md).</span></span>

-   [<span data-ttu-id="674d3-227">CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="674d3-227">CREATE COLUMNSTORE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-columnstore-index-transact-sql)

-   <span data-ttu-id="674d3-228">[ALTER INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/alter-index-transact-sql) with REBUILD。</span><span class="sxs-lookup"><span data-stu-id="674d3-228">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) with REBUILD.</span></span>

-   [<span data-ttu-id="674d3-229">DROP INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="674d3-229">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)

### <a name="clustered-columnstore-indexes"></a><span data-ttu-id="674d3-230">叢集資料行存放區索引</span><span class="sxs-lookup"><span data-stu-id="674d3-230">Clustered Columnstore Indexes</span></span>
 <span data-ttu-id="674d3-231">如需相關的一般工作，請參閱＜ [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md)＞。</span><span class="sxs-lookup"><span data-stu-id="674d3-231">For common tasks, see [Using Clustered Columnstore Indexes](../../database-engine/using-clustered-columnstore-indexes.md).</span></span>

-   [<span data-ttu-id="674d3-232">建立叢集資料行存放區索引 &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="674d3-232">CREATE CLUSTERED COLUMNSTORE INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-columnstore-index-transact-sql)

-   <span data-ttu-id="674d3-233">[ALTER INDEX &#40;transact-sql&#41;](/sql/t-sql/statements/alter-index-transact-sql) with REBUILD 或重新組織。</span><span class="sxs-lookup"><span data-stu-id="674d3-233">[ALTER INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-index-transact-sql) with REBUILD or REORGANIZE.</span></span>

-   [<span data-ttu-id="674d3-234">DROP INDEX &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="674d3-234">DROP INDEX &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-index-transact-sql)

-   [<span data-ttu-id="674d3-235">INSERT &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="674d3-235">INSERT &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/insert-transact-sql)

-   [<span data-ttu-id="674d3-236">UPDATE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="674d3-236">UPDATE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/queries/update-transact-sql)

-   [<span data-ttu-id="674d3-237">DELETE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="674d3-237">DELETE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/delete-transact-sql)

### <a name="metadata"></a><span data-ttu-id="674d3-238">中繼資料</span><span class="sxs-lookup"><span data-stu-id="674d3-238">Metadata</span></span>
 <span data-ttu-id="674d3-239">資料行存放區索引中的所有資料行都將儲存於中繼資料內成為內含資料行。</span><span class="sxs-lookup"><span data-stu-id="674d3-239">All of the columns in a columnstore index are stored in the metadata as included columns.</span></span> <span data-ttu-id="674d3-240">資料行存放區索引沒有索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="674d3-240">The columnstore index does not have key columns.</span></span>

-   [<span data-ttu-id="674d3-241">sys.indexes &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="674d3-241">sys.indexes &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-indexes-transact-sql)

-   [<span data-ttu-id="674d3-242">sys.index_columns &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="674d3-242">sys.index_columns &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-index-columns-transact-sql)

-   [<span data-ttu-id="674d3-243">sys.partitions &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="674d3-243">sys.partitions &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-partitions-transact-sql)

-   [<span data-ttu-id="674d3-244">sys.column_store_segments &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="674d3-244">sys.column_store_segments &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-column-store-segments-transact-sql)

-   [<span data-ttu-id="674d3-245">sys.column_store_dictionaries &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="674d3-245">sys.column_store_dictionaries &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-column-store-dictionaries-transact-sql)

-   [<span data-ttu-id="674d3-246">sys.column_store_row_groups &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="674d3-246">sys.column_store_row_groups &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-column-store-row-groups-transact-sql)


