---
title: 第5課：執行預測查詢 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0037bd2f-aa2d-464b-bf86-b0210f0438b1
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a5f4d6dd79f62541e207df688349f694680e2421
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703525"
---
# <a name="lesson-5-executing-prediction-queries"></a><span data-ttu-id="4e921-102">第 5 課：執行預測查詢</span><span class="sxs-lookup"><span data-stu-id="4e921-102">Lesson 5: Executing Prediction Queries</span></span>
  <span data-ttu-id="4e921-103">在這一課，您將使用 SELECT 語句的[SELECT FROM \<model> 預測聯結 (DMX) ](/sql/dmx/select-from-model-cases-dmx)形式，根據您在[第2課：將採礦模型加入至關聯採礦結構](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)中所建立的決策樹模型，建立兩種不同類型的預測。</span><span class="sxs-lookup"><span data-stu-id="4e921-103">In this lesson, you will use the [SELECT FROM \<model> PREDICTION JOIN (DMX)](/sql/dmx/select-from-model-cases-dmx) form of the SELECT statement to create two different types of predictions based on the decision tree model you created in [Lesson 2: Adding Mining Models to the Association Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md).</span></span> <span data-ttu-id="4e921-104">這些預測類型定義如下。</span><span class="sxs-lookup"><span data-stu-id="4e921-104">These prediction types are defined below.</span></span>  
  
 <span data-ttu-id="4e921-105">單一查詢</span><span class="sxs-lookup"><span data-stu-id="4e921-105">Singleton Query</span></span>  
 <span data-ttu-id="4e921-106">進行預測時，使用單一查詢提供特定的值。</span><span class="sxs-lookup"><span data-stu-id="4e921-106">Use a singleton query to provide ad hoc values when making predictions.</span></span> <span data-ttu-id="4e921-107">例如，您可以將輸入傳遞到查詢 (例如，計算距離、區域碼，或客戶的孩童數目) 來判斷單一客戶是否可能是自行車購買者。</span><span class="sxs-lookup"><span data-stu-id="4e921-107">For example, you can determine whether a single customer is likely to be a bike buyer, by passing inputs to the query such as the commute distance, the area code, or the number of children of the customer.</span></span> <span data-ttu-id="4e921-108">單一查詢會根據這些輸入傳回一個值，表示該客戶購買自行車的可能性。</span><span class="sxs-lookup"><span data-stu-id="4e921-108">The singleton query returns a value that indicates how likely the person is to purchase a bicycle based on those inputs.</span></span>  
  
 <span data-ttu-id="4e921-109">批次查詢</span><span class="sxs-lookup"><span data-stu-id="4e921-109">Batch Query</span></span>  
 <span data-ttu-id="4e921-110">使用批次查詢來判斷潛在客戶資料表中，誰有可能購買自行車。</span><span class="sxs-lookup"><span data-stu-id="4e921-110">Use a batch query to determine who in a table of potential customers is likely to purchase a bicycle.</span></span> <span data-ttu-id="4e921-111">例如，如果行銷部門提供客戶和客戶屬性之清單給您，您可以使用批次預測來判斷資料表中誰有可能購買自行車。</span><span class="sxs-lookup"><span data-stu-id="4e921-111">For example, if your marketing department provides you with a list of customers and customer attributes, then you can use a batch prediction to determine who from the table is likely to purchase a bicycle.</span></span>  
  
 <span data-ttu-id="4e921-112">SELECT 語句的[SELECT FROM \<model> 預測聯結 (DMX) ](/sql/dmx/select-from-model-cases-dmx)形式包含三個部分：</span><span class="sxs-lookup"><span data-stu-id="4e921-112">The [SELECT FROM \<model> PREDICTION JOIN (DMX)](/sql/dmx/select-from-model-cases-dmx) form of the SELECT statement contains three parts:</span></span>  
  
-   <span data-ttu-id="4e921-113">結果傳回的採礦模型資料行和預測函數的清單。</span><span class="sxs-lookup"><span data-stu-id="4e921-113">A list of the mining model columns and prediction functions that are returned in the results.</span></span> <span data-ttu-id="4e921-114">這些結果也可以包含來源資料的輸入資料行。</span><span class="sxs-lookup"><span data-stu-id="4e921-114">The results can also contain input columns from the source data.</span></span>  
  
