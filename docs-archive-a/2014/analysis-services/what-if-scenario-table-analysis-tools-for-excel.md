---
title: 適用于 Excel) 的資料表分析工具 (假設案例 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- what if scenario
- scenario analysis
ms.assetid: 4df5a5c5-1983-4009-a7c5-cd340649fd2f
author: minewiskan
ms.author: owend
ms.openlocfilehash: 4bb5c5e866c1320c297fb4f2760bca58623f6601
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710829"
---
# <a name="what-if-scenario-table-analysis-tools-for-excel"></a><span data-ttu-id="85d3b-102">假設狀況 (適用於 Excel 的資料表分析工具</span><span class="sxs-lookup"><span data-stu-id="85d3b-102">What-If Scenario (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="85d3b-103">![資料表分析工具中的假設狀況按鈕](media/tat-whatif.gif "資料表分析工具中的假設狀況按鈕")</span><span class="sxs-lookup"><span data-stu-id="85d3b-103">![What If Scenario button in Table Analysis tools](media/tat-whatif.gif "What If Scenario button in Table Analysis tools")</span></span>

 <span data-ttu-id="85d3b-104">[**假設**] 狀況工具會分析現有資料中的模式，然後讓您評估在某個資料行中的變更對不同資料行的值有何影響。</span><span class="sxs-lookup"><span data-stu-id="85d3b-104">The **What-If** scenario tool analyzes patterns in existing data, and then enables you to evaluate the effect that changes in one column would have on the value of a different column.</span></span>

 <span data-ttu-id="85d3b-105">例如，您可以探索某個項目漲價對總銷售額的影響。</span><span class="sxs-lookup"><span data-stu-id="85d3b-105">For example, you could explore the effect of raising the price of an item on its total sales.</span></span>

 <span data-ttu-id="85d3b-106">此工具對於可建立的預測數目頗有彈性。</span><span class="sxs-lookup"><span data-stu-id="85d3b-106">The tool is flexible about the number of predictions you can create.</span></span> <span data-ttu-id="85d3b-107">在完成初始分析之後，您可以預測資料表中所有資料的變更，或是一次輸入一個測試值。</span><span class="sxs-lookup"><span data-stu-id="85d3b-107">After the initial analysis is complete, you can either predict changes for all the data in the table, or enter test values one at a time.</span></span>

## <a name="using-the-what-if-scenario-tool"></a><span data-ttu-id="85d3b-108">使用假設狀況工具</span><span class="sxs-lookup"><span data-stu-id="85d3b-108">Using the What-If Scenario Tool</span></span>

1.  <span data-ttu-id="85d3b-109">開啟 Excel 資料表。</span><span class="sxs-lookup"><span data-stu-id="85d3b-109">Open an Excel data table.</span></span>

2.  <span data-ttu-id="85d3b-110">按一下 [**案例**]，然後選取 [**假設**]。</span><span class="sxs-lookup"><span data-stu-id="85d3b-110">Click **Scenarios**, and then select **What-If**.</span></span>

3.  <span data-ttu-id="85d3b-111">在 [**案例**] 方塊中，選取包含您將變更之值的資料行，並將變更指定為特定值或變更的百分比 (增加或減少) 目前的值。</span><span class="sxs-lookup"><span data-stu-id="85d3b-111">In the **Scenario** box, select the column that contains the value you will change, and specify the change either as a specific value or as a percentage of change (either increased or decreased) on the current values.</span></span>

4.  <span data-ttu-id="85d3b-112">在 [**發生什麼**事] 方塊中，指定您想要評估其效果的資料行。</span><span class="sxs-lookup"><span data-stu-id="85d3b-112">In the **What happens to** box, specify the column for which you want to assess the effect.</span></span>

5.  <span data-ttu-id="85d3b-113">（選擇性）按一下 **[選擇要用於分析的資料行**]，選取可能有助於進行預測的資料行。</span><span class="sxs-lookup"><span data-stu-id="85d3b-113">Optionally, click **Choose columns to be used for analysis** to select columns that are likely to be useful in making the prediction.</span></span> <span data-ttu-id="85d3b-114">您也可以取消選取在偵測模式時可能不太有用的資料行，例如資料列識別碼或名稱。</span><span class="sxs-lookup"><span data-stu-id="85d3b-114">You can also deselect columns that are likely to be of little use in detecting patterns, such as row IDs or names.</span></span>

6.  <span data-ttu-id="85d3b-115">在 [**指定資料列或資料表**] 方塊中，選擇您是否要針對目前選取的資料列，或資料表中的一組完整資料評估影響。</span><span class="sxs-lookup"><span data-stu-id="85d3b-115">In the **Specify row or table** box, choose whether you want the impact assessed for the currently selected row only, or for the complete set of data in the table.</span></span>

7.  <span data-ttu-id="85d3b-116">如果您選取**這個資料列**，此工具就會在對話方塊中顯示結果。</span><span class="sxs-lookup"><span data-stu-id="85d3b-116">If you select **On this row**, the tool displays the result in the dialog box.</span></span> <span data-ttu-id="85d3b-117">當對話方塊維持開啟狀態時，您可以修改您的選擇來測試其他狀況。</span><span class="sxs-lookup"><span data-stu-id="85d3b-117">While the dialog box remains open, you can modify your selections to test other scenarios.</span></span>

8.  <span data-ttu-id="85d3b-118">如果您選取 [**整份資料表**]，此工具會在對話方塊中顯示狀態訊息，並將兩個新的資料行加入至原始的資料表。</span><span class="sxs-lookup"><span data-stu-id="85d3b-118">If you select **Entire table**, the tool displays a status message in the dialog box, and adds two new columns to the original data table.</span></span> <span data-ttu-id="85d3b-119">按一下 [**關閉**] 以查看工作表中的完整結果。</span><span class="sxs-lookup"><span data-stu-id="85d3b-119">Click **Close** to view the complete results in the worksheet.</span></span>

### <a name="requirements"></a><span data-ttu-id="85d3b-120">需求</span><span class="sxs-lookup"><span data-stu-id="85d3b-120">Requirements</span></span>
 <span data-ttu-id="85d3b-121">此工具會使用 Microsoft 羅吉斯迴歸演算法，此演算法支援數值或離散值的預測。</span><span class="sxs-lookup"><span data-stu-id="85d3b-121">This tool uses the Microsoft Logistic Regression algorithm, which supports prediction of either numeric or discrete values.</span></span> <span data-ttu-id="85d3b-122">但是，為了達成最好的結果，我們建議您採用以下最佳作法：</span><span class="sxs-lookup"><span data-stu-id="85d3b-122">However, to achieve the best results, we suggest the following best practices:</span></span>

-   <span data-ttu-id="85d3b-123">選取包含有用資訊的資料行來進行分析。</span><span class="sxs-lookup"><span data-stu-id="85d3b-123">Select columns for analysis that contain useful information.</span></span>

-   <span data-ttu-id="85d3b-124">如果您包含太少的資料行，便可能會難以取得結果。</span><span class="sxs-lookup"><span data-stu-id="85d3b-124">If you include too few columns it may be difficult to obtain a result.</span></span>

-   <span data-ttu-id="85d3b-125">如果您使用 [**至值**] 選項，則必須在方塊中輸入值，或從清單中選取值。</span><span class="sxs-lookup"><span data-stu-id="85d3b-125">If you use the **To value** option, you must type a value in the box or select a value from the list.</span></span>

-   <span data-ttu-id="85d3b-126">如果您使用 [**百分比**] 選項，請將變更設定為增加或減少百分比。</span><span class="sxs-lookup"><span data-stu-id="85d3b-126">If you use the **Percentage** option, set the change as a percentage increase or decrease.</span></span> <span data-ttu-id="85d3b-127">預設值為 120%，表示比目前的值增加 20%。</span><span class="sxs-lookup"><span data-stu-id="85d3b-127">The default is 120%, meaning a 20% increase over the current value.</span></span>

> [!NOTE]
>  <span data-ttu-id="85d3b-128">如果您沒有設定值，便可能會收到錯誤。</span><span class="sxs-lookup"><span data-stu-id="85d3b-128">If you do not set a value, you might receive an error.</span></span>

## <a name="understanding-the-results-of-what-if-analysis"></a><span data-ttu-id="85d3b-129">了解假設分析的結果</span><span class="sxs-lookup"><span data-stu-id="85d3b-129">Understanding the Results of What-If Analysis</span></span>
 <span data-ttu-id="85d3b-130">當您建立**假設**案例時，此工具會執行三項工作：</span><span class="sxs-lookup"><span data-stu-id="85d3b-130">When you create a **What-If** scenario, the tool does three things:</span></span>

-   <span data-ttu-id="85d3b-131">建立資料採礦結構來儲存與資料表中的資料有關的關鍵事實。</span><span class="sxs-lookup"><span data-stu-id="85d3b-131">Creates a data mining structure that stores key facts about the data in your table.</span></span>

-   <span data-ttu-id="85d3b-132">根據資料建立羅吉斯迴歸採礦模型。</span><span class="sxs-lookup"><span data-stu-id="85d3b-132">Creates a logistic regression mining model based on the data.</span></span>

-   <span data-ttu-id="85d3b-133">針對您所指定的每個值建立預測查詢。</span><span class="sxs-lookup"><span data-stu-id="85d3b-133">Creates a prediction query for each of the values you specify.</span></span>

 <span data-ttu-id="85d3b-134">您可以藉由指定**整個資料表**，一次輸出所有的預測。</span><span class="sxs-lookup"><span data-stu-id="85d3b-134">You can output all the predictions at one time by specifying **Entire table**.</span></span> <span data-ttu-id="85d3b-135">然後工具便會在原始的資料表中建立兩個新的資料行。</span><span class="sxs-lookup"><span data-stu-id="85d3b-135">The tool then creates two new columns in the original data table.</span></span>

 <span data-ttu-id="85d3b-136">加入資料表中的資料行會包含兩種資訊類型：變更的預測值及其信心。</span><span class="sxs-lookup"><span data-stu-id="85d3b-136">The columns that are added to the table contain two types of information: the predicted value given the change, and its confidence.</span></span> <span data-ttu-id="85d3b-137">信心表示預測正確的機率。</span><span class="sxs-lookup"><span data-stu-id="85d3b-137">Confidence means the probability that the prediction is correct.</span></span>

 <span data-ttu-id="85d3b-138">您也可以在對話方塊中逐一輸入變更值，並以互動的方式檢視預測。</span><span class="sxs-lookup"><span data-stu-id="85d3b-138">You can also enter change values one by one in the dialog box, and view the predictions interactively.</span></span> <span data-ttu-id="85d3b-139">這與建立*單一預測查詢*相同。</span><span class="sxs-lookup"><span data-stu-id="85d3b-139">This is the same as creating a *singleton prediction query*.</span></span> <span data-ttu-id="85d3b-140">預測查詢的結果是具有下列資訊的輸出：預測的成功或失敗、預測的值，以及信心層級。</span><span class="sxs-lookup"><span data-stu-id="85d3b-140">The results of the prediction query are output with the following information: the success or failure of prediction, the predicted value, and the confidence level.</span></span> <span data-ttu-id="85d3b-141">信心層級會被顯示為包含虛線的列。</span><span class="sxs-lookup"><span data-stu-id="85d3b-141">The confidence level is shown as a bar that contains a dotted line.</span></span> <span data-ttu-id="85d3b-142">虛線越長，結果中的信心就越高。</span><span class="sxs-lookup"><span data-stu-id="85d3b-142">The longer the dotted line, the higher the confidence in the result.</span></span>

 <span data-ttu-id="85d3b-143">例如，如果您想要判斷增加客戶在購買客戶的年齡時的影響，以及將客戶的年齡增加至25，**假設**工具會查詢資料採礦模型並傳回下列結果：</span><span class="sxs-lookup"><span data-stu-id="85d3b-143">For example, if you are trying to determine the effect of increasing the customer's age on the customer's willingness to buy, and increase the customer's age to 25, the **What-If** tool queries the data mining model and returns the following result:</span></span>

 <span data-ttu-id="85d3b-144">**Purchases Bicycle 的假設分析已找到解決方案。**</span><span class="sxs-lookup"><span data-stu-id="85d3b-144">**What-If Analysis for Purchases Bicycle has found a solution.**</span></span>

 <span data-ttu-id="85d3b-145">**'Purchases Bicycle' = 是**</span><span class="sxs-lookup"><span data-stu-id="85d3b-145">**'Purchases Bicycle' = yes**</span></span>

 <span data-ttu-id="85d3b-146">**信心: 普通**</span><span class="sxs-lookup"><span data-stu-id="85d3b-146">**Confidence: Fair**</span></span>

 <span data-ttu-id="85d3b-147">由於這項結果是根據資料表中的現有資料列，表示對於特定的客戶，如果其他關於客戶的一切都維持不變，客戶的年齡卻增加為 25，客戶便很可能會購買單車。</span><span class="sxs-lookup"><span data-stu-id="85d3b-147">Because this result is based on an existing row in the data table, it means that, for a particular customer, if all else about the customer stayed the same but the customer's age was increased to 25, the customer would likely buy a bicycle.</span></span>

 <span data-ttu-id="85d3b-148">將預測輸出到原始資料表，可能會讓判斷預測是否有用更為容易。</span><span class="sxs-lookup"><span data-stu-id="85d3b-148">Outputting the predictions to the original data table might make it easier to determine whether the predictions are useful.</span></span>

## <a name="related-tools"></a><span data-ttu-id="85d3b-149">相關工具</span><span class="sxs-lookup"><span data-stu-id="85d3b-149">Related Tools</span></span>
 <span data-ttu-id="85d3b-150">適用於 Excel 的資料採礦用戶端，是提供更為進階資料採礦功能的獨立增益集，其中包含的精靈可建立預測行為的資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="85d3b-150">The Data Mining Client for Excel, which is a separate add-in that provides more advanced data mining functionality, includes wizards for creating data mining models that predict behavior.</span></span> <span data-ttu-id="85d3b-151">如需詳細資訊，請參閱[建立資料採礦模型](creating-a-data-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="85d3b-151">For more information, see [Creating a Data Mining Model](creating-a-data-mining-model.md).</span></span>

 <span data-ttu-id="85d3b-152">如需有關「**假設**」狀況工具使用之演算法的詳細資訊，請參閱 SQL Server 線上叢書中的「Microsoft 羅吉斯回歸演算法」主題。</span><span class="sxs-lookup"><span data-stu-id="85d3b-152">For more information about the algorithm used by the **What-If** scenario tool, see the topic "Microsoft Logistic Regression Algorithm" in SQL Server Books Online.</span></span>

## <a name="see-also"></a><span data-ttu-id="85d3b-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85d3b-153">See Also</span></span>
 [<span data-ttu-id="85d3b-154">適用於 Excel 的資料表分析工具</span><span class="sxs-lookup"><span data-stu-id="85d3b-154">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)


