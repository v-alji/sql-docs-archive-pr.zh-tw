---
title: 第3課：處理購物籃的採礦結構 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 095a043f-cf6f-45bb-a021-ae4e1b535c65
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: ce2c2e6944d524a38edc331d2cd128ca7cf7d419
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686565"
---
# <a name="lesson-3-processing-the-market-basket-mining-structure"></a><span data-ttu-id="dea4a-102">第 3 課：處理購物籃採礦結構</span><span class="sxs-lookup"><span data-stu-id="dea4a-102">Lesson 3: Processing the Market Basket Mining Structure</span></span>
  <span data-ttu-id="dea4a-103">在這一課，您將使用[INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)語句和範例資料庫中的 VAssocSeqLineItems 和 vAssocSeqOrders， [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 來處理您在[第1課：建立購物籃採礦結構](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md)和[第2課：將採礦模型新增至購物籃採礦結構](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)中所建立的採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="dea4a-103">In this lesson, you will use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement and the vAssocSeqLineItems and vAssocSeqOrders from the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample database to process the mining structures and mining models that you created in [Lesson 1: Creating the Market Basket Mining Structure](../../2014/tutorials/lesson-1-creating-the-market-basket-mining-structure.md) and [Lesson 2: Adding Mining Models to the Market Basket Mining Structure](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md).</span></span>  
  
 <span data-ttu-id="dea4a-104">當您處理採礦結構時，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會讀取來源資料並建立支援採礦模型的結構。</span><span class="sxs-lookup"><span data-stu-id="dea4a-104">When you process a mining structure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] reads the source data and builds the structures that support mining models.</span></span> <span data-ttu-id="dea4a-105">當您處理採礦模型時，採礦結構所定義的資料會透過您選擇的資料採礦演算法來傳遞。</span><span class="sxs-lookup"><span data-stu-id="dea4a-105">When you process a mining model, the data defined by the mining structure is passed through the data mining algorithm that you chose.</span></span> <span data-ttu-id="dea4a-106">此演算法會搜尋趨勢和模式，然後將此資訊儲存在採礦模型中。</span><span class="sxs-lookup"><span data-stu-id="dea4a-106">The algorithm searches for trends and patterns, and then stores this information in the mining model.</span></span> <span data-ttu-id="dea4a-107">因此，採礦模型不包含實際來源資料，而包含演算法所發現的資訊。</span><span class="sxs-lookup"><span data-stu-id="dea4a-107">The mining model, therefore, does not contain the actual source data, but instead contains the information that was discovered by the algorithm.</span></span> <span data-ttu-id="dea4a-108">如需處理採礦模型的詳細資訊，請參閱[&#40;資料採礦&#41;的處理需求和考慮](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="dea4a-108">For more information about processing mining models, see [Processing Requirements and Considerations &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).</span></span>  
  
 <span data-ttu-id="dea4a-109">唯有當您變更結構資料行或變更來源資料時，您才需要重新處理採礦結構。</span><span class="sxs-lookup"><span data-stu-id="dea4a-109">You only have to reprocess a mining structure if you change a structure column or change the source data.</span></span> <span data-ttu-id="dea4a-110">如果您將採礦模型加入至已處理的採礦結構中，就可以使用 `INSERT INTO MINING MODEL` 陳述式，在現有的資料上定型新的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="dea4a-110">If you add a mining model to a mining structure that has already been processed, you can use the `INSERT INTO MINING MODEL` statement to train the new mining model on the existing data.</span></span>  
  
 <span data-ttu-id="dea4a-111">因為購物籃採礦結構包含巢狀資料表，所以您必須使用巢狀資料表結構來定義要定型的採礦資料行，並使用 `SHAPE` 命令定義從來源資料表提取定型資料的查詢。</span><span class="sxs-lookup"><span data-stu-id="dea4a-111">Because the Market Basket mining structure contains a nested table, you will have to define the mining columns to be trained using the nested table structure, and use the `SHAPE` command to define the queries that pull the training data from the source tables.</span></span>  
  
## <a name="insert-into-statement"></a><span data-ttu-id="dea4a-112">INSERT INTO 陳述式</span><span class="sxs-lookup"><span data-stu-id="dea4a-112">INSERT INTO Statement</span></span>  
 <span data-ttu-id="dea4a-113">若要訓練購物籃的採礦結構和其相關聯的採礦模型，請使用[INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)語句。</span><span class="sxs-lookup"><span data-stu-id="dea4a-113">In order to train the Market Basket mining structure and its associated mining models, use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement.</span></span> <span data-ttu-id="dea4a-114">陳述式中的程式碼可分成下列各部份。</span><span class="sxs-lookup"><span data-stu-id="dea4a-114">The code in the statement can be broken into the following parts.</span></span>  
  
-   <span data-ttu-id="dea4a-115">識別採礦結構</span><span class="sxs-lookup"><span data-stu-id="dea4a-115">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="dea4a-116">列出採礦結構中的資料行</span><span class="sxs-lookup"><span data-stu-id="dea4a-116">Listing the columns in the mining structure</span></span>  
  
-   <span data-ttu-id="dea4a-117">使用 `SHAPE` 定義定型資料</span><span class="sxs-lookup"><span data-stu-id="dea4a-117">Defining the training data using `SHAPE`</span></span>  
  
 <span data-ttu-id="dea4a-118">下面是 `INSERT INTO` 陳述式的一般範例：</span><span class="sxs-lookup"><span data-stu-id="dea4a-118">The following is a generic example of the `INSERT INTO` statement:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
   [<nested table>]  
   ( SKIP, <skipped column> )  
)  
SHAPE {  
  OPENQUERY([<datasource>],'<SELECT statement>') }  
