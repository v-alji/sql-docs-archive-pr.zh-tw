---
title: 收益圖 (SQL Server 資料採礦增益集) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- accuracy chart
- profit chart
- mining models, charting
- mining models, testing
ms.assetid: 5c902543-4da9-4db3-99d5-4ce04c43d7ef
author: minewiskan
ms.author: owend
ms.openlocfilehash: 030e511047b816543c12c81bdab307e599bbc5d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596299"
---
# <a name="profit-chart-sql-server-data-mining-add-ins"></a><span data-ttu-id="5b38f-102">收益圖 (SQL Server 資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="5b38f-102">Profit Chart (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="5b38f-103">![資料採礦用戶端中的收益圖按鈕](media/dmc-profitchart.gif "資料採礦用戶端中的收益圖按鈕")</span><span class="sxs-lookup"><span data-stu-id="5b38f-103">![Profit Chart button in Data Mining ribbon](media/dmc-profitchart.gif "Profit Chart button in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="5b38f-104">在商務案例中，收益圖會顯示當公司使用某採礦模型來決定應連絡的客戶對象時，相關的估計收益增加量。</span><span class="sxs-lookup"><span data-stu-id="5b38f-104">A profit chart displays the estimated profit increase that is associated with using a mining model to determine which customers a company should contact in a business scenario.</span></span> <span data-ttu-id="5b38f-105">圖表的 Y 軸代表收益，而 X 軸則代表母體中公司所連絡的百分比。</span><span class="sxs-lookup"><span data-stu-id="5b38f-105">The Y-axis of the chart represents the profit, while the X-axis represents the percentage of the population that the company contacted.</span></span> <span data-ttu-id="5b38f-106">一般收益圖會顯示收益增加直到某個點為止，過了這個點之後，收益就會隨著連絡的母體百分比增加而減少。</span><span class="sxs-lookup"><span data-stu-id="5b38f-106">A typical profit chart shows an increase in profits up to a point, after which profits decrease as more of the population is contacted.</span></span>  
  
## <a name="configuring-the-profit-chart"></a><span data-ttu-id="5b38f-107">設定收益圖</span><span class="sxs-lookup"><span data-stu-id="5b38f-107">Configuring the Profit Chart</span></span>  
 <span data-ttu-id="5b38f-108">精確度圖表只評估正確或錯誤預測的機率，收益圖則會納入對預測採取行動在現實世界中的結果。</span><span class="sxs-lookup"><span data-stu-id="5b38f-108">Whereas the accuracy chart assesses only the probability that predictions are right or wrong, the profit chart incorporates real-world knowledge about the consequences of taking action on a prediction.</span></span> <span data-ttu-id="5b38f-109">這是透過考量您在執行精靈時所指定之下列因數達成的：</span><span class="sxs-lookup"><span data-stu-id="5b38f-109">This is achieved by taking into account the following factors, which you specify when you run the wizard:</span></span>  
  
-   <span data-ttu-id="5b38f-110">**人數**</span><span class="sxs-lookup"><span data-stu-id="5b38f-110">**Population**</span></span>  
  
     <span data-ttu-id="5b38f-111">資料集裡用來建立增益圖的案例數目。</span><span class="sxs-lookup"><span data-stu-id="5b38f-111">The number of cases in the dataset that is being used to create the lift chart.</span></span> <span data-ttu-id="5b38f-112">例如，潛在客戶的數目。</span><span class="sxs-lookup"><span data-stu-id="5b38f-112">For example, the number of potential customers.</span></span>  
  
-   <span data-ttu-id="5b38f-113">**固定成本**</span><span class="sxs-lookup"><span data-stu-id="5b38f-113">**Fixed Cost**</span></span>  
  
     <span data-ttu-id="5b38f-114">與商業問題相關聯的固定成本。</span><span class="sxs-lookup"><span data-stu-id="5b38f-114">The fixed cost that is associated with the business problem.</span></span> <span data-ttu-id="5b38f-115">如果是鎖定目標的郵寄方案，則成本不會隨變數而定，例如電話拜訪次數或郵寄的廣告信件數量。</span><span class="sxs-lookup"><span data-stu-id="5b38f-115">If this were for a targeted mailing solution, the cost would not depend on variables such as the number of telephone calls made or the number of promotional mailings sent.</span></span>  
  
