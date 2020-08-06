---
title: 反白顯示 (適用于 Excel) 的資料表分析工具的例外狀況 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- Table Analysis tools
- highlight exceptions
ms.assetid: d90a12f8-7bc3-4fdb-95a1-7c89058f0d9a
author: minewiskan
ms.author: owend
ms.openlocfilehash: 97e8197fc76f431cf9740c5c6fbd7ac44d8204a5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707970"
---
# <a name="highlight-exceptions-table-analysis-tools-for-excel"></a><span data-ttu-id="59037-102">反白顯示例外狀況 (適用於 Excel 的資料表分析工具)</span><span class="sxs-lookup"><span data-stu-id="59037-102">Highlight Exceptions (Table Analysis Tools for Excel)</span></span>
  <span data-ttu-id="59037-103">![功能區中的反白顯示例外狀況按鈕](media/tat-highlightex.gif "功能區中的反白顯示例外狀況按鈕")</span><span class="sxs-lookup"><span data-stu-id="59037-103">![Highlight Exceptions button in ribbon](media/tat-highlightex.gif "Highlight Exceptions button in ribbon")</span></span>  
  
 <span data-ttu-id="59037-104">資料有時可能包含不尋常的值。</span><span class="sxs-lookup"><span data-stu-id="59037-104">Sometimes your data might contain peculiar values.</span></span> <span data-ttu-id="59037-105">例如，家長的年齡可能會列為五歲。</span><span class="sxs-lookup"><span data-stu-id="59037-105">For example, a homeowner's age might be listed as five years old.</span></span> <span data-ttu-id="59037-106">這些*值（通常稱為極端*值）可能會因為資料輸入錯誤而發生錯誤，或可能表示不尋常的趨勢。</span><span class="sxs-lookup"><span data-stu-id="59037-106">These values, often called *outliers*, might be wrong because of a data input error, or they might indicate unusual trends.</span></span> <span data-ttu-id="59037-107">不論是哪一個情況，例外狀況都可影響分析的品質。</span><span class="sxs-lookup"><span data-stu-id="59037-107">Either way, exceptions can affect the quality of your analysis.</span></span> <span data-ttu-id="59037-108">[**反白顯示例外**狀況] 工具可協助您尋找這些值，並加以審查以進行進一步的動作。</span><span class="sxs-lookup"><span data-stu-id="59037-108">The **Highlight Exceptions** tool helps you find these values and review them for further action.</span></span>  
  
 <span data-ttu-id="59037-109">[**反白顯示例外**狀況] 工具可以處理 Excel 資料表中的整個資料範圍，您也可以只選取幾個資料行。</span><span class="sxs-lookup"><span data-stu-id="59037-109">The **Highlight Exceptions** tool can work with the entire range of data in an Excel data table, or you can select only a few columns.</span></span> <span data-ttu-id="59037-110">您也可以調整控制資料變化性的臨界值，以尋找更多或更少的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="59037-110">You can also adjust a threshold that controls the variability of data, to find more or fewer exceptions.</span></span>  
  
 <span data-ttu-id="59037-111">當此工具完成分析時，它會建立一張新的工作表，其中包含您所分析之每一個資料行中所找到之極端值數目的摘要報表。</span><span class="sxs-lookup"><span data-stu-id="59037-111">When the tool completes its analysis, it creates a new worksheet that contains a summary report of how many outliers were found in each of the columns that you analyzed.</span></span> <span data-ttu-id="59037-112">此工具也會在原始的資料表中反白顯示例外狀況。</span><span class="sxs-lookup"><span data-stu-id="59037-112">The tool also highlights the exceptions in the original data table.</span></span> <span data-ttu-id="59037-113">由於此工具會分析整體趨勢，所以它可能會發現資料列中的大多數值為一般值，而只反白顯示該資料列中的一個資料格。</span><span class="sxs-lookup"><span data-stu-id="59037-113">Because the tool analyzes overall trends, it might find that most of the values in a row are normal, and highlight only one cell in that row.</span></span> <span data-ttu-id="59037-114">在上述的屋主範例中，只會反白顯示 [ **Age** ] 資料行。</span><span class="sxs-lookup"><span data-stu-id="59037-114">In the homeowner example above, only the **Age** column might be highlighted.</span></span>  
  
 <span data-ttu-id="59037-115">您也可以變更 [**摘要報告**] 中的 [**例外狀況臨界**值]。</span><span class="sxs-lookup"><span data-stu-id="59037-115">You can also change the **Exception threshold** value in the **Summary Report**.</span></span> <span data-ttu-id="59037-116">這個值表示特定資料格包含異常值的機率。</span><span class="sxs-lookup"><span data-stu-id="59037-116">This value indicates the probability that a particular cell contains an abnormal value.</span></span> <span data-ttu-id="59037-117">因此，如果您增加其值，反白顯示為極端值的值數目就會減少。</span><span class="sxs-lookup"><span data-stu-id="59037-117">Therefore, if you increase the value, fewer values will be highlighted as outliers.</span></span> <span data-ttu-id="59037-118">相反地，當您減少這個值時，您將會看到更多反白顯示的資料格。</span><span class="sxs-lookup"><span data-stu-id="59037-118">Conversely, when you decrease the value, you will see more highlighted cells.</span></span>  
  
