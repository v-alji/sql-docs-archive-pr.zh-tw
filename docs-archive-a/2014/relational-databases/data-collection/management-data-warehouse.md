---
title: 管理資料倉儲 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collector [SQL Server], management data warehouse
- data warehouse
- management data warehouse
ms.assetid: 9874a8b2-7ccd-494a-944c-ad33b30b5499
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 96eb26c3e273832aead4aa0421304df17dc5b8ff
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594104"
---
# <a name="management-data-warehouse"></a><span data-ttu-id="189c3-102">管理資料倉儲</span><span class="sxs-lookup"><span data-stu-id="189c3-102">Management Data Warehouse</span></span>
  <span data-ttu-id="189c3-103">管理資料倉儲是一種關聯式資料庫，其中包含從伺服器 (它是資料收集目標) 收集而來的資料。</span><span class="sxs-lookup"><span data-stu-id="189c3-103">The management data warehouse is a relational database that contains the data that is collected from a server that is a data collection target.</span></span> <span data-ttu-id="189c3-104">這項資料是用來產生系統資料收集組的報表，而且也可用來建立自訂報表。</span><span class="sxs-lookup"><span data-stu-id="189c3-104">This data is used to generate the reports for the System Data collection sets, and can also be used to create custom reports.</span></span>  
  
 <span data-ttu-id="189c3-105">資料收集器基礎結構會定義實作資料庫管理員所定義之保留原則所需的作業和維護計畫。</span><span class="sxs-lookup"><span data-stu-id="189c3-105">The data collector infrastructure defines the jobs and maintenance plans that are needed to implement the retention policies defined by the database administrator.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="189c3-106">在這一版的資料收集器中，會使用簡單復原模式建立管理資料倉儲，使記錄量降到最小。</span><span class="sxs-lookup"><span data-stu-id="189c3-106">For this release of the data collector, the management data warehouse is created using the Simple recovery model, to minimize logging.</span></span> <span data-ttu-id="189c3-107">您應該實作適合於組織的復原模式。</span><span class="sxs-lookup"><span data-stu-id="189c3-107">You should implement the appropriate recovery model for your organization.</span></span>  
  
## <a name="deploying-and-using-the-data-warehouse"></a><span data-ttu-id="189c3-108">部署及使用資料倉儲</span><span class="sxs-lookup"><span data-stu-id="189c3-108">Deploying and Using the Data Warehouse</span></span>  
 <span data-ttu-id="189c3-109">您可以將這個管理資料倉儲安裝在執行資料收集器的相同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上。</span><span class="sxs-lookup"><span data-stu-id="189c3-109">You can install the management data warehouse on the same instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] that runs the data collector.</span></span> <span data-ttu-id="189c3-110">但是，如果所監視的伺服器上有伺服器資源或效能的問題，您可以將管理資料倉儲安裝在另一部電腦上。</span><span class="sxs-lookup"><span data-stu-id="189c3-110">However, if server resources or performance is an issue on the server being monitored, you can install the management data warehouse on a different computer.</span></span>  
  
 <span data-ttu-id="189c3-111">當您建立管理資料倉儲時，將會針對預先定義的系統收集組建立必要的結構描述及其物件。</span><span class="sxs-lookup"><span data-stu-id="189c3-111">The required schemas and their objects for the predefined system collection sets are created when you create the management data warehouse.</span></span> <span data-ttu-id="189c3-112">所建立的結構描述包括核心和快照集。第三個結構描述 custom_snapshots 是在建立使用者定義的收集組 (其中包含使用一般 T-SQL 收集器型別的收集項) 時建立。</span><span class="sxs-lookup"><span data-stu-id="189c3-112">The schemas that are created are core and snapshots.A third schema, custom_snapshots, is created when user-defined collection sets are created that include collection items that use the Generic T-SQL Query collector type.</span></span>  
  