-   <span data-ttu-id="4e921-115">定義用來建立預測資料的來源查詢。</span><span class="sxs-lookup"><span data-stu-id="4e921-115">The source query defining the data that is being used to create a prediction.</span></span> <span data-ttu-id="4e921-116">例如，在批次查詢中，這可能是一份客戶名單。</span><span class="sxs-lookup"><span data-stu-id="4e921-116">For example, in a batch query this could be a list of customers.</span></span>  
  
-   <span data-ttu-id="4e921-117">採礦模型資料行和來源資料之間的對應。</span><span class="sxs-lookup"><span data-stu-id="4e921-117">A mapping between the mining model columns and the source data.</span></span> <span data-ttu-id="4e921-118">如果這些名稱相符，您就可以使用 NATURAL 語法，並省略資料行對應。</span><span class="sxs-lookup"><span data-stu-id="4e921-118">If these names match, then you can use NATURAL syntax and leave out the column mappings.</span></span>  
  
 <span data-ttu-id="4e921-119">您可以使用預測函數，進一步加強查詢。</span><span class="sxs-lookup"><span data-stu-id="4e921-119">You can further enhance the query by using prediction functions.</span></span> <span data-ttu-id="4e921-120">預測函數提供其他資訊，例如發生預測的機率，並提供對培訓資料集的預測支援。</span><span class="sxs-lookup"><span data-stu-id="4e921-120">Prediction functions provide additional information, such as the probability of a prediction occurring, and provide support for the prediction in the training dataset.</span></span> <span data-ttu-id="4e921-121">如需預測函數的詳細資訊，請參閱[&#40;DMX&#41;](/sql/dmx/functions-dmx)的函式。</span><span class="sxs-lookup"><span data-stu-id="4e921-121">For more information about prediction functions, see [Functions &#40;DMX&#41;](/sql/dmx/functions-dmx).</span></span>  
  
 <span data-ttu-id="4e921-122">此教學課程中的預測是以 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 範例資料庫中的 ProspectiveBuyer 資料表為基礎。</span><span class="sxs-lookup"><span data-stu-id="4e921-122">The predictions in this tutorial are based on the ProspectiveBuyer table in the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database.</span></span> <span data-ttu-id="4e921-123">ProspectiveBuyer 資料表包含潛在客戶及其相關聯特性的清單。</span><span class="sxs-lookup"><span data-stu-id="4e921-123">The ProspectiveBuyer table contains a list of potential customers and their associated characteristics.</span></span> <span data-ttu-id="4e921-124">此資料表的客戶與用來建立決策樹採礦模型的客戶無關。</span><span class="sxs-lookup"><span data-stu-id="4e921-124">The customers in this table are independent of the customers that were used to create the decision tree mining model.</span></span>  
  
 <span data-ttu-id="4e921-125">您也可以在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中使用預測查詢產生器來建立預測。</span><span class="sxs-lookup"><span data-stu-id="4e921-125">You can also create predictions by using the prediction query builder in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="4e921-126">課程工作</span><span class="sxs-lookup"><span data-stu-id="4e921-126">Lesson Tasks</span></span>  
 <span data-ttu-id="4e921-127">您將在這一課執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="4e921-127">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="4e921-128">建立單一查詢來判斷特定客戶是否有可能購買自行車。</span><span class="sxs-lookup"><span data-stu-id="4e921-128">Create a singleton query to determine whether a specific customer is likely to purchase a bicycle.</span></span>  
  
-   <span data-ttu-id="4e921-129">建立批次查詢來判斷客戶資料表中列出的碼些客戶可能購買自行車。</span><span class="sxs-lookup"><span data-stu-id="4e921-129">Create a batch query to determine which customers, listed in a table of customers, are likely to purchase a bicycle.</span></span>  
  
## <a name="singleton-query"></a><span data-ttu-id="4e921-130">單一查詢</span><span class="sxs-lookup"><span data-stu-id="4e921-130">Singleton Query</span></span>  
 <span data-ttu-id="4e921-131">第一個步驟是在單一預測查詢中，使用[從 &#60;模型&#62; 預測聯結 &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx)的 [選取]。</span><span class="sxs-lookup"><span data-stu-id="4e921-131">The first step is to use the [SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx) in a singleton prediction query.</span></span> <span data-ttu-id="4e921-132">以下是單一陳述式的一般範例：</span><span class="sxs-lookup"><span data-stu-id="4e921-132">The following is a generic example of the singleton statement:</span></span>  
  
```  
SELECT <select list> FROM [<mining model name>]   
NATURAL PREDICTION JOIN  
(SELECT '<value>' AS [<column>], ...)  
AS [<input alias>]  
```  
  
 <span data-ttu-id="4e921-133">第一行程式碼會定義在採礦模型中應該由查詢傳回的資料行，並且指定用來產生預測的採礦模型：</span><span class="sxs-lookup"><span data-stu-id="4e921-133">The first line of the code defines the columns from the mining model that the query should return, and specifies the mining model that is used to generate the prediction:</span></span>  
  
```  
SELECT <select list> FROM [<mining model name>]   
```  
  
 <span data-ttu-id="4e921-134">接下來幾行的程式碼定義您用來建立預測的客戶特性：</span><span class="sxs-lookup"><span data-stu-id="4e921-134">The next lines of the code define the characteristics of the customer that you use to create a prediction:</span></span>  
  
```  
NATURAL PREDICTION JOIN  
(SELECT '<value>' AS [<column>], ...)  
AS [<input alias>]  
ORDER BY <expression>  
```  
  
 <span data-ttu-id="4e921-135">如果您指定 NATURAL PREDICTION JOIN，伺服器會根據資料行名稱來比對模型的每一個資料行與輸入的資料行。</span><span class="sxs-lookup"><span data-stu-id="4e921-135">If you specify NATURAL PREDICTION JOIN, the server matches each column from the model to a column from the input, based on column names.</span></span> <span data-ttu-id="4e921-136">如果資料行名稱不符，就會忽略這些資料行。</span><span class="sxs-lookup"><span data-stu-id="4e921-136">If column names do not match, the columns are ignored.</span></span>  
  
#### <a name="to-create-a-singleton-prediction-query"></a><span data-ttu-id="4e921-137">若要建立單一預測查詢</span><span class="sxs-lookup"><span data-stu-id="4e921-137">To create a singleton prediction query</span></span>  
  
1.  <span data-ttu-id="4e921-138">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX**]。</span><span class="sxs-lookup"><span data-stu-id="4e921-138">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="4e921-139">此時會開啟 [查詢編輯器] 且包含新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="4e921-139">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="4e921-140">將單一陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="4e921-140">Copy the generic example of the singleton statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="4e921-141">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="4e921-141">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="4e921-142">成為：</span><span class="sxs-lookup"><span data-stu-id="4e921-142">with:</span></span>  
  
    ```  
    [Bike Buyer] AS Buyer, PredictHistogram([Bike Buyer]) AS Statistics  
    ```  
  
     <span data-ttu-id="4e921-143">AS 陳述式是用來建立查詢傳回之資料行的別名。</span><span class="sxs-lookup"><span data-stu-id="4e921-143">The AS statement is used to alias columns returned by the query.</span></span> <span data-ttu-id="4e921-144">[PredictHistogram](/sql/dmx/predicthistogram-dmx)函數會傳回關於預測的統計資料，包括機率和支援。</span><span class="sxs-lookup"><span data-stu-id="4e921-144">The [PredictHistogram](/sql/dmx/predicthistogram-dmx) function returns statistics about the prediction, including the probability and the support.</span></span> <span data-ttu-id="4e921-145">如需可用於預測語句之函數的詳細資訊，請參閱[&#40;DMX&#41;](/sql/dmx/functions-dmx)的函式。</span><span class="sxs-lookup"><span data-stu-id="4e921-145">For more information about the functions that can be used in a prediction statement, see [Functions &#40;DMX&#41;](/sql/dmx/functions-dmx).</span></span>  
  
4.  <span data-ttu-id="4e921-146">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="4e921-146">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="4e921-147">成為：</span><span class="sxs-lookup"><span data-stu-id="4e921-147">with:</span></span>  
  
    ```  
    [Decision Tree]  
    ```  
  
5.  <span data-ttu-id="4e921-148">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="4e921-148">Replace the following:</span></span>  
  
    ```  
    (SELECT '<value>' AS [<column name>], ...)  AS t  
    ```  
  
     <span data-ttu-id="4e921-149">成為：</span><span class="sxs-lookup"><span data-stu-id="4e921-149">with:</span></span>  
  
    ```  
    (SELECT 35 AS [Age],  
      '5-10 Miles' AS [Commute Distance],  
      '1' AS [House Owner Flag],  
      2 AS [Number Cars Owned],  
      2 AS [Total Children]) AS t  
    ```  
  
     <span data-ttu-id="4e921-150">現在，完整的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="4e921-150">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
       [Bike Buyer] AS Buyer,  
       PredictHistogram([Bike Buyer]) AS Statistics  
    FROM  
       [Decision Tree]  
    NATURAL PREDICTION JOIN  
    (SELECT 35 AS [Age],  
       '5-10 Miles' AS [Commute Distance],  
       '1' AS [House Owner Flag],  
       2 AS [Number Cars Owned],  
       2 AS [Total Children]) AS t  
    ```  
  
6.  <span data-ttu-id="4e921-151">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="4e921-151">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="4e921-152">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `Singleton_Query.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="4e921-152">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Singleton_Query.dmx`.</span></span>  
  
8.  <span data-ttu-id="4e921-153">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4e921-153">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="4e921-154">此查詢傳回有關具有指定特性的客戶是否會購買自行車的預測，以及有關該預測的統計資料。</span><span class="sxs-lookup"><span data-stu-id="4e921-154">The query returns a prediction about whether a customer with the specified characteristics will purchase a bicycle, as well as statistics about that prediction.</span></span>  
  
## <a name="batch-query"></a><span data-ttu-id="4e921-155">批次查詢</span><span class="sxs-lookup"><span data-stu-id="4e921-155">Batch Query</span></span>  
 <span data-ttu-id="4e921-156">下一個步驟是在批次預測查詢中，使用[從 &#60;模型&#62; 預測聯結 &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx)的 [選取]。</span><span class="sxs-lookup"><span data-stu-id="4e921-156">The next step is to use the [SELECT FROM &#60;model&#62; PREDICTION JOIN &#40;DMX&#41;](/sql/dmx/select-from-model-cases-dmx) in a batch prediction query.</span></span> <span data-ttu-id="4e921-157">以下是批次陳述式的一般範例：</span><span class="sxs-lookup"><span data-stu-id="4e921-157">The following is a generic example of a batch statement:</span></span>  
  
```  
SELECT TOP <number> <select list>   
FROM [<mining model name>]  
PREDICTION JOIN  
OPENQUERY([<datasource>],'<SELECT statement>')  
  AS [<input alias>]  
ON <on clause, mapping,>  
WHERE <where clause, boolean expression,>  
ORDER BY <expression>  
```  
  
 <span data-ttu-id="4e921-158">如同在單一查詢一樣，程式碼的前兩行定義在採礦模型中由查詢傳回的資料行，以及用來產生預測的採礦模型名稱。</span><span class="sxs-lookup"><span data-stu-id="4e921-158">As in the singleton query, the first two lines of the code define the columns from mining model that the query returns, as well as the name of the mining model that is used to generate the prediction.</span></span> <span data-ttu-id="4e921-159">TOP \<number> 語句指定查詢只會傳回所指定的數位或結果 \<number> 。</span><span class="sxs-lookup"><span data-stu-id="4e921-159">The TOP \<number> statement specifies that the query will only return the number or the results specified by \<number>.</span></span>  
  
 <span data-ttu-id="4e921-160">接下來幾行的程式碼定義預測所依據的來源資料。</span><span class="sxs-lookup"><span data-stu-id="4e921-160">The next lines of the code define the source data that the predictions are based on:</span></span>  
  
```  
OPENQUERY([<datasource>],'<SELECT statement>')  
  AS [<input alias>]  
```  
  
 <span data-ttu-id="4e921-161">對於擷取來源資料的方法，您有幾個選項，但在此教學課程中，您將使用 OPENQUERY。</span><span class="sxs-lookup"><span data-stu-id="4e921-161">You have several options for the method of retrieving the source data, but in this tutorial, you will use OPENQUERY.</span></span> <span data-ttu-id="4e921-162">如需可用選項的詳細資訊，請參閱[&#60;來源資料查詢&#62;](/sql/dmx/source-data-query)。</span><span class="sxs-lookup"><span data-stu-id="4e921-162">For more information about the options available, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
 <span data-ttu-id="4e921-163">下一行定義採礦模型中的來源資料行與來源資料中資料行之間的對應：</span><span class="sxs-lookup"><span data-stu-id="4e921-163">The next line defines the mapping between the source columns in the mining model and the columns in the source data:</span></span>  
  
```  
ON <column mappings>  
```  
  
 <span data-ttu-id="4e921-164">WHERE 子句篩選預測查詢所傳回的結果：</span><span class="sxs-lookup"><span data-stu-id="4e921-164">The WHERE clause filters the results returned by the prediction query:</span></span>  
  
```  
WHERE <where clause, boolean expression,>  
```  
  
 <span data-ttu-id="4e921-165">程式碼的最後一行和選擇性的行會指定結果排序所依據的資料行：</span><span class="sxs-lookup"><span data-stu-id="4e921-165">The last and optional line of the code specifies the column that the results will be ordered by:</span></span>  
  
```  
ORDER BY <expression> [DESC|ASC]  
```  
  
 <span data-ttu-id="4e921-166">搭配使用 ORDER BY 與 TOP \<number> 語句，以篩選傳回的結果。</span><span class="sxs-lookup"><span data-stu-id="4e921-166">Use ORDER BY in combination with the TOP \<number> statement, to filter the results that are returned.</span></span> <span data-ttu-id="4e921-167">例如，在此預測中，您將按預測的正確機率排序，傳回前十個自行車買主。</span><span class="sxs-lookup"><span data-stu-id="4e921-167">For example, in this prediction you will return the top ten bike buyers, ordered by the probability of the prediction being correct.</span></span> <span data-ttu-id="4e921-168">您可以使用 [DESC|ASC] 語法來控制顯示結果的順序。</span><span class="sxs-lookup"><span data-stu-id="4e921-168">You can use [DESC|ASC] syntax to control the order in which the results are displayed.</span></span>  
  
#### <a name="to-create-a-batch-prediction-query"></a><span data-ttu-id="4e921-169">若要建立批次預測查詢</span><span class="sxs-lookup"><span data-stu-id="4e921-169">To create a batch prediction query</span></span>  
  
1.  <span data-ttu-id="4e921-170">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX**]。</span><span class="sxs-lookup"><span data-stu-id="4e921-170">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="4e921-171">此時會開啟 [查詢編輯器] 且包含新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="4e921-171">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="4e921-172">將批次陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="4e921-172">Copy the generic example of the batch statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="4e921-173">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="4e921-173">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="4e921-174">成為：</span><span class="sxs-lookup"><span data-stu-id="4e921-174">with:</span></span>  
  
    ```  
    SELECT  
      TOP 10  
      t.[LastName],  
      t.[FirstName],  
      [Decision Tree].[Bike Buyer],  
      PredictProbability([Bike Buyer])  
    ```  
  
     <span data-ttu-id="4e921-175">TOP 10 子句指定查詢只傳回前十個結果。</span><span class="sxs-lookup"><span data-stu-id="4e921-175">The TOP 10 clause specifies that only the top ten results will be returned by the query.</span></span> <span data-ttu-id="4e921-176">此查詢中的 ORDER BY 陳述式是按預測的正確機率來排序結果，因此，只傳回十個最可能的結果。</span><span class="sxs-lookup"><span data-stu-id="4e921-176">The ORDER BY statement in this query orders the results by the probability of the prediction being correct, so only the ten most likely results will be returned.</span></span>  
  
4.  <span data-ttu-id="4e921-177">取代下列預留位置：</span><span class="sxs-lookup"><span data-stu-id="4e921-177">Replace the following placeholder:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="4e921-178">改為模型的名稱：</span><span class="sxs-lookup"><span data-stu-id="4e921-178">With the name of the model:</span></span>  
  
    ```  
    [Decision Tree]  
    ```  
  
5.  <span data-ttu-id="4e921-179">取代下列泛用 OPENQUERY 陳述式：</span><span class="sxs-lookup"><span data-stu-id="4e921-179">Replace the following generic OPENQUERY statement:</span></span>  
  
    ```  
    OPENQUERY([<datasource>],'<SELECT statement>')  
    ```  
  
     <span data-ttu-id="4e921-180">改為參考目前 Adventureworks 資料倉儲的陳述式，例如：</span><span class="sxs-lookup"><span data-stu-id="4e921-180">With a statement that references the current Adventureworks data warehouse, such as:</span></span>  
  
    ```  
    OPENQUERY([Adventure Works DW 2014],  
      'SELECT  
        [LastName],  
        [FirstName],  
        [MaritalStatus],  
        [Gender],  
        [YearlyIncome],  
        [TotalChildren],  
        [NumberChildrenAtHome],  
        [Education],  
        [Occupation],  
        [HouseOwnerFlag],  
        [NumberCarsOwned]  
      FROM  
        [dbo].[ProspectiveBuyer]  
      ') AS t  
    ```  
  
6.  <span data-ttu-id="4e921-181">取代下列泛用語法：</span><span class="sxs-lookup"><span data-stu-id="4e921-181">Replace the following generic syntax:</span></span>  
  
    ```  
    <ON clause, mapping,>   
    WHERE <where clause, boolean expression,>  
    ORDER BY <expression>  
    ```  
  
     <span data-ttu-id="4e921-182">改為此模型和輸入資料集所需的資料行對應：</span><span class="sxs-lookup"><span data-stu-id="4e921-182">With the column mappings needed for this model and input data set:</span></span>  
  
    ```  
    [Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
      [Decision Tree].[Gender] = t.[Gender] AND  
      [Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
      [Decision Tree].[Total Children] = t.[TotalChildren] AND  
      [Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
      [Decision Tree].[Education] = t.[Education] AND  
      [Decision Tree].[Occupation] = t.[Occupation] AND  
      [Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
      [Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
    WHERE [Decision Tree].[Bike Buyer] =1  
    ORDER BY PredictProbability([Bike Buyer]) DESC  
    ```  
  
     <span data-ttu-id="4e921-183">指定 `DESC`，先列出具有最高機率的結果。</span><span class="sxs-lookup"><span data-stu-id="4e921-183">Specify `DESC` in order to list the results with the highest probability first.</span></span>  
  
     <span data-ttu-id="4e921-184">現在，完整的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="4e921-184">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT  
      TOP 10  
      t.[LastName],  
      t.[FirstName],  
      [Decision Tree].[Bike Buyer],  
      PredictProbability([Bike Buyer])  
    FROM  
      [Decision Tree]  
    PREDICTION JOIN  
      OPENQUERY([Adventure Works DW 2014],  
        'SELECT  
          [LastName],  
          [FirstName],  
          [MaritalStatus],  
          [Gender],  
          [YearlyIncome],  
          [TotalChildren],  
          [NumberChildrenAtHome],  
          [Education],  
          [Occupation],  
          [HouseOwnerFlag],  
          [NumberCarsOwned]  
        FROM  
          [dbo].[ProspectiveBuyer]  
        ') AS t  
    ON  
      [Decision Tree].[Marital Status] = t.[MaritalStatus] AND  
      [Decision Tree].[Gender] = t.[Gender] AND  
      [Decision Tree].[Yearly Income] = t.[YearlyIncome] AND  
      [Decision Tree].[Total Children] = t.[TotalChildren] AND  
      [Decision Tree].[Number Children At Home] = t.[NumberChildrenAtHome] AND  
      [Decision Tree].[Education] = t.[Education] AND  
      [Decision Tree].[Occupation] = t.[Occupation] AND  
      [Decision Tree].[House Owner Flag] = t.[HouseOwnerFlag] AND  
      [Decision Tree].[Number Cars Owned] = t.[NumberCarsOwned]  
    WHERE [Decision Tree].[Bike Buyer] =1  
    ORDER BY PredictProbability([Bike Buyer]) DESC  
    ```  
  
7.  <span data-ttu-id="4e921-185">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="4e921-185">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
8.  <span data-ttu-id="4e921-186">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `Batch_Prediction.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="4e921-186">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Batch_Prediction.dmx`.</span></span>  
  
9. <span data-ttu-id="4e921-187">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="4e921-187">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="4e921-188">查詢傳回一份資料表，其中包含客戶名稱、每一個客戶是否有可能購買自行車的預測及預測的機率。</span><span class="sxs-lookup"><span data-stu-id="4e921-188">The query returns a table containing customer names, a prediction of whether each customer will purchase a bicycle, and the probability of the prediction.</span></span>  
  
 <span data-ttu-id="4e921-189">這是 Bike Buyer 教學課程的最後步驟。</span><span class="sxs-lookup"><span data-stu-id="4e921-189">This is the last step in the Bike Buyer tutorial.</span></span> <span data-ttu-id="4e921-190">現在您已有採礦模型集合，可用來探索客戶之間的相似性，並預測潛在客戶是否會購買自行車。</span><span class="sxs-lookup"><span data-stu-id="4e921-190">You now have a set of mining models that you can use to explore similarities between you customers and predict whether potential customers will purchase a bicycle.</span></span>  
  
 <span data-ttu-id="4e921-191">若要瞭解如何在購物籃案例中使用 DMX，請參閱[購物籃 DMX 教學](../../2014/tutorials/market-basket-dmx-tutorial.md)課程。</span><span class="sxs-lookup"><span data-stu-id="4e921-191">To learn how to use DMX in a Market Basket scenario, see [Market Basket DMX Tutorial](../../2014/tutorials/market-basket-dmx-tutorial.md).</span></span>  
  
  
