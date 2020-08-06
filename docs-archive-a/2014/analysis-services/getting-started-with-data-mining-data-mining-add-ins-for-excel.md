---
title: 適用于 Excel 的資料採礦 (資料採礦增益集的消費者入門) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: cbe10a19-e194-408e-a65b-5fdf3fb1e880
author: minewiskan
ms.author: owend
ms.openlocfilehash: 066fc72fa0570d56376cc73478a68e42d20ffbc4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592969"
---
# <a name="getting-started-with-data-mining-data-mining-add-ins-for-excel"></a><span data-ttu-id="80e65-102">開始使用資料採礦 (適用於 Excel 的資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="80e65-102">Getting Started with Data Mining (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="80e65-103">資料採礦是探索有意義資料模式的程序。</span><span class="sxs-lookup"><span data-stu-id="80e65-103">Data mining is the process of discovering meaningful patterns in data.</span></span> <span data-ttu-id="80e65-104">資料採礦自然補充了透過傳統 BI 瀏覽及了解資料的程序。</span><span class="sxs-lookup"><span data-stu-id="80e65-104">Data mining is a natural complement to the process of exploring and understanding your data through traditional BI.</span></span> <span data-ttu-id="80e65-105">機器演算法可以處理非常大量的資料，並且找出原本隱藏的模式和趨勢。</span><span class="sxs-lookup"><span data-stu-id="80e65-105">Machine algorithms can process very large amounts of data and discover patterns and trends that would otherwise be hidden.</span></span>  
  
 <span data-ttu-id="80e65-106">若要進行資料採礦，您可以收集與特定問題相關的資料，例如「我的客戶是誰？」</span><span class="sxs-lookup"><span data-stu-id="80e65-106">To do data mining, you collect data that is relevant to a specific question, such as "Who are my customers?"</span></span> <span data-ttu-id="80e65-107">或是「購買了哪些產品？」</span><span class="sxs-lookup"><span data-stu-id="80e65-107">or "what products were purchased?"</span></span> <span data-ttu-id="80e65-108">然後套用演算法來尋找資料中的統計相互關聯。</span><span class="sxs-lookup"><span data-stu-id="80e65-108">and then apply an algorithm to find statistical correlations in the data.</span></span> <span data-ttu-id="80e65-109">透過分析找到的模式和趨勢會儲存為採礦模型。</span><span class="sxs-lookup"><span data-stu-id="80e65-109">The patterns and trends found through analysis are stored as a mining model.</span></span> <span data-ttu-id="80e65-110">您可以接著將採礦模型套用至新資料，以便在下列商務案例中進行分析：</span><span class="sxs-lookup"><span data-stu-id="80e65-110">You can then apply the mining model to new data, in business scenarios such as these:</span></span>  
  
-   <span data-ttu-id="80e65-111">使用過去的趨勢預測下一季的銷售、存貨需求或客戶滿意度。</span><span class="sxs-lookup"><span data-stu-id="80e65-111">Use past trends to forecast sales for the next quarter, inventory requirements, or customer satisfaction.</span></span>  
  
-   <span data-ttu-id="80e65-112">套用目前客戶的知識來分析新客戶並建議新產品或機會。</span><span class="sxs-lookup"><span data-stu-id="80e65-112">Apply knowledge of current customers to profile new customers and recommend new products or opportunities.</span></span>  
  
-   <span data-ttu-id="80e65-113">尋找過去事件之間的相互關聯，以預測伺服器失敗或停機時間。</span><span class="sxs-lookup"><span data-stu-id="80e65-113">Find correlations among past events to predict server failures or downtime.</span></span>  
  
-   <span data-ttu-id="80e65-114">分析客戶一起購買的產品，並使用這項資訊建議搭售或規劃產品位置。</span><span class="sxs-lookup"><span data-stu-id="80e65-114">Analyze which products customers purchase together and use the information to recommend bundles or plan product placement.</span></span>  
  
 <span data-ttu-id="80e65-115">您選擇的分析方法取決於您的目標。</span><span class="sxs-lookup"><span data-stu-id="80e65-115">The method of analysis you choose depends on your goals.</span></span> <span data-ttu-id="80e65-116">資料採礦增益集支援下列分析類型：</span><span class="sxs-lookup"><span data-stu-id="80e65-116">The Data Mining Add-ins support these types of analysis:</span></span>  
  