###### <a name="core-schema"></a><span data-ttu-id="189c3-113">核心結構描述</span><span class="sxs-lookup"><span data-stu-id="189c3-113">Core schema</span></span>  
 <span data-ttu-id="189c3-114">核心結構描述會描述用來組織及識別所收集之資料的資料表、預存程序和檢視表。</span><span class="sxs-lookup"><span data-stu-id="189c3-114">The core schema describes the tables, stored procedures, and views that are used to organize and to identify collected data.</span></span> <span data-ttu-id="189c3-115">這些資料表會在針對個別收集器型別建立的所有資料表之間共用。</span><span class="sxs-lookup"><span data-stu-id="189c3-115">These tables are shared among all the data tables created for individual collector types.</span></span> <span data-ttu-id="189c3-116">這個結構描述已經鎖定，只有管理資料倉儲資料庫的擁有者才可以修改。</span><span class="sxs-lookup"><span data-stu-id="189c3-116">This schema is locked and can only be modified by the owner of the management data warehouse database.</span></span> <span data-ttu-id="189c3-117">此結構描述中的資料表名稱會有 "core" 的前置詞。</span><span class="sxs-lookup"><span data-stu-id="189c3-117">The names of the tables in this schema are prefixed by "core".</span></span>  
  
 <span data-ttu-id="189c3-118">下表描述核心結構描述中的資料庫資料表。</span><span class="sxs-lookup"><span data-stu-id="189c3-118">The following table describes the database tables in the core schema.</span></span> <span data-ttu-id="189c3-119">這些資料庫資料表可讓資料收集器追蹤資料的來源、繼承者，以及何時將資料上傳到資料倉儲。</span><span class="sxs-lookup"><span data-stu-id="189c3-119">These database tables enable the data collector to track where the data came from, who inserted it, and when it was uploaded to the data warehouse.</span></span>  
  
