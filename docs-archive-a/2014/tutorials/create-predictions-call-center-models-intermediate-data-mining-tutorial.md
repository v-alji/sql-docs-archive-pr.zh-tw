---
title: " (元資料採礦教學課程中建立撥打電話中心模型的預測) |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5be0cec7-f639-4eeb-835e-e3204ae619e9
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: c2d402fb9f6509292442f31f85478b0612a45d56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593257"
---
# <a name="creating-predictions-for-the-call-center-models-intermediate-data-mining-tutorial"></a><span data-ttu-id="c6788-102">建立用於撥接中心模型的預測 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="c6788-102">Creating Predictions for the Call Center Models (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="c6788-103">現在您已經了解排班、操作員數目、電話，以及服務等級之間的互動關係，接著就可以準備建立一些用來進行商務分析和規劃的預測查詢。</span><span class="sxs-lookup"><span data-stu-id="c6788-103">Now that you have learned something about the interactions between shifts, the number of operators, calls, and service grade, you are ready to create some prediction queries that can be used in business analysis and planning.</span></span> <span data-ttu-id="c6788-104">您將先針對探勘模型建立一些預測，以測試一些假設。</span><span class="sxs-lookup"><span data-stu-id="c6788-104">You will first create some predictions on the exploratory model to test some assumptions.</span></span> <span data-ttu-id="c6788-105">接著您將使用羅吉斯迴歸模型建立大量預測。</span><span class="sxs-lookup"><span data-stu-id="c6788-105">Next, you will create bulk predictions by using the logistic regression model.</span></span>  
  
 <span data-ttu-id="c6788-106">本課程假設您已熟悉預測查詢的概念。</span><span class="sxs-lookup"><span data-stu-id="c6788-106">This lesson assumes that you are already familiar with the concept of prediction queries.</span></span>  
  
## <a name="creating-predictions-using-the-neural-network-model"></a><span data-ttu-id="c6788-107">使用類神經網路模型建立預測</span><span class="sxs-lookup"><span data-stu-id="c6788-107">Creating Predictions using the Neural Network Model</span></span>  
 <span data-ttu-id="c6788-108">下列範例示範如何使用為了探索資料所建立的類神經網路模型進行單一預測。</span><span class="sxs-lookup"><span data-stu-id="c6788-108">The following example demonstrates how to make a singleton prediction using the neural network model that was created for exploration.</span></span> <span data-ttu-id="c6788-109">單一預測可以讓您嘗試不同的值，是觀察在模型中會產生何種效果的好方法。</span><span class="sxs-lookup"><span data-stu-id="c6788-109">Singleton predictions are a good way to try out different values to see the effect in the model.</span></span> <span data-ttu-id="c6788-110">在這個案例中，您將預測如果有六個經驗豐富的操作員值班，大夜班 (未指定星期幾) 的服務等級將是哪個等級。</span><span class="sxs-lookup"><span data-stu-id="c6788-110">In this scenario, you will predict the service grade for the midnight shift (no day of the week specified) if six experienced operators are on duty.</span></span>  
  
#### <a name="to-create-a-singleton-query-by-using-the-neural-network-model"></a><span data-ttu-id="c6788-111">若要使用類神經網路模型建立單一查詢</span><span class="sxs-lookup"><span data-stu-id="c6788-111">To create a singleton query by using the neural network model</span></span>  
  
1.  <span data-ttu-id="c6788-112">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 中，開啟包含您要使用之模型的方案。</span><span class="sxs-lookup"><span data-stu-id="c6788-112">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the solution that contains the model that you want to use.</span></span>  
  
