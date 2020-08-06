---
title: 記錄傳送交易記錄備份設定 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.databaseproperties.logshipping.settings.tlogback.f1
ms.assetid: 9a6e6c16-7f71-412b-bba6-7bffac001277
author: stevestein
ms.author: sstein
ms.openlocfilehash: b5420f3032cd2477d23028a2e27c1ce89c4e0525
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709542"
---
# <a name="log-shipping-transaction-log-backup-settings"></a><span data-ttu-id="2a75d-102">記錄傳送交易記錄備份設定</span><span class="sxs-lookup"><span data-stu-id="2a75d-102">Log Shipping Transaction Log Backup Settings</span></span>
  <span data-ttu-id="2a75d-103">使用此對話方塊來設定和修改記錄傳送組態的交易記錄備份設定。</span><span class="sxs-lookup"><span data-stu-id="2a75d-103">Use this dialog box to configure and modify the transaction log backup settings for a log shipping configuration.</span></span>  
  
 <span data-ttu-id="2a75d-104">如需記錄傳送概念的說明，請參閱 [關於記錄傳送 &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2a75d-104">For an explanation of log shipping concepts, see [About Log Shipping &#40;SQL Server&#41;](../../database-engine/log-shipping/about-log-shipping-sql-server.md).</span></span>  
  
## <a name="options"></a><span data-ttu-id="2a75d-105">選項。</span><span class="sxs-lookup"><span data-stu-id="2a75d-105">Options</span></span>  
 <span data-ttu-id="2a75d-106">**備份資料夾的網路路徑**</span><span class="sxs-lookup"><span data-stu-id="2a75d-106">**Network path to the backup folder**</span></span>  
 <span data-ttu-id="2a75d-107">在此方塊中輸入備份資料夾的網路共用。</span><span class="sxs-lookup"><span data-stu-id="2a75d-107">Type the network share to your backup folder in this box.</span></span> <span data-ttu-id="2a75d-108">儲存交易記錄備份的本機資料夾必須共用，記錄傳送複製作業才能將這些檔案複製至次要伺服器。</span><span class="sxs-lookup"><span data-stu-id="2a75d-108">The local folder where your transaction log backups are saved must be shared so that the log shipping copy jobs can copy these files to the secondary server.</span></span> <span data-ttu-id="2a75d-109">您必須將此網路共用的讀取權限授與 Proxy 帳戶，在此帳戶下，複製作業將會在次要伺服器執行個體上執行。</span><span class="sxs-lookup"><span data-stu-id="2a75d-109">You must grant read permissions on this network share to the proxy account under which the copy job will run at the secondary server instance.</span></span> <span data-ttu-id="2a75d-110">依預設，這是次要伺服器執行個體的 SQLServerAgent 服務帳戶，但是管理員可以為此作業選擇另一個 Proxy 帳戶。</span><span class="sxs-lookup"><span data-stu-id="2a75d-110">By default, this is the SQLServerAgent service account of the secondary server instance, but an administrator can choose another proxy account for the job.</span></span>  
  
 <span data-ttu-id="2a75d-111">**如果備份資料夾位於主要伺服器上，請輸入該資料夾的本機路徑**</span><span class="sxs-lookup"><span data-stu-id="2a75d-111">**If the backup folder is located on the primary server, type the local path to the folder**</span></span>  
 <span data-ttu-id="2a75d-112">如果備份資料夾位於主要伺服器上，請輸入備份資料夾的本機磁碟機代號和路徑。</span><span class="sxs-lookup"><span data-stu-id="2a75d-112">Type the local drive letter and path to the backup folder if the backup folder is located on the primary server.</span></span> <span data-ttu-id="2a75d-113">如果備份資料夾不在主要伺服器上，您可以讓此欄位保留空白。</span><span class="sxs-lookup"><span data-stu-id="2a75d-113">If the backup folder is not located on the primary server, you can leave this blank.</span></span>  
  
 <span data-ttu-id="2a75d-114">如果您在此指定本機路徑，則 BACKUP 命令將使用此路徑來建立交易記錄備份；否則，如果未指定本機路徑，BACKUP 命令將使用 [備份資料夾的網路路徑]  方塊中所指定的網路路徑。</span><span class="sxs-lookup"><span data-stu-id="2a75d-114">If you specify a local path here, the BACKUP command will use this path to create the transaction log backups; otherwise, if no local path is specified, the BACKUP command will use the network path specified in the **Network path to the backup folder** box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2a75d-115">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶是在主要伺服器的本機系統帳戶之下執行，您就必須在主要伺服器上建立備份資料夾，然後在此指定該資料夾的本機路徑。</span><span class="sxs-lookup"><span data-stu-id="2a75d-115">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account is running under the local system account on the primary server, you must create the backup folder on the primary server and specify the local path to that folder here.</span></span> <span data-ttu-id="2a75d-116">主要伺服器執行個體的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 服務帳戶必須擁有此資料夾的讀取和寫入權限。</span><span class="sxs-lookup"><span data-stu-id="2a75d-116">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] service account of the primary server instance must have Read and Write permissions on this folder.</span></span>  
  
 <span data-ttu-id="2a75d-117">**指定刪除檔案的時限**</span><span class="sxs-lookup"><span data-stu-id="2a75d-117">**Delete files older than**</span></span>  
 <span data-ttu-id="2a75d-118">指定在刪除之前要讓交易記錄備份維持在備份目錄中的時間長度。</span><span class="sxs-lookup"><span data-stu-id="2a75d-118">Specify the length of time you want transaction log backups to remain in your backup directory before being deleted.</span></span>  
  
 <span data-ttu-id="2a75d-119">**如果未在此時間內進行備份，則發出警示**</span><span class="sxs-lookup"><span data-stu-id="2a75d-119">**Alert if no backup occurs within**</span></span>  
 <span data-ttu-id="2a75d-120">指定在引發未發生交易記錄備份的警示之前，您要記錄傳送等候的時間量。</span><span class="sxs-lookup"><span data-stu-id="2a75d-120">Specify the amount of time you want log shipping to wait before raising an alert that no transaction log backups have occurred.</span></span>  
  
 <span data-ttu-id="2a75d-121">**作業名稱**</span><span class="sxs-lookup"><span data-stu-id="2a75d-121">**Job name**</span></span>  
 <span data-ttu-id="2a75d-122">顯示用來建立記錄傳送之交易記錄備份的 SQL Server Agent 作業的名稱。</span><span class="sxs-lookup"><span data-stu-id="2a75d-122">Displays the name of the SQL Server Agent job that is used to create the transaction log backups for log shipping.</span></span> <span data-ttu-id="2a75d-123">首次建立作業時，您可以在此方塊中輸入名稱來修改其名稱。</span><span class="sxs-lookup"><span data-stu-id="2a75d-123">When first creating the job, you can modify the name by typing in the box.</span></span>  
  
 <span data-ttu-id="2a75d-124">**[排程]**</span><span class="sxs-lookup"><span data-stu-id="2a75d-124">**Schedule**</span></span>  
 <span data-ttu-id="2a75d-125">顯示備份主要資料庫之交易記錄的目前排程。</span><span class="sxs-lookup"><span data-stu-id="2a75d-125">Displays the current schedule for backing up the transaction logs of the primary database.</span></span> <span data-ttu-id="2a75d-126">建立備份作業之前，按一下 [排程...]  即可修改此排程。建立備份作業之後，按一下 [編輯作業...]  即可修改此排程。</span><span class="sxs-lookup"><span data-stu-id="2a75d-126">Before the backup job has been created, You can modify this schedule by clicking **Schedule...**. After the job has been created, you can modify this schedule by clicking **Edit Job...**.</span></span>  
  
### <a name="backup-job"></a><span data-ttu-id="2a75d-127">備份作業</span><span class="sxs-lookup"><span data-stu-id="2a75d-127">Backup Job</span></span>  
 <span data-ttu-id="2a75d-128">**[排程...]**</span><span class="sxs-lookup"><span data-stu-id="2a75d-128">**Schedule...**</span></span>  
 <span data-ttu-id="2a75d-129">修改建立 SQL Server Agent 作業時所建立的排程。</span><span class="sxs-lookup"><span data-stu-id="2a75d-129">Modify the schedule that is created when the SQL Server Agent job is created.</span></span>  
  
 <span data-ttu-id="2a75d-130">**編輯作業...**</span><span class="sxs-lookup"><span data-stu-id="2a75d-130">**Edit Job...**</span></span>  
 <span data-ttu-id="2a75d-131">修改在主要資料庫上執行交易記錄備份之作業的 SQL Server Agent 作業參數。</span><span class="sxs-lookup"><span data-stu-id="2a75d-131">Modify the SQL Server Agent job parameters for the job that performs transaction log backups on the primary database.</span></span>  
  
 <span data-ttu-id="2a75d-132">**停用此作業**</span><span class="sxs-lookup"><span data-stu-id="2a75d-132">**Disable this job**</span></span>  
 <span data-ttu-id="2a75d-133">使 SQL Server Agent 作業不能建立交易記錄備份。</span><span class="sxs-lookup"><span data-stu-id="2a75d-133">Disable the SQL Server Agent job from creating transaction log backups.</span></span>  
  
### <a name="compression"></a><span data-ttu-id="2a75d-134">壓縮</span><span class="sxs-lookup"><span data-stu-id="2a75d-134">Compression</span></span>  
 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] <span data-ttu-id="2a75d-135">(或更新版本) 支援 [備份壓縮](../backup-restore/backup-compression-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="2a75d-135">(or a later version) supports [backup compression](../backup-restore/backup-compression-sql-server.md).</span></span>  
  
 <span data-ttu-id="2a75d-136">**設定備份壓縮**</span><span class="sxs-lookup"><span data-stu-id="2a75d-136">**Set backup compression**</span></span>  
 <span data-ttu-id="2a75d-137">在 [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (或更新的版本) 中，針對此記錄傳送設定的記錄備份選取下列其中一個備份壓縮值：</span><span class="sxs-lookup"><span data-stu-id="2a75d-137">In [!INCLUDE[ssEnterpriseEd10](../../includes/ssenterpriseed10-md.md)] (or a later version), select one the following backup compression values for the log backups of this log shipping configuration:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2a75d-138">**使用預設伺服器設定**</span><span class="sxs-lookup"><span data-stu-id="2a75d-138">**Use the default server setting**</span></span>|<span data-ttu-id="2a75d-139">按一下即可使用伺服器層級的預設值。</span><span class="sxs-lookup"><span data-stu-id="2a75d-139">Click to use the server-level default.</span></span><br /><br /> <span data-ttu-id="2a75d-140">此預設值是由 [備份壓縮預設]  伺服器組態選項所設定。</span><span class="sxs-lookup"><span data-stu-id="2a75d-140">This default is set by the **backup compression default** server-configuration option.</span></span> <span data-ttu-id="2a75d-141">有關如何檢視這個選項目前之設定的詳細資訊，請參閱 [檢視或設定備份壓縮預設伺服器組態選項](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md)。</span><span class="sxs-lookup"><span data-stu-id="2a75d-141">For information about how to view the current setting of this option, see [View or Configure the backup compression default Server Configuration Option](../../database-engine/configure-windows/view-or-configure-the-backup-compression-default-server-configuration-option.md).</span></span>|  
|<span data-ttu-id="2a75d-142">**壓縮備份**</span><span class="sxs-lookup"><span data-stu-id="2a75d-142">**Compress backup**</span></span>|<span data-ttu-id="2a75d-143">不論目前的伺服器層級預設值為何，按一下即可壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="2a75d-143">Click to compress the backup, regardless of the server-level default.</span></span><br /><br /> <span data-ttu-id="2a75d-144">**\*\* 重要 \*\*** 根據預設，壓縮會大幅增加 CPU 使用量，而且壓縮程序所耗用的額外 CPU 可能會對並行作業造成不良的影響。</span><span class="sxs-lookup"><span data-stu-id="2a75d-144">**\*\* Important \*\*** By default, compression significantly increases CPU usage, and the additional CPU consumed by the compression process might adversely impact concurrent operations.</span></span> <span data-ttu-id="2a75d-145">因此，您可能會想要在 [資源管理員](../resource-governor/resource-governor.md)限制 CPU 使用量的工作階段中，建立低優先權的壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="2a75d-145">Therefore, you might want to create low-priority compressed backups in a session whose CPU usage is limited by the [Resource Governor](../resource-governor/resource-governor.md).</span></span> <span data-ttu-id="2a75d-146">如需詳細資訊，請參閱本主題稍後介紹的＜ [使用資源管理員進行備份壓縮，以限制 CPU 使用率 &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md)限制的工作階段中，建立低優先權的壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="2a75d-146">For more information, see [Use Resource Governor to Limit CPU Usage by Backup Compression &#40;Transact-SQL&#41;](../backup-restore/use-resource-governor-to-limit-cpu-usage-by-backup-compression-transact-sql.md).</span></span>|  
|<span data-ttu-id="2a75d-147">**不要壓縮備份**</span><span class="sxs-lookup"><span data-stu-id="2a75d-147">**Do not compress backup**</span></span>|<span data-ttu-id="2a75d-148">不論目前的伺服器層級預設值為何，按一下即可建立未壓縮備份。</span><span class="sxs-lookup"><span data-stu-id="2a75d-148">Click to create an uncompressed backup, regardless of the server-level default.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a75d-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a75d-149">See Also</span></span>  
 <span data-ttu-id="2a75d-150">[設定使用者可建立及管理 SQL Server Agent 作業](../../ssms/agent/configure-a-user-to-create-and-manage-sql-server-agent-jobs.md) </span><span class="sxs-lookup"><span data-stu-id="2a75d-150">[Configure a User to Create and Manage SQL Server Agent Jobs](../../ssms/agent/configure-a-user-to-create-and-manage-sql-server-agent-jobs.md) </span></span>  
 [<span data-ttu-id="2a75d-151">關於記錄傳送 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2a75d-151">About Log Shipping &#40;SQL Server&#41;</span></span>](../../database-engine/log-shipping/about-log-shipping-sql-server.md)  
  
  
