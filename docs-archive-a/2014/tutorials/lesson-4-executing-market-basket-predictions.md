---
title: 第4課：執行購物籃預測 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b3238f1b-ea04-4253-ade2-838a806b62fe
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 3b49fc242eb8b2242269c5af33cc094937bbe0de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594876"
---
# <a name="lesson-4-executing-market-basket-predictions"></a><span data-ttu-id="f0695-102">第 4 課：執行購物籃預測</span><span class="sxs-lookup"><span data-stu-id="f0695-102">Lesson 4: Executing Market Basket Predictions</span></span>
  <span data-ttu-id="f0695-103">在這一課，您將使用 DMX `SELECT` 語句，根據您在[第2課：將採礦模型新增至購物籃的採礦結構](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)中所建立的關聯模型來建立預測。</span><span class="sxs-lookup"><span data-stu-id="f0695-103">In this lesson, you will use the DMX `SELECT` statement to create predictions based on the association models you created in [Lesson 2: Adding Mining Models to the Market Basket Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md).</span></span> <span data-ttu-id="f0695-104">預測查詢的建立方式是使用 DMX `SELECT` 陳述式並加入 `PREDICTION JOIN` 子句。</span><span class="sxs-lookup"><span data-stu-id="f0695-104">A prediction query is created by using the DMX `SELECT` statement and adding a `PREDICTION JOIN` clause.</span></span> <span data-ttu-id="f0695-105">如需預測聯結語法的詳細資訊，請參閱[從 &#60;模型選取&#62; 預測聯結 &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx)。</span><span class="sxs-lookup"><span data-stu-id="f0695-105">For more information about the syntax of a prediction join, see [SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx).</span></span>  
  
 <span data-ttu-id="f0695-106">語句的**SELECT FROM \<model> 預測聯結**形式 `SELECT` 包含三個部分：</span><span class="sxs-lookup"><span data-stu-id="f0695-106">The **SELECT FROM \<model> PREDICTION JOIN** form of the `SELECT` statement contains three parts:</span></span>  
  
-   <span data-ttu-id="f0695-107">結果集傳回的採礦模型資料行和預測函數的清單。</span><span class="sxs-lookup"><span data-stu-id="f0695-107">A list of the mining model columns and prediction functions that are returned in the result set.</span></span> <span data-ttu-id="f0695-108">這份清單也可以包含來源資料的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="f0695-108">This list can also contain input columns from the source data.</span></span>  
  
-   <span data-ttu-id="f0695-109">定義用來建立預測之資料的來源查詢。</span><span class="sxs-lookup"><span data-stu-id="f0695-109">A source query that defines the data that is being used to create a prediction.</span></span> <span data-ttu-id="f0695-110">例如，如果您要在單一批次中建立許多預測，來源查詢就可以擷取客戶的清單。</span><span class="sxs-lookup"><span data-stu-id="f0695-110">For example, if you are creating many predictions in a batch, the source query could retrieve a list of customers.</span></span>  
  
-   <span data-ttu-id="f0695-111">採礦模型資料行和來源資料之間的對應。</span><span class="sxs-lookup"><span data-stu-id="f0695-111">A mapping between the mining model columns and the source data.</span></span> <span data-ttu-id="f0695-112">如果資料行名稱相符，您就可以使用 `NATURAL PREDICTION JOIN` 語法並省略資料行對應。</span><span class="sxs-lookup"><span data-stu-id="f0695-112">If the columns names match, you can use the `NATURAL PREDICTION JOIN` syntax and omit the column mappings.</span></span>  
  
 <span data-ttu-id="f0695-113">您可以使用預測函數來強化查詢。</span><span class="sxs-lookup"><span data-stu-id="f0695-113">You can enhance the query by using prediction functions.</span></span> <span data-ttu-id="f0695-114">預測函數會提供其他資訊，例如發生預測的機率，或提供對定型資料集的預測支援。</span><span class="sxs-lookup"><span data-stu-id="f0695-114">Prediction functions provide additional information, such as the probability of a prediction occurring, or the support for a prediction in the training dataset.</span></span> <span data-ttu-id="f0695-115">如需預測函數的詳細資訊，請參閱[&#40;DMX&#41;](/sql/dmx/functions-dmx)的函式。</span><span class="sxs-lookup"><span data-stu-id="f0695-115">For more information about prediction functions, see [Functions &#40;DMX&#41;](/sql/dmx/functions-dmx).</span></span>  
  
 <span data-ttu-id="f0695-116">您也可以在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中使用預測查詢產生器來建立預測查詢。</span><span class="sxs-lookup"><span data-stu-id="f0695-116">You can also use the prediction query builder in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] to create prediction queries.</span></span>  
  
## <a name="singleton-prediction-join-statement"></a><span data-ttu-id="f0695-117">單一 PREDICTION JOIN 陳述式</span><span class="sxs-lookup"><span data-stu-id="f0695-117">Singleton PREDICTION JOIN Statement</span></span>  
 <span data-ttu-id="f0695-118">第一個步驟是建立單一查詢，方法是使用**SELECT FROM \<model> 預測聯結**語法，並提供一組值做為輸入。</span><span class="sxs-lookup"><span data-stu-id="f0695-118">The first step is to create a singleton query, by using the **SELECT FROM \<model> PREDICTION JOIN** syntax and supplying a single set of values as input.</span></span> <span data-ttu-id="f0695-119">以下是單一陳述式的一般範例：</span><span class="sxs-lookup"><span data-stu-id="f0695-119">The following is a generic example of the singleton statement:</span></span>  
  
```  
SELECT <select list>  
    FROM [<mining model>]   
[NATURAL] PREDICTION JOIN  
(SELECT '<value>' AS [<column>],   
    (SELECT 'value' AS [<nested column>] UNION  
        SELECT 'value' AS [<nested column>] ...)   
    AS [<nested table>])  
AS [<input alias>]  
```  
  
 <span data-ttu-id="f0695-120">第一行程式碼會定義在採礦模型中由查詢傳回的資料行，並且指定用來產生預測之採礦模型的名稱：</span><span class="sxs-lookup"><span data-stu-id="f0695-120">The first line of the code defines the columns from the mining model that the query returns, and specifies the name of the mining model used to generate the prediction:</span></span>  
  
```  
SELECT <select list> FROM [<mining model>]   
```  
  
 <span data-ttu-id="f0695-121">下一行程式碼會指出要執行的作業。</span><span class="sxs-lookup"><span data-stu-id="f0695-121">The next line of the code indicates the operation to perform.</span></span> <span data-ttu-id="f0695-122">由於您將針對每個資料行指定值並輸入與模型完全相符的資料行名稱，因此可以使用 `NATURAL PREDICTION JOIN` 語法。</span><span class="sxs-lookup"><span data-stu-id="f0695-122">Because you will specify values for each of the columns and type the column names exactly so as to match the model, you can use the `NATURAL PREDICTION JOIN` syntax.</span></span> <span data-ttu-id="f0695-123">但是，如果資料行名稱不同，您就必須加入 `ON` 子句來指定此模型中的資料行以及新資料中的資料行之間的對應。</span><span class="sxs-lookup"><span data-stu-id="f0695-123">However, if the column names were different, you would have to specify mappings between the columns in the model and the columns in the new data by adding an `ON` clause.</span></span>  
  
```  
[NATURAL] PREDICTION JOIN  
```  
  
 <span data-ttu-id="f0695-124">接下來幾行的程式碼定義購物車中的產品，它們將用來預測客戶可能加入的其他產品：</span><span class="sxs-lookup"><span data-stu-id="f0695-124">The next lines of the code define the products in the shopping cart that will be used to predict additional products that a customer will add:</span></span>  
  
```  
(SELECT '<value>' AS [<column>],   
    (SELECT 'value' AS [<nested column>] UNION  
        SELECT 'value' AS [<nested column>] ...)   
    AS [<nested table>])  
```  
  
## <a name="lesson-tasks"></a><span data-ttu-id="f0695-125">課程工作</span><span class="sxs-lookup"><span data-stu-id="f0695-125">Lesson Tasks</span></span>  
 <span data-ttu-id="f0695-126">您將在這一課執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="f0695-126">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="f0695-127">建立一個查詢，而此查詢會依據客戶購物車中已有的項目來預測客戶可能購買的其他項目。</span><span class="sxs-lookup"><span data-stu-id="f0695-127">Create a query that predicts what other items a customer will likely purchase, based on items already existing in their shopping cart.</span></span> <span data-ttu-id="f0695-128">您將使用具有預設*MINIMUM_PROBABILITY*的「採礦模型」來建立此查詢。</span><span class="sxs-lookup"><span data-stu-id="f0695-128">You will create this query by using the mining model with the default *MINIMUM_PROBABILITY*.</span></span>  
  
-   <span data-ttu-id="f0695-129">建立一個查詢，而此查詢會依據客戶購物車中已有的項目來預測客戶可能購買的其他項目。</span><span class="sxs-lookup"><span data-stu-id="f0695-129">Create a query that predicts what other items a customer will likely purchase based on items already existing in their shopping cart.</span></span> <span data-ttu-id="f0695-130">此查詢是以不同的模型為基礎，其中*MINIMUM_PROBABILITY*已設定為0.01。</span><span class="sxs-lookup"><span data-stu-id="f0695-130">This query is based on a different model, in which *MINIMUM_PROBABILITY* has been set to 0.01.</span></span> <span data-ttu-id="f0695-131">因為關聯模型中*MINIMUM_PROBABILITY*的預設值是0.3，所以此模型上的查詢應該會傳回比預設模型上的查詢更多的可能專案。</span><span class="sxs-lookup"><span data-stu-id="f0695-131">Because the default value for *MINIMUM_PROBABILITY* in association models is 0.3, the query on this model should return more possible items than the query on the default model.</span></span>  
  
## <a name="create-a-prediction-by-using-a-model-with-the-default-minimum_probability"></a><span data-ttu-id="f0695-132">使用具有預設 MINIMUM_PROBABILITY 的模型建立預測</span><span class="sxs-lookup"><span data-stu-id="f0695-132">Create a Prediction by Using a Model with the Default MINIMUM_PROBABILITY</span></span>  
  
#### <a name="to-create-an-association-query"></a><span data-ttu-id="f0695-133">若要建立關聯查詢</span><span class="sxs-lookup"><span data-stu-id="f0695-133">To create an association query</span></span>  
  
1.  <span data-ttu-id="f0695-134">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX** ] 以開啟 [查詢編輯器]。</span><span class="sxs-lookup"><span data-stu-id="f0695-134">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open the Query Editor.</span></span>  
  
