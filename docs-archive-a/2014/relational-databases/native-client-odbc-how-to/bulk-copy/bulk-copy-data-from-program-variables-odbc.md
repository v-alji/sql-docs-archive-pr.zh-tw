---
title: 從程式變數大量資料複製 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], program variables
- bulk copy [ODBC]
ms.assetid: 0c3f2d7c-4ff2-4887-adfd-1f488a27c21c
author: rothja
ms.author: jroth
ms.openlocfilehash: e6e1c5294611b280aea8e67963613971f2690c44
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709357"
---
# <a name="bulk-copy-data-from-program-variables-odbc"></a><span data-ttu-id="d94b9-102">從程式變數中大量複製資料 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="d94b9-102">Bulk Copy Data from Program Variables (ODBC)</span></span>
  <span data-ttu-id="d94b9-103">此範例會示範如何使用大量複製函數，透過 `bcp_bind` 和 `bcp_sendrow` 從程式變數大量複製資料到 SQL Server </span><span class="sxs-lookup"><span data-stu-id="d94b9-103">This sample shows how to use bulk copy functions to bulk copy data from program variables to SQL Server using `bcp_bind` and `bcp_sendrow`.</span></span> <span data-ttu-id="d94b9-104">(為了簡化這個範例會移除錯誤檢查程式碼)。</span><span class="sxs-lookup"><span data-stu-id="d94b9-104">(Error-checking code is removed to simplify this example.)</span></span>  
  
 <span data-ttu-id="d94b9-105">此範例是針對 ODBC 3.0 版或更新版本所開發。</span><span class="sxs-lookup"><span data-stu-id="d94b9-105">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
 <span data-ttu-id="d94b9-106">**安全性注意事項**可能的話，請使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="d94b9-106">**Security Note** When possible, use Windows Authentication.</span></span> <span data-ttu-id="d94b9-107">如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。</span><span class="sxs-lookup"><span data-stu-id="d94b9-107">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="d94b9-108">請避免將認證儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="d94b9-108">Avoid storing credentials in a file.</span></span> <span data-ttu-id="d94b9-109">如果您必須保存認證，則應該用 [Win32 cryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504) 加密這些認證。</span><span class="sxs-lookup"><span data-stu-id="d94b9-109">If you must persist credentials, you should encrypt them with [the Win32 cryptoAPI](https://go.microsoft.com/fwlink/?LinkId=9504).</span></span>  
  
### <a name="to-use-bulk-copy-functions-directly-on-program-variables"></a><span data-ttu-id="d94b9-110">若要直接針對程式變數使用大量複製函數</span><span class="sxs-lookup"><span data-stu-id="d94b9-110">To use bulk copy functions directly on program variables</span></span>  
  
1.  <span data-ttu-id="d94b9-111">配置環境控制代碼和連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="d94b9-111">Allocate an environment handle and a connection handle.</span></span>  
  
2.  <span data-ttu-id="d94b9-112">將 SQL_COPT_SS_BCP 和 SQL_BCP_ON 設定為啟用大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="d94b9-112">Set SQL_COPT_SS_BCP and SQL_BCP_ON to enable bulk copy operations.</span></span>  
  
3.  <span data-ttu-id="d94b9-113">連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="d94b9-113">Connect to SQL Server.</span></span>  
  
4.  <span data-ttu-id="d94b9-114">呼叫[bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)以設定下列資訊：</span><span class="sxs-lookup"><span data-stu-id="d94b9-114">Call [bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to set the following information:</span></span>  
  
    -   <span data-ttu-id="d94b9-115">要進行大量複製之來源或目標資料表或檢視表的名稱。</span><span class="sxs-lookup"><span data-stu-id="d94b9-115">The name of the table or view to bulk copy from or to.</span></span>  
  
    -   <span data-ttu-id="d94b9-116">針對資料檔案的名稱指定 NULL。</span><span class="sxs-lookup"><span data-stu-id="d94b9-116">Specify NULL for the name of the data file.</span></span>  
  
    -   <span data-ttu-id="d94b9-117">要接收任何大量複製錯誤訊息的資料檔案名稱 (如果您不需要訊息檔案，請指定 NULL)。</span><span class="sxs-lookup"><span data-stu-id="d94b9-117">The name of an data file to receive any bulk copy error messages (specify NULL if you do not want a message file).</span></span>  
  
    -   <span data-ttu-id="d94b9-118">複製的方向：DB_IN (從應用程式到檢視表或資料表) 或 DB_OUT (從資料表或檢視表到應用程式)。</span><span class="sxs-lookup"><span data-stu-id="d94b9-118">The direction of the copy: DB_IN from the application to the view or table or DB_OUT to the application from the table or view.</span></span>  
  
5.  <span data-ttu-id="d94b9-119">針對大量複製中的每個資料行呼叫[bcp_bind](../../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) ，以將資料行系結至程式變數。</span><span class="sxs-lookup"><span data-stu-id="d94b9-119">Call [bcp_bind](../../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) for each column in the bulk copy to bind the column to a program variable.</span></span>  
  
6.  <span data-ttu-id="d94b9-120">使用資料填入程式變數，並呼叫[bcp_sendrow](../../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)來傳送資料列。</span><span class="sxs-lookup"><span data-stu-id="d94b9-120">Fill the program variables with data, and call [bcp_sendrow](../../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) to send a row of data.</span></span>  
  
7.  <span data-ttu-id="d94b9-121">傳送數個數據列之後，請呼叫[bcp_batch](../../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md)來檢查已傳送的資料列。</span><span class="sxs-lookup"><span data-stu-id="d94b9-121">After several rows have been sent, call [bcp_batch](../../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) to checkpoint the rows already sent.</span></span> <span data-ttu-id="d94b9-122">最好至少為每1000個數據列呼叫[bcp_batch](../../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md)一次。</span><span class="sxs-lookup"><span data-stu-id="d94b9-122">It is good practice to call [bcp_batch](../../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md) at least once per 1000 rows.</span></span>  
  
8.  <span data-ttu-id="d94b9-123">傳送所有資料列之後，請呼叫[bcp_done](../../native-client-odbc-extensions-bulk-copy-functions/bcp-done.md)以完成作業。</span><span class="sxs-lookup"><span data-stu-id="d94b9-123">After all rows have been sent, call [bcp_done](../../native-client-odbc-extensions-bulk-copy-functions/bcp-done.md) to complete the operation.</span></span>  
  
 <span data-ttu-id="d94b9-124">您可以藉由呼叫[bcp_colptr](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md)和[bcp_collen](../../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md)，在大量複製作業期間改變程式變數的位置和長度。</span><span class="sxs-lookup"><span data-stu-id="d94b9-124">You can vary the location and length of program variables during a bulk copy operation by calling [bcp_colptr](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colptr.md) and [bcp_collen](../../native-client-odbc-extensions-bulk-copy-functions/bcp-collen.md).</span></span> <span data-ttu-id="d94b9-125">使用[bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)來設定各種大量複製選項。</span><span class="sxs-lookup"><span data-stu-id="d94b9-125">Use [bcp_control](../../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md) to set various bulk copy options.</span></span> <span data-ttu-id="d94b9-126">使用[bcp_moretext](../../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) ，將 `text` `ntext` `image` 區段中的、和資料傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="d94b9-126">Use [bcp_moretext](../../native-client-odbc-extensions-bulk-copy-functions/bcp-moretext.md) to send `text`, `ntext`, and `image` data in segments to the server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d94b9-127">範例</span><span class="sxs-lookup"><span data-stu-id="d94b9-127">Example</span></span>  
 <span data-ttu-id="d94b9-128">IA64 不支援此範例。</span><span class="sxs-lookup"><span data-stu-id="d94b9-128">This sample is not supported on IA64.</span></span>  
  
 <span data-ttu-id="d94b9-129">您需要名為 AdventureWorks 的 ODBC 資料來源，其預設資料庫為 AdventureWorks 範例資料庫 </span><span class="sxs-lookup"><span data-stu-id="d94b9-129">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="d94b9-130"> (您可以從 [ [Microsoft SQL Server 範例] 和 [社區專案](https://go.microsoft.com/fwlink/?LinkID=85384)] 首頁下載 AdventureWorks 範例資料庫。 ) 此資料來源必須以作業系統所提供的 ODBC 驅動程式為基礎， (驅動程式名稱為 "SQL Server" ) 。</span><span class="sxs-lookup"><span data-stu-id="d94b9-130">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="d94b9-131">如果您要建立並執行此範例，當做 64 位元作業系統上的 32 位元應用程式，您必須利用 %windir%\SysWOW64\odbcad32.exe，以 ODBC 管理員身分建立 ODBC 資料來源。</span><span class="sxs-lookup"><span data-stu-id="d94b9-131">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="d94b9-132">這個範例會連接到電腦的預設 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d94b9-132">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="d94b9-133">若要連接到具名執行個體，請變更 ODBC 資料來源的定義，以便使用下列格式指定執行個體：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="d94b9-133">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="d94b9-134">根據預設，[!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] 會安裝至具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="d94b9-134">By default, [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="d94b9-135">執行第一個 ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) 程式碼清單，以便建立此範例將使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="d94b9-135">Execute the first ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to create tables that the sample will use.</span></span>  
  
 <span data-ttu-id="d94b9-136">使用 odbc32.lib 和 odbcbcp.lib 編譯第二個 (C++) 程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="d94b9-136">Compile the second (C++) code listing with odbc32.lib and odbcbcp.lib.</span></span> <span data-ttu-id="d94b9-137">如果您使用 MSBuild.exe 建立，請將 Bcpfmt.fmt 和 Bcpodbc.bcp 從專案目錄複製到具有該 .exe 的目錄，然後叫用該 .exe。</span><span class="sxs-lookup"><span data-stu-id="d94b9-137">If you built with MSBuild.exe, copy Bcpfmt.fmt and Bcpodbc.bcp from the project directory into the directory with the .exe and then invoke the .exe.</span></span>  
  
 <span data-ttu-id="d94b9-138">執行第三個 ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) 程式碼清單，以便刪除此範例所使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="d94b9-138">Execute the third ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to delete the tables that the sample used.</span></span>  
  
```  
// compile with: odbc32.lib odbcbcp.lib  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPSource')  
     DROP TABLE BCPSource  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPTarget')  
     DROP TABLE BCPTarget  
GO  
  
CREATE TABLE BCPSource (cola int PRIMARY KEY, colb CHAR(10) NULL)  
INSERT INTO BCPSource (cola, colb) VALUES (1, 'aaa')  
INSERT INTO BCPSource (cola, colb) VALUES (2, 'bbb')  
CREATE TABLE BCPTarget (cola int PRIMARY KEY, colb CHAR(10) NULL)  
```  
  
```  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
SQLHENV henv = SQL_NULL_HENV;  
HDBC hdbc1 = SQL_NULL_HDBC, hdbc2 = SQL_NULL_HDBC;  
SQLHSTMT hstmt2 = SQL_NULL_HSTMT;  
  
void Cleanup() {  
   if (hstmt2 != SQL_NULL_HSTMT)  
      SQLFreeHandle(SQL_HANDLE_STMT, hstmt2);  
  
   if (hdbc1 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc1);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   }  
  
   if (hdbc2 != SQL_NULL_HDBC) {  
      SQLDisconnect(hdbc2);  
      SQLFreeHandle(SQL_HANDLE_DBC, hdbc2);  
   }  
  
   if (henv != SQL_NULL_HENV)  
      SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
  
int main() {  
   RETCODE retcode;  
  
   // BCP variables.  
   char *terminator = "\0";  
  
   // bcp_done takes a different format return code because it returns number of rows bulk copied  
   // after the last bcp_batch call.  
   DBINT cRowsDone = 0;  
  
   // Set up separate return code for bcp_sendrow so it is not using the same retcode as SQLFetch.  
   RETCODE SendRet;  
  
   // Column variables.  cbCola and cbColb must be defined right before Cola and szColb because   
   // they are used as bulk copy indicator variables.  
   struct ColaData {  
      int cbCola;  
      SQLINTEGER Cola;  
   } ColaInst;  
  
   struct ColbData {  
      int cbColb;  
      SQLCHAR szColb[11];  
   } ColbInst;  
  
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
  
   // Allocate ODBC connection handle, set bulk copy mode, and connect.  
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
  
   // sample uses Integrated Security, create the SQL Server DSN using Windows NT authentication  
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "AdventureWorks..BCPTarget", NULL, NULL, DB_IN);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Bind the program variables for the bulk copy.  
   retcode = bcp_bind(hdbc1, (BYTE *)&ColaInst.cbCola, 4, SQL_VARLEN_DATA, NULL, (INT)NULL, SQLINT4, 1);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_bind(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Could normally use strlen to calculate the bcp_bind cbTerm parameter, but this terminator   
   // is a null byte (\0), which gives strlen a value of 0. Explicitly give cbTerm a value of 1.  
   retcode = bcp_bind(hdbc1, (BYTE *)&ColbInst.cbColb, 4, 11, (UCHAR*)terminator, 1, SQLCHARACTER, 2);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_bind(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate second ODBC connection handle so bulk copy and cursor operations do not conflict.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc2);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc2) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security, create SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc2, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate ODBC statement handle.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc2, &hstmt2);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hstmt2) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
SQLLEN lDataLengthA;  
SQLLEN lDataLengthB;  
  
   // Bind the SELECT statement to the same program variables bound to the bulk copy operation.  
   retcode = SQLBindCol(hstmt2, 1, SQL_C_SLONG, &ColaInst.Cola, 0, &lDataLengthA);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLBindCol(hstmt2) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLBindCol(hstmt2, 2, SQL_C_CHAR, &ColbInst.szColb, 11, &lDataLengthB);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLBindCol(hstmt2) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute SELECT statement to build a cursor containing data to be bulk copied to new table.  
   retcode = SQLExecDirect(hstmt2, (UCHAR*)"SELECT * FROM BCPSource", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
   // Go into a loop fetching rows from the cursor until each row is fetched. Because the   
   // bcp_bind calls and SQLBindCol calls each reference the same variables, each fetch fills   
   // the variables used by bcp_sendrow, so all you have to do to send the data to SQL Server is   
   // to call bcp_sendrow.  
   while ( (retcode = SQLFetch(hstmt2) ) != SQL_NO_DATA) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLFetch Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
  
      ColaInst.cbCola = (int)lDataLengthA;  
      ColbInst.cbColb = (int)lDataLengthB;  
  
     if ( (SendRet = bcp_sendrow(hdbc1) ) != SUCCEED ) {  
         printf("bcp_sendrow(hdbc1) Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Signal the end of the bulk copy operation.  
   cRowsDone = bcp_done(hdbc1);  
   if ( (cRowsDone == -1) ) {  
      printf("bcp_done(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied after last bcp_batch call = %d.\n", cRowsDone);  
  
   // Cleanup.  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt2);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLDisconnect(hdbc2);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc2);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
```  
  
```  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPSource')  
     DROP TABLE BCPSource  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPTarget')  
     DROP TABLE BCPTarget  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d94b9-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d94b9-139">See Also</span></span>  
 <span data-ttu-id="d94b9-140">[使用 SQL Server ODBC 驅動程式的大量複製如何 &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="d94b9-140">[Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span></span>  
 [<span data-ttu-id="d94b9-141">從程式變數中大量複製</span><span class="sxs-lookup"><span data-stu-id="d94b9-141">Bulk Copying from Program Variables</span></span>](../../native-client-odbc-bulk-copy-operations/bulk-copying-from-program-variables.md)  
  
  
