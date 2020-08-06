---
title: " (適用于 Excel) 的資料表分析工具的目標搜尋案例 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- scenario analysis
- goal seek scenario
ms.assetid: efe50306-cf7c-46b3-9cc4-e7f0b6968b0c
author: minewiskan
ms.author: owend
ms.openlocfilehash: b3b4df4f78a2d3652b1dac3c566e66507b523ea5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594262"
---
# <a name="goal-seek-scenario-table-analysis-tools-for-excel"></a><span data-ttu-id="44d01-102">搜尋目標狀況 (適用於 Excel 的資料表分析工具)</span><span class="sxs-lookup"><span data-stu-id="44d01-102">Goal Seek Scenario (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="44d01-103">![資料表分析工具中的搜尋目標按鈕](media/tat-goalseek.gif "資料表分析工具中的搜尋目標按鈕")</span><span class="sxs-lookup"><span data-stu-id="44d01-103">![Goal Seek button in Table Analysis tools](media/tat-goalseek.gif "Goal Seek button in Table Analysis tools")</span></span>  
  
 <span data-ttu-id="44d01-104">「**搜尋目標**」案例工具是[What If](what-if-scenario-table-analysis-tools-for-excel.md)案例工具的補充。</span><span class="sxs-lookup"><span data-stu-id="44d01-104">The **Goal Seek** scenario tool is complementary to the [What If](what-if-scenario-table-analysis-tools-for-excel.md) scenario tool.</span></span> <span data-ttu-id="44d01-105">[**假設**] 工具會告訴您進行變更的影響，而 [**搜尋目標**] 工具會告訴您必須變更以達到所需結果的基礎因素。</span><span class="sxs-lookup"><span data-stu-id="44d01-105">The **What-If** tool tells you the impact of making a change, whereas the **Goal Seek** tool tells you the underlying factors that must change to achieve a desired result.</span></span>  
  
 <span data-ttu-id="44d01-106">例如，假設您的目標是要提高客戶滿意度。</span><span class="sxs-lookup"><span data-stu-id="44d01-106">For example, let's say your goal is to increase customer satisfaction.</span></span> <span data-ttu-id="44d01-107">您可以使用 [**目標搜尋**分析] 來判斷哪些因素最可能會提高客戶滿意度，並決定這些變更是否符合成本效益。</span><span class="sxs-lookup"><span data-stu-id="44d01-107">You can use **Goal Seek** analysis to determine which factors would be most likely to increase customer satisfaction, and decide whether those changes are cost-effective.</span></span>  
  
 <span data-ttu-id="44d01-108">當此工具完成分析時，它會在來源資料表中建立兩個新的資料行。</span><span class="sxs-lookup"><span data-stu-id="44d01-108">When the tool finishes its analysis, it creates two new columns in the source data table.</span></span> <span data-ttu-id="44d01-109">這些資料行顯示可以達成目標結果的*可能性*，以及建議的變更（如果有的話）。</span><span class="sxs-lookup"><span data-stu-id="44d01-109">These columns show the *likelihood* that the targeted outcome can be achieved, and the recommended change, if any.</span></span>  
  
 <span data-ttu-id="44d01-110">此工具可以分析一組資料，然後針對整組進行預測，或者您可以建立分析，然後一次測試一個狀況。</span><span class="sxs-lookup"><span data-stu-id="44d01-110">The tool can analyze a set of data and make predictions for the entire set, or you can create the analysis and then test scenarios one at a time.</span></span>  
  
## <a name="using-the-goal-seek-scenario-tool"></a><span data-ttu-id="44d01-111">使用搜尋目標狀況工具</span><span class="sxs-lookup"><span data-stu-id="44d01-111">Using the Goal Seek Scenario Tool</span></span>  
  
1.  <span data-ttu-id="44d01-112">開啟 Excel 資料表。</span><span class="sxs-lookup"><span data-stu-id="44d01-112">Open an Excel table.</span></span>  
  
2.  <span data-ttu-id="44d01-113">按一下 [**案例**]，然後選取 [**搜尋目標**]。</span><span class="sxs-lookup"><span data-stu-id="44d01-113">Click **Scenarios**, and select **Goal Seek**.</span></span>  
  
