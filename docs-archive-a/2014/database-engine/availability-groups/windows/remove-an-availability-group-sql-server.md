---
title: 移除可用性群組 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.deleteag.f1
helpviewer_keywords:
- Availability Groups [SQL Server], removing
- Availability Groups [SQL Server], dropping
ms.assetid: 4b7f7f62-43a3-49db-a72e-22d4d7c2ddbb
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c17b7d5b362d8b4030d66ebf7ba0e425495410e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593600"
---
# <a name="remove-an-availability-group-sql-server"></a><span data-ttu-id="9048f-102">移除可用性群組 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="9048f-102">Remove an Availability Group (SQL Server)</span></span>
  <span data-ttu-id="9048f-103">此主題描述如何使用 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]、[!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 中的 PowerShell，刪除 (卸除) AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9048f-103">This topic describes how to delete (drop) an AlwaysOn availability group by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="9048f-104">如果當您刪除可用性群組時，裝載其中一個可用性複本的伺服器執行個體離線，則在回到線上之後此伺服器執行個體將會卸除本機可用性複本。</span><span class="sxs-lookup"><span data-stu-id="9048f-104">If a server instance that hosts one of the availability replicas is offline when you delete an availability group, after coming online, the server instance will drop the local availability replica.</span></span> <span data-ttu-id="9048f-105">卸除可用性群組，會刪除任何關聯的可用性群組接聽程式。</span><span class="sxs-lookup"><span data-stu-id="9048f-105">Dropping an availability group deletes any associated availability group listener.</span></span>  
  
 <span data-ttu-id="9048f-106">請注意，必要時您可以從任何擁有可用性群組之正確安全性認證的 Windows Server 容錯移轉叢集 (WSFC) 節點中卸除可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9048f-106">Note that, if necessary, you can drop an availability group from any Windows Server Failover Clustering (WSFC) node that possesses the correct security credentials for the availability group.</span></span> <span data-ttu-id="9048f-107">如此一來，當可用性群組沒有任何可用性複本存在時，就可以刪除此可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9048f-107">This enables you to delete an availability group when none of its availability replicas remain.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="9048f-108">如果可能的話，只在連接主控主要複本的伺服器執行個體時移除可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9048f-108">If possible, remove the availability group only while connected to the server instance that hosts the primary replica.</span></span> <span data-ttu-id="9048f-109">從主要複本卸除可用性群組時，就可以在舊的主要資料庫中進行變更 (沒有高可用性保護)。</span><span class="sxs-lookup"><span data-stu-id="9048f-109">When the availability group is dropped from the primary replica, changes are allowed in the former primary databases (without high availability protection).</span></span> <span data-ttu-id="9048f-110">從次要複本刪除可用性群組會讓主要複本處於 RESTORING 狀態，而且不允許對資料庫進行變更。</span><span class="sxs-lookup"><span data-stu-id="9048f-110">Deleting an availability group from a secondary replica leaves the primary replica in the RESTORING state, and changes are not allowed on the databases.</span></span>  
  
-   <span data-ttu-id="9048f-111">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="9048f-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="9048f-112">限制與建議</span><span class="sxs-lookup"><span data-stu-id="9048f-112">Limitations and Recommendations</span></span>](#Restrictions)  
  
     [<span data-ttu-id="9048f-113">安全性</span><span class="sxs-lookup"><span data-stu-id="9048f-113">Security</span></span>](#Security)  
  
-   <span data-ttu-id="9048f-114">**使用下列方法刪除可用性群組：**</span><span class="sxs-lookup"><span data-stu-id="9048f-114">**To delete an availability group, using:**</span></span>  
  
     [<span data-ttu-id="9048f-115">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9048f-115">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="9048f-116">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9048f-116">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="9048f-117">PowerShell</span><span class="sxs-lookup"><span data-stu-id="9048f-117">PowerShell</span></span>](#PowerShellProcedure)  
  
-   [<span data-ttu-id="9048f-118">相關內容</span><span class="sxs-lookup"><span data-stu-id="9048f-118">Related Content</span></span>](#RelatedContent)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="9048f-119">開始之前</span><span class="sxs-lookup"><span data-stu-id="9048f-119">Before You Begin</span></span>  
  
###  <a name="limitations-and-recommendations"></a><a name="Restrictions"></a><span data-ttu-id="9048f-120">限制與建議</span><span class="sxs-lookup"><span data-stu-id="9048f-120">Limitations and Recommendations</span></span>  
  
-   <span data-ttu-id="9048f-121">當可用性群組已上線時，從次要複本刪除它會導致主要複本轉換為 RESTORING 狀態。</span><span class="sxs-lookup"><span data-stu-id="9048f-121">When the availability group is online, deleting it from a secondary replica causes the primary replica to transition to the RESTORING state.</span></span> <span data-ttu-id="9048f-122">因此，如果可能的話，只能從裝載主要複本的伺服器執行個體中移除可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9048f-122">Therefore, if possible, remove the availability group only from the server instance that hosts the primary replica.</span></span>  
  
-   <span data-ttu-id="9048f-123">如果您要刪除可用性群組的電腦已經從 WSFC 容錯移轉叢集中移除或逐出，則只會在本機刪除此可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9048f-123">If you delete an availability group from a computer that has been removed or evicted from the WSFC failover cluster, the availability group is only deleted locally.</span></span>  
  
-   <span data-ttu-id="9048f-124">避免在 Windows Server 容錯移轉叢集 (WSFC) 叢集沒有仲裁時卸除可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9048f-124">Avoid dropping an availability group when the Windows Server Failover Clustering (WSFC) cluster has no quorum.</span></span> <span data-ttu-id="9048f-125">如果您必須在叢集缺少仲裁時卸除可用性群組，儲存在叢集中的中繼資料可用性群組並不會移除。</span><span class="sxs-lookup"><span data-stu-id="9048f-125">If you must drop an availability group while the cluster lacks quorum, the metadata availability group that is stored in the cluster is not removed.</span></span> <span data-ttu-id="9048f-126">在叢集重新取得仲裁之後，您將需要再次卸除可用性群組，以便從 WSFC 叢集中將它移除。</span><span class="sxs-lookup"><span data-stu-id="9048f-126">After the cluster regains quorum, you will need to drop the availability group again to remove it from the WSFC cluster.</span></span>  
  
-   <span data-ttu-id="9048f-127">在次要複本上，只有在緊急狀況下才可使用 DROP AVAILABILITY GROUP。</span><span class="sxs-lookup"><span data-stu-id="9048f-127">On a secondary replica, DROP AVAILABILITY GROUP should only be used only for emergency purposes.</span></span> <span data-ttu-id="9048f-128">這是因為卸除可用性群組會讓可用性群組離線。</span><span class="sxs-lookup"><span data-stu-id="9048f-128">This is because dropping an availability group takes the availability group offline.</span></span> <span data-ttu-id="9048f-129">如果您從次要複本卸除可用性群組，主要複本就無法判斷 OFFLINE 狀態是因為遺失仲裁、強制容錯移轉或 DROP AVAILABILITY GROUP 命令而發生。</span><span class="sxs-lookup"><span data-stu-id="9048f-129">If you drop the availability group from a secondary replica, the primary replica cannot determine whether the OFFLINE state occurred because of quorum loss, a forced failover, or a DROP AVAILABILITY GROUP command.</span></span> <span data-ttu-id="9048f-130">主要複本會轉換成 RESTORING 狀態，以防止可能的裂腦情況發生。</span><span class="sxs-lookup"><span data-stu-id="9048f-130">The primary replica transitions to the RESTORING state to prevent a possible split-brain situation.</span></span> <span data-ttu-id="9048f-131">如需詳細資訊，請參閱 [How It Works: DROP AVAILABILITY GROUP Behaviors](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (運作方式：DROP AVAILABILITY GROUP 行為) (CSS SQL Server 工程師部落格)。</span><span class="sxs-lookup"><span data-stu-id="9048f-131">For more information, see [How It Works: DROP AVAILABILITY GROUP Behaviors](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (CSS SQL Server Engineers blog).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="9048f-132">Security</span><span class="sxs-lookup"><span data-stu-id="9048f-132">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="9048f-133">權限</span><span class="sxs-lookup"><span data-stu-id="9048f-133">Permissions</span></span>  
 <span data-ttu-id="9048f-134">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="9048f-134">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span> <span data-ttu-id="9048f-135">若要卸除本機伺服器執行個體所未裝載的可用性群組，您需要該可用性群組的 CONTROL SERVER 權限或 CONTROL 權限。</span><span class="sxs-lookup"><span data-stu-id="9048f-135">To drop an availability group that is not hosted by the local server instance you need CONTROL SERVER permission or CONTROL permission on that Availability Group.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="9048f-136">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="9048f-136">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="9048f-137">**若要刪除可用性群組**</span><span class="sxs-lookup"><span data-stu-id="9048f-137">**To delete an availability group**</span></span>  
  
1.  <span data-ttu-id="9048f-138">在 [物件總管] 中，連接到裝載主要複本的伺服器執行個體，可能的話，連接到擁有可用性群組之正確安全性認證的 WSFC 節點上已啟用 AlwaysOn 可用性群組的另一個伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="9048f-138">In Object Explorer, connect to the server instance that hosts primary replica, if possible, or connect to another server instance that is enabled for AlwaysOn Availability Groups on a WSFC node that possess the correct security credentials for the availability group.</span></span> <span data-ttu-id="9048f-139">展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="9048f-139">Expand the server tree.</span></span>  
  
2.  <span data-ttu-id="9048f-140">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="9048f-140">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="9048f-141">此步驟取決於您要刪除多個可用性群組或只要刪除一個可用性群組，如下所示：</span><span class="sxs-lookup"><span data-stu-id="9048f-141">This step depends on whether you want to delete multiple availability groups or only one availability group, as follows:</span></span>  
  
    -   <span data-ttu-id="9048f-142">若要刪除多個可用性群組 (其主要複本位於連接的伺服器執行個體上)，請使用 [物件總管詳細資料]\*\*\*\* 窗格，檢視及選取要刪除的所有可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9048f-142">To delete multiple availability groups (whose primary replicas are on the connected server instance), use the **Object Explorer Details** pane to view and select all the availability groups that you want to delete.</span></span> <span data-ttu-id="9048f-143">如需詳細資訊，請參閱[使用物件總管詳細資料監視可用性群組 &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="9048f-143">For more information, see [Use the Object Explorer Details to Monitor Availability Groups &#40;SQL Server Management Studio&#41;](use-object-explorer-details-to-monitor-availability-groups.md).</span></span>  
  
    -   <span data-ttu-id="9048f-144">若要刪除單一可用性群組，請在 **[物件總管]** 窗格或 **[物件總管詳細資料]** 窗格中選取它。</span><span class="sxs-lookup"><span data-stu-id="9048f-144">To delete a single availability group, select it in either the **Object Explorer** pane or the **Object Explorer Details** pane.</span></span>  
  
4.  <span data-ttu-id="9048f-145">以滑鼠右鍵按一下一或多個選取的可用性群組，然後選取 [刪除]\*\*\*\* 命令。</span><span class="sxs-lookup"><span data-stu-id="9048f-145">Right-click the selected availability group or groups, and select the **Delete** command.</span></span>  
  
5.  <span data-ttu-id="9048f-146">在 **[移除可用性群組]** 對話方塊中，刪除所有列出的可用性群組，按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="9048f-146">In the **Remove Availability Group** dialog box, to delete all the listed availability groups, click **OK**.</span></span> <span data-ttu-id="9048f-147">如果您不要移除所有列出的可用性群組，請按一下 **[取消]**。</span><span class="sxs-lookup"><span data-stu-id="9048f-147">If you do not want to remove all the listed availability groups, click **Cancel**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="9048f-148">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="9048f-148">Using Transact-SQL</span></span>  
 <span data-ttu-id="9048f-149">**若要刪除可用性群組**</span><span class="sxs-lookup"><span data-stu-id="9048f-149">**To delete an availability group**</span></span>  
  
1.  <span data-ttu-id="9048f-150">連接到裝載主要複本的伺服器執行個體，可能的話，連接到擁有可用性群組之正確安全性認證的 WSFC 節點上已啟用 AlwaysOn 可用性群組的另一個伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="9048f-150">Connect to the server instance that hosts the primary replica, if possible, or connect to another server instance that is enabled for AlwaysOn Availability Groups on a WSFC node that possess the correct security credentials for the availability group.</span></span>  
  
2.  <span data-ttu-id="9048f-151">使用 [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) 陳述式，如下所示。</span><span class="sxs-lookup"><span data-stu-id="9048f-151">Use the [DROP AVAILABILITY GROUP](/sql/t-sql/statements/drop-availability-group-transact-sql) statement, as follows</span></span>  
  
     <span data-ttu-id="9048f-152">DROP AVAILABILITY GROUP *group_name*</span><span class="sxs-lookup"><span data-stu-id="9048f-152">DROP AVAILABILITY GROUP *group_name*</span></span>  
  
     <span data-ttu-id="9048f-153">其中 *group_name* 是要卸除的可用性群組名稱。</span><span class="sxs-lookup"><span data-stu-id="9048f-153">where *group_name* is the name of the availability group to be dropped.</span></span>  
  
     <span data-ttu-id="9048f-154">下列範例會刪除 `MyAG` 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9048f-154">The following example deletes the `MyAG` availability group.</span></span>  
  
    ```sql
    DROP AVAILABILITY GROUP MyAG;  
    ```  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="9048f-155">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="9048f-155">Using PowerShell</span></span>  
 <span data-ttu-id="9048f-156">**若要刪除可用性群組**</span><span class="sxs-lookup"><span data-stu-id="9048f-156">**To delete an availability group**</span></span>  
  
 <span data-ttu-id="9048f-157">在 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell 提供者內：</span><span class="sxs-lookup"><span data-stu-id="9048f-157">In the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell provider:</span></span>  
  
1.  <span data-ttu-id="9048f-158">將目錄切換到 (`cd`) 裝載主要複本的伺服器執行個體，可能的話，連接到擁有可用性群組之正確安全性認證的 WSFC 節點上已啟用 AlwaysOn 可用性群組的另一個伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="9048f-158">Change directory (`cd`) to the server instance that hosts the primary replica, if possible, or connect to another server instance that is enabled for AlwaysOn Availability Groups on a WSFC node that possess the correct security credentials for the availability group.</span></span>  
  
2.  <span data-ttu-id="9048f-159">使用 **Remove-SqlAvailabilityGroup** Cmdlet。</span><span class="sxs-lookup"><span data-stu-id="9048f-159">Use the **Remove-SqlAvailabilityGroup** cmdlet.</span></span>  
  
     <span data-ttu-id="9048f-160">例如，下列命令會移除名為 `MyAg`的可用性群組。</span><span class="sxs-lookup"><span data-stu-id="9048f-160">For example, the following command removes the availability group named `MyAg`.</span></span> <span data-ttu-id="9048f-161">此命令可以在裝載可用性群組之可用性複本的任何伺服器執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="9048f-161">This command can be executed on any server instance that hosts an availability replica for the availability group.</span></span>  
  
    ```powershell
    Remove-SqlAvailabilityGroup -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="9048f-162">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="9048f-162">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="9048f-163">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="9048f-163">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="9048f-164">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="9048f-164">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="9048f-165">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="9048f-165">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="9048f-166">相關內容</span><span class="sxs-lookup"><span data-stu-id="9048f-166">Related Content</span></span>  
  
-   <span data-ttu-id="9048f-167">[How It Works: DROP AVAILABILITY GROUP Behaviors](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (運作方式：DROP AVAILABILITY GROUP 行為) (CSS SQL Server 工程師部落格)</span><span class="sxs-lookup"><span data-stu-id="9048f-167">[How It Works: DROP AVAILABILITY GROUP Behaviors](https://blogs.msdn.com/b/psssql/archive/2012/06/13/how-it-works-drop-availability-group-behaviors.aspx) (CSS SQL Server Engineers blog)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9048f-168">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9048f-168">See Also</span></span>  
 <span data-ttu-id="9048f-169">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="9048f-169">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="9048f-170">建立及設定可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="9048f-170">Creation and Configuration of Availability Groups &#40;SQL Server&#41;</span></span>](creation-and-configuration-of-availability-groups-sql-server.md)  
