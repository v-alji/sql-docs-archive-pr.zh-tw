---
title: 判斷變更資料是否就緒 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],determining readiness
ms.assetid: 04935f35-96cc-4d70-a250-0fd326f8daff
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e672440938e366e53ba150f65d7bcd6aed8a58c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707718"
---
# <a name="determine-whether-the-change-data-is-ready"></a><span data-ttu-id="118cb-102">判斷變更資料是否就緒</span><span class="sxs-lookup"><span data-stu-id="118cb-102">Determine Whether the Change Data Is Ready</span></span>
  <span data-ttu-id="118cb-103">在執行累加式變更資料載入之 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝的控制流程中，第二個工作是確保所選間隔之變更資料已就緒。</span><span class="sxs-lookup"><span data-stu-id="118cb-103">In the control flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the second task is to ensure that the change data for the selected interval is ready.</span></span> <span data-ttu-id="118cb-104">由於非同步的擷取程序可能還沒有處理到所選端點的所有變更，因此這是必要的步驟。</span><span class="sxs-lookup"><span data-stu-id="118cb-104">This step is necessary because the asynchronous capture process might not yet have processed all the changes up to the selected endpoint.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="118cb-105">控制流程的第一個工作是計算變更間隔的端點。</span><span class="sxs-lookup"><span data-stu-id="118cb-105">The first task for the control flow is to calculate the endpoints of the change interval.</span></span> <span data-ttu-id="118cb-106">如需這項工作的詳細資訊，請參閱 [指定變更資料的間隔](specify-an-interval-of-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="118cb-106">For more information about this task, see [Specify an Interval of Change Data](specify-an-interval-of-change-data.md).</span></span> <span data-ttu-id="118cb-107">如需設計控制流程之完整程序的描述，請參閱[異動資料擷取 &#40;SSIS&#41;](change-data-capture-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="118cb-107">For a description of the overall process of designing the control flow, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="understanding-the-components-of-the-solution"></a><span data-ttu-id="118cb-108">了解方案的元件</span><span class="sxs-lookup"><span data-stu-id="118cb-108">Understanding the Components of the Solution</span></span>  
 <span data-ttu-id="118cb-109">本主題所描述的方案使用 4 個 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 元件：</span><span class="sxs-lookup"><span data-stu-id="118cb-109">The solution described in this topic uses 4 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] components:</span></span>  
  
-   <span data-ttu-id="118cb-110">重複評估「執行 SQL」工作之輸出的「For 迴圈」容器。</span><span class="sxs-lookup"><span data-stu-id="118cb-110">A For Loop container that repeatedly evaluates the output of an Execute SQL Task.</span></span>  
  
-   <span data-ttu-id="118cb-111">可查詢異動資料擷取程序維護然後使用此資訊判斷資料是否就緒之特殊資料表的「執行 SQL」工作。</span><span class="sxs-lookup"><span data-stu-id="118cb-111">An Execute SQL task that queries special tables that the change data capture process maintains and then uses this information to determine whether data is ready.</span></span>  
  
-   <span data-ttu-id="118cb-112">實作資料未就緒時處理之延遲的元件。</span><span class="sxs-lookup"><span data-stu-id="118cb-112">A component that implements a delay in processing when the data is not ready.</span></span> <span data-ttu-id="118cb-113">這可以是「指令碼」工作或「執行 SQL」工作。</span><span class="sxs-lookup"><span data-stu-id="118cb-113">This can be either a Script task or an Execute SQL task.</span></span>  
  
-   <span data-ttu-id="118cb-114">(選擇性) 當「執行 SQL」工作傳回表示錯誤或逾時狀況的值時，報告錯誤或逾時的元件。</span><span class="sxs-lookup"><span data-stu-id="118cb-114">Optionally, a component that reports an error or a timeout when the Execute SQL task returns a value that indicates an error or a timeout condition.</span></span>  
  
 <span data-ttu-id="118cb-115">這些元件會設定或讀取數個封裝變數的值以控制在迴圈內部或稍後在封裝中執行的流程。</span><span class="sxs-lookup"><span data-stu-id="118cb-115">These components set or read the values of several package variables to control the flow of execution inside the loop and later in the package.</span></span>  
  
#### <a name="to-set-up-package-variables"></a><span data-ttu-id="118cb-116">設定封裝變數</span><span class="sxs-lookup"><span data-stu-id="118cb-116">To set up package variables</span></span>  
  
1.  <span data-ttu-id="118cb-117">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]的 **[變數]** 視窗中，建立下列變數：</span><span class="sxs-lookup"><span data-stu-id="118cb-117">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in the **Variables** window, create the following variables:</span></span>  
  
    1.  <span data-ttu-id="118cb-118">建立具有整數資料類型的變數，以保存「執行 SQL」工作傳回的狀態值。</span><span class="sxs-lookup"><span data-stu-id="118cb-118">Create a variable with an integer data type to hold the status value returned by the Execute SQL task.</span></span>  
  
         <span data-ttu-id="118cb-119">此範例會使用變數名稱 DataReady，其初始值為 0。</span><span class="sxs-lookup"><span data-stu-id="118cb-119">This example uses the variable name, DataReady, with an initial value of 0.</span></span>  
  
    2.  <span data-ttu-id="118cb-120">建立變數以便在資料尚未就緒時，保存要延遲的期間。</span><span class="sxs-lookup"><span data-stu-id="118cb-120">Create a variable to hold the period of time to delay when data is not ready.</span></span> <span data-ttu-id="118cb-121">如果您要使用「指令碼」工作實作延遲，變數的資料類型應為整數。</span><span class="sxs-lookup"><span data-stu-id="118cb-121">If you plan to use a Script task to implement the delay, the variable should have an integer data type integer.</span></span> <span data-ttu-id="118cb-122">如果您要搭配 WAITFOR 陳述式使用「執行 SQL」工作，變數的資料類型應該為字串，才能接受諸如 "00:00:10" 的值。</span><span class="sxs-lookup"><span data-stu-id="118cb-122">If you plan to use an Execute SQL task with a WAITFOR statement, the variable should have a string data type to accept values such as "00:00:10".</span></span>  
  
         <span data-ttu-id="118cb-123">此範例會使用變數名稱 DelaySeconds，其初始值為 10。</span><span class="sxs-lookup"><span data-stu-id="118cb-123">This example uses the variable name, DelaySeconds, with an initial value of 10.</span></span>  
  
    3.  <span data-ttu-id="118cb-124">建立具有整數資料類型的變數，以保存迴圈的目前反覆運算。</span><span class="sxs-lookup"><span data-stu-id="118cb-124">Create a variable with an integer data type to hold the current iteration of the loop.</span></span>  
  
         <span data-ttu-id="118cb-125">此範例會使用變數名稱 TimeoutCount，其初始值為 0。</span><span class="sxs-lookup"><span data-stu-id="118cb-125">This example uses the variable name, TimeoutCount, with an initial value of 0.</span></span>  
  
    4.  <span data-ttu-id="118cb-126">建立具有整數資料類型的變數，以指定報告逾時狀況前，迴圈應該測試資料的次數。</span><span class="sxs-lookup"><span data-stu-id="118cb-126">Create a variable with an integer data type to specify the number of times that the loop should test for data before reporting a timeout condition.</span></span>  
  
         <span data-ttu-id="118cb-127">此範例會使用變數名稱 TimeoutCeiling，其初始值為 20。</span><span class="sxs-lookup"><span data-stu-id="118cb-127">This example uses the variable name, TimeoutCeiling, with an initial value of 20.</span></span>  
  
    5.  <span data-ttu-id="118cb-128">(選擇性) 建立具有整數資料類型的變數，用於表示變更資料的第一個載入。</span><span class="sxs-lookup"><span data-stu-id="118cb-128">(Optional) Create a variable with an integer data type that you can use to indicate the first load of change data.</span></span>  
  
         <span data-ttu-id="118cb-129">此範例會使用變數名稱 IntervalID，並僅針對 0 這個值進行檢查以表示初始載入。</span><span class="sxs-lookup"><span data-stu-id="118cb-129">This example uses the variable name, IntervalID, and checks only for a value of 0 to indicate the initial load.</span></span>  
  
