---
title: " (ODBC) 大量複製 SELECT 結果集 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC]
- bulk copy [ODBC], data files
- bulk copy [ODBC], about bulk copy
ms.assetid: 63d5a87b-4d5f-449b-8c77-9f9cc6b190d4
author: rothja
ms.author: jroth
ms.openlocfilehash: 6476d603a61b9dee0a8a71cb3ec1fa865d1156f3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709361"
---
# <a name="bulk-copy-a-select-result-set-odbc"></a><span data-ttu-id="23a41-102">大量複製 SELECT 結果集 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="23a41-102">Bulk Copy a SELECT Result Set (ODBC)</span></span>
  <span data-ttu-id="23a41-103">此範例會示範如何使用大量複製函數來大量複製 SELECT 陳述式的結果集。</span><span class="sxs-lookup"><span data-stu-id="23a41-103">This sample shows how to use bulk copy functions to bulk copy out the result set of a SELECT statement.</span></span> <span data-ttu-id="23a41-104">此範例是針對 ODBC 3.0 版或更新版本所開發。</span><span class="sxs-lookup"><span data-stu-id="23a41-104">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="23a41-105">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="23a41-105">When possible, use Windows Authentication.</span></span> <span data-ttu-id="23a41-106">如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。</span><span class="sxs-lookup"><span data-stu-id="23a41-106">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="23a41-107">請避免將認證儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="23a41-107">Avoid storing credentials in a file.</span></span> <span data-ttu-id="23a41-108">如果您必須保存認證，您應該使用[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)將它們加密。</span><span class="sxs-lookup"><span data-stu-id="23a41-108">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-bulk-copy-out-the-result-set-of-a-select-statement"></a><span data-ttu-id="23a41-109">大量複製 SELECT 陳述式的結果集</span><span class="sxs-lookup"><span data-stu-id="23a41-109">To bulk copy out the result set of a SELECT statement</span></span>  
  
1.  <span data-ttu-id="23a41-110">配置環境控制代碼和連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="23a41-110">Allocate an environment handle and a connection handle.</span></span>  
  
2.  <span data-ttu-id="23a41-111">將 SQL_COPT_SS_BCP 和 SQL_BCP_ON 設定為啟用大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="23a41-111">Set SQL_COPT_SS_BCP and SQL_BCP_ON to enable bulk copy operations.</span></span>  
  
3.  <span data-ttu-id="23a41-112">連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="23a41-112">Connect to SQL Server.</span></span>  
  
