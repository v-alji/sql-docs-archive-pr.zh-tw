---
title: 滾動和提取資料列 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- scrollable cursors [SQL Server]
- SQL Server Native Client ODBC driver, cursors
- SQLFetchScroll function
- ODBC applications, cursors
- cursors [ODBC], fetching rows
- ODBC cursors, fetching rows
- cursors [ODBC], scrolling rows
- fetching [ODBC]
- ODBC cursors, scrolling rows
ms.assetid: 9109f10d-326b-4a6d-8c97-831f60da8c4c
author: rothja
ms.author: jroth
ms.openlocfilehash: 97586f82ddddb79581b0f9c027aa60d7822b472c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707509"
---
# <a name="scrolling-and-fetching-rows"></a><span data-ttu-id="27c91-102">捲動與提取資料列</span><span class="sxs-lookup"><span data-stu-id="27c91-102">Scrolling and Fetching Rows</span></span>
  <span data-ttu-id="27c91-103">若要使用可捲動的資料指標，ODBC 應用程式必須：</span><span class="sxs-lookup"><span data-stu-id="27c91-103">To use a scrollable cursor, an ODBC application must:</span></span>  
  
-   <span data-ttu-id="27c91-104">使用[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)設定資料指標功能。</span><span class="sxs-lookup"><span data-stu-id="27c91-104">Set the cursor capabilities using [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md).</span></span>  
  
-   <span data-ttu-id="27c91-105">使用**SQLExecute**或**SQLExecDirect**開啟資料指標。</span><span class="sxs-lookup"><span data-stu-id="27c91-105">Open the cursor using **SQLExecute** or **SQLExecDirect**.</span></span>  
  
-   <span data-ttu-id="27c91-106">使用**SQLFetch**或[SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)來滾動和提取資料列。</span><span class="sxs-lookup"><span data-stu-id="27c91-106">Scroll and fetch rows using **SQLFetch** or [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).</span></span>  
  
 <span data-ttu-id="27c91-107">**SQLFetch**和**SQLFetchSroll**都可以一次提取資料列區塊。</span><span class="sxs-lookup"><span data-stu-id="27c91-107">Both **SQLFetch** and **SQLFetchSroll** can fetch blocks of rows at a time.</span></span> <span data-ttu-id="27c91-108">傳回的資料列數目是藉由使用**SQLSetStmtAttr**來設定 SQL_ATTR_ROW_ARRAY_SIZE 參數所指定。</span><span class="sxs-lookup"><span data-stu-id="27c91-108">The number of rows returned is specified by using **SQLSetStmtAttr** to set the SQL_ATTR_ROW_ARRAY_SIZE parameter.</span></span>  
  
 <span data-ttu-id="27c91-109">ODBC 應用程式可以使用**SQLFetch** ，透過順向資料指標來提取。</span><span class="sxs-lookup"><span data-stu-id="27c91-109">ODBC applications can use **SQLFetch** to fetch through a forward-only cursor.</span></span>  
  
 <span data-ttu-id="27c91-110">**SQLFetchScroll**是用來在資料指標周圍進行滾動。</span><span class="sxs-lookup"><span data-stu-id="27c91-110">**SQLFetchScroll** is used to scroll around a cursor.</span></span> <span data-ttu-id="27c91-111">**SQLFetchScroll**支援提取下一個、先前、第一個和最後一個資料列集，而相對的提取 (從目前資料列集的開頭提取資料列集*n*資料列) 而絕對提取 (提取從資料列*n*) 開始的資料列集。</span><span class="sxs-lookup"><span data-stu-id="27c91-111">**SQLFetchScroll** supports fetching the next, prior, first, and last rowsets in addition to relative fetching (fetch the rowset *n* rows from the start of the current rowset) and absolute fetching (fetch the rowset starting at row *n*).</span></span> <span data-ttu-id="27c91-112">如果*n*在絕對提取中為負數，則會從結果集的結尾計算資料列。</span><span class="sxs-lookup"><span data-stu-id="27c91-112">If *n* is negative in an absolute fetch, rows are counted from the end of the result set.</span></span> <span data-ttu-id="27c91-113">資料列的絕對提取 -1 表示提取從結果集的最後一個資料列開始的資料列集。</span><span class="sxs-lookup"><span data-stu-id="27c91-113">An absolute fetch of row -1 means to fetch the rowset that starts with the last row in the result set.</span></span>  
  
 <span data-ttu-id="27c91-114">僅針對其區塊資料指標功能使用**SQLFetchScroll**的應用程式（例如報表）可能會通過單一時間的結果集，而只會使用提取下一個資料列集的選項。</span><span class="sxs-lookup"><span data-stu-id="27c91-114">Applications that use **SQLFetchScroll** only for its block cursor capabilities, such as reports, are likely to pass through the result set a single time, using only the option to fetch the next rowset.</span></span> <span data-ttu-id="27c91-115">另一方面，以螢幕為基礎的應用程式可以利用**SQLFetchScroll**的所有功能。</span><span class="sxs-lookup"><span data-stu-id="27c91-115">Screen-based applications, on the other hand, can take advantage of all the capabilities of **SQLFetchScroll**.</span></span> <span data-ttu-id="27c91-116">如果應用程式將資料列集大小設定為螢幕上顯示的資料列數目，並將螢幕緩衝區系結至結果集，則可以直接將捲軸作業轉譯為呼叫**SQLFetchScroll**。</span><span class="sxs-lookup"><span data-stu-id="27c91-116">If the application sets the rowset size to the number of rows displayed on the screen and binds the screen buffers to the result set, it can translate scroll bar operations directly to calls to **SQLFetchScroll**.</span></span>  
  
