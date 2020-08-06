---
title: 將新模型加入至目標郵寄結構 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 512c6888-60f1-46e4-9639-bc448395b8d7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b83dfc6c9e218eecf3f2abe636b8c24d69d1b507
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704502"
---
# <a name="adding-new-models-to-the-targeted-mailing-structure-basic-data-mining-tutorial"></a><span data-ttu-id="a420c-102">將新模型加入至目標郵寄結構 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="a420c-102">Adding New Models to the Targeted Mailing Structure (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="a420c-103">在這項工作中，您將使用資料採礦設計師的 [**採礦模型**] 索引標籤來定義兩個額外的模型。</span><span class="sxs-lookup"><span data-stu-id="a420c-103">In this task, you will define two additional models by using the **Mining Models** tab of Data Mining Designer.</span></span> <span data-ttu-id="a420c-104">您將會使用 Microsoft 群集和 Microsoft 貝氏機率分類演算法來建立模型。</span><span class="sxs-lookup"><span data-stu-id="a420c-104">You will use the Microsoft Clustering and Microsoft Naive Bayes algorithms to create the models.</span></span> <span data-ttu-id="a420c-105">之所以選擇這兩種演算法，是因為它們可以預測離散值 (例如自行車購買)。</span><span class="sxs-lookup"><span data-stu-id="a420c-105">These two algorithms are selected because of their ability to predict a discrete value (i.e., bike purchase).</span></span> <span data-ttu-id="a420c-106">如需這些演算法的詳細資訊，請參閱[Microsoft 群集演算法](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)和[Microsoft 貝氏貝氏機率分類演算法](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)</span><span class="sxs-lookup"><span data-stu-id="a420c-106">For more information about these algorithms, see [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md) and [Microsoft Naive Bayes Algorithm](../../2014/analysis-services/data-mining/microsoft-naive-bayes-algorithm.md)</span></span>  
  
### <a name="to-create-a-clustering-mining-model"></a><span data-ttu-id="a420c-107">若要建立群集採礦模型</span><span class="sxs-lookup"><span data-stu-id="a420c-107">To create a clustering mining model</span></span>  
  
1.  <span data-ttu-id="a420c-108">在中，切換至 [資料採礦設計師] 中的 [**採礦模型**] 索引標籤 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a420c-108">Switch to the **Mining Models** tab in Data Mining Designer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
     <span data-ttu-id="a420c-109">請注意，設計工具會顯示兩個數據行，一個用於「採礦結構」，另一個用於「 `TM_Decision_Tree` 採礦模型」（在上一課中建立）。</span><span class="sxs-lookup"><span data-stu-id="a420c-109">Notice that the designer displays two columns, one for the mining structure and one for the `TM_Decision_Tree` mining model, which you created in the previous lesson.</span></span>  
  
2.  <span data-ttu-id="a420c-110">以滑鼠右鍵按一下 [**結構**] 資料行，然後選取 [新增] [**採礦模型**]。</span><span class="sxs-lookup"><span data-stu-id="a420c-110">Right-click the **Structure** column and select **New Mining Model**.</span></span>  
  
3.  <span data-ttu-id="a420c-111">在 [**新增採礦模型**] 對話方塊的 [**模型名稱**] 中，輸入 `TM_Clustering` 。</span><span class="sxs-lookup"><span data-stu-id="a420c-111">In the **New Mining Model** dialog box, in **Model name**, type `TM_Clustering`.</span></span>  
  
4.  <span data-ttu-id="a420c-112">在 [**演算法名稱]** 中，選取 [ **Microsoft 群集**]。</span><span class="sxs-lookup"><span data-stu-id="a420c-112">In **Algorithm name**, select **Microsoft Clustering**.</span></span>  
  
