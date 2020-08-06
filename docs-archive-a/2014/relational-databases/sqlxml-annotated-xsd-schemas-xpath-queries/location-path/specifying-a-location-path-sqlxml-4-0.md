---
title: 指定位置路徑 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- absolute location path
- node-set [SQLXML]
- XPath queries [SQLXML], location paths
- relative location path [SQLXML]
- location path for XPath query
ms.assetid: a23a2b75-bc69-49f0-99db-05e14dc15bc0
author: rothja
ms.author: jroth
ms.openlocfilehash: 4dfa1717afe55c1599ccaba4b5d044c6e5a20e84
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596590"
---
# <a name="specifying-a-location-path-sqlxml-40"></a><span data-ttu-id="5ff8b-102">指定位置路徑 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="5ff8b-102">Specifying a Location Path (SQLXML 4.0)</span></span>
  <span data-ttu-id="5ff8b-103">XPath 查詢會以運算式的形式指定。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-103">XPath queries are specified in the form of an expression.</span></span> <span data-ttu-id="5ff8b-104">運算式有各種不同的類型。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-104">There are various kinds of expressions.</span></span> <span data-ttu-id="5ff8b-105">位置路徑是一個運算式，可用來選取相對於內容節點的一組節點。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-105">A location path is an expression that selects a set of nodes relative to the context node.</span></span> <span data-ttu-id="5ff8b-106">評估位置路徑的結果為節點集。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-106">The result of evaluating a location path is a node-set.</span></span>  
  
## <a name="types-of-location-paths"></a><span data-ttu-id="5ff8b-107">位置路徑的類型</span><span class="sxs-lookup"><span data-stu-id="5ff8b-107">Types of Location Paths</span></span>  
 <span data-ttu-id="5ff8b-108">位置路徑可以是下列其中一個形式：</span><span class="sxs-lookup"><span data-stu-id="5ff8b-108">A location path can take either of these forms:</span></span>  
  
-   <span data-ttu-id="5ff8b-109">**絕對位置路徑**</span><span class="sxs-lookup"><span data-stu-id="5ff8b-109">**Absolute location path**</span></span>  
  
     <span data-ttu-id="5ff8b-110">絕對位置路徑會從文件的根節點開始。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-110">An absolute location path starts at the root node of the document.</span></span> <span data-ttu-id="5ff8b-111">其中包含一條斜線 (/)，後面選擇性地加上一個相對位置路徑。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-111">It consists of a slash mark (/) optionally followed by a relative location path.</span></span> <span data-ttu-id="5ff8b-112">斜線 (/) 會選取文件的根節點。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-112">The slash mark (/) selects the root node of the document.</span></span>  
  
