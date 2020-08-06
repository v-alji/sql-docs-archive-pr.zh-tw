---
title: 可用性群組的管理 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], managing
ms.assetid: 0b7542fa-235e-413d-81bf-3eff9ee07480
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d2cac9a34fe71c11f71ec47bbb6d690199869fef
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592257"
---
# <a name="administration-of-an-availability-group-sql-server"></a><span data-ttu-id="fd51c-102">可用性群組的管理 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="fd51c-102">Administration of an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="fd51c-103">在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 中管理現有的 AlwaysOn 可用性群組包括下列一個或多個工作：</span><span class="sxs-lookup"><span data-stu-id="fd51c-103">Managing an existing AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] involves one or more of the following tasks:</span></span>  
  
-   <span data-ttu-id="fd51c-104">改變現有可用性副本的屬性 (例如，變更用戶端連接存取 (以設定可讀取的次要副本))；變更其容錯移轉模式、可用性模式或工作階段逾時設定。</span><span class="sxs-lookup"><span data-stu-id="fd51c-104">Altering the properties of an existing availability replica, for example to change client connection access (for configuring readable secondary replicas), changing its failover mode, availability mode, or session timeout setting.</span></span>  
  
-   <span data-ttu-id="fd51c-105">加入或移除次要副本。</span><span class="sxs-lookup"><span data-stu-id="fd51c-105">Adding or removing secondary replicas.</span></span>  
  
-   <span data-ttu-id="fd51c-106">加入或移除資料庫。</span><span class="sxs-lookup"><span data-stu-id="fd51c-106">Adding or removing a database.</span></span>  
  
-   <span data-ttu-id="fd51c-107">暫停或恢復資料庫。</span><span class="sxs-lookup"><span data-stu-id="fd51c-107">Suspending or resuming a database.</span></span>  
  
-   <span data-ttu-id="fd51c-108">執行已規劃的手動容錯移轉 ( *「手動容錯移轉」*(Manual Failover)) 或強制手動容錯移轉 ( *「強制容錯移轉」*(Forced Failover))。</span><span class="sxs-lookup"><span data-stu-id="fd51c-108">Performing a planned manual failover (a *manual failover*) or a forced manual failover (a *forced failover*).</span></span>  
  
-   <span data-ttu-id="fd51c-109">建立或設定可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="fd51c-109">Creating or configuring an availability group listener.</span></span>  
  
-   <span data-ttu-id="fd51c-110">管理給定可用性群組之 [可讀取的次要複本](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) 。</span><span class="sxs-lookup"><span data-stu-id="fd51c-110">Managing [readable secondary replicas](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) for a given availability group.</span></span> <span data-ttu-id="fd51c-111">這項作業包括以次要角色執行時，將一個或多個複本設定為唯讀存取，以及設定唯讀路由。</span><span class="sxs-lookup"><span data-stu-id="fd51c-111">This involves configuring one or more replicas to read-only access when running under the secondary role, and configuring read-only routing.</span></span>  
  
-   <span data-ttu-id="fd51c-112">管理給定可用性群組之 [次要複本上的備份](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) 。</span><span class="sxs-lookup"><span data-stu-id="fd51c-112">Managing [backups on secondary replicas](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) for a given availability group.</span></span> <span data-ttu-id="fd51c-113">這項作業包括設定您希望執行備份作業的位置，然後編寫備份作業的指令碼以實作您的備份喜好設定。</span><span class="sxs-lookup"><span data-stu-id="fd51c-113">This involves configuring where you prefer that backup jobs run and then scripting backup jobs to implement your backup preference.</span></span> <span data-ttu-id="fd51c-114">您必須為裝載可用性複本的每一個 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上之可用性群組中的每一個資料庫，編寫備份作業的指令碼。</span><span class="sxs-lookup"><span data-stu-id="fd51c-114">you need to script backup jobs for every database in the availability group on every instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts an availability replica.</span></span>  
  
-   <span data-ttu-id="fd51c-115">刪除可用性群組。</span><span class="sxs-lookup"><span data-stu-id="fd51c-115">Deleting an availability group.</span></span>  
  
