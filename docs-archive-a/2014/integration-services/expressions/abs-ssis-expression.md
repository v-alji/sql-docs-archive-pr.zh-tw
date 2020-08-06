---
title: ABS (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- ABS function
- absolute positive value
ms.assetid: 156747f6-e016-44cf-9a9f-ae8e4a1b4f17
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a2f429dda94282646ef769a1c393f9fa54b56e5e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597980"
---
# <a name="abs-ssis-expression"></a><span data-ttu-id="f9003-102">ABS (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="f9003-102">ABS (SSIS Expression)</span></span>
  <span data-ttu-id="f9003-103">傳回數值運算式的絕對正數值。</span><span class="sxs-lookup"><span data-stu-id="f9003-103">Returns the absolute, positive value of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9003-104">語法</span><span class="sxs-lookup"><span data-stu-id="f9003-104">Syntax</span></span>  
  
```  
  
ABS(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="f9003-105">引數</span><span class="sxs-lookup"><span data-stu-id="f9003-105">Arguments</span></span>  
 <span data-ttu-id="f9003-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="f9003-106">*numeric_expression*</span></span>  
 <span data-ttu-id="f9003-107">是帶正負號或不帶正負號的數值運算式。</span><span class="sxs-lookup"><span data-stu-id="f9003-107">Is a signed or unsigned numeric expression.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="f9003-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="f9003-108">Result Types</span></span>  
 <span data-ttu-id="f9003-109">提交至函數之數值運算式的資料類型。</span><span class="sxs-lookup"><span data-stu-id="f9003-109">The data type of the numeric expression submitted to the function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9003-110">備註</span><span class="sxs-lookup"><span data-stu-id="f9003-110">Remarks</span></span>  
 <span data-ttu-id="f9003-111">如果引數為 Null，則 ABS 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="f9003-111">ABS returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="f9003-112">運算式範例</span><span class="sxs-lookup"><span data-stu-id="f9003-112">Expression Examples</span></span>  
 <span data-ttu-id="f9003-113">這些範例會將 ABS 函數套用至正數或負數。</span><span class="sxs-lookup"><span data-stu-id="f9003-113">These examples apply the ABS function to a positive and a negative number.</span></span> <span data-ttu-id="f9003-114">兩者都傳回 1.23。</span><span class="sxs-lookup"><span data-stu-id="f9003-114">Both return 1.23.</span></span>  
  
```  
ABS(-1.23)  
ABS(1.23)  
```  
  
 <span data-ttu-id="f9003-115">此範例會將 ABS 函數套用至減去 **HighTemperature** 和 **LowTempature**變數值的運算式。</span><span class="sxs-lookup"><span data-stu-id="f9003-115">This example applies the ABS function to an expression that subtracts values in the variables **HighTemperature** and **LowTempature**.</span></span>  
  
```  
ABS(@HighTemperature - @LowTemperature)  
```  
  
## <a name="see-also"></a><span data-ttu-id="f9003-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f9003-116">See Also</span></span>  
 [<span data-ttu-id="f9003-117">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="f9003-117">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
