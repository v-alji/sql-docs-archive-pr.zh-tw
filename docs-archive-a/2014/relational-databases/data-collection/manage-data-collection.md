---
title: 管理資料收集 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- data collection [SQL Server]
- data collector [SQL Server], Transact-SQL
- data collector [SQL Server], SQL Server Management Studio
ms.assetid: bc137daa-9f37-4c01-9766-8b7350c75af8
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 0a7d88923bc41939541bedeed2d40908e454e9c5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594106"
---
# <a name="manage-data-collection"></a><span data-ttu-id="dec7d-102">管理資料收集</span><span class="sxs-lookup"><span data-stu-id="dec7d-102">Manage Data Collection</span></span>
  <span data-ttu-id="dec7d-103">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程式和函數來管理資料收集的不同層面，例如啟用或停用資料收集、變更收集組設定，或在管理資料倉儲中查看資料。</span><span class="sxs-lookup"><span data-stu-id="dec7d-103">You can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] or [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedures and functions to manage different aspects of data collection, such as enabling or disabling data collection, changing a collection set configuration, or viewing data in the management data warehouse.</span></span>  
  
## <a name="manage-data-collection-by-using-sql-server-management-studio"></a><span data-ttu-id="dec7d-104">使用 SQL Server Management Studio 管理資料收集</span><span class="sxs-lookup"><span data-stu-id="dec7d-104">Manage Data Collection by Using SQL Server Management Studio</span></span>  
 <span data-ttu-id="dec7d-105">您可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中使用 [物件總管] 來執行與資料收集器相關的下列工作：</span><span class="sxs-lookup"><span data-stu-id="dec7d-105">You can perform the following data collector-related tasks by using Object Explorer in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]:</span></span>  
  
