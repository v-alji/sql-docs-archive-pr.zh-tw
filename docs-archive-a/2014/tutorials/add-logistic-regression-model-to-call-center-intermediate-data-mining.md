---
title: 將羅吉斯回歸模型加入至話務中心結構 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 97abb77a-346c-44fa-8959-688dee1af6a8
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 7d0100313d1ea5a1af5f729249bc2d743a730222
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704514"
---
# <a name="adding-a-logistic-regression-model-to-the-call-center-structure-intermediate-data-mining-tutorial"></a><span data-ttu-id="9c423-102">將羅吉斯迴歸模型加入到撥接中心結構 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="9c423-102">Adding a Logistic Regression Model to the Call Center Structure (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="9c423-103">除了分析可能會影響撥接中心作業的因數之外，您還必須提供有關員工如何改進服務品質的一些特定建議。</span><span class="sxs-lookup"><span data-stu-id="9c423-103">In addition to analyzing the factors that might affect call center operations, you were also asked to provide some specific recommendations on how the staff can improve service quality.</span></span> <span data-ttu-id="9c423-104">在這個工作中，您將使用和探勘模型相同的採礦結構，並加入一個採礦模型用於建立預測。</span><span class="sxs-lookup"><span data-stu-id="9c423-104">In this task, you will use the same mining structure that you used to build the exploratory model and add a mining model that will be used for creating predictions.</span></span>  
  
 <span data-ttu-id="9c423-105">在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中，羅吉斯迴歸模型是以類神經網路演算法為基礎，因此與類神經網路模型提供相同的彈性和功能。</span><span class="sxs-lookup"><span data-stu-id="9c423-105">In [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], a logistic regression model is based on the neural networks algorithm, and therefore provides the same flexibility and power as a neural network model.</span></span> <span data-ttu-id="9c423-106">不過，羅吉斯迴歸演算法特別適合用來預測二進位結果。</span><span class="sxs-lookup"><span data-stu-id="9c423-106">However, logistic regression is particularly well-suited for predicting binary outcomes.</span></span>  
  
 <span data-ttu-id="9c423-107">在這個案例中，您將使用類神經網路模型所用的相同採礦結構。</span><span class="sxs-lookup"><span data-stu-id="9c423-107">For this scenario, you will use the same mining structure that you used for the neural network model.</span></span> <span data-ttu-id="9c423-108">不過，您將針對您的商務問題自訂新的模型。</span><span class="sxs-lookup"><span data-stu-id="9c423-108">However, you will customize the new model to target your business questions.</span></span> <span data-ttu-id="9c423-109">您對改進服務品質及判斷所需的資深操作員人數特別感興趣，因此將設定模型以預測這些值。</span><span class="sxs-lookup"><span data-stu-id="9c423-109">You are interested in improving service quality and determining how many experienced operators you need, so you will set up your model to predict those values.</span></span>  
  
 <span data-ttu-id="9c423-110">為了確保以撥接中心資料為基礎的所有模型盡可能相似，您將使用和以前相同的初始值。</span><span class="sxs-lookup"><span data-stu-id="9c423-110">To ensure that all the models based on the call center data are as similar as possible, you will use the same seed value as before.</span></span> <span data-ttu-id="9c423-111">設定種子參數可確保模型會從相同起點開始處理資料，將資料中的成品所造成的變化降至最低。</span><span class="sxs-lookup"><span data-stu-id="9c423-111">Setting the seed parameter ensures that the model processes the data from the same starting point, and minimizes variations caused by artifacts in the data.</span></span>  
  
### <a name="to-add-a-new-mining-model-to-the-call-center-mining-structure"></a><span data-ttu-id="9c423-112">將新的採礦模型加入到撥接中心採礦結構中</span><span class="sxs-lookup"><span data-stu-id="9c423-112">To add a new mining model to the call center mining structure</span></span>  
  
1.  <span data-ttu-id="9c423-113">在的 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 方案總管中，以滑鼠右鍵按一下 [採礦結構]、[**撥接中心分類收納**]，然後選取 [**開啟設計**工具]。</span><span class="sxs-lookup"><span data-stu-id="9c423-113">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, right-click the mining structure, **Call Center Binned**, and select **Open Designer**.</span></span>  
  
