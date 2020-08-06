---
title: SQLDescribeParam |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLDescribeParam function
ms.assetid: 396e74b1-5d08-46dc-b404-2ef2003e4689
author: rothja
ms.author: jroth
ms.openlocfilehash: 05e14ccb0fadb4f1cf05f965c79cf8c05c71f93a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597795"
---
# <a name="sqldescribeparam"></a><span data-ttu-id="c75b5-102">SQLDescribeParam</span><span class="sxs-lookup"><span data-stu-id="c75b5-102">SQLDescribeParam</span></span>
  <span data-ttu-id="c75b5-103">為了描述任何 SQL 語句的參數， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式 [!INCLUDE[tsql](../../includes/tsql-md.md)] 會在備妥的 ODBC 語句控制碼上呼叫 SQLDescribeParam 時，建立並執行 SELECT 語句。</span><span class="sxs-lookup"><span data-stu-id="c75b5-103">To describe the parameters of any SQL statement, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver builds and executes a [!INCLUDE[tsql](../../includes/tsql-md.md)] SELECT statement when SQLDescribeParam is called on a prepared ODBC statement handle.</span></span> <span data-ttu-id="c75b5-104">結果集的中繼資料則會決定已備妥之陳述式中的參數特性。</span><span class="sxs-lookup"><span data-stu-id="c75b5-104">The metadata of the result set determines the characteristics of the parameters in the prepared statement.</span></span> <span data-ttu-id="c75b5-105">SQLDescribeParam 可能會傳回 SQLExecute 或 SQLExecDirect 可能傳回的任何錯誤碼。</span><span class="sxs-lookup"><span data-stu-id="c75b5-105">SQLDescribeParam can return any error code that SQLExecute or SQLExecDirect might return.</span></span>  
  
 <span data-ttu-id="c75b5-106">從開始，database engine 的改進 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] 可讓 SQLDescribeParam 取得預期結果的更精確描述。</span><span class="sxs-lookup"><span data-stu-id="c75b5-106">Improvements in the database engine starting with [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] allow SQLDescribeParam to obtain more accurate descriptions of the expected results.</span></span> <span data-ttu-id="c75b5-107">這些更精確的結果可能與舊版的 SQLDescribeParam 所傳回的值不同 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c75b5-107">These more accurate results may differ from the values returned by SQLDescribeParam in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="c75b5-108">如需詳細資訊，請參閱[中繼資料探索](../native-client/features/metadata-discovery.md)。</span><span class="sxs-lookup"><span data-stu-id="c75b5-108">For more information, see [Metadata Discovery](../native-client/features/metadata-discovery.md).</span></span>  
  
 <span data-ttu-id="c75b5-109">此外 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ， *ParameterSizePtr*現在也會傳回一個值，以與[ODBC 規格](https://go.microsoft.com/fwlink/?LinkId=207044)中所定義之對應參數標記的資料行或運算式大小（以字元為單位）的定義對齊。</span><span class="sxs-lookup"><span data-stu-id="c75b5-109">Also new in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], *ParameterSizePtr* now returns a value that aligns with the definition for the size, in characters, of the column or expression of the corresponding parameter marker as defined in the [ODBC specification](https://go.microsoft.com/fwlink/?LinkId=207044).</span></span> <span data-ttu-id="c75b5-110">在舊版的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 中， *ParameterSizePtr*可以是類型的對應值 `SQL_DESC_OCTET_LENGTH` ，或是針對類型提供給 SQLBindParameter 的不相關資料行大小值，應忽略 (的值 `SQL_INTEGER` ，例如) 。</span><span class="sxs-lookup"><span data-stu-id="c75b5-110">In previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client, *ParameterSizePtr* could be the corresponding value of `SQL_DESC_OCTET_LENGTH` for the type, or an irrelevant column size value that was supplied to SQLBindParameter for a type, the value of which should be ignored (`SQL_INTEGER`, for example).</span></span>  
  
 <span data-ttu-id="c75b5-111">在下列情況下，驅動程式不支援呼叫 SQLDescribeParam：</span><span class="sxs-lookup"><span data-stu-id="c75b5-111">The driver does not support calling SQLDescribeParam in the following situations:</span></span>  
  
-   <span data-ttu-id="c75b5-112">在 SQLExecDirect [!INCLUDE[tsql](../../includes/tsql-md.md)] 包含 from 子句的任何 UPDATE 或 DELETE 子句之後。</span><span class="sxs-lookup"><span data-stu-id="c75b5-112">After SQLExecDirect for any [!INCLUDE[tsql](../../includes/tsql-md.md)] UPDATE or DELETE statements containing the FROM clause.</span></span>  
  
-   <span data-ttu-id="c75b5-113">針對在 HAVING 子句中包含參數或與 SUM 函數的結果相比較的任何 ODBC 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c75b5-113">For any ODBC or [!INCLUDE[tsql](../../includes/tsql-md.md)] statement containing a parameter in a HAVING clause, or compared to the result of a SUM function.</span></span>  
  
-   <span data-ttu-id="c75b5-114">針對相依於包含參數之子查詢的任何 ODBC 或 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c75b5-114">For any ODBC or [!INCLUDE[tsql](../../includes/tsql-md.md)] statement depending on a subquery containing parameters.</span></span>  
  
-   <span data-ttu-id="c75b5-115">針對在比較 (like) 或定量述詞的運算式中都包含參數標記的 ODBC SQL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="c75b5-115">For ODBC SQL statements containing parameter markers in both expressions of a comparison, like, or quantified predicate.</span></span>  
  
-   <span data-ttu-id="c75b5-116">針對其中一個參數為函數參數的任何查詢。</span><span class="sxs-lookup"><span data-stu-id="c75b5-116">For any queries where one of the parameters is a parameter to a function.</span></span>  
  
-   <span data-ttu-id="c75b5-117">當命令中有 (/\* \* /) 的批註時 [!INCLUDE[tsql](../../includes/tsql-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="c75b5-117">When there are comments (/\* \*/) in the [!INCLUDE[tsql](../../includes/tsql-md.md)] command.</span></span>  
  
 <span data-ttu-id="c75b5-118">在處理語句批次時 [!INCLUDE[tsql](../../includes/tsql-md.md)] ，驅動程式也不支援在批次中的第一個語句之後，針對語句中的參數標記呼叫 SQLDescribeParam。</span><span class="sxs-lookup"><span data-stu-id="c75b5-118">When processing a batch of [!INCLUDE[tsql](../../includes/tsql-md.md)] statements, the driver also does not support calling SQLDescribeParam for parameter markers in statements after the first statement in the batch.</span></span>  
  
 <span data-ttu-id="c75b5-119">在描述已備妥預存程式的參數時，SQLDescribeParam 會使用系統預存程式[sp_sproc_columns](/sql/relational-databases/system-stored-procedures/sp-sproc-columns-transact-sql)來取得參數特性。</span><span class="sxs-lookup"><span data-stu-id="c75b5-119">When describing the parameters of prepared stored procedures, SQLDescribeParam uses the system stored procedure [sp_sproc_columns](/sql/relational-databases/system-stored-procedures/sp-sproc-columns-transact-sql) to retrieve parameter characteristics.</span></span> <span data-ttu-id="c75b5-120">sp_sproc_columns 可以報告目前使用者資料庫內預存程式的資料。</span><span class="sxs-lookup"><span data-stu-id="c75b5-120">sp_sproc_columns can report data for stored procedures within the current user database.</span></span> <span data-ttu-id="c75b5-121">準備完整的預存程式名稱，可讓 SQLDescribeParam 跨資料庫執行。</span><span class="sxs-lookup"><span data-stu-id="c75b5-121">Preparing a fully qualified stored procedure name allows SQLDescribeParam to execute across databases.</span></span> <span data-ttu-id="c75b5-122">例如，您可以在任何資料庫中準備和執行系統預存程式[sp_who](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) ，如下所示：</span><span class="sxs-lookup"><span data-stu-id="c75b5-122">For example, the system stored procedure [sp_who](/sql/relational-databases/system-stored-procedures/sp-who-transact-sql) can be prepared and executed in any database as:</span></span>  
  
```  
SQLPrepare(hstmt, "{call sp_who(?)}", SQL_NTS);  
```  
  
 <span data-ttu-id="c75b5-123">當成功準備之後執行 SQLDescribeParam 時，會在連接到任何資料庫時，傳回空的資料列集，但是 `master` 。</span><span class="sxs-lookup"><span data-stu-id="c75b5-123">Executing SQLDescribeParam after successful preparation returns an empty row set when connected to any database but `master`.</span></span> <span data-ttu-id="c75b5-124">無論目前的使用者資料庫為何，相同的呼叫（依照下列方式準備）都會導致 SQLDescribeParam 成功：</span><span class="sxs-lookup"><span data-stu-id="c75b5-124">The same call, prepared as follows, causes SQLDescribeParam to succeed regardless of the current user database:</span></span>  
  
```  
SQLPrepare(hstmt, "{call master..sp_who(?)}", SQL_NTS);  
```  
  
 <span data-ttu-id="c75b5-125">對於大數值資料類型，在*DataTypePtr*中傳回的值是 SQL_VARCHAR、SQL_VARBINARY 或 SQL_NVARCHAR。</span><span class="sxs-lookup"><span data-stu-id="c75b5-125">For large value data types, the value returned in *DataTypePtr* is SQL_VARCHAR, SQL_VARBINARY, or SQL_NVARCHAR.</span></span> <span data-ttu-id="c75b5-126">若要指出大數值資料類型參數的大小為「無限制」， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式會將*ParameterSizePtr*設定為0。</span><span class="sxs-lookup"><span data-stu-id="c75b5-126">To indicate that the size of the large value data type parameter is "unlimited," the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver sets *ParameterSizePtr* to 0.</span></span> <span data-ttu-id="c75b5-127">實際大小值則會以標準 `varchar` 參數傳回。</span><span class="sxs-lookup"><span data-stu-id="c75b5-127">Actual size values are returned for standard `varchar` parameters.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="c75b5-128">如果參數已與 SQL_VARCHAR、SQL_VARBINARY 或 SQL_WVARCHAR 參數的最大大小繫結，則會傳回參數的繫結大小，而不是「無限制」。</span><span class="sxs-lookup"><span data-stu-id="c75b5-128">If the parameter has already been bound with a maximum size for the SQL_VARCHAR, SQL_VARBINARY, or SQL_WVARCHAR parameters, the bound size of the parameter is returned, not "unlimited."</span></span>  
  
 <span data-ttu-id="c75b5-129">若要繫結「無限制」大小輸入參數，則必須使用資料執行中 (data-at-execution)。</span><span class="sxs-lookup"><span data-stu-id="c75b5-129">To bind an "unlimited" size input parameter, data-at-execution must be used.</span></span> <span data-ttu-id="c75b5-130">不可能會系結「無限制」大小輸出參數 (沒有從輸出參數串流資料的方法，例如[SQLGetData](sqlgetdata.md)對結果集) 的功能。</span><span class="sxs-lookup"><span data-stu-id="c75b5-130">It is not possible to bind an "unlimited" size output parameter (there is no method for streaming data from an output parameter, like [SQLGetData](sqlgetdata.md) does for result sets).</span></span>  
  
 <span data-ttu-id="c75b5-131">對輸出參數而言，必須繫結緩衝區，而且如果值過大，則緩衝區會填滿，並且傳回 SQL_SUCCESS_WITH_INFO 訊息及「字串資料；右側截斷」警告。</span><span class="sxs-lookup"><span data-stu-id="c75b5-131">For output parameters, a buffer must be bound and if the value is too large, the buffer is filled and a SQL_SUCCESS_WITH_INFO message and is returned along with the "string data; right truncation" warning.</span></span> <span data-ttu-id="c75b5-132">之後會捨棄截斷的資料。</span><span class="sxs-lookup"><span data-stu-id="c75b5-132">The data that was truncated is then discarded.</span></span>  
  
## <a name="sqldescribeparam-and-table-valued-parameters"></a><span data-ttu-id="c75b5-133">SQLDescribeParam 和資料表值參數</span><span class="sxs-lookup"><span data-stu-id="c75b5-133">SQLDescribeParam and Table-Valued Parameters</span></span>  
 <span data-ttu-id="c75b5-134">應用程式可以使用 SQLDescribeParam 來抓取備妥之語句的資料表值參數資訊。</span><span class="sxs-lookup"><span data-stu-id="c75b5-134">An application can retrieve table-valued parameter information for a prepared statement with SQLDescribeParam.</span></span> <span data-ttu-id="c75b5-135">如需詳細資訊，請參閱備妥之[語句的資料表值參數中繼資料](../native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md)。</span><span class="sxs-lookup"><span data-stu-id="c75b5-135">For more information, see [Table-Valued Parameter Metadata for Prepared Statements](../native-client-odbc-table-valued-parameters/table-valued-parameter-metadata-for-prepared-statements.md).</span></span>  
  
 <span data-ttu-id="c75b5-136">如需有關資料表值參數的一般詳細資訊，請參閱[ODBC&#41;&#40;的資料表值參數](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="c75b5-136">For more information about table-valued parameters in general, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqldescribeparam-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="c75b5-137">SQLDescribeParam 對增強日期和時間功能的支援</span><span class="sxs-lookup"><span data-stu-id="c75b5-137">SQLDescribeParam Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="c75b5-138">針對日期/時間類型所傳回的值如下：</span><span class="sxs-lookup"><span data-stu-id="c75b5-138">The values returned for date/time types are as follows:</span></span>  
  
||<span data-ttu-id="c75b5-139">*DataTypePtr*</span><span class="sxs-lookup"><span data-stu-id="c75b5-139">*DataTypePtr*</span></span>|<span data-ttu-id="c75b5-140">*ParameterSizePtr*</span><span class="sxs-lookup"><span data-stu-id="c75b5-140">*ParameterSizePtr*</span></span>|<span data-ttu-id="c75b5-141">*DecimalDigitsPtr*</span><span class="sxs-lookup"><span data-stu-id="c75b5-141">*DecimalDigitsPtr*</span></span>|  
|-|-------------------|------------------------|------------------------|  
|<span data-ttu-id="c75b5-142">Datetime</span><span class="sxs-lookup"><span data-stu-id="c75b5-142">datetime</span></span>|<span data-ttu-id="c75b5-143">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="c75b5-143">SQL_TYPE_TIMESTAMP</span></span>|<span data-ttu-id="c75b5-144">23</span><span class="sxs-lookup"><span data-stu-id="c75b5-144">23</span></span>|<span data-ttu-id="c75b5-145">3</span><span class="sxs-lookup"><span data-stu-id="c75b5-145">3</span></span>|  
|<span data-ttu-id="c75b5-146">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="c75b5-146">smalldatetime</span></span>|<span data-ttu-id="c75b5-147">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="c75b5-147">SQL_TYPE_TIMESTAMP</span></span>|<span data-ttu-id="c75b5-148">16</span><span class="sxs-lookup"><span data-stu-id="c75b5-148">16</span></span>|<span data-ttu-id="c75b5-149">0</span><span class="sxs-lookup"><span data-stu-id="c75b5-149">0</span></span>|  
|<span data-ttu-id="c75b5-150">date</span><span class="sxs-lookup"><span data-stu-id="c75b5-150">date</span></span>|<span data-ttu-id="c75b5-151">SQL_TYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="c75b5-151">SQL_TYPE_DATE</span></span>|<span data-ttu-id="c75b5-152">10</span><span class="sxs-lookup"><span data-stu-id="c75b5-152">10</span></span>|<span data-ttu-id="c75b5-153">0</span><span class="sxs-lookup"><span data-stu-id="c75b5-153">0</span></span>|  
|<span data-ttu-id="c75b5-154">time</span><span class="sxs-lookup"><span data-stu-id="c75b5-154">time</span></span>|<span data-ttu-id="c75b5-155">SQL_SS_TIME2</span><span class="sxs-lookup"><span data-stu-id="c75b5-155">SQL_SS_TIME2</span></span>|<span data-ttu-id="c75b5-156">8, 10..16</span><span class="sxs-lookup"><span data-stu-id="c75b5-156">8, 10..16</span></span>|<span data-ttu-id="c75b5-157">0..7</span><span class="sxs-lookup"><span data-stu-id="c75b5-157">0..7</span></span>|  
|<span data-ttu-id="c75b5-158">datetime2</span><span class="sxs-lookup"><span data-stu-id="c75b5-158">datetime2</span></span>|<span data-ttu-id="c75b5-159">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="c75b5-159">SQL_TYPE_TIMESTAMP</span></span>|<span data-ttu-id="c75b5-160">19, 21..27</span><span class="sxs-lookup"><span data-stu-id="c75b5-160">19, 21..27</span></span>|<span data-ttu-id="c75b5-161">0..7</span><span class="sxs-lookup"><span data-stu-id="c75b5-161">0..7</span></span>|  
|<span data-ttu-id="c75b5-162">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="c75b5-162">datetimeoffset</span></span>|<span data-ttu-id="c75b5-163">SQL_SS_TIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="c75b5-163">SQL_SS_TIMESTAMPOFFSET</span></span>|<span data-ttu-id="c75b5-164">26, 28..34</span><span class="sxs-lookup"><span data-stu-id="c75b5-164">26, 28..34</span></span>|<span data-ttu-id="c75b5-165">0..7</span><span class="sxs-lookup"><span data-stu-id="c75b5-165">0..7</span></span>|  
  
 <span data-ttu-id="c75b5-166">如需詳細資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="c75b5-166">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqldescribeparam-support-for-large-clr-udts"></a><span data-ttu-id="c75b5-167">大型 CLR UDT 的 SQLDescribeParam 支援</span><span class="sxs-lookup"><span data-stu-id="c75b5-167">SQLDescribeParam Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="c75b5-168">`SQLDescribeParam` 支援大型 CLR 使用者定義型別 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="c75b5-168">`SQLDescribeParam` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="c75b5-169">如需詳細資訊，請參閱[&#40;ODBC&#41;的大型 CLR 使用者定義類型](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="c75b5-169">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../../relational-databases/native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c75b5-170">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c75b5-170">See Also</span></span>  
 <span data-ttu-id="c75b5-171">[SQLDescribeParam 函式](https://go.microsoft.com/fwlink/?LinkId=59339) </span><span class="sxs-lookup"><span data-stu-id="c75b5-171">[SQLDescribeParam Function](https://go.microsoft.com/fwlink/?LinkId=59339) </span></span>  
 [<span data-ttu-id="c75b5-172">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="c75b5-172">ODBC API Implementation Details</span></span>](../../relational-databases/native-client-odbc-api/odbc-api-implementation-details.md)  
  
  