|<span data-ttu-id="189c3-120">資料表名稱</span><span class="sxs-lookup"><span data-stu-id="189c3-120">Table name</span></span>|<span data-ttu-id="189c3-121">描述</span><span class="sxs-lookup"><span data-stu-id="189c3-121">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="189c3-122">core.performance_counter_report_group_items</span><span class="sxs-lookup"><span data-stu-id="189c3-122">core.performance_counter_report_group_items</span></span>|<span data-ttu-id="189c3-123">儲存有關管理資料倉儲報表應該如何群組和彙總效能計數器的資訊。</span><span class="sxs-lookup"><span data-stu-id="189c3-123">Stores information about how the management data warehouse reports should group and aggregate performance counters.</span></span>|  
|<span data-ttu-id="189c3-124">core.snapshots_internal</span><span class="sxs-lookup"><span data-stu-id="189c3-124">core.snapshots_internal</span></span>|<span data-ttu-id="189c3-125">識別每個新的快照集。</span><span class="sxs-lookup"><span data-stu-id="189c3-125">Identifies each new snapshot.</span></span> <span data-ttu-id="189c3-126">每當上傳封裝開始上傳新的資料批次時，就會在這個資料表中插入新的資料列。</span><span class="sxs-lookup"><span data-stu-id="189c3-126">A new row is inserted into this table whenever an upload package starts uploading a new batch of data.</span></span>|  
|<span data-ttu-id="189c3-127">core.snapshot_timetable_internal</span><span class="sxs-lookup"><span data-stu-id="189c3-127">core.snapshot_timetable_internal</span></span>|<span data-ttu-id="189c3-128">儲存有關快照集時間的資訊。</span><span class="sxs-lookup"><span data-stu-id="189c3-128">Stores information about the snapshot times.</span></span> <span data-ttu-id="189c3-129">快照集時間會儲存在個別的資料表中，因為許多快照集可以幾乎發生在相同的時間。</span><span class="sxs-lookup"><span data-stu-id="189c3-129">The snapshot time is stored in a separate table because many snapshots can happen at nearly the same time.</span></span>|  
|<span data-ttu-id="189c3-130">core.source.info_internal</span><span class="sxs-lookup"><span data-stu-id="189c3-130">core.source.info_internal</span></span>|<span data-ttu-id="189c3-131">此資料表會儲存有關資料來源的資訊。</span><span class="sxs-lookup"><span data-stu-id="189c3-131">This table stores information about the data source.</span></span> <span data-ttu-id="189c3-132">每當新的收集組開始上傳資料到資料倉儲時，就會更新這個資料表。</span><span class="sxs-lookup"><span data-stu-id="189c3-132">This table is updated whenever a new collection set starts uploading data to the data warehouse.</span></span>|  
|<span data-ttu-id="189c3-133">core.supported_collector_types_internal</span><span class="sxs-lookup"><span data-stu-id="189c3-133">core.supported_collector_types_internal</span></span>|<span data-ttu-id="189c3-134">包含可以上傳資料到管理資料倉儲之已註冊收集器型別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="189c3-134">Contains the IDs of registered collector types that can upload data to the management data warehouse.</span></span> <span data-ttu-id="189c3-135">只有當更新倉儲的結構描述來支援新的收集器型別時，才會更新這個資料表。</span><span class="sxs-lookup"><span data-stu-id="189c3-135">This table is only updated when the schema of the warehouse is updated to support a new collector type.</span></span> <span data-ttu-id="189c3-136">當建立管理資料倉儲時，這個資料表中會填入資料收集器所提供之收集器型別的識別碼。</span><span class="sxs-lookup"><span data-stu-id="189c3-136">When the management data warehouse is created, this table is populated with the IDs of the collector types provided by the data collector.</span></span>|  
|<span data-ttu-id="189c3-137">core.wait_categories</span><span class="sxs-lookup"><span data-stu-id="189c3-137">core.wait_categories</span></span>|<span data-ttu-id="189c3-138">包含用來根據 wait_type 特性分組等候類型的類別。</span><span class="sxs-lookup"><span data-stu-id="189c3-138">Contains the categories used to group wait types according to wait_type characteristic.</span></span>|  
|<span data-ttu-id="189c3-139">core.wait_types</span><span class="sxs-lookup"><span data-stu-id="189c3-139">core.wait_types</span></span>|<span data-ttu-id="189c3-140">包含資料收集器所辨識的等候類型。</span><span class="sxs-lookup"><span data-stu-id="189c3-140">Contains the wait types recognized by the data collector.</span></span>|  
|<span data-ttu-id="189c3-141">core.purge_info_internal</span><span class="sxs-lookup"><span data-stu-id="189c3-141">core.purge_info_internal</span></span>|<span data-ttu-id="189c3-142">表示已經發出要求來停止從管理資料倉儲中移除資料的作業。</span><span class="sxs-lookup"><span data-stu-id="189c3-142">Indicates that a request has been made to stop the removal of data from the management data warehouse.</span></span>|  
  
 <span data-ttu-id="189c3-143">以上資料表會搭配收集器型別資料表一起使用，以便儲存資訊。</span><span class="sxs-lookup"><span data-stu-id="189c3-143">The preceding tables are used with collector type tables to store information.</span></span> <span data-ttu-id="189c3-144">例如，一般 SQL 追蹤收集器型別會使用以下資料表來儲存追蹤資料：</span><span class="sxs-lookup"><span data-stu-id="189c3-144">For example, the Generic SQL Trace collector type uses the following tables to store trace data:</span></span>  
  
-   <span data-ttu-id="189c3-145">core.source_info_internal</span><span class="sxs-lookup"><span data-stu-id="189c3-145">core.source_info_internal</span></span>  
  
-   <span data-ttu-id="189c3-146">core.snapshots_internal</span><span class="sxs-lookup"><span data-stu-id="189c3-146">core.snapshots_internal</span></span>  
  
