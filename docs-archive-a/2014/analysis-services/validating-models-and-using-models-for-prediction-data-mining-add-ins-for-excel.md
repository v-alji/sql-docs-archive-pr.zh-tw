---
title: 驗證模型及使用模型進行預測 (適用于 Excel 的資料採礦增益集) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- mining models, charting
- validation [data mining]
- mining models, testing
ms.assetid: e245ac1f-1230-48e9-9091-e70b131aa2a8
author: minewiskan
ms.author: owend
ms.openlocfilehash: c1dd4f9bab977a90579076b824d2c0aa525c84af
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594207"
---
# <a name="validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel"></a><span data-ttu-id="1c0b2-102">驗證模型及使用模型進行預測 (適用於 Excel 的資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="1c0b2-102">Validating Models and Using Models for Prediction (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="1c0b2-103">測試並驗證模型是資料採礦處理中的一個重要步驟。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-103">Testing and validating your model is an important step in the data mining process.</span></span> <span data-ttu-id="1c0b2-104">在將模型部署到實際環境之前，您必須了解採礦模型對實際資料的執行效能有多好。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-104">You must know how well your mining models perform against real data before you deploy the models into a production environment.</span></span>  
  
 <span data-ttu-id="1c0b2-105">資料採礦增益集所包含的工具可協助您測試您所建立的模型，以及使用模型來建立預測和建議。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-105">The Data Mining Add-ins include tools that help you test the models you built, and create predictions and recommendations using the models.</span></span>  
  
