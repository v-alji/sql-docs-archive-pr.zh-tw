---
title: 第5課：建立類神經網路和羅吉斯回歸模型 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- logistic regression [Analysis Services]
- data mining [Analysis Services], tutorials
- neural networks
- tutorials [Data Mining]
- neural network model [Analysis Services]
ms.assetid: 42c3701a-1fd2-44ff-b7de-377345bbbd6b
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a8c9fcf0380582f15fa2bf30d6fdeb97bb2ab1fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594867"
---
# <a name="lesson-5-building-neural-network-and-logistic-regression-models-intermediate-data-mining-tutorial"></a><span data-ttu-id="7e7fc-102">第五課：建立類神經網路和羅吉斯迴歸模型 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="7e7fc-102">Lesson 5: Building Neural Network and Logistic Regression Models (Intermediate Data Mining Tutorial)</span></span>
  
  
 <span data-ttu-id="7e7fc-103">[!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] 的營業部門正在負責處理一個專案，目標是提升撥接中心的客戶滿意度。</span><span class="sxs-lookup"><span data-stu-id="7e7fc-103">The Operations department of [!INCLUDE[ssSampleDBCoShort](../includes/sssampledbcoshort-md.md)] is engaged in a project to improve customer satisfaction with their call center.</span></span> <span data-ttu-id="7e7fc-104">他們雇用廠商來管理撥接中心、回報撥接中心績效的數據，並要求您分析廠商所提供的一些初步資料。</span><span class="sxs-lookup"><span data-stu-id="7e7fc-104">They hired a vendor to manage the call center and to report metrics on call center effectiveness, and have asked you to analyze some preliminary data provided by the vendor.</span></span> <span data-ttu-id="7e7fc-105">他們想要知道是否有任何有趣的發現。</span><span class="sxs-lookup"><span data-stu-id="7e7fc-105">They want to know if there are any interesting findings.</span></span> <span data-ttu-id="7e7fc-106">他們尤其想知道這些資料是否反映出有關人員雇用的任何問題，或改善客戶滿意度的方式。</span><span class="sxs-lookup"><span data-stu-id="7e7fc-106">In particular, they would like to know if the data suggests any staffing problems with staffing or ways to improve customer satisfaction.</span></span>  
  
 <span data-ttu-id="7e7fc-107">這個資料集很小，只包含期限為 30 天的撥接中心作業。</span><span class="sxs-lookup"><span data-stu-id="7e7fc-107">The data set is small and covers only a 30-day period in the operation of the call center.</span></span> <span data-ttu-id="7e7fc-108">這些資料會追蹤每個排班的新進和資深操作員數目、來電數目、訂單數目、必須解決的問題數目，以及客戶等候電話回應的平均時間。</span><span class="sxs-lookup"><span data-stu-id="7e7fc-108">The data tracks the number of new and experienced operators in each shift, the number of incoming calls, the number of orders as well as issues that must be resolved, and the average time a customer waits for someone to respond to a call.</span></span> <span data-ttu-id="7e7fc-109">資料也包含以 *「放棄率」*(Abandon Rate) (這是客戶挫折度的指標) 為基礎的服務品質標準。</span><span class="sxs-lookup"><span data-stu-id="7e7fc-109">The data also includes a service quality metric based on *abandon rate*, which is an indicator of customer frustration.</span></span>  
  
 <span data-ttu-id="7e7fc-110">由於您對於資料呈現的內容沒有任何預先的期待，因此您決定使用類神經網路模型來探索可能的相互關聯。</span><span class="sxs-lookup"><span data-stu-id="7e7fc-110">Because you do not have any prior expectations about what the data will show, you decide to use a neural network model to explore possible correlations.</span></span> <span data-ttu-id="7e7fc-111">類神經網路模型經常用於進行探索，因為這種模型可以分析許多輸入和輸出之間的複雜關聯性。</span><span class="sxs-lookup"><span data-stu-id="7e7fc-111">Neural network models are often used for exploration because they can analyze complex relationships between many inputs and outputs.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="7e7fc-112">學習內容</span><span class="sxs-lookup"><span data-stu-id="7e7fc-112">What You Will Learn</span></span>  
 <span data-ttu-id="7e7fc-113">在本課中，您將使用類神經網路演算法建立模型，幫助您和營業小組理解資料中的趨勢。</span><span class="sxs-lookup"><span data-stu-id="7e7fc-113">In this lesson, you will use the neural network algorithm to build a model that you and the Operations team can use to understand the trends in the data.</span></span> <span data-ttu-id="7e7fc-114">在這個課程中，您將嘗試回答下列問題：</span><span class="sxs-lookup"><span data-stu-id="7e7fc-114">As part of this lesson, you will try to answer the following questions:</span></span>  
  
