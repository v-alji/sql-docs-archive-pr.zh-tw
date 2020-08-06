---
title: '! (邏輯 Not) (SSIS 運算式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logical Not (!)
- '! (logical Not)'
ms.assetid: d5c4d1e1-7be4-4d25-bcd9-5b6ddb53b3b3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 1bbf313930575e864f1556952425567fca96db15
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595203"
---
# <a name="-logical-not-ssis-expression"></a><span data-ttu-id="b817d-103">!</span><span class="sxs-lookup"><span data-stu-id="b817d-103">!</span></span> <span data-ttu-id="b817d-104">(邏輯 Not) (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="b817d-104">(Logical Not) (SSIS Expression)</span></span>
  <span data-ttu-id="b817d-105">執行布林運算元的否定運算。</span><span class="sxs-lookup"><span data-stu-id="b817d-105">Negates a Boolean operand.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b817d-106">!</span><span class="sxs-lookup"><span data-stu-id="b817d-106">The !</span></span> <span data-ttu-id="b817d-107">運算子不可搭配其他運算子使用。</span><span class="sxs-lookup"><span data-stu-id="b817d-107">operator cannot be used in conjunction with other operators.</span></span> <span data-ttu-id="b817d-108">例如，您不可以將 !</span><span class="sxs-lookup"><span data-stu-id="b817d-108">For example, you cannot combine the !</span></span> <span data-ttu-id="b817d-109">及 > 運算子結合至 !>。</span><span class="sxs-lookup"><span data-stu-id="b817d-109">and the > operators into the !>.</span></span> <span data-ttu-id="b817d-110">運算子。</span><span class="sxs-lookup"><span data-stu-id="b817d-110">operator.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b817d-111">語法</span><span class="sxs-lookup"><span data-stu-id="b817d-111">Syntax</span></span>  
  
```  
  
!boolean_expression  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="b817d-112">引數</span><span class="sxs-lookup"><span data-stu-id="b817d-112">Arguments</span></span>  
 <span data-ttu-id="b817d-113">*boolean_expression*</span><span class="sxs-lookup"><span data-stu-id="b817d-113">*boolean_expression*</span></span>  
 <span data-ttu-id="b817d-114">是任何評估結果為布林的有效運算式。</span><span class="sxs-lookup"><span data-stu-id="b817d-114">Is any valid expression that evaluates to a Boolean.</span></span> <span data-ttu-id="b817d-115">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="b817d-115">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="b817d-116">結果類型</span><span class="sxs-lookup"><span data-stu-id="b817d-116">Result Types</span></span>  
 <span data-ttu-id="b817d-117">DT_BOOL</span><span class="sxs-lookup"><span data-stu-id="b817d-117">DT_BOOL</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b817d-118">備註</span><span class="sxs-lookup"><span data-stu-id="b817d-118">Remarks</span></span>  
 <span data-ttu-id="b817d-119">下表顯示 ! 運算的結果</span><span class="sxs-lookup"><span data-stu-id="b817d-119">The following table shows the result of the !</span></span> <span data-ttu-id="b817d-120">事件。</span><span class="sxs-lookup"><span data-stu-id="b817d-120">operation.</span></span>  
  
|<span data-ttu-id="b817d-121">原始布林運算式</span><span class="sxs-lookup"><span data-stu-id="b817d-121">Original Boolean expression</span></span>|<span data-ttu-id="b817d-122">套用</span><span class="sxs-lookup"><span data-stu-id="b817d-122">After applying the !</span></span> <span data-ttu-id="b817d-123">! 運算子之後</span><span class="sxs-lookup"><span data-stu-id="b817d-123">operator</span></span>|  
|---------------------------------|------------------------------------|  
|<span data-ttu-id="b817d-124">TRUE</span><span class="sxs-lookup"><span data-stu-id="b817d-124">TRUE</span></span>|<span data-ttu-id="b817d-125">FALSE</span><span class="sxs-lookup"><span data-stu-id="b817d-125">FALSE</span></span>|  
|<span data-ttu-id="b817d-126">NULL</span><span class="sxs-lookup"><span data-stu-id="b817d-126">NULL</span></span>|<span data-ttu-id="b817d-127">NULL</span><span class="sxs-lookup"><span data-stu-id="b817d-127">NULL</span></span>|  
|<span data-ttu-id="b817d-128">FALSE</span><span class="sxs-lookup"><span data-stu-id="b817d-128">FALSE</span></span>|<span data-ttu-id="b817d-129">TRUE</span><span class="sxs-lookup"><span data-stu-id="b817d-129">TRUE</span></span>|  
  
## <a name="expression-examples"></a><span data-ttu-id="b817d-130">運算式範例</span><span class="sxs-lookup"><span data-stu-id="b817d-130">Expression Examples</span></span>  
 <span data-ttu-id="b817d-131">如果 **Color** 資料行的值為 「red」，則此範例會評估為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="b817d-131">This example evaluates to FALSE if the **Color** column value is "red".</span></span>  
  
```  
!(Color == "red")  
```  
  
 <span data-ttu-id="b817d-132">如果 **MonthNumber** 變數與代表目前月份的整數相同，則此範例的評估結果為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="b817d-132">This example evaluates to TRUE if the value of the **MonthNumber** variable is the same as the integer that represents the current month.</span></span> <span data-ttu-id="b817d-133">如需詳細資訊，請參閱 [MONTH &#40;SSIS 運算式&#41;](month-ssis-expression.md) 和 [GETDATE &#40;SSIS 運算式&#41;](getdate-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="b817d-133">For more information, see [MONTH &#40;SSIS Expression&#41;](month-ssis-expression.md) and [GETDATE &#40;SSIS Expression&#41;](getdate-ssis-expression.md).</span></span>  
  
```  
!(@MonthNumber != MONTH(GETDATE())  
```  
  
## <a name="see-also"></a><span data-ttu-id="b817d-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b817d-134">See Also</span></span>  
 <span data-ttu-id="b817d-135">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="b817d-135">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="b817d-136">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="b817d-136">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
