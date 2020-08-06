---
title: 基本資料採礦教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- databases [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 6602edb6-d160-43fb-83c8-9df5dddfeb9c
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ed557ffb5b8592be4d4375aca40e461d699d6ba7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704494"
---
# <a name="basic-data-mining-tutorial"></a><span data-ttu-id="67646-102">資料採礦基本教學課程</span><span class="sxs-lookup"><span data-stu-id="67646-102">Basic Data Mining Tutorial</span></span>
  <span data-ttu-id="67646-103">歡迎使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 基本資料採礦教學課程。</span><span class="sxs-lookup"><span data-stu-id="67646-103">Welcome to the [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Basic Data Mining Tutorial.</span></span> [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="67646-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]提供用來建立資料採礦模型和進行預測的整合式環境。</span><span class="sxs-lookup"><span data-stu-id="67646-104">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] provides an integrated environment for creating data mining models and making predictions.</span></span> <span data-ttu-id="67646-105">在本教學課程中，您將完成一個目標郵寄促銷活動案例，以運用機器學習方法來分析和預測客戶購買行為。</span><span class="sxs-lookup"><span data-stu-id="67646-105">In this tutorial, you will complete a scenario for a targeted mailing campaign in which you use machine learning to analyze and predict customer purchasing behavior.</span></span> <span data-ttu-id="67646-106">本教學課程示範如何使用三種最重要的資料採礦演算法：群集、決策樹和貝氏機率分類。</span><span class="sxs-lookup"><span data-stu-id="67646-106">The tutorial demonstrates how to use three of the most important data mining algorithms: clustering, decision trees, and Naive Bayes.</span></span> <span data-ttu-id="67646-107">您也將瞭解如何使用「採礦模型檢視器」來分析您的結果，以及使用所包含的資料採礦工具來建立預測和精確度圖表 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="67646-107">You will also learn how to analyze your findings using the mining model viewers, and to create predictions and accuracy charts using the data mining tools that are included in [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="67646-108">所有範例都以虛構公司 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 為例。</span><span class="sxs-lookup"><span data-stu-id="67646-108">The fictitious company, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)], is used for all examples.</span></span>  
  
 <span data-ttu-id="67646-109">當您習慣使用資料採礦工具時，我們建議您也[&#40;Analysis Services 資料採礦&#41;，完成中繼資料採礦教學](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)課程。</span><span class="sxs-lookup"><span data-stu-id="67646-109">When you are comfortable using the data mining tools, we recommend that you also complete the [Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md).</span></span> <span data-ttu-id="67646-110">其課程示範如何使用預測、購物籃分析、時間序列、關聯模型、巢狀資料表和時序群集。</span><span class="sxs-lookup"><span data-stu-id="67646-110">The lessons demonstrate how to use forecasting, market basket analysis, time series, association models, nested tables, and sequence clustering.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="67646-111">教學課程案例</span><span class="sxs-lookup"><span data-stu-id="67646-111">Tutorial Scenario</span></span>  
 <span data-ttu-id="67646-112">在本教學課程中，您是 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 負責根據採購歷程記錄深入瞭解公司客戶的員工，然後使用該歷程記錄資料來進行可用於行銷的預測。</span><span class="sxs-lookup"><span data-stu-id="67646-112">In this tutorial, you are an employee of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] who has been tasked with learning more about the company's customers based on historical purchases, and then using that historical data to make predictions that can be used in marketing.</span></span> <span data-ttu-id="67646-113">該公司尚未進行過資料採礦，所以您必須特別針對資料採礦建立新的資料庫，並設定數個資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="67646-113">The company has never done data mining before, so you must create a new database specifically for data mining and set up several data mining models.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="67646-114">學習內容</span><span class="sxs-lookup"><span data-stu-id="67646-114">What You Will Learn</span></span>  
 <span data-ttu-id="67646-115">這個教學課程告訴您如何建立與使用幾種不同類型的機器學習方法。</span><span class="sxs-lookup"><span data-stu-id="67646-115">This tutorial teaches you how to create and work with several different types of machine learning methods.</span></span> <span data-ttu-id="67646-116">您也將學習如何建立採礦模型的副本，並對輸入資料套用篩選以取得不同的結果。</span><span class="sxs-lookup"><span data-stu-id="67646-116">You will also learn how to create a copy of a mining model, and apply a filter to the input data to get different results.</span></span> <span data-ttu-id="67646-117">而後，您可以使用增益圖比較這兩個模型的結果。</span><span class="sxs-lookup"><span data-stu-id="67646-117">Afterwards you can compare the results of both models using a lift chart.</span></span> <span data-ttu-id="67646-118">最後，您將使用鑽研功能從基礎採礦結構擷取其他資料。</span><span class="sxs-lookup"><span data-stu-id="67646-118">Finally, you will use drillthrough to retrieve additional data from the underlying mining structure.</span></span>  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="67646-119">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]資料採礦包含下列功能，可協助您輕鬆地開發和比較多個預測模型，然後對結果採取動作：</span><span class="sxs-lookup"><span data-stu-id="67646-119">[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Data Mining includes the following features that help you easily develop and compare multiple predictive models and then take actions on the results :</span></span>  
  
-   <span data-ttu-id="67646-120">*維持的測試集-* 當您建立「採礦結構」時，您現在可以將「採礦結構」中的資料分割成定型集和測試集。</span><span class="sxs-lookup"><span data-stu-id="67646-120">*Holdout Test Sets -* When you create a mining structure, you can now divide the data in the mining structure into training and testing sets.</span></span> <span data-ttu-id="67646-121">這可讓您在類似的資料集上測試模型，以及比較相關模型的精準度。</span><span class="sxs-lookup"><span data-stu-id="67646-121">This lets you test models on similar data sets, and compare the accuracy of related models.</span></span>  
  
-   <span data-ttu-id="67646-122">*採礦模型篩選-* 您現在可以將篩選附加至「採礦模型」，並在定型和測試期間套用篩選。</span><span class="sxs-lookup"><span data-stu-id="67646-122">*Mining model filters -* You can now attach filters to a mining model, and apply the filter during both training and testing.</span></span> <span data-ttu-id="67646-123">這可讓您在不同的資料子集上輕鬆建立相關的模型。</span><span class="sxs-lookup"><span data-stu-id="67646-123">This lets you easily build related models on different subsets of the data.</span></span>  
  
-   <span data-ttu-id="67646-124">*對結構案例和結構資料行的鑽取-* 您現在可以輕鬆地從「採礦模型」中的一般模式移至資料來源中的可操作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="67646-124">*Drillthrough to Structure Cases and Structure Columns -* You can now easily move from the general patterns in the mining model to actionable detail in the data source.</span></span>  
  
 <span data-ttu-id="67646-125">這個教學課程分成下列課程：</span><span class="sxs-lookup"><span data-stu-id="67646-125">This tutorial is divided into the following lessons:</span></span>  
  
 [<span data-ttu-id="67646-126">第1課：準備 Analysis Services 資料庫 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="67646-126">Lesson 1: Preparing the Analysis Services Database &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-1-preparing-the-analysis-services-database-basic-data-mining-tutorial.md)  
 <span data-ttu-id="67646-127">在這個課程中，您將學習如何建立新的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫、加入資料來源和資料來源檢視，以及準備資料採礦要用的新資料庫。</span><span class="sxs-lookup"><span data-stu-id="67646-127">In this lesson, you will learn how to create a new [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, add a data source and data source view, and prepare the new database to be used with data mining.</span></span>  
  
 [<span data-ttu-id="67646-128">第2課：建立目標郵寄結構 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="67646-128">Lesson 2: Building a Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-2-building-a-targeted-mailing-structure-basic-data-mining-tutorial.md)  
 <span data-ttu-id="67646-129">在這一課，您將學習如何建立目標郵寄狀況中所能使用的採礦模型結構。</span><span class="sxs-lookup"><span data-stu-id="67646-129">In this lesson, you will learn how to create a mining model structure that can be used as part of a targeted mailing scenario.</span></span>  
  
 [<span data-ttu-id="67646-130">第 3 課：新增及處理模型</span><span class="sxs-lookup"><span data-stu-id="67646-130">Lesson 3: Adding and Processing Models</span></span>](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
 <span data-ttu-id="67646-131">在這一課，您將學會如何將模型加入到結構中。</span><span class="sxs-lookup"><span data-stu-id="67646-131">In this lesson you will learn how to add models to a structure.</span></span> <span data-ttu-id="67646-132">您建立的模型會使用下列演算法建立：</span><span class="sxs-lookup"><span data-stu-id="67646-132">The models you create are built with the following algorithms:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="67646-133">決策樹</span><span class="sxs-lookup"><span data-stu-id="67646-133">Decision Trees</span></span>  
  
-   <span data-ttu-id="67646-134"> 群集</span><span class="sxs-lookup"><span data-stu-id="67646-134">[!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="67646-135">貝氏機率分類</span><span class="sxs-lookup"><span data-stu-id="67646-135">Naive Bayes</span></span>  
  
 [<span data-ttu-id="67646-136">第4課：探索目標郵寄模型 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="67646-136">Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
 <span data-ttu-id="67646-137">在這一課，您將學會如何使用檢視器探索及解譯各模型的發現。</span><span class="sxs-lookup"><span data-stu-id="67646-137">In this lesson you will learn how to explore and interpret the findings of each model using the Viewers.</span></span>  
  
 [<span data-ttu-id="67646-138">第5課： &#40;基本資料採礦教學課程來測試模型&#41;</span><span class="sxs-lookup"><span data-stu-id="67646-138">Lesson 5: Testing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
 <span data-ttu-id="67646-139">在這一課，您要建立其中一個目標郵寄模型的副本、加入採礦模型篩選以便將定型資料限制在特定一組客戶，然後評估模型的可用性。</span><span class="sxs-lookup"><span data-stu-id="67646-139">In this lesson, you make a copy of one of the targeted mailing models, add a mining model filter to restrict the training data to a particular set of customers, and then assess the viability of the model.</span></span>  
  
 [<span data-ttu-id="67646-140">第 6 課：建立及處理預測 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="67646-140">Lesson 6: Creating and Working with Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-6-creating-and-working-with-predictions-basic-data-mining-tutorial.md)  
 <span data-ttu-id="67646-141">在這基本資料採礦教學課程的最後一課，您將使用模型來預測哪些客戶最有可能購買自行車。</span><span class="sxs-lookup"><span data-stu-id="67646-141">In this final lesson of the Basic Data Mining Tutorial, you use the model to predict which customers are most likely to purchase a bike.</span></span> <span data-ttu-id="67646-142">接著，您要鑽研基礎案例以取得連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="67646-142">You then drill through to the underlying cases to obtain contact information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="67646-143">需求</span><span class="sxs-lookup"><span data-stu-id="67646-143">Requirements</span></span>  
 <span data-ttu-id="67646-144">請確定已安裝下列項目：</span><span class="sxs-lookup"><span data-stu-id="67646-144">Make sure that the following are installed:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="67646-145">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]</span><span class="sxs-lookup"><span data-stu-id="67646-145">[!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="67646-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 在多維度模式中</span><span class="sxs-lookup"><span data-stu-id="67646-146">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] in multidimensional mode</span></span>  
  
-   <span data-ttu-id="67646-147">[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="67646-147">The [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
 <span data-ttu-id="67646-148">為了加強安全性，範例資料庫不會隨著 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 一起安裝。</span><span class="sxs-lookup"><span data-stu-id="67646-148">To enhance security, the sample databases are not installed with [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="67646-149">若要安裝的正式資料庫 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請造訪[Microsoft SQL 範例資料庫](https://go.microsoft.com/fwlink/?LinkId=88417)頁面，並選取 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="67646-149">To install the official databases for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], visit the [Microsoft SQL Sample Databases](https://go.microsoft.com/fwlink/?LinkId=88417) page and select [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)].</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="67646-150">當您進行教學課程時，如果您將 [**下一個主題]** 和 [**上一個主題**] 按鈕新增至 [檔檢視器] 工具列，則可能會更容易在步驟之間來回移動。</span><span class="sxs-lookup"><span data-stu-id="67646-150">When you are working through a tutorial, you might find it easier to move back and forth between the steps if you add the **Next topic** and **Previous topic** buttons to the document viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67646-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67646-151">See Also</span></span>  
 <span data-ttu-id="67646-152">[資料採礦解決方案](../../2014/analysis-services/data-mining/data-mining-solutions.md) </span><span class="sxs-lookup"><span data-stu-id="67646-152">[Data Mining Solutions](../../2014/analysis-services/data-mining/data-mining-solutions.md) </span></span>  
 <span data-ttu-id="67646-153">[採礦模型工作和操作說明](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="67646-153">[Mining Model Tasks and How-tos](../../2014/analysis-services/data-mining/mining-model-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="67646-154">使用 DMX 建立並查詢資料採礦模型：教學課程 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="67646-154">Creating and Querying Data Mining Models with DMX: Tutorials &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/create-query-data-mining-models-dmx-tutorials.md)  
  
  
