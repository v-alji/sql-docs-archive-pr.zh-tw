---
title: 停用發行和散發 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- disabling publishing
- publishing [SQL Server replication], disabling
- distribution disabling [SQL Server replication]
- removing replication
- replication [SQL Server], removing
- disabling replication
- disabling distribution
ms.assetid: 6d4a1474-4d13-4826-8be2-80050fafa8a5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8843dac310d1e023fe7ce63eded02c9e1bed3731
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585872"
---
# <a name="disable-publishing-and-distribution"></a><span data-ttu-id="72a9b-102">停用發行和散發</span><span class="sxs-lookup"><span data-stu-id="72a9b-102">Disable Publishing and Distribution</span></span>
  <span data-ttu-id="72a9b-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]或 Replication Management Objects (RMO)，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中停用發行和散發。</span><span class="sxs-lookup"><span data-stu-id="72a9b-103">This topic describes how to disable publishing and distribution in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="72a9b-104">您可以執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="72a9b-104">You can do the following:</span></span>  
  
-   <span data-ttu-id="72a9b-105">刪除「散發者」上的散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="72a9b-105">Delete all distribution databases on the Distributor.</span></span>  
  
-   <span data-ttu-id="72a9b-106">停用所有使用「散發者」的「發行者」，以及刪除這些「發行者」上的所有發行集。</span><span class="sxs-lookup"><span data-stu-id="72a9b-106">Disable all Publishers that use the Distributor and delete all publications on those Publishers.</span></span>  
  
-   <span data-ttu-id="72a9b-107">刪除所有的發行集訂閱。</span><span class="sxs-lookup"><span data-stu-id="72a9b-107">Delete all subscriptions to the publications.</span></span> <span data-ttu-id="72a9b-108">發行集和訂閱資料庫中的資料不會刪除，不過它會遺失與任何發行資料庫的同步處理關聯性。</span><span class="sxs-lookup"><span data-stu-id="72a9b-108">Data in the publication and subscription databases will not be deleted; however, it loses its synchronization relationship to any publication databases.</span></span> <span data-ttu-id="72a9b-109">若要刪除「訂閱者」中的資料，您必須手動刪除。</span><span class="sxs-lookup"><span data-stu-id="72a9b-109">If you want the data at the Subscriber to be deleted, you must delete it manually.</span></span>  
  
 <span data-ttu-id="72a9b-110">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="72a9b-110">**In This Topic**</span></span>  
  
