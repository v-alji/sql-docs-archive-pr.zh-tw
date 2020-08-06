---
title: ODBC 日期和時間改善的資料類型支援 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- date/time [ODBC], data type support
- ODBC, date/time improvements
ms.assetid: 8e0d9ba2-3ec1-4680-86e3-b2590ba8e2e9
author: rothja
ms.author: jroth
ms.openlocfilehash: df0877a17ad8e2310db5c6e3ab4acd0c14d05611
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595942"
---
# <a name="data-type-support-for-odbc-date-and-time-improvements"></a><span data-ttu-id="4f7ff-102">資料類型對 ODBC 日期和時間支援的改善</span><span class="sxs-lookup"><span data-stu-id="4f7ff-102">Data Type Support for ODBC Date and Time Improvements</span></span>
  <span data-ttu-id="4f7ff-103">本主題提供有關支援 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期和時間資料類型之 ODBC 類型的資訊。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-103">This topic provides information about ODBC types that support [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date and time data types.</span></span>  
  
## <a name="data-type-mapping-in-parameters-and-resultsets"></a><span data-ttu-id="4f7ff-104">參數和資料列集中的資料類型對應</span><span class="sxs-lookup"><span data-stu-id="4f7ff-104">Data Type Mapping in Parameters and Resultsets</span></span>  
 <span data-ttu-id="4f7ff-105">除了 ODBC 資料類型 (SQL_TYPE_TIMESTAMP 和 SQL_TIMESTAMP) 之外，我們在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC 中加入了兩個新的資料類型，以便公開新的伺服器類型：</span><span class="sxs-lookup"><span data-stu-id="4f7ff-105">In addition to the ODBC data types (SQL_TYPE_TIMESTAMP and SQL_TIMESTAMP), two new data types were added in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC to expose the new server types:</span></span>  
  
-   <span data-ttu-id="4f7ff-106">SQL_SS_TIME2</span><span class="sxs-lookup"><span data-stu-id="4f7ff-106">SQL_SS_TIME2</span></span>  
  
-   <span data-ttu-id="4f7ff-107">SQL_SS_TIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="4f7ff-107">SQL_SS_TIMESTAMPOFFSET</span></span>  
  
 <span data-ttu-id="4f7ff-108">下表顯示完整伺服器類型的對應。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-108">The following table shows the complete server-type mapping.</span></span> <span data-ttu-id="4f7ff-109">請注意，資料表的某些資料格包含兩個項目：在這些情況下，第一個是 ODBC 3.0 值，而第二個是 ODBC 2.0 值。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-109">Notice that some cells of the table contain two entries; in these cases, the first is the ODBC 3.0 value and the second is the ODBC 2.0 value.</span></span>  
  
