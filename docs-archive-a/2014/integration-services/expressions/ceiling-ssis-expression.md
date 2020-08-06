---
title: CEILING (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- smallest integer great than or equal to expression
- CEILING function [SSIS]
ms.assetid: c35bd4ee-1ab6-46ab-89a7-cf771527faa2
author: chugugrace
ms.author: chugu
ms.openlocfilehash: cd2f9f455226925d6bf00842e80a8713e6c72771
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606991"
---
# <a name="ceiling-ssis-expression"></a><span data-ttu-id="681ec-102">CEILING (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="681ec-102">CEILING (SSIS Expression)</span></span>
  <span data-ttu-id="681ec-103">傳回大於或等於數值運算式的最小整數。</span><span class="sxs-lookup"><span data-stu-id="681ec-103">Returns the smallest integer that is greater than or equal to a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="681ec-104">語法</span><span class="sxs-lookup"><span data-stu-id="681ec-104">Syntax</span></span>  
  
```  
  
CEILING(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="681ec-105">引數</span><span class="sxs-lookup"><span data-stu-id="681ec-105">Arguments</span></span>  
 <span data-ttu-id="681ec-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="681ec-106">*numeric_expression*</span></span>  
 <span data-ttu-id="681ec-107">有效的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="681ec-107">Is a valid numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="681ec-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="681ec-108">Result Types</span></span>  
 <span data-ttu-id="681ec-109">提交至函數之數值運算式的資料類型。</span><span class="sxs-lookup"><span data-stu-id="681ec-109">The data type of the numeric expression submitted to the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="681ec-110">備註</span><span class="sxs-lookup"><span data-stu-id="681ec-110">Remarks</span></span>  
 <span data-ttu-id="681ec-111">如果引數為 Null，則 CEILING 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="681ec-111">CEILING returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="681ec-112">運算式範例</span><span class="sxs-lookup"><span data-stu-id="681ec-112">Expression Examples</span></span>  
 <span data-ttu-id="681ec-113">這些範例會將 CEILING 函數套用至正值、負值和零值。</span><span class="sxs-lookup"><span data-stu-id="681ec-113">These examples apply the CEILING function to positive, negative, and zero values.</span></span>  
  
```  
CEILING(123.74)  
```  
  
 <span data-ttu-id="681ec-114">傳回 124.00</span><span class="sxs-lookup"><span data-stu-id="681ec-114">Returns 124.00</span></span>  
  
```  
CEILING(-124.27)  
```  
  
 <span data-ttu-id="681ec-115">傳回 -124.00</span><span class="sxs-lookup"><span data-stu-id="681ec-115">Returns -124.00</span></span>  
  
```  
CEILING(0.00)  
```  
  
 <span data-ttu-id="681ec-116">傳回 0.00</span><span class="sxs-lookup"><span data-stu-id="681ec-116">Returns 0.00</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="681ec-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="681ec-117">See Also</span></span>  
 <span data-ttu-id="681ec-118">[FLOOR &#40;SSIS 運算式&#41;](floor-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="681ec-118">[FLOOR &#40;SSIS Expression&#41;](floor-ssis-expression.md) </span></span>  
 [<span data-ttu-id="681ec-119">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="681ec-119">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
