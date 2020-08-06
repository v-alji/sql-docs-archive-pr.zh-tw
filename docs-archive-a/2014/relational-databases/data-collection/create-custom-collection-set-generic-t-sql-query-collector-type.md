---
title: 建立使用一般 T-SQL 查詢收集器型別 (Transact-sql) 的自訂收集組 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- T-SQL Query collector type
- collection sets [SQL Server], creating custom
ms.assetid: 6b06db5b-cfdc-4ce0-addd-ec643460605b
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: ab21ad5fd65556dec639fd5ca6999d23e2de673b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597876"
---
# <a name="create-a-custom-collection-set-that-uses-the-generic-t-sql-query-collector-type-transact-sql"></a><span data-ttu-id="d3517-102">建立使用一般 T-SQL 查詢收集器型別的自訂收集組 (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="d3517-102">Create a Custom Collection Set That Uses the Generic T-SQL Query Collector Type (Transact-SQL)</span></span>
  <span data-ttu-id="d3517-103">您可以使用資料收集器所提供的預存程序，建立包含使用一般 T-SQL 查詢收集器型別之收集項的自訂收集組。</span><span class="sxs-lookup"><span data-stu-id="d3517-103">You can create a custom collection set with collection items that use the Generic T-SQL Query collector type by using the stored procedures that are provided with the data collector.</span></span> <span data-ttu-id="d3517-104">完成這項工作需要在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 中使用查詢編輯器來進行以下程序：</span><span class="sxs-lookup"><span data-stu-id="d3517-104">Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] to carry out the following procedures:</span></span>  
  
-   <span data-ttu-id="d3517-105">設定上傳排程。</span><span class="sxs-lookup"><span data-stu-id="d3517-105">Configure upload schedules.</span></span>  
  
-   <span data-ttu-id="d3517-106">定義和建立收集組。</span><span class="sxs-lookup"><span data-stu-id="d3517-106">Define and create the collection set.</span></span>  
  
-   <span data-ttu-id="d3517-107">定義和建立收集項。</span><span class="sxs-lookup"><span data-stu-id="d3517-107">Define and create a collection item.</span></span>  
  
-   <span data-ttu-id="d3517-108">確認收集組與收集項確實存在。</span><span class="sxs-lookup"><span data-stu-id="d3517-108">Verify that the collection set and collection items exist.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3517-109">在您建立自訂收集組之前，必須先設定資料收集參數。</span><span class="sxs-lookup"><span data-stu-id="d3517-109">Before you create a custom collection set, you must configure data collection parameters.</span></span> <span data-ttu-id="d3517-110">如需詳細資訊，請參閱[設定資料收集參數 &#40;Transact-SQL&#41;](configure-data-collection-parameters-transact-sql.md)。</span><span class="sxs-lookup"><span data-stu-id="d3517-110">For more information, see [Configure Data Collection Parameters &#40;Transact-SQL&#41;](configure-data-collection-parameters-transact-sql.md).</span></span>  
  
### <a name="define-and-create-the-collection-set"></a><span data-ttu-id="d3517-111">定義和建立收集組</span><span class="sxs-lookup"><span data-stu-id="d3517-111">Define and create the collection set</span></span>  
  
