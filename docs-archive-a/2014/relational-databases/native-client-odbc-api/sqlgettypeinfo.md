---
title: SQLGetTypeInfo |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLGetTypeInfo function
ms.assetid: 13b982c3-ae03-4155-bc0d-e225050703ce
author: rothja
ms.author: jroth
ms.openlocfilehash: 3b2bca833eeed5e51237347a5ea118d839dd36de
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606281"
---
# <a name="sqlgettypeinfo"></a><span data-ttu-id="b018a-102">SQLGetTypeInfo</span><span class="sxs-lookup"><span data-stu-id="b018a-102">SQLGetTypeInfo</span></span>
  <span data-ttu-id="b018a-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native CLIENT ODBC 驅動程式會在的結果集中報告額外的資料行 USERTYPE `SQLGetTypeInfo` 。</span><span class="sxs-lookup"><span data-stu-id="b018a-103">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver reports the additional column USERTYPE in the result set of `SQLGetTypeInfo`.</span></span> <span data-ttu-id="b018a-104">USERTYPE 會報告 DB-Library 資料類型定義，而且對於將現有 DB-Library 應用程式移植至 ODBC 的開發人員很有用。</span><span class="sxs-lookup"><span data-stu-id="b018a-104">USERTYPE reports the DB-Library data type definition and is useful to developers porting existing DB-Library applications to ODBC.</span></span>  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="b018a-105">會將識別視為屬性，而 ODBC 則會將它視為資料類型。</span><span class="sxs-lookup"><span data-stu-id="b018a-105">treats identity as an attribute, whereas ODBC treats it as a data type.</span></span> <span data-ttu-id="b018a-106">若要解決這種不相符的情形，會傳回 `SQLGetTypeInfo` 資料類型： **intidentity**、 **Smallintidentity**、 **Tinyintidentity**、 **decimalidentity**和**numericidentity**。</span><span class="sxs-lookup"><span data-stu-id="b018a-106">To resolve this mismatch, `SQLGetTypeInfo` returns the data types: **intidentity**, **smallintidentity**, **tinyintidentity**, **decimalidentity**, and **numericidentity**.</span></span> <span data-ttu-id="b018a-107">[ `SQLGetTypeInfo` 結果集] 資料行 AUTO_UNIQUE_VALUE 報告這些資料類型的 TRUE 值。</span><span class="sxs-lookup"><span data-stu-id="b018a-107">The `SQLGetTypeInfo` result set column AUTO_UNIQUE_VALUE reports the value TRUE for these data types.</span></span>  
  
 <span data-ttu-id="b018a-108">若為**Varchar**、 **Nvarchar**和**Varbinary**， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式會繼續針對 COLUMN_SIZE 值分別報告8000、4000和8000，即使它實際上不受限制。</span><span class="sxs-lookup"><span data-stu-id="b018a-108">For **varchar**, **nvarchar** and **varbinary**, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver continues to report 8000, 4000 and 8000 respectively for the COLUMN_SIZE value, even though it is actually unlimited.</span></span> <span data-ttu-id="b018a-109">這為了確保回溯相容性。</span><span class="sxs-lookup"><span data-stu-id="b018a-109">This is to ensure backward compatibility.</span></span>  
  
 <span data-ttu-id="b018a-110">針對**xml**資料類型， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式會報告 COLUMN_SIZE 的 SQL_SS_LENGTH_UNLIMITED，以表示無限制的大小。</span><span class="sxs-lookup"><span data-stu-id="b018a-110">For the **xml** data type, the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver reports SQL_SS_LENGTH_UNLIMITED for COLUMN_SIZE to denote unlimited size.</span></span>  
  
## <a name="sqlgettypeinfo-and-table-valued-parameters"></a><span data-ttu-id="b018a-111">SQLGetTypeInfo 和資料表值參數</span><span class="sxs-lookup"><span data-stu-id="b018a-111">SQLGetTypeInfo and Table-Valued Parameters</span></span>  
 <span data-ttu-id="b018a-112">資料表值參數的資料表類型實際上是中繼類型，也就是用來定義其他類型的類型。</span><span class="sxs-lookup"><span data-stu-id="b018a-112">The table type for table-valued parameters is effectively a meta-type-that is, a type used to define other types.</span></span> <span data-ttu-id="b018a-113">因此，它不需要透過 SQLGetTypeInfo 公開。</span><span class="sxs-lookup"><span data-stu-id="b018a-113">Therefore, it does not have to be exposed through SQLGetTypeInfo.</span></span> <span data-ttu-id="b018a-114">應用程式必須使用 SQLTables （而非 SQLGetTypeInfo）來抓取與資料表值參數搭配使用之資料表類型的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="b018a-114">Applications must use SQLTables, rather than SQLGetTypeInfo, to retrieve metadata for table types used with table-valued parameters.</span></span>  
  
 <span data-ttu-id="b018a-115">如需有關為數據表值參數抓取 metdata 的詳細資訊，請參閱[影響資料表值參數的語句屬性](../native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md)。</span><span class="sxs-lookup"><span data-stu-id="b018a-115">For more information, about retrieving metdata for table-valued parameters, see [Statement Attributes that Affect Table-Valued Parameters](../native-client-odbc-table-valued-parameters/statement-attributes-that-affect-table-valued-parameters.md).</span></span>  
  
 <span data-ttu-id="b018a-116">如需資料表值參數的詳細資訊，請參閱[ODBC&#41;&#40;的資料表值參數](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="b018a-116">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlgettypeinfo-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="b018a-117">增強型日期和時間功能的 SQLGetTypeInfo 支援</span><span class="sxs-lookup"><span data-stu-id="b018a-117">SQLGetTypeInfo Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="b018a-118">如需日期/時間類型傳回的值，請參閱[目錄中繼資料](../native-client-odbc-date-time/metadata-catalog.md)。</span><span class="sxs-lookup"><span data-stu-id="b018a-118">For the values returned for date/time types, see [Catalog Metadata](../native-client-odbc-date-time/metadata-catalog.md).</span></span>  
  
 <span data-ttu-id="b018a-119">如需更多一般資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="b018a-119">For more general information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlgettypeinfo-support-for-large-clr-udts"></a><span data-ttu-id="b018a-120">大型 CLR UDT 的 SQLGetTypeInfo 支援</span><span class="sxs-lookup"><span data-stu-id="b018a-120">SQLGetTypeInfo Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="b018a-121">`SQLGetTypeInfo` 支援大型 CLR 使用者定義型別 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="b018a-121">`SQLGetTypeInfo` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="b018a-122">如需詳細資訊，請參閱[&#40;ODBC&#41;的大型 CLR 使用者定義類型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="b018a-122">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b018a-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b018a-123">See Also</span></span>  
 <span data-ttu-id="b018a-124">[SQLGetTypeInfo 函式](https://go.microsoft.com/fwlink/?LinkId=59356) </span><span class="sxs-lookup"><span data-stu-id="b018a-124">[SQLGetTypeInfo Function](https://go.microsoft.com/fwlink/?LinkId=59356) </span></span>  
 [<span data-ttu-id="b018a-125">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="b018a-125">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
