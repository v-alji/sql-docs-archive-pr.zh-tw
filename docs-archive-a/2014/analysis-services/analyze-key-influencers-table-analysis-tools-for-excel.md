---
title: 分析 (適用于 Excel) 的資料表分析工具的關鍵影響因素 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- key influencers
- factor analysis
ms.assetid: 54d7b4ce-7b79-407a-985c-aa655ad19280
author: minewiskan
ms.author: owend
ms.openlocfilehash: f60eb5144059b0976d52eec2329f27553132146c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593185"
---
# <a name="analyze-key-influencers-table-analysis-tools-for-excel"></a><span data-ttu-id="f6182-102">分析關鍵影響因數 (適用於 Excel 的資料表分析工具)</span><span class="sxs-lookup"><span data-stu-id="f6182-102">Analyze Key Influencers (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="f6182-103">![功能區中的分析關鍵影響因數按鈕](media/tat-aki.gif "功能區中的分析關鍵影響因數按鈕")</span><span class="sxs-lookup"><span data-stu-id="f6182-103">![Analyze Key Influencers button in ribbon](media/tat-aki.gif "Analyze Key Influencers button in ribbon")</span></span>  
  
 <span data-ttu-id="f6182-104">使用 [**分析關鍵影響**因數] 工具，您可以選擇包含目標結果的資料行，而演算法會判斷哪些因數對結果有最強的影響。</span><span class="sxs-lookup"><span data-stu-id="f6182-104">With the **Analyze Key Influencers** tool, you choose a column that contains a target outcome, and the algorithm determines which factors had the strongest influence on the outcome.</span></span>  
  
 <span data-ttu-id="f6182-105">此工具會建立新的資料表，此資料表會報告與每一個結果有關的因數，並以圖形方式顯示此關聯性的機率。</span><span class="sxs-lookup"><span data-stu-id="f6182-105">The tool creates new data tables that report the factors associated with each outcome and graphically displays the probability of the relationship.</span></span> <span data-ttu-id="f6182-106">您可以依據不同的因數和結果來篩選資料表，以瀏覽更深層的結果。</span><span class="sxs-lookup"><span data-stu-id="f6182-106">You can filter the tables by different factors and outcomes to explore the results in more depth.</span></span>  
  
 <span data-ttu-id="f6182-107">您也可以選取一對可能的結果，並加以比較。</span><span class="sxs-lookup"><span data-stu-id="f6182-107">You can also select a pair of possible outcomes and compare them.</span></span> <span data-ttu-id="f6182-108">例如，您可能會比較不同的消費者群組以判斷可能的決策因數。</span><span class="sxs-lookup"><span data-stu-id="f6182-108">For example, you might compare different groups of consumers to determine possible decision-making factors.</span></span>  
  
## <a name="using-the-analyze-key-influencers-tool"></a><span data-ttu-id="f6182-109">使用分析關鍵影響因數工具</span><span class="sxs-lookup"><span data-stu-id="f6182-109">Using the Analyze Key Influencers Tool</span></span>  
  
1.  <span data-ttu-id="f6182-110">開啟 Excel 資料表。</span><span class="sxs-lookup"><span data-stu-id="f6182-110">Open an Excel data table.</span></span>  
  
2.  <span data-ttu-id="f6182-111">在 [**資料表工具**] 的 [**分析**] 功能區中，按一下 [**分析關鍵影響**因數]。</span><span class="sxs-lookup"><span data-stu-id="f6182-111">In **Table Tools**, on the **Analyze** ribbon, click **Analyze Key Influencers.**</span></span>  
  
3.  <span data-ttu-id="f6182-112">選取要當做分析目標的單一資料行。</span><span class="sxs-lookup"><span data-stu-id="f6182-112">Select the single column that is the target of analysis.</span></span>  
  
