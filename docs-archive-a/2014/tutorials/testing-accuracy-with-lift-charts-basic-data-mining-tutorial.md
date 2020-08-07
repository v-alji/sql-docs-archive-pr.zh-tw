---
title: 使用增益圖測試精確度 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 822d414b-4a39-473f-80c3-53476e30655a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7a3dcdd1d1b78911f5ffd37a383532abdd4814c3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703469"
---
# <a name="testing-accuracy-with-lift-charts-basic-data-mining-tutorial"></a><span data-ttu-id="72008-102">使用增益圖測試精確度 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="72008-102">Testing Accuracy with Lift Charts (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="72008-103">在資料採礦設計師的 [**挖掘精確度圖表**] 索引標籤上，您可以計算每個模型進行預測的程度，並將每個模型的結果與其他模型的結果直接比較。</span><span class="sxs-lookup"><span data-stu-id="72008-103">On the **Mining Accuracy Chart** tab of Data Mining Designer, you can calculate how well each of your models makes predictions, and compare the results of each model directly against the results of the other models.</span></span> <span data-ttu-id="72008-104">這種比較方法稱為增益*圖*。</span><span class="sxs-lookup"><span data-stu-id="72008-104">This method of comparison is referred to as a *lift chart*.</span></span> <span data-ttu-id="72008-105">一般來說，採礦模型的預測精確度是由「增益」(Lift) 或分類精確度所衡量。</span><span class="sxs-lookup"><span data-stu-id="72008-105">Typically, the predictive accuracy of a mining model is measured by either lift or classification accuracy.</span></span> <span data-ttu-id="72008-106">在此教學課程中，我們只會使用增益圖。</span><span class="sxs-lookup"><span data-stu-id="72008-106">For this tutorial we will use the lift chart only.</span></span>  
  
 <span data-ttu-id="72008-107">本主題中，您將會執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="72008-107">In this topic, you will perform the following tasks:</span></span>  
  