2.  <span data-ttu-id="c6788-113">在 [資料採礦設計師] 中，按一下 [**採礦模型預測**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c6788-113">In Data Mining Designer, click the **Mining Model Prediction** tab.</span></span>  
  
3.  <span data-ttu-id="c6788-114">在 [**採礦模型**] 窗格中，按一下 [**選取模型**]。</span><span class="sxs-lookup"><span data-stu-id="c6788-114">In the **Mining Model** pane, click **Select Model**.</span></span>  
  
4.  <span data-ttu-id="c6788-115">[**選取採礦模型**] 對話方塊會顯示一份採礦結構清單。</span><span class="sxs-lookup"><span data-stu-id="c6788-115">The **Select Mining Model** dialog box shows a list of mining structures.</span></span> <span data-ttu-id="c6788-116">展開採礦結構，檢視與該結構相關聯之採礦模型的清單。</span><span class="sxs-lookup"><span data-stu-id="c6788-116">Expand the mining structure to view a list of mining models associated with that structure.</span></span>  
  
5.  <span data-ttu-id="c6788-117">展開採礦結構 [撥接中心預設值]，然後選取類神經網路模型 [撥接中心 – LR]。</span><span class="sxs-lookup"><span data-stu-id="c6788-117">Expand the mining structure Call Center Default, and select the neural network model, Call Center - LR.</span></span>  
  
6.  <span data-ttu-id="c6788-118">從 [採礦模型]\*\*\*\* 功能表中選取 [單一查詢]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6788-118">From the **Mining Model** menu, select **Singleton Query**.</span></span>  
  
     <span data-ttu-id="c6788-119">[**單一查詢輸入**] 對話方塊隨即出現，其中的資料行會對應到「採礦模型」中的資料行。</span><span class="sxs-lookup"><span data-stu-id="c6788-119">The **Singleton Query Input** dialog box appears, with columns mapped to the columns in the mining model.</span></span>  
  
7.  <span data-ttu-id="c6788-120">在 [**單一查詢輸入**] 對話方塊中，按一下 [排班] 的資料列，然後選取 [*午夜*]。</span><span class="sxs-lookup"><span data-stu-id="c6788-120">In the **Singleton Query Input** dialog box, click the row for Shift, and then select *midnight*.</span></span>  
  
8.  <span data-ttu-id="c6788-121">按一下 [Lvl 2] 運算子的資料列，然後輸入 `6` 。</span><span class="sxs-lookup"><span data-stu-id="c6788-121">Click the row for Lvl 2 Operators, and type `6`.</span></span>  
  
9. <span data-ttu-id="c6788-122">在 [**採礦模型預測**] 索引標籤的下半部，按一下方格中的第一個資料列。</span><span class="sxs-lookup"><span data-stu-id="c6788-122">In the bottom half of the **Mining Model Prediction** tab, click the first row in the grid.</span></span>  
  
10. <span data-ttu-id="c6788-123">在 [**源**資料行] 中，按一下向下箭號，然後選取 [**預測函數**]。</span><span class="sxs-lookup"><span data-stu-id="c6788-123">In the **Source** column, click the down arrow, and select **Prediction function**.</span></span> <span data-ttu-id="c6788-124">在 [**欄位**] 資料行中，選取 [ **PredictHistogram**]。</span><span class="sxs-lookup"><span data-stu-id="c6788-124">In the **Field** column, select **PredictHistogram**.</span></span>  
  
     <span data-ttu-id="c6788-125">在 [**準則/引數**] 方塊中，您可以搭配此預測函數使用的引數清單會自動出現。</span><span class="sxs-lookup"><span data-stu-id="c6788-125">A list of arguments that you can use with this prediction function automatically appears in the **Criteria/Arguments** box.</span></span>  
  
11. <span data-ttu-id="c6788-126">將 [ServiceGrade] 資料行從 [**採礦模型**] 窗格中的資料行清單拖曳到 [**準則/引數**] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="c6788-126">Drag the ServiceGrade column from the list of columns in the **Mining Model** pane to the **Criteria/Arguments** box.</span></span>  
  
     <span data-ttu-id="c6788-127">資料行的名稱會自動插入做為引數。</span><span class="sxs-lookup"><span data-stu-id="c6788-127">The name of the column is automatically inserted as the argument.</span></span> <span data-ttu-id="c6788-128">您可以選擇任何可預測的屬性資料行，將其拖曳至此文字方塊中。</span><span class="sxs-lookup"><span data-stu-id="c6788-128">You can choose any predictable attribute column to drag into this text box.</span></span>  
  
12. <span data-ttu-id="c6788-129">在預測查詢產生器的右上角，按一下 [**切換到查詢結果**] 的按鈕。</span><span class="sxs-lookup"><span data-stu-id="c6788-129">Click the button **Switch to query results view**, in the upper corner of the Prediction Query Builder.</span></span>  
  
 <span data-ttu-id="c6788-130">結果應該會包含每個服務等級在這些輸入條件下可能產生的預測值，以及每個預測的支援和機率。</span><span class="sxs-lookup"><span data-stu-id="c6788-130">The expected results contain the possible predicted values for each service grade given these inputs, together with support and probability values for each prediction.</span></span> <span data-ttu-id="c6788-131">您可以隨時返回設計檢視並變更輸入，或加入更多輸入。</span><span class="sxs-lookup"><span data-stu-id="c6788-131">You can return to design view at any time and change the inputs, or add more inputs.</span></span>  
  
## <a name="creating-predictions-by-using-a-logistic-regression-model"></a><span data-ttu-id="c6788-132">使用羅吉斯迴歸模型建立預測</span><span class="sxs-lookup"><span data-stu-id="c6788-132">Creating Predictions by using a Logistic Regression Model</span></span>  
 <span data-ttu-id="c6788-133">如果您已經知道與商務問題相關的屬性，則可以使用羅吉斯迴歸模型，預測變更某些屬性後所造成的效果。</span><span class="sxs-lookup"><span data-stu-id="c6788-133">If you already know the attributes that are relevant to the business problem, you can use a logistic regression model to predict the effect of making changes in some attributes.</span></span> <span data-ttu-id="c6788-134">羅吉斯迴歸是一種統計方式，通常用於根據獨立變數 (例如財務計分) 中的變更來進行預測，例如，根據客戶人口統計來預測客戶行為。</span><span class="sxs-lookup"><span data-stu-id="c6788-134">Logistic regression is a statistical method that is commonly used to make predictions based on changes in independent variables: for example, it is used in financial scoring, to predict customer behavior based on customer demographics.</span></span>  
  
 <span data-ttu-id="c6788-135">在此工作中，您將學習如何建立用於預測的資料來源，然後進行預測以協助回答數個商務問題。</span><span class="sxs-lookup"><span data-stu-id="c6788-135">In this task, you will learn how to create a data source that will be used for predictions, and then make predictions to help answer several business questions.</span></span>  
  
### <a name="generating-data-used-for-bulk-prediction"></a><span data-ttu-id="c6788-136">產生用於大量預測的資料</span><span class="sxs-lookup"><span data-stu-id="c6788-136">Generating Data used for Bulk Prediction</span></span>  
 <span data-ttu-id="c6788-137">您可以利用許多方式提供輸入資料：例如，您可以從試算表匯入人員雇用層級，然後在模型中執行該資料，以預測下個月的服務品質。</span><span class="sxs-lookup"><span data-stu-id="c6788-137">There are many ways to provide input data: for example, you might import staffing levels from a spreadsheet, and run that data through the model to predict service quality for the next month.</span></span>  
  
 <span data-ttu-id="c6788-138">在這一課，您將使用資料來源檢視設計工具來建立具名查詢。</span><span class="sxs-lookup"><span data-stu-id="c6788-138">In this lesson, you will use the Data Source View designer to create a named query.</span></span> <span data-ttu-id="c6788-139">這個具名查詢是一個自訂 Transact-SQL 陳述式，可針對每個排班來計算排班操作員人數上限、接聽電話下限，以及所產生的平均問題數目。</span><span class="sxs-lookup"><span data-stu-id="c6788-139">This named query is a custom Transact-SQL statement that for each shift on the schedule calculates the maximum number of operators on staff, the minimum calls received, and the average number of issues that are generated.</span></span> <span data-ttu-id="c6788-140">然後您會將該資料聯結至採礦模型，進行有關一系列未來日期的預測。</span><span class="sxs-lookup"><span data-stu-id="c6788-140">You will then join that data to a mining model to make predictions about a series of upcoming dates.</span></span>  
  
##### <a name="to-generate-input-data-for-a-bulk-prediction-query"></a><span data-ttu-id="c6788-141">若要產生用於大量預測查詢的輸入資料</span><span class="sxs-lookup"><span data-stu-id="c6788-141">To generate input data for a bulk prediction query</span></span>  
  
1.  <span data-ttu-id="c6788-142">在方案總管中，以滑鼠右鍵按一下 [**資料來源視圖**]，然後選取 [**新增資料來源視圖**]。</span><span class="sxs-lookup"><span data-stu-id="c6788-142">In Solution Explorer, right-click **Data Source Views**, and then select **New Data Source View**.</span></span>  
  
2.  <span data-ttu-id="c6788-143">在 [資料來源 View wizard] 中，選取 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 做為資料來源，然後按 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="c6788-143">In the Data Source View wizard, select [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] as the data source, and then click **Next**.</span></span>  
  
3.  <span data-ttu-id="c6788-144">在 [**選取資料表和視圖**] 頁面上，按 **[下一步]** 而不選取任何資料表。</span><span class="sxs-lookup"><span data-stu-id="c6788-144">On the **Select Tables and Views** page, click **Next** without selecting any tables.</span></span>  
  
4.  <span data-ttu-id="c6788-145">在 [**正在完成嚮導]** 頁面上，輸入名稱 `Shifts` 。</span><span class="sxs-lookup"><span data-stu-id="c6788-145">On the **Completing the Wizard** page, type the name, `Shifts`.</span></span>  
  
     <span data-ttu-id="c6788-146">這個名稱會顯示在 [方案總管] 中，做為資料來源檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6788-146">This name will appear in Solution Explorer as the name of the data source view.</span></span>  
  
5.  <span data-ttu-id="c6788-147">以滑鼠右鍵按一下空白設計窗格，然後選取 [新增] [**指名的查詢**]。</span><span class="sxs-lookup"><span data-stu-id="c6788-147">Right-click the empty design pane, then select **New Named Query**.</span></span>  
  
6.  <span data-ttu-id="c6788-148">在 [**建立命名查詢**] 對話方塊中，針對 [**名稱**] 輸入 `Shifts for Call Center` 。</span><span class="sxs-lookup"><span data-stu-id="c6788-148">In the **Create Named Query** dialog box, for **Name**, type `Shifts for Call Center`.</span></span>  
  
     <span data-ttu-id="c6788-149">這個名稱會顯示在 [資料來源檢視設計師] 中，但只會做為具名查詢的名稱。</span><span class="sxs-lookup"><span data-stu-id="c6788-149">This name will appear in Data Source View designer only as the name of the named query.</span></span>  
  
7.  <span data-ttu-id="c6788-150">將下列查詢陳述式貼到對話方塊下半部的 SQL 文字窗格中。</span><span class="sxs-lookup"><span data-stu-id="c6788-150">Paste the following query statement into the SQL text pane in the lower half of the dialog box.</span></span>  
  
    ```  
    SELECT DISTINCT WageType, Shift,   
    AVG(Orders) as AvgOrders, MIN(Orders) as MinOrders, MAX(Orders) as MaxOrders,  
    AVG(Calls) as AvgCalls, MIN(Calls) as MinCalls, MAX(Calls) as MaxCalls,  
    AVG(LevelTwoOperators) as AvgOperators, MIN(LevelTwoOperators) as MinOperators, MAX(LevelTwoOperators) as MaxOperators,  
    AVG(IssuesRaised) as AvgIssues, MIN(IssuesRaised) as MinIssues, MAX(IssuesRaised) as MaxIssues  
    FROM dbo.FactCallCenter  
    GROUP BY Shift, WageType  
    ```  
  
8.  <span data-ttu-id="c6788-151">在設計窗格中，以滑鼠右鍵按一下資料表，再按 [撥接中心]，然後選取 [**流覽資料**] 來預覽 t-SQL 查詢所傳回的資料。</span><span class="sxs-lookup"><span data-stu-id="c6788-151">In the design pane, right-click the table, Shifts for Call Center, and select **Explore Data** to preview the data as returned by the T-SQL query.</span></span>  
  
9. <span data-ttu-id="c6788-152">以滑鼠右鍵按一下索引標籤，將\*\* (設計) ]，\*\* 然後按一下 [**儲存**] 以儲存新的資料來源視圖定義。</span><span class="sxs-lookup"><span data-stu-id="c6788-152">Right-click the tab, **Shifts.dsv (Design),** and then click **Save** to save the new data source view definition.</span></span>  
  
