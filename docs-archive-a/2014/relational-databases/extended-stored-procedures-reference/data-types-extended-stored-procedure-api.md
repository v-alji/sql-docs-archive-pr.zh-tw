---
title: 資料類型 (擴充預存程序 API) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: stored-procedures
ms.topic: reference
helpviewer_keywords:
- extended stored procedures [SQL Server], data types
- data types [SQL Server], extended stored procedures
ms.assetid: 37fb86b9-8819-4387-bcdc-9616968e15ad
author: rothja
ms.author: jroth
ms.openlocfilehash: aae0c6f2b309d182a93274171d2f8c21344fe3b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584511"
---
# <a name="data-types-extended-stored-procedure-api"></a><span data-ttu-id="8802d-102">資料類型 (擴充預存程序 API)</span><span class="sxs-lookup"><span data-stu-id="8802d-102">Data Types (Extended Stored Procedure API)</span></span>
    
> [!IMPORTANT]  
>  [!INCLUDE[ssNoteDepFutureDontUse](../../includes/ssnotedepfuturedontuse-md.md)] <span data-ttu-id="8802d-103">請改用 CLR 整合。</span><span class="sxs-lookup"><span data-stu-id="8802d-103">Use CLR integration instead.</span></span>  
  
 <span data-ttu-id="8802d-104">若要使用擴充預存程序 API 資料類型，請在程式中包含 Srv.h 標頭檔案。</span><span class="sxs-lookup"><span data-stu-id="8802d-104">To use the Extended Stored Procedure API data types, include the Srv.h header file in your program.</span></span>  
  