1.  <span data-ttu-id="d3517-112">使用 sp_syscollector_create_collection_set 預存程序來定義新的收集組。</span><span class="sxs-lookup"><span data-stu-id="d3517-112">Define a new collection set using the sp_syscollector_create_collection_set stored procedure.</span></span>  
  
    ```  
    USE msdb;  
    DECLARE @collection_set_id int;  
    DECLARE @collection_set_uid uniqueidentifier;  
    EXEC sp_syscollector_create_collection_set   
        @name=N'DMV Test 1',   
        @collection_mode=0,   
        @description=N'This is a test collection set',   
        @logging_level=1,   
        @days_until_expiration=14,   
        @schedule_name=N'CollectorSchedule_Every_15min',   
        @collection_set_id=@collection_set_id OUTPUT,   
        @collection_set_uid=@collection_set_uid OUTPUT;  
    SELECT @collection_set_id, @collection_set_uid;  
    ```  
  
     <span data-ttu-id="d3517-113">收集模式可以設定為 0 (快取) 或 1 (非快取)。</span><span class="sxs-lookup"><span data-stu-id="d3517-113">The collection mode can be set to either 0 (cached) or to 1 (non-cached).</span></span>  
  
     <span data-ttu-id="d3517-114">記錄層級可以設定為 0、1 或 2。</span><span class="sxs-lookup"><span data-stu-id="d3517-114">The logging level can be set to 0, 1 or 2.</span></span>  
  
     <span data-ttu-id="d3517-115">下面是資料收集器所提供的預先設定排程：</span><span class="sxs-lookup"><span data-stu-id="d3517-115">The following preconfigured schedules are provided with the data collector:</span></span>  
  
    -   <span data-ttu-id="d3517-116">CollectorSchedule_Every_5min</span><span class="sxs-lookup"><span data-stu-id="d3517-116">CollectorSchedule_Every_5min</span></span>  
  
    -   <span data-ttu-id="d3517-117">CollectorSchedule_Every_10min</span><span class="sxs-lookup"><span data-stu-id="d3517-117">CollectorSchedule_Every_10min</span></span>  
  
    -   <span data-ttu-id="d3517-118">CollectorSchedule_Every_15min</span><span class="sxs-lookup"><span data-stu-id="d3517-118">CollectorSchedule_Every_15min</span></span>  
  
    -   <span data-ttu-id="d3517-119">CollectorSchedule_Every_30min</span><span class="sxs-lookup"><span data-stu-id="d3517-119">CollectorSchedule_Every_30min</span></span>  
  
    -   <span data-ttu-id="d3517-120">CollectorSchedule_Every_60min</span><span class="sxs-lookup"><span data-stu-id="d3517-120">CollectorSchedule_Every_60min</span></span>  
  
    -   <span data-ttu-id="d3517-121">CollectorSchedule_Every_6h</span><span class="sxs-lookup"><span data-stu-id="d3517-121">CollectorSchedule_Every_6h</span></span>  
  
     <span data-ttu-id="d3517-122">如果您不想要使用所提供的其中一個排程，可以建立新的排程，然後將它用於收集組。</span><span class="sxs-lookup"><span data-stu-id="d3517-122">If you do not want to use one of the schedules that are provided, you can create a new schedule and use it for the collection set.</span></span> <span data-ttu-id="d3517-123">如需詳細資訊，請參閱 [建立及附加排程至作業](../../ssms/agent/create-and-attach-schedules-to-jobs.md)。</span><span class="sxs-lookup"><span data-stu-id="d3517-123">For more information, see [Create and Attach Schedules to Jobs](../../ssms/agent/create-and-attach-schedules-to-jobs.md).</span></span>  
  
### <a name="define-and-create-a-collection-item"></a><span data-ttu-id="d3517-124">定義和建立收集項</span><span class="sxs-lookup"><span data-stu-id="d3517-124">Define and create a collection item</span></span>  
  
1.  <span data-ttu-id="d3517-125">因為新的收集項是以已經安裝的一般收集器型別為基礎，所以您可以執行下列程式碼，將 GUID 設定為對應至一般 T-SQL 查詢收集器型別。</span><span class="sxs-lookup"><span data-stu-id="d3517-125">Because the new collection item is based on a generic collector type that is already installed, you can run the following code to set the GUID to correspond to the Generic T-SQL Query collector type.</span></span>  
  
    ```sql  
    DECLARE @collector_type_uid uniqueidentifier;  
    SELECT @collector_type_uid = collector_type_uid FROM [msdb].[dbo].[syscollector_collector_types]   
    WHERE name = N'Generic T-SQL Query Collector Type';  
    DECLARE @collection_item_id int;  
    ```  
  
2.  <span data-ttu-id="d3517-126">使用 sp_syscollector_create_collection_item 預存程序來建立收集項。</span><span class="sxs-lookup"><span data-stu-id="d3517-126">Use the sp_syscollector_create_collection_item stored procedure to create the collection item.</span></span> <span data-ttu-id="d3517-127">宣告收集項的結構描述，好讓它對應到一般 T-SQL 查詢收集器型別所需的結構描述。</span><span class="sxs-lookup"><span data-stu-id="d3517-127">Declare the schema for the collection item so it maps to the schema that is required for the Generic T-SQL Query collector type.</span></span>  
  
    ```sql  
    EXEC sp_syscollector_create_collection_item   
        @name=N'Query Stats - Test 1',   
        @parameters=N'  
            <ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
            <Query>  
            <Value>SELECT * FROM sys.dm_exec_query_stats</Value>  
            <OutputTable>dm_exec_query_stats</OutputTable>  
            </Query>  
            </ns:TSQLQueryCollector>',   
        @collection_item_id=@collection_item_id OUTPUT,   
        @frequency=5,   
        @collection_set_id=@collection_set_id,   
        @collector_type_uid=@collector_type_uid;  
    SELECT @collection_item_id;  
    ```  
  
### <a name="verify-that-the-new-collection-set-and-collection-item-exist"></a><span data-ttu-id="d3517-128">確認新的收集組與收集項確實存在</span><span class="sxs-lookup"><span data-stu-id="d3517-128">Verify that the new collection set and collection item exist</span></span>  
  
