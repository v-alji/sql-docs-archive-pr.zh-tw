---
title: 使用 ODBC)  (的資料指標 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- ODBC cursors, about ODBC cursors
- ODBC applications, cursors
- cursors [ODBC]
- ODBC cursors
ms.assetid: 51322f92-0d76-44c9-9c33-9223676cf1d3
author: rothja
ms.author: jroth
ms.openlocfilehash: 61afedab4f4a1e309a08d9c2421ca7889811da8a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707501"
---
# <a name="using-cursors-odbc"></a><span data-ttu-id="2ca80-102">使用資料指標 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="2ca80-102">Using Cursors (ODBC)</span></span>
  <span data-ttu-id="2ca80-103">ODBC 支援的資料指標模型允許：</span><span class="sxs-lookup"><span data-stu-id="2ca80-103">ODBC supports a cursor model that allows:</span></span>  
  
-   <span data-ttu-id="2ca80-104">數種資料指標類型。</span><span class="sxs-lookup"><span data-stu-id="2ca80-104">Several types of cursors.</span></span>  
  
-   <span data-ttu-id="2ca80-105">在資料指標內捲動和定位。</span><span class="sxs-lookup"><span data-stu-id="2ca80-105">Scrolling and positioning within a cursor.</span></span>  
  
-   <span data-ttu-id="2ca80-106">多個並行選項。</span><span class="sxs-lookup"><span data-stu-id="2ca80-106">Several concurrency options.</span></span>  
  
-   <span data-ttu-id="2ca80-107">定位更新。</span><span class="sxs-lookup"><span data-stu-id="2ca80-107">Positioned updates.</span></span>  
  
 <span data-ttu-id="2ca80-108">ODBC 應用程式很少會宣告及開啟資料指標，或使用任何與資料指標相關的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="2ca80-108">ODBC applications rarely declare and open cursors or use any cursor-related [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="2ca80-109">ODBC 會針對每個從 SQL 陳述式傳回的結果集而自動開啟資料指標。</span><span class="sxs-lookup"><span data-stu-id="2ca80-109">ODBC automatically opens a cursor for every result set returned from an SQL statement.</span></span> <span data-ttu-id="2ca80-110">在執行 SQL 語句之前，會使用以[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)設定的語句屬性來控制資料指標的特性。</span><span class="sxs-lookup"><span data-stu-id="2ca80-110">The characteristics of the cursors are controlled by statement attributes set with [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) before the SQL statement is executed.</span></span> <span data-ttu-id="2ca80-111">用來處理結果集的 ODBC API 函數支援完整的資料指標功能，包括提取、捲動和定位更新等。</span><span class="sxs-lookup"><span data-stu-id="2ca80-111">The ODBC API functions for processing result sets support the full range of cursor functionality, including fetching, scrolling, and positioned updates.</span></span>  
  
 <span data-ttu-id="2ca80-112">這是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼和 ODBC 應用程式如何搭配資料指標使用的比較。</span><span class="sxs-lookup"><span data-stu-id="2ca80-112">This is a comparison of how [!INCLUDE[tsql](../../includes/tsql-md.md)] scripts and ODBC applications work with cursors.</span></span>  
  
|<span data-ttu-id="2ca80-113">動作</span><span class="sxs-lookup"><span data-stu-id="2ca80-113">Action</span></span>|[!INCLUDE[tsql](../../includes/tsql-md.md)]|<span data-ttu-id="2ca80-114">ODBC</span><span class="sxs-lookup"><span data-stu-id="2ca80-114">ODBC</span></span>|  
|------------|------------------------|----------|  
|<span data-ttu-id="2ca80-115">定義資料指標行為</span><span class="sxs-lookup"><span data-stu-id="2ca80-115">Define cursor behavior</span></span>|<span data-ttu-id="2ca80-116">指定透過 DECLARE CURSOR 參數</span><span class="sxs-lookup"><span data-stu-id="2ca80-116">Specify through DECLARE CURSOR parameters</span></span>|<span data-ttu-id="2ca80-117">使用[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)設定資料指標屬性</span><span class="sxs-lookup"><span data-stu-id="2ca80-117">Set cursor attributes by using [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)</span></span>|  
|<span data-ttu-id="2ca80-118">開啟資料指標</span><span class="sxs-lookup"><span data-stu-id="2ca80-118">Open a cursor</span></span>|<span data-ttu-id="2ca80-119">將資料指標開啟*cursor_name*</span><span class="sxs-lookup"><span data-stu-id="2ca80-119">DECLARE CURSOR OPEN *cursor_name*</span></span>|<span data-ttu-id="2ca80-120">**SQLExecDirect**或**SQLExecute**</span><span class="sxs-lookup"><span data-stu-id="2ca80-120">**SQLExecDirect** or **SQLExecute**</span></span>|  
|<span data-ttu-id="2ca80-121">提取資料列</span><span class="sxs-lookup"><span data-stu-id="2ca80-121">Fetch rows</span></span>|<span data-ttu-id="2ca80-122">FETCH</span><span class="sxs-lookup"><span data-stu-id="2ca80-122">FETCH</span></span>|<span data-ttu-id="2ca80-123">**SQLFetch**或[SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)</span><span class="sxs-lookup"><span data-stu-id="2ca80-123">**SQLFetch** or [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)</span></span>|  
|<span data-ttu-id="2ca80-124">定點更新</span><span class="sxs-lookup"><span data-stu-id="2ca80-124">Positioned update</span></span>|<span data-ttu-id="2ca80-125">UPDATE 或 DELETE 上的 WHERE CURRENT OF 子句</span><span class="sxs-lookup"><span data-stu-id="2ca80-125">WHERE CURRENT OF clause on UPDATE or DELETE</span></span>|<span data-ttu-id="2ca80-126">**SQLSetPos**</span><span class="sxs-lookup"><span data-stu-id="2ca80-126">**SQLSetPos**</span></span>|  
|<span data-ttu-id="2ca80-127">關閉資料指標</span><span class="sxs-lookup"><span data-stu-id="2ca80-127">Close a cursor</span></span>|<span data-ttu-id="2ca80-128">關閉*cursor_name*解除配置</span><span class="sxs-lookup"><span data-stu-id="2ca80-128">CLOSE *cursor_name* DEALLOCATE</span></span>|[<span data-ttu-id="2ca80-129">SQLCloseCursor</span><span class="sxs-lookup"><span data-stu-id="2ca80-129">SQLCloseCursor</span></span>](../native-client-odbc-api/sqlclosecursor.md)|  
  
 <span data-ttu-id="2ca80-130">實作於 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 的伺服器資料指標支援 ODBC 資料指標模型的功能。</span><span class="sxs-lookup"><span data-stu-id="2ca80-130">The server cursors implemented in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] support the functionality of the ODBC cursor model.</span></span> <span data-ttu-id="2ca80-131">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 驅動程式使用伺服器資料指標支援 ODBC API 的資料指標功能。</span><span class="sxs-lookup"><span data-stu-id="2ca80-131">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client driver uses server cursors to support the cursor functionality of the ODBC API.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2ca80-132">本節內容</span><span class="sxs-lookup"><span data-stu-id="2ca80-132">In This Section</span></span>  
  
-   [<span data-ttu-id="2ca80-133">如何實作資料指標</span><span class="sxs-lookup"><span data-stu-id="2ca80-133">How Cursors Are Implemented</span></span>](implementation/how-cursors-are-implemented.md)  
  
-   [<span data-ttu-id="2ca80-134">資料指標類型</span><span class="sxs-lookup"><span data-stu-id="2ca80-134">Cursor Types</span></span>](cursor-types.md)  
  
-   [<span data-ttu-id="2ca80-135">資料指標行為</span><span class="sxs-lookup"><span data-stu-id="2ca80-135">Cursor Behaviors</span></span>](cursor-behaviors.md)  
  
-   [<span data-ttu-id="2ca80-136">資料指標屬性</span><span class="sxs-lookup"><span data-stu-id="2ca80-136">Cursor Properties</span></span>](properties/cursor-properties.md)  
  
-   [<span data-ttu-id="2ca80-137">ODBC&#41;&#40;的資料指標程式設計詳細資料</span><span class="sxs-lookup"><span data-stu-id="2ca80-137">Cursor Programming Details &#40;ODBC&#41;</span></span>](programming/cursor-programming-details-odbc.md)  
  
-   [<span data-ttu-id="2ca80-138">捲動與提取資料列</span><span class="sxs-lookup"><span data-stu-id="2ca80-138">Scrolling and Fetching Rows</span></span>](../native-client-ole-db-rowsets/fetching-rows.md)  
  
-   [<span data-ttu-id="2ca80-139">&#40;ODBC&#41;的定點更新</span><span class="sxs-lookup"><span data-stu-id="2ca80-139">Positioned Updates &#40;ODBC&#41;</span></span>](positioned-updates-odbc.md)  
  
## <a name="see-also"></a><span data-ttu-id="2ca80-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2ca80-140">See Also</span></span>  
 <span data-ttu-id="2ca80-141">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span><span class="sxs-lookup"><span data-stu-id="2ca80-141">[SQL Server Native Client &#40;ODBC&#41;](../native-client/odbc/sql-server-native-client-odbc.md) </span></span>  
 <span data-ttu-id="2ca80-142">[關閉 &#40;Transact-sql&#41;](/sql/t-sql/language-elements/close-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2ca80-142">[CLOSE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/close-transact-sql) </span></span>  
 <span data-ttu-id="2ca80-143">[資料指標](../../relational-databases/cursors.md) </span><span class="sxs-lookup"><span data-stu-id="2ca80-143">[Cursors](../../relational-databases/cursors.md) </span></span>  
 <span data-ttu-id="2ca80-144">[解除配置 &#40;Transact-sql&#41;](/sql/t-sql/language-elements/deallocate-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2ca80-144">[DEALLOCATE &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/deallocate-transact-sql) </span></span>  
 <span data-ttu-id="2ca80-145">[DECLARE CURSOR &#40;Transact-sql&#41;](/sql/t-sql/language-elements/declare-cursor-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2ca80-145">[DECLARE CURSOR &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-cursor-transact-sql) </span></span>  
 <span data-ttu-id="2ca80-146">[FETCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/fetch-transact-sql) </span><span class="sxs-lookup"><span data-stu-id="2ca80-146">[FETCH &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/fetch-transact-sql) </span></span>  
 [<span data-ttu-id="2ca80-147">OPEN &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="2ca80-147">OPEN &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/language-elements/open-transact-sql)  
  
  
