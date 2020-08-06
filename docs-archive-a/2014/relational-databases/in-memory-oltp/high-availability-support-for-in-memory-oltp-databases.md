---
title: 記憶體內部 OLTP 資料庫的高可用性支援 | Microsoft Docs
ms.custom: ''
ms.date: 10/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 2113a916-3b1e-496c-8650-7f495e492510
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 092f2b8158bb35286a09103ea645b2aeb1374fc7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706502"
---
# <a name="high-availability-support-for-in-memory-oltp-databases"></a><span data-ttu-id="248fb-102">記憶體內部 OLTP 資料庫的高可用性支援</span><span class="sxs-lookup"><span data-stu-id="248fb-102">High Availability Support for In-Memory OLTP databases</span></span>
  <span data-ttu-id="248fb-103">不論包含或不含原生編譯的預存程序，包含記憶體最佳化資料表的資料庫完全支援 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="248fb-103">Databases containing memory-optimized tables, with or without native compiled stored procedures, are fully supported with AlwaysOn Availability Groups.</span></span>  <span data-ttu-id="248fb-104">設定中並沒有任何差異，但與不含的情況相比，包含原生編譯的預存程序還支援包含 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 物件的資料庫。</span><span class="sxs-lookup"><span data-stu-id="248fb-104">There is no difference in the configuration and support for databases which contain [!INCLUDE[hek_2](../../includes/hek-2-md.md)] objects as compared to those without,</span></span>  
  
## <a name="alwayson-availability-groups-and-in-memory-oltp-databases"></a><span data-ttu-id="248fb-105">AlwaysOn 可用性群組和記憶體內部 OLTP 資料庫</span><span class="sxs-lookup"><span data-stu-id="248fb-105">AlwaysOn Availability Groups and In-Memory OLTP Databases</span></span>  
 <span data-ttu-id="248fb-106">利用 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 元件設定資料庫提供了下列好處：</span><span class="sxs-lookup"><span data-stu-id="248fb-106">Configuring databases with [!INCLUDE[hek_2](../../includes/hek-2-md.md)] components provides the following:</span></span>  
  
-   <span data-ttu-id="248fb-107">**完全整合的體驗** </span><span class="sxs-lookup"><span data-stu-id="248fb-107">**A fully integrated experience** </span></span>  
    <span data-ttu-id="248fb-108">您可以使用同樣支援同步和非同步次要複本的相同精靈，設定包含記憶體最佳化資料表的資料庫。</span><span class="sxs-lookup"><span data-stu-id="248fb-108">You can configure your databases containing memory-optimized tables using the same wizard with the same level of support for both synchronous and asynchronous secondary replicas.</span></span> <span data-ttu-id="248fb-109">此外，還可以使用 SQL Server Management Studio 中熟悉的 AlwaysOn 儀表板提供健全狀況監視。</span><span class="sxs-lookup"><span data-stu-id="248fb-109">Additionally, health monitoring is provided using the familiar AlwaysOn dashboard in SQL Server Management Studio.</span></span>  
  
-   <span data-ttu-id="248fb-110">**可比較的容錯移轉時間** </span><span class="sxs-lookup"><span data-stu-id="248fb-110">**Comparable Failover time** </span></span>  
    <span data-ttu-id="248fb-111">次要複本可維護持久性記憶體最佳化資料表的記憶體內部狀態。</span><span class="sxs-lookup"><span data-stu-id="248fb-111">Secondary replicas maintain the in-memory state of the durable memory-optimized tables.</span></span> <span data-ttu-id="248fb-112">在自動或強制容錯移轉的情況下，由於不需要進行復原，容錯移轉至新主要複本的時間會相當於容錯移轉至磁碟基底資料表。</span><span class="sxs-lookup"><span data-stu-id="248fb-112">In the event of automatic or forced failover, the time to failover to the new primary is comparable to disk-bases tables as no recovery is needed.</span></span> <span data-ttu-id="248fb-113">這項設定支援建立為 SCHEMA_ONLY 的記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="248fb-113">Memory-optimized tables created as SCHEMA_ONLY are supported in this configuration.</span></span> <span data-ttu-id="248fb-114">不過，系統不會記錄這些資料表的變更，因此次要複本上的這些資料表中不會有資料。</span><span class="sxs-lookup"><span data-stu-id="248fb-114">However changes to these tables are not logged and therefore no data will exist in these tables on the secondary replica.</span></span>  
  
