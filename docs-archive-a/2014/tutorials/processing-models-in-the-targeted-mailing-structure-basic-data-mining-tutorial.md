---
title: 處理目標郵寄結構中的模型 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9d8233bb-117e-4563-9302-8a5a8ad1fae2
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b8fb7b9f601f351520c3f611cc3c520614ed8ccc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699055"
---
# <a name="processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial"></a><span data-ttu-id="5cad3-102">處理目標郵寄結構中的模型 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="5cad3-102">Processing Models in the Targeted Mailing Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="5cad3-103">在您可以瀏覽或使用採礦模型之前，必須先部署 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案並處理採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="5cad3-103">Before you can browse or work with the mining models that you have created, you must deploy the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project and process the mining structure and mining models.</span></span>  
  
-   <span data-ttu-id="5cad3-104">*部署*會將專案傳送到伺服器，並在伺服器上的該專案中建立任何物件。</span><span class="sxs-lookup"><span data-stu-id="5cad3-104">*Deploying* sends the project to a server and creates any objects in that project on the server.</span></span>  
  
-   <span data-ttu-id="5cad3-105">*處理*會將 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 關聯式資料來源的資料填入物件中。</span><span class="sxs-lookup"><span data-stu-id="5cad3-105">*Processing* populates [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects with data from relational data sources.</span></span>  
  
 <span data-ttu-id="5cad3-106">模型要等到部署及處理之後，才可以使用。</span><span class="sxs-lookup"><span data-stu-id="5cad3-106">Models cannot be used until they have been deployed and processed.</span></span> <span data-ttu-id="5cad3-107">此外，一旦您對模型進行任何變更 (例如加入新資料)，就必須重新部署及重新處理模型。</span><span class="sxs-lookup"><span data-stu-id="5cad3-107">Also, when you make any changes to the model, such as adding new data, you must redeploy and reprocess the models.</span></span>  
  
## <a name="ensuring-consistency-with-holdoutseed"></a><span data-ttu-id="5cad3-108">確保與 HoldoutSeed 之間的一致性</span><span class="sxs-lookup"><span data-stu-id="5cad3-108">Ensuring Consistency with HoldoutSeed</span></span>  
 <span data-ttu-id="5cad3-109">當您部署專案以及處理結構與模型時，資料結構中的個別資料列將會指派給以數值種子值為根據的定型集或測試集。</span><span class="sxs-lookup"><span data-stu-id="5cad3-109">When you deploy a project and process the structure and models, individual rows in your data structure are assigned to either the training set or testing set based on a numerical seed value.</span></span> <span data-ttu-id="5cad3-110">依預設，數值種子值是根據資料結構中的屬性來計算。</span><span class="sxs-lookup"><span data-stu-id="5cad3-110">By default, the numerical seed value is computed based on attributes of the data structure.</span></span> <span data-ttu-id="5cad3-111">不過，如果您變更了模型的某些層面，種子值將會變更而使得結果稍微不同。</span><span class="sxs-lookup"><span data-stu-id="5cad3-111">However, if you ever change some aspects of your model, the seed value would change, leading to subtly different results.</span></span> <span data-ttu-id="5cad3-112">因此，為了確保您的結果與這裡所述相同，我們將會任意指派固定的*維持種子* `12` 。</span><span class="sxs-lookup"><span data-stu-id="5cad3-112">Therefore, in order to ensure that your results are the same as described here, we will arbitrarily assign a fixed *holdout seed* of `12`.</span></span> <span data-ttu-id="5cad3-113">鑑效組種子是用來初始化取樣演算法，並確保所有採礦結構及其模型的資料分割方式大致相同。</span><span class="sxs-lookup"><span data-stu-id="5cad3-113">The holdout seed is used to initialize the sampling algorithm, and ensures that the data is partitioned in roughly the same way for all mining structures and their models.</span></span>  
  
 <span data-ttu-id="5cad3-114">這個值不會影響定型集內的案例數目，而是要確保每次建立模型時都將使用相同的資料分割方法。</span><span class="sxs-lookup"><span data-stu-id="5cad3-114">This value does not affect the number of cases in the training set; it simply ensures that the same partitioning method will be used each time you build the model.</span></span>  
  
 <span data-ttu-id="5cad3-115">如需有關維持種子的詳細資訊，請參閱[定型和測試資料集](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="5cad3-115">For more information on holdout seed, see [Training and Testing Data Sets](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md).</span></span>  
  
#### <a name="to-set-the-holdout-seed"></a><span data-ttu-id="5cad3-116">若要設定鑑效組種子</span><span class="sxs-lookup"><span data-stu-id="5cad3-116">To set the Holdout Seed</span></span>  
  
1.  <span data-ttu-id="5cad3-117">在的 [資料採礦設計師] 中，按一下 [**採礦結構**] 索引標籤或 [**採礦模型**] 索引標籤 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="5cad3-117">Click on the **Mining Structure** tab or the **Mining Models** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="5cad3-118">**目標郵寄 MiningStructure**會顯示在 [**屬性**] 窗格中。</span><span class="sxs-lookup"><span data-stu-id="5cad3-118">**Targeted Mailing MiningStructure** displays in the **Properties** pane.</span></span>  
  
2.  <span data-ttu-id="5cad3-119">按**F4**確定 [**屬性**] 窗格已開啟。</span><span class="sxs-lookup"><span data-stu-id="5cad3-119">Ensure that the **Properties** pane is open by pressing **F4**.</span></span>  
  
3.  <span data-ttu-id="5cad3-120">確定 [ **CacheMode** ] 設定為 [ **KeepTrainingCases**]。</span><span class="sxs-lookup"><span data-stu-id="5cad3-120">Ensure that **CacheMode** is set to **KeepTrainingCases**.</span></span>  
  
4.  <span data-ttu-id="5cad3-121">`12`針對**HoldoutSeed**輸入。</span><span class="sxs-lookup"><span data-stu-id="5cad3-121">Enter `12` for **HoldoutSeed**.</span></span>  
  
## <a name="deploying-and-processing-the-models"></a><span data-ttu-id="5cad3-122">部署及處理模型</span><span class="sxs-lookup"><span data-stu-id="5cad3-122">Deploying and Processing the Models</span></span>  
 <span data-ttu-id="5cad3-123">在 [資料採礦設計師] 中，您可以根據您對模型或基礎資料所做的變更範圍，決定要處理的物件：</span><span class="sxs-lookup"><span data-stu-id="5cad3-123">In Data Mining Designer, you can decide which objects to process, depending on the scope of changes you've made to your model or the underlying data:</span></span>  
  
 <span data-ttu-id="5cad3-124">這項工作由於資料和模型都是新的，您將要同時處理此結構和所有模型。</span><span class="sxs-lookup"><span data-stu-id="5cad3-124">For this task, because the data and the models are new, you will process the structure and all the models at the same time.</span></span>  
  
#### <a name="to-deploy-the-project-and-process-all-the-mining-models"></a><span data-ttu-id="5cad3-125">若要部署專案和處理所有採礦模型</span><span class="sxs-lookup"><span data-stu-id="5cad3-125">To deploy the project and process all the mining models</span></span>  
  
1.  <span data-ttu-id="5cad3-126">在 [**採礦模型**] 功能表中，選取 [**處理採礦結構] 和 [所有模型**]。</span><span class="sxs-lookup"><span data-stu-id="5cad3-126">In the **Mining Model** menu, select **Process Mining Structure and All Models**.</span></span>  
  
     <span data-ttu-id="5cad3-127">如果您變更了結構，系統將會提示您建立及部署專案，然後才能處理模型。</span><span class="sxs-lookup"><span data-stu-id="5cad3-127">If you made changes to the structure, you will be prompted to build and deploy the project before processing the models.</span></span> <span data-ttu-id="5cad3-128">按一下 [是] 。</span><span class="sxs-lookup"><span data-stu-id="5cad3-128">Click **Yes**.</span></span>  
  
2.  <span data-ttu-id="5cad3-129">按一下 [**處理採礦結構-目標郵寄**] 對話方塊中的 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="5cad3-129">Click **Run** in the **Processing Mining Structure - Targeted Mailing** dialog box.</span></span>  
  
     <span data-ttu-id="5cad3-130">隨即開啟 **[處理進度]** 對話方塊，以顯示模型處理的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="5cad3-130">The **Process Progress** dialog box opens to display the details of model processing.</span></span> <span data-ttu-id="5cad3-131">處理模型可能需要花一些時間，這會隨著您的電腦而不同。</span><span class="sxs-lookup"><span data-stu-id="5cad3-131">Model processing might take some time, depending on your computer.</span></span>  
  
3.  <span data-ttu-id="5cad3-132">在模型完成處理之後，按一下 **[處理進度]** 對話方塊中的 **[關閉]** 。</span><span class="sxs-lookup"><span data-stu-id="5cad3-132">Click **Close** in the **Process Progress** dialog box after the models have completed processing.</span></span>  
  
4.  <span data-ttu-id="5cad3-133">在 [**處理採礦結構 \<structure> -** ] 對話方塊中，按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="5cad3-133">Click **Close** in the **Processing Mining Structure - \<structure>** dialog box.</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="5cad3-134">本課程的前一項工作</span><span class="sxs-lookup"><span data-stu-id="5cad3-134">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="5cad3-135">將新模型加入至目標郵寄結構 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="5cad3-135">Adding New Models to the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="5cad3-136">下一課</span><span class="sxs-lookup"><span data-stu-id="5cad3-136">Next Lesson</span></span>  
 [<span data-ttu-id="5cad3-137">第4課：探索目標郵寄模型 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="5cad3-137">Lesson 4: Exploring the Targeted Mailing Models &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/lesson-4-exploring-the-targeted-mailing-models-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="5cad3-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5cad3-138">See Also</span></span>  
 [<span data-ttu-id="5cad3-139">處理需求和考量 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="5cad3-139">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
