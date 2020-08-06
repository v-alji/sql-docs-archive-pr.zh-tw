---
title: 在鏡像資料庫停機時間最短的系統上安裝 Service Pack |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- hotfixes [SQL Server]
- database mirroring [SQL Server], upgrading system
- rolling upgrades [SQL Server]
- service packs [SQL Server]
- upgrading mirrored database systems
- upgrading SQL Server, mirrored databases
ms.assetid: bdc63142-027d-4ead-9d3e-147331387ef5
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: e878d31ec926f8b2cc460854f422b4d01d32d414
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703270"
---
# <a name="install-a-service-pack-on-a-system-with-minimal-downtime-for-mirrored-databases"></a><span data-ttu-id="13e37-102">在鏡像資料庫停機時間最少的情況下於系統上安裝 Service Pack</span><span class="sxs-lookup"><span data-stu-id="13e37-102">Install a Service Pack on a System with Minimal Downtime for Mirrored Databases</span></span>
  <span data-ttu-id="13e37-103">此主題描述如何在您安裝 Service Pack 和 Hotfix 時，將鏡像資料庫的停機時間減至最少。</span><span class="sxs-lookup"><span data-stu-id="13e37-103">This topic describes how to minimize downtime for mirrored databases when you install service packs and hotfixes.</span></span> <span data-ttu-id="13e37-104">這個程序牽涉到循序升級參與資料庫鏡像的 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="13e37-104">This process involves sequentially upgrading the instances of [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] that are participating in database mirroring.</span></span> <span data-ttu-id="13e37-105">這種形式的更新（稱為「輪流*更新*」）可將停機時間縮短為只有單一容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="13e37-105">This form of update, which is known as a *rolling update*, reduces downtime to only a single failover.</span></span> <span data-ttu-id="13e37-106">請注意，在高效能模式的工作階段中，如果鏡像伺服器與主體伺服器之間的地理位置遙遠，輪流更新可能不適合。</span><span class="sxs-lookup"><span data-stu-id="13e37-106">Note that for high-performance mode sessions in which the mirror server is geographically distant from the principal server, a rolling update might be inappropriate.</span></span>  
  
 <span data-ttu-id="13e37-107">輪流更新是指由下列階段組成的多階段程序：</span><span class="sxs-lookup"><span data-stu-id="13e37-107">A rolling update is a multi-stage process that consists of the following stages:</span></span>  
  
-   <span data-ttu-id="13e37-108">保護您的資料。</span><span class="sxs-lookup"><span data-stu-id="13e37-108">Protect your data.</span></span>  
  
