---
title: 將更新定位 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, cursors
- SQLSetPos function
- SQLSetCursorName function
- ODBC applications, cursors
- cursors [ODBC], positioned updates
- positioned updates [ODBC]
- ODBC cursors, positioned updates
ms.assetid: ff404e02-630f-474d-b5d4-06442b756991
author: rothja
ms.author: jroth
ms.openlocfilehash: 20272014e32632117e6282e5929d1d21789852df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594064"
---
# <a name="positioned-updates-odbc"></a><span data-ttu-id="138d0-102">定位更新 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="138d0-102">Positioned Updates (ODBC)</span></span>
  <span data-ttu-id="138d0-103">ODBC 支援兩個方法於資料指標上執行定位更新：</span><span class="sxs-lookup"><span data-stu-id="138d0-103">ODBC supports two methods for performing positioned updates in a cursor:</span></span>  
  
-   <span data-ttu-id="138d0-104">**SQLSetPos**</span><span class="sxs-lookup"><span data-stu-id="138d0-104">**SQLSetPos**</span></span>  
  
-   <span data-ttu-id="138d0-105">WHERE CURRENT OF 子句</span><span class="sxs-lookup"><span data-stu-id="138d0-105">WHERE CURRENT OF clause</span></span>  
  
 <span data-ttu-id="138d0-106">較常見的方法是使用**SQLSetPos**。</span><span class="sxs-lookup"><span data-stu-id="138d0-106">The more common approach is to use **SQLSetPos**.</span></span> <span data-ttu-id="138d0-107">它的選項如下。</span><span class="sxs-lookup"><span data-stu-id="138d0-107">It has the following options.</span></span>  
  
 <span data-ttu-id="138d0-108">SQL_POSITION</span><span class="sxs-lookup"><span data-stu-id="138d0-108">SQL_POSITION</span></span>  
 <span data-ttu-id="138d0-109">將資料指標置於目前資料列集的特定資料列中。</span><span class="sxs-lookup"><span data-stu-id="138d0-109">Positions the cursor on a specific row in the current rowset.</span></span>  
  
 <span data-ttu-id="138d0-110">SQL_REFRESH</span><span class="sxs-lookup"><span data-stu-id="138d0-110">SQL_REFRESH</span></span>  
 <span data-ttu-id="138d0-111">以資料指標目前所在位置之資料列中的值，重新整理繫結至結果集資料行的程式變數。</span><span class="sxs-lookup"><span data-stu-id="138d0-111">Refreshes program variables bound to the result set columns with the values from the row the cursor is currently positioned on.</span></span>  
  
 <span data-ttu-id="138d0-112">SQL_UPDATE</span><span class="sxs-lookup"><span data-stu-id="138d0-112">SQL_UPDATE</span></span>  
 <span data-ttu-id="138d0-113">以繫結至結果集資料行之程式變數中儲存的值，更新資料指標中的目前資料列。</span><span class="sxs-lookup"><span data-stu-id="138d0-113">Updates the current row in the cursor with the values stored in the program variables bound to the result set columns.</span></span>  
  
 <span data-ttu-id="138d0-114">SQL_DELETE</span><span class="sxs-lookup"><span data-stu-id="138d0-114">SQL_DELETE</span></span>  
 <span data-ttu-id="138d0-115">刪除資料指標中的目前資料行。</span><span class="sxs-lookup"><span data-stu-id="138d0-115">Deletes the current row in the cursor.</span></span>  
  
 <span data-ttu-id="138d0-116">當語句控制碼資料指標屬性設定為使用伺服器資料指標時， **SQLSetPos**可以與任何語句結果集搭配使用。</span><span class="sxs-lookup"><span data-stu-id="138d0-116">**SQLSetPos** can be used with any statement result set when the statement handle cursor attributes are set to use server cursors.</span></span> <span data-ttu-id="138d0-117">結果集資料行必須繫結至程式變數。</span><span class="sxs-lookup"><span data-stu-id="138d0-117">The result set columns must be bound to program variables.</span></span> <span data-ttu-id="138d0-118">一旦應用程式提取資料列，它就會呼叫**SQLSetPos** (SQL_POSTION) 將游標放在資料列上。</span><span class="sxs-lookup"><span data-stu-id="138d0-118">As soon as the application has fetched a row it calls **SQLSetPos**(SQL_POSTION) to position the cursor on the row.</span></span> <span data-ttu-id="138d0-119">然後應用程式可以呼叫 SQLSetPos(SQL_DELETE) 來刪除目前的資料列，或者可以將新的資料值移到繫結的程式變數中，並呼叫 SQLSetPos(SQL_UPDATE) 來更新目前的資料列。</span><span class="sxs-lookup"><span data-stu-id="138d0-119">The application could then call SQLSetPos(SQL_DELETE) to delete the current row, or it can move new data values into the bound program variables and call SQLSetPos(SQL_UPDATE) to update the current row.</span></span>  
  
 <span data-ttu-id="138d0-120">應用程式可以使用**SQLSetPos**來更新或刪除資料列集中的任何資料列。</span><span class="sxs-lookup"><span data-stu-id="138d0-120">Applications can update or delete any row in the rowset with **SQLSetPos**.</span></span> <span data-ttu-id="138d0-121">呼叫**SQLSetPos**是用來建立和執行 SQL 語句的方便替代方式。</span><span class="sxs-lookup"><span data-stu-id="138d0-121">Calling **SQLSetPos** is a convenient alternative to constructing and executing an SQL statement.</span></span> <span data-ttu-id="138d0-122">**SQLSetPos**會在目前的資料列集上運作，而且只能在呼叫[SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md)之後使用。</span><span class="sxs-lookup"><span data-stu-id="138d0-122">**SQLSetPos** operates on the current rowset and can be used only after a call to [SQLFetchScroll](../native-client-odbc-api/sqlfetchscroll.md).</span></span>  
  
 <span data-ttu-id="138d0-123">資料列集大小是透過 SQL_ATTR_ROW_ARRAY_SIZE 的屬性引數呼叫[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)所設定。</span><span class="sxs-lookup"><span data-stu-id="138d0-123">Rowset size is set by a call to [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) with an attribute argument of SQL_ATTR_ROW_ARRAY_SIZE.</span></span> <span data-ttu-id="138d0-124">**SQLSetPos**會使用新的資料列集大小，但只會在呼叫**SQLFetch**或**SQLFetchScroll**之後。</span><span class="sxs-lookup"><span data-stu-id="138d0-124">**SQLSetPos** uses a new rowset size, but only after a call to **SQLFetch** or **SQLFetchScroll**.</span></span> <span data-ttu-id="138d0-125">例如，如果資料列集大小已變更，則會呼叫**SQLSetPos** ，然後呼叫**SQLFetch**或**SQLFetchScroll** 。</span><span class="sxs-lookup"><span data-stu-id="138d0-125">For example, if the rowset size is changed, **SQLSetPos** is called and then **SQLFetch** or **SQLFetchScroll** is called.</span></span> <span data-ttu-id="138d0-126">對**SQLSetPos**的呼叫會使用舊的資料列集大小，但是**SQLFetch**或**SQLFetchScroll**會使用新的資料列集大小。</span><span class="sxs-lookup"><span data-stu-id="138d0-126">The call to **SQLSetPos** uses the old rowset size, but **SQLFetch** or **SQLFetchScroll** uses the new rowset size.</span></span>  
  
 <span data-ttu-id="138d0-127">資料列集中的第一個資料列是資料列號碼 1。</span><span class="sxs-lookup"><span data-stu-id="138d0-127">The first row in the rowset is row number 1.</span></span> <span data-ttu-id="138d0-128">**SQLSetPos**中的 RowNumber 引數必須識別資料列集中的資料列;也就是說，其值必須介於1到最近提取的資料列數目的範圍內。</span><span class="sxs-lookup"><span data-stu-id="138d0-128">The RowNumber argument in **SQLSetPos** must identify a row in the rowset; that is, its value must be in the range between 1 and the number of rows that were most recently fetched.</span></span> <span data-ttu-id="138d0-129">這可能會小於資料列集大小。</span><span class="sxs-lookup"><span data-stu-id="138d0-129">This may be less than the rowset size.</span></span> <span data-ttu-id="138d0-130">如果 RowNumber 是 0，此作業會套用到資料列集內的每一個資料列。</span><span class="sxs-lookup"><span data-stu-id="138d0-130">If RowNumber is 0, the operation applies to every row in the rowset.</span></span>  
  
 <span data-ttu-id="138d0-131">**SQLSetPos**的 delete 作業會使資料來源刪除資料表的一個或多個選取資料列。</span><span class="sxs-lookup"><span data-stu-id="138d0-131">The delete operation of **SQLSetPos** makes the data source delete one or more selected rows of a table.</span></span> <span data-ttu-id="138d0-132">若要使用**SQLSetPos**刪除資料列，應用程式會呼叫**SQLSetPos** ，並將 Operation 設定為 SQL_DELETE 並將 RowNumber 設定為要刪除的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="138d0-132">To delete rows with **SQLSetPos**, the application calls **SQLSetPos** with Operation set to SQL_DELETE and RowNumber set to the number of the row to delete.</span></span> <span data-ttu-id="138d0-133">如果 RowNumber 是 0，將會刪除資料列集內的所有資料列。</span><span class="sxs-lookup"><span data-stu-id="138d0-133">If RowNumber is 0, all rows in the rowset are deleted.</span></span>  
  
 <span data-ttu-id="138d0-134">**SQLSetPos**傳回之後，刪除的資料列就是目前的資料列，而且其狀態會是 SQL_ROW_DELETED。</span><span class="sxs-lookup"><span data-stu-id="138d0-134">After **SQLSetPos** returns, the deleted row is the current row and its status is SQL_ROW_DELETED.</span></span> <span data-ttu-id="138d0-135">資料列不能用於任何其他定位作業，例如呼叫[SQLGetData](../native-client-odbc-api/sqlgetdata.md)或**SQLSetPos**。</span><span class="sxs-lookup"><span data-stu-id="138d0-135">The row cannot be used in any additional positioned operations, such as calls to [SQLGetData](../native-client-odbc-api/sqlgetdata.md) or **SQLSetPos**.</span></span>  
  
 <span data-ttu-id="138d0-136">當您刪除資料列集的所有資料列時 (RowNumber 等於 0) ，應用程式可以使用資料列作業陣列，讓驅動程式無法刪除某些資料列，就像**SQLSetPos**的更新作業一樣。</span><span class="sxs-lookup"><span data-stu-id="138d0-136">When you delete all rows of the rowset (RowNumber is equal to 0), the application can prevent the driver from deleting certain rows by using the row operation array just like for the update operation of **SQLSetPos**.</span></span>  
  
 <span data-ttu-id="138d0-137">刪除的每一個資料列都應該是存在於結果集內的資料列。</span><span class="sxs-lookup"><span data-stu-id="138d0-137">Every row that is deleted should be a row that exists in the result set.</span></span> <span data-ttu-id="138d0-138">如果應用程式緩衝區已藉由提取來填滿，而且已經維護資料列狀態陣列，則它在每一個資料列位置的值都不應該是 SQL_ROW_DELETED、SQL_ROW_ERROR 或 SQL_ROW_NOROW。</span><span class="sxs-lookup"><span data-stu-id="138d0-138">If the application buffers were filled by fetching, and if a row status array has been maintained, its values at each of these row positions should not be SQL_ROW_DELETED, SQL_ROW_ERROR, or SQL_ROW_NOROW.</span></span>  
  
 <span data-ttu-id="138d0-139">定位更新也可以使用 UPDATE、DELETE 和 INSERT 陳述式上的 WHERE CURRENT OF 子句來執行。</span><span class="sxs-lookup"><span data-stu-id="138d0-139">Positioned updates can also be performed using the WHERE CURRENT OF clause on UPDATE, DELETE, and INSERT statements.</span></span> <span data-ttu-id="138d0-140">其中 CURRENT 的需要資料指標名稱，ODBC 將在呼叫[SQLGetCursorName](../native-client-odbc-api/sqlgetcursorname.md)函式時產生，或藉由呼叫**SQLSetCursorName**來指定。</span><span class="sxs-lookup"><span data-stu-id="138d0-140">WHERE CURRENT OF requires a cursor name that ODBC will generate when the [SQLGetCursorName](../native-client-odbc-api/sqlgetcursorname.md) function is called, or which you can specify by calling **SQLSetCursorName**.</span></span> <span data-ttu-id="138d0-141">下列是用來在 ODBC 應用程式內執行 WHERE CURRENT OF 更新的一般步驟：</span><span class="sxs-lookup"><span data-stu-id="138d0-141">The following are general steps used to perform a WHERE CURRENT OF update in an ODBC application:</span></span>  
  
