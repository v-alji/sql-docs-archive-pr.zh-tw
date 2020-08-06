---
title: 資料採礦設計工具 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], structure
- mining structures [Analysis Services], modifying
- data mining editor [Analysis Services]
- Data Mining Designer
- data mining [Analysis Services], modifying
ms.assetid: 2540db5b-2bf3-4b6c-87c8-79c48d71acce
author: minewiskan
ms.author: owend
ms.openlocfilehash: 820cde158dfabff525081060369daace0e83c8dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585674"
---
# <a name="data-mining-designer"></a><span data-ttu-id="359cd-102">資料採礦設計師</span><span class="sxs-lookup"><span data-stu-id="359cd-102">Data Mining Designer</span></span>
  <span data-ttu-id="359cd-103">資料採礦設計師是您在中使用採礦模型的主要環境 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="359cd-103">Data Mining Designer is the primary environment in which you work with mining models in [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="359cd-104">您可以選取現有的採礦結構，或使用資料採礦精靈來建立新的採礦結構和採礦模型，以存取此設計師。</span><span class="sxs-lookup"><span data-stu-id="359cd-104">You can access the designer either by selecting an existing mining structure, or by using the Data Mining Wizard to create a new mining structure and mining model.</span></span> <span data-ttu-id="359cd-105">您可以使用資料採礦設計師來執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="359cd-105">You can use Data Mining Designer to perform the following tasks:</span></span>  
  
-   <span data-ttu-id="359cd-106">修改一開始是由資料採礦精靈所建立的採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="359cd-106">Modify the mining structure and the mining model that were initially created by the Data Mining Wizard.</span></span>  
  
-   <span data-ttu-id="359cd-107">以現有的採礦結構為基礎來建立新模型。</span><span class="sxs-lookup"><span data-stu-id="359cd-107">Create new models based on an existing mining structure.</span></span>  
  
-   <span data-ttu-id="359cd-108">培訓及瀏覽採礦模型。</span><span class="sxs-lookup"><span data-stu-id="359cd-108">Train and browse mining models.</span></span>  
  
-   <span data-ttu-id="359cd-109">使用精確度圖表來比較模型。</span><span class="sxs-lookup"><span data-stu-id="359cd-109">Compare models by using accuracy charts.</span></span>  
  
-   <span data-ttu-id="359cd-110">依據採礦模型建立預測查詢。</span><span class="sxs-lookup"><span data-stu-id="359cd-110">Create prediction queries based on mining models.</span></span>  
  
## <a name="mining-structure-tab"></a><span data-ttu-id="359cd-111">採礦結構索引標籤</span><span class="sxs-lookup"><span data-stu-id="359cd-111">Mining Structure Tab</span></span>  
 <span data-ttu-id="359cd-112">使用 **[採礦結構]** 索引標籤，加入資料行及修改現有採礦結構的屬性。</span><span class="sxs-lookup"><span data-stu-id="359cd-112">Use the **Mining Structure** tab to add columns and modify the properties of an existing mining structure.</span></span> <span data-ttu-id="359cd-113">下列工作和主題提供有關使用採礦結構的詳細資訊：</span><span class="sxs-lookup"><span data-stu-id="359cd-113">The following tasks and topics provide more information about working with mining structures:</span></span>  
  
 [<span data-ttu-id="359cd-114">採礦結構 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="359cd-114">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](mining-structures-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="359cd-115">採礦結構工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="359cd-115">Mining Structure Tasks and How-tos</span></span>](mining-structure-tasks-and-how-tos.md)  
  
## <a name="mining-models-tab"></a><span data-ttu-id="359cd-116">採礦模型索引標籤</span><span class="sxs-lookup"><span data-stu-id="359cd-116">Mining Models Tab</span></span>  
 <span data-ttu-id="359cd-117">使用 **[採礦模型]** 索引標籤來管理現有的採礦模型和建立新的模型。</span><span class="sxs-lookup"><span data-stu-id="359cd-117">Use the **Mining Models** tab to manage existing mining models and to create new models.</span></span> <span data-ttu-id="359cd-118">採礦模型一定會以現有的採礦結構為基礎。</span><span class="sxs-lookup"><span data-stu-id="359cd-118">Mining models are always based on an existing mining structure .</span></span>  
  
 <span data-ttu-id="359cd-119">在 [採礦模型]\*\*\*\* 索引標籤中，您可以變更演算法類型、新增或移除與模型結構相關聯的資料行、調整演算法特有的資料行屬性、指定採礦模型資料行使用方式，以及調整與採礦模型相關聯的演算法參數。</span><span class="sxs-lookup"><span data-stu-id="359cd-119">In the **Mining Models** tab, you can change the algorithm type, add or remove columns that are associated with the model structure, adjust algorithm-specific column properties, specify the mining model column usage, and adjust algorithm parameters that are associated with the mining model.</span></span> <span data-ttu-id="359cd-120">您也可以同時處理採礦結構與所選取的模型或所有相關聯的模型。</span><span class="sxs-lookup"><span data-stu-id="359cd-120">You can also process the mining structure together with selected models or with all the associated models.</span></span>  
  
 <span data-ttu-id="359cd-121">如需有關使用採礦模型的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="359cd-121">See the following topics for more information about working with mining models:</span></span>  
  
 [<span data-ttu-id="359cd-122">採礦模型 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="359cd-122">Mining Models &#40;Analysis Services - Data Mining&#41;</span></span>](mining-models-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="359cd-123">採礦模型工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="359cd-123">Mining Model Tasks and How-tos</span></span>](mining-model-tasks-and-how-tos.md)  
  
## <a name="mining-model-viewer-tab"></a><span data-ttu-id="359cd-124">採礦模型檢視器索引標籤</span><span class="sxs-lookup"><span data-stu-id="359cd-124">Mining Model Viewer Tab</span></span>  
 <span data-ttu-id="359cd-125">使用 **[採礦模型檢視器]** 索引標籤，以視覺化方式瀏覽採礦模型。</span><span class="sxs-lookup"><span data-stu-id="359cd-125">Use the **Mining Model Viewer** tab to visually explore your mining models.</span></span> <span data-ttu-id="359cd-126">每一個採礦模型與一個自訂檢視器相關聯，後者會顯示該模型的特定內容。</span><span class="sxs-lookup"><span data-stu-id="359cd-126">Each mining model is associated with a custom viewer that displays content that is specific to that model.</span></span> <span data-ttu-id="359cd-127">您也可以使用內容檢視器來檢視採礦模型內容。</span><span class="sxs-lookup"><span data-stu-id="359cd-127">You can also view mining model content by using the content viewer.</span></span>  
  
 <span data-ttu-id="359cd-128">如需有關使用資料採礦檢視器瀏覽採礦模型的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="359cd-128">See the following topics for more information about exploring mining models with the data mining viewers:</span></span>  
  
 [<span data-ttu-id="359cd-129">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="359cd-129">Data Mining Model Viewers</span></span>](data-mining-model-viewers.md)  
  
 [<span data-ttu-id="359cd-130">採礦模型檢視器工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="359cd-130">Mining Model Viewer Tasks and How-tos</span></span>](mining-model-viewer-tasks-and-how-tos.md)  
  
## <a name="mining-accuracy-chart-tab"></a><span data-ttu-id="359cd-131">採礦精確度圖表索引標籤</span><span class="sxs-lookup"><span data-stu-id="359cd-131">Mining Accuracy Chart Tab</span></span>  
 <span data-ttu-id="359cd-132">使用 **[採礦精確度圖表]** 索引標籤來測試單一採礦模型的預測精確度，或比較採礦結構內所包含之多個採礦模型的效能。</span><span class="sxs-lookup"><span data-stu-id="359cd-132">Use the **Mining Accuracy Chart** tab to test the predictive accuracy of a single mining model, or to compare the effectiveness of multiple mining models contained within a mining structure.</span></span> <span data-ttu-id="359cd-133">這個索引標籤包含的工具是用來篩選資料、選取採礦模型，以及以增益圖、收益圖或分類矩陣顯示結果。</span><span class="sxs-lookup"><span data-stu-id="359cd-133">The tab contains tools for filtering the data, selecting mining models, and displaying the results in a lift chart, profit chart, or classification matrix.</span></span>  
  
 <span data-ttu-id="359cd-134">如需有關測試和驗證採礦模型的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="359cd-134">See the following topics for more information about testing and validating mining models:</span></span>  
  
 [<span data-ttu-id="359cd-135">測試及驗證 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="359cd-135">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
 [<span data-ttu-id="359cd-136">測試及驗證工作與操作方法 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="359cd-136">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)  
  
## <a name="mining-model-prediction-tab"></a><span data-ttu-id="359cd-137">採礦模型預測索引標籤</span><span class="sxs-lookup"><span data-stu-id="359cd-137">Mining Model Prediction Tab</span></span>  
 <span data-ttu-id="359cd-138">[採礦模型預測]\*\*\*\* 索引標籤包括預測查詢產生器，可用以建立資料採礦延伸模組 (DMX) 預測查詢。</span><span class="sxs-lookup"><span data-stu-id="359cd-138">The **Mining Model Prediction** tab includes Prediction Query Builder, which you can use to create a Data Mining Extensions (DMX) prediction query.</span></span> <span data-ttu-id="359cd-139">這個索引標籤包含的工具是用來指定採礦模型和輸入資料表、將採礦模型中的資料行對應到輸入資料表中的資料行、將函數加入查詢中，以及指定每一個資料行的準則。</span><span class="sxs-lookup"><span data-stu-id="359cd-139">The tab contains tools for specifying mining models and input tables, mapping the columns in the mining model to columns in the input table, adding functions to a query, and specifying criteria for each column.</span></span>  
  
 <span data-ttu-id="359cd-140">在設計查詢之後，您可以使用索引標籤中的不同檢視來顯示查詢的結果及手動修改查詢。</span><span class="sxs-lookup"><span data-stu-id="359cd-140">After you design a query, you can use different views in the tab to display the results of the query and to modify the query manually.</span></span> <span data-ttu-id="359cd-141">您也可以將查詢的結果儲存到資料庫中的資料表。</span><span class="sxs-lookup"><span data-stu-id="359cd-141">You can also save the results of the query to a table in a database.</span></span>  
  
 <span data-ttu-id="359cd-142">如需有關建立資料採礦查詢的詳細資訊，請參閱下列主題：</span><span class="sxs-lookup"><span data-stu-id="359cd-142">See the following topics for more information about creating data mining queries:</span></span>  
  
 [<span data-ttu-id="359cd-143">資料採礦查詢</span><span class="sxs-lookup"><span data-stu-id="359cd-143">Data Mining Queries</span></span>](data-mining-queries.md)  
  
 [<span data-ttu-id="359cd-144">資料採礦查詢工作和使用說明</span><span class="sxs-lookup"><span data-stu-id="359cd-144">Data Mining Query Tasks and How-tos</span></span>](data-mining-query-tasks-and-how-tos.md)  
  
## <a name="see-also"></a><span data-ttu-id="359cd-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="359cd-145">See Also</span></span>  
 [<span data-ttu-id="359cd-146">資料採礦方案</span><span class="sxs-lookup"><span data-stu-id="359cd-146">Data Mining Solutions</span></span>](data-mining-solutions.md)  
  
  
