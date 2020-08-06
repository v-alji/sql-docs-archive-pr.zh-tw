---
title: SQL Server 擴充的事件工作階段 | Microsoft Docs
ms.custom: ''
ms.date: 05/26/2020
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- xe
- sessions
- extend events [SQL Server]
ms.assetid: c3c92544-351a-4bce-a06a-1f2a47e494e9
author: rothja
ms.author: jroth
ms.openlocfilehash: 3aab8c57a578ea60829514b575e168bc5a1dd8c7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585400"
---
# <a name="sql-server-extended-events-sessions"></a><span data-ttu-id="25c59-102">SQL Server 擴充的事件工作階段</span><span class="sxs-lookup"><span data-stu-id="25c59-102">SQL Server Extended Events Sessions</span></span>
  <span data-ttu-id="25c59-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 擴充的事件工作階段會建立在主控擴充之事件引擎的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 處理序中。</span><span class="sxs-lookup"><span data-stu-id="25c59-103">A [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Extended Events session is created in the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] process hosting the Extended Events engine.</span></span> <span data-ttu-id="25c59-104">下列是擴充的事件工作階段的各個層面，可讓您了解擴充的事件基礎結構的來龍去脈以及進行的一般處理：</span><span class="sxs-lookup"><span data-stu-id="25c59-104">The following aspects of an Extended Events session provide a context for understanding the Extended Events infrastructure and the general processing that takes place:</span></span>  
  
-   <span data-ttu-id="25c59-105">工作階段狀態。</span><span class="sxs-lookup"><span data-stu-id="25c59-105">Session states.</span></span> <span data-ttu-id="25c59-106">當執行 CREATE EVENT SESSION 和 ALTER EVENT SESSION 陳述式時，擴充的事件工作階段所處於的不同狀態。</span><span class="sxs-lookup"><span data-stu-id="25c59-106">The different states that an Extended Events session is in when CREATE EVENT SESSION and ALTER EVENT SESSION statements are executed.</span></span>  
  
-   <span data-ttu-id="25c59-107">工作階段內容和特性。</span><span class="sxs-lookup"><span data-stu-id="25c59-107">Session content and characteristics.</span></span> <span data-ttu-id="25c59-108">擴充事件工作階段的內容，例如目標和事件，以及這些物件如何在工作階段內或是工作階段之間相互產生關聯。</span><span class="sxs-lookup"><span data-stu-id="25c59-108">The content of an Extended Events session, such as targets and events, and how these objects are related in a session or between sessions.</span></span>  
  
## <a name="session-states"></a><span data-ttu-id="25c59-109">工作階段狀態</span><span class="sxs-lookup"><span data-stu-id="25c59-109">Session States</span></span>  
 <span data-ttu-id="25c59-110">下圖顯示擴充事件工作階段的各個狀態。</span><span class="sxs-lookup"><span data-stu-id="25c59-110">The following illustration shows the various states of an Extended Events session.</span></span>  

<span data-ttu-id="25c59-111">![擴充事件工作階段狀態](../../database-engine/media/xesessionstate.png "擴充事件工作階段狀態")</span><span class="sxs-lookup"><span data-stu-id="25c59-111">![Extended event session state](../../database-engine/media/xesessionstate.png "Extended event session state")</span></span>

 <span data-ttu-id="25c59-112">在上圖中，請注意在針對事件工作階段發出不同的 DDL 命令時，該工作階段狀態就會變更。</span><span class="sxs-lookup"><span data-stu-id="25c59-112">Referring to the preceding figure, note that session state changes as the different DDL commands are issued for an event session.</span></span> <span data-ttu-id="25c59-113">下表說明這些狀態變更所代表的意義。</span><span class="sxs-lookup"><span data-stu-id="25c59-113">The following table describes these changes in state.</span></span>  
  