-   <span data-ttu-id="5ff8b-113">**相對位置路徑**</span><span class="sxs-lookup"><span data-stu-id="5ff8b-113">**Relative location path**</span></span>  
  
     <span data-ttu-id="5ff8b-114">相對位置路徑會從文件中的內容節點開始。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-114">A relative location path starts at the context node in the document.</span></span> <span data-ttu-id="5ff8b-115">位置路徑包含一或多個位置步驟的序列，而且每個位置步驟都以斜線 (/) 分隔。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-115">A location path consists of a sequence of one or more location steps separated by a slash mark (/).</span></span> <span data-ttu-id="5ff8b-116">每個步驟都會選取相對於內容節點的一組節點。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-116">Each step selects a set of nodes relative to the context node.</span></span> <span data-ttu-id="5ff8b-117">步驟的初始序列會選取一組相對於內容節點的節點。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-117">The initial sequence of steps selects a set of nodes relative to a context node.</span></span> <span data-ttu-id="5ff8b-118">該集合中的每個節點都會當做下列步驟的內容節點使用。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-118">Each node in that set is used as a context node for the following step.</span></span> <span data-ttu-id="5ff8b-119">系統會加入由該步驟識別的節點集合。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-119">The sets of nodes identified by that step are joined.</span></span> <span data-ttu-id="5ff8b-120">例如， **child：： Order/child：： OrderDetail**會選取 **\<OrderDetail>** **\<Order>** 內容節點之元素子系的專案子系。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-120">For example, **child::Order/child::OrderDetail** selects the **\<OrderDetail>** element children of the **\<Order>** element children of the context node.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="5ff8b-121">在 XPath 的 SQLXML 4.0 實作中，即使 XPath 明顯地不是絕對的，每個 XPath 查詢都會從根內容開始。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-121">In the SQLXML 4.0 implementation of XPath, every XPath query begins at the root context, even if the XPath is not explicitly absolute.</span></span> <span data-ttu-id="5ff8b-122">例如，系統會將 "Customer" 開頭的 XPath 查詢視為 "/Customer"。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-122">For example, an XPath query beginning with "Customer" is treated as "/Customer".</span></span> <span data-ttu-id="5ff8b-123">在 XPath 查詢**客戶 [訂單]** 中，客戶會從根內容開始，但訂單會從客戶內容開始。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-123">In the XPath query **Customer[Order]**, Customer begins at the root context, but Order begins at the Customer context.</span></span> <span data-ttu-id="5ff8b-124">如需詳細資訊，請參閱[使用 XPath 查詢的簡介 &#40;SQLXML 4.0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-124">For more information, see [Introduction to Using XPath Queries &#40;SQLXML 4.0&#41;](../introduction-to-using-xpath-queries-sqlxml-4-0.md).</span></span>  
  
## <a name="location-steps"></a><span data-ttu-id="5ff8b-125">位置步驟</span><span class="sxs-lookup"><span data-stu-id="5ff8b-125">Location Steps</span></span>  
 <span data-ttu-id="5ff8b-126">位置路徑 (絕對或相對) 是由包含三個部分的位置步驟所組成：</span><span class="sxs-lookup"><span data-stu-id="5ff8b-126">A location path (absolute or relative) is composed of location steps that contain three parts:</span></span>  
  
-   <span data-ttu-id="5ff8b-127">**軸**</span><span class="sxs-lookup"><span data-stu-id="5ff8b-127">**Axis**</span></span>  
  
     <span data-ttu-id="5ff8b-128">軸會指定位置步驟與內容節點所選取之節點間的樹狀結構關聯性。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-128">The axis specifies the tree relationship between the nodes selected by the location step and the context node.</span></span> <span data-ttu-id="5ff8b-129">系統支援 `parent`、`child`、`attribute` 和 `self` 軸。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-129">The `parent`, `child`, `attribute`, and `self` axes are supported.</span></span> <span data-ttu-id="5ff8b-130">如果在位置路徑中指定 `child` 軸，查詢所選取的所有節點都是內容節點的子系。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-130">If a `child` axis is specified in the location path, all the nodes selected by the query are the children of the context node.</span></span> <span data-ttu-id="5ff8b-131">如果指定 `parent` 軸，選取的節點為內容節點的父節點。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-131">If a `parent` axis is specified, the node selected is the parent node of the context node.</span></span> <span data-ttu-id="5ff8b-132">如果指定 `attribute` 軸，選取的節點為內容節點的屬性。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-132">If an `attribute` axis is specified, the nodes selected are the attributes of the context node.</span></span>  
  
-   <span data-ttu-id="5ff8b-133">**節點測試**</span><span class="sxs-lookup"><span data-stu-id="5ff8b-133">**Node test**</span></span>  
  
     <span data-ttu-id="5ff8b-134">節點測試會指定位置步驟所選取的節點類型。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-134">A node test specifies the node type selected by the location step.</span></span> <span data-ttu-id="5ff8b-135">每個軸 (`child`、`parent`、`attribute` 和 `self`) 都有一個主體節點類型。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-135">Every axis (`child`, `parent`, `attribute`, and `self`) has a principal node type.</span></span> <span data-ttu-id="5ff8b-136">若為 `attribute` 軸，主要節點類型為 **\<attribute>** 。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-136">For the `attribute` axis, the principal node type is **\<attribute>**.</span></span> <span data-ttu-id="5ff8b-137">針對 `parent` 、 `child` 和 `self` 座標軸，主要節點類型為 **\<element>** 。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-137">For the `parent`, `child`, and `self` axes, the principal node type is **\<element>**.</span></span>  
  
     <span data-ttu-id="5ff8b-138">例如，如果位置路徑指定了**child：： Customer**，則 **\<Customer>** 會選取內容節點的元素子系。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-138">For example, if the location path specifies **child::Customer**, the **\<Customer>** element children of the context node are selected.</span></span> <span data-ttu-id="5ff8b-139">因為 `child` 軸具有 **\<element>** 做為其主要節點類型，所以如果 customer 是節點，則節點測試 CUSTOMER 為 TRUE **\<element>** 。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-139">Because the `child` axis has **\<element>** as its principal node type, the node test, Customer, is TRUE if Customer is an **\<element>** node.</span></span>  
  
-   <span data-ttu-id="5ff8b-140">**選取述詞 (零或其他)**</span><span class="sxs-lookup"><span data-stu-id="5ff8b-140">**Selection predicates (zero or more)**</span></span>  
  
     <span data-ttu-id="5ff8b-141">述詞會針對軸篩選節點集。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-141">A predicate filters a node-set with respect to an axis.</span></span> <span data-ttu-id="5ff8b-142">在 XPath 運算式中指定選取述詞類似於在 SELECT 陳述式中指定 WHERE 子句。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-142">Specifying selection predicates in an XPath expression is similar to specifying a WHERE clause in a SELECT statement.</span></span> <span data-ttu-id="5ff8b-143">並指定在方括號之間。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-143">The predicate is specified between brackets.</span></span> <span data-ttu-id="5ff8b-144">套用在選取述詞中指定的測試會篩選由節點測試傳回的節點。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-144">Applying the test specified in the selection predicates filters the nodes returned by the node test.</span></span> <span data-ttu-id="5ff8b-145">對於節點集內要篩選的每一個節點，該節點會當做內容節點，而且節點集內的節點數目會當做內容大小，然後評估述詞運算式。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-145">For each node in the node-set to be filtered, the predicate expression is evaluated with that node as the context node, with the number of nodes in the node-set as context size.</span></span> <span data-ttu-id="5ff8b-146">如果述詞運算式評估該節點為 TRUE，則產生的節點集會包含該節點。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-146">If the predicate expression evaluates to TRUE for that node, the node is included in the resulting node-set.</span></span>  
  
     <span data-ttu-id="5ff8b-147">位置步驟的語法是軸名稱之後加上雙冒號 (::)、接著是節點測試，最後是零或其他述詞，每個述詞都會以方括弧括起來。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-147">The syntax for a location step is the axis name and node test separated by two colons (::), followed by zero or more expressions, each in square brackets.</span></span> <span data-ttu-id="5ff8b-148">例如，XPath 運算式 (位置路徑) **child：： Customer [ @CustomerID = ' ALFKI ']** 會選取 **\<Customer>** 內容節點的所有元素子系。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-148">For example, the XPath expression (location path) **child::Customer[@CustomerID='ALFKI']** selects all the **\<Customer>** element children of the context node.</span></span> <span data-ttu-id="5ff8b-149">然後，述詞中的測試會套用至節點集，而此節點集只會傳回 **\<Customer>** 其**CustomerID**屬性的屬性值為 ' ALFKI ' 的元素節點。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-149">Then the test in the predicate is applied to the node-set, which returns only the **\<Customer>** element nodes with attribute value 'ALFKI' for its **CustomerID** attribute.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ff8b-150">本節內容</span><span class="sxs-lookup"><span data-stu-id="5ff8b-150">In This Section</span></span>  
 [<span data-ttu-id="5ff8b-151">指定 &#40;SQLXML 4.0&#41;的軸</span><span class="sxs-lookup"><span data-stu-id="5ff8b-151">Specifying an Axis &#40;SQLXML 4.0&#41;</span></span>](specifying-an-axis-sqlxml-4-0.md)  
 <span data-ttu-id="5ff8b-152">提供指定軸的範例。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-152">Provides examples of specifying an axis.</span></span>  
  
 [<span data-ttu-id="5ff8b-153">在位置路徑中指定節點測試 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="5ff8b-153">Specifying a Node Test in the Location Path &#40;SQLXML 4.0&#41;</span></span>](specifying-a-node-test-in-the-location-path-sqlxml-4-0.md)  
 <span data-ttu-id="5ff8b-154">提供指定節點測試的範例。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-154">Provides examples of specifying a node test.</span></span>  
  
 [<span data-ttu-id="5ff8b-155">在位置路徑中指定選取述詞 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="5ff8b-155">Specifying Selection Predicates in the Location Path &#40;SQLXML 4.0&#41;</span></span>](specifying-selection-predicates-in-the-location-path-sqlxml-4-0.md)  
 <span data-ttu-id="5ff8b-156">提供指定選取述詞的範例。</span><span class="sxs-lookup"><span data-stu-id="5ff8b-156">Provides examples of specifying selection predicates.</span></span>  
  
  
