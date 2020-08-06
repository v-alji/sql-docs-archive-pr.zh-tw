---
title: 查看事件會話資料 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: ac742a01-2a95-42c7-b65e-ad565020dc49
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: eaeb5fd22b95b8f1056b8dce9e3c7d683b52602f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708565"
---
# <a name="view-event-session-data"></a><span data-ttu-id="3cce1-102">檢視事件工作階段資料</span><span class="sxs-lookup"><span data-stu-id="3cce1-102">View Event Session Data</span></span>
  <span data-ttu-id="3cce1-103">本主題描述如何使用顯示使用者介面來查看並分析擴充事件資料：</span><span class="sxs-lookup"><span data-stu-id="3cce1-103">This topic describes using the display user interface to see and analyze extended event data:</span></span>  
  
-   <span data-ttu-id="3cce1-104">檢視目標資料</span><span class="sxs-lookup"><span data-stu-id="3cce1-104">View Target Data</span></span>  
  
-   <span data-ttu-id="3cce1-105">使用資料</span><span class="sxs-lookup"><span data-stu-id="3cce1-105">Working With Data</span></span>  
  
## <a name="view-target-data"></a><span data-ttu-id="3cce1-106">檢視目標資料</span><span class="sxs-lookup"><span data-stu-id="3cce1-106">View Target Data</span></span>  
 <span data-ttu-id="3cce1-107">您可以在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中顯示收集到指定目標內的資料。</span><span class="sxs-lookup"><span data-stu-id="3cce1-107">You can display the data collected into the specified target within [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="view-target-data"></a><span data-ttu-id="3cce1-108">檢視目標資料</span><span class="sxs-lookup"><span data-stu-id="3cce1-108">View Target Data</span></span>  
 <span data-ttu-id="3cce1-109">若要檢視目標資料：</span><span class="sxs-lookup"><span data-stu-id="3cce1-109">To view target data:</span></span>  
  
1.  <span data-ttu-id="3cce1-110">在 [物件總管] 中，依序展開 **[管理]**、 **[擴充事件]** 和 **[工作階段]**，然後展開工作階段。</span><span class="sxs-lookup"><span data-stu-id="3cce1-110">In Object Explorer, expand **Management**, **Extended Events**, **Sessions**, and then a session.</span></span>  
  
2.  <span data-ttu-id="3cce1-111">以滑鼠右鍵按一下目標名稱，然後按一下 **[檢視目標資料]** 顯示目標資料。</span><span class="sxs-lookup"><span data-stu-id="3cce1-111">Right-click the target name, and then click **View Target Data** to display the target data.</span></span>  
  
     <span data-ttu-id="3cce1-112">目標資料視窗會出現在預設檢視中，並顯示目標資料。</span><span class="sxs-lookup"><span data-stu-id="3cce1-112">The target data window appears in default view and displays the target data.</span></span>  
  
 <span data-ttu-id="3cce1-113">有關檢視目標資料的注意事項：</span><span class="sxs-lookup"><span data-stu-id="3cce1-113">Notes on viewing target data:</span></span>  
  
-   <span data-ttu-id="3cce1-114">目標資料不適用於 ETW 目標。</span><span class="sxs-lookup"><span data-stu-id="3cce1-114">Target data is not available for the ETW target.</span></span>  
  
-   <span data-ttu-id="3cce1-115">若要檢視 xml 格式的 ring_buffer 資料，請在目標資料視窗中按一下 **[ring_buffer 目標資料]** 連結。</span><span class="sxs-lookup"><span data-stu-id="3cce1-115">To view the ring_buffer data in xml format, in the target data window click the **ring_buffer target data** link.</span></span> <span data-ttu-id="3cce1-116">ring_buffer.xml 檔案就會出現在 xml 編輯器中。</span><span class="sxs-lookup"><span data-stu-id="3cce1-116">The ring_buffer.xml file appears in the xml editor.</span></span>  
  
-   <span data-ttu-id="3cce1-117">若為 event_file 目標，請使用下列其中一種方法來檢視檔案目標資料 (.XEL 檔案)：</span><span class="sxs-lookup"><span data-stu-id="3cce1-117">For an event_file target, view the file target data (.XEL file) using one of the following methods:</span></span>  
  
    -   <span data-ttu-id="3cce1-118">使用檔案 > 在中開啟 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3cce1-118">Use File -> Open in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>
    
    -   <span data-ttu-id="3cce1-119">將檔案拖放到 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="3cce1-119">Drag and drop the file into [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span> 
    
    -   <span data-ttu-id="3cce1-120">按兩下 .XEL 檔案。</span><span class="sxs-lookup"><span data-stu-id="3cce1-120">Double click the .XEL file.</span></span>  
    
    -   <span data-ttu-id="3cce1-121">在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]中，以滑鼠右鍵按一下執行中的「擴充事件」工作階段，然後選取 [檢視目標資料]。</span><span class="sxs-lookup"><span data-stu-id="3cce1-121">In [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)], right click on a running Extended Events session and select View Target Data.</span></span> 
    
    -   <span data-ttu-id="3cce1-122">[fn_xe_file_target_read_file](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="3cce1-122">[fn_xe_file_target_read_file](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql).</span></span>
    
    -   <span data-ttu-id="3cce1-123">使用[SQLServer 模組](https://www.powershellgallery.com/packages/SqlServer.XEvent)中的 Powershell 讀取 SQLXevent。</span><span class="sxs-lookup"><span data-stu-id="3cce1-123">Use Powershell Read-SQLXevent in [SQLServer.XEvent module](https://www.powershellgallery.com/packages/SqlServer.XEvent).</span></span>
    
    -   <span data-ttu-id="3cce1-124">以程式設計方式使用[XELite NuGet](https://www.nuget.org/packages/Microsoft.SqlServer.XEvent.XELite)來取用 XEvents。</span><span class="sxs-lookup"><span data-stu-id="3cce1-124">Programmatically consume XEvents by using the [XELite NuGet](https://www.nuget.org/packages/Microsoft.SqlServer.XEvent.XELite).</span></span>
    
    -   <span data-ttu-id="3cce1-125">您可以查看一個以上的。從 [檔案->] [開啟] 功能表中選取 [**合併擴充事件**檔案]，以 .xel 檔案。</span><span class="sxs-lookup"><span data-stu-id="3cce1-125">You can view more than one .XEL file by selecting **Merge Extended Event Files** from the File -> Open menu.</span></span>

### <a name="watching-live-data"></a><span data-ttu-id="3cce1-126">監看即時資料</span><span class="sxs-lookup"><span data-stu-id="3cce1-126">Watching Live Data</span></span>  
 <span data-ttu-id="3cce1-127">您可以監看正在擷取的即時資料。</span><span class="sxs-lookup"><span data-stu-id="3cce1-127">You can watch live data as it is being captured.</span></span>  
  
-   <span data-ttu-id="3cce1-128">在物件總管中，依序展開 [**管理**]、[**擴充事件**] 和 [**會話**] 節點。</span><span class="sxs-lookup"><span data-stu-id="3cce1-128">In Object Explorer, expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  

-   <span data-ttu-id="3cce1-129">以滑鼠右鍵按一下工作階段名稱，然後按一下 **[監看即時資料]** ，開始顯示追蹤資料。</span><span class="sxs-lookup"><span data-stu-id="3cce1-129">Right-click the session name and then click **Watch Live Data** to start displaying the tracing data.</span></span>  
  
     <span data-ttu-id="3cce1-130">預設顯示資料行為 **[事件名稱]** 和 **[時間戳記]**。</span><span class="sxs-lookup"><span data-stu-id="3cce1-130">The default display columns are **Event Name** and **TimeStamp**.</span></span>  
  
     <span data-ttu-id="3cce1-131">若要在追蹤視窗中加入其他資料行，請按一下 [擴充事件] 工具列上的 **[選擇資料行]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3cce1-131">To add additional columns to the trace window, click the **Choose Columns** button on the Extended Events toolbar.</span></span> <span data-ttu-id="3cce1-132">**[詳細資料]** 索引標籤會顯示選定事件的所有事件詳細資料。</span><span class="sxs-lookup"><span data-stu-id="3cce1-132">The **Details** tab shows all of the event details for the selected event.</span></span>  
  
     <span data-ttu-id="3cce1-133">事件通常會在約 30 秒內顯示。</span><span class="sxs-lookup"><span data-stu-id="3cce1-133">Events are usually displayed in approximately 30 seconds.</span></span> <span data-ttu-id="3cce1-134">如果您想要變更延遲期間，可以在 **[新增工作階段]** 對話方塊的 **[進階]** 頁面上變更 **[最大分派延遲]** 。</span><span class="sxs-lookup"><span data-stu-id="3cce1-134">If you want to change the latency period, you can change the **Maximum dispatch latency** on the **Advanced** page of the of the **New Session** dialog.</span></span>  
     
-    <span data-ttu-id="3cce1-135">您可以透過[SqlServer PowerShell 模組](https://www.powershellgallery.com/packages/SqlServer.XEvent)來串流處理即時資料。</span><span class="sxs-lookup"><span data-stu-id="3cce1-135">Live data can be streamed by the [SqlServer.XEvent PowerShell module](https://www.powershellgallery.com/packages/SqlServer.XEvent).</span></span>
     
### <a name="to-refresh-target-data"></a><span data-ttu-id="3cce1-136">若要重新整理目標資料</span><span class="sxs-lookup"><span data-stu-id="3cce1-136">To Refresh Target Data</span></span>  
 <span data-ttu-id="3cce1-137">event_files 目標不支援重新整理目標資料：</span><span class="sxs-lookup"><span data-stu-id="3cce1-137">Refreshing target data is not supported for event_files targets:</span></span>  
  
1.  <span data-ttu-id="3cce1-138">若要自動重新整理目標資料，請以滑鼠右鍵按一下目標資料、選取 **[重新整理間隔]**，然後從間隔清單中選取重新整理間隔。</span><span class="sxs-lookup"><span data-stu-id="3cce1-138">To refresh the target data automatically, right click the target data, select **Refresh Interval**, and then select the refresh interval from the interval list.</span></span>  
  
2.  <span data-ttu-id="3cce1-139">若要暫停及繼續自動重新整理，請以滑鼠右鍵按一下目標資料，然後選取 **[暫停]** 或 **[繼續]**。</span><span class="sxs-lookup"><span data-stu-id="3cce1-139">To pause and resume the automatic refresh, right-click the target data and then select **Pause** or **Resume**.</span></span>  
  
3.  <span data-ttu-id="3cce1-140">若要手動重新整理目標資料，請以滑鼠右鍵按一下目標名稱，然後選取 **[重新整理]**。</span><span class="sxs-lookup"><span data-stu-id="3cce1-140">To refresh the target data manually, right click the target data, and then select **Refresh**.</span></span>  
  
## <a name="working-with-data"></a><span data-ttu-id="3cce1-141">使用資料</span><span class="sxs-lookup"><span data-stu-id="3cce1-141">Working With Data</span></span>  
 <span data-ttu-id="3cce1-142">您可以使用 [擴充事件] 使用者介面的分析功能來識別問題。</span><span class="sxs-lookup"><span data-stu-id="3cce1-142">You can use the analysis capabilities of the Extended Events user interface to identify problems.</span></span>  
  
### <a name="details-pane"></a><span data-ttu-id="3cce1-143">詳細資料窗格</span><span class="sxs-lookup"><span data-stu-id="3cce1-143">Details Pane</span></span>  
 <span data-ttu-id="3cce1-144">**[詳細資料]** 窗格會顯示選取事件的所有資料行，包括欄位和動作。</span><span class="sxs-lookup"><span data-stu-id="3cce1-144">The **Details** pane shows all the columns for the selected event, including fields and actions.</span></span> <span data-ttu-id="3cce1-145">您可以用滑鼠右鍵按一下 **[詳細資料]** 窗格中的資料列，然後選取 **[顯示資料表中的資料行]**，藉以將資料行加入至目標資料表。</span><span class="sxs-lookup"><span data-stu-id="3cce1-145">You can add a column to the target data table by right-clicking a row in the **Details** pane and selecting **Show Column in Table**.</span></span>  
  
### <a name="create-modify-or-delete-merged-columns"></a><span data-ttu-id="3cce1-146">建立、修改或刪除合併的資料行</span><span class="sxs-lookup"><span data-stu-id="3cce1-146">Create, Modify, or Delete Merged Columns</span></span>  
 <span data-ttu-id="3cce1-147">合併的資料行可讓您結合一組要顯示在單一資料行中的欄位。</span><span class="sxs-lookup"><span data-stu-id="3cce1-147">A merged column allows you to combine a set of fields to be displayed in a single column.</span></span> <span data-ttu-id="3cce1-148">合併的資料行將根據欄位加入至欄位清單的順序，顯示第一個非 NULL 欄位中的資料。</span><span class="sxs-lookup"><span data-stu-id="3cce1-148">The merged column will show the data from the first non-NULL field based on the order they are added to the field list.</span></span> <span data-ttu-id="3cce1-149">這與您在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler 中看見的內容很相似，其中特定資料行可能會根據事件顯示不同的資料 (最常見的範例就是 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler 中的 TextData 欄位)。</span><span class="sxs-lookup"><span data-stu-id="3cce1-149">This is similar to what you see in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler, where a specific column may show different data depending on the event (the most common example of this is the TextData field in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Profiler).</span></span> <span data-ttu-id="3cce1-150">例如，您可能會分別將 sql_statement_completed 和 sql_batch_completed 事件中的 statement 和 batch_text 欄位合併成名為 myStatement 的欄位。</span><span class="sxs-lookup"><span data-stu-id="3cce1-150">For an example, you could merge the statement and batch_text fields from the sql_statement_completed and sql_batch_completed events, respectively, into a field named myStatement.</span></span> <span data-ttu-id="3cce1-151">當您在資料表中顯示 myStatement 資料行時，它將針對相關聯的事件顯示適當的資料。</span><span class="sxs-lookup"><span data-stu-id="3cce1-151">When you display the myStatement column in the table it will show the appropriate data for the associated event.</span></span>  
  
 <span data-ttu-id="3cce1-152">您可以建立、修改或刪除合併的資料行：</span><span class="sxs-lookup"><span data-stu-id="3cce1-152">You can create, modify, or delete merged columns:</span></span>  
  
1.  <span data-ttu-id="3cce1-153">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="3cce1-153">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="3cce1-154"> (您也可以用滑鼠右鍵按一下會話名稱，然後選取 **[監看即時資料]**。 ) </span><span class="sxs-lookup"><span data-stu-id="3cce1-154">(You can also right click the session name, and then select **Watch Live Data**.)</span></span>  
  
2.  <span data-ttu-id="3cce1-155">在追蹤結果視窗中，以滑鼠右鍵按一下資料行標頭，然後按一下 **[選擇資料行]**。</span><span class="sxs-lookup"><span data-stu-id="3cce1-155">In the trace results window, right-click the column header, and then click **Choose Columns**.</span></span>  
  
 <span data-ttu-id="3cce1-156">若要建立合併的資料行，請在 **[選擇資料行]** 對話方塊中按一下 **[新增]** 。</span><span class="sxs-lookup"><span data-stu-id="3cce1-156">To create a merged column, click **New** in the **Choose Columns** dialog box.</span></span>  <span data-ttu-id="3cce1-157">在 **[新增合併的資料行]** 對話方塊中，為合併的資料行命名，然後選取要包含在合併資料行中的原始資料行。</span><span class="sxs-lookup"><span data-stu-id="3cce1-157">In the **New Merged Column** dialog, name the merged column and select the original columns to be included in the merged column.</span></span>  
  
 <span data-ttu-id="3cce1-158">若要編輯合併的資料行，請在 **[選擇資料行]** 對話方塊中選取合併的資料行，然後按一下 **[編輯]**。</span><span class="sxs-lookup"><span data-stu-id="3cce1-158">To edit a merged column, select a merged column in the **Choose Columns** dialog and click **Edit**.</span></span> <span data-ttu-id="3cce1-159">在 **[編輯合併的資料行]** 對話方塊中，重新命名合併的資料行，或修改要包含在合併資料行中的原始資料行。</span><span class="sxs-lookup"><span data-stu-id="3cce1-159">In the **Edit Merged Column** dialog, rename the merged column or modify the original columns to be included in the merged column.</span></span>  
  
 <span data-ttu-id="3cce1-160">若要刪除合併的資料行，請在 **[選擇資料行]** 對話方塊中選取合併的資料行，然後按一下 **[刪除]**。</span><span class="sxs-lookup"><span data-stu-id="3cce1-160">To delete a merged column, select a merged column in the **Choose Columns** dialog and click **Delete**.</span></span>  
  
### <a name="filter-results"></a><span data-ttu-id="3cce1-161">篩選結果</span><span class="sxs-lookup"><span data-stu-id="3cce1-161">Filter Results</span></span>  
 <span data-ttu-id="3cce1-162">您可以檢視追蹤結果，然後套用篩選以縮小追蹤視窗中顯示的追蹤結果範圍。</span><span class="sxs-lookup"><span data-stu-id="3cce1-162">You can view trace results, and then apply filters to narrow down the trace results that are displayed in the trace window.</span></span> <span data-ttu-id="3cce1-163">顯示篩選包含時間篩選和進階篩選。</span><span class="sxs-lookup"><span data-stu-id="3cce1-163">The display filter includes a time filter and an advanced filter.</span></span> <span data-ttu-id="3cce1-164">時間篩選可用來依事件時間戳記篩選追蹤結果，而進階篩選可用來透過事件欄位和動作建構篩選條件。</span><span class="sxs-lookup"><span data-stu-id="3cce1-164">You use the time filter to filter the trace results by event timestamp, and you use the advanced filter to construct filter conditions using the event fields and actions.</span></span> <span data-ttu-id="3cce1-165">時間篩選和進階篩選之間存在「及」關聯性。</span><span class="sxs-lookup"><span data-stu-id="3cce1-165">There is an "and" relationship between the time and advanced filters.</span></span>  
  
 <span data-ttu-id="3cce1-166">若要建立篩選：</span><span class="sxs-lookup"><span data-stu-id="3cce1-166">To create a filter:</span></span>  
  
1.  <span data-ttu-id="3cce1-167">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="3cce1-167">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="3cce1-168"> (您也可以用滑鼠右鍵按一下會話名稱，然後選取 **[監看即時資料]**。 ) </span><span class="sxs-lookup"><span data-stu-id="3cce1-168">(You can also right click the session name, and then select **Watch Live Data**.)</span></span>  
  
2.  <span data-ttu-id="3cce1-169">在追蹤結果視窗中選取要篩選的結果，然後在 **[擴充事件]** 工具列上按一下 **[篩選]**。</span><span class="sxs-lookup"><span data-stu-id="3cce1-169">In the trace results window, select the results you want to filter, and then on the **Extended Events** toolbar, click **Filters**.</span></span>  
  
3.  <span data-ttu-id="3cce1-170">在 **[篩選]** 對話方塊中，選取 **[設定時間篩選]** 以透過拖曳滑動軸或修改編輯方塊中的時間來設定時間篩選。</span><span class="sxs-lookup"><span data-stu-id="3cce1-170">In the **Filters** dialog box, select **Set time filter** to set the time filter by dragging the slider bars or modifying the time in the edit box.</span></span>  
  
4.  <span data-ttu-id="3cce1-171">在 **[其他篩選]** 區段中，套用篩選準則，然後按一下 **[套用]**。</span><span class="sxs-lookup"><span data-stu-id="3cce1-171">In the **Additional filters** section, apply your filter criteria, and then click **Apply**.</span></span>  
  
### <a name="sort-results"></a><span data-ttu-id="3cce1-172">排序結果</span><span class="sxs-lookup"><span data-stu-id="3cce1-172">Sort Results</span></span>  
 <span data-ttu-id="3cce1-173">若要以遞增或遞減順序排序結果：</span><span class="sxs-lookup"><span data-stu-id="3cce1-173">To sort results either in ascending or descending order:</span></span>  
  
1.  <span data-ttu-id="3cce1-174">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="3cce1-174">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="3cce1-175"> (您也可以用滑鼠右鍵按一下會話名稱、選取 **[監看即時資料]**，然後按一下工具列上的 [**停止資料**摘要] 按鈕。 ) </span><span class="sxs-lookup"><span data-stu-id="3cce1-175">(You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.)</span></span>  
  
2.  <span data-ttu-id="3cce1-176">在追蹤結果視窗中，以滑鼠右鍵按一下您想要排序的資料行標題，然後按一下 **[遞增排序]** 或 **[遞減排序]**。</span><span class="sxs-lookup"><span data-stu-id="3cce1-176">In the trace results window, right-click the column heading you want to sort and click **Sort Ascending** or **Sort Descending**.</span></span>  
  
 <span data-ttu-id="3cce1-177">您也可以按一下資料行標頭來反轉排序次序。</span><span class="sxs-lookup"><span data-stu-id="3cce1-177">You can also click the column header to reverse the sort order.</span></span>  
  
 <span data-ttu-id="3cce1-178">如果已對資料行進行分組，則資料行排序只會對群組中的資料進行排序。</span><span class="sxs-lookup"><span data-stu-id="3cce1-178">If you have grouped columns, sorting the column will only sort data within the group.</span></span>  
  
### <a name="group-results"></a><span data-ttu-id="3cce1-179">將結果分組</span><span class="sxs-lookup"><span data-stu-id="3cce1-179">Group Results</span></span>  
 <span data-ttu-id="3cce1-180">分組的結果就相當於 [!INCLUDE[tsql](../includes/tsql-md.md)] 中 `GROUP BY` 子句的功能。</span><span class="sxs-lookup"><span data-stu-id="3cce1-180">Grouped results are equivalent to the functionality of the `GROUP BY` clause in [!INCLUDE[tsql](../includes/tsql-md.md)].</span></span> <span data-ttu-id="3cce1-181">目標資料表將顯示分成一組的資料，讓您展開或摺疊資料。</span><span class="sxs-lookup"><span data-stu-id="3cce1-181">The target data table will show the data grouped together, allowing you to expand and collapse the data.</span></span>  
  
 <span data-ttu-id="3cce1-182">您必須先將資料分組，然後才能進行彙總。</span><span class="sxs-lookup"><span data-stu-id="3cce1-182">You must group data before you can aggregate it.</span></span> <span data-ttu-id="3cce1-183">例如，您可以針對 query_hash 值分組、依照持續時間遞減排序、取得每個群組的平均持續時間，然後針對彙總遞減排序。</span><span class="sxs-lookup"><span data-stu-id="3cce1-183">For example, you can group on the query_hash value, sort descending by duration, get the average duration for each group, and then sort descending on the aggregation.</span></span>  <span data-ttu-id="3cce1-184">這樣就會產生一份清單，其中列出平均持續時間最長到最短的唯一陳述式。</span><span class="sxs-lookup"><span data-stu-id="3cce1-184">This will produce a list that shows the list of unique statements from longest to shortest average duration.</span></span> <span data-ttu-id="3cce1-185">當您展開最上方的群組時，就會看見該特定查詢的個別執行時間 (從最長到最短排序)。</span><span class="sxs-lookup"><span data-stu-id="3cce1-185">When you expand the top group you will see the individual executions of that specific query sorted from longest to shortest.</span></span>  
  
 <span data-ttu-id="3cce1-186">您可以依照單一資料行或多個資料行，將結果分組。</span><span class="sxs-lookup"><span data-stu-id="3cce1-186">You can group results by a single column or by multiple columns.</span></span>  
  
 <span data-ttu-id="3cce1-187">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="3cce1-187">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="3cce1-188"> (您也可以用滑鼠右鍵按一下會話名稱、選取 **[監看即時資料]**，然後按一下工具列上的 [**停止資料**摘要] 按鈕。 ) </span><span class="sxs-lookup"><span data-stu-id="3cce1-188">(You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.)</span></span>  
  
 <span data-ttu-id="3cce1-189">若要依照單一資料行，將結果分組，請以滑鼠右鍵按一下追蹤結果視窗中的資料行標題，然後按一下 **[依此資料行群組]**。</span><span class="sxs-lookup"><span data-stu-id="3cce1-189">To group results by a single column, right-click the column heading in the trace results window, and click **Group by this Column**.</span></span> <span data-ttu-id="3cce1-190">若要恢復分組，請選取其中一個資料列，然後按一下 **[移除所有群組]**。</span><span class="sxs-lookup"><span data-stu-id="3cce1-190">To undo the grouping, select one of the rows and click **Remove All Groupings**.</span></span>  
  
 <span data-ttu-id="3cce1-191">若要依照多個資料行，將結果分組，請按一下 **[擴充事件]** 工具列上的 **[群組]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3cce1-191">To group results by a multiple columns, click the **Grouping** button on the **Extended Events** toolbar.</span></span> <span data-ttu-id="3cce1-192">在 **[群組]** 對話方塊的 **[可用的資料行]** 方塊中，選取您想要分組的資料行，然後將它們移至 **[群組的資料行依據]** 方塊中。</span><span class="sxs-lookup"><span data-stu-id="3cce1-192">In the **Available columns** box of the **Grouping** dialog, select the columns you want to group, and move them into the **Columns grouped on** box.</span></span> <span data-ttu-id="3cce1-193">若要變更 **[群組的資料行依據]** 方塊中的順序，請按一下向上箭頭或向下箭頭。</span><span class="sxs-lookup"><span data-stu-id="3cce1-193">To change the order in the **Columns grouped on** box, click the up or down arrows.</span></span>  
  
### <a name="aggregate-results"></a><span data-ttu-id="3cce1-194">彙總結果</span><span class="sxs-lookup"><span data-stu-id="3cce1-194">Aggregate Results</span></span>  
 <span data-ttu-id="3cce1-195">您可以檢視追蹤結果，然後透過彙總結果中的資料行來進一步分析事件資料。</span><span class="sxs-lookup"><span data-stu-id="3cce1-195">You can view the trace results, and then further analyze your event data by aggregating columns in your results.</span></span> <span data-ttu-id="3cce1-196">擴充事件支援五個彙總函式：</span><span class="sxs-lookup"><span data-stu-id="3cce1-196">Extended Events supports five aggregation functions:</span></span>  
  
-   <span data-ttu-id="3cce1-197">Sum</span><span class="sxs-lookup"><span data-stu-id="3cce1-197">sum</span></span>  
  
-   <span data-ttu-id="3cce1-198">Min</span><span class="sxs-lookup"><span data-stu-id="3cce1-198">min</span></span>  
  
-   <span data-ttu-id="3cce1-199">max</span><span class="sxs-lookup"><span data-stu-id="3cce1-199">max</span></span>  
  
-   <span data-ttu-id="3cce1-200">average</span><span class="sxs-lookup"><span data-stu-id="3cce1-200">average</span></span>  
  
-   <span data-ttu-id="3cce1-201">計數</span><span class="sxs-lookup"><span data-stu-id="3cce1-201">count</span></span>  
  
 <span data-ttu-id="3cce1-202">Sum、Min、Max 和 Average 只能搭配數值資料行使用。</span><span class="sxs-lookup"><span data-stu-id="3cce1-202">Sum, min, max, and average can only be used with numeric columns.</span></span> <span data-ttu-id="3cce1-203">Count 是群組中所選資料行的非 Null 值數目。</span><span class="sxs-lookup"><span data-stu-id="3cce1-203">Count is the number of non-null values that exist for the selected column in the group.</span></span>  
  
 <span data-ttu-id="3cce1-204">由於彙總是針對群組執行，因此您必須先將結果分組，然後才能執行彙總。</span><span class="sxs-lookup"><span data-stu-id="3cce1-204">Aggregation is performed on a group, so you must group the results before you can perform the aggregation.</span></span> <span data-ttu-id="3cce1-205">若要彙總結果：</span><span class="sxs-lookup"><span data-stu-id="3cce1-205">To aggregate results:</span></span>  
  
1.  <span data-ttu-id="3cce1-206">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="3cce1-206">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="3cce1-207"> (您也可以用滑鼠右鍵按一下會話名稱、選取 **[監看即時資料]**，然後按一下工具列上的 [**停止資料**摘要] 按鈕。 ) </span><span class="sxs-lookup"><span data-stu-id="3cce1-207">(You can also right click the session name, select **Watch Live Data**, and then click the **Stop Data Feed** button on the toolbar.)</span></span>  
  
2.  <span data-ttu-id="3cce1-208">在 **[擴充事件]** 工具列上，按一下 **[彙總]** 按鈕。</span><span class="sxs-lookup"><span data-stu-id="3cce1-208">On the **Extended Events** toolbar, click the **Aggregation** button.</span></span> <span data-ttu-id="3cce1-209">[彙總] 對話方塊將會顯示可用於彙總的資料行。</span><span class="sxs-lookup"><span data-stu-id="3cce1-209">The Aggregation dialog box will display the columns available for aggregation.</span></span>  
  
3.  <span data-ttu-id="3cce1-210">在 **[彙總類型]** 資料行中，選取彙總類型。</span><span class="sxs-lookup"><span data-stu-id="3cce1-210">In the **Aggregation Type** column, select the aggregation type.</span></span>  
  
4.  <span data-ttu-id="3cce1-211">在 **[彙總排序依據]** 方塊中，選取排序資料行。</span><span class="sxs-lookup"><span data-stu-id="3cce1-211">In the **Sort aggregation by** box, select the sort column.</span></span> <span data-ttu-id="3cce1-212">然後，選取遞增或遞減順序。</span><span class="sxs-lookup"><span data-stu-id="3cce1-212">Then select ascending or descending order.</span></span>  
  
### <a name="search-for-text-in-columns"></a><span data-ttu-id="3cce1-213">在資料行中搜尋文字</span><span class="sxs-lookup"><span data-stu-id="3cce1-213">Search for Text in Columns</span></span>  
 <span data-ttu-id="3cce1-214">您可以在資料行中搜尋文字：</span><span class="sxs-lookup"><span data-stu-id="3cce1-214">You can search for text in columns:</span></span>  
  
1.  <span data-ttu-id="3cce1-215">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="3cce1-215">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="3cce1-216">(您也可以用滑鼠右鍵按一下工作階段名稱，然後選取 **[監看即時資料]**)。</span><span class="sxs-lookup"><span data-stu-id="3cce1-216">(You can also right click the session name, select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="3cce1-217">按一下 **[擴充事件]** 工具列上的 **[尋找]** 。</span><span class="sxs-lookup"><span data-stu-id="3cce1-217">Click **Find** on the **Extended Events** toolbar.</span></span>  
  
3.  <span data-ttu-id="3cce1-218">在 **[在擴充事件中尋找]** 對話方塊的 **[尋找目標]** 方塊中，輸入搜尋文字。</span><span class="sxs-lookup"><span data-stu-id="3cce1-218">In the **Find what** box of the **Find in Extended Events** dialog box, enter the search text.</span></span> <span data-ttu-id="3cce1-219">您可以從下拉式清單中選取最後 20 個搜尋字串的其中之一。</span><span class="sxs-lookup"><span data-stu-id="3cce1-219">You can select one of your last 20 search strings from the drop-down list.</span></span>  
  
4.  <span data-ttu-id="3cce1-220">在 **[查詢]** 方塊中，選取要搜尋指定文字的位置。</span><span class="sxs-lookup"><span data-stu-id="3cce1-220">In the **Look in** box, select the location to search for the specified text.</span></span> <span data-ttu-id="3cce1-221">使用下列搜尋選項：</span><span class="sxs-lookup"><span data-stu-id="3cce1-221">Use the following options for searching:</span></span>  
  
    -   <span data-ttu-id="3cce1-222">資料表資料行：</span><span class="sxs-lookup"><span data-stu-id="3cce1-222">Table Columns.</span></span> <span data-ttu-id="3cce1-223">使用此選項可在追蹤視窗中搜尋所有可見資料行。</span><span class="sxs-lookup"><span data-stu-id="3cce1-223">Use this option to search all visible columns in the trace window.</span></span>  
  
    -   <span data-ttu-id="3cce1-224">詳細資料：</span><span class="sxs-lookup"><span data-stu-id="3cce1-224">Details.</span></span> <span data-ttu-id="3cce1-225">使用此選項，即可在開啟 [**在擴充事件中尋找**] 對話方塊之前選取的追蹤視窗中，搜尋所有資料行 (升級和未升級) 。</span><span class="sxs-lookup"><span data-stu-id="3cce1-225">Use this option to search all columns (promoted and non-promoted) in the trace window that were selected before opening the **Find in Extended Events** dialog box.</span></span>  
  
    -   <span data-ttu-id="3cce1-226">*Event_column_name*。</span><span class="sxs-lookup"><span data-stu-id="3cce1-226">*Event_column_name*.</span></span> <span data-ttu-id="3cce1-227">使用此選項可在下拉式清單的特定事件資料行中進行搜尋。</span><span class="sxs-lookup"><span data-stu-id="3cce1-227">Use this option to search in a specific event column from the drop-down list.</span></span>  
  
5.  <span data-ttu-id="3cce1-228">使用下列選項，指定定義搜尋的方式：</span><span class="sxs-lookup"><span data-stu-id="3cce1-228">Use the following options to specify how you want to define the search:</span></span>  
  
    -   <span data-ttu-id="3cce1-229">大小寫須相符：</span><span class="sxs-lookup"><span data-stu-id="3cce1-229">Match case.</span></span> <span data-ttu-id="3cce1-230">使用此選項可顯示與 [尋找目標] 方塊中輸入文字的內容和大小寫都相符的搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="3cce1-230">Use this option to display the search results for the text you entered in the Find what box that are matched both by content and by case.</span></span>  
  
    -   <span data-ttu-id="3cce1-231">全字拼寫須相符：</span><span class="sxs-lookup"><span data-stu-id="3cce1-231">Match whole word.</span></span> <span data-ttu-id="3cce1-232">使用此選項即可僅顯示與輸入文字完全相符的搜尋結果。</span><span class="sxs-lookup"><span data-stu-id="3cce1-232">Use this option to display only the search results for the text you entered that match complete words.</span></span>  
  
    -   <span data-ttu-id="3cce1-233">向上搜尋：</span><span class="sxs-lookup"><span data-stu-id="3cce1-233">Search up.</span></span> <span data-ttu-id="3cce1-234">使用此選項可從游標位置開始搜尋至結果開頭。</span><span class="sxs-lookup"><span data-stu-id="3cce1-234">Use this option to search from your cursor location to the beginning of the results.</span></span>  
  
    -   <span data-ttu-id="3cce1-235">使用：</span><span class="sxs-lookup"><span data-stu-id="3cce1-235">Use.</span></span> <span data-ttu-id="3cce1-236">使用此選項可解譯 [尋找目標] 方塊中輸入的特殊字元和規則運算式。</span><span class="sxs-lookup"><span data-stu-id="3cce1-236">Use this option to interpret the special characters and the regular expressions you entered in the Find what box.</span></span> <span data-ttu-id="3cce1-237">特殊字元包含萬用字元 (\*) 和 (?)，用於表示一個或多個字元。</span><span class="sxs-lookup"><span data-stu-id="3cce1-237">Special characters include the wildcard characters (\*) and (?) to represent one or more characters.</span></span> <span data-ttu-id="3cce1-238">規則運算式是用於定義搜尋文字模式的特殊標記法。</span><span class="sxs-lookup"><span data-stu-id="3cce1-238">Regular expressions are special notations used to define patterns of search text.</span></span>  
  
    -   <span data-ttu-id="3cce1-239">按一下 **[找下一個]** 可搜尋在 **[尋找目標]** 方塊中輸入的下一個文字。</span><span class="sxs-lookup"><span data-stu-id="3cce1-239">Click **Find Next** to search for the next text that you entered in the **Find what** box.</span></span>  
  
### <a name="bookmarks"></a><span data-ttu-id="3cce1-240">書籤</span><span class="sxs-lookup"><span data-stu-id="3cce1-240">Bookmarks</span></span>  
 <span data-ttu-id="3cce1-241">若要更輕鬆地返回資料列，您可以將目標資料中的一個或多個資料列設定為書籤。</span><span class="sxs-lookup"><span data-stu-id="3cce1-241">To make it easier to return to a row, you can bookmark one or more row(s) in the target data.</span></span> <span data-ttu-id="3cce1-242">請以滑鼠右鍵按一下要變更書籤的資料列。</span><span class="sxs-lookup"><span data-stu-id="3cce1-242">Right click on a row to change the bookmark.</span></span> <span data-ttu-id="3cce1-243">然後，使用 **[擴充事件]** 工具列上的 [上一個] 和 [下一個] 按鈕來導覽至設為書籤的資料列。</span><span class="sxs-lookup"><span data-stu-id="3cce1-243">Use the previous and next buttons on the **Extended Events** toolbar to navigate to bookmarked rows.</span></span>  
  
### <a name="change-display-settings"></a><span data-ttu-id="3cce1-244">變更顯示設定</span><span class="sxs-lookup"><span data-stu-id="3cce1-244">Change Display Settings</span></span>  
 <span data-ttu-id="3cce1-245">您可以儲存資料行資訊 (資料行順序、合併資料行和資料行寬度)，並將追蹤結果的資訊篩選到「擴充事件」顯示設定檔案 (.viewsetting 檔案)。</span><span class="sxs-lookup"><span data-stu-id="3cce1-245">You can save column information (column order, merge column, and column width) and filter information of a trace result into an Extended Events display setting file (.viewsetting file).</span></span> <span data-ttu-id="3cce1-246">在儲存檔案後，您可以將它套用到追蹤結果以變更檢視。</span><span class="sxs-lookup"><span data-stu-id="3cce1-246">After saving the file, you can apply it to your trace results to change the view.</span></span>  
  
 <span data-ttu-id="3cce1-247">若要變更顯示設定：</span><span class="sxs-lookup"><span data-stu-id="3cce1-247">To change the display settings:</span></span>  
  
1.  <span data-ttu-id="3cce1-248">開啟 .XEL 檔案以檢視追蹤結果</span><span class="sxs-lookup"><span data-stu-id="3cce1-248">Open a .XEL file to view the trace results.</span></span> <span data-ttu-id="3cce1-249">(您也可以用滑鼠右鍵按一下工作階段名稱，然後選取 **[監看即時資料]**)。</span><span class="sxs-lookup"><span data-stu-id="3cce1-249">(You can also right click the session name, select **Watch Live Data**.</span></span>  
  
2.  <span data-ttu-id="3cce1-250">在 **[擴充事件]** 工具列上，選取 **[顯示設定]**。</span><span class="sxs-lookup"><span data-stu-id="3cce1-250">On the **Extended Events** toolbar, select **Display Settings**.</span></span> <span data-ttu-id="3cce1-251">從下拉式清單中，選取下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="3cce1-251">From the drop-down list, select one of the following options:</span></span>  
  
    -   <span data-ttu-id="3cce1-252">另存新檔：</span><span class="sxs-lookup"><span data-stu-id="3cce1-252">Save as.</span></span> <span data-ttu-id="3cce1-253">將追蹤結果的資料行和篩選資訊儲存為 .viewsetting 檔案。</span><span class="sxs-lookup"><span data-stu-id="3cce1-253">Save the columns and filter information of a trace result to a .viewsetting file.</span></span>  
  
    -   <span data-ttu-id="3cce1-254">開啟。</span><span class="sxs-lookup"><span data-stu-id="3cce1-254">Open.</span></span> <span data-ttu-id="3cce1-255">開啟現有的 .viewsetting 檔案。</span><span class="sxs-lookup"><span data-stu-id="3cce1-255">Open an existing .viewsetting file.</span></span>  
  
    -   <span data-ttu-id="3cce1-256">開啟最近使用的項目：</span><span class="sxs-lookup"><span data-stu-id="3cce1-256">Open recent.</span></span> <span data-ttu-id="3cce1-257">開啟最近儲存的 .viewsetting 檔案。</span><span class="sxs-lookup"><span data-stu-id="3cce1-257">Open a recently saved .viewsetting file.</span></span>  
  
### <a name="copy-or-export-trace-results"></a><span data-ttu-id="3cce1-258">複製或匯出追蹤結果</span><span class="sxs-lookup"><span data-stu-id="3cce1-258">Copy or Export Trace Results</span></span>  
 <span data-ttu-id="3cce1-259">您可以將追蹤結果中的資料格、資料列和詳細資料複製到選取的資料列。</span><span class="sxs-lookup"><span data-stu-id="3cce1-259">You can copy cells, rows, and details to selected rows from your trace results.</span></span> <span data-ttu-id="3cce1-260">您也可以將追蹤結果匯出到以下項目：</span><span class="sxs-lookup"><span data-stu-id="3cce1-260">You can also export your trace results to the following:</span></span>  
  
-   <span data-ttu-id="3cce1-261">.XEL 檔</span><span class="sxs-lookup"><span data-stu-id="3cce1-261">.XEL file</span></span>  
  
-   <span data-ttu-id="3cce1-262">資料表</span><span class="sxs-lookup"><span data-stu-id="3cce1-262">table</span></span>  
  
-   <span data-ttu-id="3cce1-263">.CSV 檔</span><span class="sxs-lookup"><span data-stu-id="3cce1-263">.CSV file</span></span>  
  
 <span data-ttu-id="3cce1-264">若要複製追蹤結果，請選取資料格或資料列、按一下滑鼠右鍵、選取 **[複製]** ，然後選取 **[資料格]**、 **[資料列]** 或 **[詳細資料]**。</span><span class="sxs-lookup"><span data-stu-id="3cce1-264">To copy trace results, select a cell, row, or rows, right click, select **Copy** and then **Cell**, **Row**, or **Details**.</span></span> <span data-ttu-id="3cce1-265">擴充事件最多支援複製 1000 個資料列。</span><span class="sxs-lookup"><span data-stu-id="3cce1-265">Extended Events supports copying up to a maximum of 1000 rows.</span></span>  
  
 <span data-ttu-id="3cce1-266">您可以在 **的** [擴充事件] **功能表選項中選取** [匯出至] [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]，藉以將追蹤結果匯出至 .XEL 檔案、資料表或 .CSV 檔案。</span><span class="sxs-lookup"><span data-stu-id="3cce1-266">You can export trace results to a .XEL file, table, or .CSV file by selecting **Export to** from the **Extended Events** menu option in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="view-a-deadlock-graph-and-query-plans"></a><span data-ttu-id="3cce1-267">檢視死結圖形和查詢計畫</span><span class="sxs-lookup"><span data-stu-id="3cce1-267">View a Deadlock Graph and Query Plans</span></span>  
 <span data-ttu-id="3cce1-268">您可以在 [詳細資料] 窗格中檢視 **xml_deadlock_report** 的死結圖形，幫助您針對死結進行疑難排解。</span><span class="sxs-lookup"><span data-stu-id="3cce1-268">You can view the deadlock graph for **xml_deadlock_report** in the Details pane to help you troubleshoot deadlocks.</span></span> <span data-ttu-id="3cce1-269">您也可以檢視下列事件的查詢計畫圖形：</span><span class="sxs-lookup"><span data-stu-id="3cce1-269">You can also view query plan graphs for the following events:</span></span>  
  
-   <span data-ttu-id="3cce1-270">query_post_compilation_showplan</span><span class="sxs-lookup"><span data-stu-id="3cce1-270">query_post_compilation_showplan</span></span>  
  
-   <span data-ttu-id="3cce1-271">query_pre_execution_showplan</span><span class="sxs-lookup"><span data-stu-id="3cce1-271">query_pre_execution_showplan</span></span>  
  
-   <span data-ttu-id="3cce1-272">query_post_execution_showplan</span><span class="sxs-lookup"><span data-stu-id="3cce1-272">query_post_execution_showplan</span></span>  
  
 <span data-ttu-id="3cce1-273">若要檢視死結圖形：</span><span class="sxs-lookup"><span data-stu-id="3cce1-273">To view the deadlock graph:</span></span>  
  
-   <span data-ttu-id="3cce1-274">在物件總管中，依序展開 [**管理**]、[**擴充事件**] 和 [**會話**] 節點。</span><span class="sxs-lookup"><span data-stu-id="3cce1-274">In Object Explorer, expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  
  
-   <span data-ttu-id="3cce1-275">以滑鼠右鍵按一下包含您想要檢視之已設定死結事件的工作階段，然後選取 **[監看即時資料]**。</span><span class="sxs-lookup"><span data-stu-id="3cce1-275">Right-click the session that contains the configured deadlock event that you want to view, and select **Watch Live Data**.</span></span>  
  
-   <span data-ttu-id="3cce1-276">選取死結事件，並在 [詳細資料] 窗格的 **[死結]** 索引標籤上檢視圖形。</span><span class="sxs-lookup"><span data-stu-id="3cce1-276">Select the deadlock event and view the graph on the **Deadlock** tab in the Details pane.</span></span>  
  
 <span data-ttu-id="3cce1-277">若要檢視查詢計畫圖形：</span><span class="sxs-lookup"><span data-stu-id="3cce1-277">To view query plan graphs:</span></span>  
  
1.  <span data-ttu-id="3cce1-278">在物件總管中，依序展開 [**管理**]、[**擴充事件**] 和 [**會話**] 節點。</span><span class="sxs-lookup"><span data-stu-id="3cce1-278">In Object Explorer, expand the **Management**, **Extended Events**, and then **Sessions** nodes.</span></span>  
  
2.  <span data-ttu-id="3cce1-279">以滑鼠右鍵按一下包含您想要檢視之查詢計畫圖形的工作階段 (例如 query_post_compilation_showplan)，然後選取 **[監看即時資料]**。</span><span class="sxs-lookup"><span data-stu-id="3cce1-279">Right-click the session that contains the query plan graph that you want to view (for example, query_post_compilation_showplan), and then select **Watch Live Data**.</span></span>  
  
3.  <span data-ttu-id="3cce1-280">選取查詢計畫圖形事件 (例如 query_post_compilation_showplan)，並在 [詳細資料] 窗格的 **[查詢計畫]** 索引標籤上檢視圖形。</span><span class="sxs-lookup"><span data-stu-id="3cce1-280">Select the query plan graph event (for example, query_post_compilation_showplan) and view the graph on the **Query plan** tab in the Details pane.</span></span>  
  
  