## <a name="configuring-a-for-loop-container"></a><span data-ttu-id="118cb-130">設定 For 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="118cb-130">Configuring a For Loop Container</span></span>  
 <span data-ttu-id="118cb-131">在設定變數的情況下，「For 迴圈」容器是第一個要加入的元件。</span><span class="sxs-lookup"><span data-stu-id="118cb-131">With the variables set, the For Loop container is the first component to be added.</span></span>  
  
#### <a name="to-configure-a-for-loop-container-to-wait-until-change-data-is-ready"></a><span data-ttu-id="118cb-132">設定 For 迴圈容器以便等到變更資料就緒</span><span class="sxs-lookup"><span data-stu-id="118cb-132">To configure a For Loop container to wait until change data is ready</span></span>  
  
1.  <span data-ttu-id="118cb-133">在 **設計師的** [控制流程] [!INCLUDE[ssIS](../../includes/ssis-md.md)] 索引標籤上，將「For 迴圈」容器加入到控制流程中。</span><span class="sxs-lookup"><span data-stu-id="118cb-133">On the **Control Flow** tab of the [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, add a For Loop container to the control flow.</span></span>  
  
2.  <span data-ttu-id="118cb-134">將計算間隔端點的「執行 SQL」工作連接到「For 迴圈」容器。</span><span class="sxs-lookup"><span data-stu-id="118cb-134">Connect the Execute SQL Task that calculates the endpoints of the interval to the For Loop container.</span></span>  
  
3.  <span data-ttu-id="118cb-135">在 **[For 迴圈編輯器]** 中，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="118cb-135">In the **For Loop Editor**, select the following options:</span></span>  
  
    1.  <span data-ttu-id="118cb-136">針對 **InitExpression**，輸入 `@DataReady = 0`。</span><span class="sxs-lookup"><span data-stu-id="118cb-136">For **InitExpression**, enter `@DataReady = 0`.</span></span>  
  
         <span data-ttu-id="118cb-137">此運算式會設定迴圈變數的初始值。</span><span class="sxs-lookup"><span data-stu-id="118cb-137">This expression sets the initial value of the loop variable.</span></span>  
  
    2.  <span data-ttu-id="118cb-138">針對 **EvalExpression**m，輸入 `@DataReady == 0`。</span><span class="sxs-lookup"><span data-stu-id="118cb-138">For **EvalExpression**m, enter `@DataReady == 0`.</span></span>  
  
         <span data-ttu-id="118cb-139">當此運算式評估為 **False**時，執行會通過迴圈之外，而且會開始累加式載入。</span><span class="sxs-lookup"><span data-stu-id="118cb-139">When this expression evaluates to **False**, execution passes out of the loop and the incremental load starts.</span></span>  
  
## <a name="configuring-the-execute-sql-task-that-queries-for-change-data"></a><span data-ttu-id="118cb-140">設定查詢變更資料的執行 SQL 工作</span><span class="sxs-lookup"><span data-stu-id="118cb-140">Configuring the Execute SQL Task That Queries for Change Data</span></span>  
 <span data-ttu-id="118cb-141">在「For 迴圈」容器的內部，您可以加入「執行 SQL」工作。</span><span class="sxs-lookup"><span data-stu-id="118cb-141">Inside the For Loop container, you add an Execute SQL task.</span></span> <span data-ttu-id="118cb-142">此工作會查詢異動資料擷取程序在資料庫中維護的資料表。</span><span class="sxs-lookup"><span data-stu-id="118cb-142">This task queries the tables that the change data capture process maintains in the database.</span></span> <span data-ttu-id="118cb-143">此查詢的結果是一個狀態值，表示變更資料是否就緒。</span><span class="sxs-lookup"><span data-stu-id="118cb-143">The result of this query is a status value that indicates whether the change data is ready.</span></span>  
  
 <span data-ttu-id="118cb-144">在下表中，第一欄顯示範例 Transact-SQL 查詢從「執行 SQL」工作傳回的值。</span><span class="sxs-lookup"><span data-stu-id="118cb-144">In the following table, the first column shows the values returned from the Execute SQL task by the sample Transact-SQL query.</span></span> <span data-ttu-id="118cb-145">第二欄顯示其他元件如何回應這些值。</span><span class="sxs-lookup"><span data-stu-id="118cb-145">The second column shows how the other components respond to these values.</span></span>  
  
|<span data-ttu-id="118cb-146">傳回值</span><span class="sxs-lookup"><span data-stu-id="118cb-146">Return Value</span></span>|<span data-ttu-id="118cb-147">意義</span><span class="sxs-lookup"><span data-stu-id="118cb-147">Meaning</span></span>|<span data-ttu-id="118cb-148">回應</span><span class="sxs-lookup"><span data-stu-id="118cb-148">Response</span></span>|  
|------------------|-------------|--------------|  
|<span data-ttu-id="118cb-149">0</span><span class="sxs-lookup"><span data-stu-id="118cb-149">0</span></span>|<span data-ttu-id="118cb-150">表示變更資料尚未就緒。</span><span class="sxs-lookup"><span data-stu-id="118cb-150">Indicates that the change data is not ready.</span></span><br /><br /> <span data-ttu-id="118cb-151">沒有晚於所選間隔之結束點的異動資料擷取記錄。</span><span class="sxs-lookup"><span data-stu-id="118cb-151">There are no change data capture records later than the ending point of the selected interval.</span></span>|<span data-ttu-id="118cb-152">執行會繼續進行實作延遲的元件。</span><span class="sxs-lookup"><span data-stu-id="118cb-152">Execution continues with the component that implements a delay.</span></span> <span data-ttu-id="118cb-153">然後，控制會傳回「For 迴圈」容器，只要傳回的值為 0，就會繼續檢查「執行 SQL」工作。</span><span class="sxs-lookup"><span data-stu-id="118cb-153">Then control returns to the For Loop container, which continues to check the Execute SQL task as long as the value returned is 0.</span></span>|  
|<span data-ttu-id="118cb-154">1</span><span class="sxs-lookup"><span data-stu-id="118cb-154">1</span></span>|<span data-ttu-id="118cb-155">可能表示尚未擷取完整間隔的變更資料，或該變更資料已遭刪除。</span><span class="sxs-lookup"><span data-stu-id="118cb-155">Might indicate that the change data has not been captured for the complete interval, or that it has been deleted.</span></span> <span data-ttu-id="118cb-156">這會被視為錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="118cb-156">This is treated as an error condition.</span></span><br /><br /> <span data-ttu-id="118cb-157">沒有早於所選間隔之起始點的異動資料擷取記錄。</span><span class="sxs-lookup"><span data-stu-id="118cb-157">There are no change data capture records earlier than the starting point of the selected interval</span></span>|<span data-ttu-id="118cb-158">執行會繼續進行記錄錯誤的選擇性元件。</span><span class="sxs-lookup"><span data-stu-id="118cb-158">Execution continues with the optional component that logs the error.</span></span>|  
|<span data-ttu-id="118cb-159">2</span><span class="sxs-lookup"><span data-stu-id="118cb-159">2</span></span>|<span data-ttu-id="118cb-160">表示資料已就緒。</span><span class="sxs-lookup"><span data-stu-id="118cb-160">Indicates that data is ready.</span></span><br /><br /> <span data-ttu-id="118cb-161">沒有早於所選間隔之起始點，也沒有晚於所選間隔之結束點的異動資料擷取記錄。</span><span class="sxs-lookup"><span data-stu-id="118cb-161">There are change data capture records that are both earlier than the starting point and later than the ending point of the selected interval.</span></span>|<span data-ttu-id="118cb-162">執行會通過「For 迴圈」容器之外，而且會開始累加式載入。</span><span class="sxs-lookup"><span data-stu-id="118cb-162">Execution passes out of the For Loop container and the incremental load starts.</span></span>|  
|<span data-ttu-id="118cb-163">3</span><span class="sxs-lookup"><span data-stu-id="118cb-163">3</span></span>|<span data-ttu-id="118cb-164">表示所有可用變更資料的初始載入。</span><span class="sxs-lookup"><span data-stu-id="118cb-164">Indicates the initial load of all available change data.</span></span><br /><br /> <span data-ttu-id="118cb-165">條件式邏輯會從僅用於此用途的特殊封裝變數取得這個值。</span><span class="sxs-lookup"><span data-stu-id="118cb-165">The conditional logic obtains this value from a special package variable that is used only for this purpose.</span></span>|<span data-ttu-id="118cb-166">執行會通過「For 迴圈」容器之外，而且會開始累加式載入。</span><span class="sxs-lookup"><span data-stu-id="118cb-166">Execution passes out of the For Loop container and the incremental load starts.</span></span>|  
|<span data-ttu-id="118cb-167">5</span><span class="sxs-lookup"><span data-stu-id="118cb-167">5</span></span>|<span data-ttu-id="118cb-168">表示已達到 TimeoutCeiling。</span><span class="sxs-lookup"><span data-stu-id="118cb-168">Indicates that the TimeoutCeiling has been reached.</span></span><br /><br /> <span data-ttu-id="118cb-169">資料的迴圈已經測試過指定的次數，而且資料仍然無法使用。</span><span class="sxs-lookup"><span data-stu-id="118cb-169">The loop has tested for data the specified number of times, and data is still not available.</span></span> <span data-ttu-id="118cb-170">如果沒有這個測試或類似的測試，封裝可能會無期限地執行。</span><span class="sxs-lookup"><span data-stu-id="118cb-170">Without this test or a similar test, the package might run indefinitely.</span></span>|<span data-ttu-id="118cb-171">執行會繼續進行記錄逾時的選擇性元件。</span><span class="sxs-lookup"><span data-stu-id="118cb-171">Execution continues with the optional component that logs the timeout.</span></span>|  
  
#### <a name="to-configure-an-execute-sql-task-to-query-whether-change-data-is-ready"></a><span data-ttu-id="118cb-172">設定執行 SQL 工作查詢變更資料是否就緒</span><span class="sxs-lookup"><span data-stu-id="118cb-172">To configure an Execute SQL task to query whether change data is ready</span></span>  
  
1.  <span data-ttu-id="118cb-173">在「For 迴圈」容器的內部，加入「執行 SQL」工作。</span><span class="sxs-lookup"><span data-stu-id="118cb-173">Inside the For Loop container, add an Execute SQL task.</span></span>  
  
2.  <span data-ttu-id="118cb-174">在 **[執行 SQL 工作編輯器]** 的 **[一般]** 頁面上，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="118cb-174">In the **Execute SQL Task Editor**, on the **General** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="118cb-175">針對 **[ResultSet]** ，選取 **[單一資料列]** 。</span><span class="sxs-lookup"><span data-stu-id="118cb-175">For **ResultSet**, select **Single row**.</span></span>  
  
    2.  <span data-ttu-id="118cb-176">將有效的連接設定到來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="118cb-176">Configure a valid connection to the source database.</span></span>  
  
    3.  <span data-ttu-id="118cb-177">針對 **[SQLSourceType]** ，選取 **[直接輸入]** 。</span><span class="sxs-lookup"><span data-stu-id="118cb-177">For **SQLSourceType**, select **Direct input**.</span></span>  
  
    4.  <span data-ttu-id="118cb-178">針對 **[SQLStatement]** ，輸入下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="118cb-178">For **SQLStatement**, enter the following SQL statement:</span></span>  
  
        ```  
        declare @DataReady int, @TimeoutCount int  
  
        if not exists (select tran_end_time from cdc.lsn_time_mapping  
                where tran_end_time > ?  )  
            select @DataReady = 0  
        else  
            if ? = 0  
                select @DataReady = 3   
        else  
            if not exists (select tran_end_time from cdc.lsn_time_mapping  
                    where tran_end_time <= ? )  
                select @DataReady = 1   
        else  
            select @DataReady = 2  
  
        select @TimeoutCount = ?  
        if (@DataReady = 0)  
            select @TimeoutCount = @TimeoutCount + 1  
        else  
            select @TimeoutCount = 0  
  
        if (@TimeoutCount > ?)  
            select @DataReady = 5  
  
        select @DataReady as DataReady, @TimeoutCount as TimeoutCount  
  
        ```  
  
3.  <span data-ttu-id="118cb-179">在 **[執行 SQL 工作編輯器]** 的 **[參數對應]** 頁面上，進行下列對應：</span><span class="sxs-lookup"><span data-stu-id="118cb-179">On the **Parameter Mapping** page of the **Execute SQL Task Editor**, make the following mappings:</span></span>  
  
    1.  <span data-ttu-id="118cb-180">將 ExtractEndTime 變數對應到參數 0。</span><span class="sxs-lookup"><span data-stu-id="118cb-180">Map the ExtractEndTime variable to parameter 0.</span></span>  
  
    2.  <span data-ttu-id="118cb-181">將 IntervalID 變數對應到參數 1。</span><span class="sxs-lookup"><span data-stu-id="118cb-181">Map the IntervalID variable to parameter 1.</span></span>  
  
    3.  <span data-ttu-id="118cb-182">將 ExtractStartTime 變數對應到參數 2。</span><span class="sxs-lookup"><span data-stu-id="118cb-182">Map the ExtractStartTime variable to parameter 2.</span></span>  
  
    4.  <span data-ttu-id="118cb-183">將 TimeoutCount 變數對應到參數 3。</span><span class="sxs-lookup"><span data-stu-id="118cb-183">Map the TimeoutCount variable to parameter 3.</span></span>  
  
    5.  <span data-ttu-id="118cb-184">將 TimeoutCeiling 變數對應到參數 4。</span><span class="sxs-lookup"><span data-stu-id="118cb-184">Map the TimeoutCeiling variable to parameter 4.</span></span>  
  
4.  <span data-ttu-id="118cb-185">在 **[執行 SQL 工作編輯器]** 的 **[結果集]** 頁面上，將 DataReady 結果對應到 DataReady 變數，並將 TimeoutCount 結果對應到 TimeoutCount 變數。</span><span class="sxs-lookup"><span data-stu-id="118cb-185">On the **Result Set** page of the **Execute SQL Task Editor**, map the DataReady result to the DataReady variable, and the TimeoutCount result to the TimeoutCount variable.</span></span>  
  
## <a name="waiting-until-the-change-data-is-ready"></a><span data-ttu-id="118cb-186">等到變更資料就緒</span><span class="sxs-lookup"><span data-stu-id="118cb-186">Waiting Until the Change Data Is Ready</span></span>  
 <span data-ttu-id="118cb-187">變更資料尚未就緒時，您可以使用數個方法中的一個方法來實作延遲。</span><span class="sxs-lookup"><span data-stu-id="118cb-187">You can use one of several methods to implement a delay when the change data is not ready.</span></span> <span data-ttu-id="118cb-188">下列兩個程序說明如何使用「指令碼」工作或「執行 SQL」工作實作延遲。</span><span class="sxs-lookup"><span data-stu-id="118cb-188">The following two procedures illustrate how to use a Script task or an Execute SQL task to implement the delay.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="118cb-189">先行編譯的指令碼所產生的負擔比「執行 SQL」工作所產生的負擔少。</span><span class="sxs-lookup"><span data-stu-id="118cb-189">A precompiled script incurs less overhead than an Execute SQL task.</span></span>  
  
#### <a name="to-implement-a-delay-by-using-a-script-task"></a><span data-ttu-id="118cb-190">使用指令碼工作實作延遲</span><span class="sxs-lookup"><span data-stu-id="118cb-190">To implement a delay by using a Script task</span></span>  
  
1.  <span data-ttu-id="118cb-191">在「For 迴圈」容器的內部，加入「指令碼」工作。</span><span class="sxs-lookup"><span data-stu-id="118cb-191">Inside the For Loop container, add a Script task.</span></span>  
  
2.  <span data-ttu-id="118cb-192">將查詢以判斷變更資料是否就緒的「執行 SQL」工作連接到新的「指令碼」工作。</span><span class="sxs-lookup"><span data-stu-id="118cb-192">Connect the Execute SQL task that queries to determine whether the change data is ready to the new Script task.</span></span>  
  
3.  <span data-ttu-id="118cb-193">針對將「執行 SQL」工作連接到「指令碼」工作的優先順序條件約束，開啟 **[優先順序條件約束編輯器]** ，然後選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="118cb-193">For the precedence constraint that connects the Execute SQL task to the Script task, open the **Precedence Constraint Editor** and select the following options:</span></span>  
  
    1.  <span data-ttu-id="118cb-194">針對 **[評估作業]** ，選取 **[運算式與條件約束]** 。</span><span class="sxs-lookup"><span data-stu-id="118cb-194">For **Evaluation operation**, select **Expression and Constraint**.</span></span>  
  
    2.  <span data-ttu-id="118cb-195">針對 **[數值]** ，選取 **[成功]** 。</span><span class="sxs-lookup"><span data-stu-id="118cb-195">For **Value**, select **Success**.</span></span>  
  
         <span data-ttu-id="118cb-196">**[成功]** 的條件約束值會參考前一個工作的成功。</span><span class="sxs-lookup"><span data-stu-id="118cb-196">The constraint value of **Success** refers to the success of the previous task.</span></span> <span data-ttu-id="118cb-197">在這個情況下是「執行 SQL」工作的成功。</span><span class="sxs-lookup"><span data-stu-id="118cb-197">In this case, the success of the Execute SQL task.</span></span>  
  
    3.  <span data-ttu-id="118cb-198">針對 **[運算式]** ，輸入 `@DataReady == 0 && @TimeoutCount <= @TimeoutCeiling`。</span><span class="sxs-lookup"><span data-stu-id="118cb-198">For **Expression**, enter `@DataReady == 0 && @TimeoutCount <= @TimeoutCeiling`.</span></span>  
  
    4.  <span data-ttu-id="118cb-199">選取 **[邏輯 AND。所有的條件約束都必須評估為 True]** (如果尚未選取)。</span><span class="sxs-lookup"><span data-stu-id="118cb-199">Select **Logical AND. All constraints must evaluate to True**, if not already selected.</span></span>  
  
4.  <span data-ttu-id="118cb-200">在 **[指令碼工作編輯器]** 的 **[指令碼]** 頁面上，針對 **[ReadOnlyVariables]** ，選取清單中的 **[User::DelaySeconds]** 整數變數。</span><span class="sxs-lookup"><span data-stu-id="118cb-200">In the **Script Task Editor**, on the **Script** page, for **ReadOnlyVariables**, select the **User::DelaySeconds** integer variable from the list.</span></span>  
  
5.  <span data-ttu-id="118cb-201">在 **[指令碼工作編輯器]** 的 **[指令碼]** 頁面上，按一下 **[編輯指令碼]** 來開啟指令碼開發環境。</span><span class="sxs-lookup"><span data-stu-id="118cb-201">In the **Script Task Editor**, on the **Script** page, click **Edit Script** to open the script development environment.</span></span>  
  
6.  <span data-ttu-id="118cb-202">在 Main 程序中，輸入下列其中一個程式碼行：</span><span class="sxs-lookup"><span data-stu-id="118cb-202">In the Main procedure, enter one of the following lines of code:</span></span>  
  
    -   <span data-ttu-id="118cb-203">如果您是以 C# 撰寫程式，輸入下列程式碼行：</span><span class="sxs-lookup"><span data-stu-id="118cb-203">If you are programming in C#, enter the following line of code:</span></span>  
  
        ```  
        System.Threading.Thread.Sleep((int)Dts.Variables["DelaySeconds"].Value * 1000);  
        ```  
  
         <span data-ttu-id="118cb-204">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="118cb-204">\- or -</span></span>  
  
    -   <span data-ttu-id="118cb-205">如果您是以 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]撰寫程式，輸入下列程式碼行：</span><span class="sxs-lookup"><span data-stu-id="118cb-205">If you are programming in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], enter the following line of code:</span></span>  
  
        ```  
        System.Threading.Thread.Sleep(Ctype(Dts.Variables("DelaySeconds").Value, Integer) * 1000)  
  
        ```  
  
        > [!NOTE]  
        >  <span data-ttu-id="118cb-206">`Thread.Sleep` 方法應為以毫秒指定的引數。</span><span class="sxs-lookup"><span data-stu-id="118cb-206">The `Thread.Sleep` method expects an argument that is specified in milliseconds.</span></span>  
  
