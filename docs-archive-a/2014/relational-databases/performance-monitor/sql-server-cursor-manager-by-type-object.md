---
title: SQL Server 的 Cursor Manager by Type 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Cursor Manager by Type object
- SQLServer:Cursor Manager by Type
ms.assetid: d67fbd8a-7554-4a16-96f1-d9ee857a95e3
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7bee15aa2917f7b8890e6c1d3f26cc0e210208a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592647"
---
# <a name="sql-server-cursor-manager-by-type-object"></a><span data-ttu-id="bcbb5-102">SQL Server 的 Cursor Manager by Type 物件</span><span class="sxs-lookup"><span data-stu-id="bcbb5-102">SQL Server, Cursor Manager by Type Object</span></span>
  <span data-ttu-id="bcbb5-103">**SQLServer:Cursor Manager by Type** 物件提供計數器，可監視依類型分組的資料指標。</span><span class="sxs-lookup"><span data-stu-id="bcbb5-103">The **SQLServer:Cursor Manager by Type** object provides counters to monitor cursors, grouped by type.</span></span>  
  
 <span data-ttu-id="bcbb5-104">下表說明 SQL Server **Cursor Manager by Type** 計數器。</span><span class="sxs-lookup"><span data-stu-id="bcbb5-104">This table describes the SQL Server **Cursor Manager by Type** counters.</span></span>  
  
|<span data-ttu-id="bcbb5-105">Cursor Manager by Type 計數器</span><span class="sxs-lookup"><span data-stu-id="bcbb5-105">Cursor Manager by Type counters</span></span>|<span data-ttu-id="bcbb5-106">描述</span><span class="sxs-lookup"><span data-stu-id="bcbb5-106">Description</span></span>|  
|-------------------------------------|-----------------|  
|<span data-ttu-id="bcbb5-107">**Active cursors**</span><span class="sxs-lookup"><span data-stu-id="bcbb5-107">**Active cursors**</span></span>|<span data-ttu-id="bcbb5-108">使用中的資料指標數目。</span><span class="sxs-lookup"><span data-stu-id="bcbb5-108">Number of active cursors.</span></span>|  
|<span data-ttu-id="bcbb5-109">**Cache Hit Ratio**</span><span class="sxs-lookup"><span data-stu-id="bcbb5-109">**Cache Hit Ratio**</span></span>|<span data-ttu-id="bcbb5-110">快取叫用數和查閱數之間的比率</span><span class="sxs-lookup"><span data-stu-id="bcbb5-110">Ratio between cache hits and lookups.</span></span>|  
|<span data-ttu-id="bcbb5-111">**Cached Cursor Counts**</span><span class="sxs-lookup"><span data-stu-id="bcbb5-111">**Cached Cursor Counts**</span></span>|<span data-ttu-id="bcbb5-112">快取中給定類型的資料指標數目。</span><span class="sxs-lookup"><span data-stu-id="bcbb5-112">Number of cursors of a given type in the cache.</span></span>|  
|<span data-ttu-id="bcbb5-113">**Cursor Cache Use Count/sec**</span><span class="sxs-lookup"><span data-stu-id="bcbb5-113">**Cursor Cache Use Count/sec**</span></span>|<span data-ttu-id="bcbb5-114">每種快取資料指標類型的使用次數。</span><span class="sxs-lookup"><span data-stu-id="bcbb5-114">Times each type of cached cursor has been used.</span></span>|  
|<span data-ttu-id="bcbb5-115">**Cursor memory usage**</span><span class="sxs-lookup"><span data-stu-id="bcbb5-115">**Cursor memory usage**</span></span>|<span data-ttu-id="bcbb5-116">資料指標所耗用的記憶體數量，以 KB 為單位。</span><span class="sxs-lookup"><span data-stu-id="bcbb5-116">Amount of memory consumed by cursors in kilobytes (KB).</span></span>|  
|<span data-ttu-id="bcbb5-117">**Cursor Requests/sec**</span><span class="sxs-lookup"><span data-stu-id="bcbb5-117">**Cursor Requests/sec**</span></span>|<span data-ttu-id="bcbb5-118">伺服器收到的 SQL 資料指標要求數目。</span><span class="sxs-lookup"><span data-stu-id="bcbb5-118">Number of SQL cursor requests received by server.</span></span>|  
|<span data-ttu-id="bcbb5-119">**Cursor worktable usage**</span><span class="sxs-lookup"><span data-stu-id="bcbb5-119">**Cursor worktable usage**</span></span>|<span data-ttu-id="bcbb5-120">資料指標使用的工作資料表數目。</span><span class="sxs-lookup"><span data-stu-id="bcbb5-120">Number of worktables used by cursors.</span></span>|  
|<span data-ttu-id="bcbb5-121">**Number of active cursor plans**</span><span class="sxs-lookup"><span data-stu-id="bcbb5-121">**Number of active cursor plans**</span></span>|<span data-ttu-id="bcbb5-122">資料指標計畫的數目。</span><span class="sxs-lookup"><span data-stu-id="bcbb5-122">Number of cursor plans.</span></span>|  
  
 <span data-ttu-id="bcbb5-123">物件中的每個計數器均包含下列執行個體：</span><span class="sxs-lookup"><span data-stu-id="bcbb5-123">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="bcbb5-124">Cursor Manager 執行個體</span><span class="sxs-lookup"><span data-stu-id="bcbb5-124">Cursor Manager instance</span></span>|<span data-ttu-id="bcbb5-125">描述</span><span class="sxs-lookup"><span data-stu-id="bcbb5-125">Description</span></span>|  
|-----------------------------|-----------------|  
|<span data-ttu-id="bcbb5-126">**_Total**</span><span class="sxs-lookup"><span data-stu-id="bcbb5-126">**_Total**</span></span>|<span data-ttu-id="bcbb5-127">所有資料指標的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="bcbb5-127">Information for all cursors.</span></span>|  
|<span data-ttu-id="bcbb5-128">**API Cursor**</span><span class="sxs-lookup"><span data-stu-id="bcbb5-128">**API Cursor**</span></span>|<span data-ttu-id="bcbb5-129">僅限 API 資料指標資訊。</span><span class="sxs-lookup"><span data-stu-id="bcbb5-129">Only the API cursor information.</span></span>|  
|<span data-ttu-id="bcbb5-130">**TSQL Global Cursor**</span><span class="sxs-lookup"><span data-stu-id="bcbb5-130">**TSQL Global Cursor**</span></span>|<span data-ttu-id="bcbb5-131">僅限 [!INCLUDE[tsql](../../includes/tsql-md.md)] 全域資料指標資訊。</span><span class="sxs-lookup"><span data-stu-id="bcbb5-131">Only the [!INCLUDE[tsql](../../includes/tsql-md.md)] global cursor information.</span></span>|  
|<span data-ttu-id="bcbb5-132">**TSQL Local Cursor**</span><span class="sxs-lookup"><span data-stu-id="bcbb5-132">**TSQL Local Cursor**</span></span>|<span data-ttu-id="bcbb5-133">僅限 [!INCLUDE[tsql](../../includes/tsql-md.md)] 區域資料指標資訊。</span><span class="sxs-lookup"><span data-stu-id="bcbb5-133">Only the [!INCLUDE[tsql](../../includes/tsql-md.md)] local cursor information.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bcbb5-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bcbb5-134">See Also</span></span>  
 [<span data-ttu-id="bcbb5-135">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="bcbb5-135">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
