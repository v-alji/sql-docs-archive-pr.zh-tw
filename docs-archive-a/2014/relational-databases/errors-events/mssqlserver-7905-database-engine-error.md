---
title: MSSQLSERVER_7905 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7905 (Database Engine error)
ms.assetid: cf19fbbb-7158-45f2-8778-8f3cad7f574a
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 253bf03c1bfacccfd809cd417163eb9d54644f28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596007"
---
# <a name="mssqlserver_7905"></a><span data-ttu-id="9ccd7-102">MSSQLSERVER_7905</span><span class="sxs-lookup"><span data-stu-id="9ccd7-102">MSSQLSERVER_7905</span></span>
    
## <a name="details"></a><span data-ttu-id="9ccd7-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="9ccd7-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="9ccd7-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="9ccd7-104">Product Name</span></span>|<span data-ttu-id="9ccd7-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="9ccd7-105">SQL Server</span></span>|  
|<span data-ttu-id="9ccd7-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="9ccd7-106">Event ID</span></span>|<span data-ttu-id="9ccd7-107">7905</span><span class="sxs-lookup"><span data-stu-id="9ccd7-107">7905</span></span>|  
|<span data-ttu-id="9ccd7-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="9ccd7-108">Event Source</span></span>|<span data-ttu-id="9ccd7-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="9ccd7-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="9ccd7-110">元件</span><span class="sxs-lookup"><span data-stu-id="9ccd7-110">Component</span></span>|<span data-ttu-id="9ccd7-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="9ccd7-111">SQLEngine</span></span>|  
|<span data-ttu-id="9ccd7-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="9ccd7-112">Symbolic Name</span></span>|<span data-ttu-id="9ccd7-113">DBCC2_FS_INVALID_ROWSET_DIRECTORY</span><span class="sxs-lookup"><span data-stu-id="9ccd7-113">DBCC2_FS_INVALID_ROWSET_DIRECTORY</span></span>|  
|<span data-ttu-id="9ccd7-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="9ccd7-114">Message Text</span></span>|<span data-ttu-id="9ccd7-115">資料庫錯誤:目錄 'DIRECTORY' 不是有效的 Filestream 目錄。</span><span class="sxs-lookup"><span data-stu-id="9ccd7-115">Database error: The directory 'DIRECTORY' is not a valid Filestream directory.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="9ccd7-116">說明</span><span class="sxs-lookup"><span data-stu-id="9ccd7-116">Explanation</span></span>  
 <span data-ttu-id="9ccd7-117">除了特殊的資料列集目錄名稱 (例如 'ghost') 以外，資料列集目錄的名稱都是分割區的分割區識別碼。</span><span class="sxs-lookup"><span data-stu-id="9ccd7-117">The name of a rowset directory is the partition ID of the partition, except for the special rowset directory names such as 'ghost'.</span></span> <span data-ttu-id="9ccd7-118">如果無法將資料列集目錄名稱轉換成分割區識別碼，則表示該目錄不是有效的資料列集目錄。</span><span class="sxs-lookup"><span data-stu-id="9ccd7-118">If a rowset directory name cannot be converted to a partition ID, the directory is not a valid rowset directory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="9ccd7-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="9ccd7-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="9ccd7-120">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="9ccd7-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="9ccd7-121">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="9ccd7-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="9ccd7-122">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="9ccd7-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="9ccd7-123">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="9ccd7-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="9ccd7-124">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="9ccd7-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="9ccd7-125">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="9ccd7-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="9ccd7-126">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="9ccd7-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="9ccd7-127">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="9ccd7-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="9ccd7-128">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="9ccd7-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="9ccd7-129">還原備份</span><span class="sxs-lookup"><span data-stu-id="9ccd7-129">Restore from Backup</span></span>  
 <span data-ttu-id="9ccd7-130">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="9ccd7-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="9ccd7-131">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="9ccd7-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="9ccd7-132">不適用。</span><span class="sxs-lookup"><span data-stu-id="9ccd7-132">Not applicable.</span></span> <span data-ttu-id="9ccd7-133">此錯誤無法修復。</span><span class="sxs-lookup"><span data-stu-id="9ccd7-133">This error cannot be repaired.</span></span> <span data-ttu-id="9ccd7-134">如果無法從備份還原資料庫，請連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務及支援中心 (CSS)。</span><span class="sxs-lookup"><span data-stu-id="9ccd7-134">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
