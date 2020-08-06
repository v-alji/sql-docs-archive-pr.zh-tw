---
title: 使用查詢通知 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- data access [SQL Server Native Client], query notifications
- rowsets [SQL Server], notifications
- SQL Server Native Client, query notifications
- notifications [SQL Server Native Client]
- query notifications [SQL Server], SQL Server Native Client
- canceling rowset changes
- IRowsetNotify interface
- SQLNCLI, query notifications
- SQL Server Native Client OLE DB provider, query notifications
- consumer notification for rowset changes [SQL Server Native Client]
ms.assetid: 2f906fff-5ed9-4527-9fd3-9c0d27c3dff7
author: rothja
ms.author: jroth
ms.openlocfilehash: ba30bfc8df05a55e297ae8fcb8e2253de57e3ca6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598311"
---
# <a name="working-with-query-notifications"></a><span data-ttu-id="78346-102">使用查詢通知</span><span class="sxs-lookup"><span data-stu-id="78346-102">Working with Query Notifications</span></span>
  <span data-ttu-id="78346-103">查詢通知是在 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 和 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 中引進。</span><span class="sxs-lookup"><span data-stu-id="78346-103">Query notifications were introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] and [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client.</span></span> <span data-ttu-id="78346-104">查詢通知是根據 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中引進的 Service Broker 基礎結構而建置，可讓應用程式在資料變更時收到通知。</span><span class="sxs-lookup"><span data-stu-id="78346-104">Built upon the Service Broker infrastructure introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], query notifications allow applications to be notified when data has changed.</span></span> <span data-ttu-id="78346-105">此功能對於從資料庫中提供資訊快取的應用程式 (如 Web 應用程式)，及需要在來源資料變更時收到通知的應用程式來說非常有用。</span><span class="sxs-lookup"><span data-stu-id="78346-105">This feature is particularly useful for applications that provide a cache of information from a database, such as a Web application, and need to be notified when the source data is changed.</span></span>  
  
 <span data-ttu-id="78346-106">當查詢的基礎資料變更時，查詢通知可讓您在指定的逾時期間要求通知。</span><span class="sxs-lookup"><span data-stu-id="78346-106">Query notifications allow you to request notification within a specified time-out period when the underlying data of a query changes.</span></span> <span data-ttu-id="78346-107">通知的要求會指定通知選項，其中包含服務名稱、訊息文字和伺服器的逾時值。</span><span class="sxs-lookup"><span data-stu-id="78346-107">The request for notification specifies the notification options, which include the service name, message text, and time-out value to the server.</span></span> <span data-ttu-id="78346-108">通知會透過 Service Broker 佇列傳遞，應用程式會輪詢此佇列以查看是否有可用的通知。</span><span class="sxs-lookup"><span data-stu-id="78346-108">Notifications are delivered through a Service Broker queue that applications may poll for available notifications.</span></span>  
  
 <span data-ttu-id="78346-109">查詢通知選項字串的語法為：</span><span class="sxs-lookup"><span data-stu-id="78346-109">The syntax of the query notifications options string is:</span></span>  
  
 `service=<service-name>[;(local database=<database> | broker instance=<broker instance>)]`  
  
 <span data-ttu-id="78346-110">例如：</span><span class="sxs-lookup"><span data-stu-id="78346-110">For example:</span></span>  
  
 `service=mySSBService;local database=mydb`  
  
 <span data-ttu-id="78346-111">通知訂閱的存留時間會超過初始化這些訂閱的程序，因為應用程式可以建立通知訂閱，然後再加以結束。</span><span class="sxs-lookup"><span data-stu-id="78346-111">Notification subscriptions outlive the process that initiates them, as an application may create a notification subscription and then terminate.</span></span> <span data-ttu-id="78346-112">訂閱仍會保持有效，而如果資料在建立訂閱時所指定的逾時期間內變更，就會發生通知。</span><span class="sxs-lookup"><span data-stu-id="78346-112">The subscription remains valid, and the notification will occur if the data changes within the time-out period specified when the subscription was created.</span></span> <span data-ttu-id="78346-113">通知會由執行的查詢、通知選項和訊息文字來識別，並且可藉由將逾時值設定為零而加以取消。</span><span class="sxs-lookup"><span data-stu-id="78346-113">A notification is identified by the query executed, the notification options, and the message text, and may be cancelled by setting its time-out value to zero.</span></span>  
  
 <span data-ttu-id="78346-114">通知只會傳送一次。</span><span class="sxs-lookup"><span data-stu-id="78346-114">Notifications are sent only once.</span></span> <span data-ttu-id="78346-115">如果要持續接到資料變更的通知，必須在處理過每個通知之後重新執行查詢，以建立新的訂閱。</span><span class="sxs-lookup"><span data-stu-id="78346-115">For continuous notification of data change, a new subscription must be created by re-executing the query after each notification is processed.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]<span data-ttu-id="78346-116">原生用戶端應用程式通常會使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] [receive](/sql/t-sql/statements/receive-transact-sql)命令，從與通知選項中指定之服務相關聯的佇列讀取通知，以接收通知。</span><span class="sxs-lookup"><span data-stu-id="78346-116">Native Client applications typically receive notifications by using the [!INCLUDE[tsql](../../../includes/tsql-md.md)] [RECEIVE](/sql/t-sql/statements/receive-transact-sql) command to read notifications from the queue associated with the service specified in the notification options.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="78346-117">您必須在需要通知的查詢中限定資料表名稱，例如 `dbo.myTable`。</span><span class="sxs-lookup"><span data-stu-id="78346-117">Table names must be qualified in queries for which notification is required, for example, `dbo.myTable`.</span></span> <span data-ttu-id="78346-118">資料表名稱必須使用兩部分的名稱來加以限定。</span><span class="sxs-lookup"><span data-stu-id="78346-118">Table names must be qualified with two part names.</span></span> <span data-ttu-id="78346-119">如果使用三或四部份的名稱，則訂閱無效。</span><span class="sxs-lookup"><span data-stu-id="78346-119">Subscription is invalid if three- or four-part names are used.</span></span>  
  
 <span data-ttu-id="78346-120">通知基礎結構是依照 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 中引進的佇列功能而建立。</span><span class="sxs-lookup"><span data-stu-id="78346-120">The notification infrastructure is built on top of a queuing feature introduced in [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="78346-121">一般而言，在伺服器所產生的通知會透過這些佇列傳送，以供稍後處理。</span><span class="sxs-lookup"><span data-stu-id="78346-121">In general, notifications generated at the server are sent through these queues to be processed later.</span></span>  
  
 <span data-ttu-id="78346-122">若要使用查詢通知，伺服器上必須有佇列和服務。</span><span class="sxs-lookup"><span data-stu-id="78346-122">To use query notifications a queue and a service must exist on the server.</span></span> <span data-ttu-id="78346-123">這些項目可以使用類似下列的 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 來建立：</span><span class="sxs-lookup"><span data-stu-id="78346-123">These can be created using [!INCLUDE[tsql](../../../includes/tsql-md.md)] similar to the following:</span></span>  
  
```  
CREATE QUEUE myQueue  
CREATE SERVICE myService ON QUEUE myQueue   
  
([https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification])  
```  
  
> [!NOTE]  
>  <span data-ttu-id="78346-124">服務必須使用預先定義的合約 `https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification` (如上所示)。</span><span class="sxs-lookup"><span data-stu-id="78346-124">The service must use the predefined contract `https://schemas.microsoft.com/SQL/Notifications/PostQueryNotification` as shown above.</span></span>  
  
## <a name="sql-server-native-client-ole-db-provider"></a><span data-ttu-id="78346-125">SQL Server Native Client OLE DB 提供者</span><span class="sxs-lookup"><span data-stu-id="78346-125">SQL Server Native Client OLE DB Provider</span></span>  
 <span data-ttu-id="78346-126">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者支援在資料列集修改時使用取用者通知。</span><span class="sxs-lookup"><span data-stu-id="78346-126">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider supports consumer notification on rowset modification.</span></span> <span data-ttu-id="78346-127">使用者會在資料列集修改的每個階段以及嘗試進行任何變更時收到通知。</span><span class="sxs-lookup"><span data-stu-id="78346-127">The consumer receives notification at every phase of rowset modification and on any attempted change.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="78346-128">使用**ICommand：： Execute**將通知查詢傳遞至伺服器，是使用 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB 提供者來訂閱查詢通知的唯一有效方法。</span><span class="sxs-lookup"><span data-stu-id="78346-128">Passing a notifications query to the server with **ICommand::Execute** is the only valid way to subscribe to query notifications with the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client OLE DB provider.</span></span>  
  
### <a name="the-dbpropset_sqlserverrowset-property-set"></a><span data-ttu-id="78346-129">DBPROPSET_SQLSERVERROWSET 屬性集</span><span class="sxs-lookup"><span data-stu-id="78346-129">The DBPROPSET_SQLSERVERROWSET Property Set</span></span>  
 <span data-ttu-id="78346-130">為了透過 OLE DB 支援查詢通知， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 會將下列新屬性新增至 DBPROPSET_SQLSERVERROWSET 屬性集。</span><span class="sxs-lookup"><span data-stu-id="78346-130">In order to support query notifications through OLE DB, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client adds the following new properties to the DBPROPSET_SQLSERVERROWSET property set.</span></span>  
  
|<span data-ttu-id="78346-131">名稱</span><span class="sxs-lookup"><span data-stu-id="78346-131">Name</span></span>|<span data-ttu-id="78346-132">類型</span><span class="sxs-lookup"><span data-stu-id="78346-132">Type</span></span>|<span data-ttu-id="78346-133">描述</span><span class="sxs-lookup"><span data-stu-id="78346-133">Description</span></span>|  
|----------|----------|-----------------|  
|<span data-ttu-id="78346-134">SSPROP_QP_NOTIFICATION_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="78346-134">SSPROP_QP_NOTIFICATION_TIMEOUT</span></span>|<span data-ttu-id="78346-135">VT_UI4</span><span class="sxs-lookup"><span data-stu-id="78346-135">VT_UI4</span></span>|<span data-ttu-id="78346-136">查詢通知要維持使用中的秒數。</span><span class="sxs-lookup"><span data-stu-id="78346-136">The number of seconds that the query notification is to remain active.</span></span><br /><br /> <span data-ttu-id="78346-137">預設值為 432000 秒 (5 天)。</span><span class="sxs-lookup"><span data-stu-id="78346-137">The default is 432000 seconds (5 days).</span></span> <span data-ttu-id="78346-138">最小值為 1 秒，最大值為 2^31-1 秒。</span><span class="sxs-lookup"><span data-stu-id="78346-138">The minimum value is 1 second, and the maximum value is 2^31-1 seconds.</span></span>|  
|<span data-ttu-id="78346-139">SSPROP_QP_NOTIFICATION_MSGTEXT</span><span class="sxs-lookup"><span data-stu-id="78346-139">SSPROP_QP_NOTIFICATION_MSGTEXT</span></span>|<span data-ttu-id="78346-140">VT_BSTR</span><span class="sxs-lookup"><span data-stu-id="78346-140">VT_BSTR</span></span>|<span data-ttu-id="78346-141">通知的訊息文字。</span><span class="sxs-lookup"><span data-stu-id="78346-141">The message text of the notification.</span></span> <span data-ttu-id="78346-142">這是使用者定義的，而且沒有預先定義的格式。</span><span class="sxs-lookup"><span data-stu-id="78346-142">This is user defined, and has no predefined format.</span></span><br /><br /> <span data-ttu-id="78346-143">根據預設，字串是空的。</span><span class="sxs-lookup"><span data-stu-id="78346-143">By default, the string is empty.</span></span> <span data-ttu-id="78346-144">您可以使用 1-2000 個字元指定訊息。</span><span class="sxs-lookup"><span data-stu-id="78346-144">You can specify a message using 1-2000 characters.</span></span>|  
|<span data-ttu-id="78346-145">SSPROP_QP_NOTIFICATION_OPTIONS</span><span class="sxs-lookup"><span data-stu-id="78346-145">SSPROP_QP_NOTIFICATION_OPTIONS</span></span>|<span data-ttu-id="78346-146">VT_BSTR</span><span class="sxs-lookup"><span data-stu-id="78346-146">VT_BSTR</span></span>|<span data-ttu-id="78346-147">查詢通知選項。</span><span class="sxs-lookup"><span data-stu-id="78346-147">The query notification options.</span></span> <span data-ttu-id="78346-148">這些是在*名稱* = *值*語法的字串中指定。</span><span class="sxs-lookup"><span data-stu-id="78346-148">These are specified in a string with *name*=*value* syntax.</span></span> <span data-ttu-id="78346-149">使用者負責建立此服務以及從佇列讀取通知。</span><span class="sxs-lookup"><span data-stu-id="78346-149">The user is responsible for creating the service and reading notifications off of the queue.</span></span><br /><br /> <span data-ttu-id="78346-150">預設值是空字串。</span><span class="sxs-lookup"><span data-stu-id="78346-150">The default is an empty string.</span></span>|  
  
 <span data-ttu-id="78346-151">無論陳述式是以使用者交易或自動認可執行，或者陳述式在其中執行的交易是否已經認可或回復，系統閱永遠都會認可通知訂閱。</span><span class="sxs-lookup"><span data-stu-id="78346-151">The notification subscription is always committed, regardless of whether the statement ran in a user transaction or in auto commit or whether the transaction in which the statement ran committed or rolled back.</span></span> <span data-ttu-id="78346-152">伺服器通知會在發生下列任何無效通知條件時觸發：基礎資料或結構描述變更，或達到逾時期限 (視何者為先)。</span><span class="sxs-lookup"><span data-stu-id="78346-152">The server notification fires upon any of the following invalid notification conditions: change of underlying data or schema, or when the timeout period is reached; whichever is first.</span></span> <span data-ttu-id="78346-153">通知註冊會在觸發之後立刻刪除。</span><span class="sxs-lookup"><span data-stu-id="78346-153">Notification registrations are deleted as soon as they are fired.</span></span> <span data-ttu-id="78346-154">因此在接到通知後，應用程式必須再進行一次訂閱，才能接到進一步的更新。</span><span class="sxs-lookup"><span data-stu-id="78346-154">Hence upon receiving notifications, the application must subscribe again in case they want to get further updates.</span></span>  
  
 <span data-ttu-id="78346-155">其他的連接或執行緒可以檢查目的地佇列是否有通知。</span><span class="sxs-lookup"><span data-stu-id="78346-155">Another connection or thread can check the destination queue for notifications.</span></span> <span data-ttu-id="78346-156">例如：</span><span class="sxs-lookup"><span data-stu-id="78346-156">For example:</span></span>  
  
```  
WAITFOR (RECEIVE * FROM MyQueue);   // Where MyQueue is the queue name.   
```  
  
 <span data-ttu-id="78346-157">請注意，SELECT \* 並不會從佇列刪除項目，但 RECEIVE \* FROM 會這麼做。</span><span class="sxs-lookup"><span data-stu-id="78346-157">Note that SELECT \* does not delete the entry from the Queue, however RECEIVE \* FROM does.</span></span> <span data-ttu-id="78346-158">如果佇列是空的，這麼做會使伺服器延滯。</span><span class="sxs-lookup"><span data-stu-id="78346-158">This stalls a server thread if the queue is empty.</span></span> <span data-ttu-id="78346-159">如果呼叫時有佇列項目，則這些項目會立刻傳回；否則呼叫會等到佇列項目建立後才進行。</span><span class="sxs-lookup"><span data-stu-id="78346-159">If there are queue entries at the time of the call, they are returned immediately; otherwise the call waits until a queue entry is made.</span></span>  
  
```  
RECEIVE * FROM MyQueue  
```  
  
 <span data-ttu-id="78346-160">如果佇列是空的，這個陳述式會立刻傳回空的結果集；否則會傳回所有的佇列通知。</span><span class="sxs-lookup"><span data-stu-id="78346-160">This statement immediately returns an empty result set if the queue is empty; otherwise it returns all queue notifications.</span></span>  
  
 <span data-ttu-id="78346-161">如果 SSPROP_QP_NOTIFICATION_MSGTEXT 和 SSPROP_QP_NOTIFICATION_OPTIONS 非 NULL 且不是空的，則每次執行命令時，都會將包含以上定義的三個屬性的查詢通知 TDS 標頭傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="78346-161">If SSPROP_QP_NOTIFICATION_MSGTEXT and SSPROP_QP_NOTIFICATION_OPTIONS are non-NULL and non-empty, the query notifications TDS header containing the three properties defined above are sent to the server with each execution of the command.</span></span> <span data-ttu-id="78346-162">如果其中任一項為 Null (或是空的)，則該標頭不會傳送且會引發 DB_E_ERRORSOCCURRED (如果這兩個屬性都標示為選擇性的，則會引發 DB_S_ERRORSOCCURRED)，而且狀態值會設定為 DBPROPSTATUS_BADVALUE。</span><span class="sxs-lookup"><span data-stu-id="78346-162">If either of them is null (or empty), the header is not sent and DB_E_ERRORSOCCURRED is raised, (or DB_S_ERRORSOCCURRED if the properties are both marked as optional), and the status value is set to DBPROPSTATUS_BADVALUE.</span></span> <span data-ttu-id="78346-163">在執行/準備時會進行驗證。</span><span class="sxs-lookup"><span data-stu-id="78346-163">The validation occurs on Execute/Prepare.</span></span> <span data-ttu-id="78346-164">同樣地，當針對 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 之前的 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 版本連接設定查詢通知屬性時，會引發 DB_S_ERRORSOCCURED。</span><span class="sxs-lookup"><span data-stu-id="78346-164">Similarly, DB_S_ERRORSOCCURED is raised when the query notification properties are set for connections to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] versions before [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)].</span></span> <span data-ttu-id="78346-165">狀態值在這種情況下是 DBPROPSTATUS_NOTSUPPORTED。</span><span class="sxs-lookup"><span data-stu-id="78346-165">The status value in this case is DBPROPSTATUS_NOTSUPPORTED.</span></span>  
  
 <span data-ttu-id="78346-166">初始化訂閱並不保證後續的訊息能成功傳遞。</span><span class="sxs-lookup"><span data-stu-id="78346-166">Initiating a subscription does not guarantee that subsequent messages will be successfully delivered.</span></span> <span data-ttu-id="78346-167">此外，系統也不會對所指定服務名稱的有效性進行檢查。</span><span class="sxs-lookup"><span data-stu-id="78346-167">In addition, no check is made as to the validity of the service name specified.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="78346-168">陳述式的準備永遠都不會初始化訂閱，只有陳述式的執行才會造成初始化，此外使用 OLE DB 核心服務也不會影響查詢通知。</span><span class="sxs-lookup"><span data-stu-id="78346-168">Preparing statements will never cause the subscription to be initiated; only statement execution will achieve this and query notifications are not impacted by the use of OLE DB core services.</span></span>  
  
 <span data-ttu-id="78346-169">如需 DBPROPSET_SQLSERVERROWSET 屬性集的詳細資訊，請參閱資料列[集屬性和行為](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md)。</span><span class="sxs-lookup"><span data-stu-id="78346-169">For more information about the DBPROPSET_SQLSERVERROWSET property set, see [Rowset Properties and Behaviors](../../native-client-ole-db-rowsets/rowset-properties-and-behaviors.md).</span></span>  
  
