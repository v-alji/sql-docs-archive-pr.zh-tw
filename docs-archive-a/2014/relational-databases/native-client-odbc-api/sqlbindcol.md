---
title: SQLBindCol |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLBindCol function
ms.assetid: fbd7ba20-d917-4ca9-b018-018ac6af9f98
author: rothja
ms.author: jroth
ms.openlocfilehash: 72d0ca1b0fbad144117e409019d8d2247bbf918f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709398"
---
# <a name="sqlbindcol"></a><span data-ttu-id="7540e-102">SQLBindCol</span><span class="sxs-lookup"><span data-stu-id="7540e-102">SQLBindCol</span></span>
  <span data-ttu-id="7540e-103">作為一般規則，請考慮使用**SQLBindCol**來造成資料轉換的含意。</span><span class="sxs-lookup"><span data-stu-id="7540e-103">As a general rule, consider the implications of using **SQLBindCol** to cause data conversion.</span></span> <span data-ttu-id="7540e-104">例如，繫結轉換為用戶端處理序，所以擷取繫結至字元資料行的浮點值時，將會造成驅動程式在提取資料列時，於本機執行浮點對字元的轉換。</span><span class="sxs-lookup"><span data-stu-id="7540e-104">Binding conversions are client processes, so, for example, retrieving a floating-point value bound to a character column causes the driver to perform the float-to-character conversion locally when a row is fetched.</span></span> <span data-ttu-id="7540e-105">使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT 函數可將資料轉換的成本置於伺服器上。</span><span class="sxs-lookup"><span data-stu-id="7540e-105">The [!INCLUDE[tsql](../../includes/tsql-md.md)] CONVERT function can be used to place the cost of data conversion on the server.</span></span>  
  
 <span data-ttu-id="7540e-106">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體可以在單一陳述式執行中傳回多個結果資料列集。</span><span class="sxs-lookup"><span data-stu-id="7540e-106">An instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] can return multiple sets of result rows on a single statement execution.</span></span> <span data-ttu-id="7540e-107">每個結果集都必須個別繫結。</span><span class="sxs-lookup"><span data-stu-id="7540e-107">Each result set must be bound separately.</span></span> <span data-ttu-id="7540e-108">如需多個結果集之系結的詳細資訊，請參閱[SQLMoreResults](sqlmoreresults.md)。</span><span class="sxs-lookup"><span data-stu-id="7540e-108">For more information about binding for multiple result sets, see [SQLMoreResults](sqlmoreresults.md).</span></span>  
  
 <span data-ttu-id="7540e-109">開發人員可以使用 TargetType 值來將資料行系結至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特定的 C 資料*TargetType*類型 `SQL_C_BINARY` 。</span><span class="sxs-lookup"><span data-stu-id="7540e-109">The developer can bind columns to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific C data types using the *TargetType* value `SQL_C_BINARY`.</span></span> <span data-ttu-id="7540e-110">繫結至 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特有之類型的資料行無法移植。</span><span class="sxs-lookup"><span data-stu-id="7540e-110">Columns bound to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific types are not portable.</span></span> <span data-ttu-id="7540e-111">已定義的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 特有 ODBC C 資料類型符合 DB-Library 的類型定義，而移植應用程式的 DB-Library 開發人員可能會想要利用這項功能。</span><span class="sxs-lookup"><span data-stu-id="7540e-111">The defined [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]-specific ODBC C data types match the type definitions for DB-Library, and DB-Library developers porting applications may want to take advantage of this feature.</span></span>  
  
 <span data-ttu-id="7540e-112">報表資料截斷是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native CLIENT ODBC 驅動程式的昂貴進程。</span><span class="sxs-lookup"><span data-stu-id="7540e-112">Reporting data truncation is an expensive process for the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver.</span></span> <span data-ttu-id="7540e-113">您可以確保所有繫結的資料緩衝區都夠寬而足以傳回資料，藉此來避免資料遭到截斷。</span><span class="sxs-lookup"><span data-stu-id="7540e-113">You can avoid truncation by ensuring that all bound data buffers are wide enough to return data.</span></span> <span data-ttu-id="7540e-114">如果是字元資料，當使用字串結束的預設驅動程式行為時，寬度應該包括字串結束字元的空格。</span><span class="sxs-lookup"><span data-stu-id="7540e-114">For character data, the width should include space for a string terminator when the default driver behavior for string termination is used.</span></span> <span data-ttu-id="7540e-115">例如，將 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] \*\*char (5) \*\*資料行系結至五個字元的陣列，會導致每個提取的值截斷。</span><span class="sxs-lookup"><span data-stu-id="7540e-115">For example, binding a [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] **char(5)** column to an array of five characters results in truncation for every value fetched.</span></span> <span data-ttu-id="7540e-116">將相同的資料行繫結至六個字元的陣列可藉由提供字元元素來儲存 Null 結束字元，以避免截斷的情況發生。</span><span class="sxs-lookup"><span data-stu-id="7540e-116">Binding the same column to an array of six characters avoids the truncation by providing a character element in which to store the null terminator.</span></span> <span data-ttu-id="7540e-117">[SQLGetData](sqlgetdata.md)可以用來有效率地抓取長字元和二進位資料，而不會進行截斷。</span><span class="sxs-lookup"><span data-stu-id="7540e-117">[SQLGetData](sqlgetdata.md) can be used to efficiently retrieve long character and binary data without truncation.</span></span>  
  
 <span data-ttu-id="7540e-118">對於大數值資料類型，如果使用者提供的緩衝區不夠大，無法保存資料行的整個值， `SQL_SUCCESS_WITH_INFO` 則會傳回和「字串資料;右側截斷」警告。</span><span class="sxs-lookup"><span data-stu-id="7540e-118">For large value data types, if the user supplied buffer isn't large enough to hold the entire value of the column, `SQL_SUCCESS_WITH_INFO` is returned and the "string data; right truncation" warning is issued.</span></span> <span data-ttu-id="7540e-119">`StrLen_or_IndPtr` 引數將會包含儲存在緩衝區內的字元/位元組數目。</span><span class="sxs-lookup"><span data-stu-id="7540e-119">The `StrLen_or_IndPtr` argument will contain the number of chars/bytes stored in the buffer.</span></span>  
  