-   <span data-ttu-id="189c3-147">snapshots.trace_info</span><span class="sxs-lookup"><span data-stu-id="189c3-147">snapshots.trace_info</span></span>  
  
-   <span data-ttu-id="189c3-148">snapshots.trace_data</span><span class="sxs-lookup"><span data-stu-id="189c3-148">snapshots.trace_data</span></span>  
  
###### <a name="snapshots-schema"></a><span data-ttu-id="189c3-149">快照集結構描述</span><span class="sxs-lookup"><span data-stu-id="189c3-149">Snapshots schema</span></span>  
 <span data-ttu-id="189c3-150">快照集結構描述會描述用來儲存及維護資料所需的物件 (這些資料是由提供的收集器型別所收集而來)。</span><span class="sxs-lookup"><span data-stu-id="189c3-150">The snapshots schema describes the objects needed to store and maintain the data collected by the collector types that are provided.</span></span> <span data-ttu-id="189c3-151">此結構描述中的資料表是固定的，在收集器型別的存留期間不需要變更。</span><span class="sxs-lookup"><span data-stu-id="189c3-151">The tables in this schema are fixed and do not need to be changed during the lifetime of the collector type.</span></span> <span data-ttu-id="189c3-152">如果需要變更，只有 mdw_admin 角色的成員才可以變更此結構描述。</span><span class="sxs-lookup"><span data-stu-id="189c3-152">If changes are needed, the schema can only be changed by members of the mdw_admin role.</span></span> <span data-ttu-id="189c3-153">建立這些資料表是為了儲存系統資料收集組所收集的資料。</span><span class="sxs-lookup"><span data-stu-id="189c3-153">These tables are created to store the data collected by the System Data collection sets.</span></span>  
  
 <span data-ttu-id="189c3-154">下表說明伺服器活動和查詢統計資料收集組所需的管理資料倉儲結構描述部分。</span><span class="sxs-lookup"><span data-stu-id="189c3-154">The following tables illustrate a portion of the management data warehouse schema that is required for the Server Activity and Query Statistics collection sets.</span></span>  
  
-   <span data-ttu-id="189c3-155">系統層級的資源資料表</span><span class="sxs-lookup"><span data-stu-id="189c3-155">System-level resource tables</span></span>  
  
    -   <span data-ttu-id="189c3-156">**snapshots.os_wait_stats**</span><span class="sxs-lookup"><span data-stu-id="189c3-156">**snapshots.os_wait_stats**</span></span>  
  
    -   <span data-ttu-id="189c3-157">**snapshots.os_latch_stats**</span><span class="sxs-lookup"><span data-stu-id="189c3-157">**snapshots.os_latch_stats**</span></span>  
  
    -   <span data-ttu-id="189c3-158">**snapshots.os_schedulers**</span><span class="sxs-lookup"><span data-stu-id="189c3-158">**snapshots.os_schedulers**</span></span>  
  
    -   `snapshots.os_memory_clerks`  
  
    -   <span data-ttu-id="189c3-159">**snapshots.os_memory_nodes**</span><span class="sxs-lookup"><span data-stu-id="189c3-159">**snapshots.os_memory_nodes**</span></span>  
  
    -   <span data-ttu-id="189c3-160">snapshots.sql_process_and_system_memory</span><span class="sxs-lookup"><span data-stu-id="189c3-160">snapshots.sql_process_and_system_memory</span></span>  
  
-   <span data-ttu-id="189c3-161">系統活動</span><span class="sxs-lookup"><span data-stu-id="189c3-161">System activity</span></span>  
  
    -   <span data-ttu-id="189c3-162">snapshots.active_sessions_and_requests</span><span class="sxs-lookup"><span data-stu-id="189c3-162">snapshots.active_sessions_and_requests</span></span>  
  
