---
title: 修改和處理購物籃模型 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b6019413-aebd-4ff7-831a-644572ad88b1
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 369de98e944c5ccf5d06ef61eaa16c06bb864e7b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584909"
---
# <a name="modifying-and-processing-the-market-basket-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="98a4d-102">修改及處理購物籃模型 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="98a4d-102">Modifying and Processing the Market Basket Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="98a4d-103">在處理您建立的關聯性採礦模型之前，您必須變更兩個參數的預設值： [*支援* *] 和 [* 機率]。</span><span class="sxs-lookup"><span data-stu-id="98a4d-103">Before you process the association mining model that you created, you must change the default values of two of the parameters: *Support* and *Probability*.</span></span>  
  
-   <span data-ttu-id="98a4d-104">*支援*定義規則在被視為有效之前必須存在的案例百分比。</span><span class="sxs-lookup"><span data-stu-id="98a4d-104">*Support* defines the percentage of cases in which a rule must exist before it is considered valid.</span></span> <span data-ttu-id="98a4d-105">您將會指定，至少必須在百分之 1 的案例中找到規則。</span><span class="sxs-lookup"><span data-stu-id="98a4d-105">You will specify that a rule must be found in at least 1 percent of cases.</span></span>  
  
-   <span data-ttu-id="98a4d-106">機率定義關聯在被視為有效之前*的可能性。*</span><span class="sxs-lookup"><span data-stu-id="98a4d-106">*Probability* defines how likely an association must be before it is considered valid.</span></span> <span data-ttu-id="98a4d-107">您將會考量機率至少百分之 10 的任何關聯。</span><span class="sxs-lookup"><span data-stu-id="98a4d-107">You will consider any association with a probability of at least 10 percent.</span></span>  
  
 <span data-ttu-id="98a4d-108">如需增加或減少支援和機率之影響的詳細資訊，請參閱[Microsoft 關聯分析演算法技術參考](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md)。</span><span class="sxs-lookup"><span data-stu-id="98a4d-108">For more information about the effects of increasing or decreasing support and probability, see [Microsoft Association Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-association-algorithm-technical-reference.md).</span></span>  
  
 <span data-ttu-id="98a4d-109">定義**關聯**性採礦模型的結構和參數之後，您將會處理此模型。</span><span class="sxs-lookup"><span data-stu-id="98a4d-109">After you have defined the structure and parameters for the **Association** mining model, you will process the model.</span></span>  
  
### <a name="to-adjust-the-parameters-of-the-association-model"></a><span data-ttu-id="98a4d-110">若要調整關聯模型的參數</span><span class="sxs-lookup"><span data-stu-id="98a4d-110">To adjust the parameters of the Association model</span></span>  
  
1.  <span data-ttu-id="98a4d-111">開啟資料採礦設計師的 [**採礦模型**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="98a4d-111">Open the **Mining Models** tab of Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="98a4d-112">在設計工具中，以滑鼠右鍵按一下方格中的 [**關聯**] 資料行，然後選取 **[設定演算法參數] 以開啟 [演算法參數**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="98a4d-112">Right-click the **Association** column in the grid in the designer and select **Set Algorithm Parameters to open the Algorithm Parameters** dialog box.</span></span>  
  
3.  <span data-ttu-id="98a4d-113">在 [**演算法參數**] 對話方塊的 [**值**] 資料行中，設定下列參數：</span><span class="sxs-lookup"><span data-stu-id="98a4d-113">In the **Value** column of the **Algorithm Parameters** dialog box, set the following parameters:</span></span>  
  
     <span data-ttu-id="98a4d-114">MINIMUM_PROBABILITY = 0.1 </span><span class="sxs-lookup"><span data-stu-id="98a4d-114">MINIMUM_PROBABILITY = 0.1</span></span>  
  
     <span data-ttu-id="98a4d-115">MINIMUM_SUPPORT = 0.01</span><span class="sxs-lookup"><span data-stu-id="98a4d-115">MINIMUM_SUPPORT = 0.01</span></span>  
  
4.  [!INCLUDE[clickOK](../includes/clickok-md.md)]  
  
### <a name="to-process-the-mining-model"></a><span data-ttu-id="98a4d-116">若要處理採礦模型</span><span class="sxs-lookup"><span data-stu-id="98a4d-116">To process the mining model</span></span>  
  
1.  <span data-ttu-id="98a4d-117">在的 [**採礦模型**] 功能表上 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，選取 [**處理採礦結構] 和 [所有模型]。**</span><span class="sxs-lookup"><span data-stu-id="98a4d-117">On the **Mining Model** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], select **Process Mining Structure and All Models.**</span></span>  
  
2.  <span data-ttu-id="98a4d-118">在詢問您是否要建立及部署專案的警告中，按一下 [**是]**。</span><span class="sxs-lookup"><span data-stu-id="98a4d-118">At the warning asking whether you want to build and deploy the project, click **Yes**.</span></span>  
  
     <span data-ttu-id="98a4d-119">[**進程採礦結構-關聯**] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="98a4d-119">The **Process Mining Structure - Association** dialog box opens.</span></span>  
  
3.  <span data-ttu-id="98a4d-120">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="98a4d-120">Click **Run**.</span></span>  
  
     <span data-ttu-id="98a4d-121">[**處理進度**] 對話方塊隨即開啟，以顯示模型處理的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="98a4d-121">The **Process Progress** dialog box opens to display information about model processing.</span></span> <span data-ttu-id="98a4d-122">處理新的結構和模型可能需要花一些時間。</span><span class="sxs-lookup"><span data-stu-id="98a4d-122">Processing of the new structure and model might take some time.</span></span>  
  
4.  <span data-ttu-id="98a4d-123">處理完成之後，按一下 [**關閉**] 以結束 [**處理進度**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="98a4d-123">After processing is complete, click **Close** to exit the **Process Progress** dialog box.</span></span>  
  
5.  <span data-ttu-id="98a4d-124">再按一次 [關閉]，**結束**[**處理常式採礦結構-關聯**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="98a4d-124">Click **Close** again to exit the **Process Mining Structure - Association** dialog box.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="98a4d-125">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="98a4d-125">Next Task in Lesson</span></span>  
 [<span data-ttu-id="98a4d-126">流覽購物籃模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="98a4d-126">Exploring the Market Basket Models &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/exploring-the-market-basket-models-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="98a4d-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="98a4d-127">See Also</span></span>  
 [<span data-ttu-id="98a4d-128">處理需求和考量 (資料採礦)</span><span class="sxs-lookup"><span data-stu-id="98a4d-128">Processing Requirements and Considerations &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)  
  
  
