---
title: MSSQLSERVER_2576 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2576 (Database Engine error)
ms.assetid: b727cc2f-c76c-46f8-bbbe-5e7a05a6eabf
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8f378051c7844bf08d617db56666d69b22ecf732
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594085"
---
# <a name="mssqlserver_2576"></a><span data-ttu-id="c9212-102">MSSQLSERVER_2576</span><span class="sxs-lookup"><span data-stu-id="c9212-102">MSSQLSERVER_2576</span></span>
    
## <a name="details"></a><span data-ttu-id="c9212-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="c9212-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c9212-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="c9212-104">Product Name</span></span>|<span data-ttu-id="c9212-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="c9212-105">SQL Server</span></span>|  
|<span data-ttu-id="c9212-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="c9212-106">Event ID</span></span>|<span data-ttu-id="c9212-107">2576</span><span class="sxs-lookup"><span data-stu-id="c9212-107">2576</span></span>|  
|<span data-ttu-id="c9212-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="c9212-108">Event Source</span></span>|<span data-ttu-id="c9212-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="c9212-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="c9212-110">元件</span><span class="sxs-lookup"><span data-stu-id="c9212-110">Component</span></span>|<span data-ttu-id="c9212-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="c9212-111">SQLEngine</span></span>|  
|<span data-ttu-id="c9212-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="c9212-112">Symbolic Name</span></span>|<span data-ttu-id="c9212-113">DBCC_IAM_PARENT_PAGE_WAS_NOT_SEEN</span><span class="sxs-lookup"><span data-stu-id="c9212-113">DBCC_IAM_PARENT_PAGE_WAS_NOT_SEEN</span></span>|  
|<span data-ttu-id="c9212-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="c9212-114">Message Text</span></span>|<span data-ttu-id="c9212-115">物件識別碼 O_ID 中的索引配置對應 (IAM) 頁面 P_ID1 (索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE)) 的上一個指標指向 IAM 頁面 P_ID1，但是掃描中未偵測到這個頁面。</span><span class="sxs-lookup"><span data-stu-id="c9212-115">The Index Allocation Map (IAM) page P_ID1 is pointed to by the previous pointer of IAM page P_ID2 in object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE) but was not detected in the scan.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="c9212-116">說明</span><span class="sxs-lookup"><span data-stu-id="c9212-116">Explanation</span></span>  
 <span data-ttu-id="c9212-117">雖然有頁面參考可以做為 IAM 鏈結中其他 IAM 頁面的上一頁連結，但是卻找不到索引配置對應 (IAM) 頁面或中繼資料項目。</span><span class="sxs-lookup"><span data-stu-id="c9212-117">An Index Allocation Map (IAM) page or metadata entry was not located, even though a reference to the page exists as the previous page link on another IAM page in an IAM chain.</span></span> <span data-ttu-id="c9212-118">如果 *P_ID1* 頁面是 (0:0)，IAM 頁面 *P_ID2* 就是 IAM 鏈結的起點，而遺漏了 IAM 鏈結的中繼資料項目。</span><span class="sxs-lookup"><span data-stu-id="c9212-118">If the *P_ID1* page is (0:0), the IAM page, *P_ID2*, is the start of an IAM chain, and the metadata entry for the IAM chain is missing.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="c9212-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="c9212-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="c9212-120">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="c9212-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="c9212-121">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="c9212-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="c9212-122">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="c9212-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="c9212-123">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="c9212-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="c9212-124">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="c9212-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="c9212-125">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="c9212-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="c9212-126">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="c9212-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="c9212-127">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="c9212-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="c9212-128">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="c9212-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="c9212-129">還原備份</span><span class="sxs-lookup"><span data-stu-id="c9212-129">Restore from Backup</span></span>  
 <span data-ttu-id="c9212-130">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="c9212-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="c9212-131">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="c9212-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="c9212-132">如果沒有未受影響的備份可以使用，請執行不含 REPAIR 子句的 DBCC CHECKDB，以確定損毀的範圍。</span><span class="sxs-lookup"><span data-stu-id="c9212-132">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="c9212-133">DBCC CHECKDB 將建議適用的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="c9212-133">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="c9212-134">接著，請執行內含適當 REPAIR 子句的 DBCC CHECKDB，以修復損毀的部分。</span><span class="sxs-lookup"><span data-stu-id="c9212-134">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="c9212-135">如果不確定內含 REPAIR 子句之 DBCC CHECKDB 的效果為何，執行此陳述式之前請先與主要支援提供者連絡。</span><span class="sxs-lookup"><span data-stu-id="c9212-135">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="c9212-136">如果執行含 REPAIR 子句的 DBCC CHECKDB 並未修正這個問題，請與您的主要支援提供者連絡，再執行這個陳述式。</span><span class="sxs-lookup"><span data-stu-id="c9212-136">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="c9212-137">執行 REPAIR 選項的結果</span><span class="sxs-lookup"><span data-stu-id="c9212-137">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="c9212-138">REPAIR 將會嘗試重建包含 *P_ID2* 頁面的 IAM 鏈結。</span><span class="sxs-lookup"><span data-stu-id="c9212-138">REPAIR will try to rebuild the IAM chain involving the *P_ID2* page.</span></span> <span data-ttu-id="c9212-139">重建此鏈結可能包括從鏈結中移除頁面，或是移除整個鏈結 (如果中繼資料已損毀)。</span><span class="sxs-lookup"><span data-stu-id="c9212-139">Rebuilding the chain may involve removing pages from the chain, or removing the whole chain if the metadata is corrupted.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="c9212-140">此修復可能會導致資料遺失。</span><span class="sxs-lookup"><span data-stu-id="c9212-140">This repair may cause data loss.</span></span>  
  
  
