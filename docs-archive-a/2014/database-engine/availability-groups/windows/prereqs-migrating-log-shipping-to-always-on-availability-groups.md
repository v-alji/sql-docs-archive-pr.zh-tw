---
title: 從記錄傳送遷移至 AlwaysOn 可用性群組 (SQL Server) 的必要條件 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], AlwaysOn Availability Groups
- Availability Groups [SQL Server], interoperability
ms.assetid: 2738ce65-205e-4682-92d8-dc7e37c58b2b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 76b50d5af8eb520b3764ff56397c040f2d0d0141
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703293"
---
# <a name="prerequisites-for-migrating-from-log-shipping-to-alwayson-availability-groups-sql-server"></a><span data-ttu-id="f4480-102">從記錄傳送移轉至 AlwaysOn 可用性群組的必要條件 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f4480-102">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups (SQL Server)</span></span>
  <span data-ttu-id="f4480-103">本主題描述將記錄傳送主要資料庫與其一個或多個次要資料庫轉換成 AlwaysOn 主要資料庫和次要資料庫的必要條件。</span><span class="sxs-lookup"><span data-stu-id="f4480-103">This topic describes the prerequisites for converting a log shipping primary database along with one or more of its secondary databases to an AlwaysOn primary database and secondary database(s).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f4480-104">您可以將可用性群組中的任何主要或次要資料庫 (可能是可讀取) 設定為記錄傳送主要資料庫。</span><span class="sxs-lookup"><span data-stu-id="f4480-104">You can configure any primary or secondary database (possibly readable) in an availability group as a log shipping primary database.</span></span>  
  
 <span data-ttu-id="f4480-105">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="f4480-105">**In This Topic:**</span></span>  
  
