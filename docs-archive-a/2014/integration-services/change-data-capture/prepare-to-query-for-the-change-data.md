---
title: 準備查詢變更資料 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- incremental load [Integration Services],preparing query
ms.assetid: 9ea2db7a-3dca-4bbf-9903-cccd2d494b5f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5ab732389d5a747c596472f14f5229361dd46275
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585531"
---
# <a name="prepare-to-query-for-the-change-data"></a><span data-ttu-id="1c20f-102">準備查詢變更資料</span><span class="sxs-lookup"><span data-stu-id="1c20f-102">Prepare to Query for the Change Data</span></span>
  <span data-ttu-id="1c20f-103">在執行累加式變更資料載入之 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝的控制流程中，第三個工作 (也就是最後一個工作) 是準備查詢變更資料，並加入「資料流程」工作。</span><span class="sxs-lookup"><span data-stu-id="1c20f-103">In the control flow of an [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] package that performs an incremental load of change data, the third and final task is to prepare to query for the change data and add a Data Flow task.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1c20f-104">控制流程的第二個工作是確保所選間隔的變更資料已就緒。</span><span class="sxs-lookup"><span data-stu-id="1c20f-104">The second task for the control flow is to ensure that the change data for the selected interval is ready.</span></span> <span data-ttu-id="1c20f-105">如需這項工作的詳細資訊，請參閱 [判斷變更資料是否就緒](determine-whether-the-change-data-is-ready.md)。</span><span class="sxs-lookup"><span data-stu-id="1c20f-105">For more information about this task, see [Determine Whether the Change Data Is Ready](determine-whether-the-change-data-is-ready.md).</span></span> <span data-ttu-id="1c20f-106">如需設計控制流程之完整程序的描述，請參閱[異動資料擷取 &#40;SSIS&#41;](change-data-capture-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="1c20f-106">For a description of the overall process of designing the control flow, see [Change Data Capture &#40;SSIS&#41;](change-data-capture-ssis.md).</span></span>  
  
## <a name="design-considerations"></a><span data-ttu-id="1c20f-107">設計考量</span><span class="sxs-lookup"><span data-stu-id="1c20f-107">Design Considerations</span></span>  
 <span data-ttu-id="1c20f-108">若要擷取異動資料，您將呼叫 Transact-SQL 資料表值函式，接受間隔的端點做為輸入參數，並傳回指定之間隔的異動資料。</span><span class="sxs-lookup"><span data-stu-id="1c20f-108">To retrieve the change data, you will call a Transact-SQL table-valued function that accepts the endpoints of the interval as input parameters and returns change data for the specified interval.</span></span> <span data-ttu-id="1c20f-109">資料流程中的來源元件會呼叫這個函數。</span><span class="sxs-lookup"><span data-stu-id="1c20f-109">A source component in the data flow calls this function.</span></span> <span data-ttu-id="1c20f-110">如需此來源元件的資訊，請參閱 [擷取與了解變更資料](retrieve-and-understand-the-change-data.md)。</span><span class="sxs-lookup"><span data-stu-id="1c20f-110">For information about this source component, see [Retrieve and Understand the Change Data](retrieve-and-understand-the-change-data.md).</span></span>  
  
 <span data-ttu-id="1c20f-111">最常用的 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 來源元件 (包括 OLE DB 來源、ADO 來源和 ADO NET 來源) 無法衍生資料表值函式的參數資訊。</span><span class="sxs-lookup"><span data-stu-id="1c20f-111">The most frequently used [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] source components, including the OLE DB source, the ADO source, and the ADO NET source, cannot derive parameter information for a table-valued function.</span></span> <span data-ttu-id="1c20f-112">因此，多數來源無法直接呼叫參數化函數。</span><span class="sxs-lookup"><span data-stu-id="1c20f-112">Therefore, most sources cannot call a parameterized function directly.</span></span>  
  
 <span data-ttu-id="1c20f-113">您有兩個設計選項，可傳遞函數的輸入參數：</span><span class="sxs-lookup"><span data-stu-id="1c20f-113">You have two design options for passing the input parameters to the function:</span></span>  
  
