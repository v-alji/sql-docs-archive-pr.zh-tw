---
title: Microsoft 羅吉斯回歸演算法 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logical regression algorithms [Analysis Services]
- algorithms [data mining]
- neural network algorithms [Analysis Services]
- regression algorithms [Analysis Services]
ms.assetid: 3dd54d07-1c3b-4b87-b7f0-b962ed8cf844
author: minewiskan
ms.author: owend
ms.openlocfilehash: 56a1b0b82f82b62e55d0c7fdd528195b5713fcf9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606498"
---
# <a name="microsoft-logistic-regression-algorithm"></a><span data-ttu-id="7ecaf-102">Microsoft 羅吉斯迴歸演算法</span><span class="sxs-lookup"><span data-stu-id="7ecaf-102">Microsoft Logistic Regression Algorithm</span></span>
  <span data-ttu-id="7ecaf-103">羅吉斯迴歸演算法是知名的統計技術，可用來模型化二進位結果。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-103">Logistic regression is a well-known statistical technique that is used for modeling binary outcomes.</span></span>  
  
 <span data-ttu-id="7ecaf-104">採用不同的學習技術，就可以在統計研究中以各種方式實作邏輯迴歸。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-104">There are various implementations of logistic regression in statistics research, using different learning techniques.</span></span> <span data-ttu-id="7ecaf-105">[!INCLUDE[msCoName](../../includes/msconame-md.md)] 羅吉斯迴歸演算法已使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 類神經網路演算法的變化來實作。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-105">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Logistic Regression algorithm has been implemented by using a variation of the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Neural Network algorithm.</span></span> <span data-ttu-id="7ecaf-106">雖然此演算法與類神經網路演算法有許多共同特性，但更容易定型。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-106">This algorithm shares many of the qualities of neural networks but is easier to train.</span></span>  
  
 <span data-ttu-id="7ecaf-107">羅吉斯迴歸演算法有一個優點，就是它的彈性極高，可使用任何種類的輸入，並支援數種不同的分析工作：</span><span class="sxs-lookup"><span data-stu-id="7ecaf-107">One advantage of logistic regression is that the algorithm is highly flexible, taking any kind of input, and supports several different analytical tasks:</span></span>  
  
-   <span data-ttu-id="7ecaf-108">使用人口統計來進行有關結果的預測，例如特定疾病的風險等。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-108">Use demographics to make predictions about outcomes, such as risk for a certain disease.</span></span>  
  
-   <span data-ttu-id="7ecaf-109">瀏覽及衡量促成結果的因素。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-109">Explore and weight the factors that contribute to a result.</span></span> <span data-ttu-id="7ecaf-110">例如，尋找影響客戶重覆光顧商店的因素。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-110">For example, find the factors that influence customers to make a repeat visit to a store.</span></span>  
  
-   <span data-ttu-id="7ecaf-111">將文件、電子郵件或其他具有許多屬性的物件分類。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-111">Classify documents, e-mail, or other objects that have many attributes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ecaf-112">範例</span><span class="sxs-lookup"><span data-stu-id="7ecaf-112">Example</span></span>  
 <span data-ttu-id="7ecaf-113">試想有一群人共用類似的人口統計資訊，而且向 Adventure Works 購買產品。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-113">Consider a group of people who share similar demographic information and who buy products from the Adventure Works company.</span></span> <span data-ttu-id="7ecaf-114">藉由將資料模型化以與特定的結果 (例如購買目標產品) 產生關聯，您可以看出人口統計資訊對某人購買目標產品的可能性有何影響。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-114">By modeling the data to relate to a specific outcome, such as purchase of a target product, you can see how the demographic information contributes to someone's likelihood of buying the target product.</span></span>  
  
