---
title: " (ODBC) 設定資料指標選項 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], options
ms.assetid: 0e72b48a-fc5a-4656-8cf5-39f57d8c1565
author: rothja
ms.author: jroth
ms.openlocfilehash: 877c2596c87ce50295a15912493661c6dd4e0305
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707486"
---
# <a name="set-cursor-options-odbc"></a><span data-ttu-id="a8ee9-102">設定資料指標選項 (ODBC)</span><span class="sxs-lookup"><span data-stu-id="a8ee9-102">Set Cursor Options (ODBC)</span></span>
  <span data-ttu-id="a8ee9-103">若要設定資料指標選項，請呼叫[SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md)來設定或[SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) ，以取得控制資料指標行為的語句選項。</span><span class="sxs-lookup"><span data-stu-id="a8ee9-103">To set cursor options, Call [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) to set or [SQLGetStmtAttr](../../native-client-odbc-api/sqlgetstmtattr.md) to get the statement options that control cursor behavior.</span></span>  
  
|<span data-ttu-id="a8ee9-104">*屬性*</span><span class="sxs-lookup"><span data-stu-id="a8ee9-104">*Attribute*</span></span>|<span data-ttu-id="a8ee9-105">指定</span><span class="sxs-lookup"><span data-stu-id="a8ee9-105">Specifies</span></span>|  
|-----------------|---------------|  
|<span data-ttu-id="a8ee9-106">SQL_ATTR_CURSOR_TYPE</span><span class="sxs-lookup"><span data-stu-id="a8ee9-106">SQL_ATTR_CURSOR_TYPE</span></span>|<span data-ttu-id="a8ee9-107">順向、靜態、動態或索引鍵集驅動的資料指標類型</span><span class="sxs-lookup"><span data-stu-id="a8ee9-107">Cursor type of forward-only, static, dynamic, or keyset-driven</span></span>|  
|<span data-ttu-id="a8ee9-108">SQL_ATTR_CONCURRENCY</span><span class="sxs-lookup"><span data-stu-id="a8ee9-108">SQL_ATTR_CONCURRENCY</span></span>|<span data-ttu-id="a8ee9-109">唯讀、鎖定、開放式 (使用時間戳記) 或開放式 (使用值) 的並行控制選項</span><span class="sxs-lookup"><span data-stu-id="a8ee9-109">Concurrency control option of read-only, locking, optimistic using timestamps, or optimistic using values</span></span>|  
|<span data-ttu-id="a8ee9-110">SQL_ATTR_ROW_ARRAY_SIZE</span><span class="sxs-lookup"><span data-stu-id="a8ee9-110">SQL_ATTR_ROW_ARRAY_SIZE</span></span>|<span data-ttu-id="a8ee9-111">每次提取中擷取的資料列數目</span><span class="sxs-lookup"><span data-stu-id="a8ee9-111">Number of rows retrieved in each fetch</span></span>|  
|<span data-ttu-id="a8ee9-112">SQL_ATTR_CURSOR_SENSITIVITY</span><span class="sxs-lookup"><span data-stu-id="a8ee9-112">SQL_ATTR_CURSOR_SENSITIVITY</span></span>|<span data-ttu-id="a8ee9-113">顯示或不顯示其他連接對資料指標資料列所做之更新的資料指標</span><span class="sxs-lookup"><span data-stu-id="a8ee9-113">Cursor that does or does not show updates to cursor rows made by other connections</span></span>|  
|<span data-ttu-id="a8ee9-114">SQL_ATTR_CURSOR_SCROLLABLE</span><span class="sxs-lookup"><span data-stu-id="a8ee9-114">SQL_ATTR_CURSOR_SCROLLABLE</span></span>|<span data-ttu-id="a8ee9-115">可以前後捲動的資料指標</span><span class="sxs-lookup"><span data-stu-id="a8ee9-115">Cursor that can be scrolled forward and backward</span></span>|  
  
 <span data-ttu-id="a8ee9-116">這些屬性 (順向、唯讀、資料列集大小為 1) 的預設值不會使用伺服器資料指標。</span><span class="sxs-lookup"><span data-stu-id="a8ee9-116">The default values for these attributes (forward-only, read-only, rowset size of 1) do not use server cursors.</span></span> <span data-ttu-id="a8ee9-117">若要使用伺服器資料指標，至少其中一個屬性必須設定為預設值以外的值，而且所執行的陳述式必須為單一 SELECT 陳述式或包含單一 SELECT 陳述式的預存程序。</span><span class="sxs-lookup"><span data-stu-id="a8ee9-117">To use server cursors, at least one of these attributes must be set to a value other than the default, and the statement being executed must be a single SELECT statement or a stored procedure that contains a single SELECT statement.</span></span> <span data-ttu-id="a8ee9-118">使用伺服器資料指標時，SELECT 陳述式無法使用伺服器資料指標不支援的子句：COMPUTE、COMPUTE BY、FOR BROWSE 和 INTO。</span><span class="sxs-lookup"><span data-stu-id="a8ee9-118">When using server cursors, SELECT statements cannot use clauses not supported by server cursors: COMPUTE, COMPUTE BY, FOR BROWSE, and INTO.</span></span>  
  
 <span data-ttu-id="a8ee9-119">您可以透過設定 SQL_ATTR_CURSOR_TYPE 和 SQL_ATTR_CONCURRENCY，或是設定 SQL_ATTR_CURSOR_SENSITIVITY 和 SQL_ATTR_CURSOR_SCROLLABLE，控制所使用的資料指標類型。</span><span class="sxs-lookup"><span data-stu-id="a8ee9-119">You can control the type of cursor used either by setting SQL_ATTR_CURSOR_TYPE and SQL_ATTR_CONCURRENCY, or by setting SQL_ATTR_CURSOR_SENSITIVITY and SQL_ATTR_CURSOR_SCROLLABLE.</span></span> <span data-ttu-id="a8ee9-120">您不應該混合使用這兩種指定資料指標行為的方法。</span><span class="sxs-lookup"><span data-stu-id="a8ee9-120">You should not mix the two methods of specifying cursor behavior.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8ee9-121">範例</span><span class="sxs-lookup"><span data-stu-id="a8ee9-121">Example</span></span>  
 <span data-ttu-id="a8ee9-122">下列範例會配置陳述式控制代碼、使用資料列版本設定開放式並行存取來設定動態資料指標類型，然後執行 SELECT。</span><span class="sxs-lookup"><span data-stu-id="a8ee9-122">The following sample allocates a statement handle, sets a dynamic cursor type with row versioning optimistic concurrency, and then executes a SELECT.</span></span>  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_TYPE, (SQLPOINTER)SQL_CURSOR_DYNAMIC, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CONCURRENCY, SQLPOINTER)SQL_CONCUR_ROWVER, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, SELECT au_lname FROM authors", SQL_NTS);  
