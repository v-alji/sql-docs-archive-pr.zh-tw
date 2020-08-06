---
title: 在備份或還原期間啟用或停用備份總和檢查碼 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup checksums [SQL Server]
- disabling checksums
- checksums [SQL Server]
ms.assetid: 6786bd1e-ad97-430a-8dfb-d4ba952d6c4d
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: a239dcdfca689be8555117104264d66a2ac037f1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709693"
---
# <a name="enable-or-disable-backup-checksums-during-backup-or-restore-sql-server"></a><span data-ttu-id="c2c50-102">在備份或還原期間啟用或停用備份總和檢查碼 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="c2c50-102">Enable or Disable Backup Checksums During Backup or Restore (SQL Server)</span></span>
  <span data-ttu-id="c2c50-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中備份或還原資料庫時啟用或停用備份總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="c2c50-103">This topic describes how to enable or disable backup checksums when you are backing up or restoring a database in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="c2c50-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="c2c50-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="c2c50-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="c2c50-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="c2c50-106">安全性</span><span class="sxs-lookup"><span data-stu-id="c2c50-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="c2c50-107">**若要使用下列項目啟用或停用備份總和檢查碼：**</span><span class="sxs-lookup"><span data-stu-id="c2c50-107">**To enable or disable backup checksums, using:**</span></span>  
  
     [<span data-ttu-id="c2c50-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c2c50-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="c2c50-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c2c50-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="c2c50-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="c2c50-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="c2c50-111">Security</span><span class="sxs-lookup"><span data-stu-id="c2c50-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="c2c50-112">權限</span><span class="sxs-lookup"><span data-stu-id="c2c50-112">Permissions</span></span>  
 <span data-ttu-id="c2c50-113">備份</span><span class="sxs-lookup"><span data-stu-id="c2c50-113">BACKUP</span></span>  
 <span data-ttu-id="c2c50-114">BACKUP DATABASE 和 BACKUP LOG 權限預設為 **sysadmin** 固定伺服器角色以及 **db_owner** 和 **db_backupoperator** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="c2c50-114">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="c2c50-115">備份裝置實體檔案的擁有權和權限問題可能會干擾備份作業。</span><span class="sxs-lookup"><span data-stu-id="c2c50-115">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="c2c50-116">必須能夠讀取和寫入裝置；執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的帳戶必須具備寫入權限。</span><span class="sxs-lookup"><span data-stu-id="c2c50-116">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="c2c50-117">不過，在系統資料表中加入備份裝置項目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)並不會檢查檔案存取權限。</span><span class="sxs-lookup"><span data-stu-id="c2c50-117">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="c2c50-118">當您嘗試備份或還原時，存取實體資源之前不一定會出現備份裝置實體檔案的這些問題。</span><span class="sxs-lookup"><span data-stu-id="c2c50-118">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
 <span data-ttu-id="c2c50-119">RESTORE</span><span class="sxs-lookup"><span data-stu-id="c2c50-119">RESTORE</span></span>  
 <span data-ttu-id="c2c50-120">如果還原的資料庫不存在，使用者必須有 CREATE DATABASE 權限，才能執行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="c2c50-120">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="c2c50-121">如果資料庫存在，RESTORE 權限預設為 **系統管理員 (sysadmin)** 和 **資料庫建立者 (dbcreator)** 固定伺服器角色的成員以及資料庫的擁有者 (**dbo**) (對 FROM DATABASE_SNAPSHOT 選項而言，資料庫一律存在)。</span><span class="sxs-lookup"><span data-stu-id="c2c50-121">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="c2c50-122">RESTORE 權限提供給伺服器隨時可以取得其成員資格資訊的角色。</span><span class="sxs-lookup"><span data-stu-id="c2c50-122">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="c2c50-123">由於資料庫必須是可存取且未損毀，才能夠檢查固定資料庫角色成員資格，但執行 RESTORE 時未必如此；因此， **db_owner** 固定資料庫角色的成員並沒有 RESTORE 權限。</span><span class="sxs-lookup"><span data-stu-id="c2c50-123">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="c2c50-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="c2c50-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-enable-or-disable-checksums-during-a-backup-operation"></a><span data-ttu-id="c2c50-125">若要在備份作業期間啟用或停用總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="c2c50-125">To enable or disable checksums during a backup operation</span></span>  
  
1.  <span data-ttu-id="c2c50-126">請依照＜ [建立資料庫備份](create-a-full-database-backup-sql-server.md)＞的步驟執行。</span><span class="sxs-lookup"><span data-stu-id="c2c50-126">Follow the steps to [create a database backup](create-a-full-database-backup-sql-server.md).</span></span>  
  
2.  <span data-ttu-id="c2c50-127">在 **[選項]** 頁面的 **[可靠性]** 區段中，按一下 **[寫入媒體之前執行總和檢查碼]** 。</span><span class="sxs-lookup"><span data-stu-id="c2c50-127">On the **Options** page, in the **Reliability** section, click **Perform checksum before writing to media**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="c2c50-128">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="c2c50-128">Using Transact-SQL</span></span>  
  
#### <a name="to-enable-or-disable-backup-checksum-for-a-backup-operation"></a><span data-ttu-id="c2c50-129">若要為備份作業啟用或停用備份總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="c2c50-129">To enable or disable backup checksum for a backup operation</span></span>  
  
