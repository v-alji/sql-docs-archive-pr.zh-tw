---
title: 資料採礦查詢介面 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- predictions [Analysis Services], DMX prediction queries
- predictions [DMX]
- DMX [Analysis Services], prediction queries
- prediction queries [DMX]
- predictions [Analysis Services]
- queries [DMX], prediction queries
- mining models [Analysis Services], DMX
ms.assetid: a8952427-fd8c-4300-8f62-25f57ac1be0c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1702ad82c65b5a7370a62c4bc31a08007f374c9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606509"
---
# <a name="data-mining-query-interfaces"></a><span data-ttu-id="8dd30-102">資料採礦查詢介面</span><span class="sxs-lookup"><span data-stu-id="8dd30-102">Data Mining Query Interfaces</span></span>
  <span data-ttu-id="8dd30-103">資料採礦查詢是以資料採礦延伸模組 (DMX) 語言為基礎。</span><span class="sxs-lookup"><span data-stu-id="8dd30-103">Data mining queries are based on the Data Mining Extensions (DMX) language.</span></span> <span data-ttu-id="8dd30-104">您可以針對所有預測和模型工作使用 DMX，包括分類、風險分析、產生建議及線性迴歸。</span><span class="sxs-lookup"><span data-stu-id="8dd30-104">You use DMX for all prediction and modeling tasks, including classification, risk analysis, generation of recommendations, and linear regression.</span></span> <span data-ttu-id="8dd30-105">您也可以擷取處理模型時所產生的模式和統計資料。</span><span class="sxs-lookup"><span data-stu-id="8dd30-105">You can also retrieve the patterns and statistics that were generated when you processed the model.</span></span>  
  
 <span data-ttu-id="8dd30-106">使用 DMX 的預測查詢語法與 [!INCLUDE[tsql](../../includes/tsql-md.md)] 的查詢語法類似。</span><span class="sxs-lookup"><span data-stu-id="8dd30-106">The syntax for a prediction query using DMX is similar to the syntax for a query in [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span> <span data-ttu-id="8dd30-107">[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 都提供協助您建立 DMX 預測查詢的工具。</span><span class="sxs-lookup"><span data-stu-id="8dd30-107">Both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] provide tools that help you build DMX prediction queries.</span></span>  
  
 <span data-ttu-id="8dd30-108">此主題描述您可以透過 DMX 用來建立及執行資料採礦查詢的介面。</span><span class="sxs-lookup"><span data-stu-id="8dd30-108">This topic describes the interfaces that you can use to create and execute data mining queries using DMX.</span></span>  
  
 [<span data-ttu-id="8dd30-109">查詢工具</span><span class="sxs-lookup"><span data-stu-id="8dd30-109">Query Tools</span></span>](#bkmk_Tools)  
  
-   [<span data-ttu-id="8dd30-110">預測查詢產生器</span><span class="sxs-lookup"><span data-stu-id="8dd30-110">Prediction Query Builder</span></span>](#bkmk_Builder)  
  
-   [<span data-ttu-id="8dd30-111">查詢編輯器</span><span class="sxs-lookup"><span data-stu-id="8dd30-111">Query Editor</span></span>](#bkmk_QueryEditor)  
  
-   [<span data-ttu-id="8dd30-112">DMX 範本</span><span class="sxs-lookup"><span data-stu-id="8dd30-112">DMX Templates</span></span>](#bkmk_Templates)  
  
-   [<span data-ttu-id="8dd30-113">Integration Services</span><span class="sxs-lookup"><span data-stu-id="8dd30-113">Integration Services</span></span>](#bkmk_SSIS)  
  
 [<span data-ttu-id="8dd30-114">應用程式開發介面</span><span class="sxs-lookup"><span data-stu-id="8dd30-114">Application Programming Interfaces</span></span>](#bkmk_API)  
  
##  <a name="data-mining-query-tools"></a><a name="bkmk_Tools"></a><span data-ttu-id="8dd30-115">資料採礦查詢工具</span><span class="sxs-lookup"><span data-stu-id="8dd30-115">Data Mining Query Tools</span></span>  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="8dd30-116">會提供下列工具，這些工具可讓您用來針對資料採礦物件建立預測查詢、內容查詢和資料定義查詢：</span><span class="sxs-lookup"><span data-stu-id="8dd30-116">provides the following tools that you can use to build prediction queries, content queries, and data definition queries against data mining objects:</span></span>  
  
-   <span data-ttu-id="8dd30-117">預測查詢產生器</span><span class="sxs-lookup"><span data-stu-id="8dd30-117">Prediction Query Builder</span></span>  
  
-   <span data-ttu-id="8dd30-118">查詢編輯器</span><span class="sxs-lookup"><span data-stu-id="8dd30-118">Query Editor</span></span>  
  
-   <span data-ttu-id="8dd30-119">DMX 範本</span><span class="sxs-lookup"><span data-stu-id="8dd30-119">DMX templates</span></span>  
  
-   <span data-ttu-id="8dd30-120">Integration Services 資料採礦元件</span><span class="sxs-lookup"><span data-stu-id="8dd30-120">Integration Services data mining components</span></span>  
  
###  <a name="prediction-query-builder"></a><a name="bkmk_Builder"></a><span data-ttu-id="8dd30-121">預測查詢產生器</span><span class="sxs-lookup"><span data-stu-id="8dd30-121">Prediction Query Builder</span></span>  
 <span data-ttu-id="8dd30-122">預測查詢產生器包含在資料採礦設計師 ([!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 和 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 都有提供) 的 [採礦模型預測]\*\*\*\* 索引標籤中。</span><span class="sxs-lookup"><span data-stu-id="8dd30-122">Prediction Query Builder is included in the **Mining Model Prediction** tab of Data Mining Designer, which is available in both [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]and [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="8dd30-123">在使用查詢產生器時，可以使用圖形工具來選取採礦模型、加入新的案例資料以及加入預測函數。</span><span class="sxs-lookup"><span data-stu-id="8dd30-123">When you use the query builder, you can use graphical tools to select a mining model, add new case data, and add prediction functions.</span></span> <span data-ttu-id="8dd30-124">[預測查詢產生器] 包含可讓您手動修改查詢的文字編輯器，以及用來查看查詢結果的簡單 [**結果**] 窗格。</span><span class="sxs-lookup"><span data-stu-id="8dd30-124">The Prediction Query Builder includes a text editor that you can use to modify the query manually, and a simple **Results** pane to view the results of the query.</span></span>  
  
###  <a name="query-editor"></a><a name="bkmk_QueryEditor"></a><span data-ttu-id="8dd30-125">查詢編輯器</span><span class="sxs-lookup"><span data-stu-id="8dd30-125">Query Editor</span></span>  
 <span data-ttu-id="8dd30-126">中的查詢編輯器 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 會提供工具，讓您用來建立及執行 DMX 查詢。</span><span class="sxs-lookup"><span data-stu-id="8dd30-126">The Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] provides tools that you can use to build and run DMX queries.</span></span> <span data-ttu-id="8dd30-127">您可以連接到 SQL Server Analysis Services 的執行個體，然後選取資料庫、採礦結構資料行和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="8dd30-127">You can connect to an instance of SQL Server Analysis Services, and then select a database, mining structure columns, and a mining model.</span></span> <span data-ttu-id="8dd30-128">中繼資料總管\*\*\*\* 包含您可以瀏覽的預測函數清單。</span><span class="sxs-lookup"><span data-stu-id="8dd30-128">The **Metadata Explorer** contains a list of prediction functions that you can browse.</span></span>  
  
###  <a name="dmx-templates"></a><a name="bkmk_Templates"></a> <span data-ttu-id="8dd30-129">DMX 範本</span><span class="sxs-lookup"><span data-stu-id="8dd30-129">DMX Templates</span></span>  
 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="8dd30-130">提供互動式的 DMX 查詢範本，可用來建立 DMX 查詢。</span><span class="sxs-lookup"><span data-stu-id="8dd30-130">provides interactive DMX query templates that you can use to build DMX queries.</span></span> <span data-ttu-id="8dd30-131">如果您看不到範本清單，請按一下工具列上的 [檢視]\*\*\*\*，然後選取 [範本總管]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8dd30-131">If you do not see the list of templates, click **View** on the toolbar, and select **Template Explorer**.</span></span> <span data-ttu-id="8dd30-132">若要查看所有 Analysis Services 範本 (包括 DMX、MDX 及 XMLA 的範本)，請按一下 Cube 圖示。</span><span class="sxs-lookup"><span data-stu-id="8dd30-132">To see all Analysis Services templates, including templates for DMX, MDX, and XMLA, click the cube icon.</span></span>  
  
 <span data-ttu-id="8dd30-133">若要使用範本建立查詢，您可以將範本拖曳到開啟的查詢視窗，也可以按兩下範本，開啟新的連接和新的查詢窗格。</span><span class="sxs-lookup"><span data-stu-id="8dd30-133">To build a query using a template, you can drag the template into an open query window, or you can double-click the template to open a new connection and a new query pane.</span></span>  
  
 <span data-ttu-id="8dd30-134">如需如何根據範本建立預測查詢的範例，請參閱 [根據範本建立單一預測查詢](create-a-singleton-prediction-query-from-a-template.md)。</span><span class="sxs-lookup"><span data-stu-id="8dd30-134">For an example of how to create a prediction query from a template, see [Create a Singleton Prediction Query from a Template](create-a-singleton-prediction-query-from-a-template.md).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="8dd30-135">適用於 Microsoft Office Excel 的資料採礦增益集也包含許多範本，連同可幫助您撰寫複雜 DMX 陳述式的互動式查詢產生器。</span><span class="sxs-lookup"><span data-stu-id="8dd30-135">The Data Mining Add-in for Microsoft Office Excel also contains a number of templates, along with an interactive query builder which can help you compose complex DMX statements.</span></span> <span data-ttu-id="8dd30-136">若要使用範本，請在資料採礦用戶端中按一下 [查詢]\*\*\*\*，再按一下 [進階]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8dd30-136">To use the templates, click **Query**, and click **Advanced** in the Data Mining Client.</span></span>  
  
###  <a name="integration-services-data-mining-components"></a><a name="bkmk_SSIS"></a><span data-ttu-id="8dd30-137">Integration Services 資料採礦元件</span><span class="sxs-lookup"><span data-stu-id="8dd30-137">Integration Services Data Mining Components</span></span>  
 <span data-ttu-id="8dd30-138">您也可以將預測查詢包含為封裝的一部分 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="8dd30-138">You can also include prediction queries as part of a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="8dd30-139">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 中的下列工作和轉換支援 DMX 預測查詢和 DMX 陳述式的建立及執行。</span><span class="sxs-lookup"><span data-stu-id="8dd30-139">The following tasks and transformations in [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] support the creation and execution of DMX prediction queries and DMX statements.</span></span>  
  
|<span data-ttu-id="8dd30-140">元件</span><span class="sxs-lookup"><span data-stu-id="8dd30-140">Component</span></span>|<span data-ttu-id="8dd30-141">描述</span><span class="sxs-lookup"><span data-stu-id="8dd30-141">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8dd30-142">資料採礦查詢工作</span><span class="sxs-lookup"><span data-stu-id="8dd30-142">Data Mining Query task</span></span>|<span data-ttu-id="8dd30-143">執行 DMX 查詢和其他 DMX 陳述式當做控制流程的一部分。</span><span class="sxs-lookup"><span data-stu-id="8dd30-143">Executes DMX queries and other DMX statements as part of a control flow.</span></span><br /><br /> <span data-ttu-id="8dd30-144">工作編輯器提供預測查詢產生器，以及用來手動修改 DMX 查詢的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="8dd30-144">The task editor provides the Prediction Query Builder, and a text box for modifying the DMX query manually.</span></span> <span data-ttu-id="8dd30-145">但是，工作編輯器無法根據 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 方案中的物件驗證查詢。</span><span class="sxs-lookup"><span data-stu-id="8dd30-145">However, the task editor cannot validate the query against objects in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] solution.</span></span> <span data-ttu-id="8dd30-146">因此，最好在 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] 或 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中建立查詢，然後將陳述式或查詢文字貼入工作編輯器。</span><span class="sxs-lookup"><span data-stu-id="8dd30-146">Therefore, it is best to create a query within [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] or [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] and then paste the text of the statement or query into the task editor.</span></span>|  
|<span data-ttu-id="8dd30-147">資料採礦查詢轉換</span><span class="sxs-lookup"><span data-stu-id="8dd30-147">Data Mining Query transformation</span></span>|<span data-ttu-id="8dd30-148">使用資料流程來源所提供的資料，在資料流程內執行預測查詢。</span><span class="sxs-lookup"><span data-stu-id="8dd30-148">Executes a prediction query within a data flow, using data supplied by a data flow source.</span></span><br /><br /> <span data-ttu-id="8dd30-149">工作編輯器提供預測查詢產生器，以及用來手動修改 DMX 查詢的文字方塊。</span><span class="sxs-lookup"><span data-stu-id="8dd30-149">The task editor provides the Prediction Query Builder, and a text box for modifying the DMX query manually.</span></span><br /><br /> <span data-ttu-id="8dd30-150">轉換只能用於建立使用資料流程中之資料的查詢，也就是使用 PREDICTION JOIN 語法的查詢。</span><span class="sxs-lookup"><span data-stu-id="8dd30-150">The transformation can only be used for creating queries that use data in the data flow; that is, queries that use the PREDICTION JOIN syntax.</span></span> <span data-ttu-id="8dd30-151">此元件不能用於執行內容查詢或其他類型的 DMX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="8dd30-151">This component cannot be used for executing content queries or other kinds of DMX statements.</span></span>|  
  
##  <a name="application-programming-interfaces"></a><a name="bkmk_API"></a><span data-ttu-id="8dd30-152">應用程式設計介面</span><span class="sxs-lookup"><span data-stu-id="8dd30-152">Application Programming Interfaces</span></span>  
 <span data-ttu-id="8dd30-153">您可以搭配 OLE DB 或 Analysis Services ADOMD 用戶端等伺服器通訊協定使用各種程式語言，建立針對資料採礦模型執行查詢的自訂應用程式。</span><span class="sxs-lookup"><span data-stu-id="8dd30-153">You can create custom applications that execute queries against data mining models by using a variety of programming languages, in combination with server protocols such as OLE DB or Analysis Services ADOMD client.</span></span> <span data-ttu-id="8dd30-154">如需詳細資訊，請參閱 [資料採礦程式設計](../dev-guide/data-mining-programming.md)。</span><span class="sxs-lookup"><span data-stu-id="8dd30-154">For more information, see [Data Mining Programming](../dev-guide/data-mining-programming.md).</span></span>  
  
 <span data-ttu-id="8dd30-155">不過，XMLA 會構成與 Analysis Service 伺服器之所有互動的基礎訊息格式。</span><span class="sxs-lookup"><span data-stu-id="8dd30-155">However, XMLA constitutes the underlying message format for all interactions with an Analysis Service server.</span></span> <span data-ttu-id="8dd30-156">在 XMLA 訊息內，查詢的表示方式會根據您傳送的是以 DMX 為基礎的預測查詢、內容查詢，或使用資料採礦結構描述資料列集擷取模型中繼資料的查詢而有所不同。</span><span class="sxs-lookup"><span data-stu-id="8dd30-156">Within an XMLA message, queries are represented differently depending on whether you are sending a prediction query based on DMX, a content query, or a query that retrieves model metadata using the data mining schema rowsets.</span></span>  
  
-   <span data-ttu-id="8dd30-157">**預測查詢** (及所有其他 DMX 陳述式) 的文字會使用 [Execute 方法 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) 方法以 XMLA 傳送，並將 DMX 查詢作為文字放在 XMLA [Command 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/command-element-xmla) 元素的 [Statement 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) 內。</span><span class="sxs-lookup"><span data-stu-id="8dd30-157">The text of **prediction queries** (and all other DMX statements) is sent in XMLA by using the [Execute Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method, with the DMX query placed as text within the [Statement Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) element of the XMLA [Command Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/command-element-xmla) element.</span></span>  
  
-   <span data-ttu-id="8dd30-158">若要擷取**模型內容**和**模型中繼資料** (例如叢集數、決策樹中所使用的屬性、模型上次處理的日期及建立模型時所使用的演算法參數)，您可以使用 [Discover 方法 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) 方法，並在 [RequestType 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) 標頭中指定其中一個資料採礦結構描述資料列集。</span><span class="sxs-lookup"><span data-stu-id="8dd30-158">To retrieve **model content** and **model metadata**, such as the number of clusters, the attributes used in decision trees, the date the model was last processed, and the algorithm parameters used when creating the model, you can use the [Discover Method &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) method and specify one of the data mining schema rowsets in the [RequestType Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/type-element-xmla) header.</span></span> <span data-ttu-id="8dd30-159">若要縮小查詢範圍，請輸入準則作為 [RestrictionList 元素 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictionlist-element-xmla) 元素內的限制。</span><span class="sxs-lookup"><span data-stu-id="8dd30-159">To narrow the scope of the query, enter criteria as restrictions within the [RestrictionList Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/restrictionlist-element-xmla) element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dd30-160">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8dd30-160">See Also</span></span>  
 <span data-ttu-id="8dd30-161">[資料採礦延伸模組 &#40;DMX&#41; 參考](/sql/dmx/data-mining-extensions-dmx-reference) </span><span class="sxs-lookup"><span data-stu-id="8dd30-161">[Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference) </span></span>  
 <span data-ttu-id="8dd30-162">[資料採礦解決方案](data-mining-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="8dd30-162">[Data Mining Solutions](data-mining-solutions.md) </span></span>  
 <span data-ttu-id="8dd30-163">[瞭解 DMX Select 語句](/sql/dmx/understanding-the-dmx-select-statement) </span><span class="sxs-lookup"><span data-stu-id="8dd30-163">[Understanding the DMX Select Statement](/sql/dmx/understanding-the-dmx-select-statement) </span></span>  
 <span data-ttu-id="8dd30-164">[DMX 預測查詢的結構和使用方式](/sql/dmx/structure-and-usage-of-dmx-prediction-queries) </span><span class="sxs-lookup"><span data-stu-id="8dd30-164">[Structure and Usage of DMX Prediction Queries](/sql/dmx/structure-and-usage-of-dmx-prediction-queries) </span></span>  
 <span data-ttu-id="8dd30-165">[使用預測查詢產生器來建立預測查詢](create-a-prediction-query-using-the-prediction-query-builder.md) </span><span class="sxs-lookup"><span data-stu-id="8dd30-165">[Create a Prediction Query Using the Prediction Query Builder](create-a-prediction-query-using-the-prediction-query-builder.md) </span></span>  
 [<span data-ttu-id="8dd30-166">在 SQL Server Management Studio 中建立 DMX 查詢</span><span class="sxs-lookup"><span data-stu-id="8dd30-166">Create a DMX Query in SQL Server Management Studio</span></span>](create-a-dmx-query-in-sql-server-management-studio.md)  
  
  
