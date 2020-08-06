---
title: SQL Server 擴充的事件套件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xevents
ms.topic: conceptual
helpviewer_keywords:
- extended events [SQL Server], packages
- xe
ms.assetid: 6bcb04fc-ca04-48f4-b96a-20b604973447
author: rothja
ms.author: jroth
ms.openlocfilehash: 45c452300c008d486bd1f4ab4c92b5f76b96ecd8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585402"
---
# <a name="sql-server-extended-events-packages"></a><span data-ttu-id="09303-102">SQL Server 擴充事件封裝</span><span class="sxs-lookup"><span data-stu-id="09303-102">SQL Server Extended Events Packages</span></span>
  <span data-ttu-id="09303-103">封裝是 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 擴充事件物件的容器。</span><span class="sxs-lookup"><span data-stu-id="09303-103">A package is a container for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Extended Events objects.</span></span> <span data-ttu-id="09303-104">有三種擴充事件封裝，包括以下項目：</span><span class="sxs-lookup"><span data-stu-id="09303-104">There are three kinds of Extended Events packages, which include the following:</span></span>  
  
-   <span data-ttu-id="09303-105">package0 - 擴充事件系統物件。</span><span class="sxs-lookup"><span data-stu-id="09303-105">package0 - Extended Events system objects.</span></span> <span data-ttu-id="09303-106">這是預設封裝。</span><span class="sxs-lookup"><span data-stu-id="09303-106">This is the default package.</span></span>  
  
-   <span data-ttu-id="09303-107">sqlserver - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 相關的物件。</span><span class="sxs-lookup"><span data-stu-id="09303-107">sqlserver - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] related objects.</span></span>  
  
