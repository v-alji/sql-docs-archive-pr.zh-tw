---
title: SQLSetDescField |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetDescField function
ms.assetid: de4bed15-15be-4825-994c-1046255e725a
author: rothja
ms.author: jroth
ms.openlocfilehash: 1b8290fd90c0c9bb91f08d94e119689d38fbc04e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606248"
---
# <a name="sqlsetdescfield"></a><span data-ttu-id="f54be-102">SQLSetDescField</span><span class="sxs-lookup"><span data-stu-id="f54be-102">SQLSetDescField</span></span>
  <span data-ttu-id="f54be-103">SQLSetDescField 可以用來設定資料表值參數和資料表值參數資料行的描述項欄位。</span><span class="sxs-lookup"><span data-stu-id="f54be-103">SQLSetDescField can be used to set descriptor fields for table-valued parameters and table-valued parameter columns.</span></span> <span data-ttu-id="f54be-104">如需可用欄位的詳細資訊，請參閱資料表值參數組成資料[行的](../native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md)[資料表值參數描述項欄位](../native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md)和描述項欄位。</span><span class="sxs-lookup"><span data-stu-id="f54be-104">For information about the available fields, see [Table-Valued Parameter Descriptor Fields](../native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md) and [Descriptor Fields for Table-Valued Parameter Constituent Columns](../native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f54be-105">備註</span><span class="sxs-lookup"><span data-stu-id="f54be-105">Remarks</span></span>  
 <span data-ttu-id="f54be-106">只有當描述項標頭欄位 SQL_SOPT_SS_PARAM_FOCUS 設定為將 SQL_DESC_TYPE 設定為 SQL_SS_TABLE 之記錄的序數時，才可使用資料表值參數資料行。</span><span class="sxs-lookup"><span data-stu-id="f54be-106">Table-valued parameter columns are only available when the descriptor header field SQL_SOPT_SS_PARAM_FOCUS is set to the ordinal of a record that has SQL_DESC_TYPE set to SQL_SS_TABLE.</span></span> <span data-ttu-id="f54be-107">如需 SQL_SOPT_SS_PARAM_FOCUS 的詳細資訊，請參閱[SQLSetStmtAttr](sqlsetstmtattr.md)。</span><span class="sxs-lookup"><span data-stu-id="f54be-107">For more information about SQL_SOPT_SS_PARAM_FOCUS, see [SQLSetStmtAttr](sqlsetstmtattr.md).</span></span>  
  
 <span data-ttu-id="f54be-108">如果嘗試將 SQL_SOPT_SS_PARAM_FOCUS 設定為不是資料表值參數之參數的序數，則 SQLSetStmtAttr 會傳回 SQL_ERROR，而且會使用 SQLSTATE = HY024 和訊息「不正確屬性值」來建立診斷記錄。</span><span class="sxs-lookup"><span data-stu-id="f54be-108">If an attempt is made to set SQL_SOPT_SS_PARAM_FOCUS to the ordinal of a parameter that is not a table-valued parameter, SQLSetStmtAttr returns SQL_ERROR, and a diagnostic record is created with SQLSTATE = HY024 and the message "Invalid attribute value".</span></span> <span data-ttu-id="f54be-109">當傳回 SQL_ERROR 時，SQL_SOPT_SS_PARAM_FOCUS 不會變更。</span><span class="sxs-lookup"><span data-stu-id="f54be-109">SQL_SOPT_SS_PARAM_FOCUS is not changed when SQL_ERROR is returned.</span></span>  
  
 <span data-ttu-id="f54be-110">將 SQL_SOPT_SS_PARAM_FOCUS 設定為 0 會還原參數之描述項記錄的存取權。</span><span class="sxs-lookup"><span data-stu-id="f54be-110">Setting SQL_SOPT_SS_PARAM_FOCUS to 0 restores access to descriptor records for parameters.</span></span>  
  
 <span data-ttu-id="f54be-111">如需資料表值參數的詳細資訊，請參閱[ODBC&#41;&#40;的資料表值參數](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="f54be-111">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlsetdescfield-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="f54be-112">增強型日期和時間功能的 SQLSetDescField 支援</span><span class="sxs-lookup"><span data-stu-id="f54be-112">SQLSetDescField Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="f54be-113">ODBC 中已經增強了日期/時間功能。</span><span class="sxs-lookup"><span data-stu-id="f54be-113">Date/time features have been enhanced in ODBC.</span></span> <span data-ttu-id="f54be-114">如需針對新日期/時間類型提供之描述項欄位的詳細資訊，請參閱[參數和結果中繼資料](../native-client-odbc-date-time/metadata-parameter-and-result.md)。</span><span class="sxs-lookup"><span data-stu-id="f54be-114">For information about the descriptor field provided for the new date/time types, see [Parameter and Result Metadata](../native-client-odbc-date-time/metadata-parameter-and-result.md).</span></span>  
  
 <span data-ttu-id="f54be-115">如需詳細資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="f54be-115">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlsetdescfield-support-for-large-clr-udts"></a><span data-ttu-id="f54be-116">大型 CLR UDT 的 SQLSetDescField 支援</span><span class="sxs-lookup"><span data-stu-id="f54be-116">SQLSetDescField Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="f54be-117">SQLSetDescField 支援 (Udt) 的大型 CLR 使用者定義類型。</span><span class="sxs-lookup"><span data-stu-id="f54be-117">SQLSetDescField supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="f54be-118">如需詳細資訊，請參閱[&#40;ODBC&#41;的大型 CLR 使用者定義類型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="f54be-118">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="sqlsetdescfield-support-for-sparse-columns"></a><span data-ttu-id="f54be-119">疏鬆資料行的 SQLSetDescField 支援</span><span class="sxs-lookup"><span data-stu-id="f54be-119">SQLSetDescField Support for Sparse Columns</span></span>  
 <span data-ttu-id="f54be-120">SQLSetDecField 可以用來將應用程式參數描述項中的 SQL_SOPT_SS_NAME_SCOPE 設定 (APD) SQL_SS_NAME_SCOPE_EXTENDED 和 SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET 的值。</span><span class="sxs-lookup"><span data-stu-id="f54be-120">SQLSetDecField can be used to set SQL_SOPT_SS_NAME_SCOPE in the application parameter descriptor (APD) to the values SQL_SS_NAME_SCOPE_EXTENDED and SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET.</span></span>  
  
 <span data-ttu-id="f54be-121">如需詳細資訊，請參閱[&#40;ODBC&#41;的稀疏資料行支援](../native-client/odbc/sparse-columns-support-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="f54be-121">For more information, see [Sparse Columns Support &#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f54be-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f54be-122">See Also</span></span>  
 <span data-ttu-id="f54be-123">[SQLSetDescField](https://go.microsoft.com/fwlink/?LinkId=80705) </span><span class="sxs-lookup"><span data-stu-id="f54be-123">[SQLSetDescField](https://go.microsoft.com/fwlink/?LinkId=80705) </span></span>  
 [<span data-ttu-id="f54be-124">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="f54be-124">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
