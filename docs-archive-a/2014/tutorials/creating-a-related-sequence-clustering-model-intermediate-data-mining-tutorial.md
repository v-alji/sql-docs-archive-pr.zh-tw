---
title: 建立相關的時序群集模型 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 1fb4f5bc-1756-45ca-9cd7-411a8c5992a9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d015ed8a9887cb6164020806bf4136f58629ad11
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703566"
---
# <a name="creating-a-related-sequence-clustering-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="fa3a2-102">建立相關的時序群集採礦模型 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="fa3a2-102">Creating a Related Sequence Clustering Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="fa3a2-103">探索時序群集模型之後，您了解到 Region 或 Income 等其他屬性對於模型也有很大的影響。因此，若要進一步了解時序，您需要建立相關的時序群集模型，並移除與客戶人口統計有關的屬性。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-103">Through your exploration of the sequence clustering model, you learned that other attributes such as Region or Income have a strong effect on the models; therefore, to understand the sequences better, you will create a related sequence clustering model and remove the attributes related to customer demographics.</span></span>  
  
 <span data-ttu-id="fa3a2-104">在這項工作中，您將建立一個區域時序群集模型的副本，然後從模型中移除任何與時序無直接關聯的資料行。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-104">In this task, you will create a copy of the regional sequence clustering model, and then remove from the model any columns that are not directly related to the sequences.</span></span>  
  
 <span data-ttu-id="fa3a2-105">新的模型所包含的資料行，與所依據之採礦模型的資料行完全相同。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-105">The new model will contain all the same columns as the mining model on which it is based.</span></span> <span data-ttu-id="fa3a2-106">不過，您不必從採礦結構移除資料行，只要指定新的採礦模型忽略資料行即可。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-106">However, you do not need to remove the columns from the mining structure, only specify that the new mining model ignore the columns.</span></span>  
  
### <a name="to-make-a-copy-of-the-sequence-clustering-model"></a><span data-ttu-id="fa3a2-107">若要製作時序群集模型的副本</span><span class="sxs-lookup"><span data-stu-id="fa3a2-107">To make a copy of the sequence clustering model</span></span>  
  
1.  <span data-ttu-id="fa3a2-108">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的資料採礦設計工具中，按一下 [**採礦模型**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-108">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in the Data Mining Designer, click the **Mining Models** tab.</span></span>  
  
2.  <span data-ttu-id="fa3a2-109">以滑鼠右鍵按一下您要複製的模型，然後選取 [新增] [**採礦模型**]。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-109">Right-click the model you want to copy, and select **New Mining Model**.</span></span>  
  
3.  <span data-ttu-id="fa3a2-110">在 [**新增採礦模型**] 對話方塊中，輸入模型名稱，然後選取 [Microsoft] `Sequence Clustering` 。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-110">In the **New Mining Model** dialog box, type a model name, and select Microsoft `Sequence Clustering`.</span></span>  
  
     <span data-ttu-id="fa3a2-111">在此教學課程中，請輸入名稱 `Sequence Clustering` 。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-111">For this tutorial, type the name `Sequence Clustering`.</span></span>  
  
4.  <span data-ttu-id="fa3a2-112">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-112">Click **OK**.</span></span>  
  
### <a name="to-remove-columns-from-the-mining-model"></a><span data-ttu-id="fa3a2-113">若要從採礦模型移除資料行</span><span class="sxs-lookup"><span data-stu-id="fa3a2-113">To remove columns from the mining model</span></span>  
  
1.  <span data-ttu-id="fa3a2-114">在 [**採礦模型**] 索引標籤中，于名為 [時序群集] 的新模型之資料行中，按一下 [**收入群組**] 屬性的資料列，然後選取 [**忽略**]。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-114">In the **Mining Model** tab, in the column for the new model named Sequence Clustering, click the row for the **Income Group** attribute, and select **Ignore**.</span></span>  
  
2.  <span data-ttu-id="fa3a2-115">針對屬性**區域**重複此步驟。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-115">Repeat this step for the attribute **Region**.</span></span>  
  
3.  <span data-ttu-id="fa3a2-116">按一下資料表名稱旁邊的加號 [ **v Assoc Seq Line Items**]，以展開資料表並查看嵌套資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-116">Click the plus sign next to the table name, **v Assoc Seq Line Items**, to expand the table and view the columns from the nested table.</span></span>  
  
     <span data-ttu-id="fa3a2-117">新模型應該只包含下列資料行：</span><span class="sxs-lookup"><span data-stu-id="fa3a2-117">The new model should have only the following columns:</span></span>  
  
     <span data-ttu-id="fa3a2-118">**訂單 NumberKey**</span><span class="sxs-lookup"><span data-stu-id="fa3a2-118">**Order NumberKey**</span></span>  
  
     <span data-ttu-id="fa3a2-119">**行號索引鍵**</span><span class="sxs-lookup"><span data-stu-id="fa3a2-119">**Line Number Key**</span></span>  
  
     <span data-ttu-id="fa3a2-120">**模型預測**</span><span class="sxs-lookup"><span data-stu-id="fa3a2-120">**Model Predict**</span></span>  
  
### <a name="to-process-the-new-sequence-clustering-model"></a><span data-ttu-id="fa3a2-121">若要處理新的時序群集模型</span><span class="sxs-lookup"><span data-stu-id="fa3a2-121">To process the new sequence clustering model</span></span>  
  
1.  <span data-ttu-id="fa3a2-122">在 [**採礦模型**] 索引標籤中，以滑鼠右鍵按一下名為的新模型 `Sequence Clustering` ，然後選取 [**處理模型**]。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-122">In the **Mining Model** tab, right-click the new model named `Sequence Clustering`, and select **Process Model**.</span></span>  
  
     <span data-ttu-id="fa3a2-123">由於簡化的新採礦模型所根據的結構已經過處理，因此您不需要重新處理結構。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-123">Because the new simplified mining model is based on a structure that has already been processed, you do not need to reprocess the structure.</span></span> <span data-ttu-id="fa3a2-124">您可以只處理新的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-124">You can process just the new mining model.</span></span>  
  
2.  <span data-ttu-id="fa3a2-125">按一下 **[是]** ，將更新的資料採礦專案部署到伺服器。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-125">Click **Yes** to deploy the updated data mining project to the server.</span></span>  
  
3.  <span data-ttu-id="fa3a2-126">在 [**處理採礦模型**] 對話方塊中，按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-126">In the **Process Mining Model** dialog box, click **Run**.</span></span>  
  
4.  <span data-ttu-id="fa3a2-127">按一下 [**關閉**] 以關閉 [**處理進度**] 對話方塊，然後在 [**處理採礦模型**] 對話方塊中再次按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="fa3a2-127">Click **Close** to close the **Process Progress** dialog box, and then click **Close** again in the **Process Mining Model** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="fa3a2-128">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="fa3a2-128">Next Task in Lesson</span></span>  
 [<span data-ttu-id="fa3a2-129">在時序群集模型上建立預測 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="fa3a2-129">Creating Predictions on a Sequence Clustering Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/create-predictions-on-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="fa3a2-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa3a2-130">See Also</span></span>  
 [<span data-ttu-id="fa3a2-131">處理需求和考量 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="fa3a2-131">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
