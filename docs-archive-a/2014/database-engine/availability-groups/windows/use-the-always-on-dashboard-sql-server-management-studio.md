---
title: 使用 AlwaysOn 儀表板 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.agdashboard.f1
helpviewer_keywords:
- Availability Groups [SQL Server], policies
- Availability Groups [SQL Server], dashboard
ms.assetid: c9ba2589-139e-42bc-99e1-94546717c64d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c4ce0072bcd6642dcb4f3ac63e04c98786bd550e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593595"
---
# <a name="use-the-alwayson-dashboard-sql-server-management-studio"></a><span data-ttu-id="69ef4-102">Use the AlwaysOn Dashboard (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="69ef4-102">Use the AlwaysOn Dashboard (SQL Server Management Studio)</span></span>
  <span data-ttu-id="69ef4-103">資料庫管理員可以使用 AlwaysOn 儀表板，在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中取得 AlwaysOn 可用性群組及其可用性複本和資料庫的健全狀況摘要檢視。</span><span class="sxs-lookup"><span data-stu-id="69ef4-103">Database administrators use the AlwaysOn Dashboard to obtains an at-a-glance view the health of an AlwaysOn availability group and its availability replicas and databases in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="69ef4-104">AlwaysOn 儀表板的部分一般用法包括：</span><span class="sxs-lookup"><span data-stu-id="69ef4-104">Some of the typical uses for the AlwaysOn Dashboard are:</span></span>  
  
-   <span data-ttu-id="69ef4-105">選擇手動容錯移轉的複本。</span><span class="sxs-lookup"><span data-stu-id="69ef4-105">Choosing a replica for a manual failover.</span></span>  
  
-   <span data-ttu-id="69ef4-106">估計資料遺失 (如果您強制容錯移轉的話)。</span><span class="sxs-lookup"><span data-stu-id="69ef4-106">Estimating data loss if you force failover.</span></span>  
  
-   <span data-ttu-id="69ef4-107">評估資料同步處理效能。</span><span class="sxs-lookup"><span data-stu-id="69ef4-107">Evaluating data-synchronization performance.</span></span>  
  
-   <span data-ttu-id="69ef4-108">評估同步認可次要複本的效能影響。</span><span class="sxs-lookup"><span data-stu-id="69ef4-108">Evaluating the performance impact of a synchronous-commit secondary replica</span></span>  
  
 <span data-ttu-id="69ef4-109">AlwaysOn 儀表板提供了一些重要的可用性群組狀態和效能指標，可讓您輕鬆地使用下列資訊類型進行高可用性作業決策。</span><span class="sxs-lookup"><span data-stu-id="69ef4-109">The AlwaysOn Dashboard provides key availability group states and performance indicators allowing you to easily make high availability operational decisions using the following types of information.</span></span>  
  
-   <span data-ttu-id="69ef4-110">複本積存狀態</span><span class="sxs-lookup"><span data-stu-id="69ef4-110">Replica roll-up state</span></span>  
  
-   <span data-ttu-id="69ef4-111">同步處理模式和狀態</span><span class="sxs-lookup"><span data-stu-id="69ef4-111">Synchronization mode and state</span></span>  
  
-   <span data-ttu-id="69ef4-112">預估資料遺失</span><span class="sxs-lookup"><span data-stu-id="69ef4-112">Estimate Data Loss</span></span>  
  
-   <span data-ttu-id="69ef4-113">預估復原時間 (重做趕上)</span><span class="sxs-lookup"><span data-stu-id="69ef4-113">Estimated Recovery Time (redo catch up)</span></span>  
  
-   <span data-ttu-id="69ef4-114">資料庫複本詳細資料</span><span class="sxs-lookup"><span data-stu-id="69ef4-114">Database Replica details</span></span>  
  
-   <span data-ttu-id="69ef4-115">同步處理模式和狀態</span><span class="sxs-lookup"><span data-stu-id="69ef4-115">Synchronization mode and state</span></span>  
  
-   <span data-ttu-id="69ef4-116">還原記錄的時間</span><span class="sxs-lookup"><span data-stu-id="69ef4-116">Time to restore log</span></span>  
  
 
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="69ef4-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="69ef4-117">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="69ef4-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="69ef4-118">Prerequisites</span></span>  
 <span data-ttu-id="69ef4-119">您必須連接到裝載可用性群組之主要複本或次要複本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體 (伺服器執行個體)。</span><span class="sxs-lookup"><span data-stu-id="69ef4-119">You must be connected to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (server instance) that hosts either the primary replica or a secondary replica of an availability group.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="69ef4-120">Security</span><span class="sxs-lookup"><span data-stu-id="69ef4-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="69ef4-121">權限</span><span class="sxs-lookup"><span data-stu-id="69ef4-121">Permissions</span></span>  
 <span data-ttu-id="69ef4-122">需要 CONNECT、VIEW SERVER STATE 和 VIEW ANY DEFINITION 權限。</span><span class="sxs-lookup"><span data-stu-id="69ef4-122">Requires CONNECT, VIEW SERVER STATE, and VIEW ANY DEFINITION permissions.</span></span>  
  
##  <a name="to-start-the-alwayson-dashboard"></a><a name="SSMSProcedure"></a><span data-ttu-id="69ef4-123">啟動 AlwaysOn 儀表板</span><span class="sxs-lookup"><span data-stu-id="69ef4-123">To start the AlwaysOn Dashboard</span></span>  
  
1.  <span data-ttu-id="69ef4-124">在 [物件總管] 中，連接到您想要執行 AlwaysOn 儀表板的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="69ef4-124">In Object Explorer, connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on which you want to run the AlwaysOn Dashboard.</span></span>  
  
2.  <span data-ttu-id="69ef4-125">展開 **[AlwaysOn 高可用性]** 節點、以滑鼠右鍵按一下 **[可用性群組]** 節點，然後按一下 **[顯示儀表板]**。</span><span class="sxs-lookup"><span data-stu-id="69ef4-125">Expand the **AlwaysOn High Availability** node, right-click the **Availability Groups** node, and then click **Show Dashboard**.</span></span>  
  
###  <a name="to-change-alwayson-dashboard-options"></a><a name="DashboardOptions"></a><span data-ttu-id="69ef4-126">變更 AlwaysOn 儀表板選項</span><span class="sxs-lookup"><span data-stu-id="69ef4-126">To Change AlwaysOn Dashboard Options</span></span>  
 <span data-ttu-id="69ef4-127">您可以使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 的 [選項]\*\*\*\* 對話方塊來設定 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn 儀表板行為，以便進行自動重新整理並且啟用自動定義的 AlwaysOn 原則。</span><span class="sxs-lookup"><span data-stu-id="69ef4-127">You can use the [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]**Options** dialog box to configure the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] AlwaysOn Dashboard behavior for automatic refreshing and enabling an auto-defined AlwaysOn policy.</span></span>  
  
