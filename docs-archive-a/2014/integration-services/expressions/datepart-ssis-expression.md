---
title: DATEPART (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], DATEPART
- DATEPART function
ms.assetid: 3e590094-fc49-4144-805f-fdc1bf2fe509
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 8aed7146c74c6738ba979f422bd65b7e1b539e15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700063"
---
# <a name="datepart-ssis-expression"></a><span data-ttu-id="db5ce-102">DATEPART (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="db5ce-102">DATEPART (SSIS Expression)</span></span>
  <span data-ttu-id="db5ce-103">傳回代表日期之日期部分的整數。</span><span class="sxs-lookup"><span data-stu-id="db5ce-103">Returns an integer representing a datepart of a date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db5ce-104">語法</span><span class="sxs-lookup"><span data-stu-id="db5ce-104">Syntax</span></span>  
  
```  
  
DATEPART(datepart, date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="db5ce-105">引數</span><span class="sxs-lookup"><span data-stu-id="db5ce-105">Arguments</span></span>  
 <span data-ttu-id="db5ce-106">*datepart*</span><span class="sxs-lookup"><span data-stu-id="db5ce-106">*datepart*</span></span>  
 <span data-ttu-id="db5ce-107">這是指定日期中哪一個部分要傳回新值的參數。</span><span class="sxs-lookup"><span data-stu-id="db5ce-107">Is the parameter that specifies for which part of the date to return a new value.</span></span>  
  
 <span data-ttu-id="db5ce-108">*date*</span><span class="sxs-lookup"><span data-stu-id="db5ce-108">*date*</span></span>  
 <span data-ttu-id="db5ce-109">傳回有效日期或日期格式字串的運算式。</span><span class="sxs-lookup"><span data-stu-id="db5ce-109">Is an expression that returns a valid date or a string in date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="db5ce-110">結果類型</span><span class="sxs-lookup"><span data-stu-id="db5ce-110">Result Types</span></span>  
 <span data-ttu-id="db5ce-111">DT_I4</span><span class="sxs-lookup"><span data-stu-id="db5ce-111">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db5ce-112">備註</span><span class="sxs-lookup"><span data-stu-id="db5ce-112">Remarks</span></span>  
 <span data-ttu-id="db5ce-113">如果引數為 Null，則 DATEPART 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="db5ce-113">DATEPART returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="db5ce-114">日期常值必須明確轉換為日期資料類型之一。</span><span class="sxs-lookup"><span data-stu-id="db5ce-114">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="db5ce-115">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="db5ce-115">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="db5ce-116">下表列出運算式評估工具所辨識的日期部份與縮寫。</span><span class="sxs-lookup"><span data-stu-id="db5ce-116">The following table lists the dateparts and abbreviations recognized by the expression evaluator.</span></span> <span data-ttu-id="db5ce-117">日期部份的名稱不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="db5ce-117">Datepart names are not case sensitive.</span></span>  
  
|<span data-ttu-id="db5ce-118">日期部份</span><span class="sxs-lookup"><span data-stu-id="db5ce-118">Datepart</span></span>|<span data-ttu-id="db5ce-119">縮寫</span><span class="sxs-lookup"><span data-stu-id="db5ce-119">Abbreviations</span></span>|  
|--------------|-------------------|  
|<span data-ttu-id="db5ce-120">Year</span><span class="sxs-lookup"><span data-stu-id="db5ce-120">Year</span></span>|<span data-ttu-id="db5ce-121">yy, yyyy</span><span class="sxs-lookup"><span data-stu-id="db5ce-121">yy, yyyy</span></span>|  
|<span data-ttu-id="db5ce-122">Quarter</span><span class="sxs-lookup"><span data-stu-id="db5ce-122">Quarter</span></span>|<span data-ttu-id="db5ce-123">qq, q</span><span class="sxs-lookup"><span data-stu-id="db5ce-123">qq, q</span></span>|  
|<span data-ttu-id="db5ce-124">Month</span><span class="sxs-lookup"><span data-stu-id="db5ce-124">Month</span></span>|<span data-ttu-id="db5ce-125">mm, m</span><span class="sxs-lookup"><span data-stu-id="db5ce-125">mm, m</span></span>|  
|<span data-ttu-id="db5ce-126">Dayofyear</span><span class="sxs-lookup"><span data-stu-id="db5ce-126">Dayofyear</span></span>|<span data-ttu-id="db5ce-127">dy, y</span><span class="sxs-lookup"><span data-stu-id="db5ce-127">dy, y</span></span>|  
|<span data-ttu-id="db5ce-128">Day</span><span class="sxs-lookup"><span data-stu-id="db5ce-128">Day</span></span>|<span data-ttu-id="db5ce-129">dd, d</span><span class="sxs-lookup"><span data-stu-id="db5ce-129">dd, d</span></span>|  
|<span data-ttu-id="db5ce-130">週</span><span class="sxs-lookup"><span data-stu-id="db5ce-130">Week</span></span>|<span data-ttu-id="db5ce-131">wk, ww</span><span class="sxs-lookup"><span data-stu-id="db5ce-131">wk, ww</span></span>|  
|<span data-ttu-id="db5ce-132">Weekday</span><span class="sxs-lookup"><span data-stu-id="db5ce-132">Weekday</span></span>|<span data-ttu-id="db5ce-133">dw</span><span class="sxs-lookup"><span data-stu-id="db5ce-133">dw</span></span>|  
|<span data-ttu-id="db5ce-134">Hour</span><span class="sxs-lookup"><span data-stu-id="db5ce-134">Hour</span></span>|<span data-ttu-id="db5ce-135">Hh</span><span class="sxs-lookup"><span data-stu-id="db5ce-135">Hh</span></span>|  
|<span data-ttu-id="db5ce-136">Minute</span><span class="sxs-lookup"><span data-stu-id="db5ce-136">Minute</span></span>|<span data-ttu-id="db5ce-137">mi, n</span><span class="sxs-lookup"><span data-stu-id="db5ce-137">mi, n</span></span>|  
|<span data-ttu-id="db5ce-138">Second</span><span class="sxs-lookup"><span data-stu-id="db5ce-138">Second</span></span>|<span data-ttu-id="db5ce-139">ss, s</span><span class="sxs-lookup"><span data-stu-id="db5ce-139">ss, s</span></span>|  
|<span data-ttu-id="db5ce-140">Millisecond</span><span class="sxs-lookup"><span data-stu-id="db5ce-140">Millisecond</span></span>|<span data-ttu-id="db5ce-141">Ms</span><span class="sxs-lookup"><span data-stu-id="db5ce-141">Ms</span></span>|  
  
## <a name="ssis-expression-examples"></a><span data-ttu-id="db5ce-142">SSIS 運算式範例</span><span class="sxs-lookup"><span data-stu-id="db5ce-142">SSIS Expression Examples</span></span>  
 <span data-ttu-id="db5ce-143">這個範例會傳回在日期常值中代表月份的整數。</span><span class="sxs-lookup"><span data-stu-id="db5ce-143">This example returns the integer that represents the month in a date literal.</span></span> <span data-ttu-id="db5ce-144">如果日期格式為 mm/dd/yyyy"，則這個範例會傳回 11。</span><span class="sxs-lookup"><span data-stu-id="db5ce-144">If the date is in mm/dd/yyyy" format, this example returns 11.</span></span>  
  
```  
DATEPART("month", (DT_DBTIMESTAMP)"11/04/2002")  
```  
  
 <span data-ttu-id="db5ce-145">這個範例會傳回 **ModifiedDate** 資料行中，代表天的整數。</span><span class="sxs-lookup"><span data-stu-id="db5ce-145">This example returns the integer that represents the day in the **ModifiedDate** column.</span></span>  
  
```  
DATEPART("dd", ModifiedDate)  
```  
  
 <span data-ttu-id="db5ce-146">這個範例會傳回代表目前日期之年份的整數。</span><span class="sxs-lookup"><span data-stu-id="db5ce-146">This example returns the integer that represents the year of the current date.</span></span>  
  
```  
DATEPART("yy",GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="db5ce-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db5ce-147">See Also</span></span>  
 <span data-ttu-id="db5ce-148">[DATEADD &#40;SSIS 運算式&#41;](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="db5ce-148">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="db5ce-149">[DATEDIFF &#40;SSIS 運算式&#41;](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="db5ce-149">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="db5ce-150">[DAY &#40;SSIS 運算式&#41;](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="db5ce-150">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="db5ce-151">[MONTH &#40;SSIS 運算式&#41;](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="db5ce-151">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 <span data-ttu-id="db5ce-152">[YEAR &#40;SSIS 運算式&#41;](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="db5ce-152">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="db5ce-153">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="db5ce-153">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
