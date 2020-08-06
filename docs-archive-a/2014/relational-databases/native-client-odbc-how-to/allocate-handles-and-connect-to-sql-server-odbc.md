---
title: 配置控制碼並連接到 SQL Server (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- handles [ODBC]
- handles [ODBC], connection
- handles [ODBC], about handles
ms.assetid: 6172cd52-9c9a-467d-992f-def07f3f3bb1
author: rothja
ms.author: jroth
ms.openlocfilehash: 615a6dbe966b4c681e9cd4285ff55864d7a13370
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709365"
---
# <a name="allocate-handles-and-connect-to-sql-server-odbc"></a><span data-ttu-id="2f3b6-102">配置控制代碼並連接到 SQL Server (ODBC)</span><span class="sxs-lookup"><span data-stu-id="2f3b6-102">Allocate Handles and Connect to SQL Server (ODBC)</span></span>
    
### <a name="to-allocate-handles-and-connect-to-sql-server"></a><span data-ttu-id="2f3b6-103">配置控制代碼並連接到 SQL Server</span><span class="sxs-lookup"><span data-stu-id="2f3b6-103">To allocate handles and connect to SQL Server</span></span>  
  
1.  <span data-ttu-id="2f3b6-104">加入 ODBC 標頭檔 Sql.h、Sqlext.h、Sqltypes.h。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-104">Include the ODBC header files Sql.h, Sqlext.h, Sqltypes.h.</span></span>  
  
2.  <span data-ttu-id="2f3b6-105">加入 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 驅動程式專屬的標頭檔 Odbcss.h。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-105">Include the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] driver-specific header file, Odbcss.h.</span></span>  
  
3.  <span data-ttu-id="2f3b6-106">使用 SQL_HANDLE_ENV 的呼叫[SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) ， `HandleType` 以初始化 ODBC 並配置環境控制碼。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-106">Call [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) with a `HandleType` of SQL_HANDLE_ENV to initialize ODBC and allocate an environment handle.</span></span>  
  
4.  <span data-ttu-id="2f3b6-107">呼叫[SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) `Attribute` 並將設定為 SQL_ATTR_ODBC_VERSION，並 `ValuePtr` 將設定為 SQL_OV_ODBC3，以指示應用程式將使用 ODBC 3.x 格式函式呼叫。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-107">Call [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) with `Attribute` set to SQL_ATTR_ODBC_VERSION and `ValuePtr` set to SQL_OV_ODBC3 to indicate the application will use ODBC 3.x-format function calls.</span></span>  
  
5.  <span data-ttu-id="2f3b6-108">（選擇性）呼叫[SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md)以設定其他環境選項，或呼叫[SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403)來取得環境選項。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-108">Optionally, call [SQLSetEnvAttr](../native-client-odbc-api/sqlsetenvattr.md) to set other environment options, or call [SQLGetEnvAttr](https://go.microsoft.com/fwlink/?LinkId=58403) to get environment options.</span></span>  
  
6.  <span data-ttu-id="2f3b6-109">使用[SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) `HandleType` SQL_HANDLE_DBC 的呼叫 SQLAllocHandle，以配置連接控制碼。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-109">Call [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) with a `HandleType` of SQL_HANDLE_DBC to allocate a connection handle.</span></span>  
  
7.  <span data-ttu-id="2f3b6-110">（選擇性）呼叫[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)來設定連接選項，或呼叫[SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md)來取得連接選項。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-110">Optionally, call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) to set connection options, or call [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) to get connection options.</span></span>  
  
8.  <span data-ttu-id="2f3b6-111">呼叫 SQLConnect，以使用現有的資料來源連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-111">Call SQLConnect to use an existing data source to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="2f3b6-112">或者</span><span class="sxs-lookup"><span data-stu-id="2f3b6-112">Or</span></span>  
  
     <span data-ttu-id="2f3b6-113">呼叫[SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) ，以使用連接字串連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-113">Call [SQLDriverConnect](../native-client-odbc-api/sqldriverconnect.md) to use a connection string to connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
     <span data-ttu-id="2f3b6-114">完整的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 連接字串至少擁有下列其中一種形式：</span><span class="sxs-lookup"><span data-stu-id="2f3b6-114">A minimum complete [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] connection string has one of two forms:</span></span>  
  
    ```  
    DSN=dsn_name;Trusted_connection=yes;  
    DRIVER={SQL Server Native Client 10.0};SERVER=server;Trusted_connection=yes;  
    ```  
  
     <span data-ttu-id="2f3b6-115">如果連接字串不完整，`SQLDriverConnect` 可以提示所需的資訊。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-115">If the connection string is not complete, `SQLDriverConnect` can prompt for the required information.</span></span> <span data-ttu-id="2f3b6-116">這是由指定給*DriverCompletion*參數的值所控制。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-116">This is controlled by the value specified for the *DriverCompletion* parameter.</span></span>  
  
     <span data-ttu-id="2f3b6-117">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="2f3b6-117">\- or -</span></span>  
  
     <span data-ttu-id="2f3b6-118">以反復方式多次呼叫[SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md) ，以建立連接字串並連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-118">Call [SQLBrowseConnect](../native-client-odbc-api/sqlbrowseconnect.md) multiple times in an iterative fashion to build the connection string and connect to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
9. <span data-ttu-id="2f3b6-119">（選擇性）呼叫[SQLGetInfo](../native-client-odbc-api/sqlgetinfo.md)以取得資料來源的驅動程式屬性和行為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-119">Optionally, call [SQLGetInfo](../native-client-odbc-api/sqlgetinfo.md) to get driver attributes and behavior for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data source.</span></span>  
  
10. <span data-ttu-id="2f3b6-120">配置與使用陳述式。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-120">Allocate and use statements.</span></span>  
  
11. <span data-ttu-id="2f3b6-121">呼叫 SQLDisconnect 以中斷與的連線 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，並讓連接控制碼可用於新的連接。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-121">Call SQLDisconnect to disconnect from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and make the connection handle available for a new connection.</span></span>  
  
12. <span data-ttu-id="2f3b6-122">使用[SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) `HandleType` SQL_HANDLE_DBC 的呼叫 SQLFreeHandle 來釋放連接控制碼。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-122">Call [SQLFreeHandle](../native-client-odbc-api/sqlfreehandle.md) with a `HandleType` of SQL_HANDLE_DBC to free the connection handle.</span></span>  
  
13. <span data-ttu-id="2f3b6-123">利用 SQL_HANDLE_ENV 的 `SQLFreeHandle` 呼叫 `HandleType` 來釋放環境控制代碼。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-123">Call `SQLFreeHandle` with a `HandleType` of SQL_HANDLE_ENV to free the environment handle.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2f3b6-124">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-124">When possible, use Windows Authentication.</span></span> <span data-ttu-id="2f3b6-125">如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-125">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="2f3b6-126">請避免將認證儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-126">Avoid storing credentials in a file.</span></span> <span data-ttu-id="2f3b6-127">如果您必須保存認證，您應該使用[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)將它們加密。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-127">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f3b6-128">範例</span><span class="sxs-lookup"><span data-stu-id="2f3b6-128">Example</span></span>  
 <span data-ttu-id="2f3b6-129">此範例顯示呼叫 `SQLDriverConnect` 來連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體，而不需要現有的 ODBC 資料來源。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-129">This example shows a call to `SQLDriverConnect` to connect to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] without requiring an existing ODBC data source.</span></span> <span data-ttu-id="2f3b6-130">將不完整的連接字串傳遞到 `SQLDriverConnect` 時，會使 ODBC 驅動程式提示使用者輸入遺漏的資訊。</span><span class="sxs-lookup"><span data-stu-id="2f3b6-130">By passing an incomplete connection string to `SQLDriverConnect`, it causes the ODBC driver to prompt the user to enter the missing information.</span></span>  
  
```  
#define MAXBUFLEN   255  
  
SQLHENV      henv = SQL_NULL_HENV;  
SQLHDBC      hdbc1 = SQL_NULL_HDBC;  
SQLHSTMT      hstmt1 = SQL_NULL_HSTMT;  
  
SQLCHAR      ConnStrIn[MAXBUFLEN] =  
         "DRIVER={SQL Server Native Client 10.0};SERVER=MyServer";  
  
SQLCHAR      ConnStrOut[MAXBUFLEN];  
SQLSMALLINT   cbConnStrOut = 0;  
  
// Make connection without data source. Ask that driver   
// prompt if insufficient information. Driver returns  
// SQL_ERROR and application prompts user  
// for missing information. Window handle not needed for  
// SQL_DRIVER_NOPROMPT.  
retcode = SQLDriverConnect(hdbc1,      // Connection handle  
                  NULL,         // Window handle  
                  ConnStrIn,      // Input connect string  
                  SQL_NTS,         // Null-terminated string  
                  ConnStrOut,      // Address of output buffer  
                  MAXBUFLEN,      // Size of output buffer  
                  &cbConnStrOut,   // Address of output length  
                  SQL_DRIVER_PROMPT);  
```  
  
  
