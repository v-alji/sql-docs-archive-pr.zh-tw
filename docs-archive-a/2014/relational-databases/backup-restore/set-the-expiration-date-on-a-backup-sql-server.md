---
title: 設定備份的到期日 (SQL Server) | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: backup-restore
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [SQL Server], expiration dates
- expiration [SQL Server]
- database backups [SQL Server], expiration dates
ms.assetid: 76e814df-6487-4893-9f09-7759f1863a5c
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9185222df93e0a1150256535526ba910c593cf6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594111"
---
# <a name="set-the-expiration-date-on-a-backup-sql-server"></a><span data-ttu-id="6b2bb-102">設定備份的到期日 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6b2bb-102">Set the Expiration Date on a Backup (SQL Server)</span></span>
  <span data-ttu-id="6b2bb-103">此主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，在 [!INCLUDE[tsql](../../includes/tsql-md.md)]中設定備份的到期日。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-103">This topic describes how to set the expiration date on a backup in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="6b2bb-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="6b2bb-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="6b2bb-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="6b2bb-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="6b2bb-106">安全性</span><span class="sxs-lookup"><span data-stu-id="6b2bb-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="6b2bb-107">**若要使用下列項目，在備份上設定到期日：**</span><span class="sxs-lookup"><span data-stu-id="6b2bb-107">**To set the expiration date on a backup, using:**</span></span>  
  
     [<span data-ttu-id="6b2bb-108">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6b2bb-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="6b2bb-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6b2bb-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="6b2bb-110">開始之前</span><span class="sxs-lookup"><span data-stu-id="6b2bb-110">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="6b2bb-111">Security</span><span class="sxs-lookup"><span data-stu-id="6b2bb-111">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="6b2bb-112">權限</span><span class="sxs-lookup"><span data-stu-id="6b2bb-112">Permissions</span></span>  
 <span data-ttu-id="6b2bb-113">BACKUP DATABASE 和 BACKUP LOG 權限預設為 **sysadmin** 固定伺服器角色以及 **db_owner** 和 **db_backupoperator** 固定資料庫角色的成員。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-113">BACKUP DATABASE and BACKUP LOG permissions default to members of the **sysadmin** fixed server role and the **db_owner** and **db_backupoperator** fixed database roles.</span></span>  
  
 <span data-ttu-id="6b2bb-114">備份裝置實體檔案的擁有權和權限問題可能會干擾備份作業。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-114">Ownership and permission problems on the backup device's physical file can interfere with a backup operation.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="6b2bb-115">必須能夠讀取和寫入裝置；執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務的帳戶必須具備寫入權限。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-115">must be able to read and write to the device; the account under which the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service runs must have write permissions.</span></span> <span data-ttu-id="6b2bb-116">不過，在系統資料表中加入備份裝置項目的 [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql)並不會檢查檔案存取權限。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-116">However, [sp_addumpdevice](/sql/relational-databases/system-stored-procedures/sp-addumpdevice-transact-sql), which adds an entry for a backup device in the system tables, does not check file access permissions.</span></span> <span data-ttu-id="6b2bb-117">當您嘗試備份或還原時，存取實體資源之前不一定會出現備份裝置實體檔案的這些問題。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-117">Such problems on the backup device's physical file may not appear until the physical resource is accessed when the backup or restore is attempted.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="6b2bb-118">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="6b2bb-118">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-set-the-expiration-date-on-a-backup"></a><span data-ttu-id="6b2bb-119">若要在備份上設定到期日</span><span class="sxs-lookup"><span data-stu-id="6b2bb-119">To set the expiration date on a backup</span></span>  
  
1.  <span data-ttu-id="6b2bb-120">連線至適當的 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)]執行個體之後，在 [物件總管] 中按一下伺服器名稱，以展開伺服器樹狀目錄。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-120">After connecting to the appropriate instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)], in Object Explorer, click the server name to expand the server tree.</span></span>  
  
2.  <span data-ttu-id="6b2bb-121">展開 **[資料庫]** ，然後視資料庫而定，選取使用者資料庫，或者展開 **[系統資料庫]** 並選取一個系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-121">Expand **Databases**, and, depending on the database, either select a user database or expand **System Databases** and select a system database.</span></span>  
  
3.  <span data-ttu-id="6b2bb-122">以滑鼠右鍵按一下資料庫，指向 **[工作]** ，然後按一下 **[備份]** 。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-122">Right-click the database, point to **Tasks**, and then click **Back Up**.</span></span> <span data-ttu-id="6b2bb-123">會出現 **[備份資料庫]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-123">The **Back Up Database** dialog box appears.</span></span>  
  
