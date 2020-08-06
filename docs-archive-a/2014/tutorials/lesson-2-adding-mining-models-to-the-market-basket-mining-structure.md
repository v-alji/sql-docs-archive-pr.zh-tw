---
title: 第2課：將採礦模型加入至購物籃的採礦結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: d96a7a7d-35d7-4b34-abb5-f0822c256253
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: b9573d9359983e33cf23533787c26039572710ea
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702206"
---
# <a name="lesson-2-adding-mining-models-to-the-market-basket-mining-structure"></a><span data-ttu-id="0bc54-102">第 2 課：將採礦模型新增至購物籃採礦結構</span><span class="sxs-lookup"><span data-stu-id="0bc54-102">Lesson 2: Adding Mining Models to the Market Basket Mining Structure</span></span>
  <span data-ttu-id="0bc54-103">在這一課，您會將兩個採礦模型新增至您在[第1課：建立購物籃採礦結構](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md)中所建立的購物籃採礦結構。</span><span class="sxs-lookup"><span data-stu-id="0bc54-103">In this lesson, you will add two mining models to the Market Basket mining structure that you created in [Lesson 1: Creating the Market Basket Mining Structure](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md).</span></span> <span data-ttu-id="0bc54-104">這些採礦模型可讓您建立預測。</span><span class="sxs-lookup"><span data-stu-id="0bc54-104">These mining models will allow you to create predictions.</span></span>  
  
 <span data-ttu-id="0bc54-105">若要預測客戶可能同時購買的產品類型，您將使用[Microsoft 關聯分析演算法](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)和兩個不同的*MINIMUM_PROBABILTY*參數值來建立兩個採礦模型。</span><span class="sxs-lookup"><span data-stu-id="0bc54-105">To predict the types of products that customers tend to purchase at the same time, you will create two mining models using the [Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md) and two different values for the *MINIMUM_PROBABILTY* parameter.</span></span>  
  
 <span data-ttu-id="0bc54-106">*MINIMUM_PROBABILTY*是 [!INCLUDE[msCoName](../includes/msconame-md.md)] 關聯演算法參數，可指定規則必須具有的最小機率，以協助判斷「採礦模型」所包含的規則數目。</span><span class="sxs-lookup"><span data-stu-id="0bc54-106">*MINIMUM_PROBABILTY* is a [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm parameter that helps to determine the number of rules that a mining model will contain by specifying the minimum probability that a rule must have.</span></span> <span data-ttu-id="0bc54-107">例如，將此值設定為 0.4 是指定只有當規則所描述的產品組合至少具有百分之四十的發生機率時，才可以產生此規則。</span><span class="sxs-lookup"><span data-stu-id="0bc54-107">For example, setting this value to 0.4 specifies that a rule can be generated only if the combination of products that the rule describes has at least a forty percent probability of occurring.</span></span>  
  
 <span data-ttu-id="0bc54-108">在稍後的課程中，您將會看到變更*MINIMUM_PROBABILTY*參數的效果。</span><span class="sxs-lookup"><span data-stu-id="0bc54-108">You will view the effect of changing the *MINIMUM_PROBABILTY* parameter in a later lesson.</span></span>  
  
## <a name="alter-mining-structure-statement"></a><span data-ttu-id="0bc54-109">ALTER MINING STRUCTURE 陳述式</span><span class="sxs-lookup"><span data-stu-id="0bc54-109">ALTER MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="0bc54-110">若要將包含嵌套資料表的採礦模型加入至「採礦結構」，您可以使用[ALTER 採礦結構 &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016)語句。</span><span class="sxs-lookup"><span data-stu-id="0bc54-110">To add a mining model that contains a nested table to a mining structure, you use the [ALTER MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/alter-mining-structure-dmx?view=sql-server-2016) statement.</span></span> <span data-ttu-id="0bc54-111">陳述式中的程式碼可分成下列各部份：</span><span class="sxs-lookup"><span data-stu-id="0bc54-111">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="0bc54-112">識別採礦結構</span><span class="sxs-lookup"><span data-stu-id="0bc54-112">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="0bc54-113">命名採礦模型</span><span class="sxs-lookup"><span data-stu-id="0bc54-113">Naming the mining model</span></span>  
  
-   <span data-ttu-id="0bc54-114">定義索引鍵資料行</span><span class="sxs-lookup"><span data-stu-id="0bc54-114">Defining the key column</span></span>  
  
-   <span data-ttu-id="0bc54-115">定義輸入資料行和可預測資料行</span><span class="sxs-lookup"><span data-stu-id="0bc54-115">Defining the input and predictable columns</span></span>  
  
-   <span data-ttu-id="0bc54-116">定義巢狀資料表資料行</span><span class="sxs-lookup"><span data-stu-id="0bc54-116">Defining the nested table columns</span></span>  
  
-   <span data-ttu-id="0bc54-117">識別演算法和參數變更</span><span class="sxs-lookup"><span data-stu-id="0bc54-117">Identifying the algorithm and parameter changes</span></span>  
  
 <span data-ttu-id="0bc54-118">下面是 `ALTER MINING STRUCTURE` 陳述式的一般範例，它會將採礦模型加入至包含巢狀資料表資料行的結構：</span><span class="sxs-lookup"><span data-stu-id="0bc54-118">The following is a generic example of the `ALTER MINING STRUCTURE` statement that adds a mining model to a structure that includes nested table columns:</span></span>  
  
```  
ALTER MINING STRUCTURE [<Mining Structure Name>]  
ADD MINING MODEL [<Mining Model Name>]  
(  
    [<key column>],  
    <mining model column> <usage>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
) USING <algorithm>( <algorithm parameters> )  
```  
  
 <span data-ttu-id="0bc54-119">程式碼的第一行會識別將加入採礦模型的現有採礦結構：</span><span class="sxs-lookup"><span data-stu-id="0bc54-119">The first line of the code identifies the existing mining structure to which the mining model will be added:</span></span>  
  
```  
ALTER MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="0bc54-120">程式碼的下一行命名要加入採礦結構中的採礦模型：</span><span class="sxs-lookup"><span data-stu-id="0bc54-120">The next line of the code names the mining model that will be added to the mining structure:</span></span>  
  
```  
ADD MINING MODEL [<mining model name>]  
```  
  
 <span data-ttu-id="0bc54-121">如需 (DMX) 為資料採礦延伸模組中的物件命名的詳細資訊，請參閱[&#40;dmx&#41;的識別碼](/sql/dmx/identifiers-dmx)。</span><span class="sxs-lookup"><span data-stu-id="0bc54-121">For information about naming an object in Data Mining Extensions (DMX), see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="0bc54-122">接下來幾行的程式碼會定義採礦結構中將由採礦模型使用的資料行：</span><span class="sxs-lookup"><span data-stu-id="0bc54-122">The next lines of the code define the columns in the mining structure that will be used by the mining model:</span></span>  
  
```  
[<key column>],  
<mining model columns> <usage>,  
```  
  
 <span data-ttu-id="0bc54-123">您只能使用已經存在採礦結構中的資料行。</span><span class="sxs-lookup"><span data-stu-id="0bc54-123">You can only use columns that already exist in the mining structure.</span></span>  
  
 <span data-ttu-id="0bc54-124">採礦模型資料行清單中的第一個資料行必須是採礦結構中的索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="0bc54-124">The first column in the list of mining model columns must be the key column in the mining structure.</span></span> <span data-ttu-id="0bc54-125">不過，您不需要在索引 `KEY` 鍵資料行後面輸入來指定使用方式。</span><span class="sxs-lookup"><span data-stu-id="0bc54-125">However, you do not have to type `KEY` after the key column to specify usage.</span></span> <span data-ttu-id="0bc54-126">這是因為當您建立了採礦結構時，已經將資料行定義為索引鍵。</span><span class="sxs-lookup"><span data-stu-id="0bc54-126">That is because you have already defined the column as a key when you created the mining structure.</span></span>  
  
 <span data-ttu-id="0bc54-127">其餘幾行會指定新採礦模型中資料行的使用方式。</span><span class="sxs-lookup"><span data-stu-id="0bc54-127">The remaining lines specify the usage of the columns in the new mining model.</span></span> <span data-ttu-id="0bc54-128">您可以使用下列語法來指定要用於預測之採礦模型中的資料行：</span><span class="sxs-lookup"><span data-stu-id="0bc54-128">You can specify that a column in the mining model will be used for prediction by using the following syntax:</span></span>  
  
```  
<column name> PREDICT,  
```  
  
 <span data-ttu-id="0bc54-129">如果您沒有指定使用方式，就不需要在清單中加入資料採礦結構資料行。</span><span class="sxs-lookup"><span data-stu-id="0bc54-129">If you do not specify usage, you do not have to include a data mining structure column in the list.</span></span> <span data-ttu-id="0bc54-130">參考資料採礦結構所使用的所有資料行都會自動供以該結構為基礎的採礦模型使用。</span><span class="sxs-lookup"><span data-stu-id="0bc54-130">All columns that are used by the referenced data mining structure are automatically available for use by the mining models that are based on that structure.</span></span> <span data-ttu-id="0bc54-131">不過，除非您指定了使用方式，否則此模型將無法使用這些資料行進行定型。</span><span class="sxs-lookup"><span data-stu-id="0bc54-131">However, the model will not use the columns for training unless you specify the usage.</span></span>  
  
 <span data-ttu-id="0bc54-132">程式碼的最後一行定義將用來產生採礦模型的演算法和演算法參數。</span><span class="sxs-lookup"><span data-stu-id="0bc54-132">The last line in the code defines the algorithm and algorithm parameters that will be used to generate the mining model.</span></span>  
  
```  
) USING <algorithm>( <algorithm parameters> )  
```  
  
## <a name="lesson-tasks"></a><span data-ttu-id="0bc54-133">課程工作</span><span class="sxs-lookup"><span data-stu-id="0bc54-133">Lesson Tasks</span></span>  
 <span data-ttu-id="0bc54-134">您將在這一課執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="0bc54-134">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="0bc54-135">使用預設機率，將關聯採礦模型加入至結構</span><span class="sxs-lookup"><span data-stu-id="0bc54-135">Add an association mining model to the structure using the default probability</span></span>  
  
-   <span data-ttu-id="0bc54-136">使用修改的機率，將關聯採礦模型加入至結構</span><span class="sxs-lookup"><span data-stu-id="0bc54-136">Add an association mining model to the structure using a modified probability</span></span>  
  
## <a name="adding-an-association-mining-model-to-the-structure-using-the-default-minimum_probability"></a><span data-ttu-id="0bc54-137">使用預設 MINIMUM_PROBABILITY 將關聯採礦模型加入到結構中</span><span class="sxs-lookup"><span data-stu-id="0bc54-137">Adding an Association Mining Model to the Structure Using the Default MINIMUM_PROBABILITY</span></span>  
 <span data-ttu-id="0bc54-138">第一個工作是 [!INCLUDE[msCoName](../includes/msconame-md.md)] 使用*MINIMUM_PROBABILITY*的預設值，根據關聯分析演算法，將新的採礦模型新增至購物籃的分析結構。</span><span class="sxs-lookup"><span data-stu-id="0bc54-138">The first task is to add a new mining model to the Market Basket mining structure based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm using the default value for *MINIMUM_PROBABILITY*.</span></span>  
  
#### <a name="to-add-an-association-mining-model"></a><span data-ttu-id="0bc54-139">加入關聯採礦模型</span><span class="sxs-lookup"><span data-stu-id="0bc54-139">To add an Association mining model</span></span>  
  
1.  <span data-ttu-id="0bc54-140">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX**]。</span><span class="sxs-lookup"><span data-stu-id="0bc54-140">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="0bc54-141">此時會開啟 [查詢編輯器] 且包含新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="0bc54-141">Query Editor opens and contains a new, blank query.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0bc54-142">若要針對特定 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 資料庫建立 DMX 查詢，請以滑鼠右鍵按一下該資料庫，而非執行個體。</span><span class="sxs-lookup"><span data-stu-id="0bc54-142">To create a DMX query against a specific [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] database, right-click the database instead of the instance.</span></span>  
  
2.  <span data-ttu-id="0bc54-143">將 `ALTER MINING STRUCTURE` 陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="0bc54-143">Copy the generic example of the `ALTER MINING STRUCTURE` statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="0bc54-144">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="0bc54-144">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="0bc54-145">成為：</span><span class="sxs-lookup"><span data-stu-id="0bc54-145">with:</span></span>  
  
    ```  
    [Market Basket]  
    ```  
  
4.  <span data-ttu-id="0bc54-146">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="0bc54-146">Replace the following:</span></span>  
  
    ```  
    <mining model name>   
    ```  
  
     <span data-ttu-id="0bc54-147">成為：</span><span class="sxs-lookup"><span data-stu-id="0bc54-147">with:</span></span>  
  
    ```  
    [Default Association]  
    ```  
  
5.  <span data-ttu-id="0bc54-148">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="0bc54-148">Replace the following:</span></span>  
  
    ```  
    [<key column>],  
    <mining model columns>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
    ```  
  
     <span data-ttu-id="0bc54-149">成為：</span><span class="sxs-lookup"><span data-stu-id="0bc54-149">with:</span></span>  
  
    ```  
    OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    ```  
  
     <span data-ttu-id="0bc54-150">在此情況下，`[Products]` 資料表已指定為可預測資料行`.`。此外，`[Model]` 資料行會包含在巢狀資料表資料行的清單中，因為它是巢狀資料表的索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="0bc54-150">In this case, the `[Products]` table has been designated as the predictable column`.` Also, the `[Model]` column is included in the list of nested table columns because it is the key column of the nested table.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0bc54-151">請記住，巢狀索引鍵與案例索引鍵不同。</span><span class="sxs-lookup"><span data-stu-id="0bc54-151">Remember that a nested key is different from a case key.</span></span> <span data-ttu-id="0bc54-152">案例索引鍵是案例的唯一識別碼，而巢狀索引鍵則是您想要建立模型的屬性。</span><span class="sxs-lookup"><span data-stu-id="0bc54-152">A case key is a unique identifier of the case, whereas the nested key is an attribute that you want to model.</span></span>  
  
6.  <span data-ttu-id="0bc54-153">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="0bc54-153">Replace the following:</span></span>  
  
    ```  
    USING <algorithm>( <algorithm parameters> )  
    ```  
  
     <span data-ttu-id="0bc54-154">成為：</span><span class="sxs-lookup"><span data-stu-id="0bc54-154">with:</span></span>  
  
    ```  
    Using Microsoft_Association_Rules  
    ```  
  
     <span data-ttu-id="0bc54-155">現在，產生的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="0bc54-155">The resulting statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Market Basket]  
    ADD MINING MODEL [Default Association]  
    (  
        OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    )  
    Using Microsoft_Association_Rules  
    ```  
  
