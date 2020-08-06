---
title: 建立 (ODBC) 的大量複製格式檔案 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- bulk copy [ODBC], data files
ms.assetid: 0572fef3-daf5-409e-b557-c2a632f9a06d
author: rothja
ms.author: jroth
ms.openlocfilehash: 9d35342b2f6b25a129df968383d204931d64bfa5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585372"
---
# <a name="create-a-bulk-copy-format-file-odbc"></a><span data-ttu-id="de0a9-102">建立大量複製格式檔案 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="de0a9-102">Create a Bulk Copy Format File (ODBC)</span></span>
  <span data-ttu-id="de0a9-103">此範例將示範如何使用大量複製函數來建立資料檔案和格式檔案。</span><span class="sxs-lookup"><span data-stu-id="de0a9-103">This sample shows how to use bulk copy functions to create both a data file and a format file.</span></span> <span data-ttu-id="de0a9-104">此範例是針對 ODBC 3.0 版或更新版本所開發。</span><span class="sxs-lookup"><span data-stu-id="de0a9-104">This sample was developed for ODBC version 3.0 or later.</span></span>  
  
> [!IMPORTANT]  
>  <span data-ttu-id="de0a9-105">盡可能使用 Windows 驗證。</span><span class="sxs-lookup"><span data-stu-id="de0a9-105">When possible, use Windows Authentication.</span></span> <span data-ttu-id="de0a9-106">如果無法使用 Windows 驗證，請提示使用者在執行階段輸入認證。</span><span class="sxs-lookup"><span data-stu-id="de0a9-106">If Windows Authentication is not available, prompt users to enter their credentials at run time.</span></span> <span data-ttu-id="de0a9-107">請避免將認證儲存在檔案中。</span><span class="sxs-lookup"><span data-stu-id="de0a9-107">Avoid storing credentials in a file.</span></span> <span data-ttu-id="de0a9-108">如果您必須保存認證，您應該使用[Win32 加密 API](https://go.microsoft.com/fwlink/?LinkId=64532)將它們加密。</span><span class="sxs-lookup"><span data-stu-id="de0a9-108">If you must persist credentials, you should encrypt them with the [Win32 crypto API](https://go.microsoft.com/fwlink/?LinkId=64532).</span></span>  
  
### <a name="to-create-a-bulk-copy-format-file"></a><span data-ttu-id="de0a9-109">建立大量複製格式檔案</span><span class="sxs-lookup"><span data-stu-id="de0a9-109">To create a bulk copy format file</span></span>  
  
1.  <span data-ttu-id="de0a9-110">配置環境控制代碼和連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="de0a9-110">Allocate an environment handle and a connection handle.</span></span>  
  
2.  <span data-ttu-id="de0a9-111">將 SQL_COPT_SS_BCP 和 SQL_BCP_ON 設定為啟用大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="de0a9-111">Set SQL_COPT_SS_BCP and SQL_BCP_ON to enable bulk copy operations.</span></span>  
  
3.  <span data-ttu-id="de0a9-112">連接到 SQL Server。</span><span class="sxs-lookup"><span data-stu-id="de0a9-112">Connect to SQL Server.</span></span>  
  
4.  <span data-ttu-id="de0a9-113">呼叫[bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)以設定下列資訊：</span><span class="sxs-lookup"><span data-stu-id="de0a9-113">Call [bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to set the following information:</span></span>  
  
    -   <span data-ttu-id="de0a9-114">要進行大量複製之來源或目標資料表或檢視表的名稱。</span><span class="sxs-lookup"><span data-stu-id="de0a9-114">The name of the table or view to bulk copy from or to.</span></span>  
  
    -   <span data-ttu-id="de0a9-115">包含要複製到資料庫之資料或從資料庫複製時接收資料的資料檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="de0a9-115">The name of the data file that contains the data to copy into the database or that receives data when copying from the database.</span></span>  
  
    -   <span data-ttu-id="de0a9-116">要接收任何大量複製錯誤訊息的資料檔案名稱 (如果您不需要訊息檔案，請指定 NULL)。</span><span class="sxs-lookup"><span data-stu-id="de0a9-116">The name of a data file to receive any bulk copy error messages (specify NULL if you do not want a message file).</span></span>  
  
    -   <span data-ttu-id="de0a9-117">複製的方向：DB_OUT 到資料表或檢視表的檔案。</span><span class="sxs-lookup"><span data-stu-id="de0a9-117">The direction of the copy: DB_OUT to the file from the table or view.</span></span>  
  
5.  <span data-ttu-id="de0a9-118">呼叫[bcp_columns](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)來設定資料行數目。</span><span class="sxs-lookup"><span data-stu-id="de0a9-118">Call [bcp_columns](../../native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md) to set the number of columns.</span></span>  
  
6.  <span data-ttu-id="de0a9-119">針對每個資料行呼叫[bcp_colfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) ，以定義其在資料檔案中的特性。</span><span class="sxs-lookup"><span data-stu-id="de0a9-119">Call [bcp_colfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md) for each column to define its characteristics in the data file.</span></span>  
  
7.  <span data-ttu-id="de0a9-120">呼叫[bcp_writefmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md)來建立格式檔案，以描述大量複製作業所要建立的資料檔案。</span><span class="sxs-lookup"><span data-stu-id="de0a9-120">Call [bcp_writefmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md) to create a format file describing the data file to be created by the bulk copy operation.</span></span>  
  
8.  <span data-ttu-id="de0a9-121">呼叫[bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)以執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="de0a9-121">Call [bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) to execute the bulk copy operation.</span></span>  
  
 <span data-ttu-id="de0a9-122">以這種方式執行的大量複製作業會建立包含大量複製資料的資料檔案，以及描述資料檔案配置的格式檔案。</span><span class="sxs-lookup"><span data-stu-id="de0a9-122">A bulk copy operation run in this way creates both a data file containing the bulk copied data and a format file describing the layout of the data file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de0a9-123">範例</span><span class="sxs-lookup"><span data-stu-id="de0a9-123">Example</span></span>  
 <span data-ttu-id="de0a9-124">您需要名為 AdventureWorks 的 ODBC 資料來源，其預設資料庫為 AdventureWorks 範例資料庫 </span><span class="sxs-lookup"><span data-stu-id="de0a9-124">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="de0a9-125"> (您可以從 [ [Microsoft SQL Server 範例] 和 [社區專案](https://go.microsoft.com/fwlink/?LinkID=85384)] 首頁下載 AdventureWorks 範例資料庫。 ) 此資料來源必須以作業系統所提供的 ODBC 驅動程式為基礎， (驅動程式名稱為 "SQL Server" ) 。</span><span class="sxs-lookup"><span data-stu-id="de0a9-125">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="de0a9-126">如果您要建立並執行此範例，當做 64 位元作業系統上的 32 位元應用程式，您必須利用 %windir%\SysWOW64\odbcad32.exe，以 ODBC 管理員身分建立 ODBC 資料來源。</span><span class="sxs-lookup"><span data-stu-id="de0a9-126">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="de0a9-127">這個範例會連接到電腦的預設 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="de0a9-127">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="de0a9-128">若要連接到具名執行個體，請變更 ODBC 資料來源的定義，以便使用下列格式指定執行個體：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="de0a9-128">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="de0a9-129">根據預設，[!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] 會安裝至具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="de0a9-129">By default, [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="de0a9-130">執行第一個 ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) 程式碼清單，以便建立此範例將使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="de0a9-130">Execute the first ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to create the table that the sample will use.</span></span>  
  
 <span data-ttu-id="de0a9-131">使用 odbc32.lib 和 odbcbcp.lib 編譯第二個 (C++) 程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="de0a9-131">Compile the second (C++) code listing with odbc32.lib and odbcbcp.lib.</span></span>  
  
 <span data-ttu-id="de0a9-132">執行第三個 ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) 程式碼清單，以便刪除此範例所使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="de0a9-132">Execute the third ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to delete the table that the sample used.</span></span>  
  
```  
use AdventureWorks  
  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPDate')  
     DROP TABLE BCPDate  
GO  
  
CREATE TABLE BCPDate (cola int, colb datetime)  
insert BCPDate(cola) values(1)   
insert BCPDate(cola) values(2)   
insert BCPDate(cola) values(3)   
insert BCPDate(cola) values(4)  
```  
  
```  
// compile with: odbc32.lib odbcbcp.lib  
#include <stdio.h>  
#include <string.h>  
#include <windows.h>  
#include <sql.h>  
#include <sqlext.h>  
#include <odbcss.h>  
  
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
  
   // BCP variables.  
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
  
   // Allocate ODBC connection handle, set bulk copy mode, and connect.  
   retcode = SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc1);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLAllocHandle(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   retcode = SQLSetConnectAttr(hdbc1, SQL_COPT_SS_BCP, (void *)SQL_BCP_ON, SQL_IS_INTEGER);  
   if ( (retcode != SQL_SUCCESS_WITH_INFO) && (retcode != SQL_SUCCESS)) {  
      printf("SQLSetEnvAttr(ODBC version) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Sample uses Integrated Security, create SQL Server DSN using Windows NT authentication.   
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"",SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "BCPDate", "BCPODBC.bcp", NULL, DB_OUT);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Set the number of output columns.  
   retcode = bcp_columns(hdbc1, 2);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Describe the format of column 1 in the data file.  
   retcode = bcp_colfmt(hdbc1, 1, SQLCHARACTER, -1, 5, NULL, 0, 1);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Describe the format of column 2 in the data file.  
   retcode = bcp_colfmt(hdbc1, 2, SQLCHARACTER, -1, 20, NULL, 0, 2);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Create the format file.  
   retcode = bcp_writefmt(hdbc1, "c:\\BCPFMT.fmt");  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Execute the bulk copy.  
   retcode = bcp_exec(hdbc1, &cRows);  
   if (retcode != SUCCEED) {  
      printf("bcp_init() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   printf("Number of rows bulk copied out = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
   return(0);  
}  
```  
  
```  
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPDate')  
     DROP TABLE BCPDate  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="de0a9-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="de0a9-133">See Also</span></span>  
 <span data-ttu-id="de0a9-134">[使用 SQL Server ODBC 驅動程式的大量複製如何 &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="de0a9-134">[Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span></span>  
 [<span data-ttu-id="de0a9-135">使用資料檔案與格式檔案</span><span class="sxs-lookup"><span data-stu-id="de0a9-135">Using Data Files and Format Files</span></span>](../../native-client-odbc-bulk-copy-operations/using-data-files-and-format-files.md)  
  
  