7.  <span data-ttu-id="118cb-207">保留從指令碼之執行傳回 `DtsExecResult.Success` 的預設程式碼行。</span><span class="sxs-lookup"><span data-stu-id="118cb-207">Leave the default line of code which returns `DtsExecResult.Success` from the execution of the script.</span></span>  
  
8.  <span data-ttu-id="118cb-208">關閉指令碼開發環境以及 **[指令碼工作編輯器]** 。</span><span class="sxs-lookup"><span data-stu-id="118cb-208">Close the script development environment and the **Script Task Editor**.</span></span>  
  
#### <a name="to-implement-a-delay-by-using-an-execute-sql-task"></a><span data-ttu-id="118cb-209">使用執行 SQL 工作實作延遲</span><span class="sxs-lookup"><span data-stu-id="118cb-209">To implement a delay by using an Execute SQL task</span></span>  
  
1.  <span data-ttu-id="118cb-210">在「For 迴圈」容器的內部，加入「執行 SQL」工作。</span><span class="sxs-lookup"><span data-stu-id="118cb-210">Inside the For Loop container, add an Execute SQL task.</span></span>  
  
2.  <span data-ttu-id="118cb-211">將查詢以判斷變更資料是否就緒的「執行 SQL」工作連接到新的「執行 SQL」工作。</span><span class="sxs-lookup"><span data-stu-id="118cb-211">Connect the Execute SQL task that queries to determine whether the change data is ready to the new Execute SQL task.</span></span>  
  
