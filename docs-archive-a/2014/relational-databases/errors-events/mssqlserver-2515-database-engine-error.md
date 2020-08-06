---
title: MSSQLSERVER_2515 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2515 (Database Engine error)
ms.assetid: af93aa29-70c9-4923-90af-aafadb20c1c6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 73b2d8b8ff01b97428ba6149f537d96044c6ae3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687921"
---
# <a name="mssqlserver_2515"></a><span data-ttu-id="3c97a-102">MSSQLSERVER_2515</span><span class="sxs-lookup"><span data-stu-id="3c97a-102">MSSQLSERVER_2515</span></span>
    
## <a name="details"></a><span data-ttu-id="3c97a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3c97a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3c97a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3c97a-104">Product Name</span></span>|<span data-ttu-id="3c97a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3c97a-105">SQL Server</span></span>|  
|<span data-ttu-id="3c97a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3c97a-106">Event ID</span></span>|<span data-ttu-id="3c97a-107">2515</span><span class="sxs-lookup"><span data-stu-id="3c97a-107">2515</span></span>|  
|<span data-ttu-id="3c97a-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="3c97a-108">Event Source</span></span>|<span data-ttu-id="3c97a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3c97a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3c97a-110">元件</span><span class="sxs-lookup"><span data-stu-id="3c97a-110">Component</span></span>|<span data-ttu-id="3c97a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3c97a-111">SQLEngine</span></span>|  
|<span data-ttu-id="3c97a-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3c97a-112">Symbolic Name</span></span>|<span data-ttu-id="3c97a-113">DBCC_DIFF_MAP_OUT_OF_SYNC</span><span class="sxs-lookup"><span data-stu-id="3c97a-113">DBCC_DIFF_MAP_OUT_OF_SYNC</span></span>|  
|<span data-ttu-id="3c97a-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3c97a-114">Message Text</span></span>|<span data-ttu-id="3c97a-115">頁面 P_ID，物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID 類型 TYPE 已經修改，但是未在差異備份點陣圖中標示為已修改。</span><span class="sxs-lookup"><span data-stu-id="3c97a-115">Page P_ID, object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID type TYPE has been modified but is not marked modified in the differential backup bitmap.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3c97a-116">說明</span><span class="sxs-lookup"><span data-stu-id="3c97a-116">Explanation</span></span>  
 <span data-ttu-id="3c97a-117">指定的頁面擁有記錄序號 (LSN)，而該序號高於資料庫之 BackupManager 中的差異參考 LSN，或是檔案之檔案控制區塊中的差異基底 LSN，依據何者較新而定。</span><span class="sxs-lookup"><span data-stu-id="3c97a-117">The page specified has a log sequence number (LSN) that is higher than the differential reference LSN in the BackupManager of the database, or the differential base LSN in the file control block of the file, whichever is more recent.</span></span> <span data-ttu-id="3c97a-118">不過，在差異備份點陣圖中，此頁面並未標示為已變更。</span><span class="sxs-lookup"><span data-stu-id="3c97a-118">However, the page is not marked as changed in the differential backup bitmap.</span></span>  
  
 <span data-ttu-id="3c97a-119">每個資料庫都只會報告一個頁面，因為只有在確定差異點陣圖中沒有任何錯誤時，才會執行這項檢查。</span><span class="sxs-lookup"><span data-stu-id="3c97a-119">Only one page per database will be reported, because this check is only performed when the differential bitmap is known to be error free.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3c97a-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3c97a-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="3c97a-121">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="3c97a-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="3c97a-122">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="3c97a-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="3c97a-123">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="3c97a-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="3c97a-124">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="3c97a-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="3c97a-125">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="3c97a-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="3c97a-126">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="3c97a-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="3c97a-127">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="3c97a-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="3c97a-128">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="3c97a-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="3c97a-129">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="3c97a-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="3c97a-130">還原備份</span><span class="sxs-lookup"><span data-stu-id="3c97a-130">Restore from Backup</span></span>  
 <span data-ttu-id="3c97a-131">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="3c97a-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="3c97a-132">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="3c97a-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="3c97a-133">如果沒有未受影響的備份可以使用，請執行不含 REPAIR 子句的 DBCC CHECKDB，以確定損毀的範圍。</span><span class="sxs-lookup"><span data-stu-id="3c97a-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="3c97a-134">DBCC CHECKDB 將建議適用的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="3c97a-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="3c97a-135">接著，請執行內含適當 REPAIR 子句的 DBCC CHECKDB，以修復損毀的部分。</span><span class="sxs-lookup"><span data-stu-id="3c97a-135">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="3c97a-136">如果不確定內含 REPAIR 子句之 DBCC CHECKDB 的效果為何，執行此陳述式之前請先與主要支援提供者連絡。</span><span class="sxs-lookup"><span data-stu-id="3c97a-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="3c97a-137">如果執行含 REPAIR 子句的 DBCC CHECKDB 並未修正這個問題，請與您的主要支援提供者連絡，再執行這個陳述式。</span><span class="sxs-lookup"><span data-stu-id="3c97a-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="3c97a-138">執行 REPAIR 選項的結果</span><span class="sxs-lookup"><span data-stu-id="3c97a-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="3c97a-139">執行 REPAIR 將會導致差異點陣圖無效。</span><span class="sxs-lookup"><span data-stu-id="3c97a-139">Running REPAIR will invalidate the differential bitmap.</span></span> <span data-ttu-id="3c97a-140">在建立完整資料庫備份之前，您不能執行差異備份。</span><span class="sxs-lookup"><span data-stu-id="3c97a-140">You cannot perform a differential backup until a full database backup is taken.</span></span> <span data-ttu-id="3c97a-141">完整資料庫備份為要重建的差異點陣圖提供基準線。</span><span class="sxs-lookup"><span data-stu-id="3c97a-141">The full database backup provides a baseline for the differential bitmap to be rebuilt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c97a-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c97a-142">See Also</span></span>  
 <span data-ttu-id="3c97a-143">[建立完整資料庫備份 &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="3c97a-143">[Create a Full Database Backup &#40;SQL Server&#41;](../backup-restore/create-a-full-database-backup-sql-server.md) </span></span>  
 [<span data-ttu-id="3c97a-144">MSSQLSERVER_2516</span><span class="sxs-lookup"><span data-stu-id="3c97a-144">MSSQLSERVER_2516</span></span>](mssqlserver-2516-database-engine-error.md)  
  
  