|<span data-ttu-id="25c59-114">圖例標籤</span><span class="sxs-lookup"><span data-stu-id="25c59-114">Illustration label</span></span>|<span data-ttu-id="25c59-115">DDL 陳述式</span><span class="sxs-lookup"><span data-stu-id="25c59-115">DDL statement</span></span>|<span data-ttu-id="25c59-116">描述</span><span class="sxs-lookup"><span data-stu-id="25c59-116">Description</span></span>|  
|------------------------|-------------------|-----------------|  
|<span data-ttu-id="25c59-117">建立</span><span class="sxs-lookup"><span data-stu-id="25c59-117">Create</span></span>|<span data-ttu-id="25c59-118">CREATE EVENT SESSION</span><span class="sxs-lookup"><span data-stu-id="25c59-118">CREATE EVENT SESSION</span></span>|<span data-ttu-id="25c59-119">主機處理序會建立工作階段物件，此物件包含由 CREATE EVENT SESSION 所提供的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="25c59-119">The host process creates a session object that contains the metadata provided by CREATE EVENT SESSION.</span></span> <span data-ttu-id="25c59-120">主機處理序會驗證工作階段定義、驗證使用者權限等級，並將中繼資料儲存在 master 資料庫內。</span><span class="sxs-lookup"><span data-stu-id="25c59-120">The host process validates the session definition, validates the user permission level, and stores the metadata in the master database.</span></span> <span data-ttu-id="25c59-121">此時，工作階段不在使用中。</span><span class="sxs-lookup"><span data-stu-id="25c59-121">At this point the session is not active.</span></span>|  
|<span data-ttu-id="25c59-122">變更</span><span class="sxs-lookup"><span data-stu-id="25c59-122">Alter</span></span>|<span data-ttu-id="25c59-123">ALTER EVENT SESSION, STATE=START</span><span class="sxs-lookup"><span data-stu-id="25c59-123">ALTER EVENT SESSION, STATE=START</span></span>|<span data-ttu-id="25c59-124">主機處理序會啟動工作階段。</span><span class="sxs-lookup"><span data-stu-id="25c59-124">The host process starts the session.</span></span> <span data-ttu-id="25c59-125">主機處理序會讀取儲存的中繼資料、驗證工作階段定義、驗證使用者權限等級，並建立工作階段。</span><span class="sxs-lookup"><span data-stu-id="25c59-125">The host process reads the stored metadata, validates the session definition, verifies the level of user permission level, and creates the session.</span></span> <span data-ttu-id="25c59-126">會載入工作階段物件 (如事件和目標)，且事件處理為使用中。</span><span class="sxs-lookup"><span data-stu-id="25c59-126">Session objects, such as events and targets, are loaded and event handling is active.</span></span>|  
|<span data-ttu-id="25c59-127">變更</span><span class="sxs-lookup"><span data-stu-id="25c59-127">Alter</span></span>|<span data-ttu-id="25c59-128">ALTER EVENT SESSION, STATE=STOP</span><span class="sxs-lookup"><span data-stu-id="25c59-128">ALTER EVENT SESSION, STATE=STOP</span></span>|<span data-ttu-id="25c59-129">主機處理序會停止使用中工作階段，並保留中繼資料。</span><span class="sxs-lookup"><span data-stu-id="25c59-129">The host process stops the active session but retains the metadata.</span></span>|  
|<span data-ttu-id="25c59-130">卸除</span><span class="sxs-lookup"><span data-stu-id="25c59-130">Drop</span></span>|<span data-ttu-id="25c59-131">DROP EVENT SESSION</span><span class="sxs-lookup"><span data-stu-id="25c59-131">DROP EVENT SESSION</span></span>|<span data-ttu-id="25c59-132">根據工作階段是否在使用中，Drop (DROP SESSION) 將會刪除中繼資料並關閉使用中工作階段，或是刪除工作階段中繼資料。</span><span class="sxs-lookup"><span data-stu-id="25c59-132">Depending on whether or not the session is active, Drop (DROP SESSION) will delete the metadata and close the active session, or delete the session metadata.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="25c59-133">ALTER EVENT SESSION 和 DROP EVENT SESSION 都可以套用到中繼資料或是使用中工作階段和中繼資料。</span><span class="sxs-lookup"><span data-stu-id="25c59-133">Both ALTER EVENT SESSION and DROP EVENT SESSION can be applied to the metadata or to an active session and the metadata.</span></span>  
  
## <a name="session-content-and-characteristics"></a><span data-ttu-id="25c59-134">工作階段內容和特性</span><span class="sxs-lookup"><span data-stu-id="25c59-134">Session Content and Characteristics</span></span>  
 <span data-ttu-id="25c59-135">擴充的事件工作階段具有隱含的界限，在此界限下，某個工作階段的組態不會變更另一個工作階段的組態。</span><span class="sxs-lookup"><span data-stu-id="25c59-135">Extended Event sessions have implied boundaries in that the configuration of one session does not change the configuration of another session.</span></span> <span data-ttu-id="25c59-136">但是，這些界限並不會防止事件或目標在一個以上的工作階段內使用。</span><span class="sxs-lookup"><span data-stu-id="25c59-136">However, these boundaries do not prevent an event or target from being used in more than one session.</span></span>  
  
 <span data-ttu-id="25c59-137">下圖顯示工作階段內容以及封裝與工作階段之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="25c59-137">The following illustration shows session content and the relationship between packages and sessions.</span></span>  
  
 <span data-ttu-id="25c59-138">![工作階段中的物件並存和共用。](../../database-engine/media/xesessions.gif "工作階段中的物件並存和共用。")</span><span class="sxs-lookup"><span data-stu-id="25c59-138">![Object co-existance and sharing in sessions.](../../database-engine/media/xesessions.gif "Object co-existance and sharing in sessions.")</span></span>  
  
 <span data-ttu-id="25c59-139">在上圖中，請注意：</span><span class="sxs-lookup"><span data-stu-id="25c59-139">Referring to the preceding illustration, note that:</span></span>  
  
