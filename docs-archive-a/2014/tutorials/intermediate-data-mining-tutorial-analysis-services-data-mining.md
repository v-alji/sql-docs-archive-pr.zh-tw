---
title: 元資料採礦教學課程 (Analysis Services-資料採礦) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 404b31d5-27f4-4875-bd60-7b2b8613eb1b
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 090bcd8cc987da57a5c4bdf27e6782ae07b85719
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592407"
---
# <a name="intermediate-data-mining-tutorial-analysis-services---data-mining"></a><span data-ttu-id="72573-102">中繼資料採礦教學課程 (Analysis Services - 資料採礦)</span><span class="sxs-lookup"><span data-stu-id="72573-102">Intermediate Data Mining Tutorial (Analysis Services - Data Mining)</span></span>
  [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="72573-103">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]提供用來建立和使用資料採礦模型的整合式環境。</span><span class="sxs-lookup"><span data-stu-id="72573-103">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides an integrated environment for creating and working with data mining models.</span></span> <span data-ttu-id="72573-104">您可以輕易地繫結資料來源、以相同資料建立及測試多個模型，以及部署模型以供預測分析。</span><span class="sxs-lookup"><span data-stu-id="72573-104">You can easily bind to data sources, create and test multiple models on the same data, and deploy models for use in predictive analysis.</span></span>  
  
 <span data-ttu-id="72573-105">在基本資料採礦教學課程中，您學會了如何使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 建立資料採礦方案，並且建立了三個模型來支援目標郵寄行銷資料，以供分析客戶購買行為與目標潛在購買者。</span><span class="sxs-lookup"><span data-stu-id="72573-105">In the Basic Data Mining Tutorial, you learned how to use [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create a data mining solution, and you built three models to support a targeted mailing campaign for analyzing customer purchasing behavior and for targeting potential buyers.</span></span>  
  
 <span data-ttu-id="72573-106">這個中繼教學課程會進一步運用這些工具，並且介紹許多新狀況，包括像是預測和購物籃分析等常見的商業需求。</span><span class="sxs-lookup"><span data-stu-id="72573-106">This intermediate tutorial builds on that experience and introduces several new scenarios, including common business requirements such as forecasting and market basket analysis.</span></span> <span data-ttu-id="72573-107">您將學習如何建立時間序列模型、關聯模型以及時序群集模型。</span><span class="sxs-lookup"><span data-stu-id="72573-107">You will learn how to create a time series model, an association model, and a sequence clustering model.</span></span> <span data-ttu-id="72573-108">最後，您將學習如何使用類神經網路探索資料的相關性，以及使用羅吉斯迴歸進行預測。</span><span class="sxs-lookup"><span data-stu-id="72573-108">Finally, you will learn how to use neural network to explore correlations in data and to use logistic regression for predictions.</span></span>  
  
 <span data-ttu-id="72573-109">這些課程都是獨立的，而且可以分開完成。</span><span class="sxs-lookup"><span data-stu-id="72573-109">The lessons are independent and can be completed separately.</span></span>  
  
 <span data-ttu-id="72573-110">若要完成下列教學課程，您應該熟悉在基本資料採礦教學課程中介紹的資料採礦工具與採礦模型檢視器。</span><span class="sxs-lookup"><span data-stu-id="72573-110">To complete the following tutorials, you should to be familiar with the data mining tools and with the mining model viewers that were introduced in the Basic Data Mining Tutorial.</span></span>  
  
 <span data-ttu-id="72573-111">所有狀況都使用 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 資料來源，不過您需要為不同的狀況建立不同的資料來源。</span><span class="sxs-lookup"><span data-stu-id="72573-111">All scenarios use the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source, but you will create different data source views for different scenarios.</span></span> <span data-ttu-id="72573-112">只要先建立資料來源，就可以依任何順序進行課程。</span><span class="sxs-lookup"><span data-stu-id="72573-112">You can do the lessons in any order as long as you create the data source first.</span></span>  
  
## <a name="lesson-scenarios"></a><span data-ttu-id="72573-113">課程狀況</span><span class="sxs-lookup"><span data-stu-id="72573-113">Lesson Scenarios</span></span>  
 <span data-ttu-id="72573-114">當您成功完成目標郵寄行銷資料後，接著要運用您的資料採礦知識，開發數種新模型以便用於商務計畫。</span><span class="sxs-lookup"><span data-stu-id="72573-114">After your success with the targeted mailing campaign, you have been asked to apply your knowledge of data mining to develop several new models for use in business planning.</span></span> <span data-ttu-id="72573-115">這些包括下列工作：</span><span class="sxs-lookup"><span data-stu-id="72573-115">These include the following tasks:</span></span>  
  
-   <span data-ttu-id="72573-116">**預測：** 您將會建立*時間序列*模型，以預測全球不同區域的產品銷售。</span><span class="sxs-lookup"><span data-stu-id="72573-116">**Forecasting:** You will create a *time series* model, to forecast the sales of products in different regions around the world.</span></span> <span data-ttu-id="72573-117">您將為每個區域開發個別的模型，並瞭解如何使用*交叉預測*。</span><span class="sxs-lookup"><span data-stu-id="72573-117">You will develop individual models for each region and learn how to use *cross-prediction*.</span></span>  
  
-   <span data-ttu-id="72573-118">**購物籃分析：** 您將建立*關聯模型*，以分析造訪電子商務網站時所購買的產品群組 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="72573-118">**Market basket analysis:** You will create an *association model*, to analyze groupings of products that are purchased during visits to the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] e-commerce site.</span></span> <span data-ttu-id="72573-119">您可以根據這個購物籃模型向客戶提供產品建議。</span><span class="sxs-lookup"><span data-stu-id="72573-119">Based on this market basket model, you can recommend products to customers.</span></span>  
  