-   <span data-ttu-id="09303-108">sqlos - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 作業系統 (SQLOS) 相關的物件。</span><span class="sxs-lookup"><span data-stu-id="09303-108">sqlos - [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Operating System (SQLOS) related objects.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="09303-109">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit 會使用 SecAudit 封裝。</span><span class="sxs-lookup"><span data-stu-id="09303-109">The SecAudit package is used by [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Audit.</span></span> <span data-ttu-id="09303-110">您無法透過擴充事件資料定義語言 (DDL) 使用此封裝中的任何物件。</span><span class="sxs-lookup"><span data-stu-id="09303-110">None of the objects in the package are available through the Extended Events data definition language (DDL).</span></span>  
  
 <span data-ttu-id="09303-111">封裝是以名稱、GUID 及包含此封裝的二進位模組所識別。</span><span class="sxs-lookup"><span data-stu-id="09303-111">Packages are identified by a name, a GUID, and the binary module that contains the package.</span></span> <span data-ttu-id="09303-112">如需詳細資訊，請參閱 [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="09303-112">For more information, see [sys.dm_xe_packages &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-packages-transact-sql).</span></span>  
  
 <span data-ttu-id="09303-113">封裝可以包含下列的任何或所有物件，本主題稍後將會更詳細地討論：</span><span class="sxs-lookup"><span data-stu-id="09303-113">A package can contain any or all of the following objects, which are discussed in greater detail later in this topic:</span></span>  
  
-   <span data-ttu-id="09303-114">事件</span><span class="sxs-lookup"><span data-stu-id="09303-114">Events</span></span>  
  
-   <span data-ttu-id="09303-115">目標</span><span class="sxs-lookup"><span data-stu-id="09303-115">Targets</span></span>  
  
-   <span data-ttu-id="09303-116">[動作]</span><span class="sxs-lookup"><span data-stu-id="09303-116">Actions</span></span>  
  
-   <span data-ttu-id="09303-117">型別</span><span class="sxs-lookup"><span data-stu-id="09303-117">Types</span></span>  
  
-   <span data-ttu-id="09303-118">述詞</span><span class="sxs-lookup"><span data-stu-id="09303-118">Predicates</span></span>  
  
-   <span data-ttu-id="09303-119">地圖</span><span class="sxs-lookup"><span data-stu-id="09303-119">Maps</span></span>  
  
 <span data-ttu-id="09303-120">不同封裝中的物件可以混合在事件工作階段中。</span><span class="sxs-lookup"><span data-stu-id="09303-120">Objects from different packages can be mixed in an event session.</span></span> <span data-ttu-id="09303-121">如需詳細資訊，請參閱 [SQL Server 擴充的事件工作階段](sql-server-extended-events-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="09303-121">For more information, see [SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md).</span></span>  
  
## <a name="package-contents"></a><span data-ttu-id="09303-122">封裝內容</span><span class="sxs-lookup"><span data-stu-id="09303-122">Package Contents</span></span>  
 <span data-ttu-id="09303-123">下圖顯示封裝中可以存在的物件 (包含在模組內)。</span><span class="sxs-lookup"><span data-stu-id="09303-123">The following illustration shows the objects that can exist in packages, which are contained in a module.</span></span> <span data-ttu-id="09303-124">模組可以是可執行檔或動態連結程式庫。</span><span class="sxs-lookup"><span data-stu-id="09303-124">A module can be an executable or a dynamic link library.</span></span>  
  
 <span data-ttu-id="09303-125">![模組、套件和物件的關係](../../database-engine/media/xepackagesobjects.gif "模組、套件和物件的關係")</span><span class="sxs-lookup"><span data-stu-id="09303-125">![The relationship of a module, packages, and object](../../database-engine/media/xepackagesobjects.gif "The relationship of a module, packages, and object")</span></span>  
  
### <a name="events"></a><span data-ttu-id="09303-126">事件</span><span class="sxs-lookup"><span data-stu-id="09303-126">Events</span></span>  
 <span data-ttu-id="09303-127">事件是程式 (例如 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]) 之執行路徑中所要的監視點。</span><span class="sxs-lookup"><span data-stu-id="09303-127">Events are monitoring points of interest in the execution path of a program, such as [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="09303-128">事件引發會夾帶到達所要之點的事實以及事件開始引發之後的狀態資訊。</span><span class="sxs-lookup"><span data-stu-id="09303-128">An event firing carries with it the fact that the point of interest was reached, and state information from the time the event was fired.</span></span>  
  
 <span data-ttu-id="09303-129">事件只能用來追蹤或是觸發動作，</span><span class="sxs-lookup"><span data-stu-id="09303-129">Events can be used solely for tracing purposes or for triggering actions.</span></span> <span data-ttu-id="09303-130">這些動作可以是同步或非同步。</span><span class="sxs-lookup"><span data-stu-id="09303-130">These actions can either be synchronous or asynchronous.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="09303-131">事件不會知道為了回應事件引發所可能觸發的動作。</span><span class="sxs-lookup"><span data-stu-id="09303-131">An event does not have any knowledge of the actions that may be triggered in response to the event firing.</span></span>  
  
 <span data-ttu-id="09303-132">當封裝向擴充的事件註冊之後，就無法變更此封裝內的一組事件。</span><span class="sxs-lookup"><span data-stu-id="09303-132">A set of events in a package cannot change after the package is registered with Extended Events.</span></span>  
  
 <span data-ttu-id="09303-133">所有事件都有定義其內容的版本控制結構描述，</span><span class="sxs-lookup"><span data-stu-id="09303-133">All events have a versioned schema which defines their contents.</span></span> <span data-ttu-id="09303-134">這個結構描述是由具有定義完善之類型的事件資料行所組成。</span><span class="sxs-lookup"><span data-stu-id="09303-134">This schema is composed of event columns with well defined types.</span></span> <span data-ttu-id="09303-135">特定類型的事件一定要依照此結構描述內指定的相同順序來提供其資料。</span><span class="sxs-lookup"><span data-stu-id="09303-135">An event of a specific type must always provide its data in exactly the same order that is specified in the schema.</span></span> <span data-ttu-id="09303-136">但是，事件目標不需要使用提供的所有資料。</span><span class="sxs-lookup"><span data-stu-id="09303-136">However, an event target does not have to consume all the data that is provided.</span></span>  
  
#### <a name="event-categorization"></a><span data-ttu-id="09303-137">事件分類</span><span class="sxs-lookup"><span data-stu-id="09303-137">Event Categorization</span></span>  
 <span data-ttu-id="09303-138">擴充的事件會使用類似於 Windows 事件追蹤 (ETW) 的事件分類模型。</span><span class="sxs-lookup"><span data-stu-id="09303-138">Extended Events uses an event categorization model similar to Event Tracing for Windows (ETW).</span></span> <span data-ttu-id="09303-139">會有兩個事件屬性用於分類，也就是通道和關鍵字。</span><span class="sxs-lookup"><span data-stu-id="09303-139">Two event properties are used for categorization, channel and keyword.</span></span> <span data-ttu-id="09303-140">使用這些屬性可支援將擴充的事件與 ETW 及其工具整合。</span><span class="sxs-lookup"><span data-stu-id="09303-140">Using these properties supports the integration of Extended Events with ETW and its tools.</span></span>  
  
 <span data-ttu-id="09303-141">**通道**</span><span class="sxs-lookup"><span data-stu-id="09303-141">**Channel**</span></span>  
  
 <span data-ttu-id="09303-142">通道會識別事件的使用者。</span><span class="sxs-lookup"><span data-stu-id="09303-142">A channel identifies the audience for an event.</span></span> <span data-ttu-id="09303-143">下表將描述這些通道。</span><span class="sxs-lookup"><span data-stu-id="09303-143">These channels are described in the following table.</span></span>  
  
|<span data-ttu-id="09303-144">詞彙</span><span class="sxs-lookup"><span data-stu-id="09303-144">Term</span></span>|<span data-ttu-id="09303-145">定義</span><span class="sxs-lookup"><span data-stu-id="09303-145">Definition</span></span>|  
|----------|----------------|  
|<span data-ttu-id="09303-146">管理</span><span class="sxs-lookup"><span data-stu-id="09303-146">Admin</span></span>|<span data-ttu-id="09303-147">管理事件所針對的主要目標是使用者、管理員和支援人員。</span><span class="sxs-lookup"><span data-stu-id="09303-147">Admin events are primarily targeted to the end users, administrators, and support.</span></span> <span data-ttu-id="09303-148">在管理通道中找到的事件會指出問題，並列出定義完善的方案，供管理員做為採取動作之依據。</span><span class="sxs-lookup"><span data-stu-id="09303-148">The events that are found in the admin channels indicate a problem with a well-defined solution that an administrator can act on.</span></span> <span data-ttu-id="09303-149">管理事件的一個範例就是應用程式無法連接到印表機。</span><span class="sxs-lookup"><span data-stu-id="09303-149">An example of an admin event is when an application fails to connect to a printer.</span></span> <span data-ttu-id="09303-150">這些事件不是會完善記載下來，就是有與其相關的訊息來告訴讀者該做什麼事情來修正問題。</span><span class="sxs-lookup"><span data-stu-id="09303-150">These events are either well-documented or have a message associated with them that tells the reader what to do to rectify the problem.</span></span>|  
|<span data-ttu-id="09303-151">運作</span><span class="sxs-lookup"><span data-stu-id="09303-151">Operational</span></span>|<span data-ttu-id="09303-152">作業事件是用來分析及診斷問題或出現次數，</span><span class="sxs-lookup"><span data-stu-id="09303-152">Operational events are used for analyzing and diagnosing a problem or occurrence.</span></span> <span data-ttu-id="09303-153">根據問題或發生的情況，它們可以用來觸發工具或工作。</span><span class="sxs-lookup"><span data-stu-id="09303-153">They can be used to trigger tools or tasks based on the problem or occurrence.</span></span> <span data-ttu-id="09303-154">在系統中新增或移除印表機時即為作業事件的一個範例。</span><span class="sxs-lookup"><span data-stu-id="09303-154">An example of an operational event is when a printer is added or removed from a system.</span></span>|  
|<span data-ttu-id="09303-155">分析</span><span class="sxs-lookup"><span data-stu-id="09303-155">Analytic</span></span>|<span data-ttu-id="09303-156">分析事件的發行量很大，</span><span class="sxs-lookup"><span data-stu-id="09303-156">Analytic events are published in high volume.</span></span> <span data-ttu-id="09303-157">這些事件會描述程式作業，而且通常用於效能調查。</span><span class="sxs-lookup"><span data-stu-id="09303-157">They describe program operation and are typically used in performance investigations.</span></span>|  
|<span data-ttu-id="09303-158">偵錯</span><span class="sxs-lookup"><span data-stu-id="09303-158">Debug</span></span>|<span data-ttu-id="09303-159">偵錯事件只能由開發人員使用，以便診斷問題進行偵錯。</span><span class="sxs-lookup"><span data-stu-id="09303-159">Debug events are used solely by developers to diagnose a problem for debugging.</span></span><br /><br /> <span data-ttu-id="09303-160">注意： Debug 通道中的事件會傳回內部執行特定的狀態資料。</span><span class="sxs-lookup"><span data-stu-id="09303-160">Note: Events in the Debug channel return internal implementation-specific state data.</span></span> <span data-ttu-id="09303-161">事件所傳回的結構描述和資料在 SQL Server 的未來版本中可能會改變或變得無效。</span><span class="sxs-lookup"><span data-stu-id="09303-161">The schemas and data that the events return may change or become invalid in future versions of SQL Server.</span></span> <span data-ttu-id="09303-162">因此，偵錯通道中的事件在 SQL Server 的未來版本中可能會改變或被移除，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="09303-162">Therefore, events in the Debug channel may change or be removed in future versions of SQL Server without notice.</span></span>|  
  
 <span data-ttu-id="09303-163">**關鍵字**</span><span class="sxs-lookup"><span data-stu-id="09303-163">**Keyword**</span></span>  
  
 <span data-ttu-id="09303-164">關鍵字是應用程式所特有，可實現更精細的相關事件群組，如此可讓您更輕鬆地指定及擷取您想用於工作階段的事件。</span><span class="sxs-lookup"><span data-stu-id="09303-164">A keyword is application specific and enables a finer-grained grouping of related events, which makes it easier for you to specify and retrieve an event that you want to use in a session.</span></span> <span data-ttu-id="09303-165">您可以使用下列查詢來取得關鍵字資訊。</span><span class="sxs-lookup"><span data-stu-id="09303-165">You can use the following query to obtain keyword information.</span></span>  
  
```  
select map_value Keyword from sys.dm_xe_map_values  
where name = 'keyword_map'  
```  
  
> [!NOTE]  
>  <span data-ttu-id="09303-166">關鍵字會緊密地對應到 SQL 追蹤事件的目前群組。</span><span class="sxs-lookup"><span data-stu-id="09303-166">Keywords map closely to the current grouping of SQL Trace events.</span></span>  
  
### <a name="targets"></a><span data-ttu-id="09303-167">目標</span><span class="sxs-lookup"><span data-stu-id="09303-167">Targets</span></span>  
 <span data-ttu-id="09303-168">目標是事件取用者。</span><span class="sxs-lookup"><span data-stu-id="09303-168">Targets are event consumers.</span></span> <span data-ttu-id="09303-169">目標會處理事件 (在引發事件的執行緒上同步處理，或是在系統提供的執行緒上非同步處理)。</span><span class="sxs-lookup"><span data-stu-id="09303-169">Targets process events, either synchronously on the thread that fires the event or asynchronously on a system provided thread.</span></span> <span data-ttu-id="09303-170">擴充的事件會提供幾個目標，您可適當地使用這些目標來導向事件輸出。</span><span class="sxs-lookup"><span data-stu-id="09303-170">Extended Events provides several targets that you can use as appropriate for directing event output.</span></span> <span data-ttu-id="09303-171">如需詳細資訊，請參閱＜ [SQL Server Extended Events Targets](../../database-engine/sql-server-extended-events-targets.md)＞。</span><span class="sxs-lookup"><span data-stu-id="09303-171">For more information, see [SQL Server Extended Events Targets](../../database-engine/sql-server-extended-events-targets.md).</span></span>  
  
### <a name="actions"></a><span data-ttu-id="09303-172">[動作]</span><span class="sxs-lookup"><span data-stu-id="09303-172">Actions</span></span>  
 <span data-ttu-id="09303-173">動作是針對事件的程式設計形式的回應或回應序列。</span><span class="sxs-lookup"><span data-stu-id="09303-173">An action is a programmatic response or series of responses to an event.</span></span> <span data-ttu-id="09303-174">動作會繫結至事件，而每一個事件都可以有一組獨特的動作。</span><span class="sxs-lookup"><span data-stu-id="09303-174">Actions are bound to an event, and each event may have a unique set of actions.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="09303-175">用於特定一組事件的動作無法繫結至未知的事件。</span><span class="sxs-lookup"><span data-stu-id="09303-175">Actions that are intended for a specific set of events cannot bind to unknown events.</span></span>  
  
 <span data-ttu-id="09303-176">繫結至事件的動作會在引發此事件的執行緒上同步叫用。</span><span class="sxs-lookup"><span data-stu-id="09303-176">An action bound to an event is invoked synchronously on the thread that fired the event.</span></span> <span data-ttu-id="09303-177">動作的類型有許多種，而且功能也非常多樣。</span><span class="sxs-lookup"><span data-stu-id="09303-177">There are many types of actions and they have a wide range of capabilities.</span></span> <span data-ttu-id="09303-178">動作可以：</span><span class="sxs-lookup"><span data-stu-id="09303-178">Actions can:</span></span>  
  
-   <span data-ttu-id="09303-179">擷取堆疊傾印，並檢查資料。</span><span class="sxs-lookup"><span data-stu-id="09303-179">Capture a stack dump and inspect data.</span></span>  
  
-   <span data-ttu-id="09303-180">將狀態資訊儲存在使用變動存放區的本機環境中。</span><span class="sxs-lookup"><span data-stu-id="09303-180">Store state information in a local context using variable storage.</span></span>  
  
-   <span data-ttu-id="09303-181">彙總事件資料。</span><span class="sxs-lookup"><span data-stu-id="09303-181">Aggregate event data.</span></span>  
  
-   <span data-ttu-id="09303-182">將資料附加至事件資料。</span><span class="sxs-lookup"><span data-stu-id="09303-182">Append data to event data.</span></span>  
  
 <span data-ttu-id="09303-183">某些典型且著名的動作範例如下：</span><span class="sxs-lookup"><span data-stu-id="09303-183">Some typical and well known examples of actions are:</span></span>  
  
-   <span data-ttu-id="09303-184">堆疊傾印工具</span><span class="sxs-lookup"><span data-stu-id="09303-184">Stack dumper</span></span>  
  
-   <span data-ttu-id="09303-185">執行計畫偵測 (僅限[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] )</span><span class="sxs-lookup"><span data-stu-id="09303-185">Execution plan detection ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] only)</span></span>  
  
-   [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="09303-186">堆疊集合 (僅限[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] )</span><span class="sxs-lookup"><span data-stu-id="09303-186">stack collection ([!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] only)</span></span>  
  
-   <span data-ttu-id="09303-187">執行階段統計資料計算</span><span class="sxs-lookup"><span data-stu-id="09303-187">Run time statistics calculation</span></span>  
  
-   <span data-ttu-id="09303-188">在例外狀況發生時蒐集使用者輸入</span><span class="sxs-lookup"><span data-stu-id="09303-188">Gather user input on exception</span></span>  
  
### <a name="predicates"></a><span data-ttu-id="09303-189">述詞</span><span class="sxs-lookup"><span data-stu-id="09303-189">Predicates</span></span>  
 <span data-ttu-id="09303-190">述詞是一組邏輯規則，這些規則會在處理事件時加以評估。</span><span class="sxs-lookup"><span data-stu-id="09303-190">Predicates are a set of logical rules that are used to evaluate events when they are processed.</span></span> <span data-ttu-id="09303-191">如此可讓擴充的事件使用者選擇性地擷取以特定準則為根據的事件資料。</span><span class="sxs-lookup"><span data-stu-id="09303-191">This enables the Extended Events user to selectively capture event data based on specific criteria.</span></span>  
  
 <span data-ttu-id="09303-192">述詞可以在本機環境中儲存資料，本機環境可用來建立述詞，該述詞會在每隔 *n* 分鐘或是每當事件引發 *n* 次時傳回 True 一次。</span><span class="sxs-lookup"><span data-stu-id="09303-192">Predicates can store data in a local context that can be used for creating predicates that return true once every *n* minutes or every *n* times that an event fires.</span></span> <span data-ttu-id="09303-193">這個本機環境存放區也可用來動態地更新此述詞，藉以在事件包含類似資料時抑制未來的事件引發。</span><span class="sxs-lookup"><span data-stu-id="09303-193">This local context storage can also be used to dynamically update the predicate, thereby suppressing future event firing if the events contain similar data.</span></span>  
  
 <span data-ttu-id="09303-194">述詞能夠擷取環境資訊，例如執行緒識別碼及事件特有的資料。</span><span class="sxs-lookup"><span data-stu-id="09303-194">Predicates have the ability to retrieve context information, such as the thread ID, as well as event specific data.</span></span> <span data-ttu-id="09303-195">述詞會評估為完整布林運算式，並在發現整個運算式為 false 的第一個點支援最少運算 (Short Circuit)。</span><span class="sxs-lookup"><span data-stu-id="09303-195">Predicates are evaluated as full Boolean expressions, and support short circuiting at the first point where the entire expression is found to be false.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="09303-196">如果稍早的述詞檢查失敗，可能就無法評估有副作用的述詞。</span><span class="sxs-lookup"><span data-stu-id="09303-196">Predicates with side effects may not be evaluated if an earlier predicate check fails.</span></span>  
  
### <a name="types"></a><span data-ttu-id="09303-197">型別</span><span class="sxs-lookup"><span data-stu-id="09303-197">Types</span></span>  
 <span data-ttu-id="09303-198">由於資料是串連在一起的位元組集合，所以需要此位元組集合的長度和特性，以便能夠解譯資料。</span><span class="sxs-lookup"><span data-stu-id="09303-198">Because data is a collection of bytes strung together, the length and characteristics of the byte collection are required in order to interpret the data.</span></span> <span data-ttu-id="09303-199">這項資訊會封裝在類型物件中。</span><span class="sxs-lookup"><span data-stu-id="09303-199">This information is encapsulated in the Type object.</span></span> <span data-ttu-id="09303-200">下列是針對封裝物件所提供的類型：</span><span class="sxs-lookup"><span data-stu-id="09303-200">The following types are provided for package objects:</span></span>  
  
-   <span data-ttu-id="09303-201">event</span><span class="sxs-lookup"><span data-stu-id="09303-201">event</span></span>  
  
-   <span data-ttu-id="09303-202">動作</span><span class="sxs-lookup"><span data-stu-id="09303-202">action</span></span>  
  
-   <span data-ttu-id="09303-203">目標</span><span class="sxs-lookup"><span data-stu-id="09303-203">target</span></span>  
  
-   <span data-ttu-id="09303-204">pred_source</span><span class="sxs-lookup"><span data-stu-id="09303-204">pred_source</span></span>  
  
-   <span data-ttu-id="09303-205">pred_compare</span><span class="sxs-lookup"><span data-stu-id="09303-205">pred_compare</span></span>  
  
-   <span data-ttu-id="09303-206">類型</span><span class="sxs-lookup"><span data-stu-id="09303-206">type</span></span>  
  
 <span data-ttu-id="09303-207">如需詳細資訊，請參閱 [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="09303-207">For more information, see [sys.dm_xe_objects &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-xe-objects-transact-sql).</span></span>  
  
### <a name="maps"></a><span data-ttu-id="09303-208">地圖</span><span class="sxs-lookup"><span data-stu-id="09303-208">Maps</span></span>  
 <span data-ttu-id="09303-209">對應表會將內部值對應到字串，如此可讓使用者得知該值所表示的意義。</span><span class="sxs-lookup"><span data-stu-id="09303-209">A map table maps an internal value to a string, which enables a user to know what the value represents.</span></span> <span data-ttu-id="09303-210">使用者不只能夠取得數值，也可以取得有意義的內部值描述。</span><span class="sxs-lookup"><span data-stu-id="09303-210">Instead of only being able to obtain a numeric value, a user can get a meaningful description of the internal value.</span></span> <span data-ttu-id="09303-211">下列查詢將示範如何取得對應值。</span><span class="sxs-lookup"><span data-stu-id="09303-211">The following query shows how to obtain map values.</span></span>  
  
```  
select map_key, map_value from sys.dm_xe_map_values  
where name = 'lock_mode'  
```  
  
 <span data-ttu-id="09303-212">上述的查詢會產生下列輸出。</span><span class="sxs-lookup"><span data-stu-id="09303-212">The preceding query produces the following output.</span></span>  
  
 `map_key     map_value`  
  
 `---------------------`  
  
 `0           NL`  
  
 `1           SCH_S`  
  
 `2           SCH_M`  
  
 `3           S`  
  
 `4           U`  
  
 `5           X`  
  
 `6           IS`  
  
 `7           IU`  
  
 `8           IX`  
  
 `9           SIU`  
  
 `10          SIX`  
  
 `11          UIX`  
  
 `12          BU`  
  
 `13          RS_S`  
  
 `14          RS_U`  
  
 `15          RI_NL`  
  
 `16          RI_S`  
  
 `17          RI_U`  
  
 `18          RI_X`  
  
 `19          RX_S`  
  
 `20          RX_U`  
  
 `21          RX_X`  
  
 `21          RX_X`  
  
 <span data-ttu-id="09303-213">使用這個表格當做範例，假設您有一個名為 mode 的資料行，而且它的值為 5。</span><span class="sxs-lookup"><span data-stu-id="09303-213">Using this table as an example, assume that you have a column named mode, and its value is 5.</span></span> <span data-ttu-id="09303-214">此表格指出 5 對應到 X，這表示鎖定類型為獨佔。</span><span class="sxs-lookup"><span data-stu-id="09303-214">The table indicates that 5 maps to X, which means the lock type is Exclusive.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09303-215">另請參閱</span><span class="sxs-lookup"><span data-stu-id="09303-215">See Also</span></span>  
 <span data-ttu-id="09303-216">[SQL Server 擴充事件會話](sql-server-extended-events-sessions.md) </span><span class="sxs-lookup"><span data-stu-id="09303-216">[SQL Server Extended Events Sessions](sql-server-extended-events-sessions.md) </span></span>  
 <span data-ttu-id="09303-217">[SQL Server 擴充的事件引擎](sql-server-extended-events-engine.md) </span><span class="sxs-lookup"><span data-stu-id="09303-217">[SQL Server Extended Events Engine](sql-server-extended-events-engine.md) </span></span>  
 [<span data-ttu-id="09303-218">SQL Server 擴充的事件目標</span><span class="sxs-lookup"><span data-stu-id="09303-218">SQL Server Extended Events Targets</span></span>](../../database-engine/sql-server-extended-events-targets.md)  
  
  
