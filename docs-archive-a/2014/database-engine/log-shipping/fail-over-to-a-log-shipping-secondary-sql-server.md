---
title: 容錯移轉至記錄傳送次要 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- primary databases [SQL Server]
- secondary data files [SQL Server], manual fail over
- log shipping [SQL Server], failover
- failover [SQL Server], log shipping
ms.assetid: edfe5d59-4287-49c1-96c9-dd56212027bc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 164e2809e4eff5a14ef54124df7c7ca9077793ba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703250"
---
# <a name="fail-over-to-a-log-shipping-secondary-sql-server"></a><span data-ttu-id="64c13-102">容錯移轉至記錄傳送次要 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="64c13-102">Fail Over to a Log Shipping Secondary (SQL Server)</span></span>
  <span data-ttu-id="64c13-103">如果主要伺服器執行個體失敗或需要維護，則容錯移轉至記錄傳送次要十分有用。</span><span class="sxs-lookup"><span data-stu-id="64c13-103">Failing over to a log shipping secondary is useful if the primary server instance fails or requires maintenance.</span></span>  
  
## <a name="preparing-for-a-controlled-failover"></a><span data-ttu-id="64c13-104">準備控制的容錯移轉</span><span class="sxs-lookup"><span data-stu-id="64c13-104">Preparing for a Controlled Failover</span></span>  
 <span data-ttu-id="64c13-105">一般而言，因為主要資料庫的最新備份作業後仍會繼續更新該主要資料庫，所以主要和次要資料庫並不同步。</span><span class="sxs-lookup"><span data-stu-id="64c13-105">Typically, the primary and secondary databases are unsynchronized, because the primary database continues to be updated after its latest backup job.</span></span> <span data-ttu-id="64c13-106">而且，在某些情況下，最近的交易記錄備份尚未複製到次要伺服器執行個體，或某些複製的記錄備份可能仍未套用至次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="64c13-106">Also, in some cases, recent transaction log backups have not been copied to the secondary server instances, or some copied log backups might still not have been applied to the secondary database.</span></span> <span data-ttu-id="64c13-107">建議您，如果可能，請使用主要資料庫開始同步處理所有次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="64c13-107">We recommend that you begin by synchronizing all of the secondary databases with the primary database, if possible.</span></span>  
  
 <span data-ttu-id="64c13-108">如需記錄傳送作業的相關資訊，請參閱 [關於記錄傳送 &#40;SQL Server&#41;](about-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="64c13-108">For information about log shipping jobs, see [About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md).</span></span>  
  
## <a name="failing-over"></a><span data-ttu-id="64c13-109">容錯移轉</span><span class="sxs-lookup"><span data-stu-id="64c13-109">Failing Over</span></span>  
 <span data-ttu-id="64c13-110">若要容錯移轉至次要資料庫：</span><span class="sxs-lookup"><span data-stu-id="64c13-110">To fail over to a secondary database:</span></span>  
  
1.  <span data-ttu-id="64c13-111">將任何未複製的備份檔從備份共用複製到每個次要伺服器的複製目的資料夾。</span><span class="sxs-lookup"><span data-stu-id="64c13-111">Copy any uncopied backup files from the backup share to the copy destination folder of each secondary server.</span></span>  
  
2.  <span data-ttu-id="64c13-112">依序將任何未套用的交易記錄備份套用到每個次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="64c13-112">Apply any unapplied transaction log backups in sequence to each secondary database.</span></span> <span data-ttu-id="64c13-113">如需詳細資訊，請參閱[套用交易記錄備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="64c13-113">For more information, see [Apply Transaction Log Backups &#40;SQL Server&#41;](../../relational-databases/backup-restore/apply-transaction-log-backups-sql-server.md).</span></span>  
  
3.  <span data-ttu-id="64c13-114">如果可存取主要資料庫，則請備份使用中交易記錄，並將記錄備份套用到次要資料庫。</span><span class="sxs-lookup"><span data-stu-id="64c13-114">If the primary database is accessible, back up the active transaction log and apply the log backup to the secondary databases.</span></span>  
  
     <span data-ttu-id="64c13-115">如果原始主要伺服器執行個體未損毀，請使用 WITH NORECOVERY 來備份主要資料庫的交易記錄結尾。</span><span class="sxs-lookup"><span data-stu-id="64c13-115">If the original primary server instance is not damaged, back up the tail of the transaction log of the primary database using WITH NORECOVERY.</span></span> <span data-ttu-id="64c13-116">這樣會讓資料庫維持在還原中的狀態，所以無法提供給使用者使用。</span><span class="sxs-lookup"><span data-stu-id="64c13-116">This leaves the database in the restoring state and therefore unavailable to users.</span></span> <span data-ttu-id="64c13-117">最後，您將可從取代主要資料庫套用交易記錄備份，以向前復原這個資料庫。</span><span class="sxs-lookup"><span data-stu-id="64c13-117">Eventually you will be able to roll this database forward by applying transaction log backups from the replacement primary database.</span></span>  
  
     <span data-ttu-id="64c13-118">如需詳細資訊，請參閱[套用交易記錄備份 &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="64c13-118">For more information, see [Transaction Log Backups &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md).</span></span>  
  
4.  <span data-ttu-id="64c13-119">在同步處理次要伺服器後，您就可以透過復原次要資料庫並將用戶端重新導向至該伺服器執行個體，藉以容錯移轉至偏好的伺服器。</span><span class="sxs-lookup"><span data-stu-id="64c13-119">After the secondary servers are synchronized, you can fail over to whichever one you prefer by recovering its secondary database and redirecting clients to that server instance.</span></span> <span data-ttu-id="64c13-120">復原會讓資料庫進入一致狀態，並使其連線。</span><span class="sxs-lookup"><span data-stu-id="64c13-120">Recovering puts the database into a consistent state and brings it online.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="64c13-121">當您讓次要資料庫可以使用時，就應該確保其中繼資料與原始主要資料庫的中繼資料一致。</span><span class="sxs-lookup"><span data-stu-id="64c13-121">When you make a secondary database available, you should ensure that its metadata is consistent with the metadata of the original primary database.</span></span> <span data-ttu-id="64c13-122">如需詳細資訊，請參閱 [在另一個伺服器執行個體上提供可用的資料庫時，管理中繼資料 &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md)。</span><span class="sxs-lookup"><span data-stu-id="64c13-122">For more information, see [Manage Metadata When Making a Database Available on Another Server Instance &#40;SQL Server&#41;](../../relational-databases/databases/manage-metadata-when-making-a-database-available-on-another-server.md).</span></span>  
  
5.  <span data-ttu-id="64c13-123">在復原次要資料庫後，您可以將它重新設定為當做其他次要資料庫的主要資料庫使用。</span><span class="sxs-lookup"><span data-stu-id="64c13-123">After you have recovered a secondary database, you can reconfigure it to act as a primary database for other secondary databases.</span></span>  
  
     <span data-ttu-id="64c13-124">如果沒有其他次要資料庫可用，請參閱[設定記錄傳送 &#40;SQL Server&#41;](configure-log-shipping-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="64c13-124">If no other secondary database is available, see [Configure Log Shipping &#40;SQL Server&#41;](configure-log-shipping-sql-server.md).</span></span>  
  
##  <a name="related-tasks"></a><a name="RelatedTasks"></a> <span data-ttu-id="64c13-125">相關工作</span><span class="sxs-lookup"><span data-stu-id="64c13-125">Related Tasks</span></span>  
  
-   [<span data-ttu-id="64c13-126">變更主要與次要記錄傳送伺服器間的角色 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="64c13-126">Change Roles Between Primary and Secondary Log Shipping Servers &#40;SQL Server&#41;</span></span>](change-roles-between-primary-and-secondary-log-shipping-servers-sql-server.md)  
  
-   [<span data-ttu-id="64c13-127">角色切換後針對登入和作業進行管理 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="64c13-127">Management of Logins and Jobs After Role Switching &#40;SQL Server&#41;</span></span>](../../sql-server/failover-clusters/management-of-logins-and-jobs-after-role-switching-sql-server.md)  
  
## <a name="see-also"></a><span data-ttu-id="64c13-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="64c13-128">See Also</span></span>  
 <span data-ttu-id="64c13-129">[記錄傳送資料表與預存程序](log-shipping-tables-and-stored-procedures.md) </span><span class="sxs-lookup"><span data-stu-id="64c13-129">[Log Shipping Tables and Stored Procedures](log-shipping-tables-and-stored-procedures.md) </span></span>  
 <span data-ttu-id="64c13-130">[關於記錄傳送 &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="64c13-130">[About Log Shipping &#40;SQL Server&#41;](about-log-shipping-sql-server.md) </span></span>  
 [<span data-ttu-id="64c13-131">結尾記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="64c13-131">Tail-Log Backups &#40;SQL Server&#41;</span></span>](../../relational-databases/backup-restore/tail-log-backups-sql-server.md)  
  
  
