---
title: Cube 屬性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- Collation property
- ID property
- ErrorConfiguration property
- cubes [Analysis Services], properties
- Description property
- DefaultMeasure property
- ProcessingMode property
- AggregationPrefix property
- EstimatedRows property
- Visible property
- StorageLocation property
- StorageMode property
- ScriptErrorHandlingMode property
- Source property
- ScriptCacheProcessingMode property
- Language property
- Name property
- properties [Analysis Services], cubes
- ProcessingPriority property
- ProactiveCaching property
ms.assetid: 72ca3387-620d-4473-8e23-7fe1f2b3d5bf
author: minewiskan
ms.author: owend
ms.openlocfilehash: 27d4202774107795eaddf76c27e21010d534d977
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592312"
---
# <a name="cube-properties"></a><span data-ttu-id="a3a3e-102">Cube 屬性</span><span class="sxs-lookup"><span data-stu-id="a3a3e-102">Cube Properties</span></span>
  <span data-ttu-id="a3a3e-103">Cube 有許多屬性，您可以設定這些屬性來影響整個 Cube 的行為。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-103">Cubes have a number of properties that you can set to affect cube-wide behavior.</span></span> <span data-ttu-id="a3a3e-104">這些屬性都摘要在下表中：</span><span class="sxs-lookup"><span data-stu-id="a3a3e-104">These properties are summarized in the following table.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a3a3e-105">有些屬性是在建立 Cube 時自動設定，且無法變更。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-105">Some properties are set automatically when the cube is created and cannot be changed.</span></span>  
  
 <span data-ttu-id="a3a3e-106">如需如何設定 cube 屬性的詳細資訊，請參閱[Cube 設計師 &#40;Analysis Services 多維度資料&#41;](../cube-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-106">For more information about how to set cube properties, see [Cube Designer &#40;Analysis Services - Multidimensional Data&#41;](../cube-designer-analysis-services-multidimensional-data.md).</span></span>  
  
|<span data-ttu-id="a3a3e-107">屬性</span><span class="sxs-lookup"><span data-stu-id="a3a3e-107">Property</span></span>|<span data-ttu-id="a3a3e-108">描述</span><span class="sxs-lookup"><span data-stu-id="a3a3e-108">Description</span></span>|  
|--------------|-----------------|  
|`AggregationPrefix`|<span data-ttu-id="a3a3e-109">指定用於彙總名稱的一般前置詞。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-109">Specifies the common prefix that is used for aggregation names.</span></span>|  
|`Collation`|<span data-ttu-id="a3a3e-110">指定用底線隔開的地區設定識別碼 (LCID) 和比較旗標 (例如，Latin1_General_C1_AS)。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-110">Specifies the locale identifier (LCID) and the comparison flag, separated by an underscore: for example, Latin1_General_C1_AS.</span></span>|  
|`DefaultMeasure`|<span data-ttu-id="a3a3e-111">包含定義 Cube 之預設量值的多維度運算式 (MDX) 運算式。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-111">Contains a Multidimensional Expressions (MDX) expression that defines the default measure for the cube.</span></span>|  
|`Description`|<span data-ttu-id="a3a3e-112">提供 Cube 的描述，可以在用戶端應用程式中公開。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-112">Provides a description of the cube, which may be exposed in client applications.</span></span>|  
|`ErrorConfiguration`|<span data-ttu-id="a3a3e-113">包含用來處理重複索引鍵、未知索引鍵、錯誤限制、發生錯誤時的動作、錯誤記錄檔和 Null 索引鍵處理的可設定錯誤處理設定。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-113">Contains configurable error handling settings for handling of duplicate keys, unknown keys, error limits, action upon error detection, error log file, and null key handling.</span></span>|  
|`EstimatedRows`|<span data-ttu-id="a3a3e-114">指定 Cube 中的估計資料列數目。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-114">Specifies the number of estimated rows in the cube.</span></span>|  
|`ID`|<span data-ttu-id="a3a3e-115">包含 Cube 的唯一識別碼 (ID)。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-115">Contains the unique identifier (ID) of the cube.</span></span>|  
|`Language`|<span data-ttu-id="a3a3e-116">指定 Cube 的預設語言識別碼。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-116">Specifies the default language identifier of the cube.</span></span>|  
|`Name`|<span data-ttu-id="a3a3e-117">指定 Cube 的使用者易記名稱。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-117">Specifies the user-friendly name of the cube.</span></span>|  
|`ProactiveCaching`|<span data-ttu-id="a3a3e-118">定義 Cube 的主動式快取設定。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-118">Defines proactive cache settings for the cube.</span></span>|  
|`ProcessingMode`|<span data-ttu-id="a3a3e-119">指出在處理期間或處理之後，是否應該進行檢索和彙總。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-119">Indicates whether indexing and aggregating should occur during or after processing.</span></span> <span data-ttu-id="a3a3e-120">選項為 [**一般**] 或 [] `lazy` 。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-120">Options are **regular** or `lazy`.</span></span>|  
|`ProcessingPriority`|<span data-ttu-id="a3a3e-121">決定 Cube 在背景作業 (例如延遲彙總和索引) 期間的處理優先權。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-121">Determines the processing priority of the cube during background operations, such as lazy aggregations and indexing.</span></span> <span data-ttu-id="a3a3e-122">預設值為**0**。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-122">The default value is **0**.</span></span>|  
|`ScriptCacheProcessingMode`|<span data-ttu-id="a3a3e-123">指出在處理期間或處理之後是否應建立指令碼快取。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-123">Indicates whether the script cache should be built during or after processing.</span></span> <span data-ttu-id="a3a3e-124">選項為**一般**和 `lazy` 。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-124">Options are **regular** and `lazy`.</span></span>|  
|`ScriptErrorHandlingMode`|<span data-ttu-id="a3a3e-125">決定錯誤處理。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-125">Determines error handling.</span></span> <span data-ttu-id="a3a3e-126">選項為 `IgnoreNone` 或 `IgnoreAll`。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-126">Options are `IgnoreNone` or `IgnoreAll`</span></span>|  
|`Source`|<span data-ttu-id="a3a3e-127">顯示用於 Cube 的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-127">Displays the data source view used for the cube.</span></span>|  
|`StorageLocation`|<span data-ttu-id="a3a3e-128">指定 Cube 的檔案系統儲存位置。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-128">Specifies the file system storage location for the cube.</span></span> <span data-ttu-id="a3a3e-129">如果未指定，會從包含 Cube 物件的資料庫中繼承位置。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-129">If none is specified, the location is inherited from the database that contains the cube object.</span></span>|  
|`StorageMode`|<span data-ttu-id="a3a3e-130">指定 Cube 的儲存模式。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-130">Specifies the storage mode for the cube.</span></span> <span data-ttu-id="a3a3e-131">值為 `MOLAP` 、 `ROLAP` 或。`HOLAP``.`</span><span class="sxs-lookup"><span data-stu-id="a3a3e-131">Values are `MOLAP`, `ROLAP`, or `HOLAP``.`</span></span>|  
|`Visible`|<span data-ttu-id="a3a3e-132">決定 Cube 的可見性。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-132">Determines the visibility of the cube.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="a3a3e-133">如需在使用 null 值和其他資料完整性問題時設定 ErrorConfiguration 屬性值的詳細資訊，請參閱[處理 Analysis Services 2005 中的資料完整性問題](https://go.microsoft.com/fwlink/?LinkId=81891)。</span><span class="sxs-lookup"><span data-stu-id="a3a3e-133">For more information about setting values for the ErrorConfiguration property when working with null values and other data integrity issues, see [Handling Data Integrity Issues in Analysis Services 2005](https://go.microsoft.com/fwlink/?LinkId=81891).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3a3e-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3a3e-134">See Also</span></span>  
 [<span data-ttu-id="a3a3e-135">主動式快取 &#40;分割區&#41;</span><span class="sxs-lookup"><span data-stu-id="a3a3e-135">Proactive Caching &#40;Partitions&#41;</span></span>](partitions-proactive-caching.md)  
  
  
