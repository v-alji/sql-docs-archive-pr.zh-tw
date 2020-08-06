---
title: bcp_init |Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_init
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_init function
ms.assetid: 6a25862c-7f31-4873-ab65-30f3abde89d2
author: rothja
ms.author: jroth
ms.openlocfilehash: 72d48b2a07e425e0863084c700c4de93d2776739
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594060"
---
# <a name="bcp_init"></a><span data-ttu-id="7d9b6-102">bcp_init</span><span class="sxs-lookup"><span data-stu-id="7d9b6-102">bcp_init</span></span>
  <span data-ttu-id="7d9b6-103">初始化大量複製作業。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-103">Initializes the bulk copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d9b6-104">語法</span><span class="sxs-lookup"><span data-stu-id="7d9b6-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_init (  
HDBC   
hdbc  
,  
LPCTSTR   
szTable  
,  
LPCTSTR   
szDataFile  
,  
LPCTSTR   
szErrorFile  
,  
INT   
eDirection  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="7d9b6-105">引數</span><span class="sxs-lookup"><span data-stu-id="7d9b6-105">Arguments</span></span>  
 <span data-ttu-id="7d9b6-106">*hdbc*</span><span class="sxs-lookup"><span data-stu-id="7d9b6-106">*hdbc*</span></span>  
 <span data-ttu-id="7d9b6-107">這是已啟用大量複製的 ODBC 連接控制代碼。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-107">Is the bulk copy-enabled ODBC connection handle.</span></span>  
  
 <span data-ttu-id="7d9b6-108">*szTable*</span><span class="sxs-lookup"><span data-stu-id="7d9b6-108">*szTable*</span></span>  
 <span data-ttu-id="7d9b6-109">這是要來回複製之資料庫資料表的名稱。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-109">Is the name of the database table to be copied into or out of.</span></span> <span data-ttu-id="7d9b6-110">此名稱也可以包含資料庫名稱或擁有者名稱。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-110">This name can also include the database name or the owner name.</span></span> <span data-ttu-id="7d9b6-111">例如， **gracie. 標題**、 **pubs.。標題**、 **gracie**和**標題**都是合法的資料表名稱。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-111">For example, **pubs.gracie.titles**, **pubs..titles**, **gracie.titles**, and **titles** are all legal table names.</span></span>  
  
 <span data-ttu-id="7d9b6-112">如果*eDirection*為 DB_OUT， *szTable*也可以是資料庫檢視的名稱。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-112">If *eDirection* is DB_OUT, *szTable* can also be the name of a database view.</span></span>  
  
 <span data-ttu-id="7d9b6-113">如果 DB_OUT *eDirection* ，而且在呼叫[bcp_exec](bcp-exec.md)之前使用[bcp_control](bcp-control.md)來指定 SELECT 語句， **bcp_init**_szTable_必須設定為 Null。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-113">If *eDirection* is DB_OUT and a SELECT statement is specified using [bcp_control](bcp-control.md) before [bcp_exec](bcp-exec.md) is called, **bcp_init**_szTable_ must be set to NULL.</span></span>  
  
 <span data-ttu-id="7d9b6-114">*szDataFile*</span><span class="sxs-lookup"><span data-stu-id="7d9b6-114">*szDataFile*</span></span>  
 <span data-ttu-id="7d9b6-115">這是要來回複製之使用者檔案的名稱。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-115">Is the name of the user file to be copied into or out of.</span></span> <span data-ttu-id="7d9b6-116">如果要使用[bcp_sendrow](bcp-sendrow.md)直接從變數複製資料，請將*SZDATAFILE*設定為 Null。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-116">If data is being copied directly from variables by using [bcp_sendrow](bcp-sendrow.md), set *szDataFile* to NULL.</span></span>  
  
 <span data-ttu-id="7d9b6-117">*szErrorFile*</span><span class="sxs-lookup"><span data-stu-id="7d9b6-117">*szErrorFile*</span></span>  
 <span data-ttu-id="7d9b6-118">這是錯誤檔案的名稱，該檔案會以進度訊息、錯誤訊息，以及因為任何原因而無法從使用者檔案複製到資料表之任何資料列的複本。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-118">Is the name of the error file to be filled with progress messages, error messages, and copies of any rows that, for any reason, could not be copied from a user file to a table.</span></span> <span data-ttu-id="7d9b6-119">如果將 Null 當做*szErrorFile*傳遞，則不會使用任何錯誤檔案。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-119">If NULL is passed as *szErrorFile*, no error file is used.</span></span>  
  
 <span data-ttu-id="7d9b6-120">*eDirection*</span><span class="sxs-lookup"><span data-stu-id="7d9b6-120">*eDirection*</span></span>  
 <span data-ttu-id="7d9b6-121">這是複製的方向，DB_IN 或 DB_OUT。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-121">Is the direction of the copy, either DB_IN or DB_OUT.</span></span> <span data-ttu-id="7d9b6-122">DB_IN 表示從程式變數或使用者檔案複製到資料表。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-122">DB_IN indicates a copy from program variables or a user file to a table.</span></span> <span data-ttu-id="7d9b6-123">DB_OUT 表示從資料庫資料表複製到使用者檔案。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-123">DB_OUT indicates a copy from a database table to a user file.</span></span> <span data-ttu-id="7d9b6-124">您必須利用 DB_OUT 指定使用者檔案名稱。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-124">You must specify a user file name with DB_OUT.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="7d9b6-125">傳回</span><span class="sxs-lookup"><span data-stu-id="7d9b6-125">Returns</span></span>  
 <span data-ttu-id="7d9b6-126">SUCCEED 或 FAIL。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-126">SUCCEED or FAIL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d9b6-127">備註</span><span class="sxs-lookup"><span data-stu-id="7d9b6-127">Remarks</span></span>  
 <span data-ttu-id="7d9b6-128">呼叫任何其他大量複製函數之前，請先呼叫**bcp_init** 。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-128">Call **bcp_init** before calling any other bulk-copy function.</span></span> <span data-ttu-id="7d9b6-129">**bcp_init**會針對工作站和之間的資料大量複製，執行必要的初始化 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-129">**bcp_init** performs the necessary initializations for a bulk copy of data between the workstation and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="7d9b6-130">必須提供已啟用 ODBC 連接控制碼的**bcp_init**函式，以便搭配大量複製函數使用。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-130">The **bcp_init** function must be provided with an ODBC connection handle enabled for use with bulk copy functions.</span></span> <span data-ttu-id="7d9b6-131">若要啟用控制碼，請在已配置但未連接的連接控制碼上，使用[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)搭配 SQL_COPT_SS_BCP 設定為 SQL_BCP_ON。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-131">To enable the handle, use [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) with SQL_COPT_SS_BCP set to SQL_BCP_ON on an allocated, but not connected, connection handle.</span></span> <span data-ttu-id="7d9b6-132">嘗試在已連接的控制代碼上指派屬性會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-132">Attempting to assign the attribute on a connected handle results in an error.</span></span>  
  
 <span data-ttu-id="7d9b6-133">當指定資料檔案時， **bcp_init**會檢查資料庫來源或目標資料表的結構，而不是資料檔案。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-133">When a data file is specified, **bcp_init** examines the structure of the database source or target table, not the data file.</span></span> <span data-ttu-id="7d9b6-134">**bcp_init**會根據資料庫資料表、VIEW 或 SELECT 結果集中的每個資料行，指定資料檔案的資料格式值。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-134">**bcp_init** specifies data format values for the data file based on each column in the database table, view, or SELECT result set.</span></span> <span data-ttu-id="7d9b6-135">這個指定包括每個資料行的資料類型、資料中是否有長度或 null 指標和結束字元位元組字串，以及固定長度資料類型的寬度。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-135">This specification includes the data type of each column, the presence or absence of a length or null indicator and terminator byte strings in the data, and the width of fixed-length data types.</span></span> <span data-ttu-id="7d9b6-136">**bcp_init**設定這些值，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7d9b6-136">**bcp_init** sets these values as follows:</span></span>  
  
