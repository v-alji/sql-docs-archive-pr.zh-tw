---
title: 評估 Wizard (適用于 Excel) 的資料採礦增益集 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data modeling [data mining]
- estimation
ms.assetid: 7f2b1d5f-c9b3-4939-b35a-34ae099af15f
author: minewiskan
ms.author: owend
ms.openlocfilehash: ace9fa3a62690061677312d4f7dbb6b8a1d0ea5a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703394"
---
# <a name="estimate-wizard-data-mining-add-ins-for-excel"></a><span data-ttu-id="b114a-102">估計精靈 (適用於 Excel 的資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="b114a-102">Estimate Wizard (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="b114a-103">![資料採礦功能區中的估計精靈](media/dmc-estimate.gif "資料採礦功能區中的估計精靈")</span><span class="sxs-lookup"><span data-stu-id="b114a-103">![Estimate wizard in Data Mining ribbon](media/dmc-estimate.gif "Estimate wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="b114a-104">**估計**的 wizard 可協助您建立估計模型。</span><span class="sxs-lookup"><span data-stu-id="b114a-104">The **Estimate** wizard helps you create an estimation model.</span></span> <span data-ttu-id="b114a-105">估計模型會從資料擷取模式，並使用此模式來預測會影響結果的因數。</span><span class="sxs-lookup"><span data-stu-id="b114a-105">An estimation model extracts patterns from data and uses the patterns to predict the factors that affect outcomes.</span></span>  
  
 <span data-ttu-id="b114a-106">估計用於預測數值結果。</span><span class="sxs-lookup"><span data-stu-id="b114a-106">Estimation is used for predicting numeric outcomes.</span></span> <span data-ttu-id="b114a-107">例如，如果目標資料行包含以百分比表示的學校學生畢業率，您可以分析可能會增加或減少畢業率的因數，例如每間學校的學生人數、師生比和教師人數等。</span><span class="sxs-lookup"><span data-stu-id="b114a-107">For example, if your target column contains graduation rates for schools, with graduation rates expressed as percentages, you could analyze factors that potentially increase or decrease graduation rates, such as the number of students per school, the student-teacher ratio, and the number of teachers.</span></span>  
  
## <a name="using-the-estimate-data-wizard"></a><span data-ttu-id="b114a-108">使用估計資料精靈</span><span class="sxs-lookup"><span data-stu-id="b114a-108">Using the Estimate Data Wizard</span></span>  
  
1.  <span data-ttu-id="b114a-109">在 [**資料採礦**] 功能區上，按一下 [**估計**]。</span><span class="sxs-lookup"><span data-stu-id="b114a-109">On the **Data Mining** ribbon, click **Estimate**.</span></span>  
  
2.  <span data-ttu-id="b114a-110">在 [**選取來源資料**] 對話方塊中，選取要使用的來源資料。</span><span class="sxs-lookup"><span data-stu-id="b114a-110">In the **Select Source Data** dialog box, select the source data to use.</span></span> <span data-ttu-id="b114a-111">您可以使用 Excel**資料表**、Excel**資料範圍**或**外部資料源**中的資料。</span><span class="sxs-lookup"><span data-stu-id="b114a-111">You can use data in an Excel **Table**, an Excel **Data Range**, or from an **External data source**.</span></span>  
  
     <span data-ttu-id="b114a-112">如果使用外部資料來源，您可以建立自訂檢視或查詢，然後將其儲存為 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料來源。</span><span class="sxs-lookup"><span data-stu-id="b114a-112">If you use an external data source, you can create custom views or queries and save them as an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] data source.</span></span>  
  
3.  <span data-ttu-id="b114a-113">在 [**估計**] 對話方塊中，選取**要分析**的資料行。</span><span class="sxs-lookup"><span data-stu-id="b114a-113">In the **Estimation** dialog box, select the **Column to analyze**.</span></span>  
  
     <span data-ttu-id="b114a-114">目標資料行必須包含連續數值資料。</span><span class="sxs-lookup"><span data-stu-id="b114a-114">The target column must contain continuous numeric data.</span></span>  
  
4.  <span data-ttu-id="b114a-115">勾選 [**輸入資料行**] 核取方塊，以選取要當做輸入使用的資料行。</span><span class="sxs-lookup"><span data-stu-id="b114a-115">Select columns to use as input by checking the **Input columns** checkbox.</span></span>  
  
     <span data-ttu-id="b114a-116">這些資料行將會用來建立模式。</span><span class="sxs-lookup"><span data-stu-id="b114a-116">These columns will be used to create the patterns.</span></span> <span data-ttu-id="b114a-117">您應該從分析中刪除任何可能沒有用的資料行，例如識別碼或包含無關資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="b114a-117">You should eliminate from analysis any columns that are not likely to help, such as ID numbers, or columns that contain irrelevant data.</span></span>  
  
