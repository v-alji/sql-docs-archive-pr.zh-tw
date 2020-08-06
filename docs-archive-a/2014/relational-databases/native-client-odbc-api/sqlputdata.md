---
title: SQLPutData |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLPutData function
ms.assetid: d39aaa5b-7fbc-4315-a7f2-5a7787e04f25
author: rothja
ms.author: jroth
ms.openlocfilehash: 31da9c21f9e4323a492a25629a979c66a4f7d365
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606261"
---
# <a name="sqlputdata"></a><span data-ttu-id="0f985-102">SQLPutData</span><span class="sxs-lookup"><span data-stu-id="0f985-102">SQLPutData</span></span>
  <span data-ttu-id="0f985-103">當您使用 SQLPutData 來傳送超過65535個位元組的資料 (（適用于 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 版本 4.21 a) 或 400 KB 的資料 (6.0 SQL Server 用於) SQL_LONGVARCHAR (`text` 、) SQL_WLONGVARCHAR (或) SQL_LONGVARBINARY (資料行時，適用下列限制 `ntext` `image` ：</span><span class="sxs-lookup"><span data-stu-id="0f985-103">The following restrictions apply when using SQLPutData to send more than 65,535 bytes of data (for [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 4.21a) or 400 KB of data (for SQL Server version 6.0 and later) for a SQL_LONGVARCHAR (`text`), SQL_WLONGVARCHAR (`ntext`) or SQL_LONGVARBINARY (`image`) column:</span></span>  
  
-   <span data-ttu-id="0f985-104">參考的參數可以是 INSERT 語句中的*insert_value* 。</span><span class="sxs-lookup"><span data-stu-id="0f985-104">The referenced parameter can be the *insert_value* in an INSERT statement.</span></span>  
  
-   <span data-ttu-id="0f985-105">參考的參數可以是 UPDATE 語句的 SET 子句中的*運算式*。</span><span class="sxs-lookup"><span data-stu-id="0f985-105">The referenced parameter can be an *expression* in the SET clause of an UPDATE statement.</span></span>  
  
 <span data-ttu-id="0f985-106">在使用6.5 或更早版本時，取消將區塊中的資料提供給執行之伺服器的 SQLPutData 呼叫順序， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 會造成資料行值的部分更新。</span><span class="sxs-lookup"><span data-stu-id="0f985-106">Canceling a sequence of SQLPutData calls that provide data in blocks to a server running [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] causes a partial update of the column's value when using version 6.5 or earlier.</span></span> <span data-ttu-id="0f985-107">`text` `ntext` 呼叫 SQLCancel 時所參考的、或資料 `image` 行設定為中繼預留位置值。</span><span class="sxs-lookup"><span data-stu-id="0f985-107">The `text`, `ntext`, or `image` column that was referenced when SQLCancel was called is set to an intermediate placeholder value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="0f985-108">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 驅動程式不支援連接到 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 6.5 版和更早版本。</span><span class="sxs-lookup"><span data-stu-id="0f985-108">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC driver does not support connecting to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] version 6.5 and earlier.</span></span>  
  
## <a name="diagnostics"></a><span data-ttu-id="0f985-109">診斷</span><span class="sxs-lookup"><span data-stu-id="0f985-109">Diagnostics</span></span>  
 <span data-ttu-id="0f985-110">有一個 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 適用于 SQLPutData 的原生用戶端特定 SQLSTATE：</span><span class="sxs-lookup"><span data-stu-id="0f985-110">There is one [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client specific SQLSTATE for SQLPutData:</span></span>  
  
|<span data-ttu-id="0f985-111">SQLSTATE</span><span class="sxs-lookup"><span data-stu-id="0f985-111">SQLSTATE</span></span>|<span data-ttu-id="0f985-112">錯誤</span><span class="sxs-lookup"><span data-stu-id="0f985-112">Error</span></span>|<span data-ttu-id="0f985-113">描述</span><span class="sxs-lookup"><span data-stu-id="0f985-113">Description</span></span>|  
|--------------|-----------|-----------------|  
|<span data-ttu-id="0f985-114">22026</span><span class="sxs-lookup"><span data-stu-id="0f985-114">22026</span></span>|<span data-ttu-id="0f985-115">字串資料，長度不符</span><span class="sxs-lookup"><span data-stu-id="0f985-115">String data, length mismatch</span></span>|<span data-ttu-id="0f985-116">如果應用程式已指定要傳送的資料長度（以位元組為單位），例如，SQL_LEN_DATA_AT_EXEC (*n*) 其中*n*大於0，則應用程式透過 SQLPutData 所提供的位元組總數必須符合指定的長度。</span><span class="sxs-lookup"><span data-stu-id="0f985-116">If the length of data in bytes to be sent has been specified by an application, for example, with SQL_LEN_DATA_AT_EXEC(*n*) where *n* is greater than 0, the total number of bytes given by the application via SQLPutData must match the specified length.</span></span>|  
  
## <a name="sqlputdata-and-table-valued-parameters"></a><span data-ttu-id="0f985-117">SQLPutData 和資料表值參數</span><span class="sxs-lookup"><span data-stu-id="0f985-117">SQLPutData and Table-Valued Parameters</span></span>  
 <span data-ttu-id="0f985-118">當使用具有資料表值參數的變數資料列系結時，應用程式會使用 SQLPutData。</span><span class="sxs-lookup"><span data-stu-id="0f985-118">SQLPutData is used by an application when using variable row binding with table-valued parameters.</span></span> <span data-ttu-id="0f985-119">*StrLen_Or_Ind*參數表示已準備好讓驅動程式收集資料表值參數資料的下一個或多個資料列的資料，或沒有其他可用的資料列：</span><span class="sxs-lookup"><span data-stu-id="0f985-119">The *StrLen_Or_Ind* parameter indicates that it is ready for the driver to collect data for the next row or rows of table-valued parameter data, or that no more rows are available:</span></span>  
  
-   <span data-ttu-id="0f985-120">大於 0 的值表示有下一組資料列值。</span><span class="sxs-lookup"><span data-stu-id="0f985-120">A value greater than 0 indicates that the next set of row values is available.</span></span>  
  
-   <span data-ttu-id="0f985-121">0 這個值表示沒有其他要傳送的資料列。</span><span class="sxs-lookup"><span data-stu-id="0f985-121">A value of 0 indicates that there are no more rows to be sent.</span></span>  
  
-   <span data-ttu-id="0f985-122">小於 0 的任何值都是錯誤，而且會記錄 SQLState HY090 以及訊息「無效的字串或緩衝區長度」的診斷記錄。</span><span class="sxs-lookup"><span data-stu-id="0f985-122">Any value less than 0 is an error and results in a diagnostic record being logged with SQLState HY090 and the messaage "Invalid string or buffer length".</span></span>  
  
 <span data-ttu-id="0f985-123">*DataPtr*參數會被忽略，但必須設定為非 Null 值。</span><span class="sxs-lookup"><span data-stu-id="0f985-123">The *DataPtr* parameter is ignored, but must be set to a non-NULL value.</span></span> <span data-ttu-id="0f985-124">如需詳細資訊，請參閱在系結[和資料表值參數和資料行中的資料傳輸](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md)中的變數 TVP 資料列系結一節。</span><span class="sxs-lookup"><span data-stu-id="0f985-124">For more information, see the section on Variable TVP row binding in [Binding and Data Transfer of Table-Valued Parameters and Column Values](../native-client-odbc-table-valued-parameters/binding-and-data-transfer-of-table-valued-parameters-and-column-values.md).</span></span>  
  
 <span data-ttu-id="0f985-125">如果*StrLen_Or_Ind*具有 SQL_DEFAULT_PARAM 以外的任何值，或介於0和 SQL_PARAMSET_SIZE 之間的數位 (也就是說，SQLBindParameter) 的*ColumnSize*參數，就會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0f985-125">If *StrLen_Or_Ind* has any value other than SQL_DEFAULT_PARAM or a number between 0 and the SQL_PARAMSET_SIZE (that is, the *ColumnSize* parameter of SQLBindParameter), it is an error.</span></span> <span data-ttu-id="0f985-126">此錯誤會使 SQLPutData 傳回 SQL_ERROR：SQLSTATE=HY090，表示「無效的字串或緩衝區長度」。</span><span class="sxs-lookup"><span data-stu-id="0f985-126">This error causes SQLPutData to return SQL_ERROR: SQLSTATE=HY090, "Invalid string or buffer length".</span></span>  
  
 <span data-ttu-id="0f985-127">如需資料表值參數的詳細資訊，請參閱[ODBC&#41;&#40;的資料表值參數](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="0f985-127">For more information about table-valued parameters, see [Table-Valued Parameters &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md).</span></span>  
  
## <a name="sqlputdata-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="0f985-128">增強型日期和時間功能的 SQLPutData 支援</span><span class="sxs-lookup"><span data-stu-id="0f985-128">SQLPutData Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="0f985-129">日期/時間類型的參數值會依照[從 C 轉換成 SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md)中所述的方式進行轉換。</span><span class="sxs-lookup"><span data-stu-id="0f985-129">Parameter values of date/time types are converted as described in [Conversions from C to SQL](../native-client-odbc-date-time/datetime-data-type-conversions-from-c-to-sql.md).</span></span>  
  
 <span data-ttu-id="0f985-130">如需詳細資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="0f985-130">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="sqlputdata-support-for-large-clr-udts"></a><span data-ttu-id="0f985-131">大型 CLR UDT 的 SQLPutData 支援</span><span class="sxs-lookup"><span data-stu-id="0f985-131">SQLPutData Support for Large CLR UDTs</span></span>  
 <span data-ttu-id="0f985-132">`SQLPutData` 支援大型 CLR 使用者定義型別 (UDT)。</span><span class="sxs-lookup"><span data-stu-id="0f985-132">`SQLPutData` supports large CLR user-defined types (UDTs).</span></span> <span data-ttu-id="0f985-133">如需詳細資訊，請參閱[&#40;ODBC&#41;的大型 CLR 使用者定義類型](../native-client/odbc/large-clr-user-defined-types-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="0f985-133">For more information, see [Large CLR User-Defined Types &#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f985-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0f985-134">See Also</span></span>  
 <span data-ttu-id="0f985-135">[SQLPutData 函式](https://go.microsoft.com/fwlink/?LinkId=59365) </span><span class="sxs-lookup"><span data-stu-id="0f985-135">[SQLPutData Function](https://go.microsoft.com/fwlink/?LinkId=59365) </span></span>  
 [<span data-ttu-id="0f985-136">ODBC API 實作詳細資料</span><span class="sxs-lookup"><span data-stu-id="0f985-136">ODBC API Implementation Details</span></span>](odbc-api-implementation-details.md)  
  
  