-   <span data-ttu-id="189c3-163">查詢統計資料</span><span class="sxs-lookup"><span data-stu-id="189c3-163">Query statistics</span></span>  
  
    -   <span data-ttu-id="189c3-164">snapshots.query_stats</span><span class="sxs-lookup"><span data-stu-id="189c3-164">snapshots.query_stats</span></span>  
  
-   <span data-ttu-id="189c3-165">I/O 統計資料</span><span class="sxs-lookup"><span data-stu-id="189c3-165">I/O statistics</span></span>  
  
    -   `snapshots.io_virtual_file_stats`  
  
-   <span data-ttu-id="189c3-166">查詢文字和計畫</span><span class="sxs-lookup"><span data-stu-id="189c3-166">Query text and plan</span></span>  
  
    -   <span data-ttu-id="189c3-167">snapshots.notable_query_text</span><span class="sxs-lookup"><span data-stu-id="189c3-167">snapshots.notable_query_text</span></span>  
  
    -   <span data-ttu-id="189c3-168">snapshots.notable_query_plan</span><span class="sxs-lookup"><span data-stu-id="189c3-168">snapshots.notable_query_plan</span></span>  
  
-   <span data-ttu-id="189c3-169">正規化的查詢統計資料</span><span class="sxs-lookup"><span data-stu-id="189c3-169">Normalized query statistics</span></span>  
  
    -   <span data-ttu-id="189c3-170">snapshots.distinct_queries</span><span class="sxs-lookup"><span data-stu-id="189c3-170">snapshots.distinct_queries</span></span>  
  
    -   <span data-ttu-id="189c3-171">snapshots.distinct_query_to_handle</span><span class="sxs-lookup"><span data-stu-id="189c3-171">snapshots.distinct_query_to_handle</span></span>  
  
 <span data-ttu-id="189c3-172">**Custom_snapshots 結構描述**</span><span class="sxs-lookup"><span data-stu-id="189c3-172">**Custom_snapshots schema**</span></span>  
  
 <span data-ttu-id="189c3-173">custom_snapshots 結構描述會描述當使用標準或協力廠商收集器型別來建立使用者定義的收集組時，所建立的新資料表和檢視表。</span><span class="sxs-lookup"><span data-stu-id="189c3-173">The custom_snapshots schema describes new tables and views that are created when standard or third-party collector types are used to create user-defined collection sets.</span></span> <span data-ttu-id="189c3-174">任何需要收集項之新資料表的收集器型別都可以在這個結構描述中建立該資料表。</span><span class="sxs-lookup"><span data-stu-id="189c3-174">Any collector type that requires a new data table for a collection item can create that table in this schema.</span></span> <span data-ttu-id="189c3-175">mdw_writer 角色的成員可以在這個結構描述中加入新的資料表。</span><span class="sxs-lookup"><span data-stu-id="189c3-175">New tables can be added in this schema by members of the mdw_writer role.</span></span> <span data-ttu-id="189c3-176">只有 mdw_admin 角色的成員才可以對此結構描述進行其他任何變更。</span><span class="sxs-lookup"><span data-stu-id="189c3-176">Any other changes to the schema can only be made by members of the mdw_admin role.</span></span>  
  
 <span data-ttu-id="189c3-177">如果要取得資料庫資料表資料行的詳細資料類型和內容資訊，請讀取每一個資料表適合之資料收集器預存程序的文件集。</span><span class="sxs-lookup"><span data-stu-id="189c3-177">You can get detailed data type and content information for the database table columns by reading the documentation for the appropriate data collector stored procedure for each of the tables.</span></span>  
  
### <a name="best-practices"></a><span data-ttu-id="189c3-178">最佳做法</span><span class="sxs-lookup"><span data-stu-id="189c3-178">Best Practices</span></span>  
 <span data-ttu-id="189c3-179">當使用管理資料倉儲時，我們建議您遵循以下最佳作法：</span><span class="sxs-lookup"><span data-stu-id="189c3-179">When working with the management data warehouse, we recommend following these best practices:</span></span>  
  
