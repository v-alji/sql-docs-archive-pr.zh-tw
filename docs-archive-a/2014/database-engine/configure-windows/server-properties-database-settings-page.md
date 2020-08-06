---
title: 伺服器屬性 (資料庫設定頁面) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
f1_keywords:
- sql12.swb.serverproperties.databasesettings.f1
ms.assetid: 1cebdbd3-cbfd-4a02-bba6-a5addf4e3ada
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 3beb2b6aa9a34982cccdfb252941c1c779a16121
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706710"
---
# <a name="server-properties-database-settings-page"></a><span data-ttu-id="acd60-102">伺服器屬性 (資料庫設定頁面)</span><span class="sxs-lookup"><span data-stu-id="acd60-102">Server Properties (Database Settings Page)</span></span>
  <span data-ttu-id="acd60-103">使用此頁面來檢視或修改您的資料庫設定。</span><span class="sxs-lookup"><span data-stu-id="acd60-103">Use this page to view or modify your database settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="acd60-104">選項。</span><span class="sxs-lookup"><span data-stu-id="acd60-104">Options</span></span>  
 <span data-ttu-id="acd60-105">**預設索引填滿因數**</span><span class="sxs-lookup"><span data-stu-id="acd60-105">**Default index fill factor**</span></span>  
 <span data-ttu-id="acd60-106">指定當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 使用現有的資料建立新索引時，它應該填入每個頁面的程度。</span><span class="sxs-lookup"><span data-stu-id="acd60-106">Specifies how full [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] should make each page when it creates a new index using existing data.</span></span> <span data-ttu-id="acd60-107">填滿因數會影響效能，因為當頁面填滿之後， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 就必須花費時間進行頁面的分割。</span><span class="sxs-lookup"><span data-stu-id="acd60-107">The fill factor affects performance because [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must take time to split pages when they fill up.</span></span>  
  
 <span data-ttu-id="acd60-108">預設值是 0，有效值的範圍是從 0 到 100。</span><span class="sxs-lookup"><span data-stu-id="acd60-108">The default value is 0; valid values range from 0 through 100.</span></span> <span data-ttu-id="acd60-109">填滿因數 0 或 100 會以完整分葉頁面建立有完整資料頁面和非叢集索引的叢集索引，但是會在索引樹狀結構的上層保留部分空間。</span><span class="sxs-lookup"><span data-stu-id="acd60-109">A fill factor of 0 or 100 creates clustered indexes with full data pages and nonclustered indexes with full leaf pages, but it leaves some space within the upper level of the index tree.</span></span> <span data-ttu-id="acd60-110">從各方面來說，填滿因數值 0 和 100 都相同。</span><span class="sxs-lookup"><span data-stu-id="acd60-110">Fill factor values 0 and 100 are identical in all respects.</span></span>  
  
 <span data-ttu-id="acd60-111">較小的填滿因數值會使 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 建立不完全填滿頁面的索引。</span><span class="sxs-lookup"><span data-stu-id="acd60-111">Small fill factor values cause [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to create indexes with pages that are not full.</span></span> <span data-ttu-id="acd60-112">每一個索引佔用更多的儲存空間，但後續可以有更多插入空間，不需要再分割頁面。</span><span class="sxs-lookup"><span data-stu-id="acd60-112">Each index takes more storage space, but there is more room for subsequent insertions without requiring page splits.</span></span>  
  
 <span data-ttu-id="acd60-113">**永遠等候**</span><span class="sxs-lookup"><span data-stu-id="acd60-113">**Wait indefinitely**</span></span>  
 <span data-ttu-id="acd60-114">指定 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 在等候新備份磁帶時永不逾時。</span><span class="sxs-lookup"><span data-stu-id="acd60-114">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will never time out while waiting for a new backup tape.</span></span>  
  
 <span data-ttu-id="acd60-115">**嘗試一次**</span><span class="sxs-lookup"><span data-stu-id="acd60-115">**Try once**</span></span>  
 <span data-ttu-id="acd60-116">指定如果需要備份磁帶卻無法使用時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會逾時。</span><span class="sxs-lookup"><span data-stu-id="acd60-116">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will time out if a backup tape is not available when needed.</span></span>  
  
 <span data-ttu-id="acd60-117">**嘗試分鐘數**</span><span class="sxs-lookup"><span data-stu-id="acd60-117">**Try for minute(s)**</span></span>  
 <span data-ttu-id="acd60-118">指定如果在指定期間內沒有備份磁帶可用時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會逾時。</span><span class="sxs-lookup"><span data-stu-id="acd60-118">Specifies that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will time out if a backup tape is not available within the period specified.</span></span>  
  
 <span data-ttu-id="acd60-119">**預設備份媒體保留 (以天為單位)**</span><span class="sxs-lookup"><span data-stu-id="acd60-119">**Default backup media retention (in days)**</span></span>  
 <span data-ttu-id="acd60-120">提供每個備份媒體的全系統保存預設時間長度，設定當備份用於資料庫或交易記錄備份之後，預設要保存多久。</span><span class="sxs-lookup"><span data-stu-id="acd60-120">Provides a system-wide default for the length of time to retain each backup medium after it has been used for a database or transaction log backup.</span></span> <span data-ttu-id="acd60-121">此選項協助保護備份，在指定的天數經過之前不被覆寫。</span><span class="sxs-lookup"><span data-stu-id="acd60-121">This option helps protect backups from being overwritten until the specified number of days has elapsed.</span></span>  
  
 <span data-ttu-id="acd60-122">**壓縮備份**</span><span class="sxs-lookup"><span data-stu-id="acd60-122">**Compress backup**</span></span>  
 <span data-ttu-id="acd60-123">在 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (或更新的版本) 中，表示 [備份壓縮預設] 選項的目前設定。</span><span class="sxs-lookup"><span data-stu-id="acd60-123">In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (or later versions), indicates the current setting of the **backup compression default** option.</span></span> <span data-ttu-id="acd60-124">這一個選項會決定壓縮備份的伺服器層級預設值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="acd60-124">This option determines the server-level default for compressing backups, as follows:</span></span>  
  
-   <span data-ttu-id="acd60-125">如果 **[壓縮備份]** 方塊是空的，新備份預設不會進行壓縮。</span><span class="sxs-lookup"><span data-stu-id="acd60-125">If the **Compress backup** box is blank, new backups are uncompressed by default.</span></span>  
  
-   <span data-ttu-id="acd60-126">如果 **[壓縮備份]** 方塊已核取，新備份預設就會進行壓縮。</span><span class="sxs-lookup"><span data-stu-id="acd60-126">If the **Compress backup** box is checked, new backups are compressed by default.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="acd60-127">根據預設，壓縮會大幅增加 CPU 使用量，而且壓縮程序所耗用的額外 CPU 可能會對並行作業造成不良的影響。</span><span class="sxs-lookup"><span data-stu-id="acd60-127">By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely affect concurrent operations.</span></span> <span data-ttu-id="acd60-128">因此，您可能會想要在由[資源管理員](../../relational-databases/resource-governor/resource-governor.md)所限制之 CPU 使用量的工作階段中建立低優先權的壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="acd60-128">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by [Resource Governor](../../relational-databases/resource-governor/resource-governor.md).</span></span> <span data-ttu-id="acd60-129">如需詳細資訊，請參閱本主題稍後介紹的＜ [使用資源管理員進行備份壓縮，以限制 CPU 使用率 &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)限制的工作階段中，建立低優先權的壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="acd60-129">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../../relational-databases/backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>  
  
 <span data-ttu-id="acd60-130">如果您是 **系統管理員 (sysadmin)** 或 **serveradmin** 固定伺服器角色的成員，您可以透過按一下 [壓縮備份]  方塊，變更設定。</span><span class="sxs-lookup"><span data-stu-id="acd60-130">If you are a member of the **sysadmin** or **serveradmin** fixed server role, you can change the setting by clicking the **Compress backup** box.</span></span>  
  
 <span data-ttu-id="acd60-131">如需詳細資訊，請參閱[檢視或設定 backup compression default 伺服器組態選項](view-or-configure-the-backup-compression-default-server-configuration-option.md)和[備份壓縮 &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="acd60-131">For more information, see [View or Configure the backup compression default Server Configuration Option](view-or-configure-the-backup-compression-default-server-configuration-option.md) and [Backup Compression &#40;SQL Server&#41;](../../relational-databases/backup-restore/backup-compression-sql-server.md).</span></span>  
  
 <span data-ttu-id="acd60-132">**復原間隔 (分鐘)**</span><span class="sxs-lookup"><span data-stu-id="acd60-132">**Recovery interval (minutes)**</span></span>  
 <span data-ttu-id="acd60-133">設定每個資料庫復原的最長時間 (分鐘)。</span><span class="sxs-lookup"><span data-stu-id="acd60-133">Sets the maximum number of minutes per database to recover databases.</span></span> <span data-ttu-id="acd60-134">預設值是 0，指出由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]自動組態。</span><span class="sxs-lookup"><span data-stu-id="acd60-134">The default is 0, indicating automatic configuration by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="acd60-135">實務上，這表示復原時間小於一分鐘，而且使用中資料庫幾乎每分鐘有一次檢查點。</span><span class="sxs-lookup"><span data-stu-id="acd60-135">In practice, this means a recovery time of less than one minute and a checkpoint approximately every one minute for active databases.</span></span> <span data-ttu-id="acd60-136">如需詳細資訊，請參閱 [Configure the recovery interval Server Configuration Option](configure-the-recovery-interval-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="acd60-136">For more information, see [Configure the recovery interval Server Configuration Option](configure-the-recovery-interval-server-configuration-option.md).</span></span>  
  
 <span data-ttu-id="acd60-137">**Data**</span><span class="sxs-lookup"><span data-stu-id="acd60-137">**Data**</span></span>  
 <span data-ttu-id="acd60-138">指定資料檔案的預設位置。</span><span class="sxs-lookup"><span data-stu-id="acd60-138">Specifies the default location for data files.</span></span> <span data-ttu-id="acd60-139">按一下 [瀏覽] 按鈕，即可導覽到新的預設位置。</span><span class="sxs-lookup"><span data-stu-id="acd60-139">Click the browse button to navigate to a new default location.</span></span> <span data-ttu-id="acd60-140">要等到重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之後才會生效。</span><span class="sxs-lookup"><span data-stu-id="acd60-140">Does not take effect until [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
 <span data-ttu-id="acd60-141">**Log**</span><span class="sxs-lookup"><span data-stu-id="acd60-141">**Log**</span></span>  
 <span data-ttu-id="acd60-142">指定記錄檔案的預設位置。</span><span class="sxs-lookup"><span data-stu-id="acd60-142">Specifies the default location for log files.</span></span> <span data-ttu-id="acd60-143">按一下 [瀏覽] 按鈕，即可導覽到新的預設位置。</span><span class="sxs-lookup"><span data-stu-id="acd60-143">Click the browse button to navigate to a new default location.</span></span> <span data-ttu-id="acd60-144">要等到重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 之後才會生效。</span><span class="sxs-lookup"><span data-stu-id="acd60-144">Does not take effect until [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is restarted.</span></span>  
  
 <span data-ttu-id="acd60-145">**設定的值**</span><span class="sxs-lookup"><span data-stu-id="acd60-145">**Configured Values**</span></span>  
 <span data-ttu-id="acd60-146">針對此窗格中的選項，顯示設定的值。</span><span class="sxs-lookup"><span data-stu-id="acd60-146">Displays the configured values for the options on this pane.</span></span> <span data-ttu-id="acd60-147">如果您變更這些值，請按一下 **[執行中的值]** ，即可查看變更是否已生效。</span><span class="sxs-lookup"><span data-stu-id="acd60-147">If you change these values, click **Running Values** to see whether the changes have taken effect.</span></span> <span data-ttu-id="acd60-148">如果沒有的話，就必須先重新啟動 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="acd60-148">If they have not, the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must be restated first.</span></span>  
  
 <span data-ttu-id="acd60-149">**[執行中的值]**</span><span class="sxs-lookup"><span data-stu-id="acd60-149">**Running Values**</span></span>  
 <span data-ttu-id="acd60-150">針對此窗格中的選項，檢視目前執行中的值。</span><span class="sxs-lookup"><span data-stu-id="acd60-150">View the currently running values for the options on this pane.</span></span> <span data-ttu-id="acd60-151">這些值是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="acd60-151">These values are read-only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acd60-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acd60-152">See Also</span></span>  
 <span data-ttu-id="acd60-153">[伺服器組態選項 &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="acd60-153">[Server Configuration Options &#40;SQL Server&#41;](server-configuration-options-sql-server.md) </span></span>  
 [<span data-ttu-id="acd60-154">指定索引的填滿因素</span><span class="sxs-lookup"><span data-stu-id="acd60-154">Specify Fill Factor for an Index</span></span>](../../relational-databases/indexes/specify-fill-factor-for-an-index.md)  
  
  
