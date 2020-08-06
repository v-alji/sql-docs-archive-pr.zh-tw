---
title: 刪除發行集 | Microsoft 文件
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- removing publications
- publications [SQL Server replication], deleting
- articles [SQL Server replication], deleting
- deleting publications
ms.assetid: 408a1360-12ee-4896-ac94-482ae839593b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 5d2b39a326d59333868b4f8015eb9a2e59d59e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709141"
---
# <a name="delete-a-publication"></a><span data-ttu-id="56306-102">刪除發行集</span><span class="sxs-lookup"><span data-stu-id="56306-102">Delete a Publication</span></span>
  <span data-ttu-id="56306-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] 、 [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]或 Replication Management Objects (RMO) 來刪除 [!INCLUDE[tsql](../../../includes/tsql-md.md)]中的發行集。</span><span class="sxs-lookup"><span data-stu-id="56306-103">This topic describes how to delete a publication in [!INCLUDE[ssCurrent](../../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)], [!INCLUDE[tsql](../../../includes/tsql-md.md)], or Replication Management Objects (RMO).</span></span>  
  
 <span data-ttu-id="56306-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="56306-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="56306-105">**若要刪除發行集，請使用：**</span><span class="sxs-lookup"><span data-stu-id="56306-105">**To delete a publication, using:**</span></span>  
  
     [<span data-ttu-id="56306-106">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="56306-106">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="56306-107">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="56306-107">Transact-SQL</span></span>](#TsqlProcedure)  
  
     [<span data-ttu-id="56306-108">Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="56306-108">Replication Management Objects (RMO)</span></span>](#RMOProcedure)  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="56306-109">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="56306-109">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="56306-110">從 **的** [本機發行集] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)]資料夾中刪除發行集。</span><span class="sxs-lookup"><span data-stu-id="56306-110">Delete publications from the **Local Publications** folder in [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-delete-a-publication"></a><span data-ttu-id="56306-111">若要刪除出版品</span><span class="sxs-lookup"><span data-stu-id="56306-111">To delete a publication</span></span>  
  
1.  <span data-ttu-id="56306-112">連接到 [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)]中的發行者，然後展開伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="56306-112">Connect to the Publisher in [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], and then expand the server node.</span></span>  
  
2.  <span data-ttu-id="56306-113">展開 **[複寫]** 資料夾，然後展開 **[本機發行集]** 資料夾。</span><span class="sxs-lookup"><span data-stu-id="56306-113">Expand the **Replication** folder, and then expand the **Local Publications** folder.</span></span>  
  
3.  <span data-ttu-id="56306-114">以滑鼠右鍵按一下您想刪除的發行集，然後按一下 **[刪除]** 。</span><span class="sxs-lookup"><span data-stu-id="56306-114">Right-click the publication you want to delete, and then click **Delete**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="56306-115">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="56306-115">Using Transact-SQL</span></span>  
 <span data-ttu-id="56306-116">您可以使用複寫預存程序以程式設計的方式刪除發行集。</span><span class="sxs-lookup"><span data-stu-id="56306-116">Publications can be deleted programmatically using replication stored procedures.</span></span> <span data-ttu-id="56306-117">使用哪些預存程序取決於所要刪除的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="56306-117">The stored procedures that you use depend on the type of publication being deleted.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="56306-118">刪除發行集不會從發行集資料庫中移除發行的物件，或是從訂閱資料庫中移除對應物件。</span><span class="sxs-lookup"><span data-stu-id="56306-118">Deleting a publication does not remove published objects from the publication database or the corresponding objects from the subscription database.</span></span> <span data-ttu-id="56306-119">必要的話，請使用 `DROP <object>` 命令來手動移除這些物件。</span><span class="sxs-lookup"><span data-stu-id="56306-119">Use the `DROP <object>` command to manually remove these objects if necessary.</span></span>  
  
#### <a name="to-delete-a-snapshot-or-transactional-publication"></a><span data-ttu-id="56306-120">刪除快照式或交易式發行集</span><span class="sxs-lookup"><span data-stu-id="56306-120">To delete a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="56306-121">執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="56306-121">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="56306-122">若要刪除單一發行集，請在發行集資料庫的發行者上執行 [sp_droppublication](/sql/relational-databases/system-stored-procedures/sp-droppublication-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="56306-122">To delete a single publication, execute [sp_droppublication](/sql/relational-databases/system-stored-procedures/sp-droppublication-transact-sql) at the Publisher on the publication database.</span></span>  
  
    -   <span data-ttu-id="56306-123">若要從發行的資料庫中刪除所有發行集及移除所有複寫物件，請在發行者上執行 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="56306-123">To delete all publications in and remove all replication objects from a published database, execute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) at the Publisher.</span></span> <span data-ttu-id="56306-124">`tran`為\*\* \@ 類型\*\*指定的值。</span><span class="sxs-lookup"><span data-stu-id="56306-124">Specify a value of `tran` for **\@type**.</span></span> <span data-ttu-id="56306-125">(選擇性) 如果無法存取散發者，或是資料庫的狀態為可疑或離線，請為 **\@force** 指定 **1** 值。</span><span class="sxs-lookup"><span data-stu-id="56306-125">(Optional) If the Distributor cannot be accessed or if the status of the database is suspect or offline, specify a value of **1** for **\@force**.</span></span> <span data-ttu-id="56306-126">(選擇性) 如果未在發行集資料庫上執行 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)，請為 **\@dbname** 指定資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="56306-126">(Optional) Specify the name of the database for **\@dbname** if [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) is not executed on the publication database.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="56306-127">為 **\@force** 指定 **1** 值時，可能會將與複寫有關的發行物件留在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="56306-127">Specifying a value of **1** for **\@force** may leave replication-related publishing objects in the database.</span></span>  
  
