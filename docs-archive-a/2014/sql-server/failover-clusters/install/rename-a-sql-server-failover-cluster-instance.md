---
title: 重新命名 SQL Server 容錯移轉叢集執行個體 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: install
ms.topic: conceptual
helpviewer_keywords:
- clusters [SQL Server], virtual servers
- renaming virtual servers
- virtual servers [SQL Server], failover clustering
- failover clustering [SQL Server], virtual servers
ms.assetid: 2a49d417-25fb-4760-8ae5-5871bfb1e6f3
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 397e36931e446861db0fcb899cad30e8c7b1ffc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595591"
---
# <a name="rename-a-sql-server-failover-cluster-instance"></a><span data-ttu-id="5cc16-102">重新命名 SQL Server 容錯移轉叢集執行個體</span><span class="sxs-lookup"><span data-stu-id="5cc16-102">Rename a SQL Server Failover Cluster Instance</span></span>
  <span data-ttu-id="5cc16-103">當 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體是容錯移轉叢集的一部份時，重新命名虛擬伺服器的程序會不同於重新命名獨立執行個體的程序。</span><span class="sxs-lookup"><span data-stu-id="5cc16-103">When a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance is part of a failover cluster, the process of renaming the virtual server differs from that of renaming a stand-alone instance.</span></span> <span data-ttu-id="5cc16-104">如需詳細資訊，請參閱 [重新命名主控 SQL Server 獨立執行個體的電腦](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5cc16-104">For more information, see [Rename a Computer that Hosts a Stand-Alone Instance of SQL Server](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md).</span></span>  
  
 <span data-ttu-id="5cc16-105">虛擬伺服器的名稱一定跟「SQL 網路名稱」(SQL 虛擬伺服器網路名稱) 的名稱相同。</span><span class="sxs-lookup"><span data-stu-id="5cc16-105">The name of the virtual server is always the same as the name of the SQL Network Name (the SQL Virtual Server Network Name).</span></span> <span data-ttu-id="5cc16-106">雖然您可以變更虛擬伺服器的名稱，但無法變更執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="5cc16-106">Although you can change the name of the virtual server, you cannot change the instance name.</span></span> <span data-ttu-id="5cc16-107">例如，您可以將名稱為 VS1\instance1 的虛擬伺服器變更為其他的名稱，例如 SQL35\instance1，但名稱的執行個體部份 instance1 會維持不變。</span><span class="sxs-lookup"><span data-stu-id="5cc16-107">For example, you can change a virtual server named VS1\instance1 to some other name, such as SQL35\instance1, but the instance portion of the name, instance1, will remain unchanged.</span></span>  
  
 <span data-ttu-id="5cc16-108">在開始重新命名的程序之前，請檢閱以下項目。</span><span class="sxs-lookup"><span data-stu-id="5cc16-108">Before you begin the renaming process, review the items below.</span></span>  
  
-   [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="5cc16-109">不支援與複寫有關之伺服器的重新命名作業。</span><span class="sxs-lookup"><span data-stu-id="5cc16-109">does not support renaming servers involved in replication, except in the case of using log shipping with replication.</span></span> <span data-ttu-id="5cc16-110">如果主要伺服器永久失去了，就可以重新命名記錄傳送中的次要伺服器。</span><span class="sxs-lookup"><span data-stu-id="5cc16-110">The secondary server in log shipping can be renamed if the primary server is permanently lost.</span></span> <span data-ttu-id="5cc16-111">如需詳細資訊，請參閱[記錄傳送和複寫 &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="5cc16-111">For more information, see [Log Shipping and Replication &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md).</span></span>  
  
-   <span data-ttu-id="5cc16-112">在重新命名設定為使用資料庫鏡像的虛擬伺服器時，您必須在重新命名作業之前關閉資料庫鏡像，然後使用新的虛擬伺服器名稱，重新建立資料庫鏡像。</span><span class="sxs-lookup"><span data-stu-id="5cc16-112">When renaming a virtual server that is configured to use database mirroring, you must turn off database mirroring before the renaming operation, and then re-establish database mirroring with the new virtual server name.</span></span> <span data-ttu-id="5cc16-113">資料庫鏡像的中繼資料並不會自動更新來反映新的虛擬伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="5cc16-113">Metadata for database mirroring will not be updated automatically to reflect the new virtual server name.</span></span>  
  
### <a name="to-rename-a-virtual-server"></a><span data-ttu-id="5cc16-114">若要重新命名虛擬伺服器</span><span class="sxs-lookup"><span data-stu-id="5cc16-114">To rename a virtual server</span></span>  
  
1.  <span data-ttu-id="5cc16-115">使用 [叢集管理員]，將「SQL 網路名稱」變更為新的名稱。</span><span class="sxs-lookup"><span data-stu-id="5cc16-115">Using Cluster Administrator, change the SQL Network Name to the new name.</span></span>  
  
2.  <span data-ttu-id="5cc16-116">使網路名稱資源離線。</span><span class="sxs-lookup"><span data-stu-id="5cc16-116">Take the network name resource offline.</span></span> <span data-ttu-id="5cc16-117">這會連帶使 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資源以及其他相依的資源離線。</span><span class="sxs-lookup"><span data-stu-id="5cc16-117">This takes the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource and other dependent resources offline as well.</span></span>  
  
3.  <span data-ttu-id="5cc16-118">使 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資源回到線上。</span><span class="sxs-lookup"><span data-stu-id="5cc16-118">Bring the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource back online.</span></span>  
  
## <a name="verify-the-renaming-operation"></a><span data-ttu-id="5cc16-119">確認重新命名作業</span><span class="sxs-lookup"><span data-stu-id="5cc16-119">Verify the Renaming Operation</span></span>  
 <span data-ttu-id="5cc16-120">重新命名虛擬伺服器之後，任何使用舊名稱的連接現在都必須使用新名稱進行連接。</span><span class="sxs-lookup"><span data-stu-id="5cc16-120">After a virtual server has been renamed, any connections that used the old name must now connect using the new name.</span></span>  
  
 <span data-ttu-id="5cc16-121">若要確認重新命名作業已經完成，請從 `@@servername` 或 `sys.servers` 選取資訊。</span><span class="sxs-lookup"><span data-stu-id="5cc16-121">To verify that the renaming operation has completed, select information from either `@@servername` or `sys.servers`.</span></span> <span data-ttu-id="5cc16-122">`@@servername` 函數會傳回新的虛擬伺服器名稱，而 `sys.servers` 資料表則會顯示新的虛擬伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="5cc16-122">The `@@servername` function will return the new virtual server name, and the `sys.servers` table will show the new virtual server name.</span></span> <span data-ttu-id="5cc16-123">若要確認容錯移轉程序可以使用新名稱正常運作，使用者應該同時嘗試將 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資源容錯移轉至其他節點。</span><span class="sxs-lookup"><span data-stu-id="5cc16-123">To verify that the failover process is working correctly with the new name, the user should also try to fail the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] resource over to the other nodes.</span></span>  
  
 <span data-ttu-id="5cc16-124">對於來自叢集內任何節點的連接，幾乎可以立即使用新的名稱。</span><span class="sxs-lookup"><span data-stu-id="5cc16-124">For connections from any node in the cluster, the new name can be used almost immediately.</span></span> <span data-ttu-id="5cc16-125">不過，對於來自用戶端電腦使用新名稱的連接，必須在該用戶端電腦看到新名稱之後，才能使用新名稱連接到伺服器。</span><span class="sxs-lookup"><span data-stu-id="5cc16-125">However, for connections using the new name from a client computer, the new name cannot be used to connect to the server until the new name is visible to that client computer.</span></span> <span data-ttu-id="5cc16-126">新名稱透過網路傳播所需的時間長度可以是幾秒鐘，或長達 3 到 5 分鐘，視網路組態而定；可能也需要額外的時間，才不會在網路上看到舊的虛擬伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="5cc16-126">The length of time required for the new name to be propagated across a network can be a few seconds, or as long as 3 to 5 minutes, depending on the network configuration; additional time may be required before the old virtual server name is no longer visible on the network.</span></span>  
  
 <span data-ttu-id="5cc16-127">若要最小化虛擬伺服器重新命名作業的網路傳播延遲，請使用下列步驟：</span><span class="sxs-lookup"><span data-stu-id="5cc16-127">To minimize network propagation delay of a virtual server renaming operation, use the following steps:</span></span>  
  
#### <a name="to-minimize-network-propagation-delay"></a><span data-ttu-id="5cc16-128">若要最小化網路傳播延遲</span><span class="sxs-lookup"><span data-stu-id="5cc16-128">To minimize network propagation delay</span></span>  
  
1.  <span data-ttu-id="5cc16-129">從伺服器節點的命令提示字元發出下列命令：</span><span class="sxs-lookup"><span data-stu-id="5cc16-129">Issue the following commands from a command prompt on the server node:</span></span>  
  
    ```  
    ipconfig /flushdns  
    ipconfig /registerdns  
    nbtstat -RR  
    ```  
  
## <a name="additional-considerations-after-the-renaming-operation"></a><span data-ttu-id="5cc16-130">重新命名作業之後的其他考量</span><span class="sxs-lookup"><span data-stu-id="5cc16-130">Additional considerations after the Renaming Operation</span></span>  
 <span data-ttu-id="5cc16-131">將容錯移轉叢集的網路名稱重新命名之後，我們必須確認並執行下列指示，才能啟用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent 和 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]中的所有案例。</span><span class="sxs-lookup"><span data-stu-id="5cc16-131">After we rename the network name of failover cluster we need to verify and perform the following instructions to enable all scenarios in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent and [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="5cc16-132">\*\* [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] ：\*\* 在您 [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] 使用 Windows 叢集系統管理員工具來變更容錯移轉叢集實例的網路名稱之後，未來的升級或卸載作業可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="5cc16-132">**[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]:** After you change the network name of a [!INCLUDE[ssASCurrent](../../../includes/ssascurrent-md.md)] failover cluster instance using Windows Cluster Administrator tool, the future upgrade or uninstall operation might fail.</span></span> <span data-ttu-id="5cc16-133">若要解決此問題，請遵循[此](https://go.microsoft.com/fwlink/?LinkId=244002) (的解決方式一節中的指示，更新**ClusterName**登錄專案 https://go.microsoft.com/fwlink/?LinkId=244002) 。</span><span class="sxs-lookup"><span data-stu-id="5cc16-133">To resolve this issue update the **ClusterName** registry entry following the instructions in the resolution section of [this](https://go.microsoft.com/fwlink/?LinkId=244002) (https://go.microsoft.com/fwlink/?LinkId=244002).</span></span>  
  
 <span data-ttu-id="5cc16-134">\*\* [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 代理程式服務：\*\* 確認並執行下列其他動作 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]代理程式服務：</span><span class="sxs-lookup"><span data-stu-id="5cc16-134">**[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent Service:** Verify and perform the below additional actions for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Agent Service:</span></span>  
  
-   <span data-ttu-id="5cc16-135">如果 SQL 代理程式設定為事件轉送，請修正登錄設定。</span><span class="sxs-lookup"><span data-stu-id="5cc16-135">Fix the registry settings if SQL Agent is configured for event forwarding.</span></span> <span data-ttu-id="5cc16-136">如需詳細資訊，請參閱[指定事件轉送伺服器 &#40;SQL Server Management Studio&#41;](../../../ssms/agent/designate-an-events-forwarding-server-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="5cc16-136">For more information, see [Designate an Events Forwarding Server &#40;SQL Server Management Studio&#41;](../../../ssms/agent/designate-an-events-forwarding-server-sql-server-management-studio.md).</span></span>  
  
-   <span data-ttu-id="5cc16-137">當電腦/叢集網路名稱已重新命名時，請修正主要伺服器 (MSX) 和目標伺服器 (TSX) 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="5cc16-137">Fix the master server (MSX) and target servers (TSX) instance names when machines / cluster network name is renamed.</span></span> <span data-ttu-id="5cc16-138">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="5cc16-138">For more information, see the following topics:</span></span>  
  
    -   [<span data-ttu-id="5cc16-139">從主要伺服器脫離多個目標伺服器</span><span class="sxs-lookup"><span data-stu-id="5cc16-139">Defect Multiple Target Servers from a Master Server</span></span>](../../../ssms/agent/defect-multiple-target-servers-from-a-master-server.md)  
  
    -   [<span data-ttu-id="5cc16-140">建立多伺服器環境</span><span class="sxs-lookup"><span data-stu-id="5cc16-140">Create a Multiserver Environment</span></span>](../../../ssms/agent/create-a-multiserver-environment.md)  
  
-   <span data-ttu-id="5cc16-141">重新設定記錄傳送，以便使用更新的伺服器名稱來備份和還原記錄。</span><span class="sxs-lookup"><span data-stu-id="5cc16-141">Reconfigure the Log Shipping so that updated server name is used to backup and restore logs.</span></span> <span data-ttu-id="5cc16-142">如需詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="5cc16-142">For more information, see the following topics:</span></span>  
  
    -   [<span data-ttu-id="5cc16-143">設定記錄傳送 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5cc16-143">Configure Log Shipping &#40;SQL Server&#41;</span></span>](../../../database-engine/log-shipping/configure-log-shipping-sql-server.md)  
  
    -   [<span data-ttu-id="5cc16-144">移除記錄傳送 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="5cc16-144">Remove Log Shipping &#40;SQL Server&#41;</span></span>](../../../database-engine/log-shipping/remove-log-shipping-sql-server.md)  
  
-   <span data-ttu-id="5cc16-145">更新相依於伺服器名稱的作業步驟。</span><span class="sxs-lookup"><span data-stu-id="5cc16-145">Update the Jobsteps that depend on server name.</span></span> <span data-ttu-id="5cc16-146">如需詳細資訊，請參閱 [Manage Job Steps](../../../ssms/agent/manage-job-steps.md)。</span><span class="sxs-lookup"><span data-stu-id="5cc16-146">For more information, see [Manage Job Steps](../../../ssms/agent/manage-job-steps.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cc16-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cc16-147">See Also</span></span>  
 [<span data-ttu-id="5cc16-148">重新命名主控 SQL Server 獨立執行個體的電腦</span><span class="sxs-lookup"><span data-stu-id="5cc16-148">Rename a Computer that Hosts a Stand-Alone Instance of SQL Server</span></span>](../../../database-engine/install-windows/rename-a-computer-that-hosts-a-stand-alone-instance-of-sql-server.md)  
  
  
