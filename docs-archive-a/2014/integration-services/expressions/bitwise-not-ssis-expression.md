---
title: ~ (位元 Not) (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- bitwise NOT (~)
- ~ (bitwise NOT)
ms.assetid: e4413ddd-0d0e-40c3-9c76-b5ce323218ec
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 75745a0650c1744064f2a671659879e11464514e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597966"
---
# <a name="-bitwise-not-ssis-expression"></a><span data-ttu-id="731c9-102">~ (位元 Not) (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="731c9-102">~ (Bitwise Not) (SSIS Expression)</span></span>
  <span data-ttu-id="731c9-103">執行整數的位元否定運算。</span><span class="sxs-lookup"><span data-stu-id="731c9-103">Performs a bitwise negation of an integer.</span></span> <span data-ttu-id="731c9-104">此運算子可套用至帶正負號及不帶正負號的整數資料類型。</span><span class="sxs-lookup"><span data-stu-id="731c9-104">This operator can be applied to signed and unsigned integer data types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="731c9-105">語法</span><span class="sxs-lookup"><span data-stu-id="731c9-105">Syntax</span></span>  
  
```  
  
~integer_expression  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="731c9-106">引數</span><span class="sxs-lookup"><span data-stu-id="731c9-106">Arguments</span></span>  
 <span data-ttu-id="731c9-107">*integer_expression*</span><span class="sxs-lookup"><span data-stu-id="731c9-107">*integer_expression*</span></span>  
 <span data-ttu-id="731c9-108">是任何整數資料類型的有效運算式。</span><span class="sxs-lookup"><span data-stu-id="731c9-108">Is any valid expression of an integer data type.</span></span> <span data-ttu-id="731c9-109">*integer*_*expression* 是整數，會轉換成二進位數字以進行位元運算。</span><span class="sxs-lookup"><span data-stu-id="731c9-109">*integer*_*expression* is an integer that is transformed into a binary number for the bitwise operation.</span></span> <span data-ttu-id="731c9-110">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="731c9-110">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="731c9-111">結果類型</span><span class="sxs-lookup"><span data-stu-id="731c9-111">Result Types</span></span>  
 <span data-ttu-id="731c9-112">傳回 *integer_expression*的資料類型。</span><span class="sxs-lookup"><span data-stu-id="731c9-112">Returns the data type of *integer_expression.*</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="731c9-113">備註</span><span class="sxs-lookup"><span data-stu-id="731c9-113">Remarks</span></span>  
 <span data-ttu-id="731c9-114">None</span><span class="sxs-lookup"><span data-stu-id="731c9-114">None</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="731c9-115">運算式範例</span><span class="sxs-lookup"><span data-stu-id="731c9-115">Expression Examples</span></span>  
 <span data-ttu-id="731c9-116">此範例會在數字 170 (0000 0000 1010 1010) 上執行位元 ~ (NOT) 運算。</span><span class="sxs-lookup"><span data-stu-id="731c9-116">This example performs a bitwise ~ (NOT) operation on the number 170 (0000 0000 1010 1010).</span></span> <span data-ttu-id="731c9-117">此數字為帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="731c9-117">The number is a signed integer.</span></span>  
  
```  
  
~ 170  
```  
  
 <span data-ttu-id="731c9-118">運算式評估結果為 -170 (1111111101010101)。</span><span class="sxs-lookup"><span data-stu-id="731c9-118">The expression evaluates to -170 (1111111101010101).</span></span>  
  
 <span data-ttu-id="731c9-119">0000000010101010</span><span class="sxs-lookup"><span data-stu-id="731c9-119">0000000010101010</span></span>  
  
 ---------------------\-  
  
 <span data-ttu-id="731c9-120">1111111101010101</span><span class="sxs-lookup"><span data-stu-id="731c9-120">1111111101010101</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="731c9-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="731c9-121">See Also</span></span>  
 <span data-ttu-id="731c9-122">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="731c9-122">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="731c9-123">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="731c9-123">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
