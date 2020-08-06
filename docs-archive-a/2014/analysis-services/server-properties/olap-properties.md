---
title: OLAP 屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- AggregationPerfLog property
- DefaultPageSizeForProp property
- UseSinglePassForDimSecurityAutoExist property
- DeepCompressValue property
- CacheRowsetRows property
- Income property
- AggregationNewAlgo property
- MemoryAdjustFactor property
- DimensionLatencyAccuracy property
- InitialBonus property
- DefaultPageSizeForDataHeader property
- MaxCPUUsage property
- DistinctBuffer property
- PartitionLatencyAccuracy property
- MaxRetries property
- UseDataCacheRegistryMultiplyKey property
- ConvertDeletedToUnknown property
- DatabaseConnectionPoolMax property
- DataFileInitEnabled property
- DefaultPageSizeForHash property
- MaxRolapOrConditions property
- UseDataCacheFreeLastPageMemory property
- OLAP [Analysis Services], properties
- MapHandleAlgorithm property
- IndexBuildEnabled property
- MaxObjectsInParallel property
- IgnoreNullRolapRows property
- DimensionPropertyCacheSize property
- DefaultRefreshInterval property
- CheckDistinctRecordSortOrder property
- BufferMemoryLimit property
- EnableTableGrouping property
- ExpressNonEmptyUseEnabled property
- CopyLinkedDataCacheAndRegistry property
- UseDataSlice property
- MemoryLimitErrorEnabled property
- Enabled property
- EnableRolapOptimization property
- DatabaseConnectionPoolTimeout property
- UseDataCacheRegistryHashTable property
- AggregationsBuildEnabled property
- Tax property
- DatabaseConnectionPoolGeneralTimeout property
- DefaultPageSizeForString property
- DatabaseConnectionPoolConnectTimeout property
- MinimumBalance property
- OptimizeSchema property
- UseCalculationCacheRegistry property
- MaxTableDepth property
- DataSliceInitEnabled property
- PrefetchLowerGranularities property
- UseVBANet property
- BufferRecordLimit property
- DefaultPageSizeForIndexHeader property
- MaximumBalance property
- CalculationCacheRegistryMaxIterations property
- DefaultDrillthroughMaxRows property
- IndexBuildThreshold property
- UseDataCacheRegistry property
- MemoryAdjustConst property
- ApplyIntersect property
- IndexFileInitEnabled property
- CacheRowsetToDisk property
- DataCacheRegistryMaxIterations property
- AllowSEFiltering property
- ForceMultiPass property
- ApplySubtract property
- IndexUseEnabled property
- AggregationsUseEnabled property
- DataPlacementOptimization property
- UseMaterializedIterators property
- CacheRecordLimit property
- ROLAPDimensionProcessingEffort property
- DefaultPageSizeForIndex property
- EnableRolapDimQueryTableGrouping property
- DimensionPropertyKeyCache property
- SleepIntervalSecs property
- DefaultPageSizeForData property
- MapFormatMask property
- CalculationEvaluationPolicy property
- AggregationMemoryLimitMin property
- RecordsReportGranularity property
- MemoryLimit property
- AggregationMemoryLimitMax property
ms.assetid: 06eb0d78-96c0-42ff-b759-f4c794597c8d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2eb89d318bfdb78935eb4d9f202db11b978c59b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595309"
---
# <a name="olap-properties"></a><span data-ttu-id="dea15-102">OLAP 屬性</span><span class="sxs-lookup"><span data-stu-id="dea15-102">OLAP Properties</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="dea15-103">支援下表列出的 OLAP 伺服器屬性。</span><span class="sxs-lookup"><span data-stu-id="dea15-103">supports the OLAP server properties listed in the following tables.</span></span> <span data-ttu-id="dea15-104">如需有關其他伺服器屬性及如何設定伺服器屬性的詳細資訊，請參閱＜ [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md)＞。</span><span class="sxs-lookup"><span data-stu-id="dea15-104">For more information about additional server properties and how to set them, see [Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md).</span></span>  
  
 <span data-ttu-id="dea15-105">**適用物件：** 僅限多維度伺服器模式</span><span class="sxs-lookup"><span data-stu-id="dea15-105">**Applies to:** Multidimensional server mode only</span></span>  
  
