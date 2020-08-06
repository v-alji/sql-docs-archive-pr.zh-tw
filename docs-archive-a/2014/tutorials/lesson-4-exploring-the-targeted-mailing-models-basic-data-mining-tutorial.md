---
title: 第4課：探索目標郵寄模型 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1e00c5b9-a9f8-4503-99ee-377c9cc02d7f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 8659350b126164e06550acdbecec04bb07499c55
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704454"
---
# <a name="lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial"></a><span data-ttu-id="09bcf-102">第 4 課：探索目標郵寄模型 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="09bcf-102">Lesson 4: Exploring the Targeted Mailing Models (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="09bcf-103">處理完專案中的模型之後，您可以瀏覽模型來尋找值得參考的趨勢。</span><span class="sxs-lookup"><span data-stu-id="09bcf-103">After the models in your project have been processed, you can explore them to look for interesting trends.</span></span> <span data-ttu-id="09bcf-104">由於模式光看數字可能相當複雜且難以上手，SQL Server 資料採礦提供了一些視覺化工具，可協助您調查資料及了解演算法在資料內探索到的規則和關聯性。</span><span class="sxs-lookup"><span data-stu-id="09bcf-104">Because patterns can be complex and difficult simply by looking at numbers, SQL Server Data Mining provides some visual tools that help you investigate the data and understand the rules and relationships that the algorithms have discovered within the data.</span></span> <span data-ttu-id="09bcf-105">您也可以使用各種精確度測試，在部署模型之前驗證您的資料集或找出執行能力最佳的模型。</span><span class="sxs-lookup"><span data-stu-id="09bcf-105">You can also use a variety of accuracy tests to validate your dataset or discover which model performs best before you deploy it.</span></span>  
  
 <span data-ttu-id="09bcf-106">當您使用 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 來探索模型時，您建立的每個模型都會列在資料採礦設計師的 [**採礦模型檢視器**] 索引標籤中。</span><span class="sxs-lookup"><span data-stu-id="09bcf-106">When you use [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to explore your models, each model you created is listed in the **Mining Model Viewer** tab in Data Mining Designer.</span></span> <span data-ttu-id="09bcf-107">您可以使用檢視器瀏覽模型。</span><span class="sxs-lookup"><span data-stu-id="09bcf-107">You can use the viewers to explore the models.</span></span> <span data-ttu-id="09bcf-108">這些檢視器也可以在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中使用。</span><span class="sxs-lookup"><span data-stu-id="09bcf-108">These viewers are also available in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="09bcf-109">您在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中用來建立模型的每個演算法都會傳回不同類型的結果。</span><span class="sxs-lookup"><span data-stu-id="09bcf-109">Each algorithm that you used to build a model in [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] returns a different type of result.</span></span> <span data-ttu-id="09bcf-110">因此，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 為每一類型的機器學習模型提供自訂檢視器。</span><span class="sxs-lookup"><span data-stu-id="09bcf-110">Therefore, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] provides custom viewers for each type of machine learning model.</span></span>  
  
 <span data-ttu-id="09bcf-111">如果您想要深入瞭解詳細資料， [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 也會提供稱為「**一般內容樹狀檢視器**」的 HTML 檢視器，其中會以半表格式格式顯示模型資料的詳細資訊，以及找到的任何模式。</span><span class="sxs-lookup"><span data-stu-id="09bcf-111">If you want to get into details, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] also provides an HTML viewer, called the **Generic Content Tree Viewer**, that displays detailed information about the model data and any patterns that were found, in a semi-tabular format.</span></span> <span data-ttu-id="09bcf-112">如需詳細資訊，請參閱 [使用 Microsoft 一般內容樹狀檢視器瀏覽模型](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md)。</span><span class="sxs-lookup"><span data-stu-id="09bcf-112">For more information, see [Browse a Model Using the Microsoft Generic Content Tree Viewer](../../2014/analysis-services/data-mining/browse-a-model-using-the-microsoft-generic-content-tree-viewer.md).</span></span>  
  
 <span data-ttu-id="09bcf-113">在這一課，您將查看三種模型產生的結果。</span><span class="sxs-lookup"><span data-stu-id="09bcf-113">In this lesson you will look at the results from your three models.</span></span> <span data-ttu-id="09bcf-114">每一種模型類型都根據不同的演算法，讓您以不同的角度去了解資料。</span><span class="sxs-lookup"><span data-stu-id="09bcf-114">Each model type is based on a different algorithm and provides different insights into the data.</span></span>  
  
