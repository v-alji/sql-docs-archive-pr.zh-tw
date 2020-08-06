---
title: 第1課：建立時間序列的採礦模型和採礦結構 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b201f2b8-9ab5-425b-9ff3-fe321a60a7b7
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2513bc3837dd224f6561eb0015ced538ea3add8c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592397"
---
# <a name="lesson-1-creating-a-time-series-mining-model-and-mining-structure"></a><span data-ttu-id="cda22-102">第 1 課：建立時間序列採礦模型和採礦結構</span><span class="sxs-lookup"><span data-stu-id="cda22-102">Lesson 1: Creating a Time Series Mining Model and Mining Structure</span></span>
  <span data-ttu-id="cda22-103">在這一課，您將建立一個採礦模型，好讓您根據歷程記錄資料預測一段時間的值。</span><span class="sxs-lookup"><span data-stu-id="cda22-103">In this lesson, you will create a mining model that allows you to predict values over time, based on historical data.</span></span> <span data-ttu-id="cda22-104">當您建立此模型時，基礎結構將會自動產生而且可用來當做其他採礦模型的基礎。</span><span class="sxs-lookup"><span data-stu-id="cda22-104">When you create the model, the underlying structure will be generated automatically and can be used as the basis for additional mining models.</span></span>  
  
 <span data-ttu-id="cda22-105">本課假設您已經熟悉預測模型及 Microsoft 時間序列演算法的需求。</span><span class="sxs-lookup"><span data-stu-id="cda22-105">This lesson assumes that you are familiar with forecasting models and with the requirements of the Microsoft Time Series algorithm.</span></span> <span data-ttu-id="cda22-106">如需詳細資訊，請參閱 [Microsoft 時間序列演算法](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md)。</span><span class="sxs-lookup"><span data-stu-id="cda22-106">For more information, see [Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md).</span></span>  
  
