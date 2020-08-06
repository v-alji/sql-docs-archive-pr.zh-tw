---
title: MSSQLSERVER_5233 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5233 (Database Engine error)
ms.assetid: 7a855afa-2d3b-49b7-adef-197b99fc98b1
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0a5e2c603652534a6d3093a01da0a926a7195954
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598890"
---
# <a name="mssqlserver_5233"></a><span data-ttu-id="9065a-102">MSSQLSERVER_5233</span><span class="sxs-lookup"><span data-stu-id="9065a-102">MSSQLSERVER_5233</span></span>
    
## <a name="details"></a><span data-ttu-id="9065a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9065a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9065a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9065a-104">Product Name</span></span>|<span data-ttu-id="9065a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9065a-105">SQL Server</span></span>|  
|<span data-ttu-id="9065a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9065a-106">Event ID</span></span>|<span data-ttu-id="9065a-107">5233</span><span class="sxs-lookup"><span data-stu-id="9065a-107">5233</span></span>|  
|<span data-ttu-id="9065a-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="9065a-108">Event Source</span></span>|<span data-ttu-id="9065a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9065a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9065a-110">元件</span><span class="sxs-lookup"><span data-stu-id="9065a-110">Component</span></span>|<span data-ttu-id="9065a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9065a-111">SQLEngine</span></span>|  
|<span data-ttu-id="9065a-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9065a-112">Symbolic Name</span></span>|<span data-ttu-id="9065a-113">DBCC4_INCORRECT_VALUE_IN_PAGE_HEADER_NO_METADATA</span><span class="sxs-lookup"><span data-stu-id="9065a-113">DBCC4_INCORRECT_VALUE_IN_PAGE_HEADER_NO_METADATA</span></span>|  
|<span data-ttu-id="9065a-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9065a-114">Message Text</span></span>|<span data-ttu-id="9065a-115">資料表錯誤: 配置單位識別碼 A_ID，頁面 P_ID。</span><span class="sxs-lookup"><span data-stu-id="9065a-115">Table error: alloc unit ID A_ID, page P_ID.</span></span> <span data-ttu-id="9065a-116">測試 (TEST) 失敗。</span><span class="sxs-lookup"><span data-stu-id="9065a-116">The test (TEST) failed.</span></span> <span data-ttu-id="9065a-117">值為 VAL1 和 VAL2。</span><span class="sxs-lookup"><span data-stu-id="9065a-117">The values are VAL1 and VAL2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9065a-118">說明</span><span class="sxs-lookup"><span data-stu-id="9065a-118">Explanation</span></span>  
 <span data-ttu-id="9065a-119">頁面 *P_ID* 的稽核失敗，因為其頁首損毀。</span><span class="sxs-lookup"><span data-stu-id="9065a-119">Page *P_ID* has failed auditing due to a corruption in its page header.</span></span> <span data-ttu-id="9065a-120">TEST 中的字串提供了失敗的實際測試。</span><span class="sxs-lookup"><span data-stu-id="9065a-120">The string in TEST gives the actual test that failed.</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="9065a-121">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="9065a-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="9065a-122">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="9065a-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="9065a-123">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="9065a-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="9065a-124">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="9065a-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="9065a-125">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="9065a-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="9065a-126">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="9065a-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="9065a-127">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="9065a-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="9065a-128">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="9065a-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="9065a-129">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="9065a-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="9065a-130">還原備份</span><span class="sxs-lookup"><span data-stu-id="9065a-130">Restore from Backup</span></span>  
 <span data-ttu-id="9065a-131">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="9065a-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="9065a-132">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="9065a-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="9065a-133">不適用。</span><span class="sxs-lookup"><span data-stu-id="9065a-133">Not applicable.</span></span> <span data-ttu-id="9065a-134">此錯誤無法修復。</span><span class="sxs-lookup"><span data-stu-id="9065a-134">This error cannot be repaired.</span></span> <span data-ttu-id="9065a-135">如果無法從備份還原資料庫，請連絡 Microsoft 客戶服務及支援中心 (CSS)。</span><span class="sxs-lookup"><span data-stu-id="9065a-135">If you cannot restore the database from a backup, contact Microsoft Customer Service and Support (CSS).</span></span>  
  
  