|<span data-ttu-id="27c91-117">捲軸作業</span><span class="sxs-lookup"><span data-stu-id="27c91-117">Scroll bar operation</span></span>|<span data-ttu-id="27c91-118">SQLFetchScroll 捲動選項</span><span class="sxs-lookup"><span data-stu-id="27c91-118">SQLFetchScroll scrolling option</span></span>|  
|--------------------------|-------------------------------------|  
|<span data-ttu-id="27c91-119">向上捲動一頁</span><span class="sxs-lookup"><span data-stu-id="27c91-119">Page up</span></span>|<span data-ttu-id="27c91-120">SQL_FETCH_PRIOR</span><span class="sxs-lookup"><span data-stu-id="27c91-120">SQL_FETCH_PRIOR</span></span>|  
|<span data-ttu-id="27c91-121">向下捲動一頁</span><span class="sxs-lookup"><span data-stu-id="27c91-121">Page down</span></span>|<span data-ttu-id="27c91-122">SQL_FETCH_NEXT</span><span class="sxs-lookup"><span data-stu-id="27c91-122">SQL_FETCH_NEXT</span></span>|  
|<span data-ttu-id="27c91-123">向上捲動一行</span><span class="sxs-lookup"><span data-stu-id="27c91-123">Line up</span></span>|<span data-ttu-id="27c91-124">FetchOffset 等於-1 的 SQL_FETCH_RELATIVE</span><span class="sxs-lookup"><span data-stu-id="27c91-124">SQL_FETCH_RELATIVE with FetchOffset equal to -1</span></span>|  
|<span data-ttu-id="27c91-125">向下捲動一行</span><span class="sxs-lookup"><span data-stu-id="27c91-125">Line down</span></span>|<span data-ttu-id="27c91-126">包含 FetchOffset 的 SQL_FETCH_RELATIVE 等於 1</span><span class="sxs-lookup"><span data-stu-id="27c91-126">SQL_FETCH_RELATIVE with FetchOffset equal to 1</span></span>|  
|<span data-ttu-id="27c91-127">捲動方塊到頂端</span><span class="sxs-lookup"><span data-stu-id="27c91-127">Scroll box to top</span></span>|<span data-ttu-id="27c91-128">SQL_FETCH_FIRST</span><span class="sxs-lookup"><span data-stu-id="27c91-128">SQL_FETCH_FIRST</span></span>|  
|<span data-ttu-id="27c91-129">捲動方塊到底部</span><span class="sxs-lookup"><span data-stu-id="27c91-129">Scroll box to bottom</span></span>|<span data-ttu-id="27c91-130">SQL_FETCH_LAST</span><span class="sxs-lookup"><span data-stu-id="27c91-130">SQL_FETCH_LAST</span></span>|  
|<span data-ttu-id="27c91-131">隨機捲動方塊位置</span><span class="sxs-lookup"><span data-stu-id="27c91-131">Random scroll box position</span></span>|<span data-ttu-id="27c91-132">SQL_FETCH_ABSOLUTE</span><span class="sxs-lookup"><span data-stu-id="27c91-132">SQL_FETCH_ABSOLUTE</span></span>|  
  
## <a name="in-this-section"></a><span data-ttu-id="27c91-133">本節內容</span><span class="sxs-lookup"><span data-stu-id="27c91-133">In This Section</span></span>  
  
-   [<span data-ttu-id="27c91-134">在 ODBC 中的資料列上加上書籤</span><span class="sxs-lookup"><span data-stu-id="27c91-134">Bookmarking Rows in ODBC</span></span>](scrolling-and-fetching-rows-bookmarking-rows-in-odbc.md)  
  
## <a name="see-also"></a><span data-ttu-id="27c91-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27c91-135">See Also</span></span>  
 [<span data-ttu-id="27c91-136">&#40;ODBC&#41;使用資料指標</span><span class="sxs-lookup"><span data-stu-id="27c91-136">Using Cursors &#40;ODBC&#41;</span></span>](using-cursors-odbc.md)  
  
  
