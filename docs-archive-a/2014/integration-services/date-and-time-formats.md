---
title: 日期和時間格式 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- time data types [Integration Services]
- fast parse [Integration Services]
- date data types
- date and time formats for fast parse
ms.assetid: bed6e2c1-791a-4fa1-b29f-cbfdd1fa8d39
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 5e6c461c0cfed6a776875831a46c94c70d895ba3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592774"
---
# <a name="date-and-time-formats"></a><span data-ttu-id="19b56-102">日期和時間格式</span><span class="sxs-lookup"><span data-stu-id="19b56-102">Date and Time Formats</span></span>
  <span data-ttu-id="19b56-103">快速剖析提供一組快速、簡單的常式用以剖析資料。</span><span class="sxs-lookup"><span data-stu-id="19b56-103">Fast parse provides a fast, simple set of routines for parsing data.</span></span> <span data-ttu-id="19b56-104">快速剖析可支援下列格式的日期和時間資料類型。</span><span class="sxs-lookup"><span data-stu-id="19b56-104">Fast parse supports the following formats for date and time data types.</span></span>  
  
## <a name="date-data-types"></a><span data-ttu-id="19b56-105">日期資料類型</span><span class="sxs-lookup"><span data-stu-id="19b56-105">Date Data Types</span></span>  
 <span data-ttu-id="19b56-106">快速剖析支援下列字串格式的日期資料：</span><span class="sxs-lookup"><span data-stu-id="19b56-106">Fast parse supports the following string formats for date data:</span></span>  
  
-   <span data-ttu-id="19b56-107">包含開頭空白字元的日期格式。</span><span class="sxs-lookup"><span data-stu-id="19b56-107">Date formats that include leading white spaces.</span></span> <span data-ttu-id="19b56-108">例如，值 " 2004- 02-03"為有效。</span><span class="sxs-lookup"><span data-stu-id="19b56-108">For example, the value " 2004- 02-03" is valid.</span></span>  
  
-   <span data-ttu-id="19b56-109">ISO 8601 格式，如下表中所列：</span><span class="sxs-lookup"><span data-stu-id="19b56-109">ISO 8601 formats, as listed in the following table:</span></span>  
  
    |<span data-ttu-id="19b56-110">格式</span><span class="sxs-lookup"><span data-stu-id="19b56-110">Format</span></span>|<span data-ttu-id="19b56-111">描述</span><span class="sxs-lookup"><span data-stu-id="19b56-111">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="19b56-112">YYYYMMDD</span><span class="sxs-lookup"><span data-stu-id="19b56-112">YYYYMMDD</span></span><br /><br /> <span data-ttu-id="19b56-113">YYYY-MM-DD</span><span class="sxs-lookup"><span data-stu-id="19b56-113">YYYY-MM-DD</span></span>|<span data-ttu-id="19b56-114">四位數年份、兩位數月份和兩位數天數的基本格式與擴充格式。</span><span class="sxs-lookup"><span data-stu-id="19b56-114">Basic and extended formats for a four-digit year, a two-digit month, and a two-digit day.</span></span> <span data-ttu-id="19b56-115">在擴充格式中，日期各部份以連字號 (-) 分隔。</span><span class="sxs-lookup"><span data-stu-id="19b56-115">In the extended format, the date parts are separated by a hyphen (-).</span></span>|  
    |<span data-ttu-id="19b56-116">YYYY-MM</span><span class="sxs-lookup"><span data-stu-id="19b56-116">YYYY-MM</span></span>|<span data-ttu-id="19b56-117">降低有效位數的四位數年份和兩位數月份之基本格式與擴充格式。</span><span class="sxs-lookup"><span data-stu-id="19b56-117">Basic and extended reduced precision formats for a four-digit year and a two-digit month.</span></span> <span data-ttu-id="19b56-118">在擴充格式中，日期各部份以連字號 (-) 分隔。</span><span class="sxs-lookup"><span data-stu-id="19b56-118">In the extended format, the date parts are separated by a hyphen (-).</span></span>|  
    |<span data-ttu-id="19b56-119">YYYY</span><span class="sxs-lookup"><span data-stu-id="19b56-119">YYYY</span></span>|<span data-ttu-id="19b56-120">降低有效位數的格式為四位數年份。</span><span class="sxs-lookup"><span data-stu-id="19b56-120">Reduced precision format is a four-digit year.</span></span>|  
  
 <span data-ttu-id="19b56-121">快速剖析不支援下列格式的日期資料：</span><span class="sxs-lookup"><span data-stu-id="19b56-121">Fast parse does not support the following formats for date data:</span></span>  
  
