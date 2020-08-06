---
title: 設定 Always On 可用性群組的伺服器實例 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], server instance
- Availability Groups [SQL Server], about
ms.assetid: fad8db32-593e-49d5-989c-39eb8399c416
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3392e6189b687516e627d847acceedb165141117
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708674"
---
# <a name="configuration-of-a-server-instance-for-always-on-availability-groups-sql-server"></a><span data-ttu-id="e4d21-102">設定 AlwaysOn 可用性群組的伺服器執行個體 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e4d21-102">Configuration of a Server Instance for Always On Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="e4d21-103">本主題包含在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 中設定 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 執行個體以支援 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]之需求的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="e4d21-103">This topic contains information about the requirements for configuring an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] to support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e4d21-104">如需 Windows Server 容錯移轉叢集 (WSFC) 節點和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體之 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 必要條件與限制的基本資訊，請參閱 [AlwaysOn 可用性群組的必要條件、限制和建議 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="e4d21-104">For essential information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites and restrictions for Windows Server Failover Clustering (WSFC) nodes and for instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
 
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="e4d21-105">詞彙和定義</span><span class="sxs-lookup"><span data-stu-id="e4d21-105">Terms and Definitions</span></span>  
  
 <span data-ttu-id="e4d21-106">提供企業級資料庫鏡像替代方案的高可用性與災害復原解決方案。</span><span class="sxs-lookup"><span data-stu-id="e4d21-106">A high-availability and disaster-recovery solution that provides an enterprise-level replacement for database mirroring.</span></span> <span data-ttu-id="e4d21-107">*可用性群組*支援一組可一起容錯移轉之離散化使用者資料庫（稱為「*可用性資料庫*」（availability database））的容錯移轉環境。</span><span class="sxs-lookup"><span data-stu-id="e4d21-107">An *availability group* supports a failover environment for a discrete set of user databases, known as *availability databases*, that fail over together.</span></span>  
  
 <span data-ttu-id="e4d21-108">「可用性複本」</span><span class="sxs-lookup"><span data-stu-id="e4d21-108">availability replica</span></span>  
 <span data-ttu-id="e4d21-109">特定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體所裝載之可用性群組的具現化，其中維護屬於可用性群組之每個可用性資料庫的本機副本。</span><span class="sxs-lookup"><span data-stu-id="e4d21-109">An instantiation of an availability group that is hosted by a specific instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] and that maintains a local copy of each availability database that belongs to the availability group.</span></span> <span data-ttu-id="e4d21-110">有兩種類型的可用性複本存在：單一 *「主要複本」* (Primary Replica) 以及一到四個 *「次要複本」*(Secondary Replica)。</span><span class="sxs-lookup"><span data-stu-id="e4d21-110">Two types of availability replicas exist: a single *primary replica* and one to four *secondary replicas*.</span></span> <span data-ttu-id="e4d21-111">針對給定可用性群組裝載可用性複本的伺服器執行個體必須位於單一 Windows Server 容錯移轉叢集 (WSFC) 叢集的不同節點上。</span><span class="sxs-lookup"><span data-stu-id="e4d21-111">The server instances that host the availability replicas for a given availability group must reside on different nodes of a single Windows Server Failover Clustering (WSFC) cluster.</span></span>  
  
 [<span data-ttu-id="e4d21-112">資料庫鏡像端點</span><span class="sxs-lookup"><span data-stu-id="e4d21-112">database mirroring endpoint</span></span>](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)  
 <span data-ttu-id="e4d21-113">端點是 SQL Server 物件，可讓 SQL Server 在網路上進行通訊。</span><span class="sxs-lookup"><span data-stu-id="e4d21-113">An endpoint is a SQL Server object that enables SQL Server to communicate over the network.</span></span> <span data-ttu-id="e4d21-114">若要參與資料庫鏡像及/或 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ，伺服器執行個體需要特殊的專用端點。</span><span class="sxs-lookup"><span data-stu-id="e4d21-114">To participate in database mirroring and/or [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] a server instance requires a special, dedicated endpoint.</span></span> <span data-ttu-id="e4d21-115">伺服器執行個體上的所有鏡像和可用性群組連接都會使用相同的資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="e4d21-115">All mirroring and availability group connections on a server instance use the same database mirroring endpoint.</span></span> <span data-ttu-id="e4d21-116">這個端點是特殊目的之端點，專門用來接收其他伺服器執行個體的這些連接。</span><span class="sxs-lookup"><span data-stu-id="e4d21-116">This endpoint is a special-purpose endpoint used exclusively to receive these connections from other server instances.</span></span>  
  
##  <a name="to-configure-a-server-instance-to-support-alwayson-availability-groups"></a><a name="ConfigSI"></a><span data-ttu-id="e4d21-117">若要將伺服器實例設定為支援 AlwaysOn 可用性群組</span><span class="sxs-lookup"><span data-stu-id="e4d21-117">To Configure a Server Instance to Support AlwaysOn Availability Groups</span></span>  
 <span data-ttu-id="e4d21-118">若要支援 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]，伺服器執行個體必須位於裝載可用性群組之 WSFC 容錯移轉叢集中的節點、已啟用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] ，而且擁有資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="e4d21-118">To support [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)], a server instance must reside on a node in the WSFC failover cluster that hosts the availability group, be [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] enabled, and possess a database mirroring endpoint.</span></span>  
  
