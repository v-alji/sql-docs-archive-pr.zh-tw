---
title: 搭配伺服器事件的 WMI 提供者使用 WQL |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- queries [WMI]
- query language [WMI]
- WMI Query Language [WMI]
- WQL [WMI]
- WMI Provider for Server Events, WQL
ms.assetid: 58b67426-1e66-4445-8e2c-03182e94c4be
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: df2bbf5c6031781494695f95116441fde34bf4f5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595840"
---
# <a name="using-wql-with-the-wmi-provider-for-server-events"></a><span data-ttu-id="9b16e-102">搭配伺服器事件的 WMI 提供者使用 WQL</span><span class="sxs-lookup"><span data-stu-id="9b16e-102">Using WQL with the WMI Provider for Server Events</span></span>
  <span data-ttu-id="9b16e-103">管理應用程式可藉由發出 WMI 查詢語言 (WQL) 陳述式，使用 WMI Provider for Server Events 來存取 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 事件。</span><span class="sxs-lookup"><span data-stu-id="9b16e-103">Management applications access [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] events using the WMI Provider for Server Events by issuing WMI Query Language (WQL) statements.</span></span> <span data-ttu-id="9b16e-104">WQL 是結構化查詢語言 (SQL) 的簡化子集，具有一些 WMI 特定的延伸模組。</span><span class="sxs-lookup"><span data-stu-id="9b16e-104">WQL is a simplified subset of structured query language (SQL), with some WMI-specific extensions.</span></span> <span data-ttu-id="9b16e-105">在使用 WQL 時，應用程式會針對 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的特定執行個體、資料庫或資料庫物件 (目前唯一支援的物件是佇列) 來擷取事件類型。</span><span class="sxs-lookup"><span data-stu-id="9b16e-105">In using WQL, an application retrieves an event type against a specific instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], a database, or a database object (the only object currently supported is queue).</span></span> <span data-ttu-id="9b16e-106">伺服器事件的 WMI 提供者會將查詢轉譯為在目標資料庫中針對資料庫範圍或物件範圍的事件通知所建立的事件通知，或用於伺服器範圍事件通知的**master**資料庫中。</span><span class="sxs-lookup"><span data-stu-id="9b16e-106">The WMI Provider for Server Events translates the query into an event notification that is created in the target database for database-scoped or object-scoped event notifications, or in the **master** database for server-scoped event notifications.</span></span>  
  
 <span data-ttu-id="9b16e-107">例如，請看下列的 WQL 查詢：</span><span class="sxs-lookup"><span data-stu-id="9b16e-107">For example, consider the following WQL query:</span></span>  
  
```  
SELECT * FROM DDL_DATABASE_LEVEL_EVENTS WHERE DatabaseName = 'AdventureWorks'  
```  
  
 <span data-ttu-id="9b16e-108">WMI 提供者會嘗試從此查詢在目標伺服器上產生此事件通知的相等項目：</span><span class="sxs-lookup"><span data-stu-id="9b16e-108">From this query, the WMI Provider tries to produce the equivalent of this event notification on the target server:</span></span>  
  