3.  <span data-ttu-id="118cb-212">針對連接兩個「執行 SQL」工作的優先順序條件約束，開啟 **[優先順序條件約束編輯器]** ，然後選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="118cb-212">For the precedence constraint that connects the two Execute SQL tasks, open the **Precedence Constraint Editor** and select the following options:</span></span>  
  
    1.  <span data-ttu-id="118cb-213">針對 **[評估作業]** ，選取 **[運算式與條件約束]** 。</span><span class="sxs-lookup"><span data-stu-id="118cb-213">For **Evaluation operation**, select **Expression and Constraint**.</span></span>  
  
    2.  <span data-ttu-id="118cb-214">針對 **[數值]** ，選取 **[成功]** 。</span><span class="sxs-lookup"><span data-stu-id="118cb-214">For **Value**, select **Success**.</span></span>  
  
         <span data-ttu-id="118cb-215">**[成功]** 的條件約束值會參考前一個「執行 SQL」工作的成功。</span><span class="sxs-lookup"><span data-stu-id="118cb-215">The constraint value of **Success** refers to the success of the previous Execute SQL task.</span></span>  
  
    3.  <span data-ttu-id="118cb-216">針對 **[運算式]** ，輸入 `@DataReady == 0`。</span><span class="sxs-lookup"><span data-stu-id="118cb-216">For **Expression**, enter `@DataReady == 0`.</span></span>  
  
    4.  <span data-ttu-id="118cb-217">選取 **[邏輯 AND。所有的條件約束都必須評估為 True]** (如果尚未選取)。</span><span class="sxs-lookup"><span data-stu-id="118cb-217">Select **Logical AND. All constraints must evaluate to True**, if not already selected.</span></span>  
  
         <span data-ttu-id="118cb-218">此選項需要條件約束和運算式兩個條件必須同時為 true。</span><span class="sxs-lookup"><span data-stu-id="118cb-218">This selection requires that both conditions, the constraint and the expression, must be true.</span></span>  
  
