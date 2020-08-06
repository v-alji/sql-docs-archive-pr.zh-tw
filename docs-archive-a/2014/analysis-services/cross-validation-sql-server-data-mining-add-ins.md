---
title: SQL Server 資料採礦增益集的交叉驗證 () |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cross-validation
- partitioning data [data mining]
- mining models, testing
ms.assetid: bf9483b3-4099-41c4-bbc5-da7005e07bcd
author: minewiskan
ms.author: owend
ms.openlocfilehash: a615de9d20106041f2f01e9912928b64597bc895
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594862"
---
# <a name="cross-validation-sql-server-data-mining-add-ins"></a><span data-ttu-id="8ff15-102">交叉驗證 (SQL Server 資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="8ff15-102">Cross-Validation (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="8ff15-103">![資料採礦功能區中的交叉驗證按鈕](media/dmc-xvalid.gif "資料採礦功能區中的交叉驗證按鈕")</span><span class="sxs-lookup"><span data-stu-id="8ff15-103">![Cross-Validation button, Data Mining ribbon](media/dmc-xvalid.gif "Cross-Validation button, Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="8ff15-104">交叉驗證是一項標準分析工具，而且它是協助您開發並微調資料採礦模型的重要功能。</span><span class="sxs-lookup"><span data-stu-id="8ff15-104">Cross-validation is a standard tool in analytics and is an important feature for helping you develop and fine-tune data mining models.</span></span> <span data-ttu-id="8ff15-105">在您建立了採礦模型之後，就可以使用交叉驗證來確定模型的有效性，並在建立相關的採礦模型之後，比較彼此的結果。</span><span class="sxs-lookup"><span data-stu-id="8ff15-105">You use cross-validation after you have created a mining model to ascertain the validity of the model and to compare its results with other, related mining models.</span></span>  
  
 <span data-ttu-id="8ff15-106">交叉驗證包含兩個階段：定型和產生報表。</span><span class="sxs-lookup"><span data-stu-id="8ff15-106">Cross-validation consists of two phases: training and report generation.</span></span> <span data-ttu-id="8ff15-107">您將完成下列步驟：</span><span class="sxs-lookup"><span data-stu-id="8ff15-107">You will complete the following steps:</span></span>  
  
-   <span data-ttu-id="8ff15-108">選取目標採礦結果或採礦模型。</span><span class="sxs-lookup"><span data-stu-id="8ff15-108">Select a target mining structure or mining model.</span></span>  
  
-   <span data-ttu-id="8ff15-109">指定目標值 (如果適用)。</span><span class="sxs-lookup"><span data-stu-id="8ff15-109">Specify the target value if applicable.</span></span>  
  
-   <span data-ttu-id="8ff15-110">指定分割結構資料的交叉*區段或折*迭數目。</span><span class="sxs-lookup"><span data-stu-id="8ff15-110">Specify the number of cross-sections, or *folds*, into which to partition the structure data.</span></span>  
  
 <span data-ttu-id="8ff15-111">**交叉驗證**的 wizard 接著會在每個折迭上建立新的模型，在另一個折迭上測試模型，然後報告模型的精確度。</span><span class="sxs-lookup"><span data-stu-id="8ff15-111">The **Cross-Validation** wizard then creates a new model on each of the folds, tests the model on the other folds, and then reports the accuracy of the model.</span></span> <span data-ttu-id="8ff15-112">完成時，**交叉驗證**嚮導會建立一個報表，其中會顯示每個折迭的計量，並提供匯總中模型的摘要。</span><span class="sxs-lookup"><span data-stu-id="8ff15-112">Upon completion, the **Cross-Validation** wizard creates a report that shows you the metrics for each fold, and provides a summary of the model in aggregate.</span></span> <span data-ttu-id="8ff15-113">這項資訊可用於判斷基礎資料對於模型的良好程度，或者用於比較根據相同資料建立的不同模型。</span><span class="sxs-lookup"><span data-stu-id="8ff15-113">This information can be used to determine how good the underlying data is for a model, or to compare different models that are built on the same data.</span></span>  
  
