---
title: MSSQLSERVER_825 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 825 (Database Engine error)
ms.assetid: f69f8214-5af1-4769-878b-117ad6eaff52
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 3b17dfac371ad3c805fdbb0b5d3269fc451dd9d1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595055"
---
# <a name="mssqlserver_825"></a><span data-ttu-id="aa9ca-102">MSSQLSERVER_825</span><span class="sxs-lookup"><span data-stu-id="aa9ca-102">MSSQLSERVER_825</span></span>
    
## <a name="details"></a><span data-ttu-id="aa9ca-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="aa9ca-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="aa9ca-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="aa9ca-104">Product Name</span></span>|<span data-ttu-id="aa9ca-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="aa9ca-105">SQL Server</span></span>|  
|<span data-ttu-id="aa9ca-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="aa9ca-106">Event ID</span></span>|<span data-ttu-id="aa9ca-107">825</span><span class="sxs-lookup"><span data-stu-id="aa9ca-107">825</span></span>|  
|<span data-ttu-id="aa9ca-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="aa9ca-108">Event Source</span></span>|<span data-ttu-id="aa9ca-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="aa9ca-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="aa9ca-110">元件</span><span class="sxs-lookup"><span data-stu-id="aa9ca-110">Component</span></span>|<span data-ttu-id="aa9ca-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="aa9ca-111">SQLEngine</span></span>|  
|<span data-ttu-id="aa9ca-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="aa9ca-112">Symbolic Name</span></span>|<span data-ttu-id="aa9ca-113">B_RETRYWORKED</span><span class="sxs-lookup"><span data-stu-id="aa9ca-113">B_RETRYWORKED</span></span>|  
|<span data-ttu-id="aa9ca-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="aa9ca-114">Message Text</span></span>|<span data-ttu-id="aa9ca-115">在位移 %#016I64x 之檔案 '%ls' 的讀取已成功，但之前已經失敗過 %d 次，錯誤為: %ls。</span><span class="sxs-lookup"><span data-stu-id="aa9ca-115">A read of the file '%ls' at offset %#016I64x succeeded after failing %d time(s) with error: %ls.</span></span> <span data-ttu-id="aa9ca-116">SQL Server 錯誤記錄檔和系統事件記錄檔中的訊息或許可以提供其他詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="aa9ca-116">Additional messages in the SQL Server error log and system event log may provide more detail.</span></span> <span data-ttu-id="aa9ca-117">這個錯誤狀況可能會損及資料庫的完整性，所以必須更正。</span><span class="sxs-lookup"><span data-stu-id="aa9ca-117">This error condition threatens database integrity and must be corrected.</span></span> <span data-ttu-id="aa9ca-118">請執行完整的資料庫一致性檢查 (DBCC CHECKDB)。</span><span class="sxs-lookup"><span data-stu-id="aa9ca-118">Complete a full database consistency check (DBCC CHECKDB).</span></span> <span data-ttu-id="aa9ca-119">導致這個錯誤的原因有許多可能性; 如需詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="aa9ca-119">This error can be caused by many factors; for more information, see SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="aa9ca-120">說明</span><span class="sxs-lookup"><span data-stu-id="aa9ca-120">Explanation</span></span>  
 <span data-ttu-id="aa9ca-121">這個訊息表示讀取作業必須至少重新發出一次，也表示磁碟硬體發生嚴重問題。</span><span class="sxs-lookup"><span data-stu-id="aa9ca-121">This message indicates that the read operation had to be reissued at least one time, and indicates a major problem with the disk hardware.</span></span> <span data-ttu-id="aa9ca-122">這個訊息在目前並不表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 有問題，但是磁碟問題若沒有解決，可能會導致資料遺失或資料庫損毀。</span><span class="sxs-lookup"><span data-stu-id="aa9ca-122">This message does not currently indicate a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] problem, but the disk problem could cause data loss or database corruption if it is not resolved.</span></span> <span data-ttu-id="aa9ca-123">系統事件記錄檔可能包含相關事件，可協助診斷問題所在。</span><span class="sxs-lookup"><span data-stu-id="aa9ca-123">The system event log may contain related events that help to diagnose the problem.</span></span> <span data-ttu-id="aa9ca-124">如需 I/O 錯誤的詳細資訊，請參閱[Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)) (第 2 章 Microsoft SQL Server I/O 基本概念)。</span><span class="sxs-lookup"><span data-stu-id="aa9ca-124">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="aa9ca-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="aa9ca-125">User Action</span></span>  
 <span data-ttu-id="aa9ca-126">下列動作可以協助您找出並解決根本問題：</span><span class="sxs-lookup"><span data-stu-id="aa9ca-126">The following actions may help you identify and resolve the underlying problem:</span></span>  
  
-   <span data-ttu-id="aa9ca-127">檢閱錯誤記錄檔和此訊息中的變數文字，找出能夠解釋問題的線索。</span><span class="sxs-lookup"><span data-stu-id="aa9ca-127">Review the error log and the variable text in this message for clues that explain the problem.</span></span>  
  
-   <span data-ttu-id="aa9ca-128">檢查您的磁碟系統。</span><span class="sxs-lookup"><span data-stu-id="aa9ca-128">Check your disk system.</span></span> <span data-ttu-id="aa9ca-129">問題可能與磁碟、磁碟控制卡、陣列卡，或磁碟驅動程式有關。</span><span class="sxs-lookup"><span data-stu-id="aa9ca-129">The problem could be related to the disks, the disk controllers, array cards, or disk drivers.</span></span>  
  
-   <span data-ttu-id="aa9ca-130">連絡磁碟製造廠商，取得最新的公用程式，以檢查磁碟系統的狀態。</span><span class="sxs-lookup"><span data-stu-id="aa9ca-130">Contact the disk manufacturer for the latest utilities for checking the status of your disk system.</span></span>  
  
-   <span data-ttu-id="aa9ca-131">連絡磁碟製造廠商，取得最新的驅動程式更新。</span><span class="sxs-lookup"><span data-stu-id="aa9ca-131">Contact the disk manufacturer for the latest driver updates.</span></span>  
  
  
