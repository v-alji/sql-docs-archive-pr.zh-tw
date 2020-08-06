---
title: 設定記憶體最佳化資料表的儲存體 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 6e005de0-3a77-4b91-b497-14cc0f9f6605
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 4e6e5f5a931669e2fc07cb957e60fd9c77b9b735
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708369"
---
# <a name="configuring-storage-for-memory-optimized-tables"></a><span data-ttu-id="bd632-102">設定記憶體最佳化資料表的儲存體</span><span class="sxs-lookup"><span data-stu-id="bd632-102">Configuring Storage for Memory-Optimized Tables</span></span>
  <span data-ttu-id="bd632-103">您必須設定儲存容量和每秒的輸入/輸出作業 (IOPS)。</span><span class="sxs-lookup"><span data-stu-id="bd632-103">You need to configure storage capacity and input/output operations per second (IOPS).</span></span>  
  
## <a name="storage-capacity"></a><span data-ttu-id="bd632-104">儲存體容量</span><span class="sxs-lookup"><span data-stu-id="bd632-104">Storage Capacity</span></span>  
 <span data-ttu-id="bd632-105">請使用 [估計記憶體最佳化資料表的記憶體需求](memory-optimized-tables.md) 中的資訊來預估資料庫的持久性記憶體最佳化資料表在記憶體中的大小。</span><span class="sxs-lookup"><span data-stu-id="bd632-105">Use the information in [Estimate Memory Requirements for Memory-Optimized Tables](memory-optimized-tables.md) to estimate the in-memory size of the database's durable memory-optimized tables.</span></span> <span data-ttu-id="bd632-106">因為不會針對記憶體最佳化資料表保存索引，所以請勿包含索引的大小。</span><span class="sxs-lookup"><span data-stu-id="bd632-106">Because indexes are not persisted for memory-optimized tables, do not include the size of indexes.</span></span> <span data-ttu-id="bd632-107">一旦您決定大小之後，您提供的磁碟空間就必須是持久性記憶體中資料表大小的四倍。</span><span class="sxs-lookup"><span data-stu-id="bd632-107">Once you determine the size, you need to provide disk space that is four times the size of durable, in-memory tables.</span></span>  
  
## <a name="storage-performance"></a><span data-ttu-id="bd632-108">儲存體效能</span><span class="sxs-lookup"><span data-stu-id="bd632-108">Storage Performance</span></span>  
 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] <span data-ttu-id="bd632-109">可能會大幅增加您的工作負載輸送量。</span><span class="sxs-lookup"><span data-stu-id="bd632-109">can significantly increase your workload throughput.</span></span> <span data-ttu-id="bd632-110">因此，請務必確定 IO 不是瓶頸。</span><span class="sxs-lookup"><span data-stu-id="bd632-110">Therefore, it is important to ensure that IO is not a bottleneck.</span></span>  
  
-   <span data-ttu-id="bd632-111">將磁碟資料表移轉到記憶體最佳化資料表時，請確定交易記錄所在的儲存媒體可以支援增加的交易記錄活動。</span><span class="sxs-lookup"><span data-stu-id="bd632-111">When migrating disk-based tables to memory-optimized tables, make sure that the transaction log is on a storage media that can support increased transaction log activity.</span></span> <span data-ttu-id="bd632-112">例如，如果您的儲存媒體支援每秒 100 MB 的交易記錄作業，而且記憶體最佳化資料表會產生五倍的效能，則交易記錄的儲存媒體也必須能夠支援五倍的效能改善，以免交易記錄活動變成效能瓶頸。</span><span class="sxs-lookup"><span data-stu-id="bd632-112">For example, if your storage media supports transaction log operations at 100 MB/sec, and memory-optimized tables result in five times greater performance, the transaction log's storage media must be able to also support five times performance improvement, to prevent the transaction log activity from becoming a performance bottleneck.</span></span>  
  