-   [<span data-ttu-id="dec7d-106">設定管理資料倉儲 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-106">Configure the Management Data Warehouse &#40;SQL Server Management Studio&#41;</span></span>](configure-the-management-data-warehouse-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="dec7d-107">設定資料收集器的屬性</span><span class="sxs-lookup"><span data-stu-id="dec7d-107">Configure Properties of a Data Collector</span></span>](configure-properties-of-a-data-collector.md)  
  
-   [<span data-ttu-id="dec7d-108">啟用或停用資料收集</span><span class="sxs-lookup"><span data-stu-id="dec7d-108">Enable or Disable Data Collection</span></span>](data-collection.md)  
  
-   [<span data-ttu-id="dec7d-109">啟動或停止收集組</span><span class="sxs-lookup"><span data-stu-id="dec7d-109">Start or Stop a Collection Set</span></span>](start-or-stop-a-collection-set.md)  
  
-   [<span data-ttu-id="dec7d-110">使用 SQL Server Profiler 來建立 SQL 追蹤收集組 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-110">Use SQL Server Profiler to Create a SQL Trace Collection Set &#40;SQL Server Management Studio&#41;</span></span>](use-sql-server-profiler-to-create-a-sql-trace-collection-set.md)  
  
-   [<span data-ttu-id="dec7d-111">檢視收集組記錄 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-111">View Collection Set Logs &#40;SQL Server Management Studio&#41;</span></span>](view-collection-set-logs-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="dec7d-112">檢視或變更收集組排程 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-112">View or Change Collection Set Schedules &#40;SQL Server Management Studio&#41;</span></span>](view-or-change-collection-set-schedules-sql-server-management-studio.md)  
  
-   [<span data-ttu-id="dec7d-113">檢視收集組報表 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-113">View a Collection Set Report &#40;SQL Server Management Studio&#41;</span></span>](view-a-collection-set-report-sql-server-management-studio.md)  
  
## <a name="manage-data-collection-by-using-transact-sql"></a><span data-ttu-id="dec7d-114">使用 Transact-SQL 管理資料收集</span><span class="sxs-lookup"><span data-stu-id="dec7d-114">Manage Data Collection by Using Transact-SQL</span></span>  
 <span data-ttu-id="dec7d-115">資料收集器會提供預存程序的廣泛集合，您可使用這些預存程序來執行任何資料收集器相關的工作。</span><span class="sxs-lookup"><span data-stu-id="dec7d-115">The data collector provides an extensive collection of stored procedures that you can use to perform any data-collector related task.</span></span> <span data-ttu-id="dec7d-116">例如，您可以使用 [!INCLUDE[tsql](../../includes/tsql-md.md)]來執行下列工作：</span><span class="sxs-lookup"><span data-stu-id="dec7d-116">For example, by using [!INCLUDE[tsql](../../includes/tsql-md.md)], you can perform the following tasks:</span></span>  
  
-   [<span data-ttu-id="dec7d-117">設定資料收集參數 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-117">Configure Data Collection Parameters &#40;Transact-SQL&#41;</span></span>](configure-data-collection-parameters-transact-sql.md)  
  
-   [<span data-ttu-id="dec7d-118">啟用或停用資料收集</span><span class="sxs-lookup"><span data-stu-id="dec7d-118">Enable or Disable Data Collection</span></span>](data-collection.md)  
  
-   [<span data-ttu-id="dec7d-119">啟動或停止收集組</span><span class="sxs-lookup"><span data-stu-id="dec7d-119">Start or Stop a Collection Set</span></span>](start-or-stop-a-collection-set.md)  
  
-   [<span data-ttu-id="dec7d-120">建立使用一般 T-SQL 查詢收集器型別的自訂收集組 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-120">Create a Custom Collection Set That Uses the Generic T-SQL Query Collector Type &#40;Transact-SQL&#41;</span></span>](create-custom-collection-set-generic-t-sql-query-collector-type.md)  
  
-   [<span data-ttu-id="dec7d-121">將收集項加入收集組 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-121">Add a Collection Item to a Collection Set &#40;Transact-SQL&#41;</span></span>](add-a-collection-item-to-a-collection-set-transact-sql.md)  
  
 <span data-ttu-id="dec7d-122">此外，您還可以使用一些函數和檢視來取得 msdb 和管理資料倉儲資料庫的組態資料、執行記錄資料，以及管理資料倉儲中所儲存的資料。</span><span class="sxs-lookup"><span data-stu-id="dec7d-122">In addition, there are functions and views that you can use to get configuration data for the msdb and management data warehouse databases, execution log data, and data that is stored in the management data warehouse.</span></span>  
  
 <span data-ttu-id="dec7d-123">您可以使用預存程序、函數和檢視，而提供這些項目的目的是要建立您自己的端對端資料收集案例。</span><span class="sxs-lookup"><span data-stu-id="dec7d-123">You can use the stored procedures, functions, and views that are provided to create your own end-to-end data collection scenarios.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="dec7d-124">不同於一般預存程序，資料收集器的預存程序會使用嚴格類型的參數，而且不支援資料類型的自動轉換。</span><span class="sxs-lookup"><span data-stu-id="dec7d-124">Unlike regular stored procedures, the data collector stored procedures use strictly typed parameters and do not support automatic data type conversion.</span></span> <span data-ttu-id="dec7d-125">如果沒有依照引數描述所指定，以正確的輸入參數資料類型來呼叫這些參數，預存程序會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="dec7d-125">If these parameters are not called with the correct input parameter data types, as specified in the argument description, the stored procedure returns an error.</span></span>  
  
 <span data-ttu-id="dec7d-126">您可以使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 來建立及執行所提供的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="dec7d-126">You can use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to create and execute the provided code samples.</span></span> <span data-ttu-id="dec7d-127">如需詳細資訊，請參閱 [物件總管](../../ssms/object/object-explorer.md)。</span><span class="sxs-lookup"><span data-stu-id="dec7d-127">For more information, see [Object Explorer](../../ssms/object/object-explorer.md).</span></span> <span data-ttu-id="dec7d-128">另一個替代方法是使用任何編輯器建立查詢，並將它儲存為 .sql 副檔名的文字檔。</span><span class="sxs-lookup"><span data-stu-id="dec7d-128">As an alternative you can create the query in any editor and save it in a text file that has a .sql file name extension.</span></span> <span data-ttu-id="dec7d-129">您可以使用 `sqlcmd` 公用程式，從 Windows 命令提示字元執行查詢。</span><span class="sxs-lookup"><span data-stu-id="dec7d-129">You can execute the query from the Windows command prompt using the `sqlcmd` utility.</span></span> <span data-ttu-id="dec7d-130">如需詳細資訊，請參閱 [使用 sqlcmd 公用程式](../scripting/sqlcmd-use-the-utility.md)。</span><span class="sxs-lookup"><span data-stu-id="dec7d-130">For more information, see [Use the sqlcmd Utility](../scripting/sqlcmd-use-the-utility.md).</span></span>  
  
### <a name="stored-procedures-and-views"></a><span data-ttu-id="dec7d-131">預存程序和檢視表</span><span class="sxs-lookup"><span data-stu-id="dec7d-131">Stored Procedures and Views</span></span>  
 <span data-ttu-id="dec7d-132">**使用資料收集器**</span><span class="sxs-lookup"><span data-stu-id="dec7d-132">**Working with the data collector**</span></span>  
  
 <span data-ttu-id="dec7d-133">下表描述的是您可以用來處理資料收集器的預存程序。</span><span class="sxs-lookup"><span data-stu-id="dec7d-133">The following table describes the stored procedures that you can use to work with the data collector.</span></span>  
  
|<span data-ttu-id="dec7d-134">程序名稱</span><span class="sxs-lookup"><span data-stu-id="dec7d-134">Procedure name</span></span>|<span data-ttu-id="dec7d-135">描述</span><span class="sxs-lookup"><span data-stu-id="dec7d-135">Description</span></span>|  
|--------------------|-----------------|  
|[<span data-ttu-id="dec7d-136">sp_syscollector_enable_collector</span><span class="sxs-lookup"><span data-stu-id="dec7d-136">sp_syscollector_enable_collector</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql)|<span data-ttu-id="dec7d-137">啟用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="dec7d-137">Enable the data collector.</span></span>|  
|[<span data-ttu-id="dec7d-138">sp_syscollector_disable_collector</span><span class="sxs-lookup"><span data-stu-id="dec7d-138">sp_syscollector_disable_collector</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql)|<span data-ttu-id="dec7d-139">停用資料收集器。</span><span class="sxs-lookup"><span data-stu-id="dec7d-139">Disable the data collector.</span></span>|  
  
 <span data-ttu-id="dec7d-140">**使用收集組**</span><span class="sxs-lookup"><span data-stu-id="dec7d-140">**Working with collection sets**</span></span>  
  
 <span data-ttu-id="dec7d-141">下表描述的是您可以用來處理收集組的預存程序。</span><span class="sxs-lookup"><span data-stu-id="dec7d-141">The following table describes the stored procedures that you can use to work with collection sets.</span></span>  
  
|<span data-ttu-id="dec7d-142">程序名稱</span><span class="sxs-lookup"><span data-stu-id="dec7d-142">Procedure name</span></span>|<span data-ttu-id="dec7d-143">描述</span><span class="sxs-lookup"><span data-stu-id="dec7d-143">Description</span></span>|  
|--------------------|-----------------|  
|[<span data-ttu-id="dec7d-144">sp_syscollector_run_collection_set &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-144">sp_syscollector_run_collection_set &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-run-collection-set-transact-sql)|<span data-ttu-id="dec7d-145">視需要執行收集組。</span><span class="sxs-lookup"><span data-stu-id="dec7d-145">Run a collection set on demand.</span></span>|  
|[<span data-ttu-id="dec7d-146">sp_syscollector_start_collection_set &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-146">sp_syscollector_start_collection_set &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql)|<span data-ttu-id="dec7d-147">啟動收集組。</span><span class="sxs-lookup"><span data-stu-id="dec7d-147">Start a collection set.</span></span>|  
|[<span data-ttu-id="dec7d-148">sp_syscollector_stop_collection_set &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-148">sp_syscollector_stop_collection_set &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql)|<span data-ttu-id="dec7d-149">停止收集組。</span><span class="sxs-lookup"><span data-stu-id="dec7d-149">Stop a collection set.</span></span>|  
|[<span data-ttu-id="dec7d-150">sp_syscollector_create_collection_set &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-150">sp_syscollector_create_collection_set &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-create-collection-set-transact-sql)|<span data-ttu-id="dec7d-151">建立收集組。</span><span class="sxs-lookup"><span data-stu-id="dec7d-151">Create a collection set.</span></span>|  
|[<span data-ttu-id="dec7d-152">sp_syscollector_delete_collection_set &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-152">sp_syscollector_delete_collection_set &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-collection-set-transact-sql)|<span data-ttu-id="dec7d-153">刪除收集組。</span><span class="sxs-lookup"><span data-stu-id="dec7d-153">Delete a collection set.</span></span>|  
|[<span data-ttu-id="dec7d-154">sp_syscollector_update_collection_set &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-154">sp_syscollector_update_collection_set &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-update-collection-set-transact-sql)|<span data-ttu-id="dec7d-155">變更收集組組態。</span><span class="sxs-lookup"><span data-stu-id="dec7d-155">Change a collection set configuration.</span></span>|  
|[<span data-ttu-id="dec7d-156">sp_syscollector_upload_collection_set &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-156">sp_syscollector_upload_collection_set &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-upload-collection-set-transact-sql)|<span data-ttu-id="dec7d-157">將收集組資料上傳到管理資料倉儲。</span><span class="sxs-lookup"><span data-stu-id="dec7d-157">Upload collection set data to the management data warehouse.</span></span> <span data-ttu-id="dec7d-158">這實際上就是視需要的上傳。</span><span class="sxs-lookup"><span data-stu-id="dec7d-158">This is effectively an on-demand upload.</span></span>|  
  
 <span data-ttu-id="dec7d-159">**使用收集項**</span><span class="sxs-lookup"><span data-stu-id="dec7d-159">**Working with collection items**</span></span>  
  
 <span data-ttu-id="dec7d-160">下表描述的是您可以用來處理收集項的預存程序。</span><span class="sxs-lookup"><span data-stu-id="dec7d-160">The following table describes the stored procedures that you can use to work with collection items.</span></span>  
  
|<span data-ttu-id="dec7d-161">程序名稱</span><span class="sxs-lookup"><span data-stu-id="dec7d-161">Procedure name</span></span>|<span data-ttu-id="dec7d-162">描述</span><span class="sxs-lookup"><span data-stu-id="dec7d-162">Description</span></span>|  
|--------------------|-----------------|  
|[<span data-ttu-id="dec7d-163">sp_syscollector_create_collection_item &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-163">sp_syscollector_create_collection_item &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-create-collection-item-transact-sql)|<span data-ttu-id="dec7d-164">建立收集項。</span><span class="sxs-lookup"><span data-stu-id="dec7d-164">Create a collection item.</span></span>|  
|[<span data-ttu-id="dec7d-165">sp_syscollector_delete_collection_item &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-165">sp_syscollector_delete_collection_item &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-collection-item-transact-sql)|<span data-ttu-id="dec7d-166">刪除收集項。</span><span class="sxs-lookup"><span data-stu-id="dec7d-166">Delete a collection item.</span></span>|  
|[<span data-ttu-id="dec7d-167">sp_syscollector_update_collection_item &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-167">sp_syscollector_update_collection_item &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-update-collection-item-transact-sql)|<span data-ttu-id="dec7d-168">更新收集項。</span><span class="sxs-lookup"><span data-stu-id="dec7d-168">Update a collection item.</span></span>|  
  
 <span data-ttu-id="dec7d-169">**使用收集器型別**</span><span class="sxs-lookup"><span data-stu-id="dec7d-169">**Working with collector types**</span></span>  
  
 <span data-ttu-id="dec7d-170">下表描述的是您可以用來處理收集器型別的預存程序。</span><span class="sxs-lookup"><span data-stu-id="dec7d-170">The following table describes the stored procedures that you can use to work with collector types.</span></span>  
  
|<span data-ttu-id="dec7d-171">程序名稱</span><span class="sxs-lookup"><span data-stu-id="dec7d-171">Procedure name</span></span>|<span data-ttu-id="dec7d-172">描述</span><span class="sxs-lookup"><span data-stu-id="dec7d-172">Description</span></span>|  
|--------------------|-----------------|  
|[<span data-ttu-id="dec7d-173">sp_syscollector_create_collector_type &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-173">sp_syscollector_create_collector_type &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-create-collector-type-transact-sql)|<span data-ttu-id="dec7d-174">建立收集器型別。</span><span class="sxs-lookup"><span data-stu-id="dec7d-174">Create a collector type.</span></span>|  
|[<span data-ttu-id="dec7d-175">sp_syscollector_update_collector_type &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-175">sp_syscollector_update_collector_type &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-update-collector-type-transact-sql)|<span data-ttu-id="dec7d-176">更新收集器型別。</span><span class="sxs-lookup"><span data-stu-id="dec7d-176">Update a collector type.</span></span>|  
|[<span data-ttu-id="dec7d-177">sp_syscollector_delete_collector_type &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-177">sp_syscollector_delete_collector_type &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-collector-type-transact-sql)|<span data-ttu-id="dec7d-178">刪除收集器型別。</span><span class="sxs-lookup"><span data-stu-id="dec7d-178">Delete a collector type.</span></span>|  
  
 <span data-ttu-id="dec7d-179">**取得組態資訊**</span><span class="sxs-lookup"><span data-stu-id="dec7d-179">**Getting configuration information**</span></span>  
  
 <span data-ttu-id="dec7d-180">下表描述您可用來取得組態資訊與執行記錄資料的檢視。</span><span class="sxs-lookup"><span data-stu-id="dec7d-180">The following table describes the views that you can use for getting configuration information and execution log data.</span></span>  
  
|<span data-ttu-id="dec7d-181">檢視表名稱</span><span class="sxs-lookup"><span data-stu-id="dec7d-181">View name</span></span>|<span data-ttu-id="dec7d-182">描述</span><span class="sxs-lookup"><span data-stu-id="dec7d-182">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="dec7d-183">syscollector_config_store &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-183">syscollector_config_store &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/syscollector-config-store-transact-sql)|<span data-ttu-id="dec7d-184">取得資料收集器組態。</span><span class="sxs-lookup"><span data-stu-id="dec7d-184">Get data collector configuration.</span></span>|  
|[<span data-ttu-id="dec7d-185">syscollector_collection_items &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-185">syscollector_collection_items &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/syscollector-collection-items-transact-sql)|<span data-ttu-id="dec7d-186">取得收集項資訊。</span><span class="sxs-lookup"><span data-stu-id="dec7d-186">Get collection item information.</span></span>|  
|[<span data-ttu-id="dec7d-187">syscollector_collection_sets &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-187">syscollector_collection_sets &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql)|<span data-ttu-id="dec7d-188">取得收集組資訊。</span><span class="sxs-lookup"><span data-stu-id="dec7d-188">Get collection set information.</span></span>|  
|[<span data-ttu-id="dec7d-189">syscollector_collector_types &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-189">syscollector_collector_types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/syscollector-collector-types-transact-sql)|<span data-ttu-id="dec7d-190">取得收集器型別資訊。</span><span class="sxs-lookup"><span data-stu-id="dec7d-190">Get collector type information.</span></span>|  
|[<span data-ttu-id="dec7d-191">syscollector_execution_log &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-191">syscollector_execution_log &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/syscollector-execution-log-transact-sql)|<span data-ttu-id="dec7d-192">取得有關收集組與封裝執行的資訊。</span><span class="sxs-lookup"><span data-stu-id="dec7d-192">Get information about collection set and package execution.</span></span>|  
|[<span data-ttu-id="dec7d-193">syscollector_execution_stats &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-193">syscollector_execution_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/syscollector-execution-stats-transact-sql)|<span data-ttu-id="dec7d-194">取得有關工作執行的資訊。</span><span class="sxs-lookup"><span data-stu-id="dec7d-194">Get information about task execution.</span></span>|  
|[<span data-ttu-id="dec7d-195">syscollector_execution_log_full &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-195">syscollector_execution_log_full &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/syscollector-execution-log-full-transact-sql)|<span data-ttu-id="dec7d-196">當執行記錄已滿時取得資訊。</span><span class="sxs-lookup"><span data-stu-id="dec7d-196">Get information when the execution log is full.</span></span>|  
  
 <span data-ttu-id="dec7d-197">**設定對管理資料倉儲的存取**</span><span class="sxs-lookup"><span data-stu-id="dec7d-197">**Configuring access to the management data warehouse**</span></span>  
  
 <span data-ttu-id="dec7d-198">下表描述的是您可以用來設定對管理資料倉儲之存取的預存程序。</span><span class="sxs-lookup"><span data-stu-id="dec7d-198">The following table describes the stored procedures that you can use to configure access to the management data warehouse.</span></span>  
  
|<span data-ttu-id="dec7d-199">程序名稱</span><span class="sxs-lookup"><span data-stu-id="dec7d-199">Procedure name</span></span>|<span data-ttu-id="dec7d-200">描述</span><span class="sxs-lookup"><span data-stu-id="dec7d-200">Description</span></span>|  
|--------------------|-----------------|  
|[<span data-ttu-id="dec7d-201">sp_syscollector_set_warehouse_database_name &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-201">sp_syscollector_set_warehouse_database_name &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-warehouse-database-name-transact-sql)|<span data-ttu-id="dec7d-202">針對管理資料倉儲指定連接字串中所定義的資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="dec7d-202">Specify the database name defined in the connection string for the management data warehouse.</span></span>|  
|[<span data-ttu-id="dec7d-203">sp_syscollector_set_warehouse_instance_name &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-203">sp_syscollector_set_warehouse_instance_name &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-warehouse-instance-name-transact-sql)|<span data-ttu-id="dec7d-204">針對管理資料倉儲指定連接字串中所定義的執行個體。</span><span class="sxs-lookup"><span data-stu-id="dec7d-204">Specify the instance defined in the connection string for the management data warehouse.</span></span>|  
  
 <span data-ttu-id="dec7d-205">**設定管理資料倉儲**</span><span class="sxs-lookup"><span data-stu-id="dec7d-205">**Configuring the management data warehouse**</span></span>  
  
 <span data-ttu-id="dec7d-206">下表描述的是您可以用來處理管理資料倉儲組態的預存程序。</span><span class="sxs-lookup"><span data-stu-id="dec7d-206">The following table describes the stored procedures that you can use to work with the management data warehouse configuration.</span></span>  
  
|<span data-ttu-id="dec7d-207">程序名稱</span><span class="sxs-lookup"><span data-stu-id="dec7d-207">Procedure name</span></span>|<span data-ttu-id="dec7d-208">描述</span><span class="sxs-lookup"><span data-stu-id="dec7d-208">Description</span></span>|  
|--------------------|-----------------|  
|[<span data-ttu-id="dec7d-209">core.sp_create_snapshot &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-209">core.sp_create_snapshot &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/core-sp-create-snapshot-transact-sql)|<span data-ttu-id="dec7d-210">在管理資料倉儲中建立集合快照集。</span><span class="sxs-lookup"><span data-stu-id="dec7d-210">Create a collection snapshot in the management data warehouse.</span></span>|  
|[<span data-ttu-id="dec7d-211">core.sp_update_data_source &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-211">core.sp_update_data_source &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/core-sp-update-data-source-transact-sql)|<span data-ttu-id="dec7d-212">更新資料收集的資料來源。</span><span class="sxs-lookup"><span data-stu-id="dec7d-212">Update the data source for data collection.</span></span>|  
|[<span data-ttu-id="dec7d-213">core.sp_add_collector_type &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-213">core.sp_add_collector_type &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/core-sp-add-collector-type-transact-sql)|<span data-ttu-id="dec7d-214">將收集器型別加入到管理資料倉儲。</span><span class="sxs-lookup"><span data-stu-id="dec7d-214">Add a collector type to the management data warehouse.</span></span>|  
|[<span data-ttu-id="dec7d-215">core.sp_remove_collector_type &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-215">core.sp_remove_collector_type &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/core-sp-remove-collector-type-transact-sql)|<span data-ttu-id="dec7d-216">從管理資料倉儲中移除收集器型別。</span><span class="sxs-lookup"><span data-stu-id="dec7d-216">Remove a collector type from the management data warehouse.</span></span>|  
|[<span data-ttu-id="dec7d-217">core.sp_purge_data &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-217">core.sp_purge_data &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/core-sp-purge-data-transact-sql)|<span data-ttu-id="dec7d-218">從管理資料倉儲中刪除資料。</span><span class="sxs-lookup"><span data-stu-id="dec7d-218">Delete data from the management data warehouse.</span></span>|  
  
 <span data-ttu-id="dec7d-219">**使用上傳封裝**</span><span class="sxs-lookup"><span data-stu-id="dec7d-219">**Working with upload packages**</span></span>  
  
 <span data-ttu-id="dec7d-220">下表描述的是您可以用來處理上傳封裝的預存程序。</span><span class="sxs-lookup"><span data-stu-id="dec7d-220">The following table describes the stored procedures that you can use to work with upload packages.</span></span>  
  
|<span data-ttu-id="dec7d-221">程序名稱</span><span class="sxs-lookup"><span data-stu-id="dec7d-221">Procedure name</span></span>|<span data-ttu-id="dec7d-222">描述</span><span class="sxs-lookup"><span data-stu-id="dec7d-222">Description</span></span>|  
|--------------------|-----------------|  
|[<span data-ttu-id="dec7d-223">sp_syscollector_set_cache_window &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-223">sp_syscollector_set_cache_window &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-cache-window-transact-sql)|<span data-ttu-id="dec7d-224">設定資料上傳的重試次數。</span><span class="sxs-lookup"><span data-stu-id="dec7d-224">Configure the number of data upload retries.</span></span>|  
|[<span data-ttu-id="dec7d-225">sp_syscollector_set_cache_directory &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-225">sp_syscollector_set_cache_directory &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-set-cache-directory-transact-sql)|<span data-ttu-id="dec7d-226">指定上傳重試之間的資料暫存儲存位置。</span><span class="sxs-lookup"><span data-stu-id="dec7d-226">Specify temporary storage for data between upload retries.</span></span>|  
  
 <span data-ttu-id="dec7d-227">**使用資料收集執行記錄**</span><span class="sxs-lookup"><span data-stu-id="dec7d-227">**Working with the data collection execution log**</span></span>  
  
 <span data-ttu-id="dec7d-228">下表描述的是您可以用來處理資料收集執行記錄的預存程序。</span><span class="sxs-lookup"><span data-stu-id="dec7d-228">The following table describes the stored procedures that you can use to work with the data collection execution log.</span></span>  
  
|<span data-ttu-id="dec7d-229">程序名稱</span><span class="sxs-lookup"><span data-stu-id="dec7d-229">Procedure name</span></span>|<span data-ttu-id="dec7d-230">描述</span><span class="sxs-lookup"><span data-stu-id="dec7d-230">Description</span></span>|  
|--------------------|-----------------|  
|[<span data-ttu-id="dec7d-231">sp_syscollector_delete_execution_log_tree &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-231">sp_syscollector_delete_execution_log_tree &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-stored-procedures/sp-syscollector-delete-execution-log-tree-transact-sql)|<span data-ttu-id="dec7d-232">從執行記錄中刪除收集組項目。</span><span class="sxs-lookup"><span data-stu-id="dec7d-232">Delete collection set entries from the execution log.</span></span>|  
  
### <a name="functions"></a><span data-ttu-id="dec7d-233">函數</span><span class="sxs-lookup"><span data-stu-id="dec7d-233">Functions</span></span>  
 <span data-ttu-id="dec7d-234">下表描述的是您可以用來取得執行和追蹤資訊的函數。</span><span class="sxs-lookup"><span data-stu-id="dec7d-234">The following table describes the functions that you can use to obtain execution and trace information.</span></span>  
  
|<span data-ttu-id="dec7d-235">函式名稱</span><span class="sxs-lookup"><span data-stu-id="dec7d-235">Function name</span></span>|<span data-ttu-id="dec7d-236">描述</span><span class="sxs-lookup"><span data-stu-id="dec7d-236">Description</span></span>|  
|-------------------|-----------------|  
|[<span data-ttu-id="dec7d-237">fn_syscollector_get_execution_details &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-237">fn_syscollector_get_execution_details &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/fn-syscollector-get-execution-details-transact-sql)|<span data-ttu-id="dec7d-238">取得特定封裝的 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 執行記錄資料。</span><span class="sxs-lookup"><span data-stu-id="dec7d-238">Get [!INCLUDE[ssIS](../../includes/ssis-md.md)] execution log data for a specific package.</span></span>|  
|[<span data-ttu-id="dec7d-239">fn_syscollector_get_execution_stats &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-239">fn_syscollector_get_execution_stats &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/fn-syscollector-get-execution-stats-transact-sql)|<span data-ttu-id="dec7d-240">取得收集組或封裝的執行統計資料。</span><span class="sxs-lookup"><span data-stu-id="dec7d-240">Get execution statistics for a collection set or package.</span></span> <span data-ttu-id="dec7d-241">這些資訊包含所記錄的錯誤。</span><span class="sxs-lookup"><span data-stu-id="dec7d-241">This information includes errors that are logged.</span></span>|  
|[<span data-ttu-id="dec7d-242">snapshots.fn_trace_getdata &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="dec7d-242">snapshots.fn_trace_getdata &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-functions/snapshots-fn-trace-getdata-transact-sql)|<span data-ttu-id="dec7d-243">取得使用一般 SQL 追蹤收集器型別來收集資料時所記錄的事件。</span><span class="sxs-lookup"><span data-stu-id="dec7d-243">Get the events that are logged when the Generic SQL Trace collector type is used to collect data.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dec7d-244">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dec7d-244">See Also</span></span>  
 <span data-ttu-id="dec7d-245">[執行預存程式](../stored-procedures/execute-a-stored-procedure.md) </span><span class="sxs-lookup"><span data-stu-id="dec7d-245">[Execute a Stored Procedure](../stored-procedures/execute-a-stored-procedure.md) </span></span>  
 <span data-ttu-id="dec7d-246">[使用 SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="dec7d-246">[Use SQL Server Management Studio](../../database-engine/use-sql-server-management-studio.md) </span></span>  
 <span data-ttu-id="dec7d-247">[[資料收集]](data-collection.md)</span><span class="sxs-lookup"><span data-stu-id="dec7d-247">[Data Collection](data-collection.md)</span></span>  
  
  
