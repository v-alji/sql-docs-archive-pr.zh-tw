---
title: 建立和測試分類使用者定義函式 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, classifier function create
- classifier function [SQL Server], test
- classifier function [SQL Server], create
- Resource Governor, classifier function test
ms.assetid: 7866b3c9-385b-40c6-aca5-32d3337032be
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 1b8e5371762e38cf2b3ac8c1d506b467dcfa7e3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699415"
---
# <a name="create-and-test-a-classifier-user-defined-function"></a><span data-ttu-id="0cd63-102">建立和測試分類使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="0cd63-102">Create and Test a Classifier User-Defined Function</span></span>
  <span data-ttu-id="0cd63-103">本主題說明如何建立和測試分類使用者定義函數 (UDF)。</span><span class="sxs-lookup"><span data-stu-id="0cd63-103">This topic shows how to create and test a classifier user-defined function (UDF).</span></span> <span data-ttu-id="0cd63-104">這些步驟將包含在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢編輯器中執行 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="0cd63-104">The steps involve executing [!INCLUDE[tsql](../../includes/tsql-md.md)] statements in the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] Query Editor.</span></span>  
  
 <span data-ttu-id="0cd63-105">下列程序所示的範例會說明建立相當複雜之分類使用者定義函數的可能性。</span><span class="sxs-lookup"><span data-stu-id="0cd63-105">The example shown in the following procedure illustrates the possibilities for creating a fairly complex classifier user-defined function.</span></span>  
  
 <span data-ttu-id="0cd63-106">在我們的範例中：</span><span class="sxs-lookup"><span data-stu-id="0cd63-106">In our example:</span></span>  
  
-   <span data-ttu-id="0cd63-107">建立資源集區 (pProductionProcessing) 和工作負載群組 (gProductionProcessing)，以便在指定的時間範圍內進行生產處理。</span><span class="sxs-lookup"><span data-stu-id="0cd63-107">A resource pool (pProductionProcessing) and workload group (gProductionProcessing) are created for production processing during a specified time range.</span></span>  
  
-   <span data-ttu-id="0cd63-108">建立資源集區 (pOffHoursProcessing) 和工作負載群組 (gOffHoursProcessing)，以便處理不符合生產處理需求的連接。</span><span class="sxs-lookup"><span data-stu-id="0cd63-108">A resource pool (pOffHoursProcessing) and workload group (gOffHoursProcessing) are created for handling connections that do not meet the requirements for production processing.</span></span>  
  
-   <span data-ttu-id="0cd63-109">在 master 中建立資料表 (TblClassificationTimeTable)，以便保存可以針對登入時間評估的開始和結束時間。</span><span class="sxs-lookup"><span data-stu-id="0cd63-109">A table (TblClassificationTimeTable) is created in master to hold start and end times that can be evaluated against a login time.</span></span> <span data-ttu-id="0cd63-110">這份資料表必須建立在 master 中，因為資源管理員會使用分類函數的結構描述繫結。</span><span class="sxs-lookup"><span data-stu-id="0cd63-110">This must be created in master because Resource Governor uses schema binding for classifier functions.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="0cd63-111">最佳作法是避免將龐大且經常更新的資料表儲存在 master 中。</span><span class="sxs-lookup"><span data-stu-id="0cd63-111">As a best practice, you should not store large, frequently updated tables in master.</span></span>  
  
 <span data-ttu-id="0cd63-112">分類函數會延長登入時間。</span><span class="sxs-lookup"><span data-stu-id="0cd63-112">The classifier function extends the login time.</span></span> <span data-ttu-id="0cd63-113">任何過度複雜的函數都可能會導致登入逾時或降低快速連接的速度。</span><span class="sxs-lookup"><span data-stu-id="0cd63-113">An overly complex function can cause logins to time out or slow down fast connections.</span></span>  
  
### <a name="to-create-the-classifier-user-defined-function"></a><span data-ttu-id="0cd63-114">建立分類使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="0cd63-114">To create the classifier user-defined function</span></span>  
  
