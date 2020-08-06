---
title: MSSQLSERVER_3159 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 3159 (Database Engine error)
ms.assetid: c93c1003-0e3a-40aa-9873-44a0f5b8b57e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6b469842b2aab15980c72ea01e46270c55ef29e5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596027"
---
# <a name="mssqlserver_3159"></a><span data-ttu-id="e3df2-102">MSSQLSERVER_3159</span><span class="sxs-lookup"><span data-stu-id="e3df2-102">MSSQLSERVER_3159</span></span>
    
## <a name="details"></a><span data-ttu-id="e3df2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e3df2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e3df2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e3df2-104">Product Name</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|<span data-ttu-id="e3df2-105">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e3df2-105">Event ID</span></span>|<span data-ttu-id="e3df2-106">3159</span><span class="sxs-lookup"><span data-stu-id="e3df2-106">3159</span></span>|  
|<span data-ttu-id="e3df2-107">事件來源</span><span class="sxs-lookup"><span data-stu-id="e3df2-107">Event Source</span></span>|<span data-ttu-id="e3df2-108">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e3df2-108">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e3df2-109">元件</span><span class="sxs-lookup"><span data-stu-id="e3df2-109">Component</span></span>|<span data-ttu-id="e3df2-110">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e3df2-110">SQLEngine</span></span>|  
|<span data-ttu-id="e3df2-111">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e3df2-111">Symbolic Name</span></span>|<span data-ttu-id="e3df2-112">LDDB_LOGNOTBACKEDUP</span><span class="sxs-lookup"><span data-stu-id="e3df2-112">LDDB_LOGNOTBACKEDUP</span></span>|  
|<span data-ttu-id="e3df2-113">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e3df2-113">Message Text</span></span>|<span data-ttu-id="e3df2-114">資料庫 "%ls" 的記錄結尾尚未備份。</span><span class="sxs-lookup"><span data-stu-id="e3df2-114">The tail of the log for the database "%ls" has not been backed up.</span></span> <span data-ttu-id="e3df2-115">若您不想遺失其中的內容，請使用 BACKUP LOG WITH NORECOVERY 備份記錄。</span><span class="sxs-lookup"><span data-stu-id="e3df2-115">Use BACKUP LOG WITH NORECOVERY to back up the log if it contains work that you do not want to lose.</span></span> <span data-ttu-id="e3df2-116">亦可使用 RESTORE 陳述式的 WITH REPLACE 或 WITH STOPAT 子句，覆寫記錄的內容。</span><span class="sxs-lookup"><span data-stu-id="e3df2-116">Use the WITH REPLACE or WITH STOPAT clause of the RESTORE statement to just overwrite the contents of the log.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e3df2-117">說明</span><span class="sxs-lookup"><span data-stu-id="e3df2-117">Explanation</span></span>  
 <span data-ttu-id="e3df2-118">在完整或大量記錄復原模式下，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 多半會要求您備份記錄的結尾，以便擷取尚未備份的記錄。</span><span class="sxs-lookup"><span data-stu-id="e3df2-118">In most cases, under the full or bulk-logged recovery models, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] requires that you back up the tail of the log to capture the log records that have not yet been backed up.</span></span> <span data-ttu-id="e3df2-119">在還原作業之前對記錄結尾進行的記錄備份，就稱為「結尾記錄備份」。</span><span class="sxs-lookup"><span data-stu-id="e3df2-119">A log backup taken of the tail of the log just before a restore operation is called a tail-log backup.</span></span>  
  
 <span data-ttu-id="e3df2-120">當您將資料庫復原到失敗點時，結尾記錄備份是復原計畫中重要的最後備份。</span><span class="sxs-lookup"><span data-stu-id="e3df2-120">When you are recovering a database to the point of a failure, the tail-log backup is the last backup of interest in the recovery plan.</span></span> <span data-ttu-id="e3df2-121">如果您無法備份記錄的結尾，則只能將資料庫復原到失敗前建立的最後一個備份的結尾。</span><span class="sxs-lookup"><span data-stu-id="e3df2-121">If you cannot back up the tail of the log, you can recover a database only to the end of the last backup that was created before the failure.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e3df2-122">通常會要求您在開始還原資料庫之前進行結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="e3df2-122">usually requires that you take a tail-log backup before you start to restore a database.</span></span> <span data-ttu-id="e3df2-123">結尾記錄備份可防止工作遺失，並保持記錄鏈結完整。</span><span class="sxs-lookup"><span data-stu-id="e3df2-123">The tail-log backup prevents work loss and keeps the log chain intact.</span></span> <span data-ttu-id="e3df2-124">但是，並非所有的還原狀況都需要結尾記錄備份。</span><span class="sxs-lookup"><span data-stu-id="e3df2-124">However, not all restore scenarios require a tail-log backup.</span></span> <span data-ttu-id="e3df2-125">如果復原點已包含在較早的記錄備份中，或者您要移動或取代 (覆寫) 資料庫，就不需要有結尾記錄備份，而且不需要將它還原至最近備份之後的某個時間點。</span><span class="sxs-lookup"><span data-stu-id="e3df2-125">You do not have to have a tail-log backup if the recovery point is included in an earlier log backup, or if you are moving or replacing (overwriting) the database and do not need to restore it to a point of time after the most recent backup.</span></span> <span data-ttu-id="e3df2-126">此外，如果記錄檔損毀，而且無法建立結尾記錄備份，您也必須在不使用結尾記錄備份的情況下還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="e3df2-126">Also, if the log files are damaged and a tail-log backup cannot be created, you must restore the database without using a tail-log backup.</span></span> <span data-ttu-id="e3df2-127">任何在最近一次記錄備份之後認可的交易都會遺失。</span><span class="sxs-lookup"><span data-stu-id="e3df2-127">Any transactions committed after the latest log backup are lost.</span></span> <span data-ttu-id="e3df2-128">如需詳細資訊，請參閱本主題稍後的「不使用結尾記錄備份而進行還原」。</span><span class="sxs-lookup"><span data-stu-id="e3df2-128">For more information, see "Restoring Without Using a Tail-Log Backup," later in this topic.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="e3df2-129">REPLACE 不應經常使用，而且只應在審慎考量之後使用。</span><span class="sxs-lookup"><span data-stu-id="e3df2-129">REPLACE should be used rarely, and only after careful consideration.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e3df2-130">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e3df2-130">User Action</span></span>  
 <span data-ttu-id="e3df2-131">進行結尾記錄備份，接著再重試一次還原作業。</span><span class="sxs-lookup"><span data-stu-id="e3df2-131">Take a tail-log backup, and retry the restore operation.</span></span>  
  
 <span data-ttu-id="e3df2-132">如果無法備份記錄結尾，請在 RESTORE 陳述式中使用 WITH STOPAT 或 WITH REPLACE。</span><span class="sxs-lookup"><span data-stu-id="e3df2-132">If you cannot back up the tail of the log, use WITH STOPAT or WITH REPLACE in your RESTORE statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3df2-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3df2-133">See Also</span></span>  
 <span data-ttu-id="e3df2-134">[將 SQL Server 資料庫還原至某個時間點 &#40;完整復原模式&#41;](../backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span><span class="sxs-lookup"><span data-stu-id="e3df2-134">[Restore a SQL Server Database to a Point in Time &#40;Full Recovery Model&#41;](../backup-restore/restore-a-sql-server-database-to-a-point-in-time-full-recovery-model.md) </span></span>  
 <span data-ttu-id="e3df2-135">[當資料庫損毀 &#40;SQL Server 時，備份交易記錄&#41;](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e3df2-135">[Back Up the Transaction Log When the Database Is Damaged &#40;SQL Server&#41;](../backup-restore/back-up-the-transaction-log-when-the-database-is-damaged-sql-server.md) </span></span>  
 <span data-ttu-id="e3df2-136">[備份交易記錄 &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="e3df2-136">[Back Up a Transaction Log &#40;SQL Server&#41;](../backup-restore/back-up-a-transaction-log-sql-server.md) </span></span>  
 [<span data-ttu-id="e3df2-137">結尾記錄備份 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="e3df2-137">Tail-Log Backups &#40;SQL Server&#41;</span></span>](../backup-restore/tail-log-backups-sql-server.md)  
  
  
