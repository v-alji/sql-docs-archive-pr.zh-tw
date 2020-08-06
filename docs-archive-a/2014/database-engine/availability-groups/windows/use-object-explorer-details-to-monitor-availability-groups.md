---
title: 使用物件總管詳細資料來監視可用性群組 (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.OEdetails.f1
helpviewer_keywords:
- Availability Groups [SQL Server], monitoring
- Availability Groups [SQL Server], databases
- Availability Groups [SQL Server]
ms.assetid: 84affc47-40e0-43d9-855e-468967068c35
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 419f1cd22e0a7aa314f6a1036793091bb7b385fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592244"
---
# <a name="use-the-object-explorer-details-to-monitor-availability-groups-sql-server-management-studio"></a><span data-ttu-id="e8947-102">使用物件總管詳細資料監視可用性群組 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="e8947-102">Use the Object Explorer Details to Monitor Availability Groups (SQL Server Management Studio)</span></span>
  <span data-ttu-id="e8947-103">此主題描述如何使用 **的** [物件總管詳細資料] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] 窗格來監視及管理現有 AlwaysOn 可用性群組、可用性複本和可用性資料庫。</span><span class="sxs-lookup"><span data-stu-id="e8947-103">This topic describes how to use the **Object Explorer Details** pane of [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] to monitor and manage existing AlwaysOn availability groups, availability replicas, and availability databases.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8947-104">如需使用 [物件總管詳細資料] 窗格的詳細資訊，請參閱 [物件總管詳細資料窗格](../../../ssms/object/object-explorer-details-pane.md)。</span><span class="sxs-lookup"><span data-stu-id="e8947-104">For information about using the Object Explorer Details pane, see [Object Explorer Details Pane](../../../ssms/object/object-explorer-details-pane.md).</span></span>  
  
