---
title: " (Analysis Services 的採礦模型篩選-資料採礦) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [data mining]
- filter syntax [data mining]
- models [Analysis Services], filtering
- filters [data mining]
- filtering data [Analysis Services]
ms.assetid: 0f29c19c-4be3-4bc7-ab60-f4130a10d59c
author: minewiskan
ms.author: owend
ms.openlocfilehash: a4e2c82c977f734948e107773e439ca154f6cfdd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592323"
---
# <a name="filters-for-mining-models-analysis-services---data-mining"></a><span data-ttu-id="11331-102">採礦模型的篩選 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="11331-102">Filters for Mining Models (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="11331-103">以資料為基礎的模型篩選可協助您建立使用採礦結構中之資料子集的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="11331-103">Data-based model filtering helps you create mining models that use subsets of data in a mining structure.</span></span> <span data-ttu-id="11331-104">當您設計採礦結構和資料來源時，篩選可提供彈性，因為您可以根據完整的資料來源檢視來建立單一採礦結構。</span><span class="sxs-lookup"><span data-stu-id="11331-104">Filtering gives you flexibility when you design your mining structures and data sources, because you can create a single mining structure, based on a comprehensive data source view.</span></span> <span data-ttu-id="11331-105">然後，您可以建立篩選來單獨使用其中一部分資料進行各種模型的定型和測試，而非針對每個資料子集建立不同的結構和相關模型。</span><span class="sxs-lookup"><span data-stu-id="11331-105">You can then create filters to use only a part of that data for training and testing a variety of models, instead of building a different structure and related model for each subset of data.</span></span>  
  
 <span data-ttu-id="11331-106">例如，您可以針對 Customers 資料表和相關資料表定義資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="11331-106">For example, you define the data source view on the Customers table and related tables.</span></span> <span data-ttu-id="11331-107">接著，您可以定義包含所需之所有欄位的單一採礦結構。</span><span class="sxs-lookup"><span data-stu-id="11331-107">Next, you define a single mining structure that includes all the fields you need.</span></span> <span data-ttu-id="11331-108">最後，您可以建立在特定客戶屬性 (例如 Region) 上篩選的模型。</span><span class="sxs-lookup"><span data-stu-id="11331-108">Finally, you create a model that is filtered on a particular customer attribute, such as Region.</span></span> <span data-ttu-id="11331-109">然後，您可以輕鬆地建立該模型的副本，並且單獨將篩選條件變更為根據不同的區域產生新的模型。</span><span class="sxs-lookup"><span data-stu-id="11331-109">You can then easily make a copy of that model, and change just the filter condition to generate a new model based on a different region.</span></span>  
  
 <span data-ttu-id="11331-110">您可以從這項功能中獲益的某些真實生活狀況包括：</span><span class="sxs-lookup"><span data-stu-id="11331-110">Some real-life scenarios where you might benefit from this feature include the following:</span></span>  
  
-   <span data-ttu-id="11331-111">針對離散值 (例如性別、區域等等) 建立不同的模型。</span><span class="sxs-lookup"><span data-stu-id="11331-111">Creating separate models for discrete values such as gender, regions, and so forth.</span></span> <span data-ttu-id="11331-112">例如，服飾店可能會使用客戶人口統計來依據性別建立不同的模型，即使銷售資料來自所有客戶的單一資料來源也一樣。</span><span class="sxs-lookup"><span data-stu-id="11331-112">For example, a clothing store might use customer demographics to build separate models by gender, even though the sales data comes from a single data source for all customers.</span></span>  
  
-   <span data-ttu-id="11331-113">建立並測試相同資料的多個群組 (例如 20-30 歲、20-40 歲與 20-25 歲的比較)，藉以嘗試各種模型。</span><span class="sxs-lookup"><span data-stu-id="11331-113">Experimenting with models by creating and then testing multiple groupings of the same data, such as ages 20-30 vs. ages 20-40 vs. ages 20-25.</span></span>  
  
