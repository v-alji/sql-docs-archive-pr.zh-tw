---
title: 指定變更資料的間隔 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],specifying interval
ms.assetid: 17899078-8ba3-4f40-8769-e9837dc3ec60
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 70b9c14d609f2db69ee5751eca18acb5262a07a1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594128"
---
# <a name="specify-an-interval-of-change-data"></a><span data-ttu-id="3cadb-102">指定變更資料的間隔</span><span class="sxs-lookup"><span data-stu-id="3cadb-102">Specify an Interval of Change Data</span></span>
  <span data-ttu-id="3cadb-103">在執行累加式變更資料載入之 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝的控制流程中，第一個工作是計算變更間隔的端點。</span><span class="sxs-lookup"><span data-stu-id="3cadb-103">In the control flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the first task is to calculate the endpoints of the change interval.</span></span> <span data-ttu-id="3cadb-104">這些端點是 `datetime` 值，而且將會以封裝變數儲存，以便稍後在封裝中使用。</span><span class="sxs-lookup"><span data-stu-id="3cadb-104">These endpoints are `datetime` values and will be stored in package variables for use later in the package.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3cadb-105">如需設計控制流程之完整程序的描述，請參閱[異動資料擷取 &#40;SSIS&#41;](change-data-capture-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="3cadb-105">For a description of the overall process of designing the control flow, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="set-up-package-variables-for-the-endpoints"></a><span data-ttu-id="3cadb-106">設定端點的封裝變數</span><span class="sxs-lookup"><span data-stu-id="3cadb-106">Set Up Package Variables for the Endpoints</span></span>  
 <span data-ttu-id="3cadb-107">設定「執行 SQL」工作以計算端點前，必須先定義儲存端點的封裝變數。</span><span class="sxs-lookup"><span data-stu-id="3cadb-107">Before configuring the Execute SQL task to calculate the endpoints, the package variables that will store the endpoints have to be defined.</span></span>  
  
#### <a name="to-set-up-package-variables"></a><span data-ttu-id="3cadb-108">設定封裝變數</span><span class="sxs-lookup"><span data-stu-id="3cadb-108">To set up package variables</span></span>  
  
1.  <span data-ttu-id="3cadb-109">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中，開啟新的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="3cadb-109">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], open a new [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] project.</span></span>  
  
2.  <span data-ttu-id="3cadb-110">在 **[變數]** 視窗中，建立下列變數：</span><span class="sxs-lookup"><span data-stu-id="3cadb-110">In the **Variables** window, create the following variables:</span></span>  
  
    1.  <span data-ttu-id="3cadb-111">建立具有 `datetime` 資料類型的變數，以保存間隔的起始點。</span><span class="sxs-lookup"><span data-stu-id="3cadb-111">Create a variable with the `datetime` data type to hold the starting point for the interval.</span></span>  
  
         <span data-ttu-id="3cadb-112">這個範例會使用變數名稱 ExtractStartTime。</span><span class="sxs-lookup"><span data-stu-id="3cadb-112">This example uses the variable name, ExtractStartTime.</span></span>  
  
    2.  <span data-ttu-id="3cadb-113">建立具有 `datetime` 資料類型的另一個變數，以保存間隔的結束點。</span><span class="sxs-lookup"><span data-stu-id="3cadb-113">Create another variable with the `datetime` data type to hold the ending point for the interval.</span></span>  
  
         <span data-ttu-id="3cadb-114">這個範例會使用變數名稱 ExtractEndTime。</span><span class="sxs-lookup"><span data-stu-id="3cadb-114">This example uses the variable name, ExtractEndTime.</span></span>  
  
 <span data-ttu-id="3cadb-115">如果您要在主要封裝中，計算執行多個子封裝的端點，您可以使用「父封裝變數」組態，將這些變數的值傳遞到每個子封裝。</span><span class="sxs-lookup"><span data-stu-id="3cadb-115">If you calculate the endpoints in a master package that executes multiple child packages, you can use Parent Package Variable configurations to pass the values of these variables to each child package.</span></span> <span data-ttu-id="3cadb-116">如需詳細資訊，請參閱 [執行封裝工作](../control-flow/execute-package-task.md) 和 [在子封裝中使用變數和參數的值](../use-the-values-of-variables-and-parameters-in-a-child-package.md)。</span><span class="sxs-lookup"><span data-stu-id="3cadb-116">For more information, see [Execute Package Task](../control-flow/execute-package-task.md) and [Use the Values of Variables and Parameters in a Child Package](../use-the-values-of-variables-and-parameters-in-a-child-package.md).</span></span>  
  
