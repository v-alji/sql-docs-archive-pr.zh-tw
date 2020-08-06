---
title: MSSQLSERVER_32040 | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 32040 (Database Engine error)
ms.assetid: 709219b1-f8b2-4696-8923-dd2e91492eb8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 05692e2f20b0719c1ca8f48282c3b7aaed8e2341
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595077"
---
# <a name="mssqlserver_32040"></a><span data-ttu-id="f4782-102">MSSQLSERVER_32040</span><span class="sxs-lookup"><span data-stu-id="f4782-102">MSSQLSERVER_32040</span></span>
    
## <a name="details"></a><span data-ttu-id="f4782-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="f4782-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f4782-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="f4782-104">Product Name</span></span>|<span data-ttu-id="f4782-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="f4782-105">SQL Server</span></span>|  
|<span data-ttu-id="f4782-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="f4782-106">Event ID</span></span>|<span data-ttu-id="f4782-107">32040</span><span class="sxs-lookup"><span data-stu-id="f4782-107">32040</span></span>|  
|<span data-ttu-id="f4782-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="f4782-108">Event Source</span></span>|<span data-ttu-id="f4782-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="f4782-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="f4782-110">元件</span><span class="sxs-lookup"><span data-stu-id="f4782-110">Component</span></span>|<span data-ttu-id="f4782-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="f4782-111">SQLEngine</span></span>|  
|<span data-ttu-id="f4782-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="f4782-112">Symbolic Name</span></span>|<span data-ttu-id="f4782-113">SQLErrorNum32040</span><span class="sxs-lookup"><span data-stu-id="f4782-113">SQLErrorNum32040</span></span>|  
|<span data-ttu-id="f4782-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="f4782-114">Message Text</span></span>|<span data-ttu-id="f4782-115">已發出 [最舊尚未傳送的交易] 的警示。</span><span class="sxs-lookup"><span data-stu-id="f4782-115">The alert for 'oldest unsent transaction' has been raised.</span></span> <span data-ttu-id="f4782-116">目前的值 '%d' 已超出臨界值 '%d'。</span><span class="sxs-lookup"><span data-stu-id="f4782-116">The current value of '%d' surpasses the threshold '%d'.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="f4782-117">說明</span><span class="sxs-lookup"><span data-stu-id="f4782-117">Explanation</span></span>  
 <span data-ttu-id="f4782-118">這個資料庫鏡像事件是在主體伺服器執行個體上發出，用來指示最久未傳送交易的時間已經到達使用者指定的臨界值。</span><span class="sxs-lookup"><span data-stu-id="f4782-118">This database mirroring event is issued on the principal server instance to indicate that the age of the oldest unsent transaction has reached a user-specified threshold value.</span></span> <span data-ttu-id="f4782-119">一般而言，會發生這個事件，是因為系統效能已經變更。</span><span class="sxs-lookup"><span data-stu-id="f4782-119">Typically, this event occurs because the performance of the system has changed.</span></span> <span data-ttu-id="f4782-120">若不是兩個系統間的頻寬已經縮減，就是負載已經增加。</span><span class="sxs-lookup"><span data-stu-id="f4782-120">Either the bandwidth between the two systems has decreased, or the load has increased.</span></span>  
  
 <span data-ttu-id="f4782-121">最久未傳送交易的時間是以未傳送交易的分鐘數計算，可協助您評估資料遺失可能性的效能標準。</span><span class="sxs-lookup"><span data-stu-id="f4782-121">The age of the oldest unsent transaction is a performance metric that can help you evaluate the potential for data loss as measured by the number of minutes of unsent transactions.</span></span> <span data-ttu-id="f4782-122">這項標準與高效能模式的工作階段尤其相關。</span><span class="sxs-lookup"><span data-stu-id="f4782-122">This metric is especially relevant for high-performance mode sessions.</span></span> <span data-ttu-id="f4782-123">但是，當鏡像因為夥伴中斷連接而暫停或暫止時，這項標準也會與高安全性模式工作階段有關。</span><span class="sxs-lookup"><span data-stu-id="f4782-123">However, this metric is also relevant for high-safety mode session when mirroring is paused or suspended because the partners become disconnected.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="f4782-124">使用者動作</span><span class="sxs-lookup"><span data-stu-id="f4782-124">User Action</span></span>  
 <span data-ttu-id="f4782-125">檢查主體和鏡像伺服器執行個體上的負載及其網路連接，以了解發生原因。</span><span class="sxs-lookup"><span data-stu-id="f4782-125">Check the loads on the principal and mirror server instances and their network connection for the cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4782-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f4782-126">See Also</span></span>  
 <span data-ttu-id="f4782-127">[資料庫鏡像 &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span><span class="sxs-lookup"><span data-stu-id="f4782-127">[Database Mirroring &#40;SQL Server&#41;](../../database-engine/database-mirroring/database-mirroring-sql-server.md) </span></span>  
 [<span data-ttu-id="f4782-128">使用鏡像效能標準的警告臨界值與警示 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="f4782-128">Use Warning Thresholds and Alerts on Mirroring Performance Metrics &#40;SQL Server&#41;</span></span>](../../database-engine/database-mirroring/use-warning-thresholds-and-alerts-on-mirroring-performance-metrics-sql-server.md)  
  
  
