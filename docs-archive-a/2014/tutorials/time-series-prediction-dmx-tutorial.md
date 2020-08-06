---
title: 時間序列預測 DMX 教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 38ea7c03-4754-4e71-896a-f68cc2c98ce2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fbc9a0640767b3fbae04cebb9a047c2ec2b669b6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592372"
---
# <a name="time-series-prediction-dmx-tutorial"></a><span data-ttu-id="2d4f2-102">時間序列預測 DMX 教學課程</span><span class="sxs-lookup"><span data-stu-id="2d4f2-102">Time Series Prediction DMX Tutorial</span></span>
  <span data-ttu-id="2d4f2-103">在本教學課程中，您將學會如何建立時間序列採礦結構、建立三種自訂時間序列採礦模型，以及使用這些模型建立預測。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-103">In this tutorial, you will learn how to create a time series mining structure, create three custom time series mining models, and then make predictions by using those models.</span></span>  
  
 <span data-ttu-id="2d4f2-104">採礦模型將依據 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 範例資料庫中的資料，該資料庫儲存了虛構公司 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 的資料。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-104">The mining models are based on the data contained in the  [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database, which stores data for the fictitious company [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)].</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="2d4f2-105">是一家大型跨國製造公司。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-105">is a large, multinational manufacturing company.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="2d4f2-106">教學課程案例</span><span class="sxs-lookup"><span data-stu-id="2d4f2-106">Tutorial Scenario</span></span>  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="2d4f2-107">決定使用資料採礦來產生銷售預測。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-107">has decided to use data mining to generate sales projections.</span></span> <span data-ttu-id="2d4f2-108">他們已經建立了一些區域預測模型;如需詳細資訊，請參閱[第2課：建立預測案例 &#40;中繼資料採礦教學課程&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-108">They have already built some regional forecasting models; for more information, see [Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).</span></span> <span data-ttu-id="2d4f2-109">不過，業務部門需要能夠定期以新的銷售資料來更新資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-109">However, the Sales Department needs to be able to periodically update the data mining model with new sales data.</span></span> <span data-ttu-id="2d4f2-110">而且，還要自訂模型以提供不同預測。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-110">They also want to customize the models to provide different projections.</span></span>  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="2d4f2-111">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 提供數個可用來完成這項工作的工具：</span><span class="sxs-lookup"><span data-stu-id="2d4f2-111">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides several tools that can be used to accomplish this task:</span></span>  
  
-   <span data-ttu-id="2d4f2-112">資料採礦延伸模組 (DMX) 查詢語言</span><span class="sxs-lookup"><span data-stu-id="2d4f2-112">The Data Mining Extensions (DMX) query language</span></span>  
  
-   <span data-ttu-id="2d4f2-113">Microsoft 時間序列演算法</span><span class="sxs-lookup"><span data-stu-id="2d4f2-113">The Microsoft Time Series Algorithm</span></span>  
  