```  
USE AdventureWorks ;  
GO  
  
CREATE EVENT NOTIFICATION SQLWEP_76CF38C1_18BB_42DD_A7DC_C8820155B0E9  
    ON DATABASE  
    WITH FAN_IN  
    FOR DDL_DATABASE_LEVEL_EVENTS  
    TO SERVICE   
        'SQL/Notifications/ProcessWMIEventProviderNotification/v1.0',  
        'A7E5521A-1CA6-4741-865D-826F804E5135';  
GO  
```  
  
 <span data-ttu-id="9b16e-109">WQL 查詢的 `FROM` 子句中的引數 (`DDL_DATABASE_LEVEL_EVENTS`) 可以是能在其上建立事件通知的任何有效事件。</span><span class="sxs-lookup"><span data-stu-id="9b16e-109">The argument in the `FROM` clause of the WQL query (`DDL_DATABASE_LEVEL_EVENTS`) can be any valid event upon which an event notification can be created.</span></span> <span data-ttu-id="9b16e-110"> 和  子句中的引數可以指定與事件或其上層事件相關的任何事件屬性。</span><span class="sxs-lookup"><span data-stu-id="9b16e-110">The arguments in the `SELECT` and `WHERE` clauses can specify any event property associated with an event or its parent event.</span></span> <span data-ttu-id="9b16e-111">如需有效事件和事件屬性的清單，請參閱[事件通知 (資料庫引擎) ](https://technet.microsoft.com/library/ms182602.aspx)。</span><span class="sxs-lookup"><span data-stu-id="9b16e-111">For a list of valid events and event properties, see [Event Notifications (Database Engine)](https://technet.microsoft.com/library/ms182602.aspx).</span></span>  
  
 <span data-ttu-id="9b16e-112">下列 WQL 語法會由 WMI Provider for Server Events 明確支援。</span><span class="sxs-lookup"><span data-stu-id="9b16e-112">The following WQL syntax is supported explicitly by the WMI Provider for Server Events.</span></span> <span data-ttu-id="9b16e-113">也可以指定其他的 WQL 語法，但該語法並非此提供者所專屬，而會改由其他的 WMI 主機服務進行剖析。</span><span class="sxs-lookup"><span data-stu-id="9b16e-113">Additional WQL syntax may be specified, but it is not specific to this provider and is parsed instead by the WMI host service.</span></span> <span data-ttu-id="9b16e-114">如需有關 WMI 查詢語言的詳細資訊，請參閱 Microsoft Developer Network (MSDN) 上的 WQL 文件集。</span><span class="sxs-lookup"><span data-stu-id="9b16e-114">For more information about the WMI Query Language, see the WQL documentation on the Microsoft Developer Network (MSDN).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b16e-115">語法</span><span class="sxs-lookup"><span data-stu-id="9b16e-115">Syntax</span></span>  
  
```  
  
SELECT { event_property [ ,...n ] | * }  
FROM event_type   
WHERE where_condition  
```  
  
## <a name="arguments"></a><span data-ttu-id="9b16e-116">引數</span><span class="sxs-lookup"><span data-stu-id="9b16e-116">Arguments</span></span>  
 <span data-ttu-id="9b16e-117">*event_property*</span><span class="sxs-lookup"><span data-stu-id="9b16e-117">*event_property*</span></span>  
 <span data-ttu-id="9b16e-118">這是事件的屬性。</span><span class="sxs-lookup"><span data-stu-id="9b16e-118">Is a property of an event.</span></span> <span data-ttu-id="9b16e-119">範例包括 `PostTime`、`SPID` 和 `LoginName`。</span><span class="sxs-lookup"><span data-stu-id="9b16e-119">Examples include `PostTime`, `SPID`, and `LoginName`.</span></span> <span data-ttu-id="9b16e-120">查詢[WMI 提供者中針對伺服器事件類別和屬性](wmi-provider-for-server-events-classes-and-properties.md)所列出的每個事件，以判斷它所保留的屬性。</span><span class="sxs-lookup"><span data-stu-id="9b16e-120">Look up each event listed in [WMI Provider for Server Events Classes and Properties](wmi-provider-for-server-events-classes-and-properties.md) to determine which properties it holds.</span></span> <span data-ttu-id="9b16e-121">例如，DDL_DATABASE_LEVEL_EVENTS 事件會保存 `DatabaseName` 和 `UserName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="9b16e-121">For example, the DDL_DATABASE_LEVEL_EVENTS event holds the `DatabaseName` and `UserName` properties.</span></span> <span data-ttu-id="9b16e-122">它也會從其上層事件繼承 `SQLInstance`、`LoginName`、`PostTime`、`SPID` 和 `ComputerName` 屬性。</span><span class="sxs-lookup"><span data-stu-id="9b16e-122">It also inherits the `SQLInstance`, `LoginName`, `PostTime`, `SPID`, and `ComputerName` properties from its parent events.</span></span>  
  
 <span data-ttu-id="9b16e-123">**,** *...n*</span><span class="sxs-lookup"><span data-stu-id="9b16e-123">**,** *...n*</span></span>  
 <span data-ttu-id="9b16e-124">表示可以多次查詢*event_property* ，並以逗號分隔。</span><span class="sxs-lookup"><span data-stu-id="9b16e-124">Indicates that *event_property* can be queried multiple times, separated by commas.</span></span>  
  
 \*  
 <span data-ttu-id="9b16e-125">指定要查詢與事件相關聯的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="9b16e-125">Specifies that all properties associated with an event are queried.</span></span>  
  
 <span data-ttu-id="9b16e-126">*event_type*</span><span class="sxs-lookup"><span data-stu-id="9b16e-126">*event_type*</span></span>  
 <span data-ttu-id="9b16e-127">這是任何可針對其而建立事件通知的事件。</span><span class="sxs-lookup"><span data-stu-id="9b16e-127">Is any event against which an event notification can be created.</span></span> <span data-ttu-id="9b16e-128">如需可用事件的清單，請參閱[伺服器事件類別和屬性的 WMI 提供者](https://technet.microsoft.com/library/ms186449.aspx)。</span><span class="sxs-lookup"><span data-stu-id="9b16e-128">For a list of available events, see [WMI Provider for Server Events Classes and Properties](https://technet.microsoft.com/library/ms186449.aspx).</span></span> <span data-ttu-id="9b16e-129">請注意，當您使用 [建立事件通知] 手動建立事件通知時，*事件種類*名稱會對應至相同的*event_type*  |  *event_group* 。</span><span class="sxs-lookup"><span data-stu-id="9b16e-129">Note that *event type* names correspond to the same *event_type* | *event_group* that can be specified when you manually create an event notification by using CREATE EVENT NOTIFICATION.</span></span> <span data-ttu-id="9b16e-130">*事件種類*的範例包括 CREATE_TABLE、LOCK_DEADLOCK、DDL_USER_EVENTS 和 TRC_DATABASE。</span><span class="sxs-lookup"><span data-stu-id="9b16e-130">Examples of *event type* include CREATE_TABLE, LOCK_DEADLOCK, DDL_USER_EVENTS, and TRC_DATABASE.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9b16e-131">執行類似 DDL 作業的系統預存程序也可以引發事件通知。</span><span class="sxs-lookup"><span data-stu-id="9b16e-131">Certain system stored procedures that perform DDL-like operations can also fire event notifications.</span></span> <span data-ttu-id="9b16e-132">請測試事件通知以判斷它們對執行之系統預存程序的回應。</span><span class="sxs-lookup"><span data-stu-id="9b16e-132">Test your event notifications to determine their responses to system stored procedures that are run.</span></span> <span data-ttu-id="9b16e-133">例如，CREATE TYPE 語句和**sp_addtype**預存程式都會引發在 CREATE_TYPE 事件上建立的事件通知。</span><span class="sxs-lookup"><span data-stu-id="9b16e-133">For example, the CREATE TYPE statement and **sp_addtype** stored procedure will both fire an event notification that is created on a CREATE_TYPE event.</span></span> <span data-ttu-id="9b16e-134">不過， **sp_rename**預存程式不會引發任何事件通知。</span><span class="sxs-lookup"><span data-stu-id="9b16e-134">However, the **sp_rename** stored procedure does not fire any event notifications.</span></span> <span data-ttu-id="9b16e-135">如需詳細資訊，請參閱[DDL 事件](../triggers/ddl-events.md)。</span><span class="sxs-lookup"><span data-stu-id="9b16e-135">For more information, see[DDL Events](../triggers/ddl-events.md).</span></span>  
  
 <span data-ttu-id="9b16e-136">*where_condition*</span><span class="sxs-lookup"><span data-stu-id="9b16e-136">*where_condition*</span></span>  
 <span data-ttu-id="9b16e-137">這是 WHERE 子句查詢述詞，由*event_property*名稱和邏輯和比較運算子組成。</span><span class="sxs-lookup"><span data-stu-id="9b16e-137">Is a WHERE clause query predicate made up of *event_property* names and logical and comparison operators.</span></span> <span data-ttu-id="9b16e-138">*Where_condition*會決定對應的事件通知在目標資料庫中註冊的範圍。</span><span class="sxs-lookup"><span data-stu-id="9b16e-138">The *where_condition* determines the scope in which the corresponding event notification is registered in the target database.</span></span> <span data-ttu-id="9b16e-139">它也可以做為篩選準則，以鎖定用來查詢 event_type 的特定架構或物件 *。*</span><span class="sxs-lookup"><span data-stu-id="9b16e-139">It can also act as a filter to target a particular schema or object from which to query *event_type.*</span></span> <span data-ttu-id="9b16e-140">如需詳細資訊，請參閱本主題稍後的＜備註＞一節。</span><span class="sxs-lookup"><span data-stu-id="9b16e-140">For more information, see the Remarks section later in this topic.</span></span>  
  
 <span data-ttu-id="9b16e-141">只有 `=` 運算子可以搭配 `DatabaseName`、`SchemaName` 和 `ObjectName` 使用。</span><span class="sxs-lookup"><span data-stu-id="9b16e-141">Only the `=` operand can be used together with `DatabaseName`, `SchemaName`, and `ObjectName`.</span></span> <span data-ttu-id="9b16e-142">其他運算式無法搭配這些事件屬性使用。</span><span class="sxs-lookup"><span data-stu-id="9b16e-142">Other expressions cannot be used with these event properties.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b16e-143">備註</span><span class="sxs-lookup"><span data-stu-id="9b16e-143">Remarks</span></span>  
 <span data-ttu-id="9b16e-144">「伺服器事件的 WMI 提供者」語法的*where_condition*會決定下列各項：</span><span class="sxs-lookup"><span data-stu-id="9b16e-144">The *where_condition* of the WMI Provider for Server Events syntax determines the following:</span></span>  
  
-   <span data-ttu-id="9b16e-145">提供者嘗試用來抓取指定之*event_type*的範圍：伺服器層級、資料庫層級或物件層級 (目前唯一支援的物件是佇列) 。</span><span class="sxs-lookup"><span data-stu-id="9b16e-145">The scope by which the provider tries to retrieve the specified *event_type*: the server level, database level, or object level (the only object currently supported is queue).</span></span> <span data-ttu-id="9b16e-146">這個範圍最終會判斷在目標資料庫中所建立之事件通知的類型。</span><span class="sxs-lookup"><span data-stu-id="9b16e-146">Ultimately, this scope determines the type of event notification created in the target database.</span></span> <span data-ttu-id="9b16e-147">這個程序稱為事件通知註冊。</span><span class="sxs-lookup"><span data-stu-id="9b16e-147">This process called event notification registration.</span></span>  
  
-   <span data-ttu-id="9b16e-148">可以其上註冊之資料庫、結構描述和物件 (視何者適當)。</span><span class="sxs-lookup"><span data-stu-id="9b16e-148">The database, schema, and object, where appropriate, on which to register.</span></span>  
  
 <span data-ttu-id="9b16e-149">WMI Provider for Server Events 會使用由下而上 (Bottom-Up)、最先合適 (First-Fit) 演算法，針對基礎 EVENT NOTIFICATION 產生最小的可能範圍。</span><span class="sxs-lookup"><span data-stu-id="9b16e-149">The WMI Provider for Server Events uses a bottom-up, first-fit algorithm to produce the narrowest possible scope for the underlying EVENT NOTIFICATION.</span></span> <span data-ttu-id="9b16e-150">此種演算法會嘗試將伺服器上的內部活動以及 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體和 WMI 主機處理序之間的網路傳輸量降至最低。</span><span class="sxs-lookup"><span data-stu-id="9b16e-150">The algorithm tries to minimize internal activity on the server and network traffic between the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and the WMI host process.</span></span> <span data-ttu-id="9b16e-151">提供者會檢查在 FROM 子句中指定的*event_type*和 WHERE 子句中的條件，並嘗試以最少的可能範圍註冊基礎事件通知。</span><span class="sxs-lookup"><span data-stu-id="9b16e-151">The provider examines the *event_type* specified in the FROM clause and the conditions in the WHERE clause, and tries to register the underlying EVENT NOTIFICATION with the narrowest possible scope.</span></span> <span data-ttu-id="9b16e-152">如果提供者不能以最窄的範圍註冊，就會嘗試以連續的較高範圍註冊，直到註冊終於成功為止。</span><span class="sxs-lookup"><span data-stu-id="9b16e-152">If the provider cannot register at the narrowest scope, it tries to register at successively higher scopes until a registration finally succeeds.</span></span> <span data-ttu-id="9b16e-153">如果在達到最高的範圍 (伺服器層級) 時仍舊失敗，就會對取用者傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="9b16e-153">If it reaches the highest scope the server-level) and fails, it returns an error to the consumer.</span></span>  
  
 <span data-ttu-id="9b16e-154">例如，如果在 WHERE 子句中指定 DatabaseName =**'** AdventureWorks **'**，則提供者會嘗試在資料庫中註冊事件通知 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9b16e-154">For example, if DatabaseName=**'** AdventureWorks **'** is specified in the WHERE clause, the provider tries to register an event notification in the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database.</span></span> <span data-ttu-id="9b16e-155">如果 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫存在，而且呼叫用戶端具有在 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 中建立事件通知的必要權限，註冊作業就會成功，</span><span class="sxs-lookup"><span data-stu-id="9b16e-155">If the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database exists and the calling client has the required permissions to create an event notification in [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)], the registration is successful.</span></span> <span data-ttu-id="9b16e-156">否則系統會嘗試在伺服器層級註冊事件通知。</span><span class="sxs-lookup"><span data-stu-id="9b16e-156">Otherwise, an attempt is made to register the event notification at the server level.</span></span> <span data-ttu-id="9b16e-157">如果 WMI 用戶端擁有必要的權限，註冊就會成功。</span><span class="sxs-lookup"><span data-stu-id="9b16e-157">The registration succeeds if the WMI client has the required permissions.</span></span> <span data-ttu-id="9b16e-158">不過，在此種情況下，在建立 [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] 資料庫之前，不會對用戶端傳回事件。</span><span class="sxs-lookup"><span data-stu-id="9b16e-158">However, under this scenario, events are not returned to the client until the [!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] database has been created.</span></span>  
  
 <span data-ttu-id="9b16e-159">*Where_condition*也可以做為篩選準則，以額外限制查詢特定的資料庫、架構或物件。</span><span class="sxs-lookup"><span data-stu-id="9b16e-159">The *where_condition* can also act as a filter to additionally limit the query to a specific database, schema, or object.</span></span> <span data-ttu-id="9b16e-160">例如，請看下列的 WQL 查詢：</span><span class="sxs-lookup"><span data-stu-id="9b16e-160">For example, consider the following WQL query:</span></span>  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
 <span data-ttu-id="9b16e-161">依註冊程序的結果，這個 WQL 查詢可能會註冊於資料庫或伺服器層級。</span><span class="sxs-lookup"><span data-stu-id="9b16e-161">Depending on the outcome of the registration process, this WQL query may be registered either at the database or server level.</span></span> <span data-ttu-id="9b16e-162">不過，即使此查詢註冊於伺服器層級，提供者最終仍會篩選出不適用於 `ALTER_TABLE` 資料表的任何 `AdventureWorks.Sales.SalesOrderDetail` 事件。</span><span class="sxs-lookup"><span data-stu-id="9b16e-162">However, even if it is registered at the server level, the provider ultimately filters any `ALTER_TABLE` events that do not apply to the `AdventureWorks.Sales.SalesOrderDetail` table.</span></span> <span data-ttu-id="9b16e-163">換言之，提供者只會傳回在該特定資料表上所發生之 `ALTER_TABLE` 事件的屬性。</span><span class="sxs-lookup"><span data-stu-id="9b16e-163">In other words, the provider returns only the properties of the `ALTER_TABLE` events that occur on that specific table.</span></span>  
  
 <span data-ttu-id="9b16e-164">如果指定了 `DatabaseName='AW1'` OR `DatabaseName='AW2'` 之類的複合運算式，則會嘗試以伺服器範圍註冊單一的事件通知，而不會註冊兩個個別的事件通知。</span><span class="sxs-lookup"><span data-stu-id="9b16e-164">If a compound expression such as `DatabaseName='AW1'` OR `DatabaseName='AW2'` is specified, an attempt is made to register a single event notification at the server scope instead of two separate event notifications.</span></span> <span data-ttu-id="9b16e-165">如果呼叫用戶端擁有權限，註冊就會成功。</span><span class="sxs-lookup"><span data-stu-id="9b16e-165">The registration succeeds if the calling client has permissions.</span></span>  
  
 <span data-ttu-id="9b16e-166">如果 `SchemaName='X' AND ObjectType='Y' AND ObjectName='Z'` 已在子句中指定 all `WHERE` ，就會嘗試直接在架構的物件上註冊事件通知 `Z` `X` 。</span><span class="sxs-lookup"><span data-stu-id="9b16e-166">If `SchemaName='X' AND ObjectType='Y' AND ObjectName='Z'` are all specified in the `WHERE` clause, an attempt is made to register the event notification directly on object `Z` in schema `X`.</span></span> <span data-ttu-id="9b16e-167">如果用戶端擁有權限，註冊就會成功。</span><span class="sxs-lookup"><span data-stu-id="9b16e-167">The registration succeeds if the client has permissions.</span></span> <span data-ttu-id="9b16e-168">請注意，目前只有佇列才支持對象層級事件，而且僅適用于 QUEUE_ACTI加值稅ION *event_type*。</span><span class="sxs-lookup"><span data-stu-id="9b16e-168">Note that currently, object-level events are supported only on queues, and only for the QUEUE_ACTIVATION *event_type*.</span></span>  
  
 <span data-ttu-id="9b16e-169">請注意，並非所有事件都可以在任何的特定範圍上查詢。</span><span class="sxs-lookup"><span data-stu-id="9b16e-169">Note that not all events can be queried at any particular scope.</span></span> <span data-ttu-id="9b16e-170">例如，在追蹤事件 (例如 Lock_Deadlock) 或追蹤事件群組 (例如 TRC_LOCKS) 上的 WQL 查詢都只能在伺服器層級註冊。</span><span class="sxs-lookup"><span data-stu-id="9b16e-170">For example, a WQL query on a trace event such as Lock_Deadlock, or a trace event group such as TRC_LOCKS, can only be registered at the server level.</span></span> <span data-ttu-id="9b16e-171">同樣地，CREATE_ENDPOINT 事件和 DDL_ENDPOINT_EVENTS 事件群組也只能在伺服器層級註冊。</span><span class="sxs-lookup"><span data-stu-id="9b16e-171">Similarly, the CREATE_ENDPOINT event and the DDL_ENDPOINT_EVENTS event group can also be registered only at the server level.</span></span> <span data-ttu-id="9b16e-172">如需註冊事件之適當範圍的詳細資訊，請參閱[設計事件通知](https://technet.microsoft.com/library/ms175854\(v=sql.105\).aspx)。</span><span class="sxs-lookup"><span data-stu-id="9b16e-172">For more information about the appropriate scope for registering events, see [Designing Event Notifications](https://technet.microsoft.com/library/ms175854\(v=sql.105\).aspx).</span></span> <span data-ttu-id="9b16e-173">若嘗試註冊的 WQL 查詢，其*event_type*只能在伺服器層級註冊，則一律會在伺服器層級進行註冊。</span><span class="sxs-lookup"><span data-stu-id="9b16e-173">An attempt to register a WQL query whose *event_type* can only be registered at the server level is always made at the server level.</span></span> <span data-ttu-id="9b16e-174">如果 WMI 用戶端擁有權限，註冊就會成功。</span><span class="sxs-lookup"><span data-stu-id="9b16e-174">Registration succeeds if the WMI client has permissions.</span></span> <span data-ttu-id="9b16e-175">否則，就會對用戶端傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="9b16e-175">Otherwise, an error is returned to the client.</span></span> <span data-ttu-id="9b16e-176">不過在某些情況下，您仍可以根據與事件相對應的屬性，使用 WHERE 子句做為伺服器層級事件的篩選器。</span><span class="sxs-lookup"><span data-stu-id="9b16e-176">In some cases, however, you can still use the WHERE clause as a filter for server-level events based on the properties that correspond to the event.</span></span> <span data-ttu-id="9b16e-177">例如，許多追蹤事件都具有 `DatabaseName` 屬性，可在 WHERE 子句中用來當做篩選器。</span><span class="sxs-lookup"><span data-stu-id="9b16e-177">For example, many trace events have a `DatabaseName` property that can be used in the WHERE clause as a filter.</span></span>  
  
 <span data-ttu-id="9b16e-178">伺服器範圍的事件通知是在**master**資料庫中建立，而且可以使用[server_event_notifications](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql)目錄檢視來查詢中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9b16e-178">Server-scoped event notifications are created in the **master** database and can be queried for metadata by using the [sys.server_event_notifications](/sql/relational-databases/system-catalog-views/sys-server-event-notifications-transact-sql) catalog view.</span></span>  
  
 <span data-ttu-id="9b16e-179">系統會在指定的資料庫中建立資料庫範圍或物件範圍的事件通知，並可使用[event_notifications](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql)目錄檢視來查詢中繼資料。</span><span class="sxs-lookup"><span data-stu-id="9b16e-179">Database-scoped or object-scoped event notifications are created in the specified database and can be queried for metadata by using the [sys.event_notifications](/sql/relational-databases/system-catalog-views/sys-event-notifications-transact-sql) catalog view.</span></span> <span data-ttu-id="9b16e-180">(必須將相對應的資料庫名稱當做目錄檢視的前置詞)。</span><span class="sxs-lookup"><span data-stu-id="9b16e-180">(You must prefix the catalog view with the corresponding database name.)</span></span>  
  
## <a name="examples"></a><span data-ttu-id="9b16e-181">範例</span><span class="sxs-lookup"><span data-stu-id="9b16e-181">Examples</span></span>  
  
### <a name="a-querying-for-events-at-the-server-scope"></a><span data-ttu-id="9b16e-182">A.</span><span class="sxs-lookup"><span data-stu-id="9b16e-182">A.</span></span> <span data-ttu-id="9b16e-183">查詢伺服器範圍的事件</span><span class="sxs-lookup"><span data-stu-id="9b16e-183">Querying for events at the server scope</span></span>  
 <span data-ttu-id="9b16e-184">下列 WQL 查詢會針對任何發生於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體的 `SERVER_MEMORY_CHANGE` 追蹤事件，擷取所有的事件屬性。</span><span class="sxs-lookup"><span data-stu-id="9b16e-184">The following WQL query retrieves all event properties for any `SERVER_MEMORY_CHANGE` trace event that occurs on the instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
```  
SELECT * FROM SERVER_MEMORY_CHANGE  
```  
  
### <a name="b-querying-for-events-at-the-database-scope"></a><span data-ttu-id="9b16e-185">B.</span><span class="sxs-lookup"><span data-stu-id="9b16e-185">B.</span></span> <span data-ttu-id="9b16e-186">查詢資料庫範圍的事件</span><span class="sxs-lookup"><span data-stu-id="9b16e-186">Querying for events at the database scope</span></span>  
 <span data-ttu-id="9b16e-187">下列 WQL 查詢會針對任何發生於 `AdventureWorks` 資料庫且存在於 `DDL_DATABASE_LEVEL_EVENTS` 事件群組下方的事件，擷取特定的事件屬性。</span><span class="sxs-lookup"><span data-stu-id="9b16e-187">The following WQL query retrieves specific event properties for any event that occurs in the `AdventureWorks` database and exists under the `DDL_DATABASE_LEVEL_EVENTS` event group.</span></span>  
  
```  
SELECT SPID, SQLInstance, DatabaseName FROM DDL_DATABASE_LEVEL_EVENTS   
WHERE DatabaseName = 'AdventureWorks'   
```  
  
### <a name="c-querying-for-events-at-the-database-scope-filtering-by-schema-and-object"></a><span data-ttu-id="9b16e-188">C.</span><span class="sxs-lookup"><span data-stu-id="9b16e-188">C.</span></span> <span data-ttu-id="9b16e-189">以結構描述和物件進行篩選，查詢資料庫範圍的事件</span><span class="sxs-lookup"><span data-stu-id="9b16e-189">Querying for events at the database scope, filtering by schema and object</span></span>  
 <span data-ttu-id="9b16e-190">下列查詢會針對任何發生於 `ALTER_TABLE` 資料表的 `AdventureWorks.Sales.SalesOrderDetail` 事件，擷取所有的事件屬性。</span><span class="sxs-lookup"><span data-stu-id="9b16e-190">The following query retrieves all event properties for any `ALTER_TABLE` event that occurs on table `AdventureWorks.Sales.SalesOrderDetail`.</span></span>  
  
```  
SELECT * FROM ALTER_TABLE   
WHERE DatabaseName = 'AdventureWorks' AND SchemaName = 'Sales'   
    AND ObjectType='Table' AND ObjectName = 'SalesOrderDetail'  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b16e-191">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b16e-191">See Also</span></span>  
 <span data-ttu-id="9b16e-192">[伺服器事件的 WMI 提供者概念](https://technet.microsoft.com/library/ms180560.aspx) </span><span class="sxs-lookup"><span data-stu-id="9b16e-192">[WMI Provider for Server Events Concepts](https://technet.microsoft.com/library/ms180560.aspx) </span></span>  
 [<span data-ttu-id="9b16e-193">事件通知 (Database Engine)</span><span class="sxs-lookup"><span data-stu-id="9b16e-193">Event Notifications (Database Engine)</span></span>](https://technet.microsoft.com/library/ms182602.aspx)  
  
  