-   <span data-ttu-id="80e65-117">有人監督和無人監督的學習</span><span class="sxs-lookup"><span data-stu-id="80e65-117">Supervised and unsupervised learning</span></span>  
  
-   <span data-ttu-id="80e65-118">叢集 (分割)</span><span class="sxs-lookup"><span data-stu-id="80e65-118">Clustering (segmentation)</span></span>  
  
-   <span data-ttu-id="80e65-119">因數分析，使用 Bayesian 與類神經網路</span><span class="sxs-lookup"><span data-stu-id="80e65-119">Factor analysis, using Bayesian and neural networks</span></span>  
  
-   <span data-ttu-id="80e65-120">時間序列分析</span><span class="sxs-lookup"><span data-stu-id="80e65-120">Time series analysis</span></span>  
  
-   <span data-ttu-id="80e65-121">關聯分析、建議和購物籃分析</span><span class="sxs-lookup"><span data-stu-id="80e65-121">Association analysis, recommendations, and shopping basket analysis</span></span>  
  
-   <span data-ttu-id="80e65-122">計分二進位結果</span><span class="sxs-lookup"><span data-stu-id="80e65-122">Scoring binary outcomes</span></span>  
  
-   <span data-ttu-id="80e65-123">線性迴歸</span><span class="sxs-lookup"><span data-stu-id="80e65-123">Linear regression</span></span>  
  
 <span data-ttu-id="80e65-124">此外，增益集還會在資料準備階段提供協助：資料選取、瀏覽和資料清理。</span><span class="sxs-lookup"><span data-stu-id="80e65-124">In addition, the add-ins provide help the data preparation phase: data selection, exploration, and data cleansing.</span></span>  
  
## <a name="define-your-goal"></a><span data-ttu-id="80e65-125">定義您的目標</span><span class="sxs-lookup"><span data-stu-id="80e65-125">Define Your Goal</span></span>  
 <span data-ttu-id="80e65-126">開始之前，請先花點時間考量您實際想要解答的問題。</span><span class="sxs-lookup"><span data-stu-id="80e65-126">Before you get started, take a minute to consider the question you really want to answer.</span></span> <span data-ttu-id="80e65-127">雖然瀏覽本身很容易理解，但是，如果您要將自己的數據套用至新資料，就應該要能夠清楚陳述您預期模型產生的結果，以及您測量模型是否達成目標的方式。</span><span class="sxs-lookup"><span data-stu-id="80e65-127">Exploration for its own sake is illuminating, but if you want to apply your findings to new data, you should be able to state clearly what you expect the model to produce, and how you will measure whether the model accomplishes your goals.</span></span>  
  
 <span data-ttu-id="80e65-128">例如，不是「尋找新客戶」的目標，而是以更具體的方式來闡明您的目標，例如「識別可能購買產品的客戶人口統計，其機率至少為65%」。</span><span class="sxs-lookup"><span data-stu-id="80e65-128">For example, rather than a goal of "finding new customers", clarify your objective to something more concrete, such as "identify the demographics of customers that are likely to buy our product, with a probability of at least 65%".</span></span>  
  
-   <span data-ttu-id="80e65-129">您的資料集至少應該包含一個可用於定型和預測的「結果」屬性。</span><span class="sxs-lookup"><span data-stu-id="80e65-129">Your dataset should contain at least one "result" attribute that you can use for training and prediction.</span></span> <span data-ttu-id="80e65-130">如果沒有這類屬性，您可以手動標記一些定型資料，或使用其他資料行建立結果的 Proxy。</span><span class="sxs-lookup"><span data-stu-id="80e65-130">If there is no such attribute, you can manually label some training data, or use other columns to create a proxy for the outcome.</span></span>  
  
     <span data-ttu-id="80e65-131">例如，如果您想要預測「最佳潛在客戶」，您應該事先套用某個商務規則以標示現有的客戶，讓資料採礦可以從您提供的範例中學習。</span><span class="sxs-lookup"><span data-stu-id="80e65-131">For example, if you want to predict "the best prospects", you should apply some business rule beforehand to label existing customers, so that data mining can learn from the examples you provide.</span></span>  
  
