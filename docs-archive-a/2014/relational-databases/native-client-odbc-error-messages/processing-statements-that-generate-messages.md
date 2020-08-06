---
title: 處理產生訊息的語句 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- PRINT statement
- messages [ODBC], statements generating messages
- statements [ODBC], message generation
- errors [ODBC], statements generating messages
- SQL Server Native Client ODBC driver, errors
- STATISTICS IO option
- STATISTICS TIME option
- DBCC statements
- SQLExecute function
- RAISERROR statement
- SQLGetDiagRec function
- ODBC error handling, statements generating messages
- SQLExecDirect function
ms.assetid: 672ebdc5-7fa1-4ceb-8d52-fd25ef646654
author: rothja
ms.author: jroth
ms.openlocfilehash: c26376eabb756d356dd71fb3bd8284a6b11dced7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698176"
---
# <a name="processing-statements-that-generate-messages"></a><span data-ttu-id="0813c-102">處理產生訊息的陳述式</span><span class="sxs-lookup"><span data-stu-id="0813c-102">Processing Statements That Generate Messages</span></span>
  <span data-ttu-id="0813c-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] SET 陳述式選項 STATISTICS TIME 和 STATISTICS IO 用於取得協助診斷長時間執行之查詢的資訊。</span><span class="sxs-lookup"><span data-stu-id="0813c-103">The [!INCLUDE[tsql](../../includes/tsql-md.md)] SET statement options STATISTICS TIME and STATISTICS IO are used to get information that aids in diagnosing long-running queries.</span></span> <span data-ttu-id="0813c-104">舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 也支援 SHOWPLAN 選項來分析查詢計畫。</span><span class="sxs-lookup"><span data-stu-id="0813c-104">Earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] also support the SHOWPLAN option for analyzing query plans.</span></span> <span data-ttu-id="0813c-105">ODBC 應用程式可以執行下列陳述式來設定這些選項：</span><span class="sxs-lookup"><span data-stu-id="0813c-105">An ODBC application can set these options by executing the following statements:</span></span>  
  
```  
SQLExecDirect(hstmt, "SET SHOWPLAN ON", SQL_NTS);  
SQLExecDirect(hstmt, "SET STATISTICS TIME ON", SQL_NTS90  
);  
SQLExecDirect(hstmt, "SET STATISTICS IO ON", SQL_NTS);  
```  
  
 <span data-ttu-id="0813c-106">當設定統計資料時間或設定執行程式表是 ON 時， **SQLExecute**和**SQLExecDirect**會傳回 SQL_SUCCESS_WITH_INFO，而此時，應用程式可以藉由呼叫**SQLGetDiagRec**來抓取顯示計畫或統計資料時間輸出，直到它傳回 SQL_NO_DATA 為止。</span><span class="sxs-lookup"><span data-stu-id="0813c-106">When SET STATISTICS TIME or SET SHOWPLAN are ON, **SQLExecute** and **SQLExecDirect** return SQL_SUCCESS_WITH_INFO, and, at that point, the application can retrieve the SHOWPLAN or STATISTICS TIME output by calling **SQLGetDiagRec** until it returns SQL_NO_DATA.</span></span> <span data-ttu-id="0813c-107">SHOWPLAN 資料的每一行都會以下列格式傳回：</span><span class="sxs-lookup"><span data-stu-id="0813c-107">Each line of SHOWPLAN data comes back in the format:</span></span>  
  
```  
szSqlState="01000", *pfNativeError=6223,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]   
              Table Scan"  
```  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="0813c-108">7.0 版會將 SHOWPLAN 選項取代成 SHOWPLAN_ALL 和 SHOWPLAN_TEXT，而且這兩個都會傳回輸出當做結果集，而且一組訊息。</span><span class="sxs-lookup"><span data-stu-id="0813c-108">version 7.0 replaced the SHOWPLAN option with SHOWPLAN_ALL and SHOWPLAN_TEXT, both of which return output as a result set, not a set of messages.</span></span>  
  
 <span data-ttu-id="0813c-109">STATISTICS TIME 資料的每一行都會以下列格式傳回：</span><span class="sxs-lookup"><span data-stu-id="0813c-109">Each line of STATISTICS TIME comes back in the format:</span></span>  
  
