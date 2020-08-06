---
title: '[資料集篩選器] 或 [模型篩選器] 對話方塊 |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a9602174-b7e2-4e16-8ded-dfd8eb9264d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: afa796cd8cb23894c059deba411b3e1d6676e3b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702150"
---
# <a name="data-set-filter-or-model-filter-dialog-box"></a><span data-ttu-id="e3119-102">資料集篩選器或模型篩選器對話方塊</span><span class="sxs-lookup"><span data-stu-id="e3119-102">Data Set Filter or Model Filter Dialog Box</span></span>
  <span data-ttu-id="e3119-103">這個對話方塊可協助您建立能套用至資料集的篩選器。</span><span class="sxs-lookup"><span data-stu-id="e3119-103">This dialog box helps you build the filters that you can apply to a data set.</span></span>  <span data-ttu-id="e3119-104">資料集可以是用於字串的外部資料集，或採礦模型的案例資料。</span><span class="sxs-lookup"><span data-stu-id="e3119-104">The data set can be an external data set used for testing, or the case data for a mining model.</span></span> <span data-ttu-id="e3119-105">對話方塊的名稱會根據篩選器是用於外部資料集或採礦模型而變更。</span><span class="sxs-lookup"><span data-stu-id="e3119-105">The name of the dialog box changes depending on whether the filter is for an external data set or for a mining model.</span></span>  
  
 <span data-ttu-id="e3119-106">如果是將篩選器套用至新的資料集，則僅會使用資料集中符合條件的案例來評估資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="e3119-106">If you apply the filter to a new data set, the data mining model is evaluated by using only those cases in the data set that meet the conditions.</span></span> <span data-ttu-id="e3119-107">如果是將篩選器套用至採礦模型本身，則僅會使用現有測試資料集中符合篩選準則的案例來培訓及測試模型。</span><span class="sxs-lookup"><span data-stu-id="e3119-107">If you apply the filter to the mining model itself, the model will be trained and tested by using only the cases in the existing test data set that meet the filter criteria.</span></span>  
  
-   <span data-ttu-id="e3119-108">[資料集篩選器]\*\*\*\* 對話方塊可從 [採礦精確度圖表]\*\*\*\* 設計師的 [輸入選擇]\*\*\*\* 索引標籤中存取。</span><span class="sxs-lookup"><span data-stu-id="e3119-108">The **Data Set Filter** dialog box is available from the **Input Selection** tab of the **Mining Accuracy Chart** designer.</span></span>  
  
-   <span data-ttu-id="e3119-109">[模型篩選器]\*\*\*\* 對話方塊可從資料採礦設計師的 [採礦模型]\*\*\*\* 索引標籤中存取。</span><span class="sxs-lookup"><span data-stu-id="e3119-109">The **Model Filter** dialog box is available from the **Mining Models** tab of the Data Miningdesigner.</span></span>  
  
-   <span data-ttu-id="e3119-110">您可在 [條件]\*\*\*\* 方格包含的資料行中指定資料表或資料行名稱、運算子和目標值。</span><span class="sxs-lookup"><span data-stu-id="e3119-110">The **Conditions** grid contains columns where you can specify a table or column name, an operator, and target values.</span></span> <span data-ttu-id="e3119-111">基本上，您可以藉由使用此方格來建立 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="e3119-111">By using this grid you are essentially creating a WHERE clause.</span></span>  
  