-   <span data-ttu-id="72a9b-111">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="72a9b-111">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="72a9b-112">先決條件</span><span class="sxs-lookup"><span data-stu-id="72a9b-112">Prerequisites</span></span>](#Prerequisites)  
  
-   <span data-ttu-id="72a9b-113">**若要停用發行和散發，請使用：**</span><span class="sxs-lookup"><span data-stu-id="72a9b-113">**To disable publishing and distribution, using:**</span></span>  
  
     [<span data-ttu-id="72a9b-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="72a9b-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="72a9b-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="72a9b-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="72a9b-116">Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="72a9b-116">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="72a9b-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="72a9b-117">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="72a9b-118">必要條件</span><span class="sxs-lookup"><span data-stu-id="72a9b-118">Prerequisites</span></span>  
  
-   <span data-ttu-id="72a9b-119">若要停用發行和散發，所有散發和發行集資料庫都必須在線上。</span><span class="sxs-lookup"><span data-stu-id="72a9b-119">To disable publishing and distribution, all distribution and publication databases must be online.</span></span> <span data-ttu-id="72a9b-120">如果存在散發或發行集資料庫的任何 *「資料庫快照集」* ，則必須先卸除這些快照集，然後才能停用發行和散發。</span><span class="sxs-lookup"><span data-stu-id="72a9b-120">If any *database snapshots* exist for distribution or publication databases, they must be dropped before disabling publishing and distribution.</span></span> <span data-ttu-id="72a9b-121">資料庫快照集是資料庫的唯讀離線副本，與複寫快照集無關聯。</span><span class="sxs-lookup"><span data-stu-id="72a9b-121">A database snapshot is a read-only offline copy of a database and is not related to a replication snapshot.</span></span> <span data-ttu-id="72a9b-122">如需詳細資訊，請參閱[資料庫快照集 &#40;SQL Server&#41;](../databases/database-snapshots-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="72a9b-122">For more information, see [Database Snapshots &#40;SQL Server&#41;](../databases/database-snapshots-sql-server.md).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="72a9b-123">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="72a9b-123">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="72a9b-124">使用「停用發行與散發精靈」停用發行和散發。</span><span class="sxs-lookup"><span data-stu-id="72a9b-124">Disable publishing and distribution by using the Disable Publishing and Distribution Wizard.</span></span>  
  
#### <a name="to-disable-publishing-and-distribution"></a><span data-ttu-id="72a9b-125">停用發行和散發</span><span class="sxs-lookup"><span data-stu-id="72a9b-125">To disable publishing and distribution</span></span>  
  
1.  <span data-ttu-id="72a9b-126">連線到您要在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中停用的「發行者」或「散發者」，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="72a9b-126">Connect to the Publisher or Distributor you want to disable in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="72a9b-127">以滑鼠右鍵按一下 **[複寫]** 資料夾，然後按一下 **[停用發行與散發]** 。</span><span class="sxs-lookup"><span data-stu-id="72a9b-127">Right-click the **Replication** folder, and then click **Disable Publishing and Distribution**.</span></span>  
  
3.  <span data-ttu-id="72a9b-128">完成「停用散發暨發行精靈」中的步驟。</span><span class="sxs-lookup"><span data-stu-id="72a9b-128">Complete the steps in the Disable Publishing and Distribution Wizard.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="72a9b-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="72a9b-129">Using Transact-SQL</span></span>  
 <span data-ttu-id="72a9b-130">您可以使用複寫預存程序來以程式設計的方式停用發行和散發。</span><span class="sxs-lookup"><span data-stu-id="72a9b-130">Publishing and distributing can be disabled programmatically using replication stored procedures.</span></span>  
  
#### <a name="to-disable-publishing-and-distribution"></a><span data-ttu-id="72a9b-131">停用發行和散發</span><span class="sxs-lookup"><span data-stu-id="72a9b-131">To disable publishing and distribution</span></span>  
  
1.  <span data-ttu-id="72a9b-132">停止所有複寫相關的作業。</span><span class="sxs-lookup"><span data-stu-id="72a9b-132">Stop all replication-related jobs.</span></span> <span data-ttu-id="72a9b-133">如需作業名稱清單，請參閱＜ [複寫代理程式安全性模型](security/replication-agent-security-model.md)＞一節中的「SQL Server Agent 下的代理程式安全性」。</span><span class="sxs-lookup"><span data-stu-id="72a9b-133">For a list of job names, see the "Agent Security Under SQL Server Agent" section of [Replication Agent Security Model](security/replication-agent-security-model.md).</span></span>  
  
2.  <span data-ttu-id="72a9b-134">在訂閱資料庫的每一個訂閱者上，執行 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) 從資料庫中移除複寫物件。</span><span class="sxs-lookup"><span data-stu-id="72a9b-134">At each Subscriber on the subscription database, execute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to remove replication objects from the database.</span></span> <span data-ttu-id="72a9b-135">這個預存程序將不會移除散發者上的複寫作業。</span><span class="sxs-lookup"><span data-stu-id="72a9b-135">This stored procedure will not remove replication jobs at the Distributor.</span></span>  
  
3.  <span data-ttu-id="72a9b-136">在發行集資料庫的發行者上，執行 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) 從資料庫中移除複寫物件。</span><span class="sxs-lookup"><span data-stu-id="72a9b-136">At the Publisher on the publication database, execute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) to remove replication objects from the database.</span></span>  
  
