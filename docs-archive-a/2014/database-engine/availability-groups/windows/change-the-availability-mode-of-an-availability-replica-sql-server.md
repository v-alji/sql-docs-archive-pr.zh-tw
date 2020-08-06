---
title: 變更可用性複本的可用性模式 (SQL Server) (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], deploying
- Availability Groups [SQL Server], configuring
- Availability Groups [SQL Server], availability modes
ms.assetid: c4da8f25-fb1b-45a4-8bf2-195df6df634c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1636f3ea86e083e47276423b120dbc8d3744d387
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708689"
---
# <a name="change-the-availability-mode-of-an-availability-replica-sql-server"></a><span data-ttu-id="1e8ce-102">變更可用性複本的可用性模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1e8ce-102">Change the Availability Mode of an Availability Replica (SQL Server)</span></span>
  <span data-ttu-id="1e8ce-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 PowerShell，在 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中變更 AlwaysOn 可用性群組內可用性複本的可用性模式。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-103">This topic describes how to change the availability mode of an availability replica in an AlwaysOn availability group in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell.</span></span> <span data-ttu-id="1e8ce-104">可用性模式是指控制複本以非同步方式或同步方式認可的複本屬性。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-104">The availability mode is a replica property that controls the whether the replica commits asynchronously or synchronously.</span></span> <span data-ttu-id="1e8ce-105">「非同步認可模式」會犧牲高可用性來達到最大效能，並且只支援強制手動容錯移轉 (可能遺失資料)，這通常稱為「強制容錯移轉」。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-105">*Asynchronous-commit mode* maximizes performance at the expense of high availability and supports only forced manual failover (with possible data loss), typically called *forced failover*.</span></span> <span data-ttu-id="1e8ce-106">這種「同步認可模式」強調的是高可用性而非效能，而且一旦同步處理次要複本之後，便支援手動容錯移轉以及選擇性的自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-106">*Synchronous-commit mode* emphasizes high availability over performance and, once the secondary replica is synchronized, supports manual failover and, optionally, automatic failover.</span></span>  
  

  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1e8ce-107">開始之前</span><span class="sxs-lookup"><span data-stu-id="1e8ce-107">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="1e8ce-108">必要條件</span><span class="sxs-lookup"><span data-stu-id="1e8ce-108">Prerequisites</span></span>  
  
-   <span data-ttu-id="1e8ce-109">您必須連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-109">You must be connected to the server instance that hosts the primary replica.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1e8ce-110">Security</span><span class="sxs-lookup"><span data-stu-id="1e8ce-110">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1e8ce-111">權限</span><span class="sxs-lookup"><span data-stu-id="1e8ce-111">Permissions</span></span>  
 <span data-ttu-id="1e8ce-112">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-112">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1e8ce-113">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1e8ce-113">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="1e8ce-114">**若要變更可用性群組的可用性模式**</span><span class="sxs-lookup"><span data-stu-id="1e8ce-114">**To change the availability mode of an availability group**</span></span>  
  
1.  <span data-ttu-id="1e8ce-115">在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-115">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="1e8ce-116">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-116">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="1e8ce-117">按一下要變更複本的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-117">Click the availability group whose replica you want to change.</span></span>  
  
4.  <span data-ttu-id="1e8ce-118">以滑鼠右鍵按一下複本，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-118">Right-click the replica, and click **Properties**.</span></span>  
  
5.  <span data-ttu-id="1e8ce-119">在 **[可用性複本屬性]** 對話方塊中，使用 **[可用性模式]** 下拉式清單來變更此複本的可用性模式。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-119">In the **Availability Replica Properties** dialog box, use the **Availability mode** drop list to change the availability mode of this replica.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1e8ce-120">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1e8ce-120">Using Transact-SQL</span></span>  
 <span data-ttu-id="1e8ce-121">**若要變更可用性群組的可用性模式**</span><span class="sxs-lookup"><span data-stu-id="1e8ce-121">**To change the availability mode of an availability group**</span></span>  
  