4.  <span data-ttu-id="f6182-113">（選擇性）按一下 **[選擇要用於分析的資料行**]。</span><span class="sxs-lookup"><span data-stu-id="f6182-113">Optionally, click **Choose columns to be used for analysis**.</span></span> <span data-ttu-id="f6182-114">在 [**高級資料行選取**] 對話方塊中，選擇最有可能包含相關資料的資料行。</span><span class="sxs-lookup"><span data-stu-id="f6182-114">In the **Advanced Columns Selection** dialog box, choose the columns that are most likely to contain relevant data.</span></span> <span data-ttu-id="f6182-115">若要提升效能和精確度，請取消選取對於模式分析不重要的資料行，如識別碼或名稱。</span><span class="sxs-lookup"><span data-stu-id="f6182-115">To improve performance and accuracy, deselect columns such as ID or name that are unimportant for pattern analysis.</span></span> <span data-ttu-id="f6182-116">按一下 **[確定]** 以關閉 [**高級資料行選取**] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="f6182-116">Click **OK** to close the **Advanced Columns Selection** dialog box.</span></span>  
  
5.  <span data-ttu-id="f6182-117">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="f6182-117">Click **Run**.</span></span>  
  
     <span data-ttu-id="f6182-118">[**分析關鍵影響**因數] 工具會進行資料的分析，以判斷最佳設定，並自動設定所有參數。</span><span class="sxs-lookup"><span data-stu-id="f6182-118">The **Analyze Key Influencers** tool conducts an analysis of the data to determine the optimum settings, and sets all parameters automatically.</span></span>  
  
6.  <span data-ttu-id="f6182-119">如果未偵測到任何模式，此精靈便會建立包含問題描述的新工作表。</span><span class="sxs-lookup"><span data-stu-id="f6182-119">If no patterns were detected, the wizard creates a new worksheet that contains a description of the problem.</span></span>  
  
7.  <span data-ttu-id="f6182-120">如果偵測到模式，此精靈會在新的工作表上建立報表來顯示模式。</span><span class="sxs-lookup"><span data-stu-id="f6182-120">If patterns are detected, the wizard creates a report on a new worksheet that shows the patterns.</span></span> <span data-ttu-id="f6182-121">報表的名稱為\*\*關鍵影響 \<column> \*\*因數。</span><span class="sxs-lookup"><span data-stu-id="f6182-121">The report is named **Key Influencers for \<column>**.</span></span> <span data-ttu-id="f6182-122">您可以自訂此報表，如下列程序所述。</span><span class="sxs-lookup"><span data-stu-id="f6182-122">You can customize the report as described in the following procedure.</span></span>  
  
#### <a name="create-a-custom-report"></a><span data-ttu-id="f6182-123">建立自訂報告</span><span class="sxs-lookup"><span data-stu-id="f6182-123">Create a custom report</span></span>  
  
1.  <span data-ttu-id="f6182-124">在 [**根據關鍵影響**因數的辨識] 對話方塊中，選擇您想要比較的兩個值，方法是從 [**值 1** ] 和 [**值 2** ] 下拉式清單中選取它們。</span><span class="sxs-lookup"><span data-stu-id="f6182-124">In the **Discrimination based on key influencers** dialog box, choose the two values that you want to compare by selecting them from the **Value 1** and **Value 2** dropdown lists.</span></span> <span data-ttu-id="f6182-125">例如，您可能比較買主與非買主。</span><span class="sxs-lookup"><span data-stu-id="f6182-125">For example, you might compare buyers to non-buyers.</span></span>  
  
2.  <span data-ttu-id="f6182-126">按一下 [**加入報表**]。</span><span class="sxs-lookup"><span data-stu-id="f6182-126">Click **Add Report**.</span></span>  
  
     <span data-ttu-id="f6182-127">此精靈會建立新的工作表，並加入每一對關鍵因數比較的資料表。</span><span class="sxs-lookup"><span data-stu-id="f6182-127">The wizard creates a new worksheet and adds a table for each pair of key factor comparisons.</span></span>  
  
3.  <span data-ttu-id="f6182-128">完成比較之後，請按一下 [**關閉**]。</span><span class="sxs-lookup"><span data-stu-id="f6182-128">When you are done making comparisons, click **Close**.</span></span>  
  
## <a name="understanding-the-key-influencers-report"></a><span data-ttu-id="f6182-129">了解關鍵影響因數報表</span><span class="sxs-lookup"><span data-stu-id="f6182-129">Understanding the Key Influencers Report</span></span>  
 <span data-ttu-id="f6182-130">建立資料模型之後，[**分析關鍵影響**因數] 工具會建立可協助您探索和比較關鍵影響因數的報表。</span><span class="sxs-lookup"><span data-stu-id="f6182-130">After the data model has been created, the **Analyze Key Influencers** tool creates reports that help you explore and compare key influencers.</span></span>  
  
