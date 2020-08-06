---
title: 資料指標資料列集大小 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], rowset size
- ODBC cursors, rowset size
- rowsets [ODBC]
ms.assetid: 2febe2ae-fdc1-490e-a79f-c516bc8e7c3f
author: rothja
ms.author: jroth
ms.openlocfilehash: 83c4e55025e6e3724f354f022760b7ba1e2f10e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598336"
---
# <a name="cursor-rowset-size"></a><span data-ttu-id="5b032-102">資料指標資料列集大小</span><span class="sxs-lookup"><span data-stu-id="5b032-102">Cursor Rowset Size</span></span>
  <span data-ttu-id="5b032-103">ODBC 資料指標不限制為一次只能提取一個資料列。</span><span class="sxs-lookup"><span data-stu-id="5b032-103">ODBC cursors are not limited to fetching one row at a time.</span></span> <span data-ttu-id="5b032-104">他們可以在每次呼叫**SQLFetch**或[SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md)時，抓取多個資料列。</span><span class="sxs-lookup"><span data-stu-id="5b032-104">They can retrieve multiple rows in each call to **SQLFetch** or [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md).</span></span> <span data-ttu-id="5b032-105">與 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 之類的用戶端/伺服器資料庫搭配使用時，一次擷取數個資料列會更有效率。</span><span class="sxs-lookup"><span data-stu-id="5b032-105">When you are working with a client/server database such as Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], it is more efficient to fetch several rows at a time.</span></span> <span data-ttu-id="5b032-106">提取所傳回的資料列數目稱為資料列集大小，並使用[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)的 SQL_ATTR_ROW_ARRAY_SIZE 來指定。</span><span class="sxs-lookup"><span data-stu-id="5b032-106">The number of rows returned on a fetch is called the rowset size and is specified by using the SQL_ATTR_ROW_ARRAY_SIZE of [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md).</span></span>  
  
```  
SQLUINTEGER uwRowsize;  
SQLSetStmtAttr(m_hstmt, SQL_ATTR_ROW_ARRAY_SIZE, (SQLPOINTER)uwRowsetSize, SQL_IS_UINTEGER);  
```  
  
 <span data-ttu-id="5b032-107">資料列集大小大於 1 的資料指標稱為區塊資料指標。</span><span class="sxs-lookup"><span data-stu-id="5b032-107">Cursors with a rowset size greater than 1 are called block cursors.</span></span>  
  
 <span data-ttu-id="5b032-108">有兩個選項可用來繫結區塊資料指標的結果集資料行：</span><span class="sxs-lookup"><span data-stu-id="5b032-108">There are two options for binding result set columns for block cursors:</span></span>  
  
-   <span data-ttu-id="5b032-109">資料行取向的繫結</span><span class="sxs-lookup"><span data-stu-id="5b032-109">Column-wise binding</span></span>  
  
     <span data-ttu-id="5b032-110">每個資料行都會繫結至變數的陣列。</span><span class="sxs-lookup"><span data-stu-id="5b032-110">Each column is bound to an array of variables.</span></span> <span data-ttu-id="5b032-111">每個陣列所擁有的元素數目則都與資料列集大小相當。</span><span class="sxs-lookup"><span data-stu-id="5b032-111">Each array has the same number of elements as the rowset size.</span></span>  
  
-   <span data-ttu-id="5b032-112">資料列取向的繫結</span><span class="sxs-lookup"><span data-stu-id="5b032-112">Row-wise binding</span></span>  
  
     <span data-ttu-id="5b032-113">陣列是使用保存資料列中所有資料行之資料和指標的結構而建立。</span><span class="sxs-lookup"><span data-stu-id="5b032-113">An array is built using structures that hold the data and indicators for all the columns in a row.</span></span> <span data-ttu-id="5b032-114">陣列所擁有的結構數目與資料列集大小相當。</span><span class="sxs-lookup"><span data-stu-id="5b032-114">The array has the same number of structures as the rowset size.</span></span>  
  
 <span data-ttu-id="5b032-115">使用資料行取向或資料列取向的系結時，每次呼叫**SQLFetch**或**SQLFetchScroll**時，都會以所抓取之資料列集的資料來填入系結陣列。</span><span class="sxs-lookup"><span data-stu-id="5b032-115">When either column-wise or row-wise binding is used, each call to **SQLFetch** or **SQLFetchScroll** fills the bound arrays with data from the rowset retrieved.</span></span>  
  
 <span data-ttu-id="5b032-116">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md)也可以用來從區塊資料指標取出資料行資料。</span><span class="sxs-lookup"><span data-stu-id="5b032-116">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) can also be used to retrieve column data from a block cursor.</span></span> <span data-ttu-id="5b032-117">由於**SQLGetData**會一次處理一個資料列，因此在呼叫**SQLGetData**之前，必須先呼叫**SQLSetPos** ，將資料列集中的特定資料列設定為目前的資料列。</span><span class="sxs-lookup"><span data-stu-id="5b032-117">Because **SQLGetData** works one row at a time, **SQLSetPos** must be called to set a specific row in the rowset as the current row before calling **SQLGetData**.</span></span>  
  
 <span data-ttu-id="5b032-118">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式會使用資料列集來提供優化，以快速取得整個結果集。</span><span class="sxs-lookup"><span data-stu-id="5b032-118">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver offers an optimization using rowsets to retrieve a whole result set quickly.</span></span> <span data-ttu-id="5b032-119">若要使用此優化，請在呼叫**SQLExecDirect**或**SQLExecute**時，將資料指標屬性設定為預設值 (順向、唯讀、資料列集大小 = 1) 。</span><span class="sxs-lookup"><span data-stu-id="5b032-119">To use this optimization, set the cursor attributes to their defaults (forward-only, read-only, rowset size = 1) at the time **SQLExecDirect** or **SQLExecute** is called.</span></span> <span data-ttu-id="5b032-120">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式會設定預設的結果集。</span><span class="sxs-lookup"><span data-stu-id="5b032-120">The [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver sets up a default result set.</span></span> <span data-ttu-id="5b032-121">若要在不捲動的情況下將結果傳送到用戶端時，這種做法比伺服器資料指標有效率。</span><span class="sxs-lookup"><span data-stu-id="5b032-121">This is more efficient than server cursors when transferring results to the client without scrolling.</span></span> <span data-ttu-id="5b032-122">在執行陳述式之後，請增加資料列集大小，並使用資料行取向或資料列取向的繫結。</span><span class="sxs-lookup"><span data-stu-id="5b032-122">After the statement has been executed, increase the rowset size and use either column-wise or row-wise binding.</span></span> <span data-ttu-id="5b032-123">這可讓您 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] 使用預設結果集，將結果資料列有效率地傳送給用戶端，而 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE client ODBC 驅動程式會從用戶端上的網路緩衝區持續提取資料列。</span><span class="sxs-lookup"><span data-stu-id="5b032-123">This lets [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] use a default result set to send result rows efficiently to the client, while the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver continuously pulls rows from the network buffers on the client.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b032-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5b032-124">See Also</span></span>  
 [<span data-ttu-id="5b032-125">資料指標屬性</span><span class="sxs-lookup"><span data-stu-id="5b032-125">Cursor Properties</span></span>](cursor-properties.md)  
  
  