## <a name="using-the-cross-validation-wizard"></a><span data-ttu-id="8ff15-114">使用交叉驗證精靈</span><span class="sxs-lookup"><span data-stu-id="8ff15-114">Using the Cross-Validation Wizard</span></span>  
 <span data-ttu-id="8ff15-115">您可以針對暫存模型與存放在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 之執行個體上的模型使用交叉驗證。</span><span class="sxs-lookup"><span data-stu-id="8ff15-115">You can use cross-validation against both temporary models and models that are stored on an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
#### <a name="to-create-a-cross-validation-report"></a><span data-ttu-id="8ff15-116">建立交叉驗證報表</span><span class="sxs-lookup"><span data-stu-id="8ff15-116">To create a cross-validation report</span></span>  
  
1.  <span data-ttu-id="8ff15-117">在 [**資料採礦**] 功能區的 [**精確度和驗證**] 群組中，按一下 [**交叉驗證**]。</span><span class="sxs-lookup"><span data-stu-id="8ff15-117">In the **Accuracy and Validation** group of the **Data Mining** ribbon, click **Cross Validation**.</span></span>  
  
2.  <span data-ttu-id="8ff15-118">在 [**選取結構或模型**] 對話方塊中，選取現有的 [採礦結構] 或 [採礦模型]。</span><span class="sxs-lookup"><span data-stu-id="8ff15-118">In the **Select Structure or Model** dialog box, select an existing mining structure or mining model.</span></span> <span data-ttu-id="8ff15-119">如果選取結構，此精靈將會針對以具有相同可預測屬性之結構為基礎的所有模型，使用交叉驗證。</span><span class="sxs-lookup"><span data-stu-id="8ff15-119">If you select a structure, the wizard will use cross-validation against all models that are based on that structure that have the same predictable attribute.</span></span> <span data-ttu-id="8ff15-120">如果選擇模型，此精靈將只會針對該模型使用交叉驗證。</span><span class="sxs-lookup"><span data-stu-id="8ff15-120">If you select a model, the wizard will use cross-validation against only that model.</span></span>  
  
3.  <span data-ttu-id="8ff15-121">在 [**指定交叉驗證參數**] 對話方塊的 [折迭**計數**] 方塊中，選擇要用來分割資料集的折迭數目。</span><span class="sxs-lookup"><span data-stu-id="8ff15-121">In the **Specify Cross-Validation Parameters** dialog box, in the **Fold Count** box, choose the number of folds among which to divide the data set.</span></span> <span data-ttu-id="8ff15-122">折疊是隨機選取的交叉資料。</span><span class="sxs-lookup"><span data-stu-id="8ff15-122">A fold is a randomly selected cross-section of the data.</span></span>  
  
4.  <span data-ttu-id="8ff15-123">（選擇性）在 [**最大資料列**數] 文字方塊中輸入數位，以設定要在交叉驗證中使用的最大資料列數目。</span><span class="sxs-lookup"><span data-stu-id="8ff15-123">Optionally, set the maximum number of rows to use in cross-validation by typing a number in the **Maximum Rows** text box.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ff15-124">您使用的資料列越多，結果將會越精確。</span><span class="sxs-lookup"><span data-stu-id="8ff15-124">The more rows that you use, the more accurate the results will be.</span></span> <span data-ttu-id="8ff15-125">不過，處理時間可能也會明顯增加。</span><span class="sxs-lookup"><span data-stu-id="8ff15-125">However, processing time might also increase significantly.</span></span> <span data-ttu-id="8ff15-126">所選擇的數目取決於資料，但一般而言，您應該在不犧牲效能的情況下，盡可能選擇最多的數目。</span><span class="sxs-lookup"><span data-stu-id="8ff15-126">The number you choose depends on your data, but in general, you should choose the highest number you can without sacrificing performance.</span></span> <span data-ttu-id="8ff15-127">若要提升效能，您也可以指定較少的折疊。</span><span class="sxs-lookup"><span data-stu-id="8ff15-127">To improve performance, you can also specify fewer folds.</span></span>  
  
