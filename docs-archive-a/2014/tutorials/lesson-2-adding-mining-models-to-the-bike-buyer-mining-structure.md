---
title: 第2課：將採礦模型新增至自行車購買者採礦結構 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 03fe44c5-6452-4ed0-95f6-9682670c0f52
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: de65fb7a85154f607cd8f266faec4621cdc41476
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702213"
---
# <a name="lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure"></a><span data-ttu-id="39aa7-102">第 2 課：將採礦模型新增至自行車買主採礦結構</span><span class="sxs-lookup"><span data-stu-id="39aa7-102">Lesson 2: Adding Mining Models to the Bike Buyer Mining Structure</span></span>
  <span data-ttu-id="39aa7-103">在這一課，您會將兩個採礦模型新增至您在[第1課：建立自行車購買者採礦結構](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md)中建立的自行車購買者採礦結構。</span><span class="sxs-lookup"><span data-stu-id="39aa7-103">In this lesson, you will add two mining models to the Bike Buyer mining structure that you created [Lesson 1: Creating the Bike Buyer Mining Structure](../../2014/tutorials/lesson-1-creating-the-bike-buyer-mining-structure.md).</span></span> <span data-ttu-id="39aa7-104">這些採礦模型可讓您使用一個模型探索資料，使用另一個模型建立預測。</span><span class="sxs-lookup"><span data-stu-id="39aa7-104">These mining models will allow you to explore the data using one model, and to create predictions using another.</span></span>  
  
 <span data-ttu-id="39aa7-105">若要探索潛在客戶如何依其特性分類，您將建立以[Microsoft 群集演算法](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)為基礎的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="39aa7-105">To explore how potential customers can be categorized by their characteristics, you will create a mining model based on the [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md).</span></span> <span data-ttu-id="39aa7-106">在下一課，您將採索此演算法如何尋找共用類似特性的客戶叢集。</span><span class="sxs-lookup"><span data-stu-id="39aa7-106">In a later lesson, you will explore how this algorithm finds clusters of customers who share similar characteristics.</span></span> <span data-ttu-id="39aa7-107">例如，您會發現某些客戶很可能成為鄰居、使用自行車通勤，並具有類似的教育背景。</span><span class="sxs-lookup"><span data-stu-id="39aa7-107">For example, you might find that certain customers tend to live close to each other, commute by bicycle, and have similar education backgrounds.</span></span> <span data-ttu-id="39aa7-108">您可以利用這些叢集，進一步了解不同客戶彼此的關係，並使用此資訊來建立一個以特定客戶群為目標的行銷策略。</span><span class="sxs-lookup"><span data-stu-id="39aa7-108">You can use these clusters to better understand how different customers are related, and to use the information to create a marketing strategy that targets specific customers.</span></span>  
  
 <span data-ttu-id="39aa7-109">若要預測潛在客戶是否可能購買自行車，您將建立以[Microsoft 決策樹演算法](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)為基礎的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="39aa7-109">To predict whether a potential customer is likely to buy a bicycle, you will create a mining model based on the [Microsoft Decision Trees Algorithm](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md).</span></span> <span data-ttu-id="39aa7-110">此演算法會查看與每一位潛在客戶相關聯的資訊，並尋找在預測其是否會購買自行車時有用的特性。</span><span class="sxs-lookup"><span data-stu-id="39aa7-110">This algorithm looks through the information that is associated with each potential customer, and finds characteristics that are useful in predicting if they will buy a bicycle.</span></span> <span data-ttu-id="39aa7-111">然後它會比較之前的自行車買主與新的潛在客戶的特性值，以判斷新的潛在客戶是否有可能購買自行車。</span><span class="sxs-lookup"><span data-stu-id="39aa7-111">It then compares the values of the characteristics of previous bike buyers against new potential customers to determine whether the new potential customers are likely to buy a bicycle.</span></span>  
  
## <a name="alter-mining-structure-statement"></a><span data-ttu-id="39aa7-112">ALTER MINING STRUCTURE 陳述式</span><span class="sxs-lookup"><span data-stu-id="39aa7-112">ALTER MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="39aa7-113">若要將採礦模型加入至「採礦結構」，您可以使用[ALTER 採礦結構 &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016)語句。</span><span class="sxs-lookup"><span data-stu-id="39aa7-113">In order to add a mining model to the mining structure, you use the [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) statement.</span></span> <span data-ttu-id="39aa7-114">陳述式中的程式碼可分成下列各部份：</span><span class="sxs-lookup"><span data-stu-id="39aa7-114">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="39aa7-115">識別採礦結構</span><span class="sxs-lookup"><span data-stu-id="39aa7-115">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="39aa7-116">命名採礦模型</span><span class="sxs-lookup"><span data-stu-id="39aa7-116">Naming the mining model</span></span>  
  
