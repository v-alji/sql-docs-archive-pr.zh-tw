---
title: 將預測函數套用至模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Mining Model Prediction [Analysis Services], selecting mining models
ms.assetid: cf9a97e2-c249-441b-af12-c977c1a91c44
author: minewiskan
ms.author: owend
ms.openlocfilehash: fde9de00adaa1712a9db6e18aabc6a83dd660efb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585676"
---
# <a name="apply-prediction-functions-to-a-model"></a><span data-ttu-id="53486-102">將預測函數套用至模型</span><span class="sxs-lookup"><span data-stu-id="53486-102">Apply Prediction Functions to a Model</span></span>
  <span data-ttu-id="53486-103">若要建立預測查詢，您必須先選取查詢所根據的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="53486-103">To create a prediction query, you must first select the mining model on which the query will be based.</span></span> <span data-ttu-id="53486-104">您可以選取存在於目前專案中的任何採礦模型。</span><span class="sxs-lookup"><span data-stu-id="53486-104">You can select any mining model that exists in the current project.</span></span>  
  
 <span data-ttu-id="53486-105">在您選取模型之後，請將 [預測函數]\*\* 加入查詢中。</span><span class="sxs-lookup"><span data-stu-id="53486-105">After you have selected a model, add a *prediction function* to the query.</span></span> <span data-ttu-id="53486-106">匯入以瞭解預測函數用於許多用途-是，您可以預測值，但也可以取得相關的統計資料，以及用於產生預測的資訊。</span><span class="sxs-lookup"><span data-stu-id="53486-106">It is import to understand that prediction functions are used for many purposes-yes, you can predict values, but you can also get related statistics, as well as information that was used in generating the prediction.</span></span> <span data-ttu-id="53486-107">預測函數可以傳回以下類型的值：</span><span class="sxs-lookup"><span data-stu-id="53486-107">Prediction functions can return the following types of values:</span></span>  
  
-   <span data-ttu-id="53486-108">可預測屬性的名稱以及預測的值。</span><span class="sxs-lookup"><span data-stu-id="53486-108">The name of the predictable attribute, and the value that is predicted.</span></span>  
  
-   <span data-ttu-id="53486-109">有關預測值之分佈和變異數的統計資料。</span><span class="sxs-lookup"><span data-stu-id="53486-109">Statistics about the distribution and variance of the predicted values.</span></span>  
  
-   <span data-ttu-id="53486-110">指定之結果或是所有可能結果的機率。</span><span class="sxs-lookup"><span data-stu-id="53486-110">The probability of a specified outcome, or of all possible outcomes.</span></span>  
  
-   <span data-ttu-id="53486-111">最高或最低分數或值。</span><span class="sxs-lookup"><span data-stu-id="53486-111">The top or bottom scores or values.</span></span>  
  
-   <span data-ttu-id="53486-112">與指定之節點、物件或屬性相關聯的值。</span><span class="sxs-lookup"><span data-stu-id="53486-112">Values associated with a specified node, object, or attribute.</span></span>  
  
 <span data-ttu-id="53486-113">您可以使用各種不同的預測函數，但是您必須選擇適合您所建立之模型類型的函數。</span><span class="sxs-lookup"><span data-stu-id="53486-113">There is a wide variety of prediction functions that you can use, but you must choose the function that suits the type of model you created.</span></span> <span data-ttu-id="53486-114">通常這個選擇取決於用來建立模型的演算法。</span><span class="sxs-lookup"><span data-stu-id="53486-114">Usually this choice depends on the algorithm used to create the model.</span></span>  
  
