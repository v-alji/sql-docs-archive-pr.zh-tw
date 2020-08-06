---
title: MONTH (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- dates [Integration Services], MONTH
- MONTH function
ms.assetid: b5a47a11-c2ef-49bd-bd70-235632ff7bf6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: d1f56906b4d25f2ba01f54fbdbc404d2c9ae4704
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595199"
---
# <a name="month-ssis-expression"></a><span data-ttu-id="9b6c3-102">MONTH (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="9b6c3-102">MONTH (SSIS Expression)</span></span>
  <span data-ttu-id="9b6c3-103">傳回代表日期之月份部分的整數。</span><span class="sxs-lookup"><span data-stu-id="9b6c3-103">Returns an integer that represents the month datepart of a date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b6c3-104">語法</span><span class="sxs-lookup"><span data-stu-id="9b6c3-104">Syntax</span></span>  
  
```  
  
MONTH(date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="9b6c3-105">引數</span><span class="sxs-lookup"><span data-stu-id="9b6c3-105">Arguments</span></span>  
 <span data-ttu-id="9b6c3-106">*date*</span><span class="sxs-lookup"><span data-stu-id="9b6c3-106">*date*</span></span>  
 <span data-ttu-id="9b6c3-107">使用任何日期格式的日期。</span><span class="sxs-lookup"><span data-stu-id="9b6c3-107">Is a date in any date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="9b6c3-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="9b6c3-108">Result Types</span></span>  
 <span data-ttu-id="9b6c3-109">DT_I4</span><span class="sxs-lookup"><span data-stu-id="9b6c3-109">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b6c3-110">備註</span><span class="sxs-lookup"><span data-stu-id="9b6c3-110">Remarks</span></span>  
 <span data-ttu-id="9b6c3-111">如果引數為 Null，則 MONTH 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="9b6c3-111">MONTH returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="9b6c3-112">日期常值必須明確轉換為日期資料類型之一。</span><span class="sxs-lookup"><span data-stu-id="9b6c3-112">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="9b6c3-113">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="9b6c3-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9b6c3-114">當日期常值明確轉換成以下其中一個日期資料類型時，此運算式將會驗證失敗：DT_DBTIMESTAMPOFFSET 和 DT_DBTIMESTAMP2。</span><span class="sxs-lookup"><span data-stu-id="9b6c3-114">The expression fails to validate when a date literal is explicitly cast to one of these date data types: DT_DBTIMESTAMPOFFSET and DT_DBTIMESTAMP2.</span></span>  
  
 <span data-ttu-id="9b6c3-115">使用 MONTH 函數較為簡潔，但相當於使用 DATEPART("Month", date)。</span><span class="sxs-lookup"><span data-stu-id="9b6c3-115">Using the MONTH function is briefer but equivalent to using DATEPART("Month", date).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="9b6c3-116">運算式範例</span><span class="sxs-lookup"><span data-stu-id="9b6c3-116">Expression Examples</span></span>  
 <span data-ttu-id="9b6c3-117">這個範例會傳回日期常值的月數。</span><span class="sxs-lookup"><span data-stu-id="9b6c3-117">This example returns the number of the month in a date literal.</span></span> <span data-ttu-id="9b6c3-118">如果日期格式為「mm/dd/yyyy」，則這個範例會傳回 11。</span><span class="sxs-lookup"><span data-stu-id="9b6c3-118">If the date is in "mm/dd/yyyy" format, this example returns 11.</span></span>  
  
```  
MONTH((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 <span data-ttu-id="9b6c3-119">這個範例會傳回代表 **ModifiedDate** 資料行中月份的整數。</span><span class="sxs-lookup"><span data-stu-id="9b6c3-119">This example returns the integer that represents the month in the **ModifiedDate** column.</span></span>  
  
```  
MONTH(ModifiedDate)  
```  
  
 <span data-ttu-id="9b6c3-120">這個範例會傳回代表目前日期的月份的整數。</span><span class="sxs-lookup"><span data-stu-id="9b6c3-120">This example returns the integer that represents the month of the current date.</span></span>  
  
```  
MONTH(GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="9b6c3-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b6c3-121">See Also</span></span>  
 <span data-ttu-id="9b6c3-122">[DATEADD &#40;SSIS 運算式&#41;](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="9b6c3-122">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="9b6c3-123">[DATEDIFF &#40;SSIS 運算式&#41;](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="9b6c3-123">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="9b6c3-124">[DATEPART &#40;SSIS 運算式&#41;](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="9b6c3-124">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="9b6c3-125">[DAY &#40;SSIS 運算式&#41;](day-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="9b6c3-125">[DAY &#40;SSIS Expression&#41;](day-ssis-expression.md) </span></span>  
 <span data-ttu-id="9b6c3-126">[YEAR &#40;SSIS 運算式&#41;](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="9b6c3-126">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="9b6c3-127">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="9b6c3-127">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