1.  <span data-ttu-id="69ef4-128">在 **[工具]** 功能表中，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="69ef4-128">From the **Tools** menu, click **Options**.</span></span>  
  
2.  <span data-ttu-id="69ef4-129">若要自動重新整理儀表板，請在 **[選項]** 對話方塊中，選取 **[開啟自動重新整理]**、輸入重新整理間隔 (以秒為單位)，然後輸入您想要重試連接的次數。</span><span class="sxs-lookup"><span data-stu-id="69ef4-129">To automatically refresh the dashboard, in the **Options** dialog box, select **Turn on automatic refresh**, enter the refresh interval in seconds, and then enter the number of times you want to retry the connection.</span></span>  
  
3.  <span data-ttu-id="69ef4-130">若要啟用使用者定義的原則，請選取 **[啟用使用者定義 AlwaysOn 原則]**。</span><span class="sxs-lookup"><span data-stu-id="69ef4-130">To enable a user-defined policy, select **Enable user-defined AlwaysOn policy**.</span></span>  
  
##  <a name="availability-group-summary"></a><a name="AvGroupsView"></a><span data-ttu-id="69ef4-131">可用性群組摘要</span><span class="sxs-lookup"><span data-stu-id="69ef4-131">Availability Group Summary</span></span>  
 <span data-ttu-id="69ef4-132">可用性群組畫面會針對連接之伺服器執行個體裝載複本的每個可用性群組顯示摘要行。</span><span class="sxs-lookup"><span data-stu-id="69ef4-132">The availability group screen displays a summary line for each availability group for which the connected server instance hosts a replica.</span></span> <span data-ttu-id="69ef4-133">這個窗格會顯示下列資料行。</span><span class="sxs-lookup"><span data-stu-id="69ef4-133">This pane displays the following columns.</span></span>  
  
 <span data-ttu-id="69ef4-134">**可用性組名**</span><span class="sxs-lookup"><span data-stu-id="69ef4-134">**Availability Group Name**</span></span>  
 <span data-ttu-id="69ef4-135">連接之伺服器執行個體裝載複本的可用性群組名稱。</span><span class="sxs-lookup"><span data-stu-id="69ef4-135">The name of an availability group for which the connected server instance hosts a replica.</span></span>  
  
 <span data-ttu-id="69ef4-136">**主要實例**</span><span class="sxs-lookup"><span data-stu-id="69ef4-136">**Primary Instance**</span></span>  
 <span data-ttu-id="69ef4-137">裝載可用性群組之主要複本的伺服器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="69ef4-137">Name of the server instance that is hosting the primary replica of the availability group.</span></span>  
  
 <span data-ttu-id="69ef4-138">**容錯移轉模式**</span><span class="sxs-lookup"><span data-stu-id="69ef4-138">**Failover Mode**</span></span>  
 <span data-ttu-id="69ef4-139">顯示複本所設定的容錯移轉模式。</span><span class="sxs-lookup"><span data-stu-id="69ef4-139">Displays the failover mode for which the replica is configured.</span></span> <span data-ttu-id="69ef4-140">可能的容錯移轉模式值包括：</span><span class="sxs-lookup"><span data-stu-id="69ef4-140">The possible failover mode values are:</span></span>  
  
-   <span data-ttu-id="69ef4-141">**自動**。</span><span class="sxs-lookup"><span data-stu-id="69ef4-141">**Automatic**.</span></span> <span data-ttu-id="69ef4-142">表示一個或多個複本處於自動容錯移轉模式。</span><span class="sxs-lookup"><span data-stu-id="69ef4-142">Indicates that one or more replicas is in automatic-failover mode.</span></span>  
  
