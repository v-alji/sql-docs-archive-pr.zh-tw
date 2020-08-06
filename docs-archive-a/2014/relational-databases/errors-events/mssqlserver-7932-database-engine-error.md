---
title: MSSQLSERVER_7932 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 7932 (Database Engine error)
ms.assetid: e2ad218a-3249-4f18-8b32-09f0030765a5
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 237d9be3e0f22664adb061d3bba526c9878d3bfc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596707"
---
# <a name="mssqlserver_7932"></a><span data-ttu-id="2609f-102">MSSQLSERVER_7932</span><span class="sxs-lookup"><span data-stu-id="2609f-102">MSSQLSERVER_7932</span></span>
    
## <a name="details"></a><span data-ttu-id="2609f-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2609f-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2609f-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2609f-104">Product Name</span></span>|<span data-ttu-id="2609f-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2609f-105">SQL Server</span></span>|  
|<span data-ttu-id="2609f-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2609f-106">Event ID</span></span>|<span data-ttu-id="2609f-107">7932</span><span class="sxs-lookup"><span data-stu-id="2609f-107">7932</span></span>|  
|<span data-ttu-id="2609f-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="2609f-108">Event Source</span></span>|<span data-ttu-id="2609f-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2609f-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2609f-110">元件</span><span class="sxs-lookup"><span data-stu-id="2609f-110">Component</span></span>|<span data-ttu-id="2609f-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2609f-111">SQLEngine</span></span>|  
|<span data-ttu-id="2609f-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2609f-112">Symbolic Name</span></span>|<span data-ttu-id="2609f-113">DBCC2_FS_ROWSET_IN_WRONG_FILEGROUP</span><span class="sxs-lookup"><span data-stu-id="2609f-113">DBCC2_FS_ROWSET_IN_WRONG_FILEGROUP</span></span>|  
|<span data-ttu-id="2609f-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2609f-114">Message Text</span></span>|<span data-ttu-id="2609f-115">資料表錯誤：物件識別碼 O_ID，索引識別碼 I_ID，分割區識別碼 PN_ID 的 FileStream 目錄識別碼 F_ID 在檔案群組 FG_ID1 中，但應該要在檔案群組 FG_ID2 中。</span><span class="sxs-lookup"><span data-stu-id="2609f-115">Table error: The FileStream directory ID F_ID for object ID O_ID, index ID I_ID, partition ID PN_ID is in filegroup FG_ID1, but should be in filegroup FG_ID2.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2609f-116">說明</span><span class="sxs-lookup"><span data-stu-id="2609f-116">Explanation</span></span>  
 <span data-ttu-id="2609f-117">在 DBCC CHECKDB 執行期間，在錯誤的檔案群組中偵測到指定之物件的 FILESTREAM 儲存體。</span><span class="sxs-lookup"><span data-stu-id="2609f-117">During DBCC CHECKDB, the FILESTREAM storage for the specified object was detected in the wrong filegroup.</span></span> <span data-ttu-id="2609f-118">這可能是資料庫的中繼資料毀損。</span><span class="sxs-lookup"><span data-stu-id="2609f-118">This could be a corruption in the metadata of the object.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2609f-119">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2609f-119">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="2609f-120">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="2609f-120">Look for Hardware Failure</span></span>  
 <span data-ttu-id="2609f-121">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="2609f-121">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="2609f-122">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="2609f-122">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="2609f-123">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="2609f-123">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="2609f-124">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="2609f-124">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="2609f-125">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="2609f-125">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="2609f-126">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="2609f-126">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="2609f-127">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="2609f-127">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="2609f-128">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="2609f-128">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="2609f-129">還原備份</span><span class="sxs-lookup"><span data-stu-id="2609f-129">Restore from Backup</span></span>  
 <span data-ttu-id="2609f-130">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="2609f-130">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="2609f-131">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="2609f-131">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="2609f-132">不適用。</span><span class="sxs-lookup"><span data-stu-id="2609f-132">Not applicable.</span></span> <span data-ttu-id="2609f-133">此錯誤無法自動修復。</span><span class="sxs-lookup"><span data-stu-id="2609f-133">This error cannot be repaired automatically.</span></span> <span data-ttu-id="2609f-134">如果無法從備份還原資料庫，請連絡 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 客戶服務及支援中心 (CSS)。</span><span class="sxs-lookup"><span data-stu-id="2609f-134">If you cannot restore the database from a backup, contact [!INCLUDE[msCoName](../../includes/msconame-md.md)] Customer Service and Support (CSS).</span></span>  
  
  
