---
title: 維護 AlwaysOn 發行集資料庫 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], interoperability
- replication [SQL Server], AlwaysOn Availability Groups
ms.assetid: 55b345fe-2eb9-4b04-a900-63d858eec360
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e8f36d29049140b6e5bbdfc1a4e716d41a766a06
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595266"
---
# <a name="maintaining-an-alwayson-publication-database-sql-server"></a><span data-ttu-id="435dc-102">維護 AlwaysOn 發行集資料庫 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="435dc-102">Maintaining an AlwaysOn Publication Database (SQL Server)</span></span>
  <span data-ttu-id="435dc-103">本主題將討論使用 AlwaysOn 可用性群組時維護發行集資料庫的特殊考量。</span><span class="sxs-lookup"><span data-stu-id="435dc-103">This topic discusses special considerations for maintaining a publication database when you use AlwaysOn availability groups.</span></span>  
  
 
  
##  <a name="maintaining-a-published-database-in-an-availability-group"></a><a name="MaintainPublDb"></a><span data-ttu-id="435dc-104">在可用性群組中維護已發行的資料庫</span><span class="sxs-lookup"><span data-stu-id="435dc-104">Maintaining a Published Database in an Availability Group</span></span>  
 <span data-ttu-id="435dc-105">維護 AlwaysOn 發行集資料庫基本上與維護標準發行集資料庫相同，但是具有下列考量事項：</span><span class="sxs-lookup"><span data-stu-id="435dc-105">Maintaining an AlwaysOn publication database is basically the same as maintaining a standard publication database, with the following considerations:</span></span>  
  
-   <span data-ttu-id="435dc-106">您必須在主要複本主機上進行管理。</span><span class="sxs-lookup"><span data-stu-id="435dc-106">Administration must occur at the primary replica host.</span></span> <span data-ttu-id="435dc-107">在 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中，主要複本主機以及可讀取次要複本的發行集會出現在 **[本機發行集]** 資料夾底下。</span><span class="sxs-lookup"><span data-stu-id="435dc-107">In [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], publications appear under the **Local Publications** folder for the primary replica host and also for readable secondary replicas.</span></span> <span data-ttu-id="435dc-108">容錯移轉之後，如果升級為主要複本的次要複本無法讀取，您可能必須手動重新整理 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] ，才能反映變更。</span><span class="sxs-lookup"><span data-stu-id="435dc-108">After failover, you might have to manually refresh [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] for the change to be reflected if the secondary that was promoted to primary was not readable.</span></span>  
  
-   <span data-ttu-id="435dc-109">複寫監視器永遠都會在原始發行者底下顯示發行集資訊。</span><span class="sxs-lookup"><span data-stu-id="435dc-109">Replication Monitor always displays publication information under the original publisher.</span></span> <span data-ttu-id="435dc-110">不過，只要加入原始發行者做為伺服器，您就可以在複寫監視器中檢視任何複本的這項資訊。</span><span class="sxs-lookup"><span data-stu-id="435dc-110">However, this information can be viewed in Replication Monitor from any replica by adding the original publisher as a server.</span></span>  
  
