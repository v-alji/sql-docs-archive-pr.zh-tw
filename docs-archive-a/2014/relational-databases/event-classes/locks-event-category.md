---
title: Locks 事件類別目錄 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- Locks event category [SQL Server]
- SQL Server event classes, Locks event category
- event classes [SQL Server], Locks event category
- lock escalation [SQL Server], locks event category
ms.assetid: 27d6afa2-7dab-4fe7-a1ad-064b879dc654
author: stevestein
ms.author: sstein
ms.openlocfilehash: 3a202279021e3e6c7c3c44a167792bb9439567aa
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592697"
---
# <a name="locks-event-category"></a><span data-ttu-id="5f1ce-102">Locks 事件類別目錄</span><span class="sxs-lookup"><span data-stu-id="5f1ce-102">Locks Event Category</span></span>
  <span data-ttu-id="5f1ce-103">使用 **Locks** 事件類別目錄中事件類別來監視 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] 執行個體中的鎖定活動。</span><span class="sxs-lookup"><span data-stu-id="5f1ce-103">Use the event classes in the **Locks** event category to monitor locking activity in an instance of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="5f1ce-104">這些事件類別可協助您調查，因多位使用者同時讀取和修改資料而造成的鎖定問題。</span><span class="sxs-lookup"><span data-stu-id="5f1ce-104">These event classes can help you investigate locking problems caused by multiple users reading and modifying data concurrently.</span></span>  
  
 <span data-ttu-id="5f1ce-105">因為「 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 」經常要處理許多鎖定，於追蹤期間擷取 **Locks** 事件類別，會帶來大量負擔，而且導致產生龐大的追蹤檔案或資料表。</span><span class="sxs-lookup"><span data-stu-id="5f1ce-105">Because the [!INCLUDE[ssDE](../../includes/ssde-md.md)] often processes many locks, capturing the **Locks** event classes during a trace can incur significant overhead and result in large trace files or tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5f1ce-106">本節內容</span><span class="sxs-lookup"><span data-stu-id="5f1ce-106">In This Section</span></span>  
  
|<span data-ttu-id="5f1ce-107">主題</span><span class="sxs-lookup"><span data-stu-id="5f1ce-107">Topic</span></span>|<span data-ttu-id="5f1ce-108">描述</span><span class="sxs-lookup"><span data-stu-id="5f1ce-108">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="5f1ce-109">Deadlock Graph 事件類別</span><span class="sxs-lookup"><span data-stu-id="5f1ce-109">Deadlock Graph Event Class</span></span>](deadlock-graph-event-class.md)|<span data-ttu-id="5f1ce-110">提供死結的 XML 描述。</span><span class="sxs-lookup"><span data-stu-id="5f1ce-110">Provides an XML description of a deadlock.</span></span>|  
|[<span data-ttu-id="5f1ce-111">Lock:Acquired 事件類別</span><span class="sxs-lookup"><span data-stu-id="5f1ce-111">Lock:Acquired Event Class</span></span>](lock-acquired-event-class.md)|<span data-ttu-id="5f1ce-112">指出已經在資源上取得鎖定，例如，資料表中的資料列。</span><span class="sxs-lookup"><span data-stu-id="5f1ce-112">Indicates that a lock has been acquired on a resource, such as a row in a table.</span></span>|  
|[<span data-ttu-id="5f1ce-113">Lock:Cancel 事件類別</span><span class="sxs-lookup"><span data-stu-id="5f1ce-113">Lock:Cancel Event Class</span></span>](lock-cancel-event-class.md)|<span data-ttu-id="5f1ce-114">追蹤在取得鎖定之前，已經先取消的鎖定要求 (例如，以避免發生死結)。</span><span class="sxs-lookup"><span data-stu-id="5f1ce-114">Tracks requests for locks that were canceled before the lock was acquired (for example, to prevent a deadlock).</span></span>|  
|[<span data-ttu-id="5f1ce-115">Lock:Deadlock Chain 事件類別</span><span class="sxs-lookup"><span data-stu-id="5f1ce-115">Lock:Deadlock Chain Event Class</span></span>](lock-deadlock-chain-event-class.md)|<span data-ttu-id="5f1ce-116">監視何時發生死結狀況以及牽涉哪些物件。</span><span class="sxs-lookup"><span data-stu-id="5f1ce-116">Monitors when deadlock conditions occur and which objects are involved.</span></span>|  
|[<span data-ttu-id="5f1ce-117">Lock:Deadlock 事件類別</span><span class="sxs-lookup"><span data-stu-id="5f1ce-117">Lock:Deadlock Event Class</span></span>](lock-deadlock-event-class.md)|<span data-ttu-id="5f1ce-118">追蹤交易何時要求鎖定已由其他交易鎖定的資源，而造成死結。</span><span class="sxs-lookup"><span data-stu-id="5f1ce-118">Tracks when a transaction has requested a lock on a resource already locked by another transaction, resulting in a deadlock.</span></span>|  
|[<span data-ttu-id="5f1ce-119">Lock:Escalation 事件類別</span><span class="sxs-lookup"><span data-stu-id="5f1ce-119">Lock:Escalation Event Class</span></span>](lock-escalation-event-class.md)|<span data-ttu-id="5f1ce-120">指出細粒鎖定已經轉換成粗粒鎖定。</span><span class="sxs-lookup"><span data-stu-id="5f1ce-120">Indicates that a finer-grained lock has been converted to a coarser-grained lock.</span></span>|  
|[<span data-ttu-id="5f1ce-121">Lock:Released 事件類別</span><span class="sxs-lookup"><span data-stu-id="5f1ce-121">Lock:Released Event Class</span></span>](lock-released-event-class.md)|<span data-ttu-id="5f1ce-122">追蹤何時釋放鎖定。</span><span class="sxs-lookup"><span data-stu-id="5f1ce-122">Tracks when a lock is released.</span></span>|  
|[<span data-ttu-id="5f1ce-123">Lock:Timeout &#40;timeout &#62; 0&#41; 事件類別</span><span class="sxs-lookup"><span data-stu-id="5f1ce-123">Lock:Timeout &#40;timeout &#62; 0&#41; Event Class</span></span>](lock-timeout-timeout-0-event-class.md)|<span data-ttu-id="5f1ce-124">追蹤何時因為其他交易在所需資源上具有封鎖的鎖定，而無法完成鎖定要求。</span><span class="sxs-lookup"><span data-stu-id="5f1ce-124">Tracks when lock requests cannot be completed because another transaction has a blocking lock on the requested resource.</span></span> <span data-ttu-id="5f1ce-125">只有在鎖定的逾時值大於零的狀況發生時，才會發生此事件。</span><span class="sxs-lookup"><span data-stu-id="5f1ce-125">This event occurs only in situations where the lock time-out value is greater than zero.</span></span>|  
|[<span data-ttu-id="5f1ce-126">Lock:Timeout 事件類別</span><span class="sxs-lookup"><span data-stu-id="5f1ce-126">Lock:Timeout Event Class</span></span>](lock-timeout-event-class.md)|<span data-ttu-id="5f1ce-127">追蹤何時因為其他交易在所需資源上具有封鎖的鎖定，而無法完成鎖定要求。</span><span class="sxs-lookup"><span data-stu-id="5f1ce-127">Tracks when lock requests cannot be completed because another transaction has a blocking lock on the requested resource.</span></span>|  
  
  
