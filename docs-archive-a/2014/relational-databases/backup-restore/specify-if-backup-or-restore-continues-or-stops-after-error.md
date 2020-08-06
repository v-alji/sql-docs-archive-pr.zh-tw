---
title: 指定在發生錯誤 (SQL Server) 時，備份或還原作業是否繼續或停止 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- errors [SQL Server], backups
- backing up databases [SQL Server], errors
- backups [SQL Server], errors
- database backups [SQL Server], errors
ms.assetid: 042be17a-b9b0-4629-b6bb-b87a8bc6c316
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 87cccec6f7eea18f2750d3b0be81b577b0eb170a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599521"
---
# <a name="specify-whether-a-backup-or-restore-operation-continues-or-stops-after-encountering-an-error-sql-server"></a><span data-ttu-id="558cb-102">指定在發生錯誤後備份或還原作業應該繼續還是停止 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="558cb-102">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error (SQL Server)</span></span>
  <span data-ttu-id="558cb-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，指定在 [!INCLUDE[tsql](../../includes/tsql-md.md)]發生錯誤後，備份或還原作業應該繼續還是停止。</span><span class="sxs-lookup"><span data-stu-id="558cb-103">This topic describes how to specify whether a backup or restore operation continues or stops after encountering an error in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="558cb-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="558cb-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="558cb-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="558cb-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="558cb-106">安全性</span><span class="sxs-lookup"><span data-stu-id="558cb-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="558cb-107">**若要使用下列項目，指定在發生錯誤後備份或還原作業應該繼續還是停止：**</span><span class="sxs-lookup"><span data-stu-id="558cb-107">**To specify whether a backup or restore operation continues after encountering an error, using:**</span></span>  
  
     [<span data-ttu-id="558cb-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="558cb-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="558cb-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="558cb-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="558cb-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="558cb-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="558cb-111">Security</span><span class="sxs-lookup"><span data-stu-id="558cb-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="558cb-112">權限</span><span class="sxs-lookup"><span data-stu-id="558cb-112">Permissions</span></span>  
 <span data-ttu-id="558cb-113">備份</span><span class="sxs-lookup"><span data-stu-id="558cb-113">BACKUP</span></span>  
 <span data-ttu-id="558cb-114">BACKUP DATABASE 和 BACKUP LOG 權限預設為 **sysadmin** 固定伺服器角色以及 **db_owner** 和 **db_backupoperator** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="558cb-114">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="558cb-115">備份裝置實體檔案的擁有權和權限問題可能會干擾備份作業。</span><span class="sxs-lookup"><span data-stu-id="558cb-115">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="558cb-116">必須能夠讀取和寫入裝置；執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的帳戶必須具備寫入權限。</span><span class="sxs-lookup"><span data-stu-id="558cb-116">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="558cb-117">不過，在系統資料表中加入備份裝置項目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)並不會檢查檔案存取權限。</span><span class="sxs-lookup"><span data-stu-id="558cb-117">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="558cb-118">當您嘗試備份或還原時，存取實體資源之前不一定會出現備份裝置實體檔案的這些問題。</span><span class="sxs-lookup"><span data-stu-id="558cb-118">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
 <span data-ttu-id="558cb-119">RESTORE</span><span class="sxs-lookup"><span data-stu-id="558cb-119">RESTORE</span></span>  
 <span data-ttu-id="558cb-120">如果還原的資料庫不存在，使用者必須有 CREATE DATABASE 權限，才能執行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="558cb-120">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="558cb-121">如果資料庫存在，RESTORE 權限預設為 **系統管理員 (sysadmin)** 和 **資料庫建立者 (dbcreator)** 固定伺服器角色的成員以及資料庫的擁有者 (**dbo**) (對 FROM DATABASE_SNAPSHOT 選項而言，資料庫一律存在)。</span><span class="sxs-lookup"><span data-stu-id="558cb-121">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="558cb-122">RESTORE 權限提供給伺服器隨時可以取得其成員資格資訊的角色。</span><span class="sxs-lookup"><span data-stu-id="558cb-122">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="558cb-123">由於資料庫必須是可存取且未損毀，才能夠檢查固定資料庫角色成員資格，但執行 RESTORE 時未必如此；因此， **db_owner** 固定資料庫角色的成員並沒有 RESTORE 權限。</span><span class="sxs-lookup"><span data-stu-id="558cb-123">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="558cb-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="558cb-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-whether-backup-continues-or-stops-after-an-error-is-encountered"></a><span data-ttu-id="558cb-125">若要指定在發生錯誤後備份應該繼續還是停止</span><span class="sxs-lookup"><span data-stu-id="558cb-125">To specify whether backup continues or stops after an error is encountered</span></span>  
  
