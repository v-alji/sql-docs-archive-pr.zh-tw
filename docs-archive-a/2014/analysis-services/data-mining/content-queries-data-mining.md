---
title: " (資料採礦) 的內容查詢 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: c4f4a5a8-a230-4222-bece-9d563501f65f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44b162c34f5f505462a713205d8434484473afa4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607166"
---
# <a name="content-queries-data-mining"></a><span data-ttu-id="399b0-102">內容查詢 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="399b0-102">Content Queries (Data Mining)</span></span>
  <span data-ttu-id="399b0-103">內容查詢是一種擷取採礦模型之內部統計資料和結構相關資訊的方法。</span><span class="sxs-lookup"><span data-stu-id="399b0-103">A content query is a way of extracting information about the internal statistics and structure of the mining model.</span></span> <span data-ttu-id="399b0-104">內容查詢有時候可以提供檢視器中無法隨時取得的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="399b0-104">Sometimes a content query can provide details that are not readily available in the viewer.</span></span> <span data-ttu-id="399b0-105">您也可以使用內容查詢的結果，以程式設計的方式擷取其他用途的資訊。</span><span class="sxs-lookup"><span data-stu-id="399b0-105">You can also use the results of a content query to extract information programmatically for other uses.</span></span>  
  
 <span data-ttu-id="399b0-106">本節提供有關可使用內容查詢擷取之資訊類型，以及內容查詢之一般 DMX 語法的一般資訊。</span><span class="sxs-lookup"><span data-stu-id="399b0-106">This section provides general information about the types of information that you can retrieve by using a content query, and the general DMX syntax for content queries.</span></span>  
  
 [<span data-ttu-id="399b0-107">基本內容查詢</span><span class="sxs-lookup"><span data-stu-id="399b0-107">Basic Content Queries</span></span>](#bkmk_ContentQuery)  
  
-   [<span data-ttu-id="399b0-108">結構和案例資料的查詢</span><span class="sxs-lookup"><span data-stu-id="399b0-108">Queries on Structure and Case Data</span></span>](#bkmk_Structure)  
  
-   [<span data-ttu-id="399b0-109">模型模式的查詢</span><span class="sxs-lookup"><span data-stu-id="399b0-109">Queries on Model Patterns</span></span>](#bkmk_Patterns)  
  
 [<span data-ttu-id="399b0-110">範例</span><span class="sxs-lookup"><span data-stu-id="399b0-110">Examples</span></span>](#bkmk_Examples)  
  
-   [<span data-ttu-id="399b0-111">關聯模型的內容查詢</span><span class="sxs-lookup"><span data-stu-id="399b0-111">Content Query on an Association Model</span></span>](#bkmk_Assoc)  
  
-   [<span data-ttu-id="399b0-112">決策樹模型的內容查詢</span><span class="sxs-lookup"><span data-stu-id="399b0-112">Content Query on a Decision Trees Model</span></span>](#bkmk_DecTree)  
  
 [<span data-ttu-id="399b0-113">使用查詢結果</span><span class="sxs-lookup"><span data-stu-id="399b0-113">Working with the Query Results</span></span>](#bkmk_Results)  
  
##  <a name="basic-content-queries"></a><a name="bkmk_ContentQuery"></a><span data-ttu-id="399b0-114">基本內容查詢</span><span class="sxs-lookup"><span data-stu-id="399b0-114">Basic Content Queries</span></span>  
 <span data-ttu-id="399b0-115">您可以使用預測查詢產生器建立內容查詢、使用 SQL Server Management Studio 隨附的 DMX 內容查詢範本，或是直接以 DMX 撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="399b0-115">You can create content queries by using the Prediction Query Builder, use the DMX content query templates that are provided in SQL Server Management Studio, or write queries directly in DMX.</span></span> <span data-ttu-id="399b0-116">與預測查詢不同的是，您不需要聯結外部資料，因此可以輕鬆撰寫內容查詢。</span><span class="sxs-lookup"><span data-stu-id="399b0-116">Unlike prediction queries you do not need to join external data, so content queries are easy to write.</span></span>  
  
 <span data-ttu-id="399b0-117">本節提供您可以建立的內容查詢類型概觀。</span><span class="sxs-lookup"><span data-stu-id="399b0-117">This section provides an overview of the types of content queries you can create.</span></span>  
  
-   <span data-ttu-id="399b0-118">採礦結構或案例資料的查詢可讓您檢視用於定型的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="399b0-118">Queries on the mining structure or case data let you view the detailed data that was used for training.</span></span>  
  
-   <span data-ttu-id="399b0-119">模型的查詢可以傳回模式、屬性清單、公式等。</span><span class="sxs-lookup"><span data-stu-id="399b0-119">Queries on the model can return patterns, lists of attributes, formulas, and so forth.</span></span>  
  
###  <a name="queries-on-structure-and-case-data"></a><a name="bkmk_Structure"></a> <span data-ttu-id="399b0-120">結構和案例資料的查詢</span><span class="sxs-lookup"><span data-stu-id="399b0-120">Queries on Structure and Case Data</span></span>  
 <span data-ttu-id="399b0-121">DMX 支援對用來建立採礦結構和模型的快取資料進行查詢。</span><span class="sxs-lookup"><span data-stu-id="399b0-121">DMX supports queries on the cached data that is used to build mining structures and models.</span></span> <span data-ttu-id="399b0-122">當您定義採礦結構時，預設會建立此快取，並在您處理結構或模型時擴展快取。</span><span class="sxs-lookup"><span data-stu-id="399b0-122">By default, this cache is created when you define the mining structure, and is populated when you process the structure or model.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="399b0-123">如果您需要將資料分成定型集和測試集，請勿清除或刪除此快取。</span><span class="sxs-lookup"><span data-stu-id="399b0-123">This cache cannot be cleared or deleted if you need to separate data into training and testing sets.</span></span> <span data-ttu-id="399b0-124">如果清除快取，則無法查詢案例資料。</span><span class="sxs-lookup"><span data-stu-id="399b0-124">If the cache is cleared, you cannot query the case data.</span></span>  
  
 <span data-ttu-id="399b0-125">下列範例示範建立案例資料之查詢或是查詢採礦結構中之資料的常見模式：</span><span class="sxs-lookup"><span data-stu-id="399b0-125">The following examples show the common patterns for creating queries on the case data, or queries on the data in the mining structure:</span></span>  
  
 <span data-ttu-id="399b0-126">**取得模型的所有案例**</span><span class="sxs-lookup"><span data-stu-id="399b0-126">**Get all the cases for a model**</span></span>  
 `SELECT FROM <model>.CASES`  
  
 <span data-ttu-id="399b0-127">使用此陳述式可從用來建立模型的案例資料中，擷取指定的資料行。</span><span class="sxs-lookup"><span data-stu-id="399b0-127">Use this statement to retrieve specified columns from the case data used to build a model.</span></span> <span data-ttu-id="399b0-128">您必須具有模型的鑽研權限，才能執行此查詢。</span><span class="sxs-lookup"><span data-stu-id="399b0-128">You must have drillthrough permissions on the model to run this query.</span></span>  
  
 <span data-ttu-id="399b0-129">**檢視所有包含在結構中的資料。**</span><span class="sxs-lookup"><span data-stu-id="399b0-129">**View all the data that is included in the structure**</span></span>  
 `SELECT FROM <structure>.CASES`  
  
 <span data-ttu-id="399b0-130">使用此陳述式可檢視所有包含在結構中的資料，包括未包含在特定採礦模型中的資料行。</span><span class="sxs-lookup"><span data-stu-id="399b0-130">Use this statement to view all the data that is included in the structure, including columns that are not included in a particular mining model.</span></span> <span data-ttu-id="399b0-131">您必須具有模型及結構的鑽研權限，才能從採礦結構中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="399b0-131">You must have drillthrough permissions on the model, as well as on the structure, to retrieve data from the mining structure.</span></span>  
  
 <span data-ttu-id="399b0-132">**取得值範圍**</span><span class="sxs-lookup"><span data-stu-id="399b0-132">**Get range of values**</span></span>  
 `SELECT DISTINCT RangeMin(<column>), RangeMax(<column>) FROM <model>`  
  
 <span data-ttu-id="399b0-133">使用此陳述式可尋找連續資料行或 DISCRETIZED 資料行值區的最小值、最大值及平均值。</span><span class="sxs-lookup"><span data-stu-id="399b0-133">Use this statement to find the minimum value, maximum value, and mean of a continuous column, or of the buckets of a DISCRETIZED column.</span></span>  
  
 <span data-ttu-id="399b0-134">**取得相異值**</span><span class="sxs-lookup"><span data-stu-id="399b0-134">**Get distinct values**</span></span>  
 `SELECT DISTINCT <column>FROM <model>`  
  
 <span data-ttu-id="399b0-135">使用此陳述式可擷取 DISCRETE 資料行的所有值。</span><span class="sxs-lookup"><span data-stu-id="399b0-135">Use this statement to retrieve all the values of a DISCRETE column.</span></span>  <span data-ttu-id="399b0-136">不要對 DISCRETIZED 資料行使用這個陳述式，應改用 `RangeMin` 和 `RangeMax` 函數。</span><span class="sxs-lookup"><span data-stu-id="399b0-136">Do not use this statement for DISCRETIZED columns; use the `RangeMin` and `RangeMax` functions instead.</span></span>  
  
 <span data-ttu-id="399b0-137">**尋找用來定型模型或結構的案例**</span><span class="sxs-lookup"><span data-stu-id="399b0-137">**Find the cases that were used to train a model or structure**</span></span>  
 `SELECT  FROM <mining structure.CASES WHERE IsTrainingCase()`  
  
 <span data-ttu-id="399b0-138">使用此陳述式可取得一組用來定型模型的完整資料。</span><span class="sxs-lookup"><span data-stu-id="399b0-138">Use this statement to get the complete set of data that was used in a training a model.</span></span>  
  
 <span data-ttu-id="399b0-139">**尋找用來測試模型或結構的案例**</span><span class="sxs-lookup"><span data-stu-id="399b0-139">**Find the cases that are used for testing a model or structure**</span></span>  
 `SELECT  FROM <mining structure.CASES WHERE IsTestingCase()`  
  
 <span data-ttu-id="399b0-140">使用此陳述式可取得保留給與特定結構相關之測試採礦模型的資料。</span><span class="sxs-lookup"><span data-stu-id="399b0-140">Use this statement to get the data that has been set aside for testing mining models related to a specific structure.</span></span>  
  
 <span data-ttu-id="399b0-141">**從特定模型模式鑽研到基礎案例資料**</span><span class="sxs-lookup"><span data-stu-id="399b0-141">**Drillthrough from a specific model pattern to underlying case data**</span></span>  
 `SELECT FROM <model>.CASESWHERE IsTrainingCase() AND IsInNode(<node>)`  
  
 <span data-ttu-id="399b0-142">使用此陳述式可從定型模型中擷取詳細的案例資料。</span><span class="sxs-lookup"><span data-stu-id="399b0-142">Use this statement to retrieve detailed case data from a trained model.</span></span> <span data-ttu-id="399b0-143">您必須指定特定節點：例如，您必須知道叢集的節點識別碼、決策樹的特定分支等。此外，您也必須擁有模型的鑽研權限，才能執行此查詢。</span><span class="sxs-lookup"><span data-stu-id="399b0-143">You must specify a specific node: for example, you must know the node ID of the cluster, the specific branch of the decision tree, etc. Moreover, you must have drillthrough permissions on the model to run this query.</span></span>  
  
###  <a name="queries-on-model-patterns-statistics-and-attributes"></a><a name="bkmk_Patterns"></a><span data-ttu-id="399b0-144">模型模式、統計資料和屬性的查詢</span><span class="sxs-lookup"><span data-stu-id="399b0-144">Queries on Model Patterns, Statistics, and Attributes</span></span>  
 <span data-ttu-id="399b0-145">資料採礦模型的內容有多種用途。</span><span class="sxs-lookup"><span data-stu-id="399b0-145">The content of a data mining model is useful for many purposes.</span></span> <span data-ttu-id="399b0-146">您可以使用模型內容查詢執行以下作業：</span><span class="sxs-lookup"><span data-stu-id="399b0-146">With a model content query, you can:</span></span>  
  
-   <span data-ttu-id="399b0-147">擷取公式或機率來進行自己的計算。</span><span class="sxs-lookup"><span data-stu-id="399b0-147">Extract formulas or probabilities for making your own calculations.</span></span>  
  
-   <span data-ttu-id="399b0-148">針對關聯模型，擷取用來產生預測的規則。</span><span class="sxs-lookup"><span data-stu-id="399b0-148">For an association model, retrieve the rules that are used to generate a prediction.</span></span>  
  
-   <span data-ttu-id="399b0-149">擷取特定規則的描述，以便在自訂應用程式中使用規則。</span><span class="sxs-lookup"><span data-stu-id="399b0-149">Retrieve the descriptions of specific rules so that you can use the rules in a custom application.</span></span>  
  
-   <span data-ttu-id="399b0-150">檢視時間序列模型偵測到的移動平均。</span><span class="sxs-lookup"><span data-stu-id="399b0-150">View the moving averages detected by a time series model.</span></span>  
  
-   <span data-ttu-id="399b0-151">取得趨勢線之某個線段的迴歸公式。</span><span class="sxs-lookup"><span data-stu-id="399b0-151">Obtain the regression formula for some segment of the trend line.</span></span>  
  
-   <span data-ttu-id="399b0-152">擷取有關客戶識別為屬於特定叢集的可付諸行動之資訊。</span><span class="sxs-lookup"><span data-stu-id="399b0-152">Retrieve actionable information about customers identified as being part of a specific cluster.</span></span>  
  
 <span data-ttu-id="399b0-153">下列範例顯示用來建立模型內容查詢的一些常見模式：</span><span class="sxs-lookup"><span data-stu-id="399b0-153">The following examples show some of the common patterns for creating queries on the model content:</span></span>  
  
 <span data-ttu-id="399b0-154">**取得模型中的模式**</span><span class="sxs-lookup"><span data-stu-id="399b0-154">**Get patterns from the model**</span></span>  
 `SELECT FROM <model>.CONTENT`  
  
 <span data-ttu-id="399b0-155">使用此陳述式可擷取模型中特定節點的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="399b0-155">Use this statement to retrieve detailed information about specific nodes in the model.</span></span> <span data-ttu-id="399b0-156">視演算法類型而定，節點可以包含規則和公式、支援和變異數統計資料等等。</span><span class="sxs-lookup"><span data-stu-id="399b0-156">Depending on the algorithm type, the node can contain rules and formulas, support and variance statistics, and so forth.</span></span>  
  
 <span data-ttu-id="399b0-157">**擷取定型模型中所使用的屬性**</span><span class="sxs-lookup"><span data-stu-id="399b0-157">**Retrieve attributes used in a trained model**</span></span>  
 `CALL System.GetModelAttributes(<model>)`  
  
 <span data-ttu-id="399b0-158">使用此預存程序可擷取模型所使用的屬性清單。</span><span class="sxs-lookup"><span data-stu-id="399b0-158">Use this stored procedure to retrieve the list of attributes that were used by a model.</span></span> <span data-ttu-id="399b0-159">例如，這項資訊可用於決定因特徵選取而刪除的屬性。</span><span class="sxs-lookup"><span data-stu-id="399b0-159">This information is useful for determining attributes that were eliminated as a result of feature selection, for example.</span></span>  
  
 <span data-ttu-id="399b0-160">**擷取儲存在資料採礦維度中的內容**</span><span class="sxs-lookup"><span data-stu-id="399b0-160">**Retrieve content stored in a data mining dimension**</span></span>  
 `SELECT FROM <model>.DIMENSIONCONTENT`  
  
 <span data-ttu-id="399b0-161">使用此陳述式可從資料採礦維度中擷取資料。</span><span class="sxs-lookup"><span data-stu-id="399b0-161">Use this statement to retrieve the data from a data mining dimension.</span></span>  
  
 <span data-ttu-id="399b0-162">這個查詢類型主要供內部使用。</span><span class="sxs-lookup"><span data-stu-id="399b0-162">This query type is principally for internal use.</span></span> <span data-ttu-id="399b0-163">但是，並非所有的演算法都支援這項功能。</span><span class="sxs-lookup"><span data-stu-id="399b0-163">However, not all algorithms support this functionality.</span></span> <span data-ttu-id="399b0-164">支援是由 MINING_SERVICES 結構描述資料列集中的旗標所代表。</span><span class="sxs-lookup"><span data-stu-id="399b0-164">Support is indicated by a flag in the MINING_SERVICES schema rowset.</span></span>  
  
 <span data-ttu-id="399b0-165">如果您開發自己的外掛程式演算法，可以使用此陳述式來確認用於測試的模型內容。</span><span class="sxs-lookup"><span data-stu-id="399b0-165">If you develop your own plug-in algorithm, you might use this statement to verify the content of your model for testing.</span></span>  
  
 <span data-ttu-id="399b0-166">**取得模型的 PMML 表示**</span><span class="sxs-lookup"><span data-stu-id="399b0-166">**Get the PMML representation of a model**</span></span>  
 `SELECT * FROM <model>.PMML`  
  
 <span data-ttu-id="399b0-167">取得以 PMML 格式表示模型的 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="399b0-167">Gets an XML document that represents the model in PMML format.</span></span> <span data-ttu-id="399b0-168">並非所有模型類型都受到支援。</span><span class="sxs-lookup"><span data-stu-id="399b0-168">Not all model types are supported.</span></span>  
  
##  <a name="examples"></a><a name="bkmk_Examples"></a> <span data-ttu-id="399b0-169">範例</span><span class="sxs-lookup"><span data-stu-id="399b0-169">Examples</span></span>  
 <span data-ttu-id="399b0-170">雖然在不同的演算法中會有一些標準的模型內容，但是內容的某些部分會因為用來建立模型的演算法而有很大的差異。</span><span class="sxs-lookup"><span data-stu-id="399b0-170">Although some model content is standard across algorithms, some parts of the content vary greatly depending on the algorithm that you used to build the model.</span></span> <span data-ttu-id="399b0-171">因此，當您建立內容查詢時，必須了解模型中有哪些資訊對於特定模型最有用。</span><span class="sxs-lookup"><span data-stu-id="399b0-171">Therefore, when you create a content query, you must understand what information in the model is most useful to your specific model.</span></span>  
  
 <span data-ttu-id="399b0-172">本節提供幾個範例，以便說明演算法的選擇如何影響模型內所儲存的資訊類型。</span><span class="sxs-lookup"><span data-stu-id="399b0-172">A few examples are provided in this section to illustrate how the choice of algorithm affects the kind of information that is stored in the model.</span></span> <span data-ttu-id="399b0-173">如需採礦模型內容以及每一個模型類型特有之內容的詳細資訊，請參閱 [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="399b0-173">For more information about mining model content, and the content that is specific to each model type, see [Mining Model Content &#40;Analysis Services - Data Mining&#41;](mining-model-content-analysis-services-data-mining.md).</span></span>  
  
###  <a name="example-1-content-query-on-an-association-model"></a><a name="bkmk_Assoc"></a> <span data-ttu-id="399b0-174">範例 1：關聯模型的內容查詢</span><span class="sxs-lookup"><span data-stu-id="399b0-174">Example 1: Content Query on an Association Model</span></span>  
 <span data-ttu-id="399b0-175">`SELECT FROM <model>.CONTENT`陳述式會根據您所查詢的模型類型傳回不同種類的資訊。</span><span class="sxs-lookup"><span data-stu-id="399b0-175">The statement, `SELECT FROM <model>.CONTENT`, returns different kinds of information, depending on the type of model you are querying.</span></span> <span data-ttu-id="399b0-176">如果是關聯模型，資訊的主要片段為 *「節點類型」*(Node Type)。</span><span class="sxs-lookup"><span data-stu-id="399b0-176">For an association model, a key piece of information is the *node type*.</span></span> <span data-ttu-id="399b0-177">節點類似於模型內容中資訊的容器。</span><span class="sxs-lookup"><span data-stu-id="399b0-177">Nodes are like containers for information in the model content.</span></span> <span data-ttu-id="399b0-178">在關聯模型中，代表規則之節點的 NODE_TYPE 值為 8，而代表項目集之節點的 NODE_TYPE 值則為 7。</span><span class="sxs-lookup"><span data-stu-id="399b0-178">In an association model, nodes that represent rules have a NODE_TYPE value of 8, whereas nodes that represent itemsets have a NODE_TYPE value of 7.</span></span>  
  
 <span data-ttu-id="399b0-179">因此，下列查詢會傳回前 10 個項目集，並依照支援排序 (預設的排序)。</span><span class="sxs-lookup"><span data-stu-id="399b0-179">Thus, the following query returns the top 10 itemsets, ranked by support (the default ordering).</span></span>  
  
```  
SELECT TOP 10 NODE_DESCRIPTION, NODE_PROBABILITY, SUPPORT  
FROM <model>.CONTENT WHERE NODE_TYPE = 7  
```  
  
 <span data-ttu-id="399b0-180">下列查詢會根據這項資訊。</span><span class="sxs-lookup"><span data-stu-id="399b0-180">The following query builds on this information.</span></span> <span data-ttu-id="399b0-181">此查詢會傳回三個數據行：節點的識別碼、完整的規則以及專案集右側的產品，也就是預測為與其他產品相關聯的產品，做為專案集的一部分。</span><span class="sxs-lookup"><span data-stu-id="399b0-181">The query returns three columns: the ID of the node, the complete rule, and the product on the right-hand side of the itemset-that is, the product that is predicted to be associated with some other products as part of an itemset.</span></span>  
  
```  
SELECT FLATTENED NODE_UNIQUE_NAME, NODE_DESCRIPTION,  
     (SELECT RIGHT(ATTRIBUTE_NAME, (LEN(ATTRIBUTE_NAME)-LEN('Association model name')))   
FROM NODE_DISTRIBUTION  
WHERE LEN(ATTRIBUTE_NAME)>2  
)   
AS RightSideProduct  
FROM [<Association model name>].CONTENT  
WHERE NODE_TYPE = 8   
ORDER BY NODE_SUPPORT DESC  
```  
  
 <span data-ttu-id="399b0-182">FLATTENED 關鍵字代表巢狀資料列集應該轉換成扁平化資料表。</span><span class="sxs-lookup"><span data-stu-id="399b0-182">The FLATTENED keyword indicates that the nested rowset should be converted into a flattened table.</span></span> <span data-ttu-id="399b0-183">代表規則右側產品的屬性包含在 NODE_DISTRIBUTION 資料表中；因此，我們會加入長度必須大於 2 的需求，只擷取包含屬性名稱的資料列。</span><span class="sxs-lookup"><span data-stu-id="399b0-183">The attribute that represents the product on the right-hand side of the rule is contained in the NODE_DISTRIBUTION table; therefore, we retrieve only the row that contains an attribute name, by adding a requirement that the length be greater than 2.</span></span>  
  
 <span data-ttu-id="399b0-184">簡單字串函數是用來移除第三個資料行的模型名稱</span><span class="sxs-lookup"><span data-stu-id="399b0-184">A simple string function is used to remove the name of the model from the third column.</span></span> <span data-ttu-id="399b0-185">(通常模型名稱會加到巢狀資料行值的前面)。</span><span class="sxs-lookup"><span data-stu-id="399b0-185">(Usually the model name is prefixed to the values of nested columns.)</span></span>  
  
 <span data-ttu-id="399b0-186">WHERE 子句指定 NODE_TYPE 的值應該為 8，以便只擷取規則。</span><span class="sxs-lookup"><span data-stu-id="399b0-186">The WHERE clause specifies that the value of NODE_TYPE should be 8, to retrieve only rules.</span></span>  
  
 <span data-ttu-id="399b0-187">如需詳細範例，請參閱 [關聯模型查詢範例](association-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="399b0-187">For more examples, see [Association Model Query Examples](association-model-query-examples.md).</span></span>  
  
###  <a name="example-2-content-query-on-a-decision-trees-model"></a><a name="bkmk_DecTree"></a> <span data-ttu-id="399b0-188">範例 2：決策樹模型的內容查詢</span><span class="sxs-lookup"><span data-stu-id="399b0-188">Example 2: Content Query on a Decision Trees Model</span></span>  
 <span data-ttu-id="399b0-189">決策樹模型可用於預測及分類。</span><span class="sxs-lookup"><span data-stu-id="399b0-189">A decision tree model can be used for prediction as well as for classification.</span></span>  <span data-ttu-id="399b0-190">此範例假設您正在使用模型預測結果，但是您也會想要查明哪些因素或規則可用來分類結果。</span><span class="sxs-lookup"><span data-stu-id="399b0-190">This example assumes that you are using the model to predict an outcome, but you also want to find out which factors or rules can be used to classify the outcome.</span></span>  
  
 <span data-ttu-id="399b0-191">在決策樹模型中，節點是用來表示樹狀節點和分葉節點。</span><span class="sxs-lookup"><span data-stu-id="399b0-191">In a decision tree model, nodes are used to represent both trees and leaf nodes.</span></span> <span data-ttu-id="399b0-192">每一個節點的標題都會包含結果路徑的描述。</span><span class="sxs-lookup"><span data-stu-id="399b0-192">The caption for each node contains the description of the path to the outcome.</span></span> <span data-ttu-id="399b0-193">因此，若要追蹤任何特定結果的路徑，您需要識別包含該結果的節點，然後取得該節點的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="399b0-193">Therefore, to trace the path for any particular outcome, you need to identify the node that contains it, and get the details for that node.</span></span>  
  
 <span data-ttu-id="399b0-194">在預測查詢中，您會加入預測函數 [PredictNodeId &#40;DMX&#41;](/sql/dmx/predictnodeid-dmx) 來取得相關節點的識別碼，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="399b0-194">In your prediction query, you add the prediction function [PredictNodeId &#40;DMX&#41;](/sql/dmx/predictnodeid-dmx), to get the ID of the related node, as shown in the following example:</span></span>  
  
```  
SELECT  Predict([Bike Buyer]), PredictNodeID([Bike Buyer])   
FROM [<decision tree model name>]  
PREDICTION JOIN   
<input rowset>   
```  
  
 <span data-ttu-id="399b0-195">您一旦取得包含結果之節點的識別碼之後，您可以擷取規則或路徑來說明預測，方法是建立包含 NODE_CAPTION 的內容查詢，如下所示：</span><span class="sxs-lookup"><span data-stu-id="399b0-195">Once you have the ID of the node that contains the outcome, you can retrieve the rule or path that explains the prediction by creating a content query that includes the NODE_CAPTION, as follows:</span></span>  
  
```  
SELECT NODE_CAPTION  
FROM [<decision tree model name>]   
WHERE NODE_UNIQUE_NAME= '<node id>'  
```  
  
 <span data-ttu-id="399b0-196">如需詳細範例，請參閱 [決策樹模型查詢範例](decision-trees-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="399b0-196">For more examples, see [Decision Trees Model Query Examples](decision-trees-model-query-examples.md).</span></span>  
  
##  <a name="working-with-the-query-results"></a><a name="bkmk_Results"></a><span data-ttu-id="399b0-197">使用查詢結果</span><span class="sxs-lookup"><span data-stu-id="399b0-197">Working with the Query Results</span></span>  
 <span data-ttu-id="399b0-198">如範例所示，內容查詢主要會傳回表格式資料列集，但也可能包含巢狀資料行中的資訊。</span><span class="sxs-lookup"><span data-stu-id="399b0-198">As the examples demonstrate, content queries mostly return tabular rowsets, but can also include information from nested columns.</span></span> <span data-ttu-id="399b0-199">您可以扁平化傳回的資料列集，但是這麼做會讓結果使用起來更複雜。</span><span class="sxs-lookup"><span data-stu-id="399b0-199">You can flatten the rowset that is returned, but this can make working with results more complex.</span></span> <span data-ttu-id="399b0-200">特別是 NODE_DISTRIBUTION 節點的內容是以巢狀方式內嵌，但是包含了許多有關模型的有趣資訊。</span><span class="sxs-lookup"><span data-stu-id="399b0-200">The content of the NODE_DISTRIBUTION node in particular is nested, but contains much interesting information about the model.</span></span>  
  
 <span data-ttu-id="399b0-201">如需有關如何使用階層式資料列集的詳細資訊，請參閱 MSDN 上的 OLEDB 規格。</span><span class="sxs-lookup"><span data-stu-id="399b0-201">For more information about how to work with hierarchical rowsets, see the OLEDB specification on MSDN.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="399b0-202">另請參閱</span><span class="sxs-lookup"><span data-stu-id="399b0-202">See Also</span></span>  
 <span data-ttu-id="399b0-203">[瞭解 DMX Select 語句](/sql/dmx/understanding-the-dmx-select-statement) </span><span class="sxs-lookup"><span data-stu-id="399b0-203">[Understanding the DMX Select Statement](/sql/dmx/understanding-the-dmx-select-statement) </span></span>  
 [<span data-ttu-id="399b0-204">資料採礦查詢</span><span class="sxs-lookup"><span data-stu-id="399b0-204">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
