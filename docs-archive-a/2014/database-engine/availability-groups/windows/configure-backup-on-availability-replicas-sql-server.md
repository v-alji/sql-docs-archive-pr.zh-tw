---
title: 設定可用性複本的備份 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- backup priority
- backup on secondary replicas
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], backup on secondary replicas
- active secondary replicas [SQL Server], backup on
- automated backup preference
- Availability Groups [SQL Server], active secondary replicas
ms.assetid: 74bc40bb-9f57-44e4-8988-1d69c0585eb6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 91a781d957eb2f5a81d323fc3c65c93e34945c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708669"
---
# <a name="configure-backup-on-availability-replicas-sql-server"></a><span data-ttu-id="eed10-102">設定可用性複本的備份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="eed10-102">Configure Backup on Availability Replicas (SQL Server)</span></span>
  <span data-ttu-id="eed10-103">本主題描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]中的 [!INCLUDE[tsql](../../../includes/tsql-md.md)]、 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]或 PowerShell，針對 AlwaysOn 可用性群組設定次要複本的備份。</span><span class="sxs-lookup"><span data-stu-id="eed10-103">This topic describes how to configure backup on secondary replicas for an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eed10-104">如需在次要複本上進行備份的簡介，請參閱使用中[次要：在次要複本上備份 (AlwaysOn 可用性群組) ](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="eed10-104">For an introduction to backup on secondary replicas, see [Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md).</span></span>  
  
 
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="eed10-105">開始之前</span><span class="sxs-lookup"><span data-stu-id="eed10-105">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="eed10-106">必要條件</span><span class="sxs-lookup"><span data-stu-id="eed10-106">Prerequisites</span></span>  
 <span data-ttu-id="eed10-107">您必須連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="eed10-107">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="eed10-108">Security</span><span class="sxs-lookup"><span data-stu-id="eed10-108">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="eed10-109">權限</span><span class="sxs-lookup"><span data-stu-id="eed10-109">Permissions</span></span>  
  
|<span data-ttu-id="eed10-110">Task</span><span class="sxs-lookup"><span data-stu-id="eed10-110">Task</span></span>|<span data-ttu-id="eed10-111">權限</span><span class="sxs-lookup"><span data-stu-id="eed10-111">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="eed10-112">若要在建立可用性群組時設定次要複本的備份</span><span class="sxs-lookup"><span data-stu-id="eed10-112">To configure backup on secondary replicas when creating an availability group</span></span>|<span data-ttu-id="eed10-113">需要 **系統管理員 (sysadmin)** 固定伺服器角色的成員資格，以及 CREATE AVAILABILITY GROUP 伺服器權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="eed10-113">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
|<span data-ttu-id="eed10-114">若要修改可用性群組或可用性複本</span><span class="sxs-lookup"><span data-stu-id="eed10-114">To modify an availability group or availability replica</span></span>|<span data-ttu-id="eed10-115">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="eed10-115">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>|  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="eed10-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="eed10-116">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="eed10-117">**若要設定次要複本的備份**</span><span class="sxs-lookup"><span data-stu-id="eed10-117">**To configure backup on secondary replicas**</span></span>  
  
1.  <span data-ttu-id="eed10-118">在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，然後按一下伺服器名稱以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="eed10-118">In Object Explorer, connect to the server instance that hosts the primary replica, and click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="eed10-119">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="eed10-119">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="eed10-120">按一下您想要設定其備份喜好設定的可用性群組，然後選取 **[屬性]** 命令。</span><span class="sxs-lookup"><span data-stu-id="eed10-120">Click the availability group whose backup preferences you want to configure, and select the **Properties** command.</span></span>  
  
4.  <span data-ttu-id="eed10-121">在 **[可用性群組屬性]** 對話方塊中，選取 **[備份喜好設定]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="eed10-121">In the **Availability Group Properties** dialog box, select **Backup Preferences** page.</span></span>  
  
