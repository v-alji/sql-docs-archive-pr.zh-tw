---
title: MSSQLSERVER_2577 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2577 (Database Engine error)
ms.assetid: f53256a2-2fb0-47fd-9ed9-c45389104145
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9e4b7b85f59ba721eae6b4a0ac8db1b2d288422d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598910"
---
# <a name="mssqlserver_2577"></a><span data-ttu-id="162e6-102">MSSQLSERVER_2577</span><span class="sxs-lookup"><span data-stu-id="162e6-102">MSSQLSERVER_2577</span></span>
    
## <a name="details"></a><span data-ttu-id="162e6-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="162e6-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="162e6-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="162e6-104">Product Name</span></span>|<span data-ttu-id="162e6-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="162e6-105">SQL Server</span></span>|  
|<span data-ttu-id="162e6-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="162e6-106">Event ID</span></span>|<span data-ttu-id="162e6-107">2577</span><span class="sxs-lookup"><span data-stu-id="162e6-107">2577</span></span>|  
|<span data-ttu-id="162e6-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="162e6-108">Event Source</span></span>|<span data-ttu-id="162e6-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="162e6-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="162e6-110">元件</span><span class="sxs-lookup"><span data-stu-id="162e6-110">Component</span></span>|<span data-ttu-id="162e6-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="162e6-111">SQLEngine</span></span>|  
|<span data-ttu-id="162e6-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="162e6-112">Symbolic Name</span></span>|<span data-ttu-id="162e6-113">DBCC_IAM_CHAIN_SEQUENCE_OUT_OF_ORDER</span><span class="sxs-lookup"><span data-stu-id="162e6-113">DBCC_IAM_CHAIN_SEQUENCE_OUT_OF_ORDER</span></span>|  
|<span data-ttu-id="162e6-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="162e6-114">Message Text</span></span>|<span data-ttu-id="162e6-115">物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE) 的索引配置對應 (IAM) 鏈中的鏈序號次序不對。</span><span class="sxs-lookup"><span data-stu-id="162e6-115">Chain sequence numbers out of order in the Index Allocation Map (IAM) chain for object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="162e6-116">序號 SEQUENCE1 的頁面 P_ID1 指向序號 SEQUENCE2 的頁面 P_ID2。</span><span class="sxs-lookup"><span data-stu-id="162e6-116">Page P_ID1 with sequence number SEQUENCE1 points to page P_ID2 with sequence number SEQUENCE2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="162e6-117">說明</span><span class="sxs-lookup"><span data-stu-id="162e6-117">Explanation</span></span>  
 <span data-ttu-id="162e6-118">每個索引配置對應 (IAM) 頁面都有一個序號，</span><span class="sxs-lookup"><span data-stu-id="162e6-118">Every Index Allocation Map (IAM) page has a sequence number.</span></span> <span data-ttu-id="162e6-119">這個序號代表 IAM 頁面在 IAM 鏈結中的位置。</span><span class="sxs-lookup"><span data-stu-id="162e6-119">The sequence number is the position of the IAM page within the IAM chain.</span></span> <span data-ttu-id="162e6-120">規則是每出現一個 IAM 頁面，序號便會加 1，</span><span class="sxs-lookup"><span data-stu-id="162e6-120">The rule is that sequence numbers increase by one for each IAM page.</span></span> <span data-ttu-id="162e6-121">但是 IAM 頁面 *P_ID2* 的序號並未遵守此規則。</span><span class="sxs-lookup"><span data-stu-id="162e6-121">IAM page, *P_ID2*, has a sequence number that does not follow this rule.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="162e6-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="162e6-122">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="162e6-123">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="162e6-123">Look for Hardware Failure</span></span>  
 <span data-ttu-id="162e6-124">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="162e6-124">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="162e6-125">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="162e6-125">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="162e6-126">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="162e6-126">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="162e6-127">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="162e6-127">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="162e6-128">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="162e6-128">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="162e6-129">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="162e6-129">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="162e6-130">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="162e6-130">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="162e6-131">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="162e6-131">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="162e6-132">還原備份</span><span class="sxs-lookup"><span data-stu-id="162e6-132">Restore from Backup</span></span>  
 <span data-ttu-id="162e6-133">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="162e6-133">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="162e6-134">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="162e6-134">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="162e6-135">如果沒有未受影響的備份可以使用，請執行不含 REPAIR 子句的 DBCC CHECKDB，以確定損毀的範圍。</span><span class="sxs-lookup"><span data-stu-id="162e6-135">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="162e6-136">DBCC CHECKDB 將建議適用的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="162e6-136">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="162e6-137">接著，請執行內含適當 REPAIR 子句的 DBCC CHECKDB，以修復損毀的部分。</span><span class="sxs-lookup"><span data-stu-id="162e6-137">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="162e6-138">如果不確定內含 REPAIR 子句之 DBCC CHECKDB 的效果為何，執行此陳述式之前請先與主要支援提供者連絡。</span><span class="sxs-lookup"><span data-stu-id="162e6-138">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="162e6-139">如果執行含 REPAIR 子句的 DBCC CHECKDB 並未修正這個問題，請與您的主要支援提供者連絡，再執行這個陳述式。</span><span class="sxs-lookup"><span data-stu-id="162e6-139">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="162e6-140">執行 REPAIR 選項的結果</span><span class="sxs-lookup"><span data-stu-id="162e6-140">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="162e6-141">執行 REPAIR 將會重建 IAM 鏈結。</span><span class="sxs-lookup"><span data-stu-id="162e6-141">Running REPAIR will rebuild the IAM chain.</span></span> <span data-ttu-id="162e6-142">REPAIR 會先將現有的 IAM 鏈結分割成兩半。</span><span class="sxs-lookup"><span data-stu-id="162e6-142">REPAIR first splits the existing IAM chain in two halves.</span></span> <span data-ttu-id="162e6-143">鏈結的前半部以 IAM 頁面 *P_ID1* 結尾。</span><span class="sxs-lookup"><span data-stu-id="162e6-143">The first half of the chain will end with IAM page, *P_ID1*.</span></span> <span data-ttu-id="162e6-144">*P_ID1* 頁面的下一頁指標將設定為 (0:0)。</span><span class="sxs-lookup"><span data-stu-id="162e6-144">The next page pointer of the *P_ID1* page will be set to (0:0).</span></span> <span data-ttu-id="162e6-145">鏈結的後半部以 IAM 頁面 *P_ID2* 開頭。</span><span class="sxs-lookup"><span data-stu-id="162e6-145">The second half of the chain will start with IAM page, *P_ID2*.</span></span> <span data-ttu-id="162e6-146">*P_ID2* 頁面的上一頁指標將會設定為 (0:0)。</span><span class="sxs-lookup"><span data-stu-id="162e6-146">The previous page pointer of the *P_ID2* page will be set to (0:0).</span></span>  
  
 <span data-ttu-id="162e6-147">接著，REPAIR 會將鏈結的兩半連接在一起，並重新產生 IAM 鏈結的序號。</span><span class="sxs-lookup"><span data-stu-id="162e6-147">REPAIR will then connect the two haves of the chain together and regenerate the sequence numbers for the IAM chain.</span></span> <span data-ttu-id="162e6-148">系統將會取消配置無法修復的任何 IAM 頁面。</span><span class="sxs-lookup"><span data-stu-id="162e6-148">Any IAM pages that cannot be repaired will be deallocated.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="162e6-149">此修復可能會導致資料遺失。</span><span class="sxs-lookup"><span data-stu-id="162e6-149">This repair may cause data loss.</span></span>  
  
  
