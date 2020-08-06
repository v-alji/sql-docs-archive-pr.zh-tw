---
title: 使用 SQL Server Profiler (SQL Server Management Studio) 來建立 SQL 追蹤收集組 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- SQL Trace collector set
ms.assetid: b6941dc0-50f5-475d-82eb-ce7c68117489
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: e9c9514fef8069cef615d1480aad1e0acd1582cd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599014"
---
# <a name="use-sql-server-profiler-to-create-a-sql-trace-collection-set-sql-server-management-studio"></a><span data-ttu-id="db299-102">使用 SQL Server Profiler 來建立 SQL 追蹤收集組 (SQL Server Management Studio)</span><span class="sxs-lookup"><span data-stu-id="db299-102">Use SQL Server Profiler to Create a SQL Trace Collection Set (SQL Server Management Studio)</span></span>
  <span data-ttu-id="db299-103">在 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] 中，您可以利用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 的伺服器端追蹤功能來匯出追蹤定義，以便用來建立使用一般 SQL 追蹤收集器類型的收集組。</span><span class="sxs-lookup"><span data-stu-id="db299-103">In [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] you can exploit the server-side trace capabilities of [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to export a trace definition that you can use to create a collection set that uses the Generic SQL Trace collector type.</span></span> <span data-ttu-id="db299-104">這個程序可以分成兩個部分：</span><span class="sxs-lookup"><span data-stu-id="db299-104">There are two parts to this process:</span></span>  
  
1.  <span data-ttu-id="db299-105">建立和匯出 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 追蹤。</span><span class="sxs-lookup"><span data-stu-id="db299-105">Create and export a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace.</span></span>  
  
2.  <span data-ttu-id="db299-106">根據匯出的追蹤，編寫新收集組的指令碼。</span><span class="sxs-lookup"><span data-stu-id="db299-106">Script a new collection set based on an exported trace.</span></span>  
  
 <span data-ttu-id="db299-107">下列程序的狀況包含收集需要 80 毫秒或更長時間才能完成之任何預存程序的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="db299-107">The scenario for the following procedures involves collecting data about any stored procedure that requires 80 milliseconds or longer to complete.</span></span> <span data-ttu-id="db299-108">若要完成這些程序，您應該要能夠：</span><span class="sxs-lookup"><span data-stu-id="db299-108">In order to complete these procedures you should be able to:</span></span>  
  
-   <span data-ttu-id="db299-109">使用 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 來建立和設定追蹤。</span><span class="sxs-lookup"><span data-stu-id="db299-109">Use [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] to create and configure a trace.</span></span>  
  
-   <span data-ttu-id="db299-110">使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來開啟、編輯和執行查詢。</span><span class="sxs-lookup"><span data-stu-id="db299-110">Use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to open, edit, and execute a query.</span></span>  
  
### <a name="create-and-export-a-sql-server-profiler-trace"></a><span data-ttu-id="db299-111">建立和匯出 SQL Server Profiler 追蹤</span><span class="sxs-lookup"><span data-stu-id="db299-111">Create and export a SQL Server Profiler trace</span></span>  
  
1.  <span data-ttu-id="db299-112">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，開啟 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db299-112">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], open [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span> <span data-ttu-id="db299-113">(在 [工具]  功能表上，按一下 [SQL Server Profiler]  )。</span><span class="sxs-lookup"><span data-stu-id="db299-113">(On the **Tools** menu, click **SQL Server Profiler**.)</span></span>  
  
2.  <span data-ttu-id="db299-114">在 [連接到伺服器]  對話方塊中，按一下 [取消]  。</span><span class="sxs-lookup"><span data-stu-id="db299-114">In the **Connect to Server** dialog box, click **Cancel**.</span></span>  
  
3.  <span data-ttu-id="db299-115">在這個狀況中，請確定持續時間值設定為以毫秒顯示 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="db299-115">For this scenario, ensure that duration values are configured to display in milliseconds (the default).</span></span> <span data-ttu-id="db299-116">若要這樣做，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="db299-116">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="db299-117">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="db299-117">On the **Tools** menu, click **Options**.</span></span>  
  
    2.  <span data-ttu-id="db299-118">在 [顯示選項]  區域中，請確定已清除 [顯示 [持續時間] 資料行中的值 (以百萬分之一秒為單位)] 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="db299-118">In the **Display Options** area, ensure that the Show values in Duration column in microseconds check box is cleared.</span></span>  
  
    3.  <span data-ttu-id="db299-119">按一下 [確定]  關閉 [一般選項]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="db299-119">Click **OK** to close the **General Options** dialog box.</span></span>  
  
4.  <span data-ttu-id="db299-120">在 [檔案]  功能表上，按一下 [新增追蹤]  。</span><span class="sxs-lookup"><span data-stu-id="db299-120">On the **File** menu, click **New Trace**.</span></span>  
  
5.  <span data-ttu-id="db299-121">在 [連接到伺服器]  對話方塊中，選取您想要連接的伺服器，然後按一下 [連接]  。</span><span class="sxs-lookup"><span data-stu-id="db299-121">In the **Connect to Server** dialog box, select the server that you want to connect to, and then click **Connect**.</span></span>  
  
     <span data-ttu-id="db299-122">會出現 [追蹤屬性]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="db299-122">The **Trace Properties** dialog box appears.</span></span>  
  
6.  <span data-ttu-id="db299-123">在 [一般]  索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="db299-123">On the **General** tab, do the following:</span></span>  
  
    1.  <span data-ttu-id="db299-124">在 [追蹤名稱]  方塊中，輸入您想要用於追蹤的名稱。</span><span class="sxs-lookup"><span data-stu-id="db299-124">In the **Trace name** box, type the name that you want to use for the trace.</span></span> <span data-ttu-id="db299-125">在這則範例中，追蹤名稱為 `SPgt80`。</span><span class="sxs-lookup"><span data-stu-id="db299-125">For this example, the trace name is `SPgt80`.</span></span>  
  
    2.  <span data-ttu-id="db299-126">在 [使用範本]  清單中，選取要用於追蹤的範本。</span><span class="sxs-lookup"><span data-stu-id="db299-126">In the **Use the template list**, select the template to use for the trace.</span></span> <span data-ttu-id="db299-127">在這則範例中，請按一下 [TSQL_SPs]  。</span><span class="sxs-lookup"><span data-stu-id="db299-127">For this example, click **TSQL_SPs**.</span></span>  
  
7.  <span data-ttu-id="db299-128">在 [事件選取範圍]  索引標籤上，執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="db299-128">On the **Events Selection** tab, do the following:</span></span>  
  
    1.  <span data-ttu-id="db299-129">識別要用於追蹤的事件。</span><span class="sxs-lookup"><span data-stu-id="db299-129">Identify the events to use for the trace.</span></span> <span data-ttu-id="db299-130">在這則範例中，請清除 [事件]  資料行中的所有核取方塊，但 [ExistingConnection]  和 [SP:Completed]  除外。</span><span class="sxs-lookup"><span data-stu-id="db299-130">For this example, clear all check boxes in the **Events** column, except for **ExistingConnection** and **SP:Completed**.</span></span>  
  
    2.  <span data-ttu-id="db299-131">在右下角中，選取 [顯示所有資料行]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="db299-131">In the lower-right corner, select the **Show all columns** check box.</span></span>  
  
    3.  <span data-ttu-id="db299-132">按一下 [SP:Completed]  資料列。</span><span class="sxs-lookup"><span data-stu-id="db299-132">Click the **SP:Completed** row.</span></span>  
  
    4.  <span data-ttu-id="db299-133">在資料列中捲動至 [持續時間]  資料行，然後選取 [持續時間]  核取方塊。</span><span class="sxs-lookup"><span data-stu-id="db299-133">Scroll across the row to the **Duration** column, and then select the **Duration** check box.</span></span>  
  
8.  <span data-ttu-id="db299-134">在右下角中，按一下 [資料行篩選]  開啟 [編輯篩選]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="db299-134">In the lower-right corner, click **Column Filters** to open the **Edit Filter** dialog box.</span></span> <span data-ttu-id="db299-135">在 [編輯篩選]  對話方塊中，執行下列步驟：</span><span class="sxs-lookup"><span data-stu-id="db299-135">In the **Edit Filter** dialog box, do the following:</span></span>  
  
    1.  <span data-ttu-id="db299-136">在篩選清單中，按一下 [持續時間]  。</span><span class="sxs-lookup"><span data-stu-id="db299-136">In the filter list, click **Duration**.</span></span>  
  
    2.  <span data-ttu-id="db299-137">在布林運算子視窗中，展開 [**大於或等於**] 節點，輸入 `80` 做為值，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="db299-137">In the Boolean operator window, expand the **Greater than or equal** node, type `80` as the value, and then click **OK**.</span></span>  
  
9. <span data-ttu-id="db299-138">按一下 **[執行]** 啟動追蹤。</span><span class="sxs-lookup"><span data-stu-id="db299-138">Click **Run** to start the trace.</span></span>  
  
10. <span data-ttu-id="db299-139">在工具列上，按一下 [停止選取的追蹤]  或 [暫停選取的追蹤]  。</span><span class="sxs-lookup"><span data-stu-id="db299-139">On the toolbar, click **Stop Selected Trace** or **Pause Selected Trace**.</span></span>  
  
11. <span data-ttu-id="db299-140">在 [檔案]  功能表上，依序指向 [匯出]  和 [指令碼追蹤定義]  ，然後按一下 [對於 SQL 追蹤收集組]  。</span><span class="sxs-lookup"><span data-stu-id="db299-140">On the **File** menu, point to **Export**, point to **Script Trace Definition**, and then click **For SQL Trace Collection Set**.</span></span>  
  
12. <span data-ttu-id="db299-141">在 [另存新檔]  對話方塊的 [檔案名稱]  方塊中，輸入您想要用於追蹤定義的名稱，然後將它儲存在所需的位置。</span><span class="sxs-lookup"><span data-stu-id="db299-141">In the **Save As** dialog box, type the name that you want to use for the trace definition in the **File name** box, and then save it in the location that you want.</span></span> <span data-ttu-id="db299-142">在這則範例中，檔案名稱與追蹤名稱 (SPgt80) 相同。</span><span class="sxs-lookup"><span data-stu-id="db299-142">For this example, the file name is the same as the trace name (SPgt80).</span></span>  
  
13. <span data-ttu-id="db299-143">當您收到檔案儲存成功的訊息時，請按一下 [確定]  ，然後關閉 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="db299-143">Click **OK** when you receive a message that the file was successfully saved, and then close [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)].</span></span>  
  
