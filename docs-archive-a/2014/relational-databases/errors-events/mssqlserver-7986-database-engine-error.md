---
title: MSSQLSERVER_7986 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7986 (Database Engine error)
ms.assetid: ae64276c-4e1e-4ef3-9ee9-ebeb2f61e565
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4f7d312987a2692c95f2cf6dbe0c86a4b2acbe6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702909"
---
# <a name="mssqlserver_7986"></a><span data-ttu-id="55270-102">MSSQLSERVER_7986</span><span class="sxs-lookup"><span data-stu-id="55270-102">MSSQLSERVER_7986</span></span>
    
## <a name="details"></a><span data-ttu-id="55270-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="55270-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="55270-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="55270-104">Product Name</span></span>|<span data-ttu-id="55270-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="55270-105">SQL Server</span></span>|  
|<span data-ttu-id="55270-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="55270-106">Event ID</span></span>|<span data-ttu-id="55270-107">7986</span><span class="sxs-lookup"><span data-stu-id="55270-107">7986</span></span>|  
|<span data-ttu-id="55270-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="55270-108">Event Source</span></span>|<span data-ttu-id="55270-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="55270-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="55270-110">元件</span><span class="sxs-lookup"><span data-stu-id="55270-110">Component</span></span>|<span data-ttu-id="55270-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="55270-111">SQLEngine</span></span>|  
|<span data-ttu-id="55270-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="55270-112">Symbolic Name</span></span>|<span data-ttu-id="55270-113">DBCC2_PRE_CHECKS_CROSS_OBJECT_LINKAGE</span><span class="sxs-lookup"><span data-stu-id="55270-113">DBCC2_PRE_CHECKS_CROSS_OBJECT_LINKAGE</span></span>|  
|<span data-ttu-id="55270-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="55270-114">Message Text</span></span>|<span data-ttu-id="55270-115">系統資料表預先檢查:物件識別碼 O_ID 有跨物件的鏈結。</span><span class="sxs-lookup"><span data-stu-id="55270-115">System table pre-checks: Object ID O_ID has cross-object chain linkage.</span></span> <span data-ttu-id="55270-116">頁面 P_ID1 指向位於配置單位識別碼 A_ID1 (應該為 A_ID2) 中的 P_ID2。</span><span class="sxs-lookup"><span data-stu-id="55270-116">Page P_ID1 points to P_ID2 in alloc unit ID A_ID1 (should be A_ID2).</span></span> <span data-ttu-id="55270-117">由於無法修復的錯誤，檢查陳述式已經結束。</span><span class="sxs-lookup"><span data-stu-id="55270-117">Check statement terminated due to unrepairable error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="55270-118">說明</span><span class="sxs-lookup"><span data-stu-id="55270-118">Explanation</span></span>  
 <span data-ttu-id="55270-119">DBCC CHECKDB 的第一階段是針對關鍵的系統資料表，執行資料頁的基本檢查。</span><span class="sxs-lookup"><span data-stu-id="55270-119">The first phase of a DBCC CHECKDB is to do primitive checks on the data pages of critical system tables.</span></span> <span data-ttu-id="55270-120">如果找到任何錯誤，由於無法修復錯誤，因此 DBCC CHECKDB 會立即結束。</span><span class="sxs-lookup"><span data-stu-id="55270-120">If any errors are found, they cannot be repaired; therefore, the DBCC CHECKDB terminates immediately.</span></span> <span data-ttu-id="55270-121">指定物件資料層級中頁面 *P_ID1* 的下一頁指標指向位於不同物件的頁面 *P_ID2*。</span><span class="sxs-lookup"><span data-stu-id="55270-121">The next page pointer of page *P_ID1* in the data level of the specified object points to a page, *P_ID2*, in a different object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="55270-122">使用者動作</span><span class="sxs-lookup"><span data-stu-id="55270-122">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="55270-123">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="55270-123">Look for Hardware Failure</span></span>  
 <span data-ttu-id="55270-124">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="55270-124">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="55270-125">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="55270-125">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="55270-126">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="55270-126">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="55270-127">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="55270-127">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="55270-128">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="55270-128">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="55270-129">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="55270-129">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="55270-130">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="55270-130">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="55270-131">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="55270-131">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="55270-132">還原備份</span><span class="sxs-lookup"><span data-stu-id="55270-132">Restore from Backup</span></span>  
 <span data-ttu-id="55270-133">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="55270-133">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="55270-134">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="55270-134">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="55270-135">不適用。</span><span class="sxs-lookup"><span data-stu-id="55270-135">Not applicable.</span></span> <span data-ttu-id="55270-136">此錯誤無法自動修復。</span><span class="sxs-lookup"><span data-stu-id="55270-136">This error cannot be repaired automatically.</span></span> <span data-ttu-id="55270-137">如果無法從備份還原資料庫，請連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務及支援中心 (CSS)。</span><span class="sxs-lookup"><span data-stu-id="55270-137">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
