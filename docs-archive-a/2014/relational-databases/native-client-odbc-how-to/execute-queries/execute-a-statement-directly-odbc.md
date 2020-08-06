---
title: 直接 (ODBC) 執行語句 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statement execution
ms.assetid: b690f9de-66e1-4ee5-ab6a-121346fb5f85
author: rothja
ms.author: jroth
ms.openlocfilehash: 2aeada906a925cff93455ffd92e7c17822a80124
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584466"
---
# <a name="execute-a-statement-directly-odbc"></a><span data-ttu-id="7c1ec-102">直接執行陳述式 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="7c1ec-102">Execute a Statement Directly (ODBC)</span></span>
    
### <a name="to-execute-a-statement-directly-and-one-time-only"></a><span data-ttu-id="7c1ec-103">直接並且僅一次執行陳述式</span><span class="sxs-lookup"><span data-stu-id="7c1ec-103">To execute a statement directly and one time only</span></span>  
  
1.  <span data-ttu-id="7c1ec-104">如果語句具有參數標記，請使用[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md)將每個參數系結至程式變數。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-104">If the statement has parameter markers, use [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) to bind each parameter to a program variable.</span></span> <span data-ttu-id="7c1ec-105">使用資料值填入程式變數，然後設定任何資料執行中 (data-at-execution) 參數。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-105">Fill the program variables with data values, and then set up any data-at-execution parameters.</span></span>  
  
2.  <span data-ttu-id="7c1ec-106">呼叫[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)以執行語句。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-106">Call [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) to execute the statement.</span></span>  
  
3.  <span data-ttu-id="7c1ec-107">如果使用了資料執行中輸入參數， [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)會傳回 SQL_NEED_DATA。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-107">If data-at-execution input parameters are used, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) returns SQL_NEED_DATA.</span></span> <span data-ttu-id="7c1ec-108">使用[SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405)和[SQLPutData](../../native-client-odbc-api/sqlputdata.md)以區區塊轉送資料。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-108">Send the data in chunks by using [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) and [SQLPutData](../../native-client-odbc-api/sqlputdata.md).</span></span>  
  
### <a name="to-execute-a-statement-multiple-times-by-using-column-wise-parameter-binding"></a><span data-ttu-id="7c1ec-109">使用資料行取向的參數繫結多次執行陳述式</span><span class="sxs-lookup"><span data-stu-id="7c1ec-109">To execute a statement multiple times by using column-wise parameter binding</span></span>  
  
1.  <span data-ttu-id="7c1ec-110">呼叫[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)以設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="7c1ec-110">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
     <span data-ttu-id="7c1ec-111">將 SQL_ATTR_PARAMSET_SIZE 設定為參數集 (S) 的數目。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-111">Set SQL_ATTR_PARAMSET_SIZE to the number of sets (S) of parameters.</span></span>  
  
     <span data-ttu-id="7c1ec-112">將 SQL_ATTR_PARAM_BIND_TYPE 設定為 SQL_PARAMETER_BIND_BY_COLUMN。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-112">Set SQL_ATTR_PARAM_BIND_TYPE to SQL_PARAMETER_BIND_BY_COLUMN.</span></span>  
  
     <span data-ttu-id="7c1ec-113">將 SQL_ATTR_PARAMS_PROCESSED_PTR 屬性設定為指向 SQLUINTEGER 變數，以保存已處理的參數數目。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-113">Set the SQL_ATTR_PARAMS_PROCESSED_PTR attribute to point to a SQLUINTEGER variable to hold the number of parameters processed.</span></span>  
  
     <span data-ttu-id="7c1ec-114">將 SQL_ATTR_PARAMS_STATUS_PTR 設定為指向 SQLUSSMALLINT 變數的陣列[S]，以保存參數狀態指標。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-114">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[S] of SQLUSSMALLINT variables to hold the parameter status indicators.</span></span>  
  
2.  <span data-ttu-id="7c1ec-115">針對每個參數標記：</span><span class="sxs-lookup"><span data-stu-id="7c1ec-115">For each parameter marker:</span></span>  
  
     <span data-ttu-id="7c1ec-116">配置 S 個參數緩衝區的陣列來儲存資料值。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-116">Allocate an array of S parameter buffers to store data values.</span></span>  
  
     <span data-ttu-id="7c1ec-117">配置 S 個參數緩衝區的陣列來儲存資料長度。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-117">Allocate an array of S parameter buffers to store data lengths.</span></span>  
  
     <span data-ttu-id="7c1ec-118">呼叫[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) ，將參數資料值和資料長度陣列系結至語句參數。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-118">Call [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) to bind the parameter data value and data length arrays to the statement parameter.</span></span>  
  
     <span data-ttu-id="7c1ec-119">設定任何資料執行中的 text 或 image 參數。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-119">Set up any data-at-execution text or image parameters.</span></span>  
  
     <span data-ttu-id="7c1ec-120">將 S 資料值和 S 資料長度放在繫結參數陣列中。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-120">Put S data values and S data lengths into the bound parameter arrays.</span></span>  
  
3.  <span data-ttu-id="7c1ec-121">呼叫[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)以執行語句。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-121">Call [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) to execute the statement.</span></span> <span data-ttu-id="7c1ec-122">驅動程式會有效率地執行陳述式 S 次，針對每個參數集執行一次。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-122">The driver efficiently executes the statement S times, once for each set of parameters.</span></span>  
  
