---
title: 分析 (ODBC) 的驅動程式效能資料 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- driver performance data [ODBC]
ms.assetid: b997790a-8cc6-4800-8867-74c1bef07be3
author: rothja
ms.author: jroth
ms.openlocfilehash: 3575cfd304d526bdb25eee6a2578d67c6bb67bc9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698161"
---
# <a name="profile-driver-performance-data-odbc"></a><span data-ttu-id="65102-102">分析驅動程式效能資料 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="65102-102">Profile Driver Performance Data (ODBC)</span></span>
  <span data-ttu-id="65102-103">此範例顯示 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC 驅動程式專用選項，以記錄效能統計資料。</span><span class="sxs-lookup"><span data-stu-id="65102-103">This sample shows the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ODBC driver-specific options to record performance statistics.</span></span> <span data-ttu-id="65102-104">此範例會建立一個檔案：odbcperf.log。此範例會示範如何建立效能資料記錄檔，以及直接從 SQLPERF 資料結構顯示效能資料 (SQLPERF 結構定義於 Odbcss.h 中)。</span><span class="sxs-lookup"><span data-stu-id="65102-104">The sample creates one file: odbcperf.log.This sample shows both the creation of a performance data log file and displaying performance data directly from the SQLPERF data structure (The SQLPERF structure is defined in Odbcss.h.).</span></span> <span data-ttu-id="65102-105">此範例是針對 ODBC 3.0 版或更新版本所開發。</span><span class="sxs-lookup"><span data-stu-id="65102-105">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="65102-106">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="65102-106">When possible, use Windows Authentication.</span></span> <span data-ttu-id="65102-107">如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。</span><span class="sxs-lookup"><span data-stu-id="65102-107">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="65102-108">請避免將認證儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="65102-108">Avoid storing credentials in a file.</span></span> <span data-ttu-id="65102-109">如果您必須保存認證，您應該使用[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)將它們加密。</span><span class="sxs-lookup"><span data-stu-id="65102-109">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-log-driver-performance-data-using-odbc-administrator"></a><span data-ttu-id="65102-110">使用 ODBC 管理員記錄驅動程式效能資料</span><span class="sxs-lookup"><span data-stu-id="65102-110">To log driver performance data using ODBC Administrator</span></span>  
  
1.  <span data-ttu-id="65102-111">在 [**控制台**] 中，按兩下 [系統**管理工具**]，然後按兩下 [ \*\* (ODBC) 的資料來源\*\*]。</span><span class="sxs-lookup"><span data-stu-id="65102-111">In **Control Panel**, double-click **Administrative Tools** and then double-click **Data Sources (ODBC)**.</span></span> <span data-ttu-id="65102-112">或者，您可以叫用 odbcad32.exe。</span><span class="sxs-lookup"><span data-stu-id="65102-112">Alternatively, you can invoke odbcad32.exe.</span></span>  
  
2.  <span data-ttu-id="65102-113">按一下 [**使用者 DSN**]、[**系統 DSN**] 或 [檔案**DSN** ] 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="65102-113">Click the **User DSN**, **System DSN**, or **File DSN** tab.</span></span>  
  
3.  <span data-ttu-id="65102-114">按一下記錄效能的資料來源。</span><span class="sxs-lookup"><span data-stu-id="65102-114">Click the data source for which to log performance.</span></span>  
  
4.  <span data-ttu-id="65102-115">按一下 [設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="65102-115">Click **Configure**.</span></span>  
  
5.  <span data-ttu-id="65102-116">在 Microsoft SQL Server 設定 DSN Wizard] 中，流覽至包含**記錄檔 ODBC 驅動程式統計資料的頁面至記錄**檔。</span><span class="sxs-lookup"><span data-stu-id="65102-116">In the Microsoft SQL Server Configure DSN Wizard, navigate to the page with **Log ODBC driver statistics to the log file**.</span></span>  
  
6.  <span data-ttu-id="65102-117">選取 **[記錄 ODBC 驅動程式統計資料至記錄檔]**。</span><span class="sxs-lookup"><span data-stu-id="65102-117">Select **Log ODBC driver statistics to the log file**.</span></span> <span data-ttu-id="65102-118">在方塊中，放置應該記錄其統計資料之檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="65102-118">In the box, place the name of the file where the statistics should be logged.</span></span> <span data-ttu-id="65102-119">或者，按一下 **[流覽**] 來流覽檔案系統中的統計資料記錄檔。</span><span class="sxs-lookup"><span data-stu-id="65102-119">Optionally, click **Browse** to browse the file system for the statistics log.</span></span>  
  