APPEND  
(   
  {OPENQUERY([<datasource>],'<nested SELECT statement>')  
}  
RELATE [<case key>] TO [<foreign key>]  
) AS [<nested table>]  
```  
  
 <span data-ttu-id="dea4a-119">程式碼的第一行識別您將定型的採礦結構：</span><span class="sxs-lookup"><span data-stu-id="dea4a-119">The first line of the code identifies the mining structure that you will train:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="dea4a-120">接下來幾行的程式碼指定採礦結構定義的資料行。</span><span class="sxs-lookup"><span data-stu-id="dea4a-120">The next lines of the code specify the columns that are defined by the mining structure.</span></span> <span data-ttu-id="dea4a-121">您必須列出採礦結構的每一個資料行，且每一個資料行必須對應到來源查詢資料內包含的資料行。</span><span class="sxs-lookup"><span data-stu-id="dea4a-121">You must list each column in the mining structure, and each column must map to a column contained within the source query data.</span></span> <span data-ttu-id="dea4a-122">您可以使用 `SKIP` 來忽略存在來源資料而不存在採礦結構中的資料行。</span><span class="sxs-lookup"><span data-stu-id="dea4a-122">You can use `SKIP` to ignore columns that exist in the source data but do not exist in the mining structure.</span></span> <span data-ttu-id="dea4a-123">如需如何使用的詳細資訊 `SKIP` ，請參閱[INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)。</span><span class="sxs-lookup"><span data-stu-id="dea4a-123">For more information about how to use `SKIP`, see [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx).</span></span>  
  
```  
(  
   <mining structure columns>  
   [<nested table>]  
   ( SKIP, <skipped column> )  
)  
```  
  
 <span data-ttu-id="dea4a-124">程式碼的最後幾行定義將用於定型採礦結構的資料。</span><span class="sxs-lookup"><span data-stu-id="dea4a-124">The final lines of the code define the data that will be used to train the mining structure.</span></span> <span data-ttu-id="dea4a-125">因為來源資料包含在兩份資料表內，所以您將使用 `SHAPE` 使兩份資料表彼此相關。</span><span class="sxs-lookup"><span data-stu-id="dea4a-125">Because the source data is contained within two tables, you will use `SHAPE` to relate the tables.</span></span>  
  
```  
SHAPE {  
  OPENQUERY([<datasource>],'<SELECT statement>') }  
