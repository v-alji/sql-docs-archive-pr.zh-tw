---
title: 第1課：建立自行車購買者採礦結構 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a73ac60b-660f-458a-bd2f-993fbeba7226
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: d6384910858d87a80aa3c8f897bc88e45f4504fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703538"
---
# <a name="lesson-1-creating-the-bike-buyer-mining-structure"></a><span data-ttu-id="89fae-102">第 1 課：建立自行車買主採礦結構</span><span class="sxs-lookup"><span data-stu-id="89fae-102">Lesson 1: Creating the Bike Buyer Mining Structure</span></span>
  <span data-ttu-id="89fae-103">在這一課，您將建立一個可讓您預測 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 的潛在客戶是否將購買自行車的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="89fae-103">In this lesson, you will create a mining structure that allows you to predict whether a potential customer of [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] will purchase a bicycle.</span></span> <span data-ttu-id="89fae-104">如果您不熟悉在資料採礦中使用的是採礦結構和其角色，請參閱[&#40;Analysis Services 資料採礦&#41;的採礦結構](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="89fae-104">If you are unfamiliar with mining structures and their role in data mining, see [Mining Structures &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-structures-analysis-services-data-mining.md).</span></span>  
  
 <span data-ttu-id="89fae-105">您將在本課程中建立的自行車購買者採礦結構，支援根據[Microsoft 群集演算法](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)[Microsoft 決策樹演算法](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md)來新增採礦模型。</span><span class="sxs-lookup"><span data-stu-id="89fae-105">The Bike Buyer mining structure that you will create in this lesson supports adding mining models based on the [Microsoft Clustering Algorithm](../../2014/analysis-services/data-mining/microsoft-clustering-algorithm.md)[Microsoft Decision Trees Algorithm](../../2014/analysis-services/data-mining/microsoft-decision-trees-algorithm.md).</span></span> <span data-ttu-id="89fae-106">在後面的課程中，您將使用群集採礦模型來探索可分組客戶的不同方式，並將使用決策樹採礦模型來預測潛在客戶是否會購買自行車。</span><span class="sxs-lookup"><span data-stu-id="89fae-106">In later lessons, you will use the clustering mining models to explore the different ways in which customers can be grouped, and will use decision tree mining models to predict whether or not a potential customer will purchase a bicycle.</span></span>  
  
## <a name="create-mining-structure-statement"></a><span data-ttu-id="89fae-107">CREATE MINING STRUCTURE 陳述式</span><span class="sxs-lookup"><span data-stu-id="89fae-107">CREATE MINING STRUCTURE Statement</span></span>  
 <span data-ttu-id="89fae-108">若要建立「採礦結構」，您可以使用「[建立」採礦結構 &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx)語句。</span><span class="sxs-lookup"><span data-stu-id="89fae-108">To create a mining structure, you use the [CREATE MINING STRUCTURE &#40;DMX&#41;](/sql/dmx/create-mining-structure-dmx) statement.</span></span> <span data-ttu-id="89fae-109">陳述式中的程式碼可分成下列各部份：</span><span class="sxs-lookup"><span data-stu-id="89fae-109">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="89fae-110">命名結構。</span><span class="sxs-lookup"><span data-stu-id="89fae-110">Naming the structure.</span></span>  
  
-   <span data-ttu-id="89fae-111">定義索引鍵資料行。</span><span class="sxs-lookup"><span data-stu-id="89fae-111">Defining the key column.</span></span>  
  
-   <span data-ttu-id="89fae-112">定義採礦資料行。</span><span class="sxs-lookup"><span data-stu-id="89fae-112">Defining the mining columns.</span></span>  
  
-   <span data-ttu-id="89fae-113">定義選擇性的測試資料集。</span><span class="sxs-lookup"><span data-stu-id="89fae-113">Defining an optional testing data set.</span></span>  
  
 <span data-ttu-id="89fae-114">以下是 CREATE MINING STRUCTURE 陳述式的一般範例：</span><span class="sxs-lookup"><span data-stu-id="89fae-114">The following is a generic example of the CREATE MINING STRUCTURE statement:</span></span>  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
(  
    <key column>,  
    <mining structure columns>  
)   
WITH HOLDOUT (<holdout specifier>)  
```  
  
 <span data-ttu-id="89fae-115">程式碼的第一行定義結構的名稱：</span><span class="sxs-lookup"><span data-stu-id="89fae-115">The first line of the code defines the name of the structure:</span></span>  
  
```  
CREATE MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="89fae-116">如需 (DMX) 為資料採礦延伸模組中的物件命名的詳細資訊，請參閱[&#40;dmx&#41;的識別碼](/sql/dmx/identifiers-dmx)。</span><span class="sxs-lookup"><span data-stu-id="89fae-116">For information about naming an object in Data Mining Extensions (DMX), see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="89fae-117">程式碼的下一行定義採礦結構的索引鍵資料行，可唯一識別來源資料中的實體：</span><span class="sxs-lookup"><span data-stu-id="89fae-117">The next line of the code defines the key column for the mining structure, which uniquely identifies an entity in the source data:</span></span>  
  
```  
<key column>,  
```  
  
 <span data-ttu-id="89fae-118">在您要建立的採礦結構中，客戶識別碼 `CustomerKey` 定義來源資料中的實體。</span><span class="sxs-lookup"><span data-stu-id="89fae-118">In the mining structure you will create, the customer identifier, `CustomerKey`, defines an entity in the source data.</span></span>  
  
 <span data-ttu-id="89fae-119">程式碼的下一行用來定義採礦資料行，與採礦結構相關聯的採礦模型將使用這些資料行：</span><span class="sxs-lookup"><span data-stu-id="89fae-119">The next line of the code is used to define the mining columns that will be used by the mining models associated with the mining structure:</span></span>  
  
```  
<mining structure columns>  
```  
  
 <span data-ttu-id="89fae-120">您可以使用中的離散化函式 \<mining structure columns> 來離散化連續資料行，方法是使用下列語法：</span><span class="sxs-lookup"><span data-stu-id="89fae-120">You can use the DISCRETIZE function within \<mining structure columns> to discretize continuous columns by using the following syntax:</span></span>  
  
 `DISCRETIZE(<method>,<number of buckets>)`  
  
 <span data-ttu-id="89fae-121">如需有關分隔資料行的詳細資訊，請參閱[離散化方法 &#40;資料採礦&#41;](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="89fae-121">For more information about discretizing columns, see [Discretization Methods &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/discretization-methods-data-mining.md).</span></span> <span data-ttu-id="89fae-122">如需您可以定義之「採礦結構」資料行類型的詳細資訊，請參閱「[採礦結構資料行](../../2014/analysis-services/data-mining/mining-structure-columns.md)」。</span><span class="sxs-lookup"><span data-stu-id="89fae-122">For more information about the types of mining structure columns that you can define, see [Mining Structure Columns](../../2014/analysis-services/data-mining/mining-structure-columns.md).</span></span>  
  
 <span data-ttu-id="89fae-123">程式碼的最後一行定義採礦結構中的選擇性資料分割：</span><span class="sxs-lookup"><span data-stu-id="89fae-123">The final line of the code defines an optional partition in the mining structure:</span></span>  
  
```  
WITH HOLDOUT (<holdout specifier>)  
```  
  
 <span data-ttu-id="89fae-124">您將資料的某些部分指定為用來測試與結構相關的採購模型，而將剩餘的資料指定為用來定型模型。</span><span class="sxs-lookup"><span data-stu-id="89fae-124">You specify some portion of the data to use for testing mining models that are related to the structure, and the remaining data is used for training the models.</span></span> <span data-ttu-id="89fae-125">根據預設，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 所建立的測試資料集會包含所有案例資料的 30%。</span><span class="sxs-lookup"><span data-stu-id="89fae-125">By default, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] creates a test data set that contains 30 percent of all case data.</span></span> <span data-ttu-id="89fae-126">您要加入規格，規定測試資料集應該包含 30% 的案例，最多可達 1000 個案例。</span><span class="sxs-lookup"><span data-stu-id="89fae-126">You will add the specification that the test data set should contain 30 percent of the cases up to a maximum of 1000 cases.</span></span> <span data-ttu-id="89fae-127">如果 30% 的案例數少於 1000，則測試資料集將包含較小的數量。</span><span class="sxs-lookup"><span data-stu-id="89fae-127">If 30 percent of the cases is less than 1000, the test data set will contain the smaller amount.</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="89fae-128">課程工作</span><span class="sxs-lookup"><span data-stu-id="89fae-128">Lesson Tasks</span></span>  
 <span data-ttu-id="89fae-129">您將在這一課執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="89fae-129">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="89fae-130">建立新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="89fae-130">Create a new blank query.</span></span>  
  
-   <span data-ttu-id="89fae-131">改變查詢來建立採礦結構。</span><span class="sxs-lookup"><span data-stu-id="89fae-131">Alter the query to create the mining structure.</span></span>  
  
-   <span data-ttu-id="89fae-132">執行查詢。</span><span class="sxs-lookup"><span data-stu-id="89fae-132">Execute the query.</span></span>  
  
## <a name="creating-the-query"></a><span data-ttu-id="89fae-133">建立查詢</span><span class="sxs-lookup"><span data-stu-id="89fae-133">Creating the Query</span></span>  
 <span data-ttu-id="89fae-134">第一步是連接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的執行個體，並在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中建立新的 DMX 查詢。</span><span class="sxs-lookup"><span data-stu-id="89fae-134">The first step is to connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and create a new DMX query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a><span data-ttu-id="89fae-135">若要在 SQL Server Management Studio 中建立新的 DMX 查詢</span><span class="sxs-lookup"><span data-stu-id="89fae-135">To create a new DMX query in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="89fae-136">開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="89fae-136">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="89fae-137">在 [**連接到伺服器**] 對話方塊的 [**伺服器類型**] 中，選取 [ **Analysis Services**]。</span><span class="sxs-lookup"><span data-stu-id="89fae-137">In the **Connect to Server** dialog box, for **Server type**, select **Analysis Services**.</span></span> <span data-ttu-id="89fae-138">在 [**伺服器名稱**] 中，輸入 `LocalHost` ，或輸入 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 您想要在此課程中連接的實例名稱。</span><span class="sxs-lookup"><span data-stu-id="89fae-138">In **Server name**, type `LocalHost`, or type the name of the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you want to connect to for this lesson.</span></span> <span data-ttu-id="89fae-139">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="89fae-139">Click **Connect**.</span></span>  
  
3.  <span data-ttu-id="89fae-140">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX** ] 以開啟 [**查詢編輯器**] 和新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="89fae-140">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX** to open the **Query Editor** and a new, blank query.</span></span>  
  
## <a name="altering-the-query"></a><span data-ttu-id="89fae-141">改變查詢</span><span class="sxs-lookup"><span data-stu-id="89fae-141">Altering the Query</span></span>  
 <span data-ttu-id="89fae-142">下一步是修改上述 CREATE MINING STRUCTURE 陳述式來建立自行車買主採礦結構。</span><span class="sxs-lookup"><span data-stu-id="89fae-142">The next step is to modify the CREATE MINING STRUCTURE statement described above to create the Bike Buyer mining structure.</span></span>  
  
#### <a name="to-customize-the-create-mining-structure-statement"></a><span data-ttu-id="89fae-143">若要自訂 CREATE MINING STRUCTURE 陳述式</span><span class="sxs-lookup"><span data-stu-id="89fae-143">To customize the CREATE MINING STRUCTURE statement</span></span>  
  
1.  <span data-ttu-id="89fae-144">在查詢編輯器中，將 CREATE MINING STRUCTURE 陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="89fae-144">In the Query Editor, copy the generic example of the CREATE MINING STRUCTURE statement into the blank query.</span></span>  
  
2.  <span data-ttu-id="89fae-145">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="89fae-145">Replace the following:</span></span>  
  
    ```  
    [<mining structure>]   
    ```  
  
     <span data-ttu-id="89fae-146">成為：</span><span class="sxs-lookup"><span data-stu-id="89fae-146">with:</span></span>  
  
    ```  
    [Bike Buyer]  
    ```  
  
3.  <span data-ttu-id="89fae-147">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="89fae-147">Replace the following:</span></span>  
  
    ```  
    <key column>   
    ```  
  
     <span data-ttu-id="89fae-148">成為：</span><span class="sxs-lookup"><span data-stu-id="89fae-148">with:</span></span>  
  
    ```  
    CustomerKey LONG KEY  
    ```  
  
4.  <span data-ttu-id="89fae-149">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="89fae-149">Replace the following:</span></span>  
  
    ```  
    <mining structure columns>   
    ```  
  
     <span data-ttu-id="89fae-150">成為：</span><span class="sxs-lookup"><span data-stu-id="89fae-150">with:</span></span>  
  
    ```  
    [Age] LONG DISCRETIZED(Automatic,10),  
    [Bike Buyer] LONG DISCRETE,  
    [Commute Distance] TEXT DISCRETE,  
    [Education] TEXT DISCRETE,  
    [Gender] TEXT DISCRETE,  
    [House Owner Flag] TEXT DISCRETE,  
    [Marital Status] TEXT DISCRETE,  
    [Number Cars Owned] LONG DISCRETE,  
    [Number Children At Home] LONG DISCRETE,  
    [Occupation] TEXT DISCRETE,  
    [Region] TEXT DISCRETE,  
    [Total Children]LONG DISCRETE,  
    [Yearly Income] DOUBLE CONTINUOUS  
    ```  
  
5.  <span data-ttu-id="89fae-151">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="89fae-151">Replace the following:</span></span>  
  
    ```  
    WITH HOLDOUT (holdout specifier>)  
    ```  
  
     <span data-ttu-id="89fae-152">成為：</span><span class="sxs-lookup"><span data-stu-id="89fae-152">with:</span></span>  
  
    ```  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
    ```  
  
     <span data-ttu-id="89fae-153">現在，完整的採礦結構陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="89fae-153">The complete mining structure statement should now be as follows:</span></span>  
  
    ```  
    CREATE MINING STRUCTURE [Bike Buyer]  
    (  
       [Customer Key] LONG KEY,  
       [Age]LONG DISCRETIZED(Automatic,10),  
       [Bike Buyer] LONG DISCRETE,  
       [Commute Distance] TEXT DISCRETE,  
       [Education] TEXT DISCRETE,  
       [Gender] TEXT DISCRETE,  
       [House Owner Flag] TEXT DISCRETE,  
       [Marital Status] TEXT DISCRETE,  
       [Number Cars Owned]LONG DISCRETE,  
       [Number Children At Home]LONG DISCRETE,  
       [Occupation] TEXT DISCRETE,  
       [Region] TEXT DISCRETE,  
       [Total Children]LONG DISCRETE,  
       [Yearly Income] DOUBLE CONTINUOUS  
    )  
    WITH HOLDOUT (30 PERCENT or 1000 CASES)  
  
    ```  
  
6.  <span data-ttu-id="89fae-154">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="89fae-154">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="89fae-155">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `Bike Buyer Structure.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="89fae-155">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Bike Buyer Structure.dmx`.</span></span>  
  
## <a name="executing-the-query"></a><span data-ttu-id="89fae-156">執行查詢</span><span class="sxs-lookup"><span data-stu-id="89fae-156">Executing the Query</span></span>  
 <span data-ttu-id="89fae-157">最後的步驟是執行查詢。</span><span class="sxs-lookup"><span data-stu-id="89fae-157">The final step is to execute the query.</span></span> <span data-ttu-id="89fae-158">在建立及儲存查詢以後，將需要執行查詢。</span><span class="sxs-lookup"><span data-stu-id="89fae-158">After a query is created and saved, it needs to be executed.</span></span> <span data-ttu-id="89fae-159">也就是說，必須執行此陳述式，才能夠在伺服器上建立採礦結構。</span><span class="sxs-lookup"><span data-stu-id="89fae-159">That is, the statement needs to be run in order to create the mining structure on the server.</span></span> <span data-ttu-id="89fae-160">如需在 [查詢編輯器] 中執行查詢的詳細資訊，請參閱[資料庫引擎查詢編輯器 &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="89fae-160">For more information about executing queries in Query Editor, see [Database Engine Query Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="89fae-161">若要執行查詢</span><span class="sxs-lookup"><span data-stu-id="89fae-161">To execute the query</span></span>  
  
1.  <span data-ttu-id="89fae-162">在 [查詢編輯器] 的工具列上，按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="89fae-162">In Query Editor, on the toolbar, click **Execute**.</span></span>  
  
     <span data-ttu-id="89fae-163">查詢的狀態會在語句完成執行之後，顯示在 [查詢編輯器] 底部的 [**訊息**] 索引標籤中。</span><span class="sxs-lookup"><span data-stu-id="89fae-163">The status of the query is displayed in the **Messages** tab at the bottom of Query Editor after the statement finishes executing.</span></span> <span data-ttu-id="89fae-164">訊息應該顯示如下：</span><span class="sxs-lookup"><span data-stu-id="89fae-164">Messages should display:</span></span>  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     <span data-ttu-id="89fae-165">伺服器上現在有一個名為**自行車買方**的新結構。</span><span class="sxs-lookup"><span data-stu-id="89fae-165">A new structure named **Bike Buyer** now exists on the server.</span></span>  
  
 <span data-ttu-id="89fae-166">在下一課，您會將採礦模型加入剛才建立的結構中。</span><span class="sxs-lookup"><span data-stu-id="89fae-166">In the next lesson, you will add mining models to the structure you just created.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="89fae-167">下一課</span><span class="sxs-lookup"><span data-stu-id="89fae-167">Next Lesson</span></span>  
 [<span data-ttu-id="89fae-168">第 2 課：將採礦模型新增至自行車買主採礦結構</span><span class="sxs-lookup"><span data-stu-id="89fae-168">Lesson 2: Adding Mining Models to the Bike Buyer Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-bike-buyer-mining-structure.md)  
  
  
