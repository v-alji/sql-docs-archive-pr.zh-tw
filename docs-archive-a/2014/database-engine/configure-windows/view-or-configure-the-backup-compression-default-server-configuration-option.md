---
title: 檢視或設定 backup compression default 伺服器組態選項 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Management Studio [SQL Server], backup compression default option
- backup compression [SQL Server], backup compression default Option
ms.assetid: 23029395-3e93-4c29-b7d6-e5a47a3526ff
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: f02458c069d7c155b199e24feb7ef028ae0f258a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607077"
---
# <a name="view-or-configure-the-backup-compression-default-server-configuration-option"></a><span data-ttu-id="046f8-102">檢視或設定 backup compression default 伺服器組態選項</span><span class="sxs-lookup"><span data-stu-id="046f8-102">View or Configure the backup compression default Server Configuration Option</span></span>
  <span data-ttu-id="046f8-103">本主題描述如何使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)]，在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中檢視或設定 [備份壓縮預設] 伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="046f8-103">This topic describes how to view or configure the **backup compression default** server configuration option in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="046f8-104">**backup compression default** 選項決定伺服器執行個體根據預設是否會建立壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="046f8-104">The **backup compression default** option determines whether the server instance creates compressed backups by default.</span></span> <span data-ttu-id="046f8-105">安裝 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時， **ssCurrent** 選項已關閉。</span><span class="sxs-lookup"><span data-stu-id="046f8-105">When [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is installed, the **backup compression default** option is off.</span></span>  
  
 <span data-ttu-id="046f8-106">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="046f8-106">**In This Topic**</span></span>  
  
-   <span data-ttu-id="046f8-107">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="046f8-107">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="046f8-108">限制事項</span><span class="sxs-lookup"><span data-stu-id="046f8-108">Limitations and Restrictions</span></span>](#Restrictions)  
  
     [<span data-ttu-id="046f8-109">建議</span><span class="sxs-lookup"><span data-stu-id="046f8-109">Recommendations</span></span>](#Recommendations)  
  
     [<span data-ttu-id="046f8-110">安全性</span><span class="sxs-lookup"><span data-stu-id="046f8-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="046f8-111">**使用下列方法檢視或設定 backup compression default 選項：**</span><span class="sxs-lookup"><span data-stu-id="046f8-111">**To view or configure the backup compression default option, using:**</span></span>  
  
     [<span data-ttu-id="046f8-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="046f8-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="046f8-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="046f8-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   <span data-ttu-id="046f8-114">**後續操作：** [設定 backup compression default 選項之後](#FollowUp)</span><span class="sxs-lookup"><span data-stu-id="046f8-114">**Follow Up:**  [After you configure the backup compression default option](#FollowUp)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="046f8-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="046f8-115">Before You Begin</span></span>  
  
###  <a name="limitations-and-restrictions"></a><a name="Restrictions"></a> <span data-ttu-id="046f8-116">限制事項</span><span class="sxs-lookup"><span data-stu-id="046f8-116">Limitations and Restrictions</span></span>  
  
-   <span data-ttu-id="046f8-117">並非 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的所有版本中都提供備份壓縮。</span><span class="sxs-lookup"><span data-stu-id="046f8-117">Backup compression is not available in all editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="046f8-118">如需詳細資訊，請參閱＜ [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md)＞。</span><span class="sxs-lookup"><span data-stu-id="046f8-118">For more information, see [Features Supported by the Editions of SQL Server 2014](../../getting-started/features-supported-by-the-editions-of-sql-server-2014.md).</span></span>  
  
-   <span data-ttu-id="046f8-119">根據預設，壓縮會大幅增加 CPU 使用量，而且壓縮程序所耗用的額外 CPU 可能會對並行作業造成不良的影響。</span><span class="sxs-lookup"><span data-stu-id="046f8-119">By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations.</span></span> <span data-ttu-id="046f8-120">因此，您可能會想要在由[資源管理員](../../relational-databases/resource-governor/resource-governor.md)所限制之 CPU 使用量的工作階段中建立低優先權的壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="046f8-120">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).</span></span> <span data-ttu-id="046f8-121">如需詳細資訊，請參閱本主題稍後介紹的＜ [使用資源管理員進行備份壓縮，以限制 CPU 使用率 &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)限制的工作階段中，建立低優先權的壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="046f8-121">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="046f8-122">建議</span><span class="sxs-lookup"><span data-stu-id="046f8-122">Recommendations</span></span>  
  
-   <span data-ttu-id="046f8-123">當您建立個別備份、設定記錄傳送組態或建立維護計畫時，可以覆寫伺服器層級的預設值。</span><span class="sxs-lookup"><span data-stu-id="046f8-123">When you are creating an individual backup, configuring a log shipping configuration, or creating a maintenance plan, you can override the server-level default.</span></span>  
  
-   <span data-ttu-id="046f8-124">備份壓縮同時支援磁碟備份裝置和磁帶備份裝置。</span><span class="sxs-lookup"><span data-stu-id="046f8-124">Backup compression is supported for both disk backup devices and tape backup devices.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="046f8-125">Security</span><span class="sxs-lookup"><span data-stu-id="046f8-125">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="046f8-126">權限</span><span class="sxs-lookup"><span data-stu-id="046f8-126">Permissions</span></span>  
 <span data-ttu-id="046f8-127">不含參數或只含第一個參數之 **sp_configure** 上的執行權限預設會授與所有使用者。</span><span class="sxs-lookup"><span data-stu-id="046f8-127">Execute permissions on **sp_configure** with no parameters or with only the first parameter are granted to all users by default.</span></span> <span data-ttu-id="046f8-128">以同時設定兩個參數的 **sp_configure** 來變更組態選項或執行 RECONFIGURE 陳述式時，使用者必須取得 ALTER SETTINGS 伺服器層級權限。</span><span class="sxs-lookup"><span data-stu-id="046f8-128">To execute **sp_configure** with both parameters to change a configuration option or to run the RECONFIGURE statement, a user must be granted the ALTER SETTINGS server-level permission.</span></span> <span data-ttu-id="046f8-129">**系統管理員 (sysadmin)** 及 **serveradmin** 固定伺服器角色會隱含 ALTER SETTINGS 權限。</span><span class="sxs-lookup"><span data-stu-id="046f8-129">The ALTER SETTINGS permission is implicitly held by the **sysadmin** and **serveradmin** fixed server roles.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="046f8-130">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="046f8-130">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-view-or-configure-the-backup-compression-default-option"></a><span data-ttu-id="046f8-131">檢視或設定 backup compression default 選項</span><span class="sxs-lookup"><span data-stu-id="046f8-131">To view or configure the backup compression default option</span></span>  
  
1.  <span data-ttu-id="046f8-132">在物件總管中，請以滑鼠右鍵按一下伺服器，然後選取 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="046f8-132">In Object Explorer, right-click a server and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="046f8-133">按一下 **[資料庫設定]** 節點。</span><span class="sxs-lookup"><span data-stu-id="046f8-133">Click the **Database settings** node.</span></span>  
  
3.  <span data-ttu-id="046f8-134">在 **[備份與還原]** 底下， **[壓縮備份]** 會顯示 **backup compression default** 選項的目前設定。</span><span class="sxs-lookup"><span data-stu-id="046f8-134">Under **Backup and restore**, **Compress backup** shows the current setting of the **backup compression default** option.</span></span> <span data-ttu-id="046f8-135">這項設定會決定壓縮備份的伺服器層級預設值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="046f8-135">This setting determines the server-level default for compressing backups, as follows:</span></span>  
  
    -   <span data-ttu-id="046f8-136">如果 **[壓縮備份]** 方塊是空的，新備份預設不會進行壓縮。</span><span class="sxs-lookup"><span data-stu-id="046f8-136">If the **Compress backup** box is blank, new backups are uncompressed by default.</span></span>  
  
    -   <span data-ttu-id="046f8-137">如果 **[壓縮備份]** 方塊已核取，新備份預設就會進行壓縮。</span><span class="sxs-lookup"><span data-stu-id="046f8-137">If the **Compress backup** box is checked, new backups are compressed by default.</span></span>  
  
     <span data-ttu-id="046f8-138">如果您是 **sysadmin** 或 **serveradmin** 固定伺服器角色的成員，也可以透過按一下 **[壓縮備份]** 方塊，變更預設值。</span><span class="sxs-lookup"><span data-stu-id="046f8-138">If you are a member of the **sysadmin** or **serveradmin** fixed server role, you can also change the default setting by clicking the **Compress backup** box.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="046f8-139">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="046f8-139">Using Transact-SQL</span></span>  
  
#### <a name="to-view-the-backup-compression-default-option"></a><span data-ttu-id="046f8-140">檢視 backup compression default 選項</span><span class="sxs-lookup"><span data-stu-id="046f8-140">To view the backup compression default option</span></span>  
  
1.  <span data-ttu-id="046f8-141">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="046f8-141">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="046f8-142">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="046f8-142">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="046f8-143">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="046f8-143">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="046f8-144">這個範例會查詢 [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) 目錄檢視以判斷 `backup compression default`的值。</span><span class="sxs-lookup"><span data-stu-id="046f8-144">This example queries the [sys.configurations](/sql/relational-databases/system-catalog-views/sys-configurations-transact-sql) catalog view to determine the value for `backup compression default`.</span></span> <span data-ttu-id="046f8-145">值為 0 表示備份壓縮已關閉，值為 1 表示備份壓縮已啟用。</span><span class="sxs-lookup"><span data-stu-id="046f8-145">A value of 0 means that backup compression is off, and a value of 1 means that backup compression is enabled.</span></span>  
  
```sql  
USE AdventureWorks2012 ;  
GO  
SELECT value   
FROM sys.configurations   
WHERE name = 'backup compression default' ;  
GO  
  
```  
  
#### <a name="to-configure-the-backup-compression-default-option"></a><span data-ttu-id="046f8-146">設定 backup compression default 選項</span><span class="sxs-lookup"><span data-stu-id="046f8-146">To configure the backup compression default option</span></span>  
  
1.  <span data-ttu-id="046f8-147">連接到 [!INCLUDE[ssDE](../../includes/ssde-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="046f8-147">Connect to the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span>  
  
2.  <span data-ttu-id="046f8-148">在標準列中，按一下 **[新增查詢]** 。</span><span class="sxs-lookup"><span data-stu-id="046f8-148">From the Standard bar, click **New Query**.</span></span>  
  
3.  <span data-ttu-id="046f8-149">複製下列範例並將其貼到查詢視窗中，然後按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="046f8-149">Copy and paste the following example into the query window and click **Execute**.</span></span> <span data-ttu-id="046f8-150">這個範例示範如何使用 [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) ，將伺服器執行個體設定為依預設會建立壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="046f8-150">This example shows how to use [sp_configure](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) to configure the server instance to create compressed backups by default.</span></span>  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_configure 'backup compression default', 1 ;  
RECONFIGURE WITH OVERRIDE ;  
GO  
  
```  
  
 <span data-ttu-id="046f8-151">如需詳細資訊，請參閱 [伺服器設定選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md)伺服器組態選項。</span><span class="sxs-lookup"><span data-stu-id="046f8-151">For more information, see [Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md).</span></span>  
  
##  <a name="follow-up-after-you-configure-the-backup-compression-default-option"></a><a name="FollowUp"></a> <span data-ttu-id="046f8-152">後續操作：設定 backup compression default 選項之後</span><span class="sxs-lookup"><span data-stu-id="046f8-152">Follow Up: After you configure the backup compression default option</span></span>  
 <span data-ttu-id="046f8-153">設定會立即生效，不需要重新啟動伺服器。</span><span class="sxs-lookup"><span data-stu-id="046f8-153">The setting takes effect immediately without restarting the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="046f8-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="046f8-154">See Also</span></span>  
 <span data-ttu-id="046f8-155">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="046f8-155">[BACKUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/backup-transact-sql) </span></span>  
 <span data-ttu-id="046f8-156">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="046f8-156">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 <span data-ttu-id="046f8-157">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="046f8-157">[RECONFIGURE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/reconfigure-transact-sql) </span></span>  
 <span data-ttu-id="046f8-158">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="046f8-158">[sp_configure &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-configure-transact-sql) </span></span>  
 [<span data-ttu-id="046f8-159">備份概觀 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="046f8-159">Backup Overview &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/backup-overview-sql-server.md)  
  
  
