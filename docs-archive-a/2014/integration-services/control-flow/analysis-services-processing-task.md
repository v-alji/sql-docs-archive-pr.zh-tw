---
title: Analysis Services 處理工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asprocessingtask.f1
helpviewer_keywords:
- Analysis Services Processing task
- processing objects [Integration Services]
ms.assetid: e5748836-b4ce-4e17-ab6b-617a336f02f4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 19ef8046c06c9131b3ea2eb8ffe267c026808dfd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688118"
---
# <a name="analysis-services-processing-task"></a><span data-ttu-id="b8722-102">Analysis Services 處理工作</span><span class="sxs-lookup"><span data-stu-id="b8722-102">Analysis Services Processing Task</span></span>
  <span data-ttu-id="b8722-103">「 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 處理」工作會處理 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 物件，例如表格式模型、Cube、維度及採礦模型。</span><span class="sxs-lookup"><span data-stu-id="b8722-103">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task processes [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] objects such as tabular models, cubes, dimensions, and mining models.</span></span>  
  
 <span data-ttu-id="b8722-104">處理表格式模型時，請牢記以下事項：</span><span class="sxs-lookup"><span data-stu-id="b8722-104">When processing tabular models, keep the following in mind:</span></span>  
  
-   <span data-ttu-id="b8722-105">您無法在表格式模型上執行影響分析。</span><span class="sxs-lookup"><span data-stu-id="b8722-105">You cannot perform impact analysis on tabular models.</span></span>  
  
-   <span data-ttu-id="b8722-106">系統不會公開表格式模型的部分處理選項，例如 [處理重組] 和 [處理重新計算]。</span><span class="sxs-lookup"><span data-stu-id="b8722-106">Some processing options for tabular mode are not exposed, such as Process Defrag and Process Recalc.</span></span> <span data-ttu-id="b8722-107">您可以使用「執行 DLL」工作，執行這些功能。</span><span class="sxs-lookup"><span data-stu-id="b8722-107">You can perform these functions by using the Execute DDL task.</span></span>  
  
-   <span data-ttu-id="b8722-108">[處理索引] 和 [處理更新] 選項不適合表格式模型，因此應該不會使用。</span><span class="sxs-lookup"><span data-stu-id="b8722-108">The options Process Index and Process Update are not appropriate for tabular models and should not be used.</span></span>  
  
-   <span data-ttu-id="b8722-109">表格式模型會忽略批次處理設定。</span><span class="sxs-lookup"><span data-stu-id="b8722-109">Batch settings are ignored for tabular models.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="b8722-110">包括多項執行商業智慧作業的工作，例如執行「資料定義語言」(Data Definition Language，DDL) 和執行資料採礦預測查詢。</span><span class="sxs-lookup"><span data-stu-id="b8722-110">includes a number of tasks that perform business intelligence operations, such as running Data Definition Language (DDL) statements and data mining prediction queries.</span></span> <span data-ttu-id="b8722-111">如需有關相關之商業智慧工作的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="b8722-111">For more information about related business intelligence tasks, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="b8722-112">Analysis Services 執行 DDL 工作</span><span class="sxs-lookup"><span data-stu-id="b8722-112">Analysis Services Execute DDL Task</span></span>](analysis-services-execute-ddl-task.md)  
  
-   [<span data-ttu-id="b8722-113">資料採礦查詢工作</span><span class="sxs-lookup"><span data-stu-id="b8722-113">Data Mining Query Task</span></span>](data-mining-query-task.md)  
  