-   <span data-ttu-id="f6182-131">左邊的報表是預設產生的報表。</span><span class="sxs-lookup"><span data-stu-id="f6182-131">The report on the left side is the one generated by default.</span></span> <span data-ttu-id="f6182-132">其中會顯示結果資料行的最強預測指標 (相依變數)。</span><span class="sxs-lookup"><span data-stu-id="f6182-132">It shows the strongest predictors of the outcome column (the dependent variable).</span></span>  
  
-   <span data-ttu-id="f6182-133">右邊的報表是選擇性的，您可以藉由比較兩個特定的結果值建立該報表。</span><span class="sxs-lookup"><span data-stu-id="f6182-133">The report on the right side is optional, which you can create by comparing two specific outcome values.</span></span> <span data-ttu-id="f6182-134">這個報表會比較購買者與非購買者。</span><span class="sxs-lookup"><span data-stu-id="f6182-134">This report compares buyers and non-buyers.</span></span>  
  
-   <span data-ttu-id="f6182-135">請注意，針對您建立的每個報表會加入一個新的工作表。</span><span class="sxs-lookup"><span data-stu-id="f6182-135">Note that a new worksheet is added for each report that you create.</span></span> <span data-ttu-id="f6182-136">您可以在資料表建立之後移動資料表；我們會將它們並排放置以進行比較。</span><span class="sxs-lookup"><span data-stu-id="f6182-136">You can move the tables after they are created; we placed them side by side for comparison.</span></span>  
  
 <span data-ttu-id="f6182-137">![DM13](media/dm13-tat-aki-report.gif "DM13")</span><span class="sxs-lookup"><span data-stu-id="f6182-137">![DM13](media/dm13-tat-aki-report.gif "DM13")</span></span>  
  
 <span data-ttu-id="f6182-138">**相對影響**</span><span class="sxs-lookup"><span data-stu-id="f6182-138">**Relative Impact**</span></span>  
 <span data-ttu-id="f6182-139">第一個報表中的陰影垂直線表示此屬性與結果之間關聯的強度。</span><span class="sxs-lookup"><span data-stu-id="f6182-139">The shaded bar in the first report indicates the strength of the association of this attribute with the outcome.</span></span>  
  
 <span data-ttu-id="f6182-140">此垂直線的長度表示此因數造成結果發生的機率；因此，當陰影垂直線越長，就表示關聯性越強。</span><span class="sxs-lookup"><span data-stu-id="f6182-140">The length of the bar indicates the probability that the factor contributes to the outcome; therefore, the longer the shaded bar, the stronger the association.</span></span>  
  
 <span data-ttu-id="f6182-141">**喜好**</span><span class="sxs-lookup"><span data-stu-id="f6182-141">**Favors**</span></span>  
 <span data-ttu-id="f6182-142">在第二個報表中，您比較的目標值會列在兩個資料行中，其中相關因素會依照信心的遞減順序列出。</span><span class="sxs-lookup"><span data-stu-id="f6182-142">In the second report, the target values that you compare are listed in two columns, with the related factors listed in order of descending confidence.</span></span>  
  
-   <span data-ttu-id="f6182-143">**藍色**列會顯示影響結果的屬性「否」 (= 並未) 購買。</span><span class="sxs-lookup"><span data-stu-id="f6182-143">The **blue** bar shows attributes contributing to the outcome, "No" (=did not purchase).</span></span>  
  
-   <span data-ttu-id="f6182-144">**紅色**橫條會顯示影響結果的屬性「是」 (= 購買自行車) 。</span><span class="sxs-lookup"><span data-stu-id="f6182-144">The **red** bar shows attributes contributing to the outcome, "Yes" (=purchased a bike).</span></span>  
  
 <span data-ttu-id="f6182-145">陰影垂直線會使用任意色彩。</span><span class="sxs-lookup"><span data-stu-id="f6182-145">The colors in the shading bar are arbitrary.</span></span> <span data-ttu-id="f6182-146">您可以透過在 Excel 中設定資料表設計的選項變更這些色彩。</span><span class="sxs-lookup"><span data-stu-id="f6182-146">You can change these colors by setting the options for table design in Excel.</span></span>  
  
 <span data-ttu-id="f6182-147">在比較兩個值的報表中，第二份報表會根據對目標值的影響數量來排名關鍵影響因數。</span><span class="sxs-lookup"><span data-stu-id="f6182-147">In a report that contrasts two values, the second report ranks the key influencers by the amount of impact on the target values.</span></span>  
  
 <span data-ttu-id="f6182-148">由於所有圖表都是以 Excel 資料表為基礎，因此您可以篩選及排序，以強調特定因數或結果。</span><span class="sxs-lookup"><span data-stu-id="f6182-148">Because all the charts are based on Excel tables, you can filter and sort to focus on specific factors or outcomes.</span></span>  
  
