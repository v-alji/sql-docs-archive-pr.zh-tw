---
title: 繼續可用性資料庫 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.availabilitygroup.resumedatamove.f1
helpviewer_keywords:
- Availability Groups [SQL Server], resuming a database
- secondary databases [SQL Server], in availability group
- primary databases [SQL Server], in availability group
- Availability Groups [SQL Server], databases
ms.assetid: 20e9147b-e985-4caa-910e-fc4b38dbf9a1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a2279940c2502a310e9dac4448bd6029b6e13dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707897"
---
# <a name="resume-an-availability-database-sql-server"></a><span data-ttu-id="df232-102">繼續可用性資料庫 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="df232-102">Resume an Availability Database (SQL Server)</span></span>
  <span data-ttu-id="df232-103">您可以使用 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 [!INCLUDE[tsql](../../../includes/tsql-md.md)]的 PowerShell，在 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)]中繼續暫停的可用性資料庫。</span><span class="sxs-lookup"><span data-stu-id="df232-103">You can resume a suspended availability database in [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or PowerShell in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)].</span></span> <span data-ttu-id="df232-104">繼續暫停的資料庫會使資料庫處於 SYNCHRONIZING 狀態。</span><span class="sxs-lookup"><span data-stu-id="df232-104">Resuming a suspended database puts the database into the SYNCHRONIZING state.</span></span> <span data-ttu-id="df232-105">繼續主要資料庫也會繼續因為暫停主要資料庫而暫停的任何次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="df232-105">Resuming the primary database also resumes any of its secondary databases that were suspended as the result of suspending the primary database.</span></span> <span data-ttu-id="df232-106">如果在本機 (從裝載次要複本的伺服器執行個體) 暫停任何次要資料庫，該次要資料庫必須在本機繼續。</span><span class="sxs-lookup"><span data-stu-id="df232-106">If any secondary database was suspended locally, from the server instance that hosts the secondary replica, that secondary database must be resumed locally.</span></span> <span data-ttu-id="df232-107">給定的次要資料庫與對應的主要資料庫都處於 SYNCHRONIZING 狀態之後，資料同步處理就會在次要資料庫上繼續。</span><span class="sxs-lookup"><span data-stu-id="df232-107">Once a given secondary database and the corresponding primary database are in the SYNCHRONIZING state, data synchronization resumes on the secondary database.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df232-108">暫停和繼續 AlwaysOn 次要資料庫並不會直接影響主要資料庫的可用性，</span><span class="sxs-lookup"><span data-stu-id="df232-108">Suspending and resuming an AlwaysOn secondary database does not directly affect the availability of the primary database.</span></span> <span data-ttu-id="df232-109">不過暫停次要資料庫可能影響主要資料庫的備援和容錯移轉功能，直到暫停的次要資料庫繼續為止。</span><span class="sxs-lookup"><span data-stu-id="df232-109">However, suspending a secondary database can impact redundancy and failover capabilities for the primary database, until the suspended secondary database is resumed.</span></span> <span data-ttu-id="df232-110">相反的，在資料庫鏡像中，鏡像狀態會在鏡像資料庫和主體資料庫上暫停，直到鏡像繼續為止。</span><span class="sxs-lookup"><span data-stu-id="df232-110">This is in contrast to database mirroring, where the mirroring state is suspended on both the mirror database and the principal database until mirroring is resumed.</span></span> <span data-ttu-id="df232-111">暫停 AlwaysOn 主要資料庫會暫停所有對應次要資料庫上的資料移動，而且該資料庫的備援和容錯移轉功能也會停止，直到主要資料庫繼續為止。</span><span class="sxs-lookup"><span data-stu-id="df232-111">Suspending an AlwaysOn primary database suspends data movement on all the corresponding secondary databases, and redundancy and failover capabilities cease for that database until the primary database is resumed.</span></span>  
  