|<span data-ttu-id="4f7ff-110">SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="4f7ff-110">SQL Server data type</span></span>|<span data-ttu-id="4f7ff-111">SQL 資料類型</span><span class="sxs-lookup"><span data-stu-id="4f7ff-111">SQL data type</span></span>|<span data-ttu-id="4f7ff-112">值</span><span class="sxs-lookup"><span data-stu-id="4f7ff-112">Value</span></span>|  
|--------------------------|-------------------|-----------|  
|<span data-ttu-id="4f7ff-113">Datetime</span><span class="sxs-lookup"><span data-stu-id="4f7ff-113">Datetime</span></span>|<span data-ttu-id="4f7ff-114">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-114">SQL_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="4f7ff-115">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-115">SQL_TIMESTAMP</span></span>|<span data-ttu-id="4f7ff-116">93 (sql.h)</span><span class="sxs-lookup"><span data-stu-id="4f7ff-116">93 (sql.h)</span></span><br /><br /> <span data-ttu-id="4f7ff-117">11 (sqlext.h)</span><span class="sxs-lookup"><span data-stu-id="4f7ff-117">11 (sqlext.h)</span></span>|  
|<span data-ttu-id="4f7ff-118">Smalldatetime</span><span class="sxs-lookup"><span data-stu-id="4f7ff-118">Smalldatetime</span></span>|<span data-ttu-id="4f7ff-119">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-119">SQL_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="4f7ff-120">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-120">SQL_TIMESTAMP</span></span>|<span data-ttu-id="4f7ff-121">93 (sql.h)</span><span class="sxs-lookup"><span data-stu-id="4f7ff-121">93 (sql.h)</span></span><br /><br /> <span data-ttu-id="4f7ff-122">11 (sqlext.h)</span><span class="sxs-lookup"><span data-stu-id="4f7ff-122">11 (sqlext.h)</span></span>|  
|<span data-ttu-id="4f7ff-123">Date</span><span class="sxs-lookup"><span data-stu-id="4f7ff-123">Date</span></span>|<span data-ttu-id="4f7ff-124">SQL_TYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="4f7ff-124">SQL_TYPE_DATE</span></span><br /><br /> <span data-ttu-id="4f7ff-125">SQL_DATE</span><span class="sxs-lookup"><span data-stu-id="4f7ff-125">SQL_DATE</span></span>|<span data-ttu-id="4f7ff-126">91 (sql .h) </span><span class="sxs-lookup"><span data-stu-id="4f7ff-126">91 (sql.h)</span></span><br /><br /> <span data-ttu-id="4f7ff-127">9 (sqlext.h. h) </span><span class="sxs-lookup"><span data-stu-id="4f7ff-127">9 (sqlext.h)</span></span>|  
|<span data-ttu-id="4f7ff-128">Time</span><span class="sxs-lookup"><span data-stu-id="4f7ff-128">Time</span></span>|<span data-ttu-id="4f7ff-129">SQL_SS_TIME2</span><span class="sxs-lookup"><span data-stu-id="4f7ff-129">SQL_SS_TIME2</span></span>|<span data-ttu-id="4f7ff-130">-154 (SQLNCLI) </span><span class="sxs-lookup"><span data-stu-id="4f7ff-130">-154 (SQLNCLI.h)</span></span>|  
|<span data-ttu-id="4f7ff-131">DatetimeOFFSET</span><span class="sxs-lookup"><span data-stu-id="4f7ff-131">DatetimeOFFSET</span></span>|<span data-ttu-id="4f7ff-132">SQL_SS_TIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="4f7ff-132">SQL_SS_TIMESTAMPOFFSET</span></span>|<span data-ttu-id="4f7ff-133">-155 (SQLNCLI.h)</span><span class="sxs-lookup"><span data-stu-id="4f7ff-133">-155 (SQLNCLI.h)</span></span>|  
|<span data-ttu-id="4f7ff-134">Datetime2</span><span class="sxs-lookup"><span data-stu-id="4f7ff-134">Datetime2</span></span>|<span data-ttu-id="4f7ff-135">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-135">SQL_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="4f7ff-136">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-136">SQL_TIMESTAMP</span></span>|<span data-ttu-id="4f7ff-137">93 (sql.h)</span><span class="sxs-lookup"><span data-stu-id="4f7ff-137">93 (sql.h)</span></span><br /><br /> <span data-ttu-id="4f7ff-138">11 (sqlext.h)</span><span class="sxs-lookup"><span data-stu-id="4f7ff-138">11 (sqlext.h)</span></span>|  
  
 <span data-ttu-id="4f7ff-139">下表列出對應的結構和 ODBC C 類型。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-139">The following table lists the corresponding structures and ODBC C types.</span></span> <span data-ttu-id="4f7ff-140">ODBC 不允許使用定義 C 類型的驅動程式，因此，SQL_C_BINARY 會當做二進位結構，用於 time 和 datetimeoffset。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-140">Because ODBC does not permit driver defined C types, SQL_C_BINARY is used for time and datetimeoffset as binary structures.</span></span>  
  