4.  <span data-ttu-id="7c1ec-123">如果使用了資料執行中輸入參數， [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)會傳回 SQL_NEED_DATA。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-123">If data-at-execution input parameters are used, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) returns SQL_NEED_DATA.</span></span> <span data-ttu-id="7c1ec-124">使用[SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405)和[SQLPutData](../../native-client-odbc-api/sqlputdata.md)以區區塊轉送資料。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-124">Send the data in chunks by using [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) and [SQLPutData](../../native-client-odbc-api/sqlputdata.md).</span></span>  
  
### <a name="to-execute-a-statement-multiple-times-by-using-row-wise-parameter-binding"></a><span data-ttu-id="7c1ec-125">使用資料列取向的參數繫結多次執行陳述式</span><span class="sxs-lookup"><span data-stu-id="7c1ec-125">To execute a statement multiple times by using row-wise parameter binding</span></span>  
  
1.  <span data-ttu-id="7c1ec-126">配置結構的陣列[S]，其中 S 是參數集的數目。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-126">Allocate an array[S] of structures, where S is the number of sets of parameters.</span></span> <span data-ttu-id="7c1ec-127">結構中每個參數都具有一個元素，而每個元素則具有兩部分：</span><span class="sxs-lookup"><span data-stu-id="7c1ec-127">The structure has one element for each parameter, and each element has two parts:</span></span>  
  
     <span data-ttu-id="7c1ec-128">第一個部分是適當資料類型的變數，可保存參數資料。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-128">The first part is a variable of the appropriate data type to hold the parameter data.</span></span>  
  
     <span data-ttu-id="7c1ec-129">第二個部分是 SQLINTEGER 變數，可保存狀態指標。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-129">The second part is a SQLINTEGER variable to hold the status indicator.</span></span>  
  
2.  <span data-ttu-id="7c1ec-130">呼叫[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)以設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="7c1ec-130">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
     <span data-ttu-id="7c1ec-131">將 SQL_ATTR_PARAMSET_SIZE 設定為參數集 (S) 的數目。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-131">Set SQL_ATTR_PARAMSET_SIZE to the number of sets (S) of parameters.</span></span>  
  
     <span data-ttu-id="7c1ec-132">將 SQL_ATTR_PARAM_BIND_TYPE 設定為步驟 1 中配置的結構大小。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-132">Set SQL_ATTR_PARAM_BIND_TYPE to the size of the structure allocated in Step 1.</span></span>  
  
     <span data-ttu-id="7c1ec-133">將 SQL_ATTR_PARAMS_PROCESSED_PTR 屬性設定為指向 SQLUINTEGER 變數，以保存已處理的參數數目。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-133">Set the SQL_ATTR_PARAMS_PROCESSED_PTR attribute to point to a SQLUINTEGER variable to hold the number of parameters processed.</span></span>  
  
     <span data-ttu-id="7c1ec-134">將 SQL_ATTR_PARAMS_STATUS_PTR 設定為指向 SQLUSSMALLINT 變數的陣列[S]，以保存參數狀態指標。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-134">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[S] of SQLUSSMALLINT variables to hold the parameter status indicators.</span></span>  
  
3.  <span data-ttu-id="7c1ec-135">針對每個參數標記，呼叫[SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) ，將參數的資料值和資料長度指標指向其在步驟1所配置之結構陣列第一個元素中的變數。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-135">For each parameter marker, call [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) to point the parameter's data value and data length pointer to their variables in the first element of the array of structures allocated in Step 1.</span></span> <span data-ttu-id="7c1ec-136">如果參數是資料執行中參數，請設定此參數。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-136">If the parameter is a data-at-execution parameter, set it up.</span></span>  
  
4.  <span data-ttu-id="7c1ec-137">將資料值填入繫結參數緩衝區陣列。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-137">Fill the bound parameter buffer array with data values.</span></span>  
  
5.  <span data-ttu-id="7c1ec-138">呼叫[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)以執行語句。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-138">Call [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) to execute the statement.</span></span> <span data-ttu-id="7c1ec-139">驅動程式會有效率地執行陳述式 S 次，針對每個參數集執行一次。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-139">The driver efficiently executes the statement S times, once for each set of parameters.</span></span>  
  
6.  <span data-ttu-id="7c1ec-140">如果使用了資料執行中輸入參數， [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)會傳回 SQL_NEED_DATA。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-140">If data-at-execution input parameters are used, [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) returns SQL_NEED_DATA.</span></span> <span data-ttu-id="7c1ec-141">使用[SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405)和[SQLPutData](../../native-client-odbc-api/sqlputdata.md)以區區塊轉送資料。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-141">Send the data in chunks by using [SQLParamData](https://go.microsoft.com/fwlink/?LinkId=58405) and [SQLPutData](../../native-client-odbc-api/sqlputdata.md).</span></span>  
  
 <span data-ttu-id="7c1ec-142">**注意**資料行取向和資料列取向的系結通常會與[SQLPrepare](https://go.microsoft.com/fwlink/?LinkId=59360)函式和[SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400)搭配使用，而不是[SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399)。</span><span class="sxs-lookup"><span data-stu-id="7c1ec-142">**Note** Column-wise and row-wise binding are more typically used in conjunction with [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360) and [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) than with [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c1ec-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7c1ec-143">See Also</span></span>  
 [<span data-ttu-id="7c1ec-144">執行查詢 &#40;ODBC&#41;的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="7c1ec-144">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](executing-queries-how-to-topics-odbc.md)  
  
  
