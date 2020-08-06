---
title: 自行車購買者 DMX 教學課程 |Microsoft Docs
ms.custom: ''
ms.date: 10/19/2018
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- DMX [Analysis Services], tutorials
- data mining [Analysis Services], tutorials
- statements [DMX], tutorials
- Data Mining Extensions [Analysis Services], tutorials
- tutorials [Data Mining]
ms.assetid: 4b634cc1-86dc-42ec-9804-a19292fe8448
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3cf9a0c9e6059330c0b8edbd8228f617ba093564
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704490"
---
# <a name="bike-buyer-dmx-tutorial"></a><span data-ttu-id="f21d0-102">Bike Buyer DMX 教學課程</span><span class="sxs-lookup"><span data-stu-id="f21d0-102">Bike Buyer DMX Tutorial</span></span>
  <span data-ttu-id="f21d0-103">您將在此教學課程中學會如何使用資料採礦延伸模組 (DMX) 查詢語言，來建立、培訓和探索採礦模型。</span><span class="sxs-lookup"><span data-stu-id="f21d0-103">In this tutorial, you will learn how create, train, and explore mining models by using the Data Mining Extensions (DMX) query language.</span></span> <span data-ttu-id="f21d0-104">您將使用這些採礦模型來建立預測，以判斷客戶是否要購買自行車。</span><span class="sxs-lookup"><span data-stu-id="f21d0-104">You will then use these mining models to create predictions that determine whether a customer will purchase a bicycle.</span></span>  
  
 <span data-ttu-id="f21d0-105">這些採礦模型將從 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 範例資料庫中包含的資料來建立，該資料庫儲存了虛構公司 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 的資料。</span><span class="sxs-lookup"><span data-stu-id="f21d0-105">The mining models will be created from the data contained in the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database, which stores data for the fictitious company [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)].</span></span> [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="f21d0-106">是一家大型跨國製造公司。</span><span class="sxs-lookup"><span data-stu-id="f21d0-106">is a large, multinational manufacturing company.</span></span> <span data-ttu-id="f21d0-107">該公司製造金屬類及複合型自行車，並銷售到北美、歐洲及亞洲的商業市場。</span><span class="sxs-lookup"><span data-stu-id="f21d0-107">The company manufactures and sells metal and composite bicycles to North American, European, and Asian commercial markets.</span></span> <span data-ttu-id="f21d0-108">公司的基地位於美國華盛頓州的 Bothell 市，有 290 位員工，另外還有數個區域銷售團隊，分別位於國際銷售市場所在地。</span><span class="sxs-lookup"><span data-stu-id="f21d0-108">Its base operation is located in Bothell, Washington, with 290 employees, and it has several regional sales teams located throughout their international market base.</span></span>  
  
## <a name="tutorial-scenario"></a><span data-ttu-id="f21d0-109">教學課程案例</span><span class="sxs-lookup"><span data-stu-id="f21d0-109">Tutorial Scenario</span></span>  
 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] <span data-ttu-id="f21d0-110">決定要建立自訂應用程式，使用資料採礦功能來擴大其資料分析。</span><span class="sxs-lookup"><span data-stu-id="f21d0-110">has decided to extend their data analysis by creating a custom application that uses data mining functionality.</span></span> <span data-ttu-id="f21d0-111">自訂應用程式的目標是要能夠：</span><span class="sxs-lookup"><span data-stu-id="f21d0-111">Their goal for the custom application is to be able to:</span></span>  
  
-   <span data-ttu-id="f21d0-112">以潛在客戶的特性做為輸入，並預測他們是否會購買自行車。</span><span class="sxs-lookup"><span data-stu-id="f21d0-112">Take as input specific characteristics about a potential customer and predict whether they will buy a bicycle.</span></span>  
  