|<span data-ttu-id="4f7ff-141">SQL 資料類型</span><span class="sxs-lookup"><span data-stu-id="4f7ff-141">SQL data type</span></span>|<span data-ttu-id="4f7ff-142">記憶體配置</span><span class="sxs-lookup"><span data-stu-id="4f7ff-142">Memory layout</span></span>|<span data-ttu-id="4f7ff-143">預設 C 資料類型</span><span class="sxs-lookup"><span data-stu-id="4f7ff-143">Default C data type</span></span>|<span data-ttu-id="4f7ff-144">值 (sqlext.h)</span><span class="sxs-lookup"><span data-stu-id="4f7ff-144">Value (sqlext.h)</span></span>|  
|-------------------|-------------------|-------------------------|------------------------|  
|<span data-ttu-id="4f7ff-145">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-145">SQL_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="4f7ff-146">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-146">SQL_TIMESTAMP</span></span>|<span data-ttu-id="4f7ff-147">SQL_TIMESTAMP_STRUCT</span><span class="sxs-lookup"><span data-stu-id="4f7ff-147">SQL_TIMESTAMP_STRUCT</span></span><br /><br /> <span data-ttu-id="4f7ff-148">TIMESTAMP_STRUCT</span><span class="sxs-lookup"><span data-stu-id="4f7ff-148">TIMESTAMP_STRUCT</span></span>|<span data-ttu-id="4f7ff-149">SQL_C_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-149">SQL_C_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="4f7ff-150">SQL_C_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-150">SQL_C_TIMESTAMP</span></span>|<span data-ttu-id="4f7ff-151">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-151">SQL_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="4f7ff-152">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-152">SQL_TIMESTAMP</span></span>|  
|<span data-ttu-id="4f7ff-153">SQL_TYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="4f7ff-153">SQL_TYPE_DATE</span></span><br /><br /> <span data-ttu-id="4f7ff-154">SQL_DATE</span><span class="sxs-lookup"><span data-stu-id="4f7ff-154">SQL_DATE</span></span>|<span data-ttu-id="4f7ff-155">SQL_DATE_STRUCT</span><span class="sxs-lookup"><span data-stu-id="4f7ff-155">SQL_DATE_STRUCT</span></span><br /><br /> <span data-ttu-id="4f7ff-156">DATE_STRUCT</span><span class="sxs-lookup"><span data-stu-id="4f7ff-156">DATE_STRUCT</span></span>|<span data-ttu-id="4f7ff-157">SQL_C_TYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="4f7ff-157">SQL_C_TYPE_DATE</span></span><br /><br /> <span data-ttu-id="4f7ff-158">SQL_C_DATE</span><span class="sxs-lookup"><span data-stu-id="4f7ff-158">SQL_C_DATE</span></span>|<span data-ttu-id="4f7ff-159">SQL_TYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="4f7ff-159">SQL_TYPE_DATE</span></span><br /><br /> <span data-ttu-id="4f7ff-160">SQL_DATE</span><span class="sxs-lookup"><span data-stu-id="4f7ff-160">SQL_DATE</span></span>|  
|<span data-ttu-id="4f7ff-161">SQL_SS_TIME2</span><span class="sxs-lookup"><span data-stu-id="4f7ff-161">SQL_SS_TIME2</span></span>|<span data-ttu-id="4f7ff-162">SQL_SS_TIME2_STRUCT</span><span class="sxs-lookup"><span data-stu-id="4f7ff-162">SQL_SS_TIME2_STRUCT</span></span>|<span data-ttu-id="4f7ff-163">SQL_C_SS_TIME2</span><span class="sxs-lookup"><span data-stu-id="4f7ff-163">SQL_C_SS_TIME2</span></span><br /><br /> <span data-ttu-id="4f7ff-164">SQL_C_BINARY (ODBC 3.5 和舊版)</span><span class="sxs-lookup"><span data-stu-id="4f7ff-164">SQL_C_BINARY (ODBC 3.5 and earlier)</span></span>|<span data-ttu-id="4f7ff-165">0x4000 (sqlncli.h)</span><span class="sxs-lookup"><span data-stu-id="4f7ff-165">0x4000 (sqlncli.h)</span></span><br /><br /> <span data-ttu-id="4f7ff-166">SQL_BINARY (-2)</span><span class="sxs-lookup"><span data-stu-id="4f7ff-166">SQL_BINARY (-2)</span></span>|  
|<span data-ttu-id="4f7ff-167">SQL_SS_TIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="4f7ff-167">SQL_SS_TIMESTAMPOFFSET</span></span>|<span data-ttu-id="4f7ff-168">SQL_SS_TIMESTAMPOFFSET_STRUCT</span><span class="sxs-lookup"><span data-stu-id="4f7ff-168">SQL_SS_TIMESTAMPOFFSET_STRUCT</span></span>|<span data-ttu-id="4f7ff-169">SQL_C_SS_TIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="4f7ff-169">SQL_C_SS_TIMESTAMPOFFSET</span></span><br /><br /> <span data-ttu-id="4f7ff-170">SQL_C_BINARY (ODBC 3.5 和舊版)</span><span class="sxs-lookup"><span data-stu-id="4f7ff-170">SQL_C_BINARY (ODBC 3.5 and earlier)</span></span>|<span data-ttu-id="4f7ff-171">0x4001 (sqlncli.h)</span><span class="sxs-lookup"><span data-stu-id="4f7ff-171">0x4001 (sqlncli.h)</span></span><br /><br /> <span data-ttu-id="4f7ff-172">SQL_BINARY (-2)</span><span class="sxs-lookup"><span data-stu-id="4f7ff-172">SQL_BINARY (-2)</span></span>|  
  
 <span data-ttu-id="4f7ff-173">指定 SQL_C_BINARY 繫結時，將會執行對齊檢查，並回報對齊不正確的錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-173">When SQL_C_BINARY binding is specified, alignment checking will be performed and an error reported for incorrect alignment.</span></span> <span data-ttu-id="4f7ff-174">此錯誤的 SQLSTATE 將為 IM016，其中包含「結構對齊錯誤」訊息。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-174">The SQLSTATE for this error will be IM016, with the message "Incorrect structure alignment".</span></span>  
  
