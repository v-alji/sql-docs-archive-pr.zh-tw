---
title: 暫止可用性資料庫 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.suspenddatamove.f1
helpviewer_keywords:
- secondary databases [SQL Server], in availability group
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], suspending a database
- Availability Groups [SQL Server], databases
ms.assetid: 86858982-6af1-4e80-9a93-87451f0d7ee9
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 49afe868a509f84160fc1ad154135e8e67f6900a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708649"
---
# <a name="suspend-an-availability-database-sql-server"></a><span data-ttu-id="1c489-102">暫止可用性資料庫 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="1c489-102">Suspend an Availability Database (SQL Server)</span></span>
  <span data-ttu-id="1c489-103">您可以使用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 [!INCLUDE[tsql](../../../includes/tsql-md.md)]的 PowerShell，暫停 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中的可用性資料庫。</span><span class="sxs-lookup"><span data-stu-id="1c489-103">You can suspend an availability database in [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="1c489-104">請注意，暫停命令必須在裝載要暫停或回復之資料庫的伺服器執行個體上發出。</span><span class="sxs-lookup"><span data-stu-id="1c489-104">Note that a suspend command needs to be issued on the server instance that hosts the database to be suspended or resumed.</span></span>  
  
 <span data-ttu-id="1c489-105">暫停命令的效果取決於您暫停的是次要資料庫或主要資料庫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="1c489-105">The effect of a suspend command depends on whether you suspend a secondary database or a primary database, as follows:</span></span>  
  
|<span data-ttu-id="1c489-106">暫停的資料庫</span><span class="sxs-lookup"><span data-stu-id="1c489-106">Suspended Database</span></span>|<span data-ttu-id="1c489-107">暫停命令的效果</span><span class="sxs-lookup"><span data-stu-id="1c489-107">Effect of Suspend Command</span></span>|  
|------------------------|-------------------------------|  
|<span data-ttu-id="1c489-108">次要資料庫</span><span class="sxs-lookup"><span data-stu-id="1c489-108">Secondary database</span></span>|<span data-ttu-id="1c489-109">只有本機次要資料庫會暫停，而且其同步處理狀態會變成 NOT SYNCHRONIZING。</span><span class="sxs-lookup"><span data-stu-id="1c489-109">Only the local secondary database is suspended and its synchronization state becomes NOT SYNCHRONIZING.</span></span> <span data-ttu-id="1c489-110">其他次要資料庫不受影響。</span><span class="sxs-lookup"><span data-stu-id="1c489-110">Other secondary databases are not affected.</span></span> <span data-ttu-id="1c489-111">暫停的資料庫會停止接收和套用資料 (記錄檔記錄)，並且開始落後於主要資料庫。</span><span class="sxs-lookup"><span data-stu-id="1c489-111">The suspended database stops receiving and applying data (log records) and begins to fall behind the primary database.</span></span> <span data-ttu-id="1c489-112">可讀取次要複本上的現有連接會保持可用狀態。</span><span class="sxs-lookup"><span data-stu-id="1c489-112">Existing connections on the readable secondary remain usable.</span></span> <span data-ttu-id="1c489-113">在資料移動繼續執行之前，不允許可讀取次要複本上已暫停之資料庫的新連接。</span><span class="sxs-lookup"><span data-stu-id="1c489-113">New connections to the suspended database on the readable secondary are not allowed until data movement is resumed.</span></span><br /><br /> <span data-ttu-id="1c489-114">主要資料庫仍然可用。</span><span class="sxs-lookup"><span data-stu-id="1c489-114">The primary database remains available.</span></span> <span data-ttu-id="1c489-115">如果您暫停每個對應的次要資料庫，則主要資料庫會公開執行。</span><span class="sxs-lookup"><span data-stu-id="1c489-115">If you suspend each of the corresponding secondary databases, the primary database runs exposed.</span></span><br /><br /> <span data-ttu-id="1c489-116">**\*\* 重要事項 \*\*** 次要資料庫暫停期間，所對應之主要資料庫的傳送佇列將會累積未傳送的交易記錄檔記錄。</span><span class="sxs-lookup"><span data-stu-id="1c489-116">**\*\* Important \*\*** While a secondary database is suspended, the send queue of the corresponding primary database will accumulate unsent transaction log records.</span></span> <span data-ttu-id="1c489-117">次要複本的連接會傳回在資料移動暫停時可用的資料。</span><span class="sxs-lookup"><span data-stu-id="1c489-117">Connections to the secondary replica return data that was available at the time the data movement was suspended.</span></span>|  
|<span data-ttu-id="1c489-118">主要資料庫</span><span class="sxs-lookup"><span data-stu-id="1c489-118">Primary database</span></span>|<span data-ttu-id="1c489-119">主要資料庫會停止將資料移動到每個連接的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="1c489-119">The primary database stops data movement to every connected secondary database.</span></span> <span data-ttu-id="1c489-120">主要資料庫會繼續以公開模式執行。</span><span class="sxs-lookup"><span data-stu-id="1c489-120">The primary database continues running, in an exposed mode.</span></span> <span data-ttu-id="1c489-121">主要資料庫仍然可供用戶端使用，而可讀取次要資料庫上的現有連接仍然可以使用，並且可以建立新連接。</span><span class="sxs-lookup"><span data-stu-id="1c489-121">The primary database remains available to clients, and existing connections on a readable secondary remain usable and new connections can be made.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="1c489-122">暫停 AlwaysOn 次要資料庫不會直接影響主要資料庫的可用性，</span><span class="sxs-lookup"><span data-stu-id="1c489-122">Suspending an AlwaysOn secondary database does not directly affect the availability of the primary database.</span></span> <span data-ttu-id="1c489-123">但暫停次要資料庫可能會影響其備援及容錯移轉功能。</span><span class="sxs-lookup"><span data-stu-id="1c489-123">However, suspending a secondary database can impact redundancy and failover capabilities for the primary database.</span></span> <span data-ttu-id="1c489-124">這與資料庫鏡像相反，在資料庫鏡像中，鏡像狀態會在鏡像資料庫和主體資料庫上暫停。</span><span class="sxs-lookup"><span data-stu-id="1c489-124">This is in contrast to database mirroring, where the mirroring state is suspended on both the mirror database and the principal database.</span></span> <span data-ttu-id="1c489-125">暫停 AlwaysOn 主要資料庫會暫停所有對應次要資料庫上的資料移動，而且該資料庫的備援和容錯移轉功能也會停止，直到主要資料庫繼續為止。</span><span class="sxs-lookup"><span data-stu-id="1c489-125">Suspending an AlwaysOn primary database suspends data movement on all the corresponding secondary databases, and redundancy and failover capabilities cease for that database until the primary database is resumed.</span></span>  
  
-   <span data-ttu-id="1c489-126">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="1c489-126">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="1c489-127">限制事項</span><span class="sxs-lookup"><span data-stu-id="1c489-127">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="1c489-128">先決條件</span><span class="sxs-lookup"><span data-stu-id="1c489-128">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="1c489-129">建議</span><span class="sxs-lookup"><span data-stu-id="1c489-129">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="1c489-130">安全性</span><span class="sxs-lookup"><span data-stu-id="1c489-130">Security</span></span>](#Security)  
  
-   <span data-ttu-id="1c489-131">**若要使用下列項目暫停資料庫：**</span><span class="sxs-lookup"><span data-stu-id="1c489-131">**To suspend a database, using:**</span></span>  
  
-   [<span data-ttu-id="1c489-132">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1c489-132">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="1c489-133">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1c489-133">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="1c489-134">PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c489-134">PowerShell</span></span>](#PowerShellProcedure)  
  
-   <span data-ttu-id="1c489-135">**後續操作：** [避免填滿交易記錄](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="1c489-135">**Follow up:** [Avoiding a Full Transaction Log](#FollowUp)</span></span>  
  
-   [<span data-ttu-id="1c489-136">相關工作</span><span class="sxs-lookup"><span data-stu-id="1c489-136">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="1c489-137">開始之前</span><span class="sxs-lookup"><span data-stu-id="1c489-137">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="1c489-138">限制事項</span><span class="sxs-lookup"><span data-stu-id="1c489-138">Limitations and Restrictions</span></span>  
 <span data-ttu-id="1c489-139">一旦裝載目標資料庫的複本接受 SUSPEND 命令之後，就會將其傳回，但暫停資料庫實際上是以非同步方式進行。</span><span class="sxs-lookup"><span data-stu-id="1c489-139">A SUSPEND command returns as soon as it has been accepted by the replica that hosts the target database, but actually suspending the database occurs asynchronously.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="1c489-140">必要條件</span><span class="sxs-lookup"><span data-stu-id="1c489-140">Prerequisites</span></span>  
 <span data-ttu-id="1c489-141">您必須連接到裝載要暫停之資料庫的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1c489-141">You must be connected to the server instance that hosts the database that you want to suspend.</span></span> <span data-ttu-id="1c489-142">若要暫停主要資料庫和對應的次要資料庫，請連接到裝載主要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1c489-142">To suspend a primary database and the corresponding secondary databases, connect to the server instance that hosts the primary replica.</span></span> <span data-ttu-id="1c489-143">若要暫停次要資料庫，同時保留主要資料庫可用狀態，請連接到次要複本。</span><span class="sxs-lookup"><span data-stu-id="1c489-143">To suspend a secondary database while leaving the primary database available, connect to the secondary replica.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="1c489-144">建議</span><span class="sxs-lookup"><span data-stu-id="1c489-144">Recommendations</span></span>  
 <span data-ttu-id="1c489-145">出現瓶頸時，短暫暫停一個或多個次要資料庫，可能有助於暫時改善主要複本的效能。</span><span class="sxs-lookup"><span data-stu-id="1c489-145">During bottlenecks, suspending one or more secondary databases briefly might be useful to improve performance temporarily on the primary replica.</span></span> <span data-ttu-id="1c489-146">只要次要資料庫保持暫停狀態，對應主要資料庫的交易記錄便無法截斷。</span><span class="sxs-lookup"><span data-stu-id="1c489-146">As long as a secondary database remains suspended, the transaction log of the corresponding primary database cannot be truncated.</span></span> <span data-ttu-id="1c489-147">這會導致記錄檔記錄在主要資料庫上累積。</span><span class="sxs-lookup"><span data-stu-id="1c489-147">This causes log records to accumulate on the primary database.</span></span> <span data-ttu-id="1c489-148">因此，我們建議您盡快恢復 (或移除) 暫停的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="1c489-148">Therefore, we recommend that you resume, or remove, a suspended secondary database quickly.</span></span> <span data-ttu-id="1c489-149">如需詳細資訊，請參閱本主題稍後的[後續操作：避免填滿交易記錄](#FollowUp)。</span><span class="sxs-lookup"><span data-stu-id="1c489-149">For more information, see [Follow up: Avoiding a Full Transaction Log](#FollowUp), later in this topic.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="1c489-150">Security</span><span class="sxs-lookup"><span data-stu-id="1c489-150">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="1c489-151">權限</span><span class="sxs-lookup"><span data-stu-id="1c489-151">Permissions</span></span>  
 <span data-ttu-id="1c489-152">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="1c489-152">Requires ALTER permission on the database.</span></span>  
  
 <span data-ttu-id="1c489-153">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="1c489-153">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="1c489-154">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="1c489-154">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="1c489-155">**若要暫停資料庫**</span><span class="sxs-lookup"><span data-stu-id="1c489-155">**To suspend a database**</span></span>  
  
1.  <span data-ttu-id="1c489-156">在 [物件總管] 中，連接到裝載您要暫停資料庫之可用性複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="1c489-156">In Object Explorer, connect to the server instance that hosts the availability replica on which you want to suspend a database, and expand the server tree.</span></span> <span data-ttu-id="1c489-157">如需詳細資訊，請參閱本主題前面的＜ [必要條件](#Prerequisites)＞。</span><span class="sxs-lookup"><span data-stu-id="1c489-157">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="1c489-158">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="1c489-158">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="1c489-159">展開可用性群組。</span><span class="sxs-lookup"><span data-stu-id="1c489-159">Expand the availability group.</span></span>  
  
4.  <span data-ttu-id="1c489-160">展開 [可用性資料庫] 節點，以滑鼠右鍵按一下資料庫，然後按一下 [暫停進行資料移動]。</span><span class="sxs-lookup"><span data-stu-id="1c489-160">Expand the **Availability Databases** node, right-click the database, and click **Suspend Data Movement**.</span></span>  
  
5.  <span data-ttu-id="1c489-161">在 **[暫停資料移動]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="1c489-161">In the **Suspend Data Movement** dialog box, click **OK**.</span></span>  
  
     <span data-ttu-id="1c489-162">[物件總管] 會透過變更資料庫圖示以顯示暫停指標，指出資料庫已暫停。</span><span class="sxs-lookup"><span data-stu-id="1c489-162">Object Explorer indicates that the database is suspended by changing  the database icon to display a pause indicator.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1c489-163">若要暫停此複本位置的其他資料庫，請針對每個資料庫重複步驟 4 和 5。</span><span class="sxs-lookup"><span data-stu-id="1c489-163">To suspend additional databases on this replica location, repeat steps 4 and 5  for each database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="1c489-164">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="1c489-164">Using Transact-SQL</span></span>  
 <span data-ttu-id="1c489-165">**若要暫停資料庫**</span><span class="sxs-lookup"><span data-stu-id="1c489-165">**To suspend a database**</span></span>  
  
1.  <span data-ttu-id="1c489-166">連接至裝載您要暫停其資料庫之複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1c489-166">Connect to the server instance that hosts the replica whose database you want to suspend.</span></span> <span data-ttu-id="1c489-167">如需詳細資訊，請參閱本主題前面的＜ [必要條件](#Prerequisites)＞。</span><span class="sxs-lookup"><span data-stu-id="1c489-167">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="1c489-168">使用下列 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)陳述式暫停資料庫：</span><span class="sxs-lookup"><span data-stu-id="1c489-168">Suspend the database by using the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)statement:</span></span>  
  
     <span data-ttu-id="1c489-169">ALTER DATABASE *database_name*設定 HADR 暫止</span><span class="sxs-lookup"><span data-stu-id="1c489-169">ALTER DATABASE *database_name* SET HADR SUSPEND</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="1c489-170">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="1c489-170">Using PowerShell</span></span>  
 <span data-ttu-id="1c489-171">**若要暫停資料庫**</span><span class="sxs-lookup"><span data-stu-id="1c489-171">**To suspend a database**</span></span>  
  
1.  <span data-ttu-id="1c489-172">將目錄切換到 (`cd`) 裝載您要暫停其資料庫之複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="1c489-172">Change directory (`cd`) to the server instance that hosts the replica whose database you want to suspend.</span></span> <span data-ttu-id="1c489-173">如需詳細資訊，請參閱本主題前面的＜ [必要條件](#Prerequisites)＞。</span><span class="sxs-lookup"><span data-stu-id="1c489-173">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="1c489-174">使用 `Suspend-SqlAvailabilityDatabase` 指令程式暫停可用性群組。</span><span class="sxs-lookup"><span data-stu-id="1c489-174">Use the `Suspend-SqlAvailabilityDatabase` cmdlet to suspend the availability group.</span></span>  
  
     <span data-ttu-id="1c489-175">例如，下列命令會針對 `MyDb3` 伺服器執行個體上 `MyAg` 可用性群組中的 `Computer\Instance`可用性資料庫暫停資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="1c489-175">For example, the following command suspends data synchronization for the availability database `MyDb3` in the availability group `MyAg` on the server instance named `Computer\Instance`.</span></span>  
  
    ```powershell
    Suspend-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\Databases\MyDb3  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c489-176">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="1c489-176">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="1c489-177">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="1c489-177">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="1c489-178">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="1c489-178">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="1c489-179">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="1c489-179">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="follow-up-avoiding-a-full-transaction-log"></a><a name="FollowUp"></a> <span data-ttu-id="1c489-180">後續操作：避免填滿交易記錄</span><span class="sxs-lookup"><span data-stu-id="1c489-180">Follow Up: Avoiding a Full Transaction Log</span></span>  
 <span data-ttu-id="1c489-181">一般而言，在資料庫上執行自動檢查點時，交易記錄會在下一個記錄備份之後，截斷至該檢查點。</span><span class="sxs-lookup"><span data-stu-id="1c489-181">Normally, when an automatic checkpoint is performed on a database, its transaction log is truncated to that checkpoint after the next log backup.</span></span> <span data-ttu-id="1c489-182">但在次要資料庫暫停時，所有目前的記錄檔記錄仍在主要資料庫作用中。</span><span class="sxs-lookup"><span data-stu-id="1c489-182">However, while a secondary database is suspended, all of the current log records remain active on the primary database.</span></span> <span data-ttu-id="1c489-183">如果交易記錄已填滿 (因為已達到最大值，或者伺服器執行個體用盡空間)，資料庫就不能再執行其他更新。</span><span class="sxs-lookup"><span data-stu-id="1c489-183">If the transaction log fills up (either because it reaches its maximum size or the server instance runs out of space), the database cannot perform any more updates.</span></span>  
  
 <span data-ttu-id="1c489-184">若要避免這個問題，您應該執行下列其中一項工作：</span><span class="sxs-lookup"><span data-stu-id="1c489-184">To avoid this problem, you should do one of the following:</span></span>  
  
-   <span data-ttu-id="1c489-185">為主要資料庫增加更多的記錄空間。</span><span class="sxs-lookup"><span data-stu-id="1c489-185">Add more log space for the primary database.</span></span>  
  
-   <span data-ttu-id="1c489-186">在日誌填滿之前恢復次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="1c489-186">Resume the secondary database before the log fills up.</span></span> <span data-ttu-id="1c489-187">如需詳細資訊，請參閱本主題稍後的＜ [繼續可用性資料庫 &#40;SQL Server&#41;](resume-an-availability-database-sql-server.md)中的可用性資料庫。</span><span class="sxs-lookup"><span data-stu-id="1c489-187">For more information, see [Resume an Availability Database &#40;SQL Server&#41;](resume-an-availability-database-sql-server.md).</span></span>  
  
-   <span data-ttu-id="1c489-188">移除次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="1c489-188">Remove the secondary database.</span></span> <span data-ttu-id="1c489-189">如需詳細資訊，請參閱[將次要資料庫從可用性群組移除 &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="1c489-189">For more information, see [Remove a Secondary Database from an Availability Group &#40;SQL Server&#41;](remove-a-secondary-database-from-an-availability-group-sql-server.md).</span></span>  
  
 <span data-ttu-id="1c489-190">**若要對寫滿交易記錄進行疑難排解**</span><span class="sxs-lookup"><span data-stu-id="1c489-190">**To troubleshoot a full transaction log**</span></span>  
  
-   [<span data-ttu-id="1c489-191">寫滿交易記錄疑難排解 &#40;SQL Server 錯誤 9002&#41;</span><span class="sxs-lookup"><span data-stu-id="1c489-191">Troubleshoot a Full Transaction Log &#40;SQL Server Error 9002&#41;</span></span>](../../../relational-databases/logs/troubleshoot-a-full-transaction-log-sql-server-error-9002.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="1c489-192">相關工作</span><span class="sxs-lookup"><span data-stu-id="1c489-192">Related Tasks</span></span>  
  
-   [<span data-ttu-id="1c489-193">繼續可用性資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1c489-193">Resume an Availability Database &#40;SQL Server&#41;</span></span>](resume-an-availability-database-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="1c489-194">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c489-194">See Also</span></span>  
 <span data-ttu-id="1c489-195">[AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;](overview-of-always-on-availability-groups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="1c489-195">[Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;](overview-of-always-on-availability-groups-sql-server.md) </span></span>  
 [<span data-ttu-id="1c489-196">繼續可用性資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="1c489-196">Resume an Availability Database &#40;SQL Server&#41;</span></span>](resume-an-availability-database-sql-server.md)  