## <a name="memory"></a><span data-ttu-id="dea15-106">Memory</span><span class="sxs-lookup"><span data-stu-id="dea15-106">Memory</span></span>  
 `DefaultPageSizeForData`  
 <span data-ttu-id="dea15-107">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-107">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DefaultPageSizeForDataHeader`  
 <span data-ttu-id="dea15-108">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-108">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DefaultPageSizeForIndex`  
 <span data-ttu-id="dea15-109">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-109">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DefaultPageSizeForIndexHeader`  
 <span data-ttu-id="dea15-110">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-110">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DefaultPageSizeForString`  
 <span data-ttu-id="dea15-111">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-111">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DefaultPageSizeForHash`  
 <span data-ttu-id="dea15-112">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-112">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DefaultPageSizeForProp`  
 <span data-ttu-id="dea15-113">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-113">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="lazyprocessing"></a><span data-ttu-id="dea15-114">LazyProcessing</span><span class="sxs-lookup"><span data-stu-id="dea15-114">LazyProcessing</span></span>  
 `Enabled`  
 <span data-ttu-id="dea15-115">此為布林值屬性，指定是否啟用延遲彙總處理。</span><span class="sxs-lookup"><span data-stu-id="dea15-115">A Boolean property that specifies whether lazy aggregation processing is enabled.</span></span>  
  
 `SleepIntervalSecs`  
 <span data-ttu-id="dea15-116">此為帶正負號的 32 位元整數屬性，定義伺服器檢查是否有延遲處理作業暫止的間隔 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="dea15-116">A signed 32-bit integer property that defines the interval, in seconds, that the server checks whether there are lazy processing jobs pending.</span></span>  
  
 `MaxCPUUsage`  
 <span data-ttu-id="dea15-117">此為帶正負號的 64 位元雙精確度浮點數屬性，定義延遲處理的最大 CPU 使用率 (以百分比表示)。</span><span class="sxs-lookup"><span data-stu-id="dea15-117">A signed 64-bit double-precision floating-point number property that defines maximum CPU usage for lazy processing, expressed as a percentage.</span></span> <span data-ttu-id="dea15-118">伺服器會依據快照集監視平均 CPU 使用。</span><span class="sxs-lookup"><span data-stu-id="dea15-118">The server monitors average CPU use based on snapshots.</span></span> <span data-ttu-id="dea15-119">CPU 超過此臨界值之上是正常的行為。</span><span class="sxs-lookup"><span data-stu-id="dea15-119">It is normal behavior for the CPU to spike above this threshold.</span></span>  
  
 <span data-ttu-id="dea15-120">此屬性的預設值為 0.5，表示最多有 50% 的 CPU 會專用於延遲處理。</span><span class="sxs-lookup"><span data-stu-id="dea15-120">The default value for this property is 0.5, indicating a maximum of 50% of the CPU will be devoted to lazy processing.</span></span>  
  
 `MaxObjectsInParallel`  
 <span data-ttu-id="dea15-121">此為帶正負號的 32 位元整數屬性，指出可平行延遲處理的最大分割區數目。</span><span class="sxs-lookup"><span data-stu-id="dea15-121">A signed 32-bit integer property that specifies the maximum number of partitions that can be lazily processed in parallel.</span></span>  
  
 `MaxRetries`  
 <span data-ttu-id="dea15-122">此為帶正負號的 32 位元整數屬性，定義在引發錯誤之前，延遲處理失敗事件的重試次數。</span><span class="sxs-lookup"><span data-stu-id="dea15-122">A signed 32-bit integer property that defines the number of retries in the event that lazy processing fails before an error is raised.</span></span>  
  
