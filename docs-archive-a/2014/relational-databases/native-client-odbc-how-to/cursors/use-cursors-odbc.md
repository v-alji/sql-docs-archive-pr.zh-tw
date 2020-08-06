---
title: 使用 ODBC)  (的資料指標 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], how to topics
ms.assetid: c502736f-bca0-45c3-ae25-d2ad52d296bf
author: rothja
ms.author: jroth
ms.openlocfilehash: e08156b03407c7a05d86278c11482a568d651f5f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584473"
---
# <a name="use-cursors-odbc"></a><span data-ttu-id="e32d1-102">使用資料指標 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="e32d1-102">Use Cursors (ODBC)</span></span>
    
### <a name="to-use-cursors"></a><span data-ttu-id="e32d1-103">使用資料指標</span><span class="sxs-lookup"><span data-stu-id="e32d1-103">To use cursors</span></span>  
  
1.  <span data-ttu-id="e32d1-104">呼叫 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 來設定所需的資料指標屬性：</span><span class="sxs-lookup"><span data-stu-id="e32d1-104">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the desired cursor attributes:</span></span>  
  
     <span data-ttu-id="e32d1-105">設定 SQL_ATTR_CURSOR_TYPE 和 SQL_ATTR_CONCURRENCY 屬性 (這是慣用的選項)。</span><span class="sxs-lookup"><span data-stu-id="e32d1-105">Set the SQL_ATTR_CURSOR_TYPE and SQL_ATTR_CONCURRENCY attributes (this is the preferred option).</span></span>  
  
     <span data-ttu-id="e32d1-106">或者</span><span class="sxs-lookup"><span data-stu-id="e32d1-106">Or</span></span>  
  
     <span data-ttu-id="e32d1-107">設定 SQL_CURSOR_SCROLLABLE 和 SQL_CURSOR_SENSITIVITY 屬性。</span><span class="sxs-lookup"><span data-stu-id="e32d1-107">Set the SQL_CURSOR_SCROLLABLE and SQL_CURSOR_SENSITIVITY attributes.</span></span>  
  
2.  <span data-ttu-id="e32d1-108">使用 SQL_ATTR_ROW_ARRAY_SIZE 屬性呼叫 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 來設定資料列集大小。</span><span class="sxs-lookup"><span data-stu-id="e32d1-108">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the rowset size by using the SQL_ATTR_ROW_ARRAY_SIZE attribute.</span></span>  
  
3.  <span data-ttu-id="e32d1-109">如果使用 WHERE CURRENT OF 子句完成定點更新，可以選擇呼叫 [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) 來設定資料指標名稱。</span><span class="sxs-lookup"><span data-stu-id="e32d1-109">Optionally, call [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) to set a cursor name if positioned updates will be done by using the WHERE CURRENT OF clause.</span></span>  
  
4.  <span data-ttu-id="e32d1-110">執行 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="e32d1-110">Execute the SQL statement.</span></span>  
  
