---
title: " (資料採礦) 的處理需求和考慮 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], objects
- mining structures [Analysis Services], processing
- mining models [Analysis Services], processing
ms.assetid: f7331261-6f1c-4986-b2c7-740f4b92ca44
author: minewiskan
ms.author: owend
ms.openlocfilehash: f4b3f00692e58a55063a7d6bf4887dbee36df68c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703434"
---
# <a name="processing-requirements-and-considerations-data-mining"></a><span data-ttu-id="013ba-102">處理需求和考量 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="013ba-102">Processing Requirements and Considerations (Data Mining)</span></span>
  <span data-ttu-id="013ba-103">此主題描述在處理資料採礦物件時要記住的一些技術考量。</span><span class="sxs-lookup"><span data-stu-id="013ba-103">This topic describes some technical considerations to keep in mind when processing data mining objects.</span></span> <span data-ttu-id="013ba-104">如需什麼是處理以及如何將處理套用至資料採礦的一般說明，請參閱 [處理資料採礦物件](processing-data-mining-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="013ba-104">For a general explanation of what processing is, and how it applies to data mining, see [Processing Data Mining Objects](processing-data-mining-objects.md).</span></span>  
  
 [<span data-ttu-id="013ba-105">查詢關聯式存放區</span><span class="sxs-lookup"><span data-stu-id="013ba-105">Queries on Relational Store</span></span>](#bkmk_QueryReqs)  
  
 [<span data-ttu-id="013ba-106">處理採礦結構</span><span class="sxs-lookup"><span data-stu-id="013ba-106">Processing Mining Structures</span></span>](#bkmk_ProcessStructures)  
  
 [<span data-ttu-id="013ba-107">處理採礦模型</span><span class="sxs-lookup"><span data-stu-id="013ba-107">Processing Mining Models</span></span>](#bkmk_ProcessModels)  
  
##  <a name="queries-on-the-relational-store-during-processing"></a><a name="bkmk_QueryReqs"></a> <span data-ttu-id="013ba-108">在處理期間查詢關聯式存放區</span><span class="sxs-lookup"><span data-stu-id="013ba-108">Queries on the Relational Store during Processing</span></span>  
 <span data-ttu-id="013ba-109">對於資料採礦，處理可分成三個階段：查詢來源資料、判斷原始統計資料，以及使用模型定義和演算法來定型採礦模型。</span><span class="sxs-lookup"><span data-stu-id="013ba-109">For data mining, there are three phases to processing: querying the source data, determining raw statistics, and using the model definition and algorithm to train the mining model.</span></span>  
  
 <span data-ttu-id="013ba-110">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器會發出查詢給提供原始資料的資料庫。</span><span class="sxs-lookup"><span data-stu-id="013ba-110">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server issues queries to the database that provides the raw data.</span></span> <span data-ttu-id="013ba-111">這個資料庫可能是 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 或舊版 SQL Server 資料庫引擎的執行個體。</span><span class="sxs-lookup"><span data-stu-id="013ba-111">This database might be an instance of [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] or an earlier version of the SQL Server database engine.</span></span> <span data-ttu-id="013ba-112">當您處理資料採礦結構時，來源中的資料會傳送到採礦結構，並以新的壓縮格式保存在磁碟上。</span><span class="sxs-lookup"><span data-stu-id="013ba-112">When you process a data mining structure, the data in the source is transferred to the mining structure and persisted on disk in a new, compressed format.</span></span> <span data-ttu-id="013ba-113">系統並不會處理資料來源中的每個資料行，而只會處理包含在採礦結構中的資料行 (由繫結來定義)。</span><span class="sxs-lookup"><span data-stu-id="013ba-113">Not every column in the data source is processed: only the columns that are included in the mining structure, as defined by the bindings.</span></span>  
  
 <span data-ttu-id="013ba-114">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會使用這項資料來建置所有資料和離散化資料行的索引，而且會建立連續資料行的個別索引。</span><span class="sxs-lookup"><span data-stu-id="013ba-114">Using this data, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] builds an index of all data and discretized columns, and creates a separate index for continuous columns.</span></span> <span data-ttu-id="013ba-115">系統會針對每個巢狀資料表發出一個查詢，以便建立索引，而且會針對每個巢狀資料表產生額外的查詢，以便處理每對巢狀資料表與案例資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="013ba-115">One query is issued for each nested table to create the index, and an additional query per nested table is generated to process relationships between each pair of a nested table and case table.</span></span> <span data-ttu-id="013ba-116">建立多個查詢的原因是要處理特殊的內部多維度資料存放區。</span><span class="sxs-lookup"><span data-stu-id="013ba-116">The reason for creating multiple queries is to process a special internal multidimensional data store.</span></span> <span data-ttu-id="013ba-117">您可以透過設定伺服器屬性 `DatabaseConnectionPoolMax`，限制 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 傳送至關聯式存放區的查詢數目。</span><span class="sxs-lookup"><span data-stu-id="013ba-117">You can limit the number of queries that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] sends to the relational store by setting the server property, `DatabaseConnectionPoolMax`.</span></span> <span data-ttu-id="013ba-118">如需詳細資訊，請參閱 [OLAP 屬性](../server-properties/olap-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="013ba-118">For more information, see [OLAP Properties](../server-properties/olap-properties.md).</span></span>  
  
 <span data-ttu-id="013ba-119">當您處理模型時，模型並不會從資料來源重新讀取資料，而是從採礦結構取得資料摘要。</span><span class="sxs-lookup"><span data-stu-id="013ba-119">When you process the model, the model does not reread the data from the data source, but instead gets the summary of the data from the mining structure.</span></span> <span data-ttu-id="013ba-120">使用所建立的 Cube，連同快取索引及快取的案例資料之後，伺服器就會建立獨立的執行緒來定型模型。</span><span class="sxs-lookup"><span data-stu-id="013ba-120">Using the cube that was created, together with the cached index and case data has been cached, the server creates independent threads to train the models.</span></span>  
  
 <span data-ttu-id="013ba-121">如需支援平行模型處理之版本的詳細資訊 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱[SQL Server 2012 (版本支援的功能](https://go.microsoft.com/fwlink/?linkid=232473) https://go.microsoft.com/fwlink/?linkid=232473) 。</span><span class="sxs-lookup"><span data-stu-id="013ba-121">For more information about the editions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that support Parallel Model Processing, see [Features Supported by the Editions of SQL Server 2012](https://go.microsoft.com/fwlink/?linkid=232473) (https://go.microsoft.com/fwlink/?linkid=232473).</span></span>  
  
##  <a name="processing-mining-structures"></a><a name="bkmk_ProcessStructures"></a><span data-ttu-id="013ba-122">處理採礦結構</span><span class="sxs-lookup"><span data-stu-id="013ba-122">Processing Mining Structures</span></span>  
 <span data-ttu-id="013ba-123">採礦結構可以與所有相依模型一起處理，也可以單獨處理。</span><span class="sxs-lookup"><span data-stu-id="013ba-123">A mining structure can be processed together with all dependent models, or separately.</span></span> <span data-ttu-id="013ba-124">在預期某些模型需要長時間來處理並且您想要延遲該作業時，分開處理採礦結構與模型可能會很有用。</span><span class="sxs-lookup"><span data-stu-id="013ba-124">Processing a mining structure separately from models can be useful when some models are expected to take a long time to process and you want to defer that operation.</span></span>  
  
 <span data-ttu-id="013ba-125">如需詳細資訊，請參閱 [處理採礦結構](process-a-mining-structure.md)。</span><span class="sxs-lookup"><span data-stu-id="013ba-125">For more information, see [Process a Mining Structure](process-a-mining-structure.md).</span></span>  
  
 <span data-ttu-id="013ba-126">如果您希望節省硬碟空間，請注意 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會在本機保留採礦結構快取。</span><span class="sxs-lookup"><span data-stu-id="013ba-126">If you are concerned about conserving hard disk space, note that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] retains mining structure caches locally.</span></span> <span data-ttu-id="013ba-127">亦即，它會將所有培訓資料寫出至本機硬碟。</span><span class="sxs-lookup"><span data-stu-id="013ba-127">That is, it writes out all the training data to your local hard disk.</span></span> <span data-ttu-id="013ba-128">如果不要快取資料，您可以設定採礦結構的 <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> 屬性，將預設值變更為 `ClearAfterProcessing`。</span><span class="sxs-lookup"><span data-stu-id="013ba-128">If you do not want the data cached, you can change the default by setting the <xref:Microsoft.AnalysisServices.MiningStructureCacheMode> property on the mining structure to `ClearAfterProcessing`.</span></span> <span data-ttu-id="013ba-129">這會在處理模型之後終結快取，但是，它也會在採礦結構上停用鑽研。</span><span class="sxs-lookup"><span data-stu-id="013ba-129">This will destroy the cache after models are processed; however, it will also disable drillthrough on the mining structure.</span></span> <span data-ttu-id="013ba-130">如需詳細資訊，請參閱 [鑽研查詢 &#40;資料採礦&#41;](drillthrough-queries-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="013ba-130">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](drillthrough-queries-data-mining.md).</span></span>  
  
 <span data-ttu-id="013ba-131">同時，如果您清除快取，將無法使用鑑效組測試集；如果已經定義一個鑑效組測試集，將會遺失該測試集資料分割的定義。</span><span class="sxs-lookup"><span data-stu-id="013ba-131">Also, if you clear the cache, you will not be able to use the holdout test set, if you defined one, and the definition of the test set partition will be lost.</span></span> <span data-ttu-id="013ba-132">如需鑑效組測試集的詳細資訊，請參閱 [定型和測試資料集](training-and-testing-data-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="013ba-132">For more information about holdout test sets, see [Training and Testing Data Sets](training-and-testing-data-sets.md).</span></span>  
  
##  <a name="processing-mining-models"></a><a name="bkmk_ProcessModels"></a> <span data-ttu-id="013ba-133">處理採礦模型</span><span class="sxs-lookup"><span data-stu-id="013ba-133">Processing Mining Models</span></span>  
 <span data-ttu-id="013ba-134">您可以分開處理採礦模型與其相關聯的採礦結構，或是將以結構為基礎的所有模型與此結構一起處理。</span><span class="sxs-lookup"><span data-stu-id="013ba-134">You can process a mining model separately from its associated mining structure, or you can process all models that are based on the structure, together with the structure.</span></span>  
  
 <span data-ttu-id="013ba-135">如需詳細資訊，請參閱 [處理採礦模型](process-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="013ba-135">For more information, see [Process a Mining Model](process-a-mining-model.md).</span></span>  
  
 <span data-ttu-id="013ba-136">但在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，您無法複選多個要與結構一起處理的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="013ba-136">However, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], you cannot multiselect mining models to process with the structure.</span></span> <span data-ttu-id="013ba-137">如果您需要控制所處理的模型，則必須個別選取這些模型，或使用 XMLA 或 DMX 循序處理多個模型。</span><span class="sxs-lookup"><span data-stu-id="013ba-137">If you need to control which models are processed, you must select them individually, or use XMLA or DMX to process models serially.</span></span>  
  
## <a name="when-reprocessing-is-required"></a><span data-ttu-id="013ba-138">何時需要重新處理</span><span class="sxs-lookup"><span data-stu-id="013ba-138">When Reprocessing is Required</span></span>  
 <span data-ttu-id="013ba-139">您定義的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 模型必須經過處理之後才能開始使用。</span><span class="sxs-lookup"><span data-stu-id="013ba-139">You must process the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] models that you define before you can start to work with them.</span></span> <span data-ttu-id="013ba-140">每當變更採礦模型結構、更新定型資料、變更現有的採礦模型或將新的採礦模型加入結構中時，您也必須重新處理採礦模型。</span><span class="sxs-lookup"><span data-stu-id="013ba-140">You must also reprocess the mining models whenever you change the mining model structure, update the training data, change an existing mining model, or add a new mining model to the structure.</span></span>  
  
 <span data-ttu-id="013ba-141">在以下案例中也會處理採礦模型：</span><span class="sxs-lookup"><span data-stu-id="013ba-141">Mining models are also processed in these scenarios:</span></span>  
  
 <span data-ttu-id="013ba-142">**專案部署**：視專案設定和專案的目前狀態而定，在部署專案時通常會完整處理專案中的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="013ba-142">**Deployment of a project**: Depending on the project settings and the current state of the project, the mining models in the project are typically processed in full when the project is deployed.</span></span>  
  
 <span data-ttu-id="013ba-143">除非 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 伺服器上已有先前處理的版本，且尚無任何結構性變更，否則，起始部署時會自動開始處理。</span><span class="sxs-lookup"><span data-stu-id="013ba-143">When you initiate deployment, processing starts automatically, unless there is a previously processed version on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] server and there have been no structural changes.</span></span> <span data-ttu-id="013ba-144">您可以從下拉式清單中選取 [部署方案]\*\*\*\*，或按 F5 鍵來部署專案。</span><span class="sxs-lookup"><span data-stu-id="013ba-144">You can deploy a project by selecting **Deploy solution** from the drop-down list or by pressing the F5 key.</span></span> <span data-ttu-id="013ba-145">您可以</span><span class="sxs-lookup"><span data-stu-id="013ba-145">You can</span></span>  
  
 <span data-ttu-id="013ba-146">如需如何設定 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 部署屬性來控制採礦模型部署方式的詳細資訊，請參閱 [部署資料採礦方案](deployment-of-data-mining-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="013ba-146">For more information about how to set [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] deployment properties that control how mining models are deployed, see [Deployment of Data Mining Solutions](deployment-of-data-mining-solutions.md).</span></span>  
  
 <span data-ttu-id="013ba-147">**移動採礦模型**：在您透過使用 EXPORT 命令移動採礦模型時，只會匯出模型定義，其中包含應該向模型提供資料的採礦結構名稱。</span><span class="sxs-lookup"><span data-stu-id="013ba-147">**Moving a mining model**: When you move a mining model by using the EXPORT command, only the definition of the model is exported, which includes the name of the mining structure that is expected to provide data to the model.</span></span>  
  
 <span data-ttu-id="013ba-148">針對以下案例使用 EXPORT 和 IMPORT 命令進行重新處理的需求：</span><span class="sxs-lookup"><span data-stu-id="013ba-148">Reprocessing requirements for the following scenarios using the EXPORT and IMPORT commands:</span></span>  
  
-   <span data-ttu-id="013ba-149">採礦結構存在於目標執行個體上，並且採礦結構處於未處理狀態。</span><span class="sxs-lookup"><span data-stu-id="013ba-149">The mining structure exists on the target instance and the mining structure is in an unprocessed state.</span></span>  
  
     <span data-ttu-id="013ba-150">結構和模型都必須重新處理。</span><span class="sxs-lookup"><span data-stu-id="013ba-150">Both the structure and model must be reprocessed.</span></span>  
  
-   <span data-ttu-id="013ba-151">採礦結構存在於目標執行個體上，並且採礦結構已經處理。</span><span class="sxs-lookup"><span data-stu-id="013ba-151">The mining structure exists on the target instance and the mining structure has been processed.</span></span> <span data-ttu-id="013ba-152">只匯出了採礦模型。</span><span class="sxs-lookup"><span data-stu-id="013ba-152">Only the mining model was exported.</span></span>  
  
     <span data-ttu-id="013ba-153">模型不需處理即可使用。</span><span class="sxs-lookup"><span data-stu-id="013ba-153">The model can be used without processing.</span></span>  
  
-   <span data-ttu-id="013ba-154">也透過使用 WITH DEENDENCIES 關鍵字匯出了採礦結構定義。</span><span class="sxs-lookup"><span data-stu-id="013ba-154">The mining structure definition was also exported by using the WITH DEENDENCIES keyword.</span></span>  
  
     <span data-ttu-id="013ba-155">結構和模型都必須重新處理。</span><span class="sxs-lookup"><span data-stu-id="013ba-155">Both the structure and model must be reprocessed.</span></span>  
  
 <span data-ttu-id="013ba-156">如需詳細資訊，請參閱 [匯出和匯入資料採礦物件](export-and-import-data-mining-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="013ba-156">For more information, see [Export and Import Data Mining Objects](export-and-import-data-mining-objects.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="013ba-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="013ba-157">See Also</span></span>  
 <span data-ttu-id="013ba-158">[&#40;Analysis Services 的採礦結構-資料採礦&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="013ba-158">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="013ba-159">[&#40;Analysis Services 的採礦結構-資料採礦&#41;](mining-structures-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="013ba-159">[Mining Structures &#40;Analysis Services - Data Mining&#41;](mining-structures-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="013ba-160">多維度模型物件處理</span><span class="sxs-lookup"><span data-stu-id="013ba-160">Multidimensional Model Object Processing</span></span>](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)  
  
  
