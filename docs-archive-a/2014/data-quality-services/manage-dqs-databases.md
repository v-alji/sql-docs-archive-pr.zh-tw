---
title: 管理 DQS 資料庫 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: data-quality-services
ms.topic: conceptual
ms.assetid: 655a67aa-d662-42f2-b982-c6217125ada8
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7228021dd3fe0af61312eeb891081cc24e1aa95d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599689"
---
# <a name="manage-dqs-databases"></a><span data-ttu-id="954a0-102">管理 DQS 資料庫</span><span class="sxs-lookup"><span data-stu-id="954a0-102">Manage DQS Databases</span></span>
  <span data-ttu-id="954a0-103">本節針對 DQS 資料庫提供可執行之資料庫管理活動的相關資訊，如備份/還原或卸離/附加等。</span><span class="sxs-lookup"><span data-stu-id="954a0-103">This section provides information about database management activities that can be performed on the DQS databases such as backup/restore or detach/attach.</span></span>  
  
##  <a name="backup-and-restore-the-dqs-databases"></a><a name="BackupRestore"></a> <span data-ttu-id="954a0-104">備份與還原 DQS 資料庫</span><span class="sxs-lookup"><span data-stu-id="954a0-104">Backup and Restore the DQS Databases</span></span>  
 <span data-ttu-id="954a0-105">備份和還原 SQL Server 資料庫是資料庫管理員經常執行的作業，可在發生嚴重損毀時復原備份資料庫中的資料來避免資料遺失。</span><span class="sxs-lookup"><span data-stu-id="954a0-105">Backup and restore of SQL Server databases are common operations that database administrators perform for preventing loss of data in a case of disaster by recovering data from the backup databases.</span></span> [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] <span data-ttu-id="954a0-106">主要是由兩個 SQL Server 資料庫所實作：DQS_MAIN 和 DQS_PROJECTS。</span><span class="sxs-lookup"><span data-stu-id="954a0-106">is primarily implemented by two SQL Server databases: DQS_MAIN and DQS_PROJECTS.</span></span> <span data-ttu-id="954a0-107">[!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) 資料庫的備份與還原程序類似於其他任何 SQL Server 資料庫。在備份和還原 DQS 資料庫時，要面臨三個挑戰：</span><span class="sxs-lookup"><span data-stu-id="954a0-107">The backup and restore procedures of the [!INCLUDE[ssDQSnoversion](../includes/ssdqsnoversion-md.md)] (DQS) databases are similar to any other SQL Server databases.There are three challenges that are associated with backup and restore of the DQS databases:</span></span>  
  
-   <span data-ttu-id="954a0-108">DQS 資料庫的備份和還原作業必須同步處理。</span><span class="sxs-lookup"><span data-stu-id="954a0-108">The backup and restore operations of the DQS databases must be synchronized.</span></span> <span data-ttu-id="954a0-109">否則，還原的 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] 將無法運作。</span><span class="sxs-lookup"><span data-stu-id="954a0-109">Otherwise the restored [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)] will not be functional.</span></span>  
  
-   <span data-ttu-id="954a0-110">兩個 DQS 資料庫 DQS_MAIN 和 DQS_PROJECTS 除了簡單資料庫物件 (例如資料表和預存程序) 以外，也包含組件與其他複雜物件。</span><span class="sxs-lookup"><span data-stu-id="954a0-110">The two DQS databases, DQS_MAIN and DQS_PROJECTS, contain assemblies and other complex objects, apart from just simple database objects (such as tables and stored procedures).</span></span>  
  
