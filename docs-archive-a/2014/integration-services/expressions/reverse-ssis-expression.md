---
title: REVERSE (SSIS 運算式) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- REVERSE function
- reverse character expressions
ms.assetid: bcebcc55-7247-4896-8f53-4d582d58cfb4
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 2ace136eed0abcb9df7b25d9370c46d7556c1d48
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701410"
---
# <a name="reverse-ssis-expression"></a><span data-ttu-id="2aceb-102">REVERSE (SSIS 運算式)</span><span class="sxs-lookup"><span data-stu-id="2aceb-102">REVERSE (SSIS Expression)</span></span>
  <span data-ttu-id="2aceb-103">傳回反向順序的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="2aceb-103">Returns a character expression in reverse order.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2aceb-104">語法</span><span class="sxs-lookup"><span data-stu-id="2aceb-104">Syntax</span></span>  
  
```  
  
REVERSE(character_expression)  
```  
  
## <a name="arguments"></a><span data-ttu-id="2aceb-105">引數</span><span class="sxs-lookup"><span data-stu-id="2aceb-105">Arguments</span></span>  
 <span data-ttu-id="2aceb-106">*character_expression*</span><span class="sxs-lookup"><span data-stu-id="2aceb-106">*character_expression*</span></span>  
 <span data-ttu-id="2aceb-107">是要反向的字元運算式。</span><span class="sxs-lookup"><span data-stu-id="2aceb-107">Is a character expression to be reversed.</span></span>  
  
## <a name="result-types"></a><span data-ttu-id="2aceb-108">結果類型</span><span class="sxs-lookup"><span data-stu-id="2aceb-108">Result Types</span></span>  
 <span data-ttu-id="2aceb-109">DT_WSTR</span><span class="sxs-lookup"><span data-stu-id="2aceb-109">DT_WSTR</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2aceb-110">備註</span><span class="sxs-lookup"><span data-stu-id="2aceb-110">Remarks</span></span>  
 <span data-ttu-id="2aceb-111">*character_expression* 引數必須是 DT_WSTR 資料類型。</span><span class="sxs-lookup"><span data-stu-id="2aceb-111">The *character_expression* argument must have the DT_WSTR data type.</span></span>  
  
 <span data-ttu-id="2aceb-112">如果 *character_expression* 為 Null，則 REVERSE 會傳回 Null 結果。</span><span class="sxs-lookup"><span data-stu-id="2aceb-112">REVERSE returns a null result if *character_expression* is null.</span></span>  
  
## <a name="expression-examples"></a><span data-ttu-id="2aceb-113">運算式範例</span><span class="sxs-lookup"><span data-stu-id="2aceb-113">Expression Examples</span></span>  
 <span data-ttu-id="2aceb-114">這個範例使用字串常值。</span><span class="sxs-lookup"><span data-stu-id="2aceb-114">This example uses a string literal.</span></span> <span data-ttu-id="2aceb-115">傳回結果為「ekiB niatnuoM」。</span><span class="sxs-lookup"><span data-stu-id="2aceb-115">The return result is "ekiB niatnuoM".</span></span>  
  
```  
REVERSE("Mountain Bike")  
```  
  
 <span data-ttu-id="2aceb-116">這個範例使用變數。</span><span class="sxs-lookup"><span data-stu-id="2aceb-116">This example uses a variable.</span></span> <span data-ttu-id="2aceb-117">如果 **Name** 包含 Touring Bike，則傳回結果為 "ekiB gniruoT"。</span><span class="sxs-lookup"><span data-stu-id="2aceb-117">If **Name** contains Touring Bike, the return result is "ekiB gniruoT".</span></span>  
  
```  
REVERSE(@Name)  
```  
  
## <a name="see-also"></a><span data-ttu-id="2aceb-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2aceb-118">See Also</span></span>  
 [<span data-ttu-id="2aceb-119">函數 &#40;SSIS 運算式&#41;</span><span class="sxs-lookup"><span data-stu-id="2aceb-119">Functions &#40;SSIS Expression&#41;</span></span>](functions-ssis-expression.md)  
  
  