## <a name="more-about-the-analyze-key-influencers-tool"></a><span data-ttu-id="f6182-149">進一步了解分析關鍵影響因數工具</span><span class="sxs-lookup"><span data-stu-id="f6182-149">More About the Analyze Key Influencers Tool</span></span>  
 <span data-ttu-id="f6182-150">當 [**分析關鍵影響**因數] 工具分析您的資料時，它會執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="f6182-150">When the **Analyze Key Influencers** tool analyzes your data, it does the following:</span></span>  
  
-   <span data-ttu-id="f6182-151">建立資料結構來儲存與資料分佈有關的重要資訊。</span><span class="sxs-lookup"><span data-stu-id="f6182-151">Creates a data structure that stores key information about the distribution of your data.</span></span>  
  
-   <span data-ttu-id="f6182-152">使用 Microsoft 貝氏機率分類演算法來建立模型。</span><span class="sxs-lookup"><span data-stu-id="f6182-152">Creates a model using the Microsoft Naïve Bayes algorithm.</span></span>  
  
-   <span data-ttu-id="f6182-153">建立將每個資料行的資料與所指定結果產生關聯的預測。</span><span class="sxs-lookup"><span data-stu-id="f6182-153">Creates predictions that correlates each column of data with the specified outcome.</span></span>  
  
-   <span data-ttu-id="f6182-154">使用每個預測的信心分數識別產生目標結果的最具影響力因數。</span><span class="sxs-lookup"><span data-stu-id="f6182-154">Uses the confidence score for each of the predictions to identify the factors that are the most influential in producing the targeted outcome.</span></span>  
  
-   <span data-ttu-id="f6182-155">建立報表，描述依信心分數排序的關鍵影響因數。</span><span class="sxs-lookup"><span data-stu-id="f6182-155">Creates a report describing the key influencers, ordered by confidence scores.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="f6182-156">需求</span><span class="sxs-lookup"><span data-stu-id="f6182-156">Requirements</span></span>  
 <span data-ttu-id="f6182-157">如果目標資料行包含連續的數值，此工具會自動將這些數值分割成若干群組，</span><span class="sxs-lookup"><span data-stu-id="f6182-157">If the target column contains continuous numeric values, the tool automatically segments the numeric values into groups.</span></span> <span data-ttu-id="f6182-158">這些群組代表具有類似特性之案例的群集。</span><span class="sxs-lookup"><span data-stu-id="f6182-158">These groupings represent clusters of cases that have similar characteristics.</span></span> <span data-ttu-id="f6182-159">但是，數值可能會分成若干使用者易記的群組。</span><span class="sxs-lookup"><span data-stu-id="f6182-159">However, numeric values might not be divided into user-friendly groups.</span></span> <span data-ttu-id="f6182-160">例如，報表可能包含例如 " \< 12.85701" 的群組，而報表使用者通常會想要查看使用整數的分組，例如10-19、20-29 等等。</span><span class="sxs-lookup"><span data-stu-id="f6182-160">For example, the report might contain a grouping such as "\<12.85701", whereas report users typically like to see groupings that use whole numbers, such as 10-19, 20-29, and so on.</span></span>  
  
 <span data-ttu-id="f6182-161">如果您想要以不同的方式來分組數值資料，您必須在建立分析之前，先以您想要的方式分割資料。</span><span class="sxs-lookup"><span data-stu-id="f6182-161">If you want to group numeric data in a different way, you must segment the data the way you want before creating the analysis.</span></span> <span data-ttu-id="f6182-162">例如，您可以使用 [適用于 Excel 的資料採礦用戶端] 中[的 [重定](relabel-sql-server-data-mining-add-ins.md)標籤] 工具，在不同的資料行中建立新的群組標籤，然後只在分析中使用該新資料行。</span><span class="sxs-lookup"><span data-stu-id="f6182-162">For example, you can use the [Relabel](relabel-sql-server-data-mining-add-ins.md) tool in the Data Mining Client for Excel to create a new grouping label in a separate column, and then use only that new column in analysis.</span></span>  
  
