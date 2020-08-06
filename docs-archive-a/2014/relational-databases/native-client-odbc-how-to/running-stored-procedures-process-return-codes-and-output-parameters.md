---
title: " (ODBC) 處理傳回碼和輸出參數 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- return codes [ODBC]
- output parameters [ODBC]
ms.assetid: 102ae1d0-973d-4e12-992c-d844bf05160d
author: rothja
ms.author: jroth
ms.openlocfilehash: b119d43806dafa68fe049595d94e909a5a1bb896
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595930"
---
# <a name="process-return-codes-and-output-parameters-odbc"></a><span data-ttu-id="e8a4d-102">處理傳回碼和輸出參數 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="e8a4d-102">Process Return Codes and Output Parameters (ODBC)</span></span>
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="e8a4d-103">預存程序可以有整數傳回碼和輸出參數。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-103">stored procedures can have integer return codes and output parameters.</span></span> <span data-ttu-id="e8a4d-104">傳回碼和輸出參數會在來自伺服器的最後一個封包中傳送，而且在[SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)傳回 SQL_NO_DATA 之前，都無法供應用程式使用。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-104">The return codes and output parameters are sent in the last packet from the server and are not available to the application until [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) returns SQL_NO_DATA.</span></span> <span data-ttu-id="e8a4d-105">如果從預存程式傳回錯誤，請呼叫 SQLMoreResults 以前進到下一個結果，直到傳回 SQL_NO_DATA 為止。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-105">If an error is returned from a stored procedure, call SQLMoreResults to advance to the next result until SQL_NO_DATA is returned.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="e8a4d-106">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-106">When possible, use Windows Authentication.</span></span> <span data-ttu-id="e8a4d-107">如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-107">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="e8a4d-108">請避免將認證儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-108">Avoid storing credentials in a file.</span></span> <span data-ttu-id="e8a4d-109">如果您必須保存認證，您應該使用[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)將它們加密。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-109">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-process-return-codes-and-output-parameters"></a><span data-ttu-id="e8a4d-110">若要處理傳回碼和輸出參數</span><span class="sxs-lookup"><span data-stu-id="e8a4d-110">To process return codes and output parameters</span></span>  
  
1.  <span data-ttu-id="e8a4d-111">建構使用 ODBC CALL 逸出序列的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-111">Construct an SQL statement that uses the ODBC CALL escape sequence.</span></span> <span data-ttu-id="e8a4d-112">此陳述式應該會針對每個輸入、輸入/輸出和輸出參數，以及程序傳回值 (若有) 使用參數標記。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-112">The statement should use parameter markers for each input, input/output, and output parameter, and for the procedure return value (if any).</span></span>  
  