-   <span data-ttu-id="7d9b6-137">指定的資料類型為資料行在資料庫資料表、檢視或 SELECT 結果集中的資料類型。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-137">The data type specified is the data type of the column in the database table, view, or SELECT result set.</span></span> <span data-ttu-id="7d9b6-138">資料類型會由 sqlncli.h 中所指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 原生資料類型列舉。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-138">The data type is enumerated by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] native data types specified in sqlncli.h.</span></span> <span data-ttu-id="7d9b6-139">資料本身會以其電腦格式表示。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-139">Data itself is represented in its computer form.</span></span> <span data-ttu-id="7d9b6-140">也就是說，來自**integer**資料類型之資料行的資料會根據建立資料檔案的電腦，以四個位元組的序列來表示。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-140">That is, data from a column of **integer** data type is represented by a four-byte sequence that is big-or little-endian based on the computer that created the data file.</span></span>  
  
-   <span data-ttu-id="7d9b6-141">如果資料庫資料類型的長度是固定的，資料檔案資料的長度也是固定的。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-141">If a database data type is fixed in length, the data file data is also fixed in length.</span></span> <span data-ttu-id="7d9b6-142">處理資料的大量複製函式 (例如， [bcp_exec](bcp-exec.md)) 剖析資料列，該資料列必須要有資料檔中的資料長度，與資料庫資料表、VIEW 或 SELECT 資料行清單中所指定之資料的長度相同。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-142">Bulk-copy functions that process data (for example, [bcp_exec](bcp-exec.md)) parse data rows expecting the length of the data in the data file to be identical to the length of the data specified in the database table, view, or SELECT column list.</span></span> <span data-ttu-id="7d9b6-143">例如，定義為\*\*char (13) \*\*之資料庫資料行的資料，在檔案中的每個資料列都必須以13個字元表示。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-143">For example, data for a database column defined as **char(13)** must be represented by 13 characters for each row of data in the file.</span></span> <span data-ttu-id="7d9b6-144">如果資料庫資料行允許使用 Null 值，固定長度的資料前置詞可以是 Null 指標。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-144">Fixed-length data can be prefixed with a null indicator if the database column allows null values.</span></span>  
  