## <a name="create-mining-model-statement"></a><span data-ttu-id="cda22-107">CREATE MINING MODEL 陳述式</span><span class="sxs-lookup"><span data-stu-id="cda22-107">CREATE MINING MODEL Statement</span></span>  
 <span data-ttu-id="cda22-108">若要直接建立採礦模型並自動產生基礎的採礦結構，您可以使用[&#40;DMX&#41;語句建立採礦模型](/sql/dmx/create-mining-model-dmx)。</span><span class="sxs-lookup"><span data-stu-id="cda22-108">In order to create a mining model directly and automatically generate the underlying mining structure, you use the [CREATE MINING MODEL &#40;DMX&#41;](/sql/dmx/create-mining-model-dmx) statement.</span></span> <span data-ttu-id="cda22-109">陳述式中的程式碼可分成下列各部份：</span><span class="sxs-lookup"><span data-stu-id="cda22-109">The code in the statement can be broken into the following parts:</span></span>  
  
-   <span data-ttu-id="cda22-110">命名模型</span><span class="sxs-lookup"><span data-stu-id="cda22-110">Naming the model</span></span>  
  
-   <span data-ttu-id="cda22-111">定義時間戳記</span><span class="sxs-lookup"><span data-stu-id="cda22-111">Defining the time stamp</span></span>  
  
-   <span data-ttu-id="cda22-112">定義選擇性數列索引鍵資料行</span><span class="sxs-lookup"><span data-stu-id="cda22-112">Defining the optional series key column</span></span>  
  
-   <span data-ttu-id="cda22-113">定義可預測的屬性</span><span class="sxs-lookup"><span data-stu-id="cda22-113">Defining the predictable attribute or attributes</span></span>  
  
 <span data-ttu-id="cda22-114">以下是 CREATE MINING MODEL 陳述式的一般範例：</span><span class="sxs-lookup"><span data-stu-id="cda22-114">The following is a generic example of the CREATE MINING MODEL statement:</span></span>  
  
```  
CREATE MINING MODEL [<Mining Structure Name>]  
(  
   <key columns>,  
   <predictable attribute columns>  
)  
USING <algorithm name>([parameter list])  
WITH DRILLTHROUGH  
```  
  
 <span data-ttu-id="cda22-115">此程式碼的第一行會定義採礦模型的名稱：</span><span class="sxs-lookup"><span data-stu-id="cda22-115">The first line of the code defines the name of the mining model:</span></span>  
  
```  
CREATE MINING MODEL [Mining Model Name]  
```  
  
 <span data-ttu-id="cda22-116">Analysis Services 會自動產生基礎結構的名稱，其方式是在模型名稱後附加 "_structure"，如此可確保結構名稱與模型名稱一樣保持唯一。</span><span class="sxs-lookup"><span data-stu-id="cda22-116">Analysis Services automatically generates a name for the underlying structure, by appending "_structure" to the model name, which ensures that the structure name is unique from the model name.</span></span> <span data-ttu-id="cda22-117">如需在 DMX 中命名物件的詳細資訊，請參閱[dmx&#41;&#40;的識別碼](/sql/dmx/identifiers-dmx)。</span><span class="sxs-lookup"><span data-stu-id="cda22-117">For information about naming an object in DMX, see [Identifiers &#40;DMX&#41;](/sql/dmx/identifiers-dmx).</span></span>  
  
 <span data-ttu-id="cda22-118">此程式碼的下一行會定義採礦模型的索引鍵資料行，其中時間序列模型的案例會唯一識別來源資料中的時間步驟。</span><span class="sxs-lookup"><span data-stu-id="cda22-118">The next line of the code defines the key column for the mining model, which in the case of a time series model uniquely identifies a time step in the source data.</span></span> <span data-ttu-id="cda22-119">在資料行名稱和資料類型之後使用 `KEY TIME` 關鍵字識別時間步驟。</span><span class="sxs-lookup"><span data-stu-id="cda22-119">The time step is identified with the `KEY TIME` keywords after the column name and data types.</span></span> <span data-ttu-id="cda22-120">如果時間序列模型具有個別的數列索引鍵，將會使用 `KEY` 關鍵字來識別它。</span><span class="sxs-lookup"><span data-stu-id="cda22-120">If the time series model has a separate series key, it is identified by using the `KEY` keyword.</span></span>  
  
```  
<key columns>  
```  
  
 <span data-ttu-id="cda22-121">此程式碼的下一行是用來定義此模型中將要預測的資料行。</span><span class="sxs-lookup"><span data-stu-id="cda22-121">The next line of the code is used to define the columns in the model that will be predicted.</span></span> <span data-ttu-id="cda22-122">在單一採礦模型中可以有多個可預測屬性。</span><span class="sxs-lookup"><span data-stu-id="cda22-122">You can have multiple predictable attributes in a single mining model.</span></span> <span data-ttu-id="cda22-123">當有多個可預測屬性時，Microsoft 時間序列演算法會針對每一個數列產生個別的分析：</span><span class="sxs-lookup"><span data-stu-id="cda22-123">When there are multiple predictable attributes, the Microsoft Time Series algorithm generates a separate analysis for each series:</span></span>  
  
```  
<predictable attribute columns>  
```  
  
## <a name="lesson-tasks"></a><span data-ttu-id="cda22-124">課程工作</span><span class="sxs-lookup"><span data-stu-id="cda22-124">Lesson Tasks</span></span>  
 <span data-ttu-id="cda22-125">您將在這一課執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="cda22-125">You will perform the following tasks in this lesson:</span></span>  
  
-   <span data-ttu-id="cda22-126">建立新的空白查詢</span><span class="sxs-lookup"><span data-stu-id="cda22-126">Create a new blank query</span></span>  
  
-   <span data-ttu-id="cda22-127">改變查詢來建立採礦模型</span><span class="sxs-lookup"><span data-stu-id="cda22-127">Alter the query to create the mining model</span></span>  
  
-   <span data-ttu-id="cda22-128">執行查詢</span><span class="sxs-lookup"><span data-stu-id="cda22-128">Execute the query</span></span>  
  
## <a name="creating-the-query"></a><span data-ttu-id="cda22-129">建立查詢</span><span class="sxs-lookup"><span data-stu-id="cda22-129">Creating the Query</span></span>  
 <span data-ttu-id="cda22-130">第一步是連接到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的執行個體，並在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中建立新的 DMX 查詢。</span><span class="sxs-lookup"><span data-stu-id="cda22-130">The first step is to connect to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] and create a new DMX query in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
#### <a name="to-create-a-new-dmx-query-in-sql-server-management-studio"></a><span data-ttu-id="cda22-131">若要在 SQL Server Management Studio 中建立新的 DMX 查詢</span><span class="sxs-lookup"><span data-stu-id="cda22-131">To create a new DMX query in SQL Server Management Studio</span></span>  
  
1.  <span data-ttu-id="cda22-132">開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="cda22-132">Open [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="cda22-133">在 [**連接到伺服器**] 對話方塊的 [**伺服器類型**] 中，選取 [ **Analysis Services**]。</span><span class="sxs-lookup"><span data-stu-id="cda22-133">In the **Connect to Server** dialog box, for **Server type**, select **Analysis Services**.</span></span> <span data-ttu-id="cda22-134">在 [**伺服器名稱**] 中，輸入 `LocalHost` ，或 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 您想要在本課程中連接之實例的名稱。</span><span class="sxs-lookup"><span data-stu-id="cda22-134">In **Server name**, type `LocalHost`, or the name of the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] that you want to connect to for this lesson.</span></span> <span data-ttu-id="cda22-135">按一下 [ **連接**]。</span><span class="sxs-lookup"><span data-stu-id="cda22-135">Click **Connect**.</span></span>  
  
3.  <span data-ttu-id="cda22-136">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX**]。</span><span class="sxs-lookup"><span data-stu-id="cda22-136">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="cda22-137">此時會開啟 [查詢編輯器] 且包含新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="cda22-137">Query Editor opens and contains a new, blank query.</span></span>  
  
