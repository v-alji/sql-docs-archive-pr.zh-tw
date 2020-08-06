---
title: '* (乘) (SSIS 運算式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '* (multiply operator)'
- multiply operator (*)
ms.assetid: d457f052-ffbb-4485-833f-f4bed4349b69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16d8429a869b60be31a94244a2ce47d515770c6b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595198"
---
# <a name="-multiply-ssis-expression"></a><span data-ttu-id="1fdfe-102">\* (乘) (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="1fdfe-102">\* (Multiply) (SSIS Expression)</span></span>
  <span data-ttu-id="1fdfe-103">將兩個數值運算式相乘。</span><span class="sxs-lookup"><span data-stu-id="1fdfe-103">Multiplies two numeric expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1fdfe-104">語法</span><span class="sxs-lookup"><span data-stu-id="1fdfe-104">Syntax</span></span>  
  
```  
  
numeric_expression1 * numeric_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="1fdfe-105">引數</span><span class="sxs-lookup"><span data-stu-id="1fdfe-105">Arguments</span></span>  
 <span data-ttu-id="1fdfe-106">*numeric_expression1、numeric_expression2*</span><span class="sxs-lookup"><span data-stu-id="1fdfe-106">*numeric_expression1, numeric_expression2*</span></span>  
 <span data-ttu-id="1fdfe-107">任何有效的數值資料類型運算式。</span><span class="sxs-lookup"><span data-stu-id="1fdfe-107">Is any valid expression of a numeric data type.</span></span> <span data-ttu-id="1fdfe-108">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="1fdfe-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="1fdfe-109">結果類型</span><span class="sxs-lookup"><span data-stu-id="1fdfe-109">Result Types</span></span>  
 <span data-ttu-id="1fdfe-110">由兩個引數的資料類型決定。</span><span class="sxs-lookup"><span data-stu-id="1fdfe-110">Determined by data types of the two arguments.</span></span> <span data-ttu-id="1fdfe-111">如需相關資訊，請參閱 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="1fdfe-111">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1fdfe-112">備註</span><span class="sxs-lookup"><span data-stu-id="1fdfe-112">Remarks</span></span>  
 <span data-ttu-id="1fdfe-113">如果任一個運算元為 Null，則結果為 Null。</span><span class="sxs-lookup"><span data-stu-id="1fdfe-113">If either operand is null, the result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="1fdfe-114">運算式範例</span><span class="sxs-lookup"><span data-stu-id="1fdfe-114">Expression Examples</span></span>  
 <span data-ttu-id="1fdfe-115">此範例會乘以數值常值。</span><span class="sxs-lookup"><span data-stu-id="1fdfe-115">This example multiplies numeric literals.</span></span>  
  
```  
5 * 6.09  
```  
  
 <span data-ttu-id="1fdfe-116">此範例會將 **ListPrice** 資料行中的值乘以 10%。</span><span class="sxs-lookup"><span data-stu-id="1fdfe-116">This example multiplies values in the **ListPrice** column by 10 percent.</span></span>  
  
```  
ListPrice * .10  
```  
  
 <span data-ttu-id="1fdfe-117">此範例會從 **ListPrice** 資料行減去運算式的結果。</span><span class="sxs-lookup"><span data-stu-id="1fdfe-117">This example subtracts the result of an expression from the **ListPrice** column.</span></span> <span data-ttu-id="1fdfe-118">變數 **Discount%** 必須以方括號括住，因為名稱包含 % 字元。</span><span class="sxs-lookup"><span data-stu-id="1fdfe-118">The variable **Discount%** must be enclosed in brackets because the name includes the % character.</span></span> <span data-ttu-id="1fdfe-119">如需詳細資訊，請參閱[識別碼 &#40;SSIS&#41;](identifiers-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="1fdfe-119">For more information, see [Identifiers &#40;SSIS&#41;](identifiers-ssis.md).</span></span>  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a><span data-ttu-id="1fdfe-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1fdfe-120">See Also</span></span>  
 <span data-ttu-id="1fdfe-121">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="1fdfe-121">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="1fdfe-122">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="1fdfe-122">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
