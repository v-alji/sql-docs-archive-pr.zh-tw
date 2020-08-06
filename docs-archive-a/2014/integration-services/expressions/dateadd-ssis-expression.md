---
title: DATEADD (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEADD
- dates [Integration Services]
- DATEADD function
ms.assetid: fa5c37b1-2ddc-4857-8f8e-f6d5643b654f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9feb288318bdf9705928cb930f175f5c170c384e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705334"
---
# <a name="dateadd-ssis-expression"></a><span data-ttu-id="0bc2b-102">DATEADD (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="0bc2b-102">DATEADD (SSIS Expression)</span></span>
  <span data-ttu-id="0bc2b-103">在日期的指定之日期部分加上代表日期或時間間隔的數字之後，傳回新的 DT_DBTIMESTAMP 值。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-103">Returns a new DT_DBTIMESTAMP value after adding a number that represents a date or time interval to the specified datepart in a date.</span></span> <span data-ttu-id="0bc2b-104">number 參數必須評估為整數，date 參數必須評估為有效的日期。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-104">The number parameter must evaluate to an integer, and the date parameter must evaluate to a valid date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bc2b-105">語法</span><span class="sxs-lookup"><span data-stu-id="0bc2b-105">Syntax</span></span>  
  
```  
  
DATEADD(datepart, number, date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="0bc2b-106">引數</span><span class="sxs-lookup"><span data-stu-id="0bc2b-106">Arguments</span></span>  
 <span data-ttu-id="0bc2b-107">*datepart*</span><span class="sxs-lookup"><span data-stu-id="0bc2b-107">*datepart*</span></span>  
 <span data-ttu-id="0bc2b-108">是指定要加入數字之日期部份的參數。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-108">Is the parameter that specifies which part of the date to add a number to.</span></span>  
  
 <span data-ttu-id="0bc2b-109">*number*</span><span class="sxs-lookup"><span data-stu-id="0bc2b-109">*number*</span></span>  
 <span data-ttu-id="0bc2b-110">這是用來遞增 *datepart*的值。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-110">Is the value used to increment *datepart*.</span></span> <span data-ttu-id="0bc2b-111">值必須是剖析運算式時已知的整數值。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-111">The value must be an integer value that is known when the expression is parsed.</span></span>  
  
 <span data-ttu-id="0bc2b-112">*date*</span><span class="sxs-lookup"><span data-stu-id="0bc2b-112">*date*</span></span>  
 <span data-ttu-id="0bc2b-113">傳回有效日期或日期格式字串的運算式。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-113">Is an expression that returns a valid date or a string in date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="0bc2b-114">結果類型</span><span class="sxs-lookup"><span data-stu-id="0bc2b-114">Result Types</span></span>  
 <span data-ttu-id="0bc2b-115">DT_DBTIMESTAMP</span><span class="sxs-lookup"><span data-stu-id="0bc2b-115">DT_DBTIMESTAMP</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0bc2b-116">備註</span><span class="sxs-lookup"><span data-stu-id="0bc2b-116">Remarks</span></span>  
 <span data-ttu-id="0bc2b-117">下表列出運算式評估工具所辨識的日期部份與縮寫。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-117">The following table lists the dateparts and abbreviations recognized by the expression evaluator.</span></span> <span data-ttu-id="0bc2b-118">日期部份的名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-118">Datepart names are not case sensitive.</span></span>  
  
|<span data-ttu-id="0bc2b-119">日期部份</span><span class="sxs-lookup"><span data-stu-id="0bc2b-119">Datepart</span></span>|<span data-ttu-id="0bc2b-120">縮寫</span><span class="sxs-lookup"><span data-stu-id="0bc2b-120">Abbreviations</span></span>|  
|--------------|-------------------|  
|<span data-ttu-id="0bc2b-121">Year</span><span class="sxs-lookup"><span data-stu-id="0bc2b-121">Year</span></span>|<span data-ttu-id="0bc2b-122">yy, yyyy</span><span class="sxs-lookup"><span data-stu-id="0bc2b-122">yy, yyyy</span></span>|  
|<span data-ttu-id="0bc2b-123">Quarter</span><span class="sxs-lookup"><span data-stu-id="0bc2b-123">Quarter</span></span>|<span data-ttu-id="0bc2b-124">qq, q</span><span class="sxs-lookup"><span data-stu-id="0bc2b-124">qq, q</span></span>|  
|<span data-ttu-id="0bc2b-125">Month</span><span class="sxs-lookup"><span data-stu-id="0bc2b-125">Month</span></span>|<span data-ttu-id="0bc2b-126">mm, m</span><span class="sxs-lookup"><span data-stu-id="0bc2b-126">mm, m</span></span>|  
|<span data-ttu-id="0bc2b-127">Dayofyear</span><span class="sxs-lookup"><span data-stu-id="0bc2b-127">Dayofyear</span></span>|<span data-ttu-id="0bc2b-128">dy, y</span><span class="sxs-lookup"><span data-stu-id="0bc2b-128">dy, y</span></span>|  
|<span data-ttu-id="0bc2b-129">Day</span><span class="sxs-lookup"><span data-stu-id="0bc2b-129">Day</span></span>|<span data-ttu-id="0bc2b-130">dd, d</span><span class="sxs-lookup"><span data-stu-id="0bc2b-130">dd, d</span></span>|  
|<span data-ttu-id="0bc2b-131">週</span><span class="sxs-lookup"><span data-stu-id="0bc2b-131">Week</span></span>|<span data-ttu-id="0bc2b-132">wk, ww</span><span class="sxs-lookup"><span data-stu-id="0bc2b-132">wk, ww</span></span>|  
|<span data-ttu-id="0bc2b-133">Weekday</span><span class="sxs-lookup"><span data-stu-id="0bc2b-133">Weekday</span></span>|<span data-ttu-id="0bc2b-134">dw, w</span><span class="sxs-lookup"><span data-stu-id="0bc2b-134">dw, w</span></span>|  
|<span data-ttu-id="0bc2b-135">Hour</span><span class="sxs-lookup"><span data-stu-id="0bc2b-135">Hour</span></span>|<span data-ttu-id="0bc2b-136">Hh</span><span class="sxs-lookup"><span data-stu-id="0bc2b-136">Hh</span></span>|  
|<span data-ttu-id="0bc2b-137">Minute</span><span class="sxs-lookup"><span data-stu-id="0bc2b-137">Minute</span></span>|<span data-ttu-id="0bc2b-138">mi, n</span><span class="sxs-lookup"><span data-stu-id="0bc2b-138">mi, n</span></span>|  
|<span data-ttu-id="0bc2b-139">Second</span><span class="sxs-lookup"><span data-stu-id="0bc2b-139">Second</span></span>|<span data-ttu-id="0bc2b-140">ss, s</span><span class="sxs-lookup"><span data-stu-id="0bc2b-140">ss, s</span></span>|  
|<span data-ttu-id="0bc2b-141">Millisecond</span><span class="sxs-lookup"><span data-stu-id="0bc2b-141">Millisecond</span></span>|<span data-ttu-id="0bc2b-142">Ms</span><span class="sxs-lookup"><span data-stu-id="0bc2b-142">Ms</span></span>|  
  
 <span data-ttu-id="0bc2b-143">*number* 引數必須在剖析運算式時提供。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-143">The *number* argument must be available when the expression is parsed.</span></span> <span data-ttu-id="0bc2b-144">這個引數可以是常數或變數。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-144">The argument can be a constant or a variable.</span></span> <span data-ttu-id="0bc2b-145">您不可使用資料行的值，因為這些值在剖析運算式時並非已知。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-145">You cannot use column values because the values are not known when the expression is parsed.</span></span>  
  
 <span data-ttu-id="0bc2b-146">*datepart* 引數必須加上引號。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-146">The *datepart* argument must be enclosed by quotation marks.</span></span>  
  
 <span data-ttu-id="0bc2b-147">日期常值必須明確轉換為日期資料類型之一。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-147">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="0bc2b-148">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-148">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="0bc2b-149">如果引數為 Null，則 DATEADD 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-149">DATEADD returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="0bc2b-150">如果日期無效、日期或時間單位不是字串，或累加不是靜態整數，則會發生錯誤。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-150">Errors occur if a date is invalid, if the date or time unit is not a string, or if the increment is not a static integer.</span></span>  
  
## <a name="ssis-expression-examples"></a><span data-ttu-id="0bc2b-151">SSIS 運算式範例</span><span class="sxs-lookup"><span data-stu-id="0bc2b-151">SSIS Expression Examples</span></span>  
 <span data-ttu-id="0bc2b-152">此範例會對目前日期加上一個月。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-152">This example adds one month to the current date.</span></span>  
  
```  
DATEADD("Month", 1,GETDATE())  
```  
  
 <span data-ttu-id="0bc2b-153">此範例會對 **ModifiedDate** 資料行中的日期加上 21 天。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-153">This example adds 21 days to the dates in the **ModifiedDate** column.</span></span>  
  
```  
DATEADD("day", 21, ModifiedDate)  
```  
  
 <span data-ttu-id="0bc2b-154">此範例會對常值日期加上 2 年。</span><span class="sxs-lookup"><span data-stu-id="0bc2b-154">This example adds 2 years to a literal date.</span></span>  
  
```  
DATEADD("yyyy", 2, (DT_DBTIMESTAMP)"8/6/2003")  
```  
  
## <a name="see-also"></a><span data-ttu-id="0bc2b-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0bc2b-155">See Also</span></span>  
 <span data-ttu-id="0bc2b-156">[DATEDIFF &#40;SSIS 運算式&#41;](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="0bc2b-156">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="0bc2b-157">[DATEPART &#40;SSIS 運算式&#41;](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="0bc2b-157">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="0bc2b-158">[DAY &#40;SSIS 運算式&#41;](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="0bc2b-158">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="0bc2b-159">[MONTH &#40;SSIS 運算式&#41;](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="0bc2b-159">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 <span data-ttu-id="0bc2b-160">[YEAR &#40;SSIS 運算式&#41;](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="0bc2b-160">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="0bc2b-161">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="0bc2b-161">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
