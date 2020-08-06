---
title: 為結構指定測試資料集 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 75cd508f-b126-418b-848d-3c4c3e6c303f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c1430706a0ec2cd3ddc0eaee18d7001d05fefae1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584900"
---
# <a name="specifying-a-testing-data-set-for-the-structure-basic-data-mining-tutorial"></a><span data-ttu-id="37987-102">為結構指定測試資料集 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="37987-102">Specifying a Testing Data Set for the Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="37987-103">在資料採礦精靈的最後幾個畫面中，您會將資料分成測試集和定型集。</span><span class="sxs-lookup"><span data-stu-id="37987-103">In the final few screens of the Data Mining Wizard you will split your data into a testing set and a training set.</span></span> <span data-ttu-id="37987-104">然後您會命名您的結構，並啟用模型上的鑽研。</span><span class="sxs-lookup"><span data-stu-id="37987-104">You will then name your structure and enable drillthrough on the model.</span></span>  
  
## <a name="specifying-a-testing-set"></a><span data-ttu-id="37987-105">指定測試集</span><span class="sxs-lookup"><span data-stu-id="37987-105">Specifying a Testing Set</span></span>  
 <span data-ttu-id="37987-106">在建立採礦結構時將資料分成定型集和測試集，可輕鬆評估您稍後建立之採礦模型的精確度。</span><span class="sxs-lookup"><span data-stu-id="37987-106">Separating data into training and testing sets when you create a mining structure makes it possible to easily assess the accuracy of the mining models that you create later.</span></span> <span data-ttu-id="37987-107">如需測試集的詳細資訊，請參閱[定型和測試資料集](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md)。</span><span class="sxs-lookup"><span data-stu-id="37987-107">For more information on testing sets, see [Training and Testing Data Sets](../../2014/analysis-services/data-mining/training-and-testing-data-sets.md).</span></span>  
  
#### <a name="to-specify-the-testing-set"></a><span data-ttu-id="37987-108">若要指定測試集</span><span class="sxs-lookup"><span data-stu-id="37987-108">To specify the testing set</span></span>  
  
1.  <span data-ttu-id="37987-109">在 [**建立測試集**] 頁面上，針對 [**要測試的資料百分比**] 保留預設值 `30` 。</span><span class="sxs-lookup"><span data-stu-id="37987-109">On the **Create Testing Set** page, for **Percentage of data for testing**, leave the default value of `30`.</span></span>  
  
2.  <span data-ttu-id="37987-110">針對 [**測試資料集內的最大案例數目**]，輸入 `1000` 。</span><span class="sxs-lookup"><span data-stu-id="37987-110">For **Maximum number of cases in testing data set**, type `1000`.</span></span>  
  
3.  <span data-ttu-id="37987-111">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="37987-111">Click **Next**.</span></span>  
  
