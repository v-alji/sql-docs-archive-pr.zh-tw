---
title: 選取 [初始資料同步處理] 頁面 (AlwaysOn 可用性群組嚮導) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
f1_keywords:
- sql12.swb.addreplicawizard.selectinitialdatasync.f1
- sql12.swb.adddatabasewizard.selectinitialdatasync.f1
- sql12.swb.newagwizard.selectinitialdatasync.f1
ms.assetid: 457b1140-4819-4def-8f7c-54a406e6db12
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 20f7d8fbe6f885136e030c80719f2e16d1c689f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707886"
---
# <a name="select-initial-data-synchronization-page-alwayson-availability-group-wizards"></a><span data-ttu-id="745c9-102">選取初始資料同步處理頁面 (AlwaysOn 可用性群組精靈)</span><span class="sxs-lookup"><span data-stu-id="745c9-102">Select Initial Data Synchronization Page (AlwaysOn Availability Group Wizards)</span></span>
  <span data-ttu-id="745c9-103">使用 AlwaysOn **[選取初始資料同步處理]** 頁面，指定新次要資料庫之初始資料同步處理的喜好設定。</span><span class="sxs-lookup"><span data-stu-id="745c9-103">Use the AlwaysOn **Select Initial Data Synchronization** page to indicate your preference for initial data synchronization of new secondary databases.</span></span> <span data-ttu-id="745c9-104">此頁面由三個精靈所共用：[!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)]、[!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)] 和 [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="745c9-104">This page is shared by three wizards-the [!INCLUDE[ssAoNewAgWiz](../../../includes/ssaonewagwiz-md.md)], the [!INCLUDE[ssAoAddRepWiz](../../../includes/ssaoaddrepwiz-md.md)], and the [!INCLUDE[ssAoAddDbWiz](../../../includes/ssaoadddbwiz-md.md)].</span></span>  
  
 <span data-ttu-id="745c9-105">可能的選項包含 **[完整]**、 **[僅聯結]** 或 **[略過初始資料同步處理]**。</span><span class="sxs-lookup"><span data-stu-id="745c9-105">The possible choices include **Full**, **Join only**, or **Skip initial data synchronization**.</span></span> <span data-ttu-id="745c9-106">選取 **[完整]** 或 **[僅聯結]** 之前，請確認您的環境符合必要條件。</span><span class="sxs-lookup"><span data-stu-id="745c9-106">Before you select **Full** or **Join only** ensure that your environment meets the prerequisites.</span></span>  
  

  
##  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="745c9-107">建議</span><span class="sxs-lookup"><span data-stu-id="745c9-107">Recommendations</span></span>  
  
-   <span data-ttu-id="745c9-108">在初始資料同步處理期間，暫停主要資料庫的記錄備份工作。</span><span class="sxs-lookup"><span data-stu-id="745c9-108">Suspend log backup tasks for the primary databases during initial data synchronization.</span></span>  
  
-   <span data-ttu-id="745c9-109">大型資料庫的完整備份與還原作業可能需要大量的時間及資源。</span><span class="sxs-lookup"><span data-stu-id="745c9-109">For large database, full backup and restore operations can take extensive time and resources.</span></span> <span data-ttu-id="745c9-110">在此情況下，建議您自行準備次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="745c9-110">In such cases, we recommend that you prepare secondary databases yourself.</span></span> <span data-ttu-id="745c9-111">如需詳細資訊，請參閱本主題稍後的 [手動準備次要資料庫](#PrepareSecondaryDbs)。</span><span class="sxs-lookup"><span data-stu-id="745c9-111">For more information, see [To Prepare Secondary Databases Manually](#PrepareSecondaryDbs), later in this topic.</span></span>  
  
-   <span data-ttu-id="745c9-112">完整初始資料同步處理需要指定網路共用。</span><span class="sxs-lookup"><span data-stu-id="745c9-112">Full initial data synchronization requires you to specify a network share.</span></span> <span data-ttu-id="745c9-113">建議您先對網路共用資料夾的存取權限實作安全性計畫，然後使用精靈執行完整初始資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="745c9-113">Before you use a wizard to perform full initial data synchronization, we recommend that you implement a security plan for the access permissions on the network share folder.</span></span> <span data-ttu-id="745c9-114">此預防措施很重要，因為有此資料夾 READ 權限的任何人都可以存取備份檔案中的潛在敏感性資料。</span><span class="sxs-lookup"><span data-stu-id="745c9-114">This precaution is important because potentially sensitive data in the backup file can be accessed by anyone who has a READ permission on the folder.</span></span> <span data-ttu-id="745c9-115">此外，為了保護您的備份和還原作業，建議您對裝載可用性複本的每個伺服器執行個體與網路共用資料夾之間的網路通道進行保全。</span><span class="sxs-lookup"><span data-stu-id="745c9-115">Also, to protect your backup and restore operations, we recommend that you secure the network channels between every server instance that hosts an availability replica and the network share folder.</span></span>  
  
     <span data-ttu-id="745c9-116">如果備份和還原作業必須是高度保全，建議您選取 **[僅聯結]** 或 **[略過初始資料同步處理]** 選項。</span><span class="sxs-lookup"><span data-stu-id="745c9-116">If your backup and restore operations must be highly secured, we recommend that you select either the **Join only** or **Skip initial data synchronization** option.</span></span>  
  
##  <a name="full"></a><a name="Full"></a><span data-ttu-id="745c9-117">寫</span><span class="sxs-lookup"><span data-stu-id="745c9-117">Full</span></span>  
 <span data-ttu-id="745c9-118">**[完整]** 選項會在一個工作流程中，對每一個主要資料庫執行數項作業，包括建立主要資料庫的完整和記錄備份；透過還原裝載次要複本之每個伺服器執行個體上的這些備份，建立對應的次要資料庫；以及將每個次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="745c9-118">For each primary database, the **Full** option performs several operations in one workflow:  create a full and log backup of the primary database, create the corresponding secondary databases by restoring these backups on every server instance that is hosting a secondary replica, and join each secondary database to availability group.</span></span>  
  
 <span data-ttu-id="745c9-119">只有在環境符合下列使用完整初始資料同步處理的必要條件，且您要精靈自動啟動資料同步處理時，才選取此選項。</span><span class="sxs-lookup"><span data-stu-id="745c9-119">Select this option only if your environment meets the following prerequisites for using full initial data synchronization, and you want the wizard to automatically start data synchronization.</span></span>  
  
 <span data-ttu-id="745c9-120">**使用完整初始資料同步處理的必要條件**</span><span class="sxs-lookup"><span data-stu-id="745c9-120">**Prerequisites for using full initial data synchronization**</span></span>  
  
-   <span data-ttu-id="745c9-121">每個裝載可用性群組複本之伺服器執行個體上的所有資料庫檔案路徑均須相同。</span><span class="sxs-lookup"><span data-stu-id="745c9-121">All the database-file paths must be identical on every server instance that hosts a replica for the availability group.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="745c9-122">若執行精靈所在的伺服器執行個體與要裝載次要複本之伺服器執行個體間的備份和還原檔案路徑不同。</span><span class="sxs-lookup"><span data-stu-id="745c9-122">If the backup and restore file paths differ between the server instance where you run the wizard and any server instance that is to host a secondary replica.</span></span> <span data-ttu-id="745c9-123">備份和還原作業必須手動使用 WITH MOVE 選項執行。</span><span class="sxs-lookup"><span data-stu-id="745c9-123">The backup and restore operations must be performed manually using the WITH MOVE option.</span></span> <span data-ttu-id="745c9-124">如需詳細資訊，請參閱本主題稍後的 [手動準備次要資料庫](#PrepareSecondaryDbs)。</span><span class="sxs-lookup"><span data-stu-id="745c9-124">For more information, see [To Prepare Secondary Databases Manually](#PrepareSecondaryDbs), later in this topic.</span></span>  
  
-   <span data-ttu-id="745c9-125">任何裝載次要複本的伺服器執行個體上皆不應存在主要資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="745c9-125">No primary database name can exist on any server instance that hosts a secondary replica.</span></span> <span data-ttu-id="745c9-126">這表示目前還不可有任何新次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="745c9-126">This means that none of the new secondary databases can exist yet.</span></span>  
  
-   <span data-ttu-id="745c9-127">您必須指定網路共用，精靈才能建立及存取備份。</span><span class="sxs-lookup"><span data-stu-id="745c9-127">You will need to specify a network share in order for the wizard to create and access backups.</span></span> <span data-ttu-id="745c9-128">對於主要複本，用於啟動 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的帳戶必須具有網路共用的讀取與寫入檔案系統權限。</span><span class="sxs-lookup"><span data-stu-id="745c9-128">For the primary replica, the account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] must have read and write file-system permissions on a network share.</span></span> <span data-ttu-id="745c9-129">如果是次要複本，此帳戶必須有網路共用的讀取權限。</span><span class="sxs-lookup"><span data-stu-id="745c9-129">For secondary replicas, the account must have read permission on the network share.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="745c9-130">記錄備份將是記錄備份鏈結的一部分。</span><span class="sxs-lookup"><span data-stu-id="745c9-130">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="745c9-131">請適當地儲存記錄備份檔案。</span><span class="sxs-lookup"><span data-stu-id="745c9-131">Store the log backup files appropriately.</span></span>  
  
 <span data-ttu-id="745c9-132">**若不符合必要條件**</span><span class="sxs-lookup"><span data-stu-id="745c9-132">**If prerequisites are not met**</span></span>  
  
 <span data-ttu-id="745c9-133">精靈將無法建立此可用性群組的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="745c9-133">The wizard cannot create the secondary databases for this availability group.</span></span> <span data-ttu-id="745c9-134">如需有關如何準備的詳細資訊，請參閱本主題稍後的 [手動準備次要資料庫](#PrepareSecondaryDbs)。</span><span class="sxs-lookup"><span data-stu-id="745c9-134">For information on how to prepare them, see [To Prepare Secondary Databases Manually](#PrepareSecondaryDbs), later in this topic.</span></span>  
  
 <span data-ttu-id="745c9-135">**若符合必要條件**</span><span class="sxs-lookup"><span data-stu-id="745c9-135">**If prerequisites are met**</span></span>  
  
 <span data-ttu-id="745c9-136">若符合所有必要條件，且您要精靈執行完整初始資料同步處理，請選取 **[完整]** 選項，並指定網路共用。</span><span class="sxs-lookup"><span data-stu-id="745c9-136">If these prerequisites are all met and you want the wizard to perform full initial data synchronization, select the **Full** option and specify a network share.</span></span> <span data-ttu-id="745c9-137">如此一來，精靈即會建立完整的資料庫及每個選定資料庫的記錄備份，並將這些備份置於您指定的網路共用。</span><span class="sxs-lookup"><span data-stu-id="745c9-137">This will cause  the wizard to create full database and log backups of every selected database and to place these backups on the network share that you specify.</span></span> <span data-ttu-id="745c9-138">然後，在裝載其中一個新次要複本的每個伺服器執行個體上，精靈會透過使用 RESTORE WITH NORECOVERY 還原備份來建立次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="745c9-138">Then, on every server instance that hosts one of the new secondary replicas, the wizard will create the secondary databases by restoring backups using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="745c9-139">建立每個次要資料庫之後，精靈會將新次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="745c9-139">After creating each of the secondary databases, the wizard will join the new secondary database to the availability group.</span></span> <span data-ttu-id="745c9-140">聯結次要資料庫之後，立即會在該資料庫上啟動資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="745c9-140">As soon as a secondary database is joined, data synchronizations starts on that database.</span></span>  
  
 <span data-ttu-id="745c9-141">**指定所有複本可存取的共用網路位置**</span><span class="sxs-lookup"><span data-stu-id="745c9-141">**Specify a shared network location accessible by all replicas**</span></span>  
 <span data-ttu-id="745c9-142">若要建立及還原備份，精靈會要求您指定網路共用。</span><span class="sxs-lookup"><span data-stu-id="745c9-142">To create and restore backups, the wizard requires that you specify a network share.</span></span> <span data-ttu-id="745c9-143">在將裝載可用性複本的每個伺服器執行個體上，用來啟動 [!INCLUDE[ssDE](../../../includes/ssde-md.md)] 的帳戶必須有網路共用的讀取與寫入檔案系統權限。</span><span class="sxs-lookup"><span data-stu-id="745c9-143">The account used to start the [!INCLUDE[ssDE](../../../includes/ssde-md.md)] on each server instance that will host an availability replica must have read and write file-system permissions on the network share.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="745c9-144">記錄備份將是記錄備份鏈結的一部分。</span><span class="sxs-lookup"><span data-stu-id="745c9-144">The log backups will be part of your log backup chain.</span></span> <span data-ttu-id="745c9-145">請適當地儲存它們的備份檔案。</span><span class="sxs-lookup"><span data-stu-id="745c9-145">Store their backup files appropriately.</span></span>  
  
##  <a name="join-only"></a><a name="Joinonly"></a><span data-ttu-id="745c9-146">僅聯結</span><span class="sxs-lookup"><span data-stu-id="745c9-146">Join only</span></span>  
 <span data-ttu-id="745c9-147">只有在裝載可用性群組之次要複本的每個伺服器執行個體上已經有新次要資料庫時，才選取此選項。</span><span class="sxs-lookup"><span data-stu-id="745c9-147">Select this option only if the new secondary databases already exist on each server instance that hosts a secondary replica for the availability group.</span></span> <span data-ttu-id="745c9-148">如需有關準備次要資料庫的詳細資訊，請參閱本節稍後的 [手動準備次要資料庫](#PrepareSecondaryDbs)。</span><span class="sxs-lookup"><span data-stu-id="745c9-148">For information about preparing secondary databases, see [To Prepare Secondary Databases Manually](#PrepareSecondaryDbs), later in this section.</span></span>  
  
 <span data-ttu-id="745c9-149">如果您選取 **[僅聯結]**，精靈會嘗試將每個現有的次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="745c9-149">If you select **Join only**, the wizard will attempt to join each existing secondary database to the availability group.</span></span>  
  
## <a name="skip-initial-data-synchronization"></a><span data-ttu-id="745c9-150">略過初始資料同步處理</span><span class="sxs-lookup"><span data-stu-id="745c9-150">Skip initial data synchronization</span></span>  
 <span data-ttu-id="745c9-151">只有在您要對每個主要資料庫執行您自己的資料庫和記錄備份、將它們手動還原到裝載次要複本的每個伺服器執行個體時，才選取此選項。</span><span class="sxs-lookup"><span data-stu-id="745c9-151">Select this option if you want to perform your own database and log backups of every primary database, restore them to every server instance that hosts a secondary replica.</span></span> <span data-ttu-id="745c9-152">結束精靈之後，您需要聯結每個次要複本上的每個次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="745c9-152">After you exit the wizard, you will then need to join every secondary database on every secondary replica.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="745c9-153">如需詳細資訊，請參閱[於 AlwaysOn 次要資料庫啟動資料移動 &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="745c9-153">For more information, see [Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;](start-data-movement-on-an-always-on-secondary-database-sql-server.md).</span></span>  
  
##  <a name="to-prepare-secondary-databases-manually"></a><a name="PrepareSecondaryDbs"></a><span data-ttu-id="745c9-154">手動準備次要資料庫</span><span class="sxs-lookup"><span data-stu-id="745c9-154">To Prepare Secondary Databases Manually</span></span>  
 <span data-ttu-id="745c9-155">若要在任何 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] 精靈之外獨立準備次要資料庫，可以使用下列方法之一：</span><span class="sxs-lookup"><span data-stu-id="745c9-155">To prepare secondary databases independently of any [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)] wizard, you can use either of the following approaches:</span></span>  
  
-   <span data-ttu-id="745c9-156">使用 RESTORE WITH NORECOVERY，手動還原主要資料庫的最近資料庫備份，然後使用 RESTORE WITH NORECOVERY，還原每個後續的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="745c9-156">Manually restore a recent database backup of the primary database using RESTORE WITH NORECOVERY, and then restore each subsequent log backup using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="745c9-157">若主要與次要資料庫的檔案路徑不同，必須使用 WITH MOVE 選項。</span><span class="sxs-lookup"><span data-stu-id="745c9-157">If the primary and secondary databases have different file paths, you must use the WITH MOVE option.</span></span> <span data-ttu-id="745c9-158">在裝載可用性群組之次要複本的每個伺服器執行個體上，執行此還原順序。</span><span class="sxs-lookup"><span data-stu-id="745c9-158">Perform this restore sequence on every server instance that hosts a secondary replica for the availability group.</span></span>  <span data-ttu-id="745c9-159">您可以使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 或 PowerShell 執行這些備份和還原作業。</span><span class="sxs-lookup"><span data-stu-id="745c9-159">You can use [!INCLUDE[tsql](../../../includes/tsql-md.md)] or PowerShell to perform these backup and restore operations.</span></span>  
  
     <span data-ttu-id="745c9-160">**如需詳細資訊：**</span><span class="sxs-lookup"><span data-stu-id="745c9-160">**For more information:**</span></span>  
  
     [<span data-ttu-id="745c9-161">針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="745c9-161">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
-   <span data-ttu-id="745c9-162">若要將一個或多個記錄傳送主要資料庫加入可用性群組，或可從記錄傳送將一個或多個對應的次要資料庫移轉至 [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="745c9-162">If you are adding one or more log shipping primary databases to an availability group, you might be able to migrate one or more of the corresponding secondary databases from log shipping to [!INCLUDE[ssHADR](../../../includes/sshadr-md.md)].</span></span> <span data-ttu-id="745c9-163">如需詳細資訊，請參閱[從記錄傳送遷移至 AlwaysOn 可用性群組 &#40;SQL Server&#41;的必要條件](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)。</span><span class="sxs-lookup"><span data-stu-id="745c9-163">For more information, see [Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;](prereqs-migrating-log-shipping-to-always-on-availability-groups.md).</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="745c9-164">為可用性群組建立所有次要資料庫之後，如果您想要在次要複本上執行備份，則需要重新設定可用性群組的自動備份喜好設定。</span><span class="sxs-lookup"><span data-stu-id="745c9-164">After you have created all the secondary databases for the availability group, if you want to perform backups on secondary replicas, you will need to re-configure the automated backup preference of the availability group.</span></span>  
  
     <span data-ttu-id="745c9-165">**如需詳細資訊：**</span><span class="sxs-lookup"><span data-stu-id="745c9-165">**For more information:**</span></span>  
  
     [<span data-ttu-id="745c9-166">從記錄傳送遷移至 AlwaysOn 可用性群組 &#40;SQL Server 的必要條件&#41;</span><span class="sxs-lookup"><span data-stu-id="745c9-166">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
     [<span data-ttu-id="745c9-167">設定可用性複本的備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="745c9-167">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
 <span data-ttu-id="745c9-168">建立次要資料庫之後，將所有目前的記錄備份套用至新的次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="745c9-168">After creating a secondary database, apply all current log backups to the new secondary database.</span></span>  
  
 <span data-ttu-id="745c9-169">您也可選擇在執行精靈之前，先準備所有次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="745c9-169">Optionally, you can prepare all the secondary databases before you run the wizard.</span></span> <span data-ttu-id="745c9-170">然後在精靈的 **[指定初始資料同步處理]** 頁面上選取 **[僅聯結]** ，以自動將新的次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="745c9-170">Then, on the wizard's **Specify Initial Data Synchronization** page, select **Join only** to automatically join your new secondary databases to the availability group.</span></span>  
  
##  <a name="related-tasks"></a><a name="LaunchWiz"></a> <span data-ttu-id="745c9-171">相關工作</span><span class="sxs-lookup"><span data-stu-id="745c9-171">Related Tasks</span></span>  
  
-   [<span data-ttu-id="745c9-172">使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="745c9-172">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   <span data-ttu-id="745c9-173">[使用 [將複本加入可用性群組中精靈] &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="745c9-173">[Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="745c9-174">使用將資料庫加入至可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="745c9-174">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
-   [<span data-ttu-id="745c9-175">使用容錯移轉可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="745c9-175">Use the Fail Over Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](use-the-fail-over-availability-group-wizard-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="745c9-176">在 AlwaysOn 次要資料庫上啟動資料移動 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="745c9-176">Start Data Movement on an AlwaysOn Secondary Database &#40;SQL Server&#41;</span></span>](start-data-movement-on-an-always-on-secondary-database-sql-server.md)  
  
-   [<span data-ttu-id="745c9-177">將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="745c9-177">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
-   [<span data-ttu-id="745c9-178">使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="745c9-178">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
## <a name="see-also"></a><span data-ttu-id="745c9-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="745c9-179">See Also</span></span>  
 [<span data-ttu-id="745c9-180">AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;</span><span class="sxs-lookup"><span data-stu-id="745c9-180">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
