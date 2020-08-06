---
title: 在位置路徑中指定選取述詞 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- predicates [SQLXML]
- position-based filtering [SQLXML]
- XPath queries [SQLXML], location paths
- filtering [SQLXML]
- location path for XPath query
ms.assetid: dbef4cf4-a89b-4d7e-b72b-4062f7b29a80
author: rothja
ms.author: jroth
ms.openlocfilehash: d323558556fb05d350e48ea9218a8e9b8dc9b5c9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596583"
---
# <a name="specifying-selection-predicates-in-the-location-path-sqlxml-40"></a><span data-ttu-id="b8c52-102">在位置路徑 (SQLXML 4.0) 中指定選取述詞</span><span class="sxs-lookup"><span data-stu-id="b8c52-102">Specifying Selection Predicates in the Location Path (SQLXML 4.0)</span></span>
  <span data-ttu-id="b8c52-103">述詞會篩選與軸有關的節點集 (與 SELECT 陳述式中的 WHERE 子句相似)，</span><span class="sxs-lookup"><span data-stu-id="b8c52-103">A predicate filters a node-set with respect to an axis (similar to a WHERE clause in a SELECT statement).</span></span> <span data-ttu-id="b8c52-104">並指定在方括號之間。</span><span class="sxs-lookup"><span data-stu-id="b8c52-104">The predicate is specified between brackets.</span></span> <span data-ttu-id="b8c52-105">對於節點集內要篩選的每一個節點，該節點會當做內容節點，而且節點集內的節點數目會當做內容大小，然後評估述詞運算式。</span><span class="sxs-lookup"><span data-stu-id="b8c52-105">For each node in the node-set to be filtered, the predicate expression is evaluated with that node as the context node, with the number of nodes in the node-set as context size.</span></span> <span data-ttu-id="b8c52-106">如果述詞運算式評估該節點為 TRUE，則產生的節點集會包含該節點。</span><span class="sxs-lookup"><span data-stu-id="b8c52-106">If the predicate expression evaluates to TRUE for that node, the node is included in the resulting node-set.</span></span>  
  
 <span data-ttu-id="b8c52-107">XPath 也允許以位置為基礎的篩選。</span><span class="sxs-lookup"><span data-stu-id="b8c52-107">XPath also allows position-based filtering.</span></span> <span data-ttu-id="b8c52-108">評估為數字的述詞運算式會選取該序數節點。</span><span class="sxs-lookup"><span data-stu-id="b8c52-108">A predicate expression evaluating to a number selects that ordinal node.</span></span> <span data-ttu-id="b8c52-109">例如，位置路徑 `Customer[3]` 會傳回第三客戶。</span><span class="sxs-lookup"><span data-stu-id="b8c52-109">For example, the location path `Customer[3]` returns the third customer.</span></span> <span data-ttu-id="b8c52-110">但是不支援這類數值述詞，</span><span class="sxs-lookup"><span data-stu-id="b8c52-110">Such numeric predicates are not supported.</span></span> <span data-ttu-id="b8c52-111">只支援傳回布林值的述詞運算式。</span><span class="sxs-lookup"><span data-stu-id="b8c52-111">Only predicate expressions that return a Boolean result are supported.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b8c52-112">如需 XPath 的 xpath 實作為限制的詳細資訊，以及它與 W3C 規格之間的差異，請參閱[使用 XPath 查詢的簡介 &#40;SQLXML 4.0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="b8c52-112">For information about the limitations of this XPath implementation of XPath and the differences between it and the W3C specification, see [Introduction to Using XPath Queries &#40;SQLXML 4.0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md).</span></span>  
  
## <a name="selection-predicate-example-1"></a><span data-ttu-id="b8c52-113">選取述詞：範例1</span><span class="sxs-lookup"><span data-stu-id="b8c52-113">Selection Predicate: Example 1</span></span>  
 <span data-ttu-id="b8c52-114">下列 XPath 運算式 (位置路徑) 從目前內容節點選取所有 **\<Customer>** 具有**CustomerID**屬性且值為 ALFKI 的元素子系：</span><span class="sxs-lookup"><span data-stu-id="b8c52-114">The following XPath expression (location path) selects from the current context node all the **\<Customer>** element children that have the **CustomerID** attribute with value of ALFKI:</span></span>  
  