1.  <span data-ttu-id="d3517-129">在啟動新的收集組之前，請執行下列查詢來確認新的收集組和它的收集項確實已經建立。</span><span class="sxs-lookup"><span data-stu-id="d3517-129">Before starting the new collection set, run the following query to verify that the new collection set and its collection item have been created.</span></span>  
  
    ```sql  
    USE msdb;  
    SELECT * FROM syscollector_collection_sets;  
    SELECT * FROM syscollector_collection_items;  
    GO  
    ```  
  
     <span data-ttu-id="d3517-130">您也可以在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中進行目視檢查。</span><span class="sxs-lookup"><span data-stu-id="d3517-130">You can also do a visual check in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="d3517-131">在物件總管中，展開 [管理]  節點，然後展開 [資料收集]  。</span><span class="sxs-lookup"><span data-stu-id="d3517-131">In Object Explorer, expand the **Management** node, and then expand **Data Collection**.</span></span> <span data-ttu-id="d3517-132">將會顯示新的收集組。</span><span class="sxs-lookup"><span data-stu-id="d3517-132">The new collection set will be displayed.</span></span> <span data-ttu-id="d3517-133">收集組的紅色圓圈圖示是表示此收集組已經停止。</span><span class="sxs-lookup"><span data-stu-id="d3517-133">The red circle icon for the collection set indicates that the collection set is stopped.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3517-134">範例</span><span class="sxs-lookup"><span data-stu-id="d3517-134">Example</span></span>  
 <span data-ttu-id="d3517-135">下列程式碼範例會結合上述步驟所列的範例。</span><span class="sxs-lookup"><span data-stu-id="d3517-135">The following code sample combines the examples that are documented in the previous steps.</span></span> <span data-ttu-id="d3517-136">請注意，這時針對收集項所設定的收集頻率 (5 秒) 將會遭到忽略，因為收集組的收集模式設定為 0，而這是快取模式。</span><span class="sxs-lookup"><span data-stu-id="d3517-136">Note that the collection frequency that is set for the collection item (5 seconds) is ignored because the collection set collection mode is set to 0, which is cached mode.</span></span> <span data-ttu-id="d3517-137">如需相關資訊，請參閱 [Data Collection](data-collection.md)。</span><span class="sxs-lookup"><span data-stu-id="d3517-137">For more information, see [Data Collection](data-collection.md).</span></span>  
  
```sql  
USE msdb;  
  
DECLARE @collection_set_id int;  
DECLARE @collection_set_uid uniqueidentifier  
  
EXEC dbo.sp_syscollector_create_collection_set  
    @name = N'DMV Stats Test 1',  
    @collection_mode = 0,  
    @description = N'This is a test collection set',  
    @logging_level=1,  
    @days_until_expiration = 14,  
    @schedule_name=N'CollectorSchedule_Every_15min',  
    @collection_set_id = @collection_set_id OUTPUT,  
    @collection_set_uid = @collection_set_uid OUTPUT;  
SELECT @collection_set_id,@collection_set_uid;  
  
DECLARE @collector_type_uid uniqueidentifier;  
SELECT @collector_type_uid = collector_type_uid FROM syscollector_collector_types   
WHERE name = N'Generic T-SQL Query Collector Type';  
  
DECLARE @collection_item_id int;  
EXEC sp_syscollector_create_collection_item  
@name= N'Query Stats - Test 1',  
@parameters=N'  
<ns:TSQLQueryCollector xmlns:ns="DataCollectorType">  
<Query>  
  <Value>select * from sys.dm_exec_query_stats</Value>  
  <OutputTable>dm_exec_query_stats</OutputTable>  
</Query>  
 </ns:TSQLQueryCollector>',  
    @collection_item_id = @collection_item_id OUTPUT,  
    @frequency = 5, -- This parameter is ignored in cached mode  
    @collection_set_id = @collection_set_id,  
    @collector_type_uid = @collector_type_uid;  
SELECT @collection_item_id;  
  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3517-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3517-138">See Also</span></span>  
 <span data-ttu-id="d3517-139">[資料收集器預存程序 &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d3517-139">[Data Collector Stored Procedures &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/data-collector-stored-procedures-transact-sql) </span></span>  
 <span data-ttu-id="d3517-140">[管理排程](../../ssms/agent/manage-schedules.md) </span><span class="sxs-lookup"><span data-stu-id="d3517-140">[Manage Schedules](../../ssms/agent/manage-schedules.md) </span></span>  
 [<span data-ttu-id="d3517-141">啟動或停止收集組</span><span class="sxs-lookup"><span data-stu-id="d3517-141">Start or Stop a Collection Set</span></span>](start-or-stop-a-collection-set.md)  
  
  