-   <span data-ttu-id="69ef4-143">**手動**：</span><span class="sxs-lookup"><span data-stu-id="69ef4-143">**Manual**.</span></span> <span data-ttu-id="69ef4-144">表示沒有任何複本處於自動容錯移轉模式。</span><span class="sxs-lookup"><span data-stu-id="69ef4-144">Indicates that no replica is automatic-failover mode.</span></span>  
  
 <span data-ttu-id="69ef4-145">**問題**</span><span class="sxs-lookup"><span data-stu-id="69ef4-145">**Issues**</span></span>  
 <span data-ttu-id="69ef4-146">按一下 [問題]\*\*\*\* 連結可開啟給定問題的疑難排解文件集。</span><span class="sxs-lookup"><span data-stu-id="69ef4-146">Click the **Issues** link to open troubleshooting documentation for a given issue.</span></span> <span data-ttu-id="69ef4-147">如需所有 AlwaysOn 原則問題的清單，請參閱[AlwaysOn 可用性群組 (SQL Server) 操作問題的 AlwaysOn 原則](always-on-policies-for-operational-issues-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="69ef4-147">For a list of all the AlwaysOn policy issues, see [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="69ef4-148">按一下資料行標題可依照可用性群組、主要執行個體、容錯移轉模式或問題的名稱排序可用性群組資訊。</span><span class="sxs-lookup"><span data-stu-id="69ef4-148">Click the column headings to sort the availability group information by the name of the availability group, primary instance, failover mode, or Issue.</span></span>  
  
##  <a name="availability-group-details"></a><a name="AvGroupDetails"></a> <span data-ttu-id="69ef4-149">可用性群組詳細資料</span><span class="sxs-lookup"><span data-stu-id="69ef4-149">Availability Group Details</span></span>  
 <span data-ttu-id="69ef4-150">系統會針對您從摘要畫面中選取的可用性群組顯示下列詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="69ef4-150">The following detail information is displayed for the availability group that you select from the summary screen:</span></span>  
  
 <span data-ttu-id="69ef4-151">**可用性群組狀態**</span><span class="sxs-lookup"><span data-stu-id="69ef4-151">**Availability group state**</span></span>  
 <span data-ttu-id="69ef4-152">顯示可用性群組的健全狀態。</span><span class="sxs-lookup"><span data-stu-id="69ef4-152">Displays the state of health for the availability group.</span></span>  
  
 <span data-ttu-id="69ef4-153">**Primary instance**</span><span class="sxs-lookup"><span data-stu-id="69ef4-153">**Primary instance**</span></span>  
 <span data-ttu-id="69ef4-154">裝載可用性群組之主要複本的伺服器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="69ef4-154">Name of the server instance that is hosting the primary replica of the availability group.</span></span>  
  
 <span data-ttu-id="69ef4-155">**Failover mode**</span><span class="sxs-lookup"><span data-stu-id="69ef4-155">**Failover mode**</span></span>  
 <span data-ttu-id="69ef4-156">顯示複本所設定的容錯移轉模式。</span><span class="sxs-lookup"><span data-stu-id="69ef4-156">Displays the failover mode for which the replica is configured.</span></span> <span data-ttu-id="69ef4-157">可能的容錯移轉模式值包括：</span><span class="sxs-lookup"><span data-stu-id="69ef4-157">The possible failover mode values are:</span></span>  
  
-   <span data-ttu-id="69ef4-158">**自動**。</span><span class="sxs-lookup"><span data-stu-id="69ef4-158">**Automatic**.</span></span> <span data-ttu-id="69ef4-159">表示一個或多個複本處於自動容錯移轉模式。</span><span class="sxs-lookup"><span data-stu-id="69ef4-159">Indicates that one or more replicas is in automatic-failover mode.</span></span>  
  
-   <span data-ttu-id="69ef4-160">**手動**：</span><span class="sxs-lookup"><span data-stu-id="69ef4-160">**Manual**.</span></span> <span data-ttu-id="69ef4-161">表示沒有任何複本處於自動容錯移轉模式。</span><span class="sxs-lookup"><span data-stu-id="69ef4-161">Indicates that no replica is automatic-failover mode.</span></span>  
  
 <span data-ttu-id="69ef4-162">**叢集狀態**</span><span class="sxs-lookup"><span data-stu-id="69ef4-162">**Cluster state**</span></span>  
 <span data-ttu-id="69ef4-163">連接之伺服器執行個體與可用性群組為成員節點的叢集名稱和狀態。</span><span class="sxs-lookup"><span data-stu-id="69ef4-163">Name and state of the cluster where the instance of the connected server and the availability group is a member node.</span></span>  
  
##  <a name="availability-replica-details"></a><a name="AvReplicaDetails"></a> <span data-ttu-id="69ef4-164">可用性複本詳細資料</span><span class="sxs-lookup"><span data-stu-id="69ef4-164">Availability Replica Details</span></span>  
 <span data-ttu-id="69ef4-165">**[可用性複本]** 窗格會顯示下列資料行：</span><span class="sxs-lookup"><span data-stu-id="69ef4-165">The **Availability replica** pane displays the following columns:</span></span>  
  
 <span data-ttu-id="69ef4-166">**名稱**</span><span class="sxs-lookup"><span data-stu-id="69ef4-166">**Name**</span></span>  
 <span data-ttu-id="69ef4-167">裝載可用性複本的伺服器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="69ef4-167">The name of the server instance that hosts the availability replica.</span></span> <span data-ttu-id="69ef4-168">預設顯示此資料行。</span><span class="sxs-lookup"><span data-stu-id="69ef4-168">This column is shown by default.</span></span>  
  
 <span data-ttu-id="69ef4-169">**角色**</span><span class="sxs-lookup"><span data-stu-id="69ef4-169">**Role**</span></span>  
 <span data-ttu-id="69ef4-170">指出可用性複本的目前角色： **主要** 或 **次要**。</span><span class="sxs-lookup"><span data-stu-id="69ef4-170">Indicates the current role of the availability replica, either **Primary** or **Secondary**.</span></span> <span data-ttu-id="69ef4-171">如需 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 角色的相關資訊，請參閱 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="69ef4-171">For information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] roles, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span> <span data-ttu-id="69ef4-172">預設顯示此資料行。</span><span class="sxs-lookup"><span data-stu-id="69ef4-172">This column is shown by default.</span></span>  
  
 <span data-ttu-id="69ef4-173">**容錯移轉模式**</span><span class="sxs-lookup"><span data-stu-id="69ef4-173">**Failover Mode**</span></span>  
 <span data-ttu-id="69ef4-174">顯示複本所設定的容錯移轉模式。</span><span class="sxs-lookup"><span data-stu-id="69ef4-174">Displays the failover mode for which the replica is configured.</span></span> <span data-ttu-id="69ef4-175">可能的容錯移轉模式值包括：</span><span class="sxs-lookup"><span data-stu-id="69ef4-175">The possible failover mode values are:</span></span>  
  
-   <span data-ttu-id="69ef4-176">**自動**。</span><span class="sxs-lookup"><span data-stu-id="69ef4-176">**Automatic**.</span></span> <span data-ttu-id="69ef4-177">表示一個或多個複本處於自動容錯移轉模式。</span><span class="sxs-lookup"><span data-stu-id="69ef4-177">Indicates that one or more replicas is in automatic-failover mode.</span></span>  
  
-   <span data-ttu-id="69ef4-178">**手動**：</span><span class="sxs-lookup"><span data-stu-id="69ef4-178">**Manual**.</span></span> <span data-ttu-id="69ef4-179">表示沒有任何複本處於自動容錯移轉模式。</span><span class="sxs-lookup"><span data-stu-id="69ef4-179">Indicates that no replica is automatic-failover mode.</span></span>  
  
 <span data-ttu-id="69ef4-180">**同步處理狀態**</span><span class="sxs-lookup"><span data-stu-id="69ef4-180">**Synchronization State**</span></span>  
 <span data-ttu-id="69ef4-181">指出次要複本目前是否與主要複本進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="69ef4-181">Indicates whether a secondary replica is currently synchronized with primary replica.</span></span> <span data-ttu-id="69ef4-182">預設顯示此資料行。</span><span class="sxs-lookup"><span data-stu-id="69ef4-182">This column is shown by default.</span></span> <span data-ttu-id="69ef4-183">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="69ef4-183">The possible values are:</span></span>  
  
-   <span data-ttu-id="69ef4-184">**未同步**處理。</span><span class="sxs-lookup"><span data-stu-id="69ef4-184">**Not Synchronized**.</span></span> <span data-ttu-id="69ef4-185">複本中的一個或多個資料庫尚未同步處理，或者尚未聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="69ef4-185">One or more databases in the replica are not synchronized or have not yet been joined to the availability group.</span></span>  
  
-   <span data-ttu-id="69ef4-186">**正在同步**處理。</span><span class="sxs-lookup"><span data-stu-id="69ef4-186">**Synchronizing**.</span></span> <span data-ttu-id="69ef4-187">正在同步處理複本中的一個或多個資料庫。</span><span class="sxs-lookup"><span data-stu-id="69ef4-187">One or more databases in the replica are being synchronized.</span></span>  
  
-   <span data-ttu-id="69ef4-188">已**同步**處理。</span><span class="sxs-lookup"><span data-stu-id="69ef4-188">**Synchronized**.</span></span> <span data-ttu-id="69ef4-189">次要複本中的所有資料庫都會與目前主要複本上的對應主要資料庫 (如果有的話) 或是最後一個主要複本上的對應主要資料庫進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="69ef4-189">All databases in the secondary replica are synchronized with the corresponding primary databases on the current primary replica, if any, or on the last primary replica.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="69ef4-190">在效能模式中，資料庫永遠不會處於同步處理狀態。</span><span class="sxs-lookup"><span data-stu-id="69ef4-190">In performance mode, the database is never in the synchronized state.</span></span>  
  
-   <span data-ttu-id="69ef4-191">**Null**。</span><span class="sxs-lookup"><span data-stu-id="69ef4-191">**NULL**.</span></span> <span data-ttu-id="69ef4-192">未知的狀態。</span><span class="sxs-lookup"><span data-stu-id="69ef4-192">Unknown state.</span></span> <span data-ttu-id="69ef4-193">當本機伺服器執行個體無法與 WSFC 容錯移轉叢集通訊 (亦即，本機節點不屬於 WSFC 仲裁的一部分) 時，就會出現這個值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-193">This value occurs when the local server instance cannot communicate with the WSFC failover cluster (that is the local node is not part of WSFC quorum).</span></span>  
  
 <span data-ttu-id="69ef4-194">**問題**</span><span class="sxs-lookup"><span data-stu-id="69ef4-194">**Issues**</span></span>  
 <span data-ttu-id="69ef4-195">列出問題名稱。</span><span class="sxs-lookup"><span data-stu-id="69ef4-195">Lists the issue name.</span></span> <span data-ttu-id="69ef4-196">預設顯示此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-196">This value is shown by default.</span></span> <span data-ttu-id="69ef4-197">如需所有 AlwaysOn 原則問題的清單，請參閱[AlwaysOn 可用性群組 (SQL Server) 操作問題的 AlwaysOn 原則](always-on-policies-for-operational-issues-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="69ef4-197">For a list of all the AlwaysOn policy issues, see [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
 <span data-ttu-id="69ef4-198">**可用性模式**</span><span class="sxs-lookup"><span data-stu-id="69ef4-198">**Availability Mode**</span></span>  
 <span data-ttu-id="69ef4-199">指出您個別針對每個可用性複本所設定的複本屬性。</span><span class="sxs-lookup"><span data-stu-id="69ef4-199">Indicates the replica property that you set separately for each availability replica.</span></span> <span data-ttu-id="69ef4-200">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-200">This value is hidden by default.</span></span> <span data-ttu-id="69ef4-201">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="69ef4-201">The possible values are:</span></span>  
  
-   <span data-ttu-id="69ef4-202">**非同步**。</span><span class="sxs-lookup"><span data-stu-id="69ef4-202">**Asynchronous**.</span></span> <span data-ttu-id="69ef4-203">次要複本永遠不會變成與主要複本進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="69ef4-203">The secondary replica never becomes synchronized with the primary replica.</span></span>  
  
-   <span data-ttu-id="69ef4-204">**同步**。</span><span class="sxs-lookup"><span data-stu-id="69ef4-204">**Synchronous**.</span></span> <span data-ttu-id="69ef4-205">趕上主要資料庫時，次要資料庫就會進入此狀態，而且只要資料庫的資料同步處理繼續進行，它就會維持趕上狀態。</span><span class="sxs-lookup"><span data-stu-id="69ef4-205">When catching up to the primary database, a secondary database enters this state, and it remains caught up as long as data synchronization continues for the database.</span></span>  
  
 <span data-ttu-id="69ef4-206">**主要連接模式**</span><span class="sxs-lookup"><span data-stu-id="69ef4-206">**Primary Connection Mode**</span></span>  
 <span data-ttu-id="69ef4-207">指出用來連接到主要複本的模式。</span><span class="sxs-lookup"><span data-stu-id="69ef4-207">Indicates the mode that is used to connect to the primary replica.</span></span>  <span data-ttu-id="69ef4-208">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-208">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-209">**次要連接模式**</span><span class="sxs-lookup"><span data-stu-id="69ef4-209">**Secondary Connection Mode**</span></span>  
 <span data-ttu-id="69ef4-210">指出用來連接到次要複本的模式。</span><span class="sxs-lookup"><span data-stu-id="69ef4-210">Indicates the mode that is used to connect to the secondary replica.</span></span>  <span data-ttu-id="69ef4-211">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-211">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-212">**連接狀態**</span><span class="sxs-lookup"><span data-stu-id="69ef4-212">**Connection State**</span></span>  
 <span data-ttu-id="69ef4-213">指出次要複本目前是否已連接到主要複本。</span><span class="sxs-lookup"><span data-stu-id="69ef4-213">Indicates whether a secondary replica is currently connected to the primary replica.</span></span> <span data-ttu-id="69ef4-214">預設隱藏此資料行。</span><span class="sxs-lookup"><span data-stu-id="69ef4-214">This column is hidden by default.</span></span> <span data-ttu-id="69ef4-215">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="69ef4-215">The possible values are:</span></span>  
  
-   <span data-ttu-id="69ef4-216">已**中斷**連線。</span><span class="sxs-lookup"><span data-stu-id="69ef4-216">**Disconnected**.</span></span> <span data-ttu-id="69ef4-217">若為遠端可用性複本，表示它與本機可用性複本已中斷連接。</span><span class="sxs-lookup"><span data-stu-id="69ef4-217">For a remote availability replica, indicates that it is disconnected from the local availability replica.</span></span> <span data-ttu-id="69ef4-218">本機複本對 [已中斷連接] 狀態的回應取決於其角色，如下所示：</span><span class="sxs-lookup"><span data-stu-id="69ef4-218">The response of the local replica to the Disconnected state depends on its role, as follows:</span></span>  
  
    -   <span data-ttu-id="69ef4-219">在主要複本上，如果次要複本已中斷連接，主要複本上的次要資料庫就會標示為 **[未同步處理]** ，而且主要複本會等候次要複本重新連接。</span><span class="sxs-lookup"><span data-stu-id="69ef4-219">On the primary replica, if a secondary replica is disconnected, the secondary databases are marked as **Not Synchronized** on the primary replica, and the primary replica waits for the secondary to reconnect.</span></span>  
  
    -   <span data-ttu-id="69ef4-220">在次要複本上，一旦偵測到它已中斷連接之後，次要複本就會嘗試重新連接到主要複本。</span><span class="sxs-lookup"><span data-stu-id="69ef4-220">On the secondary replica, upon detecting that it is disconnected, the secondary replica attempts to reconnect to the primary replica.</span></span>  
  
-   <span data-ttu-id="69ef4-221">**已連線**。</span><span class="sxs-lookup"><span data-stu-id="69ef4-221">**Connected**.</span></span> <span data-ttu-id="69ef4-222">目前連接到本機複本的遠端可用性複本。</span><span class="sxs-lookup"><span data-stu-id="69ef4-222">A remote availability replica that is currently connected to the local replica.</span></span>  
  
 <span data-ttu-id="69ef4-223">**操作狀態**</span><span class="sxs-lookup"><span data-stu-id="69ef4-223">**Operational State**</span></span>  
 <span data-ttu-id="69ef4-224">指出次要複本的目前操作狀態。</span><span class="sxs-lookup"><span data-stu-id="69ef4-224">Indicates the current operational state of the secondary replica.</span></span> <span data-ttu-id="69ef4-225">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-225">This value is hidden by default.</span></span> <span data-ttu-id="69ef4-226">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="69ef4-226">The possible values are:</span></span>  
  
 <span data-ttu-id="69ef4-227">**0**.暫止容錯移轉</span><span class="sxs-lookup"><span data-stu-id="69ef4-227">**0**. Pending failover</span></span>  
  
 <span data-ttu-id="69ef4-228">**1**.暫止</span><span class="sxs-lookup"><span data-stu-id="69ef4-228">**1**. Pending</span></span>  
  
 <span data-ttu-id="69ef4-229">**2**.線上存取</span><span class="sxs-lookup"><span data-stu-id="69ef4-229">**2**. Online</span></span>  
  
 <span data-ttu-id="69ef4-230">**3**.離線</span><span class="sxs-lookup"><span data-stu-id="69ef4-230">**3**. Offline</span></span>  
  
 <span data-ttu-id="69ef4-231">**4**.失敗</span><span class="sxs-lookup"><span data-stu-id="69ef4-231">**4**. Failed</span></span>  
  
 <span data-ttu-id="69ef4-232">**5**.失敗，無仲裁</span><span class="sxs-lookup"><span data-stu-id="69ef4-232">**5**. Failed, no quorum</span></span>  
  
 <span data-ttu-id="69ef4-233">**Null**。</span><span class="sxs-lookup"><span data-stu-id="69ef4-233">**NULL**.</span></span> <span data-ttu-id="69ef4-234">複本非本機</span><span class="sxs-lookup"><span data-stu-id="69ef4-234">Replica is not local</span></span>  
  
 <span data-ttu-id="69ef4-235">**上次連接錯誤號碼**</span><span class="sxs-lookup"><span data-stu-id="69ef4-235">**Last Connection Error No.**</span></span>  
 <span data-ttu-id="69ef4-236">上次連接錯誤的號碼。</span><span class="sxs-lookup"><span data-stu-id="69ef4-236">Number of the last connection error.</span></span>  <span data-ttu-id="69ef4-237">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-237">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-238">**上次連接錯誤描述**</span><span class="sxs-lookup"><span data-stu-id="69ef4-238">**Last Connection Error Description**</span></span>  
 <span data-ttu-id="69ef4-239">上次連接錯誤的描述。</span><span class="sxs-lookup"><span data-stu-id="69ef4-239">Description of the last connection error.</span></span>  <span data-ttu-id="69ef4-240">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-240">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-241">**上次連接錯誤時間戳記**</span><span class="sxs-lookup"><span data-stu-id="69ef4-241">**Last Connection Error Timestamp**</span></span>  
 <span data-ttu-id="69ef4-242">上次連接錯誤的時間戳記。</span><span class="sxs-lookup"><span data-stu-id="69ef4-242">Timestamp of the last connection error.</span></span> <span data-ttu-id="69ef4-243">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-243">This value is hidden by default.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69ef4-244">如需可用性複本效能計數器的相關資訊，請參閱 [SQLServer，可用性複本](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)。</span><span class="sxs-lookup"><span data-stu-id="69ef4-244">For information about performance counters for availability replicas, see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
##  <a name="to-group-availability-group-information"></a><a name="AvDbDetails"></a> <span data-ttu-id="69ef4-245">若要將可用性群組資訊分組</span><span class="sxs-lookup"><span data-stu-id="69ef4-245">To Group Availability Group Information</span></span>  
 <span data-ttu-id="69ef4-246">若要將資訊分組，請按一下 **[群組依據]**，然後選取下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="69ef4-246">To group the information, click **Group by**, and select one of the following:</span></span>  
  
-   <span data-ttu-id="69ef4-247">**可用性複本**</span><span class="sxs-lookup"><span data-stu-id="69ef4-247">**Availability replicas**</span></span>  
  
-   <span data-ttu-id="69ef4-248">**可用性資料庫**</span><span class="sxs-lookup"><span data-stu-id="69ef4-248">**Availability databases**</span></span>  
  
-   <span data-ttu-id="69ef4-249">**同步處理狀態**</span><span class="sxs-lookup"><span data-stu-id="69ef4-249">**Synchronization state**</span></span>  
  
-   <span data-ttu-id="69ef4-250">**容錯移轉就緒**</span><span class="sxs-lookup"><span data-stu-id="69ef4-250">**Failover readiness**</span></span>  
  
-   <span data-ttu-id="69ef4-251">**問題**</span><span class="sxs-lookup"><span data-stu-id="69ef4-251">**Issues**</span></span>  
  
 <span data-ttu-id="69ef4-252">顯示群組資訊的窗格會顯示下列資料行：</span><span class="sxs-lookup"><span data-stu-id="69ef4-252">The pane that displays the grouped information displays the following columns:</span></span>  
  
 <span data-ttu-id="69ef4-253">**名稱**</span><span class="sxs-lookup"><span data-stu-id="69ef4-253">**Name**</span></span>  
 <span data-ttu-id="69ef4-254">可用性資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="69ef4-254">The name of the availability database.</span></span> <span data-ttu-id="69ef4-255">預設顯示此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-255">This value is shown by default.</span></span>  
  
 <span data-ttu-id="69ef4-256">**複本**</span><span class="sxs-lookup"><span data-stu-id="69ef4-256">**Replica**</span></span>  
 <span data-ttu-id="69ef4-257">裝載可用性複本之 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="69ef4-257">The name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica.</span></span> <span data-ttu-id="69ef4-258">預設顯示此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-258">This value is shown by default.</span></span>  
  
 <span data-ttu-id="69ef4-259">**同步處理狀態**</span><span class="sxs-lookup"><span data-stu-id="69ef4-259">**Synchronization State**</span></span>  
 <span data-ttu-id="69ef4-260">指出可用性資料庫目前是否與主要複本進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="69ef4-260">Indicates whether the availability database is currently synchronized with primary replica.</span></span> <span data-ttu-id="69ef4-261">預設顯示此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-261">This value is shown by default.</span></span> <span data-ttu-id="69ef4-262">可能的同步處理狀態包括：</span><span class="sxs-lookup"><span data-stu-id="69ef4-262">The possible synchronization states are:</span></span>  
  
-   <span data-ttu-id="69ef4-263">**未進行同步處理**：</span><span class="sxs-lookup"><span data-stu-id="69ef4-263">**Not synchronizing**.</span></span>  
  
    -   <span data-ttu-id="69ef4-264">如果是主要角色，表示資料庫尚未準備好要將其交易記錄與對應的次要資料庫同步處理。</span><span class="sxs-lookup"><span data-stu-id="69ef4-264">For the primary role, indicates that the database is not ready to synchronize its transaction log with the corresponding secondary databases.</span></span>  
  
    -   <span data-ttu-id="69ef4-265">如果是次要資料庫，表示資料庫尚未開始記錄同步處理，原因是因為連接問題、處於暫停狀態，或在啟動或角色切換期間正在移轉狀態。</span><span class="sxs-lookup"><span data-stu-id="69ef4-265">For a secondary database, indicates that the database has not started log synchronization because of a connection issue, is being suspended, or is going through transition states during startup or a role switch.</span></span>  
  
-   <span data-ttu-id="69ef4-266">**正在同步**處理。</span><span class="sxs-lookup"><span data-stu-id="69ef4-266">**Synchronizing**.</span></span>  
  
     <span data-ttu-id="69ef4-267">在主要複本上：</span><span class="sxs-lookup"><span data-stu-id="69ef4-267">On a primary replica:</span></span>  
  
    -   <span data-ttu-id="69ef4-268">如果是主要資料庫，表示此資料庫準備好接受次要資料庫的掃描要求。</span><span class="sxs-lookup"><span data-stu-id="69ef4-268">For a primary database, indicates that this database is ready to accept a scan request from a secondary database.</span></span>  
  
    -   <span data-ttu-id="69ef4-269">在次要複本上，表示該次要資料庫有進行中的資料移動作業。</span><span class="sxs-lookup"><span data-stu-id="69ef4-269">On a secondary replica, indicates that there is active data movement going on for that secondary database.</span></span>  
  
     <span data-ttu-id="69ef4-270">在次要複本上，表示該複本有進行中的資料移動作業。</span><span class="sxs-lookup"><span data-stu-id="69ef4-270">On a secondary replica, indicates that there is active data movement going on for that replica.</span></span>  
  
-   <span data-ttu-id="69ef4-271">已**同步**處理。</span><span class="sxs-lookup"><span data-stu-id="69ef4-271">**Synchronized**.</span></span>  
  
     <span data-ttu-id="69ef4-272">如果是主要資料庫，表示至少已同步處理一個次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="69ef4-272">For a primary database, indicates that at least one secondary database is synchronized.</span></span>  
  
     <span data-ttu-id="69ef4-273">如果是次要資料庫，表示資料庫已與對應的主要資料庫同步處理。</span><span class="sxs-lookup"><span data-stu-id="69ef4-273">For a secondary database, indicates that the database is synchronized with the corresponding primary database.</span></span>  
  
-   <span data-ttu-id="69ef4-274">**正在還原**：</span><span class="sxs-lookup"><span data-stu-id="69ef4-274">**Reverting**.</span></span>  
  
     <span data-ttu-id="69ef4-275">表示當次要資料庫積極取得主要資料庫的頁面時，復原程序中的階段。</span><span class="sxs-lookup"><span data-stu-id="69ef4-275">Indicates the phase in the undo process when a secondary database is actively getting pages from the primary database.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="69ef4-276">當資料庫處於 REVERTING 狀態時，強制容錯移轉至次要複本會將資料庫保留在無法啟動的狀態。</span><span class="sxs-lookup"><span data-stu-id="69ef4-276">When a database is in the REVERTING state, forcing failover to the secondary replica can leave that database in a state in which it cannot be started.</span></span>  
  
-   <span data-ttu-id="69ef4-277">**正在初始化**：</span><span class="sxs-lookup"><span data-stu-id="69ef4-277">**Initializing**.</span></span>  
  
     <span data-ttu-id="69ef4-278">表示次要資料庫跟上復原 LSN 所需的交易記錄正在傳送而且在次要複本上強行寫入時的復原階段。</span><span class="sxs-lookup"><span data-stu-id="69ef4-278">Indicates the phase of undo when the transaction log required for a secondary database to catch up to the undo LSN is being shipped and hardened on a secondary replica.</span></span>  
  
    > [!CAUTION]  
    >  <span data-ttu-id="69ef4-279">當資料庫處於 INITIALIZING 狀態時，強制容錯移轉至次要複本一定會將資料庫保留在無法啟動的狀態。</span><span class="sxs-lookup"><span data-stu-id="69ef4-279">When a database is in the INITIALIZING state, forcing failover to the secondary replica will always leave that database in a state in which it cannot be started.</span></span>  
  
 <span data-ttu-id="69ef4-280">**[容錯移轉整備]**</span><span class="sxs-lookup"><span data-stu-id="69ef4-280">**Failover Readiness**</span></span>  
 <span data-ttu-id="69ef4-281">指出哪個可用性複本可能會在遺失資料或不遺失資料的情況下容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="69ef4-281">Indicates which availability replica can be failed over with or without potential data loss.</span></span> <span data-ttu-id="69ef4-282">預設顯示此資料行。</span><span class="sxs-lookup"><span data-stu-id="69ef4-282">This column is shown by default.</span></span> <span data-ttu-id="69ef4-283">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="69ef4-283">The possible values are:</span></span>  
  
-   <span data-ttu-id="69ef4-284">**資料遺失**</span><span class="sxs-lookup"><span data-stu-id="69ef4-284">**Data Loss**</span></span>  
  
-   <span data-ttu-id="69ef4-285">**不遺失資料**</span><span class="sxs-lookup"><span data-stu-id="69ef4-285">**No Data Loss**</span></span>  
  
 <span data-ttu-id="69ef4-286">**問題**</span><span class="sxs-lookup"><span data-stu-id="69ef4-286">**Issues**</span></span>  
 <span data-ttu-id="69ef4-287">列出問題名稱。</span><span class="sxs-lookup"><span data-stu-id="69ef4-287">Lists the issue name.</span></span> <span data-ttu-id="69ef4-288">預設顯示此資料行。</span><span class="sxs-lookup"><span data-stu-id="69ef4-288">This column is shown by default.</span></span> <span data-ttu-id="69ef4-289">可能的值包括：</span><span class="sxs-lookup"><span data-stu-id="69ef4-289">The possible values are:</span></span>  
  
-   <span data-ttu-id="69ef4-290">**警告**：</span><span class="sxs-lookup"><span data-stu-id="69ef4-290">**Warnings**.</span></span> <span data-ttu-id="69ef4-291">按一下可顯示臨界值和警告問題。</span><span class="sxs-lookup"><span data-stu-id="69ef4-291">Click to display the thresholds and warnings issues.</span></span>  
  
-   <span data-ttu-id="69ef4-292">**關鍵**：</span><span class="sxs-lookup"><span data-stu-id="69ef4-292">**Critical**.</span></span> <span data-ttu-id="69ef4-293">按一下可顯示關鍵問題。</span><span class="sxs-lookup"><span data-stu-id="69ef4-293">Click to display the critical issues.</span></span>  
  
 <span data-ttu-id="69ef4-294">如需所有 AlwaysOn 原則問題的清單，請參閱[AlwaysOn 可用性群組 (SQL Server) 操作問題的 AlwaysOn 原則](always-on-policies-for-operational-issues-always-on-availability.md)。</span><span class="sxs-lookup"><span data-stu-id="69ef4-294">For a list of all the AlwaysOn policy issues, see [AlwaysOn Policies for Operational Issues with AlwaysOn Availability Groups (SQL Server)](always-on-policies-for-operational-issues-always-on-availability.md).</span></span>  
  
 <span data-ttu-id="69ef4-295">**已暫停**</span><span class="sxs-lookup"><span data-stu-id="69ef4-295">**Suspended**</span></span>  
 <span data-ttu-id="69ef4-296">指出資料庫 **[已暫停]** 或 **[已繼續]** 。</span><span class="sxs-lookup"><span data-stu-id="69ef4-296">Indicates whether the database is **Suspended** or has been **Resumed**.</span></span> <span data-ttu-id="69ef4-297">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-297">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-298">**暫停原因**</span><span class="sxs-lookup"><span data-stu-id="69ef4-298">**Suspend Reason**</span></span>  
 <span data-ttu-id="69ef4-299">指出暫停狀態的原因。</span><span class="sxs-lookup"><span data-stu-id="69ef4-299">Indicates the reason for the suspended state.</span></span> <span data-ttu-id="69ef4-300">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-300">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-301">**預估資料遺失 (秒)**</span><span class="sxs-lookup"><span data-stu-id="69ef4-301">**Estimate Data Loss (seconds)**</span></span>  
 <span data-ttu-id="69ef4-302">表示主要複本與次要複本中上一筆交易記錄的時間差異。</span><span class="sxs-lookup"><span data-stu-id="69ef4-302">Indicates the time difference of the last transaction log record in the primary replica and secondary replica.</span></span> <span data-ttu-id="69ef4-303">如果主要複本失敗，則時間視窗內的所有交易記錄都將遺失。</span><span class="sxs-lookup"><span data-stu-id="69ef4-303">If the primary replica fails, all transaction log records within the time window will be lost.</span></span> <span data-ttu-id="69ef4-304">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-304">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-305">**預估復原時間 (秒)**</span><span class="sxs-lookup"><span data-stu-id="69ef4-305">**Estimated Recovery Time (seconds)**</span></span>  
 <span data-ttu-id="69ef4-306">指出重做趕上時間所需要的時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="69ef4-306">Indicates the time in seconds it takes to redo the catch-up time.</span></span> <span data-ttu-id="69ef4-307">*「趕上時間」* (catch-up time) 是指次要複本趕上主要複本所需的時間。</span><span class="sxs-lookup"><span data-stu-id="69ef4-307">The *catch-up time* is the time it will take for the secondary replica to catch up with the primary replica.</span></span> <span data-ttu-id="69ef4-308">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-308">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-309">**同步處理效能 (秒)**</span><span class="sxs-lookup"><span data-stu-id="69ef4-309">**Synchronization Performance (seconds)**</span></span>  
 <span data-ttu-id="69ef4-310">指出在主要與次要複本之間同步處理所需的時間 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="69ef4-310">Indicates the time in seconds it takes to synchronize between the primary and secondary replicas.</span></span> <span data-ttu-id="69ef4-311">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-311">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-312">**記錄檔傳送佇列大小 (KB)**</span><span class="sxs-lookup"><span data-stu-id="69ef4-312">**Log Send Queue Size (KB)**</span></span>  
 <span data-ttu-id="69ef4-313">指出主要資料庫記錄檔中尚未傳送至次要複本的記錄檔記錄數量。</span><span class="sxs-lookup"><span data-stu-id="69ef4-313">Indicates the amount of log records in the log files of the primary database that have not been sent to the secondary replica.</span></span> <span data-ttu-id="69ef4-314">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-314">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-315">**記錄檔傳送速率 (KB/秒)**</span><span class="sxs-lookup"><span data-stu-id="69ef4-315">**Log Send Rate (KB/sec)**</span></span>  
 <span data-ttu-id="69ef4-316">指出將記錄檔記錄傳送到次要複本所使用的速率 (以每秒 KB 數為單位)。預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-316">Indicates the rate in KB per second at which log records are being sent to the secondary replica This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-317">**重做佇列大小 (KB)**</span><span class="sxs-lookup"><span data-stu-id="69ef4-317">**Redo Queue Size (KB)**</span></span>  
 <span data-ttu-id="69ef4-318">指出次要複本記錄檔中尚未重做的記錄檔記錄數量。</span><span class="sxs-lookup"><span data-stu-id="69ef4-318">Indicates the amount of log records in the log files of the secondary replica that have not yet been redone.</span></span> <span data-ttu-id="69ef4-319">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-319">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-320">**重做速率 (KB/秒)**</span><span class="sxs-lookup"><span data-stu-id="69ef4-320">**Redo Rate (KB/sec)**</span></span>  
 <span data-ttu-id="69ef4-321">指出重做記錄檔記錄所使用的速率 (以每秒 KB 數為單位)。</span><span class="sxs-lookup"><span data-stu-id="69ef4-321">Indicates the rate in KB per second at which the log records are being redone.</span></span> <span data-ttu-id="69ef4-322">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-322">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-323">**FileStream 傳送速率 (KB/秒)**</span><span class="sxs-lookup"><span data-stu-id="69ef4-323">**FileStream Send Rate (KB/sec)**</span></span>  
 <span data-ttu-id="69ef4-324">指出將交易傳送到複本所使用的 FileStream 速率 (以每秒 KB 數為單位)。</span><span class="sxs-lookup"><span data-stu-id="69ef4-324">Indicates the rate of the FileStream in KB per second at which transactions are being sent to the replica.</span></span> <span data-ttu-id="69ef4-325">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-325">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-326">**記錄檔結束 LSN**</span><span class="sxs-lookup"><span data-stu-id="69ef4-326">**End of Log LSN**</span></span>  
 <span data-ttu-id="69ef4-327">指出對應到主要和次要複本上記錄檔快取中之上一個記錄檔記錄的實際記錄序號 (LSN)。</span><span class="sxs-lookup"><span data-stu-id="69ef4-327">Indicates the actual log sequence number (LSN) that corresponds to the last log record in the log cache on the primary and secondary replicas.</span></span> <span data-ttu-id="69ef4-328">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-328">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-329">**復原 LSN**</span><span class="sxs-lookup"><span data-stu-id="69ef4-329">**Recovery LSN**</span></span>  
 <span data-ttu-id="69ef4-330">指出在主要複本上，此複本在復原或容錯移轉後、寫入任何新記錄檔記錄前，交易記錄的結尾。</span><span class="sxs-lookup"><span data-stu-id="69ef4-330">Indicates the end of the transaction log before the replica writes any new log records after recovery or failover on the primary replica.</span></span> <span data-ttu-id="69ef4-331">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-331">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-332">**截斷 LSN**</span><span class="sxs-lookup"><span data-stu-id="69ef4-332">**Truncation LSN**</span></span>  
 <span data-ttu-id="69ef4-333">指出主要複本的最小交易記錄值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-333">Indicates the minimum log truncation value for the primary replica.</span></span> <span data-ttu-id="69ef4-334">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-334">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-335">**上次認可 LSN**</span><span class="sxs-lookup"><span data-stu-id="69ef4-335">**Last Commit LSN**</span></span>  
 <span data-ttu-id="69ef4-336">指出對應到交易記錄中上一個認可記錄的實際 LSN。</span><span class="sxs-lookup"><span data-stu-id="69ef4-336">Indicates the actual LSN corresponding to the last commit record in the transaction log.</span></span> <span data-ttu-id="69ef4-337">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-337">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-338">**上次認可時間**</span><span class="sxs-lookup"><span data-stu-id="69ef4-338">**Last Commit Time**</span></span>  
 <span data-ttu-id="69ef4-339">指出對應到上一個認可記錄的時間。</span><span class="sxs-lookup"><span data-stu-id="69ef4-339">Indicates the time corresponding to the last commit record.</span></span> <span data-ttu-id="69ef4-340">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-340">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-341">**上次傳送 LSN**</span><span class="sxs-lookup"><span data-stu-id="69ef4-341">**Last Sent LSN**</span></span>  
 <span data-ttu-id="69ef4-342">指出主要複本已傳送所有記錄檔區塊到哪一點。</span><span class="sxs-lookup"><span data-stu-id="69ef4-342">Indicates the point up to which all log blocks have been sent by the primary replica.</span></span> <span data-ttu-id="69ef4-343">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-343">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-344">**上次傳送時間**</span><span class="sxs-lookup"><span data-stu-id="69ef4-344">**Last Sent Time**</span></span>  
 <span data-ttu-id="69ef4-345">指出上次傳送記錄檔區塊的時間。</span><span class="sxs-lookup"><span data-stu-id="69ef4-345">Indicates the time when the last log block was sent.</span></span> <span data-ttu-id="69ef4-346">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-346">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-347">**上次接收 LSN**</span><span class="sxs-lookup"><span data-stu-id="69ef4-347">**Last Received LSN**</span></span>  
 <span data-ttu-id="69ef4-348">指出裝載次要資料庫的次要複本已經接收所有記錄檔區塊到哪一點。</span><span class="sxs-lookup"><span data-stu-id="69ef4-348">Indicates the point up to which all log blocks have been received by the secondary replica that hosts the secondary database.</span></span> <span data-ttu-id="69ef4-349">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-349">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-350">**上次接收時間**</span><span class="sxs-lookup"><span data-stu-id="69ef4-350">**Last Received Time**</span></span>  
 <span data-ttu-id="69ef4-351">指出在次要複本上讀取上一個接收訊息內之記錄檔區塊識別碼的時間。</span><span class="sxs-lookup"><span data-stu-id="69ef4-351">Indicates the time when the log block identifier in last message received was read on the secondary replica.</span></span> <span data-ttu-id="69ef4-352">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-352">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-353">**上次強行寫入 LSN**</span><span class="sxs-lookup"><span data-stu-id="69ef4-353">**Last Hardened LSN**</span></span>  
 <span data-ttu-id="69ef4-354">指出次要複本上已將所有記錄檔記錄排清至磁碟到哪一點。</span><span class="sxs-lookup"><span data-stu-id="69ef4-354">Indicates the point up to which all log records have been flushed to disk on the secondary replica.</span></span> <span data-ttu-id="69ef4-355">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-355">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-356">**上次強行寫入時間**</span><span class="sxs-lookup"><span data-stu-id="69ef4-356">**Last Hardened Time**</span></span>  
 <span data-ttu-id="69ef4-357">指出在次要複本上，收到上次強行寫入 LSN 之記錄檔區塊識別碼的時間。</span><span class="sxs-lookup"><span data-stu-id="69ef4-357">Indicates the time when the log-block identifier was received for the last hardened LSN on the secondary replica.</span></span> <span data-ttu-id="69ef4-358">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-358">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-359">**上次重做 LSN**</span><span class="sxs-lookup"><span data-stu-id="69ef4-359">**Last Redone LSN**</span></span>  
 <span data-ttu-id="69ef4-360">指出上次在次要複本上重做之記錄檔記錄的實際 LSN。</span><span class="sxs-lookup"><span data-stu-id="69ef4-360">Indicates the actual LSN of the log record that was redone last on the secondary replica.</span></span> <span data-ttu-id="69ef4-361">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-361">This value is hidden by default.</span></span>  
  
 <span data-ttu-id="69ef4-362">**上次重做時間**</span><span class="sxs-lookup"><span data-stu-id="69ef4-362">**Last Redone Time**</span></span>  
 <span data-ttu-id="69ef4-363">指出在次要資料庫上重做上一個記錄檔記錄的時間。</span><span class="sxs-lookup"><span data-stu-id="69ef4-363">Indicates the time when the last log record was redone on the secondary database.</span></span> <span data-ttu-id="69ef4-364">預設隱藏此值。</span><span class="sxs-lookup"><span data-stu-id="69ef4-364">This value is hidden by default.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="69ef4-365">相關工作</span><span class="sxs-lookup"><span data-stu-id="69ef4-365">Related Tasks</span></span>  
  
-   [<span data-ttu-id="69ef4-366">使用 AlwaysOn 原則來查看可用性群組的健全狀況 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69ef4-366">Use AlwaysOn Policies to View the Health of an Availability Group &#40;SQL Server&#41;</span></span>](use-always-on-policies-to-view-the-health-of-an-availability-group-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="69ef4-367">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69ef4-367">See Also</span></span>  
 <span data-ttu-id="69ef4-368">[sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="69ef4-368">[sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql) </span></span>  
 [<span data-ttu-id="69ef4-369">監視可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="69ef4-369">Monitoring of Availability Groups &#40;SQL Server&#41;</span></span>](monitoring-of-availability-groups-sql-server.md)  
  
  
