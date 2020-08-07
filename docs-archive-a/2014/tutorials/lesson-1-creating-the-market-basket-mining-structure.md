---
title: 第1課：建立購物籃的採礦結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a817c8d1-aff4-42b4-b194-ad9cc1c60f35
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: a6a6e123e525512a72d70bcc8ca2eba549d1347e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703541"
---
# <a name="lesson-1-creating-the-market-basket-mining-structure"></a><span data-ttu-id="9ea32-102">第 1 課：建立購物籃採礦結構</span><span class="sxs-lookup"><span data-stu-id="9ea32-102">Lesson 1: Creating the Market Basket Mining Structure</span></span>
  <span data-ttu-id="9ea32-103">在這一課，您將建立一個可讓您預測客戶可能同時購買哪些 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 產品的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="9ea32-103">In this lesson, you will create a mining structure that allows you to predict what [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] products a customer tends to purchase at the same time.</span></span> <span data-ttu-id="9ea32-104">如果您不熟悉在資料採礦中使用的是採礦結構和其角色，請參閱[&#40;Analysis Services 資料採礦&#41;的採礦結構](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="9ea32-104">If you are unfamiliar with mining structures and their role in data mining, see [Mining Structures &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="9ea32-105">您在本課程中建立的關聯性採礦結構，支援加入以[Microsoft 關聯分析演算法](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md)為基礎的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="9ea32-105">The association mining structure that you will create in this lesson supports adding mining models based on the [Microsoft Association Algorithm](../../2014/analysis-services/data-mining/microsoft-association-algorithm.md).</span></span> <span data-ttu-id="9ea32-106">在後面的課程中，您將使用採礦模型來預測客戶可能同時購買的產品類型，這稱為購物籃分析。</span><span class="sxs-lookup"><span data-stu-id="9ea32-106">In later lessons, you will use the mining models to predict the type of products a customer tends to purchase at the same time, which is called a market basket analysis.</span></span> <span data-ttu-id="9ea32-107">例如，您會發現客戶可能同時購買越野車、輪胎和頭盔。</span><span class="sxs-lookup"><span data-stu-id="9ea32-107">For example, you may find that customers tend to buy mountain bikes, bike tires, and helmets at the same time.</span></span>  
  
 <span data-ttu-id="9ea32-108">在這一課，採礦結構是使用巢狀資料表來定義。</span><span class="sxs-lookup"><span data-stu-id="9ea32-108">In this lesson, the mining structure is defined by using nested tables.</span></span> <span data-ttu-id="9ea32-109">使用巢狀資料表是因為結構所要定義的資料網域是包含在兩個不同的來源資料表中。</span><span class="sxs-lookup"><span data-stu-id="9ea32-109">Nested tables are used because the data domain that will be defined by the structure is contained within two different source tables.</span></span> <span data-ttu-id="9ea32-110">如需有關嵌套資料表的詳細資訊，請參閱[Analysis Services 資料採礦&#41;的嵌套資料表 &#40;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="9ea32-110">For more information on nested tables, see [Nested Tables &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/nested-tables-analysis-services-data-mining.md).</span></span>  
  
## <a name="create-mining-structure-statement"></a><span data-ttu-id="9ea32-111">CREATE MINING STRUCTURE 陳述式</span><span class="sxs-lookup"><span data-stu-id="9ea32-111">CREATE MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="9ea32-112">若要建立包含嵌套資料表的「採礦結構」，您可以使用「[建立」採礦結構 &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx)語句。</span><span class="sxs-lookup"><span data-stu-id="9ea32-112">In order to create a mining structure containing a nested table, you use the [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) statement.</span></span> <span data-ttu-id="9ea32-113">陳述式中的程式碼可分成下列各部份：</span><span class="sxs-lookup"><span data-stu-id="9ea32-113">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="9ea32-114">命名結構</span><span class="sxs-lookup"><span data-stu-id="9ea32-114">Naming the structure</span></span>  
  
-   <span data-ttu-id="9ea32-115">定義索引鍵資料行</span><span class="sxs-lookup"><span data-stu-id="9ea32-115">Defining the key column</span></span>  
  
-   <span data-ttu-id="9ea32-116">定義採礦資料行</span><span class="sxs-lookup"><span data-stu-id="9ea32-116">Defining the mining columns</span></span>  
  
-   <span data-ttu-id="9ea32-117">定義巢狀資料表資料行</span><span class="sxs-lookup"><span data-stu-id="9ea32-117">Defining the nested table columns</span></span>  
  
 <span data-ttu-id="9ea32-118">以下是 CREATE MINING STRUCTURE 陳述式的一般範例：</span><span class="sxs-lookup"><span data-stu-id="9ea32-118">The following is a generic example of the CREATE MINING STRUCTURE statement:</span></span>  
  
```  
CREATE MINING STRUCTURE [<Mining Structure Name>]  
(  
   <key column>,  
   <mining structure columns>,  
   <table columns>  
   (  <nested key column>,  
      <nested mining structure columns> )  
)  
  
```  
  
 <span data-ttu-id="9ea32-119">程式碼的第一行定義結構的名稱：</span><span class="sxs-lookup"><span data-stu-id="9ea32-119">The first line of the code defines the name of the structure:</span></span>  
  
```  
CREATE MINING STRUCTURE [Mining Structure Name]  
```  
  
 <span data-ttu-id="9ea32-120">如需在 DMX 中命名物件的詳細資訊，請參閱[dmx&#41;&#40;的識別碼](/sql/dmx/identifiers-dmx)。</span><span class="sxs-lookup"><span data-stu-id="9ea32-120">For information about naming an object in DMX, see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="9ea32-121">程式碼的下一行定義採礦結構的索引鍵資料行，可唯一識別來源資料中的實體：</span><span class="sxs-lookup"><span data-stu-id="9ea32-121">The next line of the code defines the key column for the mining structure, which uniquely identifies an entity in the source data:</span></span>  
  
```  
<key column>  
```  
  
 <span data-ttu-id="9ea32-122">程式碼的下一行用來定義採礦資料行，與採礦結構相關聯的採礦模型將使用這些資料行：</span><span class="sxs-lookup"><span data-stu-id="9ea32-122">The next line of the code is used to define the mining columns that will be used by the mining models associated with the mining structure:</span></span>  
  
```  
<mining structure columns>  
```  
  
 <span data-ttu-id="9ea32-123">接下來的幾行程式碼會定義巢狀資料表資料行：</span><span class="sxs-lookup"><span data-stu-id="9ea32-123">The next lines of the code define the nested table columns:</span></span>  
  
```  
<table columns>  
(  <nested key column>,  
   <nested mining structure columns> )  
```  
  
 <span data-ttu-id="9ea32-124">如需您可以定義的「採礦結構」資料行類型的詳細資訊，請參閱「[採礦結構資料行](../../2014/analysis-services/data-mining/mining-structure-columns.md)」。</span><span class="sxs-lookup"><span data-stu-id="9ea32-124">For information about the types of mining structure columns that you can define, see [Mining Structure Columns](../../2014/analysis-services/data-mining/mining-structure-columns.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9ea32-125">根據預設，[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 會針對每個採礦結構建立百分之 30 的鑑效組資料集；但是，當您使用 DMX 來建立採礦結構時，您必須在需要時手動加入鑑效組資料集。</span><span class="sxs-lookup"><span data-stu-id="9ea32-125">By default, [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] creates a 30 percent holdout data set for each mining structure; however, when you use DMX to create a mining structure, you must manually add the holdout data set, if desired.</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="9ea32-126">課程工作</span><span class="sxs-lookup"><span data-stu-id="9ea32-126">Lesson Tasks</span></span>  
 <span data-ttu-id="9ea32-127">您將在這一課執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="9ea32-127">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="9ea32-128">建立新的空白查詢</span><span class="sxs-lookup"><span data-stu-id="9ea32-128">Create a new blank query</span></span>  
  
-   <span data-ttu-id="9ea32-129">改變查詢來建立採礦結構</span><span class="sxs-lookup"><span data-stu-id="9ea32-129">Alter the query to create the mining structure</span></span>  
  
-   <span data-ttu-id="9ea32-130">執行查詢</span><span class="sxs-lookup"><span data-stu-id="9ea32-130">Execute the query</span></span>  
  
## <a name="creating-the-query"></a><span data-ttu-id="9ea32-131">建立查詢</span><span class="sxs-lookup"><span data-stu-id="9ea32-131">Creating the Query</span></span>  
 <span data-ttu-id="9ea32-132">第一步是連接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的執行個體，並在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中建立新的 DMX 查詢。</span><span class="sxs-lookup"><span data-stu-id="9ea32-132">The first step is to connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and create a new DMX query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a><span data-ttu-id="9ea32-133">若要在 SQL Server Management Studio 中建立新的 DMX 查詢</span><span class="sxs-lookup"><span data-stu-id="9ea32-133">To create a new DMX query in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="9ea32-134">開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="9ea32-134">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="9ea32-135">在 [**連接到伺服器**] 對話方塊的 [**伺服器類型**] 中，選取 [ **Analysis Services**]。</span><span class="sxs-lookup"><span data-stu-id="9ea32-135">In the **Connect to Server** dialog box, for **Server type**, select **Analysis Services**.</span></span> <span data-ttu-id="9ea32-136">在 [**伺服器名稱**] 中，輸入 `LocalHost` ，或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 您想要在本課程中連接之實例的名稱。</span><span class="sxs-lookup"><span data-stu-id="9ea32-136">In **Server name**, type `LocalHost`, or the name of the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you want to connect to for this lesson.</span></span> <span data-ttu-id="9ea32-137">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="9ea32-137">Click **Connect**.</span></span>  
  
3.  <span data-ttu-id="9ea32-138">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX**]。</span><span class="sxs-lookup"><span data-stu-id="9ea32-138">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="9ea32-139">此時會開啟 [查詢編輯器] 且包含新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="9ea32-139">Query Editor opens and contains a new, blank query.</span></span>  
  
## <a name="altering-the-query"></a><span data-ttu-id="9ea32-140">改變查詢</span><span class="sxs-lookup"><span data-stu-id="9ea32-140">Altering the Query</span></span>  
 <span data-ttu-id="9ea32-141">下一步是修改上述 CREATE MINING STRUCTURE 陳述式來建立購物籃採礦結構。</span><span class="sxs-lookup"><span data-stu-id="9ea32-141">The next step is to modify the CREATE MINING STRUCTURE statement described above to create the Market Basket mining structure.</span></span>  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a><span data-ttu-id="9ea32-142">若要自訂 CREATE MINING STRUCTURE 陳述式</span><span class="sxs-lookup"><span data-stu-id="9ea32-142">To customize the CREATE MINING STRUCTURE statement</span></span>  
  
1.  <span data-ttu-id="9ea32-143">在查詢編輯器中，將 CREATE MINING STRUCTURE 陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="9ea32-143">In Query Editor, copy the generic example of the CREATE MINING STRUCTURE statement into the blank query.</span></span>  
  
2.  <span data-ttu-id="9ea32-144">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="9ea32-144">Replace the following:</span></span>  
  
    ```  
    [mining structure name]   
    ```  
  
     <span data-ttu-id="9ea32-145">成為：</span><span class="sxs-lookup"><span data-stu-id="9ea32-145">with:</span></span>  
  
    ```  
    [Market Basket]  
    ```  
  
3.  <span data-ttu-id="9ea32-146">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="9ea32-146">Replace the following:</span></span>  
  
    ```  
    <key column>  
    ```  
  
     <span data-ttu-id="9ea32-147">成為：</span><span class="sxs-lookup"><span data-stu-id="9ea32-147">with:</span></span>  
  
    ```  
    OrderNumber TEXT KEY  
    ```  
  
4.  <span data-ttu-id="9ea32-148">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="9ea32-148">Replace the following:</span></span>  
  
    ```  
    <table columns>  
    (  <nested key column>,  
       <nested mining structure columns> )  
    ```  
  
     <span data-ttu-id="9ea32-149">成為：</span><span class="sxs-lookup"><span data-stu-id="9ea32-149">with:</span></span>  
  
    ```  
    [Products] TABLE (  
        [Model] TEXT KEY  
    )  
    ```  
  
     <span data-ttu-id="9ea32-150">TEXT KEY 語言指定 [模型] 資料行是巢狀資料表的索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="9ea32-150">The TEXT KEY language specifies that the Model column is the key column for the nested table.</span></span>  
  
     <span data-ttu-id="9ea32-151">現在，完整的採礦結構陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="9ea32-151">The complete mining structure statement should now be as follows:</span></span>  
  
    ```  
    CREATE MINING STRUCTURE [Market Basket] (  
        OrderNumber TEXT KEY,  
        [Products] TABLE (  
            [Model] TEXT KEY  
        )  
    )  
    ```  
  
5.  <span data-ttu-id="9ea32-152">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="9ea32-152">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
6.  <span data-ttu-id="9ea32-153">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `Market Basket Structure.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="9ea32-153">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Market Basket Structure.dmx`.</span></span>  
  
## <a name="executing-the-query"></a><span data-ttu-id="9ea32-154">執行查詢</span><span class="sxs-lookup"><span data-stu-id="9ea32-154">Executing the Query</span></span>  
 <span data-ttu-id="9ea32-155">最後的步驟是執行查詢。</span><span class="sxs-lookup"><span data-stu-id="9ea32-155">The final step is to execute the query.</span></span> <span data-ttu-id="9ea32-156">在建立及儲存查詢之後，需要執行它 (也就是需要執行陳述式) 才能在伺服器上建立採礦結構。</span><span class="sxs-lookup"><span data-stu-id="9ea32-156">After a query is created and saved, it needs to be executed (that is, the statement needs to be run) in order to create the mining structure on the server.</span></span> <span data-ttu-id="9ea32-157">如需在 [查詢編輯器] 中執行查詢的詳細資訊，請參閱[資料庫引擎查詢編輯器 &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="9ea32-157">For more information about executing queries in Query Editor, see [Database Engine Query Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="9ea32-158">若要執行查詢</span><span class="sxs-lookup"><span data-stu-id="9ea32-158">To execute the query</span></span>  
  
-   <span data-ttu-id="9ea32-159">在 [查詢編輯器] 的工具列上，按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="9ea32-159">In Query Editor, on the toolbar, click **Execute**.</span></span>  
  
     <span data-ttu-id="9ea32-160">查詢的狀態會在語句完成執行之後，顯示在 [查詢編輯器] 底部的 [**訊息**] 索引標籤中。</span><span class="sxs-lookup"><span data-stu-id="9ea32-160">The status of the query is displayed in the **Messages** tab at the bottom of Query Editor after the statement finishes executing.</span></span> <span data-ttu-id="9ea32-161">訊息應該顯示如下：</span><span class="sxs-lookup"><span data-stu-id="9ea32-161">Messages should display:</span></span>  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     <span data-ttu-id="9ea32-162">伺服器上現在有一個名為「**購物籃**」的新結構。</span><span class="sxs-lookup"><span data-stu-id="9ea32-162">A new structure named **Market Basket** now exists on the server.</span></span>  
  
 <span data-ttu-id="9ea32-163">在下一課，您會將採礦模型加入剛才建立的購物籃採礦結構中。</span><span class="sxs-lookup"><span data-stu-id="9ea32-163">In the next lesson, you will add mining models to the Market Basket mining structure you just created.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="9ea32-164">下一課</span><span class="sxs-lookup"><span data-stu-id="9ea32-164">Next Lesson</span></span>  
 [<span data-ttu-id="9ea32-165">第 2 課：將採礦模型新增至購物籃採礦結構</span><span class="sxs-lookup"><span data-stu-id="9ea32-165">Lesson 2: Adding Mining Models to the Market Basket Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-market-basket-mining-structure.md)  
  
  