-   <span data-ttu-id="25c59-140">套件物件與工作階段之間的對應是多對多對應，這表示物件可以出現在數個工作階段中，且工作階段可以包含數個物件。</span><span class="sxs-lookup"><span data-stu-id="25c59-140">The mapping between package objects and sessions is many to many, which means that an object can appear in several sessions, and a session can contain several objects.</span></span>  
  
-   <span data-ttu-id="25c59-141">相同的事件 (事件 1) 或目標 (目標 1) 可以在一個以上的工作階段內啟用。</span><span class="sxs-lookup"><span data-stu-id="25c59-141">The same event (Event 1) or target (Target 1) can be enabled in more than one session.</span></span>  
  
 <span data-ttu-id="25c59-142">工作階段具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="25c59-142">Sessions have the following characteristics:</span></span>  
  
-   <span data-ttu-id="25c59-143">根據各個工作階段將動作和述詞繫結至事件。</span><span class="sxs-lookup"><span data-stu-id="25c59-143">Actions and predicates are bound to events on a per-session basis.</span></span> <span data-ttu-id="25c59-144">如果您在工作階段 A 內有事件 1，其中包含動作 1 和述詞 Z，這樣完全不會影響在工作階段 B 內具有事件 1，且包含動作 2 和動作 3 而沒有述詞。</span><span class="sxs-lookup"><span data-stu-id="25c59-144">If you have Event 1 in Session A with Action 1 and Predicate Z, this will not in any way affect having Event 1 in Session B with Action 2 and Action 3 with no predicate.</span></span>  
  
-   <span data-ttu-id="25c59-145">原則會附加至工作階段，以處理緩衝和分派及因果追蹤。</span><span class="sxs-lookup"><span data-stu-id="25c59-145">Policies are attached to sessions to handle buffering and dispatch, and causality tracking.</span></span>  
  
 <span data-ttu-id="25c59-146">**緩衝和分派**</span><span class="sxs-lookup"><span data-stu-id="25c59-146">**Buffering and dispatch**</span></span>  
  
 <span data-ttu-id="25c59-147">緩衝指的是當事件工作階段正在執行時，要如何儲存事件資料。</span><span class="sxs-lookup"><span data-stu-id="25c59-147">Buffering refers to how event data is stored while an event session is running.</span></span>  <span data-ttu-id="25c59-148">緩衝原則會指定用於事件資料的記憶體數量及事件的遺失原則。</span><span class="sxs-lookup"><span data-stu-id="25c59-148">Buffering policies specify how much memory to use for event data, and the loss policy for the events.</span></span> <span data-ttu-id="25c59-149">分派指的是事件在傳送至目標進行處理之前停留在緩衝區內的時間。</span><span class="sxs-lookup"><span data-stu-id="25c59-149">Dispatch refers to the amount of time events will stay in buffers before being served to targets for processing.</span></span>  
  
 <span data-ttu-id="25c59-150">**因果追蹤**</span><span class="sxs-lookup"><span data-stu-id="25c59-150">**Causality tracking**</span></span>  
  
 <span data-ttu-id="25c59-151">因果追蹤讓您能夠追蹤多個工作之間的工作。</span><span class="sxs-lookup"><span data-stu-id="25c59-151">Causality tracking provides the ability to track work across multiple tasks.</span></span> <span data-ttu-id="25c59-152">當啟用因果追蹤時，每一個引發的事件在系統中都有唯一的活動識別碼。</span><span class="sxs-lookup"><span data-stu-id="25c59-152">When causality tracking is enabled, each event fired has a unique activity ID across the system.</span></span> <span data-ttu-id="25c59-153">此活動識別碼是 GUID 值 (這個值在工作的所有事件中都維持不變) 及序號 (每次引發事件時都會隨之遞增) 的組合。</span><span class="sxs-lookup"><span data-stu-id="25c59-153">The activity ID is a combination of a GUID value that remains constant across all events for a task, and a sequence number that is incremented each time an event is fired.</span></span> <span data-ttu-id="25c59-154">當某個工作造成要在另一個工作內執行作業時，父工作的活動識別碼就會傳送給子工作。</span><span class="sxs-lookup"><span data-stu-id="25c59-154">When one task causes work to be done on another, the activity ID of the parent is sent to the child task.</span></span> <span data-ttu-id="25c59-155">子工作會在第一次引發事件時輸出父工作的活動識別碼。</span><span class="sxs-lookup"><span data-stu-id="25c59-155">The child task outputs the parent's activity ID the first time it fires an event.</span></span>  
  
 <span data-ttu-id="25c59-156">擴充的事件基礎結構會提供一個彈性的系統，可讓各種物件一起使用來解決特定的問題。</span><span class="sxs-lookup"><span data-stu-id="25c59-156">The Extended Events architecture provides a flexible system that allows a variety of objects to be used together to solve specific problems.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25c59-157">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25c59-157">See Also</span></span>  
 [<span data-ttu-id="25c59-158">擴充事件</span><span class="sxs-lookup"><span data-stu-id="25c59-158">Extended Events</span></span>](extended-events.md)  
  
  