-   <span data-ttu-id="1c20f-114">**將參數化的查詢組合成字串**。</span><span class="sxs-lookup"><span data-stu-id="1c20f-114">**Assemble the parameterized query as a string**.</span></span> <span data-ttu-id="1c20f-115">您可以使用「指令碼」工作或「執行 SQL」工作，利用硬式編碼到字串的參數值，組合動態 SQL 字串。</span><span class="sxs-lookup"><span data-stu-id="1c20f-115">You can use a Script task or an Execute SQL task to assemble a dynamic SQL string with parameter values hard-coded into the string.</span></span> <span data-ttu-id="1c20f-116">然後，您可以將此字串儲存在封裝變數中，並將其用於設定來源元件的 SqlCommand 屬性。</span><span class="sxs-lookup"><span data-stu-id="1c20f-116">Then, you can store this string in a package variable and use it to set the SqlCommand property of a source component.</span></span> <span data-ttu-id="1c20f-117">由於來源元件不再需要參數資訊，因此這個方式會成功。</span><span class="sxs-lookup"><span data-stu-id="1c20f-117">This approach succeeds because the source component no longer requires parameter information.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c20f-118">先行編譯的指令碼所產生的負擔比「執行 SQL」工作所產生的負擔少。</span><span class="sxs-lookup"><span data-stu-id="1c20f-118">A precompiled script incurs less overhead than an Execute SQL task.</span></span>  
  
-   <span data-ttu-id="1c20f-119">**使用參數化的包裝函式**。</span><span class="sxs-lookup"><span data-stu-id="1c20f-119">**Use a parameterized wrapper**.</span></span> <span data-ttu-id="1c20f-120">或者，您可以建立參數化的預存程序，當做呼叫參數化資料表值函式的包裝函數。</span><span class="sxs-lookup"><span data-stu-id="1c20f-120">Alternatively, you can create a parameterized stored procedure as a wrapper that calls the parameterized table-valued function.</span></span> <span data-ttu-id="1c20f-121">由於來源元件可以成功衍生預存程序的參數資訊，因此這個方式會成功。</span><span class="sxs-lookup"><span data-stu-id="1c20f-121">This approach succeeds because a source component can successfully derive parameter information for a stored procedure.</span></span>  
  
 <span data-ttu-id="1c20f-122">本主題使用第一個設計選項，並將參數化的查詢組合成字串。</span><span class="sxs-lookup"><span data-stu-id="1c20f-122">This topic uses the first design option and assembles a parameterized query as a string.</span></span>  
  
## <a name="preparing-the-query"></a><span data-ttu-id="1c20f-123">準備查詢</span><span class="sxs-lookup"><span data-stu-id="1c20f-123">Preparing the Query</span></span>  
 <span data-ttu-id="1c20f-124">在您可以將輸入參數的值串連到單一查詢字串前，您必須設定查詢所需的封裝變數。</span><span class="sxs-lookup"><span data-stu-id="1c20f-124">Before you can concatenate the values of the input parameters into a single query string, you have to set up the package variables that the query needs.</span></span>  
  
#### <a name="to-set-up-package-variables"></a><span data-ttu-id="1c20f-125">設定封裝變數</span><span class="sxs-lookup"><span data-stu-id="1c20f-125">To set up package variables</span></span>  
  
