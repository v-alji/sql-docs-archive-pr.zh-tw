---
title: MSSQLSERVER_7904 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7904 (Database Engine error)
ms.assetid: d047920c-f864-4338-b15f-49820886fbc5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: f5e7be2e8413bc0267a642360da66a6a9ec0de8f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596006"
---
# <a name="mssqlserver_7904"></a><span data-ttu-id="f9d69-102">MSSQLSERVER_7904</span><span class="sxs-lookup"><span data-stu-id="f9d69-102">MSSQLSERVER_7904</span></span>
    
## <a name="details"></a><span data-ttu-id="f9d69-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f9d69-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f9d69-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f9d69-104">Product Name</span></span>|<span data-ttu-id="f9d69-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f9d69-105">SQL Server</span></span>|  
|<span data-ttu-id="f9d69-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f9d69-106">Event ID</span></span>|<span data-ttu-id="f9d69-107">7904</span><span class="sxs-lookup"><span data-stu-id="f9d69-107">7904</span></span>|  
|<span data-ttu-id="f9d69-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="f9d69-108">Event Source</span></span>|<span data-ttu-id="f9d69-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f9d69-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f9d69-110">元件</span><span class="sxs-lookup"><span data-stu-id="f9d69-110">Component</span></span>|<span data-ttu-id="f9d69-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f9d69-111">SQLEngine</span></span>|  
|<span data-ttu-id="f9d69-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f9d69-112">Symbolic Name</span></span>|<span data-ttu-id="f9d69-113">DBCC2_FS_MISSING_FILE</span><span class="sxs-lookup"><span data-stu-id="f9d69-113">DBCC2_FS_MISSING_FILE</span></span>|  
|<span data-ttu-id="f9d69-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f9d69-114">Message Text</span></span>|<span data-ttu-id="f9d69-115">資料表錯誤：在物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID 中找不到資料行識別碼 C_ID，ROWGUID RG_ID 的 filestream 檔案。</span><span class="sxs-lookup"><span data-stu-id="f9d69-115">Table error: The filestream file for column ID C_ID, ROWGUID RG_ID in object ID O_ID, index ID I_ID, partition ID PN_ID was not found.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f9d69-116">說明</span><span class="sxs-lookup"><span data-stu-id="f9d69-116">Explanation</span></span>  
 <span data-ttu-id="f9d69-117">分割區的資料行值在對應的 FILESTREAM 資料行目錄中沒有相符的 FILESTREAM 檔案。</span><span class="sxs-lookup"><span data-stu-id="f9d69-117">A column value of a partition does not have a matching FILESTREAM file in the corresponding FILESTREAM column directory.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f9d69-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f9d69-118">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="f9d69-119">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="f9d69-119">Look for Hardware Failure</span></span>  
 <span data-ttu-id="f9d69-120">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="f9d69-120">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="f9d69-121">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="f9d69-121">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="f9d69-122">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="f9d69-122">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="f9d69-123">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="f9d69-123">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="f9d69-124">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="f9d69-124">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="f9d69-125">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="f9d69-125">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="f9d69-126">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="f9d69-126">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="f9d69-127">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="f9d69-127">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="f9d69-128">還原備份</span><span class="sxs-lookup"><span data-stu-id="f9d69-128">Restore from Backup</span></span>  
 <span data-ttu-id="f9d69-129">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="f9d69-129">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="f9d69-130">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="f9d69-130">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="f9d69-131">不適用。</span><span class="sxs-lookup"><span data-stu-id="f9d69-131">Not applicable.</span></span> <span data-ttu-id="f9d69-132">此錯誤無法修復。</span><span class="sxs-lookup"><span data-stu-id="f9d69-132">This error cannot be repaired.</span></span> <span data-ttu-id="f9d69-133">如果無法從備份還原資料庫，請連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務及支援中心 (CSS)。</span><span class="sxs-lookup"><span data-stu-id="f9d69-133">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
