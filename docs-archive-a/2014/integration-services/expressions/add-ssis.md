---
title: + (加法) (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- + (add)
- add operator (+)
- adding expressions
ms.assetid: 44df4154-fed5-4e7f-9995-e703a0164f6a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: fe1e8f2118e6328582cb24abfd44eef5f3b15f79
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597978"
---
# <a name="-add-ssis"></a><span data-ttu-id="cc1ee-102">+ (加) (SSIS)</span><span class="sxs-lookup"><span data-stu-id="cc1ee-102">+ (Add) (SSIS)</span></span>
  <span data-ttu-id="cc1ee-103">加入兩個數值運算式。</span><span class="sxs-lookup"><span data-stu-id="cc1ee-103">Adds two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc1ee-104">語法</span><span class="sxs-lookup"><span data-stu-id="cc1ee-104">Syntax</span></span>  
  
```  
  
numeric_expression1 + numeric_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="cc1ee-105">引數</span><span class="sxs-lookup"><span data-stu-id="cc1ee-105">Arguments</span></span>  
 <span data-ttu-id="cc1ee-106">*numeric_expression1、numeric_ expression2*</span><span class="sxs-lookup"><span data-stu-id="cc1ee-106">*numeric_expression1, numeric_ expression2*</span></span>  
 <span data-ttu-id="cc1ee-107">任何有效的數值資料類型運算式。</span><span class="sxs-lookup"><span data-stu-id="cc1ee-107">Is any valid expression of a numeric data type.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="cc1ee-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="cc1ee-108">Result Types</span></span>  
 <span data-ttu-id="cc1ee-109">由兩個引數的資料類型決定。</span><span class="sxs-lookup"><span data-stu-id="cc1ee-109">Determined by data types of the two arguments.</span></span> <span data-ttu-id="cc1ee-110">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="cc1ee-110">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cc1ee-111">備註</span><span class="sxs-lookup"><span data-stu-id="cc1ee-111">Remarks</span></span>  
 <span data-ttu-id="cc1ee-112">如果任一個運算元為 Null，則結果為 Null。</span><span class="sxs-lookup"><span data-stu-id="cc1ee-112">If either operand is null, the result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="cc1ee-113">運算式範例</span><span class="sxs-lookup"><span data-stu-id="cc1ee-113">Expression Examples</span></span>  
 <span data-ttu-id="cc1ee-114">此範例會加上數值常值。</span><span class="sxs-lookup"><span data-stu-id="cc1ee-114">This example adds numeric literals.</span></span>  
  
```  
5 + 6.09 + 7.0  
```  
  
 <span data-ttu-id="cc1ee-115">此範例會將 **VacationHours** 和 **SickLeaveHours** 資料行中的值相加。</span><span class="sxs-lookup"><span data-stu-id="cc1ee-115">This example adds values in the **VacationHours** and **SickLeaveHours** columns.</span></span>  
  
```  
VacationHours + SickLeaveHours  
```  
  
 <span data-ttu-id="cc1ee-116">此範例會將計算出的值加入至 **StandardCost** 資料行。</span><span class="sxs-lookup"><span data-stu-id="cc1ee-116">This example adds a calculated value to the **StandardCost** column.</span></span> <span data-ttu-id="cc1ee-117">**Profit%** 變數必須加上方括號，因為名稱包含 % 字元。</span><span class="sxs-lookup"><span data-stu-id="cc1ee-117">The variable **Profit%** must be enclosed in brackets because the name includes the % character.</span></span> <span data-ttu-id="cc1ee-118">如需詳細資訊，請參閱[識別碼 &#40;SSIS&#41;](identifiers-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="cc1ee-118">For more information, see [Identifiers &#40;SSIS&#41;](identifiers-ssis.md).</span></span>  
  
```  
StandardCost + (StandardCost * @[Profit%])  
```  
  
## <a name="see-also"></a><span data-ttu-id="cc1ee-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cc1ee-119">See Also</span></span>  
 <span data-ttu-id="cc1ee-120">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="cc1ee-120">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="cc1ee-121">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="cc1ee-121">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
