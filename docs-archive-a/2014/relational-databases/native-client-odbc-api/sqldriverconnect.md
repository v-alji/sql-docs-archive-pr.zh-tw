---
title: SQLDriverConnect |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDriverConnect function
ms.assetid: a1e38e2c-3a97-42d1-9c45-a0ca3282ffd1
author: rothja
ms.author: jroth
ms.openlocfilehash: 40691dfb381883b59155607fb56f4933820e3e44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705117"
---
# <a name="sqldriverconnect"></a><span data-ttu-id="c9526-102">SQLDriverConnect</span><span class="sxs-lookup"><span data-stu-id="c9526-102">SQLDriverConnect</span></span>
  <span data-ttu-id="c9526-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式會定義可取代或增強連接字串關鍵字的連接屬性。</span><span class="sxs-lookup"><span data-stu-id="c9526-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver defines connection attributes that either replace or enhance connection-string keywords.</span></span> <span data-ttu-id="c9526-104">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式已經指定數個連接字串關鍵字的預設值。</span><span class="sxs-lookup"><span data-stu-id="c9526-104">Several connection-string keywords have default values specified by the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span>  
  
 <span data-ttu-id="c9526-105">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式中可用的關鍵字清單，請參閱搭配[使用連接字串關鍵字與 SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="c9526-105">For a list of the keywords available in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, see [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
 <span data-ttu-id="c9526-106">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連接屬性和驅動程式預設行為的詳細資訊，請參閱[SQLSetConnectAttr](sqlsetconnectattr.md)。</span><span class="sxs-lookup"><span data-stu-id="c9526-106">For more information about [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection attributes and driver default behaviors, see [SQLSetConnectAttr](sqlsetconnectattr.md).</span></span>  
  
 <span data-ttu-id="c9526-107">如需對 Native Client 有效之連接字串關鍵字的討論 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，請參閱搭配[使用連接字串關鍵字與 SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md)。</span><span class="sxs-lookup"><span data-stu-id="c9526-107">For a discussion of connection string keywords that are valid for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, see [Using Connection String Keywords with SQL Server Native Client](../native-client/applications/using-connection-string-keywords-with-sql-server-native-client.md).</span></span>  
  
 <span data-ttu-id="c9526-108">當 `SQLDriverConnect` *DriverCompletion*參數值 SQL_DRIVER_PROMPT、SQL_DRIVER_COMPLETE 或 SQL_DRIVER_COMPLETE_REQUIRED 時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式會從顯示的對話方塊中抓取關鍵字值。</span><span class="sxs-lookup"><span data-stu-id="c9526-108">When the `SQLDriverConnect`*DriverCompletion* parameter value is SQL_DRIVER_PROMPT, SQL_DRIVER_COMPLETE, or SQL_DRIVER_COMPLETE_REQUIRED, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver retrieves keyword values from the displayed dialog box.</span></span> <span data-ttu-id="c9526-109">如果在連接字串中傳遞關鍵字值，而且使用者沒有在對話方塊中變更關鍵字的值，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式會使用連接字串中的值。</span><span class="sxs-lookup"><span data-stu-id="c9526-109">If the keyword value is passed in the connection string and the user does not alter the value for the keyword in the dialog box, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver uses the value from the connection string.</span></span> <span data-ttu-id="c9526-110">如果沒有在連接字串中設定值，而且使用者沒有在對話方塊中進行指派，驅動程式會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="c9526-110">If the value is not set in the connection string and the user makes no assignment in the dialog box, the driver uses the default.</span></span>  
  
 <span data-ttu-id="c9526-111">`SQLDriverConnect`當有任何*DriverCompletion*值需要 (或可能需要) 顯示驅動程式的連接對話方塊時，必須提供有效的*WindowHandle* 。</span><span class="sxs-lookup"><span data-stu-id="c9526-111">`SQLDriverConnect` must be given a valid *WindowHandle* when any *DriverCompletion* value requires (or could require) the display of the driver's connection dialog box.</span></span> <span data-ttu-id="c9526-112">無效的控制代碼會傳回 SQL_ERROR。</span><span class="sxs-lookup"><span data-stu-id="c9526-112">An invalid handle returns SQL_ERROR.</span></span>  
  
 <span data-ttu-id="c9526-113">指定 DRIVER 或 DSN 關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c9526-113">Specify either the DRIVER or DSN keywords.</span></span> <span data-ttu-id="c9526-114">ODBC 敘述如果同時指定兩個關鍵字，驅動程式會使用最左邊的關鍵字，並忽略另一個關鍵字。</span><span class="sxs-lookup"><span data-stu-id="c9526-114">ODBC states that a driver uses the leftmost of these two keywords and ignores the other if both are specified.</span></span> <span data-ttu-id="c9526-115">如果已指定 DRIVER，或為兩者的最左邊，而且 `SQLDriverConnect` *DriverCompletion*參數值為 SQL_DRIVER_NOPROMPT，則需要 SERVER 關鍵字和適當的值。</span><span class="sxs-lookup"><span data-stu-id="c9526-115">If DRIVER is specified, or is the leftmost of the two, and the `SQLDriverConnect`*DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT, the SERVER keyword and an appropriate value are required.</span></span>  
  
 <span data-ttu-id="c9526-116">指定 SQL_DRIVER_NOPROMPT 時，使用者驗證關鍵字與值必須同時存在。</span><span class="sxs-lookup"><span data-stu-id="c9526-116">When SQL_DRIVER_NOPROMPT is specified, user authentication keywords must be present with values.</span></span> <span data-ttu-id="c9526-117">驅動程式會確認字串 "Trusted_Connection=yes" 存在，或 UID 和 PWD 關鍵字同時存在。</span><span class="sxs-lookup"><span data-stu-id="c9526-117">The driver ensures that either the string "Trusted_Connection=yes" or both the UID and PWD keywords are present.</span></span>  
  
 <span data-ttu-id="c9526-118">如果*DriverCompletion*參數值為 SQL_DRIVER_NOPROMPT 或 SQL_DRIVER_COMPLETE_REQUIRED，而語言或資料庫來自連接字串，且其中一個無效，則會傳回 `SQLDriverConnect` SQL_ERROR。</span><span class="sxs-lookup"><span data-stu-id="c9526-118">If the *DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT or SQL_DRIVER_COMPLETE_REQUIRED and the language or database comes from the connection string and either is invalid, `SQLDriverConnect` returns SQL_ERROR.</span></span>  
  
 <span data-ttu-id="c9526-119">如果*DriverCompletion*參數值 SQL_DRIVER_NOPROMPT 或 SQL_DRIVER_COMPLETE_REQUIRED，而語言或資料庫來自 ODBC 資料來源定義，而且兩者都無效，則會 `SQLDriverConnect` 針對指定的使用者識別碼使用預設的語言或資料庫，並傳回 SQL_SUCCESS_WITH_INFO。</span><span class="sxs-lookup"><span data-stu-id="c9526-119">If the *DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT or SQL_DRIVER_COMPLETE_REQUIRED and the language or database comes from the ODBC data source definitions and either is invalid, `SQLDriverConnect` uses the default language or database for the specified user ID and returns SQL_SUCCESS_WITH_INFO.</span></span>  
  
 <span data-ttu-id="c9526-120">如果*DriverCompletion*參數值為 SQL_DRIVER_COMPLETE 或 SQL_DRIVER_PROMPT，而語言或資料庫無效，則會重新引發 `SQLDriverConnect` 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="c9526-120">If the *DriverCompletion* parameter value is SQL_DRIVER_COMPLETE or SQL_DRIVER_PROMPT and if the language or database is invalid, `SQLDriverConnect` redisplays the dialog box.</span></span>  
  
## <a name="sqldriverconnect-support-for-high-availability-disaster-recovery"></a><span data-ttu-id="c9526-121">高可用性/災害復原的 SQLDriverConnect 支援</span><span class="sxs-lookup"><span data-stu-id="c9526-121">SQLDriverConnect Support for High Availability, Disaster Recovery</span></span>  
 <span data-ttu-id="c9526-122">如需使用連線到叢集的詳細資訊 `SQLDriverConnect` [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] ，請參閱[高可用性和嚴重損壞修復 SQL Server Native Client 支援](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md)。</span><span class="sxs-lookup"><span data-stu-id="c9526-122">For more information about using `SQLDriverConnect` to connect to a [!INCLUDE[ssHADR](../../includes/sshadr-md.md)] cluster, see [SQL Server Native Client Support for High Availability, Disaster Recovery](../native-client/features/sql-server-native-client-support-for-high-availability-disaster-recovery.md).</span></span>  
  
## <a name="sqldriverconnect-support-for-service-principal-names-spns"></a><span data-ttu-id="c9526-123">服務主要名稱 (SPN) 的 SQLDriverConnect 支援</span><span class="sxs-lookup"><span data-stu-id="c9526-123">SQLDriverConnect Support for Service Principal Names (SPNs)</span></span>  
 <span data-ttu-id="c9526-124">SQLDDriverConnect 將會使用 [ODBC 登入] 對話方塊 boxwhen 提示已啟用。</span><span class="sxs-lookup"><span data-stu-id="c9526-124">SQLDDriverConnect will use the ODBC Login dialog boxwhen prompting is enabled.</span></span> <span data-ttu-id="c9526-125">如此可允許同時針對主體伺服器和它的容錯移轉夥伴來輸入 SPN。</span><span class="sxs-lookup"><span data-stu-id="c9526-125">This allows SPNs to be entered for both the principal server and its failover partner.</span></span>  
  
 <span data-ttu-id="c9526-126">SQLDriverConnect 將會接受新的連接字串關鍵字 `ServerSPN` 和 `FailoverPartnerSPN` ，並將會辨識新的連接屬性 SQL_COPT_SS_SERVER_SPN 和 SQL_COPT_SS_FAILOVER_PARTNER_SPN。</span><span class="sxs-lookup"><span data-stu-id="c9526-126">SQLDriverConnect will accept the new connection string keywords `ServerSPN` and `FailoverPartnerSPN`, and will recognize the new connection attributes SQL_COPT_SS_SERVER_SPN and SQL_COPT_SS_FAILOVER_PARTNER_SPN.</span></span>  
  
 <span data-ttu-id="c9526-127">當指定連接屬性值一次以上時，以程式設計方式設定的值會優先於 DSN 中的值與連接字串中的值。</span><span class="sxs-lookup"><span data-stu-id="c9526-127">When a connection attribute value is specified more than once, a value that is set programmatically takes precedence over the value in a DSN and a value in a connection string.</span></span> <span data-ttu-id="c9526-128">DSN 中的值優先於連接字串中的值。</span><span class="sxs-lookup"><span data-stu-id="c9526-128">A value in a DSN takes precedence over a value in a connection string.</span></span>  
  
 <span data-ttu-id="c9526-129">開啟連接時，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 會將 SQL_COPT_SS_MUTUALLY_AUTHENTICATED 和 SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD 設定為開啟連接所使用的驗證方法。</span><span class="sxs-lookup"><span data-stu-id="c9526-129">When a connection is opened, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client sets SQL_COPT_SS_MUTUALLY_AUTHENTICATED and SQL_COPT_SS_INTEGRATED_AUTHENTICATION_METHOD to the authentication method used to open the connection.</span></span>  
  
 <span data-ttu-id="c9526-130">如需 Spn 的詳細資訊，請參閱[&#40;ODBC&#41;的用戶端連接中 &#40;spn&#41; 的服務主體名稱](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="c9526-130">For more information about SPNs, see [Service Principal Names &#40;SPNs&#41; in Client Connections &#40;ODBC&#41;](../native-client/odbc/service-principal-names-spns-in-client-connections-odbc.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c9526-131">範例</span><span class="sxs-lookup"><span data-stu-id="c9526-131">Examples</span></span>  
 <span data-ttu-id="c9526-132">下列呼叫說明所需的最少量資料量 `SQLDriverConnect` ：</span><span class="sxs-lookup"><span data-stu-id="c9526-132">The following call illustrates the least amount of data required for `SQLDriverConnect`:</span></span>  
  
```  
SQLDriverConnect(hdbc, hwnd,  
    (SQLTCHAR*) TEXT("DRIVER={SQL Server Native Client 10};"), SQL_NTS, szOutConn,  
    MAX_CONN_OUT, &cbOutConn, SQL_DRIVER_COMPLETE);  
```  
  
 <span data-ttu-id="c9526-133">下列連接字串說明 SQL_DRIVER_NOPROMPT *DriverCompletion*參數值時所需的最小資料：</span><span class="sxs-lookup"><span data-stu-id="c9526-133">The following connection strings illustrate minimum required data when the *DriverCompletion* parameter value is SQL_DRIVER_NOPROMPT:</span></span>  
  
```  
"DSN=Human Resources;Trusted_Connection=yes"  
  
"FILEDSN=HR_FDSN;Trusted_Connection=yes"  
  
"DRIVER={SQL Server Native Client 10};SERVER=(local);Trusted_Connection=yes"  
```  
  
## <a name="see-also"></a><span data-ttu-id="c9526-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c9526-134">See Also</span></span>  
 <span data-ttu-id="c9526-135">[SQLDriverConnect 函式](https://go.microsoft.com/fwlink/?LinkId=59340) </span><span class="sxs-lookup"><span data-stu-id="c9526-135">[SQLDriverConnect Function](https://go.microsoft.com/fwlink/?LinkId=59340) </span></span>  
 <span data-ttu-id="c9526-136">[ODBC API 的執行詳細資料](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="c9526-136">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 <span data-ttu-id="c9526-137">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9526-137">[SET ANSI_NULLS &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-nulls-transact-sql) </span></span>  
 <span data-ttu-id="c9526-138">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="c9526-138">[SET ANSI_PADDING &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-ansi-padding-transact-sql) </span></span>  
 [<span data-ttu-id="c9526-139">SET ANSI_WARNINGS &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="c9526-139">SET ANSI_WARNINGS &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/statements/set-ansi-warnings-transact-sql)  
  
  
