---
title: 字串填補 (SSIS) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- padding strings [Integration Services]
- expressions [Integration Services], string padding
- string padding
ms.assetid: d3fed73d-e0d4-4c67-9355-fb7083a72dd6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3985fd1b2f29260e2313a761797d2528f5d0e328
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701365"
---
# <a name="string-padding-ssis"></a><span data-ttu-id="af4c8-102">字串填補 (SSIS)</span><span class="sxs-lookup"><span data-stu-id="af4c8-102">String Padding (SSIS)</span></span>
  <span data-ttu-id="af4c8-103">運算式評估工具不會檢查字串是否包含開頭和尾端空白，也不會在比較之前填補字串，使其長度相等。</span><span class="sxs-lookup"><span data-stu-id="af4c8-103">The expression evaluator does not check if a string contains leading and trailing spaces, and it does not pad strings to make them the same length before it compares them.</span></span> <span data-ttu-id="af4c8-104">如果運算式需要字串填補，您可使用 + 運算子串連資料行的值和空白字串。</span><span class="sxs-lookup"><span data-stu-id="af4c8-104">If expressions requires string padding, you can use the + operator to concatenate column values and blank strings.</span></span> <span data-ttu-id="af4c8-105">如需詳細資訊，請參閱 [+ &#40;串連&#41; &#40;SSIS 運算式&#41;](concatenate-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="af4c8-105">For more information, see [+ &#40;Concatenate&#41; &#40;SSIS Expression&#41;](concatenate-ssis-expression.md).</span></span>  
  
 <span data-ttu-id="af4c8-106">換句話說，如果您要移除空白，運算式評估工具提供 LTRIM、RTRIM 和 TRIM 函數，可用來移除開頭和 (或)尾端空白。</span><span class="sxs-lookup"><span data-stu-id="af4c8-106">On the other hand, if you want to remove spaces, the expression evaluator provides the LTRIM, RTRIM, and TRIM functions, which remove leading or trailing spaces, or both.</span></span> <span data-ttu-id="af4c8-107">如需詳細資訊，請參閱 [LTRIM &#40;SSIS 運算式&#41;](trim-ssis-expression.md)[RTRIM &#40;SSIS 運算式&#41;](rtrim-ssis-expression.md)，和 [TRIM &#40;SSIS 運算式&#41;](trim-ssis-expression.md)。</span><span class="sxs-lookup"><span data-stu-id="af4c8-107">For more information, see [LTRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md), [RTRIM &#40;SSIS Expression&#41;](rtrim-ssis-expression.md), and [TRIM &#40;SSIS Expression&#41;](trim-ssis-expression.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="af4c8-108">LEN 函數的計數中包含開頭和尾端空白。</span><span class="sxs-lookup"><span data-stu-id="af4c8-108">The LEN function includes leading and trailing blanks in its count.</span></span>  
  
## <a name="related-content"></a><span data-ttu-id="af4c8-109">相關內容</span><span class="sxs-lookup"><span data-stu-id="af4c8-109">Related Content</span></span>  
 <span data-ttu-id="af4c8-110">pragmaticworks.com 上的技術文件： [SSIS 運算式小抄](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet
)</span><span class="sxs-lookup"><span data-stu-id="af4c8-110">Technical article, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet
), on pragmaticworks.com</span></span>  
  
  
