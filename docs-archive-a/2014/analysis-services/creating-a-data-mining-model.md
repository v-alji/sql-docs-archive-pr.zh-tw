---
title: 建立資料採礦模型 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining models, creating
- forecasting [data mining]
- mining models, creating
- clustering [data mining]
- association [data mining]
- data modeling [data mining]
- estimation
- classification [data mining]
ms.assetid: 804b7db3-1f6a-4f73-a81d-bbe02520d7c6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1e27739d3733c0b48dc6cff3e83e01f9cb12bce7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596946"
---
# <a name="creating-a-data-mining-model"></a><span data-ttu-id="eabf0-102">建立資料採礦模型</span><span class="sxs-lookup"><span data-stu-id="eabf0-102">Creating a Data Mining Model</span></span>
  <span data-ttu-id="eabf0-103">資料模型化是資料採礦的步驟，可讓您將*演算法*套用至資料，以建立模式和趨勢。</span><span class="sxs-lookup"><span data-stu-id="eabf0-103">Data modeling is the step of data mining where you build patterns and trends by applying *algorithms* to data.</span></span> <span data-ttu-id="eabf0-104">之後就可以使用這些模式進行分析，或進行預測。</span><span class="sxs-lookup"><span data-stu-id="eabf0-104">Later you can use those patterns for analysis, or to make predictions.</span></span>  
  
 <span data-ttu-id="eabf0-105">適用於 Office 的資料採礦增益集會透過精靈支援資料採礦，可讓您輕鬆建立模型。</span><span class="sxs-lookup"><span data-stu-id="eabf0-105">The Data Mining Add-ins for Office support data mining through wizards that make it easy to create models.</span></span> <span data-ttu-id="eabf0-106">精靈會分析資料、識別相互關聯性、計算所有變數的統計重要性，以及自動選取最佳模型。</span><span class="sxs-lookup"><span data-stu-id="eabf0-106">The wizards analyze the data, identify correlations, compute statistical significance of all variables, and automatically select the best model.</span></span>  
  
 <span data-ttu-id="eabf0-107">雖然這項功能與和所提供的資料採礦工具一樣強大，但結合了和 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 熟悉的 Excel 介面，讓您可以輕鬆地建立、修改和使用資料採礦。</span><span class="sxs-lookup"><span data-stu-id="eabf0-107">Although this functionality is every bit as powerful as the data mining tools provided by [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], the combination of wizards and the familiar Excel interface makes it easy to create, modify, and use data mining.</span></span>  
  
## <a name="advanced-data-mining"></a><span data-ttu-id="eabf0-108">進階 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="eabf0-108">Advanced (Data Mining)</span></span>  
 <span data-ttu-id="eabf0-109">「高級」程式可讓您使用中的其中一種資料採礦演算法，根據儲存在 Excel 中的資料，建立新的資料採礦模型 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="eabf0-109">The Advanced wizards let you create new data mining models, based on data stored in Excel, by using one of the data mining algorithms in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
