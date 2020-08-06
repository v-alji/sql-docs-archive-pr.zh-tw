---
title: 將篩選套用至模型測試資料 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- input row filtering [SQL Server]
- filtering input rows [Analysis Services]
- Mining Accuracy Chart [Analysis Services], filtering input rows
ms.assetid: 9ccc9a23-5597-4b35-a05f-2fc8eb885147
author: minewiskan
ms.author: owend
ms.openlocfilehash: d1fd2b643ae4f7d831cab980ca45b7d43d8b58f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585677"
---
# <a name="apply-filters-to-model-testing-data"></a><span data-ttu-id="b9c7b-102">將篩選套用至模型測試資料</span><span class="sxs-lookup"><span data-stu-id="b9c7b-102">Apply Filters to Model Testing Data</span></span>
  <span data-ttu-id="b9c7b-103">當您指定要用於測試模型的外部資料來源時，可以選擇性地套用篩選，以限制輸入資料。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-103">When you specify an external data source to use in testing a model, you can optionally apply a filter to restrict the input data.</span></span> <span data-ttu-id="b9c7b-104">例如，您可能想要特別針對某個收入範圍的客戶進行預測來測試模型。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-104">For example, you might want to test the model specifically for predictions on customers in a certain income range.</span></span>  
  
 <span data-ttu-id="b9c7b-105">例如，在 AdventureWorks 目標郵寄案例中，您可以在 ProspectiveBuyer （也就是包含測試資料的資料表）上建立如下一個篩選條件運算式，並依收入範圍限制測試案例：</span><span class="sxs-lookup"><span data-stu-id="b9c7b-105">For example, in the AdventureWorks targeted mailing scenario, you can create a filter expression like the following one on ProspectiveBuyer, which is the table that contains the testing data, and restrict testing cases by income range:</span></span>  
  
 `[YearlyIncome] = '50000'`  
  
 <span data-ttu-id="b9c7b-106">根據篩選的是模型定型資料還是測試資料集，篩選行為稍微不同：</span><span class="sxs-lookup"><span data-stu-id="b9c7b-106">The behavior of filters is slightly different, depending on whether you are filtering model training data or a testing data set:</span></span>  
  
-   <span data-ttu-id="b9c7b-107">在測試資料集上定義篩選時，您要在內送資料上建立 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-107">When you define a filter on a testing data set, you create a WHERE clause on the incoming data.</span></span> <span data-ttu-id="b9c7b-108">如果要篩選用於評估模型的輸入資料集，則篩選運算式會轉譯為 Transact-SQL 陳述式，並在建立圖表時套用至輸入資料表。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-108">If you are filtering an input data set used for evaluating a model, the filter expression is translated to a Transact-SQL statement and applied to the input table when the chart is created.</span></span> <span data-ttu-id="b9c7b-109">因此，測試案例數會大幅減少。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-109">As a result, the number of test cases can be greatly reduced.</span></span>  
  
-   <span data-ttu-id="b9c7b-110">將篩選套用至採礦模型時，您建立的篩選運算式會轉譯為「資料採礦延伸模組」(DMX) 陳述式，並套用至個別模型。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-110">When you apply a filter to a mining model, the filter expression that you create is translated to a Data Mining Extensions (DMX) statement, and applied to the individual model.</span></span> <span data-ttu-id="b9c7b-111">因此，將篩選套用至模型時，只會使用原始資料的子集來定型模型。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-111">Therefore, when you apply a filter to a model, only a subset of the original data is used to train the model.</span></span> <span data-ttu-id="b9c7b-112">如果您使用一組準則來篩選定型模型，讓模型調整為某一組資料，然後使用另一組準則對模型進行測試，這可能會導致問題。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-112">This can cause problems if you filter the training model with one set of criteria, so that the model is tuned to a certain set of data, and then test the model with another set of criteria.</span></span>  
  
-   <span data-ttu-id="b9c7b-113">如果在建立結構時定義了測試資料集，則用於定型的模型案例僅會包含採礦結構定型集中的案例 **以及** 符合篩選條件的案例。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-113">If you defined a testing data set when you created the structure, the model cases used for training include only those cases that are in the mining structure training set **and** which meet the conditions of the filter.</span></span> <span data-ttu-id="b9c7b-114">因此，當您測試模型並選取 [使用採礦模型測試案例]\*\*\*\* 選項時，測試案例僅會包含採礦結構測試集中的案例以及符合篩選條件的案例。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-114">Thus, when you are testing a model and select the option **Use mining model test cases**, the testing cases will include only the cases that are in the mining structure test set and which meet the conditions of the filter.</span></span> <span data-ttu-id="b9c7b-115">不過，如果您未定義鑑效組資料集，則用於測試的模型案例會包含資料集中符合篩選條件的所有案例。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-115">However, if you did not define a holdout data set, the model cases used for testing include all the cases in the data set that meet the filter conditions</span></span>  
  
