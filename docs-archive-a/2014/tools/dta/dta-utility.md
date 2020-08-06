---
title: dta 公用程式 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- physical design structures [SQL Server]
- command prompt utilities [SQL Server], dta
- dta utility
- tuning databases [SQL Server], Database Engine Tuning Advisor
- workloads [SQL Server], analyzing
- dta utility, about dta utility
- performance [SQL Server], Database Engine Tuning Advisor
- Database Engine Tuning Advisor [SQL Server], command prompt
- optimizing databases [SQL Server]
ms.assetid: a0b210ce-9b58-4709-80cb-9363b68a1f5a
author: stevestein
ms.author: sstein
ms.openlocfilehash: f9cd5a904993f1044c1cbeff8e1cdfc07332da64
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707985"
---
# <a name="dta-utility"></a><span data-ttu-id="41260-102">dta 公用程式</span><span class="sxs-lookup"><span data-stu-id="41260-102">dta Utility</span></span>
  <span data-ttu-id="41260-103">**dta** 公用程式是 Database Engine Tuning Advisor 的命令提示字元版本。</span><span class="sxs-lookup"><span data-stu-id="41260-103">The **dta** utility is the command prompt version of Database Engine Tuning Advisor.</span></span> <span data-ttu-id="41260-104">**dta** 公用程式的設計，是為了讓您在應用程式和指令碼中使用 Database Engine Tuning Advisor 功能。</span><span class="sxs-lookup"><span data-stu-id="41260-104">The **dta** utility is designed to allow you to use Database Engine Tuning Advisor functionality in applications and scripts.</span></span>  
  
 <span data-ttu-id="41260-105">如同 Database Engine Tuning Advisor， **dta** 公用程式也會分析工作負載，並提供實體設計結構的建議，以增進該工作負載的伺服器效能。</span><span class="sxs-lookup"><span data-stu-id="41260-105">Like Database Engine Tuning Advisor, the **dta** utility analyzes a workload and recommends physical design structures to improve server performance for that workload.</span></span> <span data-ttu-id="41260-106">工作負載可能是計畫快取、 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] 追蹤檔或資料表，也可能是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼。</span><span class="sxs-lookup"><span data-stu-id="41260-106">The workload can be a plan cache, a [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] trace file or table, or a [!INCLUDE[tsql](../../includes/tsql-md.md)] script.</span></span> <span data-ttu-id="41260-107">實體設計結構包括索引、索引檢視表及資料分割。</span><span class="sxs-lookup"><span data-stu-id="41260-107">Physical design structures include indexes, indexed views, and partitioning.</span></span> <span data-ttu-id="41260-108">分析工作負載之後， **dta** 公用程式會產生資料庫實體設計的建議，且能夠產生必要的指令碼來實作建議。</span><span class="sxs-lookup"><span data-stu-id="41260-108">After analyzing a workload, the **dta** utility produces a recommendation for the physical design of databases and can generate the necessary script to implement the recommendation.</span></span> <span data-ttu-id="41260-109">您可以從命令提示字元，搭配 **-if** 或 **-it** 引數來指定工作負載。</span><span class="sxs-lookup"><span data-stu-id="41260-109">Workloads can be specified from the command prompt with the **-if** or the **-it** argument.</span></span> <span data-ttu-id="41260-110">您也可以從命令提示字元，搭配 **-ix** 引數來指定 XML 輸入檔。</span><span class="sxs-lookup"><span data-stu-id="41260-110">You can also specify an XML input file from the command prompt with the **-ix** argument.</span></span> <span data-ttu-id="41260-111">在這個情況之下，工作負載指定在 XML 輸入檔中。</span><span class="sxs-lookup"><span data-stu-id="41260-111">In that case, the workload is specified in the XML input file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41260-112">語法</span><span class="sxs-lookup"><span data-stu-id="41260-112">Syntax</span></span>  
  
