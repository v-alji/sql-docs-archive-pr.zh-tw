---
title: 使用更新的資料 (元資料採礦教學課程的時間序列預測) |Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: af73681d-ce1c-4b6e-b195-6df3d2fb5275
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 2017defaba74071b1a12bee14a5d8907e4c71cda
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584870"
---
# <a name="time-series-predictions-using-updated-data-intermediate-data-mining-tutorial"></a><span data-ttu-id="0aadd-102">使用更新資料執行時間序列預測 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="0aadd-102">Time Series Predictions using Updated Data (Intermediate Data Mining Tutorial)</span></span>
    
## <a name="creating-predictions-using-the-extended-sales-data"></a><span data-ttu-id="0aadd-103">使用擴充銷售資料建立預測</span><span class="sxs-lookup"><span data-stu-id="0aadd-103">Creating Predictions using the Extended Sales Data</span></span>  
 <span data-ttu-id="0aadd-104">在本課中，您將建立一個預測查詢，這個查詢會將新的銷售資料加入至模型中。</span><span class="sxs-lookup"><span data-stu-id="0aadd-104">In this lesson, you will create a prediction query that adds the new sales data to the model.</span></span> <span data-ttu-id="0aadd-105">透過使用新資料擴充模型，您可以取得包含最新資料點的最新預測。</span><span class="sxs-lookup"><span data-stu-id="0aadd-105">By extending the model with new data, you can get up-to-date predictions that include the newest data points.</span></span>  
  
 <span data-ttu-id="0aadd-106">建立使用新資料的時間序列預測很容易：您只需要將參數 EXTEND_MODEL_CASES 新增至[PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx)函數、指定新資料的來源，並指定您想要取得多少預測。</span><span class="sxs-lookup"><span data-stu-id="0aadd-106">Creating time series predictions that use new data is easy: you simply add the parameter EXTEND_MODEL_CASES to the [PredictTimeSeries &#40;DMX&#41;](/sql/dmx/predicttimeseries-dmx) function, specify the source of the new data, and specify how many predictions you want to get.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="0aadd-107">EXTEND_MODEL_CASES 參數是選擇性的；當您透過聯結新資料做為輸入來建立時間序列預測查詢時，預設就會擴充模型。</span><span class="sxs-lookup"><span data-stu-id="0aadd-107">The parameter EXTEND_MODEL_CASES is optional; by default the model is extended any time that you create a time series prediction query by joining new data as inputs.</span></span>  
  
#### <a name="to-build-the-prediction-query-and-add-new-data"></a><span data-ttu-id="0aadd-108">若要建立預測查詢及加入新資料</span><span class="sxs-lookup"><span data-stu-id="0aadd-108">To build the prediction query and add new data</span></span>  
  
1.  <span data-ttu-id="0aadd-109">如果模型尚未開啟，請按兩下預測結構，然後在 [資料採礦設計師] 中，按一下 [**採礦模型預測**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="0aadd-109">If the model is not already open, double-click the Forecasting structure, and in Data Mining Designer, click the **Mining Model Prediction** tab.</span></span>  
  
2.  <span data-ttu-id="0aadd-110">在 [**採礦模型**] 窗格中，應該已經選取模型預測。</span><span class="sxs-lookup"><span data-stu-id="0aadd-110">In the **Mining Model** pane, the model Forecasting should already be selected.</span></span> <span data-ttu-id="0aadd-111">如果未選取，請按一下 [**選取模型**]，然後選取模型 [預測]。</span><span class="sxs-lookup"><span data-stu-id="0aadd-111">If it is not selected, click **Select Model**, and then select the model, Forecasting.</span></span>  
  
3.  <span data-ttu-id="0aadd-112">在 [**選取輸入資料表 (s) \*\* ] 窗格中，按一下 [**選取案例資料表\*\*]。</span><span class="sxs-lookup"><span data-stu-id="0aadd-112">In the **Select Input Table(s)** pane, click **Select Case Table**.</span></span>  
  
4.  <span data-ttu-id="0aadd-113">在 [**選取資料表**] 對話方塊中，選取 [資料來源] [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="0aadd-113">In the **Select Table** dialog box, select the data source, [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span>  
  
     <span data-ttu-id="0aadd-114">從資料來源視圖清單中，選取 [NewSalesData]，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="0aadd-114">From the list of data source views, select NewSalesData and then click **OK**.</span></span>  
  
5.  <span data-ttu-id="0aadd-115">以滑鼠右鍵按一下設計區域的介面，然後選取 [**修改連接**]。</span><span class="sxs-lookup"><span data-stu-id="0aadd-115">Right-click the surface of the design area and select **Modify Connections**.</span></span>  
  
6.  <span data-ttu-id="0aadd-116">使用 [**修改對應**] 對話方塊，將模型中的資料行對應至外部資料中的資料行，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0aadd-116">Using the **Modify Mapping** dialog box, map the columns in the model to the columns in the external data as follows:</span></span>  
  
    -   <span data-ttu-id="0aadd-117">將採礦模型中的 ReportingDate 資料行對應到輸入資料中的 NewDate 資料行。</span><span class="sxs-lookup"><span data-stu-id="0aadd-117">Map the ReportingDate column in the mining model to the NewDate column in the input data.</span></span>  
  
    -   <span data-ttu-id="0aadd-118">將採礦模型中的 [金額] 資料行對應到輸入資料中的 NewAmount 資料行。</span><span class="sxs-lookup"><span data-stu-id="0aadd-118">Map the Amount column in the mining model to the NewAmount column in the input data.</span></span>  
  
    -   <span data-ttu-id="0aadd-119">將採礦模型中的 Quantity 資料行對應到輸入資料中的 NewQty 資料行。</span><span class="sxs-lookup"><span data-stu-id="0aadd-119">Map the Quantity column in the mining model to the NewQty column in the input data.</span></span>  
  
    -   <span data-ttu-id="0aadd-120">將「採礦模型」中的 ModelRegion 資料行對應到輸入資料中的數列資料行。</span><span class="sxs-lookup"><span data-stu-id="0aadd-120">Map the ModelRegion column in the mining model to the Series column in the input data.</span></span>  
  
7.  <span data-ttu-id="0aadd-121">現在，您將建立預測查詢。</span><span class="sxs-lookup"><span data-stu-id="0aadd-121">Now you will build the prediction query.</span></span>  
  
     <span data-ttu-id="0aadd-122">首先，將資料行加入到預測查詢中，以輸出套用此預測的數列。</span><span class="sxs-lookup"><span data-stu-id="0aadd-122">First, add a column to the prediction query to output the series the prediction applies to.</span></span>  
  
    1.  <span data-ttu-id="0aadd-123">在方格中，按一下 [**來源**] 底下的第一個空白資料列，然後選取 [預測]。</span><span class="sxs-lookup"><span data-stu-id="0aadd-123">In the grid, click the first empty row, under **Source**, and then select Forecasting.</span></span>  
  
    2.  <span data-ttu-id="0aadd-124">在 [**欄位**] 資料行中，選取 [模型區域]，然後在 [**別名**] 中輸入 `Model Region` 。</span><span class="sxs-lookup"><span data-stu-id="0aadd-124">In the **Field** column, select Model Region and for **Alias**, type `Model Region`.</span></span>  
  
8.  <span data-ttu-id="0aadd-125">接著加入及編輯預測函數。</span><span class="sxs-lookup"><span data-stu-id="0aadd-125">Next, add and edit the prediction function.</span></span>  
  
    1.  <span data-ttu-id="0aadd-126">按一下空白資料列，然後選取 [**來源**] 底下的 [**預測函數**]。</span><span class="sxs-lookup"><span data-stu-id="0aadd-126">Click an empty row, and under **Source**, select **Prediction Function**.</span></span>  
  
    2.  <span data-ttu-id="0aadd-127">針對 [**欄位**]，選取 [ **PredictTimeSeries**]。</span><span class="sxs-lookup"><span data-stu-id="0aadd-127">For **Field**, select **PredictTimeSeries**.</span></span>  
  
    3.  <span data-ttu-id="0aadd-128">針對 [**別名**]，輸入**預測的值**。</span><span class="sxs-lookup"><span data-stu-id="0aadd-128">For **Alias**, type **Predicted Values**.</span></span>  
  
    4.  <span data-ttu-id="0aadd-129">從 [**採礦模型**] 窗格中，將 [Quantity] 欄位拖曳到 [**準則/引數**] 資料行中。</span><span class="sxs-lookup"><span data-stu-id="0aadd-129">Drag the field Quantity from the **Mining Model** pane into the **Criteria/Argument** column.</span></span>  
  
    5.  <span data-ttu-id="0aadd-130">在 [**準則/引數**] 資料行中，于功能變數名稱後面輸入下列文字： **5，EXTEND_MODEL_CASES**</span><span class="sxs-lookup"><span data-stu-id="0aadd-130">In the **Criteria/Argument** column, after the field name, type the following text:  **5,EXTEND_MODEL_CASES**</span></span>  
  
         <span data-ttu-id="0aadd-131">[**準則/引數**] 文字方塊的完整文字應該如下所示：`[Forecasting].[Quantity],5,EXTEND_MODEL_CASES`</span><span class="sxs-lookup"><span data-stu-id="0aadd-131">The complete text of the **Criteria/Argument** text box should be as follows: `[Forecasting].[Quantity],5,EXTEND_MODEL_CASES`</span></span>  
  
9. <span data-ttu-id="0aadd-132">按一下 [**結果**]，並查看結果。</span><span class="sxs-lookup"><span data-stu-id="0aadd-132">Click **Results** and review the results.</span></span>  
  
     <span data-ttu-id="0aadd-133">預測會在 7 月開始 (原始資料結尾後的第一個時間配量) 並在 11 月結束 (原始資料結尾後的第五個時間配量)。</span><span class="sxs-lookup"><span data-stu-id="0aadd-133">The predictions begin in July (the first time slice after the end of the original data) and end at November (the fifth time slice after the end of the original data).</span></span>  
  
 <span data-ttu-id="0aadd-134">您可以看到，若要有效地使用這類預測查詢，需要知道舊資料何時結束，以及新資料中有多少時間配量。</span><span class="sxs-lookup"><span data-stu-id="0aadd-134">You can see that to use this type of prediction query effectively, you need to know when the old data ends, as well as how many time slices there are in the new data.</span></span>  
  
 <span data-ttu-id="0aadd-135">例如，在此模型中，原始資料數列在 6 月結束，而資料是 7 月、8 月和 9 月這些月份的資料。</span><span class="sxs-lookup"><span data-stu-id="0aadd-135">For example, in this model, the original data series ended in June, and the data is for the months of July, August, and September.</span></span>  
  
 <span data-ttu-id="0aadd-136">使用 EXTEND_MODEL_CASES 的預測一定開始於原始資料數列的結尾。</span><span class="sxs-lookup"><span data-stu-id="0aadd-136">Predictions that use EXTEND_MODEL_CASES always begin at the end of the original data series.</span></span> <span data-ttu-id="0aadd-137">因此，如果您只要取得未知月份的預測，則需要指定預測的起點和終點。</span><span class="sxs-lookup"><span data-stu-id="0aadd-137">Therefore, if you want to get only the predictions for the unknown months, you need to specify the starting point and the end point for prediction.</span></span> <span data-ttu-id="0aadd-138">這兩個值都是以開始於舊資料結尾的時間配量數目指定。</span><span class="sxs-lookup"><span data-stu-id="0aadd-138">Both values are specified as a number of time slices starting at the end of the old data.</span></span>  
  
 <span data-ttu-id="0aadd-139">下列程序示範此做法。</span><span class="sxs-lookup"><span data-stu-id="0aadd-139">The following procedure demonstrates how to do this.</span></span>  
  
### <a name="change-the-start-and-end-points-of-the-predictions"></a><span data-ttu-id="0aadd-140">變更預測的起點和終點</span><span class="sxs-lookup"><span data-stu-id="0aadd-140">Change the start and end points of the predictions</span></span>  
  
1.  <span data-ttu-id="0aadd-141">在預測查詢產生器中，按一下 [**查詢**] 以切換至 [DMX 視圖]。</span><span class="sxs-lookup"><span data-stu-id="0aadd-141">In Prediction Query Builder, click **Query** to switch to DMX view.</span></span>  
  
2.  <span data-ttu-id="0aadd-142">找出包含 PredictTimeSeries 函數的 DMX 陳述式，加以變更，如下所示：</span><span class="sxs-lookup"><span data-stu-id="0aadd-142">Locate the DMX statement that contains the PredictTimeSeries function and change it as follows:</span></span>  
  
     `PredictTimeSeries([Forecasting 12].[Quantity],4,6,EXTEND_MODEL_CASES)`  
  
3.  <span data-ttu-id="0aadd-143">按一下 [**結果**]，並查看結果。</span><span class="sxs-lookup"><span data-stu-id="0aadd-143">Click **Results** and review the results.</span></span>  
  
     <span data-ttu-id="0aadd-144">現在預測會在 10 月開始 (從原始資料結尾算起的第四個時間配量) 並在 12 月結束 (從原始資料結尾算起的第六個時間配量)。</span><span class="sxs-lookup"><span data-stu-id="0aadd-144">Now the predictions begin at October (the fourth time slice, counting from the end of the original data) and end at December (the sixth time slice, counting from the end of the original data).</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="0aadd-145">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="0aadd-145">Next Task in Lesson</span></span>  
 [<span data-ttu-id="0aadd-146">使用取代資料 &#40;中繼資料採礦教學課程的時間序列預測&#41;</span><span class="sxs-lookup"><span data-stu-id="0aadd-146">Time Series Predictions using Replacement Data &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/time-series-predictions-replacement-data-intermediate-data-mining.md)  
  
## <a name="see-also"></a><span data-ttu-id="0aadd-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0aadd-147">See Also</span></span>  
 <span data-ttu-id="0aadd-148">[Microsoft 時間序列演算法技術參考](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span><span class="sxs-lookup"><span data-stu-id="0aadd-148">[Microsoft Time Series Algorithm Technical Reference](../../2014/analysis-services/data-mining/microsoft-time-series-algorithm-technical-reference.md) </span></span>  
 [<span data-ttu-id="0aadd-149">時間序列模型的採礦模型內容 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="0aadd-149">Mining Model Content for Time Series Models &#40;Analysis Services - Data Mining&#41;</span></span>](../../2014/analysis-services/data-mining/mining-model-content-for-time-series-models-analysis-services-data-mining.md)  
  
  
