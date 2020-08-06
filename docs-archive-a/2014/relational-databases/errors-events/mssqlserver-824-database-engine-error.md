---
title: MSSQLSERVER_824 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 824 (Database Engine error)
ms.assetid: 2aa22246-2712-4fdb-9744-36e7e6f3175e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: d57b19bc8c837b92b65728fbb0046039b862d31a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595993"
---
# <a name="mssqlserver_824"></a><span data-ttu-id="2d830-102">MSSQLSERVER_824</span><span class="sxs-lookup"><span data-stu-id="2d830-102">MSSQLSERVER_824</span></span>
    
## <a name="details"></a><span data-ttu-id="2d830-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2d830-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2d830-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2d830-104">Product Name</span></span>|<span data-ttu-id="2d830-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2d830-105">SQL Server</span></span>|  
|<span data-ttu-id="2d830-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2d830-106">Event ID</span></span>|<span data-ttu-id="2d830-107">824</span><span class="sxs-lookup"><span data-stu-id="2d830-107">824</span></span>|  
|<span data-ttu-id="2d830-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="2d830-108">Event Source</span></span>|<span data-ttu-id="2d830-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2d830-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2d830-110">元件</span><span class="sxs-lookup"><span data-stu-id="2d830-110">Component</span></span>|<span data-ttu-id="2d830-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2d830-111">SQLEngine</span></span>|  
|<span data-ttu-id="2d830-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2d830-112">Symbolic Name</span></span>|<span data-ttu-id="2d830-113">B_HARDSSERR</span><span class="sxs-lookup"><span data-stu-id="2d830-113">B_HARDSSERR</span></span>|  
|<span data-ttu-id="2d830-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2d830-114">Message Text</span></span>|<span data-ttu-id="2d830-115">SQL Server 偵測到邏輯的一致性 I/O 錯誤: %ls。</span><span class="sxs-lookup"><span data-stu-id="2d830-115">SQL Server detected a logical consistency-based I/O error: %ls.</span></span> <span data-ttu-id="2d830-116">這是當在檔案 '%ls' 中位移 %#016I64x 的資料庫識別碼 %d 之頁面 %S_PGID 進行 %S_MSG 的期間所發生的。</span><span class="sxs-lookup"><span data-stu-id="2d830-116">It occurred during a %S_MSG of page %S_PGID in database ID %d at offset %#016I64x in file '%ls'.</span></span>  <span data-ttu-id="2d830-117">SQL Server 錯誤記錄檔和系統事件記錄檔中的訊息，或許可以提供其他詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="2d830-117">Additional messages in the SQL Server error log or system event log may provide more detail.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2d830-118">說明</span><span class="sxs-lookup"><span data-stu-id="2d830-118">Explanation</span></span>  
 <span data-ttu-id="2d830-119">此錯誤表示 Windows 回報從磁碟成功讀取頁面，但 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 發現頁面錯誤。</span><span class="sxs-lookup"><span data-stu-id="2d830-119">This error indicates that Windows reports that the page is successfully read from disk, but [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has discovered something wrong with the page.</span></span> <span data-ttu-id="2d830-120">此錯誤與錯誤 823 類似，不同的是 Windows 並未偵測到此錯誤。</span><span class="sxs-lookup"><span data-stu-id="2d830-120">This error is similar to error 823 except that Windows did not detect the error.</span></span> <span data-ttu-id="2d830-121">這通常表示 I/O 子系統發生問題，例如磁碟機故障、磁碟韌體問題、錯誤的裝置驅動程式等。</span><span class="sxs-lookup"><span data-stu-id="2d830-121">This usually indicates a problem in the I/O subsystem, such as a failing disk drive, disk firmware problems, faulty device driver, and so on.</span></span> <span data-ttu-id="2d830-122">如需 I/O 錯誤的詳細資訊，請參閱[Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)) (第 2 章 Microsoft SQL Server I/O 基本概念)。</span><span class="sxs-lookup"><span data-stu-id="2d830-122">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2d830-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2d830-123">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="2d830-124">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="2d830-124">Look for Hardware Failure</span></span>  
 <span data-ttu-id="2d830-125">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="2d830-125">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="2d830-126">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="2d830-126">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred because of hardware failure.</span></span> <span data-ttu-id="2d830-127">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="2d830-127">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="2d830-128">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="2d830-128">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="2d830-129">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="2d830-129">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="2d830-130">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="2d830-130">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="2d830-131">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="2d830-131">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="2d830-132">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="2d830-132">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="2d830-133">還原備份</span><span class="sxs-lookup"><span data-stu-id="2d830-133">Restore from Backup</span></span>  
 <span data-ttu-id="2d830-134">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="2d830-134">If the problem is not hardware-related and a known clean backup is available, restore the database from the backup.</span></span>  
  
 <span data-ttu-id="2d830-135">請考慮將資料庫變更為使用 PAGE_VERIFY CHECKSUM 選項。</span><span class="sxs-lookup"><span data-stu-id="2d830-135">Consider changing the databases to use the PAGE_VERIFY CHECKSUM option.</span></span> <span data-ttu-id="2d830-136">如需 PAGE_VERIFY 的資訊，請參閱 [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="2d830-136">For information about PAGE_VERIFY, see [ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d830-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d830-137">See Also</span></span>  
 [<span data-ttu-id="2d830-138">管理 suspect_pages 資料表 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2d830-138">Manage the suspect_pages Table &#40;SQL Server&#41;</span></span>](../backup-restore/manage-the-suspect-pages-table-sql-server.md)  
  
  
