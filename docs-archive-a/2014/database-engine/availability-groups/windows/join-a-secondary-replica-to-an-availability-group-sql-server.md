---
title: 將次要複本聯結至可用性群組 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.joinreplica.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], joining
- Availability Groups [SQL Server], configuring
ms.assetid: e5bd2489-097a-490e-8ea1-34fe48378ad1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c38c2d59a46b15fc9a1dca77ae6a67e8e59e1b80
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595269"
---
# <a name="join-a-secondary-replica-to-an-availability-group-sql-server"></a><span data-ttu-id="68f2e-102">將次要複本聯結至可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="68f2e-102">Join a Secondary Replica to an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="68f2e-103">此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]或 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中的 PowerShell，將次要複本聯結至 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="68f2e-103">This topic describes how to join a secondary replica to an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="68f2e-104">當次要複本加入至 AlwaysOn 可用性群組之後，此次要複本必須聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="68f2e-104">After a secondary replica is added to an AlwaysOn availability group, the secondary replica must be joined to the availability group.</span></span> <span data-ttu-id="68f2e-105">聯結複本作業必須在裝載次要複本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="68f2e-105">The join-replica operation must be performed on the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that is hosting the secondary replica.</span></span>  
  
-   <span data-ttu-id="68f2e-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="68f2e-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="68f2e-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="68f2e-107">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="68f2e-108">安全性</span><span class="sxs-lookup"><span data-stu-id="68f2e-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="68f2e-109">**若要使用下列項目來準備次要資料庫：**</span><span class="sxs-lookup"><span data-stu-id="68f2e-109">**To prepare a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="68f2e-110">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="68f2e-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="68f2e-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="68f2e-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="68f2e-112">PowerShell</span><span class="sxs-lookup"><span data-stu-id="68f2e-112">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="68f2e-113">**待處理：** [設定次要資料庫](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="68f2e-113">**Follow Up:** [Configure Secondary Databases](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="68f2e-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="68f2e-114">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="68f2e-115">必要條件</span><span class="sxs-lookup"><span data-stu-id="68f2e-115">Prerequisites</span></span>  
  
-   <span data-ttu-id="68f2e-116">可用性群組的主要複本目前必須在線上。</span><span class="sxs-lookup"><span data-stu-id="68f2e-116">The primary replica of the availability group must currently be online.</span></span>  
  
-   <span data-ttu-id="68f2e-117">您必須連接到伺服器執行個體，此執行個體會裝載尚未加入至可用性群組的次要複本。</span><span class="sxs-lookup"><span data-stu-id="68f2e-117">You must be connected to the server instance that hosts a secondary replica that has not yet have been joined to the availability group.</span></span>  
  