### <a name="script-a-new-collection-set-from-a-sql-server-profiler-trace"></a><span data-ttu-id="db299-144">根據 SQL Server Profiler 追蹤編寫新收集組的指令碼</span><span class="sxs-lookup"><span data-stu-id="db299-144">Script a new collection set from a SQL Server Profiler trace</span></span>  
  
1.  <span data-ttu-id="db299-145">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的 [檔案]  功能表上，指向 [開啟]  ，然後按一下 [檔案]  。</span><span class="sxs-lookup"><span data-stu-id="db299-145">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], on the **File** menu, point to **Open,** and then click **File**.</span></span>  
  
2.  <span data-ttu-id="db299-146">在 [開啟檔案]  對話方塊中，找出並開啟您在上一個程序中建立的檔案 (SPgt80)。</span><span class="sxs-lookup"><span data-stu-id="db299-146">In the **Open File** dialog box, locate and then open the file that you created in the previous procedure (SPgt80).</span></span>  
  
     <span data-ttu-id="db299-147">您所儲存的追蹤資訊會在 [查詢] 視窗中開啟，並且合併至您可以執行以建立新收集組的指令碼中。</span><span class="sxs-lookup"><span data-stu-id="db299-147">The trace information that you saved is opened in a Query window and merged into a script that you can run to create the new collection set.</span></span>  
  