4.  <span data-ttu-id="72a9b-137">如果發行者使用遠端散發者，請執行 [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="72a9b-137">If the Publisher uses a remote Distributor, execute [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql).</span></span>  
  
5.  <span data-ttu-id="72a9b-138">在散發者上執行 [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="72a9b-138">At the Distributor, execute [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql).</span></span> <span data-ttu-id="72a9b-139">應該針對散發者上註冊的每一個發行者執行此預存程序一次。</span><span class="sxs-lookup"><span data-stu-id="72a9b-139">This stored procedure should be run once for each Publisher registered at the Distributor.</span></span>  
  
6.  <span data-ttu-id="72a9b-140">在散發者上，執行 [sp_dropdistributiondb](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) 來刪除散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="72a9b-140">At the Distributor, execute [sp_dropdistributiondb](/sql/relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql) to delete the distribution database.</span></span> <span data-ttu-id="72a9b-141">應該針對散發者上的每一個散發資料庫執行此預存程序一次。</span><span class="sxs-lookup"><span data-stu-id="72a9b-141">This stored procedure should be run once for each distribution database at the Distributor.</span></span> <span data-ttu-id="72a9b-142">這樣也會移除與散發資料庫有關的任何佇列讀取器代理程式作業。</span><span class="sxs-lookup"><span data-stu-id="72a9b-142">This also removes any Queue Reader Agent jobs associated with the distribution database.</span></span>  
  
7.  <span data-ttu-id="72a9b-143">在散發者上，執行 [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql) 從伺服器移除散發者的指定。</span><span class="sxs-lookup"><span data-stu-id="72a9b-143">At the Distributor, execute [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql) to remove the Distributor designation from the server.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="72a9b-144">如果在您執行 [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql) 和 [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql)之前，尚未卸除所有複寫發行和散發物件，這些程序將會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="72a9b-144">If all replication publishing and distribution objects are not dropped before you execute [sp_dropdistpublisher](/sql/relational-databases/system-stored-procedures/sp-dropdistpublisher-transact-sql) and [sp_dropdistributor](/sql/relational-databases/system-stored-procedures/sp-dropdistributor-transact-sql), these procedures will return an error.</span></span> <span data-ttu-id="72a9b-145">若要在卸載發行者或散發者時卸載所有複寫相關的物件， \*\* \@ no_checks**參數必須設定為**1\*\*。</span><span class="sxs-lookup"><span data-stu-id="72a9b-145">To drop all replication-related objects when a Publisher or Distributor is dropped, the **\@no_checks** parameter must be set to **1**.</span></span> <span data-ttu-id="72a9b-146">如果「發行者」或「散發者」已離線或無法存取， \*\* \@ ignore_distributor**參數可以設定為**1\*\* ，以便卸載它們; 不過，您必須手動移除任何剩餘的發行和散發物件。</span><span class="sxs-lookup"><span data-stu-id="72a9b-146">If a Publisher or Distributor is offline or unreachable, the **\@ignore_distributor** parameter can be set to **1** so that they can be dropped; however, any publishing and distributing objects left behind must be removed manually.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="72a9b-147">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="72a9b-147">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="72a9b-148">這個範例指令碼會從訂閱資料庫中移除複寫物件。</span><span class="sxs-lookup"><span data-stu-id="72a9b-148">This example script removes replication objects from the subscription database.</span></span>  
  
 [!code-sql[HowTo#sp_removedbreplication](../../snippets/tsql/SQL15/replication/howto/tsql/dropdistpub.sql#sp_removedbreplication)]  
  
 <span data-ttu-id="72a9b-149">此範例指令碼會停用當做發行者和散發者之伺服器上的發行和散發，並卸除散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="72a9b-149">This example script disables publishing and distribution on a server that is a Publisher and Distributor and drops the distribution database.</span></span>  
  
 [!code-sql[HowTo#sp_DropDistPub](../../snippets/tsql/SQL15/replication/howto/tsql/dropdistpub.sql#sp_dropdistpub)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="72a9b-150">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="72a9b-150">Using Replication Management Objects (RMO)</span></span>  
  
#### <a name="to-disable-publishing-and-distribution"></a><span data-ttu-id="72a9b-151">停用發行和散發</span><span class="sxs-lookup"><span data-stu-id="72a9b-151">To disable publishing and distribution</span></span>  
  
1.  <span data-ttu-id="72a9b-152">移除使用散發者之發行集的所有訂閱。</span><span class="sxs-lookup"><span data-stu-id="72a9b-152">Remove all subscriptions to publications that use the Distributor.</span></span> <span data-ttu-id="72a9b-153">如需相關資訊，請參閱 [Delete a Pull Subscription](delete-a-pull-subscription.md) 以及 [Delete a Push Subscription](delete-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="72a9b-153">For more information, see [Delete a Pull Subscription](delete-a-pull-subscription.md) and [Delete a Push Subscription](delete-a-push-subscription.md).</span></span>  
  
2.  <span data-ttu-id="72a9b-154">移除使用散發者的所有訂閱，以及停用所有資料庫的發行 (如果發行者和散發者在相同的伺服器上)。</span><span class="sxs-lookup"><span data-stu-id="72a9b-154">Remove all publications that use the Distributor, and disable publishing for all databases if the Publisher and Distributor are on the same server.</span></span> <span data-ttu-id="72a9b-155">如需詳細資訊，請參閱 [Delete a Publication](publish/delete-a-publication.md)。</span><span class="sxs-lookup"><span data-stu-id="72a9b-155">For more information, see [Delete a Publication](publish/delete-a-publication.md).</span></span>  
  
3.  <span data-ttu-id="72a9b-156">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與散發者的連接。</span><span class="sxs-lookup"><span data-stu-id="72a9b-156">Create a connection to the Distributor by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
4.  <span data-ttu-id="72a9b-157">建立 <xref:Microsoft.SqlServer.Replication.DistributionPublisher> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="72a9b-157">Create an instance of the <xref:Microsoft.SqlServer.Replication.DistributionPublisher> class.</span></span> <span data-ttu-id="72a9b-158">指定 <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> 屬性，並傳遞步驟 3 中的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="72a9b-158">Specify the <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Name%2A> property, and pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 3.</span></span>  
  
5.  <span data-ttu-id="72a9b-159">(選擇性) 呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法，以取得物件的屬性及確認發行者確實存在。</span><span class="sxs-lookup"><span data-stu-id="72a9b-159">(Optional) Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method to get the properties of the object and verify that the Publisher exists.</span></span> <span data-ttu-id="72a9b-160">如果此方法傳回 `false`，則表示步驟 4 中設定的發行者名稱不正確，或是此散發者並未使用此發行者。</span><span class="sxs-lookup"><span data-stu-id="72a9b-160">If this method returns `false`, the Publisher name set in step 4 was incorrect or the Publisher is not used by this Distributor.</span></span>  
  
6.  <span data-ttu-id="72a9b-161">呼叫 <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="72a9b-161">Call the <xref:Microsoft.SqlServer.Replication.DistributionPublisher.Remove%2A> method.</span></span> <span data-ttu-id="72a9b-162">`true`如果發行者和散發者位於不同的伺服器上，以及應該在散發者端卸載發行者，而不需要先確認發行集已不存在於發行者端，請傳遞的值為*force* 。</span><span class="sxs-lookup"><span data-stu-id="72a9b-162">Pass a value of `true` for *force* if the Publisher and Distributor are on different servers, and when the Publisher should be uninstalled at the Distributor without first verifying that publications no longer exist at the Publisher.</span></span>  
  
7.  <span data-ttu-id="72a9b-163">建立 <xref:Microsoft.SqlServer.Replication.ReplicationServer> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="72a9b-163">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationServer> class.</span></span> <span data-ttu-id="72a9b-164">傳遞步驟 3 的 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 物件。</span><span class="sxs-lookup"><span data-stu-id="72a9b-164">Pass the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> object from step 3.</span></span>  
  
8.  <span data-ttu-id="72a9b-165">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationServer.UninstallDistributor%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="72a9b-165">Call the <xref:Microsoft.SqlServer.Replication.ReplicationServer.UninstallDistributor%2A> method.</span></span> <span data-ttu-id="72a9b-166">傳遞 `true` for *force*的值，以在散發者端移除所有複寫物件，而不需要先確認是否已停用所有本機發行集資料庫，而且已卸載散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="72a9b-166">Pass a value of `true` for *force* to remove all replication objects at the Distributor without first verifying that all local publication databases have been disabled, and distribution databases have been uninstalled.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="72a9b-167">範例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="72a9b-167">Examples (RMO)</span></span>  
 <span data-ttu-id="72a9b-168">此範例會移除散發者上的發行者註冊、捨棄散發資料庫，以及解除安裝散發者。</span><span class="sxs-lookup"><span data-stu-id="72a9b-168">This example removes the Publisher registration at the Distributor, drops the distribution database, and uninstalls the Distributor.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropDistPub](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropdistpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPub](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropdistpub)]  
  
 <span data-ttu-id="72a9b-169">此範例會解除安裝散發者，而不先停用本機發行集資料庫或捨棄散發資料庫。</span><span class="sxs-lookup"><span data-stu-id="72a9b-169">This example uninstalls the Distributor without first disabling local publication databases or dropping the distribution database.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropDistPubForce](../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropdistpubforce)]  
  
 [!code-vb[HowTo#rmo_vb_DropDistPubForce](../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropdistpubforce)]  
  
## <a name="see-also"></a><span data-ttu-id="72a9b-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72a9b-170">See Also</span></span>  
 <span data-ttu-id="72a9b-171">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="72a9b-171">[Replication Management Objects Concepts](concepts/replication-management-objects-concepts.md) </span></span>  
 [<span data-ttu-id="72a9b-172">Replication System Stored Procedures Concepts</span><span class="sxs-lookup"><span data-stu-id="72a9b-172">Replication System Stored Procedures Concepts</span></span>](concepts/replication-system-stored-procedures-concepts.md)  
  
  