5.  <span data-ttu-id="8ff15-128">從 [**目標屬性**] 下拉式清單中選取資料行。</span><span class="sxs-lookup"><span data-stu-id="8ff15-128">Select a column from the **Target Attribute** dropdown list.</span></span> <span data-ttu-id="8ff15-129">此清單只會顯示一開始建立模型時，設定為可預測屬性的資料行。</span><span class="sxs-lookup"><span data-stu-id="8ff15-129">The list displays only those columns that were configured as predictable attributes when you originally created the model.</span></span> <span data-ttu-id="8ff15-130">模型可以包含多個可預測屬性，但是您可以只選擇其中一個。</span><span class="sxs-lookup"><span data-stu-id="8ff15-130">The model may contain multiple predictable attributes, but you can choose only one.</span></span>  
  
6.  <span data-ttu-id="8ff15-131">從 [**目標狀態**] 下拉式清單中選取一個值。</span><span class="sxs-lookup"><span data-stu-id="8ff15-131">Select a value from the **Target State** dropdown list.</span></span>  
  
     <span data-ttu-id="8ff15-132">如果可預測的資料行包含連續數值資料，就無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="8ff15-132">If the predictable column contains continuous numeric data, this option is not available.</span></span>  
  
7.  <span data-ttu-id="8ff15-133">（選擇性）指定要在將預測計算為正確時作為**目標閾值**的值。</span><span class="sxs-lookup"><span data-stu-id="8ff15-133">Optionally, specify a value to use as the **Target Threshold** in counting predictions as accurate.</span></span> <span data-ttu-id="8ff15-134">這個值會以機率的方式表示，也就是介於 0 和 1 之間的數字，其中 1 表示預測保證是正確的，0 則表示預測不可能正確，而 .5 則視為隨機猜測。</span><span class="sxs-lookup"><span data-stu-id="8ff15-134">This value is expressed as a probability, which is a number between 0 and 1, where 1 means that the prediction is guaranteed to be accurate, 0 means there is no chance that the prediction is correct, and .5 is the same as a random guess.</span></span>  
  
     <span data-ttu-id="8ff15-135">如果可預測的資料行包含連續數值資料，就無法使用此選項。</span><span class="sxs-lookup"><span data-stu-id="8ff15-135">If the predictable column contains continuous numeric data, this option is not available.</span></span>  
  
8.  <span data-ttu-id="8ff15-136">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="8ff15-136">Click **Finish**.</span></span> <span data-ttu-id="8ff15-137">隨即建立新的工作表，名為**交叉驗證**。</span><span class="sxs-lookup"><span data-stu-id="8ff15-137">A new worksheet is created, named **Cross-Validation**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8ff15-138">當系統正在將模型分割為折疊，而且每個折疊都在進行測試時，Microsoft Excel 可能會暫時變成沒有回應。</span><span class="sxs-lookup"><span data-stu-id="8ff15-138">Microsoft Excel may temporarily become unresponsive while the model is being partitioned into folds and each fold is tested.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="8ff15-139">需求</span><span class="sxs-lookup"><span data-stu-id="8ff15-139">Requirements</span></span>  
 <span data-ttu-id="8ff15-140">若要建立交叉驗證報表，您必須已經建立了資料採礦結構和相關的模型。</span><span class="sxs-lookup"><span data-stu-id="8ff15-140">To create a cross-validation report, you must have already created a data mining structure and related models.</span></span> <span data-ttu-id="8ff15-141">精靈會提供一個對話方塊來協助您選擇現有的結構和模型。</span><span class="sxs-lookup"><span data-stu-id="8ff15-141">The wizard provides a dialog box to help you choose from existing structure and models.</span></span>  
  
 <span data-ttu-id="8ff15-142">如果您選擇支援多個採礦模型的採礦結構，而且模型使用不同的可預測屬性，交叉驗證精靈將會只測試共用相同可預測屬性的模型。</span><span class="sxs-lookup"><span data-stu-id="8ff15-142">If you choose a mining structure that supports multiple mining models, and the models use different predictable attributes, the Cross-Validation wizard will test only those models that share the same predictable attribute.</span></span>  
  
 <span data-ttu-id="8ff15-143">如果您選擇同時支援群集模型和其他種類模型的結構，將不會測試群集模型。</span><span class="sxs-lookup"><span data-stu-id="8ff15-143">If you choose a structure that supports both clustering models and other kinds of models, the clustering models will not be tested.</span></span>  
  
