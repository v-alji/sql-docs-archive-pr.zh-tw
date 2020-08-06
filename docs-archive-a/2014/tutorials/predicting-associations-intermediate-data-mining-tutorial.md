---
title: 預測關聯 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 9140c5f2-b340-45a6-9c27-d870d15aafea
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: bee5ca4ded1b2fd5cbda0712cb766c825b9d0318
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584902"
---
# <a name="predicting-associations-intermediate-data-mining-tutorial"></a><span data-ttu-id="0faec-102">預測關聯 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="0faec-102">Predicting Associations (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="0faec-103">當模型經過處理之後，您可以使用與模型中儲存的關聯有關的資訊來建立預測。</span><span class="sxs-lookup"><span data-stu-id="0faec-103">After the models have been processed, you can use the information about associations stored in the model to create predictions.</span></span> <span data-ttu-id="0faec-104">在本課程的最後一個工作中，您將會學習如何針對您所建立的關聯模型來建立預測查詢。</span><span class="sxs-lookup"><span data-stu-id="0faec-104">In the final task of this lesson, you learn how to build prediction queries against the association models that you created.</span></span> <span data-ttu-id="0faec-105">此課程假設您已熟悉如何使用預測查詢產生器，而且想要學習如何針對關聯模型來建立預測查詢。</span><span class="sxs-lookup"><span data-stu-id="0faec-105">This lesson assumes that you are familiar with how to use the Prediction Query Builder and want to learn how to build prediction queries against association models.</span></span> <span data-ttu-id="0faec-106">如需如何使用預測查詢產生器的詳細資訊，請參閱[資料採礦查詢介面](../../2014/analysis-services/data-mining/data-mining-query-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="0faec-106">For more information how to use Prediction Query Builder, see [Data Mining Query Interfaces](../../2014/analysis-services/data-mining/data-mining-query-tools.md).</span></span>  
  
## <a name="creating-a-singleton-prediction-query"></a><span data-ttu-id="0faec-107">建立單一預測查詢</span><span class="sxs-lookup"><span data-stu-id="0faec-107">Creating a Singleton Prediction Query</span></span>  
 <span data-ttu-id="0faec-108">關聯模型上的預測查詢可能非常實用：</span><span class="sxs-lookup"><span data-stu-id="0faec-108">Prediction queries on an association model can be very useful:</span></span>  
  
-   <span data-ttu-id="0faec-109">根據先前或相關的採購，向客戶推薦項目</span><span class="sxs-lookup"><span data-stu-id="0faec-109">Recommend items to a customer, based on prior or related purchases</span></span>  
  
-   <span data-ttu-id="0faec-110">尋找相關的事件。</span><span class="sxs-lookup"><span data-stu-id="0faec-110">Find related events.</span></span>  
  
-   <span data-ttu-id="0faec-111">識別一組交易中或跨一組交易的關聯性。</span><span class="sxs-lookup"><span data-stu-id="0faec-111">Identify relationships in or across sets of transactions.</span></span>  
  
 <span data-ttu-id="0faec-112">若要建立預測查詢，請先選取您想要使用的關聯模型，然後再指定輸入資料。</span><span class="sxs-lookup"><span data-stu-id="0faec-112">To build a prediction query, you first select the association model you want to use, and then you specify the input data.</span></span> <span data-ttu-id="0faec-113">輸入可以來自外部資料來源 (例如值的清單)，或者您可以建立單一查詢並提供值。</span><span class="sxs-lookup"><span data-stu-id="0faec-113">Inputs can come from an external data source, such as a list of values, or you can build a singleton query and provide values as you go.</span></span>  
  
 <span data-ttu-id="0faec-114">在此案例中，您會先建立某些單一預測查詢，大概了解預測的運作方式。</span><span class="sxs-lookup"><span data-stu-id="0faec-114">For this scenario, you will first create some singleton prediction queries, to get an idea of how prediction works.</span></span> <span data-ttu-id="0faec-115">然後您會建立批次預測的查詢，讓您用來根據客戶的目前購買項目來做出建議。</span><span class="sxs-lookup"><span data-stu-id="0faec-115">Then you will create a query for batch predictions that you could use for making recommendations based on a customer's current purchases.</span></span>  
  
#### <a name="to-create-a-prediction-query-on-an-association-model"></a><span data-ttu-id="0faec-116">若要在關聯模型上建立預測查詢</span><span class="sxs-lookup"><span data-stu-id="0faec-116">To create a prediction query on an association model</span></span>  
  
