---
title: MSSQLSERVER_2534 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2534 (Database Engine error)
ms.assetid: 121cf99d-0722-494c-be24-3369c1a0badc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 409c429f961cd8357bfa2e40663c33f3c1f2e36d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598923"
---
# <a name="mssqlserver_2534"></a><span data-ttu-id="740b1-102">MSSQLSERVER_2534</span><span class="sxs-lookup"><span data-stu-id="740b1-102">MSSQLSERVER_2534</span></span>
    
## <a name="details"></a><span data-ttu-id="740b1-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="740b1-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="740b1-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="740b1-104">Product Name</span></span>|<span data-ttu-id="740b1-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="740b1-105">SQL Server</span></span>|  
|<span data-ttu-id="740b1-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="740b1-106">Event ID</span></span>|<span data-ttu-id="740b1-107">2534</span><span class="sxs-lookup"><span data-stu-id="740b1-107">2534</span></span>|  
|<span data-ttu-id="740b1-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="740b1-108">Event Source</span></span>|<span data-ttu-id="740b1-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="740b1-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="740b1-110">元件</span><span class="sxs-lookup"><span data-stu-id="740b1-110">Component</span></span>|<span data-ttu-id="740b1-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="740b1-111">SQLEngine</span></span>|  
|<span data-ttu-id="740b1-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="740b1-112">Symbolic Name</span></span>|<span data-ttu-id="740b1-113">DBCC_PAGE_ALLOCATED_TO_OTHER_OBJECT</span><span class="sxs-lookup"><span data-stu-id="740b1-113">DBCC_PAGE_ALLOCATED_TO_OTHER_OBJECT</span></span>|  
|<span data-ttu-id="740b1-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="740b1-114">Message Text</span></span>|<span data-ttu-id="740b1-115">資料表錯誤：其標題顯示配置給物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE) 的頁面 P_ID 是由其他物件所配置。</span><span class="sxs-lookup"><span data-stu-id="740b1-115">Table error: Page P_ID, whose header indicates it as being allocated to object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE), is allocated by another object.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="740b1-116">說明</span><span class="sxs-lookup"><span data-stu-id="740b1-116">Explanation</span></span>  
 <span data-ttu-id="740b1-117">頁面標頭包含配置單位識別碼 (*A_ID*)，但是該配置單位中並無配置此頁面的索引配置對應 (IAM) 頁面。</span><span class="sxs-lookup"><span data-stu-id="740b1-117">The header of the page contains the allocation unit ID, *A_ID*, but none of the Index Allocation Map (IAM) pages of that allocation unit allocates the page.</span></span> <span data-ttu-id="740b1-118">因此，頁面的標頭包含錯誤的配置單位識別碼，並且頁面上將會顯示相符的 MSSQLServer_2533 錯誤，而該錯誤會對應到此頁面實際配置的配置單位識別碼。</span><span class="sxs-lookup"><span data-stu-id="740b1-118">Therefore, the header of the page contains the wrong allocation unit ID, and the page will have a matching MSSQLServer_2533 error that corresponds to the allocation unit ID to which the page is actually allocated.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="740b1-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="740b1-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="740b1-120">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="740b1-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="740b1-121">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="740b1-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="740b1-122">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="740b1-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="740b1-123">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="740b1-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="740b1-124">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="740b1-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="740b1-125">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="740b1-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="740b1-126">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="740b1-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="740b1-127">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="740b1-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="740b1-128">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="740b1-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="740b1-129">還原備份</span><span class="sxs-lookup"><span data-stu-id="740b1-129">Restore from Backup</span></span>  
 <span data-ttu-id="740b1-130">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="740b1-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="740b1-131">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="740b1-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="740b1-132">如果沒有未受影響的備份可以使用，請執行不含 REPAIR 子句的 DBCC CHECKDB，以確定損毀的範圍。</span><span class="sxs-lookup"><span data-stu-id="740b1-132">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="740b1-133">DBCC CHECKDB 將建議適用的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="740b1-133">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="740b1-134">接著，請執行內含適當 REPAIR 子句的 DBCC CHECKDB，以修復損毀的部分。</span><span class="sxs-lookup"><span data-stu-id="740b1-134">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="740b1-135">如果不確定內含 REPAIR 子句之 DBCC CHECKDB 的效果為何，執行此陳述式之前請先與主要支援提供者連絡。</span><span class="sxs-lookup"><span data-stu-id="740b1-135">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="740b1-136">如果執行含 REPAIR 子句的 DBCC CHECKDB 並未修正這個問題，請與您的主要支援提供者連絡，再執行這個陳述式。</span><span class="sxs-lookup"><span data-stu-id="740b1-136">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="740b1-137">執行 REPAIR 選項的結果</span><span class="sxs-lookup"><span data-stu-id="740b1-137">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="740b1-138">如果索引存在，REPAIR 便會重建索引。</span><span class="sxs-lookup"><span data-stu-id="740b1-138">REPAIR will rebuild the index if an index exists.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="740b1-139">若針對相符的 [MSSQLSERVER_2533](mssqlserver-2533-database-engine-error.md) 錯誤執行 REPAIR，則會先取消配置頁面再進行重建。</span><span class="sxs-lookup"><span data-stu-id="740b1-139">Running REPAIR for the matching [MSSQLSERVER_2533](mssqlserver-2533-database-engine-error.md) error deallocates the page before the rebuild.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="740b1-140">此修復可能會導致資料遺失。</span><span class="sxs-lookup"><span data-stu-id="740b1-140">This repair may cause data loss.</span></span>  
  
  