-   <span data-ttu-id="1c20f-126">在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的 [變數]  視窗中，建立具有字串資料類型的變數，以保存「執行 SQL」工作所傳回的查詢字串。</span><span class="sxs-lookup"><span data-stu-id="1c20f-126">In [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], in the **Variables** window, create a variable with a string data type to hold the query string returned by the Execute SQL Task.</span></span>  
  
     <span data-ttu-id="1c20f-127">這個範例會使用變數名稱 SqlDataQuery。</span><span class="sxs-lookup"><span data-stu-id="1c20f-127">This example uses the variable name, SqlDataQuery.</span></span>  
  
 <span data-ttu-id="1c20f-128">建立封裝變數後，您可以使用「指令碼」工作或「執行 SQL」工作來串連輸入參數的值。</span><span class="sxs-lookup"><span data-stu-id="1c20f-128">With the package variable created, you can use either a Script task or Execute SQL task to concatenate the values of the input parameters.</span></span> <span data-ttu-id="1c20f-129">下列兩個程序描述如何設定這些元件。</span><span class="sxs-lookup"><span data-stu-id="1c20f-129">The following two procedures describe how to configure these components.</span></span>  
  
#### <a name="to-use-a-script-task-to-concatenate-the-query-string"></a><span data-ttu-id="1c20f-130">使用指令碼工作串連查詢字串</span><span class="sxs-lookup"><span data-stu-id="1c20f-130">To use a Script task to concatenate the query string</span></span>  
  
1.  <span data-ttu-id="1c20f-131">在 [控制流程]  索引標籤上，將「指令碼」工作加入「For 迴圈」容器後的封裝中，然後將「For 迴圈」容器連接到該工作。</span><span class="sxs-lookup"><span data-stu-id="1c20f-131">On the **Control Flow** tab, add a Script task to the package after the For Loop container and connect the For Loop container to the task.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c20f-132">此程序假設封裝會從單一資料表執行累加式載入。</span><span class="sxs-lookup"><span data-stu-id="1c20f-132">This procedure assumes that the package performs an incremental load from a single table.</span></span> <span data-ttu-id="1c20f-133">如果封裝從多個資料表載入，而且擁有包含多個子封裝的父封裝，則會將此工作當做第一個元件，加入到每個子封裝中。</span><span class="sxs-lookup"><span data-stu-id="1c20f-133">If the package loads from multiple tables and has a parent package with multiple child packages, this task would be added as the first component to each child package.</span></span> <span data-ttu-id="1c20f-134">如需詳細資訊，請參閱 [執行多個資料表的累加式載入](perform-an-incremental-load-of-multiple-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="1c20f-134">For more information, see [Perform an Incremental Load of Multiple Tables](perform-an-incremental-load-of-multiple-tables.md).</span></span>  
  
2.  <span data-ttu-id="1c20f-135">在 **[指令碼工作編輯器]** 的 **[指令碼]** 頁面上，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="1c20f-135">In the **Script Task Editor**, on the **Script** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="1c20f-136">針對 [ReadOnlyVariables]  ，選取 [User::DataReady]  、[User::ExtractStartTime]  和 [User::ExtractEndTime]  。</span><span class="sxs-lookup"><span data-stu-id="1c20f-136">For **ReadOnlyVariables**, select **User::DataReady**, **User::ExtractStartTime**, and **User::ExtractEndTime** from the.</span></span>  
  
    2.  <span data-ttu-id="1c20f-137">針對 [ReadWriteVariables]  ，從清單中選取 [User::SqlDataQuery]。</span><span class="sxs-lookup"><span data-stu-id="1c20f-137">For **ReadWriteVariables**, select User::SqlDataQuery from the list.</span></span>  
  
3.  <span data-ttu-id="1c20f-138">在 **[指令碼工作編輯器]** 的 **[指令碼]** 頁面上，按一下 **[編輯指令碼]** 來開啟指令碼開發環境。</span><span class="sxs-lookup"><span data-stu-id="1c20f-138">In the **Script Task Editor**, on the **Script** page, click **Edit Script** to open the script development environment.</span></span>  
  
