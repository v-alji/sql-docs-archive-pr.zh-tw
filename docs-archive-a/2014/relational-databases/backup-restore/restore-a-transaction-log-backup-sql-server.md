---
title: 還原交易記錄備份 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoretlog.options.f1
- sql12.swb.restoretlog.general.f1
helpviewer_keywords:
- restore log
- backing up transaction logs [SQL Server], restoring
- transaction log backups [SQL Server], restoring
- restoring transaction logs [SQL Server], restoring backups
- transaction log restores [SQL Server], SQL Server Management Studio
ms.assetid: 1de2b888-78a6-4fb2-a647-ba4bf097caf3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 68fe4bbc199d6555bd490d25f92491100b8bbfcf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598463"
---
# <a name="restore-a-transaction-log-backup-sql-server"></a><span data-ttu-id="da96b-102">還原交易記錄備份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="da96b-102">Restore a Transaction Log Backup (SQL Server)</span></span>
  <span data-ttu-id="da96b-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中還原交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="da96b-103">This topic describes how to restore a transaction log backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="da96b-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="da96b-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="da96b-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="da96b-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="da96b-106">先決條件</span><span class="sxs-lookup"><span data-stu-id="da96b-106">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="da96b-107">安全性</span><span class="sxs-lookup"><span data-stu-id="da96b-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="da96b-108">**若要還原交易記錄備份，使用：**</span><span class="sxs-lookup"><span data-stu-id="da96b-108">**To restore a transaction log backup, using:**</span></span>  
  
     [<span data-ttu-id="da96b-109">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="da96b-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="da96b-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="da96b-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="da96b-111">相關工作</span><span class="sxs-lookup"><span data-stu-id="da96b-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="da96b-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="da96b-112">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="da96b-113">必要條件</span><span class="sxs-lookup"><span data-stu-id="da96b-113">Prerequisites</span></span>  
  
-   <span data-ttu-id="da96b-114">備份必須依照它們建立的順序還原。</span><span class="sxs-lookup"><span data-stu-id="da96b-114">Backups must be restored in the order in which they were created.</span></span> <span data-ttu-id="da96b-115">在還原特定交易記錄備份之前，您必須先還原下列先前的備份，而不必回復未認可的交易，即 WITH NORECOVERY：</span><span class="sxs-lookup"><span data-stu-id="da96b-115">Before you can restore a particular transaction log backup, you must first restore the following previous backups without rolling back uncommitted transactions, that is WITH NORECOVERY:</span></span>  
  
    -   <span data-ttu-id="da96b-116">在特定交易記錄備份之前產生的完整資料庫備份與前次差異備份 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="da96b-116">The full database backup and the last differential backup, if any, taken before the particular transaction log backup.</span></span> <span data-ttu-id="da96b-117">在建立完整或差異資料庫備份之前，資料庫必須已在使用完整復原模式或大量記錄復原模式。</span><span class="sxs-lookup"><span data-stu-id="da96b-117">Before the most recent full or differential database backup was created, the database must have been using the full recovery model or bulk-logged recovery model.</span></span>  
  
    -   <span data-ttu-id="da96b-118">在完整資料庫備份或差異備份 (如果您有還原其中一個) 之後及特定交易記錄備份之前產生的所有交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="da96b-118">All transaction log backups taken after the full database backup or the differential backup (if you restore one) and before the particular transaction log backup.</span></span> <span data-ttu-id="da96b-119">必須依建立記錄備份的順序來套用記錄備份，且記錄鏈中沒有任何間距。</span><span class="sxs-lookup"><span data-stu-id="da96b-119">Log backups must be applied in the sequence in which they were created, without any gaps in the log chain.</span></span>  
  
         <span data-ttu-id="da96b-120">如需交易記錄備份的詳細資訊，請參閱[交易記錄備份 &#40;SQL Server &#41;](transaction-log-backups-sql-server.md) 和[套用交易記錄備份 &#40;SQL Server &#41;](apply-transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="da96b-120">For more information about transaction log backups, see [Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) and [Apply Transaction Log Backups &#40;SQL Server&#41;](apply-transaction-log-backups-sql-server.md).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="da96b-121">Security</span><span class="sxs-lookup"><span data-stu-id="da96b-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="da96b-122">權限</span><span class="sxs-lookup"><span data-stu-id="da96b-122">Permissions</span></span>  
 <span data-ttu-id="da96b-123">RESTORE 權限提供給伺服器隨時可以取得其成員資格資訊的角色。</span><span class="sxs-lookup"><span data-stu-id="da96b-123">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="da96b-124">由於資料庫必須是可存取且未損毀，才能夠檢查固定資料庫角色成員資格，但執行 RESTORE 時未必如此；因此， **db_owner** 固定資料庫角色的成員並沒有 RESTORE 權限。</span><span class="sxs-lookup"><span data-stu-id="da96b-124">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="da96b-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="da96b-125">Using SQL Server Management Studio</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="da96b-126">還原的一般程序是在 [還原資料庫] 對話方塊中選取記錄備份，還有資料與差異備份。</span><span class="sxs-lookup"><span data-stu-id="da96b-126">The normal process of a restore is to select the log backups in the **Restore Database** dialog box along with the data and differential backups.</span></span>  
  
#### <a name="to-restore-a-transaction-log-backup"></a><span data-ttu-id="da96b-127">還原交易記錄備份</span><span class="sxs-lookup"><span data-stu-id="da96b-127">To restore a transaction log backup</span></span>  
  
1.  <span data-ttu-id="da96b-128">連線至適當的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體之後，在 [物件總管] 中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="da96b-128">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="da96b-129">展開 **[資料庫]** ，然後視資料庫而定，選取使用者資料庫，或者展開 **[系統資料庫]** 並選取一個系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="da96b-129">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="da96b-130">以滑鼠右鍵按一下資料庫，指向 [工作]，再指向 [還原]，然後按一下 [交易記錄]，這樣會開啟 [還原交易記錄] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="da96b-130">Right-click the database, point to **Tasks**, point to **Restore**, and then click **Transaction Log**, which opens the **Restore Transaction Log** dialog box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="da96b-131">如果 **[交易記錄]** 呈灰色，您可能需要先還原完整備份或差異備份。</span><span class="sxs-lookup"><span data-stu-id="da96b-131">If **Transaction Log** is grayed out, you may need to restore a full or differential backup first.</span></span> <span data-ttu-id="da96b-132">使用 **[資料庫備份]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="da96b-132">Use the **Database** backup dialog box.</span></span>  
  
4.  <span data-ttu-id="da96b-133">在 **[一般]** 頁面的 **[資料庫]** 清單方塊中，選取資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="da96b-133">On the **General** page, in the **Database** list box, select the name of a database.</span></span> <span data-ttu-id="da96b-134">只會列出處於正在還原狀態的資料庫。</span><span class="sxs-lookup"><span data-stu-id="da96b-134">Only databases in the restoring state are listed.</span></span>  
  
5.  <span data-ttu-id="da96b-135">若要指定要還原之備份組的來源與位置，請按一下下列任一個選項：</span><span class="sxs-lookup"><span data-stu-id="da96b-135">To specify the source and location of the backup sets to restore, click one of the following options:</span></span>  
  
    -   <span data-ttu-id="da96b-136">**從先前的資料庫備份**</span><span class="sxs-lookup"><span data-stu-id="da96b-136">**From previous backups of database**</span></span>  
  
         <span data-ttu-id="da96b-137">從下拉式清單中選取要還原的資料庫。</span><span class="sxs-lookup"><span data-stu-id="da96b-137">Select the database to restore from the drop-down list.</span></span> <span data-ttu-id="da96b-138">此清單僅包含已根據 **msdb** 備份記錄而備份的資料庫。</span><span class="sxs-lookup"><span data-stu-id="da96b-138">The list contains only databases that have been backed up according to the **msdb** backup history.</span></span>  
  
    -   <span data-ttu-id="da96b-139">**從檔案或磁帶**</span><span class="sxs-lookup"><span data-stu-id="da96b-139">**From file or tape**</span></span>  
  
         <span data-ttu-id="da96b-140">按一下瀏覽 ( **...** ) 按鈕，開啟 [選取備份裝置] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="da96b-140">Click the browse (**...**) button to open the **Select backup devices** dialog box.</span></span> <span data-ttu-id="da96b-141">在 **[備份媒體類型]** 方塊中，選取列出的其中一種裝置類型。</span><span class="sxs-lookup"><span data-stu-id="da96b-141">In the **Backup media type** box, select one of the listed device types.</span></span> <span data-ttu-id="da96b-142">若要選取 **[備份媒體]** 方塊中的一個或多個裝置，請按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="da96b-142">To select one or more devices for the **Backup media** box, click **Add**.</span></span>  
  
         <span data-ttu-id="da96b-143">將您要的裝置加入 **[備份媒體]** 清單方塊後，按一下 **[確定]** 即可回到 **[一般]** 頁面。</span><span class="sxs-lookup"><span data-stu-id="da96b-143">After you add the devices you want to the **Backup media** list box, click **OK** to return to the **General** page.</span></span>  
  
6.  <span data-ttu-id="da96b-144">在 **[選取要還原的交易記錄備份]** 方格中，選取要還原的備份。</span><span class="sxs-lookup"><span data-stu-id="da96b-144">In the **Select the transaction log backups to restore** grid, select the backups to restore.</span></span> <span data-ttu-id="da96b-145">此方格會列出選取的資料庫可用的交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="da96b-145">This grid lists the transaction log backups available for the selected database.</span></span> <span data-ttu-id="da96b-146">只有當資料庫的 **[第一個 LSN]** 大於 **[最後一個 LSN]** 時，才能使用記錄備份。</span><span class="sxs-lookup"><span data-stu-id="da96b-146">A log backup is available only if its **First LSN** greater than the **Last LSN** of the database.</span></span> <span data-ttu-id="da96b-147">記錄備份會依它們所含的記錄序號 (LSN) 順序列出，而且必須按這個順序還原。</span><span class="sxs-lookup"><span data-stu-id="da96b-147">Log backups are listed in the order of the log sequence numbers (LSN) they contain, and they must be restored in this order.</span></span>  
  
     <span data-ttu-id="da96b-148">下表列出方格的各資料行標頭，並描述各標頭的值。</span><span class="sxs-lookup"><span data-stu-id="da96b-148">The following table lists the column headers of the grid and describes their values.</span></span>  
  
    |<span data-ttu-id="da96b-149">頁首</span><span class="sxs-lookup"><span data-stu-id="da96b-149">Header</span></span>|<span data-ttu-id="da96b-150">值</span><span class="sxs-lookup"><span data-stu-id="da96b-150">Value</span></span>|  
    |------------|-----------|  
    |<span data-ttu-id="da96b-151">**Restore**</span><span class="sxs-lookup"><span data-stu-id="da96b-151">**Restore**</span></span>|<span data-ttu-id="da96b-152">選取的核取方塊表示要還原的備份組。</span><span class="sxs-lookup"><span data-stu-id="da96b-152">Selected check boxes indicate the backup sets to be restored.</span></span>|  
    |<span data-ttu-id="da96b-153">**名稱**</span><span class="sxs-lookup"><span data-stu-id="da96b-153">**Name**</span></span>|<span data-ttu-id="da96b-154">備份組的名稱。</span><span class="sxs-lookup"><span data-stu-id="da96b-154">Name of the backup set.</span></span>|  
    |<span data-ttu-id="da96b-155">**元件**</span><span class="sxs-lookup"><span data-stu-id="da96b-155">**Component**</span></span>|<span data-ttu-id="da96b-156">備份的元件：**資料庫**、**檔案** 或 \<blank> (適用於交易記錄)。</span><span class="sxs-lookup"><span data-stu-id="da96b-156">Backed-up component: **Database**, **File**, or \<blank> (for transaction logs).</span></span>|  
    |<span data-ttu-id="da96b-157">**Database**</span><span class="sxs-lookup"><span data-stu-id="da96b-157">**Database**</span></span>|<span data-ttu-id="da96b-158">執行備份所涉及的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="da96b-158">Name of the database involved in the backup operation.</span></span>|  
    |<span data-ttu-id="da96b-159">**開始日期**</span><span class="sxs-lookup"><span data-stu-id="da96b-159">**Start Date**</span></span>|<span data-ttu-id="da96b-160">備份作業開始的日期和時間，以用戶端的區域設定表示。</span><span class="sxs-lookup"><span data-stu-id="da96b-160">Date and time when the backup operation began, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="da96b-161">**完成日期**</span><span class="sxs-lookup"><span data-stu-id="da96b-161">**Finish Date**</span></span>|<span data-ttu-id="da96b-162">備份作業完成的日期和時間，以用戶端的區域設定表示。</span><span class="sxs-lookup"><span data-stu-id="da96b-162">Date and time when the backup operation finished, presented in the regional setting of the client.</span></span>|  
    |<span data-ttu-id="da96b-163">**第一個 LSN**</span><span class="sxs-lookup"><span data-stu-id="da96b-163">**First LSN**</span></span>|<span data-ttu-id="da96b-164">備份組內第一筆交易的記錄序號。</span><span class="sxs-lookup"><span data-stu-id="da96b-164">Log sequence number of the first transaction in the backup set.</span></span> <span data-ttu-id="da96b-165">針對檔案備份為空白。</span><span class="sxs-lookup"><span data-stu-id="da96b-165">Blank for file backups.</span></span>|  
    |<span data-ttu-id="da96b-166">**最後一個 LSN**</span><span class="sxs-lookup"><span data-stu-id="da96b-166">**Last LSN**</span></span>|<span data-ttu-id="da96b-167">備份組內最後一個交易的記錄序號。</span><span class="sxs-lookup"><span data-stu-id="da96b-167">Log sequence number of the last transaction in the backup set.</span></span> <span data-ttu-id="da96b-168">針對檔案備份為空白。</span><span class="sxs-lookup"><span data-stu-id="da96b-168">Blank for file backups.</span></span>|  
    |<span data-ttu-id="da96b-169">**檢查點 LSN**</span><span class="sxs-lookup"><span data-stu-id="da96b-169">**Checkpoint LSN**</span></span>|<span data-ttu-id="da96b-170">在建立備份時，最近的檢查點之記錄序號。</span><span class="sxs-lookup"><span data-stu-id="da96b-170">Log sequence number of the most recent checkpoint at the time the backup was created.</span></span>|  
    |<span data-ttu-id="da96b-171">**完整 LSN**</span><span class="sxs-lookup"><span data-stu-id="da96b-171">**Full LSN**</span></span>|<span data-ttu-id="da96b-172">最近的完整資料庫備份之記錄序號。</span><span class="sxs-lookup"><span data-stu-id="da96b-172">Log sequence number of the most recent full database backup.</span></span>|  
    |<span data-ttu-id="da96b-173">**Server**</span><span class="sxs-lookup"><span data-stu-id="da96b-173">**Server**</span></span>|<span data-ttu-id="da96b-174">執行備份作業之 Database Engine 執行個體的名稱。</span><span class="sxs-lookup"><span data-stu-id="da96b-174">Name of the Database Engine instance that performed the backup operation.</span></span>|  
    |<span data-ttu-id="da96b-175">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="da96b-175">**User Name**</span></span>|<span data-ttu-id="da96b-176">執行備份作業之使用者的名稱。</span><span class="sxs-lookup"><span data-stu-id="da96b-176">Name of the user who performed the backup operation.</span></span>|  
    |<span data-ttu-id="da96b-177">**大小**</span><span class="sxs-lookup"><span data-stu-id="da96b-177">**Size**</span></span>|<span data-ttu-id="da96b-178">備份組的大小，以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="da96b-178">Size of the backup set in bytes.</span></span>|  
    |<span data-ttu-id="da96b-179">**位置**</span><span class="sxs-lookup"><span data-stu-id="da96b-179">**Position**</span></span>|<span data-ttu-id="da96b-180">備份組在磁碟區中的位置。</span><span class="sxs-lookup"><span data-stu-id="da96b-180">Position of the backup set in the volume.</span></span>|  
    |<span data-ttu-id="da96b-181">**到期**</span><span class="sxs-lookup"><span data-stu-id="da96b-181">**Expiration**</span></span>|<span data-ttu-id="da96b-182">備份組到期的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="da96b-182">Date and time the backup set expires.</span></span>|  
  
7.  <span data-ttu-id="da96b-183">選取下列其中一個：</span><span class="sxs-lookup"><span data-stu-id="da96b-183">Select one of the following:</span></span>  
  
    -   <span data-ttu-id="da96b-184">**時間點**</span><span class="sxs-lookup"><span data-stu-id="da96b-184">**Point in time**</span></span>  
  
         <span data-ttu-id="da96b-185">保留預設值 ([最近可能的])，或按一下瀏覽按鈕，開啟 [還原時間點] 對話方塊，選取特定的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="da96b-185">Either retain the default (**Most recent possible**) or select a specific date and time by clicking the browse button, which opens the **Point in Time Restore** dialog box.</span></span>  
  
    -   <span data-ttu-id="da96b-186">**標示的交易**</span><span class="sxs-lookup"><span data-stu-id="da96b-186">**Marked transaction**</span></span>  
  
         <span data-ttu-id="da96b-187">還原資料庫至先前標示的交易。</span><span class="sxs-lookup"><span data-stu-id="da96b-187">Restore the database to a previously marked transaction.</span></span> <span data-ttu-id="da96b-188">選取此選項會啟動 **[選取標示的交易]** 對話方塊，顯示一個方格，列出所選交易記錄備份中可用的已標示交易。</span><span class="sxs-lookup"><span data-stu-id="da96b-188">Selecting this option launches the **Select Marked Transaction** dialog box, which displays a grid listing the marked transactions available in the selected transaction log backups.</span></span>  
  
         <span data-ttu-id="da96b-189">依預設，會還原到標示的交易，但是不含該交易。</span><span class="sxs-lookup"><span data-stu-id="da96b-189">By default, the restore is up to, but excluding, the marked transaction.</span></span> <span data-ttu-id="da96b-190">若也要還原標示的交易，請選取 **[包含標示的交易]** 。</span><span class="sxs-lookup"><span data-stu-id="da96b-190">To restore the marked transaction also, select **Include marked transaction**.</span></span>  
  
         <span data-ttu-id="da96b-191">下表列出方格的各資料行標頭，並描述各標頭的值。</span><span class="sxs-lookup"><span data-stu-id="da96b-191">The following table lists the column headers of the grid and describes their values.</span></span>  
  
        |<span data-ttu-id="da96b-192">頁首</span><span class="sxs-lookup"><span data-stu-id="da96b-192">Header</span></span>|<span data-ttu-id="da96b-193">值</span><span class="sxs-lookup"><span data-stu-id="da96b-193">Value</span></span>|  
        |------------|-----------|  
        |\<blank>|<span data-ttu-id="da96b-194">顯示選取標示的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="da96b-194">Displays a checkbox for selecting the mark.</span></span>|  
        |<span data-ttu-id="da96b-195">**交易標示**</span><span class="sxs-lookup"><span data-stu-id="da96b-195">**Transaction Mark**</span></span>|<span data-ttu-id="da96b-196">在認可交易時，由使用者所指定之標示交易的名稱。</span><span class="sxs-lookup"><span data-stu-id="da96b-196">Name of the marked transaction specified by the user when the transaction was committed.</span></span>|  
        |<span data-ttu-id="da96b-197">**日期**</span><span class="sxs-lookup"><span data-stu-id="da96b-197">**Date**</span></span>|<span data-ttu-id="da96b-198">認可交易的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="da96b-198">Date and time of the transaction when it was committed.</span></span> <span data-ttu-id="da96b-199">交易日期和時間是依照 **msdbgmarkhistory** 資料表中記錄的顯示，而非依照用戶端電腦的日期和時間。</span><span class="sxs-lookup"><span data-stu-id="da96b-199">Transaction date and time are displayed as recorded in the **msdbgmarkhistory** table, not in the client computer's date and time.</span></span>|  
        |<span data-ttu-id="da96b-200">**說明**</span><span class="sxs-lookup"><span data-stu-id="da96b-200">**Description**</span></span>|<span data-ttu-id="da96b-201">在認可交易時，由使用者所指定之標示交易的描述 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="da96b-201">Description of marked transaction specified by the user when the transaction was committed (if any).</span></span>|  
        |<span data-ttu-id="da96b-202">**LSN**</span><span class="sxs-lookup"><span data-stu-id="da96b-202">**LSN**</span></span>|<span data-ttu-id="da96b-203">標示之交易的記錄序號。</span><span class="sxs-lookup"><span data-stu-id="da96b-203">Log sequence number of the marked transaction.</span></span>|  
        |<span data-ttu-id="da96b-204">**Database**</span><span class="sxs-lookup"><span data-stu-id="da96b-204">**Database**</span></span>|<span data-ttu-id="da96b-205">認可標示的交易之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="da96b-205">Name of the database where the marked transaction was committed.</span></span>|  
        |<span data-ttu-id="da96b-206">**使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="da96b-206">**User Name**</span></span>|<span data-ttu-id="da96b-207">認可標示的交易之資料庫使用者的名稱。</span><span class="sxs-lookup"><span data-stu-id="da96b-207">Name of the database user who committed the marked transaction.</span></span>|  
  
8.  <span data-ttu-id="da96b-208">若要檢視或選取進階選項，請按一下 **[選取頁面]** 窗格中的 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="da96b-208">To view or select the advanced options, click **Options** in the **Select a page** pane.</span></span>  
  
9. <span data-ttu-id="da96b-209">在 **[還原選項]** 區段中，選項如下：</span><span class="sxs-lookup"><span data-stu-id="da96b-209">In the **Restore options** section, the choices are:</span></span>  
  
    -   <span data-ttu-id="da96b-210">**保留複寫設定 (WITH KEEP_REPLICATION)**</span><span class="sxs-lookup"><span data-stu-id="da96b-210">**Preserve the replication settings (WITH KEEP_REPLICATION)**</span></span>  
  
         <span data-ttu-id="da96b-211">將發行資料庫還原至並非建立該資料庫的伺服器時，就會保留複寫設定。</span><span class="sxs-lookup"><span data-stu-id="da96b-211">Preserves the replication settings when restoring a published database to a server other than the server where the database was created.</span></span>  
  
         <span data-ttu-id="da96b-212">此選項僅適用于 [**回復未認可的交易，讓資料庫保持備**妥可用 ...] 選項 (稍後) ，這相當於使用選項還原備份。 `RECOVERY`</span><span class="sxs-lookup"><span data-stu-id="da96b-212">This option is available only with the **Leave the database ready for use by rolling back the uncommitted transactions...** option (described later), which is equivalent to restoring a backup with the `RECOVERY` option.</span></span>  
  
         <span data-ttu-id="da96b-213">核取此選項相當於 `KEEP_REPLICATION` 在語句中使用選項 [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` 。</span><span class="sxs-lookup"><span data-stu-id="da96b-213">Checking this option is equivalent to using the `KEEP_REPLICATION` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
    -   <span data-ttu-id="da96b-214">**還原每個備份之前先提示**</span><span class="sxs-lookup"><span data-stu-id="da96b-214">**Prompt before restoring each backup**</span></span>  
  
         <span data-ttu-id="da96b-215">還原每個備份組之前 (第一個之後)，這個選項會帶出 [繼續還原] 對話方塊，其中會要求您指出是否要繼續還原順序。</span><span class="sxs-lookup"><span data-stu-id="da96b-215">Before restoring each backup set (after the first), this option brings up the **Continue with Restore** dialog box, which asks you to indicate whether you want to continue the restore sequence.</span></span> <span data-ttu-id="da96b-216">這個對話方塊會顯示下一個媒體集名稱 (如果有)、備份組名稱，以及備份組描述。</span><span class="sxs-lookup"><span data-stu-id="da96b-216">This dialog displays the name of the next media set (if available), the backup set name, and backup set description.</span></span>  
  
         <span data-ttu-id="da96b-217">您必須為不同的媒體集交換磁帶時，這個選項特別有用。</span><span class="sxs-lookup"><span data-stu-id="da96b-217">This option is particularly useful when you must swap tapes for different media sets.</span></span> <span data-ttu-id="da96b-218">例如，您可以在伺服器只有一個磁帶裝置時使用。</span><span class="sxs-lookup"><span data-stu-id="da96b-218">For example, you can use it when the server has only one tape device.</span></span> <span data-ttu-id="da96b-219">等到您準備好繼續後，才能按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="da96b-219">Wait until you are ready to proceed before clicking **OK**.</span></span>  
  
         <span data-ttu-id="da96b-220">按一下 **[否]** 會讓資料庫保持在還原狀態。</span><span class="sxs-lookup"><span data-stu-id="da96b-220">Clicking **No** leaves the database in the restoring state.</span></span> <span data-ttu-id="da96b-221">在上次的還原完成之後，您可以隨時繼續還原順序。</span><span class="sxs-lookup"><span data-stu-id="da96b-221">At your convenience, you can continue the restore sequence after the last restore that completed.</span></span> <span data-ttu-id="da96b-222">如果下一個備份是資料或差異備份，請再次使用 **[還原資料庫]** 工作。</span><span class="sxs-lookup"><span data-stu-id="da96b-222">If the next backup is a data or differential backup, use the **Restore Database** task again.</span></span> <span data-ttu-id="da96b-223">如果下一個備份是記錄檔備份，請使用 **[還原交易記錄檔]** 工作。</span><span class="sxs-lookup"><span data-stu-id="da96b-223">If the next backup is a log backup, use the **Restore Transaction Log** task.</span></span>  
  
    -   <span data-ttu-id="da96b-224">**限制對還原資料庫的存取 (WITH RESTRICTED_USER)**</span><span class="sxs-lookup"><span data-stu-id="da96b-224">**Restrict access to the restored database (WITH RESTRICTED_USER)**</span></span>  
  
         <span data-ttu-id="da96b-225">僅有 **db_owner**、 **dbcreator**或 **系統管理員**的成員可以使用還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="da96b-225">Makes the restored database available only to the members of **db_owner**, **dbcreator**, or **sysadmin**.</span></span>  
  
         <span data-ttu-id="da96b-226">核取此選項相當於在 `RESTRICTED_USER` 語句中使用選項 [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` 。</span><span class="sxs-lookup"><span data-stu-id="da96b-226">Checking this option is synonymous to using the `RESTRICTED_USER` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
10. <span data-ttu-id="da96b-227">針對 **[復原狀態]** 選項，指定資料庫在還原作業之後的狀態。</span><span class="sxs-lookup"><span data-stu-id="da96b-227">For the **Recovery state** options, specify the state of the database after the restore operation.</span></span>  
  
    -   <span data-ttu-id="da96b-228">**回復未認可的交易，讓資料庫保持備妥可用。無法還原其他交易記錄。(RESTORE WITH RECOVERY)**</span><span class="sxs-lookup"><span data-stu-id="da96b-228">**Leave the database ready for use by rolling back uncommitted transactions. Additional transaction logs cannot be restored. (RESTORE WITH RECOVERY)**</span></span>  
  
         <span data-ttu-id="da96b-229">復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="da96b-229">Recovers the database.</span></span> <span data-ttu-id="da96b-230">此選項相當於 `RECOVERY` 語句中的選項 [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` 。</span><span class="sxs-lookup"><span data-stu-id="da96b-230">This option is equivalent to the `RECOVERY` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
         <span data-ttu-id="da96b-231">只有當您沒有任何要還原的記錄檔時，才選擇這個選項。</span><span class="sxs-lookup"><span data-stu-id="da96b-231">Choose this option only if you have no log files you want to restore.</span></span>  
  
    -   <span data-ttu-id="da96b-232">**讓資料庫保持不運作，且不回復未認可的交易。可以還原其他交易記錄。(RESTORE WITH NORECOVERY)**</span><span class="sxs-lookup"><span data-stu-id="da96b-232">**Leave the database non-operational, and do not roll back uncommitted transactions. Additional transaction logs can be restored. (RESTORE WITH NORECOVERY)**</span></span>  
  
         <span data-ttu-id="da96b-233">讓資料庫處於無法復原狀態，也就是 `RESTORING` 的狀態。</span><span class="sxs-lookup"><span data-stu-id="da96b-233">Leaves the database unrecovered, in the `RESTORING` state.</span></span> <span data-ttu-id="da96b-234">此選項相當於 `NORECOVERY` 在語句中使用選項 [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` 。</span><span class="sxs-lookup"><span data-stu-id="da96b-234">This option is equivalent to using the `NORECOVERY` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
         <span data-ttu-id="da96b-235">選擇這個選項時，將無法使用 **[保留複寫設定]** 選項。</span><span class="sxs-lookup"><span data-stu-id="da96b-235">When you choose this option, the **Preserve replication settings** option is unavailable.</span></span>  
  
        > [!IMPORTANT]  
        >  <span data-ttu-id="da96b-236">若為鏡像或次要資料庫，請一律選取這個選項。</span><span class="sxs-lookup"><span data-stu-id="da96b-236">For a mirror or secondary database, always select this option.</span></span>  
  
    -   <span data-ttu-id="da96b-237">**讓資料庫保持唯讀模式。恢復未認可的交易，但是將恢復動作儲存在檔案中，以便能夠反轉復原結果。(RESTORE WITH STANDBY)**</span><span class="sxs-lookup"><span data-stu-id="da96b-237">**Leave the database in read-only mode. Undo uncommitted transactions, but save the undo actions in a file so that recovery effects can be reversed. (RESTORE WITH STANDBY)**</span></span>  
  
         <span data-ttu-id="da96b-238">讓資料庫處於待命狀態。</span><span class="sxs-lookup"><span data-stu-id="da96b-238">Leaves the database in a standby state.</span></span> <span data-ttu-id="da96b-239">此選項相當於 `STANDBY` 在語句中使用選項 [!INCLUDE[tsql](../../includes/tsql-md.md)] `RESTORE` 。</span><span class="sxs-lookup"><span data-stu-id="da96b-239">This option is equivalent to using the `STANDBY` option in a [!INCLUDE[tsql](../../includes/tsql-md.md)]`RESTORE` statement.</span></span>  
  
         <span data-ttu-id="da96b-240">您必須指定待命資料庫檔案，才能選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="da96b-240">Choosing this option requires that you specify a standby file.</span></span>  
  
11. <span data-ttu-id="da96b-241">在 **[待命資料庫檔案]** 文字方塊中指定待命資料庫檔案 (選擇性)。</span><span class="sxs-lookup"><span data-stu-id="da96b-241">Optionally, specify a standby file name in the **Standby file** text box.</span></span> <span data-ttu-id="da96b-242">如果您讓資料庫處於唯讀模式，就需要指定此選項。</span><span class="sxs-lookup"><span data-stu-id="da96b-242">This option is required if you leave the database in read-only mode.</span></span> <span data-ttu-id="da96b-243">您可以瀏覽待命資料庫檔案，或者在文字方塊中輸入其路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="da96b-243">You can browse for the standby file or type its pathname in the text box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="da96b-244">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="da96b-244">Using Transact-SQL</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="da96b-245">我們建議您在每一個 RESTORE 陳述式中永遠明確指定 WITH NORECOVERY 或 WITH RECOVERY，以避免模稜兩可。</span><span class="sxs-lookup"><span data-stu-id="da96b-245">We recommend that you always explicitly specify either WITH NORECOVERY or WITH RECOVERY in every RESTORE statement to eliminate ambiguity.</span></span> <span data-ttu-id="da96b-246">這在撰寫指令碼時尤其重要。</span><span class="sxs-lookup"><span data-stu-id="da96b-246">This is particularly important when writing scripts.</span></span>  
  
#### <a name="to-restore-a-transaction-log-backup"></a><span data-ttu-id="da96b-247">還原交易記錄備份</span><span class="sxs-lookup"><span data-stu-id="da96b-247">To restore a transaction log backup</span></span>  
  
1.  <span data-ttu-id="da96b-248">執行 RESTORE LOG 陳述式以套用交易記錄備份，請指定：</span><span class="sxs-lookup"><span data-stu-id="da96b-248">Execute the RESTORE LOG statement to apply the transaction log backup, specifying:</span></span>  
  
    -   <span data-ttu-id="da96b-249">交易記錄檔要套用的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="da96b-249">The name of the database to which the transaction log will be applied.</span></span>  
  
    -   <span data-ttu-id="da96b-250">用於還原交易記錄備份的備份裝置。</span><span class="sxs-lookup"><span data-stu-id="da96b-250">The backup device where the transaction log backup will be restored from.</span></span>  
  
    -   <span data-ttu-id="da96b-251">NORECOVERY 子句。</span><span class="sxs-lookup"><span data-stu-id="da96b-251">The NORECOVERY clause.</span></span>  
  
     <span data-ttu-id="da96b-252">此陳述式的基本語法如下：</span><span class="sxs-lookup"><span data-stu-id="da96b-252">The basic syntax for this statement is as follows:</span></span>  
  
     <span data-ttu-id="da96b-253">RESTORE LOG *資料庫名稱* FROM <備份裝置> WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="da96b-253">RESTORE LOG *database_name* FROM <backup_device> WITH NORECOVERY.</span></span>  
  
     <span data-ttu-id="da96b-254">其中，*資料庫名稱* 為資料庫名稱，而 <備份裝置> 為裝置名稱 (內含要還原的記錄備份)。</span><span class="sxs-lookup"><span data-stu-id="da96b-254">Where *database_name* is the name of database and <backup_device>is the name of the device that contains the log backup being restored.</span></span>  
  
2.  <span data-ttu-id="da96b-255">對於需要套用的每個交易記錄備份，請重複步驟 1。</span><span class="sxs-lookup"><span data-stu-id="da96b-255">Repeat step 1 for each transaction log backup you have to apply.</span></span>  
  
3.  <span data-ttu-id="da96b-256">依還原順序還原最後一個備份之後，若要復原資料庫，請使用下列其中一個陳述式：</span><span class="sxs-lookup"><span data-stu-id="da96b-256">After restoring the last backup in your restore sequence, to recover the database use one of the following statements:</span></span>  
  
    -   <span data-ttu-id="da96b-257">在最後一個 RESTORE LOG 陳述式之中復原資料庫：</span><span class="sxs-lookup"><span data-stu-id="da96b-257">Recover the database as part of the last RESTORE LOG statement:</span></span>  
  
        ```  
        RESTORE LOG <database_name> FROM <backup_device> WITH RECOVERY;  
        GO  
        ```  
  
    -   <span data-ttu-id="da96b-258">使用不同的 RESTORE DATABASE 陳述式來等待復原資料庫：</span><span class="sxs-lookup"><span data-stu-id="da96b-258">Wait to recover the database by using a separate RESTORE DATABASE statement:</span></span>  
  
        ```  
        RESTORE LOG <database_name> FROM <backup_device> WITH NORECOVERY;   
        RESTORE DATABASE <database_name> WITH RECOVERY;  
        GO  
        ```  
  
         <span data-ttu-id="da96b-259">等待復原資料庫，可讓您有機會確認是否已經還原所有必要的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="da96b-259">Waiting to recover the database gives you the opportunity to verify that you have restored all of the necessary log backups.</span></span> <span data-ttu-id="da96b-260">在執行時間點還原時，這個方法是較明智的。</span><span class="sxs-lookup"><span data-stu-id="da96b-260">This approach is often advisable when you are performing a point-in-time restore.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="da96b-261">如果您建立鏡像資料庫，請省略復原步驟。</span><span class="sxs-lookup"><span data-stu-id="da96b-261">If you are creating a mirror database, omit the recovery step.</span></span> <span data-ttu-id="da96b-262">鏡像資料庫必須保留 RESTORING 狀態。</span><span class="sxs-lookup"><span data-stu-id="da96b-262">A mirror database must remain in the RESTORING state.</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="TsqlExample"></a> <span data-ttu-id="da96b-263">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="da96b-263">Examples (Transact-SQL)</span></span>  
 <span data-ttu-id="da96b-264">根據預設， [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫使用簡單復原模式。</span><span class="sxs-lookup"><span data-stu-id="da96b-264">By default, the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database uses the simple recovery model.</span></span> <span data-ttu-id="da96b-265">此範例需要修改資料庫以使用完整復原模式，如下所示：</span><span class="sxs-lookup"><span data-stu-id="da96b-265">The following examples require modifying the database to use the full recovery model, as follows:</span></span>  
  
```sql  
ALTER DATABASE AdventureWorks2012 SET RECOVERY FULL;  
```  
  
#### <a name="a-applying-a-single-transaction-log-backup"></a><span data-ttu-id="da96b-266">A.</span><span class="sxs-lookup"><span data-stu-id="da96b-266">A.</span></span> <span data-ttu-id="da96b-267">套用單一交易記錄備份</span><span class="sxs-lookup"><span data-stu-id="da96b-267">Applying a single transaction log backup</span></span>  
 <span data-ttu-id="da96b-268">下列範例一開始會使用名為 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 備份裝置上的完整資料庫備份來還原 `AdventureWorks2012_1`資料庫。</span><span class="sxs-lookup"><span data-stu-id="da96b-268">The following example starts by restoring the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database by using a full database backup that resides on a backup device named `AdventureWorks2012_1`.</span></span> <span data-ttu-id="da96b-269">此範例接著套用名為 `AdventureWorks2012_log`備份裝置上的第一個交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="da96b-269">The example then applies the first transaction log backup that resides on a backup device named `AdventureWorks2012_log`.</span></span> <span data-ttu-id="da96b-270">最後，此範例復原了資料庫。</span><span class="sxs-lookup"><span data-stu-id="da96b-270">Finally, the example recovers the database.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012  
   FROM AdventureWorks2012_1  
   WITH NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 1,  
   WITH NORECOVERY;  
GO  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
#### <a name="b-applying-multiple-transaction-log-backups"></a><span data-ttu-id="da96b-271">B.</span><span class="sxs-lookup"><span data-stu-id="da96b-271">B.</span></span> <span data-ttu-id="da96b-272">套用多個交易記錄備份</span><span class="sxs-lookup"><span data-stu-id="da96b-272">Applying multiple transaction log backups</span></span>  
 <span data-ttu-id="da96b-273">下列範例一開始會使用名為 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 備份裝置上的完整資料庫備份來還原 `AdventureWorks2012_1`資料庫。</span><span class="sxs-lookup"><span data-stu-id="da96b-273">The following example starts by restoring the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database by using a full database backup that resides on a backup device named `AdventureWorks2012_1`.</span></span> <span data-ttu-id="da96b-274">此範例接著逐一套用名為 `AdventureWorks2012_log`備份裝置上的前三個交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="da96b-274">The example then applies, one by one, the first three transaction log backups that reside on a backup device named `AdventureWorks2012_log`.</span></span> <span data-ttu-id="da96b-275">最後，此範例復原了資料庫。</span><span class="sxs-lookup"><span data-stu-id="da96b-275">Finally, the example recovers the database.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012  
   FROM AdventureWorks2012_1  
   WITH NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 1,  
   NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 2,  
   WITH NORECOVERY;  
GO  
RESTORE LOG AdventureWorks2012  
   FROM AdventureWorks2012_log  
   WITH FILE = 3,  
   WITH NORECOVERY;  
GO  
RESTORE DATABASE AdventureWorks2012  
   WITH RECOVERY;  
GO  
```  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="da96b-276">相關工作</span><span class="sxs-lookup"><span data-stu-id="da96b-276">Related Tasks</span></span>  
  
-   [<span data-ttu-id="da96b-277">備份交易記錄 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="da96b-277">Back Up a Transaction Log &#40;SQL Server&#41;</span></span>](back-up-a-transaction-log-sql-server.md)  
  
-   [<span data-ttu-id="da96b-278">還原資料庫備份 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="da96b-278">Restore a Database Backup &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-backup-using-ssms.md)  
  
-   [<span data-ttu-id="da96b-279">在完整復原模式下將資料庫還原至失敗點 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="da96b-279">Restore a Database to the Point of Failure Under the Full Recovery Model &#40;Transact-SQL&#41;</span></span>](restore-database-to-point-of-failure-full-recovery.md)  
  
-   [<span data-ttu-id="da96b-280">將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;</span><span class="sxs-lookup"><span data-stu-id="da96b-280">Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;</span></span>](restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md)  
  
-   [<span data-ttu-id="da96b-281">還原資料庫至標示的交易 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="da96b-281">Restore a Database to a Marked Transaction &#40;SQL Server Management Studio&#41;</span></span>](restore-a-database-to-a-marked-transaction-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="da96b-282">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da96b-282">See Also</span></span>  
 <span data-ttu-id="da96b-283">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="da96b-283">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 [<span data-ttu-id="da96b-284">套用交易記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="da96b-284">Apply Transaction Log Backups &#40;SQL Server&#41;</span></span>](apply-transaction-log-backups-sql-server.md)  
  
  
