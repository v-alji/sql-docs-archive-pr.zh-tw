---
title: 函式 (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- functions [Integration Services]
- expressions [Integration Services], functions
- string functions
- SQL Server Integration Services, functions
- SSIS, functions
ms.assetid: e9a41a31-94f4-46a4-b737-c707dd59ce48
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 298085a1e3b9c292c9289415a4cb8a3c5adabea1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594605"
---
# <a name="functions-ssis-expression"></a><span data-ttu-id="fb8c7-102">函數 (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="fb8c7-102">Functions (SSIS Expression)</span></span>
  <span data-ttu-id="fb8c7-103">運算式語言包含一組可在運算式中使用的函數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-103">The expression language includes a set of functions for use in expressions.</span></span> <span data-ttu-id="fb8c7-104">運算式可使用單一函數，但通常運算式會結合函數與運算子，並使用多個函數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-104">An expression can use a single function, but typically an expression combines functions with operators and uses multiple functions.</span></span>  
  
 <span data-ttu-id="fb8c7-105">函數可分類成下列各群組：</span><span class="sxs-lookup"><span data-stu-id="fb8c7-105">The functions can be categorized into the following groups:</span></span>  
  
-   <span data-ttu-id="fb8c7-106">數學函數，執行以做為函數參數的數字輸入值為主的運算並傳回數值。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-106">Mathematical functions that perform calculations based on numeric input values provided as parameters to the functions and return numeric values.</span></span>  
  
-   <span data-ttu-id="fb8c7-107">字串函數，執行字串和十六進位輸入值的運算，並傳回字串或數值。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-107">String functions that perform operations on string or hexadecimal input values and return a string or numeric value.</span></span>  
  
-   <span data-ttu-id="fb8c7-108">日期和時間函數，執行日期和時間值的運算，並傳回字串、數值或日期和時間值。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-108">Date and time functions that perform operations on date and time values and return string, numeric, or date and time values.</span></span>  
  
-   <span data-ttu-id="fb8c7-109">系統函數，會傳回運算式的資訊。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-109">System functions that return information about an expression.</span></span>  
  
 <span data-ttu-id="fb8c7-110">運算式語言提供下列數學函數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-110">The expression language provides the following mathematical functions.</span></span>  
  
|<span data-ttu-id="fb8c7-111">函式</span><span class="sxs-lookup"><span data-stu-id="fb8c7-111">Function</span></span>|<span data-ttu-id="fb8c7-112">描述</span><span class="sxs-lookup"><span data-stu-id="fb8c7-112">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="fb8c7-113">ABS &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-113">ABS &#40;SSIS Expression&#41;</span></span>](abs-ssis-expression.md)|<span data-ttu-id="fb8c7-114">傳回數值運算式的絕對正數值。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-114">Returns the absolute, positive value of a numeric expression.</span></span>|  
|[<span data-ttu-id="fb8c7-115">EXP &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-115">EXP &#40;SSIS Expression&#41;</span></span>](exp-ssis-expression.md)|<span data-ttu-id="fb8c7-116">傳回做為指定運算式中 e 之基底的指數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-116">Returns the exponent to base e of the specified expression.</span></span>|  
|[<span data-ttu-id="fb8c7-117">CEILING &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-117">CEILING &#40;SSIS Expression&#41;</span></span>](ceiling-ssis-expression.md)|<span data-ttu-id="fb8c7-118">傳回大於或等於數值運算式的最小整數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-118">Returns the smallest integer that is greater than or equal to a numeric expression.</span></span>|  
|[<span data-ttu-id="fb8c7-119">FLOOR &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-119">FLOOR &#40;SSIS Expression&#41;</span></span>](floor-ssis-expression.md)|<span data-ttu-id="fb8c7-120">傳回小於或等於數值運算式的最大整數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-120">Returns the largest integer that is less than or equal to a numeric expression.</span></span>|  
|[<span data-ttu-id="fb8c7-121">LN &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-121">LN &#40;SSIS Expression&#41;</span></span>](ln-ssis-expression.md)|<span data-ttu-id="fb8c7-122">傳回數值運算式的自然對數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-122">Returns the natural logarithm of a numeric expression.</span></span>|  
|[<span data-ttu-id="fb8c7-123">LOG &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-123">LOG &#40;SSIS Expression&#41;</span></span>](log-ssis-expression.md)|<span data-ttu-id="fb8c7-124">傳回數值運算式以 10 為底的對數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-124">Returns the base-10 logarithm of a numeric expression.</span></span>|  
|[<span data-ttu-id="fb8c7-125">POWER &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-125">POWER &#40;SSIS Expression&#41;</span></span>](power-ssis-expression.md)|<span data-ttu-id="fb8c7-126">傳回數值運算式的乘冪結果。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-126">Returns the result of raising a numeric expression to a power.</span></span>|  
|[<span data-ttu-id="fb8c7-127">ROUND &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-127">ROUND &#40;SSIS Expression&#41;</span></span>](round-ssis-expression.md)|<span data-ttu-id="fb8c7-128">傳回已經進位到指定長度或有效位數的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-128">Returns a numeric expression that is rounded to the specified length or precision.</span></span> <span data-ttu-id="fb8c7-129">。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-129">.</span></span>|  
|[<span data-ttu-id="fb8c7-130">SIGN &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-130">SIGN &#40;SSIS Expression&#41;</span></span>](sign-ssis-expression.md)|<span data-ttu-id="fb8c7-131">傳回數值運算式的正 (+)、負 (-) 或零 (0) 符號。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-131">Returns the positive (+), negative (-), or zero (0) sign of a numeric expression.</span></span>|  
|[<span data-ttu-id="fb8c7-132">SQUARE &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-132">SQUARE &#40;SSIS Expression&#41;</span></span>](square-ssis-expression.md)|<span data-ttu-id="fb8c7-133">傳回數值運算式的平方。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-133">Returns the square of a numeric expression.</span></span>|  
|[<span data-ttu-id="fb8c7-134">SQRT &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-134">SQRT &#40;SSIS Expression&#41;</span></span>](sqrt-ssis-expression.md)|<span data-ttu-id="fb8c7-135">傳回數值運算式的平方根。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-135">Returns the square root of a numeric expression.</span></span>|  
  
 <span data-ttu-id="fb8c7-136">運算式評估工具提供下列字串函數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-136">The expression evaluator provides the following string functions.</span></span>  
  
|<span data-ttu-id="fb8c7-137">函式</span><span class="sxs-lookup"><span data-stu-id="fb8c7-137">Function</span></span>|<span data-ttu-id="fb8c7-138">描述</span><span class="sxs-lookup"><span data-stu-id="fb8c7-138">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="fb8c7-139">CODEPOINT &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-139">CODEPOINT &#40;SSIS Expression&#41;</span></span>](codepoint-ssis-expression.md)|<span data-ttu-id="fb8c7-140">傳回字元運算式最左邊字元的 Unicode 字碼值。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-140">Returns the Unicode code value of the leftmost character of a character expression.</span></span>|  
|[<span data-ttu-id="fb8c7-141">FINDSTRING &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-141">FINDSTRING &#40;SSIS Expression&#41;</span></span>](findstring-ssis-expression.md)|<span data-ttu-id="fb8c7-142">傳回運算式中，所指定字元字串出現位置的以 1 為基底的索引。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-142">Returns the one-based index of the specified occurrence of a character string within an expression.</span></span>|  
|[<span data-ttu-id="fb8c7-143">HEX &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-143">HEX &#40;SSIS Expression&#41;</span></span>](hex-ssis-expression.md)|<span data-ttu-id="fb8c7-144">傳回代表整數的十六進位值的字串。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-144">Returns a string representing the hexadecimal value of an integer.</span></span>|  
|[<span data-ttu-id="fb8c7-145">LEN &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-145">LEN &#40;SSIS Expression&#41;</span></span>](len-ssis-expression.md)|<span data-ttu-id="fb8c7-146">傳回字元運算式中的字元數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-146">Returns the number of characters in a character expression.</span></span>|  
|[<span data-ttu-id="fb8c7-147">LEFT &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-147">LEFT &#40;SSIS Expression&#41;</span></span>](left-ssis-expression.md)|<span data-ttu-id="fb8c7-148">傳回來自給定字元運算式最左邊部分的指定字元數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-148">Returns the specified number of characters from the leftmost portion of the given character expression.</span></span>|  
|[<span data-ttu-id="fb8c7-149">LOWER &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-149">LOWER &#40;SSIS Expression&#41;</span></span>](lower-ssis-expression.md)|<span data-ttu-id="fb8c7-150">傳回將大寫字元轉換為小寫字元之後的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-150">Returns a character expression after converting uppercase characters to lowercase characters.</span></span>|  
|[<span data-ttu-id="fb8c7-151">LTRIM &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-151">LTRIM &#40;SSIS Expression&#41;</span></span>](trim-ssis-expression.md)|<span data-ttu-id="fb8c7-152">傳回移除開頭空白之後的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-152">Returns a character expression after removing leading spaces.</span></span>|  
|[<span data-ttu-id="fb8c7-153">REPLACE &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-153">REPLACE &#40;SSIS Expression&#41;</span></span>](replace-ssis-expression.md)|<span data-ttu-id="fb8c7-154">以不同的字串或空白字串取代運算式中的字串後，傳回字元運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-154">Returns a character expression after replacing a string within the expression with either a different string or an empty string.</span></span>|  
|[<span data-ttu-id="fb8c7-155">REPLICATE &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-155">REPLICATE &#40;SSIS Expression&#41;</span></span>](replicate-ssis-expression.md)|<span data-ttu-id="fb8c7-156">傳回重複了指定次數的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-156">Returns a character expression, replicated a specified number of times.</span></span>|  
|[<span data-ttu-id="fb8c7-157">REVERSE &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-157">REVERSE &#40;SSIS Expression&#41;</span></span>](reverse-ssis-expression.md)|<span data-ttu-id="fb8c7-158">傳回反向順序的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-158">Returns a character expression in reverse order.</span></span>|  
|[<span data-ttu-id="fb8c7-159">RIGHT &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-159">RIGHT &#40;SSIS Expression&#41;</span></span>](right-ssis-expression.md)|<span data-ttu-id="fb8c7-160">傳回來自給定字元運算式最右邊部分的指定字元數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-160">Returns the specified number of characters from the rightmost portion of the given character expression.</span></span>|  
|[<span data-ttu-id="fb8c7-161">RTRIM &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-161">RTRIM &#40;SSIS Expression&#41;</span></span>](rtrim-ssis-expression.md)|<span data-ttu-id="fb8c7-162">傳回移除尾端空白之後的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-162">Returns a character expression after removing trailing spaces.</span></span>|  
|[<span data-ttu-id="fb8c7-163">SUBSTRING &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-163">SUBSTRING &#40;SSIS Expression&#41;</span></span>](substring-ssis-expression.md)|<span data-ttu-id="fb8c7-164">傳回部份字元運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-164">Returns a part of a character expression.</span></span>|  
|[<span data-ttu-id="fb8c7-165">TRIM &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-165">TRIM &#40;SSIS Expression&#41;</span></span>](trim-ssis-expression.md)|<span data-ttu-id="fb8c7-166">傳回移除開頭和尾端空白之後的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-166">Returns a character expression after removing leading and trailing spaces.</span></span>|  
|[<span data-ttu-id="fb8c7-167">UPPER &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-167">UPPER &#40;SSIS Expression&#41;</span></span>](upper-ssis-expression.md)|<span data-ttu-id="fb8c7-168">傳回小寫字元轉換為大寫字元之後的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-168">Returns a character expression after converting lowercase characters to uppercase characters.</span></span>|  
  
 <span data-ttu-id="fb8c7-169">運算式評估工具提供下列日期和時間函數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-169">The expression evaluator provides the following date and time functions.</span></span>  
  
|<span data-ttu-id="fb8c7-170">函式</span><span class="sxs-lookup"><span data-stu-id="fb8c7-170">Function</span></span>|<span data-ttu-id="fb8c7-171">描述</span><span class="sxs-lookup"><span data-stu-id="fb8c7-171">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="fb8c7-172">DATEADD &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-172">DATEADD &#40;SSIS Expression&#41;</span></span>](dateadd-ssis-expression.md)|<span data-ttu-id="fb8c7-173">藉由將日期或時間間隔加入至指定的日期，傳回新的 DT_DBTIMESTAMP 值。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-173">Returns a new DT_DBTIMESTAMP value by adding a date or time interval to a specified date.</span></span>|  
|[<span data-ttu-id="fb8c7-174">DATEDIFF &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-174">DATEDIFF &#40;SSIS Expression&#41;</span></span>](datediff-ssis-expression.md)|<span data-ttu-id="fb8c7-175">傳回跨越兩個指定日期的日期和時間界線數目。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-175">Returns the number of date and time boundaries crossed between two specified dates.</span></span>|  
|[<span data-ttu-id="fb8c7-176">DATEPART &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-176">DATEPART &#40;SSIS Expression&#41;</span></span>](datepart-ssis-expression.md)|<span data-ttu-id="fb8c7-177">傳回代表日期之日期部分的整數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-177">Returns an integer representing a datepart of a date.</span></span>|  
|[<span data-ttu-id="fb8c7-178">DAY &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-178">DAY &#40;SSIS Expression&#41;</span></span>](day-ssis-expression.md)|<span data-ttu-id="fb8c7-179">傳回代表指定日期中日部份的整數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-179">Returns an integer that represents the day of the specified date.</span></span>|  
|[<span data-ttu-id="fb8c7-180">GETDATE &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-180">GETDATE &#40;SSIS Expression&#41;</span></span>](getdate-ssis-expression.md)|<span data-ttu-id="fb8c7-181">傳回系統目前的日期。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-181">Returns the current date of the system.</span></span>|  
|[<span data-ttu-id="fb8c7-182">GETUTCDATE &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-182">GETUTCDATE &#40;SSIS Expression&#41;</span></span>](getutcdate-ssis-expression.md)|<span data-ttu-id="fb8c7-183">傳回以 UTC 時間 (Universal Time Coordinate 或 Greenwich Mean Time) 表示的系統目前日期。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-183">Returns the current date of the system in UTC time (Universal Time Coordinate or Greenwich Mean Time).</span></span>|  
|[<span data-ttu-id="fb8c7-184">MONTH &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-184">MONTH &#40;SSIS Expression&#41;</span></span>](month-ssis-expression.md)|<span data-ttu-id="fb8c7-185">傳回代表指定日期中月份的整數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-185">Returns an integer that represents the month of the specified date.</span></span>|  
|[<span data-ttu-id="fb8c7-186">YEAR &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-186">YEAR &#40;SSIS Expression&#41;</span></span>](year-ssis-expression.md)|<span data-ttu-id="fb8c7-187">傳回代表指定日期中年份的整數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-187">Returns an integer that represents the year of the specified date.</span></span>|  
  
 <span data-ttu-id="fb8c7-188">運算式評估工具提供下列 Null 函數。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-188">The expression evaluator provides the following null functions.</span></span>  
  
|<span data-ttu-id="fb8c7-189">函式</span><span class="sxs-lookup"><span data-stu-id="fb8c7-189">Function</span></span>|<span data-ttu-id="fb8c7-190">描述</span><span class="sxs-lookup"><span data-stu-id="fb8c7-190">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="fb8c7-191">ISNULL &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-191">ISNULL &#40;SSIS Expression&#41;</span></span>](null-ssis-expression.md)|<span data-ttu-id="fb8c7-192">依據運算式是否為 Null 來傳回布林結果。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-192">Returns a Boolean result based on whether an expression is null.</span></span>|  
|[<span data-ttu-id="fb8c7-193">NULL &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fb8c7-193">NULL &#40;SSIS Expression&#41;</span></span>](null-ssis-expression.md)|<span data-ttu-id="fb8c7-194">傳回所要求資料類型的 Null 值。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-194">Returns a null value of a requested data type.</span></span>|  
  
 <span data-ttu-id="fb8c7-195">運算式名稱會以大寫字元顯示，但運算式名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-195">Expression names are shown in uppercase characters, but expression names are not case-sensitive.</span></span> <span data-ttu-id="fb8c7-196">例如，使用「null」與使用「NULL」的功能相同。</span><span class="sxs-lookup"><span data-stu-id="fb8c7-196">For example, using "null" works as well as using "NULL".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb8c7-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fb8c7-197">See Also</span></span>  
 <span data-ttu-id="fb8c7-198">[運算子 &#40;SSIS 運算式&#41;](operators-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="fb8c7-198">[Operators &#40;SSIS Expression&#41;](operators-ssis-expression.md) </span></span>  
 <span data-ttu-id="fb8c7-199">[進階 Integration Services 運算式範例](examples-of-advanced-integration-services-expressions.md) </span><span class="sxs-lookup"><span data-stu-id="fb8c7-199">[Examples of Advanced Integration Services Expressions](examples-of-advanced-integration-services-expressions.md) </span></span>  
 [<span data-ttu-id="fb8c7-200">Integration Services &#40;SSIS&#41; 運算式</span><span class="sxs-lookup"><span data-stu-id="fb8c7-200">Integration Services &#40;SSIS&#41; Expressions</span></span>](integration-services-ssis-expressions.md)  
  
  