2.  <span data-ttu-id="56306-128">(選擇性) 如果此資料庫沒有任何其他發行集，請執行 [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)，以便使用快照式或異動複寫來停用目前資料庫的發行集。</span><span class="sxs-lookup"><span data-stu-id="56306-128">(Optional) If this database has no other publications, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) to disable publication of the current database using snapshot or transactional replication.</span></span>  
  
3.  <span data-ttu-id="56306-129">(選擇性) 在訂閱資料庫的訂閱者上，執行 [sp_subscription_cleanup](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql) 來移除訂閱資料庫中任何剩餘的複寫中繼資料。</span><span class="sxs-lookup"><span data-stu-id="56306-129">(Optional) At the Subscriber on the subscription database, execute [sp_subscription_cleanup](/sql/relational-databases/system-stored-procedures/sp-subscription-cleanup-transact-sql) to remove any remaining replication metadata in the subscription database.</span></span>  
  
#### <a name="to-delete-a-merge-publication"></a><span data-ttu-id="56306-130">刪除合併式發行集</span><span class="sxs-lookup"><span data-stu-id="56306-130">To delete a merge publication</span></span>  
  
1.  <span data-ttu-id="56306-131">執行下列其中一個動作：</span><span class="sxs-lookup"><span data-stu-id="56306-131">Do one of the following:</span></span>  
  
    -   <span data-ttu-id="56306-132">若要刪除單一發行集，請在發行集資料庫的發行者端執行 [sp_dropmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="56306-132">To delete a single publication, execute [sp_dropmergepublication &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropmergepublication-transact-sql) at the Publisher on the publication database.</span></span>  
  
    -   <span data-ttu-id="56306-133">若要從發行的資料庫中刪除所有發行集及移除所有複寫物件，請在發行者上執行 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) 。</span><span class="sxs-lookup"><span data-stu-id="56306-133">To delete all publications in and remove all replication objects from a published database, execute [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) at the Publisher.</span></span> <span data-ttu-id="56306-134">`merge`為\*\* \@ 類型\*\*指定的值。</span><span class="sxs-lookup"><span data-stu-id="56306-134">Specify a value of `merge` for **\@type**.</span></span> <span data-ttu-id="56306-135">(選擇性) 如果無法存取散發者，或是資料庫的狀態為可疑或離線，請為 **\@force** 指定 **1** 值。</span><span class="sxs-lookup"><span data-stu-id="56306-135">(Optional) If the Distributor cannot be accessed or if the status of the database is suspect or offline, specify a value of **1** for **\@force**.</span></span> <span data-ttu-id="56306-136">(選擇性) 如果未在發行集資料庫上執行 [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql)，請為 **\@dbname** 指定資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="56306-136">(Optional) Specify the name of the database for **\@dbname** if [sp_removedbreplication](/sql/relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql) is not executed on the publication database.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="56306-137">為 **\@force** 指定 **1** 值時，可能會將與複寫有關的發行物件留在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="56306-137">Specifying a value of **1** for **\@force** may leave replication-related publishing objects in the database.</span></span>  
  
