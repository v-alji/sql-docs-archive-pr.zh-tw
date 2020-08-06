---
title: 流覽貝氏貝氏機率分類模型 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: f9160b48-3beb-439c-9694-f084e1afa625
author: minewiskan
ms.author: owend
ms.openlocfilehash: 3b0d18cd74e71f1ef18bffd6b0998e0b326e887a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593111"
---
# <a name="browsing-a-naive-bayes-model"></a><span data-ttu-id="1f0f5-102">瀏覽貝式機率分類模型</span><span class="sxs-lookup"><span data-stu-id="1f0f5-102">Browsing a Naive Bayes Model</span></span>
  <span data-ttu-id="1f0f5-103">當您使用 **[流覽]** 來開啟簡單的貝氏機率分類模型時，該模型會顯示在具有四個不同窗格的互動式檢視器中。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-103">When you open a Naïve Bayes model using **Browse**, the model is displayed in an interactive viewer with four different panes.</span></span> <span data-ttu-id="1f0f5-104">您可以使用此檢視器來探索相互關聯，以及取得有關模型和基礎資料的資訊。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-104">Use the viewer to explore correlations, and get information about the model and the underlying data.</span></span>  
  
-   [<span data-ttu-id="1f0f5-105">相依性網路</span><span class="sxs-lookup"><span data-stu-id="1f0f5-105">Dependency Network</span></span>](#bkmk_DepNet)  
  
-   [<span data-ttu-id="1f0f5-106">屬性設定檔</span><span class="sxs-lookup"><span data-stu-id="1f0f5-106">Attribute Profiles</span></span>](#bkmk_AttProf)  
  
-   [<span data-ttu-id="1f0f5-107">屬性特性</span><span class="sxs-lookup"><span data-stu-id="1f0f5-107">Attribute Characteristics</span></span>](#bkmk_AttChar)  
  
-   [<span data-ttu-id="1f0f5-108">屬性辨識</span><span class="sxs-lookup"><span data-stu-id="1f0f5-108">Attribute Discrimination</span></span>](#bkmk_AttDisc)  
  
##  <a name="explore-the-model"></a><a name="BKMK_Tabs"></a><span data-ttu-id="1f0f5-109">探索模型</span><span class="sxs-lookup"><span data-stu-id="1f0f5-109">Explore the Model</span></span>  
 <span data-ttu-id="1f0f5-110">此檢視器的用途是要協助您探索 [!INCLUDE[msCoName](../includes/msconame-md.md)] 貝氏機率分類模型所發現之輸入與輸出屬性 (輸入與相依變數) 之間的互動。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-110">The purpose of the viewer is to help you explore the interaction between input and output attributes (inputs and dependent variables) that were discovered by the [!INCLUDE[msCoName](../includes/msconame-md.md)] Naive Bayes model.</span></span>  
  
 <span data-ttu-id="1f0f5-111">如果您想要試驗簡單的貝氏機率分類檢視器，請使用 [分類] Wizard &#40;[資料採礦] 功能區中的 [[適用于 Excel 的資料採礦增益集&#41;](classify-wizard-data-mining-add-ins-for-excel.md) Wizard]，按一下 [ **Advanced** ] 選項，然後將演算法變更為 [使用簡單的貝氏機率分類演算法]</span><span class="sxs-lookup"><span data-stu-id="1f0f5-111">If you want to experiment with the Naïve Bayes viewer, use the [Classify Wizard &#40;Data Mining Add-ins for Excel&#41;](classify-wizard-data-mining-add-ins-for-excel.md) wizard in the Data Mining ribbon, click the **Advanced** option, and change the algorithm to use the Naïve Bayes algorithm</span></span>  
  
 <span data-ttu-id="1f0f5-112">在這些範例中，我們使用範例活頁簿中的來源資料，並將資料行（**每年收入**）分組成五個收入群組，從**極低**到**非常高**。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-112">For these examples, we used the Source data in the sample workbook, and grouped the column, **Yearly Income**, into five income groups, from **Very Low** to **Very High**.</span></span> <span data-ttu-id="1f0f5-113">然後，貝氏機率分類模型便分析了與每個收入類別目錄相互關聯的因數。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-113">The Naïve Bayes model then analyzed the factors correlated with each income category.</span></span>  
  
###  <a name="dependency-network"></a><a name="bkmk_DepNet"></a><span data-ttu-id="1f0f5-114">相依性網路</span><span class="sxs-lookup"><span data-stu-id="1f0f5-114">Dependency Network</span></span>  
 <span data-ttu-id="1f0f5-115">您將使用的第一個視窗是相依性**網路**。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-115">The first window you'll use is the **Dependency Network**.</span></span> <span data-ttu-id="1f0f5-116">它會概略顯示哪些輸入與選取的結果密切相關。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-116">It shows you at a glance which inputs are closely correlated to the selected outcome.</span></span>  
  
 <span data-ttu-id="1f0f5-117">![貝氏機率分類檢視器中的相依性網路](media/dm13-nb.gif "貝氏機率分類檢視器中的相依性網路")</span><span class="sxs-lookup"><span data-stu-id="1f0f5-117">![dependency network in Naive Bayes viewer](media/dm13-nb.gif "dependency network in Naive Bayes viewer")</span></span>  
  
##### <a name="explore-the-dependency-network"></a><span data-ttu-id="1f0f5-118">探索相依性網路</span><span class="sxs-lookup"><span data-stu-id="1f0f5-118">Explore the dependency network</span></span>  
  
1.  <span data-ttu-id="1f0f5-119">首先，按一下 [目標結果] [**年收入**]，這會以圖形中的節點表示。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-119">First, click the target outcome, **Yearly Income**, which is represented as a node in the graph.</span></span>  
  
     <span data-ttu-id="1f0f5-120">目標變數周圍的反白顯示節點就是在統計上與此結果相關的節點。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-120">The highlighted nodes surrounding the target variable are those that are statistically correlated with this outcome.</span></span> <span data-ttu-id="1f0f5-121">請使用位於檢視器底部的圖例來了解關聯性的本質。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-121">Use the legend at the bottom of the viewer to understand the nature of the relationship.</span></span>  
  
2.  <span data-ttu-id="1f0f5-122">按一下檢視器左側的滑動軸，並向下拖曳。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-122">Click the slider at the left of the viewer and drag it downward.</span></span>  
  
     <span data-ttu-id="1f0f5-123">此控制項會根據相依性的強度，篩選獨立變數。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-123">This control filters the independent variables, based on the strengths of the dependencies.</span></span> <span data-ttu-id="1f0f5-124">當您向下拖曳滑動軸時，圖形中只會保留最強的連結。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-124">When you drag the slider down, only the strongest links remain in the graph.</span></span>  
  
3.  <span data-ttu-id="1f0f5-125">篩選圖形之後，請按一下 [**複製圖形視圖**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-125">After you have filtered the graph, click the button, **Copy Graph View**.</span></span> <span data-ttu-id="1f0f5-126">然後，選取 Excel 中的工作表，並且按下 Ctrl+V。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-126">Then select a worksheet in Excel, and press Ctrl+V.</span></span>  
  
     <span data-ttu-id="1f0f5-127">此選項會複製您已經選取的檢視，包括篩選和反白顯示。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-127">This option copies the view that you have selected, including filters and highlighting.</span></span>  
  
 [<span data-ttu-id="1f0f5-128">回到頁首</span><span class="sxs-lookup"><span data-stu-id="1f0f5-128">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="attribute-profiles"></a><a name="bkmk_AttProf"></a> <span data-ttu-id="1f0f5-129">屬性設定檔</span><span class="sxs-lookup"><span data-stu-id="1f0f5-129">Attribute Profiles</span></span>  
 <span data-ttu-id="1f0f5-130">[**屬性設定檔**] 視窗可讓您以視覺方式指出所有其他變數與個別結果的關聯。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-130">The **Attribute Profiles** windows gives you a visual indication of how all other variables are related to the individual outcomes.</span></span>  
  
##### <a name="explore-the-profiles"></a><span data-ttu-id="1f0f5-131">探索設定檔</span><span class="sxs-lookup"><span data-stu-id="1f0f5-131">Explore the profiles</span></span>  
  
1.  <span data-ttu-id="1f0f5-132">若要隱藏部分值，讓您能夠更輕易地比較結果，請按一下資料行標題並將它拖曳到其他資料行底下。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-132">To hide some values so that you can more easily compare outcomes, click the column heading and drag it under another column.</span></span>  
  
     <span data-ttu-id="1f0f5-133">![貝氏機率分類檢視器中的屬性設定檔](media/dm13-nb-attprof.gif "貝氏機率分類檢視器中的屬性設定檔")</span><span class="sxs-lookup"><span data-stu-id="1f0f5-133">![attribute profiles in Naive Bayes viewer](media/dm13-nb-attprof.gif "attribute profiles in Naive Bayes viewer")</span></span>  
  
2.  <span data-ttu-id="1f0f5-134">按一下任何資料格，即可在 [**挖掘圖例**] 中查看值的分佈。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-134">Click in any cell to view the distribution of values in the **Mining Legend**.</span></span>  
  
     <span data-ttu-id="1f0f5-135">因為與不同結果相關聯的屬性會以視覺效果方式顯示，所以您可以輕鬆地識別感興趣的相互關聯，例如各地區的收入分佈狀況。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-135">Because the attributes associated with different outcomes are displayed visually, it is easy to spot interesting correlations, such as how incomes are distributed by region.</span></span>  
  
3.  <span data-ttu-id="1f0f5-136">若要取得此視圖的基礎資料，請按一下 [**複製到 Excel**]。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-136">To obtain the data underlying this view, click **Copy to Excel**.</span></span> <span data-ttu-id="1f0f5-137">系統就會在新的工作表中產生資料表，其中顯示個別屬性與結果之間的相互關聯。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-137">A table is generated in a new worksheet that shows the correlations among individual attributes and outcomes.</span></span> <span data-ttu-id="1f0f5-138">在這個 Excel 資料表中，您可以輕鬆地隱藏或篩選資料行。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-138">In this Excel table you can easily hide or filter columns.</span></span>  
  
 [<span data-ttu-id="1f0f5-139">回到頁首</span><span class="sxs-lookup"><span data-stu-id="1f0f5-139">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="attribute-characteristics"></a><a name="bkmk_AttChar"></a><span data-ttu-id="1f0f5-140">屬性特性</span><span class="sxs-lookup"><span data-stu-id="1f0f5-140">Attribute Characteristics</span></span>  
 <span data-ttu-id="1f0f5-141">[**屬性特性**] 視圖適用于深入檢查特定結果變數和貢獻因素。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-141">The **Attribute Characteristics** view is useful for in-depth examination of a particular outcome variable and the contributing factors.</span></span>  
  
 <span data-ttu-id="1f0f5-142">![貝氏機率分類檢視器中的屬性特性](media/dm13-nb-viewer.gif "貝氏機率分類檢視器中的屬性特性")</span><span class="sxs-lookup"><span data-stu-id="1f0f5-142">![attribute characteristics in Naive Bayes viewer](media/dm13-nb-viewer.gif "attribute characteristics in Naive Bayes viewer")</span></span>  
  
##### <a name="explore-the-attribute-characteristics"></a><span data-ttu-id="1f0f5-143">探索屬性特性</span><span class="sxs-lookup"><span data-stu-id="1f0f5-143">Explore the attribute characteristics</span></span>  
  
1.  <span data-ttu-id="1f0f5-144">按一下 [**值**]，然後從**值**中選取一個專案。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-144">Click **Value** and select an item from the **Value**.</span></span>  
  
     <span data-ttu-id="1f0f5-145">當您選取目標結果時，圖形就會更新為顯示與結果關聯最強的因數，並按照重要性排序。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-145">As you select a target outcome, the graph updates to show the factors that are most strongly associated with the outcome, sorted by importance.</span></span>  
  
     <span data-ttu-id="1f0f5-146">請注意，如果您使用 [[分析關鍵影響因數] &#40;[適用于 Excel 的資料表分析工具&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md) ] 選項建立模型，則可以建立具有一個以上可預測屬性的模型。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-146">Note that if you create a model using the [Analyze Key Influencers &#40;Table Analysis Tools for Excel&#41;](analyze-key-influencers-table-analysis-tools-for-excel.md) option, you can create models that have more than one predictable attribute.</span></span> <span data-ttu-id="1f0f5-147">不過，資料採礦增益集中的所有其他精靈則會限制使用一個可預測屬性。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-147">However, all other wizards in the Data Mining add-ins limit you to one predictable attribute.</span></span>  
  
2.  <span data-ttu-id="1f0f5-148">按一下 [**複製到 Excel** ]，在新的工作表中建立資料表，列出與所選目標結果相關之所有屬性的分數。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-148">Click **Copy to Excel** to create a table, in a new worksheet, listing the scores for all attributes that are related to the selected target outcome.</span></span>  
  
 [<span data-ttu-id="1f0f5-149">回到頁首</span><span class="sxs-lookup"><span data-stu-id="1f0f5-149">Back To Top</span></span>](#BKMK_Tabs)  
  
###  <a name="attribute-discrimination"></a><a name="bkmk_AttDisc"></a><span data-ttu-id="1f0f5-150">屬性辨識</span><span class="sxs-lookup"><span data-stu-id="1f0f5-150">Attribute Discrimination</span></span>  
 <span data-ttu-id="1f0f5-151">**屬性**辨識視圖有助於比較兩個結果，或一個結果與其他所有結果。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-151">The **Attribute Discrimination** view helps compare two outcomes, or one outcome vs. all other outcomes.</span></span>  
  
 <span data-ttu-id="1f0f5-152">![貝氏機率分類檢視器中的屬性辨識](media/dm13-nb-attdisc.gif "貝氏機率分類檢視器中的屬性辨識")</span><span class="sxs-lookup"><span data-stu-id="1f0f5-152">![attribute discrimination in Naive Bayes viewer](media/dm13-nb-attdisc.gif "attribute discrimination in Naive Bayes viewer")</span></span>  
  
##### <a name="explore-attribute-discrimination"></a><span data-ttu-id="1f0f5-153">探索屬性辨識</span><span class="sxs-lookup"><span data-stu-id="1f0f5-153">Explore attribute discrimination</span></span>  
  
1.  <span data-ttu-id="1f0f5-154">使用 [**值 1** ] 和 [**值 2**] 控制項來選取您想要比較的結果。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-154">Use the controls, **Value 1** and **Value 2**, to select the outcomes that you want to compare.</span></span>  
  
     <span data-ttu-id="1f0f5-155">例如，在此模型中，「低收入」群組中有一些有趣的屬性，因此我們在第一個下拉式清單中選擇最低的「收入」群組，然後在第二個下拉式清單中選擇 [**其他所有狀態**]。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-155">For example, in this model there were some interesting attributes in the low income group, so we chose the lowest income group in the first dropdown list, and chose **All other states** in the second dropdown list.</span></span>  
  
     <span data-ttu-id="1f0f5-156">屬性就會按照重要性的順序 (根據定型資料計算而來) 排序。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-156">The attributes are sorted by order of importance (calculated based on the training data).</span></span> <span data-ttu-id="1f0f5-157">因此，職業是與收入最密切相關的因數 (至少這個目標群組是如此)。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-157">Therefore, occupation is the factor most closely correlated with income (for this target group, at least),</span></span>  
  
     <span data-ttu-id="1f0f5-158">若要查看確切的圖形，請按一下彩色列，並查看 [**挖掘圖例**]。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-158">To see the exact figures, click the colored bar and view the **Mining Legend**.</span></span>  
  
2.  <span data-ttu-id="1f0f5-159">請注意，較低收入也與歐洲地區相互關聯。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-159">Note that lower incomes are also correlated with the Europe region.</span></span>  
  
     <span data-ttu-id="1f0f5-160">貝氏機率分類模型不支援向下鑽研。不過，如果您想要調查與這個結果群組相關聯的案例，可以使用查詢。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-160">The Naïve Bayes model does not support drilldown; however, if you wanted to investigate the cases associated with this outcome group, you could use a query.</span></span> <span data-ttu-id="1f0f5-161">如需這種模型類型之查詢的詳細資訊，請參閱[貝氏貝氏機率分類模型查詢範例](data-mining/naive-bayes-model-query-examples.md)。</span><span class="sxs-lookup"><span data-stu-id="1f0f5-161">For information about queries on this type of model, see [Naive Bayes Model Query Examples](data-mining/naive-bayes-model-query-examples.md).</span></span>  
  
 [<span data-ttu-id="1f0f5-162">回到頁首</span><span class="sxs-lookup"><span data-stu-id="1f0f5-162">Back To Top</span></span>](#BKMK_Tabs)  
  
## <a name="see-also"></a><span data-ttu-id="1f0f5-163">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1f0f5-163">See Also</span></span>  
 [<span data-ttu-id="1f0f5-164">在 Excel 中流覽模型 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="1f0f5-164">Browsing Models in Excel &#40;SQL Server Data Mining Add-ins&#41;</span></span>](browsing-models-in-excel-sql-server-data-mining-add-ins.md)  
  
  
