---
title: MSSQLSERVER_2540 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 2540 (Database Engine error)
ms.assetid: eb5ee2be-acbb-4fb7-9b45-dc6200bde06e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 4a49abeadcd49263ea7d0701ee468a36882179cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687917"
---
# <a name="mssqlserver_2540"></a><span data-ttu-id="e96ec-102">MSSQLSERVER_2540</span><span class="sxs-lookup"><span data-stu-id="e96ec-102">MSSQLSERVER_2540</span></span>
    
## <a name="details"></a><span data-ttu-id="e96ec-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="e96ec-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="e96ec-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="e96ec-104">Product Name</span></span>|<span data-ttu-id="e96ec-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="e96ec-105">SQL Server</span></span>|  
|<span data-ttu-id="e96ec-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="e96ec-106">Event ID</span></span>|<span data-ttu-id="e96ec-107">2540</span><span class="sxs-lookup"><span data-stu-id="e96ec-107">2540</span></span>|  
|<span data-ttu-id="e96ec-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="e96ec-108">Event Source</span></span>|<span data-ttu-id="e96ec-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="e96ec-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="e96ec-110">元件</span><span class="sxs-lookup"><span data-stu-id="e96ec-110">Component</span></span>|<span data-ttu-id="e96ec-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="e96ec-111">SQLEngine</span></span>|  
|<span data-ttu-id="e96ec-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="e96ec-112">Symbolic Name</span></span>|<span data-ttu-id="e96ec-113">DBCC_REPAIR_ERROR_NOT_REPAIRABLE</span><span class="sxs-lookup"><span data-stu-id="e96ec-113">DBCC_REPAIR_ERROR_NOT_REPAIRABLE</span></span>|  
|<span data-ttu-id="e96ec-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="e96ec-114">Message Text</span></span>|<span data-ttu-id="e96ec-115">系統無法自行修復這個錯誤。</span><span class="sxs-lookup"><span data-stu-id="e96ec-115">The system cannot self repair this error.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="e96ec-116">說明</span><span class="sxs-lookup"><span data-stu-id="e96ec-116">Explanation</span></span>  
 <span data-ttu-id="e96ec-117">此錯誤訊息指出無法自動修復的問題，例如中繼資料損毀、分頁可用空間 (Page Free Space，PFS) 頁面損毀，或特定關鍵系統基底資料表損毀。</span><span class="sxs-lookup"><span data-stu-id="e96ec-117">This error message indicates problems that cannot be repaired automatically, such as corrupt metadata, Page Free Space (PFS) page corruptions, or corruptions in certain critical system base tables.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="e96ec-118">使用者動作</span><span class="sxs-lookup"><span data-stu-id="e96ec-118">User Action</span></span>  
  
### <a name="look-for-hardware-failure"></a><span data-ttu-id="e96ec-119">尋找硬體故障</span><span class="sxs-lookup"><span data-stu-id="e96ec-119">Look for Hardware Failure</span></span>  
 <span data-ttu-id="e96ec-120">請執行硬體診斷並更正所有問題，</span><span class="sxs-lookup"><span data-stu-id="e96ec-120">Run hardware diagnostics and correct any problems.</span></span> <span data-ttu-id="e96ec-121">同時檢查 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 系統和應用程式記錄檔以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 錯誤記錄檔，以查看錯誤發生的原因是否為硬體故障。</span><span class="sxs-lookup"><span data-stu-id="e96ec-121">Also examine the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows system and application logs and the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] error log to see whether the error occurred as the result of hardware failure.</span></span> <span data-ttu-id="e96ec-122">請修正前述記錄檔中所包含的任何硬體相關問題。</span><span class="sxs-lookup"><span data-stu-id="e96ec-122">Fix any hardware-related problems that are contained in the logs.</span></span>  
  
 <span data-ttu-id="e96ec-123">若有持續發生的資料損毀問題，請嘗試抽換不同的硬體元件以隔離問題。</span><span class="sxs-lookup"><span data-stu-id="e96ec-123">If you have persistent data corruption problems, try to swap out different hardware components to isolate the problem.</span></span> <span data-ttu-id="e96ec-124">請檢查以確認系統並未啟用磁碟控制器上的寫入快取功能。</span><span class="sxs-lookup"><span data-stu-id="e96ec-124">Check to make sure that the system does not have write-caching enabled on the disk controller.</span></span> <span data-ttu-id="e96ec-125">如果您懷疑寫入快取就是問題所在，請與您的硬體廠商連絡。</span><span class="sxs-lookup"><span data-stu-id="e96ec-125">If you suspect write-caching to be the problem, contact your hardware vendor.</span></span>  
  
 <span data-ttu-id="e96ec-126">最後，切換到新的硬體系統可能也會有幫助。</span><span class="sxs-lookup"><span data-stu-id="e96ec-126">Finally, you might find it useful to switch to a new hardware system.</span></span> <span data-ttu-id="e96ec-127">此切換作業可能包括重新格式化磁碟機以及重新安裝作業系統。</span><span class="sxs-lookup"><span data-stu-id="e96ec-127">This switch may include reformatting the disk drives and reinstalling the operating system.</span></span>  
  
### <a name="restore-from-backup"></a><span data-ttu-id="e96ec-128">還原備份</span><span class="sxs-lookup"><span data-stu-id="e96ec-128">Restore from Backup</span></span>  
 <span data-ttu-id="e96ec-129">如果問題與硬體無關，而且確定有未受影響的備份可以使用，請利用該備份來還原資料庫。</span><span class="sxs-lookup"><span data-stu-id="e96ec-129">If the problem is not hardware related and a known clean backup is available, restore the database from the backup.</span></span>  
  
### <a name="run-dbcc-checkdb"></a><span data-ttu-id="e96ec-130">執行 DBCC CHECKDB</span><span class="sxs-lookup"><span data-stu-id="e96ec-130">Run DBCC CHECKDB</span></span>  
 <span data-ttu-id="e96ec-131">不適用。</span><span class="sxs-lookup"><span data-stu-id="e96ec-131">Not applicable.</span></span> <span data-ttu-id="e96ec-132">此錯誤無法自動修復。</span><span class="sxs-lookup"><span data-stu-id="e96ec-132">This error cannot be repaired automatically.</span></span>  
  
  