3.  <span data-ttu-id="44d01-114">在 [**案例分析：搜尋目標**] 對話方塊中，從清單中選取包含目標值的資料行。</span><span class="sxs-lookup"><span data-stu-id="44d01-114">In the **Scenario Analysis: Goal Seek** dialog box, select the column that contains the target value from the list.</span></span>  
  
4.  <span data-ttu-id="44d01-115">指定您想要達到的值。</span><span class="sxs-lookup"><span data-stu-id="44d01-115">Specify the value that you want to achieve.</span></span>  
  
     <span data-ttu-id="44d01-116">如果資料行目標包含連續的數值，您也可以指定想要增加或減少的值部分。</span><span class="sxs-lookup"><span data-stu-id="44d01-116">If the column goal contains continuous numeric values, you can also specify a desired increase or decrease in the value.</span></span> <span data-ttu-id="44d01-117">例如，您可以選擇 [**銷售**] 做為資料行，並將目標指定為增加120%。</span><span class="sxs-lookup"><span data-stu-id="44d01-117">For example, you might choose **Sales** as the column and specify that the target is an increase of 120%.</span></span>  
  
     <span data-ttu-id="44d01-118">或者，您可以輸入下限和上限，將目標指定為值的範圍。</span><span class="sxs-lookup"><span data-stu-id="44d01-118">Or, you can specify the goal as a range of values, by typing a lower and upper limit.</span></span>  
  
5.  <span data-ttu-id="44d01-119">指定包含您將變更之值的資料行。</span><span class="sxs-lookup"><span data-stu-id="44d01-119">Specify the column that contains the values you will change.</span></span> <span data-ttu-id="44d01-120">換句話說，挑選要操作的資料行來產生所需的結果。</span><span class="sxs-lookup"><span data-stu-id="44d01-120">In other words, pick the column that will be manipulated to produce the desired result.</span></span>  
  
6.  <span data-ttu-id="44d01-121">（選擇性）按一下 **[選擇要用於分析的資料行**]，然後選取包含有用資訊的資料行。</span><span class="sxs-lookup"><span data-stu-id="44d01-121">Optionally, click **Choose columns to be used for analysis**, and select columns that contain useful information.</span></span> <span data-ttu-id="44d01-122">取消選取對於分析沒有用處的資料行。</span><span class="sxs-lookup"><span data-stu-id="44d01-122">Deselect columns that will not contribute to the analysis.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="44d01-123">請不要取消選取您將用於目標或變更的資料行。</span><span class="sxs-lookup"><span data-stu-id="44d01-123">Do not deselect columns that you will use for either the goal or the change.</span></span> <span data-ttu-id="44d01-124">這些資料行是必要的。</span><span class="sxs-lookup"><span data-stu-id="44d01-124">These columns are required.</span></span>  
  
7.  <span data-ttu-id="44d01-125">指定您要針對整份資料表還是只有選取的資料列進行預測。</span><span class="sxs-lookup"><span data-stu-id="44d01-125">Specify whether you want to make predictions for the entire table, or for only the selected row.</span></span>  
  
8.  <span data-ttu-id="44d01-126">如果您選取 [**整份資料表**] 選項，此工具就會將預測加入至來源資料表中兩個新的資料行。</span><span class="sxs-lookup"><span data-stu-id="44d01-126">If you selected the **Entire table** option, the tool adds the predictions to the source table in two new columns.</span></span>  
  