-   <span data-ttu-id="39aa7-117">定義索引鍵資料行</span><span class="sxs-lookup"><span data-stu-id="39aa7-117">Defining the key column</span></span>  
  
-   <span data-ttu-id="39aa7-118">定義輸入資料行和可預測資料行</span><span class="sxs-lookup"><span data-stu-id="39aa7-118">Defining the input and predictable columns</span></span>  
  
-   <span data-ttu-id="39aa7-119">識別演算法和參數變更</span><span class="sxs-lookup"><span data-stu-id="39aa7-119">Identifying the algorithm and parameter changes</span></span>  
  
 <span data-ttu-id="39aa7-120">以下是 ALTER MINING MODEL 陳述式的一般範例：</span><span class="sxs-lookup"><span data-stu-id="39aa7-120">The following is a generic example of the ALTER MINING MODEL statement:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
ADD MINING MODEL [<mining model name>]  
(  
    [<key column>],  
    <mining model columns>,  
) USING <algorithm name>( <algorithm parameters> )  
WITH FILTER (<expression>)  
```  
  
 <span data-ttu-id="39aa7-121">程式碼的第一行會識別將加入採礦模型的現有採礦結構：</span><span class="sxs-lookup"><span data-stu-id="39aa7-121">The first line of the code identifies the existing mining structure to which the mining models will be added:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="39aa7-122">程式碼的下一行命名要加入採礦結構中的採礦模型：</span><span class="sxs-lookup"><span data-stu-id="39aa7-122">The next line of the code names the mining model that will be added to the mining structure:</span></span>  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 <span data-ttu-id="39aa7-123">如需在 DMX 中命名物件的詳細資訊，請參閱[dmx&#41;&#40;的識別碼](/sql/dmx/identifiers-dmx)。</span><span class="sxs-lookup"><span data-stu-id="39aa7-123">For information about naming an object in DMX, see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="39aa7-124">接下來幾行的程式碼定義採礦結構中將由採礦模型使用的資料行：</span><span class="sxs-lookup"><span data-stu-id="39aa7-124">The next lines of the code define columns from the mining structure that will be used by the mining model:</span></span>  
  
```  
[<key column>],  
<mining model columns>  
```  
  
 <span data-ttu-id="39aa7-125">您只能使用已存在於採礦結構中的資料行，且清單中的第一個資料行必須是採礦結構中的索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="39aa7-125">You can only use columns that already exist in the mining structure, and the first column in the list must be the key column from the mining structure.</span></span>  
  
 <span data-ttu-id="39aa7-126">程式碼的下一行定義產生採礦模型的採礦演算法，以及您可以在演算法上設定的演算法參數：</span><span class="sxs-lookup"><span data-stu-id="39aa7-126">The next line of the code defines the mining algorithm that generates the mining model and the algorithm parameters that you can set on the algorithm:</span></span>  
  
```  
) USING <algorithm name>( <algorithm parameters> )  
```  
  
 <span data-ttu-id="39aa7-127">如需您可以調整之演算法參數的詳細資訊，請參閱[Microsoft 決策樹演算法](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)和[microsoft 群集演算法](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="39aa7-127">For more information about the algorithm parameters that you can adjust, see [Microsoft Decision Trees Algorithm](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md) and [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md).</span></span>  
  
 <span data-ttu-id="39aa7-128">您可以使用下列語法來指定採礦模型中要用於預測的資料行：</span><span class="sxs-lookup"><span data-stu-id="39aa7-128">You can specify that a column in the mining model be used for prediction by using the following syntax:</span></span>  
  
```  
<mining model column> PREDICT  
```  
  
 <span data-ttu-id="39aa7-129">程式碼的最後一行是選擇性的，可定義在定型及測試模型時所套用的篩選。</span><span class="sxs-lookup"><span data-stu-id="39aa7-129">The final line of the code, which is optional, defines a filter that is applied when training and testing the model.</span></span> <span data-ttu-id="39aa7-130">如需如何將篩選套用至採礦模型的詳細資訊，請參閱[&#40;Analysis Services 資料採礦&#41;的採礦模型篩選](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="39aa7-130">For more information about how to apply filters to mining models, see [Filters for Mining Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/filters-for-mining-models-analysis-services-data-mining.md).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="39aa7-131">課程工作</span><span class="sxs-lookup"><span data-stu-id="39aa7-131">Lesson Tasks</span></span>  
 <span data-ttu-id="39aa7-132">您將在這一課執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="39aa7-132">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="39aa7-133">使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 決策樹演算法，將決策樹採礦模型加入 Bike Buyer 結構中</span><span class="sxs-lookup"><span data-stu-id="39aa7-133">Add a decision tree mining model to the Bike Buyer structure by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm</span></span>  
  
-   <span data-ttu-id="39aa7-134">使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 群集演算法，將群集採礦模型加入 Bike Buyer 結構中</span><span class="sxs-lookup"><span data-stu-id="39aa7-134">Add a clustering mining model to the Bike Buyer structure by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm</span></span>  
  
-   <span data-ttu-id="39aa7-135">因為您要查看所有情況的結果，所以請先不要對任一模型新增篩選。</span><span class="sxs-lookup"><span data-stu-id="39aa7-135">Because you want to see results for all cases, you will not yet add a filter to either model.</span></span>  
  
## <a name="adding-a-decision-tree-mining-model-to-the-structure"></a><span data-ttu-id="39aa7-136">將決策樹採礦模型加入結構中</span><span class="sxs-lookup"><span data-stu-id="39aa7-136">Adding a Decision Tree Mining Model to the Structure</span></span>  
 <span data-ttu-id="39aa7-137">第一步是加入以 [!INCLUDE[msCoName](../includes/msconame-md.md)] 決策樹演算法為基礎的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="39aa7-137">The first step is to add a mining model based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Decision Trees algorithm.</span></span>  
  
#### <a name="to-add-a-decision-tree-mining-model"></a><span data-ttu-id="39aa7-138">若要加入決策樹採礦模型</span><span class="sxs-lookup"><span data-stu-id="39aa7-138">To add a decision tree mining model</span></span>  
  
1.  <span data-ttu-id="39aa7-139">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX** ] 以開啟 [查詢編輯器] 和新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="39aa7-139">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open Query Editor and a new, blank query.</span></span>  
  
2.  <span data-ttu-id="39aa7-140">將 ALTER MINING STRUCTURE 陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="39aa7-140">Copy the generic example of the ALTER MINING STRUCTURE statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="39aa7-141">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="39aa7-141">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="39aa7-142">成為：</span><span class="sxs-lookup"><span data-stu-id="39aa7-142">with:</span></span>  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  <span data-ttu-id="39aa7-143">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="39aa7-143">Replace the following:</span></span>  
  
    ```  
    <mining model name>   
    ```  
  
     <span data-ttu-id="39aa7-144">成為：</span><span class="sxs-lookup"><span data-stu-id="39aa7-144">with:</span></span>  
  
    ```  
    Decision Tree  
    ```  
  
5.  <span data-ttu-id="39aa7-145">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="39aa7-145">Replace the following:</span></span>  
  
    ```  
    <mining model columns>,  
    ```  
  
     <span data-ttu-id="39aa7-146">成為：</span><span class="sxs-lookup"><span data-stu-id="39aa7-146">with:</span></span>  
  
    ```  
    (  
       CustomerKey,  
       [Age],  
       [Bike Buyer] PREDICT,  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]  
    ```  
  
     <span data-ttu-id="39aa7-147">在此案例中，`[Bike Buyer]` 資料行已指定為 PREDICT 資料行。</span><span class="sxs-lookup"><span data-stu-id="39aa7-147">In this case, the `[Bike Buyer]` column has been designated as the PREDICT column.</span></span>  
  
6.  <span data-ttu-id="39aa7-148">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="39aa7-148">Replace the following:</span></span>  
  
    ```  
    USING <algorithm name>( <algorithm parameters> )   
    ```  
  
     <span data-ttu-id="39aa7-149">成為：</span><span class="sxs-lookup"><span data-stu-id="39aa7-149">with:</span></span>  
  
    ```  
    Using Microsoft_Decision_Trees  
    WITH DRILLTHROUGH  
    ```  
  
     <span data-ttu-id="39aa7-150">WITH DRILLTHROUGH 陳述式可讓您探索用於建立採礦模型的案例。</span><span class="sxs-lookup"><span data-stu-id="39aa7-150">The WITH DRILLTHROUGH statement allows you to explore the cases that were used to build the mining model.</span></span>  
  
     <span data-ttu-id="39aa7-151">現在，產生的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="39aa7-151">The resulting statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Decision Tree]  
    (  
       CustomerKey,  
       [Age],  
       [Bike Buyer] PREDICT,  
       [Commute Distance],  
       [Education],  
       [Gender],  
       [House Owner Flag],  
       [Marital Status],  
       [Number Cars Owned],  
       [Number Children At Home],  
       [Occupation],  
       [Region],  
       [Total Children],  
       [Yearly Income]  
    ) USING Microsoft_Decision_Trees  
    WITH DRILLTHROUGH  
    ```  
  
