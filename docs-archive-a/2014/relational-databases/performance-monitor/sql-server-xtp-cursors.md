---
title: XTP 資料指標 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
ms.assetid: 84bf4654-3ef7-4d7f-a269-c8bb4ed4acad
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 217a1196717492cb92adb24eaf7c06c8867abc2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704046"
---
# <a name="xtp-cursors"></a><span data-ttu-id="4f501-102">XTP 資料指標</span><span class="sxs-lookup"><span data-stu-id="4f501-102">XTP Cursors</span></span>
  <span data-ttu-id="4f501-103">XTP 資料指標效能物件包含與內部 XTP 引擎資料指標相關的計數器。</span><span class="sxs-lookup"><span data-stu-id="4f501-103">The XTP Cursors performance object contains counters related to internal XTP engine cursors.</span></span> <span data-ttu-id="4f501-104">資料指標是 XTP 引擎用來處理 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢的低階建置組塊。</span><span class="sxs-lookup"><span data-stu-id="4f501-104">Cursors are the low-level building blocks the XTP engine uses to process [!INCLUDE[tsql](../../includes/tsql-md.md)] queries.</span></span> <span data-ttu-id="4f501-105">因此，您通常不會有這些指標的直接控制權。</span><span class="sxs-lookup"><span data-stu-id="4f501-105">As such, you do not typically have direct control over them.</span></span>  
  
 <span data-ttu-id="4f501-106">下表描述**XTP 資料指標**計數器。</span><span class="sxs-lookup"><span data-stu-id="4f501-106">This table describes the **XTP Cursors** counters.</span></span>  
  