9. <span data-ttu-id="44d01-127">如果您已選取**此資料列上**的選項，則分析的結果會輸出到對話方塊進行審核。</span><span class="sxs-lookup"><span data-stu-id="44d01-127">If you selected the option **On this row**, the results of analysis are output to the dialog box for review.</span></span> <span data-ttu-id="44d01-128">此對話方塊會維持開啟的狀態，讓您可以繼續輸入不同的值和目標。</span><span class="sxs-lookup"><span data-stu-id="44d01-128">The dialog box stays open so that you can continue trying out different values and goals.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="44d01-129">需求</span><span class="sxs-lookup"><span data-stu-id="44d01-129">Requirements</span></span>  
 <span data-ttu-id="44d01-130">此工具會使用可處理數值或離散值的 Microsoft 羅吉斯迴歸演算法。</span><span class="sxs-lookup"><span data-stu-id="44d01-130">This tool uses the Microsoft Logistic Regression algorithm, which can process either numeric or discrete values.</span></span>  
  
 <span data-ttu-id="44d01-131">您可以執行預測多次，並在之後選取不同的資料行，但是必須個別計算每一個目標和變更的組合。</span><span class="sxs-lookup"><span data-stu-id="44d01-131">You can run the prediction multiple times, and select different columns later, but each combination of a goal and a change must be calculated separately.</span></span>  
  
 <span data-ttu-id="44d01-132">如果您選取包含有用資訊的資料行進行分析，可以達成較理想的結果。</span><span class="sxs-lookup"><span data-stu-id="44d01-132">You can achieve better results if you select columns for analysis that contain useful information.</span></span> <span data-ttu-id="44d01-133">但是，如果您包含太少的資料行，則可能很難取得結果。</span><span class="sxs-lookup"><span data-stu-id="44d01-133">However, if you include too few columns, it might be difficult to obtain a result.</span></span>  
  
 <span data-ttu-id="44d01-134">當您一次建立一個預測時，請務必選取尚未包含所需結果的資料列，否則會出現錯誤。</span><span class="sxs-lookup"><span data-stu-id="44d01-134">When you create predictions one at a time, be sure to select a row that does not already contain the desired result, or you may get an error.</span></span> <span data-ttu-id="44d01-135">換句話說，如果搜尋目標的目的在於判斷鼓勵購買腳踏車的因數，您應該只包含沒有購買腳踏車的客戶。</span><span class="sxs-lookup"><span data-stu-id="44d01-135">In other words, if the purpose of goal seeking is to determine factors that encourage bike purchases, you should only include customers who did not purchase a bike.</span></span>  
  
## <a name="understanding-the-results-of-goal-seek-analysis"></a><span data-ttu-id="44d01-136">了解搜尋目標分析的結果</span><span class="sxs-lookup"><span data-stu-id="44d01-136">Understanding the Results of Goal Seek Analysis</span></span>  
 <span data-ttu-id="44d01-137">當您建立搜尋目標狀況時，此工具會執行三個動作：</span><span class="sxs-lookup"><span data-stu-id="44d01-137">When you create a goal seeking scenario, the tool does three things:</span></span>  
  
-   <span data-ttu-id="44d01-138">建立資料採礦結構來儲存與資料表中的資料有關的關鍵事實。</span><span class="sxs-lookup"><span data-stu-id="44d01-138">Creates a data mining structure that stores key facts about the data in your table.</span></span>  
  
-   <span data-ttu-id="44d01-139">根據資料建立羅吉斯迴歸採礦模型。</span><span class="sxs-lookup"><span data-stu-id="44d01-139">Creates a logistic regression mining model based on the data.</span></span>  
  
