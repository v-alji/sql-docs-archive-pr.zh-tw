---
title: 定義磁帶機的邏輯備份裝置 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], defining
- backup devices [SQL Server], tapes
- backing up databases [SQL Server], tapes
- database backups [SQL Server], tapes
- tape backup devices, creating
ms.assetid: 66f36e1d-0287-4fac-8a51-71f9f0d7ad5b
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 8728df2cc0b5907e51da84ed9e77d897a1718d36
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709694"
---
# <a name="define-a-logical-backup-device-for-a-tape-drive-sql-server"></a><span data-ttu-id="f6663-102">定義磁帶機的邏輯備份裝置 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="f6663-102">Define a Logical Backup Device for a Tape Drive (SQL Server)</span></span>
  <span data-ttu-id="f6663-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中定義磁帶機的邏輯備份裝置。</span><span class="sxs-lookup"><span data-stu-id="f6663-103">This topic describes how to define a logical backup device for a tape drive in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="f6663-104">邏輯裝置是使用者定義名稱，指向特定的實體備份裝置 (磁碟檔案或磁帶機)。</span><span class="sxs-lookup"><span data-stu-id="f6663-104">A logical device is a user-defined name that points to a specific physical backup device (a disk file or tape drive).</span></span>  <span data-ttu-id="f6663-105">當備份寫入備份裝置後，才會進行實體裝置的初始化。</span><span class="sxs-lookup"><span data-stu-id="f6663-105">The initialization of the physical device occurs later, when a backup is written to the backup device.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f6663-106">未來的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]版本中將會移除磁帶備份裝置的支援。</span><span class="sxs-lookup"><span data-stu-id="f6663-106">Support for tape backup devices will be removed in a future version of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f6663-107">請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f6663-107">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="f6663-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="f6663-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="f6663-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="f6663-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="f6663-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="f6663-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="f6663-111">安全性</span><span class="sxs-lookup"><span data-stu-id="f6663-111">Security</span></span>](#Security)  
  
-   <span data-ttu-id="f6663-112">**若要使用下列項目定義磁帶機的邏輯備份裝置：**</span><span class="sxs-lookup"><span data-stu-id="f6663-112">**To define a logical backup device for a tape drive, using:**</span></span>  
  
     [<span data-ttu-id="f6663-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f6663-113">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="f6663-114">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f6663-114">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="f6663-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="f6663-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="f6663-116">限制事項</span><span class="sxs-lookup"><span data-stu-id="f6663-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="f6663-117">磁帶機必須受到 Microsoft Windows 作業系統支援。</span><span class="sxs-lookup"><span data-stu-id="f6663-117">The tape drive or drives must be supported by the Microsoft Windows operating system.</span></span>  
  
-   <span data-ttu-id="f6663-118">磁帶裝置必須在實體上連接至執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體的電腦。</span><span class="sxs-lookup"><span data-stu-id="f6663-118">The tape device must be connected physically to the computer that is running an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="f6663-119">不支援備份至遠端磁帶裝置。</span><span class="sxs-lookup"><span data-stu-id="f6663-119">Backing up to remote tape devices is not supported.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="f6663-120">Security</span><span class="sxs-lookup"><span data-stu-id="f6663-120">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="f6663-121">權限</span><span class="sxs-lookup"><span data-stu-id="f6663-121">Permissions</span></span>  
 <span data-ttu-id="f6663-122">需要 **diskadmin** 固定伺服器角色的成員資格。</span><span class="sxs-lookup"><span data-stu-id="f6663-122">Requires membership in the **diskadmin** fixed server role.</span></span>  
  
 <span data-ttu-id="f6663-123">需要寫入磁碟的權限。</span><span class="sxs-lookup"><span data-stu-id="f6663-123">Requires permission to write to the disk.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="f6663-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="f6663-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-define-a-logical-backup-device-for-a-tape-drive"></a><span data-ttu-id="f6663-125">定義磁帶機的邏輯備份裝置</span><span class="sxs-lookup"><span data-stu-id="f6663-125">To define a logical backup device for a tape drive</span></span>  
  
1.  <span data-ttu-id="f6663-126">連線至適當的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體之後，在 [物件總管] 中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="f6663-126">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="f6663-127">展開 [伺服器物件]  ，然後以滑鼠右鍵按一下 [備份裝置]  。</span><span class="sxs-lookup"><span data-stu-id="f6663-127">Expand **Server Objects**, and then right-click **Backup Devices**.</span></span>  
  
3.  <span data-ttu-id="f6663-128">按一下 **[新增備份裝置]** ，開啟 **[備份裝置]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f6663-128">Click **New Backup Device**, which opens the **Backup Device** dialog box.</span></span>  
  
4.  <span data-ttu-id="f6663-129">輸入裝置名稱。</span><span class="sxs-lookup"><span data-stu-id="f6663-129">Enter a device name.</span></span>  
  
5.  <span data-ttu-id="f6663-130">在目的地中，請按一下 **[磁帶]** ，選取尚未與其他備份裝置連接的磁帶機。</span><span class="sxs-lookup"><span data-stu-id="f6663-130">For the destination, click **Tape** and select a tape drive that is not already associated with another backup device.</span></span> <span data-ttu-id="f6663-131">如果沒有這樣的磁帶機可用， **[磁帶]** 選項會停用。</span><span class="sxs-lookup"><span data-stu-id="f6663-131">If no such tape drives are available, the **Tape** option is inactive.</span></span>  
  
6.  <span data-ttu-id="f6663-132">若要定義新裝置，請按一下 **[確定]** 。</span><span class="sxs-lookup"><span data-stu-id="f6663-132">To define the new device, click **OK**.</span></span>  
  
 <span data-ttu-id="f6663-133">若要備份至這個新裝置，請將它加入 [備份資料庫]  \([一般]  ) 對話方塊中的 [備份至:]  欄位。</span><span class="sxs-lookup"><span data-stu-id="f6663-133">To back up to this new device, add it to the **Back up to:** field in the **Back up Database** (**General**) dialog box.</span></span> <span data-ttu-id="f6663-134">如需詳細資訊，請參閱 [建立完整資料庫備份 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md)中建立差異資料庫備份。</span><span class="sxs-lookup"><span data-stu-id="f6663-134">For more information, see [Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md).</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="f6663-135">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="f6663-135">Using Transact-SQL</span></span>  
  
#### <a name="to-define-a-logical-backup-device-for-a-tape-drive"></a><span data-ttu-id="f6663-136">定義磁帶機的邏輯備份裝置</span><span class="sxs-lookup"><span data-stu-id="f6663-136">To define a logical backup device for a tape drive</span></span>  
  
1.  <span data-ttu-id="f6663-137">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="f6663-137">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="f6663-138">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="f6663-138">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="f6663-139">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="f6663-139">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="f6663-140">這個範例示範如何使用 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) ，定義磁帶的邏輯備份裝置。</span><span class="sxs-lookup"><span data-stu-id="f6663-140">This example shows how to use [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) to define a logical backup device for a tape.</span></span> <span data-ttu-id="f6663-141">範例會加入名稱為 `tapedump1`的磁帶備份裝置，實體名稱是 `\\.\tape0`。</span><span class="sxs-lookup"><span data-stu-id="f6663-141">The example adds the tape backup device named `tapedump1`, with the physical name `\\.\tape0`.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_addumpdevice 'tape', 'tapedump1', '\\.\tape0' ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="f6663-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6663-142">See Also</span></span>  
 <span data-ttu-id="f6663-143">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f6663-143">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="f6663-144">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f6663-144">[sys.backup_devices &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-backup-devices-transact-sql) </span></span>  
 <span data-ttu-id="f6663-145">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f6663-145">[sp_addumpdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql) </span></span>  
 <span data-ttu-id="f6663-146">[sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="f6663-146">[sp_dropdevice &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-dropdevice-transact-sql) </span></span>  
 <span data-ttu-id="f6663-147">[備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f6663-147">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 <span data-ttu-id="f6663-148">[定義磁碟檔案的邏輯備份裝置 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f6663-148">[Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span></span>  
 [<span data-ttu-id="f6663-149">檢視邏輯備份裝置的屬性和內容 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f6663-149">View the Properties and Contents of a Logical Backup Device &#40;SQL Server&#41;</span></span>](view-the-properties-and-contents-of-a-logical-backup-device-sql-server.md)  
  
  
