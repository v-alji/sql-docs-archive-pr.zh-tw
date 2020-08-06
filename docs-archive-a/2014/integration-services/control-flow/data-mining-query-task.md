---
title: 資料採礦查詢工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataminingquerytask.f1
helpviewer_keywords:
- prediction queries [Integration Services]
- Data Mining Query task [Integration Services]
ms.assetid: f489348c-2008-4f66-8c2c-c07c3029439a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 6bb3cea630401f92395e2ca4416c03bcd870c881
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596857"
---
# <a name="data-mining-query-task"></a><span data-ttu-id="4b07d-102">資料採礦查詢工作</span><span class="sxs-lookup"><span data-stu-id="4b07d-102">Data Mining Query Task</span></span>
  <span data-ttu-id="4b07d-103">「資料採礦查詢」工作會根據 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]內建的資料採礦模型執行預測查詢。</span><span class="sxs-lookup"><span data-stu-id="4b07d-103">The Data Mining Query task runs prediction queries based on data mining models built in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="4b07d-104">預測查詢會使用採礦模型建立新資料的預測。</span><span class="sxs-lookup"><span data-stu-id="4b07d-104">The prediction query creates a prediction for new data by using mining models.</span></span> <span data-ttu-id="4b07d-105">例如，預測查詢可預測夏季各月間可能出售的帆船數目，或產生可能購買帆船的預期客戶清單。</span><span class="sxs-lookup"><span data-stu-id="4b07d-105">For example, a prediction query can predict how many sailboats are likely to sell during the summer months or generate a list of prospective customers who are likely to buy a sailboat.</span></span>  
  
 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] <span data-ttu-id="4b07d-106">亦提供執行其他商業智慧作業的工作，例如執行「資料定義語言」(DDL) 陳述式和處理分析物件。</span><span class="sxs-lookup"><span data-stu-id="4b07d-106">provides tasks that perform other business intelligence operations, such as running Data Definition Language (DDL) statements and processing analytic objects.</span></span>  
  
 <span data-ttu-id="4b07d-107">如需其他商業智慧工作的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="4b07d-107">For more information about other business intelligence tasks, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="4b07d-108">Analysis Services 執行 DDL 工作</span><span class="sxs-lookup"><span data-stu-id="4b07d-108">Analysis Services Execute DDL Task</span></span>](analysis-services-execute-ddl-task.md)  
  
-   [<span data-ttu-id="4b07d-109">Analysis Services 處理工作</span><span class="sxs-lookup"><span data-stu-id="4b07d-109">Analysis Services Processing Task</span></span>](analysis-services-processing-task.md)  
  
