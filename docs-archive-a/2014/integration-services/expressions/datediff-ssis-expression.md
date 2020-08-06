---
title: DATEDIFF (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- DATEDIFF statement
- dates [Integration Services], DATEDIFF
ms.assetid: 449b327f-47c7-4709-8bc6-4ee9a35cc330
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 33edf2a152f70bb8c5bbd1f69cb87354e099b246
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700069"
---
# <a name="datediff-ssis-expression"></a><span data-ttu-id="311ac-102">DATEDIFF (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="311ac-102">DATEDIFF (SSIS Expression)</span></span>
  <span data-ttu-id="311ac-103">傳回跨越兩個指定日期的日期和時間界線數目。</span><span class="sxs-lookup"><span data-stu-id="311ac-103">Returns the number of date and time boundaries crossed between two specified dates.</span></span> <span data-ttu-id="311ac-104">*datepart* 參數會識別要比較的日期和時間界線。</span><span class="sxs-lookup"><span data-stu-id="311ac-104">The *datepart* parameter identifies which date and time boundaries to compare.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="311ac-105">語法</span><span class="sxs-lookup"><span data-stu-id="311ac-105">Syntax</span></span>  
  
```  
  
DATEDIFF(datepart, startdate, endate)  
```  
  
## <a name="arguments"></a><span data-ttu-id="311ac-106">引數</span><span class="sxs-lookup"><span data-stu-id="311ac-106">Arguments</span></span>  
 <span data-ttu-id="311ac-107">*datepart*</span><span class="sxs-lookup"><span data-stu-id="311ac-107">*datepart*</span></span>  
 <span data-ttu-id="311ac-108">是指定日期中哪一個部分要進行比較和傳回值的參數。</span><span class="sxs-lookup"><span data-stu-id="311ac-108">Is the parameter that specifies which part of the date to compare and return a value for.</span></span>  
  
 <span data-ttu-id="311ac-109">*startdate*</span><span class="sxs-lookup"><span data-stu-id="311ac-109">*startdate*</span></span>  
 <span data-ttu-id="311ac-110">是間隔的開始日期。</span><span class="sxs-lookup"><span data-stu-id="311ac-110">Is the start date of the interval.</span></span>  
  
 <span data-ttu-id="311ac-111">*endate*</span><span class="sxs-lookup"><span data-stu-id="311ac-111">*endate*</span></span>  
 <span data-ttu-id="311ac-112">是間隔的結束日期。</span><span class="sxs-lookup"><span data-stu-id="311ac-112">Is the end date of the interval.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="311ac-113">結果類型</span><span class="sxs-lookup"><span data-stu-id="311ac-113">Result Types</span></span>  
 <span data-ttu-id="311ac-114">DT_I4</span><span class="sxs-lookup"><span data-stu-id="311ac-114">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="311ac-115">備註</span><span class="sxs-lookup"><span data-stu-id="311ac-115">Remarks</span></span>  
 <span data-ttu-id="311ac-116">下表列出運算式評估工具所辨識的日期部份與縮寫。</span><span class="sxs-lookup"><span data-stu-id="311ac-116">The following table lists the dateparts and abbreviations recognized by the expression evaluator.</span></span>  
  
|<span data-ttu-id="311ac-117">日期部份</span><span class="sxs-lookup"><span data-stu-id="311ac-117">Datepart</span></span>|<span data-ttu-id="311ac-118">縮寫</span><span class="sxs-lookup"><span data-stu-id="311ac-118">Abbreviations</span></span>|  
|--------------|-------------------|  
|<span data-ttu-id="311ac-119">Year</span><span class="sxs-lookup"><span data-stu-id="311ac-119">Year</span></span>|<span data-ttu-id="311ac-120">yy, yyyy</span><span class="sxs-lookup"><span data-stu-id="311ac-120">yy, yyyy</span></span>|  
|<span data-ttu-id="311ac-121">Quarter</span><span class="sxs-lookup"><span data-stu-id="311ac-121">Quarter</span></span>|<span data-ttu-id="311ac-122">qq, q</span><span class="sxs-lookup"><span data-stu-id="311ac-122">qq, q</span></span>|  
|<span data-ttu-id="311ac-123">Month</span><span class="sxs-lookup"><span data-stu-id="311ac-123">Month</span></span>|<span data-ttu-id="311ac-124">mm, m</span><span class="sxs-lookup"><span data-stu-id="311ac-124">mm, m</span></span>|  
|<span data-ttu-id="311ac-125">Dayofyear</span><span class="sxs-lookup"><span data-stu-id="311ac-125">Dayofyear</span></span>|<span data-ttu-id="311ac-126">dy, y</span><span class="sxs-lookup"><span data-stu-id="311ac-126">dy, y</span></span>|  
|<span data-ttu-id="311ac-127">Day</span><span class="sxs-lookup"><span data-stu-id="311ac-127">Day</span></span>|<span data-ttu-id="311ac-128">dd, d</span><span class="sxs-lookup"><span data-stu-id="311ac-128">dd, d</span></span>|  
|<span data-ttu-id="311ac-129">週</span><span class="sxs-lookup"><span data-stu-id="311ac-129">Week</span></span>|<span data-ttu-id="311ac-130">wk, ww</span><span class="sxs-lookup"><span data-stu-id="311ac-130">wk, ww</span></span>|  
|<span data-ttu-id="311ac-131">Weekday</span><span class="sxs-lookup"><span data-stu-id="311ac-131">Weekday</span></span>|<span data-ttu-id="311ac-132">dw, w</span><span class="sxs-lookup"><span data-stu-id="311ac-132">dw, w</span></span>|  
|<span data-ttu-id="311ac-133">Hour</span><span class="sxs-lookup"><span data-stu-id="311ac-133">Hour</span></span>|<span data-ttu-id="311ac-134">Hh</span><span class="sxs-lookup"><span data-stu-id="311ac-134">Hh</span></span>|  
|<span data-ttu-id="311ac-135">Minute</span><span class="sxs-lookup"><span data-stu-id="311ac-135">Minute</span></span>|<span data-ttu-id="311ac-136">mi, n</span><span class="sxs-lookup"><span data-stu-id="311ac-136">mi, n</span></span>|  
|<span data-ttu-id="311ac-137">Second</span><span class="sxs-lookup"><span data-stu-id="311ac-137">Second</span></span>|<span data-ttu-id="311ac-138">ss, s</span><span class="sxs-lookup"><span data-stu-id="311ac-138">ss, s</span></span>|  
|<span data-ttu-id="311ac-139">Millisecond</span><span class="sxs-lookup"><span data-stu-id="311ac-139">Millisecond</span></span>|<span data-ttu-id="311ac-140">Ms</span><span class="sxs-lookup"><span data-stu-id="311ac-140">Ms</span></span>|  
  
 <span data-ttu-id="311ac-141">如果任何引數為 Null，則 DATEDIFF 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="311ac-141">DATEDIFF returns a null result if any argument is null.</span></span>  
  
 <span data-ttu-id="311ac-142">日期常值必須明確轉換為日期資料類型之一。</span><span class="sxs-lookup"><span data-stu-id="311ac-142">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="311ac-143">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="311ac-143">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="311ac-144">如果日期無效、日期或時間單位不是字串、開始日期不是日期，或結束日期不是日期，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="311ac-144">An error occurs if a date is not valid, if the date or time unit is not a string, if the start date is not a date, or if the end date is not a date.</span></span>  
  
 <span data-ttu-id="311ac-145">如果結束日期早於開始日期，則函數會傳回負數。</span><span class="sxs-lookup"><span data-stu-id="311ac-145">If the end date is earlier than the start date, the function returns a negative number.</span></span> <span data-ttu-id="311ac-146">如果開始和結束日期相等或落在相同的間隔內，則函數會傳回零。</span><span class="sxs-lookup"><span data-stu-id="311ac-146">If the start and end dates are equal or fall within the same interval, the function returns zero.</span></span>  
  
## <a name="ssis-expression-examples"></a><span data-ttu-id="311ac-147">SSIS 運算式範例</span><span class="sxs-lookup"><span data-stu-id="311ac-147">SSIS Expression Examples</span></span>  
 <span data-ttu-id="311ac-148">此範例會計算兩個日期常值之間的天數。</span><span class="sxs-lookup"><span data-stu-id="311ac-148">This example calculates the number of days between two date literals.</span></span> <span data-ttu-id="311ac-149">如果日期格式為 "mm/dd/yyyy"，則函數會傳回 7。</span><span class="sxs-lookup"><span data-stu-id="311ac-149">If the date is in "mm/dd/yyyy" format, the function returns 7.</span></span>  
  
```  
DATEDIFF("dd", (DT_DBTIMESTAMP)"8/1/2003", (DT_DBTIMESTAMP)"8/8/2003")  
```  
  
 <span data-ttu-id="311ac-150">此範例會傳回日期常值和目前日期之間的月數。</span><span class="sxs-lookup"><span data-stu-id="311ac-150">This example returns the number of months between a date literal and the current date.</span></span>  
  
```  
DATEDIFF("mm", (DT_DBTIMESTAMP)"8/1/2003",GETDATE())  
```  
  
 <span data-ttu-id="311ac-151">此範例會傳回 **ModifiedDate** 資料行中的日期與 **YearEndDate** 變數之間的星期數。</span><span class="sxs-lookup"><span data-stu-id="311ac-151">This example returns the number of weeks between the date in the **ModifiedDate** column and the **YearEndDate** variable.</span></span> <span data-ttu-id="311ac-152">如果**YearEndDate**具有 `date` 資料類型，則不需要明確轉換。</span><span class="sxs-lookup"><span data-stu-id="311ac-152">If **YearEndDate** has a `date` data type, no explicit casting is required.</span></span>  
  
```  
DATEDIFF("Week", ModifiedDate,@YearEndDate)  
```  
  
## <a name="see-also"></a><span data-ttu-id="311ac-153">另請參閱</span><span class="sxs-lookup"><span data-stu-id="311ac-153">See Also</span></span>  
 <span data-ttu-id="311ac-154">[DATEADD &#40;SSIS 運算式&#41;](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="311ac-154">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="311ac-155">[DATEPART &#40;SSIS 運算式&#41;](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="311ac-155">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="311ac-156">[DAY &#40;SSIS 運算式&#41;](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="311ac-156">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="311ac-157">[MONTH &#40;SSIS 運算式&#41;](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="311ac-157">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 <span data-ttu-id="311ac-158">[YEAR &#40;SSIS 運算式&#41;](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="311ac-158">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="311ac-159">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="311ac-159">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
