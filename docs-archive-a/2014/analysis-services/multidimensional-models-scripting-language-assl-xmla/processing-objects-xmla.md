---
title: 處理 (XMLA) 的物件 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- errors [XML for Analysis]
- objects [XML for Analysis]
- XML for Analysis, objects
- XMLA, partitions
- partitions [Analysis Services], XML for Analysis
- XML for Analysis, partitions
- writeback [Analysis Services], XML for Analysis
- out-of-line bindings
- processing objects [XML for Analysis]
- XMLA, objects
ms.assetid: a65b3249-303d-49c6-98af-6ac6eed11a03
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2e59c7953ae8fc7d3cfceafa7b0e9d8c7186daf8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706866"
---
# <a name="processing-objects-xmla"></a><span data-ttu-id="927e4-102">處理物件 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="927e4-102">Processing Objects (XMLA)</span></span>
  <span data-ttu-id="927e4-103">在中 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，處理是將資料轉換成商務分析資訊的步驟或一系列步驟。</span><span class="sxs-lookup"><span data-stu-id="927e4-103">In [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], processing is the step or series of steps that turn data into information for business analysis.</span></span> <span data-ttu-id="927e4-104">處理會因物件類型而異，但是處理永遠都是將資料轉換為資訊的一部分。</span><span class="sxs-lookup"><span data-stu-id="927e4-104">Processing is different depending on the type of object, but processing is always part of turning data into information.</span></span>  
  
 <span data-ttu-id="927e4-105">若要處理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件，您可以使用[process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)命令。</span><span class="sxs-lookup"><span data-stu-id="927e4-105">To process an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] object, you can use the [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla) command.</span></span> <span data-ttu-id="927e4-106">`Process` 命令可以處理在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上的下列物件：</span><span class="sxs-lookup"><span data-stu-id="927e4-106">The `Process` command can process the following objects on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance:</span></span>  
  
-   <span data-ttu-id="927e4-107">Cube</span><span class="sxs-lookup"><span data-stu-id="927e4-107">Cubes</span></span>  
  
-   <span data-ttu-id="927e4-108">資料庫</span><span class="sxs-lookup"><span data-stu-id="927e4-108">Databases</span></span>  
  
-   <span data-ttu-id="927e4-109">維度</span><span class="sxs-lookup"><span data-stu-id="927e4-109">Dimensions</span></span>  
  
-   <span data-ttu-id="927e4-110">量值群組</span><span class="sxs-lookup"><span data-stu-id="927e4-110">Measure groups</span></span>  
  
-   <span data-ttu-id="927e4-111">採礦模型</span><span class="sxs-lookup"><span data-stu-id="927e4-111">Mining models</span></span>  
  
-   <span data-ttu-id="927e4-112">採礦結構</span><span class="sxs-lookup"><span data-stu-id="927e4-112">Mining structures</span></span>  
  
-   <span data-ttu-id="927e4-113">資料分割</span><span class="sxs-lookup"><span data-stu-id="927e4-113">Partitions</span></span>  
  
 <span data-ttu-id="927e4-114">若要控制物件的處理，`Process` 命令具有各種可以設定的屬性。</span><span class="sxs-lookup"><span data-stu-id="927e4-114">To control the processing of objects, the `Process` command has various properties that can be set.</span></span> <span data-ttu-id="927e4-115">`Process` 命令具有可控制以下動作的屬性：將完成多少處理、將處理哪些物件、是否使用非正規的繫結、如何處理錯誤以及如何管理回寫資料表。</span><span class="sxs-lookup"><span data-stu-id="927e4-115">The `Process` command has properties that control: how much processing will be done, which objects will be processed, whether to use out-of-line bindings, how to handle errors, and how to manage writeback tables.</span></span>  
  
