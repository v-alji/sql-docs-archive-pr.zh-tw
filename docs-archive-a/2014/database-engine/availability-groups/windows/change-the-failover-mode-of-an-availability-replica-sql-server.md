---
title: 變更可用性複本的容錯移轉模式 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- failover modes [SQL Server]
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], failover modes
- Availability Groups [SQL Server], configuring
ms.assetid: 619a826f-8e65-48eb-8c34-39497d238279
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d946440e2950192299c42652babb4082790dbd03
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708678"
---
# <a name="change-the-failover-mode-of-an-availability-replica-sql-server"></a><span data-ttu-id="f5c6d-102">變更可用性複本的容錯移轉模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f5c6d-102">Change the Failover Mode of an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="f5c6d-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 PowerShell，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中變更 AlwaysOn 可用性群組內可用性複本的容錯移轉模式。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-103">This topic describes how to change the failover mode of an availability replica in an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span> <span data-ttu-id="f5c6d-104">容錯移轉模式是複本屬性，用於判斷以同步認可可用性模式下執行之複本的容錯移轉模式。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-104">The failover mode is a replica property that determines the failover mode for replicas that run under synchronous-commit availability mode.</span></span> <span data-ttu-id="f5c6d-105">如需詳細資訊，請參閱[容錯移轉及容錯移轉模式 &#40;AlwaysOn 可用性群組&#41;](failover-and-failover-modes-always-on-availability-groups.md) 和[可用性模式 &#40;AlwaysOn 可用性群組&#41;](availability-modes-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-105">For more information, see [Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;](failover-and-failover-modes-always-on-availability-groups.md) and [Availability Modes &#40;AlwaysOn Availability Groups&#41;](availability-modes-always-on-availability-groups.md).</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f5c6d-106">開始之前</span><span class="sxs-lookup"><span data-stu-id="f5c6d-106">Before You Begin</span></span>  
  
###  <a name="prerequisites-and-restrictions"></a><a name="Prerequisites"></a> <span data-ttu-id="f5c6d-107">必要條件和限制</span><span class="sxs-lookup"><span data-stu-id="f5c6d-107">Prerequisites and Restrictions</span></span>  
  
-   <span data-ttu-id="f5c6d-108">只有在主要複本上才支援這個工作。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-108">This task is supported only on primary replicas.</span></span> <span data-ttu-id="f5c6d-109">您必須連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-109">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
-   <span data-ttu-id="f5c6d-110">SQL Server 容錯移轉叢集執行個體 (FCI) 不支援依照可用性群組進行自動容錯移轉，因此任何由 FCI 裝載的可用性複本只能設定為手動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-110">SQL Server Failover Cluster Instances (FCIs) do not support automatic failover by availability groups, so any availability replica that is hosted by an FCI can only be configured for manual failover.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f5c6d-111">Security</span><span class="sxs-lookup"><span data-stu-id="f5c6d-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f5c6d-112">權限</span><span class="sxs-lookup"><span data-stu-id="f5c6d-112">Permissions</span></span>  
 <span data-ttu-id="f5c6d-113">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-113">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f5c6d-114">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f5c6d-114">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="f5c6d-115">**若要變更可用性複本的容錯移轉模式**</span><span class="sxs-lookup"><span data-stu-id="f5c6d-115">**To change the failover mode of an availability replica**</span></span>  
  
1.  <span data-ttu-id="f5c6d-116">在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-116">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="f5c6d-117">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-117">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="f5c6d-118">按一下要變更複本的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-118">Click the availability group whose replica you want to change.</span></span>  
  
4.  <span data-ttu-id="f5c6d-119">以滑鼠右鍵按一下複本，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-119">Right-click the replica, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="f5c6d-120">在 **[可用性複本屬性]** 對話方塊中，使用 **[容錯移轉模式]** 下拉式清單來變更此複本的容錯移轉模式。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-120">In the **Availability Replica Properties** dialog box, use the **Failover mode** drop list to change the failover mode of this replica.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f5c6d-121">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f5c6d-121">Using Transact-SQL</span></span>  
 <span data-ttu-id="f5c6d-122">**若要變更可用性複本的容錯移轉模式**</span><span class="sxs-lookup"><span data-stu-id="f5c6d-122">**To change the failover mode of an availability replica**</span></span>  
  
