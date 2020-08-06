---
title: MSSQLSERVER_2575 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2575 (Database Engine error)
ms.assetid: 92dfe449-a122-4730-942b-e1d319862d20
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 461d2b57b5ace98ca624f8dc3717c98f3e9e4d67
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585470"
---
# <a name="mssqlserver_2575"></a><span data-ttu-id="84db5-102">MSSQLSERVER_2575</span><span class="sxs-lookup"><span data-stu-id="84db5-102">MSSQLSERVER_2575</span></span>
    
## <a name="details"></a><span data-ttu-id="84db5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="84db5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="84db5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="84db5-104">Product Name</span></span>|<span data-ttu-id="84db5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="84db5-105">SQL Server</span></span>|  
|<span data-ttu-id="84db5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="84db5-106">Event ID</span></span>|<span data-ttu-id="84db5-107">2575</span><span class="sxs-lookup"><span data-stu-id="84db5-107">2575</span></span>|  
|<span data-ttu-id="84db5-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="84db5-108">Event Source</span></span>|<span data-ttu-id="84db5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="84db5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="84db5-110">元件</span><span class="sxs-lookup"><span data-stu-id="84db5-110">Component</span></span>|<span data-ttu-id="84db5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="84db5-111">SQLEngine</span></span>|  
|<span data-ttu-id="84db5-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="84db5-112">Symbolic Name</span></span>|<span data-ttu-id="84db5-113">DBCC_IAM_PAGE_WAS_NOT_SEEN</span><span class="sxs-lookup"><span data-stu-id="84db5-113">DBCC_IAM_PAGE_WAS_NOT_SEEN</span></span>|  
|<span data-ttu-id="84db5-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="84db5-114">Message Text</span></span>|<span data-ttu-id="84db5-115">物件識別碼 O_ID 中的索引配置對應 (IAM) 頁面 P_ID1 (索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE)) 的下一個指標指向 IAM 頁面 P_ID2，但是掃描中未偵測到這個頁面。</span><span class="sxs-lookup"><span data-stu-id="84db5-115">IAM page P_ID1 is pointed to by the next pointer of IAM page P_ID2 in object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE) but was not detected in the scan.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="84db5-116">說明</span><span class="sxs-lookup"><span data-stu-id="84db5-116">Explanation</span></span>  
 <span data-ttu-id="84db5-117">已找到指定之索引的索引配置對應 (IAM) 頁面，但卻找不到其下一頁指標的 IAM 頁面。</span><span class="sxs-lookup"><span data-stu-id="84db5-117">An Index Allocation Map (IAM) page was found for the specified index; however, the IAM page for its next-page pointer was not found.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="84db5-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="84db5-118">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="84db5-119">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="84db5-119">Look for Hardware Failure</span></span>  
 <span data-ttu-id="84db5-120">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="84db5-120">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="84db5-121">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="84db5-121">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="84db5-122">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="84db5-122">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="84db5-123">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="84db5-123">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="84db5-124">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="84db5-124">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="84db5-125">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="84db5-125">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="84db5-126">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="84db5-126">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="84db5-127">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="84db5-127">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="84db5-128">還原備份</span><span class="sxs-lookup"><span data-stu-id="84db5-128">Restore from Backup</span></span>  
 <span data-ttu-id="84db5-129">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="84db5-129">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="84db5-130">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="84db5-130">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="84db5-131">如果沒有未受影響的備份可以使用，請執行不含 REPAIR 子句的 DBCC CHECKDB，以確定損毀的範圍。</span><span class="sxs-lookup"><span data-stu-id="84db5-131">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="84db5-132">DBCC CHECKDB 將建議適用的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="84db5-132">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="84db5-133">接著，請執行內含適當 REPAIR 子句的 DBCC CHECKDB，以修復損毀的部分。</span><span class="sxs-lookup"><span data-stu-id="84db5-133">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="84db5-134">如果不確定內含 REPAIR 子句之 DBCC CHECKDB 的效果為何，執行此陳述式之前請先與主要支援提供者連絡。</span><span class="sxs-lookup"><span data-stu-id="84db5-134">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="84db5-135">如果執行含 REPAIR 子句的 DBCC CHECKDB 並未修正這個問題，請與您的主要支援提供者連絡，再執行這個陳述式。</span><span class="sxs-lookup"><span data-stu-id="84db5-135">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
#### <a name="results-of-running-repair-options"></a><span data-ttu-id="84db5-136">執行 REPAIR 選項的結果</span><span class="sxs-lookup"><span data-stu-id="84db5-136">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="84db5-137">DBCC 會重建索引。</span><span class="sxs-lookup"><span data-stu-id="84db5-137">DBCC will rebuild the index.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84db5-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84db5-138">See Also</span></span>  
 [<span data-ttu-id="84db5-139">DBCC CHECKDB &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="84db5-139">DBCC CHECKDB &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/database-console-commands/dbcc-checkdb-transact-sql)  
  
  