|<span data-ttu-id="8802d-105">資料類型</span><span class="sxs-lookup"><span data-stu-id="8802d-105">Data type</span></span>|<span data-ttu-id="8802d-106">SQL Server 資料類型</span><span class="sxs-lookup"><span data-stu-id="8802d-106">SQL Server data type</span></span>|<span data-ttu-id="8802d-107">描述</span><span class="sxs-lookup"><span data-stu-id="8802d-107">Description</span></span>|  
|---------------|--------------------------|-----------------|  
|<span data-ttu-id="8802d-108">SRVBIGBINARY</span><span class="sxs-lookup"><span data-stu-id="8802d-108">SRVBIGBINARY</span></span>|`binary`|<span data-ttu-id="8802d-109">`binary` 資料類型，長度為 0 到 8000 個位元組。</span><span class="sxs-lookup"><span data-stu-id="8802d-109">`binary` data type, length 0 to 8000 bytes.</span></span>|  
|<span data-ttu-id="8802d-110">SRVBIGCHAR</span><span class="sxs-lookup"><span data-stu-id="8802d-110">SRVBIGCHAR</span></span>|`char`|<span data-ttu-id="8802d-111">`character` 資料類型，長度為 0 到 8000 個位元組。</span><span class="sxs-lookup"><span data-stu-id="8802d-111">`character` data type, length 0 to 8000 bytes.</span></span>|  
|<span data-ttu-id="8802d-112">SRVBIGVARBINARY</span><span class="sxs-lookup"><span data-stu-id="8802d-112">SRVBIGVARBINARY</span></span>|`varbinary`|<span data-ttu-id="8802d-113">可變長度的 `binary` 資料類型，長度為 0 到 8000 個字元組。</span><span class="sxs-lookup"><span data-stu-id="8802d-113">Variable-length `binary` data type, length 0 to 8000 bytes.</span></span>|  
|<span data-ttu-id="8802d-114">SRVBIGVARCHAR</span><span class="sxs-lookup"><span data-stu-id="8802d-114">SRVBIGVARCHAR</span></span>|`varchar`|<span data-ttu-id="8802d-115">可變長度的 `character` 資料類型，長度為 0 到 8000 個字元組。</span><span class="sxs-lookup"><span data-stu-id="8802d-115">Variable-length `character` data type, length 0 to 8000 bytes.</span></span>|  
|<span data-ttu-id="8802d-116">SRVBINARY</span><span class="sxs-lookup"><span data-stu-id="8802d-116">SRVBINARY</span></span>|`binary`|<span data-ttu-id="8802d-117">`binary` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-117">`binary` data type.</span></span>|  
|<span data-ttu-id="8802d-118">SRVBIT</span><span class="sxs-lookup"><span data-stu-id="8802d-118">SRVBIT</span></span>|`Bit`|<span data-ttu-id="8802d-119">`bit` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-119">`bit` data type.</span></span>|  
|<span data-ttu-id="8802d-120">SRVBITN</span><span class="sxs-lookup"><span data-stu-id="8802d-120">SRVBITN</span></span>|`bit null`|<span data-ttu-id="8802d-121">`bit` 資料類型，允許 Null 值。</span><span class="sxs-lookup"><span data-stu-id="8802d-121">`bit` data type, null values allowed.</span></span>|  
|<span data-ttu-id="8802d-122">SRVCHAR</span><span class="sxs-lookup"><span data-stu-id="8802d-122">SRVCHAR</span></span>|`char`|<span data-ttu-id="8802d-123">`character` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-123">`character` data type.</span></span>|  
|<span data-ttu-id="8802d-124">SRVDATETIME</span><span class="sxs-lookup"><span data-stu-id="8802d-124">SRVDATETIME</span></span>|`datetime`|<span data-ttu-id="8802d-125">8 個位元組的 `datetime` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-125">8-byte `datetime` data type.</span></span>|  
|<span data-ttu-id="8802d-126">SRVDATETIM4</span><span class="sxs-lookup"><span data-stu-id="8802d-126">SRVDATETIM4</span></span>|`smalldatetime`|<span data-ttu-id="8802d-127">4個位元組的 `smalldatetime` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-127">4-byte `smalldatetime` data type.</span></span>|  
|<span data-ttu-id="8802d-128">SRVDATETIMN</span><span class="sxs-lookup"><span data-stu-id="8802d-128">SRVDATETIMN</span></span>|<span data-ttu-id="8802d-129">**datetime null**</span><span class="sxs-lookup"><span data-stu-id="8802d-129">**datetime null**</span></span>|<span data-ttu-id="8802d-130">`smalldatetime` 或 `datetime` 資料類型，允許 Null 值。</span><span class="sxs-lookup"><span data-stu-id="8802d-130">`smalldatetime` or `datetime` data type, null values allowed.</span></span>|  
|<span data-ttu-id="8802d-131">SRVDECIMAL</span><span class="sxs-lookup"><span data-stu-id="8802d-131">SRVDECIMAL</span></span>|`decimal`|<span data-ttu-id="8802d-132">`decimal` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-132">`decimal` data type.</span></span>|  
|<span data-ttu-id="8802d-133">SRVDECIMALN</span><span class="sxs-lookup"><span data-stu-id="8802d-133">SRVDECIMALN</span></span>|`decimal null`|<span data-ttu-id="8802d-134">`decimal` 資料類型，允許 Null 值。</span><span class="sxs-lookup"><span data-stu-id="8802d-134">`decimal` data type, null values allowed.</span></span>|  
|<span data-ttu-id="8802d-135">SRVFLT4</span><span class="sxs-lookup"><span data-stu-id="8802d-135">SRVFLT4</span></span>|`real`|<span data-ttu-id="8802d-136">4個位元組的 `real` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-136">4-byte `real` data type.</span></span>|  
|<span data-ttu-id="8802d-137">SRVFLT8</span><span class="sxs-lookup"><span data-stu-id="8802d-137">SRVFLT8</span></span>|`float`|<span data-ttu-id="8802d-138">8 個位元組的 `float` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-138">8-byte `float` data type.</span></span>|  
|<span data-ttu-id="8802d-139">SRVFLTN</span><span class="sxs-lookup"><span data-stu-id="8802d-139">SRVFLTN</span></span>|<span data-ttu-id="8802d-140">`real` &#124; `float null`</span><span class="sxs-lookup"><span data-stu-id="8802d-140">`real` &#124; `float null`</span></span>|<span data-ttu-id="8802d-141">`real` 或 `float` 資料類型，允許 Null 值。</span><span class="sxs-lookup"><span data-stu-id="8802d-141">`real` or `float` data type, null values allowed.</span></span>|  
|<span data-ttu-id="8802d-142">SRVIMAGE</span><span class="sxs-lookup"><span data-stu-id="8802d-142">SRVIMAGE</span></span>|`image`|<span data-ttu-id="8802d-143">`image` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-143">`image` data type.</span></span>|  
|<span data-ttu-id="8802d-144">SRVINT1</span><span class="sxs-lookup"><span data-stu-id="8802d-144">SRVINT1</span></span>|`tinyint`|<span data-ttu-id="8802d-145">1個位元組的 `tinyint` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-145">1-byte `tinyint` data type.</span></span>|  
|<span data-ttu-id="8802d-146">SRVINT2</span><span class="sxs-lookup"><span data-stu-id="8802d-146">SRVINT2</span></span>|`smallint`|<span data-ttu-id="8802d-147">2個位元組的 `smallint` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-147">2-byte `smallint` data type.</span></span>|  
|<span data-ttu-id="8802d-148">SRVINT4</span><span class="sxs-lookup"><span data-stu-id="8802d-148">SRVINT4</span></span>|`int`|<span data-ttu-id="8802d-149">4個位元組的 `int` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-149">4-byte `int` data type.</span></span>|  
|<span data-ttu-id="8802d-150">SRVINTN</span><span class="sxs-lookup"><span data-stu-id="8802d-150">SRVINTN</span></span>|<span data-ttu-id="8802d-151">`tinyint` &#124; `smallint` &#124; `int null`</span><span class="sxs-lookup"><span data-stu-id="8802d-151">`tinyint` &#124; `smallint` &#124; `int null`</span></span>|<span data-ttu-id="8802d-152">`tinyint`、`smallint` 或 `int` 資料類型，允許 Null 值。</span><span class="sxs-lookup"><span data-stu-id="8802d-152">`tinyint`, `smallint`, or `int` data type, null values allowed.</span></span>|  
|<span data-ttu-id="8802d-153">SRVMONEY4</span><span class="sxs-lookup"><span data-stu-id="8802d-153">SRVMONEY4</span></span>|`smallmoney`|<span data-ttu-id="8802d-154">4個位元組的 `smallmoney` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-154">4-byte `smallmoney` data type.</span></span>|  
|<span data-ttu-id="8802d-155">SRVMONEY</span><span class="sxs-lookup"><span data-stu-id="8802d-155">SRVMONEY</span></span>|`money`|<span data-ttu-id="8802d-156">8 個位元組的 `money` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-156">8-byte `money` data type.</span></span>|  
|<span data-ttu-id="8802d-157">SRVMONEYN</span><span class="sxs-lookup"><span data-stu-id="8802d-157">SRVMONEYN</span></span>|<span data-ttu-id="8802d-158">`money` &#124; `smallmoney null`</span><span class="sxs-lookup"><span data-stu-id="8802d-158">`money` &#124; `smallmoney null`</span></span>|<span data-ttu-id="8802d-159">`smallmoney` 或 `money` 資料類型，允許 Null 值。</span><span class="sxs-lookup"><span data-stu-id="8802d-159">`smallmoney` or `money` data type, null values allowed.</span></span>|  
|<span data-ttu-id="8802d-160">SRVNCHAR</span><span class="sxs-lookup"><span data-stu-id="8802d-160">SRVNCHAR</span></span>|<span data-ttu-id="8802d-161">**nchar**</span><span class="sxs-lookup"><span data-stu-id="8802d-161">**nchar**</span></span>|<span data-ttu-id="8802d-162">Unicode `character` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-162">Unicode `character` data type.</span></span>|  
|<span data-ttu-id="8802d-163">SRVNTEXT</span><span class="sxs-lookup"><span data-stu-id="8802d-163">SRVNTEXT</span></span>|`ntext`|<span data-ttu-id="8802d-164">Unicode `text` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-164">Unicode `text` data type.</span></span>|  
|<span data-ttu-id="8802d-165">SRVNUMERIC</span><span class="sxs-lookup"><span data-stu-id="8802d-165">SRVNUMERIC</span></span>|`numeric`|<span data-ttu-id="8802d-166">`numeric` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-166">`numeric` data type.</span></span>|  
|<span data-ttu-id="8802d-167">SRVNUMERICN</span><span class="sxs-lookup"><span data-stu-id="8802d-167">SRVNUMERICN</span></span>|`numeric null`|<span data-ttu-id="8802d-168">`numeric` 資料類型，允許 Null 值。</span><span class="sxs-lookup"><span data-stu-id="8802d-168">`numeric` data type, null values allowed.</span></span>|  
|<span data-ttu-id="8802d-169">SRVNVARCHAR</span><span class="sxs-lookup"><span data-stu-id="8802d-169">SRVNVARCHAR</span></span>|<span data-ttu-id="8802d-170">**nvarchar**</span><span class="sxs-lookup"><span data-stu-id="8802d-170">**nvarchar**</span></span>|<span data-ttu-id="8802d-171">Unicode 可變長度的 `character` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-171">Unicode variable-length `character` data type.</span></span>|  
|<span data-ttu-id="8802d-172">SRVTEXT</span><span class="sxs-lookup"><span data-stu-id="8802d-172">SRVTEXT</span></span>|`text`|<span data-ttu-id="8802d-173">`text` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-173">`text` data type.</span></span>|  
|<span data-ttu-id="8802d-174">SRVVARBINARY</span><span class="sxs-lookup"><span data-stu-id="8802d-174">SRVVARBINARY</span></span>|`varbinary`|<span data-ttu-id="8802d-175">可變長度的 `binary` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-175">Variable-length `binary` data type.</span></span>|  
|<span data-ttu-id="8802d-176">SRVVARCHAR</span><span class="sxs-lookup"><span data-stu-id="8802d-176">SRVVARCHAR</span></span>|`varchar`|<span data-ttu-id="8802d-177">可變長度的 `character` 資料類型。</span><span class="sxs-lookup"><span data-stu-id="8802d-177">Variable-length `character` data type.</span></span>|  
  
> [!IMPORTANT]  
>  <span data-ttu-id="8802d-178">您應該徹底檢閱擴充預存程序的原始程式碼，您也應該先測試編譯過的 DLL，才能將它們安裝在實際執行伺服器上。</span><span class="sxs-lookup"><span data-stu-id="8802d-178">You should thoroughly review the source code of extended stored procedures, and you should test the compiled DLLs before you install them on a production server.</span></span> <span data-ttu-id="8802d-179">如需安全性檢閱和測試的資訊，請參閱此 [Microsoft 網站](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/)。</span><span class="sxs-lookup"><span data-stu-id="8802d-179">For information about security review and testing, see this [Microsoft Web site](https://go.microsoft.com/fwlink/?LinkID=54761&amp;clcid=0x409https://msdn.microsoft.com/security/).</span></span>  
  
  
