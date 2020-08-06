---
title: 第3課：處理時間序列結構和模型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 16e27b57-eae1-47a7-a02c-47b6ed487d87
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 493d27c9836eb765c655eba5bbb004e4d48cde40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702201"
---
# <a name="lesson-3-processing-the-time-series-structure-and-models"></a><span data-ttu-id="733f6-102">第 3 課：處理時間序列結構和模型</span><span class="sxs-lookup"><span data-stu-id="733f6-102">Lesson 3: Processing the Time Series Structure and Models</span></span>
  <span data-ttu-id="733f6-103">在這一課，您將使用[INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)語句，來處理您所建立的時間序列採礦結構和採礦模型。</span><span class="sxs-lookup"><span data-stu-id="733f6-103">In this lesson, you will use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement to process the time series mining structures and mining models that you created.</span></span>  
  
 <span data-ttu-id="733f6-104">當您處理採礦結構時，[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 會讀取來源資料並建立支援採礦模型的結構。</span><span class="sxs-lookup"><span data-stu-id="733f6-104">When you process a mining structure, [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] reads the source data and builds the structures that support mining models.</span></span> <span data-ttu-id="733f6-105">當您首次建立採礦模型和結構時，一定要進行處理。</span><span class="sxs-lookup"><span data-stu-id="733f6-105">You always have to process a mining model and structure when you first create it.</span></span> <span data-ttu-id="733f6-106">如果您在使用 INSERT INTO 時指定採礦結構，陳述式會處理採礦結構及其所有相關聯的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="733f6-106">If you specify the mining structure when using INSERT INTO, the statement processes the mining structure and all its associated mining models.</span></span>  
  
 <span data-ttu-id="733f6-107">當您將採礦模型加入至已處理的採礦結構中，就可以使用 `INSERT INTO MINING MODEL` 陳述式，以現有的資料只處理新的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="733f6-107">When you add a mining model to a mining structure that has already been processed, you can use the `INSERT INTO MINING MODEL` statement to process just the new mining model by using the existing data.</span></span>  
  
 <span data-ttu-id="733f6-108">如需處理採礦模型的詳細資訊，請參閱[&#40;資料採礦&#41;的處理需求和考慮](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md)。</span><span class="sxs-lookup"><span data-stu-id="733f6-108">For more information about processing mining models, see [Processing Requirements and Considerations &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md).</span></span>  
  
## <a name="insert-into-statement"></a><span data-ttu-id="733f6-109">INSERT INTO 陳述式</span><span class="sxs-lookup"><span data-stu-id="733f6-109">INSERT INTO Statement</span></span>  
 <span data-ttu-id="733f6-110">若要將時間序列的採礦結構及其所有相關聯的採礦模型定型，請使用[INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx)語句。</span><span class="sxs-lookup"><span data-stu-id="733f6-110">In order to train the time series mining structure and all its associated mining models, use the [INSERT INTO &#40;DMX&#41;](/sql/dmx/insert-into-dmx) statement.</span></span> <span data-ttu-id="733f6-111">陳述式中的程式碼可分成下列各部份。</span><span class="sxs-lookup"><span data-stu-id="733f6-111">The code in the statement can be broken into the following parts.</span></span>  
  
-   <span data-ttu-id="733f6-112">識別採礦結構</span><span class="sxs-lookup"><span data-stu-id="733f6-112">Identifying the mining structure</span></span>  
  
-   <span data-ttu-id="733f6-113">列出採礦結構中的資料行</span><span class="sxs-lookup"><span data-stu-id="733f6-113">Listing the columns in the mining structure</span></span>  
  
-   <span data-ttu-id="733f6-114">定義定型資料</span><span class="sxs-lookup"><span data-stu-id="733f6-114">Defining the training data</span></span>  
  
 <span data-ttu-id="733f6-115">下面是 `INSERT INTO` 陳述式的一般範例：</span><span class="sxs-lookup"><span data-stu-id="733f6-115">The following is a generic example of the `INSERT INTO` statement:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
(  
   <mining structure columns>  
)  
OPENQUERY (<source data definition>)  
```  
  
 <span data-ttu-id="733f6-116">程式碼的第一行識別您將定型的採礦結構：</span><span class="sxs-lookup"><span data-stu-id="733f6-116">The first line of the code identifies the mining structure that you will train:</span></span>  
  
```  
INSERT INTO MINING STRUCTURE [<mining structure name>]  
```  
  
 <span data-ttu-id="733f6-117">接下來幾行的程式碼指定採礦結構定義的資料行。</span><span class="sxs-lookup"><span data-stu-id="733f6-117">The next lines of the code specify the columns that are defined by the mining structure.</span></span> <span data-ttu-id="733f6-118">您必須列出採礦結構的每一個資料行，且每一個資料行必須對應到來源查詢資料內包含的資料行。</span><span class="sxs-lookup"><span data-stu-id="733f6-118">You must list each column in the mining structure, and each column must map to a column contained within the source query data.</span></span>  
  
```  
(  
   <mining structure columns>  
)  
```  
  
 <span data-ttu-id="733f6-119">程式碼的最後幾行定義將用於定型採礦結構的資料。</span><span class="sxs-lookup"><span data-stu-id="733f6-119">The final lines of the code define the data that will be used to train the mining structure.</span></span>  
  
```  
OPENQUERY (<source data definition>)  
```  
  
 <span data-ttu-id="733f6-120">在這一課，您使用 `OPENQUERY` 來定義來源資料。</span><span class="sxs-lookup"><span data-stu-id="733f6-120">In this lesson, you use `OPENQUERY` to define the source data.</span></span> <span data-ttu-id="733f6-121">如需有關在來源資料上定義查詢之其他方法的詳細資訊，請參閱[&#60;來源資料查詢&#62;](/sql/dmx/source-data-query)。</span><span class="sxs-lookup"><span data-stu-id="733f6-121">For more information about other methods of defining a query on the source data, see [&#60;source data query&#62;](/sql/dmx/source-data-query).</span></span>  
  
## <a name="lesson-tasks"></a><span data-ttu-id="733f6-122">課程工作</span><span class="sxs-lookup"><span data-stu-id="733f6-122">Lesson Tasks</span></span>  
 <span data-ttu-id="733f6-123">您將在這一課執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="733f6-123">You will perform the following task in this lesson:</span></span>  
  
-   <span data-ttu-id="733f6-124">處理採礦結構 Forecasting_MIXED_Structure</span><span class="sxs-lookup"><span data-stu-id="733f6-124">Process the mining structure Forecasting_MIXED_Structure</span></span>  
  
-   <span data-ttu-id="733f6-125">處理 Forecasting_MIXED、Forecasting_ARIMA 和 Forecasting_ARTXP 等相關聯的採礦模型</span><span class="sxs-lookup"><span data-stu-id="733f6-125">Process the related mining models Forecasting_MIXED, Forecasting_ARIMA, and Forecasting_ARTXP</span></span>  
  
## <a name="processing-the-time-series-mining-structure"></a><span data-ttu-id="733f6-126">處理時間序列採礦結構</span><span class="sxs-lookup"><span data-stu-id="733f6-126">Processing the Time Series Mining Structure</span></span>  
  
#### <a name="to-process-the-mining-structure-and-related-mining-models-by-using-insert-into"></a><span data-ttu-id="733f6-127">若要使用 INSERT INTO 來處理採礦結構和相關的採礦模型</span><span class="sxs-lookup"><span data-stu-id="733f6-127">To process the mining structure and related mining models by using INSERT INTO</span></span>  
  
1.  <span data-ttu-id="733f6-128">在**物件總管**中，以滑鼠右鍵按一下的實例 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，指向 [追加**查詢**]，然後按一下 [ **DMX**]。</span><span class="sxs-lookup"><span data-stu-id="733f6-128">In **Object Explorer**, right-click the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], point to **New Query**, and then click **DMX**.</span></span>  
  
     <span data-ttu-id="733f6-129">此時會開啟 [查詢編輯器] 且包含新的空白查詢。</span><span class="sxs-lookup"><span data-stu-id="733f6-129">Query Editor opens and contains a new, blank query.</span></span>  
  
2.  <span data-ttu-id="733f6-130">將 INSERT INTO 陳述式的一般範例複製到空白查詢中。</span><span class="sxs-lookup"><span data-stu-id="733f6-130">Copy the generic example of the INSERT INTO statement into the blank query.</span></span>  
  
3.  <span data-ttu-id="733f6-131">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="733f6-131">Replace the following:</span></span>  
  
    ```  
    [<mining structure>]  
    ```  
  
     <span data-ttu-id="733f6-132">成為：</span><span class="sxs-lookup"><span data-stu-id="733f6-132">with:</span></span>  
  
    ```  
    Forecasting_MIXED_Structure  
    ```  
  
4.  <span data-ttu-id="733f6-133">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="733f6-133">Replace the following:</span></span>  
  
    ```  
    <mining structure columns>  
    ```  
  
     <span data-ttu-id="733f6-134">成為：</span><span class="sxs-lookup"><span data-stu-id="733f6-134">with:</span></span>  
  
    ```  
    [ReportingDate],  
    [ModelRegion]   
    ```  
  
5.  <span data-ttu-id="733f6-135">取代下列項目：</span><span class="sxs-lookup"><span data-stu-id="733f6-135">Replace the following:</span></span>  
  
    ```  
    OPENQUERY(<source data definition>)  
    ```  
  
     <span data-ttu-id="733f6-136">成為：</span><span class="sxs-lookup"><span data-stu-id="733f6-136">with:</span></span>  
  
    ```  
    OPENQUERY([Adventure Works DW 2008R2],'SELECT [ReportingDate], [ModelRegion], [Quantity], [Amount]  
    FROM vTimeSeries ORDER BY [ReportingDate]')  
    ```  
  
     <span data-ttu-id="733f6-137">來源查詢會參考 [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] IntermediateTutorial 範例專案中定義的資料來源。</span><span class="sxs-lookup"><span data-stu-id="733f6-137">The source query references the  [!INCLUDE[ssSampleDBDWobject](../includes/sssampledbdwobject-md.md)] data source defined in the IntermediateTutorial sample project.</span></span> <span data-ttu-id="733f6-138">它使用此資料來源來存取 view vTimeSerie。</span><span class="sxs-lookup"><span data-stu-id="733f6-138">It uses this data source to access the view vTimeSeries.</span></span> <span data-ttu-id="733f6-139">此檢視包含要用於定型採礦模型的來源資料。</span><span class="sxs-lookup"><span data-stu-id="733f6-139">This view contains the source data that will be used to train the mining model.</span></span> <span data-ttu-id="733f6-140">如果您不熟悉此專案或此視圖，請參閱[第2課：建立預測案例 &#40;中繼資料採礦教學課程&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md)。</span><span class="sxs-lookup"><span data-stu-id="733f6-140">If you are not familiar with this project or this views, see[Lesson 2: Building a Forecasting Scenario &#40;Intermediate Data Mining Tutorial&#41;](../../2014/tutorials/lesson-2-building-a-forecasting-scenario-intermediate-data-mining-tutorial.md).</span></span>  
  
     <span data-ttu-id="733f6-141">現在，完整的陳述式應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="733f6-141">The complete statement should now be as follows:</span></span>  
  
    ```  
    INSERT INTO MINING STRUCTURE [Forecasting_MIXED_Structure]  
    (  
       [ReportingDate],[ModelRegion],[Quantity],[Amount])  
    )  
    OPENQUERY(  
    [Adventure Works DW 2008R2],  
    'SELECT [ReportingDate],[ModelRegion],[Quantity],[Amount] FROM vTimeSeries ORDER BY [ReportingDate]'  
    )   
    ```  
  
6.  <span data-ttu-id="733f6-142">**在 [檔案**] 功能表上，按一下 [**將 DMXQuery1 另存為**]。</span><span class="sxs-lookup"><span data-stu-id="733f6-142">On the **File** menu, click **Save DMXQuery1.dmx As**.</span></span>  
  
7.  <span data-ttu-id="733f6-143">在 [**另存**新檔] 對話方塊中，流覽至適當的資料夾，並將檔案命名為 `ProcessForecastingAll.dmx` 。</span><span class="sxs-lookup"><span data-stu-id="733f6-143">In the **Save As** dialog box, browse to the appropriate folder, and name the file `ProcessForecastingAll.dmx`.</span></span>  
  
8.  <span data-ttu-id="733f6-144">在工具列上，按一下 [**執行**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="733f6-144">On the toolbar, click the **Execute** button.</span></span>  
  
 <span data-ttu-id="733f6-145">執行完查詢之後，您可以使用已處理的採礦模型建立預測。</span><span class="sxs-lookup"><span data-stu-id="733f6-145">After the query has finished running, you can create predictions by using the processed mining models.</span></span> <span data-ttu-id="733f6-146">在下一課，您將依據您建立的採礦模型來建立幾個預測。</span><span class="sxs-lookup"><span data-stu-id="733f6-146">In the next lesson, you will create several predictions based on the mining models that you created.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="733f6-147">下一課</span><span class="sxs-lookup"><span data-stu-id="733f6-147">Next Lesson</span></span>  
 [<span data-ttu-id="733f6-148">第 4 課：使用 DMX 建立時間序列預測</span><span class="sxs-lookup"><span data-stu-id="733f6-148">Lesson 4: Creating Time Series Predictions Using DMX</span></span>](../../2014/tutorials/lesson-4-creating-time-series-predictions-using-dmx.md)  
  
## <a name="see-also"></a><span data-ttu-id="733f6-149">另請參閱</span><span class="sxs-lookup"><span data-stu-id="733f6-149">See Also</span></span>  
 <span data-ttu-id="733f6-150">[&#40;資料採礦&#41;的處理需求和考慮](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md) </span><span class="sxs-lookup"><span data-stu-id="733f6-150">[Processing Requirements and Considerations &#40;Data Mining&#41;](../../2014/analysis-services/data-mining/processing-requirements-and-considerations-data-mining.md) </span></span>  
 <span data-ttu-id="733f6-151">[&#60;來源資料查詢&#62;](/sql/dmx/source-data-query) </span><span class="sxs-lookup"><span data-stu-id="733f6-151">[&#60;source data query&#62;](/sql/dmx/source-data-query) </span></span>  
 [<span data-ttu-id="733f6-152">&#40;DMX&#41;的 OPENQUERY</span><span class="sxs-lookup"><span data-stu-id="733f6-152">OPENQUERY &#40;DMX&#41;</span></span>](/sql/dmx/source-data-query-openquery)  
  
  