### <a name="predicting-service-metrics-for-each-shift"></a><span data-ttu-id="c6788-153">預測每個排班的服務標準</span><span class="sxs-lookup"><span data-stu-id="c6788-153">Predicting Service Metrics for Each Shift</span></span>  
 <span data-ttu-id="c6788-154">現在您已經為每個排班產生一些值，您將使用這些值做為您所建立之羅吉斯迴歸模型的輸入，以產生可用於商務計畫的一些預測。</span><span class="sxs-lookup"><span data-stu-id="c6788-154">Now that you have generated some values for each shift, you will use those values as input to the logistic regression model that you built, to generate some predictions that can be used in business planning.</span></span>  
  
##### <a name="to-use-the-new-dsv-as-input-to-a-prediction-query"></a><span data-ttu-id="c6788-155">若要使用新的 DSV 做為預測查詢的輸入</span><span class="sxs-lookup"><span data-stu-id="c6788-155">To use the new DSV as input to a prediction query</span></span>  
  
1.  <span data-ttu-id="c6788-156">在 [資料採礦設計師] 中，按一下 [**採礦模型預測**] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="c6788-156">In Data Mining Designer, click the **Mining Model Prediction** tab.</span></span>  
  
2.  <span data-ttu-id="c6788-157">在 [**採礦模型**] 窗格中，按一下 [**選取模型**]，然後從可用的模型清單中選擇 [撥接中心-LR]。</span><span class="sxs-lookup"><span data-stu-id="c6788-157">In the **Mining Model** pane, click **Select Model**, and choose Call Center - LR from the list of available models.</span></span>  
  
