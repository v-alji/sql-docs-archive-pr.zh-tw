---
title: 購物籃 DMX 教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DMX [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- statements [DMX], tutorials
- Data Mining Extensions [Analysis Services], tutorials
- market basket analysis [Analysis Services]
- tutorials [Data Mining]
- tutorials [DMX]
ms.assetid: 6e262a1d-c89e-4033-8368-46cf25168ef5
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: fe12f1c4ca1c0946572c61e89f4f4edb8ba9a762
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704450"
---
# <a name="market-basket-dmx-tutorial"></a><span data-ttu-id="1755a-102">購物籃 DMX 教學課程</span><span class="sxs-lookup"><span data-stu-id="1755a-102">Market Basket DMX Tutorial</span></span>
  <span data-ttu-id="1755a-103">您將在此教學課程中學會如何使用資料採礦延伸模組 (DMX) 查詢語言，來建立、定型和探索採礦模型。</span><span class="sxs-lookup"><span data-stu-id="1755a-103">In this tutorial, you will learn how to create, train, and explore mining models by using the Data Mining Extensions (DMX) query language.</span></span> <span data-ttu-id="1755a-104">您將使用這些採礦模型來建立預測，說明哪些產品有可能同時被購買。</span><span class="sxs-lookup"><span data-stu-id="1755a-104">You will then use these mining models to create predictions that describe which products tend to be purchased at the same time.</span></span>  
  
 <span data-ttu-id="1755a-105">這些採礦模型將從 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 範例資料庫中包含的資料來建立，該資料庫儲存了虛構公司 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 的資料。</span><span class="sxs-lookup"><span data-stu-id="1755a-105">The mining models will be created from the data contained in the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database, which stores data for the fictitious company [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)].</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="1755a-106">是一家大型跨國製造公司。</span><span class="sxs-lookup"><span data-stu-id="1755a-106">is a large, multinational manufacturing company.</span></span> <span data-ttu-id="1755a-107">該公司製造金屬類及複合型自行車，並銷售到北美、歐洲及亞洲的商業市場。</span><span class="sxs-lookup"><span data-stu-id="1755a-107">The company manufactures and sells metal and composite bicycles to North American, European, and Asian commercial markets.</span></span> <span data-ttu-id="1755a-108">公司的基地位於美國華盛頓州的 Bothell 市，有 290 位員工，另外還有數個區域銷售團隊，分別位於國際銷售市場所在地。</span><span class="sxs-lookup"><span data-stu-id="1755a-108">Its base operation is located in Bothell, Washington, with 290 employees, and it has several regional sales teams are located throughout their international market base.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="1755a-109">教學課程案例</span><span class="sxs-lookup"><span data-stu-id="1755a-109">Tutorial Scenario</span></span>  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="1755a-110">已決定要建立自訂應用程式，運用資料採礦功能來預測其客戶可能同時購買的產品類型。</span><span class="sxs-lookup"><span data-stu-id="1755a-110">has decided to create a custom application that employs data mining functionality to predict what types of products their customers tend to purchase at the same time.</span></span> <span data-ttu-id="1755a-111">自訂應用程式的目標是要能夠指定一組產品，並預測將與指定的產品一起購買的其他產品有哪些。</span><span class="sxs-lookup"><span data-stu-id="1755a-111">The goal for the custom application is to be able to specify a set of products, and predict what additional products will be purchased with the specified products.</span></span> <span data-ttu-id="1755a-112">然後，[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 將使用此資訊將「建議」功能加入其網站中，並為呈現給其客戶的資訊提供更佳的組織方法。</span><span class="sxs-lookup"><span data-stu-id="1755a-112">[!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] will then use this information to add a "suggest" feature to their website, and also to better organize the way that they present information to their customers.</span></span>  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="1755a-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 提供數個可用來完成這項工作的工具：</span><span class="sxs-lookup"><span data-stu-id="1755a-113">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides several tools that can be used to accomplish this task:</span></span>  
  
-   <span data-ttu-id="1755a-114">DMX 查詢語言</span><span class="sxs-lookup"><span data-stu-id="1755a-114">The DMX query language</span></span>  
  
-   <span data-ttu-id="1755a-115">[Microsoft 關聯分析演算法](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)</span><span class="sxs-lookup"><span data-stu-id="1755a-115">The [Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)</span></span>  
  
-   <span data-ttu-id="1755a-116"> 中的查詢編輯器</span><span class="sxs-lookup"><span data-stu-id="1755a-116">Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]</span></span>  
  
 <span data-ttu-id="1755a-117">資料採礦延伸模組 (DMX) 是 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 提供的一種查詢語言，您可以使用它來建立及處理採礦模型。</span><span class="sxs-lookup"><span data-stu-id="1755a-117">Data Mining Extensions (DMX) is a query language provided by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you can use to create and work with mining models.</span></span> <span data-ttu-id="1755a-118">[!INCLUDE[msCoName](../includes/msconame-md.md)]關聯分析演算法會建立模型來預測可能一起購買的產品。</span><span class="sxs-lookup"><span data-stu-id="1755a-118">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm creates models that can predict the products that are likely to be purchased together.</span></span>  
  
 <span data-ttu-id="1755a-119">此教學課程的目標是要提供將用於自訂應用程式的 DMX 查詢。</span><span class="sxs-lookup"><span data-stu-id="1755a-119">The goal of this tutorial is to provide the DMX queries that will be used in the custom application.</span></span>  
  
 <span data-ttu-id="1755a-120">**如需詳細資訊：** [資料採礦解決方案](../../2014/analysis-services/data-mining/data-mining-solutions.md)</span><span class="sxs-lookup"><span data-stu-id="1755a-120">**For more information:** [Data Mining Solutions](../../2014/analysis-services/data-mining/data-mining-solutions.md)</span></span>  
  
