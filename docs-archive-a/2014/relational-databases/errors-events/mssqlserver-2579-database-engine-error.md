---
title: MSSQLSERVER_2579 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2579 (Database Engine error)
ms.assetid: 8f929d69-8eb4-4fe9-be52-b9680a7820db
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e68cd090ff9d20b14b3456dcda66496fc2bc02d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598906"
---
# <a name="mssqlserver_2579"></a><span data-ttu-id="46042-102">MSSQLSERVER_2579</span><span class="sxs-lookup"><span data-stu-id="46042-102">MSSQLSERVER_2579</span></span>
    
## <a name="details"></a><span data-ttu-id="46042-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="46042-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="46042-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="46042-104">Product Name</span></span>|<span data-ttu-id="46042-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="46042-105">SQL Server</span></span>|  
|<span data-ttu-id="46042-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="46042-106">Event ID</span></span>|<span data-ttu-id="46042-107">2579</span><span class="sxs-lookup"><span data-stu-id="46042-107">2579</span></span>|  
|<span data-ttu-id="46042-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="46042-108">Event Source</span></span>|<span data-ttu-id="46042-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="46042-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="46042-110">元件</span><span class="sxs-lookup"><span data-stu-id="46042-110">Component</span></span>|<span data-ttu-id="46042-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="46042-111">SQLEngine</span></span>|  
|<span data-ttu-id="46042-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="46042-112">Symbolic Name</span></span>|<span data-ttu-id="46042-113">DBCC_EXTENT_OUT_OF_RANGE</span><span class="sxs-lookup"><span data-stu-id="46042-113">DBCC_EXTENT_OUT_OF_RANGE</span></span>|  
|<span data-ttu-id="46042-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="46042-114">Message Text</span></span>|<span data-ttu-id="46042-115">資料表錯誤：物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE) 的範圍 P_ID 超出這個資料庫範圍。</span><span class="sxs-lookup"><span data-stu-id="46042-115">Table error: Extent P_ID in object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE) is beyond the range of this database.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="46042-116">說明</span><span class="sxs-lookup"><span data-stu-id="46042-116">Explanation</span></span>  
 <span data-ttu-id="46042-117">*P_ID* 是採用 *(filenum:pageinfile)* 格式的頁面識別碼。</span><span class="sxs-lookup"><span data-stu-id="46042-117">*P_ID* is a PageID of the form *(filenum:pageinfile)*.</span></span> <span data-ttu-id="46042-118">此範圍的 *pageinfile* 大於資料庫檔案 *filenum)* 的實際大小。</span><span class="sxs-lookup"><span data-stu-id="46042-118">The *pageinfile* of this extent is greater than the physical size of the file (*filenum)* of the database.</span></span> <span data-ttu-id="46042-119">該範圍標示為已配置於指定配置單位識別碼的 IAM 頁面中。</span><span class="sxs-lookup"><span data-stu-id="46042-119">The extent is marked as being allocated in an IAM page for the indicated allocation unit ID.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="46042-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="46042-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="46042-121">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="46042-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="46042-122">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="46042-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="46042-123">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="46042-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="46042-124">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="46042-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="46042-125">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="46042-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="46042-126">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="46042-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="46042-127">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="46042-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="46042-128">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="46042-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="46042-129">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="46042-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="46042-130">還原備份</span><span class="sxs-lookup"><span data-stu-id="46042-130">Restore from Backup</span></span>  
 <span data-ttu-id="46042-131">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="46042-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="46042-132">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="46042-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="46042-133">如果沒有未受影響的備份可以使用，請執行不含 REPAIR 子句的 DBCC CHECKDB，以確定損毀的範圍。</span><span class="sxs-lookup"><span data-stu-id="46042-133">If no clean backup is available, run DBCC CHECKDB without a REPAIR clause to determine the extent of the corruption.</span></span> <span data-ttu-id="46042-134">DBCC CHECKDB 將建議適用的 REPAIR 子句。</span><span class="sxs-lookup"><span data-stu-id="46042-134">DBCC CHECKDB will recommend a REPAIR clause to use.</span></span> <span data-ttu-id="46042-135">接著，請執行內含適當 REPAIR 子句的 DBCC CHECKDB，以修復損毀的部分。</span><span class="sxs-lookup"><span data-stu-id="46042-135">Then, run DBCC CHECKDB with the appropriate REPAIR clause to repair the corruption.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="46042-136">如果不確定內含 REPAIR 子句之 DBCC CHECKDB 的效果為何，執行此陳述式之前請先與主要支援提供者連絡。</span><span class="sxs-lookup"><span data-stu-id="46042-136">If you are not sure what effect DBCC CHECKDB with a REPAIR clause has on your data, contact your primary support provider before running this statement.</span></span>  
  
 <span data-ttu-id="46042-137">如果執行含 REPAIR 子句的 DBCC CHECKDB 並未修正這個問題，請與您的主要支援提供者連絡，再執行這個陳述式。</span><span class="sxs-lookup"><span data-stu-id="46042-137">If running DBCC CHECKDB with one of the REPAIR clauses does not correct the problem, contact your primary support provider.</span></span>  
  
### <a name="results-of-running-repair-options"></a><span data-ttu-id="46042-138">執行 REPAIR 選項的結果</span><span class="sxs-lookup"><span data-stu-id="46042-138">Results of Running REPAIR Options</span></span>  
 <span data-ttu-id="46042-139">執行 REPAIR 將導致系統從 IAM 頁面取消配置範圍。</span><span class="sxs-lookup"><span data-stu-id="46042-139">Running REPAIR will cause the extent to be deallocated from the IAM page.</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="46042-140">此修復可能會導致資料遺失。</span><span class="sxs-lookup"><span data-stu-id="46042-140">This repair may cause data loss.</span></span>  
  
  