-   <span data-ttu-id="80e65-132">如果您要使用隨時間變更的值，而且想要預測未來的趨勢，請考慮所需結果的資料粒度。</span><span class="sxs-lookup"><span data-stu-id="80e65-132">If you are working with a value that changes over time, and want to predict future trends, think about the granularity of the results you need.</span></span> <span data-ttu-id="80e65-133">您想要每個月、每天還是每年預測一次？</span><span class="sxs-lookup"><span data-stu-id="80e65-133">Do you want predictions for a month, day, or yearly basis?</span></span> <span data-ttu-id="80e65-134">分析資料所使用的單位必須與預測所使用的單位相同。</span><span class="sxs-lookup"><span data-stu-id="80e65-134">Your data has to be analyzed using the same units that you want to predict.</span></span>  
  
     <span data-ttu-id="80e65-135">使用迴圈模式時，如果您沒有每日資料的良好結果，請嘗試不同的時間配量，或嘗試使用周日、月或甚至假日。</span><span class="sxs-lookup"><span data-stu-id="80e65-135">With cyclical patterns, if you don't get good results with daily data, try different time slices, or try using week days, months, or even holidays.</span></span>  
  
-   <span data-ttu-id="80e65-136">在您啟動精靈尋找資料中新的相互關聯之前，請再看一眼您的資料，並考慮哪種現有的關聯性可能會出現在資料集中。</span><span class="sxs-lookup"><span data-stu-id="80e65-136">Before you launch a wizard to find new correlations in your data, take one more look at your data and consider what sort of existing relationships might be present in the dataset.</span></span> <span data-ttu-id="80e65-137">是否有混淆的變數？</span><span class="sxs-lookup"><span data-stu-id="80e65-137">Are there confounding variables?</span></span> <span data-ttu-id="80e65-138">是否有重複或取代項目？</span><span class="sxs-lookup"><span data-stu-id="80e65-138">Are there duplicates or proxies?</span></span>  
  
-   <span data-ttu-id="80e65-139">將會評估模型成功的計量為何？</span><span class="sxs-lookup"><span data-stu-id="80e65-139">What are the metrics by which the model's success will be evaluated?</span></span> <span data-ttu-id="80e65-140">您如何知道模型「夠好」了？</span><span class="sxs-lookup"><span data-stu-id="80e65-140">How will you know that the model is "good enough"?</span></span>  
  
-   <span data-ttu-id="80e65-141">您要從資料採礦模型建立預測，或是只尋找有趣的模式和關聯？</span><span class="sxs-lookup"><span data-stu-id="80e65-141">Do you want to make predictions from the data mining model or just look for interesting patterns and associations?</span></span>  
  
## <a name="explore-your-data-and-explore-the-model"></a><span data-ttu-id="80e65-142">瀏覽資料及瀏覽模型</span><span class="sxs-lookup"><span data-stu-id="80e65-142">Explore Your Data and Explore the Model</span></span>  
 <span data-ttu-id="80e65-143">您可能已經徹底了解資料和網域。</span><span class="sxs-lookup"><span data-stu-id="80e65-143">Perhaps you already thoroughly understand the data and the domain.</span></span> <span data-ttu-id="80e65-144">即使您已徹底了解，仍建議您花一些時間從模型的角度來分析您的資料。</span><span class="sxs-lookup"><span data-stu-id="80e65-144">Even if you do, you should take some time to profile your data with modeling in mind.</span></span>  
  
 <span data-ttu-id="80e65-145">花點時間檢視值的分佈情形，並找出可能的問題，例如遺漏值或預留位置。</span><span class="sxs-lookup"><span data-stu-id="80e65-145">Take a minute to view the distribution of values, and identify potential problems such as missing values or placeholders.</span></span>  
  
 <span data-ttu-id="80e65-146">如果您打算對資料集執行資料採礦，而這是因為您無法使用其他方法來分析，請考慮取樣或減少資料。</span><span class="sxs-lookup"><span data-stu-id="80e65-146">If you are planning to perform data mining against a data set that was so large or complex that you couldn't analyze it with other methods, consider sampling or data reduction.</span></span>  
  
