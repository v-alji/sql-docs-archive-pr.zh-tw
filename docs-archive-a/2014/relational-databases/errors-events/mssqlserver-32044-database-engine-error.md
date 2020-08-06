---
title: MSSQLSERVER_32044 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32044 (Database Engine error)
ms.assetid: f2d073be-d9a1-4837-8a38-028d3e3403bd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 27d9655c3a908f1302f048c6f68159d4f610367a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595075"
---
# <a name="mssqlserver_32044"></a><span data-ttu-id="2b8d4-102">MSSQLSERVER_32044</span><span class="sxs-lookup"><span data-stu-id="2b8d4-102">MSSQLSERVER_32044</span></span>
    
## <a name="details"></a><span data-ttu-id="2b8d4-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="2b8d4-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="2b8d4-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="2b8d4-104">Product Name</span></span>|<span data-ttu-id="2b8d4-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="2b8d4-105">SQL Server</span></span>|  
|<span data-ttu-id="2b8d4-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="2b8d4-106">Event ID</span></span>|<span data-ttu-id="2b8d4-107">32044</span><span class="sxs-lookup"><span data-stu-id="2b8d4-107">32044</span></span>|  
|<span data-ttu-id="2b8d4-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="2b8d4-108">Event Source</span></span>|<span data-ttu-id="2b8d4-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="2b8d4-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="2b8d4-110">元件</span><span class="sxs-lookup"><span data-stu-id="2b8d4-110">Component</span></span>|<span data-ttu-id="2b8d4-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="2b8d4-111">SQLEngine</span></span>|  
|<span data-ttu-id="2b8d4-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="2b8d4-112">Symbolic Name</span></span>|<span data-ttu-id="2b8d4-113">SQLErrorNum32044</span><span class="sxs-lookup"><span data-stu-id="2b8d4-113">SQLErrorNum32044</span></span>|  
|<span data-ttu-id="2b8d4-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="2b8d4-114">Message Text</span></span>|<span data-ttu-id="2b8d4-115">已發出 [鏡像認可負擔] 的警示。</span><span class="sxs-lookup"><span data-stu-id="2b8d4-115">The alert for 'mirror commit overhead' has been raised.</span></span> <span data-ttu-id="2b8d4-116">目前的值 '%d' 已超出臨界值 '%d'。</span><span class="sxs-lookup"><span data-stu-id="2b8d4-116">The current value of '%d' surpasses the threshold '%d'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="2b8d4-117">說明</span><span class="sxs-lookup"><span data-stu-id="2b8d4-117">Explanation</span></span>  
 <span data-ttu-id="2b8d4-118">這個資料庫鏡像事件是在主體伺服器執行個體上發出，用來指示由於資料庫鏡像，彙總認可等待時間已達到或超出使用者指定的臨界值。</span><span class="sxs-lookup"><span data-stu-id="2b8d4-118">This database mirroring event is issued on the principal server instance to indicate that the aggregate commit wait time reached or exceeded a user-specified threshold value because of database mirroring.</span></span> <span data-ttu-id="2b8d4-119">等待時間是交易數目和各交易時間的乘積。</span><span class="sxs-lookup"><span data-stu-id="2b8d4-119">The wait time is the product of the number of transactions and the time of each.</span></span> <span data-ttu-id="2b8d4-120">例如，下列情況都會產生 1000 毫秒的等待時間：1000 筆交易 \* 1 毫秒，以及 1 筆交易 \* 1000 毫秒。</span><span class="sxs-lookup"><span data-stu-id="2b8d4-120">For example, the following cases both produce 1000 milliseconds of wait time: 1000 transactions \* 1 millisecond, and 1 transaction \* 1000 milliseconds.</span></span> <span data-ttu-id="2b8d4-121">交易計數激增、傳送記錄延遲，或是排清鏡像伺服器執行個體上的記錄延遲，都可能會使認可等待時間增加。</span><span class="sxs-lookup"><span data-stu-id="2b8d4-121">An increased commit wait time can be caused by a surge in the transaction count, delays in sending the log, or delays in flushing the log on the mirror server instance.</span></span>  
  
 <span data-ttu-id="2b8d4-122">鏡像認可負擔量是一項效能標準，可協助您評估目前同步作業的效能衝擊。</span><span class="sxs-lookup"><span data-stu-id="2b8d4-122">The amount of mirror commit overhead is a performance metric that can help you evaluate the current performance impact of synchronous operation.</span></span> <span data-ttu-id="2b8d4-123">這項標準只有在高安全性模式中才會相關。</span><span class="sxs-lookup"><span data-stu-id="2b8d4-123">This metric is relevant only in high-safety mode.</span></span> <span data-ttu-id="2b8d4-124">由於高安全性模式是同步的，主體伺服器執行個體會在傳送記錄給鏡像伺服器執行個體之後，等待認可交易，直到接到鏡像伺服器執行個體已將記錄寫入磁碟的確認為止。</span><span class="sxs-lookup"><span data-stu-id="2b8d4-124">Because high-safety mode is synchronous, the principal server instance waits to commit the transaction after it sends a log record to the mirror server instance until it receives confirmation that the mirror server instance has written the log record to disk.</span></span> <span data-ttu-id="2b8d4-125">在等待還原至鏡像資料庫的同時，記錄會一直保留在鏡像伺服器執行個體的磁碟上。</span><span class="sxs-lookup"><span data-stu-id="2b8d4-125">The log record remains on disk on the mirror server instance while it waits to be restored to the mirror database.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="2b8d4-126">使用者動作</span><span class="sxs-lookup"><span data-stu-id="2b8d4-126">User Action</span></span>  
 <span data-ttu-id="2b8d4-127">檢查主體和鏡像伺服器執行個體上的負載及其網路連接，以了解發生原因。</span><span class="sxs-lookup"><span data-stu-id="2b8d4-127">Check the loads on the principal and mirror server instances and their network connection for the cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b8d4-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b8d4-128">See Also</span></span>  
 <span data-ttu-id="2b8d4-129">[資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="2b8d4-129">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="2b8d4-130">使用鏡像效能標準的警告臨界值與警示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="2b8d4-130">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