-   <span data-ttu-id="13e37-109">如果工作階段包含見證，建議您最好移除該見證。</span><span class="sxs-lookup"><span data-stu-id="13e37-109">If the session includes a witness, we recommend that you remove the witness.</span></span> <span data-ttu-id="13e37-110">否則，當更新鏡像伺服器執行個體時，資料庫可用性會相依於仍然連接至主體伺服器執行個體的見證。</span><span class="sxs-lookup"><span data-stu-id="13e37-110">Otherwise, when the mirror server instance is being updated, database availability depends on the witness that remains connected to the principal server instance.</span></span> <span data-ttu-id="13e37-111">當您移除見證之後，您可以在輪流更新期間的任何時候將它更新，避免發生資料庫停機的風險。</span><span class="sxs-lookup"><span data-stu-id="13e37-111">After you remove a witness, you can update it at any time during the rolling update process without risking database downtime.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="13e37-112">如需詳細資訊，請參閱[仲裁：見證如何影響資料庫可用性 &#40;資料庫鏡像&#41;](database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md)。</span><span class="sxs-lookup"><span data-stu-id="13e37-112">For more information, see [Quorum: How a Witness Affects Database Availability &#40;Database Mirroring&#41;](database-mirroring/quorum-how-a-witness-affects-database-availability-database-mirroring.md).</span></span>  
  
-   <span data-ttu-id="13e37-113">如果工作階段是在高效能模式中執行，請將作業模式變更為高安全性模式。</span><span class="sxs-lookup"><span data-stu-id="13e37-113">If a session is running in high-performance mode, change the operating mode to high-safety mode.</span></span>  
  
-   <span data-ttu-id="13e37-114">更新與資料庫鏡像有關的每一個伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="13e37-114">Update each server instance that is involved in database mirroring.</span></span> <span data-ttu-id="13e37-115">輪流更新牽涉到將目前為鏡像伺服器的伺服器執行個體升級、手動容錯移轉它的每一個鏡像資料庫，以及將一開始為主體伺服器 (現在為新的鏡像伺服器) 的伺服器執行個體升級。</span><span class="sxs-lookup"><span data-stu-id="13e37-115">A rolling update involves upgrading the server instance that is currently the mirror server, manually failing over each of its mirrored databases, and upgrading the server instance that was first the principal server (and is now the new mirror server).</span></span> <span data-ttu-id="13e37-116">在此時，您必須繼續鏡像作業。</span><span class="sxs-lookup"><span data-stu-id="13e37-116">At this point, you will have to resume mirroring.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="13e37-117">在開始輪流更新之前，我們建議您至少在一個鏡像工作階段執行手動容錯移轉練習。</span><span class="sxs-lookup"><span data-stu-id="13e37-117">Before starting a rolling update, we recommend that you perform a practice manual failover on at least one of your mirroring sessions.</span></span>  
  
-   <span data-ttu-id="13e37-118">在必要時還原成高效能模式。</span><span class="sxs-lookup"><span data-stu-id="13e37-118">Revert to high-performance mode, if it is required.</span></span>  
  
-   <span data-ttu-id="13e37-119">在必要時讓見證回到鏡像工作階段。</span><span class="sxs-lookup"><span data-stu-id="13e37-119">Return the witness to the mirroring session, if it is required.</span></span>  
  
 <span data-ttu-id="13e37-120">這裡將說明這些階段的程序。</span><span class="sxs-lookup"><span data-stu-id="13e37-120">The procedures for these stages are described here.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="13e37-121">伺服器執行個體可能在並行鏡像工作階段中執行不同的鏡像角色 (主體伺服器、鏡像伺服器或見證)。</span><span class="sxs-lookup"><span data-stu-id="13e37-121">A server instance might be performing different mirroring roles (principal server, mirror server, or witness) in concurrent mirroring sessions.</span></span> <span data-ttu-id="13e37-122">在此情況下，您必須依照狀況來配合基本輪流更新程序。</span><span class="sxs-lookup"><span data-stu-id="13e37-122">In this case, you will have to adapt the basic rolling update process accordingly.</span></span>  
  
### <a name="to-protect-your-data-before-an-update-a-best-practice"></a><span data-ttu-id="13e37-123">在更新之前保護資料 (最佳作法)</span><span class="sxs-lookup"><span data-stu-id="13e37-123">To protect your data before an update (a best practice)</span></span>  
  
1.  <span data-ttu-id="13e37-124">在每一個主體資料庫上執行完整資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="13e37-124">Perform a full database backup on every principal database.</span></span>  
  
     <span data-ttu-id="13e37-125">**備份資料庫**</span><span class="sxs-lookup"><span data-stu-id="13e37-125">**To back up a database**</span></span>  
  
    -   <span data-ttu-id="13e37-126">[建立完整資料庫備份 &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="13e37-126">[Create a Full Database Backup &#40;SQL Server&#41;](../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="13e37-127">在每一個主體資料庫上執行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 命令。</span><span class="sxs-lookup"><span data-stu-id="13e37-127">Run the [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) command on every principal database.</span></span>  
  
### <a name="to-remove-a-witness-from-a-session"></a><span data-ttu-id="13e37-128">從工作階段中移除見證</span><span class="sxs-lookup"><span data-stu-id="13e37-128">To remove a witness from a session</span></span>  
  
1.  <span data-ttu-id="13e37-129">如果鏡像工作階段牽涉到見證，我們建議您在執行輪流更新之前，最好先移除該見證。</span><span class="sxs-lookup"><span data-stu-id="13e37-129">If a mirroring session involves a witness, we recommend that you remove the witness before you perform a rolling update.</span></span>  
  
     <span data-ttu-id="13e37-130">**移除見證**</span><span class="sxs-lookup"><span data-stu-id="13e37-130">**To remove the witness**</span></span>  
  
    -   [<span data-ttu-id="13e37-131">從資料庫鏡像工作階段移除見證 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="13e37-131">Remove the Witness from a Database Mirroring Session &#40;SQL Server&#41;</span></span>](database-mirroring/remove-the-witness-from-a-database-mirroring-session-sql-server.md)  
  
### <a name="to-change-a-session-from-high-performance-mode-to-high-safety-mode"></a><span data-ttu-id="13e37-132">將工作階段從高效能模式變更為高安全性模式</span><span class="sxs-lookup"><span data-stu-id="13e37-132">To change a session from high-performance mode to high-safety mode</span></span>  
  
1.  <span data-ttu-id="13e37-133">如果鏡像工作階段是在高效能模式下執行，請在執行輪流更新之前，將作業模式變更為高安全性模式，而沒有自動容錯移轉。</span><span class="sxs-lookup"><span data-stu-id="13e37-133">If a mirroring session is running in high-performance mode, before you perform a rolling update, change the operating mode to high safety without automatic failover.</span></span> <span data-ttu-id="13e37-134">請使用下列其中一個方法：</span><span class="sxs-lookup"><span data-stu-id="13e37-134">Use one of the following methods:</span></span>  
  
    -   <span data-ttu-id="13e37-135">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中：使用 [資料庫屬性] 對話方塊的[鏡像頁面](../relational-databases/databases/database-properties-mirroring-page.md)，將 [作業模式] 選項變更為 [不具有自動容錯移轉的高安全性 (同步)]。</span><span class="sxs-lookup"><span data-stu-id="13e37-135">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]: Change the **Operating mode** option to **High safety without automatic failover (synchronous)** by using the [Mirroring Page](../relational-databases/databases/database-properties-mirroring-page.md) of the **Database Properties** dialog box.</span></span> <span data-ttu-id="13e37-136">如需如何存取此頁面的資訊，請參閱[啟動設定資料庫鏡像安全性精靈 &#40;SQL Server Management Studio&#41;](database-mirroring/start-the-configuring-database-mirroring-security-wizard.md)。</span><span class="sxs-lookup"><span data-stu-id="13e37-136">For information about how to access this page, see [Start the Configuring Database Mirroring Security Wizard &#40;SQL Server Management Studio&#41;](database-mirroring/start-the-configuring-database-mirroring-security-wizard.md).</span></span>  
  
    -   <span data-ttu-id="13e37-137">在 [!INCLUDE[tsql](../includes/tsql-md.md)] 中：將交易安全性設定為 FULL。</span><span class="sxs-lookup"><span data-stu-id="13e37-137">In [!INCLUDE[tsql](../includes/tsql-md.md)]: Set transaction safety to FULL.</span></span> <span data-ttu-id="13e37-138">如需詳細資訊，請參閱[在資料庫鏡像工作階段中變更交易安全性 &#40;Transact-SQL&#41;](database-mirroring/change-transaction-safety-in-a-database-mirroring-session-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="13e37-138">For more information, see [Change Transaction Safety in a Database Mirroring Session &#40;Transact-SQL&#41;](database-mirroring/change-transaction-safety-in-a-database-mirroring-session-transact-sql.md).</span></span>  
  
### <a name="to-perform-the-rolling-update"></a><span data-ttu-id="13e37-139">若要執行輪流更新</span><span class="sxs-lookup"><span data-stu-id="13e37-139">To perform the rolling update</span></span>  
  
1.  <span data-ttu-id="13e37-140">若要讓停機時間減至最少，我們建議您採取以下作法：在所有鏡像工作階段中更新目前為鏡像伺服器的任何鏡像夥伴伺服器，藉以開始輪流更新。</span><span class="sxs-lookup"><span data-stu-id="13e37-140">To minimize downtime, we recommend the following: Start the rolling update by updating any mirroring partner that is currently the mirror server in all its mirroring sessions.</span></span> <span data-ttu-id="13e37-141">您在此時可能必須更新多個伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="13e37-141">You might have to update multiple server instances at this point.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="13e37-142">您可以在輪流更新程序的任何時間更新見證。</span><span class="sxs-lookup"><span data-stu-id="13e37-142">A witness can be updated at any point in the rolling update process.</span></span> <span data-ttu-id="13e37-143">例如，如果伺服器執行個體在工作階段 1 為鏡像伺服器，而在工作階段 2 為見證，您可以立刻更新此伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="13e37-143">For example, if a server instance is a mirror server in Session 1 and is a witness in Session 2, you can update the server instance now.</span></span>  
  
     <span data-ttu-id="13e37-144">要更新的伺服器執行個體首先取決於鏡像工作階段的目前組態，如下面所述：</span><span class="sxs-lookup"><span data-stu-id="13e37-144">The server instance to update first depends on the current configuration of your mirroring sessions, as follows:</span></span>  
  
    -   <span data-ttu-id="13e37-145">如果有任何伺服器執行個體在所有鏡像工作階段中已經是鏡像伺服器，請在該伺服器執行個體上安裝 Service Pack 或 Hotfix。</span><span class="sxs-lookup"><span data-stu-id="13e37-145">If any server instance is already the mirror server in all of its mirroring sessions, install the service pack or the hotfix on that server instance.</span></span>  
  
    -   <span data-ttu-id="13e37-146">如果所有的伺服器執行個體目前在任何鏡像工作階段中都是主體伺服器，請先選取一個伺服器執行個體來更新。</span><span class="sxs-lookup"><span data-stu-id="13e37-146">If all of your server instances are currently the principal server in any mirroring sessions, select one server instance to update first.</span></span> <span data-ttu-id="13e37-147">然後，手動容錯移轉它的每一個主體資料庫，並透過安裝 Service Pack 或 Hotfix 來更新該伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="13e37-147">Then, manually fail over each of its principal databases and update that server instance by installing the service pack or the hotfix.</span></span>  
  
     <span data-ttu-id="13e37-148">在更新之後，伺服器執行個體會自動重新加入它的每一個鏡像工作階段。</span><span class="sxs-lookup"><span data-stu-id="13e37-148">After being updated, a server instance automatically rejoins each of its mirroring sessions.</span></span>  
  
     <span data-ttu-id="13e37-149">**若要執行手動容錯移轉**</span><span class="sxs-lookup"><span data-stu-id="13e37-149">**To perform a manual failover**</span></span>  
  
    -   [<span data-ttu-id="13e37-150">手動容錯移轉資料庫鏡像工作階段 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="13e37-150">Manually Fail Over a Database Mirroring Session &#40;SQL Server Management Studio&#41;</span></span>](database-mirroring/manually-fail-over-a-database-mirroring-session-sql-server-management-studio.md)  
  
    -   <span data-ttu-id="13e37-151">[手動容錯移轉資料庫鏡像工作階段 &#40;Transact-SQL&#41;](database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="13e37-151">[Manually Fail Over a Database Mirroring Session &#40;Transact-SQL&#41;](database-mirroring/manually-fail-over-a-database-mirroring-session-transact-sql.md).</span></span>  
  
     <span data-ttu-id="13e37-152">如需手動容錯移轉如何運作的資訊，請參閱[資料庫鏡像工作階段期間的角色切換 &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="13e37-152">For information about how manual failover works, see [Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="13e37-153">請針對剛剛更新鏡像伺服器執行個體的每一個鏡像工作階段，等候此工作階段同步處理。</span><span class="sxs-lookup"><span data-stu-id="13e37-153">For each mirroring session whose mirror server instance has just been updated, wait for the session to synchronize.</span></span> <span data-ttu-id="13e37-154">然後，連接到主體伺服器執行個體，並手動容錯移轉工作階段。</span><span class="sxs-lookup"><span data-stu-id="13e37-154">Then, connect to the principal server instance, and manually fail over the session.</span></span> <span data-ttu-id="13e37-155">在容錯移轉時，更新的伺服器執行個體會變成該工作階段的主體伺服器，而之前的主體伺服器會變成鏡像伺服器。</span><span class="sxs-lookup"><span data-stu-id="13e37-155">On failover, the updated server instance becomes the principal server for that session, and the former principal server becomes the mirror server.</span></span>  
  
     <span data-ttu-id="13e37-156">這個步驟的目標是要讓另一個伺服器執行個體在當做夥伴伺服器的每一個鏡像工作階段中變成鏡像伺服器。</span><span class="sxs-lookup"><span data-stu-id="13e37-156">The goal of this step is for another server instance to become the mirror server in every mirroring session in which it is a partner.</span></span>  
  
3.  <span data-ttu-id="13e37-157">在您容錯移轉之後，我們建議您在主體資料庫上執行 [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) 命令。</span><span class="sxs-lookup"><span data-stu-id="13e37-157">After you fail over, we recommend that you run the [DBCC CHECKDB](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql) command on the principal database.</span></span>  
  
4.  <span data-ttu-id="13e37-158">如果有任何伺服器執行個體目前在當做夥伴伺服器的所有鏡像工作階段中為鏡像伺服器，請在該伺服器執行個體上安裝 Service Pack 或 Hotfix。</span><span class="sxs-lookup"><span data-stu-id="13e37-158">Install the service pack or the hotfix on each server instance that is now the mirror server in all mirroring sessions in which it is a partner.</span></span> <span data-ttu-id="13e37-159">您在此時可能必須更新多部伺服器。</span><span class="sxs-lookup"><span data-stu-id="13e37-159">You might have to update multiple servers at this point.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="13e37-160">在複雜鏡像組態中，某些伺服器執行個體在一或多個鏡像工作階段中可能仍然是原始的主體伺服器。</span><span class="sxs-lookup"><span data-stu-id="13e37-160">In a complex mirroring configuration, some server instance might still be the original principal server in one or more mirroring sessions.</span></span> <span data-ttu-id="13e37-161">針對這些伺服器實例重複步驟2-4，直到所有相關的實例都更新為止。</span><span class="sxs-lookup"><span data-stu-id="13e37-161">Repeat steps 2-4 for those server instances until all instances involved are updated.</span></span>  
  
5.  <span data-ttu-id="13e37-162">繼續鏡像工作階段。</span><span class="sxs-lookup"><span data-stu-id="13e37-162">Resume the mirroring session.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="13e37-163">要等到更新見證之後，自動容錯移轉才能運作。</span><span class="sxs-lookup"><span data-stu-id="13e37-163">Automatic failover will not work until the witness has been updated.</span></span>  
  
6.  <span data-ttu-id="13e37-164">如果有任何其餘的伺服器執行個體在所有鏡像工作階段中為見證，請在該伺服器執行個體上安裝 Service Pack 或 Hotfix。</span><span class="sxs-lookup"><span data-stu-id="13e37-164">Install the service packs or hotfixes on any remaining server instance that is the witness in all its mirroring sessions.</span></span> <span data-ttu-id="13e37-165">在更新之後，見證會重新加入鏡像工作階段，而自動容錯移轉可再度運作。</span><span class="sxs-lookup"><span data-stu-id="13e37-165">After an updated witness rejoins a mirroring session, automatic failover becomes possible again.</span></span> <span data-ttu-id="13e37-166">您在此時可能必須更新多部伺服器。</span><span class="sxs-lookup"><span data-stu-id="13e37-166">You might have to update multiple servers at this point.</span></span>  
  
### <a name="to-return-a-session-to-high-performance-mode"></a><span data-ttu-id="13e37-167">讓工作階段回到高效能模式</span><span class="sxs-lookup"><span data-stu-id="13e37-167">To return a session to high-performance mode</span></span>  
  
1.  <span data-ttu-id="13e37-168">您可以選擇使用下列其中一個方法來回到高效能模式：</span><span class="sxs-lookup"><span data-stu-id="13e37-168">Optionally, return to high-performance mode by using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="13e37-169">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中：使用 [資料庫屬性] 對話方塊的[鏡像頁面](../relational-databases/databases/database-properties-mirroring-page.md)，將 [作業模式] 選項變更為 [高效能 (非同步)]。</span><span class="sxs-lookup"><span data-stu-id="13e37-169">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]: Change the **Operating mode** option to **High performance (asynchronous)** by using the [Mirroring Page](../relational-databases/databases/database-properties-mirroring-page.md) of the **Database Properties** dialog box.</span></span>  
  
    -   <span data-ttu-id="13e37-170">在中 [!INCLUDE[tsql](../includes/tsql-md.md)] ：使用[ALTER database](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring)將交易安全性設定為 OFF。</span><span class="sxs-lookup"><span data-stu-id="13e37-170">In [!INCLUDE[tsql](../includes/tsql-md.md)]: Use [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) to set transaction safety to OFF.</span></span>  
  
### <a name="to-return-a-witness-to-a-mirroring-session"></a><span data-ttu-id="13e37-171">讓見證回到鏡像工作階段</span><span class="sxs-lookup"><span data-stu-id="13e37-171">To return a witness to a mirroring session</span></span>  
  
1.  <span data-ttu-id="13e37-172">您可以選擇在高安全性模式下，重新建立每一個鏡像工作階段的見證。</span><span class="sxs-lookup"><span data-stu-id="13e37-172">Optionally, in high-safety mode, reestablish the witness to each mirroring session.</span></span>  
  
     <span data-ttu-id="13e37-173">**若要重新建立見證**</span><span class="sxs-lookup"><span data-stu-id="13e37-173">**To reestablish the witness**</span></span>  
  
    -   [<span data-ttu-id="13e37-174">新增或取代資料庫鏡像見證 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="13e37-174">Add or Replace a Database Mirroring Witness &#40;SQL Server Management Studio&#41;</span></span>](database-mirroring/add-or-replace-a-database-mirroring-witness-sql-server-management-studio.md)  
  
    -   [<span data-ttu-id="13e37-175">使用 Windows 驗證新增資料庫鏡像見證 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="13e37-175">Add a Database Mirroring Witness Using Windows Authentication &#40;Transact-SQL&#41;</span></span>](database-mirroring/add-a-database-mirroring-witness-using-windows-authentication-transact-sql.md)  
  
## <a name="see-also"></a><span data-ttu-id="13e37-176">另請參閱</span><span class="sxs-lookup"><span data-stu-id="13e37-176">See Also</span></span>  
 <span data-ttu-id="13e37-177">[ALTER DATABASE 資料庫鏡像 &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span><span class="sxs-lookup"><span data-stu-id="13e37-177">[ALTER DATABASE Database Mirroring &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-database-mirroring) </span></span>  
 <span data-ttu-id="13e37-178">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="13e37-178">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="13e37-179">[資料庫鏡像 &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="13e37-179">[Database Mirroring &#40;SQL Server&#41;](database-mirroring/database-mirroring-sql-server.md) </span></span>  
 <span data-ttu-id="13e37-180">[資料庫鏡像作業模式](database-mirroring/database-mirroring-operating-modes.md) </span><span class="sxs-lookup"><span data-stu-id="13e37-180">[Database Mirroring Operating Modes](database-mirroring/database-mirroring-operating-modes.md) </span></span>  
 <span data-ttu-id="13e37-181">[資料庫鏡像工作階段期間的角色切換 &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="13e37-181">[Role Switching During a Database Mirroring Session &#40;SQL Server&#41;](database-mirroring/role-switching-during-a-database-mirroring-session-sql-server.md) </span></span>  
 <span data-ttu-id="13e37-182">[啟動資料庫鏡像監視器 &#40;SQL Server Management Studio&#41;](database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="13e37-182">[Start Database Mirroring Monitor &#40;SQL Server Management Studio&#41;](database-mirroring/start-database-mirroring-monitor-sql-server-management-studio.md) </span></span>  
 [<span data-ttu-id="13e37-183">檢視鏡像資料庫的狀態 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="13e37-183">View the State of a Mirrored Database &#40;SQL Server Management Studio&#41;</span></span>](database-mirroring/view-the-state-of-a-mirrored-database-sql-server-management-studio.md)  
  
  