## <a name="understanding-cross-validation-results"></a><span data-ttu-id="8ff15-144">了解交叉驗證結果</span><span class="sxs-lookup"><span data-stu-id="8ff15-144">Understanding Cross-Validation Results</span></span>  
 <span data-ttu-id="8ff15-145">交叉驗證的結果會顯示在新的工作表中，標題**為的 \<attribute name> 交叉驗證報表**。</span><span class="sxs-lookup"><span data-stu-id="8ff15-145">The results of cross-validation are displayed in a new worksheet, titled **Cross-Validation Report for \<attribute name>**.</span></span> <span data-ttu-id="8ff15-146">新的工作表包含數個區段：第一個區段是摘要，提供關於經過測試之模型的重要中繼資料，讓您知道這是哪個模型或結構的結果。</span><span class="sxs-lookup"><span data-stu-id="8ff15-146">The new worksheet contains several sections: the first section is a summary that provides important metadata about the model that was tested, so that you can know which model or structure the results are for.</span></span>  
  
 <span data-ttu-id="8ff15-147">報表中的第二個區段提供統計摘要，表示原始模型的良好程度。</span><span class="sxs-lookup"><span data-stu-id="8ff15-147">The second section in the report provides a statistical summary that indicates how good the original model is.</span></span> <span data-ttu-id="8ff15-148">在此摘要中，針對每個折迭所建立的模型之間的差異會針對三個主要量值進行分析：*根平均平方誤差*、*平均絕對錯誤*和*記錄分數*。</span><span class="sxs-lookup"><span data-stu-id="8ff15-148">In this summary, the differences between the models created for each fold are analyzed for three key measures: *root mean square error*, *mean absolute error*, and *log score*.</span></span> <span data-ttu-id="8ff15-149">這些是標準的統計量值，不但可用於資料採礦，而且也可以用於大部分類型的統計分析。</span><span class="sxs-lookup"><span data-stu-id="8ff15-149">These are standard statistical measures used not only in data mining but also in most kinds of statistical analysis.</span></span>  
  
 <span data-ttu-id="8ff15-150">整體來說，交叉驗證精靈會針對這些每個量值，透過模型計算平均和標準差。</span><span class="sxs-lookup"><span data-stu-id="8ff15-150">For each of these measures, the Cross-Validation wizard calculates the mean and standard deviation across the model as a whole.</span></span> <span data-ttu-id="8ff15-151">這會告訴您在不同的資料子集上進行預測時，模型一致性的程度。</span><span class="sxs-lookup"><span data-stu-id="8ff15-151">This tells you how consistent the model is when prediction on different subsets of the data.</span></span> <span data-ttu-id="8ff15-152">例如，如果標準差非常大，表示針對每個折疊所建立的模型有非常不同的結果，因此，模型在特定資料群組上的定型可能太接近，而且不適用於其他資料集。</span><span class="sxs-lookup"><span data-stu-id="8ff15-152">For example, if the standard deviation is very large, it indicates that the models created for each fold have very different results, and therefore the model may have trained too closely on a particular group of data and not be applicable to other data sets.</span></span>  
  
 <span data-ttu-id="8ff15-153">下節說明評估模型所使用的量值。</span><span class="sxs-lookup"><span data-stu-id="8ff15-153">The following section explains the measures that are used to assess the models.</span></span>  
  
