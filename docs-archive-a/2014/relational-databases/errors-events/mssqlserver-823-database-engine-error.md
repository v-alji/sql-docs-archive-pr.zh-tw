---
title: MSSQLSERVER_823 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 823 (Database Engine error)
ms.assetid: 0d9fce3c-3772-46ce-a7a3-4f4988dc6cae
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: fa5858bbdc9452a33a3d43fdd783e59556a11e57
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595998"
---
# <a name="mssqlserver_823"></a><span data-ttu-id="1dfde-102">MSSQLSERVER_823</span><span class="sxs-lookup"><span data-stu-id="1dfde-102">MSSQLSERVER_823</span></span>
    
## <a name="details"></a><span data-ttu-id="1dfde-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="1dfde-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="1dfde-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="1dfde-104">Product Name</span></span>|<span data-ttu-id="1dfde-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="1dfde-105">SQL Server</span></span>|  
|<span data-ttu-id="1dfde-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="1dfde-106">Event ID</span></span>|<span data-ttu-id="1dfde-107">823</span><span class="sxs-lookup"><span data-stu-id="1dfde-107">823</span></span>|  
|<span data-ttu-id="1dfde-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="1dfde-108">Event Source</span></span>|<span data-ttu-id="1dfde-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="1dfde-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="1dfde-110">元件</span><span class="sxs-lookup"><span data-stu-id="1dfde-110">Component</span></span>|<span data-ttu-id="1dfde-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="1dfde-111">SQLEngine</span></span>|  
|<span data-ttu-id="1dfde-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="1dfde-112">Symbolic Name</span></span>|<span data-ttu-id="1dfde-113">B_HARDERR</span><span class="sxs-lookup"><span data-stu-id="1dfde-113">B_HARDERR</span></span>|  
|<span data-ttu-id="1dfde-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="1dfde-114">Message Text</span></span>|<span data-ttu-id="1dfde-115">作業系統將錯誤 %ls 傳回給 SQL Server，期間：%S_MSG 在 %#016I64x 位移，檔案：'%ls'。</span><span class="sxs-lookup"><span data-stu-id="1dfde-115">The operating system returned error %ls to SQL Server during a %S_MSG at offset %#016I64x in file '%ls'.</span></span> <span data-ttu-id="1dfde-116">SQL Server 錯誤記錄檔和系統事件記錄檔中的訊息或許可以提供其他詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="1dfde-116">Additional messages in the SQL Server error log and system event log may provide more detail.</span></span> <span data-ttu-id="1dfde-117">這是嚴重的系統層級錯誤狀況，且可能會損及資料庫的完整性，所以必須立即更正。</span><span class="sxs-lookup"><span data-stu-id="1dfde-117">This is a severe system-level error condition that threatens database integrity and must be corrected immediately.</span></span> <span data-ttu-id="1dfde-118">請執行完整的資料庫一致性檢查 (DBCC CHECKDB)。</span><span class="sxs-lookup"><span data-stu-id="1dfde-118">Complete a full database consistency check (DBCC CHECKDB).</span></span> <span data-ttu-id="1dfde-119">導致這個錯誤的原因有許多可能性; 如需詳細資訊，請參閱《SQL Server 線上叢書》。</span><span class="sxs-lookup"><span data-stu-id="1dfde-119">This error can be caused by many factors; for more information, see SQL Server Books Online.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="1dfde-120">說明</span><span class="sxs-lookup"><span data-stu-id="1dfde-120">Explanation</span></span>  
 <span data-ttu-id="1dfde-121">Windows 讀取或寫入要求失敗。</span><span class="sxs-lookup"><span data-stu-id="1dfde-121">A Windows read or write request has failed.</span></span> <span data-ttu-id="1dfde-122">Windows 傳回的錯誤碼和對應的文字都已插入訊息中。</span><span class="sxs-lookup"><span data-stu-id="1dfde-122">The error code that is returned by Windows and the corresponding text are inserted into the message.</span></span> <span data-ttu-id="1dfde-123">在讀取案例中，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已經重試讀取要求四次。</span><span class="sxs-lookup"><span data-stu-id="1dfde-123">In the read case, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] will have already retried the read request four times.</span></span> <span data-ttu-id="1dfde-124">這個錯誤通常是硬體錯誤所造成的結果，但也可能是裝置驅動程式所引起的。</span><span class="sxs-lookup"><span data-stu-id="1dfde-124">This error is often the result of a hardware error, but may be caused by the device driver.</span></span> <span data-ttu-id="1dfde-125">如需錯誤823的詳細資訊，請參閱 [https://support.microsoft.com/kb/828339](https://support.microsoft.com/kb/828339) 。</span><span class="sxs-lookup"><span data-stu-id="1dfde-125">For more information about error 823, see [https://support.microsoft.com/kb/828339](https://support.microsoft.com/kb/828339).</span></span> <span data-ttu-id="1dfde-126">如需 I/O 錯誤的詳細資訊，請參閱[Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)) (第 2 章 Microsoft SQL Server I/O 基本概念)。</span><span class="sxs-lookup"><span data-stu-id="1dfde-126">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)).</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="1dfde-127">使用者動作</span><span class="sxs-lookup"><span data-stu-id="1dfde-127">User Action</span></span>  
 <span data-ttu-id="1dfde-128">查看系統事件記錄檔中的其他資訊，</span><span class="sxs-lookup"><span data-stu-id="1dfde-128">Check for additional information in the system event log.</span></span> <span data-ttu-id="1dfde-129">並連絡硬體製造商或 Microsoft 客戶服務及支援中心，確定其原因與更正動作。</span><span class="sxs-lookup"><span data-stu-id="1dfde-129">Contact the hardware manufacturer or Microsoft Customer Services and Support to determine the cause and corrective action.</span></span> <span data-ttu-id="1dfde-130">更正硬體錯誤之後，請還原所有資料庫並執行 DBCC CHECKDB。</span><span class="sxs-lookup"><span data-stu-id="1dfde-130">After the hardware error is fixed, restore all databases and run DBCC CHECKDB.</span></span>  
  
  
