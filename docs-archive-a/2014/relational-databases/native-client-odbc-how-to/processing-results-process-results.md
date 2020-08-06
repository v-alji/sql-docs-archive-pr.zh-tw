---
title: " (ODBC) 處理結果 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- processing results [ODBC]
ms.assetid: 4810fe3f-78ee-4f0d-8bcc-a4659fbcf46f
author: rothja
ms.author: jroth
ms.openlocfilehash: 8a22e9d7280f88de7799c31d2d0611e5299043d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706438"
---
# <a name="process-results-odbc"></a><span data-ttu-id="9cea8-102">處理結果 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="9cea8-102">Process Results (ODBC)</span></span>
    
### <a name="to-process-results"></a><span data-ttu-id="9cea8-103">處理結果</span><span class="sxs-lookup"><span data-stu-id="9cea8-103">To process results</span></span>  
  
1.  <span data-ttu-id="9cea8-104">擷取結果集資訊。</span><span class="sxs-lookup"><span data-stu-id="9cea8-104">Retrieve result set information.</span></span>  
  
2.  <span data-ttu-id="9cea8-105">如果使用繫結資料行，則針對您要繫結到的每個資料行呼叫 [SQLBindCol](../native-client-odbc-api/sqlbindcol.md)，將程式緩衝區繫結到該資料行。</span><span class="sxs-lookup"><span data-stu-id="9cea8-105">If bound columns are used, for each column you want to bind to, call [SQLBindCol](../native-client-odbc-api/sqlbindcol.md) to bind a program buffer to the column.</span></span>  
  
3.  <span data-ttu-id="9cea8-106">針對結果集中的每個資料列：</span><span class="sxs-lookup"><span data-stu-id="9cea8-106">For each row in the result set:</span></span>  
  
    -   <span data-ttu-id="9cea8-107">呼叫 [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) 以取得下一個資料列。</span><span class="sxs-lookup"><span data-stu-id="9cea8-107">Call [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) to get the next row.</span></span>  
  
    -   <span data-ttu-id="9cea8-108">如果是使用繫結資料行，請使用繫結資料行緩衝區中目前可用的資料。</span><span class="sxs-lookup"><span data-stu-id="9cea8-108">If bound columns are used, use the data now available in the bound column buffers.</span></span>  
  
    -   <span data-ttu-id="9cea8-109">如果是使用未繫結資料行，請呼叫 [SQLGetData](../native-client-odbc-api/sqlgetdata.md) 一或多次，以取得最後一個繫結資料行之後未繫結資料行的資料。</span><span class="sxs-lookup"><span data-stu-id="9cea8-109">If unbound columns are used, call [SQLGetData](../native-client-odbc-api/sqlgetdata.md) one or more times to get the data for unbound columns after the last bound column.</span></span> <span data-ttu-id="9cea8-110">對 `SQLGetData` 的呼叫應該以資料行號碼的遞增順序進行。</span><span class="sxs-lookup"><span data-stu-id="9cea8-110">Calls to `SQLGetData` should be in increasing order of column number.</span></span>  
  
    -   <span data-ttu-id="9cea8-111">呼叫 `SQLGetData` 多次，以便從 text 或 image 資料行取得資料。</span><span class="sxs-lookup"><span data-stu-id="9cea8-111">Call `SQLGetData` multiple times to get data from a text or image column.</span></span>  
  