## <a name="specifying-processing-options"></a><span data-ttu-id="927e4-116">指定處理選項</span><span class="sxs-lookup"><span data-stu-id="927e4-116">Specifying Processing Options</span></span>  
 <span data-ttu-id="927e4-117">命令的[Type](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla)屬性會 `Process` 指定處理物件時所要使用的處理選項。</span><span class="sxs-lookup"><span data-stu-id="927e4-117">The [Type](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) property of the `Process` command specifies the processing option to use when processing the object.</span></span> <span data-ttu-id="927e4-118">如需處理選項的詳細資訊，請參閱[處理選項和設定 &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="927e4-118">For more information about processing options, see [Processing Options and Settings &#40;Analysis Services&#41;](../multidimensional-models/processing-options-and-settings-analysis-services.md).</span></span>  
  
 <span data-ttu-id="927e4-119">下表列出 `Type` 屬性的常數，以及各種可使用每個常數處理的物件。</span><span class="sxs-lookup"><span data-stu-id="927e4-119">The following table lists the constants for the `Type` property and the various objects that can be processed using each constant.</span></span>  
  
|<span data-ttu-id="927e4-120">`Type` 值</span><span class="sxs-lookup"><span data-stu-id="927e4-120">`Type` value</span></span>|<span data-ttu-id="927e4-121">適用的物件</span><span class="sxs-lookup"><span data-stu-id="927e4-121">Applicable objects</span></span>|  
|--------------------|------------------------|  
|<span data-ttu-id="927e4-122">*ProcessFull*</span><span class="sxs-lookup"><span data-stu-id="927e4-122">*ProcessFull*</span></span>|<span data-ttu-id="927e4-123">Cube、資料庫、維度、量值群組、採礦模型、採礦結構、資料分割</span><span class="sxs-lookup"><span data-stu-id="927e4-123">Cube, database, dimension, measure group, mining model, mining structure, partition</span></span>|  
|<span data-ttu-id="927e4-124">*ProcessAdd*</span><span class="sxs-lookup"><span data-stu-id="927e4-124">*ProcessAdd*</span></span>|<span data-ttu-id="927e4-125">維度、資料分割</span><span class="sxs-lookup"><span data-stu-id="927e4-125">Dimension, partition</span></span>|  
|<span data-ttu-id="927e4-126">*ProcessUpdate*</span><span class="sxs-lookup"><span data-stu-id="927e4-126">*ProcessUpdate*</span></span>|<span data-ttu-id="927e4-127">維度</span><span class="sxs-lookup"><span data-stu-id="927e4-127">Dimension</span></span>|  
|<span data-ttu-id="927e4-128">*ProcessIndexes*</span><span class="sxs-lookup"><span data-stu-id="927e4-128">*ProcessIndexes*</span></span>|<span data-ttu-id="927e4-129">維度、Cube、量值群組，磁碟分割</span><span class="sxs-lookup"><span data-stu-id="927e4-129">Dimension, cube, measure group, partition</span></span>|  
|<span data-ttu-id="927e4-130">*ProcessData*</span><span class="sxs-lookup"><span data-stu-id="927e4-130">*ProcessData*</span></span>|<span data-ttu-id="927e4-131">維度、Cube、量值群組，磁碟分割</span><span class="sxs-lookup"><span data-stu-id="927e4-131">Dimension, cube, measure group, partition</span></span>|  
|<span data-ttu-id="927e4-132">*ProcessDefault*</span><span class="sxs-lookup"><span data-stu-id="927e4-132">*ProcessDefault*</span></span>|<span data-ttu-id="927e4-133">Cube、資料庫、維度、量值群組、採礦模型、採礦結構、資料分割</span><span class="sxs-lookup"><span data-stu-id="927e4-133">Cube, database, dimension, measure group, mining model, mining structure, partition</span></span>|  
|<span data-ttu-id="927e4-134">*ProcessClear*</span><span class="sxs-lookup"><span data-stu-id="927e4-134">*ProcessClear*</span></span>|<span data-ttu-id="927e4-135">Cube、資料庫、維度、量值群組、採礦模型、採礦結構、資料分割</span><span class="sxs-lookup"><span data-stu-id="927e4-135">Cube, database, dimension, measure group, mining model, mining structure, partition</span></span>|  
|<span data-ttu-id="927e4-136">*ProcessStructure*</span><span class="sxs-lookup"><span data-stu-id="927e4-136">*ProcessStructure*</span></span>|<span data-ttu-id="927e4-137">Cube、採礦結構</span><span class="sxs-lookup"><span data-stu-id="927e4-137">Cube, mining structure</span></span>|  
|<span data-ttu-id="927e4-138">*ProcessClearStructureOnly*</span><span class="sxs-lookup"><span data-stu-id="927e4-138">*ProcessClearStructureOnly*</span></span>|<span data-ttu-id="927e4-139">採礦結構</span><span class="sxs-lookup"><span data-stu-id="927e4-139">Mining structure</span></span>|  
|<span data-ttu-id="927e4-140">*ProcessScriptCache*</span><span class="sxs-lookup"><span data-stu-id="927e4-140">*ProcessScriptCache*</span></span>|<span data-ttu-id="927e4-141">Cube</span><span class="sxs-lookup"><span data-stu-id="927e4-141">Cube</span></span>|  
  
 <span data-ttu-id="927e4-142">如需處理物件的詳細資訊 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，請參閱多[維度模型物件處理](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="927e4-142">For more information about processing [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects, see [Multidimensional Model Object Processing](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md).</span></span>  
  
## <a name="specifying-objects-to-be-processed"></a><span data-ttu-id="927e4-143">指定要處理的物件</span><span class="sxs-lookup"><span data-stu-id="927e4-143">Specifying Objects to be Processed</span></span>  
 <span data-ttu-id="927e4-144">命令的[object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)屬性 `Process` 包含要處理之物件的物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="927e4-144">The [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property of the `Process` command contains the object identifier of the object to be processed.</span></span> <span data-ttu-id="927e4-145">在 `Process` 命令中只能指定一個物件，但是處理物件也會處理任何子系物件。</span><span class="sxs-lookup"><span data-stu-id="927e4-145">Only one object can be specified in a `Process` command, but processing an object also processes any child objects.</span></span> <span data-ttu-id="927e4-146">例如，在 Cube 處理序中處理量值群組會處理該量值群組的所有資料分割，然而處理資料庫處理序則會處理資料庫包含的所有物件，包括 Cube、維度和採礦結構。</span><span class="sxs-lookup"><span data-stu-id="927e4-146">For example, processing a measure group in a cube processes all the partitions for that measure group, while processing a database processes all the objects, including cubes, dimensions, and mining structures, that are contained by the database.</span></span>  
  
 <span data-ttu-id="927e4-147">如果您將 `ProcessAffectedObjects` 命令的 `Process` 屬性設定為 True，則也會處理指定物件所影響的任何相關物件。</span><span class="sxs-lookup"><span data-stu-id="927e4-147">If you set the `ProcessAffectedObjects` attribute of the `Process` command to true, any related object affected by processing the specified object is also processed.</span></span> <span data-ttu-id="927e4-148">例如，如果維度是使用命令中的 [ *ProcessUpdate*處理] 選項進行累加更新 `Process` ，則任何匯總因為加入或刪除的成員而失效的資料分割，也會在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] `ProcessAffectedObjects` 設定為 true 時由處理。</span><span class="sxs-lookup"><span data-stu-id="927e4-148">For example, if a dimension is incrementally updated by using the *ProcessUpdate* processing option in the `Process` command, any partition whose aggregations are invalidated because of members being added or deleted is also processed by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] if `ProcessAffectedObjects` is set to true.</span></span> <span data-ttu-id="927e4-149">在這種情況下，單一 `Process` 命令可以處理在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上的多個物件，但是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會決定除了在 `Process` 命令中指定的單一物件之外，還必須處理哪些物件。</span><span class="sxs-lookup"><span data-stu-id="927e4-149">In this case, a single `Process` command can process multiple objects on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, but [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] determines which objects besides the single object specified in the `Process` command must also be processed.</span></span>  
  
 <span data-ttu-id="927e4-150">不過，您可以使用 `Process` 命令中的 `Batch` 命令來同時處理多個物件 (例如維度)。</span><span class="sxs-lookup"><span data-stu-id="927e4-150">However, you can process multiple objects, such as dimensions, at the same time by using multiple `Process` commands within a `Batch` command.</span></span> <span data-ttu-id="927e4-151">相較於使用 `ProcessAffectedObjects` 屬性，批次作業在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上依序或平行處理物件時，提供更細的控制層級，而且可讓您為較大的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫調整您的處理方法。</span><span class="sxs-lookup"><span data-stu-id="927e4-151">Batch operations provide a finer level of control for serial or parallel processing of objects on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance than using the `ProcessAffectedObjects` attribute, and let you to tune your processing approach for larger [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] databases.</span></span> <span data-ttu-id="927e4-152">如需執行批次作業的詳細資訊，請參閱[&#40;XMLA&#41;執行批次作業](performing-batch-operations-xmla.md)。</span><span class="sxs-lookup"><span data-stu-id="927e4-152">For more information about performing batch operations, see [Performing Batch Operations &#40;XMLA&#41;](performing-batch-operations-xmla.md).</span></span>  
  
## <a name="specifying-out-of-line-bindings"></a><span data-ttu-id="927e4-153">指定非正規繫結</span><span class="sxs-lookup"><span data-stu-id="927e4-153">Specifying Out-of-Line Bindings</span></span>  
 <span data-ttu-id="927e4-154">如果命令 `Process` 不包含在命令中 `Batch` ，您可以選擇性地在命令的 [系結]、[DataSource [ ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla)] 和[DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)[ [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) ] 屬性中，指定 `Process` 要處理之物件的非行系結。</span><span class="sxs-lookup"><span data-stu-id="927e4-154">If the `Process` command is not contained by a `Batch` command, you can optionally specify out-of-line bindings in the [Bindings](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla), [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla), and [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla) properties of the `Process` command for the objects to be processed.</span></span> <span data-ttu-id="927e4-155">非正規 (out-of-line) 繫結是資料來源、資料來源檢視以及其他物件的參考，其中繫結只會在 `Process` 命令執行期間存在，而且會覆寫任何與要處理的物件關聯的現有繫結。</span><span class="sxs-lookup"><span data-stu-id="927e4-155">Out-of-line bindings are references to data sources, data source views, and other objects in which the binding exists only during the execution of the `Process` command, and which override any existing bindings associated with the objects being processed.</span></span> <span data-ttu-id="927e4-156">如果未指定非正規 (out-of-line) 繫結，會使用與要處理的物件目前關聯的繫結。</span><span class="sxs-lookup"><span data-stu-id="927e4-156">If out-of-line bindings are not specified, the bindings currently associated with the objects to be processed are used.</span></span>  
  
 <span data-ttu-id="927e4-157">非正規 (out-of-line) 繫結用於在下列情況：</span><span class="sxs-lookup"><span data-stu-id="927e4-157">Out-of-line bindings are used in the following circumstances:</span></span>  
  
-   <span data-ttu-id="927e4-158">以累加方式處理資料分割，其中必須指定替代的事實資料表或是在現有事實資料表上的篩選，以確定不會計數資料列兩次。</span><span class="sxs-lookup"><span data-stu-id="927e4-158">Incrementally processing a partition, in which an alternative fact table or a filter on the existing fact table must be specified to make sure that rows are not counted twice.</span></span>  
  
-   <span data-ttu-id="927e4-159">使用中的資料流程工作，在 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 處理維度、採礦模型或分割區時提供資料。</span><span class="sxs-lookup"><span data-stu-id="927e4-159">Using a data flow task in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] to provide data while processing a dimension, mining model, or partition.</span></span>  
  
 <span data-ttu-id="927e4-160">非正規繫結 (out-of-line) 是以 Analysis Services 指令碼語言 (ASSL) 的一部分來描述。</span><span class="sxs-lookup"><span data-stu-id="927e4-160">Out-of-line bindings are described as part of the Analysis Services Scripting Language (ASSL).</span></span> <span data-ttu-id="927e4-161">如需 ASSL 中之非正規系結的詳細資訊，請參閱[&#40;SSAS 多維度&#41;的資料來源和](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md)系結。</span><span class="sxs-lookup"><span data-stu-id="927e4-161">For more information about out-of-line bindings in ASSL, see [Data Sources and Bindings &#40;SSAS Multidimensional&#41;](../multidimensional-models/data-sources-and-bindings-ssas-multidimensional.md).</span></span>  
  
### <a name="incrementally-updating-partitions"></a><span data-ttu-id="927e4-162">以累加方式更新資料分割</span><span class="sxs-lookup"><span data-stu-id="927e4-162">Incrementally Updating Partitions</span></span>  
 <span data-ttu-id="927e4-163">以累加方式更新已經處理的資料分割通常需要非正規繫結 (out-of-line)，因為針對資料分割所指定的繫結，會參考已經在資料分割中彙總的事實資料表資料。</span><span class="sxs-lookup"><span data-stu-id="927e4-163">Incrementally updating an already processed partition typically requires an out-of-line binding because the binding specified for the partition references fact table data already aggregated within the partition.</span></span> <span data-ttu-id="927e4-164">當使用 `Process` 命令時，以累加方式更新已經處理的資料分割時，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="927e4-164">When incrementally updating an already processed partition by using the `Process` command, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] performs the following actions:</span></span>  
  
-   <span data-ttu-id="927e4-165">建立一個與要以累加方式更新的資料分割有相同結構的暫存資料分割。</span><span class="sxs-lookup"><span data-stu-id="927e4-165">Creates a temporary partition with a structure identical to that of the partition to be incrementally updated.</span></span>  
  
-   <span data-ttu-id="927e4-166">使用在 `Process` 命令中指定的非正規繫結 (out-of-line) 來處理暫存資料分割。</span><span class="sxs-lookup"><span data-stu-id="927e4-166">Processes the temporary partition, using the out-of-line binding specified in the `Process` command.</span></span>  
  
-   <span data-ttu-id="927e4-167">以現有選取的資料分割，合併暫存資料分割。</span><span class="sxs-lookup"><span data-stu-id="927e4-167">Merges the temporary partition with the existing selected partition.</span></span>  
  
 <span data-ttu-id="927e4-168">如需有關使用 XML for Analysis (XMLA) 合併資料分割的詳細資訊，請參閱[合併 xmla &#40;](merging-partitions-xmla.md)的資料分割&#41;。</span><span class="sxs-lookup"><span data-stu-id="927e4-168">For more information about merging partitions using XML for Analysis (XMLA), see [Merging Partitions &#40;XMLA&#41;](merging-partitions-xmla.md).</span></span>  
  
## <a name="handling-processing-errors"></a><span data-ttu-id="927e4-169">處理在處理時發生的錯誤</span><span class="sxs-lookup"><span data-stu-id="927e4-169">Handling Processing Errors</span></span>  
 <span data-ttu-id="927e4-170">命令的[ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla)屬性 `Process` 可讓您指定在處理物件時，如何處理遇到的錯誤。</span><span class="sxs-lookup"><span data-stu-id="927e4-170">The [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla) property of the `Process` command lets you specify how to handle errors encountered while processing an object.</span></span> <span data-ttu-id="927e4-171">例如，處理維度時，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在索引鍵屬性的索引鍵資料行中遇到重複的值。</span><span class="sxs-lookup"><span data-stu-id="927e4-171">For example, while processing a dimension, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encounters a duplicate value in the key column of the key attribute.</span></span> <span data-ttu-id="927e4-172">由於屬性索引鍵必須是唯一的，所以 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會捨棄重複的記錄。</span><span class="sxs-lookup"><span data-stu-id="927e4-172">Because attribute keys must be unique, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] discards the duplicate records.</span></span> <span data-ttu-id="927e4-173">根據的[KeyDuplicate](https://docs.microsoft.com/bi-reference/assl/properties/keyduplicate-element-assl)屬性 `ErrorConfiguration` ， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 可以：</span><span class="sxs-lookup"><span data-stu-id="927e4-173">Based on the [KeyDuplicate](https://docs.microsoft.com/bi-reference/assl/properties/keyduplicate-element-assl) property of `ErrorConfiguration`, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] could:</span></span>  
  
-   <span data-ttu-id="927e4-174">忽略錯誤並繼續處理維度。</span><span class="sxs-lookup"><span data-stu-id="927e4-174">Ignore the error and continue processing the dimension.</span></span>  
  
-   <span data-ttu-id="927e4-175">傳回訊息以說明 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 遇到重複的索引鍵並繼續處理。</span><span class="sxs-lookup"><span data-stu-id="927e4-175">Return a message that states [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encountered a duplicate key and continue processing.</span></span>  
  
 <span data-ttu-id="927e4-176">當 `ErrorConfiguration` 在 `Process` 命令期間提供選項時，有許多類似的狀況。</span><span class="sxs-lookup"><span data-stu-id="927e4-176">There are many similar conditions for which `ErrorConfiguration` provides options during a `Process` command.</span></span>  
  
## <a name="managing-writeback-tables"></a><span data-ttu-id="927e4-177">管理回寫資料表</span><span class="sxs-lookup"><span data-stu-id="927e4-177">Managing Writeback Tables</span></span>  
 <span data-ttu-id="927e4-178">如果 `Process` 命令遇到可寫入的資料分割，或是這類資料分割尚未完全處理的 Cube 或是量值群組，該資料分割可能不會有已經存在的回寫資料表。</span><span class="sxs-lookup"><span data-stu-id="927e4-178">If the `Process` command encounters a write-enabled partition, or a cube or measure group for such a partition, that is not already fully processed, a writeback table may not already exist for that partition.</span></span> <span data-ttu-id="927e4-179">命令的[WritebackTableCreation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/writebacktablecreation-element-xmla)屬性 `Process` 會決定是否 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 應該建立回寫資料表。</span><span class="sxs-lookup"><span data-stu-id="927e4-179">The [WritebackTableCreation](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/writebacktablecreation-element-xmla) property of the `Process` command determines whether [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] should create a writeback table.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="927e4-180">範例</span><span class="sxs-lookup"><span data-stu-id="927e4-180">Examples</span></span>  
  
### <a name="description"></a><span data-ttu-id="927e4-181">描述</span><span class="sxs-lookup"><span data-stu-id="927e4-181">Description</span></span>  
 <span data-ttu-id="927e4-182">下列範例會完整處理 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] 範例 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="927e4-182">The following example fully processes the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span>  
  
### <a name="code"></a><span data-ttu-id="927e4-183">程式碼</span><span class="sxs-lookup"><span data-stu-id="927e4-183">Code</span></span>  
  
```  
<Process xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
  </Object>  
  <Type>ProcessFull</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
### <a name="description"></a><span data-ttu-id="927e4-184">描述</span><span class="sxs-lookup"><span data-stu-id="927e4-184">Description</span></span>  
 <span data-ttu-id="927e4-185">下列範例會以累加方式處理範例資料庫中「**艾德作用的 DW** 」 cube 之「**網際網路銷售**」量值群組中的**Internet_Sales_2004**資料分割 [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="927e4-185">The following example incrementally processes the **Internet_Sales_2004** partition in the **Internet Sales** measure group of the **Adventure Works DW** cube in the [!INCLUDE[ssAWDWsp](../../includes/ssawdwsp-md.md)] sample [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="927e4-186">此 `Process` 命令會在命令的屬性中使用非正規查詢系結，將訂單日期的匯總加入至資料分割2006，以 `Bindings` `Process` 取得要在其中產生匯總以加入至資料分割的事實資料表資料列。</span><span class="sxs-lookup"><span data-stu-id="927e4-186">The `Process` command is adding aggregations for order dates later than December 31, 2006 to the partition by using an out-of-line query binding in the `Bindings` property of the `Process` command to retrieve the fact table rows from which to generate aggregations to add to the partition.</span></span>  
  
### <a name="code"></a><span data-ttu-id="927e4-187">程式碼</span><span class="sxs-lookup"><span data-stu-id="927e4-187">Code</span></span>  
  
```  
<Process ProcessAffectedObjects="true" xmlns="https://schemas.microsoft.com/analysisservices/2003/engine">  
  <Object>  
    <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
    <CubeID>Adventure Works DW</CubeID>  
    <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
    <PartitionID>Internet_Sales_2006</PartitionID>  
  </Object>  
  <Bindings>  
    <Binding>  
      <DatabaseID>Adventure Works DW Multidimensional 2012</DatabaseID>  
      <CubeID>Adventure Works DW</CubeID>  
      <MeasureGroupID>Fact Internet Sales 1</MeasureGroupID>  
      <PartitionID>Internet_Sales_2006</PartitionID>  
      <Source xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:type="QueryBinding">  
        <DataSourceID>Adventure Works DW</DataSourceID>  
        <QueryDefinition>  
          SELECT  
            [dbo].[FactInternetSales].[ProductKey],  
            [dbo].[FactInternetSales].[OrderDateKey],  
            [dbo].[FactInternetSales].[DueDateKey],  
            [dbo].[FactInternetSales].[ShipDateKey],   
            [dbo].[FactInternetSales].[CustomerKey],   
            [dbo].[FactInternetSales].[PromotionKey],  
            [dbo].[FactInternetSales].[CurrencyKey],  
            [dbo].[FactInternetSales].[SalesTerritoryKey],  
            [dbo].[FactInternetSales].[SalesOrderNumber],  
            [dbo].[FactInternetSales].[SalesOrderLineNumber],  
            [dbo].[FactInternetSales].[RevisionNumber],  
            [dbo].[FactInternetSales].[OrderQuantity],  
            [dbo].[FactInternetSales].[UnitPrice],  
            [dbo].[FactInternetSales].[ExtendedAmount],  
            [dbo].[FactInternetSales].[UnitPriceDiscountPct],  
            [dbo].[FactInternetSales].[DiscountAmount],  
            [dbo].[FactInternetSales].[ProductStandardCost],  
            [dbo].[FactInternetSales].[TotalProductCost],  
            [dbo].[FactInternetSales].[SalesAmount],  
            [dbo].[FactInternetSales].[TaxAmt],  
            [dbo].[FactInternetSales].[Freight],  
            [dbo].[FactInternetSales].[CarrierTrackingNumber],  
            [dbo].[FactInternetSales].[CustomerPONumber]  
          FROM [dbo].[FactInternetSales]  
          WHERE OrderDateKey > '1280'  
        </QueryDefinition>  
      </Source>  
    </Binding>  
  </Bindings>  
  <Type>ProcessAdd</Type>  
  <WriteBackTableCreation>UseExisting</WriteBackTableCreation>  
</Process>  
```  
  
  
