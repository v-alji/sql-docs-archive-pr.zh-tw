---
title: SQLProcedureColumns |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLProcedureColumns function
ms.assetid: 6671e180-0072-4de5-90f5-314306d2ba9c
author: rothja
ms.author: jroth
ms.openlocfilehash: 66814c4d79108b2bb2c829a5e522d45d7eeaed22
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606264"
---
# <a name="sqlprocedurecolumns"></a><span data-ttu-id="d86fa-102">SQLProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="d86fa-102">SQLProcedureColumns</span></span>
  <span data-ttu-id="d86fa-103">`SQLProcedureColumns`傳回一個資料列，報告所有預存程式的傳回值屬性 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d86fa-103">`SQLProcedureColumns` returns one row reporting the return value attributes of all [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] stored procedures.</span></span>  
  
 <span data-ttu-id="d86fa-104">`SQLProcedureColumns`傳回 SQL_SUCCESS *CatalogName*、 *SchemaName*、 *ProcName*或*ColumnName*參數值是否存在。</span><span class="sxs-lookup"><span data-stu-id="d86fa-104">`SQLProcedureColumns` returns SQL_SUCCESS whether or not values exist for *CatalogName*, *SchemaName*, *ProcName*, or *ColumnName* parameters.</span></span> <span data-ttu-id="d86fa-105">當這些參數中使用了不正確值時， **SQLFetch**會傳回 SQL_NO_DATA。</span><span class="sxs-lookup"><span data-stu-id="d86fa-105">**SQLFetch** returns SQL_NO_DATA when invalid values are used in these parameters.</span></span>  
  
 <span data-ttu-id="d86fa-106">`SQLProcedureColumns` 可以在靜態伺服器資料指標上執行。</span><span class="sxs-lookup"><span data-stu-id="d86fa-106">`SQLProcedureColumns` can be executed on a static server cursor.</span></span> <span data-ttu-id="d86fa-107">嘗試在可更新的 (動態或索引鍵集) 資料指標上執行 `SQLProcedureColumns` 時，將會傳回 SQL_SUCCESS_WITH_INFO，表示資料指標類型已變更。</span><span class="sxs-lookup"><span data-stu-id="d86fa-107">An attempt to execute `SQLProcedureColumns` on an updatable (dynamic or keyset) cursor will return SQL_SUCCESS_WITH_INFO indicating that the cursor type has been changed.</span></span>  
  
 <span data-ttu-id="d86fa-108">下表列出結果集所傳回的資料行，以及如何透過 Native Client ODBC 驅動程式擴充以處理**udt**和**xml**資料類型 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ：</span><span class="sxs-lookup"><span data-stu-id="d86fa-108">The following table lists the columns returned by the result set and how they have been extended to handle the **udt** and **xml** data types through the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver:</span></span>  
  