5.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
 <span data-ttu-id="a420c-113">新的模型現在會出現在資料採礦設計師的 [**採礦模型**] 索引標籤中。</span><span class="sxs-lookup"><span data-stu-id="a420c-113">The new model now appears in the **Mining Models** tab of Data Mining Designer.</span></span> <span data-ttu-id="a420c-114">此模型是以叢集演算法為基礎 [!INCLUDE[msCoName](../includes/msconame-md.md)] ，將具有類似特性的客戶群組到叢集，並預測每個叢集的自行車購買。</span><span class="sxs-lookup"><span data-stu-id="a420c-114">This model, built with the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm, groups customers with similar characteristics into clusters and predicts bike buying for each cluster.</span></span> <span data-ttu-id="a420c-115">雖然您可以修改新模型的資料行使用方式和屬性，但在本教學課程中不需要對模型進行任何變更 `TM_Clustering` 。</span><span class="sxs-lookup"><span data-stu-id="a420c-115">Although you can modify the column usage and properties for the new model, no changes to the `TM_Clustering` model are necessary for this tutorial.</span></span>  
  
### <a name="to-create-a-naive-bayes-mining-model"></a><span data-ttu-id="a420c-116">若要建立貝氏機率分類採礦模型</span><span class="sxs-lookup"><span data-stu-id="a420c-116">To create a Naive Bayes mining model</span></span>  
  
1.  <span data-ttu-id="a420c-117">在資料採礦設計師的 [**採礦模型**] 索引標籤中，以滑鼠右鍵 clickthe**結構**資料行，然後選取 [新增] [**採礦模型**]。</span><span class="sxs-lookup"><span data-stu-id="a420c-117">In the **Mining Models** tab of Data Mining Designer, right-clickthe **Structure** column, and select **New Mining Model**.</span></span>  
  
2.  <span data-ttu-id="a420c-118">在 [**新增採礦模型**] 對話方塊的 [**模型名稱**] 下，輸入 `TM_NaiveBayes` 。</span><span class="sxs-lookup"><span data-stu-id="a420c-118">In the **New Mining Model** dialog box, under **Model name**, type `TM_NaiveBayes`.</span></span>  
  
3.  <span data-ttu-id="a420c-119">在 [**演算法名稱]** 中，選取 [ **Microsoft 貝氏貝氏機率分類**]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="a420c-119">In **Algorithm name**, select **Microsoft Naive Bayes**, then click **OK**.</span></span>  
  
     <span data-ttu-id="a420c-120">此時會出現一則訊息 [!INCLUDE[msCoName](../includes/msconame-md.md)] ，指出貝氏貝氏機率分類演算法不支援**Age**和**年收入**資料行，這是連續的。</span><span class="sxs-lookup"><span data-stu-id="a420c-120">A message appears stating that the [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes algorithm does not support the **Age** and **Yearly Income** columns, which are continuous.</span></span>  
  
4.  <span data-ttu-id="a420c-121">按一下 **[是]** 以確認訊息並繼續。</span><span class="sxs-lookup"><span data-stu-id="a420c-121">Click **Yes** to acknowledge the message and continue.</span></span>  
  
 <span data-ttu-id="a420c-122">新模型會出現在 [資料採礦設計師] 的 [**採礦模型**] 索引標籤中。</span><span class="sxs-lookup"><span data-stu-id="a420c-122">A new model appears in the **Mining Models** tab of Data Mining Designer.</span></span> <span data-ttu-id="a420c-123">雖然您可以修改此索引標籤中所有模型的資料行使用方式和屬性，但在本教學課程中不需要對模型進行任何變更 `TM_NaiveBayes` 。</span><span class="sxs-lookup"><span data-stu-id="a420c-123">Although you can modify the column usage and properties for all the models in this tab, no changes to the `TM_NaiveBayes` model are necessary for this tutorial.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="a420c-124">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="a420c-124">Next Task in Lesson</span></span>  
 [<span data-ttu-id="a420c-125">處理目標郵寄結構中的模型 &#40;基本資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="a420c-125">Processing Models in the Targeted Mailing Structure &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/processing-models-in-the-targeted-mailing-structure-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="a420c-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a420c-126">See Also</span></span>  
 <span data-ttu-id="a420c-127">[將採礦模型新增至結構 &#40;Analysis Services 資料採礦&#41;](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="a420c-127">[Add Mining Models to a Structure &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/add-mining-models-to-a-structure-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="a420c-128">[資料採礦設計工具](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="a420c-128">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 [<span data-ttu-id="a420c-129">移動資料採礦物件</span><span class="sxs-lookup"><span data-stu-id="a420c-129">Moving Data Mining Objects</span></span>](../../2014/analysis-services/data-mining/moving-data-mining-objects.md)  
  
  