-   <span data-ttu-id="11331-114">針對巢狀資料表內容指定複雜的篩選，例如只有當客戶至少購買兩個特定項目時，才會在模型中加入案例。</span><span class="sxs-lookup"><span data-stu-id="11331-114">Specifying complex filters on nested table contents, such as requiring that a case be included in the model only if the customer has purchased at least two of a particular item.</span></span>  
  
 <span data-ttu-id="11331-115">本節將說明如何建立、使用和管理採礦模型的篩選。</span><span class="sxs-lookup"><span data-stu-id="11331-115">This section explains how to build, use, and manage filters on mining models.</span></span>  
  
## <a name="creating-model-filters"></a><span data-ttu-id="11331-116">建立模型篩選</span><span class="sxs-lookup"><span data-stu-id="11331-116">Creating Model Filters</span></span>  
 <span data-ttu-id="11331-117">您可以利用下列方式來建立和套用篩選：</span><span class="sxs-lookup"><span data-stu-id="11331-117">You can create and apply filters in the following ways:</span></span>  
  
-   <span data-ttu-id="11331-118">使用資料採礦設計師中的 **[採礦模型]** 索引標籤並搭配篩選編輯器對話方塊來建立條件。</span><span class="sxs-lookup"><span data-stu-id="11331-118">Using the **Mining Models** tab in Data Mining Designer to build conditions with the help of filter editor dialog boxes.</span></span>  
  
-   <span data-ttu-id="11331-119">直接在「採礦模型」的屬性中輸入篩選運算式 `Filter` 。</span><span class="sxs-lookup"><span data-stu-id="11331-119">Typing a filter expression directly into the `Filter` property of the mining model.</span></span>  
  
-   <span data-ttu-id="11331-120">使用分析管理物件 (AMO)，以程式設計方式設定模型的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="11331-120">Setting filter conditions on a model programmatically, by using AMO.</span></span>  
  
### <a name="creating-model-filters-using-data-mining-designer"></a><span data-ttu-id="11331-121">使用資料採礦設計師來建立模型篩選</span><span class="sxs-lookup"><span data-stu-id="11331-121">Creating Model Filters using Data Mining Designer</span></span>  
 <span data-ttu-id="11331-122">您可以變更採礦模型的 `Filter` 屬性，藉以在資料採礦設計師中篩選模型。</span><span class="sxs-lookup"><span data-stu-id="11331-122">You filter a model in Data Mining Designer by changing the `Filter` property of the mining model.</span></span> <span data-ttu-id="11331-123">您可以直接在 **[屬性]** 窗格中輸入篩選運算式，也可以開啟篩選對話方塊來建立條件。</span><span class="sxs-lookup"><span data-stu-id="11331-123">You can either type a filter expression directly into the **Properties** pane, or you can open a filter dialog box to build conditions.</span></span>  
  
 <span data-ttu-id="11331-124">目前提供了兩個篩選對話方塊。</span><span class="sxs-lookup"><span data-stu-id="11331-124">There are two filter dialog boxes.</span></span> <span data-ttu-id="11331-125">第一個對話方塊可讓您建立套用至案例資料表的條件。</span><span class="sxs-lookup"><span data-stu-id="11331-125">The first lets you create conditions that are applied to the case table.</span></span> <span data-ttu-id="11331-126">如果資料來源包含多份資料表，您首先要選取一份資料表，然後選取資料行並指定套用至該資料行的運算子與條件。</span><span class="sxs-lookup"><span data-stu-id="11331-126">If the data source contains multiple tables, first you select a table, and then you select a column and specify operators and conditions that apply to that column.</span></span> <span data-ttu-id="11331-127">您可以使用運算子來連結多個條件 `AND` / `OR` 。</span><span class="sxs-lookup"><span data-stu-id="11331-127">You can link multiple conditions by using `AND`/`OR` operators.</span></span> <span data-ttu-id="11331-128">可用來定義值的運算子會因資料行包含離散值或連續值而不同。</span><span class="sxs-lookup"><span data-stu-id="11331-128">The operators that are available for defining values depend on whether the column contains discrete or continuous values.</span></span> <span data-ttu-id="11331-129">例如，如果包含連續值，您就可以使用 `greater than` 和 `less than` 運算子。</span><span class="sxs-lookup"><span data-stu-id="11331-129">For example, with continuous values, you can use `greater than` and `less than` operators.</span></span> <span data-ttu-id="11331-130">不過，如果包含離散值，您就只能使用 `= (equal to)`、`!= (not equal to)` 和 `is null` 運算子。</span><span class="sxs-lookup"><span data-stu-id="11331-130">However, for discrete values, you can only use `= (equal to)`, `!= (not equal to)`, and `is null` operators.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="11331-131">不支援 `LIKE` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="11331-131">The `LIKE` keyword is not supported.</span></span> <span data-ttu-id="11331-132">如果您想要加入多個離散屬性，就必須建立不同的條件，然後使用 `OR` 運算子來連結它們。</span><span class="sxs-lookup"><span data-stu-id="11331-132">If you want to include multiple discrete attributes, you must create separate conditions and link them by using the `OR` operator.</span></span>  
  
 <span data-ttu-id="11331-133">如果這些條件很複雜，您可以使用第二個篩選對話方塊來一次使用一份資料表。</span><span class="sxs-lookup"><span data-stu-id="11331-133">If the conditions are complex, you can use the second filter dialog box to work with one table at a time.</span></span> <span data-ttu-id="11331-134">當您關閉第二個篩選對話方塊時，運算式會進行評估，然後與案例資料表中已設定於其他資料行的篩選條件結合。</span><span class="sxs-lookup"><span data-stu-id="11331-134">When you close the second filter dialog box, the expression is evaluated and then combined with filter conditions that have been set on other columns in the case table.</span></span>  
  
