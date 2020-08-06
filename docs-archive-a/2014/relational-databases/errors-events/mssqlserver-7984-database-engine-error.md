---
title: MSSQLSERVER_7984 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7984 (Database Engine error)
ms.assetid: e3192f56-e4e2-41da-b132-65f1e7540b1a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c7f92fe4f3751621e0cc636ffcd2d4de73b348d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598426"
---
# <a name="mssqlserver_7984"></a><span data-ttu-id="95559-102">MSSQLSERVER_7984</span><span class="sxs-lookup"><span data-stu-id="95559-102">MSSQLSERVER_7984</span></span>
    
## <a name="details"></a><span data-ttu-id="95559-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="95559-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="95559-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="95559-104">Product Name</span></span>|<span data-ttu-id="95559-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="95559-105">SQL Server</span></span>|  
|<span data-ttu-id="95559-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="95559-106">Event ID</span></span>|<span data-ttu-id="95559-107">7984</span><span class="sxs-lookup"><span data-stu-id="95559-107">7984</span></span>|  
|<span data-ttu-id="95559-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="95559-108">Event Source</span></span>|<span data-ttu-id="95559-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="95559-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="95559-110">元件</span><span class="sxs-lookup"><span data-stu-id="95559-110">Component</span></span>|<span data-ttu-id="95559-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="95559-111">SQLEngine</span></span>|  
|<span data-ttu-id="95559-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="95559-112">Symbolic Name</span></span>|<span data-ttu-id="95559-113">DBCC2_PRE_CHECKS_BAD_PAGE_TYPE</span><span class="sxs-lookup"><span data-stu-id="95559-113">DBCC2_PRE_CHECKS_BAD_PAGE_TYPE</span></span>|  
|<span data-ttu-id="95559-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="95559-114">Message Text</span></span>|<span data-ttu-id="95559-115">系統資料表預先檢查:物件識別碼 O_ID。</span><span class="sxs-lookup"><span data-stu-id="95559-115">System table pre-checks: Object ID O_ID.</span></span> <span data-ttu-id="95559-116">頁面 P_ID 有非預期的頁面類型 PAGETYPE。</span><span class="sxs-lookup"><span data-stu-id="95559-116">Page P_ID has unexpected page type PAGETYPE.</span></span> <span data-ttu-id="95559-117">由於無法修復的錯誤，檢查陳述式已經結束。</span><span class="sxs-lookup"><span data-stu-id="95559-117">Check statement terminated because of an irreparable error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="95559-118">說明</span><span class="sxs-lookup"><span data-stu-id="95559-118">Explanation</span></span>  
 <span data-ttu-id="95559-119">在指定物件的資料層級中找到 DATA_PAGE 以外的頁面類型。</span><span class="sxs-lookup"><span data-stu-id="95559-119">A page with a type other than DATA_PAGE was found in the data level of the specified object.</span></span> <span data-ttu-id="95559-120">這是在 DBCC CHECKDB 命令檢查的第一階段所引發的錯誤。</span><span class="sxs-lookup"><span data-stu-id="95559-120">This error is raised during the first phase of the DBCC CHECKDB command checks.</span></span> <span data-ttu-id="95559-121">在這個階段，DBCC CHECKDB 會針對關鍵的系統基底資料表，執行資料頁的基本檢查。</span><span class="sxs-lookup"><span data-stu-id="95559-121">During this phase, DBCC CHECKDB performs primitive checks on the data pages of critical system base tables.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95559-122">如果在系統資料表中找到任何錯誤，由於無法修復錯誤，因此 DBCC CHECKDB 命令會立即結束。</span><span class="sxs-lookup"><span data-stu-id="95559-122">If any errors are found in the system tables, the errors cannot be repaired; therefore, the DBCC CHECKDB command ends immediately.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="95559-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="95559-123">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="95559-124">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="95559-124">Look for Hardware Failure</span></span>  
 <span data-ttu-id="95559-125">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="95559-125">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="95559-126">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="95559-126">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="95559-127">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="95559-127">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="95559-128">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="95559-128">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="95559-129">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="95559-129">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="95559-130">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="95559-130">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="95559-131">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="95559-131">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="95559-132">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="95559-132">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="95559-133">還原備份</span><span class="sxs-lookup"><span data-stu-id="95559-133">Restore from Backup</span></span>  
 <span data-ttu-id="95559-134">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="95559-134">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="95559-135">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="95559-135">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="95559-136">不適用。</span><span class="sxs-lookup"><span data-stu-id="95559-136">Not applicable.</span></span> <span data-ttu-id="95559-137">此錯誤無法自動修復。</span><span class="sxs-lookup"><span data-stu-id="95559-137">This error cannot be repaired automatically.</span></span> <span data-ttu-id="95559-138">如果無法從備份還原資料庫，請連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 服務及支援中心 (CSS)。</span><span class="sxs-lookup"><span data-stu-id="95559-138">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service and Support (CSS).</span></span>  
  
  
