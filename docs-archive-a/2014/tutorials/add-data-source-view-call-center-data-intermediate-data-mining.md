---
title: 加入撥打電話中心資料的資料來源視圖 (中繼資料採礦教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: a448e7e4-dbd1-4d31-90bc-4d4a1c23b352
author: minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 6d3d9aa3153b39b9ef7f4a92af20e0e8791780bc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704521"
---
# <a name="adding-a-data-source-view-for-call-center-data-intermediate-data-mining-tutorial"></a><span data-ttu-id="3ff17-102">加入用於撥接中心資料的資料來源檢視 (中繼資料採礦教學課程)</span><span class="sxs-lookup"><span data-stu-id="3ff17-102">Adding a Data Source View for Call Center Data (Intermediate Data Mining Tutorial)</span></span>
  <span data-ttu-id="3ff17-103">在這項工作中，您將加入資料來源檢視，用來存取撥接中心資料。</span><span class="sxs-lookup"><span data-stu-id="3ff17-103">In this task, you add a data source view that will be used to access the call center data.</span></span> <span data-ttu-id="3ff17-104">相同的資料將用於建立用來進行探索的初步類神經網路模型，以及用於提出建議的羅吉斯迴歸模型。</span><span class="sxs-lookup"><span data-stu-id="3ff17-104">The same data will be used to build both the initial neural network model for exploration, and the logistic regression model that you will use to make recommendations.</span></span>  
  
 <span data-ttu-id="3ff17-105">您也將會使用資料來源檢視設計工具，為週中的日加入一個資料行。</span><span class="sxs-lookup"><span data-stu-id="3ff17-105">You will also use the Data Source View Designer to add a column for the day of the week.</span></span> <span data-ttu-id="3ff17-106">因為雖然來源資料依日期追蹤撥接中心的資料，但是您根據經驗得知，依據當天是工作日或週末，在通話量和服務品質方面有重複的模式。</span><span class="sxs-lookup"><span data-stu-id="3ff17-106">That is because, although the source data tracks call center data by dates, your experience tells you that there are recurring patterns both in terms of call volume and service quality, depending on whether the day is a weekend or a weekday.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="3ff17-107">程序</span><span class="sxs-lookup"><span data-stu-id="3ff17-107">Procedures</span></span>  
  
#### <a name="to-add-a-data-source-view"></a><span data-ttu-id="3ff17-108">若要加入資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="3ff17-108">To add a data source view</span></span>  
  
1.  <span data-ttu-id="3ff17-109">在**方案總管**中，以滑鼠右鍵按一下 [**資料來源視圖**]，然後選取 [**新增資料來源視圖**]。</span><span class="sxs-lookup"><span data-stu-id="3ff17-109">In **Solution Explorer**, right-click **Data Source Views**, and select **New Data Source View**.</span></span>  
  
     <span data-ttu-id="3ff17-110">此時會開啟資料來源檢視精靈。</span><span class="sxs-lookup"><span data-stu-id="3ff17-110">The Data Source View Wizard opens.</span></span>  
  
2.  <span data-ttu-id="3ff17-111">在 [歡迎使用資料來源檢視精靈]  頁面上，按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="3ff17-111">On the **Welcome to the Data Source View Wizard** page, click **Next**.</span></span>  
  
3.  <span data-ttu-id="3ff17-112">在 [**選取資料來源**] 頁面的 [**關聯式資料來源**] 底下，選取 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 資料來源。</span><span class="sxs-lookup"><span data-stu-id="3ff17-112">On the **Select a Data Source** page, under **Relational data sources**, select the [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] data source.</span></span> <span data-ttu-id="3ff17-113">如果您沒有此資料來源，請參閱[基本資料採礦教學](../../2014/tutorials/basic-data-mining-tutorial.md)課程。</span><span class="sxs-lookup"><span data-stu-id="3ff17-113">If you do not have this data source, see [Basic Data Mining Tutorial](../../2014/tutorials/basic-data-mining-tutorial.md).</span></span> <span data-ttu-id="3ff17-114">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="3ff17-114">Click **Next**.</span></span>  
  
4.  <span data-ttu-id="3ff17-115">在 [**選取資料表和資料檢視]** 頁面上，選取下列資料表，然後按一下向右箭號，將它加入至資料來源視圖：</span><span class="sxs-lookup"><span data-stu-id="3ff17-115">On the **Select Tables and Views** page, select the following table and then click the right arrow to add it to the data source view:</span></span>  
  
    -   <span data-ttu-id="3ff17-116">**FactCallCenter (dbo)**</span><span class="sxs-lookup"><span data-stu-id="3ff17-116">**FactCallCenter (dbo)**</span></span>  
  
    -   <span data-ttu-id="3ff17-117">**DimDate**</span><span class="sxs-lookup"><span data-stu-id="3ff17-117">**DimDate**</span></span>  
  
5.  <span data-ttu-id="3ff17-118">按 [下一步] 。</span><span class="sxs-lookup"><span data-stu-id="3ff17-118">Click **Next**.</span></span>  
  
6.  <span data-ttu-id="3ff17-119">在 [**正在完成嚮導]** 頁面上，預設會將 [資料來源] 視圖命名為 [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3ff17-119">On the **Completing the Wizard** page, by default the data source view is named [!INCLUDE[ssAWDWsp](../includes/ssawdwsp-md.md)].</span></span> <span data-ttu-id="3ff17-120">將名稱變更為**CallCenter**，然後按一下 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="3ff17-120">Change the name to **CallCenter**, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="3ff17-121">[資料來源視圖設計工具] 隨即開啟，以顯示 [ **CallCenter** ] 資料來源視圖。</span><span class="sxs-lookup"><span data-stu-id="3ff17-121">Data Source View Designer opens to display the **CallCenter** data source view.</span></span>  
  
7.  <span data-ttu-id="3ff17-122">以滑鼠右鍵按一下 [資料來源] 視圖窗格內，然後選取 [**新增/移除資料表]**。</span><span class="sxs-lookup"><span data-stu-id="3ff17-122">Right-click inside the Data Source View pane, and select **Add/Remove Tables**.</span></span> <span data-ttu-id="3ff17-123">選取資料表**DimDate** ，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="3ff17-123">Select the table, **DimDate** and click **OK**.</span></span>  
  
     <span data-ttu-id="3ff17-124">應該在每個資料表的資料行之間自動加入關聯性 `DateKey` 。</span><span class="sxs-lookup"><span data-stu-id="3ff17-124">A relationship should be automatically added between the `DateKey` columns in each table.</span></span> <span data-ttu-id="3ff17-125">您將使用此關聯性從**DimDate**資料表取得**EnglishDayNameOfWeek**資料行，並在您的模型中使用它。</span><span class="sxs-lookup"><span data-stu-id="3ff17-125">You will use this relationship to get the column, **EnglishDayNameOfWeek**, from the **DimDate** table and use it in your model.</span></span>  
  
8.  <span data-ttu-id="3ff17-126">在 [資料來源視圖設計工具] 中，以滑鼠右鍵按一下資料表**FactCallCenter**，然後選取 [新增] [**命名計算**]。</span><span class="sxs-lookup"><span data-stu-id="3ff17-126">In the Data Source View designer, right-click the table, **FactCallCenter**, and select **New Named Calculation**.</span></span>  
  
     <span data-ttu-id="3ff17-127">在 [**建立命名計算**] 對話方塊中，輸入下列值：</span><span class="sxs-lookup"><span data-stu-id="3ff17-127">In the **Create Named Calculation** dialog box, type the following values:</span></span>  
  
    |||  
    |-|-|  
    |<span data-ttu-id="3ff17-128">**資料行名稱**</span><span class="sxs-lookup"><span data-stu-id="3ff17-128">**Column name**</span></span>|<span data-ttu-id="3ff17-129">DayOfWeek</span><span class="sxs-lookup"><span data-stu-id="3ff17-129">DayOfWeek</span></span>|  
    |<span data-ttu-id="3ff17-130">**說明**</span><span class="sxs-lookup"><span data-stu-id="3ff17-130">**Description**</span></span>|<span data-ttu-id="3ff17-131">從 DimDate 資料表取得週中的日</span><span class="sxs-lookup"><span data-stu-id="3ff17-131">Get day of week from DimDate table</span></span>|  
    |<span data-ttu-id="3ff17-132">**運算式**</span><span class="sxs-lookup"><span data-stu-id="3ff17-132">**Expression**</span></span>|`(SELECT EnglishDayNameOfWeek AS DayOfWeek FROM DimDate where FactCallCenter.DateKey = DimDate.DateKey)`|  
  
     <span data-ttu-id="3ff17-133">若要確認運算式是否會建立您所需的資料，請以滑鼠右鍵按一下資料表**FactCallCenter**，然後選取 [**流覽資料**]。</span><span class="sxs-lookup"><span data-stu-id="3ff17-133">To verify that the expression creates the data you need, right-click the table **FactCallCenter**, and then select **Explore Data**.</span></span>  
  
9. <span data-ttu-id="3ff17-134">花一分鐘檢閱可用的資料，以便了解資料在資料採礦中的用法：</span><span class="sxs-lookup"><span data-stu-id="3ff17-134">Take a minute to review the data that is available, so that you can understand how it is used in data mining:</span></span>  
  
|<span data-ttu-id="3ff17-135">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="3ff17-135">Column name</span></span>|<span data-ttu-id="3ff17-136">包含</span><span class="sxs-lookup"><span data-stu-id="3ff17-136">Contains</span></span>|  
|-----------------|--------------|  
|<span data-ttu-id="3ff17-137">FactCallCenterID</span><span class="sxs-lookup"><span data-stu-id="3ff17-137">FactCallCenterID</span></span>|<span data-ttu-id="3ff17-138">當資料匯入資料倉儲時建立的任意索引鍵。</span><span class="sxs-lookup"><span data-stu-id="3ff17-138">An arbitrary key created when the data was imported to the data warehouse.</span></span><br /><br /> <span data-ttu-id="3ff17-139">此資料行會識別唯一記錄，應該做為資料採礦模型的案例索引鍵。</span><span class="sxs-lookup"><span data-stu-id="3ff17-139">This column identifies unique records and should be used as the case key for the data mining model.</span></span>|  
|<span data-ttu-id="3ff17-140">DateKey</span><span class="sxs-lookup"><span data-stu-id="3ff17-140">DateKey</span></span>|<span data-ttu-id="3ff17-141">撥接中心作業的日期，以整數表示。</span><span class="sxs-lookup"><span data-stu-id="3ff17-141">The date of the call center operation, expressed as an integer.</span></span> <span data-ttu-id="3ff17-142">資料倉儲中通常使用整數日期索引鍵，但是如果您要依日期值進行分組，可能想要取得日期/時間格式的日期。</span><span class="sxs-lookup"><span data-stu-id="3ff17-142">Integer date keys are often used in data warehouses, but you might want to obtain the date in date/time format if you were going to group by date values.</span></span><br /><br /> <span data-ttu-id="3ff17-143">請注意，日期不是唯一的，因為廠商會在作業的每一天，為每個排班提供一個個別的報表。</span><span class="sxs-lookup"><span data-stu-id="3ff17-143">Note that dates are not unique because the vendor provides a separate report for each shift in each day of operation.</span></span>|  
|<span data-ttu-id="3ff17-144">WageType</span><span class="sxs-lookup"><span data-stu-id="3ff17-144">WageType</span></span>|<span data-ttu-id="3ff17-145">表示該日期為工作日、週末或假日。</span><span class="sxs-lookup"><span data-stu-id="3ff17-145">Indicates whether the day was a weekday, a weekend, or a holiday.</span></span><br /><br /> <span data-ttu-id="3ff17-146">客戶服務在週末與工作日的品質可能有所差異，因此您將使用此資料行做為輸入。</span><span class="sxs-lookup"><span data-stu-id="3ff17-146">It is possible that there is a difference in quality of customer service on weekends vs. weekdays so you will use this column as an input.</span></span>|  
|<span data-ttu-id="3ff17-147">Shift</span><span class="sxs-lookup"><span data-stu-id="3ff17-147">Shift</span></span>|<span data-ttu-id="3ff17-148">表示記錄電話當時的排班。</span><span class="sxs-lookup"><span data-stu-id="3ff17-148">Indicates the shift for which calls are recorded.</span></span> <span data-ttu-id="3ff17-149">此撥接中心將工作日分成四個排班：AM、PM1、PM2，以及 Midnight。</span><span class="sxs-lookup"><span data-stu-id="3ff17-149">This call center divides the working day into four shifts: AM, PM1, PM2, and Midnight.</span></span><br /><br /> <span data-ttu-id="3ff17-150">排班可能對客戶服務品質造成影響，因此您將它做為輸入。</span><span class="sxs-lookup"><span data-stu-id="3ff17-150">It is possible that the shift influences the quality of customer service so you will use this as an input.</span></span>|  
|<span data-ttu-id="3ff17-151">LevelOneOperators</span><span class="sxs-lookup"><span data-stu-id="3ff17-151">LevelOneOperators</span></span>|<span data-ttu-id="3ff17-152">表示待命的一級操作員數目。</span><span class="sxs-lookup"><span data-stu-id="3ff17-152">Indicates the number of Level 1 operators on duty.</span></span><br /><br /> <span data-ttu-id="3ff17-153">撥接中心員工從一級開始，因此這些員工資歷較淺。</span><span class="sxs-lookup"><span data-stu-id="3ff17-153">Call center employees start at Level 1 so these employees are less experienced.</span></span>|  
|<span data-ttu-id="3ff17-154">LevelTwoOperators</span><span class="sxs-lookup"><span data-stu-id="3ff17-154">LevelTwoOperators</span></span>|<span data-ttu-id="3ff17-155">表示待命的二級操作員數目。</span><span class="sxs-lookup"><span data-stu-id="3ff17-155">Indicates the number of Level 2 operators on duty.</span></span><br /><br /> <span data-ttu-id="3ff17-156">員工必須記錄特定的服務時數才能限定為二級操作員。</span><span class="sxs-lookup"><span data-stu-id="3ff17-156">An employee must log a certain number of service hours to qualify as a Level 2 operator.</span></span>|  
|<span data-ttu-id="3ff17-157">TotalOperators</span><span class="sxs-lookup"><span data-stu-id="3ff17-157">TotalOperators</span></span>|<span data-ttu-id="3ff17-158">排班期間出現的操作員總數。</span><span class="sxs-lookup"><span data-stu-id="3ff17-158">The total number of operators present during the shift.</span></span>|  
|<span data-ttu-id="3ff17-159">呼叫</span><span class="sxs-lookup"><span data-stu-id="3ff17-159">Calls</span></span>|<span data-ttu-id="3ff17-160">排班期間接到的電話通數。</span><span class="sxs-lookup"><span data-stu-id="3ff17-160">Number of calls received during the shift.</span></span>|  
|<span data-ttu-id="3ff17-161">AutomaticResponses</span><span class="sxs-lookup"><span data-stu-id="3ff17-161">AutomaticResponses</span></span>|<span data-ttu-id="3ff17-162">完全由自動化電話處理 (互動式語音應答，也就是 IVR) 所處理的電話通數。</span><span class="sxs-lookup"><span data-stu-id="3ff17-162">The number of calls that were handled entirely by automated call processing (Interactive Voice Response, or IVR).</span></span>|  
|<span data-ttu-id="3ff17-163">訂單</span><span class="sxs-lookup"><span data-stu-id="3ff17-163">Orders</span></span>|<span data-ttu-id="3ff17-164">來自電話的訂單數目。</span><span class="sxs-lookup"><span data-stu-id="3ff17-164">The number of orders that resulted from calls.</span></span>|  
|<span data-ttu-id="3ff17-165">IssuesRaised</span><span class="sxs-lookup"><span data-stu-id="3ff17-165">IssuesRaised</span></span>|<span data-ttu-id="3ff17-166">由電話產生、需要後續追蹤的問題數目。</span><span class="sxs-lookup"><span data-stu-id="3ff17-166">The number of issues requiring follow-up that were generated by calls.</span></span>|  
|<span data-ttu-id="3ff17-167">AverageTimePerIssue</span><span class="sxs-lookup"><span data-stu-id="3ff17-167">AverageTimePerIssue</span></span>|<span data-ttu-id="3ff17-168">回應來電所需的平均時間。</span><span class="sxs-lookup"><span data-stu-id="3ff17-168">The average time required to respond to an incoming call.</span></span>|  
|<span data-ttu-id="3ff17-169">ServiceGrade</span><span class="sxs-lookup"><span data-stu-id="3ff17-169">ServiceGrade</span></span>|<span data-ttu-id="3ff17-170">指出一般服務品質的度量，以整個排班的*放棄速率*來測量。</span><span class="sxs-lookup"><span data-stu-id="3ff17-170">A metric that indicates the general quality of service, measured as the *abandon rate* for the entire shift.</span></span> <span data-ttu-id="3ff17-171">放棄率越高，客戶越可能不滿意，而且可能會遺失潛在的訂單。</span><span class="sxs-lookup"><span data-stu-id="3ff17-171">The higher the abandon rate, the more likely it is that customers are dissatisfied and that potential orders are being lost.</span></span>|  
  
 <span data-ttu-id="3ff17-172">請注意，資料包含四個以單一日期資料行為基礎的不同資料行： `WageType` 、 **DayOfWeek**、 `Shift` 和 `DateKey` 。</span><span class="sxs-lookup"><span data-stu-id="3ff17-172">Note that the data includes four different columns that are based on a single date column: `WageType`, **DayOfWeek**, `Shift`, and `DateKey`.</span></span> <span data-ttu-id="3ff17-173">通常在資料採礦中，最好不要使用多個衍生自相同資料的資料行，因為值的相互關聯性太強，可能會遮蔽其他模式。</span><span class="sxs-lookup"><span data-stu-id="3ff17-173">Ordinarily in data mining it is not a good idea to use multiple columns that are derived from the same data, as the values correlate with each other too strongly and can obscure other patterns.</span></span>  
  
 <span data-ttu-id="3ff17-174">不過，我們不會 `DateKey` 在模型中使用，因為它包含太多的唯一值。</span><span class="sxs-lookup"><span data-stu-id="3ff17-174">However, we will not use `DateKey` in the model because it contains too many unique values.</span></span> <span data-ttu-id="3ff17-175">和 DayOfWeek 之間沒有直接的關聯性 `Shift` ， **DayOfWeek**而且 `WageType` 和**DayOfWeek**只有部分相關。</span><span class="sxs-lookup"><span data-stu-id="3ff17-175">There is no direct relationship between `Shift` and **DayOfWeek**, and `WageType` and **DayOfWeek** are only partly related.</span></span> <span data-ttu-id="3ff17-176">如果您對共線性有顧慮，可以使用所有可用的資料行建立結構，然後忽略各模型中不同的資料行並測試效果。</span><span class="sxs-lookup"><span data-stu-id="3ff17-176">If you were worried about collinearity, you could create the structure using all of the available columns, and then ignore different columns in each model and test the effect.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="3ff17-177">本課程的下一項工作</span><span class="sxs-lookup"><span data-stu-id="3ff17-177">Next Task in Lesson</span></span>  
 [<span data-ttu-id="3ff17-178">建立類神經網路結構和模型 &#40;中繼資料採礦教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="3ff17-178">Creating a Neural Network Structure and Model &#40;Intermediate Data Mining Tutorial&#41;</span></span>](../../2014/tutorials/creating-a-neural-network-structure-and-model-intermediate-data-mining-tutorial.md)  
  
## <a name="see-also"></a><span data-ttu-id="3ff17-179">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3ff17-179">See Also</span></span>  
 [<span data-ttu-id="3ff17-180">多維度模型中的資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="3ff17-180">Data Source Views in Multidimensional Models</span></span>](https://docs.microsoft.com/analysis-services/multidimensional-models/data-source-views-in-multidimensional-models)  
  
  
