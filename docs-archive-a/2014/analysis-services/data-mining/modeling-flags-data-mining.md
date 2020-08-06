---
title: 資料採礦) 的模型旗標 (|Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [data mining]
- data types [data mining]
- REGRESSOR flag
- MODEL_EXISTENCE_ONLY flag
- REGRESSOR column
- columns [data mining], modeling flags
- NOT NULL modeling flag
- modeling flags [data mining]
- null values [Analysis Services]
- MODEL_EXISTENCE_ONLY column
- coding [Data Mining]
ms.assetid: 8826d5ce-9ba8-4490-981b-39690ace40a4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0f1c802f6503b84ff4f6879c18d3bffebb46d7ad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687370"
---
# <a name="modeling-flags-data-mining"></a><span data-ttu-id="251da-102">模型旗標 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="251da-102">Modeling Flags (Data Mining)</span></span>
  <span data-ttu-id="251da-103">您可以使用中的模型旗標 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ，將有關案例資料表中所定義資料的其他資訊提供給資料採礦演算法。</span><span class="sxs-lookup"><span data-stu-id="251da-103">You can use modeling flags in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to provide additional information to a data mining algorithm about the data that is defined in a case table.</span></span> <span data-ttu-id="251da-104">演算法可以使用此一資訊建立更精確的資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="251da-104">The algorithm can use this information to build a more accurate data mining model.</span></span>  
  
 <span data-ttu-id="251da-105">有些模型旗標會定義於採礦結構層級，有些則會定義於採礦模型資料行的層級。</span><span class="sxs-lookup"><span data-stu-id="251da-105">Some modeling flags are defined at the level of the mining structure, whereas others are defined at the level of the mining model column.</span></span> <span data-ttu-id="251da-106">例如，`NOT NULL` 模型旗標是用於採礦結構資料行。</span><span class="sxs-lookup"><span data-stu-id="251da-106">For example, the `NOT NULL` modeling flag is used with mining structure columns.</span></span> <span data-ttu-id="251da-107">您可以根據您用來建立模型的演算法，在採礦模型資料行上定義其他模型旗標。</span><span class="sxs-lookup"><span data-stu-id="251da-107">You can define additional modeling flags on the mining model columns, depending on the algorithm you use to create the model.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="251da-108">除了 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]預先定義的模型旗標外，協力廠商外掛程式也可能擁有其他的模型旗標。</span><span class="sxs-lookup"><span data-stu-id="251da-108">Third-party plug-ins might have other modeling flags, in addition to those pre-defined by [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="list-of-modeling-flags"></a><span data-ttu-id="251da-109">模型旗標的清單</span><span class="sxs-lookup"><span data-stu-id="251da-109">List of Modeling Flags</span></span>  
 <span data-ttu-id="251da-110">下列清單描述 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]中支援的模型旗標。</span><span class="sxs-lookup"><span data-stu-id="251da-110">The following list describes the modeling flags that are supported in [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="251da-111">如需有關特定演算法所支援之模型旗標的詳細資訊，請參閱之前用來建立模型之演算法的技術參考主題。</span><span class="sxs-lookup"><span data-stu-id="251da-111">For information about modeling flags that are supported by specific algorithms, see the technical reference topic for the algorithm that was used to create the model.</span></span>  
  
 `NOT NULL`  
 <span data-ttu-id="251da-112">表示屬性資料行的值絕對不能包含 Null 值。</span><span class="sxs-lookup"><span data-stu-id="251da-112">Indicates that the values for the attribute column should never contain a null value.</span></span> <span data-ttu-id="251da-113">如果 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 在模型培訓處理過程中遇到這個屬性資料行的 Null 值，將會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="251da-113">An error will result if [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] encounters a null value for this attribute column during the model training process.</span></span>  
  
 <span data-ttu-id="251da-114">**MODEL_EXISTENCE_ONLY**</span><span class="sxs-lookup"><span data-stu-id="251da-114">**MODEL_EXISTENCE_ONLY**</span></span>  
 <span data-ttu-id="251da-115">表示將資料行視為有兩個狀態：`Missing` 和 `Existing`。</span><span class="sxs-lookup"><span data-stu-id="251da-115">Indicates that the column will be treated as having two states: `Missing` and `Existing`.</span></span> <span data-ttu-id="251da-116">若值為 `NULL`，則會視為「遺漏」。</span><span class="sxs-lookup"><span data-stu-id="251da-116">If the value is `NULL`, it is treated as Missing.</span></span> <span data-ttu-id="251da-117">MODEL_EXISTENCE_ONLY 旗標會套用到可預測的屬性，而且受到大多數的演算法所支援。</span><span class="sxs-lookup"><span data-stu-id="251da-117">The MODEL_EXISTENCE_ONLY flag is applied to the predictable attribute and is supported by most algorithms.</span></span>  
  
 <span data-ttu-id="251da-118">實際上，將 MODEL_EXISTENCE_ONLY 旗標設定為 `True` 會變更值的表示法，因此只會有兩個狀態：`Missing` 和 `Existing`。</span><span class="sxs-lookup"><span data-stu-id="251da-118">In effect, setting the MODEL_EXISTENCE_ONLY flag to `True` changes the representation of the values such that there are only two states: `Missing` and `Existing`.</span></span> <span data-ttu-id="251da-119">所有非遺漏狀態都會結合到單一 `Existing` 值中。</span><span class="sxs-lookup"><span data-stu-id="251da-119">All the non-missing states are combined into a single `Existing` value.</span></span>  
  
 <span data-ttu-id="251da-120">此模型旗標的一般用法是 `NULL` 狀態具有隱含意義的屬性，而 `NOT NULL` 狀態的明確值則可能不如資料行擁有任何值來得重要。</span><span class="sxs-lookup"><span data-stu-id="251da-120">A typical use for this modeling flag would be in attributes for which the `NULL` state has an implicit meaning, and the explicit value of the `NOT NULL` state might not be as important as the fact that the column has any value.</span></span> <span data-ttu-id="251da-121">例如，如果從未簽署過合約，[DateContractSigned] 資料行可能為 `NULL`，如果簽署了合約，則為 `NOT NULL`。</span><span class="sxs-lookup"><span data-stu-id="251da-121">For example, a [DateContractSigned] column might be `NULL` if a contract was never signed and `NOT NULL` if the contract was signed.</span></span> <span data-ttu-id="251da-122">因此，如果模型的用途是預測是否會簽署合約，可以使用 MODEL_EXISTENCE_ONLY 旗標來忽略 `NOT NULL` 案例中的精確日期值，並僅區分合約為 `Missing` 或 `Existing` 的案例。</span><span class="sxs-lookup"><span data-stu-id="251da-122">Therefore, if the purpose of the model is to predict whether a contract will be signed, you can use the MODEL_EXISTENCE_ONLY flag to ignore the exact date value in the `NOT NULL` cases and distinguish only between cases where a contract is `Missing` or `Existing`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="251da-123">「遺漏」是演算法所使用的特殊狀態，與資料行中的文字值「遺漏」不同。</span><span class="sxs-lookup"><span data-stu-id="251da-123">Missing is a special state used by the algorithm, and differs from the text value "Missing" in a column.</span></span> <span data-ttu-id="251da-124">如需詳細資訊，請參閱 [遺漏值 &#40;Analysis Services - 資料採礦&#41;](missing-values-analysis-services-data-mining.md)預先定義的模型旗標外，協力廠商外掛程式也可能擁有其他的模型旗標。</span><span class="sxs-lookup"><span data-stu-id="251da-124">For more information, see [Missing Values &#40;Analysis Services - Data Mining&#41;](missing-values-analysis-services-data-mining.md).</span></span>  
  
 `REGRESSOR`  
 <span data-ttu-id="251da-125">指出資料行是處理期間做為迴歸輸入變數使用的候選選項。</span><span class="sxs-lookup"><span data-stu-id="251da-125">Indicates that the column is a candidate for used as a regressor during processing.</span></span> <span data-ttu-id="251da-126">這個旗標是在採礦模型資料行上定義，並且只能套用至採用連續數值資料類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="251da-126">This flag is defined on a mining model column, and can only be applied to columns that have a continuous numeric data type.</span></span> <span data-ttu-id="251da-127">如需有關使用這個旗標的詳細資訊，請參閱本主題的 [使用 REGRESSOR 模型旗標](#bkmk_UseRegressors)一節。</span><span class="sxs-lookup"><span data-stu-id="251da-127">For more information about the use of this flag, see the section in this topic, [Uses of the REGRESSOR Modeling Flag](#bkmk_UseRegressors).</span></span>  
  
## <a name="viewing-and-changing-modeling-flags"></a><span data-ttu-id="251da-128">檢視和變更模型旗標</span><span class="sxs-lookup"><span data-stu-id="251da-128">Viewing and Changing Modeling Flags</span></span>  
 <span data-ttu-id="251da-129">在資料採礦設計師中，您可以藉由檢視結構或模型的屬性來檢視與採礦結構資料行或模型資料行相關聯的模型旗標。</span><span class="sxs-lookup"><span data-stu-id="251da-129">You can view the modeling flags associated with a mining structure column or model column in Data Mining Designer by viewing the properties of the structure or model.</span></span>  
  
 <span data-ttu-id="251da-130">若要判斷哪些模型旗標已經套用至目前的採礦結構，您可以使用類似以下的查詢，針對傳回結構資料行之模型旗標的資料採礦結構描述資料列集來建立查詢：</span><span class="sxs-lookup"><span data-stu-id="251da-130">To determine which modeling flags have been applied to the current mining structure, you can create a query against the data mining schema rowset that returns the modeling flags for just the structure columns, by using a query like the following:</span></span>  
  
```  
SELECT COLUMN_NAME, MODELING_FLAG  
FROM $system.DMSCHEMA_MINING_STRUCTURE_COLUMNS  
WHERE STRUCTURE_NAME = '<structure name>'  
```  
  
 <span data-ttu-id="251da-131">您可以加入或變更模型中所使用的模型旗標，方法是使用資料採礦設計師及編輯關聯資料行的屬性。</span><span class="sxs-lookup"><span data-stu-id="251da-131">You can add or change the modeling flags used in a model by using the Data Mining Designer and editing the properties of the associated columns.</span></span> <span data-ttu-id="251da-132">這類變更需要重新處理結構或模型。</span><span class="sxs-lookup"><span data-stu-id="251da-132">Such changes require that the structure or model be reprocessed.</span></span>  
  
 <span data-ttu-id="251da-133">您可以使用 DMX 或是 AMO 或 XMLA 指令碼，在新的採礦結構或採礦模型中指定模型旗標。</span><span class="sxs-lookup"><span data-stu-id="251da-133">You can specify modeling flags in a new mining structure or mining model by using DMX, or by using AMO or XMLA scripts.</span></span> <span data-ttu-id="251da-134">但是，您不能使用 DMX 變更在現有採礦模型和結構中使用的模型旗標。</span><span class="sxs-lookup"><span data-stu-id="251da-134">However, you cannot change the modeling flags used in an existing mining model and structure by using DMX.</span></span> <span data-ttu-id="251da-135">您必須使用 `ALTER MINING STRUCTURE....ADD MINING MODEL`語法建立新的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="251da-135">You must create a new mining model by using the syntax, `ALTER MINING STRUCTURE....ADD MINING MODEL`.</span></span>  
  
##  <a name="uses-of-the-regressor-modeling-flag"></a><a name="bkmk_UseRegressors"></a><span data-ttu-id="251da-136">使用回歸輸入變數模型旗標</span><span class="sxs-lookup"><span data-stu-id="251da-136">Uses of the REGRESSOR Modeling Flag</span></span>  
 <span data-ttu-id="251da-137">在資料行上設定 REGRESSOR 模型旗標亦即向演算法表示，該資料行包含潛在的迴歸輸入變數。</span><span class="sxs-lookup"><span data-stu-id="251da-137">When you set the REGRESSOR modeling flag on a column, you are indicating to the algorithm that the column contains potential regressors.</span></span> <span data-ttu-id="251da-138">模型中使用的實際迴歸輸入變數是依照演算法而定。</span><span class="sxs-lookup"><span data-stu-id="251da-138">The actual regressors that are used in the model are determined by the algorithm.</span></span> <span data-ttu-id="251da-139">如果潛在的迴歸輸入變數無法將可預測屬性模型化，則可能會遭到捨棄。</span><span class="sxs-lookup"><span data-stu-id="251da-139">A potential regressor can be discarded if it does not model the predictable attribute.</span></span>  
  
 <span data-ttu-id="251da-140">使用資料採礦精靈建立模型時，所有連續的輸入資料行都會標記為可能的迴歸輸入變數。</span><span class="sxs-lookup"><span data-stu-id="251da-140">When you build a model by using the Data Mining wizard, all continuous input columns are flagged as possible regressors.</span></span> <span data-ttu-id="251da-141">因此，即使未在資料行上明確地設定 REGRESSOR 旗標，也可能會在模型中將該資料行當做迴歸輸入變數使用。</span><span class="sxs-lookup"><span data-stu-id="251da-141">Therefore, even if you do not explicitly set the REGRESSOR flag on a column, the column might be used as a regressor in the model.</span></span>  
  
 <span data-ttu-id="251da-142">您可以針對採礦模型的結構描述資料列集執行查詢來判斷實際用於已處理模型的迴歸輸入變數，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="251da-142">You can determine the regressors that were actually used in the processed model by performing a query against the schema rowset for the mining model, as shown in the following example:</span></span>  
  
```  
SELECT COLUMN_NAME, MODELING_FLAG  
FROM $system.DMSCHEMA_MINING_COLUMNS  
WHERE MODEL_NAME = '<model name>'  
```  
  
 <span data-ttu-id="251da-143">**注意** ：如果您修改採礦模型並將資料行的內容類型從連續變更為離散，則必須手動變更採礦資料行上的旗標，然後重新處理模型。</span><span class="sxs-lookup"><span data-stu-id="251da-143">**Note** If you modify a mining model and change the content type of a column from continuous to discrete, you must manually change the flag on the mining column and then reprocess the model.</span></span>  
  
### <a name="regressors-in-linear-regression-models"></a><span data-ttu-id="251da-144">線性迴歸模型中的迴歸輸入變數</span><span class="sxs-lookup"><span data-stu-id="251da-144">Regressors in Linear Regression Models</span></span>  
 <span data-ttu-id="251da-145">線性迴歸模型是以 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 決策樹演算法為基礎。</span><span class="sxs-lookup"><span data-stu-id="251da-145">Linear regression models are based on the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm.</span></span> <span data-ttu-id="251da-146">即使您不使用 [!INCLUDE[msCoName](../../includes/msconame-md.md)] 線性迴歸演算法，任何決策樹模型仍可能包含代表連續屬性迴歸的樹狀結構或節點。</span><span class="sxs-lookup"><span data-stu-id="251da-146">Even if you do not use the [!INCLUDE[msCoName](../../includes/msconame-md.md)] Linear Regression algorithm, any decision tree model can contain a tree or nodes that represents a regression on a continuous attribute.</span></span>  
  
 <span data-ttu-id="251da-147">因此您在這些模型中，不需要指定代表迴歸輸入變數的連續資料行。</span><span class="sxs-lookup"><span data-stu-id="251da-147">Therefore, in these models you do not need to specify that a continuous column represents a regressor.</span></span> <span data-ttu-id="251da-148">即使未在資料行上設定 REGRESSOR 旗標， [!INCLUDE[msCoName](../../includes/msconame-md.md)] 決策樹演算法也會將資料集分割成具備有意義之模式的區域。</span><span class="sxs-lookup"><span data-stu-id="251da-148">The [!INCLUDE[msCoName](../../includes/msconame-md.md)] Decision Trees algorithm will partition the dataset into regions with meaningful patterns even if you do not set the REGRESSOR flag on the column.</span></span> <span data-ttu-id="251da-149">其差異是當您設定模型旗標時，演算法會嘗試尋找以下形式的迴歸方程式，在樹狀結構的節點中比對模式。</span><span class="sxs-lookup"><span data-stu-id="251da-149">The difference is that when you set the modeling flag, the algorithm will try to find regression equations of the following form to fit the patterns in the nodes of  the tree.</span></span>  
  
 <span data-ttu-id="251da-150">a\*C1 + b\*C2 + ...</span><span class="sxs-lookup"><span data-stu-id="251da-150">a\*C1 + b\*C2 + ...</span></span>  
  
 <span data-ttu-id="251da-151">然後會計算剩餘數的總和，如果差異過大，就會在樹狀結構中強制進行分割。</span><span class="sxs-lookup"><span data-stu-id="251da-151">Then, the sum of the residuals is calculated, and if the deviation is too great, a split is forced in the tree.</span></span>  
  
 <span data-ttu-id="251da-152">例如，如果您使用 **Income** 做為屬性來預測客戶購買行為，且在資料行上設定 REGRESSOR 模型旗標，則演算法首先會使用標準迴歸公式來比對 **Income** 值。</span><span class="sxs-lookup"><span data-stu-id="251da-152">For example, if you are predicting customer purchasing behavior using **Income** as an attribute, and set the REGRESSOR modeling flag on the column, the algorithm would first try to fit the **Income** values by using a standard regression formula.</span></span> <span data-ttu-id="251da-153">如果差異過大，就會放棄迴歸公式，且根據其他的屬性分割樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="251da-153">If the deviation is too great, the regression formula is abandoned and the tree would be split on some other attribute.</span></span> <span data-ttu-id="251da-154">在分割之後，決策樹演算法就會接著嘗試在每個分支中比對迴歸輸入變數與收入。</span><span class="sxs-lookup"><span data-stu-id="251da-154">The decision tree algorithm would then try fit a regressor for income in each of the branches after the split.</span></span>  
  
 <span data-ttu-id="251da-155">您可以使用 FORCE_REGRESSOR 參數來確保演算法會使用特定的迴歸輸入變數。</span><span class="sxs-lookup"><span data-stu-id="251da-155">You can use the FORCE_REGRESSOR parameter to guarantee that the algorithm will use a particular regressor.</span></span> <span data-ttu-id="251da-156">這個參數可用於決策樹演算法及線性迴歸演算法。</span><span class="sxs-lookup"><span data-stu-id="251da-156">This parameter can be used with the Decision Trees algorithm and Linear Regression algorithm.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="251da-157">相關工作</span><span class="sxs-lookup"><span data-stu-id="251da-157">Related Tasks</span></span>  
 <span data-ttu-id="251da-158">使用下列連結，深入了解如何使用模型旗標。</span><span class="sxs-lookup"><span data-stu-id="251da-158">Use the following links to learn more about using modeling flags.</span></span>  
  
|<span data-ttu-id="251da-159">Task</span><span class="sxs-lookup"><span data-stu-id="251da-159">Task</span></span>|<span data-ttu-id="251da-160">主題</span><span class="sxs-lookup"><span data-stu-id="251da-160">Topic</span></span>|  
|----------|-----------|  
|<span data-ttu-id="251da-161">使用資料採礦設計師來編輯模型旗標</span><span class="sxs-lookup"><span data-stu-id="251da-161">Edit modeling flags by using the Data Mining Designer</span></span>|[<span data-ttu-id="251da-162">檢視或變更模型旗標 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="251da-162">View or Change Modeling Flags &#40;Data Mining&#41;</span></span>](modeling-flags-data-mining.md)|  
|<span data-ttu-id="251da-163">為演算法指定提示，以建議可能的迴歸輸入變數</span><span class="sxs-lookup"><span data-stu-id="251da-163">Specify a hint to the algorithm to recommend likely regressors</span></span>|[<span data-ttu-id="251da-164">在模型中指定當做迴歸輸入變數使用的資料行</span><span class="sxs-lookup"><span data-stu-id="251da-164">Specify a Column to Use as Regressor in a Model</span></span>](specify-a-column-to-use-as-regressor-in-a-model.md)|  
|<span data-ttu-id="251da-165">請參閱特定演算法所支援的模型旗標 (在每一個演算法參考主題的＜模型旗標＞一節內)。</span><span class="sxs-lookup"><span data-stu-id="251da-165">See the modeling flags supported by specific algorithms (in the Modeling Flags section for each algorithm reference topic)</span></span>|[<span data-ttu-id="251da-166">資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="251da-166">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](data-mining-algorithms-analysis-services-data-mining.md)|  
|<span data-ttu-id="251da-167">深入了解採礦結構資料行以及您可以在資料行上設定的屬性</span><span class="sxs-lookup"><span data-stu-id="251da-167">Learn more about mining structure columns and the properties that you can set on them</span></span>|[<span data-ttu-id="251da-168">採礦結構資料行</span><span class="sxs-lookup"><span data-stu-id="251da-168">Mining Structure Columns</span></span>](mining-structure-columns.md)|  
|<span data-ttu-id="251da-169">深入了解採礦模型資料行以及可以在模型層級套用的模型旗標</span><span class="sxs-lookup"><span data-stu-id="251da-169">Learn about mining model columns and modeling flags that can be applied at the model level</span></span>|[<span data-ttu-id="251da-170">採礦模型資料行</span><span class="sxs-lookup"><span data-stu-id="251da-170">Mining Model Columns</span></span>](mining-model-columns.md)|  
|<span data-ttu-id="251da-171">請參閱在 DMX 陳述式中搭配模型旗標使用的語法</span><span class="sxs-lookup"><span data-stu-id="251da-171">See syntax for  working with modeling  flags in DMX statements</span></span>|[<span data-ttu-id="251da-172">模型旗標 &#40;DMX&#41;</span><span class="sxs-lookup"><span data-stu-id="251da-172">Modeling Flags &#40;DMX&#41;</span></span>](/sql/dmx/modeling-flags-dmx)|  
|<span data-ttu-id="251da-173">了解遺漏的值以及如何處理這些值</span><span class="sxs-lookup"><span data-stu-id="251da-173">Understand missing values and how to work with  them</span></span>|[<span data-ttu-id="251da-174">遺漏值 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="251da-174">Missing Values &#40;Analysis Services - Data Mining&#41;</span></span>](missing-values-analysis-services-data-mining.md)|  
|<span data-ttu-id="251da-175">了解如何管理模型和結構以及設定使用屬性</span><span class="sxs-lookup"><span data-stu-id="251da-175">Learn about managing models and structures and setting usage properties</span></span>|[<span data-ttu-id="251da-176">移動資料採礦物件</span><span class="sxs-lookup"><span data-stu-id="251da-176">Moving Data Mining Objects</span></span>](moving-data-mining-objects.md)|  
  
  
