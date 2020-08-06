---
title: 系結參數 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, parameters
- parameters [SQL Server Native Client], ODBC
- statements [ODBC], parameters
- binding parameters [SQL Server Native Client]
- parameter markers [ODBC]
- unbound parameter markers
- SQLBindParameter function
- ODBC applications, parameters
- bound parameter markers [SQL Server Native Client]
ms.assetid: d6c69739-8f89-475f-a60a-b2f6c06576e2
author: rothja
ms.author: jroth
ms.openlocfilehash: 3402a7efce43d0ce94a20c93504ac1dcb2c7b48f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585344"
---
# <a name="binding-parameters"></a><span data-ttu-id="598f6-102">繫結參數</span><span class="sxs-lookup"><span data-stu-id="598f6-102">Binding Parameters</span></span>
  <span data-ttu-id="598f6-103">SQL 陳述式中的每一個參數標記都必須與應用程式的變數相關聯或繫結，才能執行該陳述式。</span><span class="sxs-lookup"><span data-stu-id="598f6-103">Each parameter marker in an SQL statement must be associated, or bound, to a variable in the application before the statement can be executed.</span></span> <span data-ttu-id="598f6-104">這是藉由呼叫[SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md)函數來完成。</span><span class="sxs-lookup"><span data-stu-id="598f6-104">This is done by calling the [SQLBindParameter](../native-client-odbc-api/sqlbindparameter.md) function.</span></span> <span data-ttu-id="598f6-105">**SQLBindParameter**描述程式變數 (位址、C 資料類型，以及驅動程式) 。</span><span class="sxs-lookup"><span data-stu-id="598f6-105">**SQLBindParameter** describes the program variable (address, C data type, and so on) to the driver.</span></span> <span data-ttu-id="598f6-106">它也會藉由指定序數值以辨識參數標記，然後描述它所代表的 SQL 物件的特性 (SQL 資料類型、有效位數等)。</span><span class="sxs-lookup"><span data-stu-id="598f6-106">It also identifies the parameter marker by indicating its ordinal value and then describes the characteristics of the SQL object it represents (SQL data type, precision, and so on).</span></span>

 <span data-ttu-id="598f6-107">參數標記可以在執行陳述式之前的任何時候繫結或重新繫結。</span><span class="sxs-lookup"><span data-stu-id="598f6-107">Parameter markers can be bound or rebound at any time before a statement is executed.</span></span> <span data-ttu-id="598f6-108">在發生下列其中一個事件之前，參數繫結都會持續有效：</span><span class="sxs-lookup"><span data-stu-id="598f6-108">A parameter binding remains in effect until one of the following occurs:</span></span>

-   <span data-ttu-id="598f6-109">呼叫[SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md)並將*Option*參數設為 SQL_RESET_PARAMS 會釋出系結至語句控制碼的所有參數。</span><span class="sxs-lookup"><span data-stu-id="598f6-109">A call to [SQLFreeStmt](../native-client-odbc-api/sqlfreestmt.md) with the *Option* parameter set to SQL_RESET_PARAMS frees all parameters bound to the statement handle.</span></span>

-   <span data-ttu-id="598f6-110">呼叫**SQLBindParameter**並將*ParameterNumber*設定為系結參數標記的序數時，會自動釋放先前的系結。</span><span class="sxs-lookup"><span data-stu-id="598f6-110">A call to **SQLBindParameter** with *ParameterNumber* set to the ordinal of a bound parameter marker automatically releases the previous binding.</span></span>

 <span data-ttu-id="598f6-111">應用程式也可以將參數繫結到程式變數的陣列，以批次的方式處理 SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="598f6-111">An application can also bind parameters to arrays of program variables to process an SQL statement in batches.</span></span> <span data-ttu-id="598f6-112">陣列繫結有兩種類型：</span><span class="sxs-lookup"><span data-stu-id="598f6-112">There are two types of array binding:</span></span>

-   <span data-ttu-id="598f6-113">當每一個個別參數繫結到自己的變數陣列時，就會完成資料行取向繫結。</span><span class="sxs-lookup"><span data-stu-id="598f6-113">Column-wise binding is done when each individual parameter is bound to its own array of variables.</span></span>

     <span data-ttu-id="598f6-114">藉由呼叫[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)並將*屬性*設定為 SQL_ATTR_PARAM_BIND_TYPE，並將*valueptr 是*設定為 SQL_PARAM_BIND_BY_COLUMN 來指定資料行取向系結。</span><span class="sxs-lookup"><span data-stu-id="598f6-114">Column-wise binding is specified by calling [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) with *Attribute* set to SQL_ATTR_PARAM_BIND_TYPE and *ValuePtr* set to SQL_PARAM_BIND_BY_COLUMN.</span></span>

