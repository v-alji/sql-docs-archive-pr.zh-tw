---
title: 第3課：建立購物籃案例 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data mining [Analysis Services], tutorials
- association algorithms [Analysis Services]
- nested tables
- tutorials [Data Mining]
ms.assetid: 651eef38-772e-4d97-af51-075b1b27fc5a
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a281aa62fbf08393c95f12ded9886ac212b3165f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704462"
---
# <a name="lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial"></a><span data-ttu-id="446dc-102">第 3 課：建立購物籃狀況 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="446dc-102">Lesson 3: Building a Market Basket Scenario (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="446dc-103">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 的行銷部門想改進公司網站，採行交叉銷售 (Cross-selling) 的策略進行促銷。</span><span class="sxs-lookup"><span data-stu-id="446dc-103">The marketing department of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] wants to improve the company Web site to promote cross-selling.</span></span> <span data-ttu-id="446dc-104">在更新網站時，他們想要能夠根據客戶線上購物籃中的其他產品來預測客戶可能會想購買的產品。</span><span class="sxs-lookup"><span data-stu-id="446dc-104">As part of the site update, they would like the ability to predict products that a customer might want to purchase, based on the other products that are already in the customer's online shopping basket.</span></span> <span data-ttu-id="446dc-105">行銷部門也想要更了解客戶的購買行為，讓他們可以設計網站，將客戶想要同時購買的項目放在一起。</span><span class="sxs-lookup"><span data-stu-id="446dc-105">The marketing department also wants to understand customer purchasing behavior better, so that they can design the Web site so that the items that tend to be purchased together appear together.</span></span> <span data-ttu-id="446dc-106">他們了解到資料採礦對於此種類型的 *「購物籃分析」* (Market Basket Analysis) 特別實用，要求您開發資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="446dc-106">They have learned that data mining is especially useful for this kind of *market basket analysis* and have asked you to develop a data mining model.</span></span>  
  
 <span data-ttu-id="446dc-107">當您完成本課程的工作時，將會有一個顯示客戶交易歷程記錄中之產品群組的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="446dc-107">After you complete the tasks in this lesson, you will have a mining model that shows groups of items from historical customer transactions.</span></span> <span data-ttu-id="446dc-108">而且，您可以使用這個採礦模型來預測客戶可能購買的其他產品。</span><span class="sxs-lookup"><span data-stu-id="446dc-108">Additionally, you can use the mining model to predict additional items that a customer may want to purchase.</span></span>  
  
 <span data-ttu-id="446dc-109">若要完成這一課的工作，您將使用在元資料採礦教學課程的第一課中建立的解決方案和資料來源， [&#40;Analysis Services 資料採礦&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="446dc-109">To complete the tasks in this lesson, you will use the solution and data source that you created in the first lesson of the [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).</span></span> <span data-ttu-id="446dc-110">您將加入包含客戶相關資料表 (包括客戶購買記錄的巢狀資料表) 的資料來源檢視，以修改這個方案。</span><span class="sxs-lookup"><span data-stu-id="446dc-110">You will modify this solution by adding a data source view that contains tables about the customer, including a nested table of customer purchases.</span></span>  <span data-ttu-id="446dc-111">接著，您將建立一個採礦模型，使用適用於購物籃狀況的 Microsoft 關聯規則演算法。</span><span class="sxs-lookup"><span data-stu-id="446dc-111">You will then build a mining model that uses the Microsoft Association Rules algorithm, which is suited to market basket scenarios.</span></span>  
  
 <span data-ttu-id="446dc-112">這個課程包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="446dc-112">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="446dc-113">使用嵌套的資料表加入資料來源視圖 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="446dc-113">Adding a Data Source View with Nested Tables &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="446dc-114">建立購物籃結構和模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="446dc-114">Creating a Market Basket Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="446dc-115">修改和處理購物籃模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="446dc-115">Modifying and Processing the Market Basket Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="446dc-116">流覽購物籃模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="446dc-116">Exploring the Market Basket Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="446dc-117">&#40;中繼資料採礦教學課程來篩選模型中的嵌套資料表&#41;</span><span class="sxs-lookup"><span data-stu-id="446dc-117">Filtering a Nested Table in a Mining Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/filtering-a-nested-table-in-a-mining-model-intermediate-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="446dc-118">&#40;中繼資料採礦教學課程來預測關聯&#41;</span><span class="sxs-lookup"><span data-stu-id="446dc-118">Predicting Associations &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/predicting-associations-intermediate-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="446dc-119">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="446dc-119">Next Task in Lesson</span></span>  
 [<span data-ttu-id="446dc-120">使用嵌套的資料表加入資料來源視圖 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="446dc-120">Adding a Data Source View with Nested Tables &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)  
  
## <a name="all-lessons"></a><span data-ttu-id="446dc-121">所有課程</span><span class="sxs-lookup"><span data-stu-id="446dc-121">All Lessons</span></span>  
 [<span data-ttu-id="446dc-122">第1課：建立中繼資料採礦解決方案 &#40;元資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="446dc-122">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
  
 [<span data-ttu-id="446dc-123">第2課：建立預測案例 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="446dc-123">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
  
 <span data-ttu-id="446dc-124">第 3 課：購物籃案例 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="446dc-124">Lesson 3: Market Basket Scenario (Intermediate Data Mining Tutorial)</span></span>  
  
 [<span data-ttu-id="446dc-125">第4課：建立時序群集案例 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="446dc-125">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
 [<span data-ttu-id="446dc-126">第五課：建立類神經網路和羅吉斯迴歸模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="446dc-126">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="446dc-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="446dc-127">See Also</span></span>  
 <span data-ttu-id="446dc-128">[基本資料採礦教學課程](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="446dc-128">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 <span data-ttu-id="446dc-129">[第2課：建立預測案例 &#40;中繼資料採礦教學課程&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="446dc-129">[Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="446dc-130">第4課：建立時序群集案例 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="446dc-130">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
  
  
