---
title: ROUND (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- rounding expressions
- ROUND function [SSIS]
ms.assetid: 376f1947-4fc5-4611-ad86-823e4db1b468
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 9d77045787eafbc3dd402db9982d8d7a98190bc2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701398"
---
# <a name="round-ssis-expression"></a><span data-ttu-id="fd4c6-102">ROUND (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="fd4c6-102">ROUND (SSIS Expression)</span></span>
  <span data-ttu-id="fd4c6-103">傳回已經進位到指定長度或有效位數的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="fd4c6-103">Returns a numeric expression that is rounded to the specified length or precision.</span></span> <span data-ttu-id="fd4c6-104">length 參數必須評估為整數。</span><span class="sxs-lookup"><span data-stu-id="fd4c6-104">The length parameter must evaluate to an integer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd4c6-105">語法</span><span class="sxs-lookup"><span data-stu-id="fd4c6-105">Syntax</span></span>  
  
```  
  
ROUND(numeric_expression,length)  
```  
  
## <a name="arguments"></a><span data-ttu-id="fd4c6-106">引數</span><span class="sxs-lookup"><span data-stu-id="fd4c6-106">Arguments</span></span>  
 <span data-ttu-id="fd4c6-107">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="fd4c6-107">*numeric_expression*</span></span>  
 <span data-ttu-id="fd4c6-108">是有效數值類型的運算式。</span><span class="sxs-lookup"><span data-stu-id="fd4c6-108">Is an expression of a valid numeric type.</span></span> <span data-ttu-id="fd4c6-109">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="fd4c6-109">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="fd4c6-110">*length*</span><span class="sxs-lookup"><span data-stu-id="fd4c6-110">*length*</span></span>  
 <span data-ttu-id="fd4c6-111">是整數運算式。</span><span class="sxs-lookup"><span data-stu-id="fd4c6-111">Is an integer expression.</span></span> <span data-ttu-id="fd4c6-112">它是 *numeric_expression* 進位到的有效位數。</span><span class="sxs-lookup"><span data-stu-id="fd4c6-112">It is the precision to which *numeric_expression* is rounded.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="fd4c6-113">結果類型</span><span class="sxs-lookup"><span data-stu-id="fd4c6-113">Result Types</span></span>  
 <span data-ttu-id="fd4c6-114">與 *numeric*_*expression*相同的類型。</span><span class="sxs-lookup"><span data-stu-id="fd4c6-114">The same type as *numeric*_*expression.*</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fd4c6-115">備註</span><span class="sxs-lookup"><span data-stu-id="fd4c6-115">Remarks</span></span>  
 <span data-ttu-id="fd4c6-116">*length* 引數必須評估為正整數或零。</span><span class="sxs-lookup"><span data-stu-id="fd4c6-116">The *length* argument must evaluate to a positive integer or zero.</span></span>  
  
 <span data-ttu-id="fd4c6-117">如果引數為 Null，則 ROUND 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="fd4c6-117">ROUND returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="fd4c6-118">運算式範例</span><span class="sxs-lookup"><span data-stu-id="fd4c6-118">Expression Examples</span></span>  
 <span data-ttu-id="fd4c6-119">這些範例會將數值常值進位到長度 3。</span><span class="sxs-lookup"><span data-stu-id="fd4c6-119">These examples round numeric literals to a length of three.</span></span> <span data-ttu-id="fd4c6-120">第一個傳回結果為 137.1570，第二個為 137.1580。</span><span class="sxs-lookup"><span data-stu-id="fd4c6-120">The first return result is 137.1570, the second 137.1580.</span></span>  
  
```  
ROUND(137.1574,3)  
ROUND(137.1575,3)  
```  
  
## <a name="see-also"></a><span data-ttu-id="fd4c6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fd4c6-121">See Also</span></span>  
 [<span data-ttu-id="fd4c6-122">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="fd4c6-122">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