## <a name="altering-the-query"></a><span data-ttu-id="cda22-138">改變查詢</span><span class="sxs-lookup"><span data-stu-id="cda22-138">Altering the Query</span></span>  
 <span data-ttu-id="cda22-139">下一步是修改 CREATE MINING MODEL 陳述式來建立預測用的採礦模型，連同它的基礎採礦結構。</span><span class="sxs-lookup"><span data-stu-id="cda22-139">The next step is to modify the CREATE MINING MODEL statement to create the mining model used for forecasting, together with its underlying mining structure.</span></span>  
  
#### <a name="to-customize-the-create-mining-model-statement"></a><span data-ttu-id="cda22-140">若要自訂 CREATE MINING MODEL 陳述式</span><span class="sxs-lookup"><span data-stu-id="cda22-140">To customize the CREATE MINING MODEL statement</span></span>  
  
1.  <span data-ttu-id="cda22-141">在查詢編輯器中，將 CREATE MINING MODEL 陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="cda22-141">In Query Editor, copy the generic example of the CREATE MINING MODEL statement into the blank query.</span></span>  
  
2.  <span data-ttu-id="cda22-142">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="cda22-142">Replace the following:</span></span>  
  
    ```  
    [mining model name]   
    ```  
  
     <span data-ttu-id="cda22-143">成為：</span><span class="sxs-lookup"><span data-stu-id="cda22-143">with:</span></span>  
  
    ```  
    [Forecasting_MIXED]  
    ```  
  
3.  <span data-ttu-id="cda22-144">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="cda22-144">Replace the following:</span></span>  
  
    ```  
    <key columns>  
    ```  
  
     <span data-ttu-id="cda22-145">成為：</span><span class="sxs-lookup"><span data-stu-id="cda22-145">with:</span></span>  
  
    ```  
    [Reporting Date] DATE KEY TIME,  
    [Model Region] TEXT KEY  
    ```  
  
     <span data-ttu-id="cda22-146">`TIME KEY` 關鍵字指示 ReportingDate 資料行包含用來排序值的時間步驟值。</span><span class="sxs-lookup"><span data-stu-id="cda22-146">The `TIME KEY` keyword indicates that the ReportingDate column contains the time step values used to order the values.</span></span> <span data-ttu-id="cda22-147">時間步驟可以是日期和時間、整數，或是任何排序的資料類型，只要這些值是唯一而且可排序資料即可。</span><span class="sxs-lookup"><span data-stu-id="cda22-147">Time steps can be dates and times, integers, or any ordered data type, so long as the values are unique and the data is sorted.</span></span>  
  
     <span data-ttu-id="cda22-148">`TEXT` 和 `KEY` 關鍵字指示 ModelRegion 資料行包含其他數列索引鍵。</span><span class="sxs-lookup"><span data-stu-id="cda22-148">The `TEXT` and `KEY` keywords indicate that the ModelRegion column contains an additional series key.</span></span> <span data-ttu-id="cda22-149">您只能有一個數列索引鍵，而且此資料行中的值必須相異。</span><span class="sxs-lookup"><span data-stu-id="cda22-149">You can have only one series key, and the values in the column must be distinct.</span></span>  
  
