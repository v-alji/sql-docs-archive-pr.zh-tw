---
title: 在結構資料上使用鑽取 (基本資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a693979c-0564-4d6d-b35d-cbbc8f350469
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 49a1ced27150676def541548f47a90a3f847c8ca
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584866"
---
# <a name="using-drillthrough-on-structure-data-basic-data-mining-tutorial"></a><span data-ttu-id="b8c8f-102">在結構資料上使用鑽研 (基本資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="b8c8f-102">Using Drillthrough on Structure Data (Basic Data Mining Tutorial)</span></span>
  <span data-ttu-id="b8c8f-103">作為其廣告行銷活動的一部分， [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 會傳送郵件給34-40 年齡人口統計中的潛在客戶。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-103">As part of their advertising campaign, [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] is sending a mailer to potential customers in the 34-40 age demographic.</span></span> <span data-ttu-id="b8c8f-104">行銷部門決定，他們也想要傳送郵件給五年以前曾經從 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 購買自行車的客戶。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-104">The marketing department has decided that they would also like to send the mailer to the customers who purchased bikes from [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] more than five years ago.</span></span> <span data-ttu-id="b8c8f-105">在這一課，您將會識別擁有比較舊的自行車的客戶，並擷取他們的連絡資訊。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-105">In this lesson you will identify customers with older bikes and retrieve their contact information.</span></span> <span data-ttu-id="b8c8f-106">此資訊不包括在模型中，但是會包括在結構中。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-106">This information is not included in the model, but is included in the structure.</span></span> <span data-ttu-id="b8c8f-107">若要擷取連絡資訊，您要先確定此結構已啟用鑽研，然後您將會使用鑽研來顯示目標客戶的姓名和地址。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-107">To retrieve the contact information you will first ensure that drillthrough is enabled for the structure and then you will use drillthrough to reveal the names and addresses of the targeted customers.</span></span>  
  
### <a name="to-enable-drillthrough-on-a-mining-model"></a><span data-ttu-id="b8c8f-108">針對採礦模型啟用鑽研</span><span class="sxs-lookup"><span data-stu-id="b8c8f-108">To enable drillthrough on a mining model</span></span>  
  
1.  <span data-ttu-id="b8c8f-109">在中 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，于資料採礦設計師的 [**採礦模型**] 索引標籤上，以滑鼠右鍵按一下 [ **TM_Decision_Tree** ] 模型，然後選取 [**屬性**]。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-109">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], on the **Mining Models** tab of Data Mining Designer, right-click the **TM_Decision_Tree** model, and select **Properties**.</span></span>  
  
2.  <span data-ttu-id="b8c8f-110">在 [屬性] 視窗中，按一下 **[AllowDrillThrough]**，然後選取 **[True]**。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-110">In the Properties windows, click **AllowDrillthrough**, and select **True**.</span></span>  
  
3.  <span data-ttu-id="b8c8f-111">在 [採礦模型] 索引標籤中，以滑鼠右鍵按一下模型，然後選取 [處理模型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-111">In the Mining Models tab, right-click the model, and select **Process Model**.</span></span>  
  
 <span data-ttu-id="b8c8f-112">如需詳細資訊，請參閱[&#40;資料採礦的鑽看查詢&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)</span><span class="sxs-lookup"><span data-stu-id="b8c8f-112">For more information, see [Drillthrough Queries &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/drillthrough-queries-data-mining.md)</span></span>  
  
### <a name="to-view-drillthrough-data-from-a-mining-model"></a><span data-ttu-id="b8c8f-113">若要檢視採礦模型中的鑽研資料</span><span class="sxs-lookup"><span data-stu-id="b8c8f-113">To view drillthrough data from a mining model</span></span>  
  
1.  <span data-ttu-id="b8c8f-114">在資料採礦設計師中，按一下 **[採礦模型檢視器]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-114">In Data Mining Designer, click the **Mining Model Viewer** tab.</span></span>  
  
2.  <span data-ttu-id="b8c8f-115">從 [**採礦模型**] 清單中選取**TM_Decision_Tree**模型。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-115">Select the **TM_Decision_Tree** model from the **Mining Model** list.</span></span>  
  
3.  <span data-ttu-id="b8c8f-116">將 [**背景**] 值變更為 `1` 。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-116">Change the **Background** value to `1`.</span></span> <span data-ttu-id="b8c8f-117">這樣就只會顯示模型中與購買自行車的客戶相關的部分。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-117">By doing this, you show only the part of the model that is related to customer who bought bikes.</span></span>  
  
4.  <span data-ttu-id="b8c8f-118">從 **[檢視器]** 清單中，選取 [Microsoft 樹狀檢視器]。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-118">Select the Microsoft Tree viewer from the **Viewer** list.</span></span> <span data-ttu-id="b8c8f-119">這樣會強制檢視器重新整理並顯示新的篩選條件。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-119">This will force the viewer to refresh with the new filter conditions.</span></span> <span data-ttu-id="b8c8f-120">然後，找出 [ **Age >= 34] 和 [<41** ] 節點，然後以滑鼠右鍵按一下該節點。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-120">Then, locate the **Age >=34 and <41** node and right-click the node.</span></span>  
  
5.  <span data-ttu-id="b8c8f-121">選取 **[鑽研]**，然後選取 **[模型和結構資料行]** ，開啟 **[鑽研]** 視窗。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-121">Select **Drill Through**, and then select **Model and Structure Columns** to open the **Drill Through** window.</span></span>  
  
6.  <span data-ttu-id="b8c8f-122">捲動到 **[Structure.Date First Purchase]** 資料行，檢視較舊的自行車的購買日期。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-122">Scroll to the **Structure.Date First Purchase** column to view the purchase dates for the older bikes.</span></span>  
  
7.  <span data-ttu-id="b8c8f-123">若要將資料複製到剪貼簿，請以滑鼠右鍵按一下資料表中的任何資料列，然後選取 [全部複製]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-123">To copy the data to the Clipboard, right-click any row in the table, and select **Copy All**.</span></span>  
  
 <span data-ttu-id="b8c8f-124">恭喜！您已順利完成基本資料採礦教學課程。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-124">Congratulations, you have completed the basic data mining tutorial.</span></span> <span data-ttu-id="b8c8f-125">現在您可以輕鬆地使用資料採礦工具，我們建議您最好也完成中繼資料採礦教學課程，其中會示範如何建立模型以供預測、購物籃分析和時序群集。</span><span class="sxs-lookup"><span data-stu-id="b8c8f-125">Now that you are comfortable using the data mining tools, we recommend that you also complete the intermediate data mining tutorial, which demonstrates how to create models for forecasting, market basket analysis, and sequence clustering.</span></span>  
  
## <a name="previous-task-in-lesson"></a><span data-ttu-id="b8c8f-126">本課程的前一項工作</span><span class="sxs-lookup"><span data-stu-id="b8c8f-126">Previous Task in Lesson</span></span>  
 [<span data-ttu-id="b8c8f-127">建立預測 &#40;資料採礦基本教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="b8c8f-127">Creating Predictions &#40;Basic Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-predictions-basic-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="b8c8f-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8c8f-128">See Also</span></span>  
 [<span data-ttu-id="b8c8f-129">使用預測查詢產生器來建立預測查詢</span><span class="sxs-lookup"><span data-stu-id="b8c8f-129">Create a Prediction Query Using the Prediction Query Builder</span></span>](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
