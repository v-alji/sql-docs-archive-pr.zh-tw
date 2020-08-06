---
title: 第4課：流覽自行車購買者採礦模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8de3c500-f881-42da-a096-b6c03300d58d
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 709df371d840d4b24e420b4fcd08750fd31e8075
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594881"
---
# <a name="lesson-4-browsing-the-bike-buyer-mining-models"></a><span data-ttu-id="716ea-102">第 4 課：瀏覽自行車買主採礦模型</span><span class="sxs-lookup"><span data-stu-id="716ea-102">Lesson 4: Browsing the Bike Buyer Mining Models</span></span>
  <span data-ttu-id="716ea-103">在這一課，您將使用[SELECT (DMX) ](/sql/dmx/select-dmx)語句來流覽決策樹中的內容，以及在[第2課：將採礦模型加入至預測性採礦結構](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)中所建立的叢集化採礦模型。</span><span class="sxs-lookup"><span data-stu-id="716ea-103">In this lesson, you will use the [SELECT (DMX)](/sql/dmx/select-dmx) statement to explore the content in the decision tree and clustering mining models that you created in [Lesson 2: Adding Mining Models to the Predictive Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md).</span></span>  
  
 <span data-ttu-id="716ea-104">包含在採礦模型中的資料行不是採礦結構所定義的資料行，而是描述該演算法所發現的趨勢和模式的一組特定資料行。</span><span class="sxs-lookup"><span data-stu-id="716ea-104">The columns contained in a mining model are not the columns defined by the mining structure, but instead are a specific set of columns that describe the trends and patterns that are found by the algorithm.</span></span> <span data-ttu-id="716ea-105">DMSCHEMA_MINING_MODEL_CONTENT 資料列[集](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)架構資料列集中會描述這些採礦模型資料行。</span><span class="sxs-lookup"><span data-stu-id="716ea-105">These mining model columns are described in the [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset) schema rowset.</span></span> <span data-ttu-id="716ea-106">例如，內容結構描述資料列集的 MODEL_NAME 資料行包含採礦模型的名稱。</span><span class="sxs-lookup"><span data-stu-id="716ea-106">For example, the MODEL_NAME column in the content schema rowset contains the name of the mining model.</span></span> <span data-ttu-id="716ea-107">若為群集採礦模型，NODE_CAPTION 資料行包含每一個群集的名稱，NODE_DESCRIPTION 資料行包含每一個群集之特性的描述。</span><span class="sxs-lookup"><span data-stu-id="716ea-107">For a clustering mining model, the NODE_CAPTION column contains the name of each cluster, and the NODE_DESCRIPTION column contains a description of the characteristics of each cluster.</span></span> <span data-ttu-id="716ea-108">您可以使用 SELECT FROM 來流覽這些資料行 \<model> 。DMX 中的 CONTENT 語句。</span><span class="sxs-lookup"><span data-stu-id="716ea-108">You can browse these columns by using the SELECT FROM \<model>.CONTENT statement in DMX.</span></span> <span data-ttu-id="716ea-109">您也可以使用此陳述式來探索用來建立採礦模型的資料。</span><span class="sxs-lookup"><span data-stu-id="716ea-109">You can also use this statement to explore the data that was used to create the mining model.</span></span> <span data-ttu-id="716ea-110">您必須在採礦結構中啟用鑽研，才能使用此陳述式。</span><span class="sxs-lookup"><span data-stu-id="716ea-110">Drillthrough must be enabled on the mining structure in order to use this statement.</span></span> <span data-ttu-id="716ea-111">如需語句的詳細資訊，請參閱[SELECT FROM &#60;model&#62;。&#40;DMX&#41;的案例](/sql/dmx/select-from-model-content-dmx)。</span><span class="sxs-lookup"><span data-stu-id="716ea-111">For more information about the statement, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).</span></span>  
  
 <span data-ttu-id="716ea-112">您也可以使用 SELECT DISTINCT 陳述式來傳回分隔資料行的所有狀態。</span><span class="sxs-lookup"><span data-stu-id="716ea-112">You can also return all the states of a discrete column by using the SELECT DISTINCT statement.</span></span> <span data-ttu-id="716ea-113">例如，如果您在性別資料行執行此作業，該查詢將傳回 `male` 和 `female`。</span><span class="sxs-lookup"><span data-stu-id="716ea-113">For example, if you perform this operation on a gender column, the query will return `male` and `female`.</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="716ea-114">課程工作</span><span class="sxs-lookup"><span data-stu-id="716ea-114">Lesson Tasks</span></span>  
 <span data-ttu-id="716ea-115">您將在這一課執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="716ea-115">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="716ea-116">探索採礦模型所包含的內容</span><span class="sxs-lookup"><span data-stu-id="716ea-116">Explore the content contained within the mining models</span></span>  
  
-   <span data-ttu-id="716ea-117">從用來培訓採礦模型的來源資料中傳回案例</span><span class="sxs-lookup"><span data-stu-id="716ea-117">Return the cases from the source data that was used to train the mining models</span></span>  
  
-   <span data-ttu-id="716ea-118">探索特定分隔資料行可用的不同狀態</span><span class="sxs-lookup"><span data-stu-id="716ea-118">Explore the different states available for a specific discrete column</span></span>  
  
## <a name="returning-the-content-of-a-mining-model"></a><span data-ttu-id="716ea-119">傳回採礦模型的內容</span><span class="sxs-lookup"><span data-stu-id="716ea-119">Returning the Content of a Mining Model</span></span>  
 <span data-ttu-id="716ea-120">在這一課，您會使用[&#60;模型&#62; 中的 [選取]。CONTENT &#40;DMX&#41;](/sql/dmx/select-from-model-dimension-content-dmx)語句，以傳回群集模型的內容。</span><span class="sxs-lookup"><span data-stu-id="716ea-120">In this lesson, you use the [SELECT FROM &#60;model&#62;.CONTENT &#40;DMX&#41;](/sql/dmx/select-from-model-dimension-content-dmx) statement to return the contents of the clustering model.</span></span>  
  
 <span data-ttu-id="716ea-121">以下是 SELECT FROM 的一般範例 \<model> 。CONTENT 語句：</span><span class="sxs-lookup"><span data-stu-id="716ea-121">The following is a generic example of the SELECT FROM \<model>.CONTENT statement:</span></span>  
  
```  
SELECT <select list> FROM [<mining model>].CONTENT  
WHERE <where clause>  
```  
  
 <span data-ttu-id="716ea-122">程式碼的第一行定義要從採礦模型內容中傳回的資料行，及其相關聯的採礦模型：</span><span class="sxs-lookup"><span data-stu-id="716ea-122">The first line of the code defines the columns to return from the mining model content, and the mining model they are associated with:</span></span>  
  
```  
SELECT <select list> FROM [<mining model].CONTENT  
```  
  
 <span data-ttu-id="716ea-123">採礦模型名稱旁邊的 .CONTENT 子句指定您要從採礦模型傳回內容。</span><span class="sxs-lookup"><span data-stu-id="716ea-123">The .CONTENT clause next to the name of the mining model specifies that you are returning content from the mining model.</span></span> <span data-ttu-id="716ea-124">如需有關「採礦模型」中所包含之資料行的詳細資訊，請參閱 DMSCHEMA_MINING_MODEL_CONTENT 資料列[集](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)。</span><span class="sxs-lookup"><span data-stu-id="716ea-124">For more information about the columns contained in the mining model, see [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).</span></span>  
  
 <span data-ttu-id="716ea-125">您可以選擇性地使用程式碼的最後一行來篩選陳述式傳回的結果：</span><span class="sxs-lookup"><span data-stu-id="716ea-125">You can optionally use the final line of the code to filter the results returned by the statement:</span></span>  
  
```  
WHERE <where clause>  
```  
  
 <span data-ttu-id="716ea-126">例如，如果您想要將查詢的結果限制為只有包含大量案例的群集，您可以將下列 WHERE 子句加入 SELECT 陳述式中：</span><span class="sxs-lookup"><span data-stu-id="716ea-126">For example, if you want to restrict the results of the query to only the clusters that contain a high number of cases, you can add the following WHERE clause to the SELECT statement:</span></span>  
  
```  
WHERE NODE_SUPPORT > 100  
```  
  
 <span data-ttu-id="716ea-127">如需使用 WHERE 語句的詳細資訊，請參閱[SELECT &#40;DMX&#41;](/sql/dmx/select-dmx)。</span><span class="sxs-lookup"><span data-stu-id="716ea-127">For more information about using the WHERE statement, see [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).</span></span>  
  
#### <a name="to-return-the-content-of-the-clustering-mining-model"></a><span data-ttu-id="716ea-128">若要傳回群集採礦模型的內容</span><span class="sxs-lookup"><span data-stu-id="716ea-128">To return the content of the clustering mining model</span></span>  
  
1.  <span data-ttu-id="716ea-129">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX**]。</span><span class="sxs-lookup"><span data-stu-id="716ea-129">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="716ea-130">此時會開啟 [查詢編輯器] 且包含新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="716ea-130">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="716ea-131">從複製 SELECT 的一般範例 \<model> 。CONTENT 語句放入空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="716ea-131">Copy the generic example of the SELECT FROM \<model>.CONTENT statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="716ea-132">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="716ea-132">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="716ea-133">成為：</span><span class="sxs-lookup"><span data-stu-id="716ea-133">with:</span></span>  
  
    ```  
    *  
    ```  
  
     <span data-ttu-id="716ea-134">您也可以使用 DMSCHEMA_MINING_MODEL_CONTENT 資料列集內所包含之任何資料[行](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset)的清單來取代 \*。</span><span class="sxs-lookup"><span data-stu-id="716ea-134">You can also replace \* with a list of any of the columns contained within the [DMSCHEMA_MINING_MODEL_CONTENT Rowset](https://docs.microsoft.com/bi-reference/schema-rowsets/data-mining/dmschema-mining-model-content-rowset).</span></span>  
  
4.  <span data-ttu-id="716ea-135">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="716ea-135">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="716ea-136">成為：</span><span class="sxs-lookup"><span data-stu-id="716ea-136">with:</span></span>  
  
    ```  
    [Clustering]  
    ```  
  
     <span data-ttu-id="716ea-137">現在，完整的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="716ea-137">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT * FROM [Clustering].CONTENT  
    ```  
  
5.  <span data-ttu-id="716ea-138">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="716ea-138">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
6.  <span data-ttu-id="716ea-139">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `SELECT_CONTENT.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="716ea-139">In the **Save As** dialog box, browse to the appropriate folder, and name the file `SELECT_CONTENT.dmx`.</span></span>  
  
7.  <span data-ttu-id="716ea-140">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="716ea-140">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="716ea-141">此查詢會傳回採礦模型的內容。</span><span class="sxs-lookup"><span data-stu-id="716ea-141">The query returns the content of the mining model.</span></span>  
  
## <a name="use-drillthrough"></a><span data-ttu-id="716ea-142">使用鑽研</span><span class="sxs-lookup"><span data-stu-id="716ea-142">Use Drillthrough</span></span>  
 <span data-ttu-id="716ea-143">下一步是使用鑽研陳述式來傳回用來培訓決策樹採礦模型的案例取樣。</span><span class="sxs-lookup"><span data-stu-id="716ea-143">The next step is to use the drillthrough statement to return a sampling of the cases that were used to train the decision tree mining model.</span></span> <span data-ttu-id="716ea-144">在這一課，您會使用[&#60;模型&#62; 中的 [選取]。案例 &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx)語句，以傳回決策樹模型的內容。</span><span class="sxs-lookup"><span data-stu-id="716ea-144">In this lesson, you use the [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx) statement to return the contents of the decision tree model.</span></span>  
  
 <span data-ttu-id="716ea-145">以下是 SELECT FROM 的一般範例 \<model> 。案例語句：</span><span class="sxs-lookup"><span data-stu-id="716ea-145">The following is a generic example of the SELECT FROM \<model>.CASES statement:</span></span>  
  
```  
SELECT <select list>   
FROM [<mining model>].CASES  
WHERE IsInNode('<node id>')  
```  
  
 <span data-ttu-id="716ea-146">程式碼的第一行定義要從來源資料中傳回的資料行，及其包含的採礦模型：</span><span class="sxs-lookup"><span data-stu-id="716ea-146">The first line of the code defines the columns to return from the source data, and the mining model they are contained within:</span></span>  
  
```  
SELECT <select list> FROM [<mining model>].CASES  
```  
  
 <span data-ttu-id="716ea-147">.CASES 子句會指定您執行鑽研查詢。</span><span class="sxs-lookup"><span data-stu-id="716ea-147">The .CASES clause specifies that you are performing a drillthrough query.</span></span> <span data-ttu-id="716ea-148">若要使用鑽研，則當您建立採礦模型時必須啟用鑽研。</span><span class="sxs-lookup"><span data-stu-id="716ea-148">In order to use drillthrough you must enable drillthrough when you create the mining model.</span></span>  
  
 <span data-ttu-id="716ea-149">程式碼的最後一行是選用的，它指定採礦模型中您要求案例的節點：</span><span class="sxs-lookup"><span data-stu-id="716ea-149">The final line of the code is optional and specifies the node in the mining model that you are requesting cases from:</span></span>  
  
```  
WHERE IsInNode('<node id>')  
```  
  
 <span data-ttu-id="716ea-150">如需搭配 IsInNode 使用 WHERE 語句的詳細資訊，請參閱[SELECT FROM &#60;model&#62;。&#40;DMX&#41;的案例](/sql/dmx/select-from-model-content-dmx)。</span><span class="sxs-lookup"><span data-stu-id="716ea-150">For more information about using the WHERE statement with IsInNode, see [SELECT FROM &#60;model&#62;.CASES &#40;DMX&#41;](/sql/dmx/select-from-model-content-dmx).</span></span>  
  
#### <a name="to-return-the-cases-that-were-used-to-train-the-mining-model"></a><span data-ttu-id="716ea-151">若要傳回用來培訓採礦模型的案例</span><span class="sxs-lookup"><span data-stu-id="716ea-151">To return the cases that were used to train the mining model</span></span>  
  
1.  <span data-ttu-id="716ea-152">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX**]。</span><span class="sxs-lookup"><span data-stu-id="716ea-152">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="716ea-153">此時會開啟 [查詢編輯器] 且包含新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="716ea-153">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="716ea-154">從複製 SELECT 的一般範例 \<model> 。案例語句放入空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="716ea-154">Copy the generic example of the SELECT FROM \<model>.CASES statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="716ea-155">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="716ea-155">Replace the following:</span></span>  
  
    ```  
    <select list>   
    ```  
  
     <span data-ttu-id="716ea-156">成為：</span><span class="sxs-lookup"><span data-stu-id="716ea-156">with:</span></span>  
  
    ```  
    *  
    ```  
  
     <span data-ttu-id="716ea-157">您也可以將 \* 取代成來源資料 (例如 [Bike Buyer]) 所包含的任何資料行清單。</span><span class="sxs-lookup"><span data-stu-id="716ea-157">You can also replace \* with a list of any of the columns contained within the source data (such as [Bike Buyer]).</span></span>  
  
4.  <span data-ttu-id="716ea-158">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="716ea-158">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="716ea-159">成為：</span><span class="sxs-lookup"><span data-stu-id="716ea-159">with:</span></span>  
  
    ```  
    [Decision Tree]  
    ```  
  
     <span data-ttu-id="716ea-160">現在，完整的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="716ea-160">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT *   
    FROM [Decision Tree].CASES  
    ```  
  
5.  <span data-ttu-id="716ea-161">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="716ea-161">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
6.  <span data-ttu-id="716ea-162">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `SELECT_DRILLTHROUGH.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="716ea-162">In the **Save As** dialog box, browse to the appropriate folder, and name the file `SELECT_DRILLTHROUGH.dmx`.</span></span>  
  
7.  <span data-ttu-id="716ea-163">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="716ea-163">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="716ea-164">該查詢會傳回用來培訓決策樹採礦模型的來源資料。</span><span class="sxs-lookup"><span data-stu-id="716ea-164">The query returns the source data that was used to train the decision tree mining model.</span></span>  
  
## <a name="return-the-states-of-a-discrete-mining-model-column"></a><span data-ttu-id="716ea-165">傳回分隔採礦模型資料行的狀態</span><span class="sxs-lookup"><span data-stu-id="716ea-165">Return the States of a Discrete Mining Model Column</span></span>  
 <span data-ttu-id="716ea-166">下一步是使用 SELECT DISTINCT 陳述式來傳回指定的採礦模型資料行中不同的可能狀態。</span><span class="sxs-lookup"><span data-stu-id="716ea-166">The next step is to use the SELECT DISTINCT statement to return the different possible states in the specified mining model column.</span></span>  
  
 <span data-ttu-id="716ea-167">以下是 SELECT DISTINCT 陳述式的一般範例：</span><span class="sxs-lookup"><span data-stu-id="716ea-167">The following is a generic example of the SELECT DISTINCT statement:</span></span>  
  
```  
SELECT DISTINCT [<column>]   
FROM [<mining model>]  
```  
  
 <span data-ttu-id="716ea-168">程式碼的第一行定義傳回其狀態的採礦模型資料行：</span><span class="sxs-lookup"><span data-stu-id="716ea-168">The first line of the code defines the mining model columns for which the states are returned:</span></span>  
  
```  
SELECT DISTINCT [<column>]   
```  
  
 <span data-ttu-id="716ea-169">您必須包括 DISTINCT 才能傳回資料行的所有狀態。</span><span class="sxs-lookup"><span data-stu-id="716ea-169">You must include DISTINCT in order to return all of the states of the column.</span></span> <span data-ttu-id="716ea-170">如果您排除 DISTINCT，則完整陳述式將成為預測的捷徑，並傳回所指定資料行最可能的狀態。</span><span class="sxs-lookup"><span data-stu-id="716ea-170">If you exclude DISTINCT, then the full statement becomes a shortcut for a prediction and returns the most likely state of the specified column.</span></span> <span data-ttu-id="716ea-171">如需詳細資訊，請參閱 [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx)。</span><span class="sxs-lookup"><span data-stu-id="716ea-171">For more information, see [SELECT &#40;DMX&#41;](/sql/dmx/select-dmx).</span></span>  
  
#### <a name="to-return-the-states-of-a-discrete-column"></a><span data-ttu-id="716ea-172">若要傳回分隔資料行的狀態</span><span class="sxs-lookup"><span data-stu-id="716ea-172">To return the states of a discrete column</span></span>  
  
1.  <span data-ttu-id="716ea-173">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX**]。</span><span class="sxs-lookup"><span data-stu-id="716ea-173">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="716ea-174">此時會開啟 [查詢編輯器] 且包含新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="716ea-174">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="716ea-175">將 SELECT Distinct 陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="716ea-175">Copy the generic example of the SELECT Distinct statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="716ea-176">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="716ea-176">Replace the following:</span></span>  
  
    ```  
    [<column,name>   
    ```  
  
     <span data-ttu-id="716ea-177">成為：</span><span class="sxs-lookup"><span data-stu-id="716ea-177">with:</span></span>  
  
    ```  
    [Bike Buyer]  
    ```  
  
4.  <span data-ttu-id="716ea-178">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="716ea-178">Replace the following:</span></span>  
  
    ```  
    [<mining model>]   
    ```  
  
     <span data-ttu-id="716ea-179">成為：</span><span class="sxs-lookup"><span data-stu-id="716ea-179">with:</span></span>  
  
    ```  
    [Decision Tree]  
    ```  
  
     <span data-ttu-id="716ea-180">現在，完整的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="716ea-180">The complete statement should now be as follows:</span></span>  
  
    ```  
    SELECT DISTINCT [Bike Buyer]   
    FROM [Decision Tree]  
    ```  
  
5.  <span data-ttu-id="716ea-181">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="716ea-181">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
6.  <span data-ttu-id="716ea-182">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `SELECT_DISCRETE.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="716ea-182">In the **Save As** dialog box, browse to the appropriate folder, and name the file `SELECT_DISCRETE.dmx`.</span></span>  
  
7.  <span data-ttu-id="716ea-183">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="716ea-183">On the toolbar, click the **Execute** button.</span></span>  
  
     <span data-ttu-id="716ea-184">該查詢會傳回 Bike Buyer 資料行的可能狀態。</span><span class="sxs-lookup"><span data-stu-id="716ea-184">The query returns the possible states of the Bike Buyer column.</span></span>  
  
 <span data-ttu-id="716ea-185">在下一課，您將使用決策樹採礦模型來預測潛在客戶是否會成為自行車買主。</span><span class="sxs-lookup"><span data-stu-id="716ea-185">In the next lesson, you will predict whether potential customers will be bike buyers by using the decision tree mining model.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="716ea-186">下一課</span><span class="sxs-lookup"><span data-stu-id="716ea-186">Next Lesson</span></span>  
 [<span data-ttu-id="716ea-187">第 5 課：執行預測查詢</span><span class="sxs-lookup"><span data-stu-id="716ea-187">Lesson 5: Executing Prediction Queries</span></span>](../../2014/tutorials/lesson-5-executing-prediction-queries.md)  
  
  