2.  <span data-ttu-id="f0695-135">將 `PREDICTION JOIN` 陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="f0695-135">Copy the generic example of the `PREDICTION JOIN` statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="f0695-136">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="f0695-136">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="f0695-137">成為：</span><span class="sxs-lookup"><span data-stu-id="f0695-137">with:</span></span>  
  
    ```  
    PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
     <span data-ttu-id="f0695-138">您可以只包含資料行名稱 [Products]，但藉由使用 [ [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx) ] 函式，您可以將演算法傳回的產品數目限制為三個。</span><span class="sxs-lookup"><span data-stu-id="f0695-138">You could just include the column name [Products], but by using the [Predict &#40;DMX&#41;](/sql/dmx/predict-dmx) function, you can limit the number of products that are returned by the algorithm to three.</span></span> <span data-ttu-id="f0695-139">您也可以使用 `INCLUDE_STATISTICS`，它可傳回每一項產品的支援、機率和調整機率。</span><span class="sxs-lookup"><span data-stu-id="f0695-139">You can also use `INCLUDE_STATISTICS`, which returns the support, probability, and adjusted probability for each product.</span></span> <span data-ttu-id="f0695-140">這些統計資料有助您評比預測的精確性。</span><span class="sxs-lookup"><span data-stu-id="f0695-140">These statistics help you rate the accuracy of the prediction.</span></span>  
  
4.  <span data-ttu-id="f0695-141">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="f0695-141">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="f0695-142">成為：</span><span class="sxs-lookup"><span data-stu-id="f0695-142">with:</span></span>  
  
    ```  
    [Default Association]  
    ```  
  
5.  <span data-ttu-id="f0695-143">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="f0695-143">Replace the following:</span></span>  
  
    ```  
    (SELECT '<value>' AS [<column>],   
        (SELECT 'value' AS [<nested column>] UNION  
            SELECT 'value' AS [<nested column>] ...)   
        AS [<nested table>])  
    ```  
  
     <span data-ttu-id="f0695-144">成為：</span><span class="sxs-lookup"><span data-stu-id="f0695-144">with:</span></span>  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     <span data-ttu-id="f0695-145">此陳述式會使用 `UNION` 陳述式來指定三項產品，而這些產品必須連同預測的產品一起加入購物車內。</span><span class="sxs-lookup"><span data-stu-id="f0695-145">This statement uses the `UNION` statement to specify three products that must be included in the shopping cart together with the predicted products.</span></span> <span data-ttu-id="f0695-146">`SELECT` 陳述式中的 Model 資料行會對應到巢狀產品資料表所包含的模型資料行。</span><span class="sxs-lookup"><span data-stu-id="f0695-146">The Model column in the `SELECT` statement corresponds to the model column that is contained in the nested products table.</span></span>  
  
     <span data-ttu-id="f0695-147">現在，完整的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="f0695-147">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
      PREDICT([Default Association].[Products],INCLUDE_STATISTICS,3)  
    From  
      [Default Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
6.  <span data-ttu-id="f0695-148">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="f0695-148">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="f0695-149">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `Association Prediction.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="f0695-149">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Association Prediction.dmx`.</span></span>  
  
8.  <span data-ttu-id="f0695-150">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f0695-150">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="f0695-151">此查詢會傳回一個包含三項產品的資料表：HL Mountain Tire、Fender Set - Mountain 和 ML Mountain Tire。</span><span class="sxs-lookup"><span data-stu-id="f0695-151">The query returns a table that contains three products: HL Mountain Tire, Fender Set - Mountain, and ML Mountain Tire.</span></span> <span data-ttu-id="f0695-152">此資料表會按照機率的順序列出這些傳回的產品。</span><span class="sxs-lookup"><span data-stu-id="f0695-152">The table lists these returned products in order of probability.</span></span> <span data-ttu-id="f0695-153">最有可能與查詢中指定之三項產品加入同一個購物車的傳回產品會顯示在資料表的最上方。</span><span class="sxs-lookup"><span data-stu-id="f0695-153">The returned product that is most likely to be included in the same shopping cart as the three products specified in the query appears at the top of the table.</span></span> <span data-ttu-id="f0695-154">後面兩項產品則是後續最有可能加入購物車的產品。</span><span class="sxs-lookup"><span data-stu-id="f0695-154">The two products that follow are the next most likely to be included in the shopping cart.</span></span> <span data-ttu-id="f0695-155">此資料表也包含描述預測精確性的統計資料。</span><span class="sxs-lookup"><span data-stu-id="f0695-155">The table also contains statistics describing the accuracy of the prediction.</span></span>  
  
## <a name="create-a-prediction-by-using-a-model-with-a-minimum_probability-of-001"></a><span data-ttu-id="f0695-156">使用具有 MINIMUM_PROBABILITY 0.01 的模型建立預測</span><span class="sxs-lookup"><span data-stu-id="f0695-156">Create a Prediction by Using a Model with a MINIMUM_PROBABILITY of 0.01</span></span>  
  
#### <a name="to-create-an-association-query"></a><span data-ttu-id="f0695-157">若要建立關聯查詢</span><span class="sxs-lookup"><span data-stu-id="f0695-157">To create an association query</span></span>  
  
1.  <span data-ttu-id="f0695-158">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX** ] 以開啟 [查詢編輯器]。</span><span class="sxs-lookup"><span data-stu-id="f0695-158">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open the Query Editor.</span></span>  
  
2.  <span data-ttu-id="f0695-159">將 `PREDICTION JOIN` 陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="f0695-159">Copy the generic example of the `PREDICTION JOIN` statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="f0695-160">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="f0695-160">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="f0695-161">成為：</span><span class="sxs-lookup"><span data-stu-id="f0695-161">with:</span></span>  
  
    ```  
    PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    ```  
  
4.  <span data-ttu-id="f0695-162">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="f0695-162">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="f0695-163">成為：</span><span class="sxs-lookup"><span data-stu-id="f0695-163">with:</span></span>  
  
    ```  
    [Modified Association]  
    ```  
  
5.  <span data-ttu-id="f0695-164">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="f0695-164">Replace the following:</span></span>  
  
    ```  
    (SELECT '<value>' AS [<column>],   
        (SELECT 'value' AS [<nested column>] UNION  
            SELECT 'value' AS [<nested column>] ...)   
        AS [<nested table>])  
    ```  
  
     <span data-ttu-id="f0695-165">成為：</span><span class="sxs-lookup"><span data-stu-id="f0695-165">with:</span></span>  
  
    ```  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
     <span data-ttu-id="f0695-166">此陳述式會使用 `UNION` 陳述式來指定三項產品，而這些產品必須連同預測的產品一起加入購物車內。</span><span class="sxs-lookup"><span data-stu-id="f0695-166">This statement uses the `UNION` statement to specify three products that must be included in the shopping cart together with the predicted products.</span></span> <span data-ttu-id="f0695-167">`SELECT` 陳述式中的 `[Model]` 資料行會對應到巢狀產品資料表中的資料行。</span><span class="sxs-lookup"><span data-stu-id="f0695-167">The `[Model]` column in the `SELECT` statement corresponds to the column in the nested products table.</span></span>  
  
     <span data-ttu-id="f0695-168">現在，完整的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="f0695-168">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
      PREDICT([Modified Association].[Products],INCLUDE_STATISTICS,3)  
    From  
      [Modified Association]  
    NATURAL PREDICTION JOIN  
    (SELECT (SELECT 'Mountain Bottle Cage' AS [Model]  
      UNION SELECT 'Mountain Tire Tube' AS [Model]  
      UNION SELECT 'Mountain-200' AS [Model]) AS [Products]) AS t  
    ```  
  
6.  <span data-ttu-id="f0695-169">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="f0695-169">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="f0695-170">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `Modified Association Prediction.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="f0695-170">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Modified Association Prediction.dmx`.</span></span>  
  
8.  <span data-ttu-id="f0695-171">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="f0695-171">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="f0695-172">此查詢會傳回一個包含三項產品的資料表：HL Mountain Tire、Water Bottle 和 Fender Set – Mountain。</span><span class="sxs-lookup"><span data-stu-id="f0695-172">The query returns a table that contains three products: HL Mountain Tire, Water Bottle, and Fender Set - Mountain.</span></span> <span data-ttu-id="f0695-173">此資料表會按照機率的順序列出這些產品。</span><span class="sxs-lookup"><span data-stu-id="f0695-173">The table lists these products in order of probability.</span></span> <span data-ttu-id="f0695-174">顯示在資料表最上方的產品就是最有可能與查詢中指定之三項產品加入同一個購物車的產品。</span><span class="sxs-lookup"><span data-stu-id="f0695-174">The product that appears at the top of the table is the product that is most likely to be included in the same shopping cart as the three products specified in the query.</span></span> <span data-ttu-id="f0695-175">其餘產品則是後續最有可能加入購物車的產品。</span><span class="sxs-lookup"><span data-stu-id="f0695-175">The remaining products are the next most likely to be included in the shopping cart.</span></span> <span data-ttu-id="f0695-176">此資料表也包含描述預測精確度的統計資料。</span><span class="sxs-lookup"><span data-stu-id="f0695-176">The table also contains statistics that describe the accuracy of the prediction.</span></span>  
  
     <span data-ttu-id="f0695-177">您可以從這個查詢的結果看到， *MINIMUM_PROBABILITY*參數的值會影響查詢所傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="f0695-177">You can see from the results of this query that the value of the *MINIMUM_PROBABILITY* parameter affects the results returned by the query.</span></span>  
  
 <span data-ttu-id="f0695-178">這是購物籃教學課程的最後步驟。</span><span class="sxs-lookup"><span data-stu-id="f0695-178">This is the last step in the Market Basket tutorial.</span></span> <span data-ttu-id="f0695-179">現在您擁有了一組模型，可用來預測客戶可能會同時購買的產品。</span><span class="sxs-lookup"><span data-stu-id="f0695-179">You now have a set of models that you can use to predict the products that customers might purchase at the same time.</span></span>  
  
 <span data-ttu-id="f0695-180">若要瞭解如何在另一個預測案例中使用 DMX，請參閱[自行車購買者 DMX 教學](../../2014/tutorials/bike-buyer-dmx-tutorial.md)課程。</span><span class="sxs-lookup"><span data-stu-id="f0695-180">To learn how to use DMX in another predictive scenario, see [Bike Buyer DMX Tutorial](../../2014/tutorials/bike-buyer-dmx-tutorial.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0695-181">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f0695-181">See Also</span></span>  
 <span data-ttu-id="f0695-182">[關聯模型查詢範例](../../2014/analysis-services/data-mining/association-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="f0695-182">[Association Model Query Examples](../../2014/analysis-services/data-mining/association-model-query-examples.md) </span></span>  
 [<span data-ttu-id="f0695-183">資料採礦查詢介面</span><span class="sxs-lookup"><span data-stu-id="f0695-183">Data Mining Query Interfaces</span></span>](../../2014/analysis-services/data-mining/data-mining-query-tools.md)  
  
  