## <a name="mining-structure-and-mining-models"></a><span data-ttu-id="1755a-121">採礦結構和採礦模型</span><span class="sxs-lookup"><span data-stu-id="1755a-121">Mining Structure and Mining Models</span></span>  
 <span data-ttu-id="1755a-122">開始建立 DMX 陳述式之前，一定要先了解 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 用來建立採礦模型的主要物件。</span><span class="sxs-lookup"><span data-stu-id="1755a-122">Before you begin to create DMX statements, it is important to understand the main objects that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to create mining models.</span></span> <span data-ttu-id="1755a-123">「*採礦結構*」是一種資料結構，可定義用來建立採礦模型的資料網域。</span><span class="sxs-lookup"><span data-stu-id="1755a-123">The *mining structure* is a data structure that defines the data domain from which mining models are built.</span></span> <span data-ttu-id="1755a-124">單一的採礦結構可以包含多個共用相同網域的*採礦模型*。</span><span class="sxs-lookup"><span data-stu-id="1755a-124">A single mining structure can contain multiple *mining models* that share the same domain.</span></span> <span data-ttu-id="1755a-125">採礦模型會將採礦模型演算法套用至以採礦結構表示的資料。</span><span class="sxs-lookup"><span data-stu-id="1755a-125">A mining model applies a mining model algorithm to the data, which is represented by a mining structure.</span></span>  
  
 <span data-ttu-id="1755a-126">採礦結構的建置組塊是採礦結構資料行，它們會描述資料來源包含的資料。</span><span class="sxs-lookup"><span data-stu-id="1755a-126">The building blocks of the mining structure are the mining structure columns, which describe the data that the data source contains.</span></span> <span data-ttu-id="1755a-127">這些資料行包含如資料類型、內容類型和資料散發方式等資訊。</span><span class="sxs-lookup"><span data-stu-id="1755a-127">These columns contain information such as data type, content type, and how the data is distributed.</span></span>  
  
 <span data-ttu-id="1755a-128">採礦模型必須包含採礦結構所描述的索引鍵資料行，以及剩餘資料行的子集。</span><span class="sxs-lookup"><span data-stu-id="1755a-128">Mining models must contain the key column described in the mining structure, as well as a subset of the remaining columns.</span></span> <span data-ttu-id="1755a-129">採礦模型定義每一個資料行的使用方式，以及定義用來建立採礦模型的演算法。</span><span class="sxs-lookup"><span data-stu-id="1755a-129">The mining model defines the usage for each column and defines the algorithm that is used to create the mining model.</span></span> <span data-ttu-id="1755a-130">例如，在 DMX 中，您可以指定資料行為索引鍵資料行或 PREDICT 資料行。</span><span class="sxs-lookup"><span data-stu-id="1755a-130">For example, in DMX you can specify that a column is a Key column or a PREDICT column.</span></span> <span data-ttu-id="1755a-131">如果未指定資料行，則假設它是輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="1755a-131">If a column is left unspecified, it is assumed to be an input column.</span></span>  
  
 <span data-ttu-id="1755a-132">在 DMX 中，有兩種方式建立採礦模型。</span><span class="sxs-lookup"><span data-stu-id="1755a-132">In DMX, there are two ways to create mining models.</span></span> <span data-ttu-id="1755a-133">您可以使用 `CREATE MINING MODEL` 陳述式來同時建立採礦結構和相關聯的採礦模型，也可以先使用 `CREATE MINING STRUCTURE` 陳述式來建立採礦結構，然後使用 `ALTER STRUCTURE` 陳述式，將採礦模型加入至結構。</span><span class="sxs-lookup"><span data-stu-id="1755a-133">You can either create the mining structure and associated mining model together by using the `CREATE MINING MODEL` statement, or you can first create a mining structure by using the `CREATE MINING STRUCTURE` statement, and then add a mining model to the structure by using the `ALTER STRUCTURE` statement.</span></span> <span data-ttu-id="1755a-134">以下將描述這些方法。</span><span class="sxs-lookup"><span data-stu-id="1755a-134">These methods are described below.</span></span>  
  
 `CREATE MINING MODEL`  
 <span data-ttu-id="1755a-135">使用此陳述式可同時建立使用相同名稱的採礦結構和相關聯的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="1755a-135">Use this statement to create a mining structure and associated mining model together using the same name.</span></span> <span data-ttu-id="1755a-136">採礦模型名稱後面會加上 "Structure"，以便與採礦結構區別。</span><span class="sxs-lookup"><span data-stu-id="1755a-136">The mining model name is appended with "Structure" to differentiate it from the mining structure.</span></span>  
  
 <span data-ttu-id="1755a-137">如果您要建立包含單一採礦模型的採礦結構，則此陳述式很有幫助。</span><span class="sxs-lookup"><span data-stu-id="1755a-137">This statement is useful if you are creating a mining structure that will contain a single mining model.</span></span>  
  
 <span data-ttu-id="1755a-138">如需詳細資訊，請參閱 [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx)。</span><span class="sxs-lookup"><span data-stu-id="1755a-138">For more information, see [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).</span></span>  
  
 <span data-ttu-id="1755a-139">CREATE MINING STRUCTURE</span><span class="sxs-lookup"><span data-stu-id="1755a-139">CREATE MINING STRUCTURE</span></span>  
 <span data-ttu-id="1755a-140">使用這個陳述式可建立新的採礦結構而不使用任何模型。</span><span class="sxs-lookup"><span data-stu-id="1755a-140">Use this statement to create a new mining structure without any models.</span></span>  
  
 <span data-ttu-id="1755a-141">當您使用 CREATE MINING STRUCTURE 時，您也可以建立鑑效組資料集，該資料集可用來測試以相同採礦結構為根據的任何模型。</span><span class="sxs-lookup"><span data-stu-id="1755a-141">When you use CREATE MINING STRUCTURE, you can also create a holdout data set that can be used for testing any models that are based on the same mining structure.</span></span>  
  
 <span data-ttu-id="1755a-142">如需詳細資訊，請參閱 [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx)。</span><span class="sxs-lookup"><span data-stu-id="1755a-142">For more information, see [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx).</span></span>  
  
 `ALTER MINING STRUCTURE`  
 <span data-ttu-id="1755a-143">使用此陳述式將採礦模型加入已存在於伺服器上的採礦結構中。</span><span class="sxs-lookup"><span data-stu-id="1755a-143">Use this statement to add a mining model to a mining structure that already exists on the server.</span></span>  
  
 <span data-ttu-id="1755a-144">您要在單一採礦結構中加入不止一個採礦模型，有幾個原因。</span><span class="sxs-lookup"><span data-stu-id="1755a-144">There are several reasons that you would want to add more than one mining model in a single mining structure.</span></span> <span data-ttu-id="1755a-145">例如，您可以使用不同演算法來建立數個採礦模型，看看哪一個最好用。</span><span class="sxs-lookup"><span data-stu-id="1755a-145">For example, you might create several mining models using different algorithms to see which one works best.</span></span> <span data-ttu-id="1755a-146">或者，您也可以建立數個使用相同演算法的採礦模型，但每一個採礦模型要設定不同的參數，以找出該參數的最佳設定。</span><span class="sxs-lookup"><span data-stu-id="1755a-146">Alternatively, you might create several mining models using the same algorithm, but with a parameter set differently for each mining model to find the best setting for that parameter.</span></span>  
  
 <span data-ttu-id="1755a-147">如需詳細資訊，請參閱[ALTER &#40;DMX&#41;的採礦結構](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016)。</span><span class="sxs-lookup"><span data-stu-id="1755a-147">For more information, see [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016).</span></span>  
  
 <span data-ttu-id="1755a-148">因為您要建立包含數個採礦模型的採礦結構，所以您將使用此教學課程的第二個方法。</span><span class="sxs-lookup"><span data-stu-id="1755a-148">Because you will create a mining structure that contains several mining models, you will use the second method in this tutorial.</span></span>  
  
 <span data-ttu-id="1755a-149">**詳細資訊**</span><span class="sxs-lookup"><span data-stu-id="1755a-149">**For More Information**</span></span>  
  
 <span data-ttu-id="1755a-150">[資料採礦延伸模組 &#40;dmx&#41; 參考](/sql/dmx/data-mining-extensions-dmx-reference)，瞭解 Dmx 預測查詢[的 dmx Select 語句](/sql/dmx/understanding-the-dmx-select-statement)、[結構和使用](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)方式</span><span class="sxs-lookup"><span data-stu-id="1755a-150">[Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference), [Understanding the DMX Select Statement](/sql/dmx/understanding-the-dmx-select-statement), [Structure and Usage of DMX Prediction Queries](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="1755a-151">學習內容</span><span class="sxs-lookup"><span data-stu-id="1755a-151">What You Will Learn</span></span>  
 <span data-ttu-id="1755a-152">這個教學課程分成下列課程：</span><span class="sxs-lookup"><span data-stu-id="1755a-152">This tutorial is divided into the following lessons:</span></span>  
  
 [<span data-ttu-id="1755a-153">第 1 課：建立購物籃採礦結構</span><span class="sxs-lookup"><span data-stu-id="1755a-153">Lesson 1: Creating the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md)  
 <span data-ttu-id="1755a-154">在這一課，您將學會如何使用 `CREATE` 陳述式來建立採礦結構。</span><span class="sxs-lookup"><span data-stu-id="1755a-154">In this lesson, you will learn how to use the `CREATE` statement to create mining structures.</span></span>  
  
 [<span data-ttu-id="1755a-155">第 2 課：將採礦模型新增至購物籃採礦結構</span><span class="sxs-lookup"><span data-stu-id="1755a-155">Lesson 2: Adding Mining Models to the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
 <span data-ttu-id="1755a-156">在這一課，您將學會如何使用 `ALTER` 陳述式將採礦模型加入至採礦結構。</span><span class="sxs-lookup"><span data-stu-id="1755a-156">In this lesson, you will learn how to use the `ALTER` statement to add mining models to a mining structure.</span></span>  
  
 [<span data-ttu-id="1755a-157">第 3 課：處理購物籃採礦結構</span><span class="sxs-lookup"><span data-stu-id="1755a-157">Lesson 3: Processing the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-3-processing-the-market-basket-mining-structure.md)  
 <span data-ttu-id="1755a-158">在這一課，您將學會如何使用 `INSERT INTO` 陳述式來處理採礦結構及其相關聯的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="1755a-158">In this lesson, you will learn how to use the `INSERT INTO` statement to process mining structures and their associated mining models.</span></span>  
  
 [<span data-ttu-id="1755a-159">第 4 課：執行購物籃預測</span><span class="sxs-lookup"><span data-stu-id="1755a-159">Lesson 4: Executing Market Basket Predictions</span></span>](../../2014/tutorials/lesson-4-executing-market-basket-predictions.md)  
 <span data-ttu-id="1755a-160">在這一課，您將學會如何使用 `PREDICTION JOIN` 陳述式來建立採礦模型的預測。</span><span class="sxs-lookup"><span data-stu-id="1755a-160">In this lesson, you will learn how to use the `PREDICTION JOIN` statement to create predictions against mining models.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1755a-161">需求</span><span class="sxs-lookup"><span data-stu-id="1755a-161">Requirements</span></span>  
 <span data-ttu-id="1755a-162">在執行此教學課程之前，請確定有安裝下列各項：</span><span class="sxs-lookup"><span data-stu-id="1755a-162">Before doing this tutorial, make sure that the following are installed:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="1755a-163">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1755a-163">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="1755a-164">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1755a-164">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="1755a-165"> 資料庫</span><span class="sxs-lookup"><span data-stu-id="1755a-165">The [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database</span></span>  
  
 <span data-ttu-id="1755a-166">為了加強安全性，系統預設不會安裝範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="1755a-166">By default, the sample databases are not installed, to enhance security.</span></span> <span data-ttu-id="1755a-167">若要安裝的正式範例資料庫 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請移至 [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) 或 Microsoft SQL Server 產品範例一節中的 Microsoft SQL Server 範例和 [社區專案] 首頁。</span><span class="sxs-lookup"><span data-stu-id="1755a-167">To install the official sample databases for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], go to [http://www.CodePlex.com/MSFTDBProdSamples](https://go.microsoft.com/fwlink/?LinkId=88417) or on the Microsoft SQL Server Samples and Community Projects home page in the section Microsoft SQL Server Product Samples.</span></span> <span data-ttu-id="1755a-168">按一下 [**資料庫**]，然後按一下 [**發行**] 索引標籤，並選取您想要的資料庫。</span><span class="sxs-lookup"><span data-stu-id="1755a-168">Click **Databases**, then click the **Releases** tab and select the databases that you want.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1755a-169">當您查看教學課程時，建議您將 **[下一個主題]** 和 [**上一個主題**] 按鈕新增至 [檔檢視器] 工具列。</span><span class="sxs-lookup"><span data-stu-id="1755a-169">When you review tutorials, we recommend that you add **Next topic** and **Previous topic** buttons to the document viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1755a-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1755a-170">See Also</span></span>  
 <span data-ttu-id="1755a-171">[自行車購買者 DMX 教學課程](../../2014/tutorials/bike-buyer-dmx-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="1755a-171">[Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md) </span></span>  
 <span data-ttu-id="1755a-172">[基本資料採礦教學課程](../../2014/tutorials/basic-data-mining-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="1755a-172">[Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md) </span></span>  
 [<span data-ttu-id="1755a-173">第 3 課：建立購物籃狀況 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="1755a-173">Lesson 3: Building a Market Basket Scenario &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-3-building-a-market-basket-scenario-intermediate-data-mining-tutorial.md)  
  
  
