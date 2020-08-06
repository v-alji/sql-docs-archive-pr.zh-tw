---
title: 實作事件通知 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], target service
- target service [SQL Server]
- event notifications [SQL Server], creating
ms.assetid: 29ac8f68-a28a-4a77-b67b-a8663001308c
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 6a89c66ca5c3b420fff14c087bd604b16c641369
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596608"
---
# <a name="implement-event-notifications"></a><span data-ttu-id="2ddab-102">實作事件通知</span><span class="sxs-lookup"><span data-stu-id="2ddab-102">Implement Event Notifications</span></span>
  <span data-ttu-id="2ddab-103">若要實作事件通知，您必須先建立目標服務來接收事件通知，然後建立事件通知。</span><span class="sxs-lookup"><span data-stu-id="2ddab-103">To implement an event notification, you must first create a target service to receive event notifications, and then create the event notification.</span></span>  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="2ddab-104">對話安全性。</span><span class="sxs-lookup"><span data-stu-id="2ddab-104">dialog security should be configured for event notifications that send messages to a service broker on a remote server.</span></span> <span data-ttu-id="2ddab-105">對話安全性必須根據完整安全性模型，以手動方式加以設定。</span><span class="sxs-lookup"><span data-stu-id="2ddab-105">Dialog security must be configured manually according to the full security model.</span></span>  
  
## <a name="creating-the-target-service"></a><span data-ttu-id="2ddab-106">建立目標服務</span><span class="sxs-lookup"><span data-stu-id="2ddab-106">Creating the Target Service</span></span>  
 <span data-ttu-id="2ddab-107">您不必建立 [!INCLUDE[ssSB](../../includes/sssb-md.md)]起始服務，因為 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 包括下列特定訊息類型和事件通知的合約：</span><span class="sxs-lookup"><span data-stu-id="2ddab-107">You do not have to create a [!INCLUDE[ssSB](../../includes/sssb-md.md)]-initiating service because [!INCLUDE[ssSB](../../includes/sssb-md.md)] includes the following specific message type and contract for event notifications:</span></span>  
  
```  
https://schemas.microsoft.com/SQL/Notifications/PostEventNotification  
```  
  
 <span data-ttu-id="2ddab-108">接收事件通知的目標服務必須遵照這項預先存在的合約。</span><span class="sxs-lookup"><span data-stu-id="2ddab-108">The target service that receives event notifications must honor this preexisting contract.</span></span>  
  
 <span data-ttu-id="2ddab-109">**若要建立目標服務**：</span><span class="sxs-lookup"><span data-stu-id="2ddab-109">**To create a target service**:</span></span>  
  
1.  <span data-ttu-id="2ddab-110">建立要接收訊息的佇列。</span><span class="sxs-lookup"><span data-stu-id="2ddab-110">Create a queue to receive messages.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="2ddab-111">佇列會接收下列訊息類型： `https://schemas.microsoft.com/SQL/Notifications/QueryNotification`。</span><span class="sxs-lookup"><span data-stu-id="2ddab-111">The queue receives the following message type: `https://schemas.microsoft.com/SQL/Notifications/QueryNotification`.</span></span>  
  
2.  <span data-ttu-id="2ddab-112">在參考事件通知合約的佇列上建立服務。</span><span class="sxs-lookup"><span data-stu-id="2ddab-112">Create a service on the queue that references the event notifications contract.</span></span>  
  
3.  <span data-ttu-id="2ddab-113">在服務上建立路由，以定義要 [!INCLUDE[ssSB](../../includes/sssb-md.md)] 將該服務的訊息傳送到哪一個位址。</span><span class="sxs-lookup"><span data-stu-id="2ddab-113">Create a route on the service to define the address to which [!INCLUDE[ssSB](../../includes/sssb-md.md)] sends messages for the service.</span></span> <span data-ttu-id="2ddab-114">如果事件通知是以相同資料庫中的服務為目標，請指定 `ADDRESS = 'LOCAL'`。</span><span class="sxs-lookup"><span data-stu-id="2ddab-114">For event notifications that target a service in the same database, specify `ADDRESS = 'LOCAL'`.</span></span>  
  
    > [!NOTE]  
    >  [!INCLUDE[ssSB](../../includes/sssb-md.md)] <span data-ttu-id="2ddab-115">路由會判斷要接收通知訊息的服務。</span><span class="sxs-lookup"><span data-stu-id="2ddab-115">routing determines the service that receives the notification messages.</span></span> <span data-ttu-id="2ddab-116">如果事件通知是以遠端伺服器的服務為目標，則來源伺服器和目標伺服器上都必須要定義路由，以確保可以進行雙向通訊。</span><span class="sxs-lookup"><span data-stu-id="2ddab-116">If the event notification targets a service on a remote server, both the source server and the target server must have routes defined on them to make sure that two-way communication occurs.</span></span>  
  
 <span data-ttu-id="2ddab-117">下列範例會建立佇列、佇列上的服務及服務上的路由，以處理來自事件通知合約的訊息：</span><span class="sxs-lookup"><span data-stu-id="2ddab-117">The following example creates a queue, a service on the queue, and a route on the service to handle messages from the event notification contract.</span></span>  
  