-   <span data-ttu-id="598f6-115">當 SQL 陳述式的所有參數都是以單位的形式繫結到含有參數個別變數的結構陣列時，會形成資料列取向繫結。</span><span class="sxs-lookup"><span data-stu-id="598f6-115">Row-wise binding is done when all of the parameters in the SQL statement are bound as a unit to an array of structures that contain the individual variables for the parameters.</span></span>

     <span data-ttu-id="598f6-116">藉由呼叫**SQLSetStmtAttr**並將*屬性*設定為 SQL_ATTR_PARAM_BIND_TYPE，並將*valueptr 是*設定為保留程式變數的結構大小，來指定資料列取向系結。</span><span class="sxs-lookup"><span data-stu-id="598f6-116">Row-wise binding is specified by calling **SQLSetStmtAttr** with *Attribute* set to SQL_ATTR_PARAM_BIND_TYPE and *ValuePtr* set to the size of the structure holding the program variables.</span></span>

 <span data-ttu-id="598f6-117">當 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式將字元或二進位字串參數傳送至伺服器時，它會將值填補至**SQLBindParameter** *ColumnSize*參數中指定的長度。</span><span class="sxs-lookup"><span data-stu-id="598f6-117">When the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver sends character or binary string parameters to the server, it pads the values to the length specified in **SQLBindParameter** *ColumnSize* parameter.</span></span> <span data-ttu-id="598f6-118">如果 ODBC 2.x 應用程式為*ColumnSize*指定0，驅動程式會將參數值填補至資料類型的有效位數。</span><span class="sxs-lookup"><span data-stu-id="598f6-118">If an ODBC 2.x application specifies 0 for *ColumnSize*, the driver pads the parameter value to the precision of the data type.</span></span> <span data-ttu-id="598f6-119">當連接至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 伺服器時，有效位數為 8000，連接至舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 時則為 255。</span><span class="sxs-lookup"><span data-stu-id="598f6-119">The precision is 8000 when connected to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servers, 255 when connected to earlier versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="598f6-120">Variant 資料行的*ColumnSize*是以位元組為單位。</span><span class="sxs-lookup"><span data-stu-id="598f6-120">*ColumnSize* is in bytes for variant columns.</span></span>

 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="598f6-121">支援定義預存程序參數的名稱。</span><span class="sxs-lookup"><span data-stu-id="598f6-121">supports defining names for stored procedure parameters.</span></span> <span data-ttu-id="598f6-122">ODBC 3.5 也導入了對呼叫 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 預存程序時所使用之具名參數的支援。</span><span class="sxs-lookup"><span data-stu-id="598f6-122">ODBC 3.5 also introduced support for named parameters used when calling [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures.</span></span> <span data-ttu-id="598f6-123">這項支援可用來：</span><span class="sxs-lookup"><span data-stu-id="598f6-123">This support can be used to:</span></span>

-   <span data-ttu-id="598f6-124">呼叫預存程序，並提供為預存程序定義之參數子集的值。</span><span class="sxs-lookup"><span data-stu-id="598f6-124">Call a stored procedure and provide values for a subset of the parameters defined for the stored procedure.</span></span>

-   <span data-ttu-id="598f6-125">以不同的順序指定參數，也就是在應用程式中的順序，與在預存程序建立時所指定的順序不同。</span><span class="sxs-lookup"><span data-stu-id="598f6-125">Specify the parameters in a different order in the application than the order specified when the stored procedure was created.</span></span>

 <span data-ttu-id="598f6-126">只有在使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] `EXECUTE` 語句或 ODBC 呼叫 escape 序列來執行預存程式時，才支援具名引數。</span><span class="sxs-lookup"><span data-stu-id="598f6-126">Named parameters are only supported when using the [!INCLUDE[tsql](../../includes/tsql-md.md)] `EXECUTE` statement or the ODBC CALL escape sequence to execute a stored procedure.</span></span>

 <span data-ttu-id="598f6-127">如果針對預存程序參數設定 `SQL_DESC_NAME`，則查詢中的所有預存程序參數也都應該設定 `SQL_DESC_NAME`。</span><span class="sxs-lookup"><span data-stu-id="598f6-127">If `SQL_DESC_NAME` is set for a stored procedure parameter, all stored procedure parameters in the query should also set `SQL_DESC_NAME`.</span></span>  <span data-ttu-id="598f6-128">如果在預存程序呼叫中使用常值，其中參數已 `SQL_DESC_NAME` 設定，則常值應使用格式 *' name* = *value*'，其中*name*是預存程式參數名稱 (例如， @p1) 。</span><span class="sxs-lookup"><span data-stu-id="598f6-128">If literals are used in stored procedure calls, where parameters have `SQL_DESC_NAME` set, the literals should use the format *'name*=*value*', where *name* is the stored procedure parameter name (for example, @p1).</span></span> <span data-ttu-id="598f6-129">如需詳細資訊，請參閱[依名稱系結參數 (具名引數) ](https://go.microsoft.com/fwlink/?LinkId=167215)。</span><span class="sxs-lookup"><span data-stu-id="598f6-129">For more information, see [Binding Parameters by Name (Named Parameters)](https://go.microsoft.com/fwlink/?LinkId=167215).</span></span>

## <a name="see-also"></a><span data-ttu-id="598f6-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="598f6-130">See Also</span></span>
 [<span data-ttu-id="598f6-131">使用陳述式參數</span><span class="sxs-lookup"><span data-stu-id="598f6-131">Using Statement Parameters</span></span>](using-statement-parameters.md)