-   <span data-ttu-id="19b56-122">字母月份值。</span><span class="sxs-lookup"><span data-stu-id="19b56-122">Alphabetical month values.</span></span> <span data-ttu-id="19b56-123">例如，日期格式 Oct-31-2003 無效。</span><span class="sxs-lookup"><span data-stu-id="19b56-123">For example, the date format Oct-31-2003 is not valid.</span></span>  
  
-   <span data-ttu-id="19b56-124">模稜兩可的格式，例如 DD-MM-YYYY 和 MM-DD-YYYY。</span><span class="sxs-lookup"><span data-stu-id="19b56-124">Ambiguous formats such as DD-MM-YYYY and MM-DD-YYYY.</span></span> <span data-ttu-id="19b56-125">例如，日期 03-04-1995 和日期 04-03-1995 無效。</span><span class="sxs-lookup"><span data-stu-id="19b56-125">For example, the dates 03-04-1995 and 04-03-1995 are not valid.</span></span>  
  
-   <span data-ttu-id="19b56-126">四位數日曆年度和一年中三位數天數的基本截斷格式與擴充截斷格式 (YYYYDDD 和 YYYY-DDD)。</span><span class="sxs-lookup"><span data-stu-id="19b56-126">Basic and extended truncated formats for a four-digit calendar year and a three-digit day within a year, YYYYDDD and YYYY-DDD.</span></span>  
  
-   <span data-ttu-id="19b56-127">四位數年份、一年中兩位數週數和一週中一位數天數的基本格式與擴充格式 (YYYYWwwD 和 YYYY-Www-D)。</span><span class="sxs-lookup"><span data-stu-id="19b56-127">Basic and extended formats for a four-digit year, a two-digit number for the week of the year, and a one-digit number for the day of the week, YYYYWwwD and YYYY-Www-D</span></span>  
  