4.  <span data-ttu-id="118cb-219">在 **[執行 SQL 工作編輯器]** 的 **[一般]** 頁面上，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="118cb-219">In the **Execute SQL Task Editor**, on the **General** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="118cb-220">針對 **[ResultSet]** ，選取 **[單一資料列]** 。</span><span class="sxs-lookup"><span data-stu-id="118cb-220">For **ResultSet**, select **Single row**.</span></span>  
  
    2.  <span data-ttu-id="118cb-221">將有效的連接設定到來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="118cb-221">Configure a valid connection to the source database.</span></span>  
  
    3.  <span data-ttu-id="118cb-222">針對 **[SQLSourceType]** ，選取 **[直接輸入]** 。</span><span class="sxs-lookup"><span data-stu-id="118cb-222">For **SQLSourceType**, select **Direct input**.</span></span>  
  
    4.  <span data-ttu-id="118cb-223">針對 **[SQLStatement]** ，輸入下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="118cb-223">For **SQLStatement**, enter the following SQL statement:</span></span>  
  
        ```  
        WAITFOR DELAY ?  
  
        ```  
  
5.  <span data-ttu-id="118cb-224">在編輯器的 **[參數對應]** 頁面上，將 DelaySeconds 字串變數對應到參數 0。</span><span class="sxs-lookup"><span data-stu-id="118cb-224">On the **Parameter Mapping** page of the editor, map the DelaySeconds string variable to parameter 0.</span></span>  
  
