---
title: Analysis Services 中的記錄作業 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: aa1db060-95dc-4198-8aeb-cffdda44b140
author: minewiskan
ms.author: owend
ms.openlocfilehash: 95d0e41576e449ab10b243ef49cbe283940afe0b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598043"
---
# <a name="log-operations-in-analysis-services"></a><span data-ttu-id="fa56d-102">Analysis Services 中的記錄作業</span><span class="sxs-lookup"><span data-stu-id="fa56d-102">Log operations in Analysis Services</span></span>
  <span data-ttu-id="fa56d-103">Analysis Services 實例會將伺服器通知、錯誤和警告記錄到 msmdsrv.exe 檔中，您安裝的每個實例各一個。</span><span class="sxs-lookup"><span data-stu-id="fa56d-103">An Analysis Services instance will log server notifications, errors, and warnings to the msmdsrv.log file - one for each instance you install.</span></span> <span data-ttu-id="fa56d-104">管理員可以參考此記錄檔，獲得例行和異常等事件的深入見解。</span><span class="sxs-lookup"><span data-stu-id="fa56d-104">Administrators refer to this log for insights into routine and extraordinary events alike.</span></span> <span data-ttu-id="fa56d-105">最新版本的記錄功能已經過增強，可以加入更多資訊。</span><span class="sxs-lookup"><span data-stu-id="fa56d-105">In recent releases, logging has been enhanced to include more information.</span></span> <span data-ttu-id="fa56d-106">記錄檔記錄現在包含產品版本和版本資訊，以及處理器、記憶體、連接及封鎖事件。</span><span class="sxs-lookup"><span data-stu-id="fa56d-106">Log records now include product version and edition information, as well as processor, memory, connectivity, and blocking events.</span></span> <span data-ttu-id="fa56d-107">您可以在 [記錄改進](https://support.microsoft.com/kb/2965035)檢閱整個變更清單。</span><span class="sxs-lookup"><span data-stu-id="fa56d-107">You can review the entire change list at [Logging improvements](https://support.microsoft.com/kb/2965035).</span></span>  
  
 <span data-ttu-id="fa56d-108">除了內建的記錄功能，許多管理員和開發人員也使用 Analysis Services 社群所提供的工具來收集有關伺服器作業 (例如 **ASTrace**) 的資料。</span><span class="sxs-lookup"><span data-stu-id="fa56d-108">Besides the built-in logging feature, many administrators and developers also use tools provided by the Analysis Services community to collect data about server operations, such as **ASTrace**.</span></span> <span data-ttu-id="fa56d-109">請參閱 [Microsoft SQL Server 社群範例：Analysis Services](https://sqlsrvanalysissrvcs.codeplex.com/) 以取得下載連結。</span><span class="sxs-lookup"><span data-stu-id="fa56d-109">See [Microsoft SQL Server Community Samples: Analysis Services](https://sqlsrvanalysissrvcs.codeplex.com/) for the download links.</span></span>  
  
 <span data-ttu-id="fa56d-110">本主題包含下列幾節：</span><span class="sxs-lookup"><span data-stu-id="fa56d-110">This topic contains the following sections:</span></span>  
  
-   [<span data-ttu-id="fa56d-111">記錄檔的位置和類型</span><span class="sxs-lookup"><span data-stu-id="fa56d-111">Location and types of logs</span></span>](#bkmk_location)  
  
-   [<span data-ttu-id="fa56d-112">記錄檔組態設定的一般資訊</span><span class="sxs-lookup"><span data-stu-id="fa56d-112">General information on log file configuration settings</span></span>](#bkmk_general)  
  
-   [<span data-ttu-id="fa56d-113">MSMDSRV.EXE 服務記錄檔</span><span class="sxs-lookup"><span data-stu-id="fa56d-113">MSMDSRV service log file</span></span>](#bkmk_msmdsrv)  
  
-   [<span data-ttu-id="fa56d-114">查詢記錄</span><span class="sxs-lookup"><span data-stu-id="fa56d-114">Query logs</span></span>](#bkmk_querylog)  
  
-   [<span data-ttu-id="fa56d-115">迷你傾印 (.mdmp) 檔案</span><span class="sxs-lookup"><span data-stu-id="fa56d-115">Mini dump (.mdmp) files</span></span>](#bkmk_mdmp)  
  
-   [<span data-ttu-id="fa56d-116">訣竅和最佳做法</span><span class="sxs-lookup"><span data-stu-id="fa56d-116">Tips and best practices</span></span>](#bkmk_tips)  
  
> [!NOTE]  
>  <span data-ttu-id="fa56d-117">如果您正在尋找記錄的相關資訊，您也可能想要追蹤顯示處理和查詢執行路徑的作業。</span><span class="sxs-lookup"><span data-stu-id="fa56d-117">If you're looking for information about logging, you might also be interested in tracing operations that show processing and query execution paths.</span></span> <span data-ttu-id="fa56d-118">臨機操作和持續性追蹤 (例如稽核 Cube 存取) 的追蹤物件，以及如何充分運用可以在此頁面上找到連結的 Flight Recorder、SQL Server Profiler 和 xEvent 的建議： [監視 Analysis Services 執行個體](monitor-an-analysis-services-instance.md)。</span><span class="sxs-lookup"><span data-stu-id="fa56d-118">Trace objects for ad hoc and sustained tracing (such as auditing cube access) ─ as well as recommendations on how to best use Flight Recorder, SQL Server Profiler, and xEvents ─ can be found through the links on this page: [Monitor an Analysis Services Instance](monitor-an-analysis-services-instance.md).</span></span>  
  
##  <a name="location-and-types-of-logs"></a><a name="bkmk_location"></a><span data-ttu-id="fa56d-119">記錄檔的位置和類型</span><span class="sxs-lookup"><span data-stu-id="fa56d-119">Location and types of logs</span></span>  
 <span data-ttu-id="fa56d-120">Analysis Services 提供如下所述的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="fa56d-120">Analysis Services provides the logs described below.</span></span>  
  
|<span data-ttu-id="fa56d-121">檔案名稱或位置</span><span class="sxs-lookup"><span data-stu-id="fa56d-121">File name or Location</span></span>|<span data-ttu-id="fa56d-122">類型</span><span class="sxs-lookup"><span data-stu-id="fa56d-122">Type</span></span>|<span data-ttu-id="fa56d-123">用於</span><span class="sxs-lookup"><span data-stu-id="fa56d-123">Used for</span></span>|<span data-ttu-id="fa56d-124">依預設開啟</span><span class="sxs-lookup"><span data-stu-id="fa56d-124">On by default</span></span>|  
|---------------------------|----------|--------------|-------------------|  
|<span data-ttu-id="fa56d-125">Msmdsrv.log</span><span class="sxs-lookup"><span data-stu-id="fa56d-125">Msmdsrv.log</span></span>|<span data-ttu-id="fa56d-126">錯誤記錄檔</span><span class="sxs-lookup"><span data-stu-id="fa56d-126">Error log</span></span>|<span data-ttu-id="fa56d-127">例行監視和基本疑難排解</span><span class="sxs-lookup"><span data-stu-id="fa56d-127">Routine monitoring and basic troubleshooting</span></span>|<span data-ttu-id="fa56d-128">是</span><span class="sxs-lookup"><span data-stu-id="fa56d-128">Yes</span></span>|  
|<span data-ttu-id="fa56d-129">關聯式資料庫中的 OlapQueryLog 資料表</span><span class="sxs-lookup"><span data-stu-id="fa56d-129">OlapQueryLog table in a relational database</span></span>|<span data-ttu-id="fa56d-130">查詢記錄</span><span class="sxs-lookup"><span data-stu-id="fa56d-130">Query log</span></span>|<span data-ttu-id="fa56d-131">收集使用方式的最佳化精靈的輸入</span><span class="sxs-lookup"><span data-stu-id="fa56d-131">Collect inputs for the Usage Optimization Wizard</span></span>|<span data-ttu-id="fa56d-132">否</span><span class="sxs-lookup"><span data-stu-id="fa56d-132">No</span></span>|  
|<span data-ttu-id="fa56d-133">Sqldmp<guid>.mdmp \<guid> . .mdmp 檔案</span><span class="sxs-lookup"><span data-stu-id="fa56d-133">SQLDmp\<guid>.mdmp files</span></span>|<span data-ttu-id="fa56d-134">當機和例外狀況</span><span class="sxs-lookup"><span data-stu-id="fa56d-134">Crashes and exceptions</span></span>|<span data-ttu-id="fa56d-135">深入疑難排解</span><span class="sxs-lookup"><span data-stu-id="fa56d-135">Deep troubleshooting</span></span>|<span data-ttu-id="fa56d-136">否</span><span class="sxs-lookup"><span data-stu-id="fa56d-136">No</span></span>|  
  
 <span data-ttu-id="fa56d-137">我們強烈建議使用下列連結，以取得本主題中未涵蓋的其他資訊資源： [來自 Microsoft 支援的初始資料收集提示](https://blogs.msdn.com/b/as_emea/archive/2012/01/02/initial-data-collection-for-troubleshooting-analysis-services-issues.aspx)。</span><span class="sxs-lookup"><span data-stu-id="fa56d-137">We highly recommend the following link for additional information resources not covered in this topic: [Initial data collection tips from Microsoft Support](https://blogs.msdn.com/b/as_emea/archive/2012/01/02/initial-data-collection-for-troubleshooting-analysis-services-issues.aspx).</span></span>  
  
##  <a name="general-information-on-log-file-configuration-settings"></a><a name="bkmk_general"></a><span data-ttu-id="fa56d-138">記錄檔設定的一般資訊</span><span class="sxs-lookup"><span data-stu-id="fa56d-138">General information on log file configuration settings</span></span>  
 <span data-ttu-id="fa56d-139">您可以在 msmdsrv.ini 伺服器組態檔案中找到每個記錄檔的區段，其位於 \Program Files\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config 資料夾。</span><span class="sxs-lookup"><span data-stu-id="fa56d-139">You can find sections for each log in the msmdsrv.ini server configuration file, located in the \Program Files\Microsoft SQL Server\MSAS12.MSSQLSERVER\OLAP\Config folder.</span></span> <span data-ttu-id="fa56d-140">如需編輯此檔案的指示，請參閱 [Configure Server Properties in Analysis Services](../server-properties/server-properties-in-analysis-services.md) 。</span><span class="sxs-lookup"><span data-stu-id="fa56d-140">See [Configure Server Properties in Analysis Services](../server-properties/server-properties-in-analysis-services.md) for instructions on editing the file.</span></span>  
  
 <span data-ttu-id="fa56d-141">如果可行，我們建議您在 Management Studio 的伺服器屬性頁面中設定記錄屬性。</span><span class="sxs-lookup"><span data-stu-id="fa56d-141">Where possible, we suggest that you set logging properties in the server properties page of Management Studio.</span></span> <span data-ttu-id="fa56d-142">不過在某些情況下，您必須直接編輯 msmdsrv.ini 檔案，以設定系統管理工具中看不到的設定。</span><span class="sxs-lookup"><span data-stu-id="fa56d-142">Although in some cases, you must edit the msmdsrv.ini file directly to configure settings that are not visible in the administrative tools.</span></span>  
  
 <span data-ttu-id="fa56d-143">![顯示記錄檔設定的組態檔區段](../media/ssas-logfilesettings.png "顯示記錄檔設定的組態檔區段")</span><span class="sxs-lookup"><span data-stu-id="fa56d-143">![Section of the config file showing log settings](../media/ssas-logfilesettings.png "Section of the config file showing log settings")</span></span>  
  
##  <a name="msmdsrv-service-log-file"></a><a name="bkmk_msmdsrv"></a> <span data-ttu-id="fa56d-144">MSMDSRV 服務記錄檔</span><span class="sxs-lookup"><span data-stu-id="fa56d-144">MSMDSRV service log file</span></span>  
 <span data-ttu-id="fa56d-145">Analysis Services 會將伺服器作業記錄至 msmdsrv.log 檔案，其位於 \program files\Microsoft SQL Server\\<執行個體\>\Olap\Log，每個執行個體一個。</span><span class="sxs-lookup"><span data-stu-id="fa56d-145">Analysis Services logs server operations to the msmdsrv.log file, one per instance, located at \program files\Microsoft SQL Server\\<instance\>\Olap\Log.</span></span>  
  
 <span data-ttu-id="fa56d-146">這個記錄檔會在每次服務重新啟動時清空。</span><span class="sxs-lookup"><span data-stu-id="fa56d-146">This log file is emptied at each service restart.</span></span> <span data-ttu-id="fa56d-147">在舊版中，管理員之所以重新啟動服務，有時只是為了在記錄檔成長到太大而變得無法使用之前加以清除。</span><span class="sxs-lookup"><span data-stu-id="fa56d-147">In previous releases, administrators would sometimes restart the service for the sole purpose of flushing the log file before it could grow so large as to become unusable.</span></span> <span data-ttu-id="fa56d-148">現已不再需要這麼做。</span><span class="sxs-lookup"><span data-stu-id="fa56d-148">This is no longer necessary.</span></span> <span data-ttu-id="fa56d-149">SQL Server 2012 SP2 中及更新版本中推出的組態設定，可讓您控制記錄檔和其歷程記錄的大小：</span><span class="sxs-lookup"><span data-stu-id="fa56d-149">Configuration settings, introduced in SQL Server 2012 SP2 and later, give you control over the size of the log file and its history:</span></span>  
  
-   <span data-ttu-id="fa56d-150">`MaxFileSizeMB` 指定最大記錄檔大小 (以 MB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="fa56d-150">`MaxFileSizeMB` specifies a maximum log file size in megabytes.</span></span> <span data-ttu-id="fa56d-151">預設值是 256。</span><span class="sxs-lookup"><span data-stu-id="fa56d-151">The default is 256.</span></span> <span data-ttu-id="fa56d-152">有效的取代值必須是正整數。</span><span class="sxs-lookup"><span data-stu-id="fa56d-152">A valid replacement value must be a positive integer.</span></span> <span data-ttu-id="fa56d-153">達到 `MaxFileSizeMB` 時，Analysis Services 會將目前的檔案重新命名為 msmdsrv{current timestamp}.log 檔案，並啟動新的 msmdsrv.log 檔案。</span><span class="sxs-lookup"><span data-stu-id="fa56d-153">When `MaxFileSizeMB` is reached, Analysis Services renames the current file as msmdsrv{current timestamp}.log file, and starts a new msmdsrv.log file.</span></span>  
  
-   <span data-ttu-id="fa56d-154">`MaxNumberFiles`指定保留較舊的記錄檔。</span><span class="sxs-lookup"><span data-stu-id="fa56d-154">`MaxNumberFiles` specifies retention of older log files.</span></span> <span data-ttu-id="fa56d-155">預設值是 0 (停用)。</span><span class="sxs-lookup"><span data-stu-id="fa56d-155">The default is 0 (disabled).</span></span> <span data-ttu-id="fa56d-156">您可以將它變更為正整數，以保留記錄檔的版本。</span><span class="sxs-lookup"><span data-stu-id="fa56d-156">You can change it to a positive integer to keep versions of the log file.</span></span> <span data-ttu-id="fa56d-157">達到 `MaxNumberFiles` 時，Analysis Services 會刪除其名稱中具有最舊的時間戳記的檔案。</span><span class="sxs-lookup"><span data-stu-id="fa56d-157">When `MaxNumberFiles` is reached, Analysis Services deletes the file with the oldest timestamp in its name.</span></span>  
  
 <span data-ttu-id="fa56d-158">若要使用這些設定，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="fa56d-158">To use these settings, do the following:</span></span>  
  
1.  <span data-ttu-id="fa56d-159">在記事本中開啟 msmdsrv.ini。</span><span class="sxs-lookup"><span data-stu-id="fa56d-159">Open msmdsrv.ini in NotePad.</span></span>  
  
2.  <span data-ttu-id="fa56d-160">複製下列兩行：</span><span class="sxs-lookup"><span data-stu-id="fa56d-160">Copy the following two lines:</span></span>  
  
    ```  
    <MaxFileSizeMB>256</MaxFileSizeMB>  
    <MaxNumberOfLogFiles>5</MaxNumberOfLogFiles>  
    ```  
  
3.  <span data-ttu-id="fa56d-161">將兩行貼到 msmdsrv.ini 的的 Log 區段，位於 msmdsrv.log 檔案名稱下。</span><span class="sxs-lookup"><span data-stu-id="fa56d-161">Paste the two lines into the Log section of msmdsrv.ini, below the filename for msmdsrv.log.</span></span> <span data-ttu-id="fa56d-162">這兩個設定必須手動加入。</span><span class="sxs-lookup"><span data-stu-id="fa56d-162">Both settings must be added manually.</span></span> <span data-ttu-id="fa56d-163">msmdsrv.ini 檔案中沒有其預留位置。</span><span class="sxs-lookup"><span data-stu-id="fa56d-163">There are no placeholders for them in the msmdsrv.ini file.</span></span>  
  
     <span data-ttu-id="fa56d-164">已變更的組態檔看起來應該如下所示：</span><span class="sxs-lookup"><span data-stu-id="fa56d-164">The changed configuration file should look like the following:</span></span>  
  
    ```  
    <Log>  
    <File>msmdsrv.log</File>  
    <MaxFileSizeMB>256</MaxFileSizeMB>  
    <MaxNumberOfLogFiles>5</MaxNumberOfLogFiles>  
    <FileBufferSize>0</FileBufferSize>  
  
    ```  
  
4.  <span data-ttu-id="fa56d-165">如果提供的值與您想要的不同，請編輯值。</span><span class="sxs-lookup"><span data-stu-id="fa56d-165">Edit the values if those provided differ from what you want.</span></span>  
  
5.  <span data-ttu-id="fa56d-166">儲存檔案。</span><span class="sxs-lookup"><span data-stu-id="fa56d-166">Save the file.</span></span>  
  
6.  <span data-ttu-id="fa56d-167">重新啟動服務。</span><span class="sxs-lookup"><span data-stu-id="fa56d-167">Restart the service.</span></span>  
  
##  <a name="query-logs"></a><a name="bkmk_querylog"></a><span data-ttu-id="fa56d-168">查詢記錄</span><span class="sxs-lookup"><span data-stu-id="fa56d-168">Query logs</span></span>  
 <span data-ttu-id="fa56d-169">查詢記錄的名稱與它的功能有些出入，因為它並不會為您記錄使用者的 MDX 或 DAX 查詢活動。</span><span class="sxs-lookup"><span data-stu-id="fa56d-169">The query log is a bit of a misnomer in that it does not log the MDX or DAX query activity of your users.</span></span> <span data-ttu-id="fa56d-170">相反地，它會收集 Analysis Services 產生的查詢中的資料，這後續會做為使用方式的最佳化精靈中的資料輸入。</span><span class="sxs-lookup"><span data-stu-id="fa56d-170">Instead, it collects data about queries generated by Analysis Services, which is subsequently used as data input in the Usage Based Optimization Wizard.</span></span> <span data-ttu-id="fa56d-171">查詢記錄中收集的資料不適合直接分析。</span><span class="sxs-lookup"><span data-stu-id="fa56d-171">The data collected in the query log is not intended for direct analysis.</span></span> <span data-ttu-id="fa56d-172">具體而言，資料集是以位元陣列描述，具有零或一，指出查詢中包含的資料集部分。</span><span class="sxs-lookup"><span data-stu-id="fa56d-172">Specifically, the datasets are described in bit arrays, with a zero or a one indicating the parts of dataset is included in the query.</span></span> <span data-ttu-id="fa56d-173">重申，此資料專供精靈使用。</span><span class="sxs-lookup"><span data-stu-id="fa56d-173">Again, this data is meant for the wizard.</span></span>  
  
 <span data-ttu-id="fa56d-174">針對查詢監視和疑難排解，許多開發人員和管理員會使用社群工具 **ASTrace**來監視查詢。</span><span class="sxs-lookup"><span data-stu-id="fa56d-174">For query monitoring and troubleshooting, many developers and administrators use a community tool, **ASTrace**, to monitor queries.</span></span> <span data-ttu-id="fa56d-175">您也可以使用 SQL Server Profiler、xEvents 或 Analysis Services 追蹤。</span><span class="sxs-lookup"><span data-stu-id="fa56d-175">You can also use SQL Server Profiler, xEvents, or an Analysis Services trace.</span></span> <span data-ttu-id="fa56d-176">請參閱 [監視 Analysis Services 執行個體](monitor-an-analysis-services-instance.md) ，以取得追蹤的相關連結。</span><span class="sxs-lookup"><span data-stu-id="fa56d-176">See [Monitor an Analysis Services Instance](monitor-an-analysis-services-instance.md) for tracing-related links.</span></span>  
  
 <span data-ttu-id="fa56d-177">何時應該使用查詢記錄？</span><span class="sxs-lookup"><span data-stu-id="fa56d-177">When should you use the query log?</span></span> <span data-ttu-id="fa56d-178">我們建議您在包含使用方式的最佳化精靈的查詢效能微調練習中啟用查詢記錄。</span><span class="sxs-lookup"><span data-stu-id="fa56d-178">We recommend enabling the query log as part of a query performance tuning exercise that includes the Usage Based Optimization Wizard.</span></span> <span data-ttu-id="fa56d-179">在您啟用功能、建立資料結構以支援它，並設定 Analysis Services 用來找出並填入記錄檔的屬性之前，查詢記錄不會存在。</span><span class="sxs-lookup"><span data-stu-id="fa56d-179">The query log does not exist until you enable the feature, create the data structures to support it, and set properties used by Analysis Services to locate and populate the log.</span></span>  
  
 <span data-ttu-id="fa56d-180">若要啟用查詢記錄，請遵循下列步驟：</span><span class="sxs-lookup"><span data-stu-id="fa56d-180">To enable the query log, follow these steps:</span></span>  
  
1.  <span data-ttu-id="fa56d-181">建立 SQL Server 關聯式資料庫來儲存查詢記錄。</span><span class="sxs-lookup"><span data-stu-id="fa56d-181">Create a SQL Server relational database to store the query log.</span></span>  
  
2.  <span data-ttu-id="fa56d-182">授與 Analysis Services 服務帳戶資料庫的足夠權限。</span><span class="sxs-lookup"><span data-stu-id="fa56d-182">Grant the Analysis Services service account sufficient permissions on the database.</span></span> <span data-ttu-id="fa56d-183">帳戶需要建立資料表、寫入資料表，並從資料表讀取的權限。</span><span class="sxs-lookup"><span data-stu-id="fa56d-183">The account needs permission to create a table, write to the table, and read from the table.</span></span>  
  
3.  <span data-ttu-id="fa56d-184">在 SQL Server Management Studio 中，以滑鼠右鍵按一下**Analysis Services**  |  **屬性**]  |  **[一般**]，將**CreateQueryLogTable**設定為 [true]。</span><span class="sxs-lookup"><span data-stu-id="fa56d-184">In SQL Server Management Studio, right-click **Analysis Services** | **Properties** | **General**, set **CreateQueryLogTable** to true.</span></span>  
  
4.  <span data-ttu-id="fa56d-185">如果您想要以不同的速率對查詢取樣，或使用不同的資料表名稱，請選擇性地變更 **QueryLogSampling** 或 **QueryLogTableName** 。</span><span class="sxs-lookup"><span data-stu-id="fa56d-185">Optionally, change **QueryLogSampling** or **QueryLogTableName** if you want to sample queries at a different rate, or use a different name for the table.</span></span>  
  
 <span data-ttu-id="fa56d-186">在您執行足夠的 MDX 查詢以符合取樣需求之前，將不會建立查詢記錄資料表。</span><span class="sxs-lookup"><span data-stu-id="fa56d-186">The query log table will not be created until you have run enough MDX queries to meet the sampling requirements.</span></span> <span data-ttu-id="fa56d-187">比方說，如果您保留預設值 10，您必須先執行至少 10 個查詢，才會建立資料表。</span><span class="sxs-lookup"><span data-stu-id="fa56d-187">For example, if you keep the default value of 10, you must run at least 10 queries before the table will be created.</span></span>  
  
 <span data-ttu-id="fa56d-188">查詢記錄設定是以整個伺服器為範圍。</span><span class="sxs-lookup"><span data-stu-id="fa56d-188">Query log settings are server wide.</span></span> <span data-ttu-id="fa56d-189">您指定的設定會用於此伺服器上執行的所有資料庫。</span><span class="sxs-lookup"><span data-stu-id="fa56d-189">The settings you specify will be used by all databases running on this server.</span></span>  
  
 <span data-ttu-id="fa56d-190">![Management Studio 中的查詢記錄設定](../media/ssas-querylogsettings.png "Management Studio 中的查詢記錄設定")</span><span class="sxs-lookup"><span data-stu-id="fa56d-190">![Query log settings in Management Studio](../media/ssas-querylogsettings.png "Query log settings in Management Studio")</span></span>  
  
 <span data-ttu-id="fa56d-191">在指定組態設定之後，執行 MDX 查詢多次。</span><span class="sxs-lookup"><span data-stu-id="fa56d-191">After the configuration settings are specified, run an MDX query multiple times.</span></span> <span data-ttu-id="fa56d-192">如果取樣設為 10，則執行查詢 11 次。確認已建立資料表。</span><span class="sxs-lookup"><span data-stu-id="fa56d-192">If sampling is set to 10, run the query 11 times.Verify the table is created.</span></span> <span data-ttu-id="fa56d-193">在 Management Studio 中，連接到關聯式資料庫引擎，開啟資料庫資料夾，開啟 **[資料表]** 資料夾，並確認 **OlapQueryLog** 存在。</span><span class="sxs-lookup"><span data-stu-id="fa56d-193">In Management Studio, connect to the relational database engine, open the database folder, open the **Tables** folder, and verify that **OlapQueryLog** exists.</span></span> <span data-ttu-id="fa56d-194">如果無法立即看到資料表，請重新整理資料夾，以收取其內容的任何變更。</span><span class="sxs-lookup"><span data-stu-id="fa56d-194">If you do not immediately see the table, refresh the folder to pick up any changes to its contents.</span></span>  
  
 <span data-ttu-id="fa56d-195">允許查詢記錄對使用方式的最佳化精靈累積足夠的資料。</span><span class="sxs-lookup"><span data-stu-id="fa56d-195">Allow the query log to accumulate sufficient data for the Usage Based Optimization Wizard.</span></span> <span data-ttu-id="fa56d-196">如果查詢量會循環，請擷取足夠的流量來取得具有代表性的資料集。</span><span class="sxs-lookup"><span data-stu-id="fa56d-196">If query volumes are cyclical, capture enough traffic to have a representative set of data.</span></span> <span data-ttu-id="fa56d-197">請參閱 [使用方式的最佳化精靈](https://msdn.microsoft.com/library/ms189706.aspx) ，以取得如何執行此精靈的指示。</span><span class="sxs-lookup"><span data-stu-id="fa56d-197">See [Usage Based Optimization Wizard](https://msdn.microsoft.com/library/ms189706.aspx) for instructions on how to run the wizard.</span></span>  
  
 <span data-ttu-id="fa56d-198">請參閱 [設定 Analysis Services 查詢記錄](https://technet.microsoft.com/library/Cc917676) ，以深入了解查詢記錄組態。</span><span class="sxs-lookup"><span data-stu-id="fa56d-198">See [Configuring the Analysis Services Query Log](https://technet.microsoft.com/library/Cc917676) to learn more about query log configuration.</span></span> <span data-ttu-id="fa56d-199">雖然本文件相當老舊，但最新版本中並未變更查詢記錄組態，因此其內含的資訊仍適用。</span><span class="sxs-lookup"><span data-stu-id="fa56d-199">Although the paper is quite old, query log configuration has not changed in recent releases and the information it contains still applies.</span></span>  
  
##  <a name="mini-dump-mdmp-files"></a><a name="bkmk_mdmp"></a><span data-ttu-id="fa56d-200">迷你傾印 (. .mdmp) 檔案</span><span class="sxs-lookup"><span data-stu-id="fa56d-200">Mini dump (.mdmp) files</span></span>  
 <span data-ttu-id="fa56d-201">傾印檔案會擷取用於分析異常事件的資料。</span><span class="sxs-lookup"><span data-stu-id="fa56d-201">Dump files capture data used for analyzing extraordinary events.</span></span> <span data-ttu-id="fa56d-202">Analysis Services 會自動產生迷你傾印 (.mdmp)，以回應伺服器當機、例外狀況，以及一些組態錯誤。</span><span class="sxs-lookup"><span data-stu-id="fa56d-202">Analysis Services automatically generates mini dumps (.mdmp) in response to a server crash, exception, and some configuration errors.</span></span> <span data-ttu-id="fa56d-203">此功能已啟用，但不會自動傳送當機報告。</span><span class="sxs-lookup"><span data-stu-id="fa56d-203">The feature is enabled, but does not send crash reports automatically.</span></span>  
  
 <span data-ttu-id="fa56d-204">當機報告是透過 Msmdsrv.ini 檔案中的 Exception 區段設定。</span><span class="sxs-lookup"><span data-stu-id="fa56d-204">Crash reports are configured through the Exception section in the Msmdsrv.ini file.</span></span> <span data-ttu-id="fa56d-205">這些設定會控制記憶體傾印檔案產生。</span><span class="sxs-lookup"><span data-stu-id="fa56d-205">These settings control memory dump file generation.</span></span> <span data-ttu-id="fa56d-206">下列程式碼片段會顯示預設值：</span><span class="sxs-lookup"><span data-stu-id="fa56d-206">The following snippet shows the default values:</span></span>  
  
```  
<Exception>  
<CreateAndSendCrashReports>1</CreateAndSendCrashReports>  
<CrashReportsFolder/>  
<SQLDumperFlagsOn>0x0</SQLDumperFlagsOn>  
<SQLDumperFlagsOff>0x0</SQLDumperFlagsOff>  
<MiniDumpFlagsOn>0x0</MiniDumpFlagsOn>  
<MiniDumpFlagsOff>0x0</MiniDumpFlagsOff>  
<MinidumpErrorList>0xC1000000, 0xC1000001, 0xC102003F, 0xC1360054, 0xC1360055</MinidumpErrorList>  
<ExceptionHandlingMode>0</ExceptionHandlingMode>  
<CriticalErrorHandling>1</CriticalErrorHandling>  
<MaxExceptions>500</MaxExceptions>  
<MaxDuplicateDumps>1</MaxDuplicateDumps>  
</Exception>  
```  
  
 <span data-ttu-id="fa56d-207">**設定當機報告**</span><span class="sxs-lookup"><span data-stu-id="fa56d-207">**Configure Crash Reports**</span></span>  
  
 <span data-ttu-id="fa56d-208">除非 Microsoft 支援另有指示，否則大部分的管理員均會使用預設設定。</span><span class="sxs-lookup"><span data-stu-id="fa56d-208">Unless otherwise directed by Microsoft Support, most administrators use the default settings.</span></span> <span data-ttu-id="fa56d-209">這個較舊的知識庫文件仍然用來提供有關如何設定傾印檔案的指示： [如何設定 Analysis Services 以產生記憶體傾印檔案](https://support.microsoft.com/kb/919711)。</span><span class="sxs-lookup"><span data-stu-id="fa56d-209">This older KB article is still used to provide instruction on how to configure dump files: [How to configure Analysis Services to generate memory dump files](https://support.microsoft.com/kb/919711).</span></span>  
  
 <span data-ttu-id="fa56d-210">最有可能遭到修改的組態設定是用來判斷是否會產生記憶體傾印檔案的 `CreateAndSendCrashReports` 設定。</span><span class="sxs-lookup"><span data-stu-id="fa56d-210">The configuration setting most likely to be modified is the `CreateAndSendCrashReports` setting used to determine whether a memory dump file will be generated.</span></span>  
  
|<span data-ttu-id="fa56d-211">值</span><span class="sxs-lookup"><span data-stu-id="fa56d-211">Value</span></span>|<span data-ttu-id="fa56d-212">描述</span><span class="sxs-lookup"><span data-stu-id="fa56d-212">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fa56d-213">0</span><span class="sxs-lookup"><span data-stu-id="fa56d-213">0</span></span>|<span data-ttu-id="fa56d-214">關閉記憶體傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="fa56d-214">Turns off the memory dump file.</span></span> <span data-ttu-id="fa56d-215">將會忽略 Exception 區段下的所有其他設定。</span><span class="sxs-lookup"><span data-stu-id="fa56d-215">All other settings under the Exception section are ignored.</span></span>|  
|<span data-ttu-id="fa56d-216">1</span><span class="sxs-lookup"><span data-stu-id="fa56d-216">1</span></span>|<span data-ttu-id="fa56d-217">(預設值) 啟用，但不會傳送記憶體傾印檔案。</span><span class="sxs-lookup"><span data-stu-id="fa56d-217">(Default) Enables, but does not send, the memory dump file.</span></span>|  
|<span data-ttu-id="fa56d-218">2</span><span class="sxs-lookup"><span data-stu-id="fa56d-218">2</span></span>|<span data-ttu-id="fa56d-219">啟用並自動傳送錯誤報告給 Microsoft。</span><span class="sxs-lookup"><span data-stu-id="fa56d-219">Enables and automatically sends an error report to Microsoft.</span></span>|  
  
 <span data-ttu-id="fa56d-220">`CrashReportsFolder` 是將傾印檔案的位置。</span><span class="sxs-lookup"><span data-stu-id="fa56d-220">`CrashReportsFolder` is the location of the dump files.</span></span> <span data-ttu-id="fa56d-221">根據預設，可以在 \Olap\Log 資料夾中找到一個 .mdmp 檔以及相關聯的記錄檔記錄。</span><span class="sxs-lookup"><span data-stu-id="fa56d-221">By default, an .mdmp file and associated log records can be found in the \Olap\Log folder.</span></span>  
  
 <span data-ttu-id="fa56d-222">`SQLDumperFlagsOn` 用來產生完整傾印。</span><span class="sxs-lookup"><span data-stu-id="fa56d-222">`SQLDumperFlagsOn` is used to generate a full dump.</span></span> <span data-ttu-id="fa56d-223">根據預設，不會啟用完整傾印。</span><span class="sxs-lookup"><span data-stu-id="fa56d-223">By default, full dumps are not enabled.</span></span> <span data-ttu-id="fa56d-224">您可以將此屬性設定為 `0x34`。</span><span class="sxs-lookup"><span data-stu-id="fa56d-224">You can set this property to `0x34`.</span></span>  
  
 <span data-ttu-id="fa56d-225">下列連結提供更多背景：</span><span class="sxs-lookup"><span data-stu-id="fa56d-225">The following links provide more background:</span></span>  
  
-   [<span data-ttu-id="fa56d-226">想要使用小型傾印更深入了解 SQL Server</span><span class="sxs-lookup"><span data-stu-id="fa56d-226">Looking Deeper into SQL Server using Minidumps</span></span>](https://blogs.msdn.com/b/sqlcat/archive/2009/09/11/looking-deeper-into-sql-server-using-minidumps.aspx)  
  
-   [<span data-ttu-id="fa56d-227">如何建立使用者模式傾印檔案</span><span class="sxs-lookup"><span data-stu-id="fa56d-227">How to create a user mode dump file</span></span>](https://support.microsoft.com/kb/931673)  
  
-   [<span data-ttu-id="fa56d-228">如何使用 Sqldumper.exe 公用程式，在 SQL Server 產生傾印檔案</span><span class="sxs-lookup"><span data-stu-id="fa56d-228">How to use the Sqldumper.exe utility to generate a dump file in SQL Server</span></span>](https://support.microsoft.com/kb/917825)  
  
##  <a name="tips-and-best-practices"></a><a name="bkmk_tips"></a><span data-ttu-id="fa56d-229">秘訣和最佳作法</span><span class="sxs-lookup"><span data-stu-id="fa56d-229">Tips and best practices</span></span>  
 <span data-ttu-id="fa56d-230">本節是整篇文章所述秘訣的回顧。</span><span class="sxs-lookup"><span data-stu-id="fa56d-230">This section is a recap of the tips mentioned throughout this article.</span></span>  
  
-   <span data-ttu-id="fa56d-231">設定 msmdsrv.log 檔案來控制 msmdsrv 記錄檔的大小和數目。</span><span class="sxs-lookup"><span data-stu-id="fa56d-231">Configure the msmdsrv.log file to control the size and number of msmdsrv log file.</span></span> <span data-ttu-id="fa56d-232">預設不會啟用此設定，因此務必將它們加入做為後續安裝步驟。</span><span class="sxs-lookup"><span data-stu-id="fa56d-232">The settings are not enabled by default, so be sure to add them as post-installation step.</span></span> <span data-ttu-id="fa56d-233">請參閱本主題的 [MSMDSRV 服務記錄檔](#bkmk_msmdsrv) 。</span><span class="sxs-lookup"><span data-stu-id="fa56d-233">See [MSMDSRV service log file](#bkmk_msmdsrv) in this topic.</span></span>  
  
-   <span data-ttu-id="fa56d-234">檢閱來自 Microsoft 客戶支援的這些部落格文章，以了解他們用何資源來取得有關伺服器作業的資訊： [初始資料收集](https://blogs.msdn.com/b/as_emea/archive/2012/01/02/initial-data-collection-for-troubleshooting-analysis-services-issues.aspx)</span><span class="sxs-lookup"><span data-stu-id="fa56d-234">Review this blog post from Microsoft Customer Support to learn what resources they use to get information about server operations: [Initial Data Collection](https://blogs.msdn.com/b/as_emea/archive/2012/01/02/initial-data-collection-for-troubleshooting-analysis-services-issues.aspx)</span></span>  
  
-   <span data-ttu-id="fa56d-235">若要找出查詢 Cube 的對象，請使用 ASTrace2012，而不是查詢記錄。</span><span class="sxs-lookup"><span data-stu-id="fa56d-235">Use ASTrace2012, rather than a query log, to find out who is querying cubes.</span></span> <span data-ttu-id="fa56d-236">查詢記錄通常用來對使用方式的最佳化精靈提供輸入，其擷取的資料並不易閱讀或解譯。</span><span class="sxs-lookup"><span data-stu-id="fa56d-236">The query log is typically used to provide input into the Usage Based Optimization Wizard, and the data it captures is not easy to read or interpret.</span></span> <span data-ttu-id="fa56d-237">ASTrace2012 是廣泛使用的社群工具，可擷取查詢作業。</span><span class="sxs-lookup"><span data-stu-id="fa56d-237">ASTrace2012 is a community tool, widely used, that captures query operations.</span></span> <span data-ttu-id="fa56d-238">請參閱 [Microsoft SQL Server 社群範例：Analysis Services](https://sqlsrvanalysissrvcs.codeplex.com/)。</span><span class="sxs-lookup"><span data-stu-id="fa56d-238">See [Microsoft SQL Server Community Samples: Analysis Services](https://sqlsrvanalysissrvcs.codeplex.com/).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa56d-239">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa56d-239">See Also</span></span>  
 <span data-ttu-id="fa56d-240">[Analysis Services 實例管理](analysis-services-instance-management.md) </span><span class="sxs-lookup"><span data-stu-id="fa56d-240">[Analysis Services Instance Management](analysis-services-instance-management.md) </span></span>  
 <span data-ttu-id="fa56d-241">[使用 SQL Server Profiler 監視 Analysis Services 簡介](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md) </span><span class="sxs-lookup"><span data-stu-id="fa56d-241">[Introduction to Monitoring Analysis Services with SQL Server Profiler](introduction-to-monitoring-analysis-services-with-sql-server-profiler.md) </span></span>  
 [<span data-ttu-id="fa56d-242">在 Analysis Services 中設定伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="fa56d-242">Configure Server Properties in Analysis Services</span></span>](../server-properties/server-properties-in-analysis-services.md)  
  
  