### <a name="tests-and-measures"></a><span data-ttu-id="8ff15-154">測試和量值</span><span class="sxs-lookup"><span data-stu-id="8ff15-154">Tests and Measures</span></span>  
 <span data-ttu-id="8ff15-155">除了一些有關資料中的折疊數以及每個折疊中的資料量等基本資訊外，工作表也會顯示有關每個模型的標準集並以測試類型分類。</span><span class="sxs-lookup"><span data-stu-id="8ff15-155">In addition to some basic information about the number of folds in the data, and the amount of data in each fold, the worksheet displays a set of metrics about each model, categorized by test type.</span></span> <span data-ttu-id="8ff15-156">例如，群集模型的精確度是透過不同於您用於預測模型的測試進行評估。</span><span class="sxs-lookup"><span data-stu-id="8ff15-156">For example, the accuracy of a clustering model is assessed by different tests than you would use for a forecasting model.</span></span>  
  
 <span data-ttu-id="8ff15-157">下表列出測試和標準，並提供標準所代表意義的說明。</span><span class="sxs-lookup"><span data-stu-id="8ff15-157">The following table lists the tests and metrics, with an explanation of what the metric means.</span></span>  
  
#### <a name="aggregates-and-general-statistical-measures"></a><span data-ttu-id="8ff15-158">彙總和一般統計量值</span><span class="sxs-lookup"><span data-stu-id="8ff15-158">Aggregates and General Statistical Measures</span></span>  
 <span data-ttu-id="8ff15-159">報表中提供的彙總量值表示您在資料中建立之折疊之間的差異。</span><span class="sxs-lookup"><span data-stu-id="8ff15-159">The aggregate measures provided in the report indicate how the folds that you created in the data differ from each other.</span></span>  
  
-   <span data-ttu-id="8ff15-160">平均和標準差</span><span class="sxs-lookup"><span data-stu-id="8ff15-160">Average and standard deviation.</span></span>  
  
-   <span data-ttu-id="8ff15-161">在模型的所有資料分割中，與特定量值平均數的差異平均值。</span><span class="sxs-lookup"><span data-stu-id="8ff15-161">Average of the deviation from the mean for a specific measure, across all the partitions in a model.</span></span>  
  
#### <a name="classification-passfail"></a><span data-ttu-id="8ff15-162">分類：通過/失敗</span><span class="sxs-lookup"><span data-stu-id="8ff15-162">Classification: Pass/Fail</span></span>  
 <span data-ttu-id="8ff15-163">當您沒有指定可預測屬性的目標值時，會在分類模型中使用這個量值。</span><span class="sxs-lookup"><span data-stu-id="8ff15-163">This measure is used in classification models when you do not specify a target value for the predictable attribute.</span></span> <span data-ttu-id="8ff15-164">例如，如果您建立可預測多個可能性的模型，這個量值會告訴您該模型在預測所有可能值的妥善程度。</span><span class="sxs-lookup"><span data-stu-id="8ff15-164">For example, if you create a model that predicts multiple possibilities, this measure tells you how well the model did at predicting all possible values.</span></span>  
  
 <span data-ttu-id="8ff15-165">通過/失敗是由符合下列條件的案例計數計算：如果具有最高機率的預測狀態與輸入狀態相同，且機率大於您為 [**狀態閾值**] 指定的值，則會進行**傳遞**。否則**會失敗**。</span><span class="sxs-lookup"><span data-stu-id="8ff15-165">Pass/fail is calculated by counting of cases that meet the following conditions: **pass** if the predicted state with the highest probability is the same as the input state and probability is greater than the value that you specified for **State Threshold**; otherwise, **fail**.</span></span>  
  