-   <span data-ttu-id="2d4f2-114"> 中的查詢編輯器</span><span class="sxs-lookup"><span data-stu-id="2d4f2-114">Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]</span></span>  
  
 <span data-ttu-id="2d4f2-115"> 時間序列演算法所建立的模型，可用來進行與時間相關的資料預測。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-115">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm creates models that can be used for prediction of time-related data.</span></span> <span data-ttu-id="2d4f2-116">資料採礦延伸模組 (DMX) 是 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 提供的一種查詢語言，您可以使用它來建立採礦模型與預測查詢。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-116">Data Mining Extensions (DMX) is a query language provided by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you can use to create mining models and prediction queries.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="2d4f2-117">學習內容</span><span class="sxs-lookup"><span data-stu-id="2d4f2-117">What You Will Learn</span></span>  
 <span data-ttu-id="2d4f2-118">這個教學課程假設您已熟悉 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 用來建立採礦模型的物件。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-118">This tutorial assumes that you are already familiar with the objects that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to create mining models.</span></span> <span data-ttu-id="2d4f2-119">如果您先前未曾使用 DMX 建立了「採礦結構」或「採礦模型」，請參閱[自行車購買者 DMX 教學](../../2014/tutorials/bike-buyer-dmx-tutorial.md)課程。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-119">If you have not previously created a mining structure or mining model by using DMX, see [Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md).</span></span>  
  
 <span data-ttu-id="2d4f2-120">這個教學課程分成下列課程：</span><span class="sxs-lookup"><span data-stu-id="2d4f2-120">This tutorial is divided into the following lessons:</span></span>  
  
 [<span data-ttu-id="2d4f2-121">第 1 課：建立時間序列採礦模型和採礦結構</span><span class="sxs-lookup"><span data-stu-id="2d4f2-121">Lesson 1: Creating a Time Series Mining Model and Mining Structure</span></span>](../../2014/tutorials/lesson-1-creating-a-time-series-mining-model-and-mining-structure.md)  
 <span data-ttu-id="2d4f2-122">在這一課，您將學會如何使用 `CREATE MINING MODEL` 陳述式來新增預測模型及相關聯的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-122">In this lesson, you will learn how to use the `CREATE MINING MODEL` statement to add a new forecasting model and a related mining model.</span></span>  
  
 [<span data-ttu-id="2d4f2-123">第 2 課：將採礦模型新增至時間序列採礦結構</span><span class="sxs-lookup"><span data-stu-id="2d4f2-123">Lesson 2: Adding Mining Models to the Time Series Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
 <span data-ttu-id="2d4f2-124">在這一課，您將學會如何使用 ALTER MINING STRUCTURE 陳述式將新的採礦模型加入至時間序列結構。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-124">In this lesson, you will learn how to use the ALTER MINING STRUCTURE statement to add new mining models to the time series structure.</span></span> <span data-ttu-id="2d4f2-125">此外，您還將學習如何自訂用於分析時間序列的演算法。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-125">You will also learn how to customize the algorithm used for analyzing a time series.</span></span>  
  
 [<span data-ttu-id="2d4f2-126">第 3 課：處理時間序列結構和模型</span><span class="sxs-lookup"><span data-stu-id="2d4f2-126">Lesson 3: Processing the Time Series Structure and Models</span></span>](../../2014/tutorials/lesson-3-processing-the-time-series-structure-and-models.md)  
 <span data-ttu-id="2d4f2-127">在這一課，您將學習如何使用 `INSERT INTO` 陳述式來定型模型，以及用 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 資料庫中的資料來擴展結構。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-127">In this lesson, you will learn how to train the models by using the `INSERT INTO` statement and populating the structure with data from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span>  
  
 [<span data-ttu-id="2d4f2-128">第 4 課：使用 DMX 建立時間序列預測</span><span class="sxs-lookup"><span data-stu-id="2d4f2-128">Lesson 4: Creating Time Series Predictions Using DMX</span></span>](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
 <span data-ttu-id="2d4f2-129">在這一課，您將學習如何建立時間序列預測。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-129">In this lesson, you will learn how to create time series predictions.</span></span>  
  
 [<span data-ttu-id="2d4f2-130">第 5 課：擴充時間序列模型</span><span class="sxs-lookup"><span data-stu-id="2d4f2-130">Lesson 5: Extending the Time Series Model</span></span>](../../2014/tutorials/lesson-5-extending-the-time-series-model.md)  
 <span data-ttu-id="2d4f2-131">在這一課，您將學會如何使用 `EXTEND_MODEL_CASES` 參數，在進行預測時以新資料更新模型。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-131">In this lesson, you will learn how to use the `EXTEND_MODEL_CASES` parameter to update the model with new data when you make predictions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d4f2-132">需求</span><span class="sxs-lookup"><span data-stu-id="2d4f2-132">Requirements</span></span>  
 <span data-ttu-id="2d4f2-133">在執行此教學課程之前，請確定有安裝下列各項：</span><span class="sxs-lookup"><span data-stu-id="2d4f2-133">Before doing this tutorial, make sure that the following are installed:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="2d4f2-134">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d4f2-134">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="2d4f2-135">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d4f2-135">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="2d4f2-136"> 資料庫</span><span class="sxs-lookup"><span data-stu-id="2d4f2-136">The [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database</span></span>  
  
 <span data-ttu-id="2d4f2-137">為了加強安全性，系統預設不會安裝範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-137">By default, the sample databases are not installed, to enhance security.</span></span> <span data-ttu-id="2d4f2-138">若要安裝的正式範例資料庫 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請移至 [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) 或 Microsoft SQL Server 產品範例一節中的 Microsoft SQL Server 範例和 [社區專案] 首頁。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-138">To install the official sample databases for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], go to [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) or on the Microsoft SQL Server Samples and Community Projects home page in the section Microsoft SQL Server Product Samples.</span></span> <span data-ttu-id="2d4f2-139">按一下 [**資料庫**]，然後按一下 [**發行**] 索引標籤，並選取您想要的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-139">Click **Databases**, then click the **Releases** tab and select the databases that you want.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="2d4f2-140">當您查看教學課程時，建議您將 **[下一個主題]** 和 [**上一個主題**] 按鈕新增至 [檔檢視器] 工具列。</span><span class="sxs-lookup"><span data-stu-id="2d4f2-140">When you review tutorials, we recommend that you add **Next topic** and **Previous topic** buttons to the document viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d4f2-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2d4f2-141">See Also</span></span>  
 <span data-ttu-id="2d4f2-142">[基本資料採礦教學課程](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="2d4f2-142">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="2d4f2-143">元資料採礦教學課程 &#40;Analysis Services-資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="2d4f2-143">Intermediate Data Mining Tutorial &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/tutorials/intermediate-data-mining-tutorial-analysis-services-data-mining.md)  
  
  
