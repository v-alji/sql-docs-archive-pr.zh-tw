---
title: 在位置路徑中指定節點測試 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], location paths
- principal node types [SQLXML]
- node tests [SQLXML]
- location path for XPath query
ms.assetid: f46c30bf-1e24-4435-9ac2-f8ba43a8ff94
author: rothja
ms.author: jroth
ms.openlocfilehash: 9d8535154f4b481c8a47bfdb8b801e3136a1ef0f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596588"
---
# <a name="specifying-a-node-test-in-the-location-path-sqlxml-40"></a><span data-ttu-id="f6daa-102">在位置路徑中指定節點測試 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="f6daa-102">Specifying a Node Test in the Location Path (SQLXML 4.0)</span></span>
  <span data-ttu-id="f6daa-103">節點測試會指定位置步驟所選取的節點類型。</span><span class="sxs-lookup"><span data-stu-id="f6daa-103">A node test specifies the node type selected by the location step.</span></span> <span data-ttu-id="f6daa-104">每個軸 (`child`、`parent`、`attribute` 或 `self`) 都有一個主要節點類型。</span><span class="sxs-lookup"><span data-stu-id="f6daa-104">Every axis (`child`, `parent`, `attribute`, or `self`) has a principal node type.</span></span> <span data-ttu-id="f6daa-105">若為 `attribute` 軸，主要節點類型為 **\<attribute>** 。</span><span class="sxs-lookup"><span data-stu-id="f6daa-105">For the `attribute` axis, the principal node type is **\<attribute>**.</span></span> <span data-ttu-id="f6daa-106">針對 `parent` 、 `child` 和 `self` 座標軸，主要節點類型為 **\<element>** 。</span><span class="sxs-lookup"><span data-stu-id="f6daa-106">For the `parent`, `child`, and `self` axes, the principal node type is **\<element>**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f6daa-107">不支援萬用字元節點測試 \* (例如 `child::*`)。</span><span class="sxs-lookup"><span data-stu-id="f6daa-107">The wildcard node test \* (for example, `child::*`) is not supported.</span></span>  
  
## <a name="node-test-example-1"></a><span data-ttu-id="f6daa-108">節點測試：範例1</span><span class="sxs-lookup"><span data-stu-id="f6daa-108">Node Test: Example 1</span></span>  
 <span data-ttu-id="f6daa-109">位置路徑會 `child::Customer` 選取 **\<Customer>** 內容節點的元素子系。</span><span class="sxs-lookup"><span data-stu-id="f6daa-109">The location path `child::Customer` selects **\<Customer>** element children of the context node.</span></span>  
  
 <span data-ttu-id="f6daa-110">在此範例中，`child` 為軸，而 `Customer` 為節點測試。</span><span class="sxs-lookup"><span data-stu-id="f6daa-110">In this example, `child` is the axis and `Customer` is the node test.</span></span> <span data-ttu-id="f6daa-111">軸的主要節點類型 `child` 是 **\<element>** 。</span><span class="sxs-lookup"><span data-stu-id="f6daa-111">The principal node type for the `child` axis is **\<element>**.</span></span> <span data-ttu-id="f6daa-112">因此，如果節點是節點，節點測試就是 TRUE **\<Customer>** **\<element>** 。</span><span class="sxs-lookup"><span data-stu-id="f6daa-112">Therefore, the node test is TRUE if the **\<Customer>** node is an **\<element>** node.</span></span> <span data-ttu-id="f6daa-113">如果內容節點沒有子系 **\<Customer>** ，則會傳回空的節點集。</span><span class="sxs-lookup"><span data-stu-id="f6daa-113">If the context node has no **\<Customer>** children, an empty set of nodes is returned.</span></span>  
  