## <a name="using-the-highlight-exceptions-tool"></a><span data-ttu-id="59037-119">使用反白顯示例外狀況工具</span><span class="sxs-lookup"><span data-stu-id="59037-119">Using the Highlight Exceptions Tool</span></span>  
  
1.  <span data-ttu-id="59037-120">開啟 Excel 資料表，然後按一下 [**反白顯示例外**狀況]。</span><span class="sxs-lookup"><span data-stu-id="59037-120">Open an Excel table and click **Highlight Exceptions**.</span></span>  
  
2.  <span data-ttu-id="59037-121">指定要分析的資料行。</span><span class="sxs-lookup"><span data-stu-id="59037-121">Specify the columns to analyze.</span></span>  
  
3.  <span data-ttu-id="59037-122">按一下 **[執行]** 。</span><span class="sxs-lookup"><span data-stu-id="59037-122">Click **Run**.</span></span>  
  
4.  <span data-ttu-id="59037-123">開啟標題為 [極端值] 的工作表， \<table name> 以查看找到的極端值摘要。</span><span class="sxs-lookup"><span data-stu-id="59037-123">Open the worksheet titled \<table name> Outliers to view a summary of the outliers that were found.</span></span>  
  
5.  <span data-ttu-id="59037-124">若要變更重點的數目，請按一下 [**反白顯示例外**狀況] 報告之 [**例外狀況臨界值**] 資料列中的向上和向下箭號。</span><span class="sxs-lookup"><span data-stu-id="59037-124">To change the number of highlights, click the up and down arrows in the **Exception Threshold** row of the **Highlight Exceptions Report**.</span></span>  
  
### <a name="requirements"></a><span data-ttu-id="59037-125">需求</span><span class="sxs-lookup"><span data-stu-id="59037-125">Requirements</span></span>  
 <span data-ttu-id="59037-126">您可以包括未含有錯誤值的資料行，但前提是這些值所包含的資訊可能對於預測其他資料列很有協助。</span><span class="sxs-lookup"><span data-stu-id="59037-126">You can include columns that do not contain bad values if these values contain information that might be useful in predicting other rows.</span></span> <span data-ttu-id="59037-127">但是，您應該取消選取有許多遺失值或零值的資料行。</span><span class="sxs-lookup"><span data-stu-id="59037-127">However, you should deselect columns that have many missing or zero values.</span></span>  
  
 <span data-ttu-id="59037-128">由於所有選取的資料行都用於建立一般模式，因此，您應該避免使用已知效能低落的輸入資料行，例如下列：</span><span class="sxs-lookup"><span data-stu-id="59037-128">Because all of the selected columns are used to create a general pattern, you should avoid using input columns that you know to have poor information, such as the following:</span></span>  
  
-   <span data-ttu-id="59037-129">包含識別碼之類唯一值的資料行。</span><span class="sxs-lookup"><span data-stu-id="59037-129">Columns that contain unique values such as IDs.</span></span>  
  
-   <span data-ttu-id="59037-130">包含高百分比錯誤值的資料行。</span><span class="sxs-lookup"><span data-stu-id="59037-130">Columns that contain a high percentage of wrong values.</span></span>  
  
