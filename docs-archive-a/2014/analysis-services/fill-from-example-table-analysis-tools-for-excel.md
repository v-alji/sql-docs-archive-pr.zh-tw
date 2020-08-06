---
title: " (適用于 Excel) 的資料表分析工具範例填滿 |Microsoft Docs"
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- fill from example
ms.assetid: dac57d8f-1c65-4878-8ea0-9c680df5e4fb
author: minewiskan
ms.author: owend
ms.openlocfilehash: 69ff9f554c51240eb6f9151718d30677bfb57996
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700480"
---
# <a name="fill-from-example-table-analysis-tools-for-excel"></a><span data-ttu-id="60537-102">根據範例填滿 (適用於 Excel 的資料表分析工具)</span><span class="sxs-lookup"><span data-stu-id="60537-102">Fill From Example (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="60537-103">![資料表分析工具中的根據範例填滿按鈕](media/tat-fillex.gif "資料表分析工具中的根據範例填滿按鈕")</span><span class="sxs-lookup"><span data-stu-id="60537-103">![Fill From Example button in Table Analysis Tools](media/tat-fillex.gif "Fill From Example button in Table Analysis Tools")</span></span>  
  
 <span data-ttu-id="60537-104">[**根據範例填滿**] 工具可協助您根據現有的值建立新的資料行。</span><span class="sxs-lookup"><span data-stu-id="60537-104">The **Fill From Example** tool helps you build new columns of data based on existing values.</span></span>  
  
 <span data-ttu-id="60537-105">例如，假設您的資料包含 [**採購金額**] 資料行、[**訂單數量**] 資料行和 [**頂級客戶**] 資料行，其以使用其他資料行的公式為基礎。</span><span class="sxs-lookup"><span data-stu-id="60537-105">For example, suppose your data contains a **Purchase Amount** column, an **Orders Quantity** column, and a **Premier Customer** column that is based on some formula using the other columns.</span></span> <span data-ttu-id="60537-106">如果 [**頂級客戶**] 資料行包含許多空白資料列，您可以使用 [**購買數量**] 和 [**訂單數量**] 欄做為輸入，以推斷遺漏的值。</span><span class="sxs-lookup"><span data-stu-id="60537-106">If the  **Premier Customer** column contains many blank rows, you could use the **Purchase Amount** and **Orders Quantity** columns as the inputs, to infer the missing values.</span></span> <span data-ttu-id="60537-107">此工具會分析資料中現有的模式連同您所輸入的範例，並且預測每個客戶將獲指派的分類。</span><span class="sxs-lookup"><span data-stu-id="60537-107">The tool analyzes existing patterns in the data together with the examples you entered, and predicts which category to assign to each customer.</span></span>  
  
 <span data-ttu-id="60537-108">如果您對結果感到不滿意，可提供更多範例來改善結果。</span><span class="sxs-lookup"><span data-stu-id="60537-108">If you are not satisfied with the results, you can refine the results by providing more examples.</span></span>  
  
## <a name="using-the-fill-from-example-tool"></a><span data-ttu-id="60537-109">使用根據範例填滿工具</span><span class="sxs-lookup"><span data-stu-id="60537-109">Using the Fill From Example Tool</span></span>  
  
1.  <span data-ttu-id="60537-110">在 [**分析**] 功能區中，按一下 [**根據範例填滿**]。</span><span class="sxs-lookup"><span data-stu-id="60537-110">In the **Analyze** ribbon, click **Fill From Example**.</span></span>  
  
2.  <span data-ttu-id="60537-111">此工具將會根據資料分析自動挑選要填滿的資料行，而且您可以接受或覆寫這項建議。</span><span class="sxs-lookup"><span data-stu-id="60537-111">The tool will automatically pick a column to fill based on analysis of the data, and you can either accept or override this suggestion.</span></span>  
  
3.  <span data-ttu-id="60537-112">為新的資料建立資料行，並輸入您所要預測的資料範例。</span><span class="sxs-lookup"><span data-stu-id="60537-112">Create a column for the new data, and type in examples of the data that you want to predict.</span></span> <span data-ttu-id="60537-113">確定您所要預測的每個值至少都有一個範例。</span><span class="sxs-lookup"><span data-stu-id="60537-113">Make sure that there is at least one example for every value that you want to predict.</span></span> <span data-ttu-id="60537-114">如果是在將資料填滿到現有的資料行中，請選取具有遺失值的資料行。</span><span class="sxs-lookup"><span data-stu-id="60537-114">If you are filling in data in an existing column, select the column that has missing values.</span></span>  
  
