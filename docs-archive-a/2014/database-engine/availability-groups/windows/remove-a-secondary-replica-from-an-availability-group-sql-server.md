---
title: 將次要複本從可用性群組移除 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.removesecondaryar.f1
helpviewer_keywords:
- Availability Groups [SQL Server], availability replicas
- Availability Groups [SQL Server], configuring
ms.assetid: 35ddc8b6-3e7c-4417-9a0a-d4987a09ddf7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e3f2b35ec9cf27f2f7b23714a41665f2709837a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593602"
---
# <a name="remove-a-secondary-replica-from-an-availability-group-sql-server"></a><span data-ttu-id="462a6-102">將次要複本從可用性群組移除 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="462a6-102">Remove a Secondary Replica from an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="462a6-103">本主題描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、 [!INCLUDE[tsql](../../../includes/tsql-md.md)]或 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中的 PowerShell，將次要複本從 AlwaysOn 可用性群組中移除。</span><span class="sxs-lookup"><span data-stu-id="462a6-103">This topic describes how to remove a secondary replica from an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span>  
  
-   <span data-ttu-id="462a6-104">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="462a6-104">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="462a6-105">限制事項</span><span class="sxs-lookup"><span data-stu-id="462a6-105">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="462a6-106">先決條件</span><span class="sxs-lookup"><span data-stu-id="462a6-106">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="462a6-107">安全性</span><span class="sxs-lookup"><span data-stu-id="462a6-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="462a6-108">**若要使用下列項目移除次要複本：**</span><span class="sxs-lookup"><span data-stu-id="462a6-108">**To remove a secondary replica, using:**</span></span>  
  
     [<span data-ttu-id="462a6-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="462a6-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="462a6-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="462a6-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="462a6-111">PowerShell</span><span class="sxs-lookup"><span data-stu-id="462a6-111">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="462a6-112">**後續操作：**  [移除次要複本之後](#PostBestPractices)</span><span class="sxs-lookup"><span data-stu-id="462a6-112">**Follow Up:**  [After Removing a Secondary Replica](#PostBestPractices)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="462a6-113">開始之前</span><span class="sxs-lookup"><span data-stu-id="462a6-113">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="462a6-114">限制事項</span><span class="sxs-lookup"><span data-stu-id="462a6-114">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="462a6-115">只有在主要複本上才支援這個工作。</span><span class="sxs-lookup"><span data-stu-id="462a6-115">This task is supported only on the primary replica.</span></span>  
  
-   <span data-ttu-id="462a6-116">只有次要複本可以從可用性群組中移除。</span><span class="sxs-lookup"><span data-stu-id="462a6-116">Only a secondary replica can be removed from an availability group.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="462a6-117">必要條件</span><span class="sxs-lookup"><span data-stu-id="462a6-117">Prerequisites</span></span>  
  
-   <span data-ttu-id="462a6-118">您必須連接到裝載可用性群組之主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="462a6-118">You must be connected to the server instance that hosts the primary replica of the availability group.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="462a6-119">Security</span><span class="sxs-lookup"><span data-stu-id="462a6-119">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="462a6-120">權限</span><span class="sxs-lookup"><span data-stu-id="462a6-120">Permissions</span></span>  
 <span data-ttu-id="462a6-121">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="462a6-121">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="462a6-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="462a6-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="462a6-123">**若要移除次要複本**</span><span class="sxs-lookup"><span data-stu-id="462a6-123">**To remove a secondary replica**</span></span>  
  
1.  <span data-ttu-id="462a6-124">在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="462a6-124">In Object Explorer, connect to the server instance that hosts the primary replica, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="462a6-125">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="462a6-125">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="462a6-126">選取可用性群組，然後展開 **[可用性複本]** 節點。</span><span class="sxs-lookup"><span data-stu-id="462a6-126">Select the availability group, and expand the **Availability Replicas** node.</span></span>  
  
4.  <span data-ttu-id="462a6-127">此步驟取決於您要移除多個複本或只要移除一個複本，如下所示：</span><span class="sxs-lookup"><span data-stu-id="462a6-127">This step depends on whether you want to remove multiple replicas or only one replica, as follows:</span></span>  
  
    -   <span data-ttu-id="462a6-128">若要移除多個複本，請使用 **[物件總管詳細資料]** 窗格檢視及選取您要移除的所有複本。</span><span class="sxs-lookup"><span data-stu-id="462a6-128">To remove multiple replicas, use the **Object Explorer Details** pane to view and select all the replicas that you want to remove.</span></span> <span data-ttu-id="462a6-129">如需詳細資訊，請參閱[使用物件總管詳細資料監視可用性群組 &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="462a6-129">For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="462a6-130">若要移除單一複本，請在 **[物件總管]** 窗格或 **[物件總管詳細資料]** 窗格中選取它。</span><span class="sxs-lookup"><span data-stu-id="462a6-130">To remove a single replica, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.</span></span>  
  
5.  <span data-ttu-id="462a6-131">以滑鼠右鍵按一下選取的一或多個次要複本，然後在命令功能表中選取 [從可用性群組移除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="462a6-131">Right-click the selected secondary replica or replicas, and select **Remove from Availability Group** in the command menu.</span></span>  
  
6.  <span data-ttu-id="462a6-132">在 **[從可用性群組移除次要複本]** 對話方塊中，若要移除所有列出的次要複本，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="462a6-132">In the **Remove Secondary Replicas from Availability Group** dialog box, to remove all the listed secondary replicas, click **OK**.</span></span> <span data-ttu-id="462a6-133">如果您不要移除所有列出的複本，請按一下 **[取消]**。</span><span class="sxs-lookup"><span data-stu-id="462a6-133">If you do not want to remove all the listed replicas, click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="462a6-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="462a6-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="462a6-135">**若要移除次要複本**</span><span class="sxs-lookup"><span data-stu-id="462a6-135">**To remove a secondary replica**</span></span>  
  
1.  <span data-ttu-id="462a6-136">連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="462a6-136">Connect to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="462a6-137">使用 [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) 陳述式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="462a6-137">Use the [ALTER AVAILABILITY GROUP](/sql/t-sql/statements/alter-availability-group-transact-sql) statement, as follows:</span></span>  
  
     <span data-ttu-id="462a6-138">ALTER AVAILABILITY GROUP *group_name* REMOVE REPLICA ON '*instance_name*' [,...*n*]</span><span class="sxs-lookup"><span data-stu-id="462a6-138">ALTER AVAILABILITY GROUP *group_name* REMOVE REPLICA ON '*instance_name*' [,...*n*]</span></span>  
  
     <span data-ttu-id="462a6-139">其中 *group_name* 是可用性群組的名稱，而 *instance_name* 是次要複本所在的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="462a6-139">where *group_name* is the name of the availability group and *instance_name* is the server instance where the secondary replica is located.</span></span>  
  
     <span data-ttu-id="462a6-140">下列範例會將次要複本從 *MyAG* 可用性群組中移除。</span><span class="sxs-lookup"><span data-stu-id="462a6-140">The following example removes a secondary replica from the *MyAG* availability group.</span></span> <span data-ttu-id="462a6-141">目標次要複本位於名為 *COMPUTER02* 之電腦上的 *HADR_INSTANCE*具名伺服器執行個體上。</span><span class="sxs-lookup"><span data-stu-id="462a6-141">The target secondary replica is located on a server instance named *HADR_INSTANCE* on a computer named *COMPUTER02*.</span></span>  
  
    ```sql
    ALTER AVAILABILITY GROUP MyAG REMOVE REPLICA ON 'COMPUTER02\HADR_INSTANCE';  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="462a6-142">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="462a6-142">Using PowerShell</span></span>  
 <span data-ttu-id="462a6-143">**若要移除次要複本**</span><span class="sxs-lookup"><span data-stu-id="462a6-143">**To remove a secondary replica**</span></span>  
  
1.  <span data-ttu-id="462a6-144">變更目錄 (`cd`) 為裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="462a6-144">Change directory (`cd`) to the server instance that hosts the primary replica.</span></span>  
  
2.  <span data-ttu-id="462a6-145">使用 **Remove-SqlAvailabilityReplica** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="462a6-145">Use the **Remove-SqlAvailabilityReplica** cmdlet.</span></span>  
  
     <span data-ttu-id="462a6-146">例如，下列命令會將伺服器上的 `MyReplica` 可用性複本從名為 `MyAg`的可用性群組中移除。</span><span class="sxs-lookup"><span data-stu-id="462a6-146">For example, the following command removes the availability replica on the server `MyReplica` from the availability group named `MyAg`.</span></span>  <span data-ttu-id="462a6-147">此命令必須在裝載可用性群組之主要複本的伺服器執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="462a6-147">This command must be run on the server instance that hosts the primary replica of the availability group.</span></span>  
  
    ```powershell
    Remove-SqlAvailabilityReplica -Path SQLSERVER:\SQL\PrimaryServer\InstanceName\AvailabilityGroups\MyAg\AvailabilityReplicas\MyReplica  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="462a6-148">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="462a6-148">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="462a6-149">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="462a6-149">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="462a6-150">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="462a6-150">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="462a6-151">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="462a6-151">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-after-removing-a-secondary-replica"></a><a name="PostBestPractices"></a> <span data-ttu-id="462a6-152">追蹤：移除次要複本之後</span><span class="sxs-lookup"><span data-stu-id="462a6-152">Follow Up: After Removing a Secondary Replica</span></span>  
 <span data-ttu-id="462a6-153">如果您指定目前無法使用的複本，當複本連線時，將會發現該複本已經遭到移除。</span><span class="sxs-lookup"><span data-stu-id="462a6-153">If you specify a replica that is currently unavailable, when the replica comes online, it will discover that it has been removed.</span></span>  
  
 <span data-ttu-id="462a6-154">移除複本會使它停止接收資料。</span><span class="sxs-lookup"><span data-stu-id="462a6-154">Removing a replica causes it to stop receiving data.</span></span> <span data-ttu-id="462a6-155">當次要複本確認它已從全域存放區移除之後，複本會從其資料庫移除可用性群組設定，處於 RECOVERING 狀態時，這些設定仍然存在於本機伺服器執行個體上。</span><span class="sxs-lookup"><span data-stu-id="462a6-155">After a secondary replica confirms that it has been removed from the global store, the replica removes the availability group settings from its databases, which remain on the local server instance in the RECOVERING state.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="462a6-156">另請參閱</span><span class="sxs-lookup"><span data-stu-id="462a6-156">See Also</span></span>  
 <span data-ttu-id="462a6-157">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="462a6-157">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 <span data-ttu-id="462a6-158">[將次要複本加入至可用性群組 &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="462a6-158">[Add a Secondary Replica to an Availability Group &#40;SQL Server&#41;](add-a-secondary-replica-to-an-availability-group-sql-server.md) </span></span>  
 [<span data-ttu-id="462a6-159">移除可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="462a6-159">Remove an Availability Group &#40;SQL Server&#41;</span></span>](remove-an-availability-group-sql-server.md)  