-   <span data-ttu-id="80e65-147">資料如何分佈？</span><span class="sxs-lookup"><span data-stu-id="80e65-147">How is the data distributed?</span></span>  
  
-   <span data-ttu-id="80e65-148">資料行之間如何相關，或是如果有多個資料表，資料表之間如何相關？</span><span class="sxs-lookup"><span data-stu-id="80e65-148">How are the columns related, or if there are multiple tables, how are the tables related?</span></span>  
  
-   <span data-ttu-id="80e65-149">是否遺漏任何值？</span><span class="sxs-lookup"><span data-stu-id="80e65-149">Are any values missing?</span></span> <span data-ttu-id="80e65-150">是否有需要轉換或前置處理的值？</span><span class="sxs-lookup"><span data-stu-id="80e65-150">Are there values that need conversion or preprocessing?</span></span>  
  
-   <span data-ttu-id="80e65-151">資料主要為文字、數字或兩者混合？</span><span class="sxs-lookup"><span data-stu-id="80e65-151">Is the data mostly text, mostly numbers, or a mix?</span></span>  
  
-   <span data-ttu-id="80e65-152">您是否有足夠的資料來支援目標結果的分析？</span><span class="sxs-lookup"><span data-stu-id="80e65-152">Do you have enough data to support analysis of the targeted outcomes?</span></span> <span data-ttu-id="80e65-153">如果您要分析不同產品之間的關聯，可能需要更多資料。</span><span class="sxs-lookup"><span data-stu-id="80e65-153">If you are analyzing associations among products, you might need lots more data.</span></span> <span data-ttu-id="80e65-154">如果您要預測二進位結果，您可以使用較少的資料來完成 (假設資料集是對稱的)。</span><span class="sxs-lookup"><span data-stu-id="80e65-154">If you are predicting a binary outcome, you can get by with much less, assuming the dataset is balanced.</span></span>  
  
 <span data-ttu-id="80e65-155">模型完成後，請花一些時間檢閱結果，並找出方式修正資料或取得更理想的結果。</span><span class="sxs-lookup"><span data-stu-id="80e65-155">After your model is complete, take some time to review the results and identify ways to amend the data or get better results.</span></span> <span data-ttu-id="80e65-156">您的第一個模型鮮少會提供所有答案。</span><span class="sxs-lookup"><span data-stu-id="80e65-156">It is exceedingly rare that your first model provides all the answers.</span></span> <span data-ttu-id="80e65-157">資料採礦通常是反覆進行的程序。</span><span class="sxs-lookup"><span data-stu-id="80e65-157">Data mining is typically an iterative process.</span></span>  
  
 <span data-ttu-id="80e65-158">當您嘗試以不同方式分類收納資料，或加入新的資料行時，請記得使用 [**檔模型**] wizard 來捕捉每個模型中繼資料和結果的快照集。</span><span class="sxs-lookup"><span data-stu-id="80e65-158">As you try binning your data different ways, or adding new columns, remember to use the **Document Model** wizard to capture a snapshot of each model's metadata and results.</span></span> <span data-ttu-id="80e65-159">保有記錄可讓您在探索的過程中更輕鬆地追蹤進度。</span><span class="sxs-lookup"><span data-stu-id="80e65-159">Having a record will make it easier to track progress in your exploration.</span></span>  
  
 [<span data-ttu-id="80e65-160">瀏覽和清除資料</span><span class="sxs-lookup"><span data-stu-id="80e65-160">Exploring and Cleaning Data</span></span>](exploring-and-cleaning-data.md)  
  