5.  <span data-ttu-id="eed10-122">在 **[應該在何處執行備份?]** 面板上，選取可用性群組的自動備份喜好設定，它有下列幾種：</span><span class="sxs-lookup"><span data-stu-id="eed10-122">On the **Where should backups occur?** panel, select the automated backup preference for the availability group, one of:</span></span>  
  
     <span data-ttu-id="eed10-123">**慣用次要**</span><span class="sxs-lookup"><span data-stu-id="eed10-123">**Prefer Secondary**</span></span>  
     <span data-ttu-id="eed10-124">指定應該在次要複本上進行備份，但是主要複本是唯一線上複本的情況例外。</span><span class="sxs-lookup"><span data-stu-id="eed10-124">Specifies that backups should occur on a secondary replica except when the primary replica is the only replica online.</span></span> <span data-ttu-id="eed10-125">在此情況下，應該在主要複本上進行備份。</span><span class="sxs-lookup"><span data-stu-id="eed10-125">In that case, the backup should occur on the primary replica.</span></span> <span data-ttu-id="eed10-126">這是預設選項。</span><span class="sxs-lookup"><span data-stu-id="eed10-126">This is the default option.</span></span>  
  
     <span data-ttu-id="eed10-127">**僅次要**</span><span class="sxs-lookup"><span data-stu-id="eed10-127">**Secondary only**</span></span>  
     <span data-ttu-id="eed10-128">指定絕對不能在主要複本上執行備份。</span><span class="sxs-lookup"><span data-stu-id="eed10-128">Specifies that backups should never be performed on the primary replica.</span></span> <span data-ttu-id="eed10-129">如果主要複本是唯一的線上複本，不應該進行備份。</span><span class="sxs-lookup"><span data-stu-id="eed10-129">If the primary replica is the only replica online, the backup should not occur.</span></span>  
  
     `Primary`  
     <span data-ttu-id="eed10-130">指定備份一定要在主要複本上進行。</span><span class="sxs-lookup"><span data-stu-id="eed10-130">Specifies that the backups should always occur on the primary replica.</span></span> <span data-ttu-id="eed10-131">如果當您在次要複本上執行備份時，需要不支援的備份功能 (例如建立差異備份)，這個選項會很實用。</span><span class="sxs-lookup"><span data-stu-id="eed10-131">This option is useful if you need backup features, such as creating differential backups, that are not supported when backup is run on a secondary replica.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="eed10-132">如果您計畫要使用記錄傳送來準備可用性群組的任何次要資料庫，請將自動備份喜好設定設為 `Primary`，直到所有次要資料庫都已經準備完成並且聯結至可用性群組為止。</span><span class="sxs-lookup"><span data-stu-id="eed10-132">If you plan to use log shipping to prepare any secondary databases for an availability group, set the automated backup preference to `Primary` until all the secondary databases have been prepared and joined to the availability group.</span></span>  
  
     <span data-ttu-id="eed10-133">**任何複本**</span><span class="sxs-lookup"><span data-stu-id="eed10-133">**Any Replica**</span></span>  
     <span data-ttu-id="eed10-134">指定當您選擇要執行備份的複本時，您希望備份作業忽略可用性複本的角色。</span><span class="sxs-lookup"><span data-stu-id="eed10-134">Specifies that you prefer that backup jobs ignore the role of the availability replicas when choosing the replica to perform backups.</span></span> <span data-ttu-id="eed10-135">請注意，備份作業可能會評估其他因素，例如每個可用性複本的備份優先權，搭配其操作狀態和連接狀態。</span><span class="sxs-lookup"><span data-stu-id="eed10-135">Note backup jobs might evaluate other factors such as backup priority of each availability replica in combination with its operational state and connected state.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="eed10-136">不會強制執行自動備份喜好設定。</span><span class="sxs-lookup"><span data-stu-id="eed10-136">There is no enforcement of the automated backup preference setting.</span></span> <span data-ttu-id="eed10-137">這個喜好設定的解譯取決於您在給定可用性群組之資料庫的備份作業中所編寫的邏輯 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="eed10-137">The interpretation of this preference depends on the logic, if any, that you script into backup jobs for the databases in a given availability group.</span></span> <span data-ttu-id="eed10-138">自動備份喜好設定對於特定備份沒有任何影響。</span><span class="sxs-lookup"><span data-stu-id="eed10-138">The automated backup preference setting has no impact on ad-hoc backups.</span></span> <span data-ttu-id="eed10-139">如需詳細資訊，請參閱本主題稍後的＜ [後續操作：設定次要複本的備份之後](#FollowUp) ＞。</span><span class="sxs-lookup"><span data-stu-id="eed10-139">For more information, see [Follow Up: After Configuring Backup on Secondary Replicas](#FollowUp) later in this topic.</span></span>  
  
6.  <span data-ttu-id="eed10-140">您可以使用 **[複本備份優先權]** 方格來變更可用性複本的備份優先權。</span><span class="sxs-lookup"><span data-stu-id="eed10-140">Use the **Replica backup priorities** grid to change the backup priority of the availability replicas.</span></span> <span data-ttu-id="eed10-141">此方格顯示裝載可用性群組複本的每個伺服器執行個體的目前備份優先權。</span><span class="sxs-lookup"><span data-stu-id="eed10-141">This grid displays the current backup priority of each server instance that hosts a replica for the availability group.</span></span> <span data-ttu-id="eed10-142">方格資料行如下所示：</span><span class="sxs-lookup"><span data-stu-id="eed10-142">The grid columns are as follows:</span></span>  
  
     <span data-ttu-id="eed10-143">**伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="eed10-143">**Server Instance**</span></span>  
     <span data-ttu-id="eed10-144">裝載可用性複本之 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="eed10-144">The name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica.</span></span>  
  
     <span data-ttu-id="eed10-145">**備份優先權 (最低 = 1，最高 = 100)**</span><span class="sxs-lookup"><span data-stu-id="eed10-145">**Backup Priority (Lowest=1, Highest=100)**</span></span>  
     <span data-ttu-id="eed10-146">指定在這個複本上執行備份的優先權 (相對於相同可用性群組中的其他複本)。</span><span class="sxs-lookup"><span data-stu-id="eed10-146">Specifies your priority for performing backups on this replica relative to the other replicas in the same availability group.</span></span> <span data-ttu-id="eed10-147">這個值是 0 到 100 範圍之間的整數。</span><span class="sxs-lookup"><span data-stu-id="eed10-147">The value is an integer in the range of 0..100.</span></span> <span data-ttu-id="eed10-148">1 表示最低優先權，100 表示最高優先權。</span><span class="sxs-lookup"><span data-stu-id="eed10-148">1 indicates the lowest priority, and 100 indicates the highest priority.</span></span> <span data-ttu-id="eed10-149">如果 [備份優先權]\*\*\*\* = 1，則只有當目前沒有更高優先權的可用性複本可用時，才會選擇此可用性複本來執行備份。</span><span class="sxs-lookup"><span data-stu-id="eed10-149">If **Backup Priority** = 1, the availability replica would be chosen for performing backups only if no higher priority availability replicas are currently available.</span></span>  
  
     <span data-ttu-id="eed10-150">**排除複本**</span><span class="sxs-lookup"><span data-stu-id="eed10-150">**Exclude Replica**</span></span>  
     <span data-ttu-id="eed10-151">決定是否絕對不要選擇這個可用性複本來執行備份。</span><span class="sxs-lookup"><span data-stu-id="eed10-151">Select if you never want this availability replica to be chosen for performing backups.</span></span> <span data-ttu-id="eed10-152">例如，這對於您永遠不希望將備份容錯移轉到其中的遠端可用性複本十分有用。</span><span class="sxs-lookup"><span data-stu-id="eed10-152">This is useful, for example, for a remote availability replica to which you never want backups to fail over.</span></span>  
  
7.  <span data-ttu-id="eed10-153">若要認可變更，請按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="eed10-153">To commit your changes, click **OK**.</span></span>  
  
 <span data-ttu-id="eed10-154">**存取備份喜好設定頁面的其他方式**</span><span class="sxs-lookup"><span data-stu-id="eed10-154">**Alternative ways to access the Backup Preferences page**</span></span>  
  
-   [<span data-ttu-id="eed10-155">使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="eed10-155">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   <span data-ttu-id="eed10-156">[使用 [將複本加入可用性群組中精靈] &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="eed10-156">[Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="eed10-157">使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="eed10-157">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="eed10-158">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eed10-158">Using Transact-SQL</span></span>  
 <span data-ttu-id="eed10-159">**若要設定次要複本的備份**</span><span class="sxs-lookup"><span data-stu-id="eed10-159">**To configure backup on secondary replicas**</span></span>  
  
1.  <span data-ttu-id="eed10-160">連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="eed10-160">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="eed10-161">若為新的可用性群組，請使用 [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="eed10-161">For a new availability group, use the [CREATE AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-availability-group-transact-sql) statement.</span></span> <span data-ttu-id="eed10-162">如果您要修改現有的可用性群組，請使用 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="eed10-162">If you are modifying an existing availability group, use the [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql) statement.</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="eed10-163">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="eed10-163">Using PowerShell</span></span>  

### <a name="to-configure-backup-on-secondary-replicas"></a><span data-ttu-id="eed10-164">若要設定次要複本的備份</span><span class="sxs-lookup"><span data-stu-id="eed10-164">To configure backup on secondary replicas</span></span>
  
1.  <span data-ttu-id="eed10-165">將預設值 (`cd`) 設定為裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="eed10-165">Set default (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="eed10-166">(選擇性) 設定您要加入或修改之每個可用性複本的備份優先權。</span><span class="sxs-lookup"><span data-stu-id="eed10-166">Optionally, configure the backup priority of each availability replica that you are adding or modifying.</span></span> <span data-ttu-id="eed10-167">裝載主要複本的伺服器執行個體會使用這個優先權來決定哪個複本應該服務可用性群組中資料庫的自動備份要求 (系統會選擇優先權最高的複本)。</span><span class="sxs-lookup"><span data-stu-id="eed10-167">This priority is used by the server instance that hosts the primary replica to decide which replica should service an automated backup request on a database in the availability group (the replica with highest priority is chosen).</span></span> <span data-ttu-id="eed10-168">這個優先權可以是 0 和 100 (含) 之間的任何數字。</span><span class="sxs-lookup"><span data-stu-id="eed10-168">This priority can be any number between 0 and 100, inclusive.</span></span> <span data-ttu-id="eed10-169">如果優先權為 0，就表示系統不應該將複本視為服務備份要求的候選。</span><span class="sxs-lookup"><span data-stu-id="eed10-169">A priority of 0 indicates that the replica should not be considered as a candidate for servicing backup requests.</span></span>  <span data-ttu-id="eed10-170">預設值為 50。</span><span class="sxs-lookup"><span data-stu-id="eed10-170">The default setting is 50.</span></span>  
  
     <span data-ttu-id="eed10-171">將可用性複本加入至可用性群組時，請使用 `New-SqlAvailabilityReplica` 指令程式。</span><span class="sxs-lookup"><span data-stu-id="eed10-171">When adding an availability replica to an availability group, use the `New-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="eed10-172">修改現有的可用性複本時，請使用 `Set-SqlAvailabilityReplica` 指令程式。</span><span class="sxs-lookup"><span data-stu-id="eed10-172">When modifying an existing availability replica, use the `Set-SqlAvailabilityReplica` cmdlet.</span></span> <span data-ttu-id="eed10-173">不論是哪一種情況，請指定 `BackupPriority` *n*參數，其中*n*是介於0到100之間的值。</span><span class="sxs-lookup"><span data-stu-id="eed10-173">In either case, specify the `BackupPriority`*n* parameter, where *n* is a value from 0 to 100.</span></span>  
  
     <span data-ttu-id="eed10-174">例如，下列命令會將可用性複本 `MyReplica` 的備份優先權設定為 `60`。</span><span class="sxs-lookup"><span data-stu-id="eed10-174">For example, the following command sets the backup priority of the availability replica `MyReplica` to `60`.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityReplica -BackupPriority 60 -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
3.  <span data-ttu-id="eed10-175">(選擇性) 設定您要建立或修改之可用性群組的自動備份喜好設定。</span><span class="sxs-lookup"><span data-stu-id="eed10-175">Optionally, configure the automated backup preference for the availability group that you are creating  or modifying.</span></span> <span data-ttu-id="eed10-176">這個喜好設定會指出備份作業在選擇要在何處執行備份時應該如何評估主要複本。</span><span class="sxs-lookup"><span data-stu-id="eed10-176">This preference indicates how a backup job should evaluate the primary replica when choosing where to perform backups.</span></span> <span data-ttu-id="eed10-177">預設設定是慣用次要複本。</span><span class="sxs-lookup"><span data-stu-id="eed10-177">The default setting is to prefer secondary replicas.</span></span>  
  
     <span data-ttu-id="eed10-178">建立可用性群組時，請使用 `New-SqlAvailabilityGroup` 指令程式。</span><span class="sxs-lookup"><span data-stu-id="eed10-178">When creating an availability group, use the `New-SqlAvailabilityGroup` cmdlet.</span></span> <span data-ttu-id="eed10-179">修改現有的可用性群組時，請使用 `Set-SqlAvailabilityGroup` 指令程式。</span><span class="sxs-lookup"><span data-stu-id="eed10-179">When modifying an existing availability group, use the `Set-SqlAvailabilityGroup` cmdlet.</span></span> <span data-ttu-id="eed10-180">在任何一種情況中，請指定 `AutomatedBackupPreference` 參數。</span><span class="sxs-lookup"><span data-stu-id="eed10-180">In either case, specify the `AutomatedBackupPreference` parameter.</span></span>  
  
     <span data-ttu-id="eed10-181">其中</span><span class="sxs-lookup"><span data-stu-id="eed10-181">where,</span></span>  
  
     `Primary`  
     <span data-ttu-id="eed10-182">指定備份一定要在主要複本上進行。</span><span class="sxs-lookup"><span data-stu-id="eed10-182">Specifies that the backups should always occur on the primary replica.</span></span> <span data-ttu-id="eed10-183">如果當您在次要複本上執行備份時，需要不支援的備份功能 (例如建立差異備份)，這個選項會很實用。</span><span class="sxs-lookup"><span data-stu-id="eed10-183">This option is useful if you need backup features, such as creating differential backups, that are not supported when backup is run on a secondary replica.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="eed10-184">如果您計畫要使用記錄傳送來準備可用性群組的任何次要資料庫，請將自動備份喜好設定設為 `Primary`，直到所有次要資料庫都已經準備完成並且聯結至可用性群組為止。</span><span class="sxs-lookup"><span data-stu-id="eed10-184">If you plan to use log shipping to prepare any secondary databases for an availability group, set the automated backup preference to `Primary` until all the secondary databases have been prepared and joined to the availability group.</span></span>  
  
     `SecondaryOnly`  
     <span data-ttu-id="eed10-185">指定絕對不能在主要複本上執行備份。</span><span class="sxs-lookup"><span data-stu-id="eed10-185">Specifies that backups should never be performed on the primary replica.</span></span> <span data-ttu-id="eed10-186">如果主要複本是唯一的線上複本，不應該進行備份。</span><span class="sxs-lookup"><span data-stu-id="eed10-186">If the primary replica is the only replica online, the backup should not occur.</span></span>  
  
     `Secondary`  
     <span data-ttu-id="eed10-187">指定應該在次要複本上進行備份，但是主要複本是唯一線上複本的情況例外。</span><span class="sxs-lookup"><span data-stu-id="eed10-187">Specifies that backups should occur on a secondary replica except when the primary replica is the only replica online.</span></span> <span data-ttu-id="eed10-188">在此情況下，應該在主要複本上進行備份。</span><span class="sxs-lookup"><span data-stu-id="eed10-188">In that case, the backup should occur on the primary replica.</span></span> <span data-ttu-id="eed10-189">此為預設行為。</span><span class="sxs-lookup"><span data-stu-id="eed10-189">This is the default behavior.</span></span>  
  
     `None`  
     <span data-ttu-id="eed10-190">指定當您選擇要執行備份的複本時，您希望備份作業忽略可用性複本的角色。</span><span class="sxs-lookup"><span data-stu-id="eed10-190">Specifies that you prefer that backup jobs ignore the role of the availability replicas when choosing the replica to perform backups.</span></span> <span data-ttu-id="eed10-191">請注意，備份作業可能會評估其他因素，例如每個可用性複本的備份優先權，搭配其操作狀態和連接狀態。</span><span class="sxs-lookup"><span data-stu-id="eed10-191">Note backup jobs might evaluate other factors such as backup priority of each availability replica in combination with its operational state and  connected state.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="eed10-192">不會強制執行 `AutomatedBackupPreference`。</span><span class="sxs-lookup"><span data-stu-id="eed10-192">There is no enforcement of `AutomatedBackupPreference`.</span></span> <span data-ttu-id="eed10-193">這個喜好設定的解譯取決於您在給定可用性群組之資料庫的備份作業中所編寫的邏輯 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="eed10-193">The interpretation of this preference depends on the logic, if any, that you script into backup jobs for the databases in a given availability group.</span></span> <span data-ttu-id="eed10-194">自動備份喜好設定對於特定備份沒有任何影響。</span><span class="sxs-lookup"><span data-stu-id="eed10-194">The automated backup preference setting has no impact on ad-hoc backups.</span></span> <span data-ttu-id="eed10-195">如需詳細資訊，請參閱本主題稍後的＜ [後續操作：設定次要複本的備份之後](#FollowUp) ＞。</span><span class="sxs-lookup"><span data-stu-id="eed10-195">For more information, see [Follow Up: After Configuring Backup on Secondary Replicas](#FollowUp) later in this topic.</span></span>  
  
     <span data-ttu-id="eed10-196">例如，下列命令會將可用性群組 `MyAg` 的 `AutomatedBackupPreference` 屬性設定為 `SecondaryOnly`。</span><span class="sxs-lookup"><span data-stu-id="eed10-196">For example, the following command sets the `AutomatedBackupPreference` property on the availability group `MyAg` to `SecondaryOnly`.</span></span> <span data-ttu-id="eed10-197">這個可用性群組中資料庫的自動備份永遠不會在主要複本上進行，但是會重新導向至備份優先權設定最高的次要複本。</span><span class="sxs-lookup"><span data-stu-id="eed10-197">Automated backups of databases in this availability group will never occur on the primary replica, but will be redirected to the secondary replica with the highest backup priority setting.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityGroup -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg `  
     -AutomatedBackupPreference SecondaryOnly  
    ```  
  
> [!NOTE]  
>  <span data-ttu-id="eed10-198">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="eed10-198">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="eed10-199">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="eed10-199">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="eed10-200">若要設定及使用 SQL Server PowerShell 提供者，請參閱[SQL Server PowerShell 提供者](../../../powershell/sql-server-powershell-provider.md)並[取得說明 SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="eed10-200">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md) and [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>
  
##  <a name="follow-up-after-configuring-backup-on-secondary-replicas"></a><a name="FollowUp"></a><span data-ttu-id="eed10-201">後續操作：在次要複本上設定備份之後</span><span class="sxs-lookup"><span data-stu-id="eed10-201">Follow Up: After Configuring Backup on Secondary Replicas</span></span>  
 <span data-ttu-id="eed10-202">若要針對給定可用性群組將自動備份喜好設定納入考量，您必須在備份優先權大於零 (>0) 之裝載可用性複本的每個伺服器執行個體上，針對可用性群組中的資料庫編寫備份作業的指令碼。</span><span class="sxs-lookup"><span data-stu-id="eed10-202">To take the automated backup preference into account for a given availability group, on each server instance that hosts an availability replica whose backup priority is greater than zero (>0), you need to script backup jobs for the databases in the availability group.</span></span> <span data-ttu-id="eed10-203">若要判斷目前的複本是否為慣用的備份複本，請在您的備份指令碼中使用 [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) 函數。</span><span class="sxs-lookup"><span data-stu-id="eed10-203">To determine whether the current replica is the preferred backup replica, use the [sys.fn_hadr_backup_is_preferred_replica](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql) function in your backup script.</span></span> <span data-ttu-id="eed10-204">如果目前伺服器執行個體所裝載的可用性複本是慣用的備份複本，此函數會傳回 1。</span><span class="sxs-lookup"><span data-stu-id="eed10-204">If the availability replica that is hosted by the current server instance is the preferred replica for backups, this function returns 1.</span></span> <span data-ttu-id="eed10-205">如果不是，函數會傳回 0。</span><span class="sxs-lookup"><span data-stu-id="eed10-205">If not, the function returns 0.</span></span> <span data-ttu-id="eed10-206">透過在每個可用性複本上執行簡單的指令碼來查詢這個函數，您就可以判斷哪個複本應該執行給定的備份作業。</span><span class="sxs-lookup"><span data-stu-id="eed10-206">By running a simple script on each availability replica that queries this function, you can determine which replica should run a given backup job.</span></span> <span data-ttu-id="eed10-207">例如，備份作業指令碼的一般程式碼片段看起來可能像是：</span><span class="sxs-lookup"><span data-stu-id="eed10-207">For example, a typical snippet of a backup-job script would look like:</span></span>  
  
```  
IF (NOT sys.fn_hadr_backup_is_preferred_replica(@DBNAME))  
BEGIN  
      Select 'This is not the preferred replica, exiting with success';  
      RETURN 0 - This is a normal, expected condition, so the script returns success  
END  
BACKUP DATABASE @DBNAME TO DISK=<disk>  
   WITH COPY_ONLY;  
```  
  
 <span data-ttu-id="eed10-208">使用這類邏輯編寫備份作業的指令碼，可讓您指定備份作業以相同排程在每個可用性複本上執行。</span><span class="sxs-lookup"><span data-stu-id="eed10-208">Scripting a backup job with this logic enables you to schedule the job to run on every availability replica on the same schedule.</span></span> <span data-ttu-id="eed10-209">每一個作業都會查看相同的資料，以判斷應該執行哪一個作業，如此一來，只有其中一個排程作業會實際進行到備份階段。</span><span class="sxs-lookup"><span data-stu-id="eed10-209">Each of these jobs looks at the same data to determine which job should run, so only one of the scheduled job actually proceeds to the backup stage.</span></span>  <span data-ttu-id="eed10-210">萬一發生容錯移轉，指令碼或作業都不需要修改。</span><span class="sxs-lookup"><span data-stu-id="eed10-210">In the event of a failover, none of the scripts or jobs needs to be modified.</span></span> <span data-ttu-id="eed10-211">此外，如果您重新設定可用性群組以加入可用性複本，備份作業管理只需要複製或排程備份作業。</span><span class="sxs-lookup"><span data-stu-id="eed10-211">Also, if you reconfigure an availability group to add an availability replica, managing the backup job requires simply copying or scheduling the backup job.</span></span> <span data-ttu-id="eed10-212">如果您移除可用性複本，只需從原先裝載該複本的伺服器執行個體刪除備份作業。</span><span class="sxs-lookup"><span data-stu-id="eed10-212">If you remove an availability replica, simply delete the backup job from the server instance that hosted that replica.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="eed10-213">如果您使用[維護計畫精靈](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)來建立指定的備份作業，此作業就會自動包含呼叫並檢查 **sys.fn_hadr_backup_is_preferred_replica** 函數的指令碼邏輯。</span><span class="sxs-lookup"><span data-stu-id="eed10-213">If you use the[Maintenance Plan Wizard](../../../relational-databases/maintenance-plans/use-the-maintenance-plan-wizard.md)to create a given backup job, the job will automatically include the scripting logic that calls and checks the **sys.fn_hadr_backup_is_preferred_replica** function.</span></span> <span data-ttu-id="eed10-214">不過，此備份作業不會傳回「這不是慣用的複本...」訊息。請務必在裝載可用性群組之可用性複本的每一個伺服器執行個體上，為每個可用性資料庫建立作業。</span><span class="sxs-lookup"><span data-stu-id="eed10-214">However, the backup job will not return the "This is not the preferred replica..." message.Be sure to create the job(s) for each availability database on every server instance that hosts an availability replica for the availability group.</span></span>  
  
##  <a name="to-obtain-information-about-backup-preference-settings"></a><a name="ForInfoAboutBuPref"></a><span data-ttu-id="eed10-215">取得備份喜好設定的相關資訊</span><span class="sxs-lookup"><span data-stu-id="eed10-215">To Obtain Information About Backup Preference Settings</span></span>  
 <span data-ttu-id="eed10-216">下列檢視表可用於取得次要備份的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eed10-216">The following are useful for obtaining information that is relevant for backup on secondary.</span></span>  
  
|<span data-ttu-id="eed10-217">檢視</span><span class="sxs-lookup"><span data-stu-id="eed10-217">View</span></span>|<span data-ttu-id="eed10-218">資訊</span><span class="sxs-lookup"><span data-stu-id="eed10-218">Information</span></span>|<span data-ttu-id="eed10-219">相關資料行</span><span class="sxs-lookup"><span data-stu-id="eed10-219">Relevant Columns</span></span>|  
|----------|-----------------|----------------------|  
|[<span data-ttu-id="eed10-220">sys.fn_hadr_backup_is_preferred_replica</span><span class="sxs-lookup"><span data-stu-id="eed10-220">sys.fn_hadr_backup_is_preferred_replica</span></span>](/sql/relational-databases/system-functions/sys-fn-hadr-backup-is-preferred-replica-transact-sql)|<span data-ttu-id="eed10-221">目前的複本是否為慣用的備份複本？</span><span class="sxs-lookup"><span data-stu-id="eed10-221">Is the current replica the preferred backup replica?</span></span>|<span data-ttu-id="eed10-222">不適用。</span><span class="sxs-lookup"><span data-stu-id="eed10-222">Not applicable.</span></span>|  
|[<span data-ttu-id="eed10-223">sys.availability_groups</span><span class="sxs-lookup"><span data-stu-id="eed10-223">sys.availability_groups</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-groups-transact-sql)|<span data-ttu-id="eed10-224">自動備份喜好設定</span><span class="sxs-lookup"><span data-stu-id="eed10-224">Automated backup preference</span></span>|<span data-ttu-id="eed10-225">**automated_backup_preference**</span><span class="sxs-lookup"><span data-stu-id="eed10-225">**automated_backup_preference**</span></span><br /><br /> <span data-ttu-id="eed10-226">**automated_backup_preference_desc**</span><span class="sxs-lookup"><span data-stu-id="eed10-226">**automated_backup_preference_desc**</span></span>|  
|[<span data-ttu-id="eed10-227">sys.availability_replicas</span><span class="sxs-lookup"><span data-stu-id="eed10-227">sys.availability_replicas</span></span>](/sql/relational-databases/system-catalog-views/sys-availability-replicas-transact-sql)|<span data-ttu-id="eed10-228">給定可用性複本的備份優先權</span><span class="sxs-lookup"><span data-stu-id="eed10-228">Backup priority of a given availability replica</span></span>|<span data-ttu-id="eed10-229">**backup_priority**</span><span class="sxs-lookup"><span data-stu-id="eed10-229">**backup_priority**</span></span>|  
|[<span data-ttu-id="eed10-230">sys.dm_hadr_availability_replica_states</span><span class="sxs-lookup"><span data-stu-id="eed10-230">sys.dm_hadr_availability_replica_states</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-hadr-availability-replica-states-transact-sql)|<span data-ttu-id="eed10-231">複本是否為伺服器執行個體的本機複本？</span><span class="sxs-lookup"><span data-stu-id="eed10-231">Is replica local to the server instance?</span></span><br /><br /> <span data-ttu-id="eed10-232">目前的角色</span><span class="sxs-lookup"><span data-stu-id="eed10-232">Current role</span></span><br /><br /> <span data-ttu-id="eed10-233">操作狀態</span><span class="sxs-lookup"><span data-stu-id="eed10-233">Operational state</span></span><br /><br /> <span data-ttu-id="eed10-234">連接狀態</span><span class="sxs-lookup"><span data-stu-id="eed10-234">Connected state</span></span><br /><br /> <span data-ttu-id="eed10-235">可用性複本的同步處理健全狀況</span><span class="sxs-lookup"><span data-stu-id="eed10-235">Synchronization health of an availability replica</span></span>|<span data-ttu-id="eed10-236">**is_local**</span><span class="sxs-lookup"><span data-stu-id="eed10-236">**is_local**</span></span><br /><br /> <span data-ttu-id="eed10-237">**role**、 **role_desc**</span><span class="sxs-lookup"><span data-stu-id="eed10-237">**role**, **role_desc**</span></span><br /><br /> <span data-ttu-id="eed10-238">**operational_state**、 **operational_state_desc**</span><span class="sxs-lookup"><span data-stu-id="eed10-238">**operational_state**, **operational_state_desc**</span></span><br /><br /> <span data-ttu-id="eed10-239">**connected_state**、 **connected_state_desc**</span><span class="sxs-lookup"><span data-stu-id="eed10-239">**connected_state**, **connected_state_desc**</span></span><br /><br /> <span data-ttu-id="eed10-240">**synchronization_health**、 **synchronization_health_desc**</span><span class="sxs-lookup"><span data-stu-id="eed10-240">**synchronization_health**, **synchronization_health_desc**</span></span>|  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="eed10-241">相關內容</span><span class="sxs-lookup"><span data-stu-id="eed10-241">Related Content</span></span>  
  
-   [<span data-ttu-id="eed10-242">Microsoft SQL Server AlwaysOn 高可用性和災害復原方案指南</span><span class="sxs-lookup"><span data-stu-id="eed10-242">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
-   [<span data-ttu-id="eed10-243">SQL Server AlwaysOn 團隊部落格：官方 SQL Server AlwaysOn 團隊部落格</span><span class="sxs-lookup"><span data-stu-id="eed10-243">SQL Server AlwaysOn Team Blog: The official SQL Server AlwaysOn Team Blog</span></span>](https://blogs.msdn.com/b/sqlalwayson/)  
  
## <a name="see-also"></a><span data-ttu-id="eed10-244">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eed10-244">See Also</span></span>  
 <span data-ttu-id="eed10-245">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="eed10-245">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="eed10-246">使用中次要：在次要複本上備份 (AlwaysOn 可用性群組)</span><span class="sxs-lookup"><span data-stu-id="eed10-246">Active Secondaries: Backup on Secondary Replicas (AlwaysOn Availability Groups)</span></span>](active-secondaries-backup-on-secondary-replicas-always-on-availability-groups.md) 
