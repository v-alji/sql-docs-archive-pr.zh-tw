---
title: 在 AlwaysOn 次要資料庫上啟動資料移動 (SQL Server) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- Availability Groups [SQL Server], databases
ms.assetid: 498eb3fb-6a43-434d-ad95-68a754232c45
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3ce4f80b456244cd6e024377383abe75e002057a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708650"
---
# <a name="start-data-movement-on-an-alwayson-secondary-database-sql-server"></a><span data-ttu-id="d1d63-102">於 AlwaysOn 次要資料庫啟動資料移動 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="d1d63-102">Start Data Movement on an AlwaysOn Secondary Database (SQL Server)</span></span>
  <span data-ttu-id="d1d63-103">此主題描述在將資料庫加入至 AlwaysOn 可用性群組之後如何啟動資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="d1d63-103">This topic contains information about how to start data synchronization after you add a database to an AlwaysOn availability group.</span></span> <span data-ttu-id="d1d63-104">對於每個新的主要複本，必須在裝載次要複本的伺服器執行個體上準備次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="d1d63-104">For each new primary replica, secondary databases must be prepared on the server instances that host the secondary replicas.</span></span> <span data-ttu-id="d1d63-105">然後每個次要資料庫必須手動聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="d1d63-105">Then each of these secondary databases must be manually joined to the availability group.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1d63-106">如果在裝載可用性群組之可用性複本的每個伺服器執行個體上檔案路徑都相同， [[新增可用性群組精靈]](use-the-availability-group-wizard-sql-server-management-studio.md)、 [[將複本加入至可用性群組精靈]](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)或 [[將資料庫加入至可用性群組精靈]](availability-group-add-database-to-group-wizard.md) 可能會自動為您啟動資料同步處理。</span><span class="sxs-lookup"><span data-stu-id="d1d63-106">If the file paths are identical on every server instance that hosts an availability replica for an availability group, the [New Availability Group Wizard](use-the-availability-group-wizard-sql-server-management-studio.md), [Add Replica to Availability Group Wizard](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md), or [Add Database to Availability Group Wizard](availability-group-add-database-to-group-wizard.md) might be able to automatically start data synchronization for you.</span></span>  
  
 <span data-ttu-id="d1d63-107">若要手動啟動資料同步處理，您需要依次連接到裝載此可用性群組之次要複本的每個伺服器執行個體，並完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="d1d63-107">To start data synchronization manually, you need to connect, in turn, to each server instance that is hosting a secondary replica for the availability group and complete the following steps:</span></span>  
  
