---
title: 為數據指標建立 SQL 語句 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], statement construction
- ODBC applications, cursors
- SQL Server Native Client ODBC driver, statements
- statements [ODBC], constructing
- ODBC applications, statements
- statements [ODBC], cursors
ms.assetid: 134003fd-9c93-4f5c-a988-045990933b80
author: rothja
ms.author: jroth
ms.openlocfilehash: b0fe0831b97c13c5d20067386f4e9d8c97ee19ed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585363"
---
# <a name="constructing-sql-statements-for-cursors"></a><span data-ttu-id="a611c-102">建構資料指標的 SQL 陳述式</span><span class="sxs-lookup"><span data-stu-id="a611c-102">Constructing SQL Statements for Cursors</span></span>
  <span data-ttu-id="a611c-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式會使用伺服器資料指標來執行 ODBC 規格中所定義的資料指標功能。</span><span class="sxs-lookup"><span data-stu-id="a611c-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver uses server cursors to implement the cursor functionality defined in the ODBC specification.</span></span> <span data-ttu-id="a611c-104">ODBC 應用程式會使用[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)來設定不同的語句屬性，以控制資料指標的行為。</span><span class="sxs-lookup"><span data-stu-id="a611c-104">An ODBC application controls the cursor behavior by using [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) to set different statement attributes.</span></span> <span data-ttu-id="a611c-105">下面是這些屬性及其預設值。</span><span class="sxs-lookup"><span data-stu-id="a611c-105">These are the attributes and their defaults.</span></span>  
  
|<span data-ttu-id="a611c-106">屬性</span><span class="sxs-lookup"><span data-stu-id="a611c-106">Attribute</span></span>|<span data-ttu-id="a611c-107">預設</span><span class="sxs-lookup"><span data-stu-id="a611c-107">Default</span></span>|  
|---------------|-------------|  
|<span data-ttu-id="a611c-108">SQL_ATTR_CONCURRENCY</span><span class="sxs-lookup"><span data-stu-id="a611c-108">SQL_ATTR_CONCURRENCY</span></span>|<span data-ttu-id="a611c-109">SQL_CONCUR_READ_ONLY</span><span class="sxs-lookup"><span data-stu-id="a611c-109">SQL_CONCUR_READ_ONLY</span></span>|  
|<span data-ttu-id="a611c-110">SQL_ATTR_CURSOR_TYPE</span><span class="sxs-lookup"><span data-stu-id="a611c-110">SQL_ATTR_CURSOR_TYPE</span></span>|<span data-ttu-id="a611c-111">SQL_CURSOR_FORWARD_ONLY</span><span class="sxs-lookup"><span data-stu-id="a611c-111">SQL_CURSOR_FORWARD_ONLY</span></span>|  
|<span data-ttu-id="a611c-112">SQL_ATTR_CURSOR_SCROLLABLE</span><span class="sxs-lookup"><span data-stu-id="a611c-112">SQL_ATTR_CURSOR_SCROLLABLE</span></span>|<span data-ttu-id="a611c-113">SQL_NONSCROLLABLE</span><span class="sxs-lookup"><span data-stu-id="a611c-113">SQL_NONSCROLLABLE</span></span>|  
|<span data-ttu-id="a611c-114">SQL_ATTR_CURSOR_SENSITIVITY</span><span class="sxs-lookup"><span data-stu-id="a611c-114">SQL_ATTR_CURSOR_SENSITIVITY</span></span>|<span data-ttu-id="a611c-115">SQL_UNSPECIFIED</span><span class="sxs-lookup"><span data-stu-id="a611c-115">SQL_UNSPECIFIED</span></span>|  
|<span data-ttu-id="a611c-116">SQL_ATTR_ROW_ARRAY_SIZE</span><span class="sxs-lookup"><span data-stu-id="a611c-116">SQL_ATTR_ROW_ARRAY_SIZE</span></span>|<span data-ttu-id="a611c-117">1</span><span class="sxs-lookup"><span data-stu-id="a611c-117">1</span></span>|  
  
 <span data-ttu-id="a611c-118">當執行 SQL 語句時，這些選項設定為預設值時， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式不會使用伺服器資料指標來執行結果集，而是使用預設的結果集。</span><span class="sxs-lookup"><span data-stu-id="a611c-118">When these options are set to their defaults at the time an SQL statement is executed, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not use a server cursor to implement the result set; instead, it uses a default result set.</span></span> <span data-ttu-id="a611c-119">如果在執行 SQL 語句時，任何這些選項的預設值已變更， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式會嘗試使用伺服器資料指標來執行結果集。</span><span class="sxs-lookup"><span data-stu-id="a611c-119">If any of these options are changed from their defaults at the time an SQL statement is executed, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver attempts to use a server cursor to implement the result set.</span></span>  
  
 <span data-ttu-id="a611c-120">預設結果集支援所有 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a611c-120">Default result sets support all of the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="a611c-121">使用預設結果集時，可執行的 SQL 陳述式類型沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="a611c-121">There are no restrictions on the types of SQL statements that can be executed when using a default result set.</span></span>  
  
 <span data-ttu-id="a611c-122">伺服器資料指標不支援所有 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a611c-122">Server cursors do not support all [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span> <span data-ttu-id="a611c-123">伺服器資料指標不支援任何產生多個結果集的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a611c-123">Server cursors do not support any SQL statement that generates multiple result sets.</span></span>  
  
 <span data-ttu-id="a611c-124">伺服器資料指標不支援下列陳述式類型：</span><span class="sxs-lookup"><span data-stu-id="a611c-124">The following types of statements are not supported by server cursors:</span></span>  
  
