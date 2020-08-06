---
title: 記憶體最佳化檔案群組 | Microsoft Docs
ms.custom: ''
ms.date: 11/19/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 14106cc9-816b-493a-bcb9-fe66a1cd4630
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: a4ab6423159d0ba5a27af152cc5578905f57eec6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606309"
---
# <a name="the-memory-optimized-filegroup"></a><span data-ttu-id="fba8c-102">記憶體最佳化檔案群組</span><span class="sxs-lookup"><span data-stu-id="fba8c-102">The Memory Optimized Filegroup</span></span>
  <span data-ttu-id="fba8c-103">若要建立記憶體最佳化資料表，您必須先建立記憶體最佳化檔案群組。</span><span class="sxs-lookup"><span data-stu-id="fba8c-103">To create memory-optimized tables, you must first create a memory-optimized filegroup.</span></span> <span data-ttu-id="fba8c-104">記憶體最佳化檔案群組會保存一個或多個容器。</span><span class="sxs-lookup"><span data-stu-id="fba8c-104">The memory-optimized filegroup holds one or more containers.</span></span> <span data-ttu-id="fba8c-105">每個容器都包含資料檔案及/或差異檔案。</span><span class="sxs-lookup"><span data-stu-id="fba8c-105">Each container contains data files or delta files or both.</span></span>  
  
 <span data-ttu-id="fba8c-106">即使 `SCHEMA_ONLY` 資料表中的資料列並未保存，而且記憶體最佳化資料表和原生編譯預存程序的中繼資料儲存在傳統目錄中，則 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 引擎仍然需要 `SCHEMA_ONLY` 記憶體最佳化資料表的記憶體最佳化檔案群組，以便針對具有記憶體最佳化資料表的資料庫提供一致體驗。</span><span class="sxs-lookup"><span data-stu-id="fba8c-106">Even though data rows from `SCHEMA_ONLY` tables are not persisted and the metadata for memory-optimized tables and natively compiled stored procedures is stored in the traditional catalogs, the [!INCLUDE[hek_2](../../includes/hek-2-md.md)] engine still requires a memory-optimized filegroup for `SCHEMA_ONLY` memory-optimized tables to provide a uniform experience for databases with memory-optimized tables.</span></span>  
  
 <span data-ttu-id="fba8c-107">記憶體最佳化檔案群組是根據檔案資料流檔案群組，但有下列差異：</span><span class="sxs-lookup"><span data-stu-id="fba8c-107">The memory-optimized filegroup is based on filestream filegroup, with the following differences:</span></span>  
  