-   [<span data-ttu-id="f4480-106">可用性群組必要條件</span><span class="sxs-lookup"><span data-stu-id="f4480-106">Availability Group Prerequisites</span></span>](#AGPrereqsRealAddress)  
  
-   [<span data-ttu-id="f4480-107">記錄傳送必要條件</span><span class="sxs-lookup"><span data-stu-id="f4480-107">Log Shipping Prerequisites</span></span>](#LogShipPrereqs)  
  
-   [<span data-ttu-id="f4480-108">相關工作</span><span class="sxs-lookup"><span data-stu-id="f4480-108">Related Tasks</span></span>](#RelatedTasks)  
  
-   [<span data-ttu-id="f4480-109">相關內容</span><span class="sxs-lookup"><span data-stu-id="f4480-109">Related Content</span></span>](#RelatedContent)  
  
##  <a name="availability-group-prerequisites"></a><a name="AGPrereqsRealAddress"></a><span data-ttu-id="f4480-110">可用性群組必要條件</span><span class="sxs-lookup"><span data-stu-id="f4480-110">Availability Group Prerequisites</span></span>  
 <span data-ttu-id="f4480-111">若要允許備份作業在可用性群組的主要複本上執行，請使用下列 AlwaysOn 可用性群組備份設定：</span><span class="sxs-lookup"><span data-stu-id="f4480-111">To allow backup jobs to run on the primary replica of the availability group, use the following AlwaysOn Availability Groups backup settings:</span></span>  
  
|<span data-ttu-id="f4480-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f4480-112">Property</span></span>|<span data-ttu-id="f4480-113">設定</span><span class="sxs-lookup"><span data-stu-id="f4480-113">Setting</span></span>|  
|--------------|-------------|  
|<span data-ttu-id="f4480-114">可用性群組的自動備份喜好設定</span><span class="sxs-lookup"><span data-stu-id="f4480-114">Automated backup preference of availability group</span></span>|<span data-ttu-id="f4480-115">只在主要複本上</span><span class="sxs-lookup"><span data-stu-id="f4480-115">Only on the primary replica</span></span>|  
|<span data-ttu-id="f4480-116">主要複本的備份優先權。</span><span class="sxs-lookup"><span data-stu-id="f4480-116">Backup priority of the primary replica.</span></span>|<span data-ttu-id="f4480-117">>0</span><span class="sxs-lookup"><span data-stu-id="f4480-117">>0</span></span>|  
  
 <span data-ttu-id="f4480-118">**如需詳細資訊：**</span><span class="sxs-lookup"><span data-stu-id="f4480-118">**For more information:**</span></span>  
  
 [<span data-ttu-id="f4480-119">檢視可用性群組屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f4480-119">View Availability Group Properties &#40;SQL Server&#41;</span></span>](view-availability-group-properties-sql-server.md)  
  
 [<span data-ttu-id="f4480-120">設定可用性複本的備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f4480-120">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="log-shipping-prerequisites"></a><a name="LogShipPrereqs"></a> <span data-ttu-id="f4480-121">記錄傳送必要條件</span><span class="sxs-lookup"><span data-stu-id="f4480-121">Log Shipping Prerequisites</span></span>  
  
-   <span data-ttu-id="f4480-122">記錄傳送主要資料庫必須位於主控可用性群組之初始/目前主要複本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上。</span><span class="sxs-lookup"><span data-stu-id="f4480-122">The log shipping primary database must reside on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the initial/current primary replica of the availability group.</span></span>  
  
-   <span data-ttu-id="f4480-123">為了將指定的記錄傳送次要資料庫轉換成 AlwaysOn 次要資料庫，它必須：</span><span class="sxs-lookup"><span data-stu-id="f4480-123">For a given log shipping secondary database to be converted to an AlwaysOn secondary database, it must:</span></span>  
  
    -   <span data-ttu-id="f4480-124">使用與主要資料庫相同的名稱。</span><span class="sxs-lookup"><span data-stu-id="f4480-124">Use the same name as the primary database.</span></span>  
  
    -   <span data-ttu-id="f4480-125">位於主控可用性群組之次要複本的伺服器執行個體上。</span><span class="sxs-lookup"><span data-stu-id="f4480-125">Reside on a server instance that hosts a secondary replica for the availability group.</span></span>  
  
 <span data-ttu-id="f4480-126">備份作業在主要資料庫上執行之後，請停用備份作業；還原作業在指定的次要資料庫上執行之後，請停用還原作業。</span><span class="sxs-lookup"><span data-stu-id="f4480-126">Once the backup job has run on the primary database, disable the backup job, and once the restore job has run on a given secondary database, disable the restore job.</span></span>  
  
 <span data-ttu-id="f4480-127">為可用性群組建立所有次要資料庫之後，如果您想要在次要複本上執行備份，則需要重新設定可用性群組的自動備份喜好設定。</span><span class="sxs-lookup"><span data-stu-id="f4480-127">After you have created all the secondary databases for the availability group, if you want to perform backups on secondary replicas, you need to re-configure the automated backup preference of the availability group.</span></span>  
  
 <span data-ttu-id="f4480-128">**如需詳細資訊：**</span><span class="sxs-lookup"><span data-stu-id="f4480-128">**For more information:**</span></span>  
  
 <span data-ttu-id="f4480-129">[Converting a logshipping configuration to Availability Group](https://blogs.msdn.com/b/sqlalwayson/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx) (將記錄傳送組態轉換成可用性群組) (SQL Server 部落格)</span><span class="sxs-lookup"><span data-stu-id="f4480-129">[Converting a logshipping configuration to Availability Group](https://blogs.msdn.com/b/sqlalwayson/archive/2012/01/09/converting-a-logshipping-configuration-to-availability-group.aspx) (a SQL Server blog)</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="f4480-130">相關工作</span><span class="sxs-lookup"><span data-stu-id="f4480-130">Related Tasks</span></span>  
 <span data-ttu-id="f4480-131">**記錄傳送**</span><span class="sxs-lookup"><span data-stu-id="f4480-131">**Log shipping**</span></span>  
  
-   [<span data-ttu-id="f4480-132">將記錄傳送升級至 SQL Server 2014 &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="f4480-132">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](../../log-shipping/upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="f4480-133">移除記錄傳送 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f4480-133">Remove Log Shipping &#40;SQL Server&#41;</span></span>](../../log-shipping/remove-log-shipping-sql-server.md)  
  
 <span data-ttu-id="f4480-134">**AlwaysOn 可用性群組**</span><span class="sxs-lookup"><span data-stu-id="f4480-134">**AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="f4480-135">使用可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f4480-135">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="f4480-136">使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="f4480-136">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="f4480-137">建立可用性群組 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="f4480-137">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="f4480-138">建立可用性群組 &#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="f4480-138">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
-   [<span data-ttu-id="f4480-139">將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f4480-139">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="f4480-140">設定可用性複本的備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f4480-140">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="f4480-141">相關內容</span><span class="sxs-lookup"><span data-stu-id="f4480-141">Related Content</span></span>  
  
-   <span data-ttu-id="f4480-142">**部落格：**</span><span class="sxs-lookup"><span data-stu-id="f4480-142">**Blogs:**</span></span>  
  
     [<span data-ttu-id="f4480-143">Converting a logshipping configuration to Availability Group</span><span class="sxs-lookup"><span data-stu-id="f4480-143">Converting a logshipping configuration to Availability Group</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/converting-a-logshipping-configuration-to-availability-group)  
  
     [<span data-ttu-id="f4480-144">將記錄傳送主要資料庫和次要資料庫加入至現有的可用性群組</span><span class="sxs-lookup"><span data-stu-id="f4480-144">Add a Log Shipping Primary Database and Secondary Database(s) to an Existing Availability Group</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/add-a-log-shipping-primary-database-and-secondary-databases-to-an-existing-availability-group)  
  
     [<span data-ttu-id="f4480-145">SQL Server AlwaysOn 團隊部落格：官方 SQL Server AlwaysOn 團隊部落格</span><span class="sxs-lookup"><span data-stu-id="f4480-145">SQL Server AlwaysOn Team Blogs: The official SQL Server AlwaysOn Team Blog</span></span>](https://docs.microsoft.com/archive/blogs/sqlalwayson/)  
  
     [<span data-ttu-id="f4480-146">CSS SQL Server 工程師部落格</span><span class="sxs-lookup"><span data-stu-id="f4480-146">CSS SQL Server Engineers Blogs</span></span>](https://blogs.msdn.com/b/psssql/)  
  
-   <span data-ttu-id="f4480-147">**白皮書：**</span><span class="sxs-lookup"><span data-stu-id="f4480-147">**Whitepapers:**</span></span>  
  
     [<span data-ttu-id="f4480-148">移轉指南：從結合資料庫鏡像與記錄傳送的先前部署移轉至 AlwaysOn 可用性群組</span><span class="sxs-lookup"><span data-stu-id="f4480-148">Migration Guide: Migrating to AlwaysOn Availability Groups from Prior Deployments Combining Database Mirroring and Log Shipping</span></span>](https://msdn.microsoft.com/library/jj635217)  
  
     [<span data-ttu-id="f4480-149">Microsoft 的 SQL Server 2012 白皮書</span><span class="sxs-lookup"><span data-stu-id="f4480-149">Microsoft White Papers for SQL Server 2012</span></span>](https://msdn.microsoft.com/library/hh403491.aspx)  
  
     [<span data-ttu-id="f4480-150">SQL Server 客戶諮詢團隊白皮書</span><span class="sxs-lookup"><span data-stu-id="f4480-150">SQL Server Customer Advisory Team Whitepapers</span></span>](http://sqlcat.com/)  
  
## <a name="see-also"></a><span data-ttu-id="f4480-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4480-151">See Also</span></span>  
 <span data-ttu-id="f4480-152">[關於記錄傳送 &#40;SQL Server&#41;](../../log-shipping/about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f4480-152">[About Log Shipping &#40;SQL Server&#41;](../../log-shipping/about-log-shipping-sql-server.md) </span></span>  
 <span data-ttu-id="f4480-153">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f4480-153">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="f4480-154">監視可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f4480-154">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](monitoring-of-availability-groups-sql-server.md)  
  
  