2.  <span data-ttu-id="e8a4d-113">針對每個輸入、輸入/輸出和輸出參數呼叫[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) ，如果有任何) ，則 (程式傳回值。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-113">Call [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) for each input, input/output, and output parameter, and for the procedure return value (if any).</span></span>  
  
3.  <span data-ttu-id="e8a4d-114">使用 `SQLExecDirect` 來執行此陳述式。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-114">Execute the statement with `SQLExecDirect`.</span></span>  
  
4.  <span data-ttu-id="e8a4d-115">處理結果集，直到 `SQLFetch` 或 `SQLFetchScroll` 傳回 SQL_NO_DATA 為止，同時處理最後一個結果集，直到 `SQLMoreResults` 傳回 SQL_NO_DATA 為止。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-115">Process result sets until `SQLFetch` or `SQLFetchScroll` returns SQL_NO_DATA while processing the last result set or until `SQLMoreResults` returns SQL_NO_DATA.</span></span> <span data-ttu-id="e8a4d-116">此時，繫結至傳回碼和輸出參數的變數會填入傳回的資料值。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-116">At this point, the variables bound to the return code and output parameters are filled with returned data values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8a4d-117">範例</span><span class="sxs-lookup"><span data-stu-id="e8a4d-117">Example</span></span>  
 <span data-ttu-id="e8a4d-118">此範例顯示處理傳回碼和輸出參數。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-118">This sample shows processing a return code and output parameter.</span></span> <span data-ttu-id="e8a4d-119">IA64 不支援此範例。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-119">This sample is not supported on IA64.</span></span> <span data-ttu-id="e8a4d-120">此範例是針對 ODBC 3.0 版或更新版本所開發。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-120">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
 <span data-ttu-id="e8a4d-121">您需要名為 AdventureWorks 的 ODBC 資料來源，其預設資料庫為 AdventureWorks 範例資料庫 </span><span class="sxs-lookup"><span data-stu-id="e8a4d-121">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="e8a4d-122"> (您可以從 [ [Microsoft SQL Server 範例] 和 [社區專案](https://go.microsoft.com/fwlink/?LinkID=85384)] 首頁下載 AdventureWorks 範例資料庫。 ) 此資料來源必須以作業系統所提供的 ODBC 驅動程式為基礎， (驅動程式名稱為 "SQL Server" ) 。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-122">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="e8a4d-123">如果您要建立並執行此範例，當做 64 位元作業系統上的 32 位元應用程式，您必須利用 %windir%\SysWOW64\odbcad32.exe，以 ODBC 管理員身分建立 ODBC 資料來源。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-123">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="e8a4d-124">這個範例會連接到電腦的預設 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-124">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="e8a4d-125">若要連接到具名執行個體，請變更 ODBC 資料來源的定義，以便使用下列格式指定執行個體：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-125">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="e8a4d-126">根據預設，[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 會安裝至具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-126">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="e8a4d-127">第一個 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 程式碼清單會建立此範例所使用的預存程序。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-127">The first ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing creates a stored procedure used by this sample.</span></span>  
  
 <span data-ttu-id="e8a4d-128">使用 odbc32.lib 編譯第二個 (C++) 程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-128">Compile the second (C++) code listing with odbc32.lib.</span></span> <span data-ttu-id="e8a4d-129">然後，執行此程式。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-129">Then, execute the program.</span></span>  
  
 <span data-ttu-id="e8a4d-130">第三個 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 程式碼清單會刪除此範例所使用的預存程序。</span><span class="sxs-lookup"><span data-stu-id="e8a4d-130">The third ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing deletes the stored procedure used by this sample.</span></span>  
  
```  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'TestParm')  
   DROP PROCEDURE TestParm  
GO  
  
CREATE PROCEDURE TestParm   
@OutParm int OUTPUT   
AS  
SELECT Name FROM Purchasing.Vendor  
SELECT @OutParm = 88  
RETURN 99  
go  
```  
  
```  
// compile with: odbc32.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
#define MAXBUFLEN 255  
  
SQLHENV henv = SQL_NULL_HENV;  
SQLHDBC hdbc1 = SQL_NULL_HDBC;       
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;  
  
void Cleanup() {  
   if (hstmt1 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
   // SQLBindParameter variables.  
   SWORD sParm1 = 0, sParm2 = 1;  
   SQLLEN cbParm1 = SQL_NTS;  
   SQLLEN cbParm2 = SQL_NTS;  
  
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
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // This sample use Integrated Security. Create the SQL Server DSN by using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Bind the return code to variable sParm1.  
   retcode = SQLBindParameter(hstmt1, 1, SQL_PARAM_OUTPUT, SQL_C_SSHORT, SQL_INTEGER, 0, 0, &sParm1, 0, &cbParm1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLBindParameter(sParm1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Bind the output parameter to variable sParm2.  
   retcode = SQLBindParameter(hstmt1, 2, SQL_PARAM_OUTPUT, SQL_C_SSHORT, SQL_INTEGER, 0, 0, &sParm2, 0, &cbParm2);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLBindParameter(sParm2) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the command.   
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"{? = call TestParm(?)}", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Show parameters are not filled.  
   printf("Before result sets cleared: RetCode = %d, OutParm = %d.\n", sParm1, sParm2);  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA )  
      ;  
  
   // Show parameters are now filled.  
   printf("After result sets drained: RetCode = %d, OutParm = %d.\n", sParm1, sParm2);  
  
   // Clean up.   
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
```  
use AdventureWorks  
DROP PROCEDURE TestParm  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="e8a4d-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e8a4d-131">See Also</span></span>  
 [<span data-ttu-id="e8a4d-132">執行預存程式的 how to 主題 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="e8a4d-132">Running Stored Procedures How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/running-stored-procedures-how-to-topics-odbc.md)  
  
  
