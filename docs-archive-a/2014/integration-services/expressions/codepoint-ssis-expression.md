---
title: CODEPOINT (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- CODEPOINT function
- leftmost character of expression
ms.assetid: 0783d05e-7f35-42fb-a2c4-9621c46effd6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: bf05cc0838763ba9e22707af57892133d449da07
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585505"
---
# <a name="codepoint-ssis-expression"></a><span data-ttu-id="aaeca-102">CODEPOINT (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="aaeca-102">CODEPOINT (SSIS Expression)</span></span>
  <span data-ttu-id="aaeca-103">傳回字元運算式最左邊字元的 Unicode 字碼指標。</span><span class="sxs-lookup"><span data-stu-id="aaeca-103">Returns the Unicode code point of the leftmost character of a character expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aaeca-104">語法</span><span class="sxs-lookup"><span data-stu-id="aaeca-104">Syntax</span></span>  
  
```  
  
CODEPOINT(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="aaeca-105">引數</span><span class="sxs-lookup"><span data-stu-id="aaeca-105">Arguments</span></span>  
 <span data-ttu-id="aaeca-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="aaeca-106">*character_expression*</span></span>  
 <span data-ttu-id="aaeca-107">是將要評估最左邊字元的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="aaeca-107">Is a character expression whose leftmost character will be evaluated.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="aaeca-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="aaeca-108">Result Types</span></span>  
 <span data-ttu-id="aaeca-109">DT_UI2</span><span class="sxs-lookup"><span data-stu-id="aaeca-109">DT_UI2</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aaeca-110">備註</span><span class="sxs-lookup"><span data-stu-id="aaeca-110">Remarks</span></span>  
 <span data-ttu-id="aaeca-111">*character_expression* 引數必須是 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="aaeca-111">*character_expression* must have the DT_WSTR data type.</span></span>  
  
 <span data-ttu-id="aaeca-112">如果 *character_expression* 為 Null 或空字串，則 CODEPOINT 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="aaeca-112">CODEPOINT returns a null result if *character_expression* is null or an empty string.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="aaeca-113">運算式範例</span><span class="sxs-lookup"><span data-stu-id="aaeca-113">Expression Examples</span></span>  
 <span data-ttu-id="aaeca-114">這個範例使用字串常值。</span><span class="sxs-lookup"><span data-stu-id="aaeca-114">This example uses a string literal.</span></span> <span data-ttu-id="aaeca-115">傳回結果為 77，即 M 的 Unicode 字碼指標。</span><span class="sxs-lookup"><span data-stu-id="aaeca-115">The return result is 77, the Unicode code point for M.</span></span>  
  
```  
CODEPOINT("Mountain Bike")  
```  
  
 <span data-ttu-id="aaeca-116">這個範例使用變數。</span><span class="sxs-lookup"><span data-stu-id="aaeca-116">This example uses a variable.</span></span> <span data-ttu-id="aaeca-117">如果 **Name** 是 Touring Front Wheel，則傳回結果為 84，即 T 的 Unicode 字碼指標。</span><span class="sxs-lookup"><span data-stu-id="aaeca-117">If **Name** is Touring Front Wheel, the return result is 84, the Unicode code point for T.</span></span>  
  
```  
CODEPOINT(@Name)  
```  
  
## <a name="see-also"></a><span data-ttu-id="aaeca-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aaeca-118">See Also</span></span>  
 [<span data-ttu-id="aaeca-119">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="aaeca-119">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
