---
title: 建立購物籃結構和模型 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 659b7a4e-f687-44d9-a60a-86490ccbf90f
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b276fe5bed1d9df8e8b2e3e2826966b6abfb734e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584925"
---
# <a name="creating-a-market-basket-structure-and-model-intermediate-data-mining-tutorial"></a><span data-ttu-id="54d61-102">建立購物籃結構和模型 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="54d61-102">Creating a Market Basket Structure and Model (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="54d61-103">現在您已經建立了資料來源檢視，接著要使用資料採礦精靈建立新的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="54d61-103">Now that you have created a data source view, you will use the Data Mining Wizard to create a new mining structure.</span></span> <span data-ttu-id="54d61-104">在這項工作中，您將根據 [!INCLUDE[msCoName](../includes/msconame-md.md)] 關聯分析演算法建立一個採礦結構和一個採礦模型。</span><span class="sxs-lookup"><span data-stu-id="54d61-104">In this task, you will create a mining structure and a mining model that is based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="54d61-105">如果出現 vAssocSeqLineItems 無法當做巢狀資料表使用的錯誤訊息，請返回本課程的上一個工作，並務必從 vAssocSeqLineItems 資料表 (多方) 拖曳至 vAssocSeqOrders 資料表 (一方)，藉以建立多對一聯結。</span><span class="sxs-lookup"><span data-stu-id="54d61-105">If you encounter an error stating that vAssocSeqLineItems cannot be used as a nested table, return to the previous task in the lesson, and be sure to create the many-to-one join by dragging from the vAssocSeqLineItems table (the many side) to the vAssocSeqOrders table (the one side).</span></span> <span data-ttu-id="54d61-106">您也可以用滑鼠右鍵按一下聯結線，編輯資料表之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="54d61-106">You can also edit the relationship between the tables by right-clicking the join line.</span></span>  
  
### <a name="to-create-an-association-mining-structure"></a><span data-ttu-id="54d61-107">若要建立關聯採礦結構</span><span class="sxs-lookup"><span data-stu-id="54d61-107">To create an association mining structure</span></span>  
  
1.  <span data-ttu-id="54d61-108">在的方案總管中 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，以滑鼠右鍵按一下 [**採礦結構**]，然後選取 [新增] [**採礦結構**] 以開啟 [資料採礦嚮導]。</span><span class="sxs-lookup"><span data-stu-id="54d61-108">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click **Mining Structures** and select **New Mining Structure** to open the Data Mining Wizard.</span></span>  
  
