---
title: " (ODBC) 使用資料列集系結 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- rowset binding [ODBC]
ms.assetid: a7be05f0-6b11-4b53-9fbc-501e591eef09
author: rothja
ms.author: jroth
ms.openlocfilehash: e2e0671fd1140e72005cd1a7532ea581f077382f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584470"
---
# <a name="use-rowset-binding-odbc"></a><span data-ttu-id="300d7-102">使用資料列集繫結 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="300d7-102">Use Rowset Binding (ODBC)</span></span>
    
### <a name="to-use-column-wise-binding"></a><span data-ttu-id="300d7-103">使用資料行取向的繫結</span><span class="sxs-lookup"><span data-stu-id="300d7-103">To use column-wise binding</span></span>  
  
1.  <span data-ttu-id="300d7-104">針對每個繫結資料行，請執行下列動作：</span><span class="sxs-lookup"><span data-stu-id="300d7-104">For each bound column, do the following:</span></span>  
  
    -   <span data-ttu-id="300d7-105">配置 R (或更多) 個資料行緩衝區的陣列以儲存資料值，其中 R 是資料列集的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="300d7-105">Allocate an array of R (or more) column buffers to store data values, where R is number of rows in the rowset.</span></span>  
  
    -   <span data-ttu-id="300d7-106">或者，配置 R (或更多) 個資料行緩衝區的陣列來儲存資料長度。</span><span class="sxs-lookup"><span data-stu-id="300d7-106">Optionally, allocate an array of R (or more) column buffers to store data lengths.</span></span>  
  
    -   <span data-ttu-id="300d7-107">呼叫[SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) ，將資料行的資料值和資料長度陣列系結至資料列集的資料行。</span><span class="sxs-lookup"><span data-stu-id="300d7-107">Call [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) to bind the column's data value and data length arrays to the column of the rowset.</span></span>  
  
2.  <span data-ttu-id="300d7-108">呼叫[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)以設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="300d7-108">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
    -   <span data-ttu-id="300d7-109">將 SQL_ATTR_ROW_ARRAY_SIZE 設定為資料列集的資料列數目 (R)。</span><span class="sxs-lookup"><span data-stu-id="300d7-109">Set SQL_ATTR_ROW_ARRAY_SIZE to the number of rows in the rowset (R).</span></span>  
  
    -   <span data-ttu-id="300d7-110">將 SQL_ATTR_ROW_BIND_TYPE 設定為 SQL_BIND_BY_COLUMN。</span><span class="sxs-lookup"><span data-stu-id="300d7-110">Set SQL_ATTR_ROW_BIND_TYPE to SQL_BIND_BY_COLUMN.</span></span>  
  
    -   <span data-ttu-id="300d7-111">將 SQL_ATTR_ROWS FETCHED_PTR 屬性設定為指向 SQLUINTEGER 變數，以保存提取的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="300d7-111">Set the SQL_ATTR_ROWS FETCHED_PTR attribute to point to a SQLUINTEGER variable to hold the number of rows fetched.</span></span>  
  
    -   <span data-ttu-id="300d7-112">將 SQL_ATTR_ROW_STATUS_PTR 設定為指向 SQLUSSMALLINT 變數的陣列[R]，以保存資料列狀態指標。</span><span class="sxs-lookup"><span data-stu-id="300d7-112">Set SQL_ATTR_ROW_STATUS_PTR to point to an array[R] of SQLUSSMALLINT variables to hold the row-status indicators.</span></span>  
  
3.  <span data-ttu-id="300d7-113">執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="300d7-113">Execute the statement.</span></span>  
  
4.  <span data-ttu-id="300d7-114">[SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401)或[SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)的每個呼叫都會抓取 R 資料列，並將資料傳輸至系結的資料行。</span><span class="sxs-lookup"><span data-stu-id="300d7-114">Each call to [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) or [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) retrieves R rows and transfers the data into the bound columns.</span></span>  
  
### <a name="to-use-row-wise-binding"></a><span data-ttu-id="300d7-115">使用資料列取向的繫結</span><span class="sxs-lookup"><span data-stu-id="300d7-115">To use row-wise binding</span></span>  
  
