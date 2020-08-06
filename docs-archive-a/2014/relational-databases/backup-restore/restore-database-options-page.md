---
title: 還原資料庫 (選項頁面) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
f1_keywords:
- sql12.swb.restoredb.options.f1
ms.assetid: 9a75d48b-c25f-40f3-8ea1-32cfa8211754
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d60474b5d72ab9745500325dfd523f83f155343c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595133"
---
# <a name="restore-database-options-page"></a><span data-ttu-id="2538f-102">還原資料庫 (選項頁面)</span><span class="sxs-lookup"><span data-stu-id="2538f-102">Restore Database (Options Page)</span></span>
  <span data-ttu-id="2538f-103">使用 [還原資料庫]  對話方塊的 [選項]  頁面，即可修改還原作業的行為和結果。</span><span class="sxs-lookup"><span data-stu-id="2538f-103">Use the **Options** page of the **Restore Database** dialog box to modify the behavior and outcome of the restore operation.</span></span>  
  
 <span data-ttu-id="2538f-104">**若要使用 SQL Server Management Studio 還原資料庫備份**</span><span class="sxs-lookup"><span data-stu-id="2538f-104">**To use SQL Server Management Studio to restore a database backup**</span></span>  
  
-   [<span data-ttu-id="2538f-105">RESTORE &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2538f-105">RESTORE &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/restore-statements-transact-sql)  
  
-   [<span data-ttu-id="2538f-106">定義磁帶機的邏輯備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2538f-106">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
> [!NOTE]  
>  <span data-ttu-id="2538f-107">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]指定還原工作時，可以針對這個還原作業產生包含 RESTORE 陳述式的對應 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="2538f-107">When you specify a restore task by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you can generate a corresponding [!INCLUDE[tsql](../../includes/tsql-md.md)] script containing the RESTORE statements for this restore operation.</span></span> <span data-ttu-id="2538f-108">若要產生指令碼，請按一下 [指令碼]  ，然後選取指令碼的目的地。</span><span class="sxs-lookup"><span data-stu-id="2538f-108">To generate the script, click **Script** and then select a destination for the script.</span></span> <span data-ttu-id="2538f-109">如需 RESTORE 語法的資訊，請參閱 [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2538f-109">For information about the RESTORE syntax, see [RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql).</span></span>  
  
## <a name="options"></a><span data-ttu-id="2538f-110">選項。</span><span class="sxs-lookup"><span data-stu-id="2538f-110">Options</span></span>  
  
### <a name="restore-options"></a><span data-ttu-id="2538f-111">還原選項</span><span class="sxs-lookup"><span data-stu-id="2538f-111">Restore options</span></span>  
 <span data-ttu-id="2538f-112">若要修改還原作業的行為方面，可以使用 [還原選項]  面板的選項。</span><span class="sxs-lookup"><span data-stu-id="2538f-112">To modify aspects of the behavior of the restore operation, use the options of the **Restore options** panel.</span></span>  
  
 <span data-ttu-id="2538f-113">**覆寫現有的資料庫 [WITH REPLACE]**</span><span class="sxs-lookup"><span data-stu-id="2538f-113">**Overwrite the existing database [WITH REPLACE]**</span></span>  
 <span data-ttu-id="2538f-114">還原作業將會覆寫目前正在使用資料庫名稱 (在 [還原資料庫]  對話方塊之 [一般](../../integration-services/general-page-of-integration-services-designers-options.md) 頁面的 [還原至]  欄位中指定) 的任何資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="2538f-114">The restore operation will overwrite the files of any database that is currently using the database name that you are specifying in the **Restore to**field on the [General](../../integration-services/general-page-of-integration-services-designers-options.md) page of the **Restore Database** dialog box.</span></span> <span data-ttu-id="2538f-115">即使是將備份從不同的資料庫還原為現有的資料庫名稱，現有資料庫的檔案也會遭到覆寫。</span><span class="sxs-lookup"><span data-stu-id="2538f-115">The files of the existing database will be overwritten even if you are restoring backups from a different database to the existing database name.</span></span> <span data-ttu-id="2538f-116">選取此選項相當於使用 [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) 陳述式 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 的 REPLACE 選項。</span><span class="sxs-lookup"><span data-stu-id="2538f-116">Selecting this option is equivalent to using the REPLACE option in a [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) statement ([!INCLUDE[tsql](../../includes/tsql-md.md)]).</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="2538f-117">請仔細考慮之後再使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="2538f-117">Use this option only after careful consideration.</span></span> <span data-ttu-id="2538f-118">如需詳細資訊，請參閱 [RESTORE 引數 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2538f-118">For more information, see [RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql).</span></span>  
  
 <span data-ttu-id="2538f-119">**保留複寫設定 [WITH KEEP_REPLICATION]**</span><span class="sxs-lookup"><span data-stu-id="2538f-119">**Preserve the replication settings [WITH KEEP_REPLICATION]**</span></span>  
 <span data-ttu-id="2538f-120">將發行資料庫還原至並非建立該資料庫的伺服器時，就會保留複寫設定。</span><span class="sxs-lookup"><span data-stu-id="2538f-120">Preserves the replication settings when restoring a published database to a server other than the server where the database was created.</span></span> <span data-ttu-id="2538f-121">只有在建立備份時複寫了資料庫，這個選項才會相關。</span><span class="sxs-lookup"><span data-stu-id="2538f-121">This option is relevant only if the database was replicated when the backup was created.</span></span>  
  
 <span data-ttu-id="2538f-122">這個選項只能搭配 [回復未認可的交易，讓資料庫保持備妥可用]  選項 (本資料表稍後會描述) 使用，這相當於使用 RECOVERY 選項來還原備份。</span><span class="sxs-lookup"><span data-stu-id="2538f-122">This option is available only with the **Leave the database ready for use by rolling back the uncommitted transactions** option (described later in this table), which is equivalent to restoring a backup with the RECOVERY option.</span></span>  
  
 <span data-ttu-id="2538f-123">選取此選項相當於使用 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 陳述式中的 KEEP_REPLICATION 選項。</span><span class="sxs-lookup"><span data-stu-id="2538f-123">Selecting this option is equivalent to using the KEEP_REPLICATION option in a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement.</span></span>  
  
 <span data-ttu-id="2538f-124">如需詳細資訊，請參閱 [備份及還原複寫的資料庫](../replication/administration/back-up-and-restore-replicated-databases.md)。</span><span class="sxs-lookup"><span data-stu-id="2538f-124">For more information, see [Back Up and Restore Replicated Databases](../replication/administration/back-up-and-restore-replicated-databases.md).</span></span>  
  
 <span data-ttu-id="2538f-125">**限制對還原資料庫的存取 [WITH RESTRICTED_USER]**</span><span class="sxs-lookup"><span data-stu-id="2538f-125">**Restrict access to the restored database [WITH RESTRICTED_USER]**</span></span>  
 <span data-ttu-id="2538f-126">僅有 **db_owner**、 **dbcreator**或 **系統管理員**的成員可以使用還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="2538f-126">Makes the restored database available only to the members of **db_owner**, **dbcreator**, or **sysadmin**.</span></span>  
  
 <span data-ttu-id="2538f-127">選取此選項相當於使用 RESTORE 陳述式的 RESTRICTED_USER 選項。</span><span class="sxs-lookup"><span data-stu-id="2538f-127">Selecting this option is synonymous to using the RESTRICTED_USER option in a RESTORE statement.</span></span>  
  
### <a name="recovery-state"></a><span data-ttu-id="2538f-128">復原狀態</span><span class="sxs-lookup"><span data-stu-id="2538f-128">Recovery state</span></span>  
 <span data-ttu-id="2538f-129">若要在存放區作業之後判斷資料庫的狀態，則必須選取 [復原狀態]  面板的其中一個選項。</span><span class="sxs-lookup"><span data-stu-id="2538f-129">To determine the state of the database after the store operation, you must select one of the options of the **Recovery state** panel.</span></span>  
  
 <span data-ttu-id="2538f-130">**RESTORE WITH RECOVERY**</span><span class="sxs-lookup"><span data-stu-id="2538f-130">**RESTORE WITH RECOVERY**</span></span>  
 <span data-ttu-id="2538f-131">透過還原 [[一般] 頁面](../../integration-services/general-page-of-integration-services-designers-options.md)之 [要還原的備份組]  方格中所核取的最後一個備份來復原資料庫。</span><span class="sxs-lookup"><span data-stu-id="2538f-131">Recovers the database after restoring the final backup checked in the **Backup sets to restore**grid on the [General page](../../integration-services/general-page-of-integration-services-designers-options.md).</span></span> <span data-ttu-id="2538f-132">這是預設的選項，而且相當於在 [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) 陳述式 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 中指定 WITH RECOVERY。</span><span class="sxs-lookup"><span data-stu-id="2538f-132">This is the default option and is equivalent to specifying WITH RECOVERY in a [RESTORE](/sql/t-sql/statements/restore-statements-arguments-transact-sql) statement ([!INCLUDE[tsql](../../includes/tsql-md.md)]).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2538f-133">在完整復原模式或大量記錄復原模式下時，只有在需要立即還原所有記錄檔時才選擇此選項。</span><span class="sxs-lookup"><span data-stu-id="2538f-133">Under the full recovery model or bulk-logged recovery model, choose this option only if you are restoring all the log files now.</span></span>  
  
 <span data-ttu-id="2538f-134">**RESTORE WITH NORECOVERY**</span><span class="sxs-lookup"><span data-stu-id="2538f-134">**RESTORE WITH NORECOVERY**</span></span>  
 <span data-ttu-id="2538f-135">讓資料庫保持在還原狀態。</span><span class="sxs-lookup"><span data-stu-id="2538f-135">Leaves the database in the restoring state.</span></span> <span data-ttu-id="2538f-136">這樣可讓您還原目前復原路徑中的其他備份。</span><span class="sxs-lookup"><span data-stu-id="2538f-136">This allows you to restore additional backups in the current recovery path.</span></span> <span data-ttu-id="2538f-137">若要復原資料庫，必須使用 RESTORE WITH RECOVERY 選項 (請參閱先前選項) 執行還原作業。</span><span class="sxs-lookup"><span data-stu-id="2538f-137">To recover the database, you will have to perform a restore operation by using the RESTORE WITH RECOVERY option (see the preceding option).</span></span>  
  
 <span data-ttu-id="2538f-138">此選項相當於在 RESTORE 陳述式中指定 WITH NORECOVERY。</span><span class="sxs-lookup"><span data-stu-id="2538f-138">This option is equivalent to specifying WITH NORECOVERY in a RESTORE statement.</span></span>  
  
 <span data-ttu-id="2538f-139">如果選取此選項，將無法使用 **[保留複寫設定]** 選項。</span><span class="sxs-lookup"><span data-stu-id="2538f-139">If you select this option, the **Preserve replication settings** option is unavailable.</span></span>  
  
 <span data-ttu-id="2538f-140">**RESTORE WITH STANDBY**</span><span class="sxs-lookup"><span data-stu-id="2538f-140">**RESTORE WITH STANDBY**</span></span>  
 <span data-ttu-id="2538f-141">將資料庫保留為待命狀態，資料庫在此狀態下可提供有限的唯讀存取。</span><span class="sxs-lookup"><span data-stu-id="2538f-141">Leaves the database in a standby state, in which the database is available for limited read-only access.</span></span> <span data-ttu-id="2538f-142">此選項相當於在 RESTORE 陳述式中指定 WITH STANDBY。</span><span class="sxs-lookup"><span data-stu-id="2538f-142">This option is equivalent to specifying WITH STANDBY in a RESTORE statement.</span></span>  
  
 <span data-ttu-id="2538f-143">若要選擇此選項，則必須在 [待命資料庫檔案]  文字方塊中指定待命資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="2538f-143">Choosing this option requires that you specify a standby file in the **Standby file** text box.</span></span> <span data-ttu-id="2538f-144">待命資料庫檔案可以恢復復原效果。</span><span class="sxs-lookup"><span data-stu-id="2538f-144">The standby file allows the recovery effects to be undone.</span></span>  
  
 <span data-ttu-id="2538f-145">**待命資料庫檔案**</span><span class="sxs-lookup"><span data-stu-id="2538f-145">**Standby file**</span></span>  
 <span data-ttu-id="2538f-146">指定待命資料庫檔案。</span><span class="sxs-lookup"><span data-stu-id="2538f-146">Specifies a standby file.</span></span> <span data-ttu-id="2538f-147">您可以瀏覽待命資料庫檔案，或者在文字方塊中直接輸入其路徑名稱。</span><span class="sxs-lookup"><span data-stu-id="2538f-147">You can browse for the standby file or enter its pathname directly in the text box.</span></span>  
  
### <a name="tail-log-backup"></a><span data-ttu-id="2538f-148">結尾記錄備份</span><span class="sxs-lookup"><span data-stu-id="2538f-148">Tail-Log backup</span></span>  
 <span data-ttu-id="2538f-149">可讓您指定在資料庫還原時一併執行結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="2538f-149">Allows you to designate that a tail-log backup be performed along with the database restore.</span></span>  
  
 <span data-ttu-id="2538f-150">**還原前建立結尾記錄備份**</span><span class="sxs-lookup"><span data-stu-id="2538f-150">**Take tail-Log backup before restoring**</span></span>  
 <span data-ttu-id="2538f-151">核取此方塊，即可指定應該執行結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="2538f-151">Check this box to designate that a tail-log backup should be performed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2538f-152">如果您在 [[備份時間表]](backup-timeline.md) 對話方塊中選取的時間點需要結尾記錄備份，系統就會選取這個方塊，而且您無法進行編輯。</span><span class="sxs-lookup"><span data-stu-id="2538f-152">If the point-in-time you have selected in the [Backup Timeline](backup-timeline.md) dialog box requires a tail-log backup, this box will be selected and you will not be able to edit it.</span></span>  
  
 <span data-ttu-id="2538f-153">**[備份檔案]**</span><span class="sxs-lookup"><span data-stu-id="2538f-153">**Backup file**</span></span>  
 <span data-ttu-id="2538f-154">指定記錄結尾的備份檔案。</span><span class="sxs-lookup"><span data-stu-id="2538f-154">Specifies a backup file for the tail of the log.</span></span> <span data-ttu-id="2538f-155">您可以瀏覽備份檔案，也可以直接在文字方塊中輸入其名稱。</span><span class="sxs-lookup"><span data-stu-id="2538f-155">You can browse for the backup file or enter its name directly in the text box.</span></span>  
  
### <a name="server-connections"></a><span data-ttu-id="2538f-156">伺服器連線</span><span class="sxs-lookup"><span data-stu-id="2538f-156">Server connections</span></span>  
 <span data-ttu-id="2538f-157">可讓您關閉現有的資料庫連接。</span><span class="sxs-lookup"><span data-stu-id="2538f-157">Allows you to close existing database connections.</span></span>  
  
 <span data-ttu-id="2538f-158">**關閉現有的連接**</span><span class="sxs-lookup"><span data-stu-id="2538f-158">**Close existing connections**</span></span>  
 <span data-ttu-id="2538f-159">若資料庫有使用中的連接，還原作業可能會失敗。</span><span class="sxs-lookup"><span data-stu-id="2538f-159">Restore operations may fail if there are active connections to the database.</span></span> <span data-ttu-id="2538f-160">核取 **[關閉現有的連接選項]** ，確定已關閉 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 與資料庫之間的所有使用中連接。</span><span class="sxs-lookup"><span data-stu-id="2538f-160">Check the **Close existing connections option** to ensure that all active connections between [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and the database are closed.</span></span> <span data-ttu-id="2538f-161">這個核取方塊會在執行還原作業之前將資料庫設定為單一使用者模式，並在完成後將資料庫設定為多使用者模式。</span><span class="sxs-lookup"><span data-stu-id="2538f-161">This check box sets the database to single user mode before performing the restore operations, and sets the database to multi-user mode when complete.</span></span>  
  
### <a name="prompt"></a><span data-ttu-id="2538f-162">Prompt</span><span class="sxs-lookup"><span data-stu-id="2538f-162">Prompt</span></span>  
 <span data-ttu-id="2538f-163">**還原每個備份之前先提示**</span><span class="sxs-lookup"><span data-stu-id="2538f-163">**Prompt before restoring each backup**</span></span>  
 <span data-ttu-id="2538f-164">指定在還原每個備份之後顯示 [繼續還原]  對話方塊，以便詢問是否還要繼續還原順序。</span><span class="sxs-lookup"><span data-stu-id="2538f-164">Specifies that after each backup is restored, the **Continue with Restore** dialog box will be displayed to inquire whether you want to continue the restore sequence.</span></span> <span data-ttu-id="2538f-165">這個對話方塊會顯示下一個媒體集的名稱 (如果知道)，以及下一個備份組的名稱和描述。</span><span class="sxs-lookup"><span data-stu-id="2538f-165">This dialog box displays the name of the next media set (if known) and the name and description of the next backup set.</span></span>  
  
 <span data-ttu-id="2538f-166">這個選項可讓您在還原任何備份之後暫停還原順序。</span><span class="sxs-lookup"><span data-stu-id="2538f-166">This option allows you to pause a restore sequence after restoring any of the backups.</span></span> <span data-ttu-id="2538f-167">您必須為不同的媒體集交換磁帶時，這個選項特別有用，例如當伺服器只有一個磁帶裝置時。</span><span class="sxs-lookup"><span data-stu-id="2538f-167">This option is particularly useful when you must swap tapes for different media sets; for example, when your server has only one tape device.</span></span> <span data-ttu-id="2538f-168">當您準備繼續時，請按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="2538f-168">When you are ready to proceed, click **OK**.</span></span>  
  
 <span data-ttu-id="2538f-169">您可以按一下 [否]  中斷還原順序。</span><span class="sxs-lookup"><span data-stu-id="2538f-169">You can interrupt a restore sequence by clicking **No**.</span></span> <span data-ttu-id="2538f-170">這會使資料庫處於還原狀態。</span><span class="sxs-lookup"><span data-stu-id="2538f-170">This leaves the database is in the restoring state.</span></span> <span data-ttu-id="2538f-171">您可以依您的方便，稍後再繼續 [繼續還原]  對話方塊中描述的下一項備份，以繼續進行還原順序。</span><span class="sxs-lookup"><span data-stu-id="2538f-171">At your convenience, you can later continue the restore sequence by resuming with the next backup described in the **Continue with Restore** dialog box.</span></span> <span data-ttu-id="2538f-172">還原下一項備份的程序是依照該備份是否包含資料或交易記錄而定，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2538f-172">The procedure restoring the next backup depends on whether it contains data or transaction log, as follows:</span></span>  
  
-   <span data-ttu-id="2538f-173">如果下一個備份是完整備份或差異備份，請再次使用 [還原資料庫]  工作。</span><span class="sxs-lookup"><span data-stu-id="2538f-173">If the next backup is a full or differential backup, use the **Restore Database** task again.</span></span>  
  
-   <span data-ttu-id="2538f-174">如果下一個備份是檔案備份，請使用 [還原檔案和檔案群組]  工作。</span><span class="sxs-lookup"><span data-stu-id="2538f-174">If the next backup is a file backup, use the **Restore Files and Filegroup**s task.</span></span> <span data-ttu-id="2538f-175">如需詳細資訊，請參閱[還原檔案和檔案群組 &#40;SQL Server&#41;](restore-files-and-filegroups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2538f-175">For more information, see [Restore Files and Filegroups &#40;SQL Server&#41;](restore-files-and-filegroups-sql-server.md).</span></span>  
  
-   <span data-ttu-id="2538f-176">如果下一個備份是記錄檔備份，請使用 **[還原交易記錄檔]** 工作。</span><span class="sxs-lookup"><span data-stu-id="2538f-176">If the next backup is a log backup, use the **Restore Transaction Log** task.</span></span> <span data-ttu-id="2538f-177">如需藉由還原交易記錄來繼續還原順序的資訊，請參閱 [還原交易記錄備份 &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2538f-177">For information about resuming a restore sequence by restoring a transaction log, see [Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2538f-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2538f-178">See Also</span></span>  
 <span data-ttu-id="2538f-179">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2538f-179">[RESTORE &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-transact-sql) </span></span>  
 <span data-ttu-id="2538f-180">[從裝置還原備份 &#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2538f-180">[Restore a Backup from a Device &#40;SQL Server&#41;](restore-a-backup-from-a-device-sql-server.md) </span></span>  
 <span data-ttu-id="2538f-181">[還原交易記錄備份 &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2538f-181">[Restore a Transaction Log Backup &#40;SQL Server&#41;](restore-a-transaction-log-backup-sql-server.md) </span></span>  
 <span data-ttu-id="2538f-182">[媒體集、媒體家族與備份組 &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2538f-182">[Media Sets, Media Families, and Backup Sets &#40;SQL Server&#41;](media-sets-media-families-and-backup-sets-sql-server.md) </span></span>  
 <span data-ttu-id="2538f-183">[套用交易記錄備份 &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2538f-183">[Apply Transaction Log Backups &#40;SQL Server&#41;](transaction-log-backups-sql-server.md) </span></span>  
 [<span data-ttu-id="2538f-184">還原資料庫 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="2538f-184">Restore Database &#40;General Page&#41;</span></span>](../../integration-services/general-page-of-integration-services-designers-options.md)  
  
  