1.  <span data-ttu-id="d1d63-108">還原每個主要資料庫及其交易記錄的目前備份 (使用 RESTORE WITH NORECOVERY)。</span><span class="sxs-lookup"><span data-stu-id="d1d63-108">Restore current backups of each primary database and its transaction log (using RESTORE WITH NORECOVERY).</span></span> <span data-ttu-id="d1d63-109">您可以使用下列其中一種替代方法：</span><span class="sxs-lookup"><span data-stu-id="d1d63-109">You can use either of the following alternative approaches:</span></span>  
  
    -   <span data-ttu-id="d1d63-110">使用 RESTORE WITH NORECOVERY，手動還原主要資料庫的最近資料庫備份，然後使用 RESTORE WITH NORECOVERY，還原每個後續的記錄備份。</span><span class="sxs-lookup"><span data-stu-id="d1d63-110">Manually restore a recent database backup of the primary database using RESTORE WITH NORECOVERY, and then restore each subsequent log backup using RESTORE WITH NORECOVERY.</span></span> <span data-ttu-id="d1d63-111">在裝載可用性群組之次要複本的每個伺服器執行個體上，執行此還原順序。</span><span class="sxs-lookup"><span data-stu-id="d1d63-111">Perform this restore sequence on every server instance that hosts a secondary replica for the availability group.</span></span>  
  
         <span data-ttu-id="d1d63-112">**如需詳細資訊：**</span><span class="sxs-lookup"><span data-stu-id="d1d63-112">**For more information:**</span></span>  
  
         [<span data-ttu-id="d1d63-113">針對可用性群組手動準備次要資料庫 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d1d63-113">Manually Prepare a Secondary Database for an Availability Group &#40;SQL Server&#41;</span></span>](manually-prepare-a-secondary-database-for-an-availability-group-sql-server.md)  
  
    -   <span data-ttu-id="d1d63-114">如果您要將一個或多個記錄傳送主要資料庫加入至可用性群組，您可能可以從記錄傳送將一個或多個對應的次要資料庫移轉至 AlwaysOn 可用性群組。</span><span class="sxs-lookup"><span data-stu-id="d1d63-114">If you are adding one or more log shipping primary databases to an availability group, you might be able to migrate one or more of the corresponding secondary databases from log shipping to AlwaysOn Availability Groups.</span></span> <span data-ttu-id="d1d63-115">移轉記錄傳送次要資料庫會要求該資料庫使用與主要資料庫相同的資料庫名稱，以及該資料庫位於主控可用性群組之次要複本的伺服器執行個體上。</span><span class="sxs-lookup"><span data-stu-id="d1d63-115">Migrating a log shipping secondary database requires that it use the same database name as the primary database and that it reside on a server instance that is hosting a secondary replica for the availability group.</span></span> <span data-ttu-id="d1d63-116">此外，可用性群組必須設定，才能以主要複本做為備份的優先考量，並且適合用於執行備份 (也就是說，它的備份優先權為 >0)。</span><span class="sxs-lookup"><span data-stu-id="d1d63-116">Furthermore, the availability group must be configured so that the primary replica is preferred for backups and is a candidate for performing backups (that is, that has a backup priority that is >0).</span></span> <span data-ttu-id="d1d63-117">備份作業在主要資料庫上執行之後，您將需要停用備份作業；還原作業在指定的次要資料庫上執行之後，您將需要停用還原作業。</span><span class="sxs-lookup"><span data-stu-id="d1d63-117">Once the backup job has run on the primary database, you will need to disable the backup job, and once the restore job has run on a given secondary database, you will need to disable the restore job.</span></span>  
  
        > [!NOTE]  
        >  <span data-ttu-id="d1d63-118">為可用性群組建立所有次要資料庫之後，如果您想要在次要複本上執行備份，則需要重新設定可用性群組的自動備份喜好設定。</span><span class="sxs-lookup"><span data-stu-id="d1d63-118">After you have created all the secondary databases for the availability group, if you want to perform backups on secondary replicas, you will need to re-configure the automated backup preference of the availability group.</span></span>  
  
         <span data-ttu-id="d1d63-119">**如需詳細資訊：**</span><span class="sxs-lookup"><span data-stu-id="d1d63-119">**For more information:**</span></span>  
  
         [<span data-ttu-id="d1d63-120">從記錄傳送遷移至 AlwaysOn 可用性群組 &#40;SQL Server 的必要條件&#41;</span><span class="sxs-lookup"><span data-stu-id="d1d63-120">Prerequisites for Migrating from Log Shipping to AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](prereqs-migrating-log-shipping-to-always-on-availability-groups.md)  
  
         [<span data-ttu-id="d1d63-121">設定可用性複本的備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d1d63-121">Configure Backup on Availability Replicas &#40;SQL Server&#41;</span></span>](configure-backup-on-availability-replicas-sql-server.md)  
  
2.  <span data-ttu-id="d1d63-122">盡快將每個新備妥的次要資料庫聯結至可用性群組。</span><span class="sxs-lookup"><span data-stu-id="d1d63-122">As soon as possible, join each newly prepared secondary database to the availability group.</span></span>  
  
     <span data-ttu-id="d1d63-123">**如需詳細資訊：**</span><span class="sxs-lookup"><span data-stu-id="d1d63-123">**For more information:**</span></span>  
  
     [<span data-ttu-id="d1d63-124">將次要資料庫聯結至可用性群組 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="d1d63-124">Join a Secondary Database to an Availability Group &#40;SQL Server&#41;</span></span>](join-a-secondary-database-to-an-availability-group-sql-server.md)  
  
##  <a name="related-tasks"></a><a name="LaunchWiz"></a> <span data-ttu-id="d1d63-125">相關工作</span><span class="sxs-lookup"><span data-stu-id="d1d63-125">Related Tasks</span></span>  
  
-   [<span data-ttu-id="d1d63-126">使用新增可用性群組對話方塊 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="d1d63-126">Use the New Availability Group Dialog Box &#40;SQL Server Management Studio&#41;</span></span>](use-the-new-availability-group-dialog-box-sql-server-management-studio.md)  
  
-   <span data-ttu-id="d1d63-127">[使用 [將複本加入可用性群組中精靈] &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)</span><span class="sxs-lookup"><span data-stu-id="d1d63-127">[Use the Add Replica to Availability Group Wizard &#40;SQL Server Management Studio&#41;](use-the-add-replica-to-availability-group-wizard-sql-server-management-studio.md)</span></span>  
  
-   [<span data-ttu-id="d1d63-128">使用將資料庫加入至可用性群組精靈 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="d1d63-128">Use the Add Database to Availability Group Wizard &#40;SQL Server Management Studio&#41;</span></span>](availability-group-add-database-to-group-wizard.md)  
  
## <a name="see-also"></a><span data-ttu-id="d1d63-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1d63-129">See Also</span></span>  
 [<span data-ttu-id="d1d63-130">AlwaysOn 可用性群組 &#40;SQL Server 的總覽&#41;</span><span class="sxs-lookup"><span data-stu-id="d1d63-130">Overview of AlwaysOn Availability Groups &#40;SQL Server&#41;</span></span>](overview-of-always-on-availability-groups-sql-server.md)  
  
  