4.  <span data-ttu-id="1c20f-139">在 Main 程序中，輸入下列其中一個程式碼區段：</span><span class="sxs-lookup"><span data-stu-id="1c20f-139">In the Main procedure, enter one of the following code segments:</span></span>  
  
    -   <span data-ttu-id="1c20f-140">如果您是以 C# 撰寫程式，輸入下列程式碼行：</span><span class="sxs-lookup"><span data-stu-id="1c20f-140">If you are programming in C#, enter the following lines of code:</span></span>  
  
        ```  
        int dataReady;  
        System.DateTime extractStartTime;  
        System.DateTime extractEndTime;  
        string sqlDataQuery;  
  
        dataReady = (int)Dts.Variables["DataReady"].Value;  
        extractStartTime = (System.DateTime)Dts.Variables["ExtractStartTime"].Value;  
        extractEndTime = (System.DateTime)Dts.Variables["ExtractEndTime"].Value;  
  
        if (dataReady == 2)  
          {  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer('" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractStartTime) + "', '" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) + "')";  
          }  
        else  
          {  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer(null" + ", '" + string.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) + "')";  
          }  
  
        Dts.Variables["SqlDataQuery"].Value = sqlDataQuery;  
        ```  
  
         <span data-ttu-id="1c20f-141">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="1c20f-141">\- or -</span></span>  
  
    -   <span data-ttu-id="1c20f-142">如果您是以 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]撰寫程式，輸入下列程式碼行：</span><span class="sxs-lookup"><span data-stu-id="1c20f-142">If you are programming in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], enter the following lines of code:</span></span>  
  
        ```  
        Dim dataReady As Integer  
        Dim extractStartTime As Date  
        Dim extractEndTime As Date  
        Dim sqlDataQuery As String  
  
        dataReady = CType(Dts.Variables("DataReady").Value, Integer)  
        extractStartTime = CType(Dts.Variables("ExtractStartTime").Value, Date)  
        extractEndTime = CType(Dts.Variables("ExtractEndTime").Value, Date)  
  
        If dataReady = 2 Then  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer('" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractStartTime) & _  
              "', '" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) & _  
              "')"  
        Else  
          sqlDataQuery = "SELECT * FROM CDCSample.uf_Customer(null" & _  
              ", '" & _  
              String.Format("{0:yyyy-MM-dd hh:mm:ss}", extractEndTime) & _  
              "')"  
        End If  
  
        Dts.Variables("SqlDataQuery").Value = sqlDataQuery  
  
        ```  
  
5.  <span data-ttu-id="1c20f-143">保留從指令碼之執行傳回 `DtsExecResult.Success` 的預設程式碼行。</span><span class="sxs-lookup"><span data-stu-id="1c20f-143">Leave the default line of code which returns `DtsExecResult.Success` from the execution of the script.</span></span>  
  
6.  <span data-ttu-id="1c20f-144">關閉指令碼開發環境以及 **[指令碼工作編輯器]** 。</span><span class="sxs-lookup"><span data-stu-id="1c20f-144">Close the script development environment and the **Script Task Editor**.</span></span>  
  
#### <a name="to-use-an-execute-sql-task-to-concatenate-the-query-string"></a><span data-ttu-id="1c20f-145">使用執行 SQL 工作串連查詢字串</span><span class="sxs-lookup"><span data-stu-id="1c20f-145">To use an Execute SQL task to concatenate the query string</span></span>  
  
1.  <span data-ttu-id="1c20f-146">在 [控制流程]  索引標籤上，將「執行 SQL」工作加入「For 迴圈」容器後的封裝中，然後將「For 迴圈」容器連接到此工作。</span><span class="sxs-lookup"><span data-stu-id="1c20f-146">On the **Control Flow** tab, add an Execute SQL task to the package after the For Loop container and connect the For Loop container to this task.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="1c20f-147">此程序假設封裝會從單一資料表執行累加式載入。</span><span class="sxs-lookup"><span data-stu-id="1c20f-147">This procedure assumes that the package performs an incremental load from a single table.</span></span> <span data-ttu-id="1c20f-148">如果封裝從多個資料表載入，而且擁有包含多個子封裝的父封裝，則會將此工作當做第一個元件，加入到每個子封裝中。</span><span class="sxs-lookup"><span data-stu-id="1c20f-148">If the package loads from multiple tables and has a parent package with multiple child packages, this task would be added as the first component to each child package.</span></span> <span data-ttu-id="1c20f-149">如需詳細資訊，請參閱 [執行多個資料表的累加式載入](perform-an-incremental-load-of-multiple-tables.md)。</span><span class="sxs-lookup"><span data-stu-id="1c20f-149">For more information, see [Perform an Incremental Load of Multiple Tables](perform-an-incremental-load-of-multiple-tables.md).</span></span>  
  