-   <span data-ttu-id="44d01-140">針對您所指定的每個值建立預測。</span><span class="sxs-lookup"><span data-stu-id="44d01-140">Creates a prediction for each value that you specify.</span></span>  
  
 <span data-ttu-id="44d01-141">如果您一次測試一個搜尋目標狀況，則可以用互動方式檢視其結果。</span><span class="sxs-lookup"><span data-stu-id="44d01-141">If you test goal-seeking scenarios one at a time, you can view the results interactively.</span></span> <span data-ttu-id="44d01-142">這與建立*單一預測查詢*相同。</span><span class="sxs-lookup"><span data-stu-id="44d01-142">This is the same as creating a *singleton prediction query*.</span></span>  
  
 <span data-ttu-id="44d01-143">此工具會在對話方塊的**結果**窗格中報告，不論是否成功尋找達成所需目標的案例。</span><span class="sxs-lookup"><span data-stu-id="44d01-143">The tool reports in the **Results** pane of the dialog box whether it was successful in finding a scenario that achieves the desired goal.</span></span> <span data-ttu-id="44d01-144">如果找到成功的方案，此工具也會產生一項建議，告訴您所需的變更。</span><span class="sxs-lookup"><span data-stu-id="44d01-144">If a successful solution was found, the tool also generates a recommendation that tells you the required change.</span></span> <span data-ttu-id="44d01-145">例如，[**搜尋目標**] 工具可能會告訴您，通勤距離應小於5英里。</span><span class="sxs-lookup"><span data-stu-id="44d01-145">For example, the **Goal Seek** tool might tell you that the commuting distance should be less than 5 miles.</span></span>  
  
 <span data-ttu-id="44d01-146">範例結果︰</span><span class="sxs-lookup"><span data-stu-id="44d01-146">Example results:</span></span>  
  
 <span data-ttu-id="44d01-147">**針對「有興趣購買」搜尋目標已找到方案。**</span><span class="sxs-lookup"><span data-stu-id="44d01-147">**Goal Seeking for Interest in Buying has found a solution.**</span></span>  
  
 <span data-ttu-id="44d01-148">**將「通勤距離」變更為「2-5 英哩」得到最符合的項目。**</span><span class="sxs-lookup"><span data-stu-id="44d01-148">**Closest match obtained by changing 'Commute distance' to '2-5 miles'.**</span></span>  
  
 <span data-ttu-id="44d01-149">由於這項結果是以資料表中的現有資料列為基礎，這表示對於特定客戶而言，如果該客戶的所有其他條件維持相同，但是此客戶的通勤距離減少到 2-5 英哩，則此客戶比較可能會購買腳踏車。</span><span class="sxs-lookup"><span data-stu-id="44d01-149">Because this result is based on an existing row in the data table, it means that, for a particular customer, if all else about the customer stayed the same but the customer's commute was reduced to 2-5 miles, the customer would be somewhat more likely buy a bicycle.</span></span>  
  
 <span data-ttu-id="44d01-150">如果您藉由指定**整個資料表**來建立 Excel 資料表中所有資料列的目標搜尋預測，thetool 會在原始資料表中建立兩個新的資料行。</span><span class="sxs-lookup"><span data-stu-id="44d01-150">If you create goal-seeking predictions for all the rows in the Excel table by specifying **Entire table**, thetool creates two new columns in the original data table.</span></span> <span data-ttu-id="44d01-151">加入到資料表的第一個資料行會包含綠色圓形中的核取標記 (表示可以達成目標)，或是包含紅色圓形中的 X 記號 (表示無法進行會達成目標的任何變更)。</span><span class="sxs-lookup"><span data-stu-id="44d01-151">The first column that is added to the table contains either a check mark in a green circle, to indicate that the goal can be met, or an X mark in a red circle, to indicate that no changes can be made that will enable the goal.</span></span>  
  
 <span data-ttu-id="44d01-152">第二個資料行會包含建議的變更。</span><span class="sxs-lookup"><span data-stu-id="44d01-152">The second column contains the recommended change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="44d01-153">此建議的信心層級和它的成功與否是由演算法所預先決定，且無法變更。</span><span class="sxs-lookup"><span data-stu-id="44d01-153">The confidence level for the recommendation and its success are predetermined by the algorithm and cannot be changed.</span></span>  
  
## <a name="related-tools"></a><span data-ttu-id="44d01-154">相關工具</span><span class="sxs-lookup"><span data-stu-id="44d01-154">Related Tools</span></span>  
 <span data-ttu-id="44d01-155">適用於 Excel 的資料採礦用戶端，是提供更為進階資料採礦功能的獨立增益集，其中包含的精靈可建立預測行為的資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="44d01-155">The Data Mining Client for Excel, which is a separate add-in that provides more advanced data mining functionality, includes wizards for creating data mining models that predict behavior.</span></span> <span data-ttu-id="44d01-156">如需詳細資訊，請參閱[建立資料採礦模型](creating-a-data-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="44d01-156">For more information, see [Creating a Data Mining Model](creating-a-data-mining-model.md).</span></span>  
  
 <span data-ttu-id="44d01-157">如需「**搜尋目標**」案例工具所使用之演算法的詳細資訊，請參閱《線上叢書》中的「Microsoft 羅吉斯回歸演算法」主題 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="44d01-157">For more information about the algorithm used by the **Goal Seek** scenario tool, see the topic "Microsoft Logistic Regression Algorithm" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44d01-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="44d01-158">See Also</span></span>  
 [<span data-ttu-id="44d01-159">適用於 Excel 的資料表分析工具</span><span class="sxs-lookup"><span data-stu-id="44d01-159">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
  
