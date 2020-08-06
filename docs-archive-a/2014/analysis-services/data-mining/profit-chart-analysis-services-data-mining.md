---
title: 收益圖 (Analysis Services-資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy, charting
- revenue, estimating
- benefits, estimating
- charts [Analysis Services]
- profit charts [Analysis Services]
ms.assetid: 760ee051-6fd8-48e3-8d2e-82db3ab45e45
author: minewiskan
ms.author: owend
ms.openlocfilehash: a38a1d5062f53de4be9129c2305d8d3c84593f9e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703429"
---
# <a name="profit-chart-analysis-services---data-mining"></a><span data-ttu-id="bbf85-102">收益圖 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="bbf85-102">Profit Chart (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="bbf85-103">收益圖會顯示與使用採礦模型有關聯的預估獲利率。</span><span class="sxs-lookup"><span data-stu-id="bbf85-103">A profit chart displays the estimated profitability associated with using a mining model.</span></span> <span data-ttu-id="bbf85-104">例如，假設您的模型會預測公司應該在商務案例中聯繫的客戶。</span><span class="sxs-lookup"><span data-stu-id="bbf85-104">For example, let's assume your model predicts which customers a company should contact in a business scenario.</span></span> <span data-ttu-id="bbf85-105">在此情況下，您的收益圖就要加入與執行目標郵寄促銷活動的成本有關的資訊。</span><span class="sxs-lookup"><span data-stu-id="bbf85-105">In that case, you would add to the profit chart information about the cost of conducting the targeted mailing campaign.</span></span> <span data-ttu-id="bbf85-106">然後，您便能在完成的圖表中看到正確鎖定目標客戶相較於隨機連絡客戶的預估收益。</span><span class="sxs-lookup"><span data-stu-id="bbf85-106">Then, in the completed chart, you can see the estimated profit if customers are correctly targeted, as compared to randomly contacting customers.</span></span>  
  
## <a name="build-a-profit-chart"></a><span data-ttu-id="bbf85-107">建置收益圖</span><span class="sxs-lookup"><span data-stu-id="bbf85-107">Build a Profit Chart</span></span>  
 <span data-ttu-id="bbf85-108">收益圖類似於增益圖。</span><span class="sxs-lookup"><span data-stu-id="bbf85-108">A profit chart is similar to a lift chart.</span></span> <span data-ttu-id="bbf85-109">您首先要建立增益圖，然後再加入成本和收益資訊。</span><span class="sxs-lookup"><span data-stu-id="bbf85-109">You start by creating a lift chart, and then add in the cost and profit information.</span></span>  
  
 <span data-ttu-id="bbf85-110">若要建置收益圖，您必須已有現存的模型。</span><span class="sxs-lookup"><span data-stu-id="bbf85-110">To build a profit chart, you must have an existing model.</span></span>  
  
 <span data-ttu-id="bbf85-111">本範例使用的是目標郵寄決策樹模型。</span><span class="sxs-lookup"><span data-stu-id="bbf85-111">For this example, we used the Targeted Mailing decision tree model.</span></span> <span data-ttu-id="bbf85-112">此模型識別了可能購買自行車的客戶。</span><span class="sxs-lookup"><span data-stu-id="bbf85-112">The model identifies customers who are likely to buy a bike.</span></span> <span data-ttu-id="bbf85-113">您可以套用 [收益圖]\*\*\*\* 來判斷能夠達到最高收益的目標客戶數。</span><span class="sxs-lookup"><span data-stu-id="bbf85-113">You can apply the **Profit Chart** to determine how many of your customers to target to maximize your profit.</span></span>  
  
 <span data-ttu-id="bbf85-114">如果您沒有範例模型，可以使用[基本資料採礦教學](../../tutorials/basic-data-mining-tutorial.md)課程來建立。</span><span class="sxs-lookup"><span data-stu-id="bbf85-114">If you don't have the sample model, you can create it using the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span>  
  
1.  <span data-ttu-id="bbf85-115">開啟採礦精確度圖表產生器。</span><span class="sxs-lookup"><span data-stu-id="bbf85-115">Open the mining accuracy chart builder.</span></span>  
  
    -   <span data-ttu-id="bbf85-116">在 SQL Server Management Studio 中，以滑鼠右鍵按一下模型，然後選取 [檢視增益圖]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbf85-116">In SQL Server Management Studio, right-click the model, and select **View Lift Chart**.</span></span>  
  
    -   <span data-ttu-id="bbf85-117">在 SQL Server Data Tools 中，開啟您已在其中建立模型的專案，然後按一下 [採礦精確度圖表]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bbf85-117">In SQL Server Data Tools, open the project in which you created the model, and click the **Mining Accuracy Chart** tab.</span></span>  
  
2.  <span data-ttu-id="bbf85-118">在 [輸入選擇]\*\*\*\* 索引標籤上，選取模型並選擇可預測的屬性值。</span><span class="sxs-lookup"><span data-stu-id="bbf85-118">In **the Input Selection** tab, select the model and choose the predictable attribute value.</span></span>  
  
     <span data-ttu-id="bbf85-119">就這個特定案例而言，您只有興趣知道能準確預測此值的獲利率：[Bike Buyer] =1。</span><span class="sxs-lookup"><span data-stu-id="bbf85-119">For this particular scenario, you are interested only in the profitability of accurately predicting one value: [Bike Buyer] =1.</span></span>  
  
     <span data-ttu-id="bbf85-120">不過，您也一樣重視能準確預測 false 值的其他案例。</span><span class="sxs-lookup"><span data-stu-id="bbf85-120">However, there are other scenarios in which you are equally interested in predicting false values correctly.</span></span> <span data-ttu-id="bbf85-121">例如，醫療診斷檢驗誤判的成本可能很高，以致必須將這項因素計入獲利率預測，而誤否定的成本也是如此。</span><span class="sxs-lookup"><span data-stu-id="bbf85-121">For example, the cost of a false positive on a medical diagnostic test can be significant and needs to be factored into the profitability of the prediction, as does the cost of false negatives.</span></span> <span data-ttu-id="bbf85-122">在這類情況下，您就要測量所有結果。</span><span class="sxs-lookup"><span data-stu-id="bbf85-122">In such scenarios, you would measure all outcomes.</span></span>  
  
3.  <span data-ttu-id="bbf85-123">選取要測試的資料集。</span><span class="sxs-lookup"><span data-stu-id="bbf85-123">Select a data set for testing.</span></span> <span data-ttu-id="bbf85-124">針對本範例，請選取測試資料集。</span><span class="sxs-lookup"><span data-stu-id="bbf85-124">For this example, select the testing data set.</span></span>  
  
4.  <span data-ttu-id="bbf85-125">接著，按一下 [增益圖]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bbf85-125">Now click the **Lift Chart** tab.</span></span>  
  
     <span data-ttu-id="bbf85-126">隨即會自動產生增益圖。</span><span class="sxs-lookup"><span data-stu-id="bbf85-126">A lift chart is automatically generated.</span></span>  
  
5.  <span data-ttu-id="bbf85-127">從 [圖表類型]\*\*\*\* 清單中選取 [收益圖]\*\*\*\*，以將其變更為收益圖。</span><span class="sxs-lookup"><span data-stu-id="bbf85-127">To change this to a profit chart, select **Profit Chart** from the **Chart type** list.</span></span>  
  
6.  <span data-ttu-id="bbf85-128">只要您選擇了收益圖作為圖表類型，即會自動開啟 [收益圖設定]\*\*\*\* 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="bbf85-128">As soon as you choose profit chart as the chart type, the **Profit Chart Setting** dialog box automatically opens.</span></span>  
  
     <span data-ttu-id="bbf85-129">此對話方塊可協助您指定與目標郵寄促銷活動相關的成本與效益。</span><span class="sxs-lookup"><span data-stu-id="bbf85-129">This dialog box helps you specify the costs and benefits associated with a targeted mailing campaign.</span></span> <span data-ttu-id="bbf85-130">針對這些範例中所示的圖表，我們使用下列值：</span><span class="sxs-lookup"><span data-stu-id="bbf85-130">For the chart shown in these examples, we used the following values:</span></span>  
  
    |<span data-ttu-id="bbf85-131">設定</span><span class="sxs-lookup"><span data-stu-id="bbf85-131">Setting</span></span>|<span data-ttu-id="bbf85-132">值</span><span class="sxs-lookup"><span data-stu-id="bbf85-132">Value</span></span>|<span data-ttu-id="bbf85-133">註解</span><span class="sxs-lookup"><span data-stu-id="bbf85-133">Comments</span></span>|  
    |-------------|-----------|--------------|  
    |<span data-ttu-id="bbf85-134">**人數**</span><span class="sxs-lookup"><span data-stu-id="bbf85-134">**Population**</span></span>|<span data-ttu-id="bbf85-135">20,000</span><span class="sxs-lookup"><span data-stu-id="bbf85-135">20,000</span></span>|<span data-ttu-id="bbf85-136">設定總目標母體的值</span><span class="sxs-lookup"><span data-stu-id="bbf85-136">Set the value for the total target population</span></span><br /><br /> <span data-ttu-id="bbf85-137">您的資料庫可能包含許多客戶，但是為了省下郵寄支出，您可以選擇只鎖定最有可能回應的 20,000 名目標客戶。</span><span class="sxs-lookup"><span data-stu-id="bbf85-137">Your database might contain many customers, but to save on mailing expenses you might choose to target only the 20,000 customers who are most likely to respond.</span></span> <span data-ttu-id="bbf85-138">藉由執行預測查詢，並依預測模型所輸出的機率排序，即可取得這份清單。</span><span class="sxs-lookup"><span data-stu-id="bbf85-138">You can get this list by running a prediction query and sorting by the probability output by the predictive model.</span></span>|  
    |<span data-ttu-id="bbf85-139">**固定成本**</span><span class="sxs-lookup"><span data-stu-id="bbf85-139">**Fixed cost**</span></span>|<span data-ttu-id="bbf85-140">500</span><span class="sxs-lookup"><span data-stu-id="bbf85-140">500</span></span>|<span data-ttu-id="bbf85-141">輸入為 20,000 人設定目標郵寄促銷活動的單次成本。</span><span class="sxs-lookup"><span data-stu-id="bbf85-141">Enter the one-time cost of setting up a targeted mailing campaign for 20,000 people.</span></span> <span data-ttu-id="bbf85-142">這可能包括印刷品，或是設定電子郵件促銷活動的成本。</span><span class="sxs-lookup"><span data-stu-id="bbf85-142">This might include printing, or the cost of setting up an e-mail campaign.</span></span>|  
    |<span data-ttu-id="bbf85-143">**單位成本**</span><span class="sxs-lookup"><span data-stu-id="bbf85-143">**Individual cost**</span></span>|<span data-ttu-id="bbf85-144">3</span><span class="sxs-lookup"><span data-stu-id="bbf85-144">3</span></span>|<span data-ttu-id="bbf85-145">輸入目標郵寄促銷活動的每單位成本。</span><span class="sxs-lookup"><span data-stu-id="bbf85-145">Enter the per-unit cost for the targeted mailing campaign.</span></span><br /><br /> <span data-ttu-id="bbf85-146">這個金額將會乘以小於或等於 20000 的數字，端視模型預測多少客戶為良好潛在客戶而定。</span><span class="sxs-lookup"><span data-stu-id="bbf85-146">This amount will be multiplied by a number equal to or less than 20000, depending on how many customers the model predicts are good prospects.</span></span>|  
    |<span data-ttu-id="bbf85-147">**每個別營收**</span><span class="sxs-lookup"><span data-stu-id="bbf85-147">**Revenue per individual**</span></span>|<span data-ttu-id="bbf85-148">400</span><span class="sxs-lookup"><span data-stu-id="bbf85-148">400</span></span>|<span data-ttu-id="bbf85-149">輸入代表預期可從成功的結果獲得的收益或收入金額值。</span><span class="sxs-lookup"><span data-stu-id="bbf85-149">Enter a value that represents the amount of profit or income that can be expected from a successful result.</span></span> <span data-ttu-id="bbf85-150">在此情況下，我們會假設郵寄目錄會導致購買配件或自行車平均 $400。</span><span class="sxs-lookup"><span data-stu-id="bbf85-150">In this case, we'll assume that mailing a catalog results in purchase of accessories or bikes averaging $400.</span></span><br /><br /> <span data-ttu-id="bbf85-151">此金額將會用來預估與高機率案例有關的總收益。</span><span class="sxs-lookup"><span data-stu-id="bbf85-151">This amount will be used to project the total profit associated with high probability cases.</span></span>|  
  
7.  <span data-ttu-id="bbf85-152">在您設定妥必要的參數之後，按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="bbf85-152">After you have set the required parameters, click **OK**.</span></span>  
  
8.  <span data-ttu-id="bbf85-153">圖表隨即更新，以顯示收益曲線。</span><span class="sxs-lookup"><span data-stu-id="bbf85-153">The chart updates to show the profit curve.</span></span>  
  
## <a name="understanding-the-profit-chart"></a><span data-ttu-id="bbf85-154">了解收益圖</span><span class="sxs-lookup"><span data-stu-id="bbf85-154">Understanding the Profit Chart</span></span>  
 <span data-ttu-id="bbf85-155">下圖顯示以這些參數為基礎的圖表。</span><span class="sxs-lookup"><span data-stu-id="bbf85-155">The following diagram shows the chart that was based on these parameters.</span></span> <span data-ttu-id="bbf85-156">圖表的 Y 軸代表收益，而 X 軸則代表目標郵寄促銷活動所連絡的客戶百分比。</span><span class="sxs-lookup"><span data-stu-id="bbf85-156">The Y-axis of the chart represents the profit, while the X-axis represents the percentage of the customers who were contacted by the targeted mailing campaign.</span></span>  
  
 <span data-ttu-id="bbf85-157">如下所示，使用收益圖能讓您比較多個模型，只要這些模型都預測相同的離散屬性即可。</span><span class="sxs-lookup"><span data-stu-id="bbf85-157">As shown here, you can use a profit chart to compare multiple models, as long as they all predict the same discrete attribute.</span></span>  
  
 <span data-ttu-id="bbf85-158">![比較三個模型的收益圖](../media/dm14-profitchartupdated.gif "比較三個模型的收益圖")</span><span class="sxs-lookup"><span data-stu-id="bbf85-158">![a profit chart comparing three models](../media/dm14-profitchartupdated.gif "a profit chart comparing three models")</span></span>  
  
 <span data-ttu-id="bbf85-159">請注意圖表中的灰色垂直線。</span><span class="sxs-lookup"><span data-stu-id="bbf85-159">Notice the gray vertical line in the chart.</span></span> <span data-ttu-id="bbf85-160">當您按一下並拖曳這條線時，工具提示便會顯示曲線底下於各點位置所包括的目標母體的百分比。</span><span class="sxs-lookup"><span data-stu-id="bbf85-160">As you click and drag the line, the ToolTip display the percentage of the target population that is included under the curve at that point.</span></span>  
  
 <span data-ttu-id="bbf85-161">隨著您拖曳這條線，[採礦圖例]\*\*\*\* 也將更新以顯示百分比值、收益分數以及此灰色垂直線上與母體百分比有關的預測機率。</span><span class="sxs-lookup"><span data-stu-id="bbf85-161">The **Mining Legend** is also updated as you drag the line, to display the percentage value, a profit score, and the predict probability that is associated with the population percentage at the vertical gray line.</span></span>  
  
 <span data-ttu-id="bbf85-162">例如，若您使用此模型決定要將促銷文宣寄給哪些人，您可能就會根據預測機率而決定以母體的 25% 為目標。不過，圖表的收益曲線底下介於 40% 到 70% 之間的面積最大，表示就算整體百分比回應偏低，郵寄的人數愈多還是能夠獲得愈高的報酬。</span><span class="sxs-lookup"><span data-stu-id="bbf85-162">For example, if you were using this model to decide who to send your promotional material to, you might decide to target 25% of the population, based on the predict probabilities, However, the area under the profit curve of the chart is greatest between 40 and 70 percent, indicating that by mailing to more people, you can maximize your return, even if a smaller overall percentage responds.</span></span>  
  
## <a name="saving-charts"></a><span data-ttu-id="bbf85-163">儲存圖表</span><span class="sxs-lookup"><span data-stu-id="bbf85-163">Saving Charts</span></span>  
 <span data-ttu-id="bbf85-164">當您建立精確度圖表或收益圖時，在伺服器上並不會建立任何物件。</span><span class="sxs-lookup"><span data-stu-id="bbf85-164">When you create an accuracy chart or profit chart, no objects are created on the server.</span></span> <span data-ttu-id="bbf85-165">但是，此時會對現有的模型執行查詢，再由檢視器轉譯結果。</span><span class="sxs-lookup"><span data-stu-id="bbf85-165">Instead, queries are executed against an existing model and the results are rendered in the viewer.</span></span> <span data-ttu-id="bbf85-166">如果您需要儲存結果，則必須將圖表或結果複製到 Excel 或其他檔案。</span><span class="sxs-lookup"><span data-stu-id="bbf85-166">If you need to save the results, you must copy either the chart or the results to Excel or another file.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="bbf85-167">相關內容</span><span class="sxs-lookup"><span data-stu-id="bbf85-167">Related Content</span></span>  
 <span data-ttu-id="bbf85-168">下列主題包含您可以如何建立及使用精確度圖表的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="bbf85-168">The following topics contain more information about how you can build and use accuracy charts.</span></span>  
  
|<span data-ttu-id="bbf85-169">主題</span><span class="sxs-lookup"><span data-stu-id="bbf85-169">Topics</span></span>|<span data-ttu-id="bbf85-170">連結</span><span class="sxs-lookup"><span data-stu-id="bbf85-170">Links</span></span>|  
|------------|-----------|  
|<span data-ttu-id="bbf85-171">提供如何為此目標郵寄模型建立增益圖的逐步解說。</span><span class="sxs-lookup"><span data-stu-id="bbf85-171">Provides a walkthrough of how to create a lift chart for the Targeted Mailing model.</span></span>|[<span data-ttu-id="bbf85-172">資料採礦基本教學課程</span><span class="sxs-lookup"><span data-stu-id="bbf85-172">Basic Data Mining Tutorial</span></span>](../../tutorials/basic-data-mining-tutorial.md)<br /><br /> [<span data-ttu-id="bbf85-173">使用增益圖測試精確度 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="bbf85-173">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)|  
|<span data-ttu-id="bbf85-174">說明相關的圖表類型。</span><span class="sxs-lookup"><span data-stu-id="bbf85-174">Explains related chart types.</span></span>|[<span data-ttu-id="bbf85-175">增益圖 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="bbf85-175">Lift Chart &#40;Analysis Services - Data Mining&#41;</span></span>](lift-chart-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="bbf85-176">分類矩陣 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="bbf85-176">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](classification-matrix-analysis-services-data-mining.md)<br /><br /> [<span data-ttu-id="bbf85-177">散佈圖 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="bbf85-177">Scatter Plot &#40;Analysis Services - Data Mining&#41;</span></span>](scatter-plot-analysis-services-data-mining.md)|  
|<span data-ttu-id="bbf85-178">描述採礦模型和採礦結構的交叉驗證。</span><span class="sxs-lookup"><span data-stu-id="bbf85-178">Describes cross-validation for mining models and mining structures.</span></span>|[<span data-ttu-id="bbf85-179">交叉驗證 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="bbf85-179">Cross-Validation &#40;Analysis Services - Data Mining&#41;</span></span>](cross-validation-analysis-services-data-mining.md)|  
|<span data-ttu-id="bbf85-180">描述建立增益圖及其他精確度圖表的步驟。</span><span class="sxs-lookup"><span data-stu-id="bbf85-180">Describes steps for creating lift charts and other accuracy charts.</span></span>|[<span data-ttu-id="bbf85-181">測試及驗證工作與操作方法 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="bbf85-181">Testing and Validation Tasks and How-tos &#40;Data Mining&#41;</span></span>](testing-and-validation-tasks-and-how-tos-data-mining.md)|  
  
## <a name="see-also"></a><span data-ttu-id="bbf85-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbf85-182">See Also</span></span>  
 <span data-ttu-id="bbf85-183">[測試和驗證 &#40;資料採礦&#41;](testing-and-validation-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="bbf85-183">[Testing and Validation &#40;Data Mining&#41;](testing-and-validation-data-mining.md) </span></span>  
 [<span data-ttu-id="bbf85-184">使用增益圖測試精確度 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="bbf85-184">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
  