```  
szSqlState="01000", *pfNativeError= 3613,  
szErrorMsg="[Microsoft][SQL Server Native Client][SQL Server]  
   SQL Server Parse and Compile Time: cpu time = 0 ms."  
```  
  
 <span data-ttu-id="0813c-110">在結果集結束之前，不會提供 SET STATISTICS IO 的輸出。</span><span class="sxs-lookup"><span data-stu-id="0813c-110">The output of SET STATISTICS IO is not available until the end of a result set.</span></span> <span data-ttu-id="0813c-111">若要取得統計資料 IO 輸出，應用程式會在**SQLFetch**或[SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)傳回 SQL_NO_DATA 時呼叫**SQLGetDiagRec** 。</span><span class="sxs-lookup"><span data-stu-id="0813c-111">To get STATISTICS IO output, the application calls **SQLGetDiagRec** at the time **SQLFetch** or [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md) returns SQL_NO_DATA.</span></span> <span data-ttu-id="0813c-112">STATISTICS IO 的輸出會以下列格式傳回：</span><span class="sxs-lookup"><span data-stu-id="0813c-112">The output of STATISTICS IO comes back in the format:</span></span>  
  
```  
szSqlState="01000", *pfNativeError= 3615,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table: testshow  scan count 1,  logical reads: 1,  
   physical reads: 0."  
```  
  
## <a name="using-dbcc-statements"></a><span data-ttu-id="0813c-113">使用 DBCC 陳述式</span><span class="sxs-lookup"><span data-stu-id="0813c-113">Using DBCC Statements</span></span>  
 <span data-ttu-id="0813c-114">DBCC 陳述式會傳回其資料做為訊息，而非結果集。</span><span class="sxs-lookup"><span data-stu-id="0813c-114">DBCC statements return their data as messages, not result sets.</span></span> <span data-ttu-id="0813c-115">**SQLExecDirect**或**SQLExecute**會傳回 SQL_SUCCESS_WITH_INFO，而應用程式會藉由呼叫**SQLGetDiagRec**來抓取輸出，直到傳回 SQL_NO_DATA 為止。</span><span class="sxs-lookup"><span data-stu-id="0813c-115">**SQLExecDirect** or **SQLExecute** return SQL_SUCCESS_WITH_INFO, and the application retrieves the output by calling **SQLGetDiagRec** until it returns SQL_NO_DATA.</span></span>  
  
 <span data-ttu-id="0813c-116">例如，下列陳述式會傳回 SQL_SUCCESS_WITH_INFO：</span><span class="sxs-lookup"><span data-stu-id="0813c-116">For example, the following statement returns SQL_SUCCESS_WITH_INFO:</span></span>  
  
```  
SQLExecDirect(hstmt, "DBCC CHECKTABLE(Authors)", SQL_NTS);  
```  
  
 <span data-ttu-id="0813c-117">呼叫**SQLGetDiagRec**會傳回：</span><span class="sxs-lookup"><span data-stu-id="0813c-117">Calls to **SQLGetDiagRec** return:</span></span>  
  
```  
szSqlState = "01000", *pfNativeError = 2536,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Checking authors"  
szSqlState = "01000", *pfNativeError = 2579,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   The total number of data pages in this table is 1."  
szSqlState = "01000", *pfNativeError = 7929,  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   Table has 23 data rows."  
szSqlState = "01000", *pfNativeError = 2528  
szErrorMsg="[Microsoft][ SQL Server Native Client][SQL Server]  
   DBCC execution completed. If DBCC printed error messages,  
   see your System Administrator."  
```  
  
