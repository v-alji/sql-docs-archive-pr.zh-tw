---
title: 適用于 Excel 的資料表分析工具 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- getting started
ms.assetid: 6d9d1481-18e4-4108-9efa-68152b0940c9
author: minewiskan
ms.author: owend
ms.openlocfilehash: e566f5213f1ecd98685a3199c57b962be96c5aa7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705449"
---
# <a name="table-analysis-tools-for-excel"></a><span data-ttu-id="33218-102">適用於 Excel 的資料表分析工具</span><span class="sxs-lookup"><span data-stu-id="33218-102">Table Analysis Tools for Excel</span></span>
  <span data-ttu-id="33218-103">[**分析**] 工具列中的資料採礦工具是開始使用資料採礦的最簡單方式。</span><span class="sxs-lookup"><span data-stu-id="33218-103">The data mining tools in the **Analyze** toolbar are the easiest way to get started with data mining.</span></span> <span data-ttu-id="33218-104">每個工具都會自動分析資料的散發和類型，並設定參數以確保結果是有效的。</span><span class="sxs-lookup"><span data-stu-id="33218-104">Each tool automatically analyzes the distribution and type of your data, and sets the parameters to ensure that results are valid.</span></span> <span data-ttu-id="33218-105">您不需選取演算法或設定複雜參數。</span><span class="sxs-lookup"><span data-stu-id="33218-105">You do not have to select an algorithm or configure complex parameters.</span></span>  
  
 <span data-ttu-id="33218-106">![DM](media/dm-tabletoolsanalyze.gif "DM")</span><span class="sxs-lookup"><span data-stu-id="33218-106">![DM](media/dm-tabletoolsanalyze.gif "DM")</span></span>  
  
 <span data-ttu-id="33218-107">[**分析**] 功能區包含下列工具：</span><span class="sxs-lookup"><span data-stu-id="33218-107">The **Analyze** ribbon includes the following tools:</span></span>  
  
 [<span data-ttu-id="33218-108">&#40;適用于 Excel 的資料表分析工具分析關鍵影響因數&#41;</span><span class="sxs-lookup"><span data-stu-id="33218-108">Analyze Key Influencers &#40;Table Analysis Tools for Excel&#41;</span></span>](analyze-key-influencers-table-analysis-tools-for-excel.md)  
 <span data-ttu-id="33218-109">您選擇感興趣的資料行或輸出值，然後演算法就會分析所有輸入資料以識別對目標有最大影響的因素。</span><span class="sxs-lookup"><span data-stu-id="33218-109">You choose a column or output value of interest, and then the algorithm analyzes all the input data to identify the factors that have the most influence on the target.</span></span> <span data-ttu-id="33218-110">或者，您可以建立會比較任何兩個值的報表，這樣就可以查看影響因數如何變更。</span><span class="sxs-lookup"><span data-stu-id="33218-110">Optionally, you can create a report that compares any two values, so that you can see how the influencers change.</span></span>  
  
 <span data-ttu-id="33218-111">[**分析關鍵影響**因數] 工具會使用 Microsoft 的簡單貝氏機率分類演算法。</span><span class="sxs-lookup"><span data-stu-id="33218-111">The **Analyze Key Influencers** tool uses the Microsoft Naïve Bayes algorithm.</span></span>  
  
 [<span data-ttu-id="33218-112">偵測適用于 Excel&#41;&#40;資料表分析工具的分類</span><span class="sxs-lookup"><span data-stu-id="33218-112">Detect Categories &#40;Table Analysis Tools for Excel&#41;</span></span>](detect-categories-table-analysis-tools-for-excel.md)  
 <span data-ttu-id="33218-113">此工具可讓您新增任何資料集和套用叢集以尋找資料的群組。</span><span class="sxs-lookup"><span data-stu-id="33218-113">This tool lets you add any data set and apply clustering to find groupings of data.</span></span> <span data-ttu-id="33218-114">這適用于尋找相似之處，以及建立群組以進一步分析。</span><span class="sxs-lookup"><span data-stu-id="33218-114">It's useful for finding similarities and for creating groups to further analyze.</span></span>  
  
 <span data-ttu-id="33218-115">[偵測**類別目錄**] 工具會使用 Microsoft 群集演算法。</span><span class="sxs-lookup"><span data-stu-id="33218-115">The **Detect Categories** tool uses the Microsoft Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="33218-116">&#40;適用于 Excel 的資料表分析工具&#41;的範例填滿</span><span class="sxs-lookup"><span data-stu-id="33218-116">Fill From Example &#40;Table Analysis Tools for Excel&#41;</span></span>](fill-from-example-table-analysis-tools-for-excel.md)  
 <span data-ttu-id="33218-117">此工具會協助您推算遺漏值。</span><span class="sxs-lookup"><span data-stu-id="33218-117">This tool helps you impute missing values.</span></span> <span data-ttu-id="33218-118">您要提供遺漏值應該會是什麼的一些範例，此工具就會依據資料表中的所有資料來建立模式，然後依據資料模式建議新的值。</span><span class="sxs-lookup"><span data-stu-id="33218-118">You provide some examples of what the missing values should be, and the tool builds patterns based on all data in the table, and then recommends new values based on patterns in the data.</span></span>  
  
 <span data-ttu-id="33218-119">[**根據範例填滿**] 工具會使用 Microsoft 羅吉斯回歸演算法。</span><span class="sxs-lookup"><span data-stu-id="33218-119">The **Fill From Example** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="33218-120">適用于 Excel&#41;的預測 &#40;資料表分析工具</span><span class="sxs-lookup"><span data-stu-id="33218-120">Forecast &#40;Table Analysis Tools for Excel&#41;</span></span>](forecast-table-analysis-tools-for-excel.md)  
 <span data-ttu-id="33218-121">此工具會採用隨著時間而變更的資料，然後預測未來值。</span><span class="sxs-lookup"><span data-stu-id="33218-121">This tool takes data that changes over time, and predicts future values.</span></span>  
  
 <span data-ttu-id="33218-122">「**預測**」工具會使用 Microsoft 時間序列演算法。</span><span class="sxs-lookup"><span data-stu-id="33218-122">The **Forecast** tool uses the Microsoft Time Series algorithm.</span></span>  
  
 [<span data-ttu-id="33218-123">反白顯示 &#40;適用于 Excel 的資料表分析工具的例外狀況&#41;</span><span class="sxs-lookup"><span data-stu-id="33218-123">Highlight Exceptions &#40;Table Analysis Tools for Excel&#41;</span></span>](highlight-exceptions-table-analysis-tools-for-excel.md)  
 <span data-ttu-id="33218-124">這項工具會分析資料表中的模式，並尋找不符合模式的資料列和值。</span><span class="sxs-lookup"><span data-stu-id="33218-124">This tool analyzes patterns in a table of data and finds rows and values that don't fit the pattern.</span></span> <span data-ttu-id="33218-125">接著您就可以檢閱這些值並加以更正，然後重新執行模型或標記這些值以供稍後採取動作。</span><span class="sxs-lookup"><span data-stu-id="33218-125">You can then review and correct them and rerun the model, or flag values for later action.</span></span>  
  
 <span data-ttu-id="33218-126">[**反白顯示例外**狀況] 工具會使用 Microsoft 群集演算法。</span><span class="sxs-lookup"><span data-stu-id="33218-126">The **Highlight Exceptions** tool uses the Microsoft Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="33218-127">&#40;適用于 Excel&#41;的資料表分析工具的目標搜尋案例</span><span class="sxs-lookup"><span data-stu-id="33218-127">Goal Seek Scenario &#40;Table Analysis Tools for Excel&#41;</span></span>](goal-seek-scenario-table-analysis-tools-for-excel.md)  
 <span data-ttu-id="33218-128">在 [**搜尋目標**] 工具中，您可以指定目標值，而此工具會識別必須變更以符合該目標的基礎因數。</span><span class="sxs-lookup"><span data-stu-id="33218-128">In the **Goal Seek** tool, you specify a target value, and the tool identifies the underlying factors that must change to meet that target.</span></span> <span data-ttu-id="33218-129">例如，如果您知道必須增加通話滿意度 20%，就可以要求模型預測應該要變更才能達到目標的因數。</span><span class="sxs-lookup"><span data-stu-id="33218-129">For example, if you know that you must increase call satisfaction by 20%, you can ask the model to predict the factors that should change to produce that goal.</span></span>  
  
 <span data-ttu-id="33218-130">[**搜尋目標**] 工具使用 Microsoft 羅吉斯回歸演算法。</span><span class="sxs-lookup"><span data-stu-id="33218-130">The **Goal Seek** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="33218-131">適用于 Excel 的資料表分析工具 &#40;假設案例&#41;</span><span class="sxs-lookup"><span data-stu-id="33218-131">What-If Scenario &#40;Table Analysis Tools for Excel&#41;</span></span>](what-if-scenario-table-analysis-tools-for-excel.md)  
 <span data-ttu-id="33218-132">[**假設分析**] 工具會補充 [**搜尋目標**] 工具。</span><span class="sxs-lookup"><span data-stu-id="33218-132">The **What-If Analysis** tool complements the **Goal Seek** tool.</span></span> <span data-ttu-id="33218-133">使用此工具時，您要輸入您想要變更的值，模型就會預測該變更是否足以達到所要的結果。</span><span class="sxs-lookup"><span data-stu-id="33218-133">With this tool, you entered the value you want to change, and the model predicts whether that change will be sufficient to achieve the desired outcome.</span></span> <span data-ttu-id="33218-134">例如，您可以要求模型推測若額外增加一個話務員是否能將客戶滿意度提高一個積分點。</span><span class="sxs-lookup"><span data-stu-id="33218-134">For example, you might ask the model to infer whether adding one extra call operator would increase customer satisfaction by one point.</span></span>  
  
 <span data-ttu-id="33218-135">**假設**工具會使用 Microsoft 羅吉斯回歸演算法。</span><span class="sxs-lookup"><span data-stu-id="33218-135">The **What-If** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="33218-136">預測計算器 &#40;適用于 Excel 的資料表分析工具&#41;</span><span class="sxs-lookup"><span data-stu-id="33218-136">Prediction Calculator &#40;Table Analysis Tools for Excel&#41;</span></span>](prediction-calculator-table-analysis-tools-for-excel.md)  
 <span data-ttu-id="33218-137">這個工具會建立模型，用於分析產生目標結果的因數，然後根據從資料衍生的計分規則預測任何新輸入的結果。</span><span class="sxs-lookup"><span data-stu-id="33218-137">This tool creates a model that analyzes the factors leading to the target outcome, and then predicts a result for any new inputs, based on scoring rules derived from the data.</span></span> <span data-ttu-id="33218-138">這個工具也會產生互動式決策工作表，讓您輕鬆為新輸入計分。</span><span class="sxs-lookup"><span data-stu-id="33218-138">This tool also generates an interactive decision-making worksheet that lets you easily score new inputs.</span></span> <span data-ttu-id="33218-139">您還可以建立計分工作表的列印版本，以供離線使用。</span><span class="sxs-lookup"><span data-stu-id="33218-139">You can also create a printed version of the scoring worksheet for offline use.</span></span>  
  
 <span data-ttu-id="33218-140">**預測計算器**工具會使用 Microsoft 羅吉斯回歸演算法。</span><span class="sxs-lookup"><span data-stu-id="33218-140">The **Prediction Calculator** tool uses the Microsoft Logistic Regression algorithm.</span></span>  
  
 [<span data-ttu-id="33218-141">適用于 Excel&#41;的購物籃分析 &#40;資料表 AnalysisTools</span><span class="sxs-lookup"><span data-stu-id="33218-141">Shopping Basket Analysis &#40;Table AnalysisTools for Excel&#41;</span></span>](shopping-basket-analysis-table-analysistools-for-excel.md)  
 <span data-ttu-id="33218-142">這個工具會識別可用於交叉銷售或向上銷售的模式。</span><span class="sxs-lookup"><span data-stu-id="33218-142">This tool identifies patterns that can be used in cross-selling or up-selling.</span></span> <span data-ttu-id="33218-143">它會識別經常一起購買的產品群組，也會根據相關產品組合的價格和成本來產生報表，以輔助您做決策。</span><span class="sxs-lookup"><span data-stu-id="33218-143">It identifies groups of products that are frequently purchased together, and also generates reports based on the price and cost of related product bundles, to aid in decision-making.</span></span>  
  
 <span data-ttu-id="33218-144">這項工具不限於購物籃分析；您可以將它套用到任何有助於關聯分析的問題。</span><span class="sxs-lookup"><span data-stu-id="33218-144">The tool is not limited to market basket analysis; you can apply it to any problem that lends itself to association analysis.</span></span> <span data-ttu-id="33218-145">例如，您可以查看經常一起發生的事件、會導致診斷的因素，或任何其他可能的原因集和結果集。</span><span class="sxs-lookup"><span data-stu-id="33218-145">For example, you might look for events that frequently occur together, factors leading to a diagnosis, or any other set of potential causes and outcomes.</span></span>  
  
 <span data-ttu-id="33218-146">[**購物籃分析**] 工具使用 Microsoft 關聯演算法。</span><span class="sxs-lookup"><span data-stu-id="33218-146">The **Shopping Basket Analysis** tool uses the Microsoft Association algorithm.</span></span>  
  
## <a name="requirements-for-the-table-analysis-tools-for-excel"></a><span data-ttu-id="33218-147">適用於 Excel 的資料表分析工具的需求</span><span class="sxs-lookup"><span data-stu-id="33218-147">Requirements for the Table Analysis Tools for Excel</span></span>  
 <span data-ttu-id="33218-148">若要使用適用於 Excel 的資料表分析工具，您必須先建立與 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體的連接。</span><span class="sxs-lookup"><span data-stu-id="33218-148">To use the Table Analysis Tools for Excel, you must first create a connection to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="33218-149">此連接可讓您存取分析資料時所用的 Microsoft 資料採礦演算法。</span><span class="sxs-lookup"><span data-stu-id="33218-149">This connection gives you access to the Microsoft data mining algorithms that are used to analyze your data.</span></span> <span data-ttu-id="33218-150">如果您無法存取執行個體，建議您請系統管理員設定一個執行個體，讓您能夠用於實驗資料採礦。</span><span class="sxs-lookup"><span data-stu-id="33218-150">If you do not have access to an instance, we recommend that you ask your administrator to set up an instance that you can use for experimenting with data mining.</span></span> <span data-ttu-id="33218-151">如需詳細資訊，請參閱[連接到來源資料 &#40;適用于 Excel&#41;的資料採礦用戶端](connect-to-source-data-data-mining-client-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="33218-151">For more information, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="33218-152">若要使用資料表分析工具來處理資料，您必須將您要使用的資料範圍轉換成 Excel 資料表。</span><span class="sxs-lookup"><span data-stu-id="33218-152">To work with data using the Table Analysis Tools, you must convert the range of data you want to use to Excel tables.</span></span>  
  
 <span data-ttu-id="33218-153">如果您看不到 [**分析**] 功能區，請嘗試先在資料表中按一下。</span><span class="sxs-lookup"><span data-stu-id="33218-153">If you cannot see the **Analyze** ribbon, try clicking inside a data table first.</span></span> <span data-ttu-id="33218-154">此功能表要等到選取了資料表之後才會啟動。</span><span class="sxs-lookup"><span data-stu-id="33218-154">The menu is not activated until a data table is selected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33218-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33218-155">See Also</span></span>  
 <span data-ttu-id="33218-156">[適用于 Excel &#40;SQL Server 資料採礦增益集的資料採礦用戶端&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="33218-156">[Data Mining Client for Excel &#40;SQL Server Data Mining Add-ins&#41;](data-mining-client-for-excel-sql-server-data-mining-add-ins.md) </span></span>  
 <span data-ttu-id="33218-157">[針對 Visio 資料採礦圖表進行疑難排解 &#40;SQL Server 資料採礦增益集&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md) </span><span class="sxs-lookup"><span data-stu-id="33218-157">[Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md) </span></span>  
 [<span data-ttu-id="33218-158">適用於 Office 的資料採礦增益集包含的內容</span><span class="sxs-lookup"><span data-stu-id="33218-158">What's Included in the Data Mining Add-Ins for Office</span></span>](what-s-included-in-the-data-mining-add-ins-for-office.md)  
  
  