1.  <span data-ttu-id="1e8ce-122">連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-122">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="1e8ce-123">使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 陳述式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1e8ce-123">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="1e8ce-124">ALTER AVAILABILITY GROUP *群組名稱* MODIFY REPLICA ON '*伺服器名稱*'</span><span class="sxs-lookup"><span data-stu-id="1e8ce-124">ALTER AVAILABILITY GROUP *group_name* MODIFY REPLICA ON '*server_name*'</span></span>  
  
     <span data-ttu-id="1e8ce-125">WITH ( {</span><span class="sxs-lookup"><span data-stu-id="1e8ce-125">WITH ( {</span></span>  
  
     <span data-ttu-id="1e8ce-126">AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }</span><span class="sxs-lookup"><span data-stu-id="1e8ce-126">AVAILABILITY_MODE = { SYNCHRONOUS_COMMIT | ASYNCHRONOUS_COMMIT }</span></span>  
  
     <span data-ttu-id="1e8ce-127">| FAILOVER_MODE = { AUTOMATIC | MANUAL }</span><span class="sxs-lookup"><span data-stu-id="1e8ce-127">| FAILOVER_MODE = { AUTOMATIC | MANUAL }</span></span>  
  
     <span data-ttu-id="1e8ce-128">} )</span><span class="sxs-lookup"><span data-stu-id="1e8ce-128">} )</span></span>  
  
     <span data-ttu-id="1e8ce-129">其中*group_name*是可用性群組的名稱，而*server_name*是裝載要修改之複本的伺服器實例名稱。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-129">where *group_name* is the name of the availability group and *server_name* is the name of the server instance that hosts the replica to be modified.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1e8ce-130">只有當您同時指定 AVAILABILITY_MODE = SYNCHRONOUS_COMMIT 時，才支援 FAILOVER_MODE = AUTOMATIC。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-130">FAILOVER_MODE = AUTOMATIC is supported only if you also specify AVAILABILITY_MODE = SYNCHRONOUS_COMMIT.</span></span>  
  
     <span data-ttu-id="1e8ce-131">下列範例 (在 `AccountsAG` 可用性群組的主要複本上輸入) 會針對 `INSTANCE09` 伺服器執行個體上裝載的複本，將可用性和容錯移轉模式分別變更為同步認可和自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-131">The following example, entered on the primary replica of the `AccountsAG` availability group, changes the availability and failover modes to synchronous commit and automatic failover, respectively, for the replica hosted by the `INSTANCE09` server instance.</span></span>  
  
    ```  
  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (AVAILABILITY_MODE = SYNCHRONOUS_COMMIT);  
    ALTER AVAILABILITY GROUP AccountsAG MODIFY REPLICA ON 'INSTANCE09'  
       WITH (FAILOVER_MODE = AUTOMATIC);  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="1e8ce-132">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1e8ce-132">Using PowerShell</span></span>

### <a name="to-change-the-availability-mode-of-an-availability-group"></a><span data-ttu-id="1e8ce-133">若要變更可用性群組的可用性模式</span><span class="sxs-lookup"><span data-stu-id="1e8ce-133">To change the availability mode of an availability group</span></span>
  
1.  <span data-ttu-id="1e8ce-134">變更目錄 (`cd`) 為裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-134">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="1e8ce-135">使用 `Set-SqlAvailabilityReplica` 指令程式搭配 `AvailabilityMode` 參數，以及選擇性的 `FailoverMode` 參數。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-135">Use the `Set-SqlAvailabilityReplica` cmdlet with the `AvailabilityMode` parameter and, optionally, the `FailoverMode` parameter.</span></span>  
  
     <span data-ttu-id="1e8ce-136">例如，下列命令會將可用性群組 `MyReplica` 中的複本 `MyAg` 修改成使用同步認可的可用性模式並且支援自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-136">For example, the following command modifies the replica `MyReplica` in the availability group `MyAg` to use synchronous-commit availability mode and to support automatic failover.</span></span>  
  
    ```powershell
    Set-SqlAvailabilityReplica -AvailabilityMode "SynchronousCommit" -FailoverMode "Automatic" `   
     -Path SQLSERVER:\Sql\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="1e8ce-137">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-137">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="1e8ce-138">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-138">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
<span data-ttu-id="1e8ce-139">若要設定及使用 SQL Server PowerShell 提供者，請參閱[SQL Server PowerShell 提供者](../../../powershell/sql-server-powershell-provider.md)。</span><span class="sxs-lookup"><span data-stu-id="1e8ce-139">To set up and use the SQL Server PowerShell provider, see [SQL Server PowerShell Provider](../../../powershell/sql-server-powershell-provider.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="1e8ce-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e8ce-140">See Also</span></span>  
 <span data-ttu-id="1e8ce-141">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1e8ce-141">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="1e8ce-142">[可用性模式 (AlwaysOn 可用性群組) ](availability-modes-always-on-availability-groups.md) </span><span class="sxs-lookup"><span data-stu-id="1e8ce-142">[Availability Modes (AlwaysOn Availability Groups)](availability-modes-always-on-availability-groups.md) </span></span>  
 [<span data-ttu-id="1e8ce-143">容錯移轉和容錯移轉模式 &#40;AlwaysOn 可用性群組&#41;</span><span class="sxs-lookup"><span data-stu-id="1e8ce-143">Failover and Failover Modes &#40;AlwaysOn Availability Groups&#41;</span></span>](failover-and-failover-modes-always-on-availability-groups.md)  
