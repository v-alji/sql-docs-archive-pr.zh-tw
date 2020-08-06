---
title: 使用格式檔案進行大量複製 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 10/18/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy using format file [ODBC]
- ODBC, bulk copy operations
ms.assetid: 970fd3af-f918-4fc3-a5b1-92596515d4de
author: rothja
ms.author: jroth
ms.openlocfilehash: 19959d5f1da7243275c60560963d577446f809b8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709358"
---
# <a name="bulk-copy-by-using-a-format-file-odbc"></a><span data-ttu-id="d1493-102">使用格式檔案進行大量複製 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="d1493-102">Bulk Copy by Using a Format File (ODBC)</span></span>
  <span data-ttu-id="d1493-103">此範例顯示如何利用格式檔案使用 ODBC bcp_init 函數。</span><span class="sxs-lookup"><span data-stu-id="d1493-103">This sample shows how to use the ODBC bcp_init function with a format file.</span></span>  
  
### <a name="to-bulk-copy-by-using-a-format-file"></a><span data-ttu-id="d1493-104">若要使用格式檔案進行大量複製</span><span class="sxs-lookup"><span data-stu-id="d1493-104">To bulk copy by using a format file</span></span>  
  
1.  <span data-ttu-id="d1493-105">配置環境控制代碼和連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="d1493-105">Allocate an environment handle and a connection handle.</span></span>  
  
2.  <span data-ttu-id="d1493-106">將 SQL_COPT_SS_BCP 和 SQL_BCP_ON 設定為啟用大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="d1493-106">Set SQL_COPT_SS_BCP and SQL_BCP_ON to enable bulk copy operations.</span></span>  
  
3.  <span data-ttu-id="d1493-107">連接到 Microsoft SQL Server。</span><span class="sxs-lookup"><span data-stu-id="d1493-107">Connect to Microsoft SQL Server.</span></span>  
  
4.  <span data-ttu-id="d1493-108">呼叫[bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)以設定下列資訊：</span><span class="sxs-lookup"><span data-stu-id="d1493-108">Call [bcp_init](../../native-client-odbc-extensions-bulk-copy-functions/bcp-init.md) to set the following information:</span></span>  
  
    -   <span data-ttu-id="d1493-109">要進行大量複製之來源或目標資料表或檢視表的名稱。</span><span class="sxs-lookup"><span data-stu-id="d1493-109">The name of the table or view to bulk copy from or to.</span></span>  
  
    -   <span data-ttu-id="d1493-110">包含要複製到資料庫之資料或從資料庫複製時接收資料的資料檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="d1493-110">The name of the data file that contains the data to copy into the database or that receives data when copying from the database.</span></span>  
  
    -   <span data-ttu-id="d1493-111">要接收任何大量複製錯誤訊息的資料檔案名稱 (如果您不需要訊息檔案，請指定 NULL)。</span><span class="sxs-lookup"><span data-stu-id="d1493-111">The name of a data file to receive any bulk copy error messages (specify NULL if you do not want a message file).</span></span>  
  
    -   <span data-ttu-id="d1493-112">複製的方向：DB_IN 從檔案到資料表或檢視表。</span><span class="sxs-lookup"><span data-stu-id="d1493-112">The direction of the copy: DB_IN from the file to the table or view.</span></span>  
  
5.  <span data-ttu-id="d1493-113">呼叫[bcp_readfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)以讀取描述大量複製作業所要使用之資料檔案的格式檔案。</span><span class="sxs-lookup"><span data-stu-id="d1493-113">Call [bcp_readfmt](../../native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md) to read the format file describing the data file to be used by the bulk copy operation.</span></span>  
  