3.  <span data-ttu-id="db299-148">捲動指令碼並進行下列取代 (這些取代會以指令碼註解文字顯示)：</span><span class="sxs-lookup"><span data-stu-id="db299-148">Scroll through the script and make the following replacements, which are noted in the script comment text:</span></span>  
  
    -   <span data-ttu-id="db299-149">將 **SQLTrace Collection Set Name Here** 取代成您想要針對收集組使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="db299-149">Replace **SQLTrace Collection Set Name Here** with the name that you want to use for the collection set.</span></span> <span data-ttu-id="db299-150">針對此範例，請將收集組命名為 `SPROC_CollectionSet`。</span><span class="sxs-lookup"><span data-stu-id="db299-150">For this example, name the collection set `SPROC_CollectionSet`.</span></span>  
  
    -   <span data-ttu-id="db299-151">將 **SQLTrace Collection Item Name Here** 取代成您想要針對收集項使用的名稱。</span><span class="sxs-lookup"><span data-stu-id="db299-151">Replace **SQLTrace Collection Item Name Here** with the name that you want to use for the collection item.</span></span> <span data-ttu-id="db299-152">針對此範例，請將收集項命名為 `SPROC_Collection_Item`。</span><span class="sxs-lookup"><span data-stu-id="db299-152">For this example, name the collection item `SPROC_Collection_Item`.</span></span>  
  