### <a name="create-mining-structure"></a><span data-ttu-id="eabf0-110">建立採礦結構</span><span class="sxs-lookup"><span data-stu-id="eabf0-110">Create Mining Structure</span></span>  
 <span data-ttu-id="eabf0-111">建立採礦結構精靈會協助您建立新的資料採礦結構，此結構可當做多個採礦模型的基礎。</span><span class="sxs-lookup"><span data-stu-id="eabf0-111">The Create Mining Structure wizard helps you build a new data mining structure, which you can use as the basis for multiple mining models.</span></span> <span data-ttu-id="eabf0-112">此精靈提供選項讓您將資料的某部分擱置在一旁當做測試集使用，好讓您可以根據一致的測試標準來評估使用相同資料的所有模型。</span><span class="sxs-lookup"><span data-stu-id="eabf0-112">The wizard gives you the option to set aside a portion of the data to use as a testing set, so that you can evaluate all models that use the same data according to a consistent testing standard.</span></span>  
  
 [<span data-ttu-id="eabf0-113">建立 &#40;SQL Server 資料採礦增益集的採礦結構&#41;</span><span class="sxs-lookup"><span data-stu-id="eabf0-113">Create Mining Structure &#40;SQL Server Data Mining Add-ins&#41;</span></span>](create-mining-structure-sql-server-data-mining-add-ins.md)  
  
### <a name="add-model-to-structure"></a><span data-ttu-id="eabf0-114">將模型加入結構</span><span class="sxs-lookup"><span data-stu-id="eabf0-114">Add Model to Structure</span></span>  
 <span data-ttu-id="eabf0-115">將模型加入結構精靈讓您選擇現有的資料採礦結構，並為其建立新的資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="eabf0-115">The Add Model to Structure wizard lets you choose an existing data mining structure and create a new data mining model for it.</span></span> <span data-ttu-id="eabf0-116">您可以將多個採礦模型加入結構中，變更參數或選擇不同的資料採礦演算法及自訂輸出。</span><span class="sxs-lookup"><span data-stu-id="eabf0-116">You can add multiple mining models to a structure, changing the parameters or choosing different data mining algorithms, and customize the output.</span></span>  
  
 [<span data-ttu-id="eabf0-117">將模型加入結構 &#40;適用于 Excel 的資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="eabf0-117">Add Model to Structure &#40;Data Mining Add-ins for Excel&#41;</span></span>](add-model-to-structure-data-mining-add-ins-for-excel.md)  
  
## <a name="analyze-key-influencers-analyze"></a><span data-ttu-id="eabf0-118">分析關鍵影響因數 (分析)</span><span class="sxs-lookup"><span data-stu-id="eabf0-118">Analyze Key Influencers (Analyze)</span></span>  
 <span data-ttu-id="eabf0-119">您選擇感興趣的資料行或輸出值，然後演算法就會分析所有輸入資料以識別對目標有最大影響的因素。</span><span class="sxs-lookup"><span data-stu-id="eabf0-119">You choose a column or output value of interest, and then the algorithm analyzes all the input data to identify the factors that have the most influence on the target.</span></span> <span data-ttu-id="eabf0-120">或者，您可以建立會比較任何兩個值的報表，這樣就可以查看影響因數如何變更。</span><span class="sxs-lookup"><span data-stu-id="eabf0-120">Optionally, you can create a report that compares any two values, so that you can see how the influencers change.</span></span>  
  
 <span data-ttu-id="eabf0-121">[**分析關鍵影響**因數] 工具會使用 Microsoft 的簡單貝氏機率分類演算法。</span><span class="sxs-lookup"><span data-stu-id="eabf0-121">The **Analyze Key Influencers** tool uses the Microsoft Naïve Bayes algorithm.</span></span>  
  
 [<span data-ttu-id="eabf0-122">&#40;適用于 Excel 的資料表分析工具分析關鍵影響因數&#41;</span><span class="sxs-lookup"><span data-stu-id="eabf0-122">Analyze Key Influencers &#40;Table Analysis Tools for Excel&#41;</span></span>](analyze-key-influencers-table-analysis-tools-for-excel.md)  
  
## <a name="associate-data-mining"></a><span data-ttu-id="eabf0-123">關聯 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="eabf0-123">Associate (Data Mining)</span></span>  
 <span data-ttu-id="eabf0-124">[**關聯**] 嚮導會建立關聯模型，以偵測出現在多筆交易中之專案之間的關聯：例如，在購物籃分析中。</span><span class="sxs-lookup"><span data-stu-id="eabf0-124">The **Associate** wizard builds an association model that detects associations between items that appear in multiple transactions: for example, in market basket analysis.</span></span>  
  
 [<span data-ttu-id="eabf0-125">&#40;適用于 Excel&#41;的資料採礦用戶端相關聯的 Wizard</span><span class="sxs-lookup"><span data-stu-id="eabf0-125">Associate Wizard &#40;Data Mining Client for Excel&#41;</span></span>](associate-wizard-data-mining-client-for-excel.md)  
  
## <a name="classify-data-mining"></a><span data-ttu-id="eabf0-126">分類 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="eabf0-126">Classify (Data Mining)</span></span>  
 <span data-ttu-id="eabf0-127">**分類**嚮導會建立分類模型，以分析提供給目標結果的因素。</span><span class="sxs-lookup"><span data-stu-id="eabf0-127">The  **Classify** wizard builds a classification model that analyzes the factors that contributed to a target outcome.</span></span> <span data-ttu-id="eabf0-128">您可以搭配此精靈使用多種演算法，包括決策樹、貝氏機率分類與類神經網路。</span><span class="sxs-lookup"><span data-stu-id="eabf0-128">You can use multiple algorithms with this wizard, including Decision Trees, Naïve Bayes, and Neural Networks.</span></span>  
  
 [<span data-ttu-id="eabf0-129">適用于 Excel 的資料採礦增益集&#41;的分類嚮導 &#40;</span><span class="sxs-lookup"><span data-stu-id="eabf0-129">Classify Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](classify-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="cluster-data-mining"></a><span data-ttu-id="eabf0-130">叢集 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="eabf0-130">Cluster (Data Mining)</span></span>  
 <span data-ttu-id="eabf0-131">叢集**嚮導會**建立叢集模型，以偵測共用相似特性的資料列群組。</span><span class="sxs-lookup"><span data-stu-id="eabf0-131">The **Cluster** wizard builds a clustering model that detects groups of rows that share similar characteristics.</span></span> <span data-ttu-id="eabf0-132">叢集 (有時稱為「*分割*) 」是一種不受監督學習技術，在嘗試瞭解新資料中的模式和群組時非常有用。</span><span class="sxs-lookup"><span data-stu-id="eabf0-132">Clustering (sometimes called *segmentation*) is an unsupervised learning technique that is very useful when trying to understand patterns and groupings in new data.</span></span>  
  
 <span data-ttu-id="eabf0-133">Microsoft 叢集演算法支援數種 K-means 和 Expectation Maximization (EM) 叢集</span><span class="sxs-lookup"><span data-stu-id="eabf0-133">The Microsoft Clustering algorithm supports several varieties of both K-means and Expectation maximization (EM) clustering</span></span>  
  
 <span data-ttu-id="eabf0-134">[Cluster Wizard &#40;適用于 Excel&#41;的資料採礦增益集](cluster-wizard-data-mining-add-ins-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="eabf0-134">[Cluster Wizard &#40;Data Mining Add-ins for Excel&#41;](cluster-wizard-data-mining-add-ins-for-excel.md).</span></span>  
  
## <a name="detect-categories-analyze"></a><span data-ttu-id="eabf0-135">偵測類別目錄 (分析)</span><span class="sxs-lookup"><span data-stu-id="eabf0-135">Detect Categories (Analyze)</span></span>  
 <span data-ttu-id="eabf0-136">[偵測**類別目錄**] 工具可讓您新增任何資料集，並套用叢集以尋找資料的群組。</span><span class="sxs-lookup"><span data-stu-id="eabf0-136">The **Detect Categories** tool lets you add any data set and apply clustering to find groupings of data.</span></span> <span data-ttu-id="eabf0-137">這適用于尋找相似之處，以及建立群組以進一步分析。</span><span class="sxs-lookup"><span data-stu-id="eabf0-137">It's useful for finding similarities and for creating groups to further analyze.</span></span>  
  
 <span data-ttu-id="eabf0-138">[偵測**類別目錄**] 工具會使用 Microsoft 群集演算法。</span><span class="sxs-lookup"><span data-stu-id="eabf0-138">The **Detect Categories** tool uses the Microsoft Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="eabf0-139">偵測適用于 Excel&#41;&#40;資料表分析工具的分類</span><span class="sxs-lookup"><span data-stu-id="eabf0-139">Detect Categories &#40;Table Analysis Tools for Excel&#41;</span></span>](detect-categories-table-analysis-tools-for-excel.md)  
  
## <a name="estimate-data-mining"></a><span data-ttu-id="eabf0-140">估計 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="eabf0-140">Estimate (Data Mining)</span></span>  
 <span data-ttu-id="eabf0-141">[估計] 精靈會建立估計模型，該模型會擷取資料模式並使用樣式來預測連續的數字、日期或時間值。</span><span class="sxs-lookup"><span data-stu-id="eabf0-141">The Estimate wizard builds an estimation model that extracts data patterns and uses the patterns to predict continuous numeric, date, or time values.</span></span> <span data-ttu-id="eabf0-142">此精靈使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 決策樹演算法。</span><span class="sxs-lookup"><span data-stu-id="eabf0-142">It uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm.</span></span>  
  
 [<span data-ttu-id="eabf0-143">評估 Wizard &#40;適用于 Excel 的資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="eabf0-143">Estimate Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](estimate-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="fill-from-example-analyze"></a><span data-ttu-id="eabf0-144">根據範例填滿 (分析)</span><span class="sxs-lookup"><span data-stu-id="eabf0-144">Fill From Example (Analyze)</span></span>  
 <span data-ttu-id="eabf0-145">[**根據範例填滿**] 工具可協助您插補遺漏值。</span><span class="sxs-lookup"><span data-stu-id="eabf0-145">The **Fill From Example** tool helps you impute missing values.</span></span> <span data-ttu-id="eabf0-146">您要提供遺漏值應該會是什麼的一些範例，此工具就會依據資料表中的所有資料來建立模式，然後依據資料模式建議新的值。</span><span class="sxs-lookup"><span data-stu-id="eabf0-146">You provide some examples of what the missing values should be, and the tool builds patterns based on all data in the table, and then recommends new values based on patterns in the data.</span></span>  
  
 <span data-ttu-id="eabf0-147">[**根據範例填滿**] 工具會使用 Microsoft 羅吉斯回歸演算法。</span><span class="sxs-lookup"><span data-stu-id="eabf0-147">The **Fill From Example** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="eabf0-148">&#40;適用于 Excel 的資料表分析工具&#41;的範例填滿</span><span class="sxs-lookup"><span data-stu-id="eabf0-148">Fill From Example &#40;Table Analysis Tools for Excel&#41;</span></span>](fill-from-example-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-analyze"></a><span data-ttu-id="eabf0-149">預測 (分析)</span><span class="sxs-lookup"><span data-stu-id="eabf0-149">Forecast (Analyze)</span></span>  
 <span data-ttu-id="eabf0-150">「**預測**」工具會採用隨著時間而變更的資料，並預測未來的值。</span><span class="sxs-lookup"><span data-stu-id="eabf0-150">The **Forecast** tool takes data that changes over time, and predicts future values.</span></span>  
  
 <span data-ttu-id="eabf0-151">「**預測**」工具會使用 Microsoft 時間序列演算法。</span><span class="sxs-lookup"><span data-stu-id="eabf0-151">The **Forecast** tool uses the Microsoft Time Series algorithm.</span></span>  
  
 [<span data-ttu-id="eabf0-152">適用于 Excel&#41;的預測 &#40;資料表分析工具</span><span class="sxs-lookup"><span data-stu-id="eabf0-152">Forecast &#40;Table Analysis Tools for Excel&#41;</span></span>](forecast-table-analysis-tools-for-excel.md)  
  
## <a name="forecast-data-mining"></a><span data-ttu-id="eabf0-153">預測 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="eabf0-153">Forecast (Data Mining)</span></span>  
 <span data-ttu-id="eabf0-154">「**預測**」 wizard 會建立一個預測模型，它會偵測一系列資料格中的模式，然後再預測其他的值。</span><span class="sxs-lookup"><span data-stu-id="eabf0-154">The **Forecast** wizard builds a forecasting model that detects patterns in a series of cells, and then forecasts additional values.</span></span>  
  
 [<span data-ttu-id="eabf0-155">&#40;適用于 Excel 的資料採礦增益集&#41;的預測 Wizard</span><span class="sxs-lookup"><span data-stu-id="eabf0-155">Forecast Wizard &#40;Data Mining Add-ins for Excel&#41;</span></span>](forecast-wizard-data-mining-add-ins-for-excel.md)  
  
## <a name="highlight-exceptions-analyze"></a><span data-ttu-id="eabf0-156">反白顯示例外狀況 (分析)</span><span class="sxs-lookup"><span data-stu-id="eabf0-156">Highlight Exceptions (Analyze)</span></span>  
 <span data-ttu-id="eabf0-157">[**反白顯示例外**狀況] 工具會分析資料表中的模式，並尋找不符合模式的資料列和值。</span><span class="sxs-lookup"><span data-stu-id="eabf0-157">The **Highlight Exceptions** tool analyzes patterns in a table of data and finds rows and values that don't fit the pattern.</span></span> <span data-ttu-id="eabf0-158">接著您就可以檢閱這些值並加以更正，然後重新執行模型或標記這些值以供稍後採取動作。</span><span class="sxs-lookup"><span data-stu-id="eabf0-158">You can then review and correct them and rerun the model, or flag values for later action.</span></span>  
  
 <span data-ttu-id="eabf0-159">[**反白顯示例外**狀況] 工具會使用 Microsoft 群集演算法。</span><span class="sxs-lookup"><span data-stu-id="eabf0-159">The **Highlight Exceptions** tool uses the Microsoft Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="eabf0-160">反白顯示 &#40;適用于 Excel 的資料表分析工具的例外狀況&#41;</span><span class="sxs-lookup"><span data-stu-id="eabf0-160">Highlight Exceptions &#40;Table Analysis Tools for Excel&#41;</span></span>](highlight-exceptions-table-analysis-tools-for-excel.md)  
  
## <a name="prediction-calculator-analyze"></a><span data-ttu-id="eabf0-161">預測計算器 (分析)</span><span class="sxs-lookup"><span data-stu-id="eabf0-161">Prediction Calculator (Analyze)</span></span>  
 <span data-ttu-id="eabf0-162">此工具會建立模型以分析可導致目標結果的因數，並根據衍生自這些模式的準則來預測任何新輸入的結果。此外，它也會產生一個互動式決策工作表，讓您輕鬆地為新輸入計分。</span><span class="sxs-lookup"><span data-stu-id="eabf0-162">This tool creates a model that analyzes the factors leading to target outcomes, and then predicts a result for any new input, based on criteria derived from these patterns It also generates an interactive decision making worksheet that lets you easily score new inputs.</span></span> <span data-ttu-id="eabf0-163">您還可以建立計分工作表的列印版本，以供離線使用。</span><span class="sxs-lookup"><span data-stu-id="eabf0-163">You can also create a printed version of the scoring worksheet for offline use.</span></span>  
  
 <span data-ttu-id="eabf0-164">**預測計算器**工具會使用 Microsoft 羅吉斯回歸演算法。</span><span class="sxs-lookup"><span data-stu-id="eabf0-164">The **Prediction Calculator** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="eabf0-165">預測計算器 &#40;適用于 Excel 的資料表分析工具&#41;</span><span class="sxs-lookup"><span data-stu-id="eabf0-165">Prediction Calculator &#40;Table Analysis Tools for Excel&#41;</span></span>](prediction-calculator-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-goal-seek-analyze"></a><span data-ttu-id="eabf0-166">狀況：搜尋目標 (分析)</span><span class="sxs-lookup"><span data-stu-id="eabf0-166">Scenario: Goal Seek (Analyze)</span></span>  
 <span data-ttu-id="eabf0-167">在 [**搜尋目標**] 工具中，您可以指定目標值，而此工具會識別必須變更以符合該目標的基礎因數。</span><span class="sxs-lookup"><span data-stu-id="eabf0-167">In the **Goal Seek** tool, you specify a target value, and the tool identifies the underlying factors that must change to meet that target.</span></span> <span data-ttu-id="eabf0-168">例如，如果您知道必須增加通話滿意度 20%，就可以要求模型預測應該要變更才能達到目標的因數。</span><span class="sxs-lookup"><span data-stu-id="eabf0-168">For example, if you know that you must increase call satisfaction by 20%, you can ask the model to predict the factors that should change to produce that goal.</span></span>  
  
 <span data-ttu-id="eabf0-169">[**搜尋目標**] 工具使用 Microsoft 羅吉斯回歸演算法。</span><span class="sxs-lookup"><span data-stu-id="eabf0-169">The **Goal Seek** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 <span data-ttu-id="eabf0-170">詳細資料</span><span class="sxs-lookup"><span data-stu-id="eabf0-170">details</span></span>  
  
 [<span data-ttu-id="eabf0-171">&#40;適用于 Excel&#41;的資料表分析工具的目標搜尋案例</span><span class="sxs-lookup"><span data-stu-id="eabf0-171">Goal Seek Scenario &#40;Table Analysis Tools for Excel&#41;</span></span>](goal-seek-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="scenario-what-if-scenario-analyze"></a><span data-ttu-id="eabf0-172">狀況：假設狀況 (分析)</span><span class="sxs-lookup"><span data-stu-id="eabf0-172">Scenario: What-If Scenario (Analyze)</span></span>  
 <span data-ttu-id="eabf0-173">[**假設分析**] 工具會補充 [**搜尋目標**] 工具。</span><span class="sxs-lookup"><span data-stu-id="eabf0-173">The **What-If Analysis** tool complements the **Goal Seek** tool.</span></span> <span data-ttu-id="eabf0-174">使用此工具時，您要輸入您想要變更的值，模型就會預測該變更是否足以達到所要的結果。</span><span class="sxs-lookup"><span data-stu-id="eabf0-174">With this tool, you entered the value you want to change, and the model predicts whether that change will be sufficient to achieve the desired outcome.</span></span> <span data-ttu-id="eabf0-175">例如，您可以要求模型推測若額外增加一個話務員是否能將客戶滿意度提高一個積分點。</span><span class="sxs-lookup"><span data-stu-id="eabf0-175">For example, you might ask the model to infer whether adding one extra call operator would increase customer satisfaction by one point.</span></span>  
  
 <span data-ttu-id="eabf0-176">**假設**工具會使用 Microsoft 羅吉斯回歸演算法。</span><span class="sxs-lookup"><span data-stu-id="eabf0-176">The **What-If** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="eabf0-177">適用于 Excel 的資料表分析工具 &#40;假設案例&#41;</span><span class="sxs-lookup"><span data-stu-id="eabf0-177">What-If Scenario &#40;Table Analysis Tools for Excel&#41;</span></span>](what-if-scenario-table-analysis-tools-for-excel.md)  
  
## <a name="shopping-basket-analysis-analyze"></a><span data-ttu-id="eabf0-178">購物籃分析 (分析)</span><span class="sxs-lookup"><span data-stu-id="eabf0-178">Shopping Basket Analysis (Analyze)</span></span>  
 <span data-ttu-id="eabf0-179">[**購物籃分析**] 工具會建立經常一起購買的產品群組，以識別可用於交叉銷售或向上銷售的模式。</span><span class="sxs-lookup"><span data-stu-id="eabf0-179">The **Shopping Basket Analysis** tool creates groups of products that are frequently purchased together, to identify patterns that can be used in cross-selling or up-selling.</span></span> <span data-ttu-id="eabf0-180">它也會根據相關產品組合的價格和成本來產生報表，以輔助您做決策。</span><span class="sxs-lookup"><span data-stu-id="eabf0-180">It also generates reports based on the price and cost of related product bundles, to aid in decision-making.</span></span>  
  
 <span data-ttu-id="eabf0-181">您也可以將此工具用於經常一起發生的事件、會導致診斷的因素，或任何其他可能的原因集和結果集。</span><span class="sxs-lookup"><span data-stu-id="eabf0-181">You can also use this tool for events that frequently occur together, factors leading to a diagnosis, or any other set of potential causes and outcomes.</span></span>  
  
 <span data-ttu-id="eabf0-182">[**購物籃分析**] 工具使用 Microsoft 關聯演算法。</span><span class="sxs-lookup"><span data-stu-id="eabf0-182">The **Shopping Basket Analysis** tool uses the Microsoft Association algorithm.</span></span>  
  
 [<span data-ttu-id="eabf0-183">適用于 Excel&#41;的購物籃分析 &#40;資料表 AnalysisTools</span><span class="sxs-lookup"><span data-stu-id="eabf0-183">Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;</span></span>](shopping-basket-analysis-table-analysistools-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="eabf0-184">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eabf0-184">See Also</span></span>  
 <span data-ttu-id="eabf0-185">[探索和清除資料](exploring-and-cleaning-data.md) </span><span class="sxs-lookup"><span data-stu-id="eabf0-185">[Exploring and Cleaning Data](exploring-and-cleaning-data.md) </span></span>  
 <span data-ttu-id="eabf0-186">[驗證模型及使用模型進行預測 &#40;適用于 Excel 的資料採礦增益集&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="eabf0-186">[Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md) </span></span>  
 [<span data-ttu-id="eabf0-187">&#40;適用于 Excel 的資料採礦增益集部署和調整採礦模型&#41;</span><span class="sxs-lookup"><span data-stu-id="eabf0-187">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