7.  <span data-ttu-id="39aa7-152">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="39aa7-152">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="39aa7-153">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `DT_Model.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="39aa7-153">In the **Save As** dialog box, browse to the appropriate folder, and name the file `DT_Model.dmx`.</span></span>  
  
9. <span data-ttu-id="39aa7-154">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="39aa7-154">On the toolbar, click the **Execute** button.</span></span>  
  
## <a name="adding-a-clustering-mining-model-to-the-structure"></a><span data-ttu-id="39aa7-155">將群集採礦模型加入結構中</span><span class="sxs-lookup"><span data-stu-id="39aa7-155">Adding a Clustering Mining Model to the Structure</span></span>  
 <span data-ttu-id="39aa7-156">現在可以將採礦模型加入以 [!INCLUDE[msCoName](../includes/msconame-md.md)] 群組演算法為基礎的 Bike Buyer 採礦結構中。</span><span class="sxs-lookup"><span data-stu-id="39aa7-156">You can now add a mining model to the Bike Buyer mining structure based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm.</span></span> <span data-ttu-id="39aa7-157">因為群集採礦模型將使用採礦結構中定義的所有資料行，所以您可以利用捷徑，以省略採礦資料行之定義的方式，將此模型加入結構中。</span><span class="sxs-lookup"><span data-stu-id="39aa7-157">Because the clustering mining model will use all the columns defined in the mining structure, you can use a shortcut to add the model to the structure by omitting the definition of the mining columns.</span></span>  
  
#### <a name="to-add-a-clustering-mining-model"></a><span data-ttu-id="39aa7-158">若要加入群集採礦模型</span><span class="sxs-lookup"><span data-stu-id="39aa7-158">To add a Clustering mining model</span></span>  
  
1.  <span data-ttu-id="39aa7-159">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX** ] 開啟 [查詢編輯器] 和新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="39aa7-159">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open Query Editor opens and a new, blank query.</span></span>  
  
2.  <span data-ttu-id="39aa7-160">將 ALTER MINING STRUCTURE 陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="39aa7-160">Copy the generic example of the ALTER MINING STRUCTURE statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="39aa7-161">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="39aa7-161">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="39aa7-162">成為：</span><span class="sxs-lookup"><span data-stu-id="39aa7-162">with:</span></span>  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  <span data-ttu-id="39aa7-163">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="39aa7-163">Replace the following:</span></span>  
  
    ```  
    <mining model>   
    ```  
  
     <span data-ttu-id="39aa7-164">成為：</span><span class="sxs-lookup"><span data-stu-id="39aa7-164">with:</span></span>  
  
    ```  
    Clustering Model  
    ```  
  
5.  <span data-ttu-id="39aa7-165">刪除下面這一行：</span><span class="sxs-lookup"><span data-stu-id="39aa7-165">Delete the following:</span></span>  
  
    ```  
    (  
        [<key column>],  
        <mining model columns>,  
    )  
    ```  
  
6.  <span data-ttu-id="39aa7-166">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="39aa7-166">Replace the following:</span></span>  
  
    ```  
    USING <algorithm name>( <algorithm parameters> )  
    ```  
  
     <span data-ttu-id="39aa7-167">成為：</span><span class="sxs-lookup"><span data-stu-id="39aa7-167">with:</span></span>  
  
    ```  
    USING Microsoft_Clustering  
    ```  
  
     <span data-ttu-id="39aa7-168">現在，完整的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="39aa7-168">The complete statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Bike Buyer]  
    ADD MINING MODEL [Clustering]  
    USING Microsoft_Clustering   
    ```  
  
7.  <span data-ttu-id="39aa7-169">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="39aa7-169">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="39aa7-170">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `Clustering_Model.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="39aa7-170">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Clustering_Model.dmx`.</span></span>  
  
9. <span data-ttu-id="39aa7-171">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="39aa7-171">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="39aa7-172">在下一課，您將處理模型和採礦結構。</span><span class="sxs-lookup"><span data-stu-id="39aa7-172">In the next lesson, you will process the models and the mining structure.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="39aa7-173">下一課</span><span class="sxs-lookup"><span data-stu-id="39aa7-173">Next Lesson</span></span>  
 [<span data-ttu-id="39aa7-174">第 3 課：處理自行車買主採礦結構</span><span class="sxs-lookup"><span data-stu-id="39aa7-174">Lesson 3: Processing the Bike Buyer Mining Structure</span></span>](../../2014/tutorials/lesson-3-processing-the-bike-buyer-mining-structure.md)  
  
  
