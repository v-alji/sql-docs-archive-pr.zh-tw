---
title: 從裝置還原備份 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- restoring databases [SQL Server], device restores
- backup devices [SQL Server], restoring from
- database restores [SQL Server], device restores
- devices [SQL Server]
ms.assetid: 6e139de7-7de2-4d18-9df0-beac31ba7ff1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 50d7f7b8e255aea470a1065df669c0cc3169a8dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698326"
---
# <a name="restore-a-backup-from-a-device-sql-server"></a><span data-ttu-id="6daa9-102">從裝置還原備份 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6daa9-102">Restore a Backup from a Device (SQL Server)</span></span>
  <span data-ttu-id="6daa9-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中從裝置還原備份。</span><span class="sxs-lookup"><span data-stu-id="6daa9-103">This topic describes how to restore a backup from a device in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="6daa9-104">如需 SQL Server 備份至 Azure Blob 儲存體服務的相關資訊，請參閱[SQL Server 使用 Azure Blob 儲存體服務的備份與還原](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)。</span><span class="sxs-lookup"><span data-stu-id="6daa9-104">For information on SQL Server backup to the Azure Blob storage service, see, [SQL Server Backup and Restore with Azure Blob Storage Service](sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md).</span></span>  
  
 <span data-ttu-id="6daa9-105">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="6daa9-105">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6daa9-106">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="6daa9-106">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6daa9-107">安全性</span><span class="sxs-lookup"><span data-stu-id="6daa9-107">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6daa9-108">**若要使用下列項目，從裝置還原備份：**</span><span class="sxs-lookup"><span data-stu-id="6daa9-108">**To restore a backup from a device, using:**</span></span>  
  
     [<span data-ttu-id="6daa9-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6daa9-109">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6daa9-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6daa9-110">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6daa9-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="6daa9-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6daa9-112">Security</span><span class="sxs-lookup"><span data-stu-id="6daa9-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6daa9-113">權限</span><span class="sxs-lookup"><span data-stu-id="6daa9-113">Permissions</span></span>  
 <span data-ttu-id="6daa9-114">如果還原的資料庫不存在，使用者必須有 CREATE DATABASE 權限，才能執行 RESTORE。</span><span class="sxs-lookup"><span data-stu-id="6daa9-114">If the database being restored does not exist, the user must have CREATE DATABASE permissions to be able to execute RESTORE.</span></span> <span data-ttu-id="6daa9-115">如果資料庫存在，RESTORE 權限預設為 **系統管理員 (sysadmin)** 和 **資料庫建立者 (dbcreator)** 固定伺服器角色的成員以及資料庫的擁有者 (**dbo**) (對 FROM DATABASE_SNAPSHOT 選項而言，資料庫一律存在)。</span><span class="sxs-lookup"><span data-stu-id="6daa9-115">If the database exists, RESTORE permissions default to members of the **sysadmin** and **dbcreator** fixed server roles and the owner (**dbo**) of the database (for the FROM DATABASE_SNAPSHOT option, the database always exists).</span></span>  
  
 <span data-ttu-id="6daa9-116">RESTORE 權限提供給伺服器隨時可以取得其成員資格資訊的角色。</span><span class="sxs-lookup"><span data-stu-id="6daa9-116">RESTORE permissions are given to roles in which membership information is always readily available to the server.</span></span> <span data-ttu-id="6daa9-117">由於資料庫必須是可存取且未損毀，才能夠檢查固定資料庫角色成員資格，但執行 RESTORE 時未必如此；因此， **db_owner** 固定資料庫角色的成員並沒有 RESTORE 權限。</span><span class="sxs-lookup"><span data-stu-id="6daa9-117">Because fixed database role membership can be checked only when the database is accessible and undamaged, which is not always the case when RESTORE is executed, members of the **db_owner** fixed database role do not have RESTORE permissions.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6daa9-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6daa9-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-restore-a-backup-from-a-device"></a><span data-ttu-id="6daa9-119">若要從裝置還原備份</span><span class="sxs-lookup"><span data-stu-id="6daa9-119">To restore a backup from a device</span></span>  
  
1.  <span data-ttu-id="6daa9-120">連線至適當的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體之後，在 [物件總管] 中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="6daa9-120">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="6daa9-121">展開 **[資料庫]** ，然後視資料庫而定，選取使用者資料庫，或者展開 **[系統資料庫]** 並選取一個系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="6daa9-121">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="6daa9-122">以滑鼠右鍵按一下資料庫，指向 [工作]  ，然後按一下 [還原]  。</span><span class="sxs-lookup"><span data-stu-id="6daa9-122">Right-click the database, point to **Tasks**, and then click **Restore**.</span></span>  
  
4.  <span data-ttu-id="6daa9-123">按一下您想要的還原作業類型 ([資料庫]  、[檔案和檔案群組]  或 [交易記錄檔]  )。</span><span class="sxs-lookup"><span data-stu-id="6daa9-123">Click the type of restore operation you want (**Database**, **Files and Filegroups**, or **Transaction Log**).</span></span> <span data-ttu-id="6daa9-124">這會開啟對應的還原對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6daa9-124">This opens the corresponding restore dialog box.</span></span>  
  
5.  <span data-ttu-id="6daa9-125">在 **[一般]** 頁面的 **[還原來源]** 區段中，按一下 **[來源裝置]** 。</span><span class="sxs-lookup"><span data-stu-id="6daa9-125">On the **General** page, in the **Restore source** section, click **From device**.</span></span>  
  
6.  <span data-ttu-id="6daa9-126">按一下 **[來源裝置]** 文字方塊的瀏覽按鈕，這會開啟 **[指定備份]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6daa9-126">Click the browse button for the **From device** text box, which opens the **Specify Backup** dialog box.</span></span>  
  
7.  <span data-ttu-id="6daa9-127">在 **[備份媒體]** 文字方塊中，選取 **[備份裝置]** ，然後按一下 **[加入]** 按鈕，以開啟 **[選取備份裝置]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6daa9-127">In the **Backup media** text box, select **Backup Device**, and click the **Add** button to open the **Select Backup Device** dialog box.</span></span>  
  
8.  <span data-ttu-id="6daa9-128">在 **[備份裝置]** 文字方塊中，選取您要用於還原作業的裝置。</span><span class="sxs-lookup"><span data-stu-id="6daa9-128">In the **Backup device** text box, select the device you want to use for the restore operation.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6daa9-129">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6daa9-129">Using Transact-SQL</span></span>  
  
#### <a name="to-restore-a-backup-from-a-device"></a><span data-ttu-id="6daa9-130">若要從裝置還原備份</span><span class="sxs-lookup"><span data-stu-id="6daa9-130">To restore a backup from a device</span></span>  
  
1.  <span data-ttu-id="6daa9-131">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6daa9-131">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6daa9-132">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="6daa9-132">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6daa9-133">在 [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) 陳述式中，指定備份作業要用的邏輯或實體備份裝置。</span><span class="sxs-lookup"><span data-stu-id="6daa9-133">In the [RESTORE](/sql/t-sql/statements/restore-statements-transact-sql) statement, specify a logical or physical backup device to use for the backup operation.</span></span> <span data-ttu-id="6daa9-134">這個範例會從實體名稱為 `Z:\SQLServerBackups\AdventureWorks2012.bak`的磁碟檔案還原。</span><span class="sxs-lookup"><span data-stu-id="6daa9-134">This example restores from a disk file that has the physical name `Z:\SQLServerBackups\AdventureWorks2012.bak`.</span></span>  
  
```sql  
RESTORE DATABASE AdventureWorks2012  
   FROM DISK = 'Z:\SQLServerBackups\AdventureWorks2012.bak' ;  
  
```  
  
## <a name="see-also"></a><span data-ttu-id="6daa9-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6daa9-135">See Also</span></span>  
 <span data-ttu-id="6daa9-136">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6daa9-136">[RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) </span></span>  
 <span data-ttu-id="6daa9-137">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6daa9-137">[RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) </span></span>  
 <span data-ttu-id="6daa9-138">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6daa9-138">[RESTORE LABELONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-labelonly-transact-sql) </span></span>  
 <span data-ttu-id="6daa9-139">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="6daa9-139">[RESTORE VERIFYONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-verifyonly-transact-sql) </span></span>  
 <span data-ttu-id="6daa9-140">[在簡單復原模式下還原資料庫備份 &#40;Transact-SQL&#41;](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md) </span><span class="sxs-lookup"><span data-stu-id="6daa9-140">[Restore a Database Backup Under the Simple Recovery Model &#40;Transact-SQL&#41;](restore-a-database-backup-under-the-simple-recovery-model-transact-sql.md) </span></span>  
 <span data-ttu-id="6daa9-141">[還原資料庫備份 &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span><span class="sxs-lookup"><span data-stu-id="6daa9-141">[Restore a Database Backup &#40;SQL Server Management Studio&#41;](restore-a-database-backup-using-ssms.md) </span></span>  
 <span data-ttu-id="6daa9-142">[還原差異資料庫備份 &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6daa9-142">[Restore a Differential Database Backup &#40;SQL Server&#41;](restore-a-differential-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="6daa9-143">[將資料庫還原到新位置 &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6daa9-143">[Restore a Database to a New Location &#40;SQL Server&#41;](restore-a-database-to-a-new-location-sql-server.md) </span></span>  
 <span data-ttu-id="6daa9-144">[備份檔案和檔案群組 &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6daa9-144">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="6daa9-145">[備份交易記錄 &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6daa9-145">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="6daa9-146">建立差異資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6daa9-146">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
  
