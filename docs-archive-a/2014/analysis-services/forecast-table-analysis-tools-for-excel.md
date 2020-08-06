---
title: " (適用于 Excel) 的資料表分析工具進行預測 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- forecasting
- mining model, time series
- time series [data mining]
ms.assetid: 22bb0b5e-78f5-484e-883d-2b5985a12749
author: minewiskan
ms.author: owend
ms.openlocfilehash: abca22dbcb9ae6426e839f92e391a658f5029e31
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592978"
---
# <a name="forecast-table-analysis-tools-for-excel"></a><span data-ttu-id="7dc75-102">預測 (適用於 Excel 的資料表分析工具)</span><span class="sxs-lookup"><span data-stu-id="7dc75-102">Forecast (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="7dc75-103">![資料表分析工具功能區中的預測按鈕](media/tat-forecast.gif "資料表分析工具功能區中的預測按鈕")</span><span class="sxs-lookup"><span data-stu-id="7dc75-103">![Forecast button in Table Analysis tools ribbon](media/tat-forecast.gif "Forecast button in Table Analysis tools ribbon")</span></span>  
  
 <span data-ttu-id="7dc75-104">「**預測**」工具可協助您根據 Excel 資料表或其他資料來源中的資料進行預測，並選擇性地查看與每個預測值相關聯的機率。</span><span class="sxs-lookup"><span data-stu-id="7dc75-104">The **Forecast** tool helps you make predictions based on data in an Excel data table or other data source, and optionally view the probabilities associated with each predicted value.</span></span> <span data-ttu-id="7dc75-105">例如，如果資料包含日期資料行以及顯示當月每日總銷售額的資料行，您就可以預測未來日期的銷售。</span><span class="sxs-lookup"><span data-stu-id="7dc75-105">For example, if your data contains a date column and a column that shows total sales for each day of the month, you could predict the sales for future days.</span></span> <span data-ttu-id="7dc75-106">您也可以指定所要做出的預測數目。</span><span class="sxs-lookup"><span data-stu-id="7dc75-106">You can also specify the number of predictions to make.</span></span> <span data-ttu-id="7dc75-107">例如，您可以預測五天或 30。</span><span class="sxs-lookup"><span data-stu-id="7dc75-107">For example, you can predict five days, or thirty.</span></span>  
  
 <span data-ttu-id="7dc75-108">當此工具完成時，它會將新預測附加至來源資料表結尾，並且反白顯示新值。</span><span class="sxs-lookup"><span data-stu-id="7dc75-108">When the tool completes, it appends the new predictions to the end of the source data table, and highlights the new values.</span></span> <span data-ttu-id="7dc75-109">新的時間序列值不會附加，這可讓您先檢閱預測。</span><span class="sxs-lookup"><span data-stu-id="7dc75-109">New time series values are not appended; this allows you to review the predictions first.</span></span>  
  
 <span data-ttu-id="7dc75-110">此工具也會建立名為 [**預測報表**] 的新工作表。</span><span class="sxs-lookup"><span data-stu-id="7dc75-110">The tool also creates a new worksheet named **Forecasting Report**.</span></span> <span data-ttu-id="7dc75-111">這個工作表會報告精靈是否已成功建立預測。</span><span class="sxs-lookup"><span data-stu-id="7dc75-111">This worksheet reports whether the wizard successfully created a prediction.</span></span> <span data-ttu-id="7dc75-112">新工作表也包含顯示歷史趨勢的折線圖。</span><span class="sxs-lookup"><span data-stu-id="7dc75-112">The new worksheet also contains a line graph that shows the historical trends.</span></span>  
  
 <span data-ttu-id="7dc75-113">當您延伸時間序列以包含新預測時，預測值會加入折線圖。</span><span class="sxs-lookup"><span data-stu-id="7dc75-113">When you extend the time series to include the new predictions, the predicted values are added to the line graph.</span></span> <span data-ttu-id="7dc75-114">記錄值以實線表示，預測則以虛線表示。</span><span class="sxs-lookup"><span data-stu-id="7dc75-114">The historical values are shown as a solid line and the predictions are shown as a dotted line.</span></span>  
  