4.  <span data-ttu-id="db299-153">按一下 [執行]  執行查詢並建立收集組。</span><span class="sxs-lookup"><span data-stu-id="db299-153">Click **Execute** to run the query and to create the collection set.</span></span>  
  
5.  <span data-ttu-id="db299-154">在 [物件總管] 中，確認已建立收集組。</span><span class="sxs-lookup"><span data-stu-id="db299-154">In Object Explorer, verify that the collection set was created.</span></span> <span data-ttu-id="db299-155">若要這樣做，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="db299-155">To do this, follow these steps:</span></span>  
  
    1.  <span data-ttu-id="db299-156">以滑鼠右鍵按一下 [管理]  ，然後按一下 [重新整理]  。</span><span class="sxs-lookup"><span data-stu-id="db299-156">Right-click **Management**, and then click **Refresh**.</span></span>  
  
    2.  <span data-ttu-id="db299-157">展開 [管理]  ，然後展開 [資料收集]  。</span><span class="sxs-lookup"><span data-stu-id="db299-157">Expand **Management**, and then expand **Data Collection**.</span></span>  
  
     <span data-ttu-id="db299-158">`SPROC_CollectionSet`收集組會與 [**系統資料收集組**] 節點顯示在相同的層級。</span><span class="sxs-lookup"><span data-stu-id="db299-158">The `SPROC_CollectionSet` collection set appears at the same level as the **System Data Collection Sets** node.</span></span> <span data-ttu-id="db299-159">根據預設，此收集組是停用的。</span><span class="sxs-lookup"><span data-stu-id="db299-159">By default, the collection set is disabled.</span></span>  
  
6.  <span data-ttu-id="db299-160">您可以使用 [物件總管] 來編輯 SPROC_CollectionSet 的屬性，例如收集模式和上傳排程。</span><span class="sxs-lookup"><span data-stu-id="db299-160">Use Object Explorer to edit the properties of SPROC_CollectionSet, such as the collection mode and upload schedule.</span></span> <span data-ttu-id="db299-161">請遵循您用來處理資料收集器所提供之系統資料收集組的相同程序。</span><span class="sxs-lookup"><span data-stu-id="db299-161">Follow the same procedures that you would for the System Data collection sets that are provided with the data collector.</span></span>  
  
## <a name="example"></a><span data-ttu-id="db299-162">範例</span><span class="sxs-lookup"><span data-stu-id="db299-162">Example</span></span>  
 <span data-ttu-id="db299-163">下列程式碼範例是上述程序所列步驟所產生的最終指令碼。</span><span class="sxs-lookup"><span data-stu-id="db299-163">The following code sample is the final script resulting from the steps documented in the preceding procedures.</span></span>  
  
