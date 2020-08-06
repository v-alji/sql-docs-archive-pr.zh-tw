---
title: 定義和流覽 Kpi |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 648b9a02-1278-4f11-b940-6f0de6a4042d
author: minewiskan
ms.author: owend
ms.openlocfilehash: 44febe6c6c5d432f0cdee43e8eaaa3401c54a2c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698749"
---
# <a name="defining-and-browsing-kpis"></a><span data-ttu-id="3ffa6-102">定義和瀏覽 KPI</span><span class="sxs-lookup"><span data-stu-id="3ffa6-102">Defining and Browsing KPIs</span></span>
  <span data-ttu-id="3ffa6-103">若要定義關鍵效能指標 (KPI)，您必須先定義 KPI 名稱以及與該 KPI 相關聯的量值群組。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-103">To define key performance indicators (KPIs), you first define a KPI name and the measure group to which the KPI is associated.</span></span> <span data-ttu-id="3ffa6-104">KPI 可以和所有的量值群組或單一量值群組相關聯。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-104">A KPI can be associated with all measure groups or with a single measure group.</span></span> <span data-ttu-id="3ffa6-105">接著就定義 KPI 的下列元素：</span><span class="sxs-lookup"><span data-stu-id="3ffa6-105">You then define the following elements of the KPI:</span></span>

-   <span data-ttu-id="3ffa6-106">值運算式</span><span class="sxs-lookup"><span data-stu-id="3ffa6-106">The value expression</span></span>

     <span data-ttu-id="3ffa6-107">值運算式是一個實體量值 (例如，銷售)、導出量值 (例如，利潤) 或是利用多維度運算式 (MDX) 運算式，在 KPI 中定義的計算。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-107">A value expression is a physical measure such as Sales, a calculated measure such as Profit, or a calculation that is defined within the KPI by using a Multidimensional Expressions (MDX) expression.</span></span>

-   <span data-ttu-id="3ffa6-108">目標運算式</span><span class="sxs-lookup"><span data-stu-id="3ffa6-108">The goal expression</span></span>

     <span data-ttu-id="3ffa6-109">目標運算式是一個值，或是解析為一值的 MDX 運算式，它會針對值運算式所定義的量值定義目標。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-109">A goal expression is a value, or an MDX expression that resolves to a value, that defines the target for the measure that the value expression defines.</span></span> <span data-ttu-id="3ffa6-110">例如，目標運算式可能是公司業務經理想要提升銷售或利潤所用的量。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-110">For example, a goal expression could be the amount by which the business managers of a company want to increase sales or profit.</span></span>

-   <span data-ttu-id="3ffa6-111">狀態運算式</span><span class="sxs-lookup"><span data-stu-id="3ffa6-111">The status expression</span></span>

     <span data-ttu-id="3ffa6-112">狀態運算式是一個 MDX 運算式，可讓 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 用於評估相較於目標運算式的值運算式目前狀態。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-112">A status expression is an MDX expression that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to evaluate the current status of the value expression compared to the goal expression.</span></span> <span data-ttu-id="3ffa6-113">目標運算式是 -1 至 +1 範圍內的正規化值，其中 -1 表示非常差，而 +1 則表示非常好。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-113">A goal expression is a normalized value in the range of -1 to +1, where -1 is very bad, and +1 is very good.</span></span> <span data-ttu-id="3ffa6-114">狀態運算式會顯示一個圖形，幫助您輕鬆地判斷相較於目標運算式的值運算式狀態。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-114">The status expression displays a graphic to help you easily determine the status of the value expression compared to the goal expression.</span></span>