-   <span data-ttu-id="e8947-105">**開始之前：**  [必要條件](#Prerequisites)</span><span class="sxs-lookup"><span data-stu-id="e8947-105">**Before you begin:**  [Prerequisites](#Prerequisites)</span></span>  
  
-   <span data-ttu-id="e8947-106">**若要使用下列項目監視可用性群組：**  [SQL Server Management Studio](#SSMSProcedure)</span><span class="sxs-lookup"><span data-stu-id="e8947-106">**To Monitor an Availability Group, using:**  [SQL Server Management Studio](#SSMSProcedure)</span></span>  
  
-   <span data-ttu-id="e8947-107">**物件總管詳細資料：**</span><span class="sxs-lookup"><span data-stu-id="e8947-107">**Object Explorer Details:**</span></span>  
  
     [<span data-ttu-id="e8947-108">可用性群組詳細資料</span><span class="sxs-lookup"><span data-stu-id="e8947-108">Availability Group Details</span></span>](#AvGroupsDetails)  
  
     [<span data-ttu-id="e8947-109">可用性複本詳細資料</span><span class="sxs-lookup"><span data-stu-id="e8947-109">Availability Replica Details</span></span>](#AvReplicaDetails)  
  
     [<span data-ttu-id="e8947-110">可用性資料庫詳細資料</span><span class="sxs-lookup"><span data-stu-id="e8947-110">Availability Database Details</span></span>](#AvDbDetails)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="e8947-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="e8947-111">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="e8947-112">必要條件</span><span class="sxs-lookup"><span data-stu-id="e8947-112">Prerequisites</span></span>  
 <span data-ttu-id="e8947-113">您必須連接到裝載主要複本或次要複本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體 (伺服器執行個體)。</span><span class="sxs-lookup"><span data-stu-id="e8947-113">You must be connected to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] (server instance) that hosts either the primary replica or a secondary replica.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="e8947-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="e8947-114">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="e8947-115">**監視可用性群組、可用性複本和可用性資料庫**</span><span class="sxs-lookup"><span data-stu-id="e8947-115">**To monitor availability groups, availability replicas, and availability databases**</span></span>  
  
1.  <span data-ttu-id="e8947-116">在 [檢視] 功能表上，按一下 **[物件總管詳細資料]** 或按 **F7** 鍵。</span><span class="sxs-lookup"><span data-stu-id="e8947-116">On the View menu, click **Object Explorer Details**, or press the **F7** key.</span></span>  
  
2.  <span data-ttu-id="e8947-117">在 [物件總管] 中，連接到您要監視可用性群組的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體，然後按一下伺服器名稱以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="e8947-117">In Object Explorer, connect to the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] on which you want to monitor an availability group, and click the server name to expand the server tree.</span></span>  
  
3.  <span data-ttu-id="e8947-118">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="e8947-118">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
4.  <span data-ttu-id="e8947-119">**[物件總管詳細資料]** 窗格會顯示連接之伺服器執行個體裝載複本的每個可用性群組。</span><span class="sxs-lookup"><span data-stu-id="e8947-119">The **Object Explorer Details** pane displays every availability group for which the connected server instance hosts a replica.</span></span> <span data-ttu-id="e8947-120">對於每個可用性群組，[伺服器執行個體 (主要)] 資料行會顯示目前裝載主要複本的伺服器執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="e8947-120">For each availability group, the **Server Instance (Primary)** column displays the name of the server instance that is currently hosting the primary replica.</span></span>  <span data-ttu-id="e8947-121">若要顯示有關給定之可用性群組的詳細資訊，請在 [物件總管] 中選取它。</span><span class="sxs-lookup"><span data-stu-id="e8947-121">To display more information about a given availability group, select it in Object Explorer.</span></span>  
  
5.  <span data-ttu-id="e8947-122">接著 **[物件總管詳細資料]** 窗格會顯示此可用性群組的 **[可用性複本]** 和 **[可用性資料庫]** 節點：</span><span class="sxs-lookup"><span data-stu-id="e8947-122">The **Object Explorer Details** pane then displays the **Availability Replicas** and **Availability Databases** nodes for this availability group:</span></span>  
  
    -   <span data-ttu-id="e8947-123">當您在 [物件總管] 中展開 **[可用性群組]** 節點並選取 **[可用性複本]** 節點時， **[物件總管詳細資料]** 窗格會顯示有關群組中每個可用性複本的資訊。</span><span class="sxs-lookup"><span data-stu-id="e8947-123">When you expand the **Availability Group** node in Object Explorer and select the **Availability Replicas** node, the **Object Explorer Details** pane displays information about each of the availability replicas in the group.</span></span> <span data-ttu-id="e8947-124">如需詳細資訊，請參閱本主題稍後的＜ [可用性複本詳細資料](#AvReplicaDetails)＞。</span><span class="sxs-lookup"><span data-stu-id="e8947-124">For more information, see [Availability Replica Details](#AvReplicaDetails), later in this topic.</span></span>  
  
         <span data-ttu-id="e8947-125">若要對多個可用性複本執行作業，請選取它們，並以滑鼠右鍵按一下它們，開啟列出可用命令的內容功能表。</span><span class="sxs-lookup"><span data-stu-id="e8947-125">To perform operations on multiple availability replicas, select them, and right-click them to open up a context menu that lists the available commands.</span></span>  
  
    -   <span data-ttu-id="e8947-126">當您在 [物件總管] 中展開 **[可用性群組]** 節點並選取 **[可用性資料庫]** 節點時， **[物件總管詳細資料]** 窗格會顯示有關群組中每個可用性資料庫的資訊。</span><span class="sxs-lookup"><span data-stu-id="e8947-126">When you expand the **Availability Group** node in Object Explorer and select the **Availability Databases** node, the **Object Explorer Details** pane displays information about each of the availability databases in the group.</span></span> <span data-ttu-id="e8947-127">如需詳細資訊，請參閱本主題稍後的＜ [可用性資料庫詳細資料](#AvDbDetails)＞。</span><span class="sxs-lookup"><span data-stu-id="e8947-127">For more information, see [Availability Database Details](#AvDbDetails), later in this topic.</span></span>  
  
         <span data-ttu-id="e8947-128">若要對多個可用性資料庫執行作業，請選取它們，並以滑鼠右鍵按一下它們，開啟列出可用命令的內容功能表。</span><span class="sxs-lookup"><span data-stu-id="e8947-128">To perform operations on multiple availability databases, select them, and right-click them to open up a context menu that lists the available commands.</span></span>  
  
##  <a name="availability-groups-details"></a><a name="AvGroupsDetails"></a> <span data-ttu-id="e8947-129">可用性群組詳細資料</span><span class="sxs-lookup"><span data-stu-id="e8947-129">Availability Groups Details</span></span>  
 <span data-ttu-id="e8947-130">**[可用性群組]** 詳細資料畫面顯示下列資料行：</span><span class="sxs-lookup"><span data-stu-id="e8947-130">The **Availability Groups** details screen displays the following columns:</span></span>  
  
 <span data-ttu-id="e8947-131">**名稱**</span><span class="sxs-lookup"><span data-stu-id="e8947-131">**Name**</span></span>  
 <span data-ttu-id="e8947-132">列出所選可用性群組的 [可用性複本]、[可用性資料庫] 和 [可用性群組接聽程式] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e8947-132">Lists the **Availability Replicas**, **Availability Databases**, and **Availability Group** Listeners folders of the selected availability group.</span></span>  
  
##  <a name="availability-replica-details"></a><a name="AvReplicaDetails"></a> <span data-ttu-id="e8947-133">可用性複本詳細資料</span><span class="sxs-lookup"><span data-stu-id="e8947-133">Availability Replica Details</span></span>  
 <span data-ttu-id="e8947-134">**[可用性複本]** 詳細資料畫面顯示下列資料行：</span><span class="sxs-lookup"><span data-stu-id="e8947-134">The **Availability Replica** details screen displays the following columns:</span></span>  
  
 <span data-ttu-id="e8947-135">**伺服器執行個體**</span><span class="sxs-lookup"><span data-stu-id="e8947-135">**Server Instance**</span></span>  
 <span data-ttu-id="e8947-136">顯示裝載可用性複本的伺服器執行個體名稱，以及表示此伺服器執行個體與本機伺服器執行個體之間目前連接狀態的圖示。</span><span class="sxs-lookup"><span data-stu-id="e8947-136">Displays the name of the server instance that hosts the availability replica, along with an icon that indicates the current connection state of the server instance to the local server instance.</span></span>  
  
 <span data-ttu-id="e8947-137">**角色**</span><span class="sxs-lookup"><span data-stu-id="e8947-137">**Role**</span></span>  
 <span data-ttu-id="e8947-138">指出可用性複本的目前角色： **主要** 或 **次要**。</span><span class="sxs-lookup"><span data-stu-id="e8947-138">Indicates the current role of the availability replica, either **Primary** or **Secondary**.</span></span> <span data-ttu-id="e8947-139">如需 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 角色的相關資訊，請參閱 [AlwaysOn 可用性群組概觀 &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="e8947-139">For information about [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] roles, see [Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md).</span></span>  
  
 <span data-ttu-id="e8947-140">**次要角色的連接模式**</span><span class="sxs-lookup"><span data-stu-id="e8947-140">**Connection Mode in Secondary Role**</span></span>  
 <span data-ttu-id="e8947-141">指出執行次要角色之給定可用性複本 (也就是做為次要複本) 的資料庫是否可接受來自用戶端的連接。</span><span class="sxs-lookup"><span data-stu-id="e8947-141">Indicates whether the databases of a given availability replica that is performing the secondary role (that is, is acting as a secondary replica) can accept connections from clients.</span></span>  
  
 <span data-ttu-id="e8947-142">可能的值如下：</span><span class="sxs-lookup"><span data-stu-id="e8947-142">The possible values are as follows:</span></span>  
  
|<span data-ttu-id="e8947-143">值</span><span class="sxs-lookup"><span data-stu-id="e8947-143">Value</span></span>|<span data-ttu-id="e8947-144">描述</span><span class="sxs-lookup"><span data-stu-id="e8947-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e8947-145">**不允許連接**</span><span class="sxs-lookup"><span data-stu-id="e8947-145">**Disallow Connections**</span></span>|<span data-ttu-id="e8947-146">當此可用性複本做為次要複本時，不允許直接連接到可用性資料庫。</span><span class="sxs-lookup"><span data-stu-id="e8947-146">No direct connections are allowed to the availability databases when this availability replica is acting as a secondary replica.</span></span> <span data-ttu-id="e8947-147">次要資料庫不適用於讀取。</span><span class="sxs-lookup"><span data-stu-id="e8947-147">Secondary databases are not available for read access.</span></span>|  
|<span data-ttu-id="e8947-148">**只允許讀取意圖的連接**</span><span class="sxs-lookup"><span data-stu-id="e8947-148">**Allow Only Read Intent Connections**</span></span>|<span data-ttu-id="e8947-149">當此複本做為次要複本時，只允許進行直接唯讀連接。</span><span class="sxs-lookup"><span data-stu-id="e8947-149">Only direct read-only connections are allowed  when this replica acting as a secondary replica.</span></span> <span data-ttu-id="e8947-150">可讀取複本中的所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="e8947-150">All database(s) in the replica are available for read access.</span></span>|  
|<span data-ttu-id="e8947-151">**允許所有連接**</span><span class="sxs-lookup"><span data-stu-id="e8947-151">**Allow All Connections**</span></span>|<span data-ttu-id="e8947-152">當此複本做為次要複本時，允許與這些資料庫之間的所有連接。</span><span class="sxs-lookup"><span data-stu-id="e8947-152">All connections are allowed to these databases for read-only access when this replica acting as a secondary replica.</span></span>|  
  
 <span data-ttu-id="e8947-153">**連接狀態**</span><span class="sxs-lookup"><span data-stu-id="e8947-153">**Connection State**</span></span>  
 <span data-ttu-id="e8947-154">指出次要複本目前是否已連接到主要複本。</span><span class="sxs-lookup"><span data-stu-id="e8947-154">Indicates whether a secondary replica is currently connected to the primary replica.</span></span> <span data-ttu-id="e8947-155">可能的值如下：</span><span class="sxs-lookup"><span data-stu-id="e8947-155">The possible values are as follows:</span></span>  
  
|<span data-ttu-id="e8947-156">值</span><span class="sxs-lookup"><span data-stu-id="e8947-156">Value</span></span>|<span data-ttu-id="e8947-157">描述</span><span class="sxs-lookup"><span data-stu-id="e8947-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e8947-158">**已中斷連線**</span><span class="sxs-lookup"><span data-stu-id="e8947-158">**Disconnected**</span></span>|<span data-ttu-id="e8947-159">若為遠端可用性複本，表示它與本機可用性複本已中斷連接。</span><span class="sxs-lookup"><span data-stu-id="e8947-159">For a remote availability replica, indicates that it is disconnected from the local availability replica.</span></span> <span data-ttu-id="e8947-160">本機複本對 [已中斷連接] 狀態的回應取決於其角色，如下所示：</span><span class="sxs-lookup"><span data-stu-id="e8947-160">The response of the local replica to the Disconnected state depends on its role, as follows:</span></span><br /><br /> <span data-ttu-id="e8947-161">在主要複本上，如果次要複本已中斷連接，主要複本上的次要資料庫就會標示為 **[未同步處理]** ，而且主要複本會等候次要複本重新連接。</span><span class="sxs-lookup"><span data-stu-id="e8947-161">On the primary replica, if a secondary replica is disconnected, the secondary databases are marked as **Not Synchronized** on the primary replica, and the primary replica waits for the secondary to reconnect.</span></span><br /><br /> <span data-ttu-id="e8947-162">在次要複本上，一旦偵測到它已中斷連接之後，次要複本就會嘗試重新連接到主要複本。</span><span class="sxs-lookup"><span data-stu-id="e8947-162">On the secondary replica, upon detecting that it is disconnected, the secondary replica attempts to reconnect to the primary replica.</span></span>|  
|<span data-ttu-id="e8947-163">**已連接**</span><span class="sxs-lookup"><span data-stu-id="e8947-163">**Connected**</span></span>|<span data-ttu-id="e8947-164">目前連接到本機複本的遠端可用性複本。</span><span class="sxs-lookup"><span data-stu-id="e8947-164">A remote availability replica that is currently connected to the local replica.</span></span>|  
|<span data-ttu-id="e8947-165">**NULL**</span><span class="sxs-lookup"><span data-stu-id="e8947-165">**NULL**</span></span>|<span data-ttu-id="e8947-166">如果本機複本是次要複本，其他次要複本的此值就是 NULL。</span><span class="sxs-lookup"><span data-stu-id="e8947-166">If the local replica is a secondary replica, this value is NULL for other secondary replicas.</span></span>|  
  
 <span data-ttu-id="e8947-167">**同步處理狀態**</span><span class="sxs-lookup"><span data-stu-id="e8947-167">**Synchronization State**</span></span>  
 <span data-ttu-id="e8947-168">指出次要複本目前是否與主要複本進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="e8947-168">Indicates whether a secondary replica is currently synchronized with primary replica.</span></span> <span data-ttu-id="e8947-169">可能的值如下：</span><span class="sxs-lookup"><span data-stu-id="e8947-169">The possible values are as follows:</span></span>  
  
|<span data-ttu-id="e8947-170">值</span><span class="sxs-lookup"><span data-stu-id="e8947-170">Value</span></span>|<span data-ttu-id="e8947-171">描述</span><span class="sxs-lookup"><span data-stu-id="e8947-171">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e8947-172">**[未同步處理]**</span><span class="sxs-lookup"><span data-stu-id="e8947-172">**Not Synchronized**</span></span>|<span data-ttu-id="e8947-173">資料庫未同步處理或者尚未聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="e8947-173">The database is not synchronized or has not yet been joined to the availability group.</span></span>|  
|<span data-ttu-id="e8947-174">**已同步處理**</span><span class="sxs-lookup"><span data-stu-id="e8947-174">**Synchronized**</span></span>|<span data-ttu-id="e8947-175">資料庫會與目前主要複本 (如果有的話) 或最後一個主要複本的主要資料庫進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="e8947-175">The database is synchronized with the primary database on the current primary replica, if any, or on the last primary replica.</span></span><br /><br /> <span data-ttu-id="e8947-176">注意:在效能模式中，資料庫永遠不會處於同步處理狀態。</span><span class="sxs-lookup"><span data-stu-id="e8947-176">Note: In performance mode, the database is never in the Synchronized state.</span></span>|  
|<span data-ttu-id="e8947-177">**NULL**</span><span class="sxs-lookup"><span data-stu-id="e8947-177">**NULL**</span></span>|<span data-ttu-id="e8947-178">未知的狀態。</span><span class="sxs-lookup"><span data-stu-id="e8947-178">Unknown state.</span></span> <span data-ttu-id="e8947-179">當本機伺服器執行個體無法與 WSFC 容錯移轉叢集通訊 (亦即，本機節點不屬於 WSFC 仲裁的一部分) 時，就會出現這個值。</span><span class="sxs-lookup"><span data-stu-id="e8947-179">This value occurs when the local server instance cannot communicate with the WSFC failover cluster (that is the local node is not part of WSFC quorum).</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="e8947-180">如需可用性複本效能計數器的相關資訊，請參閱 [SQLServer，可用性複本](../../../relational-databases/performance-monitor/sql-server-availability-replica.md)。</span><span class="sxs-lookup"><span data-stu-id="e8947-180">For information about performance counters for availability replicas, see [SQL Server, Availability Replica](../../../relational-databases/performance-monitor/sql-server-availability-replica.md).</span></span>  
  
##  <a name="availability-database-details"></a><a name="AvDbDetails"></a> <span data-ttu-id="e8947-181">可用性資料庫詳細資料</span><span class="sxs-lookup"><span data-stu-id="e8947-181">Availability Database Details</span></span>  
 <span data-ttu-id="e8947-182">**[可用性資料庫]** 詳細資料畫面顯示給定之可用性群組中可用性資料庫的下列屬性：</span><span class="sxs-lookup"><span data-stu-id="e8947-182">The **Availability Database** details screen displays the following properties of the availability databases in a given availability group:</span></span>  
  
 <span data-ttu-id="e8947-183">**名稱**</span><span class="sxs-lookup"><span data-stu-id="e8947-183">**Name**</span></span>  
 <span data-ttu-id="e8947-184">可用性資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="e8947-184">The name of the availability database.</span></span>  
  
 <span data-ttu-id="e8947-185">**同步處理狀態**</span><span class="sxs-lookup"><span data-stu-id="e8947-185">**Synchronization State**</span></span>  
 <span data-ttu-id="e8947-186">指出可用性資料庫目前是否與主要複本進行同步處理。</span><span class="sxs-lookup"><span data-stu-id="e8947-186">Indicates whether the availability database is currently synchronized with primary replica.</span></span>  
  
 <span data-ttu-id="e8947-187">可能的同步處理狀態如下所示：</span><span class="sxs-lookup"><span data-stu-id="e8947-187">The possible synchronization states are as follows:</span></span>  
  
|<span data-ttu-id="e8947-188">值</span><span class="sxs-lookup"><span data-stu-id="e8947-188">Value</span></span>|<span data-ttu-id="e8947-189">描述</span><span class="sxs-lookup"><span data-stu-id="e8947-189">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e8947-190">正在同步處理</span><span class="sxs-lookup"><span data-stu-id="e8947-190">Synchronizing</span></span>|<span data-ttu-id="e8947-191">次要資料庫已經收到主要資料庫中尚未寫入磁碟 (強行寫入) 的交易記錄檔記錄。</span><span class="sxs-lookup"><span data-stu-id="e8947-191">The secondary database has received the transaction log records for the primary database that are not yet written to disk (hardened).</span></span><br /><br /> <span data-ttu-id="e8947-192">注意:在非同步認可模式中，同步處理模式一律為 [正在同步處理]。</span><span class="sxs-lookup"><span data-stu-id="e8947-192">Note: In asynchronous-commit mode, the synchronization state is always **Synchronizing**.</span></span>|  
  
 <span data-ttu-id="e8947-193">**已暫停**</span><span class="sxs-lookup"><span data-stu-id="e8947-193">**Suspended**</span></span>  
 <span data-ttu-id="e8947-194">指出可用性資料庫目前是否已上線。</span><span class="sxs-lookup"><span data-stu-id="e8947-194">Indicates whether the availability database is currently online.</span></span> <span data-ttu-id="e8947-195">可能的值如下：</span><span class="sxs-lookup"><span data-stu-id="e8947-195">The possible values are as follows:</span></span>  
  
|<span data-ttu-id="e8947-196">值</span><span class="sxs-lookup"><span data-stu-id="e8947-196">Value</span></span>|<span data-ttu-id="e8947-197">描述</span><span class="sxs-lookup"><span data-stu-id="e8947-197">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e8947-198">**已暫停**</span><span class="sxs-lookup"><span data-stu-id="e8947-198">**Suspended**</span></span>|<span data-ttu-id="e8947-199">此狀態指出資料庫在本機已暫停，需要手動恢復。</span><span class="sxs-lookup"><span data-stu-id="e8947-199">This state indicates that the database is suspended locally and needs to be manually resumed.</span></span><br /><br /> <span data-ttu-id="e8947-200">在主要複本上，此值對次要資料庫是不可靠的。</span><span class="sxs-lookup"><span data-stu-id="e8947-200">On the primary replica, the value is unreliable for a secondary database.</span></span> <span data-ttu-id="e8947-201">若要可靠地判斷次要資料庫是否已暫止，請在裝載此資料庫的次要複本上查詢它。</span><span class="sxs-lookup"><span data-stu-id="e8947-201">To reliably determine whether a secondary database is suspended, query it on the secondary replica that hosts the database.</span></span>|  
|<span data-ttu-id="e8947-202">**未聯結**</span><span class="sxs-lookup"><span data-stu-id="e8947-202">**Not Joined**</span></span>|<span data-ttu-id="e8947-203">指出次要資料庫尚未聯結至可用性群組或已從群組中移除。</span><span class="sxs-lookup"><span data-stu-id="e8947-203">Indicates that the secondary database either has not been joined to the availability group or has been removed from the group.</span></span>|  
|<span data-ttu-id="e8947-204">**線上存取**</span><span class="sxs-lookup"><span data-stu-id="e8947-204">**Online**</span></span>|<span data-ttu-id="e8947-205">指出在本機可用性複本上的資料庫未暫止，並且已連接到資料庫。</span><span class="sxs-lookup"><span data-stu-id="e8947-205">Indicates that the database is not suspended on the local availability replica and that the database is connected.</span></span>|  
|<span data-ttu-id="e8947-206">**未連接**</span><span class="sxs-lookup"><span data-stu-id="e8947-206">**Not Connected**</span></span>|<span data-ttu-id="e8947-207">指出次要複本目前無法連接到主要複本。</span><span class="sxs-lookup"><span data-stu-id="e8947-207">Indicates that the secondary replica is currently unable to connect to the primary replica.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="e8947-208">如需可用性資料庫效能計數器的詳細資訊，請參閱 [SQL Server，資料庫複本](../../../relational-databases/performance-monitor/sql-server-database-replica.md)。</span><span class="sxs-lookup"><span data-stu-id="e8947-208">For information about performance counters for availability databases, see [SQL Server, Database Replica](../../../relational-databases/performance-monitor/sql-server-database-replica.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8947-209">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8947-209">See Also</span></span>  
 <span data-ttu-id="e8947-210">[sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="e8947-210">[sys.dm_os_performance_counters &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-os-performance-counters-transact-sql) </span></span>  
 <span data-ttu-id="e8947-211">[使用 AlwaysOn 儀表板 &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="e8947-211">[Use the AlwaysOn Dashboard &#40;SQL Server Management Studio&#41;](use-the-always-on-dashboard-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="e8947-212">[檢視可用性群組屬性 &#40;SQL Server&#41;](view-availability-group-properties-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e8947-212">[View Availability Group Properties &#40;SQL Server&#41;](view-availability-group-properties-sql-server.md) </span></span>  
 [<span data-ttu-id="e8947-213">檢視可用性複本屬性 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e8947-213">View Availability Replica Properties &#40;SQL Server&#41;</span></span>](view-availability-replica-properties-sql-server.md)  
  
  