2.  <span data-ttu-id="1c20f-150">在 **[執行 SQL 工作編輯器]** 的 **[一般]** 頁面上，選取下列選項：</span><span class="sxs-lookup"><span data-stu-id="1c20f-150">In the **Execute SQL Task Editor**, on the **General** page, select the following options:</span></span>  
  
    1.  <span data-ttu-id="1c20f-151">針對 **[ResultSet]** ，選取 **[單一資料列]** 。</span><span class="sxs-lookup"><span data-stu-id="1c20f-151">For **ResultSet**, select **Single row**.</span></span>  
  
    2.  <span data-ttu-id="1c20f-152">將有效的連接設定到來源資料庫。</span><span class="sxs-lookup"><span data-stu-id="1c20f-152">Configure a valid connection to the source database.</span></span>  
  
    3.  <span data-ttu-id="1c20f-153">針對 **[SQLSourceType]** ，選取 **[直接輸入]** 。</span><span class="sxs-lookup"><span data-stu-id="1c20f-153">For **SQLSourceType**, select **Direct input**.</span></span>  
  
    4.  <span data-ttu-id="1c20f-154">針對 **[SQLStatement]** ，輸入下列 SQL 陳述式：</span><span class="sxs-lookup"><span data-stu-id="1c20f-154">For **SQLStatement**, enter the following SQL statement:</span></span>  
  
        ```  
        declare @ExtractStartTime datetime,  
        @ExtractEndTime datetime,   
        @DataReady int  
  
        select @DataReady = ?,   
        @ExtractStartTime = ?,   
        @ExtractEndTime = ?  
  
        if @DataReady = 2  
        select N'select * from CDCSample.uf_Customer'  
        + N'('''+ convert(nvarchar(30),@ExtractStartTime,120)  
        + ''', '''  
        + convert(nvarchar(30),@ExtractEndTime,120) + ''') '   
        as SqlDataQuery  
        else  
        select N'select * from CDCSample.uf_Customer'  
        + N'(null, '''  
        + convert(nvarchar(30),@ExtractEndTime,120)  
        + ''') '  
        as SqlDataQuery  
  
        ```  
  
        > [!NOTE]  
        >  <span data-ttu-id="1c20f-155">此範例中的 `else` 子句會傳遞開始日期和時間的 Null 值，藉以產生變更資料之初始載入的查詢。</span><span class="sxs-lookup"><span data-stu-id="1c20f-155">The `else` clause in this sample generates a query for the initial load of change data by passing a null value for the starting date and time.</span></span> <span data-ttu-id="1c20f-156">此範例不處理啟用異動資料擷取前所進行之變更也必須上傳到資料倉儲的狀況。</span><span class="sxs-lookup"><span data-stu-id="1c20f-156">This sample does not address the scenario in which changes that were made before change data capture was enabled also have to be uploaded to the data warehouse.</span></span>  
  
