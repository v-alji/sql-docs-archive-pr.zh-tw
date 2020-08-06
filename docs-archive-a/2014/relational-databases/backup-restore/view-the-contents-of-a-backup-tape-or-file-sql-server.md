---
title: 檢視備份磁帶或檔案的內容 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backup devices [SQL Server], tapes
- displaying backup content
- viewing backup content
- tape backup devices, viewing contents
- database backups [SQL Server], viewing content
- backing up databases [SQL Server], viewing content
ms.assetid: cd6674a2-ca55-4b5a-a971-878ba001821e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 044519b64d41fbbdfc9302ce24369ab282727f67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703010"
---
# <a name="view-the-contents-of-a-backup-tape-or-file-sql-server"></a><span data-ttu-id="eed02-102">檢視備份磁帶或檔案的內容 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="eed02-102">View the Contents of a Backup Tape or File (SQL Server)</span></span>
  <span data-ttu-id="eed02-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視備份磁帶或檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="eed02-103">This topic describes how to view the content of a backup tape or file in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="eed02-104">未來的 SQL Server 版本中將會移除磁帶備份裝置的支援。</span><span class="sxs-lookup"><span data-stu-id="eed02-104">Support for tape backup devices will be removed in a future version of SQL Server.</span></span> <span data-ttu-id="eed02-105">請避免在新的開發工作中使用這項功能，並規劃修改目前使用這項功能的應用程式。</span><span class="sxs-lookup"><span data-stu-id="eed02-105">Avoid using this feature in new development work, and plan to modify applications that currently use this feature.</span></span>  
  
 <span data-ttu-id="eed02-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="eed02-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="eed02-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="eed02-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="eed02-108">安全性</span><span class="sxs-lookup"><span data-stu-id="eed02-108">Security</span></span>](#Security)  
  
-   <span data-ttu-id="eed02-109">**若要使用下列項目檢視備份磁帶或檔案的內容：**</span><span class="sxs-lookup"><span data-stu-id="eed02-109">**To view the content of a backup tape or file, using:**</span></span>  
  
     [<span data-ttu-id="eed02-110">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eed02-110">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="eed02-111">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eed02-111">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="eed02-112">開始之前</span><span class="sxs-lookup"><span data-stu-id="eed02-112">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="eed02-113">Security</span><span class="sxs-lookup"><span data-stu-id="eed02-113">Security</span></span>  
 <span data-ttu-id="eed02-114">如需安全性的相關資訊，請參閱 [RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="eed02-114">For information about security, see [RESTORE HEADERONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-headeronly-transact-sql).</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="eed02-115">權限</span><span class="sxs-lookup"><span data-stu-id="eed02-115">Permissions</span></span>  
 <span data-ttu-id="eed02-116">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 及更新版本中，取得有關備份組或備份裝置的資訊需要 CREATE DATABASE 權限。</span><span class="sxs-lookup"><span data-stu-id="eed02-116">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission.</span></span> <span data-ttu-id="eed02-117">如需詳細資訊，請參閱 [GRANT 資料庫權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="eed02-117">For more information, see [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="eed02-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="eed02-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-content-of-a-backup-tape-or-file"></a><span data-ttu-id="eed02-119">檢視備份磁帶或檔案的內容</span><span class="sxs-lookup"><span data-stu-id="eed02-119">To view the content of a backup tape or file</span></span>  
  
1.  <span data-ttu-id="eed02-120">連線至適當的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]執行個體之後，在 [物件總管] 中按一下伺服器名稱，展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="eed02-120">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="eed02-121">展開 **[資料庫]** ，然後視資料庫而定，選取使用者資料庫，或者展開 **[系統資料庫]** 並選取一個系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="eed02-121">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="eed02-122">以滑鼠右鍵按一下要備份的資料庫，指向 [工作]  ，然後按一下 [備份]  。</span><span class="sxs-lookup"><span data-stu-id="eed02-122">Right-click the database you want to backup, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="eed02-123">會出現 **[備份資料庫]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="eed02-123">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="eed02-124">在 **[一般]** 頁面的 **[目的地]** 區段中，按一下 **[磁碟]** 或 **[磁帶]** 。</span><span class="sxs-lookup"><span data-stu-id="eed02-124">In the **Destination** section of the **General** page, click either **Disk** or **Tape**.</span></span> <span data-ttu-id="eed02-125">在 **[備份至]** 清單方塊中，找出您要的磁碟檔案或磁帶。</span><span class="sxs-lookup"><span data-stu-id="eed02-125">In the **Back up to** list box, look for the disk file or tape you want.</span></span>  
  
     <span data-ttu-id="eed02-126">如果清單方塊中未顯示磁碟檔案或磁帶，按一下 [新增]  。</span><span class="sxs-lookup"><span data-stu-id="eed02-126">If the disk file or tape is not displayed in the list-box, click **Add**.</span></span> <span data-ttu-id="eed02-127">選取檔案名稱或磁帶機。</span><span class="sxs-lookup"><span data-stu-id="eed02-127">Select a file name or tape drive.</span></span> <span data-ttu-id="eed02-128">按一下 [確定]  ，將其加入 [備份至]  清單方塊。</span><span class="sxs-lookup"><span data-stu-id="eed02-128">To add it to the **Back up to** list-box, click **OK**.</span></span>  
  
5.  <span data-ttu-id="eed02-129">在 [備份至]  清單方塊中，選取您要檢視的磁碟或磁帶機路徑，然後按一下 [內容]  。</span><span class="sxs-lookup"><span data-stu-id="eed02-129">In the **Back up to** list-box, select the path of the disk or tape drive you want to view, and click **Contents**.</span></span> <span data-ttu-id="eed02-130">這會開啟 **[裝置內容]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="eed02-130">This opens the **Device Contents** dialog box.</span></span>  
  
6.  <span data-ttu-id="eed02-131">右窗格會針對所選取的磁帶或檔案，顯示其媒體集與備份組的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="eed02-131">The right-hand pane displays information about the media set and backup sets on the selected tape or file.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="eed02-132">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="eed02-132">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-content-of-a-backup-tape-or-file"></a><span data-ttu-id="eed02-133">檢視備份磁帶或檔案的內容</span><span class="sxs-lookup"><span data-stu-id="eed02-133">To view the content of a backup tape or file</span></span>  
  
1.  <span data-ttu-id="eed02-134">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="eed02-134">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="eed02-135">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="eed02-135">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="eed02-136">使用 [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="eed02-136">Use the [RESTORE HEADERONLY](/sql/t-sql/statements/restore-statements-headeronly-transact-sql) statement.</span></span> <span data-ttu-id="eed02-137">此範例會傳回 `AdventureWorks2012-FullBackup.bak`檔案的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="eed02-137">This example returns information about the file named `AdventureWorks2012-FullBackup.bak`.</span></span>  
  
```sql  
USE AdventureWorks2012;  
RESTORE HEADERONLY   
FROM DISK = N'C:\AdventureWorks2012-FullBackup.bak' ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="eed02-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eed02-138">See Also</span></span>  
 <span data-ttu-id="eed02-139">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eed02-139">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span></span>  
 <span data-ttu-id="eed02-140">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eed02-140">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span></span>  
 <span data-ttu-id="eed02-141">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eed02-141">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="eed02-142">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eed02-142">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span></span>  
 <span data-ttu-id="eed02-143">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="eed02-143">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span></span>  
 <span data-ttu-id="eed02-144">[備份裝置 &#40;SQL Server&#41;](backup-devices-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="eed02-144">[Backup Devices &#40;SQL Server&#41;](backup-devices-sql-server.md) </span></span>  
 <span data-ttu-id="eed02-145">[定義磁碟檔案的邏輯備份裝置 &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="eed02-145">[Define a Logical Backup Device for a Disk File &#40;SQL Server&#41;](define-a-logical-backup-device-for-a-disk-file-sql-server.md) </span></span>  
 [<span data-ttu-id="eed02-146">定義磁帶機的邏輯備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="eed02-146">Define a Logical Backup Device for a Tape Drive &#40;SQL Server&#41;</span></span>](define-a-logical-backup-device-for-a-tape-drive-sql-server.md)  
  
  