## <a name="validate-your-model"></a><span data-ttu-id="80e65-161">驗證模型</span><span class="sxs-lookup"><span data-stu-id="80e65-161">Validate Your Model</span></span>  
 <span data-ttu-id="80e65-162">您執行每個精靈或工具時，演算法都會分析資料的內容，並判斷統計上有效的模式是否存在。</span><span class="sxs-lookup"><span data-stu-id="80e65-162">As you run each wizard or tool, the algorithm analyzes the contents of the data and determines whether a statistically valid pattern exists.</span></span> <span data-ttu-id="80e65-163">如果演算法找不到有效的模式，您將會收到錯誤訊息。</span><span class="sxs-lookup"><span data-stu-id="80e65-163">If the algorithm cannot find valid patterns, you'll get an error message.</span></span> <span data-ttu-id="80e65-164">不過，即使已成功建立模型，您仍會想要測試模型，以查看它是否驗證您的假設。</span><span class="sxs-lookup"><span data-stu-id="80e65-164">However, even if a model was successfully created, you'll want to test the model to see if it validates your assumptions.</span></span> <span data-ttu-id="80e65-165">您可以使用 [精確度圖表] 之類的工具[&#40;SQL Server 資料採礦增益集&#41;](accuracy-chart-sql-server-data-mining-add-ins.md)或[交叉驗證 &#40;SQL Server 資料採礦增益集&#41;](cross-validation-sql-server-data-mining-add-ins.md)來產生模型品質的統計量值。</span><span class="sxs-lookup"><span data-stu-id="80e65-165">You can use tools such as the [Accuracy Chart &#40;SQL Server Data Mining Add-ins&#41;](accuracy-chart-sql-server-data-mining-add-ins.md) or [Cross-Validation &#40;SQL Server Data Mining Add-ins&#41;](cross-validation-sql-server-data-mining-add-ins.md) to produce statistical measures of model quality.</span></span>  
  
 <span data-ttu-id="80e65-166">當您評估第一個模型的結果時，請反問自己下列問題：</span><span class="sxs-lookup"><span data-stu-id="80e65-166">As you assess the results of your first model, ask yourself questions such as these:</span></span>  
  
-   <span data-ttu-id="80e65-167">找到哪種模式？</span><span class="sxs-lookup"><span data-stu-id="80e65-167">What kinds of patterns were found?</span></span> <span data-ttu-id="80e65-168">機率和支援的值是哪些？</span><span class="sxs-lookup"><span data-stu-id="80e65-168">What are the probabilities and support values?</span></span>  
  
-   <span data-ttu-id="80e65-169">我們對趨勢的猜測是正確的，還是資料中有令人意外的關聯？</span><span class="sxs-lookup"><span data-stu-id="80e65-169">Were our guesses about trends correct, or were there surprising correlations?</span></span>  
  
-   <span data-ttu-id="80e65-170">收集的資料是否足夠？</span><span class="sxs-lookup"><span data-stu-id="80e65-170">Did we collect enough data?</span></span> <span data-ttu-id="80e65-171">分類收納資料是否會產生更清楚的模式？</span><span class="sxs-lookup"><span data-stu-id="80e65-171">Would binning the data produce clearer patterns?</span></span>  
  
-   <span data-ttu-id="80e65-172">資料集是否平衡？</span><span class="sxs-lookup"><span data-stu-id="80e65-172">Is the data set balanced?</span></span> <span data-ttu-id="80e65-173">交叉驗證可以測試資料的代表性。</span><span class="sxs-lookup"><span data-stu-id="80e65-173">Cross-validation can test the representativeness of your data.</span></span>  
  
 [<span data-ttu-id="80e65-174">適用於 Excel 的資料表分析工具</span><span class="sxs-lookup"><span data-stu-id="80e65-174">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
 [<span data-ttu-id="80e65-175">適用于 Excel &#40;SQL Server 資料採礦增益集的資料採礦用戶端&#41;</span><span class="sxs-lookup"><span data-stu-id="80e65-175">Data Mining Client for Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](data-mining-client-for-excel-sql-server-data-mining-add-ins.md)  
  
 [<span data-ttu-id="80e65-176">選擇模型</span><span class="sxs-lookup"><span data-stu-id="80e65-176">Choosing a Model</span></span>](choosing-a-model.md)  
  
## <a name="explore-and-refine"></a><span data-ttu-id="80e65-177">瀏覽及精簡</span><span class="sxs-lookup"><span data-stu-id="80e65-177">Explore and Refine</span></span>  
 <span data-ttu-id="80e65-178">如果模型看似有效，您可以使用模型進行預測、提出建議、衍生深入資訊或規劃商務策略。</span><span class="sxs-lookup"><span data-stu-id="80e65-178">If the model appears to be valid, you can use the model for prediction, recommendation, deriving insights, or planning business strategies..</span></span>  
  
-   <span data-ttu-id="80e65-179">在適用於 Excel 的資料採礦用戶端中使用資料採礦瀏覽器瀏覽模型並進行互動。</span><span class="sxs-lookup"><span data-stu-id="80e65-179">Use the data mining browser in the Data Mining Client for Excel to explore and interact with the model.</span></span>  
  
-   <span data-ttu-id="80e65-180">使用 Excel 重新排列和篩選結果。</span><span class="sxs-lookup"><span data-stu-id="80e65-180">Use Excel to rearrange and filter the results.</span></span>  
  
-   <span data-ttu-id="80e65-181">使用 Visio 建立簡報並反白顯示資料中找到的關聯性。</span><span class="sxs-lookup"><span data-stu-id="80e65-181">Use Visio to create presentations and highlight the relationships found in the data.</span></span>  
  
 <span data-ttu-id="80e65-182">您通常可透過分析的第一個結果找到改進分析的方式，或了解是否需要取得新資料和更佳的資料。</span><span class="sxs-lookup"><span data-stu-id="80e65-182">Often, the first result of analysis is that you see ways to improve the analysis, or realize that you need to get new and better data.</span></span> <span data-ttu-id="80e65-183">由於使用適用於 Excel 的資料採礦增益集建立的模型可儲存至 Analysis Services 執行個體，因此您可以輕鬆以新資料更新模型，並繼續精簡及重複使用成功的模型。</span><span class="sxs-lookup"><span data-stu-id="80e65-183">Because the models that you create using the Data Mining Add-ins for Excel can be saved to an instance of Analysis Service, it is relatively easy to update the model with new data, and continue to refine and re-use successful models.</span></span>  
  
 <span data-ttu-id="80e65-184">資料採礦模型的重要用途是建立預測和建議。</span><span class="sxs-lookup"><span data-stu-id="80e65-184">An important use of data mining models is to create predictions and recommendations.</span></span> <span data-ttu-id="80e65-185">適用於 Excel 的資料採礦增益集中的工具可讓您輕鬆產生更複雜的預測查詢，將深入資訊轉換成可採取動作的結果。</span><span class="sxs-lookup"><span data-stu-id="80e65-185">The Data Mining Add-ins for Excel includes tools that make it easy to generate even complex prediction queries, for converting insights into actionable results.</span></span> <span data-ttu-id="80e65-186">所有這些工具都完全整合到 Excel 中。</span><span class="sxs-lookup"><span data-stu-id="80e65-186">All of these tools are fully integrated with Excel.</span></span>  
  
 [<span data-ttu-id="80e65-187">&#40;適用于 Office&#41;的資料採礦增益集來查看模型</span><span class="sxs-lookup"><span data-stu-id="80e65-187">Viewing Models &#40;Data Mining Add-ins for Office&#41;</span></span>](viewing-models-data-mining-add-ins-for-office.md)  
  
 [<span data-ttu-id="80e65-188">驗證模型及使用模型進行預測 &#40;適用于 Excel 的資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="80e65-188">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
## <a name="see-also"></a><span data-ttu-id="80e65-189">另請參閱</span><span class="sxs-lookup"><span data-stu-id="80e65-189">See Also</span></span>  
 <span data-ttu-id="80e65-190">[適用于 Office 的資料採礦增益集包含的內容](what-s-included-in-the-data-mining-add-ins-for-office.md) </span><span class="sxs-lookup"><span data-stu-id="80e65-190">[What's Included in the Data Mining Add-Ins for Office](what-s-included-in-the-data-mining-add-ins-for-office.md) </span></span>  
 [<span data-ttu-id="80e65-191">適用于 Excel&#41;的資料採礦增益集的技術參考 &#40;</span><span class="sxs-lookup"><span data-stu-id="80e65-191">Technical Reference &#40;Data Mining Add-ins for Excel&#41;</span></span>](technical-reference-data-mining-add-ins-for-excel.md)  
  
  
