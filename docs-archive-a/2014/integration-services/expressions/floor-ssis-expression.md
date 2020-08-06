---
title: FLOOR (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- largest integer less than or equal to expression
- FLOOR function [SSIS]
ms.assetid: 168084db-badd-40f2-87b4-1f5bc45c3e24
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b638c9a7215d120c562e416cdecee463f031ad2a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595205"
---
# <a name="floor-ssis-expression"></a><span data-ttu-id="e39ba-102">FLOOR (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="e39ba-102">FLOOR (SSIS Expression)</span></span>
  <span data-ttu-id="e39ba-103">傳回小於或等於數值運算式的最大整數。</span><span class="sxs-lookup"><span data-stu-id="e39ba-103">Returns the largest integer that is less than or equal to a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e39ba-104">語法</span><span class="sxs-lookup"><span data-stu-id="e39ba-104">Syntax</span></span>  
  
```  
  
FLOOR(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="e39ba-105">引數</span><span class="sxs-lookup"><span data-stu-id="e39ba-105">Arguments</span></span>  
 <span data-ttu-id="e39ba-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="e39ba-106">*numeric_expression*</span></span>  
 <span data-ttu-id="e39ba-107">有效的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="e39ba-107">Is a valid numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="e39ba-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="e39ba-108">Result Types</span></span>  
 <span data-ttu-id="e39ba-109">引數運算式的數值資料類型。</span><span class="sxs-lookup"><span data-stu-id="e39ba-109">The numeric data type of the argument expression.</span></span> <span data-ttu-id="e39ba-110">結果是計算值的整數部分，與 *numeric_expression*具有相同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="e39ba-110">The result is the integer portion of the calculated value in the same data type as *numeric_expression.*</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e39ba-111">備註</span><span class="sxs-lookup"><span data-stu-id="e39ba-111">Remarks</span></span>  
 <span data-ttu-id="e39ba-112">如果引數為 Null，則 FLOOR 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="e39ba-112">FLOOR returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="e39ba-113">運算式範例</span><span class="sxs-lookup"><span data-stu-id="e39ba-113">Expression Examples</span></span>  
 <span data-ttu-id="e39ba-114">這些範例會將 FLOOR 函數套用至正值、負值和零值。</span><span class="sxs-lookup"><span data-stu-id="e39ba-114">These examples apply the FLOOR function to positive, negative, and zero values.</span></span>  
  
```  
FLOOR(123.45)  
```  
  
 <span data-ttu-id="e39ba-115">傳回 123.00</span><span class="sxs-lookup"><span data-stu-id="e39ba-115">Returns 123.00</span></span>  
  
```  
FLOOR(-123.45)  
```  
  
 <span data-ttu-id="e39ba-116">傳回 -124.00</span><span class="sxs-lookup"><span data-stu-id="e39ba-116">Returns -124.00</span></span>  
  
```  
FLOOR(0.00)  
```  
  
 <span data-ttu-id="e39ba-117">傳回 0.00</span><span class="sxs-lookup"><span data-stu-id="e39ba-117">Returns 0.00</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e39ba-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e39ba-118">See Also</span></span>  
 <span data-ttu-id="e39ba-119">[CEILING &#40;SSIS 運算式&#41;](ceiling-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="e39ba-119">[CEILING &#40;SSIS Expression&#41;](ceiling-ssis-expression.md) </span></span>  
 [<span data-ttu-id="e39ba-120">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="e39ba-120">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