1.  <span data-ttu-id="300d7-116">配置結構的陣列[R]，其中 R 是資料列集的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="300d7-116">Allocate an array[R] of structures, where R is the number of rows in the rowset.</span></span> <span data-ttu-id="300d7-117">結構中每個資料行都具有一個元素，而每個元素則具有兩部分：</span><span class="sxs-lookup"><span data-stu-id="300d7-117">The structure has one element for each column, and each element has two parts:</span></span>  
  
    -   <span data-ttu-id="300d7-118">第一個部分是適當資料類型的變數，可保存資料行資料。</span><span class="sxs-lookup"><span data-stu-id="300d7-118">The first part is a variable of the appropriate data type to hold the column data.</span></span>  
  
    -   <span data-ttu-id="300d7-119">第二個部分是 SQLINTEGER 變數，可保存資料行狀態指標。</span><span class="sxs-lookup"><span data-stu-id="300d7-119">The second part is a SQLINTEGER variable to hold the column status indicator.</span></span>  
  
2.  <span data-ttu-id="300d7-120">呼叫[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)以設定下列屬性：</span><span class="sxs-lookup"><span data-stu-id="300d7-120">Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set the following attributes:</span></span>  
  
    -   <span data-ttu-id="300d7-121">將 SQL_ATTR_ROW_ARRAY_SIZE 設定為資料列集的資料列數目 (R)。</span><span class="sxs-lookup"><span data-stu-id="300d7-121">Set SQL_ATTR_ROW_ARRAY_SIZE to the number of rows in the rowset (R).</span></span>  
  
    -   <span data-ttu-id="300d7-122">將 SQL_ATTR_ROW_BIND_TYPE 設定為步驟 1 中配置的結構大小。</span><span class="sxs-lookup"><span data-stu-id="300d7-122">Set SQL_ATTR_ROW_BIND_TYPE to the size of the structure allocated in Step 1.</span></span>  
  
    -   <span data-ttu-id="300d7-123">將 SQL_ATTR_ROWS_FETCHED_PTR 屬性設定為指向 SQLUINTEGER 變數，以保存提取的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="300d7-123">Set the SQL_ATTR_ROWS_FETCHED_PTR attribute to point to a SQLUINTEGER variable to hold the number of rows fetched.</span></span>  
  
    -   <span data-ttu-id="300d7-124">將 SQL_ATTR_PARAMS_STATUS_PTR 設定為指向 SQLUSSMALLINT 變數的陣列[R]，以保存資料列狀態指標。</span><span class="sxs-lookup"><span data-stu-id="300d7-124">Set SQL_ATTR_PARAMS_STATUS_PTR to point to an array[R] of SQLUSSMALLINT variables to hold the row-status indicators.</span></span>  
  
3.  <span data-ttu-id="300d7-125">針對結果集中的每個資料行呼叫[SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) ，以將資料行的資料值和資料長度指標指向其在步驟1所配置之結構陣列第一個元素中的變數。</span><span class="sxs-lookup"><span data-stu-id="300d7-125">For each column in the result set, call [SQLBindCol](../../native-client-odbc-api/sqlbindcol.md) to point the data value and data length pointer of the column to their variables in the first element of the array of structures allocated in Step 1.</span></span>  
  
4.  <span data-ttu-id="300d7-126">執行陳述式。</span><span class="sxs-lookup"><span data-stu-id="300d7-126">Execute the statement.</span></span>  
  
5.  <span data-ttu-id="300d7-127">[SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401)或[SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)的每個呼叫都會抓取 R 資料列，並將資料傳輸至系結的資料行。</span><span class="sxs-lookup"><span data-stu-id="300d7-127">Each call to [SQLFetch](https://go.microsoft.com/fwlink/?LinkId=58401) or [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md) retrieves R rows and transfers the data into the bound columns.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="300d7-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="300d7-128">See Also</span></span>  
 <span data-ttu-id="300d7-129">[使用資料指標的 how to 主題 &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="300d7-129">[Using Cursors How-to Topics &#40;ODBC&#41;](using-cursors-how-to-topics-odbc.md) </span></span>  
 <span data-ttu-id="300d7-130">[如何實作為資料指標](../../native-client-odbc-cursors/implementation/how-cursors-are-implemented.md) </span><span class="sxs-lookup"><span data-stu-id="300d7-130">[How Cursors Are Implemented](../../native-client-odbc-cursors/implementation/how-cursors-are-implemented.md) </span></span>  
 [<span data-ttu-id="300d7-131">&#40;ODBC&#41;使用資料指標</span><span class="sxs-lookup"><span data-stu-id="300d7-131">Use Cursors &#40;ODBC&#41;</span></span>](use-cursors-odbc.md)  
  
  
