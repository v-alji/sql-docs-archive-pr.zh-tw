---
title: 對 OLE DB 日期和時間改善的資料類型支援 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- date/time [OLE DB], data type support
- OLE DB, date/time improvements
ms.assetid: d40e3fd6-9057-4371-8236-95cef300603e
author: rothja
ms.author: jroth
ms.openlocfilehash: 834583fdec63a8f613e623c239f9c3a1c9398950
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706414"
---
# <a name="data-type-support-for-ole-db-date-and-time-improvements"></a><span data-ttu-id="f1307-102">對 OLE DB 日期和時間改善的資料類型支援</span><span class="sxs-lookup"><span data-stu-id="f1307-102">Data Type Support for OLE DB Date and Time Improvements</span></span>
  <span data-ttu-id="f1307-103">本主題提供有關支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期/時間資料類型之 OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) 類型的資訊。</span><span class="sxs-lookup"><span data-stu-id="f1307-103">This topic provides information about OLE DB ([!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client) types that support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date/time data types.</span></span>  
  
## <a name="data-type-mapping-in-rowsets-and-parameters"></a><span data-ttu-id="f1307-104">資料列集和參數中的資料類型對應</span><span class="sxs-lookup"><span data-stu-id="f1307-104">Data Type Mapping in Rowsets and Parameters</span></span>  
 <span data-ttu-id="f1307-105">OLE DB 提供兩種新的資料類型來支援新的伺服器類型：DBTYPE_DBTIME2 和 DBTYPE_DBTIMESTAMPOFFSET。</span><span class="sxs-lookup"><span data-stu-id="f1307-105">OLE DB provides two new data types to support the new server types: DBTYPE_DBTIME2 and DBTYPE_DBTIMESTAMPOFFSET.</span></span> <span data-ttu-id="f1307-106">下表顯示完整伺服器類型的對應：</span><span class="sxs-lookup"><span data-stu-id="f1307-106">The following table shows the complete server type mapping:</span></span>  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f1307-107">資料類型</span><span class="sxs-lookup"><span data-stu-id="f1307-107">data type</span></span>|<span data-ttu-id="f1307-108">OLE DB 資料類型</span><span class="sxs-lookup"><span data-stu-id="f1307-108">OLE DB data type</span></span>|<span data-ttu-id="f1307-109">值</span><span class="sxs-lookup"><span data-stu-id="f1307-109">Value</span></span>|  
|-----------------------------------------|----------------------|-----------|  
|<span data-ttu-id="f1307-110">Datetime</span><span class="sxs-lookup"><span data-stu-id="f1307-110">datetime</span></span>|<span data-ttu-id="f1307-111">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="f1307-111">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="f1307-112">135 (oledb.h)</span><span class="sxs-lookup"><span data-stu-id="f1307-112">135 (oledb.h)</span></span>|  
|<span data-ttu-id="f1307-113">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="f1307-113">smalldatetime</span></span>|<span data-ttu-id="f1307-114">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="f1307-114">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="f1307-115">135 (oledb.h)</span><span class="sxs-lookup"><span data-stu-id="f1307-115">135 (oledb.h)</span></span>|  
|<span data-ttu-id="f1307-116">date</span><span class="sxs-lookup"><span data-stu-id="f1307-116">date</span></span>|<span data-ttu-id="f1307-117">DBTYPE_DBDATE</span><span class="sxs-lookup"><span data-stu-id="f1307-117">DBTYPE_DBDATE</span></span>|<span data-ttu-id="f1307-118">133 (oledb.h)</span><span class="sxs-lookup"><span data-stu-id="f1307-118">133 (oledb.h)</span></span>|  
|<span data-ttu-id="f1307-119">time</span><span class="sxs-lookup"><span data-stu-id="f1307-119">time</span></span>|<span data-ttu-id="f1307-120">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="f1307-120">DBTYPE_DBTIME2</span></span>|<span data-ttu-id="f1307-121">145 (sqlncli) </span><span class="sxs-lookup"><span data-stu-id="f1307-121">145 (sqlncli.h)</span></span>|  
|<span data-ttu-id="f1307-122">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="f1307-122">datetimeoffset</span></span>|<span data-ttu-id="f1307-123">DBTYPE_DBTIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="f1307-123">DBTYPE_DBTIMESTAMPOFFSET</span></span>|<span data-ttu-id="f1307-124">146 (sqlncli) </span><span class="sxs-lookup"><span data-stu-id="f1307-124">146 (sqlncli.h)</span></span>|  
|<span data-ttu-id="f1307-125">datetime2</span><span class="sxs-lookup"><span data-stu-id="f1307-125">datetime2</span></span>|<span data-ttu-id="f1307-126">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="f1307-126">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="f1307-127">135 (oledb.h)</span><span class="sxs-lookup"><span data-stu-id="f1307-127">135 (oledb.h)</span></span>|  
  
## <a name="data-formats-strings-and-literals"></a><span data-ttu-id="f1307-128">資料格式：字串和常值</span><span class="sxs-lookup"><span data-stu-id="f1307-128">Data Formats: Strings and Literals</span></span>  
  
|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f1307-129">資料類型</span><span class="sxs-lookup"><span data-stu-id="f1307-129">data type</span></span>|<span data-ttu-id="f1307-130">OLE DB 資料類型</span><span class="sxs-lookup"><span data-stu-id="f1307-130">OLE DB data type</span></span>|<span data-ttu-id="f1307-131">用於用戶端轉換的字串格式</span><span class="sxs-lookup"><span data-stu-id="f1307-131">String format for client conversions</span></span>|  
|-----------------------------------------|----------------------|------------------------------------------|  
|<span data-ttu-id="f1307-132">Datetime</span><span class="sxs-lookup"><span data-stu-id="f1307-132">datetime</span></span>|<span data-ttu-id="f1307-133">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="f1307-133">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="f1307-134">'yyyy-mm-dd hh:mm:ss[.999]'</span><span class="sxs-lookup"><span data-stu-id="f1307-134">'yyyy-mm-dd hh:mm:ss[.999]'</span></span><br /><br /> <span data-ttu-id="f1307-135">針對 Datetime，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 最多支援三個小數秒位數。</span><span class="sxs-lookup"><span data-stu-id="f1307-135">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports up to three fractional second digits for Datetime.</span></span>|  
|<span data-ttu-id="f1307-136">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="f1307-136">smalldatetime</span></span>|<span data-ttu-id="f1307-137">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="f1307-137">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="f1307-138">'yyyy-mm-dd hh:mm:ss'</span><span class="sxs-lookup"><span data-stu-id="f1307-138">'yyyy-mm-dd hh:mm:ss'</span></span><br /><br /> <span data-ttu-id="f1307-139">此資料類型的精確度為一分鐘。</span><span class="sxs-lookup"><span data-stu-id="f1307-139">This data type has an accuracy of one minute.</span></span> <span data-ttu-id="f1307-140">輸出時，秒數元件為零，而在輸入時，將會由伺服器捨去。</span><span class="sxs-lookup"><span data-stu-id="f1307-140">The seconds component will be zero on output and will be rounded by the server on input.</span></span>|  
|<span data-ttu-id="f1307-141">date</span><span class="sxs-lookup"><span data-stu-id="f1307-141">date</span></span>|<span data-ttu-id="f1307-142">DBTYPE_DBDATE</span><span class="sxs-lookup"><span data-stu-id="f1307-142">DBTYPE_DBDATE</span></span>|<span data-ttu-id="f1307-143">'yyyy-mm-dd'</span><span class="sxs-lookup"><span data-stu-id="f1307-143">'yyyy-mm-dd'</span></span>|  
|<span data-ttu-id="f1307-144">time</span><span class="sxs-lookup"><span data-stu-id="f1307-144">time</span></span>|<span data-ttu-id="f1307-145">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="f1307-145">DBTYPE_DBTIME2</span></span>|<span data-ttu-id="f1307-146">'hh:mm:ss[.9999999]'</span><span class="sxs-lookup"><span data-stu-id="f1307-146">'hh:mm:ss[.9999999]'</span></span><br /><br /> <span data-ttu-id="f1307-147">您最多可以使用七位數選擇性地指定小數秒。</span><span class="sxs-lookup"><span data-stu-id="f1307-147">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
|<span data-ttu-id="f1307-148">datetime2</span><span class="sxs-lookup"><span data-stu-id="f1307-148">datetime2</span></span>|<span data-ttu-id="f1307-149">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="f1307-149">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="f1307-150">'yyyy-mm-dd hh:mm:ss[.fffffff]'</span><span class="sxs-lookup"><span data-stu-id="f1307-150">'yyyy-mm-dd hh:mm:ss[.fffffff]'</span></span><br /><br /> <span data-ttu-id="f1307-151">您最多可以使用七位數選擇性地指定小數秒。</span><span class="sxs-lookup"><span data-stu-id="f1307-151">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
|<span data-ttu-id="f1307-152">datetimeoffset</span><span class="sxs-lookup"><span data-stu-id="f1307-152">datetimeoffset</span></span>|<span data-ttu-id="f1307-153">DBTYPE_DBTIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="f1307-153">DBTYPE_DBTIMESTAMPOFFSET</span></span>|<span data-ttu-id="f1307-154">'yyyy-mm-dd hh:mm:ss[.fffffff] +/-hh:mm'</span><span class="sxs-lookup"><span data-stu-id="f1307-154">'yyyy-mm-dd hh:mm:ss[.fffffff] +/-hh:mm'</span></span><br /><br /> <span data-ttu-id="f1307-155">您最多可以使用七位數選擇性地指定小數秒。</span><span class="sxs-lookup"><span data-stu-id="f1307-155">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
  
 <span data-ttu-id="f1307-156">日期/時間常值的逸出序列沒有變更。</span><span class="sxs-lookup"><span data-stu-id="f1307-156">There are no changes to the escape sequences for date/time literals.</span></span>  
  
 <span data-ttu-id="f1307-157">結果中的小數秒會使用點 (.) 而非冒號 (:)。</span><span class="sxs-lookup"><span data-stu-id="f1307-157">Fractional seconds in results use a dot (.) rather than a colon (:).</span></span>  
  
 <span data-ttu-id="f1307-158">傳回到應用程式的字串值一律為適用於給定資料行的相同長度。</span><span class="sxs-lookup"><span data-stu-id="f1307-158">String values returned to applications will always be the same length for a given column.</span></span> <span data-ttu-id="f1307-159">年、月、日、時、分和秒元件會以前置零填補以符合最大寬度。</span><span class="sxs-lookup"><span data-stu-id="f1307-159">Year, month, day, hour, minute, and second components will be padded with leading zeros to their maximum width.</span></span> <span data-ttu-id="f1307-160">在日期和時間之間將有一個空格，而在時間和時區位移之間也將有一個空格。</span><span class="sxs-lookup"><span data-stu-id="f1307-160">There will be exactly one space between date and time and exactly one space between the time and timezone offset.</span></span> <span data-ttu-id="f1307-161">時區位移一律置於一個符號之後。</span><span class="sxs-lookup"><span data-stu-id="f1307-161">A timezone offset will always be preceded by a sign.</span></span> <span data-ttu-id="f1307-162">當位移為零時，此符號為加號 (+)。</span><span class="sxs-lookup"><span data-stu-id="f1307-162">This sign will be a plus (+) when the offset is zero.</span></span> <span data-ttu-id="f1307-163">在符號和位移值之間將沒有任何空格。</span><span class="sxs-lookup"><span data-stu-id="f1307-163">There will be no white space between the sign and the offset value.</span></span> <span data-ttu-id="f1307-164">如果需要，小數秒將會以尾端零填補，最多填補到針對資料行定義的有效位數，但沒有其他東西。</span><span class="sxs-lookup"><span data-stu-id="f1307-164">Fractional seconds will be padded with trailing zeros, if necessary, up to the defined precision for the column, but no further.</span></span> <span data-ttu-id="f1307-165">對於 datetime 資料行，將有三個小數秒位數。</span><span class="sxs-lookup"><span data-stu-id="f1307-165">For datetime columns, there will be three fractional seconds digits.</span></span> <span data-ttu-id="f1307-166">對於 smalldatetime 資料行，則沒有小數秒的位數，而且秒數將永遠為零。</span><span class="sxs-lookup"><span data-stu-id="f1307-166">For smalldatetime columns, there will be no fractional seconds digits and the seconds will always be zero.</span></span>  
  
 <span data-ttu-id="f1307-167">應用程式從字串值進行的轉換將更具彈性，而且將允許元件值小於最大寬度。</span><span class="sxs-lookup"><span data-stu-id="f1307-167">Conversions from string values provided by the application will be more flexible and will allow component values less than maximum width.</span></span> <span data-ttu-id="f1307-168">年可以是 1-4 位數。</span><span class="sxs-lookup"><span data-stu-id="f1307-168">Years can be 1-4 digits.</span></span> <span data-ttu-id="f1307-169">月、日、時、分和秒可以是 1 或 2 位數。</span><span class="sxs-lookup"><span data-stu-id="f1307-169">Months, days, hours, minutes, and seconds can be 1 or 2 digits.</span></span> <span data-ttu-id="f1307-170">在日期/時間和時間/時區位移之間可以有一個任意空格。</span><span class="sxs-lookup"><span data-stu-id="f1307-170">There can be arbitrary white space between date/time and time/timezone offsets.</span></span> <span data-ttu-id="f1307-171">包含零小時和零分鐘的位移符號可以是加號或減號。</span><span class="sxs-lookup"><span data-stu-id="f1307-171">The sign of an offset with zero hours and zero minutes can be plus or minus.</span></span> <span data-ttu-id="f1307-172">小數秒允許使用尾端零，最多可達 9 位數。</span><span class="sxs-lookup"><span data-stu-id="f1307-172">Trailing zeros are allowed for fractional seconds up to a maximum of 9 digits.</span></span> <span data-ttu-id="f1307-173">時間元件可以利用一個小數點 (沒有小數秒位數) 結束。</span><span class="sxs-lookup"><span data-stu-id="f1307-173">A time component can terminate with a decimal point and no fractional seconds digits.</span></span>  
  
 <span data-ttu-id="f1307-174">空字串不是有效的日期/時間常值，而且它不代表 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="f1307-174">An empty string is not a valid date/time literal and it does not represent a NULL value.</span></span> <span data-ttu-id="f1307-175">嘗試將空字串轉換為日期/時間值時，將會導致 SQLState 22018 的錯誤，而且會出現「轉換規格的字元值無效」訊息。</span><span class="sxs-lookup"><span data-stu-id="f1307-175">An attempt to convert an empty string to a date/time value will result in errors with SQLState 22018 and the message "Invalid character value for cast specification".</span></span>  
  
## <a name="data-formats-data-structures"></a><span data-ttu-id="f1307-176">資料格式：資料結構</span><span class="sxs-lookup"><span data-stu-id="f1307-176">Data Formats: Data Structures</span></span>  
 <span data-ttu-id="f1307-177">在以下描述的 OLE DB 專屬結構中，OLE DB 符合與 ODBC 相同的限制。</span><span class="sxs-lookup"><span data-stu-id="f1307-177">In the OLE DB-specific structures described below, OLE DB conforms to the same constraints as ODBC.</span></span> <span data-ttu-id="f1307-178">這些是取自西曆：</span><span class="sxs-lookup"><span data-stu-id="f1307-178">These are taken from the Gregorian calendar:</span></span>  
  
-   <span data-ttu-id="f1307-179">月份的範圍由 1 至 12。</span><span class="sxs-lookup"><span data-stu-id="f1307-179">Month range is 1 through 12.</span></span>  
  
-   <span data-ttu-id="f1307-180">日期欄位範圍為 1 至該月份的天數，而且如果是潤年，則必須與年和月欄位一致。</span><span class="sxs-lookup"><span data-stu-id="f1307-180">Day field range is 1 through the number of days in the month, and must be consistent with year and month fields, taking account of leap years.</span></span>  
  
-   <span data-ttu-id="f1307-181">小時的範圍由 0 至 23。</span><span class="sxs-lookup"><span data-stu-id="f1307-181">Hour range is 0 through 23.</span></span>  
  
-   <span data-ttu-id="f1307-182">分鐘的範圍由 0 至 59。</span><span class="sxs-lookup"><span data-stu-id="f1307-182">Minute range is 0 through 59.</span></span>  
  
-   <span data-ttu-id="f1307-183">秒數的範圍從 0 至 59。</span><span class="sxs-lookup"><span data-stu-id="f1307-183">Seconds range from 0 through 59.</span></span> <span data-ttu-id="f1307-184">這可讓最多兩個潤秒與恆星時間保持同步。</span><span class="sxs-lookup"><span data-stu-id="f1307-184">This allows up to two leap seconds to maintain synchronization with sidereal time.</span></span>  
  
 <span data-ttu-id="f1307-185">下列現有 OLE DB 結構的實作已經經過修改，支援新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期和時間資料類型。</span><span class="sxs-lookup"><span data-stu-id="f1307-185">Implementations for the following existing OLE DB structs have been modified to support the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date and time data types.</span></span> <span data-ttu-id="f1307-186">不過，定義尚未變更。</span><span class="sxs-lookup"><span data-stu-id="f1307-186">The definitions, however, have not changed.</span></span>  
  
-   <span data-ttu-id="f1307-187">DBTYPE_DATE (這是一個自動化 DATE 類型。</span><span class="sxs-lookup"><span data-stu-id="f1307-187">DBTYPE_DATE (This is an automation DATE type.</span></span> <span data-ttu-id="f1307-188">這在內部表示為 `double`。</span><span class="sxs-lookup"><span data-stu-id="f1307-188">It is internally represented as a `double`..</span></span> <span data-ttu-id="f1307-189">整數部分為自 1899 年 12 月 30 日起的天數，而分數部分則為一天的分數部分。</span><span class="sxs-lookup"><span data-stu-id="f1307-189">The whole part is the number of days since December 30, 1899 and the fractional part is the fraction of a day.</span></span> <span data-ttu-id="f1307-190">此類型的精確度為 1 秒，因此，有效的小數位數為 0)。</span><span class="sxs-lookup"><span data-stu-id="f1307-190">This type has an accuracy of 1 second, so has an effective scale of 0.)</span></span>  
  
-   <span data-ttu-id="f1307-191">DBTYPE_DBDATE</span><span class="sxs-lookup"><span data-stu-id="f1307-191">DBTYPE_DBDATE</span></span>  
  
-   <span data-ttu-id="f1307-192">DBTYPE_DBTIME</span><span class="sxs-lookup"><span data-stu-id="f1307-192">DBTYPE_DBTIME</span></span>  
  
-   <span data-ttu-id="f1307-193">DBTYPE_DBTIMESTAMP (分數欄位會由 OLE DB 定義為十億分之一秒 (奈秒) 的數字，而範圍為 0-999,999,999)</span><span class="sxs-lookup"><span data-stu-id="f1307-193">DBTYPE_DBTIMESTAMP (the fraction field is defined by OLE DB as the number of billionths of a second (nanoseconds) and ranges from 0-999,999,999)</span></span>  
  
-   <span data-ttu-id="f1307-194">DBTYPE_FILETIME</span><span class="sxs-lookup"><span data-stu-id="f1307-194">DBTYPE_FILETIME</span></span>  
  
### <a name="dbtype_dbtime2"></a><span data-ttu-id="f1307-195">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="f1307-195">DBTYPE_DBTIME2</span></span>  
 <span data-ttu-id="f1307-196">此結構在 32 位元和 64 位元作業系統上會填補到 12 個位元組。</span><span class="sxs-lookup"><span data-stu-id="f1307-196">This struct is padded to 12 bytes on both 32-bit and 64-bit operating systems.</span></span>  
  
```  
typedef struct tagDBTIME2 {  
    USHORT hour;  
    USHORT minute;  
    USHORT second;  
    ULONG fraction;  
    } DBTIME2;  
```  
  
### <a name="dbtype_-dbtimestampoffset"></a><span data-ttu-id="f1307-197">DBTYPE_ DBTIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="f1307-197">DBTYPE_ DBTIMESTAMPOFFSET</span></span>  
  
```  
typedef struct tagDBTIMESTAMPOFFSET {  
    SHORT year;  
    USHORT month;  
    USHORT day;  
    USHORT hour;  
    USHORT minute;  
    USHORT second;  
    ULONG fraction;  
    SHORT timezone_hour;  
    SHORT timezone_minute;  
    } DBTIMESTAMPOFFSET;  
```  
  
 <span data-ttu-id="f1307-198">如果 `timezone_hour` 是負數，`timezone_minute` 必須為負數或零。</span><span class="sxs-lookup"><span data-stu-id="f1307-198">If `timezone_hour` is negative, `timezone_minute` must be negative or zero.</span></span> <span data-ttu-id="f1307-199">如果 `timezone_hour` 是正數，`timezone minute` 必須為正數或零。</span><span class="sxs-lookup"><span data-stu-id="f1307-199">If `timezone_hour` is positive, `timezone minute` must be positive or zero.</span></span> <span data-ttu-id="f1307-200">如果 `timezone_hour` 為零，`timezone minute` 可以容納介於 -59 和 +59 之間的值。</span><span class="sxs-lookup"><span data-stu-id="f1307-200">If `timezone_hour` is zero, `timezone minute` can hold a value between -59 and +59.</span></span>  
  
### <a name="ssvariant"></a><span data-ttu-id="f1307-201">SSVARIANT</span><span class="sxs-lookup"><span data-stu-id="f1307-201">SSVARIANT</span></span>  
 <span data-ttu-id="f1307-202">此結構現在包含新的結構 DBTYPE_DBTIME2 和 DBTYPE_DBTIMESTAMPOFFSET，而且可以針對適當的類型加入小數秒小數位數。</span><span class="sxs-lookup"><span data-stu-id="f1307-202">This struct now includes the new structures, DBTYPE_DBTIME2 and DBTYPE_DBTIMESTAMPOFFSET, and adds fractional seconds scale for appropriate types.</span></span>  
  
```  
struct SSVARIANT {  
   SSVARTYPE vt;  
   DWORD dwReserved1;  
   DWORD dwReserved2;  
   union {  
// ...  
      DBTIMESTAMP tsDateTimeVal;  
      DBDATE dDateVal;  
      struct _Time2Val {  
         DBTIME2 tTime2Val;  
         BYTE bScale;  
      } Time2Val;  
      struct _DateTimeVal {  
         DBTIMESTAMP tsDateTimeVal;  
         BYTE bScale;  
      } DateTimeVal;  
      struct _DateTimeOffsetVal {   
         DBTIMESTAMPOFFSET tsoDateTimeOffsetVal;  
         BYTE bScale;  
      } DateTimeOffsetVal;  
// ...  
   };  
};  
```  
  
 <span data-ttu-id="f1307-203">此外，與 SSVARIANT 類型編碼 (可判斷列舉的類型) 相關聯的列舉將會擴充如下：</span><span class="sxs-lookup"><span data-stu-id="f1307-203">In addition, the enum associated with SSVARIANT type encoding, which determines the type of the enum, will be extended as follows:</span></span>  
  
```  
enum SQLVARENUM {  
// ...  
   // Datetime  
   VT_SS_DATETIME      = DBTYPE_DBTIMESTAMP,  
   VT_SS_SMALLDATETIME = 206,  
  
   VT_SS_DATE = DBTYPE_DBDATE,  
   VT_SS_TIME2 = DBTYPE_DBTIME2,  
   VT_SS_DATETIME2 = 212  
   VT_SS_DATETIMEOFFSET = DBTYPE_DBTIMESTAMPOFFSET  
};  
```  
  
 <span data-ttu-id="f1307-204">如果基礎結構描述更新為使用 `sql_variant` 而非 `datetime`，將需要更新移轉至使用 `datetime2` 並依賴 `datetime` 限制有效位數之 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f1307-204">Applications migrating to [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client that use `sql_variant` and rely on the limited precision of `datetime` will have to be updated if the underlying schema is updated to use `datetime2` rather than `datetime`.</span></span>  
  
 <span data-ttu-id="f1307-205">SSVARIANT 的存取巨集也已經透過加入下列項目來擴充：</span><span class="sxs-lookup"><span data-stu-id="f1307-205">The access macros for SSVARIANT have also been extended with the addition of the following:</span></span>  
  
```  
#define V_SS_DATETIME2(X)       V_SS_UNION(X, DateTimeVal)  
#define V_SS_TIME2(X)           V_SS_UNION(X, Time2Val)  
#define V_SS_DATE(X)            V_SS_UNION(X, dDateVal)  
#define V_SS_DATETIMEOFFSET(X)  V_SS_UNION(X, DateTimeOffsetVal)  
```  
  
## <a name="data-type-mapping-in-itabledefinitioncreatetable"></a><span data-ttu-id="f1307-206">ITableDefinition::CreateTable 中的資料類型對應</span><span class="sxs-lookup"><span data-stu-id="f1307-206">Data Type Mapping in ITableDefinition::CreateTable</span></span>  
 <span data-ttu-id="f1307-207">下列類型對應會搭配 ITableDefinition::CreateTable 所使用的 DBCOLUMNDESC 結構使用：</span><span class="sxs-lookup"><span data-stu-id="f1307-207">The following type mapping is used with DBCOLUMNDESC structures used by ITableDefinition::CreateTable:</span></span>  
  
|<span data-ttu-id="f1307-208">OLE DB 資料類型 (*wType*)</span><span class="sxs-lookup"><span data-stu-id="f1307-208">OLE DB data type (*wType*)</span></span>|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="f1307-209">資料類型</span><span class="sxs-lookup"><span data-stu-id="f1307-209">data type</span></span>|<span data-ttu-id="f1307-210">注意</span><span class="sxs-lookup"><span data-stu-id="f1307-210">Notes</span></span>|  
|----------------------------------|-----------------------------------------|-----------|  
|<span data-ttu-id="f1307-211">DBTYPE_DBDATE</span><span class="sxs-lookup"><span data-stu-id="f1307-211">DBTYPE_DBDATE</span></span>|<span data-ttu-id="f1307-212">date</span><span class="sxs-lookup"><span data-stu-id="f1307-212">date</span></span>||  
|<span data-ttu-id="f1307-213">DBTYPE_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="f1307-213">DBTYPE_DBTIMESTAMP</span></span>|<span data-ttu-id="f1307-214">`datetime2`(p)</span><span class="sxs-lookup"><span data-stu-id="f1307-214">`datetime2`(p)</span></span>|<span data-ttu-id="f1307-215">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會檢查 DBCOLUMDESC *bScale*成員，以判斷小數秒數有效位數。</span><span class="sxs-lookup"><span data-stu-id="f1307-215">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider inspects the DBCOLUMDESC *bScale* member to determine the fractional seconds precision.</span></span>|  
|<span data-ttu-id="f1307-216">DBTYPE_DBTIME2</span><span class="sxs-lookup"><span data-stu-id="f1307-216">DBTYPE_DBTIME2</span></span>|<span data-ttu-id="f1307-217">`time`(p)</span><span class="sxs-lookup"><span data-stu-id="f1307-217">`time`(p)</span></span>|<span data-ttu-id="f1307-218">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會檢查 DBCOLUMDESC *bScale*成員，以判斷小數秒數有效位數。</span><span class="sxs-lookup"><span data-stu-id="f1307-218">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider inspects the DBCOLUMDESC *bScale* member to determine the fractional seconds precision.</span></span>|  
|<span data-ttu-id="f1307-219">DBTYPE_DBTIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="f1307-219">DBTYPE_DBTIMESTAMPOFFSET</span></span>|<span data-ttu-id="f1307-220">`datetimeoffset`(p)</span><span class="sxs-lookup"><span data-stu-id="f1307-220">`datetimeoffset`(p)</span></span>|<span data-ttu-id="f1307-221">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB 提供者會檢查 DBCOLUMDESC *bScale*成員，以判斷小數秒數有效位數。</span><span class="sxs-lookup"><span data-stu-id="f1307-221">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB provider inspects the DBCOLUMDESC *bScale* member to determine the fractional seconds precision.</span></span>|  
  
 <span data-ttu-id="f1307-222">當應用程式在*wType*中指定 DBTYPE_DBTIMESTAMP 時，它可以藉 `datetime2` 由在*pwszTypeName*中提供類型名稱來覆寫的對應。</span><span class="sxs-lookup"><span data-stu-id="f1307-222">When an application specifies DBTYPE_DBTIMESTAMP in *wType*, it can override the mapping to `datetime2` by supplying a type name in *pwszTypeName*.</span></span> <span data-ttu-id="f1307-223">如果 `datetime` 指定了， *bScale*必須是3。</span><span class="sxs-lookup"><span data-stu-id="f1307-223">If `datetime` is specified, *bScale* must be 3.</span></span> <span data-ttu-id="f1307-224">如果 `smalldatetime` 指定了， *bScale*必須是0。</span><span class="sxs-lookup"><span data-stu-id="f1307-224">If `smalldatetime` is specified, *bScale* must be 0.</span></span> <span data-ttu-id="f1307-225">如果*bScale*與*wType*和*pwszTypeName*不一致，則會傳回 DB_E_BADSCALE。</span><span class="sxs-lookup"><span data-stu-id="f1307-225">If *bScale* is not consistent with *wType* and *pwszTypeName*,DB_E_BADSCALE is returned.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1307-226">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1307-226">See Also</span></span>  
 [<span data-ttu-id="f1307-227">日期和時間改善 &#40;OLE DB&#41;</span><span class="sxs-lookup"><span data-stu-id="f1307-227">Date and Time Improvements &#40;OLE DB&#41;</span></span>](date-and-time-improvements-ole-db.md)  
  
  
