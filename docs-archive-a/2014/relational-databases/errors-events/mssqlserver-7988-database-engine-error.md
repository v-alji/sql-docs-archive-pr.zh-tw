---
title: MSSQLSERVER_7988 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7988 (Database Engine error)
ms.assetid: 29b967b8-de30-4618-99a8-8b1155e69026
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 984cb03aeb5feaa230762e200304f16cd8c5df08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699616"
---
# <a name="mssqlserver_7988"></a><span data-ttu-id="d40ce-102">MSSQLSERVER_7988</span><span class="sxs-lookup"><span data-stu-id="d40ce-102">MSSQLSERVER_7988</span></span>
    
## <a name="details"></a><span data-ttu-id="d40ce-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="d40ce-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="d40ce-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="d40ce-104">Product Name</span></span>|<span data-ttu-id="d40ce-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="d40ce-105">SQL Server</span></span>|  
|<span data-ttu-id="d40ce-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="d40ce-106">Event ID</span></span>|<span data-ttu-id="d40ce-107">7988</span><span class="sxs-lookup"><span data-stu-id="d40ce-107">7988</span></span>|  
|<span data-ttu-id="d40ce-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="d40ce-108">Event Source</span></span>|<span data-ttu-id="d40ce-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="d40ce-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="d40ce-110">元件</span><span class="sxs-lookup"><span data-stu-id="d40ce-110">Component</span></span>|<span data-ttu-id="d40ce-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="d40ce-111">SQLEngine</span></span>|  
|<span data-ttu-id="d40ce-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="d40ce-112">Symbolic Name</span></span>|<span data-ttu-id="d40ce-113">DBCC2_PRE_CHECKS_CHAIN_LOOP_DETECTED</span><span class="sxs-lookup"><span data-stu-id="d40ce-113">DBCC2_PRE_CHECKS_CHAIN_LOOP_DETECTED</span></span>|  
|<span data-ttu-id="d40ce-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="d40ce-114">Message Text</span></span>|<span data-ttu-id="d40ce-115">系統資料表預先檢查:物件識別碼 O_ID。</span><span class="sxs-lookup"><span data-stu-id="d40ce-115">System table pre-checks: Object ID O_ID.</span></span> <span data-ttu-id="d40ce-116">於 P_ID 偵測到資料鍊迴圈。</span><span class="sxs-lookup"><span data-stu-id="d40ce-116">Loop in data chain detected at P_ID.</span></span> <span data-ttu-id="d40ce-117">由於無法修復的錯誤，檢查陳述式已經結束。</span><span class="sxs-lookup"><span data-stu-id="d40ce-117">Check statement terminated because of an irreparable error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="d40ce-118">說明</span><span class="sxs-lookup"><span data-stu-id="d40ce-118">Explanation</span></span>  
 <span data-ttu-id="d40ce-119">DBCC CHECKDB 的第一階段是針對關鍵的系統資料表，執行資料頁的基本檢查。</span><span class="sxs-lookup"><span data-stu-id="d40ce-119">The first phase of a DBCC CHECKDB is to do primitive checks on the data pages of critical system tables.</span></span> <span data-ttu-id="d40ce-120">如果找到任何錯誤，由於無法修復錯誤，因此 DBCC CHECKDB 會立即結束。</span><span class="sxs-lookup"><span data-stu-id="d40ce-120">If any errors are found, they cannot be repaired; therefore, DBCC CHECKDB terminates immediately.</span></span> <span data-ttu-id="d40ce-121">已經在頁面 *P_ID* 上偵測到頁面連結迴圈。</span><span class="sxs-lookup"><span data-stu-id="d40ce-121">A page linkage loop has been detected on page *P_ID*.</span></span> <span data-ttu-id="d40ce-122">若某個頁面的下一頁指標最後會返回該頁面，便會發生頁面連結迴圈。</span><span class="sxs-lookup"><span data-stu-id="d40ce-122">A page linkage loop occurs when the next page pointers from a page eventually return to the page.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="d40ce-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="d40ce-123">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="d40ce-124">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="d40ce-124">Look for Hardware Failure</span></span>  
 <span data-ttu-id="d40ce-125">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="d40ce-125">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="d40ce-126">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="d40ce-126">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="d40ce-127">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="d40ce-127">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="d40ce-128">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="d40ce-128">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="d40ce-129">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="d40ce-129">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="d40ce-130">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="d40ce-130">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="d40ce-131">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="d40ce-131">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="d40ce-132">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="d40ce-132">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="d40ce-133">還原備份</span><span class="sxs-lookup"><span data-stu-id="d40ce-133">Restore from Backup</span></span>  
 <span data-ttu-id="d40ce-134">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="d40ce-134">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="d40ce-135">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="d40ce-135">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="d40ce-136">不適用。</span><span class="sxs-lookup"><span data-stu-id="d40ce-136">Not applicable.</span></span> <span data-ttu-id="d40ce-137">此錯誤無法自動修復。</span><span class="sxs-lookup"><span data-stu-id="d40ce-137">This error cannot be repaired automatically.</span></span> <span data-ttu-id="d40ce-138">如果無法從備份還原資料庫，請連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 服務及支援中心 (CSS)。</span><span class="sxs-lookup"><span data-stu-id="d40ce-138">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Service and Support (CSS).</span></span>  
  
  
