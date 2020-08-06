---
title: 第5課： (基本資料採礦教學課程) 測試模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e9a7ddcf-2b01-485f-bbb5-62638b303bc6
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fcfd9a9e90d9c6800af4dfd1599bbdd62d9520ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703518"
---
# <a name="lesson-5-testing-models-basic-data-mining-tutorial"></a><span data-ttu-id="c2b03-102">第 5 課：測試模型 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="c2b03-102">Lesson 5: Testing Models (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="c2b03-103">現在您已經使用目標郵寄案例定型集處理過模型，所以將會針對測試集來測試模型。</span><span class="sxs-lookup"><span data-stu-id="c2b03-103">Now that you have processed the model by using the targeted mailing scenario training set, you will test your models against the testing set.</span></span> <span data-ttu-id="c2b03-104">驗證是資料採礦程序中的一個重要步驟。</span><span class="sxs-lookup"><span data-stu-id="c2b03-104">Validation is an important step in the data mining process.</span></span> <span data-ttu-id="c2b03-105">將模型部署到實際環境之前，了解目標郵寄採礦模型對實際資料的執行效能有多好是非常重要的事情。</span><span class="sxs-lookup"><span data-stu-id="c2b03-105">Knowing how well your targeted mailing mining models perform against real data is important before you deploy the models into a production environment.</span></span>  
  
 <span data-ttu-id="c2b03-106">由於測試集中的資料已經包含自行車購買的已知值，所以可以輕鬆地判斷模型的預測是否正確。</span><span class="sxs-lookup"><span data-stu-id="c2b03-106">Because the data in the testing set already contains known values for bike buying, it is easy to determine whether the model's predictions are correct.</span></span> <span data-ttu-id="c2b03-107">行銷部門會使用執行最佳的模型 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 來識別其目標郵寄行銷活動的客戶。</span><span class="sxs-lookup"><span data-stu-id="c2b03-107">The model that performs the best will be used by the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] marketing department to identify the customers for their targeted mailing campaign.</span></span>  
  
 <span data-ttu-id="c2b03-108">在這一課，您將使用多種方法來驗證模型：</span><span class="sxs-lookup"><span data-stu-id="c2b03-108">In this lesson you will validate your models using multiple methods:</span></span>  
  
1.  <span data-ttu-id="c2b03-109">您將針對測試集進行預測，以查看模型對已知結果的精確度。</span><span class="sxs-lookup"><span data-stu-id="c2b03-109">You'll make predictions against the testing set to see how accurate the model is on known results.</span></span> <span data-ttu-id="c2b03-110">您將使用增益*圖*來測量其效益。</span><span class="sxs-lookup"><span data-stu-id="c2b03-110">You'll use a *lift chart* to measure its effectiveness.</span></span>  
  
     [<span data-ttu-id="c2b03-111">使用增益圖測試精確度 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="c2b03-111">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
2.  <span data-ttu-id="c2b03-112">您要針對篩選的資料子集測試模型。</span><span class="sxs-lookup"><span data-stu-id="c2b03-112">You will test your models on a filtered subset of the data.</span></span> <span data-ttu-id="c2b03-113">您可以在同一個增益圖中比較多個模型。</span><span class="sxs-lookup"><span data-stu-id="c2b03-113">You can compare multiple models in the same lift chart.</span></span>  
  
     [<span data-ttu-id="c2b03-114">&#40;基本資料採礦教學課程中測試篩選過的模型&#41;</span><span class="sxs-lookup"><span data-stu-id="c2b03-114">Testing a Filtered Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-a-filtered-model-basic-data-mining-tutorial.md)  
  
 <span data-ttu-id="c2b03-115">如需模型驗證的一般詳細資訊，請參閱[資料採礦概念](../../2014/analysis-services/data-mining/data-mining-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="c2b03-115">For more information about how model validation in general, see [Data Mining Concepts](../../2014/analysis-services/data-mining/data-mining-concepts.md).</span></span>  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="c2b03-116">本課程的第一項工作</span><span class="sxs-lookup"><span data-stu-id="c2b03-116">First Task in Lesson</span></span>  
 [<span data-ttu-id="c2b03-117">使用增益圖測試精確度 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="c2b03-117">Testing Accuracy with Lift Charts &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/testing-accuracy-with-lift-charts-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="c2b03-118">上一課</span><span class="sxs-lookup"><span data-stu-id="c2b03-118">Previous Lesson</span></span>  
 [<span data-ttu-id="c2b03-119">第4課：探索目標郵寄模型 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="c2b03-119">Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="c2b03-120">下一課</span><span class="sxs-lookup"><span data-stu-id="c2b03-120">Next Lesson</span></span>  
 [<span data-ttu-id="c2b03-121">第 6 課：建立及處理預測 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="c2b03-121">Lesson 6: Creating and Working with Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="c2b03-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c2b03-122">See Also</span></span>  
 <span data-ttu-id="c2b03-123">[增益圖索引標籤 &#40;&#41;的 [挖掘準確度] 圖表視圖](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md) </span><span class="sxs-lookup"><span data-stu-id="c2b03-123">[Lift Chart Tab &#40;Mining Accuracy Chart View&#41;](../../2014/analysis-services/lift-chart-tab-mining-accuracy-chart-view.md) </span></span>  
 <span data-ttu-id="c2b03-124">[增益圖 &#40;Analysis Services-資料採礦&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c2b03-124">[Lift Chart &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/lift-chart-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="c2b03-125">[測試和驗證 &#40;資料採礦&#41;](../../2014/analysis-services/data-mining/testing-and-validation-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="c2b03-125">[Testing and Validation &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/testing-and-validation-data-mining.md) </span></span>  
 <span data-ttu-id="c2b03-126">[[分類矩陣] 索引標籤 &#40;&#41;的挖掘精確度圖表視圖](../../2014/analysis-services/classification-matrix-tab-mining-accuracy-chart-view.md) </span><span class="sxs-lookup"><span data-stu-id="c2b03-126">[Classification Matrix Tab &#40;Mining Accuracy Chart View&#41;](../../2014/analysis-services/classification-matrix-tab-mining-accuracy-chart-view.md) </span></span>  
 [<span data-ttu-id="c2b03-127">分類矩陣 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="c2b03-127">Classification Matrix &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/classification-matrix-analysis-services-data-mining.md)  
  
  