2.  <span data-ttu-id="56306-138">(選擇性) 如果此資料庫沒有任何其他發行集，請執行 [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql)，以便使用合併式複寫來停用目前資料庫的發行集。</span><span class="sxs-lookup"><span data-stu-id="56306-138">(Optional) If this database has no other publications, execute [sp_replicationdboption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-replicationdboption-transact-sql) to disable publication of the current database using merge replication.</span></span>  
  
3.  <span data-ttu-id="56306-139">(選擇性) 在訂閱資料庫的訂閱者端，執行 [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql) 來移除訂閱資料庫中任何剩餘的複寫中繼資料。</span><span class="sxs-lookup"><span data-stu-id="56306-139">(Optional) At the Subscriber on the subscription database, execute [sp_mergesubscription_cleanup &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-mergesubscription-cleanup-transact-sql) to remove any remaining replication metadata in the subscription database.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="56306-140">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="56306-140">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="56306-141">此範例會示範如何移除交易式發行集，並針對資料庫停用交易式發行。</span><span class="sxs-lookup"><span data-stu-id="56306-141">This example shows how to remove a transactional publication and disable transactional publishing for a database.</span></span> <span data-ttu-id="56306-142">這個範例假設之前已移除所有的訂閱。</span><span class="sxs-lookup"><span data-stu-id="56306-142">This example assumes that all subscriptions were previously removed.</span></span> <span data-ttu-id="56306-143">如需相關資訊，請參閱 [Delete a Pull Subscription](../delete-a-pull-subscription.md) 或 [Delete a Push Subscription](../delete-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="56306-143">For more information, see [Delete a Pull Subscription](../delete-a-pull-subscription.md) or [Delete a Push Subscription](../delete-a-push-subscription.md).</span></span>  
  
 [!code-sql[HowTo#sp_droppublication](../../../snippets/tsql/SQL15/replication/howto/tsql/droptranpub.sql#sp_droppublication)]  
  
 <span data-ttu-id="56306-144">此範例會示範如何移除合併式發行集，並針對資料庫停用合併式發行。</span><span class="sxs-lookup"><span data-stu-id="56306-144">This example shows how to remove a merge publication and disable merge publishing for a database.</span></span> <span data-ttu-id="56306-145">這個範例假設之前已移除所有的訂閱。</span><span class="sxs-lookup"><span data-stu-id="56306-145">This example assumes that all subscriptions were previously removed.</span></span> <span data-ttu-id="56306-146">如需相關資訊，請參閱 [Delete a Pull Subscription](../delete-a-pull-subscription.md) 或 [Delete a Push Subscription](../delete-a-push-subscription.md)。</span><span class="sxs-lookup"><span data-stu-id="56306-146">For more information, see [Delete a Pull Subscription](../delete-a-pull-subscription.md) or [Delete a Push Subscription](../delete-a-push-subscription.md).</span></span>  
  
 [!code-sql[HowTo#sp_dropmergepublication](../../../snippets/tsql/SQL15/replication/howto/tsql/dropmergepub.sql#sp_dropmergepublication)]  
  
##  <a name="using-replication-management-objects-rmo"></a><a name="RMOProcedure"></a> <span data-ttu-id="56306-147">使用 Replication Management Objects (RMO)</span><span class="sxs-lookup"><span data-stu-id="56306-147">Using Replication Management Objects (RMO)</span></span>  
 <span data-ttu-id="56306-148">您可以使用 Replication Management Objects (RMO) 以程式設計的方式刪除發行集。</span><span class="sxs-lookup"><span data-stu-id="56306-148">You can delete publications programmatically by using Replication Management Objects (RMO).</span></span> <span data-ttu-id="56306-149">用來移除發行集的 RMO 類別，將取決於所移除的發行集類型而定。</span><span class="sxs-lookup"><span data-stu-id="56306-149">The RMO classes that you use to remove a publication depend on the type of publication you remove.</span></span>  
  
#### <a name="to-remove-a-snapshot-or-transactional-publication"></a><span data-ttu-id="56306-150">移除快照式或交易式發行集</span><span class="sxs-lookup"><span data-stu-id="56306-150">To remove a snapshot or transactional publication</span></span>  
  
1.  <span data-ttu-id="56306-151">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="56306-151">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="56306-152">建立 <xref:Microsoft.SqlServer.Replication.TransPublication> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="56306-152">Create an instance of the <xref:Microsoft.SqlServer.Replication.TransPublication> class.</span></span>  
  
3.  <span data-ttu-id="56306-153">設定發行集的 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 屬性，並將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定為在步驟 1 中建立的連接。</span><span class="sxs-lookup"><span data-stu-id="56306-153">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="56306-154">檢查 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 屬性，確認該發行集存在。</span><span class="sxs-lookup"><span data-stu-id="56306-154">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the publication exists.</span></span> <span data-ttu-id="56306-155">如果這個屬性的值為 `false`，則表示步驟 3 中的發行集屬性定義錯誤或是此發行集不存在。</span><span class="sxs-lookup"><span data-stu-id="56306-155">If the value of this property is `false`, either the publication properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="56306-156">呼叫 <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="56306-156">Call the <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> method.</span></span>  
  
6.  <span data-ttu-id="56306-157">(選擇性) 如果此資料庫沒有任何其他的交易式發行集存在，則可以針對交易式發行停用此資料庫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="56306-157">(Optional) If no other transactional publications exist for this database, the database can be disabled for transactional publishing as follows:</span></span>  
  
    1.  <span data-ttu-id="56306-158">建立 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="56306-158">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> class.</span></span> <span data-ttu-id="56306-159">將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定為步驟 1 中 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="56306-159">Set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the instance of <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from step 1.</span></span>  
  
    2.  <span data-ttu-id="56306-160">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="56306-160">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="56306-161">如果此方法傳回 `false`，請確認此資料庫存在。</span><span class="sxs-lookup"><span data-stu-id="56306-161">If this method returns `false`, confirm that the database exists.</span></span>  
  
    3.  <span data-ttu-id="56306-162">將 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> 屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="56306-162">Set the <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledTransPublishing%2A> property to `false`.</span></span>  
  
    4.  <span data-ttu-id="56306-163">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="56306-163">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="56306-164">關閉連接。</span><span class="sxs-lookup"><span data-stu-id="56306-164">Close the connections.</span></span>  
  
#### <a name="to-remove-a-merge-publication"></a><span data-ttu-id="56306-165">移除合併式發行集</span><span class="sxs-lookup"><span data-stu-id="56306-165">To remove a merge publication</span></span>  
  
1.  <span data-ttu-id="56306-166">使用 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 類別建立與發行者的連接。</span><span class="sxs-lookup"><span data-stu-id="56306-166">Create a connection to the Publisher by using the <xref:Microsoft.SqlServer.Management.Common.ServerConnection> class.</span></span>  
  
2.  <span data-ttu-id="56306-167">建立 <xref:Microsoft.SqlServer.Replication.MergePublication> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="56306-167">Create an instance of the <xref:Microsoft.SqlServer.Replication.MergePublication> class.</span></span>  
  
3.  <span data-ttu-id="56306-168">設定發行集的 <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> 和 <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> 屬性，並將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定為在步驟 1 中建立的連接。</span><span class="sxs-lookup"><span data-stu-id="56306-168">Set the <xref:Microsoft.SqlServer.Replication.Publication.Name%2A> and <xref:Microsoft.SqlServer.Replication.Publication.DatabaseName%2A> properties for the publication, and set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the connection created in step 1.</span></span>  
  
4.  <span data-ttu-id="56306-169">檢查 <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> 屬性，確認該發行集存在。</span><span class="sxs-lookup"><span data-stu-id="56306-169">Check the <xref:Microsoft.SqlServer.Replication.ReplicationObject.IsExistingObject%2A> property to verify that the publication exists.</span></span> <span data-ttu-id="56306-170">如果這個屬性的值為 `false`，則表示步驟 3 中的發行集屬性定義錯誤或是此發行集不存在。</span><span class="sxs-lookup"><span data-stu-id="56306-170">If the value of this property is `false`, either the publication properties in step 3 were defined incorrectly or the publication does not exist.</span></span>  
  
5.  <span data-ttu-id="56306-171">呼叫 <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="56306-171">Call the <xref:Microsoft.SqlServer.Replication.Publication.Remove%2A> method.</span></span>  
  
6.  <span data-ttu-id="56306-172">(選擇性) 如果此資料庫沒有任何其他的合併式發行集存在，則可以針對合併式發行停用此資料庫，如下所示：</span><span class="sxs-lookup"><span data-stu-id="56306-172">(Optional) If no other merge publications exist for this database, the database can be disabled for merge publishing as follows:</span></span>  
  
    1.  <span data-ttu-id="56306-173">建立 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="56306-173">Create an instance of the <xref:Microsoft.SqlServer.Replication.ReplicationDatabase> class.</span></span> <span data-ttu-id="56306-174">將 <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> 屬性設定為步驟 1 中 <xref:Microsoft.SqlServer.Management.Common.ServerConnection> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="56306-174">Set the <xref:Microsoft.SqlServer.Replication.ReplicationObject.ConnectionContext%2A> property to the instance of <xref:Microsoft.SqlServer.Management.Common.ServerConnection> from Step 1.</span></span>  
  
    2.  <span data-ttu-id="56306-175">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="56306-175">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.LoadProperties%2A> method.</span></span> <span data-ttu-id="56306-176">如果此方法傳回 `false`，請確認此資料庫存在。</span><span class="sxs-lookup"><span data-stu-id="56306-176">If this method returns `false`, verify that the database exists.</span></span>  
  
    3.  <span data-ttu-id="56306-177">將 <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> 屬性設定為 `false`。</span><span class="sxs-lookup"><span data-stu-id="56306-177">Set the <xref:Microsoft.SqlServer.Replication.ReplicationDatabase.EnabledMergePublishing%2A> property to `false`.</span></span>  
  
    4.  <span data-ttu-id="56306-178">呼叫 <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="56306-178">Call the <xref:Microsoft.SqlServer.Replication.ReplicationObject.CommitPropertyChanges%2A> method.</span></span>  
  
7.  <span data-ttu-id="56306-179">關閉連接。</span><span class="sxs-lookup"><span data-stu-id="56306-179">Close the connections.</span></span>  
  
###  <a name="examples-rmo"></a><a name="PShellExample"></a> <span data-ttu-id="56306-180">範例 (RMO)</span><span class="sxs-lookup"><span data-stu-id="56306-180">Examples (RMO)</span></span>  
 <span data-ttu-id="56306-181">下列範例會刪除交易式發行集。</span><span class="sxs-lookup"><span data-stu-id="56306-181">The following example deletes a transactional publication.</span></span> <span data-ttu-id="56306-182">如果此資料庫沒有任何其他的交易式發行集存在，則也會停用交易式發行。</span><span class="sxs-lookup"><span data-stu-id="56306-182">If no other transactional publications exist for this database, transactional publishing is also disabled.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropTranPub](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_droptranpub)]  
  
 [!code-vb[HowTo#rmo_vb_DropTranPub](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_droptranpub)]  
  
 <span data-ttu-id="56306-183">下列範例會刪除合併式發行集。</span><span class="sxs-lookup"><span data-stu-id="56306-183">The following example deletes a merge publication.</span></span> <span data-ttu-id="56306-184">如果此資料庫沒有任何其他的合併式發行集存在，則也會停用合併式發行。</span><span class="sxs-lookup"><span data-stu-id="56306-184">If no other merge publications exist for this database, merge publishing is also disabled.</span></span>  
  
 [!code-csharp[HowTo#rmo_DropMergePub](../../../snippets/csharp/SQL15/replication/howto/cs/rmotestevelope.cs#rmo_dropmergepub)]  
  
 [!code-vb[HowTo#rmo_vb_DropMergePub](../../../snippets/visualbasic/SQL15/replication/howto/vb/rmotestenv.vb#rmo_vb_dropmergepub)]  
  
## <a name="see-also"></a><span data-ttu-id="56306-185">另請參閱</span><span class="sxs-lookup"><span data-stu-id="56306-185">See Also</span></span>  
 <span data-ttu-id="56306-186">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span><span class="sxs-lookup"><span data-stu-id="56306-186">[Replication System Stored Procedures Concepts](../concepts/replication-system-stored-procedures-concepts.md) </span></span>  
 [<span data-ttu-id="56306-187">發行資料和資料庫物件</span><span class="sxs-lookup"><span data-stu-id="56306-187">Publish Data and Database Objects</span></span>](publish-data-and-database-objects.md)  
  
  