-   <span data-ttu-id="189c3-180">請勿修改管理資料倉儲資料表的中繼資料，除非您要加入新的收集器型別。</span><span class="sxs-lookup"><span data-stu-id="189c3-180">Do not modify the metadata of management data warehouse tables unless you are adding a new collector type.</span></span>  
  
-   <span data-ttu-id="189c3-181">請勿在管理資料倉儲中直接修改資料。</span><span class="sxs-lookup"><span data-stu-id="189c3-181">Do not directly modify the data in the management data warehouse.</span></span> <span data-ttu-id="189c3-182">變更您收集的資料會讓收集的資料變成無效。</span><span class="sxs-lookup"><span data-stu-id="189c3-182">Changing the data that you have collected invalidates the legitimacy of the collected data.</span></span>  
  
-   <span data-ttu-id="189c3-183">請勿直接使用資料表，而是要使用資料收集器所提供之記載的預存程序和函數，以存取執行個體和應用程式資料。</span><span class="sxs-lookup"><span data-stu-id="189c3-183">Instead of directly using the tables, use the documented stored procedures and functions that are provided with the data collector to access instance and application data.</span></span> <span data-ttu-id="189c3-184">資料表名稱和定義可以變更，在您更新應用程式時也確實會變更，也可能在未來版本中變更。</span><span class="sxs-lookup"><span data-stu-id="189c3-184">The table names and definitions can change, do change when you update the application, and might change in future releases.</span></span>  
  
## <a name="change-history"></a><span data-ttu-id="189c3-185">變更記錄</span><span class="sxs-lookup"><span data-stu-id="189c3-185">Change History</span></span>  
  
|<span data-ttu-id="189c3-186">更新的內容</span><span class="sxs-lookup"><span data-stu-id="189c3-186">Updated content</span></span>|  
|---------------------|  
|<span data-ttu-id="189c3-187">在「核心結構描述」一節中，新增 core.performance_counter_report_group_items 資料表。</span><span class="sxs-lookup"><span data-stu-id="189c3-187">Added the core.performance_counter_report_group_items table to the "Core schema" section.</span></span>|  
|<span data-ttu-id="189c3-188">在「快照集結構描述」一節中，更新資料表的清單。</span><span class="sxs-lookup"><span data-stu-id="189c3-188">Updated the list of tables in the "Snapshots schema" section.</span></span> <span data-ttu-id="189c3-189">新增 snapshots.os_memory_clerks、snapshots.sql_process_and_system_memory 和 snapshots.io_virtual_file_stats。</span><span class="sxs-lookup"><span data-stu-id="189c3-189">Added snapshots.os_memory_clerks,snapshots.sql_process_and_system_memory, and snapshots.io_virtual_file_stats.</span></span> <span data-ttu-id="189c3-190">移除 snapshots.os_process_memory 和 snapshots.distinct_query_stats。</span><span class="sxs-lookup"><span data-stu-id="189c3-190">Removedsnapshots.os_process_memory and snapshots.distinct_query_stats.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="189c3-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="189c3-191">See Also</span></span>  
 <span data-ttu-id="189c3-192">[管理資料倉儲預存程序 &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/management-data-warehouse-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="189c3-192">[Management Data Warehouse Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/management-data-warehouse-stored-procedures-transact-sql) </span></span>  
 <span data-ttu-id="189c3-193">[資料收集器預存程序 &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="189c3-193">[Data Collector Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql) </span></span>  
 <span data-ttu-id="189c3-194">[資料收集](data-collection.md) </span><span class="sxs-lookup"><span data-stu-id="189c3-194">[Data Collection](data-collection.md) </span></span>  
 [<span data-ttu-id="189c3-195">檢視收集組報表 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="189c3-195">View a Collection Set Report &#40;SQL Server Management Studio&#41;</span></span>](view-a-collection-set-report-sql-server-management-studio.md)  
  
  
