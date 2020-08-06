---
title: 檢視及閱讀容錯移轉叢集執行個體診斷記錄檔 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: high-availability
ms.topic: conceptual
ms.assetid: 68074bd5-be9d-4487-a320-5b51ef8e2b2d
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 774dc4ec4a02c72420d004909cb7e6ee1b31f3a7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595559"
---
# <a name="view-and-read-failover-cluster-instance-diagnostics-log"></a><span data-ttu-id="db01c-102">檢視及閱讀容錯移轉叢集執行個體診斷記錄檔</span><span class="sxs-lookup"><span data-stu-id="db01c-102">View and Read Failover Cluster Instance Diagnostics Log</span></span>
  <span data-ttu-id="db01c-103">SQL Server 資源 DLL 的所有重大錯誤和警告事件都會寫入 Windows 事件記錄檔。</span><span class="sxs-lookup"><span data-stu-id="db01c-103">All critical errors and warning events for the SQL Server Resource DLL are written to the Windows event log.</span></span> <span data-ttu-id="db01c-104">SQL Server 的特定診斷資訊執行記錄檔是由 [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) 系統預存程序所擷取，並且會寫入 SQL Server 容錯移轉叢集診斷 (也稱為 *SQLDIAG* 記錄) 記錄檔。</span><span class="sxs-lookup"><span data-stu-id="db01c-104">A running log of the diagnostic information specific to SQL Server is captured by the [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) system stored procedure and is written to the SQL Server failover cluster diagnostics (also known as the *SQLDIAG* logs) log files.</span></span>  
  