2.  <span data-ttu-id="9c423-114">在資料採礦設計工具中，按一下 [**採礦模型**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="9c423-114">In Data Mining Designer, click the **Mining Models** tab.</span></span>  
  
3.  <span data-ttu-id="9c423-115">按一下 [**建立相關的採礦模型**]。</span><span class="sxs-lookup"><span data-stu-id="9c423-115">Click **Create a related mining model**.</span></span>  
  
4.  <span data-ttu-id="9c423-116">在 [**新增採礦模型**] 對話方塊的 [**模型名稱**] 中，輸入 `Call Center - LR` 。</span><span class="sxs-lookup"><span data-stu-id="9c423-116">In the **New Mining Model** dialog box, for **Model name**, type `Call Center - LR`.</span></span>  <span data-ttu-id="9c423-117">在 [**演算法名稱]** 中，選取 [ **Microsoft 羅吉斯回歸**]。</span><span class="sxs-lookup"><span data-stu-id="9c423-117">For **Algorithm name**, select **Microsoft Logistic Regression**.</span></span>  
  
5.  <span data-ttu-id="9c423-118">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="9c423-118">Click **OK**.</span></span>  
  
     <span data-ttu-id="9c423-119">新的採礦模型會顯示在 [**採礦模型**] 索引標籤中。</span><span class="sxs-lookup"><span data-stu-id="9c423-119">The new mining model is displayed in the **Mining Models** tab.</span></span>  
  
### <a name="to-customize-the-logistic-regression-model"></a><span data-ttu-id="9c423-120">自訂羅吉斯迴歸模型</span><span class="sxs-lookup"><span data-stu-id="9c423-120">To customize the logistic regression model</span></span>  
  
1.  <span data-ttu-id="9c423-121">在新的「採礦模型」的資料行中， `Call Center - LR` 保留事實 CALLCENTER ID 做為索引鍵。</span><span class="sxs-lookup"><span data-stu-id="9c423-121">In the column for the new mining model, `Call Center - LR`, leave Fact CallCenter ID as the key.</span></span>  
  
2.  <span data-ttu-id="9c423-122">將 [ServiceGrade] 和 [層級 2] 運算子的值變更為 [**預測**]。</span><span class="sxs-lookup"><span data-stu-id="9c423-122">Change the value of ServiceGrade and Level Two Operators to **Predict**.</span></span>  
  
     <span data-ttu-id="9c423-123">這些資料行將同時用於輸入和預測。</span><span class="sxs-lookup"><span data-stu-id="9c423-123">These columns will be used both as input and for prediction.</span></span> <span data-ttu-id="9c423-124">基本上，您是在相同的資料上建立兩個不同的模型：一個用來預測操作員人數，一個用來預測服務等級。</span><span class="sxs-lookup"><span data-stu-id="9c423-124">In essence, you are creating two separate models on the same data: one that predicts the number of operators, and one that predicts the service grade.</span></span>  
  
3.  <span data-ttu-id="9c423-125">將所有其他資料行變更為 [**輸入**]。</span><span class="sxs-lookup"><span data-stu-id="9c423-125">Change all other columns to **Input**.</span></span>  
  
### <a name="to-specify-the-seed-and-process-the-models"></a><span data-ttu-id="9c423-126">指定種子和處理模型</span><span class="sxs-lookup"><span data-stu-id="9c423-126">To specify the seed and process the models</span></span>  
  
1.  <span data-ttu-id="9c423-127">在 [**採礦模型**] 索引標籤中，以滑鼠右鍵按一下名為 [撥接中心-LR] 之模型的資料行，然後選取 [**設定演算法參數]**。</span><span class="sxs-lookup"><span data-stu-id="9c423-127">In the **Mining Model** tab, right-click the column for the model named Call Center - LR, and select **Set Algorithm Parameters**.</span></span>  
  
2.  <span data-ttu-id="9c423-128">在 [HOLDOUT_SEED] 參數的資料列中，按一下 [**值**] 底下的空白資料格，然後輸入 `1` 。</span><span class="sxs-lookup"><span data-stu-id="9c423-128">In the row for the HOLDOUT_SEED parameter, click the empty cell under **Value**, and type `1`.</span></span> <span data-ttu-id="9c423-129">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="9c423-129">Click **OK**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9c423-130">只要您將相同的種子用於所有相關的模型，您選擇做為種子的值就不重要了。</span><span class="sxs-lookup"><span data-stu-id="9c423-130">The value that you choose as the seed does not matter, as long as you use the same seed for all related models.</span></span>  
  
3.  <span data-ttu-id="9c423-131">在 [**採礦模型**] 功能表中，選取 [**處理採礦結構] 和 [所有模型**]。</span><span class="sxs-lookup"><span data-stu-id="9c423-131">In the **Mining Models** menu, select **Process Mining Structure and All Models**.</span></span> <span data-ttu-id="9c423-132">按一下 **[是]** ，將更新的資料採礦專案部署到伺服器。</span><span class="sxs-lookup"><span data-stu-id="9c423-132">Click **Yes** to deploy the updated data mining project to the server.</span></span>  
  
4.  <span data-ttu-id="9c423-133">在 [**處理採礦模型**] 對話方塊中，按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="9c423-133">In the **Process Mining Model** dialog box, click **Run**.</span></span>  
  
5.  <span data-ttu-id="9c423-134">按一下 [**關閉**] 以關閉 [**處理進度**] 對話方塊，然後在 [**處理採礦模型**] 對話方塊中再次按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="9c423-134">Click **Close** to close the **Process Progress** dialog box, and then click **Close** again in the **Process Mining Model** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="9c423-135">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="9c423-135">Next Task in Lesson</span></span>  
 [<span data-ttu-id="9c423-136">&#40;中繼資料採礦教學課程建立撥打電話中心模型的預測&#41;</span><span class="sxs-lookup"><span data-stu-id="9c423-136">Creating Predictions for the Call Center Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="9c423-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c423-137">See Also</span></span>  
 [<span data-ttu-id="9c423-138">處理需求和考量 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="9c423-138">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