## <a name="using-print-and-raiserror-statements"></a><span data-ttu-id="0813c-118">使用 PRINT 和 RAISERROR 陳述式</span><span class="sxs-lookup"><span data-stu-id="0813c-118">Using PRINT and RAISERROR Statements</span></span>  
 [!INCLUDE[tsql](../../includes/tsql-md.md)]<span data-ttu-id="0813c-119">PRINT 和 RAISERROR 語句也會藉由呼叫**SQLGetDiagRec**來傳回資料。</span><span class="sxs-lookup"><span data-stu-id="0813c-119">PRINT and RAISERROR statements also return data by calling **SQLGetDiagRec**.</span></span> <span data-ttu-id="0813c-120">PRINT 語句會導致 SQL 語句執行傳回 SQL_SUCCESS_WITH_INFO，後續對**SQLGetDiagRec**的呼叫會傳回01000的*SQLState* 。</span><span class="sxs-lookup"><span data-stu-id="0813c-120">PRINT statements cause the SQL statement execution to return SQL_SUCCESS_WITH_INFO, and a subsequent call to **SQLGetDiagRec** returns a *SQLState* of 01000.</span></span> <span data-ttu-id="0813c-121">嚴重性為 10 或更低之 RAISERROR 陳述式的行為與 PRINT 相同。</span><span class="sxs-lookup"><span data-stu-id="0813c-121">A RAISERROR with a severity of ten or lower behaves the same as PRINT.</span></span> <span data-ttu-id="0813c-122">嚴重性為11或更高的 RAISERROR 會導致執行傳回 SQL_ERROR，而後續的**SQLGetDiagRec**呼叫會傳回*SQLState* 42000。</span><span class="sxs-lookup"><span data-stu-id="0813c-122">A RAISERROR with a severity of 11 or higher causes the execute to return SQL_ERROR, and a subsequent call to **SQLGetDiagRec** returns *SQLState* 42000.</span></span> <span data-ttu-id="0813c-123">例如，下列陳述式會傳回 SQL_SUCCESS_WITH_INFO：</span><span class="sxs-lookup"><span data-stu-id="0813c-123">For example, the following statement returns SQL_SUCCESS_WITH_INFO:</span></span>  
  
```  
SQLExecDirect (hstmt, "PRINT  'Some message' ", SQL_NTS);  
```  
  
 <span data-ttu-id="0813c-124">呼叫**SQLGetDiagRec**會傳回：</span><span class="sxs-lookup"><span data-stu-id="0813c-124">Calling **SQLGetDiagRec** returns:</span></span>  
  
```  
szSQLState = "01000", *pfNative Error = 0,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Some message"  
```  
  
 <span data-ttu-id="0813c-125">下列陳述式會傳回 SQL_SUCCESS_WITH_INFO：</span><span class="sxs-lookup"><span data-stu-id="0813c-125">The following statement returns SQL_SUCCESS_WITH_INFO:</span></span>  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 1.', 10, -1)",  
   SQL_NTS)  
```  
  
 <span data-ttu-id="0813c-126">呼叫**SQLGetDiagRec**會傳回：</span><span class="sxs-lookup"><span data-stu-id="0813c-126">Calling **SQLGetDiagRec** returns:</span></span>  
  
```  
szSQLState = "01000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 1."  
```  
  
 <span data-ttu-id="0813c-127">下列陳述式會傳回 SQL_ERROR：</span><span class="sxs-lookup"><span data-stu-id="0813c-127">The following statement returns SQL_ERROR:</span></span>  
  
```  
SQLExecDirect (hstmt, "RAISERROR ('Sample error 2.', 11, -1)", SQL_NTS)  
```  
  
 <span data-ttu-id="0813c-128">呼叫**SQLGetDiagRec**會傳回：</span><span class="sxs-lookup"><span data-stu-id="0813c-128">Calling **SQLGetDiagRec** returns:</span></span>  
  
```  
szSQLState = "42000", *pfNative Error = 50000,  
szErrorMsg= "[Microsoft] [SQL Server Native Client][SQL Server]  
   Sample error 2."  