3.  <span data-ttu-id="c6788-158">從 [**採礦模型**] 功能表中，清除 [**單一查詢**] 選項。</span><span class="sxs-lookup"><span data-stu-id="c6788-158">From the **Mining Model** menu, clear the option, **Singleton Query**.</span></span> <span data-ttu-id="c6788-159">此時會出現一個警告，告知您將會失去單一查詢輸入。</span><span class="sxs-lookup"><span data-stu-id="c6788-159">A warning tells you that the singleton query inputs will be lost.</span></span> <span data-ttu-id="c6788-160">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="c6788-160">Click **OK**.</span></span>  
  
     <span data-ttu-id="c6788-161">[**單一查詢輸入**] 對話方塊會取代為 [\*\*選取輸入資料表 (s) \*\* ] 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c6788-161">The **Singleton Query Input** dialog box is replaced with the **Select Input Table(s)** dialog box.</span></span>  
  
4.  <span data-ttu-id="c6788-162">按一下 [選取案例資料表] \*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6788-162">Click **Select Case Table**.</span></span>  
  
5.  <span data-ttu-id="c6788-163">在 [**選取資料表**] 對話方塊中，從資料來源清單中 selectShifts。</span><span class="sxs-lookup"><span data-stu-id="c6788-163">In the **Select Table** dialog box, selectShifts from the list of data sources.</span></span> <span data-ttu-id="c6788-164">在 [**資料表/視圖名稱**] 清單中，選取 [撥接中心的位移] (它可能會自動選取) ]，然後按一下 **[確定]。**</span><span class="sxs-lookup"><span data-stu-id="c6788-164">In the **Table/View name** list, select Shifts for Call Center (it might be automatically selected), and then click **OK.**</span></span>  
  
     <span data-ttu-id="c6788-165">[**採礦模型預測**] 設計介面會更新，以顯示根據輸入資料和模型中的資料行名稱和資料類型所建立的對應。</span><span class="sxs-lookup"><span data-stu-id="c6788-165">The **Mining Model Prediction** design surface is updated to show mappings that are created based on the names and data types of columns in the input data and in the model.</span></span>  
  
6.  <span data-ttu-id="c6788-166">以滑鼠右鍵按一下其中一條聯結線，然後選取 [**修改連接**]。</span><span class="sxs-lookup"><span data-stu-id="c6788-166">Right-click one of the join lines, and then select **Modify Connections**.</span></span>  
  
     <span data-ttu-id="c6788-167">在此對話方塊中，您可以清楚地看到對應的資料行以及沒有對應的資料行。</span><span class="sxs-lookup"><span data-stu-id="c6788-167">In this dialog box, you can see exactly which columns are mapped and which are not.</span></span> <span data-ttu-id="c6788-168">採礦模型包含 Calls、Orders、IssuesRaised，以及 LvlTwoOperators 的資料行，您可以將這些資料行對應到您在來源資料中根據這些資料行所建立的任何彙總。</span><span class="sxs-lookup"><span data-stu-id="c6788-168">The mining model contains columns for Calls, Orders, IssuesRaised, and LvlTwoOperators, which you can map to any of the aggregates that you created based on these columns in the source data.</span></span> <span data-ttu-id="c6788-169">在這個案例中，您將對應到平均值。</span><span class="sxs-lookup"><span data-stu-id="c6788-169">In this scenario, you will map to the averages.</span></span>  
  
7.  <span data-ttu-id="c6788-170">按一下 [LevelTwoOperators] 旁邊的空資料格，然後選取 [**撥接中心 AvgOperators**]。</span><span class="sxs-lookup"><span data-stu-id="c6788-170">Click the empty cell next to LevelTwoOperators, and select **Shifts for Call Center.AvgOperators**.</span></span>  
  
