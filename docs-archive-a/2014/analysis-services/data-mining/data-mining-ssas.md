---
title: 資料採礦 (SSAS) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], about data mining
ms.assetid: b1c912da-72f6-4d96-89c8-55a2c4f19e88
author: minewiskan
ms.author: owend
ms.openlocfilehash: 7044ee397d457f7924d0db99dbec6659f969f104
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598676"
---
# <a name="data-mining-ssas"></a><span data-ttu-id="fc6cc-102">資料採礦 (SSAS)</span><span class="sxs-lookup"><span data-stu-id="fc6cc-102">Data Mining (SSAS)</span></span>
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="fc6cc-103">提供併入資料採礦的方案一個整合式平台。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-103">provides an integrated platform for solutions that incorporate data mining.</span></span> <span data-ttu-id="fc6cc-104">您可以使用關聯式資料或 Cube 資料建立具有預測分析的商業智慧方案。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-104">You can use either relational or cube data to create business intelligence solutions with predictive analytics.</span></span>  
  
## <a name="benefits-of-data-mining"></a><span data-ttu-id="fc6cc-105">資料採礦的優點</span><span class="sxs-lookup"><span data-stu-id="fc6cc-105">Benefits of Data Mining</span></span>  
 <span data-ttu-id="fc6cc-106">資料採礦使用適當研究的統計原則探索資料中的模式，並協助您針對複雜的問題，做出明智的決策。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-106">Data mining uses well-researched statistical principles to discover patterns in your data, helping you make intelligent decisions about complex problems.</span></span> <span data-ttu-id="fc6cc-107">您可以將 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 中的資料採礦演算法套用至資料，以預測趨勢、識別模式、建立規則和建議、分析複雜資料集中的事件順序，以及取得新觀點。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-107">By applying the data mining algorithms in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to your data, you can forecast trends, identify patterns, create rules and recommendations, analyze the sequence of events in complex data sets, and gain new insights.</span></span>  
  
 <span data-ttu-id="fc6cc-108">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]中，資料採礦功能強大、可以存取，而且與許多人喜歡用於分析和報表的工具整合在一起。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-108">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)], data mining is powerful, accessible, and integrated with the tools that many people prefer to use for analysis and reporting.</span></span> <span data-ttu-id="fc6cc-109">請參閱本節中的連結，以取得有關入門所需之資料採礦的廣大背景。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-109">See the links in this section to get the broad background about data mining that you need to get started.</span></span>  
  
## <a name="key-data-mining-features"></a><span data-ttu-id="fc6cc-110">主要資料採礦功能</span><span class="sxs-lookup"><span data-stu-id="fc6cc-110">Key Data Mining Features</span></span>  
 <span data-ttu-id="fc6cc-111">SQL Server 提供下列功能，以支援整合式資料採礦方案：</span><span class="sxs-lookup"><span data-stu-id="fc6cc-111">SQL Server provides the following features in support of integrated data mining solutions:</span></span>  
  
-   <span data-ttu-id="fc6cc-112">多個資料來源：您不必建立資料倉儲或 OLAP Cube 來進行資料採礦。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-112">Multiple data sources: You do not have to create a data warehouse or an OLAP cube to do data mining.</span></span> <span data-ttu-id="fc6cc-113">您可以使用外部提供者的表格式資料、試算表，甚至文字檔。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-113">You can use tabular data from external providers, spreadsheets, and even text files.</span></span> <span data-ttu-id="fc6cc-114">您也可以輕鬆對 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中建立的 OLAP Cube 進行採礦。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-114">You can also easily mine OLAP cubes created in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="fc6cc-115">但是，您無法使用記憶體中資料庫內的資料。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-115">However, you cannot use data from an in-memory database.</span></span>  
  
-   <span data-ttu-id="fc6cc-116">整合式資料清理、資料管理及 ETL：Data Quality Services 提供分析及清理資料的進階工具。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-116">Integrated data cleansing, data management, and ETL: Data Quality Services provides advanced tools for profiling and cleansing data.</span></span> <span data-ttu-id="fc6cc-117">Integration Services 可用來建立 ETL 程序，該程序不僅可以用來清理資料，也可以用來建立、處理、定型及更新模型。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-117">Integration Services can be used to build ETL processes for cleaning data, and also for building, processing, training, and updating models.</span></span>  
  
-   <span data-ttu-id="fc6cc-118">多個可自訂的演算法：除了提供叢集、類神經網路及決策樹等演算法之外，此平台也支援開發您自己的自訂外掛程式演算法。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-118">Multiple customizable algorithms: In addition to providing algorithms such as clustering, neural networks, and decisions trees, the platform supports development of your own custom plug-in algorithms.</span></span>  
  