## <a name="handling-an-error-condition"></a><span data-ttu-id="118cb-225">處理錯誤條件</span><span class="sxs-lookup"><span data-stu-id="118cb-225">Handling an Error Condition</span></span>  
 <span data-ttu-id="118cb-226">您可以在迴圈內部，選擇性地設定其他元件，以記錄錯誤或逾時條件：</span><span class="sxs-lookup"><span data-stu-id="118cb-226">You can optionally configure an additional component inside the loop to log an error or a timeout condition:</span></span>  
  
-   <span data-ttu-id="118cb-227">此元件可以在 DataReady 變數的值 = 1 時，記錄錯誤條件。</span><span class="sxs-lookup"><span data-stu-id="118cb-227">This component can log an error condition when the value of the DataReady variable = 1.</span></span> <span data-ttu-id="118cb-228">這個值表示在所選間隔開始前，沒有可用的變更資料。</span><span class="sxs-lookup"><span data-stu-id="118cb-228">This value indicates that there is no available change data before the start of the selected interval.</span></span>  
  
-   <span data-ttu-id="118cb-229">此元件也可以在達到 Timeout Ceiling 變數的值時，記錄逾時條件。</span><span class="sxs-lookup"><span data-stu-id="118cb-229">This component can also log a timeout condition when the value of the TimeoutCeiling variable is reached.</span></span> <span data-ttu-id="118cb-230">這個值表示資料的迴圈已經測試過指定的次數，而且資料仍然無法使用。</span><span class="sxs-lookup"><span data-stu-id="118cb-230">This value indicates the loop has tested for data the specified number of times, and data is still not available.</span></span> <span data-ttu-id="118cb-231">如果沒有這個測試或類似的測試，封裝可能會無期限地執行。</span><span class="sxs-lookup"><span data-stu-id="118cb-231">Without this test or a similar test, the package might run indefinitely.</span></span>  
  