-   <span data-ttu-id="53486-115">如需幾乎支援所有模型類型的預測函數清單，請參閱[一般預測函數 &#40;DMX)](/sql/dmx/general-prediction-functions-dmx)。</span><span class="sxs-lookup"><span data-stu-id="53486-115">For a list of the prediction functions that are supported for almost all model types, see [General Prediction Functions &#40;DMX&#41;](/sql/dmx/general-prediction-functions-dmx).</span></span>  
  
-   <span data-ttu-id="53486-116">此外，個別演算法也會支援各種不同的專用函數。</span><span class="sxs-lookup"><span data-stu-id="53486-116">Additionally, individual algorithms support a variety of specialized functions.</span></span> <span data-ttu-id="53486-117">例如，如果您建立以 Microsoft 叢集演算法為根據的採礦模型，您可以使用專門的預測函數來尋找有關叢集的資訊，例如從資料值到叢集距心的距離。</span><span class="sxs-lookup"><span data-stu-id="53486-117">For example, if you create a mining model based on the Microsoft Clustering algorithm, you can use specialized prediction functions to find information about the clusters, such as the distance from a data value to the cluster centroid.</span></span>  
  
     <span data-ttu-id="53486-118">如需如何查詢特定採礦模型類型的範例，請參閱[資料採礦演算法 &#40;Analysis Services - 資料採礦&#41;](data-mining-algorithms-analysis-services-data-mining.md) 中的演算法參考主題。</span><span class="sxs-lookup"><span data-stu-id="53486-118">For examples of how to query a specific type of mining model, see the algorithm reference topic, in [Data Mining Algorithms &#40;Analysis Services - Data Mining&#41;](data-mining-algorithms-analysis-services-data-mining.md).</span></span>  
  
### <a name="choose-a-mining-model-to-use-for-prediction"></a><span data-ttu-id="53486-119">選擇用來預測的採礦模型</span><span class="sxs-lookup"><span data-stu-id="53486-119">Choose a mining model to use for prediction</span></span>  
  
1.  <span data-ttu-id="53486-120">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，以滑鼠右鍵按一下模型，然後選取 [Build Prediction Query (建立預測查詢)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="53486-120">From [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click the model, and select **Build Prediction Query**.</span></span>  
  
     <span data-ttu-id="53486-121">--或--</span><span class="sxs-lookup"><span data-stu-id="53486-121">--OR --</span></span>  
  
     <span data-ttu-id="53486-122">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中，按一下 [採礦模型預測]\*\*\*\* 索引標籤，然後按一下 [採礦模型]\*\*\*\* 資料表中的 [選取模型]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="53486-122">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the tab, **Mining Model Prediction**, and then click **Select Model** in the  **Mining Model** table.</span></span>  
  
2.  <span data-ttu-id="53486-123">在 [選取採礦模型]\*\*\*\* 對話方塊中選取採礦模型，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="53486-123">In the **Select Mining Model** dialog box, select a mining model, and then click **OK**.</span></span>  
  
     <span data-ttu-id="53486-124">您可以在目前的 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 資料庫中選擇任何模型。</span><span class="sxs-lookup"><span data-stu-id="53486-124">You can choose any model within the current [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] database.</span></span> <span data-ttu-id="53486-125">若要使用不同資料庫中的模型建立查詢，您必須在該資料庫的內容中開啟新的查詢視窗，或是開啟包含該模型的方案檔。</span><span class="sxs-lookup"><span data-stu-id="53486-125">To create a query using a model in a different database, you must either open a new query window in the context of that database, or open the solution file that contains that model.</span></span>  
  
### <a name="add-prediction-functions-to-a-query"></a><span data-ttu-id="53486-126">將預測函數加入至查詢中</span><span class="sxs-lookup"><span data-stu-id="53486-126">Add prediction functions to a query</span></span>  
  
1.  <span data-ttu-id="53486-127">在 [Prediction Query Builder (預測查詢產生器)]\*\*\*\* 中，設定用於預測的輸入資料，其方法是在 [單一查詢輸入]\*\*\*\* 對話方塊中提供值，或是將模型對應到外部資料來源。</span><span class="sxs-lookup"><span data-stu-id="53486-127">In the **Prediction Query Builder**, configure the input data used for prediction, either by providing values in the **Singleton Query Input** dialog box, or by mapping the model to an external data source.</span></span>  
  
     <span data-ttu-id="53486-128">如需詳細資訊，請參閱 [為預測查詢選擇和對應輸入資料](choose-and-map-input-data-for-a-prediction-query.md)。</span><span class="sxs-lookup"><span data-stu-id="53486-128">For more information, see [Choose and Map Input Data for a Prediction Query](choose-and-map-input-data-for-a-prediction-query.md).</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="53486-129">您不需要提供輸入來產生預測。</span><span class="sxs-lookup"><span data-stu-id="53486-129">It is not required that you provide inputs to generate predictions.</span></span> <span data-ttu-id="53486-130">當沒有輸入時，此演算法通常會傳回所有可能的輸入中最有可能的預測值。</span><span class="sxs-lookup"><span data-stu-id="53486-130">When there is no input, the algorithm will typically return the mostly likely predicted value across all possible inputs.</span></span>  
  
2.  <span data-ttu-id="53486-131">按一下 [來源]\*\*\*\* 資料行，然後從清單中選擇值：</span><span class="sxs-lookup"><span data-stu-id="53486-131">Click the **Source** column, and choose a value from the list:</span></span>  
  
    |||  
    |-|-|  
    |**\<model name>**|<span data-ttu-id="53486-132">選取此選項，將採礦模型中的值包含在輸出中。</span><span class="sxs-lookup"><span data-stu-id="53486-132">Select this option to include values from the mining model in the output.</span></span> <span data-ttu-id="53486-133">您只能加入可預測的資料行。</span><span class="sxs-lookup"><span data-stu-id="53486-133">You can only add predictable columns.</span></span><br /><br /> <span data-ttu-id="53486-134">當您加入模型中的資料行時，傳回的結果會是該資料行中的非相異值清單。</span><span class="sxs-lookup"><span data-stu-id="53486-134">When you add a column from the model, the result returned is the non-distinct list of values in that column.</span></span><br /><br /> <span data-ttu-id="53486-135">您以這個選項加入的資料行會包含在產生之 DMX 陳述式的 SELECT 部分內。</span><span class="sxs-lookup"><span data-stu-id="53486-135">The columns that you add with this option are included in the SELECT portion of the resulting DMX statement.</span></span>|  
    |<span data-ttu-id="53486-136">**預測函數**</span><span class="sxs-lookup"><span data-stu-id="53486-136">**Prediction Function**</span></span>|<span data-ttu-id="53486-137">選取這個選項可瀏覽預測函數清單。</span><span class="sxs-lookup"><span data-stu-id="53486-137">Select this option to browse a list of prediction functions.</span></span><br /><br /> <span data-ttu-id="53486-138">您選取的值或函數會加入至產生之 DMX 陳述式的 SELECT 部分內。</span><span class="sxs-lookup"><span data-stu-id="53486-138">The values or functions you select are added to the SELECT portion of the resulting DMX statement.</span></span><br /><br /> <span data-ttu-id="53486-139">系統不會篩選預測函數清單，也不會由您選取的模型類型加以限制。</span><span class="sxs-lookup"><span data-stu-id="53486-139">The list of prediction functions is not filtered or constrained by the type of model you have selected.</span></span> <span data-ttu-id="53486-140">因此，如果您對於目前模型類型是否支援此函數有任何疑問，您只需要將此函數加入至清單中，並查看是否有錯誤發生。</span><span class="sxs-lookup"><span data-stu-id="53486-140">Therefore, if you have any doubt about whether the function is supported for the current model type, you can just add the function to the list and see if there is an error.</span></span><br /><br /> <span data-ttu-id="53486-141">前有 $ 的清單項目 (例如 $AdjustedProbability) 代表巢狀資料表中的資料行，當您使用 `PredictHistogram` 函數時，該資料表為輸出。</span><span class="sxs-lookup"><span data-stu-id="53486-141">List items that are preceded by $ (such as $AdjustedProbability) represent columns from the nested table that is output when you use the function, `PredictHistogram`.</span></span> <span data-ttu-id="53486-142">當您傳回單一資料行而非巢狀資料表時，可以使用這些當做捷徑。</span><span class="sxs-lookup"><span data-stu-id="53486-142">These are shortcuts that you can use to return a single column and not a nested table.</span></span>|  
    |<span data-ttu-id="53486-143">**自訂運算式**</span><span class="sxs-lookup"><span data-stu-id="53486-143">**Custom Expression**</span></span>|<span data-ttu-id="53486-144">選取這個選項來輸入自訂運算式，然後為輸出指派別名。</span><span class="sxs-lookup"><span data-stu-id="53486-144">Select this option to type a custom expression and then assign an alias to the output.</span></span><br /><br /> <span data-ttu-id="53486-145">此自訂運算式會加入至產生之 DMX 預測查詢的 SELECT 部分中。</span><span class="sxs-lookup"><span data-stu-id="53486-145">The custom expression is added to the SELECT portion of the resulting DMX prediction query.</span></span><br /><br /> <span data-ttu-id="53486-146">如果您想要針對包含每一個資料列的輸出加入文字、呼叫 VB 函數或是呼叫自訂預存程序，這個選項會非常實用。</span><span class="sxs-lookup"><span data-stu-id="53486-146">This option is useful if you want to add text for output with each row, to call VB functions, or to call custom stored procedures.</span></span><br /><br /> <span data-ttu-id="53486-147">如需從 DMX 使用 VBA 和 Excel 函數的資訊，請參閱 [MDX 和 DAX 中的 VBA 函數](/sql/mdx/vba-functions-in-mdx-and-dax)。</span><span class="sxs-lookup"><span data-stu-id="53486-147">For information about using VBA and Excel functions from DMX, see [VBA functions in MDX and DAX](/sql/mdx/vba-functions-in-mdx-and-dax).</span></span>|  
  
3.  <span data-ttu-id="53486-148">在您加入每一個函數或運算式之後，切換到 DMX 檢視可查看此函數如何加入至 DMX 陳述式內。</span><span class="sxs-lookup"><span data-stu-id="53486-148">After adding each function or expression, switch to DMX view to see how the function is added within the DMX statement.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="53486-149">要等到您按一下 [結果]\*\*\*\* 之後，預測查詢產生器才會驗證 DMX。</span><span class="sxs-lookup"><span data-stu-id="53486-149">The Prediction Query Builder does not validate the DMX until you click **Results**.</span></span> <span data-ttu-id="53486-150">通常您會發現，查詢產生器所產生的運算式並不是有效的 DMX。</span><span class="sxs-lookup"><span data-stu-id="53486-150">Often, you will find that the expression that is produced by the query builder is not valid DMX.</span></span> <span data-ttu-id="53486-151">通常原因是因為參考的資料行與可預測資料行無關，或是嘗試預測巢狀資料表中的資料行 (這需要子 SELECT 陳述式)。</span><span class="sxs-lookup"><span data-stu-id="53486-151">Typical causes are referencing a column that is not related to the predictable column, or trying to predict a column in a nested table, which requires a sub-SELECT statement.</span></span> <span data-ttu-id="53486-152">此時，您可以切換到 DMX 檢視，並繼續編輯陳述式。</span><span class="sxs-lookup"><span data-stu-id="53486-152">At this point, you can switch to DMX view and continue editing the statement.</span></span>  
  
### <a name="example-create-a-query-on-a-clustering-model"></a><span data-ttu-id="53486-153">範例：在群集模型上建立查詢</span><span class="sxs-lookup"><span data-stu-id="53486-153">Example: Create a query on a clustering model</span></span>  
  
1.  <span data-ttu-id="53486-154">如果您沒有叢集模型可用來建立此範例查詢，請使用 [資料採礦基本教學課程](../../tutorials/basic-data-mining-tutorial.md)建立 [TM_Clustering] 模型。</span><span class="sxs-lookup"><span data-stu-id="53486-154">If you do not have a clustering model available for building this sample query, create the model, [TM_Clustering], using the [Basic Data Mining Tutorial](../../tutorials/basic-data-mining-tutorial.md).</span></span>  
  
2.  <span data-ttu-id="53486-155">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中，以滑鼠右鍵按一下模型 [TM_Clustering]，然後選取 [Build Prediction Query (建立預測查詢)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="53486-155">From [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], right-click the model, [TM_Clustering], and select **Build Prediction Query**.</span></span>  
  
3.  <span data-ttu-id="53486-156">從 [採礦模型]\*\*\*\* 功能表中選取 [單一查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="53486-156">From the **Mining Model** menu, select **Singleton Query**.</span></span>  
  
4.  <span data-ttu-id="53486-157">在 [單一查詢輸入]\*\*\*\* 對話方塊中，將以下的值設定為輸入：</span><span class="sxs-lookup"><span data-stu-id="53486-157">In the **Singleton Query Input** dialog box, set the following values as inputs:</span></span>  
  
    -   <span data-ttu-id="53486-158">Gender = M</span><span class="sxs-lookup"><span data-stu-id="53486-158">Gender = M</span></span>  
  
    -   <span data-ttu-id="53486-159">Commute Distance = 5-10 miles</span><span class="sxs-lookup"><span data-stu-id="53486-159">Commute Distance = 5-10 miles</span></span>  
  
5.  <span data-ttu-id="53486-160">在查詢方格中，針對 [來源]\*\*\*\* 選取 TM_Clustering 採礦模型，並加入 [Bike Buyer] 資料行。</span><span class="sxs-lookup"><span data-stu-id="53486-160">In the query grid, for **Source**, select TM_Clustering mining model, and add the column, [Bike Buyer].</span></span>  
  
6.  <span data-ttu-id="53486-161">針對 [**來源**] 選取 [**預測函數**]，然後新增函式 `Cluster` 。</span><span class="sxs-lookup"><span data-stu-id="53486-161">For **Source**, select **Prediction Function**, and add the function, `Cluster`.</span></span>  
  
7.  <span data-ttu-id="53486-162">針對 [**來源**] 選取 [**預測函數**]，加入函數， `PredictSupport` 然後將模型資料行 [自行車買方] 拖曳至 [**準則/引數**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="53486-162">For **Source**, select **Prediction Function**, add the function, `PredictSupport`, and drag the model column [Bike Buyer] into the **Criteria/Argument** box.</span></span> <span data-ttu-id="53486-163">在 [別名]\*\*\*\* 資料行中輸入 **Support**。</span><span class="sxs-lookup"><span data-stu-id="53486-163">Type **Support** in the **Alias** column.</span></span>  
  
     <span data-ttu-id="53486-164">從 [準則/引數]\*\*\*\* 方塊複製代表預測函數和資料行參考的運算式。</span><span class="sxs-lookup"><span data-stu-id="53486-164">Copy the expression representing the prediction function and column reference from the **Criteria/Argument** box.</span></span>  
  
8.  <span data-ttu-id="53486-165">針對 [來源]\*\*\*\* 選取 [自訂運算式]\*\*\*\*、輸入別名，然後使用以下語法來參考 Excel CEILING 函數：</span><span class="sxs-lookup"><span data-stu-id="53486-165">For **Source**, select **Custom Expression**, type an alias, and then reference the Excel CEILING function by using the following syntax:</span></span>  
  
    ```  
    Excel![CEILING](<arguments) as <return type>  
    ```  
  
     <span data-ttu-id="53486-166">貼上資料行參考，當做函數的引數。</span><span class="sxs-lookup"><span data-stu-id="53486-166">Paste the column reference in as the argument to the function.</span></span>  
  
     <span data-ttu-id="53486-167">例如，下列運算式會傳回支援值的 CEILING：</span><span class="sxs-lookup"><span data-stu-id="53486-167">For example, the following expression returns the CEILING of the support value:</span></span>  
  
    ```  
    EXCEL!CEILING(PredictSupport([TM_Clustering].[Bike Buyer]),2)  
    ```  
  
     <span data-ttu-id="53486-168">在 [別名]\*\*\*\* 資料行中輸入「CEILING」。</span><span class="sxs-lookup"><span data-stu-id="53486-168">Type CEILING in the **Alias** column.</span></span>  
  
9. <span data-ttu-id="53486-169">按一下 [切換到查詢文字檢視]\*\*\*\* 來檢閱產生的 DMX 陳述式，然後按一下 [切換到查詢結果檢視]\*\*\*\* 來查看預測查詢的資料行輸出。</span><span class="sxs-lookup"><span data-stu-id="53486-169">Click **Switch to query text view** to review the DMX statement that was generated, and then click **Switch to query result view** to see the columns output by the prediction query.</span></span>  
  
     <span data-ttu-id="53486-170">下表會顯示預期的結果：</span><span class="sxs-lookup"><span data-stu-id="53486-170">The following table shows the expected results:</span></span>  
  
    |<span data-ttu-id="53486-171">Bike Buyer</span><span class="sxs-lookup"><span data-stu-id="53486-171">Bike Buyer</span></span>|<span data-ttu-id="53486-172">$Cluster</span><span class="sxs-lookup"><span data-stu-id="53486-172">$Cluster</span></span>|<span data-ttu-id="53486-173">SUPPORT</span><span class="sxs-lookup"><span data-stu-id="53486-173">SUPPORT</span></span>|<span data-ttu-id="53486-174">CEILING</span><span class="sxs-lookup"><span data-stu-id="53486-174">CEILING</span></span>|  
    |----------------|--------------|-------------|-------------|  
    |<span data-ttu-id="53486-175">0</span><span class="sxs-lookup"><span data-stu-id="53486-175">0</span></span>|<span data-ttu-id="53486-176">叢集 8</span><span class="sxs-lookup"><span data-stu-id="53486-176">Cluster 8</span></span>|<span data-ttu-id="53486-177">954</span><span class="sxs-lookup"><span data-stu-id="53486-177">954</span></span>|<span data-ttu-id="53486-178">953.948638926372</span><span class="sxs-lookup"><span data-stu-id="53486-178">953.948638926372</span></span>|  
  
 <span data-ttu-id="53486-179">如果您想要在語句中的其他位置新增其他子句（例如，如果您想要加入 WHERE 子句），則無法使用方格來加入它。您必須先切換到 DMX view。</span><span class="sxs-lookup"><span data-stu-id="53486-179">If you want to add other clauses elsewhere in the statement-for example, if you want to add a WHERE clause-you cannot add it by using the grid; you must switch to DMX view first.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53486-180">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53486-180">See Also</span></span>  
 [<span data-ttu-id="53486-181">資料採礦查詢</span><span class="sxs-lookup"><span data-stu-id="53486-181">Data Mining Queries</span></span>](data-mining-queries.md)  
  
  