-   <span data-ttu-id="3ffa6-115">趨勢運算式</span><span class="sxs-lookup"><span data-stu-id="3ffa6-115">The trend expression</span></span>

     <span data-ttu-id="3ffa6-116">趨勢運算式是一個 MDX 運算式，是 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 用於評估相較於目標運算式的值運算式目前趨勢。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-116">A trend expression is an MDX expression that [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] uses to evaluate the current trend of the value expression compared to the goal expression.</span></span> <span data-ttu-id="3ffa6-117">趨勢運算式可以幫助商務使用者快速判斷，相對於目標運算式來說，值運算式是越來越好亦或越來越糟。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-117">The trend expression helps the business user to quickly determine whether the value expression is becoming better or worse relative to the goal expression.</span></span> <span data-ttu-id="3ffa6-118">您可以將其中一個圖形關聯到趨勢運算式，幫助商務使用者快速了解趨勢。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-118">You can associate one of several graphics with the trend expression to help business users be able to quickly understand the trend.</span></span>

 <span data-ttu-id="3ffa6-119">除了您為 KPI 定義的這些元素之外，還可以定義 KPI 的幾種屬性。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-119">In addition to these elements that you define for a KPI, you also define several properties of a KPI.</span></span> <span data-ttu-id="3ffa6-120">這些屬性包括顯示資料夾、父系 KPI (如果 KPI 是從其他 KPI 計算而來)、目前時間成員 (如果有的話)、KPI 的加權 (如果有的話) 以及 KPI 的描述。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-120">These properties include a display folder, a parent KPI if the KPI is computed from other KPIs, the current time member if there is one, the weight of the KPI if it has one, and a description of the KPI.</span></span>

> [!NOTE]
>  <span data-ttu-id="3ffa6-121">如需 KPI 的其他範例，請參閱 [計算工具] 窗格之 [範本] 索引標籤上的 KPI 範例，或是 **Adventure Works DW 2012** 範例資料倉儲中的範例。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-121">For more examples of KPIs, see the KPI examples on the Templates tab in the Calculation Tools pane or in the examples in the **Adventure Works DW 2012** sample data warehouse.</span></span> <span data-ttu-id="3ffa6-122">如需如何安裝此資料庫的詳細資訊，請參閱 [安裝 Analysis Services 多維度模型化教學課程的範例資料和專案](install-sample-data-and-projects.md)。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-122">For more information about how to install this database, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).</span></span>

 <span data-ttu-id="3ffa6-123">在這一課的工作中，您會在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程專案中定義 KPI，然後利用這些 KPI 來瀏覽 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-123">In the task in this lesson, you define  KPIs in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, and you then browse the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube by using these KPIs.</span></span> <span data-ttu-id="3ffa6-124">您將定義下列 KPI：</span><span class="sxs-lookup"><span data-stu-id="3ffa6-124">You will define the following KPIs:</span></span>

-   <span data-ttu-id="3ffa6-125">轉售商收入</span><span class="sxs-lookup"><span data-stu-id="3ffa6-125">Reseller Revenue</span></span>

     <span data-ttu-id="3ffa6-126">這個 KPI 是用於測量實際轉售商銷售與轉售商銷售配額之間的對比、銷售情形與目標之間的差距，以及達到目標的趨勢走向。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-126">This KPI is used to measure how actual reseller sales compare to sales quotas for reseller sales, how close the sales are to the goal, and what the trend is toward reaching the goal.</span></span>

-   <span data-ttu-id="3ffa6-127">產品毛利率</span><span class="sxs-lookup"><span data-stu-id="3ffa6-127">Product Gross Profit Margin</span></span>

     <span data-ttu-id="3ffa6-128">這個 KPI 是用於判斷每個產品類別目錄的毛利率與每個產品類別目錄指定的目標之間的差距，同時也用於判斷達到此目標的趨勢走向。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-128">This KPI is used to determine how close the gross profit margin is for each product category to a specified goal for each product category, and also to determine the trend toward reaching this goal.</span></span>

## <a name="defining-the-reseller-revenue-kpi"></a><span data-ttu-id="3ffa6-129">定義轉售商收入 KPI</span><span class="sxs-lookup"><span data-stu-id="3ffa6-129">Defining the Reseller Revenue KPI</span></span>

