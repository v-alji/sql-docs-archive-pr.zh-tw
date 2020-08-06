---
title: MSSQLSERVER_8996 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 8996 (Database Engine error)
ms.assetid: 4e655cdc-945a-4a18-95dd-75f050563d26
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6d0cb5f0294ea471a6e300adbabc0f7b55632994
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598879"
---
# <a name="mssqlserver_8996"></a><span data-ttu-id="f2f57-102">MSSQLSERVER_8996</span><span class="sxs-lookup"><span data-stu-id="f2f57-102">MSSQLSERVER_8996</span></span>
    
## <a name="details"></a><span data-ttu-id="f2f57-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f2f57-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f2f57-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f2f57-104">Product Name</span></span>|<span data-ttu-id="f2f57-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f2f57-105">SQL Server</span></span>|  
|<span data-ttu-id="f2f57-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f2f57-106">Event ID</span></span>|<span data-ttu-id="f2f57-107">8996</span><span class="sxs-lookup"><span data-stu-id="f2f57-107">8996</span></span>|  
|<span data-ttu-id="f2f57-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="f2f57-108">Event Source</span></span>|<span data-ttu-id="f2f57-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f2f57-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f2f57-110">元件</span><span class="sxs-lookup"><span data-stu-id="f2f57-110">Component</span></span>|<span data-ttu-id="f2f57-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f2f57-111">SQLEngine</span></span>|  
|<span data-ttu-id="f2f57-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f2f57-112">Symbolic Name</span></span>|<span data-ttu-id="f2f57-113">DBCC3_IAM_PAGE_RANGE_IN_WRONG_FILEGROUP</span><span class="sxs-lookup"><span data-stu-id="f2f57-113">DBCC3_IAM_PAGE_RANGE_IN_WRONG_FILEGROUP</span></span>|  
|<span data-ttu-id="f2f57-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f2f57-114">Message Text</span></span>|<span data-ttu-id="f2f57-115">物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID，配置單位識別碼 A_ID (類型 TYPE) 的 IAM 頁面 P_ID 控制應該是位於檔案群組 FG_ID2，卻位於檔案群組 FG_ID1 的頁面。</span><span class="sxs-lookup"><span data-stu-id="f2f57-115">IAM page P_ID for object ID O_ID, index ID I_ID, partition ID PN_ID, alloc unit ID A_ID (type TYPE) controls pages in filegroup FG_ID1, that should be in filegroup FG_ID2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f2f57-116">說明</span><span class="sxs-lookup"><span data-stu-id="f2f57-116">Explanation</span></span>  
 <span data-ttu-id="f2f57-117">檔案群組 *FG_ID1* 中的索引配置對應 (IAM) 頁面 *P_ID* 錯誤地將檔案群組 *FG_ID2* 的範圍包含在內。</span><span class="sxs-lookup"><span data-stu-id="f2f57-117">The index allocation map (IAM) page *P_ID* in filegroup *FG_ID1* incorrectly includes extents from filegroup *FG_ID2*.</span></span> <span data-ttu-id="f2f57-118">IAM 頁面的所有範圍都應該和 IAM 頁面本身位於同一個檔案群組。</span><span class="sxs-lookup"><span data-stu-id="f2f57-118">All extents for an IAM page should be in the same filegroup as the IAM page itself.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f2f57-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f2f57-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="f2f57-120">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="f2f57-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="f2f57-121">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="f2f57-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="f2f57-122">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="f2f57-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="f2f57-123">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="f2f57-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="f2f57-124">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="f2f57-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="f2f57-125">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="f2f57-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="f2f57-126">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="f2f57-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="f2f57-127">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="f2f57-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="f2f57-128">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="f2f57-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="f2f57-129">還原備份</span><span class="sxs-lookup"><span data-stu-id="f2f57-129">Restore from Backup</span></span>  
 <span data-ttu-id="f2f57-130">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="f2f57-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="f2f57-131">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="f2f57-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="f2f57-132">不適用。</span><span class="sxs-lookup"><span data-stu-id="f2f57-132">Not applicable.</span></span> <span data-ttu-id="f2f57-133">此錯誤無法修復。</span><span class="sxs-lookup"><span data-stu-id="f2f57-133">This error cannot be repaired.</span></span> <span data-ttu-id="f2f57-134">如果無法從備份還原資料庫，請連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務及支援中心 (CSS)。</span><span class="sxs-lookup"><span data-stu-id="f2f57-134">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
