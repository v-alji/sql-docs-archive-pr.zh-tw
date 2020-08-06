---
title: " (元資料採礦教學課程的先進時間序列預測) |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: b614ebdb-07ca-44af-a0ff-893364bd4b71
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 70ebf856ba0782cbf44969aba30602818015582a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704501"
---
# <a name="advanced-time-series-predictions-intermediate-data-mining-tutorial"></a><span data-ttu-id="65f50-102">進階時間序列預測 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="65f50-102">Advanced Time Series Predictions (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="65f50-103">您已經從預測模型的瀏覽得知，雖然大部分地區的銷售都遵循類似的模式，但是某些地區和某些模型 (如太平洋地區的 M200 模型) 則呈現了非常不同的趨勢。</span><span class="sxs-lookup"><span data-stu-id="65f50-103">You saw from exploring the forecasting model that although sales in most of the regions follow a similar pattern, some regions and some models, such as the M200 model in the Pacific region, exhibit very different trends.</span></span> <span data-ttu-id="65f50-104">這不令您吃驚，因為您知道地區之間的差異是很常見的，而且可能是因為許多因素所造成，其中包括促銷活動、不正確的報表或地理政治事件。</span><span class="sxs-lookup"><span data-stu-id="65f50-104">This does not surprise you, as you know that differences among regions are common and can be caused by many factors, including marketing promotions, inaccurate reporting, or geopolitical events.</span></span>  
  
 <span data-ttu-id="65f50-105">但是您的使用者要求全球適用的模型。</span><span class="sxs-lookup"><span data-stu-id="65f50-105">However, your users are asking for a model that can be applied worldwide.</span></span> <span data-ttu-id="65f50-106">因此，為了讓個別因素對預測的影響降至最低，您決定建立一個根據全球銷售彙總量值的模型。</span><span class="sxs-lookup"><span data-stu-id="65f50-106">Therefore, to minimize the effect of individual factors on projections, you decide to build a model that is based on aggregated measures of worldwide sales.</span></span> <span data-ttu-id="65f50-107">然後您可以使用這個模型，針對各地區做預測。</span><span class="sxs-lookup"><span data-stu-id="65f50-107">You can then use this model to make predictions for each individual region.</span></span>  
  
 <span data-ttu-id="65f50-108">在這項工作中，您將建立執行進階預測工作所需的所有資料來源。</span><span class="sxs-lookup"><span data-stu-id="65f50-108">In this task, you will build all the data sources that you need to perform the advanced prediction tasks.</span></span> <span data-ttu-id="65f50-109">您將建立兩個做為預測查詢輸入的資料來源檢視和一個用於建立新模型的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="65f50-109">You will create two data source views for use as inputs to the prediction query, and one data source view to use in building a new model.</span></span>  
  
 <span data-ttu-id="65f50-110">**步驟**</span><span class="sxs-lookup"><span data-stu-id="65f50-110">**Steps**</span></span>  
  
