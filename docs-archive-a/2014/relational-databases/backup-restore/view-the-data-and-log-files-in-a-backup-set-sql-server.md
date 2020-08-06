---
title: 檢視備份組中的資料和記錄檔 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- database backups [SQL Server], viewing backup sets
- viewing backup set information
- backup sets [SQL Server], viewing files in
- displaying backup set information
- transaction log backups [SQL Server], viewing backup sets
- backing up [SQL Server], viewing backup sets
ms.assetid: abb6420c-f809-426e-aeb4-d0a74989cf39
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7dbcb14a658b49aba6f5f2ebe3425a2ab5759efa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703009"
---
# <a name="view-the-data-and-log-files-in-a-backup-set-sql-server"></a><span data-ttu-id="008bd-102">檢視備份組中的資料和記錄檔 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="008bd-102">View the Data and Log Files in a Backup Set (SQL Server)</span></span>
  <span data-ttu-id="008bd-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中檢視備份組中的資料和記錄檔。</span><span class="sxs-lookup"><span data-stu-id="008bd-103">This topic describes how to view the data and log files in a backup set in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="008bd-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="008bd-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="008bd-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="008bd-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="008bd-106">安全性</span><span class="sxs-lookup"><span data-stu-id="008bd-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="008bd-107">**若要使用下列項目檢視備份組中的資料和記錄檔：**</span><span class="sxs-lookup"><span data-stu-id="008bd-107">**To view the data and log files in a backup set, using:**</span></span>  
  
     [<span data-ttu-id="008bd-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="008bd-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="008bd-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="008bd-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="008bd-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="008bd-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="008bd-111">Security</span><span class="sxs-lookup"><span data-stu-id="008bd-111">Security</span></span>  
 <span data-ttu-id="008bd-112">如需安全性的相關資訊，請參閱 [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="008bd-112">For information about security, see [RESTORE FILELISTONLY &#40;Transact-SQL&#41;](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql)</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="008bd-113">權限</span><span class="sxs-lookup"><span data-stu-id="008bd-113">Permissions</span></span>  
 <span data-ttu-id="008bd-114">在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 及更新版本中，取得有關備份組或備份裝置的資訊需要 CREATE DATABASE 權限。</span><span class="sxs-lookup"><span data-stu-id="008bd-114">In [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions, obtaining information about a backup set or backup device requires CREATE DATABASE permission.</span></span> <span data-ttu-id="008bd-115">如需詳細資訊，請參閱 [GRANT 資料庫權限 &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="008bd-115">For more information, see [GRANT Database Permissions &#40;Transact-SQL&#41;](/sql/t-sql/statements/grant-database-permissions-transact-sql).</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="008bd-116">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="008bd-116">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-the-data-and-log-files-in-a-backup-set"></a><span data-ttu-id="008bd-117">檢視備份組中的資料與記錄檔</span><span class="sxs-lookup"><span data-stu-id="008bd-117">To view the data and log files in a backup set</span></span>  
  
1.  <span data-ttu-id="008bd-118">連線到適當的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體之後，在物件總管中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="008bd-118">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="008bd-119">展開 **[資料庫]** ，然後視資料庫而定，選取使用者資料庫，或者展開 **[系統資料庫]** 並選取一個系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="008bd-119">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="008bd-120">以滑鼠右鍵按一下資料庫，然後按一下 [屬性]  ，這會開啟 [資料庫屬性]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="008bd-120">Right-click the database, and then click **Properties**, which opens the **Database Properties** dialog box.</span></span>  
  
4.  <span data-ttu-id="008bd-121">在 **[選取頁面]** 窗格中，按一下 **[檔案]** 。</span><span class="sxs-lookup"><span data-stu-id="008bd-121">In the **Select a Page** pane, click **Files**.</span></span>  
  
5.  <span data-ttu-id="008bd-122">在 **[資料庫檔案]** 方格中尋找資料與記錄檔的清單，以及這些檔案的屬性。</span><span class="sxs-lookup"><span data-stu-id="008bd-122">Look in the **Database files** grid for a list of the data and log files and their properties.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="008bd-123">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="008bd-123">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-data-and-log-files-in-a-backup-set"></a><span data-ttu-id="008bd-124">檢視備份組中的資料與記錄檔</span><span class="sxs-lookup"><span data-stu-id="008bd-124">To view the data and log files in a backup set</span></span>  
  
1.  <span data-ttu-id="008bd-125">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="008bd-125">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="008bd-126">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="008bd-126">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="008bd-127">使用 [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="008bd-127">Use the [RESTORE FILELISTONLY](/sql/t-sql/statements/restore-statements-filelistonly-transact-sql) statement.</span></span> <span data-ttu-id="008bd-128">此範例會傳回`FILE=2`備份裝置上第二個備份組 ( `AdventureWorksBackups` ) 的資訊。</span><span class="sxs-lookup"><span data-stu-id="008bd-128">This example returns information about the second backup set (`FILE=2`) on the `AdventureWorksBackups` backup device.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
RESTORE FILELISTONLY FROM AdventureWorksBackups   
   WITH FILE=2;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="008bd-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="008bd-129">See Also</span></span>  
 <span data-ttu-id="008bd-130">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="008bd-130">[backupfilegroup &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfilegroup-transact-sql) </span></span>  
 <span data-ttu-id="008bd-131">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="008bd-131">[backupfile &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupfile-transact-sql) </span></span>  
 <span data-ttu-id="008bd-132">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="008bd-132">[backupset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupset-transact-sql) </span></span>  
 <span data-ttu-id="008bd-133">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="008bd-133">[backupmediaset &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediaset-transact-sql) </span></span>  
 <span data-ttu-id="008bd-134">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="008bd-134">[backupmediafamily &#40;Transact-SQL&#41;](/sql/relational-databases/system-tables/backupmediafamily-transact-sql) </span></span>  
 [<span data-ttu-id="008bd-135">備份裝置 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="008bd-135">Backup Devices &#40;SQL Server&#41;</span></span>](backup-devices-sql-server.md)  
  
  