## <a name="sql-server-native-client-odbc-driver"></a><span data-ttu-id="78346-170">SQL Server Native Client ODBC 驅動程式</span><span class="sxs-lookup"><span data-stu-id="78346-170">SQL Server Native Client ODBC Driver</span></span>  
 <span data-ttu-id="78346-171">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式透過將三個新屬性新增至[SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md)和[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)函數，來支援查詢通知：</span><span class="sxs-lookup"><span data-stu-id="78346-171">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports query notifications through the addition of three new attributes to the [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) and [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) functions:</span></span>  
  
-   <span data-ttu-id="78346-172">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT</span><span class="sxs-lookup"><span data-stu-id="78346-172">SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT</span></span>  
  
-   <span data-ttu-id="78346-173">SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS</span><span class="sxs-lookup"><span data-stu-id="78346-173">SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS</span></span>  
  
-   <span data-ttu-id="78346-174">SQL_SOPT_SS_QUERYNOTIFICATION_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="78346-174">SQL_SOPT_SS_QUERYNOTIFICATION_TIMEOUT</span></span>  
  
 <span data-ttu-id="78346-175">如果 SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT 和 SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS 並非 NULL，則每次執行命令時，都會將包含上述定義的三個屬性的查詢通知 TDS 標頭傳送到伺服器。</span><span class="sxs-lookup"><span data-stu-id="78346-175">If SQL_SOPT_SS_QUERYNOTIFICATION_MSGTEXT and SQL_SOPT_SS_QUERYNOTIFICATION_OPTIONS are not NULL, the query notifications TDS header containing the three attributes defined above will be sent to the server each time the command is executed.</span></span> <span data-ttu-id="78346-176">如果其中任一項為 Null，則不會傳送標頭，而會傳回 SQL_SUCCESS_WITH_INFO。</span><span class="sxs-lookup"><span data-stu-id="78346-176">If either of them is null, the header is not sent, and SQL_SUCCESS_WITH_INFO is returned.</span></span> <span data-ttu-id="78346-177">驗證會在[SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360)函式、 **SqlExecDirect**和**SqlExecute**上進行，而且如果屬性無效，這些會失敗。</span><span class="sxs-lookup"><span data-stu-id="78346-177">The validation occurs on [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360), **SqlExecDirect**, and **SqlExecute**, all of which fail if the attributes are not valid.</span></span> <span data-ttu-id="78346-178">同樣地，當針對 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之前的 [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)] 版本設定這些查詢通知屬性時，執行會失敗且引發 SQL_SUCCESS_WITH_INFO。</span><span class="sxs-lookup"><span data-stu-id="78346-178">Similarly, when these query notification attributes are set for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] versions before [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], the execution fails with SQL_SUCCESS_WITH_INFO.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="78346-179">訂閱永遠都不會因為準備陳述式而初始化，但可能會因為執行陳述式而初始化。</span><span class="sxs-lookup"><span data-stu-id="78346-179">Prepare statements will never cause the subscription to be initiated; subscription can be initiated by statement execution.</span></span>  
  
