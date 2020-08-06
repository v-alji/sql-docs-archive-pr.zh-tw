---
title: 建立及設定可用性群組 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], creating
ms.assetid: 7f89fab8-6ee2-4273-9de0-e594bfb9407f
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bc33da393527c19985f5e7b214ba4bc02dc2f3af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710805"
---
# <a name="creation-and-configuration-of-availability-groups-sql-server"></a><span data-ttu-id="5af0f-102">建立及設定可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5af0f-102">Creation and Configuration of Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="5af0f-103">本章節的主題將說明如何在位於單一 WSFC 容錯移轉叢集內不同 Windows Server 容錯移轉叢集 (WSFC) 節點上的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 執行個體上部署 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 實作。</span><span class="sxs-lookup"><span data-stu-id="5af0f-103">The topics in this section explain how to deploy a [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] implementation on instances of [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] that reside on different Windows Server Failover Clustering (WSFC) nodes within a single WSFC failover cluster.</span></span>  
  
 <span data-ttu-id="5af0f-104">建立第一個可用性群組之前，我們建議您先熟悉下列主題中的資訊：</span><span class="sxs-lookup"><span data-stu-id="5af0f-104">Before you create your first availability group, we strongly recommend that you familiarize yourself with the information in the following topics:</span></span>  
  
 [<span data-ttu-id="5af0f-105">AlwaysOn 可用性群組 &#40;SQL Server 的必要條件、限制和建議&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-105">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
 <span data-ttu-id="5af0f-106">此主題描述電腦、WSFC 節點、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]執行個體、可用性群組、複本和資料庫的必要條件、限制和建議。</span><span class="sxs-lookup"><span data-stu-id="5af0f-106">This topic describes the prerequisites, restrictions, and recommendations for computers; WSFC nodes; instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]; availability groups, replicas, and databases.</span></span> <span data-ttu-id="5af0f-107">此主題也包含安全性考量的資訊。</span><span class="sxs-lookup"><span data-stu-id="5af0f-107">This topic also contains information about security considerations.</span></span>  
  
 [<span data-ttu-id="5af0f-108">具有 AlwaysOn 可用性群組 &#40;SQL Server 的消費者入門&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-108">Getting Started with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](getting-started-with-always-on-availability-groups-sql-server.md)  
 <span data-ttu-id="5af0f-109">包含下列作業的步驟資訊：設定伺服器執行個體、建立可用性群組、設定用戶端連接的可用性群組、管理可用性群組，以及監視可用性群組。</span><span class="sxs-lookup"><span data-stu-id="5af0f-109">Contains information about the steps for configuring a server instance, creating an availability group, configuring the availability group for client connections, managing availability groups, and monitoring availability groups.</span></span>  
  
 
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="5af0f-110">相關工作</span><span class="sxs-lookup"><span data-stu-id="5af0f-110">Related Tasks</span></span>  
 <span data-ttu-id="5af0f-111">**為 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]**</span><span class="sxs-lookup"><span data-stu-id="5af0f-111">**To configure a server instance for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]**</span></span>  
  
