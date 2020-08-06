---
title: " (ODBC) 的快速順向資料指標 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- fast forward-only cursors
- forward-only cursors
- cursors [ODBC], fast forward-only
- ODBC cursors, fast forward-only
ms.assetid: 0707d07e-fc95-42ed-9280-b7e508ac8c62
author: rothja
ms.author: jroth
ms.openlocfilehash: de8d82a0c72ad51741a3785fba2910f691028cba
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598349"
---
# <a name="fast-forward-only-cursors-odbc"></a><span data-ttu-id="99be7-102">快速順向資料指標 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="99be7-102">Fast Forward-Only Cursors (ODBC)</span></span>
  <span data-ttu-id="99be7-103">當連接到的實例時 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] ， [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] NATIVE Client ODBC 驅動程式支援順向、唯讀資料指標的效能優化。</span><span class="sxs-lookup"><span data-stu-id="99be7-103">When connected to an instance of [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)], the [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client ODBC driver supports performance optimizations for forward-only, read-only cursors.</span></span> <span data-ttu-id="99be7-104">快速順向資料指標是由驅動程式和伺服器以非常類似於預設結果集的方式在內部實作。</span><span class="sxs-lookup"><span data-stu-id="99be7-104">Fast forward-only cursors are implemented internally by the driver and server in a manner very similar to default result sets.</span></span> <span data-ttu-id="99be7-105">除了具有高效能以外，快速順向資料指標還具有下列特性：</span><span class="sxs-lookup"><span data-stu-id="99be7-105">Besides having high performance, fast forward-only cursors also have these characteristics:</span></span>  
  
-   <span data-ttu-id="99be7-106">不支援[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) 。</span><span class="sxs-lookup"><span data-stu-id="99be7-106">[SQLGetData](../../native-client-odbc-api/sqlgetdata.md) is not supported.</span></span> <span data-ttu-id="99be7-107">結果集資料行必須繫結至程式變數。</span><span class="sxs-lookup"><span data-stu-id="99be7-107">The result set columns must be bound to program variables.</span></span>  
  
-   <span data-ttu-id="99be7-108">偵測到資料指標的結尾時，伺服器就會自動關閉資料指標。</span><span class="sxs-lookup"><span data-stu-id="99be7-108">The server automatically closes the cursor when the end of the cursor is detected.</span></span> <span data-ttu-id="99be7-109">應用程式仍然必須呼叫[SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md)或[SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md) (SQL_CLOSE) ，但驅動程式不需要將關閉要求傳送至伺服器。</span><span class="sxs-lookup"><span data-stu-id="99be7-109">The application must still call [SQLCloseCursor](../../native-client-odbc-api/sqlclosecursor.md) or [SQLFreeStmt](../../native-client-odbc-api/sqlfreestmt.md)(SQL_CLOSE), but the driver does not have to send the close request to the server.</span></span> <span data-ttu-id="99be7-110">這樣可節省透過網路與伺服器之間的往返。</span><span class="sxs-lookup"><span data-stu-id="99be7-110">This saves a roundtrip across the network to the server.</span></span>  
  
 <span data-ttu-id="99be7-111">應用程式會使用驅動程式特有的陳述式屬性 SQL_SOPT_SS_CURSOR_OPTIONS 來要求快速順向資料指標。</span><span class="sxs-lookup"><span data-stu-id="99be7-111">The application requests fast forward-only cursors using the driver-specific statement attribute SQL_SOPT_SS_CURSOR_OPTIONS.</span></span> <span data-ttu-id="99be7-112">設定為 SQL_CO_FFO 時，就會啟用快速順向資料指標，但不啟用自動擷取。</span><span class="sxs-lookup"><span data-stu-id="99be7-112">When set to SQL_CO_FFO, fast forward-only cursors are enabled without autofetch.</span></span> <span data-ttu-id="99be7-113">設定為 SQL_CO_FFO_AF 時，則會一併啟用自動擷取選項。</span><span class="sxs-lookup"><span data-stu-id="99be7-113">When set to SQL_CO_FFO_AF, the autofetch option is also enabled.</span></span> <span data-ttu-id="99be7-114">如需自動擷取的詳細資訊，請參閱搭配[ODBC 資料指標使用自動擷取](using-autofetch-with-odbc-cursors.md)。</span><span class="sxs-lookup"><span data-stu-id="99be7-114">For more information about autofetch, see [Using Autofetch with ODBC Cursors](using-autofetch-with-odbc-cursors.md).</span></span>  
  
 <span data-ttu-id="99be7-115">包含自動擷取的快速順向資料指標可用來透過與伺服器之間的一次往返，擷取小型結果集。</span><span class="sxs-lookup"><span data-stu-id="99be7-115">Fast forward-only cursors with autofetch can be used to retrieve a small result set with only one roundtrip to the server.</span></span> <span data-ttu-id="99be7-116">在這些步驟中， *n*是要傳回的資料列數目：</span><span class="sxs-lookup"><span data-stu-id="99be7-116">In these steps, *n* is the number of rows to be returned:</span></span>  
  
1.  <span data-ttu-id="99be7-117">將 SQL_SOPT_SS_CURSOR_OPTIONS 設定為 SQL_CO_FFO_AF。</span><span class="sxs-lookup"><span data-stu-id="99be7-117">Set SQL_SOPT_SS_CURSOR_OPTIONS to SQL_CO_FFO_AF.</span></span>  
  
2.  <span data-ttu-id="99be7-118">將 SQL_ATTR_ROW_ARRAY_SIZE 設定為*n* + 1。</span><span class="sxs-lookup"><span data-stu-id="99be7-118">Set SQL_ATTR_ROW_ARRAY_SIZE to *n* + 1.</span></span>  
  
3.  <span data-ttu-id="99be7-119">將結果資料行系結至*n* + 1 個元素的陣列 (在) 實際提取*n* + 1 個數據列時，都是安全的。</span><span class="sxs-lookup"><span data-stu-id="99be7-119">Bind the result columns to arrays of *n* + 1 elements (to be safe if *n* + 1 rows are actually fetched).</span></span>  
  
4.  <span data-ttu-id="99be7-120">使用**SQLExecDirect**或**SQLExecute**開啟資料指標。</span><span class="sxs-lookup"><span data-stu-id="99be7-120">Open the cursor with either **SQLExecDirect** or **SQLExecute**.</span></span>  
  
5.  <span data-ttu-id="99be7-121">如果傳回狀態為 SQL_SUCCESS，則呼叫**SQLFreeStmt**或**SQLCloseCursor**來關閉資料指標。</span><span class="sxs-lookup"><span data-stu-id="99be7-121">If the return status is SQL_SUCCESS, then call **SQLFreeStmt** or **SQLCloseCursor** to close the cursor.</span></span> <span data-ttu-id="99be7-122">資料列的所有資料都將位於繫結的程式變數中。</span><span class="sxs-lookup"><span data-stu-id="99be7-122">All data for the rows will be in the bound program variables.</span></span>  
  
 <span data-ttu-id="99be7-123">透過這些步驟， **SQLExecDirect**或**SQLExecute**會傳送已啟用自動擷取選項的資料指標開啟要求。</span><span class="sxs-lookup"><span data-stu-id="99be7-123">With these steps, the **SQLExecDirect** or **SQLExecute** sends a cursor open request with the autofetch option enabled.</span></span> <span data-ttu-id="99be7-124">在收到來自用戶端的單一要求時，伺服器會：</span><span class="sxs-lookup"><span data-stu-id="99be7-124">On that single request from the client, the server:</span></span>  
  
-   <span data-ttu-id="99be7-125">開啟資料指標。</span><span class="sxs-lookup"><span data-stu-id="99be7-125">Opens the cursor.</span></span>  
  
-   <span data-ttu-id="99be7-126">建立結果集並將資料列傳送至用戶端。</span><span class="sxs-lookup"><span data-stu-id="99be7-126">Builds the result set and sends the rows to the client.</span></span>  
  
-   <span data-ttu-id="99be7-127">由於資料列集大小設定為結果集的資料列數目加上 1，所以伺服器會偵測資料指標的結尾並關閉資料指標。</span><span class="sxs-lookup"><span data-stu-id="99be7-127">Because the rowset size was set to 1 more than the number of rows in the result set, the server detects the end of the cursor and closes the cursor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99be7-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="99be7-128">See Also</span></span>  
 [<span data-ttu-id="99be7-129">ODBC&#41;&#40;的資料指標程式設計詳細資料</span><span class="sxs-lookup"><span data-stu-id="99be7-129">Cursor Programming Details &#40;ODBC&#41;</span></span>](cursor-programming-details-odbc.md)  
  
  