4.  <span data-ttu-id="6b2bb-124">在 **[一般]** 頁面上的 **[備份組逾期時間]** ，指定到期日以表示備份組可由其他備份覆寫的時間：</span><span class="sxs-lookup"><span data-stu-id="6b2bb-124">On the **General** page, for **Backup set will expire**, specify an expiration date to indicate when the backup set can be overwritten by another backup:</span></span>  
  
    -   <span data-ttu-id="6b2bb-125">若要讓備份組在特定的天數後過期，請按一下 [之後]  \(預設選項)，然後輸入備份組建立之後將會過期的天數。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-125">To have the backup set expire after a specific number of days, click **After** (the default option), and enter the number of days after set creation that the set will expire.</span></span> <span data-ttu-id="6b2bb-126">這個值可以介於 0 到 99999 日之間；值為 0 日意指備份組永遠不會過期。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-126">This value can be from 0 to 99999 days; a value of 0 days means that the backup set will never expire.</span></span>  
  
         <span data-ttu-id="6b2bb-127">預設值會在 **[伺服器屬性]** 對話方塊 ( **[資料庫設定]** 頁面) 的 **[預設備份媒體保留 (以天為單位)]** 選項中設定。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-127">The default value is set in the **Default backup media retention (in days)** option of the **Server Properties** dialog box (**Database Settings** page).</span></span> <span data-ttu-id="6b2bb-128">若要存取，請以滑鼠右鍵按一下物件總管中的伺服器名稱並選取 [屬性]，然後選取 [資料庫設定]  頁面。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-128">To access this, right-click the server name in Object Explorer and select properties; then select the **Database Settings** page.</span></span>  
  
    -   <span data-ttu-id="6b2bb-129">若要讓備份組在特定日期過期，請按一下 **[於]** ，然後輸入備份組將過期的日期。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-129">To have the backup set expire on a specific date, click **On**, and enter the date on which the set will expire.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="6b2bb-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="6b2bb-130">Using Transact-SQL</span></span>  
  
#### <a name="to-set-the-expiration-date-on-a-backup"></a><span data-ttu-id="6b2bb-131">若要在備份上設定到期日</span><span class="sxs-lookup"><span data-stu-id="6b2bb-131">To set the expiration date on a backup</span></span>  
  
1.  <span data-ttu-id="6b2bb-132">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-132">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="6b2bb-133">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-133">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="6b2bb-134">在 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 陳述式中，指定 EXPIREDATE 或 RETAINDAYS 選項，以決定 [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] 何時可覆寫備份。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-134">In the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement, specify either the EXPIREDATE or RETAINDAYS option to determine when the [!INCLUDE[ssDEnoversion](../../../includes/ssdenoversion-md.md)] can overwrite the backup.</span></span> <span data-ttu-id="6b2bb-135">如果沒有指定任何選項，便會由 [media retention](../../database-engine/configure-windows/configure-the-media-retention-server-configuration-option.md) 伺服器組態設定來決定到期日。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-135">If neither option is specified, the expiration date is determined by the [media retention](../../database-engine/configure-windows/configure-the-media-retention-server-configuration-option.md) server configuration setting.</span></span> <span data-ttu-id="6b2bb-136">此範例使用 `EXPIREDATE` 選項，指定到期日為 2015 年 6 月 30 日 (`6/30/2015`)。</span><span class="sxs-lookup"><span data-stu-id="6b2bb-136">This example uses the `EXPIREDATE` option to specify an expiration date of June 30, 2015 (`6/30/2015`).</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
BACKUP DATABASE AdventureWorks2012  
 TO DISK = 'Z:\SQLServerBackups\AdventureWorks2012.Bak'  
   WITH EXPIREDATE = '6/30/2015' ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="6b2bb-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b2bb-137">See Also</span></span>  
 <span data-ttu-id="6b2bb-138">[建立完整資料庫備份 &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6b2bb-138">[Create a Full Database Backup &#40;SQL Server&#41;](create-a-full-database-backup-sql-server.md) </span></span>  
 <span data-ttu-id="6b2bb-139">[備份檔案和檔案群組 &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6b2bb-139">[Back Up Files and Filegroups &#40;SQL Server&#41;](back-up-files-and-filegroups-sql-server.md) </span></span>  
 <span data-ttu-id="6b2bb-140">[備份交易記錄 &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="6b2bb-140">[Back Up a Transaction Log &#40;SQL Server&#41;](back-up-a-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="6b2bb-141">建立差異資料庫備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6b2bb-141">Create a Differential Database Backup &#40;SQL Server&#41;</span></span>](create-a-differential-database-backup-sql-server.md)  
  
  