#### <a name="to-configure-an-optional-script-task-to-log-an-error-condition"></a><span data-ttu-id="118cb-232">設定選擇性的指令碼工作以記錄錯誤條件</span><span class="sxs-lookup"><span data-stu-id="118cb-232">To configure an optional Script task to log an error condition</span></span>  
  
1.  <span data-ttu-id="118cb-233">如果您要將訊息寫入記錄檔藉以報告錯誤或逾時，請設定封裝的記錄。</span><span class="sxs-lookup"><span data-stu-id="118cb-233">If you want to report the error or timeout by writing a message to the log, configure logging for the package.</span></span> <span data-ttu-id="118cb-234">如需詳細資訊，請參閱 [在 SQL Server Data Tools 中啟用封裝記錄功能](../enable-package-logging-in-sql-server-data-tools.md)。</span><span class="sxs-lookup"><span data-stu-id="118cb-234">For more information, see [Enable Package Logging in SQL Server Data Tools](../enable-package-logging-in-sql-server-data-tools.md).</span></span>  
  
2.  <span data-ttu-id="118cb-235">在「For 迴圈」容器的內部，加入「指令碼」工作。</span><span class="sxs-lookup"><span data-stu-id="118cb-235">Inside the For Loop container, add a Script task.</span></span>  
  
3.  <span data-ttu-id="118cb-236">將查詢以判斷變更資料是否就緒的「執行 SQL」工作連接到新的「指令碼」工作。</span><span class="sxs-lookup"><span data-stu-id="118cb-236">Connect the Execute SQL task that queries to determine whether the change data is ready to the new Script task.</span></span>  
  
4.  <span data-ttu-id="118cb-237">針對將「執行 SQL」工作連接到「指令碼」工作的優先順序條件約束，開啟 **[優先順序條件約束編輯器]** ，然後選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="118cb-237">For the precedence constraint that connects the Execute SQL task to the Script task, open the **Precedence Constraint Editor** and select the following options:</span></span>  
  
    1.  <span data-ttu-id="118cb-238">針對 **[評估作業]** ，選取 **[運算式與條件約束]** 。</span><span class="sxs-lookup"><span data-stu-id="118cb-238">For **Evaluation operation**, select **Expression and Constraint**.</span></span>  
  
    2.  <span data-ttu-id="118cb-239">針對 **[數值]** ，選取 **[成功]** 。</span><span class="sxs-lookup"><span data-stu-id="118cb-239">For **Value**, select **Success**.</span></span>  
  
         <span data-ttu-id="118cb-240">**[成功]** 的條件約束值會參考前一個工作的成功。</span><span class="sxs-lookup"><span data-stu-id="118cb-240">The constraint value of **Success** refers to the success of the previous task.</span></span> <span data-ttu-id="118cb-241">在這個情況下是「執行 SQL」工作的成功。</span><span class="sxs-lookup"><span data-stu-id="118cb-241">In this case, the success of the Execute SQL task.</span></span>  
  
    3.  <span data-ttu-id="118cb-242">針對 **[運算式]** ，輸入 `@DataReady == 1 || @DataReady == 5`。</span><span class="sxs-lookup"><span data-stu-id="118cb-242">For **Expression**, enter `@DataReady == 1 || @DataReady == 5`.</span></span>  
  
    4.  <span data-ttu-id="118cb-243">選取 **[邏輯 AND。所有的條件約束都必須評估為 True]** (如果尚未選取)。</span><span class="sxs-lookup"><span data-stu-id="118cb-243">Select **Logical AND. All constraints must evaluate to True**, if not already selected.</span></span>  
  
         <span data-ttu-id="118cb-244">此選項需要條件約束和運算式兩個條件必須同時為 true。</span><span class="sxs-lookup"><span data-stu-id="118cb-244">This selection requires that both conditions, the constraint and the expression, must be true.</span></span>  
  
