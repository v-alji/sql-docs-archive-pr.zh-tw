---
title: 建立時序群集採礦模型結構 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: e9339227-6c2e-4c4b-8be2-8c1960bc4a8d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 37d0a1738a758a9d8c4fd6b80310037937a9803f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594294"
---
# <a name="creating-a-sequence-clustering-mining-model-structure-intermediate-data-mining-tutorial"></a><span data-ttu-id="da6ab-102">建立時序群集採礦模型結構 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="da6ab-102">Creating a Sequence Clustering Mining Model Structure (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="da6ab-103">建立時序群集採礦模型的第一個步驟就是使用資料採礦精靈，根據 [!INCLUDE[msCoName](../includes/msconame-md.md)] 時序群集演算法來建立新的採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="da6ab-103">The first step in creating a sequence clustering mining model is to use the Data Mining Wizard to create a new mining structure and a mining model based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Sequence Clustering algorithm.</span></span>  
  
 <span data-ttu-id="da6ab-104">您將會使用與購物籃分析相同的資料來源檢視，但是您會加入一個包含 `sequence` 識別碼的資料行。</span><span class="sxs-lookup"><span data-stu-id="da6ab-104">You will use the same data source view that you used for the market basket analysis, but you will add a column that contains the `sequence` identifier.</span></span> <span data-ttu-id="da6ab-105">在此案例中，時序表示客戶將項目加入到購物籃的順序。</span><span class="sxs-lookup"><span data-stu-id="da6ab-105">In this scenario, the sequence means the order in which the customer added items to the shopping basket.</span></span>  
  
 <span data-ttu-id="da6ab-106">您也會加入某些資料行，這些資料行會在其中一個模型內使用，以根據人口統計資料來分組客戶。</span><span class="sxs-lookup"><span data-stu-id="da6ab-106">You will also add some columns that are used in one of the models to group customers by demographics.</span></span>  
  
### <a name="to-create-a-sequence-clustering-structure-and-model"></a><span data-ttu-id="da6ab-107">若要建立時序群集結構和模型</span><span class="sxs-lookup"><span data-stu-id="da6ab-107">To create a sequence clustering structure and model</span></span>  
  
1.  <span data-ttu-id="da6ab-108">在的方案總管中 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] ，以滑鼠右鍵按一下 [**採礦結構**]，然後選取 [**新增採礦結構**]。</span><span class="sxs-lookup"><span data-stu-id="da6ab-108">In Solution Explorer in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], right-click **Mining Structures** and select **New Mining Structure**.</span></span>  
  
