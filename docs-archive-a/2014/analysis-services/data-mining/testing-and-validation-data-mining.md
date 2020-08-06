---
title: 測試和驗證 (資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- testing data mining models
- comparing mining models
- continuous attribute charts
- data mining [Analysis Services], models
- charts [Analysis Services]
- predictive modeling [Analysis Services]
- mining models [Analysis Services], validating
- validating data mining models
- viewing mining accuracy
- confidence scores [data mining]
- displaying mining accuracy
- predictions [Analysis Services], comparing mining models
- scoring [data mining]
- lift charts [Analysis Services]
- classification matrix [Analysis Services]
- CRISP-DM
- accuracy testing [data mining]
ms.assetid: 197144f5-21ed-4009-b448-fe412fb3916c
author: minewiskan
ms.author: owend
ms.openlocfilehash: c12f0215daed0c3308c63f36df0ba323152ec8d0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584825"
---
# <a name="testing-and-validation-data-mining"></a><span data-ttu-id="4e230-102">測試和驗證 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="4e230-102">Testing and Validation (Data Mining)</span></span>
  <span data-ttu-id="4e230-103">驗證是評估採礦模型對實際資料的執行效能有多好的處理程序。</span><span class="sxs-lookup"><span data-stu-id="4e230-103">Validation is the process of assessing how well your mining models perform against real data.</span></span> <span data-ttu-id="4e230-104">在部署採礦模型至生產環境之前，先了解其品質和特性以驗證採礦模型是很重要的。</span><span class="sxs-lookup"><span data-stu-id="4e230-104">It is important that you validate your mining models by understanding their quality and characteristics before you deploy them into a production environment.</span></span>  
  
 <span data-ttu-id="4e230-105">本節介紹一些與模型品質相關的基本概念，並說明中提供的模型驗證策略 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4e230-105">This section introduces some basic concepts related to model quality, and describes the strategies for model validation that are provided in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="4e230-106">如需模型驗證如何配合較大型資料採礦處理的概觀，請參閱 [資料採礦方案](data-mining-solutions.md)。</span><span class="sxs-lookup"><span data-stu-id="4e230-106">For an overview of how model validation fits into the larger data mining process, see [Data Mining Solutions](data-mining-solutions.md).</span></span>  
  
## <a name="methods-for-testing-and-validation-of-data-mining-models"></a><span data-ttu-id="4e230-107">測試的方法和資料採礦模型的驗證</span><span class="sxs-lookup"><span data-stu-id="4e230-107">Methods for Testing and Validation of Data Mining Models</span></span>  
 <span data-ttu-id="4e230-108">有多種方法可以評估資料採礦模型的品質和特性。</span><span class="sxs-lookup"><span data-stu-id="4e230-108">There are many approaches for assessing the quality and characteristics of a data mining model.</span></span>  
  
-   <span data-ttu-id="4e230-109">您可以使用各種統計驗證量值來判斷資料或模型中是否有問題。</span><span class="sxs-lookup"><span data-stu-id="4e230-109">Use various measures of statistical validity to determine whether there are problems in the data or in the model.</span></span>  
  
-   <span data-ttu-id="4e230-110">也可以將資料分隔成定型集和測試集以測試預測的精確度。</span><span class="sxs-lookup"><span data-stu-id="4e230-110">Separate the data into training and testing sets to test the accuracy of predictions.</span></span>  
  
-   <span data-ttu-id="4e230-111">您也可以要求商務專家檢閱資料採礦模型的結果，以判斷找到的模式在目標商務案例中是否具有意義。</span><span class="sxs-lookup"><span data-stu-id="4e230-111">Ask business experts to review the results of the data mining model to determine whether the discovered patterns have meaning in the targeted business scenario</span></span>  
  
 <span data-ttu-id="4e230-112">上述所有方法在資料採礦方法中都很有用，可在您建立、測試和精簡模型以解決特定問題時反覆使用。</span><span class="sxs-lookup"><span data-stu-id="4e230-112">All of these methods are useful in data mining methodology and are used iteratively as you create, test, and refine models to answer a specific problem.</span></span> <span data-ttu-id="4e230-113">沒有任何一項規則能完整地可以告訴您模型是否夠好，或是資料是否足夠。</span><span class="sxs-lookup"><span data-stu-id="4e230-113">No single comprehensive rule can tell you when a model is good enough, or when you have enough data.</span></span>  
  
## <a name="definition-of-criteria-for-validating-data-mining-models"></a><span data-ttu-id="4e230-114">驗證資料採礦模型的準則定義</span><span class="sxs-lookup"><span data-stu-id="4e230-114">Definition of Criteria for Validating Data Mining Models</span></span>  
 <span data-ttu-id="4e230-115">資料採礦的量值一般可分為精確度、可靠性和效益等類別目錄。</span><span class="sxs-lookup"><span data-stu-id="4e230-115">Measures of data mining generally fall into the categories of accuracy, reliability, and usefulness.</span></span>  
  
 <span data-ttu-id="4e230-116">*「精確度」* (Accuracy) 是一種量值，代表模型可將結果與所提供資料中的屬性相互關聯的程度。</span><span class="sxs-lookup"><span data-stu-id="4e230-116">*Accuracy* is a measure of how well the model correlates an outcome with the attributes in the data that has been provided.</span></span> <span data-ttu-id="4e230-117">精確度有多種量值，但所有的精確度量值都是依所使用的資料而定。</span><span class="sxs-lookup"><span data-stu-id="4e230-117">There are various measures of accuracy, but all measures of accuracy are dependent on the data that is used.</span></span> <span data-ttu-id="4e230-118">事實上，值可能會遺失或僅是近似值，或者資料可能已由多項處理序變更。</span><span class="sxs-lookup"><span data-stu-id="4e230-118">In reality, values might be missing or approximate, or the data might have been changed by multiple processes.</span></span> <span data-ttu-id="4e230-119">特別是在瀏覽和開發階段中，您可能會決定接受資料中特定的錯誤量 (尤其是當資料的特性相當統一時)。</span><span class="sxs-lookup"><span data-stu-id="4e230-119">Particularly in the phase of exploration and development, you might decide to accept a certain amount of error in the data, especially if the data is fairly uniform in its characteristics.</span></span> <span data-ttu-id="4e230-120">例如，根據過去的銷售量而預測特定店家銷售額的模型，可能會具有強烈的關聯性而且非常正確，即使該店家過去一直使用錯誤的會計方法；</span><span class="sxs-lookup"><span data-stu-id="4e230-120">For example, a model that predicts sales for a particular store based on past sales can be strongly correlated and very accurate, even if that store consistently used the wrong accounting method.</span></span> <span data-ttu-id="4e230-121">因此，精確度的測量必須藉由可靠性的評估來平衡。</span><span class="sxs-lookup"><span data-stu-id="4e230-121">Therefore, measurements of accuracy must be balanced by assessments of reliability.</span></span>  
  
 <span data-ttu-id="4e230-122">*「可靠性」* 評估資料採礦模型在不同的資料集上執行的方式。</span><span class="sxs-lookup"><span data-stu-id="4e230-122">*Reliability* assesses the way that a data mining model performs on different data sets.</span></span> <span data-ttu-id="4e230-123">如果不管所提供的測試資料為何，資料採礦模型都會產生相同的預測類型或找到相同的一般模式類型，則該模型就是可靠的。</span><span class="sxs-lookup"><span data-stu-id="4e230-123">A data mining model is reliable if it generates the same type of predictions or finds the same general kinds of patterns regardless of the test data that is supplied.</span></span> <span data-ttu-id="4e230-124">例如，您針對使用錯誤會計方法的店家所產生的模型，就無法通用於其他店家，因此並不可靠。</span><span class="sxs-lookup"><span data-stu-id="4e230-124">For example, the model that you generate for the store that used the wrong accounting method would not generalize well to other stores, and therefore would not be reliable.</span></span>  
  
 <span data-ttu-id="4e230-125">*「效益」* 包含多種標準，可表示模型是否提供有用的資訊。</span><span class="sxs-lookup"><span data-stu-id="4e230-125">*Usefulness* includes various metrics that tell you whether the model provides useful information.</span></span> <span data-ttu-id="4e230-126">例如，將店家地點與銷售額相互關聯的資料採礦模型可能既精確又可靠，但效益卻可能不高，因為無法新增更多位於相同地點的店家來廣泛應用該結果。</span><span class="sxs-lookup"><span data-stu-id="4e230-126">For example, a data mining model that correlates store location with sales might be both accurate and reliable, but might not be useful, because you cannot generalize that result by adding more stores at the same location.</span></span> <span data-ttu-id="4e230-127">此外，該模型也無法回答為何特定地點的銷售額較高的基本商務問題。</span><span class="sxs-lookup"><span data-stu-id="4e230-127">Moreover, it does not answer the fundamental business question of why certain locations have more sales.</span></span> <span data-ttu-id="4e230-128">您也可能發現看來成功的模型實際上卻沒有意義，因為它是根據資料中的交叉相互關聯而定。</span><span class="sxs-lookup"><span data-stu-id="4e230-128">You might also find that a model that appears successful in fact is meaningless, because it is based on cross-correlations in the data.</span></span>  
  
## <a name="tools-for-testing-and-validation-of-mining-models"></a><span data-ttu-id="4e230-129">測試的工具和資料採礦模型的驗證</span><span class="sxs-lookup"><span data-stu-id="4e230-129">Tools for Testing and Validation of Mining Models</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] <span data-ttu-id="4e230-130">支援資料採礦方案的多種驗證方法，且這些方法支援資料採礦測試方法的所有階段。</span><span class="sxs-lookup"><span data-stu-id="4e230-130">supports multiple approaches to validation of data mining solutions, supporting all phases of the data mining test methodology.</span></span>  
  
-   <span data-ttu-id="4e230-131">將資料分割到定型集和測試集中。</span><span class="sxs-lookup"><span data-stu-id="4e230-131">Partitioning data into testing and training sets.</span></span>  
  
-   <span data-ttu-id="4e230-132">篩選模型，以定型和測試相同來源資料的不同組合。</span><span class="sxs-lookup"><span data-stu-id="4e230-132">Filtering models to train and test different combinations of the same source data.</span></span>  
  
-   <span data-ttu-id="4e230-133">測量 *「增益」* (Lift) 和 *「改善」*(Gain)。</span><span class="sxs-lookup"><span data-stu-id="4e230-133">Measuring *lift* and *gain*.</span></span> <span data-ttu-id="4e230-134">*「增益圖」* (Lift chart) 是當您將使用資料採礦模型而獲得的改進與隨機猜測進行比較時，將改進的程度視覺化的方法。</span><span class="sxs-lookup"><span data-stu-id="4e230-134">A *lift chart* is a method of visualizing the improvement that you get from using a data mining model, when you compare it to random guessing.</span></span>  
  
-   <span data-ttu-id="4e230-135">執行資料集的「交叉驗證」\*\*</span><span class="sxs-lookup"><span data-stu-id="4e230-135">Performing *cross-validation* of data sets</span></span>  
  
-   <span data-ttu-id="4e230-136">產生 *「分類矩陣」*(Classification matrices)。</span><span class="sxs-lookup"><span data-stu-id="4e230-136">Generating *classification matrices*.</span></span> <span data-ttu-id="4e230-137">這些圖表可將良好和不正確的猜測排序成資料表，即可快速簡易地量測出模型在預測目標值時精確度。</span><span class="sxs-lookup"><span data-stu-id="4e230-137">These charts sort good and bad guesses into a table so that you can quickly and easily gauge how accurately the model predicts the target value.</span></span>  
  
-   <span data-ttu-id="4e230-138">建立 *「散佈圖」* (Scatter plot) 評估迴歸公式的適合度。</span><span class="sxs-lookup"><span data-stu-id="4e230-138">Creating *scatter plots* to assess the fit of a regression formula.</span></span>  
  
-   <span data-ttu-id="4e230-139">您可建立 *「收益圖」* (Profit chart)，將財務收益或成本與採礦模型使用方式產生關聯，以便評估建議的值。</span><span class="sxs-lookup"><span data-stu-id="4e230-139">Creating *profit charts* that associate financial gain or costs with the use of a mining model, so that you can assess the value of the recommendations.</span></span>  
  
 <span data-ttu-id="4e230-140">這些度量的目的不是用來回答資料採礦模型是否能解答您的商務疑問，而是提供客觀的測量，以供您評估預測分析資料的可靠性，並引導您判斷開發程序是否需要使用特定的反覆運算。</span><span class="sxs-lookup"><span data-stu-id="4e230-140">These metrics do not aim to answer the question of whether the data mining model answers your business question; rather, these metrics provide objective measurements that you can use to assess the reliability of your data for predictive analytics, and to guide your decision of whether to use a particular iterate on the development process.</span></span>  
  
 <span data-ttu-id="4e230-141">本節中的主題提供每一種方法的概觀，並逐步引導您使用 SQL Server 資料採礦所建立之測量模型精確度的程序。</span><span class="sxs-lookup"><span data-stu-id="4e230-141">The topics in this section provide an overview of each method and walk you through the process of measuring the accuracy of models that you build using SQL Server Data Mining.</span></span>  
  
### <a name="related-topics"></a><span data-ttu-id="4e230-142">相關主題</span><span class="sxs-lookup"><span data-stu-id="4e230-142">Related Topics</span></span>  
  
|<span data-ttu-id="4e230-143">主題</span><span class="sxs-lookup"><span data-stu-id="4e230-143">Topics</span></span>|<span data-ttu-id="4e230-144">連結</span><span class="sxs-lookup"><span data-stu-id="4e230-144">Links</span></span>|  
|------------|-----------|  
|<span data-ttu-id="4e230-145">了解如何使用精靈或 DMX 命令來設定測試資料集</span><span class="sxs-lookup"><span data-stu-id="4e230-145">Learn how to set up a testing data set using a wizard or DMX commands</span></span>|[<span data-ttu-id="4e230-146">定型和測試資料集</span><span class="sxs-lookup"><span data-stu-id="4e230-146">Training and Testing Data Sets</span></span>](training-and-testing-data-sets.md)|  
|<span data-ttu-id="4e230-147">了解如何測試採礦結構中資料的散發及代表意義</span><span class="sxs-lookup"><span data-stu-id="4e230-147">Learn how to test the distribution and representativeness of the data in a mining structure</span></span>|[<span data-ttu-id="4e230-148">交叉驗證 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="4e230-148">Cross-Validation &#40;Analysis Services - Data Mining&#41;</span></span>](cross-validation-analysis-services-data-mining.md)|  
|<span data-ttu-id="4e230-149">了解 [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)]中提供的精確度圖表類型。</span><span class="sxs-lookup"><span data-stu-id="4e230-149">Learn about the accuracy chart types provided in [!INCLUDE[ssASCurrent](../../includes/ssascurrent-md.md)].</span></span>|[<span data-ttu-id="4e230-150">增益圖 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="4e230-150">Lift Chart &#40;Analysis Services - Data Mining&#41;</span></span>](lift-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="4e230-151">收益圖 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="4e230-151">Profit Chart &#40;Analysis Services - Data Mining&#41;</span></span>](profit-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="4e230-152">散佈圖 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="4e230-152">Scatter Plot &#40;Analysis Services - Data Mining&#41;</span></span>](scatter-plot-analysis-services-data-mining.md)|  
|<span data-ttu-id="4e230-153">了解如何建立分類矩陣 (也稱為混淆矩陣) 以評估真肯定、誤判、真否定、誤否定的數量。</span><span class="sxs-lookup"><span data-stu-id="4e230-153">Learn how to create a classification matrix, sometimes called a confusion matrix, for assessing the number of true and false positives and negatives.</span></span>|[<span data-ttu-id="4e230-154">分類矩陣 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="4e230-154">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](classification-matrix-analysis-services-data-mining.md)|  
  
## <a name="see-also"></a><span data-ttu-id="4e230-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e230-155">See Also</span></span>  
 <span data-ttu-id="4e230-156">[資料採礦工具](data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="4e230-156">[Data Mining Tools](data-mining-tools.md) </span></span>  
 <span data-ttu-id="4e230-157">[資料採礦解決方案](data-mining-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="4e230-157">[Data Mining Solutions](data-mining-solutions.md) </span></span>  
 [<span data-ttu-id="4e230-158">測試及驗證工作與操作方法 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="4e230-158">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
  
