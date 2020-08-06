---
title: 第2課：建立預測案例 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- time series [Analysis Services]
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 9a988156-c900-4c22-97fa-f6b0c1aea9e2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c81d5846df0a37c2b4182cb92fea86ce6f3417a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584919"
---
# <a name="lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial"></a><span data-ttu-id="2dcc9-102">第 2 課：建立預測案例 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="2dcc9-102">Lesson 2: Building a Forecasting Scenario (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="2dcc9-103">您是 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]的銷售分析師，奉命預測下一年度產品的銷售狀況。</span><span class="sxs-lookup"><span data-stu-id="2dcc9-103">As the sales analyst for [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], you have been asked to forecast the sales of products for the next year.</span></span> <span data-ttu-id="2dcc9-104">您特別奉命比較不同區域和產品線的預測狀況。</span><span class="sxs-lookup"><span data-stu-id="2dcc9-104">In particular, you have been asked to compare forecasts for the different regions and product lines.</span></span> <span data-ttu-id="2dcc9-105">另外，您也受要求判斷不同產品的銷售情況是否會隨著年度時段而有所不同。</span><span class="sxs-lookup"><span data-stu-id="2dcc9-105">Additionally, you have been asked to determine whether sales of different products vary depending on the time of the year.</span></span>  
  
 <span data-ttu-id="2dcc9-106">為了找到所要求的資訊，在這個課程中，您將摘要說明公司每月的銷售資料，而且您要依照三個地區摘要這些銷售數字：歐洲、北美和太平洋地區。</span><span class="sxs-lookup"><span data-stu-id="2dcc9-106">To find the requested information, in this lesson you will summarize the company's sales data at the monthly level, and you will also summarize sales figures by three regions: Europe, North America, and the Pacific.</span></span>  
  
 <span data-ttu-id="2dcc9-107">完成這個課程的工作之後，您將能夠回答下列問題：</span><span class="sxs-lookup"><span data-stu-id="2dcc9-107">After you complete the tasks in this lesson, you will be able to answer the following questions:</span></span>  
  
-   <span data-ttu-id="2dcc9-108">不同自行車型號的銷售情況隨著時間改變的情況如何？</span><span class="sxs-lookup"><span data-stu-id="2dcc9-108">How do the sales of different bike models change over time?</span></span>  
  
-   <span data-ttu-id="2dcc9-109">這三個區域的銷售模式之間是否有差異？</span><span class="sxs-lookup"><span data-stu-id="2dcc9-109">Are there differences between the patterns for sales in the three regions?</span></span>  
  
-   <span data-ttu-id="2dcc9-110">是否能夠預測銷售旺季？</span><span class="sxs-lookup"><span data-stu-id="2dcc9-110">Can we forecast sales peaks?</span></span>  
  
 <span data-ttu-id="2dcc9-111">這一課可以分成兩個部分完成：</span><span class="sxs-lookup"><span data-stu-id="2dcc9-111">The lesson can be completed in two parts:</span></span>  
  
-   <span data-ttu-id="2dcc9-112">第一部分介紹如何建立和使用時序模型的基本知識。</span><span class="sxs-lookup"><span data-stu-id="2dcc9-112">Part One introduces the basics of how to create and use a time series model.</span></span>  
  