4.  <span data-ttu-id="60537-115">（選擇性）按一下 **[選擇要用於分析的資料行**]。</span><span class="sxs-lookup"><span data-stu-id="60537-115">Optionally, click **Choose columns to be used in analysis**.</span></span> <span data-ttu-id="60537-116">在 [資料**行選取範圍**] 對話方塊中，指定填入遺漏的資料時，最有可能有用的資料行。</span><span class="sxs-lookup"><span data-stu-id="60537-116">In the **Advanced Columns Selection** dialog box, specify the columns that are most likely to be useful when filling in the missing data.</span></span>  
  
     <span data-ttu-id="60537-117">例如，如果您從經驗得知，某個資料行與另一個具有遺失值的資料行之間有因果關係，即可取消選取其他資料行來獲得更好的結果。</span><span class="sxs-lookup"><span data-stu-id="60537-117">For example, if you know from experience that there is a causal effect between one column and the column that has missing values, you can deselect other columns to get better results.</span></span>  
  
     <span data-ttu-id="60537-118">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="60537-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="60537-119">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="60537-119">Click **Run**.</span></span>  
  
     <span data-ttu-id="60537-120">分析完成時，工具會建立新的**模式**工作表，其中包含分析的結果。</span><span class="sxs-lookup"><span data-stu-id="60537-120">When analysis is complete, the tool creates a new **Patterns** worksheet that contains the results of analysis.</span></span> <span data-ttu-id="60537-121">此報表會列出找到的規則或關鍵影響因數，並且顯示每個規則的機率。</span><span class="sxs-lookup"><span data-stu-id="60537-121">The report lists the rules, or key influencers, that were found, and shows the probability for each rule.</span></span>  
  
     <span data-ttu-id="60537-122">此工具也會將包含新值的資料行加入到原始的資料表。</span><span class="sxs-lookup"><span data-stu-id="60537-122">The tool also automatically adds a column that contains the new values to the original data table.</span></span> <span data-ttu-id="60537-123">您可以檢閱這些值，並且將其與原始的值比較。</span><span class="sxs-lookup"><span data-stu-id="60537-123">You can review the values and compare them against the original.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="60537-124">需求</span><span class="sxs-lookup"><span data-stu-id="60537-124">Requirements</span></span>  
 <span data-ttu-id="60537-125">您只能使用在資料行中的資料。</span><span class="sxs-lookup"><span data-stu-id="60537-125">You can only work with data in columns.</span></span> <span data-ttu-id="60537-126">如果您要填滿的數列存放在資料列中，您可以使用 Excel 中的 Paste、Transpose 函數將資料變更為單欄式格式。</span><span class="sxs-lookup"><span data-stu-id="60537-126">If the series that you want to fill is stored in a row, you can use the Paste, Transpose function in Excel to change the data to a columnar format.</span></span>  
  
## <a name="understanding-the-pattern-report"></a><span data-ttu-id="60537-127">了解模式報表</span><span class="sxs-lookup"><span data-stu-id="60537-127">Understanding the Pattern Report</span></span>  
 <span data-ttu-id="60537-128">當您執行 [**根據範例填滿**] 工具時，會建立一份報告，提供所偵測到之模式的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="60537-128">When you run the **Fill From Example** tool, a report is created that provides more information about the patterns that were detected.</span></span> <span data-ttu-id="60537-129">這些模式會用於推斷新的資料值。</span><span class="sxs-lookup"><span data-stu-id="60537-129">These patterns are used for extrapolating new data values.</span></span>  
  
 <span data-ttu-id="60537-130">模式報表會顯示所預測之每個值的關鍵影響因數。</span><span class="sxs-lookup"><span data-stu-id="60537-130">The Pattern Report shows the key influencers for each value that was predicted.</span></span> <span data-ttu-id="60537-131">每個影響因數或規則都會被描述為資料行、該資料行中的值，以及規則對於預測之相對影響的組合。</span><span class="sxs-lookup"><span data-stu-id="60537-131">Each influencer or rule is described as a combination of a column, the value in that column, and the relative impact of the rule on the prediction.</span></span>  
  
 <span data-ttu-id="60537-132">例如，如果您嘗試填滿顯示訂單運輸距離的工作表，便能在邏輯上期待目的地會對運輸距離值具有強烈影響。</span><span class="sxs-lookup"><span data-stu-id="60537-132">For example, if you were trying to fill in a worksheet that shows the shipping distance for orders, you might logically expect the destination to have a strong impact on the value for shipping distance.</span></span> <span data-ttu-id="60537-133">在此情況下，報表可能會包含以下資料列：</span><span class="sxs-lookup"><span data-stu-id="60537-133">In this case, the report might contain the following row:</span></span>  
  