## <a name="prediction-queries"></a><span data-ttu-id="4b07d-110">預測查詢</span><span class="sxs-lookup"><span data-stu-id="4b07d-110">Prediction Queries</span></span>  
 <span data-ttu-id="4b07d-111">查詢為「資料採礦延伸模組」(DMX) 陳述式。</span><span class="sxs-lookup"><span data-stu-id="4b07d-111">The query is a Data Mining Extensions (DMX) statement.</span></span> <span data-ttu-id="4b07d-112">DMX 語言為 SQL 語言的擴充模組，能提供使用採礦模型的支援。</span><span class="sxs-lookup"><span data-stu-id="4b07d-112">The DMX language is an extension of the SQL language that provides support for working with mining models.</span></span> <span data-ttu-id="4b07d-113">如需如何使用 DMX 語言的詳細資訊，請參閱[資料採礦延伸模組 &#40;DMX&#41; 參考](/sql/dmx/data-mining-extensions-dmx-reference)。</span><span class="sxs-lookup"><span data-stu-id="4b07d-113">For more information about how to use the DMX language, see [Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference).</span></span>  
  
 <span data-ttu-id="4b07d-114">此工作可查詢相同採礦結構上建立的多個採礦模型。</span><span class="sxs-lookup"><span data-stu-id="4b07d-114">The task can query multiple mining models that are built on the same mining structure.</span></span> <span data-ttu-id="4b07d-115">採礦模型是使用 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 提供的其中一種資料採礦演算法建立。</span><span class="sxs-lookup"><span data-stu-id="4b07d-115">A mining model is built using one of the data mining algorithms that [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] provides.</span></span> <span data-ttu-id="4b07d-116">「資料採礦查詢」工作參考的採礦結構，可包含多個使用不同演算法建立的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="4b07d-116">The mining structure that the Data Mining Query task references can include multiple mining models, built using different algorithms.</span></span> <span data-ttu-id="4b07d-117">如需詳細資訊，請參閱[採礦結構 &#40;Analysis Services - 資料採礦&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-structures-analysis-services-data-mining) 和[資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining)。</span><span class="sxs-lookup"><span data-stu-id="4b07d-117">For more information, see [Mining Structures &#40;Analysis Services - Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/mining-structures-analysis-services-data-mining) and [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](https://docs.microsoft.com/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining).</span></span>  
  
 <span data-ttu-id="4b07d-118">「資料採礦查詢」工作執行的預測查詢會傳回單一資料列或資料集的結果。</span><span class="sxs-lookup"><span data-stu-id="4b07d-118">The prediction query that the Data Mining Query task runs returns a result that is a single row or a data set.</span></span> <span data-ttu-id="4b07d-119">傳回單一資料列的查詢稱為單一查詢：例如，預測夏季各月間將售出之帆船數的查詢會傳回數字。</span><span class="sxs-lookup"><span data-stu-id="4b07d-119">A query that returns a single row is called a singleton query: for example, the query that predicts how many sailboats will be sold during the summer months returns a number.</span></span> <span data-ttu-id="4b07d-120">如需傳回單一資料列之預測查詢的詳細資訊，請參閱[資料採礦查詢介面](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools)。</span><span class="sxs-lookup"><span data-stu-id="4b07d-120">For more information about prediction queries that return a single row, see [Data Mining Query Interfaces](https://docs.microsoft.com/analysis-services/data-mining/data-mining-query-tools).</span></span>  
  
 <span data-ttu-id="4b07d-121">查詢結果會儲存到資料表。</span><span class="sxs-lookup"><span data-stu-id="4b07d-121">The query results are saved to tables.</span></span> <span data-ttu-id="4b07d-122">如果「資料採礦查詢」工作指定的資料表名稱已存在，則工作可使用相同的名稱附加一個號碼建立新的資料表，或者覆寫資料表內容。</span><span class="sxs-lookup"><span data-stu-id="4b07d-122">If a table with the name that the Data Mining Query task specifies already exists, the task can create a new table, using the same name with a number appended, or it can overwrite the table content.</span></span>  
  
 <span data-ttu-id="4b07d-123">如果結果包含巢狀，則會在儲存之前扁平化結果。</span><span class="sxs-lookup"><span data-stu-id="4b07d-123">If the results include nesting, the result is flattened before it is saved.</span></span> <span data-ttu-id="4b07d-124">扁平化結果會將巢狀結果集變更成資料表。</span><span class="sxs-lookup"><span data-stu-id="4b07d-124">Flattening a result changes a nested result set to a table.</span></span> <span data-ttu-id="4b07d-125">例如，扁平化含有 **Customer** 資料行和巢狀 **Product** 資料行的巢狀結果，會將資料列加入至 **Customer** 資料行，以製作包含各客戶之產品資料的資料表。</span><span class="sxs-lookup"><span data-stu-id="4b07d-125">For example, flattening a nested result with a **Customer** column and a nested **Product** column adds rows to the **Customer** column to make a table that includes product data for each customer.</span></span> <span data-ttu-id="4b07d-126">例如，擁有三種不同產品的客戶會變成擁有三個資料列的資料表，各資料列中會重複該客戶並包含不同的產品。</span><span class="sxs-lookup"><span data-stu-id="4b07d-126">For example, a customer with three different products becomes a table with three rows, repeating the customer in each row and including a different product in each row.</span></span> <span data-ttu-id="4b07d-127">如果省略 FLATTENED 關鍵字，則資料表只會包含 **Customer** 資料行，且每個客戶只有一個資料列。</span><span class="sxs-lookup"><span data-stu-id="4b07d-127">If the FLATTENED keyword is omitted, the table contains only the **Customer** column and only one row per customer.</span></span> <span data-ttu-id="4b07d-128">如需詳細資訊，請參閱 [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx)。</span><span class="sxs-lookup"><span data-stu-id="4b07d-128">For more information, see [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).</span></span>  
  
## <a name="configuration-of-the-data-mining-query-task"></a><span data-ttu-id="4b07d-129">設定資料採礦查詢工作</span><span class="sxs-lookup"><span data-stu-id="4b07d-129">Configuration of the Data Mining Query Task</span></span>  
 <span data-ttu-id="4b07d-130">「資料採礦查詢」工作需要兩個連接。</span><span class="sxs-lookup"><span data-stu-id="4b07d-130">The Data Mining Query task requires two connections.</span></span> <span data-ttu-id="4b07d-131">第一個連線是 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 連線管理員，其會連線到 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 的執行個體，或含有採礦結構和採礦模型的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="4b07d-131">The first connection is an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] connection manager that connects either to an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] or to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project that contains the mining structure and the mining model.</span></span> <span data-ttu-id="4b07d-132">第二個連接是 OLE DB 連接管理員，會連接到含有工作所寫入資料表的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="4b07d-132">The second connection is an OLE DB connection manager that connects to the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] database that contains the table to which the task writes.</span></span> <span data-ttu-id="4b07d-133">如需相關資訊，請參閱 [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md) 及 [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="4b07d-133">For more information, see [Analysis Services Connection Manager](../connection-manager/analysis-services-connection-manager.md) and [OLE DB Connection Manager](../connection-manager/ole-db-connection-manager.md).</span></span>  
  
 <span data-ttu-id="4b07d-134">您可以透過 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="4b07d-134">You can set properties through [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer or programmatically.</span></span>  
  
 <span data-ttu-id="4b07d-135">如需有關可以在「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」中設定之屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="4b07d-135">For more information about the properties that you can set in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click one of the following topics:</span></span>  
  
-   [<span data-ttu-id="4b07d-136">資料採礦查詢工作編輯器 &#40;採礦模型索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="4b07d-136">Data Mining Query Task Editor &#40;Mining Model Tab&#41;</span></span>](../data-mining-query-task-editor-mining-model-tab.md)  
  
-   [<span data-ttu-id="4b07d-137">資料採礦查詢工作編輯器 &#40;查詢索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="4b07d-137">Data Mining Query Task Editor &#40;Query Tab&#41;</span></span>](../data-mining-query-task-editor-query-tab.md)  
  
-   [<span data-ttu-id="4b07d-138">資料採礦查詢工作編輯器 &#40;輸出索引標籤&#41;</span><span class="sxs-lookup"><span data-stu-id="4b07d-138">Data Mining Query Task Editor &#40;Output Tab&#41;</span></span>](../data-mining-query-task-editor-output-tab.md)  
  
> [!NOTE]  
>  <span data-ttu-id="4b07d-139">「資料採礦查詢編輯器」沒有「運算式」頁面，</span><span class="sxs-lookup"><span data-stu-id="4b07d-139">The Data Mining Query Editor has no Expressions page.</span></span> <span data-ttu-id="4b07d-140">而是另外使用 **[屬性]** 視窗存取用來建立和管理「資料採礦查詢」工作屬性之屬性運算式的工具。</span><span class="sxs-lookup"><span data-stu-id="4b07d-140">Instead, use the **Properties** window to access the tools for creating and managing property expressions for properties of the Data Mining Query task.</span></span>  
  
 <span data-ttu-id="4b07d-141">如需有關如何在「 [!INCLUDE[ssIS](../../../includes/ssis-md.md)] 設計師」中設定這些屬性的詳細資訊，請按下列主題：</span><span class="sxs-lookup"><span data-stu-id="4b07d-141">For more information about how to set these properties in [!INCLUDE[ssIS](../../../includes/ssis-md.md)] Designer, click the following topic:</span></span>  
  
-   [<span data-ttu-id="4b07d-142">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="4b07d-142">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="programmatic-configuration-of-data-mining-query-task"></a><span data-ttu-id="4b07d-143">以程式設計方式設定資料採礦查詢工作</span><span class="sxs-lookup"><span data-stu-id="4b07d-143">Programmatic Configuration of Data Mining Query Task</span></span>  
 <span data-ttu-id="4b07d-144">如需有關以程式設計方式設定這些屬性的詳細資訊，請按下列其中一個主題：</span><span class="sxs-lookup"><span data-stu-id="4b07d-144">For more information about programmatically setting these properties, click one of the following topics:</span></span>  
  
-   <xref:Microsoft.SqlServer.Dts.Tasks.DMQueryTask.DMQueryTask>  
  
  
