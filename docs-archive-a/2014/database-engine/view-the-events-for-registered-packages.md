---
title: 查看已註冊之封裝的事件 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- viewing events
- extended events [SQL Server], viewing events
ms.assetid: 9a90b1a2-aa69-43f6-bdeb-cc5f57a26c6f
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: 5e3665a695bd3f40407a8680872c9b0dc79fbc53
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607013"
---
# <a name="view-the-events-for-registered-packages"></a><span data-ttu-id="02d4d-102">檢視已註冊之封裝的事件</span><span class="sxs-lookup"><span data-stu-id="02d4d-102">View the Events for Registered Packages</span></span>
  <span data-ttu-id="02d4d-103">在您建立 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 擴充的事件工作階段之前，找出註冊之封裝中可用的事件會非常有用。</span><span class="sxs-lookup"><span data-stu-id="02d4d-103">Before you create a [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Extended Events session, it is useful to find out what events are available in the registered packages.</span></span> <span data-ttu-id="02d4d-104">如需詳細資訊，請參閱＜ [SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md)＞。</span><span class="sxs-lookup"><span data-stu-id="02d4d-104">For more information, see [SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md).</span></span>  
  
 <span data-ttu-id="02d4d-105">完成這項工作需要在 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] 中使用查詢編輯器來進行以下程序。</span><span class="sxs-lookup"><span data-stu-id="02d4d-105">Accomplishing this task involves using Query Editor in [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] to carry out the following procedure.</span></span>  
  
 <span data-ttu-id="02d4d-106">當此程序中的陳述式完成之後，查詢編輯器的 **[結果]** 索引標籤會顯示以下資料行：</span><span class="sxs-lookup"><span data-stu-id="02d4d-106">After the statements in this procedure finish, the **Results** tab of Query Editor displays the following columns:</span></span>  
  
-   <span data-ttu-id="02d4d-107">名稱。</span><span class="sxs-lookup"><span data-stu-id="02d4d-107">name.</span></span> <span data-ttu-id="02d4d-108">封裝名稱。</span><span class="sxs-lookup"><span data-stu-id="02d4d-108">The package name.</span></span>  
  
-   <span data-ttu-id="02d4d-109">事件。</span><span class="sxs-lookup"><span data-stu-id="02d4d-109">event.</span></span> <span data-ttu-id="02d4d-110">事件名稱。</span><span class="sxs-lookup"><span data-stu-id="02d4d-110">The event name.</span></span>  
  
-   <span data-ttu-id="02d4d-111">關鍵字。</span><span class="sxs-lookup"><span data-stu-id="02d4d-111">keyword.</span></span> <span data-ttu-id="02d4d-112">衍生自內部數值對應資料表的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="02d4d-112">A keyword derived from an internal numeric mapping table.</span></span>  
  
-   <span data-ttu-id="02d4d-113">通道。</span><span class="sxs-lookup"><span data-stu-id="02d4d-113">channel.</span></span> <span data-ttu-id="02d4d-114">事件的使用者。</span><span class="sxs-lookup"><span data-stu-id="02d4d-114">The audience for an event.</span></span>  
  
-   <span data-ttu-id="02d4d-115">描述。</span><span class="sxs-lookup"><span data-stu-id="02d4d-115">description.</span></span> <span data-ttu-id="02d4d-116">事件描述。</span><span class="sxs-lookup"><span data-stu-id="02d4d-116">The event description.</span></span>  
  
## <a name="to-view-the-events-for-registered-packages-using-query-editor"></a><span data-ttu-id="02d4d-117">若要使用查詢編輯器來檢視已註冊之封裝的事件</span><span class="sxs-lookup"><span data-stu-id="02d4d-117">To view the events for registered packages using Query Editor</span></span>  
  
-   <span data-ttu-id="02d4d-118">在查詢編輯器中，發出下列陳述式。</span><span class="sxs-lookup"><span data-stu-id="02d4d-118">In Query Editor, issue the following statements.</span></span>  
  
    ```  
    USE msdb  
    SELECT p.name, c.event, k.keyword, c.channel, c.description FROM  
    (  
    SELECT event_package=o.package_guid, o.description,   
    event=c.object_name, channel=v.map_value  
    FROM sys.dm_xe_objects o  
    LEFT JOIN sys.dm_xe_object_columns c ON o.name=c.object_name  
    INNER JOIN sys.dm_xe_map_values v ON c.type_name=v.name   
    AND c.column_value=cast(v.map_key AS nvarchar)  
    WHERE object_type='event' AND (c.name='CHANNEL' or c.name IS NULL)  
  
    ) c LEFT JOIN   
    (  
    SELECT event_package=c.object_package_guid, event=c.object_name,   
    keyword=v.map_value  
    FROM sys.dm_xe_object_columns c INNER JOIN sys.dm_xe_map_values v   
    ON c.type_name=v.name AND c.column_value=v.map_key   
    AND c.type_package_guid=v.object_package_guid  
    INNER JOIN sys.dm_xe_objects o ON o.name=c.object_name   
    AND o.package_guid=c.object_package_guid  
    WHERE object_type='event' AND c.name='KEYWORD'   
    ) k  
    ON  
    k.event_package=c.event_package AND (k.event=c.event or k.event IS NULL)  
    INNER JOIN sys.dm_xe_packages p ON p.guid=c.event_package  
    ORDER BY keyword desc, channel, event  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="02d4d-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02d4d-119">See Also</span></span>  
 <span data-ttu-id="02d4d-120">[SQL Server 擴充的事件封裝](../relational-databases/extended-events/sql-server-extended-events-packages.md) </span><span class="sxs-lookup"><span data-stu-id="02d4d-120">[SQL Server Extended Events Packages](../relational-databases/extended-events/sql-server-extended-events-packages.md) </span></span>  
 <span data-ttu-id="02d4d-121">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="02d4d-121">[sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql) </span></span>  
 [<span data-ttu-id="02d4d-122">sys.dm_xe_packages &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="02d4d-122">sys.dm_xe_packages &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)  
  
  