1.  <span data-ttu-id="3ffa6-130">針對 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube，開啟 [Cube 設計師]，然後按一下 [KPI]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-130">Open Cube Designer for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube, and then click the **KPIs** tab.</span></span>

     <span data-ttu-id="3ffa6-131">[KPI]\*\*\*\* 索引標籤包含多個窗格。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-131">The **KPIs** tab includes several panes.</span></span> <span data-ttu-id="3ffa6-132">在該索引標籤的左方，是 [KPI 組合管理]\*\*\*\* 窗格和 [計算工具]\*\*\*\* 窗格。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-132">On the left side of the tab are the **KPI Organizer** pane and the **Calculation Tools** pane.</span></span> <span data-ttu-id="3ffa6-133">索引標籤中間的顯示窗格，含有在 [KPI 組合管理]\*\*\*\* 窗格所選的 KPI 詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-133">The display pane in the middle of the tab contains the details of the KPI that is selected in the **KPI Organizer** pane.</span></span>

     <span data-ttu-id="3ffa6-134">下圖顯示 [Cube 設計師] 的 [KPI]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-134">The following image shows the **KPIs** tab of Cube Designer.</span></span>

     <span data-ttu-id="3ffa6-135">![Cube 設計師的 KPI 索引標籤](../../2014/tutorials/media/l7-kpi-1.gif "Cube 設計師的 KPI 索引標籤")</span><span class="sxs-lookup"><span data-stu-id="3ffa6-135">![KPIs tab of Cube Designer](../../2014/tutorials/media/l7-kpi-1.gif "KPIs tab of Cube Designer")</span></span>

2.  <span data-ttu-id="3ffa6-136">在 [KPI]\*\*\*\* 索引標籤的工具列上，按一下 [新增 KPI]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-136">On the toolbar of the **KPIs** tab, click the **New KPI** button.</span></span>

     <span data-ttu-id="3ffa6-137">顯示窗格中會出現一個空白的 KPI 範本，如下圖所示。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-137">A blank KPI template appears in the display pane, as shown in the following image.</span></span>

     <span data-ttu-id="3ffa6-138">![顯示窗格中的空白 KPI 範本](../../2014/tutorials/media/l7-kpi-2.gif "顯示窗格中的空白 KPI 範本")</span><span class="sxs-lookup"><span data-stu-id="3ffa6-138">![Blank KPI template in display pane](../../2014/tutorials/media/l7-kpi-2.gif "Blank KPI template in display pane")</span></span>

3.  <span data-ttu-id="3ffa6-139">在 [**名稱**] 方塊中，輸入 `Reseller Revenue` ，然後在 [**相關聯的量值群組**] 清單中選取 [**轉售商銷售**]。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-139">In the **Name** box, type `Reseller Revenue`, and then select **Reseller Sales** in the **Associated measure group** list.</span></span>

4.  <span data-ttu-id="3ffa6-140">在 [計算工具]\*\*\*\* 窗格的 [中繼資料]\*\*\*\* 索引標籤上，依序展開 [量值]\*\*\*\* 和 [轉售商銷售]\*\*\*\*，然後將 [轉售商銷售 - 銷售量]\*\*\*\* 量值拖曳到 [值運算式]\*\*\*\* 方塊。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-140">On the **Metadata** tab in the **Calculation Tools** pane, expand **Measures**, expand **Reseller Sales**, and then drag the **Reseller Sales-Sales Amount** measure to the **Value Expression** box.</span></span>

5.  <span data-ttu-id="3ffa6-141">在 [計算工具]\*\*\*\* 窗格的 [中繼資料]\*\*\*\* 索引標籤上，依序展開 [量值]\*\*\*\* 和 [銷售配額]\*\*\*\*，然後將 [銷售量配額]\*\*\*\* 量值拖曳到 [目標運算式]\*\*\*\* 方塊。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-141">On the **Metadata** tab in the **Calculation Tools** pane, expand **Measures**, expand **Sales Quotas**, and then drag the **Sales Amount Quota** measure to the **Goal Expression** box.</span></span>