```  
  
      dta  
[ -? ] |  
[  
      [ -S server_name[ \instance ] ]  
      { { -U login_id [-P password ] } | -E  }  
      { -D database_name [ ,...n ] }  
      [ -ddatabase_name ]   
      [ -Tltable_list | -Tf table_list_file ]  
      { -if workload_file | -it workload_trace_table_name  |   
        -ip | -ipf }  
      { -ssession_name | -IDsession_ID }  
      [ -F ]  
      [ -of output_script_file_name ]  
      [ -oroutput_xml_report_file_name ]  
      [ -ox output_XML_file_name ]  
      [ -rl analysis_report_list [ ,...n ] ]  
      [ -ix input_XML_file_name ]  
      [ -A time_for_tuning_in_minutes ]  
      [ -nnumber_of_events ]  
      [ -m minimum_improvement ]  
      [ -fa physical_design_structures_to_add ]  
      [ -fi ]  
      [ -fppartitioning_strategy ]  
      [ -fk keep_existing_option ]  
      [ -fxdrop_only_mode ]  
      [ -B storage_size ]  
      [ -cmax_key_columns_in_index ]  
      [ -C max_columns_in_index ]  
      [ -e | -e tuning_log_name ]  
      [ -N online_option]  
      [ -q ]  
      [ -u ]  
      [ -x ]  
      [ -a ]  
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="41260-113">引數</span><span class="sxs-lookup"><span data-stu-id="41260-113">Arguments</span></span>  
 <span data-ttu-id="41260-114">**-?**</span><span class="sxs-lookup"><span data-stu-id="41260-114">**-?**</span></span>  
 <span data-ttu-id="41260-115">顯示使用資訊。</span><span class="sxs-lookup"><span data-stu-id="41260-115">Displays usage information.</span></span>  
  
 <span data-ttu-id="41260-116">**-A** _time_for_tuning_in_minutes_</span><span class="sxs-lookup"><span data-stu-id="41260-116">**-A** _time_for_tuning_in_minutes_</span></span>  
 <span data-ttu-id="41260-117">指定微調時間限制 (以分鐘為單位)。</span><span class="sxs-lookup"><span data-stu-id="41260-117">Specifies the tuning time limit in minutes.</span></span> <span data-ttu-id="41260-118">**dta** 會利用指定的時間量來微調工作負載，以及產生含有建議的實體設計變更的指令碼。</span><span class="sxs-lookup"><span data-stu-id="41260-118">**dta** uses the specified amount of time to tune the workload and generate a script with the recommended physical design changes.</span></span> <span data-ttu-id="41260-119">依預設， **dta** 假設微調時間是 8 小時。</span><span class="sxs-lookup"><span data-stu-id="41260-119">By default **dta** assumes a tuning time of 8 hours.</span></span> <span data-ttu-id="41260-120">指定 0 代表微調時間無限制。</span><span class="sxs-lookup"><span data-stu-id="41260-120">Specifying 0allows unlimited tuning time.</span></span> <span data-ttu-id="41260-121">**dta** 可能會在時間限制過期之前，完成整個工作負載的微調。</span><span class="sxs-lookup"><span data-stu-id="41260-121">**dta** might finish tuning the entire workload before the time limit expires.</span></span> <span data-ttu-id="41260-122">不過，為了確保整個工作負載都能得到微調，我們建議您指定無限的微調時間 (-A 0)。</span><span class="sxs-lookup"><span data-stu-id="41260-122">However, to make sure that the entire workload is tuned, we recommend that you specify unlimited tuning time (-A 0).</span></span>  
  
 <span data-ttu-id="41260-123">**-a**</span><span class="sxs-lookup"><span data-stu-id="41260-123">**-a**</span></span>  
 <span data-ttu-id="41260-124">不發出提示，直接微調工作負載並套用建議的內容。</span><span class="sxs-lookup"><span data-stu-id="41260-124">Tunes workload and applies the recommendation without prompting you.</span></span>  
  
 <span data-ttu-id="41260-125">**-B** _storage_size_</span><span class="sxs-lookup"><span data-stu-id="41260-125">**-B** _storage_size_</span></span>  
 <span data-ttu-id="41260-126">指定建議的索引和資料分割所能使用的最大空間 (以 MB 為單位)。</span><span class="sxs-lookup"><span data-stu-id="41260-126">Specifies the maximum space in megabytes that can be consumed by the recommended index and partitioning.</span></span> <span data-ttu-id="41260-127">微調多個資料庫時，所有資料庫的建議內容都考量了空間的計算。</span><span class="sxs-lookup"><span data-stu-id="41260-127">When multiple databases are tuned, recommendations for all databases are considered for the space calculation.</span></span> <span data-ttu-id="41260-128">依預設， **dta** 會採用下列較小的儲存體大小：</span><span class="sxs-lookup"><span data-stu-id="41260-128">By default, **dta** assumes the smaller of the following storage sizes:</span></span>  
  
-   <span data-ttu-id="41260-129">目前的原始資料大小的三倍，其中包括資料庫中各資料表的堆積和叢集索引的總大小。</span><span class="sxs-lookup"><span data-stu-id="41260-129">Three times the current raw data size, which includes the total size of heaps and clustered indexes on tables in the database.</span></span>  
  
-   <span data-ttu-id="41260-130">所有相連硬碟的可用空間，加上原始資料大小。</span><span class="sxs-lookup"><span data-stu-id="41260-130">The free space on all attached disk drives plus the raw data size.</span></span>  
  
 <span data-ttu-id="41260-131">預設儲存體大小不包括非叢集索引和索引檢視。</span><span class="sxs-lookup"><span data-stu-id="41260-131">The default storage size does not include nonclustered indexes and indexed views.</span></span>  
  
 <span data-ttu-id="41260-132">**-C** _max_columns_in_index_</span><span class="sxs-lookup"><span data-stu-id="41260-132">**-C** _max_columns_in_index_</span></span>  
 <span data-ttu-id="41260-133">指定 **dta** 所提出之索引內的資料行數目上限。</span><span class="sxs-lookup"><span data-stu-id="41260-133">Specifies the maximum number of columns in indexes that **dta** proposes.</span></span> <span data-ttu-id="41260-134">最大值為 1024。</span><span class="sxs-lookup"><span data-stu-id="41260-134">The maximum value  is 1024.</span></span> <span data-ttu-id="41260-135">依預設，引數設定為 16。</span><span class="sxs-lookup"><span data-stu-id="41260-135">By default, this argument is set to 16.</span></span>  
  
 <span data-ttu-id="41260-136">**-c** _max_key_columns_in_index_</span><span class="sxs-lookup"><span data-stu-id="41260-136">**-c** _max_key_columns_in_index_</span></span>  
 <span data-ttu-id="41260-137">指定 **dta** 所提出之索引內索引鍵資料行數目上限。</span><span class="sxs-lookup"><span data-stu-id="41260-137">Specifies the maximum number of key columns in indexes that **dta** proposes.</span></span> <span data-ttu-id="41260-138">預設值是 16，這是允許的最大值。</span><span class="sxs-lookup"><span data-stu-id="41260-138">The default value is 16, the maximum value allowed.</span></span> <span data-ttu-id="41260-139">**dta** 也會考慮使用內含資料行建立索引。</span><span class="sxs-lookup"><span data-stu-id="41260-139">**dta** also considers creating indexes with included columns.</span></span> <span data-ttu-id="41260-140">內含資料行的索引建議可能超出這個引數所指定的資料行數目。</span><span class="sxs-lookup"><span data-stu-id="41260-140">Indexes recommended with included columns may exceed the number of columns specified in this argument.</span></span>  
  
 <span data-ttu-id="41260-141">**-D** _database_name_</span><span class="sxs-lookup"><span data-stu-id="41260-141">**-D** _database_name_</span></span>  
 <span data-ttu-id="41260-142">指定要微調的每個資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="41260-142">Specifies the name of each database that is to be tuned.</span></span> <span data-ttu-id="41260-143">第一個資料庫是預設資料庫。</span><span class="sxs-lookup"><span data-stu-id="41260-143">The first database is the default database.</span></span> <span data-ttu-id="41260-144">您可以指定多個資料庫，以逗號分隔各個資料庫名稱，例如：</span><span class="sxs-lookup"><span data-stu-id="41260-144">You can specify multiple databases by separating the database names with commas, for example:</span></span>  
  
```  
dta -D database_name1, database_name2...  
```  
  
 <span data-ttu-id="41260-145">另外，您也可以在各個資料庫名稱上使用 **-D** 引數來指定多個資料庫，例如：</span><span class="sxs-lookup"><span data-stu-id="41260-145">Alternatively, you can specify multiple databases by using the **-D** argument for each database name, for example:</span></span>  
  
```  
dta -D database_name1 -D database_name2... n  
```  
  
 <span data-ttu-id="41260-146">**-D** 引數是必要項目。</span><span class="sxs-lookup"><span data-stu-id="41260-146">The **-D** argument is mandatory.</span></span> <span data-ttu-id="41260-147">如果未指定 **-d** 引數， **dta** 一開始會連接到工作負載中第一個 `USE database_name` 子句所指定的資料庫。</span><span class="sxs-lookup"><span data-stu-id="41260-147">If the **-d** argument has not been specified, **dta** initially connects to the database that is specified with the first `USE database_name` clause in the workload.</span></span> <span data-ttu-id="41260-148">如果工作負載中沒有明確的 `USE database_name` 子句，您就必須使用 **-d** 引數。</span><span class="sxs-lookup"><span data-stu-id="41260-148">If there is not explicit `USE database_name` clause in the workload, you must use the **-d** argument.</span></span>  
  
 <span data-ttu-id="41260-149">例如，如果您的工作負載沒有包含明確的 `USE database_name` 子句，而且您使用下列 **dta** 命令，就不會產生任何建議：</span><span class="sxs-lookup"><span data-stu-id="41260-149">For example, if you have a workload that contains no explicit `USE database_name` clause, and you use the following **dta** command, a recommendation will not be generated:</span></span>  
  
```  
dta -D db_name1, db_name2...  
```  
  
 <span data-ttu-id="41260-150">但是，如果您使用相同的工作負載，而且利用下列使用 **-d** 引數的 **dta** 命令，就會產生建議：</span><span class="sxs-lookup"><span data-stu-id="41260-150">But if you use the same workload, and use the following **dta** command that uses the **-d** argument, a recommendation will be generated:</span></span>  
  
```  
dta -D db_name1, db_name2 -d db_name1  
```  
  
 <span data-ttu-id="41260-151">**-d** _database_name_</span><span class="sxs-lookup"><span data-stu-id="41260-151">**-d** _database_name_</span></span>  
 <span data-ttu-id="41260-152">指定微調工作負載時， **dta** 所連接的第一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="41260-152">Specifies the first database to which **dta** connects when tuning a workload.</span></span> <span data-ttu-id="41260-153">這個引數只能指定一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="41260-153">Only one database can be specified for this argument.</span></span> <span data-ttu-id="41260-154">例如：</span><span class="sxs-lookup"><span data-stu-id="41260-154">For example:</span></span>  
  
```  
dta -d AdventureWorks2012 ...  
```  
  
 <span data-ttu-id="41260-155">如果指定了多個資料庫名稱， **dta** 就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="41260-155">If multiple database names are specified, then **dta** returns an error.</span></span> <span data-ttu-id="41260-156">**-d** 引數是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="41260-156">The **-d** argument is optional.</span></span>  
  
 <span data-ttu-id="41260-157">如果您使用 XML 輸入檔，您可以使用位於專案底下的專案，指定**dta**所連接的第一個資料庫 `DatabaseToConnect` `TuningOptions` 。</span><span class="sxs-lookup"><span data-stu-id="41260-157">If you are using an XML input file, you can specify the first database to which **dta** connects by using the `DatabaseToConnect` element that is located under the `TuningOptions` element.</span></span> <span data-ttu-id="41260-158">如需詳細資訊，請參閱 [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md)。</span><span class="sxs-lookup"><span data-stu-id="41260-158">For more information, see [Database Engine Tuning Advisor](../../relational-databases/performance/database-engine-tuning-advisor.md).</span></span>  
  
 <span data-ttu-id="41260-159">如果您只微調一個資料庫， **-d** 引數會提供類似 **sqlcmd** 公用程式中 **-d** 引數的功能，但它不會執行 USE *database_name* 陳述式。</span><span class="sxs-lookup"><span data-stu-id="41260-159">If you are tuning only one database, the **-d** argument provides functionality that is similar to the **-d** argument in the **sqlcmd** utility, but it does not execute the USE *database_name* statement.</span></span> <span data-ttu-id="41260-160">如需詳細資訊，請參閱 [sqlcmd Utility](../sqlcmd-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="41260-160">For more information, see [sqlcmd Utility](../sqlcmd-utility.md).</span></span>  
  
 <span data-ttu-id="41260-161">**-E**</span><span class="sxs-lookup"><span data-stu-id="41260-161">**-E**</span></span>  
 <span data-ttu-id="41260-162">使用信任連接，不要求密碼。</span><span class="sxs-lookup"><span data-stu-id="41260-162">Uses a trusted connection instead of requesting a password.</span></span> <span data-ttu-id="41260-163">必須使用指定登入識別碼的 **-E** 引數或 **-U** 引數。</span><span class="sxs-lookup"><span data-stu-id="41260-163">Either the **-E** argument or the **-U** argument, which specifies a login ID, must be used.</span></span>  
  
 <span data-ttu-id="41260-164">**-e** _tuning_log_name_</span><span class="sxs-lookup"><span data-stu-id="41260-164">**-e** _tuning_log_name_</span></span>  
 <span data-ttu-id="41260-165">指定 **dta** 用來記錄它無法微調之事件的資料表或檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="41260-165">Specifies the name of the table or file where **dta** records events that it could not tune.</span></span> <span data-ttu-id="41260-166">資料表會建立在執行微調的伺服器中。</span><span class="sxs-lookup"><span data-stu-id="41260-166">The table is created on the server where the tuning is performed.</span></span>  
  
 <span data-ttu-id="41260-167">如果使用某份資料表，請依照下列格式來指定它的名稱： *[database_name].[owner_name].table_name*。</span><span class="sxs-lookup"><span data-stu-id="41260-167">If a table is used, specify its name in the format: *[database_name].[owner_name].table_name*.</span></span> <span data-ttu-id="41260-168">下表顯示各個參數的預設值：</span><span class="sxs-lookup"><span data-stu-id="41260-168">The following table shows the default values for each parameter:</span></span>  
  
|<span data-ttu-id="41260-169">參數</span><span class="sxs-lookup"><span data-stu-id="41260-169">Parameter</span></span>|<span data-ttu-id="41260-170">預設值</span><span class="sxs-lookup"><span data-stu-id="41260-170">Default value</span></span>|  
|---------------|-------------------|  
|<span data-ttu-id="41260-171">*database_name*</span><span class="sxs-lookup"><span data-stu-id="41260-171">*database_name*</span></span>|<span data-ttu-id="41260-172">使用 **-D** 選項指定的 *database_name*</span><span class="sxs-lookup"><span data-stu-id="41260-172">*database_name* specified with the **-D** option</span></span>|  
|<span data-ttu-id="41260-173">*owner_name*</span><span class="sxs-lookup"><span data-stu-id="41260-173">*owner_name*</span></span>|<span data-ttu-id="41260-174">**dbo**</span><span class="sxs-lookup"><span data-stu-id="41260-174">**dbo**</span></span><br /><br /> <span data-ttu-id="41260-175">注意： *owner_name*必須是**dbo**。</span><span class="sxs-lookup"><span data-stu-id="41260-175">Note: *owner_name* must be **dbo**.</span></span> <span data-ttu-id="41260-176">如果指定了任何其他值， **dta** 的執行便會失敗並傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="41260-176">If any other value is specified, then **dta** execution fails and it returns an error.</span></span>|  
|<span data-ttu-id="41260-177">*table_name*</span><span class="sxs-lookup"><span data-stu-id="41260-177">*table_name*</span></span>|<span data-ttu-id="41260-178">None</span><span class="sxs-lookup"><span data-stu-id="41260-178">None</span></span>|  
  
 <span data-ttu-id="41260-179">如果使用檔案，請指定 .xml 副檔名。</span><span class="sxs-lookup"><span data-stu-id="41260-179">If a file is used, specify .xml as its extension.</span></span> <span data-ttu-id="41260-180">例如，TuningLog.xml。</span><span class="sxs-lookup"><span data-stu-id="41260-180">For example, TuningLog.xml.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="41260-181">如果工作階段遭到刪除， **dta** 公用程式就不會刪除使用者指定之微調記錄資料表的內容。</span><span class="sxs-lookup"><span data-stu-id="41260-181">The **dta** utility does not delete the contents of user-specified tuning log tables if the session is deleted.</span></span> <span data-ttu-id="41260-182">在微調超大型工作負載時，我們建議您對微調記錄指定資料表。</span><span class="sxs-lookup"><span data-stu-id="41260-182">When tuning very large workloads, we recommend that a table be specified for the tuning log.</span></span> <span data-ttu-id="41260-183">由於微調大型工作負載會產生大量微調記錄，因此，在使用資料表時可以更快刪除工作階段。</span><span class="sxs-lookup"><span data-stu-id="41260-183">Since tuning large workloads can result in large tuning logs, the sessions can be deleted much faster when a table is used.</span></span>  
  
 <span data-ttu-id="41260-184">**-F**</span><span class="sxs-lookup"><span data-stu-id="41260-184">**-F**</span></span>  
 <span data-ttu-id="41260-185">允許 **dta** 覆寫現有的輸出檔。</span><span class="sxs-lookup"><span data-stu-id="41260-185">Permits **dta** to overwrite an existing output file.</span></span> <span data-ttu-id="41260-186">如果已存在相同名稱的輸出檔，且未指定 **-F** ， **dta**就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="41260-186">If an output file with the same name already exists and **-F** is not specified, **dta**returns an error.</span></span> <span data-ttu-id="41260-187">您可以使用 **-F** 搭配 **-of**、 **-or**或 **-ox**。</span><span class="sxs-lookup"><span data-stu-id="41260-187">You can use **-F** with **-of**, **-or**, or **-ox**.</span></span>  
  
 <span data-ttu-id="41260-188">**-fa** _physical_design_structures_to_add_</span><span class="sxs-lookup"><span data-stu-id="41260-188">**-fa** _physical_design_structures_to_add_</span></span>  
 <span data-ttu-id="41260-189">指定 **dta** 應該在建議中包含的實體設計結構類型。</span><span class="sxs-lookup"><span data-stu-id="41260-189">Specifies what types of physical design structures **dta** should include in the recommendation.</span></span> <span data-ttu-id="41260-190">下表列出並說明這個引數所能指定的值。</span><span class="sxs-lookup"><span data-stu-id="41260-190">The following table lists and describes the values that can be specified for this argument.</span></span> <span data-ttu-id="41260-191">若未指定任何值， **dta**就會使用預設的 **-fa** `IDX` 。</span><span class="sxs-lookup"><span data-stu-id="41260-191">When no value is specified, **dta** uses the default **-fa**`IDX`.</span></span>  
  
|<span data-ttu-id="41260-192">值</span><span class="sxs-lookup"><span data-stu-id="41260-192">Value</span></span>|<span data-ttu-id="41260-193">描述</span><span class="sxs-lookup"><span data-stu-id="41260-193">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="41260-194">IDX_IV</span><span class="sxs-lookup"><span data-stu-id="41260-194">IDX_IV</span></span>|<span data-ttu-id="41260-195">索引和索引檢視表。</span><span class="sxs-lookup"><span data-stu-id="41260-195">Indexes and indexed views.</span></span>|  
|<span data-ttu-id="41260-196">IDX</span><span class="sxs-lookup"><span data-stu-id="41260-196">IDX</span></span>|<span data-ttu-id="41260-197">只有索引。</span><span class="sxs-lookup"><span data-stu-id="41260-197">Indexes only.</span></span>|  
|<span data-ttu-id="41260-198">IV</span><span class="sxs-lookup"><span data-stu-id="41260-198">IV</span></span>|<span data-ttu-id="41260-199">只有索引檢視表。</span><span class="sxs-lookup"><span data-stu-id="41260-199">Indexed views only.</span></span>|  
|<span data-ttu-id="41260-200">NCL_IDX</span><span class="sxs-lookup"><span data-stu-id="41260-200">NCL_IDX</span></span>|<span data-ttu-id="41260-201">只有非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="41260-201">Nonclustered indexes only.</span></span>|  
  
 <span data-ttu-id="41260-202">**-fi**</span><span class="sxs-lookup"><span data-stu-id="41260-202">**-fi**</span></span>  
 <span data-ttu-id="41260-203">指定應為新建議考量篩選的索引。</span><span class="sxs-lookup"><span data-stu-id="41260-203">Specifies that filtered indexes be considered for new recommendations.</span></span> <span data-ttu-id="41260-204">如需詳細資訊，請參閱 [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md)。</span><span class="sxs-lookup"><span data-stu-id="41260-204">For more information, see [Create Filtered Indexes](../../relational-databases/indexes/create-filtered-indexes.md).</span></span>  
  
 <span data-ttu-id="41260-205">**-fk** _keep_existing_option_</span><span class="sxs-lookup"><span data-stu-id="41260-205">**-fk** _keep_existing_option_</span></span>  
 <span data-ttu-id="41260-206">指定 **dta** 在產生建議時，必須保留的現有實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="41260-206">Specifies what existing physical design structures **dta** must retain when generating its recommendation.</span></span> <span data-ttu-id="41260-207">下表列出並說明這個引數所能指定的值：</span><span class="sxs-lookup"><span data-stu-id="41260-207">The following table lists and describes the values that can be specified for this argument:</span></span>  
  
|<span data-ttu-id="41260-208">值</span><span class="sxs-lookup"><span data-stu-id="41260-208">Value</span></span>|<span data-ttu-id="41260-209">描述</span><span class="sxs-lookup"><span data-stu-id="41260-209">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="41260-210">無</span><span class="sxs-lookup"><span data-stu-id="41260-210">NONE</span></span>|<span data-ttu-id="41260-211">無現有結構。</span><span class="sxs-lookup"><span data-stu-id="41260-211">No existing structures</span></span>|  
|<span data-ttu-id="41260-212">ALL</span><span class="sxs-lookup"><span data-stu-id="41260-212">ALL</span></span>|<span data-ttu-id="41260-213">所有現有結構。</span><span class="sxs-lookup"><span data-stu-id="41260-213">All existing structures</span></span>|  
|<span data-ttu-id="41260-214">ALIGNED</span><span class="sxs-lookup"><span data-stu-id="41260-214">ALIGNED</span></span>|<span data-ttu-id="41260-215">所有資料分割對齊結構。</span><span class="sxs-lookup"><span data-stu-id="41260-215">All partition-aligned structures.</span></span>|  
|<span data-ttu-id="41260-216">CL_IDX</span><span class="sxs-lookup"><span data-stu-id="41260-216">CL_IDX</span></span>|<span data-ttu-id="41260-217">資料表的所有叢集索引。</span><span class="sxs-lookup"><span data-stu-id="41260-217">All clustered indexes on tables</span></span>|  
|<span data-ttu-id="41260-218">IDX</span><span class="sxs-lookup"><span data-stu-id="41260-218">IDX</span></span>|<span data-ttu-id="41260-219">資料表的所有叢集和非叢集索引。</span><span class="sxs-lookup"><span data-stu-id="41260-219">All clustered and nonclustered indexes on tables</span></span>|  
  
 <span data-ttu-id="41260-220">**-fp** _partitioning_strategy_</span><span class="sxs-lookup"><span data-stu-id="41260-220">**-fp** _partitioning_strategy_</span></span>  
 <span data-ttu-id="41260-221">指定是否應該分割 **dta** 所提出的新實體設計結構 (索引和索引檢視表) 及其分割方式。</span><span class="sxs-lookup"><span data-stu-id="41260-221">Specifies whether new physical design structures (indexes and indexed views) that **dta** proposes should be partitioned, and how they should be partitioned.</span></span> <span data-ttu-id="41260-222">下表列出並說明這個引數所能指定的值：</span><span class="sxs-lookup"><span data-stu-id="41260-222">The following table lists and describes the values that can be specified for this argument:</span></span>  
  
|<span data-ttu-id="41260-223">值</span><span class="sxs-lookup"><span data-stu-id="41260-223">Value</span></span>|<span data-ttu-id="41260-224">描述</span><span class="sxs-lookup"><span data-stu-id="41260-224">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="41260-225">無</span><span class="sxs-lookup"><span data-stu-id="41260-225">NONE</span></span>|<span data-ttu-id="41260-226">沒有資料分割。</span><span class="sxs-lookup"><span data-stu-id="41260-226">No partitioning</span></span>|  
|<span data-ttu-id="41260-227">FULL</span><span class="sxs-lookup"><span data-stu-id="41260-227">FULL</span></span>|<span data-ttu-id="41260-228">完整的資料分割 (選擇這個項目，可以增進效能)。</span><span class="sxs-lookup"><span data-stu-id="41260-228">Full partitioning (choose to enhance performance)</span></span>|  
|<span data-ttu-id="41260-229">ALIGNED</span><span class="sxs-lookup"><span data-stu-id="41260-229">ALIGNED</span></span>|<span data-ttu-id="41260-230">只有對齊的資料分割 (選擇這個項目，管理會更容易)。</span><span class="sxs-lookup"><span data-stu-id="41260-230">Aligned partitioning only (choose to enhance manageability)</span></span>|  
  
 <span data-ttu-id="41260-231">ALIGNED 表示在 **dta** 所產生的建議中，每個建議的索引都會完全依照定義索引之基礎資料表的相同方式進行分割。</span><span class="sxs-lookup"><span data-stu-id="41260-231">ALIGNED means that in the recommendation generated by **dta** every proposed index is partitioned in exactly the same way as the underlying table for which the index is defined.</span></span> <span data-ttu-id="41260-232">索引檢視表中的非叢集索引會對齊索引檢視表。</span><span class="sxs-lookup"><span data-stu-id="41260-232">Nonclustered indexes on an indexed view are aligned with the indexed view.</span></span> <span data-ttu-id="41260-233">這個引數只能指定一個值。</span><span class="sxs-lookup"><span data-stu-id="41260-233">Only one value can be specified for this argument.</span></span> <span data-ttu-id="41260-234">預設值為 **-fp** `NONE` 。</span><span class="sxs-lookup"><span data-stu-id="41260-234">The default is **-fp**`NONE`.</span></span>  
  
 <span data-ttu-id="41260-235">**-fx** _drop_only_mode_</span><span class="sxs-lookup"><span data-stu-id="41260-235">**-fx** _drop_only_mode_</span></span>  
 <span data-ttu-id="41260-236">指定 **dta** 只考慮卸除現有的實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="41260-236">Specifies that **dta** only considers dropping existing physical design structures.</span></span> <span data-ttu-id="41260-237">不考慮任何新的實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="41260-237">No new physical design structures are considered.</span></span> <span data-ttu-id="41260-238">指定此選項時， **dta** 會評估現有實體設計結構的可用程度，並建議您卸除不常使用的結構。</span><span class="sxs-lookup"><span data-stu-id="41260-238">When this option is specified, **dta** evaluates the usefulness of existing physical design structures and recommends dropping seldom used structures.</span></span> <span data-ttu-id="41260-239">這個引數沒有任何值。</span><span class="sxs-lookup"><span data-stu-id="41260-239">This argument takes no values.</span></span> <span data-ttu-id="41260-240">它不能搭配 **-fa**、 **-fp**或 **-fk ALL** 等引數一起使用。</span><span class="sxs-lookup"><span data-stu-id="41260-240">It cannot be used with the **-fa**, **-fp**, or **-fk ALL** arguments</span></span>  
  
 <span data-ttu-id="41260-241">**-ID** _session_ID_</span><span class="sxs-lookup"><span data-stu-id="41260-241">**-ID** _session_ID_</span></span>  
 <span data-ttu-id="41260-242">指定微調工作階段的數值識別碼。</span><span class="sxs-lookup"><span data-stu-id="41260-242">Specifies a numerical identifier for the tuning session.</span></span> <span data-ttu-id="41260-243">若未指定，則 **dta** 會產生一個識別碼。</span><span class="sxs-lookup"><span data-stu-id="41260-243">If not specified, then **dta** generates an ID number.</span></span> <span data-ttu-id="41260-244">您可以利用這個識別碼來檢視現有微調工作階段的資訊。</span><span class="sxs-lookup"><span data-stu-id="41260-244">You can use this identifier to view information for existing tuning sessions.</span></span> <span data-ttu-id="41260-245">如果您沒有指定 **-ID**值，就必須利用 **-s**來指定工作階段名稱。</span><span class="sxs-lookup"><span data-stu-id="41260-245">If you do not specify a value for **-ID**, then a session name must be specified with **-s**.</span></span>  
  
 <span data-ttu-id="41260-246">**-ip**</span><span class="sxs-lookup"><span data-stu-id="41260-246">**-ip**</span></span>  
 <span data-ttu-id="41260-247">指定計畫快取可用做為工作負載。</span><span class="sxs-lookup"><span data-stu-id="41260-247">Specifies that the plan cache be used as the workload.</span></span> <span data-ttu-id="41260-248">針對明確選定的資料庫排名前 1000 個計畫快取事件，進行分析。</span><span class="sxs-lookup"><span data-stu-id="41260-248">The top 1,000 plan cache events for explicitly selected databases are analyzed.</span></span> <span data-ttu-id="41260-249">您可以利用 **-n** 選項變更此值。</span><span class="sxs-lookup"><span data-stu-id="41260-249">This value can be changed using the **-n** option.</span></span>  
  
 <span data-ttu-id="41260-250">**-ipf**</span><span class="sxs-lookup"><span data-stu-id="41260-250">**-ipf**</span></span>  
 <span data-ttu-id="41260-251">指定計畫快取可用做為工作負載。</span><span class="sxs-lookup"><span data-stu-id="41260-251">Specifies that the plan cache be used as the workload.</span></span> <span data-ttu-id="41260-252">針對所有資料庫排名前 1000 個計畫快取事件，進行分析。</span><span class="sxs-lookup"><span data-stu-id="41260-252">The top 1,000 plan cache events for all databases are analyzed.</span></span> <span data-ttu-id="41260-253">您可以利用 **-n** 選項變更此值。</span><span class="sxs-lookup"><span data-stu-id="41260-253">This value can be changed using the **-n** option.</span></span>  
  
 <span data-ttu-id="41260-254">**-if** _workload_file_</span><span class="sxs-lookup"><span data-stu-id="41260-254">**-if** _workload_file_</span></span>  
 <span data-ttu-id="41260-255">指定微調輸入所用的工作負載檔案之路徑與名稱。</span><span class="sxs-lookup"><span data-stu-id="41260-255">Specifies the path and name of the workload file to use as input for tuning.</span></span> <span data-ttu-id="41260-256">檔案必須是下列格式之一：.trc (SQL Server Profiler 追蹤檔)、.sql (SQL 檔) 或 .log ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 追蹤檔)。</span><span class="sxs-lookup"><span data-stu-id="41260-256">The file must be in one of these formats: .trc (SQL Server Profiler trace file), .sql (SQL file), or .log ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] trace file).</span></span> <span data-ttu-id="41260-257">您必須指定一個工作負載檔案或一份工作負載資料表。</span><span class="sxs-lookup"><span data-stu-id="41260-257">Either one workload file or one workload table must be specified.</span></span>  
  
 <span data-ttu-id="41260-258">**-it** _workload_trace_table_name_</span><span class="sxs-lookup"><span data-stu-id="41260-258">**-it** _workload_trace_table_name_</span></span>  
 <span data-ttu-id="41260-259">指定包含微調工作負載追蹤的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="41260-259">Specifies the name of a table containing the workload trace for tuning.</span></span> <span data-ttu-id="41260-260">請使用下列格式來指定名稱：[*database_name*] **.** [*owner_name*] **.** _table_name_。</span><span class="sxs-lookup"><span data-stu-id="41260-260">The name is specified in the format: [*database_name*]**.**[*owner_name*]**.**_table_name_.</span></span>  
  
 <span data-ttu-id="41260-261">下表顯示各項目的預設值：</span><span class="sxs-lookup"><span data-stu-id="41260-261">The following table shows the default values for each:</span></span>  
  
|<span data-ttu-id="41260-262">參數</span><span class="sxs-lookup"><span data-stu-id="41260-262">Parameter</span></span>|<span data-ttu-id="41260-263">預設值</span><span class="sxs-lookup"><span data-stu-id="41260-263">Default value</span></span>|  
|---------------|-------------------|  
|<span data-ttu-id="41260-264">*database_name*</span><span class="sxs-lookup"><span data-stu-id="41260-264">*database_name*</span></span>|<span data-ttu-id="41260-265">使用 **-D** 選項指定的 *database_name*。</span><span class="sxs-lookup"><span data-stu-id="41260-265">*database_name* specified with **-D** option.</span></span>|  
|<span data-ttu-id="41260-266">*owner_name*</span><span class="sxs-lookup"><span data-stu-id="41260-266">*owner_name*</span></span>|<span data-ttu-id="41260-267">**dbo**。</span><span class="sxs-lookup"><span data-stu-id="41260-267">**dbo**.</span></span>|  
|<span data-ttu-id="41260-268">*table_name*</span><span class="sxs-lookup"><span data-stu-id="41260-268">*table_name*</span></span>|<span data-ttu-id="41260-269">無。</span><span class="sxs-lookup"><span data-stu-id="41260-269">None.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="41260-270">*owner_name* 必須是 **dbo**。</span><span class="sxs-lookup"><span data-stu-id="41260-270">*owner_name* must be **dbo**.</span></span> <span data-ttu-id="41260-271">如果指定了任何其他值， **dta** 的執行便會失敗並傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="41260-271">If any other value is specified, execution of **dta** fails and an error is returned.</span></span> <span data-ttu-id="41260-272">另外，也請注意，您必須指定一份工作負載資料表，或指定一個工作負載檔案。</span><span class="sxs-lookup"><span data-stu-id="41260-272">Also note that either one workload table or one workload file must be specified.</span></span>  
  
 <span data-ttu-id="41260-273">**-ix** _input_XML_file_name_</span><span class="sxs-lookup"><span data-stu-id="41260-273">**-ix** _input_XML_file_name_</span></span>  
 <span data-ttu-id="41260-274">指定包含 **dta** 輸入資訊的 XML 檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="41260-274">Specifies the name of the XML file containing **dta** input information.</span></span> <span data-ttu-id="41260-275">這必須是符合 DTASchema.xsd 的有效 XML 文件。</span><span class="sxs-lookup"><span data-stu-id="41260-275">This must be a valid XML document conforming to DTASchema.xsd.</span></span> <span data-ttu-id="41260-276">微調選項的命令提示字元所指定的衝突引數會覆寫這個 XML 檔案中的對應值。</span><span class="sxs-lookup"><span data-stu-id="41260-276">Conflicting arguments specified from the command prompt for tuning options override the corresponding value in this XML file.</span></span> <span data-ttu-id="41260-277">XML 輸入檔中以評估模式輸入的使用者指定組態是唯一例外。</span><span class="sxs-lookup"><span data-stu-id="41260-277">The only exception is if a user-specified configuration is entered in the evaluate mode in the XML input file.</span></span> <span data-ttu-id="41260-278">例如，如果在 XML 輸入檔的 **Configuration** 元素中輸入了某項組態， **EvaluateConfiguration** 元素也指定成一個微調選項，XML 輸入檔所指定的微調選項會覆寫在命令提示字元之下輸入的任何微調選項。</span><span class="sxs-lookup"><span data-stu-id="41260-278">For example, if a configuration is entered in the **Configuration** element of the XML input file and the **EvaluateConfiguration** element is also specified as one of the tuning options, the tuning options specified in the XML input file will override any tuning options entered from the command prompt.</span></span>  
  
 <span data-ttu-id="41260-279">**-m** _minimum_improvement_</span><span class="sxs-lookup"><span data-stu-id="41260-279">**-m** _minimum_improvement_</span></span>  
 <span data-ttu-id="41260-280">指定建議的組態必須符合之最小改進百分比。</span><span class="sxs-lookup"><span data-stu-id="41260-280">Specifies the minimum percentage of improvement that the recommended configuration must satisfy.</span></span>  
  
 <span data-ttu-id="41260-281">**-N** _online_option_</span><span class="sxs-lookup"><span data-stu-id="41260-281">**-N** _online_option_</span></span>  
 <span data-ttu-id="41260-282">指定是否在線上建立實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="41260-282">Specifies whether physical design structures are created online.</span></span> <span data-ttu-id="41260-283">下表列出和描述這個引數所能指定的值：</span><span class="sxs-lookup"><span data-stu-id="41260-283">The following table lists and describes the values you can specify for this argument:</span></span>  
  
|<span data-ttu-id="41260-284">值</span><span class="sxs-lookup"><span data-stu-id="41260-284">Value</span></span>|<span data-ttu-id="41260-285">描述</span><span class="sxs-lookup"><span data-stu-id="41260-285">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="41260-286">OFF</span><span class="sxs-lookup"><span data-stu-id="41260-286">OFF</span></span>|<span data-ttu-id="41260-287">不能在線上建立任何建議的實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="41260-287">No recommended physical design structures can be created online.</span></span>|  
|<span data-ttu-id="41260-288">開啟</span><span class="sxs-lookup"><span data-stu-id="41260-288">ON</span></span>|<span data-ttu-id="41260-289">可以在線上建立所有建議的實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="41260-289">All recommended physical design structures can be created online.</span></span>|  
|<span data-ttu-id="41260-290">MIXED</span><span class="sxs-lookup"><span data-stu-id="41260-290">MIXED</span></span>|<span data-ttu-id="41260-291">Database Engine Tuning Advisor 嘗試建議在可能的情況下，能夠在線上建立的實體設計結構。</span><span class="sxs-lookup"><span data-stu-id="41260-291">Database Engine Tuning Advisor attempts to recommend physical design structures that can be created online when possible.</span></span>|  
  
 <span data-ttu-id="41260-292">如果在線上建立索引，就會在它的物件定義上附加 ONLINE = ON。</span><span class="sxs-lookup"><span data-stu-id="41260-292">If indexes are created online, ONLINE = ON is appended to its object definition.</span></span>  
  
 <span data-ttu-id="41260-293">**-n** _number_of_events_</span><span class="sxs-lookup"><span data-stu-id="41260-293">**-n** _number_of_events_</span></span>  
 <span data-ttu-id="41260-294">指定在工作負載中 **dta** 應微調的事件數目。</span><span class="sxs-lookup"><span data-stu-id="41260-294">Specifies the number of events in the workload that **dta** should tune.</span></span> <span data-ttu-id="41260-295">如果指定了此引數，且工作負載是包含持續時間資訊的追蹤檔， **dta** 就會依據持續時間的遞減順序來微調事件。</span><span class="sxs-lookup"><span data-stu-id="41260-295">If this argument is specified and the workload is a trace file that contains duration information, then **dta** tunes events in decreasing order of duration.</span></span> <span data-ttu-id="41260-296">這個引數可用來比較實體設計結構的兩個組態。</span><span class="sxs-lookup"><span data-stu-id="41260-296">This argument is useful to compare two configurations of physical design structures.</span></span> <span data-ttu-id="41260-297">若要比較兩個組態，請依照下列方式，先指定相同的微調事件數目給這兩個組態，之後，兩個組態都指定無限的微調時間：</span><span class="sxs-lookup"><span data-stu-id="41260-297">To compare two configurations, specify the same number of events to be tuned for both configurations and then specify an unlimited tuning time for both also as follows:</span></span>  
  
```  
dta -n number_of_events -A 0  
```  
  
 <span data-ttu-id="41260-298">在這個情況下，指定無限微調時間 (`-A 0`) 非常重要。</span><span class="sxs-lookup"><span data-stu-id="41260-298">In this case, it is important to specify an unlimited tuning time (`-A 0`).</span></span> <span data-ttu-id="41260-299">否則，Database Engine Tuning Advisor 會預設 8 小時的微調時間。</span><span class="sxs-lookup"><span data-stu-id="41260-299">Otherwise, Database Engine Tuning Advisor assumes an 8 hour tuning time by default.</span></span>  
  
 <span data-ttu-id="41260-300">**-of** _output_script_file_name_</span><span class="sxs-lookup"><span data-stu-id="41260-300">**-of** _output_script_file_name_</span></span>  
 <span data-ttu-id="41260-301">指定 **dta** 將建議以 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼形式，寫入指定的檔案名稱與目的地。</span><span class="sxs-lookup"><span data-stu-id="41260-301">Specifies that **dta** writes the recommendation as a [!INCLUDE[tsql](../../includes/tsql-md.md)] script to the file name and destination specified.</span></span>  
  
 <span data-ttu-id="41260-302">您可以搭配此選項來使用 **-F** 。</span><span class="sxs-lookup"><span data-stu-id="41260-302">You can use **-F** with this option.</span></span> <span data-ttu-id="41260-303">請確定檔案名稱沒有重複，特別是當您也正在使用 **-or** 和 **-ox**時。</span><span class="sxs-lookup"><span data-stu-id="41260-303">Make sure that the file name is unique, especially if you are also using **-or** and **-ox**.</span></span>  
  
 <span data-ttu-id="41260-304">**-or** _output_xml_report_file_name_</span><span class="sxs-lookup"><span data-stu-id="41260-304">**-or** _output_xml_report_file_name_</span></span>  
 <span data-ttu-id="41260-305">指定 **dta** 將建議以 XML 格式寫入輸出報表。</span><span class="sxs-lookup"><span data-stu-id="41260-305">Specifies that **dta** writes the recommendation to an output report in XML.</span></span> <span data-ttu-id="41260-306">如果提供了檔案名稱，建議便會寫入該目的地。</span><span class="sxs-lookup"><span data-stu-id="41260-306">If a file name is supplied, then the recommendations are written to that destination.</span></span> <span data-ttu-id="41260-307">否則， **dta** 將使用該工作階段名稱來產生檔案名稱，並將其寫入目前的目錄。</span><span class="sxs-lookup"><span data-stu-id="41260-307">Otherwise, **dta** uses the session name to generate the file name and writes it to the current directory.</span></span>  
  
 <span data-ttu-id="41260-308">您可以搭配此選項來使用 **-F** 。</span><span class="sxs-lookup"><span data-stu-id="41260-308">You can use **-F** with this option.</span></span> <span data-ttu-id="41260-309">請確定檔案名稱沒有重複，特別是當您也正在使用 **-of** 和 **-ox**時。</span><span class="sxs-lookup"><span data-stu-id="41260-309">Make sure that the file name is unique, especially if you are also using **-of** and **-ox**.</span></span>  
  
 <span data-ttu-id="41260-310">**-ox** _output_XML_file_name_</span><span class="sxs-lookup"><span data-stu-id="41260-310">**-ox** _output_XML_file_name_</span></span>  
 <span data-ttu-id="41260-311">指定 **dta** 將建議以 XML 檔案格式寫入提供的檔案名稱與目的地。</span><span class="sxs-lookup"><span data-stu-id="41260-311">Specifies that **dta** writes the recommendation as an XML file to the file name and destination supplied.</span></span> <span data-ttu-id="41260-312">請確定 Database Engine Tuning Advisor 有寫入目的地目錄的權限。</span><span class="sxs-lookup"><span data-stu-id="41260-312">Ensure that Database Engine Tuning Advisor has permissions to write to the destination directory.</span></span>  
  
 <span data-ttu-id="41260-313">您可以搭配此選項來使用 **-F** 。</span><span class="sxs-lookup"><span data-stu-id="41260-313">You can use **-F** with this option.</span></span> <span data-ttu-id="41260-314">請確定檔案名稱沒有重複，特別是當您也正在使用 **-of** 和 **-or**時。</span><span class="sxs-lookup"><span data-stu-id="41260-314">Make sure that the file name is unique, especially if you are also using **-of** and **-or**.</span></span>  
  
 <span data-ttu-id="41260-315">**-P** _password_</span><span class="sxs-lookup"><span data-stu-id="41260-315">**-P** _password_</span></span>  
 <span data-ttu-id="41260-316">指定登入識別碼的密碼。</span><span class="sxs-lookup"><span data-stu-id="41260-316">Specifies the password for the login ID.</span></span> <span data-ttu-id="41260-317">若未使用此選項， **dta** 將提示您輸入密碼。</span><span class="sxs-lookup"><span data-stu-id="41260-317">If this option is not used, **dta** prompts for a password.</span></span>  
  
 <span data-ttu-id="41260-318">**-q**</span><span class="sxs-lookup"><span data-stu-id="41260-318">**-q**</span></span>  
 <span data-ttu-id="41260-319">設定無訊息模式。</span><span class="sxs-lookup"><span data-stu-id="41260-319">Sets quiet mode.</span></span> <span data-ttu-id="41260-320">不會將任何資訊寫入主控台中，進度和標頭資訊都包括在內。</span><span class="sxs-lookup"><span data-stu-id="41260-320">No information is written to the console, including progress and header information.</span></span>  
  
 <span data-ttu-id="41260-321">**-rl** _analysis_report_list_</span><span class="sxs-lookup"><span data-stu-id="41260-321">**-rl** _analysis_report_list_</span></span>  
 <span data-ttu-id="41260-322">指定要產生的分析報表清單。</span><span class="sxs-lookup"><span data-stu-id="41260-322">Specifies the list of analysis reports to generate.</span></span> <span data-ttu-id="41260-323">下表列出這個引數所能指定的值：</span><span class="sxs-lookup"><span data-stu-id="41260-323">The following table lists the values that can be specified for this argument:</span></span>  
  
|<span data-ttu-id="41260-324">值</span><span class="sxs-lookup"><span data-stu-id="41260-324">Value</span></span>|<span data-ttu-id="41260-325">Report</span><span class="sxs-lookup"><span data-stu-id="41260-325">Report</span></span>|  
|-----------|------------|  
|<span data-ttu-id="41260-326">ALL</span><span class="sxs-lookup"><span data-stu-id="41260-326">ALL</span></span>|<span data-ttu-id="41260-327">所有分析報表</span><span class="sxs-lookup"><span data-stu-id="41260-327">All analysis reports</span></span>|  
|<span data-ttu-id="41260-328">STMT_COST</span><span class="sxs-lookup"><span data-stu-id="41260-328">STMT_COST</span></span>|<span data-ttu-id="41260-329">陳述式成本報表</span><span class="sxs-lookup"><span data-stu-id="41260-329">Statement cost report</span></span>|  
|<span data-ttu-id="41260-330">EVT_FREQ</span><span class="sxs-lookup"><span data-stu-id="41260-330">EVT_FREQ</span></span>|<span data-ttu-id="41260-331">事件頻率報表</span><span class="sxs-lookup"><span data-stu-id="41260-331">Event frequency report</span></span>|  
|<span data-ttu-id="41260-332">STMT_DET</span><span class="sxs-lookup"><span data-stu-id="41260-332">STMT_DET</span></span>|<span data-ttu-id="41260-333">陳述式詳細資料報表</span><span class="sxs-lookup"><span data-stu-id="41260-333">Statement detail report</span></span>|  
|<span data-ttu-id="41260-334">CUR_STMT_IDX</span><span class="sxs-lookup"><span data-stu-id="41260-334">CUR_STMT_IDX</span></span>|<span data-ttu-id="41260-335">陳述式-索引關聯性報表 (目前組態)</span><span class="sxs-lookup"><span data-stu-id="41260-335">Statement-index relations report (current configuration)</span></span>|  
|<span data-ttu-id="41260-336">REC_STMT_IDX</span><span class="sxs-lookup"><span data-stu-id="41260-336">REC_STMT_IDX</span></span>|<span data-ttu-id="41260-337">陳述式-索引關聯性報表 (建議組態)</span><span class="sxs-lookup"><span data-stu-id="41260-337">Statement-index relations report (recommended configuration)</span></span>|  
|<span data-ttu-id="41260-338">STMT_COSTRANGE</span><span class="sxs-lookup"><span data-stu-id="41260-338">STMT_COSTRANGE</span></span>|<span data-ttu-id="41260-339">陳述式成本範圍報表</span><span class="sxs-lookup"><span data-stu-id="41260-339">Statement cost range report</span></span>|  
|<span data-ttu-id="41260-340">CUR_IDX_USAGE</span><span class="sxs-lookup"><span data-stu-id="41260-340">CUR_IDX_USAGE</span></span>|<span data-ttu-id="41260-341">索引使用方式報表 (目前的組態)</span><span class="sxs-lookup"><span data-stu-id="41260-341">Index usage report (current configuration)</span></span>|  
|<span data-ttu-id="41260-342">REC_IDX_USAGE</span><span class="sxs-lookup"><span data-stu-id="41260-342">REC_IDX_USAGE</span></span>|<span data-ttu-id="41260-343">索引使用方式報表 (建議的組態)</span><span class="sxs-lookup"><span data-stu-id="41260-343">Index usage report (recommended configuration)</span></span>|  
|<span data-ttu-id="41260-344">CUR_IDX_DET</span><span class="sxs-lookup"><span data-stu-id="41260-344">CUR_IDX_DET</span></span>|<span data-ttu-id="41260-345">索引詳細資料報表 (目前的組態)</span><span class="sxs-lookup"><span data-stu-id="41260-345">Index detail report (current configuration)</span></span>|  
|<span data-ttu-id="41260-346">REC_IDX_DET</span><span class="sxs-lookup"><span data-stu-id="41260-346">REC_IDX_DET</span></span>|<span data-ttu-id="41260-347">索引詳細資料報表 (建議的組態)</span><span class="sxs-lookup"><span data-stu-id="41260-347">Index detail report (recommended configuration)</span></span>|  
|<span data-ttu-id="41260-348">VIW_TAB</span><span class="sxs-lookup"><span data-stu-id="41260-348">VIW_TAB</span></span>|<span data-ttu-id="41260-349">檢視表-資料表關聯性報表</span><span class="sxs-lookup"><span data-stu-id="41260-349">View-table relations report</span></span>|  
|<span data-ttu-id="41260-350">WKLD_ANL</span><span class="sxs-lookup"><span data-stu-id="41260-350">WKLD_ANL</span></span>|<span data-ttu-id="41260-351">工作負載分析報表</span><span class="sxs-lookup"><span data-stu-id="41260-351">Workload analysis report</span></span>|  
|<span data-ttu-id="41260-352">DB_ACCESS</span><span class="sxs-lookup"><span data-stu-id="41260-352">DB_ACCESS</span></span>|<span data-ttu-id="41260-353">資料庫存取報表</span><span class="sxs-lookup"><span data-stu-id="41260-353">Database access report</span></span>|  
|<span data-ttu-id="41260-354">TAB_ACCESS</span><span class="sxs-lookup"><span data-stu-id="41260-354">TAB_ACCESS</span></span>|<span data-ttu-id="41260-355">資料表存取報表</span><span class="sxs-lookup"><span data-stu-id="41260-355">Table access report</span></span>|  
|<span data-ttu-id="41260-356">COL_ACCESS</span><span class="sxs-lookup"><span data-stu-id="41260-356">COL_ACCESS</span></span>|<span data-ttu-id="41260-357">資料行存取報表</span><span class="sxs-lookup"><span data-stu-id="41260-357">Column access report</span></span>|  
  
 <span data-ttu-id="41260-358">請用逗號分隔各值以指定多份報表，例如：</span><span class="sxs-lookup"><span data-stu-id="41260-358">Specify multiple reports by separating the values with commas, for example:</span></span>  
  
```  
... -rl EVT_FREQ, VIW_TAB, WKLD_ANL ...  
```  
  
 <span data-ttu-id="41260-359">**-S** _server_name_[ *\instance*]</span><span class="sxs-lookup"><span data-stu-id="41260-359">**-S** _server_name_[ *\instance*]</span></span>  
 <span data-ttu-id="41260-360">指定電腦名稱及要連接的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="41260-360">Specifies the name of the computer and instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] to connect to.</span></span> <span data-ttu-id="41260-361">若未指定 *server_name* ， **dta** 會連接至本機電腦上的預設 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="41260-361">If no *server_name* is specified, **dta** connects to the default instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] on the local computer.</span></span> <span data-ttu-id="41260-362">連接至具名的執行個體或透過網路從遠端電腦執行 **dta** 時，必須使用此選項。</span><span class="sxs-lookup"><span data-stu-id="41260-362">This option is required when connecting to a named instance or when executing **dta** from a remote computer on the network.</span></span>  
  
 <span data-ttu-id="41260-363">**-s** _session_name_</span><span class="sxs-lookup"><span data-stu-id="41260-363">**-s** _session_name_</span></span>  
 <span data-ttu-id="41260-364">指定微調工作階段的名稱。</span><span class="sxs-lookup"><span data-stu-id="41260-364">Specifies the name of the tuning session.</span></span> <span data-ttu-id="41260-365">若未指定 **-ID** ，則必須進行此步驟。</span><span class="sxs-lookup"><span data-stu-id="41260-365">This is required if **-ID** is not specified.</span></span>  
  
 <span data-ttu-id="41260-366">**-Tf** _table_list_file_</span><span class="sxs-lookup"><span data-stu-id="41260-366">**-Tf** _table_list_file_</span></span>  
 <span data-ttu-id="41260-367">指定包含要微調的資料表清單之檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="41260-367">Specifies the name of a file containing a list of tables to be tuned.</span></span> <span data-ttu-id="41260-368">檔案中所列出的每份資料表，都應該從新的一行中開始。</span><span class="sxs-lookup"><span data-stu-id="41260-368">Each table listed within the file should begin on a new line.</span></span> <span data-ttu-id="41260-369">資料表名稱應該採用三部分命名，例如 **AdventureWorks2012.HumanResources.Department**。</span><span class="sxs-lookup"><span data-stu-id="41260-369">Table names should be qualified with three-part naming, for example, **AdventureWorks2012.HumanResources.Department**.</span></span> <span data-ttu-id="41260-370">另外，如果您要叫用資料表調整功能，現有資料表的名稱後面可以接著一個指示預計資料表列數的數字。</span><span class="sxs-lookup"><span data-stu-id="41260-370">Optionally, to invoke the table-scaling feature, the name of an existing table can be followed by a number indicating the projected number of rows in the table.</span></span> <span data-ttu-id="41260-371">當微調或評估工作負載中參考這些資料表的陳述式時，Database Engine Tuning Advisor 會考量預計的列數。</span><span class="sxs-lookup"><span data-stu-id="41260-371">Database Engine Tuning Advisor takes into consideration the projected number of rows while tuning or evaluating statements in the workload that reference these tables.</span></span> <span data-ttu-id="41260-372">請注意， *number_of_rows* 計數與 *table_name*之間可能有一個或多個空格。</span><span class="sxs-lookup"><span data-stu-id="41260-372">Note that there can be one or more spaces between the *number_of_rows* count and the *table_name*.</span></span>  
  
 <span data-ttu-id="41260-373">這是 *table_list_file*的檔案格式：</span><span class="sxs-lookup"><span data-stu-id="41260-373">This is the file format for *table_list_file*:</span></span>  
  
 <span data-ttu-id="41260-374">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span><span class="sxs-lookup"><span data-stu-id="41260-374">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span></span>  
  
 <span data-ttu-id="41260-375">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span><span class="sxs-lookup"><span data-stu-id="41260-375">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span></span>  
  
 <span data-ttu-id="41260-376">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span><span class="sxs-lookup"><span data-stu-id="41260-376">*database_name*.[*schema_name*].*table_name* [*number_of_rows*]</span></span>  
  
 <span data-ttu-id="41260-377">這個引數是在命令提示字元中輸入資料表清單的另一種方法 ( **-Tl**)。</span><span class="sxs-lookup"><span data-stu-id="41260-377">This argument is an alternative to entering a table list at the command prompt (**-Tl**).</span></span> <span data-ttu-id="41260-378">如果您使用 **-Tl**，請勿使用資料表清單檔案 ( **-Tf**)。</span><span class="sxs-lookup"><span data-stu-id="41260-378">Do not use a table list file (**-Tf**) if you are using **-Tl**.</span></span> <span data-ttu-id="41260-379">如果同時使用這兩個引數， **dta** 會失敗並傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="41260-379">If both arguments are used, **dta** fails and returns an error.</span></span>  
  
 <span data-ttu-id="41260-380">如果省略了 **-Tf** 和 **-Tl** 引數，則會將指定資料庫中的所有使用者資料表視為要進行微調。</span><span class="sxs-lookup"><span data-stu-id="41260-380">If the **-Tf** and **-Tl** arguments are omitted, all user tables in the specified databases are considered for tuning.</span></span>  
  
 <span data-ttu-id="41260-381">**-Tl** _table_list_</span><span class="sxs-lookup"><span data-stu-id="41260-381">**-Tl** _table_list_</span></span>  
 <span data-ttu-id="41260-382">在命令提示字元之下，指定要微調的資料表清單。</span><span class="sxs-lookup"><span data-stu-id="41260-382">Specifies at the command prompt a list of tables to be tuned.</span></span> <span data-ttu-id="41260-383">請在資料表名稱之間加上逗號，將它們分開。</span><span class="sxs-lookup"><span data-stu-id="41260-383">Place commas between table names to separate them.</span></span> <span data-ttu-id="41260-384">如果使用 **-D** 引數只指定一個資料庫，就不需要使用資料庫名稱限定資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="41260-384">If only one database is specified with the **-D** argument, then table names do not need to be qualified with a database name.</span></span> <span data-ttu-id="41260-385">否則，每份資料表都需要完整的名稱格式： *database_name.schema_name.table_name* 。</span><span class="sxs-lookup"><span data-stu-id="41260-385">Otherwise, the fully qualified name in the format: *database_name.schema_name.table_name* is required for each table.</span></span>  
  
 <span data-ttu-id="41260-386">這個引數是使用資料表清單檔案的另一種方法 ( **-Tf**)。</span><span class="sxs-lookup"><span data-stu-id="41260-386">This argument is an alternative to using a table list file (**-Tf**).</span></span> <span data-ttu-id="41260-387">如果同時使用 **-Tl** 和 **-Tf** ， **dta** 會失敗並傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="41260-387">If both **-Tl** and **-Tf** are used, **dta** fails and returns an error.</span></span>  
  
 <span data-ttu-id="41260-388">**-U** _login_id_</span><span class="sxs-lookup"><span data-stu-id="41260-388">**-U** _login_id_</span></span>  
 <span data-ttu-id="41260-389">指定用來連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]的登入識別碼。</span><span class="sxs-lookup"><span data-stu-id="41260-389">Specifies the login ID used to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="41260-390">**-u**</span><span class="sxs-lookup"><span data-stu-id="41260-390">**-u**</span></span>  
 <span data-ttu-id="41260-391">啟動 Database Engine Tuning Advisor GUI。</span><span class="sxs-lookup"><span data-stu-id="41260-391">Launches the Database Engine Tuning Advisor GUI.</span></span> <span data-ttu-id="41260-392">所有參數都會視做為使用者介面的初始設定。</span><span class="sxs-lookup"><span data-stu-id="41260-392">All parameters are treated as the initial settings for the user interface.</span></span>  
  
 <span data-ttu-id="41260-393">**-x**</span><span class="sxs-lookup"><span data-stu-id="41260-393">**-x**</span></span>  
 <span data-ttu-id="41260-394">啟動微調工作階段並結束。</span><span class="sxs-lookup"><span data-stu-id="41260-394">Starts tuning session and exits.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41260-395">備註</span><span class="sxs-lookup"><span data-stu-id="41260-395">Remarks</span></span>  
 <span data-ttu-id="41260-396">按一下 CTRL+C 可停止微調工作階段，並依據 **dta** 截至目前為止所完成的分析來產生建議。</span><span class="sxs-lookup"><span data-stu-id="41260-396">Press CTRL+C once to stop the tuning session and generate recommendations based on the analysis **dta** has completed up to this point.</span></span> <span data-ttu-id="41260-397">系統會提示您決定是否要產生建議。</span><span class="sxs-lookup"><span data-stu-id="41260-397">You will be prompted to decide whether you want to generate recommendations or not.</span></span> <span data-ttu-id="41260-398">請再按一下 CTRL+C 來停止微調工作階段，不產生建議。</span><span class="sxs-lookup"><span data-stu-id="41260-398">Press CTRL+C again to stop the tuning session without generating recommendations.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="41260-399">範例</span><span class="sxs-lookup"><span data-stu-id="41260-399">Examples</span></span>  
 <span data-ttu-id="41260-400">**A.微調建議中包含索引和索引檢視表的工作負載**</span><span class="sxs-lookup"><span data-stu-id="41260-400">**A. Tune a workload that includes indexes and indexed views in its recommendation**</span></span>  
  
 <span data-ttu-id="41260-401">這個範例利用安全連接 (`-E`) 來連接 MyServer 中的 **tpcd1G** 資料庫，以分析工作負載和建立各項建議。</span><span class="sxs-lookup"><span data-stu-id="41260-401">This example uses a secure connection (`-E`) to connect to the **tpcd1G** database on MyServer to analyze a workload and create recommendations.</span></span> <span data-ttu-id="41260-402">它會將輸出寫入名為 script.sql 的指令碼檔案。</span><span class="sxs-lookup"><span data-stu-id="41260-402">It writes the output to a script file named script.sql.</span></span> <span data-ttu-id="41260-403">如果 script.sql 已經存在，則因已指定 **引數，所以** dta `-F` 會覆寫該檔案。</span><span class="sxs-lookup"><span data-stu-id="41260-403">If script.sql already exists, then **dta** will overwrite the file because the `-F` argument has been specified.</span></span> <span data-ttu-id="41260-404">微調工作階段的執行時間沒有限制，以便確保能夠完整分析工作負載 (`-A 0`)。</span><span class="sxs-lookup"><span data-stu-id="41260-404">The tuning session runs for an unlimited length of time to ensure a complete analysis of the workload (`-A 0`).</span></span> <span data-ttu-id="41260-405">建議至少必須能夠增進 5% (`-m 5`)。</span><span class="sxs-lookup"><span data-stu-id="41260-405">The recommendation must provide a minimum improvement of 5% (`-m 5`).</span></span> <span data-ttu-id="41260-406">**dta** 的最終建議應該包含索引與索引檢視表 (`-fa IDX_IV`)。</span><span class="sxs-lookup"><span data-stu-id="41260-406">**dta** should include indexes and indexed views in its final recommendation (`-fa IDX_IV`).</span></span>  
  
```  
dta -S MyServer -E -D tpcd1G -if tpcd_22.sql -F -of script.sql -A 0 -m 5 -fa IDX_IV  
```  
  
 <span data-ttu-id="41260-407">**B.限制磁碟空間的使用**</span><span class="sxs-lookup"><span data-stu-id="41260-407">**B. Limit disk use**</span></span>  
  
 <span data-ttu-id="41260-408">這個範例將資料庫大小總計限制成 3 GB (`-B 3000`)，其中包括原始資料和其他索引，且會將輸出導向 d:\result_dir\script1.sql。</span><span class="sxs-lookup"><span data-stu-id="41260-408">This example limits the total database size, which includes the raw data and the additional indexes, to 3 gigabytes (GB) (`-B 3000`) and directs the output to d:\result_dir\script1.sql.</span></span> <span data-ttu-id="41260-409">它的執行時間不超出 1 小時 (`-A 60`)。</span><span class="sxs-lookup"><span data-stu-id="41260-409">It runs for no more than 1 hour (`-A 60`).</span></span>  
  
```  
dta -D tpcd1G -if tpcd_22.sql -B 3000 -of "d:\result_dir\script1.sql" -A 60  
```  
  
 <span data-ttu-id="41260-410">**C.限制微調查詢的數目**</span><span class="sxs-lookup"><span data-stu-id="41260-410">**C. Limit the number of tuned queries**</span></span>  
  
 <span data-ttu-id="41260-411">這個範例會將從 orders_wkld.sql 檔讀取的查詢數目限制為最大值 10 (`-n 10`)，或執行 15 分鐘 (`-A 15`)，兩者中先出現者優先。</span><span class="sxs-lookup"><span data-stu-id="41260-411">This example limits the number of queries read from the file orders_wkld.sql to a maximum of 10 (`-n 10`) and runs for 15 minutes (`-A 15`), whichever comes first.</span></span> <span data-ttu-id="41260-412">若要確定 10 項查詢全都得到微調，請利用 `-A 0` 來指定無限微調時間。</span><span class="sxs-lookup"><span data-stu-id="41260-412">To make sure that all 10 queries are tuned, specify an unlimited tuning time with `-A 0`.</span></span> <span data-ttu-id="41260-413">如果時間很重要，請依照這個範例所顯示，利用 `-A` 引數指定微調所能使用的分鐘數來指定適當的時間限制。</span><span class="sxs-lookup"><span data-stu-id="41260-413">If time is important, specify an appropriate time limit by specifying the number of minutes that are available for tuning with the `-A` argument as shown in this example.</span></span>  
  
```  
dta -D orders -if orders_wkld.sql -of script.sql -A 15 -n 10  
```  
  
 <span data-ttu-id="41260-414">**D.微調檔案中所列出的特定資料表**</span><span class="sxs-lookup"><span data-stu-id="41260-414">**D. Tune specific tables listed in a file**</span></span>  
  
 <span data-ttu-id="41260-415">此範例示範 *table_list_file* ( **-Tf** 引數) 的用法。</span><span class="sxs-lookup"><span data-stu-id="41260-415">This example demonstrates the use of *table_list_file* (the **-Tf** argument).</span></span> <span data-ttu-id="41260-416">table_list.txt 檔的內容如下：</span><span class="sxs-lookup"><span data-stu-id="41260-416">The contents of the file table_list.txt are as follows:</span></span>  
  
```  
AdventureWorks2012.Sales.Customer  100000  
AdventureWorks2012.Sales.Store  
AdventureWorks2012.Production.Product  2000000  
```  
  
 <span data-ttu-id="41260-417">table_list.txt 的內容指定：</span><span class="sxs-lookup"><span data-stu-id="41260-417">The contents of table_list.txt specifies that:</span></span>  
  
-   <span data-ttu-id="41260-418">只應微調資料庫中的 **Customer**、 **Store**和 **Product** 等資料表。</span><span class="sxs-lookup"><span data-stu-id="41260-418">Only the **Customer**, **Store**, and **Product** tables in the database should be tuned.</span></span>  
  
-   <span data-ttu-id="41260-419">**Customer** 和 **Product** 資料表中的列數，分別假設為 100,000 和 2,000,000。</span><span class="sxs-lookup"><span data-stu-id="41260-419">The number of rows in the **Customer** and **Product** tables are assumed to be 100,000 and 2,000,000, respectively.</span></span>  
  
-   <span data-ttu-id="41260-420">**Store** 中的列數假設為資料表目前的列數。</span><span class="sxs-lookup"><span data-stu-id="41260-420">The number of rows in **Store** are assumed to be the current number of rows in the table.</span></span>  
  
 <span data-ttu-id="41260-421">請注意，資料列計數與 *table_list_file*的先前資料表名稱之間可能有一個或多個空格。</span><span class="sxs-lookup"><span data-stu-id="41260-421">Note that there can be one or more spaces between the number of rows count and the preceding table name in the *table_list_file*.</span></span>  
  
 <span data-ttu-id="41260-422">微調時間是 2 小時 (`-A 120`)，輸出寫在 XML 檔 (`-ox XMLTune.xml`) 中。</span><span class="sxs-lookup"><span data-stu-id="41260-422">The tuning time is 2 hours (`-A 120`) and the output is written to an XML file (`-ox XMLTune.xml`).</span></span>  
  
```  
dta -D pubs -if pubs_wkld.sql -ox XMLTune.xml -A 120 -Tf table_list.txt  
```  
  
## <a name="see-also"></a><span data-ttu-id="41260-423">另請參閱</span><span class="sxs-lookup"><span data-stu-id="41260-423">See Also</span></span>  
 <span data-ttu-id="41260-424">[命令提示字元公用程式參考 &#40;資料庫引擎&#41;](../command-prompt-utility-reference-database-engine.md) </span><span class="sxs-lookup"><span data-stu-id="41260-424">[Command Prompt Utility Reference &#40;Database Engine&#41;](../command-prompt-utility-reference-database-engine.md) </span></span>  
 [<span data-ttu-id="41260-425">Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="41260-425">Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/database-engine-tuning-advisor.md)  
  
  