## <a name="calculate-a-starting-point-and-an-ending-point-for-change-data"></a><span data-ttu-id="3cadb-117">計算變更資料的起始點和結束點</span><span class="sxs-lookup"><span data-stu-id="3cadb-117">Calculate a Starting Point and an Ending Point for Change Data</span></span>  
 <span data-ttu-id="3cadb-118">設定間隔端點的封裝變數後，您可以計算這些端點的實際值，然後將這些值對應到對應的封裝變數。</span><span class="sxs-lookup"><span data-stu-id="3cadb-118">After you set up the package variables for the interval endpoints, you can calculate the actual values for those endpoints and map those values to the corresponding package variables.</span></span> <span data-ttu-id="3cadb-119">這些端點都是 `datetime` 值，因此您必須使用可以計算或處理 `datetime` 值的函數。</span><span class="sxs-lookup"><span data-stu-id="3cadb-119">Because those endpoints are `datetime` values, you will have to use functions that can calculate or work with `datetime` values.</span></span> <span data-ttu-id="3cadb-120">[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 運算式語言和 Transact-SQL 都有可以使用 `datetime` 值的函數：</span><span class="sxs-lookup"><span data-stu-id="3cadb-120">Both the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language and Transact-SQL have functions that work with `datetime` values:</span></span>  
  
 <span data-ttu-id="3cadb-121">在 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 運算式語言中，使用 `datetime` 值的函數</span><span class="sxs-lookup"><span data-stu-id="3cadb-121">Functions in the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language that work with `datetime` values</span></span>  
 -   [<span data-ttu-id="3cadb-122">DATEADD &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="3cadb-122">DATEADD &#40;SSIS Expression&#41;</span></span>](../expressions/dateadd-ssis-expression.md)  
  
-   [<span data-ttu-id="3cadb-123">DATEDIFF &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="3cadb-123">DATEDIFF &#40;SSIS Expression&#41;</span></span>](../expressions/datediff-ssis-expression.md)  
  
-   [<span data-ttu-id="3cadb-124">DATEPART &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="3cadb-124">DATEPART &#40;SSIS Expression&#41;</span></span>](../expressions/datepart-ssis-expression.md)  
  
-   [<span data-ttu-id="3cadb-125">DAY &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="3cadb-125">DAY &#40;SSIS Expression&#41;</span></span>](../expressions/day-ssis-expression.md)  
  
-   [<span data-ttu-id="3cadb-126">GETDATE &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="3cadb-126">GETDATE &#40;SSIS Expression&#41;</span></span>](../expressions/getdate-ssis-expression.md)  
  
-   [<span data-ttu-id="3cadb-127">GETUTCDATE &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="3cadb-127">GETUTCDATE &#40;SSIS Expression&#41;</span></span>](../expressions/getutcdate-ssis-expression.md)  
  
-   [<span data-ttu-id="3cadb-128">MONTH &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="3cadb-128">MONTH &#40;SSIS Expression&#41;</span></span>](../expressions/month-ssis-expression.md)  
  
-   [<span data-ttu-id="3cadb-129">YEAR &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="3cadb-129">YEAR &#40;SSIS Expression&#41;</span></span>](../expressions/year-ssis-expression.md)  
  
 <span data-ttu-id="3cadb-130">在 Transact-SQL 中，使用 `datetime` 值的函數</span><span class="sxs-lookup"><span data-stu-id="3cadb-130">Functions in Transact-SQL that work with `datetime` values</span></span>  
 <span data-ttu-id="3cadb-131">[日期和時間資料類型與函數 &#40;Transact-SQL&#41;](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3cadb-131">[Date and Time Data Types and Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql).</span></span>  
  
 <span data-ttu-id="3cadb-132">使用其中任何一個 `datetime` 函數計算端點前，您必須判斷間隔是否已經固定，而且是否定期發生。</span><span class="sxs-lookup"><span data-stu-id="3cadb-132">Before you use any one of these `datetime` functions to calculate the endpoints, you have to determine whether the interval is fixed and occurs on a regular schedule.</span></span> <span data-ttu-id="3cadb-133">一般而言，您會想要將來源資料表中發生的變更定期套用到目的地資料表。</span><span class="sxs-lookup"><span data-stu-id="3cadb-133">Typically, you want to apply changes that have occurred in source tables to destination tables on a regular schedule.</span></span> <span data-ttu-id="3cadb-134">例如，您可能會想要每小時、每天，或每週套用一次這些變更。</span><span class="sxs-lookup"><span data-stu-id="3cadb-134">For example, you might want to apply those changes on an hourly, daily, or weekly basis.</span></span>  
  
 <span data-ttu-id="3cadb-135">了解您的變更間隔是固定還是比較隨機後，您就可以計算端點：</span><span class="sxs-lookup"><span data-stu-id="3cadb-135">After you understand whether your change interval is fixed or is more random, you can calculate the endpoints:</span></span>  
  
-   <span data-ttu-id="3cadb-136">**計算開始日期和時間**。</span><span class="sxs-lookup"><span data-stu-id="3cadb-136">**Calculating the starting date and time**.</span></span> <span data-ttu-id="3cadb-137">您可以使用上次載入的結束日期和時間當做目前的開始日期和時間。</span><span class="sxs-lookup"><span data-stu-id="3cadb-137">You use the ending date and time from the previous load as the current starting date and time.</span></span> <span data-ttu-id="3cadb-138">如果您將固定間隔用於累加式載入，您可以使用 Transact-SQL 或 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 運算式語言的 `datetime` 函數來計算這個值。</span><span class="sxs-lookup"><span data-stu-id="3cadb-138">If you use a fixed interval for incremental loads, you can calculate this value by using the `datetime` functions of Transact-SQL or of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language.</span></span> <span data-ttu-id="3cadb-139">否則，您可能需要保存執行之間的端點，並使用「執行 SQL」工作或「指令碼」工作來載入前一個端點。</span><span class="sxs-lookup"><span data-stu-id="3cadb-139">Otherwise, you might have to persist the endpoints between executions, and use an Execute SQL task or a Script task to load the previous endpoint.</span></span>  
  
-   <span data-ttu-id="3cadb-140">**計算結束日期和時間**。</span><span class="sxs-lookup"><span data-stu-id="3cadb-140">**Calculating the ending date and time**.</span></span> <span data-ttu-id="3cadb-141">如果您將固定間隔用於累加式載入，計算目前的結束日期和時間當做開始日期和時間的位移。</span><span class="sxs-lookup"><span data-stu-id="3cadb-141">If you use a fixed interval for incremental loads, calculate the current ending date and time as an offset from the starting date and time.</span></span> <span data-ttu-id="3cadb-142">同樣地，您可以使用 `datetime` transact-sql 或運算式語言的函數來計算此值 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3cadb-142">Again, you can calculate this value by using the `datetime` functions of Transact-SQL or of the [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] expression language.</span></span>  
  
 <span data-ttu-id="3cadb-143">在下列程序中，變更間隔會使用固定間隔，並假設累加式載入封裝是每天執行而沒有例外。</span><span class="sxs-lookup"><span data-stu-id="3cadb-143">In the following procedure, the change interval uses a fixed interval and assumes that the incremental load package is run daily without exception.</span></span> <span data-ttu-id="3cadb-144">否則，將會遺失遺漏間隔的變更資料。</span><span class="sxs-lookup"><span data-stu-id="3cadb-144">Otherwise, change data for missed intervals would be lost.</span></span> <span data-ttu-id="3cadb-145">間隔的起點是前天的午夜，也就是在前 24 到 48 小時之間。</span><span class="sxs-lookup"><span data-stu-id="3cadb-145">The starting point for the interval is midnight the day before yesterday, that is, between 24 and 48 hours ago.</span></span> <span data-ttu-id="3cadb-146">間隔的結束點是昨天的午夜，也就是昨天晚上，前 0 到 24 小時之間。</span><span class="sxs-lookup"><span data-stu-id="3cadb-146">The ending point for the interval is midnight yesterday, that is, the previous night, between 0 and 24 hours ago.</span></span>  
  
#### <a name="to-calculate-the-starting-point-and-ending-point-for-the-capture-interval"></a><span data-ttu-id="3cadb-147">計算擷取間隔的起點和結束點</span><span class="sxs-lookup"><span data-stu-id="3cadb-147">To calculate the starting point and ending point for the capture interval</span></span>  
  
1.  <span data-ttu-id="3cadb-148">在「 **設計師」的** [控制流程] [!INCLUDE[ssIS](../../includes/ssis-md.md)] 索引標籤上，將「執行 SQL」工作加入到封裝中。</span><span class="sxs-lookup"><span data-stu-id="3cadb-148">On the **Control Flow** tab of [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add an Execute SQL Task to the package.</span></span>  
  
2.  <span data-ttu-id="3cadb-149">開啟 **[執行 SQL 工作編輯器]** 然後在編輯器的 **[一般]** 頁面上，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="3cadb-149">Open the **Execute SQL Task Editor**, and on the **General** page of the editor, select the following options:</span></span>  
  
    1.  <span data-ttu-id="3cadb-150">針對 **[ResultSet]** ，選取 **[單一資料列]** 。</span><span class="sxs-lookup"><span data-stu-id="3cadb-150">For **ResultSet**, select **Single row**.</span></span>  
  
    2.  <span data-ttu-id="3cadb-151">將有效的連接設定到來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="3cadb-151">Configure a valid connection to the source database.</span></span>  
  
    3.  <span data-ttu-id="3cadb-152">針對 **[SQLSourceType]** ，選取 **[直接輸入]** 。</span><span class="sxs-lookup"><span data-stu-id="3cadb-152">For **SQLSourceType**, select **Direct input**.</span></span>  
  
    4.  <span data-ttu-id="3cadb-153">針對 **[SQLStatement]** ，輸入下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="3cadb-153">For **SQLStatement**, enter the following SQL statement:</span></span>  
  
        ```  
        SELECT DATEADD(dd,0, DATEDIFF(dd,0,GETDATE()-1)) AS ExtractStartTime,  
          DATEADD(dd,0, DATEDIFF(dd,0,GETDATE())) AS ExtractEndTime  
  
        ```  
  
3.  <span data-ttu-id="3cadb-154">在 **[執行 SQL 工作編輯器]** 的 **[結果集]** 頁面上，將 ExtractStartTime 結果對應到 ExtractStartTime 封裝變數，並將 ExtractEndTime 結果對應到 ExtractEndTime 封裝變數。</span><span class="sxs-lookup"><span data-stu-id="3cadb-154">On the **Result Set** page of the **Execute SQL Task Editor**, map the ExtractStartTime result to the ExtractStartTime package variable, and map the ExtractEndTime result to the ExtractEndTime package variable.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="3cadb-155">當您使用運算式來設定 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 變數的值時，每次存取變數的值時，就會評估該運算式。</span><span class="sxs-lookup"><span data-stu-id="3cadb-155">When you use an expression to set the value of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] variable, the expression is evaluated every time that the value of the variable is accessed.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="3cadb-156">後續步驟</span><span class="sxs-lookup"><span data-stu-id="3cadb-156">Next Step</span></span>  
 <span data-ttu-id="3cadb-157">計算變更範圍的起點和結束點後，下一個步驟是判斷變更資料是否就緒。</span><span class="sxs-lookup"><span data-stu-id="3cadb-157">After you calculate the starting point and ending point for a range of changes, the next step is to determine whether the change data is ready.</span></span>  
  
 <span data-ttu-id="3cadb-158">**下一個主題：** [判斷變更資料是否就緒](determine-whether-the-change-data-is-ready.md)</span><span class="sxs-lookup"><span data-stu-id="3cadb-158">**Next topic:** [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cadb-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3cadb-159">See Also</span></span>  
 <span data-ttu-id="3cadb-160">[在封裝中使用變數](../use-variables-in-packages.md) </span><span class="sxs-lookup"><span data-stu-id="3cadb-160">[Use Variables in Packages](../use-variables-in-packages.md) </span></span>  
 <span data-ttu-id="3cadb-161">[Integration Services &#40;SSIS&#41; 運算式](../expressions/integration-services-ssis-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="3cadb-161">[Integration Services &#40;SSIS&#41; Expressions](../expressions/integration-services-ssis-expressions.md) </span></span>  
 <span data-ttu-id="3cadb-162">[執行 SQL 工作](../control-flow/execute-sql-task.md) </span><span class="sxs-lookup"><span data-stu-id="3cadb-162">[Execute SQL Task](../control-flow/execute-sql-task.md) </span></span>  
 [<span data-ttu-id="3cadb-163">指令碼工作</span><span class="sxs-lookup"><span data-stu-id="3cadb-163">Script Task</span></span>](../control-flow/script-task.md)  
  
  