6.  <span data-ttu-id="3ffa6-142">驗證 [狀態指標]\*\*\*\* 清單中是否已經選取 [量測計]\*\*\*\*，然後在 [狀態運算式]\*\*\*\* 方塊中，輸入下列 MDX 運算式：</span><span class="sxs-lookup"><span data-stu-id="3ffa6-142">Verify that **Gauge** is selected in the **Status indicator** list, and then type the following MDX expression in the **Status expression** box:</span></span>

    ```
    Case
     When 
      KpiValue("Reseller Revenue")/KpiGoal("Reseller Revenue")>=.95
       Then 1
     When
      KpiValue("Reseller Revenue")/KpiGoal("Reseller Revenue")<.95
       And 
      KpiValue("Reseller Revenue")/KpiGoal("Reseller Revenue")>=.85
       Then 0
      Else-1
    End
    ```

     <span data-ttu-id="3ffa6-143">這個 MDX 運算式可提供一個依據，讓您評估到達目標的進度。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-143">This MDX expression provides the basis for evaluating the progress toward the goal.</span></span> <span data-ttu-id="3ffa6-144">在這個 MDX 運算式中，如果實際的轉售商銷售超過目標的 85%，則會使用 0 值來擴展所選擇的圖形。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-144">In this MDX expression, if actual reseller sales are more than 85 percent of the goal, a value of 0 is used to populate the chosen graphic.</span></span> <span data-ttu-id="3ffa6-145">由於量測計是所選的圖形，量測計中的指標是介於空和滿之間。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-145">Because a gauge is the chosen graphic, the pointer in the gauge will be half-way between empty and full.</span></span> <span data-ttu-id="3ffa6-146">如果實際的轉售商銷售超過 90%，則量測計上的指標，大約是在空和滿之間的四分之三處。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-146">If actual reseller sales are more the 90 percent, the pointer on the gauge will be three-fourths of the way between empty and full.</span></span>

7.  <span data-ttu-id="3ffa6-147">驗證 [趨勢指標]\*\*\*\* 清單中是否已選取 [標準箭頭]\*\*\*\*，然後在 [趨勢運算式]\*\*\*\* 方塊中輸入下列運算式：</span><span class="sxs-lookup"><span data-stu-id="3ffa6-147">Verify that **Standard arrow** is selected in the **Trend indicator** list, and then type the following expression in the **Trend expression** box:</span></span>

    ```
    Case
     When IsEmpty
      (ParallelPeriod
       ([Date].[Calendar Date].[Calendar Year],1,
           [Date].[Calendar Date].CurrentMember))
      Then 0  
     When  (
      KpiValue("Reseller Revenue") - 
       (KpiValue("Reseller Revenue"), 
        ParallelPeriod
         ([Date].[Calendar Date].[Calendar Year],1,
           [Date].[Calendar Date].CurrentMember))
          /
          (KpiValue ("Reseller Revenue"),
           ParallelPeriod
            ([Date].[Calendar Date].[Calendar Year],1,
             [Date].[Calendar Date].CurrentMember)))
           >=.02
      Then 1
       When(
        KpiValue("Reseller Revenue") - 
         (KpiValue ( "Reseller Revenue" ),
          ParallelPeriod
           ([Date].[Calendar Date].[Calendar Year],1,
            [Date].[Calendar Date].CurrentMember))
           /
            (KpiValue("Reseller Revenue"),
             ParallelPeriod
              ([Date].[Calendar Date].[Calendar Year],1,
                [Date].[Calendar Date].CurrentMember)))
            <=.02
      Then -1
       Else 0
    End
    ```

     <span data-ttu-id="3ffa6-148">這個 MDX 運算式可提供一個依據，讓您評估到達定義目標的趨勢。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-148">This MDX expression provides the basis for evaluating the trend toward achieving the defined goal.</span></span>

## <a name="browsing-the-cube-by-using-the-reseller-revenue-kpi"></a><span data-ttu-id="3ffa6-149">使用轉售商收入 KPI 來瀏覽 Cube</span><span class="sxs-lookup"><span data-stu-id="3ffa6-149">Browsing the Cube by Using the Reseller Revenue KPI</span></span>