```  
/*************************************************************/  
-- SQL Trace collection set generated from SQL Server Profiler  
-- Date: 11/19/2007  12:55:31 AM  
/*************************************************************/  
  
USE msdb  
GO  
  
BEGIN TRANSACTION  
BEGIN TRY  
  
-- Define collection set  
-- ***  
-- *** Replace 'SqlTrace Collection Set Name Here' in the   
-- *** following script with the name you want  
-- *** to use for the collection set.  
-- ***  
DECLARE @collection_set_id int;  
EXEC [dbo].[sp_syscollector_create_collection_set]  
    @name = N'SPROC_CollectionSet',  
    @schedule_name = N'CollectorSchedule_Every_15min',  
    @collection_mode = 0, -- cached mode needed for Trace collections  
    @logging_level = 0, -- minimum logging  
    @days_until_expiration = 5,  
    @description = N'Collection set generated by SQL Server Profiler',  
    @collection_set_id = @collection_set_id output;  
SELECT @collection_set_id;  
  
-- Define input and output variables for the collection item.  
DECLARE @trace_definition xml;  
DECLARE @collection_item_id int;  
  
-- Define the trace parameters as an XML variable  
SELECT @trace_definition = convert(xml,   
N'<ns:SqlTraceCollector xmlns:ns"DataCollectorType" use_default="0">  
<Events>  
  <EventType name="Sessions">  
    <Event id="17" name="ExistingConnection" columnslist="1,2,14,26,3,35,12" />  
  </EventType>  
  <EventType name="Stored Procedures">  
    <Event id="43" name="SP:Completed" columnslist="1,2,26,34,3,35,12,13,14,22" />  
  </EventType>  
</Events>  
<Filters>  
  <Filter columnid="13" columnname="Duration" logical_operator="AND" comparison_operator="GE" value="80000L" />  
</Filters>  
</ns:SqlTraceCollector>  
');  
  
-- Retrieve the collector type GUID for the trace collector type.  
DECLARE @collector_type_GUID uniqueidentifier;  
SELECT @collector_type_GUID = collector_type_uid FROM [dbo].[syscollector_collector_types] WHERE name = N'Generic SQL Trace Collector Type';  
  
-- Create the trace collection item.  
-- ***  
-- *** Replace 'SqlTrace Collection Item Name Here' in   
-- *** the following script with the name you want to  
-- *** use for the collection item.  
-- ***  
EXEC [dbo].[sp_syscollector_create_collection_item]  
   @collection_set_id = @collection_set_id,  
   @collector_type_uid = @collector_type_GUID,  
   @name = N'SPROC_Collection_Item',  
   @frequency = 900, -- specified the frequency for checking to see if trace is still running  
   @parameters = @trace_definition,  
   @collection_item_id = @collection_item_id output;  
SELECT @collection_item_id;  
  
COMMIT TRANSACTION;  
END TRY  
  
BEGIN CATCH  
ROLLBACK TRANSACTION;  
DECLARE @ErrorMessage nvarchar(4000);  
DECLARE @ErrorSeverity int;  
DECLARE @ErrorState int;  
DECLARE @ErrorNumber int;  
DECLARE @ErrorLine int;  
DECLARE @ErrorProcedure nvarchar(200);  
SELECT @ErrorLine = ERROR_LINE(),  
       @ErrorSeverity = ERROR_SEVERITY(),  
       @ErrorState = ERROR_STATE(),  
       @ErrorNumber = ERROR_NUMBER(),  
       @ErrorMessage = ERROR_MESSAGE(),  
       @ErrorProcedure = ISNULL(ERROR_PROCEDURE(), '-');  
RAISERROR (14684, @ErrorSeverity, 1 , @ErrorNumber, @ErrorSeverity, @ErrorState, @ErrorProcedure, @ErrorLine, @ErrorMessage);  
END CATCH;  
GO  
```  
  
  
