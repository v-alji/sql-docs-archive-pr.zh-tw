---
title: 取得事件通知詳細資訊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- event notifications [SQL Server], metadata
- status information [SQL Server], event notifications
- metadata [SQL Server], event notifications
ms.assetid: 8bc10867-66d6-4f57-ac32-a6c29f3327cd
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: c8d8271b6279910321058d01c7b2f96b1df62bd0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700912"
---
# <a name="get-information-about-event-notifications"></a><span data-ttu-id="2595c-102">取得事件通知詳細資訊</span><span class="sxs-lookup"><span data-stu-id="2595c-102">Get Information About Event Notifications</span></span>
  <span data-ttu-id="2595c-103">下列目錄檢視可用以查詢事件通知的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2595c-103">The following catalog views are available to query metadata about event notifications.</span></span>  
  
 <span data-ttu-id="2595c-104">**若要取得非伺服器層級的事件通知資訊**</span><span class="sxs-lookup"><span data-stu-id="2595c-104">**To get information about nonserver-level event notifications**</span></span>  
  
-   [<span data-ttu-id="2595c-105">sys.event_notifications &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2595c-105">sys.event_notifications &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql)  
  
> [!NOTE]  
>  <span data-ttu-id="2595c-106">若要檢視在資料庫層級所建立之 **sys.event_notifications** 中任何事件通知的相關中繼資料，您必須至少具有資料庫的 CONTROL、ALTER、TAKE OWNERSHIP 或 VIEW DEFINITION 權限、身為事件通知的擁有者，或是具有 ALTER ANY DATABASE EVENT NOTIFICATION 權限。</span><span class="sxs-lookup"><span data-stu-id="2595c-106">To view metadata about any event notification in **sys.event_notifications** created at the database level, at the minimum you must have the following: CONTROL, ALTER, TAKE OWNERSHIP, or VIEW DEFINITION permission on the database, be the owner of the event notification, or have ALTER ANY DATABASE EVENT NOTIFICATION permission.</span></span> <span data-ttu-id="2595c-107">如果是特定佇列上建立的事件通知，您至少必須要有以下權限：物件上的 CONTROL、ALTER、TAKE OWNERSHIP 或 VIEW DEFINITION 權限、身為事件通知的擁有者，或是具備 ALTER ANY DATABASE EVENT NOTIFICATION 權限。</span><span class="sxs-lookup"><span data-stu-id="2595c-107">For event notifications created on a specific queue, at the minimum you must have the following: CONTROL, ALTER, TAKE OWNERSHIP, or VIEW DEFINITION permission on the object, be the owner of the event notification, or have ALTER ANY DATABASE EVENT NOTIFICATION permission.</span></span>  
  
 <span data-ttu-id="2595c-108">**若要取得伺服器層級的事件通知資訊**</span><span class="sxs-lookup"><span data-stu-id="2595c-108">**To get information about server-level event notifications**</span></span>  
  
-   [<span data-ttu-id="2595c-109">sys.server_event_notifications &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2595c-109">sys.server_event_notifications &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql)  
  
> [!NOTE]  
>  <span data-ttu-id="2595c-110">您必須至少具有伺服器的 CONTROL 或 VIEW ANY DEFINITION 權限、身為事件通知的登入或擁有者，或是具有 ALTER ANY EVENT NOTIFICATION 權限，才能檢視 **sys.server_event_notifications**中任何事件通知的相關中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2595c-110">At the minimum, you must have the following: CONTROL or VIEW ANY DEFINITION permission on the server, be the logon or owner of the event notification, or have ALTER ANY EVENT NOTIFICATION permission to view metadata about any event notification in **sys.server_event_notifications**.</span></span>  
  
 <span data-ttu-id="2595c-111">**若要取得所有可以引發事件通知的事件資訊**</span><span class="sxs-lookup"><span data-stu-id="2595c-111">**To get information about all events that can fire event notifications**</span></span>  
  
-   [<span data-ttu-id="2595c-112">sys.event_notification_event_types &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2595c-112">sys.event_notification_event_types &#40;Transact-SQL&#41;</span></span>](/sql/relational-databases/system-catalog-views/sys-event-notification-event-types-transact-sql)  
  
> [!NOTE]  
>  <span data-ttu-id="2595c-113">此目錄檢視不會傳回事件群組。</span><span class="sxs-lookup"><span data-stu-id="2595c-113">This catalog view does not return event groups.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2595c-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2595c-114">See Also</span></span>  
 [<span data-ttu-id="2595c-115">事件通知</span><span class="sxs-lookup"><span data-stu-id="2595c-115">Event Notifications</span></span>](event-notifications.md)  
  
  
