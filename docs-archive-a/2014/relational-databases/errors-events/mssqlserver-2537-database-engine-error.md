---
title: MSSQLSERVER_2537 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2537 (Database Engine error)
ms.assetid: 0af6ff69-d75a-4c39-8da2-9bd0695277c6
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c227867bac5a0ea5789ba653414444d011e5910d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598918"
---
# <a name="mssqlserver_2537"></a><span data-ttu-id="22251-102">MSSQLSERVER_2537</span><span class="sxs-lookup"><span data-stu-id="22251-102">MSSQLSERVER_2537</span></span>
    
## <a name="details"></a><span data-ttu-id="22251-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="22251-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="22251-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="22251-104">Product Name</span></span>|<span data-ttu-id="22251-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="22251-105">SQL Server</span></span>|  
|<span data-ttu-id="22251-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="22251-106">Event ID</span></span>|<span data-ttu-id="22251-107">2537</span><span class="sxs-lookup"><span data-stu-id="22251-107">2537</span></span>|  
|<span data-ttu-id="22251-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="22251-108">Event Source</span></span>|<span data-ttu-id="22251-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="22251-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="22251-110">元件</span><span class="sxs-lookup"><span data-stu-id="22251-110">Component</span></span>|<span data-ttu-id="22251-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="22251-111">SQLEngine</span></span>|  
|<span data-ttu-id="22251-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="22251-112">Symbolic Name</span></span>|<span data-ttu-id="22251-113">DBCC_RECORD_CHECK_FAILED</span><span class="sxs-lookup"><span data-stu-id="22251-113">DBCC_RECORD_CHECK_FAILED</span></span>|  
|<span data-ttu-id="22251-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="22251-114">Message Text</span></span>|<span data-ttu-id="22251-115">資料表錯誤：物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE)，頁面 P_ID，資料列 ROW_ID。</span><span class="sxs-lookup"><span data-stu-id="22251-115">Table error: Object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), page P_ID, row ROW_ID.</span></span> <span data-ttu-id="22251-116">記錄檢查 (CHECK_TEXT) 失敗。</span><span class="sxs-lookup"><span data-stu-id="22251-116">Record check (CHECK_TEXT) failed.</span></span> <span data-ttu-id="22251-117">值為 VALUE1 和 VALUE2。</span><span class="sxs-lookup"><span data-stu-id="22251-117">Values are VALUE1 and VALUE2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="22251-118">說明</span><span class="sxs-lookup"><span data-stu-id="22251-118">Explanation</span></span>  
 <span data-ttu-id="22251-119">資料列 ROW_ID (或資料列中的資料行) 無法通過 CHECK_TEXT 所描述的測試或條件。</span><span class="sxs-lookup"><span data-stu-id="22251-119">The row ROW_ID (or a column in the row) failed the test or condition described by CHECK_TEXT.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="22251-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="22251-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="22251-121">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="22251-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="22251-122">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="22251-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="22251-123">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="22251-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="22251-124">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="22251-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="22251-125">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="22251-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="22251-126">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="22251-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="22251-127">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="22251-127">If you suspect that write-caching is the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="22251-128">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="22251-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="22251-129">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="22251-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="22251-130">還原備份</span><span class="sxs-lookup"><span data-stu-id="22251-130">Restore from Backup</span></span>  
 <span data-ttu-id="22251-131">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="22251-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="22251-132">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="22251-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="22251-133">如果沒有未受影響的備份可以使用，請執行不含 REPAIR 子句的 DBCC CHECKDB，以確定損毀的範圍。</span><span class="sxs-lookup"><span data-stu-id="22251-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="22251-134">DBCC CHECKDB 將建議適用的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="22251-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="22251-135">接著，執行含建議 REPAIR 子句的 DBCC CHECKDB。</span><span class="sxs-lookup"><span data-stu-id="22251-135">Then, run DBCC CHECKDB with the recommended REPAIR clause.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="22251-136">如果不確定內含 REPAIR 子句之 DBCC CHECKDB 的效果為何，執行此陳述式之前請先與主要支援提供者連絡。</span><span class="sxs-lookup"><span data-stu-id="22251-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="22251-137">如果執行含 REPAIR 子句的 DBCC CHECKDB 並未修正這個問題，請與您的主要支援提供者連絡，再執行這個陳述式。</span><span class="sxs-lookup"><span data-stu-id="22251-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="22251-138">執行 REPAIR 選項的結果</span><span class="sxs-lookup"><span data-stu-id="22251-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="22251-139">如果索引存在，REPAIR 便會重建索引。</span><span class="sxs-lookup"><span data-stu-id="22251-139">REPAIR will rebuild the index if an index exists.</span></span>  
  
 <span data-ttu-id="22251-140">**注意**：此修復可能會導致資料遺失。</span><span class="sxs-lookup"><span data-stu-id="22251-140">**Caution** This repair may cause data loss.</span></span>  
  
  