```  
  
 <span data-ttu-id="0813c-129">當來自 PRINT 或 RAISERROR 語句的輸出包含在結果集中時，呼叫**SQLGetDiagRec**的時機很重要。</span><span class="sxs-lookup"><span data-stu-id="0813c-129">The timing of calling **SQLGetDiagRec** is critical when output from PRINT or RAISERROR statements is included in a result set.</span></span> <span data-ttu-id="0813c-130">**SQLGetDiagRec**用來抓取 PRINT 或 RAISERROR 輸出的呼叫，必須緊接在接收 SQL_ERROR 或 SQL_SUCCESS_WITH_INFO 的語句之後才進行。</span><span class="sxs-lookup"><span data-stu-id="0813c-130">The call to **SQLGetDiagRec** to retrieve the PRINT or RAISERROR output must be made immediately after the statement that receives SQL_ERROR or SQL_SUCCESS_WITH_INFO.</span></span> <span data-ttu-id="0813c-131">僅執行單一 SQL 陳述式時，這是相當直接的，如以上的範例所示。</span><span class="sxs-lookup"><span data-stu-id="0813c-131">This is straightforward when only a single SQL statement is executed, as in the examples above.</span></span> <span data-ttu-id="0813c-132">在這些情況下，呼叫**SQLExecDirect**或**SQLExecute**會傳回 SQL_ERROR 或 SQL_SUCCESS_WITH_INFO，然後可以呼叫**SQLGetDiagRec** 。</span><span class="sxs-lookup"><span data-stu-id="0813c-132">In these cases, the call to **SQLExecDirect** or **SQLExecute** returns SQL_ERROR or SQL_SUCCESS_WITH_INFO and **SQLGetDiagRec** can then be called.</span></span> <span data-ttu-id="0813c-133">當編碼使用迴圈處理 SQL 陳述式的批次輸出時，或執行 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預存程序時，比較不直接。</span><span class="sxs-lookup"><span data-stu-id="0813c-133">It is less straightforward when coding loops to handle the output of a batch of SQL statements or when executing [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures.</span></span>  
  
 <span data-ttu-id="0813c-134">在此情況下，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會針對批次或預存程序中執行的每個 SELECT 陳述式傳回一個結果集。</span><span class="sxs-lookup"><span data-stu-id="0813c-134">In this case, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] returns a result set for every SELECT statement executed in a batch or stored procedure.</span></span> <span data-ttu-id="0813c-135">如果批次或程序包含 PRINT 或 RAISERROR 陳述式，這些陳述式的輸出會與 SELECT 陳述式結果集交錯。</span><span class="sxs-lookup"><span data-stu-id="0813c-135">If the batch or procedure contains PRINT or RAISERROR statements, the output for these is interleaved with the SELECT statement result sets.</span></span> <span data-ttu-id="0813c-136">如果批次或程式中的第一個語句是 PRINT 或 RAISERROR，則**SQLExecute**或**SQLExecDirect**會傳回 SQL_SUCCESS_WITH_INFO 或 SQL_ERROR，而應用程式必須呼叫**SQLGetDiagRec** ，直到它傳回 SQL_NO_DATA 以取得列印或 RAISERROR 資訊為止。</span><span class="sxs-lookup"><span data-stu-id="0813c-136">If the first statement in the batch or procedure is a PRINT or RAISERROR, the **SQLExecute** or **SQLExecDirect** returns SQL_SUCCESS_WITH_INFO or SQL_ERROR, and the application needs to call **SQLGetDiagRec** until it returns SQL_NO_DATA to retrieve the PRINT or RAISERROR information.</span></span>  
  
 <span data-ttu-id="0813c-137">如果 PRINT 或 RAISERROR 語句在 SQL 語句 (（例如 SELECT 語句) ）之後，則在包含錯誤的結果集上[SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)位置時，就會傳回 PRINT 或 RAISERROR 資訊。</span><span class="sxs-lookup"><span data-stu-id="0813c-137">If the PRINT or RAISERROR statement comes after an SQL statement (such as a SELECT statement), then the PRINT or RAISERROR information is returned when [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md)positions on the result set containing the error.</span></span> <span data-ttu-id="0813c-138">**SQLMoreResults**會根據訊息的嚴重性傳回 SQL_SUCCESS_WITH_INFO 或 SQL_ERROR。</span><span class="sxs-lookup"><span data-stu-id="0813c-138">**SQLMoreResults** returns SQL_SUCCESS_WITH_INFO or SQL_ERROR depending on the severity of the message.</span></span> <span data-ttu-id="0813c-139">藉由呼叫**SQLGetDiagRec**來抓取訊息，直到傳回 SQL_NO_DATA 為止。</span><span class="sxs-lookup"><span data-stu-id="0813c-139">Messages are retrieved by calling **SQLGetDiagRec** until it returns SQL_NO_DATA.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0813c-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0813c-140">See Also</span></span>  
 [<span data-ttu-id="0813c-141">處理錯誤與訊息</span><span class="sxs-lookup"><span data-stu-id="0813c-141">Handling Errors and Messages</span></span>](handling-errors-and-messages.md)  
  
  
