---
title: 關於記錄傳送 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- secondary servers [SQL Server]
- log shipping [SQL Server], jobs
- copy jobs [SQL Server]
- primary databases [SQL Server]
- log shipping [SQL Server], monitoring
- log shipping [SQL Server], about log shipping
- alert jobs [SQL Server]
- availability [SQL Server]
- jobs [SQL Server], log shipping
- monitor servers [SQL Server]
- restore jobs [SQL Server]
- log shipping [SQL Server]
- backup jobs [SQL Server]
- primary servers [SQL Server]
ms.assetid: 55da6b94-3a4b-4bae-850f-4bf7f6e918ca
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: cbf36e0ddd94ec0ab0a40a448e50602decfc0645
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698494"
---
# <a name="about-log-shipping-sql-server"></a><span data-ttu-id="89dc6-102">關於記錄傳送 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="89dc6-102">About Log Shipping (SQL Server)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="89dc6-103">記錄傳送可讓您將 *「主要伺服器」* 執行個體上 *「主要資料庫」* 中的交易記錄備份，自動傳送到個別的 *「次要伺服器」* 執行個體上的一個或多個 *「次要資料庫」* 。</span><span class="sxs-lookup"><span data-stu-id="89dc6-103">Log shipping allows you to automatically send transaction log backups from a *primary database* on a *primary server* instance to one or more *secondary databases* on separate *secondary server* instances.</span></span> <span data-ttu-id="89dc6-104">交易記錄備份會個別套用到每一個次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="89dc6-104">The transaction log backups are applied to each of the secondary databases individually.</span></span> <span data-ttu-id="89dc6-105">第三部選擇性的伺服器執行個體，稱為 *「監視伺服器」* ，負責記錄備份和還原作業的記錄與狀態，如果這些作業未依排程進行，還可以選擇性地發出警示。</span><span class="sxs-lookup"><span data-stu-id="89dc6-105">An optional third server instance, known as the *monitor server*, records the history and status of backup and restore operations and, optionally, raises alerts if these operations fail to occur as scheduled.</span></span>  
  
 <span data-ttu-id="89dc6-106">**本主題內容：**</span><span class="sxs-lookup"><span data-stu-id="89dc6-106">**In this Topic:**</span></span>  
  
