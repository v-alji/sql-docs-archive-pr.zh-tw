---
title: 使用新增可用性群組對話方塊 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], creating
ms.assetid: 1b0a6421-fbd4-4bb4-87ca-657f4782c433
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 811710051089dfeb402e59bf1b7f45d05c84d925
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594185"
---
# <a name="use-the-new-availability-group-dialog-box-sql-server-management-studio"></a><span data-ttu-id="18f47-102">使用新增可用性群組對話方塊 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="18f47-102">Use the New Availability Group Dialog Box (SQL Server Management Studio)</span></span>
  <span data-ttu-id="18f47-103">此主題描述如何使用 **的** [新增可用性群組] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 對話方塊，在已啟用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 功能的 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]執行個體建立 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="18f47-103">This topic contains information about how to use the **New Availability Group** dialog box of [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to create an AlwaysOn availability group on instances of [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] that are enabled for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="18f47-104">*「可用性群組」* (Availability Group) 會定義當做單一單位容錯移轉的一組使用者資料庫，以及支援容錯移轉的一組容錯移轉夥伴 (也稱為 *「可用性複本」* (Availability Replica))。</span><span class="sxs-lookup"><span data-stu-id="18f47-104">An *availability group* defines a set of user databases that will fail over as a single unit and a set of failover partners, known as *availability replicas*, that support failover.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="18f47-105">如需可用性群組的簡介，請參閱 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="18f47-105">For an introduction to availability groups, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  

> [!NOTE]  
>  <span data-ttu-id="18f47-106">如需建立可用性群組之其他方法的相關資訊，請參閱本主題稍後的 [相關工作](#RelatedTasks)。</span><span class="sxs-lookup"><span data-stu-id="18f47-106">For information about alternative ways to create an availability group, see [Related Tasks](#RelatedTasks), later in this topic.</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="18f47-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="18f47-107">Before You Begin</span></span>  
 <span data-ttu-id="18f47-108">我們強烈建議您先閱讀本節內容，然後再嘗試建立您的第一個可用性群組。</span><span class="sxs-lookup"><span data-stu-id="18f47-108">We strongly recommend that you read this section before attempting to create your first availability group.</span></span>  
  
###  <a name="prerequisites"></a><a name="PrerequisitesRestrictions"></a> <span data-ttu-id="18f47-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="18f47-109">Prerequisites</span></span>  
  
-   <span data-ttu-id="18f47-110">建立可用性群組之前，請確認裝載可用性複本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體位於相同 Windows Server 容錯移轉叢集 (WSFC) 容錯移轉叢集的不同 WSFC 節點上。</span><span class="sxs-lookup"><span data-stu-id="18f47-110">Before creating an availability group, verify that the instances of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that host availability replicas reside on different Windows Server Failover Clustering (WSFC) node within the same WSFC failover cluster.</span></span> <span data-ttu-id="18f47-111">也請確認每個伺服器執行個體都已啟用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 且符合所有其他 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 必要條件。</span><span class="sxs-lookup"><span data-stu-id="18f47-111">Also, verify that each of the server instance is enabled for [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] and meets all other [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] prerequisites.</span></span> <span data-ttu-id="18f47-112">如需詳細資訊，強烈建議您閱讀 [AlwaysOn 可用性群組的必要條件、限制和建議 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="18f47-112">For more information, we strongly recommend that you read [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
-   <span data-ttu-id="18f47-113">在建立可用性群組之前，請確定將要裝載可用性複本的每個伺服器執行個體都擁有可完全運作的資料庫鏡像端點。</span><span class="sxs-lookup"><span data-stu-id="18f47-113">Before you create an availability group, ensure that every server instance that will host an availability replica has a fully functioning database mirroring endpoint.</span></span> <span data-ttu-id="18f47-114">如需詳細資訊，請參閱 [資料庫鏡像端點 &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="18f47-114">For more information, see [The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md).</span></span>  
  
-   <span data-ttu-id="18f47-115">若要使用 **[新增可用性群組]** 對話方塊，您需要知道將要裝載可用性複本的伺服器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="18f47-115">To use the **New Availability Group** dialog box, you need to know the names of the server instances that will host availability replicas.</span></span> <span data-ttu-id="18f47-116">您也需要知道要新增至新可用性群組的任何資料庫名稱，而且需要確定這些資料庫符合 [AlwaysOn 可用性群組的必要條件、限制和建議 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md) 中所述的可用性資料庫必要條件和限制。</span><span class="sxs-lookup"><span data-stu-id="18f47-116">Also, you need know the names of any databases that you intend to add to your new availability group, and you need to ensure that these databases meet the availability database prerequisites and restrictions described in [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span> <span data-ttu-id="18f47-117">如果您輸入無效值，新的可用性群組將無法運作。</span><span class="sxs-lookup"><span data-stu-id="18f47-117">If you enter invalid values, the new availability group will not work.</span></span>  
  
###  <a name="limitations"></a><a name="Limitations"></a> <span data-ttu-id="18f47-118">限制</span><span class="sxs-lookup"><span data-stu-id="18f47-118">Limitations</span></span>  
 <span data-ttu-id="18f47-119">**[新增可用性群組]** 對話方塊不會：</span><span class="sxs-lookup"><span data-stu-id="18f47-119">The **New Availability Group** dialog box does not:</span></span>  
  
-   <span data-ttu-id="18f47-120">建立可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="18f47-120">Create an availability group listener.</span></span>  
  
-   <span data-ttu-id="18f47-121">將次要複本聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="18f47-121">Join secondary replicas to the availability group.</span></span>  
  
-   <span data-ttu-id="18f47-122">執行初始資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="18f47-122">Perform initial data synchronization.</span></span>  
  
 <span data-ttu-id="18f47-123">如需這些設定工作的相關資訊，請參閱本主題稍後的＜[後續操作：建立可用性群組之後](#FollowUp)＞。</span><span class="sxs-lookup"><span data-stu-id="18f47-123">For information about these configuration tasks, see [Follow Up: After Creating an Availability Group](#FollowUp), later in this topic.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="18f47-124">Security</span><span class="sxs-lookup"><span data-stu-id="18f47-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="18f47-125">權限</span><span class="sxs-lookup"><span data-stu-id="18f47-125">Permissions</span></span>  
 <span data-ttu-id="18f47-126">需要 **系統管理員 (sysadmin)** 固定伺服器角色的成員資格，以及 CREATE AVAILABILITY GROUP 伺服器權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="18f47-126">Requires membership in the **sysadmin** fixed server role and either CREATE AVAILABILITY GROUP server permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-the-new-availability-group-dialog-box-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="18f47-127">使用新增可用性群組對話方塊 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="18f47-127">Using the New Availability Group Dialog Box (SQL Server Management Studio)</span></span>  
 <span data-ttu-id="18f47-128">**建立可用性群組**</span><span class="sxs-lookup"><span data-stu-id="18f47-128">**To create an availability group**</span></span>  
  
1.  <span data-ttu-id="18f47-129">在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，然後按一下伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="18f47-129">In Object Explorer, connect to the server instance that hosts the primary replica, and click the server name.</span></span>  
  
2.  <span data-ttu-id="18f47-130">展開 **[AlwaysOn 高可用性]** 節點。</span><span class="sxs-lookup"><span data-stu-id="18f47-130">Expand the **AlwaysOn High Availability** node.</span></span>  
  
3.  <span data-ttu-id="18f47-131">以滑鼠右鍵按一下 [可用性群組] 節點，然後選取 [新增可用性群組] 命令。</span><span class="sxs-lookup"><span data-stu-id="18f47-131">Right-click the **Availability Groups** node, and select the **New Availability Group** command.</span></span>  
  
4.  <span data-ttu-id="18f47-132">這個命令會開啟 **[新增可用性群組]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="18f47-132">This command opens up the **New Availability Group** dialog box.</span></span>  
  
5.  <span data-ttu-id="18f47-133">在 **[一般]** 頁面上，使用 **[可用性群組名稱]** 欄位輸入新可用性群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="18f47-133">On the **General** page, use the **Availability group name** field to enter a name for the new availability group.</span></span> <span data-ttu-id="18f47-134">這個名稱必須是有效的 SQL Server 識別碼，而且在 WSFC 叢集的所有可用性群組中是唯一的。</span><span class="sxs-lookup"><span data-stu-id="18f47-134">This name must be a valid SQL Server identifier that is unique across all availability groups in the WSFC cluster.</span></span> <span data-ttu-id="18f47-135">可用性群組名稱的最大長度為 128 個字元。</span><span class="sxs-lookup"><span data-stu-id="18f47-135">The maximum length for an availability group name is 128 characters.</span></span>  
  
6.  <span data-ttu-id="18f47-136">在 **[可用性資料庫]** 方格中，按一下 **[加入]** 並輸入要屬於此可用性群組的本機資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="18f47-136">In the **Availability Databases** grid, click **Add** and enter the name of a local database that you want to belong to this availability group.</span></span> <span data-ttu-id="18f47-137">為每個要加入的資料庫重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="18f47-137">Repeat this for every database to be added.</span></span> <span data-ttu-id="18f47-138">當您按一下 **[確定]** 時，對話方塊會驗證指定的資料庫是否符合屬於可用性群組的必要條件。</span><span class="sxs-lookup"><span data-stu-id="18f47-138">When you click **OK**, the dialog will verify whether your specified database meet the prerequisites for belonging to an availability group.</span></span> <span data-ttu-id="18f47-139">如需這些必要條件的相關資訊，請參閱 [AlwaysOn 可用性群組的必要條件、限制和建議 &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="18f47-139">For information about these prerequisites, see [Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-restrictions-recommendations-always-on-availability.md).</span></span>  
  
7.  <span data-ttu-id="18f47-140">在 **[可用性資料庫]** 方格中，按一下 **[加入]** 並輸入要裝載次要複本的伺服器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="18f47-140">In the **Availability Databases** grid, click **Add** and enter the name of a server instance to host a secondary replica.</span></span> <span data-ttu-id="18f47-141">此對話方塊不會嘗試連接到這些執行個體。</span><span class="sxs-lookup"><span data-stu-id="18f47-141">The dialog will not attempt to connect to these instances.</span></span> <span data-ttu-id="18f47-142">如果您指定不正確的伺服器名稱，次要複本會加入但無法連接。</span><span class="sxs-lookup"><span data-stu-id="18f47-142">If you specify an incorrect server name, a secondary replica will be added but you will be unable to connect to that replica.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="18f47-143">如果您已經加入複本，但無法連接到主機伺服器執行個體，則可以移除該複本並加入新複本。</span><span class="sxs-lookup"><span data-stu-id="18f47-143">If you have added a replica and cannot connect to the host server instance, you can remove the replica and add a new one.</span></span> <span data-ttu-id="18f47-144">如需詳細資訊，請參閱[將次要複本從可用性群組移除 &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md) 和[將次要複本加入至可用性群組 &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="18f47-144">For more information, see [Remove a Secondary Replica from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-replica-from-an-availability-group-sql-server.md) and [Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
8.  <span data-ttu-id="18f47-145">在對話方塊的 **[選取頁面]** 窗格上，按一下 **[備份喜好設定]** 。</span><span class="sxs-lookup"><span data-stu-id="18f47-145">On the **Select a page** pane of the dialog box, click **Backup Preferences**.</span></span> <span data-ttu-id="18f47-146">然後在 **[備份喜好設定]** 頁面上，根據複本角色指定應該進行備份的位置，並為將要裝載此可用性群組之可用性複本的每個伺服器執行個體指派備份優先權。</span><span class="sxs-lookup"><span data-stu-id="18f47-146">Then, on the **Backup Preferences** page, specify where backups should occur based on replica role and assign backup priorities to each server instances that will host an availability replica for this availability group.</span></span> <span data-ttu-id="18f47-147">如需詳細資訊，請參閱[可用性群組屬性：新增可用性群組 &#40;備份喜好設定頁面&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md)。</span><span class="sxs-lookup"><span data-stu-id="18f47-147">For more information, see [Availability Group Properties: New Availability Group &#40;Backup Preferences Page&#41;](availability-group-properties-new-availability-group-backup-preferences-page.md).</span></span>  
  
9. <span data-ttu-id="18f47-148">若要建立可用性群組，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="18f47-148">To create the availability group, click **OK**.</span></span> <span data-ttu-id="18f47-149">這會導致對話方塊驗證該指定的資料庫是否符合必要條件。</span><span class="sxs-lookup"><span data-stu-id="18f47-149">This causes the dialog to verify whether that specified databases meet the prerequisites.</span></span>  
  
     <span data-ttu-id="18f47-150">若要結束對話方塊而不建立可用性群組，請按一下 **[取消]** 。</span><span class="sxs-lookup"><span data-stu-id="18f47-150">To exit the dialog box without creating the availability group, click **Cancel**.</span></span>  
  
##  <a name="follow-up-after-using-the-new-availability-group-dialog-box-to-create-an-availability-group"></a><a name="FollowUp"></a> <span data-ttu-id="18f47-151">後續操作：使用 [新增可用性群組] 對話方塊建立可用性群組之後</span><span class="sxs-lookup"><span data-stu-id="18f47-151">Follow Up: After Using the New Availability Group Dialog Box to Create an Availability Group</span></span>  
  
-   <span data-ttu-id="18f47-152">接著您需要連接到裝載此可用性群組之次要複本的每個伺服器執行個體，並完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="18f47-152">You will need to connect, in turn, to each server instance that is hosting a secondary replica for the availability group and complete the following steps:</span></span>  
  
    1.  <span data-ttu-id="18f47-153">將次要複本聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="18f47-153">Join the secondary replica to the availability group.</span></span> <span data-ttu-id="18f47-154">如需詳細資訊，請參閱 [將次要複本聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="18f47-154">For more information, see [Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;](join-a-secondary-replica-to-an-availability-group-sql-server.md).</span></span>  
  
    2.  <span data-ttu-id="18f47-155">還原每個主要資料庫及其交易記錄的目前備份 (使用 RESTORE WITH NORECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="18f47-155">Restore current backups of each primary database and its transaction log (using RESTORE WITH NORECOVERY).</span></span> <span data-ttu-id="18f47-156">如需詳細資訊，請參閱 [針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)中的 PowerShell，將次要資料庫聯結至 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="18f47-156">For more information, see [Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md).</span></span>  
  
    3.  <span data-ttu-id="18f47-157">立即將每個新備妥的次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="18f47-157">Immediately join each newly prepared secondary database to the availability group.</span></span> <span data-ttu-id="18f47-158">如需詳細資訊，請參閱 [將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="18f47-158">For more information, see [Join a Secondary Database to an Availability Group &#40;SQL Server&#41;](join-a-secondary-database-to-an-availability-group-sql-server.md).</span></span>  
  
-   <span data-ttu-id="18f47-159">建議您為新可用性群組建立可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="18f47-159">We recommend that you create an availability group listener for the new availability group.</span></span> <span data-ttu-id="18f47-160">這需要您連接到裝載目前主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="18f47-160">This requires that you be connected to the server instance that hosts the current primary replica.</span></span> <span data-ttu-id="18f47-161">如需詳細資訊，請參閱 [建立或設定可用性群組接聽程式 &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="18f47-161">For more information, see [Create or Configure an Availability Group Listener &#40;SQL Server&#41;](create-or-configure-an-availability-group-listener-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="18f47-162">相關工作</span><span class="sxs-lookup"><span data-stu-id="18f47-162">Related Tasks</span></span>  
 <span data-ttu-id="18f47-163">**若要設定可用性群組和複本屬性**</span><span class="sxs-lookup"><span data-stu-id="18f47-163">**To configure availability group and replica properties**</span></span>  
  
-   [<span data-ttu-id="18f47-164">變更可用性複本的可用性模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-164">Change the Availability Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-availability-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="18f47-165">變更可用性複本的容錯移轉模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-165">Change the Failover Mode of an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-failover-mode-of-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="18f47-166">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-166">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
-   [<span data-ttu-id="18f47-167">設定彈性容錯移轉原則以控制自動容錯移轉的條件 (AlwaysOn 可用性群組)</span><span class="sxs-lookup"><span data-stu-id="18f47-167">Configure the Flexible Failover Policy to Control Conditions for Automatic Failover (AlwaysOn Availability Groups)</span></span>](configure-flexible-automatic-failover-policy.md)  
  
-   [<span data-ttu-id="18f47-168">在新增或修改可用性複本時指定端點 URL &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-168">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
-   [<span data-ttu-id="18f47-169">設定可用性複本的備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-169">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
-   [<span data-ttu-id="18f47-170">設定可用性複本的唯讀存取 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-170">Configure Read-Only Access on an Availability Replica &#40;SQL Server&#41;</span></span>](configure-read-only-access-on-an-availability-replica-sql-server.md)  
  
-   [<span data-ttu-id="18f47-171">設定可用性群組的唯讀路由 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-171">Configure Read-Only Routing for an Availability Group &#40;SQL Server&#41;</span></span>](configure-read-only-routing-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="18f47-172">變更可用性複本的工作階段逾時期限 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-172">Change the Session-Timeout Period for an Availability Replica &#40;SQL Server&#41;</span></span>](change-the-session-timeout-period-for-an-availability-replica-sql-server.md)  
  
 <span data-ttu-id="18f47-173">**若要完成可用性群組組態**</span><span class="sxs-lookup"><span data-stu-id="18f47-173">**To complete availability group configuration**</span></span>  
  
-   [<span data-ttu-id="18f47-174">將次要複本聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-174">Join a Secondary Replica to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-replica-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="18f47-175">針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-175">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="18f47-176">將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-176">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="18f47-177">建立或設定可用性群組接聽程式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-177">Create or Configure an Availability Group Listener &#40;SQL Server&#41;</span></span>](create-or-configure-an-availability-group-listener-sql-server.md)  
  
 <span data-ttu-id="18f47-178">**建立可用性群組的其他方法**</span><span class="sxs-lookup"><span data-stu-id="18f47-178">**Alternative ways to create an availability group**</span></span>  
  
-   [<span data-ttu-id="18f47-179">使用可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-179">Use the Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="18f47-180">建立可用性群組 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-180">Create an Availability Group &#40;Transact-SQL&#41;</span></span>](create-an-availability-group-transact-sql.md)  
  
-   [<span data-ttu-id="18f47-181">建立可用性群組 &#40;SQL Server PowerShell&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-181">Create an Availability Group &#40;SQL Server PowerShell&#41;</span></span>](../../../powershell/sql-server-powershell.md)  
  
 <span data-ttu-id="18f47-182">**若要啟用 AlwaysOn 可用性群組**</span><span class="sxs-lookup"><span data-stu-id="18f47-182">**To enable AlwaysOn Availability Groups**</span></span>  
  
-   [<span data-ttu-id="18f47-183">啟用和停用 AlwaysOn 可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-183">Enable and Disable AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](enable-and-disable-always-on-availability-groups-sql-server.md)  
  
 <span data-ttu-id="18f47-184">**若要設定資料庫鏡像端點**</span><span class="sxs-lookup"><span data-stu-id="18f47-184">**To configure a database mirroring endpoint**</span></span>  
  
-   [<span data-ttu-id="18f47-185">建立 AlwaysOn 可用性群組 &#40;SQL Server PowerShell 的資料庫鏡像端點&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-185">Create a Database Mirroring Endpoint for AlwaysOn Availability Groups &#40;SQL Server PowerShell&#41;</span></span>](database-mirroring-always-on-availability-groups-powershell.md)  
  
-   [<span data-ttu-id="18f47-186">建立 Windows 驗證的資料庫鏡像端點 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-186">Create a Database Mirroring Endpoint for Windows Authentication &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/create-a-database-mirroring-endpoint-for-windows-authentication-transact-sql.md)  
  
-   [<span data-ttu-id="18f47-187">使用資料庫鏡像端點憑證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-187">Use Certificates for a Database Mirroring Endpoint &#40;Transact-SQL&#41;</span></span>](../../database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql.md)  
  
-   [<span data-ttu-id="18f47-188">在新增或修改可用性複本時指定端點 URL &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-188">Specify the Endpoint URL When Adding or Modifying an Availability Replica &#40;SQL Server&#41;</span></span>](specify-endpoint-url-adding-or-modifying-availability-replica.md)  
  
 <span data-ttu-id="18f47-189">**若要疑難排解 AlwaysOn 可用性群組組態**</span><span class="sxs-lookup"><span data-stu-id="18f47-189">**To troubleshoot AlwaysOn Availability Groups configuration**</span></span>  
  
-   [<span data-ttu-id="18f47-190">針對 AlwaysOn 可用性群組 Configuration (SQL Server) 已刪除進行疑難排解</span><span class="sxs-lookup"><span data-stu-id="18f47-190">Troubleshoot AlwaysOn Availability Groups Configuration (SQL Server)deleted</span></span>](troubleshoot-always-on-availability-groups-configuration-sql-server.md)  
  
-   [<span data-ttu-id="18f47-191">針對失敗的新增檔案作業進行疑難排解 &#40;AlwaysOn 可用性群組&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-191">Troubleshoot a Failed Add-File Operation &#40;AlwaysOn Availability Groups&#41;</span></span>](troubleshoot-a-failed-add-file-operation-always-on-availability-groups.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="18f47-192">相關內容</span><span class="sxs-lookup"><span data-stu-id="18f47-192">Related Content</span></span>  
  
-   [<span data-ttu-id="18f47-193">Microsoft SQL Server AlwaysOn 高可用性和災害復原方案指南</span><span class="sxs-lookup"><span data-stu-id="18f47-193">Microsoft SQL Server AlwaysOn Solutions Guide for High Availability and Disaster Recovery</span></span>](https://go.microsoft.com/fwlink/?LinkId=227600)  
  
## <a name="see-also"></a><span data-ttu-id="18f47-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="18f47-194">See Also</span></span>  
 <span data-ttu-id="18f47-195">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="18f47-195">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="18f47-196">[資料庫鏡像端點 &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="18f47-196">[The Database Mirroring Endpoint &#40;SQL Server&#41;](../../database-mirroring/the-database-mirroring-endpoint-sql-server.md) </span></span>  
 <span data-ttu-id="18f47-197">[可用性群組接聽程式、用戶端連接性及應用程式容錯移轉 &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span><span class="sxs-lookup"><span data-stu-id="18f47-197">[Availability Group Listeners, Client Connectivity, and Application Failover &#40;SQL Server&#41;](../../listeners-client-connectivity-application-failover.md) </span></span>  
 [<span data-ttu-id="18f47-198">AlwaysOn 可用性群組 &#40;SQL Server 的必要條件、限制和建議&#41;</span><span class="sxs-lookup"><span data-stu-id="18f47-198">Prerequisites, Restrictions, and Recommendations for AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-restrictions-recommendations-always-on-availability.md)  