-   <span data-ttu-id="19b56-128">年份和週日期的基本截斷格式與擴充截斷格式為四位數年份和兩位數週數 (YYYWww 和 YYYY-Www)。</span><span class="sxs-lookup"><span data-stu-id="19b56-128">Basic and extended truncated formats for a year and week date are a four-digit year and a two-digit number for the week, YYYWww and YYYY-Www</span></span>  
  
 <span data-ttu-id="19b56-129">快速剖析會以 DT_DBDATE 輸出資料。</span><span class="sxs-lookup"><span data-stu-id="19b56-129">Fast parse outputs the data as DT_DBDATE.</span></span> <span data-ttu-id="19b56-130">將填補以截斷格式表示的日期值。</span><span class="sxs-lookup"><span data-stu-id="19b56-130">Date values in truncated formats are padded.</span></span> <span data-ttu-id="19b56-131">例如，YYYY 會變為 YYYY0101。</span><span class="sxs-lookup"><span data-stu-id="19b56-131">For example, YYYY becomes YYYY0101.</span></span>  
  
 <span data-ttu-id="19b56-132">如需詳細資訊，請參閱 [Integration Services 資料類型](data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="19b56-132">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="time-data-type"></a><span data-ttu-id="19b56-133">時間資料類型</span><span class="sxs-lookup"><span data-stu-id="19b56-133">Time Data Type</span></span>  
 <span data-ttu-id="19b56-134">快速剖析支援下列字串格式的時間資料：</span><span class="sxs-lookup"><span data-stu-id="19b56-134">Fast parse supports the following string formats for time data:</span></span>  
  
-   <span data-ttu-id="19b56-135">包含開頭空白字元的時間格式。</span><span class="sxs-lookup"><span data-stu-id="19b56-135">Time formats that include leading white spaces.</span></span> <span data-ttu-id="19b56-136">例如，值「 10:24」為有效。</span><span class="sxs-lookup"><span data-stu-id="19b56-136">For example, the value " 10:24" is valid.</span></span>  
  
-   <span data-ttu-id="19b56-137">24 小時格式。</span><span class="sxs-lookup"><span data-stu-id="19b56-137">24-hour format.</span></span> <span data-ttu-id="19b56-138">快速剖析不支援 AM 和 PM 標記法。</span><span class="sxs-lookup"><span data-stu-id="19b56-138">Fast parse does not support the AM and PM notation.</span></span>  
  
-   <span data-ttu-id="19b56-139">ISO 8601 時間格式，如下表中所列：</span><span class="sxs-lookup"><span data-stu-id="19b56-139">ISO 8601 time formats, as listed in the following table:</span></span>  
  
    |<span data-ttu-id="19b56-140">格式</span><span class="sxs-lookup"><span data-stu-id="19b56-140">Format</span></span>|<span data-ttu-id="19b56-141">描述</span><span class="sxs-lookup"><span data-stu-id="19b56-141">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="19b56-142">HHMISS</span><span class="sxs-lookup"><span data-stu-id="19b56-142">HHMISS</span></span><br /><br /> <span data-ttu-id="19b56-143">HH:MI:SS</span><span class="sxs-lookup"><span data-stu-id="19b56-143">HH:MI:SS</span></span>|<span data-ttu-id="19b56-144">四位數小時、兩位數分鐘和兩位數秒鐘的基本格式與擴充格式。</span><span class="sxs-lookup"><span data-stu-id="19b56-144">Basic and extended formats for a two-digit hour, a two-digit minute, and a two-digit second.</span></span> <span data-ttu-id="19b56-145">在擴充格式中，時間各部份以冒號 (:) 分隔。</span><span class="sxs-lookup"><span data-stu-id="19b56-145">In the extended format, the time parts are separated by a colon (:).</span></span>|  
    |<span data-ttu-id="19b56-146">HHMI</span><span class="sxs-lookup"><span data-stu-id="19b56-146">HHMI</span></span><br /><br /> <span data-ttu-id="19b56-147">HH:MI</span><span class="sxs-lookup"><span data-stu-id="19b56-147">HH:MI</span></span>|<span data-ttu-id="19b56-148">兩位數小時和兩位數分鐘之基本截斷格式與擴充截斷格式。</span><span class="sxs-lookup"><span data-stu-id="19b56-148">Basic and extended truncated format for a two-digit hour and a two-digit minute.</span></span> <span data-ttu-id="19b56-149">在擴充格式中，時間各部份以冒號 (:) 分隔。</span><span class="sxs-lookup"><span data-stu-id="19b56-149">In the extended format, the time parts are separated by a colon (:).</span></span>|  
    |<span data-ttu-id="19b56-150">HH</span><span class="sxs-lookup"><span data-stu-id="19b56-150">HH</span></span>|<span data-ttu-id="19b56-151">兩位數小時的截斷格式。</span><span class="sxs-lookup"><span data-stu-id="19b56-151">Truncated format for a two-digit hour.</span></span>|  
    |<span data-ttu-id="19b56-152">00:00:00</span><span class="sxs-lookup"><span data-stu-id="19b56-152">00:00:00</span></span><br /><br /> <span data-ttu-id="19b56-153">000000</span><span class="sxs-lookup"><span data-stu-id="19b56-153">000000</span></span><br /><br /> <span data-ttu-id="19b56-154">0000</span><span class="sxs-lookup"><span data-stu-id="19b56-154">0000</span></span><br /><br /> <span data-ttu-id="19b56-155">00</span><span class="sxs-lookup"><span data-stu-id="19b56-155">00</span></span><br /><br /> <span data-ttu-id="19b56-156">240000</span><span class="sxs-lookup"><span data-stu-id="19b56-156">240000</span></span><br /><br /> <span data-ttu-id="19b56-157">24:00:00</span><span class="sxs-lookup"><span data-stu-id="19b56-157">24:00:00</span></span><br /><br /> <span data-ttu-id="19b56-158">2400</span><span class="sxs-lookup"><span data-stu-id="19b56-158">2400</span></span><br /><br /> <span data-ttu-id="19b56-159">24</span><span class="sxs-lookup"><span data-stu-id="19b56-159">24</span></span>|<span data-ttu-id="19b56-160">午夜格式。</span><span class="sxs-lookup"><span data-stu-id="19b56-160">The format for midnight.</span></span>|  
  
-   <span data-ttu-id="19b56-161">指定時區的時間格式，如下表中所列：</span><span class="sxs-lookup"><span data-stu-id="19b56-161">Time formats that specify a time zone, as listed in the following table:.</span></span>  
  
    |<span data-ttu-id="19b56-162">格式</span><span class="sxs-lookup"><span data-stu-id="19b56-162">Format</span></span>|<span data-ttu-id="19b56-163">描述</span><span class="sxs-lookup"><span data-stu-id="19b56-163">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="19b56-164">+HH:MI</span><span class="sxs-lookup"><span data-stu-id="19b56-164">+HH:MI</span></span><br /><br /> <span data-ttu-id="19b56-165">+HHMI</span><span class="sxs-lookup"><span data-stu-id="19b56-165">+HHMI</span></span>|<span data-ttu-id="19b56-166">基本格式及擴充格式，指出要加入至「國際標準時間」(UTC) 以取得本地時間的小時和分鐘數。</span><span class="sxs-lookup"><span data-stu-id="19b56-166">Basic and extended formats that indicate the number of hours and minutes that are added to Coordinated Universal Time (UTC) to obtain the local time.</span></span>|  
    |<span data-ttu-id="19b56-167">-HH:MI</span><span class="sxs-lookup"><span data-stu-id="19b56-167">-HH:MI</span></span><br /><br /> <span data-ttu-id="19b56-168">-HHMI</span><span class="sxs-lookup"><span data-stu-id="19b56-168">-HHMI</span></span>|<span data-ttu-id="19b56-169">基本格式及擴充格式，指出要從 UTC 減去以取得本地時間的小時和分鐘數。</span><span class="sxs-lookup"><span data-stu-id="19b56-169">Basic and extended formats that indicate the number of hours and minutes that are subtracted from UTC to obtain the local time.</span></span>|  
    |<span data-ttu-id="19b56-170">+HH</span><span class="sxs-lookup"><span data-stu-id="19b56-170">+HH</span></span>|<span data-ttu-id="19b56-171">截斷格式，指出要加入至 UTC 以取得本地時間的小時數。</span><span class="sxs-lookup"><span data-stu-id="19b56-171">Truncated format that indicates the number of hours that are added to UTC to obtain the local time.</span></span>|  
    |<span data-ttu-id="19b56-172">-HH</span><span class="sxs-lookup"><span data-stu-id="19b56-172">-HH</span></span>|<span data-ttu-id="19b56-173">截斷格式，指出要從 UTC 減去以取得本地時間的小時數。</span><span class="sxs-lookup"><span data-stu-id="19b56-173">Truncated format that indicates the number of hours that are subtracted from UTC to obtain the local time.</span></span>|  
    |<span data-ttu-id="19b56-174">Z</span><span class="sxs-lookup"><span data-stu-id="19b56-174">Z</span></span>|<span data-ttu-id="19b56-175">0 的值，指出時間是以 UTC 表示。</span><span class="sxs-lookup"><span data-stu-id="19b56-175">A value of 0 that indicates the time is represented in UTC.</span></span>|  
  
     <span data-ttu-id="19b56-176">所有時間和日期/時間資料的格式都可以包含時區元素。</span><span class="sxs-lookup"><span data-stu-id="19b56-176">The formats for all time and date/time data can include a time zone element.</span></span> <span data-ttu-id="19b56-177">不過，除非資料是 DT_DBTIMESTAMPOFFSET 類型，否則系統會忽略時區值。</span><span class="sxs-lookup"><span data-stu-id="19b56-177">However, the system ignores the time zone value except when the data is of type DT_DBTIMESTAMPOFFSET.</span></span> <span data-ttu-id="19b56-178">如需詳細資訊，請參閱 [Integration Services 資料類型](data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="19b56-178">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
     <span data-ttu-id="19b56-179">在包含時區元素的格式中，在時間元素和時區元素之間沒有空格，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="19b56-179">In formats that include a time zone element, there is no space between the time element and the time zone element, as shown in the following example:</span></span>  
  
     <span data-ttu-id="19b56-180">HH:MI:SS[+HH:MI]</span><span class="sxs-lookup"><span data-stu-id="19b56-180">HH:MI:SS[+HH:MI]</span></span>  
  
     <span data-ttu-id="19b56-181">前述範例中的方括號表示時區值是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="19b56-181">The brackets in the previous example indicate that the time zone value is optional.</span></span>  
  
-   <span data-ttu-id="19b56-182">包含小數的時間格式，如下表中所列：</span><span class="sxs-lookup"><span data-stu-id="19b56-182">Time formats that include a decimal fraction, as listed in the following table:</span></span>  
  
    |<span data-ttu-id="19b56-183">格式</span><span class="sxs-lookup"><span data-stu-id="19b56-183">Format</span></span>|<span data-ttu-id="19b56-184">描述</span><span class="sxs-lookup"><span data-stu-id="19b56-184">Description</span></span>|  
    |------------|-----------------|  
    |<span data-ttu-id="19b56-185">HH[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="19b56-185">HH[.nnnnnnn]</span></span>|<span data-ttu-id="19b56-186">n 是介於 0 和 9999999 之間且代表小數時數的值。</span><span class="sxs-lookup"><span data-stu-id="19b56-186">n is a value between 0 and 9999999 that represents a fraction of hours.</span></span> <span data-ttu-id="19b56-187">方括號表示此值是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="19b56-187">The brackets indicate that this value is optional.</span></span><br /><br /> <span data-ttu-id="19b56-188">例如，值 12.750 表示 12:45。</span><span class="sxs-lookup"><span data-stu-id="19b56-188">For example, the value 12.750 indicates 12:45.</span></span>|  
    |<span data-ttu-id="19b56-189">HHMI[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="19b56-189">HHMI[.nnnnnnn]</span></span><br /><br /> <span data-ttu-id="19b56-190">HH:MI[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="19b56-190">HH:MI[.nnnnnnn]</span></span>|<span data-ttu-id="19b56-191">n 是介於 0 和 9999999 之間且代表小數分鐘數的值。</span><span class="sxs-lookup"><span data-stu-id="19b56-191">n is a value between 0 and 9999999 that represents a fraction of minutes.</span></span> <span data-ttu-id="19b56-192">方括號表示此值是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="19b56-192">The brackets indicate that this value is optional.</span></span><br /><br /> <span data-ttu-id="19b56-193">例如，值 1220.500 表示 12:20:30。</span><span class="sxs-lookup"><span data-stu-id="19b56-193">For example, the value 1220.500 indicates 12:20:30.</span></span>|  
    |<span data-ttu-id="19b56-194">HHMISS[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="19b56-194">HHMISS[.nnnnnnn]</span></span><br /><br /> <span data-ttu-id="19b56-195">HH:MI:SS[.nnnnnnn]</span><span class="sxs-lookup"><span data-stu-id="19b56-195">HH:MI:SS[.nnnnnnn]</span></span>|<span data-ttu-id="19b56-196">n 是介於 0 和 9999999 之間且代表小數秒數的值。</span><span class="sxs-lookup"><span data-stu-id="19b56-196">n is a value between 0 and 9999999 that represents a fraction of seconds.</span></span> <span data-ttu-id="19b56-197">方括號表示此值是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="19b56-197">The brackets indicate that this value is optional.</span></span><br /><br /> <span data-ttu-id="19b56-198">例如，值 122040.250 表示 12:20:40.15。</span><span class="sxs-lookup"><span data-stu-id="19b56-198">For example, the value 122040.250 indicates 12:20:40.15.</span></span>|  
  
    > [!NOTE]  
    >  <span data-ttu-id="19b56-199">前述表格中時間格式的小數分隔符號可以是小數點或逗號。</span><span class="sxs-lookup"><span data-stu-id="19b56-199">The fraction separator for the time formats in the previous table can be a decimal or a comma.</span></span>  
  
-   <span data-ttu-id="19b56-200">包含閏秒 (Leap Second) 的時間值，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="19b56-200">Time values that include a leap second, as shown in the following examples:</span></span>  
  
     <span data-ttu-id="19b56-201">23:59:60[.0000000]</span><span class="sxs-lookup"><span data-stu-id="19b56-201">23:59:60[.0000000]</span></span>  
  
     <span data-ttu-id="19b56-202">235960[.0000000]</span><span class="sxs-lookup"><span data-stu-id="19b56-202">235960[.0000000]</span></span>  
  
 <span data-ttu-id="19b56-203">快速剖析會以 DT_DBTIME 和 DT_DBTIME2 輸出字串。</span><span class="sxs-lookup"><span data-stu-id="19b56-203">Fast parse outputs the strings as DT_DBTIME and DT_DBTIME2.</span></span> <span data-ttu-id="19b56-204">將填補以截斷格式表示的時間值。</span><span class="sxs-lookup"><span data-stu-id="19b56-204">Time values in truncated formats are padded.</span></span> <span data-ttu-id="19b56-205">例如，HH:MI 會變為 HH:MM:00.000。</span><span class="sxs-lookup"><span data-stu-id="19b56-205">For example, HH:MI becomes HH:MM:00.000.</span></span>  
  
 <span data-ttu-id="19b56-206">如需詳細資訊，請參閱 [Integration Services 資料類型](data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="19b56-206">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="datetime-data-type"></a><span data-ttu-id="19b56-207">日期/時間資料類型</span><span class="sxs-lookup"><span data-stu-id="19b56-207">Date/Time Data Type</span></span>  
 <span data-ttu-id="19b56-208">快速剖析支援下列字串格式的日期/時間資料：</span><span class="sxs-lookup"><span data-stu-id="19b56-208">Fast parse supports the following string formats for date/time data:</span></span>  
  
-   <span data-ttu-id="19b56-209">包含開頭空白字元的格式。</span><span class="sxs-lookup"><span data-stu-id="19b56-209">Formats that include leading white spaces.</span></span> <span data-ttu-id="19b56-210">例如，值 "  2003-01-10T203910" 有效。</span><span class="sxs-lookup"><span data-stu-id="19b56-210">For example, the value "  2003-01-10T203910" is valid.</span></span>  
  
-   <span data-ttu-id="19b56-211">有效日期格式和有效時間格式的組合會以大寫的 T 及有效的時區格式分隔，例如 YYYYMMDDT[HHMISS][+HH:MI]。</span><span class="sxs-lookup"><span data-stu-id="19b56-211">Combinations of valid date formats and valid time formats separated by an uppercase T, and valid time zone formats, such as YYYYMMDDT[HHMISS][+HH:MI].</span></span> <span data-ttu-id="19b56-212">時間和時區值不是必要值。</span><span class="sxs-lookup"><span data-stu-id="19b56-212">The time and time zone values are not required.</span></span> <span data-ttu-id="19b56-213">例如，"2003-10-14" 是有效值。</span><span class="sxs-lookup"><span data-stu-id="19b56-213">For example, "2003-10-14" is valid.</span></span>  
  
 <span data-ttu-id="19b56-214">快速剖析不支援時間間隔。</span><span class="sxs-lookup"><span data-stu-id="19b56-214">Fast parse does not support time intervals.</span></span> <span data-ttu-id="19b56-215">例如，格式為 YYYYMMDDThhmmss/YYYYMMDDThhmmss 之開始日期和時間以及結束日期和時間所識別的時間間隔將無法剖析。</span><span class="sxs-lookup"><span data-stu-id="19b56-215">For example, a time interval identified by a start and end date and time in the format YYYYMMDDThhmmss/YYYYMMDDThhmmss cannot be parsed.</span></span>  
  
 <span data-ttu-id="19b56-216">快速剖析會以 DT_DATE、DT_DBTIMESTAMP、DT_DBTIMESTAMP2 和 DT_DBTIMESTAMPOFFSET 輸出字串。</span><span class="sxs-lookup"><span data-stu-id="19b56-216">Fast parse outputs the strings as DT_DATE, DT_DBTIMESTAMP, DT_DBTIMESTAMP2, and DT_DBTIMESTAMPOFFSET.</span></span> <span data-ttu-id="19b56-217">將填補以截斷格式表示的日期/時間值。</span><span class="sxs-lookup"><span data-stu-id="19b56-217">Date/time values in truncated formats are padded.</span></span> <span data-ttu-id="19b56-218">下表列出針對遺失的日期和時間部分而加入的值。</span><span class="sxs-lookup"><span data-stu-id="19b56-218">The following table lists the values that are added for missing date and time parts.</span></span>  
  
|<span data-ttu-id="19b56-219">日期/時間部分</span><span class="sxs-lookup"><span data-stu-id="19b56-219">Date/Time part</span></span>|<span data-ttu-id="19b56-220">填補</span><span class="sxs-lookup"><span data-stu-id="19b56-220">Padding</span></span>|  
|---------------------|-------------|  
|<span data-ttu-id="19b56-221">秒</span><span class="sxs-lookup"><span data-stu-id="19b56-221">Seconds</span></span>|<span data-ttu-id="19b56-222">加入 00。</span><span class="sxs-lookup"><span data-stu-id="19b56-222">Add 00.</span></span>|  
|<span data-ttu-id="19b56-223">分鐘</span><span class="sxs-lookup"><span data-stu-id="19b56-223">Minutes</span></span>|<span data-ttu-id="19b56-224">加入 00:00。</span><span class="sxs-lookup"><span data-stu-id="19b56-224">Add 00:00.</span></span>|  
|<span data-ttu-id="19b56-225">小時</span><span class="sxs-lookup"><span data-stu-id="19b56-225">Hour</span></span>|<span data-ttu-id="19b56-226">加入 00:00:00。</span><span class="sxs-lookup"><span data-stu-id="19b56-226">Add 00:00:00.</span></span>|  
|<span data-ttu-id="19b56-227">天</span><span class="sxs-lookup"><span data-stu-id="19b56-227">Day</span></span>|<span data-ttu-id="19b56-228">加入 01 做為此月的某個日期。</span><span class="sxs-lookup"><span data-stu-id="19b56-228">Add 01 for the day of the month.</span></span>|  
|<span data-ttu-id="19b56-229">Month</span><span class="sxs-lookup"><span data-stu-id="19b56-229">Month</span></span>|<span data-ttu-id="19b56-230">加入 01 做為此年份的某個月份。</span><span class="sxs-lookup"><span data-stu-id="19b56-230">Add 01 for the month of the year.</span></span>|  
  
 <span data-ttu-id="19b56-231">如需詳細資訊，請參閱 [Integration Services 資料類型](data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="19b56-231">For more information, see [Integration Services Data Types](data-flow/integration-services-data-types.md).</span></span>  
  
  
