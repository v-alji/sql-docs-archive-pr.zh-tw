---
title: 使用 FILESTREAM 以累加的方式傳送和接收資料 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
ms.assetid: b82ecf4c-f151-4a99-8717-a73ee5ec994f
author: rothja
ms.author: jroth
ms.openlocfilehash: c7a47f0b0647516430f50dec433a93b4da2d2b49
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595926"
---
# <a name="send-and-receive-data-incrementally-with-filestream-odbc"></a><span data-ttu-id="a7860-102">利用 FILESTREAM 累加地傳送和接收資料 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="a7860-102">Send and Receive Data Incrementally with FILESTREAM (ODBC)</span></span>
  <span data-ttu-id="a7860-103">此範例會示範如何使用 FILESTREAM 功能，以 SQLPutData 和 SQLGetData 累加地傳送和接收資料。</span><span class="sxs-lookup"><span data-stu-id="a7860-103">This sample shows how to use the FILESTREAM feature to send and receive data incrementally with SQLPutData and SQLGetData.</span></span>  
  
 <span data-ttu-id="a7860-104">如需有關 FILESTREAM 功能的詳細資訊，請參閱[&#40;ODBC&#41;的 Filestream 支援](../native-client/odbc/filestream-support-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="a7860-104">For more information about the FILESTREAM feature, see [FILESTREAM Support &#40;ODBC&#41;](../native-client/odbc/filestream-support-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7860-105">範例</span><span class="sxs-lookup"><span data-stu-id="a7860-105">Example</span></span>  
 <span data-ttu-id="a7860-106">編譯並執行此範例之前，請先啟用 FILESTREAM 支援 ([啟用及設定 FILESTREAM](../blob/enable-and-configure-filestream.md))。</span><span class="sxs-lookup"><span data-stu-id="a7860-106">Before you compile and run this sample, enable FILESTREAM support ([Enable and Configure FILESTREAM](../blob/enable-and-configure-filestream.md)).</span></span>  
  
 <span data-ttu-id="a7860-107">第一個 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 程式碼清單會建立此範例所使用的資料庫。</span><span class="sxs-lookup"><span data-stu-id="a7860-107">The first ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing creates a database used by this sample.</span></span> <span data-ttu-id="a7860-108">您的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體必須擁有執行這個指令碼的寫入存取權 (例如，以本機系統帳戶的身分登入)。</span><span class="sxs-lookup"><span data-stu-id="a7860-108">Your instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] must have write access to run this script (for example, log on as a local system account).</span></span>  
  
 <span data-ttu-id="a7860-109">第二個程式碼清單是 C++ 程式碼。</span><span class="sxs-lookup"><span data-stu-id="a7860-109">The second code listing is the C++ code.</span></span> <span data-ttu-id="a7860-110">您必須指定伺服器，然後在 C++ 程式碼清單中，將 "MyServer" 變更為有效的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="a7860-110">You must specify a server; in the C++ code listing, change "MyServer" to a valid server name.</span></span> <span data-ttu-id="a7860-111">請確認您的 INCLUDE 環境變數包含的目錄內含 sqlncli.h。</span><span class="sxs-lookup"><span data-stu-id="a7860-111">Make sure your INCLUDE environment variable includes the directory that contains sqlncli.h.</span></span> <span data-ttu-id="a7860-112">請使用 odbc32.lib、user32.lib、/D "_UNICODE"、/D "UNICODE"、odbc32.lib 和 /EHsc 編譯 C++ 程式碼清單。</span><span class="sxs-lookup"><span data-stu-id="a7860-112">Compile the C++ code listing with odbc32.lib, user32.lib, /D "_UNICODE", /D "UNICODE", odbc32.lib, and /EHsc.</span></span>  
  
 <span data-ttu-id="a7860-113">第三個 ([!INCLUDE[tsql](../../includes/tsql-md.md)]) 程式碼清單會刪除此範例所使用的資料庫。</span><span class="sxs-lookup"><span data-stu-id="a7860-113">The third ([!INCLUDE[tsql](../../includes/tsql-md.md)]) code listing deletes the database used by this sample.</span></span>  
  
```  
USE master  
GO  
  
-- enable file stream  
exec sp_configure 'filestream access level', 2  
GO  
  
-- create directory for filestream database  
EXEC sp_configure 'show advanced options', 1  
GO  
RECONFIGURE  
GO  
EXEC sp_configure 'xp_cmdshell', 1  
GO  
RECONFIGURE  
GO  
EXEC xp_cmdshell 'md c:\filestreamdemo'  
GO  
  
-- Drop the filestream demo database  
IF EXISTS (SELECT name FROM master..sysdatabases WHERE name = 'myfilestreamdb')  
    DROP DATABASE [myfilestreamdb]  
GO  
  
-- Create filestream demo database  
CREATE DATABASE [myfilestreamdb] ON PRIMARY  
    (NAME=[myfilestreamdbprimary], FILENAME='c:\filestreamdemo\dbf.mdf'),  
    FILEGROUP [fsgrp] CONTAINS FILESTREAM (NAME=[fscnt],FILENAME='c:\filestreamdemo\fscnt')  
    LOG ON (NAME=[dblog], FILENAME='c:\filestreamdemo\db1.ldf', SIZE=5MB, MAXSIZE=3000MB, FILEGROWTH=5MB)  
GO  
  
-- Create table that contain filestream column  
CREATE TABLE [myfilestreamdb]..[mydocs]  
(  
    id UNIQUEIDENTIFIER ROWGUIDCOL NOT NULL UNIQUE,  
    doc VARBINARY(MAX) FILESTREAM  
)  
GO  
```  
  
