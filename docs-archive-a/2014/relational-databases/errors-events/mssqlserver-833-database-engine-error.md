---
title: MSSQLSERVER_833 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 833 (Database Engine error)
ms.assetid: 14129cc4-be80-4772-9e3f-0e5da4d0696b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 8e20018c0fe1cd0748f4930e0022622adcbfad10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595988"
---
# <a name="mssqlserver_833"></a><span data-ttu-id="16546-102">MSSQLSERVER_833</span><span class="sxs-lookup"><span data-stu-id="16546-102">MSSQLSERVER_833</span></span>
    
## <a name="details"></a><span data-ttu-id="16546-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="16546-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="16546-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="16546-104">Product Name</span></span>|<span data-ttu-id="16546-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="16546-105">SQL Server</span></span>|  
|<span data-ttu-id="16546-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="16546-106">Event ID</span></span>|<span data-ttu-id="16546-107">833</span><span class="sxs-lookup"><span data-stu-id="16546-107">833</span></span>|  
|<span data-ttu-id="16546-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="16546-108">Event Source</span></span>|<span data-ttu-id="16546-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="16546-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="16546-110">元件</span><span class="sxs-lookup"><span data-stu-id="16546-110">Component</span></span>|<span data-ttu-id="16546-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="16546-111">SQLEngine</span></span>|  
|<span data-ttu-id="16546-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="16546-112">Symbolic Name</span></span>|<span data-ttu-id="16546-113">BUF_LONG_IO</span><span class="sxs-lookup"><span data-stu-id="16546-113">BUF_LONG_IO</span></span>|  
|<span data-ttu-id="16546-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="16546-114">Message Text</span></span>|<span data-ttu-id="16546-115">SQL Server 在資料庫中的檔案 [% ls] 上發現% d 次發生 (s) 的 i/o 要求超過% d 秒 `[%ls] (%d)` 。</span><span class="sxs-lookup"><span data-stu-id="16546-115">SQL Server has encountered %d occurrence(s) of I/O requests taking longer than %d seconds to complete on file [%ls] in database`[%ls] (%d)`.</span></span>  <span data-ttu-id="16546-116">作業系統檔案控制代碼為 0x%p。</span><span class="sxs-lookup"><span data-stu-id="16546-116">The OS file handle is 0x%p.</span></span>  <span data-ttu-id="16546-117">最新的長 I/O 的位移為: %#016I64x。</span><span class="sxs-lookup"><span data-stu-id="16546-117">The offset of the latest long I/O is: %#016I64x.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="16546-118">說明</span><span class="sxs-lookup"><span data-stu-id="16546-118">Explanation</span></span>  
 <span data-ttu-id="16546-119">此訊息表示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 已經從磁碟發出讀取或寫入要求，且該要求花費超過 15 秒才傳回。</span><span class="sxs-lookup"><span data-stu-id="16546-119">This message indicates that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] has issued a read or write request from disk, and that the request has taken longer than 15 seconds to return.</span></span> <span data-ttu-id="16546-120">此錯誤是由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 回報，並且表示 IO 子系統發生問題。</span><span class="sxs-lookup"><span data-stu-id="16546-120">This error is reported by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and indicates a problem with the IO subsystem.</span></span>  
  
### <a name="possible-causes"></a><span data-ttu-id="16546-121">可能的原因</span><span class="sxs-lookup"><span data-stu-id="16546-121">Possible Causes</span></span>  
 <span data-ttu-id="16546-122">造成此問題的原因可能是系統效能問題、硬體錯誤、韌體錯誤、裝置驅動程式問題，或篩選驅動程式介入 IO 處理序。</span><span class="sxs-lookup"><span data-stu-id="16546-122">This problem can be caused system performance issues, hardware errors, firmware errors, device driver problems, or filter driver intervention in the IO process.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="16546-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="16546-123">User Action</span></span>  
 <span data-ttu-id="16546-124">查看系統事件記錄檔中是否有與硬體相關的錯誤訊息，以便對此錯誤進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="16546-124">Troubleshoot this error by examining the system event log for hardware-related error messages.</span></span> <span data-ttu-id="16546-125">同時，也查看硬體特定的記錄檔 (如果有的話)。</span><span class="sxs-lookup"><span data-stu-id="16546-125">Also, examine hardware-specific logs if they are available.</span></span>  
  
 <span data-ttu-id="16546-126">使用「效能監視器」檢查下列計數器︰</span><span class="sxs-lookup"><span data-stu-id="16546-126">Use Performance Monitor to examine the following counters:</span></span>  
  
-   <span data-ttu-id="16546-127">**Average Disk Sec/Transfer**</span><span class="sxs-lookup"><span data-stu-id="16546-127">**Average Disk Sec/Transfer**</span></span>  
  
-   <span data-ttu-id="16546-128">**Average Disk Queue Length**</span><span class="sxs-lookup"><span data-stu-id="16546-128">**Average Disk Queue Length**</span></span>  
  
-   <span data-ttu-id="16546-129">**Current Disk Queue Length**</span><span class="sxs-lookup"><span data-stu-id="16546-129">**Current Disk Queue Length**</span></span>  
  
 <span data-ttu-id="16546-130">例如，在執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的電腦上，**Average Disk Sec/Transfer** 時間通常少於 15 毫秒。</span><span class="sxs-lookup"><span data-stu-id="16546-130">For example, the **Average Disk Sec/Transfer** time on a computer that is running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is typically less than 15 milliseconds.</span></span> <span data-ttu-id="16546-131">如果 **Average Disk Sec/Transfer** 值增加，表示 I/O 子系統並未以最佳的方式應付 I/O 需要。</span><span class="sxs-lookup"><span data-stu-id="16546-131">If the **Average Disk Sec/Transfer** value increases, this indicates that the I/O subsystem is not optimally keeping up with the I/O demand.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="16546-132">防毒程式可能會降低磁碟存取的速度。</span><span class="sxs-lookup"><span data-stu-id="16546-132">Disk access can be slowed by an antivirus program.</span></span> <span data-ttu-id="16546-133">若要加快存取速度，請從使用中的病毒掃描排除錯誤訊息中所指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料檔案。</span><span class="sxs-lookup"><span data-stu-id="16546-133">To increase access speed, exclude the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data files that are specified in the error message from active virus scans.</span></span>  
  
 <span data-ttu-id="16546-134">如需 I/O 錯誤的詳細資訊，請參閱 [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)) (第 2 章 Microsoft SQL Server I/O 基本概念) 以及 [https://support.microsoft.com/kb/897284](https://support.microsoft.com/kb/897284) 的知識庫文章。</span><span class="sxs-lookup"><span data-stu-id="16546-134">For more information about I/O errors, see [Microsoft SQL Server I/O Basics, Chapter 2](/previous-versions/sql/sql-server-2005/administrator/cc917726(v=technet.10)) and the Knowledge Base article at [https://support.microsoft.com/kb/897284](https://support.microsoft.com/kb/897284).</span></span>  
  
  