#### <a name="classification-true-or-false-positives-and-negatives"></a><span data-ttu-id="8ff15-166">分類：真肯定和真否定或誤判和誤否定</span><span class="sxs-lookup"><span data-stu-id="8ff15-166">Classification: True or False Positives and Negatives</span></span>  
 <span data-ttu-id="8ff15-167">此測試用於具有指定之目標的所有分類模型。</span><span class="sxs-lookup"><span data-stu-id="8ff15-167">This test is used for all classification models that have a specified target.</span></span> <span data-ttu-id="8ff15-168">量值表示每個案例對於下列問題的回應如何進行分類：模型在預測什麼，以及實際的結果是什麼。</span><span class="sxs-lookup"><span data-stu-id="8ff15-168">The measure indicates how each case is classified in response to these questions: what did the model predict, and what was the actual result.</span></span>  
  
|<span data-ttu-id="8ff15-169">Measure</span><span class="sxs-lookup"><span data-stu-id="8ff15-169">Measure</span></span>|<span data-ttu-id="8ff15-170">描述</span><span class="sxs-lookup"><span data-stu-id="8ff15-170">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8ff15-171">真肯定</span><span class="sxs-lookup"><span data-stu-id="8ff15-171">True positive</span></span>|<span data-ttu-id="8ff15-172">符合這些條件的案例計數：</span><span class="sxs-lookup"><span data-stu-id="8ff15-172">Count of cases that meet these conditions:</span></span><br /><br /> <span data-ttu-id="8ff15-173">案例包含目標值。</span><span class="sxs-lookup"><span data-stu-id="8ff15-173">Case contains the target value.</span></span><br /><br /> <span data-ttu-id="8ff15-174">模型預測出案例包含目標值。</span><span class="sxs-lookup"><span data-stu-id="8ff15-174">Model predicted that case contains the target value.</span></span>|  
|<span data-ttu-id="8ff15-175">誤判</span><span class="sxs-lookup"><span data-stu-id="8ff15-175">False positive</span></span>|<span data-ttu-id="8ff15-176">符合這些條件的案例計數：</span><span class="sxs-lookup"><span data-stu-id="8ff15-176">Count of cases that meet these conditions:</span></span><br /><br /> <span data-ttu-id="8ff15-177">實際的值等於目標值。</span><span class="sxs-lookup"><span data-stu-id="8ff15-177">Actual value is equal to target value.</span></span><br /><br /> <span data-ttu-id="8ff15-178">模型預測出案例包含目標值。</span><span class="sxs-lookup"><span data-stu-id="8ff15-178">Model predicted that case contains the target value.</span></span>|  
|<span data-ttu-id="8ff15-179">真否定</span><span class="sxs-lookup"><span data-stu-id="8ff15-179">True negative</span></span>|<span data-ttu-id="8ff15-180">符合這些條件的案例計數：</span><span class="sxs-lookup"><span data-stu-id="8ff15-180">Count of cases that meet these conditions:</span></span><br /><br /> <span data-ttu-id="8ff15-181">案例不包含目標值。</span><span class="sxs-lookup"><span data-stu-id="8ff15-181">Case does not contain the target value.</span></span><br /><br /> <span data-ttu-id="8ff15-182">模型預測出案例不包含目標值。</span><span class="sxs-lookup"><span data-stu-id="8ff15-182">Model predicted that case does not contain the target value.</span></span>|  
|<span data-ttu-id="8ff15-183">誤否定</span><span class="sxs-lookup"><span data-stu-id="8ff15-183">False negative</span></span>|<span data-ttu-id="8ff15-184">符合這些條件的案例計數：</span><span class="sxs-lookup"><span data-stu-id="8ff15-184">Count of cases that meet these conditions:</span></span><br /><br /> <span data-ttu-id="8ff15-185">實際的值不等於目標值。</span><span class="sxs-lookup"><span data-stu-id="8ff15-185">Actual value not equal to target value.</span></span><br /><br /> <span data-ttu-id="8ff15-186">模型預測出案例不包含目標值。</span><span class="sxs-lookup"><span data-stu-id="8ff15-186">Model predicted that case does not contain the target value.</span></span>|  
  
