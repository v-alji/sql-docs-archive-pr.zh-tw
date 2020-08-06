---
title: 將次要資料庫新增至記錄傳送組態 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- adding secondary databases
- secondary databases [SQL Server], in log shipping
- secondary data files [SQL Server], adding
- log shipping [SQL Server], secondary databases
ms.assetid: b02eba13-f8e6-4684-b7e4-75ea038ea473
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 062df1b53ed74321ba0c75c9df763de79a4802bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596250"
---
# <a name="add-a-secondary-database-to-a-log-shipping-configuration-sql-server"></a><span data-ttu-id="60940-102">將次要資料庫加入至記錄傳送組態 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="60940-102">Add a Secondary Database to a Log Shipping Configuration (SQL Server)</span></span>
  <span data-ttu-id="60940-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ，將次要資料庫加入至 [!INCLUDE[tsql](../../includes/tsql-md.md)]中現有的記錄傳送組態。</span><span class="sxs-lookup"><span data-stu-id="60940-103">This topic describes how to add a secondary database to an existing log shipping configuration in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="60940-104">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="60940-104">**In This Topic**</span></span>  
  
-   <span data-ttu-id="60940-105">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="60940-105">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="60940-106">安全性</span><span class="sxs-lookup"><span data-stu-id="60940-106">Security</span></span>](#Security)  
  
-   <span data-ttu-id="60940-107">**若要加入記錄傳送次要資料庫，請使用：**</span><span class="sxs-lookup"><span data-stu-id="60940-107">**To add a log shipping secondary database, using:**</span></span>  
  
     [<span data-ttu-id="60940-108">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="60940-108">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="60940-109">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="60940-109">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="60940-110">相關工作</span><span class="sxs-lookup"><span data-stu-id="60940-110">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="60940-111">開始之前</span><span class="sxs-lookup"><span data-stu-id="60940-111">Before You Begin</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="60940-112">Security</span><span class="sxs-lookup"><span data-stu-id="60940-112">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="60940-113">權限</span><span class="sxs-lookup"><span data-stu-id="60940-113">Permissions</span></span>  
 <span data-ttu-id="60940-114">記錄傳送預存程序需要 **sysadmin** 固定伺服器角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="60940-114">The log-shipping stored procedures require membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="60940-115">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="60940-115">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-add-a-log-shipping-secondary-database"></a><span data-ttu-id="60940-116">若要加入記錄傳送次要資料庫</span><span class="sxs-lookup"><span data-stu-id="60940-116">To add a log shipping secondary database</span></span>  
  
1.  <span data-ttu-id="60940-117">以滑鼠右鍵按一下記錄傳送組態中要作為主要資料庫的資料庫，然後按一下 [屬性]。</span><span class="sxs-lookup"><span data-stu-id="60940-117">Right-click the database you want to use as your primary database in the log shipping configuration, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="60940-118">在 **[選取頁面]** 下，按一下 **[交易記錄傳送]** 。</span><span class="sxs-lookup"><span data-stu-id="60940-118">Under **Select a page**, click **Transaction Log Shipping**.</span></span>  
  
3.  <span data-ttu-id="60940-119">在 **[次要伺服器執行個體與資料庫]** 下，按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="60940-119">Under **Secondary server instances and databases**, click **Add**.</span></span>  
  
4.  <span data-ttu-id="60940-120">按一下 **[連接]** ，連接到您要做為次要伺服器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="60940-120">Click **Connect** and connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to use as your secondary server.</span></span>  
  
5.  <span data-ttu-id="60940-121">在 **[次要資料庫]** 方塊中，從清單中選擇資料庫，或輸入您要建立的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="60940-121">In the **Secondary database** box, choose a database from the list or type the name of the database you want to create.</span></span>  
  
6.  <span data-ttu-id="60940-122">在 **[初始化次要資料庫]** 索引標籤上，選擇要用於初始化次要資料庫的選項。</span><span class="sxs-lookup"><span data-stu-id="60940-122">On the **Initialize Secondary database** tab, choose the option that you want to use to initialize the secondary database.</span></span>  
  
7.  <span data-ttu-id="60940-123">在 **[複製檔案]** 索引標籤上的 **[複製之檔案的目的資料夾]** 方塊中，輸入交易記錄檔備份所應複製到的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="60940-123">On the **Copy Files tab**, in the **Destination folder for copied files** box, type the path of the folder into which the transaction logs backups should be copied.</span></span> <span data-ttu-id="60940-124">這個資料夾通常位於次要伺服器上。</span><span class="sxs-lookup"><span data-stu-id="60940-124">This folder is often located on the secondary server.</span></span>  
  
8.  <span data-ttu-id="60940-125">請注意 **[複製作業]** 之下 **[排程]** 方塊中所列的複製排程。</span><span class="sxs-lookup"><span data-stu-id="60940-125">Note the copy schedule listed in the **Schedule** box under **Copy job**.</span></span> <span data-ttu-id="60940-126">如果您要自訂安裝的排程，請按一下 **[排程]** ，然後視需要調整 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 排程。</span><span class="sxs-lookup"><span data-stu-id="60940-126">If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span> <span data-ttu-id="60940-127">這個排程應接近備份排程。</span><span class="sxs-lookup"><span data-stu-id="60940-127">This schedule should approximate the backup schedule.</span></span>  
  
9. <span data-ttu-id="60940-128">在 **[還原]** 索引標籤上的 **[還原備份時的資料庫狀態]** 下，選擇 **[不復原模式]** 或 **[待命模式]** 選項。</span><span class="sxs-lookup"><span data-stu-id="60940-128">On the **Restore** tab, under **Database state when restoring backups**, choose the **No recovery mode** or **Standby mode** option.</span></span>  
  
10. <span data-ttu-id="60940-129">如果您選擇 **[待命模式]** 選項，請選擇是否要在還原作業進行時，中斷使用者與次要資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="60940-129">If you chose the **Standby mode** option, choose if you want to disconnect users from the secondary database while the restore operation is underway.</span></span>  
  
11. <span data-ttu-id="60940-130">如果您要延遲次要伺服器上的還原處理序，請在 **[延遲還原備份至少]** 下選擇延遲時間。</span><span class="sxs-lookup"><span data-stu-id="60940-130">If you want to delay the restore process on the secondary server, choose a delay time under **Delay restoring backups at least**.</span></span>  
  
12. <span data-ttu-id="60940-131">在 **[如果未在此時間內進行還原，則發出警示]** 下選擇警示臨界值。</span><span class="sxs-lookup"><span data-stu-id="60940-131">Choose an alert threshold under **Alert if no restore occurs within**.</span></span>  
  
13. <span data-ttu-id="60940-132">請注意 **[還原作業]** 下之 **[排程]** 方塊中所列的還原排程。</span><span class="sxs-lookup"><span data-stu-id="60940-132">Note the restore schedule listed in the **Schedule** box under **Restore job**.</span></span> <span data-ttu-id="60940-133">如果您要自訂安裝的排程，請按一下 **[排程]** ，然後視需要調整 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 排程。</span><span class="sxs-lookup"><span data-stu-id="60940-133">If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span> <span data-ttu-id="60940-134">這個排程應接近備份排程。</span><span class="sxs-lookup"><span data-stu-id="60940-134">This schedule should approximate the backup schedule.</span></span>  
  
14. <span data-ttu-id="60940-135">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="60940-135">Click **OK**.</span></span>  
  
15. <span data-ttu-id="60940-136">按一下 [資料庫屬性] 對話方塊上的 **[確定]** ，開始執行組態處理序。</span><span class="sxs-lookup"><span data-stu-id="60940-136">Click **OK** on the Database Properties dialog box to begin the configuration process.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="60940-137">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="60940-137">Using Transact-SQL</span></span>  
  
#### <a name="to-add-a-log-shipping-secondary-database"></a><span data-ttu-id="60940-138">若要加入記錄傳送次要資料庫</span><span class="sxs-lookup"><span data-stu-id="60940-138">To add a log shipping secondary database</span></span>  
  
1.  <span data-ttu-id="60940-139">在次要伺服器上，執行 [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) ，提供主要伺服器與資料庫的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="60940-139">On the secondary server, execute [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) supplying the details of the primary server and database.</span></span> <span data-ttu-id="60940-140">這個預存程序會傳回次要識別碼及複製與還原作業識別碼。</span><span class="sxs-lookup"><span data-stu-id="60940-140">This stored procedure returns the secondary ID and the copy and restore job IDs.</span></span>  
  
2.  <span data-ttu-id="60940-141">在次要伺服器上執行 [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) ，以設定複製與還原作業的排程。</span><span class="sxs-lookup"><span data-stu-id="60940-141">On the secondary server, execute [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) to set the schedule for the copy and restore jobs.</span></span>  
  
3.  <span data-ttu-id="60940-142">在次要伺服器上執行 [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) ，以加入次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="60940-142">On the secondary server, execute [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) to add a secondary database.</span></span>  
  
4.  <span data-ttu-id="60940-143">在主要伺服器上執行 [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) ，將有關新次要資料庫的必要資訊加入主要伺服器。</span><span class="sxs-lookup"><span data-stu-id="60940-143">On the primary server, execute [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) to add the required information about the new secondary database to the primary server.</span></span>  
  
5.  <span data-ttu-id="60940-144">在次要伺服器上，啟用複製與還原作業。</span><span class="sxs-lookup"><span data-stu-id="60940-144">On the secondary server, enable the copy and restore jobs.</span></span> <span data-ttu-id="60940-145">如需詳細資訊，請參閱 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)。</span><span class="sxs-lookup"><span data-stu-id="60940-145">For more information, see [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="60940-146">相關工作</span><span class="sxs-lookup"><span data-stu-id="60940-146">Related Tasks</span></span>  
  
-   [<span data-ttu-id="60940-147">將記錄傳送升級至 SQL Server 2014 &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="60940-147">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="60940-148">設定記錄傳送 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="60940-148">Configure Log Shipping &#40;SQL Server&#41;</span></span>](configure-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="60940-149">從記錄傳送組態中移除次要資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="60940-149">Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="60940-150">移除記錄傳送 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="60940-150">Remove Log Shipping &#40;SQL Server&#41;</span></span>](remove-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="60940-151">檢視記錄傳送報表 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="60940-151">View the Log Shipping Report &#40;SQL Server Management Studio&#41;</span></span>](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="60940-152">監視記錄傳送 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="60940-152">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="60940-153">容錯移轉至記錄傳送次要 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="60940-153">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="60940-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60940-154">See Also</span></span>  
 <span data-ttu-id="60940-155">[關於記錄傳送 &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="60940-155">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="60940-156">記錄傳送資料表與預存程序</span><span class="sxs-lookup"><span data-stu-id="60940-156">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
