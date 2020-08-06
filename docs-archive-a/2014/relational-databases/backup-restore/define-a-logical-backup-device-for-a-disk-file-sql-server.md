---
title: 定義磁碟檔案的邏輯備份裝置 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], defining
- backup devices [SQL Server], disks
- disk backup devices [SQL Server]
- database backups [SQL Server], disks
- backing up databases [SQL Server], disks
ms.assetid: 86331d43-c738-4523-ae3d-7d6700348ed1
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8aa92296da81f984f260deace887c15f13443b95
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709701"
---
# <a name="define-a-logical-backup-device-for-a-disk-file-sql-server"></a><span data-ttu-id="20f2e-102">定義磁碟檔案的邏輯備份裝置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="20f2e-102">Define a Logical Backup Device for a Disk File (SQL Server)</span></span>
  <span data-ttu-id="20f2e-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中定義磁碟檔案的邏輯備份裝置。</span><span class="sxs-lookup"><span data-stu-id="20f2e-103">This topic describes how to define a logical backup device for a disk file in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="20f2e-104">邏輯裝置是使用者定義名稱，指向特定的實體備份裝置 (磁碟檔案或磁帶機)。</span><span class="sxs-lookup"><span data-stu-id="20f2e-104">A logical device is a user-defined name that points to a specific physical backup device (a disk file or tape drive).</span></span>  <span data-ttu-id="20f2e-105">當備份寫入備份裝置後，才會進行實體裝置的初始化。</span><span class="sxs-lookup"><span data-stu-id="20f2e-105">The initialization of the physical device occurs later, when a backup is written to the backup device.</span></span>  
  
 <span data-ttu-id="20f2e-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="20f2e-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="20f2e-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="20f2e-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="20f2e-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="20f2e-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="20f2e-109">建議</span><span class="sxs-lookup"><span data-stu-id="20f2e-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="20f2e-110">安全性</span><span class="sxs-lookup"><span data-stu-id="20f2e-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="20f2e-111">**若要使用下列項目定義磁碟檔案的邏輯備份裝置：**</span><span class="sxs-lookup"><span data-stu-id="20f2e-111">**To define a logical backup device for a disk file, using:**</span></span>  
  
     [<span data-ttu-id="20f2e-112">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="20f2e-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="20f2e-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="20f2e-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="20f2e-114">開始之前</span><span class="sxs-lookup"><span data-stu-id="20f2e-114">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="20f2e-115">限制事項</span><span class="sxs-lookup"><span data-stu-id="20f2e-115">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="20f2e-116">邏輯裝置名稱在伺服器執行個體上所有邏輯備份裝置中都必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="20f2e-116">The logical device name must be unique among all the logical backup devices on the server instance.</span></span> <span data-ttu-id="20f2e-117">若要檢視現有的邏輯裝置名稱，請查詢 [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) 目錄檢視。</span><span class="sxs-lookup"><span data-stu-id="20f2e-117">To view the existing logical device names, query the [sys.backup_devices](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) catalog view.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="20f2e-118">建議</span><span class="sxs-lookup"><span data-stu-id="20f2e-118">Recommendations</span></span>  
  
-   <span data-ttu-id="20f2e-119">我們建議備份磁碟應該與資料庫資料和記錄磁碟使用不同的磁碟。</span><span class="sxs-lookup"><span data-stu-id="20f2e-119">We recommend that a backup disk be a different disk than the database data and log disks.</span></span> <span data-ttu-id="20f2e-120">為了確保您可以在資料或記錄磁碟故障時存取備份，這樣做有其必要。</span><span class="sxs-lookup"><span data-stu-id="20f2e-120">This is necessary to make sure that you can access the backups if the data or log disk fails.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="20f2e-121">Security</span><span class="sxs-lookup"><span data-stu-id="20f2e-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="20f2e-122">權限</span><span class="sxs-lookup"><span data-stu-id="20f2e-122">Permissions</span></span>  
 <span data-ttu-id="20f2e-123">需要 **diskadmin** 固定伺服器角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="20f2e-123">Requires membership in the **diskadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="20f2e-124">需要寫入磁碟的權限。</span><span class="sxs-lookup"><span data-stu-id="20f2e-124">Requires permission to write to the disk.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="20f2e-125">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="20f2e-125">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-define-a-logical-backup-device-for-a-disk-file"></a><span data-ttu-id="20f2e-126">定義磁碟檔案的邏輯備份裝置</span><span class="sxs-lookup"><span data-stu-id="20f2e-126">To define a logical backup device for a disk file</span></span>  
  
1.  <span data-ttu-id="20f2e-127">連線到適當的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體之後，在物件總管中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="20f2e-127">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="20f2e-128">展開 [伺服器物件]  ，然後以滑鼠右鍵按一下 [備份裝置]  。</span><span class="sxs-lookup"><span data-stu-id="20f2e-128">Expand **Server Objects**, and right-click **Backup Devices**.</span></span>  
  
3.  <span data-ttu-id="20f2e-129">按一下 **[新增備份裝置]** 。</span><span class="sxs-lookup"><span data-stu-id="20f2e-129">Click **New Backup Device**.</span></span> <span data-ttu-id="20f2e-130">會開啟 **[備份裝置]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="20f2e-130">The **Backup Device** dialog box opens.</span></span>  
  
4.  <span data-ttu-id="20f2e-131">輸入裝置名稱。</span><span class="sxs-lookup"><span data-stu-id="20f2e-131">Enter a device name.</span></span>  
  
5.  <span data-ttu-id="20f2e-132">若要指定目的地，請按一下 **[檔案]** 並指定檔案的完整路徑。</span><span class="sxs-lookup"><span data-stu-id="20f2e-132">For the destination, click **File** and specify the full path of the file.</span></span>  
  
6.  <span data-ttu-id="20f2e-133">若要定義新裝置，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="20f2e-133">To define the new device, click **OK**.</span></span>  
  
 <span data-ttu-id="20f2e-134">若要備份至這個新裝置，請將它加入 [備份資料庫]  \([一般]  ) 對話方塊中的 [備份至:]  欄位。</span><span class="sxs-lookup"><span data-stu-id="20f2e-134">To back up to this new device, add it to the **Back up to:** field in the **Back up Database** (**General**) dialog box.</span></span> <span data-ttu-id="20f2e-135">如需詳細資訊，請參閱 [建立完整資料庫備份 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)中建立差異資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="20f2e-135">For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="20f2e-136">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="20f2e-136">Using Transact-SQL</span></span>  
  
#### <a name="to-define-a-logical-backup-for-a-disk-file"></a><span data-ttu-id="20f2e-137">定義磁碟檔案的邏輯備份裝置</span><span class="sxs-lookup"><span data-stu-id="20f2e-137">To define a logical backup for a disk file</span></span>  
  
1.  <span data-ttu-id="20f2e-138">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="20f2e-138">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="20f2e-139">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="20f2e-139">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="20f2e-140">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="20f2e-140">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="20f2e-141">這個範例示範如何使用 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) ，定義磁碟檔案的邏輯備份裝置。</span><span class="sxs-lookup"><span data-stu-id="20f2e-141">This example shows how to use [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) to define a logical backup device for a disk file.</span></span> <span data-ttu-id="20f2e-142">範例會加入名稱為 `mydiskdump`的磁碟備份裝置，實體名稱是 `c:\dump\dump1.bak`。</span><span class="sxs-lookup"><span data-stu-id="20f2e-142">The example adds the disk backup device named `mydiskdump`, with the physical name `c:\dump\dump1.bak`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'disk', 'mydiskdump', 'c:\dump\dump1.bak' ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="20f2e-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20f2e-143">See Also</span></span>  
 <span data-ttu-id="20f2e-144">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="20f2e-144">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="20f2e-145">[備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="20f2e-145">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 <span data-ttu-id="20f2e-146">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="20f2e-146">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span></span>  
 <span data-ttu-id="20f2e-147">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="20f2e-147">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="20f2e-148">[sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="20f2e-148">[sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) </span></span>  
 <span data-ttu-id="20f2e-149">[定義磁帶機的邏輯備份裝置 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="20f2e-149">[Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-tape-drive-sql-server.md) </span></span>  
 [<span data-ttu-id="20f2e-150">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="20f2e-150">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  
