---
title: SQLGetDescField |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetDescField function
ms.assetid: 3e59a37a-28ee-4c91-8968-7fe3b966739d
author: rothja
ms.author: jroth
ms.openlocfilehash: 4538396dbfb5406d0464c4730c1f6f3bd5882799
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597106"
---
# <a name="sqlgetdescfield"></a><span data-ttu-id="f8f16-102">SQLGetDescField</span><span class="sxs-lookup"><span data-stu-id="f8f16-102">SQLGetDescField</span></span>
  <span data-ttu-id="f8f16-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式會公開「執行資料列描述項」的驅動程式特定描述項欄位，僅 (IRD) 。</span><span class="sxs-lookup"><span data-stu-id="f8f16-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver exposes driver-specific descriptor fields for the implementation row descriptor (IRD) only.</span></span> <span data-ttu-id="f8f16-104">在 IRD 內， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會透過驅動程式特有的資料行屬性來參考描述項欄位。</span><span class="sxs-lookup"><span data-stu-id="f8f16-104">Within the IRD, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] descriptor fields are referenced through driver-specific column attributes.</span></span> <span data-ttu-id="f8f16-105">如需可用驅動程式專屬描述項欄位的完整清單的詳細資訊，請參閱[SQLColAttribute](sqlcolattribute.md)。</span><span class="sxs-lookup"><span data-stu-id="f8f16-105">For information about a complete list of available driver-specific descriptor fields, see [SQLColAttribute](sqlcolattribute.md).</span></span>  
  
 <span data-ttu-id="f8f16-106">包含資料行識別項字串的描述項欄位常是零長度的字串。</span><span class="sxs-lookup"><span data-stu-id="f8f16-106">Descriptor fields that contain column identifier strings are often zero-length strings.</span></span> <span data-ttu-id="f8f16-107">所有 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特定的描述項欄位值都是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="f8f16-107">All [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific descriptor field values are read-only.</span></span>  
  
 <span data-ttu-id="f8f16-108">就像使用 SQLColAttribute 抓取的屬性一樣，會針對結果集中的所有資料行，報告資料列層級屬性 (例如 SQL_CA_SS_COMPUTE_ID) 的描述項欄位。</span><span class="sxs-lookup"><span data-stu-id="f8f16-108">Like attributes retrieved with SQLColAttribute, descriptor fields that report row-level attributes (such as SQL_CA_SS_COMPUTE_ID) are reported for all columns in the result set.</span></span>  
  
## <a name="sqlgetdescfield-and-table-valued-parameters"></a><span data-ttu-id="f8f16-109">SQLGetDescField 和資料表值參數</span><span class="sxs-lookup"><span data-stu-id="f8f16-109">SQLGetDescField and Table-Valued Parameters</span></span>  
 <span data-ttu-id="f8f16-110">SQLGetDescField 可以用來取得資料表值參數和資料表值參數資料行之擴充屬性的值。</span><span class="sxs-lookup"><span data-stu-id="f8f16-110">SQLGetDescField can be used to get values for extended attributes of table-valued parameters and table-valued parameter columns.</span></span> <span data-ttu-id="f8f16-111">如需資料表值參數的詳細資訊，請參閱[ODBC&#41;&#40;的資料表值參數](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="f8f16-111">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlgetdescfield-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="f8f16-112">增強型日期和時間功能的 SQLGetDescField 支援</span><span class="sxs-lookup"><span data-stu-id="f8f16-112">SQLGetDescField Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="f8f16-113">如需新日期/時間類型可用之描述項欄位的詳細資訊，請參閱[參數和結果中繼資料](../native-client-odbc-date-time/metadata-parameter-and-result.md)。</span><span class="sxs-lookup"><span data-stu-id="f8f16-113">For information about the descriptor fields available with the new date/time types, see [Parameter and Result Metadata](../native-client-odbc-date-time/metadata-parameter-and-result.md).</span></span>  
  
 <span data-ttu-id="f8f16-114">如需詳細資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="f8f16-114">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
 <span data-ttu-id="f8f16-115">從開始 [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] ， `SQL_C_SS_TIME2` `time` `SQL_C_SS_TIMESTAMPOFFSET` `datetimeoffset` `SQL_C_BINARY` 如果您的應用程式使用 ODBC 3.8，SQLGetDescField 可以傳回) 的 (類型) 或 (，而不是。</span><span class="sxs-lookup"><span data-stu-id="f8f16-115">Beginning in [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], SQLGetDescField can return `SQL_C_SS_TIME2` (for `time` types) or `SQL_C_SS_TIMESTAMPOFFSET` (for `datetimeoffset`) instead of `SQL_C_BINARY`, if your application uses ODBC 3.8.</span></span>  
  
## <a name="sqlgetdescfield-support-for-large-clr-udts"></a><span data-ttu-id="f8f16-116">大型 CLR UDT 的 SQLGetDescField 支援</span><span class="sxs-lookup"><span data-stu-id="f8f16-116">SQLGetDescField Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="f8f16-117">`SQLGetDescField` 支援大型 CLR 使用者定義型別 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="f8f16-117">`SQLGetDescField` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="f8f16-118">如需詳細資訊，請參閱[&#40;ODBC&#41;的大型 CLR 使用者定義類型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="f8f16-118">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="sqlgetdescfield-support-for-sparse-columns"></a><span data-ttu-id="f8f16-119">疏鬆資料行的 SQLGetDescField 支援</span><span class="sxs-lookup"><span data-stu-id="f8f16-119">SQLGetDescField Support for Sparse Columns</span></span>  
 <span data-ttu-id="f8f16-120">SQLGetDescField 可以用來查詢新的 IRD 欄位 SQL_CA_SS_IS_COLUMN_SET 來判斷資料行是否為數據行 `column_set` 。</span><span class="sxs-lookup"><span data-stu-id="f8f16-120">SQLGetDescField can be used to query the new IRD field SQL_CA_SS_IS_COLUMN_SET to determine if a column is a `column_set` column.</span></span>  
  
 <span data-ttu-id="f8f16-121">如需詳細資訊，請參閱[&#40;ODBC&#41;的稀疏資料行支援](../native-client/odbc/sparse-columns-support-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="f8f16-121">For more information, see [Sparse Columns Support &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8f16-122">範例</span><span class="sxs-lookup"><span data-stu-id="f8f16-122">Example</span></span>  
  
```  
typedef struct tagCOMPUTEBYLIST  
    {  
    SQLSMALLINT nBys;  
    SQLSMALLINT aByList[1];  
    } COMPUTEBYLIST;  
typedef COMPUTEBYLIST* PCOMPUTEBYLIST;   
  
SQLHDESC    hIRD;   
SQLINTEGER  cbIRD;   
SQLINTEGER  nSet = 0;   
  
// . . .  
// Execute a statement that contains a COMPUTE clause,  
//  then get the descriptor handle of the IRD and  
//  get some IRD values.  
  
SQLGetStmtAttr(g_hStmt, SQL_ATTR_IMP_ROW_DESC,  
    (SQLPOINTER) &hIRD, sizeof(SQLHDESC), &cbIRD);  
  
// For statement-wide column attributes, any  
//  descriptor record will do. You know that 1 exists,  
//  so use it.  
SQLGetDescField(hIRD, 1, SQL_CA_SS_NUM_COMPUTES,  
    (SQLPOINTER) &nComputes, SQL_IS_INTEGER, &cbIRD);  
  
if (nSet == 0)  
    {  
    SQLINTEGER      nOrderID;  
  
    printf_s("Normal result set.\n");  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ORDER,  
            (SQLPOINTER) &nOrderID, SQL_IS_INTEGER,  
            &cbIRD);  
  
        if (nOrderID != 0)  
            {  
            printf_s("Col in ORDER BY, pos: %ld",  
                nOrderID);  
            }  
            printf_s("\n");  
        }  
  
    printf_s("\n");  
    }  
else  
    {  
    PCOMPUTEBYLIST  pByList;  
    SQLSMALLINT     nBy;  
    SQLINTEGER      nColID;  
  
    printf_s("Computed result set number: %lu\n",  
        nSet);  
  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_BYLIST,  
        (SQLPOINTER) &pByList, SQL_IS_INTEGER,  
        &cbIRD);  
  
    if (pByList != NULL)  
        {  
        printf_s("Clause ordered by columns: ");  
        for (nBy = 0; nBy < pByList->nBys; )  
            {  
            printf_s("%u", pByList->aByList[nBy]);  
            nBy++;  
  
            if (nBy == pByList->nBys)  
                {  
                printf_s("\n");  
                }  
            else  
                {  
                printf_s(", ");  
                }  
            }  
        }  
    else  
        {  
        printf_s("Compute clause set not ordered.\n");  
        }  
  
    for (nCol = 0; nCol < nCols; nCol++)  
        {  
        SQLGetDescField(hIRD, nCol+1,  
            SQL_CA_SS_COLUMN_ID, (SQLPOINTER) &nColID,  
            SQL_IS_INTEGER, &cbIRD);  
        printf_s("ColumnID: %lu, nColID);  
        }  
    printf_s("\n");  
    }  
  
if (SQLMoreResults(g_hStmt) == SQL_SUCCESS)  
    {  
    // Determine the result set indicator.  
    SQLGetDescField(hIRD, 1, SQL_CA_SS_COMPUTE_ID,  
        (SQLPOINTER) &nSet, SQL_IS_INTEGER, &cbIRD);  
    }  
```  
  
## <a name="see-also"></a><span data-ttu-id="f8f16-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f8f16-123">See Also</span></span>  
 <span data-ttu-id="f8f16-124">[SQLGetDescField 函式](https://go.microsoft.com/fwlink/?LinkId=59351) </span><span class="sxs-lookup"><span data-stu-id="f8f16-124">[SQLGetDescField Function](https://go.microsoft.com/fwlink/?LinkId=59351) </span></span>  
 [<span data-ttu-id="f8f16-125">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="f8f16-125">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