### <a name="to-log-driver-performance-data-programmatically"></a><span data-ttu-id="65102-120">以程式設計方式記錄驅動程式效能資料</span><span class="sxs-lookup"><span data-stu-id="65102-120">To log driver performance data programmatically</span></span>  
  
1.  <span data-ttu-id="65102-121">使用 SQL_COPT_SS_PERF_DATA_LOG 和效能資料記錄檔的完整路徑和檔案名來呼叫[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) 。</span><span class="sxs-lookup"><span data-stu-id="65102-121">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_DATA_LOG and the full path and file name of the performance data log file.</span></span> <span data-ttu-id="65102-122">例如：</span><span class="sxs-lookup"><span data-stu-id="65102-122">For example:</span></span>  
  
    ```  
    "C:\\Odbcperf.log"  
    ```  
  
2.  <span data-ttu-id="65102-123">使用 SQL_COPT_SS_PERF_DATA 和 SQL_PERF_START 呼叫[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) ，以開始記錄效能資料。</span><span class="sxs-lookup"><span data-stu-id="65102-123">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_DATA and SQL_PERF_START to start logging performance data.</span></span>  
  
3.  <span data-ttu-id="65102-124">（選擇性）使用 SQL_COPT_SS_LOG_NOW 和 Null 呼叫[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) ，將效能資料的 tab 鍵分隔記錄寫入效能資料記錄檔。</span><span class="sxs-lookup"><span data-stu-id="65102-124">Optionally, call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_LOG_NOW and NULL to write a tab-delimited record of performance data to the performance data log file.</span></span> <span data-ttu-id="65102-125">這可以在應用程式執行時完成多次。</span><span class="sxs-lookup"><span data-stu-id="65102-125">This can be done multiple times as the application runs.</span></span>  
  
4.  <span data-ttu-id="65102-126">使用 SQL_COPT_SS_PERF_DATA 和 SQL_PERF_STOP 呼叫[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) ，以停止記錄效能資料。</span><span class="sxs-lookup"><span data-stu-id="65102-126">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_DATA and SQL_PERF_STOP to stop logging performance data.</span></span>  
  
### <a name="to-pull-driver-performance-data-into-an-application"></a><span data-ttu-id="65102-127">將驅動程式效能資料提取到應用程式中</span><span class="sxs-lookup"><span data-stu-id="65102-127">To pull driver performance data into an application</span></span>  
  
1.  <span data-ttu-id="65102-128">使用 SQL_COPT_SS_PERF_DATA 和 SQL_PERF_START 呼叫[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) ，以開始分析效能資料。</span><span class="sxs-lookup"><span data-stu-id="65102-128">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_DATA and SQL_PERF_START to start profiling performance data.</span></span>  
  
2.  <span data-ttu-id="65102-129">使用 SQL_COPT_SS_PERF_DATA 和 SQLPERF 結構之指標的位址來呼叫[SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) 。</span><span class="sxs-lookup"><span data-stu-id="65102-129">Call [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) with SQL_COPT_SS_PERF_DATA and the address of a pointer to a SQLPERF structure.</span></span> <span data-ttu-id="65102-130">第一個這類呼叫會將指標設定為有效 SQLPERF 結構的位址，其中包含目前的效能資料。</span><span class="sxs-lookup"><span data-stu-id="65102-130">The first such call sets the pointer to the address of a valid SQLPERF structure that contains current performance data.</span></span> <span data-ttu-id="65102-131">驅動程式不會在效能結構中持續重新整理資料。</span><span class="sxs-lookup"><span data-stu-id="65102-131">The driver does not continually refresh the data in the performance structure.</span></span> <span data-ttu-id="65102-132">應用程式必須在需要使用更多目前的效能資料重新整理結構時，重複呼叫[SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) 。</span><span class="sxs-lookup"><span data-stu-id="65102-132">The application must repeat the call to [SQLGetConnectAttr](../native-client-odbc-api/sqlgetconnectattr.md) any time it needs to refresh the structure with more current performance data.</span></span>  
  