-   <span data-ttu-id="fd51c-116">針對作業系統升級進行 AlwaysOn 可用性群組的跨叢集移轉</span><span class="sxs-lookup"><span data-stu-id="fd51c-116">Cross-cluster migration of AlwaysOn Availability Groups for OS upgrade</span></span>  
  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="fd51c-117">相關工作</span><span class="sxs-lookup"><span data-stu-id="fd51c-117">Related Tasks</span></span>  
 <span data-ttu-id="fd51c-118">**設定現有的可用性群組**</span><span class="sxs-lookup"><span data-stu-id="fd51c-118">**To configure an existing availability group**</span></span>  
  
-   [<span data-ttu-id="fd51c-119">將次要複本加入至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-119">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-120">將次要複本從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-120">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-121">將資料庫加入至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-121">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="fd51c-122">將次要資料庫從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-122">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-123">將主要資料庫從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-123">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-124">設定彈性容錯移轉原則，以控制自動容錯移轉 &#40;AlwaysOn 可用性群組的條件&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-124">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover &#40;AlwaysOn Availability Groups&#41;</span></span>](configure-flexible-automatic-failover-policy.md)  
  
 <span data-ttu-id="fd51c-125">**管理可用性群組**</span><span class="sxs-lookup"><span data-stu-id="fd51c-125">**To manage an availability group**</span></span>  
  
-   [<span data-ttu-id="fd51c-126">設定可用性複本的備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-126">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-127">執行可用性群組的已規劃手動容錯移轉 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-127">Perform a Planned Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-planned-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-128">執行可用性群組的強制手動容錯移轉 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-128">Perform a Forced Manual Failover of an Availability Group &#40;SQL Server&#41;</span></span>](perform-a-forced-manual-failover-of-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-129">移除可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-129">Remove an Availability Group &#40;SQL Server&#41;</span></span>](remove-an-availability-group-sql-server.md)  
  
 <span data-ttu-id="fd51c-130">**管理可用性複本**</span><span class="sxs-lookup"><span data-stu-id="fd51c-130">**To manage an availability replica**</span></span>  
  
-   [<span data-ttu-id="fd51c-131">將次要複本加入至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-131">Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](add-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-132">將次要複本聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-132">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-133">將次要複本從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-133">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-134">變更可用性複本的可用性模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-134">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-135">變更可用性複本的容錯移轉模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-135">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-136">設定可用性複本的備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-136">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-137">設定可用性複本的唯讀存取 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-137">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-138">設定可用性群組的唯讀路由 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-138">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-139">變更可用性複本的工作階段逾時期限 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-139">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="fd51c-140">**管理可用性資料庫**</span><span class="sxs-lookup"><span data-stu-id="fd51c-140">**To manage an availability database**</span></span>  
  
-   [<span data-ttu-id="fd51c-141">將資料庫加入至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-141">Add a Database to an Availability Group &#40;SQL Server&#41;</span></span>](availability-group-add-a-database.md)  
  
-   [<span data-ttu-id="fd51c-142">將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-142">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-143">將主要資料庫從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-143">Remove a Primary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-primary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-144">將次要資料庫從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-144">Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-145">暫止可用性資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-145">Suspend an Availability Database &#40;SQL Server&#41;</span></span>](suspend-an-availability-database-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-146">繼續可用性資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-146">Resume an Availability Database &#40;SQL Server&#41;</span></span>](resume-an-availability-database-sql-server.md)  
  
 <span data-ttu-id="fd51c-147">**監視可用性群組**</span><span class="sxs-lookup"><span data-stu-id="fd51c-147">**To monitor an availability group**</span></span>  
  
-   [<span data-ttu-id="fd51c-148">監視可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-148">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](monitoring-of-availability-groups-sql-server.md)  
  
 <span data-ttu-id="fd51c-149">**若要支援將可用性群組移轉至新的 WSFC 叢集 (跨叢集移轉)**</span><span class="sxs-lookup"><span data-stu-id="fd51c-149">**To support migrating availability groups to a new WSFC cluster (cross-cluster migration)**</span></span>  
  
-   [<span data-ttu-id="fd51c-150">變更伺服器執行個體的 HADR 叢集內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-150">Change the HADR Cluster Context of Server Instance &#40;SQL Server&#41;</span></span>](change-the-hadr-cluster-context-of-server-instance-sql-server.md)  
  
-   [<span data-ttu-id="fd51c-151">讓可用性群組離線 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-151">Take an Availability Group Offline &#40;SQL Server&#41;</span></span>](../../take-an-availability-group-offline-sql-server.md)  
  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="fd51c-152">相關內容</span><span class="sxs-lookup"><span data-stu-id="fd51c-152">Related Content</span></span>  
  
-   <span data-ttu-id="fd51c-153">**部落格：**</span><span class="sxs-lookup"><span data-stu-id="fd51c-153">**Blogs:**</span></span>  
  
     [<span data-ttu-id="fd51c-154">SQL Server AlwaysOn 團隊部落格：官方 SQL Server AlwaysOn 團隊部落格</span><span class="sxs-lookup"><span data-stu-id="fd51c-154">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="fd51c-155">CSS SQL Server 工程師部落格</span><span class="sxs-lookup"><span data-stu-id="fd51c-155">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="fd51c-156">**影片：**</span><span class="sxs-lookup"><span data-stu-id="fd51c-156">**Videos:**</span></span>  
  
     [<span data-ttu-id="fd51c-157">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第 1 部：新一代高可用性解決方案簡介</span><span class="sxs-lookup"><span data-stu-id="fd51c-157">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="fd51c-158">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第 2 部：使用 AlwaysOn 建立關鍵任務的高可用性方案</span><span class="sxs-lookup"><span data-stu-id="fd51c-158">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="fd51c-159">**白皮書：**</span><span class="sxs-lookup"><span data-stu-id="fd51c-159">**White papers:**</span></span>  
  
     [<span data-ttu-id="fd51c-160">Microsoft 的 SQL Server 2012 白皮書</span><span class="sxs-lookup"><span data-stu-id="fd51c-160">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="fd51c-161">SQL Server 客戶諮詢團隊白皮書</span><span class="sxs-lookup"><span data-stu-id="fd51c-161">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
  
## <a name="see-also"></a><span data-ttu-id="fd51c-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd51c-162">See Also</span></span>  
 <span data-ttu-id="fd51c-163">[AlwaysOn 可用性群組 &#40;SQL Server&#41;](always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fd51c-163">[AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="fd51c-164">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fd51c-164">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="fd51c-165">設定 AlwaysOn 可用性群組 &#40;SQL Server 的伺服器實例&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-165">Configuration of a Server Instance for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](configuration-of-a-server-instance-for-always-on-availability-groups-sql-server.md)  
 <span data-ttu-id="fd51c-166">[建立及設定可用性群組 &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fd51c-166">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="fd51c-167">[使用中次要：可讀取的次要複本 &#40;AlwaysOn 可用性群組&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="fd51c-167">[Active Secondaries: Readable Secondary Replicas &#40;AlwaysOn Availability Groups&#41;](active-secondaries-readable-secondary-replicas-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="fd51c-168">作用中次要資料庫：次要複本上的備份 &#40;AlwaysOn 可用性群組&#41;</span><span class="sxs-lookup"><span data-stu-id="fd51c-168">Active Secondaries: Backup on Secondary Replicas &#40;AlwaysOn Availability Groups&#41;</span></span>](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)  
 <span data-ttu-id="fd51c-169">[可用性群組接聽程式、用戶端連接性及應用程式容錯移轉 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="fd51c-169">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 <span data-ttu-id="fd51c-170">[AlwaysOn 可用性群組 &#40;SQL Server 的操作問題 AlwaysOn 原則&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="fd51c-170">[AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups &#40;SQL Server&#41;](always-on-policies-for-operational-issues-always-on-availability.md) </span></span>  
 <span data-ttu-id="fd51c-171">[監視可用性群組 &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fd51c-171">[Monitoring of Availability Groups &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="fd51c-172">[AlwaysOn 可用性群組：互通性 &#40;SQL Server&#41;](always-on-availability-groups-interoperability-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="fd51c-172">[AlwaysOn Availability Groups: Interoperability &#40;SQL Server&#41;](always-on-availability-groups-interoperability-sql-server.md) </span></span>  
 <span data-ttu-id="fd51c-173">[AlwaysOn 可用性群組 &#40;SQL Server&#41;的 Transact-sql 語句總覽](transact-sql-statements-for-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="fd51c-173">[Overview of Transact-SQL Statements for AlwaysOn Availability Groups &#40;SQL Server&#41;](transact-sql-statements-for-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="fd51c-174">AlwaysOn 可用性群組 &#40;SQL Server&#41;的 PowerShell Cmdlet 總覽</span><span class="sxs-lookup"><span data-stu-id="fd51c-174">Overview of PowerShell Cmdlets for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-powershell-cmdlets-for-always-on-availability-groups-sql-server.md)  
  
