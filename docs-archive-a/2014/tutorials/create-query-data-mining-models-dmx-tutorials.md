---
title: 使用 DMX 建立和查詢資料採礦模型：教學課程 (Analysis Services-資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- content queries [DMX]
ms.assetid: 145b81a7-c0c3-4ca3-bb32-0b482423b9a0
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 22ed01105a32f460bcbeb2c067299fdf62af2eed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584207"
---
# <a name="creating-and-querying-data-mining-models-with-dmx-tutorials-analysis-services---data-mining"></a><span data-ttu-id="acc3f-102">使用 DMX 建立並查詢資料採礦模型：教學課程 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="acc3f-102">Creating and Querying Data Mining Models with DMX: Tutorials (Analysis Services - Data Mining)</span></span>
  <span data-ttu-id="acc3f-103">使用建立資料採礦解決方案之後 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，您可以針對資料採礦模型建立查詢來預測趨勢、取得資料中的模式，以及測量採礦模型的精確度。</span><span class="sxs-lookup"><span data-stu-id="acc3f-103">After you have created a data mining solution by using [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], you can create queries against the data mining models to predict trends, retrieve patterns in the data, and measure the accuracy of the mining models.</span></span>  
  
 <span data-ttu-id="acc3f-104">下列清單中的逐步教學課程將協助您瞭解如何使用來建立和執行資料採礦查詢， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 讓您可以充分利用您的資料。</span><span class="sxs-lookup"><span data-stu-id="acc3f-104">The step-by-step tutorials in the following list will help you learn how to build and run data mining queries by using [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] so that you can get the most from your data.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="acc3f-105">本節內容</span><span class="sxs-lookup"><span data-stu-id="acc3f-105">In This Section</span></span>  
  
-   [<span data-ttu-id="acc3f-106">Bike Buyer DMX 教學課程</span><span class="sxs-lookup"><span data-stu-id="acc3f-106">Bike Buyer DMX Tutorial</span></span>](../../2014/tutorials/bike-buyer-dmx-tutorial.md)  
  
     <span data-ttu-id="acc3f-107">本教學課程會引導您使用資料採礦延伸模組 (DMX) 語言建立新的採礦結構與採礦模型，並說明如何建立 DMX 預測查詢。</span><span class="sxs-lookup"><span data-stu-id="acc3f-107">This tutorial walks you through the creation of a new mining structure and mining models by using the Data Mining Extensions (DMX) language, and explains how to create DMX prediction queries.</span></span>  
  
-   [<span data-ttu-id="acc3f-108">購物籃 DMX 教學課程</span><span class="sxs-lookup"><span data-stu-id="acc3f-108">Market Basket DMX Tutorial</span></span>](../../2014/tutorials/market-basket-dmx-tutorial.md)  
  
     <span data-ttu-id="acc3f-109">本教學課程使用一般購物籃案例，您可以在其中找到客戶一起購買之產品間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="acc3f-109">This tutorial uses a typical market basket scenario, where you find associations between the products that customers purchase together.</span></span> <span data-ttu-id="acc3f-110">本教學課程也會示範如何在建立採礦結構時使用巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="acc3f-110">This tutorial also demonstrates how to use nested tables when you create a mining structure.</span></span> <span data-ttu-id="acc3f-111">您可以根據此結構建立並定型模型，然後使用 DMX 建立預測。</span><span class="sxs-lookup"><span data-stu-id="acc3f-111">You build and train a model based on this structure, and then create predictions using DMX.</span></span>  
  
-   [<span data-ttu-id="acc3f-112">時間序列預測 DMX 教學課程</span><span class="sxs-lookup"><span data-stu-id="acc3f-112">Time Series Prediction DMX Tutorial</span></span>](../../2014/tutorials/time-series-prediction-dmx-tutorial.md)  
  
     <span data-ttu-id="acc3f-113">這個教學課程會建立一個預測模型，用於說明 CREATE MODEL (DMX) 陳述式的使用方法。</span><span class="sxs-lookup"><span data-stu-id="acc3f-113">This tutorial creates a forecasting model to illustrate the use of the CREATE MODEL (DMX) statement.</span></span> <span data-ttu-id="acc3f-114">接著您要加入相關模型，並且變更 Microsoft 時間序列演算法的參數以自訂各模型的行為。</span><span class="sxs-lookup"><span data-stu-id="acc3f-114">You then add related models and customize the behavior of each by changing the parameters of the Microsoft Time Series algorithm.</span></span> <span data-ttu-id="acc3f-115">最後，您要建立預測，然後使用新資料更新預測。</span><span class="sxs-lookup"><span data-stu-id="acc3f-115">Finally you create predictions and update the predictions with new data.</span></span> <span data-ttu-id="acc3f-116">在進行預測時更新時間序列這項功能已加入至 [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="acc3f-116">The ability to update a time series while making predictions was added in [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="acc3f-117">參考</span><span class="sxs-lookup"><span data-stu-id="acc3f-117">Reference</span></span>  
 [<span data-ttu-id="acc3f-118">資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="acc3f-118">Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/data-mining-algorithms-analysis-services-data-mining.md)  
  
 [<span data-ttu-id="acc3f-119">資料採礦延伸模組 &#40;DMX&#41; 參考</span><span class="sxs-lookup"><span data-stu-id="acc3f-119">Data Mining Extensions &#40;DMX&#41; Reference</span></span>](/sql/dmx/data-mining-extensions-dmx-reference)  
  
## <a name="related-sections"></a><span data-ttu-id="acc3f-120">相關章節</span><span class="sxs-lookup"><span data-stu-id="acc3f-120">Related Sections</span></span>  
  
-   [<span data-ttu-id="acc3f-121">資料採礦基本教學課程</span><span class="sxs-lookup"><span data-stu-id="acc3f-121">Basic Data Mining Tutorial</span></span>](../../2014/tutorials/basic-data-mining-tutorial.md)  
  
     <span data-ttu-id="acc3f-122">本教學課程介紹基本概念，例如，如何建立專案，以及如何建立採礦結構與採礦模型。</span><span class="sxs-lookup"><span data-stu-id="acc3f-122">This tutorial introduces basic concepts, such as how to create a project and how to build mining structures and mining models.</span></span>  
  
-   [<span data-ttu-id="acc3f-123">元資料採礦教學課程 &#40;Analysis Services-資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="acc3f-123">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
     <span data-ttu-id="acc3f-124">這個教學課程包含一些獨立課程，每一個課程介紹不同的模型類型。</span><span class="sxs-lookup"><span data-stu-id="acc3f-124">This tutorial contains a number of independent lessons, each introducing you to a different model type.</span></span> <span data-ttu-id="acc3f-125">每一個課程都會逐步引導您完成建立模型、探索模型，以及自訂模型並建立預測查詢的程序。</span><span class="sxs-lookup"><span data-stu-id="acc3f-125">Each lesson walks you through the process of creating a model, exploring the model, and then customizing the model and creating prediction queries.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acc3f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="acc3f-126">See Also</span></span>  
 <span data-ttu-id="acc3f-127">[資料採礦解決方案](../../2014/analysis-services/data-mining/data-mining-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="acc3f-127">[Data Mining Solutions](../../2014/analysis-services/data-mining/data-mining-solutions.md) </span></span>  
 <span data-ttu-id="acc3f-128">[資料採礦工具](../../2014/analysis-services/data-mining/data-mining-tools.md) </span><span class="sxs-lookup"><span data-stu-id="acc3f-128">[Data Mining Tools](../../2014/analysis-services/data-mining/data-mining-tools.md) </span></span>  
 [<span data-ttu-id="acc3f-129">資料採礦專案</span><span class="sxs-lookup"><span data-stu-id="acc3f-129">Data Mining Projects</span></span>](../../2014/analysis-services/data-mining/data-mining-projects.md)  
  
  