## <a name="data-formats-strings-and-literals"></a><span data-ttu-id="4f7ff-175">資料格式：字串和常值</span><span class="sxs-lookup"><span data-stu-id="4f7ff-175">Data Formats: Strings and Literals</span></span>  
 <span data-ttu-id="4f7ff-176">下表顯示在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型、ODBC 資料類型與 ODBC 字串常值之間的對應。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-176">The following table shows the mappings between [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types, ODBC data types, and the ODBC string literals.</span></span>  
  
|<span data-ttu-id="4f7ff-177">SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="4f7ff-177">SQL Server data type</span></span>|<span data-ttu-id="4f7ff-178">ODBC 資料類型</span><span class="sxs-lookup"><span data-stu-id="4f7ff-178">ODBC data type</span></span>|<span data-ttu-id="4f7ff-179">用於用戶端轉換的字串格式</span><span class="sxs-lookup"><span data-stu-id="4f7ff-179">String format for client conversions</span></span>|  
|--------------------------|--------------------|------------------------------------------|  
|<span data-ttu-id="4f7ff-180">Datetime</span><span class="sxs-lookup"><span data-stu-id="4f7ff-180">Datetime</span></span>|<span data-ttu-id="4f7ff-181">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-181">SQL_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="4f7ff-182">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-182">SQL_TIMESTAMP</span></span>|<span data-ttu-id="4f7ff-183">'yyyy-mm-dd hh:mm:ss[.999]'</span><span class="sxs-lookup"><span data-stu-id="4f7ff-183">'yyyy-mm-dd hh:mm:ss[.999]'</span></span><br /><br /> <span data-ttu-id="4f7ff-184">針對 Datetime，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 最多支援三個小數秒位數。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-184">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] supports up to three fractional second digits for Datetime.</span></span>|  
|<span data-ttu-id="4f7ff-185">Smalldatetime</span><span class="sxs-lookup"><span data-stu-id="4f7ff-185">Smalldatetime</span></span>|<span data-ttu-id="4f7ff-186">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-186">SQL_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="4f7ff-187">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-187">SQL_TIMESTAMP</span></span>|<span data-ttu-id="4f7ff-188">'yyyy-mm-dd hh:hh:ss'</span><span class="sxs-lookup"><span data-stu-id="4f7ff-188">'yyyy-mm-dd hh:hh:ss'</span></span><br /><br /> <span data-ttu-id="4f7ff-189">此資料類型的精確度為一分鐘。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-189">This data type has an accuracy of one minute.</span></span> <span data-ttu-id="4f7ff-190">輸出時，秒數元件為零，而在輸入時，將會由伺服器捨去。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-190">The seconds component will be zero on output and will be rounded by the server on input.</span></span>|  
|<span data-ttu-id="4f7ff-191">Date</span><span class="sxs-lookup"><span data-stu-id="4f7ff-191">Date</span></span>|<span data-ttu-id="4f7ff-192">SQL_TYPE_DATE</span><span class="sxs-lookup"><span data-stu-id="4f7ff-192">SQL_TYPE_DATE</span></span><br /><br /> <span data-ttu-id="4f7ff-193">SQL_DATE</span><span class="sxs-lookup"><span data-stu-id="4f7ff-193">SQL_DATE</span></span>|<span data-ttu-id="4f7ff-194">'yyyy-mm-dd'</span><span class="sxs-lookup"><span data-stu-id="4f7ff-194">'yyyy-mm-dd'</span></span>|  
|<span data-ttu-id="4f7ff-195">Time</span><span class="sxs-lookup"><span data-stu-id="4f7ff-195">Time</span></span>|<span data-ttu-id="4f7ff-196">SQL_SS_TIME2</span><span class="sxs-lookup"><span data-stu-id="4f7ff-196">SQL_SS_TIME2</span></span>|<span data-ttu-id="4f7ff-197">'hh:mm:ss[.9999999]'</span><span class="sxs-lookup"><span data-stu-id="4f7ff-197">'hh:mm:ss[.9999999]'</span></span><br /><br /> <span data-ttu-id="4f7ff-198">您最多可以使用七位數選擇性地指定小數秒。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-198">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
|<span data-ttu-id="4f7ff-199">Datetime2</span><span class="sxs-lookup"><span data-stu-id="4f7ff-199">Datetime2</span></span>|<span data-ttu-id="4f7ff-200">SQL_TYPE_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-200">SQL_TYPE_TIMESTAMP</span></span><br /><br /> <span data-ttu-id="4f7ff-201">SQL_TIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="4f7ff-201">SQL_TIMESTAMP</span></span>|<span data-ttu-id="4f7ff-202">' yyyy-mm-dd hh： mm： ss [. 9999999] '</span><span class="sxs-lookup"><span data-stu-id="4f7ff-202">'yyyy-mm-dd hh:mm:ss[.9999999]'</span></span><br /><br /> <span data-ttu-id="4f7ff-203">您最多可以使用七位數選擇性地指定小數秒。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-203">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
|<span data-ttu-id="4f7ff-204">DatetimeOFFSET</span><span class="sxs-lookup"><span data-stu-id="4f7ff-204">DatetimeOFFSET</span></span>|<span data-ttu-id="4f7ff-205">SQL_SS_TIMESTAMPOFFSET</span><span class="sxs-lookup"><span data-stu-id="4f7ff-205">SQL_SS_TIMESTAMPOFFSET</span></span>|<span data-ttu-id="4f7ff-206">'yyyy-mm-dd hh:mm:ss[.9999999] +/- hh:mm'</span><span class="sxs-lookup"><span data-stu-id="4f7ff-206">'yyyy-mm-dd hh:mm:ss[.9999999] +/- hh:mm'</span></span><br /><br /> <span data-ttu-id="4f7ff-207">您最多可以使用七位數選擇性地指定小數秒。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-207">Fractional seconds can optionally be specified using up to seven digits.</span></span>|  
  
 <span data-ttu-id="4f7ff-208">日期/時間常值的 ODBC 逸出序列沒有變更。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-208">There are no changes to the ODBC escape sequences for date/time literals.</span></span>  
  
 <span data-ttu-id="4f7ff-209">結果中的小數秒一律使用點 (.) 而非冒號 (:)。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-209">Fractional seconds in results always use a dot (.), rather than a colon (:).</span></span>  
  
 <span data-ttu-id="4f7ff-210">傳回到應用程式的字串值一律為適用於給定資料行的相同長度。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-210">String values returned to applications are always the same length for a given column.</span></span> <span data-ttu-id="4f7ff-211">年、月、日、十、分和秒元件會以前置零填補以符合最大寬度，而且在 datetime 值的日期和時間之間會有一個空格。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-211">Year, month, day, hour, minute, and second components are padded with leading zeros to their maximum width, and there is one space between date and time in datetime values.</span></span> <span data-ttu-id="4f7ff-212">在 datetimeoffset 值的時間和時區位移之間也有一個空格。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-212">There is also one space between the time and timezone offset in a datetimeoffset value.</span></span> <span data-ttu-id="4f7ff-213">時區位移一律置於一個符號之後；當位移為零時，此符號為加號 (+)。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-213">A timezone offset is always preceded by a sign; when the offset is zero, this sign is a plus (+).</span></span> <span data-ttu-id="4f7ff-214">如果需要，小數秒會以尾端零填補，最多填補到針對資料行定義的有效位數。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-214">Fractional seconds are padded with trailing zeros if necessary, up to the defined precision for the column.</span></span> <span data-ttu-id="4f7ff-215">對於 datetime 資料行，有三個小數秒位數。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-215">For datetime columns, there are three fractional seconds digits.</span></span> <span data-ttu-id="4f7ff-216">對於 smalldatetime 資料行，則沒有小數秒的位數，而且秒數將永遠為零。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-216">For smalldatetime columns, there are no fractional seconds' digits, and the seconds will always be zero.</span></span>  
  
 <span data-ttu-id="4f7ff-217">空字串不是有效的日期/時間常值，而且它不代表 NULL 值。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-217">An empty string is not a valid date/time literal and it does not represent a NULL value.</span></span> <span data-ttu-id="4f7ff-218">嘗試將空字串轉換為日期/時間值時，將會導致 SQLState 22018 錯誤，而且會出現「轉換規格的字元值無效」訊息。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-218">An attempt to convert an empty string to a date/time value will result in SQLState 22018 error and the message "Invalid character value for cast specification".</span></span>  
  
 <span data-ttu-id="4f7ff-219">從字串參數進行轉換時，字串格式應該相同，但是小時和分鐘為零的時區符號可以是加號或減號，而且小數秒可以使用最多 9 位數的尾端零。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-219">Conversions from string parameters will expect strings in the same format, with the exceptions that the sign of a timezone with zero hours and zero minutes can be either plus or minus, and trailing zeros are allowed for fractional seconds up to a maximum of 9 digits.</span></span> <span data-ttu-id="4f7ff-220">時間元件可以利用一個小數點 (沒有小數秒位數) 結束。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-220">A time component can terminate with a decimal point and no fractional seconds digits.</span></span>  
  
 <span data-ttu-id="4f7ff-221">驅動程式目前在標點符號字元周圍允許額外的空白，而時間和時區位移之間的空格則是選擇性的。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-221">Currently, the driver allows additional white space around punctuation characters and the space between time and timezone offset is optional.</span></span> <span data-ttu-id="4f7ff-222">不過，這在後續的版本中可能會有變更；應用程式不應該依賴目前的行為。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-222">However, this might change in a future release; applications should not rely on the current behavior.</span></span>  
  
