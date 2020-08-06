---
title: 為記憶體最佳化物件定義持久性 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 0fe85fbf-8e8d-4983-96fd-d04b3c7d6d65
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 325f50a74ea75270dd62fc3564200c59255dc6cb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593379"
---
# <a name="defining-durability-for-memory-optimized-objects"></a><span data-ttu-id="d4cf3-102">為記憶體最佳化的物件定義持久性</span><span class="sxs-lookup"><span data-stu-id="d4cf3-102">Defining Durability for Memory-Optimized Objects</span></span>
  <span data-ttu-id="d4cf3-103">記憶體中 OLTP 可保證完整的不可部分完成性、一致性、隔離性與完全持久性 (ACID) 屬性。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-103">In-Memory OLTP guarantees full atomicity, consistency, isolation, and full durability (ACID) properties.</span></span> <span data-ttu-id="d4cf3-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 環境和記憶體最佳化的資料表中的持久性會提供下列保證：</span><span class="sxs-lookup"><span data-stu-id="d4cf3-104">Durability in the context of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and memory-optimized tables provides following guarantees:</span></span>  
  
 <span data-ttu-id="d4cf3-105">交易持久性</span><span class="sxs-lookup"><span data-stu-id="d4cf3-105">Transactional Durability</span></span>  
 <span data-ttu-id="d4cf3-106">當您認可一項對記憶體最佳化資料表進行 (DDL 或 DML) 變更的完全持久交易時，對持久的記憶體最佳化資料表所做的變更就會變成永久變更。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-106">When you commit a fully durable transaction that made (DDL or DML) changes to a memory-optimized table, the changes made to a durable memory-optimized table are permanent.</span></span>  
  
 <span data-ttu-id="d4cf3-107">當您將延遲的持久交易認可到記憶體最佳化資料表時，只有將記憶體中的交易記錄儲存至磁碟之後，交易才會變成持久。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-107">When you commit a delayed durable transaction to a memory-optimized table, the transaction becomes durable only after the in-memory transaction log is saved to disk.</span></span>  
  
 <span data-ttu-id="d4cf3-108">重新啟動持久性</span><span class="sxs-lookup"><span data-stu-id="d4cf3-108">Restart Durability</span></span>  
 <span data-ttu-id="d4cf3-109">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在當機或計劃中的關機之後重新啟動時，記憶體最佳化的持久性資料表會重新具現化，以還原到關機或當機之前的狀態。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-109">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] restarts after a crash or planned shutdown, the memory-optimized durable tables are reinstantiated to restore them to the state before the shutdown or crash.</span></span>  
  
 <span data-ttu-id="d4cf3-110">媒體故障持久性</span><span class="sxs-lookup"><span data-stu-id="d4cf3-110">Media Failure Durability</span></span>  
 <span data-ttu-id="d4cf3-111">如果故障或損毀的磁碟包含持久性記憶體最佳化物件的一個或多個保存複本， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 備份和還原功能會在新的媒體上還原記憶體最佳化的資料表。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-111">If a failed or corrupt disk contains one or more persisted copies of durable memory-optimized objects, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] backup and restore feature restores memory-optimized tables on the new media.</span></span>  
  
 <span data-ttu-id="d4cf3-112">記憶體最佳化的資料表有兩個持久性選項：</span><span class="sxs-lookup"><span data-stu-id="d4cf3-112">There are two durability options for memory-optimized tables:</span></span>  
  
 <span data-ttu-id="d4cf3-113">SCHEMA_ONLY (非持久性資料表)</span><span class="sxs-lookup"><span data-stu-id="d4cf3-113">SCHEMA_ONLY (non-durable table)</span></span>  
 <span data-ttu-id="d4cf3-114">此選項可確保資料表結構描述的持久性，包括索引在內。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-114">This option ensures durability of the table schema, including indexes.</span></span> <span data-ttu-id="d4cf3-115">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 重新啟動時，非持久性資料表會重新建立，但是一開始沒有資料 </span><span class="sxs-lookup"><span data-stu-id="d4cf3-115">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted, the non-durable table is recreated, but starts with no data.</span></span> <span data-ttu-id="d4cf3-116">(這不同於 tempdb 中的資料表，後者的資料表及資料表資料都會在重新啟動之後遺失)。建立非持久性資料表的典型案例為儲存暫時性資料，例如 ETL 處理序的暫存資料表。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-116">(This is unlike a table in tempdb, where both the table and its data are lost upon restart.) A typical scenario for creating a non-durable table is to store transient data, such as a staging table for an ETL process.</span></span> <span data-ttu-id="d4cf3-117">SCHEMA_ONLY 持久性會避免交易記錄和檢查點，這樣可大幅減少 I/O 作業。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-117">A SCHEMA_ONLY durability avoids both transaction logging and checkpoint, which can significantly reduce I/O operations.</span></span>  
  
 <span data-ttu-id="d4cf3-118">SCHEMA_AND_DATA (持久性資料表)</span><span class="sxs-lookup"><span data-stu-id="d4cf3-118">SCHEMA_AND_DATA (durable table)</span></span>  
 <span data-ttu-id="d4cf3-119">此選項提供結構描述和資料的持久性。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-119">This option provides durability of both schema and data.</span></span> <span data-ttu-id="d4cf3-120">資料持久性層級取決於您是否將交易認可為完全持久或具有延遲持久性。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-120">The level of data durability depends on whether you commit a transaction as fully durable or with delayed durability.</span></span> <span data-ttu-id="d4cf3-121">完全持久交易提供與資料和結構描述相同的持久性保證，類似以磁碟為基礎的資料表。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-121">Fully durable transactions provide the same durability guarantee for data and schema, similar to a disk-based table.</span></span> <span data-ttu-id="d4cf3-122">延遲持久性可增進效能，但是在伺服器當機或容錯移轉的情況下可能會導致資料損失。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-122">Delayed durability will improve performance but can potentially result in data loss in case of a server crash or fail over.</span></span> <span data-ttu-id="d4cf3-123">(如需延遲持久性的詳細資訊，請參閱 [控制交易持久性](../logs/control-transaction-durability.md)。)</span><span class="sxs-lookup"><span data-stu-id="d4cf3-123">(For more information about delayed durability, see [Control Transaction Durability](../logs/control-transaction-durability.md).)</span></span>  
  
 <span data-ttu-id="d4cf3-124">系統會將記憶體最佳化的資料表的結構描述保存在資料庫的主要檔案群組中，類似於以磁碟為基礎的資料表。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-124">The schema of the memory-optimized table is persisted, similar to disk-based tables, in the primary file group of a database.</span></span>  
  
 <span data-ttu-id="d4cf3-125">持久的記憶體最佳化資料表中的資料會儲存在資料和差異檔案組中。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-125">Data in durable memory-optimized tables is saved in data and delta file pairs.</span></span>  
  
 <span data-ttu-id="d4cf3-126">記憶體最佳化的資料表中定義的索引只保存在中繼資料中，不會保存在儲存體中。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-126">The indexes defined in memory-optimized tables persist only in metadata, not in storage.</span></span> <span data-ttu-id="d4cf3-127">載入記憶體最佳化的資料表時，將會產生索引結構。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-127">Index structures are generated as part of loading memory-optimized tables.</span></span>  
  
 <span data-ttu-id="d4cf3-128">資料列會由 DELETE 陳述式明確刪除或由 UPDATE 陳述式間接刪除。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-128">Rows are deleted either explicitly by a DELETE statement or indirectly by an UPDATE statement.</span></span> <span data-ttu-id="d4cf3-129">UPDATE 作業會當做插入之後的刪除來執行。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-129">An UPDATE operation is executed as a delete followed by an insert.</span></span> <span data-ttu-id="d4cf3-130">刪除資料列時，資料檔案不會進行任何變更，但是識別已刪除之資料列的新資料列會附加到對應的差異檔案。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-130">When a row is deleted, no change is made to a data file but a new row, identifying the deleted row, is appended to the corresponding delta file.</span></span>  
  
 <span data-ttu-id="d4cf3-131">在復原或還原作業期間，記憶體中 OLTP 引擎會讀取資料和差異檔案，以便將資料載入實體記憶體中。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-131">During recovery or restore operations, the In-Memory OLTP engine reads data and delta files for loading into physical memory.</span></span> <span data-ttu-id="d4cf3-132">載入時間是由以下條件所決定：</span><span class="sxs-lookup"><span data-stu-id="d4cf3-132">The load time is determined by:</span></span>  
  
-   <span data-ttu-id="d4cf3-133">要載入的資料數量。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-133">The amount of data to load.</span></span>  
  
-   <span data-ttu-id="d4cf3-134">連續 I/O 頻寬。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-134">Sequential I/O bandwidth.</span></span>  
  
-   <span data-ttu-id="d4cf3-135">平行處理原則的程度，取決於檔案容器和處理器核心的數量。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-135">Degree of parallelism, determined by number of file containers and processor cores.</span></span>  
  
-   <span data-ttu-id="d4cf3-136">記錄檔記錄的數目，這些記錄位於需要重做之記錄檔的使用中部分。</span><span class="sxs-lookup"><span data-stu-id="d4cf3-136">The amount of log records in the active portion of the log that need to be redone.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4cf3-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4cf3-137">See Also</span></span>  
 [<span data-ttu-id="d4cf3-138">建立及管理記憶體最佳化物件的儲存體</span><span class="sxs-lookup"><span data-stu-id="d4cf3-138">Creating and Managing Storage for Memory-Optimized Objects</span></span>](creating-and-managing-storage-for-memory-optimized-objects.md)  
  
  
