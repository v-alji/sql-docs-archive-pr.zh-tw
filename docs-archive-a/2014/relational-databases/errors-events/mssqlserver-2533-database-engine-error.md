---
title: MSSQLSERVER_2533 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2533 (Database Engine error)
ms.assetid: 0418352c-0ab2-4dc7-b8b9-5c3bad94560c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 1eb3e2780693a3a0ffed21ce7b9d7887615536c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699634"
---
# <a name="mssqlserver_2533"></a><span data-ttu-id="a5cb8-102">MSSQLSERVER_2533</span><span class="sxs-lookup"><span data-stu-id="a5cb8-102">MSSQLSERVER_2533</span></span>
    
## <a name="details"></a><span data-ttu-id="a5cb8-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="a5cb8-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="a5cb8-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="a5cb8-104">Product Name</span></span>|<span data-ttu-id="a5cb8-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="a5cb8-105">SQL Server</span></span>|  
|<span data-ttu-id="a5cb8-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="a5cb8-106">Event ID</span></span>|<span data-ttu-id="a5cb8-107">2533</span><span class="sxs-lookup"><span data-stu-id="a5cb8-107">2533</span></span>|  
|<span data-ttu-id="a5cb8-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="a5cb8-108">Event Source</span></span>|<span data-ttu-id="a5cb8-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="a5cb8-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="a5cb8-110">元件</span><span class="sxs-lookup"><span data-stu-id="a5cb8-110">Component</span></span>|<span data-ttu-id="a5cb8-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="a5cb8-111">SQLEngine</span></span>|  
|<span data-ttu-id="a5cb8-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="a5cb8-112">Symbolic Name</span></span>|<span data-ttu-id="a5cb8-113">DBCC_PAGE_WAS_NOT_SEEN</span><span class="sxs-lookup"><span data-stu-id="a5cb8-113">DBCC_PAGE_WAS_NOT_SEEN</span></span>|  
|<span data-ttu-id="a5cb8-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="a5cb8-114">Message Text</span></span>|<span data-ttu-id="a5cb8-115">資料表錯誤：看不到配置給物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE) 的頁面 P_ID。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-115">Table error: Page P_ID allocated to object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE) was not seen.</span></span> <span data-ttu-id="a5cb8-116">頁面可能無效，或標頭中的配置單位識別碼不正確。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-116">Page may be invalid or have incorrect alloc unit ID in its header.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="a5cb8-117">說明</span><span class="sxs-lookup"><span data-stu-id="a5cb8-117">Explanation</span></span>  
 <span data-ttu-id="a5cb8-118">已將某個頁面配置給配置單位識別碼 (*A_ID*)，但是該頁面的標頭中沒有這個配置單位識別碼。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-118">A page is allocated to the allocation unit ID, *A_ID*, but this allocation unit ID is not in the header of the page.</span></span> <span data-ttu-id="a5cb8-119">標頭中有另一個配置單位識別碼。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-119">The header has a different allocation unit ID.</span></span> <span data-ttu-id="a5cb8-120">如果頁面標頭中的配置單位識別碼適用於有效的物件，頁面上可能會出現相符的 MSSQLEngine_2534 錯誤。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-120">If the allocation unit ID in the header of the page is for a valid object, the page may have a matching MSSQLEngine_2534 error.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="a5cb8-121">使用者動作</span><span class="sxs-lookup"><span data-stu-id="a5cb8-121">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="a5cb8-122">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="a5cb8-122">Look for Hardware Failure</span></span>  
 <span data-ttu-id="a5cb8-123">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="a5cb8-123">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="a5cb8-124">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-124">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="a5cb8-125">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-125">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="a5cb8-126">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-126">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="a5cb8-127">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-127">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="a5cb8-128">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-128">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="a5cb8-129">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-129">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="a5cb8-130">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-130">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="a5cb8-131">還原備份</span><span class="sxs-lookup"><span data-stu-id="a5cb8-131">Restore from Backup</span></span>  
 <span data-ttu-id="a5cb8-132">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-132">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="a5cb8-133">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="a5cb8-133">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="a5cb8-134">如果沒有未受影響的備份可以使用，請執行不含 REPAIR 子句的 DBCC CHECKDB，以確定損毀的範圍。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-134">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="a5cb8-135">DBCC CHECKDB 將建議適用的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-135">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="a5cb8-136">接著，請執行內含適當 REPAIR 子句的 DBCC CHECKDB，以修復損毀的部分。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-136">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="a5cb8-137">如果不確定內含 REPAIR 子句之 DBCC CHECKDB 的效果為何，執行此陳述式之前請先與主要支援提供者連絡。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-137">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="a5cb8-138">如果執行含 REPAIR 子句的 DBCC CHECKDB 並未修正這個問題，請與您的主要支援提供者連絡，再執行這個陳述式。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-138">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="a5cb8-139">執行 REPAIR 選項的結果</span><span class="sxs-lookup"><span data-stu-id="a5cb8-139">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="a5cb8-140">REPAIR 會取消配置頁面。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-140">REPAIR will deallocate the page.</span></span> <span data-ttu-id="a5cb8-141">如果頁面來自同資料列資料配置單位，將會重建索引 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-141">If the page was from an in-row data allocation unit, the index, if one exists, will be rebuilt.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="a5cb8-142">此修復可能會導致資料遺失。</span><span class="sxs-lookup"><span data-stu-id="a5cb8-142">This repair may cause data loss.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5cb8-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5cb8-143">See Also</span></span>  
 [<span data-ttu-id="a5cb8-144">MSSQLSERVER_2534</span><span class="sxs-lookup"><span data-stu-id="a5cb8-144">MSSQLSERVER_2534</span></span>](mssqlserver-2534-database-engine-error.md)  
  
  