5.  <span data-ttu-id="e32d1-111">如果使用 WHERE CURRENT OF 子句完成定點更新，而且資料指標名稱沒有隨步驟 3 中的 [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) 提供，可以選擇呼叫 [SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md) 來設定資料指標名稱。</span><span class="sxs-lookup"><span data-stu-id="e32d1-111">Optionally, call [SQLGetCursorName](../../native-client-odbc-api/sqlgetcursorname.md) to get the cursor name if positioned updates will be done by using the WHERE CURRENT OF clause and a cursor name was not supplied with [SQLSetCursorName](https://go.microsoft.com/fwlink/?LinkId=58406) in Step 3.</span></span>  
  
6.  <span data-ttu-id="e32d1-112">呼叫 [SQLNumResultCols](../../native-client-odbc-api/sqlnumresultcols.md) 來取得資料列集中的資料行 (C) 數目。</span><span class="sxs-lookup"><span data-stu-id="e32d1-112">Call [SQLNumResultCols](../../native-client-odbc-api/sqlnumresultcols.md) to get the number of columns (C) in the rowset.</span></span>  
  
     <span data-ttu-id="e32d1-113">使用資料行取向的繫結。</span><span class="sxs-lookup"><span data-stu-id="e32d1-113">Use column-wise binding.</span></span>  
  
     <span data-ttu-id="e32d1-114">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="e32d1-114">\- or -</span></span>  
  
     <span data-ttu-id="e32d1-115">使用資料列取向的繫結。</span><span class="sxs-lookup"><span data-stu-id="e32d1-115">Use row-wise binding.</span></span>  
  
7.  <span data-ttu-id="e32d1-116">視需要，從資料指標提取資料列集。</span><span class="sxs-lookup"><span data-stu-id="e32d1-116">Fetch rowsets from the cursor as desired.</span></span>  
  
8.  <span data-ttu-id="e32d1-117">呼叫 [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) 來判斷是否有其他結果集可用。</span><span class="sxs-lookup"><span data-stu-id="e32d1-117">Call [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) to determine if another result set is available.</span></span>  
  
    -   <span data-ttu-id="e32d1-118">如果該函數傳回 SQL_SUCCESS，表示有其他可用的結果集。</span><span class="sxs-lookup"><span data-stu-id="e32d1-118">If it returns SQL_SUCCESS, another result set is available.</span></span>  
  
    -   <span data-ttu-id="e32d1-119">如果該函數傳回 SQL_NO_DATA，表示沒有其他可用的結果集。</span><span class="sxs-lookup"><span data-stu-id="e32d1-119">If it returns SQL_NO_DATA, no more result sets are available.</span></span>  
  
    -   <span data-ttu-id="e32d1-120">如果該函數傳回 SQL_SUCCESS_WITH_INFO 或 SQL_ERROR，請呼叫 [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) 來判斷是否可以使用來自 PRINT 或 RAISERROR 陳述式的輸出。</span><span class="sxs-lookup"><span data-stu-id="e32d1-120">If it returns SQL_SUCCESS_WITH_INFO or SQL_ERROR, call [SQLGetDiagRec](https://go.microsoft.com/fwlink/?LinkId=58402) to determine if the output from a PRINT or RAISERROR statement is available.</span></span>  
  
     <span data-ttu-id="e32d1-121">如果繫結陳述式參數用於預存程序的輸出參數或傳回值，請使用繫結參數緩衝區中目前可用的資料。</span><span class="sxs-lookup"><span data-stu-id="e32d1-121">If bound statement parameters are used for output parameters or the return value of a stored procedure, use the data now available in the bound parameter buffers.</span></span>  
  
     <span data-ttu-id="e32d1-122">在使用繫結參數時，每個 [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) 或 [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) 呼叫都會執行 SQL 陳述式 S 次，其中 S 是繫結參數陣列中的元素數。</span><span class="sxs-lookup"><span data-stu-id="e32d1-122">When bound parameters are used, each call to [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) or [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) will have executed the SQL statement S times, where S is the number of elements in the array of bound parameters.</span></span> <span data-ttu-id="e32d1-123">這代表將要處理 S 個結果集，其中每個結果集都是由 SQL 陳述式的單一執行通常會傳回的結果集、輸出參數和傳回碼等所有項目而組成。</span><span class="sxs-lookup"><span data-stu-id="e32d1-123">This means that there will be S sets of results to process, where each set of results comprises all of the result sets, output parameters, and return codes usually returned by a single execution of the SQL statement.</span></span>  
  
     <span data-ttu-id="e32d1-124">請注意，當結果集包含計算資料列時，每個計算資料列都可以提供為個別的結果集。</span><span class="sxs-lookup"><span data-stu-id="e32d1-124">Note that when a result set contains compute rows, each compute row is made available as a separate result set.</span></span> <span data-ttu-id="e32d1-125">這些計算結果集會散佈在一般的資料列內，將一般的資料列分隔成多個結果集。</span><span class="sxs-lookup"><span data-stu-id="e32d1-125">These compute result sets are interspersed within the normal rows and break normal rows into multiple result sets.</span></span>  
  
9. <span data-ttu-id="e32d1-126">您可以選擇使用 SQL_UNBIND 呼叫 [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)，以釋放任何繫結的資料行緩衝區。</span><span class="sxs-lookup"><span data-stu-id="e32d1-126">Optionally, call [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) with SQL_UNBIND to release any bound column buffers.</span></span>  
  
10. <span data-ttu-id="e32d1-127">如果有其他可用的結果集，請到步驟 6。</span><span class="sxs-lookup"><span data-stu-id="e32d1-127">If another result set is available, go to Step 6.</span></span>  
  
     <span data-ttu-id="e32d1-128">在步驟 9 中，呼叫部分處理之結果集上的 [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) 會清除結果集的其餘部分。</span><span class="sxs-lookup"><span data-stu-id="e32d1-128">In Step 9, calling [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) on a partially processed result set clears the remainder of the result set.</span></span> <span data-ttu-id="e32d1-129">清除部分處理之結果集的另一個方式為，呼叫 [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md)。</span><span class="sxs-lookup"><span data-stu-id="e32d1-129">Another way to clear a partially processed result set is to call [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md).</span></span>  
  
     <span data-ttu-id="e32d1-130">您可以透過設定 SQL_ATTR_CURSOR_TYPE 和 SQL_ATTR_CONCURRENCY，或是設定 SQL_ATTR_CURSOR_SENSITIVITY 和 SQL_ATTR_CURSOR_SCROLLABLE，控制所使用的資料指標類型。</span><span class="sxs-lookup"><span data-stu-id="e32d1-130">You can control the type of cursor used by setting either SQL_ATTR_CURSOR_TYPE and SQL_ATTR_CONCURRENCY, or by setting SQL_ATTR_CURSOR_SENSITIVITY and SQL_ATTR_CURSOR_SCROLLABLE.</span></span> <span data-ttu-id="e32d1-131">您不應該混合使用這兩種指定資料指標行為的方法。</span><span class="sxs-lookup"><span data-stu-id="e32d1-131">You should not mix the two methods of specifying cursor behavior.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e32d1-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e32d1-132">See Also</span></span>  
 [<span data-ttu-id="e32d1-133">使用資料指標的 how to 主題 &#40;ODBC&#41;</span><span class="sxs-lookup"><span data-stu-id="e32d1-133">Using Cursors How-to Topics &#40;ODBC&#41;</span></span>](using-cursors-how-to-topics-odbc.md)  
  
  
