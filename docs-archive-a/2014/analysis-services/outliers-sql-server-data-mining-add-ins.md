---
title: SQL Server 資料採礦增益集的極端值 () |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- exceptions [data mining]
- data preparation
- outliers [data mining]
- data cleaning
ms.assetid: e6fa7c62-4005-4792-9211-3b699377a517
author: minewiskan
ms.author: owend
ms.openlocfilehash: 92dddf3338d15e700576a13476ee364696bfd274
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710894"
---
# <a name="outliers-sql-server-data-mining-add-ins"></a><span data-ttu-id="06e93-102">極端值 (SQL Server 資料採礦增益集)</span><span class="sxs-lookup"><span data-stu-id="06e93-102">Outliers (SQL Server Data Mining Add-ins)</span></span>
  <span data-ttu-id="06e93-103">![資料採礦功能區中的極端值精靈](media/dmc-outliers.gif "資料採礦功能區中的極端值精靈")</span><span class="sxs-lookup"><span data-stu-id="06e93-103">![Outliers wizard in Data Mining ribbon](media/dmc-outliers.gif "Outliers wizard in Data Mining ribbon")</span></span>  
  
 <span data-ttu-id="06e93-104">極端*值表示因*下列其中一個原因而發生問題的資料值：</span><span class="sxs-lookup"><span data-stu-id="06e93-104">An *outlier* means a data value that is problematic for any one of the following reasons:</span></span>  
  
-   <span data-ttu-id="06e93-105">值在預期的範圍之外。</span><span class="sxs-lookup"><span data-stu-id="06e93-105">Value is outside the expected range.</span></span>  
  
-   <span data-ttu-id="06e93-106">資料可能未正確輸入。</span><span class="sxs-lookup"><span data-stu-id="06e93-106">Data might have been entered incorrectly.</span></span>  
  
-   <span data-ttu-id="06e93-107">值遺失。</span><span class="sxs-lookup"><span data-stu-id="06e93-107">Value is missing.</span></span>  
  
-   <span data-ttu-id="06e93-108">資料是由空格或其他 null 字串組成。</span><span class="sxs-lookup"><span data-stu-id="06e93-108">Data consists of a space or other null string.</span></span>  
  
-   <span data-ttu-id="06e93-109">值是正確的，不過目前仍是在分佈範圍之外，可能大幅影響模型。</span><span class="sxs-lookup"><span data-stu-id="06e93-109">Value is accurate, but is so far outside the distribution that it can significantly affect the model.</span></span>  
  
 <span data-ttu-id="06e93-110">適用於 Excel 的資料採礦用戶端可協助您偵測此資料，然後升級這些值或隱藏這些值。</span><span class="sxs-lookup"><span data-stu-id="06e93-110">The Data Mining Client for Excel helps you detect this data, and then update the values or suppress them.</span></span> <span data-ttu-id="06e93-111">例如，您可以用算術平均值來取代極端值，或是可以刪除可能包含錯誤值的資料列。</span><span class="sxs-lookup"><span data-stu-id="06e93-111">For example, you can replace outliers with an arithmetic mean, or you can delete rows that contain potentially wrong values.</span></span>  
  
## <a name="handling-outliers"></a><span data-ttu-id="06e93-112">處理極端值</span><span class="sxs-lookup"><span data-stu-id="06e93-112">Handling Outliers</span></span>  
 <span data-ttu-id="06e93-113">[**移除**極端值] wizard 提供幾個工具來適當地處理極端值：</span><span class="sxs-lookup"><span data-stu-id="06e93-113">The **Remove Outliers** wizard gives you several tools to handle outliers appropriately:</span></span>  
  
-   <span data-ttu-id="06e93-114">首先，您可以瀏覽資料來進一步了解值的分佈以及極端值與其他資料的關係。</span><span class="sxs-lookup"><span data-stu-id="06e93-114">First, you can explore the data to better understand the distribution of values and the relationship of the outliers to other data.</span></span>  
  
     <span data-ttu-id="06e93-115">例如，您可以使用 [**流覽資料**] 工作來檢查並修正值。</span><span class="sxs-lookup"><span data-stu-id="06e93-115">For example, you can use the **Explore Data** task to review and fix the values.</span></span> <span data-ttu-id="06e93-116">[**移除**極端值] wizard 也會顯示圖形（線條或橫條圖），以協助您瞭解所有值的分佈。</span><span class="sxs-lookup"><span data-stu-id="06e93-116">The **Remove Outliers** wizard also displays a graph, either a line or a bar chart, to help you understand the distribution of all values.</span></span>  
  
