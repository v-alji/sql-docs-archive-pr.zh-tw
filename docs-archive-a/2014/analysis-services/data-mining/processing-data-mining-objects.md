---
title: 處理資料採礦物件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- processing objects [Analysis Services]
- mining structures [Analysis Services]
- process [Analysis Services]
- mining structures [Analysis Services], creating
- mining structures [Analysis Services], how-to topics
- mining structures [Analysis Services], processing
ms.assetid: 0f6993c0-0917-4935-82f9-7b8a8a7cc627
author: minewiskan
ms.author: owend
ms.openlocfilehash: a4a6693a46679badc068111a311bb82219e752cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703438"
---
# <a name="processing-data-mining-objects"></a><span data-ttu-id="29c6b-102">處理資料採礦物件</span><span class="sxs-lookup"><span data-stu-id="29c6b-102">Processing Data Mining Objects</span></span>
  <span data-ttu-id="29c6b-103">資料採礦物件在處理之前只是一個空容器。</span><span class="sxs-lookup"><span data-stu-id="29c6b-103">A data mining object is only an empty container until it has been processed.</span></span> <span data-ttu-id="29c6b-104">*「處理」* (Processing) 資料採礦模型也稱為 *「定型」*(Training)。</span><span class="sxs-lookup"><span data-stu-id="29c6b-104">*Processing* a data mining model is also called *training*.</span></span>  
  
 <span data-ttu-id="29c6b-105">**處理採礦結構** ：採礦結構會從外部資料來源取得資料 (依資料行繫結和使用方式中繼資料的定義)，並讀取資料。</span><span class="sxs-lookup"><span data-stu-id="29c6b-105">**Processing mining structures:** A mining structure gets data from an external data source, as defined by the column bindings and usage metadata, and reads the data.</span></span> <span data-ttu-id="29c6b-106">系統會完整地讀取這項資料，再加以分析以擷取各種統計資料。</span><span class="sxs-lookup"><span data-stu-id="29c6b-106">This data is read in full and then analyzed to extract various statistics.</span></span> <span data-ttu-id="29c6b-107">Analysis Services 會在本機快取中儲存資料的壓縮表示 (適合以資料採礦演算法進行分析)。</span><span class="sxs-lookup"><span data-stu-id="29c6b-107">Analysis Services stores a compact representation of the data, which is suitable for analysis by data mining algorithms, in a local cache.</span></span> <span data-ttu-id="29c6b-108">您可在模型經過處理後保存此快取或加以刪除。</span><span class="sxs-lookup"><span data-stu-id="29c6b-108">You can either keep this cache or delete it after your models have been processed.</span></span> <span data-ttu-id="29c6b-109">依預設會儲存此快取。</span><span class="sxs-lookup"><span data-stu-id="29c6b-109">By default, the cache is stored.</span></span> <span data-ttu-id="29c6b-110">如需詳細資訊，請參閱 [處理採礦結構](process-a-mining-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="29c6b-110">For more information, see [Process a Mining Structure](process-a-mining-structure.md).</span></span>  
  
 <span data-ttu-id="29c6b-111">**處理採礦模型** ：採礦模型在處理之前是空的，只包含定義。</span><span class="sxs-lookup"><span data-stu-id="29c6b-111">**Processing mining models:** A mining model is empty, containing definitions only, until it is processed.</span></span> <span data-ttu-id="29c6b-112">若要處理採礦模型，則該模型所依據的採礦結構必須已經過處理。</span><span class="sxs-lookup"><span data-stu-id="29c6b-112">To process a mining model, the mining structure that it is based on must have been processed.</span></span> <span data-ttu-id="29c6b-113">採礦模型在從採礦結構快取取得資料之後，會套用已在模型上建立的任何篩選，然後再透過演算法傳遞資料集來偵測模式。</span><span class="sxs-lookup"><span data-stu-id="29c6b-113">The mining model gets the data from the mining structure cache, applies any filters that may have been created on the model, and then passes the data set through the algorithm to detect patterns.</span></span> <span data-ttu-id="29c6b-114">採礦模型在經過處理之後，只會儲存處理的結果，而非資料本身。</span><span class="sxs-lookup"><span data-stu-id="29c6b-114">After the model is processed, the model stores only the results of processing, not the data itself.</span></span> <span data-ttu-id="29c6b-115">如需詳細資訊，請參閱 [處理採礦模型](process-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="29c6b-115">For more information, see [Process a Mining Model](process-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="29c6b-116">下列圖表說明在處理採礦結構和資料模型時的資料流程。</span><span class="sxs-lookup"><span data-stu-id="29c6b-116">The following diagram illustrates the flow of data when a mining structure is processed, and when a mining model is processed.</span></span>  
  
 <span data-ttu-id="29c6b-117">![資料處理：來源到結構到模型](../media/dmcon-modelarch.gif "資料處理：來源到結構到模型")</span><span class="sxs-lookup"><span data-stu-id="29c6b-117">![Processing of data: source to structure to model](../media/dmcon-modelarch.gif "Processing of data: source to structure to model")</span></span>  
  
## <a name="viewing-the-results-of-processing"></a><span data-ttu-id="29c6b-118">檢視處理的結果</span><span class="sxs-lookup"><span data-stu-id="29c6b-118">Viewing the Results of Processing</span></span>  
 <span data-ttu-id="29c6b-119">採礦結構經過處理之後會包含資料的壓縮表示，以供統計資料分析使用。</span><span class="sxs-lookup"><span data-stu-id="29c6b-119">After a mining structure has been processed, it contains a compact representation of the data for use in statistical analysis.</span></span> <span data-ttu-id="29c6b-120">如果尚未清除快取，可以用下列方式存取此快取的資料：</span><span class="sxs-lookup"><span data-stu-id="29c6b-120">If the cache has not been cleared, you can access the data in this cache in the following ways:</span></span>  
  
-   <span data-ttu-id="29c6b-121">在模型上建立資料採礦延伸模組 (DMX) 查詢並鑽研至結構。</span><span class="sxs-lookup"><span data-stu-id="29c6b-121">Creating a Data Mining Extensions (DMX) query on the model and drilling through to the structure.</span></span> <span data-ttu-id="29c6b-122">如需詳細資訊，請參閱 [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx)。</span><span class="sxs-lookup"><span data-stu-id="29c6b-122">For more information, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).</span></span>  
  
-   <span data-ttu-id="29c6b-123">請根據結構瀏覽模型，並使用使用者介面中的一個選項以鑽研至結構案例。</span><span class="sxs-lookup"><span data-stu-id="29c6b-123">Browsing a model based on the structure, and using one of the options in the user interface to drill through to structure cases.</span></span> <span data-ttu-id="29c6b-124">如需詳細資訊，請參閱 [Data Mining Model Viewers](data-mining-model-viewers.md)(資料採礦模型檢視器) 或 [Drill Through to Case Data from a Mining Model](drill-through-to-case-data-from-a-mining-model.md)(鑽研採礦模型的案例資料)。</span><span class="sxs-lookup"><span data-stu-id="29c6b-124">For more information, see [Data Mining Model Viewers](data-mining-model-viewers.md), or [Drill Through to Case Data from a Mining Model](drill-through-to-case-data-from-a-mining-model.md).</span></span>  
  
-   <span data-ttu-id="29c6b-125">在結構案例上建立 DMX 查詢。</span><span class="sxs-lookup"><span data-stu-id="29c6b-125">Creating a DMX query on the structure cases.</span></span> <span data-ttu-id="29c6b-126">如需詳細資訊，請參閱 [SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases)。</span><span class="sxs-lookup"><span data-stu-id="29c6b-126">For more information, see [SELECT FROM &#60;structure&#62;.CASES](/sql/dmx/select-from-structure-cases).</span></span>  
  
 <span data-ttu-id="29c6b-127">採礦模型經過處理之後只會包含衍生自分析的模式，以及模型結果與快取之定型資料的對應。</span><span class="sxs-lookup"><span data-stu-id="29c6b-127">After a mining model has been processed, it contains only the patterns that were derived from analysis, and mappings from the model results to the cached training data.</span></span> <span data-ttu-id="29c6b-128">您可以瀏覽或查詢模型結果 (稱為 *「模型內容」*)，或者也可以查詢模型和結構案例 (若已存入快取)。</span><span class="sxs-lookup"><span data-stu-id="29c6b-128">You can browse or query the model results, called *model content*, or you can query the model and structure cases, if they have been cached.</span></span>  
  
 <span data-ttu-id="29c6b-129">每個採礦模型的模型內容都是根據建立時所使用的演算法而定。</span><span class="sxs-lookup"><span data-stu-id="29c6b-129">The model content for each mining model depends on the algorithm that was used to create it.</span></span> <span data-ttu-id="29c6b-130">例如，如果某個模式是叢集模型，而另一個模型是決策樹模型，則即使模型使用的資料完全相同，模型的內容也會非常不同。</span><span class="sxs-lookup"><span data-stu-id="29c6b-130">For example, if one model is a clustering model and another is a decision trees model, the model content is very different even though the models use exactly the same data.</span></span> <span data-ttu-id="29c6b-131">如需詳細資訊，請參閱[採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="29c6b-131">For more information, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
## <a name="processing-requirements"></a><span data-ttu-id="29c6b-132">處理需求</span><span class="sxs-lookup"><span data-stu-id="29c6b-132">Processing Requirements</span></span>  
 <span data-ttu-id="29c6b-133">根據採礦模型只根據關聯式資料還是多維度資料來源，處理需求可能會有所差異。</span><span class="sxs-lookup"><span data-stu-id="29c6b-133">Processing requirements may differ depending on whether your mining models are based solely on relational data, or on multidimensional data source.</span></span>  
  
 <span data-ttu-id="29c6b-134">如果是關聯式資料來源，處理作業只需要您建立定型資料，並在該資料上執行採礦演算法。</span><span class="sxs-lookup"><span data-stu-id="29c6b-134">For relational data source, processing requires only that you create training data and run mining algorithms on that data.</span></span> <span data-ttu-id="29c6b-135">但是，根據 OLAP 物件的採礦模型 (例如維度和量值) 需要基礎資料處於已處理的狀態。</span><span class="sxs-lookup"><span data-stu-id="29c6b-135">However, mining models that are based on OLAP objects, such as dimensions and measures, require that the underlying data be in a processed state.</span></span> <span data-ttu-id="29c6b-136">這可能需要處理多維度物件，才能擴展採礦模型。</span><span class="sxs-lookup"><span data-stu-id="29c6b-136">This may requires that the multidimensional objects be processed to populate the mining model.</span></span>  
  
 <span data-ttu-id="29c6b-137">如需詳細資訊，請參閱[處理需求和考量 &#40;資料採礦&#41;](processing-requirements-and-considerations-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="29c6b-137">For more information, see [Processing Requirements and Considerations &#40;Data Mining&#41;](processing-requirements-and-considerations-data-mining.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29c6b-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="29c6b-138">See Also</span></span>  
 <span data-ttu-id="29c6b-139">[資料採礦&#41;&#40;的鑽取查詢](drillthrough-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="29c6b-139">[Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md) </span></span>  
 <span data-ttu-id="29c6b-140">[&#40;Analysis Services 的採礦結構-資料採礦&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="29c6b-140">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="29c6b-141">[&#40;Analysis Services 的採礦模型-資料採礦&#41;](mining-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="29c6b-141">[Mining Models &#40;Analysis Services - Data Mining&#41;](mining-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="29c6b-142">邏輯架構 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="29c6b-142">Logical Architecture &#40;Analysis Services - Data Mining&#41;</span></span>](logical-architecture-analysis-services-data-mining.md)  
  
  