|<span data-ttu-id="d86fa-109">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="d86fa-109">Column name</span></span>|<span data-ttu-id="d86fa-110">描述</span><span class="sxs-lookup"><span data-stu-id="d86fa-110">Description</span></span>|  
|-----------------|-----------------|  
|<span data-ttu-id="d86fa-111">SS_UDT_CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="d86fa-111">SS_UDT_CATALOG_NAME</span></span>|<span data-ttu-id="d86fa-112">傳回包含 UDT (使用者定義型別) 之目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="d86fa-112">Returns the name of the catalog containing the UDT (user-defined type).</span></span>|  
|<span data-ttu-id="d86fa-113">SS_UDT_SCHEMA_NAME</span><span class="sxs-lookup"><span data-stu-id="d86fa-113">SS_UDT_SCHEMA_NAME</span></span>|<span data-ttu-id="d86fa-114">傳回包含 UDT 之結構描述的名稱。</span><span class="sxs-lookup"><span data-stu-id="d86fa-114">Returns the name of the schema containing the UDT.</span></span>|  
|<span data-ttu-id="d86fa-115">SS_UDT_ASSEMBLY_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d86fa-115">SS_UDT_ASSEMBLY_TYPE_NAME</span></span>|<span data-ttu-id="d86fa-116">傳回 UDT 的組件完整名稱。</span><span class="sxs-lookup"><span data-stu-id="d86fa-116">Returns the assembly-qualified name of the UDT.</span></span>|  
|<span data-ttu-id="d86fa-117">SS_XML_SCHEMACOLLECTION_CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="d86fa-117">SS_XML_SCHEMACOLLECTION_CATALOG_NAME</span></span>|<span data-ttu-id="d86fa-118">傳回定義 XML 結構描述集合名稱所在目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="d86fa-118">Returns the name of the catalog where an XML schema collection name is defined.</span></span> <span data-ttu-id="d86fa-119">如果找不到目錄名稱，則此變數包含空字串。</span><span class="sxs-lookup"><span data-stu-id="d86fa-119">If the catalog name cannot be found, then this variable contains an empty string.</span></span>|  
|<span data-ttu-id="d86fa-120">SS_XML_SCHEMACOLLECTION_SCHEMA_NAME</span><span class="sxs-lookup"><span data-stu-id="d86fa-120">SS_XML_SCHEMACOLLECTION_SCHEMA_NAME</span></span>|<span data-ttu-id="d86fa-121">傳回定義 XML 結構描述集合名稱所在結構描述的名稱。</span><span class="sxs-lookup"><span data-stu-id="d86fa-121">Returns the name of the schema where an XML schema collection name is defined.</span></span> <span data-ttu-id="d86fa-122">如果找不到結構描述名稱，則此變數包含空字串。</span><span class="sxs-lookup"><span data-stu-id="d86fa-122">If the schema name cannot be found, then this variable contains an empty string.</span></span>|  
|<span data-ttu-id="d86fa-123">SS_XML_SCHEMACOLLECTION_NAME</span><span class="sxs-lookup"><span data-stu-id="d86fa-123">SS_XML_SCHEMACOLLECTION_NAME</span></span>|<span data-ttu-id="d86fa-124">傳回 XML 結構描述集合的名稱。</span><span class="sxs-lookup"><span data-stu-id="d86fa-124">Returns the name of an XML schema collection.</span></span> <span data-ttu-id="d86fa-125">如果找不到名稱，則此變數包含空字串。</span><span class="sxs-lookup"><span data-stu-id="d86fa-125">If the name cannot be found, then this variable contains an empty string.</span></span>|  
  
## <a name="sqlprocedurecolumns-and-table-valued-parameters"></a><span data-ttu-id="d86fa-126">SQLProcedureColumns 和資料表值參數</span><span class="sxs-lookup"><span data-stu-id="d86fa-126">SQLProcedureColumns and Table-Valued Parameters</span></span>  
 <span data-ttu-id="d86fa-127">SQLProcedureColumns 會以類似 CLR 使用者自訂類型的方式來處理資料表值參數。</span><span class="sxs-lookup"><span data-stu-id="d86fa-127">SQLProcedureColumns handles table-valued parameters in a manner similar to CLR user-defined types.</span></span> <span data-ttu-id="d86fa-128">在針對資料表值參數傳回的資料列中，資料行包含下列值：</span><span class="sxs-lookup"><span data-stu-id="d86fa-128">In rows returned for table-valued parameters, columns have the following values:</span></span>  
  
