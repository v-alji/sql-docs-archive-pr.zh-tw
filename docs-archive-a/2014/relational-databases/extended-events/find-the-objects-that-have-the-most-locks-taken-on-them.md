---
title: 尋找持有最多鎖定的物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- objects [SQL Server], extended events
- xe
- extended events [SQL Server], locks
- objects [SQL Server], locks
ms.assetid: fcbadbda-c91c-43f0-a1b5-601e40110e07
author: rothja
ms.author: jroth
ms.openlocfilehash: 345c5f179358bd7b8df587b76c9c6053235d3a73
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585411"
---
# <a name="find-the-objects-that-have-the-most-locks-taken-on-them"></a><span data-ttu-id="04464-102">尋找持有最多鎖定的物件</span><span class="sxs-lookup"><span data-stu-id="04464-102">Find the Objects That Have the Most Locks Taken on Them</span></span>
  <span data-ttu-id="04464-103">資料庫管理員經常需要識別阻礙資料庫效能的鎖定來源。</span><span class="sxs-lookup"><span data-stu-id="04464-103">Database administrators often need to identify the source of locks that are hindering database performance.</span></span>  
  
 <span data-ttu-id="04464-104">例如，您正在監視實際伺服器，以找出任何可能的瓶頸。</span><span class="sxs-lookup"><span data-stu-id="04464-104">For example, you are monitoring your production server for any possible bottlenecks.</span></span> <span data-ttu-id="04464-105">您懷疑可能有高度爭用的資源，而且想要了解這些物件所持有的鎖定數量。</span><span class="sxs-lookup"><span data-stu-id="04464-105">You suspect that there might be highly contested resources, and would like to know how many locks are taken on those objects.</span></span> <span data-ttu-id="04464-106">一旦識別出最常鎖定的物件之後，就可以採取步驟來最佳化爭用物件的存取。</span><span class="sxs-lookup"><span data-stu-id="04464-106">Once the most frequently locked objects are identified, steps can be taken to optimize access to the contended objects.</span></span>  
  
 <span data-ttu-id="04464-107">若要這樣做，請在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中使用查詢編輯器。</span><span class="sxs-lookup"><span data-stu-id="04464-107">To do this, use Query Editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
### <a name="to-find-the-objects-that-have-the-most-locks"></a><span data-ttu-id="04464-108">尋找持有最多鎖定的物件</span><span class="sxs-lookup"><span data-stu-id="04464-108">To find the objects that have the most locks</span></span>  
  
1.  <span data-ttu-id="04464-109">在查詢編輯器中，發出下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="04464-109">In Query Editor, issue the following statements.</span></span>  
  
    ```  
    -- Find objects in a particular database that have the most  
    -- lock acquired. This sample uses AdventureWorksDW2012.  
    -- Create the session and add an event and target.  
    --   
    IF EXISTS(SELECT * FROM sys.server_event_sessions WHERE name='LockCounts')  
    DROP EVENT session LockCounts ON SERVER  
    GO  
    DECLARE @dbid int  
  
    SELECT @dbid = db_id('AdventureWorksDW2012')  
  
    DECLARE @sql nvarchar(1024)  
    SET @sql = '  
    CREATE event session LockCounts ON SERVER  
    ADD EVENT sqlserver.lock_acquired (WHERE database_id =' + CAST(@dbid AS nvarchar) +')  
    ADD TARGET package0.histogram(   
    SET filtering_event_name=''sqlserver.lock_acquired'', source_type=0, source=''resource_0'')'  
  
    EXEC (@sql)  
    GO  
    ALTER EVENT session LockCounts ON SERVER   
    STATE=start  
    GO  
    --   
    -- Create a simple workload that takes locks.  
    --   
    USE AdventureWorksDW2012  
    GO  
    SELECT TOP 1 * FROM dbo.vAssocSeqLineItems  
    GO  
    -- The histogram target output is available from the   
    -- sys.dm_xe_session_targets dynamic management view in  
    -- XML format.  
    -- The following query joins the bucketizing target output with  
    -- sys.objects to obtain the object names.  
    --  
    SELECT name, object_id, lock_count FROM   
    (SELECT objstats.value('.','bigint') AS lobject_id,   
    objstats.value('@count', 'bigint') AS lock_count  
    FROM (  
    SELECT CAST(xest.target_data AS XML)  
    LockData  
    FROM sys.dm_xe_session_targets xest  
    JOIN sys.dm_xe_sessions xes ON xes.address = xest.event_session_address  
    JOIN sys.server_event_sessions ses ON xes.name = ses.name  
    WHERE xest.target_name = 'histogram' AND xes.name = 'LockCounts'  
    ) Locks  
    CROSS APPLY LockData.nodes('//HistogramTarget/Slot') AS T(objstats)  
     ) LockedObjects   
    INNER JOIN sys.objects o  
    ON LockedObjects.lobject_id = o.object_id  
    WHERE o.type != 'S' AND o.type = 'U'  
    ORDER BY lock_count desc  
    GO  
    --   
    -- Stop the event session.  
    --   
    ALTER EVENT SESSION LockCounts ON SERVER  
    state=stop  
    GO  
  
    ```  
  
 <span data-ttu-id="04464-110">當此程序中的陳述式完成之後，查詢編輯器的 **[結果]** 索引標籤會顯示以下資料行：</span><span class="sxs-lookup"><span data-stu-id="04464-110">After the statements in this procedure finish, the **Results** tab of Query Editor displays the following columns:</span></span>  
  
-   <span data-ttu-id="04464-111">NAME</span><span class="sxs-lookup"><span data-stu-id="04464-111">name</span></span>  
  
-   <span data-ttu-id="04464-112">object_id</span><span class="sxs-lookup"><span data-stu-id="04464-112">object_id</span></span>  
  
-   <span data-ttu-id="04464-113">lock_count</span><span class="sxs-lookup"><span data-stu-id="04464-113">lock_count</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04464-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04464-114">See Also</span></span>  
 <span data-ttu-id="04464-115">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="04464-115">[CREATE EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-event-session-transact-sql) </span></span>  
 <span data-ttu-id="04464-116">[ALTER EVENT SESSION &#40;Transact-sql&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="04464-116">[ALTER EVENT SESSION &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-event-session-transact-sql) </span></span>  
 <span data-ttu-id="04464-117">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="04464-117">[sys.dm_xe_session_targets &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-session-targets-transact-sql) </span></span>  
 <span data-ttu-id="04464-118">[dm_xe_sessions &#40;Transact-sql&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="04464-118">[sys.dm_xe_sessions &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-sessions-transact-sql) </span></span>  
 [<span data-ttu-id="04464-119">sys.server_event_sessions &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="04464-119">sys.server_event_sessions &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-event-sessions-transact-sql)  
  
  
