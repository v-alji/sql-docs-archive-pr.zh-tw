---
title: 設定量值群組屬性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- properties [Analysis Services], measure groups
ms.assetid: fa66bdb6-60b8-413c-ac2a-00e4d09f60a2
author: minewiskan
ms.author: owend
ms.openlocfilehash: 03dad3d8ee33ea8a78b08f9a354d0db3d177198c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705650"
---
# <a name="configure-measure-group-properties"></a><span data-ttu-id="f7256-102">設定量值群組屬性</span><span class="sxs-lookup"><span data-stu-id="f7256-102">Configure Measure Group Properties</span></span>
  <span data-ttu-id="f7256-103">量值群組有一些屬性可讓您定義量值群組的運作方式。</span><span class="sxs-lookup"><span data-stu-id="f7256-103">Measures groups have properties that enable you to define how measure groups function.</span></span>  
  
## <a name="measure-group-properties"></a><span data-ttu-id="f7256-104">量值群組屬性</span><span class="sxs-lookup"><span data-stu-id="f7256-104">Measure Group Properties</span></span>  
 <span data-ttu-id="f7256-105">量值群組屬性會決定整個量值群組的行為，以及設定量值群組內量值之某些屬性的預設行為。</span><span class="sxs-lookup"><span data-stu-id="f7256-105">Measure group properties determine behaviors for the entire measure group and set the default behaviors for certain properties of measures within a measure group.</span></span>  
  
