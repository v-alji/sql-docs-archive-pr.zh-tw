---
title: 主動式快取 (分割區) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- hybrid OLAP
- partitions [Analysis Services], proactive caching
- relational OLAP
- multidimensional OLAP
- MOLAP
- proactive caching [Analysis Services]
- ROLAP
- cache [Analysis Services]
ms.assetid: 422660b2-4d80-4165-b1c9-3963bcde556b
author: minewiskan
ms.author: owend
ms.openlocfilehash: a903d73394b191dbfe96dea710fb2c6c86165402
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607123"
---
# <a name="proactive-caching-partitions"></a><span data-ttu-id="61b9d-102">主動式快取 (資料分割)</span><span class="sxs-lookup"><span data-stu-id="61b9d-102">Proactive Caching (Partitions)</span></span>
  <span data-ttu-id="61b9d-103">主動式快取會提供自動 MOLAP 快取建立及 OLAP 物件的管理。</span><span class="sxs-lookup"><span data-stu-id="61b9d-103">Proactive caching provides automatic MOLAP cache creation and management for OLAP objects.</span></span> <span data-ttu-id="61b9d-104">Cube 會根據從資料庫接收而來的通知，立即併入對資料庫資料所做的變更。</span><span class="sxs-lookup"><span data-stu-id="61b9d-104">The cubes immediately incorporate changes that are made to the data in the database, based upon notifications received from the database.</span></span> <span data-ttu-id="61b9d-105">主動式快取的目標是要提供傳統 MOLAP 的效能，同時保持 ROLAP 所提供的立即性與便於管理性。</span><span class="sxs-lookup"><span data-stu-id="61b9d-105">The goal of proactive caching is to provide the performance of traditional MOLAP, while retaining the immediacy and ease of management offered by ROLAP.</span></span>  
  
 <span data-ttu-id="61b9d-106">簡單的 <xref:Microsoft.AnalysisServices.ProactiveCaching> 物件是由時間指定和資料表通知所組成。</span><span class="sxs-lookup"><span data-stu-id="61b9d-106">A simple <xref:Microsoft.AnalysisServices.ProactiveCaching> object is composed of: timing specification, and table notification.</span></span> <span data-ttu-id="61b9d-107">時間指定會定義在收到變更通知以後，用於更新快取的時間範圍。</span><span class="sxs-lookup"><span data-stu-id="61b9d-107">The timing specification defines the timeframe for updating the cache after a change notification has been received.</span></span> <span data-ttu-id="61b9d-108">資料表通知會定義在資料表與 <xref:Microsoft.AnalysisServices.ProactiveCaching> 物件之間的通知結構描述。</span><span class="sxs-lookup"><span data-stu-id="61b9d-108">The table notification defines the notification schema between the data table and the <xref:Microsoft.AnalysisServices.ProactiveCaching> object.</span></span>  
  
 <span data-ttu-id="61b9d-109">多維度 OLAP (MOLAP) 儲存提供最佳查詢回應，但有些資料延遲是其負面影響。</span><span class="sxs-lookup"><span data-stu-id="61b9d-109">Multidimensional OLAP (MOLAP) storage provides the best query response, but with a penalty of some data latency.</span></span> <span data-ttu-id="61b9d-110">即時關聯式 OLAP (ROLAP) 儲存可讓使用者立即瀏覽資料來源的最新變更，但效能比多維度 OLAP (MOLAP) 儲存差很多是其負面影響，因為資料缺乏預先導出摘要，且因為關聯式儲存不是 OLAP 式查詢的最佳方式。</span><span class="sxs-lookup"><span data-stu-id="61b9d-110">Real-time relational OLAP (ROLAP) storage lets users immediately browse the most recent changes in a data source, but at the penalty of significantly poorer performance than multidimensional OLAP (MOLAP) storage because of the absence of precalculated summaries of data and because relational storage is not optimized for OLAP-style queries.</span></span> <span data-ttu-id="61b9d-111">如果使用者需要在您的應用程式中查看最新資料，而且您也想要擁有 MOLAP 儲存的效能優勢，SQL Server Analysis Services 提供了主動式快取的選擇來應付這個狀況，特別是在結合使用資料分割時。</span><span class="sxs-lookup"><span data-stu-id="61b9d-111">If you have applications in which your users need to see recent data and you also want the performance advantages of MOLAP storage, SQL Server Analysis Services offers the option of proactive caching to address this scenario, particularly in combination with the use of partitions.</span></span> <span data-ttu-id="61b9d-112">主動式快取的設定是以每個資料分割和每個維度為準，</span><span class="sxs-lookup"><span data-stu-id="61b9d-112">Proactive caching is set on a per partition and per dimension basis.</span></span> <span data-ttu-id="61b9d-113">主動式快取選項可以在 MOLAP 儲存的增強式效能及 ROLAP 儲存的立即性之間提供平衡，並在基礎資料變更時或是根據設定的排程來提供自動資料分割處理。</span><span class="sxs-lookup"><span data-stu-id="61b9d-113">Proactive caching options can provide a balance between the enhanced performance of MOLAP storage and the immediacy of ROLAP storage, and provide automatic partition processing when underlying data changes or on a set schedule.</span></span>  
  