|<span data-ttu-id="60537-134">資料行</span><span class="sxs-lookup"><span data-stu-id="60537-134">Column</span></span>|<span data-ttu-id="60537-135">值</span><span class="sxs-lookup"><span data-stu-id="60537-135">Value</span></span>|<span data-ttu-id="60537-136">喜好</span><span class="sxs-lookup"><span data-stu-id="60537-136">Favors</span></span>|<span data-ttu-id="60537-137">相對影響</span><span class="sxs-lookup"><span data-stu-id="60537-137">Relative Impact</span></span>|  
|------------|-----------|------------|---------------------|  
|<span data-ttu-id="60537-138">StateProvinceCode</span><span class="sxs-lookup"><span data-stu-id="60537-138">StateProvinceCode</span></span>|<span data-ttu-id="60537-139">AB</span><span class="sxs-lookup"><span data-stu-id="60537-139">AB</span></span>|<span data-ttu-id="60537-140">>500 公里</span><span class="sxs-lookup"><span data-stu-id="60537-140">>500 kilometers</span></span>|<span data-ttu-id="60537-141">80%</span><span class="sxs-lookup"><span data-stu-id="60537-141">80%</span></span>|  
  
 <span data-ttu-id="60537-142">這表示**StateProvinceCode**資料行中的值 AB 會強烈預測 >500 公里的出貨距離。</span><span class="sxs-lookup"><span data-stu-id="60537-142">This means that the value AB in the **StateProvinceCode** column strongly predicts a shipping distance of >500 kilometers.</span></span>  
  
 <span data-ttu-id="60537-143">通常，預測都會根據複雜度遠勝於此範例的模式，而且報表可能會針對每項預測包含許多規則資料列。</span><span class="sxs-lookup"><span data-stu-id="60537-143">Typically, predictions are based on patterns that are far more complex than this example, and the report may contain many rows of rules for each prediction.</span></span> <span data-ttu-id="60537-144">所有規則的效果都會組合以衍生出預測值。</span><span class="sxs-lookup"><span data-stu-id="60537-144">The effect of all the rules are combined to derive the predicted value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="60537-145">**相對影響**會顯示為陰影橫條。</span><span class="sxs-lookup"><span data-stu-id="60537-145">**Relative Impact** is shown as a shaded bar.</span></span> <span data-ttu-id="60537-146">該橫條越長，這條規則也就越有可能是填滿值的預測。</span><span class="sxs-lookup"><span data-stu-id="60537-146">The longer the bar, the greater the probability that this rule is predictive of the filled-in value.</span></span>  
  
 <span data-ttu-id="60537-147">此工具也會將新的資料行加入至名為 Extended 的原始資料表 \<column name> 。</span><span class="sxs-lookup"><span data-stu-id="60537-147">The tool also adds a new column to the original data table, named \<column name> Extended.</span></span>  
  
 <span data-ttu-id="60537-148">如果原始的資料資料行包含某個值，該值便會複製到新資料行中。</span><span class="sxs-lookup"><span data-stu-id="60537-148">If the original data column contained a value, that value is copied into the new column.</span></span> <span data-ttu-id="60537-149">不過，如果原始的資料行包含空白的儲存格，新資料行便會包含由精靈所預測的值。</span><span class="sxs-lookup"><span data-stu-id="60537-149">However, if the original column contained a blank cell, the new column contains the value that was predicted by the wizard.</span></span>  
  
## <a name="related-tools-and-information"></a><span data-ttu-id="60537-150">相關工具和資訊</span><span class="sxs-lookup"><span data-stu-id="60537-150">Related Tools and Information</span></span>  
 <span data-ttu-id="60537-151">您也可以使用 [適用于 Excel 的資料採礦用戶端] 中的 [[流覽資料](explore-data-sql-server-data-mining-add-ins.md)] wizard，檢查 excel 資料行中的值分佈。</span><span class="sxs-lookup"><span data-stu-id="60537-151">You can also use the [Explore Data](explore-data-sql-server-data-mining-add-ins.md) wizard, available in the Data Mining Client for Excel, to examine the distribution of values in an Excel column.</span></span> <span data-ttu-id="60537-152">如需詳細資訊，請參閱[探索和清除資料](exploring-and-cleaning-data.md)。</span><span class="sxs-lookup"><span data-stu-id="60537-152">For more information, see [Exploring and Cleaning Data](exploring-and-cleaning-data.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60537-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="60537-153">See Also</span></span>  
 [<span data-ttu-id="60537-154">適用於 Excel 的資料表分析工具</span><span class="sxs-lookup"><span data-stu-id="60537-154">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
  
