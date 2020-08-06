---
title: 在查詢中建立 Cube 內容 (MDX) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- cubes [Analysis Services], MDX
- MDX [Analysis Services], cube context
- SELECT statement [MDX]
- Multidimensional Expressions [Analysis Services], cube context
- queries [MDX], cube context
ms.assetid: 79d6a1e8-2825-4eb9-97df-5071aecae8f0
author: minewiskan
ms.author: owend
ms.openlocfilehash: 72ae6e19f879651feb47841d70b444e9f845c74e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686503"
---
# <a name="establishing-cube-context-in-a-query-mdx"></a><span data-ttu-id="7dfb6-102">建立查詢中的 Cube 內容 (MDX)</span><span class="sxs-lookup"><span data-stu-id="7dfb6-102">Establishing Cube Context in a Query (MDX)</span></span>
  <span data-ttu-id="7dfb6-103">每個  MDX 查詢都會在指定的 Cube 內容內執行。</span><span class="sxs-lookup"><span data-stu-id="7dfb6-103">Every MDX query runs within a specified cube context.</span></span> <span data-ttu-id="7dfb6-104">此內容定義在查詢內由運算式評估的成員。</span><span class="sxs-lookup"><span data-stu-id="7dfb6-104">This context defines the members that are evaluated by the expressions within the query.</span></span>  
  
 <span data-ttu-id="7dfb6-105">在 SELECT 陳述式中，FROM 子句可決定 Cube 內容。</span><span class="sxs-lookup"><span data-stu-id="7dfb6-105">In the SELECT statement, the FROM clause determines the cube context.</span></span> <span data-ttu-id="7dfb6-106">此內容可以是整個 Cube 或只是 Cube 的一個 Subcube。</span><span class="sxs-lookup"><span data-stu-id="7dfb6-106">This context can be the whole cube or just a subcube from that cube.</span></span> <span data-ttu-id="7dfb6-107">透過 FROM 子句取得指定的 Cube 內容，您可以使用其他函數來擴充或限制內容。</span><span class="sxs-lookup"><span data-stu-id="7dfb6-107">Having specified cube context through the FROM clause, you can use additional functions to expand or restrict that context.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7dfb6-108">您也可以使用 SCOPE 與 CALCULATE 陳述式，管理 MDX 指令碼內的 Cube 內容。</span><span class="sxs-lookup"><span data-stu-id="7dfb6-108">The SCOPE and CALCULATE statements also let you manage cube context from within an MDX script.</span></span> <span data-ttu-id="7dfb6-109">如需詳細資訊，請參閱 [MDX 指令碼基礎觀念 &#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7dfb6-109">For more information, see [MDX Scripting Fundamentals &#40;Analysis Services&#41;](mdx-scripting-fundamentals-analysis-services.md).</span></span>  
  
## <a name="from-clause-syntax"></a><span data-ttu-id="7dfb6-110">FROM 子句語法</span><span class="sxs-lookup"><span data-stu-id="7dfb6-110">FROM Clause Syntax</span></span>  
 <span data-ttu-id="7dfb6-111">以下語法描述 FROM 子句：</span><span class="sxs-lookup"><span data-stu-id="7dfb6-111">The following syntax describes the FROM clause:</span></span>  
  
```  
<SELECT subcube clause> ::=  
   Cube_Identifier |   
   (SELECT [  
      * |   
      ( <SELECT query axis clause> [ , <SELECT query axis clause> ... ] ) ]   
   FROM <SELECT subcube clause> <SELECT slicer axis clause> )  
```  
  
 <span data-ttu-id="7dfb6-112">請注意，在此語法中，描述執行 SELECT 陳述式所在的 Cube 或 Subcube 是 `<SELECT subcube clause>` 子句。</span><span class="sxs-lookup"><span data-stu-id="7dfb6-112">In this syntax, notice that it is the `<SELECT subcube clause>` clause that describes the cube or subcube on which the SELECT statement is executed.</span></span>  
  
 <span data-ttu-id="7dfb6-113">針對整個 Adventure Works 範例 Cube 執行的 FROM 子句，就是簡單的 FROM 子句範例。</span><span class="sxs-lookup"><span data-stu-id="7dfb6-113">A simple example of a FROM clause would be one that runs against the entire Adventure Works sample cube.</span></span> <span data-ttu-id="7dfb6-114">這類 FROM 子句可有以下格式：</span><span class="sxs-lookup"><span data-stu-id="7dfb6-114">Such a FROM clause would have the following format:</span></span>  
  
```  
FROM [Adventure Works]  
```  
  
 <span data-ttu-id="7dfb6-115">如需 MDX SELECT 陳述式的 FROM 子句詳細資訊，請參閱 [SELECT 陳述式 &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select)。</span><span class="sxs-lookup"><span data-stu-id="7dfb6-115">For more information about the FROM clause in the MDX SELECT statement, see [SELECT Statement &#40;MDX&#41;](/sql/mdx/mdx-data-manipulation-select).</span></span>  
  
## <a name="refining-the-context"></a><span data-ttu-id="7dfb6-116">精簡內容</span><span class="sxs-lookup"><span data-stu-id="7dfb6-116">Refining the Context</span></span>  
 <span data-ttu-id="7dfb6-117">雖然 FROM 子句如同在單一 Cube 內指定 Cube 內容，但您要一次處理多個 Cube 的資料不會受到限制。</span><span class="sxs-lookup"><span data-stu-id="7dfb6-117">Although the FROM clause specifies the cube context as within a single cube, this does not have to limit you from working with data from more than one cube at a time.</span></span>  
  
 <span data-ttu-id="7dfb6-118">您可以使用 MDX [LookupCube](/sql/mdx/lookupcube-mdx) 函數來擷取 Cube 內容之外的 Cube 資料。</span><span class="sxs-lookup"><span data-stu-id="7dfb6-118">You can use the MDX [LookupCube](/sql/mdx/lookupcube-mdx) function to retrieve data from cubes outside the cube context.</span></span> <span data-ttu-id="7dfb6-119">此外，例如可用的 [Filter](/sql/mdx/filter-mdx) 函數，允許在評估查詢時暫時限制內容。</span><span class="sxs-lookup"><span data-stu-id="7dfb6-119">Additionally, functions such as the [Filter](/sql/mdx/filter-mdx) function, are available that allow temporary restriction of the context while evaluating the query.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7dfb6-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7dfb6-120">See Also</span></span>  
 [<span data-ttu-id="7dfb6-121">MDX 查詢基礎觀念 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7dfb6-121">MDX Query Fundamentals &#40;Analysis Services&#41;</span></span>](mdx-query-fundamentals-analysis-services.md)  
  
  