-   <span data-ttu-id="5b38f-116">**個別成本**</span><span class="sxs-lookup"><span data-stu-id="5b38f-116">**Individual Cost**</span></span>  
  
     <span data-ttu-id="5b38f-117">除了固定成本外，與每一個客戶連絡的相關聯成本。</span><span class="sxs-lookup"><span data-stu-id="5b38f-117">Costs that are in addition to the fixed cost, that can be associated with each customer contact.</span></span> <span data-ttu-id="5b38f-118">例如，廣告信件或電話費用。</span><span class="sxs-lookup"><span data-stu-id="5b38f-118">For example, promotional mailings or telephone calls.</span></span>  
  
-   <span data-ttu-id="5b38f-119">**每個人的收入**</span><span class="sxs-lookup"><span data-stu-id="5b38f-119">**Revenue Per Individual**</span></span>  
  
     <span data-ttu-id="5b38f-120">與每一次成功銷售相關聯的營收金額。</span><span class="sxs-lookup"><span data-stu-id="5b38f-120">The amount of revenue that is associated with each successful sale.</span></span>  
  
## <a name="using-the-profit-chart-wizard"></a><span data-ttu-id="5b38f-121">使用收益圖精靈</span><span class="sxs-lookup"><span data-stu-id="5b38f-121">Using the Profit Chart Wizard</span></span>  
 <span data-ttu-id="5b38f-122">若要建立收益圖，您必須參考現有的資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="5b38f-122">To create a profit chart, you must reference an existing data mining model.</span></span> <span data-ttu-id="5b38f-123">您可以按一下 [**管理模型**] 或 **[流覽]** 以查看所使用之演算法的詳細資料，以及在此模型中的資料行，以流覽模型來尋找符合您資料的模型。</span><span class="sxs-lookup"><span data-stu-id="5b38f-123">You can browse models to find a model that matches your data by clicking **Manage Models** or **Browse** to see details about the algorithm that was used and the columns in the mining model.</span></span>  
  
 <span data-ttu-id="5b38f-124">如需詳細資訊，請參閱[在 Excel 中流覽模型 &#40;SQL Server 資料採礦增益集&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)和[管理模型 &#40;SQL Server 資料採礦增益集&#41;](manage-models-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="5b38f-124">For more information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md) and [Manage Models &#40;SQL Server Data Mining Add-ins&#41;](manage-models-sql-server-data-mining-add-ins.md).</span></span>  
  
#### <a name="to-create-a-profit-chart"></a><span data-ttu-id="5b38f-125">建立收益圖</span><span class="sxs-lookup"><span data-stu-id="5b38f-125">To create a profit chart</span></span>  
  
1.  <span data-ttu-id="5b38f-126">選取現有的模型。</span><span class="sxs-lookup"><span data-stu-id="5b38f-126">Select an existing model.</span></span>  
  
2.  <span data-ttu-id="5b38f-127">指定要預測的資料行和目標值 (如果適用)。</span><span class="sxs-lookup"><span data-stu-id="5b38f-127">Specify the column that you want to predict, and a target value, if appropriate.</span></span>  
  
3.  <span data-ttu-id="5b38f-128">選取來源資料，這是您將會傳遞通過模型以便建立預測的資料。</span><span class="sxs-lookup"><span data-stu-id="5b38f-128">Select the source data, which means the data you will pass through the model in order to create a prediction.</span></span> <span data-ttu-id="5b38f-129">來源資料不應與用來建立模型的資料相同。</span><span class="sxs-lookup"><span data-stu-id="5b38f-129">This should not be the same data that you used to create the model.</span></span>  
  
4.  <span data-ttu-id="5b38f-130">將新 (來源) 日期中的資料行對應到在資料採礦模型中使用的資料行。</span><span class="sxs-lookup"><span data-stu-id="5b38f-130">Map the columns in the new (source) date to the columns used in the data mining model.</span></span> <span data-ttu-id="5b38f-131">如果資料行名稱相似，精靈便會自動加以對應。</span><span class="sxs-lookup"><span data-stu-id="5b38f-131">If the column names are similar, the wizard will automatically map them.</span></span>  
  
5.  <span data-ttu-id="5b38f-132">輸入精靈需要的成本資訊：固定成本、單位成本、母體及預期營收。</span><span class="sxs-lookup"><span data-stu-id="5b38f-132">Enter the cost information required by the wizard: the fixed cost, individual cost, the population, and the revenue expected.</span></span>  
  
6.  <span data-ttu-id="5b38f-133">（選擇性）您可以輸入一連串的成本， (按一下 [流覽\*\* ( ... ) \*\* ] 按鈕) 。</span><span class="sxs-lookup"><span data-stu-id="5b38f-133">Optionally, you can enter a graduated series of costs (click the browse **(...)** button).</span></span> <span data-ttu-id="5b38f-134">例如，郵寄成本可能會在寄送的項目數目增加時變得更便宜，所以您可以根據項目數目輸入不同成本，然後精靈會自動調整每個取樣大小的成本。</span><span class="sxs-lookup"><span data-stu-id="5b38f-134">For example, a mailing might become cheaper as you increase the number of items that are sent, so you can enter a different cost depending on the number of items, and the wizard will automatically adjust the costs for each sample size.</span></span>  
  
7.  <span data-ttu-id="5b38f-135">精靈隨即建立包含模型之成本-效益分析的圖表。</span><span class="sxs-lookup"><span data-stu-id="5b38f-135">The wizard creates a chart that includes the cost-benefit analysis for the model.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="5b38f-136">需求</span><span class="sxs-lookup"><span data-stu-id="5b38f-136">Requirements</span></span>  
 <span data-ttu-id="5b38f-137">如果您要預測離散數值，必須選取要預測的精確目標值。</span><span class="sxs-lookup"><span data-stu-id="5b38f-137">If you are predicting a discrete numeric value, you must select the exact target value to predict.</span></span>  
  
## <a name="understanding-the-profit-chart"></a><span data-ttu-id="5b38f-138">了解收益圖</span><span class="sxs-lookup"><span data-stu-id="5b38f-138">Understanding the Profit Chart</span></span>  
 <span data-ttu-id="5b38f-139">收益圖包含一條灰色垂直線，您可以按一下圖表中的位置來移動此線條。</span><span class="sxs-lookup"><span data-stu-id="5b38f-139">The profit chart contains a gray vertical line, which you can move by clicking a location in the chart.</span></span> <span data-ttu-id="5b38f-140">[**挖掘圖例**] 會顯示分數、人口校正，以及與圖表上的灰階位置相關聯的預測機率。</span><span class="sxs-lookup"><span data-stu-id="5b38f-140">The **Mining Legend** displays a score, the population correct, and the predict probability that are associated with the location of the gray line on the chart.</span></span> <span data-ttu-id="5b38f-141">如果您在圖表中使用灰線選取最大收益點，則可以使用預測機率值來判斷連絡客戶的機率臨界值。</span><span class="sxs-lookup"><span data-stu-id="5b38f-141">If you select the maximum point of profits in the chart by using the gray line, you can use the predict probability value to determine a probability threshold for contacting a customer.</span></span>  
  
 <span data-ttu-id="5b38f-142">例如，假設收益曲線的峰值是母體的 55%，而相關聯的預測機率是 20%，這表示您應該只連絡預測回應機率在 20% 以上的客戶，才能達到最大收益。</span><span class="sxs-lookup"><span data-stu-id="5b38f-142">For example, if the peak of the profit curve is at 55 percent of the population and the associated predict probability is 20 percent, this indicates that to achieve maximum profits you should only contact those customers whose response is predicted with a 20 percent or greater probability.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b38f-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b38f-143">See Also</span></span>  
 [<span data-ttu-id="5b38f-144">驗證模型及使用模型進行預測 &#40;適用于 Excel 的資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="5b38f-144">Validating Models and Using Models for Prediction &#40;Data Mining Add-ins for Excel&#41;</span></span>](validating-models-and-using-models-for-prediction-data-mining-add-ins-for-excel.md)  
  
  