## <a name="special-cases-and-restrictions"></a><span data-ttu-id="78346-180">特殊案例和限制</span><span class="sxs-lookup"><span data-stu-id="78346-180">Special Cases and Restrictions</span></span>  
 <span data-ttu-id="78346-181">通知不支援下列資料類型：</span><span class="sxs-lookup"><span data-stu-id="78346-181">The following data types are not supported for notifications:</span></span>  
  
-   `text`  
  
-   `ntext`  
  
-   `image`  
  
 <span data-ttu-id="78346-182">如果針對傳回任何這些類型的查詢進行通知要求，就會立刻觸發通知，指出不可能進行通知訂閱。</span><span class="sxs-lookup"><span data-stu-id="78346-182">If a notification request is made for a query which returns any of these types, the notification fires immediately, specifying that notification subscription was not possible.</span></span>  
  
 <span data-ttu-id="78346-183">如果訂閱要求是針對批次或預存程序所建立的，就會針對批次或預存程序內執行的每個陳述式建立個別的訂閱要求。</span><span class="sxs-lookup"><span data-stu-id="78346-183">If a subscription request is made for a batch or stored procedure, a separate subscription request is made for each statement executed within the batch or stored procedure.</span></span> <span data-ttu-id="78346-184">EXECUTE 陳述式不會註冊通知，不過會將通知要求傳送至執行的命令。</span><span class="sxs-lookup"><span data-stu-id="78346-184">EXECUTE statements will not register a notification, but will send the notification request to the executed command.</span></span> <span data-ttu-id="78346-185">如果它是批次，內容就會套用至執行的陳述式，而且適用上述的相同規則。</span><span class="sxs-lookup"><span data-stu-id="78346-185">If it is a batch, the context will be applied to the executed statements and the same rules described above apply.</span></span>  
  
 <span data-ttu-id="78346-186">提交在相同資料庫內容下由相同使用者提交之通知的查詢，並具有相同的範本、相同的參數值、相同的通知識別碼，以及現有作用中訂閱的相同傳遞位置，將會更新現有的訂閱，並重設新指定的超時時間。這表示如果要求相同查詢的通知，則只會傳送一則通知。</span><span class="sxs-lookup"><span data-stu-id="78346-186">Submission of a query for notification that was submitted by the same user under the same database context and has the same template, same parameter values, same notification ID, and same delivery location of an existing active subscription, will renew the existing subscription, resetting the new specified time-out. This means that if notification is requested for identical queries, only one notification will be sent.</span></span> <span data-ttu-id="78346-187">這適用於批次中重複的查詢，或預存程序中多次呼叫的查詢。</span><span class="sxs-lookup"><span data-stu-id="78346-187">This would apply to a query duplicated in a batch, or a query in a stored procedure that was called multiple times.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78346-188">另請參閱</span><span class="sxs-lookup"><span data-stu-id="78346-188">See Also</span></span>  
 [<span data-ttu-id="78346-189">SQL Server Native Client 功能</span><span class="sxs-lookup"><span data-stu-id="78346-189">SQL Server Native Client Features</span></span>](sql-server-native-client-features.md)  
  
  
