---
title: SQLGetConnectAttr |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetConnectAttr function
ms.assetid: 26e4e69a-44fd-45e3-b47a-ae39184f041b
author: rothja
ms.author: jroth
ms.openlocfilehash: f82a0fb71103e811b36280f9722c160791023e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584495"
---
# <a name="sqlgetconnectattr"></a><span data-ttu-id="d395a-102">SQLGetConnectAttr</span><span class="sxs-lookup"><span data-stu-id="d395a-102">SQLGetConnectAttr</span></span>
  <span data-ttu-id="d395a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式會定義驅動程式特有的連接屬性。</span><span class="sxs-lookup"><span data-stu-id="d395a-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver defines driver-specific connection attributes.</span></span> <span data-ttu-id="d395a-104">有些屬性可供使用 `SQLGetConnectAttr` ，而函數則用來報告其目前的設定。</span><span class="sxs-lookup"><span data-stu-id="d395a-104">Some of the attributes are available to `SQLGetConnectAttr`, and the function is used to report their current settings.</span></span> <span data-ttu-id="d395a-105">在建立連接或使用[SQLSetConnectAttr](sqlsetconnectattr.md)設定屬性之前，不保證會針對這些屬性回報的值。</span><span class="sxs-lookup"><span data-stu-id="d395a-105">The values reported for these attributes are not guaranteed until after a connection has been made or the attribute has been set using [SQLSetConnectAttr](sqlsetconnectattr.md).</span></span>  
  
 <span data-ttu-id="d395a-106">本主題將列出唯讀屬性。</span><span class="sxs-lookup"><span data-stu-id="d395a-106">This topic lists the read only attributes.</span></span> <span data-ttu-id="d395a-107">如需有關其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式特定連接屬性的詳細資訊，請參閱[SQLSetConnectAttr](sqlsetconnectattr.md)。</span><span class="sxs-lookup"><span data-stu-id="d395a-107">For information about the other [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver-specific connection attributes, see [SQLSetConnectAttr](sqlsetconnectattr.md).</span></span>  
  
## <a name="sql_copt_ss_connection_dead"></a><span data-ttu-id="d395a-108">SQL_COPT_SS_CONNECTION_DEAD</span><span class="sxs-lookup"><span data-stu-id="d395a-108">SQL_COPT_SS_CONNECTION_DEAD</span></span>  
 <span data-ttu-id="d395a-109">SQL_COPT_SS_CONNECTION_DEAD 屬性會將連接的狀態報告給伺服器。</span><span class="sxs-lookup"><span data-stu-id="d395a-109">The SQL_COPT_SS_CONNECTION_DEAD attribute reports the state of a connection to a server.</span></span> <span data-ttu-id="d395a-110">此驅動程式會查詢網路，以得知目前連接狀態。</span><span class="sxs-lookup"><span data-stu-id="d395a-110">The driver queries the network for the current state of the connection.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d395a-111">標準 ODBC 連接屬性 SQL_ATTR_CONNECTION_DEAD 會傳回最新的連接狀態。</span><span class="sxs-lookup"><span data-stu-id="d395a-111">The standard ODBC connection attribute SQL_ATTR_CONNECTION_DEAD returns the most recent state of the connection.</span></span> <span data-ttu-id="d395a-112">這可能不是目前的連接狀態。</span><span class="sxs-lookup"><span data-stu-id="d395a-112">This might not be the current connection state.</span></span>  
  
|<span data-ttu-id="d395a-113">值</span><span class="sxs-lookup"><span data-stu-id="d395a-113">Value</span></span>|<span data-ttu-id="d395a-114">描述</span><span class="sxs-lookup"><span data-stu-id="d395a-114">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d395a-115">SQL_CD_TRUE</span><span class="sxs-lookup"><span data-stu-id="d395a-115">SQL_CD_TRUE</span></span>|<span data-ttu-id="d395a-116">已經遺失與伺服器的連接。</span><span class="sxs-lookup"><span data-stu-id="d395a-116">The connection to the server has been lost.</span></span>|  
|<span data-ttu-id="d395a-117">SQL_CD_FALSE</span><span class="sxs-lookup"><span data-stu-id="d395a-117">SQL_CD_FALSE</span></span>|<span data-ttu-id="d395a-118">連接已開啟，而且可用來處理陳述式。</span><span class="sxs-lookup"><span data-stu-id="d395a-118">The connection is open and available for statement processing.</span></span>|  
  
## <a name="sql_copt_ss_client_connection_id"></a><span data-ttu-id="d395a-119">SQL_COPT_SS_CLIENT_CONNECTION_ID</span><span class="sxs-lookup"><span data-stu-id="d395a-119">SQL_COPT_SS_CLIENT_CONNECTION_ID</span></span>  
 <span data-ttu-id="d395a-120">SQL_COPT_SS_CLIENT_CONNECTION_ID 屬性擷取用戶端連接識別碼，然後可使用此識別碼尋找：</span><span class="sxs-lookup"><span data-stu-id="d395a-120">The SQL_COPT_SS_CLIENT_CONNECTION_ID attribute retrieves the client connection ID, which can then be used to locate:</span></span>  
  
-   <span data-ttu-id="d395a-121">啟用之 XEvents 記錄檔中的診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="d395a-121">Diagnostic information in the XEvents log, when enabled.</span></span>  
  
-   <span data-ttu-id="d395a-122">連接信號緩衝區中的連接錯誤資訊。</span><span class="sxs-lookup"><span data-stu-id="d395a-122">Connection error information in the connection ring buffer.</span></span>  
  
-   <span data-ttu-id="d395a-123">啟用之資料存取追蹤記錄檔中的診斷資訊。</span><span class="sxs-lookup"><span data-stu-id="d395a-123">Diagnostic information in the data access tracing logs, when enabled.</span></span>  
  
 <span data-ttu-id="d395a-124">如需詳細資訊，請參閱[存取擴充事件記錄檔中的診斷資訊](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md)。</span><span class="sxs-lookup"><span data-stu-id="d395a-124">For more information, see [Accessing Diagnostic Information in the Extended Events Log](../native-client/features/accessing-diagnostic-information-in-the-extended-events-log.md).</span></span>  
  
|<span data-ttu-id="d395a-125">值</span><span class="sxs-lookup"><span data-stu-id="d395a-125">Value</span></span>|<span data-ttu-id="d395a-126">描述</span><span class="sxs-lookup"><span data-stu-id="d395a-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d395a-127">SQL_ERROR</span><span class="sxs-lookup"><span data-stu-id="d395a-127">SQL_ERROR</span></span>|<span data-ttu-id="d395a-128">連接失敗。</span><span class="sxs-lookup"><span data-stu-id="d395a-128">The connection failed.</span></span>|  
|<span data-ttu-id="d395a-129">SQL_SUCCESS</span><span class="sxs-lookup"><span data-stu-id="d395a-129">SQL_SUCCESS</span></span>|<span data-ttu-id="d395a-130">此連接已成功。</span><span class="sxs-lookup"><span data-stu-id="d395a-130">The connection succeeded.</span></span> <span data-ttu-id="d395a-131">輸出緩衝區中將可以找到用戶端連接識別碼。</span><span class="sxs-lookup"><span data-stu-id="d395a-131">The client connection ID will be found in the output buffer.</span></span>|  
  
## <a name="sql_copt_ss_perf_data"></a><span data-ttu-id="d395a-132">SQL_COPT_SS_PERF_DATA</span><span class="sxs-lookup"><span data-stu-id="d395a-132">SQL_COPT_SS_PERF_DATA</span></span>  
 <span data-ttu-id="d395a-133">SQL_COPT_SS_PERF_DATA 屬性會傳回 SQLPERF 結構的指標，其中包含目前的驅動程式效能統計資料。</span><span class="sxs-lookup"><span data-stu-id="d395a-133">The SQL_COPT_SS_PERF_DATA attribute returns a pointer to a SQLPERF structure containing the current driver performance statistics.</span></span> <span data-ttu-id="d395a-134">`SQLGetConnectAttr`如果未啟用效能記錄，將會傳回 Null。</span><span class="sxs-lookup"><span data-stu-id="d395a-134">`SQLGetConnectAttr` will return NULL if performance logging is not enabled.</span></span> <span data-ttu-id="d395a-135">此驅動程式不會動態更新 SQLPERF 結構中的統計資料。</span><span class="sxs-lookup"><span data-stu-id="d395a-135">The statistics in the SQLPERF structure are not dynamically updated by the driver.</span></span> <span data-ttu-id="d395a-136">`SQLGetConnectAttr`每次需要重新整理效能統計資料時呼叫。</span><span class="sxs-lookup"><span data-stu-id="d395a-136">Call `SQLGetConnectAttr` each time the performance statistics need to be refreshed.</span></span>  
  
|<span data-ttu-id="d395a-137">值</span><span class="sxs-lookup"><span data-stu-id="d395a-137">Value</span></span>|<span data-ttu-id="d395a-138">描述</span><span class="sxs-lookup"><span data-stu-id="d395a-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d395a-139">NULL</span><span class="sxs-lookup"><span data-stu-id="d395a-139">NULL</span></span>|<span data-ttu-id="d395a-140">未啟用效能記錄。</span><span class="sxs-lookup"><span data-stu-id="d395a-140">Performance logging is not enabled.</span></span>|  
|<span data-ttu-id="d395a-141">任何其他值</span><span class="sxs-lookup"><span data-stu-id="d395a-141">Any other value</span></span>|<span data-ttu-id="d395a-142">SQLPERF 結構的指標。</span><span class="sxs-lookup"><span data-stu-id="d395a-142">A pointer to a SQLPERF structure.</span></span>|  
  
## <a name="sql_copt_ss_perf_query"></a><span data-ttu-id="d395a-143">SQL_COPT_SS_PERF_QUERY</span><span class="sxs-lookup"><span data-stu-id="d395a-143">SQL_COPT_SS_PERF_QUERY</span></span>  
 <span data-ttu-id="d395a-144">如果啟用了長時間執行之查詢的記錄，SQL_COPT_SS_PERF_QUERY 屬性會傳回 TRUE。</span><span class="sxs-lookup"><span data-stu-id="d395a-144">The SQL_COPT_SS_PERF_QUERY attribute returns TRUE if logging of long running queries is enabled.</span></span> <span data-ttu-id="d395a-145">如果查詢記錄不在使用中，要求會傳回 FALSE。</span><span class="sxs-lookup"><span data-stu-id="d395a-145">The request returns FALSE if query logging is not active.</span></span>  
  
## <a name="sql_copt_ss_user_data"></a><span data-ttu-id="d395a-146">SQL_COPT_SS_USER_DATA</span><span class="sxs-lookup"><span data-stu-id="d395a-146">SQL_COPT_SS_USER_DATA</span></span>  
 <span data-ttu-id="d395a-147">SQL_COPT_SS_USER_DATA 屬性會擷取使用者-資料指標。</span><span class="sxs-lookup"><span data-stu-id="d395a-147">The SQL_COPT_SS_USER_DATA attribute retrieves the user-data pointer.</span></span> <span data-ttu-id="d395a-148">使用者資料會儲存在用戶端擁有的記憶體中，而且針對每個連接記錄下來。</span><span class="sxs-lookup"><span data-stu-id="d395a-148">User data is stored in client-owned memory and recorded per connection.</span></span> <span data-ttu-id="d395a-149">如果尚未設定使用者-資料指標，便會傳回 SQL_UD_NOTSET (一種 NULL 指標)。</span><span class="sxs-lookup"><span data-stu-id="d395a-149">If the user-data pointer has not been set, SQL_UD_NOTSET, a NULL pointer, is returned.</span></span>  
  
|<span data-ttu-id="d395a-150">值</span><span class="sxs-lookup"><span data-stu-id="d395a-150">Value</span></span>|<span data-ttu-id="d395a-151">描述</span><span class="sxs-lookup"><span data-stu-id="d395a-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d395a-152">SQL_UD_NOTSET</span><span class="sxs-lookup"><span data-stu-id="d395a-152">SQL_UD_NOTSET</span></span>|<span data-ttu-id="d395a-153">不會設定任何使用者-資料指標。</span><span class="sxs-lookup"><span data-stu-id="d395a-153">No user-data pointer is set.</span></span>|  
|<span data-ttu-id="d395a-154">任何其他值</span><span class="sxs-lookup"><span data-stu-id="d395a-154">Any other value</span></span>|<span data-ttu-id="d395a-155">使用者資料的指標。</span><span class="sxs-lookup"><span data-stu-id="d395a-155">A pointer to the user data.</span></span>|  
  
## <a name="sqlgetconnectattr-support-for-service-principal-names-spns"></a><span data-ttu-id="d395a-156">服務主要名稱 (SPN) 的 SQLGetConnectAttr 支援</span><span class="sxs-lookup"><span data-stu-id="d395a-156">SQLGetConnectAttr Support for Service Principal Names (SPNs)</span></span>  
 <span data-ttu-id="d395a-157">SQLGetConnectAttr 可以用來查詢新連接屬性的值 SQL_COPT_SS_SERVER_SPN、SQL_COPT_SS_FAILOVER_PARTNER_SPN、SQL_COPT_SS_MUTUALLY_AUTHENTICATED 和 SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD。</span><span class="sxs-lookup"><span data-stu-id="d395a-157">SQLGetConnectAttr can be used to query the value of the new connection attributes SQL_COPT_SS_SERVER_SPN, SQL_COPT_SS_FAILOVER_PARTNER_SPN, SQL_COPT_SS_MUTUALLY_AUTHENTICATED, and SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD.</span></span> <span data-ttu-id="d395a-158"> (SQLGetConnectOption 也可以用來查詢這些值。 ) </span><span class="sxs-lookup"><span data-stu-id="d395a-158">(SQLGetConnectOption can also be used to query these values.)</span></span>  
  
 <span data-ttu-id="d395a-159">SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD 只供使用 Windows 驗證的已開啟連接使用。</span><span class="sxs-lookup"><span data-stu-id="d395a-159">SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD is only available for open connections that use Windows Authentication.</span></span>  
  
 <span data-ttu-id="d395a-160">如果尚未設定 SQL_COPT_SS_SERVER_SPN 或 SQL_COPT_SS_FAILOVER_PARTNER，就會傳回預設值 (空字串)。</span><span class="sxs-lookup"><span data-stu-id="d395a-160">If SQL_COPT_SS_SERVER_SPN or SQL_COPT_SS_FAILOVER_PARTNER has not been set, the default value (an empty string) is returned.</span></span>  
  
 <span data-ttu-id="d395a-161">如需 Spn 的詳細資訊，請參閱[&#40;ODBC&#41;的用戶端連接中 &#40;spn&#41; 的服務主體名稱](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="d395a-161">For more information about SPNs, see [Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d395a-162">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d395a-162">See Also</span></span>  
 <span data-ttu-id="d395a-163">[SQLGetConnectAttr 函式](https://go.microsoft.com/fwlink/?LinkId=59347) </span><span class="sxs-lookup"><span data-stu-id="d395a-163">[SQLGetConnectAttr Function](https://go.microsoft.com/fwlink/?LinkId=59347) </span></span>  
 <span data-ttu-id="d395a-164">[ODBC API 的執行詳細資料](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="d395a-164">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 <span data-ttu-id="d395a-165">[設定 QUOTED_IDENTIFIER &#40;Transact-sql&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d395a-165">[SET QUOTED_IDENTIFIER &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-quoted-identifier-transact-sql) </span></span>  
 <span data-ttu-id="d395a-166">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d395a-166">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span></span>  
 <span data-ttu-id="d395a-167">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="d395a-167">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span></span>  
 [<span data-ttu-id="d395a-168">SET ANSI_WARNINGS &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="d395a-168">SET ANSI_WARNINGS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-ansi-warnings-transact-sql)  
  
  