-   <span data-ttu-id="72573-120">**順序分析：** 您會建立時序*群集模型*，以分析客戶購買產品的順序。</span><span class="sxs-lookup"><span data-stu-id="72573-120">**Sequence analysis:** You build a *sequence clustering model*, to analyze the order in which customers buy products.</span></span> <span data-ttu-id="72573-121">您可以根據這個模型，計畫網站設計變更或規劃新產品供應項目。</span><span class="sxs-lookup"><span data-stu-id="72573-121">Based on this model, you can plan changes in Web site design or new product offerings.</span></span>  
  
-   <span data-ttu-id="72573-122">**因素分析：** 您可以使用類*神經網路*模型，在撥接中心資料中探索服務品質不佳的可能原因。</span><span class="sxs-lookup"><span data-stu-id="72573-122">**Factor analysis:** You use a *neural network* model to explore the possible causes of poor service quality in call center data.</span></span> <span data-ttu-id="72573-123">根據初步模型的見解，您將建立*羅吉斯回歸模型*，以預測改善客戶經驗的策略。</span><span class="sxs-lookup"><span data-stu-id="72573-123">Based on the insights from the preliminary model, you will create a *logistic regression model* to predict strategies for improving customer experience.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="72573-124">學習內容</span><span class="sxs-lookup"><span data-stu-id="72573-124">What You Will Learn</span></span>  
 <span data-ttu-id="72573-125">這個教學課程告訴您如何建立和使用各種類型的資料採礦演算法。</span><span class="sxs-lookup"><span data-stu-id="72573-125">This tutorial teaches you how to create and work with several types of data mining algorithms.</span></span> <span data-ttu-id="72573-126">這個教學課程分成下列課程：</span><span class="sxs-lookup"><span data-stu-id="72573-126">This tutorial is divided into the following lessons:</span></span>  
  
 [<span data-ttu-id="72573-127">第1課：建立中繼資料採礦解決方案 &#40;元資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="72573-127">Lesson 1: Creating the Intermediate Data Mining Solution &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-create-solution-intermediate-data-mining-tutorial.md)  
 <span data-ttu-id="72573-128">在這一課，您將根據 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 資料庫建立新專案，以便支援多個新資料來源檢視和更多的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="72573-128">In this lesson, you will create a new project based on the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database, to support several new data sources views and many more mining models.</span></span>  
  
 [<span data-ttu-id="72573-129">第2課：建立預測案例 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="72573-129">Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)  
 <span data-ttu-id="72573-130">在這個課程中，您將建立預測狀況中所能使用的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="72573-130">In this lesson, you will create a mining model that can be used as part of a forecasting scenario.</span></span> <span data-ttu-id="72573-131">另外，您還將探索 [!INCLUDE[msCoName](../includes/msconame-md.md)] 時間序列演算法建立的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="72573-131">You will also explore mining models that are built with the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm.</span></span>  
  
 <span data-ttu-id="72573-132">您將為各區域建立個別的模型，然後建立一個用來交叉預測的一般模型。</span><span class="sxs-lookup"><span data-stu-id="72573-132">You will build models for individual regions, and then build a general model that can be used for cross-prediction.</span></span>  
  
 [<span data-ttu-id="72573-133">第 3 課：建立購物籃狀況 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="72573-133">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
 <span data-ttu-id="72573-134">在這個課程中，您將加入新的資料來源檢視，並學習如何使用巢狀資料表與索引鍵。</span><span class="sxs-lookup"><span data-stu-id="72573-134">In this lesson, you will add a new data source view and learn how to work with nested tables and keys.</span></span> <span data-ttu-id="72573-135">根據這項資料，您將建立購物籃狀況中所能使用的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="72573-135">Based on this data, you will create a mining model that can be used as part of a market basket scenario.</span></span> <span data-ttu-id="72573-136">此外，您還將探索 [!INCLUDE[msCoName](../includes/msconame-md.md)] 關聯分析演算法建立的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="72573-136">You will also explore mining models that are built with the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm.</span></span>  
  
 [<span data-ttu-id="72573-137">第4課：建立時序群集案例 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="72573-137">Lesson 4: Building a Sequence Clustering Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-build-sequence-clustering-scenario-intermediate-data-mining.md)  
 <span data-ttu-id="72573-138">在這個課程中，您將建立時序群集狀況中所能使用的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="72573-138">In this lesson, you will create a mining model that can be used as part of a sequence clustering scenario.</span></span> <span data-ttu-id="72573-139">另外，您也將學習如何探索 [!INCLUDE[msCoName](../includes/msconame-md.md)] 時序群集演算法所建立的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="72573-139">You will also learn how to explore mining models that are built with the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span>  
  
 [<span data-ttu-id="72573-140">第五課：建立類神經網路和羅吉斯迴歸模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="72573-140">Lesson 5: Building Neural Network and Logistic Regression Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-build-models-intermediate-data-mining-tutorial.md)  
 <span data-ttu-id="72573-141">在這一課，您將使用 Microsoft 類神經網路演算法和 Microsoft 羅吉斯迴歸演算法，建立數個相關的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="72573-141">In this lesson, you will create several related mining models, using the Microsoft Neural Network and Microsoft Logistic Regression algorithms.</span></span> <span data-ttu-id="72573-142">另外，您也將學習如何使用資料來源檢視探索模型的基礎資料。</span><span class="sxs-lookup"><span data-stu-id="72573-142">You will also learn to work with data source views to explore data underlying the models.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72573-143">需求</span><span class="sxs-lookup"><span data-stu-id="72573-143">Requirements</span></span>  
 <span data-ttu-id="72573-144">請確定已安裝下列項目：</span><span class="sxs-lookup"><span data-stu-id="72573-144">Make sure that the following are installed:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="72573-145">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72573-145">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="72573-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72573-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span></span>  
  
-   [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] <span data-ttu-id="72573-147">與 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="72573-147">with the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="72573-148">為了加強安全性，系統預設不會安裝範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="72573-148">By default, the sample databases are not installed, to enhance security.</span></span> <span data-ttu-id="72573-149">若要安裝的正式資料庫 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請造訪[Microsoft SQL 範例資料庫](https://go.microsoft.com/fwlink/?LinkId=88417)頁面，並選取適當版本的範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="72573-149">To install the official databases for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], visit the [Microsoft SQL Sample Databases](https://go.microsoft.com/fwlink/?LinkId=88417) page and select the appropriate version of the sample database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72573-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="72573-150">See Also</span></span>  
 <span data-ttu-id="72573-151">[基本資料採礦教學課程](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="72573-151">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 <span data-ttu-id="72573-152">[自行車購買者 DMX 教學課程](../../2014/tutorials/bike-buyer-dmx-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="72573-152">[Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md) </span></span>  
 [<span data-ttu-id="72573-153">購物籃 DMX 教學課程</span><span class="sxs-lookup"><span data-stu-id="72573-153">Market Basket DMX Tutorial</span></span>](../../2014/tutorials/market-basket-dmx-tutorial.md)  
  
  