```  
CREATE QUEUE NotifyQueue ;  
GO  
CREATE SERVICE NotifyService  
ON QUEUE NotifyQueue  
(  
[https://schemas.microsoft.com/SQL/Notifications/PostEventNotification]  
);  
GO  
CREATE ROUTE NotifyRoute  
WITH SERVICE_NAME = 'NotifyService',  
ADDRESS = 'LOCAL';  
GO  
```  
  
## <a name="creating-the-event-notification"></a><span data-ttu-id="2ddab-118">建立事件通知</span><span class="sxs-lookup"><span data-stu-id="2ddab-118">Creating the Event Notification</span></span>  
 <span data-ttu-id="2ddab-119">事件通知是使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE EVENT NOTIFICATION 陳述式建立，並使用 DROP EVENT NOTIFICATION STATEMENT 卸除。</span><span class="sxs-lookup"><span data-stu-id="2ddab-119">Event notifications are created by using the [!INCLUDE[tsql](../../includes/tsql-md.md)] CREATE EVENT NOTIFICATION statement, and are dropped by using the DROP EVENT NOTIFICATION STATEMENT.</span></span> <span data-ttu-id="2ddab-120">若要修改事件通知，您必須先卸除再重新建立事件通知。</span><span class="sxs-lookup"><span data-stu-id="2ddab-120">To modify an event notification, you must drop and re-create the event notification.</span></span>  
  
 <span data-ttu-id="2ddab-121">下列範例會建立事件通知 `CreateDatabaseNotification`。</span><span class="sxs-lookup"><span data-stu-id="2ddab-121">The following example creates the event notification `CreateDatabaseNotification`.</span></span> <span data-ttu-id="2ddab-122">當伺服器上發生任何 `CREATE_DATABASE` 事件時，這個通知會傳送此訊息給先前建立的 `NotifyService` 服務。</span><span class="sxs-lookup"><span data-stu-id="2ddab-122">This notification sends a message about any `CREATE_DATABASE` event that occurs on the server to the `NotifyService` service that was previously created.</span></span>  
  
```  
CREATE EVENT NOTIFICATION CreateDatabaseNotification  
ON SERVER  
FOR CREATE_DATABASE  
TO SERVICE 'NotifyService', '8140a771-3c4b-4479-8ac0-81008ab17984' ;  
```  
  
> [!CAUTION]  
>  <span data-ttu-id="2ddab-123">事件通知以不同事件來辨識 CREATE_SCHEMA 事件和 CREATE SCHEMA 陳述式的 <schema_element> 定義。</span><span class="sxs-lookup"><span data-stu-id="2ddab-123">Event notifications recognize CREATE_SCHEMA events and the <schema_element> definitions of CREATE SCHEMA statements as separate events.</span></span> <span data-ttu-id="2ddab-124">例如，對 CREATE_SCHEMA 和 CREATE_TABLE 事件建立事件通知，且您執行下列批次。</span><span class="sxs-lookup"><span data-stu-id="2ddab-124">For example, an event notification is created on both the CREATE_SCHEMA and CREATE_TABLE events, and you run the following batch.</span></span>  
>   
>  `CREATE SCHEMA s`  
>   
>  `CREATE TABLE t1 (col1 int)`  
>   
>  <span data-ttu-id="2ddab-125">在此案例中，事件通知引發了兩次：一次是在 CREATE_SCHEMA 事件發生時，一次只在 CREATE_TABLE 事件發生時。</span><span class="sxs-lookup"><span data-stu-id="2ddab-125">In this case, the event notification is raised two times: Onne time when the CREATE_SCHEMA event occurs, and again when the CREATE_TABLE event occurs.</span></span> <span data-ttu-id="2ddab-126">我們建議您避免在 CREATE_SCHEMA 事件和任何對應 CREATE SCHEMA  定義的 <schema_element> 文字上建立事件通知，或在應用程式中建立邏輯，以避免擷取不想要的事件資料。</span><span class="sxs-lookup"><span data-stu-id="2ddab-126">We recommend that you either avoid creating event notifications on both the CREATE_SCHEMA events and the <schema_element> texts of any corresponding CREATE SCHEMA definitions, or build logic into your application to avoid capturing unwanted event data.</span></span>  
  
 <span data-ttu-id="2ddab-127">**若要建立事件通知**</span><span class="sxs-lookup"><span data-stu-id="2ddab-127">**To create an event notification**</span></span>  
  
-   [<span data-ttu-id="2ddab-128">CREATE EVENT NOTIFICATION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2ddab-128">CREATE EVENT NOTIFICATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/create-event-notification-transact-sql)  
  
 <span data-ttu-id="2ddab-129">**若要卸除事件通知**</span><span class="sxs-lookup"><span data-stu-id="2ddab-129">**To drop an event notification**</span></span>  
  
-   [<span data-ttu-id="2ddab-130">DROP EVENT NOTIFICATION &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2ddab-130">DROP EVENT NOTIFICATION &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/drop-event-notification-transact-sql)  
  
## <a name="see-also"></a><span data-ttu-id="2ddab-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ddab-131">See Also</span></span>  
 <span data-ttu-id="2ddab-132">[取得事件通知詳細資訊](event-notifications.md) </span><span class="sxs-lookup"><span data-stu-id="2ddab-132">[Get Information About Event Notifications](event-notifications.md) </span></span>  
 [<span data-ttu-id="2ddab-133">EVENTDATA &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2ddab-133">EVENTDATA &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/functions/eventdata-transact-sql)  
  
  