-   <span data-ttu-id="09bcf-115">決策樹模型指出影響自行車購買行為的因素。</span><span class="sxs-lookup"><span data-stu-id="09bcf-115">The Decision Tree model tells you about factors that influence bike buying.</span></span>  
  
-   <span data-ttu-id="09bcf-116">群集模型依客戶的自行車購買行為以及您選擇的其他屬性，將客戶予以分組。</span><span class="sxs-lookup"><span data-stu-id="09bcf-116">The Clustering model groups your customers by attributes that include their bike buying behavior and other selected attributes.</span></span>  
  
-   <span data-ttu-id="09bcf-117">貝氏機率分類模型可以讓您探索不同屬性之間的關聯。</span><span class="sxs-lookup"><span data-stu-id="09bcf-117">The Naive Bayes model enables you to explore the relationship between different attributes.</span></span>  
  
 <span data-ttu-id="09bcf-118">請參閱下列主題，深入了解每一種採礦模型檢視器。</span><span class="sxs-lookup"><span data-stu-id="09bcf-118">See the following topics to learn more about each of the mining model viewers.</span></span>  
  
-   [<span data-ttu-id="09bcf-119">流覽決策樹模型 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="09bcf-119">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="09bcf-120">&#40;基本資料採礦教學課程中探索群集模型&#41;</span><span class="sxs-lookup"><span data-stu-id="09bcf-120">Exploring the Clustering Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-clustering-model-basic-data-mining-tutorial.md)  
  
-   [<span data-ttu-id="09bcf-121">探索貝氏貝氏機率分類模型 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="09bcf-121">Exploring the Naive Bayes Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-naive-bayes-model-basic-data-mining-tutorial.md)  
  
 <span data-ttu-id="09bcf-122">這三種模型都可以使用**一般內容樹狀檢視器**來查看，以解壓縮公式、資料值等等。</span><span class="sxs-lookup"><span data-stu-id="09bcf-122">All three models can be viewed using the **Generic Content Tree Viewer**, to extract formulas, data values, and so forth.</span></span>  
  
## <a name="first-task-in-lesson"></a><span data-ttu-id="09bcf-123">本課程的第一項工作</span><span class="sxs-lookup"><span data-stu-id="09bcf-123">First Task in Lesson</span></span>  
 [<span data-ttu-id="09bcf-124">流覽決策樹模型 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="09bcf-124">Exploring the Decision Tree Model &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-decision-tree-model-basic-data-mining-tutorial.md)  
  
## <a name="previous-lesson"></a><span data-ttu-id="09bcf-125">上一課</span><span class="sxs-lookup"><span data-stu-id="09bcf-125">Previous Lesson</span></span>  
 [<span data-ttu-id="09bcf-126">第 3 課：新增及處理模型</span><span class="sxs-lookup"><span data-stu-id="09bcf-126">Lesson 3: Adding and Processing Models</span></span>](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="09bcf-127">下一課</span><span class="sxs-lookup"><span data-stu-id="09bcf-127">Next Lesson</span></span>  
 [<span data-ttu-id="09bcf-128">第5課： &#40;基本資料採礦教學課程來測試模型&#41;</span><span class="sxs-lookup"><span data-stu-id="09bcf-128">Lesson 5: Testing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-5-testing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="09bcf-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09bcf-129">See Also</span></span>  
 <span data-ttu-id="09bcf-130">[採礦模型檢視器工作和操作說明](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md) </span><span class="sxs-lookup"><span data-stu-id="09bcf-130">[Mining Model Viewer Tasks and How-tos](../../2014/analysis-services/data-mining/mining-model-viewer-tasks-and-how-tos.md) </span></span>  
 [<span data-ttu-id="09bcf-131">資料採礦模型檢視器</span><span class="sxs-lookup"><span data-stu-id="09bcf-131">Data Mining Model Viewers</span></span>](../../2014/analysis-services/data-mining/data-mining-model-viewers.md)  
  
  
