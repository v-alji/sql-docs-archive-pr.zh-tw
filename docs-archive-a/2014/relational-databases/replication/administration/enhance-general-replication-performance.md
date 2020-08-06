---
title: 增強一般複寫效能 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- publications [SQL Server replication], design and performance
- designing databases [SQL Server], replication performance
- Snapshot Agent, performance
- snapshots [SQL Server replication], performance considerations
- merge replication performance [SQL Server replication]
- snapshot replication [SQL Server], performance
- subscriptions [SQL Server replication], performance considerations
- agents [SQL Server replication], performance
- performance [SQL Server replication], general considerations
- transactional replication, performance
ms.assetid: 895b1ad7-ffb9-4a5c-bda6-e1dfbd56d9bf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0a85519a947e7d5d03f324b71984d2ffb40bcefe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709238"
---
# <a name="enhance-general-replication-performance"></a><span data-ttu-id="3ec6c-102">增強一般複寫效能</span><span class="sxs-lookup"><span data-stu-id="3ec6c-102">Enhance General Replication Performance</span></span>
  <span data-ttu-id="3ec6c-103">透過使用本主題中所述的指導方針，您可以提升應用程式及網路上所有複寫類型的一般效能：</span><span class="sxs-lookup"><span data-stu-id="3ec6c-103">You can enhance the general performance for all types of replication in your application and on your network by using the guidelines described in this topic.</span></span>  
  
## <a name="server-and-network"></a><span data-ttu-id="3ec6c-104">伺服器和網路</span><span class="sxs-lookup"><span data-stu-id="3ec6c-104">Server and Network</span></span>  
  
