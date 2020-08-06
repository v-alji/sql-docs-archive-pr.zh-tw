---
title: 備份及還原複寫的資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- backups [SQL Server replication]
- administering replication, restoring
- backing up replicated databases
- backups [SQL Server replication], about backups
- restoring replicated databases [SQL Server replication]
- recovery [SQL Server replication], about recovery
- restoring databases [SQL Server], replicated databases
- backing up databases [SQL Server], replicated databases
- restoring [SQL Server replication], about restoring
- recovery [SQL Server replication]
- replication [SQL Server], administering
- distribution databases [SQL Server replication], backing up
- restoring [SQL Server replication]
- administering replication, backing up
ms.assetid: 04588807-21e7-4bbe-9727-b72f692cffa7
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e91505bacf67f7f4628bd1b3f6b2cc78a6bc4c3a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596662"
---
# <a name="back-up-and-restore-replicated-databases"></a><span data-ttu-id="dc8b9-102">備份及還原複寫的資料庫</span><span class="sxs-lookup"><span data-stu-id="dc8b9-102">Back Up and Restore Replicated Databases</span></span>
  <span data-ttu-id="dc8b9-103">針對複寫的資料庫進行資料的備份與還原時，需要特別地注意。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-103">Replicated databases require special attention with regards to backing up and restoring data.</span></span> <span data-ttu-id="dc8b9-104">本主題提供每種複寫類型的備份與還原策略之簡介資訊，以及取得詳細資訊的連結。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-104">This topic provides introductory information and links to further information on backup and restore strategies for each type of replication.</span></span>  
  
 <span data-ttu-id="dc8b9-105">複寫支援將複寫資料庫還原到與原先建立備份的同一個伺服器與資料庫。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-105">Replication supports restoring replicated databases to the same server and database from which the backup was created.</span></span> <span data-ttu-id="dc8b9-106">如果您將複寫資料庫的備份還原到另一個伺服器或資料庫，將無法保留複寫設定。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-106">If you restore a backup of a replicated database to another server or database, replication settings cannot be preserved.</span></span> <span data-ttu-id="dc8b9-107">在這種情況下，您必須於還原備份後重新建立所有發行集與訂閱。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-107">In this case, you must recreate all publications and subscriptions after backups are restored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="dc8b9-108">如果使用記錄傳送，也可以將複寫的資料庫還原至待命伺服器。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-108">It is possible to restore a replicated database to a standby server if log shipping is being used.</span></span> <span data-ttu-id="dc8b9-109">如需詳細資訊，請參閱[記錄傳送和複寫 &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-109">For more information, see [Log Shipping and Replication &#40;SQL Server&#41;](../../../database-engine/log-shipping/log-shipping-and-replication-sql-server.md).</span></span>  
  
 <span data-ttu-id="dc8b9-110">您應該定期備份複寫的資料庫及其相關聯的系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-110">Replicated databases and their associated system databases should be backed up regularly.</span></span> <span data-ttu-id="dc8b9-111">請備份下列資料庫：</span><span class="sxs-lookup"><span data-stu-id="dc8b9-111">Back up the following databases:</span></span>  
  
-   <span data-ttu-id="dc8b9-112">發行者端的發行集資料庫</span><span class="sxs-lookup"><span data-stu-id="dc8b9-112">The publication database at the Publisher</span></span>  
  
-   <span data-ttu-id="dc8b9-113">散發者端的散發資料庫</span><span class="sxs-lookup"><span data-stu-id="dc8b9-113">The distribution database at the Distributor</span></span>  
  
-   <span data-ttu-id="dc8b9-114">每個訂閱者端的訂閱資料庫</span><span class="sxs-lookup"><span data-stu-id="dc8b9-114">The subscription database at each Subscriber</span></span>  
  
-   <span data-ttu-id="dc8b9-115">發行者、散發者及所有訂閱者端的 **master** 與 **msdb** 系統資料庫。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-115">The **master** and **msdb** system databases at the Publisher, Distributor and all Subscribers.</span></span> <span data-ttu-id="dc8b9-116">這些資料庫應與其他每個及相關的複寫資料庫同時備份。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-116">These databases should be backed up at the same time as each other and the relevant replication database.</span></span> <span data-ttu-id="dc8b9-117">例如，在您備份發行集資料庫的同時，在發行者端備份 **master** 與 **msdb** 資料庫。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-117">For example, back up the **master** and **msdb** databases at the Publisher at the same time you back up the publication database.</span></span> <span data-ttu-id="dc8b9-118">還原發行集資料庫時，請確定 **master** 與 **msdb** 資料庫的複寫組態與設定和發行集資料庫一致。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-118">If the publication database is restored, ensure that the **master** and **msdb** database are consistent with the publication database in terms of replication configuration and settings.</span></span>  
  
 <span data-ttu-id="dc8b9-119">如果您執行一般記錄備份，就必須在記錄備份中擷取任何複寫相關的變更。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-119">If you perform regular log backups, any replication-related changes should be captured in the log backups.</span></span> <span data-ttu-id="dc8b9-120">如果不執行記錄備份，則每當與複寫相關的設定發生變更時，便應該執行備份。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-120">If you do not perform log backups, a backup should be performed whenever a setting relevant to replication is changed.</span></span> <span data-ttu-id="dc8b9-121">如需相關資訊，請參閱 [Common Actions Requiring an Updated Backup](common-actions-requiring-an-updated-backup.md)。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-121">For more information, see [Common Actions Requiring an Updated Backup](common-actions-requiring-an-updated-backup.md).</span></span>  
  
## <a name="backup-and-restore-strategies"></a><span data-ttu-id="dc8b9-122">備份與還原策略</span><span class="sxs-lookup"><span data-stu-id="dc8b9-122">Backup and Restore Strategies</span></span>  
 <span data-ttu-id="dc8b9-123">備份與還原複寫拓撲中每個節點的策略，會因所用的複寫類型而異。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-123">The strategies for backing up and restoring each node in a replication topology differ according to the type of replication used.</span></span> <span data-ttu-id="dc8b9-124">如需每種複寫類型的備份與還原策略之詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="dc8b9-124">For information on backup and restore strategies for each type of replication, see the following topics:</span></span>  
  
-   [<span data-ttu-id="dc8b9-125">備份與還原快照式和異動複寫的策略</span><span class="sxs-lookup"><span data-stu-id="dc8b9-125">Strategies for Backing Up and Restoring Snapshot and Transactional Replication</span></span>](strategies-for-backing-up-and-restoring-snapshot-and-transactional-replication.md)  
  
-   [<span data-ttu-id="dc8b9-126">備份與還原合併式複寫的策略</span><span class="sxs-lookup"><span data-stu-id="dc8b9-126">Strategies for Backing Up and Restoring Merge Replication</span></span>](strategies-for-backing-up-and-restoring-merge-replication.md)  
  
 <span data-ttu-id="dc8b9-127">請隨時將一份您現行複寫設定的指令碼存放在安全之處，作為復原策略的一部份。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-127">As part of any recovery strategy, always keep a current script of your replication settings in a safe location.</span></span> <span data-ttu-id="dc8b9-128">如此一來，倘若伺服器發生錯誤或需要設定測試環境，您可藉由變更伺服器名稱參考來修改該指令碼，如此可幫助重新建立您的複寫設定。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-128">In the event of server failure or the need to set up a test environment, you can modify the script by changing server name references, and it can be used to help recreate your replication settings.</span></span> <span data-ttu-id="dc8b9-129">除了將現行複寫設定撰寫成指令碼之外，您還必須撰寫可啟用及停用複寫的指令碼。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-129">In addition to scripting your current replication settings, you should script the enabling and disabling of replication.</span></span> <span data-ttu-id="dc8b9-130">如需有關編寫複寫物件指令碼的詳細資訊，請參閱＜ [Scripting Replication](../scripting-replication.md)＞。</span><span class="sxs-lookup"><span data-stu-id="dc8b9-130">For information about scripting replication objects, see [Scripting Replication](../scripting-replication.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc8b9-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dc8b9-131">See Also</span></span>  
 <span data-ttu-id="dc8b9-132">[SQL Server 資料庫的備份與還原](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span><span class="sxs-lookup"><span data-stu-id="dc8b9-132">[Back Up and Restore of SQL Server Databases](../../backup-restore/back-up-and-restore-of-sql-server-databases.md) </span></span>  
 [<span data-ttu-id="dc8b9-133">Best Practices for Replication Administration</span><span class="sxs-lookup"><span data-stu-id="dc8b9-133">Best Practices for Replication Administration</span></span>](best-practices-for-replication-administration.md)  
  
  
