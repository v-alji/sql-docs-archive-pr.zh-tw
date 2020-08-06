---
title: 不使用格式檔案進行大量複製 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- bulk copy [ODBC]
- bulk copy [ODBC], data files
- bulk copy [ODBC], about bulk copy
ms.assetid: 4ee969a7-44ba-40d0-b9ab-8306f1a2b19d
author: rothja
ms.author: jroth
ms.openlocfilehash: a65f013d92f5a5d39a580cfb3a9bd77bc6f84e9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709349"
---
# <a name="bulk-copy-without-a-format-file-odbc"></a><span data-ttu-id="a20eb-102">不使用格式檔案進行大量複製 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="a20eb-102">Bulk Copy Without a Format File (ODBC)</span></span>
  <span data-ttu-id="a20eb-103">此範例會示範如何在沒有格式檔案的情況下，使用大量複製函數來建立原生模式資料檔案。</span><span class="sxs-lookup"><span data-stu-id="a20eb-103">This sample shows how to use bulk copy functions to create a native mode data file, without a format file.</span></span> <span data-ttu-id="a20eb-104">此範例是針對 ODBC 3.0 版或更新版本所開發。</span><span class="sxs-lookup"><span data-stu-id="a20eb-104">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="a20eb-105">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="a20eb-105">When possible, use Windows Authentication.</span></span> <span data-ttu-id="a20eb-106">如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。</span><span class="sxs-lookup"><span data-stu-id="a20eb-106">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="a20eb-107">請避免將認證儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="a20eb-107">Avoid storing credentials in a file.</span></span> <span data-ttu-id="a20eb-108">如果您必須保存認證，您應該使用[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)將它們加密。</span><span class="sxs-lookup"><span data-stu-id="a20eb-108">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-bulk-copy-without-a-format-file"></a><span data-ttu-id="a20eb-109">不使用格式檔案進行大量複製</span><span class="sxs-lookup"><span data-stu-id="a20eb-109">To bulk copy without a format file</span></span>  
  
1.  <span data-ttu-id="a20eb-110">配置環境控制代碼和連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="a20eb-110">Allocate an environment handle and a connection handle.</span></span>  
  
2.  <span data-ttu-id="a20eb-111">將 SQL_COPT_SS_BCP 和 SQL_BCP_ON 設定為啟用大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="a20eb-111">Set SQL_COPT_SS_BCP and SQL_BCP_ON to enable bulk copy operations.</span></span>  
  
3.  <span data-ttu-id="a20eb-112">連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="a20eb-112">Connect to SQL Server.</span></span>  
  
4.  <span data-ttu-id="a20eb-113">呼叫[bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)以設定下列資訊：</span><span class="sxs-lookup"><span data-stu-id="a20eb-113">Call [bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to set the following information:</span></span>  
  
    -   <span data-ttu-id="a20eb-114">要進行大量複製之來源或目標資料表或檢視表的名稱。</span><span class="sxs-lookup"><span data-stu-id="a20eb-114">The name of the table or view to bulk copy from or to.</span></span>  
  
    -   <span data-ttu-id="a20eb-115">包含要複製到資料庫之資料或從資料庫複製時接收資料的資料檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="a20eb-115">The name of the data file that contains the data to copy into the database or that receives data when copying from the database.</span></span>  
  
    -   <span data-ttu-id="a20eb-116">要接收任何大量複製錯誤訊息的資料檔案名稱 (如果您不需要訊息檔案，請指定 NULL)。</span><span class="sxs-lookup"><span data-stu-id="a20eb-116">The name of a data file to receive any bulk copy error messages (specify NULL if you do not want a message file).</span></span>  
  
    -   <span data-ttu-id="a20eb-117">複製的方向：DB_IN (從檔案到檢視或資料表) 或 DB_OUT (從資料表或檢視到檔案)。</span><span class="sxs-lookup"><span data-stu-id="a20eb-117">The direction of the copy: DB_IN from the file to the view or table, or DB_OUT to the file from the table or view.</span></span>  
  
5.  <span data-ttu-id="a20eb-118">呼叫[bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)以執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="a20eb-118">Call [bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) to execute the bulk copy operation.</span></span>  
  
 <span data-ttu-id="a20eb-119">使用這些步驟設定 DB_OUT 時，檔案會以原生格式建立。</span><span class="sxs-lookup"><span data-stu-id="a20eb-119">When DB_OUT is set with these steps, the file is created in native format.</span></span> <span data-ttu-id="a20eb-120">接著可以藉由遵照這些相同的步驟，將檔案大量複製到伺服器 (除了設定的是 DB_OUT，而不是 DB_IN)。</span><span class="sxs-lookup"><span data-stu-id="a20eb-120">The file can then be bulk copied into a server by following these same steps, except that DB_OUT is set instead of DB_IN.</span></span> <span data-ttu-id="a20eb-121">只有當來源資料表和目標資料表兩者都具有相同的結構時，才適用這種方法。</span><span class="sxs-lookup"><span data-stu-id="a20eb-121">This works only if both the source and target tables have exactly the same structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a20eb-122">範例</span><span class="sxs-lookup"><span data-stu-id="a20eb-122">Example</span></span>  
 <span data-ttu-id="a20eb-123">IA64 不支援此範例。</span><span class="sxs-lookup"><span data-stu-id="a20eb-123">This sample is not supported on IA64.</span></span>  
  
 <span data-ttu-id="a20eb-124">您需要名為 AdventureWorks 的 ODBC 資料來源，其預設資料庫為 AdventureWorks 範例資料庫 </span><span class="sxs-lookup"><span data-stu-id="a20eb-124">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="a20eb-125"> (您可以從 [ [Microsoft SQL Server 範例] 和 [社區專案](https://go.microsoft.com/fwlink/?LinkID=85384)] 首頁下載 AdventureWorks 範例資料庫。 ) 此資料來源必須以作業系統所提供的 ODBC 驅動程式為基礎， (驅動程式名稱為 "SQL Server" ) 。</span><span class="sxs-lookup"><span data-stu-id="a20eb-125">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="a20eb-126">如果您要建立並執行此範例，當做 64 位元作業系統上的 32 位元應用程式，您必須利用 %windir%\SysWOW64\odbcad32.exe，以 ODBC 管理員身分建立 ODBC 資料來源。</span><span class="sxs-lookup"><span data-stu-id="a20eb-126">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="a20eb-127">這個範例會連接到電腦的預設 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="a20eb-127">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="a20eb-128">若要連接到具名執行個體，請變更 ODBC 資料來源的定義，以便使用下列格式指定執行個體：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="a20eb-128">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="a20eb-129">根據預設，[!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] 會安裝至具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="a20eb-129">By default, [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="a20eb-130">使用 odbc32.lib 和 odbcbcp.lib 編譯。</span><span class="sxs-lookup"><span data-stu-id="a20eb-130">Compile with odbc32.lib and odbcbcp.lib.</span></span>  
  
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
  
   // Sample uses Integrated Security, create the SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "Purchasing.Vendor", "BCPODBC.bcp", "BCPERROR.out", DB_OUT);  
   // Test is for the bulk copy return of SUCCEED, not the ODBC return of SQL_SUCCESS.  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
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
  
## <a name="see-also"></a><span data-ttu-id="a20eb-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a20eb-131">See Also</span></span>  
 [<span data-ttu-id="a20eb-132">使用 SQL Server ODBC 驅動程式的大量複製如何 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="a20eb-132">Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;</span></span>](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md)  
  
  