-   <span data-ttu-id="954a0-111">DQS 資料庫之外必須有一些實體存在，DQS 資料庫才能當做 [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)]運作，特別是兩個 SQL Server 登入 (##MS_dqs_db_owner_login## 和 ##MS_dqs_service_login##) 及 master 資料庫中的初始化預存程序 (DQInitDQS_MAIN)。</span><span class="sxs-lookup"><span data-stu-id="954a0-111">There are some entities outside of the DQS databases that must exist for the DQS databases to be functional as [!INCLUDE[ssDQSServer](../includes/ssdqsserver-md.md)], specifically the two SQL Server logins (##MS_dqs_db_owner_login## and ##MS_dqs_service_login##), and an initialization stored procedure (DQInitDQS_MAIN) in the master database.</span></span>  
  
 <span data-ttu-id="954a0-112">如需有關 SQL Server 中之備份與還原的詳細資訊，請參閱＜ [SQL Server 資料庫的備份與還原](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md)＞。</span><span class="sxs-lookup"><span data-stu-id="954a0-112">For detailed information about backup and restore in SQL Server, see [Back Up and Restore of SQL Server Databases](../relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases.md).</span></span>  
  
### <a name="default-autogrowth-size-and-recovery-model-for-the-dqs-databases"></a><span data-ttu-id="954a0-113">DQS 資料庫的預設自動成長大小和復原模式</span><span class="sxs-lookup"><span data-stu-id="954a0-113">Default Autogrowth Size and Recovery Model for the DQS Databases</span></span>  
 <span data-ttu-id="954a0-114">為了避免 DQS 資料庫和交易記錄無限成長而且可能填滿硬碟：</span><span class="sxs-lookup"><span data-stu-id="954a0-114">To prevent DQS databases and transaction logs to grow infinitely and potentially fill the hard disk:</span></span>  
  
-   <span data-ttu-id="954a0-115">DQS 資料庫的預設 **[自動成長]** 大小設定為 10%。</span><span class="sxs-lookup"><span data-stu-id="954a0-115">The default **Autogrowth** size of the DQS databases is set to 10%.</span></span>  
  
-   <span data-ttu-id="954a0-116">DQS 資料庫的預設復原模式設定為 **[簡單]**。</span><span class="sxs-lookup"><span data-stu-id="954a0-116">The default recovery model of the DQS databases is set to **Simple**.</span></span> <span data-ttu-id="954a0-117">在簡單復原模式中，交易會使用最低限度記錄，而且系統會在交易完成之後自動進行記錄截斷，以便釋出交易記錄 (.ldf 檔案) 中的空間。</span><span class="sxs-lookup"><span data-stu-id="954a0-117">In the Simple recovery model, transactions are minimally logged, and the log truncation happens automatically after the transaction is complete to free up space in the transaction log (.ldf file).</span></span> <span data-ttu-id="954a0-118">如需簡單復原模式的詳細資訊，請參閱[完整資料庫備份 &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="954a0-118">For detailed information about the simple recovery model, see [Full Database Backups &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md).</span></span>  
  
> [!IMPORTANT]
>  -   <span data-ttu-id="954a0-119">在簡單復原模式中，當記錄檔記錄有一段很長的時間維持在使用中狀態 (例如，冗長且耗時的交易) 時，記錄截斷可能會延遲，因此可能會導致交易記錄填滿。</span><span class="sxs-lookup"><span data-stu-id="954a0-119">In the Simple recovery model, when log records remain active for a long time (for example, a long and time-consuming transaction), log truncation can be delayed, and therefore can result in the filling up of transaction log.</span></span> <span data-ttu-id="954a0-120">此外，記錄截斷不會縮減實體記錄檔 (.ldf 檔案) 的大小。</span><span class="sxs-lookup"><span data-stu-id="954a0-120">Also, log truncation does not reduce the size of the physical log file (.ldf file).</span></span> <span data-ttu-id="954a0-121">若要縮減實體記錄檔的大小，您必須壓縮記錄檔。</span><span class="sxs-lookup"><span data-stu-id="954a0-121">To reduce the size of a physical log file, you need to shrink the log file.</span></span> <span data-ttu-id="954a0-122">如需有關疑難排解交易記錄之相關問題的詳細資訊，請參閱[交易記錄 &#40;SQL Server&#41;](../relational-databases/logs/the-transaction-log-sql-server.md) 或位於 [https://go.microsoft.com/fwlink/?LinkId=237446](https://go.microsoft.com/fwlink/?LinkId=237446) 的 Microsoft 支援服務文件。</span><span class="sxs-lookup"><span data-stu-id="954a0-122">For information about troubleshooting issues around transaction log, see [The Transaction Log &#40;SQL Server&#41;](../relational-databases/logs/the-transaction-log-sql-server.md) or the Microsoft Support article at [https://go.microsoft.com/fwlink/?LinkId=237446](https://go.microsoft.com/fwlink/?LinkId=237446).</span></span>  
> -   <span data-ttu-id="954a0-123">您必須定期執行 DQS 資料庫的完整或差異備份，並且備份交易記錄，以便執行資料的時間點復原。</span><span class="sxs-lookup"><span data-stu-id="954a0-123">You must regularly perform a Full or Differential backup of the DQS databases and back up the transaction log as well to perform point-in-time recovery of data.</span></span> <span data-ttu-id="954a0-124">如需詳細資訊，請參閱[完整資料庫備份 &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md) 和[備份交易記錄 &#40;SQL Server&#41;](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="954a0-124">For more information, see [Full Database Backups &#40;SQL Server&#41;](../relational-databases/backup-restore/full-database-backups-sql-server.md) and [Back Up a Transaction Log &#40;SQL Server&#41;](../relational-databases/backup-restore/back-up-a-transaction-log-sql-server.md).</span></span>  
  
##  <a name="detachattach-the-dqs-databases"></a><a name="DetachAttach"></a><span data-ttu-id="954a0-125">卸離/附加 DQS 資料庫</span><span class="sxs-lookup"><span data-stu-id="954a0-125">Detach/Attach the DQS Databases</span></span>  
 <span data-ttu-id="954a0-126">您可以卸離 DQS 資料庫的資料檔和交易記錄檔，再將資料庫重新附加至相同或不同的 SQL Server 執行個體，藉此將 DQS 資料庫更換到相同電腦上的另一個 SQL Server 執行個體或是移動資料庫。</span><span class="sxs-lookup"><span data-stu-id="954a0-126">You can detach the data and transaction log files of the DQS databases, and then reattach the databases to the same or another instance of SQL Server if you want to change the DQS databases to a different instance of SQL Server on the same computer or to move the database.</span></span>  
  
 <span data-ttu-id="954a0-127">如需在 SQL Server 中卸離和附加資料庫之事前考量與操作期間注意事項的詳細資訊，請參閱[卸離和附加資料庫 &#40;SQL Server&#41;](../relational-databases/databases/database-detach-and-attach-sql-server.md)。</span><span class="sxs-lookup"><span data-stu-id="954a0-127">For detailed information about things to consider before and during detaching and attaching databases in SQL Server, see [Database Detach and Attach &#40;SQL Server&#41;](../relational-databases/databases/database-detach-and-attach-sql-server.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="954a0-128">相關工作</span><span class="sxs-lookup"><span data-stu-id="954a0-128">Related Tasks</span></span>  
  
|<span data-ttu-id="954a0-129">工作描述</span><span class="sxs-lookup"><span data-stu-id="954a0-129">Task Description</span></span>|<span data-ttu-id="954a0-130">主題</span><span class="sxs-lookup"><span data-stu-id="954a0-130">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="954a0-131">描述如何備份及還原 DQS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="954a0-131">Describes how to back up and restore the DQS databases.</span></span>|[<span data-ttu-id="954a0-132">備份及還原 DQS 資料庫</span><span class="sxs-lookup"><span data-stu-id="954a0-132">Backing Up and Restoring DQS Databases</span></span>](../../2014/data-quality-services/backing-up-and-restoring-dqs-databases.md)|  
|<span data-ttu-id="954a0-133">描述如何卸離和附加 DQS 資料庫。</span><span class="sxs-lookup"><span data-stu-id="954a0-133">Describes how to detach and attach the DQS databases.</span></span>|[<span data-ttu-id="954a0-134">卸離和附加 DQS 資料庫</span><span class="sxs-lookup"><span data-stu-id="954a0-134">Detaching and Attaching DQS Databases</span></span>](../../2014/data-quality-services/detaching-and-attaching-dqs-databases.md)|  
  
## <a name="see-also"></a><span data-ttu-id="954a0-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="954a0-135">See Also</span></span>  
 [<span data-ttu-id="954a0-136">dqs 管理</span><span class="sxs-lookup"><span data-stu-id="954a0-136">DQS Administration</span></span>](../../2014/data-quality-services/dqs-administration.md)  
  
  