-   <span data-ttu-id="fba8c-108">每個資料庫只能建立一個記憶體最佳化檔案群組。</span><span class="sxs-lookup"><span data-stu-id="fba8c-108">You can only create one memory-optimized filegroup per database.</span></span> <span data-ttu-id="fba8c-109">您必須明確地將檔案群組標示為包含 memory_optimized_data。</span><span class="sxs-lookup"><span data-stu-id="fba8c-109">You need to explicitly mark the filegroup as containing memory_optimized_data.</span></span> <span data-ttu-id="fba8c-110">您可以在建立資料庫時建立檔案群組，或是稍後新增檔案群組：</span><span class="sxs-lookup"><span data-stu-id="fba8c-110">You can create the filegroup when you create the database or you can add it later:</span></span>  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILEGROUP imoltp_mod CONTAINS MEMORY_OPTIMIZED_DATA  
    ```  
  
-   <span data-ttu-id="fba8c-111">您必須將一個或多個容器加入至 MEMORY_OPTIMIZED_DATA 檔案群組。</span><span class="sxs-lookup"><span data-stu-id="fba8c-111">You need to add one or more containers to the MEMORY_OPTIMIZED_DATA filegroup.</span></span> <span data-ttu-id="fba8c-112">例如：</span><span class="sxs-lookup"><span data-stu-id="fba8c-112">For example:</span></span>  
  
    ```sql  
    ALTER DATABASE imoltp ADD FILE (name='imoltp_mod1', filename='c:\data\imoltp_mod1') TO FILEGROUP imoltp_mod  
    ```  
  
-   <span data-ttu-id="fba8c-113">您不需要啟用檔案資料流 ([啟用及設定 FILESTREAM](../blob/enable-and-configure-filestream.md)) 也能建立記憶體最佳化檔案群組。</span><span class="sxs-lookup"><span data-stu-id="fba8c-113">You do not need to enable filestream ([Enable and Configure FILESTREAM](../blob/enable-and-configure-filestream.md)) to create a memory-optimized filegroup.</span></span> <span data-ttu-id="fba8c-114">與檔案資料流的對應是由 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 引擎執行。</span><span class="sxs-lookup"><span data-stu-id="fba8c-114">The mapping to filestream is done by the [!INCLUDE[hek_2](../../includes/hek-2-md.md)] engine.</span></span>  
  
-   <span data-ttu-id="fba8c-115">您可以將新的容器加入至記憶體最佳化檔案群組。</span><span class="sxs-lookup"><span data-stu-id="fba8c-115">You can add new containers to a memory-optimized filegroup.</span></span> <span data-ttu-id="fba8c-116">您可能需要新的容器，以擴充持久性記憶體優化資料表所需的儲存體，並同時在多個容器之間散發 i/o。</span><span class="sxs-lookup"><span data-stu-id="fba8c-116">You may need a new container to expand the storage needed for durable memory-optimized table and also to distribute I/O across multiple containers.</span></span>  
  
-   <span data-ttu-id="fba8c-117">具有記憶體最佳化檔案群組的資料移動會在 AlwaysOn 可用性群組組態中最佳化。</span><span class="sxs-lookup"><span data-stu-id="fba8c-117">Data movement with a memory-optimized filegroup is optimized in an AlwaysOn Availability Group configuration.</span></span> <span data-ttu-id="fba8c-118">不同於傳送到次要複本的檔案資料流檔案，記憶體最佳化檔案群組中的檢查點檔案 (資料和差異處) 不會傳送至次要複本。</span><span class="sxs-lookup"><span data-stu-id="fba8c-118">Unlike filestream files that are sent to secondary replicas, the checkpoint files (both data and delta) within the memory-optimized filegroup are not sent to secondary replicas.</span></span> <span data-ttu-id="fba8c-119">資料和差異檔案會使用次要複本上的交易記錄來建構。</span><span class="sxs-lookup"><span data-stu-id="fba8c-119">The data and delta files are constructed using the transaction log on the secondary replica.</span></span>  
  
<span data-ttu-id="fba8c-120">以下是記憶體最佳化檔案群組的限制。</span><span class="sxs-lookup"><span data-stu-id="fba8c-120">The following limitations of memory-optimized filegroup,</span></span>  
  
-   <span data-ttu-id="fba8c-121">一旦您建立記憶體最佳化檔案群組之後，就可以卸除資料庫來移除它。</span><span class="sxs-lookup"><span data-stu-id="fba8c-121">Once you create a memory-optimized filegroup, you can only remove it by dropping the database.</span></span> <span data-ttu-id="fba8c-122">在實際執行環境中，您不太可能需要移除記憶體最佳化檔案群組。</span><span class="sxs-lookup"><span data-stu-id="fba8c-122">In a production environment, it is unlikely that you will need to remove the memory-optimized filegroup.</span></span>  
  
-   <span data-ttu-id="fba8c-123">您無法卸除非空白的容器或是將資料和差異檔案組移至記憶體最佳化檔案群組中的另一個容器。</span><span class="sxs-lookup"><span data-stu-id="fba8c-123">You cannot drop a non-empty container or move data and delta file pairs to another container in the memory-optimized filegroup.</span></span>  
  
## <a name="configuring-a-memory-optimized-filegroup"></a><span data-ttu-id="fba8c-124">設定記憶體最佳化檔案群組</span><span class="sxs-lookup"><span data-stu-id="fba8c-124">Configuring a Memory-Optimized Filegroup</span></span>  
<span data-ttu-id="fba8c-125">考慮在記憶體最佳化檔案群組中建立多個容器，並將它們分散到不同的磁碟機，以便有更多的頻寬可讓資料流入記憶體中。</span><span class="sxs-lookup"><span data-stu-id="fba8c-125">Consider creating multiple containers in the memory-optimized filegroup and distribute them on different drives to achieve more bandwidth to stream the data into memory.</span></span>  
  
<span data-ttu-id="fba8c-126">當設定儲存空間時，您提供的可用磁碟空間必須是持久性記憶體最佳化資料表大小的四倍。</span><span class="sxs-lookup"><span data-stu-id="fba8c-126">When configuring storage, you must provide free disk space that is four times the size of durable memory-optimized tables.</span></span> <span data-ttu-id="fba8c-127">請確定您的 i/o 子系統支援您的工作負載所需的 IOPS。</span><span class="sxs-lookup"><span data-stu-id="fba8c-127">Ensure that your I/O subsystem supports the required IOPS for your workload.</span></span> <span data-ttu-id="fba8c-128">如果在指定的 IOPS 上填入資料和差異檔案組，您需要 IOPS 的 3 倍來處理儲存和合併作業。</span><span class="sxs-lookup"><span data-stu-id="fba8c-128">If data and delta file pairs are populated at a given IOPS, you need three times that IOPS to account for storing and merge operations.</span></span> <span data-ttu-id="fba8c-129">您可以將一個或多個容器加入至記憶體最佳化檔案群組，以增加儲存容量和 IOPS。</span><span class="sxs-lookup"><span data-stu-id="fba8c-129">You can add storage capacity and IOPS by adding one or more containers to the memory-optimized filegroup.</span></span>  
  
<span data-ttu-id="fba8c-130">在多容器、多磁碟機的案例中，資料和差異檔案會以循環方式配置到容器中。</span><span class="sxs-lookup"><span data-stu-id="fba8c-130">In a multiple container, multiple drive scenario, data and delta files are allocated in a round-robin fashion into containers.</span></span> <span data-ttu-id="fba8c-131">第一個資料檔案會從第一個容器配置，而差異檔案則是從下一個容器配置，依此方式重複這個配置模式。</span><span class="sxs-lookup"><span data-stu-id="fba8c-131">The first data file is allocated from the first container and the delta file is allocated from the next container and this allocation pattern repeats.</span></span> <span data-ttu-id="fba8c-132">如果您有奇數磁碟機 (每個都對應到一個容器)，此配置方案會在所有容器中平均分散資料檔案和差異檔案。</span><span class="sxs-lookup"><span data-stu-id="fba8c-132">This allocation scheme distributes data and delta files evenly across containers if you have an odd number of drives, each mapped to one container.</span></span> <span data-ttu-id="fba8c-133">但是，如果您有偶數磁碟機 (每個都對應到容器)，可能會造成儲存空間不平衡，導致資料檔案對應到奇數磁碟機而差異檔案則對應到偶數磁碟機。</span><span class="sxs-lookup"><span data-stu-id="fba8c-133">However, if you have an even number of drives, each mapped to a container, it can result in imbalanced storage with data files mapped to odd drives and delta files mapped to even drives.</span></span> <span data-ttu-id="fba8c-134">若要在復原時取得平衡的 i/o 串流，請考慮將資料檔案和差異檔案組放在相同的主軸/儲存體上，如下列範例所述。</span><span class="sxs-lookup"><span data-stu-id="fba8c-134">To obtain a balanced stream of I/O on recovery, consider placing pairs of data and delta files on the same spindles/storage as described in the example below.</span></span>  

> [!CAUTION]
> <span data-ttu-id="fba8c-135">若已針對記憶體最佳化檔案群組設定 `MAXSIZE` 值，且檢查點檔案超過容器的大小上限，則資料庫的狀態會變成 SUSPECT。</span><span class="sxs-lookup"><span data-stu-id="fba8c-135">If a `MAXSIZE` value is set for the memory-optimized filegroup, and checkpoint files exceed the max size of the container, then the database will become SUSPECT.</span></span>   
> <span data-ttu-id="fba8c-136">在此情況下，請不要嘗試將資料庫設為 OFFLINE 和 ONLINE，這會造成資料庫狀態進入 RECOVERY_PENDING。</span><span class="sxs-lookup"><span data-stu-id="fba8c-136">In this case do not attempt to set the database OFFLINE and ONLINE, causing the database to stay in RECOVERY_PENDING state.</span></span>
  
### <a name="example"></a><span data-ttu-id="fba8c-137">範例</span><span class="sxs-lookup"><span data-stu-id="fba8c-137">Example</span></span> 
<span data-ttu-id="fba8c-138">假設記憶體最佳化檔案群組有兩個容器：磁碟機 X 上的容器 1 和磁碟機 Y 上的容器 2。</span><span class="sxs-lookup"><span data-stu-id="fba8c-138">Consider a memory-optimized filegroup with two containers: container 1 on drive X and container 2 on drives Y.</span></span>  
<span data-ttu-id="fba8c-139">由於資料檔案和差異檔案的配置是以循環方式進行，所以容器 1 將只有資料檔案，容器 2 將只有差異檔案，這樣導致儲存空間及每秒輸入/輸出作業持續失衡，因為資料檔案明顯大於差異檔案。</span><span class="sxs-lookup"><span data-stu-id="fba8c-139">Since the allocation of data and delta files is done in round-robin fashion, container 1 will only have data files and container 2 will only have delta files, which leads to imbalanced persistence for storage as well as input/output operations per second, as data files are significantly larger than the delta files.</span></span>    
<span data-ttu-id="fba8c-140">若要在磁片磁碟機 X 和 Y 之間統一散發資料和差異檔案，請建立四個容器，而不是兩個，然後將前兩個容器對應到磁片磁碟機 X，再將接下來的兩個容器對應到 Y。</span><span class="sxs-lookup"><span data-stu-id="fba8c-140">To distribute data and delta files uniformly across drives X and Y, create four containers instead of two, and map the first two containers to drive X and the next two containers to drive Y.</span></span>  
<span data-ttu-id="fba8c-141">使用迴圈配置資源配置時，第一個資料和第一個差異檔案會分別從容器1和容器2進行配置，而這些檔案會對應到磁片磁碟機 X。</span><span class="sxs-lookup"><span data-stu-id="fba8c-141">With round-robin allocation, the first data and first delta file will be allocated from container-1 and container-2 respectively, which are mapped to drive X.</span></span>   
<span data-ttu-id="fba8c-142">同樣地，下一個資料檔案和差異檔案將會從對應至磁片磁碟機 Y 的容器3和第4個容器配置。這可讓您在兩個磁片磁碟機上一致地散佈資料和差異檔案。</span><span class="sxs-lookup"><span data-stu-id="fba8c-142">Similarly, the next data and delta file will be allocated from container-3 and container-4 which are mapped to drive Y. This allows distributing data and delta files across two drives uniformly.</span></span>  
 
  
## <a name="see-also"></a><span data-ttu-id="fba8c-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fba8c-143">See Also</span></span>  
<span data-ttu-id="fba8c-144">[建立及管理記憶體最佳化物件的儲存體](creating-and-managing-storage-for-memory-optimized-objects.md)   </span><span class="sxs-lookup"><span data-stu-id="fba8c-144">[Creating and Managing Storage for Memory-Optimized Objects](creating-and-managing-storage-for-memory-optimized-objects.md)   </span></span>  
[<span data-ttu-id="fba8c-145">資料庫檔案與檔案群組</span><span class="sxs-lookup"><span data-stu-id="fba8c-145">Database Files and Filegroups</span></span>](../../relational-databases/databases/database-files-and-filegroups.md)    
  