-   [<span data-ttu-id="89dc6-107">優點</span><span class="sxs-lookup"><span data-stu-id="89dc6-107">Benefits</span></span>](#Benefits)  
  
-   [<span data-ttu-id="89dc6-108">詞彙和定義</span><span class="sxs-lookup"><span data-stu-id="89dc6-108">Terms and Definitions</span></span>](#TermsAndDefinitions)  
  
-   [<span data-ttu-id="89dc6-109">記錄傳送概觀</span><span class="sxs-lookup"><span data-stu-id="89dc6-109">Log Shipping Overview</span></span>](#ComponentsAndConcepts)  
  
-   [<span data-ttu-id="89dc6-110">互通性</span><span class="sxs-lookup"><span data-stu-id="89dc6-110">Interoperability</span></span>](#Interoperability)  
  
-   [<span data-ttu-id="89dc6-111">相關工作</span><span class="sxs-lookup"><span data-stu-id="89dc6-111">Related Tasks</span></span>](#RelatedTasks)  
  
##  <a name="benefits"></a><a name="Benefits"></a> <span data-ttu-id="89dc6-112">優點</span><span class="sxs-lookup"><span data-stu-id="89dc6-112">Benefits</span></span>  
  
-   <span data-ttu-id="89dc6-113">為單一主要資料庫以及一個或多個次要資料庫 (每個資料庫都位於單獨的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]執行個體上) 提供災害復原方案。</span><span class="sxs-lookup"><span data-stu-id="89dc6-113">Provides a disaster-recovery solution for a single primary database and one or more secondary databases, each on a separate instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="89dc6-114">支援對次要資料庫的有限唯讀存取 (在還原作業之間的間隔期間)。</span><span class="sxs-lookup"><span data-stu-id="89dc6-114">Supports limited read-only access to secondary databases (during the interval between restore jobs).</span></span>  
  
-   <span data-ttu-id="89dc6-115">可讓使用者指定在主要伺服器備份主要資料庫的記錄檔之後，延遲多久次要伺服器才必須還原 (套用) 記錄備份。</span><span class="sxs-lookup"><span data-stu-id="89dc6-115">Allows a user-specified delay between when the primary server backs up the log of the primary database and when the secondary servers must restore (apply) the log backup.</span></span> <span data-ttu-id="89dc6-116">長時間的延遲可能會有幫助，例如，當您意外變更了主要資料庫上的資料時。</span><span class="sxs-lookup"><span data-stu-id="89dc6-116">A longer delay can be useful, for example, if data is accidentally changed on the primary database.</span></span> <span data-ttu-id="89dc6-117">如果您很快就注意到這項意外變更，延遲便可讓您在次要資料庫反映變更之前，從次要資料庫擷取尚未變更的資料。</span><span class="sxs-lookup"><span data-stu-id="89dc6-117">If the accidental change is noticed quickly, a delay can let you retrieve still unchanged data from a secondary database before the change is reflected there.</span></span>  
  
##  <a name="terms-and-definitions"></a><a name="TermsAndDefinitions"></a> <span data-ttu-id="89dc6-118">詞彙和定義</span><span class="sxs-lookup"><span data-stu-id="89dc6-118">Terms and Definitions</span></span>  
 <span data-ttu-id="89dc6-119">「主要資料庫」</span><span class="sxs-lookup"><span data-stu-id="89dc6-119">primary server</span></span>  
 <span data-ttu-id="89dc6-120">做為實際執行伺服器的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="89dc6-120">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that is your production server.</span></span>  
  
 <span data-ttu-id="89dc6-121">「主要伺服器」</span><span class="sxs-lookup"><span data-stu-id="89dc6-121">primary database</span></span>  
 <span data-ttu-id="89dc6-122">主要伺服器上的資料庫，也就是您要備份至其他伺服器的資料庫。</span><span class="sxs-lookup"><span data-stu-id="89dc6-122">The database on the primary server that you want to back up to another server.</span></span> <span data-ttu-id="89dc6-123">所有透過 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 進行的記錄傳送組態管理，都是從主要資料庫執行。</span><span class="sxs-lookup"><span data-stu-id="89dc6-123">All administration of the log shipping configuration through [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] is performed from the primary database.</span></span>  
  
 <span data-ttu-id="89dc6-124">「次要資料庫」</span><span class="sxs-lookup"><span data-stu-id="89dc6-124">secondary server</span></span>  
 <span data-ttu-id="89dc6-125">您要在其中保留主要資料庫暖待命副本的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="89dc6-125">The instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] where you want to keep a warm standby copy of your primary database.</span></span>  
  
 <span data-ttu-id="89dc6-126">次要資料庫</span><span class="sxs-lookup"><span data-stu-id="89dc6-126">secondary database</span></span>  
 <span data-ttu-id="89dc6-127">主要資料庫的暖待命副本。</span><span class="sxs-lookup"><span data-stu-id="89dc6-127">The warm standby copy of the primary database.</span></span> <span data-ttu-id="89dc6-128">次要資料庫可以處於 RECOVERING 狀態或 STANDBY 狀態，讓資料庫提供有限的唯讀存取。</span><span class="sxs-lookup"><span data-stu-id="89dc6-128">The secondary database may be in either the RECOVERING state or the STANDBY state, which leaves the database available for limited read-only access.</span></span>  
  
 <span data-ttu-id="89dc6-129">「監視伺服器」</span><span class="sxs-lookup"><span data-stu-id="89dc6-129">monitor server</span></span>  
 <span data-ttu-id="89dc6-130">選擇性的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，可以追蹤記錄傳送的所有詳細資料，包括：</span><span class="sxs-lookup"><span data-stu-id="89dc6-130">An optional instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that tracks all of the details of log shipping, including:</span></span>  
  
-   <span data-ttu-id="89dc6-131">主要資料庫上次備份交易記錄檔的時間。</span><span class="sxs-lookup"><span data-stu-id="89dc6-131">When the transaction log on the primary database was last backed up.</span></span>  
  
-   <span data-ttu-id="89dc6-132">次要伺服器上次複製及還原備份檔案的時間。</span><span class="sxs-lookup"><span data-stu-id="89dc6-132">When the secondary servers last copied and restored the backup files.</span></span>  
  
-   <span data-ttu-id="89dc6-133">任何備份失敗警示的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="89dc6-133">Information about any backup failure alerts.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="89dc6-134">在設定監視伺服器之後，如果未先移除記錄傳送，就無法進行變更。</span><span class="sxs-lookup"><span data-stu-id="89dc6-134">Once the monitor server has been configured, it cannot be changed without removing log shipping first.</span></span>  
  
 <span data-ttu-id="89dc6-135">備份作業 (backup job)</span><span class="sxs-lookup"><span data-stu-id="89dc6-135">backup job</span></span>  
 <span data-ttu-id="89dc6-136">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業，可執行備份作業、將記錄記錄到本機伺服器與監視伺服器上，以及刪除舊的備份檔案與記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="89dc6-136">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that  performs the backup operation, logs history to the local server and the monitor server, and deletes old backup files and history information.</span></span> <span data-ttu-id="89dc6-137">啟用記錄傳送時，「記錄傳送備份」作業類別目錄會在主要伺服器執行個體上建立。</span><span class="sxs-lookup"><span data-stu-id="89dc6-137">When log shipping is enabled, the job category "Log Shipping Backup" is created on the primary server instance.</span></span>  
  
 <span data-ttu-id="89dc6-138">複製作業 (copy job)</span><span class="sxs-lookup"><span data-stu-id="89dc6-138">copy job</span></span>  
 <span data-ttu-id="89dc6-139">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業，可將主要伺服器的備份檔案複製到次要伺服器上可設定的目的地，並在次要伺服器與監視伺服器上記錄記錄。</span><span class="sxs-lookup"><span data-stu-id="89dc6-139">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that copies the backup files from the primary server to a configurable destination on the secondary server and logs history on the secondary server and the monitor server.</span></span> <span data-ttu-id="89dc6-140">在資料庫上啟用記錄傳送時，「記錄傳送複製」作業類別目錄會在每個次要伺服器執行個體的記錄傳送組態中建立。</span><span class="sxs-lookup"><span data-stu-id="89dc6-140">When log shipping is enabled on a database, the job category "Log Shipping Copy" is created on each secondary server in a log shipping configuration.</span></span>  
  
 <span data-ttu-id="89dc6-141">還原作業 (restore job)</span><span class="sxs-lookup"><span data-stu-id="89dc6-141">restore job</span></span>  
 <span data-ttu-id="89dc6-142">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業，可將複製的備份檔案還原到次要資料庫上。</span><span class="sxs-lookup"><span data-stu-id="89dc6-142">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that restores the copied backup files to the secondary databases.</span></span> <span data-ttu-id="89dc6-143">它可將記錄在本機伺服器與監視伺服器上，並刪除舊的檔案與記錄資訊。</span><span class="sxs-lookup"><span data-stu-id="89dc6-143">It logs history on the local server and the monitor server, and deletes old files and old history information.</span></span> <span data-ttu-id="89dc6-144">在資料庫上啟用記錄傳送時，「記錄傳送還原」作業類別目錄會在次要伺服器執行個體上建立。</span><span class="sxs-lookup"><span data-stu-id="89dc6-144">When log shipping is enabled on a database, the job category "Log Shipping Restore" is created on the secondary server instance.</span></span>  
  
 <span data-ttu-id="89dc6-145">警示作業 (alert job)</span><span class="sxs-lookup"><span data-stu-id="89dc6-145">alert job</span></span>  
 <span data-ttu-id="89dc6-146">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業，若備份或還原作業未在指定臨界值內順利完成，此作業就會為主要及次要資料庫發出警示。</span><span class="sxs-lookup"><span data-stu-id="89dc6-146">A [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent job that raises alerts for primary and secondary databases when a backup or restore operation does not complete successfully within a specified threshold.</span></span> <span data-ttu-id="89dc6-147">在資料庫上啟用記錄傳送時，「記錄傳送警示」作業類別目錄會在監視伺服器執行個體上建立。</span><span class="sxs-lookup"><span data-stu-id="89dc6-147">When log shipping is enabled on a database, job category "Log Shipping Alert" is created on the monitor server instance.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="89dc6-148">對於每個警示，您需要指定警示編號。</span><span class="sxs-lookup"><span data-stu-id="89dc6-148">For each alert, you need to specify an alert number.</span></span> <span data-ttu-id="89dc6-149">此外，請務必設定警示，以便在引發警示時通知操作員。</span><span class="sxs-lookup"><span data-stu-id="89dc6-149">Also, be sure to configure the alert to notify an operator when an alert is raised.</span></span>  
  
##  <a name="log-shipping-overview"></a><a name="ComponentsAndConcepts"></a> <span data-ttu-id="89dc6-150">記錄傳送概觀</span><span class="sxs-lookup"><span data-stu-id="89dc6-150">Log Shipping Overview</span></span>  
 <span data-ttu-id="89dc6-151">記錄傳送由三項作業組成：</span><span class="sxs-lookup"><span data-stu-id="89dc6-151">Log shipping consists of three operations:</span></span>  
  
1.  <span data-ttu-id="89dc6-152">在主要伺服器執行個體上備份交易記錄檔。</span><span class="sxs-lookup"><span data-stu-id="89dc6-152">Back up the transaction log at the primary server instance.</span></span>  
  
2.  <span data-ttu-id="89dc6-153">將交易記錄檔複製到次要伺服器執行個體上。</span><span class="sxs-lookup"><span data-stu-id="89dc6-153">Copy the transaction log file to the secondary server instance.</span></span>  
  
3.  <span data-ttu-id="89dc6-154">在次要伺服器執行個體上還原記錄備份。</span><span class="sxs-lookup"><span data-stu-id="89dc6-154">Restore the log backup on the secondary server instance.</span></span>  
  
 <span data-ttu-id="89dc6-155">記錄可傳送到多個次要伺服器執行個體上。</span><span class="sxs-lookup"><span data-stu-id="89dc6-155">The log can be shipped to multiple secondary server instances.</span></span> <span data-ttu-id="89dc6-156">在此情況下，會為每個次要伺服器執行個體重複執行作業 2 與作業 3。</span><span class="sxs-lookup"><span data-stu-id="89dc6-156">In such cases, operations 2 and 3 are duplicated for each secondary server instance.</span></span>  
  
 <span data-ttu-id="89dc6-157">記錄傳送組態不會自動從主要伺服器容錯移轉到次要伺服器，</span><span class="sxs-lookup"><span data-stu-id="89dc6-157">A log shipping configuration does not automatically fail over from the primary server to the secondary server.</span></span> <span data-ttu-id="89dc6-158">若主要資料庫無法使用，您可以手動將任何次要資料庫連上線。</span><span class="sxs-lookup"><span data-stu-id="89dc6-158">If the primary database becomes unavailable, any of the secondary databases can be brought online manually.</span></span>  
  
 <span data-ttu-id="89dc6-159">您可以將次要資料庫做為報表用途。</span><span class="sxs-lookup"><span data-stu-id="89dc6-159">You can use a secondary database for reporting purposes.</span></span>  
  
 <span data-ttu-id="89dc6-160">此外，您可以在記錄傳送組態中設定警示。</span><span class="sxs-lookup"><span data-stu-id="89dc6-160">In addition, you can configure alerts for your log shipping configuration.</span></span>  
  
### <a name="a-typical-log-shipping-configuration"></a><span data-ttu-id="89dc6-161">典型記錄傳送組態</span><span class="sxs-lookup"><span data-stu-id="89dc6-161">A Typical Log Shipping Configuration</span></span>  
 <span data-ttu-id="89dc6-162">下圖顯示的記錄傳送組態含有主要伺服器執行個體、三個次要伺服器執行個體和一個監視伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="89dc6-162">The following figure shows a log shipping configuration with the primary server instance, three secondary server instances, and a monitor server instance.</span></span> <span data-ttu-id="89dc6-163">此圖說明備份、複製和還原作業執行的步驟，如下所示：</span><span class="sxs-lookup"><span data-stu-id="89dc6-163">The figure illustrates the steps performed by backup, copy, and restorejobs, as follows:</span></span>  
  
1.  <span data-ttu-id="89dc6-164">主要伺服器執行個體執行備份作業來備份主要資料庫上的交易記錄。</span><span class="sxs-lookup"><span data-stu-id="89dc6-164">The primary server instance runs the backup job to back up the transaction log on the primary database.</span></span> <span data-ttu-id="89dc6-165">此伺服器執行個體將記錄備份放在主要記錄備份檔中，再將它傳送到備份資料夾。</span><span class="sxs-lookup"><span data-stu-id="89dc6-165">This server instance then places the log backup into a primary log-backup file, which it sends to the backup folder.</span></span>  <span data-ttu-id="89dc6-166">在此圖中，備份資料夾位於共用目錄，亦即「備份共用」。</span><span class="sxs-lookup"><span data-stu-id="89dc6-166">In this figure, the backup folder is on a shared directory-the *backup share*.</span></span>  
  
2.  <span data-ttu-id="89dc6-167">三個次要伺服器執行個體的每一個都執行它自己的複製作業，將主要記錄備份檔複製到它自己的本機目的資料夾。</span><span class="sxs-lookup"><span data-stu-id="89dc6-167">Each of the three secondary server instances runs its own copy job to copy the primary log-backup file to its own local destination folder.</span></span>  
  
3.  <span data-ttu-id="89dc6-168">每一個次要伺服器執行個體執行它自己的還原作業，將本機目的資料夾的記錄備份還原到本機次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="89dc6-168">Each secondary server instance runs its own restore job to restore the log backup from the local destination folder onto the local secondary database.</span></span>  
  
 <span data-ttu-id="89dc6-169">主要和次要伺服器執行個體傳送其記錄和狀態至監視伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="89dc6-169">The primary and secondary server instances send their own history and status to the monitor server instance.</span></span>  
  
 <span data-ttu-id="89dc6-170">![顯示備份、複製與還原作業的組態](../media/ls-typical-configuration.gif "顯示備份、複製與還原作業的組態")</span><span class="sxs-lookup"><span data-stu-id="89dc6-170">![Configuration showing backup, copy, & restore jobs](../media/ls-typical-configuration.gif "Configuration showing backup, copy, & restore jobs")</span></span>  
  
##  <a name="interoperability"></a><a name="Interoperability"></a> <span data-ttu-id="89dc6-171">互通性</span><span class="sxs-lookup"><span data-stu-id="89dc6-171">Interoperability</span></span>  
 <span data-ttu-id="89dc6-172">記錄傳送只能與 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的下列功能或元件搭配使用：</span><span class="sxs-lookup"><span data-stu-id="89dc6-172">Log shipping can be used with the following features or components of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]:</span></span>  
  
-   [<span data-ttu-id="89dc6-173">從記錄傳送遷移至 AlwaysOn 可用性群組 &#40;SQL Server 的必要條件&#41;</span><span class="sxs-lookup"><span data-stu-id="89dc6-173">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](../availability-groups/windows/prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
-   [<span data-ttu-id="89dc6-174">資料庫鏡像和記錄傳送 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89dc6-174">Database Mirroring and Log Shipping &#40;SQL Server&#41;</span></span>](../database-mirroring/database-mirroring-and-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="89dc6-175">記錄傳送和複寫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89dc6-175">Log Shipping and Replication &#40;SQL Server&#41;</span></span>](log-shipping-and-replication-sql-server.md)  
  
> [!NOTE]  
>  [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] <span data-ttu-id="89dc6-176">和資料庫鏡像互斥。</span><span class="sxs-lookup"><span data-stu-id="89dc6-176">and database mirroring are mutually exclusive.</span></span> <span data-ttu-id="89dc6-177">資料庫已設定其中一項功能後，便不能設定另一項功能。</span><span class="sxs-lookup"><span data-stu-id="89dc6-177">A database that is configured for one of these features cannot be configured for the other.</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="89dc6-178">相關工作</span><span class="sxs-lookup"><span data-stu-id="89dc6-178">Related Tasks</span></span>  
  
-   [<span data-ttu-id="89dc6-179">將記錄傳送升級至 SQL Server 2014 &#40;Transact-sql&#41;</span><span class="sxs-lookup"><span data-stu-id="89dc6-179">Upgrade Log Shipping to SQL Server 2014 &#40;Transact-SQL&#41;</span></span>](upgrading-log-shipping-to-sql-server-2016-transact-sql.md)  
  
-   [<span data-ttu-id="89dc6-180">設定記錄傳送 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89dc6-180">Configure Log Shipping &#40;SQL Server&#41;</span></span>](configure-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="89dc6-181">將次要資料庫加入至記錄傳送組態 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89dc6-181">Add a Secondary Database to a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](add-a-secondary-database-to-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="89dc6-182">從記錄傳送組態中移除次要資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89dc6-182">Remove a Secondary Database from a Log Shipping Configuration &#40;SQL Server&#41;</span></span>](remove-a-secondary-database-from-a-log-shipping-configuration-sql-server.md)  
  
-   [<span data-ttu-id="89dc6-183">移除記錄傳送 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89dc6-183">Remove Log Shipping &#40;SQL Server&#41;</span></span>](remove-log-shipping-sql-server.md)  
  
-   [<span data-ttu-id="89dc6-184">檢視記錄傳送報表 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="89dc6-184">View the Log Shipping Report &#40;SQL Server Management Studio&#41;</span></span>](view-the-log-shipping-report-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="89dc6-185">監視記錄傳送 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="89dc6-185">Monitor Log Shipping &#40;Transact-SQL&#41;</span></span>](monitor-log-shipping-transact-sql.md)  
  
-   [<span data-ttu-id="89dc6-186">容錯移轉至記錄傳送次要 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89dc6-186">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [<span data-ttu-id="89dc6-187">容錯移轉至記錄傳送次要 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89dc6-187">Fail Over to a Log Shipping Secondary &#40;SQL Server&#41;</span></span>](fail-over-to-a-log-shipping-secondary-sql-server.md)  
  
-   [<span data-ttu-id="89dc6-188">角色切換後針對登入和作業進行管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="89dc6-188">Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;</span></span>](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="89dc6-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="89dc6-189">See Also</span></span>  
 [<span data-ttu-id="89dc6-190">AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;</span><span class="sxs-lookup"><span data-stu-id="89dc6-190">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](../availability-groups/windows/overview-of-always-on-availability-groups-sql-server.md)  
  
  