-   <span data-ttu-id="248fb-115">**可讀取次要** </span><span class="sxs-lookup"><span data-stu-id="248fb-115">**Readable Secondary** </span></span>  
    <span data-ttu-id="248fb-116">您可以存取與查詢次要複本上的記憶體最佳化資料表 (如果它已設定讀取權限)。</span><span class="sxs-lookup"><span data-stu-id="248fb-116">You can access and query memory-optimized tables on the secondary replica if it has been configured for read access.</span></span> <span data-ttu-id="248fb-117">如需詳細資訊，請參閱[使用中次要：可讀取的次要複本 (AlwaysOn 可用性群組)](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="248fb-117">For more information see [Active Secondaries: Readable Secondary Replicas (AlwaysOn Availability Groups)](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
## <a name="failover-clustering-instance-fci-and-in-memory-oltp-databases"></a><span data-ttu-id="248fb-118">容錯移轉叢集執行個體 (FCI) 和記憶體內部 OLTP 資料庫</span><span class="sxs-lookup"><span data-stu-id="248fb-118">Failover Clustering Instance (FCI) and In-Memory OLTP Databases</span></span>  
 <span data-ttu-id="248fb-119">若要達到共用儲存體設定的高可用性，您可以設定執行個體與一個或多個具有記憶體最佳化資料表之資料庫的容錯移轉叢集。</span><span class="sxs-lookup"><span data-stu-id="248fb-119">To achieve high-availability in a shared-storage configuration, you can setup failover clustering on instances with one or more database with memory-optimized tables.</span></span> <span data-ttu-id="248fb-120">在設定 FCI 的過程中，您必須考慮下列因素。</span><span class="sxs-lookup"><span data-stu-id="248fb-120">You need to consider the following factors as part of setting up an FCI.</span></span>  
  
-   <span data-ttu-id="248fb-121">**復原時間目標** </span><span class="sxs-lookup"><span data-stu-id="248fb-121">**Recovery Time Objective** </span></span>  
    <span data-ttu-id="248fb-122">由於記憶體最佳化的資料表必須先載入到記憶體才能使用資料庫，因此會有較高的容錯移轉時間。</span><span class="sxs-lookup"><span data-stu-id="248fb-122">Failover time will likely to be higher as the memory-optimized tables must be loaded into memory before the database is made available.</span></span>  
  
-   <span data-ttu-id="248fb-123">**SCHEMA_ONLY 資料表** </span><span class="sxs-lookup"><span data-stu-id="248fb-123">**SCHEMA_ONLY tables** </span></span>  
    <span data-ttu-id="248fb-124">請注意，在容錯移轉之後，SCHEMA_ONLY 資料表將會是空的，沒有任何資料列。</span><span class="sxs-lookup"><span data-stu-id="248fb-124">Be aware that SCHEMA_ONLY tables will be empty with no rows after the failover.</span></span> <span data-ttu-id="248fb-125">這是由應用程式進行設計與定義。</span><span class="sxs-lookup"><span data-stu-id="248fb-125">This is as designed and defined by the application.</span></span> <span data-ttu-id="248fb-126">這種行為與您重新啟動具有一或多個 SCHEMA_ONLY 資料表的 [!INCLUDE[hek_2](../../includes/hek-2-md.md)] 資料庫完全相同。</span><span class="sxs-lookup"><span data-stu-id="248fb-126">This is exactly the same behavior when you restart an [!INCLUDE[hek_2](../../includes/hek-2-md.md)] database with one or more SCHEMA_ONLY tables.</span></span>  
  
## <a name="support-for-transaction-replication-in-in-memory-oltp"></a><span data-ttu-id="248fb-127">支援記憶體內部 OLTP 的異動複寫</span><span class="sxs-lookup"><span data-stu-id="248fb-127">Support for transaction replication in In-Memory OLTP</span></span>  
 <span data-ttu-id="248fb-128">做為異動複寫訂閱者的資料表 (不包括點對點異動複寫) 可以設定為記憶體最佳化資料表。</span><span class="sxs-lookup"><span data-stu-id="248fb-128">Tables acting as transactional replication subscribers, excluding Peer-to-peer transactional replication, can be configured as memory-optimized tables.</span></span> <span data-ttu-id="248fb-129">其他複寫組態與記憶體最佳化資料表不相容。</span><span class="sxs-lookup"><span data-stu-id="248fb-129">Other replication configurations are not compatible with memory-optimized tables.</span></span>  <span data-ttu-id="248fb-130">如需詳細資訊，請參閱 [複寫至記憶體最佳化資料表訂閱者](../replication/replication-to-memory-optimized-table-subscribers.md)。</span><span class="sxs-lookup"><span data-stu-id="248fb-130">For more information see [Replication to Memory-Optimized Table Subscribers](../replication/replication-to-memory-optimized-table-subscribers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="248fb-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="248fb-131">See Also</span></span>  
 <span data-ttu-id="248fb-132">[AlwaysOn 可用性群組 (SQL Server) ](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="248fb-132">[AlwaysOn Availability Groups (SQL Server)](../../database-engine/availability-groups/windows/always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="248fb-133">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="248fb-133">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](../../database-engine/availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="248fb-134">[使用中次要：可讀取的次要複本 &#40;AlwaysOn 可用性群組&#41;](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="248fb-134">[Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;](../../database-engine/availability-groups/windows/active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="248fb-135">複寫至記憶體最佳化資料表訂閱者</span><span class="sxs-lookup"><span data-stu-id="248fb-135">Replication to Memory-Optimized Table Subscribers</span></span>](../replication/replication-to-memory-optimized-table-subscribers.md)  
  
  