## <a name="object-processing"></a><span data-ttu-id="b8722-114">物件處理</span><span class="sxs-lookup"><span data-stu-id="b8722-114">Object Processing</span></span>  
 <span data-ttu-id="b8722-115">可以同時處理多個物件。</span><span class="sxs-lookup"><span data-stu-id="b8722-115">Multiple objects can be processed at the same time.</span></span> <span data-ttu-id="b8722-116">處理多個物件時，您會定義套用至處理該批次中所有物件的設定。</span><span class="sxs-lookup"><span data-stu-id="b8722-116">When processing multiple objects, you define settings that apply to the processing of all the objects in the batch.</span></span>  
  
 <span data-ttu-id="b8722-117">批次中的物件可循序或平行處理。</span><span class="sxs-lookup"><span data-stu-id="b8722-117">Objects in a batch can be processed in sequence or in parallel.</span></span> <span data-ttu-id="b8722-118">如果批次未包含重視處理順序的物件，使用平行處理可加快處理速度。</span><span class="sxs-lookup"><span data-stu-id="b8722-118">If the batch does not contain objects for which processing sequence is important, parallel processing can speed up processing.</span></span> <span data-ttu-id="b8722-119">如果平行處理批次中的物件，可設定讓工作判斷平行處理的物件數目，或者手動指定同時處理的物件數目。</span><span class="sxs-lookup"><span data-stu-id="b8722-119">If objects in the batch are processed in parallel, you can configure the task to let it determine how many objects to process in parallel, or you can manually specify the number of objects to process at the same time.</span></span> <span data-ttu-id="b8722-120">如果循序處理物件，可將所有物件列入一項交易中，或針對批次中各物件使用不同的交易，藉此在批次上設定交易屬性。</span><span class="sxs-lookup"><span data-stu-id="b8722-120">If objects are processed sequentially, you can set a transaction attribute on the batch either by enlisting all objects in one transaction or by using a separate transaction for each object in the batch.</span></span>  
  
 <span data-ttu-id="b8722-121">當您處理分析物件時，可能也會想處理倚賴該些物件的物件。</span><span class="sxs-lookup"><span data-stu-id="b8722-121">When you process analytic objects, you might also want to process the objects that depend on them.</span></span> <span data-ttu-id="b8722-122">「 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 處理」工作包含的選項除了可以處理選取的物件以外，也可以處理任何相依物件。</span><span class="sxs-lookup"><span data-stu-id="b8722-122">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task includes an option to process any dependent objects in addition to the selected objects.</span></span>  
  
 <span data-ttu-id="b8722-123">您通常會在處理事實資料表之前處理維度資料表。</span><span class="sxs-lookup"><span data-stu-id="b8722-123">Typically, you process dimension tables before processing fact tables.</span></span> <span data-ttu-id="b8722-124">如果嘗試在處理維度資料表之前處理事實資料表，則可能會出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="b8722-124">You may encounter errors if you try to process fact tables before processing the dimension tables.</span></span>  
  
 <span data-ttu-id="b8722-125">此工作亦可讓您設定在維度索引鍵中處理錯誤。</span><span class="sxs-lookup"><span data-stu-id="b8722-125">This task also lets you configure the handling of errors in dimension keys.</span></span> <span data-ttu-id="b8722-126">例如，工作可忽略錯誤，或在發生指定的錯誤數目之後停止。</span><span class="sxs-lookup"><span data-stu-id="b8722-126">For example, the task can ignore errors or stop after a specified number of errors occur.</span></span> <span data-ttu-id="b8722-127">工作可使用預設錯誤組態，或者您可以建構自訂錯誤組態。</span><span class="sxs-lookup"><span data-stu-id="b8722-127">The task can use the default error configuration, or you can construct a custom error configuration.</span></span> <span data-ttu-id="b8722-128">在自訂錯誤組態中，請指定工作處理錯誤的方式和錯誤的條件。</span><span class="sxs-lookup"><span data-stu-id="b8722-128">In the custom error configuration, you specify how the task handles errors and the error conditions.</span></span> <span data-ttu-id="b8722-129">例如，您可以指定在發生四項錯誤時停止執行工作，或指定工作處理 **Null** 索引鍵值的方式。</span><span class="sxs-lookup"><span data-stu-id="b8722-129">For example, you can specify that the task should stop running when the fourth error occurs, or specify how the task should handle **Null** key values.</span></span> <span data-ttu-id="b8722-130">自訂錯誤組態亦可包含錯誤記錄的路徑。</span><span class="sxs-lookup"><span data-stu-id="b8722-130">The custom error configuration can also include the path of an error log.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8722-131">「 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 處理」工作只能處理使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 工具建立的分析物件。</span><span class="sxs-lookup"><span data-stu-id="b8722-131">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task can process only analytic objects created by using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] tools.</span></span>  
  
 <span data-ttu-id="b8722-132">此工作經常用來搭配將資料載入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料表的「大量插入」工作使用，或搭配實作將資料載入資料表之資料流程的資料流程工作使用。</span><span class="sxs-lookup"><span data-stu-id="b8722-132">This task is frequently used in combination with a Bulk Insert task that loads data into a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] table, or a Data Flow task that implements a data flow that loads data into a table.</span></span> <span data-ttu-id="b8722-133">例如，資料流程工作可能包含從線上交易處理 (OLTP) 資料庫擷取資料，並將資料載入資料倉儲中事實資料表的資料流程，而在此之後，會呼叫「 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 處理」工作處理於資料倉儲上建立的 Cube。</span><span class="sxs-lookup"><span data-stu-id="b8722-133">For example, the Data Flow task might have a data flow that extracts data from an online transactional database (OLTP) database and loads it into a fact table in a data warehouse, after which the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task is called to process the cube built on the data warehouse.</span></span>  
  
 <span data-ttu-id="b8722-134">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 處理工作會使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 連線管理員來連線到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="b8722-134">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] Processing task uses an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager to connect to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="b8722-135">如需相關資訊，請參閱 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="b8722-135">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md).</span></span>  
  