#### <a name="lift"></a><span data-ttu-id="8ff15-187">增益</span><span class="sxs-lookup"><span data-stu-id="8ff15-187">Lift</span></span>  
 <span data-ttu-id="8ff15-188">增益*是與*可能性相關聯的量值。</span><span class="sxs-lookup"><span data-stu-id="8ff15-188">*Lift* is a measure that is associated with likelihood.</span></span> <span data-ttu-id="8ff15-189">當您使用模型時，如果您在進行隨機猜測時，會產生較多的結果，則模型會被稱為提供*正面*增益。</span><span class="sxs-lookup"><span data-stu-id="8ff15-189">If an outcome is more likely when you use the model than when you make a random guess, the model is said to provide *positive lift*.</span></span> <span data-ttu-id="8ff15-190">不過，如果模型做出的預測較不可能是隨機機率，增益分數就是*負值*。</span><span class="sxs-lookup"><span data-stu-id="8ff15-190">However, if the model makes predictions that are less likely than random chance, the lift score is *negative*.</span></span> <span data-ttu-id="8ff15-191">因此，這項標準表示使用模型可以達到的改進程度，其分數越高越好。</span><span class="sxs-lookup"><span data-stu-id="8ff15-191">Therefore, this metric indicates the amount of improvement that can be achieved by using the model, where a higher score is better.</span></span>  
  
 <span data-ttu-id="8ff15-192">系統會將增益當做實際預測機率與測試案例中臨界機率的比率計算。</span><span class="sxs-lookup"><span data-stu-id="8ff15-192">Lift is calculated as the ratio of the actual prediction probability to the marginal probability in the test cases.</span></span>  
  
#### <a name="log-score"></a><span data-ttu-id="8ff15-193">對數分數</span><span class="sxs-lookup"><span data-stu-id="8ff15-193">Log Score</span></span>  
 <span data-ttu-id="8ff15-194">*對數分數*（也稱為預測的*記錄可能性分數*）代表兩個機率之間的比率，轉換成對數刻度。</span><span class="sxs-lookup"><span data-stu-id="8ff15-194">The *log score*, also called the *log likelihood score* for the prediction, represents the ratio between two probabilities, converted to a logarithmic scale.</span></span> <span data-ttu-id="8ff15-195">由於機率會以小數表示，因此對數分數永遠為負數。</span><span class="sxs-lookup"><span data-stu-id="8ff15-195">Because probabilities are represented as a decimal fraction, the log score is always a negative number.</span></span> <span data-ttu-id="8ff15-196">分數越接近 0，表示得分越高。</span><span class="sxs-lookup"><span data-stu-id="8ff15-196">A score that is closer to 0 is a better score.</span></span>  
  
 <span data-ttu-id="8ff15-197">鑑於原始分數可能具有非常不尋常或偏斜的散發，對數分數會與百分比類似。</span><span class="sxs-lookup"><span data-stu-id="8ff15-197">Whereas raw scores can have very irregular or skewed distributions, a log score is similar to a percentage.</span></span>  
  
