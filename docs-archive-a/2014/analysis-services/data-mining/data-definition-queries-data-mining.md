---
title: 資料定義查詢 (資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 49e02de1-4ffa-401c-8eee-471a9c25b86a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 153369979737dded52609843cd30cf914315e9cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594276"
---
# <a name="data-definition-queries-data-mining"></a><span data-ttu-id="7ab6c-102">資料定義查詢 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="7ab6c-102">Data Definition Queries (Data Mining)</span></span>
  <span data-ttu-id="7ab6c-103">如果是資料採礦， *「資料定義查詢」* (Data Definition Query) 類別目錄表示執行以下作業的 DMX 陳述式或 XMLA 命令：</span><span class="sxs-lookup"><span data-stu-id="7ab6c-103">For data mining, the category *data definition query* means DMX statements or XMLA commands that do the following:</span></span>  
  
-   <span data-ttu-id="7ab6c-104">建立、更改或操作資料採礦物件，例如模型。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-104">Create, alter, or manipulate data mining objects, such as a model.</span></span>  
  
-   <span data-ttu-id="7ab6c-105">定義要用於定型或預測的資料來源。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-105">Define the source of data to be used in training or for prediction.</span></span>  
  
-   <span data-ttu-id="7ab6c-106">匯出或匯入採礦模型和採礦結構。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-106">Export or import mining models and mining structures.</span></span>  
  
 [<span data-ttu-id="7ab6c-107">建立資料定義查詢</span><span class="sxs-lookup"><span data-stu-id="7ab6c-107">Creating Data Definition Queries</span></span>](#bkmk_Create)  
  
-   [<span data-ttu-id="7ab6c-108">SQL Server 資料工具中的資料定義查詢</span><span class="sxs-lookup"><span data-stu-id="7ab6c-108">Data Definition Queries in SQL Server Data Tools</span></span>](#bkmk_ssdt)  
  
-   [<span data-ttu-id="7ab6c-109">SQL Server Management Studio 中的資料定義查詢</span><span class="sxs-lookup"><span data-stu-id="7ab6c-109">Data Definition Queries in SQL Server Management Studio</span></span>](#bkmk_SSMS)  
  
 [<span data-ttu-id="7ab6c-110">編寫資料定義陳述式的指令碼</span><span class="sxs-lookup"><span data-stu-id="7ab6c-110">Scripting Data Definition Statements</span></span>](#bkmk_Scripts)  
  
 [<span data-ttu-id="7ab6c-111">編寫資料定義陳述式的指令碼</span><span class="sxs-lookup"><span data-stu-id="7ab6c-111">Scripting Data Definition Statements</span></span>](#bkmk_Export)  
  
##  <a name="creating-data-definition-queries"></a><a name="bkmk_Create"></a><span data-ttu-id="7ab6c-112">建立資料定義查詢</span><span class="sxs-lookup"><span data-stu-id="7ab6c-112">Creating Data Definition Queries</span></span>  
 <span data-ttu-id="7ab6c-113">您可以在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 和 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中使用預測查詢產生器或是在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中使用 DMX 查詢視窗來建立資料定義查詢 (陳述式)。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-113">You can create data definition queries (statements) by using the Prediction Query Builder in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] and [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], or by using the DMX Query window in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="7ab6c-114">DMX 中的資料定義陳述式是 Analysis Services 資料定義語言 (DDL) 的一部分。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-114">Data definition statements in DMX are part of the Analysis Services data definition language (DDL).</span></span>  
  
 <span data-ttu-id="7ab6c-115">如需特定資料定義陳述式之語法的詳細資訊，請參閱[資料採礦延伸模組 &#40;DMX&#41; 參考](/sql/dmx/data-mining-extensions-dmx-reference)。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-115">For information about the syntax of specific data definition statements, see [Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference).</span></span>  
  
###  <a name="data-definition-queries-in-sql-server-data-tools"></a><a name="bkmk_ssdt"></a><span data-ttu-id="7ab6c-116">SQL Server Data Tools 中的資料定義查詢</span><span class="sxs-lookup"><span data-stu-id="7ab6c-116">Data Definition Queries in SQL Server Data Tools</span></span>  
 <span data-ttu-id="7ab6c-117">資料採礦精靈是 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中用來執行以下操作的慣用工具：建立及修改採礦模型和採礦結構，以及定義用於預測查詢和定型的資料來源。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-117">The Data Mining Wizard is the preferred tool in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] for creating and modifying mining models and mining structures, and for defining the data sources that are used in prediction queries and for training.</span></span>  
  
 <span data-ttu-id="7ab6c-118">但是，如果您想要知道精靈傳送哪些陳述式到伺服器來建立資料結構或採礦模型，您可以使用 SQL Server Profiler 擷取資料定義陳述式。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-118">However, if you want to know what statements are being sent to the server by the wizard to create data structures or mining models, you can use SQL Server Profiler to capture the data definition statements.</span></span> <span data-ttu-id="7ab6c-119">如需詳細資訊，請參閱 [Use SQL Server Profiler to Monitor Analysis Services](../instances/use-sql-server-profiler-to-monitor-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-119">For more information, see [Use SQL Server Profiler to Monitor Analysis Services](../instances/use-sql-server-profiler-to-monitor-analysis-services.md).</span></span>  
  
 <span data-ttu-id="7ab6c-120">若要檢視用來定義定型或預測中所使用之資料來源的陳述式，您可以使用預測查詢產生器中的 **[SQL 檢視]** 。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-120">To view the statements used for defining data sources used for training or prediction, you can use the **SQL View** in the Prediction Query Builder.</span></span> <span data-ttu-id="7ab6c-121">有時候使用預測查詢產生器來建立用於定型和測試模型的基本查詢會很有用處，這樣可建立正確的語法。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-121">Sometimes it can be helpful to build basic queries for training and testing models by using Prediction Query Builder, to establish the correct syntax.</span></span> <span data-ttu-id="7ab6c-122">然後您可以切換到 **[SQL 檢視]** 並手動編輯查詢。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-122">You can then switch to **SQL View** and manually edit the query.</span></span> <span data-ttu-id="7ab6c-123">如需詳細資訊，請參閱 [Manually Edit a Prediction Query](manually-edit-a-prediction-query.md)。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-123">For more information, see [Manually Edit a Prediction Query](manually-edit-a-prediction-query.md).</span></span>  
  
###  <a name="data-definition-queries-in-sql-server-management-studio"></a><a name="bkmk_SSMS"></a><span data-ttu-id="7ab6c-124">SQL Server Management Studio 中的資料定義查詢</span><span class="sxs-lookup"><span data-stu-id="7ab6c-124">Data Definition Queries in SQL Server Management Studio</span></span>  
 <span data-ttu-id="7ab6c-125">如果是資料採礦物件，您可以使用資料定義查詢來執行以下動作：</span><span class="sxs-lookup"><span data-stu-id="7ab6c-125">For data mining objects, you can use data definition queries to perform the following actions:</span></span>  
  
-   <span data-ttu-id="7ab6c-126">使用 [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx) 來建立特定類型的模型，例如叢集模型或決策樹模型。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-126">Create specific types of models, such as a clustering model or decision tree model, by using [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).</span></span>  
  
-   <span data-ttu-id="7ab6c-127">使用 [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx)，藉由加入模型或變更資料行來更改現有的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-127">Alter an existing mining structure by adding a model or by changing the columns, by using [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx).</span></span> <span data-ttu-id="7ab6c-128">請注意，您不能使用 DMX 更改採礦模型，您只能在現有的結構中加入新的模型。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-128">Note that you cannot alter a mining model by using DMX; you only add new models to an existing structure.</span></span>  
  
-   <span data-ttu-id="7ab6c-129">建立採礦模型的複本，然後使用 [SELECT INTO &#40;DMX&#41;](/sql/dmx/select-into-dmx) 加以更改。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-129">Make a copy of a mining model and then alter it, by using [SELECT INTO &#40;DMX&#41;](/sql/dmx/select-into-dmx).</span></span>  
  
-   <span data-ttu-id="7ab6c-130">搭配資料來源查詢 (例如 OPENROWSET) 一起使用 [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)，以定義用於定型模型的資料集。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-130">Define the data set used for training a model, by using [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) together with a data source query such as OPENROWSET.</span></span>  
  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="7ab6c-131">提供可幫助您建立資料定義查詢的查詢範本。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-131">provides query templates that can help you create data definition queries.</span></span> <span data-ttu-id="7ab6c-132">如需詳細資訊，請參閱 [在 SQL Server Management Studio 中使用 Analysis Services 範本](../instances/use-analysis-services-templates-in-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-132">For more information, see [Use Analysis Services Templates in SQL Server Management Studio](../instances/use-analysis-services-templates-in-sql-server-management-studio.md).</span></span>  
  
 <span data-ttu-id="7ab6c-133">一般來說， [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中針對 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 所提供的範本只包含一般語法定義，您必須在 **[查詢]** 視窗中輸入或是使用為了輸入參數所提供的對話方塊來自訂這些語法定義。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-133">In general, the templates that are provided for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] contain only the general syntax definition, which you must customize, either by typing in the **Query** window, or by using the dialog box provided for entering parameters.</span></span>  
  
 <span data-ttu-id="7ab6c-134">如需如何使用此介面輸入參數的範例，請參閱 [根據範本建立單一預測查詢](create-a-singleton-prediction-query-from-a-template.md)。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-134">For an example of how to enter parameters using the interface, see [Create a Singleton Prediction Query from a Template](create-a-singleton-prediction-query-from-a-template.md).</span></span>  
  
###  <a name="scripting-data-definition-statements"></a><a name="bkmk_Scripts"></a><span data-ttu-id="7ab6c-135">編寫資料定義語句的腳本</span><span class="sxs-lookup"><span data-stu-id="7ab6c-135">Scripting Data Definition Statements</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="7ab6c-136">提供多種指令碼和程式語言，您可以使用這些語言來建立或更改資料採礦物件或是定義資料來源。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-136">provides multiple scripting and programming languages that you can use to create or alter data mining objects, or to define data sources.</span></span>  <span data-ttu-id="7ab6c-137">雖然 DMX 是為了加速資料採礦工作所設計，您也可以在指令碼或自訂程式碼中同時使用 XMLA 和 AMO 來操作物件。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-137">Although DMX is designed for expediting data mining tasks, you can also use both XMLA and AMO to manipulate objects in scripts or in custom code.</span></span>  
  
 <span data-ttu-id="7ab6c-138">適用於 Excel 的資料採礦增益集也包含許多查詢範本，並提供 [進階查詢編輯器]\*\*\*\*，此編輯器可幫助您撰寫複雜的 DMX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-138">The Data Mining Add-in for Excel also includes many query templates, and provides the **Advanced Query Editor**, which helps you compose complex DMX statements.</span></span> <span data-ttu-id="7ab6c-139">您可以互動方式建立查詢，然後切換到 [SQL 檢視] 來擷取 DMX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-139">You can build a query interactively and then switch to SQL View to capture the DMX statement.</span></span>  
  
##  <a name="exporting-and-importing-models"></a><a name="bkmk_Export"></a><span data-ttu-id="7ab6c-140">匯出和匯入模型</span><span class="sxs-lookup"><span data-stu-id="7ab6c-140">Exporting and Importing Models</span></span>  
 <span data-ttu-id="7ab6c-141">您可以在 DMX 中使用資料定義陳述式來匯出模型的定義以及其必要結構和資料來源，然後將該定義匯入至不同的伺服器。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-141">You can use data definition statements in DMX to export the definition of a model and its required structure and data sources, and then import that definition into a different server.</span></span> <span data-ttu-id="7ab6c-142">使用匯出和匯入是在不同的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]執行個體之間移動資料採礦模型和採礦結構的最快速且最簡單的方法。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-142">Using export and import is the fastest and easiest way to move data mining models and mining structures between instances of [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="7ab6c-143">如需詳細資訊，請參閱[資料採礦解決方案和物件的管理](management-of-data-mining-solutions-and-objects.md)。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-143">For more information, see [Management of Data Mining Solutions and Objects](management-of-data-mining-solutions-and-objects.md).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="7ab6c-144">如果您的模型是根據 Cube 資料來源中的資料，您不能使用 DMX 來匯出模型，而且應該改用備份和還原。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-144">If your model is based on data from a cube data srouce, you cannot use DMX to export the model, and should use backup and restore instead.</span></span>  
  
##  <a name="related-tasks"></a><a name="bkmk_Tasks"></a> <span data-ttu-id="7ab6c-145">相關工作</span><span class="sxs-lookup"><span data-stu-id="7ab6c-145">Related Tasks</span></span>  
 <span data-ttu-id="7ab6c-146">下表提供與資料定義查詢有關之工作的連結。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-146">The following table provides links to tasks that are related to data definition queries.</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="7ab6c-147">處理 DMX 查詢的範本。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-147">Work with templates for DMX queries.</span></span>|[<span data-ttu-id="7ab6c-148">在 SQL Server Management Studio 中使用 Analysis Services 範本</span><span class="sxs-lookup"><span data-stu-id="7ab6c-148">Use Analysis Services Templates in SQL Server Management Studio</span></span>](../instances/use-analysis-services-templates-in-sql-server-management-studio.md)|  
|<span data-ttu-id="7ab6c-149">使用預測查詢產生器來設計所有種類的查詢。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-149">Design queries of all kinds, using Prediction Query Builder.</span></span>|[<span data-ttu-id="7ab6c-150">使用預測查詢產生器來建立預測查詢</span><span class="sxs-lookup"><span data-stu-id="7ab6c-150">Create a Prediction Query Using the Prediction Query Builder</span></span>](create-a-prediction-query-using-the-prediction-query-builder.md)|  
|<span data-ttu-id="7ab6c-151">使用 SQL Server Profiler 來擷取查詢定義，並使用追蹤來監視 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-151">Capture query definitions by using SQL Server Profiler, and use traces to monitor [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|[<span data-ttu-id="7ab6c-152">使用 SQL Server Profiler 監視 Analysis Services</span><span class="sxs-lookup"><span data-stu-id="7ab6c-152">Use SQL Server Profiler to Monitor Analysis Services</span></span>](../instances/use-sql-server-profiler-to-monitor-analysis-services.md)|  
|<span data-ttu-id="7ab6c-153">深入了解針對 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]所提供的指令碼語言和程式語言。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-153">Learn more about the scripting languages and programming languages provided for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>|[<span data-ttu-id="7ab6c-154">XML for Analysis &#40;XMLA&#41; 參考</span><span class="sxs-lookup"><span data-stu-id="7ab6c-154">XML for Analysis  &#40;XMLA&#41; Reference</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)<br /><br /> [<span data-ttu-id="7ab6c-155">使用分析管理物件 &#40;AMO&#41; 來開發</span><span class="sxs-lookup"><span data-stu-id="7ab6c-155">Developing with Analysis Management Objects &#40;AMO&#41;</span></span>](https://docs.microsoft.com/bi-reference/amo/developing-with-analysis-management-objects-amo)|  
|<span data-ttu-id="7ab6c-156">了解如何在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中管理模型。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-156">Learn how to manage models in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>|[<span data-ttu-id="7ab6c-157">匯出及匯入資料採礦物件</span><span class="sxs-lookup"><span data-stu-id="7ab6c-157">Export and Import Data Mining Objects</span></span>](export-and-import-data-mining-objects.md)<br /><br /> [<span data-ttu-id="7ab6c-158">EXPORT &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="7ab6c-158">EXPORT &#40;DMX&#41;</span></span>](/sql/dmx/export-dmx)<br /><br /> [<span data-ttu-id="7ab6c-159">IMPORT &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="7ab6c-159">IMPORT &#40;DMX&#41;</span></span>](/sql/dmx/import-dmx)|  
|<span data-ttu-id="7ab6c-160">深入了解 OPENROWSET 及查詢外部資料的其他方式。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-160">Learn more about OPENROWSET and other ways to query external data.</span></span>|<span data-ttu-id="7ab6c-161">[&#60;來源資料查詢&#62;](/sql/dmx/source-data-query)。</span><span class="sxs-lookup"><span data-stu-id="7ab6c-161">[&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7ab6c-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ab6c-162">See Also</span></span>  
 [<span data-ttu-id="7ab6c-163">資料採礦精靈 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="7ab6c-163">Data Mining Wizard &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-wizard-analysis-services-data-mining.md)  
  
  