## <a name="processplan"></a><span data-ttu-id="dea15-123">ProcessPlan</span><span class="sxs-lookup"><span data-stu-id="dea15-123">ProcessPlan</span></span>  
 `CacheRowsetRows`  
 <span data-ttu-id="dea15-124">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-124">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `CacheRowsetToDisk`  
 <span data-ttu-id="dea15-125">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-125">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DistinctBuffer`  
 <span data-ttu-id="dea15-126">此為帶正負號的 32 位元整數屬性，定義用於相異計數的內部緩衝區大小。</span><span class="sxs-lookup"><span data-stu-id="dea15-126">A signed 32-bit integer property that defines the size of an internal buffer used for distinct counts.</span></span> <span data-ttu-id="dea15-127">增加此值即可加速相異計數處理，但要耗用較多記憶體。</span><span class="sxs-lookup"><span data-stu-id="dea15-127">Increase this value to speed up distinct count processing at the cost of memory use.</span></span>  
  
 `EnableRolapDimQueryTableGrouping`  
 <span data-ttu-id="dea15-128">此為布林值屬性，指定是否為 ROLAP 維度啟用資料表分組。</span><span class="sxs-lookup"><span data-stu-id="dea15-128">A Boolean property that specifies whether table grouping is enabled for ROLAP dimensions.</span></span> <span data-ttu-id="dea15-129">如果為 True，在執行階段查詢 ROLAP 維度時，會立即查詢整個 ROLAP 維度資料表 (而非針對每個屬性個別查詢)。</span><span class="sxs-lookup"><span data-stu-id="dea15-129">If True, when querying ROLAP dimensions at runtime, entire ROLAP dimension tables are queried at once, as opposed to separate queries for each attribute.</span></span>  
  
 `EnableTableGrouping`  
 <span data-ttu-id="dea15-130">此為布林值屬性，指定是否啟用資料表分組。</span><span class="sxs-lookup"><span data-stu-id="dea15-130">A Boolean property that specifies whether table grouping is enabled.</span></span> <span data-ttu-id="dea15-131">如果為 True，在處理維度時，會立即查詢整個維度資料表 (而非針對每個屬性個別查詢)。</span><span class="sxs-lookup"><span data-stu-id="dea15-131">If True, when processing dimensions, entire dimension tables are queried at once, as opposed to separate queries for each attribute.</span></span>  
  
 `ForceMultiPass`  
 <span data-ttu-id="dea15-132">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-132">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxTableDepth`  
 <span data-ttu-id="dea15-133">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-133">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryAdjustConst`  
 <span data-ttu-id="dea15-134">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-134">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryAdjustFactor`  
 <span data-ttu-id="dea15-135">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-135">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MemoryLimit`  
 <span data-ttu-id="dea15-136">此為帶正負號的 64 位元雙精確度浮點數屬性，定義專用於處理的記憶體數量上限 (以實體記憶體的百分比表示)。</span><span class="sxs-lookup"><span data-stu-id="dea15-136">A signed 64-bit double-precision floating-point number property that defines the maximum amount of memory to be devoted to processing, expressed as a percentage of physical memory.</span></span>  
  
 <span data-ttu-id="dea15-137">此屬性的預設值為 65，表示實體記憶體的 65% 可能會專用於 Cube 和維度處理。</span><span class="sxs-lookup"><span data-stu-id="dea15-137">The default value for this property is 65, indicating that 65% of physical memory may be devoted to cube and dimension processing.</span></span>  
  
 `MemoryLimitErrorEnabled`  
 <span data-ttu-id="dea15-138">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-138">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `OptimizeSchema`  
 <span data-ttu-id="dea15-139">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-139">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="proactivecaching"></a><span data-ttu-id="dea15-140">ProactiveCaching</span><span class="sxs-lookup"><span data-stu-id="dea15-140">ProactiveCaching</span></span>  
 `DefaultRefreshInterval`  
 <span data-ttu-id="dea15-141">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-141">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DimensionLatencyAccuracy`  
 <span data-ttu-id="dea15-142">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-142">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `PartitionLatencyAccuracy`  
 <span data-ttu-id="dea15-143">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-143">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="process"></a><span data-ttu-id="dea15-144">Process</span><span class="sxs-lookup"><span data-stu-id="dea15-144">Process</span></span>  
 `AggregationMemoryLimitMax`  
 <span data-ttu-id="dea15-145">此為帶正負號的 64 位元雙精確度浮點數屬性，定義可專用於彙總處理的記憶體數量上限 (以實體記憶體的百分比表示)。</span><span class="sxs-lookup"><span data-stu-id="dea15-145">A signed 64-bit double-precision floating-point number property that defines the maximum amount of memory that can be devoted to aggregation processing, expressed as a percentage of physical memory.</span></span>  
  
 <span data-ttu-id="dea15-146">此屬性的預設值為 80，表示實體記憶體的 80% 可能會專用於彙總處理。</span><span class="sxs-lookup"><span data-stu-id="dea15-146">The default value for this property is 80, indicating that 80% of physical memory may be devoted to aggregation processing.</span></span>  
  
 `AggregationMemoryLimitMin`  
 <span data-ttu-id="dea15-147">此為帶正負號的 64 位元雙精確度浮點數屬性，定義可專用於彙總處理的記憶體數量下限 (以實體記憶體的百分比表示)。</span><span class="sxs-lookup"><span data-stu-id="dea15-147">A signed 64-bit double-precision floating-point number property that defines the minimum amount of memory that can be devoted to aggregation processing, expressed as a percentage of physical memory.</span></span> <span data-ttu-id="dea15-148">此值較大時可加速彙總處理，但要耗用較多記憶體。</span><span class="sxs-lookup"><span data-stu-id="dea15-148">A larger value may speed up aggregation processing at the cost of memory usage.</span></span>  
  
 <span data-ttu-id="dea15-149">此屬性的預設值為 10，表示實體記憶體最少有 10% 將會專用於彙總處理。</span><span class="sxs-lookup"><span data-stu-id="dea15-149">The default value for this property is 10, indicating that minimally 10% of physical memory will be devoted to aggregation processing.</span></span>  
  
 `AggregationNewAlgo`  
 <span data-ttu-id="dea15-150">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-150">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `AggregationPerfLog2`  
 <span data-ttu-id="dea15-151">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-151">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `AggregationsBuildEnabled`  
 <span data-ttu-id="dea15-152">此為布林值屬性，指定是否啟用彙總建立。</span><span class="sxs-lookup"><span data-stu-id="dea15-152">A Boolean property that specifies whether aggregation building is enabled.</span></span> <span data-ttu-id="dea15-153">這是不用變更彙總設計即可對彙總建立進行效能評定的機制。</span><span class="sxs-lookup"><span data-stu-id="dea15-153">This is a mechanism to benchmark aggregation building without changing aggregation design.</span></span>  
  
 `BufferMemoryLimit`  
 <span data-ttu-id="dea15-154">此為帶正負號的 64 位元雙精確度浮點數屬性，定義處理緩衝區記憶體的限制 (以實體記憶體的百分比表示)。</span><span class="sxs-lookup"><span data-stu-id="dea15-154">A signed 64-bit double-precision floating-point number property that defines the processing buffer memory limit, expressed as a percent of physical memory.</span></span>  
  
 <span data-ttu-id="dea15-155">此屬性的預設值為 60，表示最多有 60% 的實體記憶體可用於緩衝區記憶體。</span><span class="sxs-lookup"><span data-stu-id="dea15-155">The default value for this property is 60, which indicates that up to 60% of physical memory can be used for buffer memory.</span></span>  
  
 `BufferRecordLimit`  
 <span data-ttu-id="dea15-156">此為帶正負號的 32 位元整數屬性，定義處理期間可以緩衝的記錄數目。</span><span class="sxs-lookup"><span data-stu-id="dea15-156">A signed 32-bit integer property that defines the number of records that can be buffered during processing.</span></span>  
  
 <span data-ttu-id="dea15-157">此屬性的預設值為 1048576 (個記錄)。</span><span class="sxs-lookup"><span data-stu-id="dea15-157">The default value for this property is 1048576 (records).</span></span>  
  
 `CacheRecordLimit`  
 <span data-ttu-id="dea15-158">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-158">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `CheckDistinctRecordSortOrder`  
 <span data-ttu-id="dea15-159">此為布林值屬性，定義處理分割區時，相異計數查詢結果的排序順序是否有意義。</span><span class="sxs-lookup"><span data-stu-id="dea15-159">A Boolean property that defines if the sort order for the results of a distinct count query are meaningful when processing partitions.</span></span> <span data-ttu-id="dea15-160">True 表示排序順序沒有意義，且必須由伺服器進行「檢查」。</span><span class="sxs-lookup"><span data-stu-id="dea15-160">True indicates the sort order is not meaningful and must be "checked" by the server.</span></span> <span data-ttu-id="dea15-161">處理具有相異計數量值的分割區時，會使用 order-by 將查詢傳送到 SQL。</span><span class="sxs-lookup"><span data-stu-id="dea15-161">When processing partitions with distinct count measure, query sent to SQL with order-by.</span></span> <span data-ttu-id="dea15-162">設定為 False 即可加速處理。</span><span class="sxs-lookup"><span data-stu-id="dea15-162">Set to false to speed up processing.</span></span>  
  
 <span data-ttu-id="dea15-163">此屬性的預設值為 True，表示排序順序沒有意義且必須進行檢查。</span><span class="sxs-lookup"><span data-stu-id="dea15-163">The default value for this property is True, which indicates that the sort order is not meaningful and must be checked.</span></span>  
  
 `DatabaseConnectionPoolConnectTimeout`  
 <span data-ttu-id="dea15-164">此為帶正負號的 32 位元整數屬性，指定開啟新連接時的逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="dea15-164">A signed 32-bit integer property that specifies timeout when opening a new connection in seconds.</span></span>  
  
 `DatabaseConnectionPoolGeneralTimeout`  
 <span data-ttu-id="dea15-165">此為帶正負號的 32 位元整數屬性，指定與外部 OLEDB 連接一起使用時的資料庫連接逾時 (以秒為單位)。</span><span class="sxs-lookup"><span data-stu-id="dea15-165">A signed 32-bit integer property that specifies database connection timeout for use with external OLEDB connections in seconds.</span></span>  
  
 `DatabaseConnectionPoolMax`  
 <span data-ttu-id="dea15-166">此為帶正負號的 32 位元整數屬性，指定集區資料庫連接的最大數目。</span><span class="sxs-lookup"><span data-stu-id="dea15-166">A signed 32-bit integer property that specifies the maximum number of pooled database connections.</span></span>  
  
 <span data-ttu-id="dea15-167">此屬性的預設值為 50 (個連接)。</span><span class="sxs-lookup"><span data-stu-id="dea15-167">The default value for this property is 50 (connections).</span></span>  
  
 `DatabaseConnectionPoolTimeout`  
 <span data-ttu-id="dea15-168">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-168">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataFileInitEnabled`  
 <span data-ttu-id="dea15-169">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-169">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataPlacementOptimization`  
 <span data-ttu-id="dea15-170">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-170">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataSliceInitEnabled`  
 <span data-ttu-id="dea15-171">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-171">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DeepCompressValue`  
 <span data-ttu-id="dea15-172">此布林值屬性會套用到具 Double 資料類型的量值，以指定是否可壓縮數字而造成數值有效位數的遺失。</span><span class="sxs-lookup"><span data-stu-id="dea15-172">A Boolean property applying to measures with Double data type that specifies whether numbers can be compressed, causing a loss in numeric precision.</span></span> <span data-ttu-id="dea15-173">值為 False 表示不壓縮，且不會遺失有效位數。</span><span class="sxs-lookup"><span data-stu-id="dea15-173">A value of False indicates no compression and no precision loss.</span></span>  
  
 <span data-ttu-id="dea15-174">此屬性的預設值為 True，表示已啟用壓縮且會遺失有效位數。</span><span class="sxs-lookup"><span data-stu-id="dea15-174">The default value for this property is True, which indicates that compression is enabled and precision will be lost.</span></span>  
  
 `DimensionPropertyKeyCache`  
 <span data-ttu-id="dea15-175">此為布林值屬性，指定是否要快取維度屬性索引鍵。</span><span class="sxs-lookup"><span data-stu-id="dea15-175">A Boolean property that specifies whether dimension property keys are cached.</span></span> <span data-ttu-id="dea15-176">如果索引鍵為非唯一的，則必須設定為 True。</span><span class="sxs-lookup"><span data-stu-id="dea15-176">Must be set to True if keys are non-unique.</span></span>  
  
 `IndexBuildEnabled`  
 <span data-ttu-id="dea15-177">此為布林值屬性，指定是否在處理上建立索引。</span><span class="sxs-lookup"><span data-stu-id="dea15-177">A Boolean property that specifies whether indexes are built upon processing.</span></span> <span data-ttu-id="dea15-178">此屬性適用於效能評定和參考。</span><span class="sxs-lookup"><span data-stu-id="dea15-178">This property is for benchmarking and informational purposes.</span></span>  
  
 `IndexBuildThreshold`  
 <span data-ttu-id="dea15-179">此為帶正負號的 32 位元整數屬性，指定資料列計數的臨界值，在此臨界值之下將不會為分割區建立索引。</span><span class="sxs-lookup"><span data-stu-id="dea15-179">A signed 32-bit integer property that specifies a row count threshold below which indexes will not be built for partitions.</span></span>  
  
 <span data-ttu-id="dea15-180">這個屬性的預設值為 4096 (個資料列)。</span><span class="sxs-lookup"><span data-stu-id="dea15-180">The default value for this property is 4096 (rows).</span></span>  
  
 `IndexFileInitEnabled`  
 <span data-ttu-id="dea15-181">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-181">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MapFormatMask`  
 <span data-ttu-id="dea15-182">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-182">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `RecordsReportGranularity`  
 <span data-ttu-id="dea15-183">此為帶正負號的 32 位元整數屬性，指定處理期間伺服器記錄追蹤事件的頻率 (以資料列為單位)。</span><span class="sxs-lookup"><span data-stu-id="dea15-183">A signed 32-bit integer property that specifies how often the server records Trace events during processing, in rows.</span></span>  
  
 <span data-ttu-id="dea15-184">此屬性的預設值為 1000，表示每 1000 個資料列會記錄追蹤事件一次。</span><span class="sxs-lookup"><span data-stu-id="dea15-184">The default value for this property is 1000, which indicates that a Trace event is logged once every 1000 rows.</span></span>  
  
 `ROLAPDimensionProcessingEffort`  
 <span data-ttu-id="dea15-185">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-185">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="query"></a><span data-ttu-id="dea15-186">查詢</span><span class="sxs-lookup"><span data-stu-id="dea15-186">Query</span></span>  
 `AggregationsUseEnabled`  
 <span data-ttu-id="dea15-187">此為布林值屬性，定義在執行階段是否使用預存彙總。</span><span class="sxs-lookup"><span data-stu-id="dea15-187">A Boolean property that defines whether stored aggregations are used at runtime.</span></span> <span data-ttu-id="dea15-188">此屬性可以不必變更彙總設計或重新處理而停用彙總，適用於參考和效能評定。</span><span class="sxs-lookup"><span data-stu-id="dea15-188">This property allows aggregations to be disabled without changing the aggregation design or re-processing, for informational and benchmarking purposes.</span></span>  
  
 <span data-ttu-id="dea15-189">此屬性的預設值為 True，表示已啟用彙總。</span><span class="sxs-lookup"><span data-stu-id="dea15-189">The default value for this property is True, indicating that aggregations are enabled.</span></span>  
  
 `AllowSEFiltering`  
 <span data-ttu-id="dea15-190">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-190">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `CalculationCacheRegistryMaxIterations`  
 <span data-ttu-id="dea15-191">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-191">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `CalculationEvaluationPolicy`  
 <span data-ttu-id="dea15-192">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-192">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ConvertDeletedToUnknown`  
 <span data-ttu-id="dea15-193">此為布林值屬性，指定刪除的維度成員是否會轉換成未知的成員。</span><span class="sxs-lookup"><span data-stu-id="dea15-193">A Boolean property that specifies whether deleted dimension members are converted to Unknown member.</span></span>  
  
 `CopyLinkedDataCacheAndRegistry`  
 <span data-ttu-id="dea15-194">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-194">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCacheRegistryMaxIterations`  
 <span data-ttu-id="dea15-195">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-195">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DefaultDrillthroughMaxRows`  
 <span data-ttu-id="dea15-196">此為帶正負號的 32 位元整數屬性，指定從鑽研查詢傳回的最大資料列數目。</span><span class="sxs-lookup"><span data-stu-id="dea15-196">A signed 32-bit integer property that specifies the maximum number of rows that will return from a drill-through query.</span></span>  
  
 <span data-ttu-id="dea15-197">此屬性的預設值為 10000 (個資料列)。</span><span class="sxs-lookup"><span data-stu-id="dea15-197">The default value for this property is 10000 (rows).</span></span>  
  
 `DimensionPropertyCacheSize`  
 <span data-ttu-id="dea15-198">此為帶正負號的 32 位元整數屬性，指定用來快取查詢所使用之維度成員的記憶體數量 (位元組)。</span><span class="sxs-lookup"><span data-stu-id="dea15-198">A signed 32-bit integer property that specifies the amount of memory (in bytes) used to cache dimension members used in a query.</span></span>  
  
 <span data-ttu-id="dea15-199">預設值是每個屬性階層、每個使用中查詢 4,000,000 個位元組 (4 MB)。</span><span class="sxs-lookup"><span data-stu-id="dea15-199">The default is 4,000,000 bytes (or 4 MB) per attribute hierarchy, per active query.</span></span> <span data-ttu-id="dea15-200">預設值為有一般階層的方案提供平衡的快取大小。</span><span class="sxs-lookup"><span data-stu-id="dea15-200">The default value provides a well-balanced cache size for solutions having typical hierarchies.</span></span> <span data-ttu-id="dea15-201">不過，如果您增加此值，有極大量成員 (數百萬名) 或深度階層的維度會執行得更好。</span><span class="sxs-lookup"><span data-stu-id="dea15-201">However, dimensions with a very large number of members (in the millions) or deep hierarchies perform better if you increase this value.</span></span>  
  
 <span data-ttu-id="dea15-202">增加快取大小的含意：</span><span class="sxs-lookup"><span data-stu-id="dea15-202">Implications of increasing cache size:</span></span>  
  