#### <a name="root-mean-square-error"></a><span data-ttu-id="8ff15-198">均方根誤差</span><span class="sxs-lookup"><span data-stu-id="8ff15-198">Root Mean Square Error</span></span>  
 <span data-ttu-id="8ff15-199">*根平均平方誤差* (RMSE) 是統計資料中的標準方法，以查看不同的資料集比較方式，並將輸入的小數位數所能引進的差異平滑化。</span><span class="sxs-lookup"><span data-stu-id="8ff15-199">*Root mean square error* (RMSE) is a standard method in statistics for looking at how different data sets compare, and smoothing out the differences that can be introduced by the scale of the inputs.</span></span>  
  
 <span data-ttu-id="8ff15-200">RMSE 代表與實際值相比時，預測值的平均誤差。</span><span class="sxs-lookup"><span data-stu-id="8ff15-200">RMSE represents the average error of the predicted value when compared to the actual value.</span></span> <span data-ttu-id="8ff15-201">它會以所有資料分割案例平均誤差的平方根，除以資料分割中的案例數目來計算，不包括目標屬性擁有遺漏值的資料列。</span><span class="sxs-lookup"><span data-stu-id="8ff15-201">It is calculated as the square root of the mean error for all partition cases, divided by the number of cases in the partition, excluding rows that have missing values for the target attributes.</span></span>  
  
#### <a name="mean-absolute-error"></a><span data-ttu-id="8ff15-202">平均絕對誤差</span><span class="sxs-lookup"><span data-stu-id="8ff15-202">Mean Absolute Error</span></span>  
 <span data-ttu-id="8ff15-203">*平均絕對錯誤*是預測值對實際值的平均誤差。</span><span class="sxs-lookup"><span data-stu-id="8ff15-203">The *mean absolute error* is the average error of the predicted value to the actual value.</span></span> <span data-ttu-id="8ff15-204">計算方式為，取得誤差總和的絕對值，然後尋找這些誤差的平均值。</span><span class="sxs-lookup"><span data-stu-id="8ff15-204">It is calculated by obtaining the absolute sum of errors, and finding the mean of those errors.</span></span>  
  
 <span data-ttu-id="8ff15-205">這個值有助於了解分數與平均值距離的變化。</span><span class="sxs-lookup"><span data-stu-id="8ff15-205">This value helps you understand how far scores vary from the mean.</span></span>  
  
#### <a name="case-likelihood"></a><span data-ttu-id="8ff15-206">案例概似值</span><span class="sxs-lookup"><span data-stu-id="8ff15-206">Case Likelihood</span></span>  
 <span data-ttu-id="8ff15-207">此量值僅用於群集模型，表示新案例屬於特定群集的可能性。</span><span class="sxs-lookup"><span data-stu-id="8ff15-207">This measure is used only for clustering models, and indicates how probable it is that a new case belongs to a particular cluster.</span></span>  
  
 <span data-ttu-id="8ff15-208">在群集模型中，根據您建立模型所使用的方法，有兩種群集成員資格。</span><span class="sxs-lookup"><span data-stu-id="8ff15-208">In clustering models, there are two kinds of cluster membership, depending on the method you used to create the model.</span></span> <span data-ttu-id="8ff15-209">在某些模型中，根據 K-means 演算法，新案例應該只屬於一個群集。</span><span class="sxs-lookup"><span data-stu-id="8ff15-209">In some models, based on the K-means algorithm, a new case is expected to belong to only one cluster.</span></span> <span data-ttu-id="8ff15-210">不過根據預設，Microsoft 群集演算法使用最大期望值方法，假設新案例潛在可能屬於任何群集。</span><span class="sxs-lookup"><span data-stu-id="8ff15-210">However, by default the Microsoft Clustering algorithm uses the Expectation Maximization method, which assumes that a new case potentially can belong to any cluster.</span></span> <span data-ttu-id="8ff15-211">因此在這些模型中，一個案例可以有多個 `CaseLikelihood` 值，但是根據預設回報的值是屬於最符合新案例之群集的案例概似值。</span><span class="sxs-lookup"><span data-stu-id="8ff15-211">Therefore, in these models a case can have multiple `CaseLikelihood` values, but the one reported by default is the likelihood of the case belonging to the cluster that is the best match for the new case.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ff15-212">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8ff15-212">See Also</span></span>  
 [<span data-ttu-id="8ff15-213">驗證模型及使用模型進行預測 &#40;適用于 Excel 的資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="8ff15-213">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