## <a name="how-the-algorithm-works"></a><span data-ttu-id="7ecaf-115">演算法的運作方式</span><span class="sxs-lookup"><span data-stu-id="7ecaf-115">How the Algorithm Works</span></span>  
 <span data-ttu-id="7ecaf-116">羅吉斯迴歸是知名的統計方法，可用來判斷多個因素對一組結果的比重。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-116">Logistic regression is a well-known statistical method for determining the contribution of multiple factors to a pair of outcomes.</span></span> <span data-ttu-id="7ecaf-117">Microsoft 實作使用修改過的類神經網路來建立輸入及輸出之間關聯性的模型。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-117">The Microsoft implementation uses a modified neural network to model the relationships between inputs and outputs.</span></span> <span data-ttu-id="7ecaf-118">這會評估每個輸入對輸出所造成的效果，而且在完成的模型中會衡量各種輸入。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-118">The effect of each input on the output is measured, and the various inputs are weighted in the finished model.</span></span> <span data-ttu-id="7ecaf-119">羅吉斯迴歸之所以如此命名，是因為資料曲線會藉由使用羅吉斯轉換進行壓縮，以最小化極端值的效果。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-119">The name logistic regression comes from the fact that the data curve is compressed by using a logistic transformation, to minimize the effect of extreme values.</span></span> <span data-ttu-id="7ecaf-120">如需此實作以及如何自訂此演算法的詳細資訊，請參閱 [Microsoft 羅吉斯迴歸演算法技術參考](microsoft-logistic-regression-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-120">For more information about the implementation, and how to customize the algorithm, see [Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md).</span></span>  
  
## <a name="data-required-for-logistic-regression-models"></a><span data-ttu-id="7ecaf-121">羅吉斯迴歸模型所需的資料</span><span class="sxs-lookup"><span data-stu-id="7ecaf-121">Data Required for Logistic Regression Models</span></span>  
 <span data-ttu-id="7ecaf-122">當您準備資料以供羅吉斯迴歸模型使用時，應該要了解特定演算法的需求，包括所需的資料量以及資料的使用方式。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-122">When you prepare data for use in training a logistic regression model, you should understand the requirements for the particular algorithm, including how much data is needed, and how the data is used.</span></span>  
  
 <span data-ttu-id="7ecaf-123">羅吉斯迴歸模型的需求如下：</span><span class="sxs-lookup"><span data-stu-id="7ecaf-123">The requirements for a logistic regression model are as follows:</span></span>  
  
 <span data-ttu-id="7ecaf-124">**單一索引鍵資料行** ：每個模型都必須包含一個能唯一識別每一筆記錄的數值或文字資料行。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-124">**A single key column** Each model must contain one numeric or text column that uniquely identifies each record.</span></span> <span data-ttu-id="7ecaf-125">不允許複合的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-125">Compound keys are not allowed.</span></span>  
  
 <span data-ttu-id="7ecaf-126">**輸入資料行** ：每個模型都至少包含一個輸入資料行，內含用來當做分析因素的值。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-126">**Input columns** Each model must contain at least one input column that contains the values that are used as factors in analysis.</span></span> <span data-ttu-id="7ecaf-127">您可以依需求擁有任何數量的輸入資料行，但根據每個資料行中的值數目，加入額外的資料行可能會增加培訓模型所需的時間。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-127">You can have as many input columns as you want, but depending on the number of values in each column, the addition of extra columns can increase the time it takes to train the model.</span></span>  
  
 <span data-ttu-id="7ecaf-128">**至少有一個可預測資料行** ：模型至少必須包含一個任何資料類型的可預測資料行，連續數值資料也包括在內。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-128">**At least one predictable column** The model must contain at least one predictable column of any data type, including continuous numeric data.</span></span> <span data-ttu-id="7ecaf-129">可預測資料行的值也可用來當做模型的輸入，或者也可以指定只將其用於預測。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-129">The values of the predictable column can also be treated as inputs to the model, or you can specify that it be used for prediction only.</span></span> <span data-ttu-id="7ecaf-130">巢狀資料表不可用於可預測的資料行，但可用來當做輸入。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-130">Nested tables are not allowed for predictable columns, but can be used as inputs.</span></span>  
  
 <span data-ttu-id="7ecaf-131">如需羅吉斯迴歸模型所支援之內容類型和資料類型的詳細資訊，請參閱 [Microsoft 羅吉斯迴歸演算法技術參考](microsoft-logistic-regression-algorithm-technical-reference.md)的＜需求＞一節。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-131">For more detailed information about the content types and data types supported for logistic regression models, see the Requirements section of [Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md).</span></span>  
  
## <a name="viewing-a-logistic-regression-model"></a><span data-ttu-id="7ecaf-132">檢視羅吉斯迴歸模型</span><span class="sxs-lookup"><span data-stu-id="7ecaf-132">Viewing a Logistic Regression Model</span></span>  
 <span data-ttu-id="7ecaf-133">若要瀏覽此模型，可以使用 Microsoft 類神經網路檢視器，或 Microsoft 一般內容樹狀檢視器。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-133">To explore the model, you can use the Microsoft Neural Network Viewer, or the Microsoft Generic Content Tree Viewer.</span></span>  
  
 <span data-ttu-id="7ecaf-134">當您使用 Microsoft 類神經網路檢視器檢視此模型時，Analysis Services 會顯示對特定結果有影響的因素，並依其重要性排序。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-134">When you view the model by using the Microsoft Neural Network Viewer, Analysis Services shows you the factors that contribute to a particular outcome, ranked by their importance.</span></span> <span data-ttu-id="7ecaf-135">您可以選擇要比較的屬性和值。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-135">You can choose an attribute and values to compare.</span></span> <span data-ttu-id="7ecaf-136">如需詳細資訊，請參閱 [使用 Microsoft 類神經網路檢視器瀏覽模型](browse-a-model-using-the-microsoft-neural-network-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-136">For more information, see [Browse a Model Using the Microsoft Neural Network Viewer](browse-a-model-using-the-microsoft-neural-network-viewer.md).</span></span>  
  
 <span data-ttu-id="7ecaf-137">如果想要知道更多詳細資訊，您可以在 Microsoft 一般內容樹狀檢視器中瀏覽此模型的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-137">If you want to know more, you can browse the model details by using the Microsoft Generic Content Tree Viewer.</span></span> <span data-ttu-id="7ecaf-138">羅吉斯迴歸模型的模型內容包含可顯示該模型所用之所有輸入的臨界節點，以及可預測屬性的子網路。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-138">The model content for a logistic regression model includes a marginal node that shows you the all the inputs used for the model, and subnetworks for the predictable attributes.</span></span> <span data-ttu-id="7ecaf-139">如需詳細資訊，請參閱 [羅吉斯迴歸模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;](mining-model-content-for-logistic-regression-models.md)。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-139">For more information, see [Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md).</span></span>  
  
## <a name="creating-predictions"></a><span data-ttu-id="7ecaf-140">建立預測</span><span class="sxs-lookup"><span data-stu-id="7ecaf-140">Creating Predictions</span></span>  
 <span data-ttu-id="7ecaf-141">在模型定型之後，您可以針對模型內容建立查詢以取得迴歸係數和其他詳細資料，也可以使用模型來進行預測。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-141">After the model has been trained, you can create queries against the model content to get the regression coefficients and other details, or you can use the model to make predictions.</span></span>  
  
-   <span data-ttu-id="7ecaf-142">如需如何針對資料採礦模型建立查詢的一般資訊，請參閱 [資料採礦查詢](data-mining-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-142">For general information about how to create queries against a data mining model, see [Data Mining Queries](data-mining-queries.md).</span></span>  
  
-   <span data-ttu-id="7ecaf-143">如需羅吉斯迴歸模型使用之查詢的範例，請參閱 [叢集模型查詢範例](clustering-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-143">For examples of queries on a logistic regression model, see [Clustering Model Query Examples](clustering-model-query-examples.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ecaf-144">備註</span><span class="sxs-lookup"><span data-stu-id="7ecaf-144">Remarks</span></span>  
  
-   <span data-ttu-id="7ecaf-145">不支援鑽研。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-145">Does not support drillthrough.</span></span> <span data-ttu-id="7ecaf-146">這是因為採礦模型中的節點結構不一定會直接對應至基礎資料。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-146">This is because the structure of nodes in the mining model does not necessarily correspond directly to the underlying data.</span></span>  
  
-   <span data-ttu-id="7ecaf-147">不支援建立資料採礦維度。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-147">Does not support the creation of data mining dimensions.</span></span>  
  
-   <span data-ttu-id="7ecaf-148">支援 OLAP 採礦模型的使用。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-148">Supports the use of OLAP mining models.</span></span>  
  
-   <span data-ttu-id="7ecaf-149">不支援使用預測模型標記語言 (PMML) 來建立採礦模型。</span><span class="sxs-lookup"><span data-stu-id="7ecaf-149">Does not support the use of Predictive Model Markup Language (PMML) to create mining models.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ecaf-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7ecaf-150">See Also</span></span>  
 <span data-ttu-id="7ecaf-151">[羅吉斯回歸模型的採礦模型內容 &#40;Analysis Services 資料採礦&#41;](mining-model-content-for-logistic-regression-models.md) </span><span class="sxs-lookup"><span data-stu-id="7ecaf-151">[Mining Model Content for Logistic Regression Models &#40;Analysis Services - Data Mining&#41;](mining-model-content-for-logistic-regression-models.md) </span></span>  
 <span data-ttu-id="7ecaf-152">[Microsoft 羅吉斯回歸演算法技術參考](microsoft-logistic-regression-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="7ecaf-152">[Microsoft Logistic Regression Algorithm Technical Reference](microsoft-logistic-regression-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="7ecaf-153">羅吉斯迴歸模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="7ecaf-153">Logistic Regression Model Query Examples</span></span>](logistic-regression-model-query-examples.md)  
  
  