1.  <span data-ttu-id="f5c6d-123">連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-123">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="f5c6d-124">使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 陳述式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="f5c6d-124">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="f5c6d-125">ALTER AVAILABILITY GROUP *群組名稱* MODIFY REPLICA ON '*伺服器名稱*'</span><span class="sxs-lookup"><span data-stu-id="f5c6d-125">ALTER AVAILABILITY GROUP *group_name* MODIFY REPLICA ON '*server_name*'</span></span>  
  
     <span data-ttu-id="f5c6d-126">WITH ( {</span><span class="sxs-lookup"><span data-stu-id="f5c6d-126">WITH ( {</span></span>  
  
     <span data-ttu-id="f5c6d-127">AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }</span><span class="sxs-lookup"><span data-stu-id="f5c6d-127">AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }</span></span>  
  
     <span data-ttu-id="f5c6d-128">| FAILOVER_MODE = { AUTOMATIC | MANUAL }</span><span class="sxs-lookup"><span data-stu-id="f5c6d-128">| FAILOVER_MODE = { AUTOMATIC | MANUAL }</span></span>  
  
     <span data-ttu-id="f5c6d-129">}  )</span><span class="sxs-lookup"><span data-stu-id="f5c6d-129">}  )</span></span>  
  
     <span data-ttu-id="f5c6d-130">其中</span><span class="sxs-lookup"><span data-stu-id="f5c6d-130">where</span></span>  
  
    -   <span data-ttu-id="f5c6d-131">*group_name* 是可用性群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-131">*group_name* is the name of the availability group.</span></span>  
  
    -   <span data-ttu-id="f5c6d-132">{ '*system_name*[\\*instance_name*]' | '*FCI_network_name*[\\*instance_name*]' }</span><span class="sxs-lookup"><span data-stu-id="f5c6d-132">{ '*system_name*[\\*instance_name*]' | '*FCI_network_name*[\\*instance_name*]' }</span></span>  
  
         <span data-ttu-id="f5c6d-133">指定裝載要改變之可用性複本的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體位址。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-133">Specifies the address of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the availability replica to be altered.</span></span> <span data-ttu-id="f5c6d-134">這個位址的元件如下所示：</span><span class="sxs-lookup"><span data-stu-id="f5c6d-134">The components of this address are as follows:</span></span>  
  
         <span data-ttu-id="f5c6d-135">*system_name*</span><span class="sxs-lookup"><span data-stu-id="f5c6d-135">*system_name*</span></span>  
         <span data-ttu-id="f5c6d-136">這是獨立伺服器執行個體所在之電腦系統的 NetBIOS 名稱。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-136">Is the NetBIOS name of the computer system on which a stand-alone server instance resides.</span></span>  
  
         <span data-ttu-id="f5c6d-137">*FCI_network_name*</span><span class="sxs-lookup"><span data-stu-id="f5c6d-137">*FCI_network_name*</span></span>  
         <span data-ttu-id="f5c6d-138">這是用來存取 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉叢集的網路名稱，其中的目標伺服器執行個體是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 容錯移轉夥伴 (為 FCI)。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-138">Is the network name that is used to access a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover cluster in which a target server instance is a [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] failover partner (an FCI).</span></span>  
  
         <span data-ttu-id="f5c6d-139">*instance_name*</span><span class="sxs-lookup"><span data-stu-id="f5c6d-139">*instance_name*</span></span>  
         <span data-ttu-id="f5c6d-140">這是裝載目標可用性複本之 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-140">Is the name of the instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] that hosts the target availability replica.</span></span> <span data-ttu-id="f5c6d-141">如果是預設伺服器執行個體， *instance_name* 為選擇性。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-141">For a default server instance, *instance_name* is optional.</span></span>  
  
     <span data-ttu-id="f5c6d-142">如需這些參數的詳細資訊，請參閱 [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-142">For more information about these parameters, see [ALTER AVAILABILITY GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-availability-group-transact-sql).</span></span>  
  
     <span data-ttu-id="f5c6d-143">下列範例 (在 *MyAG* 可用性群組的主要複本上輸入) 會針對位於 *COMPUTER01*電腦的預設伺服器執行個體上的可用性複本，將容錯移轉模式變更為自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-143">The following example, entered on the primary replica of the *MyAG* availability group, changes the failover mode to automatic failover on the availability replica that is located on the default server instance on a computer named *COMPUTER01*.</span></span>  
  
    ```  
    ALTER AVAILABILITY GROUP MyAG MODIFY REPLICA ON 'COMPUTER01' WITH  
       (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="f5c6d-144">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="f5c6d-144">Using PowerShell</span></span>  

### <a name="to-change-the-failover-mode-of-an-availability-replica"></a><span data-ttu-id="f5c6d-145">若要變更可用性複本的容錯移轉模式</span><span class="sxs-lookup"><span data-stu-id="f5c6d-145">To change the failover mode of an availability replica</span></span>
  
1.  <span data-ttu-id="f5c6d-146">變更目錄 (`cd`) 為裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-146">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="f5c6d-147">使用 `Set-SqlAvailabilityReplica` 指令程式搭配 `FailoverMode` 參數。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-147">Use the `Set-SqlAvailabilityReplica` cmdlet with the `FailoverMode` parameter.</span></span> <span data-ttu-id="f5c6d-148">將複本設定為自動容錯移轉時，您可能需要使用 `AvailabilityMode` 參數將複本變更成同步認可的可用性模式。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-148">When setting a replica to automatic failover, you might need to use the `AvailabilityMode` parameter to change the replica to synchronous-commit availability mode.</span></span>  
  
     <span data-ttu-id="f5c6d-149">例如，下列命令會將可用性群組 `MyReplica` 中的複本 `MyAg` 修改成使用同步認可的可用性模式並且支援自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-149">For example, the following command modifies the replica `MyReplica` in the availability group `MyAg` to use synchronous-commit availability mode and to support automatic failover.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `
     -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\Replicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="f5c6d-150">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-150">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="f5c6d-151">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-151">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="f5c6d-152">若要設定及使用 SQL Server PowerShell 提供者，請參閱[SQL Server PowerShell 提供者](../../../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="f5c6d-152">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f5c6d-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5c6d-153">See Also</span></span>  
 [<span data-ttu-id="f5c6d-154">AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;</span><span class="sxs-lookup"><span data-stu-id="f5c6d-154">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
 <span data-ttu-id="f5c6d-155">[可用性模式 &#40;AlwaysOn 可用性群組&#41;](availability-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="f5c6d-155">[Availability Modes &#40;AlwaysOn Availability Groups&#41;](availability-modes-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="f5c6d-156">容錯移轉和容錯移轉模式 &#40;AlwaysOn 可用性群組&#41;</span><span class="sxs-lookup"><span data-stu-id="f5c6d-156">Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;</span></span>](failover-and-failover-modes-always-on-availability-groups.md) 