1.  <span data-ttu-id="0cd63-115">建立並設定新的資源集區和工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="0cd63-115">Create and configure the new resource pools and workload groups.</span></span> <span data-ttu-id="0cd63-116">將每個工作負載群組指派給適當的資源集區。</span><span class="sxs-lookup"><span data-stu-id="0cd63-116">Assign each workload group to the appropriate resource pool.</span></span>  
  
    ```  
    --- Create a resource pool for production processing  
    --- and set limits.  
    USE master  
    GO  
    CREATE RESOURCE POOL pProductionProcessing  
    WITH  
    (  
         MAX_CPU_PERCENT = 100,  
         MIN_CPU_PERCENT = 50  
    )  
    GO  
    --- Create a workload group for production processing  
    --- and configure the relative importance.  
    CREATE WORKLOAD GROUP gProductionProcessing  
    WITH  
    (  
         IMPORTANCE = MEDIUM  
    )  
    --- Assign the workload group to the production processing  
    --- resource pool.  
    USING pProductionProcessing  
    GO  
    --- Create a resource pool for off-hours processing  
    --- and set limits.  
  
    CREATE RESOURCE POOL pOffHoursProcessing  
    WITH  
    (  
         MAX_CPU_PERCENT = 50,  
         MIN_CPU_PERCENT = 0  
    )  
    GO  
    --- Create a workload group for off-hours processing  
    --- and configure the relative importance.  
    CREATE WORKLOAD GROUP gOffHoursProcessing  
    WITH  
    (  
         IMPORTANCE = LOW  
    )  
    --- Assign the workload group to the off-hours processing  
    --- resource pool.  
    USING pOffHoursProcessing  
    GO  
    ```  
  
2.  <span data-ttu-id="0cd63-117">更新記憶體中組態。</span><span class="sxs-lookup"><span data-stu-id="0cd63-117">Update the in-memory configuration.</span></span>  
  
    ```  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
    ```  
  
3.  <span data-ttu-id="0cd63-118">建立資料表並定義生產處理時間範圍的開始和結束時間。</span><span class="sxs-lookup"><span data-stu-id="0cd63-118">Create a table and define the start and end times for the production processing time range.</span></span>  
  
    ```  
    USE master  
    GO  
    CREATE TABLE tblClassificationTimeTable  
    (  
         strGroupName     sysname          not null,  
         tStartTime       time              not null,  
         tEndTime         time              not null  
    )  
    GO  
    --- Add time values that the classifier will use to  
    --- determine the workload group for a session.  
    INSERT into tblClassificationTimeTable VALUES('gProductionProcessing', '6:35 AM', '6:15 PM')  
    go  
    ```  
  
