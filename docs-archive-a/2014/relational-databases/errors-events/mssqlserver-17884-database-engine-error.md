---
title: MSSQLSERVER_17884 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- 17884 (Database Engine error)
ms.assetid: 8d05ba05-3f71-4dc3-bd81-2ea5ac9fe843
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: bd5beca2a7dfd20afbf9eff196d89452ef3533d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702942"
---
# <a name="mssqlserver_17884"></a><span data-ttu-id="649b9-102">MSSQLSERVER_17884</span><span class="sxs-lookup"><span data-stu-id="649b9-102">MSSQLSERVER_17884</span></span>
    
## <a name="details"></a><span data-ttu-id="649b9-103">詳細資料</span><span class="sxs-lookup"><span data-stu-id="649b9-103">Details</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="649b9-104">產品名稱</span><span class="sxs-lookup"><span data-stu-id="649b9-104">Product Name</span></span>|<span data-ttu-id="649b9-105">SQL Server</span><span class="sxs-lookup"><span data-stu-id="649b9-105">SQL Server</span></span>|  
|<span data-ttu-id="649b9-106">事件識別碼</span><span class="sxs-lookup"><span data-stu-id="649b9-106">Event ID</span></span>|<span data-ttu-id="649b9-107">17884</span><span class="sxs-lookup"><span data-stu-id="649b9-107">17884</span></span>|  
|<span data-ttu-id="649b9-108">事件來源</span><span class="sxs-lookup"><span data-stu-id="649b9-108">Event Source</span></span>|<span data-ttu-id="649b9-109">MSSQLSERVER</span><span class="sxs-lookup"><span data-stu-id="649b9-109">MSSQLSERVER</span></span>|  
|<span data-ttu-id="649b9-110">元件</span><span class="sxs-lookup"><span data-stu-id="649b9-110">Component</span></span>|<span data-ttu-id="649b9-111">SQLEngine</span><span class="sxs-lookup"><span data-stu-id="649b9-111">SQLEngine</span></span>|  
|<span data-ttu-id="649b9-112">符號名稱</span><span class="sxs-lookup"><span data-stu-id="649b9-112">Symbolic Name</span></span>|<span data-ttu-id="649b9-113">SRV_SCHEDULER_DEADLOCK</span><span class="sxs-lookup"><span data-stu-id="649b9-113">SRV_SCHEDULER_DEADLOCK</span></span>|  
|<span data-ttu-id="649b9-114">訊息文字</span><span class="sxs-lookup"><span data-stu-id="649b9-114">Message Text</span></span>|<span data-ttu-id="649b9-115">在過去的 %d 秒內，工作者執行緒未在節點 %d 上收取到指派給處理序的新查詢。</span><span class="sxs-lookup"><span data-stu-id="649b9-115">New queries assigned to process on Node %d have not been picked  up by a worker thread in the last %d seconds.</span></span> <span data-ttu-id="649b9-116">這種狀況可能是由封鎖或長時間執行的查詢所造成，且可能會對用戶端的回應時間造成負面影響。</span><span class="sxs-lookup"><span data-stu-id="649b9-116">Blocking or long-running queries can contribute to this condition, and may degrade client response time.</span></span> <span data-ttu-id="649b9-117">請使用 "max worker threads" 組態選項以增加允許的執行緒數目，或最佳化目前執行中的查詢。</span><span class="sxs-lookup"><span data-stu-id="649b9-117">Use the "max worker threads" configuration option to increase number  of allowable threads, or optimize current running queries.</span></span>  <span data-ttu-id="649b9-118">SQL 處理序使用率: %d%%。</span><span class="sxs-lookup"><span data-stu-id="649b9-118">SQL Process Utilization: %d%%.</span></span> <span data-ttu-id="649b9-119">系統閒置率: %d%%。</span><span class="sxs-lookup"><span data-stu-id="649b9-119">System Idle: %d%%.</span></span>|  
  
## <a name="explanation"></a><span data-ttu-id="649b9-120">說明</span><span class="sxs-lookup"><span data-stu-id="649b9-120">Explanation</span></span>  
 <span data-ttu-id="649b9-121">每個排程器都沒有進度的徵兆，而且可能是由於死結所造成，因為沒有任何執行緒可以進行及/或沒有新的工作可挑選和處理。</span><span class="sxs-lookup"><span data-stu-id="649b9-121">There is no sign of progress in each of the schedulers and could be caused by deadlocks where none of the threads can advance and/or no new work can be picked up and processed.</span></span> <span data-ttu-id="649b9-122">如果處理序使用率很低，則電腦上的其他處理序可能會導致伺服器處理序 CPU 資源用盡。</span><span class="sxs-lookup"><span data-stu-id="649b9-122">If process utilization is low then other processes on the machine may be causing the server process CPU starvation.</span></span>  
  
## <a name="user-action"></a><span data-ttu-id="649b9-123">使用者動作</span><span class="sxs-lookup"><span data-stu-id="649b9-123">User Action</span></span>  
 <span data-ttu-id="649b9-124">判斷為何產生封鎖而且沒有任何進度，並據以解決此狀況。</span><span class="sxs-lookup"><span data-stu-id="649b9-124">Determine why there is blocking and no progress being made and resolve situation accordingly.</span></span> <span data-ttu-id="649b9-125">如果處理序使用率很低，請檢查其他處理序所造成的系統負載。</span><span class="sxs-lookup"><span data-stu-id="649b9-125">If process utilization is low check the load on the system caused by other processes.</span></span>  
  
  
