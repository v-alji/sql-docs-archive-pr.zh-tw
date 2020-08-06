---
title: " (ODBC) 記錄長時間執行的查詢 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- queries [ODBC]
ms.assetid: b9c1ddce-1dd9-409d-a414-8b544d616273
author: rothja
ms.author: jroth
ms.openlocfilehash: f73dbf6fe8fc4b3dfbbbc0012d14a58614b218dd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708278"
---
# <a name="log-long-running-queries-odbc"></a><span data-ttu-id="3c6ad-102">記錄長時間執行的查詢 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="3c6ad-102">Log Long-Running Queries (ODBC)</span></span>
  <span data-ttu-id="3c6ad-103">此範例會顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC 驅動程式專用選項，用以記錄長時間執行的查詢。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-103">This sample shows the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver-specific options to log long-running queries.</span></span> <span data-ttu-id="3c6ad-104">執行時，此範例會建立 Odbcqry.log，其中包含執行超過應用程式設定之間隔的查詢清單。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-104">When run, this sample creates Odbcqry.log, which contains a list of queries whose execution exceeds an interval set by the application.</span></span> <span data-ttu-id="3c6ad-105">IA64 不支援此範例。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-105">This sample is not supported on IA64.</span></span> <span data-ttu-id="3c6ad-106">此範例是針對 ODBC 3.0 版或更新版本所開發。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-106">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="3c6ad-107">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-107">When possible, use Windows Authentication.</span></span> <span data-ttu-id="3c6ad-108">如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-108">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="3c6ad-109">請避免將認證儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-109">Avoid storing credentials in a file.</span></span> <span data-ttu-id="3c6ad-110">如果您必須保存認證，您應該使用[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)將它們加密。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-110">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-log-long-running-queries-using-odbc-administrator"></a><span data-ttu-id="3c6ad-111">使用 ODBC 管理員記錄長時間執行的查詢</span><span class="sxs-lookup"><span data-stu-id="3c6ad-111">To log long-running queries using ODBC Administrator</span></span>  
  
1.  <span data-ttu-id="3c6ad-112">在 [**控制台**] 中，按兩下 [系統**管理工具**]，然後按兩下 [ \*\* (ODBC) 的資料來源\*\*]。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-112">In **Control Panel**, double-click **Administrative Tools** and then double-click **Data Sources (ODBC)**.</span></span> <span data-ttu-id="3c6ad-113">(或者，您也可以從命令提示字元執行 odbcad32.exe)。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-113">(Alternatively, you can run odbcad32.exe from the command prompt.)</span></span>  
  
2.  <span data-ttu-id="3c6ad-114">按一下 [**使用者 DSN**]、[**系統 DSN**] 或 [檔案**DSN** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-114">Click the **User DSN**, **System DSN**, or **File DSN** tab.</span></span>  
  
3.  <span data-ttu-id="3c6ad-115">按一下記錄長時間執行之查詢的資料來源。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-115">Click the data source for which to log long-running queries.</span></span>  
  
4.  <span data-ttu-id="3c6ad-116">按一下 [設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-116">Click **Configure**.</span></span>  
  
5.  <span data-ttu-id="3c6ad-117">在 Microsoft SQL Server 設定 DSN Wizard] 中，流覽至 [**將長時間執行的查詢儲存到記錄**檔] 頁面。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-117">In the Microsoft SQL Server Configure DSN Wizard, navigate to the page with **Save long-running queries to the log file**.</span></span>  
  
6.  <span data-ttu-id="3c6ad-118">選取 **[將長時間執行的查詢儲存到記錄**檔]。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-118">Select **Save long-running queries to the log file**.</span></span> <span data-ttu-id="3c6ad-119">在方塊中，放置應該記錄其長時間執行查詢之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-119">In the box, place the name of the file where the long-running queries should be logged.</span></span> <span data-ttu-id="3c6ad-120">或者，按一下 [**流覽]** 來流覽檔案系統中的查詢記錄檔。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-120">Optionally, click **Browse** to browse the file system for the query log.</span></span>  
  
7.  <span data-ttu-id="3c6ad-121">設定查詢逾時間隔（以毫秒為單位），在 [\*\*長時間查詢時間] (毫秒) \*\* ] 方塊中。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-121">Set a query time-out interval, in milliseconds, in the **Long query time (milliseconds)** box.</span></span>  
  
