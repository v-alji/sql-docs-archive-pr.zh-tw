---
title: MSSQLSERVER_5228 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5228 (Database Engine error)
ms.assetid: 5e83c617-4aa2-4755-bcc5-a798c46b97e4
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: eef59e62f00a44aad7bfefb1719a6d8d2b3d0290
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585466"
---
# <a name="mssqlserver_5228"></a><span data-ttu-id="93563-102">MSSQLSERVER_5228</span><span class="sxs-lookup"><span data-stu-id="93563-102">MSSQLSERVER_5228</span></span>
    
## <a name="details"></a><span data-ttu-id="93563-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="93563-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="93563-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="93563-104">Product Name</span></span>|<span data-ttu-id="93563-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="93563-105">SQL Server</span></span>|  
|<span data-ttu-id="93563-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="93563-106">Event ID</span></span>|<span data-ttu-id="93563-107">5228</span><span class="sxs-lookup"><span data-stu-id="93563-107">5228</span></span>|  
|<span data-ttu-id="93563-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="93563-108">Event Source</span></span>|<span data-ttu-id="93563-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="93563-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="93563-110">元件</span><span class="sxs-lookup"><span data-stu-id="93563-110">Component</span></span>|<span data-ttu-id="93563-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="93563-111">SQLEngine</span></span>|  
|<span data-ttu-id="93563-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="93563-112">Symbolic Name</span></span>|<span data-ttu-id="93563-113">DBCC4_ANTIMATTER_COLUMN_DETECTED</span><span class="sxs-lookup"><span data-stu-id="93563-113">DBCC4_ANTIMATTER_COLUMN_DETECTED</span></span>|  
|<span data-ttu-id="93563-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="93563-114">Message Text</span></span>|<span data-ttu-id="93563-115">資料表錯誤：物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE)，頁面 PG_ID，資料列 R_ID。</span><span class="sxs-lookup"><span data-stu-id="93563-115">Table error: Object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), page PG_ID, row R_ID.</span></span> <span data-ttu-id="93563-116">DBCC 偵測到線上索引建立作業有不完整清除。</span><span class="sxs-lookup"><span data-stu-id="93563-116">DBCC detected incomplete cleanup from an online index build operation.</span></span> <span data-ttu-id="93563-117">(反物質資料行值為 VALUE)。</span><span class="sxs-lookup"><span data-stu-id="93563-117">(Antimatter column value is VALUE.)</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="93563-118">說明</span><span class="sxs-lookup"><span data-stu-id="93563-118">Explanation</span></span>  
 <span data-ttu-id="93563-119">偵測到物件 *O_ID*、索引 *I_ID* 和資料分割 *PN_ID* 的線上索引建立作業未完成。</span><span class="sxs-lookup"><span data-stu-id="93563-119">An unfinished online index build was detected for object *O_ID*, index *I_ID*, and partition *PN_ID*.</span></span> <span data-ttu-id="93563-120">其證據在於資料列 *R_ID* 包含反物質資料行。</span><span class="sxs-lookup"><span data-stu-id="93563-120">This is manifested by the presence of an antimatter column on the row *R_ID*.</span></span> <span data-ttu-id="93563-121">線上索引建立期間，反物質資料行用於協調多個來源提供的記錄。</span><span class="sxs-lookup"><span data-stu-id="93563-121">An antimatter column is used when reconciling records from multiple sources during an online index build.</span></span> <span data-ttu-id="93563-122">錯誤訊息也指出反物質資料行的值。</span><span class="sxs-lookup"><span data-stu-id="93563-122">The error message also indicates the value of the antimatter column.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="93563-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="93563-123">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="93563-124">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="93563-124">Look for Hardware Failure</span></span>  
 <span data-ttu-id="93563-125">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="93563-125">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="93563-126">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="93563-126">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="93563-127">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="93563-127">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="93563-128">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="93563-128">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="93563-129">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="93563-129">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="93563-130">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="93563-130">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="93563-131">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="93563-131">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="93563-132">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="93563-132">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="93563-133">還原備份</span><span class="sxs-lookup"><span data-stu-id="93563-133">Restore from Backup</span></span>  
 <span data-ttu-id="93563-134">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="93563-134">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="93563-135">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="93563-135">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="93563-136">如果沒有未受影響的備份可以使用，請執行不含 REPAIR 子句的 DBCC CHECKDB，以確定損毀的範圍。</span><span class="sxs-lookup"><span data-stu-id="93563-136">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="93563-137">DBCC CHECKDB 將建議適用的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="93563-137">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="93563-138">接著，請執行內含適當 REPAIR 子句的 DBCC CHECKDB，以修復損毀的部分。</span><span class="sxs-lookup"><span data-stu-id="93563-138">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="93563-139">如果不確定內含 REPAIR 子句之 DBCC CHECKDB 的效果為何，執行此陳述式之前請先與主要支援提供者連絡。</span><span class="sxs-lookup"><span data-stu-id="93563-139">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="93563-140">如果執行含 REPAIR 子句的 DBCC CHECKDB 並未修正這個問題，請與您的主要支援提供者連絡，再執行這個陳述式。</span><span class="sxs-lookup"><span data-stu-id="93563-140">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="93563-141">執行 REPAIR 選項的結果</span><span class="sxs-lookup"><span data-stu-id="93563-141">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="93563-142">執行 REPAIR 將導致重建指定的索引及其所有相依索引。</span><span class="sxs-lookup"><span data-stu-id="93563-142">Running REPAIR will cause the specified index and all its dependent indexes to be rebuilt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93563-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="93563-143">See Also</span></span>  
 [<span data-ttu-id="93563-144">DBCC CHECKDB &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="93563-144">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
