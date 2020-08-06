---
title: SQLBindParameter |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindParameter function
ms.assetid: c302c87a-e7f4-4d2b-a0a7-de42210174ac
author: rothja
ms.author: jroth
ms.openlocfilehash: 6e50886457c4c20110880cc5b75ec594fd3eaba5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606280"
---
# <a name="sqlbindparameter"></a><span data-ttu-id="50df4-102">SQLBindParameter</span><span class="sxs-lookup"><span data-stu-id="50df4-102">SQLBindParameter</span></span>
  <span data-ttu-id="50df4-103">`SQLBindParameter`當用來提供 Native Client ODBC 驅動程式的資料時，可以消除資料轉換的負擔 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，進而大幅提升應用程式的用戶端和伺服器元件的效能。</span><span class="sxs-lookup"><span data-stu-id="50df4-103">`SQLBindParameter` can eliminate the burden of data conversion when used to provide data for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, resulting in significant performance gains for both the client and server components of applications.</span></span> <span data-ttu-id="50df4-104">其他優點包括插入或更新近似的數值資料類型時，降低有效位數的損失。</span><span class="sxs-lookup"><span data-stu-id="50df4-104">Other benefits include reduced loss of precision when inserting or updating approximate numeric data types.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="50df4-105">將 `char` 和 `wchar` 類型資料插入 image 資料行時，會使用傳入之資料的大小，而非轉換為二進位格式後的資料大小。</span><span class="sxs-lookup"><span data-stu-id="50df4-105">When inserting `char` and `wchar` type data into an image column, the size of the data being passed in is used, as opposed to the size of the data after conversion to a binary format.</span></span>  
  
 <span data-ttu-id="50df4-106">如果 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式在任何參數陣列的單一陣列元素上碰到錯誤，驅動程式會繼續執行其餘陣列元素的陳述式。</span><span class="sxs-lookup"><span data-stu-id="50df4-106">If the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver encounters an error on a single array element of an array of parameters, the driver continues to execute the statement for the remaining array elements.</span></span> <span data-ttu-id="50df4-107">如果應用程式已經繫結陳述式的參數狀態元素陣列，可以從陣列判斷產生錯誤的參數資料列。</span><span class="sxs-lookup"><span data-stu-id="50df4-107">If the application has bound an array of parameter status elements for the statement, the rows of parameters generating errors can be determined from the array.</span></span>  
  
 <span data-ttu-id="50df4-108">如果使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式，指定繫結輸入參數時的 SQL_PARAM_INPUT。</span><span class="sxs-lookup"><span data-stu-id="50df4-108">When using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver, specify SQL_PARAM_INPUT when binding input parameters.</span></span> <span data-ttu-id="50df4-109">繫結使用 OUTPUT 關鍵字定義的預存程序參數時，只會指定 SQL_PARAM_OUTPUT 或 SQL_PARAM_INPUT_OUTPUT。</span><span class="sxs-lookup"><span data-stu-id="50df4-109">Only specify SQL_PARAM_OUTPUT or SQL_PARAM_INPUT_OUTPUT when binding stored procedure parameters defined with the OUTPUT keyword.</span></span>  
  
 <span data-ttu-id="50df4-110">[SQLRowCount](sqlrowcount.md)如果系結 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 參數陣列的陣列元素導致語句執行發生錯誤，則 SQLRowCount 與 Native Client ODBC 驅動程式不可靠。</span><span class="sxs-lookup"><span data-stu-id="50df4-110">[SQLRowCount](sqlrowcount.md) is unreliable with the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver if an array element of a bound-parameter array causes an error in statement execution.</span></span> <span data-ttu-id="50df4-111">ODBC 陳述式屬性 SQL_ATTR_PARAMS_PROCESSED_PTR 會報告錯誤發生前處理的資料列數目。</span><span class="sxs-lookup"><span data-stu-id="50df4-111">The ODBC statement attribute SQL_ATTR_PARAMS_PROCESSED_PTR reports the number of rows processed before the error occurs.</span></span> <span data-ttu-id="50df4-112">接著，如果需要，此應用程式可以周遊其參數狀態陣列以探索成功執行的陳述式數目。</span><span class="sxs-lookup"><span data-stu-id="50df4-112">The application can then traverse its parameter status array to discover the number of statements successfully executed, if necessary.</span></span>  
  
## <a name="binding-parameters-for-sql-character-types"></a><span data-ttu-id="50df4-113">SQL 字元類型的繫結參數</span><span class="sxs-lookup"><span data-stu-id="50df4-113">Binding Parameters for SQL Character Types</span></span>  
 <span data-ttu-id="50df4-114">如果傳入的 SQL 資料類型是字元類型，則*ColumnSize*是以字元為單位的大小， (不是位元組) 。</span><span class="sxs-lookup"><span data-stu-id="50df4-114">If the SQL data type passed in is a character type, *ColumnSize* is the size in characters (not bytes).</span></span> <span data-ttu-id="50df4-115">如果資料字串的長度（以位元組為單位）大於8000，則*ColumnSize*應該設定為 `SQL_SS_LENGTH_UNLIMITED` ，表示 SQL 類型的大小沒有任何限制。</span><span class="sxs-lookup"><span data-stu-id="50df4-115">If the length of the data string in bytes is greater than 8000, *ColumnSize* should be set to `SQL_SS_LENGTH_UNLIMITED`, indicating that there is no limit to the size of the SQL type.</span></span>  
  
 <span data-ttu-id="50df4-116">例如，如果 SQL 資料類型為，則 `SQL_WVARCHAR` *ColumnSize*不應大於4000。</span><span class="sxs-lookup"><span data-stu-id="50df4-116">For instance, if the SQL data type is `SQL_WVARCHAR`, *ColumnSize* should not be greater than 4000.</span></span> <span data-ttu-id="50df4-117">如果實際的資料長度大於4000，則*ColumnSize*應該設定為，以 `SQL_SS_LENGTH_UNLIMITED` `nvarchar(max)` 供驅動程式使用。</span><span class="sxs-lookup"><span data-stu-id="50df4-117">If the actual data length is greater than 4000, then *ColumnSize* should be set to `SQL_SS_LENGTH_UNLIMITED` so that `nvarchar(max)` will be used by driver.</span></span>  
  