7.  <span data-ttu-id="0bc54-156">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="0bc54-156">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="0bc54-157">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `Default_Association_Model.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="0bc54-157">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Default_Association_Model.dmx`.</span></span>  
  
9. <span data-ttu-id="0bc54-158">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0bc54-158">On the toolbar, click the **Execute** button.</span></span>  
  
## <a name="adding-an-association-mining-model-to-the-structure-changing-the-default-minimum_probability"></a><span data-ttu-id="0bc54-159">變更預設 MINIMUM_PROBABILITY 以便將關聯採礦模型加入到結構中</span><span class="sxs-lookup"><span data-stu-id="0bc54-159">Adding an Association Mining Model to the Structure Changing the Default MINIMUM_PROBABILITY</span></span>  
 <span data-ttu-id="0bc54-160">下一項工作是根據 [!INCLUDE[msCoName](../includes/msconame-md.md)] 關聯分析演算法，將新的採礦模型加入至購物籃採礦結構中，並將 MINIMUM_PROBABILITY 的預設值變更為 0.01。</span><span class="sxs-lookup"><span data-stu-id="0bc54-160">The next task is to add a new mining model to the Market Basket mining structure based on the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm, and change the default value for MINIMUM_PROBABILITY to 0.01.</span></span> <span data-ttu-id="0bc54-161">變更參數將導致 [!INCLUDE[msCoName](../includes/msconame-md.md)] 關聯分析演算法建立更多規則。</span><span class="sxs-lookup"><span data-stu-id="0bc54-161">Changing the parameter will cause the [!INCLUDE[msCoName](../includes/msconame-md.md)] Association algorithm to create more rules.</span></span>  
  