8.  <span data-ttu-id="c6788-171">按一下 [呼叫] 旁的空白資料格，選取 [ **AvgCalls] 的 [移位**]。</span><span class="sxs-lookup"><span data-stu-id="c6788-171">Click the empty cell next to Calls, select **Shifts for Call Center.AvgCalls**.</span></span> <span data-ttu-id="c6788-172">然後按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c6788-172">and then click **OK**.</span></span>  
  
##### <a name="to-create-the-predictions-for-each-shift"></a><span data-ttu-id="c6788-173">若要建立每個排班的預測</span><span class="sxs-lookup"><span data-stu-id="c6788-173">To create the predictions for each shift</span></span>  
  
1.  <span data-ttu-id="c6788-174">在**預測查詢**產生器下半部的方格中，按一下 [**來源**] 底下的空白資料格，然後選取 [撥接中心的轉移]。</span><span class="sxs-lookup"><span data-stu-id="c6788-174">In the grid at the bottom half of the **Prediction Query Builder**, click the empty cell under **Source,** and then select Shifts for Call Center.</span></span>  
  
2.  <span data-ttu-id="c6788-175">在 [**欄位**] 底下的空白資料格中，選取 [Shift]。</span><span class="sxs-lookup"><span data-stu-id="c6788-175">In the empty cell under **Field**, select Shift.</span></span>  
  
3.  <span data-ttu-id="c6788-176">按一下方格中的下一個空行，然後重複上述的程序，為 [薪資類型] 加入另一個資料列。</span><span class="sxs-lookup"><span data-stu-id="c6788-176">Click the next empty line in the grid and repeat the procedure described above to add another row for WageType.</span></span>  
  
4.  <span data-ttu-id="c6788-177">在方格中，按下一個空行。</span><span class="sxs-lookup"><span data-stu-id="c6788-177">Click the next empty line in the grid.</span></span> <span data-ttu-id="c6788-178">在 [**源**資料行] 中，選取 [**預測函數**]。</span><span class="sxs-lookup"><span data-stu-id="c6788-178">In the **Source** column, select **Prediction Function**.</span></span> <span data-ttu-id="c6788-179">在 [**欄位**] 資料行中，選取 [**預測**]。</span><span class="sxs-lookup"><span data-stu-id="c6788-179">In the **Field** column, select **Predict**.</span></span>  
  
5.  <span data-ttu-id="c6788-180">將 [ServiceGrade] 資料行從 [**採礦模型**] 窗格向下拖曳到方格中，然後拖曳至 [**準則/引數**] 資料格中。</span><span class="sxs-lookup"><span data-stu-id="c6788-180">Drag the column ServiceGrade from the **Mining Model** pane down to the grid, and into the **Criteria/Argument** cell.</span></span> <span data-ttu-id="c6788-181">在 [**別名**] 欄位中，輸入**預測的服務等級**。</span><span class="sxs-lookup"><span data-stu-id="c6788-181">In the **Alias** field, type **Predicted Service Grade**.</span></span>  
  
6.  <span data-ttu-id="c6788-182">在方格中，按下一個空行。</span><span class="sxs-lookup"><span data-stu-id="c6788-182">Click the next empty line in the grid.</span></span> <span data-ttu-id="c6788-183">在 [**源**資料行] 中，選取 [**預測函數**]。</span><span class="sxs-lookup"><span data-stu-id="c6788-183">In the **Source** column, select **Prediction Function**.</span></span> <span data-ttu-id="c6788-184">在 [**欄位**] 資料行中，選取 [ **[predictprobability]**]。</span><span class="sxs-lookup"><span data-stu-id="c6788-184">In the **Field** column, select **PredictProbability**.</span></span>  
  
7.  <span data-ttu-id="c6788-185">將 [ServiceGrade] 資料行從 [**採礦模型**] 窗格向下拖曳到方格中，然後拖曳至 [**準則/引數**] 資料格中。</span><span class="sxs-lookup"><span data-stu-id="c6788-185">Drag the column ServiceGrade from the **Mining Model** pane down to the grid, and into the **Criteria/Argument** cell.</span></span> <span data-ttu-id="c6788-186">在 [**別名**] 欄位中 **，輸入機率**。</span><span class="sxs-lookup"><span data-stu-id="c6788-186">In the **Alias** field, type **Probability**.</span></span>  
  
8.  <span data-ttu-id="c6788-187">按一下 [**切換到查詢結果檢視**] 以查看預測。</span><span class="sxs-lookup"><span data-stu-id="c6788-187">Click **Switch to query result view** to view the predictions.</span></span>  
  
 <span data-ttu-id="c6788-188">下表顯示每個排班的範例結果。</span><span class="sxs-lookup"><span data-stu-id="c6788-188">The following table shows sample results for each shift.</span></span>  
  