-   <span data-ttu-id="435dc-111">使用預存程序或 Replication Management Objects (RMO) 在目前主要複本上管理複寫時，如果您指定了發行者名稱，就必須指定在其上啟用資料庫以供複寫的執行個體名稱 (原始發行者)。</span><span class="sxs-lookup"><span data-stu-id="435dc-111">When using stored procedures or Replication Management Objects (RMO) to administer replication at the current primary, for cases in which you specify the Publisher name, you must specify the name of the instance on which the database was enabled for replication (the original publisher).</span></span> <span data-ttu-id="435dc-112">若要決定適當的名稱，請使用 `PUBLISHINGSERVERNAME` 函數。</span><span class="sxs-lookup"><span data-stu-id="435dc-112">To determine the appropriate name, use the `PUBLISHINGSERVERNAME` function.</span></span> <span data-ttu-id="435dc-113">當發行資料庫聯結了可用性群組時，儲存在次要資料庫複本中的複寫中繼資料會與主要複本上的中繼資料完全相同。</span><span class="sxs-lookup"><span data-stu-id="435dc-113">When a publishing database joins an availability group, the replication metadata stored in the secondary database replicas is identical to that at the primary.</span></span> <span data-ttu-id="435dc-114">因此，對於在主要複本上啟用以供複寫的發行集資料庫而言，儲存在次要複本之系統資料表中的發行者執行個體名稱是主要複本的名稱，而不是次要複本的名稱。</span><span class="sxs-lookup"><span data-stu-id="435dc-114">Consequently, for publication databases enabled for replication at the primary, the publisher instance name stored in system tables at the secondary is the name of the primary, not the secondary.</span></span> <span data-ttu-id="435dc-115">如果發行集資料庫容錯移轉至次要複本，這會影響複寫組態和維護。</span><span class="sxs-lookup"><span data-stu-id="435dc-115">This affects replication configuration and maintenance if the publication database fails over to a secondary.</span></span> <span data-ttu-id="435dc-116">例如，如果您要在容錯移轉後於次要資料庫上使用預存程式來設定複寫，而且您想要在不同複本上啟用的發行集資料庫的提取訂閱，則必須將原始發行者（而非目前發行者）的名稱指定為 *@publisher* 或的參數 `sp_addpullsubscription` `sp_addmergepulllsubscription` 。</span><span class="sxs-lookup"><span data-stu-id="435dc-116">For example, if you are configuring replication with stored procedures at a secondary after failover, and you want a pull subscription to a publication database that was enabled at a different replica, you must specify the name of the original publisher instead of the current publisher as the *@publisher* parameter of `sp_addpullsubscription` or `sp_addmergepulllsubscription`.</span></span> <span data-ttu-id="435dc-117">不過，如果您在容錯移轉後啟用發行集資料庫，則儲存在系統資料表中的發行者執行個體名稱就是目前主要主機的名稱。</span><span class="sxs-lookup"><span data-stu-id="435dc-117">However, if you enable a publication database after failover, the publisher instance name stored in the system tables is the name of the current primary host.</span></span> <span data-ttu-id="435dc-118">在此情況下，您會針對參數使用目前主要複本的主機名稱 *@publisher* 。</span><span class="sxs-lookup"><span data-stu-id="435dc-118">In this case, you would use the host name of the current primary replica for the *@publisher* parameter.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="435dc-119">對於某些程式（例如 `sp_addpublication` ）， *@publisher* 參數僅支援非實例的發行者 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ; 在這些情況下，它與 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn 無關。</span><span class="sxs-lookup"><span data-stu-id="435dc-119">For some procedures, such as `sp_addpublication`, the *@publisher* parameter is supported only for publishers that are not instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; in these cases, it is not relevant for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn.</span></span>  
  
-   <span data-ttu-id="435dc-120">若要在容錯移轉後同步處理 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] 中的訂閱，請從訂閱者同步處理提取訂閱，並從使用中發行者同步處理發送訂閱。</span><span class="sxs-lookup"><span data-stu-id="435dc-120">To synchronize a subscription in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)] after a failover, synchronize pull subscriptions from the subscriber and synchronize push subscriptions from the active publisher.</span></span>  
  
##  <a name="removing-a-published-database-from-an-availability-group"></a><a name="RemovePublDb"></a> <span data-ttu-id="435dc-121">從可用性群組中移除已發行的資料庫</span><span class="sxs-lookup"><span data-stu-id="435dc-121">Removing a Published Database from an Availability Group</span></span>  
 <span data-ttu-id="435dc-122">如果您已從可用性群組中移除已發行的資料庫，或者已卸除具有已發行成員資料庫的可用性群組，請考慮下列問題。</span><span class="sxs-lookup"><span data-stu-id="435dc-122">Consider the following issues if a published database is removed from an availability group, or if an availability group that has a published member database is dropped.</span></span>  
  
-   <span data-ttu-id="435dc-123">如果從可用性群組主要複本中移除位於原始發行者端的發行集資料庫，您就必須執行 `sp_redirect_publisher` 而不指定參數的值， *@redirected_publisher* 以便移除發行者/資料庫配對的重新導向。</span><span class="sxs-lookup"><span data-stu-id="435dc-123">If the publication database at the original publisher is removed from an availability group primary replica, you must run `sp_redirect_publisher` without specifying a value for the *@redirected_publisher* parameter in order to remove the redirection for the publisher/database pair.</span></span>  
  
    ```  
    EXEC sys.sp_redirect_publisher   
        @original_publisher = 'MyPublisher',  
        @published_database = 'MyPublishedDB';  
    ```  
  
     <span data-ttu-id="435dc-124">主要複本上的資料庫將保持復原狀態，而且必須進行還原。</span><span class="sxs-lookup"><span data-stu-id="435dc-124">The database will be left in the recovering state at the primary and must be restored.</span></span> <span data-ttu-id="435dc-125">一旦您這樣做之後，複寫應該會針對原始發行者維持相同的運作方式。</span><span class="sxs-lookup"><span data-stu-id="435dc-125">Once you do this, replication should work unchanged against the original Publisher.</span></span>  
  