-   <span data-ttu-id="a611c-125">批次</span><span class="sxs-lookup"><span data-stu-id="a611c-125">Batches</span></span>  
  
     <span data-ttu-id="a611c-126">根據兩個或多個個別 SQL SELECT 陳述式所建立的 SQL 陳述式，例如：</span><span class="sxs-lookup"><span data-stu-id="a611c-126">SQL statements built from two or more individual SQL SELECT statements, for example:</span></span>  
  
    ```  
    SELECT * FROM Authors; SELECT * FROM Titles  
    ```  
  
-   <span data-ttu-id="a611c-127">具有多個 SELECT 陳述式的預存程序</span><span class="sxs-lookup"><span data-stu-id="a611c-127">Stored procedures with multiple SELECT statements</span></span>  
  
     <span data-ttu-id="a611c-128">執行包含多個 SELECT 陳述式之預存程序的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a611c-128">SQL statements that execute a stored procedure containing more than one SELECT statement.</span></span> <span data-ttu-id="a611c-129">這包括填入參數或變數的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a611c-129">This includes SELECT statements that fill parameters or variables.</span></span>  
  
-   <span data-ttu-id="a611c-130">關鍵字</span><span class="sxs-lookup"><span data-stu-id="a611c-130">Keywords</span></span>  
  
     <span data-ttu-id="a611c-131">包含 FOR BROWSE 或 INTO 關鍵字的 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="a611c-131">SQL statements containing the keywords FOR BROWSE, or INTO.</span></span>  
  
 <span data-ttu-id="a611c-132">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中，如果與其中任何條件相符的 SQL 陳述式是使用伺服器資料指標執行，此伺服器資料指標就會隱含轉換成預設結果集。</span><span class="sxs-lookup"><span data-stu-id="a611c-132">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], if an SQL statement that matches any of these conditions is executed with a server cursor, the server cursor is implicitly converted to a default result set.</span></span> <span data-ttu-id="a611c-133">**SQLExecDirect**或**SQLExecute**傳回 SQL_SUCCESS_WITH_INFO 之後，資料指標屬性將會設回其預設設定。</span><span class="sxs-lookup"><span data-stu-id="a611c-133">After **SQLExecDirect** or **SQLExecute** returns SQL_SUCCESS_WITH_INFO, the cursor attributes will be set back to their default settings.</span></span>  
  
 <span data-ttu-id="a611c-134">不符合上述類別目錄的 SQL 陳述式可以使用任何陳述式屬性設定執行。它們的運作方式就如同預設結果集或伺服器資料指標。</span><span class="sxs-lookup"><span data-stu-id="a611c-134">SQL statements that do not fit the categories above can be executed with any statement attribute settings; they work equally well with either a default result set or a server cursor.</span></span>  
  
## <a name="errors"></a><span data-ttu-id="a611c-135">Errors</span><span class="sxs-lookup"><span data-stu-id="a611c-135">Errors</span></span>  
 <span data-ttu-id="a611c-136">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 和更新版本中，如果嘗試執行產生多個結果集的陳述式，就會產生 SQL_SUCCESS_WITH INFO 和下列訊息：</span><span class="sxs-lookup"><span data-stu-id="a611c-136">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 7.0 and later, an attempt to execute a statement that produces multiple result sets generates SQL_SUCCESS_WITH INFO and the following message:</span></span>  
  
```  
SqlState: 01S02"  
pfNative: 0  
szErrorMsgString: "[Microsoft][SQL Server Native Client][SQL Server]  
               Cursor type changed."  
```  
  
 <span data-ttu-id="a611c-137">接收此訊息的 ODBC 應用程式可以呼叫[SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md)來判斷目前的資料指標設定。</span><span class="sxs-lookup"><span data-stu-id="a611c-137">ODBC applications receiving this message can call [SQLGetStmtAttr](../native-client-odbc-api/sqlgetstmtattr.md) to determine the current cursor settings.</span></span>  
  
 <span data-ttu-id="a611c-138">如果使用伺服器資料指標時嘗試執行具有多個 SELECT 陳述式的程序，就會產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="a611c-138">An attempt to execute a procedure with multiple SELECT statements when using server cursors generates the following error:</span></span>  
  
```  
SqlState: 42000  
pfNative: 16937  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               A server cursor is not allowed on a stored procedure  
               with more than one SELECT statement in it. Use a  
               default result set or client cursor.  
```  
  
 <span data-ttu-id="a611c-139">如果使用伺服器資料指標時嘗試執行具有多個 SELECT 陳述式的批次，就會產生下列錯誤：</span><span class="sxs-lookup"><span data-stu-id="a611c-139">An attempt to execute a batch with multiple SELECT statements when using server cursors generates the following error:</span></span>  
  
```  
SqlState: 42000  
pfNative: 16938  
szErrorMsgString: [Microsoft][SQL Server Native Client][SQL Server]  
               sp_cursoropen. The statement parameter can only  
               be a single SELECT statement or a single stored   
               procedure.  
```  
  
 <span data-ttu-id="a611c-140">收到這些錯誤的 ODBC 應用程式必須將所有資料指標陳述式屬性重設為其預設值，然後再嘗試執行此陳述式。</span><span class="sxs-lookup"><span data-stu-id="a611c-140">ODBC applications receiving these errors must reset all the cursor statement attributes to their defaults before attempting to execute the statement.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a611c-141">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a611c-141">See Also</span></span>  
 [<span data-ttu-id="a611c-142">&#40;ODBC&#41;執行查詢</span><span class="sxs-lookup"><span data-stu-id="a611c-142">Executing Queries &#40;ODBC&#41;</span></span>](executing-queries-odbc.md)  
  
  