|<span data-ttu-id="c6788-189">Shift</span><span class="sxs-lookup"><span data-stu-id="c6788-189">Shift</span></span>|<span data-ttu-id="c6788-190">WageType</span><span class="sxs-lookup"><span data-stu-id="c6788-190">WageType</span></span>|<span data-ttu-id="c6788-191">預測的服務等級</span><span class="sxs-lookup"><span data-stu-id="c6788-191">Predicted Service Grade</span></span>|<span data-ttu-id="c6788-192">機率</span><span class="sxs-lookup"><span data-stu-id="c6788-192">Probability</span></span>|  
|-----------|--------------|-----------------------------|-----------------|  
|<span data-ttu-id="c6788-193">AM</span><span class="sxs-lookup"><span data-stu-id="c6788-193">AM</span></span>|<span data-ttu-id="c6788-194">假日</span><span class="sxs-lookup"><span data-stu-id="c6788-194">holiday</span></span>|<span data-ttu-id="c6788-195">0.165</span><span class="sxs-lookup"><span data-stu-id="c6788-195">0.165</span></span>|<span data-ttu-id="c6788-196">0.377520666</span><span class="sxs-lookup"><span data-stu-id="c6788-196">0.377520666</span></span>|  
|<span data-ttu-id="c6788-197">midnight</span><span class="sxs-lookup"><span data-stu-id="c6788-197">midnight</span></span>|<span data-ttu-id="c6788-198">假日</span><span class="sxs-lookup"><span data-stu-id="c6788-198">holiday</span></span>|<span data-ttu-id="c6788-199">0.105</span><span class="sxs-lookup"><span data-stu-id="c6788-199">0.105</span></span>|<span data-ttu-id="c6788-200">0.364105573</span><span class="sxs-lookup"><span data-stu-id="c6788-200">0.364105573</span></span>|  
|<span data-ttu-id="c6788-201">PM1</span><span class="sxs-lookup"><span data-stu-id="c6788-201">PM1</span></span>|<span data-ttu-id="c6788-202">假日</span><span class="sxs-lookup"><span data-stu-id="c6788-202">holiday</span></span>|<span data-ttu-id="c6788-203">0.165</span><span class="sxs-lookup"><span data-stu-id="c6788-203">0.165</span></span>|<span data-ttu-id="c6788-204">0.40056055</span><span class="sxs-lookup"><span data-stu-id="c6788-204">0.40056055</span></span>|  
|<span data-ttu-id="c6788-205">PM2</span><span class="sxs-lookup"><span data-stu-id="c6788-205">PM2</span></span>|<span data-ttu-id="c6788-206">假日</span><span class="sxs-lookup"><span data-stu-id="c6788-206">holiday</span></span>|<span data-ttu-id="c6788-207">0.165</span><span class="sxs-lookup"><span data-stu-id="c6788-207">0.165</span></span>|<span data-ttu-id="c6788-208">0.338532973</span><span class="sxs-lookup"><span data-stu-id="c6788-208">0.338532973</span></span>|  
|<span data-ttu-id="c6788-209">AM</span><span class="sxs-lookup"><span data-stu-id="c6788-209">AM</span></span>|<span data-ttu-id="c6788-210">weekday</span><span class="sxs-lookup"><span data-stu-id="c6788-210">weekday</span></span>|<span data-ttu-id="c6788-211">0.165</span><span class="sxs-lookup"><span data-stu-id="c6788-211">0.165</span></span>|<span data-ttu-id="c6788-212">0.370847617</span><span class="sxs-lookup"><span data-stu-id="c6788-212">0.370847617</span></span>|  
|<span data-ttu-id="c6788-213">midnight</span><span class="sxs-lookup"><span data-stu-id="c6788-213">midnight</span></span>|<span data-ttu-id="c6788-214">weekday</span><span class="sxs-lookup"><span data-stu-id="c6788-214">weekday</span></span>|<span data-ttu-id="c6788-215">0.08</span><span class="sxs-lookup"><span data-stu-id="c6788-215">0.08</span></span>|<span data-ttu-id="c6788-216">0.352999173</span><span class="sxs-lookup"><span data-stu-id="c6788-216">0.352999173</span></span>|  
|<span data-ttu-id="c6788-217">PM1</span><span class="sxs-lookup"><span data-stu-id="c6788-217">PM1</span></span>|<span data-ttu-id="c6788-218">weekday</span><span class="sxs-lookup"><span data-stu-id="c6788-218">weekday</span></span>|<span data-ttu-id="c6788-219">0.165</span><span class="sxs-lookup"><span data-stu-id="c6788-219">0.165</span></span>|<span data-ttu-id="c6788-220">0.317419177</span><span class="sxs-lookup"><span data-stu-id="c6788-220">0.317419177</span></span>|  
|<span data-ttu-id="c6788-221">PM2</span><span class="sxs-lookup"><span data-stu-id="c6788-221">PM2</span></span>|<span data-ttu-id="c6788-222">weekday</span><span class="sxs-lookup"><span data-stu-id="c6788-222">weekday</span></span>|<span data-ttu-id="c6788-223">0.105</span><span class="sxs-lookup"><span data-stu-id="c6788-223">0.105</span></span>|<span data-ttu-id="c6788-224">0.311672027</span><span class="sxs-lookup"><span data-stu-id="c6788-224">0.311672027</span></span>|  
  