1.  <span data-ttu-id="e4d21-119">在要參與一個或多個可用性群組的每一個伺服器執行個體上啟用 AlwaysOn 可用性群組功能。</span><span class="sxs-lookup"><span data-stu-id="e4d21-119">Enable the AlwaysOn Availability Groups feature on every server instance that is to participate in one or more availability groups.</span></span> <span data-ttu-id="e4d21-120">給定伺服器執行個體只能裝載給定可用性群組的單一可用性複本。</span><span class="sxs-lookup"><span data-stu-id="e4d21-120">A given server instance can host only a single availability replica for a given availability group.</span></span>  
  
2.  <span data-ttu-id="e4d21-121">確定伺服器執行個體擁有資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="e4d21-121">Ensure that the server instance possesses a database mirroring endpoint.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e4d21-122">相關工作</span><span class="sxs-lookup"><span data-stu-id="e4d21-122">Related Tasks</span></span>  
 <span data-ttu-id="e4d21-123">**若要啟用 AlwaysOn 可用性群組**</span><span class="sxs-lookup"><span data-stu-id="e4d21-123">**To enable AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="e4d21-124">啟用和停用 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e4d21-124">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="e4d21-125">**若要判斷資料庫鏡像端點是否存在**</span><span class="sxs-lookup"><span data-stu-id="e4d21-125">**To determine whether a database mirroring endpoint exists**</span></span>  
  
-   [<span data-ttu-id="e4d21-126">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e4d21-126">sys.database_mirroring_endpoints &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-database-mirroring-endpoints-transact-sql)  
  
 <span data-ttu-id="e4d21-127">**若要建立資料庫鏡像端點**</span><span class="sxs-lookup"><span data-stu-id="e4d21-127">**To create a database mirroring endpoint**</span></span>  
  
-   [<span data-ttu-id="e4d21-128">建立 AlwaysOn 可用性群組 &#40;SQL Server PowerShell 的資料庫鏡像端點&#41;</span><span class="sxs-lookup"><span data-stu-id="e4d21-128">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="e4d21-129">建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e4d21-129">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="e4d21-130">允許資料庫鏡像端點使用輸出連線的憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e4d21-130">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="e4d21-131">相關內容</span><span class="sxs-lookup"><span data-stu-id="e4d21-131">Related Content</span></span>  
  
-   <span data-ttu-id="e4d21-132">**部落格：**</span><span class="sxs-lookup"><span data-stu-id="e4d21-132">**Blogs:**</span></span>  
  
     [<span data-ttu-id="e4d21-133">AlwaysON - HADRON 學習系列：具備 HADRON 功能之資料庫的工作者集區使用方式</span><span class="sxs-lookup"><span data-stu-id="e4d21-133">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="e4d21-134">SQL Server AlwaysOn 團隊部落格：官方 SQL Server AlwaysOn 團隊部落格</span><span class="sxs-lookup"><span data-stu-id="e4d21-134">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="e4d21-135">CSS SQL Server 工程師部落格</span><span class="sxs-lookup"><span data-stu-id="e4d21-135">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="e4d21-136">**影片：**</span><span class="sxs-lookup"><span data-stu-id="e4d21-136">**Videos:**</span></span>  
  
     [<span data-ttu-id="e4d21-137">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第 1 部：新一代高可用性解決方案簡介</span><span class="sxs-lookup"><span data-stu-id="e4d21-137">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="e4d21-138">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第 2 部：使用 AlwaysOn 建立關鍵任務的高可用性方案</span><span class="sxs-lookup"><span data-stu-id="e4d21-138">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="e4d21-139">**白皮書：**</span><span class="sxs-lookup"><span data-stu-id="e4d21-139">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="e4d21-140">Microsoft SQL Server AlwaysOn 高可用性和災害復原方案指南</span><span class="sxs-lookup"><span data-stu-id="e4d21-140">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="e4d21-141">Microsoft 的 SQL Server 2012 白皮書</span><span class="sxs-lookup"><span data-stu-id="e4d21-141">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="e4d21-142">SQL Server 客戶諮詢團隊白皮書</span><span class="sxs-lookup"><span data-stu-id="e4d21-142">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="e4d21-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4d21-143">See Also</span></span>  
 <span data-ttu-id="e4d21-144">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e4d21-144">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="e4d21-145">[AlwaysOn 可用性群組 &#40;SQL Server 的必要條件、限制和建議&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="e4d21-145">[Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) </span></span>  
 <span data-ttu-id="e4d21-146">[資料庫鏡像端點 &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e4d21-146">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="e4d21-147">[AlwaysOn 可用性群組：互通性 (SQL Server) ](always-on-availability-groups-interoperability-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e4d21-147">[AlwaysOn Availability Groups: Interoperability (SQL Server)](always-on-availability-groups-interoperability-sql-server.md) </span></span>  
 <span data-ttu-id="e4d21-148">[容錯移轉叢集和 AlwaysOn 可用性群組 &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e4d21-148">[Failover Clustering and AlwaysOn Availability Groups &#40;SQL Server&#41;](failover-clustering-and-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="e4d21-149">[SQL Server 的 Windows Server 容錯移轉叢集 &#40;WSFC&#41;](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e4d21-149">[Windows Server Failover Clustering &#40;WSFC&#41; with SQL Server](../../../sql-server/failover-clusters/windows/windows-server-failover-clustering-wsfc-with-sql-server.md) </span></span>  
 [<span data-ttu-id="e4d21-150">AlwaysOn 容錯移轉叢集實例</span><span class="sxs-lookup"><span data-stu-id="e4d21-150">AlwaysOn Failover Cluster Instances</span></span>](../../../sql-server/failover-clusters/windows/always-on-failover-cluster-instances-sql-server.md)  
  
