---
title: LEFT (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 5634dbfb-740d-4c93-8fd5-2854cc741327
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7f21d134988414c7d8579d720877feec45383270
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599065"
---
# <a name="left-ssis-expression"></a><span data-ttu-id="870ad-102">LEFT (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="870ad-102">LEFT (SSIS Expression)</span></span>
  <span data-ttu-id="870ad-103">傳回來自給定字元運算式最左邊部分的指定字元數。</span><span class="sxs-lookup"><span data-stu-id="870ad-103">Returns the specified number of characters from the leftmost portion of the given character expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="870ad-104">語法</span><span class="sxs-lookup"><span data-stu-id="870ad-104">Syntax</span></span>  
  
```  
  
LEFT(character_expression,number)  
```  
  
## <a name="arguments"></a><span data-ttu-id="870ad-105">引數</span><span class="sxs-lookup"><span data-stu-id="870ad-105">Arguments</span></span>  
 <span data-ttu-id="870ad-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="870ad-106">*character_expression*</span></span>  
 <span data-ttu-id="870ad-107">要擷取字元的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="870ad-107">Is a character expression from which to extract characters.</span></span>  
  
 <span data-ttu-id="870ad-108">*number*</span><span class="sxs-lookup"><span data-stu-id="870ad-108">*number*</span></span>  
 <span data-ttu-id="870ad-109">為表示要傳回字元數的整數運算式。</span><span class="sxs-lookup"><span data-stu-id="870ad-109">Is an integer expression that indicates the number of characters to be returned.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="870ad-110">結果類型</span><span class="sxs-lookup"><span data-stu-id="870ad-110">Result Types</span></span>  
 <span data-ttu-id="870ad-111">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="870ad-111">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="870ad-112">備註</span><span class="sxs-lookup"><span data-stu-id="870ad-112">Remarks</span></span>  
 <span data-ttu-id="870ad-113">如果 *number* 大於 *character_expression*的長度，函數會傳回 *character_expression*。</span><span class="sxs-lookup"><span data-stu-id="870ad-113">If *number* is greater than the length of *character_expression*, the function returns *character_expression*.</span></span>  
  
 <span data-ttu-id="870ad-114">如果 *number* 為零，則函數會傳回長度為 0 的字串。</span><span class="sxs-lookup"><span data-stu-id="870ad-114">If *number* is zero, the function returns a zero-length string.</span></span>  
  
 <span data-ttu-id="870ad-115">如果 *number* 為負數，則函數會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="870ad-115">If *number* is a negative number, the function returns an error.</span></span>  
  
 <span data-ttu-id="870ad-116">*number* 引數可採用變數和資料行。</span><span class="sxs-lookup"><span data-stu-id="870ad-116">The *number* argument can take variables and columns.</span></span>  
  
 <span data-ttu-id="870ad-117">LEFT 只適用於 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="870ad-117">LEFT works only with the DT_WSTR data type.</span></span> <span data-ttu-id="870ad-118">如果 *character_expression* 引數是字串常值或具有 DT_STR 資料類型的資料行，則該引數會在 LEFT 執行其作業前隱含轉換成 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="870ad-118">A *character_expression* argument that is a string literal or a data column with the DT_STR data type is implicitly cast to the DT_WSTR data type before LEFT performs its operation.</span></span> <span data-ttu-id="870ad-119">其他資料類型必須明確地轉換為 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="870ad-119">Other data types must be explicitly cast to the DT_WSTR data type.</span></span> <span data-ttu-id="870ad-120">如需詳細資訊，請參閱 [Integration Services 資料類型](../data-flow/integration-services-data-types.md)和[轉換 &#40;SSIS 運算式&#41;](cast-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="870ad-120">For more information, see [Integration Services Data Types](../data-flow/integration-services-data-types.md) and [Cast &#40;SSIS Expression&#41;](cast-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="870ad-121">如果其中一個引數為 Null，則 LEFT 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="870ad-121">LEFT returns a null result if either argument is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="870ad-122">運算式範例</span><span class="sxs-lookup"><span data-stu-id="870ad-122">Expression Examples</span></span>  
 <span data-ttu-id="870ad-123">下列範例會使用字串常值。</span><span class="sxs-lookup"><span data-stu-id="870ad-123">The following example uses a string literal.</span></span> <span data-ttu-id="870ad-124">傳回結果為 `"Mountain"`。</span><span class="sxs-lookup"><span data-stu-id="870ad-124">The return result is `"Mountain"`.</span></span>  
  
```  
LEFT("Mountain Bike", 8)  
```  
  
## <a name="see-also"></a><span data-ttu-id="870ad-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="870ad-125">See Also</span></span>  
 <span data-ttu-id="870ad-126">[RIGHT &#40;SSIS 運算式&#41;](right-ssis-expression.md) </span><span class="sxs-lookup"><span data-stu-id="870ad-126">[RIGHT &#40;SSIS Expression&#41;](right-ssis-expression.md) </span></span>  
 [<span data-ttu-id="870ad-127">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="870ad-127">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