### <a name="predicting-the-effect-of-reduced-response-time-on-service-grade"></a><span data-ttu-id="c6788-225">預測回應時間縮短對於服務等級的影響</span><span class="sxs-lookup"><span data-stu-id="c6788-225">Predicting the Effect of Reduced Response Time on Service Grade</span></span>  
 <span data-ttu-id="c6788-226">您已經為每個排班產生一些平均值，並且使用這些值做為羅吉斯迴歸模型的輸入。</span><span class="sxs-lookup"><span data-stu-id="c6788-226">You generated some average values for each shift, and used those values as input to the logistic regression model.</span></span> <span data-ttu-id="c6788-227">不過，因為商務目標是要將放棄率保持在 0.00-0.05 的範圍內，這樣結果並不令人滿意。</span><span class="sxs-lookup"><span data-stu-id="c6788-227">However, given that the business objective is to keep abandon rate within the range 0.00-0.05, the results are not encouraging.</span></span>  
  
 <span data-ttu-id="c6788-228">根據原始的模型看來，回應時間對於服務等級具有顯著的影響，因此營業小組決定執行一些預測，評估降低回應來電的平均時間是否可以提升服務品質。</span><span class="sxs-lookup"><span data-stu-id="c6788-228">Therefore, based on the original model, which showed a strong influence of response time on service grade, the Operations team decides to run some predictions to assess whether reducing the average time for responding to calls might improve service quality.</span></span> <span data-ttu-id="c6788-229">例如，如果您將來電回應時間縮短為目前來電回應時間的 90% 甚至 80%，服務等級值會發生什麼情況？</span><span class="sxs-lookup"><span data-stu-id="c6788-229">For example, if you cut the call response time to 90 percent or even to 80 percent of the current call response time, what would happen to service grade values?</span></span>  
  
 <span data-ttu-id="c6788-230">建立計算每個排班之平均回應時間的資料來源檢視 (DSV)，然後新增資料行來計算該平均回應時間的 80% 或 90% 是相當容易的工作。</span><span class="sxs-lookup"><span data-stu-id="c6788-230">It is easy to create a data source view (DSV) that calculates the average response times for each shift, and then add columns that calculate 80% or 90% of the average response time.</span></span> <span data-ttu-id="c6788-231">接著，您就可以使用 DSV 做為模型的輸入。</span><span class="sxs-lookup"><span data-stu-id="c6788-231">You can then use the DSV as input to the model.</span></span>  
  
 <span data-ttu-id="c6788-232">雖然這裡未顯示確切的步驟，但下表會比較當您將回應時間縮短為目前回應時間的 80% 或 90% 時，對服務等級造成的影響。</span><span class="sxs-lookup"><span data-stu-id="c6788-232">Although the exact steps are not shown here, the following table compares the effects on service grade when you reduce response times to 80% or to 90% of current response times.</span></span>  
  
 <span data-ttu-id="c6788-233">您可以從這些結果得出結論，也就是針對目標排班，應該將回應時間縮短為目前速率的 90%，以改進服務品質。</span><span class="sxs-lookup"><span data-stu-id="c6788-233">From these results, you might conclude that on targeted shifts you should reduce the response time to 90 percent of the current rate in order to improve service quality.</span></span>  
  
|<span data-ttu-id="c6788-234">排班、薪資和星期幾</span><span class="sxs-lookup"><span data-stu-id="c6788-234">Shift, wage, and day</span></span>|<span data-ttu-id="c6788-235">使用目前的平均回應時間時，預測的服務品質</span><span class="sxs-lookup"><span data-stu-id="c6788-235">Predicted service quality with current average response time</span></span>|<span data-ttu-id="c6788-236">回應時間縮短為 90% 時，預測的服務品質</span><span class="sxs-lookup"><span data-stu-id="c6788-236">Predicted service quality with 90 percent reduction in response time</span></span>|<span data-ttu-id="c6788-237">回應時間縮短為 80% 時，預測的服務品質</span><span class="sxs-lookup"><span data-stu-id="c6788-237">Predicted service quality with 80 percent reduction in response time</span></span>|  
|--------------------------|------------------------------------------------------------------|--------------------------------------------------------------------------|--------------------------------------------------------------------------|  
|<span data-ttu-id="c6788-238">假日 AM</span><span class="sxs-lookup"><span data-stu-id="c6788-238">Holiday AM</span></span>|<span data-ttu-id="c6788-239">0.165</span><span class="sxs-lookup"><span data-stu-id="c6788-239">0.165</span></span>|<span data-ttu-id="c6788-240">0.05</span><span class="sxs-lookup"><span data-stu-id="c6788-240">0.05</span></span>|<span data-ttu-id="c6788-241">0.05</span><span class="sxs-lookup"><span data-stu-id="c6788-241">0.05</span></span>|  
|<span data-ttu-id="c6788-242">假日 PM1</span><span class="sxs-lookup"><span data-stu-id="c6788-242">Holiday PM1</span></span>|<span data-ttu-id="c6788-243">0.05</span><span class="sxs-lookup"><span data-stu-id="c6788-243">0.05</span></span>|<span data-ttu-id="c6788-244">0.05</span><span class="sxs-lookup"><span data-stu-id="c6788-244">0.05</span></span>|<span data-ttu-id="c6788-245">0.05</span><span class="sxs-lookup"><span data-stu-id="c6788-245">0.05</span></span>|  
|<span data-ttu-id="c6788-246">假日 Midnight</span><span class="sxs-lookup"><span data-stu-id="c6788-246">Holiday Midnight</span></span>|<span data-ttu-id="c6788-247">0.165</span><span class="sxs-lookup"><span data-stu-id="c6788-247">0.165</span></span>|<span data-ttu-id="c6788-248">0.05</span><span class="sxs-lookup"><span data-stu-id="c6788-248">0.05</span></span>|<span data-ttu-id="c6788-249">0.05</span><span class="sxs-lookup"><span data-stu-id="c6788-249">0.05</span></span>|  
  
 <span data-ttu-id="c6788-250">您還可以在此模型上建立各種其他的預測查詢。</span><span class="sxs-lookup"><span data-stu-id="c6788-250">There are a variety of other prediction queries that you can create on this model.</span></span> <span data-ttu-id="c6788-251">例如，您可以預測需要多少位操作員，才能達到特定的服務等級或者回應特定的來電數目。</span><span class="sxs-lookup"><span data-stu-id="c6788-251">For example, you could predict how many operators are required to meet a certain service level or to respond to a certain number of incoming calls.</span></span> <span data-ttu-id="c6788-252">因為在羅吉斯迴歸模型中可以加入多個輸出，所以您可以輕鬆地試驗不同的獨立變數與結果，而不需要建立許多個別的模型。</span><span class="sxs-lookup"><span data-stu-id="c6788-252">Because you can include multiple outputs in a logistic regression model, it is easy to experiment with different independent variables and outcomes without having to create many separate models.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6788-253">備註</span><span class="sxs-lookup"><span data-stu-id="c6788-253">Remarks</span></span>  
 <span data-ttu-id="c6788-254">適用於 Excel 2007 的資料採礦增益集提供羅吉斯迴歸精靈，讓您輕鬆回應複雜的問題，例如，需要多少位二級操作員，才能將某個排班的服務等級提升至目標等級。</span><span class="sxs-lookup"><span data-stu-id="c6788-254">The Data Mining Add-Ins for Excel 2007 provide logistic regression wizards that make it easy to answer complex questions, such as how many Level Two Operators would be required to improve service grade to a target level for a specific shift.</span></span> <span data-ttu-id="c6788-255">您可以免費下載資料採礦增益集，其中包含類神經網路或羅吉斯迴歸演算法的精靈。</span><span class="sxs-lookup"><span data-stu-id="c6788-255">The data mining add-ins are a free download, and include wizards that are based on the neural network or logistic regression algorithms.</span></span> <span data-ttu-id="c6788-256">如需詳細資訊，請參閱下列連結：</span><span class="sxs-lookup"><span data-stu-id="c6788-256">For more information, see the following links:</span></span>  
  
