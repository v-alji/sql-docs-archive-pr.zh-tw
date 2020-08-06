---
title: 使用 (ODBC) 的語句 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- statements [ODBC]
ms.assetid: f7573f8f-6f21-4e03-8dd5-a5f2ea4878cc
author: rothja
ms.author: jroth
ms.openlocfilehash: 8ff3bc8c545cc9b55f0da3bb31d68d1ecbb5b547
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707493"
---
# <a name="use-a-statement-odbc"></a><span data-ttu-id="5f283-102">使用陳述式 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="5f283-102">Use a Statement (ODBC)</span></span>
    
### <a name="to-use-a-statement"></a><span data-ttu-id="5f283-103">使用陳述式</span><span class="sxs-lookup"><span data-stu-id="5f283-103">To use a statement</span></span>  
  
1.  <span data-ttu-id="5f283-104">利用 SQL_HANDLE_STMT 的 *HandleType* 來呼叫 [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396)，以配置陳述式控制代碼。</span><span class="sxs-lookup"><span data-stu-id="5f283-104">Call [SQLAllocHandle](https://go.microsoft.com/fwlink/?LinkId=58396) with a *HandleType* of SQL_HANDLE_STMT to allocate a statement handle.</span></span>  
  
2.  <span data-ttu-id="5f283-105">您可以選擇呼叫 [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) 來設定陳述式選項，或是呼叫 [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) 來取得陳述式屬性。</span><span class="sxs-lookup"><span data-stu-id="5f283-105">Optionally, call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set statement options or [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) to get statement attributes.</span></span>  
  
     <span data-ttu-id="5f283-106">若要使用伺服器資料指標，您必須將資料指標屬性設定為預設值以外的值。</span><span class="sxs-lookup"><span data-stu-id="5f283-106">To use server cursors, you must set cursor attributes to values other than their defaults.</span></span>  
  
3.  <span data-ttu-id="5f283-107">如果此陳述式將會執行數次，您可以選擇預備此陳述式搭配 [SQLPrepare 函數](https://go.microsoft.com/fwlink/?LinkId=59360)一起執行。</span><span class="sxs-lookup"><span data-stu-id="5f283-107">Optionally, if the statement will be executed several times, prepare the statement for execution with [SQLPrepare Function](https://go.microsoft.com/fwlink/?LinkId=59360).</span></span>  
  
4.  <span data-ttu-id="5f283-108">如果此陳述式已經繫結參數標記，您可以選擇使用 [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md) 將這些參數標記繫結至程式變數。</span><span class="sxs-lookup"><span data-stu-id="5f283-108">Optionally, if the statement has bound parameter markers, bind the parameter markers to program variables by using [SQLBindParameter](../../native-client-odbc-api/sqlbindparameter.md).</span></span> <span data-ttu-id="5f283-109">如果此陳述式已備妥，您可以呼叫 [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) 和 [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) 來尋找參數的數目和參數的特性。</span><span class="sxs-lookup"><span data-stu-id="5f283-109">If the statement was prepared, you can call [SQLNumParams](https://go.microsoft.com/fwlink/?LinkId=58404) and [SQLDescribeParam](../../native-client-odbc-api/sqldescribeparam.md) to find the number and characteristics of the parameters.</span></span>  
  
5.  <span data-ttu-id="5f283-110">使用 SQLExecDirect 直接執行陳述式</span><span class="sxs-lookup"><span data-stu-id="5f283-110">Execute a statement directly by using SQLExecDirect.</span></span>  
  
     <span data-ttu-id="5f283-111">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="5f283-111">\- or -</span></span>  
  
     <span data-ttu-id="5f283-112">如果此陳述式已備妥，請使用 [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400) 將它執行多次。</span><span class="sxs-lookup"><span data-stu-id="5f283-112">If the statement was prepared, execute it multiple times by using [SQLExecute](https://go.microsoft.com/fwlink/?LinkId=58400).</span></span>  
  
     <span data-ttu-id="5f283-113">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="5f283-113">\- or -</span></span>  
  
     <span data-ttu-id="5f283-114">呼叫目錄函數，這樣會傳回結果。</span><span class="sxs-lookup"><span data-stu-id="5f283-114">Call a catalog function, which returns results.</span></span>  
  
6.  <span data-ttu-id="5f283-115">若要處理結果，請將結果集資料行繫結至程式變數、使用 [SQLGetData](../../native-client-odbc-api/sqlgetdata.md) 將資料從結果集資料行中移到程式變數，或是結合這兩個方法。</span><span class="sxs-lookup"><span data-stu-id="5f283-115">Process the results by binding the result set columns to program variables, by moving data from the result set columns to program variables by using [SQLGetData](../../native-client-odbc-api/sqlgetdata.md), or a combination of the two methods.</span></span>  
  
     <span data-ttu-id="5f283-116">透過陳述式的結果集一次提取一個資料列。</span><span class="sxs-lookup"><span data-stu-id="5f283-116">Fetch through the result set of a statement one row at a time.</span></span>  
  
     <span data-ttu-id="5f283-117">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="5f283-117">\- or -</span></span>  
  
     <span data-ttu-id="5f283-118">透過結果集，利用區塊資料指標一次提取數個資料列。</span><span class="sxs-lookup"><span data-stu-id="5f283-118">Fetch through the result set several rows at a time by using a block cursor.</span></span>  
  
     <span data-ttu-id="5f283-119">\- 或 -</span><span class="sxs-lookup"><span data-stu-id="5f283-119">\- or -</span></span>  
  
     <span data-ttu-id="5f283-120">呼叫 [SQLRowCount](../../native-client-odbc-api/sqlrowcount.md) 來判斷受到 INSERT、UPDATE 或 DELETE 陳述式影響的資料列數。</span><span class="sxs-lookup"><span data-stu-id="5f283-120">Call [SQLRowCount](../../native-client-odbc-api/sqlrowcount.md) to determine the number of rows affected by an INSERT, UPDATE, or DELETE statement.</span></span>  
  
     <span data-ttu-id="5f283-121">如果 SQL 陳述式可以有多個結果集，請在每一個結果集的結尾呼叫 [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)，以查看是否有其他結果集要處理。</span><span class="sxs-lookup"><span data-stu-id="5f283-121">If the SQL statement can have multiple result sets, call [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) at the end of each result set to see if there are additional result sets to process.</span></span>  
  
7.  <span data-ttu-id="5f283-122">處理完結果之後，可能需要採取以下動作，以便提供陳述式控制代碼來執行新的陳述式：</span><span class="sxs-lookup"><span data-stu-id="5f283-122">After results are processed, the following actions may be necessary to make the statement handle available to execute a new statement:</span></span>  
  
    -   <span data-ttu-id="5f283-123">如果您要等到它傳回 SQL_NO_DATA 之後才會呼叫 [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md)，請呼叫 [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) 來關閉此資料指標。</span><span class="sxs-lookup"><span data-stu-id="5f283-123">If you did not call [SQLMoreResults](../../native-client-odbc-api/sqlmoreresults.md) until it returned SQL_NO_DATA, call [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) to close the cursor.</span></span>  
  
    -   <span data-ttu-id="5f283-124">如果您將參數標記繫結至程式變數，請呼叫 [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) 並將 *Option* 設定為 SQL_RESET_PARAMS，以釋放繫結參數。</span><span class="sxs-lookup"><span data-stu-id="5f283-124">If you bound parameter markers to program variables, call [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) with *Option* set to SQL_RESET_PARAMS to free the bound parameters.</span></span>  
  
    -   <span data-ttu-id="5f283-125">如果您將結果集資料行繫結至程式變數，請呼叫 [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) 並將 *Option* 設定為 SQL_UNBIND，以釋放繫結的資料行。</span><span class="sxs-lookup"><span data-stu-id="5f283-125">If you bound result set columns to program variables, call [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) with *Option* set to SQL_UNBIND to free the bound columns.</span></span>  
  
    -   <span data-ttu-id="5f283-126">若要重複使用陳述式控制代碼，請移至步驟 2。</span><span class="sxs-lookup"><span data-stu-id="5f283-126">To reuse the statement handle, go to Step 2.</span></span>  
  
8.  <span data-ttu-id="5f283-127">使用 SQL_HANDLE_STMT 的 *HandleType* 呼叫 [SQLFreeHandle](../../native-client-odbc-api/sqlfreehandle.md)，以釋放陳述式控制代碼。</span><span class="sxs-lookup"><span data-stu-id="5f283-127">Call [SQLFreeHandle](../../native-client-odbc-api/sqlfreehandle.md) with a *HandleType* of SQL_HANDLE_STMT to free the statement handle.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f283-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5f283-128">See Also</span></span>  
 [<span data-ttu-id="5f283-129">執行查詢 &#40;ODBC&#41;的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="5f283-129">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](executing-queries-how-to-topics-odbc.md)  
  
  