-   <span data-ttu-id="db01c-105">**開始之前**  [建議](#Recommendations)、 [安全性](#Security)</span><span class="sxs-lookup"><span data-stu-id="db01c-105">**Before you begin:**  [Recommendations](#Recommendations), [Security](#Security)</span></span>  
  
-   <span data-ttu-id="db01c-106">**使用下列項目，檢視診斷記錄：**  [SQL Server Management Studio](#SSMSProcedure)、[Transact-SQL](#TsqlProcedure)</span><span class="sxs-lookup"><span data-stu-id="db01c-106">**To View the Diagnostic Log, using:**  [SQL Server Management Studio](#SSMSProcedure), [Transact-SQL](#TsqlProcedure)</span></span>  
  
-   <span data-ttu-id="db01c-107">**使用下列項目，設定診斷記錄設定：** [Transact-SQL](#TsqlConfigure)</span><span class="sxs-lookup"><span data-stu-id="db01c-107">**To Configure Diagnostic Log settings, using:** [Transact-SQL](#TsqlConfigure)</span></span>  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> <span data-ttu-id="db01c-108">開始之前</span><span class="sxs-lookup"><span data-stu-id="db01c-108">Before You Begin</span></span>  
  
###  <a name="recommendations"></a><a name="Recommendations"></a> <span data-ttu-id="db01c-109">建議</span><span class="sxs-lookup"><span data-stu-id="db01c-109">Recommendations</span></span>  
 <span data-ttu-id="db01c-110">根據預設，SQLDIAG 會儲存在 SQL Server 實例目錄的本機 LOG 資料夾底下，例如 ' C\Program Files\Microsoft SQL Server\MSSQL12. \<InstanceName>AlwaysOn 容錯移轉叢集實例之擁有節點的 \MSSQL\LOG ' (FCI) 。</span><span class="sxs-lookup"><span data-stu-id="db01c-110">By default, the SQLDIAG are stored under a local LOG folder of the SQL Server instance directory, for example, 'C\Program Files\Microsoft SQL Server\MSSQL12.\<InstanceName>\MSSQL\LOG' of the owning node of the AlwaysOn Failover Cluster Instance (FCI).</span></span> <span data-ttu-id="db01c-111">每個 SQLDIAG 記錄檔的大小會固定為 100 MB。</span><span class="sxs-lookup"><span data-stu-id="db01c-111">The size of each SQLDIAG log file is fixed at 100 MB.</span></span> <span data-ttu-id="db01c-112">電腦上會儲存十個此類型的記錄檔，再將它們回收以用於新的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="db01c-112">Ten such log files are stored on the computer before they are recycled for new logs.</span></span>  
  
 <span data-ttu-id="db01c-113">記錄檔會使用擴充的事件檔案格式。</span><span class="sxs-lookup"><span data-stu-id="db01c-113">The logs use the extended events file format.</span></span> <span data-ttu-id="db01c-114">**sys.fn_xe_file_target_read_file** 系統函數可用來讀取擴充事件所建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="db01c-114">The **sys.fn_xe_file_target_read_file** system function can be used to read the files that are created by Extended Events.</span></span> <span data-ttu-id="db01c-115">系統會以 XML 格式針對每個資料列傳回一個事件。</span><span class="sxs-lookup"><span data-stu-id="db01c-115">One event, in XML format, is returned per row.</span></span> <span data-ttu-id="db01c-116">查詢系統檢視，即可將 XML 資料剖析為結果集。</span><span class="sxs-lookup"><span data-stu-id="db01c-116">Query the system view to parse the XML data as a result-set.</span></span> <span data-ttu-id="db01c-117">如需詳細資訊，請參閱 [sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="db01c-117">For more information, see [sys.fn_xe_file_target_read_file &#40;Transact-SQL&#41;](/sql/relational-databases/system-functions/sys-fn-xe-file-target-read-file-transact-sql).</span></span>  
  
###  <a name="security"></a><a name="Security"></a> <span data-ttu-id="db01c-118">Security</span><span class="sxs-lookup"><span data-stu-id="db01c-118">Security</span></span>  
  
####  <a name="permissions"></a><a name="Permissions"></a> <span data-ttu-id="db01c-119">權限</span><span class="sxs-lookup"><span data-stu-id="db01c-119">Permissions</span></span>  
 <span data-ttu-id="db01c-120">需要有 VIEW SERVER STATE 權限才能執行 **fn_xe_file_target_read_file**。</span><span class="sxs-lookup"><span data-stu-id="db01c-120">VIEW SERVER STATE permission is needed to run **fn_xe_file_target_read_file**.</span></span>  
  
 <span data-ttu-id="db01c-121">以管理員的身分開啟 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="db01c-121">Open SQL Server Management Studio as Administrator</span></span>  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> <span data-ttu-id="db01c-122">使用 SQL Server Management Studio</span><span class="sxs-lookup"><span data-stu-id="db01c-122">Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="db01c-123">**若要檢視診斷記錄檔：**</span><span class="sxs-lookup"><span data-stu-id="db01c-123">**To view the Diagnostic log files:**</span></span>  
  
1.  <span data-ttu-id="db01c-124">從 **[檔案]** 功能表中，依序選取 **[開啟]** 和 **[檔案]**，然後選擇想要檢視的診斷記錄檔。</span><span class="sxs-lookup"><span data-stu-id="db01c-124">From the **File** menu, select **Open**, **File**, and choose the diagnostic log file you want to view.</span></span>  
  
2.  <span data-ttu-id="db01c-125">事件在右窗格中會顯示為資料列，而且依預設只會顯示 **[name]** 和 **[timestamp]** 這兩個資料行。</span><span class="sxs-lookup"><span data-stu-id="db01c-125">The events are displayed as rows in the right pane, and by default **name**, and **timestamp** are the only two columns displayed.</span></span>  
  
     <span data-ttu-id="db01c-126">這也會啟動 **[ExtendedEvents]** 功能表。</span><span class="sxs-lookup"><span data-stu-id="db01c-126">This also activates the **ExtendedEvents** menu.</span></span>  
  
3.  <span data-ttu-id="db01c-127">若要查看其他資料行，請前往 **[ExtendedEvents]** 功能表，並選取 **[選擇資料行]**。</span><span class="sxs-lookup"><span data-stu-id="db01c-127">To see more columns, go the **ExtendedEvents** menu, and select **Choose Columns**.</span></span>  
  
     <span data-ttu-id="db01c-128">隨即開啟對話方塊，內含可讓您選取資料行進行顯示的可用資料行。</span><span class="sxs-lookup"><span data-stu-id="db01c-128">A dialog box opens with the available columns allowing you to select the columns for display.</span></span>  
  
4.  <span data-ttu-id="db01c-129">您可以使用 **[ExtendedEvents]** 功能表並選取 **[篩選]** 選項，來篩選和排序事件資料。</span><span class="sxs-lookup"><span data-stu-id="db01c-129">You can filter, and sort the event data using the **ExtendedEvents** menu and selecting the **Filter** option.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> <span data-ttu-id="db01c-130">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="db01c-130">Using Transact-SQL</span></span>  
 <span data-ttu-id="db01c-131">**若要檢視診斷記錄檔：**</span><span class="sxs-lookup"><span data-stu-id="db01c-131">**To view the Diagnostic log files:**</span></span>  
  
 <span data-ttu-id="db01c-132">若要檢視 SQLDIAG 記錄檔中的所有記錄項目，請使用下列查詢：</span><span class="sxs-lookup"><span data-stu-id="db01c-132">To view all the log items in the SQLDIAG log file, use the following query:</span></span>  
  
```  
SELECT  
xml_data.value('(event/@name)[1]','varchar(max)') AS 'Name'  
,xml_data.value('(event/@package)[1]','varchar(max)') AS 'Package'  
,xml_data.value('(event/@timestamp)[1]','datetime') AS 'Time'  
,xml_data.value('(event/data[@name=''state'']/value)[1]','int') AS 'State'  
,xml_data.value('(event/data[@name=''state_desc'']/text)[1]','varchar(max)') AS 'State Description'  
,xml_data.value('(event/data[@name=''failure_condition_level'']/value)[1]','int') AS 'Failure Conditions'  
,xml_data.value('(event/data[@name=''node_name'']/value)[1]','varchar(max)') AS 'Node_Name'  
,xml_data.value('(event/data[@name=''instancename'']/value)[1]','varchar(max)') AS 'Instance Name'  
,xml_data.value('(event/data[@name=''creation time'']/value)[1]','datetime') AS 'Creation Time'  
,xml_data.value('(event/data[@name=''component'']/value)[1]','varchar(max)') AS 'Component'  
,xml_data.value('(event/data[@name=''data'']/value)[1]','varchar(max)') AS 'Data'  
,xml_data.value('(event/data[@name=''info'']/value)[1]','varchar(max)') AS 'Info'  
FROM  
 ( SELECT object_name AS 'event'  
  ,CONVERT(xml,event_data) AS 'xml_data'  
  FROM sys.fn_xe_file_target_read_file('C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\Log\SQLNODE1_MSSQLSERVER_SQLDIAG_0_129936003752530000.xel',NULL,NULL,NULL)   
)   
AS XEventData  
ORDER BY Time;  
  
```  
  
> [!NOTE]  
>  <span data-ttu-id="db01c-133">您可以篩選特定元件或使用 WHERE 子句之狀態的結果。</span><span class="sxs-lookup"><span data-stu-id="db01c-133">You can filter the results for specific components or state using the WHERE clause.</span></span>  
  
##  <a name="using-transact-sql"></a><a name="TsqlConfigure"></a> <span data-ttu-id="db01c-134">使用 Transact-SQL</span><span class="sxs-lookup"><span data-stu-id="db01c-134">Using Transact-SQL</span></span>  
 <span data-ttu-id="db01c-135">**設定診斷記錄屬性**</span><span class="sxs-lookup"><span data-stu-id="db01c-135">**To configure the Diagnostic Log Properties**</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db01c-136">如需這個程序的範例，請參閱本節稍後的 [範例 &#40;Transact-SQL&#41;](#TsqlExample)。</span><span class="sxs-lookup"><span data-stu-id="db01c-136">For an example of this procedure, see [Example (Transact-SQL)](#TsqlExample), later in this section.</span></span>  
  
 <span data-ttu-id="db01c-137">使用資料定義語言 (DDL) 語句， `ALTER SERVER CONFIGURATION` 您可以啟動或停止[Sp_server_diagnostics &#40;transact-sql&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql)程式所捕捉的記錄診斷資料，並設定 SQLDIAG 記錄檔設定參數，例如記錄檔換用計數、記錄檔大小和檔案位置。</span><span class="sxs-lookup"><span data-stu-id="db01c-137">Using the Data Definition Language (DDL) statement, `ALTER SERVER CONFIGURATION`, you can start or stop logging diagnostic data captured by the [sp_server_diagnostics &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-server-diagnostics-transact-sql) procedure, and set SQLDIAG log configuration parameters such as the log file rollover count, log file size, and file location.</span></span> <span data-ttu-id="db01c-138">如需語法的詳細資料，請參閱 [Setting diagnostic log options](/sql/t-sql/statements/alter-server-configuration-transact-sql#Diagnostic)。</span><span class="sxs-lookup"><span data-stu-id="db01c-138">For syntax details, see [Setting diagnostic log options](/sql/t-sql/statements/alter-server-configuration-transact-sql#Diagnostic).</span></span>  
  
###  <a name="examples-transact-sql"></a><a name="ConfigTsqlExample"></a> <span data-ttu-id="db01c-139">範例 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="db01c-139">Examples (Transact-SQL)</span></span>  
  
####  <a name="setting-diagnostic-log-options"></a><a name="TsqlExample"></a> <span data-ttu-id="db01c-140">Setting diagnostic log options</span><span class="sxs-lookup"><span data-stu-id="db01c-140">Setting diagnostic log options</span></span>  
 <span data-ttu-id="db01c-141">本節的範例示範如何設定診斷記錄檔選項的值。</span><span class="sxs-lookup"><span data-stu-id="db01c-141">The examples in this section show how to set the values for the diagnostic log option.</span></span>  
  
##### <a name="a-starting-diagnostic-logging"></a><span data-ttu-id="db01c-142">A.</span><span class="sxs-lookup"><span data-stu-id="db01c-142">A.</span></span> <span data-ttu-id="db01c-143">啟動診斷記錄</span><span class="sxs-lookup"><span data-stu-id="db01c-143">Starting diagnostic logging</span></span>  
 <span data-ttu-id="db01c-144">下列範例會啟動診斷資料記錄。</span><span class="sxs-lookup"><span data-stu-id="db01c-144">The following example starts the logging of diagnostic data.</span></span>  
  
```  
ALTER SERVER CONFIGURATION SET DIAGNOSTICS LOG ON;  
```  
  
##### <a name="b-stopping-diagnostic-logging"></a><span data-ttu-id="db01c-145">B.</span><span class="sxs-lookup"><span data-stu-id="db01c-145">B.</span></span> <span data-ttu-id="db01c-146">停止診斷記錄</span><span class="sxs-lookup"><span data-stu-id="db01c-146">Stopping diagnostic logging</span></span>  
 <span data-ttu-id="db01c-147">下列範例會停止診斷資料記錄。</span><span class="sxs-lookup"><span data-stu-id="db01c-147">The following example stops the logging of diagnostic data.</span></span>  
  
```  
ALTER SERVER CONFIGURATION SET DIAGNOSTICS LOG OFF;  
```  
  
##### <a name="c-specifying-the-location-of-the-diagnostic-logs"></a><span data-ttu-id="db01c-148">C.</span><span class="sxs-lookup"><span data-stu-id="db01c-148">C.</span></span> <span data-ttu-id="db01c-149">指定診斷記錄的位置</span><span class="sxs-lookup"><span data-stu-id="db01c-149">Specifying the location of the diagnostic logs</span></span>  
 <span data-ttu-id="db01c-150">下列範例會將診斷記錄檔的位置設定為指定的檔案路徑。</span><span class="sxs-lookup"><span data-stu-id="db01c-150">The following example sets the location of the diagnostic logs to the specified file path.</span></span>  
  
```  
ALTER SERVER CONFIGURATION  
SET DIAGNOSTICS LOG PATH = 'C:\logs';  
```  
  
##### <a name="d-specifying-the-maximum-size-of-each-diagnostic-log"></a><span data-ttu-id="db01c-151">D.</span><span class="sxs-lookup"><span data-stu-id="db01c-151">D.</span></span> <span data-ttu-id="db01c-152">指定每個診斷記錄的大小上限</span><span class="sxs-lookup"><span data-stu-id="db01c-152">Specifying the maximum size of each diagnostic log</span></span>  
 <span data-ttu-id="db01c-153">下列範例會將每個診斷記錄檔的大小上限設為 10 MB。</span><span class="sxs-lookup"><span data-stu-id="db01c-153">The following example set the maximum size of each diagnostic log to 10 megabytes.</span></span>  
  
```  
ALTER SERVER CONFIGURATION   
SET DIAGNOSTICS LOG MAX_SIZE = 10 MB;  
```  
  
## <a name="see-also"></a><span data-ttu-id="db01c-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db01c-154">See Also</span></span>  
 [<span data-ttu-id="db01c-155">Failover Policy for Failover Cluster Instances</span><span class="sxs-lookup"><span data-stu-id="db01c-155">Failover Policy for Failover Cluster Instances</span></span>](failover-policy-for-failover-cluster-instances.md)  
  
  