1.  <span data-ttu-id="c2c50-130">連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c2c50-130">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c2c50-131">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="c2c50-131">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c2c50-132">若要在 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 陳述式中啟用備份總和檢查碼，請指定 WITH CHECKSUM 選項。</span><span class="sxs-lookup"><span data-stu-id="c2c50-132">To enable backup checksums in a [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement, specify the WITH CHECKSUM option.</span></span> <span data-ttu-id="c2c50-133">若要停用備份總和檢查碼，請指定 WITH NO_CHECKSUM 選項。</span><span class="sxs-lookup"><span data-stu-id="c2c50-133">To disable backup checksums, specify the WITH NO_CHECKSUM option.</span></span> <span data-ttu-id="c2c50-134">這是預設行為，但是壓縮備份除外。</span><span class="sxs-lookup"><span data-stu-id="c2c50-134">This is the default behavior, except for a compressed backup.</span></span> <span data-ttu-id="c2c50-135">下列範例指定應執行總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="c2c50-135">The following example specifies that checksums be performed.</span></span>  
  
```sql  
BACKUP DATABASE AdventureWorks2012   
 TO DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM;  
GO  
```  
  
#### <a name="to-enable-or-disable-backup-checksum-for-a-restore-operation"></a><span data-ttu-id="c2c50-136">若要為還原作業啟用或停用備份總和檢查碼</span><span class="sxs-lookup"><span data-stu-id="c2c50-136">To enable or disable backup checksum for a restore operation</span></span>  
  
1.  <span data-ttu-id="c2c50-137">連接到 [!INCLUDE[ssDE](../../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="c2c50-137">Connect to the [!INCLUDE[ssDE](../../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="c2c50-138">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="c2c50-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="c2c50-139">若要在 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 陳述式中啟用備份總和檢查碼，請指定 WITH CHECKSUM 選項。</span><span class="sxs-lookup"><span data-stu-id="c2c50-139">To enable backup checksums in a [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, specify the WITH CHECKSUM option.</span></span> <span data-ttu-id="c2c50-140">這是壓縮備份的預設行為。</span><span class="sxs-lookup"><span data-stu-id="c2c50-140">This is the default behavior for a compressed backup.</span></span> <span data-ttu-id="c2c50-141">若要停用備份總和檢查碼，請指定 WITH NO_CHECKSUM 選項。</span><span class="sxs-lookup"><span data-stu-id="c2c50-141">To disable backup checksums, specify the WITH NO_CHECKSUM option.</span></span> <span data-ttu-id="c2c50-142">這是預設行為，但是壓縮備份除外。</span><span class="sxs-lookup"><span data-stu-id="c2c50-142">This is the default behavior, except for a compressed backup.</span></span> <span data-ttu-id="c2c50-143">下列範例指定應執行備份總和檢查碼。</span><span class="sxs-lookup"><span data-stu-id="c2c50-143">The following example specifies that backup checksums be performed.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012   
 FROM DISK = 'Z:\SQLServerBackups\AdvWorksData.bak'  
   WITH CHECKSUM;  
GO  
```  
  
> [!WARNING]  
>  <span data-ttu-id="c2c50-144">如果您明確地在還原作業中要求 CHECKSUM，而且備份包含備份總和檢查碼，就會和預設情況一樣，備份總和檢查碼及分頁總和檢查碼都會加以驗證。</span><span class="sxs-lookup"><span data-stu-id="c2c50-144">If you explicitly request CHECKSUM for a restore operation and if the backup contains backup checksums, backup checksums and page checksums are both verified, as in the default case.</span></span> <span data-ttu-id="c2c50-145">然而，如果備份組沒有備份總和檢查碼，則還原作業就會失敗，並且會產生訊息指出總和檢查碼不存在。</span><span class="sxs-lookup"><span data-stu-id="c2c50-145">However, if the backup set lacks backup checksums, the restore operation fails with a message indicating that checksums are not present.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c50-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2c50-146">See Also</span></span>  
 <span data-ttu-id="c2c50-147">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c2c50-147">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span></span>  
 <span data-ttu-id="c2c50-148">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c2c50-148">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span></span>  
 <span data-ttu-id="c2c50-149">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c2c50-149">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span></span>  
 <span data-ttu-id="c2c50-150">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c2c50-150">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span></span>  
 <span data-ttu-id="c2c50-151">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c2c50-151">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="c2c50-152">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c2c50-152">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="c2c50-153">[RESTORE 引數 &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c2c50-153">[RESTORE Arguments &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-arguments-transact-sql) </span></span>  
 <span data-ttu-id="c2c50-154">[備份和還原期間可能發生的媒體錯誤 &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="c2c50-154">[Possible Media Errors During Backup and Restore &#40;SQL Server&#41;](possible-media-errors-during-backup-and-restore-sql-server.md) </span></span>  
 [<span data-ttu-id="c2c50-155">指定在發生錯誤後備份或還原作業應該繼續還是停止 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="c2c50-155">Specify Whether a Backup or Restore Operation Continues or Stops After Encountering an Error &#40;SQL Server&#41;</span></span>](specify-if-backup-or-restore-continues-or-stops-after-error.md)  
  
  