-   <span data-ttu-id="dea15-203">當您允許維度快取使用更多記憶體時，記憶體使用量成本會增加。</span><span class="sxs-lookup"><span data-stu-id="dea15-203">Memory utilization costs increase when you allow more memory to be used by the dimension cache.</span></span> <span data-ttu-id="dea15-204">實際的使用量取決於查詢執行。</span><span class="sxs-lookup"><span data-stu-id="dea15-204">Actual usage depends on query execution.</span></span> <span data-ttu-id="dea15-205">並非所有的查詢都會使用最大允許值。</span><span class="sxs-lookup"><span data-stu-id="dea15-205">Not all queries will use the allowable maximum.</span></span>  
  
     <span data-ttu-id="dea15-206">請注意，這些快取所使用的記憶體會視為不可壓縮，而且會計入 **TotalMemoryLimit**。</span><span class="sxs-lookup"><span data-stu-id="dea15-206">Note that the memory used by these caches is considered nonshrinkable and will be included when accounting against the **TotalMemoryLimit**.</span></span>  
  
-   <span data-ttu-id="dea15-207">會影響伺服器上的所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="dea15-207">Affects all databases on the server.</span></span> <span data-ttu-id="dea15-208">**DimensionPropertyCachesize** 是伺服器範圍屬性。</span><span class="sxs-lookup"><span data-stu-id="dea15-208">**DimensionPropertyCachesize** is a server-wide property.</span></span> <span data-ttu-id="dea15-209">變更此屬性會影響在目前執行個體上執行的所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="dea15-209">Changing this property affects all databases running on the current instance.</span></span>  
  
 <span data-ttu-id="dea15-210">估計維度快取需求的方式：</span><span class="sxs-lookup"><span data-stu-id="dea15-210">Approach for estimating dimension cache requirements:</span></span>  
  
