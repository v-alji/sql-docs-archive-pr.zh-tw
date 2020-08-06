---
title: '[交叉驗證] 索引標籤 () 的挖掘精確度圖表視圖 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.accuracychart.crossvalidation.f1
ms.assetid: bd215a68-1ad7-4046-9c44-ec8e2be13a64
author: minewiskan
ms.author: owend
ms.openlocfilehash: 867bd6d1abffb29ec3eb2a8a78e562e5cbcc5b29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594860"
---
# <a name="cross-validation-tab-mining-accuracy-chart-view"></a><span data-ttu-id="f7059-102">交叉驗證索引標籤 (採礦精確度圖表檢視)</span><span class="sxs-lookup"><span data-stu-id="f7059-102">Cross-Validation Tab (Mining Accuracy Chart View)</span></span>
  <span data-ttu-id="f7059-103">交叉驗證可讓您將採礦結構資料分割成交叉區段，並反覆地針對每個交叉區段培訓和測試模型。</span><span class="sxs-lookup"><span data-stu-id="f7059-103">Cross-validation lets you partition a mining structure into cross-sections and iteratively train and test models against each cross-section.</span></span> <span data-ttu-id="f7059-104">您會指定數個將資料分割成的折疊，然後使用每個折疊當做測試資料，而剩餘的資料則用來定型新模型。</span><span class="sxs-lookup"><span data-stu-id="f7059-104">You specify a number of folds to divide the data into, and each fold is used in turn as the test data, whereas the remaining data is used to train a new model.</span></span> <span data-ttu-id="f7059-105">然後 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 接著會針對每個模型產生一組標準精確度度量。</span><span class="sxs-lookup"><span data-stu-id="f7059-105">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] then generates a set of standard accuracy metrics for each model.</span></span> <span data-ttu-id="f7059-106">藉由比較針對每個交叉區段所產生的模型標準，您可以充分了解採礦模型對整個資料集而言有多可靠。</span><span class="sxs-lookup"><span data-stu-id="f7059-106">By comparing the metrics for the models generated for each cross-section, you can get a good idea of how reliable the mining model is for the whole data set.</span></span>  
  
 <span data-ttu-id="f7059-107">如需詳細資訊，請參閱[交叉驗證 &#40;Analysis Services - 資料採礦&#41;](data-mining/cross-validation-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="f7059-107">For more information, see [Cross-Validation &#40;Analysis Services - Data Mining&#41;](data-mining/cross-validation-analysis-services-data-mining.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7059-108">交叉驗證無法用於使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 時間序列演算法或 [!INCLUDE[msCoName](../includes/msconame-md.md)] 時序叢集演算法所建立的模型。</span><span class="sxs-lookup"><span data-stu-id="f7059-108">Cross-validation cannot be used with models that were built by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm or the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span> <span data-ttu-id="f7059-109">如果在包含上述類型之模型的採礦結構上執行報表，則報表中不會包含模型。</span><span class="sxs-lookup"><span data-stu-id="f7059-109">If you run the report on a mining structure that contains these types of models, the models will not be included in the report.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="f7059-110">工作清單</span><span class="sxs-lookup"><span data-stu-id="f7059-110">Task List</span></span>  
  
-   <span data-ttu-id="f7059-111">指定摺疊數。</span><span class="sxs-lookup"><span data-stu-id="f7059-111">Specify the number of folds.</span></span>  
  
-   <span data-ttu-id="f7059-112">指定用於交叉驗證的最大案例數目。</span><span class="sxs-lookup"><span data-stu-id="f7059-112">Specify the maximum number of cases to use for cross-validation.</span></span>  
  
-   <span data-ttu-id="f7059-113">指定可預測的資料行。</span><span class="sxs-lookup"><span data-stu-id="f7059-113">Specify the predictable column.</span></span>  
  
-   <span data-ttu-id="f7059-114">選擇性地指定可預測的狀態。</span><span class="sxs-lookup"><span data-stu-id="f7059-114">Optionally, specify a predictable state.</span></span>  
  
-   <span data-ttu-id="f7059-115">選擇性地設定參數以控制預測精確度的評估方式。</span><span class="sxs-lookup"><span data-stu-id="f7059-115">Optionally, set parameters that control how the accuracy of prediction is assessed.</span></span>  
  
-   <span data-ttu-id="f7059-116">按一下 [取得結果]\*\*\*\* 以顯示交叉驗證的結果。</span><span class="sxs-lookup"><span data-stu-id="f7059-116">Click **Get Results** to display the results of cross-validation.</span></span>  
  
## <a name="ui-element-list"></a><span data-ttu-id="f7059-117">UI 元素清單</span><span class="sxs-lookup"><span data-stu-id="f7059-117">UI element list</span></span>  
 <span data-ttu-id="f7059-118">**折迭計數**</span><span class="sxs-lookup"><span data-stu-id="f7059-118">**Fold Count**</span></span>  
 <span data-ttu-id="f7059-119">指定要建立之摺疊或資料分割的數目。</span><span class="sxs-lookup"><span data-stu-id="f7059-119">Specify the number of folds, or partitions, to create.</span></span> <span data-ttu-id="f7059-120">最小值為 2，代表半數的資料集用於測試，半數用於培訓。</span><span class="sxs-lookup"><span data-stu-id="f7059-120">The minimum value is 2, meaning that half the data set is used for testing and half for training.</span></span>  
  
 <span data-ttu-id="f7059-121">工作階段採礦結構的最大值為 10。</span><span class="sxs-lookup"><span data-stu-id="f7059-121">The maximum value is 10 for session mining structures.</span></span>  
  
 <span data-ttu-id="f7059-122">如果採礦結構儲存於 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的執行個體，則最大值為 256。</span><span class="sxs-lookup"><span data-stu-id="f7059-122">The maximum value is 256 if the mining structure is stored in an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7059-123">隨著摺疊數增加，執行交叉驗證所需的時間同樣會增加 n。</span><span class="sxs-lookup"><span data-stu-id="f7059-123">As you increase the number of folds, the time that is required to perform cross-validation similarly increases by n.</span></span> <span data-ttu-id="f7059-124">如果案例數目很大，[摺疊計數]\*\*\*\* 的值也很大時，可能會發生效能問題。</span><span class="sxs-lookup"><span data-stu-id="f7059-124">You might experience performance issues if the number of cases is large and the value of **Fold Count** is also large.</span></span>  
  
 <span data-ttu-id="f7059-125">**最大案例數**</span><span class="sxs-lookup"><span data-stu-id="f7059-125">**Max Cases**</span></span>  
 <span data-ttu-id="f7059-126">指定用於交叉驗證的最大案例數目。</span><span class="sxs-lookup"><span data-stu-id="f7059-126">Specify the maximum number of cases to use for cross-validation.</span></span> <span data-ttu-id="f7059-127">任何特定摺疊中的案例數都與 [最大案例數]\*\*\*\* 值除以 [摺疊計數]\*\*\*\* 值相同。</span><span class="sxs-lookup"><span data-stu-id="f7059-127">The number of cases in any particular fold is equal to the **Max Cases** value divided by the **Fold Count** value.</span></span>  
  
 <span data-ttu-id="f7059-128">如果使用 **0**，則來源資料中的所有案例都會用來進行交叉驗證。</span><span class="sxs-lookup"><span data-stu-id="f7059-128">If you use **0**, all cases in the source data are used for cross-validation.</span></span>  
  
 <span data-ttu-id="f7059-129">沒有任何預設值。</span><span class="sxs-lookup"><span data-stu-id="f7059-129">There is no default value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7059-130">如果增加案例數，則處理時間也會增加。</span><span class="sxs-lookup"><span data-stu-id="f7059-130">As you increase the number of cases, processing time also increases.</span></span>  
  
 <span data-ttu-id="f7059-131">**目標屬性**</span><span class="sxs-lookup"><span data-stu-id="f7059-131">**Target Attribute**</span></span>  
 <span data-ttu-id="f7059-132">從所有模型中的可預測資料行清單選取資料行。</span><span class="sxs-lookup"><span data-stu-id="f7059-132">Select a column from the list of predictable columns found in all models.</span></span> <span data-ttu-id="f7059-133">每次在執行交叉驗證時只能選取一個可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="f7059-133">You can only select one predictable column every time that you perform cross-validation.</span></span>  
  
 <span data-ttu-id="f7059-134">若僅要測試叢集模型，請選取 [叢集]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f7059-134">To test only clustering models, select **Cluster**.</span></span>  
  
 <span data-ttu-id="f7059-135">**目標狀態**</span><span class="sxs-lookup"><span data-stu-id="f7059-135">**Target State**</span></span>  
 <span data-ttu-id="f7059-136">輸入值，或從下拉式的值清單選取目標值。</span><span class="sxs-lookup"><span data-stu-id="f7059-136">Type a value, or select a target value from a drop-down list of values.</span></span>  
  
 <span data-ttu-id="f7059-137">預設值為 `null`，表示要測試所有狀態。</span><span class="sxs-lookup"><span data-stu-id="f7059-137">The default value is `null`, indicating that all states are to be tested.</span></span>  
  
 <span data-ttu-id="f7059-138">已停用於叢集模型。</span><span class="sxs-lookup"><span data-stu-id="f7059-138">Disabled for clustering models.</span></span>  
  
 <span data-ttu-id="f7059-139">**目標**  **閾值**</span><span class="sxs-lookup"><span data-stu-id="f7059-139">**Target**  **Threshold**</span></span>  
 <span data-ttu-id="f7059-140">指定 0 和 1 之間代表預測機率的值，高於該值的預測狀態會被視為正確。</span><span class="sxs-lookup"><span data-stu-id="f7059-140">Specify a value between 0 and 1 that indicates the prediction probability above which a predicted state is considered to be correct.</span></span> <span data-ttu-id="f7059-141">可以用 0.1 的增量設定此值。</span><span class="sxs-lookup"><span data-stu-id="f7059-141">The value can be set in 0.1 increments.</span></span>  
  
 <span data-ttu-id="f7059-142">預設值是 `null`，代表會將最可能的預測計為正確。</span><span class="sxs-lookup"><span data-stu-id="f7059-142">The default is `null`, indicating that the most probable prediction is counted as correct.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f7059-143">雖然可以將此值設定為 0.0，但使用此值會增加處理時間且不會產生有意義的結果。</span><span class="sxs-lookup"><span data-stu-id="f7059-143">Although you can set the value to 0.0, using this value will increase processing time and not yield meaningful results.</span></span>  
  
 <span data-ttu-id="f7059-144">**取得結果**</span><span class="sxs-lookup"><span data-stu-id="f7059-144">**Get Results**</span></span>  
 <span data-ttu-id="f7059-145">按一下即可使用指定的參數開始對模型進行交叉驗證。</span><span class="sxs-lookup"><span data-stu-id="f7059-145">Click to begin cross-validation of the model using the specified parameters.</span></span>  
  
 <span data-ttu-id="f7059-146">模型會資料分割成指定的摺疊數，且針對每個折疊測試個別的模型。</span><span class="sxs-lookup"><span data-stu-id="f7059-146">The model is partitioned into the specified number of folds and a separate model is tested for each fold.</span></span> <span data-ttu-id="f7059-147">因此，交叉驗證可能要花一些時間才能傳回結果。</span><span class="sxs-lookup"><span data-stu-id="f7059-147">Therefore, it might take some time for cross-validation to return the results.</span></span>  
  
 <span data-ttu-id="f7059-148">如需如何解譯交叉驗證報表結果的詳細資訊，請參閱 [交叉驗證報表中的量值](data-mining/measures-in-the-cross-validation-report.md)。</span><span class="sxs-lookup"><span data-stu-id="f7059-148">For more information about how to interpret the results of the cross-validation report, see [Measures in the Cross-Validation Report](data-mining/measures-in-the-cross-validation-report.md).</span></span>  
  
## <a name="setting-the-accuracy-threshold"></a><span data-ttu-id="f7059-149">設定精確度臨界值</span><span class="sxs-lookup"><span data-stu-id="f7059-149">Setting the Accuracy Threshold</span></span>  
 <span data-ttu-id="f7059-150">您可以藉由設定 [目標臨界值]\*\*\*\* \*\*\*\* 的值來控制預測精確度的測量標準。</span><span class="sxs-lookup"><span data-stu-id="f7059-150">You can control the standard for measuring prediction accuracy by setting a value for **Target** **Threshold**.</span></span> <span data-ttu-id="f7059-151">臨界值代表一種精確度列。</span><span class="sxs-lookup"><span data-stu-id="f7059-151">A threshold represents a kind of accuracy bar.</span></span> <span data-ttu-id="f7059-152">每個預測都會被指派預測值正確的機率。</span><span class="sxs-lookup"><span data-stu-id="f7059-152">Each prediction is assigned a probability that the predicted value is correct.</span></span> <span data-ttu-id="f7059-153">因此，如果將 [目標臨界值]\*\*\*\* \*\*\*\* 的值設定為接近 1，則任何特定預測的機率必須相當高才會計為良好的預測。</span><span class="sxs-lookup"><span data-stu-id="f7059-153">Therefore, if you set the **Target** **Threshold** value closer to 1, you are requiring that the probability for any particular prediction to be fairly high to be counted as a good prediction.</span></span> <span data-ttu-id="f7059-154">相反地，如果將 [目標臨界值]\*\*\*\* \*\*\*\* 的值設定為接近 0，則即使具有較低機率值的預測也會計為「良好」的預測。</span><span class="sxs-lookup"><span data-stu-id="f7059-154">Conversely, if you set **Target** **Threshold** closer to 0, even predictions with lower probability values are counted as "good" predictions.</span></span>  
  
 <span data-ttu-id="f7059-155">我們不推薦任何臨界值，因為預測的機率是根據資料量及進行的預測類型而定。</span><span class="sxs-lookup"><span data-stu-id="f7059-155">There is no recommended threshold value because the probability of any prediction depends on the amount of data and the type of prediction you are making.</span></span> <span data-ttu-id="f7059-156">您應該以不同的機率層級檢閱一些預測，如此才能為資料判斷適當的精確度列。</span><span class="sxs-lookup"><span data-stu-id="f7059-156">You should review some predictions at different probability levels to determine an appropriate accuracy bar for your data.</span></span> <span data-ttu-id="f7059-157">這項作業很重要，因為您為 [目標臨界值]\*\*\*\* \*\*\*\* 所設定的值會影響測量到的模型精確度。</span><span class="sxs-lookup"><span data-stu-id="f7059-157">It is important that you do this, because the value that you set for **Target** **Threshold** affects the measured accuracy of the model.</span></span>  
  
 <span data-ttu-id="f7059-158">例如，假設針對特定的目標狀態進行了三項預測，而每項預測的機率分別為 0.05、0.15 和 0.8。</span><span class="sxs-lookup"><span data-stu-id="f7059-158">For example, suppose three predictions are made for a particular target state, and the probabilities of each prediction are 0.05, 0.15, and 0.8.</span></span> <span data-ttu-id="f7059-159">如果將臨界值設定為 0.5，只有一項預測會計為正確。</span><span class="sxs-lookup"><span data-stu-id="f7059-159">If you set the threshold to 0.5, only one prediction is counted as being correct.</span></span> <span data-ttu-id="f7059-160">如果您將 [目標臨界值]\*\*\*\* \*\*\*\* 設定為 0.10，其中兩項預測就會計為正確。</span><span class="sxs-lookup"><span data-stu-id="f7059-160">If you set **Target** **Threshold** to 0.10, two predictions are counted as being correct.</span></span>  
  
 <span data-ttu-id="f7059-161">當 [**目標\*\*\*\*臨界**值] 設定為 `null` （預設值）時，會將每個案例最可能的預測計為正確。</span><span class="sxs-lookup"><span data-stu-id="f7059-161">When **Target** **Threshold** is set to `null`, which is the default value, the most probable prediction for each case is counted as correct.</span></span> <span data-ttu-id="f7059-162">在剛剛提及的範例中，0.05、0.15 和 0.8 是三個不同案例的預測機率。</span><span class="sxs-lookup"><span data-stu-id="f7059-162">In the example just cited, 0.05, 0.15, and 0.8 are the probabilities for predictions in three different cases.</span></span> <span data-ttu-id="f7059-163">雖然機率非常不同，但每項預測都會被視為正確，因為每個案例都只會產生一項預測，而這些都是這些案例的最佳預測。</span><span class="sxs-lookup"><span data-stu-id="f7059-163">Although the probabilities are very different, each prediction would be counted as correct, because each case generates only one prediction and these are the best predictions for these cases.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7059-164">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7059-164">See Also</span></span>  
 <span data-ttu-id="f7059-165">[測試和驗證 &#40;資料採礦&#41;](data-mining/testing-and-validation-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="f7059-165">[Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md) </span></span>  
 <span data-ttu-id="f7059-166">[交叉驗證 &#40;Analysis Services-資料採礦&#41;](data-mining/cross-validation-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="f7059-166">[Cross-Validation &#40;Analysis Services - Data Mining&#41;](data-mining/cross-validation-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="f7059-167">[交叉驗證報表中的量值](data-mining/measures-in-the-cross-validation-report.md) </span><span class="sxs-lookup"><span data-stu-id="f7059-167">[Measures in the Cross-Validation Report](data-mining/measures-in-the-cross-validation-report.md) </span></span>  
 [<span data-ttu-id="f7059-168">資料採礦預存程序 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="f7059-168">Data Mining Stored Procedures &#40;Analysis Services - Data Mining&#41;</span></span>](/sql/analysis-services/data-mining/data-mining-stored-procedures-analysis-services-data-mining)  
  
  