```  
/child::Customer[attribute::CustomerID="ALFKI"]  
```  
  
 <span data-ttu-id="b8c52-115">在這個 XPath 查詢中，`child` 和 `attribute` 是軸的名稱。</span><span class="sxs-lookup"><span data-stu-id="b8c52-115">In this XPath query, `child` and `attribute` are axis names.</span></span> <span data-ttu-id="b8c52-116">`Customer`是，如果是，節點測試 (TRUE `Customer` **\<element node>** ，因為 **\<element>** 是軸) 的主要節點類型 `child` 。</span><span class="sxs-lookup"><span data-stu-id="b8c52-116">`Customer` is the node test (TRUE if `Customer` is an **\<element node>**, because **\<element>** is the principal node type for the `child` axis).</span></span> <span data-ttu-id="b8c52-117">`attribute::CustomerID="ALFKI"` 是述詞。</span><span class="sxs-lookup"><span data-stu-id="b8c52-117">`attribute::CustomerID="ALFKI"` is the predicate.</span></span> <span data-ttu-id="b8c52-118">在述詞中， `attribute` 是軸，而 `CustomerID` 如果**CustomerID**是內容節點的屬性，則是節點測試 (TRUE，因為 **\<attribute>** 是軸) 的主要節點類型 `attribute` 。</span><span class="sxs-lookup"><span data-stu-id="b8c52-118">In the predicate, `attribute` is the axis and `CustomerID` is the node test (TRUE if **CustomerID** is an attribute of the context node, because **\<attribute>** is the principal node type of `attribute` axis).</span></span>  
  
 <span data-ttu-id="b8c52-119">使用縮寫語法，XPath 查詢也可以指定為：</span><span class="sxs-lookup"><span data-stu-id="b8c52-119">Using the abbreviated syntax, the XPath query can also be specified as:</span></span>  
  
```  
/Customer[@CustomerID="ALFKI"]  
```  
  
## <a name="selection-predicate-example-2"></a><span data-ttu-id="b8c52-120">選取述詞：範例2</span><span class="sxs-lookup"><span data-stu-id="b8c52-120">Selection Predicate: Example 2</span></span>  
 <span data-ttu-id="b8c52-121">下列 XPath 運算式 (位置路徑) 從目前內容節點選取所有 **\<Order>** 具有**SalesOrderID**屬性且值為1的孫系：</span><span class="sxs-lookup"><span data-stu-id="b8c52-121">The following XPath expression (location path) selects from the current context node all the **\<Order>** grandchildren that have the **SalesOrderID** attribute with the value 1:</span></span>  
  
```  
/child::Customer/child::Order[attribute::SalesOrderID="1"]  
```  
  
 <span data-ttu-id="b8c52-122">在這個 XPath 運算式中，`child` 和 `attribute` 是軸的名稱。</span><span class="sxs-lookup"><span data-stu-id="b8c52-122">In this XPath expression, `child` and `attribute` are the axis names.</span></span> <span data-ttu-id="b8c52-123">`Customer`、`Order` 和 `SalesOrderID` 是節點測試。</span><span class="sxs-lookup"><span data-stu-id="b8c52-123">`Customer`, `Order`, and `SalesOrderID` are the node tests.</span></span> <span data-ttu-id="b8c52-124">`attribute::OrderID="1"` 是述詞。</span><span class="sxs-lookup"><span data-stu-id="b8c52-124">`attribute::OrderID="1"` is the predicate.</span></span>  
  
 <span data-ttu-id="b8c52-125">使用縮寫語法，XPath 查詢也可以指定為：</span><span class="sxs-lookup"><span data-stu-id="b8c52-125">Using the abbreviated syntax, the XPath query can also be specified as:</span></span>  
  
```  
/Customer/Order[@SalesOrderID="1"]  
```  
  
## <a name="selection-predicate-example-3"></a><span data-ttu-id="b8c52-126">選取述詞：範例3</span><span class="sxs-lookup"><span data-stu-id="b8c52-126">Selection Predicate: Example 3</span></span>  
 <span data-ttu-id="b8c52-127">下列 XPath 運算式 (位置路徑) 從目前內容節點選取 **\<Customer>** 具有一或多個子系的所有子系 **\<ContactName>** ：</span><span class="sxs-lookup"><span data-stu-id="b8c52-127">The following XPath expression (location path) selects from the current context node all the **\<Customer>** children that have one or more **\<ContactName>** children:</span></span>  
  
