---
title: " (ODBC) 處理 ODBC 錯誤 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- errors [ODBC]
ms.assetid: 66ab0762-79fe-4a31-b655-27dd215a0af7
author: rothja
ms.author: jroth
ms.openlocfilehash: 9f42223ffda8462ec740b94eb584565dfe286e0d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706441"
---
# <a name="process-odbc-errors-odbc"></a><span data-ttu-id="2c727-102">處理 ODBC 錯誤 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="2c727-102">Process ODBC Errors (ODBC)</span></span>
  <span data-ttu-id="2c727-103">您可以使用兩個 ODBC 函式呼叫來抓取 ODBC 訊息： [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402)和[SQLGetDiagField](../native-client-odbc-api/sqlgetdiagfield.md)。</span><span class="sxs-lookup"><span data-stu-id="2c727-103">Two ODBC function calls can be used to retrieve ODBC messages: [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) and [SQLGetDiagField](../native-client-odbc-api/sqlgetdiagfield.md).</span></span> <span data-ttu-id="2c727-104">若要在 **SQLState**、**pfNative** 和 **ErrorMessage** 診斷欄位中取得與主要 ODBC 相關的資訊，請呼叫 [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402)，直到它傳回 SQL_NO_DATA 為止。</span><span class="sxs-lookup"><span data-stu-id="2c727-104">To obtain primary ODBC-related information in the **SQLState**, **pfNative**, and **ErrorMessage** diagnostic fields, call [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) until it returns SQL_NO_DATA.</span></span> <span data-ttu-id="2c727-105">對於每個診斷記錄，可以呼叫 [SQLGetDiagField](../native-client-odbc-api/sqlgetdiagfield.md) 來擷取個別的欄位。</span><span class="sxs-lookup"><span data-stu-id="2c727-105">For each diagnostic record, [SQLGetDiagField](../native-client-odbc-api/sqlgetdiagfield.md) can be called to retrieve individual fields.</span></span> <span data-ttu-id="2c727-106">所有驅動程式專用的欄位都必須使用 `SQLGetDiagField` 擷取。</span><span class="sxs-lookup"><span data-stu-id="2c727-106">All driver-specific fields must be retrieved using `SQLGetDiagField`.</span></span>  
  
 <span data-ttu-id="2c727-107">[SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) 和 [SQLGetDiagField](../native-client-odbc-api/sqlgetdiagfield.md) 是透過 ODBC 驅動程式管理員，而非個別的驅動程式處理。</span><span class="sxs-lookup"><span data-stu-id="2c727-107">[SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) and [SQLGetDiagField](../native-client-odbc-api/sqlgetdiagfield.md) are processed by ODBC Driver Manager, not an individual driver.</span></span> <span data-ttu-id="2c727-108">在成功建立連接之前，ODBC 驅動程式管理員不會快取驅動程式專用的診斷欄位。</span><span class="sxs-lookup"><span data-stu-id="2c727-108">ODBC Driver Manager does not cache driver-specific diagnostic fields until a successful connection has been made.</span></span> <span data-ttu-id="2c727-109">在成功連接之前，無法針對驅動程式專用的診斷欄位呼叫 [SQLGetDiagField](../native-client-odbc-api/sqlgetdiagfield.md)。</span><span class="sxs-lookup"><span data-stu-id="2c727-109">Calling [SQLGetDiagField](../native-client-odbc-api/sqlgetdiagfield.md) for driver-specific diagnostic fields is not possible before a successful connection.</span></span> <span data-ttu-id="2c727-110">這包含 ODBC 連接命令，即使它們傳回 SQL_SUCCESS_WITH_INFO 也一樣。</span><span class="sxs-lookup"><span data-stu-id="2c727-110">This includes the ODBC connection commands, even if they return SQL_SUCCESS_WITH_INFO.</span></span> <span data-ttu-id="2c727-111">在下次呼叫 ODBC 函數之前，將無法使用驅動程式專用的診斷欄位。</span><span class="sxs-lookup"><span data-stu-id="2c727-111">Driver-specific diagnostic fields will not be available until the next ODBC function call.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c727-112">範例</span><span class="sxs-lookup"><span data-stu-id="2c727-112">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="2c727-113">描述</span><span class="sxs-lookup"><span data-stu-id="2c727-113">Description</span></span>  
 <span data-ttu-id="2c727-114">此範例會顯示呼叫標準 ODBC 資訊之 [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) 的簡單錯誤處理常式。</span><span class="sxs-lookup"><span data-stu-id="2c727-114">This sample shows a simple error handler that calls [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) for the standard ODBC information.</span></span> <span data-ttu-id="2c727-115">然後它會測試是否有有效連接，如果有，就會為 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC 驅動程式專用的診斷欄位呼叫 `SQLGetDiagField`。</span><span class="sxs-lookup"><span data-stu-id="2c727-115">It then tests for a valid connection, and if one exists, it calls `SQLGetDiagField` for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver-specific diagnostic fields.</span></span> <span data-ttu-id="2c727-116">IA64 不支援此範例。</span><span class="sxs-lookup"><span data-stu-id="2c727-116">This sample is not supported on IA64.</span></span>  
  
 <span data-ttu-id="2c727-117">此範例是針對 ODBC 3.0 版或更新版本所開發。</span><span class="sxs-lookup"><span data-stu-id="2c727-117">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="2c727-118">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="2c727-118">When possible, use Windows Authentication.</span></span> <span data-ttu-id="2c727-119">如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。</span><span class="sxs-lookup"><span data-stu-id="2c727-119">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="2c727-120">請避免將認證儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="2c727-120">Avoid storing credentials in a file.</span></span> <span data-ttu-id="2c727-121">如果您必須保存認證，您應該使用[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)將它們加密。</span><span class="sxs-lookup"><span data-stu-id="2c727-121">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
 <span data-ttu-id="2c727-122">您需要名為 AdventureWorks 的 ODBC 資料來源，其預設資料庫為 AdventureWorks 範例資料庫 </span><span class="sxs-lookup"><span data-stu-id="2c727-122">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="2c727-123"> (您可以從 [ [Microsoft SQL Server 範例] 和 [社區專案](https://go.microsoft.com/fwlink/?LinkID=85384)] 首頁下載 AdventureWorks 範例資料庫。 ) 此資料來源必須以作業系統所提供的 ODBC 驅動程式為基礎， (驅動程式名稱為 "SQL Server" ) 。</span><span class="sxs-lookup"><span data-stu-id="2c727-123">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="2c727-124">如果您要建立並執行此範例，當做 64 位元作業系統上的 32 位元應用程式，您必須利用 %windir%\SysWOW64\odbcad32.exe，以 ODBC 管理員身分建立 ODBC 資料來源。</span><span class="sxs-lookup"><span data-stu-id="2c727-124">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="2c727-125">這個範例會連接到電腦的預設 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="2c727-125">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="2c727-126">若要連接到具名執行個體，請變更 ODBC 資料來源的定義，以便使用下列格式指定執行個體：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="2c727-126">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="2c727-127">根據預設，[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 會安裝至具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="2c727-127">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="2c727-128">執行第一個 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 程式碼清單，以便建立此範例所使用的預存程序。</span><span class="sxs-lookup"><span data-stu-id="2c727-128">Execute the first ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing to create the stored procedure used by this sample.</span></span>  
  
 <span data-ttu-id="2c727-129">使用 odbc32.lib 編譯第二個 (C++) 程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="2c727-129">Compile the second (C++) code listing with odbc32.lib.</span></span> <span data-ttu-id="2c727-130">然後，執行此程式。</span><span class="sxs-lookup"><span data-stu-id="2c727-130">Then, execute the program.</span></span>  
  
 <span data-ttu-id="2c727-131">執行第三個 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 程式碼清單，以便刪除此範例所使用的預存程序。</span><span class="sxs-lookup"><span data-stu-id="2c727-131">Execute the third ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing to delete the stored procedure used by this sample.</span></span>  
  
### <a name="code"></a><span data-ttu-id="2c727-132">程式碼</span><span class="sxs-lookup"><span data-stu-id="2c727-132">Code</span></span>  
  
```  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BadOne')  
   DROP PROCEDURE BadOne  
  
Go  
  
CREATE PROCEDURE BadOne   
AS   
SELECT * FROM Purchasing.Vendor  
Go  
```  
  
### <a name="code"></a><span data-ttu-id="2c727-133">程式碼</span><span class="sxs-lookup"><span data-stu-id="2c727-133">Code</span></span>  
  
```  
// compile with: odbc32.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
#define MAXBUFLEN 256  
  
SQLHENV henv = SQL_NULL_HENV;  
SQLHDBC hdbc1 = SQL_NULL_HDBC;       
SQLHSTMT hstmt1 = SQL_NULL_HSTMT;  
  
void ProcessLogMessages(SQLSMALLINT plm_handle_type, SQLHANDLE plm_handle, char *logstring, int ConnInd);  
  
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
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, SQL_IS_INTEGER);  
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
  
   // This sample use Integrated Security. Please create the SQL Server   
   // DSN by using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) &&  
      (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         ProcessLogMessages(SQL_HANDLE_DBC, hdbc1, "SQLConnect() Failed\n\n", FALSE);  
         Cleanup();  
         return(9);  
   }  
   else {  
      ProcessLogMessages(SQL_HANDLE_DBC, hdbc1,  
         "\nConnect Successful\n\n", FALSE);  
   }  
  
   // Allocate statement handle, and then execute command.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      ProcessLogMessages(SQL_HANDLE_DBC, hdbc1, "SQLAllocHandle(hstmt1) Failed\n\n", TRUE);  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"exec BadOne", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         ProcessLogMessages(SQL_HANDLE_STMT, hstmt1, "SQLExecute() Failed\n\n", TRUE);  
         Cleanup();  
         return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA )  
      ;  
  
   // Clean up.   
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
void ProcessLogMessages(SQLSMALLINT plm_handle_type, SQLHANDLE plm_handle, char *logstring, int ConnInd) {  
   RETCODE plm_retcode = SQL_SUCCESS;  
   UCHAR plm_szSqlState[MAXBUFLEN] = "", plm_szErrorMsg[MAXBUFLEN] = "";  
   SDWORD plm_pfNativeError = 0L;  
   SWORD plm_pcbErrorMsg = 0;  
   SQLSMALLINT plm_cRecNmbr = 1;  
   SDWORD plm_SS_MsgState = 0, plm_SS_Severity = 0;  
   SQLINTEGER plm_Rownumber = 0;  
   USHORT plm_SS_Line;  
   SQLSMALLINT plm_cbSS_Procname, plm_cbSS_Srvname;  
   SQLCHAR plm_SS_Procname[MAXNAME], plm_SS_Srvname[MAXNAME];  
  
   if (logstring)  
      printf(logstring);  
  
   while (plm_retcode != SQL_NO_DATA_FOUND) {  
      plm_retcode = SQLGetDiagRec(plm_handle_type, plm_handle, plm_cRecNmbr,   
                                  plm_szSqlState, &plm_pfNativeError, plm_szErrorMsg,   
                                  MAXBUFLEN - 1, &plm_pcbErrorMsg);  
  
      // Note that if the application has not yet made a successful connection,   
      // the SQLGetDiagField information has not yet been cached by ODBC Driver Manager and   
      // these calls to SQLGetDiagField will fail.  
      if (plm_retcode != SQL_NO_DATA_FOUND) {  
         if (ConnInd) {   
            plm_retcode = SQLGetDiagField( plm_handle_type, plm_handle, plm_cRecNmbr,  
                                                        SQL_DIAG_ROW_NUMBER, &plm_Rownumber,  
                                                        SQL_IS_INTEGER, NULL);  
  
            plm_retcode = SQLGetDiagField( plm_handle_type, plm_handle, plm_cRecNmbr,  
                                           SQL_DIAG_SS_LINE, &plm_SS_Line, SQL_IS_INTEGER, NULL);  
  
            plm_retcode = SQLGetDiagField( plm_handle_type, plm_handle, plm_cRecNmbr,   
                                           SQL_DIAG_SS_MSGSTATE, &plm_SS_MsgState,  
                                           SQL_IS_INTEGER, NULL);  
  
            plm_retcode = SQLGetDiagField( plm_handle_type, plm_handle, plm_cRecNmbr,  
                                           SQL_DIAG_SS_SEVERITY, &plm_SS_Severity,  
                                           SQL_IS_INTEGER, NULL);  
  
            plm_retcode = SQLGetDiagField( plm_handle_type, plm_handle, plm_cRecNmbr,  
                                           SQL_DIAG_SS_PROCNAME, &plm_SS_Procname,  
                                           sizeof(plm_SS_Procname), &plm_cbSS_Procname);  
  
            plm_retcode = SQLGetDiagField( plm_handle_type, plm_handle, plm_cRecNmbr,  
                                           SQL_DIAG_SS_SRVNAME, &plm_SS_Srvname,   
                                           sizeof(plm_SS_Srvname), &plm_cbSS_Srvname);  
         }  
  
         printf("szSqlState = %s\n", plm_szSqlState);  
         printf("pfNativeError = %d\n", plm_pfNativeError);  
         printf("szErrorMsg = %s\n", plm_szErrorMsg);  
         printf("pcbErrorMsg = %d\n\n", plm_pcbErrorMsg);  
  
         if (ConnInd) {  
            printf("ODBCRowNumber = %d\n", plm_Rownumber);  
            printf("SSrvrLine = %d\n", plm_Rownumber);  
            printf("SSrvrMsgState = %d\n", plm_SS_MsgState);  
            printf("SSrvrSeverity = %d\n", plm_SS_Severity);  
            printf("SSrvrProcname = %s\n", plm_SS_Procname);  
            printf("SSrvrSrvname = %s\n\n", plm_SS_Srvname);  
         }  
      }  
  
      plm_cRecNmbr++;   // Increment to next diagnostic record.  
   }  
}  
```  
  
### <a name="code"></a><span data-ttu-id="2c727-134">程式碼</span><span class="sxs-lookup"><span data-stu-id="2c727-134">Code</span></span>  
  
```  
use AdventureWorks  
DROP PROCEDURE BadOne  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c727-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2c727-135">See Also</span></span>  
 [<span data-ttu-id="2c727-136">ODBC 的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="2c727-136">ODBC How-to Topics</span></span>](odbc-how-to-topics.md)  
  
  