4.  <span data-ttu-id="0cd63-119">建立使用時間函數和值 (可針對查閱資料表中的時間評估) 的分類函數。</span><span class="sxs-lookup"><span data-stu-id="0cd63-119">Create the classifier function that uses time functions and values that can be evaluated against the times in the lookup table.</span></span> <span data-ttu-id="0cd63-120">如需在分類函式使用中使用查閱資料表的詳細資訊，請參閱本主題中的＜在分類函式中使用查閱資料表的最佳做法＞。</span><span class="sxs-lookup"><span data-stu-id="0cd63-120">For information about using Lookup Tables in a classifier function, see "Best practices for using Lookup Tables in a classifier function" in this topic.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] <span data-ttu-id="0cd63-121">導入了一組擴充的日期與時間資料類型和函數。</span><span class="sxs-lookup"><span data-stu-id="0cd63-121">introduced an expanded set of date and time data types and functions.</span></span> <span data-ttu-id="0cd63-122">如需詳細資訊，請參閱[日期和時間資料類型與函數 &#40;Transact-SQL&#41;](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="0cd63-122">For more information, see [Date and Time Data Types and Functions &#40;Transact-SQL&#41;](/sql/t-sql/functions/date-and-time-data-types-and-functions-transact-sql).</span></span>  
  
    ```  
    CREATE FUNCTION fnTimeClassifier()  
    RETURNS sysname  
    WITH SCHEMABINDING  
    AS  
    BEGIN  
         DECLARE @strGroup sysname  
         DECLARE @loginTime time  
         SET @loginTime = CONVERT(time,GETDATE())  
         SELECT TOP 1 @strGroup = strGroupName  
              FROM dbo.tblClassificationTimeTable  
              WHERE tStartTime <= @loginTime and tEndTime >= @loginTime  
         IF(@strGroup is not null)  
         BEGIN  
              RETURN @strGroup  
         END  
    --- Use the default workload group if there is no match  
    --- on the lookup.  
         RETURN N'gOffHoursProcessing'  
    END  
    GO  
    ```  
  
5.  <span data-ttu-id="0cd63-123">註冊此分類函數並更新記憶體中組態。</span><span class="sxs-lookup"><span data-stu-id="0cd63-123">Register the classifier function and update the in-memory configuration.</span></span>  
  
    ```  
    ALTER RESOURCE GOVERNOR with (CLASSIFIER_FUNCTION = dbo.fnTimeClassifier)  
    ALTER RESOURCE GOVERNOR RECONFIGURE  
    GO  
    ```  
  
### <a name="to-verify-the-resource-pools-workload-groups-and-the-classifier-user-defined-function"></a><span data-ttu-id="0cd63-124">確認資源集區、工作負載群組和分類使用者定義函數</span><span class="sxs-lookup"><span data-stu-id="0cd63-124">To verify the resource pools, workload groups, and the classifier user-defined function</span></span>  
  
1.  <span data-ttu-id="0cd63-125">使用下列查詢來取得資源集區和工作負載群組組態。</span><span class="sxs-lookup"><span data-stu-id="0cd63-125">Obtain the resource pool and workload group configuration by using the following query.</span></span>  
  
    ```  
    USE master  
    SELECT * FROM sys.resource_governor_resource_pools  
    SELECT * FROM sys.resource_governor_workload_groups  
    GO  
    ```  
  
2.  <span data-ttu-id="0cd63-126">使用下列查詢來確認分類函數存在而且已啟用。</span><span class="sxs-lookup"><span data-stu-id="0cd63-126">Verify that the classifier function exists and is enabled by using the following queries.</span></span>  
  
    ```  
    --- Get the classifier function Id and state (enabled).  
    SELECT * FROM sys.resource_governor_configuration  
    GO  
    --- Get the classifer function name and the name of the schema  
    --- that it is bound to.  
    SELECT   
          object_schema_name(classifier_function_id) AS [schema_name],  
          object_name(classifier_function_id) AS [function_name]  
    FROM sys.dm_resource_governor_configuration  
  
    ```  
  
3.  <span data-ttu-id="0cd63-127">使用下列查詢來取得資源集區和工作負載群組的目前執行階段資料。</span><span class="sxs-lookup"><span data-stu-id="0cd63-127">Obtain the current runtime data for the resource pools and workload groups by using the following query.</span></span>  
  
    ```  
    SELECT * FROM sys.dm_resource_governor_resource_pools  
    SELECT * FROM sys.dm_resource_governor_workload_groups  
    GO  
    ```  
  
4.  <span data-ttu-id="0cd63-128">使用下列查詢來了解每個群組中含有哪些工作階段。</span><span class="sxs-lookup"><span data-stu-id="0cd63-128">Find out what sessions are in each group by using the following query.</span></span>  
  
    ```  
    SELECT s.group_id, CAST(g.name as nvarchar(20)), s.session_id, s.login_time, CAST(s.host_name as nvarchar(20)), CAST(s.program_name AS nvarchar(20))  
              FROM sys.dm_exec_sessions s  
         INNER JOIN sys.dm_resource_governor_workload_groups g  
              ON g.group_id = s.group_id  
    ORDER BY g.name  
    GO  
    ```  
  
5.  <span data-ttu-id="0cd63-129">使用下列查詢來了解每個群組中含有哪些要求。</span><span class="sxs-lookup"><span data-stu-id="0cd63-129">Find out which requests are in each group by using the following query.</span></span>  
  
    ```  
    SELECT r.group_id, g.name, r.status, r.session_id, r.request_id, r.start_time, r.command, r.sql_handle, t.text   
               FROM sys.dm_exec_requests r  
         INNER JOIN sys.dm_resource_governor_workload_groups g  
                ON g.group_id = r.group_id  
         CROSS APPLY sys.dm_exec_sql_text(r.sql_handle) AS t  
    ORDER BY g.name  
    GO  
    ```  
  
6.  <span data-ttu-id="0cd63-130">使用下列查詢來了解哪些要求正在分類中執行。</span><span class="sxs-lookup"><span data-stu-id="0cd63-130">Find out what requests are running in the classifier by using the following query.</span></span>  
  
    ```  
    SELECT s.group_id, g.name, s.session_id, s.login_time, s.host_name, s.program_name   
               FROM sys.dm_exec_sessions s  
         INNER JOIN sys.dm_resource_governor_workload_groups g  
               ON g.group_id = s.group_id  
                     AND 'preconnect' = s.status  
    ORDER BY g.name  
    GO  
  
    SELECT r.group_id, g.name, r.status, r.session_id, r.request_id, r.start_time, r.command, r.sql_handle, t.text   
               FROM sys.dm_exec_requests r  
         INNER JOIN sys.dm_resource_governor_workload_groups g  
               ON g.group_id = r.group_id  
                     AND 'preconnect' = r.status  
         CROSS APPLY sys.dm_exec_sql_text(r.sql_handle) AS t  
    ORDER BY g.name  
    GO  
    ```  
  
### <a name="best-practices-for-using-lookup-tables-in-a-classifier-function"></a><span data-ttu-id="0cd63-131">在分類函數中使用查閱資料表的最佳做法</span><span class="sxs-lookup"><span data-stu-id="0cd63-131">Best practices for using Lookup Tables in a classifier function</span></span>  
  
1.  <span data-ttu-id="0cd63-132">除非絕對必要，否則不要使用查閱資料表。</span><span class="sxs-lookup"><span data-stu-id="0cd63-132">Do not use a lookup table unless it is absolutely necessary.</span></span> <span data-ttu-id="0cd63-133">如果您需要使用查閱資料表，它可能以硬編碼的方式將本身寫入函數中；不過它需要與分類函數的複雜度和動態變更相互平衡。</span><span class="sxs-lookup"><span data-stu-id="0cd63-133">If you need to use a lookup table, it can be hard coded into the function itself; however, this needs to be balanced with the complexity and dynamic changes of the classifier function.</span></span>  
  
2.  <span data-ttu-id="0cd63-134">限制針對查閱資料庫執行的 I/O。</span><span class="sxs-lookup"><span data-stu-id="0cd63-134">Limit the I/O performed for lookup tables.</span></span>  
  
    1.  <span data-ttu-id="0cd63-135">使用 TOP 1 只會傳回一個資料列。</span><span class="sxs-lookup"><span data-stu-id="0cd63-135">Use the TOP 1 to return only one row.</span></span>  
  
    2.  <span data-ttu-id="0cd63-136">最小化資料表中的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="0cd63-136">Minimize the number of rows in the table.</span></span>  
  
    3.  <span data-ttu-id="0cd63-137">在單一頁面或是盡量少的頁面上顯示資料表的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="0cd63-137">Make all rows of the table exist on a single page, or a small number of pages.</span></span>  
  
    4.  <span data-ttu-id="0cd63-138">確認使用索引搜尋作業找到的資料列盡可能使用多個搜尋資料行。</span><span class="sxs-lookup"><span data-stu-id="0cd63-138">Confirm that rows found using the Index Seek operations use as many seeking columns as possible.</span></span>  
  
    5.  <span data-ttu-id="0cd63-139">如果您考慮透過聯結使用多個資料表，則反正規化為單一資料表。</span><span class="sxs-lookup"><span data-stu-id="0cd63-139">De-normalize to a single table if you are considering using multiple tables with joins.</span></span>  
  
3.  <span data-ttu-id="0cd63-140">避免在查閱資料表上進行封鎖。</span><span class="sxs-lookup"><span data-stu-id="0cd63-140">Prevent blocking on the lookup table.</span></span>  
  
    1.  <span data-ttu-id="0cd63-141">使用 `NOLOCK` 提示避免鎖定，或是在函數中使用最大值 1000 毫秒的 `SET LOCK_TIMEOUT` 。</span><span class="sxs-lookup"><span data-stu-id="0cd63-141">Use the `NOLOCK` hint to prevent blocking or use `SET LOCK_TIMEOUT` in the function with a maximum value of 1000 milliseconds.</span></span>  
  
    2.  <span data-ttu-id="0cd63-142">資料表必須在 master 資料庫中</span><span class="sxs-lookup"><span data-stu-id="0cd63-142">Table(s) must exist in the master database.</span></span> <span data-ttu-id="0cd63-143">(master 資料庫是在用戶端電腦嘗試連線時，唯一保證可以復原的資料庫)。</span><span class="sxs-lookup"><span data-stu-id="0cd63-143">(The master database is the only database that is guaranteed to be recovered when the client computers attempt to connect).</span></span>  
  
    3.  <span data-ttu-id="0cd63-144">務必以結構描述完整限定資料庫名稱。</span><span class="sxs-lookup"><span data-stu-id="0cd63-144">Always fully-qualify the table name with the schema.</span></span> <span data-ttu-id="0cd63-145">資料庫名稱並非必要，因為一定要是 master 資料庫。</span><span class="sxs-lookup"><span data-stu-id="0cd63-145">The database name is not necessary since it has to be the master database.</span></span>  
  
    4.  <span data-ttu-id="0cd63-146">資料表上沒有觸發程序。</span><span class="sxs-lookup"><span data-stu-id="0cd63-146">No triggers on the table.</span></span>  
  
    5.  <span data-ttu-id="0cd63-147">如果您要更新資料表內容，則務必使用快照隔離等級交易避免寫入器封鎖讀取器。</span><span class="sxs-lookup"><span data-stu-id="0cd63-147">If you are updating the table contents, make sure to use a snapshot isolation level transaction to prevent Writer blocking Readers.</span></span> <span data-ttu-id="0cd63-148">請注意，使用 `NOLOCK` 提示也可以防止這種情況發生。</span><span class="sxs-lookup"><span data-stu-id="0cd63-148">Note that using the `NOLOCK` hint should also mitigate this.</span></span>  
  
    6.  <span data-ttu-id="0cd63-149">如有可能，變更資料表內容時，請停用分類函數。</span><span class="sxs-lookup"><span data-stu-id="0cd63-149">If possible, disable the classifier function when changing the table contents.</span></span>  
  
        > [!WARNING]  
        >  <span data-ttu-id="0cd63-150">以下是我們建議的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="0cd63-150">We highly recommend following these best practices.</span></span> <span data-ttu-id="0cd63-151">如果有問題導致無法遵循下列最佳做法，建議您連絡 Microsoft 支援部門，以便主動避免未來發生任何問題。</span><span class="sxs-lookup"><span data-stu-id="0cd63-151">If there are issues that prevent you from following the best practices, we recommend that you contact Microsoft Support so that you can proactively prevent any future problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cd63-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0cd63-152">See Also</span></span>  
 <span data-ttu-id="0cd63-153">[資源管理員](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="0cd63-153">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="0cd63-154">[啟用資源管理員](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="0cd63-154">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="0cd63-155">[資源管理員資源集區](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="0cd63-155">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="0cd63-156">[資源管理員工作負載群組](resource-governor-workload-group.md) </span><span class="sxs-lookup"><span data-stu-id="0cd63-156">[Resource Governor Workload Group](resource-governor-workload-group.md) </span></span>  
 <span data-ttu-id="0cd63-157">[使用範本來設定資源管理員](configure-resource-governor-using-a-template.md) </span><span class="sxs-lookup"><span data-stu-id="0cd63-157">[Configure Resource Governor Using a Template](configure-resource-governor-using-a-template.md) </span></span>  
 <span data-ttu-id="0cd63-158">[檢視資源管理員屬性](view-resource-governor-properties.md) </span><span class="sxs-lookup"><span data-stu-id="0cd63-158">[View Resource Governor Properties](view-resource-governor-properties.md) </span></span>  
 <span data-ttu-id="0cd63-159">[ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0cd63-159">[ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-resource-governor-transact-sql) </span></span>  
 <span data-ttu-id="0cd63-160">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0cd63-160">[CREATE RESOURCE POOL &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-resource-pool-transact-sql) </span></span>  
 <span data-ttu-id="0cd63-161">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0cd63-161">[CREATE WORKLOAD GROUP &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-workload-group-transact-sql) </span></span>  
 <span data-ttu-id="0cd63-162">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="0cd63-162">[CREATE FUNCTION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-function-transact-sql) </span></span>  
 [<span data-ttu-id="0cd63-163">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="0cd63-163">ALTER RESOURCE GOVERNOR &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/alter-resource-governor-transact-sql)  
  
  