-   <span data-ttu-id="68f2e-118">本機伺服器執行個體必須能夠連接到裝載主要複本之伺服器執行個體的資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="68f2e-118">The local server instance must be able to connect to the database mirroring endpoint of the server instance that is hosting the primary replica.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="68f2e-119">如果不符合任何先決條件，聯結作業會失敗。</span><span class="sxs-lookup"><span data-stu-id="68f2e-119">If any prerequisite is not met, the join operation fails.</span></span> <span data-ttu-id="68f2e-120">聯結嘗試失敗之後，您可能需要連接至裝載主要複本的伺服器執行個體，以移除及重新加入次要複本，然後將其聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="68f2e-120">After a failed join attempt, you might need to connect to the server instance that hosts the primary replica to remove and re-add the secondary replica before you can join it to the availability group.</span></span> <span data-ttu-id="68f2e-121">如需詳細資訊，請參閱[將次要複本從可用性群組移除 &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md) 和[將次要複本加入至可用性群組 &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="68f2e-121">For more information, see [Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md) and [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="68f2e-122">Security</span><span class="sxs-lookup"><span data-stu-id="68f2e-122">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="68f2e-123">權限</span><span class="sxs-lookup"><span data-stu-id="68f2e-123">Permissions</span></span>  
 <span data-ttu-id="68f2e-124">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="68f2e-124">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="68f2e-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="68f2e-125">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="68f2e-126">**若要將可用性複本聯結至可用性群組**</span><span class="sxs-lookup"><span data-stu-id="68f2e-126">**To join an availability replica to an availability group**</span></span>  
  
1.  <span data-ttu-id="68f2e-127">在 [物件總管] 中，連接到裝載次要複本的伺服器執行個體，然後按一下伺服器名稱以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="68f2e-127">In Object Explorer, connect to the server instance that hosts the secondary replica, and click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="68f2e-128">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="68f2e-128">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="68f2e-129">選取所連接之次要複本的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="68f2e-129">Select the availability group of the secondary replica to which you are connected.</span></span>  
  
4.  <span data-ttu-id="68f2e-130">以滑鼠右鍵按一下次要複本，然後按一下 [加入可用性群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="68f2e-130">Right-click the secondary replica, and click **Join to Availability Group**.</span></span>  
  
5.  <span data-ttu-id="68f2e-131">這會開啟 **[將複本加入至可用性群組]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="68f2e-131">This opens the **Join Replica to Availability Group** dialog box.</span></span>  
  
6.  <span data-ttu-id="68f2e-132">若要將次要複本聯結至可用性群組，請按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="68f2e-132">To join the secondary replica to the availability group, click **OK**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="68f2e-133">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="68f2e-133">Using Transact-SQL</span></span>  
 <span data-ttu-id="68f2e-134">**若要將可用性複本聯結至可用性群組**</span><span class="sxs-lookup"><span data-stu-id="68f2e-134">**To join an availability replica to an availability group**</span></span>  
  
1.  <span data-ttu-id="68f2e-135">連接到裝載次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="68f2e-135">Connect to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="68f2e-136">使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 陳述式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="68f2e-136">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="68f2e-137">ALTER AVAILABILITY GROUP <群組名稱>\*\* JOIN</span><span class="sxs-lookup"><span data-stu-id="68f2e-137">ALTER AVAILABILITY GROUP *group_name* JOIN</span></span>  
  
     <span data-ttu-id="68f2e-138">其中 <群組名稱> 是可用性群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="68f2e-138">where *group_name* is the name of the availability group.</span></span>  
  
     <span data-ttu-id="68f2e-139">下列範例會將次要複本加入至 `MyAG` 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="68f2e-139">The following example, joins the secondary replica to the `MyAG` availability group.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG JOIN;  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="68f2e-140">若要查看內容中使用的這個 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式，請參閱 [建立可用性群組和 &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="68f2e-140">To see this [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement used in context, see [Create an Availability Group &#40;Transact-SQL&#41;](create-an-availability-group-transact-sql.md).</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="68f2e-141">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="68f2e-141">Using PowerShell</span></span>  
 <span data-ttu-id="68f2e-142">**若要將可用性複本聯結至可用性群組**</span><span class="sxs-lookup"><span data-stu-id="68f2e-142">**To join an availability replica to an availability group**</span></span>  
  
 <span data-ttu-id="68f2e-143">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 提供者內：</span><span class="sxs-lookup"><span data-stu-id="68f2e-143">In the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell provider:</span></span>  
  
1.  <span data-ttu-id="68f2e-144">將目錄切換到 (`cd`) 裝載次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="68f2e-144">Change directory (`cd`) to the server instance that hosts the secondary replica.</span></span>  
  
2.  <span data-ttu-id="68f2e-145">使用可用性群組的名稱執行 **Join-SqlAvailabilityGroup** Cmdlet，將次要複本聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="68f2e-145">Join the secondary replica to the availability group by executing the **Join-SqlAvailabilityGroup** cmdlet with the name of the availability group.</span></span>  
  
     <span data-ttu-id="68f2e-146">例如，下列命令會將位於指定路徑之伺服器執行個體所裝載的次要複本聯結至名為 `MyAg`的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="68f2e-146">For example, the following command joins a secondary replica hosted by the server instance located at the specified path to the availability group named `MyAg`.</span></span>  <span data-ttu-id="68f2e-147">這個伺服器執行個體必須裝載這個可用性群組中的次要複本。</span><span class="sxs-lookup"><span data-stu-id="68f2e-147">This server instance must host a secondary replica in this availability group.</span></span>  
  
    ```powershell
    Join-SqlAvailabilityGroup -Path SQLSERVER:\SQL\SecondaryServer\InstanceName -Name 'MyAg'  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="68f2e-148">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="68f2e-148">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="68f2e-149">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="68f2e-149">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="68f2e-150">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="68f2e-150">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="68f2e-151">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="68f2e-151">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-configure-secondary-databases"></a><a name="FollowUp"></a><span data-ttu-id="68f2e-152">後續操作：設定次要資料庫</span><span class="sxs-lookup"><span data-stu-id="68f2e-152">Follow Up: Configure Secondary Databases</span></span>  
 <span data-ttu-id="68f2e-153">對於可用性群組中的每個資料庫而言，您需要在裝載次要複本的伺服器執行個體上擁有次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="68f2e-153">For every database in the availability group, you need a secondary database on the server instance that is hosting the secondary replica.</span></span> <span data-ttu-id="68f2e-154">在您將次要複本加入可用性群組之前或之後，您都可以設定次要資料庫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="68f2e-154">You can configure secondary databases either before or after you join a secondary replica to an availability group, as follows:</span></span>  
  
1.  <span data-ttu-id="68f2e-155">針對每一個還原作業使用 RESTORE WITH NORECOVERY，將每一個主要資料庫的最新資料庫和記錄備份還原到裝載次要複本的伺服器執行個體上。</span><span class="sxs-lookup"><span data-stu-id="68f2e-155">Restore recent database and log backups of each primary database onto the server instance that hosts the secondary replica, using RESTORE WITH NORECOVERY for every restore operation.</span></span> <span data-ttu-id="68f2e-156">如需詳細資訊，請參閱 [針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)中的 PowerShell，將次要資料庫聯結至 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="68f2e-156">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="68f2e-157">將每一個次要資料庫加入可用性群組。</span><span class="sxs-lookup"><span data-stu-id="68f2e-157">Join each secondary database to the availability group.</span></span> <span data-ttu-id="68f2e-158">如需詳細資訊，請參閱 [將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="68f2e-158">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f2e-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68f2e-159">See Also</span></span>  
 <span data-ttu-id="68f2e-160">[建立及設定可用性群組 &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="68f2e-160">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="68f2e-161">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="68f2e-161">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="68f2e-162">針對 AlwaysOn 可用性群組 Configuration &#40;SQL Server&#41;已刪除進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="68f2e-162">Troubleshoot AlwaysOn Availability Groups Configuration &#40;SQL Server&#41;deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
