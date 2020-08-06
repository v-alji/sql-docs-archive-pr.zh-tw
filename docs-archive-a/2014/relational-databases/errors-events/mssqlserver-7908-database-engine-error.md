---
title: MSSQLSERVER_7908 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7908 (Database Engine error)
ms.assetid: 470045b0-ebe9-44a7-b456-480e7a516a2c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: b80812e0e36e5bed542f7193b7422f2de37720f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596001"
---
# <a name="mssqlserver_7908"></a><span data-ttu-id="ee237-102">MSSQLSERVER_7908</span><span class="sxs-lookup"><span data-stu-id="ee237-102">MSSQLSERVER_7908</span></span>
    
## <a name="details"></a><span data-ttu-id="ee237-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="ee237-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="ee237-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="ee237-104">Product Name</span></span>|<span data-ttu-id="ee237-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="ee237-105">SQL Server</span></span>|  
|<span data-ttu-id="ee237-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="ee237-106">Event ID</span></span>|<span data-ttu-id="ee237-107">7908</span><span class="sxs-lookup"><span data-stu-id="ee237-107">7908</span></span>|  
|<span data-ttu-id="ee237-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="ee237-108">Event Source</span></span>|<span data-ttu-id="ee237-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="ee237-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="ee237-110">元件</span><span class="sxs-lookup"><span data-stu-id="ee237-110">Component</span></span>|<span data-ttu-id="ee237-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="ee237-111">SQLEngine</span></span>|  
|<span data-ttu-id="ee237-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="ee237-112">Symbolic Name</span></span>|<span data-ttu-id="ee237-113">DBCC2_FS_INVALID_COLUMN_LEVEL_FILE</span><span class="sxs-lookup"><span data-stu-id="ee237-113">DBCC2_FS_INVALID_COLUMN_LEVEL_FILE</span></span>|  
|<span data-ttu-id="ee237-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="ee237-114">Message Text</span></span>|<span data-ttu-id="ee237-115">資料表錯誤：在分割區識別碼 PN_ID 中的檔案 'FILE' 不是有效 Filestream 檔案。</span><span class="sxs-lookup"><span data-stu-id="ee237-115">Table error: The file 'FILE' in partition ID PN_ID is not a valid Filestream file.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="ee237-116">說明</span><span class="sxs-lookup"><span data-stu-id="ee237-116">Explanation</span></span>  
 <span data-ttu-id="ee237-117">資料行目錄中 FILESTREAM 檔案的名稱是 ROWGUID。</span><span class="sxs-lookup"><span data-stu-id="ee237-117">The name of a FILESTREAM file in a column directory is a ROWGUID.</span></span> <span data-ttu-id="ee237-118">如果無法將資料行目錄中的檔案名稱轉換成 ROWGUID，則表示該檔案不是有效的檔案。</span><span class="sxs-lookup"><span data-stu-id="ee237-118">If a file name in a column directory cannot be converted to a ROWGUID, the file is not a valid file.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="ee237-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="ee237-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="ee237-120">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="ee237-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="ee237-121">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="ee237-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="ee237-122">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="ee237-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="ee237-123">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="ee237-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="ee237-124">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="ee237-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="ee237-125">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="ee237-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="ee237-126">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="ee237-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="ee237-127">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="ee237-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="ee237-128">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="ee237-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="ee237-129">還原備份</span><span class="sxs-lookup"><span data-stu-id="ee237-129">Restore from Backup</span></span>  
 <span data-ttu-id="ee237-130">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="ee237-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="ee237-131">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="ee237-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="ee237-132">不適用。</span><span class="sxs-lookup"><span data-stu-id="ee237-132">Not applicable.</span></span> <span data-ttu-id="ee237-133">此錯誤無法修復。</span><span class="sxs-lookup"><span data-stu-id="ee237-133">This error cannot be repaired.</span></span> <span data-ttu-id="ee237-134">如果無法從備份還原資料庫，請連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務及支援中心 (CSS)。</span><span class="sxs-lookup"><span data-stu-id="ee237-134">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