APPEND  
(   
  {OPENQUERY([<datasource>],''<nested SELECT statement>'')  
}  
RELATE [<case key>] TO [<foreign key>]  
) AS [<nested table>]  
```  
  
 <span data-ttu-id="dea4a-126">在這一課，您使用 `OPENQUERY` 來定義來源資料。</span><span class="sxs-lookup"><span data-stu-id="dea4a-126">In this lesson, you use `OPENQUERY` to define the source data.</span></span> <span data-ttu-id="dea4a-127">如需有關在來源資料上定義查詢之其他方法的詳細資訊，請參閱[&#60;來源資料查詢&#62;](/sql/dmx/source-data-query)。</span><span class="sxs-lookup"><span data-stu-id="dea4a-127">For information about other methods of defining a query on the source data, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="dea4a-128">課程工作</span><span class="sxs-lookup"><span data-stu-id="dea4a-128">Lesson Tasks</span></span>  
 <span data-ttu-id="dea4a-129">您將在這一課執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="dea4a-129">You will perform the following task in this lesson:</span></span>  
  
-   <span data-ttu-id="dea4a-130">處理購物籃採礦結構</span><span class="sxs-lookup"><span data-stu-id="dea4a-130">Process the Market Basket mining structure</span></span>  
  
## <a name="processing-the-market-basket-mining-structure"></a><span data-ttu-id="dea4a-131">處理購物籃採礦結構</span><span class="sxs-lookup"><span data-stu-id="dea4a-131">Processing the Market Basket Mining Structure</span></span>  
  
#### <a name="to-process-the-mining-structure-by-using-insert-into"></a><span data-ttu-id="dea4a-132">若要使用 INSERT INTO 處理採礦結構</span><span class="sxs-lookup"><span data-stu-id="dea4a-132">To process the mining structure by using INSERT INTO</span></span>  
  
1.  <span data-ttu-id="dea4a-133">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX**]。</span><span class="sxs-lookup"><span data-stu-id="dea4a-133">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="dea4a-134">此時會開啟 [查詢編輯器] 且包含新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="dea4a-134">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="dea4a-135">將 INSERT INTO 陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="dea4a-135">Copy the generic example of the INSERT INTO statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="dea4a-136">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="dea4a-136">Replace the following:</span></span>  
  
    ```  
    [<mining structure>]  
    ```  
  
     <span data-ttu-id="dea4a-137">成為：</span><span class="sxs-lookup"><span data-stu-id="dea4a-137">with:</span></span>  
  
    ```  
    Market Basket  
    ```  
  
4.  <span data-ttu-id="dea4a-138">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="dea4a-138">Replace the following:</span></span>  
  
    ```  
    <mining structure columns>  
    [<nested table>]  
    ( SKIP, <skipped column> )  
    ```  
  
     <span data-ttu-id="dea4a-139">成為：</span><span class="sxs-lookup"><span data-stu-id="dea4a-139">with:</span></span>  
  
    ```  
    [OrderNumber],  
    [Products]   
    (SKIP, [Model])  
    ```  
  
     <span data-ttu-id="dea4a-140">陳述式中的 `Products` 會參考 SHAPE 陳述式所定義的 Products 資料表。</span><span class="sxs-lookup"><span data-stu-id="dea4a-140">In the statement, `Products` refers to the Products table defined by the SHAPE statement.</span></span> <span data-ttu-id="dea4a-141">`SKIP` 用來忽略 Model 資料行，此資料行在來源資料中做為索引鍵，但在採礦結構中沒有使用。</span><span class="sxs-lookup"><span data-stu-id="dea4a-141">`SKIP` is used to ignore the Model column, which exists in the source data as a key, but is not used by the mining structure.</span></span>  
  
5.  <span data-ttu-id="dea4a-142">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="dea4a-142">Replace the following:</span></span>  
  
    ```  
    SHAPE {  
      OPENQUERY([<datasource>],'<SELECT statement>') }  
    APPEND  
    (   
      {OPENQUERY([<datasource>],'<nested SELECT statement>')  
    }  
    RELATE [<case key>] TO [<foreign key>]  
    ) AS [<nested table>]  
    ```  
  
     <span data-ttu-id="dea4a-143">成為：</span><span class="sxs-lookup"><span data-stu-id="dea4a-143">with:</span></span>  
  
    ```  
    SHAPE {  
      OPENQUERY([Adventure Works DW],'SELECT OrderNumber  
                FROM vAssocSeqOrders ORDER BY OrderNumber')}  
    APPEND  
    (   
      {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, Model FROM   
        dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')  
    }  
    RELATE OrderNumber to OrderNumber   
    ) AS [Products]  
    ```  
  
     <span data-ttu-id="dea4a-144">來源查詢會參考 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 範例專案中所定義的資料來源 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="dea4a-144">The source query references the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source defined in the [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] sample project.</span></span> <span data-ttu-id="dea4a-145">它使用此資料來源來存取 vAssocSeqLineItems 和 vAssocSeqOrders 檢視。</span><span class="sxs-lookup"><span data-stu-id="dea4a-145">It uses this data source to access the vAssocSeqLineItems and vAssocSeqOrders views.</span></span> <span data-ttu-id="dea4a-146">這些檢視包含將用於定型採礦模型的來源資料。</span><span class="sxs-lookup"><span data-stu-id="dea4a-146">These views contain the source data that will be used to train the mining model.</span></span> <span data-ttu-id="dea4a-147">如果您尚未建立此專案或這些視圖，請參閱[基本資料採礦教學](../../2014/tutorials/basic-data-mining-tutorial.md)課程。</span><span class="sxs-lookup"><span data-stu-id="dea4a-147">If you have not created this project or these views, see [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).</span></span>  
  
     <span data-ttu-id="dea4a-148">在 `SHAPE` 命令內，您將使用 `OPENQUERY` 來定義兩項查詢。</span><span class="sxs-lookup"><span data-stu-id="dea4a-148">Within the `SHAPE` command, you will use `OPENQUERY` to define two queries.</span></span> <span data-ttu-id="dea4a-149">第一項查詢定義父資料表，第二項查詢定義巢狀資料表。</span><span class="sxs-lookup"><span data-stu-id="dea4a-149">The first query defines the parent table, and the second query defines the nested table.</span></span> <span data-ttu-id="dea4a-150">兩份資料表利用同時存在於其中的 OrderNumber 資料行而彼此相關。</span><span class="sxs-lookup"><span data-stu-id="dea4a-150">The two tables are related using the OrderNumber column, which exists in both tables.</span></span>  
  
     <span data-ttu-id="dea4a-151">現在，完整的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="dea4a-151">The complete statement should now be as follows:</span></span>  
  
    ```  
    INSERT INTO MINING STRUCTURE [Market Basket]  
    (  
       [OrderNumber],[Products] (SKIP, [Model])  
    )  
    SHAPE {  
      OPENQUERY([Adventure Works DW],'SELECT OrderNumber  
                FROM vAssocSeqOrders ORDER BY OrderNumber')}  
    APPEND  
    (   
      {OPENQUERY([Adventure Works DW],'SELECT OrderNumber, Model FROM   
        dbo.vAssocSeqLineItems ORDER BY OrderNumber, Model')  
    }  
    RELATE OrderNumber to OrderNumber   
    ) AS [Products]  
    ```  
  
6.  <span data-ttu-id="dea4a-152">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="dea4a-152">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="dea4a-153">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `Process Market Basket.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="dea4a-153">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Process Market Basket.dmx`.</span></span>  
  
8.  <span data-ttu-id="dea4a-154">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="dea4a-154">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="dea4a-155">在查詢執行完成之後，您就可以檢視找到的模式和項目集、檢視關聯，或依據項目集、機率或重要性進行篩選。</span><span class="sxs-lookup"><span data-stu-id="dea4a-155">After the query has finished running, you can view the patterns and itemsets that were found, view associations, or filter by itemset, probability, or importance.</span></span> <span data-ttu-id="dea4a-156">若要查看這項資訊，請在中 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] ，以滑鼠右鍵按一下資料模型的名稱，然後按一下 **[流覽]**。</span><span class="sxs-lookup"><span data-stu-id="dea4a-156">To view this information, in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right-click the name of the data model, and then click **Browse**.</span></span>  
  
 <span data-ttu-id="dea4a-157">在下一課，您將依據您加入購物籃結構中的採礦模型來建立幾個預測。</span><span class="sxs-lookup"><span data-stu-id="dea4a-157">In the next lesson, you will create several predictions based on the mining models that you added to the Market Basket structure.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="dea4a-158">下一課</span><span class="sxs-lookup"><span data-stu-id="dea4a-158">Next Lesson</span></span>  
 [<span data-ttu-id="dea4a-159">第 4 課：執行購物籃預測</span><span class="sxs-lookup"><span data-stu-id="dea4a-159">Lesson 4: Executing Market Basket Predictions</span></span>](../../2014/tutorials/lesson-4-executing-market-basket-predictions.md)  
  
  
