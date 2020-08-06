---
title: SIGN (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- positive values [Integration Services]
- SIGN function
- negative values
ms.assetid: 1547db08-4329-4781-91c2-36898ed71b15
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a34992b0029cd378274e38ce4e37fcd313d2b788
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701389"
---
# <a name="sign-ssis-expression"></a><span data-ttu-id="74f3d-102">SIGN (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="74f3d-102">SIGN (SSIS Expression)</span></span>
  <span data-ttu-id="74f3d-103">傳回數值運算式的正 (+1)、負 (-1) 或零 (0) 符號。</span><span class="sxs-lookup"><span data-stu-id="74f3d-103">Returns the positive (+1), negative (-1), or zero (0) sign of a numeric expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74f3d-104">語法</span><span class="sxs-lookup"><span data-stu-id="74f3d-104">Syntax</span></span>  
  
```  
  
SIGN(numeric_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="74f3d-105">引數</span><span class="sxs-lookup"><span data-stu-id="74f3d-105">Arguments</span></span>  
 <span data-ttu-id="74f3d-106">*numeric_expression*</span><span class="sxs-lookup"><span data-stu-id="74f3d-106">*numeric_expression*</span></span>  
 <span data-ttu-id="74f3d-107">是帶正負號的有效數值運算式。</span><span class="sxs-lookup"><span data-stu-id="74f3d-107">Is a valid signed numeric expression.</span></span> <span data-ttu-id="74f3d-108">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="74f3d-108">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="74f3d-109">結果類型</span><span class="sxs-lookup"><span data-stu-id="74f3d-109">Result Types</span></span>  
 <span data-ttu-id="74f3d-110">DT_I4</span><span class="sxs-lookup"><span data-stu-id="74f3d-110">DT_I4</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="74f3d-111">備註</span><span class="sxs-lookup"><span data-stu-id="74f3d-111">Remarks</span></span>  
 <span data-ttu-id="74f3d-112">如果引數為 Null，則 SIGN 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="74f3d-112">SIGN returns a null result if the argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="74f3d-113">運算式範例</span><span class="sxs-lookup"><span data-stu-id="74f3d-113">Expression Examples</span></span>  
 <span data-ttu-id="74f3d-114">此範例會傳回數值常值的正負號。</span><span class="sxs-lookup"><span data-stu-id="74f3d-114">This example returns the sign of a numeric literal.</span></span> <span data-ttu-id="74f3d-115">傳回結果為 -1。</span><span class="sxs-lookup"><span data-stu-id="74f3d-115">The return result is -1.</span></span>  
  
```  
SIGN(-123.45)  
```  
  
 <span data-ttu-id="74f3d-116">此範例會傳回從 **DealerPrice** 資料行減去 **StandardCost** 資料行之結果的正負號。</span><span class="sxs-lookup"><span data-stu-id="74f3d-116">This example returns the sign of the result of subtracting the **StandardCost** column from the **DealerPrice** column.</span></span>  
  
```  
SIGN(DealerPrice - StandardCost)  
```  
  
## <a name="see-also"></a><span data-ttu-id="74f3d-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="74f3d-117">See Also</span></span>  
 [<span data-ttu-id="74f3d-118">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="74f3d-118">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