-   <span data-ttu-id="7d9b6-145">定義結束字元位元組順序時，結束字元位元組順序的長度會設定為 0。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-145">When terminator-byte sequence is defined, the length of the terminator-byte sequence is set to 0.</span></span>  
  
-   <span data-ttu-id="7d9b6-146">複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，資料檔案對於資料庫資料表中的每個資料行都必須有資料。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-146">When copying to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the data file must have data for each column in the database table.</span></span> <span data-ttu-id="7d9b6-147">從 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 複製時，來自資料庫資料表、檢視或 SELECT 結果集中所有資料行的資料都會複製到資料檔案中。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-147">When copying from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], data from all columns in the database table, view, or SELECT result set are copied to the data file.</span></span>  
  
-   <span data-ttu-id="7d9b6-148">複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時，資料行在資料檔案中的序數位置必須與資料行在資料庫資料表中的序數位置相同。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-148">When copying to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], the ordinal position of a column in the data file must be identical to the ordinal position of the column in the database table.</span></span> <span data-ttu-id="7d9b6-149">從複製時 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ， **bcp_exec**會根據資料庫資料表中資料行的序數位置來放置資料。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-149">When copying from [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], **bcp_exec** places data based on the ordinal position of the column in the database table.</span></span>  
  
-   <span data-ttu-id="7d9b6-150">如果資料庫資料類型的長度可變 (例如， \*\*Varbinary (22) \*\*) 或者，如果資料庫資料行可以包含 null 值，資料檔案中的資料就會以長度/null 指標作為前置詞。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-150">If a database data type is variable in length (for example, **varbinary(22)**) or if a database column can contain null values, data in the data file is prefixed by a length/null indicator.</span></span> <span data-ttu-id="7d9b6-151">指標的寬度會根據資料類型和大量複製的版本而改變。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-151">The width of the indicator varies based on the data type and version of bulk copy.</span></span>  
  
 <span data-ttu-id="7d9b6-152">若要變更針對資料檔案指定的資料格式值，請呼叫[bcp_columns](bcp-columns.md)並[bcp_colfmt](bcp-colfmt.md)。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-152">To change data format values specified for a data file, call [bcp_columns](bcp-columns.md) and [bcp_colfmt](bcp-colfmt.md).</span></span>  
  
 <span data-ttu-id="7d9b6-153">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的大量複製可以針對不包含索引的資料表進行最佳化，方法是，將資料庫復原模式設定為 SIMPLE 或 BULK_LOGGED。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-153">Bulk copies to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can be optimized for tables that do not contain indexes by setting the database recovery model to SIMPLE or BULK_LOGGED.</span></span> <span data-ttu-id="7d9b6-154">如需詳細資訊，請參閱大量匯入和[ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql)[中最低限度記錄的必要條件](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md)。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-154">For more information, see [Prerequisites for Minimal Logging in Bulk Import](../import-export/prerequisites-for-minimal-logging-in-bulk-import.md) and [ALTER DATABASE](/sql/t-sql/statements/alter-database-transact-sql).</span></span>  
  
 <span data-ttu-id="7d9b6-155">如果沒有使用任何資料檔案，您必須呼叫[bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)來指定記憶體中每個資料行之為的格式和位置，然後使用 bcp_sendrow 將資料列複製到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。 [bcp_sendrow](bcp-sendrow.md)</span><span class="sxs-lookup"><span data-stu-id="7d9b6-155">If no data file is used, you must call [bcp_bind](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md) to specify the format and location in memory of the data fsor each column, then copy data rows to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using [bcp_sendrow](bcp-sendrow.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d9b6-156">範例</span><span class="sxs-lookup"><span data-stu-id="7d9b6-156">Example</span></span>  
 <span data-ttu-id="7d9b6-157">此範例顯示如何利用格式檔案使用 ODBC bcp_init 函數。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-157">This sample shows how to use the ODBC bcp_init function with a format file.</span></span>  
  
 <span data-ttu-id="7d9b6-158">編譯與執行 C++ 程式碼之前，您需要執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="7d9b6-158">Before you compile and run the C++ code, you need to do the following:</span></span>  
  
-   <span data-ttu-id="7d9b6-159">建立成為 Test 的 ODBC 資料來源。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-159">Create an ODBC data source called Test.</span></span> <span data-ttu-id="7d9b6-160">您可以讓此資料來源與任何資料庫產生關聯。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-160">You can associate this data source with any database.</span></span>  
  
-   <span data-ttu-id="7d9b6-161">在資料庫上執行下列 [!INCLUDE[tsql](../../includes/tsql-md.md)]：</span><span class="sxs-lookup"><span data-stu-id="7d9b6-161">Run the following [!INCLUDE[tsql](../../includes/tsql-md.md)] on the database:</span></span>  
  
    ```  
    CREATE TABLE BCPDate (cola int, colb datetime);  
    ```  
  
-   <span data-ttu-id="7d9b6-162">在您執行應用程式的目錄中，加入稱為 Bcpfmt.fmt 的檔案，並將其加入至檔案中：</span><span class="sxs-lookup"><span data-stu-id="7d9b6-162">In the directory where you will run the application, add a file called Bcpfmt.fmt, and add this to the file:</span></span>  
  
    ```  
    8.0  
    2  
    1SQLCHAR04"\t"1colaSQL_Latin1_General_Cp437_Bin  
    2SQLCHAR08"\r\n"2colbSQL_Latin1_General_Cp437_Bin  
    ```  
  
-   <span data-ttu-id="7d9b6-163">在您執行應用程式的目錄中，加入稱為 Bcpodbc.bcp 的檔案，並將其加入至檔案中：</span><span class="sxs-lookup"><span data-stu-id="7d9b6-163">In the directory where you will run the application, add a file called Bcpodbc.bcp, and add this to the file:</span></span>  
  
    ```  
    1  
    2  
    ```  
  
 <span data-ttu-id="7d9b6-164">現在，您可以編譯及執行 C++ 程式碼。</span><span class="sxs-lookup"><span data-stu-id="7d9b6-164">Now you are ready to compile and run the C++ code.</span></span>  
  
```  
// compile with: odbc32.lib sqlncli11.lib  
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
   retcode = SQLConnect(hdbc1, (UCHAR*)"Test", SQL_NTS, (UCHAR*)"", SQL_NTS, (UCHAR*)"", SQL_NTS);  
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
  
## <a name="see-also"></a><span data-ttu-id="7d9b6-165">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7d9b6-165">See Also</span></span>  
 [<span data-ttu-id="7d9b6-166">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="7d9b6-166">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