5.  <span data-ttu-id="b114a-118">**估計**嚮導會為您的資料集選取最佳的演算法。</span><span class="sxs-lookup"><span data-stu-id="b114a-118">The **Estimate** wizard selects the optimum algorithm for your data set.</span></span> <span data-ttu-id="b114a-119">不過，您可以按一下 [**參數**] 來開啟 [**演算法參數**] 對話方塊，並設定 [advanced options]。</span><span class="sxs-lookup"><span data-stu-id="b114a-119">However, you can click **Parameters** to open the **Algorithm Parameters** dialog box and set advanced options.</span></span>  
  
6.  <span data-ttu-id="b114a-120">如果您的資料是數值，而且您可以使用 Microsoft 線性回歸方法，您可以針對您知道 (或強烈懷疑) 與可預測值相互關聯的任何數值資料行，核取 [**回歸輸入變數**] 方塊。</span><span class="sxs-lookup"><span data-stu-id="b114a-120">If your data is numeric and you can use the Microsoft Linear Regression method, you can check the **Regressor** box for any numeric columns that you know (or strongly suspect) to be correlated with the predictable value.</span></span>  
  
     <span data-ttu-id="b114a-121">演算法接著會測試該資料行中的值，以判斷這些值是否會影響結果。</span><span class="sxs-lookup"><span data-stu-id="b114a-121">The algorithm will then test the values in that column to determine if they affect the outcomes.</span></span> <span data-ttu-id="b114a-122">如果您不確定，請按一下 [**建議**]，演算法就會測試所有資料行，並自動偵測要當做回歸輸入變數使用的最佳值。</span><span class="sxs-lookup"><span data-stu-id="b114a-122">If you are unsure, click **Suggest** and the algorithm will test all column and automatically detect the best values to use as regressors.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="b114a-123">需要迴歸輸入變數，才能建立估計值。</span><span class="sxs-lookup"><span data-stu-id="b114a-123">A regressor is required to create an estimate.</span></span> <span data-ttu-id="b114a-124">此精靈一定會根據最初資料的行程來建議最佳迴歸輸入變數；</span><span class="sxs-lookup"><span data-stu-id="b114a-124">The wizard always recommends the best regressor, based on an initial pass over the data.</span></span> <span data-ttu-id="b114a-125">因此，如果您不確定的話，最好接受建議的選擇。</span><span class="sxs-lookup"><span data-stu-id="b114a-125">Therefore, if you are not sure, it is best to accept the recommended selections.</span></span>  
  
7.  <span data-ttu-id="b114a-126">在 [將**資料分割成定型集和測試集**] 頁面上，指定是否要建立一小部分的資料來進行測試。</span><span class="sxs-lookup"><span data-stu-id="b114a-126">On the **Split data into training and testing sets** page, specify whether you want to create a small subset of the data for testing.</span></span>  
  
8.  <span data-ttu-id="b114a-127">在 [**完成]** 頁面上，提供新的「採礦結構」和「挖掘模式」的名稱，或接受所提供的預設名稱。</span><span class="sxs-lookup"><span data-stu-id="b114a-127">On the **Finish** page, provide names for the new mining structure and mining mode, or accept the default names that are provided.</span></span>  
  
9. <span data-ttu-id="b114a-128">設定用來使用此模型的選項。</span><span class="sxs-lookup"><span data-stu-id="b114a-128">Set options for using the model.</span></span>  
  
    -   <span data-ttu-id="b114a-129">選取 **[流覽]** ，立即在檢視器中開啟模型。</span><span class="sxs-lookup"><span data-stu-id="b114a-129">Select **Browse** to immediately open the model in a viewer.</span></span>  
  
         <span data-ttu-id="b114a-130">這個圖形化檢視器可顯示相依性網路圖形以及演算法產生的決策樹。</span><span class="sxs-lookup"><span data-stu-id="b114a-130">This graphical viewer displays a dependency network graph and the decision tree generated by the algorithm.</span></span> <span data-ttu-id="b114a-131">藉由瀏覽此資訊，您可以更加了解會影響預估值的因數。</span><span class="sxs-lookup"><span data-stu-id="b114a-131">By exploring this information, you can better understand the factors that contribute to the estimated values.</span></span>  
  
    -   <span data-ttu-id="b114a-132">選取 [**啟用鑽取**]，讓您分析的使用者能夠查看基礎資料。</span><span class="sxs-lookup"><span data-stu-id="b114a-132">Select **Enable drillthrough** to let users of your analysis view the underlying data.</span></span>  
  
         <span data-ttu-id="b114a-133">只有在使用決策樹 opr 線性迴歸演算法時，才可以使用此選項。</span><span class="sxs-lookup"><span data-stu-id="b114a-133">This option is available only if you use the Decision Trees opr Linear Regression algorithms.</span></span>  
  
    -   <span data-ttu-id="b114a-134">**使用暫時性模型**。</span><span class="sxs-lookup"><span data-stu-id="b114a-134">**Use temporary model**.</span></span> <span data-ttu-id="b114a-135">如果選取這個選項，此模型將無法儲存到伺服器。</span><span class="sxs-lookup"><span data-stu-id="b114a-135">If you select this option, the model will not be saved to the server.</span></span> <span data-ttu-id="b114a-136">當您關閉 Excel 時，即會刪除暫時性模型。</span><span class="sxs-lookup"><span data-stu-id="b114a-136">Temporary models are deleted when you close Excel.</span></span>  
  