4.  <span data-ttu-id="cda22-150">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="cda22-150">Replace the following:</span></span>  
  
    ```  
    < predictable attribute columns> )  
    ```  
  
     <span data-ttu-id="cda22-151">成為：</span><span class="sxs-lookup"><span data-stu-id="cda22-151">with:</span></span>  
  
    ```  
    [Quantity] LONG CONTINUOUS PREDICT,  
    [Amount] DOUBLE CONTINUOUS PREDICT  
    )  
    ```  
  
5.  <span data-ttu-id="cda22-152">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="cda22-152">Replace the following:</span></span>  
  
    ```  
    USING <algorithm name>([parameter list])  
    WITH DRILLTHROUGH  
    ```  
  
     <span data-ttu-id="cda22-153">成為：</span><span class="sxs-lookup"><span data-stu-id="cda22-153">with:</span></span>  
  
    ```  
    USING Microsoft_Time_Series(AUTO_DETECT_PERIODICITY = 0.8, FORECAST_METHOD = 'MIXED')  
    WITH DRILLTHROUGH  
    ```  
  
     <span data-ttu-id="cda22-154">演算法參數 `AUTO_DETECT_PERIODICITY` = 0.8 指示您希望此演算法偵測資料中的循環。</span><span class="sxs-lookup"><span data-stu-id="cda22-154">The algorithm parameter, `AUTO_DETECT_PERIODICITY` = 0.8, indicates that you want the algorithm to detect cycles in the data.</span></span> <span data-ttu-id="cda22-155">將這個值設定為越接近 1，就會探索更多的模式，但是會減緩處理的速度。</span><span class="sxs-lookup"><span data-stu-id="cda22-155">Setting this value closer to 1 favors the discovery of many patterns but can slow processing.</span></span>  
  
     <span data-ttu-id="cda22-156">演算法參數 `FORECAST_METHOD` 指示您是否想要使用 ARTXP、ARIMA 或混用這兩者來分析資料。</span><span class="sxs-lookup"><span data-stu-id="cda22-156">The algorithm parameter, `FORECAST_METHOD`, indicates whether you want the data to be analyzed using ARTXP, ARIMA, or a mixture of both.</span></span>  
  
     <span data-ttu-id="cda22-157">`WITH DRILLTHROUGH` 關鍵字指定您希望在完成此模型之後，能夠檢視來源資料中的詳細統計資料。</span><span class="sxs-lookup"><span data-stu-id="cda22-157">The keyword, `WITH DRILLTHROUGH`, specify that you want to be able to view detailed statistics in the source data after the model is complete.</span></span> <span data-ttu-id="cda22-158">如果您想要使用 Microsoft 時間序列檢視器來瀏覽此模型，必須加入這個子句。</span><span class="sxs-lookup"><span data-stu-id="cda22-158">You must add this clause if you want to browse the model by using the Microsoft Time Series Viewer.</span></span> <span data-ttu-id="cda22-159">預測時則不需要使用它。</span><span class="sxs-lookup"><span data-stu-id="cda22-159">It is not required for prediction.</span></span>  
  
     <span data-ttu-id="cda22-160">現在，完整的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="cda22-160">The complete statement should now be as follows:</span></span>  
  
    ```  
    CREATE MINING MODEL [Forecasting_MIXED]  
         (  
        [Reporting Date] DATE KEY TIME,  
        [Model Region] TEXT KEY,  
        [Quantity] LONG CONTINUOUS PREDICT,  
        [Amount] DOUBLE CONTINUOUS PREDICT  
        )  
    USING Microsoft_Time_Series (AUTO_DETECT_PERIODICITY = 0.8, FORECAST_METHOD = 'MIXED')  
    WITH DRILLTHROUGH  
  
    ```  
  
