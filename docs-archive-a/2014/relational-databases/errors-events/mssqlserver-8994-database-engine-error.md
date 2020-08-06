---
title: MSSQLSERVER_8994 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8994 (Database Engine error)
ms.assetid: 8f4b0e2f-04c0-46e4-9208-20a7085d7a1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0bcc0b1db100b70390c09e9c825dbfd068d968af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585461"
---
# <a name="mssqlserver_8994"></a><span data-ttu-id="8b739-102">MSSQLSERVER_8994</span><span class="sxs-lookup"><span data-stu-id="8b739-102">MSSQLSERVER_8994</span></span>
    
## <a name="details"></a><span data-ttu-id="8b739-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="8b739-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="8b739-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="8b739-104">Product Name</span></span>|<span data-ttu-id="8b739-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="8b739-105">SQL Server</span></span>|  
|<span data-ttu-id="8b739-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="8b739-106">Event ID</span></span>|<span data-ttu-id="8b739-107">8994</span><span class="sxs-lookup"><span data-stu-id="8b739-107">8994</span></span>|  
|<span data-ttu-id="8b739-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="8b739-108">Event Source</span></span>|<span data-ttu-id="8b739-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="8b739-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="8b739-110">元件</span><span class="sxs-lookup"><span data-stu-id="8b739-110">Component</span></span>|<span data-ttu-id="8b739-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="8b739-111">SQLEngine</span></span>|  
|<span data-ttu-id="8b739-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="8b739-112">Symbolic Name</span></span>|<span data-ttu-id="8b739-113">DBCC3_MISSING_FORWARDING_ROW</span><span class="sxs-lookup"><span data-stu-id="8b739-113">DBCC3_MISSING_FORWARDING_ROW</span></span>|  
|<span data-ttu-id="8b739-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="8b739-114">Message Text</span></span>|<span data-ttu-id="8b739-115">物件識別碼 O_ID，轉送資料列頁面 P_ID1，位置 S_ID1 應該由轉送資料列頁面 P_ID2，位置 S_ID2 所指向。</span><span class="sxs-lookup"><span data-stu-id="8b739-115">Object ID O_ID, forwarded row page P_ID1, slot S_ID1 should be pointed to by forwarding row page P_ID2, slot S_ID2.</span></span> <span data-ttu-id="8b739-116">沒有遇到轉送資料列。</span><span class="sxs-lookup"><span data-stu-id="8b739-116">Did not encounter forwarding row.</span></span> <span data-ttu-id="8b739-117">可能是配置錯誤。</span><span class="sxs-lookup"><span data-stu-id="8b739-117">Possible allocation error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="8b739-118">說明</span><span class="sxs-lookup"><span data-stu-id="8b739-118">Explanation</span></span>  
 <span data-ttu-id="8b739-119">堆積中的轉送資料列遺漏了應該指向它的轉送資料列。</span><span class="sxs-lookup"><span data-stu-id="8b739-119">A forwarded row in a heap is missing the forwarding row that should point to it.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="8b739-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="8b739-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="8b739-121">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="8b739-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="8b739-122">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="8b739-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="8b739-123">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="8b739-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="8b739-124">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="8b739-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="8b739-125">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="8b739-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="8b739-126">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="8b739-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="8b739-127">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="8b739-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="8b739-128">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="8b739-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="8b739-129">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="8b739-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="8b739-130">還原備份</span><span class="sxs-lookup"><span data-stu-id="8b739-130">Restore from Backup</span></span>  
 <span data-ttu-id="8b739-131">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="8b739-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="8b739-132">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="8b739-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="8b739-133">如果沒有未受影響的備份可以使用，請執行不含 REPAIR 子句的 DBCC CHECKDB，以確定損毀的範圍。</span><span class="sxs-lookup"><span data-stu-id="8b739-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="8b739-134">DBCC CHECKDB 將建議適用的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="8b739-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="8b739-135">接著，請執行內含適當 REPAIR 子句的 DBCC CHECKDB，以修復損毀的部分。</span><span class="sxs-lookup"><span data-stu-id="8b739-135">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="8b739-136">如果不確定內含 REPAIR 子句之 DBCC CHECKDB 的效果為何，執行此陳述式之前請先與主要支援提供者連絡。</span><span class="sxs-lookup"><span data-stu-id="8b739-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="8b739-137">如果執行含 REPAIR 子句的 DBCC CHECKDB 並未修正這個問題，請與您的主要支援提供者連絡，再執行這個陳述式。</span><span class="sxs-lookup"><span data-stu-id="8b739-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
#### <a name="results-of-running-repair-options"></a><span data-ttu-id="8b739-138">執行 REPAIR 選項的結果</span><span class="sxs-lookup"><span data-stu-id="8b739-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="8b739-139">轉送資料列將轉換成一般資料列。</span><span class="sxs-lookup"><span data-stu-id="8b739-139">The forwarded row will be converted to a regular data row.</span></span>  
  
  