-   <span data-ttu-id="7e7fc-115">什麼因數會影響客戶滿意度？</span><span class="sxs-lookup"><span data-stu-id="7e7fc-115">What factors affect customer satisfaction?</span></span>  
  
-   <span data-ttu-id="7e7fc-116">撥接中心可以做些什麼來改善服務品質？</span><span class="sxs-lookup"><span data-stu-id="7e7fc-116">What can the call center do to improve service quality?</span></span>  
  
 <span data-ttu-id="7e7fc-117">根據這些結果，您將接著建立一個羅吉斯迴歸模型以進行預測。</span><span class="sxs-lookup"><span data-stu-id="7e7fc-117">Based on the results, you will then build a logistic regression model that you can use for predictions.</span></span> <span data-ttu-id="7e7fc-118">營業小組將使用這些預測來協助規劃撥接中心作業。</span><span class="sxs-lookup"><span data-stu-id="7e7fc-118">The predictions will be used by the Operations team as an aid in planning call center operation.</span></span>  
  
 <span data-ttu-id="7e7fc-119">這個課程包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="7e7fc-119">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="7e7fc-120">加入撥打電話中心資料的資料來源視圖 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="7e7fc-120">Adding a Data Source View for Call Center Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/add-data-source-view-call-center-data-intermediate-data-mining.md)  
  
-   [<span data-ttu-id="7e7fc-121">建立類神經網路結構和模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="7e7fc-121">Creating a Neural Network Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="7e7fc-122">流覽撥打電話中心模型 &#40;元資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="7e7fc-122">Exploring the Call Center Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-call-center-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="7e7fc-123">&#40;元資料採礦教學課程中，將羅吉斯回歸模型加入至撥中心結構&#41;</span><span class="sxs-lookup"><span data-stu-id="7e7fc-123">Adding a Logistic Regression Model to the Call Center Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/add-logistic-regression-model-to-call-center-intermediate-data-mining.md)  
  
-   [<span data-ttu-id="7e7fc-124">&#40;中繼資料採礦教學課程建立撥打電話中心模型的預測&#41;</span><span class="sxs-lookup"><span data-stu-id="7e7fc-124">Creating Predictions for the Call Center Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-predictions-call-center-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="7e7fc-125">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="7e7fc-125">Next Task in Lesson</span></span>  
 [<span data-ttu-id="7e7fc-126">加入撥打電話中心資料的資料來源視圖 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="7e7fc-126">Adding a Data Source View for Call Center Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/add-data-source-view-call-center-data-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a><span data-ttu-id="7e7fc-127">所有課程</span><span class="sxs-lookup"><span data-stu-id="7e7fc-127">All Lessons</span></span>  
 [<span data-ttu-id="7e7fc-128">第1課：建立中繼資料採礦解決方案 &#40;元資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="7e7fc-128">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="7e7fc-129">第2課：建立預測案例 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="7e7fc-129">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="7e7fc-130">第 3 課：建立購物籃狀況 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="7e7fc-130">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="7e7fc-131">第4課：建立時序群集案例 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="7e7fc-131">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 <span data-ttu-id="7e7fc-132">第五課：類神經網路和羅吉斯迴歸案例 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="7e7fc-132">Lesson 5: Neural Network and Logistic Regression Scenario (Intermediate Data Mining Tutorial)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e7fc-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7e7fc-133">See Also</span></span>  
 <span data-ttu-id="7e7fc-134">[基本資料採礦教學課程](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="7e7fc-134">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="7e7fc-135">元資料採礦教學課程 &#40;Analysis Services-資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="7e7fc-135">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