## <a name="proactive-caching-configuration-options"></a><span data-ttu-id="61b9d-114">主動式快取組態選項</span><span class="sxs-lookup"><span data-stu-id="61b9d-114">Proactive Caching Configuration Options</span></span>  
 <span data-ttu-id="61b9d-115">SQL Server Analysis Services 提供數個主動式快取組態選項，可讓您將效能最大化、將延遲最小化，及排程處理。</span><span class="sxs-lookup"><span data-stu-id="61b9d-115">SQL Server Analysis Services provides several proactive caching configuration options that enable you to maximize performance, minimize latency, and schedule processing.</span></span> <span data-ttu-id="61b9d-116">主動式快取功能可簡化處理資料陳舊過時的過程。</span><span class="sxs-lookup"><span data-stu-id="61b9d-116">Proactive caching features simplify the process of managing data obsolescence.</span></span> <span data-ttu-id="61b9d-117">主動式快取設定會決定多維度 OLAP 結構 (也稱為 MOLAP 快取) 的重建頻率、重建快取時會查詢過期的 MOLAP 儲存還是基礎 ROLAP 資料來源，以及重建快取時是依照排程還是根據資料庫中的變更。</span><span class="sxs-lookup"><span data-stu-id="61b9d-117">The proactive caching settings determine how frequently the multidimensional OLAP structure, also called the MOLAP cache, is rebuilt, whether the outdated MOLAP storage is queried while the cache is rebuilt or the underlying ROLAP data source, and whether the cache is rebuilt on a schedule or based on changes in the database.</span></span>  
  
### <a name="minimizing-latency"></a><span data-ttu-id="61b9d-118">將延遲最小化</span><span class="sxs-lookup"><span data-stu-id="61b9d-118">Minimizing Latency</span></span>  
 <span data-ttu-id="61b9d-119">當主動式快取設為將延遲最小化時，會根據資料最近是否發生變更以及設定主動式快取的方式，對 ROLAP 儲存或 MOLAP 儲存提出 OLAP 物件的使用者查詢。</span><span class="sxs-lookup"><span data-stu-id="61b9d-119">With proactive caching set to minimize latency, user queries against an OLAP object are made against either ROLAP storage or MOLAP storage, depending whether recent changes have occurred to the data and how proactive caching is configured.</span></span> <span data-ttu-id="61b9d-120">查詢引擎會將查詢引導至 MOLAP 儲存的來源資料，直到資料來源發生變更為止。</span><span class="sxs-lookup"><span data-stu-id="61b9d-120">The query engine directs queries against source data in MOLAP storage until changes occur in the data source.</span></span> <span data-ttu-id="61b9d-121">為了將延遲減至最少，資料來源中發生變更之後，可以卸除快取的 MOLAP 物件，而當 MOLAP 物件在快取中重建時，查詢會切換至 ROLAP 儲存。</span><span class="sxs-lookup"><span data-stu-id="61b9d-121">To minimize latency, after changes occur in a data source, cached MOLAP objects can be dropped and querying switched to ROLAP storage while the MOLAP objects are rebuilt in cache.</span></span> <span data-ttu-id="61b9d-122">當 MOLAP 物件重建及處理之後，查詢會自動切換回 MOLAP 儲存。</span><span class="sxs-lookup"><span data-stu-id="61b9d-122">After the MOLAP objects are rebuilt and processed, queries are automatically switched to the MOLAP storage.</span></span> <span data-ttu-id="61b9d-123">在小的資料分割中 (如目前的資料分割，可能會和當日的資料一樣小)，會以極快的速度重新整理快取。</span><span class="sxs-lookup"><span data-stu-id="61b9d-123">The cache refresh can occur extremely quickly for a small partition, such as the current partition - which can be as small as the current day.</span></span>  
  
### <a name="maximizing-performance"></a><span data-ttu-id="61b9d-124">將效能最大化</span><span class="sxs-lookup"><span data-stu-id="61b9d-124">Maximizing Performance</span></span>  
 <span data-ttu-id="61b9d-125">為了要將效能提升到最高，同時也減少延遲，也可以在不卸除目前 MOLAP 物件的情況下使用快取。</span><span class="sxs-lookup"><span data-stu-id="61b9d-125">To maximize performance while also reducing latency, caching can also be used without dropping the current MOLAP objects.</span></span> <span data-ttu-id="61b9d-126">於是，查詢會繼續針對 MOLAP 物件提出，但資料則讀入新的快取中加以處理。</span><span class="sxs-lookup"><span data-stu-id="61b9d-126">Queries then continue against the MOLAP objects while data is read into and processed in a new cache.</span></span> <span data-ttu-id="61b9d-127">此方法提供更好的效能，但會導致在建立新快取時，查詢仍傳回舊資料。</span><span class="sxs-lookup"><span data-stu-id="61b9d-127">This method provides better performance but may result in queries returning old data while the new cache is being built.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61b9d-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="61b9d-128">See Also</span></span>  
 <span data-ttu-id="61b9d-129">[維度儲存體](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md) </span><span class="sxs-lookup"><span data-stu-id="61b9d-129">[Dimension Storage](../multidimensional-models-olap-logical-dimension-objects/dimensions-storage.md) </span></span>  
 [<span data-ttu-id="61b9d-130">設定分割區儲存 &#40;Analysis Services - 多維度&#41;</span><span class="sxs-lookup"><span data-stu-id="61b9d-130">Set Partition Storage &#40;Analysis Services - Multidimensional&#41;</span></span>](../multidimensional-models/set-partition-storage-analysis-services-multidimensional.md)  
  
  