-   <span data-ttu-id="df232-112">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="df232-112">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="df232-113">限制事項</span><span class="sxs-lookup"><span data-stu-id="df232-113">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="df232-114">先決條件</span><span class="sxs-lookup"><span data-stu-id="df232-114">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="df232-115">安全性</span><span class="sxs-lookup"><span data-stu-id="df232-115">Security</span></span>](#Security)  
  
-   <span data-ttu-id="df232-116">**若要使用下列項目繼續次要資料庫：**</span><span class="sxs-lookup"><span data-stu-id="df232-116">**To resume a secondary database, using:**</span></span>  
  
     [<span data-ttu-id="df232-117">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="df232-117">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="df232-118">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="df232-118">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="df232-119">PowerShell</span><span class="sxs-lookup"><span data-stu-id="df232-119">PowerShell</span></span>](#PowerShellProcedure)  
  
-   [<span data-ttu-id="df232-120">相關工作</span><span class="sxs-lookup"><span data-stu-id="df232-120">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="df232-121">開始之前</span><span class="sxs-lookup"><span data-stu-id="df232-121">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="df232-122">限制事項</span><span class="sxs-lookup"><span data-stu-id="df232-122">Limitations and Restrictions</span></span>  
 <span data-ttu-id="df232-123">一旦裝載目標資料庫的複本接受 RESUME 命令之後，就會將其傳回，但繼續資料庫實際上是以非同步方式進行。</span><span class="sxs-lookup"><span data-stu-id="df232-123">A RESUME command returns as soon as it has been accepted by the replica that hosts the target database, but actually resuming the database occurs asynchronously.</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="df232-124">必要條件</span><span class="sxs-lookup"><span data-stu-id="df232-124">Prerequisites</span></span>  
  
-   <span data-ttu-id="df232-125">您必須連接到裝載要繼續之資料庫的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="df232-125">You must be connected to the server instance that hosts the database to be resumed.</span></span>  
  
-   <span data-ttu-id="df232-126">可用性群組必須在線上。</span><span class="sxs-lookup"><span data-stu-id="df232-126">The availability group must be online.</span></span>  
  
-   <span data-ttu-id="df232-127">主要資料庫必須在線上而且可用。</span><span class="sxs-lookup"><span data-stu-id="df232-127">The primary database must be online and available.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="df232-128">Security</span><span class="sxs-lookup"><span data-stu-id="df232-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="df232-129">權限</span><span class="sxs-lookup"><span data-stu-id="df232-129">Permissions</span></span>  
 <span data-ttu-id="df232-130">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="df232-130">Requires ALTER permission on the database.</span></span>  
  
 <span data-ttu-id="df232-131">需要可用性群組的 ALTER AVAILABILITY GROUP 權限、CONTROL AVAILABILITY GROUP 權限、ALTER ANY AVAILABILITY GROUP 權限或 CONTROL SERVER 權限。</span><span class="sxs-lookup"><span data-stu-id="df232-131">Requires ALTER AVAILABILITY GROUP permission on the availability group, CONTROL AVAILABILITY GROUP permission, ALTER ANY AVAILABILITY GROUP permission, or CONTROL SERVER permission.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="df232-132">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="df232-132">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="df232-133">**若要繼續次要資料庫**</span><span class="sxs-lookup"><span data-stu-id="df232-133">**To resume a secondary database**</span></span>  
  
1.  <span data-ttu-id="df232-134">在 [物件總管] 中，連接到裝載您要繼續資料庫之可用性複本的伺服器執行個體，然後展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="df232-134">In Object Explorer, connect to the server instance that hosts the availability replica on which you want to resume a database, and expand the server tree.</span></span>  
  
2.  <span data-ttu-id="df232-135">依序展開 **[AlwaysOn 高可用性]** 節點和 **[可用性群組]** 節點。</span><span class="sxs-lookup"><span data-stu-id="df232-135">Expand the **AlwaysOn High Availability** node and the **Availability Groups** node.</span></span>  
  
3.  <span data-ttu-id="df232-136">展開可用性群組。</span><span class="sxs-lookup"><span data-stu-id="df232-136">Expand the availability group.</span></span>  
  
4.  <span data-ttu-id="df232-137">展開 [可用性資料庫] 節點、以滑鼠右鍵按一下資料庫，然後按一下 [繼續進行資料移動]。</span><span class="sxs-lookup"><span data-stu-id="df232-137">Expand the **Availability Databases** node, right-click the database, and click **Resume Data Movement**.</span></span>  
  
5.  <span data-ttu-id="df232-138">在 **[繼續進行資料移動]** 對話方塊中，按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="df232-138">In the **Resume Data Movement** dialog box, click **OK**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="df232-139">若要繼續此複本位置的其他資料庫，請針對每個資料庫重複步驟 4 和 5。</span><span class="sxs-lookup"><span data-stu-id="df232-139">To resume additional databases on this replica location, repeat steps 4 and 5 for each database.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="df232-140">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="df232-140">Using Transact-SQL</span></span>  
 <span data-ttu-id="df232-141">**若要繼續在本機上暫停的次要資料庫**</span><span class="sxs-lookup"><span data-stu-id="df232-141">**To resume a secondary database that was suspended locally**</span></span>  
  
1.  <span data-ttu-id="df232-142">連接至裝載您要繼續其資料庫之次要複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="df232-142">Connect to the server instance that hosts the secondary replica whose database you want to resume.</span></span>  
  
2.  <span data-ttu-id="df232-143">使用下列 [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)陳述式，繼續次要資料庫：</span><span class="sxs-lookup"><span data-stu-id="df232-143">Resume the secondary database by using the following [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-hadr)statement:</span></span>  
  
     <span data-ttu-id="df232-144">ALTER DATABASE *database_name*設定 HADR RESUME</span><span class="sxs-lookup"><span data-stu-id="df232-144">ALTER DATABASE *database_name* SET HADR RESUME</span></span>  
  
##  <a name="using-powershell"></a><a name="PowerShellProcedure"></a> <span data-ttu-id="df232-145">使用 PowerShell</span><span class="sxs-lookup"><span data-stu-id="df232-145">Using PowerShell</span></span>  

### <a name="to-resume-a-secondary-database"></a><span data-ttu-id="df232-146">若要繼續次要資料庫</span><span class="sxs-lookup"><span data-stu-id="df232-146">To resume a secondary database</span></span>
  
1.  <span data-ttu-id="df232-147">將目錄 (`cd`) 變更為裝載您要繼續其資料庫之複本的伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="df232-147">Change directory (`cd`) to the server instance that hosts the replica whose database you want to resume.</span></span> <span data-ttu-id="df232-148">如需詳細資訊，請參閱本主題前面的＜ [必要條件](#Prerequisites)＞。</span><span class="sxs-lookup"><span data-stu-id="df232-148">For more information, see [Prerequisites](#Prerequisites), earlier in this topic.</span></span>  
  
2.  <span data-ttu-id="df232-149">使用 **Resume-SqlAvailabilityDatabase** Cmdlet 繼續可用性群組。</span><span class="sxs-lookup"><span data-stu-id="df232-149">Use the **Resume-SqlAvailabilityDatabase** cmdlet to resume the availability group.</span></span>  
  
     <span data-ttu-id="df232-150">例如，下列命令會針對可用性群組 `MyDb3` 中的可用性資料庫 `MyAg`繼續進行資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="df232-150">For example, the following command resumes data synchronization for the availability database `MyDb3` in the availability group `MyAg`.</span></span>  
  
    ```powershell
    Resume-SqlAvailabilityDatabase -Path SQLSERVER:\Sql\Computer\Instance\AvailabilityGroups\MyAg\Databases\MyDb3  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="df232-151">若要檢視指令程式的語法，請在 `Get-Help` PowerShell 環境中使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 指令程式。</span><span class="sxs-lookup"><span data-stu-id="df232-151">To view the syntax of a cmdlet, use the `Get-Help` cmdlet in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] PowerShell environment.</span></span> <span data-ttu-id="df232-152">如需詳細資訊，請參閱 [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md)。</span><span class="sxs-lookup"><span data-stu-id="df232-152">For more information, see [Get Help SQL Server PowerShell](../../../powershell/sql-server-powershell.md).</span></span>  
  
 <span data-ttu-id="df232-153">**若要設定和使用 SQL Server PowerShell 提供者**</span><span class="sxs-lookup"><span data-stu-id="df232-153">**To set up and use the SQL Server PowerShell provider**</span></span>  
  
-   [<span data-ttu-id="df232-154">SQL Server PowerShell 提供者</span><span class="sxs-lookup"><span data-stu-id="df232-154">SQL Server PowerShell Provider</span></span>](../../../powershell/sql-server-powershell-provider.md)  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="df232-155">相關工作</span><span class="sxs-lookup"><span data-stu-id="df232-155">Related Tasks</span></span>  
  
-   [<span data-ttu-id="df232-156">暫止可用性資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="df232-156">Suspend an Availability Database &#40;SQL Server&#41;</span></span>](suspend-an-availability-database-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="df232-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="df232-157">See Also</span></span>  
 [<span data-ttu-id="df232-158">AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;</span><span class="sxs-lookup"><span data-stu-id="df232-158">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