```  
// compile with: /D "_UNICODE" /D "UNICODE" odbc32.lib /EHsc  
#pragma once  
#define WIN32_LEAN_AND_MEAN  
#include <tchar.h>  
#include <windows.h>  
#include <stdio.h>  
#include <sql.h>  
#include <sqlext.h>  
  
#define _SQLNCLI_ODBC_  
#include <sqlncli.h>  
  
#define SUCCESS(x) (!((x) & 0xFFFE))  
  
#define CHKRC(stmt) do { \  
                        rc = (stmt); \  
                        if (!SUCCESS(rc)) \  
                            throw (RETCODE) rc; \  
                    } while(0);  
  
void PrintError(SQLSMALLINT HandleType, SQLHANDLE Handle) {  
    RETCODE rc = SQL_SUCCESS;  
    SQLTCHAR szSqlState[6], szMessage[1024];  
    SQLSMALLINT i = 1, msgLen = 0;  
    SQLINTEGER NativeError;  
  
    do {  
       i = 1;  
       while (SQL_NO_DATA != (rc = SQLGetDiagRec(HandleType, Handle, i, szSqlState, &NativeError, szMessage, sizeof(szMessage)/sizeof(SQLTCHAR), &msgLen)) && SUCCESS(rc)) {  
            _tprintf(_T("SQLState=%s, NativeError=%ld, Message=%s\r\n"), szSqlState, NativeError, szMessage);  
            i++;  
        }  
    }   
    while (SQL_NO_DATA != (rc = SQLMoreResults(Handle)) && SUCCESS(rc));  
}  
  
int _tmain(int argc, _TCHAR* argv[]) {  
    RETCODE rc = SQL_SUCCESS;  
    HENV henv = SQL_NULL_HENV;  
    HDBC hdbc = SQL_NULL_HDBC;  
    SQLHSTMT hstmt = SQL_NULL_HSTMT;  
    SQLTCHAR * pszConnection = _T("DRIVER={SQL Server Native Client 10.0};")  
                               _T("Server=MyServer;")  
                               _T("Trusted_Connection=Yes;");  
    SQLLEN cbBuffer = SQL_DATA_AT_EXEC;  
    BYTE rgbDoc[1024];  
    SQLLEN cbDoc;  
  
    try {  
        CHKRC(SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HENV, &henv));  
        CHKRC(SQLSetEnvAttr(henv, SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, 0));  
        CHKRC(SQLAllocHandle(SQL_HANDLE_DBC, henv, &hdbc));  
        CHKRC(SQLDriverConnect(hdbc, NULL, pszConnection, SQL_NTS, NULL, 0, NULL, SQL_DRIVER_NOPROMPT));  
  
        CHKRC(SQLAllocHandle(SQL_HANDLE_STMT, hdbc, &hstmt));  
        CHKRC(SQLPrepare(hstmt,  (SQLTCHAR *)_T("INSERT INTO [myfilestreamdb]..[mydocs] VALUES(newid(), ?)"), SQL_NTS));  
        CHKRC(SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_BINARY, SQL_VARBINARY, SQL_SS_LENGTH_UNLIMITED, 0, (SQLPOINTER)1, 0, &cbBuffer));  
  
        rc = ::SQLExecute(hstmt);  
        if (SQL_NEED_DATA == rc) {  
            SQLPOINTER pParam = NULL;  
            while (SQL_NEED_DATA == (rc = ::SQLParamData(hstmt, (SQLPOINTER *)&pParam))) {  
                CHKRC(SQLPutData(hstmt, "Hello ", 6));  
                CHKRC(SQLPutData(hstmt, "World!", 6));  
            }  
        }  
  
        CHKRC(SQLFreeStmt(hstmt, SQL_CLOSE));  
        CHKRC(SQLExecDirect(hstmt, _T("SELECT doc FROM [myfilestreamdb]..[mydocs]"), SQL_NTS));  
        CHKRC(SQLBindCol(hstmt, 1, SQL_C_BINARY, (SQLPOINTER)rgbDoc, sizeof(rgbDoc), &cbDoc));  
        CHKRC(SQLFetch(hstmt));  
  
        rgbDoc[cbDoc] = '\0';  
        printf("%s\r\n", (LPSTR)rgbDoc);  
    }  
    catch (RETCODE retcode) {  
        rc = retcode;  
    }  
  
    if (!SUCCESS(rc))  
        if (hstmt)  
            PrintError(SQL_HANDLE_STMT, hstmt);  
        else if (hdbc)  
            PrintError(SQL_HANDLE_DBC, hdbc);  
        else if(henv)  
            PrintError(SQL_HANDLE_ENV, henv);  
  
    if (hstmt)  
        SQLFreeHandle(SQL_HANDLE_STMT, hstmt);  
  
    if (hdbc) {  
        SQLDisconnect(hdbc);  
        SQLFreeHandle(SQL_HANDLE_DBC, hdbc);  
    }  
  
    if (henv)  
        SQLFreeHandle(SQL_HANDLE_ENV, henv);  
}  
```  
  
```  
USE master  
GO  
-- Drop the filestream demo database  
sp_detach_db 'myfilestreamdb'  
IF EXISTS (SELECT name FROM master..sysdatabases WHERE name = 'myfilestreamdb')  
    DROP DATABASE [myfilestreamdb]  
EXEC xp_cmdshell 'rd /s /q c:\filestreamdemo'  
GO  
```  
  
  