## <a name="error-handling"></a><span data-ttu-id="b8722-136">錯誤處理</span><span class="sxs-lookup"><span data-stu-id="b8722-136">Error Handling</span></span>  
  
## <a name="configuration-of-the-analysis-services-processing-task"></a><span data-ttu-id="b8722-137">Analysis Services 處理工作的組態</span><span class="sxs-lookup"><span data-stu-id="b8722-137">Configuration of the Analysis Services Processing Task</span></span>  
 <span data-ttu-id="b8722-138">您可以透過 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="b8722-138">You can set properties through [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="b8722-139">如需有關可以在「 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="b8722-139">For more information about the properties that you can set in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="b8722-140">Analysis Services 處理工作編輯器 &#40;一般頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="b8722-140">Analysis Services Processing Task Editor &#40;General Page&#41;</span></span>](../general-page-of-integration-services-designers-options.md)  
  
-   [<span data-ttu-id="b8722-141">Analysis Services 處理工作編輯器 &#40;Analysis Services 頁面&#41;</span><span class="sxs-lookup"><span data-stu-id="b8722-141">Analysis Services Processing Task Editor &#40;Analysis Services Page&#41;</span></span>](../analysis-services-processing-task-editor-analysis-services-page.md)  
  
-   [<span data-ttu-id="b8722-142">運算式頁面</span><span class="sxs-lookup"><span data-stu-id="b8722-142">Expressions Page</span></span>](../expressions/expressions-page.md)  
  
 <span data-ttu-id="b8722-143">如需在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="b8722-143">For more information about setting these properties in [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="b8722-144">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="b8722-144">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-the-analysis-services-processing-task"></a><span data-ttu-id="b8722-145">以程式設計方式設定 Analysis Services 處理工作</span><span class="sxs-lookup"><span data-stu-id="b8722-145">Programmatic Configuration of the Analysis Services Processing Task</span></span>  
 <span data-ttu-id="b8722-146">如需有關以程式設計方式設定這些屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="b8722-146">For more information about programmatically setting these properties, click one of the following topics:</span></span>  
  
-   <xref:Microsoft.DataTransformationServices.Tasks.DTSProcessingTask.DTSProcessingTask>  
  
  