### <a name="creating-filters-on-nested-tables"></a><span data-ttu-id="11331-135">建立巢狀資料表的篩選</span><span class="sxs-lookup"><span data-stu-id="11331-135">Creating Filters on Nested Tables</span></span>  
 <span data-ttu-id="11331-136">如果資料來源檢視包含巢狀資料表，您就可以使用第二個篩選對話方塊，針對巢狀資料表中的資料列建立條件。</span><span class="sxs-lookup"><span data-stu-id="11331-136">If the data source view contains nested tables, you can use the second filter dialog box to build conditions on the rows in the nested tables.</span></span>  
  
 <span data-ttu-id="11331-137">例如，如果您的案例資料表與客戶有關，而且巢狀資料表顯示某位客戶已經購買的產品，您就可以在巢狀資料表篩選中使用下列語法，藉以針對已經購買特定項目的客戶建立篩選： `[ProductName]='Water Bottle' OR ProductName='Water Bottle Cage'`。</span><span class="sxs-lookup"><span data-stu-id="11331-137">For example, if your case table is related to customers, and the nested table shows the products that a customer has purchased, you can create a filter for customers who have purchased particular items by using the following syntax in the nested table filter: `[ProductName]='Water Bottle' OR ProductName='Water Bottle Cage'`.</span></span>  
  
 <span data-ttu-id="11331-138">您也可以使用 `EXISTS` 或 `NOT EXISTS` 關鍵字和子查詢，藉以篩選巢狀資料表中是否存在特定值。</span><span class="sxs-lookup"><span data-stu-id="11331-138">You can also filter on the existence of a particular value in the nested table by using the `EXISTS` or `NOT EXISTS` keywords and a subquery.</span></span> <span data-ttu-id="11331-139">這可讓您建立 `EXISTS (SELECT * FROM Products WHERE ProductName='Water Bottle')`等條件。</span><span class="sxs-lookup"><span data-stu-id="11331-139">This lets you create conditions such as `EXISTS (SELECT * FROM Products WHERE ProductName='Water Bottle')`.</span></span> <span data-ttu-id="11331-140">如果巢狀資料表至少有一個資料列包含 `EXISTS SELECT(<subquery>)` 值，`Water Bottle` 就會傳回 `true`。</span><span class="sxs-lookup"><span data-stu-id="11331-140">The `EXISTS SELECT(<subquery>)` returns `true` if the nested table contains at least one row that includes the value, `Water Bottle`.</span></span>  
  
 <span data-ttu-id="11331-141">您可以結合案例資料表的條件與巢狀資料表的條件。</span><span class="sxs-lookup"><span data-stu-id="11331-141">You can combine conditions on the case table with conditions on the nested table.</span></span> <span data-ttu-id="11331-142">例如，下列語法包含案例資料表的條件 (`Age > 30` )、巢狀資料表的子查詢 (`EXISTS (SELECT * FROM Products)`)，以及巢狀資料表的多項條件 (`WHERE ProductName='Milk'  AND Quantity>2`) )。</span><span class="sxs-lookup"><span data-stu-id="11331-142">For example, the following syntax includes a condition on the case table (`Age > 30` ), a subquery on the nested table (`EXISTS (SELECT * FROM Products)`), and multiple conditions on the nested table (`WHERE ProductName='Milk'  AND Quantity>2`) ).</span></span>  
  
