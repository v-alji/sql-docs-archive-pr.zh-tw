---
title: MSSQLSERVER_2522 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2522 (Database Engine error)
ms.assetid: 19b9b00c-330f-4dd3-9052-9d88bce83849
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 60446c21599c02ee9c4bc96789b106b49b71582a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585473"
---
# <a name="mssqlserver_2522"></a><span data-ttu-id="3629a-102">MSSQLSERVER_2522</span><span class="sxs-lookup"><span data-stu-id="3629a-102">MSSQLSERVER_2522</span></span>
    
## <a name="details"></a><span data-ttu-id="3629a-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="3629a-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="3629a-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="3629a-104">Product Name</span></span>|<span data-ttu-id="3629a-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="3629a-105">SQL Server</span></span>|  
|<span data-ttu-id="3629a-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="3629a-106">Event ID</span></span>|<span data-ttu-id="3629a-107">2522</span><span class="sxs-lookup"><span data-stu-id="3629a-107">2522</span></span>|  
|<span data-ttu-id="3629a-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="3629a-108">Event Source</span></span>|<span data-ttu-id="3629a-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="3629a-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="3629a-110">元件</span><span class="sxs-lookup"><span data-stu-id="3629a-110">Component</span></span>|<span data-ttu-id="3629a-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="3629a-111">SQLEngine</span></span>|  
|<span data-ttu-id="3629a-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="3629a-112">Symbolic Name</span></span>|<span data-ttu-id="3629a-113">DBCC_INDEX_FILEGROUP_IS_INVALID</span><span class="sxs-lookup"><span data-stu-id="3629a-113">DBCC_INDEX_FILEGROUP_IS_INVALID</span></span>|  
|<span data-ttu-id="3629a-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="3629a-114">Message Text</span></span>|<span data-ttu-id="3629a-115">檔案群組 F_NAME 無效，因此無法處理資料表 O_NAME 的索引 I_NAME。</span><span class="sxs-lookup"><span data-stu-id="3629a-115">Unable to process index I_NAME of table O_NAME because filegroup F_NAME is invalid.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="3629a-116">說明</span><span class="sxs-lookup"><span data-stu-id="3629a-116">Explanation</span></span>  
 <span data-ttu-id="3629a-117">這項參考用訊息指出由於儲存在索引中繼資料的其中一個檔案群組識別碼不存在，因此無法檢查索引。</span><span class="sxs-lookup"><span data-stu-id="3629a-117">This informational message indicates that the index cannot be checked because one of the filegroup IDs that is stored in the metadata of the index does not exist.</span></span> <span data-ttu-id="3629a-118">無效的檔案群組識別碼可能與資料本身、大型物件 (LOB) 資料或資料列溢位資料有關。</span><span class="sxs-lookup"><span data-stu-id="3629a-118">The filegroup ID that is not valid might pertain to the data itself, or to the large object (LOB) data, or to the row-overflow data.</span></span>  
  
 <span data-ttu-id="3629a-119">如果沒有問題，則會檢查相同物件的其他所有索引。</span><span class="sxs-lookup"><span data-stu-id="3629a-119">If there are no problems, all other indexes of the same object will be checked.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="3629a-120">使用者動作</span><span class="sxs-lookup"><span data-stu-id="3629a-120">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="3629a-121">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="3629a-121">Look for Hardware Failure</span></span>  
 <span data-ttu-id="3629a-122">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="3629a-122">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="3629a-123">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="3629a-123">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="3629a-124">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="3629a-124">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="3629a-125">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="3629a-125">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="3629a-126">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="3629a-126">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="3629a-127">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="3629a-127">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="3629a-128">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="3629a-128">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="3629a-129">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="3629a-129">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="3629a-130">還原備份</span><span class="sxs-lookup"><span data-stu-id="3629a-130">Restore from Backup</span></span>  
 <span data-ttu-id="3629a-131">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="3629a-131">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="3629a-132">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="3629a-132">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="3629a-133">不適用。</span><span class="sxs-lookup"><span data-stu-id="3629a-133">Not applicable.</span></span> <span data-ttu-id="3629a-134">此錯誤無法自動修復。</span><span class="sxs-lookup"><span data-stu-id="3629a-134">This error cannot be repaired automatically.</span></span>  
  
  
