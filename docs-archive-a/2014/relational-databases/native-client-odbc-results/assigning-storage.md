---
title: 指派儲存體 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- column-wise binding [ODBC]
- SQL Server Native Client ODBC driver, result sets
- ODBC applications, result sets
- SQLBindCol function
- storing data [ODBC]
- result sets [ODBC], storage
- SQL Server Native Client ODBC driver, data storage
- row-wise binding
- binding result sets [SQL Server Native Client]
- array binding
ms.assetid: 11c81955-5300-495f-925f-9256f2587b58
author: rothja
ms.author: jroth
ms.openlocfilehash: ada18c91493d91b36ced51bf84c32513a0c5f5df
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598319"
---
# <a name="assigning-storage"></a><span data-ttu-id="1360c-102">指派儲存體</span><span class="sxs-lookup"><span data-stu-id="1360c-102">Assigning Storage</span></span>
  <span data-ttu-id="1360c-103">應用程式可以在執行 SQL 陳述式之前或之後指派結果的儲存體。</span><span class="sxs-lookup"><span data-stu-id="1360c-103">An application can assign storage for results before or after it executes a SQL statement.</span></span> <span data-ttu-id="1360c-104">如果應用程式先準備或執行 SQL 陳述式，它就可以查詢結果集的相關資訊，然後再指派結果的儲存體。</span><span class="sxs-lookup"><span data-stu-id="1360c-104">If an application prepares or executes the SQL statement first, it can inquire about the result set before it assigns storage for results.</span></span> <span data-ttu-id="1360c-105">例如，如果結果集是未知的，應用程式就必須擷取資料行的數目，然後才能指派它們的儲存體。</span><span class="sxs-lookup"><span data-stu-id="1360c-105">For example, if the result set is unknown, the application must retrieve the number of columns before it can assign storage for them.</span></span>  
  
 <span data-ttu-id="1360c-106">為了讓資料行的儲存區產生關聯，應用程式會呼叫[SQLBindCol](../native-client-odbc-api/sqlbindcol.md)並傳遞它：</span><span class="sxs-lookup"><span data-stu-id="1360c-106">To associate storage for a column of data, an application calls [SQLBindCol](../native-client-odbc-api/sqlbindcol.md)and passes it:</span></span>  
  
-   <span data-ttu-id="1360c-107">要轉換資料的目標資料類型。</span><span class="sxs-lookup"><span data-stu-id="1360c-107">The data type to which the data is to be converted.</span></span>  
  
-   <span data-ttu-id="1360c-108">資料之輸出緩衝區的位址。</span><span class="sxs-lookup"><span data-stu-id="1360c-108">The address of an output buffer for the data.</span></span>  
  
     <span data-ttu-id="1360c-109">應用程式必須配置這個緩衝區，而且緩衝區必須夠大，足以用轉換的格式來保存資料。</span><span class="sxs-lookup"><span data-stu-id="1360c-109">The application must allocate this buffer, and it must be large enough to hold the data in the form to which it is converted.</span></span>  
  
-   <span data-ttu-id="1360c-110">輸出緩衝區的長度。</span><span class="sxs-lookup"><span data-stu-id="1360c-110">The length of the output buffer.</span></span>  
  
     <span data-ttu-id="1360c-111">如果傳回的資料具有固定寬度 C (例如整數、實數或資料結構)，系統就會忽略此值。</span><span class="sxs-lookup"><span data-stu-id="1360c-111">This value is ignored if the returned data has a fixed width in C, such as an integer, real number, or date structure.</span></span>  
  
-   <span data-ttu-id="1360c-112">要傳回可用資料之位元組數目的儲存緩衝區位址。</span><span class="sxs-lookup"><span data-stu-id="1360c-112">The address of a storage buffer in which to return the number of bytes of available data.</span></span>  
  
 <span data-ttu-id="1360c-113">應用程式也可以將結果集資料行繫結至程式變數的陣列，以便支援在區塊中提取結果集資料行。</span><span class="sxs-lookup"><span data-stu-id="1360c-113">An application can also bind result set columns to arrays of program variables to support fetching result set rows in blocks.</span></span> <span data-ttu-id="1360c-114">陣列繫結有兩種不同的類型：</span><span class="sxs-lookup"><span data-stu-id="1360c-114">There are two different types of array binding:</span></span>  
  
-   <span data-ttu-id="1360c-115">當每個資料行繫結至自己的變數陣列時，就會完成資料行取向繫結。</span><span class="sxs-lookup"><span data-stu-id="1360c-115">Column-wise binding is finished when each column is bound to its own array of variables.</span></span>  
  
     <span data-ttu-id="1360c-116">藉由呼叫[SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md)並將*屬性*設定為 SQL_ATTR_ROW_BIND_TYPE，並將*valueptr 是*設定為 SQL_BIND_BY_COLUMN 來指定資料行取向系結。</span><span class="sxs-lookup"><span data-stu-id="1360c-116">Column-wise binding is specified by calling [SQLSetStmtAttr](../native-client-odbc-api/sqlsetstmtattr.md) with *Attribute* set to SQL_ATTR_ROW_BIND_TYPE and *ValuePtr* set to SQL_BIND_BY_COLUMN.</span></span> <span data-ttu-id="1360c-117">所有陣列的元素數目都必須相同。</span><span class="sxs-lookup"><span data-stu-id="1360c-117">All the arrays must have the same number of elements.</span></span>  
  
-   <span data-ttu-id="1360c-118">當 SQL 陳述式的所有參數都是以單位的形式繫結至含有參數個別變數的結構陣列時，就會完成資料列取向繫結。</span><span class="sxs-lookup"><span data-stu-id="1360c-118">Row-wise binding is finished when all the parameters in the SQL statement are bound as a unit to an array of structures that contain the individual variables for the parameters.</span></span>  
  
     <span data-ttu-id="1360c-119">資料列取向系結的指定方式是呼叫**SQLSetStmtAttr** ，並將*屬性*設定為 SQL_ATTR_ROW_BIND_TYPE，並將*valueptr 是*設定為包含將會接收結果集資料行之變數的結構大小。</span><span class="sxs-lookup"><span data-stu-id="1360c-119">Row-wise binding is specified by calling **SQLSetStmtAttr** with *Attribute* set to SQL_ATTR_ROW_BIND_TYPE and *ValuePtr* set to the size of the structure holding the variables that will receive the result set columns.</span></span>  
  
 <span data-ttu-id="1360c-120">應用程式也會將 SQL_ATTR_ROW_ARRAY_SIZE 設定為資料行或資料列陣列中的元素數目，並且設定 SQL_ATTR_ROW_STATUS_PTR 和 SQL_ATTR_ROWS_FETCHED_PTR。</span><span class="sxs-lookup"><span data-stu-id="1360c-120">The application also sets SQL_ATTR_ROW_ARRAY_SIZE to the number of elements in the column or row arrays and sets SQL_ATTR_ROW_STATUS_PTR and SQL_ATTR_ROWS_FETCHED_PTR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1360c-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1360c-121">See Also</span></span>  
 [<span data-ttu-id="1360c-122">&#40;ODBC&#41;處理結果</span><span class="sxs-lookup"><span data-stu-id="1360c-122">Processing Results &#40;ODBC&#41;</span></span>](processing-results-odbc.md)  
  
  
