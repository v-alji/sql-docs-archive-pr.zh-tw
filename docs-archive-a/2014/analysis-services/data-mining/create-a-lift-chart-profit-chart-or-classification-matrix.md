---
title: 建立增益圖、收益圖或分類矩陣 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Accuracy Chart [Analysis Services], mining structures
ms.assetid: aa3d052f-58a9-4417-8e7a-5e6feb562af0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 932138b37b36269bed86df42786bd5d684f75ee9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687374"
---
# <a name="create-a-lift-chart-profit-chart-or-classification-matrix"></a><span data-ttu-id="e8cb9-102">建立增益圖、收益圖或分類矩陣</span><span class="sxs-lookup"><span data-stu-id="e8cb9-102">Create a Lift Chart, Profit Chart, or Classification Matrix</span></span>
  <span data-ttu-id="e8cb9-103">您可以使用五個基本步驟，為 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料採礦模型建立精確度圖表：</span><span class="sxs-lookup"><span data-stu-id="e8cb9-103">You can create an accuracy chart for an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] data mining model in five basic steps:</span></span>  
  
-   <span data-ttu-id="e8cb9-104">選取包含您要比較之採礦模型的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-104">Select the mining structure that contains the mining models that you want to compare.</span></span>  
  
-   <span data-ttu-id="e8cb9-105">選取要加入至圖表的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-105">Select the mining models to add to the chart.</span></span>  
  
-   <span data-ttu-id="e8cb9-106">指定要用來產生圖表的測試資料來源。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-106">Specify a source of testing data to use in generating the chart.</span></span>  
  
-   <span data-ttu-id="e8cb9-107">選擇圖表類型。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-107">Choose the chart type.</span></span>  
  
-   <span data-ttu-id="e8cb9-108">設定圖表選項。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-108">Configure the chart options.</span></span>  
  
 <span data-ttu-id="e8cb9-109">這些基本步驟對於增益圖、收益圖表和分類矩陣而言都相同。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-109">These basic steps are the same for the lift chart, profit chart, and classification matrix.</span></span> <span data-ttu-id="e8cb9-110">下列程序將概略說明為這些圖表類型設定基本圖表選項的步驟。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-110">The following procedures outline the steps to configure the basic chart options for these chart types.</span></span> <span data-ttu-id="e8cb9-111">如需如何建立交叉驗證報表的資訊，請參閱 [交叉驗證報表中的量值](measures-in-the-cross-validation-report.md)。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-111">For information about how to create a cross-validation report, see [Measures in the Cross-Validation Report](measures-in-the-cross-validation-report.md).</span></span>  
  
### <a name="open-the-mining-structure-in-the-accuracy-chart-designer"></a><span data-ttu-id="e8cb9-112">在精確度圖表設計師中開啟採礦結構</span><span class="sxs-lookup"><span data-stu-id="e8cb9-112">Open the mining structure in the Accuracy Chart Designer</span></span>  
  
1.  <span data-ttu-id="e8cb9-113">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中開啟資料採礦設計師。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-113">Open the Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="e8cb9-114">在 [方案總管] 中，按兩下包含採礦模型的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-114">In Solution Explorer, double-click the structure that contains the mining model or models.</span></span>  
  
3.  <span data-ttu-id="e8cb9-115">按一下 **[採礦精確度圖表]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-115">Click the **Mining Accuracy Chart** tab.</span></span>  
  
### <a name="select-mining-models-for-inclusion-in-the-chart"></a><span data-ttu-id="e8cb9-116">選取要包含在圖表中的採礦模型</span><span class="sxs-lookup"><span data-stu-id="e8cb9-116">Select mining models for inclusion in the chart</span></span>  
  
1.  <span data-ttu-id="e8cb9-117">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，於資料採礦設計師的 [採礦精確度圖表]\*\*\*\* 索引標籤上，按一下 [輸入選擇]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-117">On the **Mining Accuracy Chart** tab of Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Input Selection** tab.</span></span>  
  
     <span data-ttu-id="e8cb9-118">清單會顯示目前結構中所有具有相同可預測屬性的模型。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-118">The list displays all models in the current structure that have the same predictable attribute.</span></span>  
  