2.  <span data-ttu-id="da6ab-109">在 **[歡迎使用資料採礦精靈]** 頁面上，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="da6ab-109">On the **Welcome to the Data Mining Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="da6ab-110">在 [**選取定義方法**] 頁面上，確認已選取 [**從現有的關係資料庫或資料倉儲**]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="da6ab-110">On the **Select the Definition Method** page, verify that **From existing relational database or data warehouse** is selected, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="da6ab-111">在 [**建立資料採礦結構**] 頁面上，確認已選取 [**使用採礦模型建立採礦結構**] 選項。</span><span class="sxs-lookup"><span data-stu-id="da6ab-111">On the **Create the Data Mining Structure** page, verify that the option **Create mining structure with a mining model** is selected.</span></span> <span data-ttu-id="da6ab-112">接下來，按一下 [**您要使用哪一項資料採礦技術？**] 選項的下拉式清單，然後選取 [ **Microsoft 時序群集**]。</span><span class="sxs-lookup"><span data-stu-id="da6ab-112">Next, click the dropdown list for the option, **Which data mining technique do you want to use?**, and select **Microsoft Sequence Clustering**.</span></span> <span data-ttu-id="da6ab-113">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="da6ab-113">Click **Next**.</span></span>  
  
     <span data-ttu-id="da6ab-114">[**選取資料來源視圖**] 頁面隨即出現。</span><span class="sxs-lookup"><span data-stu-id="da6ab-114">The **Select Data Source View** page appears.</span></span> <span data-ttu-id="da6ab-115">在 [**可用的資料來源視圖**] 底下，選取 `Orders` 。</span><span class="sxs-lookup"><span data-stu-id="da6ab-115">Under **Available data source views**, select `Orders`.</span></span>  
  
     <span data-ttu-id="da6ab-116">Orders 是您用於購物籃分析案例的相同資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="da6ab-116">Orders is the same data source view that you used for the market basket scenario.</span></span> <span data-ttu-id="da6ab-117">如果您尚未建立此資料來源視圖，請參閱[使用嵌套資料表加入資料來源視圖 &#40;中繼資料採礦教學課程&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="da6ab-117">If you have not created this data source view, see [Adding a Data Source View with Nested Tables &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/adding-a-data-source-view-with-nested-tables-intermediate-data-mining-tutorial.md).</span></span>  
  
5.  <span data-ttu-id="da6ab-118">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="da6ab-118">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="da6ab-119">在 [**指定資料表類型**] 頁面上，選取 [ **vAssocSeqOrders** ] 資料表旁的 [**案例**] 核取方塊，然後選取 [ **vAssocSeqLineItems** ] 資料表旁的 [**嵌套**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="da6ab-119">On the **Specify Table Types** page, select the **Case** check box next to the **vAssocSeqOrders** table, and select the **Nested** check box next to the **vAssocSeqLineItems** table.</span></span> <span data-ttu-id="da6ab-120">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="da6ab-120">Click **Next**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="da6ab-121">如果您選取 [**案例**] 或 [**嵌套**] 核取方塊時發生錯誤，可能是資料來源視圖中的聯結不正確。</span><span class="sxs-lookup"><span data-stu-id="da6ab-121">If an error occurs when you select the **Case** or **Nested** check boxes, it may be that the join in the data source view is not correct.</span></span> <span data-ttu-id="da6ab-122">**VAssocSeqLineItems**的嵌套資料表必須透過多對一聯結連接到案例資料表**vAssocSeqOrders** 。</span><span class="sxs-lookup"><span data-stu-id="da6ab-122">The nested table, **vAssocSeqLineItems**, must be connected to the case table, **vAssocSeqOrders,** by a many-to-one join.</span></span> <span data-ttu-id="da6ab-123">您可以用滑鼠右鍵按一下聯結線並反轉聯結的方向，藉以編輯關聯性。</span><span class="sxs-lookup"><span data-stu-id="da6ab-123">You can edit the relationship by right-clicking on the join line and then reversing the direction of the join.</span></span> <span data-ttu-id="da6ab-124">如需詳細資訊，請參閱[建立或編輯關聯性對話方塊 &#40;Analysis Services 多維度資料&#41;](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="da6ab-124">For more information, see [Create or Edit Relationship Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](../../2014/analysis-services/create-or-edit-relationship-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
7.  <span data-ttu-id="da6ab-125">在 [**指定定型資料**] 頁面上，選取核取方塊以選擇要用於模型的資料行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="da6ab-125">On the **Specify the Training Data** page, choose the columns for use in the model by selecting a check box as follows:</span></span>  
  
    -   <span data-ttu-id="da6ab-126">**IncomeGroup**選取 [**輸入**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="da6ab-126">**IncomeGroup** Select the **Input** check box.</span></span>  
  
         <span data-ttu-id="da6ab-127">這個資料行包含有關您可用於群集之客戶的有趣資訊。</span><span class="sxs-lookup"><span data-stu-id="da6ab-127">This column contains interesting information about the customers that you can use for clustering.</span></span> <span data-ttu-id="da6ab-128">您將會在第一個模型中使用它，然後在第二個模型中忽略它。</span><span class="sxs-lookup"><span data-stu-id="da6ab-128">You will use it in the first model and then ignore it in the second model.</span></span>  
  
    -   <span data-ttu-id="da6ab-129">**OrderNumber**選取此 `Key` 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="da6ab-129">**OrderNumber** Select the `Key` check box.</span></span>  
  
         <span data-ttu-id="da6ab-130">此欄位將會當做案例資料表的識別碼或 `Key` 使用。</span><span class="sxs-lookup"><span data-stu-id="da6ab-130">This field will be used as the identifier for the case table, or `Key`.</span></span> <span data-ttu-id="da6ab-131">一般來說，您絕對不應該使用案例資料表的索引鍵欄位當做輸入，因為此索引鍵包含對於群集沒什麼用處的唯一值。</span><span class="sxs-lookup"><span data-stu-id="da6ab-131">In general, you should never use the key field of the case table as an input, because the key contains unique values that are not useful for clustering.</span></span>  
  
    -   <span data-ttu-id="da6ab-132">**區域**選取 [**輸入**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="da6ab-132">**Region** Select the **Input** check box.</span></span>  
  
         <span data-ttu-id="da6ab-133">這個資料行包含有關您可用於群集之客戶的有趣資訊。</span><span class="sxs-lookup"><span data-stu-id="da6ab-133">This column contains interesting information about the customers that you can use for clustering.</span></span> <span data-ttu-id="da6ab-134">您將會在第一個模型中使用它，然後在第二個模型中忽略它。</span><span class="sxs-lookup"><span data-stu-id="da6ab-134">You will use it in the first model and then ignore it in the second model.</span></span>  
  
    -   <span data-ttu-id="da6ab-135">**LineNumber**選取 [] `Key` 和 [**輸入**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="da6ab-135">**LineNumber** Select the `Key` and **Input** check boxes.</span></span>  
  
         <span data-ttu-id="da6ab-136">**LineNumber**欄位將用來當做嵌套資料表的識別碼，或 `Sequence Key` 。</span><span class="sxs-lookup"><span data-stu-id="da6ab-136">The **LineNumber** field will be used as the identifier for the nested table, or `Sequence Key`.</span></span> <span data-ttu-id="da6ab-137">巢狀資料表的索引鍵永遠都必須用於輸入。</span><span class="sxs-lookup"><span data-stu-id="da6ab-137">The key for a nested table must always be used for input.</span></span>  
  
    -   <span data-ttu-id="da6ab-138">**模型**選取 [**輸入**] 和 [**可預測**] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="da6ab-138">**Model** Select the **Input** and **Predictable** check boxes.</span></span>  
  
     <span data-ttu-id="da6ab-139">確認選取範圍正確，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="da6ab-139">Verify that the selections are correct, and then click **Next**.</span></span>  
  
8.  <span data-ttu-id="da6ab-140">在 [**指定欄位的內容和資料類型**] 頁面上，確認方格包含下表所示的資料行、內容類型和資料類型，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="da6ab-140">On the **Specify Columns' Content and Data Type** page, verify that the grid contains the columns, content types, and data types shown in the following table, and then click **Next**.</span></span>  
  
    |<span data-ttu-id="da6ab-141">資料表/資料行</span><span class="sxs-lookup"><span data-stu-id="da6ab-141">Tables/Columns</span></span>|<span data-ttu-id="da6ab-142">內容類型</span><span class="sxs-lookup"><span data-stu-id="da6ab-142">Content Type</span></span>|<span data-ttu-id="da6ab-143">資料類型</span><span class="sxs-lookup"><span data-stu-id="da6ab-143">Data Type</span></span>|  
    |---------------------|------------------|---------------|  
    |<span data-ttu-id="da6ab-144">IncomeGroup</span><span class="sxs-lookup"><span data-stu-id="da6ab-144">IncomeGroup</span></span>|<span data-ttu-id="da6ab-145">Discrete</span><span class="sxs-lookup"><span data-stu-id="da6ab-145">Discrete</span></span>|<span data-ttu-id="da6ab-146">Text</span><span class="sxs-lookup"><span data-stu-id="da6ab-146">Text</span></span>|  
    |<span data-ttu-id="da6ab-147">OrderNumber</span><span class="sxs-lookup"><span data-stu-id="da6ab-147">OrderNumber</span></span>|<span data-ttu-id="da6ab-148">Key</span><span class="sxs-lookup"><span data-stu-id="da6ab-148">Key</span></span>|<span data-ttu-id="da6ab-149">Text</span><span class="sxs-lookup"><span data-stu-id="da6ab-149">Text</span></span>|  
    |<span data-ttu-id="da6ab-150">區域</span><span class="sxs-lookup"><span data-stu-id="da6ab-150">Region</span></span>|<span data-ttu-id="da6ab-151">Discrete</span><span class="sxs-lookup"><span data-stu-id="da6ab-151">Discrete</span></span>|<span data-ttu-id="da6ab-152">Text</span><span class="sxs-lookup"><span data-stu-id="da6ab-152">Text</span></span>|  
    |<span data-ttu-id="da6ab-153">vAssocSeqLineItems</span><span class="sxs-lookup"><span data-stu-id="da6ab-153">vAssocSeqLineItems</span></span>|||  
    |<span data-ttu-id="da6ab-154">Line Number</span><span class="sxs-lookup"><span data-stu-id="da6ab-154">Line Number</span></span>|<span data-ttu-id="da6ab-155">Key Sequence</span><span class="sxs-lookup"><span data-stu-id="da6ab-155">Key Sequence</span></span>|<span data-ttu-id="da6ab-156">long</span><span class="sxs-lookup"><span data-stu-id="da6ab-156">Long</span></span>|  
    |<span data-ttu-id="da6ab-157">模型</span><span class="sxs-lookup"><span data-stu-id="da6ab-157">Model</span></span>|<span data-ttu-id="da6ab-158">Discrete</span><span class="sxs-lookup"><span data-stu-id="da6ab-158">Discrete</span></span>|<span data-ttu-id="da6ab-159">Text</span><span class="sxs-lookup"><span data-stu-id="da6ab-159">Text</span></span>|  
  
9. <span data-ttu-id="da6ab-160">在 [**建立測試集**] 頁面上，將**測試的資料百分比**變更為20，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="da6ab-160">On the **Create Testing Set** page, change the **Percentage of data for testing** to 20, and then click **Next**.</span></span>  
  
10. <span data-ttu-id="da6ab-161">在 [**正在完成嚮導]** 頁面上，針對 [**採礦結構名稱**] 輸入 `Sequence Clustering with Region` 。</span><span class="sxs-lookup"><span data-stu-id="da6ab-161">On the **Completing the Wizard** page, for the **Mining structure name**, type `Sequence Clustering with Region`.</span></span>  
  
11. <span data-ttu-id="da6ab-162">針對 [**採礦模型名稱**]，輸入 `Sequence Clustering with Region` 。</span><span class="sxs-lookup"><span data-stu-id="da6ab-162">For the **Mining model name**, type `Sequence Clustering with Region`.</span></span>  
  
12. <span data-ttu-id="da6ab-163">勾選 [**允許流覽**] 方塊，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="da6ab-163">Check the **Allow drill through** box, and then click **Finish**.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="da6ab-164">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="da6ab-164">Next Task in Lesson</span></span>  
 [<span data-ttu-id="da6ab-165">處理時序群集模型</span><span class="sxs-lookup"><span data-stu-id="da6ab-165">Processing the Sequence Clustering Model</span></span>](../../2014/tutorials/processing-the-sequence-clustering-model.md)  
  
## <a name="see-also"></a><span data-ttu-id="da6ab-166">另請參閱</span><span class="sxs-lookup"><span data-stu-id="da6ab-166">See Also</span></span>  
 <span data-ttu-id="da6ab-167">[資料採礦設計工具](../../2014/analysis-services/data-mining/data-mining-designer.md) </span><span class="sxs-lookup"><span data-stu-id="da6ab-167">[Data Mining Designer](../../2014/analysis-services/data-mining/data-mining-designer.md) </span></span>  
 [<span data-ttu-id="da6ab-168">Microsoft 時序叢集演算法</span><span class="sxs-lookup"><span data-stu-id="da6ab-168">Microsoft Sequence Clustering Algorithm</span></span>](../../2014/analysis-services/data-mining/microsoft-sequence-clustering-algorithm.md)  
  
  
