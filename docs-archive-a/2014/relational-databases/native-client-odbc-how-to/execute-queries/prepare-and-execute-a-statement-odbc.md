---
title: 準備和執行 (ODBC) 的語句 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
- statement preparation
ms.assetid: 0adecc63-4da5-486c-bc48-09a004a2fae6
author: rothja
ms.author: jroth
ms.openlocfilehash: 607d8ad1509eca1204f6d029842b04120d3f5d9a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707490"
---
# <a name="prepare-and-execute-a-statement-odbc"></a><span data-ttu-id="88688-102">準備和執行陳述式 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="88688-102">Prepare and Execute a Statement (ODBC)</span></span>
    
### <a name="to-prepare-a-statement-once-and-then-execute-it-multiple-times"></a><span data-ttu-id="88688-103">準備一次陳述式，然後執行多次</span><span class="sxs-lookup"><span data-stu-id="88688-103">To prepare a statement once, and then execute it multiple times</span></span>  
  
1.  <span data-ttu-id="88688-104">呼叫[SQLPrepare 函數](https://go.microsoft.com/fwlink/?LinkId=59360)來準備語句。</span><span class="sxs-lookup"><span data-stu-id="88688-104">Call [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) to prepare the statement.</span></span>  
  
2.  <span data-ttu-id="88688-105">（選擇性）呼叫[SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404)來判斷準備語句中的參數數目。</span><span class="sxs-lookup"><span data-stu-id="88688-105">Optionally, call [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) to determine the number of parameters in the prepared statement.</span></span>  
  
3.  <span data-ttu-id="88688-106">(選擇性) 針對準備陳述式中的每個參數：</span><span class="sxs-lookup"><span data-stu-id="88688-106">Optionally, for each parameter in the prepared statement:</span></span>  
  
    -   <span data-ttu-id="88688-107">呼叫[SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md)以取得參數資訊。</span><span class="sxs-lookup"><span data-stu-id="88688-107">Call [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) to get parameter information.</span></span>  
  
    -   <span data-ttu-id="88688-108">使用[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md)，將每個參數系結至程式變數。</span><span class="sxs-lookup"><span data-stu-id="88688-108">Bind each parameter to a program variable by using [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md).</span></span> <span data-ttu-id="88688-109">設定任何資料執行中參數。</span><span class="sxs-lookup"><span data-stu-id="88688-109">Set up any data-at-execution parameters.</span></span>  
  
4.  <span data-ttu-id="88688-110">針對準備陳述式的每個執行：</span><span class="sxs-lookup"><span data-stu-id="88688-110">For each execution of a prepared statement:</span></span>  
  
    -   <span data-ttu-id="88688-111">如果陳述式具有參數標記，請將資料值放在繫結參數緩衝區中。</span><span class="sxs-lookup"><span data-stu-id="88688-111">If the statement has parameter markers, put the data values into the bound parameter buffer.</span></span>  
  
    -   <span data-ttu-id="88688-112">呼叫[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400)來執行備妥的語句。</span><span class="sxs-lookup"><span data-stu-id="88688-112">Call [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) to execute the prepared statement.</span></span>  
  
    -   <span data-ttu-id="88688-113">如果使用了資料執行中輸入參數， [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400)會傳回 SQL_NEED_DATA。</span><span class="sxs-lookup"><span data-stu-id="88688-113">If data-at-execution input parameters are used, [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) returns SQL_NEED_DATA.</span></span> <span data-ttu-id="88688-114">使用[SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405)和[SQLPutData](../../native-client-odbc-api/sqlputdata.md)以區區塊轉送資料。</span><span class="sxs-lookup"><span data-stu-id="88688-114">Send the data in chunks by using [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) and [SQLPutData](../../native-client-odbc-api/sqlputdata.md).</span></span>  
  
### <a name="to-prepare-a-statement-with-column-wise-parameter-binding"></a><span data-ttu-id="88688-115">準備含有資料行取向參數繫結的陳述式</span><span class="sxs-lookup"><span data-stu-id="88688-115">To prepare a statement with column-wise parameter binding</span></span>  
  
1.  <span data-ttu-id="88688-116">呼叫[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)以設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="88688-116">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
    -   <span data-ttu-id="88688-117">將 SQL_ATTR_PARAMSET_SIZE 設定為參數集 (S) 的數目。</span><span class="sxs-lookup"><span data-stu-id="88688-117">Set SQL_ATTR_PARAMSET_SIZE to the number of sets (S) of parameters.</span></span>  
  
    -   <span data-ttu-id="88688-118">將 SQL_ATTR_PARAM_BIND_TYPE 設定為 SQL_PARAMETER_BIND_BY_COLUMN。</span><span class="sxs-lookup"><span data-stu-id="88688-118">Set SQL_ATTR_PARAM_BIND_TYPE to SQL_PARAMETER_BIND_BY_COLUMN.</span></span>  
  
    -   <span data-ttu-id="88688-119">將 SQL_ATTR_PARAMS_PROCESSED_PTR 屬性設定為指向 SQLUINTEGER 變數，以保存已處理的參數數目。</span><span class="sxs-lookup"><span data-stu-id="88688-119">Set the SQL_ATTR_PARAMS_PROCESSED_PTR attribute to point to a SQLUINTEGER variable to hold the number of parameters processed.</span></span>  
  
    -   <span data-ttu-id="88688-120">將 SQL_ATTR_PARAMS_STATUS_PTR 設定為指向 SQLUSSMALLINT 變數的陣列[S]，以保存參數狀態指標。</span><span class="sxs-lookup"><span data-stu-id="88688-120">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[S] of SQLUSSMALLINT variables to hold parameter status indicators.</span></span>  
  
2.  <span data-ttu-id="88688-121">呼叫 SQLPrepare 以準備語句。</span><span class="sxs-lookup"><span data-stu-id="88688-121">Call SQLPrepare to prepare the statement.</span></span>  
  
3.  <span data-ttu-id="88688-122">（選擇性）呼叫[SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404)來判斷準備語句中的參數數目。</span><span class="sxs-lookup"><span data-stu-id="88688-122">Optionally, call [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) to determine the number of parameters in the prepared statement.</span></span>  
  
4.  <span data-ttu-id="88688-123">（選擇性）針對準備語句中的每個參數，呼叫 SQLDescribeParam 以取得參數資訊。</span><span class="sxs-lookup"><span data-stu-id="88688-123">Optionally, for each parameter in the prepared statement, call SQLDescribeParam to get parameter information.</span></span>  
  
5.  <span data-ttu-id="88688-124">針對每個參數標記：</span><span class="sxs-lookup"><span data-stu-id="88688-124">For each parameter marker:</span></span>  
  
    -   <span data-ttu-id="88688-125">配置 S 個參數緩衝區的陣列來儲存資料值。</span><span class="sxs-lookup"><span data-stu-id="88688-125">Allocate an array of S parameter buffers to store data values.</span></span>  
  
    -   <span data-ttu-id="88688-126">配置 S 個參數緩衝區的陣列來儲存資料長度。</span><span class="sxs-lookup"><span data-stu-id="88688-126">Allocate an array of S parameter buffers to store data lengths.</span></span>  
  
    -   <span data-ttu-id="88688-127">呼叫 SQLBindParameter，將參數資料值和資料長度陣列系結至語句參數。</span><span class="sxs-lookup"><span data-stu-id="88688-127">Call SQLBindParameter to bind the parameter data value and data length arrays to the statement parameter.</span></span>  
  
    -   <span data-ttu-id="88688-128">如果參數是資料執行中的 text 或 image 參數，請設定此參數。</span><span class="sxs-lookup"><span data-stu-id="88688-128">If the parameter is a data-at-execution text or image parameter, set it up.</span></span>  
  
    -   <span data-ttu-id="88688-129">如果使用了任何資料執行中參數，請設定這些參數。</span><span class="sxs-lookup"><span data-stu-id="88688-129">If any data-at-execution parameters are used, set them up.</span></span>  
  
6.  <span data-ttu-id="88688-130">針對準備陳述式的每個執行：</span><span class="sxs-lookup"><span data-stu-id="88688-130">For each execution of a prepared statement:</span></span>  
  
    -   <span data-ttu-id="88688-131">將 S 資料值和 S 資料長度放在繫結參數陣列中。</span><span class="sxs-lookup"><span data-stu-id="88688-131">Put the S data values and S data lengths into the bound parameter arrays.</span></span>  
  
    -   <span data-ttu-id="88688-132">呼叫 SQLExecute，以便執行準備陳述式。</span><span class="sxs-lookup"><span data-stu-id="88688-132">Call SQLExecute to execute the prepared statement.</span></span>  
  
    -   <span data-ttu-id="88688-133">如果使用了資料執行中輸入參數，SQLExecute 就會傳回 SQL_NEED_DATA。</span><span class="sxs-lookup"><span data-stu-id="88688-133">If data-at-execution input parameters are used, SQLExecute returns SQL_NEED_DATA.</span></span> <span data-ttu-id="88688-134">使用 SQLParamData 和 SQLPutData 以區區塊轉送資料。</span><span class="sxs-lookup"><span data-stu-id="88688-134">Send the data in chunks by using SQLParamData and SQLPutData.</span></span>  
  
### <a name="to-prepare-a-statement-with-row-wise-bound-parameters"></a><span data-ttu-id="88688-135">準備含有資料列取向繫結參數的陳述式</span><span class="sxs-lookup"><span data-stu-id="88688-135">To prepare a statement with row-wise bound parameters</span></span>  
  
1.  <span data-ttu-id="88688-136">配置結構的陣列[S]，其中 S 是參數集的數目。</span><span class="sxs-lookup"><span data-stu-id="88688-136">Allocate an array[S] of structures, where S is the number of sets of parameters.</span></span> <span data-ttu-id="88688-137">結構中每個參數都具有一個元素，而每個元素則具有兩部分：</span><span class="sxs-lookup"><span data-stu-id="88688-137">The structure has one element for each parameter, and each element has two parts:</span></span>  
  
    -   <span data-ttu-id="88688-138">第一個部分是適當資料類型的變數，可保存參數資料。</span><span class="sxs-lookup"><span data-stu-id="88688-138">The first part is a variable of the appropriate data type to hold the parameter data.</span></span>  
  
    -   <span data-ttu-id="88688-139">第二個部分是 SQLINTEGER 變數，可保存狀態指標。</span><span class="sxs-lookup"><span data-stu-id="88688-139">The second part is a SQLINTEGER variable to hold the status indicator.</span></span>  
  
2.  <span data-ttu-id="88688-140">呼叫[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)以設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="88688-140">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
    -   <span data-ttu-id="88688-141">將 SQL_ATTR_PARAMSET_SIZE 設定為參數集 (S) 的數目。</span><span class="sxs-lookup"><span data-stu-id="88688-141">Set SQL_ATTR_PARAMSET_SIZE to the number of sets (S) of parameters.</span></span>  
  
    -   <span data-ttu-id="88688-142">將 SQL_ATTR_PARAM_BIND_TYPE 設定為步驟 1 中配置的結構大小。</span><span class="sxs-lookup"><span data-stu-id="88688-142">Set SQL_ATTR_PARAM_BIND_TYPE to the size of the structure allocated in Step 1.</span></span>  
  
    -   <span data-ttu-id="88688-143">將 SQL_ATTR_PARAMS_PROCESSED_PTR 屬性設定為指向 SQLUINTEGER 變數，以保存已處理的參數數目。</span><span class="sxs-lookup"><span data-stu-id="88688-143">Set the SQL_ATTR_PARAMS_PROCESSED_PTR attribute to point to a SQLUINTEGER variable to hold the number of parameters processed.</span></span>  
  
    -   <span data-ttu-id="88688-144">將 SQL_ATTR_PARAMS_STATUS_PTR 設定為指向 SQLUSSMALLINT 變數的陣列[S]，以保存參數狀態指標。</span><span class="sxs-lookup"><span data-stu-id="88688-144">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[S] of SQLUSSMALLINT variables to hold parameter status indicators.</span></span>  
  
3.  <span data-ttu-id="88688-145">呼叫 SQLPrepare 以準備語句。</span><span class="sxs-lookup"><span data-stu-id="88688-145">Call SQLPrepare to prepare the statement.</span></span>  
  
4.  <span data-ttu-id="88688-146">針對每個參數標記，呼叫 SQLBindParameter，將參數資料值和資料長度指標指向其在步驟1所配置之結構陣列第一個元素中的變數。</span><span class="sxs-lookup"><span data-stu-id="88688-146">For each parameter marker, call SQLBindParameter to point the parameter data value and data length pointer to their variables in the first element of the array of structures allocated in Step 1.</span></span> <span data-ttu-id="88688-147">如果參數是資料執行中參數，請設定此參數。</span><span class="sxs-lookup"><span data-stu-id="88688-147">If the parameter is a data-at-execution parameter, set it up.</span></span>  
  
5.  <span data-ttu-id="88688-148">針對準備陳述式的每個執行：</span><span class="sxs-lookup"><span data-stu-id="88688-148">For each execution of a prepared statement:</span></span>  
  
    -   <span data-ttu-id="88688-149">將資料值填入繫結參數緩衝區陣列。</span><span class="sxs-lookup"><span data-stu-id="88688-149">Fill the bound parameter buffer array with data values.</span></span>  
  
    -   <span data-ttu-id="88688-150">呼叫 SQLExecute，以便執行準備陳述式。</span><span class="sxs-lookup"><span data-stu-id="88688-150">Call SQLExecute to execute the prepared statement.</span></span> <span data-ttu-id="88688-151">驅動程式會有效率地執行 SQL 陳述式 S 次，針對每個參數集執行一次。</span><span class="sxs-lookup"><span data-stu-id="88688-151">The driver efficiently executes the SQL statement S times, once for each set of parameters.</span></span>  
  
    -   <span data-ttu-id="88688-152">如果使用了資料執行中輸入參數，SQLExecute 就會傳回 SQL_NEED_DATA。</span><span class="sxs-lookup"><span data-stu-id="88688-152">If data-at-execution input parameters are used, SQLExecute returns SQL_NEED_DATA.</span></span> <span data-ttu-id="88688-153">使用 SQLParamData 和 SQLPutData 以區區塊轉送資料。</span><span class="sxs-lookup"><span data-stu-id="88688-153">Send the data in chunks by using SQLParamData and SQLPutData.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88688-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="88688-154">See Also</span></span>  
 [<span data-ttu-id="88688-155">執行查詢 &#40;ODBC&#41;的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="88688-155">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](executing-queries-how-to-topics-odbc.md)  
  
  
