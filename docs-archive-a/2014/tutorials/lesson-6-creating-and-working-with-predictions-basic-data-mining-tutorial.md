---
title: 第6課：建立和使用預測 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b213cb58-2c40-4c89-b08b-d3c36a4afad3
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d0a8bfdf83e96622a19ac72490e8602d12afc9df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593713"
---
# <a name="lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial"></a><span data-ttu-id="9406c-102">第 6 課：建立及處理預測 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="9406c-102">Lesson 6: Creating and Working with Predictions (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="9406c-103">您已經定型、測試及瀏覽您所建立的資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="9406c-103">You have trained, tested, and explored the data mining models you created.</span></span> <span data-ttu-id="9406c-104">現在，您可準備開始使用模型來識別最有可能對新的目標郵寄促銷活動做出回應的人。</span><span class="sxs-lookup"><span data-stu-id="9406c-104">Now you are ready to use the models to identify the people most likely to respond to the new targeted mailing campaign.</span></span>  
  
 <span data-ttu-id="9406c-105">在這一課，您將會建立一個查詢來預測哪些客戶最有可能購買自行車。</span><span class="sxs-lookup"><span data-stu-id="9406c-105">In this lesson you will create a query to predict which customers are most likely to purchase a bike.</span></span> <span data-ttu-id="9406c-106">您也會抓取預測*正確的機率*，因此行銷部門可以決定是否可以決定是否要使用預測。</span><span class="sxs-lookup"><span data-stu-id="9406c-106">You will also retrieve the *probability* that the prediction is correct, so the marketing department can decide whether to you can decide whether to use the prediction or not.</span></span>  
  
 <span data-ttu-id="9406c-107">一旦您識別出購買自行車機率很高的客戶之後，您將會鑽研採礦模型中案例的詳細資料，以擷取這些客戶的名稱和連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="9406c-107">Once you have identified customers with a high probability of purchasing a bike, you will drill through to the details of the cases in the mining model to retrieve names and contact information for these customers.</span></span>  
  
 <span data-ttu-id="9406c-108">這個課程包含下列主題：</span><span class="sxs-lookup"><span data-stu-id="9406c-108">This lesson contains the following topics:</span></span>  
  
 [<span data-ttu-id="9406c-109">建立預測 &#40;資料採礦基本教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="9406c-109">Creating Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
 [<span data-ttu-id="9406c-110">在結構資料上使用鑽取 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="9406c-110">Using Drillthrough on Structure Data &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/using-drillthrough-on-structure-data-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="9406c-111">下一課</span><span class="sxs-lookup"><span data-stu-id="9406c-111">Next Lesson</span></span>  
 [<span data-ttu-id="9406c-112">元資料採礦教學課程 &#40;Analysis Services-資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="9406c-112">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="9406c-113">上一課</span><span class="sxs-lookup"><span data-stu-id="9406c-113">Previous Lesson</span></span>  
 [<span data-ttu-id="9406c-114">第5課： &#40;基本資料採礦教學課程來測試模型&#41;</span><span class="sxs-lookup"><span data-stu-id="9406c-114">Lesson 5: Testing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="9406c-115">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="9406c-115">Next Task in Lesson</span></span>  
 [<span data-ttu-id="9406c-116">建立預測 &#40;資料採礦基本教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="9406c-116">Creating Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="9406c-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9406c-117">See Also</span></span>  
 <span data-ttu-id="9406c-118">[&#40;Analysis Services 的決策樹模型的模型內容-資料採礦&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-decision-tree-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="9406c-118">[Mining Model Content for Decision Tree Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-decision-tree-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="9406c-119">使用預測查詢產生器來建立預測查詢</span><span class="sxs-lookup"><span data-stu-id="9406c-119">Create a Prediction Query Using the Prediction Query Builder</span></span>](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
