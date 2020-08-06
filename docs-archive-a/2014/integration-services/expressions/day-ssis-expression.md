---
title: DAY (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- DAY function
- dates [Integration Services], DAY
ms.assetid: d8447187-49df-45b7-a98e-142ad44fd3e2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1b7acac3f3949cbbd07adbe6382ea3d875f94cb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700057"
---
# <a name="day-ssis-expression"></a><span data-ttu-id="d9670-102">DAY (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="d9670-102">DAY (SSIS Expression)</span></span>
  <span data-ttu-id="d9670-103">傳回代表日期之日部分的整數。</span><span class="sxs-lookup"><span data-stu-id="d9670-103">Returns an integer that represents the day datepart of a date.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9670-104">語法</span><span class="sxs-lookup"><span data-stu-id="d9670-104">Syntax</span></span>  
  
```  
  
DAY(date)  
```  
  
## <a name="arguments"></a><span data-ttu-id="d9670-105">引數</span><span class="sxs-lookup"><span data-stu-id="d9670-105">Arguments</span></span>  
 <span data-ttu-id="d9670-106">*date*</span><span class="sxs-lookup"><span data-stu-id="d9670-106">*date*</span></span>  
 <span data-ttu-id="d9670-107">傳回有效日期或日期格式字串的運算式。</span><span class="sxs-lookup"><span data-stu-id="d9670-107">Is an expression that returns a valid date or a string in date format.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="d9670-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="d9670-108">Result Types</span></span>  
 <span data-ttu-id="d9670-109">DT_I4</span><span class="sxs-lookup"><span data-stu-id="d9670-109">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9670-110">備註</span><span class="sxs-lookup"><span data-stu-id="d9670-110">Remarks</span></span>  
 <span data-ttu-id="d9670-111">如果引數為 Null，則 DAY 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="d9670-111">DAY returns a null result if the argument is null.</span></span>  
  
 <span data-ttu-id="d9670-112">日期常值必須明確轉換為日期資料類型之一。</span><span class="sxs-lookup"><span data-stu-id="d9670-112">A date literal must be explicitly cast to one of the date data types.</span></span> <span data-ttu-id="d9670-113">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="d9670-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d9670-114">當日期常值明確轉換成以下其中一個日期資料類型時，此運算式將會驗證失敗：DT_DBTIMESTAMPOFFSET 和 DT_DBTIMESTAMP2。</span><span class="sxs-lookup"><span data-stu-id="d9670-114">The expression fails to validate when a date literal is explicitly cast to one of these date data types: DT_DBTIMESTAMPOFFSET and DT_DBTIMESTAMP2.</span></span>  
  
 <span data-ttu-id="d9670-115">使用 DAY 函數較為簡潔，但相當於使用 DATEPART("Day", date)。</span><span class="sxs-lookup"><span data-stu-id="d9670-115">Using the DAY function is briefer but equivalent to using DATEPART("Day", date).</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="d9670-116">運算式範例</span><span class="sxs-lookup"><span data-stu-id="d9670-116">Expression Examples</span></span>  
 <span data-ttu-id="d9670-117">這個範例會傳回日期常值的日數。</span><span class="sxs-lookup"><span data-stu-id="d9670-117">This example returns the number of the day in a date literal.</span></span> <span data-ttu-id="d9670-118">如果日期格式為「mm/dd/yyyy」，則這個範例會傳回 23。</span><span class="sxs-lookup"><span data-stu-id="d9670-118">If the date format is in "mm/dd/yyyy" format, this example returns 23.</span></span>  
  
```  
DAY((DT_DBTIMESTAMP)"11/23/2002")  
```  
  
 <span data-ttu-id="d9670-119">這個範例會傳回 **ModifiedDate** 資料行中，代表天的整數。</span><span class="sxs-lookup"><span data-stu-id="d9670-119">This example returns the integer that represents the day in the **ModifiedDate** column.</span></span>  
  
```  
DAY(ModifiedDate)  
```  
  
 <span data-ttu-id="d9670-120">這個範例會傳回代表目前日期之日子的整數。</span><span class="sxs-lookup"><span data-stu-id="d9670-120">This example returns the integer that represents the day of the current date.</span></span>  
  
```  
DAY(GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9670-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d9670-121">See Also</span></span>  
 <span data-ttu-id="d9670-122">[DATEADD &#40;SSIS 運算式&#41;](dateadd-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d9670-122">[DATEADD &#40;SSIS Expression&#41;](dateadd-ssis-expression.md) </span></span>  
 <span data-ttu-id="d9670-123">[DATEDIFF &#40;SSIS 運算式&#41;](datediff-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d9670-123">[DATEDIFF &#40;SSIS Expression&#41;](datediff-ssis-expression.md) </span></span>  
 <span data-ttu-id="d9670-124">[DATEPART &#40;SSIS 運算式&#41;](datepart-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d9670-124">[DATEPART &#40;SSIS Expression&#41;](datepart-ssis-expression.md) </span></span>  
 <span data-ttu-id="d9670-125">[MONTH &#40;SSIS 運算式&#41;](month-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d9670-125">[MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) </span></span>  
 <span data-ttu-id="d9670-126">[YEAR &#40;SSIS 運算式&#41;](year-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="d9670-126">[YEAR &#40;SSIS Expression&#41;](year-ssis-expression.md) </span></span>  
 [<span data-ttu-id="d9670-127">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="d9670-127">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