## <a name="sqlbindparameter-and-table-valued-parameters"></a><span data-ttu-id="50df4-118">SQLBindParameter 和資料表值參數</span><span class="sxs-lookup"><span data-stu-id="50df4-118">SQLBindParameter and Table-Valued Parameters</span></span>  
 <span data-ttu-id="50df4-119">資料表值參數與其他參數類型一樣，是由 SQLBindParameter 所系結。</span><span class="sxs-lookup"><span data-stu-id="50df4-119">Like other parameter types, table-valued parameters are bound by SQLBindParameter.</span></span>  
  
 <span data-ttu-id="50df4-120">繫結資料表值參數之後，也會一併繫結其資料行。</span><span class="sxs-lookup"><span data-stu-id="50df4-120">After a table-valued parameter has been bound, its columns are also bound.</span></span> <span data-ttu-id="50df4-121">若要系結資料行，您可以呼叫[SQLSetStmtAttr](sqlsetstmtattr.md) ，將 SQL_SOPT_SS_PARAM_FOCUS 設定為數據表值參數的序數。</span><span class="sxs-lookup"><span data-stu-id="50df4-121">To bind the columns, you call [SQLSetStmtAttr](sqlsetstmtattr.md) to set SQL_SOPT_SS_PARAM_FOCUS to the ordinal of the table-valued parameter.</span></span> <span data-ttu-id="50df4-122">然後，針對資料表值參數中的每個資料行呼叫 SQLBindParameter。</span><span class="sxs-lookup"><span data-stu-id="50df4-122">Then, call SQLBindParameter for each column in the table-valued parameter.</span></span> <span data-ttu-id="50df4-123">若要傳回到最上層參數繫結，將 SQL_SOPT_SS_PARAM_FOCUS 設定為 0。</span><span class="sxs-lookup"><span data-stu-id="50df4-123">To return to the top-level parameter bindings, set SQL_SOPT_SS_PARAM_FOCUS to 0.</span></span>  
  
 <span data-ttu-id="50df4-124">如需將參數對應至資料表值參數之描述項欄位的詳細資訊，請參閱[資料表值參數和資料行值的系結和資料傳輸](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)。</span><span class="sxs-lookup"><span data-stu-id="50df4-124">For information about mapping parameters to descriptor fields for table-valued parameters, see [Binding and Data Transfer of Table-Valued Parameters and Column Values](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).</span></span>  
  
 <span data-ttu-id="50df4-125">如需資料表值參數的詳細資訊，請參閱[ODBC&#41;&#40;的資料表值參數](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="50df4-125">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlbindparameter-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="50df4-126">SQLBindParameter 對增強型日期和時間功能的支援</span><span class="sxs-lookup"><span data-stu-id="50df4-126">SQLBindParameter Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="50df4-127">日期/時間類型的參數值會依照[從 C 轉換成 SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)中所述的方式進行轉換。</span><span class="sxs-lookup"><span data-stu-id="50df4-127">Parameter values of date/time types are converted as described in [Conversions from C to SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).</span></span> <span data-ttu-id="50df4-128">請注意，和類型的參數 `time` `datetimeoffset` 必須*ValueType*指定為 `SQL_C_DEFAULT` 或， `SQL_C_BINARY` 如果其對應的結構 (`SQL_SS_TIME2_STRUCT` 並 `SQL_SS_TIMESTAMPOFFSET_STRUCT` 使用) 。</span><span class="sxs-lookup"><span data-stu-id="50df4-128">Note that parameters of type `time` and `datetimeoffset` must have *ValueType* specified as `SQL_C_DEFAULT` or `SQL_C_BINARY` if their corresponding structures (`SQL_SS_TIME2_STRUCT` and `SQL_SS_TIMESTAMPOFFSET_STRUCT`) are used.</span></span>  
  
 <span data-ttu-id="50df4-129">如需詳細資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="50df4-129">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlbindparameter-support-for-large-clr-udts"></a><span data-ttu-id="50df4-130">大型 CLR UDT 的 SQLBindParameter 支援</span><span class="sxs-lookup"><span data-stu-id="50df4-130">SQLBindParameter Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="50df4-131">`SQLBindParameter` 支援大型 CLR 使用者定義型別 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="50df4-131">`SQLBindParameter` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="50df4-132">如需詳細資訊，請參閱[&#40;ODBC&#41;的大型 CLR 使用者定義類型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="50df4-132">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50df4-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50df4-133">See Also</span></span>  
 <span data-ttu-id="50df4-134">[ODBC API 的執行詳細資料](odbc-api-implementation-details.md) </span><span class="sxs-lookup"><span data-stu-id="50df4-134">[ODBC API Implementation Details](odbc-api-implementation-details.md) </span></span>  
 [<span data-ttu-id="50df4-135">SQLBindParameter 函式</span><span class="sxs-lookup"><span data-stu-id="50df4-135">SQLBindParameter Function</span></span>](https://go.microsoft.com/fwlink/?LinkId=59328)  
  
  
