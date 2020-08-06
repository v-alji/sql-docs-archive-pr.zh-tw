---
title: MSSQLSERVER_5256 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5256 (Database Engine error)
ms.assetid: 6fe254b4-2926-446f-8b20-0f1d921a4615
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 9146b7744e78550463cbec4c05df5fd75a049898
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702917"
---
# <a name="mssqlserver_5256"></a><span data-ttu-id="b5f76-102">MSSQLSERVER_5256</span><span class="sxs-lookup"><span data-stu-id="b5f76-102">MSSQLSERVER_5256</span></span>
    
## <a name="details"></a><span data-ttu-id="b5f76-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="b5f76-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="b5f76-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="b5f76-104">Product Name</span></span>|<span data-ttu-id="b5f76-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="b5f76-105">SQL Server</span></span>|  
|<span data-ttu-id="b5f76-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="b5f76-106">Event ID</span></span>|<span data-ttu-id="b5f76-107">5256</span><span class="sxs-lookup"><span data-stu-id="b5f76-107">5256</span></span>|  
|<span data-ttu-id="b5f76-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="b5f76-108">Event Source</span></span>|<span data-ttu-id="b5f76-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="b5f76-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="b5f76-110">元件</span><span class="sxs-lookup"><span data-stu-id="b5f76-110">Component</span></span>|<span data-ttu-id="b5f76-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="b5f76-111">SQLEngine</span></span>|  
|<span data-ttu-id="b5f76-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="b5f76-112">Symbolic Name</span></span>|<span data-ttu-id="b5f76-113">DBCC4_INCORRECT_PAGE_ID_IN_HEADER_NO_METADATA</span><span class="sxs-lookup"><span data-stu-id="b5f76-113">DBCC4_INCORRECT_PAGE_ID_IN_HEADER_NO_METADATA</span></span>|  
|<span data-ttu-id="b5f76-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="b5f76-114">Message Text</span></span>|<span data-ttu-id="b5f76-115">資料表錯誤: 配置單位識別碼 A_ID，頁面 P_ID1 的頁首包含不正確的頁面識別碼。</span><span class="sxs-lookup"><span data-stu-id="b5f76-115">Table error: alloc unit ID A_ID, page P_ID1 contains an incorrect page ID in its page header.</span></span> <span data-ttu-id="b5f76-116">頁首中的 PageId = P_ID2。</span><span class="sxs-lookup"><span data-stu-id="b5f76-116">The PageId in the page header = P_ID2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="b5f76-117">說明</span><span class="sxs-lookup"><span data-stu-id="b5f76-117">Explanation</span></span>  
 <span data-ttu-id="b5f76-118">頁面 *P_ID1* 的頁首包含不正確的頁面識別碼 *P_ID2*。</span><span class="sxs-lookup"><span data-stu-id="b5f76-118">The page header of page *P_ID1* contains an incorrect page ID, *P_ID2*.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="b5f76-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="b5f76-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="b5f76-120">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="b5f76-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="b5f76-121">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="b5f76-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="b5f76-122">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="b5f76-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="b5f76-123">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="b5f76-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="b5f76-124">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="b5f76-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="b5f76-125">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="b5f76-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="b5f76-126">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="b5f76-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="b5f76-127">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="b5f76-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="b5f76-128">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="b5f76-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="b5f76-129">還原備份</span><span class="sxs-lookup"><span data-stu-id="b5f76-129">Restore from Backup</span></span>  
 <span data-ttu-id="b5f76-130">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="b5f76-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="b5f76-131">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="b5f76-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="b5f76-132">不適用。</span><span class="sxs-lookup"><span data-stu-id="b5f76-132">Not applicable.</span></span> <span data-ttu-id="b5f76-133">此錯誤無法修復。</span><span class="sxs-lookup"><span data-stu-id="b5f76-133">This error cannot be repaired.</span></span> <span data-ttu-id="b5f76-134">如果無法從備份還原資料庫，請連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務及支援中心 (CSS)。</span><span class="sxs-lookup"><span data-stu-id="b5f76-134">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
