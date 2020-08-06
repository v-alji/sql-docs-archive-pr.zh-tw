---
title: HEX (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- hexadecimal data
- HEX function
ms.assetid: f5d471ee-aeef-421c-b6e1-55b9676c3842
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 640ae38ec5d2cd5ffb448e9aebde5ba5ceba2684
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705330"
---
# <a name="hex-ssis-expression"></a><span data-ttu-id="a7543-102">HEX (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="a7543-102">HEX (SSIS Expression)</span></span>
  <span data-ttu-id="a7543-103">傳回代表整數的十六進位值的字串。</span><span class="sxs-lookup"><span data-stu-id="a7543-103">Returns a string representing the hexadecimal value of an integer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7543-104">語法</span><span class="sxs-lookup"><span data-stu-id="a7543-104">Syntax</span></span>  
  
```  
  
HEX(integer_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="a7543-105">引數</span><span class="sxs-lookup"><span data-stu-id="a7543-105">Arguments</span></span>  
 <span data-ttu-id="a7543-106">*integer_expression*</span><span class="sxs-lookup"><span data-stu-id="a7543-106">*integer_expression*</span></span>  
 <span data-ttu-id="a7543-107">是帶正負號或不帶正負號的整數。</span><span class="sxs-lookup"><span data-stu-id="a7543-107">Is a signed or unsigned integer.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="a7543-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="a7543-108">Result Types</span></span>  
 <span data-ttu-id="a7543-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="a7543-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7543-110">備註</span><span class="sxs-lookup"><span data-stu-id="a7543-110">Remarks</span></span>  
 <span data-ttu-id="a7543-111">如果 *integer_expression* 是 Null，則 HEX 會傳回 Null。</span><span class="sxs-lookup"><span data-stu-id="a7543-111">HEX returns null if *integer_expression* is null.</span></span>  
  
 <span data-ttu-id="a7543-112">*integer_expression* 引數必須評估為整數。</span><span class="sxs-lookup"><span data-stu-id="a7543-112">The *integer_expression* argument must evaluate to an integer.</span></span> <span data-ttu-id="a7543-113">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)。</span><span class="sxs-lookup"><span data-stu-id="a7543-113">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md).</span></span>  
  
 <span data-ttu-id="a7543-114">傳回結果不包含限定詞，例如 0x 前置詞。</span><span class="sxs-lookup"><span data-stu-id="a7543-114">The return result does not include qualifiers such as the 0x prefix.</span></span> <span data-ttu-id="a7543-115">若要包含前置詞，請使用 + (串連) 運算子。</span><span class="sxs-lookup"><span data-stu-id="a7543-115">To include a prefix, use the + (Concatenate) operator.</span></span> <span data-ttu-id="a7543-116">如需詳細資訊，請參閱 [+ &#40;串連&#41; &#40;SSIS 運算式&#41;](concatenate-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="a7543-116">For more information, see [+ &#40;Concatenate&#41; &#40;SSIS Expression&#41;](concatenate-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="a7543-117">HEX 標記法中使用的字母 A-F 會以大寫字元顯示。</span><span class="sxs-lookup"><span data-stu-id="a7543-117">The letters A - F, used in HEX notations, appear as uppercase characters.</span></span>  
  
 <span data-ttu-id="a7543-118">整數資料類型的結果字串長度如下：</span><span class="sxs-lookup"><span data-stu-id="a7543-118">The length of the resulting string for integer data types is as follows:</span></span>  
  
-   <span data-ttu-id="a7543-119">DT_I1 和 DT_UI1 傳回最大長度為 2 的字串。</span><span class="sxs-lookup"><span data-stu-id="a7543-119">DT_I1 and DT_UI1 return a string with a maximum length of 2.</span></span>  
  
-   <span data-ttu-id="a7543-120">DT_I2 和 DT_UI2 傳回最大長度為 4 的字串。</span><span class="sxs-lookup"><span data-stu-id="a7543-120">DT_I2 and DT_UI2 return a string with a maximum length of 4.</span></span>  
  
-   <span data-ttu-id="a7543-121">DT_I4 和 DT_UI4 傳回最大長度為 8 的字串。</span><span class="sxs-lookup"><span data-stu-id="a7543-121">DT_I4 and DT_UI4 return a string with a maximum length of 8.</span></span>  
  
-   <span data-ttu-id="a7543-122">DT_I8 和 DT_UI8 傳回最大長度為 16 的字串。</span><span class="sxs-lookup"><span data-stu-id="a7543-122">DT_I8 and DT_UI8 return a string with a maximum length of 16.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="a7543-123">運算式範例</span><span class="sxs-lookup"><span data-stu-id="a7543-123">Expression Examples</span></span>  
 <span data-ttu-id="a7543-124">這個範例使用數值常值。</span><span class="sxs-lookup"><span data-stu-id="a7543-124">This example uses a numeric literal.</span></span> <span data-ttu-id="a7543-125">函數傳回值 190。</span><span class="sxs-lookup"><span data-stu-id="a7543-125">The function returns the value 190.</span></span>  
  
```  
HEX(400)   
```  
  
 <span data-ttu-id="a7543-126">此範例使用 **ReorderPoint** 資料行。</span><span class="sxs-lookup"><span data-stu-id="a7543-126">This example uses the **ReorderPoint** column.</span></span> <span data-ttu-id="a7543-127">資料行資料類型為 `smallint`。</span><span class="sxs-lookup"><span data-stu-id="a7543-127">The column data type is `smallint`.</span></span> <span data-ttu-id="a7543-128">如果 **ReorderPoint** 是 750，則函數會傳回 2EE。</span><span class="sxs-lookup"><span data-stu-id="a7543-128">If **ReorderPoint** is 750, the function returns 2EE.</span></span>  
  
```  
HEX(ReorderPoint)   
```  
  
 <span data-ttu-id="a7543-129">此範例使用系統變數 **LocaleID**。</span><span class="sxs-lookup"><span data-stu-id="a7543-129">This example uses **LocaleID**, a system variable.</span></span> <span data-ttu-id="a7543-130">如果 **LocaleID** 是 1033，則函數會傳回 409。</span><span class="sxs-lookup"><span data-stu-id="a7543-130">If **LocaleID** is 1033, the function returns 409.</span></span>  
  
```  
HEX(@LocaleID)  
```  
  
## <a name="see-also"></a><span data-ttu-id="a7543-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a7543-131">See Also</span></span>  
 [<span data-ttu-id="a7543-132">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="a7543-132">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
