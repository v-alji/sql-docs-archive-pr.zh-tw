---
title: 資料庫鏡像和資料庫快照集 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- database mirroring [SQL Server], interoperability
- snapshots [SQL Server database snapshots], database mirroring
- database snapshots [SQL Server], database mirroring
ms.assetid: 0bf1be90-7ce4-484c-aaa7-f8a782f57c5f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9df0b74270280bf2315c6a35a80d4b009b75a908
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593575"
---
# <a name="database-mirroring-and-database-snapshots-sql-server"></a><span data-ttu-id="ae6e5-102">資料庫鏡像和資料庫快照集 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="ae6e5-102">Database Mirroring and Database Snapshots (SQL Server)</span></span>
  <span data-ttu-id="ae6e5-103">您可以利用為了提供可用性而維護的鏡像資料庫卸載報表。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-103">You can take advantage of a mirror database that you are maintaining for availability purposes to offload reporting.</span></span> <span data-ttu-id="ae6e5-104">若要對報表使用鏡像資料庫，請在鏡像資料庫上建立資料庫快照集，然後將用戶端連接要求導向最近一次的快照集。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-104">To use a mirror database for reporting, you can create a database snapshot on the mirror database and direct client connection requests to the most recent snapshot.</span></span> <span data-ttu-id="ae6e5-105">資料庫快照集是其來源資料庫的一個靜態、唯讀、交易一致的快照集，存在於快照集建立時。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-105">A database snapshot is a static, read-only, transaction-consistent snapshot of its source database as it existed at the moment of the snapshot's creation.</span></span> <span data-ttu-id="ae6e5-106">若要在鏡像資料庫上建立資料庫快照集，資料庫必須處於同步處理的鏡像狀態。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-106">To create a database snapshot on a mirror database, the database must be in the synchronized mirroring state.</span></span>  
  
 <span data-ttu-id="ae6e5-107">不像鏡像資料庫，用戶端可以存取資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-107">Unlike the mirror database itself, a database snapshot is accessible to clients.</span></span> <span data-ttu-id="ae6e5-108">只要鏡像伺服器仍與主體伺服器進行通訊，就可以將報表用戶端導向連接到快照集。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-108">As long as the mirror server is communicating with the principal server, you can direct reporting clients to connect to a snapshot.</span></span> <span data-ttu-id="ae6e5-109">請注意，因為資料庫快照集是靜態的，所以不會有新的資料可用。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-109">Note that because a database snapshot is static, new data is not available.</span></span> <span data-ttu-id="ae6e5-110">若要使較新的資料可供使用者使用，您必須定期建立新的資料庫快照集，並使應用程式與最新快照集之間有直接傳入用戶端的連接。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-110">To make relatively recent data available to your users, you must create a new database snapshot periodically and have applications direct incoming client connections to the newest snapshot.</span></span>  
  
 <span data-ttu-id="ae6e5-111">新的資料庫快照集幾乎是空的，但它會隨著時間成長，因為有愈來愈多資料庫頁面都是第一次更新。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-111">A new database snapshot is almost empty, but it grows over time as more and more database pages are updated for the first time.</span></span> <span data-ttu-id="ae6e5-112">由於資料庫上的每個快照集都會以這種方式累加成長，所以每個資料庫快照集會與一般資料庫取用同等的資源。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-112">Because every snapshot on a database grows incrementally in this way, each database snapshot consumes as much resources as a normal database.</span></span> <span data-ttu-id="ae6e5-113">根據鏡像伺服器和主體伺服器的組態而定，如果鏡像資料庫上有太多資料庫快照集，可能就會降低主體資料庫的效能。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-113">Depending on the configurations of the mirror server and principal server, having an excessive number of database snapshots on a mirror database might decrease performance on the principal database.</span></span> <span data-ttu-id="ae6e5-114">因此，我們建議您僅在鏡像資料庫上保留一些較新的快照集。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-114">Therefore, we recommend that you keep only a few relatively recent snapshots on your mirror databases.</span></span> <span data-ttu-id="ae6e5-115">通常，在建立取代快照集之後，您應該將傳入的查詢重新導向至新的快照集，並在完成任何現行查詢之後卸除較早的快照集。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-115">Typically, after you create a replacement snapshot, you should redirect incoming queries to the new snapshot and drop the earlier snapshot after any current queries complete.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ae6e5-116">如需資料庫快照集的詳細資訊，請參閱 [資料庫快照集 &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-116">For more information about database snapshots, see [Database Snapshots &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md).</span></span>  
  
 <span data-ttu-id="ae6e5-117">如果發生角色切換，會重新啟動資料庫及其快照集，並暫時中斷使用者。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-117">If role switching occurs, the database and its snapshots are restarted, temporarily disconnecting users.</span></span> <span data-ttu-id="ae6e5-118">然後，資料庫快照集會留在當初建立它們的伺服器執行個體上，該執行個體已變成新的主體資料庫。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-118">Afterwards, the database snapshots remain on the server instance where they were created, which has become the new principal database.</span></span> <span data-ttu-id="ae6e5-119">使用者可在容錯移轉之後，繼續使用快照集。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-119">Users can continue to use the snapshots after the failover.</span></span> <span data-ttu-id="ae6e5-120">不過，這會為新的主體伺服器帶來額外負荷。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-120">However, this places an additional load on the new principal server.</span></span> <span data-ttu-id="ae6e5-121">如果效能是您環境中的一項考量，我們建議您在新的鏡像資料庫 (當它可用時) 建立快照集，再將用戶端重新導向至新的快照集，然後從先前的鏡像資料庫中卸除所有資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-121">If performance is a concern in your environment, we recommend that you create a snapshot on the new mirror database when it becomes available, redirect clients to the new snapshot, and drop all of the database snapshots from the former mirror database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ae6e5-122">如需能有效擴充的專用報表解決方案，請考慮複寫。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-122">For a dedicated reporting solution that scales out well, consider replication.</span></span> <span data-ttu-id="ae6e5-123">如需詳細資訊，請參閱 [SQL Server Replication](../install-windows/install-sql-server-replication.md)。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-123">For more information, see [SQL Server Replication](../install-windows/install-sql-server-replication.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae6e5-124">範例</span><span class="sxs-lookup"><span data-stu-id="ae6e5-124">Example</span></span>  
 <span data-ttu-id="ae6e5-125">此範例會在鏡像資料庫上建立快照集。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-125">This example creates snapshots on a mirrored database.</span></span>  
  
 <span data-ttu-id="ae6e5-126">假設資料庫鏡像工作階段的資料庫為 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-126">Assume that the database of a database mirroring session is [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span> <span data-ttu-id="ae6e5-127">此範例會在 `AdventureWorks` 資料庫的鏡像副本上建立三個資料庫快照集，該資料庫位於 `F` 磁碟機上。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-127">This example creates three database snapshots on the mirror copy of the `AdventureWorks` database, which resides on the `F` drive.</span></span> <span data-ttu-id="ae6e5-128">這些快照集名為 `AdventureWorks_0600`、 `AdventureWorks_1200`及 `AdventureWorks_1800` ，用以識別其大約的建立時間。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-128">The snapshots are named `AdventureWorks_0600`, `AdventureWorks_1200`, and `AdventureWorks_1800` to identify their approximate creation times.</span></span>  
  
1.  <span data-ttu-id="ae6e5-129">在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]的鏡像上建立第一個資料庫快照集。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-129">Create the first database snapshot on the mirror of [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span>  
  
    ```  
    CREATE DATABASE AdventureWorks_0600  
    ON (NAME = 'datafile', FILENAME = 'F:\AdventureWorks_0600.SNP')  
       AS SNAPSHOT OF AdventureWorks2012  
    ```  
  
2.  <span data-ttu-id="ae6e5-130">在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]的鏡像上建立第二個資料庫快照集：</span><span class="sxs-lookup"><span data-stu-id="ae6e5-130">Create the second database snapshot on the mirror of [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span> <span data-ttu-id="ae6e5-131">仍在使用 `AdventureWorks_0600` 的使用者可以繼續使用。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-131">Users who are still using `AdventureWorks_0600` can continue to use it.</span></span>  
  
    ```  
    CREATE DATABASE AdventureWorks_1200  
    ON (NAME = 'datafile', FILENAME = 'F:\AdventureWorks_1200.SNP')  
       AS SNAPSHOT OF AdventureWorks2012  
    ```  
  
     <span data-ttu-id="ae6e5-132">如此一來，可以利用程式將新用戶端連接導向最新的快照集。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-132">At this point, new client connections can be programmatically directed to the latest snapshot.</span></span>  
  
3.  <span data-ttu-id="ae6e5-133">在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]鏡像上建立第三個快照集。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-133">Create the third snapshot on the mirror [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)].</span></span> <span data-ttu-id="ae6e5-134">仍在使用 `AdventureWorks_0600` 或 `AdventureWorks_1200` 的使用者可以繼續使用。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-134">Users who are still using `AdventureWorks_0600` or `AdventureWorks_1200` can continue to use them.</span></span>  
  
    ```  
    CREATE DATABASE AdventureWorks_1800  
    ON (NAME = 'datafile', FILENAME = 'F:\AdventureWorks_1800.SNP')  
        AS SNAPSHOT OF AdventureWorks2012  
    ```  
  
     <span data-ttu-id="ae6e5-135">如此一來，可以利用程式將新用戶端連接導向最新的快照集。</span><span class="sxs-lookup"><span data-stu-id="ae6e5-135">At this point, new client connections can be programmatically directed to the latest snapshot.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="ae6e5-136">相關工作</span><span class="sxs-lookup"><span data-stu-id="ae6e5-136">Related Tasks</span></span>  
  