-   <span data-ttu-id="435dc-126">如果發行集資料庫從原始發行者容錯移轉至複本，而且您已從可用性群組主要複本中移除該資料庫，請使用 `sp_redirect_publisher` 預存程序，將原始發行者明確重新導向至新的發行者。</span><span class="sxs-lookup"><span data-stu-id="435dc-126">If the publication database fails over from the original publisher to a replica and the database is removed from the availability group primary replica, use the stored procedure `sp_redirect_publisher` to explicitly redirect the original publisher to the new publisher.</span></span> <span data-ttu-id="435dc-127">資料庫將保持復原狀態，而且必須進行還原。</span><span class="sxs-lookup"><span data-stu-id="435dc-127">The database will be left in the recovering state and must be restored.</span></span> <span data-ttu-id="435dc-128">一旦您這樣做之後，複寫應該會繼續運作，如同它在可用性群組底下運作一樣。</span><span class="sxs-lookup"><span data-stu-id="435dc-128">Once you do this, replication should continue to work as it did under the availability group.</span></span>  
  
    ```  
    EXEC sys.sp_redirect_publisher   
        @original_publisher = 'MyPublisher',  
        @published_database = 'MyPublishedDB',  
        @redirected_publisher = 'MyNewPublisher';  
    ```  
  
     <span data-ttu-id="435dc-129">請勿從散發者中移除原始發行者的遠端伺服器，即使無法再存取伺服器也一樣。</span><span class="sxs-lookup"><span data-stu-id="435dc-129">Do not remove the remote server for the original publisher from the distributor, even if the server can no longer be accessed.</span></span> <span data-ttu-id="435dc-130">散發者需要原始發行者的伺服器中繼資料，才能滿足發行集中繼資料查詢。</span><span class="sxs-lookup"><span data-stu-id="435dc-130">The server metadata for the original publisher is needed at the distributor to satisfy publication metadata queries.</span></span>  
  