-   <span data-ttu-id="06e93-117">接下來，您可以使用 **[極端**值] wizard 來移除或變更極端值。</span><span class="sxs-lookup"><span data-stu-id="06e93-117">Next, you can use the **Outliers** wizard to remove or change outliers.</span></span> <span data-ttu-id="06e93-118">您使用的方法取決於值為離散或連續而定。</span><span class="sxs-lookup"><span data-stu-id="06e93-118">The method that you use depends on whether the values are discrete or continuous.</span></span>  
  
     <span data-ttu-id="06e93-119">此精靈會將離散值顯示在橫條圖中，每一橫條都代表特定的值，而該橫條的高度則代表每個值的案例數。</span><span class="sxs-lookup"><span data-stu-id="06e93-119">The wizard displays discrete values in a bar chart, where each bar represents a specific value, and the height of the bar indicates the number of cases for each value.</span></span> <span data-ttu-id="06e93-120">藉由滑動圖形上的臨界值控制項，您可以切掉代表過於極端或可能有錯誤值之群組的橫條。</span><span class="sxs-lookup"><span data-stu-id="06e93-120">By sliding the threshold control on the chart, you can cut off bars that represent groups of extreme or potentially bad values.</span></span>  
  
-   <span data-ttu-id="06e93-121">此精靈會在橫條圖或折線圖上顯示連續的值。</span><span class="sxs-lookup"><span data-stu-id="06e93-121">The wizard displays continuous values either on a bar chart or line chart.</span></span> <span data-ttu-id="06e93-122">在折線圖上，值是由 X 軸上的值表示，而計數值則是由 Y 軸上的值表示。</span><span class="sxs-lookup"><span data-stu-id="06e93-122">On the line chart, the value is represented on the x-axis and the count of values on the y-axis.</span></span>  
  
     <span data-ttu-id="06e93-123">您可以藉由變更**最小**和**最大**值，或是滑動列，來控制是否要在圖表的低端和高階端移除或保留值。</span><span class="sxs-lookup"><span data-stu-id="06e93-123">You can control whether to remove or keep values at the low and high ends of the chart by changing the **Minimum** and **Maximum** values, or sliding the bars.</span></span> <span data-ttu-id="06e93-124">當您變更最小和最大值設定時，將會隱藏的資料會以圖中的陰影來顯示。</span><span class="sxs-lookup"><span data-stu-id="06e93-124">As you change the minimum and maximum value settings, the data that will be suppressed is shown by shading in the graph.</span></span>  
  
 <span data-ttu-id="06e93-125">在您選取要處理的極端值之後，您會告訴精靈要如何處理極端值。</span><span class="sxs-lookup"><span data-stu-id="06e93-125">After you have selected which outliers to work with, you tell the wizard how to handle the outliers.</span></span> <span data-ttu-id="06e93-126">您可以刪除包含極端值的資料列，或是可以指定取代值，如平均值、null 或另一個您所選擇的值。</span><span class="sxs-lookup"><span data-stu-id="06e93-126">You can either delete the rows that contain the outlier values, or you can specify a replacement value, such as a mean, a null, or another value of your choice.</span></span>  
  
 <span data-ttu-id="06e93-127">最後，此精靈會提供您一些選項來顯示新的資料。</span><span class="sxs-lookup"><span data-stu-id="06e93-127">Finally, the wizard gives you some options for displaying the new data.</span></span> <span data-ttu-id="06e93-128">您可以用新的值取代原始資料、將新資料行加入包含新值的資料表，或是建立包含更新資料的新工作表。</span><span class="sxs-lookup"><span data-stu-id="06e93-128">You can replace the original data with the new values, add a new column to the table that contains the new values, or create a new worksheet that contains the updated data.</span></span>  
  
### <a name="using-the-outlier-wizard"></a><span data-ttu-id="06e93-129">使用極端值精靈</span><span class="sxs-lookup"><span data-stu-id="06e93-129">Using the Outlier Wizard</span></span>  
  
1.  <span data-ttu-id="06e93-130">在 [**資料採礦**] 功能區中，按一下 [**清除資料**]，**然後選取 [** 極端值]。</span><span class="sxs-lookup"><span data-stu-id="06e93-130">In the **Data Mining** ribbon, click **Clean Data**, and select **Outliers**.</span></span>  
  
2.  <span data-ttu-id="06e93-131">在 [**選取來源資料**] 對話方塊中，選取 Excel 資料表或資料格範圍，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="06e93-131">In the **Select Source Data** dialog box, select an Excel data table, or a range of cells, and click **Next**.</span></span>  
  
    > [!WARNING]  
    >  <span data-ttu-id="06e93-132">您不能在外部資料上**使用 [極端**值] wizard，除非您先將它複製到 Excel。</span><span class="sxs-lookup"><span data-stu-id="06e93-132">You cannot use the **Outliers** wizard on external data, unless you copy it to Excel first.</span></span>  
  
