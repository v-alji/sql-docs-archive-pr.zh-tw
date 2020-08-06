---
title: '- (減) (SSIS 運算式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (subtract)'
- subtract operator (-)
ms.assetid: b48da086-37dd-460a-8a4b-912f52c9b158
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 79c47689baf47c33952c6b208ac622e9920d05fe
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701350"
---
# <a name="--subtract-ssis-expression"></a><span data-ttu-id="50dcd-102">- (減) (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="50dcd-102">- (Subtract) (SSIS Expression)</span></span>
  <span data-ttu-id="50dcd-103">將第一個數值運算式減第二個數值運算式。</span><span class="sxs-lookup"><span data-stu-id="50dcd-103">Subtracts the second numeric expression from the first one.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50dcd-104">語法</span><span class="sxs-lookup"><span data-stu-id="50dcd-104">Syntax</span></span>  
  
```  
  
numeric_expression1 - numeric_expression2  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="50dcd-105">引數</span><span class="sxs-lookup"><span data-stu-id="50dcd-105">Arguments</span></span>  
 <span data-ttu-id="50dcd-106">*numeric_expression1、numeric_expression2*</span><span class="sxs-lookup"><span data-stu-id="50dcd-106">*numeric_expression1, numeric_expression2*</span></span>  
 <span data-ttu-id="50dcd-107">任何有效的數值資料類型運算式。</span><span class="sxs-lookup"><span data-stu-id="50dcd-107">Is any valid expression of a numeric data type.</span></span> <span data-ttu-id="50dcd-108">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="50dcd-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="50dcd-109">結果類型</span><span class="sxs-lookup"><span data-stu-id="50dcd-109">Result Types</span></span>  
 <span data-ttu-id="50dcd-110">由兩個引數的資料類型決定。</span><span class="sxs-lookup"><span data-stu-id="50dcd-110">Determined by the data types of the two arguments.</span></span> <span data-ttu-id="50dcd-111">如需相關資訊，請參閱 [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="50dcd-111">For more information, see [Integration Services Data Types in Expressions](integration-services-data-types-in-expressions.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50dcd-112">備註</span><span class="sxs-lookup"><span data-stu-id="50dcd-112">Remarks</span></span>  
 <span data-ttu-id="50dcd-113">用括號括住一元減號運算式，以確保運算式以正確的順序接受評估。</span><span class="sxs-lookup"><span data-stu-id="50dcd-113">Enclose the minus unary expression in parenthesis to ensure that the expression is evaluated in the correct order</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="50dcd-114">備註</span><span class="sxs-lookup"><span data-stu-id="50dcd-114">Remarks</span></span>  
 <span data-ttu-id="50dcd-115">如果任一個運算元為 Null，則結果為 Null。</span><span class="sxs-lookup"><span data-stu-id="50dcd-115">If either operand is null, the result is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="50dcd-116">運算式範例</span><span class="sxs-lookup"><span data-stu-id="50dcd-116">Expression Examples</span></span>  
 <span data-ttu-id="50dcd-117">此範例會減去數值常值。</span><span class="sxs-lookup"><span data-stu-id="50dcd-117">This example subtracts numeric literals.</span></span>  
  
```  
5 - 6.09  
```  
  
 <span data-ttu-id="50dcd-118">此範例會將 **ListPrice** 資料行中的值減去 **StandardCost** 資料行中的值。</span><span class="sxs-lookup"><span data-stu-id="50dcd-118">This example subtracts the value in the **StandardCost** column from the value in the **ListPrice** column.</span></span>  
  
```  
ListPrice - StandardCost  
```  
  
 <span data-ttu-id="50dcd-119">此範例會從 **ListPrice** 資料行減去導出值。</span><span class="sxs-lookup"><span data-stu-id="50dcd-119">This example subtracts a calculated value from the **ListPrice** column.</span></span> <span data-ttu-id="50dcd-120">變數 **Discount%** 必須以方括號括住，因為名稱包含 % 字元。</span><span class="sxs-lookup"><span data-stu-id="50dcd-120">The variable **Discount%** must be enclosed in brackets because the name includes the % character.</span></span> <span data-ttu-id="50dcd-121">如需詳細資訊，請參閱[識別碼 &#40;SSIS&#41;](identifiers-ssis.md)。</span><span class="sxs-lookup"><span data-stu-id="50dcd-121">For more information, see [Identifiers &#40;SSIS&#41;](identifiers-ssis.md).</span></span>  
  
```  
ListPrice - (ListPrice * @[Discount%])  
```  
  
## <a name="see-also"></a><span data-ttu-id="50dcd-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="50dcd-122">See Also</span></span>  
 <span data-ttu-id="50dcd-123">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="50dcd-123">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="50dcd-124">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="50dcd-124">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