|<span data-ttu-id="4f501-107">計數器</span><span class="sxs-lookup"><span data-stu-id="4f501-107">Counter</span></span>|<span data-ttu-id="4f501-108">描述</span><span class="sxs-lookup"><span data-stu-id="4f501-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4f501-109">**資料指標刪除/秒**</span><span class="sxs-lookup"><span data-stu-id="4f501-109">**Cursor deletes/sec**</span></span>|<span data-ttu-id="4f501-110">(平均) 每秒資料指標刪除數目。</span><span class="sxs-lookup"><span data-stu-id="4f501-110">The number of cursor deletes (on average), per second.</span></span>|  
|<span data-ttu-id="4f501-111">**資料指標插入/秒**</span><span class="sxs-lookup"><span data-stu-id="4f501-111">**Cursor inserts/sec**</span></span>|<span data-ttu-id="4f501-112">(平均) 每秒資料指標插入數目。</span><span class="sxs-lookup"><span data-stu-id="4f501-112">The number of cursor inserts (on average), per second.</span></span>|  
|<span data-ttu-id="4f501-113">**啟動的資料指標掃描/秒**</span><span class="sxs-lookup"><span data-stu-id="4f501-113">**Cursor scans started /sec**</span></span>|<span data-ttu-id="4f501-114">(平均) 每秒啟動的資料指標掃描次數。</span><span class="sxs-lookup"><span data-stu-id="4f501-114">The number of cursor scans started (on average), per second.</span></span>|  
|<span data-ttu-id="4f501-115">**資料指標唯一違規/秒**</span><span class="sxs-lookup"><span data-stu-id="4f501-115">**Cursor unique violations/sec**</span></span>|<span data-ttu-id="4f501-116">(平均) 每秒唯一約束違規數目。</span><span class="sxs-lookup"><span data-stu-id="4f501-116">The number of unique-constraint violations (on average), per second.</span></span>|  
|<span data-ttu-id="4f501-117">**資料指標更新/秒**</span><span class="sxs-lookup"><span data-stu-id="4f501-117">**Cursor updates/sec**</span></span>|<span data-ttu-id="4f501-118">(平均) 每秒資料指標更新數目。</span><span class="sxs-lookup"><span data-stu-id="4f501-118">The number of cursor updates (on average), per second.</span></span>|  
|<span data-ttu-id="4f501-119">**資料指標寫入衝突/秒**</span><span class="sxs-lookup"><span data-stu-id="4f501-119">**Cursor write   conflicts/sec**</span></span>|<span data-ttu-id="4f501-120">(平均) 每秒寫至相同資料列版本的寫入 - 寫入衝突數目。</span><span class="sxs-lookup"><span data-stu-id="4f501-120">The number of write-write conflicts to the same row version (on average), per second.</span></span>|  
|<span data-ttu-id="4f501-121">**塵封角落掃描重試次數/秒 (由使用者發出)**</span><span class="sxs-lookup"><span data-stu-id="4f501-121">**Dusty corner scan retries/sec (user-issued)**</span></span>|<span data-ttu-id="4f501-122">使用者完整資料表掃描發出的塵封角落掃掠期間，(平均) 每秒因為發生寫入衝突而進行掃描的重試次數。</span><span class="sxs-lookup"><span data-stu-id="4f501-122">The number of scan retries due to write conflicts during dusty corner sweeps issued by a user's full-table scan (on average), per second.</span></span> <span data-ttu-id="4f501-123">這是層級非常低的計數器，非供客戶使用。</span><span class="sxs-lookup"><span data-stu-id="4f501-123">This is a very low-level counter, not intended for customer use.</span></span>|  
|<span data-ttu-id="4f501-124">**移除的過期資料列/秒**</span><span class="sxs-lookup"><span data-stu-id="4f501-124">**Expired rows removed/sec**</span></span>|<span data-ttu-id="4f501-125">(平均) 每秒由資料指標移除的過期資料列數。</span><span class="sxs-lookup"><span data-stu-id="4f501-125">The number of expired rows removed by cursors (on average), per second.</span></span>|  
|<span data-ttu-id="4f501-126">**接觸到的過期資料列/秒**</span><span class="sxs-lookup"><span data-stu-id="4f501-126">**Expired rows touched/sec**</span></span>|<span data-ttu-id="4f501-127">(平均) 每秒資料指標接觸到的過期資料列數。</span><span class="sxs-lookup"><span data-stu-id="4f501-127">The number of expired rows touched by cursors (on average), per second.</span></span>|  
|<span data-ttu-id="4f501-128">**傳回的資料列/秒**</span><span class="sxs-lookup"><span data-stu-id="4f501-128">**Rows returned/sec**</span></span>|<span data-ttu-id="4f501-129">(平均) 每秒由資料指標傳回的資料列數。</span><span class="sxs-lookup"><span data-stu-id="4f501-129">The number of rows returned by cursors (on average), per second.</span></span>|  
|<span data-ttu-id="4f501-130">**接觸到的資料列/秒**</span><span class="sxs-lookup"><span data-stu-id="4f501-130">**Rows touched/sec**</span></span>|<span data-ttu-id="4f501-131">(平均) 每秒資料指標接觸到的資料列數。</span><span class="sxs-lookup"><span data-stu-id="4f501-131">The number of rows touched by cursors (on average), per second.</span></span>|  
|<span data-ttu-id="4f501-132">**接觸到的暫訂刪除資料列/秒**</span><span class="sxs-lookup"><span data-stu-id="4f501-132">**Tentatively-deleted rows touched/sec**</span></span>|<span data-ttu-id="4f501-133">(平均) 每秒資料指標接觸到的將過期資料列數。</span><span class="sxs-lookup"><span data-stu-id="4f501-133">The number of expiring rows touched by cursors (on average), per second.</span></span> <span data-ttu-id="4f501-134">如果刪除資料列的交易仍為使用中 (也就是尚未認可或中止)，則資料列即將過期。</span><span class="sxs-lookup"><span data-stu-id="4f501-134">A row is expiring if the transaction that deleted it is still active (i.e. has not yet committed or aborted.)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4f501-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f501-135">See Also</span></span>  
 [<span data-ttu-id="4f501-136">XTP &#40;記憶體內部 OLTP&#41; 效能計數器</span><span class="sxs-lookup"><span data-stu-id="4f501-136">XTP &#40;In-Memory OLTP&#41; Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
