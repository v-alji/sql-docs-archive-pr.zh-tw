---
title: YEAR (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], YEAR
- YEAR function
ms.assetid: 9d88dead-ace8-44b9-b8e2-916c1842e155
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 181375d489fbf7abf0718386efacf4167ba555d7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598501"
---
# <a name="year-ssis-expression"></a><span data-ttu-id="43f08-102">YEAR (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="43f08-102">YEAR (SSIS Expression)</span></span>
  <span data-ttu-id="43f08-103">傳回代表日期之年份部分的整數。</span><span class="sxs-lookup"><span data-stu-id="43f08-103">Returns an integer that represents the year datepart of a date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43f08-104">語法</span><span class="sxs-lookup"><span data-stu-id="43f08-104">Syntax</span></span>  
  
```  
  
YEAR(date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="43f08-105">引數</span><span class="sxs-lookup"><span data-stu-id="43f08-105">Arguments</span></span>  
 <span data-ttu-id="43f08-106">*date*</span><span class="sxs-lookup"><span data-stu-id="43f08-106">*date*</span></span>  
 <span data-ttu-id="43f08-107">使用任何日期格式的日期。</span><span class="sxs-lookup"><span data-stu-id="43f08-107">Is a date in any date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="43f08-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="43f08-108">Result Types</span></span>  
 <span data-ttu-id="43f08-109">DT_I4</span><span class="sxs-lookup"><span data-stu-id="43f08-109">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="43f08-110">備註</span><span class="sxs-lookup"><span data-stu-id="43f08-110">Remarks</span></span>  
 <span data-ttu-id="43f08-111">如果引數為 Null，則 YEAR 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="43f08-111">YEAR returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="43f08-112">日期常值必須明確轉換為日期資料類型之一。</span><span class="sxs-lookup"><span data-stu-id="43f08-112">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="43f08-113">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="43f08-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="43f08-114">當日期常值明確轉換成以下其中一個日期資料類型時，此運算式將會驗證失敗：DT_DBTIMESTAMPOFFSET 和 DT_DBTIMESTAMP2。</span><span class="sxs-lookup"><span data-stu-id="43f08-114">The expression fails to validate when a date literal is explicitly cast to one of these date data types: DT_DBTIMESTAMPOFFSET and DT_DBTIMESTAMP2.</span></span>  
  
 <span data-ttu-id="43f08-115">使用 YEAR 函數較為簡潔，但相當於使用 DATEPART("Year", date) 函數。</span><span class="sxs-lookup"><span data-stu-id="43f08-115">Using the YEAR function is briefer but equivalent to using the DATEPART("Year", date) function.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="43f08-116">運算式範例</span><span class="sxs-lookup"><span data-stu-id="43f08-116">Expression Examples</span></span>  
 <span data-ttu-id="43f08-117">這個範例會傳回日期常值的年數。</span><span class="sxs-lookup"><span data-stu-id="43f08-117">This example returns the number of the year in a date literal.</span></span> <span data-ttu-id="43f08-118">如果日期格式為 mm/dd/yyyy，則這個範例會傳回「2002」。</span><span class="sxs-lookup"><span data-stu-id="43f08-118">If the date is in mm/dd/yyyy format, this example returns "2002".</span></span>  
  
```  
YEAR((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 <span data-ttu-id="43f08-119">這個範例會傳回代表 **ModifiedDate** 資料行中年份的整數。</span><span class="sxs-lookup"><span data-stu-id="43f08-119">This example returns the integer that represents the year in the **ModifiedDate** column.</span></span>  
  
```  
YEAR(ModifiedDate)  
```  
  
 <span data-ttu-id="43f08-120">這個範例會傳回代表目前日期之年份的整數。</span><span class="sxs-lookup"><span data-stu-id="43f08-120">This example returns the integer that represents the year of the current date.</span></span>  
  
```  
YEAR(GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="43f08-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="43f08-121">See Also</span></span>  
 <span data-ttu-id="43f08-122">[DATEADD &#40;SSIS 運算式&#41;](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="43f08-122">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="43f08-123">[DATEDIFF &#40;SSIS 運算式&#41;](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="43f08-123">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="43f08-124">[DATEPART &#40;SSIS 運算式&#41;](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="43f08-124">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="43f08-125">[DAY &#40;SSIS 運算式&#41;](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="43f08-125">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="43f08-126">[MONTH &#40;SSIS 運算式&#41;](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="43f08-126">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 [<span data-ttu-id="43f08-127">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="43f08-127">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