1.  <span data-ttu-id="558cb-126">請依照＜ [建立資料庫備份](create-a-full-database-backup-sql-server.md)＞的步驟執行。</span><span class="sxs-lookup"><span data-stu-id="558cb-126">Follow the steps to [create a database backup](create-a-full-database-backup-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="558cb-127">在 **[選項]** 頁面的 **[可靠性]** 區段中，按一下 **[寫入媒體之前執行總和檢查碼]** 和 **[發生錯誤時繼續]** 。</span><span class="sxs-lookup"><span data-stu-id="558cb-127">On the **Options** page, in the **Reliability** section, click **Perform checksum before writing to media** and **Continue on error**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="558cb-128">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="558cb-128">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-whether-a-backup-operation-continues-or-stops-after-encountering-an-error"></a><span data-ttu-id="558cb-129">若要指定在發生錯誤後備份作業應該繼續還是停止</span><span class="sxs-lookup"><span data-stu-id="558cb-129">To specify whether a backup operation continues or stops after encountering an error</span></span>  
  
1.  <span data-ttu-id="558cb-130">連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="558cb-130">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="558cb-131">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="558cb-131">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="558cb-132">在 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 陳述式中，指定 CONTINUE_AFTER_ERROR 選項以繼續，或指定 STOP_ON_ERROR 選項以停止。</span><span class="sxs-lookup"><span data-stu-id="558cb-132">In the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement, specify the CONTINUE_AFTER ERROR option to continue or the STOP_ON_ERROR option to stop.</span></span> <span data-ttu-id="558cb-133">預設行為是在發生錯誤後停止。</span><span class="sxs-lookup"><span data-stu-id="558cb-133">The default behavior is to stop after encountering an error.</span></span> <span data-ttu-id="558cb-134">此範例指示備份作業儘管發生錯誤時仍繼續進行。</span><span class="sxs-lookup"><span data-stu-id="558cb-134">This example instructs the backup operation to continue despite encountering an error.</span></span>  
  
```sql  
BACKUP DATABASE AdventureWorks2012   
 TO DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM, CONTINUE_AFTER_ERROR;  
GO  
```  
  
#### <a name="to-specify-whether-a-restore-operation-continues-or-stops-after-encountering-an-error"></a><span data-ttu-id="558cb-135">若要指定在發生錯誤後還原作業應該繼續還是停止</span><span class="sxs-lookup"><span data-stu-id="558cb-135">To specify whether a restore operation continues or stops after encountering an error</span></span>  
  
1.  <span data-ttu-id="558cb-136">連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="558cb-136">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="558cb-137">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="558cb-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="558cb-138">在 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 陳述式中，指定 CONTINUE_AFTER_ERROR 選項以繼續，或指定 STOP_ON_ERROR 選項以停止。</span><span class="sxs-lookup"><span data-stu-id="558cb-138">In the [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, specify the CONTINUE_AFTER ERROR option to continue or the STOP_ON_ERROR option to stop.</span></span> <span data-ttu-id="558cb-139">預設行為是在發生錯誤後停止。</span><span class="sxs-lookup"><span data-stu-id="558cb-139">The default behavior is to stop after encountering an error.</span></span> <span data-ttu-id="558cb-140">此範例指示還原作業儘管發生錯誤時仍繼續進行。</span><span class="sxs-lookup"><span data-stu-id="558cb-140">This example instructs the restore operation to continue despite encountering an error.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012   
 FROM DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'   
   WITH CHECKSUM, CONTINUE_AFTER_ERROR;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="558cb-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="558cb-141">See Also</span></span>  
 <span data-ttu-id="558cb-142">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="558cb-142">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span></span>  
 <span data-ttu-id="558cb-143">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="558cb-143">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span></span>  
 <span data-ttu-id="558cb-144">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="558cb-144">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span></span>  
 <span data-ttu-id="558cb-145">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="558cb-145">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span></span>  
 <span data-ttu-id="558cb-146">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="558cb-146">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="558cb-147">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="558cb-147">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="558cb-148">[RESTORE 引數 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="558cb-148">[RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span></span>  
 <span data-ttu-id="558cb-149">[備份和還原期間可能發生的媒體錯誤 &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="558cb-149">[Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span></span>  
 [<span data-ttu-id="558cb-150">在備份或還原期間啟用或停用備份總和檢查碼 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="558cb-150">Enable or Disable Backup Checksums During Backup or Restore &#40;SQL Server&#41;</span></span>](enable-or-disable-backup-checksums-during-backup-or-restore-sql-server.md)  
  
  