-   <span data-ttu-id="f21d0-113">以潛在客戶清單及客戶特性做為輸入，並預測誰會購買自行車。</span><span class="sxs-lookup"><span data-stu-id="f21d0-113">Take as input a list of potential customers, as well as characteristics about the customers, and predict which ones will buy a bicycle.</span></span>  
  
 <span data-ttu-id="f21d0-114">在第一個案例中，客戶資料是由客戶註冊頁提供，在第二個案例中，潛在客戶的清單是由 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 行銷部門提供。</span><span class="sxs-lookup"><span data-stu-id="f21d0-114">In the first case, customer data is provided by a customer registration page, and in the second case, a list of potential customers is provided by the [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] marketing department.</span></span>  
  
 <span data-ttu-id="f21d0-115">此外，行銷部門要求能夠將現有客戶依特性分類，例如居住地、子女人數及通勤距離。</span><span class="sxs-lookup"><span data-stu-id="f21d0-115">In addition, the marketing department has asked for the ability to group existing customers into categories based on characteristics such as where they live, the number of children they have, and their commute distance.</span></span> <span data-ttu-id="f21d0-116">他們想知道是否能使用群集來幫助鎖定特定客戶群。</span><span class="sxs-lookup"><span data-stu-id="f21d0-116">They want to see whether these clusters can be used to help target specific kinds of customers.</span></span> <span data-ttu-id="f21d0-117">這需要其他採礦模型。</span><span class="sxs-lookup"><span data-stu-id="f21d0-117">This will require an additional mining model.</span></span>  
  
 [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="f21d0-118">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 提供數個用來完成這些工作的工具：</span><span class="sxs-lookup"><span data-stu-id="f21d0-118">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides several tools that can be used to accomplish these tasks:</span></span>  
  
-   <span data-ttu-id="f21d0-119">DMX 查詢語言</span><span class="sxs-lookup"><span data-stu-id="f21d0-119">The DMX query language</span></span>  
  
-   <span data-ttu-id="f21d0-120">[Microsoft 決策樹演算法](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)和[microsoft 群集演算法](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)</span><span class="sxs-lookup"><span data-stu-id="f21d0-120">The [Microsoft Decision Trees Algorithm](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md) and the [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)</span></span>  
  
-   <span data-ttu-id="f21d0-121"> 中的查詢編輯器</span><span class="sxs-lookup"><span data-stu-id="f21d0-121">Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]</span></span>  
  
 <span data-ttu-id="f21d0-122">資料採礦延伸模組 (DMX) 是 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 提供的一種查詢語言，您可以使用它來建立及處理採礦模型。</span><span class="sxs-lookup"><span data-stu-id="f21d0-122">Data Mining Extensions (DMX) is a query language provided by [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you can use to create and work with mining models.</span></span> <span data-ttu-id="f21d0-123">[!INCLUDE[msCoName](../includes/msconame-md.md)] 決策樹演算法建立可用來預測某人是否會購買自行車的模型。</span><span class="sxs-lookup"><span data-stu-id="f21d0-123">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm creates models that can be used to predict whether someone will purchase a bicycle.</span></span> <span data-ttu-id="f21d0-124">產生的模型可以用個別使用者或客戶資料表做為輸入。</span><span class="sxs-lookup"><span data-stu-id="f21d0-124">The resulting model can take an individual customer or a table of customers as an input.</span></span> <span data-ttu-id="f21d0-125">[!INCLUDE[msCoName](../includes/msconame-md.md)] 群集演算法可依共用特性建立客戶群組。</span><span class="sxs-lookup"><span data-stu-id="f21d0-125">The [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm can create groupings of customers based on shared characteristics.</span></span> <span data-ttu-id="f21d0-126">此教學課程的目標是要提供用於自訂應用程式的 DMX 指令碼。</span><span class="sxs-lookup"><span data-stu-id="f21d0-126">The goal of this tutorial is to provide the DMX scripts that will be used in the custom application.</span></span>  
  
 <span data-ttu-id="f21d0-127">**如需詳細資訊：** [資料採礦解決方案](../../2014/analysis-services/data-mining/data-mining-solutions.md)</span><span class="sxs-lookup"><span data-stu-id="f21d0-127">**For more information:** [Data Mining Solutions](../../2014/analysis-services/data-mining/data-mining-solutions.md)</span></span>  
  
## <a name="mining-structure-and-mining-models"></a><span data-ttu-id="f21d0-128">採礦結構和採礦模型</span><span class="sxs-lookup"><span data-stu-id="f21d0-128">Mining Structure and Mining Models</span></span>  
 <span data-ttu-id="f21d0-129">開始建立 DMX 陳述式之前，一定要先了解 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 用來建立採礦模型的主要物件。</span><span class="sxs-lookup"><span data-stu-id="f21d0-129">Before you begin to create DMX statements, it is important to understand the main objects that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to create mining models.</span></span> <span data-ttu-id="f21d0-130">資料採礦結構是定義資料網域 (從中建立採礦模型) 的資料結構。</span><span class="sxs-lookup"><span data-stu-id="f21d0-130">The mining structure is a data structure that defines the data domain from which mining models are built.</span></span> <span data-ttu-id="f21d0-131">單一採礦結構可包含共用相同網域的多個採礦模型。</span><span class="sxs-lookup"><span data-stu-id="f21d0-131">A single mining structure can contain multiple mining models that share the same domain.</span></span> <span data-ttu-id="f21d0-132">採礦模型會將採礦模型演算法套用至以採礦結構表示的資料。</span><span class="sxs-lookup"><span data-stu-id="f21d0-132">A mining model applies a mining model algorithm to the data, which is represented by a mining structure.</span></span>  
  
 <span data-ttu-id="f21d0-133">採礦結構的建置組塊是採礦結構資料行，它們會描述資料來源包含的資料。</span><span class="sxs-lookup"><span data-stu-id="f21d0-133">The building blocks of the mining structure are the mining structure columns, which describe the data that the data source contains.</span></span> <span data-ttu-id="f21d0-134">這些資料行包含如資料類型、內容類型和資料散發方式等資訊。</span><span class="sxs-lookup"><span data-stu-id="f21d0-134">These columns contain information such as data type, content type, and how the data is distributed.</span></span>  
  
 <span data-ttu-id="f21d0-135">採礦模型必須包含採礦結構所描述的索引鍵資料行，以及剩餘資料行的子集。</span><span class="sxs-lookup"><span data-stu-id="f21d0-135">Mining models must contain the key column described in the mining structure, as well as a subset of the remaining columns.</span></span> <span data-ttu-id="f21d0-136">採礦模型定義每一個資料行的使用方式，以及定義用來建立採礦模型的演算法。</span><span class="sxs-lookup"><span data-stu-id="f21d0-136">The mining model defines the usage for each column and defines the algorithm that is used to create the mining model.</span></span> <span data-ttu-id="f21d0-137">例如，在 DMX 中，您可以指定資料行為索引鍵資料行或 PREDICT 資料行。</span><span class="sxs-lookup"><span data-stu-id="f21d0-137">For example, in DMX you can specify that a column is a Key column or a PREDICT column.</span></span> <span data-ttu-id="f21d0-138">如果未指定資料行，則假設它是輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="f21d0-138">If a column is left unspecified, it is assumed to be an input column.</span></span>  
  
 <span data-ttu-id="f21d0-139">在 DMX 中，有兩種方式建立採礦模型。</span><span class="sxs-lookup"><span data-stu-id="f21d0-139">In DMX, there are two ways to create mining models.</span></span> <span data-ttu-id="f21d0-140">您可以使用 CREATE MINING MODEL 陳述式，同時建立採礦結構和相關聯的採礦模型，也可以先使用 CREATE MINING STRUCTURE 陳述式建立採礦結構，然後使用 ALTER STRUCTURE 陳述式將採礦模型加入結構中。</span><span class="sxs-lookup"><span data-stu-id="f21d0-140">You can either create the mining structure and associated mining model together by using the CREATE MINING MODEL statement, or you can first create a mining structure by using the CREATE MINING STRUCTURE statement, and then add a mining model to the structure by using the ALTER STRUCTURE statement.</span></span> <span data-ttu-id="f21d0-141">下表將描述這些方法。</span><span class="sxs-lookup"><span data-stu-id="f21d0-141">These methods are described in the following table.</span></span>  
  
 <span data-ttu-id="f21d0-142">CREATE MINING MODEL</span><span class="sxs-lookup"><span data-stu-id="f21d0-142">CREATE MINING MODEL</span></span>  
 <span data-ttu-id="f21d0-143">使用此陳述式可同時建立使用相同名稱的採礦結構和相關聯的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="f21d0-143">Use this statement to create a mining structure and associated mining model together using the same name.</span></span> <span data-ttu-id="f21d0-144">採礦模型名稱後面會加上 "Structure"，以便與採礦結構區別。</span><span class="sxs-lookup"><span data-stu-id="f21d0-144">The mining model name is appended with "Structure" to differentiate it from the mining structure.</span></span> <span data-ttu-id="f21d0-145">如果您要建立包含單一採礦模型的採礦結構，則此陳述式很有幫助。</span><span class="sxs-lookup"><span data-stu-id="f21d0-145">This statement is useful if you are creating a mining structure that will contain a single mining model.</span></span>  
  
 <span data-ttu-id="f21d0-146">如需詳細資訊，請參閱 [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx)。</span><span class="sxs-lookup"><span data-stu-id="f21d0-146">For more information, see [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx).</span></span>  
  
 <span data-ttu-id="f21d0-147">ALTER MINING STRUCTURE</span><span class="sxs-lookup"><span data-stu-id="f21d0-147">ALTER MINING STRUCTURE</span></span>  
 <span data-ttu-id="f21d0-148">使用此陳述式將採礦模型加入已存在於伺服器上的採礦結構中。</span><span class="sxs-lookup"><span data-stu-id="f21d0-148">Use this statement to add a mining model to a mining structure that already exists on the server.</span></span> <span data-ttu-id="f21d0-149">如果您想要建立包含數個不同採礦模型的採礦結構，則此陳述式很有幫助。</span><span class="sxs-lookup"><span data-stu-id="f21d0-149">This statement is useful if you want to create a mining structure that contains several different mining models.</span></span> <span data-ttu-id="f21d0-150">您要在單一採礦結構中加入不止一個採礦模型，有幾個原因。</span><span class="sxs-lookup"><span data-stu-id="f21d0-150">There are several reasons that you would want to add more than one mining model in a single mining structure.</span></span> <span data-ttu-id="f21d0-151">例如，您可以建立數個使用不同演算法的採礦模型，看看哪一個最好用。</span><span class="sxs-lookup"><span data-stu-id="f21d0-151">For example, you might create several mining models that use different algorithms to see which algorithm works best.</span></span> <span data-ttu-id="f21d0-152">您可以建立數個使用相同演算法的採礦模型，但每一個採礦模型要設定不同的參數，以找出參數的最佳設定。</span><span class="sxs-lookup"><span data-stu-id="f21d0-152">You might create several mining models that use the same algorithm, but with a parameter set differently for each mining model to find the best setting for the parameter.</span></span>  
  
 <span data-ttu-id="f21d0-153">如需詳細資訊，請參閱[ALTER &#40;DMX&#41;的採礦結構](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016)。</span><span class="sxs-lookup"><span data-stu-id="f21d0-153">For more information, see [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016).</span></span>  
  
 <span data-ttu-id="f21d0-154">因為您要建立包含數個採礦模型的採礦結構，所以您將使用此教學課程的第二個方法。</span><span class="sxs-lookup"><span data-stu-id="f21d0-154">Because you will create a mining structure that contains several mining models, you will use the second method in this tutorial.</span></span>  
  
 <span data-ttu-id="f21d0-155">**詳細資訊**</span><span class="sxs-lookup"><span data-stu-id="f21d0-155">**For More Information**</span></span>  
  
 <span data-ttu-id="f21d0-156">[資料採礦延伸模組 &#40;dmx&#41; 參考](/sql/dmx/data-mining-extensions-dmx-reference)，瞭解 Dmx 預測查詢[的 dmx Select 語句](/sql/dmx/understanding-the-dmx-select-statement)、[結構和使用](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)方式</span><span class="sxs-lookup"><span data-stu-id="f21d0-156">[Data Mining Extensions &#40;DMX&#41; Reference](/sql/dmx/data-mining-extensions-dmx-reference), [Understanding the DMX Select Statement](/sql/dmx/understanding-the-dmx-select-statement), [Structure and Usage of DMX Prediction Queries](/sql/dmx/structure-and-usage-of-dmx-prediction-queries)</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="f21d0-157">學習內容</span><span class="sxs-lookup"><span data-stu-id="f21d0-157">What You Will Learn</span></span>  
 <span data-ttu-id="f21d0-158">這個教學課程分成下列課程：</span><span class="sxs-lookup"><span data-stu-id="f21d0-158">This tutorial is divided into the following lessons:</span></span>  
  
 [<span data-ttu-id="f21d0-159">第 1 課：建立自行車買主採礦結構</span><span class="sxs-lookup"><span data-stu-id="f21d0-159">Lesson 1: Creating the Bike Buyer Mining Structure</span></span>](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)  
 <span data-ttu-id="f21d0-160">在這一課，您將學會如何使用 `CREATE` 陳述式來建立採礦結構。</span><span class="sxs-lookup"><span data-stu-id="f21d0-160">In this lesson, you will learn how to use the `CREATE` statement to create mining structures.</span></span>  
  
 [<span data-ttu-id="f21d0-161">第 2 課：將採礦模型新增至自行車買主採礦結構</span><span class="sxs-lookup"><span data-stu-id="f21d0-161">Lesson 2: Adding Mining Models to the Bike Buyer Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
 <span data-ttu-id="f21d0-162">在這一課，您將學會如何使用 `ALTER` 陳述式將採礦模型加入至採礦結構。</span><span class="sxs-lookup"><span data-stu-id="f21d0-162">In this lesson, you will learn how to use the `ALTER` statement to add mining models to a mining structure.</span></span>  
  
 [<span data-ttu-id="f21d0-163">第 3 課：處理自行車買主採礦結構</span><span class="sxs-lookup"><span data-stu-id="f21d0-163">Lesson 3: Processing the Bike Buyer Mining Structure</span></span>](../../2014/tutorials/lesson-3-processing-the-bike-buyer-mining-structure.md)  
 <span data-ttu-id="f21d0-164">在這一課，您將學會如何使用 `INSERT INTO` 陳述式來處理採礦結構及其相關聯的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="f21d0-164">In this lesson you will learn how to use the `INSERT INTO` statement to process mining structures and their associated mining models.</span></span>  
  
 [<span data-ttu-id="f21d0-165">第 4 課：瀏覽自行車買主採礦模型</span><span class="sxs-lookup"><span data-stu-id="f21d0-165">Lesson 4: Browsing the Bike Buyer Mining Models</span></span>](../../2014/tutorials/lesson-4-browsing-the-bike-buyer-mining-models.md)  
 <span data-ttu-id="f21d0-166">在這一課，您將學會如何使用 `SELECT` 陳述式來探索採礦模型的內容。</span><span class="sxs-lookup"><span data-stu-id="f21d0-166">In this lesson, you will learn how to use the `SELECT` statement to explore the content of the mining models.</span></span>  
  
 [<span data-ttu-id="f21d0-167">第 5 課：執行預測查詢</span><span class="sxs-lookup"><span data-stu-id="f21d0-167">Lesson 5: Executing Prediction Queries</span></span>](../../2014/tutorials/lesson-5-executing-prediction-queries.md)  
 <span data-ttu-id="f21d0-168">在這一課，您將學會如何使用 `PREDICTION JOIN` 陳述式來建立採礦模型的預測。</span><span class="sxs-lookup"><span data-stu-id="f21d0-168">In this lesson, you will learn how to use the `PREDICTION JOIN` statement to create predictions against mining models.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f21d0-169">需求</span><span class="sxs-lookup"><span data-stu-id="f21d0-169">Requirements</span></span>  
 <span data-ttu-id="f21d0-170">在執行此教學課程之前，請確定有安裝下列各項：</span><span class="sxs-lookup"><span data-stu-id="f21d0-170">Before doing this tutorial, make sure that the following are installed:</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)] <span data-ttu-id="f21d0-171">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f21d0-171">[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]</span></span>  
  
-   [!INCLUDE[msCoName](../includes/msconame-md.md)]<span data-ttu-id="f21d0-172">[!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)]、 [!INCLUDE[ssASversion10](../includes/ssasversion10-md.md)] 、 [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)] 或 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f21d0-172">[!INCLUDE[ssASversion2005](../includes/ssasversion2005-md.md)], [!INCLUDE[ssASversion10](../includes/ssasversion10-md.md)], [!INCLUDE[ssASCurrent](../includes/ssascurrent-md.md)], or [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]</span></span>  
  
-   <span data-ttu-id="f21d0-173">[!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 資料庫。</span><span class="sxs-lookup"><span data-stu-id="f21d0-173">The [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] database.</span></span> <span data-ttu-id="f21d0-174">為了加強安全性，系統預設不會安裝範例資料庫。</span><span class="sxs-lookup"><span data-stu-id="f21d0-174">By default, the sample databases are not installed, to enhance security.</span></span> <span data-ttu-id="f21d0-175">若要安裝的正式範例資料庫 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ，請造訪[Microsoft SQL 範例資料庫](https://go.microsoft.com/fwlink/?LinkId=88417)頁面，並選取您要安裝的資料庫。</span><span class="sxs-lookup"><span data-stu-id="f21d0-175">To install official sample databases for [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], visit the [Microsoft SQL Sample Databases](https://go.microsoft.com/fwlink/?LinkId=88417) page and select the databases that you want to install..</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f21d0-176">當您查看教學課程時，建議您將 **[下一個主題]** 和 [**上一個主題**] 按鈕新增至 [檔檢視器] 工具列。</span><span class="sxs-lookup"><span data-stu-id="f21d0-176">When you review tutorials, we recommend that you add **Next topic** and **Previous topic** buttons to the document viewer toolbar.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f21d0-177">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f21d0-177">See Also</span></span>  
 <span data-ttu-id="f21d0-178">[購物籃 DMX 教學課程](../../2014/tutorials/market-basket-dmx-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="f21d0-178">[Market Basket DMX Tutorial](../../2014/tutorials/market-basket-dmx-tutorial.md) </span></span>  
 [<span data-ttu-id="f21d0-179">資料採礦基本教學課程</span><span class="sxs-lookup"><span data-stu-id="f21d0-179">Basic Data Mining Tutorial</span></span>](../../2014/tutorials/basic-data-mining-tutorial.md)  
  
  