2.  <span data-ttu-id="54d61-109">在 **[歡迎使用資料採礦精靈]** 頁面上，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="54d61-109">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="54d61-110">在 [**選取定義方法**] 頁面上，確認已選取 [**從現有的關係資料庫或資料倉儲**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="54d61-110">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="54d61-111">在 [**建立資料採礦結構**] 頁面上，于 [**您要使用哪一項資料採礦技術？**] 下，從清單中選取 [ **Microsoft 關聯規則**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="54d61-111">On the **Create the Data Mining Structure** page, under **Which data mining technique do you want to use?**, select **Microsoft Association Rules** from the list, and then click **Next**.</span></span> <span data-ttu-id="54d61-112">[**選取資料來源視圖**] 頁面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="54d61-112">The **Select Data Source View** page appears.</span></span>  
  
5.  <span data-ttu-id="54d61-113">在 [**可用的資料來源視圖**] 底下選取**訂單**，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="54d61-113">Select **Orders**under **Available data source views**, and then click **Next**.</span></span>  
  
6.  <span data-ttu-id="54d61-114">在 [**指定資料表類型**] 頁面的 [vAssocSeqLineItems] 資料表的資料列中，選取 [**嵌套**] 核取方塊，然後在 [嵌套資料表 vAssocSeqOrders] 的資料列中選取 [**案例**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="54d61-114">On the **Specify Table Types** page, in the row for the vAssocSeqLineItems table, select the **Nested** check box, and in the row for the nested table vAssocSeqOrders, select the **Case** check box.</span></span> <span data-ttu-id="54d61-115">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="54d61-115">Click **Next**.</span></span>  
  
7.  <span data-ttu-id="54d61-116">在 [**指定定型資料**] 頁面上，清除任何可能已核取的方塊。</span><span class="sxs-lookup"><span data-stu-id="54d61-116">On the **Specify the Training Data** page, clear any boxes that might be checked.</span></span> <span data-ttu-id="54d61-117">選取 [OrderNumber] 旁的 [索引**鍵**] 核取方塊，以設定案例資料表的索引鍵（vAssocSeqOrders）。</span><span class="sxs-lookup"><span data-stu-id="54d61-117">Set the key for the case table, vAssocSeqOrders, by selecting the **Key** check box next to OrderNumber.</span></span>  
  
     <span data-ttu-id="54d61-118">因為購物籃分析的目的是要判斷哪些產品包含在單一交易中，所以您不需要使用**CustomerKey**欄位。</span><span class="sxs-lookup"><span data-stu-id="54d61-118">Because the purpose of the market basket analysis is to determine which products are included in a single transaction, you do not have to use the **CustomerKey** field.</span></span>  
  
8.  <span data-ttu-id="54d61-119">選取 [模型] 旁的 [索引**鍵**] 核取方塊，以設定 vAssocSeqLineItems 嵌套資料表的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="54d61-119">Set the key for the nested table, vAssocSeqLineItems, by selecting the **Key** check box next to Model.</span></span> <span data-ttu-id="54d61-120">當您執行此動作時，也會自動選取 [**輸入**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="54d61-120">The **Input** check box is also automatically selected when you do this.</span></span> <span data-ttu-id="54d61-121">也請選取 [**可預測**] 核取方塊 `Model` 。</span><span class="sxs-lookup"><span data-stu-id="54d61-121">Select the **Predictable** check box for `Model` as well.</span></span>  
  
     <span data-ttu-id="54d61-122">在購物籃模型中，您不在意購物籃中的產品順序，因此您不應該將**LineNumber**納入為嵌套資料表的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="54d61-122">In a market basket model, you do not care about the sequence of products in the shopping basket, and therefore you should not include **LineNumber** as a key for the nested table.</span></span> <span data-ttu-id="54d61-123">在序列很重要的模型中，您只會使用**LineNumber**做為索引鍵。</span><span class="sxs-lookup"><span data-stu-id="54d61-123">You would use **LineNumber** as a key only in a model where the sequence is important.</span></span> <span data-ttu-id="54d61-124">您將在第 4 課建立一個使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 時序群集演算法的模型。</span><span class="sxs-lookup"><span data-stu-id="54d61-124">You will create a model that uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering algorithm in Lesson 4.</span></span>  
  
9. <span data-ttu-id="54d61-125">選取 IncomeGroup 和 Region 左邊的核取方塊，但不要選取其他任何選項。</span><span class="sxs-lookup"><span data-stu-id="54d61-125">Select the check box to the left of IncomeGroup and Region,but do not make any other selections.</span></span> <span data-ttu-id="54d61-126">檢查最左邊的資料行時，會將資料行加入到結構中供您日後參考，但是不會用於模型中。</span><span class="sxs-lookup"><span data-stu-id="54d61-126">Checking the leftmost column adds the columns to the structure for later reference, but the columns will not be used in the model.</span></span> <span data-ttu-id="54d61-127">您的選擇應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="54d61-127">Your selections should look like the following:</span></span>  
  
     <span data-ttu-id="54d61-128">![對話方塊應有的外觀](../../2014/tutorials/media/tutorial-configassocmodel.gif "對話方塊應有的外觀")</span><span class="sxs-lookup"><span data-stu-id="54d61-128">![how dialog box should look](../../2014/tutorials/media/tutorial-configassocmodel.gif "how dialog box should look")</span></span>  
  
10. <span data-ttu-id="54d61-129">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="54d61-129">Click **Next**.</span></span>  
  
11. <span data-ttu-id="54d61-130">在 [**指定欄位的內容和資料類型**] 頁面上，檢查選取專案，如下表所示，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="54d61-130">On the **Specify Columns' Content and Data Type**page, review the selections, which should be as shown in the following table, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="54d61-131">資料行</span><span class="sxs-lookup"><span data-stu-id="54d61-131">Columns</span></span>|<span data-ttu-id="54d61-132">內容類型</span><span class="sxs-lookup"><span data-stu-id="54d61-132">Content Type</span></span>|<span data-ttu-id="54d61-133">資料類型</span><span class="sxs-lookup"><span data-stu-id="54d61-133">Data Type</span></span>|  
    |-------------|------------------|---------------|  
    |<span data-ttu-id="54d61-134">IncomeGroup</span><span class="sxs-lookup"><span data-stu-id="54d61-134">IncomeGroup</span></span>|<span data-ttu-id="54d61-135">Discrete</span><span class="sxs-lookup"><span data-stu-id="54d61-135">Discrete</span></span>|<span data-ttu-id="54d61-136">Text</span><span class="sxs-lookup"><span data-stu-id="54d61-136">Text</span></span>|  
    |<span data-ttu-id="54d61-137">訂單編號</span><span class="sxs-lookup"><span data-stu-id="54d61-137">Order Number</span></span>|<span data-ttu-id="54d61-138">Key</span><span class="sxs-lookup"><span data-stu-id="54d61-138">Key</span></span>|<span data-ttu-id="54d61-139">Text</span><span class="sxs-lookup"><span data-stu-id="54d61-139">Text</span></span>|  
    |<span data-ttu-id="54d61-140">區域</span><span class="sxs-lookup"><span data-stu-id="54d61-140">Region</span></span>|<span data-ttu-id="54d61-141">Discrete</span><span class="sxs-lookup"><span data-stu-id="54d61-141">Discrete</span></span>|<span data-ttu-id="54d61-142">Text</span><span class="sxs-lookup"><span data-stu-id="54d61-142">Text</span></span>|  
    |<span data-ttu-id="54d61-143">vAssocSeqLineItems</span><span class="sxs-lookup"><span data-stu-id="54d61-143">vAssocSeqLineItems</span></span>|||  
    |<span data-ttu-id="54d61-144">模型</span><span class="sxs-lookup"><span data-stu-id="54d61-144">Model</span></span>|<span data-ttu-id="54d61-145">Key</span><span class="sxs-lookup"><span data-stu-id="54d61-145">Key</span></span>|<span data-ttu-id="54d61-146">Text</span><span class="sxs-lookup"><span data-stu-id="54d61-146">Text</span></span>|  
  
12. <span data-ttu-id="54d61-147">在 [**建立測試集**] 頁面上，[**測試資料的百分比**] 選項的預設值為30%。</span><span class="sxs-lookup"><span data-stu-id="54d61-147">On the **Create testing set** page, the default value for the option **Percentage of data for testing** is 30 percent.</span></span> <span data-ttu-id="54d61-148">將此變更為**0**。</span><span class="sxs-lookup"><span data-stu-id="54d61-148">Change this to **0**.</span></span> <span data-ttu-id="54d61-149">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="54d61-149">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] <span data-ttu-id="54d61-150">會提供不同的圖表來測量模型精確度。</span><span class="sxs-lookup"><span data-stu-id="54d61-150">provides different charts for measuring model accuracy.</span></span> <span data-ttu-id="54d61-151">不過，有些圖表類型 (例如增益圖和交叉驗證報告)，是專為分類和估計而設計。</span><span class="sxs-lookup"><span data-stu-id="54d61-151">However, some accuracy chart types, such as the lift chart and cross-validation report, are designed for classification and estimation.</span></span> <span data-ttu-id="54d61-152">這些方法不支援用於關聯式預測。</span><span class="sxs-lookup"><span data-stu-id="54d61-152">They are not supported for associative prediction.</span></span>  
  
13. <span data-ttu-id="54d61-153">在 [**正在完成嚮導]** 頁面的 [**採礦結構名稱**] 中，輸入 `Association` 。</span><span class="sxs-lookup"><span data-stu-id="54d61-153">On the **Completing the Wizard** page, in **Mining structure name**, type `Association`.</span></span>  
  
14. <span data-ttu-id="54d61-154">在 [**採礦模型名稱**] 中，輸入 `Association` 。</span><span class="sxs-lookup"><span data-stu-id="54d61-154">In **Mining model name**, type `Association`.</span></span>  
  
15. <span data-ttu-id="54d61-155">選取 [**允許深入流覽**] 選項，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="54d61-155">Select the option **Allow drill through**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="54d61-156">[資料採礦設計師] 隨即開啟，以顯示 `Association` 您剛建立的「採礦結構」。</span><span class="sxs-lookup"><span data-stu-id="54d61-156">Data Mining Designer opens to display the `Association` mining structure that you just created.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="54d61-157">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="54d61-157">Next Task in Lesson</span></span>  
 [<span data-ttu-id="54d61-158">修改和處理購物籃模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="54d61-158">Modifying and Processing the Market Basket Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/modify-process-market-basket-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="54d61-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="54d61-159">See Also</span></span>  
 <span data-ttu-id="54d61-160">[Microsoft 關聯分析演算法](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="54d61-160">[Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) </span></span>  
 [<span data-ttu-id="54d61-161">內容類型 &#40;資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="54d61-161">Content Types &#40;Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/content-types-data-mining.md)  
  
  