4.  <span data-ttu-id="23a41-113">呼叫[bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)以設定下列資訊：</span><span class="sxs-lookup"><span data-stu-id="23a41-113">Call [bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to set the following information:</span></span>  
  
    -   <span data-ttu-id="23a41-114">為*szTable*參數指定 Null。</span><span class="sxs-lookup"><span data-stu-id="23a41-114">Specify NULL for the *szTable* parameter.</span></span>  
  
    -   <span data-ttu-id="23a41-115">接收結果集資料的資料檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="23a41-115">The name of the data file that receives result set data.</span></span>  
  
    -   <span data-ttu-id="23a41-116">要接收任何大量複製錯誤訊息的資料檔案名稱 (如果您不需要訊息檔案，請指定 NULL)。</span><span class="sxs-lookup"><span data-stu-id="23a41-116">The name of a data file to receive any bulk copy error messages (specify NULL if you do not want a message file).</span></span>  
  
    -   <span data-ttu-id="23a41-117">複製的方向：DB_OUT。</span><span class="sxs-lookup"><span data-stu-id="23a41-117">The direction of the copy: DB_OUT.</span></span>  
  
5.  <span data-ttu-id="23a41-118">呼叫[bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)，將 eOption 設定為 BCPHINTS，並將指標放在 IVALUE 包含 SELECT 語句的 SQLTCHAR 陣列。</span><span class="sxs-lookup"><span data-stu-id="23a41-118">Call [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md), set eOption to BCPHINTS and place in iValue a pointer to a SQLTCHAR array containing the SELECT statement.</span></span>  
  
6.  <span data-ttu-id="23a41-119">呼叫[bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)以執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="23a41-119">Call [bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) to execute the bulk copy operation.</span></span>  
  
 <span data-ttu-id="23a41-120">使用這些步驟時，檔案會以原生格式建立。</span><span class="sxs-lookup"><span data-stu-id="23a41-120">When using these steps the file is created in native format.</span></span> <span data-ttu-id="23a41-121">您可以使用[bcp_colfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)，將資料值轉換成其他資料類型。</span><span class="sxs-lookup"><span data-stu-id="23a41-121">You can convert the data values to other data types by using [bcp_colfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md).</span></span> <span data-ttu-id="23a41-122">如需詳細資訊，請參閱[&#40;ODBC&#41;建立大量複製格式](create-a-bulk-copy-format-file-odbc.md)檔案。</span><span class="sxs-lookup"><span data-stu-id="23a41-122">For more information, see [Create a Bulk Copy Format File &#40;ODBC&#41;](create-a-bulk-copy-format-file-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="23a41-123">範例</span><span class="sxs-lookup"><span data-stu-id="23a41-123">Example</span></span>  
 <span data-ttu-id="23a41-124">您需要名為 AdventureWorks 的 ODBC 資料來源，其預設資料庫為 AdventureWorks 範例資料庫 </span><span class="sxs-lookup"><span data-stu-id="23a41-124">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="23a41-125"> (您可以從 [ [Microsoft SQL Server 範例] 和 [社區專案](https://go.microsoft.com/fwlink/?LinkID=85384)] 首頁下載 AdventureWorks 範例資料庫。 ) 此資料來源必須以作業系統所提供的 ODBC 驅動程式為基礎， (驅動程式名稱為 "SQL Server" ) 。</span><span class="sxs-lookup"><span data-stu-id="23a41-125">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="23a41-126">如果您要建立並執行此範例，當做 64 位元作業系統上的 32 位元應用程式，您必須利用 %windir%\SysWOW64\odbcad32.exe，以 ODBC 管理員身分建立 ODBC 資料來源。</span><span class="sxs-lookup"><span data-stu-id="23a41-126">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="23a41-127">這個範例會連接到電腦的預設 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="23a41-127">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="23a41-128">若要連接到具名執行個體，請變更 ODBC 資料來源的定義，以便使用下列格式指定執行個體：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="23a41-128">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="23a41-129">根據預設，[!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] 會安裝至具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="23a41-129">By default, [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="23a41-130">使用 odbc32.lib 和 odbcbcp.lib 編譯。</span><span class="sxs-lookup"><span data-stu-id="23a41-130">Compile with odbc32.lib and odbcbcp.lib.</span></span>  
  
```  
// compile with: odbc32.lib odbcbcp.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
#define MAXBUFLEN 256  
  
SQLHENV henv = SQL_NULL_HENV;  
HDBC hdbc1 = SQL_NULL_HDBC;  
  
void Cleanup() {  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // Bulk copy variables.  
   SDWORD cRows;  
   SQLTCHAR szBCPQuery[] = "SELECT BirthDate FROM HumanResources.Employee";  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle, set bulk copy mode, and then connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLSetConnectAttr(hdbc1, SQL_COPT_SS_BCP, (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetConnectAttr(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample use Integrated Security, create SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, NULL, "BCPODBC.bcp", "BCPERROR.out", DB_OUT);  
   // The test is for the bulk copy return of SUCCEED, not the ODBC return of SQL_SUCCESS.  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Specify the query to use.  
   retcode = bcp_control(hdbc1, BCPHINTS, (void *)szBCPQuery);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_control(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the bulk copy.  
   retcode = bcp_exec(hdbc1, &cRows);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_exec(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied out = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="23a41-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="23a41-131">See Also</span></span>  
 [<span data-ttu-id="23a41-132">使用 SQL Server ODBC 驅動程式的大量複製如何 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="23a41-132">Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;</span></span>](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md)  
  
  