2.  <span data-ttu-id="e8cb9-119">針對您要包含在圖表中的每個模型選取 [顯示方塊]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-119">Select the **Show box** for each model that you want to include in the chart.</span></span>  
  
3.  <span data-ttu-id="e8cb9-120">按一下 [可預測資料行名稱]\*\*\*\* 文字方塊，然後從清單選取可預測資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-120">Click the **Predictable Column Name** text box, and select the name of a predictable column from the list.</span></span> <span data-ttu-id="e8cb9-121">您放入單一圖表中的所有模型都必須具有相同的可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-121">All models that you put in one chart must have the same predictable column.</span></span>  
  
4.  <span data-ttu-id="e8cb9-122">如果您要比較兩個模型，而可預測資料行具有不同的值或不同的資料類型，請清除 [同步處理預測資料行和值]\*\*\*\* 方塊以強制進行比較。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-122">If you compare two models and the predictable columns have different values or different data types, clear the **Synchonize prediction columns and values** box to force a comparison.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="e8cb9-123">如果選取 [同步處理預測資料行和值]\*\*\*\* 方塊，Analysis Services 就會分析模型和測試資料的可預測資料行中的資料，並嘗試尋找最佳的相符項目。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-123">If the **Synchonize prediction columns and values** box is selected, Analysis Services analyzes the data in the predictable columns of the model and the test data, and attempts to find the best match.</span></span> <span data-ttu-id="e8cb9-124">因此，請不要清除此方塊，除非絕對有必要要強制比較資料行。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-124">Therefore, do not clear the box unless absolutely necessary to force a comparison of the columns.</span></span>  
  