3.  <span data-ttu-id="1c20f-157">在 [執行 SQL 工作編輯器]  的 [參數對應]  頁面上，進行下列對應：</span><span class="sxs-lookup"><span data-stu-id="1c20f-157">On the **Parameter Mapping** page of the **Execute SQL Task Editor**, do the following mapping:</span></span>  
  
    1.  <span data-ttu-id="1c20f-158">將 DataReady 變數對應到參數 0。</span><span class="sxs-lookup"><span data-stu-id="1c20f-158">Map the DataReady variable to parameter 0.</span></span>  
  
    2.  <span data-ttu-id="1c20f-159">將 ExtractStartTime 變數對應到參數 1。</span><span class="sxs-lookup"><span data-stu-id="1c20f-159">Map the ExtractStartTime variable to parameter 1.</span></span>  
  
    3.  <span data-ttu-id="1c20f-160">將 ExtractEndTime 變數對應到參數 2。</span><span class="sxs-lookup"><span data-stu-id="1c20f-160">Map the ExtractEndTime variable to parameter 2.</span></span>  
  
4.  <span data-ttu-id="1c20f-161">在 [執行 SQL 工作編輯器]  的 [結果集]  頁面上，將 [結果名稱] 對應到 SqlDataQuery 變數。</span><span class="sxs-lookup"><span data-stu-id="1c20f-161">On the **Result Set** page of the **Execute SQL Task Editor**, map the Result Name to the SqlDataQuery variable.</span></span>  
  
     <span data-ttu-id="1c20f-162">[結果名稱] 是所傳回之單一資料行的名稱，也就是 SqlDataQuery。</span><span class="sxs-lookup"><span data-stu-id="1c20f-162">The Result Name is the name of the single column that is returned, SqlDataQuery.</span></span>  
  
 <span data-ttu-id="1c20f-163">上一個程序會利用輸入參數的硬式編碼字串值，設定可準備查詢字串的工作。</span><span class="sxs-lookup"><span data-stu-id="1c20f-163">The previous procedures configure a task that prepares a query string with hard-coded string values for the input parameters.</span></span> <span data-ttu-id="1c20f-164">下列程式碼為此種查詢字串的範例：</span><span class="sxs-lookup"><span data-stu-id="1c20f-164">The following code is an example of such a query string:</span></span>  
  
 `select * from CDCSample. uf_Customer('2007-06-11 14:21:58', '2007-06-12 14:21:58')`  
  
## <a name="adding-a-data-flow-task"></a><span data-ttu-id="1c20f-165">加入資料流程工作</span><span class="sxs-lookup"><span data-stu-id="1c20f-165">Adding a Data Flow Task</span></span>  
 <span data-ttu-id="1c20f-166">設計封裝之控制流程的最後一個步驟是加入「資料流程」工作。</span><span class="sxs-lookup"><span data-stu-id="1c20f-166">The last step in designing the control flow for the package is to add a Data Flow task.</span></span>  
  
#### <a name="to-add-a-data-flow-task-and-complete-the-control-flow"></a><span data-ttu-id="1c20f-167">加入資料流程工作並完成控制流程</span><span class="sxs-lookup"><span data-stu-id="1c20f-167">To add a Data Flow task and complete the control flow</span></span>  
  
-   <span data-ttu-id="1c20f-168">在 [控制流程]  索引標籤上，加入「資料流程」工作，然後連接串連查詢字串的工作。</span><span class="sxs-lookup"><span data-stu-id="1c20f-168">On the **Control Flow** tab, add a Data Flow task and connect the task that concatenated the query string.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="1c20f-169">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1c20f-169">Next Step</span></span>  
 <span data-ttu-id="1c20f-170">準備查詢字串並設定「資料流程」工作後，下一個步驟是建立將從資料庫擷取變更資料的資料表值函式。</span><span class="sxs-lookup"><span data-stu-id="1c20f-170">After you prepare the query string and configure the Data Flow task, the next step is create the table-valued function that will retrieve the change data from the database.</span></span>  
  
 <span data-ttu-id="1c20f-171">**下一個主題：** [建立函式以擷取變更資料](create-the-function-to-retrieve-the-change-data.md)</span><span class="sxs-lookup"><span data-stu-id="1c20f-171">**Next topic:** [Create the Function to Retrieve the Change Data](create-the-function-to-retrieve-the-change-data.md)</span></span>  
  
  