## <a name="accuracy-chart"></a><span data-ttu-id="1c0b2-106">精確度圖表</span><span class="sxs-lookup"><span data-stu-id="1c0b2-106">Accuracy Chart</span></span>  
 <span data-ttu-id="1c0b2-107">**精確度圖表**wizard 可協助您建立預測查詢，並藉由建立增益圖或散佈圖來評估資料採礦模型的效能。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-107">The **Accuracy Chart** wizard helps you create a prediction query and assess the performance of a data mining model by creating a lift chart or scatter plot chart.</span></span> <span data-ttu-id="1c0b2-108">增益圖有助於將結構中幾乎相同的模型加以區分，以協助您判斷哪一個模型的預測能力最佳。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-108">The lift chart helps distinguish between models in a structure that are almost the same, to help you determine which model provides the best predictions.</span></span>  
  
 [<span data-ttu-id="1c0b2-109">精確度圖表 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="1c0b2-109">Accuracy Chart &#40;SQL Server Data Mining Add-ins&#41;</span></span>](accuracy-chart-sql-server-data-mining-add-ins.md)  
  
## <a name="classification-matrix"></a><span data-ttu-id="1c0b2-110">分類矩陣</span><span class="sxs-lookup"><span data-stu-id="1c0b2-110">Classification Matrix</span></span>  
 <span data-ttu-id="1c0b2-111">[**分類矩陣**] wizard 可協助您建立預測查詢，以評估分類模型的效能。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-111">The **Classification Matrix** wizard helps you create a prediction query to assess the performance of a classification model.</span></span> <span data-ttu-id="1c0b2-112">其輸出是描述由模型所做之精確與不精確預測的摘要圖表。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-112">The output is a chart that summarizes both accurate and inaccurate predictions made by the model.</span></span> <span data-ttu-id="1c0b2-113">矩陣是重要的工具，因為它不僅會顯示模型正確地預測值的頻率，也會顯示模型最常預測錯誤的值。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-113">The matrix is a valuable tool because it not only shows how frequently the model correctly predicted a value, but also shows which values the model most frequently predicted incorrectly.</span></span>  
  
 [<span data-ttu-id="1c0b2-114">SQL Server 資料採礦增益集的分類矩陣 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="1c0b2-114">Classification Matrix &#40;SQL Server Data Mining Add-ins&#41;</span></span>](classification-matrix-sql-server-data-mining-add-ins.md)  
  
## <a name="profit-chart"></a><span data-ttu-id="1c0b2-115">收益圖</span><span class="sxs-lookup"><span data-stu-id="1c0b2-115">Profit Chart</span></span>  
 <span data-ttu-id="1c0b2-116">**收益圖**wizard 可協助您衡量使用資料採礦模型的優點，並評估誤報和誤否定的成本</span><span class="sxs-lookup"><span data-stu-id="1c0b2-116">The **Profit Chart** wizard helps you weigh the benefits of using a data mining model and assess the costs of both false positives and false negatives</span></span>  
  
 <span data-ttu-id="1c0b2-117">此圖表類型會測量模型的預測精確度，並併入您指定的單位和總成本。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-117">This chart type measures the prediction accuracy of the model and incorporates unit and overall costs that you specify.</span></span>  
  
 <span data-ttu-id="1c0b2-118">[收益圖 &#40;SQL Server 資料採礦增益集&#41;](profit-chart-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-118">[Profit Chart &#40;SQL Server Data Mining Add-ins&#41;](profit-chart-sql-server-data-mining-add-ins.md).</span></span>  
  
## <a name="cross-validation"></a><span data-ttu-id="1c0b2-119">交叉驗證</span><span class="sxs-lookup"><span data-stu-id="1c0b2-119">Cross-Validation</span></span>  
 <span data-ttu-id="1c0b2-120">交叉驗證是資料採礦社群中早已建立的技術，用於評估資料集的有效性以及該資料集的採礦模型的精確度。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-120">Cross-validation is an established technique in the data mining community for assessing the validity of a data set and the accuracy of a mining model on that data set.</span></span> <span data-ttu-id="1c0b2-121">它會將資料集分割為子集，然後反覆地建立、定型及測試每個子集的模型。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-121">It divides a set of data into subsets, and then iteratively creates, trains, and tests models on each subset.</span></span>  
  
 <span data-ttu-id="1c0b2-122">**交叉驗證**嚮導可讓您指定用來分割資料的折迭數目，然後提供交叉驗證報表，以統計方式描述這些交叉區段之間的差異。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-122">The **Cross-Validation** wizard lets you specify the number of folds to divide your data by, and then provides a cross-validation report that statistically describes the differences among these cross-sections.</span></span> <span data-ttu-id="1c0b2-123">根據此報表，您可以判斷模型是否在所有定型資料上都順利執行，或者可能對特定子集有所偏差。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-123">From this you can determine whether the model performs well on all training data, or might be skewed to a particular subset.</span></span>  
  
 [<span data-ttu-id="1c0b2-124">SQL Server 資料採礦增益集的交叉驗證 &#40;&#41;</span><span class="sxs-lookup"><span data-stu-id="1c0b2-124">Cross-Validation &#40;SQL Server Data Mining Add-ins&#41;</span></span>](cross-validation-sql-server-data-mining-add-ins.md)  
  
## <a name="query-wizard"></a><span data-ttu-id="1c0b2-125">查詢精靈</span><span class="sxs-lookup"><span data-stu-id="1c0b2-125">Query Wizard</span></span>  
 <span data-ttu-id="1c0b2-126">**查詢**嚮導是一種互動式工具，可協助您建立預測查詢。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-126">The **Query** wizard is an interactive tool that helps you build a prediction query.</span></span> <span data-ttu-id="1c0b2-127">查詢是用來產生建議、未來預測等等的方式。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-127">Queries are how you generate recommendations, future forecasts, and so forth.</span></span>  
  
 <span data-ttu-id="1c0b2-128">在 [**查詢**嚮導] 中，您可以挑選模型，然後提供輸入資料做為單一值或從資料表或範圍中取得，而 wizard 可協助您選取要輸出的資料行。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-128">In the **Query** wizard, you pick a model, and then provide input data, either as single values or from a table or range, and the wizard helps you select columns to output.</span></span> <span data-ttu-id="1c0b2-129">您也可以將函數加入至查詢，以產生機率分數和其他有用的統計資料。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-129">You can also add functions to your query to generate probability scores and other useful statistics.</span></span>  
  
 [<span data-ttu-id="1c0b2-130">查詢 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="1c0b2-130">Query &#40;SQL Server Data Mining Add-ins&#41;</span></span>](query-sql-server-data-mining-add-ins.md)  
  
## <a name="advanced-query-editor"></a><span data-ttu-id="1c0b2-131">進階查詢編輯器</span><span class="sxs-lookup"><span data-stu-id="1c0b2-131">Advanced Query Editor</span></span>  
 <span data-ttu-id="1c0b2-132">「**高級查詢編輯器**」是一組互動式的對話方塊，可協助您建立各種 DMX 語句、執行自訂查詢來建立和定型新模型、刪除模型，或建立新的資料集。</span><span class="sxs-lookup"><span data-stu-id="1c0b2-132">The **Advanced Query Editor** is an interactive set of dialog boxes that helps you build all kinds of DMX statements, anything from running custom queries to creating and training new models, deleting models, or creating new data sets.</span></span>  
  
 [<span data-ttu-id="1c0b2-133">進階資料採礦查詢編輯器</span><span class="sxs-lookup"><span data-stu-id="1c0b2-133">Advanced Data Mining Query Editor</span></span>](advanced-data-mining-query-editor.md)  
  
## <a name="see-also"></a><span data-ttu-id="1c0b2-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1c0b2-134">See Also</span></span>  
 <span data-ttu-id="1c0b2-135">[探索和清除資料](exploring-and-cleaning-data.md) </span><span class="sxs-lookup"><span data-stu-id="1c0b2-135">[Exploring and Cleaning Data](exploring-and-cleaning-data.md) </span></span>  
 <span data-ttu-id="1c0b2-136">[建立資料採礦模型](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="1c0b2-136">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 [<span data-ttu-id="1c0b2-137">&#40;適用于 Excel 的資料採礦增益集部署和調整採礦模型&#41;</span><span class="sxs-lookup"><span data-stu-id="1c0b2-137">Deploying and Scaling Mining Models &#40;Data Mining Add-ins for Excel&#41;</span></span>](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
