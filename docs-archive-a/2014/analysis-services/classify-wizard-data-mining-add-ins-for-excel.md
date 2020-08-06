---
title: 適用于 Excel) 的資料採礦增益集 (分類嚮導 |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data modeling [data mining]
- classification [data mining]
ms.assetid: 409c5076-c4c3-4f09-8f30-d3297df45f13
author: minewiskan
ms.author: owend
ms.openlocfilehash: b82fc98df10ae2e6754a378dacea108f9f3379ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593072"
---
# <a name="classify-wizard-data-mining-add-ins-for-excel"></a><span data-ttu-id="7a1ed-102">分類精靈 (適用於 Excel 的資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="7a1ed-102">Classify Wizard (Data Mining Add-ins for Excel)</span></span>
  <span data-ttu-id="7a1ed-103">![資料採礦功能區中的分類精靈](media/dmc-classify.gif "資料採礦功能區中的分類精靈")</span><span class="sxs-lookup"><span data-stu-id="7a1ed-103">![Classify wizard in Data Mining ribbon](media/dmc-classify.gif "Classify wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="7a1ed-104">[**分類**] wizard 可協助您根據 excel 資料表、excel 範圍或外部資料源中的現有資料，建立分類模型。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-104">The **Classify** wizard helps you build a classification model based on existing data in an Excel table, an Excel range, or an external data source.</span></span>  
  
 <span data-ttu-id="7a1ed-105">分類模型會擷取可指示資料相似性的模式，並協助您根據值的分組來做出預測。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-105">A classification model extracts patterns in your data that indicate similarities and helps you make predictions based on groupings of values.</span></span> <span data-ttu-id="7a1ed-106">例如，分類模型可能會用來根據收入或花費模式預測風險。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-106">For example, a classification model might be used to predict risk based on income or spending patterns.</span></span>  
  
## <a name="using-the-classify-wizard"></a><span data-ttu-id="7a1ed-107">使用分類精靈</span><span class="sxs-lookup"><span data-stu-id="7a1ed-107">Using the Classify Wizard</span></span>  
  
1.  <span data-ttu-id="7a1ed-108">在 [**資料採礦**] 功能區中，按一下 [**分類**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-108">In the **Data Mining** ribbon, click **Classify**, and then click **Next**.</span></span>  
  
2.  <span data-ttu-id="7a1ed-109">在 [**選取來源資料**] 頁面中，選擇要分析的資料。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-109">In the **Select Source Data** page, choose the data to analyze.</span></span>  
  
     <span data-ttu-id="7a1ed-110">此精靈支援多種資料類型：Excel 資料表、Excel 範圍和外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-110">This wizard supports multiple kinds of data: Excel tables, Excel ranges, and external data sources.</span></span> <span data-ttu-id="7a1ed-111">使用外部資料時，您可以將資料加入 Excel，或者在 Analysis Services 資料來源中選擇一組資料表或檢視。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-111">With external data, you can either add it into Excel, or choose a set of tables or views in an Analysis Services data source.</span></span> <span data-ttu-id="7a1ed-112">您也可以新增資料表並變更資料行，以建立隨選資料來源。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-112">You can also add tables and change columns to create ad hoc data sources.</span></span>  
  
3.  <span data-ttu-id="7a1ed-113">在 [**分類**] 頁面上，選擇您想要分類的資料行。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-113">On the **Classification** page, choose the column that you want to classify.</span></span>  
  
     <span data-ttu-id="7a1ed-114">請檢查清單中的資料行、**輸入資料行**，然後取消選取任何具有唯一值的資料行，因此不適合用來建立模式，例如 ID 號碼、客戶名稱等等。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-114">Review the columns in the list, **Input columns**, and deselect any columns that have unique values and thus aren't useful for creating patterns, such as ID numbers, customer names, and so on.</span></span> <span data-ttu-id="7a1ed-115">您也應該將基本上與可分類資料行重複的資料行移除。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-115">You should also remove columns that essentially duplicate the classifiable column.</span></span>  
  
     <span data-ttu-id="7a1ed-116">例如，如果您想分類產品類別的預測，應該排除含有已知商務規則的子類別欄位，否則該規則的強度可能會防止您探索其他相互關聯。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-116">For example, if you are classifying predicting the category of a product, you should exclude the subcategory field if there is a known business rule, or else the strength of that rule might prevent you from discovering other correlations.</span></span>  
  
4.  <span data-ttu-id="7a1ed-117">（選擇性）按一下 [**參數**] 以變更演算法參數，並自訂群集模型的行為。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-117">Optionally, click **Parameters** to change the algorithm parameters and customize the behavior of the clustering model.</span></span>  
  
5.  <span data-ttu-id="7a1ed-118">在 [將**資料分割成定型集和測試集**] 頁面上，指定要保留多少資料來進行測試。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-118">In the **Split data into training and testing sets** page, specify how much data to hold out for testing.</span></span> <span data-ttu-id="7a1ed-119">定型模型時，一律會使用其餘資料。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-119">The remainder is always used for training the model.</span></span>  
  
     <span data-ttu-id="7a1ed-120">預設設定為 30% 測試資料和 70% 定型資料。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-120">The default setting is 30% testing data and 70% training data.</span></span>  
  
6.  <span data-ttu-id="7a1ed-121">在 [**完成]** 頁面上，為您的資料集和模型提供描述性的名稱，並設定下列選項來控制如何使用完成的模型：</span><span class="sxs-lookup"><span data-stu-id="7a1ed-121">On the **Finish** page, provide a descriptive name for your data set and model, and set the following options that control how you work with the finished model:</span></span>  
  
    -   <span data-ttu-id="7a1ed-122">**流覽模型**。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-122">**Browse model**.</span></span> <span data-ttu-id="7a1ed-123">選取這個選項時，一旦 wizard 完成模型的處理，就會開啟 **[流覽**] 視窗以協助您流覽結果。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-123">When this option is selected, as soon as the wizard finishes processing the model, it opens a **Browse** window to help you explore the results.</span></span> <span data-ttu-id="7a1ed-124">檢視器的內容取決於建立的模型類型。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-124">The contents of the viewer depend on the type of model you built.</span></span> <span data-ttu-id="7a1ed-125">如需詳細資訊，請參閱[流覽決策樹模型](browsing-a-decision-trees-model.md)和[流覽類神經網路模型](browsing-a-neural-network-model.md)。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-125">For more information, see [Browsing a Decision Trees Model](browsing-a-decision-trees-model.md) and [Browsing a Neural Network Model](browsing-a-neural-network-model.md).</span></span>  
  
    -   <span data-ttu-id="7a1ed-126">**啟用 [鑽取**]。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-126">**Enable drillthrough**.</span></span> <span data-ttu-id="7a1ed-127">選取此選項可檢視完成模型中的基礎資料。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-127">Select this option to view the underlying data from the finished model.</span></span> <span data-ttu-id="7a1ed-128">只有建立決策樹模型時，才能使用這個選項。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-128">This option is only available if you build a Decision Tree model.</span></span>  
  
    -   <span data-ttu-id="7a1ed-129">**使用暫時性模型**。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-129">**Use temporary model**.</span></span> <span data-ttu-id="7a1ed-130">如果選取這個選項，此模型將無法儲存到伺服器。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-130">If you select this option, the model will not be saved to the server.</span></span> <span data-ttu-id="7a1ed-131">當您關閉 Excel 時，即會刪除暫時性模型。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-131">Temporary models are deleted when you close Excel.</span></span>  
  
## <a name="more-about-classification-models"></a><span data-ttu-id="7a1ed-132">深入了解分類模型</span><span class="sxs-lookup"><span data-stu-id="7a1ed-132">More About Classification Models</span></span>  
 <span data-ttu-id="7a1ed-133">在 [**演算法參數**] 對話方塊中，您也可以從 Analysis Services 所提供的演算法中選擇分類方法：</span><span class="sxs-lookup"><span data-stu-id="7a1ed-133">In the **Algorithm Parameters** dialog box, you can also choose the classification method from among these algorithms provided in Analysis Services:</span></span>  
  
-   <span data-ttu-id="7a1ed-134">Microsoft 決策樹</span><span class="sxs-lookup"><span data-stu-id="7a1ed-134">Microsoft Decision Tree</span></span>  
  
-   <span data-ttu-id="7a1ed-135">Microsoft 羅吉斯迴歸</span><span class="sxs-lookup"><span data-stu-id="7a1ed-135">Microsoft Logistic Regression</span></span>  
  
-   <span data-ttu-id="7a1ed-136">Microsoft 貝氏機率分類</span><span class="sxs-lookup"><span data-stu-id="7a1ed-136">Microsoft Naïve Bayes</span></span>  
  
-   <span data-ttu-id="7a1ed-137">Microsoft 類神經網路</span><span class="sxs-lookup"><span data-stu-id="7a1ed-137">Microsoft Neural Network</span></span>  
  
 <span data-ttu-id="7a1ed-138">雖然演算法可能產生類似的結果，但是其分析資料的方式並不同，因此建議嘗試數種演算法並比較結果。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-138">Although the algorithms might yield similar results, they analyze the data differently, so we recommend trying several algorithms and comparing the results.</span></span> <span data-ttu-id="7a1ed-139">預設方法是 Microsoft 決策樹。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-139">The default method is Microsoft Decision Trees.</span></span>  
  
 <span data-ttu-id="7a1ed-140">在 [**參數**] 清單中，您可以變更 [advanced options]，這取決於您選擇的演算法類型。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-140">In the **Parameters** list, you can change advanced options, which depend on the type of algorithm you choose.</span></span> <span data-ttu-id="7a1ed-141">每個演算法的參數在《SQL Server 線上叢書》中有更詳細的說明。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-141">The parameters for each algorithm are described in more detail in SQL Server Books Online.</span></span>  
  
 [<span data-ttu-id="7a1ed-142">Microsoft 決策樹演算法技術參考</span><span class="sxs-lookup"><span data-stu-id="7a1ed-142">Microsoft Decision Trees Algorithm Technical Reference</span></span>](data-mining/microsoft-decision-trees-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="7a1ed-143">Microsoft 羅吉斯迴歸演算法技術參考</span><span class="sxs-lookup"><span data-stu-id="7a1ed-143">Microsoft Logistic Regression Algorithm Technical Reference</span></span>](data-mining/microsoft-logistic-regression-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="7a1ed-144">Microsoft 貝氏機率分類演算法技術參考</span><span class="sxs-lookup"><span data-stu-id="7a1ed-144">Microsoft Naive Bayes Algorithm Technical Reference</span></span>](data-mining/microsoft-naive-bayes-algorithm-technical-reference.md)  
  
 [<span data-ttu-id="7a1ed-145">Microsoft 類神經網路演算法技術參考資料</span><span class="sxs-lookup"><span data-stu-id="7a1ed-145">Microsoft Neural Network Algorithm Technical Reference</span></span>](data-mining/microsoft-neural-network-algorithm-technical-reference.md)  
  
### <a name="requirements"></a><span data-ttu-id="7a1ed-146">需求</span><span class="sxs-lookup"><span data-stu-id="7a1ed-146">Requirements</span></span>  
 <span data-ttu-id="7a1ed-147">若要使用 [**分類**] wizard，您必須連接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-147">To use the **Classify** wizard, you must be connected to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="7a1ed-148">如需有關如何建立連線的詳細資訊，請參閱[連接到來源資料 &#40;適用于 Excel&#41;的資料採礦用戶端](connect-to-source-data-data-mining-client-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="7a1ed-148">For information about how to create a connection, see [Connect to Source Data &#40;Data Mining Client for Excel&#41;](connect-to-source-data-data-mining-client-for-excel.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a1ed-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7a1ed-149">See Also</span></span>  
 [<span data-ttu-id="7a1ed-150">建立資料採礦模型</span><span class="sxs-lookup"><span data-stu-id="7a1ed-150">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)  
  
  