-   <span data-ttu-id="b9c7b-116">模型上套用的篩選條件也會影響模型案例的鑽研查詢。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-116">Filter conditions that you apply on a model also affect drillthrough queries on the model cases.</span></span>  
  
 <span data-ttu-id="b9c7b-117">總之，在您測試多個模型時，即使所有模型都是根據相同的採礦結構，您也必須意識到模型可能會使用不同的資料子集來進行定型和測試。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-117">In summary, when you test multiple models, even if all the models are based on the same mining structure, you must be aware that the models potentially use different subsets of data for training and testing.</span></span> <span data-ttu-id="b9c7b-118">這可能對精確度圖表具有下列影響：</span><span class="sxs-lookup"><span data-stu-id="b9c7b-118">This can have the following effects on accuracy charts:</span></span>  
  
-   <span data-ttu-id="b9c7b-119">測試集中案例的總數在多個測試的模型中可能會不同。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-119">The total number of cases in the testing sets can vary among the models being tested.</span></span>  
  
-   <span data-ttu-id="b9c7b-120">如果模型使用不同的定型資料或測試資料的子集，則每個模型的百分比在圖表中可能不會對齊。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-120">The percentages for each model may not align in the chart, if the models use different subsets of training data or testing data.</span></span>  
  
 <span data-ttu-id="b9c7b-121">若要判斷模型是否包含可能會影響結果的預先定義篩選，您可以在 [屬性]\*\*\*\* 窗格中尋找 [篩選]\*\*\*\* 屬性，或透過使用資料採礦結構描述資料列集來查詢模型。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-121">To determine whether a model contains a predefined filter that might affect results, you can look for the **Filter** property in the **Property** pane, or you can query the model by using the data mining schema rowsets.</span></span> <span data-ttu-id="b9c7b-122">例如，下列查詢會傳回指定之模型的篩選文字：</span><span class="sxs-lookup"><span data-stu-id="b9c7b-122">For example, the following query returns the filter text for the specified model:</span></span>  
  
 `SELECT [FILTER] FROM $system.DMSCHEMA_MINING_MODELS WHERE MODEL_NAME = 'name of model'`  
  
> [!WARNING]  
>  <span data-ttu-id="b9c7b-123">如果您要從現有的採礦模型中移除篩選，或者變更篩選條件，則必須重新處理採礦模型。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-123">If you want to remove the filter from an existing mining model, or change the filter conditions, you must reprocess the mining model.</span></span>  
  
 <span data-ttu-id="b9c7b-124">如需可套用的篩選類型以及如何評估篩選運算式的詳細資訊，請參閱[模型篩選語法和範例 &#40;Analysis Services - 資料採礦&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-124">For more information about the kinds of filters you can apply, and how filter expressions are evaluated, see [Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md).</span></span>  
  
### <a name="create-a-filter-on-external-testing-data"></a><span data-ttu-id="b9c7b-125">針對外部測試資料建立篩選</span><span class="sxs-lookup"><span data-stu-id="b9c7b-125">Create a filter on external testing data</span></span>  
  
1.  <span data-ttu-id="b9c7b-126">按兩下包含要測試模型的採礦結構，以開啟資料採礦設計師。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-126">Double-click the mining structure that contains the model you want to test, to open Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="b9c7b-127">選取 **[採礦精確度圖表]** 索引標籤，然後選取 **[輸入選擇]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-127">Select the **Mining Accuracy Chart** tab, and then select the **Input Selection** tab.</span></span>  
  
3.  <span data-ttu-id="b9c7b-128">在 [輸入選擇]\*\*\*\* 索引標籤的 [選取要用於精確度圖表的資料集]\*\*\*\* 下，選取 [指定不同的資料集]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-128">On the **Input Selection** tab, under **Select data set to be used for Accuracy Chart**, select the option **Specify a different data set**.</span></span>  
  
4.  <span data-ttu-id="b9c7b-129">按一下 [流覽] 按鈕\*\* ( ...] ) \*\*開啟對話方塊，並選擇外部資料集。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-129">Click the browse button **(...)** to open a dialog box and choose the external data set.</span></span>  
  
5.  <span data-ttu-id="b9c7b-130">選擇案例資料表，並視需要新增巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-130">Choose the case table, and add a nested table if necessary.</span></span> <span data-ttu-id="b9c7b-131">視需要將模型中的資料行對應至外部資料集中的資料行。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-131">Map columns in the model to columns in the external data set as necessary.</span></span> <span data-ttu-id="b9c7b-132">關閉 [指定資料行對應]\*\*\*\* 對話方塊，以儲存來源資料表定義。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-132">Close the **Specify Column Mapping** dialog box to save the source table definition.</span></span>  
  