## <a name="sqlbindcol-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="7540e-120">SQLBindCol 對於增強型日期和時間功能的支援</span><span class="sxs-lookup"><span data-stu-id="7540e-120">SQLBindCol Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="7540e-121">日期/時間類型的結果資料行值會轉換，如[從 SQL 轉換為 C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md)中所述。請注意，若要取出 time 和 datetimeoffset 資料行做為其對應的結構 (`SQL_SS_TIME2_STRUCT` 並**SQL_SS_TIMESTAMPOFFSET_STRUCT**) ， *TargetType*必須指定為 `SQL_C_DEFAULT` 或 `SQL_C_BINARY` 。</span><span class="sxs-lookup"><span data-stu-id="7540e-121">Result column values of date/time types are converted as described in [Conversions from SQL to C](../native-client-odbc-date-time/datetime-data-type-conversions-from-sql-to-c.md). Note that to retrieve time and datetimeoffset columns as their corresponding structures (`SQL_SS_TIME2_STRUCT` and **SQL_SS_TIMESTAMPOFFSET_STRUCT**), *TargetType* must be specified as `SQL_C_DEFAULT` or `SQL_C_BINARY`.</span></span>  
  
 <span data-ttu-id="7540e-122">如需詳細資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="7540e-122">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlbindcol-support-for-large-clr-udts"></a><span data-ttu-id="7540e-123">SQLBindCol 對於大型 CLR UDT 的支援</span><span class="sxs-lookup"><span data-stu-id="7540e-123">SQLBindCol Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="7540e-124">**SQLBindCol**支援 (udt) 的大型 CLR 使用者定義類型。</span><span class="sxs-lookup"><span data-stu-id="7540e-124">**SQLBindCol** supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="7540e-125">如需詳細資訊，請參閱[&#40;ODBC&#41;的大型 CLR 使用者定義類型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="7540e-125">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7540e-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7540e-126">See Also</span></span>  
 <span data-ttu-id="7540e-127">[SQLBindCol 函式](https://go.microsoft.com/fwlink/?LinkId=59327) </span><span class="sxs-lookup"><span data-stu-id="7540e-127">[SQLBindCol Function](https://go.microsoft.com/fwlink/?LinkId=59327) </span></span>  
 [<span data-ttu-id="7540e-128">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="7540e-128">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
