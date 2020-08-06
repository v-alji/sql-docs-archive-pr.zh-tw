---
title: bcp_gettypename |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
api_name:
- bcp_gettypename
api_location:
- sqlncli11.dll
topic_type:
- apiref
helpviewer_keywords:
- bcp_gettypename function
ms.assetid: 65f036d1-f60e-4b8a-97b3-76fccf0dfed4
author: rothja
ms.author: jroth
ms.openlocfilehash: b2d92498b9d863fa2cb700ec4d88868c0984c4d4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594061"
---
# <a name="bcp_gettypename"></a><span data-ttu-id="e4a97-102">bcp_gettypename</span><span class="sxs-lookup"><span data-stu-id="e4a97-102">bcp_gettypename</span></span>
  <span data-ttu-id="e4a97-103">傳回指定之 BCP 類型 Token 的 SQL 類型名稱。</span><span class="sxs-lookup"><span data-stu-id="e4a97-103">Returns the SQL type name for a specified BCP type token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4a97-104">語法</span><span class="sxs-lookup"><span data-stu-id="e4a97-104">Syntax</span></span>  
  
```  
  
RETCODE bcp_gettypename (  
INT   
token  
,  
DBBOOL   
fIsMaxType  
);  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="e4a97-105">引數</span><span class="sxs-lookup"><span data-stu-id="e4a97-105">Arguments</span></span>  
 <span data-ttu-id="e4a97-106">*token*</span><span class="sxs-lookup"><span data-stu-id="e4a97-106">*token*</span></span>  
 <span data-ttu-id="e4a97-107">指出 BCP 類型 Token 的值。</span><span class="sxs-lookup"><span data-stu-id="e4a97-107">A value indicating a BCP type token.</span></span>  
  
 <span data-ttu-id="e4a97-108">*欄位*</span><span class="sxs-lookup"><span data-stu-id="e4a97-108">*field*</span></span>  
 <span data-ttu-id="e4a97-109">指出要求的 Token 是否為最大值類型。</span><span class="sxs-lookup"><span data-stu-id="e4a97-109">Indicates if token requested is a max type.</span></span>  
  
## <a name="returns"></a><span data-ttu-id="e4a97-110">傳回</span><span class="sxs-lookup"><span data-stu-id="e4a97-110">Returns</span></span>  
 <span data-ttu-id="e4a97-111">包含對應到 BCP 類型之 SQL 類型名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="e4a97-111">A string containing the SQL type name corresponding to the BCP type.</span></span> <span data-ttu-id="e4a97-112">如果指定無效的 BCP 類型，則傳回空字串。</span><span class="sxs-lookup"><span data-stu-id="e4a97-112">If an invalid BCP type is specified, an empty string is returned..</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4a97-113">備註</span><span class="sxs-lookup"><span data-stu-id="e4a97-113">Remarks</span></span>  
 <span data-ttu-id="e4a97-114">BCP 類型 Token 是在 sqlncli.h 標頭檔和 sqlncli11.lib 程式庫中定義的。</span><span class="sxs-lookup"><span data-stu-id="e4a97-114">The BCP type tokens are defined in the sqlncli.h header file and the sqlncli11.lib library.</span></span>  
  
 <span data-ttu-id="e4a97-115">以下的資料表會指定可能的 BCP 類型 (不論它們是否為最大類型) 以及預期的輸出。</span><span class="sxs-lookup"><span data-stu-id="e4a97-115">The table below specifies the possible BCP types, whether or not they are max types, and the expected output.</span></span>  
  
|<span data-ttu-id="e4a97-116">BCP 類型名稱</span><span class="sxs-lookup"><span data-stu-id="e4a97-116">BCP type name</span></span>|<span data-ttu-id="e4a97-117">MaxType</span><span class="sxs-lookup"><span data-stu-id="e4a97-117">MaxType</span></span>|<span data-ttu-id="e4a97-118">輸出</span><span class="sxs-lookup"><span data-stu-id="e4a97-118">Output</span></span>|  
|-------------------|-------------|------------|  
|`SQLDECIMAL`|<span data-ttu-id="e4a97-119">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-119">Either</span></span>|<span data-ttu-id="e4a97-120">**decimal**</span><span class="sxs-lookup"><span data-stu-id="e4a97-120">**decimal**</span></span>|  
|`SQLNUMERIC`|<span data-ttu-id="e4a97-121">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-121">Either</span></span>|<span data-ttu-id="e4a97-122">**numeric**</span><span class="sxs-lookup"><span data-stu-id="e4a97-122">**numeric**</span></span>|  
|`SQLINT1`|<span data-ttu-id="e4a97-123">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-123">Either</span></span>|<span data-ttu-id="e4a97-124">**tinyint**</span><span class="sxs-lookup"><span data-stu-id="e4a97-124">**tinyint**</span></span>|  
|`SQLINT2`|<span data-ttu-id="e4a97-125">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-125">Either</span></span>|<span data-ttu-id="e4a97-126">**smallint**</span><span class="sxs-lookup"><span data-stu-id="e4a97-126">**smallint**</span></span>|  
|`SQLINT4`|<span data-ttu-id="e4a97-127">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-127">Either</span></span>|<span data-ttu-id="e4a97-128">**int**</span><span class="sxs-lookup"><span data-stu-id="e4a97-128">**int**</span></span>|  
|`SQLMONEY`|<span data-ttu-id="e4a97-129">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-129">Either</span></span>|<span data-ttu-id="e4a97-130">**money**</span><span class="sxs-lookup"><span data-stu-id="e4a97-130">**money**</span></span>|  
|`SQLFLT8`|<span data-ttu-id="e4a97-131">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-131">Either</span></span>|<span data-ttu-id="e4a97-132">**float**</span><span class="sxs-lookup"><span data-stu-id="e4a97-132">**float**</span></span>|  
|`SQLDATETIME`|<span data-ttu-id="e4a97-133">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-133">Either</span></span>|<span data-ttu-id="e4a97-134">**datetime**</span><span class="sxs-lookup"><span data-stu-id="e4a97-134">**datetime**</span></span>|  
|`SQLBITN`|<span data-ttu-id="e4a97-135">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-135">Either</span></span>|<span data-ttu-id="e4a97-136">**bit-null**</span><span class="sxs-lookup"><span data-stu-id="e4a97-136">**bit-null**</span></span>|  
|`SQLBIT`|<span data-ttu-id="e4a97-137">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-137">Either</span></span>|<span data-ttu-id="e4a97-138">**bit**</span><span class="sxs-lookup"><span data-stu-id="e4a97-138">**bit**</span></span>|  
|`SQLBIGCHAR`|<span data-ttu-id="e4a97-139">否</span><span class="sxs-lookup"><span data-stu-id="e4a97-139">No</span></span>|<span data-ttu-id="e4a97-140">**char**</span><span class="sxs-lookup"><span data-stu-id="e4a97-140">**char**</span></span>|  
|`SQLCHARACTER`|<span data-ttu-id="e4a97-141">否</span><span class="sxs-lookup"><span data-stu-id="e4a97-141">No</span></span>|<span data-ttu-id="e4a97-142">**char**</span><span class="sxs-lookup"><span data-stu-id="e4a97-142">**char**</span></span>|  
|`SQLBIGVARCHAR`|<span data-ttu-id="e4a97-143">否</span><span class="sxs-lookup"><span data-stu-id="e4a97-143">No</span></span>|<span data-ttu-id="e4a97-144">**varchar**</span><span class="sxs-lookup"><span data-stu-id="e4a97-144">**varchar**</span></span>|  
|`SQLVARCHAR`|<span data-ttu-id="e4a97-145">否</span><span class="sxs-lookup"><span data-stu-id="e4a97-145">No</span></span>|<span data-ttu-id="e4a97-146">**varchar**</span><span class="sxs-lookup"><span data-stu-id="e4a97-146">**varchar**</span></span>|  
|`SQLTEXT`|<span data-ttu-id="e4a97-147">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-147">Either</span></span>|<span data-ttu-id="e4a97-148">**text**</span><span class="sxs-lookup"><span data-stu-id="e4a97-148">**text**</span></span>|  
|`SQLBIGBINARY`|<span data-ttu-id="e4a97-149">否</span><span class="sxs-lookup"><span data-stu-id="e4a97-149">No</span></span>|<span data-ttu-id="e4a97-150">**binary**</span><span class="sxs-lookup"><span data-stu-id="e4a97-150">**binary**</span></span>|  
|`SQLBINARY`|<span data-ttu-id="e4a97-151">否</span><span class="sxs-lookup"><span data-stu-id="e4a97-151">No</span></span>|<span data-ttu-id="e4a97-152">**二進位**</span><span class="sxs-lookup"><span data-stu-id="e4a97-152">**Binary**</span></span>|  
|`SQLBIGVARBINARY`|<span data-ttu-id="e4a97-153">否</span><span class="sxs-lookup"><span data-stu-id="e4a97-153">No</span></span>|<span data-ttu-id="e4a97-154">**Varbinary**</span><span class="sxs-lookup"><span data-stu-id="e4a97-154">**Varbinary**</span></span>|  
|`SQLVARBINARY`|<span data-ttu-id="e4a97-155">否</span><span class="sxs-lookup"><span data-stu-id="e4a97-155">No</span></span>|<span data-ttu-id="e4a97-156">**Varbinary**</span><span class="sxs-lookup"><span data-stu-id="e4a97-156">**Varbinary**</span></span>|  
|`SQLIMAGE`|<span data-ttu-id="e4a97-157">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-157">Either</span></span>|<span data-ttu-id="e4a97-158">**影像**</span><span class="sxs-lookup"><span data-stu-id="e4a97-158">**Image**</span></span>|  
|`SQLINTN`|<span data-ttu-id="e4a97-159">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-159">Either</span></span>|<span data-ttu-id="e4a97-160">**int-null**</span><span class="sxs-lookup"><span data-stu-id="e4a97-160">**int-null**</span></span>|  
|`SQLDATETIMN`|<span data-ttu-id="e4a97-161">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-161">Either</span></span>|<span data-ttu-id="e4a97-162">**datetime-null**</span><span class="sxs-lookup"><span data-stu-id="e4a97-162">**datetime-null**</span></span>|  
|`SQLMONEYN`|<span data-ttu-id="e4a97-163">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-163">Either</span></span>|<span data-ttu-id="e4a97-164">**money-null**</span><span class="sxs-lookup"><span data-stu-id="e4a97-164">**money-null**</span></span>|  
|`SQLFLTN`|<span data-ttu-id="e4a97-165">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-165">Either</span></span>|<span data-ttu-id="e4a97-166">**float-null**</span><span class="sxs-lookup"><span data-stu-id="e4a97-166">**float-null**</span></span>|  
|`SQLAOPSUM`|<span data-ttu-id="e4a97-167">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-167">Either</span></span>|<span data-ttu-id="e4a97-168">**要求**</span><span class="sxs-lookup"><span data-stu-id="e4a97-168">**Sum**</span></span>|  
|`SQLAOPAVG`|<span data-ttu-id="e4a97-169">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-169">Either</span></span>|<span data-ttu-id="e4a97-170">**Avg**</span><span class="sxs-lookup"><span data-stu-id="e4a97-170">**Avg**</span></span>|  
|`SQLAOPCNT`|<span data-ttu-id="e4a97-171">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-171">Either</span></span>|<span data-ttu-id="e4a97-172">**Count**</span><span class="sxs-lookup"><span data-stu-id="e4a97-172">**Count**</span></span>|  
|`SQLAOPMIN`|<span data-ttu-id="e4a97-173">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-173">Either</span></span>|<span data-ttu-id="e4a97-174">**分鐘**</span><span class="sxs-lookup"><span data-stu-id="e4a97-174">**Min**</span></span>|  
|`SQLAOPMAX`|<span data-ttu-id="e4a97-175">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-175">Either</span></span>|<span data-ttu-id="e4a97-176">**讀數**</span><span class="sxs-lookup"><span data-stu-id="e4a97-176">**Max**</span></span>|  
|`SQLDATETIM4`|<span data-ttu-id="e4a97-177">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-177">Either</span></span>|<span data-ttu-id="e4a97-178">**smalldatetime**</span><span class="sxs-lookup"><span data-stu-id="e4a97-178">**smalldatetime**</span></span>|  
|`SQLMONEY4`|<span data-ttu-id="e4a97-179">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-179">Either</span></span>|<span data-ttu-id="e4a97-180">**Smallmoney**</span><span class="sxs-lookup"><span data-stu-id="e4a97-180">**Smallmoney**</span></span>|  
|`SQLFLT4`|<span data-ttu-id="e4a97-181">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-181">Either</span></span>|<span data-ttu-id="e4a97-182">**即時**</span><span class="sxs-lookup"><span data-stu-id="e4a97-182">**Real**</span></span>|  
|`SQLUNIQUEID`|<span data-ttu-id="e4a97-183">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-183">Either</span></span>|<span data-ttu-id="e4a97-184">**uniqueidentifier**</span><span class="sxs-lookup"><span data-stu-id="e4a97-184">**uniqueidentifier**</span></span>|  
|`SQLNCHAR`|<span data-ttu-id="e4a97-185">否</span><span class="sxs-lookup"><span data-stu-id="e4a97-185">No</span></span>|<span data-ttu-id="e4a97-186">**Nchar**</span><span class="sxs-lookup"><span data-stu-id="e4a97-186">**Nchar**</span></span>|  
|`SQLNVARCHAR`|<span data-ttu-id="e4a97-187">否</span><span class="sxs-lookup"><span data-stu-id="e4a97-187">No</span></span>|<span data-ttu-id="e4a97-188">**Nvarchar**</span><span class="sxs-lookup"><span data-stu-id="e4a97-188">**Nvarchar**</span></span>|  
|`SQLNTEXT`|<span data-ttu-id="e4a97-189">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-189">Either</span></span>|<span data-ttu-id="e4a97-190">**Ntext**</span><span class="sxs-lookup"><span data-stu-id="e4a97-190">**Ntext**</span></span>|  
|`SQLVARIANT`|<span data-ttu-id="e4a97-191">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-191">Either</span></span>|<span data-ttu-id="e4a97-192">**sql_variant**</span><span class="sxs-lookup"><span data-stu-id="e4a97-192">**sql_variant**</span></span>|  
|`SQLINT8`|<span data-ttu-id="e4a97-193">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-193">Either</span></span>|<span data-ttu-id="e4a97-194">**Bigint**</span><span class="sxs-lookup"><span data-stu-id="e4a97-194">**Bigint**</span></span>|  
|`SQLCHARACTER`|<span data-ttu-id="e4a97-195">是</span><span class="sxs-lookup"><span data-stu-id="e4a97-195">Yes</span></span>|<span data-ttu-id="e4a97-196">**varchar(max)**</span><span class="sxs-lookup"><span data-stu-id="e4a97-196">**varchar(max)**</span></span>|  
|`SQLBIGCHAR`|<span data-ttu-id="e4a97-197">是</span><span class="sxs-lookup"><span data-stu-id="e4a97-197">Yes</span></span>|<span data-ttu-id="e4a97-198">**varchar(max)**</span><span class="sxs-lookup"><span data-stu-id="e4a97-198">**varchar(max)**</span></span>|  
|`SQLBIGVARCHAR`|<span data-ttu-id="e4a97-199">是</span><span class="sxs-lookup"><span data-stu-id="e4a97-199">Yes</span></span>|<span data-ttu-id="e4a97-200">**varchar(max)**</span><span class="sxs-lookup"><span data-stu-id="e4a97-200">**varchar(max)**</span></span>|  
|`SQLVARCHAR`|<span data-ttu-id="e4a97-201">是</span><span class="sxs-lookup"><span data-stu-id="e4a97-201">Yes</span></span>|<span data-ttu-id="e4a97-202">**varchar(max)**</span><span class="sxs-lookup"><span data-stu-id="e4a97-202">**varchar(max)**</span></span>|  
|`SQLBINARY`|<span data-ttu-id="e4a97-203">是</span><span class="sxs-lookup"><span data-stu-id="e4a97-203">Yes</span></span>|<span data-ttu-id="e4a97-204">**varbinary(max)**</span><span class="sxs-lookup"><span data-stu-id="e4a97-204">**varbinary(max)**</span></span>|  
|`SQLBIGBINARY`|<span data-ttu-id="e4a97-205">是</span><span class="sxs-lookup"><span data-stu-id="e4a97-205">Yes</span></span>|<span data-ttu-id="e4a97-206">**varbinary(max)**</span><span class="sxs-lookup"><span data-stu-id="e4a97-206">**varbinary(max)**</span></span>|  
|`SQLBIGVARBINARY`|<span data-ttu-id="e4a97-207">是</span><span class="sxs-lookup"><span data-stu-id="e4a97-207">Yes</span></span>|<span data-ttu-id="e4a97-208">**varbinary(max)**</span><span class="sxs-lookup"><span data-stu-id="e4a97-208">**varbinary(max)**</span></span>|  
|`SQLVARBINARY`|<span data-ttu-id="e4a97-209">是</span><span class="sxs-lookup"><span data-stu-id="e4a97-209">Yes</span></span>|<span data-ttu-id="e4a97-210">**varbinary(max)**</span><span class="sxs-lookup"><span data-stu-id="e4a97-210">**varbinary(max)**</span></span>|  
|`SQLNCHAR`|<span data-ttu-id="e4a97-211">是</span><span class="sxs-lookup"><span data-stu-id="e4a97-211">Yes</span></span>|<span data-ttu-id="e4a97-212">**nvarchar(max)**</span><span class="sxs-lookup"><span data-stu-id="e4a97-212">**nvarchar(max)**</span></span>|  
|`SQLNVARCHAR`|<span data-ttu-id="e4a97-213">是</span><span class="sxs-lookup"><span data-stu-id="e4a97-213">Yes</span></span>|<span data-ttu-id="e4a97-214">**nvarchar(max)**</span><span class="sxs-lookup"><span data-stu-id="e4a97-214">**nvarchar(max)**</span></span>|  
|`SQLXML`|<span data-ttu-id="e4a97-215">是</span><span class="sxs-lookup"><span data-stu-id="e4a97-215">Yes</span></span>|<span data-ttu-id="e4a97-216">**XML**</span><span class="sxs-lookup"><span data-stu-id="e4a97-216">**Xml**</span></span>|  
|`SQLUDT`|<span data-ttu-id="e4a97-217">之前或之後</span><span class="sxs-lookup"><span data-stu-id="e4a97-217">Either</span></span>|<span data-ttu-id="e4a97-218">**Udt**</span><span class="sxs-lookup"><span data-stu-id="e4a97-218">**Udt**</span></span>|  
  
## <a name="bcp_gettypename-support-for-enhanced-date-and-time-features"></a><span data-ttu-id="e4a97-219">bcp_gettypename 支援增強的日期和時間功能</span><span class="sxs-lookup"><span data-stu-id="e4a97-219">bcp_gettypename Support for Enhanced Date and Time Features</span></span>  
 <span data-ttu-id="e4a97-220">適用于日期/時間類型的 token 參數值會在[&#40;OLE DB 和 ODBC&#41;的增強型日期和時間類型的大量複製變更](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md)中，描述于資料表中的 "Type in sqlncli. h" 資料行。</span><span class="sxs-lookup"><span data-stu-id="e4a97-220">The token parameter values for date/time types are described in the "Type in sqlncli.h" column of the table in [Bulk Copy Changes for Enhanced Date and Time Types &#40;OLE DB and ODBC&#41;](../native-client-odbc-date-time/bulk-copy-changes-for-enhanced-date-and-time-types-ole-db-and-odbc.md).</span></span> <span data-ttu-id="e4a97-221">傳回值位於 "File storage type" 資料行的對應資料列中。</span><span class="sxs-lookup"><span data-stu-id="e4a97-221">The returned value is in the corresponding row of the "File storage type" column.</span></span>  
  
 <span data-ttu-id="e4a97-222">如需詳細資訊，請參閱[ODBC&#41;&#40;的日期和時間改善](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)。</span><span class="sxs-lookup"><span data-stu-id="e4a97-222">For more information, see [Date and Time Improvements &#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4a97-223">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4a97-223">See Also</span></span>  
 [<span data-ttu-id="e4a97-224">大量複製函數</span><span class="sxs-lookup"><span data-stu-id="e4a97-224">Bulk Copy Functions</span></span>](sql-server-driver-extensions-bulk-copy-functions.md)  
  
  
