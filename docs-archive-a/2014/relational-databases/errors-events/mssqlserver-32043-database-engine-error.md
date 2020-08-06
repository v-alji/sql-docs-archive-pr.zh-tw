---
title: MSSQLSERVER_32043 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32043 (Database Engine error)
ms.assetid: a0c48ae3-4c8c-419c-afb5-579fcefac01d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 2febc7173c8144451c7a9b0576f2293d5594c6df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585469"
---
# <a name="mssqlserver_32043"></a><span data-ttu-id="00de5-102">MSSQLSERVER_32043</span><span class="sxs-lookup"><span data-stu-id="00de5-102">MSSQLSERVER_32043</span></span>
    
## <a name="details"></a><span data-ttu-id="00de5-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="00de5-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="00de5-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="00de5-104">Product Name</span></span>|<span data-ttu-id="00de5-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="00de5-105">SQL Server</span></span>|  
|<span data-ttu-id="00de5-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="00de5-106">Event ID</span></span>|<span data-ttu-id="00de5-107">32043</span><span class="sxs-lookup"><span data-stu-id="00de5-107">32043</span></span>|  
|<span data-ttu-id="00de5-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="00de5-108">Event Source</span></span>|<span data-ttu-id="00de5-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="00de5-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="00de5-110">元件</span><span class="sxs-lookup"><span data-stu-id="00de5-110">Component</span></span>|<span data-ttu-id="00de5-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="00de5-111">SQLEngine</span></span>|  
|<span data-ttu-id="00de5-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="00de5-112">Symbolic Name</span></span>|<span data-ttu-id="00de5-113">SQLErrorNum32043</span><span class="sxs-lookup"><span data-stu-id="00de5-113">SQLErrorNum32043</span></span>|  
|<span data-ttu-id="00de5-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="00de5-114">Message Text</span></span>|<span data-ttu-id="00de5-115">已發出 [未還原的記錄] 的警示。</span><span class="sxs-lookup"><span data-stu-id="00de5-115">The alert for 'unrestored log' has been raised.</span></span> <span data-ttu-id="00de5-116">目前的值 '%d' 已超出臨界值 '%d'。</span><span class="sxs-lookup"><span data-stu-id="00de5-116">The current value of '%d' surpasses the threshold '%d'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="00de5-117">說明</span><span class="sxs-lookup"><span data-stu-id="00de5-117">Explanation</span></span>  
 <span data-ttu-id="00de5-118">這個資料庫鏡像事件是在鏡像伺服器執行個體上發出，用來指示未還原記錄數量已經到達使用者指定的臨界值。</span><span class="sxs-lookup"><span data-stu-id="00de5-118">This database mirroring event is issued on the mirror server instance to indicate that the amount of unrestored log reached a user-specified threshold value.</span></span> <span data-ttu-id="00de5-119">一般而言，會發生這個事件，是因為系統效能已經變更。</span><span class="sxs-lookup"><span data-stu-id="00de5-119">Typically, this event occurs because the performance of the system has changed.</span></span> <span data-ttu-id="00de5-120">若不是兩個系統間的頻寬已經縮減，就是負載已經增加。</span><span class="sxs-lookup"><span data-stu-id="00de5-120">Either the bandwidth between the two systems has decreased, or the load has increased.</span></span>  
  
 <span data-ttu-id="00de5-121">未還原的記錄是指，已由鏡像伺服器執行個體接收且寫入磁碟，但正等待還原至鏡像資料庫的記錄。</span><span class="sxs-lookup"><span data-stu-id="00de5-121">An unrestored log is a log that has been received by the mirror server instance and written to disk but is waiting to be restored to the mirror database.</span></span> <span data-ttu-id="00de5-122">未還原記錄的數量是以 KB 為單位，可協助您評估目前容錯移轉時間的效能標準。</span><span class="sxs-lookup"><span data-stu-id="00de5-122">The amount of unrestored log in kilobytes (KB) is a performance metric that can help you evaluate the current failover time.</span></span> <span data-ttu-id="00de5-123">容錯移轉所花費最主要的時間是套用未還原的記錄，還有一些零星時間則是用來復原資料庫並讓它上線。</span><span class="sxs-lookup"><span data-stu-id="00de5-123">The time that is required to apply the unrestored log is the main factor in failover time, along with a short additional time that is required to recover the database and bring it online.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="00de5-124">如果是自動容錯移轉，則系統發現錯誤的時間與容錯移轉時間無關。</span><span class="sxs-lookup"><span data-stu-id="00de5-124">For an automatic failover, the time for the system to notice the failure is independent of the failover time.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="00de5-125">使用者動作</span><span class="sxs-lookup"><span data-stu-id="00de5-125">User Action</span></span>  
 <span data-ttu-id="00de5-126">檢查主體和鏡像伺服器執行個體上的負載及其網路連接，以了解發生原因。</span><span class="sxs-lookup"><span data-stu-id="00de5-126">Check the loads on the principal and mirror server instances and their network connection for the cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00de5-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="00de5-127">See Also</span></span>  
 <span data-ttu-id="00de5-128">[資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="00de5-128">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="00de5-129">使用鏡像效能標準的警告臨界值與警示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="00de5-129">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