## <a name="specifying-drillthrough"></a><span data-ttu-id="37987-112">指定鑽研</span><span class="sxs-lookup"><span data-stu-id="37987-112">Specifying Drillthrough</span></span>  
 <span data-ttu-id="37987-113">可以在模型和結構上啟用鑽研。</span><span class="sxs-lookup"><span data-stu-id="37987-113">Drillthrough can be enabled on models and on structures.</span></span> <span data-ttu-id="37987-114">此對話方塊中的核取方塊允許在具名模型上鑽研。</span><span class="sxs-lookup"><span data-stu-id="37987-114">The checkbox in this dialog box enables drillthrough on the named model.</span></span> <span data-ttu-id="37987-115">此模型經過處理之後，您將能夠從定型資料 中擷取用來建立模型的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="37987-115">After the model has been processed,  you will be able to retrieve detailed information from the training data that were used to create the model.</span></span>  
  
 <span data-ttu-id="37987-116">如果基礎採礦結構也已經設定為允許鑽研，您就可以同時從模型案例和採礦結構中擷取詳細資訊，包括未包含在採礦模型中的資料行。</span><span class="sxs-lookup"><span data-stu-id="37987-116">If the underlying mining structure has also been configured to allow drillthrough, you can retrieve detailed information from both the model cases and the mining structure, including columns that were not included in the mining model.</span></span> <span data-ttu-id="37987-117">如需詳細資訊，請參閱 [鑽研查詢 &#40;資料採礦&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="37987-117">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md).</span></span>  
  
#### <a name="to-name-the-model-and-structure-and-specify-drillthrough"></a><span data-ttu-id="37987-118">若要命名模型和結構及指定鑽研</span><span class="sxs-lookup"><span data-stu-id="37987-118">To name the model and structure and specify drillthrough</span></span>  
  
1.  <span data-ttu-id="37987-119">在 [**正在完成嚮導]** 頁面的 [**採礦結構名稱**] 中，輸入 `Targeted Mailing` 。</span><span class="sxs-lookup"><span data-stu-id="37987-119">On the **Completing the Wizard** page, in **Mining structure name**, type `Targeted Mailing`.</span></span>  
  
2.  <span data-ttu-id="37987-120">在 [**採礦模型名稱**] 中，輸入 `TM_Decision_Tree` 。</span><span class="sxs-lookup"><span data-stu-id="37987-120">In **Mining model name**, type `TM_Decision_Tree`.</span></span>  
  
3.  <span data-ttu-id="37987-121">選取 [**允許流覽**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="37987-121">Select the **Allow drill through** check box.</span></span>  
  
4.  <span data-ttu-id="37987-122">查看**預覽**窗格。</span><span class="sxs-lookup"><span data-stu-id="37987-122">Review the **Preview** pane.</span></span> <span data-ttu-id="37987-123">請注意，只會顯示選取做為索引**鍵**、**輸入**或**可預測**的資料行。</span><span class="sxs-lookup"><span data-stu-id="37987-123">Notice that only those columns selected as **Key**, **Input** or **Predictable** are shown.</span></span> <span data-ttu-id="37987-124">您所選的其他資料行 (例如 AddressLine1) 不會用於建立模型，但是可在基礎結構中使用，而且可在處理及部署模型之後加以查詢。</span><span class="sxs-lookup"><span data-stu-id="37987-124">The other columns you selected (e.g., AddressLine1) are not used for building the model but will be available in the underlying structure, and can be queried after the model is processed and deployed.</span></span>  
  
5.  <span data-ttu-id="37987-125">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="37987-125">Click **Finish**.</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="37987-126">本課程的前一項工作</span><span class="sxs-lookup"><span data-stu-id="37987-126">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="37987-127">&#40;基本資料採礦教學課程中指定資料類型和內容類型&#41;</span><span class="sxs-lookup"><span data-stu-id="37987-127">Specifying the Data Type and Content Type &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/specifying-the-data-type-and-content-type-basic-data-mining-tutorial.md)  
  
## <a name="next-lesson"></a><span data-ttu-id="37987-128">下一課</span><span class="sxs-lookup"><span data-stu-id="37987-128">Next Lesson</span></span>  
 [<span data-ttu-id="37987-129">第 3 課：新增及處理模型</span><span class="sxs-lookup"><span data-stu-id="37987-129">Lesson 3: Adding and Processing Models</span></span>](../../2014/tutorials/lesson-3-adding-and-processing-models.md)  
  
## <a name="see-also"></a><span data-ttu-id="37987-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="37987-130">See Also</span></span>  
 <span data-ttu-id="37987-131">[啟用採礦模型的鑽取](../../2014/analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md) </span><span class="sxs-lookup"><span data-stu-id="37987-131">[Enable Drillthrough for a Mining Model](../../2014/analysis-services/data-mining/enable-drillthrough-for-a-mining-model.md) </span></span>  
 <span data-ttu-id="37987-132">[資料採礦&#41;&#40;的鑽取查詢](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="37987-132">[Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md) </span></span>  
 [<span data-ttu-id="37987-133">指定定型資料 &#40;資料採礦嚮導&#41;</span><span class="sxs-lookup"><span data-stu-id="37987-133">Specify the Training Data &#40;Data Mining Wizard&#41;</span></span>](../../2014/analysis-services/specify-the-training-data-data-mining-wizard.md)  
  
  
