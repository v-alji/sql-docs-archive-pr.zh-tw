---
title: 存取擴充事件記錄檔中的診斷資訊 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: aaa180c2-5e1a-4534-a125-507c647186ab
author: rothja
ms.author: jroth
ms.openlocfilehash: 5148683d464f06e8a4f52cc924baaacac9102b12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698107"
---
# <a name="accessing-diagnostic-information-in-the-extended-events-log"></a><span data-ttu-id="019eb-102">存取擴展事件記錄檔中的診斷資訊</span><span class="sxs-lookup"><span data-stu-id="019eb-102">Accessing Diagnostic Information in the Extended Events Log</span></span>
  <span data-ttu-id="019eb-103">從開始 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] ， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 和資料存取追蹤 ([資料存取追蹤](https://go.microsoft.com/fwlink/?LinkId=125805)) 已更新，可讓您更輕鬆地從連接信號緩衝區取得連接失敗的診斷資訊，以及擴充事件記錄檔中的應用程式效能資訊。</span><span class="sxs-lookup"><span data-stu-id="019eb-103">Beginning in [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client and data access tracing ([Data Access Tracing](https://go.microsoft.com/fwlink/?LinkId=125805)) have been updated to make it easier to get diagnostic information about connection failures from the connectivity ring buffer and application performance information from the extended events log.</span></span>  
  
 <span data-ttu-id="019eb-104">如需讀取擴充事件記錄檔的資訊，請參閱[檢視事件工作階段資料](../../../database-engine/view-event-session-data.md)。</span><span class="sxs-lookup"><span data-stu-id="019eb-104">For information about reading the extended events log, see [View Event Session Data](../../../database-engine/view-event-session-data.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="019eb-105">此功能僅供疑難排解及診斷使用，可能不適用稽核或安全性。</span><span class="sxs-lookup"><span data-stu-id="019eb-105">This feature is intended only for troubleshooting and diagnostic purposes and may not be suitable for auditing or security purposes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="019eb-106">備註</span><span class="sxs-lookup"><span data-stu-id="019eb-106">Remarks</span></span>  
 <span data-ttu-id="019eb-107">針對連接作業，[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client 會傳送用戶端連接識別碼。</span><span class="sxs-lookup"><span data-stu-id="019eb-107">For connection operations, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client will send a client connection ID.</span></span> <span data-ttu-id="019eb-108">如果連線失敗，您可以使用連線信號) 緩衝區，在[SQL Server 2008 中](https://go.microsoft.com/fwlink/?LinkId=207752)存取連線性信號緩衝區 (連線疑難排解，並尋找 `ClientConnectionID` 欄位並取得有關連線失敗的診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="019eb-108">If the connection fails, you can access the connectivity ring buffer ([Connectivity troubleshooting in SQL Server 2008 with the Connectivity Ring Buffer](https://go.microsoft.com/fwlink/?LinkId=207752)) and find the `ClientConnectionID` field and get diagnostic information about the connection failure.</span></span> <span data-ttu-id="019eb-109">僅在發生錯誤時，才會在信號緩衝區中記錄用戶端連接識別碼。</span><span class="sxs-lookup"><span data-stu-id="019eb-109">Client connection IDs are logged in the ring buffer only if an error occurs.</span></span> <span data-ttu-id="019eb-110">(如果在傳送登入前封包之前連接失敗，則不會產生用戶端連接識別碼。)用戶端連接識別碼是 16 位元組的 GUID。</span><span class="sxs-lookup"><span data-stu-id="019eb-110">(If a connection fails before sending the prelogin packet, a client connection ID will not be generated.) The client connection ID is a 16-byte GUID.</span></span> <span data-ttu-id="019eb-111">如果在擴充的事件工作階段中，將 `client_connection_id` 動作加入至事件，您也可以在擴充的事件輸出目標中找到用戶端連接識別碼。</span><span class="sxs-lookup"><span data-stu-id="019eb-111">You can also find the client connection ID in the extended events output target, if the `client_connection_id` action is added to events in an extended events session.</span></span> <span data-ttu-id="019eb-112">如果您需要進一步的診斷協助，您可以啟用資料存取追蹤並重新執行連接命令，然後觀察資料存取追蹤的 `ClientConnectionID` 欄位中是否有失敗的作業。</span><span class="sxs-lookup"><span data-stu-id="019eb-112">You can enable data access tracing and rerun the connection command and observe the `ClientConnectionID` field in the data access trace for a failed operation, if you need further diagnostic assistance.</span></span>  
  
 <span data-ttu-id="019eb-113">如果您在 Native Client 中使用 ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ，而連接成功，則可以使用屬性搭配 SQLGetConnectAttr 來取得用戶端連接識別碼 `SQL_COPT_SS_CLIENT_CONNECTION_ID` 。 [SQLGetConnectAttr](../../native-client-odbc-api/sqlgetconnectattr.md)</span><span class="sxs-lookup"><span data-stu-id="019eb-113">If you are using ODBC in [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client and a connection succeeds, you can get the client connection ID by using the `SQL_COPT_SS_CLIENT_CONNECTION_ID` attribute with [SQLGetConnectAttr](../../native-client-odbc-api/sqlgetconnectattr.md).</span></span>  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] <span data-ttu-id="019eb-114">Native Client 也會傳送執行緒專屬的活動識別碼。</span><span class="sxs-lookup"><span data-stu-id="019eb-114">Native Client also sends a thread-specific activity ID.</span></span> <span data-ttu-id="019eb-115">如果已啟動工作階段並啟用 TRACK_CAUSAILITY 選項，即可在擴充的事件工作階段中擷取活動識別碼。</span><span class="sxs-lookup"><span data-stu-id="019eb-115">The activity ID is captured in the extended events sessions if the sessions are started with the TRACK_CAUSAILITY option enabled.</span></span> <span data-ttu-id="019eb-116">如需與使用中連接相關的效能問題，您可以從用戶端的資料存取追蹤 (`ActivityID` 欄位) 取得活動識別碼，然後在擴充的事件輸出中尋找此活動識別碼。</span><span class="sxs-lookup"><span data-stu-id="019eb-116">For performance issues with an active connection, you can get the activity ID from the client's data access trace (`ActivityID` field) and then locate the activity ID in the extended events output.</span></span> <span data-ttu-id="019eb-117">擴充事件中的活動識別碼為 16 位元組的 GUID (與用戶端連接識別碼的 GUID 不同)，後面附加 4 位元組的序號。</span><span class="sxs-lookup"><span data-stu-id="019eb-117">The activity ID in the extended events is a 16-byte GUID (not the same as the GUID for the client connection ID) appended with a four-byte sequence number.</span></span> <span data-ttu-id="019eb-118">此序號表示執行緒內要求的順序，並指出執行緒的批次和 RPC 陳述式的相對排序。</span><span class="sxs-lookup"><span data-stu-id="019eb-118">The sequence number represents the order of a request within a thread and indicates the relative ordering of batch and RPC statements for the thread.</span></span> <span data-ttu-id="019eb-119">啟用資料存取追蹤，並開啟資料存取追蹤組態中的 18 位元時，會選擇性地針對 SQL 批次陳述式和 RPC 要求傳送 `ActivityID`。</span><span class="sxs-lookup"><span data-stu-id="019eb-119">The `ActivityID` is optionally sent for SQL batch statements and RPC requests when data access tracing is enabled on and the 18th bit in the data access tracing configuration word is turned ON.</span></span>  
  
 <span data-ttu-id="019eb-120">以下是使用 [!INCLUDE[tsql](../../../includes/tsql-md.md)] 啟動擴充事件工作階段的範例，該工作階段會儲存在信號緩衝區中，並且會記錄從 RPC 和批次作業上之用戶端傳送的活動識別碼。</span><span class="sxs-lookup"><span data-stu-id="019eb-120">The following is a sample that uses [!INCLUDE[tsql](../../../includes/tsql-md.md)] to start an extended events session that will be stored in a ring buffer and will record the activity ID sent from a client on RPC and batch operations.</span></span>  
  
```  
create event session MySession on server   
add event connectivity_ring_buffer_recorded,   
add event sql_statement_starting (action (client_connection_id)),   
add event sql_statement_completed (action (client_connection_id)),   
add event rpc_starting (action (client_connection_id)),   
add event rpc_completed (action (client_connection_id))  
add target ring_buffer with (track_causality=on)  
  
```  
  
## <a name="control-file"></a><span data-ttu-id="019eb-121">控制檔案</span><span class="sxs-lookup"><span data-stu-id="019eb-121">Control File</span></span>  
 <span data-ttu-id="019eb-122">在 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中，SQL Server Native Client 控制檔案 (ctrl.guid.snac11) 的內容為：</span><span class="sxs-lookup"><span data-stu-id="019eb-122">In [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], the contents of the SQL Server Native  Client control file (ctrl.guid.snac11) is:</span></span>  
  
```  
{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}  0x00000000  0   MSDADIAG.ETW  
{2DA81B52-908E-7DB6-EF81-76856BB47C4F}  0xFFFFFFFF  0   SQLNCLI11.1  
```  
  
## <a name="mof-file"></a><span data-ttu-id="019eb-123">MOF 檔案</span><span class="sxs-lookup"><span data-stu-id="019eb-123">MOF File</span></span>  
 <span data-ttu-id="019eb-124">在 [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] 中，SQL Server Native Client mof 檔的內容為：</span><span class="sxs-lookup"><span data-stu-id="019eb-124">In [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)], the contents of the SQL Server Native  Client mof file is:</span></span>  
  
```  
#pragma classflags("forceupdate")  
#pragma namespace ("\\\\.\\Root\\WMI")  
  
/////////////////////////////////////////////////////////////////////////////  
//  
//  MSDADIAG.ETW  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW"),  
 Guid("{8B98D3F2-3CC6-0B9C-6651-9649CCE5C752}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW"),  
 Guid("{8B98D3F3-3CC6-0B9C-6651-9649CCE5C752}"),  
 DisplayName("msdadiag"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace : Bid2Etw_MSDADIAG_ETW  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace_TextA : Bid2Etw_MSDADIAG_ETW_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringA"),  
     extension("RString"),  
     read  
    ]  
    object msgStr;  
};  
  
[  
 dynamic: ToInstance,  
 Description("MSDADIAG.ETW formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_MSDADIAG_ETW_Trace_TextW : Bid2Etw_MSDADIAG_ETW_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringW"),  
     extension("RWString"),  
     read  
    ]  
    object msgStr;  
};  
  
/////////////////////////////////////////////////////////////////////////////  
//  
//  SQLNCLI11.1  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1"),  
 Guid("{2DA81B52-908E-7DB6-EF81-76856BB47C4F}"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1 : EventTrace  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1"),  
 Guid("{2DA81B53-908E-7DB6-EF81-76856BB47C4F}"),  
 DisplayName("SQLNCLI11.1"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace : Bid2Etw_SQLNCLI11_1  
{  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1 formatted output (A)"),  
 EventType(17),  
 EventTypeName("TextA"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace_TextA : Bid2Etw_SQLNCLI11_1_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringA"),  
     extension("RString"),  
     read  
    ]  
    object msgStr;  
};  
  
[  
 dynamic: ToInstance,  
 Description("SQLNCLI11.1 formatted output (W)"),  
 EventType(18),  
 EventTypeName("TextW"),  
 locale("MS\\0x409")  
]  
class Bid2Etw_SQLNCLI11_1_Trace_TextW : Bid2Etw_SQLNCLI11_1_Trace  
{  
    [  
     WmiDataId(1),  
     Description("Module ID"),  
     read  
    ]  
    uint32 ModID;  
  
    [  
     WmiDataId(2),  
     Description("Text StringW"),  
     extension("RWString"),  
     read  
    ]  
    object msgStr;  
};  
```  
  
## <a name="see-also"></a><span data-ttu-id="019eb-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="019eb-125">See Also</span></span>  
 [<span data-ttu-id="019eb-126">處理錯誤與訊息</span><span class="sxs-lookup"><span data-stu-id="019eb-126">Handling Errors and Messages</span></span>](../../native-client-odbc-error-messages/handling-errors-and-messages.md)  
  
  
