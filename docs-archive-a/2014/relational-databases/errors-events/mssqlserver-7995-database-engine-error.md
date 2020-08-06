---
title: MSSQLSERVER_7995 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7995 (Database Engine error)
ms.assetid: af6d6322-3cba-43d8-be97-e6ef15f8c933
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8c65cf2b16c4d7a0dcf40272f8280205a111d08e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596694"
---
# <a name="mssqlserver_7995"></a><span data-ttu-id="29919-102">MSSQLSERVER_7995</span><span class="sxs-lookup"><span data-stu-id="29919-102">MSSQLSERVER_7995</span></span>
    
## <a name="details"></a><span data-ttu-id="29919-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="29919-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="29919-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="29919-104">Product Name</span></span>|<span data-ttu-id="29919-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="29919-105">SQL Server</span></span>|  
|<span data-ttu-id="29919-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="29919-106">Event ID</span></span>|<span data-ttu-id="29919-107">7995</span><span class="sxs-lookup"><span data-stu-id="29919-107">7995</span></span>|  
|<span data-ttu-id="29919-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="29919-108">Event Source</span></span>|<span data-ttu-id="29919-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="29919-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="29919-110">元件</span><span class="sxs-lookup"><span data-stu-id="29919-110">Component</span></span>|<span data-ttu-id="29919-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="29919-111">SQLEngine</span></span>|  
|<span data-ttu-id="29919-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="29919-112">Symbolic Name</span></span>|<span data-ttu-id="29919-113">DBCC2_SYSTEM_CATALOGS_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="29919-113">DBCC2_SYSTEM_CATALOGS_CORRUPT</span></span>|  
|<span data-ttu-id="29919-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="29919-114">Message Text</span></span>|<span data-ttu-id="29919-115">資料庫 'DBNAME': 在系統目錄中的一致性錯誤導致無法進一步 DBCC CHECKNAME 處理。</span><span class="sxs-lookup"><span data-stu-id="29919-115">Database 'DBNAME': consistency errors in system catalogs prevent further DBCC CHECKNAME processing.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="29919-116">說明</span><span class="sxs-lookup"><span data-stu-id="29919-116">Explanation</span></span>  
 <span data-ttu-id="29919-117">DBCC CHECKDB 處理序由下列三個階段組成：</span><span class="sxs-lookup"><span data-stu-id="29919-117">The DBCC CHECKDB process consists of the following three stages:</span></span>  
  
1.  <span data-ttu-id="29919-118">配置檢查。</span><span class="sxs-lookup"><span data-stu-id="29919-118">Allocation checks.</span></span> <span data-ttu-id="29919-119">這相當於執行 DBCC CHECKALLOC。</span><span class="sxs-lookup"><span data-stu-id="29919-119">This is equivalent to running DBCC CHECKALLOC.</span></span>  
  
2.  <span data-ttu-id="29919-120">系統資料表一致性的檢查。</span><span class="sxs-lookup"><span data-stu-id="29919-120">System tables consistency checks.</span></span> <span data-ttu-id="29919-121">這相當於針對必要的系統基底資料表，執行小型清單的 DBCC CHECKTABLE。</span><span class="sxs-lookup"><span data-stu-id="29919-121">This is equivalent to running DBCC CHECKTABLE on a small list of necessary system base tables.</span></span>  
  
3.  <span data-ttu-id="29919-122">完整資料庫一致性的檢查。</span><span class="sxs-lookup"><span data-stu-id="29919-122">Complete database consistency checks.</span></span>  
  
 <span data-ttu-id="29919-123">MSSQLEngine_7995 在第 2 階段引發，指出 DBCC CHECKDB 已經找到命令無法修復或尚未指定 REPAIR 的錯誤。</span><span class="sxs-lookup"><span data-stu-id="29919-123">MSSQLEngine_7995 is raised in stage 2 to indicate that DBCC CHECKDB has found errors that the command cannot repair or that REPAIR has not been specified.</span></span> <span data-ttu-id="29919-124">DBCC CHECKDB 無法繼續進行第 3 階段，因為有問題的系統基底資料表儲存資料庫中所有物件的中繼資料，或是系統基底資料表已損毀。</span><span class="sxs-lookup"><span data-stu-id="29919-124">DBCC CHECKDB cannot continue with stage 3 because either the system base tables in question store the metadata for all objects in the database or the system base tables are corrupted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="29919-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="29919-125">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="29919-126">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="29919-126">Look for Hardware Failure</span></span>  
 <span data-ttu-id="29919-127">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="29919-127">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="29919-128">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="29919-128">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="29919-129">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="29919-129">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="29919-130">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="29919-130">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="29919-131">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="29919-131">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="29919-132">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="29919-132">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="29919-133">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="29919-133">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="29919-134">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="29919-134">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="29919-135">還原備份</span><span class="sxs-lookup"><span data-stu-id="29919-135">Restore from Backup</span></span>  
 <span data-ttu-id="29919-136">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="29919-136">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="29919-137">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="29919-137">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="29919-138">如果沒有未受影響的備份可以使用，請執行不含 REPAIR 子句的 DBCC CHECKDB，以確定損毀的範圍。</span><span class="sxs-lookup"><span data-stu-id="29919-138">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="29919-139">DBCC CHECKDB 將建議適用的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="29919-139">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="29919-140">接著，請執行內含適當 REPAIR 子句的 DBCC CHECKDB，以修復損毀的部分。</span><span class="sxs-lookup"><span data-stu-id="29919-140">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="29919-141">如果不確定內含 REPAIR 子句之 DBCC CHECKDB 的效果為何，執行此陳述式之前請先與主要支援提供者連絡。</span><span class="sxs-lookup"><span data-stu-id="29919-141">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="29919-142">如果執行含 REPAIR 子句的 DBCC CHECKDB 並未修正這個問題，請與您的主要支援提供者連絡，再執行這個陳述式。</span><span class="sxs-lookup"><span data-stu-id="29919-142">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="29919-143">執行 REPAIR 選項的結果</span><span class="sxs-lookup"><span data-stu-id="29919-143">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="29919-144">請檢查錯誤清單，查看 REPAIR 針對每項錯誤所執行的動作。</span><span class="sxs-lookup"><span data-stu-id="29919-144">Examine the list of errors to see what REPAIR will do for each.</span></span>  
  
  
