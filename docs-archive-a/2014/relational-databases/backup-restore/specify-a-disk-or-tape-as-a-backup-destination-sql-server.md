---
title: 指定磁碟或磁帶作為備份目的地 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], tapes
- backing up databases [SQL Server], tapes
- database backups [SQL Server], tapes
- backup devices [SQL Server], disks
- disk backup devices [SQL Server]
- database backups [SQL Server], disks
- backing up databases [SQL Server], disks
- backups [SQL Server], creating
- tape backup devices, backing up
ms.assetid: e391f452-ed8c-4b40-b846-ac3881271b94
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8a0f8ec5d9741e42f3b7d8eda8ebdba23622982d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699787"
---
# <a name="specify-a-disk-or-tape-as-a-backup-destination-sql-server"></a><span data-ttu-id="15270-102">指定磁碟或磁帶做為備份目的地 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="15270-102">Specify a Disk or Tape As a Backup Destination (SQL Server)</span></span>
  <span data-ttu-id="15270-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中指定磁碟或磁帶做為備份目的地。</span><span class="sxs-lookup"><span data-stu-id="15270-103">This topic describes how to specify a disk or tape as a backup destination in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="15270-104">未來的 SQL Server 版本中將會移除磁帶備份裝置的支援。</span><span class="sxs-lookup"><span data-stu-id="15270-104">Support for tape backup devices will be removed in a future version of SQL Server.</span></span> <span data-ttu-id="15270-105">請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="15270-105">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="15270-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="15270-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="15270-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="15270-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="15270-108">安全性</span><span class="sxs-lookup"><span data-stu-id="15270-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="15270-109">**若要使用下列項目指定磁碟或磁帶做為備份目的地：**</span><span class="sxs-lookup"><span data-stu-id="15270-109">**To specify a disk or tape as a backup destination, using:**</span></span>  
  
     [<span data-ttu-id="15270-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="15270-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="15270-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="15270-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="15270-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="15270-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="15270-113">Security</span><span class="sxs-lookup"><span data-stu-id="15270-113">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="15270-114">權限</span><span class="sxs-lookup"><span data-stu-id="15270-114">Permissions</span></span>  
 <span data-ttu-id="15270-115">BACKUP DATABASE 和 BACKUP LOG 權限預設為 **sysadmin** 固定伺服器角色以及 **db_owner** 和 **db_backupoperator** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="15270-115">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="15270-116">備份裝置實體檔案的擁有權和權限問題可能會干擾備份作業。</span><span class="sxs-lookup"><span data-stu-id="15270-116">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="15270-117">必須能夠讀取和寫入裝置；執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的帳戶必須具備寫入權限。</span><span class="sxs-lookup"><span data-stu-id="15270-117">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="15270-118">不過，在系統資料表中加入備份裝置項目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)並不會檢查檔案存取權限。</span><span class="sxs-lookup"><span data-stu-id="15270-118">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="15270-119">當您嘗試備份或還原時，存取實體資源之前不一定會出現備份裝置實體檔案的這些問題。</span><span class="sxs-lookup"><span data-stu-id="15270-119">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="15270-120">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="15270-120">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-specify-a-disk-or-tape-as-a-backup-destination"></a><span data-ttu-id="15270-121">若要指定磁碟或磁帶做為備份目的地</span><span class="sxs-lookup"><span data-stu-id="15270-121">To specify a disk or tape as a backup destination</span></span>  
  
1.  <span data-ttu-id="15270-122">連線到適當的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體之後，在物件總管中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="15270-122">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="15270-123">展開 **[資料庫]** ，然後視資料庫而定，選取使用者資料庫，或者展開 **[系統資料庫]** 並選取一個系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="15270-123">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="15270-124">以滑鼠右鍵按一下資料庫，指向 **[工作]** ，然後按一下 **[備份]** 。</span><span class="sxs-lookup"><span data-stu-id="15270-124">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="15270-125">會出現 **[備份資料庫]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="15270-125">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="15270-126">在 **[一般]** 頁面的 **[目的地]** 區段中，按一下 **[磁碟]** 或 **[磁帶]** 。</span><span class="sxs-lookup"><span data-stu-id="15270-126">In the **Destination** section of the **General** page, click **Disk** or **Tape**.</span></span> <span data-ttu-id="15270-127">若要選取包含單一媒體集的磁碟或磁帶機 (最多 64 個) 的路徑，請按一下 **[加入]** 。</span><span class="sxs-lookup"><span data-stu-id="15270-127">To select the paths of up to 64 disk or tape drives containing a single media set, click **Add**.</span></span>  
  
     <span data-ttu-id="15270-128">若要移除備份目的地，請選取目的地，然後按一下 **[移除]** 。</span><span class="sxs-lookup"><span data-stu-id="15270-128">To remove a backup destination, select it and click **Remove**.</span></span> <span data-ttu-id="15270-129">若要檢視備份目的地的內容，請選取目的地，然後按一下 **[內容]** 。</span><span class="sxs-lookup"><span data-stu-id="15270-129">To view the contents of a backup destination, select it and click **Contents**.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="15270-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="15270-130">Using Transact-SQL</span></span>  
  
#### <a name="to-specify-a-disk-or-tape-as-a-backup-destination"></a><span data-ttu-id="15270-131">若要指定磁碟或磁帶做為備份目的地</span><span class="sxs-lookup"><span data-stu-id="15270-131">To specify a disk or tape as a backup destination</span></span>  
  
1.  <span data-ttu-id="15270-132">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="15270-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="15270-133">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="15270-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="15270-134">在 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 陳述式中，指定檔案或裝置及其實體名稱。</span><span class="sxs-lookup"><span data-stu-id="15270-134">In the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement, specify the file or device and its physical name.</span></span> <span data-ttu-id="15270-135">這個範例會將 `AdventureWorks2012` 資料庫備份到磁碟檔案 `Z:\SQLServerBackups\AdventureWorks2012.Bak`。</span><span class="sxs-lookup"><span data-stu-id="15270-135">This example backs up the `AdventureWorks2012` database to the disk file `Z:\SQLServerBackups\AdventureWorks2012.Bak`.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="15270-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15270-136">See Also</span></span>  
 <span data-ttu-id="15270-137">[備份交易記錄 &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="15270-137">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 <span data-ttu-id="15270-138">[備份檔案和檔案群組 &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="15270-138">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="15270-139">[定義磁碟檔案的邏輯備份裝置 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="15270-139">[Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span></span>  
 <span data-ttu-id="15270-140">[建立差異資料庫備份 &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="15270-140">[Create a Differential Database Backup &#40;SQL Server&#41;](create-a-differential-database-backup-sql-server.md) </span></span>  
 [<span data-ttu-id="15270-141">定義磁帶機的邏輯備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="15270-141">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
  