#### <a name="to-add-an-association-mining-model"></a><span data-ttu-id="0bc54-162">加入關聯採礦模型</span><span class="sxs-lookup"><span data-stu-id="0bc54-162">To add an Association mining model</span></span>  
  
1.  <span data-ttu-id="0bc54-163">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX**]。</span><span class="sxs-lookup"><span data-stu-id="0bc54-163">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="0bc54-164">此時會開啟 [查詢編輯器] 且包含新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="0bc54-164">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="0bc54-165">將 `ALTER MINING STRUCTURE` 陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="0bc54-165">Copy the generic example of the `ALTER MINING STRUCTURE` statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="0bc54-166">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="0bc54-166">Replace the following:</span></span>  
  
    ```  
    <mining structure name>   
    ```  
  
     <span data-ttu-id="0bc54-167">成為：</span><span class="sxs-lookup"><span data-stu-id="0bc54-167">with:</span></span>  
  
    ```  
    Market Basket  
    ```  
  
4.  <span data-ttu-id="0bc54-168">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="0bc54-168">Replace the following:</span></span>  
  
    ```  
    <mining model name>   
    ```  
  
     <span data-ttu-id="0bc54-169">成為：</span><span class="sxs-lookup"><span data-stu-id="0bc54-169">with:</span></span>  
  
    ```  
    [Modified Association]  
    ```  
  