## <a name="more-about-estimation-models"></a><span data-ttu-id="b114a-137">進一步了解估計模型</span><span class="sxs-lookup"><span data-stu-id="b114a-137">More About Estimation Models</span></span>  
 <span data-ttu-id="b114a-138">**估計**的 wizard 支援使用下列任何一種演算法：</span><span class="sxs-lookup"><span data-stu-id="b114a-138">The **Estimate** wizard supports the use of any of the following algorithms:</span></span>  
  
-   <span data-ttu-id="b114a-139">Microsoft 決策樹演算法</span><span class="sxs-lookup"><span data-stu-id="b114a-139">Microsoft Decision Tree algorithm</span></span>  
  
-   <span data-ttu-id="b114a-140">Microsoft 線性迴歸演算法</span><span class="sxs-lookup"><span data-stu-id="b114a-140">Microsoft Linear Regression algorithm</span></span>  
  
-   <span data-ttu-id="b114a-141">Microsoft 羅吉斯迴歸演算法</span><span class="sxs-lookup"><span data-stu-id="b114a-141">Microsoft Logistic Regression algorithm</span></span>  
  
-   <span data-ttu-id="b114a-142">Microsoft 類神經網路演算法</span><span class="sxs-lookup"><span data-stu-id="b114a-142">Microsoft Neural network algorithm</span></span>  
  
 <span data-ttu-id="b114a-143">在 [**演算法參數**] 對話方塊中，您可以根據您選擇的演算法，設定其他的 [其他] 選項。</span><span class="sxs-lookup"><span data-stu-id="b114a-143">In the **Algorithm Parameters** dialog box, you can set additional advanced options, depending on which algorithm you chose.</span></span> <span data-ttu-id="b114a-144">如需每個演算法選項的資訊，請參閱《SQL Server 線上叢書》的下列主題：</span><span class="sxs-lookup"><span data-stu-id="b114a-144">For information on the options for each algorithm see these topics in SQL Server Books Online:</span></span>  
  
 [<span data-ttu-id="b114a-145">Microsoft 決策樹演算法技術參考</span><span class="sxs-lookup"><span data-stu-id="b114a-145">Microsoft Decision Trees Algorithm Technical Reference</span></span>](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="b114a-146">Microsoft 線性迴歸演算法技術參考</span><span class="sxs-lookup"><span data-stu-id="b114a-146">Microsoft Linear Regression Algorithm Technical Reference</span></span>](data-mining/microsoft-linear-regression-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="b114a-147">Microsoft 羅吉斯迴歸演算法技術參考</span><span class="sxs-lookup"><span data-stu-id="b114a-147">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="b114a-148">Microsoft 類神經網路演算法技術參考資料</span><span class="sxs-lookup"><span data-stu-id="b114a-148">Microsoft Neural Network Algorithm Technical Reference</span></span>](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a><span data-ttu-id="b114a-149">需求</span><span class="sxs-lookup"><span data-stu-id="b114a-149">Requirements</span></span>  
 <span data-ttu-id="b114a-150">您必須連接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫，才能使用估計資料精靈。</span><span class="sxs-lookup"><span data-stu-id="b114a-150">To use the Estimate Data Wizard, you must be connected to a [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span>  
  
 <span data-ttu-id="b114a-151">如需有關如何建立連線的詳細資訊，請參閱[連接到來源資料 &#40;適用于 Excel&#41;的資料採礦用戶端](connect-to-source-data-data-mining-client-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="b114a-151">For information about how to create a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
 <span data-ttu-id="b114a-152">若要使用估計演算法，您嘗試預測的結果必須以數值表示，例如貨幣、銷售量、日期或時間。</span><span class="sxs-lookup"><span data-stu-id="b114a-152">To use the estimation algorithm, the outcome that you are trying to predict must be expressed as a numeric value, such as a currency, sales amount, date, or time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b114a-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b114a-153">See Also</span></span>  
 <span data-ttu-id="b114a-154">[建立資料採礦模型](creating-a-data-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="b114a-154">[Creating a Data Mining Model](creating-a-data-mining-model.md) </span></span>  
 [<span data-ttu-id="b114a-155">決策樹圖表逐步解說 &#40;資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="b114a-155">Decision Tree Diagram Walkthrough  &#40;Data Mining Add-ins&#41;</span></span>](decision-tree-diagram-walkthrough-data-mining-add-ins.md)  
  
  