### <a name="related-tools"></a><span data-ttu-id="f6182-163">相關工具</span><span class="sxs-lookup"><span data-stu-id="f6182-163">Related Tools</span></span>  
 <span data-ttu-id="f6182-164">**資料採礦**功能區提供更多的先進工具，包括自訂資料採礦模型的能力</span><span class="sxs-lookup"><span data-stu-id="f6182-164">The **Data Mining** ribbon provides more advanced tools, including the ability to customize data mining models</span></span>  
  
 <span data-ttu-id="f6182-165">如果您使用 [**分析關鍵影響**因數] 工具來儲存模型，您可以使用資料採礦用戶端流覽模型，並更詳細地探索關聯性。</span><span class="sxs-lookup"><span data-stu-id="f6182-165">If you save your model by using the **Analyze Key Influencers** tool, you can use the Data Mining Client to browse the model and explore relationships in more detail.</span></span> <span data-ttu-id="f6182-166">如需詳細資訊，請參閱[在 Excel 中流覽模型 &#40;SQL Server 資料採礦增益集&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="f6182-166">For information, see [Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;](browsing-models-in-excel-sql-server-data-mining-add-ins.md).</span></span> <span data-ttu-id="f6182-167">您也可以使用 Microsoft Office Visio 來建立圖表，以群集或相依性網路的形式顯示關聯性。</span><span class="sxs-lookup"><span data-stu-id="f6182-167">You can also use Microsoft Office Visio to create charts and diagrams that display the relationships as cluster or as dependency networks.</span></span> <span data-ttu-id="f6182-168">如需詳細資訊，請參閱針對[Visio 資料採礦圖表進行疑難排解 &#40;SQL Server 資料採礦增益集&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md)。</span><span class="sxs-lookup"><span data-stu-id="f6182-168">For more information, see [Troubleshooting Visio Data Mining Diagrams &#40;SQL Server Data Mining Add-ins&#41;](troubleshooting-visio-data-mining-diagrams-sql-server-data-mining-add-ins.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f6182-169">當您關閉工作表或結束與 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 伺服器的連接時，使用資料表分析工具所建立的模型會被刪除。</span><span class="sxs-lookup"><span data-stu-id="f6182-169">The models that are created when you use the Table Analysis Tools are deleted when you close your worksheet or terminate the connection with the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] server.</span></span> <span data-ttu-id="f6182-170">因此，只能在連接保持開啟時瀏覽模型。</span><span class="sxs-lookup"><span data-stu-id="f6182-170">Therefore, you can only browse the models as long as the connection remains open.</span></span> <span data-ttu-id="f6182-171">如果您關閉連接或關閉工作表，就無法在 Visio 中轉譯模型。</span><span class="sxs-lookup"><span data-stu-id="f6182-171">You cannot render the models in Visio if you close the connection or close the worksheet.</span></span>  
  
 <span data-ttu-id="f6182-172">如需「**分析關鍵影響**因數」工具所使用之演算法的詳細資訊，請參閱 SQL Server 線上叢書中的「Microsoft 簡單的貝氏機率分類演算法」。</span><span class="sxs-lookup"><span data-stu-id="f6182-172">For more information about the algorithm used by the **Analyze Key Influencers** tool, see "Microsoft Naïve Bayes Algorithm" in SQL Server Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6182-173">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f6182-173">See Also</span></span>  
 <span data-ttu-id="f6182-174">[適用于 Excel 的資料表分析工具](table-analysis-tools-for-excel.md) </span><span class="sxs-lookup"><span data-stu-id="f6182-174">[Table Analysis Tools for Excel](table-analysis-tools-for-excel.md) </span></span>  
 [<span data-ttu-id="f6182-175">建立資料採礦模型</span><span class="sxs-lookup"><span data-stu-id="f6182-175">Creating a Data Mining Model</span></span>](creating-a-data-mining-model.md)  
  
  