6.  <span data-ttu-id="b9c7b-133">按一下 [開啟篩選編輯器]\*\*\*\* 定義資料集的篩選。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-133">Click **Open Filter Editor** to define a filter for the data set.</span></span>  
  
     <span data-ttu-id="b9c7b-134">[資料集篩選器]\*\*\*\* 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-134">The **Data Set Filter** dialog box opens.</span></span> <span data-ttu-id="b9c7b-135">如果結構包含巢狀資料表，您就可以分成兩個部分來建立篩選。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-135">If the structure contains a nested table, you can create a filter in two parts.</span></span> <span data-ttu-id="b9c7b-136">首先，請使用 [資料集篩選器]\*\*\*\* 對話方塊來設定案例資料表的條件，然後使用 [篩選]\*\*\*\* 對話方塊來設定巢狀資料列的條件。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-136">First, set conditions on the case table by using the **Data Set Filter** dialog box, and then set conditions on the nested rows by using the **Filter** dialog box.</span></span>  
  
7.  <span data-ttu-id="b9c7b-137">在 [資料集篩選器]\*\*\*\* 對話方塊中，按一下方格中最上方的資料列 ([採礦結構資料行]\*\*\*\* 底下)，然後從清單中選取資料表或資料行。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-137">In the **Data Set Filter** dialog box, click the top row in the grid, under **Mining Structure Column**, and select a table or column from the list.</span></span>  
  
     <span data-ttu-id="b9c7b-138">如果資料來源檢視包含多份資料表或一份巢狀資料表，您就必須先選取資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-138">If the data source view contains multiple tables, or a nested table, you must first select the table name.</span></span> <span data-ttu-id="b9c7b-139">否則，您可以直接從案例資料表中選取資料行。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-139">Otherwise, you can select columns from the case table directly.</span></span>  
  
     <span data-ttu-id="b9c7b-140">針對您想要篩選的每個資料行，加入新的資料列。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-140">Add a new row for each column that you want to filter.</span></span>  
  
8.  <span data-ttu-id="b9c7b-141">您可以使用 [運算子]\*\*\*\* 和 [值]\*\*\*\* 資料行來定義資料行的篩選方式。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-141">Use **Operator**, and **Value** columns to define how the column is filtered.</span></span>  
  
     <span data-ttu-id="b9c7b-142">**注意** ：當您輸入值時，請勿使用引號。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-142">**Note** Type values without using quotation marks.</span></span>  
  
9. <span data-ttu-id="b9c7b-143">按一下 [及/或]\*\*\*\* 文字方塊並選取邏輯運算子來定義多項條件的組合方式。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-143">Click the **And/Or** text box and select a logical operator to define how multiple conditions are combine.</span></span>  
  
10. <span data-ttu-id="b9c7b-144">（選擇性）按一下 [**值**] 文字方塊右邊的 [流覽] 按鈕\*\* ( ...] ) **開啟 [**篩選\*\*] 對話方塊，並設定嵌套資料表或個別案例資料表資料行上的條件。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-144">Optionally, click the browse button **(...)** at the right of the **Value** text box to open the **Filter** dialog box and set conditions on the nested table or on the individual case table columns.</span></span>  
  
11. <span data-ttu-id="b9c7b-145">檢視 [運算式]\*\*\*\* 窗格中的文字，藉以確認完成的篩選條件是否正確。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-145">Verify that the completed filter conditions are correct by viewing the text in the **Expression** pane.</span></span>  
  
12. [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     <span data-ttu-id="b9c7b-146">當您建立精確度圖表時，此篩選條件會套用至資料來源。</span><span class="sxs-lookup"><span data-stu-id="b9c7b-146">The filter condition is applied to the data source when you create the accuracy chart.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b9c7b-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b9c7b-147">See Also</span></span>  
 <span data-ttu-id="b9c7b-148">[選擇和對應模型測試資料](choose-and-map-model-testing-data.md) </span><span class="sxs-lookup"><span data-stu-id="b9c7b-148">[Choose and Map Model Testing Data](choose-and-map-model-testing-data.md) </span></span>  
 <span data-ttu-id="b9c7b-149">[使用嵌套資料表資料當做精確度圖表的輸入](using-nested-table-data-as-an-input-for-an-accuracy-chart.md) </span><span class="sxs-lookup"><span data-stu-id="b9c7b-149">[Using Nested Table Data as an Input for an Accuracy Chart](using-nested-table-data-as-an-input-for-an-accuracy-chart.md) </span></span>  
 [<span data-ttu-id="b9c7b-150">選擇精確度圖表類型及設定圖表選項</span><span class="sxs-lookup"><span data-stu-id="b9c7b-150">Choose an Accuracy Chart Type and Set Chart Options</span></span>](choose-an-accuracy-chart-type-and-set-chart-options.md)  
  
  