```  
child::Customer[child::ContactName]  
```  
  
 <span data-ttu-id="b8c52-128">這個範例假設 **\<ContactName>** 是 XML 檔中專案的子專案 **\<Customer>** ，這在批註式 XSD 架構中稱為*元素中心對應*。</span><span class="sxs-lookup"><span data-stu-id="b8c52-128">This example assumes that the **\<ContactName>** is a child element of the **\<Customer>** element in the XML document, which is referred to as *element-centric mapping* in an annotated XSD schema.</span></span>  
  
 <span data-ttu-id="b8c52-129">在這個 XPath 運算式中，`child` 是軸的名稱。</span><span class="sxs-lookup"><span data-stu-id="b8c52-129">In this XPath expression, `child` is the axis name.</span></span> <span data-ttu-id="b8c52-130">`Customer`如果是節點，節點測試 (TRUE `Customer` **\<element>** ，因為 **\<element>** 是軸) 的主要節點類型 `child` 。</span><span class="sxs-lookup"><span data-stu-id="b8c52-130">`Customer` is the node test (TRUE if `Customer` is an **\<element>** node, because **\<element>** is the principal node type for `child` axis).</span></span> <span data-ttu-id="b8c52-131">`child::ContactName` 是述詞。</span><span class="sxs-lookup"><span data-stu-id="b8c52-131">`child::ContactName` is the predicate.</span></span> <span data-ttu-id="b8c52-132">在述詞中， `child` 是軸， `ContactName` 如果 `ContactName` 是節點) ，則是節點測試 (TRUE **\<element>** 。</span><span class="sxs-lookup"><span data-stu-id="b8c52-132">In the predicate, `child` is the axis and `ContactName` is the node test (TRUE if `ContactName` is an **\<element>** node).</span></span>  
  
 <span data-ttu-id="b8c52-133">此運算式只會傳回 **\<Customer>** 具有元素子系之內容節點的元素子系 **\<ContactName>** 。</span><span class="sxs-lookup"><span data-stu-id="b8c52-133">This expression returns only the **\<Customer>** element children of the context node that have **\<ContactName>** element children.</span></span>  
  
 <span data-ttu-id="b8c52-134">使用縮寫語法，XPath 查詢也可以指定為：</span><span class="sxs-lookup"><span data-stu-id="b8c52-134">Using the abbreviated syntax, the XPath query can also be specified as:</span></span>  
  
```  
Customer[ContactName]  
```  
  
## <a name="selection-predicate-example-4"></a><span data-ttu-id="b8c52-135">選取述詞：範例4</span><span class="sxs-lookup"><span data-stu-id="b8c52-135">Selection Predicate: Example 4</span></span>  
 <span data-ttu-id="b8c52-136">下列 XPath 運算式會選取 **\<Customer>** 不具有專案子系之內容節點的元素子系 **\<ContactName>** ：</span><span class="sxs-lookup"><span data-stu-id="b8c52-136">The following XPath expression selects **\<Customer>** element children of the context node that do not have **\<ContactName>** element children:</span></span>  
  
```  
child::Customer[not(child::ContactName)]  
```  
  
 <span data-ttu-id="b8c52-137">這個範例假設 **\<ContactName>** 是 **\<Customer>** XML 檔中元素的子專案，而且資料庫中不需要 [連絡人] 欄位。</span><span class="sxs-lookup"><span data-stu-id="b8c52-137">This example assumes that **\<ContactName>** is a child element of the **\<Customer>** element in the XML document, and the ContactName field is not required in the database.</span></span>  
  
 <span data-ttu-id="b8c52-138">在此範例中，`child` 為軸。</span><span class="sxs-lookup"><span data-stu-id="b8c52-138">In this example, `child` is the axis.</span></span> <span data-ttu-id="b8c52-139">`Customer`如果 `Customer` 是節點) ，節點測試 (為 TRUE \<element> 。</span><span class="sxs-lookup"><span data-stu-id="b8c52-139">`Customer` is the node test (TRUE if `Customer` is an \<element> node).</span></span> <span data-ttu-id="b8c52-140">`not(child::ContactName)` 是述詞。</span><span class="sxs-lookup"><span data-stu-id="b8c52-140">`not(child::ContactName)` is the predicate.</span></span> <span data-ttu-id="b8c52-141">在述詞中， `child` 是軸， `ContactName` 如果 `ContactName` 是節點) ，則是節點測試 (TRUE \<element> 。</span><span class="sxs-lookup"><span data-stu-id="b8c52-141">In the predicate, `child` is the axis and `ContactName` is the node test (TRUE if `ContactName` is an \<element> node).</span></span>  
  
 <span data-ttu-id="b8c52-142">使用縮寫語法，XPath 查詢也可以指定為：</span><span class="sxs-lookup"><span data-stu-id="b8c52-142">Using the abbreviated syntax, the XPath query can also be specified as:</span></span>  
  
```  
Customer[not(ContactName)]  
```  
  
## <a name="selection-predicate-example-5"></a><span data-ttu-id="b8c52-143">選取述詞：範例5</span><span class="sxs-lookup"><span data-stu-id="b8c52-143">Selection Predicate: Example 5</span></span>  
 <span data-ttu-id="b8c52-144">下列 XPath 運算式會從目前的內容節點中選取所有 **\<Customer>** 具有**CustomerID**屬性的子系：</span><span class="sxs-lookup"><span data-stu-id="b8c52-144">The following XPath expression selects from the current context node all the **\<Customer>** children that have the **CustomerID** attribute:</span></span>  
  
```  
child::Customer[attribute::CustomerID]  
```  
  
 <span data-ttu-id="b8c52-145">在此範例中， `child` 是軸，而 `Customer` 如果 `Customer` 是節點) ，則是節點測試 (TRUE \<element> 。</span><span class="sxs-lookup"><span data-stu-id="b8c52-145">In this example, `child` is the axis and `Customer` is node test (TRUE if `Customer` is an \<element> node).</span></span> <span data-ttu-id="b8c52-146">`attribute::CustomerID` 是述詞。</span><span class="sxs-lookup"><span data-stu-id="b8c52-146">`attribute::CustomerID` is the predicate.</span></span> <span data-ttu-id="b8c52-147">在述詞中， `attribute` 是軸，而 `CustomerID` 如果 `CustomerID` 是節點) ，則是述詞 (為 TRUE **\<attribute>** 。</span><span class="sxs-lookup"><span data-stu-id="b8c52-147">In the predicate, `attribute` is the axis and `CustomerID` is the predicate (TRUE if `CustomerID` is an **\<attribute>** node).</span></span>  
  
 <span data-ttu-id="b8c52-148">使用縮寫語法，XPath 查詢也可以指定為：</span><span class="sxs-lookup"><span data-stu-id="b8c52-148">Using the abbreviated syntax, the XPath query can also be specified as:</span></span>  
  
```  
Customer[@CustomerID]  
```  
  
## <a name="selection-predicate-example-6"></a><span data-ttu-id="b8c52-149">選取述詞：範例 6</span><span class="sxs-lookup"><span data-stu-id="b8c52-149">Selection Predicate: Example 6</span></span>  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] <span data-ttu-id="b8c52-150">SQLXML 4.0 支援在述詞中包含交叉乘積的 XPath 查詢，如下列範例所示：</span><span class="sxs-lookup"><span data-stu-id="b8c52-150">SQLXML 4.0 includes support for XPath queries that contain a cross-product in the predicate, as shown in the following example:</span></span>  
  
```  
Customer[Order/@OrderDate=Order/@ShipDate]  
```  
  
 <span data-ttu-id="b8c52-151">這個查詢會選取所有客戶，其方式是使用任何 `Order`，其中 `OrderDate` 要等於任何 `ShipDate` 的 `Order`。</span><span class="sxs-lookup"><span data-stu-id="b8c52-151">This query selects all customers with any `Order` for which the `OrderDate` equals the `ShipDate` of any `Order`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8c52-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8c52-152">See Also</span></span>  
 <span data-ttu-id="b8c52-153">[批註式 XSD 架構簡介 &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="b8c52-153">[Introduction to Annotated XSD Schemas &#40;SQLXML 4.0&#41;](../../sqlxml/annotated-xsd-schemas/introduction-to-annotated-xsd-schemas-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="b8c52-154">用戶端 XML 格式 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="b8c52-154">Client-side XML Formatting &#40;SQLXML 4.0&#41;</span></span>](../../sqlxml/formatting/client-side-xml-formatting-sqlxml-4-0.md)  
  
  