### <a name="to-log-long-running-queries-data-programmatically"></a><span data-ttu-id="3c6ad-122">以程式設計方式記錄長時間執行的查詢資料</span><span class="sxs-lookup"><span data-stu-id="3c6ad-122">To log long-running queries data programmatically</span></span>  
  
1.  <span data-ttu-id="3c6ad-123">使用 SQL_COPT_SS_PERF_QUERY_LOG 以及長時間執行之查詢記錄檔的完整路徑和檔案名來呼叫[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) 。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-123">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_QUERY_LOG and the full path and file name of the long-running query log file.</span></span> <span data-ttu-id="3c6ad-124">例如：</span><span class="sxs-lookup"><span data-stu-id="3c6ad-124">For example:</span></span>  
  
    ```  
    C:\\Odbcqry.log  
    ```  
  
2.  <span data-ttu-id="3c6ad-125">使用 SQL_COPT_SS_PERF_QUERY_INTERVAL 呼叫[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) ，並將設定為逾時間隔（以毫秒為單位）。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-125">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_QUERY_INTERVAL and set to the time-out interval, in milliseconds.</span></span>  
  
3.  <span data-ttu-id="3c6ad-126">使用 SQL_COPT_SS_PERF_QUERY 和 SQL_PERF_START 呼叫[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) ，以開始記錄長時間執行的查詢。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-126">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_QUERY and SQL_PERF_START to start logging long-running queries.</span></span>  
  
4.  <span data-ttu-id="3c6ad-127">使用 SQL_COPT_SS_PERF_QUERY 和 SQL_PERF_STOP 呼叫[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) ，以停止記錄長時間執行的查詢。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-127">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_QUERY and SQL_PERF_STOP to stop logging long-running queries.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c6ad-128">範例</span><span class="sxs-lookup"><span data-stu-id="3c6ad-128">Example</span></span>  
 <span data-ttu-id="3c6ad-129">您需要名為 AdventureWorks 的 ODBC 資料來源，其預設資料庫為 AdventureWorks 範例資料庫 </span><span class="sxs-lookup"><span data-stu-id="3c6ad-129">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="3c6ad-130"> (您可以從 [ [Microsoft SQL Server 範例] 和 [社區專案](https://go.microsoft.com/fwlink/?LinkID=85384)] 首頁下載 AdventureWorks 範例資料庫。 ) 此資料來源必須以作業系統所提供的 ODBC 驅動程式為基礎， (驅動程式名稱為 "SQL Server" ) 。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-130">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="3c6ad-131">如果您要建立並執行此範例，當做 64 位元作業系統上的 32 位元應用程式，您必須利用 %windir%\SysWOW64\odbcad32.exe，以 ODBC 管理員身分建立 ODBC 資料來源。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-131">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="3c6ad-132">這個範例會連接到電腦的預設 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-132">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="3c6ad-133">若要連接到具名執行個體，請變更 ODBC 資料來源的定義，以便使用下列格式指定執行個體：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-133">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="3c6ad-134">根據預設，[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 會安裝至具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-134">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="3c6ad-135">使用 odbc32.lib 編譯。</span><span class="sxs-lookup"><span data-stu-id="3c6ad-135">Compile with odbc32.lib.</span></span>  
  
```  
// compile with: odbc32.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
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
  
   // sample uses Integrated Security, create SQL Server DSN using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set options to log long-running queries, including the file to use for the log.  
   retcode = SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY_LOG, &"odbcqry.log", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set the long-running query interval (in milliseconds).  Note that for version 2.50 and 2.65  
   // drivers, this value is specified in seconds, not milliseconds.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY_INTERVAL, (SQLPOINTER)3000, SQL_IS_UINTEGER);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Start the long-running query log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_QUERY, (SQLPOINTER)SQL_PERF_START, SQL_IS_UINTEGER);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle then execute commands.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle(hstmt1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Purchasing.Vendor", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
           return(9);  
      }  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Sales.Store", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Generate a long-running query.  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"waitfor delay '00:00:04' ", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Cleanup  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c6ad-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c6ad-136">See Also</span></span>  
 [<span data-ttu-id="3c6ad-137">分析 ODBC 驅動程式效能的使用說明主題 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="3c6ad-137">Profiling ODBC Driver Performance How-to Topics &#40;ODBC&#41;</span></span>](profiling-odbc-driver-performance-odbc.md)  
  
  
