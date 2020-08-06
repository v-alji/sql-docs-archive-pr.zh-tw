---
title: 鏡像狀態 (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
helpviewer_keywords:
- states [SQL Server], database mirroring
- PENDING_FAILOVER state
- mirroring states [SQL Server]
- DISCONNECTED state
- SYNCHRONIZING state
- SYNCHRONIZED state
- SUSPENDED state
- database mirroring [SQL Server], states
ms.assetid: 90062917-74f9-471b-b49e-bc153ae1a468
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: d458939ba233bdfe7a99edd38afc74b5433ae061
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592197"
---
# <a name="mirroring-states-sql-server"></a><span data-ttu-id="6b020-102">鏡像狀態 (SQL Server)</span><span class="sxs-lookup"><span data-stu-id="6b020-102">Mirroring States (SQL Server)</span></span>
  <span data-ttu-id="6b020-103">在資料庫鏡像工作階段期間，鏡像資料庫一定會處於特定狀態 (「鏡像狀態」)。</span><span class="sxs-lookup"><span data-stu-id="6b020-103">During a database mirroring session, the mirrored database is always in a specific state (the *mirroring state*).</span></span> <span data-ttu-id="6b020-104">資料庫的狀態會反映通訊狀態、資料流程，以及夥伴之間的資料差異。</span><span class="sxs-lookup"><span data-stu-id="6b020-104">The state of the database reflects the communication status, data flow, and the difference in data between the partners.</span></span> <span data-ttu-id="6b020-105">資料庫鏡像工作階段會與主體資料庫採用相同的狀態。</span><span class="sxs-lookup"><span data-stu-id="6b020-105">The database mirroring session adopts the same state as the principal database.</span></span>  
  
 <span data-ttu-id="6b020-106">在資料庫鏡像工作階段內，伺服器執行個體會彼此監視。</span><span class="sxs-lookup"><span data-stu-id="6b020-106">Throughout a database mirroring session, the server instances monitor each other.</span></span> <span data-ttu-id="6b020-107">夥伴會使用鏡像狀態來監視資料庫。</span><span class="sxs-lookup"><span data-stu-id="6b020-107">The partners use the mirroring state to monitor the database.</span></span> <span data-ttu-id="6b020-108">除了 PENDING_FAILOVER 狀態之外，主體資料庫和鏡像資料庫永遠處於相同的狀態。</span><span class="sxs-lookup"><span data-stu-id="6b020-108">With the exception of the PENDING_FAILOVER state, the principal and mirror database are always in the same state.</span></span> <span data-ttu-id="6b020-109">若為工作階段設定見證，則每部夥伴伺服器都會利用其連接狀態 (CONNECTED 或 DISCONNECTED) 來監視見證。</span><span class="sxs-lookup"><span data-stu-id="6b020-109">If a witness is set for the session, each of the partners monitors the witness using its connection state (CONNECTED or DISCONNECTED).</span></span>  
  
 <span data-ttu-id="6b020-110">可能的資料庫鏡像狀態如下：</span><span class="sxs-lookup"><span data-stu-id="6b020-110">The possible mirroring states of the database are as follows:</span></span>  
  
|<span data-ttu-id="6b020-111">鏡像狀態</span><span class="sxs-lookup"><span data-stu-id="6b020-111">Mirroring state</span></span>|<span data-ttu-id="6b020-112">描述</span><span class="sxs-lookup"><span data-stu-id="6b020-112">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="6b020-113">SYNCHRONIZING</span><span class="sxs-lookup"><span data-stu-id="6b020-113">SYNCHRONIZING</span></span>|<span data-ttu-id="6b020-114">鏡像資料庫的內容落後於主體資料庫的內容。</span><span class="sxs-lookup"><span data-stu-id="6b020-114">The contents of the mirror database are lagging behind the contents of the principal database.</span></span> <span data-ttu-id="6b020-115">主體伺服器將記錄檔記錄傳送至鏡像伺服器，將所做的變更套用到鏡像資料庫來向前復原。</span><span class="sxs-lookup"><span data-stu-id="6b020-115">The principal server is sending log records to the mirror server, which is applying the changes to the mirror database to roll it forward.</span></span><br /><br /> <span data-ttu-id="6b020-116">在資料庫鏡像工作階段開始時，資料庫處於 SYNCHRONIZING 狀態。</span><span class="sxs-lookup"><span data-stu-id="6b020-116">At the start of a database mirroring session, the database is in the SYNCHRONIZING state.</span></span> <span data-ttu-id="6b020-117">主體伺服器正為資料庫提供服務，而鏡像伺服器則試圖趕上。</span><span class="sxs-lookup"><span data-stu-id="6b020-117">The principal server is serving the database, and the mirror is trying to catch up.</span></span>|  
|<span data-ttu-id="6b020-118">SYNCHRONIZED</span><span class="sxs-lookup"><span data-stu-id="6b020-118">SYNCHRONIZED</span></span>|<span data-ttu-id="6b020-119">當鏡像伺服器足以追趕上主體伺服器時，鏡像狀態就會變更為 SYNCHRONIZED。</span><span class="sxs-lookup"><span data-stu-id="6b020-119">When the mirror server becomes sufficiently caught up to the principal server, the mirroring state changes to SYNCHRONIZED.</span></span> <span data-ttu-id="6b020-120">只要主體伺服器繼續傳送變更到鏡像伺服器，而鏡像伺服器也繼續將變更套用到鏡像資料庫，資料庫便會保持在這種狀態。</span><span class="sxs-lookup"><span data-stu-id="6b020-120">The database remains in this state as long as the principal server continues to send changes to the mirror server and the mirror server continues to apply changes to the mirror database.</span></span><br /><br /> <span data-ttu-id="6b020-121">如果交易安全性設定為 FULL，SYNCHRONIZED 狀態將可同時支援自動容錯移轉和手動容錯移轉，而且容錯移轉之後不會遺失任何資料。</span><span class="sxs-lookup"><span data-stu-id="6b020-121">If transaction safety is set to FULLautomatic failover and manual failover are both supported in the SYNCHRONIZED state, there is no data loss after a failover.</span></span><br /><br /> <span data-ttu-id="6b020-122">如果關閉交易安全性，永遠都有可能遺失部分資料，即使是在 SYNCHRONIZED 狀態也是如此。</span><span class="sxs-lookup"><span data-stu-id="6b020-122">If transaction safety is off, some data loss is always possible, even in the SYNCHRONIZED state.</span></span>|  
|<span data-ttu-id="6b020-123">SUSPENDED</span><span class="sxs-lookup"><span data-stu-id="6b020-123">SUSPENDED</span></span>|<span data-ttu-id="6b020-124">無法使用資料庫的鏡像副本。</span><span class="sxs-lookup"><span data-stu-id="6b020-124">The mirror copy of the database is not available.</span></span> <span data-ttu-id="6b020-125">主體資料庫執行時並沒有傳送任何記錄檔到鏡像伺服器，這種狀況稱為「執行公開」。</span><span class="sxs-lookup"><span data-stu-id="6b020-125">The principal database is running without sending any logs to the mirror server, a condition known as *running exposed*.</span></span> <span data-ttu-id="6b020-126">這是容錯移轉之後的狀態。</span><span class="sxs-lookup"><span data-stu-id="6b020-126">This is the state after a failover.</span></span><br /><br /> <span data-ttu-id="6b020-127">工作階段也會因為重做錯誤或管理員暫停工作階段而變成 SUSPENDED。</span><span class="sxs-lookup"><span data-stu-id="6b020-127">A session can also become SUSPENDED as a result of redo errors or if the administrator pauses the session.</span></span><br /><br /> <span data-ttu-id="6b020-128">SUSPENDED 是夥伴關機和啟動時仍然有效的永續性狀態。</span><span class="sxs-lookup"><span data-stu-id="6b020-128">SUSPENDED is a persistent state that survives partner shutdowns and startups.</span></span>|  
|<span data-ttu-id="6b020-129">PENDING_FAILOVER</span><span class="sxs-lookup"><span data-stu-id="6b020-129">PENDING_FAILOVER</span></span>|<span data-ttu-id="6b020-130">唯有開始進行容錯移轉之後但伺服器尚未轉換為鏡像角色之前，主體伺服器上才會出現此狀態。</span><span class="sxs-lookup"><span data-stu-id="6b020-130">This state is found only on the principal server after a failover has begun, but the server has not transitioned into the mirror role.</span></span><br /><br /> <span data-ttu-id="6b020-131">起始容錯移轉時，主體資料庫便會進入 PENDING_FAILOVER 狀態，迅速終止任何使用者連接，然後馬上接替鏡像角色。</span><span class="sxs-lookup"><span data-stu-id="6b020-131">When the failover is initiated, the principal database goes into the PENDING_FAILOVER state, quickly terminates any user connections, and takes over the mirror role soon thereafter.</span></span>|  
|<span data-ttu-id="6b020-132">DISCONNECTED</span><span class="sxs-lookup"><span data-stu-id="6b020-132">DISCONNECTED</span></span>|<span data-ttu-id="6b020-133">夥伴已經與其他夥伴失去通訊。</span><span class="sxs-lookup"><span data-stu-id="6b020-133">The partner has lost communication with the other partner.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6b020-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6b020-134">See Also</span></span>  
 [<span data-ttu-id="6b020-135">監視資料庫鏡像 &#40;SQL Server&#41;</span><span class="sxs-lookup"><span data-stu-id="6b020-135">Monitoring Database Mirroring &#40;SQL Server&#41;</span></span>](database-mirroring-sql-server.md)  
  
  