1.  <span data-ttu-id="0faec-117">按一下資料採礦設計師的 [**採礦模型預測**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0faec-117">Click the **Mining Model Prediction** tab of Data Mining Designer.</span></span>  
  
2.  <span data-ttu-id="0faec-118">在 [**採礦模型**] 窗格中，按一下 [**選取模型**]。</span><span class="sxs-lookup"><span data-stu-id="0faec-118">In the **Mining Model** pane, click **Select Model**.</span></span> <span data-ttu-id="0faec-119">(如果已選取正確的模型，您可以略過這個步驟和下一個步驟)。</span><span class="sxs-lookup"><span data-stu-id="0faec-119">(You can skip this step and the next step if the correct model is already selected.)</span></span>  
  
3.  <span data-ttu-id="0faec-120">在 [**選取採礦模型**] 對話方塊中，展開代表「採礦結構**關聯**」的節點，然後選取模型**關聯**。</span><span class="sxs-lookup"><span data-stu-id="0faec-120">In the **Select Mining Model** dialog box, expand the node that represents the mining structure **Association**, and select the model **Association**.</span></span> <span data-ttu-id="0faec-121">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="0faec-121">Click **OK**.</span></span>  
  
     <span data-ttu-id="0faec-122">現在可以忽略輸入窗格。</span><span class="sxs-lookup"><span data-stu-id="0faec-122">For now, you can ignore the input pane.</span></span>  
  
4.  <span data-ttu-id="0faec-123">在方格中，按一下 [**來源**] 底下的空白資料格，然後選取 [**預測函數]。**</span><span class="sxs-lookup"><span data-stu-id="0faec-123">In the grid, click the empty cell under **Source** and select **Prediction Function.**</span></span> <span data-ttu-id="0faec-124">在 [**欄位**] 底下的資料格中，選取 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="0faec-124">In the cell under **Field**, select `PredictAssociation`.</span></span>  
  
     <span data-ttu-id="0faec-125">您也可以使用**predict**函數來預測關聯。</span><span class="sxs-lookup"><span data-stu-id="0faec-125">You can also use the **Predict** function to predict associations.</span></span> <span data-ttu-id="0faec-126">如果您這樣做，請務必選擇採用資料表資料行做為引數的**Predict**函數版本。</span><span class="sxs-lookup"><span data-stu-id="0faec-126">If you do, be sure to choose the version of the **Predict** function that takes a table column as argument.</span></span>  
  
5.  <span data-ttu-id="0faec-127">在 [**採礦模型**] 窗格中，選取 [嵌套] 資料表 `vAssocSeqLineItems` ，並將它拖曳到方格中，指向函數的 [**準則/引數**] 方塊 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="0faec-127">In the **Mining Model** pane, select the nested table `vAssocSeqLineItems`, and drag it into the grid, to the **Criteria/Argument** box for the `PredictAssociation` function.</span></span>  
  
     <span data-ttu-id="0faec-128">拖曳資料表和資料行名稱可讓您建立複雜的陳述式，而不會產生語法錯誤。</span><span class="sxs-lookup"><span data-stu-id="0faec-128">Dragging and dropping table and column names lets you build complex statements without syntax errors.</span></span> <span data-ttu-id="0faec-129">不過，它會取代資料格的目前內容，其中包括函數的其他選擇性引數 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="0faec-129">However, it replaces the current contents of the cell, which include other optional arguments for the `PredictAssociation` function.</span></span> <span data-ttu-id="0faec-130">若要檢視其他引數，您可以暫時將此函數的第二個執行個體加入至方格內以供參考。</span><span class="sxs-lookup"><span data-stu-id="0faec-130">To view the other arguments, you can temporarily add a second instance of the function to the grid for reference.</span></span>  
  
6.  <span data-ttu-id="0faec-131">按一下 [**準則/引數**] 方塊，並在資料表名稱後面輸入下列文字：`,3`</span><span class="sxs-lookup"><span data-stu-id="0faec-131">Click the **Criteria/Argument** box and type the following text after the table name: `,3`</span></span>  
  
     <span data-ttu-id="0faec-132">[**準則/引數**] 方塊中的完整文字應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="0faec-132">The complete text in the **Criteria/Argument** box should be as follows:</span></span>  
  
     `[Association].[v Assoc Seq Line Items],3`  
  
7.  <span data-ttu-id="0faec-133">按一下預測查詢產生器上方角落的 [**結果**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0faec-133">Click the **Results** button in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="0faec-134">預期的結果會包含具有標題**運算式**的單一資料行。</span><span class="sxs-lookup"><span data-stu-id="0faec-134">The expected results contain a single column with the heading **Expression**.</span></span> <span data-ttu-id="0faec-135">[**運算式**] 資料行包含具有單一資料行和下列三個數據列的嵌套資料表。</span><span class="sxs-lookup"><span data-stu-id="0faec-135">The **Expression** column contains a nested table with a single column and the following three rows.</span></span> <span data-ttu-id="0faec-136">因為您未指定輸入值，所以這些預測代表整體而言，此型號最有可能的產品關聯。</span><span class="sxs-lookup"><span data-stu-id="0faec-136">Because you did not specify an input value, these predictions represent the most likely product associations for the model as a whole.</span></span>  
  
|<span data-ttu-id="0faec-137">模型</span><span class="sxs-lookup"><span data-stu-id="0faec-137">Model</span></span>|  
|-----------|  
|<span data-ttu-id="0faec-138">Women's Mountain Shorts</span><span class="sxs-lookup"><span data-stu-id="0faec-138">Women's Mountain Shorts</span></span>|  
|<span data-ttu-id="0faec-139">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="0faec-139">Water Bottle</span></span>|  
|<span data-ttu-id="0faec-140">Touring-3000</span><span class="sxs-lookup"><span data-stu-id="0faec-140">Touring-3000</span></span>|  
  
 <span data-ttu-id="0faec-141">接下來，您將使用 [**單一查詢輸入**] 窗格，將產品指定為查詢的輸入，並查看最有可能與該專案相關聯的產品。</span><span class="sxs-lookup"><span data-stu-id="0faec-141">Next, you will use the **Singleton Query Input** pane to specify a product as input to the query, and view the products that are most likely associated with that item.</span></span>  
  
#### <a name="to-create-a-singleton-prediction-query-with-nested-table-inputs"></a><span data-ttu-id="0faec-142">若要使用巢狀資料表輸入建立單一預測查詢</span><span class="sxs-lookup"><span data-stu-id="0faec-142">To create a singleton prediction query with nested table inputs</span></span>  
  
1.  <span data-ttu-id="0faec-143">按一下預測查詢產生器角落的 [**設計**] 按鈕，切換回查詢建立方格。</span><span class="sxs-lookup"><span data-stu-id="0faec-143">Click the **Design** button in the corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="0faec-144">在 [**採礦模型**] 功能表上，選取 [**單一查詢**]。</span><span class="sxs-lookup"><span data-stu-id="0faec-144">On the **Mining Model** menu, select **Singleton Query**.</span></span>  
  
3.  <span data-ttu-id="0faec-145">在 [**採礦模型**] 對話方塊中，選取 [**關聯**] 模型。</span><span class="sxs-lookup"><span data-stu-id="0faec-145">In the **Mining Model** dialog box, select the **Association** model.</span></span>  
  
4.  <span data-ttu-id="0faec-146">在方格中，按一下 [**來源**] 底下的空白資料格，然後選取 [**預測函數]。**</span><span class="sxs-lookup"><span data-stu-id="0faec-146">In the grid, click the empty cell under **Source** and select **Prediction Function.**</span></span> <span data-ttu-id="0faec-147">在 [**欄位**] 底下的資料格中，選取 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="0faec-147">In the cell under **Field**, select `PredictAssociation`.</span></span>  
  
5.  <span data-ttu-id="0faec-148">在 [**採礦模型**] 窗格中，選取 [嵌套] 資料表 `vAssocSeqLineItems` ，並將它拖曳到方格中，指向函數的 [**準則/引數**] 方塊 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="0faec-148">In the **Mining Model** pane, select the nested table `vAssocSeqLineItems`, and drag it into the grid, to the **Criteria/Argument** box for the `PredictAssociation` function.</span></span> <span data-ttu-id="0faec-149">在 `,3` 嵌套的資料表名稱後面輸入，如同上一個程式所示。</span><span class="sxs-lookup"><span data-stu-id="0faec-149">Type `,3` after the nested table name just as in the previous procedure.</span></span>  
  
6.  <span data-ttu-id="0faec-150">在 [**單一查詢輸入**] 對話方塊中，按一下 [ **VAssoc Seq Line Items**] 旁的 [**值**] 方塊，然後按一下 [ \*\* ( ... ) \*\* ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0faec-150">In the **Singleton Query Input** dialog box, click the **Value** box next to **vAssoc Seq Line Items**, and then click the **(...)** button.</span></span>  
  
7.  <span data-ttu-id="0faec-151">在 [**嵌套資料表輸入**] 對話方塊中，選取 `Touring Tire` [索引鍵資料**行**] 窗格中的，然後按一下 [**加入**]。</span><span class="sxs-lookup"><span data-stu-id="0faec-151">In the **Nested Table Input** dialog box, select `Touring Tire` in the **Key column** pane, and then click **Add**.</span></span>  
  
8.  <span data-ttu-id="0faec-152">按一下 [**結果**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0faec-152">Click the **Results** button.</span></span>  
  
 <span data-ttu-id="0faec-153">結果現在會顯示最有可能與 Touring Tire 產生關聯之產品的預測。</span><span class="sxs-lookup"><span data-stu-id="0faec-153">The results now show the predictions for products that are most likely associated with the Touring Tire.</span></span>  
  
|<span data-ttu-id="0faec-154">模型</span><span class="sxs-lookup"><span data-stu-id="0faec-154">Model</span></span>|  
|-----------|  
|<span data-ttu-id="0faec-155">Touring Tire Tube</span><span class="sxs-lookup"><span data-stu-id="0faec-155">Touring Tire Tube</span></span>|  
|<span data-ttu-id="0faec-156">Sport-100</span><span class="sxs-lookup"><span data-stu-id="0faec-156">Sport-100</span></span>|  
|<span data-ttu-id="0faec-157">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="0faec-157">Water Bottle</span></span>|  
  
 <span data-ttu-id="0faec-158">但是，您已經從模型的瀏覽知道 Touring Tire Tube 經常會與 Touring Tire 一起被購買；您比較有興趣知道，您可以向購買這些產品的客戶推薦可以一起購買哪些產品。</span><span class="sxs-lookup"><span data-stu-id="0faec-158">However, you already know from exploring the model that the Touring Tire Tube is frequently purchased with the Touring Tire; you are more interested in knowing what products you can recommend to customers who purchase these items together.</span></span> <span data-ttu-id="0faec-159">您將會變更此查詢，好讓它根據購物籃中的兩個項目預測相關產品。</span><span class="sxs-lookup"><span data-stu-id="0faec-159">You will change the query so that it predicts related products based on two items in the basket.</span></span> <span data-ttu-id="0faec-160">您也將修改此查詢，為每一個預測的產品增加機率。</span><span class="sxs-lookup"><span data-stu-id="0faec-160">You will also modify the query to add the probability for each predicted product.</span></span>  
  
#### <a name="to-add-inputs-and-probabilities-to-the-singleton-prediction-query"></a><span data-ttu-id="0faec-161">若要在單一預測查詢中加入輸入和機率</span><span class="sxs-lookup"><span data-stu-id="0faec-161">To add inputs and probabilities to the singleton prediction query</span></span>  
  
1.  <span data-ttu-id="0faec-162">按一下預測查詢產生器角落的 [**設計**] 按鈕，切換回查詢建立方格。</span><span class="sxs-lookup"><span data-stu-id="0faec-162">Click the **Design** button in the corner of the Prediction Query Builder to switch back to the query building grid.</span></span>  
  
2.  <span data-ttu-id="0faec-163">在 [**單一查詢輸入**] 對話方塊中，按一下 [ **VAssoc Seq Line Items**] 旁的 [**值**] 方塊，然後按一下 [ \*\* ( ... ) \*\* ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0faec-163">In the **Singleton Query Input** dialog box, click the **Value** box next to **vAssoc Seq Line Items**, and then click the **(...)** button.</span></span>  
  
3.  <span data-ttu-id="0faec-164">在 [索引**鍵資料行**] 窗格中，選取 [] `Touring Tire` ，然後按一下 [**新增**]。</span><span class="sxs-lookup"><span data-stu-id="0faec-164">In the **Key column** pane, select `Touring Tire`, and then click **Add**.</span></span>  
  
4.  <span data-ttu-id="0faec-165">在方格中，按一下 [**來源**] 底下的空白資料格，然後選取 [**預測函數]。**</span><span class="sxs-lookup"><span data-stu-id="0faec-165">In the grid, click the empty cell under **Source** and select **Prediction Function.**</span></span> <span data-ttu-id="0faec-166">在 [**欄位**] 底下的資料格中，選取 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="0faec-166">In the cell under **Field**, select `PredictAssociation`.</span></span>  
  
5.  <span data-ttu-id="0faec-167">在 [**採礦模型**] 窗格中，選取 [嵌套] 資料表 `vAssocSeqLineItems` ，並將它拖曳到方格中，指向函數的 [**準則/引數**] 方塊 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="0faec-167">In the **Mining Model** pane, select the nested table `vAssocSeqLineItems`, and drag it into the grid, to the **Criteria/Argument** box for the `PredictAssociation` function.</span></span> <span data-ttu-id="0faec-168">在 `,3` 嵌套的資料表名稱後面輸入，如同上一個程式所示。</span><span class="sxs-lookup"><span data-stu-id="0faec-168">Type `,3` after the nested table name just as in the previous procedure.</span></span>  
  
6.  <span data-ttu-id="0faec-169">在 [**嵌套資料表輸入**] 對話方塊中，選取 `Touring Tire Tube` [索引鍵資料**行**] 窗格中的，然後按一下 [**加入**]。</span><span class="sxs-lookup"><span data-stu-id="0faec-169">In the **Nested Table Input** dialog box, select `Touring Tire Tube` in the **Key column** pane, and then click **Add**.</span></span>  
  
7.  <span data-ttu-id="0faec-170">在方格中，于函數的資料列中 `PredictAssociation` ，按一下 [**準則/引數**] 方塊，然後變更引數以加入引數 INCLUDE_STATISTICS。</span><span class="sxs-lookup"><span data-stu-id="0faec-170">In the grid, in the row for the `PredictAssociation` function, click the **Criteria/Argument** box, and change the arguments to add the argument, INCLUDE_STATISTICS.</span></span>  
  
     <span data-ttu-id="0faec-171">[**準則/引數**] 方塊中的完整文字應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="0faec-171">The complete text in the **Criteria/Argument** box should be as follows:</span></span>  
  
     `[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`  
  
8.  <span data-ttu-id="0faec-172">按一下 [**結果**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0faec-172">Click the **Results** button.</span></span>  
  
 <span data-ttu-id="0faec-173">巢狀資料表中的結果現在會變更為顯示預測，連同支援和機率。</span><span class="sxs-lookup"><span data-stu-id="0faec-173">The results in the nested table now change to show the predictions, together with support and probability.</span></span> <span data-ttu-id="0faec-174">如需如何解讀這些值的詳細資訊，請參閱[關聯模型的採礦模型內容 &#40;Analysis Services 資料採礦&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="0faec-174">For more information about how to interpret these values, see [Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md).</span></span>  
  
|<span data-ttu-id="0faec-175">模型</span><span class="sxs-lookup"><span data-stu-id="0faec-175">Model</span></span>|<span data-ttu-id="0faec-176">$SUPPORT</span><span class="sxs-lookup"><span data-stu-id="0faec-176">$SUPPORT</span></span>|<span data-ttu-id="0faec-177">$PROBABILITY</span><span class="sxs-lookup"><span data-stu-id="0faec-177">$PROBABILITY</span></span>|<span data-ttu-id="0faec-178">$ADJUSTEDPROBABILITY</span><span class="sxs-lookup"><span data-stu-id="0faec-178">$ADJUSTEDPROBABILITY</span></span>|  
|-----------|--------------|------------------|--------------------------|  
|<span data-ttu-id="0faec-179">Sport-100</span><span class="sxs-lookup"><span data-stu-id="0faec-179">Sport-100</span></span>|<span data-ttu-id="0faec-180">4334</span><span class="sxs-lookup"><span data-stu-id="0faec-180">4334</span></span>|<span data-ttu-id="0faec-181">0.291 .。。</span><span class="sxs-lookup"><span data-stu-id="0faec-181">0.291...</span></span>|<span data-ttu-id="0faec-182">0.252 .。。</span><span class="sxs-lookup"><span data-stu-id="0faec-182">0.252...</span></span>|  
|<span data-ttu-id="0faec-183">Water Bottle</span><span class="sxs-lookup"><span data-stu-id="0faec-183">Water Bottle</span></span>|<span data-ttu-id="0faec-184">2866</span><span class="sxs-lookup"><span data-stu-id="0faec-184">2866</span></span>|<span data-ttu-id="0faec-185">0.192 .。。</span><span class="sxs-lookup"><span data-stu-id="0faec-185">0.192...</span></span>|<span data-ttu-id="0faec-186">0.175 .。。</span><span class="sxs-lookup"><span data-stu-id="0faec-186">0.175...</span></span>|  
|<span data-ttu-id="0faec-187">Patch Kit</span><span class="sxs-lookup"><span data-stu-id="0faec-187">Patch Kit</span></span>|<span data-ttu-id="0faec-188">2113</span><span class="sxs-lookup"><span data-stu-id="0faec-188">2113</span></span>|<span data-ttu-id="0faec-189">0.142 .。。</span><span class="sxs-lookup"><span data-stu-id="0faec-189">0.142...</span></span>|<span data-ttu-id="0faec-190">0.132</span><span class="sxs-lookup"><span data-stu-id="0faec-190">0.132</span></span>|  
  
## <a name="working-with-results"></a><span data-ttu-id="0faec-191">使用結果</span><span class="sxs-lookup"><span data-stu-id="0faec-191">Working with Results</span></span>  
 <span data-ttu-id="0faec-192">當結果中有許多巢狀資料表時，您可能會想要扁平化結果，以方便檢視。</span><span class="sxs-lookup"><span data-stu-id="0faec-192">When there are many nested tables in the results, you might want to flatten the results for easier viewing.</span></span> <span data-ttu-id="0faec-193">若要這樣做，您可以手動修改查詢，並加入 `FLATTENED` 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="0faec-193">To do this, you can manually modify the query and add the `FLATTENED` keyword.</span></span>  
  
#### <a name="to-flatten-nested-rowsets-in-a-prediction-query"></a><span data-ttu-id="0faec-194">若要扁平化預測查詢中的巢狀資料列集</span><span class="sxs-lookup"><span data-stu-id="0faec-194">To flatten nested rowsets in a prediction query</span></span>  
  
1.  <span data-ttu-id="0faec-195">按一下「預測查詢產生器」角落的 [ **SQL** ] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0faec-195">Click the **SQL** button in the corner of the Prediction Query Builder.</span></span>  
  
     <span data-ttu-id="0faec-196">此方格會變成開啟的窗格，您可以在此窗格中檢視及修改之前由預測查詢產生器所建立的 DMX 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0faec-196">The grid changes to an open pane where you can view and modify the DMX statement that was created by the Prediction Query Builder.</span></span>  
  
2.  <span data-ttu-id="0faec-197">在 `SELECT` 關鍵字之後輸入 `FLATTENED`。</span><span class="sxs-lookup"><span data-stu-id="0faec-197">After the `SELECT` keyword, type `FLATTENED`.</span></span>  
  
     <span data-ttu-id="0faec-198">此查詢的完整文字應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="0faec-198">The complete text of the query should be as follows:</span></span>  
  
    ```  
    SELECT FLATTENED  
      PredictAssociation([Association].[v Assoc Seq Line Items],INCLUDE_STATISTICS,3)  
    FROM  
      [Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Touring Tire' AS [Model]  
      UNION SELECT 'Touring Tire Tube' AS [Model]) AS [v Assoc Seq Line Items]) AS t  
    ```  
  
3.  <span data-ttu-id="0faec-199">按一下預測查詢產生器上方角落的 [**結果**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0faec-199">Click the **Results** button in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="0faec-200">現在您已經手動編輯了查詢，如果您切換回 [設計] 檢視，一定會遺失變更。</span><span class="sxs-lookup"><span data-stu-id="0faec-200">Note that after you have manually edited a query, you will not be able to switch back to Design view without losing the changes.</span></span> <span data-ttu-id="0faec-201">如果您想要儲存查詢，可以將您手動建立的 DMX 陳述式複製到文字檔。</span><span class="sxs-lookup"><span data-stu-id="0faec-201">If you wish to save the query, you can copy the DMX statement that you created manually to a text file.</span></span> <span data-ttu-id="0faec-202">當您變更回 [設計] 檢視後，此查詢會還原成之前在 [設計] 檢視中有效的上一個版本。</span><span class="sxs-lookup"><span data-stu-id="0faec-202">When you change back to Design view, the query is reverted to the last version that was valid in Design view.</span></span>  
  
## <a name="creating-multiple-predictions"></a><span data-ttu-id="0faec-203">建立多個預測</span><span class="sxs-lookup"><span data-stu-id="0faec-203">Creating Multiple Predictions</span></span>  
 <span data-ttu-id="0faec-204">假設您想要知道個別客戶的最佳預測 (根據過去購買的產品)。</span><span class="sxs-lookup"><span data-stu-id="0faec-204">Suppose you want to know the best predictions for individual customers, based on past purchases.</span></span> <span data-ttu-id="0faec-205">您可以使用外部資料當做預測查詢的輸入，例如包含客戶識別碼和最近購買之產品的資料表。</span><span class="sxs-lookup"><span data-stu-id="0faec-205">You can use external data as input to the prediction query, such as tables containing the customer ID and the most recent product purchases.</span></span> <span data-ttu-id="0faec-206">其需求是資料表必須已經定義為 Analysis Services 資料來源檢視，而且輸入資料必須包含案例和巢狀資料表 (就像模型中使用的資料表)。</span><span class="sxs-lookup"><span data-stu-id="0faec-206">The requirements are that the data tables be already defined as an Analysis Services data source view; moreover, the input data must contain case and nested tables like those used in the model.</span></span> <span data-ttu-id="0faec-207">它們不需要同名，但是結構必須類似。</span><span class="sxs-lookup"><span data-stu-id="0faec-207">They need not have the same names, but the structure must be similar.</span></span> <span data-ttu-id="0faec-208">基於這個教學課程的目的，您將會使用此模型定型所在的原始資料表。</span><span class="sxs-lookup"><span data-stu-id="0faec-208">For the purpose of this tutorial, you will use the original tables on which the model was trained.</span></span>  
  
#### <a name="to-change-the-input-method-for-the-prediction-query"></a><span data-ttu-id="0faec-209">若要變更預測查詢的輸入方法</span><span class="sxs-lookup"><span data-stu-id="0faec-209">To change the input method for the prediction query</span></span>  
  
1.  <span data-ttu-id="0faec-210">在 [**採礦模型**] 功能表中，再次選取 [**單一查詢**]，以清除核取記號。</span><span class="sxs-lookup"><span data-stu-id="0faec-210">In the **Mining Model** menu, select **Singleton Query** again, to clear the check mark.</span></span>  
  
2.  <span data-ttu-id="0faec-211">隨即出現一則錯誤訊息，警告您單一查詢將會遺失。</span><span class="sxs-lookup"><span data-stu-id="0faec-211">An error message appears warning that your singleton query will be lost.</span></span> <span data-ttu-id="0faec-212">按一下 [是] 。</span><span class="sxs-lookup"><span data-stu-id="0faec-212">Click **Yes**.</span></span>  
  
     <span data-ttu-id="0faec-213">輸入對話方塊的名稱會變更為 [\*\*選取輸入資料表] (s) \*\*。</span><span class="sxs-lookup"><span data-stu-id="0faec-213">The name of the input dialog box changes to **Select Input Table(s)**.</span></span>  
  
 <span data-ttu-id="0faec-214">因為您對於建立預測查詢來提供客戶識別碼和產品清單當做輸入很感興趣，所以您將會加入客戶資料表當做案例資料表，並加入購買資料表當做巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="0faec-214">Because you are interested in creating a prediction query that provides Customer ID and a list of products as input, you will add the customer table as the case table, and the purchases table as the nested table.</span></span> <span data-ttu-id="0faec-215">然後您會加入預測函數來產生建議。</span><span class="sxs-lookup"><span data-stu-id="0faec-215">Then you will add prediction functions to create recommendations.</span></span>  
  
#### <a name="to-create-a-prediction-query-using-nested-table-inputs"></a><span data-ttu-id="0faec-216">若要使用巢狀資料表輸入來建立預測查詢</span><span class="sxs-lookup"><span data-stu-id="0faec-216">To create a prediction query using nested table inputs</span></span>  
  
1.  <span data-ttu-id="0faec-217">在 [採礦模型] 窗格上，選取 [篩選的關聯] 模型。</span><span class="sxs-lookup"><span data-stu-id="0faec-217">In the Mining Model pane, select the Association Filtered model.</span></span>  
  
2.  <span data-ttu-id="0faec-218">在 [**選取輸入資料表 (s) \*\* ] 對話方塊中，按一下 [**選取案例資料表\*\*]。</span><span class="sxs-lookup"><span data-stu-id="0faec-218">In the **Select Input Table(s)** dialog box, click **Select Case Table**.</span></span>  
  
3.  <span data-ttu-id="0faec-219">在 [**選取資料表**] 對話方塊中，針對 [**資料來源**] 選取 [AdventureWorksDW2008]。</span><span class="sxs-lookup"><span data-stu-id="0faec-219">In the **Select Table** dialog box, for **Data Source**, select AdventureWorksDW2008.</span></span> <span data-ttu-id="0faec-220">在 [**資料表/視圖名稱**] 清單中，選取 [vAssocSeqOrders]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0faec-220">In the **Table/View Name** list, select vAssocSeqOrders, and then click **OK**.</span></span>  
  
     <span data-ttu-id="0faec-221">vAssocSeqOrders 資料表就會加入此窗格中。</span><span class="sxs-lookup"><span data-stu-id="0faec-221">The table vAssocSeqOrders is added to the pane.</span></span>  
  
4.  <span data-ttu-id="0faec-222">在 [**選取輸入資料表 (s) \*\* ] 對話方塊中，按一下 [**選取嵌套資料表\*\*]。</span><span class="sxs-lookup"><span data-stu-id="0faec-222">In the **Select Input Table(s)** dialog box, click **Select Nested Table**.</span></span>  
  
5.  <span data-ttu-id="0faec-223">在 [**選取資料表**] 對話方塊中，針對 [**資料來源**] 選取 [AdventureWorksDW2008]。</span><span class="sxs-lookup"><span data-stu-id="0faec-223">In the **Select Table** dialog box, for **Data Source**, select AdventureWorksDW2008.</span></span> <span data-ttu-id="0faec-224">在 [**資料表/視圖名稱**] 清單中，選取 [vAssocSeqLineItems]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0faec-224">In the **Table/View name** list, select vAssocSeqLineItems, and then click **OK**.</span></span>  
  
     <span data-ttu-id="0faec-225">vAssocSeqLineItems 資料表就會加入此窗格中。</span><span class="sxs-lookup"><span data-stu-id="0faec-225">The table vAssocSeqLineItems is added to the pane.</span></span>  
  
6.  <span data-ttu-id="0faec-226">在 [**指定嵌套聯結**] 對話方塊中，從案例資料表拖曳 [OrderNumber] 欄位，並將它放到嵌套資料表的 [OrderNumber] 欄位中。</span><span class="sxs-lookup"><span data-stu-id="0faec-226">In the **Specify Nested Join** dialog box, drag the OrderNumber field from the case table and drop it onto the OrderNumber field in the nested table.</span></span>  
  
     <span data-ttu-id="0faec-227">您也可以按一下 [**新增關聯**性]，並從清單中選取資料行來建立關聯性。</span><span class="sxs-lookup"><span data-stu-id="0faec-227">You can also click **Add Relationship** and create the relationship by selecting columns from a list.</span></span>  
  
7.  <span data-ttu-id="0faec-228">在 [**指定關聯**性] 對話方塊中，確認 [OrderNumber] 欄位已正確對應，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0faec-228">In the **Specify Relationship** dialog box, verify that the OrderNumber fields are mapped correctly, and then click **OK**.</span></span>  
  
8.  <span data-ttu-id="0faec-229">按一下 **[確定]** 以關閉 [**指定嵌套聯結**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0faec-229">Click **OK** to close the **Specify Nested Join** dialog box.</span></span>  
  
     <span data-ttu-id="0faec-230">案例資料表和巢狀資料表會在 [設計] 窗格中更新，以顯示連接外部資料行與此模型中之資料行的聯結。</span><span class="sxs-lookup"><span data-stu-id="0faec-230">The case and nested tables are updated in the design pane to show the joins connecting the external data columns to the columns in the model.</span></span> <span data-ttu-id="0faec-231">如果關聯性錯誤，您可以用滑鼠右鍵按一下聯結線，然後選取 [**修改連接**] 來編輯資料行對應，也可以用滑鼠右鍵按一下聯結線，然後選取 [**刪除**] 來完全移除關聯性。</span><span class="sxs-lookup"><span data-stu-id="0faec-231">If the relationships are wrong, you can right-click the join line and select **Modify Connections** to edit the column mapping, or you can right-click the join line and select **Delete** to remove the relationship completely.</span></span>  
  
9. <span data-ttu-id="0faec-232">將新的資料列加入方格中。</span><span class="sxs-lookup"><span data-stu-id="0faec-232">Add a new row to the grid.</span></span> <span data-ttu-id="0faec-233">針對 [**來源**]，選取 [ **vAssocSeqOrders 資料表**]。</span><span class="sxs-lookup"><span data-stu-id="0faec-233">For **Source**, select **vAssocSeqOrders table**.</span></span> <span data-ttu-id="0faec-234">針對 [**欄位**]，選取 [CustomerKey]。</span><span class="sxs-lookup"><span data-stu-id="0faec-234">For **Field**, select CustomerKey.</span></span>  
  
10. <span data-ttu-id="0faec-235">將新的資料列加入方格中。</span><span class="sxs-lookup"><span data-stu-id="0faec-235">Add a new row to the grid.</span></span> <span data-ttu-id="0faec-236">針對 [**來源**]，選取 [ **vAssocSeqOrders 資料表**]。</span><span class="sxs-lookup"><span data-stu-id="0faec-236">For **Source**, select **vAssocSeqOrders table**.</span></span> <span data-ttu-id="0faec-237">針對 [**欄位**]，選取 [區域]。</span><span class="sxs-lookup"><span data-stu-id="0faec-237">For **Field**, select Region.</span></span>  
  
11. <span data-ttu-id="0faec-238">將新的資料列加入方格中。</span><span class="sxs-lookup"><span data-stu-id="0faec-238">Add a new row to the grid.</span></span> <span data-ttu-id="0faec-239">針對 [**來源**] 選取 [**預測函數**]，然後針對 [**欄位**] 選取 [] `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="0faec-239">For **Source**, select **Prediction Function**, and for **Field**, select `PredictAssociation`.</span></span>  
  
12. <span data-ttu-id="0faec-240">將 [vAssocSeqLineItems] 拖曳到資料列的 [**準則/引數**] 方塊中 `PredictAssociation` 。</span><span class="sxs-lookup"><span data-stu-id="0faec-240">Drag vAssocSeqLineItems, into the **Criteria/Argument** box of the `PredictAssociation` row.</span></span> <span data-ttu-id="0faec-241">按一下 [**準則/引數**] 方塊的結尾，然後輸入下列文字：`INCLUDE_STATISTICS,3`</span><span class="sxs-lookup"><span data-stu-id="0faec-241">Click at the end of the **Criteria/Argument** box and then type the following text: `INCLUDE_STATISTICS,3`</span></span>  
  
     <span data-ttu-id="0faec-242">[**準則/引數**] 方塊中的完整文字應該是：`[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`</span><span class="sxs-lookup"><span data-stu-id="0faec-242">The complete text in the **Criteria/Argument** box should be: `[Association].[v Assoc Seq Line Items], INCLUDE_STATISTICS, 3`</span></span>  
  
13. <span data-ttu-id="0faec-243">按一下 [**結果**] 按鈕，以查看每個客戶的預測。</span><span class="sxs-lookup"><span data-stu-id="0faec-243">Click the **Result** button to view the predictions for each customer.</span></span>  
  
 <span data-ttu-id="0faec-244">您可嘗試在多個模型上建立類似的預測查詢，以查看篩選是否會變更預測結果。</span><span class="sxs-lookup"><span data-stu-id="0faec-244">You might try creating a similar prediction query on the multiple models, to see whether filtering changes the prediction results.</span></span> <span data-ttu-id="0faec-245">如需有關建立預測和其他類型查詢的詳細資訊，請參閱[關聯模型查詢範例](../../2014/analysis-services/data-mining/association-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="0faec-245">For more information about creating predictions and other types of queries, see [Association Model Query Examples](../../2014/analysis-services/data-mining/association-model-query-examples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0faec-246">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0faec-246">See Also</span></span>  
 <span data-ttu-id="0faec-247">[關聯模型的採礦模型內容 &#40;Analysis Services 資料採礦&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="0faec-247">[Mining Model Content for Association Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-association-models-analysis-services-data-mining.md) </span></span>  
 <span data-ttu-id="0faec-248">[DMX&#41;的 PredictAssociation &#40;](/sql/dmx/predictassociation-dmx) </span><span class="sxs-lookup"><span data-stu-id="0faec-248">[PredictAssociation &#40;DMX&#41;](/sql/dmx/predictassociation-dmx) </span></span>  
 [<span data-ttu-id="0faec-249">使用預測查詢產生器來建立預測查詢</span><span class="sxs-lookup"><span data-stu-id="0faec-249">Create a Prediction Query Using the Prediction Query Builder</span></span>](../../2014/analysis-services/data-mining/create-a-prediction-query-using-the-prediction-query-builder.md)  
  
  