> [!TIP]  
>  <span data-ttu-id="e3119-112">若要測試原始定型資料子集的精確度，您可以加入曾用來將定型集定義為外部測試資料的資料來源檢視，然後在 [資料集篩選器]\*\*\*\* 方格中加入條件。</span><span class="sxs-lookup"><span data-stu-id="e3119-112">To test accuracy on a subset of the original training data, you can add the data source view that was used to define the training set as the external testing data, and then add conditions in the **Data Set Filter** grid.</span></span>  
  
 <span data-ttu-id="e3119-113">**如需詳細資訊，請參閱：** [測試和驗證 &#40;資料採礦&#41;](data-mining/testing-and-validation-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="e3119-113">**For more information:** [Testing and Validation &#40;Data Mining&#41;](data-mining/testing-and-validation-data-mining.md)</span></span>  
  
## <a name="options"></a><span data-ttu-id="e3119-114">選項</span><span class="sxs-lookup"><span data-stu-id="e3119-114">Options</span></span>  
 <span data-ttu-id="e3119-115">**條件**</span><span class="sxs-lookup"><span data-stu-id="e3119-115">**Conditions**</span></span>  
 <span data-ttu-id="e3119-116">顯示資料表名稱，後面跟著資料行名稱及條件。</span><span class="sxs-lookup"><span data-stu-id="e3119-116">Displays table names, followed by column names with conditions.</span></span>  
  
|<span data-ttu-id="e3119-117">值</span><span class="sxs-lookup"><span data-stu-id="e3119-117">Value</span></span>|<span data-ttu-id="e3119-118">描述</span><span class="sxs-lookup"><span data-stu-id="e3119-118">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e3119-119">**和/或**</span><span class="sxs-lookup"><span data-stu-id="e3119-119">**And/Or**</span></span>|<span data-ttu-id="e3119-120">選擇運算子來聯結多個條件。</span><span class="sxs-lookup"><span data-stu-id="e3119-120">Choose an operator to join multiple conditions.</span></span>|  
|<span data-ttu-id="e3119-121">**採礦結構資料行**</span><span class="sxs-lookup"><span data-stu-id="e3119-121">**Mining Structure Column**</span></span>|<span data-ttu-id="e3119-122">按一下以選取資料來源，然後再按一下方格中的連續行來從資料來源新增資料行。</span><span class="sxs-lookup"><span data-stu-id="e3119-122">Click to select a data source, and then click successive lines in the grid to add columns from the data source.</span></span><br /><br /> <span data-ttu-id="e3119-123">方格中的第一行會指定資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="e3119-123">The first line in the grid specifies the data source view.</span></span> <span data-ttu-id="e3119-124">在選取資料來源檢視之後，[採礦結構資料行]\*\*\*\* 會顯示資料表圖示，而 [值]\*\*\*\* 欄位則顯示已為此資料來源所定義之所有準則的組合。</span><span class="sxs-lookup"><span data-stu-id="e3119-124">After you select a data source view, **Mining Structure Column** displays a table icon, and the **Value** field displays the combination of all criteria that you have defined for this data source.</span></span><br /><br /> <span data-ttu-id="e3119-125">在選取資料來源之後，[採礦結構資料行]\*\*\*\* 方塊會提供資料來源中個別資料行的下拉式清單。</span><span class="sxs-lookup"><span data-stu-id="e3119-125">After you have selected a data source, the **Mining Structure Column** box provides a dropdown list of individual columns in the data source.</span></span>|  
|<span data-ttu-id="e3119-126">**運算子**</span><span class="sxs-lookup"><span data-stu-id="e3119-126">**Operator**</span></span>|<span data-ttu-id="e3119-127">從清單選取運算子。</span><span class="sxs-lookup"><span data-stu-id="e3119-127">Select an operator from the list.</span></span>|  
|<span data-ttu-id="e3119-128">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="e3119-128">**Value**</span></span>|<span data-ttu-id="e3119-129">對於資料表而言，[值]\*\*\*\* 欄位會顯示套用至資料來源的所有篩選組合。</span><span class="sxs-lookup"><span data-stu-id="e3119-129">For tables, the **Value** field shows the combination of all filters applied to the data source.</span></span> <span data-ttu-id="e3119-130">您也可以按一下文字方塊右邊的 [組建\*\* ( ... ) \*\* ] 按鈕，以開啟 [**篩選**] 對話方塊並建立條件。</span><span class="sxs-lookup"><span data-stu-id="e3119-130">You can also click the build **(...)** button at the right of the text box to open the **Filter** dialog box and build a condition.</span></span>|  
  
 <span data-ttu-id="e3119-131">**運算式**</span><span class="sxs-lookup"><span data-stu-id="e3119-131">**Expression**</span></span>  
 <span data-ttu-id="e3119-132">顯示您使用方格所建立的準則集。</span><span class="sxs-lookup"><span data-stu-id="e3119-132">Displays the set of criteria that you built by using the grid.</span></span>  
  
 <span data-ttu-id="e3119-133">**編輯查詢**</span><span class="sxs-lookup"><span data-stu-id="e3119-133">**Edit Query**</span></span>  
 <span data-ttu-id="e3119-134">變更篩選編輯模式，使您可以直接在 [運算式]\*\*\*\* 文字方塊中輸入篩選運算式。</span><span class="sxs-lookup"><span data-stu-id="e3119-134">Changes the filter editing mode so that you can type a filter expression directly in the **Expression** text box.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e3119-135">當您對篩選運算式進行手動變更之後，即使在 [**輸入選擇**] 索引標籤的 [**篩選運算式**] 方塊中儲存運算式之後，也無法返回方格編輯模式。如果您想要使用方格來建立運算式，就必須刪除現有的篩選條件運算式，然後再開始進行。</span><span class="sxs-lookup"><span data-stu-id="e3119-135">After you have made manual changes to the filter expression, you cannot return to grid edit mode, even after you have saved the expression in the **Filter Expression** box on the **Input Selection** tab. If you want to build an expression by using the grid, you must delete the existing filter expression and start over.</span></span>  
  
 <span data-ttu-id="e3119-136">**還原查詢編輯**</span><span class="sxs-lookup"><span data-stu-id="e3119-136">**Revert Query Edits**</span></span>  
 <span data-ttu-id="e3119-137">將方格還原至先前的狀態，並取消對篩選運算式所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="e3119-137">Restores the grid to its previous state and cancels any changes that you made to the filter expression.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3119-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e3119-138">See Also</span></span>  
 <span data-ttu-id="e3119-139">[測試和驗證工作，以及如何 &#40;資料採礦&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e3119-139">[Testing and Validation Tasks and How-tos &#40;Data Mining&#41;](data-mining/testing-and-validation-tasks-and-how-tos-data-mining.md) </span></span>  
 [<span data-ttu-id="e3119-140">&#40;資料採礦&#41;的挖掘精確度圖表設計工具</span><span class="sxs-lookup"><span data-stu-id="e3119-140">Mining Accuracy Chart Designer &#40;Data Mining&#41;</span></span>](mining-accuracy-chart-designer-data-mining.md)  
  
  