-   <span data-ttu-id="435dc-131">如果您已移除完整可用性群組，成員複寫資料庫的相關行為就會與從可用性群組中移除已發行資料庫時的行為相同。</span><span class="sxs-lookup"><span data-stu-id="435dc-131">If a complete availability group is removed, the behavior with regard to a member replicated database is the same as when a published database is removed from an availability group.</span></span> <span data-ttu-id="435dc-132">一旦您已經還原資料庫並且修改重新導向之後，就可以從最後一個主要複本恢復複寫。</span><span class="sxs-lookup"><span data-stu-id="435dc-132">Replication can be resumed from the last primary as soon as the database has been restored and the redirection has been modified.</span></span> <span data-ttu-id="435dc-133">如果資料庫是在其原始發行者端還原，您就應該移除重新導向。</span><span class="sxs-lookup"><span data-stu-id="435dc-133">If the database is restored at its original publisher, redirection should be removed.</span></span> <span data-ttu-id="435dc-134">如果資料庫是在不同的主機上還原，您就應該將重新導向明確導向至新主機。</span><span class="sxs-lookup"><span data-stu-id="435dc-134">If the database is restored at a different host, redirection should be explicitly directed to the new host.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="435dc-135">當您移除了具有已發行成員資料庫的可用性群組，或者從可用性群組中移除已發行的資料庫時，已發行資料庫的所有複本都將保持復原狀態。</span><span class="sxs-lookup"><span data-stu-id="435dc-135">When an availability group is removed that has published member databases, or a published database is removed from an availability group, all copies of the published databases will be left in the recovering state.</span></span> <span data-ttu-id="435dc-136">如果進行還原，每個複本都會顯示成已發行的資料庫。</span><span class="sxs-lookup"><span data-stu-id="435dc-136">If restored, each will appear as a published database.</span></span> <span data-ttu-id="435dc-137">您應該只保留一個具有發行集中繼資料的複本。</span><span class="sxs-lookup"><span data-stu-id="435dc-137">Only one copy should be retained with publication metadata.</span></span> <span data-ttu-id="435dc-138">若要針對已發行的資料庫複本停用複寫，請先從資料庫中移除所有訂閱和發行集。</span><span class="sxs-lookup"><span data-stu-id="435dc-138">To disable replication for a published database copy, first remove all subscriptions and publications from the database.</span></span>  
  
     <span data-ttu-id="435dc-139">執行 `sp_dropsubscription` 可移除發行集訂閱。</span><span class="sxs-lookup"><span data-stu-id="435dc-139">Run `sp_dropsubscription` to remove publication subscriptions.</span></span> <span data-ttu-id="435dc-140">請務必將參數設定 *@ignore_distributributor* 為1，以便在散發者端保留使用中發行資料庫的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="435dc-140">Make sure to set the parameter *@ignore_distributributor* to 1 to preserve the metadata for the active publishing database at the distributor.</span></span>  
  
    ```  
    USE MyDBName;  
    GO  
  
    EXEC sys.sp_dropsubscription   
        @subscriber = 'MySubscriber',  
        @publication = 'MyPublication',  
        @article = 'all',  
        @ignore_distributor = 1;  
    ```  
  
     <span data-ttu-id="435dc-141">執行 `sp_droppublication` 可移除所有發行集。</span><span class="sxs-lookup"><span data-stu-id="435dc-141">Run `sp_droppublication` to remove all publications.</span></span> <span data-ttu-id="435dc-142">同樣地，請將參數設定 *@ignore_distributor* 為1，以便在散發者端保留使用中發行資料庫的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="435dc-142">Again, set the parameter *@ignore_distributor* to 1 to preserve the metadata for the active publishing database at the distributor.</span></span>  
  
    ```  
    EXEC sys.sp_droppublication   
        @publication = 'MyPublication',  
        @ignore_distributor = 1;  
    ```  
  
     <span data-ttu-id="435dc-143">執行 `sp_replicationdboption` 可針對資料庫停用複寫。</span><span class="sxs-lookup"><span data-stu-id="435dc-143">Run `sp_replicationdboption` to disable replication for the database.</span></span>  
  
    ```  
    EXEC sys.sp_replicationdboption  
        @dbname = 'MyDBName',  
        @optname = 'publish',  
        @value = 'false';  
    ```  
  
     <span data-ttu-id="435dc-144">此時，您就可以保留或卸除已發行資料庫的複本。</span><span class="sxs-lookup"><span data-stu-id="435dc-144">At this point, the copy of the published database can be retained or dropped.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="435dc-145">相關工作</span><span class="sxs-lookup"><span data-stu-id="435dc-145">Related Tasks</span></span>  
  
-   [<span data-ttu-id="435dc-146">設定 AlwaysOn 可用性群組的複寫 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="435dc-146">Configure Replication for AlwaysOn Availability Groups (SQL Server)</span></span>](always-on-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="435dc-147">複寫、變更追蹤、變更資料捕獲，以及 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="435dc-147">Replication, Change Tracking, Change Data Capture, and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replicate-track-change-data-capture-always-on-availability.md)  
  
-   [<span data-ttu-id="435dc-148">複寫管理常見問題集</span><span class="sxs-lookup"><span data-stu-id="435dc-148">Replication Administration FAQ</span></span>](../../../relational-databases/replication/administration/frequently-asked-questions-for-replication-administrators.md)  
  
-   [<span data-ttu-id="435dc-149">複寫訂閱者及 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="435dc-149">Replication Subscribers and AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](replication-subscribers-and-always-on-availability-groups-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="435dc-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="435dc-150">See Also</span></span>  
 <span data-ttu-id="435dc-151">[AlwaysOn 可用性群組 &#40;SQL Server 的必要條件、限制和建議&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="435dc-151">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="435dc-152">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="435dc-152">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="435dc-153">[AlwaysOn 可用性群組：互通性 (SQL Server) ](always-on-availability-groups-interoperability-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="435dc-153">[AlwaysOn Availability Groups: Interoperability (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span></span>  
 [<span data-ttu-id="435dc-154">SQL Server 複寫</span><span class="sxs-lookup"><span data-stu-id="435dc-154">SQL Server Replication</span></span>](../../../relational-databases/replication/sql-server-replication.md)  
  
  