1.  [<span data-ttu-id="65f50-111">準備擴充銷售資料 (用於預測)</span><span class="sxs-lookup"><span data-stu-id="65f50-111">Prepare the extended sales data (for prediction)</span></span>](#bkmk_newExtendData)  
  
2.  [<span data-ttu-id="65f50-112">準備彙總資料 (用於建立模型)</span><span class="sxs-lookup"><span data-stu-id="65f50-112">Prepare the aggregated data (for building the model)</span></span>](#bkmk_newReplaceData)  
  
3.  [<span data-ttu-id="65f50-113">準備數列資料 (用於交叉預測)</span><span class="sxs-lookup"><span data-stu-id="65f50-113">Prepare the series data (for cross-prediction)</span></span>](#bkmk_CrossData2)  
  
4.  [<span data-ttu-id="65f50-114">使用 EXTEND 做預測</span><span class="sxs-lookup"><span data-stu-id="65f50-114">Predict using EXTEND</span></span>](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
5.  [<span data-ttu-id="65f50-115">建立交叉預測模型</span><span class="sxs-lookup"><span data-stu-id="65f50-115">Create the cross-prediction model</span></span>](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
6.  [<span data-ttu-id="65f50-116">使用 REPLACE 做預測</span><span class="sxs-lookup"><span data-stu-id="65f50-116">Predict using REPLACE</span></span>](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
7.  [<span data-ttu-id="65f50-117">檢閱新預測</span><span class="sxs-lookup"><span data-stu-id="65f50-117">Review the new predictions</span></span>](../../2014/tutorials/comparing-predictions-for-forecasting-models-intermediate-data-mining-tutorial.md)  
  
##  <a name="creating-the-new-extended-sales-data"></a><a name="bkmk_newExtendData"></a><span data-ttu-id="65f50-118">建立新的擴充銷售資料</span><span class="sxs-lookup"><span data-stu-id="65f50-118">Creating the New Extended Sales Data</span></span>  
 <span data-ttu-id="65f50-119">您需要取得最新的銷售數字，以更新銷售資料。</span><span class="sxs-lookup"><span data-stu-id="65f50-119">To update your sales data, you will need to get the latest sales figures.</span></span> <span data-ttu-id="65f50-120">特別值得注意的是來自太平洋地區的最新資料，這裡剛發起區域性銷售促銷，讓新店面及其商品吸引眾人目光。</span><span class="sxs-lookup"><span data-stu-id="65f50-120">Of particular interest are the data just in from the Pacific region, which launched a regional sales promotion to call attention to the new stores and raise awareness of their products.</span></span>  
  
 <span data-ttu-id="65f50-121">在此案例中，我們假設已從 Excel 活頁簿匯入資料，其中只包含三個月的新資料供幾個區域使用。</span><span class="sxs-lookup"><span data-stu-id="65f50-121">For this scenario, we'll assume that the data has been imported from an Excel workbook that contains just three months of new data for a couple of regions.</span></span> <span data-ttu-id="65f50-122">您將使用 Transact-sql 腳本來建立資料的資料表，然後定義要用於預測的資料來源 view。</span><span class="sxs-lookup"><span data-stu-id="65f50-122">You'll create a table for the data using a Transact-SQL script, and then define a data source view to use for prediction.</span></span>  
  
#### <a name="create-the-table-with-new-sales-data"></a><span data-ttu-id="65f50-123">使用新銷售資料建立資料表</span><span class="sxs-lookup"><span data-stu-id="65f50-123">Create the table with new sales data</span></span>  
  
1.  <span data-ttu-id="65f50-124">在 Transact-SQL 查詢視窗中，執行下列陳述式，將銷售資料加入至 AdventureWorksDW 資料庫 (或其他任何資料庫)。</span><span class="sxs-lookup"><span data-stu-id="65f50-124">In a Transact-SQL query window, execute the following statement to add the sales data to the AdventureWorksDW database (or any other database).</span></span>  
  
    ```  
    USE [database name];  
    GO  
    IF OBJECT_ID ([dbo].[NewSalesData]) IS NOT NULL   
        DROP TABLE [dbo].[NewSalesData];  
    GO  
    CREATE TABLE [dbo].[NewSalesData]([Series] [nvarchar](255) NULL,  
    [NewDate] [datetime] NULL,  
    [NewQty] [float] NULL,  
    [NewAmount] [money] NULL) ON [PRIMARY]  
  
    GO  
    ```  
  
2.  <span data-ttu-id="65f50-125">使用下列指令碼插入新值。</span><span class="sxs-lookup"><span data-stu-id="65f50-125">Insert the new values using the following script.</span></span>  
  
    ```  
    INSERT INTO [NewSalesData]  
    (Series,NewDate,NewQty,NewAmount)  
    VALUES('T1000 Pacific', '7/25/08', 55, '$130,170.22'),  
    ('T1000 Pacific', '8/25/08', 50, '$114,435.36 '),  
    ('T1000 Pacific', '9/25/08', 50, '$117,296.24 '),  
    ('T1000 Europe', '7/25/08', 37, '$88,210.00 '),  
    ('T1000 Europe', '8/25/08', 41, '$97,746.00 '),  
    ('T1000 Europe', '9/25/08', 37, '$88,210.00 '),  
    ('T1000 North America', '7/25/08', 69, '$164,500.00 '),  
    ('T1000 North America', '8/25/08', 66, '$157,348.00 '),  
    ('T1000 North America', '9/25/08', 58, '$138,276.00 '),  
    ('M200 Pacific', '7/25/08', 65, '$149,824.35'),  
    ('M200 Pacific', '8/25/08', 54,  '$124,619.46'),  
    ('M200 Pacific', '9/25/08', 61, '$141,143.39'),  
    ('M200 Europe', '7/25/08', 75, '$173,026.00'),  
    ('M200 Europe', '8/25/08', 76, '$175,212.00'),  
    ('M200 Europe', '9/25/08', 84, '$193,731.00'),  
    ('M200 North America', '7/25/08', 94, '$216,916.00'),  
    ('M200 North America', '8/25/08', 94, '$216,891.00'),  
    ('M200 North America', '9/25/08', 91,'$209,943.00');  
    ```  
  
    > [!WARNING]  
    >  <span data-ttu-id="65f50-126">引號用於貨幣值，以避免通用分隔符號和貨幣符號發生問題。</span><span class="sxs-lookup"><span data-stu-id="65f50-126">The quotation marks are used with the currency values to prevent problems with the comma separator and the currency symbol.</span></span> <span data-ttu-id="65f50-127">您也可以使用下列格式傳入貨幣值：`130170.22`</span><span class="sxs-lookup"><span data-stu-id="65f50-127">You could also pass in the currency values in this format: `130170.22`</span></span>  
    >   
    >  <span data-ttu-id="65f50-128">請注意，範例資料庫中使用的日期已在此版本中變更。</span><span class="sxs-lookup"><span data-stu-id="65f50-128">Note that the dates used in the sample database have changed for this release.</span></span> <span data-ttu-id="65f50-129">如果您使用的是舊版的 AdventureWorks，可能需要針對插入的日期進行相應的調整。</span><span class="sxs-lookup"><span data-stu-id="65f50-129">If you are using an earlier edition of AdventureWorks, you might need to adjust the inserted dates accordingly.</span></span>  
  
###  <a name="create-a-data-source-view-using-the-new-sales-data"></a><a name="bkmk_newReplaceData"></a><span data-ttu-id="65f50-130">使用新的銷售資料來建立資料來源視圖</span><span class="sxs-lookup"><span data-stu-id="65f50-130">Create a data source view using the new sales data</span></span>  
  
1.  <span data-ttu-id="65f50-131">在**方案總管**中，以滑鼠右鍵按一下 [**資料來源視圖**]，然後選取 [**新增資料來源視圖**]。</span><span class="sxs-lookup"><span data-stu-id="65f50-131">In **Solution Explorer**, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="65f50-132">在資料來源檢視精靈中，進行下列選擇：</span><span class="sxs-lookup"><span data-stu-id="65f50-132">In the Data Source View wizard, make the following selections:</span></span>  
  
     <span data-ttu-id="65f50-133">**資料來源**：[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65f50-133">**Data Source**: [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]</span></span>  
  
     <span data-ttu-id="65f50-134">**選取資料表和視圖**：選取您剛才建立的資料表 NewSalesData。</span><span class="sxs-lookup"><span data-stu-id="65f50-134">**Select Tables and Views**: Select the table that you just created, NewSalesData.</span></span>  
  
3.  <span data-ttu-id="65f50-135">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="65f50-135">Click **Finish**.</span></span>  
  
4.  <span data-ttu-id="65f50-136">在 [資料來源] 視圖設計介面中，以滑鼠右鍵按一下 [NewSalesData]，然後選取 [**流覽資料**] 以驗證資料。</span><span class="sxs-lookup"><span data-stu-id="65f50-136">In the Data Source View design surface, right-click NewSalesData, and then select **Explore Data** to verify the data.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="65f50-137">此資料僅供預測，資料不完整沒有關係。</span><span class="sxs-lookup"><span data-stu-id="65f50-137">You will use this data for prediction only, so it does not matter that the data is incomplete.</span></span>  
  
##  <a name="creating-the-data-for-the-cross-prediction-model"></a><a name="bkmk_CrossData2"></a><span data-ttu-id="65f50-138">建立交叉預測模型的資料</span><span class="sxs-lookup"><span data-stu-id="65f50-138">Creating the Data for the Cross-Prediction Model</span></span>  
 <span data-ttu-id="65f50-139">原始預測模型中所用的資料已經依 vTimeSeries 檢視稍微分組，數款自行車已摺疊為較少的類別目錄數目，各國結果已合併為地區。</span><span class="sxs-lookup"><span data-stu-id="65f50-139">The data that was used in the original forecasting model was already grouped somewhat by the view vTimeSeries, which collapsed several bike models into a smaller number of categories, and merged results from individual countries into regions.</span></span> <span data-ttu-id="65f50-140">若要建立可用於全球預測的模型，您將直接在資料來源檢視設計工具中建立一些其他簡單彙總。</span><span class="sxs-lookup"><span data-stu-id="65f50-140">To create a model that can be used for world-wide projections, you will create some additional simple aggregations directly in the Data Source View Designer.</span></span> <span data-ttu-id="65f50-141">新的資料來源檢視只包含所有地區所有產品的銷售總和與平均值。</span><span class="sxs-lookup"><span data-stu-id="65f50-141">The new data source view will contain just a sum and an average of the sales of all products for all regions.</span></span>  
  
 <span data-ttu-id="65f50-142">在建立用於模型的資料來源之後，您必須建立一個用於預測的新資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="65f50-142">After you have created the data source used for the model, you must create a new data source view to use for prediction.</span></span> <span data-ttu-id="65f50-143">例如，如果您要使用新的全球模型來預測歐洲銷售，必須只饋送歐洲地區的資料。</span><span class="sxs-lookup"><span data-stu-id="65f50-143">For example, if you want to predict sales for Europe using the new worldwide model, you must feed in data for the Europe region only.</span></span> <span data-ttu-id="65f50-144">因此，您將設定可篩選原始資料的新資料來源檢視，並針對各組預測查詢來變更篩選條件。</span><span class="sxs-lookup"><span data-stu-id="65f50-144">So you will set up a new data source view that filters the original data, and change the filter condition for each set of prediction queries.</span></span>  
  
#### <a name="to-create-the-model-data-using-a-custom-data-source-view"></a><span data-ttu-id="65f50-145">若要使用自訂資料來源檢視建立模型資料</span><span class="sxs-lookup"><span data-stu-id="65f50-145">To create the model data using a custom data source view</span></span>  
  
1.  <span data-ttu-id="65f50-146">在**方案總管**中，以滑鼠右鍵按一下 [**資料來源視圖**]，然後選取 [**新增資料來源視圖**]。</span><span class="sxs-lookup"><span data-stu-id="65f50-146">In **Solution Explorer**, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="65f50-147">在精靈的歡迎頁面中，按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="65f50-147">On the welcome page of the wizard, click **Next**.</span></span>  
  
3.  <span data-ttu-id="65f50-148">在 **[選取資料來源]** 頁面上，選取 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="65f50-148">On the **Select Data Source** page, select [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)], and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="65f50-149">在頁面中，**選取 [資料表和視圖]**，不要加入任何資料表，只要按 **[下一步]** 即可。</span><span class="sxs-lookup"><span data-stu-id="65f50-149">In the page, **Select Tables and Views**, do not add any tables-just click **Next**.</span></span>  
  
5.  <span data-ttu-id="65f50-150">在 [**完成嚮導]** 頁面上，輸入名稱 `AllRegions` ，然後按一下 **[完成**]。</span><span class="sxs-lookup"><span data-stu-id="65f50-150">On the page, **Completing the Wizard**, type the name `AllRegions`, and then click **Finish**.</span></span>  
  
6.  <span data-ttu-id="65f50-151">接下來，以滑鼠右鍵按一下空白的資料來源視圖設計介面，然後選取 [新增] [**指名的查詢**]。</span><span class="sxs-lookup"><span data-stu-id="65f50-151">Next, right-click the blank data source view design surface, and then select **New Named Query**.</span></span>  
  
7.  <span data-ttu-id="65f50-152">在 [**建立指名的查詢**] 對話方塊中，針對 [**名稱**] 輸入 `AllRegions` ，並針對 [**描述**] 輸入**所有模型和地區的銷售總和和平均值**。</span><span class="sxs-lookup"><span data-stu-id="65f50-152">In the **Create Named Query** dialog box, for **Name**, type `AllRegions`, and for **Description**, type **Sum and average of sales for all models and regions**.</span></span>  
  
8.  <span data-ttu-id="65f50-153">在 SQL 文字窗格中，輸入下列陳述式，然後按一下 [確定]：</span><span class="sxs-lookup"><span data-stu-id="65f50-153">In the SQL text pane, type the following statement and then click OK:</span></span>  
  
    ```  
    SELECT ReportingDate,   
    SUM([Quantity]) as SumQty, AVG([Quantity]) as AvgQty,  
    SUM([Amount]) AS SumAmt, AVG([Amount]) AS AvgAmt,  
    'All Regions' as [Region]  
    FROM dbo.vTimeSeries   
    GROUP BY ReportingDate  
    ```  
  
9. <span data-ttu-id="65f50-154">以滑鼠右鍵按一下 `AllRegions` 資料表，然後選取 [**流覽資料**]。</span><span class="sxs-lookup"><span data-stu-id="65f50-154">Right-click the `AllRegions` table, and then select **Explore Data**.</span></span>  
  
###  <a name="to-create-the-series-data-for-cross-prediction"></a><a name="bkmk_CrossData"></a><span data-ttu-id="65f50-155">若要建立交叉預測的數列資料</span><span class="sxs-lookup"><span data-stu-id="65f50-155">To create the series data for cross-prediction</span></span>  
  
1.  <span data-ttu-id="65f50-156">在**方案總管**中，以滑鼠右鍵按一下 [**資料來源視圖**]，然後選取 [**新增資料來源視圖**]。</span><span class="sxs-lookup"><span data-stu-id="65f50-156">In **Solution Explorer**, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="65f50-157">在資料來源檢視精靈中，進行下列選擇：</span><span class="sxs-lookup"><span data-stu-id="65f50-157">In the Data Source View wizard, make the following selections:</span></span>  
  
     <span data-ttu-id="65f50-158">**資料來源**：[!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]</span><span class="sxs-lookup"><span data-stu-id="65f50-158">**Data Source**: [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)]</span></span>  
  
     <span data-ttu-id="65f50-159">**選取資料表和檢視表**：不選取任何資料表</span><span class="sxs-lookup"><span data-stu-id="65f50-159">**Select Tables and Views**: Do not select any tables</span></span>  
  
     <span data-ttu-id="65f50-160">**名稱**：`T1000 Pacific Region`</span><span class="sxs-lookup"><span data-stu-id="65f50-160">**Name**: `T1000 Pacific Region`</span></span>  
  
3.  <span data-ttu-id="65f50-161">按一下 [完成] 。</span><span class="sxs-lookup"><span data-stu-id="65f50-161">Click **Finish**.</span></span>  
  
4.  <span data-ttu-id="65f50-162">以滑鼠右鍵按一下**T1000 太平洋 Region. dsv**的空白設計介面，然後選取 [**新增**] [指名的查詢]。</span><span class="sxs-lookup"><span data-stu-id="65f50-162">Right-click the empty design surface for **T1000 Pacific Region.dsv**, and then select **New Named Query**.</span></span>  
  
     <span data-ttu-id="65f50-163">**[建立具名查詢]** 對話方塊隨即出現。</span><span class="sxs-lookup"><span data-stu-id="65f50-163">The **Create Named Query** dialog box appears.</span></span> <span data-ttu-id="65f50-164">重新輸入名稱，然後加入以下的描述：</span><span class="sxs-lookup"><span data-stu-id="65f50-164">Retype the name, and then add the following description:</span></span>  
  
     <span data-ttu-id="65f50-165">**名稱**：`T1000 Pacific Region`</span><span class="sxs-lookup"><span data-stu-id="65f50-165">**Name**: `T1000 Pacific Region`</span></span>  
  
     <span data-ttu-id="65f50-166">**描述**： \*\* `vTimeSeries` 依區域和模型篩選\*\*</span><span class="sxs-lookup"><span data-stu-id="65f50-166">**Description**: **Filter`vTimeSeries`by region and model**</span></span>  
  
5.  <span data-ttu-id="65f50-167">在文字窗格中，輸入下列查詢，然後按一下 [確定]：</span><span class="sxs-lookup"><span data-stu-id="65f50-167">In the text pane, type the following query, and then click OK:</span></span>  
  
    ```  
    SELECT ReportingDate, ModelRegion, Quantity, Amount  
    FROM dbo.vTimeSeries  
    WHERE (ModelRegion = N'T1000 Pacific')  
    ```  
  
    > [!NOTE]  
    >  <span data-ttu-id="65f50-168">因為您需要為各數列分別建立預測，您可能會想要複製查詢文字，並將它儲存到文字檔中，以便重複將它用於其他資料數列。</span><span class="sxs-lookup"><span data-stu-id="65f50-168">Since you will need to create predictions for each series separately, you might want to copy the query text and save it to a text file so that you can re-use it for the other data series.</span></span>  
  
6.  <span data-ttu-id="65f50-169">在 [資料來源] 視圖設計介面中，以滑鼠右鍵按一下 [T1000]，然後選取 [**流覽資料**]，確認資料已正確篩選。</span><span class="sxs-lookup"><span data-stu-id="65f50-169">In the Data Source View design surface, right-click T1000 Pacific, and then select **Explore Data** to verify that the data is filtered correctly.</span></span>  
  
     <span data-ttu-id="65f50-170">在建立交叉預測查詢時，您將會使用此資料做為模型的輸入。</span><span class="sxs-lookup"><span data-stu-id="65f50-170">You will use this data as the input to the model when creating cross-prediction queries.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="65f50-171">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="65f50-171">Next Task in Lesson</span></span>  
 [<span data-ttu-id="65f50-172">使用更新的資料 &#40;中繼資料採礦教學課程的時間序列預測&#41;</span><span class="sxs-lookup"><span data-stu-id="65f50-172">Time Series Predictions using Updated Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-predictions-using-updated-data-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="65f50-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65f50-173">See Also</span></span>  
 <span data-ttu-id="65f50-174">[Microsoft 時間序列演算法](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="65f50-174">[Microsoft Time Series Algorithm](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm.md) </span></span>  
 <span data-ttu-id="65f50-175">[Microsoft 時間序列演算法技術參考](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="65f50-175">[Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="65f50-176">多維度模型中的資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="65f50-176">Data Source Views in Multidimensional Models</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