6.  <span data-ttu-id="d1493-114">呼叫[bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)以執行大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="d1493-114">Call [bcp_exec](../../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md) to execute the bulk copy operation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d1493-115">範例</span><span class="sxs-lookup"><span data-stu-id="d1493-115">Example</span></span>  
 <span data-ttu-id="d1493-116">IA64 不支援此範例。</span><span class="sxs-lookup"><span data-stu-id="d1493-116">This sample is not supported on IA64.</span></span>  
  
 <span data-ttu-id="d1493-117">您需要名為 AdventureWorks 的 ODBC 資料來源，其預設資料庫為 AdventureWorks 範例資料庫 </span><span class="sxs-lookup"><span data-stu-id="d1493-117">You will need an ODBC data source called AdventureWorks, whose default database is the AdventureWorks sample database.</span></span> <span data-ttu-id="d1493-118"> (您可以從 [ [Microsoft SQL Server 範例] 和 [社區專案](https://go.microsoft.com/fwlink/?LinkID=85384)] 首頁下載 AdventureWorks 範例資料庫。 ) 此資料來源必須以作業系統所提供的 ODBC 驅動程式為基礎， (驅動程式名稱為 "SQL Server" ) 。</span><span class="sxs-lookup"><span data-stu-id="d1493-118">(You can download the AdventureWorks sample database from the [Microsoft SQL Server Samples and Community Projects](https://go.microsoft.com/fwlink/?LinkID=85384) home page.) This data source must be based on the ODBC driver that is supplied by the operating system (the driver name is "SQL Server").</span></span> <span data-ttu-id="d1493-119">如果您要建立並執行此範例，當做 64 位元作業系統上的 32 位元應用程式，您必須利用 %windir%\SysWOW64\odbcad32.exe，以 ODBC 管理員身分建立 ODBC 資料來源。</span><span class="sxs-lookup"><span data-stu-id="d1493-119">If you will build and run this sample as a 32-bit application on a 64-bit operating system, you must create the ODBC data source with the ODBC Administrator in %windir%\SysWOW64\odbcad32.exe.</span></span>  
  
 <span data-ttu-id="d1493-120">這個範例會連接到電腦的預設 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 執行個體。</span><span class="sxs-lookup"><span data-stu-id="d1493-120">This sample connects to your computer's default [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="d1493-121">若要連接到具名執行個體，請變更 ODBC 資料來源的定義，以便使用下列格式指定執行個體：server\namedinstance。</span><span class="sxs-lookup"><span data-stu-id="d1493-121">To connect to a named instance, change the definition of the ODBC data source to specify the instance using the following format: server\namedinstance.</span></span> <span data-ttu-id="d1493-122">根據預設，[!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] 會安裝至具名執行個體。</span><span class="sxs-lookup"><span data-stu-id="d1493-122">By default, [!INCLUDE[ssExpress](../../../includes/ssexpress-md.md)] installs to a named instance.</span></span>  
  
 <span data-ttu-id="d1493-123">執行第一個 ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) 程式碼清單，以便建立此範例將使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="d1493-123">Execute the first ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to create the table that the sample will use.</span></span>  
  
 <span data-ttu-id="d1493-124">複製第二個程式碼清單並將它貼入名為 Bcpfmt.fmt 的檔案中。</span><span class="sxs-lookup"><span data-stu-id="d1493-124">Copy the second code listing and paste it into a file called Bcpfmt.fmt.</span></span> <span data-ttu-id="d1493-125">資料表中的每個資料行都以定位字元分隔。</span><span class="sxs-lookup"><span data-stu-id="d1493-125">Each column in the table is separated by a tab character.</span></span>  
  
 <span data-ttu-id="d1493-126">複製第三個程式碼清單並將它貼入名為 Bcpodbc.bcp 的檔案中。</span><span class="sxs-lookup"><span data-stu-id="d1493-126">Copy the third code listing and paste it into a file called Bcpodbc.bcp.</span></span> <span data-ttu-id="d1493-127">定位字元位於檔案中的每個歸位字元前面。</span><span class="sxs-lookup"><span data-stu-id="d1493-127">A tab character precedes each carriage return in the file.</span></span>  
  
 <span data-ttu-id="d1493-128">使用 odbc32.lib 和 odbcbcp.lib 編譯第四個 (C++) 程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="d1493-128">Compile the fourth (C++) code listing with odbc32.lib and odbcbcp.lib.</span></span> <span data-ttu-id="d1493-129">如果您使用 MSBuild.exe 建立，請將 Bcpfmt.fmt 和 Bcpodbc.bcp 從專案目錄複製到具有該 .exe 的目錄，然後叫用該 .exe。</span><span class="sxs-lookup"><span data-stu-id="d1493-129">If you built with MSBuild.exe, copy Bcpfmt.fmt and Bcpodbc.bcp from the project directory into the directory with the .exe and then invoke the .exe.</span></span>  
  
 <span data-ttu-id="d1493-130">執行第五個 ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) 程式碼清單，以便刪除此範例所使用的資料表。</span><span class="sxs-lookup"><span data-stu-id="d1493-130">Execute the fifth ([!INCLUDE[tsql](../../../includes/tsql-md.md)]) code listing to delete the table that the sample used.</span></span>  
  
```sql
use AdventureWorks  
CREATE TABLE BCPDate (cola int, colb datetime)  
```  
  
```  
8.0  
2  
1SQLCHAR04"\t"1colaSQL_Latin1_General_Cp437_Bin  
2SQLCHAR08"\r\n"2colbSQL_Latin1_General_Cp437_Bin  
```  
  
```  
1  
2  
```  
  
```cpp
// compile with: odbc32.lib odbcbcp.lib  
#include <stdio.h>  
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
  
   // Allocate ODBC connection handle, set BCP mode, and connect.  
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
  
   // Sample uses Integrated Security. Create SQL Server DSN using Windows NT authentication.  
   retcode = SQLConnect(hdbc1, (UCHAR*)"AdventureWorks", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
   if ( (retcode != SQL_SUCCESS) && (retcode != SQL_SUCCESS_WITH_INFO) ) {  
      printf("SQLConnect() Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Initialize the bulk copy.  
   retcode = bcp_init(hdbc1, "BCPDate", "BCPODBC.bcp", NULL, DB_IN);  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_init(hdbc1) Failed\n\n");  
      Cleanup();  
      return(9);  
   }  
  
   // Read the format file.  
   retcode = bcp_readfmt(hdbc1, "BCPFMT.fmt");  
   if ( (retcode != SUCCEED) ) {  
      printf("bcp_readfmt(hdbc1) Failed\n\n");  
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
  
   printf("Number of rows bulk copied in = %d.\n", cRows);  
  
   // Cleanup  
   SQLDisconnect(hdbc1);  
   SQLFreeHandle(SQL_HANDLE_DBC, hdbc1);  
   SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
```sql
use AdventureWorks  
IF EXISTS (SELECT name FROM sysobjects WHERE name = 'BCPDate')  
     DROP TABLE BCPDate  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="d1493-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1493-131">See Also</span></span>  
 <span data-ttu-id="d1493-132">[使用 SQL Server ODBC 驅動程式的大量複製如何 &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="d1493-132">[Bulk Copying with the SQL Server ODBC Driver How-to Topics &#40;ODBC&#41;](bulk-copying-with-the-sql-server-odbc-driver-how-to-topics-odbc.md) </span></span>  
 [<span data-ttu-id="d1493-133">使用資料檔案與格式檔案</span><span class="sxs-lookup"><span data-stu-id="d1493-133">Using Data Files and Format Files</span></span>](../../native-client-odbc-bulk-copy-operations/using-data-files-and-format-files.md)  
  
  