## <a name="data-formats-data-structures"></a><span data-ttu-id="4f7ff-223">資料格式：資料結構</span><span class="sxs-lookup"><span data-stu-id="4f7ff-223">Data Formats: Data Structures</span></span>  
 <span data-ttu-id="4f7ff-224">在以下描述的結構中，ODBC 會指定採用自西曆的下列條件約束：</span><span class="sxs-lookup"><span data-stu-id="4f7ff-224">In the structures described below, ODBC specifies the following constraints, which are taken from the Gregorian calendar:</span></span>  
  
-   <span data-ttu-id="4f7ff-225">月份的範圍由 1 至 12。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-225">Month range is 1 through 12.</span></span>  
  
-   <span data-ttu-id="4f7ff-226">日期欄位範圍為 1 至該月份的天數，而且如果是潤年，則必須與年和月欄位一致。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-226">Day field range is 1 through the number of days in the month, and must be consistent with year and month fields, taking account of leap years.</span></span>  
  
-   <span data-ttu-id="4f7ff-227">小時的範圍由 0 至 23。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-227">Hour range is 0 through 23.</span></span>  
  
-   <span data-ttu-id="4f7ff-228">分鐘的範圍由 0 至 59。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-228">Minute range is 0 through 59.</span></span>  
  
-   <span data-ttu-id="4f7ff-229">秒數的範圍由 0 至 61.9(n)。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-229">Seconds range is 0 through 61.9(n).</span></span> <span data-ttu-id="4f7ff-230">這可讓最多兩個潤秒與恆星時間保持同步。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-230">This allows up to two leap seconds to maintain synchronization with sidereal time.</span></span>  
  
     <span data-ttu-id="4f7ff-231">請注意，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 不允許使用潤秒，因此，大於 59 的秒數值將會導致伺服器錯誤。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-231">Note that [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] does not allow leap seconds, so second values greater than 59 will cause a server error.</span></span>  
  
 <span data-ttu-id="4f7ff-232">下列現有 ODBC 結構的實作已經經過修改，支援新的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 日期和時間資料類型。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-232">Implementations for the following existing ODBC structs have been modified to support the new [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] date and time data types.</span></span> <span data-ttu-id="4f7ff-233">不過，定義尚未變更。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-233">The definitions, however, have not changed.</span></span>  
  