-   <span data-ttu-id="3ec6c-105">設定配置給 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 的最小和最大記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-105">Set the minimum and maximum amount of memory allocated to [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)].</span></span>  
  
     <span data-ttu-id="3ec6c-106">依預設， [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 將根據可用的系統資源，動態地變更其記憶體需求。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-106">By default, the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] changes its memory requirements dynamically based on available system resources.</span></span> <span data-ttu-id="3ec6c-107">若要避免複寫活動執行期間記憶體可用量過低，請使用 **min server memory** 選項設定最小可用的記憶體。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-107">To avoid low memory availability during replication activities, use the **min server memory** option to set the minimum available memory.</span></span> <span data-ttu-id="3ec6c-108">若要避免作業系統將記憶體分頁部署到光碟，亦可使用 **max server memory** 選項設定最大記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-108">To avoid having the operating system page to disc for memory, you can also set a maximum amount of memory with the **max server memory** option.</span></span> <span data-ttu-id="3ec6c-109">如需詳細資訊，請參閱[伺服器記憶體伺服器組態選項](../../../database-engine/configure-windows/server-memory-server-configuration-options.md)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-109">For more information, see [Server Memory Server Configuration Options](../../../database-engine/configure-windows/server-memory-server-configuration-options.md).</span></span>  
  
-   <span data-ttu-id="3ec6c-110">確保適當配置資料庫資料檔案和記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-110">Ensure proper allocation of database data files and log files.</span></span> <span data-ttu-id="3ec6c-111">針對複寫相關的所有資料庫交易記錄，使用個別的磁碟機。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-111">Use a separate disk drive for the transaction log for all databases involved in replication.</span></span>  
  
     <span data-ttu-id="3ec6c-112">若想縮短寫入交易的時間，請將記錄檔儲存到與儲存資料庫不同的磁碟機上。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-112">You can decrease the time it takes to write transactions by storing the log files on a disk drive different than the one used to store the database.</span></span> <span data-ttu-id="3ec6c-113">如果需要容錯功能，您可以使用磁碟陣列 (RAID)-1 來鏡射該磁碟。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-113">You can mirror that drive, using a Redundant Array of Inexpensive Disks (RAID)-1, if you require fault tolerance.</span></span> <span data-ttu-id="3ec6c-114">對其他資料庫檔案請使用 RAID 0 或 0+1 (視您對容錯的需求而定)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-114">Use RAID 0 or 0+1 (depending on your need for fault tolerance) for other database files.</span></span> <span data-ttu-id="3ec6c-115">不論是否正在使用複寫，這都是很好的習慣。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-115">This is a good practice regardless of whether or not replication is being used.</span></span>  
  
-   <span data-ttu-id="3ec6c-116">考慮為複寫用伺服器加入記憶體，特別是散發者。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-116">Consider adding memory to servers used in replication, particularly the Distributor.</span></span>  
  
-   <span data-ttu-id="3ec6c-117">使用多處理器電腦。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-117">Use multiprocessor computers.</span></span>  
  
     <span data-ttu-id="3ec6c-118">複寫代理程式可以利用伺服器上額外的處理器。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-118">Replication agents can take advantage of additional processors on the server.</span></span> <span data-ttu-id="3ec6c-119">如果您執行作業時 CPU 的使用量較高，則可考慮安裝一個更快的 CPU 或安裝多個 CPU。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-119">If you are running at high CPU usage, consider installing a faster CPU or multiple CPUs.</span></span>  
  
-   <span data-ttu-id="3ec6c-120">使用高速網路。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-120">Use a fast network.</span></span>  
  
     <span data-ttu-id="3ec6c-121">網路可能會成為顯著的效能瓶頸，特別是對於異動複寫而言。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-121">The network can be a significant performance bottleneck, particularly for transactional replication.</span></span> <span data-ttu-id="3ec6c-122">可藉由使用 100 Mbps 或更快的高速網路而大幅提高將變更傳播到「訂閱者」的速度。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-122">The propagation of changes to Subscribers can be significantly enhanced by using a fast network of 100 megabits per second (Mbps) or faster.</span></span> <span data-ttu-id="3ec6c-123">若網路太慢，請指定適當的網路設定與代理程式參數。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-123">If the network is slow, specify appropriate network settings and agent parameters.</span></span>  
  
## <a name="database-design"></a><span data-ttu-id="3ec6c-124">資料庫設計</span><span class="sxs-lookup"><span data-stu-id="3ec6c-124">Database Design</span></span>  
  
-   <span data-ttu-id="3ec6c-125">依照資料庫設計的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-125">Follow best practices for database design.</span></span>  
  
     <span data-ttu-id="3ec6c-126">一般，複寫資料庫與非複寫資料庫一樣享受效能最佳化帶來的助益。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-126">A replicated database generally benefits from the same performance optimizations as a non-replicated database.</span></span> <span data-ttu-id="3ec6c-127">但是，在「訂閱者」端應小心使用索引：「訂閱者」端的主索引鍵資料行應進行索引，但其他索引可能會影響插入、更新和刪除效能。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-127">However, indexes should be used with caution at the Subscriber: the primary key column at the Subscriber should be indexed, but additional indexes can affect insert, update, and delete performance.</span></span>  
  
-   <span data-ttu-id="3ec6c-128">考慮設定 READ_COMMITTED_SNAPSHOT 資料庫選項。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-128">Consider setting the READ_COMMITTED_SNAPSHOT database option.</span></span>  
  
     <span data-ttu-id="3ec6c-129">若要協助減少使用者活動與複寫代理程式活動之間的競爭，請為發行集和訂閱資料庫設定此選項：</span><span class="sxs-lookup"><span data-stu-id="3ec6c-129">To help reduce contention between user activity and replication agent activity, set this option for the publication and subscription databases:</span></span>  
  
    ```  
    ALTER DATABASE AdventureWorks  
    SET READ_COMMITTED_SNAPSHOT ON  
    ```  
  
     <span data-ttu-id="3ec6c-130">如需詳細資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-130">For more information, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
-   <span data-ttu-id="3ec6c-131">小心使用觸發程序的應用程式邏輯。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-131">Be cautious with application logic in triggers.</span></span>  
  
     <span data-ttu-id="3ec6c-132">在「訂閱者」端使用者自訂觸發程序中的商務邏輯可能會降低複寫變更到「訂閱者」的速度。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-132">Business logic in user-defined triggers at the Subscriber can slow down the replication of changes to the Subscriber:</span></span>  
  
    -   <span data-ttu-id="3ec6c-133">對於異動複寫而言，將這種邏輯包含於用來套用複寫命令的自訂預存程序中則更有效率。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-133">For transactional replication, it can be more efficient to include this logic in custom stored procedures used to apply the replicated commands.</span></span> <span data-ttu-id="3ec6c-134">如需詳細資訊，請參閱[指定交易式發行項變更的傳播方式](../transactional/transactional-articles-specify-how-changes-are-propagated.md)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-134">For more information, see [Specify How Changes Are Propagated for Transactional Articles](../transactional/transactional-articles-specify-how-changes-are-propagated.md).</span></span>  
  
    -   <span data-ttu-id="3ec6c-135">對於合併式複寫而言，使用商務邏輯處理常式可能更有效。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-135">For merge replication, it can be more efficient to use business logic handlers.</span></span> <span data-ttu-id="3ec6c-136">如需詳細資訊，請參閱[在合併同步處理期間執行商務邏輯](../merge/execute-business-logic-during-merge-synchronization.md)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-136">For more information, see [Execute Business Logic During Merge Synchronization](../merge/execute-business-logic-during-merge-synchronization.md).</span></span>  
  
     <span data-ttu-id="3ec6c-137">如果使用觸發程序來維護為合併式複寫發行之資料表中的參考完整性，請指定資料表的處理順序，以減少「合併代理程式」所需的重試次數。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-137">If you use triggers to maintain referential integrity in tables published for merge replication, specify the processing order of tables to reduce the number of retries required for the Merge Agent.</span></span> <span data-ttu-id="3ec6c-138">如需詳細資訊，請參閱[指定合併式複寫屬性](../publish/specify-merge-replication-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-138">For more information, see [Specify Merge Replication properties](../publish/specify-merge-replication-properties.md).</span></span>  
  
-   <span data-ttu-id="3ec6c-139">限制使用大型物件 (LOB) 資料類型。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-139">Limit the use of Large Object (LOB) data types.</span></span>  
  
     <span data-ttu-id="3ec6c-140">LOB 比其他資料行資料類型需要更多儲存空間和處理。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-140">LOBs require more storage space and processing than other column data types.</span></span> <span data-ttu-id="3ec6c-141">除非您的應用程式需要，否則不要在發行項中包含這些資料行。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-141">Do not include these columns in articles unless necessary for your application.</span></span> <span data-ttu-id="3ec6c-142">資料類型 `text`、`ntext` 和 `image` 已被取代。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-142">The data types `text`, `ntext`, and `image` are deprecated.</span></span> <span data-ttu-id="3ec6c-143">若您納入 LOB，建議您分別依序使用資料類型 `varchar(max)`、`nvarchar(max)`、`varbinary(max)`。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-143">If you do include LOBs, we recommend that you use the data types `varchar(max)`, `nvarchar(max)`, `varbinary(max)`, respectively.</span></span>  
  
     <span data-ttu-id="3ec6c-144">對於異動複寫，請考慮使用名為 **OLEDB 資料流的散發設定檔**的「散發代理程式」設定檔。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-144">For transactional replication, consider using the Distribution Agent profile called **Distribution Profile for OLEDB streaming**.</span></span> <span data-ttu-id="3ec6c-145">如需相關資訊，請參閱 [Replication Agent Profiles](../agents/replication-agent-profiles.md)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-145">For more information, see [Replication Agent Profiles](../agents/replication-agent-profiles.md).</span></span>  
  
## <a name="publication-design"></a><span data-ttu-id="3ec6c-146">發行集設計</span><span class="sxs-lookup"><span data-stu-id="3ec6c-146">Publication Design</span></span>  
  
-   <span data-ttu-id="3ec6c-147">只發行需要的資料。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-147">Publish only the data required.</span></span>  
  
     <span data-ttu-id="3ec6c-148">由於複寫的設定相當容易，因此容易發生發行超過實際需要的資料數量。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-148">Because replication is easy to set up, there is a tendency to publish more data than is actually required.</span></span> <span data-ttu-id="3ec6c-149">這樣會耗用散發資料庫與快照集內的額外資源，而且可能降低必要資料的處理能力。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-149">This can consume additional resources within the distribution databases and snapshot files, and can lower the throughput for required data.</span></span> <span data-ttu-id="3ec6c-150">請避免發行不必要的資料表，並降低更新發行的頻率。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-150">Avoid publishing unnecessary tables and consider updating publications less frequently.</span></span>  
  
-   <span data-ttu-id="3ec6c-151">透過發行集設計和發行集行為，將衝突最小化。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-151">Minimize conflicts through publication design and application behavior.</span></span>  
  
     <span data-ttu-id="3ec6c-152">下列複寫類型可讓資料在「訂閱者」端變更：合併式複寫、具有可更新訂閱的異動複寫以及點對點異動複寫。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-152">The following types of replication allow data to be changed at Subscribers: merge replication, transactional replication with updatable subscriptions, and peer-to-peer transactional replication.</span></span> <span data-ttu-id="3ec6c-153">如果給定資料列在同步處理之間的多個節點上有更新，則合併式複寫和具有可更新訂閱的異動複寫支援資料衝突。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-153">Merge replication and transactional replication with updatable subscriptions support data conflicts if a given row is updated at more than one node between synchronizations.</span></span> <span data-ttu-id="3ec6c-154">對點對複寫不支援資料衝突；必須對資料變更進行資料分割。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-154">Peer-to-peer replication does not support data conflicts; data changes must be partitioned.</span></span> <span data-ttu-id="3ec6c-155">無論使用何種複寫類型，都建議您盡可能分割變更，因為這樣會減少衝突偵測和解決方案所需的處理。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-155">Regardless of the type of replication used, we recommend that you partition changes whenever possible, because this reduces the processing required for conflict detection and resolution.</span></span>  
  
     <span data-ttu-id="3ec6c-156">變更可透過發行資料子集到每個「訂閱者」或透過使用可直接變更給定資料列到給定節點的應用程式來進行分割：</span><span class="sxs-lookup"><span data-stu-id="3ec6c-156">Changes can be partitioned by publishing subsets of data to each Subscriber or by having an application direct changes for a given row to a given node:</span></span>  
  
    -   <span data-ttu-id="3ec6c-157">合併式複寫支援使用具有單一發行集的參數化篩選來發行資料子集。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-157">Merge replication supports publishing subsets of data using parameterized filters with a single publication.</span></span> <span data-ttu-id="3ec6c-158">如需詳細資訊，請參閱＜ [參數化資料列篩選器](../merge/parameterized-filters-parameterized-row-filters.md)＞。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-158">For more information, see [Parameterized Row Filters](../merge/parameterized-filters-parameterized-row-filters.md).</span></span>  
  
    -   <span data-ttu-id="3ec6c-159">異動複寫支援使用具有多個發行集的靜態篩選來發行資料子集。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-159">Transactional replication supports publishing subsets of data using static filters with multiple publications.</span></span> <span data-ttu-id="3ec6c-160">如需詳細資訊，請參閱[篩選發行的資料](../publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-160">For more information, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
-   <span data-ttu-id="3ec6c-161">明智使用資料列篩選。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-161">Use row filters judiciously.</span></span>  
  
     <span data-ttu-id="3ec6c-162">如果交易式發行集包括一或多個使用資料列篩選的發行項，則「記錄讀取器代理程式」就必須在掃描交易記錄檔時，將篩選套用到受資料表更新影響的每個資料列。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-162">When a transactional publication includes one or more articles that use row filters, the Log Reader Agent must apply the filter to each row affected by an update to the table as it scans the transaction log.</span></span> <span data-ttu-id="3ec6c-163">「記錄讀取器代理程式」的輸送量因而受到影響。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-163">The throughput of the Log Reader Agent is therefore affected.</span></span>  
  
     <span data-ttu-id="3ec6c-164">同樣地，合併式複寫必須評估變更或刪除的資料列，以判斷哪些「訂閱者」應接收這些資料列。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-164">Similarly, merge replication must evaluate changed or deleted rows to determine which Subscribers should receive those rows.</span></span> <span data-ttu-id="3ec6c-165">當資料列篩選是用來減少「訂閱者」端所需的資料時，此處理就會更複雜而且可能比發行資料表的所有資料列更慢。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-165">When row filters are employed to reduce the data required at a Subscriber, this processing is more complex and can be slower than when you publish all rows in a table.</span></span> <span data-ttu-id="3ec6c-166">請仔細權衡降低每個「訂閱者」端儲存需求以及達到最大輸送量需求之間的優劣。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-166">Consider carefully the tradeoff between reduced storage requirements at each Subscriber and the need for achieving maximum throughput.</span></span> <span data-ttu-id="3ec6c-167">如需篩選的詳細資訊，請參閱[篩選發行的資料](../publish/filter-published-data.md)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-167">For more information on filtering, see [Filter Published Data](../publish/filter-published-data.md).</span></span>  
  
## <a name="subscription-considerations"></a><span data-ttu-id="3ec6c-168">訂閱考量因素</span><span class="sxs-lookup"><span data-stu-id="3ec6c-168">Subscription Considerations</span></span>  
  
-   <span data-ttu-id="3ec6c-169">有大量訂閱者時，使用提取訂閱。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-169">Use pull subscriptions when there are a large number of Subscribers.</span></span>  
  
     <span data-ttu-id="3ec6c-170">「散發代理程式」與「合併代理程式」在發送訂閱的「散發者」端和提取訂閱的「訂閱者」端執行。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-170">The Distribution Agent and Merge Agent run at the Distributor for push subscriptions, and at Subscribers for pull subscriptions.</span></span> <span data-ttu-id="3ec6c-171">使用提取訂閱可透過將代理程式處理從「散發者」移動到「訂閱者」來提升效能。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-171">Using pull subscriptions can improve performance by moving agent processing from the Distributor to Subscribers.</span></span> <span data-ttu-id="3ec6c-172">如需詳細資訊，請參閱[訂閱發行集](../subscribe-to-publications.md)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-172">For more information, see [Subscribe to Publications](../subscribe-to-publications.md).</span></span>  
  
-   <span data-ttu-id="3ec6c-173">若訂閱者嚴重落後，將考慮訂閱重新初始化。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-173">Consider reinitialization of the subscription if Subscribers are too far behind.</span></span>  
  
     <span data-ttu-id="3ec6c-174">當需要將大量的變更傳送到「訂閱者」時，請使用新的快照集來重新初始化訂閱，這可能比使用複寫來移動個別的變更還要快。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-174">When large amounts of changes need to be sent to Subscribers, reinitializing them with a new snapshot might be faster than using replication to move the individual changes.</span></span> <span data-ttu-id="3ec6c-175">如需詳細資訊，請參閱 [重新初始化訂閱](../reinitialize-subscriptions.md)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-175">For more information, see [Reinitialize Subscriptions](../reinitialize-subscriptions.md).</span></span>  
  
     <span data-ttu-id="3ec6c-176">對於異動複寫，「複寫監視器」在 **[未散發的命令]** 索引標籤上顯示以下資訊：在散發資料庫中尚未散發到「訂閱者」的交易數量；散發這些交易的估計時間。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-176">For transactional replication, Replication Monitor displays on the **Undistributed Commands** tab information about: the number of transactions in the distribution database that have not yet been distributed to a Subscriber; and the estimated time for distributing these transactions.</span></span> <span data-ttu-id="3ec6c-177">如需詳細資訊，請參閱[使用複寫監視器來檢視資訊及執行工作](../monitor/view-information-and-perform-tasks-replication-monitor.md)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-177">For more information, see [View Information and Perform Tasks using Replication Monitor](../monitor/view-information-and-perform-tasks-replication-monitor.md).</span></span>  
  
## <a name="snapshot-considerations"></a><span data-ttu-id="3ec6c-178">快照集考量</span><span class="sxs-lookup"><span data-stu-id="3ec6c-178">Snapshot Considerations</span></span>  
  
-   <span data-ttu-id="3ec6c-179">視需要且必須在離峰時間才執行快照集代理程式。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-179">Run the Snapshot Agent only when necessary and at off-peak times.</span></span>  
  
     <span data-ttu-id="3ec6c-180">「快照集代理程式」會將發行者已經發行的資料表資料大量複製到散發者快照集資料夾中的一個檔案。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-180">The Snapshot Agent bulk copies data from the published table on the Publisher to a file in the snapshot folder on the Distributor.</span></span> <span data-ttu-id="3ec6c-181">產生快照集可能是一項需要大量資源的處理，因此最好排程在離峰時間。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-181">Generating a snapshot can be a resource intensive process and is best scheduled during off-peak times.</span></span>  
  
-   <span data-ttu-id="3ec6c-182">除非需要字元模式快照集，否則請使用原生模式快照集。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-182">Use a native mode snapshot unless a character mode snapshot is required.</span></span>  
  
     <span data-ttu-id="3ec6c-183">除了非[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 訂閱者和執行 [!INCLUDE[ssEW](../../../includes/ssew-md.md)]的訂閱者 (這兩者需要字元模式快照集) 以外，對所有訂閱者使用預設的原生模式快照集。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-183">Use the default native mode snapshot for all Subscribers except non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Subscribers and Subscribers running [!INCLUDE[ssEW](../../../includes/ssew-md.md)], which require a character mode snapshot.</span></span>  
  
-   <span data-ttu-id="3ec6c-184">為發行集使用單一快照集資料夾。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-184">Use a single snapshot folder for a publication.</span></span>  
  
     <span data-ttu-id="3ec6c-185">指定與快照集位置有關的發行集屬性時，您可以選擇讓快照集檔案產生於預設的快照集資料夾、替代的快照集資料夾、或是兩者皆採用。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-185">When specifying the publication properties related to snapshot location, you can choose to generate snapshot files to the default snapshot folder, to an alternate snapshot folder, or to both.</span></span> <span data-ttu-id="3ec6c-186">同時在兩個位置上產生快照集檔案，則執行「快照集代理程式」時需要額外的磁碟空間和更多的處理。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-186">Generating snapshot files in both locations requires additional disk space and more processing when the Snapshot Agent runs.</span></span>  
  
-   <span data-ttu-id="3ec6c-187">將快照集資料夾置於散發者本機磁碟機，且該散發者並非用來儲存資料庫或記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-187">Place the snapshot folder on a drive local to the Distributor that is not used to store database or log files.</span></span>  
  
     <span data-ttu-id="3ec6c-188">「快照集代理程式」將資料循序寫入快照集資料夾。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-188">The Snapshot Agent performs a sequential write of data to the snapshot folder.</span></span> <span data-ttu-id="3ec6c-189">將快照集資料夾放置在與任何資料庫或記錄檔不同的磁碟機上，會減少磁碟之間的競爭，有助於更快地完成快照集處理。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-189">Placing the snapshot folder on a separate drive from any database or log files reduces contention among the disks and helps the snapshot process complete faster.</span></span>  
  
-   <span data-ttu-id="3ec6c-190">在訂閱者端建立訂閱資料庫時，考慮指定簡單或大量記錄復原模式。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-190">When you create the subscription database at the Subscriber, consider specifying a recovery model of simple or bulk-logged.</span></span> <span data-ttu-id="3ec6c-191">這樣可讓在「訂閱者」端執行快照集應用程式時，對執行大量插入工作的記錄最小。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-191">This allows minimal logging of the bulk inserts performed during the application of the snapshot at the Subscriber.</span></span> <span data-ttu-id="3ec6c-192">在將快照集套用到訂閱資料庫之後，如有必要，可變更為另一個復原模式 (複寫的資料庫可使用任何復原模式)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-192">After the snapshot has been applied to the subscription database, you can change to a different recovery model if necessary (replicated databases can use any of the recovery models).</span></span> <span data-ttu-id="3ec6c-193">如需選取復原模式的詳細資訊，請參閱[還原和復原概觀 &#40;SQL Server&#41;](../../backup-restore/restore-and-recovery-overview-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-193">For more information about selecting a recovery model, see [Restore and Recovery Overview &#40;SQL Server&#41;](../../backup-restore/restore-and-recovery-overview-sql-server.md).</span></span>  
  
-   <span data-ttu-id="3ec6c-194">對於低頻寬網路，請考慮在抽取式媒體上使用替代快照集資料夾和壓縮快照集。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-194">Consider using the alternate snapshot folder and compressed snapshots on removable media for low-bandwidth networks.</span></span>  
  
     <span data-ttu-id="3ec6c-195">壓縮替代快照集資料夾中的快照集檔案，可減少磁碟儲存需求，使在抽取式媒體上傳送快照集檔案更容易。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-195">Compressing snapshot files in the alternate snapshot folder can reduce snapshot disk storage requirements and make it easier to transfer snapshot files on removable media.</span></span>  
  
     <span data-ttu-id="3ec6c-196">在某些情況下，壓縮的快照集可以改善網路之間傳送快照集檔案的效能。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-196">Compressed snapshots can, in some cases, improve the performance of transferring snapshot files across the network.</span></span> <span data-ttu-id="3ec6c-197">不過，壓縮快照集需要由快照集代理程式在產生快照集檔案時，進行其他處理動作；並於套用快照集檔案時，進行散發代理程式或合併代理程式。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-197">However, compressing the snapshot requires additional processing by the Snapshot Agent when generating the snapshot files, and by the Distribution Agent or Merge Agent when applying the snapshot files.</span></span> <span data-ttu-id="3ec6c-198">如此可能會減緩快照集的產生且在某些情況下會增加套用快照集的時間。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-198">This may slow down snapshot generation and increase the time it takes to apply a snapshot in some cases.</span></span> <span data-ttu-id="3ec6c-199">此外，若發生網路失敗，則無法繼續壓縮快照集；因此並不適合不穩定的網路。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-199">Additionally, compressed snapshots cannot be resumed if a network failure occurs; therefore they are not suitable for unreliable networks.</span></span> <span data-ttu-id="3ec6c-200">透過網路使用壓縮快照集時，仔細考量這些權衡問題。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-200">Consider these tradeoffs carefully when using compressed snapshots across a network.</span></span> <span data-ttu-id="3ec6c-201">如需相關資訊，請參閱 [Alternate Snapshot Folder Locations](../alternate-snapshot-folder-locations.md) 及 [Compressed Snapshots](../compressed-snapshots.md)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-201">For more information, see [Alternate Snapshot Folder Locations](../alternate-snapshot-folder-locations.md) and [Compressed Snapshots](../compressed-snapshots.md).</span></span>  
  
-   <span data-ttu-id="3ec6c-202">考慮手動初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-202">Consider initializing a subscription manually.</span></span>  
  
     <span data-ttu-id="3ec6c-203">在某些情況下，例如涉及大型初始資料集，最好是使用快照集之外的方法初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-203">In some scenarios, such as those involving large initial datasets, it is preferable to initialize a subscription using a method other than a snapshot.</span></span> <span data-ttu-id="3ec6c-204">如需詳細資訊，請參閱 [不使用快照集初始化交易式訂閱](../initialize-a-transactional-subscription-without-a-snapshot.md)中手動初始化訂閱。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-204">For more information, see [Initialize a Transactional Subscription Without a Snapshot](../initialize-a-transactional-subscription-without-a-snapshot.md).</span></span>  
  
## <a name="agent-parameters"></a><span data-ttu-id="3ec6c-205">代理程式參數</span><span class="sxs-lookup"><span data-stu-id="3ec6c-205">Agent Parameters</span></span>  
  
-   <span data-ttu-id="3ec6c-206">減少複寫代理程式的詳細資訊層級，僅初始化測試、監視或偵錯時除外。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-206">Reduce the verbose levels of replication agents except during initial testing, monitoring, or debugging.</span></span>  
  
     <span data-ttu-id="3ec6c-207">減少散發代理程式或合併代理程式的 **-HistoryVerboseLevel** 參數和 **-OutputVerboseLevel** 參數。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-207">Reduce the **-HistoryVerboseLevel** parameter and the **-OutputVerboseLevel** parameter of the Distribution Agents or Merge Agents.</span></span> <span data-ttu-id="3ec6c-208">如此可減少插入追蹤代理程式記錄和輸出中的新資料列數目。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-208">This reduces the number of new rows inserted to track agent history and output.</span></span> <span data-ttu-id="3ec6c-209">反之，具有相同狀態的先前記錄訊息會更新為新的記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-209">Instead, previous history messages with the same status are updated to the new history information.</span></span> <span data-ttu-id="3ec6c-210">提高測試、監視及偵錯的詳細資訊層級，以便您能盡可能多地獲得代理程式活動的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-210">Increase the verbose levels for testing, monitoring, and debugging so that you have as much information about agent activity as possible.</span></span>  
  
-   <span data-ttu-id="3ec6c-211">使用快照集代理程式、合併代理程式以及散發代理程式的 **-MaxBCPThreads** 參數 (指定的執行緒數目不應超過電腦上的處理器數目)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-211">Use the **-MaxBCPThreads** parameter of the Snapshot Agent, Merge Agent, and Distribution Agent (the number of threads specified should not exceed the number of processors on the computer).</span></span> <span data-ttu-id="3ec6c-212">此參數指定在建立和套用快照集時可平行執行的大量複製作業數目。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-212">This parameter specifies the number of bulk copy operations that can be performed in parallel when the snapshot is created and applied.</span></span>  
  
-   <span data-ttu-id="3ec6c-213">使用散發代理程式和合併代理程式的 **-UseInprocLoader** 參數 (如果發行的資料表包括 XML 資料行，則不可使用此參數)。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-213">Use the **-UseInprocLoader** parameter of the Distribution Agent and the Merge Agent (this parameter cannot be used if published tables include XML columns).</span></span> <span data-ttu-id="3ec6c-214">此參數會使代理程式在套用快照集時使用 BULK INSERT 命令。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-214">This parameter causes the agent to use the BULK INSERT command when the snapshot is applied.</span></span>  
  
 <span data-ttu-id="3ec6c-215">可於代理程式設定檔和命令列中指定代理程式參數。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-215">Agent parameters can be specified in agent profiles and on the command line.</span></span> <span data-ttu-id="3ec6c-216">如需詳細資訊，請參閱</span><span class="sxs-lookup"><span data-stu-id="3ec6c-216">For more information, see:</span></span>  
  
-   [<span data-ttu-id="3ec6c-217">處理複寫代理程式設定檔</span><span class="sxs-lookup"><span data-stu-id="3ec6c-217">Work with Replication Agent Profiles</span></span>](../agents/work-with-replication-agent-profiles.md)  
  
-   [<span data-ttu-id="3ec6c-218">檢視並修改複寫代理程式命令提示字元參數 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="3ec6c-218">View and Modify Replication Agent Command Prompt Parameters &#40;SQL Server Management Studio&#41;</span></span>](../agents/view-and-modify-replication-agent-command-prompt-parameters.md)  
  
-   <span data-ttu-id="3ec6c-219">[Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md)的最小和最大記憶體數量。</span><span class="sxs-lookup"><span data-stu-id="3ec6c-219">[Replication Agent Executables Concepts](../concepts/replication-agent-executables-concepts.md).</span></span>  
  
  