4.  <span data-ttu-id="9cea8-112">當 [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) 藉由傳回 SQL_NO_DATA 來表示達到結果集的結尾時，請呼叫 [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) 來判斷是否仍有其他的結果集可以使用。</span><span class="sxs-lookup"><span data-stu-id="9cea8-112">When [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) signals the end of the result set by returning SQL_NO_DATA, call [SQLMoreResults](../native-client-odbc-api/sqlmoreresults.md) to determine if another result set is available.</span></span>  
  
    -   <span data-ttu-id="9cea8-113">如果該函數傳回 SQL_SUCCESS，表示有其他可用的結果集。</span><span class="sxs-lookup"><span data-stu-id="9cea8-113">If it returns SQL_SUCCESS, another result set is available.</span></span>  
  
    -   <span data-ttu-id="9cea8-114">如果該函數傳回 SQL_NO_DATA，表示沒有其他可用的結果集。</span><span class="sxs-lookup"><span data-stu-id="9cea8-114">If it returns SQL_NO_DATA, no more result sets are available.</span></span>  
  
    -   <span data-ttu-id="9cea8-115">如果該函數傳回 SQL_SUCCESS_WITH_INFO 或 SQL_ERROR，請呼叫 [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) 來判斷是否可以使用來自 PRINT 或 RAISERROR 陳述式的輸出。</span><span class="sxs-lookup"><span data-stu-id="9cea8-115">If it returns SQL_SUCCESS_WITH_INFO or SQL_ERROR, call [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) to determine if the output from a PRINT or RAISERROR statement is available.</span></span>  
  
         <span data-ttu-id="9cea8-116">如果繫結陳述式參數用於預存程序的輸出參數或傳回值，請使用繫結參數緩衝區中目前可用的資料。</span><span class="sxs-lookup"><span data-stu-id="9cea8-116">If bound statement parameters are used for output parameters or the return value of a stored procedure, use the data now available in the bound parameter buffers.</span></span> <span data-ttu-id="9cea8-117">此外，在使用繫結參數時，每個 [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) 或 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) 呼叫都會執行 SQL 陳述式 *S* 次，其中 *S* 是繫結參數陣列中的元素數。</span><span class="sxs-lookup"><span data-stu-id="9cea8-117">Also, when bound parameters are used, each call to [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) or [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) will have executed the SQL statement *S* times, where *S* is the number of elements in the array of bound parameters.</span></span> <span data-ttu-id="9cea8-118">這代表將要處理 *S* 個結果集，其中每個結果集都是由 SQL 陳述式的單一執行通常會傳回的結果集、輸出參數和傳回碼等所有項目而組成。</span><span class="sxs-lookup"><span data-stu-id="9cea8-118">This means that there will be *S* sets of results to process, where each set of results comprises all of the result sets, output parameters, and return codes usually returned by a single execution of the SQL statement.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="9cea8-119">當結果集包含計算資料列時，每個計算資料列都可以提供為個別的結果集。</span><span class="sxs-lookup"><span data-stu-id="9cea8-119">When a result set contains compute rows, each compute row is made available as a separate result set.</span></span> <span data-ttu-id="9cea8-120">這些計算結果集會散佈在一般的資料列內，將一般的資料列分隔成多個結果集。</span><span class="sxs-lookup"><span data-stu-id="9cea8-120">These compute result sets are interspersed within the normal rows and break normal rows into multiple result sets.</span></span>  
  
5.  <span data-ttu-id="9cea8-121">您可以選擇使用 SQL_UNBIND 呼叫 [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md)，以釋放任何繫結的資料行緩衝區。</span><span class="sxs-lookup"><span data-stu-id="9cea8-121">Optionally, call [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) with SQL_UNBIND to release any bound column buffers.</span></span>  
  
6.  <span data-ttu-id="9cea8-122">如果有其他可用的結果集，請到步驟 1。</span><span class="sxs-lookup"><span data-stu-id="9cea8-122">If another result set is available, go to Step 1.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9cea8-123">若要在 [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) 傳回 SQL_NO_DATA 之前取消結果集的處理，請呼叫 [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md)。</span><span class="sxs-lookup"><span data-stu-id="9cea8-123">To cancel processing a result set before [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) returns SQL_NO_DATA, call [SQLCloseCursor](../native-client-odbc-api/sqlclosecursor.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cea8-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9cea8-124">See Also</span></span>  
 [<span data-ttu-id="9cea8-125">處理結果如何 &#40;ODBC&#41;的 how to 主題</span><span class="sxs-lookup"><span data-stu-id="9cea8-125">Processing Results How-to Topics &#40;ODBC&#41;</span></span>](../../database-engine/dev-guide/processing-results-how-to-topics-odbc.md)  
  
  