3.  <span data-ttu-id="65102-133">使用 SQL_COPT_SS_PERF_DATA 和 SQL_PERF_STOP 呼叫[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) ，以停止記錄效能資料。</span><span class="sxs-lookup"><span data-stu-id="65102-133">Call [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_PERF_DATA and SQL_PERF_STOP to stop logging performance data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65102-134">範例</span><span class="sxs-lookup"><span data-stu-id="65102-134">Example</span></span>  
 <span data-ttu-id="65102-135">您需要名為 AdventureWorks 的 ODBC 資料來源，其預設資料庫為 AdventureWorks 範例資料庫 </span><span class="sxs-lookup"><span data-stu-id="65102-135">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="65102-136"> (您可以從 [ [Microsoft SQL Server 範例] 和 [社區專案](https://go.microsoft.com/fwlink/?LinkID=85384)] 首頁下載 AdventureWorks 範例資料庫。 ) 此資料來源必須以作業系統所提供的 ODBC 驅動程式為基礎， (驅動程式名稱為 "SQL Server" ) 。</span><span class="sxs-lookup"><span data-stu-id="65102-136">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="65102-137">如果您要建立並執行此範例，當做 64 位元作業系統上的 32 位元應用程式，您必須利用 %windir%\SysWOW64\odbcad32.exe，以 ODBC 管理員身分建立 ODBC 資料來源。</span><span class="sxs-lookup"><span data-stu-id="65102-137">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="65102-138">這個範例會連接到電腦的預設 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="65102-138">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="65102-139">若要連接到具名執行個體，請變更 ODBC 資料來源的定義，以便使用下列格式指定執行個體：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="65102-139">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="65102-140">根據預設，[!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] 會安裝至具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="65102-140">By default, [!INCLUDE[ssExpress](../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="65102-141">使用 odbc32.lib 編譯。</span><span class="sxs-lookup"><span data-stu-id="65102-141">Compile with odbc32.lib.</span></span>  
  
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
  
   // Pointer to the ODBC driver performance structure.  
   SQLPERF *PerfPtr;  
   SQLINTEGER cbPerfPtr;  
  
   // Allocate the ODBC environment and save handle.  
   retcode = SQLAllocHandle (SQL_HANDLE_ENV, NULL, &henv);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(Env) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Notify ODBC that this is an ODBC 3.0 app.  
   retcode = SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER) SQL_OV_ODBC3, SQL_IS_INTEGER);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);      
   }  
  
   // Allocate ODBC connection handle and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // This sample use Integrated Security. Please create the SQL Server   
   // DSN by using the Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set options to log performance statistics.  Specify file to use for the log.  
   retcode = SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA_LOG, &"odbcperf.log", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Start the performance statistics log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA, (SQLPOINTER)SQL_PERF_START, SQL_IS_UINTEGER);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Allocate statement handle, then execute command.  
   retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLAllocHandle() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Purchasing.Vendor", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"SELECT * FROM Sales.Store", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Generate a long-running query.  
   retcode = SQLExecDirect(hstmt1, (UCHAR*)"waitfor delay '00:00:04' ", SQL_NTS);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLExecDirect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Clear any result sets generated.  
   while ( ( retcode = SQLMoreResults(hstmt1) ) != SQL_NO_DATA ) {  
      if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
         printf("SQLMoreResults() Failed\n\n");  
         Cleanup();  
         return(9);  
      }  
   }  
  
   // Write current statistics to the performance log.  
   retcode =   
      SQLSetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA_LOG_NOW, (SQLPOINTER)NULL, SQL_IS_UINTEGER);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLSetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Get pointer to current SQLPerf structure.  
   // Print a couple of statistics.  
   retcode =   
      SQLGetConnectAttr( hdbc1, SQL_COPT_SS_PERF_DATA, (SQLPOINTER)&PerfPtr, SQL_IS_POINTER, &cbPerfPtr);  
   if( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLGetConnectAttr() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("SQLSelects = %d, SQLSelectRows = %d\n", PerfPtr->SQLSelects, PerfPtr->SQLSelectRows);  
  
   // Cleanup  
   SQLFreeHandle(SQL_HANDLE_STMT, hstmt1);  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="65102-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="65102-142">See Also</span></span>  
 <span data-ttu-id="65102-143">[分析 ODBC 驅動程式效能的使用說明主題 &#40;ODBC&#41;](profiling-odbc-driver-performance-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="65102-143">[Profiling ODBC Driver Performance How-to Topics &#40;ODBC&#41;](profiling-odbc-driver-performance-odbc.md) </span></span>  
 [<span data-ttu-id="65102-144">分析 ODBC 驅動程式效能</span><span class="sxs-lookup"><span data-stu-id="65102-144">Profiling ODBC Driver Performance</span></span>](../native-client/odbc/profiling-odbc-driver-performance.md)  
  
  
