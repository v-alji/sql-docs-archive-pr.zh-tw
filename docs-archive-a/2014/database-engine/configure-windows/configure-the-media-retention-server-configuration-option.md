---
title: 設定 media retention 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- backup retention duration [SQL Server]
- backup sets [SQL Server], retention duration
- media retention option
ms.assetid: 12e9fe6a-20a5-4c6e-9cc9-d500c003b70a
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 092e0a2b5cfc30fd2d2362645fc1242bf4a1651e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594178"
---
# <a name="configure-the-media-retention-server-configuration-option"></a><span data-ttu-id="a8ec9-102">設定 media retention 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="a8ec9-102">Configure the media retention Server Configuration Option</span></span>
  <span data-ttu-id="a8ec9-103">此主題描述如何使用 **或** ，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中設定 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] media retention [!INCLUDE[tsql](../../includes/tsql-md.md)]伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-103">This topic describes how to configure the **media retention** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="a8ec9-104">**media retention** 選項指定每個備份組的保留時間。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-104">The **media retention** option specifies the length of time to retain each backup set.</span></span> <span data-ttu-id="a8ec9-105">此選項協助保護備份，在指定的天數經過之前不被覆寫。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-105">The option helps protect backups from being overwritten until the specified number of days has elapsed.</span></span> <span data-ttu-id="a8ec9-106">在設定 **media retention** 選項之後，每次執行備份時不需指定保留系統備份的時間長度。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-106">After you configure **media retention** option, you do not have to specify the length of time to retain system backups each time you perform a backup.</span></span> <span data-ttu-id="a8ec9-107">預設值是 0 天，最大值是 365 天。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-107">The default value is 0 days, and the maximum value is 365 days.</span></span>  
  
 <span data-ttu-id="a8ec9-108">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="a8ec9-108">**In This Topic**</span></span>  
  
-   <span data-ttu-id="a8ec9-109">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="a8ec9-109">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="a8ec9-110">限制事項</span><span class="sxs-lookup"><span data-stu-id="a8ec9-110">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="a8ec9-111">建議</span><span class="sxs-lookup"><span data-stu-id="a8ec9-111">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="a8ec9-112">安全性</span><span class="sxs-lookup"><span data-stu-id="a8ec9-112">Security</span></span>](#Security)  
  
-   <span data-ttu-id="a8ec9-113">**使用下列方法設定 media retention 選項：**</span><span class="sxs-lookup"><span data-stu-id="a8ec9-113">**To configure the media retention option, using:**</span></span>  
  
     [<span data-ttu-id="a8ec9-114">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a8ec9-114">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="a8ec9-115">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a8ec9-115">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="a8ec9-116">**後續操作：** [設定媒體保留選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="a8ec9-116">**Follow Up:**  [After you configure the media retention option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="a8ec9-117">開始之前</span><span class="sxs-lookup"><span data-stu-id="a8ec9-117">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="a8ec9-118">限制事項</span><span class="sxs-lookup"><span data-stu-id="a8ec9-118">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="a8ec9-119">如果您在超過設定的天數之前使用備份媒體， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將發出警告訊息。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-119">If you use the backup medium before the set number of days has passed, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] issues a warning message.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a8ec9-120">將不會發出警告。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-120">does not issue a warning unless you change the default.</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="a8ec9-121">建議</span><span class="sxs-lookup"><span data-stu-id="a8ec9-121">Recommendations</span></span>  
  
-   <span data-ttu-id="a8ec9-122">這個選項是進階選項，只有有經驗的資料庫管理員或通過認證的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 技術人員才可變更。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-122">This option is an advanced option and should be changed only by an experienced database administrator or certified [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] technician.</span></span>  
  
-   <span data-ttu-id="a8ec9-123">**media retention** 選項可使用 [BACKUP](/sql/t-sql/statements/backup-transact-sql) 陳述式的 RETAINDAYS 子句完成覆寫。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-123">The **media retention** option can be overridden by using the RETAINDAYS clause of the [BACKUP](/sql/t-sql/statements/backup-transact-sql) statement.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="a8ec9-124">Security</span><span class="sxs-lookup"><span data-stu-id="a8ec9-124">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="a8ec9-125">權限</span><span class="sxs-lookup"><span data-stu-id="a8ec9-125">Permissions</span></span>  
 <span data-ttu-id="a8ec9-126">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-126">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="a8ec9-127">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-127">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="a8ec9-128">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-128">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="a8ec9-129">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="a8ec9-129">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-the-media-retention-option"></a><span data-ttu-id="a8ec9-130">設定 media retention 選項</span><span class="sxs-lookup"><span data-stu-id="a8ec9-130">To configure the media retention option</span></span>  
  
1.  <span data-ttu-id="a8ec9-131">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-131">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="a8ec9-132">按一下 **[資料庫設定]** 節點。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-132">Click the **Database settings** node.</span></span>  
  
3.  <span data-ttu-id="a8ec9-133">在 **[備份/還原]** 的 **[預設備份媒體保留]** 方塊中，輸入或選取 0 到 365 間的任一數值，以設定進行資料庫或交易記錄備份之後，備份媒體的保留天數。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-133">Under **Backup/Restore**, in the **Default backup media retention** box, type or select a value from 0 through 365 to set the number of days the backup medium will be retained after a database or transaction log backup.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="a8ec9-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="a8ec9-134">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-the-media-retention-option"></a><span data-ttu-id="a8ec9-135">設定 media retention 選項</span><span class="sxs-lookup"><span data-stu-id="a8ec9-135">To configure the media retention option</span></span>  
  
1.  <span data-ttu-id="a8ec9-136">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-136">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="a8ec9-137">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-137">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="a8ec9-138">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-138">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="a8ec9-139">此範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) 將 `media retention` 選項的值設定為 `60` 天。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-139">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to set the value of the `media retention` option to `60` days.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE ;  
GO  
EXEC sp_configure 'media retention', 60 ;  
GO  
RECONFIGURE;  
GO  
  
```  
  
 <span data-ttu-id="a8ec9-140">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-140">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-media-retention-option"></a><a name="FollowUp"></a> <span data-ttu-id="a8ec9-141">後續操作：設定媒體保留選項之後</span><span class="sxs-lookup"><span data-stu-id="a8ec9-141">Follow Up: After you configure the media retention option</span></span>  
 <span data-ttu-id="a8ec9-142">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="a8ec9-142">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8ec9-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8ec9-143">See Also</span></span>  
 <span data-ttu-id="a8ec9-144">[SQL Server 資料庫的備份與還原](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="a8ec9-144">[Back Up and Restore of SQL Server Databases](../../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 <span data-ttu-id="a8ec9-145">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a8ec9-145">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="a8ec9-146">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="a8ec9-146">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="a8ec9-147">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="a8ec9-147">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="a8ec9-148">sp_configure &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="a8ec9-148">sp_configure &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql)  
  
  
