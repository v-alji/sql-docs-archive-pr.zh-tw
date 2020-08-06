---
title: bcp_setbulkmode |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bcp_setbulkmode function
ms.assetid: de56f206-1f7e-4c03-bf22-da9c7f9f4433
author: rothja
ms.author: jroth
ms.openlocfilehash: 1b7a68dfb3c868422b2e01cccf511a623d3afe52
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597102"
---
# <a name="bcp_setbulkmode"></a><span data-ttu-id="f643b-102">bcp_setbulkmode</span><span class="sxs-lookup"><span data-stu-id="f643b-102">bcp_setbulkmode</span></span>
  <span data-ttu-id="f643b-103">bcp_setbulkmode 可讓您在大量複製作業中指定資料行格式，在單一函數呼叫中設定所有資料行屬性。</span><span class="sxs-lookup"><span data-stu-id="f643b-103">bcp_setbulkmode lets you specify the column format in a bulk copy operation, setting all the column attributes in a single function call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f643b-104">語法</span><span class="sxs-lookup"><span data-stu-id="f643b-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_setbulkmode (  
   HDBC   
hdbc  
,  
   INT   
property  
,  
   void *   
pField  
,  
   INT   
cbField  
,  
   void *   
pRow  
,  
   INT   
cbRow  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="f643b-105">引數</span><span class="sxs-lookup"><span data-stu-id="f643b-105">Arguments</span></span>  
 <span data-ttu-id="f643b-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="f643b-106">*hdbc*</span></span>  
 <span data-ttu-id="f643b-107">已啟用大量複製的 ODBC 連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="f643b-107">The bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="f643b-108">*property*</span><span class="sxs-lookup"><span data-stu-id="f643b-108">*property*</span></span>  
 <span data-ttu-id="f643b-109">類型為 BYTE 的常數。</span><span class="sxs-lookup"><span data-stu-id="f643b-109">A constant of type BYTE.</span></span> <span data-ttu-id="f643b-110">如需常數的清單，請參閱＜備註＞一節中的表格。</span><span class="sxs-lookup"><span data-stu-id="f643b-110">See the table in the Remarks section for a list of the constants.</span></span>  
  
 <span data-ttu-id="f643b-111">*pField*</span><span class="sxs-lookup"><span data-stu-id="f643b-111">*pField*</span></span>  
 <span data-ttu-id="f643b-112">欄位結束字元值的指標。</span><span class="sxs-lookup"><span data-stu-id="f643b-112">The pointer to the field terminator value.</span></span>  
  
 <span data-ttu-id="f643b-113">*cbField*</span><span class="sxs-lookup"><span data-stu-id="f643b-113">*cbField*</span></span>  
 <span data-ttu-id="f643b-114">欄位結束字元值的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="f643b-114">The length (in bytes) of the field terminator value.</span></span>  
  
 <span data-ttu-id="f643b-115">*pRow*</span><span class="sxs-lookup"><span data-stu-id="f643b-115">*pRow*</span></span>  
 <span data-ttu-id="f643b-116">資料列結束字元值的指標。</span><span class="sxs-lookup"><span data-stu-id="f643b-116">The pointer to the row terminator value.</span></span>  
  
 <span data-ttu-id="f643b-117">*cbRow*</span><span class="sxs-lookup"><span data-stu-id="f643b-117">*cbRow*</span></span>  
 <span data-ttu-id="f643b-118">資料列結束字元值的長度 (以位元組為單位)。</span><span class="sxs-lookup"><span data-stu-id="f643b-118">The length in bytes of the row terminator value.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="f643b-119">傳回</span><span class="sxs-lookup"><span data-stu-id="f643b-119">Returns</span></span>  
 <span data-ttu-id="f643b-120">SUCCEED 或 FAIL</span><span class="sxs-lookup"><span data-stu-id="f643b-120">SUCCEED or FAIL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f643b-121">備註</span><span class="sxs-lookup"><span data-stu-id="f643b-121">Remarks</span></span>  
 <span data-ttu-id="f643b-122">bcp_setbulkmode 可以用來從查詢或資料表大量複製。</span><span class="sxs-lookup"><span data-stu-id="f643b-122">bcp_setbulkmode can be used to bulk copy out of either a query or a table.</span></span> <span data-ttu-id="f643b-123">當 bcp_setbulkmode 用來大量複製查詢語句時，必須先呼叫它，才能使用 BCP_HINT 呼叫 bcp_control。</span><span class="sxs-lookup"><span data-stu-id="f643b-123">When bcp_setbulkmode is used to bulk copy out a query statement, it must be called before calling bcp_control with BCP_HINT.</span></span>  
  
 <span data-ttu-id="f643b-124">bcp_setbulkmode 是使用[bcp_setcolfmt](bcp-setcolfmt.md)和[bcp_columns](bcp-columns.md)的替代方法，其只可讓您針對每個函式呼叫指定一個資料行的格式。</span><span class="sxs-lookup"><span data-stu-id="f643b-124">bcp_setbulkmode is an alternative to using [bcp_setcolfmt](bcp-setcolfmt.md) and [bcp_columns](bcp-columns.md), which only let you specify the format of one column per function call.</span></span>  
  
 <span data-ttu-id="f643b-125">下表將列出 *property* 參數的常數。</span><span class="sxs-lookup"><span data-stu-id="f643b-125">The following table lists the constants for the *property* parameter.</span></span>  
  
|<span data-ttu-id="f643b-126">屬性</span><span class="sxs-lookup"><span data-stu-id="f643b-126">Property</span></span>|<span data-ttu-id="f643b-127">描述</span><span class="sxs-lookup"><span data-stu-id="f643b-127">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="f643b-128">BCP_OUT_CHARACTER_MODE</span><span class="sxs-lookup"><span data-stu-id="f643b-128">BCP_OUT_CHARACTER_MODE</span></span>|<span data-ttu-id="f643b-129">指定字元輸出模式。</span><span class="sxs-lookup"><span data-stu-id="f643b-129">Specifies character output mode.</span></span><br /><br /> <span data-ttu-id="f643b-130">對應至 BCP.EXE 中的-c 選項，以及 `BCP_FMT_TYPE` 屬性設定為的 bcp_setcolfmt `SQLCHARACTER` 。</span><span class="sxs-lookup"><span data-stu-id="f643b-130">Corresponds to the -c option in BCP.EXE, and to bcp_setcolfmt with `BCP_FMT_TYPE` property set to `SQLCHARACTER`.</span></span>|  
|<span data-ttu-id="f643b-131">BCP_OUT_WIDE_CHARACTER_MODE</span><span class="sxs-lookup"><span data-stu-id="f643b-131">BCP_OUT_WIDE_CHARACTER_MODE</span></span>|<span data-ttu-id="f643b-132">指定 Unicode 輸出模式。</span><span class="sxs-lookup"><span data-stu-id="f643b-132">Specifies Unicode output mode.</span></span><br /><br /> <span data-ttu-id="f643b-133">對應至 BCP.EXE 和 bcp_setcolfmt 中的-w 選項，並 `BCP_FMT_TYPE` 將屬性設定為 `SQLNCHAR` 。</span><span class="sxs-lookup"><span data-stu-id="f643b-133">Corresponds to the -w option in BCP.EXE and bcp_setcolfmt with `BCP_FMT_TYPE` property set to `SQLNCHAR`.</span></span>|  
|<span data-ttu-id="f643b-134">BCP_OUT_NATIVE_TEXT_MODE</span><span class="sxs-lookup"><span data-stu-id="f643b-134">BCP_OUT_NATIVE_TEXT_MODE</span></span>|<span data-ttu-id="f643b-135">指定非字元類型的原生類型和字元類型的 Unicode。</span><span class="sxs-lookup"><span data-stu-id="f643b-135">Specifies native types for non-character types and Unicode for character types.</span></span><br /><br /> <span data-ttu-id="f643b-136">對應至 BCP.EXE 中的-N 選項，而且如果資料 `BCP_FMT_TYPE` 行類型是 (字串，則為屬性設定為的 bcp_setcolfmt （ `SQLNCHAR` 如果不是字串) 則為預設值）。</span><span class="sxs-lookup"><span data-stu-id="f643b-136">Corresponds to the -N option in BCP.EXE and bcp_setcolfmt with `BCP_FMT_TYPE` property set to `SQLNCHAR` if the column type is a string (default if not a string).</span></span>|  
|<span data-ttu-id="f643b-137">BCP_OUT_NATIVE_MODE</span><span class="sxs-lookup"><span data-stu-id="f643b-137">BCP_OUT_NATIVE_MODE</span></span>|<span data-ttu-id="f643b-138">指定原生資料庫類型。</span><span class="sxs-lookup"><span data-stu-id="f643b-138">Specifies native database types.</span></span><br /><br /> <span data-ttu-id="f643b-139">對應至 BCP.EXE 和 bcp_setcolfmt 中的-n 選項，並 `BCP_FMT_TYPE` 將屬性設定為預設值。</span><span class="sxs-lookup"><span data-stu-id="f643b-139">Corresponds to the -n option in BCP.EXE and bcp_setcolfmt with `BCP_FMT_TYPE` property set to the default.</span></span>|  
  
 <span data-ttu-id="f643b-140">您不應將 bcp_setbulkmode 與包含 bcp_setcolfmt、bcp_control 和 bcp_readfmt 的函式呼叫順序搭配使用。</span><span class="sxs-lookup"><span data-stu-id="f643b-140">You should not use bcp_setbulkmode with a sequence of function calls that includes bcp_setcolfmt, bcp_control, and bcp_readfmt.</span></span> <span data-ttu-id="f643b-141">例如，您不應該呼叫 bcp_control (BCPTEXTFILE) 和 bcp_setbulkmode。</span><span class="sxs-lookup"><span data-stu-id="f643b-141">For example, you should not call bcp_control(BCPTEXTFILE) and bcp_setbulkmode.</span></span>  
  
 <span data-ttu-id="f643b-142">您可以針對不與 bcp_setbulkmode 衝突的 bcp_control 選項呼叫 bcp_control 和 bcp_setbulkmode。</span><span class="sxs-lookup"><span data-stu-id="f643b-142">You can call bcp_control and bcp_setbulkmode for bcp_control options that do not conflict with bcp_setbulkmode.</span></span> <span data-ttu-id="f643b-143">例如，您可以呼叫 bcp_control (BCPFIRST) 和 bcp_setbulkmode。</span><span class="sxs-lookup"><span data-stu-id="f643b-143">For example, you can call bcp_control(BCPFIRST) and bcp_setbulkmode.</span></span>  
  
 <span data-ttu-id="f643b-144">如果您嘗試使用包含 bcp_setcolfmt、bcp_control 和 bcp_readfmt 的函式呼叫序列來呼叫 bcp_setbulkmode，其中一個函式呼叫會傳回序列錯誤失敗。</span><span class="sxs-lookup"><span data-stu-id="f643b-144">If you attempt to call bcp_setbulkmode with a sequence of function calls that includes bcp_setcolfmt, bcp_control, and bcp_readfmt, one of the function calls will return a sequence error failure.</span></span> <span data-ttu-id="f643b-145">如果您選擇更正失敗，請呼叫 bcp_init 以重設所有設定並重新開始。</span><span class="sxs-lookup"><span data-stu-id="f643b-145">If you choose to correct the failure, call bcp_init to reset all the settings and start over.</span></span>  
  
 <span data-ttu-id="f643b-146">下表將呈現產生函數順序錯誤之函數呼叫的部分範例。</span><span class="sxs-lookup"><span data-stu-id="f643b-146">The following table presents some examples of function calls that result in a function sequence error:</span></span>  
  
 <span data-ttu-id="f643b-147">呼叫順序</span><span class="sxs-lookup"><span data-stu-id="f643b-147">Call sequence</span></span>  
  
```  
bcp_init("table", DB_IN);  
bcp_setbulkmode();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_setbulkmode();  
bcp_readfmt();  
```  
  
```  
bcp_init(NULL, DB_OUT);  
bcp_control(BCPHINTS, "select ...");  
bcp_setbulkmode();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_setbulkmode();  
bcp_setcolfmt();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_readfmt();  
bcp_setcolfmt();  
```  
  
```  
bcp_init(NULL, DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_setbulkmode();  
bcp_control(BCPHINTS, "select ...");  
bcp_readfmt();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_columns();  
```  
  
```  
bcp_init("table", DB_OUT);  
bcp_control(BCPDELAYREADFMT, true);  
bcp_setcolfmt();  
```  
  
## <a name="example"></a><span data-ttu-id="f643b-148">範例</span><span class="sxs-lookup"><span data-stu-id="f643b-148">Example</span></span>  
 <span data-ttu-id="f643b-149">下列範例會使用不同的 bcp_setbulkmode 設定來建立四個檔案。</span><span class="sxs-lookup"><span data-stu-id="f643b-149">The following sample creates four files using different settings of bcp_setbulkmode.</span></span>  
  
```  
// compile with: sqlncli11.lib odbc32.lib  
  
#include <windows.h>  
#include <stdio.h>  
#include <tchar.h>  
#include <sqlext.h>  
#include "sqlncli.h"  
  
// Global variables  
SQLHENV g_hEnv = NULL;  
SQLHDBC g_hDbc = NULL;  
  
void ODBCCleanUp() {  
   if (g_hDbc) {  
      SQLDisconnect(g_hDbc);  
      SQLFreeHandle(SQL_HANDLE_DBC, g_hDbc);  
      g_hDbc = NULL;  
   }  
   if (g_hEnv) {  
      SQLFreeHandle(SQL_HANDLE_ENV, g_hEnv);  
      g_hEnv = NULL;  
   }  
}  
  
BOOL MakeODBCConnection(TCHAR * pszServer) {  
   TCHAR szConnectionString[500];  
   TCHAR szOutConnectionString[500];  
   SQLSMALLINT iLen;  
   SQLRETURN rc;  
  
   _sntprintf_s(szConnectionString, 500, TEXT("DRIVER={SQL Server Native Client 11.0};Server=%s;Trusted_connection=yes;"), pszServer);  
   rc = SQLAllocHandle(SQL_HANDLE_ENV, SQL_NULL_HANDLE,&g_hEnv);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLAllocHandle(SQL_HANDLE_ENV...) failed\n");  
      return false;  
   }  
   rc = SQLSetEnvAttr(g_hEnv,SQL_ATTR_ODBC_VERSION, (SQLPOINTER)SQL_OV_ODBC3, SQL_IS_UINTEGER);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLSetEnvAttr failed\n");  
      SQLFreeHandle(SQL_HANDLE_ENV, g_hEnv);  
      return false;  
   }  
   rc = SQLAllocHandle( SQL_HANDLE_DBC, g_hEnv , &g_hDbc);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLAllocHandle(SQL_HANDLE_DBC...) failed\n");  
      SQLFreeHandle(SQL_HANDLE_ENV, g_hEnv);  
      return false;  
   }  
   // Enable BCP  
   rc = SQLSetConnectAttr(g_hDbc, SQL_COPT_SS_BCP, (SQLPOINTER)SQL_BCP_ON, SQL_IS_INTEGER);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLSetConnectAttr(.. SQL_COPT_SS_BCP, (SQLPOINTER)SQL_BCP_ON ...) failed\n");  
      ODBCCleanUp();  
      return false;  
   }  
   // connecting ...  
   rc = SQLDriverConnect(g_hDbc,NULL, (SQLTCHAR*)szConnectionString, SQL_NTS, (SQLTCHAR*)szOutConnectionString, 500, &iLen, SQL_DRIVER_NOPROMPT);  
   if (SQL_SUCCESS != rc && SQL_SUCCESS_WITH_INFO != rc) {  
      printf("SQLDriverConnect(SQL_HANDLE_DBC...) failed\n");  
      ODBCCleanUp();  
      return false;  
   }  
   return true;  
}  
  
BOOL BCPSetBulkMode(TCHAR * pszServer, TCHAR * pszQureryOut, char BCPType, TCHAR * pszDataFile) {  
   SQLRETURN rc;  
  
   if (!MakeODBCConnection(pszServer))  
      return false;  
   rc = bcp_init(g_hDbc, NULL, pszDataFile, NULL, DB_OUT);   // bcp init for queryout  
   if (SUCCEED != rc) {  
      printf("bcp_init failed\n");  
      ODBCCleanUp();  
      return false;  
   }  
   // setbulkmode  
   char ColTerm[] = "\t";  
   char RowTerm[] = "\r\n";  
   wchar_t wColTerm[] = L"\t";  
   wchar_t wRowTerm[] = L"\r\n";  
   BYTE * pColTerm = NULL;  
   int cbColTerm = NULL;  
   BYTE * pRowTerm = 0;  
   int cbRowTerm = 0;  
   int bulkmode = -1;  
  
   if (BCPType == 'c') {   // bcp -c  
      pColTerm = (BYTE*)ColTerm;  
      pRowTerm = (BYTE*)RowTerm;  
      cbColTerm = 1;  
      cbRowTerm = 2;  
      bulkmode = BCP_OUT_CHARACTER_MODE;  
   }  
   else  
      if (BCPType == 'w') {   // bcp -w   
         pColTerm = (BYTE*)wColTerm;  
         pRowTerm = (BYTE*)wRowTerm;  
         cbColTerm = 2;  
         cbRowTerm = 4;  
         bulkmode = BCP_OUT_WIDE_CHARACTER_MODE;  
      }  
      else  
         if (BCPType == 'n')   // bcp -n  
            bulkmode = BCP_OUT_NATIVE_MODE;  
         else  
            if (BCPType == 'N')   // bcp -n  
               bulkmode = BCP_OUT_NATIVE_TEXT_MODE;  
            else {  
               printf("unknown bcp mode\n");  
               ODBCCleanUp();  
               return false;  
            }  
            rc = bcp_setbulkmode(g_hDbc, bulkmode, pColTerm, cbColTerm, pRowTerm, cbRowTerm);  
            if (SUCCEED != rc) {  
               printf("bcp_setbulkmode failed\n");  
               ODBCCleanUp();  
               return false;  
            }  
            // set queryout TSQL statement  
            rc = bcp_control(g_hDbc, BCPHINTS , pszQureryOut);  
            if (SUCCEED != rc) {  
               printf("bcp_control(..BCP_OPTION_HINTS..) failed\n");  
               ODBCCleanUp();  
               return false;  
            }  
            // bcp copy  
            DBINT nRowsInserted = 0;  
            rc = bcp_exec(g_hDbc, &nRowsInserted);  
            if (SUCCEED != rc) {  
               printf("bcp_exec failed\n");  
               ODBCCleanUp();  
               return false;  
            }  
            printf("bcp done\n");  
            ODBCCleanUp();  
            return true;  
}  
  
int main() {  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -c test', 1,2") , 'c', TEXT("bcpc.dat"));  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -w test', 1,2") , 'w', TEXT("bcpw.dat"));  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -c test', 1,2") , 'n', TEXT("bcpn.dat"));  
   BCPSetBulkMode(TEXT("localhost"), TEXT("SELECT 'this is a bcp -w test', 1,2") , 'N', TEXT("bcp_N.dat"));  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="f643b-150">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f643b-150">See Also</span></span>  
 [<span data-ttu-id="f643b-151">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="f643b-151">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