5.  <span data-ttu-id="0bc54-170">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="0bc54-170">Replace the following:</span></span>  
  
    ```  
    <mining model columns>,  
    <table columns>  
    (  [<nested key column>],  
       <nested mining model columns> )  
    ```  
  
     <span data-ttu-id="0bc54-171">成為：</span><span class="sxs-lookup"><span data-stu-id="0bc54-171">with:</span></span>  
  
    ```  
    OrderNumber,  
    [Products] PREDICT (  
            [Model]  
        )  
    ```  
  
     <span data-ttu-id="0bc54-172">在此情況下，`[Products]` 資料表已指定為可預測資料行。</span><span class="sxs-lookup"><span data-stu-id="0bc54-172">In this case, the `[Products]` table has been designated as the predictable column.</span></span> <span data-ttu-id="0bc54-173">此外，`[MODEL]` 資料行會包含在清單中，因為它是巢狀資料表中的索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="0bc54-173">Also, the `[MODEL]` column is included in the list because it is the key column in the nested table.</span></span>  
  
6.  <span data-ttu-id="0bc54-174">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="0bc54-174">Replace the following:</span></span>  
  
    ```  
    USING <algorithm>( <algorithm parameters> )  
    ```  
  
     <span data-ttu-id="0bc54-175">成為：</span><span class="sxs-lookup"><span data-stu-id="0bc54-175">with:</span></span>  
  
    ```  
    USING Microsoft_Association_Rules (Minimum_Probability = 0.1)  
    ```  
  
     <span data-ttu-id="0bc54-176">現在，產生的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="0bc54-176">The resulting statement should now be as follows:</span></span>  
  
    ```  
    ALTER MINING STRUCTURE [Market Basket]  
    ADD MINING MODEL [Modified Assocation]  
    (  
        OrderNumber,  
        [Products] PREDICT (  
            [Model]  
        )  
    )  
    USING Microsoft_Association_Rules (Minimum_Probability = 0.1)  
    ```  
  
7.  <span data-ttu-id="0bc54-177">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="0bc54-177">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="0bc54-178">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `Modified Association_Model.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="0bc54-178">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Modified Association_Model.dmx`.</span></span>  
  
9. <span data-ttu-id="0bc54-179">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="0bc54-179">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="0bc54-180">在下一課，您將處理購物籃採礦結構及其相關聯的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="0bc54-180">In this next lesson you will process the Market Basket mining structure together with its associated mining models.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="0bc54-181">下一課</span><span class="sxs-lookup"><span data-stu-id="0bc54-181">Next Lesson</span></span>  
 [<span data-ttu-id="0bc54-182">第 3 課：處理購物籃採礦結構</span><span class="sxs-lookup"><span data-stu-id="0bc54-182">Lesson 3: Processing the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-3-processing-the-market-basket-mining-structure.md)  
  
  