-   <span data-ttu-id="2dcc9-113">第二部分將逐步引導您依據所有區域建立一般的時間序列模型。</span><span class="sxs-lookup"><span data-stu-id="2dcc9-113">Part Two walks you through creation of a general time series model, based on all regions.</span></span> <span data-ttu-id="2dcc9-114">您可以使用此一般模型進行*交叉預測*。</span><span class="sxs-lookup"><span data-stu-id="2dcc9-114">You can use this general model for *cross-prediction*.</span></span>  
  
 <span data-ttu-id="2dcc9-115">若要完成本課程中所列的工作（如下所示），您將使用在 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] [第1課：建立中繼資料採礦方案 &#40;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)中建立的資料來源，&#41;。</span><span class="sxs-lookup"><span data-stu-id="2dcc9-115">To complete the tasks in this lesson, which are listed below, you will use the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source that you created in [Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md).</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="2dcc9-116">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 範例資料庫中的日期已在此版本中更新。</span><span class="sxs-lookup"><span data-stu-id="2dcc9-116">The dates in the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] sample database have been updated for this release.</span></span> <span data-ttu-id="2dcc9-117">如果您使用舊版 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)]，可以在這些步驟後建立模型，但您可能會看到不同的結果。</span><span class="sxs-lookup"><span data-stu-id="2dcc9-117">If you use an earlier version of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], you can build the model following these steps, but you might see different results.</span></span>  
  
 <span data-ttu-id="2dcc9-118">**建立簡單的預測模型**</span><span class="sxs-lookup"><span data-stu-id="2dcc9-118">**Creating a Simple Forecasting Model**</span></span>  
  
-   [<span data-ttu-id="2dcc9-119">加入資料來源視圖以進行預測 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcc9-119">Adding a Data Source View for Forecasting &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="2dcc9-120">建立預測結構和模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcc9-120">Creating a Forecasting Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-forecasting-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="2dcc9-121">&#40;中繼資料採礦教學課程修改預測結構&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcc9-121">Modifying the Forecasting Structure &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/modifying-the-forecasting-structure-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="2dcc9-122">自訂及處理預測模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcc9-122">Customizing and Processing the Forecasting Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/customize-process-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="2dcc9-123">&#40;中繼資料採礦教學課程中探索預測模型&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcc9-123">Exploring the Forecasting Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-forecasting-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="2dcc9-124">&#40;中繼資料採礦教學課程建立時間序列預測&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcc9-124">Creating Time Series Predictions &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
 <span data-ttu-id="2dcc9-125">**建立一般預測模型以供交叉預測**</span><span class="sxs-lookup"><span data-stu-id="2dcc9-125">**Creating a General Forecasting Model for Cross-Prediction**</span></span>  
  
-   [<span data-ttu-id="2dcc9-126">&#40;中繼資料採礦教學課程的先進時間序列預測&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcc9-126">Advanced Time Series Predictions &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/advanced-time-series-predictions-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="2dcc9-127">使用更新的資料 &#40;中繼資料採礦教學課程的時間序列預測&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcc9-127">Time Series Predictions using Updated Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="2dcc9-128">使用取代資料 &#40;中繼資料採礦教學課程的時間序列預測&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcc9-128">Time Series Predictions using Replacement Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
-   [<span data-ttu-id="2dcc9-129">比較預測模型 &#40;中繼資料採礦教學課程的預測&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcc9-129">Comparing Predictions for Forecasting Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="2dcc9-130">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="2dcc9-130">Next Task in Lesson</span></span>  
 [<span data-ttu-id="2dcc9-131">加入資料來源視圖以進行預測 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcc9-131">Adding a Data Source View for Forecasting &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-a-data-source-view-for-forecasting-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="2dcc9-132">瞭解時間序列模型的需求 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcc9-132">Understanding the Requirements for a Time Series Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-model-requirements-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a><span data-ttu-id="2dcc9-133">所有課程</span><span class="sxs-lookup"><span data-stu-id="2dcc9-133">All Lessons</span></span>  
 [<span data-ttu-id="2dcc9-134">第1課：建立中繼資料採礦解決方案 &#40;元資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcc9-134">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 <span data-ttu-id="2dcc9-135">第 2 課：預測案例 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="2dcc9-135">Lesson 2: Forecasting Scenario (Intermediate Data Mining Tutorial)</span></span>  
  
 [<span data-ttu-id="2dcc9-136">第 3 課：建立購物籃狀況 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcc9-136">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="2dcc9-137">第4課：建立時序群集案例 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcc9-137">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [<span data-ttu-id="2dcc9-138">第五課：建立類神經網路和羅吉斯迴歸模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="2dcc9-138">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="2dcc9-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2dcc9-139">See Also</span></span>  
 <span data-ttu-id="2dcc9-140">[基本資料採礦教學課程](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="2dcc9-140">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 <span data-ttu-id="2dcc9-141">[元資料採礦教學課程 &#40;Analysis Services-資料採礦&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="2dcc9-141">[Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="2dcc9-142">Microsoft 時間序列演算法</span><span class="sxs-lookup"><span data-stu-id="2dcc9-142">Microsoft Time Series Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)  
  
  