5.  <span data-ttu-id="e8cb9-125">按一下 [預測值]\*\*\*\* 文字方塊，然後從清單選取值。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-125">Click the **Predict Value** text box, and select a value from the list.</span></span> <span data-ttu-id="e8cb9-126">如果可預測資料行是連續的資料類型，您必須在文字方塊中輸入值。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-126">If the predictable column is a continuous data type, you must type a value in the text box.</span></span>  
  
     <span data-ttu-id="e8cb9-127">如需詳細資訊，請參閱 [選擇用於測試採礦模型的資料行](choose-the-column-to-use-for-testing-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-127">For more information, see [Choose the Column to Use for Testing a Mining Model](choose-the-column-to-use-for-testing-a-mining-model.md).</span></span>  
  
### <a name="select-testing-data"></a><span data-ttu-id="e8cb9-128">選取測試資料</span><span class="sxs-lookup"><span data-stu-id="e8cb9-128">Select testing data</span></span>  
  
1.  <span data-ttu-id="e8cb9-129">在 [採礦精確度圖表]\*\*\*\* 索引標籤的 [輸入選擇]\*\*\*\* 索引標籤上，指定要用來產生圖表的資料來源，方法是在 [選取要用於精確度圖表的資料集]\*\*\*\* 群組中選取其中一個選項。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-129">On the **Input Selection** tab of the **Mining Accuracy Chart** tab, specify the source of the data that you will use to generate the chart by selecting one of the options in the group, **Select data set to be used for accuracy chart**.</span></span>  
  
    -   <span data-ttu-id="e8cb9-130">如果您想要使用採礦結構測試案例和在模型建立期間可能套用的任何篩選的交集所定義的案例子集，請選取 [使用採礦模型測試案例]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-130">Select the option, **Use Mining Model test cases**, if you want to use the subset of cases that is defined by the intersection of the mining structure test cases and any filters that may have been applied during model creation.</span></span>  
  
    -   <span data-ttu-id="e8cb9-131">選取 [使用採礦結構測試案例]\*\*\*\* 選項可以使用採礦結構鑑效組資料集中所定義的測試案例完整集合。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-131">Select the option, **Use mining structure test cases**, to use the full set of testing cases that were defined as part of the mining structures holdout data set.</span></span>  
  
    -   <span data-ttu-id="e8cb9-132">如果您想要使用外部資料的話，請選取 [指定不同的資料集]\*\*\*\* 選項。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-132">Select the option, **Specify a different data set**, if you want to use external data.</span></span>  <span data-ttu-id="e8cb9-133">資料集必須可以作為資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-133">The data set must be available as a data source view.</span></span>   <span data-ttu-id="e8cb9-134">按一下 [流覽 (**...**) ] 按鈕，選擇要用於精確度圖表的資料表。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-134">Click the browse (**...**) button to choose the data tables to use for the accuracy chart.</span></span> <span data-ttu-id="e8cb9-135">如需詳細資訊，請參閱 [選擇和對應模型測試資料](choose-and-map-model-testing-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-135">For more information, see [Choose and Map Model Testing Data](choose-and-map-model-testing-data.md).</span></span>  
  
         <span data-ttu-id="e8cb9-136">如果您要使用外部資料集，可以選擇性地篩選輸入資料集。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-136">If you are using an external data set, you can optionally filter the input data set.</span></span> <span data-ttu-id="e8cb9-137">如需詳細資訊，請參閱 [將篩選套用至模型測試資料](apply-filters-to-model-testing-data.md)。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-137">For more information, see [Apply Filters to Model Testing Data](apply-filters-to-model-testing-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="e8cb9-138">您無法在 [**輸入選擇**] 索引標籤上的模型測試案例或 [採礦結構] 測試案例上建立篩選。若要在「採礦模型」上建立篩選，請修改模型的 Filter 屬性。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-138">You cannot create a filter on the model test cases or the mining structure test cases on the **Input Selection** tab. To create a filter on the mining model, modify the Filter property of the model.</span></span> <span data-ttu-id="e8cb9-139">如需詳細資訊，請參閱 [將篩選套用至採礦模型](apply-a-filter-to-a-mining-model.md)。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-139">For more information, see [Apply a Filter to a Mining Model](apply-a-filter-to-a-mining-model.md).</span></span>  
  
### <a name="configure-chart-settings-and-generate-the-chart"></a><span data-ttu-id="e8cb9-140">設定圖表設定並產生圖表</span><span class="sxs-lookup"><span data-stu-id="e8cb9-140">Configure chart settings and generate the chart</span></span>  
  
1.  <span data-ttu-id="e8cb9-141">在 [採礦精確度圖表]\*\*\*\* 索引標籤中，針對要建立的圖表按一下索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-141">In the **Mining Accuracy Chart** tab, click the tab for the chart you want to create.</span></span>  
  
2.  <span data-ttu-id="e8cb9-142">針對增益**圖**，按一下 [增益**圖**] 索引標籤。圖表會根據您剛才選取的模型、可預測屬性和輸入資料自動產生。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-142">For a **lift chart**, click the **Lift Chart** tab. The chart is automatically generated based on the model, predictable attributes, and input data that you just selected.</span></span>  
  
3.  <span data-ttu-id="e8cb9-143">若為**分類矩陣**，請按一下 [**分類矩陣**] 索引標籤。不需要進一步的設定;圖表會根據您選取的輸入資料和模型自動產生。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-143">For a **classification matrix**, click the **Classification Matrix** tab. No further settings are needed; the chart is automatically generated based on the input data and model that you selected.</span></span>  
  
4.  <span data-ttu-id="e8cb9-144">若為**收益圖**，請先按一下 [增益**圖**] 索引標籤。然後，從 [**圖表類型**] 下拉式清單中選取 [**收益圖**]。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-144">For a **profit chart**, first click the **Lift Chart** tab. Then, from the **Chart type** drop-down list, select **Profit chart**.</span></span>  
  
     <span data-ttu-id="e8cb9-145">在 [收益圖設定]\*\*\*\* 對話方塊中輸入下列設定。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-145">Enter the following settings in the **Profit Chart Settings** dialog box.</span></span>  
  
     <span data-ttu-id="e8cb9-146">**人數**</span><span class="sxs-lookup"><span data-stu-id="e8cb9-146">**Population**</span></span>  
     <span data-ttu-id="e8cb9-147">當您建立增益圖時，想要使用之資料集內的案例數。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-147">The number of cases from the data set that you want to use when creating the lift chart.</span></span>  
  
     <span data-ttu-id="e8cb9-148">此模型一定會依據遞減機率的順序來選擇案例；也就是說，如果您要評估潛在的客戶，並選擇只代表客戶資料庫中一半記錄的數目，此模型將會針對最適合模型的案例子集來測量精確度。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-148">The model always chooses the cases in order of decreasing probability; that is, if you are assessing potential customers and you choose a number that represents only half the records in your customer database, the model will measure accuracy on the subset of cases that best fit your model.</span></span>  
  
     <span data-ttu-id="e8cb9-149">這是因為當您使用此模型來產生郵寄或建立促銷活動時，您將會使用與每一個案例有關聯的預測機率，只針對做出正面回應的機率最高的客戶。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-149">This is because when you use the model to generate a mailing or create a campaign, you will use the prediction probability associated with each case to target only the customers who have the highest probability of making a positive response.</span></span>  
  
     <span data-ttu-id="e8cb9-150">**固定成本**</span><span class="sxs-lookup"><span data-stu-id="e8cb9-150">**Fixed Cost**</span></span>  
     <span data-ttu-id="e8cb9-151">與商業問題相關聯的固定成本。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-151">The fixed cost that is associated with the business problem.</span></span>  
  
     <span data-ttu-id="e8cb9-152">如果這是針對郵寄方案，則固定成本可能代表印表機安裝費用，其中涵蓋了準備促銷郵件的初始成本。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-152">If this were for a targeted mailing solution, the fixed cost might represent a printer setup fee that covers the initial cost of preparing the promotional mailing.</span></span>  
  
     <span data-ttu-id="e8cb9-153">這項成本會套用到整個目標母體一次。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-153">This cost applies one time to the entire target population.</span></span>  
  
     <span data-ttu-id="e8cb9-154">**個別成本**</span><span class="sxs-lookup"><span data-stu-id="e8cb9-154">**Individual Cost**</span></span>  
     <span data-ttu-id="e8cb9-155">除了固定成本外，與每一個客戶連絡的相關聯成本。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-155">Costs that are in addition to the fixed cost, that can be associated with each customer contact.</span></span> <span data-ttu-id="e8cb9-156">例如，您可能會輸入促銷郵件的郵資成本或是打電話的成本。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-156">For example, you might enter the postage cost for a promotional mailing or the cost of making telephone calls.</span></span>  
  
     <span data-ttu-id="e8cb9-157">這個成本對於整個目標母體都必須是相同的。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-157">This cost must be the same for the entire target population.</span></span> <span data-ttu-id="e8cb9-158">每個值都會乘以目標的案例數。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-158">Each value is multiplied by the number of cases that are targeted.</span></span>  
  
     <span data-ttu-id="e8cb9-159">**每個人的收入**</span><span class="sxs-lookup"><span data-stu-id="e8cb9-159">**Revenue Per Individual**</span></span>  
     <span data-ttu-id="e8cb9-160">與每一次成功銷售相關聯的營收金額。</span><span class="sxs-lookup"><span data-stu-id="e8cb9-160">The amount of revenue that is associated with each successful sale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8cb9-161">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8cb9-161">See Also</span></span>  
 <span data-ttu-id="e8cb9-162">[增益圖 &#40;Analysis Services-資料採礦&#41;](lift-chart-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="e8cb9-162">[Lift Chart &#40;Analysis Services - Data Mining&#41;](lift-chart-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="e8cb9-163">分類矩陣 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="e8cb9-163">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](classification-matrix-analysis-services-data-mining.md)  
  
  