-   [<span data-ttu-id="72008-108">選擇輸入資料</span><span class="sxs-lookup"><span data-stu-id="72008-108">Choose the Input Data</span></span>](#BKMK_InputData)  
  
-   [<span data-ttu-id="72008-109">設定精確度圖表參數</span><span class="sxs-lookup"><span data-stu-id="72008-109">Configure Accuracy Chart Parameters</span></span>](#BKMK_Selecting)  
  
##  <a name="choosing-the-input-data"></a><a name="BKMK_InputData"></a><span data-ttu-id="72008-110">選擇輸入資料</span><span class="sxs-lookup"><span data-stu-id="72008-110">Choosing the Input Data</span></span>  
 <span data-ttu-id="72008-111">若要測試採礦模型的精確度，第一個步驟就是要選取您將用於測試的資料來源。</span><span class="sxs-lookup"><span data-stu-id="72008-111">The first step in testing the accuracy of your mining models is to select the data source that you will use for testing.</span></span> <span data-ttu-id="72008-112">您將會對照測試資料來測試模型的執行效果，然後搭配外部資料來使用模型。</span><span class="sxs-lookup"><span data-stu-id="72008-112">You will test how well the models perform against your testing data and then you will use them with external data.</span></span>  
  
#### <a name="to-select-the-data-set"></a><span data-ttu-id="72008-113">若要選取資料集</span><span class="sxs-lookup"><span data-stu-id="72008-113">To select the data set</span></span>  
  
1.  <span data-ttu-id="72008-114">在的資料採礦設計師中，切換至 [**挖掘精確度圖表**] 索引標籤 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，然後選取 [**輸入選擇**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="72008-114">Switch to the **Mining Accuracy Chart** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] and select the **Input Selection** tab.</span></span>  
  
2.  <span data-ttu-id="72008-115">在 [**選取要用於精確度圖表的資料集**] 群組方塊中，選取 [**使用採礦結構測試案例**]。</span><span class="sxs-lookup"><span data-stu-id="72008-115">In the **Select data set to be used for Accuracy Chart** group box, select **Use mining structure test cases**.</span></span> <span data-ttu-id="72008-116">這是您在建立採礦結構時擱置在一旁的測試資料。</span><span class="sxs-lookup"><span data-stu-id="72008-116">This is the testing data that you set aside when you created the mining structure.</span></span>  
  
     <span data-ttu-id="72008-117">如需其他選項的詳細資訊，請參閱[選擇精確度圖表類型和設定圖表選項](../../2014/analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md)。</span><span class="sxs-lookup"><span data-stu-id="72008-117">For more information on the other options, see [Choose an Accuracy Chart Type and Set Chart Options](../../2014/analysis-services/data-mining/choose-an-accuracy-chart-type-and-set-chart-options.md).</span></span>  
  
##  <a name="setting-accuracy-chart-parameters"></a><a name="BKMK_Selecting"></a><span data-ttu-id="72008-118">設定精確度圖表參數</span><span class="sxs-lookup"><span data-stu-id="72008-118">Setting Accuracy Chart Parameters</span></span>  
 <span data-ttu-id="72008-119">若要建立精確度圖表，您必須定義三件事：</span><span class="sxs-lookup"><span data-stu-id="72008-119">To create an accuracy chart, you must define three things:</span></span>  
  
-   <span data-ttu-id="72008-120">精確度圖表中應該納入哪些模型？</span><span class="sxs-lookup"><span data-stu-id="72008-120">Which models should you include in the accuracy chart?</span></span>  
  
-   <span data-ttu-id="72008-121">您要測量哪些可預測屬性？</span><span class="sxs-lookup"><span data-stu-id="72008-121">Which predictable attribute do you want to measure?</span></span> <span data-ttu-id="72008-122">某些模型可能會有多個目標，但是每個圖表一次只能測量一項結果。</span><span class="sxs-lookup"><span data-stu-id="72008-122">Some models might have multiple targets, but each chart can measure only one outcome at a time.</span></span>  
  
     <span data-ttu-id="72008-123">若要使用資料行做為精確度圖表中的**可預測資料行名稱**，這些資料行的使用類型必須是 `Predict` 或 `Predict Only` 。</span><span class="sxs-lookup"><span data-stu-id="72008-123">To use a column as the **Predictable Column Name** in an accuracy chart, the columns must have the usage type of `Predict` or `Predict Only`.</span></span> <span data-ttu-id="72008-124">此外，目標資料行的內容類型必須為 `Discrete` 或 `Discretized`。</span><span class="sxs-lookup"><span data-stu-id="72008-124">Also, the content type of the target column must be either `Discrete` or `Discretized`.</span></span> <span data-ttu-id="72008-125">換句話說，您無法使用增益圖測量連續數值輸出的精確度。</span><span class="sxs-lookup"><span data-stu-id="72008-125">In other words, you cannot measure accuracy against continuous numeric outputs using the lift chart.</span></span>  
  
-   <span data-ttu-id="72008-126">您要測量模型的一般精確度，或其預測特定值的精確度 (例如 [自行車購買者] = [是] ) </span><span class="sxs-lookup"><span data-stu-id="72008-126">Do you want to measure the model's general accuracy, or its accuracy  in predicting a particular value (such as [Bike Buyer] = 'Yes')</span></span>  
  
#### <a name="to-generate-the-lift-chart"></a><span data-ttu-id="72008-127">產生增益圖</span><span class="sxs-lookup"><span data-stu-id="72008-127">To generate the lift chart</span></span>  
  
1.  <span data-ttu-id="72008-128">在資料採礦設計師的 [**輸入選擇**] 索引標籤上，于 [**選取可預測的採礦模型資料行以顯示在增益圖中**] 底下，選取 [**同步處理預測資料行和值**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="72008-128">On the **Input Selection** tab of Data Mining Designer, under **Select predictable mining model columns to show in the lift chart**, select the checkbox for **Synchronize Prediction Columns and Values**.</span></span>  
  
2.  <span data-ttu-id="72008-129">在 [**可預測的資料行名稱**] 資料行中，確認已為每個模型選取 [**自行車購買**者]。</span><span class="sxs-lookup"><span data-stu-id="72008-129">In the **Predictable Column Name** column, verify that **Bike Buyer** is selected for each model.</span></span>  
  
3.  <span data-ttu-id="72008-130">在 [**顯示**] 資料行中，選取每個模型。</span><span class="sxs-lookup"><span data-stu-id="72008-130">In the **Show** column, select each of the models.</span></span>  
  
     <span data-ttu-id="72008-131">依預設，會選取採礦結構中所有的模型。</span><span class="sxs-lookup"><span data-stu-id="72008-131">By default, all the models in the mining structure are selected.</span></span> <span data-ttu-id="72008-132">您可以決定不加入某個模型，但在本教學課程中，則是維持選取所有模型。</span><span class="sxs-lookup"><span data-stu-id="72008-132">You can decide not to include a model, but for this tutorial leave all the models selected.</span></span>  
  
4.  <span data-ttu-id="72008-133">在 [**預測值**] 資料行中，選取 [ **1**]。</span><span class="sxs-lookup"><span data-stu-id="72008-133">In the **Predict Value** column, select **1**.</span></span> <span data-ttu-id="72008-134">系統會針對具有相同可預測資料行的每個模型，自動填入相同的值。</span><span class="sxs-lookup"><span data-stu-id="72008-134">The same value is automatically filled in for each model that has the same predictable column.</span></span>  
  
5.  <span data-ttu-id="72008-135">選取 [增益**圖**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="72008-135">Select the **Lift Chart** tab.</span></span>  
  
     <span data-ttu-id="72008-136">當您按一下此索引標籤時，預測查詢會隨即執行以取得測試資料的預測，且結果將與已知值做比較。</span><span class="sxs-lookup"><span data-stu-id="72008-136">When you click the tab, a prediction query is executed to get predictions for the test data, and the results are compared against the known values.</span></span> <span data-ttu-id="72008-137">結果會繪製在圖形上。</span><span class="sxs-lookup"><span data-stu-id="72008-137">The results are plotted on the graph.</span></span>  
  
     <span data-ttu-id="72008-138">如果您使用 [**預測值**] 選項來指定特定的目標結果，增益圖就會繪製隨機猜測的結果和理想模型的結果。</span><span class="sxs-lookup"><span data-stu-id="72008-138">If you specified a particular target outcome using the **Predict Value** option, the lift chart plots the results of random guesses and the results of an ideal model.</span></span>  
  
    -   <span data-ttu-id="72008-139">隨機猜測線條將顯示模型在沒有使用任何資料做預測時的精確度：即兩項結果彼此間為 50-50 均分。</span><span class="sxs-lookup"><span data-stu-id="72008-139">The random guess line shows how accurate the model would be without using any data to inform its predictions: that is, a 50-50 split between two outcomes.</span></span> <span data-ttu-id="72008-140">增益圖可協助您從視覺上了解模型的執行效益與隨機猜測相比高出多少。</span><span class="sxs-lookup"><span data-stu-id="72008-140">The lift chart helps you visualize how much better your model performs in comparison to a random guess.</span></span>  
  
    -   <span data-ttu-id="72008-141">理想模型線條代表精確度的上限。</span><span class="sxs-lookup"><span data-stu-id="72008-141">The ideal model line represents the upper bound of accuracy.</span></span> <span data-ttu-id="72008-142">此線條顯示了當模型始終都能準確預測時，可能達到的最大效益。</span><span class="sxs-lookup"><span data-stu-id="72008-142">It shows you the maximum possible benefit you could achieve if your model always predicted accurately.</span></span>  
  
     <span data-ttu-id="72008-143">您所建立的採礦模型通常會介於這兩種極端之間。</span><span class="sxs-lookup"><span data-stu-id="72008-143">The mining models you created will usually fall between these two extremes.</span></span> <span data-ttu-id="72008-144">隨機猜測的任何改進*都會被視為增益。*</span><span class="sxs-lookup"><span data-stu-id="72008-144">Any improvement from the random guess is considered to be *lift*.</span></span>  
  
6.  <span data-ttu-id="72008-145">使用圖例可找出代表理想的模型與隨機猜測模型的有色線條。</span><span class="sxs-lookup"><span data-stu-id="72008-145">Use the legend to locate the colored lines representing the Ideal Model and the Random Guess Model.</span></span>  
  
     <span data-ttu-id="72008-146">您會發現 `TM_Decision_Tree` 模型提供最大增益，同時其效果優於群集和貝氏貝氏機率分類模型。</span><span class="sxs-lookup"><span data-stu-id="72008-146">You'll notice that the `TM_Decision_Tree` model provides the greatest lift,  outperforming both the Clustering and Naive Bayes models.</span></span>  
  
 <span data-ttu-id="72008-147">如需類似于此課程中所建立之增益圖的深入說明，請參閱增益[圖 &#40;Analysis Services-資料採礦&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="72008-147">For an in-depth explanation of a lift chart similar to the one created in this lesson, see [Lift Chart &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="72008-148">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="72008-148">Next Task in Lesson</span></span>  
 [<span data-ttu-id="72008-149">&#40;基本資料採礦教學課程中測試篩選過的模型&#41;</span><span class="sxs-lookup"><span data-stu-id="72008-149">Testing a Filtered Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="72008-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72008-150">See Also</span></span>  
 <span data-ttu-id="72008-151">[增益圖 &#40;Analysis Services-資料採礦&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="72008-151">[Lift Chart &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="72008-152">[增益圖索引標籤 &#40;&#41;的 [挖掘準確度] 圖表視圖](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)</span><span class="sxs-lookup"><span data-stu-id="72008-152">[Lift Chart Tab &#40;Mining Accuracy Chart View&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md)</span></span>  
  
  
