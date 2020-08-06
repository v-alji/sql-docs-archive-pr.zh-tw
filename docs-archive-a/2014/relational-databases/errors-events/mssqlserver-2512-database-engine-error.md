---
title: MSSQLSERVER_2512 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2512 (Database Engine error)
ms.assetid: 989b527f-5b02-403c-9b7f-51580f4e7688
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: da121c8b49ab8290c494d33f0f2a0ba6fded9e41
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698257"
---
# <a name="mssqlserver_2512"></a><span data-ttu-id="cf4e2-102">MSSQLSERVER_2512</span><span class="sxs-lookup"><span data-stu-id="cf4e2-102">MSSQLSERVER_2512</span></span>
    
## <a name="details"></a><span data-ttu-id="cf4e2-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="cf4e2-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="cf4e2-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="cf4e2-104">Product Name</span></span>|<span data-ttu-id="cf4e2-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="cf4e2-105">SQL Server</span></span>|  
|<span data-ttu-id="cf4e2-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="cf4e2-106">Event ID</span></span>|<span data-ttu-id="cf4e2-107">2512</span><span class="sxs-lookup"><span data-stu-id="cf4e2-107">2512</span></span>|  
|<span data-ttu-id="cf4e2-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="cf4e2-108">Event Source</span></span>|<span data-ttu-id="cf4e2-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="cf4e2-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="cf4e2-110">元件</span><span class="sxs-lookup"><span data-stu-id="cf4e2-110">Component</span></span>|<span data-ttu-id="cf4e2-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="cf4e2-111">SQLEngine</span></span>|  
|<span data-ttu-id="cf4e2-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="cf4e2-112">Symbolic Name</span></span>|<span data-ttu-id="cf4e2-113">DBCC_DUPLICATE_KEYS</span><span class="sxs-lookup"><span data-stu-id="cf4e2-113">DBCC_DUPLICATE_KEYS</span></span>|  
|<span data-ttu-id="cf4e2-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="cf4e2-114">Message Text</span></span>|<span data-ttu-id="cf4e2-115">資料表錯誤：物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE)。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-115">Table error: Object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE).</span></span> <span data-ttu-id="cf4e2-116">頁面 P_ID1 位置 SLOT1 和頁面 P_ID2 位置 SLOT2 上有重複的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-116">Duplicate keys on page P_ID1 slot SLOT1 and page P_ID2 slot SLOT2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="cf4e2-117">說明</span><span class="sxs-lookup"><span data-stu-id="cf4e2-117">Explanation</span></span>  
 <span data-ttu-id="cf4e2-118">指定的兩個位置具有相同的索引鍵，包括任何 `uniqueifiers`。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-118">The two specified slots have identical keys, including any `uniqueifiers`.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="cf4e2-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="cf4e2-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="cf4e2-120">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="cf4e2-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="cf4e2-121">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="cf4e2-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="cf4e2-122">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="cf4e2-123">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="cf4e2-124">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="cf4e2-125">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="cf4e2-126">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="cf4e2-127">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="cf4e2-128">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="cf4e2-129">還原備份</span><span class="sxs-lookup"><span data-stu-id="cf4e2-129">Restore from Backup</span></span>  
 <span data-ttu-id="cf4e2-130">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="cf4e2-131">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="cf4e2-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="cf4e2-132">如果沒有未受影響的備份可以使用，請執行不含 REPAIR 子句的 DBCC CHECKDB，以確定損毀的範圍。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-132">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="cf4e2-133">DBCC CHECKDB 將建議適用的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-133">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="cf4e2-134">接著，請執行內含適當 REPAIR 子句的 DBCC CHECKDB，以修復損毀的部分。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-134">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="cf4e2-135">如果不確定內含 REPAIR 子句之 DBCC CHECKDB 的效果為何，執行此陳述式之前請先與主要支援提供者連絡。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-135">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="cf4e2-136">如果執行含 REPAIR 子句的 DBCC CHECKDB 並未修正這個問題，請與您的主要支援提供者連絡，再執行這個陳述式。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-136">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="cf4e2-137">執行 REPAIR 選項的結果</span><span class="sxs-lookup"><span data-stu-id="cf4e2-137">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="cf4e2-138">如果記錄是準刪除項目或者索引不是唯一項目，DBCC 就可以透過重建索引的方式來修復這個問題。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-138">If either record is a ghost or the index is nonunique, DBCC can repair this problem by rebuilding the index.</span></span> <span data-ttu-id="cf4e2-139">否則，REPAIR 便會在必要時刪除 *P_ID2* 頁面上的 *SLOT2* 位置，或將該位置標示為準刪除項目。</span><span class="sxs-lookup"><span data-stu-id="cf4e2-139">Otherwise, if necessary, REPAIR will delete slot *SLOT2* on page *P_ID2* or mark the slot as a ghost.</span></span>  
  
  
