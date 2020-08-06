---
title: '- (負) (SSIS 運算式) | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- '- (negative)'
- negative operator (-)
ms.assetid: f0118dfc-aced-4de2-953e-5ebf9c962b8d
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2a2d8ba292f2d24633598ab080ddf75ded5e8bd1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704321"
---
# <a name="--negate-ssis-expression"></a><span data-ttu-id="6074e-102">- (負) (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="6074e-102">- (Negate) (SSIS Expression)</span></span>
  <span data-ttu-id="6074e-103">執行數值運算式的否定運算。</span><span class="sxs-lookup"><span data-stu-id="6074e-103">Negates a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6074e-104">語法</span><span class="sxs-lookup"><span data-stu-id="6074e-104">Syntax</span></span>  
  
```  
  
-numeric_expression  
  
```  
  
## <a name="arguments"></a><span data-ttu-id="6074e-105">引數</span><span class="sxs-lookup"><span data-stu-id="6074e-105">Arguments</span></span>  
 <span data-ttu-id="6074e-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="6074e-106">*numeric_expression*</span></span>  
 <span data-ttu-id="6074e-107">是任何數值資料類型的任何有效運算式。</span><span class="sxs-lookup"><span data-stu-id="6074e-107">Is any valid expression of any numeric data type.</span></span> <span data-ttu-id="6074e-108">只支援帶正負號的數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="6074e-108">Only signed numeric data types are supported.</span></span> <span data-ttu-id="6074e-109">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="6074e-109">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="6074e-110">結果類型</span><span class="sxs-lookup"><span data-stu-id="6074e-110">Result Types</span></span>  
 <span data-ttu-id="6074e-111">傳回 *numeric_expression*的資料類型。</span><span class="sxs-lookup"><span data-stu-id="6074e-111">Returns the data type of *numeric_expression*.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="6074e-112">運算式範例</span><span class="sxs-lookup"><span data-stu-id="6074e-112">Expression Examples</span></span>  
 <span data-ttu-id="6074e-113">此範例會執行 **Counter** 變數值的否定運算並與數值常值 50 相加。</span><span class="sxs-lookup"><span data-stu-id="6074e-113">This example negates the value of the **Counter** variable and adds the numeric literal 50.</span></span>  
  
```  
-@Counter + 50  
```  
  
## <a name="see-also"></a><span data-ttu-id="6074e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6074e-114">See Also</span></span>  
 <span data-ttu-id="6074e-115">[運算子優先順序與關聯性](operator-precedence-and-associativity.md) </span><span class="sxs-lookup"><span data-stu-id="6074e-115">[Operator Precedence and Associativity](operator-precedence-and-associativity.md) </span></span>  
 [<span data-ttu-id="6074e-116">運算子 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="6074e-116">Operators &#40;SSIS Expression&#41;</span></span>](operators-ssis-expression.md)  
  
  