-   [<span data-ttu-id="5af0f-112">啟用和停用 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-112">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
-   [<span data-ttu-id="5af0f-113">建立 AlwaysOn 可用性群組 &#40;SQL Server PowerShell 的資料庫鏡像端點&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-113">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="5af0f-114">建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-114">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="5af0f-115">允許資料庫鏡像端點使用輸出連線的憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-115">Allow a Database Mirroring Endpoint to Use Certificates for Outbound Connections &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/database-mirroring-use-certificates-for-outbound-connections.md)  
  
 <span data-ttu-id="5af0f-116">**開始使用設定 AlwaysOn 可用性群組**</span><span class="sxs-lookup"><span data-stu-id="5af0f-116">**To get started with configuring AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="5af0f-117">具有 AlwaysOn 可用性群組 &#40;SQL Server 的消費者入門&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-117">Getting Started with AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](getting-started-with-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="5af0f-118">**建立並設定新的可用性群組**</span><span class="sxs-lookup"><span data-stu-id="5af0f-118">**To create and configure a new availability group**</span></span>  
  
-   [<span data-ttu-id="5af0f-119">使用可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-119">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="5af0f-120">建立可用性群組 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-120">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="5af0f-121">建立可用性群組 &#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-121">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
-   [<span data-ttu-id="5af0f-122">使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-122">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="5af0f-123">在新增或修改可用性複本時指定端點 URL &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-123">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="5af0f-124">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-124">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="5af0f-125">設定彈性容錯移轉原則以控制自動容錯移轉的條件 (AlwaysOn 可用性群組)</span><span class="sxs-lookup"><span data-stu-id="5af0f-125">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (AlwaysOn Availability Groups)</span></span>](configure-flexible-automatic-failover-policy.md)  
  
-   [<span data-ttu-id="5af0f-126">設定可用性複本的備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-126">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="5af0f-127">設定可用性複本的唯讀存取 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-127">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="5af0f-128">設定可用性群組的唯讀路由 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-128">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="5af0f-129">將次要複本聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-129">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="5af0f-130">在 AlwaysOn 次要資料庫上啟動資料移動 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-130">Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;</span></span>](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [<span data-ttu-id="5af0f-131">針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-131">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="5af0f-132">將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-132">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="5af0f-133">管理可用性群組之資料庫的登入及工作 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-133">Management of Logins and Jobs for the Databases of an Availability Group &#40;SQL Server&#41;</span></span>](../../logins-and-jobs-for-availability-group-databases.md)  
  
 <span data-ttu-id="5af0f-134">**疑難排解**</span><span class="sxs-lookup"><span data-stu-id="5af0f-134">**To troubleshoot**</span></span>  
  
-   [<span data-ttu-id="5af0f-135">針對 AlwaysOn 可用性群組 Configuration (SQL Server) 已刪除進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="5af0f-135">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="5af0f-136">針對失敗的新增檔案作業進行疑難排解 &#40;AlwaysOn 可用性群組&#41;</span><span class="sxs-lookup"><span data-stu-id="5af0f-136">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="5af0f-137">相關內容</span><span class="sxs-lookup"><span data-stu-id="5af0f-137">Related Content</span></span>  
  
-   <span data-ttu-id="5af0f-138">**部落格：**</span><span class="sxs-lookup"><span data-stu-id="5af0f-138">**Blogs:**</span></span>  
  
     [<span data-ttu-id="5af0f-139">AlwaysON - HADRON 學習系列：具備 HADRON 功能之資料庫的工作者集區使用方式</span><span class="sxs-lookup"><span data-stu-id="5af0f-139">AlwaysON - HADRON Learning Series: Worker Pool Usage for HADRON Enabled Databases</span></span>](https://blogs.msdn.com/b/psssql/archive/2012/05/17/alwayson-hadron-learning-series-worker-pool-usage-for-hadron-enabled-databases.aspx)  
  
     [<span data-ttu-id="5af0f-140">SQL Server AlwaysOn 團隊部落格：官方 SQL Server AlwaysOn 團隊部落格</span><span class="sxs-lookup"><span data-stu-id="5af0f-140">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
     [<span data-ttu-id="5af0f-141">CSS SQL Server 工程師部落格</span><span class="sxs-lookup"><span data-stu-id="5af0f-141">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="5af0f-142">**影片：**</span><span class="sxs-lookup"><span data-stu-id="5af0f-142">**Videos:**</span></span>  
  
     [<span data-ttu-id="5af0f-143">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第 1 部：新一代高可用性解決方案簡介</span><span class="sxs-lookup"><span data-stu-id="5af0f-143">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 1: Introducing the Next Generation High Availability Solution</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI302)  
  
     [<span data-ttu-id="5af0f-144">Microsoft SQL Server Code-Named "Denali" AlwaysOn 系列，第 2 部：使用 AlwaysOn 建立關鍵任務的高可用性方案</span><span class="sxs-lookup"><span data-stu-id="5af0f-144">Microsoft SQL Server Code-Named "Denali" AlwaysOn Series,Part 2: Building a Mission-Critical High Availability Solution Using AlwaysOn</span></span>](https://channel9.msdn.com/Events/TechEd/NorthAmerica/2011/DBI404)  
  
-   <span data-ttu-id="5af0f-145">**白皮書：**</span><span class="sxs-lookup"><span data-stu-id="5af0f-145">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="5af0f-146">Microsoft SQL Server AlwaysOn 高可用性和災害復原方案指南</span><span class="sxs-lookup"><span data-stu-id="5af0f-146">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
     [<span data-ttu-id="5af0f-147">Microsoft 的 SQL Server 2012 白皮書</span><span class="sxs-lookup"><span data-stu-id="5af0f-147">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="5af0f-148">SQL Server 客戶諮詢團隊白皮書</span><span class="sxs-lookup"><span data-stu-id="5af0f-148">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="5af0f-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5af0f-149">See Also</span></span>  
 <span data-ttu-id="5af0f-150">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5af0f-150">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="5af0f-151">[管理可用性群組 &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5af0f-151">[Administration of an Availability Group &#40;SQL Server&#41;](administration-of-an-availability-group-sql-server.md) </span></span>  
 <span data-ttu-id="5af0f-152">[AlwaysOn 可用性群組 (SQL Server 的操作問題 AlwaysOn 原則) ](always-on-policies-for-operational-issues-always-on-availability.md) </span><span class="sxs-lookup"><span data-stu-id="5af0f-152">[AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md) </span></span>  
 <span data-ttu-id="5af0f-153">[監視可用性群組 &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="5af0f-153">[Monitoring of Availability Groups &#40;SQL Server&#41;](monitoring-of-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="5af0f-154">AlwaysOn 可用性群組：互通性 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="5af0f-154">AlwaysOn Availability Groups: Interoperability (SQL Server)</span></span>](always-on-availability-groups-interoperability-sql-server.md)  
  