1.  <span data-ttu-id="dea15-211">一開始大量增加大小，決定增加維度快取大小是否有利。</span><span class="sxs-lookup"><span data-stu-id="dea15-211">Start by increasing the size by a large number to determine whether there is a benefit to increasing the dimension cache size.</span></span> <span data-ttu-id="dea15-212">例如，您可能會想要在初始步驟中將預設值加倍。</span><span class="sxs-lookup"><span data-stu-id="dea15-212">For example, you might want to double the default value as an initial step.</span></span>  
  
2.  <span data-ttu-id="dea15-213">如果效能明顯改善，請逐步遞減值，直到達到效能和記憶體使用量之間的平衡。</span><span class="sxs-lookup"><span data-stu-id="dea15-213">If a performance improvement is evident, incrementally reduce the value until you reach a balance between performance and memory utilization.</span></span>  
  
 `ExpressNonEmptyUseEnabled`  
 <span data-ttu-id="dea15-214">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-214">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `IgnoreNullRolapRows`  
 <span data-ttu-id="dea15-215">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-215">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `IndexUseEnabled`  
 <span data-ttu-id="dea15-216">此為布林值屬性，定義在執行階段是否使用索引。</span><span class="sxs-lookup"><span data-stu-id="dea15-216">A Boolean property that defines whether indexes are used at runtime.</span></span> <span data-ttu-id="dea15-217">此屬性適用於參考和效能評定。</span><span class="sxs-lookup"><span data-stu-id="dea15-217">This property is for informational and benchmarking purposes.</span></span>  
  
 `MapHandleAlgorithm`  
 <span data-ttu-id="dea15-218">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-218">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `MaxRolapOrConditions`  
 <span data-ttu-id="dea15-219">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-219">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `UseCalculationCacheRegistry`  
 <span data-ttu-id="dea15-220">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-220">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `UseDataCacheFreeLastPageMemory`  
 <span data-ttu-id="dea15-221">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-221">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `UseDataCacheRegistry`  
 <span data-ttu-id="dea15-222">此為布林值屬性，指定是否要啟用資料快取登錄，並在其中快取查詢結果 (雖然並非導出結果)。</span><span class="sxs-lookup"><span data-stu-id="dea15-222">A Boolean property that specifies whether to enable the data cache registry, where query results are cached (though not calculated results).</span></span>  
  
 `UseDataCacheRegistryHashTable`  
 <span data-ttu-id="dea15-223">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-223">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `UseDataCacheRegistryMultiplyKey`  
 <span data-ttu-id="dea15-224">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-224">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `UseDataSlice`  
 <span data-ttu-id="dea15-225">此為布林值屬性，定義在執行階段是否要針對查詢最佳化使用分割區的資料配量。</span><span class="sxs-lookup"><span data-stu-id="dea15-225">A Boolean property that defines whether to use partition data slices at runtime for query optimization.</span></span> <span data-ttu-id="dea15-226">此屬性適用於效能評定和參考。</span><span class="sxs-lookup"><span data-stu-id="dea15-226">This property is for benchmarking and informational purposes.</span></span>  
  
 `UseMaterializedIterators`  
 <span data-ttu-id="dea15-227">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-227">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `UseSinglePassForDimSecurityAutoExist`  
 <span data-ttu-id="dea15-228">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-228">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `UseVBANet`  
 <span data-ttu-id="dea15-229">此為布林值屬性，定義是否要針對使用者定義函數使用 VBA .net 組件。</span><span class="sxs-lookup"><span data-stu-id="dea15-229">A Boolean property that defines whether to use the VBA .net assembly for user-defined functions.</span></span>  
  
 `CalculationPrefetchLocality\ ApplyIntersect`  
 <span data-ttu-id="dea15-230">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-230">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `CalculationPrefetchLocality\ ApplySubtract`  
 <span data-ttu-id="dea15-231">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-231">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `CalculationPrefetchLocality\ PrefetchLowerGranularities`  
 <span data-ttu-id="dea15-232">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-232">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\  CachedPageAlloc\ Income`  
 <span data-ttu-id="dea15-233">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-233">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\  CachedPageAlloc\ InitialBonus`  
 <span data-ttu-id="dea15-234">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-234">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\  CachedPageAlloc\ MaximumBalance`  
 <span data-ttu-id="dea15-235">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-235">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\  CachedPageAlloc\ MinimumBalance`  
 <span data-ttu-id="dea15-236">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-236">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\  CachedPageAlloc\ Tax`  
 <span data-ttu-id="dea15-237">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-237">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\CellStore\ Income`  
 <span data-ttu-id="dea15-238">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-238">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\CellStore\ InitialBonus`  
 <span data-ttu-id="dea15-239">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-239">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\CellStore\ MaximumBalance`  
 <span data-ttu-id="dea15-240">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-240">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\CellStore\ MinimumBalance`  
 <span data-ttu-id="dea15-241">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-241">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\CellStore\ Tax`  
 <span data-ttu-id="dea15-242">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-242">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\ MemoryModel \ Income`  
 <span data-ttu-id="dea15-243">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-243">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\ MemoryModel \ InitialBonus`  
 <span data-ttu-id="dea15-244">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-244">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\ MemoryModel \ MaximumBalance`  
 <span data-ttu-id="dea15-245">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-245">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\ MemoryModel \ MinimumBalance`  
 <span data-ttu-id="dea15-246">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-246">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `DataCache\ MemoryModel\ Tax`  
 <span data-ttu-id="dea15-247">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-247">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="jobs"></a><span data-ttu-id="dea15-248">工作</span><span class="sxs-lookup"><span data-stu-id="dea15-248">Jobs</span></span>  
 `ProcessAggregation\ MemoryModel\ Income`  
 <span data-ttu-id="dea15-249">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-249">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ MemoryModel\ InitialBonus`  
 <span data-ttu-id="dea15-250">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-250">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ MemoryModel\ MaximumBalance`  
 <span data-ttu-id="dea15-251">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-251">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ MemoryModel\ MinimumBalance`  
 <span data-ttu-id="dea15-252">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-252">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ MemoryModel\ Tax`  
 <span data-ttu-id="dea15-253">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-253">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessPartition\ Income`  
 <span data-ttu-id="dea15-254">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-254">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessPartition \ InitialBonus`  
 <span data-ttu-id="dea15-255">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-255">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessPartition \ MaximumBalance`  
 <span data-ttu-id="dea15-256">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-256">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessPartition \ MinimumBalance`  
 <span data-ttu-id="dea15-257">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-257">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessPartition \ Tax`  
 <span data-ttu-id="dea15-258">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-258">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessProperty\ Income`  
 <span data-ttu-id="dea15-259">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-259">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessProperty\ InitialBonus`  
 <span data-ttu-id="dea15-260">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-260">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessProperty\ MaximumBalance`  
 <span data-ttu-id="dea15-261">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-261">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessProperty\ MinimumBalance`  
 <span data-ttu-id="dea15-262">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-262">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
 `ProcessAggregation\ ProcessProperty\ Tax`  
 <span data-ttu-id="dea15-263">此為進階屬性，除非在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 技術支援的指導之下，否則不應隨意變更。</span><span class="sxs-lookup"><span data-stu-id="dea15-263">An advanced property that you should not change, except under the guidance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] support.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dea15-264">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dea15-264">See Also</span></span>  
 <span data-ttu-id="dea15-265">[在 Analysis Services 中設定伺服器屬性](server-properties-in-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="dea15-265">[Configure Server Properties in Analysis Services](server-properties-in-analysis-services.md) </span></span>  
 [<span data-ttu-id="dea15-266">判斷 Analysis Services 執行個體的伺服器模式</span><span class="sxs-lookup"><span data-stu-id="dea15-266">Determine the Server Mode of an Analysis Services Instance</span></span>](../instances/determine-the-server-mode-of-an-analysis-services-instance.md)  
  
  
