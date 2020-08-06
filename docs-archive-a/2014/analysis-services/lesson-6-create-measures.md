---
title: 第7課：建立量值 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 01bd2ad7-09b7-49ae-ad80-83f25da301aa
author: minewiskan
ms.author: owend
ms.openlocfilehash: d89ea5c847276c7a34b4fc800d8bed7b9cd8ad34
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594778"
---
# <a name="lesson-7-create-measures"></a><span data-ttu-id="fddd9-102">第 7 課：建立量值</span><span class="sxs-lookup"><span data-stu-id="fddd9-102">Lesson 7: Create Measures</span></span>
  <span data-ttu-id="fddd9-103">在這一課，您將建立要包含在模型中的量值。</span><span class="sxs-lookup"><span data-stu-id="fddd9-103">In this lesson, you will create measures to be included in your model.</span></span> <span data-ttu-id="fddd9-104">量值與您在上一課建立的導出資料行相似，基本上是使用 DAX 公式建立的計算。</span><span class="sxs-lookup"><span data-stu-id="fddd9-104">Similar to the calculated columns you created in the previous lesson, a measure is essentially a calculation created using a DAX formula.</span></span> <span data-ttu-id="fddd9-105">不過，與導出資料行不同，量值評估是根據使用者選取的「篩選條件」\*\*。例如，在樞紐分析表的 [資料列標籤] 欄位中新增的特定資料行或交叉分析篩選器。</span><span class="sxs-lookup"><span data-stu-id="fddd9-105">However, unlike calculated columns, measures are evaluated based on a user selected *filter*; for example, a particular column or slicer added to the Row Labels field in a PivotTable.</span></span>   <span data-ttu-id="fddd9-106">然後會以套用的量值，計算篩選條件中每個資料格的值。</span><span class="sxs-lookup"><span data-stu-id="fddd9-106">A value for each cell in the filter is then calculated by the applied measure.</span></span> <span data-ttu-id="fddd9-107">量值是功能強大且彈性的計算，您會希望將它包含在幾乎所有表格式模型中，以便在數值資料上執行動態計算。</span><span class="sxs-lookup"><span data-stu-id="fddd9-107">Measures are powerful, flexible calculations that you will want to include in almost all tabular models, to perform dynamic calculations on numerical data.</span></span> <span data-ttu-id="fddd9-108">如需詳細資訊，請參閱[量值 &#40;SSAS 表格式&#41;](tabular-models/measures-ssas-tabular.md)。</span><span class="sxs-lookup"><span data-stu-id="fddd9-108">To learn more, see [Measures &#40;SSAS Tabular&#41;](tabular-models/measures-ssas-tabular.md).</span></span>  
  
 <span data-ttu-id="fddd9-109">您將使用 [量值方格] 建立量值。</span><span class="sxs-lookup"><span data-stu-id="fddd9-109">To create measures, you will use the Measure Grid.</span></span> <span data-ttu-id="fddd9-110">根據預設，每個資料表都有一個空白的量值方格，不過，通常您不會為每個資料表建立量值。</span><span class="sxs-lookup"><span data-stu-id="fddd9-110">By default, each table has an empty measure grid; however, you typically will not create measures for every table.</span></span> <span data-ttu-id="fddd9-111">在 [資料檢視] 中，量值方格會出現在模型設計師中的資料表下方。</span><span class="sxs-lookup"><span data-stu-id="fddd9-111">The Measure Grid appears below a table in the model designer when in Data View.</span></span> <span data-ttu-id="fddd9-112">若要隱藏或顯示資料表的量值方格，請按一下 [資料表]\*\*\*\* 功能表，然後按一下 [顯示量值方格]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fddd9-112">To hide or show the measure grid for a table, click the **Table** menu, and then click **Show Measure Grid**.</span></span>  
  
 <span data-ttu-id="fddd9-113">若要建立量值，您可以按一下量值方格中的空資料格，然後在公式列中輸入 DAX 公式。</span><span class="sxs-lookup"><span data-stu-id="fddd9-113">You can create a measure by clicking on an empty cell in the measure grid, and then typing a DAX formula in the formula bar.</span></span> <span data-ttu-id="fddd9-114">按 ENTER 完成公式時，量值就會出現在資料格中。</span><span class="sxs-lookup"><span data-stu-id="fddd9-114">When you click ENTER to complete the formula, the measure will then appear in the cell.</span></span> <span data-ttu-id="fddd9-115">您也可以按一下資料行，然後按一下工具列上的 [自動加總] 按鈕 (**∑**)，利用標準彙總函式建立量值。</span><span class="sxs-lookup"><span data-stu-id="fddd9-115">You can also create measures using a standard aggregation function by clicking on a column, and then clicking on the AutoSum button (**∑**) on the toolbar.</span></span> <span data-ttu-id="fddd9-116">使用 [自動加總] 功能建立的量值會出現在資料行正下方的量值方格資料格中，不過必要時可以將其移除。</span><span class="sxs-lookup"><span data-stu-id="fddd9-116">Measures created using the AutoSum feature will appear in the measure grid cell directly beneath the column, but can be moved if necessary.</span></span>  
  
 <span data-ttu-id="fddd9-117">在這一課，您將藉由在公式列中輸入 DAX 公式以及使用 [自動加總] 功能這兩種方式建立量值。</span><span class="sxs-lookup"><span data-stu-id="fddd9-117">In this lesson, you will create measures by both entering a DAX formula in the formula bar and by using the AutoSum feature.</span></span>  
  
 <span data-ttu-id="fddd9-118">這堂課的預估完成時間：**30 分鐘**</span><span class="sxs-lookup"><span data-stu-id="fddd9-118">Estimated time to complete this lesson: **30 minutes**</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fddd9-119">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="fddd9-119">Prerequisites</span></span>  
 <span data-ttu-id="fddd9-120">本主題是表格式模型教學課程的一部分，請依序完成。</span><span class="sxs-lookup"><span data-stu-id="fddd9-120">This topic is part of a tabular modeling tutorial, which should be completed in order.</span></span> <span data-ttu-id="fddd9-121">在執行本課中的工作之前，您應已完成上一課： [第 6 課：建立導出資料行](lesson-5-create-calculated-columns.md)。</span><span class="sxs-lookup"><span data-stu-id="fddd9-121">Before performing the tasks in this lesson, you should have completed the previous lesson: [Lesson 6: Create Calculated Columns](lesson-5-create-calculated-columns.md).</span></span>  
  
## <a name="create-measures"></a><span data-ttu-id="fddd9-122">建立量值</span><span class="sxs-lookup"><span data-stu-id="fddd9-122">Create Measures</span></span>  
  
#### <a name="to-create-a-days-current-quarter-to-date-measure-in-the-date-table"></a><span data-ttu-id="fddd9-123">在日期資料表中建立當季目前為止天數量值</span><span class="sxs-lookup"><span data-stu-id="fddd9-123">To create a Days Current Quarter to Date measure in the Date table</span></span>  
  
1.  <span data-ttu-id="fddd9-124">在模型設計師中，按一下 [日期]\*\*\*\* 資料表。</span><span class="sxs-lookup"><span data-stu-id="fddd9-124">In the model designer, click the **Date** table.</span></span>  
  
2.  <span data-ttu-id="fddd9-125">如果資料表下方尚未出現空的量值方格，請按一下 [資料表]\*\*\*\* 功能表，然後按一下 [顯示量值方格]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fddd9-125">If an empty measure grid does not already appear beneath the table, click on the **Table** menu, and then click **Show Measure Grid**.</span></span>  
  
3.  <span data-ttu-id="fddd9-126">在量值方格中，按一下左上方的空資料格。</span><span class="sxs-lookup"><span data-stu-id="fddd9-126">In the measure grid, click the top-left empty cell.</span></span>  
  
4.  <span data-ttu-id="fddd9-127">在資料表上方的公式列中，輸入下列公式︰</span><span class="sxs-lookup"><span data-stu-id="fddd9-127">In the formula bar, above the table, type the following formula:</span></span>  
  
     `=COUNTROWS( DATESQTD( 'Date'[Date]))`  
  
     <span data-ttu-id="fddd9-128">完成建立公式時，按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="fddd9-128">When you have finished building the formula, press ENTER.</span></span>  
  
     <span data-ttu-id="fddd9-129">請注意，左上方的資料格現在包含量值名稱 [**量值 1**]，後面接著結果 [ **30**]。</span><span class="sxs-lookup"><span data-stu-id="fddd9-129">Notice the top-left cell now contains a measure name, **Measure 1**, followed by the result, **30**.</span></span> <span data-ttu-id="fddd9-130">公式列中的公式前面也會有量值名稱。</span><span class="sxs-lookup"><span data-stu-id="fddd9-130">The measure name also precedes the formula in the formula bar.</span></span>  
  
5.  <span data-ttu-id="fddd9-131">若要重新命名量值，請在公式列中反白顯示名稱 [**量值 1**]，然後輸入 `Days Current Quarter to Date` ，然後按 enter 鍵。</span><span class="sxs-lookup"><span data-stu-id="fddd9-131">To rename the measure, in the formula bar, highlight the name, **Measure  1**, then type `Days Current Quarter to Date`, and then press ENTER.</span></span>  
  
    > [!TIP]  
    >  <span data-ttu-id="fddd9-132">在公式列中輸入公式時，您也可以先輸入量值名稱，後面接著冒號 (:)，再接著一個空格，最後是公式。</span><span class="sxs-lookup"><span data-stu-id="fddd9-132">When typing a formula in the formula bar, you can also first type the measure name followed by a colon (:), followed by a space, and then followed by the formula.</span></span> <span data-ttu-id="fddd9-133">使用這個方法就不需要重新命名量值。</span><span class="sxs-lookup"><span data-stu-id="fddd9-133">Using this method, you do not have to rename the measure.</span></span>  
  
#### <a name="to-create-a-days-in-current-quarter-measure-in-the-date-table"></a><span data-ttu-id="fddd9-134">在日期資料表中建立當季天數量值</span><span class="sxs-lookup"><span data-stu-id="fddd9-134">To create a Days in Current Quarter measure in the Date table</span></span>  
  
1.  <span data-ttu-id="fddd9-135">在 [日期]\*\*\*\* 資料表於模型設計師中仍為使用中狀態時，在量值方格中按一下您剛剛建立之量值下方的空資料格。</span><span class="sxs-lookup"><span data-stu-id="fddd9-135">With the **Date** table still active in the model designer, in the measure grid, click the empty cell below the measure you just created.</span></span>  
  
2.  <span data-ttu-id="fddd9-136">在公式列中，輸入下列公式︰</span><span class="sxs-lookup"><span data-stu-id="fddd9-136">In the formula bar, type the following formula:</span></span>  
  
     `Days in Current Quarter :=COUNTROWS( DATESBETWEEN( 'Date'[Date], STARTOFQUARTER( LASTDATE('Date'[Date])), ENDOFQUARTER('Date'[Date])))`  
  
     <span data-ttu-id="fddd9-137">請注意，在此公式中，您先包含了量值名稱後面接著冒號 (:)。</span><span class="sxs-lookup"><span data-stu-id="fddd9-137">Notice in this formula you first included the measure name followed by a colon (:).</span></span>  
  
     <span data-ttu-id="fddd9-138">完成建立公式時，按 ENTER。</span><span class="sxs-lookup"><span data-stu-id="fddd9-138">When you have finished building the formula, press ENTER.</span></span>  
  
 <span data-ttu-id="fddd9-139">在一個不完整期間與前一個期間之間建立比率時，公式必須考慮期間內已經過的比例，並且將它與前一個期間中的相同比例進行比較。</span><span class="sxs-lookup"><span data-stu-id="fddd9-139">When creating a comparison ratio between one incomplete period and the previous period; the formula must take into account the proportion of the period that has elapsed, and compare it to the same proportion in the previous period.</span></span> <span data-ttu-id="fddd9-140">在此案例中，[Days Current Quarter to Date]/[Days in Current Quarter] 會得出目前期間內已經過的比例。</span><span class="sxs-lookup"><span data-stu-id="fddd9-140">In this case, [Days Current Quarter to Date]/[Days in Current Quarter] gives the proportion elapsed in the current period.</span></span>  
  
#### <a name="to-create-an-internet-distinct-count-sales-order-measure-in-the-internet-sales-table"></a><span data-ttu-id="fddd9-141">在 Internet Sales 資料表中建立網際網路相異計數銷售訂單量值</span><span class="sxs-lookup"><span data-stu-id="fddd9-141">To create an Internet Distinct Count Sales Order measure in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="fddd9-142">在模型設計師中，按一下 [網際網路銷售]\*\*\*\* 資料表 (索引標籤)。</span><span class="sxs-lookup"><span data-stu-id="fddd9-142">In the model designer, click the **Internet Sales** table (tab).</span></span>  
  
     <span data-ttu-id="fddd9-143">如果量值方格尚未出現，請以滑鼠右鍵按一下 [網際網路銷售]\*\*\*\* 資料表 (索引標籤)，然後按一下 [顯示量值方格]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fddd9-143">If the measure grid does not already appear, right-click the **Internet Sales** table (tab), and then click **Show Measure Grid**.</span></span>  
  
2.  <span data-ttu-id="fddd9-144">按一下 [銷售訂單號碼]\*\*\*\* 欄位標題。</span><span class="sxs-lookup"><span data-stu-id="fddd9-144">Click on the **Sales Order Number** column heading.</span></span>  
  
3.  <span data-ttu-id="fddd9-145">在工具列上，按一下 「自動加總」 \(**∑**) 按鈕旁的向下箭號，然後選取 **[DistinctCount]**。</span><span class="sxs-lookup"><span data-stu-id="fddd9-145">On the toolbar, click the down-arrow next to the AutoSum (**∑**) button, and then select **DistinctCount**.</span></span>  
  
     <span data-ttu-id="fddd9-146">「自動加總」功能會使用 DistinctCount 標準彙總公式，自動為選取的資料行建立量值。</span><span class="sxs-lookup"><span data-stu-id="fddd9-146">The AutoSum feature automatically creates a measure for the selected column using the DistinctCount standard aggregation formula.</span></span>  
  
     <span data-ttu-id="fddd9-147">您會發現，量值方格中該資料行下方的頂部資料格現在包含量值名稱 **Distinct Count Sales Order Number**。</span><span class="sxs-lookup"><span data-stu-id="fddd9-147">Notice the top cell below the column in the measure grid now contains a measure name, **Distinct Count Sales Order Number**.</span></span> <span data-ttu-id="fddd9-148">使用 [自動加總] 功能建立的量值會自動放入關聯資料行下方量值方格中的最頂部資料格內。</span><span class="sxs-lookup"><span data-stu-id="fddd9-148">Measures created using the AutoSum feature are automatically placed in the top-most cell in the measure grid below the associated column.</span></span>  
  
4.  <span data-ttu-id="fddd9-149">在量值方格中，按一下新的量值，然後在 [屬性]\*\*\*\* 視窗的 [量值名稱]\*\*\*\* 中，將量值重新命名為 **Internet Distinct Count Sales Order**。</span><span class="sxs-lookup"><span data-stu-id="fddd9-149">In the measure grid, click the new measure, and then in the **Properties** window, in **Measure Name**, rename the measure to **Internet Distinct Count Sales Order**.</span></span>  
  
#### <a name="to-create-additional-measures-in-the-internet-sales-table"></a><span data-ttu-id="fddd9-150">在 Internet Sales 資料表中建立其他量值</span><span class="sxs-lookup"><span data-stu-id="fddd9-150">To create additional measures in the Internet Sales table</span></span>  
  
1.  <span data-ttu-id="fddd9-151">使用「自動加總」功能建立並命名下列量值︰</span><span class="sxs-lookup"><span data-stu-id="fddd9-151">By using the AutoSum feature, create and name the following measures:</span></span>  
  
    |<span data-ttu-id="fddd9-152">[量值名稱]</span><span class="sxs-lookup"><span data-stu-id="fddd9-152">Measure Name</span></span>|<span data-ttu-id="fddd9-153">資料行</span><span class="sxs-lookup"><span data-stu-id="fddd9-153">Column</span></span>|<span data-ttu-id="fddd9-154">自動加總 (∑)</span><span class="sxs-lookup"><span data-stu-id="fddd9-154">AutoSum (∑)</span></span>|<span data-ttu-id="fddd9-155">Formula</span><span class="sxs-lookup"><span data-stu-id="fddd9-155">Formula</span></span>|  
    |------------------|------------|-------------------|-------------|  
    |<span data-ttu-id="fddd9-156">Internet Order Lines Count</span><span class="sxs-lookup"><span data-stu-id="fddd9-156">Internet Order Lines Count</span></span>|<span data-ttu-id="fddd9-157">Sales Order Line Number</span><span class="sxs-lookup"><span data-stu-id="fddd9-157">Sales Order Line Number</span></span>|<span data-ttu-id="fddd9-158">計數</span><span class="sxs-lookup"><span data-stu-id="fddd9-158">Count</span></span>|<span data-ttu-id="fddd9-159">=COUNT([Sales Order Line Number])</span><span class="sxs-lookup"><span data-stu-id="fddd9-159">=COUNT([Sales Order Line Number])</span></span>|  
    |<span data-ttu-id="fddd9-160">Internet Total Units</span><span class="sxs-lookup"><span data-stu-id="fddd9-160">Internet Total Units</span></span>|<span data-ttu-id="fddd9-161">Order Quantity</span><span class="sxs-lookup"><span data-stu-id="fddd9-161">Order Quantity</span></span>|<span data-ttu-id="fddd9-162">加總</span><span class="sxs-lookup"><span data-stu-id="fddd9-162">Sum</span></span>|<span data-ttu-id="fddd9-163">=SUM([Order Quantity])</span><span class="sxs-lookup"><span data-stu-id="fddd9-163">=SUM([Order Quantity])</span></span>|  
    |<span data-ttu-id="fddd9-164">Internet Total Discount Amount</span><span class="sxs-lookup"><span data-stu-id="fddd9-164">Internet Total Discount Amount</span></span>|<span data-ttu-id="fddd9-165">折扣量</span><span class="sxs-lookup"><span data-stu-id="fddd9-165">Discount Amount</span></span>|<span data-ttu-id="fddd9-166">加總</span><span class="sxs-lookup"><span data-stu-id="fddd9-166">Sum</span></span>|<span data-ttu-id="fddd9-167">=SUM([Discount Amount])</span><span class="sxs-lookup"><span data-stu-id="fddd9-167">=SUM([Discount Amount])</span></span>|  
    |<span data-ttu-id="fddd9-168">Internet Total Product Cost</span><span class="sxs-lookup"><span data-stu-id="fddd9-168">Internet Total Product Cost</span></span>|<span data-ttu-id="fddd9-169">產品總成本</span><span class="sxs-lookup"><span data-stu-id="fddd9-169">Total Product Cost</span></span>|<span data-ttu-id="fddd9-170">加總</span><span class="sxs-lookup"><span data-stu-id="fddd9-170">Sum</span></span>|<span data-ttu-id="fddd9-171">=SUM([Total Product Cost])</span><span class="sxs-lookup"><span data-stu-id="fddd9-171">=SUM([Total Product Cost])</span></span>|  
    |<span data-ttu-id="fddd9-172">Internet Total Sales</span><span class="sxs-lookup"><span data-stu-id="fddd9-172">Internet Total Sales</span></span>|<span data-ttu-id="fddd9-173">銷售量</span><span class="sxs-lookup"><span data-stu-id="fddd9-173">Sales Amount</span></span>|<span data-ttu-id="fddd9-174">加總</span><span class="sxs-lookup"><span data-stu-id="fddd9-174">Sum</span></span>|<span data-ttu-id="fddd9-175">=SUM([Sales Amount])</span><span class="sxs-lookup"><span data-stu-id="fddd9-175">=SUM([Sales Amount])</span></span>|  
    |<span data-ttu-id="fddd9-176">Internet Total Margin</span><span class="sxs-lookup"><span data-stu-id="fddd9-176">Internet Total Margin</span></span>|<span data-ttu-id="fddd9-177">Margin</span><span class="sxs-lookup"><span data-stu-id="fddd9-177">Margin</span></span>|<span data-ttu-id="fddd9-178">加總</span><span class="sxs-lookup"><span data-stu-id="fddd9-178">Sum</span></span>|<span data-ttu-id="fddd9-179">=SUM([Margin])</span><span class="sxs-lookup"><span data-stu-id="fddd9-179">=SUM([Margin])</span></span>|  
    |<span data-ttu-id="fddd9-180">Internet Total Tax Amt</span><span class="sxs-lookup"><span data-stu-id="fddd9-180">Internet Total Tax Amt</span></span>|<span data-ttu-id="fddd9-181">稅額</span><span class="sxs-lookup"><span data-stu-id="fddd9-181">Tax Amt</span></span>|<span data-ttu-id="fddd9-182">加總</span><span class="sxs-lookup"><span data-stu-id="fddd9-182">Sum</span></span>|<span data-ttu-id="fddd9-183">=SUM([Tax Amt])</span><span class="sxs-lookup"><span data-stu-id="fddd9-183">=SUM([Tax Amt])</span></span>|  
    |<span data-ttu-id="fddd9-184">Internet Total Freight</span><span class="sxs-lookup"><span data-stu-id="fddd9-184">Internet Total Freight</span></span>|<span data-ttu-id="fddd9-185">Freight</span><span class="sxs-lookup"><span data-stu-id="fddd9-185">Freight</span></span>|<span data-ttu-id="fddd9-186">加總</span><span class="sxs-lookup"><span data-stu-id="fddd9-186">Sum</span></span>|<span data-ttu-id="fddd9-187">=SUM([Freight])</span><span class="sxs-lookup"><span data-stu-id="fddd9-187">=SUM([Freight])</span></span>|  
  
2.  <span data-ttu-id="fddd9-188">藉由按一下量值方格中的空白資料格，以及使用公式列，建立並命名下列量值：</span><span class="sxs-lookup"><span data-stu-id="fddd9-188">By clicking on an empty cell in the measure grid, and by using the formula bar, create and name the following measures:</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="fddd9-189">您必須依序建立下列量值；後續量值中的公式會參考之前的量值。</span><span class="sxs-lookup"><span data-stu-id="fddd9-189">You must create the following measures in order; formulas in later measures refer to earlier measures.</span></span>  
  
    |<span data-ttu-id="fddd9-190">[量值名稱]</span><span class="sxs-lookup"><span data-stu-id="fddd9-190">Measure Name</span></span>|<span data-ttu-id="fddd9-191">Formula</span><span class="sxs-lookup"><span data-stu-id="fddd9-191">Formula</span></span>|  
    |------------------|-------------|  
    |<span data-ttu-id="fddd9-192">Internet Previous Quarter Margin</span><span class="sxs-lookup"><span data-stu-id="fddd9-192">Internet Previous Quarter Margin</span></span>|<span data-ttu-id="fddd9-193">=CALCULATE([Internet Total Margin],PREVIOUSQUARTER('Date'[Date]))</span><span class="sxs-lookup"><span data-stu-id="fddd9-193">=CALCULATE([Internet Total Margin],PREVIOUSQUARTER('Date'[Date]))</span></span>|  
    |<span data-ttu-id="fddd9-194">Internet Current Quarter Margin</span><span class="sxs-lookup"><span data-stu-id="fddd9-194">Internet Current Quarter Margin</span></span>|<span data-ttu-id="fddd9-195">=TOTALQTD([Internet Total Margin],'Date'[Date])</span><span class="sxs-lookup"><span data-stu-id="fddd9-195">=TOTALQTD([Internet Total Margin],'Date'[Date])</span></span>|  
    |<span data-ttu-id="fddd9-196">Internet Previous Quarter Margin Proportion to QTD</span><span class="sxs-lookup"><span data-stu-id="fddd9-196">Internet Previous Quarter Margin Proportion to QTD</span></span>|<span data-ttu-id="fddd9-197">=[Internet Previous Quarter Margin]\*([Days Current Quarter to Date]/[Days In Current Quarter])</span><span class="sxs-lookup"><span data-stu-id="fddd9-197">=[Internet Previous Quarter Margin]\*([Days Current Quarter to Date]/[Days In Current Quarter])</span></span>|  
    |<span data-ttu-id="fddd9-198">Internet Previous Quarter Sales</span><span class="sxs-lookup"><span data-stu-id="fddd9-198">Internet Previous Quarter Sales</span></span>|<span data-ttu-id="fddd9-199">=CALCULATE([Internet Total Sales],PREVIOUSQUARTER('Date'[Date]))</span><span class="sxs-lookup"><span data-stu-id="fddd9-199">=CALCULATE([Internet Total Sales],PREVIOUSQUARTER('Date'[Date]))</span></span>|  
    |<span data-ttu-id="fddd9-200">Internet Current Quarter Sales</span><span class="sxs-lookup"><span data-stu-id="fddd9-200">Internet Current Quarter Sales</span></span>|<span data-ttu-id="fddd9-201">=TOTALQTD([Internet Total Sales],'Date'[Date])</span><span class="sxs-lookup"><span data-stu-id="fddd9-201">=TOTALQTD([Internet Total Sales],'Date'[Date])</span></span>|  
    |<span data-ttu-id="fddd9-202">Internet Previous Quarter Sales Proportion to QTD</span><span class="sxs-lookup"><span data-stu-id="fddd9-202">Internet Previous Quarter Sales Proportion to QTD</span></span>|<span data-ttu-id="fddd9-203">=[Internet Previous Quarter Sales]\*([Days Current Quarter to Date]/[Days In Current Quarter])</span><span class="sxs-lookup"><span data-stu-id="fddd9-203">=[Internet Previous Quarter Sales]\*([Days Current Quarter to Date]/[Days In Current Quarter])</span></span>|  
  
 <span data-ttu-id="fddd9-204">針對 [Internet Sales] 資料表建立的量值可用來分析關鍵的財務資料，例如使用者選取的篩選所定義的項目銷售額、成本和利率。</span><span class="sxs-lookup"><span data-stu-id="fddd9-204">Measures created for the Internet Sales table can be used to analyze critical financial data such as sales, costs, and profit margin for items defined by the user selected filter.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="fddd9-205">後續步驟</span><span class="sxs-lookup"><span data-stu-id="fddd9-205">Next Step</span></span>  
 <span data-ttu-id="fddd9-206">若要繼續進行本教學課程，請前往下一課： [第 8 課：建立關鍵效能指標](lesson-7-create-key-performance-indicators.md)。</span><span class="sxs-lookup"><span data-stu-id="fddd9-206">To continue this tutorial, go to the next lesson: [Lesson 8: Create Key Performance Indicators](lesson-7-create-key-performance-indicators.md).</span></span>  
  
  