## <a name="using-the-forecast-tool"></a><span data-ttu-id="7dc75-115">使用預測工具</span><span class="sxs-lookup"><span data-stu-id="7dc75-115">Using the Forecast Tool</span></span>  
  
1.  <span data-ttu-id="7dc75-116">開啟包含可預測數值資料的 Excel 資料表。</span><span class="sxs-lookup"><span data-stu-id="7dc75-116">Open an Excel table that contains predictable numeric data.</span></span>  
  
2.  <span data-ttu-id="7dc75-117">按一下 [**分析**] 索引標籤上的 [**預測**]。</span><span class="sxs-lookup"><span data-stu-id="7dc75-117">Click **Forecast** on the **Analyze** tab.</span></span>  
  
3.  <span data-ttu-id="7dc75-118">指定要預測的資料行。</span><span class="sxs-lookup"><span data-stu-id="7dc75-118">Specify the columns to forecast.</span></span> <span data-ttu-id="7dc75-119">此工具會自動選取具有可預測資料類型的資料行（也就是連續數值資料）。</span><span class="sxs-lookup"><span data-stu-id="7dc75-119">The tool automatically selects columns in the data that have a predictable data type-that is, continuous numeric data.</span></span> <span data-ttu-id="7dc75-120">如果資料行包含許多 null 或零值，此工具便可能不會選取一些具有連續數值資料的資料行，因為資料遺失可能會影響結果。</span><span class="sxs-lookup"><span data-stu-id="7dc75-120">The tool might not select some columns that have continuous numeric data if the columns contain many null or zero values, because the missing data might affect the results.</span></span> <span data-ttu-id="7dc75-121">如果發生這種情況，您可以使用 [重定標籤[&#40;SQL Server 資料採礦增益集&#41;](relabel-sql-server-data-mining-add-ins.md)工具來修正資料。</span><span class="sxs-lookup"><span data-stu-id="7dc75-121">If this happens, you can fix the data by using the [Relabel &#40;SQL Server Data Mining Add-ins&#41;](relabel-sql-server-data-mining-add-ins.md) tool.</span></span>  
  
4.  <span data-ttu-id="7dc75-122">指定包含日期、時間或其他序列識別碼的資料行。</span><span class="sxs-lookup"><span data-stu-id="7dc75-122">Specify the column that contains the date, time, or other series identifier.</span></span> <span data-ttu-id="7dc75-123">如果您選取選項 **\<no time stamp>** ，此工具會根據來源資料中的資料列順序來建立數列。</span><span class="sxs-lookup"><span data-stu-id="7dc75-123">If you select the option **\<no time stamp>** the tool will create a series based on the sequence of rows in the source data.</span></span>  
  
5.  <span data-ttu-id="7dc75-124">指定要做出的預測數目。</span><span class="sxs-lookup"><span data-stu-id="7dc75-124">Specify the number of predictions to make.</span></span>  
  
6.  <span data-ttu-id="7dc75-125">您可以選擇性地提供有關您預期資料是要每週、每月或依其他間隔重複之演算法的提示。</span><span class="sxs-lookup"><span data-stu-id="7dc75-125">Optionally, provide a hint to the algorithm about whether you expect your data to repeat weekly, monthly, or in other periods.</span></span> <span data-ttu-id="7dc75-126">如果您的資料不符合任何給定的模式，或如果您不知道任何模式，請選取 **\<detect automatically>** 讓工具尋找重複的時間週期。</span><span class="sxs-lookup"><span data-stu-id="7dc75-126">If your data does not fit any of the given patterns, or if you are unaware of any patterns, select **\<detect automatically>** to have the tool find the repeating time periods.</span></span>  
  
7.  <span data-ttu-id="7dc75-127">精靈會將預測加入來源資料表，並且在新的工作表中建立預測報表。</span><span class="sxs-lookup"><span data-stu-id="7dc75-127">The wizard adds the predictions to the source table, and creates a forecasting report in a new worksheet.</span></span>  
  
8.  <span data-ttu-id="7dc75-128">若要將新值加入預測圖形，請延伸時間序列以包含預測值。</span><span class="sxs-lookup"><span data-stu-id="7dc75-128">To add the new values to the prediction graph, extend the time series to include the forecasted values.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="7dc75-129">需求</span><span class="sxs-lookup"><span data-stu-id="7dc75-129">Requirements</span></span>  
 <span data-ttu-id="7dc75-130">您預測的資料行必須包含連續數值資料，例如貨幣或其他數字。</span><span class="sxs-lookup"><span data-stu-id="7dc75-130">The columns that you predict must contain continuous numeric data, such as currency or other numbers.</span></span>  
  
 <span data-ttu-id="7dc75-131">可能的話，您的資料也應包含有時間或日期序列的資料行。</span><span class="sxs-lookup"><span data-stu-id="7dc75-131">If possible, your data should also include a column that contains a series of times or dates.</span></span> <span data-ttu-id="7dc75-132">您可以使用數位序列 (1、2、3 .... ) ，而不是日期和時間資料。</span><span class="sxs-lookup"><span data-stu-id="7dc75-132">You can use a numeric series (1,2,3....) instead of date and time data.</span></span> <span data-ttu-id="7dc75-133">不過，序列資料行中的值必須是唯一的。</span><span class="sxs-lookup"><span data-stu-id="7dc75-133">However, values in the series column must be unique.</span></span> <span data-ttu-id="7dc75-134">如果**預測**工具在數列資料行中找到重複的值，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="7dc75-134">An error occurs if the **Forecast** tool finds duplicate values in the series column.</span></span>  
  
 <span data-ttu-id="7dc75-135">您無法使用 [**預測**] 工具來預測日期。</span><span class="sxs-lookup"><span data-stu-id="7dc75-135">You cannot predict a date by using the **Forecast** tool.</span></span> <span data-ttu-id="7dc75-136">雖然可能不會發生錯誤，但這個演算法不是設計成使用日期做為可預測值。</span><span class="sxs-lookup"><span data-stu-id="7dc75-136">Although an error might not occur, this algorithm is not designed to use dates as predictable values.</span></span>  
  
### <a name="understanding-time-stamps"></a><span data-ttu-id="7dc75-137">了解時間戳記</span><span class="sxs-lookup"><span data-stu-id="7dc75-137">Understanding Time Stamps</span></span>  
 <span data-ttu-id="7dc75-138">您必須識別要當做*時間戳記*使用的資料行。</span><span class="sxs-lookup"><span data-stu-id="7dc75-138">You must identify a column to use as a *time stamp*.</span></span> <span data-ttu-id="7dc75-139">此時間戳記有兩個目的。</span><span class="sxs-lookup"><span data-stu-id="7dc75-139">The time stamp serves two purposes.</span></span> <span data-ttu-id="7dc75-140">第一個目的是要唯一識別時間序列中的值。</span><span class="sxs-lookup"><span data-stu-id="7dc75-140">First, it uniquely identifies a value in a time series.</span></span> <span data-ttu-id="7dc75-141">例如，如果您每天追蹤銷售，每一天只應該有一筆銷售值。</span><span class="sxs-lookup"><span data-stu-id="7dc75-141">For example, if you are tracking sales on a daily basis, you should have only one sales value for each day.</span></span> <span data-ttu-id="7dc75-142">日曆日期可以當做時間戳記使用。</span><span class="sxs-lookup"><span data-stu-id="7dc75-142">The calendar date can be used as the time stamp.</span></span> <span data-ttu-id="7dc75-143">第二，時間戳記資料行表示做出預測的單位。</span><span class="sxs-lookup"><span data-stu-id="7dc75-143">Second, the time stamp column indicates the unit for making predictions.</span></span> <span data-ttu-id="7dc75-144">如果您要追蹤每天的銷售，您的預測也會使用天的單位。</span><span class="sxs-lookup"><span data-stu-id="7dc75-144">If you are tracking daily sales, your predictions will also be in units of days.</span></span>  
  
 <span data-ttu-id="7dc75-145">如果您的資料沒有包含日期或時間資料行，此工具便會自動建立名為 _RowIndex 的暫時性序列索引鍵。</span><span class="sxs-lookup"><span data-stu-id="7dc75-145">If your data does not include a date or time column, the tool will automatically create a temporary series key, named _RowIndex.</span></span> <span data-ttu-id="7dc75-146">該索引鍵將根據資料集中的資料列順序而定。</span><span class="sxs-lookup"><span data-stu-id="7dc75-146">The key will be based on the order of the rows in the data set.</span></span>  
  
 <span data-ttu-id="7dc75-147">當您指定預測的數目時，您會輸入指出步驟數目的整數。</span><span class="sxs-lookup"><span data-stu-id="7dc75-147">When you specify the number of predictions, you enter a whole number that indicates the number of steps.</span></span> <span data-ttu-id="7dc75-148">這些步驟的單位取決於資料之時間序列和資料數列中所使用的單位。</span><span class="sxs-lookup"><span data-stu-id="7dc75-148">The units for these steps depend on the units used in the time and date series in your data.</span></span> <span data-ttu-id="7dc75-149">如果您的資料會依據月份列出銷售結果，預測將會是月份的數列。</span><span class="sxs-lookup"><span data-stu-id="7dc75-149">If your data lists sales results by the month, the prediction will be for a series of months.</span></span> <span data-ttu-id="7dc75-150">除非您變更來源資料，否則將無法變更時間的單位。</span><span class="sxs-lookup"><span data-stu-id="7dc75-150">You cannot change the units of time unless you change the source data.</span></span>  
  
### <a name="understanding-periodicity"></a><span data-ttu-id="7dc75-151">了解週期性</span><span class="sxs-lookup"><span data-stu-id="7dc75-151">Understanding Periodicity</span></span>  
 <span data-ttu-id="7dc75-152">預測是以一段時間的重複模式為根據；</span><span class="sxs-lookup"><span data-stu-id="7dc75-152">A forecast is based on repeating patterns over a period of time.</span></span> <span data-ttu-id="7dc75-153">因此，Microsoft 時間序列演算法會執行計算，以判斷具有最強模式的期間。</span><span class="sxs-lookup"><span data-stu-id="7dc75-153">Therefore, the Microsoft Time Series algorithm performs calculations to determine the time periods that have the strongest patterns.</span></span> <span data-ttu-id="7dc75-154">*週期*指的是這些時間週期。</span><span class="sxs-lookup"><span data-stu-id="7dc75-154">*Periodicity* refers to these time periods.</span></span>  
  
 <span data-ttu-id="7dc75-155">時間序列可包含許多可能的模式。</span><span class="sxs-lookup"><span data-stu-id="7dc75-155">A time series can contain many potential patterns.</span></span> <span data-ttu-id="7dc75-156">如果您很確定您的資料有包含某個模式，您或許能夠提供提示給演算法來提升預測的品質。</span><span class="sxs-lookup"><span data-stu-id="7dc75-156">If you are certain that your data contains a certain pattern, you may be able to improve the quality of prediction by providing a hint to the algorithm.</span></span>  
  
 <span data-ttu-id="7dc75-157">例如，如果您預期您的資料每週會重複一次，您可以選取 [每週] 來指示此演算法應該尋找每週的模式。</span><span class="sxs-lookup"><span data-stu-id="7dc75-157">For example, if you expect that your data repeats on a weekly basis, you can select Weekly to indicate that the algorithm should look for weekly patterns.</span></span> <span data-ttu-id="7dc75-158">但是，如果未找到任何強的模式，此演算法將會忽略此提示。</span><span class="sxs-lookup"><span data-stu-id="7dc75-158">However, if no strong weekly patterns are found, the algorithm will ignore the hint.</span></span>  
  
## <a name="understanding-the-forecasting-report"></a><span data-ttu-id="7dc75-159">了解預測報表</span><span class="sxs-lookup"><span data-stu-id="7dc75-159">Understanding the Forecasting Report</span></span>  
 <span data-ttu-id="7dc75-160">在這個圖形中，來自資料表的記錄值會顯示為深色線條，</span><span class="sxs-lookup"><span data-stu-id="7dc75-160">In this graph, the historical values from your data table appear as a dark line.</span></span> <span data-ttu-id="7dc75-161">預測值則顯示為虛線。</span><span class="sxs-lookup"><span data-stu-id="7dc75-161">The predicted values appear as dotted lines.</span></span> <span data-ttu-id="7dc75-162">您可以按一下線條上的某一點來查看預測值。</span><span class="sxs-lookup"><span data-stu-id="7dc75-162">You can click a point on the line to see the forecasted value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7dc75-163">如果您在圖表中看不到預測值的時間軸上的標籤，請開啟包含預測值的工作表，然後使用 Excel 中的**Fill，Series**函數來擴充時間戳記資料行，以包含預測的值。</span><span class="sxs-lookup"><span data-stu-id="7dc75-163">If you do not see labels on the time axis for the predicted values in the graph, open the worksheet that contains the predicted values, and use the **Fill, Series** function in Excel to extend the time stamp column to include the predicted values.</span></span>  
  
 <span data-ttu-id="7dc75-164">在某些狀況下，預測的時間配量可能不如要求得多。</span><span class="sxs-lookup"><span data-stu-id="7dc75-164">In some cases, the forecast may not have as many time slices as requested.</span></span> <span data-ttu-id="7dc75-165">這通常表示資料不足，無法讓演算法預測這樣遙遠的未來。</span><span class="sxs-lookup"><span data-stu-id="7dc75-165">This usually means that data was insufficient to allow the algorithm to forecast that far into the future.</span></span> <span data-ttu-id="7dc75-166">[**預測**] 工具只會做出符合最小機率臨界值的預測。</span><span class="sxs-lookup"><span data-stu-id="7dc75-166">The **Forecast** tool will only make predictions that meet a minimum probability threshold.</span></span>  
  
## <a name="related-tools"></a><span data-ttu-id="7dc75-167">相關工具</span><span class="sxs-lookup"><span data-stu-id="7dc75-167">Related Tools</span></span>  
 <span data-ttu-id="7dc75-168">適用於 Excel 的資料採礦用戶端是獨立的增益集，它提供更多進階資料採礦功能，也包含預測用的精靈。</span><span class="sxs-lookup"><span data-stu-id="7dc75-168">The Data Mining Client for Excel, which is a separate add-in that provides more advanced data mining functionality, also contains a wizard for forecasting.</span></span>  
  
 <span data-ttu-id="7dc75-169">[適用于 Excel 的資料表分析工具]) 中 (的 [**預測**] 工具，以及適用于 Excel 的資料採礦用戶端 (的 [**預測**]) 使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 時間序列演算法。</span><span class="sxs-lookup"><span data-stu-id="7dc75-169">Both the **Forecast** tool (in the Table Analysis Tools for Excel) and the **Forecast** wizard (in the Data Mining Client for Excel) use the [!INCLUDE[msCoName](../includes/msconame-md.md)] Time Series algorithm.</span></span>  
  
-   <span data-ttu-id="7dc75-170">**預測**工具較容易使用，因為它會自動將演算法設定為使用最適合您資料的設定。</span><span class="sxs-lookup"><span data-stu-id="7dc75-170">The **Forecast** tool is easier to use because it automatically configures the algorithm to use the settings that are best for your data.</span></span>  
  
-   <span data-ttu-id="7dc75-171">適用于 Excel 的資料採礦用戶端中的 [**預測**] wizard 提供您自訂參數的能力。</span><span class="sxs-lookup"><span data-stu-id="7dc75-171">The **Forecast** wizard in the Data Mining Client for Excel provides you with the ability to customize the parameters.</span></span>  
  
 <span data-ttu-id="7dc75-172">如需有關 [**預測**] wizard 的詳細資訊，請參閱[&#40;適用于 Excel 的資料採礦增益集&#41;的預測 wizard ](forecast-wizard-data-mining-add-ins-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="7dc75-172">For more information about the **Forecast** wizard, see [Forecast Wizard &#40;Data Mining Add-ins for Excel&#41;](forecast-wizard-data-mining-add-ins-for-excel.md).</span></span> <span data-ttu-id="7dc75-173">如需有關預測使用之演算法的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 線上叢書》中的＜Microsoft 時間序列演算法＞主題。</span><span class="sxs-lookup"><span data-stu-id="7dc75-173">For more information about the algorithm used for forecasting, see the topic "Microsoft Time Series Algorithm" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dc75-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dc75-174">See Also</span></span>  
 [<span data-ttu-id="7dc75-175">適用於 Excel 的資料表分析工具</span><span class="sxs-lookup"><span data-stu-id="7dc75-175">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
  