```  
  
## <a name="example"></a><span data-ttu-id="a8ee9-123">範例</span><span class="sxs-lookup"><span data-stu-id="a8ee9-123">Example</span></span>  
 <span data-ttu-id="a8ee9-124">下列範例會配置陳述式控制代碼、設定可捲動的感應式資料指標，然後執行 SELECT。</span><span class="sxs-lookup"><span data-stu-id="a8ee9-124">The following sample allocates a statement handle, sets a scrollable, sensitive cursor, and then executes a SELECT</span></span>  
  
```  
retcode = SQLAllocHandle(SQL_HANDLE_STMT, hdbc1, &hstmt1);  
  
// Set the cursor options and execute the statement.  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SCROLLABLE, SQLPOINTER)SQL_SCROLLABLE, SQL_IS_INTEGER);  
retcode = SQLSetStmtAttr(hstmt1, SQL_ATTR_CURSOR_SENSITIVITY, SQLPOINTER)SQL_INSENSITIVE, SQL_IS_INTEGER);  
retcode = SQLExecDirect(hstmt1, select au_lname from authors", SQL_NTS);  
```  
  
## <a name="see-also"></a><span data-ttu-id="a8ee9-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a8ee9-125">See Also</span></span>  
 [<span data-ttu-id="a8ee9-126">執行查詢 &#40;ODBC&#41;的使用說明主題</span><span class="sxs-lookup"><span data-stu-id="a8ee9-126">Executing Queries How-to Topics &#40;ODBC&#41;</span></span>](executing-queries-how-to-topics-odbc.md)  
  
  
