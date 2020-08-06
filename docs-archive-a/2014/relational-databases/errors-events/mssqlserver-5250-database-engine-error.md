---
title: MSSQLSERVER_5250 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 5250 (Database Engine error)
ms.assetid: f4a1d0e8-f27f-4cb8-a25d-040b40555dcc
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ace26b88aca5b00c23aff3fe48f7c1d04ef35245
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702921"
---
# <a name="mssqlserver_5250"></a><span data-ttu-id="19339-102">MSSQLSERVER_5250</span><span class="sxs-lookup"><span data-stu-id="19339-102">MSSQLSERVER_5250</span></span>
    
## <a name="details"></a><span data-ttu-id="19339-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="19339-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="19339-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="19339-104">Product Name</span></span>|<span data-ttu-id="19339-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="19339-105">SQL Server</span></span>|  
|<span data-ttu-id="19339-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="19339-106">Event ID</span></span>|<span data-ttu-id="19339-107">5250</span><span class="sxs-lookup"><span data-stu-id="19339-107">5250</span></span>|  
|<span data-ttu-id="19339-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="19339-108">Event Source</span></span>|<span data-ttu-id="19339-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="19339-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="19339-110">元件</span><span class="sxs-lookup"><span data-stu-id="19339-110">Component</span></span>|<span data-ttu-id="19339-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="19339-111">SQLEngine</span></span>|  
|<span data-ttu-id="19339-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="19339-112">Symbolic Name</span></span>|<span data-ttu-id="19339-113">DBCC4_CRITICAL_DATABASE_PAGE_CORRUPT</span><span class="sxs-lookup"><span data-stu-id="19339-113">DBCC4_CRITICAL_DATABASE_PAGE_CORRUPT</span></span>|  
|<span data-ttu-id="19339-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="19339-114">Message Text</span></span>|<span data-ttu-id="19339-115">資料庫錯誤:資料庫 'NAME' (資料庫識別碼 DB_ID) 的 PAGE_TYPE 頁面 P_ID 無效。</span><span class="sxs-lookup"><span data-stu-id="19339-115">Database error: PAGE_TYPE page P_ID for database 'NAME' (database ID DB_ID) is invalid.</span></span> <span data-ttu-id="19339-116">此錯誤無法修復。</span><span class="sxs-lookup"><span data-stu-id="19339-116">This error cannot be repaired.</span></span> <span data-ttu-id="19339-117">您必須從備份還原。</span><span class="sxs-lookup"><span data-stu-id="19339-117">You must restore from backup.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="19339-118">說明</span><span class="sxs-lookup"><span data-stu-id="19339-118">Explanation</span></span>  
 <span data-ttu-id="19339-119">指定之資料庫的檔案標頭頁面或啟動頁面已損毀。</span><span class="sxs-lookup"><span data-stu-id="19339-119">A file header page or boot page in the specified database is corrupted.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="19339-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="19339-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="19339-121">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="19339-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="19339-122">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="19339-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="19339-123">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="19339-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="19339-124">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="19339-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="19339-125">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="19339-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="19339-126">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="19339-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="19339-127">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="19339-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="19339-128">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="19339-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="19339-129">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="19339-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="19339-130">還原備份</span><span class="sxs-lookup"><span data-stu-id="19339-130">Restore from Backup</span></span>  
 <span data-ttu-id="19339-131">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="19339-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="19339-132">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="19339-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="19339-133">不適用。</span><span class="sxs-lookup"><span data-stu-id="19339-133">Not applicable.</span></span> <span data-ttu-id="19339-134">此錯誤無法修復。</span><span class="sxs-lookup"><span data-stu-id="19339-134">This error cannot be repaired.</span></span> <span data-ttu-id="19339-135">如果無法從備份還原資料庫，請連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務及支援中心 (CSS)。</span><span class="sxs-lookup"><span data-stu-id="19339-135">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