|<span data-ttu-id="d86fa-129">資料行名稱</span><span class="sxs-lookup"><span data-stu-id="d86fa-129">Column name</span></span>|<span data-ttu-id="d86fa-130">描述/值</span><span class="sxs-lookup"><span data-stu-id="d86fa-130">Description/value</span></span>|  
|-----------------|------------------------|  
|<span data-ttu-id="d86fa-131">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d86fa-131">DATA_TYPE</span></span>|<span data-ttu-id="d86fa-132">SQL_SS_TABLE</span><span class="sxs-lookup"><span data-stu-id="d86fa-132">SQL_SS_TABLE</span></span>|  
|<span data-ttu-id="d86fa-133">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="d86fa-133">TYPE_NAME</span></span>|<span data-ttu-id="d86fa-134">資料表值參數的資料表類型名稱。</span><span class="sxs-lookup"><span data-stu-id="d86fa-134">The name of the table type for the table-valued parameter.</span></span>|  
|<span data-ttu-id="d86fa-135">COLUMN_SIZE</span><span class="sxs-lookup"><span data-stu-id="d86fa-135">COLUMN_SIZE</span></span>|<span data-ttu-id="d86fa-136">NULL</span><span class="sxs-lookup"><span data-stu-id="d86fa-136">NULL</span></span>|  
|<span data-ttu-id="d86fa-137">BUFFER_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d86fa-137">BUFFER_LENGTH</span></span>|<span data-ttu-id="d86fa-138">0</span><span class="sxs-lookup"><span data-stu-id="d86fa-138">0</span></span>|  
|<span data-ttu-id="d86fa-139">DECIMAL_DIGITS</span><span class="sxs-lookup"><span data-stu-id="d86fa-139">DECIMAL_DIGITS</span></span>|<span data-ttu-id="d86fa-140">資料表值參數中，資料行的計數。</span><span class="sxs-lookup"><span data-stu-id="d86fa-140">The number of columns in the table-valued parameter.</span></span>|  
|<span data-ttu-id="d86fa-141">NUM_PREC_RADIX</span><span class="sxs-lookup"><span data-stu-id="d86fa-141">NUM_PREC_RADIX</span></span>|<span data-ttu-id="d86fa-142">NULL</span><span class="sxs-lookup"><span data-stu-id="d86fa-142">NULL</span></span>|  
|<span data-ttu-id="d86fa-143">NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d86fa-143">NULLABLE</span></span>|<span data-ttu-id="d86fa-144">SQL_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d86fa-144">SQL_NULLABLE</span></span>|  
|<span data-ttu-id="d86fa-145">REMARKS</span><span class="sxs-lookup"><span data-stu-id="d86fa-145">REMARKS</span></span>|<span data-ttu-id="d86fa-146">NULL</span><span class="sxs-lookup"><span data-stu-id="d86fa-146">NULL</span></span>|  
|<span data-ttu-id="d86fa-147">COLUMN_DEF</span><span class="sxs-lookup"><span data-stu-id="d86fa-147">COLUMN_DEF</span></span>|<span data-ttu-id="d86fa-148">NULL。</span><span class="sxs-lookup"><span data-stu-id="d86fa-148">NULL.</span></span> <span data-ttu-id="d86fa-149">資料表類型可能沒有預設值。</span><span class="sxs-lookup"><span data-stu-id="d86fa-149">Table types might not have default values.</span></span>|  
|<span data-ttu-id="d86fa-150">SQL_DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="d86fa-150">SQL_DATA_TYPE</span></span>|<span data-ttu-id="d86fa-151">SQL_SS_TABLE</span><span class="sxs-lookup"><span data-stu-id="d86fa-151">SQL_SS_TABLE</span></span>|  
|<span data-ttu-id="d86fa-152">SQL_DATEIME_SUB</span><span class="sxs-lookup"><span data-stu-id="d86fa-152">SQL_DATEIME_SUB</span></span>|<span data-ttu-id="d86fa-153">NULL</span><span class="sxs-lookup"><span data-stu-id="d86fa-153">NULL</span></span>|  
|<span data-ttu-id="d86fa-154">CHAR_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="d86fa-154">CHAR_OCTET_LENGTH</span></span>|<span data-ttu-id="d86fa-155">NULL</span><span class="sxs-lookup"><span data-stu-id="d86fa-155">NULL</span></span>|  
|<span data-ttu-id="d86fa-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="d86fa-156">IS_NULLABLE</span></span>|<span data-ttu-id="d86fa-157">"YES"</span><span class="sxs-lookup"><span data-stu-id="d86fa-157">"YES"</span></span>|  
|<span data-ttu-id="d86fa-158">SS_TYPE_CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="d86fa-158">SS_TYPE_CATALOG_NAME</span></span>|<span data-ttu-id="d86fa-159">傳回包含資料表或 CLR 使用者定義型別之目錄的名稱。</span><span class="sxs-lookup"><span data-stu-id="d86fa-159">Returns the name of the catalog that contains the table or CLR user-defined type.</span></span>|  
|<span data-ttu-id="d86fa-160">SS_TYPE_SCHEMA_NAME</span><span class="sxs-lookup"><span data-stu-id="d86fa-160">SS_TYPE_SCHEMA_NAME</span></span>|<span data-ttu-id="d86fa-161">傳回包含資料表或 CLR 使用者定義型別之結構描述的名稱。</span><span class="sxs-lookup"><span data-stu-id="d86fa-161">Returns the name of the schema that contains the table or CLR user-defined type.</span></span>|  
  
 <span data-ttu-id="d86fa-162">SS_TYPE_CATALOG_NAME 和 SS_TYPE_SCHEMA_NAME 資料行會在 [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] 和更新版本中提供，以便針對資料表值參數個別傳回目錄與結構描述。</span><span class="sxs-lookup"><span data-stu-id="d86fa-162">The SS_TYPE_CATALOG_NAME and SS_TYPE_SCHEMA_NAME columns are available in [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] and later versions to return the catalog and schema, respectively, for table-valued parameters.</span></span> <span data-ttu-id="d86fa-163">這些資料行會針對資料表值參數及 CLR 使用者定義型別參數擴展 </span><span class="sxs-lookup"><span data-stu-id="d86fa-163">These columns are populated for table-valued parameters, and also for CLR user-defined type parameters.</span></span> <span data-ttu-id="d86fa-164">(CLR 使用者定義型別參數的現有結構描述與目錄不會受到這個額外功能的影響。</span><span class="sxs-lookup"><span data-stu-id="d86fa-164">(Existing schema and catalog columns for CLR user-defined type parameters are not affected by this additional functionality.</span></span> <span data-ttu-id="d86fa-165">系統也會擴展它們來維護回溯相容性)。</span><span class="sxs-lookup"><span data-stu-id="d86fa-165">They are also populated to maintain backward compatibility).</span></span>  
  
 <span data-ttu-id="d86fa-166">依照 ODBC 規格規定，SS_TYPE_CATALOG_NAME 和 SS_TYPE_SCHEMA_NAME 會出現在舊版 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中所加入的所有驅動程式專用資料行之前，以及 ODBC 本身所託管的所有資料行之後。</span><span class="sxs-lookup"><span data-stu-id="d86fa-166">In conformance with the ODBC specification, SS_TYPE_CATALOG_NAME and SS_TYPE_SCHEMA_NAME appear before all driver-specific columns added in previous versions of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], and after all columns mandated by ODBC itself.</span></span>  
  
 <span data-ttu-id="d86fa-167">如需資料表值參數的詳細資訊，請參閱[ODBC&#41;&#40;的資料表值參數](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="d86fa-167">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlprocedurecolumns-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="d86fa-168">SQLProcedureColumns 對增強日期和時間功能的支援</span><span class="sxs-lookup"><span data-stu-id="d86fa-168">SQLProcedureColumns Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="d86fa-169">如需日期/時間類型傳回的值，請參閱[目錄中繼資料](../native-client-odbc-date-time/metadata-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="d86fa-169">For the values returned for date/time types, see [Catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md).</span></span>  
  
 <span data-ttu-id="d86fa-170">如需更多一般資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="d86fa-170">For more general information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlprocedurecolumns-support-for-large-clr-udts"></a><span data-ttu-id="d86fa-171">SQLProcedureColumns 對大型 CLR UDT 的支援</span><span class="sxs-lookup"><span data-stu-id="d86fa-171">SQLProcedureColumns Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="d86fa-172">`SQLProcedureColumns` 支援大型 CLR 使用者定義型別 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="d86fa-172">`SQLProcedureColumns` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="d86fa-173">如需詳細資訊，請參閱[&#40;ODBC&#41;的大型 CLR 使用者定義類型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="d86fa-173">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d86fa-174">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d86fa-174">See Also</span></span>  
 <span data-ttu-id="d86fa-175">[SQLProcedureColumns 函式](https://go.microsoft.com/fwlink/?LinkId=59363) </span><span class="sxs-lookup"><span data-stu-id="d86fa-175">[SQLProcedureColumns Function](https://go.microsoft.com/fwlink/?LinkId=59363) </span></span>  
 [<span data-ttu-id="d86fa-176">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="d86fa-176">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