-   <span data-ttu-id="138d0-142">呼叫**SQLSetCursorName**以建立語句控制碼的資料指標名稱。</span><span class="sxs-lookup"><span data-stu-id="138d0-142">Call **SQLSetCursorName** to establish a cursor name for the statement handle.</span></span>  
  
-   <span data-ttu-id="138d0-143">建立包含 FOR UPDATE OF 子句的 SELECT 陳述式，並加以執行。</span><span class="sxs-lookup"><span data-stu-id="138d0-143">Build a SELECT statement with a FOR UPDATE OF clause and execute it.</span></span>  
  
-   <span data-ttu-id="138d0-144">呼叫**SQLFetchScroll**來抓取資料列集或**SQLFetch** ，以取得資料列。</span><span class="sxs-lookup"><span data-stu-id="138d0-144">Call **SQLFetchScroll** to retrieve a rowset or **SQLFetch** to retrieve a row.</span></span>  
  
-   <span data-ttu-id="138d0-145">呼叫**SQLSetPos** (SQL_POSITION) ，將游標放在資料列上。</span><span class="sxs-lookup"><span data-stu-id="138d0-145">Call **SQLSetPos** (SQL_POSITION) to position the cursor on the row.</span></span>  
  
-   <span data-ttu-id="138d0-146">使用以**SQLSetCursorName**設定的資料指標名稱，建立並執行含有 WHERE CURRENT of 子句的 UPDATE 語句。</span><span class="sxs-lookup"><span data-stu-id="138d0-146">Build and execute an UPDATE statement with a WHERE CURRENT OF clause using the cursor name set with **SQLSetCursorName**.</span></span>  
  
 <span data-ttu-id="138d0-147">或者，您可以在執行 SELECT 語句後呼叫**SQLGetCursorName** ，而不是在執行 select 語句之前呼叫**SQLSetCursorName** 。</span><span class="sxs-lookup"><span data-stu-id="138d0-147">Alternatively, you could call **SQLGetCursorName** after you execute the SELECT statement instead of calling **SQLSetCursorName** before executing the SELECT statement.</span></span> <span data-ttu-id="138d0-148">如果您未使用**SQLSetCursorName**來設定資料指標名稱，則**SQLGETCURSORNAME**會傳回 ODBC 指派的預設資料指標名稱。</span><span class="sxs-lookup"><span data-stu-id="138d0-148">**SQLGetCursorName** returns a default cursor name assigned by ODBC if you do not set a cursor name using **SQLSetCursorName**.</span></span>  
  
 <span data-ttu-id="138d0-149">當您使用伺服器資料指標時， **SQLSetPos**會優先于目前的。</span><span class="sxs-lookup"><span data-stu-id="138d0-149">**SQLSetPos** is preferred over WHERE CURRENT OF when you are using server cursors.</span></span> <span data-ttu-id="138d0-150">如果您搭配 ODBC 資料指標程式庫使用可更新的靜態資料指標，此資料指標程式庫會實作 WHERE CURRENT OF 更新，其方式是針對基礎資料表加入具有索引鍵值的 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="138d0-150">If you are using a static, updatable cursor with the ODBC cursor library, the cursor library implements WHERE CURRENT OF updates by adding a WHERE clause with the key values for the underlying table.</span></span> <span data-ttu-id="138d0-151">如果資料表內的索引鍵不是唯一的，這樣會造成非預期的更新。</span><span class="sxs-lookup"><span data-stu-id="138d0-151">This can cause unintended updates if the keys in the table are not unique.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="138d0-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="138d0-152">See Also</span></span>  
 [<span data-ttu-id="138d0-153">&#40;ODBC&#41;使用資料指標</span><span class="sxs-lookup"><span data-stu-id="138d0-153">Using Cursors &#40;ODBC&#41;</span></span>](using-cursors-odbc.md)  
  
  