-   <span data-ttu-id="4f7ff-234">DATE_STRUCT</span><span class="sxs-lookup"><span data-stu-id="4f7ff-234">DATE_STRUCT</span></span>  
  
-   <span data-ttu-id="4f7ff-235">TIME_STRUCT</span><span class="sxs-lookup"><span data-stu-id="4f7ff-235">TIME_STRUCT</span></span>  
  
-   <span data-ttu-id="4f7ff-236">TIMESTAMP_STRUCT</span><span class="sxs-lookup"><span data-stu-id="4f7ff-236">TIMESTAMP_STRUCT</span></span>  
  
 <span data-ttu-id="4f7ff-237">另外還有兩個新的結構：</span><span class="sxs-lookup"><span data-stu-id="4f7ff-237">There are also two new structs:</span></span>  
  
-   <span data-ttu-id="4f7ff-238">SQL_SS_TIME2_STRUCT</span><span class="sxs-lookup"><span data-stu-id="4f7ff-238">SQL_SS_TIME2_STRUCT</span></span>  
  
-   <span data-ttu-id="4f7ff-239">SQL_SS_TIMESTAMPOFFSET_STRUCT</span><span class="sxs-lookup"><span data-stu-id="4f7ff-239">SQL_SS_TIMESTAMPOFFSET_STRUCT</span></span>  
  
