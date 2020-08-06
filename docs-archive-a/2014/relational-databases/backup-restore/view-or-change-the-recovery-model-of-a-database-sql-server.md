---
title: 檢視或變更資料庫的復原模式 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], recovery models
- recovery [SQL Server], recovery model
- backing up databases [SQL Server], recovery models
- recovery models [SQL Server], switching
- recovery models [SQL Server], viewing
- database restores [SQL Server], recovery models
- modifying database recovery models
ms.assetid: 94918d1d-7c10-4be7-bf9f-27e00b003a0f
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 889080301109938f0514bd6b81265c100237ab60
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703013"
---
# <a name="view-or-change-the-recovery-model-of-a-database-sql-server"></a><span data-ttu-id="16738-102">檢視或變更資料庫的復原模式 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="16738-102">View or Change the Recovery Model of a Database (SQL Server)</span></span>
  <span data-ttu-id="16738-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視或變更資料庫的復原模式。</span><span class="sxs-lookup"><span data-stu-id="16738-103">This topic describes how to view or change the recovery model of a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="16738-104">「復原模式」  是一項資料庫屬性，可控制交易的記錄方式、是否需要 (及允許) 備份交易記錄，以及可用的還原作業類型。</span><span class="sxs-lookup"><span data-stu-id="16738-104">A *recovery model* is a database property that controls how transactions are logged, whether the transaction log requires (and allows) backing up, and what kinds of restore operations are available.</span></span> <span data-ttu-id="16738-105">復原模式共有三種：簡單、完整和大量記錄。</span><span class="sxs-lookup"><span data-stu-id="16738-105">Three recovery models exist: simple, full, and bulk-logged.</span></span> <span data-ttu-id="16738-106">一般而言，資料庫會使用完整復原模式或簡單復原模式。</span><span class="sxs-lookup"><span data-stu-id="16738-106">Typically, a database uses the full recovery model or simple recovery model.</span></span> <span data-ttu-id="16738-107">資料庫可以隨時切換到另一個復原模式。</span><span class="sxs-lookup"><span data-stu-id="16738-107">A database can be switched to another recovery model at any time.</span></span> <span data-ttu-id="16738-108">**model** 資料庫會設定新資料庫的預設復原模式。</span><span class="sxs-lookup"><span data-stu-id="16738-108">The **model** database sets the default recovery model of new databases.</span></span>  
  
 <span data-ttu-id="16738-109">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="16738-109">**In This Topic**</span></span>  
  