## <a name="node-test-example-2"></a><span data-ttu-id="f6daa-114">節點測試：範例 2</span><span class="sxs-lookup"><span data-stu-id="f6daa-114">Node Test: Example 2</span></span>  
 <span data-ttu-id="f6daa-115">位置路徑會 `attribute::CustomerID` 選取內容節點的**CustomerID**屬性。</span><span class="sxs-lookup"><span data-stu-id="f6daa-115">The location path `attribute::CustomerID` selects the **CustomerID** attribute of the context node.</span></span>  
  
 <span data-ttu-id="f6daa-116">在此範例中，`attribute` 為軸，而 `CustomerID` 為節點測試。</span><span class="sxs-lookup"><span data-stu-id="f6daa-116">In the example, `attribute` is the axis and `CustomerID` is the node test.</span></span> <span data-ttu-id="f6daa-117">軸的主要節點類型 `attribute` 是 **\<attribute>** 。</span><span class="sxs-lookup"><span data-stu-id="f6daa-117">The principal node type of the `attribute` axis is **\<attribute>**.</span></span> <span data-ttu-id="f6daa-118">因此，如果**CustomerID**為節點，則節點測試為 TRUE **\<attribute>** 。</span><span class="sxs-lookup"><span data-stu-id="f6daa-118">Therefore, the node test is TRUE if **CustomerID** is an **\<attribute>** node.</span></span> <span data-ttu-id="f6daa-119">如果內容節點沒有**CustomerID**，則會傳回空的節點集。</span><span class="sxs-lookup"><span data-stu-id="f6daa-119">If the context node has no **CustomerID**, an empty set of nodes is returned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f6daa-120">在此 XPath 的執行中，如果位置步驟參考的 **\<element>** **\<attribute>** 是或未在架構中宣告的類型，則會產生錯誤。</span><span class="sxs-lookup"><span data-stu-id="f6daa-120">In this implementation of XPath, if a location step refers to an **\<element>** or an **\<attribute>** type that is not declared in the schema, an error is generated.</span></span> <span data-ttu-id="f6daa-121">這與 MSXML 中的 XPath 實作不同，該實作會傳回空的節點集。</span><span class="sxs-lookup"><span data-stu-id="f6daa-121">This is different from the implementation of XPath in MSXML, which returns an empty node set.</span></span>  
  
## <a name="abbreviated-syntax-for-the-axes"></a><span data-ttu-id="f6daa-122">軸的縮寫語法</span><span class="sxs-lookup"><span data-stu-id="f6daa-122">Abbreviated Syntax for the Axes</span></span>  
 <span data-ttu-id="f6daa-123">位置路徑的以下縮寫語法有受到支援：</span><span class="sxs-lookup"><span data-stu-id="f6daa-123">The following abbreviated syntax for the location path is supported:</span></span>  
  
-   <span data-ttu-id="f6daa-124">`attribute::` 可縮寫成 `@`。</span><span class="sxs-lookup"><span data-stu-id="f6daa-124">`attribute::` can be abbreviated to `@`.</span></span>  
  
     <span data-ttu-id="f6daa-125">位置路徑 `Customer[@CustomerID="ALFKI"]` 與 `child::Customer[attribute::CustomerID="ALFKI"]` 相同。</span><span class="sxs-lookup"><span data-stu-id="f6daa-125">The location path `Customer[@CustomerID="ALFKI"]` is the same as `child::Customer[attribute::CustomerID="ALFKI"]`.</span></span>  
  
-   <span data-ttu-id="f6daa-126">位置步驟中可省略 `child::`。</span><span class="sxs-lookup"><span data-stu-id="f6daa-126">`child::` can be omitted from a location step.</span></span>  
  
     <span data-ttu-id="f6daa-127">因此，`child` 是預設軸。</span><span class="sxs-lookup"><span data-stu-id="f6daa-127">Thus, `child` is the default axis.</span></span> <span data-ttu-id="f6daa-128">位置路徑 `Customer/Order` 與 `child::Customer/child::Order` 相同。</span><span class="sxs-lookup"><span data-stu-id="f6daa-128">The location path `Customer/Order` is the same as `child::Customer/child::Order`.</span></span>  
  
-   <span data-ttu-id="f6daa-129">`self::node()` 可以縮寫成一個句號 (.)，而 `parent::node()` 可縮寫成兩個句號 (..)。</span><span class="sxs-lookup"><span data-stu-id="f6daa-129">`self::node()` can be abbreviated to one period (.), and `parent::node()` can be abbreviated to two periods (..).</span></span>  
  
  