-   <span data-ttu-id="fc6cc-119">模型測試基礎結構：使用交叉驗證、分類矩陣、增益圖及散佈圖等重要的統計工具，來測試您的模型和資料集。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-119">Model testing infrastructure: Test your models and data sets using important statistical tools as cross-validation, classification matrices, lift charts, and scatter plots.</span></span> <span data-ttu-id="fc6cc-120">輕鬆建立及管理測試集和定型集。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-120">Easily create and manage testing and training sets.</span></span>  
  
-   <span data-ttu-id="fc6cc-121">查詢和鑽研：建立預測查詢、擷取模型模式和統計資料，以及鑽研到案例資料。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-121">Querying and drillthrough: Create prediction queries, retrieve model patterns and statistics, and drill through to case data.</span></span>  
  
-   <span data-ttu-id="fc6cc-122">用戶端工具：除了 SQL Server 提供的開發和設計 Studio 之外，您也可以使用 Excel 的資料採礦增益集建立、查詢及瀏覽模型，</span><span class="sxs-lookup"><span data-stu-id="fc6cc-122">Client tools: In addition to the development and design studios provided by SQL Server, you can use the Data Mining Add-ins for Excel to create, query, and browse models.</span></span> <span data-ttu-id="fc6cc-123">或建立自訂用戶端，包括 Web 服務。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-123">Or, create custom clients, including Web services.</span></span>  
  
-   <span data-ttu-id="fc6cc-124">指令碼語言支援和 Managed API：所有資料採礦物件皆可完整程式化。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-124">Scripting language support and managed API: All data mining objects are fully programmable.</span></span> <span data-ttu-id="fc6cc-125">您可以透過 MDX、XMLA 或 PowerShell Extensions for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]編寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-125">Scripting is possible through MDX, XMLA, or the PowerShell extensions for [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="fc6cc-126">使用資料採礦延伸模組 (DMX) 語言快速查詢及編寫指令碼。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-126">Use the Data Mining Extensions (DMX) language for fast querying and scripting.</span></span>  
  
-   <span data-ttu-id="fc6cc-127">安全性和部署：透過 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]提供以角色為基礎的安全性，包括鑽研到模型及結構化資料的個別權限。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-127">Security and deployment: Provides role-based security through [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], including separate permissions for drillthrough to model and structure data.</span></span> <span data-ttu-id="fc6cc-128">輕鬆將模型部署至其他伺服器，讓使用者可以存取模式或執行預測</span><span class="sxs-lookup"><span data-stu-id="fc6cc-128">Easy deployment of models to other servers, so that users can access the patterns or perform predictions</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fc6cc-129">本節內容</span><span class="sxs-lookup"><span data-stu-id="fc6cc-129">In This Section</span></span>  
 <span data-ttu-id="fc6cc-130">本節中的主題介紹 SQL Server 資料採礦的主要功能及相關工作。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-130">The topics in this section introduce the principal features of SQL Server Data Mining and related tasks.</span></span>  
  
-   [<span data-ttu-id="fc6cc-131">資料採礦概念</span><span class="sxs-lookup"><span data-stu-id="fc6cc-131">Data Mining Concepts</span></span>](data-mining-concepts.md)  
  
-   [<span data-ttu-id="fc6cc-132">資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="fc6cc-132">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-algorithms-analysis-services-data-mining.md)  
  
-   [<span data-ttu-id="fc6cc-133">採礦結構 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="fc6cc-133">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](mining-structures-analysis-services-data-mining.md)  
  
-   [<span data-ttu-id="fc6cc-134">採礦模型 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="fc6cc-134">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-models-analysis-services-data-mining.md)  
  
-   [<span data-ttu-id="fc6cc-135">測試及驗證 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="fc6cc-135">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
-   [<span data-ttu-id="fc6cc-136">資料採礦查詢</span><span class="sxs-lookup"><span data-stu-id="fc6cc-136">Data Mining Queries</span></span>](data-mining-queries.md)  
  
-   [<span data-ttu-id="fc6cc-137">資料採礦方案</span><span class="sxs-lookup"><span data-stu-id="fc6cc-137">Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
-   [<span data-ttu-id="fc6cc-138">資料採礦工具。</span><span class="sxs-lookup"><span data-stu-id="fc6cc-138">Data Mining Tools</span></span>](data-mining-tools.md)  
  
-   [<span data-ttu-id="fc6cc-139">資料採礦架構</span><span class="sxs-lookup"><span data-stu-id="fc6cc-139">Data Mining Architecture</span></span>](data-mining-architecture.md)  
  
-   [<span data-ttu-id="fc6cc-140">安全性概觀 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="fc6cc-140">Security Overview &#40;Data Mining&#41;</span></span>](security-overview-data-mining.md)  
  
  