-   <span data-ttu-id="c6788-257">[SQL Server 2005 適用于 Office 2007 的資料採礦增益集](https://www.microsoft.com/sql/technologies/dm/addins.mspx)：目標搜尋和 What If 案例分析</span><span class="sxs-lookup"><span data-stu-id="c6788-257">[SQL Server 2005 Data Mining Add-Ins for Office 2007](https://www.microsoft.com/sql/technologies/dm/addins.mspx): Goal Seek and What If Scenario Analysis</span></span>  
  
-   <span data-ttu-id="c6788-258">[SQL Server 2008 適用于 Office 2007 的資料採礦增益集](https://go.microsoft.com/fwlink/?LinkID=117790)：目標搜尋案例分析、What If 案例分析，以及預測計算器</span><span class="sxs-lookup"><span data-stu-id="c6788-258">[SQL Server 2008 Data Mining Add-Ins for Office 2007](https://go.microsoft.com/fwlink/?LinkID=117790): Goal Seek Scenario Analysis, What If Scenario Analysis, and Prediction Calculator</span></span>  
  
## <a name="conclusion"></a><span data-ttu-id="c6788-259">結論</span><span class="sxs-lookup"><span data-stu-id="c6788-259">Conclusion</span></span>  
 <span data-ttu-id="c6788-260">您已經學到如何建立、自訂與解譯以 Microsoft 類神經網路演算法和 Microsoft 羅吉斯迴歸演算法為基礎的採礦模型。</span><span class="sxs-lookup"><span data-stu-id="c6788-260">You have learned to create, customize, and interpret mining models that are based on the Microsoft Neural Network algorithm and the Microsoft Logistic Regression algorithm.</span></span> <span data-ttu-id="c6788-261">這些模型類型相當複雜，在分析方式上也可以有無限的變化，因此可能相當複雜且難以上手。</span><span class="sxs-lookup"><span data-stu-id="c6788-261">These model types are sophisticated and permit almost infinite variety in analysis, and therefore can be complex and difficult to master.</span></span>  
  
 <span data-ttu-id="c6788-262">不過，這些演算法會逐一查看許多因數組合，並自動識別最強的互相關聯，為洞察力提供統計資料的支援，但在使用 Transact-SQL 或甚至 PowerPivot 手動瀏覽資料時難以發現此洞察力。</span><span class="sxs-lookup"><span data-stu-id="c6788-262">However, these algorithms can iterate through many combinations of factors and automatically identify the strongest correlations, providing statistical support for insights that would be very difficult to discover through manual exploration of data using Transact-SQL or even PowerPivot.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6788-263">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c6788-263">See Also</span></span>  
 <span data-ttu-id="c6788-264">[羅吉斯回歸模型查詢範例](../../2014/analysis-services/data-mining/logistic-regression-model-query-examples.md) </span><span class="sxs-lookup"><span data-stu-id="c6788-264">[Logistic Regression Model Query Examples](../../2014/analysis-services/data-mining/logistic-regression-model-query-examples.md) </span></span>  
 <span data-ttu-id="c6788-265">[Microsoft 羅吉斯回歸演算法](../../2014/analysis-services/data-mining/microsoft-logistic-regression-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="c6788-265">[Microsoft Logistic Regression Algorithm](../../2014/analysis-services/data-mining/microsoft-logistic-regression-algorithm.md) </span></span>  
 <span data-ttu-id="c6788-266">[Microsoft 類神經網路演算法](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm.md) </span><span class="sxs-lookup"><span data-stu-id="c6788-266">[Microsoft Neural Network Algorithm](../../2014/analysis-services/data-mining/microsoft-neural-network-algorithm.md) </span></span>  
 [<span data-ttu-id="c6788-267">類神經網路模型查詢範例</span><span class="sxs-lookup"><span data-stu-id="c6788-267">Neural Network Model Query Examples</span></span>](../../2014/analysis-services/data-mining/neural-network-model-query-examples.md)  
  
  
