---
title: MSSQLSERVER_32042 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32042 (Database Engine error)
ms.assetid: 53a51c7a-dcd4-4c15-b4d2-6aaa9dce76da
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bd959d84da2c54310dea5156b1a45b73490211a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595076"
---
# <a name="mssqlserver_32042"></a><span data-ttu-id="38895-102">MSSQLSERVER_32042</span><span class="sxs-lookup"><span data-stu-id="38895-102">MSSQLSERVER_32042</span></span>
    
## <a name="details"></a><span data-ttu-id="38895-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="38895-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="38895-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="38895-104">Product Name</span></span>|<span data-ttu-id="38895-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="38895-105">SQL Server</span></span>|  
|<span data-ttu-id="38895-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="38895-106">Event ID</span></span>|<span data-ttu-id="38895-107">32042</span><span class="sxs-lookup"><span data-stu-id="38895-107">32042</span></span>|  
|<span data-ttu-id="38895-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="38895-108">Event Source</span></span>|<span data-ttu-id="38895-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="38895-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="38895-110">元件</span><span class="sxs-lookup"><span data-stu-id="38895-110">Component</span></span>|<span data-ttu-id="38895-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="38895-111">SQLEngine</span></span>|  
|<span data-ttu-id="38895-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="38895-112">Symbolic Name</span></span>|<span data-ttu-id="38895-113">SQLErrorNum32042</span><span class="sxs-lookup"><span data-stu-id="38895-113">SQLErrorNum32042</span></span>|  
|<span data-ttu-id="38895-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="38895-114">Message Text</span></span>|<span data-ttu-id="38895-115">已發出 '未傳送記錄' 的警示。</span><span class="sxs-lookup"><span data-stu-id="38895-115">The alert for 'unsent log' has been raised.</span></span> <span data-ttu-id="38895-116">目前的值 '%d' 已超出臨界值 '%d'。</span><span class="sxs-lookup"><span data-stu-id="38895-116">The current value of '%d' surpasses the threshold '%d'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="38895-117">說明</span><span class="sxs-lookup"><span data-stu-id="38895-117">Explanation</span></span>  
 <span data-ttu-id="38895-118">這個資料庫鏡像事件是在主體伺服器執行個體上發出，用來指示未傳送記錄數量已經到達使用者指定的臨界值。</span><span class="sxs-lookup"><span data-stu-id="38895-118">This database mirroring event is issued on the principal server instance to indicate that the amount of unsent log has reached a user-specified threshold value.</span></span> <span data-ttu-id="38895-119">一般而言，會發生這個事件，是因為系統效能已經變更。</span><span class="sxs-lookup"><span data-stu-id="38895-119">Typically, this event occurs because the performance of the system has changed.</span></span> <span data-ttu-id="38895-120">若不是兩個系統間的頻寬已經縮減，就是負載已經增加。</span><span class="sxs-lookup"><span data-stu-id="38895-120">Either the bandwidth between the two systems has decreased, or the load has increased.</span></span>  
  
 <span data-ttu-id="38895-121">未傳送記錄的數量是以未傳送記錄的 KB 數表示，可協助您評估資料遺失可能性的效能標準。</span><span class="sxs-lookup"><span data-stu-id="38895-121">The amount of unsent log is a performance metric that can help you evaluate the potential for data loss in terms of the number of kilobytes (KB) of unsent log.</span></span> <span data-ttu-id="38895-122">這項標準與高效能模式的工作階段尤其相關。</span><span class="sxs-lookup"><span data-stu-id="38895-122">This metric is particularly relevant for high-performance mode sessions.</span></span> <span data-ttu-id="38895-123">但是，當鏡像因為夥伴中斷連接而暫停或暫止時，這項標準也會與高安全性模式工作階段有關。</span><span class="sxs-lookup"><span data-stu-id="38895-123">However, this metric is also a relevant for high-safety mode session when mirroring is paused or suspended because the partners become disconnected.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="38895-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="38895-124">User Action</span></span>  
 <span data-ttu-id="38895-125">檢查主體和鏡像伺服器執行個體上的負載及其網路連接，以了解發生原因。</span><span class="sxs-lookup"><span data-stu-id="38895-125">Check the loads on the principal and mirror server instances and their network connection for the cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38895-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38895-126">See Also</span></span>  
 <span data-ttu-id="38895-127">[資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="38895-127">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="38895-128">使用鏡像效能標準的警告臨界值與警示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="38895-128">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