5.  <span data-ttu-id="118cb-245">在 **[指令碼工作編輯器]** 的 **[指令碼]** 頁面上，針對 **[ReadOnlyVariables]** ，從清單選取 **[User::DataReady]** 和 **[User::ExtractStartTime]** ，讓其值可以用於指令碼中。</span><span class="sxs-lookup"><span data-stu-id="118cb-245">In the **Script Task Editor**, on the **Script** page of the editor, for **ReadOnlyVariables**, select **User::DataReady** and **User::ExtractStartTime** from the list to make their values available to the script.</span></span>  
  
     <span data-ttu-id="118cb-246">如果您要將來自特定系統變數 (例如，System::PackageName) 的資訊加入到您要寫入記錄檔的資訊，請同時選取這些變數。</span><span class="sxs-lookup"><span data-stu-id="118cb-246">If you want to include information from certain system variables (for example, System::PackageName) in the information that you write to the log, select those variables also.</span></span>  
  
6.  <span data-ttu-id="118cb-247">在 **[指令碼工作編輯器]** 的 **[指令碼]** 頁面上，按一下 **[編輯指令碼]** 來開啟指令碼開發環境。</span><span class="sxs-lookup"><span data-stu-id="118cb-247">In the **Script Task Editor**, on the **Script** page, click **Edit Script** to open the script development environment.</span></span>  
  
7.  <span data-ttu-id="118cb-248">在 Main 程序中，呼叫 `Dts.Log` 方法來輸入程式碼以記錄錯誤，或呼叫 `Dts.Events` 介面的其中一個方法來引發事件。</span><span class="sxs-lookup"><span data-stu-id="118cb-248">In the Main procedure, enter code to log an error by calling the `Dts.Log` method, or to raise an event by calling one of the methods of the `Dts.Events` interface.</span></span> <span data-ttu-id="118cb-249">傳回 `Dts.TaskResult = Dts.Results.Failure`以通知封裝發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="118cb-249">Inform the package of the error by returning `Dts.TaskResult = Dts.Results.Failure`.</span></span>  
  
     <span data-ttu-id="118cb-250">下列範例顯示如何將訊息寫入到記錄檔中。</span><span class="sxs-lookup"><span data-stu-id="118cb-250">The following sample shows how to write a message to the log.</span></span> <span data-ttu-id="118cb-251">如需相關資訊，請參閱 [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md)、 [Raising Events in the Script Task](../extending-packages-scripting/task/raising-events-in-the-script-task.md)及 [Returning Results from the Script Task](../extending-packages-scripting/task/returning-results-from-the-script-task.md)。</span><span class="sxs-lookup"><span data-stu-id="118cb-251">For more information, see [Logging in the Script Task](../extending-packages-scripting/task/logging-in-the-script-task.md), [Raising Events in the Script Task](../extending-packages-scripting/task/raising-events-in-the-script-task.md), and [Returning Results from the Script Task](../extending-packages-scripting/task/returning-results-from-the-script-task.md).</span></span>  
  
    ```  
    ' User variables.  
    Dim dataReady As Integer = _  
      CType(Dts.Variables("DataReady").Value, Integer)  
    Dim extractStartTime As Date = _  
      CType(Dts.Variables("ExtractStartTime").Value, DateTime)  
  
    ' System variables.  
    Dim packageName As String = _  
      Dts.Variables("PackageName").Value.ToString()  
    Dim executionStartTime As Date = _  
      CType(Dts.Variables("StartTime").Value, DateTime)  
  
    Dim eventMessage As New System.Text.StringBuilder()  
  
    If dataReady = 1 OrElse dataReady = 5 Then  
  
      If dataReady = 1 Then  
        eventMessage.AppendLine("Start Time Error")  
      Else  
        eventMessage.AppendLine("Timeout Error")  
      End If  
  
      With eventMessage  
        .Append("The package ")  
        .Append(packageName)  
        .Append(" started at ")  
        .Append(executionStartTime.ToString())  
        .Append(" and ended at ")  
        .AppendLine(DateTime.Now().ToString())  
        If dataReady = 1 Then  
          .Append("The specified ExtractStartTime was ")  
          .AppendLine(extractStartTime.ToString())  
        End If  
      End With  
  
      System.Windows.Forms.MessageBox.Show(eventMessage.ToString())  
  
      Dts.Log(eventMessage.ToString(), 0, Nothing)  
  
      Dts.TaskResult = Dts.Results.Failure  
  
    Else  
  
      Dts.TaskResult = Dts.Results.Success  
  
    End If  
  
    ```  
  
8.  <span data-ttu-id="118cb-252">關閉指令碼開發環境以及 **[指令碼工作編輯器]** 。</span><span class="sxs-lookup"><span data-stu-id="118cb-252">Close the script development environment and the **Script Task Editor**.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="118cb-253">後續步驟</span><span class="sxs-lookup"><span data-stu-id="118cb-253">Next Step</span></span>  
 <span data-ttu-id="118cb-254">判斷變更資料就緒後，下一個步驟是準備針對變更資料進行查詢。</span><span class="sxs-lookup"><span data-stu-id="118cb-254">After you determine that change data is ready, the next step is to prepare to query for the change data.</span></span>  
  
 <span data-ttu-id="118cb-255">**下一個主題：** [準備查詢變更資料](prepare-to-query-for-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="118cb-255">**Next topic:** [Prepare to Query for the Change Data](prepare-to-query-for-the-change-data.md)</span></span>  
  
  