6.  <span data-ttu-id="cda22-161">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="cda22-161">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="cda22-162">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `Forecasting_MIXED.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="cda22-162">In the **Save As** dialog box, browse to the appropriate folder, and name the file `Forecasting_MIXED.dmx`.</span></span>  
  
## <a name="executing-the-query"></a><span data-ttu-id="cda22-163">執行查詢</span><span class="sxs-lookup"><span data-stu-id="cda22-163">Executing the Query</span></span>  
 <span data-ttu-id="cda22-164">最後的步驟是執行查詢。</span><span class="sxs-lookup"><span data-stu-id="cda22-164">The final step is to execute the query.</span></span> <span data-ttu-id="cda22-165">在建立及儲存查詢之後，需要執行它，才能在伺服器上建立採礦模型和它的採礦結構。</span><span class="sxs-lookup"><span data-stu-id="cda22-165">After a query is created and saved, it needs to be executed to create the mining model and its mining structure on the server.</span></span> <span data-ttu-id="cda22-166">如需在 [查詢編輯器] 中執行查詢的詳細資訊，請參閱[資料庫引擎查詢編輯器 &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md)。</span><span class="sxs-lookup"><span data-stu-id="cda22-166">For more information about executing queries in Query Editor, see [Database Engine Query Editor &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/database-engine-query-editor-sql-server-management-studio.md).</span></span>  
  
#### <a name="to-execute-the-query"></a><span data-ttu-id="cda22-167">若要執行查詢</span><span class="sxs-lookup"><span data-stu-id="cda22-167">To execute the query</span></span>  
  
-   <span data-ttu-id="cda22-168">在 [查詢編輯器] 的工具列上，按一下 [**執行**]。</span><span class="sxs-lookup"><span data-stu-id="cda22-168">In Query Editor, on the toolbar, click **Execute**.</span></span>  
  
     <span data-ttu-id="cda22-169">查詢的狀態會在語句完成執行之後，顯示在 [查詢編輯器] 底部的 [**訊息**] 索引標籤中。</span><span class="sxs-lookup"><span data-stu-id="cda22-169">The status of the query is displayed in the **Messages** tab at the bottom of Query Editor after the statement finishes executing.</span></span> <span data-ttu-id="cda22-170">訊息應該顯示如下：</span><span class="sxs-lookup"><span data-stu-id="cda22-170">Messages should display:</span></span>  
  
    ```  
    Executing the query   
    Execution complete  
    ```  
  
     <span data-ttu-id="cda22-171">現在伺服器上已存在名為**Forecasting_MIXED_Structure**的新結構，以及相關的「採礦模型**Forecasting_MIXED**。</span><span class="sxs-lookup"><span data-stu-id="cda22-171">A new structure named **Forecasting_MIXED_Structure** now exists on the server, together with the related mining model **Forecasting_MIXED**.</span></span>  
  
 <span data-ttu-id="cda22-172">在下一課中，您會將「採礦模型」新增至您剛才建立的**Forecasting_MIXED**的「採礦結構」中。</span><span class="sxs-lookup"><span data-stu-id="cda22-172">In the next lesson, you will add a mining model to the **Forecasting_MIXED** mining structure that you just created.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="cda22-173">下一課</span><span class="sxs-lookup"><span data-stu-id="cda22-173">Next Lesson</span></span>  
 [<span data-ttu-id="cda22-174">第 2 課：將採礦模型新增至時間序列採礦結構</span><span class="sxs-lookup"><span data-stu-id="cda22-174">Lesson 2: Adding Mining Models to the Time Series Mining Structure</span></span>](../../2014/tutorials/lesson-2-adding-mining-models-to-the-time-series-mining-structure.md)  
  
## <a name="see-also"></a><span data-ttu-id="cda22-175">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cda22-175">See Also</span></span>  
 <span data-ttu-id="cda22-176">[時間序列模型的採礦模型內容 &#40;Analysis Services 資料採礦&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="cda22-176">[Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md) </span></span>  
 [<span data-ttu-id="cda22-177">Microsoft 時間序列演算法技術參考</span><span class="sxs-lookup"><span data-stu-id="cda22-177">Microsoft Time Series Algorithm Technical Reference</span></span>](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md)  
  
  