|<span data-ttu-id="f7256-106">屬性</span><span class="sxs-lookup"><span data-stu-id="f7256-106">Property</span></span>|<span data-ttu-id="f7256-107">定義</span><span class="sxs-lookup"><span data-stu-id="f7256-107">Definition</span></span>|  
|--------------|----------------|  
|`AggregationPrefix`|<span data-ttu-id="f7256-108">套用至 ROLAP 儲存體。</span><span class="sxs-lookup"><span data-stu-id="f7256-108">Applies to ROLAP storage.</span></span> <span data-ttu-id="f7256-109">指派一般的前置詞給 SQL Server 中的索引檢視表，以供儲存此量值群組所關聯之資料分割的彙總。</span><span class="sxs-lookup"><span data-stu-id="f7256-109">Assigns a common prefix to the indexed views in SQL Server, used to store aggregations for the partitions associated with this measure group.</span></span>|  
|`DataAggregation`|<span data-ttu-id="f7256-110">此屬性保留供日後使用，目前沒有任何作用。</span><span class="sxs-lookup"><span data-stu-id="f7256-110">This property is reserved for future use and currently has no effect.</span></span> <span data-ttu-id="f7256-111">建議您不要修改此設定。</span><span class="sxs-lookup"><span data-stu-id="f7256-111">Therefore, it is recommended that you do not modify this setting.</span></span>|  
|`Description`|<span data-ttu-id="f7256-112">您可以使用此屬性記錄量值群組。</span><span class="sxs-lookup"><span data-stu-id="f7256-112">You can use this property to document the measure group.</span></span>|  
|`ErrorConfiguration`|<span data-ttu-id="f7256-113">用於處理重複索引鍵、未知索引鍵、Null 索引鍵、錯誤限制、偵測到錯誤時的動作和錯誤記錄檔的可設定錯誤處理設定。</span><span class="sxs-lookup"><span data-stu-id="f7256-113">Configurable error handling settings for handling of duplicate keys, unknown keys, null keys, error limits, action upon error detection, and the error log file.</span></span> <span data-ttu-id="f7256-114">請參閱[設定 Cube、資料分割和維度處理時發生錯誤 &#40;SSAS - 多維度&#41;](error-configuration-for-cube-partition-and-dimension-processing.md)。</span><span class="sxs-lookup"><span data-stu-id="f7256-114">See [Error Configuration for Cube, Partition, and Dimension Processing &#40;SSAS - Multidimensional&#41;](error-configuration-for-cube-partition-and-dimension-processing.md).</span></span>|  
|`EstimatedRows`|<span data-ttu-id="f7256-115">指定事實資料表中的估計資料列數目。</span><span class="sxs-lookup"><span data-stu-id="f7256-115">Specifies the estimated number of rows in the fact table.</span></span>|  
|`EstimatedSize`|<span data-ttu-id="f7256-116">指定量值群組的估計大小 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="f7256-116">Specifies the estimated size (in bytes) of the measure group.</span></span>|  
|`ID`|<span data-ttu-id="f7256-117">指定物件的識別碼。</span><span class="sxs-lookup"><span data-stu-id="f7256-117">Specifies the identifier of the object.</span></span>|  
|`IgnoreUnrelatedDimensions`|<span data-ttu-id="f7256-118">決定當查詢中包含與量值群組不相關的維度成員時，是否將不相關的維度強制在其最上層。</span><span class="sxs-lookup"><span data-stu-id="f7256-118">Determines whether unrelated dimensions are forced to their top level when members of dimensions that are unrelated to the measure group are included in a query.</span></span> <span data-ttu-id="f7256-119">預設值是 `True`。</span><span class="sxs-lookup"><span data-stu-id="f7256-119">Default setting is `True`.</span></span>|  
|`Name`|<span data-ttu-id="f7256-120">量值的名稱。</span><span class="sxs-lookup"><span data-stu-id="f7256-120">Name of the measure.</span></span> <span data-ttu-id="f7256-121">這個屬性是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="f7256-121">This property is read-only.</span></span>|  
|`ProactiveCaching`|<span data-ttu-id="f7256-122">用於處理重複索引鍵、未知索引鍵、Null 索引鍵、錯誤限制、偵測到錯誤時的動作和錯誤記錄檔的可設定錯誤處理設定。</span><span class="sxs-lookup"><span data-stu-id="f7256-122">Configurable error handling settings for handling of duplicate keys, unknown keys, null keys, error limits, action upon error detection, and the error log file.</span></span>|  
|`ProcessingMode`|<span data-ttu-id="f7256-123">指出在處理期間或處理之後，是否應該進行檢索和彙總。</span><span class="sxs-lookup"><span data-stu-id="f7256-123">Indicates whether indexing and aggregating should occur during or after processing.</span></span> <span data-ttu-id="f7256-124">選項為 Regular 和 LazyAggregations。</span><span class="sxs-lookup"><span data-stu-id="f7256-124">Options are Regular and LazyAggregations.</span></span> <span data-ttu-id="f7256-125">LazyAggregations 可以用於將彙總以背景工作方式執行。</span><span class="sxs-lookup"><span data-stu-id="f7256-125">LazyAggregations can be used to run aggregation as a background task.</span></span>|  
|`ProcessingPriority`|<span data-ttu-id="f7256-126">決定 Cube 在背景作業 (例如延遲彙總和索引) 期間的處理優先權。</span><span class="sxs-lookup"><span data-stu-id="f7256-126">Determines the processing priority of the cube during background operations, such as lazy aggregations and indexing.</span></span> <span data-ttu-id="f7256-127">預設值為**0**。</span><span class="sxs-lookup"><span data-stu-id="f7256-127">The default value is **0**.</span></span>|  
|`StorageLocation`|<span data-ttu-id="f7256-128">量值群組的檔案系統儲存位置。</span><span class="sxs-lookup"><span data-stu-id="f7256-128">The file system storage location for the measure group.</span></span> <span data-ttu-id="f7256-129">如果未指定，則會從包含該量值群組的 Cube 中繼承位置。</span><span class="sxs-lookup"><span data-stu-id="f7256-129">If none is specified, the location is inherited from the cube that contains the measure group.</span></span>|  
|`StorageMode`|<span data-ttu-id="f7256-130">量值群組的儲存模式。</span><span class="sxs-lookup"><span data-stu-id="f7256-130">The storage mode for the measure group.</span></span> <span data-ttu-id="f7256-131">可用的值為 MOLAP、ROLAP 或 HOLAP。</span><span class="sxs-lookup"><span data-stu-id="f7256-131">Available values are MOLAP, ROLAP, or HOLAP.</span></span>|  
|`Type`|<span data-ttu-id="f7256-132">指定量值群組的類型。</span><span class="sxs-lookup"><span data-stu-id="f7256-132">Specifies the type of the measure group.</span></span>|  
  
  
