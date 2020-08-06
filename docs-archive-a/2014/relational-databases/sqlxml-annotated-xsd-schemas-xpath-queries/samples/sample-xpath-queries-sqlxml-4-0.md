---
title: " (SQLXML 4.0) 的範例 XPath 查詢 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- examples [SQLXML], XPath
- sample applications [SQLXML]
- sample XPath queries [SQLXML]
- mapping schema [SQLXML], queries
- XPath queries [SQLXML], samples
ms.assetid: 1595c2d4-0e9c-4969-84c8-a793a32df57d
author: rothja
ms.author: jroth
ms.openlocfilehash: 08ed32433e9bed4cc1542d6700ad73dc96f3c2dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585238"
---
# <a name="sample-xpath-queries-sqlxml-40"></a><span data-ttu-id="75dd3-102">範例 XPath 查詢 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="75dd3-102">Sample XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="75dd3-103">本章節將提供 SQLXML 4.0 之 XPath 查詢的範例。</span><span class="sxs-lookup"><span data-stu-id="75dd3-103">This section provides examples of XPath queries for SQLXML 4.0.</span></span> <span data-ttu-id="75dd3-104">為了提供說明，這些範例 XPath 查詢都指定於使用 ADO 所執行的範本中。</span><span class="sxs-lookup"><span data-stu-id="75dd3-104">For illustration purposes, these example XPath queries are specified in a template executed using ADO.</span></span> <span data-ttu-id="75dd3-105">因此，您必須使用本節所提供的對應結構描述檔案 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="75dd3-105">Therefore, you must use a mapping schema file, SampleSchema1.xml, which is also provided in this section.</span></span> <span data-ttu-id="75dd3-106">將這個檔案儲存在您存放範本的目錄中。</span><span class="sxs-lookup"><span data-stu-id="75dd3-106">Save this file in the directory where your templates are stored.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="75dd3-107">本節的範例查詢會依據查詢所執行的 XPath 作業類型分組。</span><span class="sxs-lookup"><span data-stu-id="75dd3-107">The sample queries in this section are grouped by the type of XPath operation that is performed by the query.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="75dd3-108">本節內容</span><span class="sxs-lookup"><span data-stu-id="75dd3-108">In This Section</span></span>  
 [<span data-ttu-id="75dd3-109">XPath 範例的批註式 XSD 架構範例 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="75dd3-109">Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;</span></span>](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)  
 <span data-ttu-id="75dd3-110">使用這個檔案搭配本節所提供的 XPath 查詢範例。</span><span class="sxs-lookup"><span data-stu-id="75dd3-110">Use this file with the XPath query examples provided in this section.</span></span>  
  
 [<span data-ttu-id="75dd3-111">在 XPath 查詢中指定軸 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="75dd3-111">Specifying Axes in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-axes-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="75dd3-112">說明如何在 XPath 查詢中指定軸。</span><span class="sxs-lookup"><span data-stu-id="75dd3-112">Illustrates how axes are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="75dd3-113">在 XPath 查詢中指定布林值述詞 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="75dd3-113">Specifying Boolean-Valued Predicates in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-boolean-valued-predicates-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="75dd3-114">說明如何在 XPath 查詢中指定布林值述詞。</span><span class="sxs-lookup"><span data-stu-id="75dd3-114">Illustrates how Boolean-valued predicates are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="75dd3-115">在 XPath 查詢中指定關聯式運算子 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="75dd3-115">Specifying Relational Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-relational-operators-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="75dd3-116">說明如何在 XPath 查詢中指定關係運算子。</span><span class="sxs-lookup"><span data-stu-id="75dd3-116">Illustrates how relational operators are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="75dd3-117">在 XPath 查詢中指定算術運算子 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="75dd3-117">Specifying Arithmetic Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-arithmetic-operators-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="75dd3-118">說明如何在 XPath 查詢中指定算術運算子。</span><span class="sxs-lookup"><span data-stu-id="75dd3-118">Illustrates how arithmetic operators are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="75dd3-119">在 XPath 查詢中指定明確轉換函數 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="75dd3-119">Specifying Explicit Conversion Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="75dd3-120">說明如何在 XPath 查詢中指定明確轉換函數。</span><span class="sxs-lookup"><span data-stu-id="75dd3-120">Illustrates how explicit conversion functions are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="75dd3-121">在 XPath 查詢中指定布林運算子 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="75dd3-121">Specifying Boolean Operators in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-boolean-operators-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="75dd3-122">說明如何在 XPath 查詢中指定布林運算子。</span><span class="sxs-lookup"><span data-stu-id="75dd3-122">Illustrates how Boolean operators are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="75dd3-123">在 &#40;SQLXML 4.0&#41;的 XPath 查詢中指定布耳函數</span><span class="sxs-lookup"><span data-stu-id="75dd3-123">Specifying Boolean Functions in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-boolean-functions-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="75dd3-124">說明如何在 XPath 查詢中指定布林函數。</span><span class="sxs-lookup"><span data-stu-id="75dd3-124">Illustrates how Boolean functions are specified in XPath queries.</span></span>  
  
 [<span data-ttu-id="75dd3-125">在 XPath 查詢中指定 XPath 變數 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="75dd3-125">Specifying XPath Variables in XPath Queries &#40;SQLXML 4.0&#41;</span></span>](specifying-xpath-variables-in-xpath-queries-sqlxml-4-0.md)  
 <span data-ttu-id="75dd3-126">說明如何在 XPath 查詢中指定 XPath 變數。</span><span class="sxs-lookup"><span data-stu-id="75dd3-126">Illustrates how XPath variables are specified in XPath queries.</span></span>  
  
  