-   [<span data-ttu-id="ae6e5-137">建立資料庫快照集 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ae6e5-137">Create a Database Snapshot &#40;Transact-SQL&#41;</span></span>](../../relational-databases/databases/create-a-database-snapshot-transact-sql.md)  
  
-   [<span data-ttu-id="ae6e5-138">檢視資料庫快照集 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ae6e5-138">View a Database Snapshot &#40;SQL Server&#41;</span></span>](../../relational-databases/databases/view-a-database-snapshot-sql-server.md)  
  
-   [<span data-ttu-id="ae6e5-139">卸除資料庫快照集 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="ae6e5-139">Drop a Database Snapshot &#40;Transact-SQL&#41;</span></span>](../../relational-databases/databases/drop-a-database-snapshot-transact-sql.md)  

  
## <a name="see-also"></a><span data-ttu-id="ae6e5-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae6e5-140">See Also</span></span>  
 <span data-ttu-id="ae6e5-141">[資料庫快照集 &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="ae6e5-141">[Database Snapshots &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md) </span></span>  
 [<span data-ttu-id="ae6e5-142">將用戶端連接至資料庫鏡像工作階段 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="ae6e5-142">Connect Clients to a Database Mirroring Session &#40;SQL Server&#41;</span></span>](connect-clients-to-a-database-mirroring-session-sql-server.md)  
  
  