```  
(Age > 30 AND EXISTS (SELECT * FROM Products WHERE ProductName='Milk'  AND Quantity>2) )  
```  
  
 <span data-ttu-id="11331-143">當您建立篩選完成時，篩選文字就會由 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]進行評估、轉譯成 DMX 運算式，然後與模型一起儲存。</span><span class="sxs-lookup"><span data-stu-id="11331-143">When you have finished building the filter, the filter text is evaluated by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], translated to a DMX expression, and then saved with the model.</span></span>  
  
 <span data-ttu-id="11331-144">如需如何使用 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]之篩選對話方塊的指示，請參閱 [Apply a Filter to a Mining Model](apply-a-filter-to-a-mining-model.md)(將篩選套用至採礦模型)。</span><span class="sxs-lookup"><span data-stu-id="11331-144">For instructions on how to use the filter dialog boxes in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Apply a Filter to a Mining Model](apply-a-filter-to-a-mining-model.md).</span></span>  
  
## <a name="managing-mining-model-filters"></a><span data-ttu-id="11331-145">管理採礦模型篩選</span><span class="sxs-lookup"><span data-stu-id="11331-145">Managing Mining Model Filters</span></span>  
 <span data-ttu-id="11331-146">以資料為基礎的模型篩選會大幅簡化管理採礦結構和採礦模型的工作，因為您可以輕鬆地建立以相同結構為基礎的多個模型。</span><span class="sxs-lookup"><span data-stu-id="11331-146">Data-based model filtering greatly simplifies the task of managing mining structures and mining models, because you can easily create multiple models that are based on the same structure.</span></span> <span data-ttu-id="11331-147">您也可以快速地建立現有採礦模型的副本，然後單獨變更篩選條件。</span><span class="sxs-lookup"><span data-stu-id="11331-147">You can also quickly make copies of existing mining models and then change only the filter condition.</span></span> <span data-ttu-id="11331-148">但是，篩選可能會產生一些混淆。</span><span class="sxs-lookup"><span data-stu-id="11331-148">However, filters can lead to some confusion.</span></span>  
  
 <span data-ttu-id="11331-149">以下是有關如何針對採礦模型管理及解譯篩選的一些常見問題：</span><span class="sxs-lookup"><span data-stu-id="11331-149">Here are some frequently asked questions about how to manage and interpret filters on mining models:</span></span>  
  
### <a name="how-can-i-tell-whether-a-filter-is-being-used"></a><span data-ttu-id="11331-150">我要如何判斷是否使用篩選？</span><span class="sxs-lookup"><span data-stu-id="11331-150">How can I tell whether a filter is being used?</span></span>  
 <span data-ttu-id="11331-151">有多種方法可判斷篩選是否套用到模型：</span><span class="sxs-lookup"><span data-stu-id="11331-151">There are multiple ways to determine whether a filter is applied to a model:</span></span>  
  
-   <span data-ttu-id="11331-152">在設計工具中，按一下 [**採礦模型**] 索引標籤，開啟 [**屬性**]，然後查看 `Filter` [採礦模型] 的屬性。</span><span class="sxs-lookup"><span data-stu-id="11331-152">In the designer, click the **Mining Models** tab, open **Properties**, and view the `Filter` property of the mining model.</span></span>  
  
