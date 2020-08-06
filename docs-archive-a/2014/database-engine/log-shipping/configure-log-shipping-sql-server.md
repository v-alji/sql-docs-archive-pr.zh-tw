---
title: 設定記錄傳送 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- log shipping [SQL Server], enabling
- log shipping [SQL Server], configuring
ms.assetid: c42aa04a-4945-4417-b4c7-50589d727e9c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 269b0ae2980435e507128cc87606f7eb702c2b7f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688149"
---
# <a name="configure-log-shipping-sql-server"></a><span data-ttu-id="99bd3-102">設定記錄傳送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="99bd3-102">Configure Log Shipping (SQL Server)</span></span>
  <span data-ttu-id="99bd3-103">本主題描述如何使用 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 設定 [!INCLUDE[tsql](../../includes/tsql-md.md)]中的記錄傳送。</span><span class="sxs-lookup"><span data-stu-id="99bd3-103">This topic describes how to configure log shipping in [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] by using [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="99bd3-104">(含) 以後版本支援備份壓縮。</span><span class="sxs-lookup"><span data-stu-id="99bd3-104">and later versions support backup compression.</span></span> <span data-ttu-id="99bd3-105">在建立記錄傳送設定時，您可以控制記錄備份的備份壓縮行為。</span><span class="sxs-lookup"><span data-stu-id="99bd3-105">When creating a log shipping configuration, you can control the backup compression behavior of log backups.</span></span> <span data-ttu-id="99bd3-106">如需詳細資訊，請參閱[備份壓縮 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="99bd3-106">For more information, see [Backup Compression &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-compression-sql-server.md).</span></span>  
  
 <span data-ttu-id="99bd3-107">**本主題內容**</span><span class="sxs-lookup"><span data-stu-id="99bd3-107">**In This Topic**</span></span>  
  
-   <span data-ttu-id="99bd3-108">**開始之前：**</span><span class="sxs-lookup"><span data-stu-id="99bd3-108">**Before you begin:**</span></span>  
  
     [<span data-ttu-id="99bd3-109">先決條件</span><span class="sxs-lookup"><span data-stu-id="99bd3-109">Prerequisites</span></span>](#Prerequisites)  
  
     [<span data-ttu-id="99bd3-110">安全性</span><span class="sxs-lookup"><span data-stu-id="99bd3-110">Security</span></span>](#Security)  
  
-   <span data-ttu-id="99bd3-111">**若要設定記錄傳送，請使用：**</span><span class="sxs-lookup"><span data-stu-id="99bd3-111">**To configure log shipping, using:**</span></span>  
  
     [<span data-ttu-id="99bd3-112">SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="99bd3-112">SQL Server Management Studio</span></span>](#SSMSProcedure)  
  
     [<span data-ttu-id="99bd3-113">Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="99bd3-113">Transact-SQL</span></span>](#TsqlProcedure)  
  
-   [<span data-ttu-id="99bd3-114">相關工作</span><span class="sxs-lookup"><span data-stu-id="99bd3-114">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="99bd3-115">開始之前</span><span class="sxs-lookup"><span data-stu-id="99bd3-115">Before You Begin</span></span>  
  
###  <a name="prerequisites"></a><a name="Prerequisites"></a> <span data-ttu-id="99bd3-116">必要條件</span><span class="sxs-lookup"><span data-stu-id="99bd3-116">Prerequisites</span></span>  
  
-   <span data-ttu-id="99bd3-117">主要資料庫必須使用完整或大量記錄復原模式；若將資料庫切換為簡單復原模式，會使記錄傳送停止運作。</span><span class="sxs-lookup"><span data-stu-id="99bd3-117">The primary database must use the full or bulk-logged recovery model; switching the database to simple recovery will cause log shipping to stop functioning.</span></span>  
  
-   <span data-ttu-id="99bd3-118">在設定記錄傳送之前，您必須建立一個共用，讓次要伺服器能夠使用交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="99bd3-118">Before you configure log shipping, you must create a share to make the transaction log backups available to the secondary server.</span></span> <span data-ttu-id="99bd3-119">這是將要產生交易記錄檔備份之目錄的共用。</span><span class="sxs-lookup"><span data-stu-id="99bd3-119">This is a share of the directory where the transaction log backups will be generated.</span></span> <span data-ttu-id="99bd3-120">例如，您若是將交易記錄備份到 c:\data\tlogs\\目錄，就可以建立該目錄的 \\\\*primaryserver*\tlogs 共用。</span><span class="sxs-lookup"><span data-stu-id="99bd3-120">For example, if you back up your transaction logs to the directory c:\data\tlogs\\, you could create the \\\\*primaryserver*\tlogs share of that directory.</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="99bd3-121">Security</span><span class="sxs-lookup"><span data-stu-id="99bd3-121">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="99bd3-122">權限</span><span class="sxs-lookup"><span data-stu-id="99bd3-122">Permissions</span></span>  
 <span data-ttu-id="99bd3-123">記錄傳送預存程序需要 **sysadmin** 固定伺服器角色中的成員資格。</span><span class="sxs-lookup"><span data-stu-id="99bd3-123">The log-shipping stored procedures require membership in the **sysadmin** fixed server role.</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="99bd3-124">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="99bd3-124">Using SQL Server Management Studio</span></span>  
  
#### <a name="to-configure-log-shipping"></a><span data-ttu-id="99bd3-125">設定記錄傳送</span><span class="sxs-lookup"><span data-stu-id="99bd3-125">To configure log shipping</span></span>  
  
1.  <span data-ttu-id="99bd3-126">以滑鼠右鍵按一下記錄傳送組態中要做為主要資料庫的資料庫，然後按一下 **[屬性]** 。</span><span class="sxs-lookup"><span data-stu-id="99bd3-126">Right click the database you want to use as your primary database in the log shipping configuration, and then click **Properties**.</span></span>  
  
2.  <span data-ttu-id="99bd3-127">在 **[選取頁面]** 下，按一下 **[交易記錄傳送]** 。</span><span class="sxs-lookup"><span data-stu-id="99bd3-127">Under **Select a page**, click **Transaction Log Shipping**.</span></span>  
  
3.  <span data-ttu-id="99bd3-128">選取 **[將此啟用為記錄傳送組態的主要資料庫 ]** 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="99bd3-128">Select the **Enable this as a primary database in a log shipping configuration** check box.</span></span>  
  
4.  <span data-ttu-id="99bd3-129">在 **[交易記錄檔備份]** 下，按一下 **[備份設定]** 。</span><span class="sxs-lookup"><span data-stu-id="99bd3-129">Under **Transaction log backups**, click **Backup Settings**.</span></span>  
  
5.  <span data-ttu-id="99bd3-130">在 **[到備份資料夾的網路路徑]** 方塊中，輸入您針對交易記錄檔備份資料夾所建立之共用的網路路徑。</span><span class="sxs-lookup"><span data-stu-id="99bd3-130">In the **Network path to the backup folder** box, type the network path to the share you created for the transaction log backup folder.</span></span>  
  
6.  <span data-ttu-id="99bd3-131">如果備份資料夾位於主要伺服器，請在 **[如果備份資料夾位於主要伺服器上，請輸入至該資料夾的本機路徑]** 方塊中，輸入備份資料夾的本機路徑</span><span class="sxs-lookup"><span data-stu-id="99bd3-131">If the backup folder is located on the primary server, type the local path to the backup folder in the **If the backup folder is located on the primary server, type a local path to the folder** box.</span></span> <span data-ttu-id="99bd3-132">(如果備份資料夾不在主要伺服器，您可以將這個方塊留空)。</span><span class="sxs-lookup"><span data-stu-id="99bd3-132">(If the backup folder is not on the primary server, you can leave this box empty.)</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="99bd3-133">如果主要伺服器上的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶是在本機系統帳戶下執行，您必須在主要伺服器上建立備份資料夾，並指定該資料夾的本機路徑。</span><span class="sxs-lookup"><span data-stu-id="99bd3-133">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account on your primary server runs under the local system account, you must create your backup folder on the primary server and specify a local path to that folder.</span></span>  
  
7.  <span data-ttu-id="99bd3-134">設定 **[指定刪除檔案的時限]** 及 **[如果未在此時間內進行備份，則發出警示]** 參數。</span><span class="sxs-lookup"><span data-stu-id="99bd3-134">Configure the **Delete files older than** and **Alert if no backup occurs within** parameters.</span></span>  
  
8.  <span data-ttu-id="99bd3-135">請注意 **[備份作業]** 之下 **[排程]** 方塊所列的備份排程。</span><span class="sxs-lookup"><span data-stu-id="99bd3-135">Note the backup schedule listed in the **Schedule** box under **Backup job**.</span></span> <span data-ttu-id="99bd3-136">如果您想要自訂安裝的排程，請按一下 **[排程]** ，並視需要調整 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 排程。</span><span class="sxs-lookup"><span data-stu-id="99bd3-136">If you want to customize the schedule for your installation, then click **Schedule** and adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span>  
  
9. [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] <span data-ttu-id="99bd3-137">支援 [備份壓縮](../../relational-databases/backup-restore/backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="99bd3-137">supports [backup compression](../../relational-databases/backup-restore/backup-compression-sql-server.md).</span></span> <span data-ttu-id="99bd3-138">在建立記錄傳送設定時，您可以透過選擇下列其中一個選項，來控制記錄備份的備份壓縮行為：[使用預設伺服器設定]、[壓縮備份]，或 [不要壓縮備份]。</span><span class="sxs-lookup"><span data-stu-id="99bd3-138">When creating a log shipping configuration, you can control the backup compression behavior of log backups by choosing one of the following options: **Use the default server setting**, **Compress backup**, or **Do not compress backup**.</span></span> <span data-ttu-id="99bd3-139">如需詳細資訊，請參閱 [Log Shipping Transaction Log Backup Settings](../../relational-databases/databases/log-shipping-transaction-log-backup-settings.md)。</span><span class="sxs-lookup"><span data-stu-id="99bd3-139">For more information, see [Log Shipping Transaction Log Backup Settings](../../relational-databases/databases/log-shipping-transaction-log-backup-settings.md).</span></span>  
  
10. <span data-ttu-id="99bd3-140">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="99bd3-140">Click **OK**.</span></span>  
  
11. <span data-ttu-id="99bd3-141">在 **[次要伺服器執行個體與資料庫]** 下，按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="99bd3-141">Under **Secondary server instances and databases**, click **Add**.</span></span>  
  
12. <span data-ttu-id="99bd3-142">按一下 **[連接]** ，連接到您要做為次要伺服器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="99bd3-142">Click **Connect** and connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to use as your secondary server.</span></span>  
  
13. <span data-ttu-id="99bd3-143">在 **[次要資料庫]** 方塊中，從清單中選擇資料庫，或輸入您要建立的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="99bd3-143">In the **Secondary Database** box, choose a database from the list or type the name of the database you want to create.</span></span>  
  
14. <span data-ttu-id="99bd3-144">在 **[初始化次要資料庫]** 索引標籤上，選擇要用於初始化次要資料庫的選項。</span><span class="sxs-lookup"><span data-stu-id="99bd3-144">On the **Initialize Secondary database** tab, choose the option that you want to use to initialize the secondary database.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="99bd3-145">如果您選擇讓 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 從資料庫備份初始化次要資料庫，次要資料庫的資料和記錄檔就會與 **master** 資料庫的資料和記錄檔放置於相同的位置。</span><span class="sxs-lookup"><span data-stu-id="99bd3-145">If you choose to have [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] initialize the secondary database from a database backup, the data and log files of the secondary database are placed in the same location as the data and log files of the **master** database.</span></span> <span data-ttu-id="99bd3-146">這個位置可能會與主要資料庫之資料和記錄檔的位置不同。</span><span class="sxs-lookup"><span data-stu-id="99bd3-146">This location is likely to be different than the location of the data and log files of the primary database.</span></span>  
  
15. <span data-ttu-id="99bd3-147">在 **[複製檔案]** 索引標籤的 **[複製之檔案的目的資料夾]** 方塊中，輸入交易記錄檔備份所應複製到的資料夾路徑。</span><span class="sxs-lookup"><span data-stu-id="99bd3-147">On the **Copy Files** tab, in the **Destination folder for copied files** box, type the path of the folder into which the transaction logs backups should be copied.</span></span> <span data-ttu-id="99bd3-148">這個資料夾通常位於次要伺服器上。</span><span class="sxs-lookup"><span data-stu-id="99bd3-148">This folder is often located on the secondary server.</span></span>  
  
16. <span data-ttu-id="99bd3-149">請注意 **[複製作業]** 之下 **[排程]** 方塊中所列的複製排程。</span><span class="sxs-lookup"><span data-stu-id="99bd3-149">Note the copy schedule listed in the **Schedule** box under **Copy job**.</span></span> <span data-ttu-id="99bd3-150">如果您要自訂安裝的排程，請按一下 **[排程]** ，然後視需要調整 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 排程。</span><span class="sxs-lookup"><span data-stu-id="99bd3-150">If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span> <span data-ttu-id="99bd3-151">這個排程應接近備份排程。</span><span class="sxs-lookup"><span data-stu-id="99bd3-151">This schedule should approximate the backup schedule.</span></span>  
  
17. <span data-ttu-id="99bd3-152">在 **[還原]** 索引標籤上的 **[還原備份時的資料庫狀態]** 下，選擇 **[不復原模式]** 或 **[待命模式]** 選項。</span><span class="sxs-lookup"><span data-stu-id="99bd3-152">On the **Restore** tab, under **Database state when restoring backups**, choose the **No recovery mode** or **Standby mode** option.</span></span>  
  
18. <span data-ttu-id="99bd3-153">如果您選擇 **[待命模式]** 選項，請選擇是否要在還原作業進行時，中斷使用者與次要資料庫的連接。</span><span class="sxs-lookup"><span data-stu-id="99bd3-153">If you chose the **Standby mode** option, choose if you want to disconnect users from the secondary database while the restore operation is underway.</span></span>  
  
19. <span data-ttu-id="99bd3-154">如果您要延遲次要伺服器上的還原處理序，請在 **[延遲還原備份至少]** 下選擇延遲時間。</span><span class="sxs-lookup"><span data-stu-id="99bd3-154">If you want to delay the restore process on the secondary server, choose a delay time under **Delay restoring backups at least**.</span></span>  
  
20. <span data-ttu-id="99bd3-155">在 **[如果未在此時間內進行還原，則發出警示]** 下選擇警示臨界值。</span><span class="sxs-lookup"><span data-stu-id="99bd3-155">Choose an alert threshold under **Alert if no restore occurs within**.</span></span>  
  
21. <span data-ttu-id="99bd3-156">請注意 **[還原作業]** 下之 **[排程]** 方塊中所列的還原排程。</span><span class="sxs-lookup"><span data-stu-id="99bd3-156">Note the restore schedule listed in the **Schedule** box under **Restore job**.</span></span> <span data-ttu-id="99bd3-157">如果您要自訂安裝的排程，請按一下 **[排程]** ，然後視需要調整 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 排程。</span><span class="sxs-lookup"><span data-stu-id="99bd3-157">If you want to customize the schedule for your installation, click **Schedule** and then adjust the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent schedule as needed.</span></span> <span data-ttu-id="99bd3-158">這個排程應接近備份排程。</span><span class="sxs-lookup"><span data-stu-id="99bd3-158">This schedule should approximate the backup schedule.</span></span>  
  
22. <span data-ttu-id="99bd3-159">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="99bd3-159">Click **OK**.</span></span>  
  
23. <span data-ttu-id="99bd3-160">在 **[監視伺服器執行個體]** 下，選取 **[使用監視伺服器執行個體]** 核取方塊，再按一下 **[設定]** 。</span><span class="sxs-lookup"><span data-stu-id="99bd3-160">Under **Monitor server instance**, select the **Use a monitor server instance** check box, and then click **Settings**.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="99bd3-161">若要監視這個記錄傳送組態，您必須立即加入監視伺服器。</span><span class="sxs-lookup"><span data-stu-id="99bd3-161">To monitor this log shipping configuration, you must add the monitor server now.</span></span> <span data-ttu-id="99bd3-162">若要在日後加入監視伺服器，您就必須移除這個記錄傳送組態，然後將它取代成包含監視伺服器的新組態。</span><span class="sxs-lookup"><span data-stu-id="99bd3-162">To add the monitor server later, you would need to remove this log shipping configuration and then replace it with a new configuration that includes a monitor server.</span></span>  
  
24. <span data-ttu-id="99bd3-163">按一下 **[連接]** ，然後連接到要做為監視伺服器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="99bd3-163">Click **Connect** and connect to the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that you want to use as your monitor server.</span></span>  
  
25. <span data-ttu-id="99bd3-164">在 **[監視器連接]** 下，選擇備份、複製及還原作業用來連接到監視伺服器的連接方法。</span><span class="sxs-lookup"><span data-stu-id="99bd3-164">Under **Monitor connections**, choose the connection method to be used by the backup, copy, and restore jobs to connect to the monitor server.</span></span>  
  
26. <span data-ttu-id="99bd3-165">在 **[記錄保留]** 下，選擇您要保留記錄傳送記錄的時間長度。</span><span class="sxs-lookup"><span data-stu-id="99bd3-165">Under **History retention**, choose the length of time you want to retain a record of your log shipping history.</span></span>  
  
27. <span data-ttu-id="99bd3-166">按一下 [確定]。</span><span class="sxs-lookup"><span data-stu-id="99bd3-166">Click **OK**.</span></span>  
  
28. <span data-ttu-id="99bd3-167">在 **[資料庫屬性]** 對話方塊上，按一下 **[確定]** 以開始設定處理序。</span><span class="sxs-lookup"><span data-stu-id="99bd3-167">On the **Database Properties** dialog box, click **OK** to begin the configuration process.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="99bd3-168">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="99bd3-168">Using Transact-SQL</span></span>  
  
#### <a name="to-configure-log-shipping"></a><span data-ttu-id="99bd3-169">設定記錄傳送</span><span class="sxs-lookup"><span data-stu-id="99bd3-169">To configure log shipping</span></span>  
  
1.  <span data-ttu-id="99bd3-170">在次要伺服器上還原主要資料庫的完整備份，以初始化次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="99bd3-170">Initialize the secondary database by restoring a full backup of the primary database on the secondary server.</span></span>  
  
2.  <span data-ttu-id="99bd3-171">在主要伺服器上執行 [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql) ，以加入主要資料庫。</span><span class="sxs-lookup"><span data-stu-id="99bd3-171">On the primary server, execute [sp_add_log_shipping_primary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-database-transact-sql) to add a primary database.</span></span> <span data-ttu-id="99bd3-172">預存程序會傳回備份作業識別碼及主要識別碼。</span><span class="sxs-lookup"><span data-stu-id="99bd3-172">The stored procedure returns the backup job ID and primary ID.</span></span>  
  
3.  <span data-ttu-id="99bd3-173">在主要伺服器上執行 [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) ，以加入排程來供備份作業使用。</span><span class="sxs-lookup"><span data-stu-id="99bd3-173">On the primary server, execute [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) to add a schedule for the backup job.</span></span>  
  
4.  <span data-ttu-id="99bd3-174">在監視伺服器上執行 [sp_add_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-alert-job-transact-sql) ，以加入警示作業。</span><span class="sxs-lookup"><span data-stu-id="99bd3-174">On the monitor server, execute [sp_add_log_shipping_alert_job](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-alert-job-transact-sql) to add the alert job.</span></span>  
  
5.  <span data-ttu-id="99bd3-175">在主要伺服器上啟用備份作業。</span><span class="sxs-lookup"><span data-stu-id="99bd3-175">On the primary server, enable the backup job.</span></span>  
  
6.  <span data-ttu-id="99bd3-176">在次要伺服器上，執行 [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) ，提供主要伺服器與資料庫的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="99bd3-176">On the secondary server, execute [sp_add_log_shipping_secondary_primary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-primary-transact-sql) supplying the details of the primary server and database.</span></span> <span data-ttu-id="99bd3-177">這個預存程序會傳回次要識別碼及複製與還原作業識別碼。</span><span class="sxs-lookup"><span data-stu-id="99bd3-177">This stored procedure returns the secondary ID and the copy and restore job IDs.</span></span>  
  
7.  <span data-ttu-id="99bd3-178">在次要伺服器上執行 [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) ，以設定複製與還原作業的排程。</span><span class="sxs-lookup"><span data-stu-id="99bd3-178">On the secondary server, execute [sp_add_jobschedule](/sql/relational-databases/system-stored-procedures/sp-add-jobschedule-transact-sql) to set the schedule for the copy and restore jobs.</span></span>  
  
8.  <span data-ttu-id="99bd3-179">在次要伺服器上執行 [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) ，以加入次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="99bd3-179">On the secondary server, execute [sp_add_log_shipping_secondary_database](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-secondary-database-transact-sql) to add a secondary database.</span></span>  
  
9. <span data-ttu-id="99bd3-180">在主要伺服器上執行 [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) ，將有關新次要資料庫的必要資訊加入主要伺服器。</span><span class="sxs-lookup"><span data-stu-id="99bd3-180">On the primary server, execute [sp_add_log_shipping_primary_secondary](/sql/relational-databases/system-stored-procedures/sp-add-log-shipping-primary-secondary-transact-sql) to add the required information about the new secondary database to the primary server.</span></span>  
  
10. <span data-ttu-id="99bd3-181">在次要伺服器上，啟用複製與還原作業。</span><span class="sxs-lookup"><span data-stu-id="99bd3-181">On the secondary server, enable the copy and restore jobs.</span></span> <span data-ttu-id="99bd3-182">如需詳細資訊，請參閱 [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md)。</span><span class="sxs-lookup"><span data-stu-id="99bd3-182">For more information, see [Disable or Enable a Job](../../ssms/agent/disable-or-enable-a-job.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="99bd3-183">相關工作</span><span class="sxs-lookup"><span data-stu-id="99bd3-183">Related Tasks</span></span>  
  
-   [<span data-ttu-id="99bd3-184">將記錄傳送升級至 SQL Server 2014 &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="99bd3-184">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="99bd3-185">將次要資料庫加入至記錄傳送組態 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="99bd3-185">Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="99bd3-186">從記錄傳送組態中移除次要資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="99bd3-186">Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="99bd3-187">移除記錄傳送 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="99bd3-187">Remove Log Shipping &#40;SQL Server&#41;</span></span>](remove-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="99bd3-188">檢視記錄傳送報表 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="99bd3-188">View the Log Shipping Report &#40;SQL Server Management Studio&#41;</span></span>](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="99bd3-189">監視記錄傳送 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="99bd3-189">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="99bd3-190">容錯移轉至記錄傳送次要 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="99bd3-190">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="99bd3-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99bd3-191">See Also</span></span>  
 <span data-ttu-id="99bd3-192">[關於記錄傳送 &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="99bd3-192">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="99bd3-193">記錄傳送資料表與預存程序</span><span class="sxs-lookup"><span data-stu-id="99bd3-193">Log Shipping Tables and Stored Procedures</span></span>](log-shipping-tables-and-stored-procedures.md)  
  
  
