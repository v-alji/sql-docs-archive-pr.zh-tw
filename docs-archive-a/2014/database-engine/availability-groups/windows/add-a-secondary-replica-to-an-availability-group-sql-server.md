---
title: 將次要複本新增至可用性群組 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], configuring
ms.assetid: 6669dcce-85f9-495f-aadf-7f62cff4a9da
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 498103a781641c72e166c6b11663f5248ae5ccfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592262"
---
# <a name="add-a-secondary-replica-to-an-availability-group-sql-server"></a><span data-ttu-id="e7694-102">將次要複本加入至可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="e7694-102">Add a Secondary Replica to an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="e7694-103">此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]或 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中的 PowerShell，將次要複本加入至現有的 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="e7694-103">This topic describes how to add a secondary replica to an existing AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="e7694-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="e7694-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="e7694-105">必要條件和限制</span><span class="sxs-lookup"><span data-stu-id="e7694-105">Prerequisites and Restrictions</span></span>](#PrerequisitesRestrictions)  
  
     [<span data-ttu-id="e7694-106">安全性</span><span class="sxs-lookup"><span data-stu-id="e7694-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="e7694-107">**使用下列方法加入複本：**</span><span class="sxs-lookup"><span data-stu-id="e7694-107">**To add a replica, using:**</span></span>  
  
     [<span data-ttu-id="e7694-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e7694-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="e7694-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e7694-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="e7694-110">PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7694-110">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="e7694-111">**待處理：**  [加入次要複本之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="e7694-111">**Follow Up:**  [After Adding a Secondary Replica](#FollowUp)</span></span>  
  
## <a name="before-you-begin"></a><span data-ttu-id="e7694-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="e7694-112">Before You Begin</span></span>  
 <span data-ttu-id="e7694-113">我們強烈建議您先閱讀本節內容，然後再嘗試建立您的第一個可用性群組。</span><span class="sxs-lookup"><span data-stu-id="e7694-113">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
##  <a name="prerequisites-and-restrictions"></a><a name="PrerequisitesRestrictions"></a> <span data-ttu-id="e7694-114">必要條件和限制</span><span class="sxs-lookup"><span data-stu-id="e7694-114">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="e7694-115">您必須連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="e7694-115">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
 <span data-ttu-id="e7694-116">如需詳細資訊，請參閱 [AlwaysOn 可用性群組的必要條件、限制和建議 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="e7694-116">For more information, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
##  <a name="security"></a><a name="Security"></a> <span data-ttu-id="e7694-117">Security</span><span class="sxs-lookup"><span data-stu-id="e7694-117">Security</span></span>  
  
###  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="e7694-118">權限</span><span class="sxs-lookup"><span data-stu-id="e7694-118">Permissions</span></span>  
 <span data-ttu-id="e7694-119">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="e7694-119">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e7694-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e7694-120">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e7694-121">**加入複本**</span><span class="sxs-lookup"><span data-stu-id="e7694-121">**To add a replica**</span></span>  
  
1.  <span data-ttu-id="e7694-122">在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="e7694-122">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="e7694-123">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="e7694-123">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="e7694-124">以滑鼠右鍵按一下可用性群組，然後選取下列其中一個命令：</span><span class="sxs-lookup"><span data-stu-id="e7694-124">Right-click the availability group, and select one of the following commands:</span></span>  
  
    -   <span data-ttu-id="e7694-125">選取 **[加入複本]** 命令，以啟動 [將複本加入至可用性群組] 精靈。</span><span class="sxs-lookup"><span data-stu-id="e7694-125">Select the **Add Replica** command to launch the Add Replica to Availability Group Wizard.</span></span> <span data-ttu-id="e7694-126">如需詳細資訊，請參閱[使用將複本加入至可用性群組精靈 &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="e7694-126">For more information, see [Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md).</span></span>  
  
    -   <span data-ttu-id="e7694-127">或者，選取 **[屬性]** 命令，以開啟 **[可用性群組屬性]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="e7694-127">Alternatively, select the **Properties** command to open the **Availability Group Properties** dialog box.</span></span> <span data-ttu-id="e7694-128">在此對話方塊中加入複本的步驟如下：</span><span class="sxs-lookup"><span data-stu-id="e7694-128">The steps for adding a replica in this dialog box are as follows:</span></span>  
  
        1.  <span data-ttu-id="e7694-129">在對話方塊的 **[可用性複本]** 窗格中，按一下 **[加入]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="e7694-129">In the **Availability Replicas** pane of the dialog box, click the **Add** button.</span></span> <span data-ttu-id="e7694-130">這會建立及選取複本項目，其中的空白伺服器執行個體欄位為已選取。</span><span class="sxs-lookup"><span data-stu-id="e7694-130">This creates and selects a replica entry in which the blank Server Instance field is selected.</span></span>  
  
        2.  <span data-ttu-id="e7694-131">請輸入符合裝載可用性複本必要條件的伺服器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="e7694-131">Enter the name of a server instance that meets the prerequisites for hosting an availability replica.</span></span>  
  
         <span data-ttu-id="e7694-132">若要加入其他複本，請重複上述步驟。</span><span class="sxs-lookup"><span data-stu-id="e7694-132">To add an additional replicas, repeat the preceding steps.</span></span> <span data-ttu-id="e7694-133">當您指定好複本時，按一下 **[確定]** 以完成該作業。</span><span class="sxs-lookup"><span data-stu-id="e7694-133">When you are done specifying replicas, click **OK** to complete the operation.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="e7694-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="e7694-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="e7694-135">**加入複本**</span><span class="sxs-lookup"><span data-stu-id="e7694-135">**To add a replica**</span></span>  
  
1.  <span data-ttu-id="e7694-136">連接到裝載主要複本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e7694-136">Connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="e7694-137">使用 ALTER AVAILABILITY GROUP 陳述式的 ADD REPLICA ON 子句，將新的次要複本加入至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="e7694-137">Add the new secondary replica to the availability group by using the ADD REPLICA ON clause of the ALTER AVAILABILITY GROUP statement.</span></span> <span data-ttu-id="e7694-138">ENDPOINT_URL、AVAILABILITY_MODE 和 FAILOVER_MODE 選項在 ADD REPLICA ON 子句中是必要項。</span><span class="sxs-lookup"><span data-stu-id="e7694-138">The ENDPOINT_URL, AVAILABILITY_MODE, and FAILOVER_MODE options are required in an ADD REPLICA ON clause.</span></span> <span data-ttu-id="e7694-139">其他複本選項 BACKUP_PRIORITY、SECONDARY_ROLE、PRIMARY_ROLE 和 SESSION_TIMEOUT 都是選擇項。</span><span class="sxs-lookup"><span data-stu-id="e7694-139">The other replica options- BACKUP_PRIORITY, SECONDARY_ROLE, PRIMARY_ROLE, and SESSION_TIMEOUT-are optional.</span></span> <span data-ttu-id="e7694-140">如需詳細資訊，請參閱 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)中的 PowerShell，將次要複本加入現有的 AlwaysOn 可用性群組中。</span><span class="sxs-lookup"><span data-stu-id="e7694-140">For more information, see [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql).</span></span>  
  
     <span data-ttu-id="e7694-141">例如，下列 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 陳述式會在位於 `MyAG` 所裝載的預設伺服器執行個體的 `COMPUTER04`可用性群組中建立新的複本，而此電腦的端點 URL 為 `TCP://COMPUTER04.Adventure-Works.com:5022'`。</span><span class="sxs-lookup"><span data-stu-id="e7694-141">For example, the following [!INCLUDE[tsql](../../../includes/tsql-md.md)] statement creates a new replica to an availability group named `MyAG` on the default server instance hosted by `COMPUTER04`, whose endpoint URL is `TCP://COMPUTER04.Adventure-Works.com:5022'`.</span></span> <span data-ttu-id="e7694-142">此複本支援手動容錯移轉和非同步認可的可用性模式。</span><span class="sxs-lookup"><span data-stu-id="e7694-142">This replica supports manual failover and asynchronous-commit availability mode.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG ADD REPLICA ON 'COMPUTER04'   
       WITH (  
             ENDPOINT_URL = 'TCP://COMPUTER04.Adventure-Works.com:5022',  
             AVAILABILITY_MODE = ASYNCHRONOUS_COMMIT,  
             FAILOVER_MODE = MANUAL  
             );  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="e7694-143">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="e7694-143">Using PowerShell</span></span>  
 <span data-ttu-id="e7694-144">**加入複本**</span><span class="sxs-lookup"><span data-stu-id="e7694-144">**To add a replica**</span></span>  
  
1.  <span data-ttu-id="e7694-145">變更目錄 (`cd`) 為裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="e7694-145">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="e7694-146">使用 **New-SqlAvailabilityReplica** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="e7694-146">Use the **New-SqlAvailabilityReplica** cmdlet.</span></span>  
  
     <span data-ttu-id="e7694-147">例如，下列命令會將可用性複本加入至名為 `MyAg`的現有可用性群組。</span><span class="sxs-lookup"><span data-stu-id="e7694-147">For example, the following command adds an availability replica to an existing availability group named `MyAg`.</span></span> <span data-ttu-id="e7694-148">此複本支援手動容錯移轉和非同步認可的可用性模式。</span><span class="sxs-lookup"><span data-stu-id="e7694-148">This replica supports manual failover and asynchronous-commit availability mode.</span></span> <span data-ttu-id="e7694-149">在次要角色中，此複本將支援讀取連接，可讓您將唯讀處理卸載至此複本。</span><span class="sxs-lookup"><span data-stu-id="e7694-149">In the secondary role, this replica will support read access connections, allowing you to offload read-only processing to this replica.</span></span>  
  
    ```powershell
    $agPath = "SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg"  
    $endpointURL = "TCP://PrimaryServerName.domain.com:5022"  
    $failoverMode = "Manual"  
    $availabilityMode = "AsynchronousCommit"  
    $secondaryReadMode = "AllowAllConnections"  
  
    New-SqlAvailabilityReplica -Name SecondaryServer\Instance `   
    -EndpointUrl $endpointURL `   
    -FailoverMode $failoverMode `   
    -AvailabilityMode $availabilityMode `   
    -ConnectionModeInSecondaryRole $secondaryReadMode `   
    -Path $agPath  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="e7694-150">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="e7694-150">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="e7694-151">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="e7694-151">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="e7694-152">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="e7694-152">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="e7694-153">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="e7694-153">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-adding-a-secondary-replica"></a><a name="FollowUp"></a><span data-ttu-id="e7694-154">後續操作：加入次要複本之後</span><span class="sxs-lookup"><span data-stu-id="e7694-154">Follow Up: After Adding a Secondary Replica</span></span>  
 <span data-ttu-id="e7694-155">若要將複本加入至現有的可用性群組，您必須執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="e7694-155">To add a replica for an existing availability group, you must perform the following steps:</span></span>  
  
1.  <span data-ttu-id="e7694-156">連接到將要裝載新次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="e7694-156">Connect to the server instance that is going to host the new secondary replica.</span></span>  
  
2.  <span data-ttu-id="e7694-157">將新的次要複本加入可用性群組。</span><span class="sxs-lookup"><span data-stu-id="e7694-157">Join the new secondary replica to the availability group.</span></span> <span data-ttu-id="e7694-158">如需詳細資訊，請參閱 [將次要複本聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e7694-158">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="e7694-159">對於可用性群組中的每個資料庫，在裝載次要複本的伺服器執行個體上建立次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="e7694-159">For each database in the availability group, create a secondary database on the server instance that is hosting the secondary replica.</span></span> <span data-ttu-id="e7694-160">如需詳細資訊，請參閱 [針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)中的 PowerShell，將次要資料庫聯結至 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="e7694-160">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="e7694-161">將每一個新的次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="e7694-161">Join each of the new secondary databases to the availability group.</span></span> <span data-ttu-id="e7694-162">如需詳細資訊，請參閱 [將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e7694-162">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="e7694-163">相關工作</span><span class="sxs-lookup"><span data-stu-id="e7694-163">Related Tasks</span></span>  
 <span data-ttu-id="e7694-164">**管理可用性複本**</span><span class="sxs-lookup"><span data-stu-id="e7694-164">**To manage an availability replica**</span></span>  
  
-   [<span data-ttu-id="e7694-165">將次要複本聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e7694-165">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="e7694-166">將次要複本從可用性群組移除 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e7694-166">Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;</span></span>](remove-a-secondary-replica-from-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="e7694-167">設定可用性複本的唯讀存取 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e7694-167">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="e7694-168">變更可用性複本的可用性模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e7694-168">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="e7694-169">變更可用性複本的容錯移轉模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e7694-169">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="e7694-170">變更可用性複本的工作階段逾時期限 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e7694-170">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="e7694-171">變更可用性複本的工作階段逾時期限 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e7694-171">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="e7694-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e7694-172">See Also</span></span>  
 <span data-ttu-id="e7694-173">[ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e7694-173">[ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) </span></span>  
 <span data-ttu-id="e7694-174">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e7694-174">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="e7694-175">[建立及設定可用性群組 &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e7694-175">[Creation and Configuration of Availability Groups &#40;SQL Server&#41;](creation-and-configuration-of-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="e7694-176">[使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="e7694-176">[Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="e7694-177">監視可用性群組 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="e7694-177">Monitor Availability Groups &#40;Transact-SQL&#41;</span></span>](monitor-availability-groups-transact-sql.md)  
  
  