-   <span data-ttu-id="11331-153">DMV、DMSCHEMA_MINING_MODELS 會輸出包含篩選文字的資料行。</span><span class="sxs-lookup"><span data-stu-id="11331-153">The DMV, DMSCHEMA_MINING_MODELS, outputs a column that contains the text of the filter.</span></span> <span data-ttu-id="11331-154">您可以針對 DMV 使用以下查詢來傳回模型的名稱以及其篩選：</span><span class="sxs-lookup"><span data-stu-id="11331-154">You can use the following query on a DMV to return the names of models and their filters:</span></span>  
  
    ```  
    SELECT MODEL_NAME, [FILTER]   
    FROM $SYSTEM.DMSCHEMA_MINING_MODELS  
  
    ```  
  
-   <span data-ttu-id="11331-155">您可以在 AMO 中取得 MiningModel 物件的 Filter 屬性值，或是檢查 XMLA 中的 Filter 元素。</span><span class="sxs-lookup"><span data-stu-id="11331-155">You can get the value of the Filter property of the MiningModel object in AMO, or inspect the Filter element in XMLA.</span></span>  
  
 <span data-ttu-id="11331-156">您或許也可以為模型建立命名慣例來反映篩選的內容。</span><span class="sxs-lookup"><span data-stu-id="11331-156">You might also establish a naming convention for models to reflect the contents of the filter.</span></span> <span data-ttu-id="11331-157">這可讓您更方便區分相關的模型。</span><span class="sxs-lookup"><span data-stu-id="11331-157">This can make it easier to tell related models apart.</span></span>  
  
### <a name="how-can-i-save-a-filter"></a><span data-ttu-id="11331-158">如何儲存篩選？</span><span class="sxs-lookup"><span data-stu-id="11331-158">How can I save a filter?</span></span>  
 <span data-ttu-id="11331-159">篩選運算式會儲存成指令碼，並且與相關聯的採礦模型或巢狀資料表一起儲存。</span><span class="sxs-lookup"><span data-stu-id="11331-159">The filter expression is saved as a script that is stored with the associated mining model or nested table.</span></span> <span data-ttu-id="11331-160">如果您刪除了篩選文字，就只能手動重新建立篩選運算式，才能加以還原。</span><span class="sxs-lookup"><span data-stu-id="11331-160">If you delete the filter text, it can only be restored by manually re-creating the filter expression.</span></span> <span data-ttu-id="11331-161">因此，如果您建立複雜的篩選運算式，就應該建立篩選文字的備份副本。</span><span class="sxs-lookup"><span data-stu-id="11331-161">Therefore, if you create complex filter expressions, you should create a backup copy of the filter text.</span></span>  
  
### <a name="why-cant-i-see-any-effects-from-the-filter"></a><span data-ttu-id="11331-162">為什麼我看不到篩選準則的任何影響？</span><span class="sxs-lookup"><span data-stu-id="11331-162">Why can't I see any effects from the filter?</span></span>  
 <span data-ttu-id="11331-163">每當您變更或加入篩選運算式時，就必須重新處理結構和模型，然後才能檢視篩選的效果。</span><span class="sxs-lookup"><span data-stu-id="11331-163">Whenever you change or add a filter expression, you must reprocess the structure and model before you can view the effects of the filter.</span></span>  
  