-   <span data-ttu-id="59037-131">包含許多遺漏值的資料行。</span><span class="sxs-lookup"><span data-stu-id="59037-131">Columns with many missing values.</span></span>  
  
     <span data-ttu-id="59037-132">請注意，在某些情況下，包含有許多遺漏值的輸入資料行很有用。</span><span class="sxs-lookup"><span data-stu-id="59037-132">Note that there are some cases where it is useful to include input columns that have many missing values.</span></span> <span data-ttu-id="59037-133">例如，若客戶向零售店購買時，地址欄位的值總是遺漏，資料採礦演算法就可以使用這項資訊來識別其他類似的客戶。</span><span class="sxs-lookup"><span data-stu-id="59037-133">For example, if the value of the address field is always missing when the customer buys through a retailer, the data mining algorithm can use this information to identify other similar customers.</span></span> <span data-ttu-id="59037-134">您必須依各個案例來判斷資料是因省略而遺漏，或是由於遺漏的狀態有意義。</span><span class="sxs-lookup"><span data-stu-id="59037-134">You must determine on a case-by-case basis whether data is missing by omission or because the Missing state is meaningful.</span></span>  
  
-   <span data-ttu-id="59037-135">建立模式時，可能不實用的資料行。</span><span class="sxs-lookup"><span data-stu-id="59037-135">Columns that are unlikely to be useful in creating a pattern.</span></span> <span data-ttu-id="59037-136">例如，在每個資料列都有相同值的資料行不會加入建立模式時相當實用的資訊。</span><span class="sxs-lookup"><span data-stu-id="59037-136">For example, a column that has the same value in every row adds no information that would be useful in building patterns.</span></span>  
  
## <a name="understanding-the-highlight-exceptions-report"></a><span data-ttu-id="59037-137">了解反白顯示例外狀況報表</span><span class="sxs-lookup"><span data-stu-id="59037-137">Understanding the Highlight Exceptions Report</span></span>  
 <span data-ttu-id="59037-138">當您按一下 [**執行**] 時，此工具會執行三項動作：</span><span class="sxs-lookup"><span data-stu-id="59037-138">When you click **Run**, the tool does three things:</span></span>  
  
-   <span data-ttu-id="59037-139">根據目前在資料表中的資料來建立資料採礦結構。</span><span class="sxs-lookup"><span data-stu-id="59037-139">Creates a data mining structure based on the current data in the table.</span></span>  
  
-   <span data-ttu-id="59037-140">使用 [!INCLUDE[msCoName](../includes/msconame-md.md)] 群集演算法建立新的資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="59037-140">Creates a new data mining model by using the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm.</span></span>  
  
-   <span data-ttu-id="59037-141">根據模式來建立預測查詢，以判斷工作表中是否有任何值未必會發生。</span><span class="sxs-lookup"><span data-stu-id="59037-141">Creates a prediction query based on the patterns to determine whether any values in the worksheet are improbable.</span></span>  
  
 <span data-ttu-id="59037-142">例外狀況臨界值的初始值一定是 75，這表示那裡計算的演算法有 75% 的機率代表反白的資料有誤。</span><span class="sxs-lookup"><span data-stu-id="59037-142">The initial value for the exception threshold is always 75, meaning that the algorithm calculated there is a 75% chance that the highlighted data is wrong.</span></span> <span data-ttu-id="59037-143">此工具會自動設定這個臨界值，好讓初始分析能夠通過，但是您可以在報表中變更該值。</span><span class="sxs-lookup"><span data-stu-id="59037-143">The tool automatically sets this threshold for the initial analysis pass, but you can change the value in the report.</span></span>  
  
 <span data-ttu-id="59037-144">[**反白顯示例外**狀況] 工具會醒目提示原始資料表中可疑的資料格。</span><span class="sxs-lookup"><span data-stu-id="59037-144">The **Highlight Exceptions** tool highlights cells in the original data table that are suspicious.</span></span> <span data-ttu-id="59037-145">如果反白顯示的顏色很深，則表示資料列需要您特別留意。</span><span class="sxs-lookup"><span data-stu-id="59037-145">Dark highlighting means the row needs attention.</span></span> <span data-ttu-id="59037-146">如果反白顯示的顏色很亮，則表示該特定資料格中的值識別為可疑值。</span><span class="sxs-lookup"><span data-stu-id="59037-146">Bright highlighting means the value in that particular cell was identified as suspect.</span></span> <span data-ttu-id="59037-147">如果您變更例外狀況的臨界值，反白顯示的值也會隨著變更。</span><span class="sxs-lookup"><span data-stu-id="59037-147">If you change the threshold for the exceptions, the highlighted values will change accordingly.</span></span>  
  
 <span data-ttu-id="59037-148">摘要圖表會顯示每一個資料行中在例外狀況臨界值以上的資料格數目。</span><span class="sxs-lookup"><span data-stu-id="59037-148">The summary chart shows the number of cells in each column that were above the exception threshold.</span></span>  
  