-   <span data-ttu-id="bd632-113">記憶體最佳化資料表會分散在一個或多個容器的檔案中來保存。</span><span class="sxs-lookup"><span data-stu-id="bd632-113">Memory-optimized tables are persisted in files distributed across one or more containers.</span></span> <span data-ttu-id="bd632-114">通常每個容器都應該對應至其本身的主軸，並用於增加儲存容量及改良效能。</span><span class="sxs-lookup"><span data-stu-id="bd632-114">Each container should typically be mapped to its own spindle and is used both for increased storage capacity and improved performance.</span></span> <span data-ttu-id="bd632-115">您必須確定儲存媒體的連續 IOPS 可支援交易記錄輸送量增加3倍。</span><span class="sxs-lookup"><span data-stu-id="bd632-115">You need to ensure that sequential IOPS of the storage media can support a 3 times increase in transaction log throughput.</span></span>  
  
     <span data-ttu-id="bd632-116">例如，如果記憶體優化資料表在交易記錄檔中產生活動的 500MB/sec，則記憶體優化資料表的儲存體必須支援 1.5 GB/秒。在交易記錄輸送量中支援3倍增加的需求來自于觀察，資料和差異檔案組會先以初始資料寫入，然後在合併作業中必須讀取/重新寫入。</span><span class="sxs-lookup"><span data-stu-id="bd632-116">For example, if memory-optimized tables generate 500MB/sec of activity in the transaction log, the storage for memory-optimized tables must support 1.5GB/sec. The need to support a 3 times increase in transaction log throughput comes from the observation that the data and delta file pairs are first written with the initial data and then need to be read/re-written as part of a merge operation.</span></span>  
  
     <span data-ttu-id="bd632-117">評估儲存體輸送量的另一個因素是記憶體最佳化資料表的復原時間。</span><span class="sxs-lookup"><span data-stu-id="bd632-117">Another factor in estimating throughput for storage is the recovery time for memory-optimized tables.</span></span> <span data-ttu-id="bd632-118">持久性資料表中的資料必須先讀入記憶體中，然後資料庫才可以提供給應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="bd632-118">Data from durable tables must be read into memory before a database is made available to applications.</span></span> <span data-ttu-id="bd632-119">一般來說，將資料載入記憶體最佳化資料表的作業可以根據 IOPS 的速度來進行。</span><span class="sxs-lookup"><span data-stu-id="bd632-119">Commonly, loading data into memory-optimized tables can be done at the speed of IOPS.</span></span> <span data-ttu-id="bd632-120">因此，如果持久性記憶體最佳化資料表的總儲存空間為 60 GB，而您希望能夠在 1 分鐘內載入這些資料，則儲存空間的 IOPS 必須設定為每秒鐘 1 GB。</span><span class="sxs-lookup"><span data-stu-id="bd632-120">So if the total storage for durable, memory-optimized tables is 60 GB and you want to be able to load this data in 1 minute, the IOPS for the storage must be set at 1 GB/sec.</span></span>  
  
-   <span data-ttu-id="bd632-121">如果您有偶數的主軸，您應該建立兩倍的容器數目，每組都對應到相同的主軸。</span><span class="sxs-lookup"><span data-stu-id="bd632-121">If you have even number of spindles, you should create two times the number of containers, each pair mapped to the same spindle.</span></span> <span data-ttu-id="bd632-122">如果要分散 IOPS 和儲存空間，就必須這樣做。</span><span class="sxs-lookup"><span data-stu-id="bd632-122">This is needed to spread the IOPS and the storage.</span></span> <span data-ttu-id="bd632-123">如需詳細資訊，請參閱[記憶體優化的](the-memory-optimized-filegroup.md)檔案群組。</span><span class="sxs-lookup"><span data-stu-id="bd632-123">For more information, see [The Memory Optimized Filegroup](the-memory-optimized-filegroup.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd632-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd632-124">See Also</span></span>  
 [<span data-ttu-id="bd632-125">建立及管理記憶體最佳化物件的儲存體</span><span class="sxs-lookup"><span data-stu-id="bd632-125">Creating and Managing Storage for Memory-Optimized Objects</span></span>](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
