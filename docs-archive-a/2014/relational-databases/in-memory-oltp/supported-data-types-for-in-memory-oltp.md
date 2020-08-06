---
title: 支援的資料類型 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: a7380ef0-c9d7-49e4-b6de-fad34752b9f3
author: rothja
ms.author: jroth
ms.openlocfilehash: a7dda500486c39a66f871d5934f957028fc51e9d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708345"
---
# <a name="supported-data-types"></a><span data-ttu-id="cc183-102">支援的資料類型</span><span class="sxs-lookup"><span data-stu-id="cc183-102">Supported Data Types</span></span>
  <span data-ttu-id="cc183-103">記憶體最佳化的資料表及原生編譯預存程序 **支援** 下列資料類型：</span><span class="sxs-lookup"><span data-stu-id="cc183-103">The following data types are **supported** in memory-optimized tables and natively compiled stored procedures:</span></span>  
  
 <span data-ttu-id="cc183-104">**數值資料類型**</span><span class="sxs-lookup"><span data-stu-id="cc183-104">**Numeric Data Types**</span></span>  
  
|<span data-ttu-id="cc183-105">資料類型</span><span class="sxs-lookup"><span data-stu-id="cc183-105">Data type</span></span>|<span data-ttu-id="cc183-106">取得詳細資訊</span><span class="sxs-lookup"><span data-stu-id="cc183-106">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="cc183-107">int</span><span class="sxs-lookup"><span data-stu-id="cc183-107">int</span></span>|[<span data-ttu-id="cc183-108">int、bigint、smallint 和 tinyint &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-108">int, bigint, smallint, and tinyint &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|<span data-ttu-id="cc183-109">BIGINT</span><span class="sxs-lookup"><span data-stu-id="cc183-109">bigint</span></span>|[<span data-ttu-id="cc183-110">int、bigint、smallint 和 tinyint &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-110">int, bigint, smallint, and tinyint &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|<span data-ttu-id="cc183-111">SMALLINT</span><span class="sxs-lookup"><span data-stu-id="cc183-111">smallint</span></span>|[<span data-ttu-id="cc183-112">int、bigint、smallint 和 tinyint &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-112">int, bigint, smallint, and tinyint &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|<span data-ttu-id="cc183-113">TINYINT</span><span class="sxs-lookup"><span data-stu-id="cc183-113">tinyint</span></span>|[<span data-ttu-id="cc183-114">int、bigint、smallint 和 tinyint &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-114">int, bigint, smallint, and tinyint &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/int-bigint-smallint-and-tinyint-transact-sql)|  
|<span data-ttu-id="cc183-115">decimal</span><span class="sxs-lookup"><span data-stu-id="cc183-115">decimal</span></span>|[<span data-ttu-id="cc183-116">decimal 和 numeric &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-116">decimal and numeric &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|<span data-ttu-id="cc183-117">NUMERIC</span><span class="sxs-lookup"><span data-stu-id="cc183-117">numeric</span></span>|[<span data-ttu-id="cc183-118">decimal 和 numeric &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-118">decimal and numeric &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/decimal-and-numeric-transact-sql)|  
|<span data-ttu-id="cc183-119">FLOAT</span><span class="sxs-lookup"><span data-stu-id="cc183-119">float</span></span>|[<span data-ttu-id="cc183-120">float 和 real &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-120">float and real &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|<span data-ttu-id="cc183-121">real</span><span class="sxs-lookup"><span data-stu-id="cc183-121">real</span></span>|[<span data-ttu-id="cc183-122">float 和 real &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-122">float and real &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/float-and-real-transact-sql)|  
|<span data-ttu-id="cc183-123">money</span><span class="sxs-lookup"><span data-stu-id="cc183-123">money</span></span>|[<span data-ttu-id="cc183-124">money 和 smallmoney &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-124">money and smallmoney &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
|<span data-ttu-id="cc183-125">SMALLMONEY</span><span class="sxs-lookup"><span data-stu-id="cc183-125">smallmoney</span></span>|[<span data-ttu-id="cc183-126">money 和 smallmoney &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-126">money and smallmoney &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/money-and-smallmoney-transact-sql)|  
  
 <span data-ttu-id="cc183-127">**字串資料類型**</span><span class="sxs-lookup"><span data-stu-id="cc183-127">**String Data Types**</span></span>  
  
|<span data-ttu-id="cc183-128">資料類型</span><span class="sxs-lookup"><span data-stu-id="cc183-128">Data type</span></span>|<span data-ttu-id="cc183-129">取得詳細資訊</span><span class="sxs-lookup"><span data-stu-id="cc183-129">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="cc183-130">char(n)</span><span class="sxs-lookup"><span data-stu-id="cc183-130">char(n)</span></span>|[<span data-ttu-id="cc183-131">char 和 varchar &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-131">char and varchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|<span data-ttu-id="cc183-132">Varchar (n) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cc183-132">varchar(n) <sup>1</sup></span></span>|[<span data-ttu-id="cc183-133">char 和 varchar &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-133">char and varchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/char-and-varchar-transact-sql)|  
|<span data-ttu-id="cc183-134">nchar(n)</span><span class="sxs-lookup"><span data-stu-id="cc183-134">nchar(n)</span></span>|[<span data-ttu-id="cc183-135">nchar 和 nvarchar &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-135">nchar and nvarchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|<span data-ttu-id="cc183-136">Nvarchar (n) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cc183-136">nvarchar(n) <sup>1</sup></span></span>|[<span data-ttu-id="cc183-137">nchar 和 nvarchar &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-137">nchar and nvarchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
|<span data-ttu-id="cc183-138">sysname</span><span class="sxs-lookup"><span data-stu-id="cc183-138">sysname</span></span>|[<span data-ttu-id="cc183-139">nchar 和 nvarchar &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-139">nchar and nvarchar &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/nchar-and-nvarchar-transact-sql)|  
  
 <span data-ttu-id="cc183-140"><sup>1</sup>限制為每個資料列總計8060個位元組，計算可變長度類型中 (n) 。</span><span class="sxs-lookup"><span data-stu-id="cc183-140"><sup>1</sup> Limitation is 8060 bytes per row total, counting (n) in variable-length types.</span></span>  
  
 <span data-ttu-id="cc183-141">如需支援之定序的資訊，請參閱＜ [Collations and Code Pages](../../database-engine/collations-and-code-pages.md)＞。</span><span class="sxs-lookup"><span data-stu-id="cc183-141">For information about supported collations, see [Collations and Code Pages](../../database-engine/collations-and-code-pages.md).</span></span>  
  
 <span data-ttu-id="cc183-142">**日期和時間資料類型**</span><span class="sxs-lookup"><span data-stu-id="cc183-142">**Date and Time Data Types**</span></span>  
  
|<span data-ttu-id="cc183-143">資料類型</span><span class="sxs-lookup"><span data-stu-id="cc183-143">Data type</span></span>|<span data-ttu-id="cc183-144">取得詳細資訊</span><span class="sxs-lookup"><span data-stu-id="cc183-144">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="cc183-145">date</span><span class="sxs-lookup"><span data-stu-id="cc183-145">date</span></span>|[<span data-ttu-id="cc183-146">日期 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-146">date &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/date-transact-sql)|  
|<span data-ttu-id="cc183-147">time</span><span class="sxs-lookup"><span data-stu-id="cc183-147">time</span></span>|[<span data-ttu-id="cc183-148">time &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-148">time &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/time-transact-sql)|  
|<span data-ttu-id="cc183-149">Datetime</span><span class="sxs-lookup"><span data-stu-id="cc183-149">datetime</span></span>|[<span data-ttu-id="cc183-150">datetime &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-150">datetime &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/datetime-transact-sql)|  
|<span data-ttu-id="cc183-151">datetime2</span><span class="sxs-lookup"><span data-stu-id="cc183-151">datetime2</span></span>|[<span data-ttu-id="cc183-152">datetime2 &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-152">datetime2 &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/datetime2-transact-sql)|  
|<span data-ttu-id="cc183-153">smalldatetime</span><span class="sxs-lookup"><span data-stu-id="cc183-153">smalldatetime</span></span>|[<span data-ttu-id="cc183-154">smalldatetime &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-154">smalldatetime &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/smalldatetime-transact-sql)|  
  
 <span data-ttu-id="cc183-155">**二進位資料類型**</span><span class="sxs-lookup"><span data-stu-id="cc183-155">**Binary Data Types**</span></span>  
  
|<span data-ttu-id="cc183-156">資料類型</span><span class="sxs-lookup"><span data-stu-id="cc183-156">Data type</span></span>|<span data-ttu-id="cc183-157">取得詳細資訊</span><span class="sxs-lookup"><span data-stu-id="cc183-157">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="cc183-158">bit</span><span class="sxs-lookup"><span data-stu-id="cc183-158">bit</span></span>|[<span data-ttu-id="cc183-159">bit &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-159">bit &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/bit-transact-sql)|  
|<span data-ttu-id="cc183-160">binary(n)</span><span class="sxs-lookup"><span data-stu-id="cc183-160">binary(n)</span></span>|[<span data-ttu-id="cc183-161">binary 和 varbinary &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-161">binary and varbinary &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
|<span data-ttu-id="cc183-162">Varbinary (n) <sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="cc183-162">varbinary(n) <sup>1</sup></span></span>|[<span data-ttu-id="cc183-163">binary 和 varbinary &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-163">binary and varbinary &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/binary-and-varbinary-transact-sql)|  
  
 <span data-ttu-id="cc183-164"><sup>1</sup>限制為每個資料列總計8060個位元組，計算可變長度類型中 (n) 。</span><span class="sxs-lookup"><span data-stu-id="cc183-164"><sup>1</sup> Limitation is 8060 bytes per row total, counting (n) in variable-length types.</span></span>  
  
 <span data-ttu-id="cc183-165">**其他資料類型**</span><span class="sxs-lookup"><span data-stu-id="cc183-165">**Other data types**</span></span>  
  
|<span data-ttu-id="cc183-166">資料類型</span><span class="sxs-lookup"><span data-stu-id="cc183-166">Data type</span></span>|<span data-ttu-id="cc183-167">取得詳細資訊</span><span class="sxs-lookup"><span data-stu-id="cc183-167">For more information</span></span>|  
|---------------|--------------------------|  
|<span data-ttu-id="cc183-168">UNIQUEIDENTIFIER</span><span class="sxs-lookup"><span data-stu-id="cc183-168">uniqueidentifier</span></span>|[<span data-ttu-id="cc183-169">uniqueidentifier &#40;Transact-SQL&#41;</span><span class="sxs-lookup"><span data-stu-id="cc183-169">uniqueidentifier &#40;Transact-SQL&#41;</span></span>](/sql/t-sql/data-types/uniqueidentifier-transact-sql)|  
  
 <span data-ttu-id="cc183-170">**不支援的資料類型**</span><span class="sxs-lookup"><span data-stu-id="cc183-170">**Unsupported Data Types**</span></span>  
  
 <span data-ttu-id="cc183-171">以下是不支援的資料類型：</span><span class="sxs-lookup"><span data-stu-id="cc183-171">The following data types are not supported:</span></span>  
  
||||  
|-|-|-|  
|<span data-ttu-id="cc183-172">DATETIMEOFFSET</span><span class="sxs-lookup"><span data-stu-id="cc183-172">DATETIMEOFFSET</span></span>|<span data-ttu-id="cc183-173">GEOGRAPHY</span><span class="sxs-lookup"><span data-stu-id="cc183-173">GEOGRAPHY</span></span>|<span data-ttu-id="cc183-174">GEOMETRY</span><span class="sxs-lookup"><span data-stu-id="cc183-174">GEOMETRY</span></span>|  
|<span data-ttu-id="cc183-175">HIERARCHYID</span><span class="sxs-lookup"><span data-stu-id="cc183-175">HIERARCHYID</span></span>|<span data-ttu-id="cc183-176">大型物件 (LOB)。</span><span class="sxs-lookup"><span data-stu-id="cc183-176">Large Objects (LOBs).</span></span> <span data-ttu-id="cc183-177">例如，varchar(max)、nvarchar(max)、varbinary(max)、影像、xml、文字和 ntext。</span><span class="sxs-lookup"><span data-stu-id="cc183-177">For example, varchar(max), nvarchar(max), varbinary(max), image, xml, text, and ntext.</span></span>|<span data-ttu-id="cc183-178">ROWVERSION</span><span class="sxs-lookup"><span data-stu-id="cc183-178">ROWVERSION</span></span>|  
|<span data-ttu-id="cc183-179">sql_variant</span><span class="sxs-lookup"><span data-stu-id="cc183-179">sql_variant</span></span>|<span data-ttu-id="cc183-180">CLR 函數</span><span class="sxs-lookup"><span data-stu-id="cc183-180">CLR functions</span></span>|<span data-ttu-id="cc183-181">使用者定義型別 (UDT)</span><span class="sxs-lookup"><span data-stu-id="cc183-181">User-defined types (UDTs)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cc183-182">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc183-182">See Also</span></span>  
 <span data-ttu-id="cc183-183">[記憶體中 OLTP 的 Transact-SQL 支援](transact-sql-support-for-in-memory-oltp.md) </span><span class="sxs-lookup"><span data-stu-id="cc183-183">[Transact-SQL Support for In-Memory OLTP](transact-sql-support-for-in-memory-oltp.md) </span></span>  
 <span data-ttu-id="cc183-184">[在記憶體優化資料表中執行 LOB 資料行](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md) </span><span class="sxs-lookup"><span data-stu-id="cc183-184">[Implementing LOB Columns in a Memory-Optimized Table](../../database-engine/implementing-lob-columns-in-a-memory-optimized-table.md) </span></span>  
 [<span data-ttu-id="cc183-185">在記憶體最佳化資料表中實作 SQL_VARIANT</span><span class="sxs-lookup"><span data-stu-id="cc183-185">Implementing SQL_VARIANT in a Memory-Optimized Table</span></span>](implementing-sql-variant-in-a-memory-optimized-table.md)  
  
  