## <a name="related-tools"></a><span data-ttu-id="59037-149">相關工具</span><span class="sxs-lookup"><span data-stu-id="59037-149">Related Tools</span></span>  
 <span data-ttu-id="59037-150">當您在準備資料採礦的過程中要清除或檢閱資料時，您可能也會嘗試適用於 Excel 的資料採礦用戶端中的資料瀏覽功能。</span><span class="sxs-lookup"><span data-stu-id="59037-150">When you are cleaning or reviewing data in preparation for data mining, you might also try the data exploration features in the Data Mining Client for Excel.</span></span> <span data-ttu-id="59037-151">這個增益集提供了更多進階的工具來協助您尋找極端值、重定資料標籤，或是檢視資料的分佈。</span><span class="sxs-lookup"><span data-stu-id="59037-151">This add-in provides more advanced tools to help you find outliers, relabel data, or view the distribution of data.</span></span> <span data-ttu-id="59037-152">如需適用于 Excel 的資料採礦用戶端中的資料探索工具的詳細資訊，請參閱[探索和清除資料](exploring-and-cleaning-data.md)。</span><span class="sxs-lookup"><span data-stu-id="59037-152">For more information about data exploration tools in the Data Mining Client for Excel, see [Exploring and Cleaning Data](exploring-and-cleaning-data.md).</span></span>  
  
 <span data-ttu-id="59037-153">[**反白顯示例外**狀況 [!INCLUDE[msCoName](../includes/msconame-md.md)] ] 工具使用群集演算法。</span><span class="sxs-lookup"><span data-stu-id="59037-153">The **Highlight Exceptions** tool uses the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm.</span></span> <span data-ttu-id="59037-154">群集模型會偵測共用類似特性的資料列群組。</span><span class="sxs-lookup"><span data-stu-id="59037-154">A clustering model detects groups of rows that share similar characteristics.</span></span> <span data-ttu-id="59037-155">適用于 Excel 的資料採礦用戶端會提供一個 **[流覽**] 視窗，其中使用圖形和特性設定檔，讓您探索叢集所建立的資料採礦模型。</span><span class="sxs-lookup"><span data-stu-id="59037-155">The Data Mining Client for Excel provides a **Browse** window that uses graphs and characteristic profiles to let you explore data mining models created by clustering.</span></span> <span data-ttu-id="59037-156">如需如何流覽「**反白顯示例外**狀況」工具所建立之群集模型的詳細資訊，請參閱[流覽模型 (適用于 Excel) 的資料採礦用戶端](highlight-exceptions-table-analysis-tools-for-excel.md)。</span><span class="sxs-lookup"><span data-stu-id="59037-156">For information about how to browse the clustering model created by the **Highlight Exceptions** tool, see [Browse Models (Data Mining Client for Excel)](highlight-exceptions-table-analysis-tools-for-excel.md).</span></span>  
  
 <span data-ttu-id="59037-157">如需有關 [!INCLUDE[msCoName](../includes/msconame-md.md)] 群集演算法的詳細資訊，請參閱《[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 線上叢書》中的＜Microsoft 群集演算法＞主題。</span><span class="sxs-lookup"><span data-stu-id="59037-157">For more information about the [!INCLUDE[msCoName](../includes/msconame-md.md)] Clustering algorithm, see the topic "Microsoft Clustering Algorithm" in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Books Online.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59037-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="59037-158">See Also</span></span>  
 [<span data-ttu-id="59037-159">適用於 Excel 的資料表分析工具</span><span class="sxs-lookup"><span data-stu-id="59037-159">Table Analysis Tools for Excel</span></span>](table-analysis-tools-for-excel.md)  
  
  
