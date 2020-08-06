---
title: 支援的 MDX (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- MDX [Analysis Services], statements
- MDX [Analysis Services], functions
ms.assetid: 308bc0b3-4fd6-4435-972b-5e40d9e3c99b
author: minewiskan
ms.author: owend
ms.openlocfilehash: 17e8df6a2aa6da6b88a07a2abdef99d6ea03d8eb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705594"
---
# <a name="supported-mdx-mdx"></a><span data-ttu-id="25737-102">支援的 MDX (MDX)</span><span class="sxs-lookup"><span data-stu-id="25737-102">Supported MDX (MDX)</span></span>
  <span data-ttu-id="25737-103">多維度運算式 (MDX) 指令碼內支援下列陳述式及函數：</span><span class="sxs-lookup"><span data-stu-id="25737-103">The following statements and functions are supported within Multidimensional Expressions (MDX) Script:</span></span>  
  
 [<span data-ttu-id="25737-104">&#40;註解&#41; &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="25737-104">&#40;Comment&#41; &#40;MDX&#41;</span></span>](/sql/mdx/comment-mdx)  
  
 [<span data-ttu-id="25737-105">-- &#40;註解&#41; &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="25737-105">-- &#40;Comment&#41; &#40;MDX&#41;</span></span>](/sql/mdx/comment-mdx)  
  
 [<span data-ttu-id="25737-106">註解 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="25737-106">Comment &#40;MDX&#41;</span></span>](/sql/mdx/comment-mdx)  
  
 [<span data-ttu-id="25737-107">ALTER CUBE 陳述式 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="25737-107">ALTER CUBE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-alter-cube)  
  
> [!NOTE]  
>  <span data-ttu-id="25737-108">MDX 指令碼中只支援改變預設成員。</span><span class="sxs-lookup"><span data-stu-id="25737-108">Only altering the default member is supported in MDX Scripting.</span></span>  
  
 [<span data-ttu-id="25737-109">CALCULATE 陳述式 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="25737-109">CALCULATE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-calculate)  
  
 [<span data-ttu-id="25737-110">CASE 陳述式 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="25737-110">CASE Statement &#40;MDX&#41;</span></span>](/sql/mdx/case-statement-mdx)  
  
 [<span data-ttu-id="25737-111">CREATE CELL CALCULATION 陳述式 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="25737-111">CREATE CELL CALCULATION Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-create-cell-calculation)  
  
 [<span data-ttu-id="25737-112">CREATE MEMBER 陳述式 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="25737-112">CREATE MEMBER Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-create-member)  
  
 [<span data-ttu-id="25737-113">CREATE SET 陳述式 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="25737-113">CREATE SET Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-data-definition-create-set)  
  
 [<span data-ttu-id="25737-114">EXISTING 關鍵字 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="25737-114">EXISTING Keyword &#40;MDX&#41;</span></span>](mdx-query-existing-keyword.md)  
  
 [<span data-ttu-id="25737-115">FREEZE 陳述式 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="25737-115">FREEZE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-freeze)  
  
 [<span data-ttu-id="25737-116">IF 陳述式 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="25737-116">IF Statement  &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-if)  
  
 [<span data-ttu-id="25737-117">此 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="25737-117">This &#40;MDX&#41;</span></span>](/sql/mdx/this-mdx)  
  
> [!NOTE]  
>  <span data-ttu-id="25737-118">MDX 支援對以下資料格屬性進行指派：`BACK_COLOR`、`FORE_COLOR`、`FORMAT_STRING`、`FONT_FLAGS`、`FONT_NAME` 與 `FONT_SIZE`。</span><span class="sxs-lookup"><span data-stu-id="25737-118">MDX supports assignment to the following cell properties: `BACK_COLOR`, `FORE_COLOR`, `FORMAT_STRING`, `FONT_FLAGS`, `FONT_NAME`, and `FONT_SIZE`.</span></span> <span data-ttu-id="25737-119">如需詳細資訊，請參閱[使用資料格屬性 &#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="25737-119">For more information, see [Using Cell Properties &#40;MDX&#41;](mdx-cell-properties-using-cell-properties.md).</span></span> <span data-ttu-id="25737-120">MDX 也支援對 `NON_EMPTY_BEHAVIOR` [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member)語句的屬性進行指派。</span><span class="sxs-lookup"><span data-stu-id="25737-120">MDX also supports assignment to the `NON_EMPTY_BEHAVIOR` property of the [CREATE MEMBER](/sql/mdx/mdx-data-definition-create-member) statement.</span></span>  
  
 [<span data-ttu-id="25737-121">SCOPE 陳述式 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="25737-121">SCOPE Statement &#40;MDX&#41;</span></span>](/sql/mdx/mdx-scripting-scope)  
  
## <a name="see-also"></a><span data-ttu-id="25737-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="25737-122">See Also</span></span>  
 [<span data-ttu-id="25737-123">基本 MDX 指令碼 &#40;MDX&#41;</span><span class="sxs-lookup"><span data-stu-id="25737-123">The Basic MDX Script &#40;MDX&#41;</span></span>](the-basic-mdx-script-mdx.md)  
  
  