### <a name="sql_ss_time2_struct"></a><span data-ttu-id="4f7ff-240">SQL_SS_TIME2_STRUCT</span><span class="sxs-lookup"><span data-stu-id="4f7ff-240">SQL_SS_TIME2_STRUCT</span></span>  
 <span data-ttu-id="4f7ff-241">此結構在 32 位元和 64 位元作業系統上會填補到 12 個位元組。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-241">This struct is padded to 12 bytes on both 32-bit and 64-bit operating systems.</span></span>  
  
```  
typedef struct tagSS_TIME2_STRUCT {  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
   SQLUINTEGER fraction;  
} SQL_SS_TIME2_STRUCT;  
```  
  
### <a name="sql_ss_timestampoffset_struct"></a><span data-ttu-id="4f7ff-242">SQL_SS_TIMESTAMPOFFSET_STRUCT</span><span class="sxs-lookup"><span data-stu-id="4f7ff-242">SQL_SS_TIMESTAMPOFFSET_STRUCT</span></span>  
  
```  
typedef struct tagSS_TIMESTAMPOFFSET_STRUCT {  
   SQLSMALLINT year;  
   SQLUSMALLINT month;  
   SQLUSMALLINT day;  
   SQLUSMALLINT hour;  
   SQLUSMALLINT minute;  
   SQLUSMALLINT second;  
   SQLUINTEGER fraction;  
   SQLSMALLINT timezone_hour;  
   SQLSMALLINT timezone_minute;  
} SQL_SS_TIMESTAMPOFFSET_STRUCT;  
```  
  
 <span data-ttu-id="4f7ff-243">如果 `timezone_hour` 是負數，`timezone_minute` 必須為負數或零。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-243">If the `timezone_hour` is negative, the `timezone_minute` must be negative or zero.</span></span> <span data-ttu-id="4f7ff-244">如果 `timezone_hour` 是正數，`timezone_minute` 必須為正數或零。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-244">If the `timezone_hour` is positive, the `timezone_minute` must be positive or zero.</span></span> <span data-ttu-id="4f7ff-245">如果 `timezone_hour` 為零，`timezone_minute` 可能擁有 -59 到 +59 範圍內的任何值。</span><span class="sxs-lookup"><span data-stu-id="4f7ff-245">If the `timezone_hour` is zero, the s`timezone_minute` may have any value in the range -59 through +59.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f7ff-246">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4f7ff-246">See Also</span></span>  
 [<span data-ttu-id="4f7ff-247">ODBC&#41;&#40;的日期和時間改善</span><span class="sxs-lookup"><span data-stu-id="4f7ff-247">Date and Time Improvements &#40;ODBC&#41;</span></span>](date-and-time-improvements-odbc.md)  
  
  