1.  <span data-ttu-id="3ffa6-150">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的 [建立]\*\*\*\* 功能表上，按一下 [Deploy Analysis Services Tutorial (部署 Analysis Services Tutorial)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-150">On the **Build** menu of [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], click **Deploy Analysis Service Tutorial**.</span></span>

2.  <span data-ttu-id="3ffa6-151">當您順利完成部署時，請在 [KPI]\*\*\*\* 索引標籤的工具列上，按一下 [瀏覽器檢視]\*\*\*\* 按鈕，然後按一下 [重新連接]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-151">When deployment has successfully completed, on the toolbar of the **KPIs** tab, click the **Browser View** button, and then click **Reconnect**.</span></span>

     <span data-ttu-id="3ffa6-152">狀態和趨勢量測計會根據每個維度的預設成員值，顯示在轉售商銷售的 [KPI 瀏覽器]\*\*\*\* 窗格中，連同該值和目標的值一起。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-152">The status and trend gauges are displayed in the **KPI Browser** pane for reseller sales based on the values for the default member of each dimension, together with the value for the value and the goal.</span></span> <span data-ttu-id="3ffa6-153">每個維度的預設成員是 [所有層級] 的 [所有成員]，因為您尚未定義任何維度的其他成員，做為預設成員。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-153">The default member of each dimension is the All member of the All level, because you have not defined any other member of any dimension as the default member.</span></span>

3.  <span data-ttu-id="3ffa6-154">在 [篩選] 窗格中，從 [維度]\*\*\*\* 清單中選取 [銷售領域]\*\*\*\*、從 [階層]\*\*\*\* 清單中選取 [銷售領域]\*\*\*\*、從 [運算子]\*\*\*\* 清單中選取 [等於]\*\*\*\*、從 [篩選運算式]\*\*\*\* 清單中選取 [北美洲]\*\*\*\* 核取方塊，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-154">In the filter pane, select **Sales Territory** in the **Dimension** list, select **Sales Territories** in the **Hierarchy** list, select **Equal** in the **Operator** list, select the **North America** check box in the **Filter Expression** list, and then click **OK**.</span></span>

4.  <span data-ttu-id="3ffa6-155">在 [篩選]\*\*\*\* 窗格的下一個資料列中，從 [維度]\*\*\*\* 清單中選取 [日期]\*\*\*\*、從 [階層]\*\*\*\* 清單中選取 [日曆日期]\*\*\*\*、從 [運算子]\*\*\*\* 清單中選取 [等於]\*\*\*\*、從 [篩選運算式]\*\*\*\* 清單中選取 [Q3 CY 2007]\*\*\*\* 核取方塊，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-155">In the next row in the **Filter** pane, select **Date** in the **Dimension** list, select **Calendar Date** in the **Hierarchy** list, select **Equal** in the **Operator** list, select the **Q3 CY 2007** check box in the **Filter Expression** list, and then click **OK**.</span></span>

5.  <span data-ttu-id="3ffa6-156">按一下 [KPI 瀏覽器]\*\*\*\* 窗格中的任何位置，更新 [轉售商收入 KPI]\*\*\*\* 的值。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-156">Click anywhere in the **KPI Browser** pane to update the values for the **Reseller Revenue KPI**.</span></span>

     <span data-ttu-id="3ffa6-157">請注意，KPI 的 [值]\*\*\*\*、[目標]\*\*\*\* 和 [狀態]\*\*\*\* 區段都反映新時段的值。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-157">Notice that the **Value**, **Goal**, and **Status** sections of the KPI reflect the values for the new time period</span></span>

## <a name="defining-the-product-gross-profit-margin-kpi"></a><span data-ttu-id="3ffa6-158">定義產品毛利率 KPI</span><span class="sxs-lookup"><span data-stu-id="3ffa6-158">Defining the Product Gross Profit Margin KPI</span></span>

1.  <span data-ttu-id="3ffa6-159">按一下 [KPI]\*\*\*\* 索引標籤之工具列上的 [表單檢視]\*\*\*\* 按鈕，然後按一下 [新增 KPI]\*\*\*\* 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-159">Click the **Form View** button on the toolbar of the **KPIs** tab, and then click the **New KPI** button.</span></span>

2.  <span data-ttu-id="3ffa6-160">在 [**名稱**] 方塊中，輸入 `Product Gross Profit Margin` ，然後確認 **\<All>** 出現在 [**相關聯的量值群組**] 清單中。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-160">In the **Name** box, type `Product Gross Profit Margin`, and then verify that **\<All>** appears in the **Associated measure group** list.</span></span>

3.  <span data-ttu-id="3ffa6-161">在 [計算工具]\*\*\*\* 窗格的 [中繼資料]\*\*\*\* 索引標籤中，將 [總毛利率]\*\*\*\* 量值拖曳到 [值運算式]\*\*\*\* 方塊。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-161">In the **Metadata** tab in the **Calculation Tools** pane, drag the **Total GPM** measure to the **Value Expression** box.</span></span>

4.  <span data-ttu-id="3ffa6-162">在 [目標運算式]\*\*\*\* 方塊中，輸入下列運算式：</span><span class="sxs-lookup"><span data-stu-id="3ffa6-162">In the **Goal Expression** box, type the following expression:</span></span>

    ```
    Case
        When [Product].[Category].CurrentMember Is
          [Product].[Category].[Accessories]
        Then .40                 
        When [Product].[Category].CurrentMember 
          Is [Product].[Category].[Bikes]
        Then .12                
        When [Product].[Category].CurrentMember Is
          [Product].[Category].[Clothing]
        Then .20
        When [Product].[Category].CurrentMember Is
          [Product].[Category].[Components]
        Then .10
        Else .12            
    End
    ```

5.  <span data-ttu-id="3ffa6-163">在 [狀態指標]\*\*\*\* 清單中，選取 [圓柱]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-163">In the **Status indicator** list, select **Cylinder**.</span></span>

6.  <span data-ttu-id="3ffa6-164">在 [狀態運算式]\*\*\*\* 方塊中，輸入下列 MDX 運算式：</span><span class="sxs-lookup"><span data-stu-id="3ffa6-164">Type the following MDX expression in the **Status expression** box:</span></span>

    ```
    Case
        When KpiValue( "Product Gross Profit Margin" ) / 
             KpiGoal ( "Product Gross Profit Margin" ) >= .90
        Then 1
        When KpiValue( "Product Gross Profit Margin" ) / 
             KpiGoal ( "Product Gross Profit Margin" ) <  .90
             And 
             KpiValue( "Product Gross Profit Margin" ) / 
             KpiGoal ( "Product Gross Profit Margin" ) >= .80
        Then 0
        Else -1
    End
    ```

     <span data-ttu-id="3ffa6-165">這個 MDX 運算式可提供一個依據，讓您評估到達目標的進度。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-165">This MDX expression provides the basis for evaluating the progress toward the goal.</span></span>

7.  <span data-ttu-id="3ffa6-166">驗證 [趨勢指標]\*\*\*\* 清單中是否已選取 [標準箭頭]\*\*\*\*，然後在 [趨勢運算式]\*\*\*\* 方塊中輸入下列 MDX 運算式：</span><span class="sxs-lookup"><span data-stu-id="3ffa6-166">Verify that **Standard arrow** is selected in the **Trend indicator** list, and then type the following MDX expression in the **Trend expression** box:</span></span>

    ```
    Case
    When IsEmpty
      (ParallelPeriod
       ([Date].[Calendar Date].[Calendar Year],1,
           [Date].[Calendar Date].CurrentMember))
      Then 0  
       When VBA!Abs
        (
          KpiValue( "Product Gross Profit Margin" ) - 
           (
             KpiValue ( "Product Gross Profit Margin" ),
              ParallelPeriod
              ( 
                [Date].[ Calendar Date].[ Calendar Year],
                1,
                [Date].[ Calendar Date].CurrentMember
              )
            ) /
            (
              KpiValue ( "Product Gross Profit Margin" ),
              ParallelPeriod
              ( 
                [Date].[ Calendar Date].[ Calendar Year],
                1,
                [Date].[ Calendar Date].CurrentMember
              )
            )  
          ) <=.02
      Then 0
      When KpiValue( "Product Gross Profit Margin" ) - 
           (
             KpiValue ( "Product Gross Profit Margin" ),
             ParallelPeriod
             ( 
               [Date].[ Calendar Date].[ Calendar Year],
               1,
               [Date].[ Calendar Date].CurrentMember
             )
           ) /
           (
             KpiValue ( "Product Gross Profit Margin" ),
             ParallelPeriod
             ( 
               [Date].[Calendar Date].[Calendar Year],
               1,
               [Date].[Calendar Date].CurrentMember
             )
           )  >.02
      Then 1
      Else -1
    End
    ```

     <span data-ttu-id="3ffa6-167">這個 MDX 運算式可提供一個依據，讓您評估到達定義目標的趨勢。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-167">This MDX expression provides the basis for evaluating the trend toward achieving the defined goal.</span></span>

## <a name="browsing-the-cube-by-using-the-total-gross-profit-margin-kpi"></a><span data-ttu-id="3ffa6-168">使用總毛利率 KPI 來瀏覽 Cube</span><span class="sxs-lookup"><span data-stu-id="3ffa6-168">Browsing the Cube by Using the Total Gross Profit Margin KPI</span></span>

1.  <span data-ttu-id="3ffa6-169">在 [建立]\*\*\*\* 功能表上，按一下 [Deploy Analysis Services Tutorial (部署 Analysis Services Tutorial)]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-169">On the **Build** menu, click **Deploy Analysis Service Tutorial**.</span></span>

2.  <span data-ttu-id="3ffa6-170">當您順利完成部署時，請在 [KPI]\*\*\*\* 索引標籤的工具列上按一下 [重新連接]\*\*\*\*，然後按一下 [瀏覽器檢視]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-170">When deployment has successfully completed, click **Reconnect** on the toolbar of the **KPIs** tab, and then click **Browser View**.</span></span>

     <span data-ttu-id="3ffa6-171">`Product Gross Profit Margin`Kpi 隨即出現，並顯示**Q3 CY 2007**和**北美洲**sales 領域的 KPI 值。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-171">The `Product Gross Profit Margin` KPI appears and displays the KPI value for **Q3 CY 2007** and the **North America** sales territory.</span></span>

3.  <span data-ttu-id="3ffa6-172">在 [篩選]\*\*\*\* 窗格中，從 [維度]\*\*\*\* 清單中選取 [產品]\*\*\*\*、從 [階層]\*\*\*\* 清單中選取 [類別目錄]\*\*\*\*、從 [運算子]\*\*\*\* 清單中選取 [等於]\*\*\*\*，並從 [篩選運算式]\*\*\*\* 清單中選取 [自行車]\*\*\*\*，然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-172">In the **Filter** pane, select **Product** in the **Dimension** list, select **Category** in the **Hierarchy** list, select **Equal** in the **Operator** list, and then select **Bikes** in the **Filter Expression** list, and then click **OK**.</span></span>

     <span data-ttu-id="3ffa6-173">北美地區轉售商 Q3 CY 2007 自行車銷售的毛利率隨即出現。</span><span class="sxs-lookup"><span data-stu-id="3ffa6-173">The gross profit margin for the sale of Bikes by resellers in North America in Q3 CY 2007 appears.</span></span>

## <a name="next-lesson"></a><span data-ttu-id="3ffa6-174">下一課</span><span class="sxs-lookup"><span data-stu-id="3ffa6-174">Next Lesson</span></span>
 [<span data-ttu-id="3ffa6-175">第8課：定義動作</span><span class="sxs-lookup"><span data-stu-id="3ffa6-175">Lesson 8: Defining Actions</span></span>](lesson-8-defining-actions.md)