-   <span data-ttu-id="16738-110">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="16738-110">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="16738-111">建議</span><span class="sxs-lookup"><span data-stu-id="16738-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="16738-112">安全性</span><span class="sxs-lookup"><span data-stu-id="16738-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="16738-113">**若要使用下列項目檢視或變更資料庫的復原模式：**</span><span class="sxs-lookup"><span data-stu-id="16738-113">**To view or change the recovery model of a database, using:**</span></span>  
  
     [<span data-ttu-id="16738-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="16738-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="16738-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="16738-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="16738-116">**後續操作建議：**  [變更復原模式之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="16738-116">**Follow Up Recommendations:**  [After You Change the Recovery Model](#FollowUp)</span></span>  
  
-   [<span data-ttu-id="16738-117">相關工作</span><span class="sxs-lookup"><span data-stu-id="16738-117">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="16738-118">開始之前</span><span class="sxs-lookup"><span data-stu-id="16738-118">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="16738-119">建議</span><span class="sxs-lookup"><span data-stu-id="16738-119">Recommendations</span></span>  
  
-   <span data-ttu-id="16738-120">從完整復原模式或大量記錄復原模式切換之前，請備份交易記錄。</span><span class="sxs-lookup"><span data-stu-id="16738-120">Before switching from the full recovery or bulk-logged recovery model, back up the transaction log.</span></span>  
  
-   <span data-ttu-id="16738-121">在大量記錄模式下無法使用時間點復原。</span><span class="sxs-lookup"><span data-stu-id="16738-121">Point-in-time recovery is not possible with bulk-logged model.</span></span> <span data-ttu-id="16738-122">因此，如果您在可能需要交易記錄還原的大量記錄復原模式下執行交易，則這些交易可能會有資料遺失的風險。</span><span class="sxs-lookup"><span data-stu-id="16738-122">Therefore, if you run transactions under the bulk-logged recovery model that might require a transaction log restore, these transactions could be exposed to data loss.</span></span> <span data-ttu-id="16738-123">若要在災難復原的情況下獲得最佳資料復原能力，建議您只能在下列情況下切換到大量記錄復原模式，以避免資料遺失：</span><span class="sxs-lookup"><span data-stu-id="16738-123">To maximize data recoverability in a disaster-recovery scenario, we recommend that you switch to the bulk-logged recovery model only under the following conditions:</span></span>  
  
    -   <span data-ttu-id="16738-124">資料庫中目前不允許有使用者。</span><span class="sxs-lookup"><span data-stu-id="16738-124">Users are currently not allowed in the database.</span></span>  
  
    -   <span data-ttu-id="16738-125">大量處理期間進行的所有修改都可復原，不必依賴建立記錄備份；例如，重新執行大量處理序。</span><span class="sxs-lookup"><span data-stu-id="16738-125">All modifications made during bulk processing are recoverable without depending on taking a log backup; for example, by re-running the bulk processes.</span></span>  
  
     <span data-ttu-id="16738-126">如果您滿足這兩項條件，還原大量記錄復原模式下備份的交易記錄時，就不必擔心資料遺失。</span><span class="sxs-lookup"><span data-stu-id="16738-126">If you satisfy these two conditions, you will not be exposed to any data loss while restoring a transaction log that was backed up under the bulk-logged recovery model..</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="16738-127">如果您在大量作業期間切換到完整復原模式，大量作業的記錄將從最小記錄變成完整記錄，反之亦然。</span><span class="sxs-lookup"><span data-stu-id="16738-127">If you switch to the full recovery model during a bulk operation, the logging of the bulk operation changes from minimal logging to full logging, and vice versa.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="16738-128">Security</span><span class="sxs-lookup"><span data-stu-id="16738-128">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="16738-129">權限</span><span class="sxs-lookup"><span data-stu-id="16738-129">Permissions</span></span>  
 <span data-ttu-id="16738-130">需要資料庫的 ALTER 權限。</span><span class="sxs-lookup"><span data-stu-id="16738-130">Requires ALTER permission on the database.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="16738-131">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="16738-131">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-change-the-recovery-model"></a><span data-ttu-id="16738-132">檢視或變更復原模式</span><span class="sxs-lookup"><span data-stu-id="16738-132">To view or change the recovery model</span></span>  
  
1.  <span data-ttu-id="16738-133">連接到適當的 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體之後，請在 [物件總管] 中按一下伺服器名稱以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="16738-133">After connecting to the appropriate instance of the [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="16738-134">展開 **[資料庫]** ，然後視資料庫而定，選取使用者資料庫，或者展開 **[系統資料庫]** 並選取一個系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="16738-134">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="16738-135">以滑鼠右鍵按一下資料庫，然後按一下 [屬性]  ，這會開啟 [資料庫屬性]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="16738-135">Right-click the database, and then click **Properties**, which opens the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="16738-136">在 **[選取頁面]** 窗格中，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="16738-136">In the **Select a page** pane, click **Options**.</span></span>  
  
5.  <span data-ttu-id="16738-137">目前的復原模式會顯示在 **[復原模式]** 清單方塊中。</span><span class="sxs-lookup"><span data-stu-id="16738-137">The current recovery model is displayed in the **Recovery model** list box.</span></span>  
  
6.  <span data-ttu-id="16738-138">或者，您可以從不同的模式清單中選取來變更復原模式。</span><span class="sxs-lookup"><span data-stu-id="16738-138">Optionally, to change the recovery model select a different model list.</span></span> <span data-ttu-id="16738-139">這些選擇包括 [完整]  、[大量記錄]  或 [簡單]  。</span><span class="sxs-lookup"><span data-stu-id="16738-139">The choices are **Full**, **Bulk-logged**, or **Simple**.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="16738-140">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="16738-140">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-recovery-model"></a><span data-ttu-id="16738-141">檢視復原模式</span><span class="sxs-lookup"><span data-stu-id="16738-141">To view the recovery model</span></span>  
  
1.  <span data-ttu-id="16738-142">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="16738-142">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="16738-143">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="16738-143">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="16738-144">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="16738-144">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="16738-145">這個範例示範如何查詢 [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) 目錄檢視，以了解 **model** 資料庫的復原模式。</span><span class="sxs-lookup"><span data-stu-id="16738-145">This example shows how to query the [sys.databases](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) catalog view to learn the recovery model of the **model** database.</span></span>  
  
```sql  
SELECT name, recovery_model_desc  
   FROM sys.databases  
      WHERE name = 'model' ;  
GO  
  
```  
  
#### <a name="to-change-the-recovery-model"></a><span data-ttu-id="16738-146">變更復原模式</span><span class="sxs-lookup"><span data-stu-id="16738-146">To change the recovery model</span></span>  
  
1.  <span data-ttu-id="16738-147">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="16738-147">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="16738-148">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="16738-148">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="16738-149">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="16738-149">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="16738-150">這個範例示範如何使用 `model` ALTER DATABASE `FULL` 陳述式的 `SET RECOVERY` 選項，將 [資料庫的復原模式變更為](/sql/t-sql/statements/alter-database-transact-sql-set-options) 。</span><span class="sxs-lookup"><span data-stu-id="16738-150">This example shows how to change the recovery model in the `model` database to `FULL` by using the `SET RECOVERY` option of the [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql-set-options) statement.</span></span>  
  
```sql  
USE master ;  
ALTER DATABASE model SET RECOVERY FULL ;  
```  
  
##  <a name="follow-up-recommendations-after-you-change-the-recovery-model"></a><a name="FollowUp"></a><span data-ttu-id="16738-151">後續操作建議：變更復原模式之後</span><span class="sxs-lookup"><span data-stu-id="16738-151">Follow Up Recommendations: After You Change the Recovery Model</span></span>  
  
-   <span data-ttu-id="16738-152">**在完整模式與大量記錄復原模式之間切換之後**</span><span class="sxs-lookup"><span data-stu-id="16738-152">**After switching between the full and bulk-logged recovery models**</span></span>  
  
    -   <span data-ttu-id="16738-153">在完成大量作業之後，立即切換回完整復原模式。</span><span class="sxs-lookup"><span data-stu-id="16738-153">After completing the bulk operations, immediately switch back to full recovery mode.</span></span>  
  
    -   <span data-ttu-id="16738-154">從大量記錄復原模式切換回完整復原模式之後，請備份記錄檔。</span><span class="sxs-lookup"><span data-stu-id="16738-154">After switching from the bulk-logged recovery model back to the full recovery model, back up the log.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="16738-155">您的備份策略維持不變：持續執行定期資料庫備份、記錄備份及差異備份。</span><span class="sxs-lookup"><span data-stu-id="16738-155">Your backup strategy remains the same: continue performing periodic database, log, and differential backups.</span></span>  
  
-   <span data-ttu-id="16738-156">**從簡單復原模式切換之後**</span><span class="sxs-lookup"><span data-stu-id="16738-156">**After switching from the simple recovery model**</span></span>  
  
    -   <span data-ttu-id="16738-157">在切換至完整復原模式或大量記錄復原模式的作業之後，立即建立完整或差異資料庫備份，以便啟動記錄鏈結。</span><span class="sxs-lookup"><span data-stu-id="16738-157">Immediately after switching to the full recovery model or bulk-logged recovery model, take a full or differential database backup to start the log chain.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="16738-158">只有在第一次資料備份之後，切換到完整或大量記錄復原模式才會生效。</span><span class="sxs-lookup"><span data-stu-id="16738-158">The switch to the full or bulk-logged recovery model takes effect only after the first data backup.</span></span>  
  
    -   <span data-ttu-id="16738-159">排程定期記錄備份並據此更新還原計畫。</span><span class="sxs-lookup"><span data-stu-id="16738-159">Schedule regular log backups, and update your restore plan accordingly.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="16738-160">如果您沒有經常備份記錄，交易記錄會一直擴充，直到磁碟空間用盡為止。</span><span class="sxs-lookup"><span data-stu-id="16738-160">If you do not back up the log frequently enough, the transaction log can expand until it runs out of disk space.</span></span>  
  
-   <span data-ttu-id="16738-161">**切換到簡單復原模式之後**</span><span class="sxs-lookup"><span data-stu-id="16738-161">**After switching to the simple recovery model**</span></span>  
  
    -   <span data-ttu-id="16738-162">中止備份交易記錄的任何排程作業</span><span class="sxs-lookup"><span data-stu-id="16738-162">Discontinue any scheduled jobs for backing up the transaction log.</span></span>  
  
    -   <span data-ttu-id="16738-163">確定已排程定期資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="16738-163">Ensure periodic database backups are scheduled.</span></span> <span data-ttu-id="16738-164">備份資料庫是必要的動作，才能保護資料及截斷交易記錄中非使用中的部分。</span><span class="sxs-lookup"><span data-stu-id="16738-164">Backing up your database is essential both to protect your data and to truncate the inactive portion of the transaction log.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="16738-165">相關工作</span><span class="sxs-lookup"><span data-stu-id="16738-165">Related Tasks</span></span>  
  
-   [<span data-ttu-id="16738-166">建立完整資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="16738-166">Create a Full Database Backup &#40;SQL Server&#41;</span></span>](create-a-full-database-backup-sql-server.md)  
  
-   [<span data-ttu-id="16738-167">備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="16738-167">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="16738-168">建立作業</span><span class="sxs-lookup"><span data-stu-id="16738-168">Create a Job</span></span>](../../ssms/agent/create-a-job.md)  
  
-   [<span data-ttu-id="16738-169">Disable or Enable a Job</span><span class="sxs-lookup"><span data-stu-id="16738-169">Disable or Enable a Job</span></span>](../../ssms/agent/disable-or-enable-a-job.md)  
  
##  <a name="related-content"></a><a name="RelatedContent"></a> <span data-ttu-id="16738-170">相關內容</span><span class="sxs-lookup"><span data-stu-id="16738-170">Related Content</span></span>  
  
-   <span data-ttu-id="16738-171">[資料庫維護計畫](../maintenance-plans/maintenance-plans.md) (在《 [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] 線上叢書》中)</span><span class="sxs-lookup"><span data-stu-id="16738-171">[Database Maintenance Plans](../maintenance-plans/maintenance-plans.md) (in [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)] Books Online)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16738-172">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16738-172">See Also</span></span>  
 <span data-ttu-id="16738-173">[復原模式 &#40;SQL Server&#41;](recovery-models-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="16738-173">[Recovery Models &#40;SQL Server&#41;](recovery-models-sql-server.md) </span></span>  
 <span data-ttu-id="16738-174">[交易記錄 &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="16738-174">[The Transaction Log &#40;SQL Server&#41;](../logs/the-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="16738-175">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="16738-175">[ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql) </span></span>  
 <span data-ttu-id="16738-176">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="16738-176">[sys.databases &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-databases-transact-sql) </span></span>  
 [<span data-ttu-id="16738-177">復原模式 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="16738-177">Recovery Models &#40;SQL Server&#41;</span></span>](recovery-models-sql-server.md)  
  
  
