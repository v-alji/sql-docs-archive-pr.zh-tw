---
title: SQL Server 的 Plan Cache 物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Plan Cache object
- SQLServer:Plan Cache
ms.assetid: 225e2b02-8d2f-4f29-9eba-f5847c36ea99
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 002cbe261c531c18bdbb2170da9694cc8abde89d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687806"
---
# <a name="sql-server-plan-cache-object"></a><span data-ttu-id="b03f0-102">SQL Server 的 Plan Cache 物件</span><span class="sxs-lookup"><span data-stu-id="b03f0-102">SQL Server, Plan Cache Object</span></span>
  <span data-ttu-id="b03f0-103">**Plan Cache** 物件所提供的計數器，可監視 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 如何使用記憶體來儲存物件，例如預存程序、特定與備妥 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式，以及觸發程序。</span><span class="sxs-lookup"><span data-stu-id="b03f0-103">The **Plan Cache** object provides counters to monitor how [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses memory to store objects such as stored procedures, ad hoc and prepared [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, and triggers.</span></span> <span data-ttu-id="b03f0-104">可同時監視 **Plan Cache** 物件的多個執行個體，每個執行個體都代表所要監視的不同計畫類型。</span><span class="sxs-lookup"><span data-stu-id="b03f0-104">Multiple instances of the **Plan Cache** object can be monitored at the same time, with each instance representing a different type of plan to monitor.</span></span>  
  
 <span data-ttu-id="b03f0-105">下表描述 **SQLServer:Plan Cache**計數器。</span><span class="sxs-lookup"><span data-stu-id="b03f0-105">This table describes are the **SQLServer:Plan Cache**counters.</span></span>  
  
|<span data-ttu-id="b03f0-106">SQL Server Plan Cache 計數器</span><span class="sxs-lookup"><span data-stu-id="b03f0-106">SQL Server Plan Cache counters</span></span>|<span data-ttu-id="b03f0-107">描述</span><span class="sxs-lookup"><span data-stu-id="b03f0-107">Description</span></span>|  
|------------------------------------|-----------------|  
|<span data-ttu-id="b03f0-108">**Cache Hit Ratio**</span><span class="sxs-lookup"><span data-stu-id="b03f0-108">**Cache Hit Ratio**</span></span>|<span data-ttu-id="b03f0-109">快取叫用數和查閱數之間的比率</span><span class="sxs-lookup"><span data-stu-id="b03f0-109">Ratio between cache hits and lookups.</span></span>|  
|<span data-ttu-id="b03f0-110">**Cache Object Counts**</span><span class="sxs-lookup"><span data-stu-id="b03f0-110">**Cache Object Counts**</span></span>|<span data-ttu-id="b03f0-111">快取中的快取物件數。</span><span class="sxs-lookup"><span data-stu-id="b03f0-111">Number of cache objects in the cache.</span></span>|  
|<span data-ttu-id="b03f0-112">**快取頁面**</span><span class="sxs-lookup"><span data-stu-id="b03f0-112">**Cache Pages**</span></span>|<span data-ttu-id="b03f0-113">快取物件所用的 8 KB 分頁數。</span><span class="sxs-lookup"><span data-stu-id="b03f0-113">Number of 8-kilobyte (KB) pages used by cache objects.</span></span>|  
|<span data-ttu-id="b03f0-114">**Cache Objects in use**</span><span class="sxs-lookup"><span data-stu-id="b03f0-114">**Cache Objects in use**</span></span>|<span data-ttu-id="b03f0-115">使用中的快取物件數目。</span><span class="sxs-lookup"><span data-stu-id="b03f0-115">Number of cache objects in use.</span></span>|  
  
 <span data-ttu-id="b03f0-116">物件中的每個計數器均包含下列執行個體：</span><span class="sxs-lookup"><span data-stu-id="b03f0-116">Each counter in the object contains the following instances:</span></span>  
  
|<span data-ttu-id="b03f0-117">Plan Cache 執行個體</span><span class="sxs-lookup"><span data-stu-id="b03f0-117">Plan Cache instance</span></span>|<span data-ttu-id="b03f0-118">描述</span><span class="sxs-lookup"><span data-stu-id="b03f0-118">Description</span></span>|  
|-------------------------|-----------------|  
|<span data-ttu-id="b03f0-119">**_Total**</span><span class="sxs-lookup"><span data-stu-id="b03f0-119">**_Total**</span></span>|<span data-ttu-id="b03f0-120">所有快取執行個體類型的資訊。</span><span class="sxs-lookup"><span data-stu-id="b03f0-120">Information for all types of cache instances.</span></span>|  
|<span data-ttu-id="b03f0-121">**Sql Plans**</span><span class="sxs-lookup"><span data-stu-id="b03f0-121">**Sql Plans**</span></span>|<span data-ttu-id="b03f0-122">從特定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢 (包括自動參數化查詢) 產生的查詢計劃，或從使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] sp_prepare **或** sp_cursorprepare **準備之**陳述式產生的查詢計劃。</span><span class="sxs-lookup"><span data-stu-id="b03f0-122">Query plans produced from an ad hoc [!INCLUDE[tsql](../../includes/tsql-md.md)] query, including auto-parameterized queries, or from [!INCLUDE[tsql](../../includes/tsql-md.md)] statements prepared using **sp_prepare** or **sp_cursorprepare**.</span></span> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b03f0-123">會快取特定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的計畫，以便稍後執行相同的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式時重複使用。</span><span class="sxs-lookup"><span data-stu-id="b03f0-123">caches the plans for ad hoc [!INCLUDE[tsql](../../includes/tsql-md.md)] statements for later reuse if the identical [!INCLUDE[tsql](../../includes/tsql-md.md)] statement is later executed.</span></span> <span data-ttu-id="b03f0-124">使用者的參數化查詢 (即使未確實預備) 也會當作預備的 SQL 計畫來監視。</span><span class="sxs-lookup"><span data-stu-id="b03f0-124">User-parameterized queries (even if not explicitly prepared) are also monitored as Prepared SQL Plans.</span></span>|  
|<span data-ttu-id="b03f0-125">**Object Plans**</span><span class="sxs-lookup"><span data-stu-id="b03f0-125">**Object Plans**</span></span>|<span data-ttu-id="b03f0-126">藉著建立預存程序、函數或觸發程序而產生的查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="b03f0-126">Query plans generated by creating a stored procedure, function, or trigger.</span></span>|  
|<span data-ttu-id="b03f0-127">**Bound Trees**</span><span class="sxs-lookup"><span data-stu-id="b03f0-127">**Bound Trees**</span></span>|<span data-ttu-id="b03f0-128">檢視、規則、計算資料行與檢查條件約束的正規化樹。</span><span class="sxs-lookup"><span data-stu-id="b03f0-128">Normalized trees for views, rules, computed columns, and check constraints.</span></span>|  
|<span data-ttu-id="b03f0-129">**擴充預存程序**</span><span class="sxs-lookup"><span data-stu-id="b03f0-129">**Extended Stored Procedures**</span></span>|<span data-ttu-id="b03f0-130">擴充預存程序的目錄資訊。</span><span class="sxs-lookup"><span data-stu-id="b03f0-130">Catalog information for extended stores procedures.</span></span>|  
|<span data-ttu-id="b03f0-131">**暫存資料表 & 資料表變數**</span><span class="sxs-lookup"><span data-stu-id="b03f0-131">**Temporary Tables & Table Variables**</span></span>|<span data-ttu-id="b03f0-132">與暫存資料表和資料表變數相關的快取資訊。</span><span class="sxs-lookup"><span data-stu-id="b03f0-132">Cache information related to temporary tables and table variables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b03f0-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b03f0-133">See Also</span></span>  
 <span data-ttu-id="b03f0-134">[伺服器記憶體伺服器組態選項](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span><span class="sxs-lookup"><span data-stu-id="b03f0-134">[Server Memory Server Configuration Options](../../database-engine/configure-windows/server-memory-server-configuration-options.md) </span></span>  
 <span data-ttu-id="b03f0-135">[SQL Server 的 Buffer Manager 物件](sql-server-buffer-manager-object.md) </span><span class="sxs-lookup"><span data-stu-id="b03f0-135">[SQL Server, Buffer Manager Object](sql-server-buffer-manager-object.md) </span></span>  
 [<span data-ttu-id="b03f0-136">監視資源使用狀況 &#40;System Monitor&#41;</span><span class="sxs-lookup"><span data-stu-id="b03f0-136">Monitor Resource Usage &#40;System Monitor&#41;</span></span>](monitor-resource-usage-system-monitor.md)  
  
  
