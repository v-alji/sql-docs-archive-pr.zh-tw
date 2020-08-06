---
title: 第4課：建立時序群集案例 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- sequence clustering algorithms [Analysis Services]
- tutorials [Data Mining]
ms.assetid: 63436bbd-0f73-4012-b6f1-358c81e4d92a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 0f417c685d8af898de7c66ffe82045fa76b582e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686555"
---
# <a name="lesson-4-building-a-sequence-clustering-scenario-intermediate-data-mining-tutorial"></a><span data-ttu-id="593ea-102">第 4 課：建立時序群集案例 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="593ea-102">Lesson 4: Building a Sequence Clustering Scenario (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="593ea-103">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 的行銷部門想了解客戶如何在 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 網站中隨意瀏覽。</span><span class="sxs-lookup"><span data-stu-id="593ea-103">The marketing department of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] wants to understand how customers move through the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] Web site.</span></span> <span data-ttu-id="593ea-104">公司猜想客戶會依某種次序模式，將產品放入購物籃中。</span><span class="sxs-lookup"><span data-stu-id="593ea-104">The company suspects that there is a pattern to the order in which customers put products into their shopping baskets.</span></span> <span data-ttu-id="593ea-105">公司希望分析購物次序，以了解客戶如何將相關的產品加入購物籃中。</span><span class="sxs-lookup"><span data-stu-id="593ea-105">They want to analyze the order of purchase sequences to learn how customers add related items to their baskets.</span></span> <span data-ttu-id="593ea-106">之後，他們就能利用這項資訊來簡化網站的流程，以便引導客戶購買其他產品。</span><span class="sxs-lookup"><span data-stu-id="593ea-106">They can then use this information to streamline the flow of the Web site so that it leads customers to purchase additional products.</span></span>  
  
 <span data-ttu-id="593ea-107">當您完成這個課程的工作時，將會建好一個採礦模型，使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 時序群集演算法預測客戶接著會將哪一項產品放入購物籃中。</span><span class="sxs-lookup"><span data-stu-id="593ea-107">After you complete the tasks in this lesson, you will have created a mining model that uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering algorithm to predict the next item that customers will put into their shopping baskets.</span></span> <span data-ttu-id="593ea-108">您將實驗兩種版本的模型：第一個模型只分析購物籃中的產品順序，而第二個模型另外包含一些用於群集的客戶人口統計資料。</span><span class="sxs-lookup"><span data-stu-id="593ea-108">You will experiment with two versions of the model: one that analyzes only the order of products in the basket, and one that contains some additional customer demographics for clustering.</span></span> <span data-ttu-id="593ea-109">最後，您將使用這些模型來建立預測，以便向客戶提供產品建議。</span><span class="sxs-lookup"><span data-stu-id="593ea-109">Finally, you will use the models to create predictions that you can use to recommend products to customers.</span></span>  
  
 <span data-ttu-id="593ea-110">若要完成課程中的工作，您將使用您在[第3課：建立購物籃案例](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)中所建立的購物籃採礦結構，&#40;中繼資料採礦教學課程&#41;。</span><span class="sxs-lookup"><span data-stu-id="593ea-110">To complete the tasks in the lesson, you will use the market basket mining structure that you created in [Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md).</span></span> <span data-ttu-id="593ea-111">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="593ea-111">This lesson contains the following tasks:</span></span>  
  
-   [<span data-ttu-id="593ea-112">建立時序群集採礦模型結構 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="593ea-112">Creating a Sequence Clustering Mining Model Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
-   [<span data-ttu-id="593ea-113">處理時序群集模型</span><span class="sxs-lookup"><span data-stu-id="593ea-113">Processing the Sequence Clustering Model</span></span>](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
-   [<span data-ttu-id="593ea-114">探索時序群集模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="593ea-114">Exploring the Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="593ea-115">建立相關的時序群集模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="593ea-115">Creating a Related Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="593ea-116">在時序群集模型上建立預測 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="593ea-116">Creating Predictions on a Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="593ea-117">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="593ea-117">Next Task in Lesson</span></span>  
 [<span data-ttu-id="593ea-118">建立時序群集採礦模型結構 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="593ea-118">Creating a Sequence Clustering Mining Model Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-sequence-clustering-mining-model-intermediate-data-mining.md)  
  
## <a name="all-lessons"></a><span data-ttu-id="593ea-119">所有課程</span><span class="sxs-lookup"><span data-stu-id="593ea-119">All Lessons</span></span>  
 [<span data-ttu-id="593ea-120">第1課：建立中繼資料採礦解決方案 &#40;元資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="593ea-120">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="593ea-121">第2課：建立預測案例 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="593ea-121">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="593ea-122">第 3 課：建立購物籃狀況 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="593ea-122">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 <span data-ttu-id="593ea-123">第 4 課：時序群集案例 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="593ea-123">Lesson 4: Sequence Clustering Scenario (Intermediate Data Mining Tutorial)</span></span>  
  
 [<span data-ttu-id="593ea-124">第五課：建立類神經網路和羅吉斯迴歸模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="593ea-124">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="593ea-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="593ea-125">See Also</span></span>  
 <span data-ttu-id="593ea-126">[基本資料採礦教學課程](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="593ea-126">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="593ea-127">元資料採礦教學課程 &#40;Analysis Services-資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="593ea-127">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