### <a name="why-do-i-see-filtered-attributes-in-prediction-query-results"></a><span data-ttu-id="11331-164">為什麼在預測查詢結果中看到已篩選的屬性？</span><span class="sxs-lookup"><span data-stu-id="11331-164">Why do I see filtered attributes in prediction query results?</span></span>  
 <span data-ttu-id="11331-165">將篩選套用至模型時，它只會影響用於定型模型的選定案例。</span><span class="sxs-lookup"><span data-stu-id="11331-165">When you apply a filter to a model, it affects only the selection of cases used for training the model.</span></span> <span data-ttu-id="11331-166">篩選不會影響模型已知的屬性或是變更或隱藏資料來源中的資料。</span><span class="sxs-lookup"><span data-stu-id="11331-166">The filter does not affect the attributes known to the model, or change or suppress data that is present in the data source.</span></span> <span data-ttu-id="11331-167">因此，針對模型所做的查詢可以傳回其他案例類型的預測，而模型所使用之值的下拉式清單可能會顯示篩選所排除的屬性值。</span><span class="sxs-lookup"><span data-stu-id="11331-167">As a result, queries against the model can return predictions for other types of cases, and dropdown lists of values used by the model might show attribute values excluded by the filter.</span></span>  
  
 <span data-ttu-id="11331-168">例如，假設您只使用 20-30 歲婦女的案例來定型 [Bike Buyer] 模型。</span><span class="sxs-lookup"><span data-stu-id="11331-168">For example, suppose you train the [Bike Buyer] model using only cases involving women aged 20-30.</span></span> <span data-ttu-id="11331-169">您依然可以執行預測查詢來預測男性購買自行車的機率，或是預測 30-40 歲婦女的結果。</span><span class="sxs-lookup"><span data-stu-id="11331-169">You can still run a prediction query that predicts the probability of a man buying a bike, or predict the outcome for a woman aged 30-40.</span></span> <span data-ttu-id="11331-170">這是因為資料來源中的屬性和值會定義理論上可能發生的狀況，而案例則會定義用於定型的發生狀況。</span><span class="sxs-lookup"><span data-stu-id="11331-170">That is because the attributes and values present in the data source define what is theoretically possible, while the cases define the occurrences used for training.</span></span> <span data-ttu-id="11331-171">但是，這些查詢將會傳回極小的機率，因為定型資料不包含任何有目標值的案例。</span><span class="sxs-lookup"><span data-stu-id="11331-171">However, these queries would return very small probabilities, because the training data does not contain any cases with the target values.</span></span>  
  
 <span data-ttu-id="11331-172">如果您必須將模型中的屬性值完全隱藏或匿名，有許多選擇可以採用：</span><span class="sxs-lookup"><span data-stu-id="11331-172">If you need to completely hide or anonymize attribute values in the model, there are various options:</span></span>  
  
-   <span data-ttu-id="11331-173">篩選屬於資料來源檢視定義之一部分或是關聯式資料來源中的內送資料。</span><span class="sxs-lookup"><span data-stu-id="11331-173">Filter the incoming data as part of the definition of the data source view, or in the relational data source.</span></span>  
  
-   <span data-ttu-id="11331-174">為屬性值加上遮罩或編碼。</span><span class="sxs-lookup"><span data-stu-id="11331-174">Mask or encode the attribute value.</span></span>  
  
-   <span data-ttu-id="11331-175">將已排除的值摺疊到類別目錄中，當做採礦結構定義的一部分。</span><span class="sxs-lookup"><span data-stu-id="11331-175">Collapse excluded values into a category as part of the mining structure definition.</span></span>  
  
## <a name="related-resources"></a><span data-ttu-id="11331-176">相關資源</span><span class="sxs-lookup"><span data-stu-id="11331-176">Related Resources</span></span>  
 <span data-ttu-id="11331-177">如需篩選語法的詳細資訊以及篩選運算式的範例，請參閱 [模型篩選語法和範例 &#40;Analysis Services - 資料採礦&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="11331-177">For more information about filter syntax, and examples of filter expressions, see [Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="11331-178">如需在測試採礦模型時如何使用模型篩選的資訊，請參閱 [Choose an Accuracy Chart Type and Set Chart Options](choose-an-accuracy-chart-type-and-set-chart-options.md)(選擇精確度圖表類型及設定圖表選項)。</span><span class="sxs-lookup"><span data-stu-id="11331-178">For information about how to use model filters when you are testing a mining model, see [Choose an Accuracy Chart Type and Set Chart Options](choose-an-accuracy-chart-type-and-set-chart-options.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11331-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11331-179">See Also</span></span>  
 <span data-ttu-id="11331-180">[模型篩選語法和範例 &#40;Analysis Services-資料採礦&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="11331-180">[Model Filter Syntax and Examples &#40;Analysis Services - Data Mining&#41;](model-filter-syntax-and-examples-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="11331-181">測試及驗證 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="11331-181">Testing and Validation &#40;Data Mining&#41;</span></span>](testing-and-validation-data-mining.md)  
  
  