3.  <span data-ttu-id="06e93-133">在 [**選取資料行**] 對話方塊中，選取**單一**資料行。</span><span class="sxs-lookup"><span data-stu-id="06e93-133">In the **Select Column** dialog box, select a **single** column.</span></span>  
  
     <span data-ttu-id="06e93-134">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="06e93-134">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="06e93-135">在 [**指定臨界**值] 對話方塊中，檢查資料的分佈。</span><span class="sxs-lookup"><span data-stu-id="06e93-135">In the **Specify Thresholds** dialog box, review the distribution of data.</span></span>  
  
    -   <span data-ttu-id="06e93-136">如果資料行包含離散值，則精靈會顯示包含每個離散值計數的長條圖。</span><span class="sxs-lookup"><span data-stu-id="06e93-136">If the column contains discrete values, the wizard displays a histogram containing the count for each discrete value.</span></span>  
  
         <span data-ttu-id="06e93-137">假設極端值是罕見的值，您可以藉由變更**最小**值來篩選它們。</span><span class="sxs-lookup"><span data-stu-id="06e93-137">Assuming that outliers are rare values, you can filter them out by changing the **Minimum** value.</span></span>  
  
    -   <span data-ttu-id="06e93-138">如果資料行包含數值資料，您可以按一下 [**以離散方式顯示**] 按鈕或 [**以數值形式**顯示] 按鈕，在查看橫條圖或折線圖中的值之間切換。</span><span class="sxs-lookup"><span data-stu-id="06e93-138">If the column contains numeric data, you can click the **View as Discrete** button or the **View as Numeric** button to toggle between viewing the values in a bar chart or line chart.</span></span>  
  
5.  <span data-ttu-id="06e93-139">在 [**指定臨界**值] 對話方塊中，選擇您想要保留的資料範圍，方法是輸入最小和最大值，或拖曳滑動軸。</span><span class="sxs-lookup"><span data-stu-id="06e93-139">In the **Specify Thresholds** dialog box, choose the range of data you want to keep by typing a minimum and maximum value, or by dragging the slider bars.</span></span> <span data-ttu-id="06e93-140">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="06e93-140">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="06e93-141">在 [極端值**處理**] 對話方塊中，指定是否要刪除或取代值，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="06e93-141">In the **Outlier Handling** dialog box, specify whether you want the values to be deleted or replaced, and click **Next**.</span></span>  
  
7.  <span data-ttu-id="06e93-142">在 [**選取目的地**] 對話方塊中，指定您要儲存新資料的位置。</span><span class="sxs-lookup"><span data-stu-id="06e93-142">In the **Select Destination** dialog box, specify where you want the new data to be saved.</span></span>  
  
### <a name="related-options"></a><span data-ttu-id="06e93-143">相關的選項</span><span class="sxs-lookup"><span data-stu-id="06e93-143">Related Options</span></span>  
 <span data-ttu-id="06e93-144">精靈提供下列選項：</span><span class="sxs-lookup"><span data-stu-id="06e93-144">The wizard provides these options:</span></span>  
  
|<span data-ttu-id="06e93-145">**選項**</span><span class="sxs-lookup"><span data-stu-id="06e93-145">**Options**</span></span>|<span data-ttu-id="06e93-146">**註解**</span><span class="sxs-lookup"><span data-stu-id="06e93-146">**Comment**</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="06e93-147">**選取資料行**</span><span class="sxs-lookup"><span data-stu-id="06e93-147">**Select Column**</span></span>|<span data-ttu-id="06e93-148">您一次只能使用一個資料行。</span><span class="sxs-lookup"><span data-stu-id="06e93-148">You can work with only one column at a time.</span></span>|  
|<span data-ttu-id="06e93-149">**指定臨界值處理方式**</span><span class="sxs-lookup"><span data-stu-id="06e93-149">**Specify Thresholds Handling**</span></span>|<span data-ttu-id="06e93-150">使用 [**最小**值] 設定閾值，以排除比閾值更少的資料列中所找到的值。</span><span class="sxs-lookup"><span data-stu-id="06e93-150">Set a threshold using **Minimum** to exclude values that are found in fewer rows than the threshold value.</span></span><br /><br /> <span data-ttu-id="06e93-151">一開始，**最小**值等於資料列數目下限的值，而且您無法將最小值設為小於該值。</span><span class="sxs-lookup"><span data-stu-id="06e93-151">Initially the value in **Minimum** is equal to the value with the fewest rows, and you cannot make the minimum lower than that value.</span></span>|  
|<span data-ttu-id="06e93-152">**極端值處理**</span><span class="sxs-lookup"><span data-stu-id="06e93-152">**Outlier Handling**</span></span>|<span data-ttu-id="06e93-153">如果您決定刪除極端值，可以變更目前工作表中的資料，或是在新工作表中建立資料複本。</span><span class="sxs-lookup"><span data-stu-id="06e93-153">If you decide to delete outliers, you can either change the data in the current worksheet, or create a copy of the data in a new worksheet.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="06e93-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="06e93-154">See Also</span></span>  
 [<span data-ttu-id="06e93-155">流覽資料 &#40;SQL Server 資料採礦增益集&#41;</span><span class="sxs-lookup"><span data-stu-id="06e93-155">Explore Data &#40;SQL Server Data Mining Add-ins&#41;</span></span>](explore-data-sql-server-data-mining-add-ins.md)  
  
  
