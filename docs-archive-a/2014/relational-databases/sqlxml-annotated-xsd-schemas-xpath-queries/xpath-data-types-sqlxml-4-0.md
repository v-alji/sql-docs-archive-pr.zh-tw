---
title: " (SQLXML 4.0) 的 XPath 資料類型 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- mapping XDR types to XPath types [SQLXML]
- data types [XPath]
- arithmetic operators
- mapping data types [SQLXML]
- relational operators [SQLXML]
- node-set [SQLXML]
- data types [SQLXML], XPath
- XPath operators [SQLXML]
- XDR data type [SQLXML]
- equality operators [SQLXML]
- XPath conversions [SQLXML]
- converting data types [SQLXML]
- Boolean operators
- XPath queries [SQLXML], data types
- XPath data types [SQLXML]
- operators [SQLXML]
ms.assetid: a90374bf-406f-4384-ba81-59478017db68
author: rothja
ms.author: jroth
ms.openlocfilehash: 846fc5a17ac97d30b6f0ab65fee176ac459c20cc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597735"
---
# <a name="xpath-data-types-sqlxml-40"></a><span data-ttu-id="a44ee-102">XPath 資料類型 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="a44ee-102">XPath Data Types (SQLXML 4.0)</span></span>
  [!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="a44ee-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、XPath 和 XML 架構 (XSD) 有非常不同的資料類型。</span><span class="sxs-lookup"><span data-stu-id="a44ee-103">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], XPath, and XML Schema (XSD) have very different data types.</span></span> <span data-ttu-id="a44ee-104">例如，XPath 沒有整數或日期資料類型，但是 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 和 XSD 則有許多。</span><span class="sxs-lookup"><span data-stu-id="a44ee-104">For example, XPath does not have integer or date data types, but [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] and XSD have many.</span></span> <span data-ttu-id="a44ee-105">XSD 會將奈秒的有效位數用於時間值，而 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 則至多使用 1/300 秒的有效位數。</span><span class="sxs-lookup"><span data-stu-id="a44ee-105">XSD uses nanosecond precision for time values, and [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses at most 1/300-second precision.</span></span> <span data-ttu-id="a44ee-106">因此，並非永遠都能將一個資料類型對應到另一個。</span><span class="sxs-lookup"><span data-stu-id="a44ee-106">Consequently, mapping one data type to another is not always possible.</span></span> <span data-ttu-id="a44ee-107">如需 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 將資料類型對應到 XSD 資料類型的詳細資訊，請參閱[資料類型強制型轉和 sql： datatype 注釋 &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="a44ee-107">For more information about mapping [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data types to XSD data types, see [Data Type Coercions and the sql:datatype Annotation &#40;SQLXML 4.0&#41;](../sqlxml-annotated-xsd-schemas-using/data-type-coercions-and-the-sql-datatype-annotation-sqlxml-4-0.md).</span></span>  
  
 <span data-ttu-id="a44ee-108">XPath 具備三種資料類型：`string`、`number` 和 `boolean`。</span><span class="sxs-lookup"><span data-stu-id="a44ee-108">XPath has three data types: `string`, `number`, and `boolean`.</span></span> <span data-ttu-id="a44ee-109">`number` 資料類型永遠是 IEEE 754 雙精確度浮點數。</span><span class="sxs-lookup"><span data-stu-id="a44ee-109">The `number` data type is always an IEEE 754 double-precision floating-point.</span></span> <span data-ttu-id="a44ee-110">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `float(53)` 資料類型是最接近的 XPath `number` 。</span><span class="sxs-lookup"><span data-stu-id="a44ee-110">The [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`float(53)` data type is the closest to XPath `number`.</span></span> <span data-ttu-id="a44ee-111">不過，`float(53)` 不完全是 IEEE 754。</span><span class="sxs-lookup"><span data-stu-id="a44ee-111">However, `float(53)` is not exactly IEEE 754.</span></span> <span data-ttu-id="a44ee-112">例如，不會使用 NaN (非數字的值)，也不會使用無限。</span><span class="sxs-lookup"><span data-stu-id="a44ee-112">For example, neither NaN (Not-a-Number) nor infinity is used.</span></span> <span data-ttu-id="a44ee-113">嘗試將非數值字串轉換為 `number` 並嘗試除以零會導致錯誤。</span><span class="sxs-lookup"><span data-stu-id="a44ee-113">Attempting to convert a nonnumeric string to `number` and trying to divide by zero results in an error.</span></span>  
  
## <a name="xpath-conversions"></a><span data-ttu-id="a44ee-114">XPath 轉換</span><span class="sxs-lookup"><span data-stu-id="a44ee-114">XPath Conversions</span></span>  
 <span data-ttu-id="a44ee-115">當您使用 XPath 查詢 (例如，`OrderDetail[@UnitPrice > "10.0"]`) 時，隱含和明確的資料類型轉換可能會以明顯的方式變更查詢的意義。</span><span class="sxs-lookup"><span data-stu-id="a44ee-115">When you use an XPath query such as `OrderDetail[@UnitPrice > "10.0"]`, implicit and explicit data type conversions can change the meaning of the query in subtle ways.</span></span> <span data-ttu-id="a44ee-116">因此，了解如何實作 XPath 資料類型相當重要。</span><span class="sxs-lookup"><span data-stu-id="a44ee-116">Therefore, it is important to understand how XPath data types are implemented.</span></span> <span data-ttu-id="a44ee-117">您可以在位於的 W3C 網站，找到 XPath 語言規格、XML 路徑語言 (XPath) 1.0 版 W3C 建議的建議 8 1999 http://www.w3.org/TR/1999/PR-xpath-19991008.html 。</span><span class="sxs-lookup"><span data-stu-id="a44ee-117">The XPath language specification, XML Path Language (XPath) version 1.0 W3C Proposed Recommendation 8 October 1999, can be found at the W3C Web site at http://www.w3.org/TR/1999/PR-xpath-19991008.html.</span></span>  
  
 <span data-ttu-id="a44ee-118">XPath 運算子分為四個類別：</span><span class="sxs-lookup"><span data-stu-id="a44ee-118">XPath operators are divided into four categories:</span></span>  
  
-   <span data-ttu-id="a44ee-119">布林運算子 (and、or)</span><span class="sxs-lookup"><span data-stu-id="a44ee-119">Boolean operators (and, or)</span></span>  
  
-   <span data-ttu-id="a44ee-120">關係運算子 (\<, > ， \<=, > =) </span><span class="sxs-lookup"><span data-stu-id="a44ee-120">Relational operators (\<, >, \<=, >=)</span></span>  
  
-   <span data-ttu-id="a44ee-121">相等運算子 (=、!=)</span><span class="sxs-lookup"><span data-stu-id="a44ee-121">Equality operators (=, !=)</span></span>  
  
-   <span data-ttu-id="a44ee-122">算術運算子 (+、-、\*、div、mod)</span><span class="sxs-lookup"><span data-stu-id="a44ee-122">Arithmetic operators (+, -, \*, div, mod)</span></span>  
  
 <span data-ttu-id="a44ee-123">運算子的每個類別都會以不同的方式轉換其運算元。</span><span class="sxs-lookup"><span data-stu-id="a44ee-123">Each category of operator converts its operands differently.</span></span> <span data-ttu-id="a44ee-124">如果必要，XPath 運算子會以隱含的方式轉換其運算元。</span><span class="sxs-lookup"><span data-stu-id="a44ee-124">XPath operators implicitly convert their operands if necessary.</span></span> <span data-ttu-id="a44ee-125">算術運算子會將其運算元轉換為 `number`，並成為數值。</span><span class="sxs-lookup"><span data-stu-id="a44ee-125">Arithmetic operators convert their operands to `number`, and result in a number value.</span></span> <span data-ttu-id="a44ee-126">布林運算子會將其運算元轉換為 `boolean`，並成為布林值。</span><span class="sxs-lookup"><span data-stu-id="a44ee-126">Boolean operators convert their operands to `boolean`, and result in a Boolean value.</span></span> <span data-ttu-id="a44ee-127">關係運算子和相等運算子會成為布林值。</span><span class="sxs-lookup"><span data-stu-id="a44ee-127">Relational operators and equality operators result in a Boolean value.</span></span> <span data-ttu-id="a44ee-128">不過，根據其運算元的原始資料類型，它們擁有不同的轉換規則，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="a44ee-128">However, they have different conversion rules depending on the original data types of their operands, as shown in this table.</span></span>  
  
|<span data-ttu-id="a44ee-129">運算元</span><span class="sxs-lookup"><span data-stu-id="a44ee-129">Operand</span></span>|<span data-ttu-id="a44ee-130">關聯式運算子</span><span class="sxs-lookup"><span data-stu-id="a44ee-130">Relational operator</span></span>|<span data-ttu-id="a44ee-131">等號比較運算子</span><span class="sxs-lookup"><span data-stu-id="a44ee-131">Equality operator</span></span>|  
|-------------|-------------------------|-----------------------|  
|<span data-ttu-id="a44ee-132">兩個運算元都是節點集。</span><span class="sxs-lookup"><span data-stu-id="a44ee-132">Both operands are node-sets.</span></span>|<span data-ttu-id="a44ee-133">只有在一個集合中有一個節點，而且在第二個集合中有一個節點，讓其 `string` 值的比較為 TRUE 時，才為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="a44ee-133">TRUE if and only if there is a node in one set and a node in the second set such that the comparison of their `string` values is TRUE.</span></span>|<span data-ttu-id="a44ee-134">相同。</span><span class="sxs-lookup"><span data-stu-id="a44ee-134">Same.</span></span>|  
|<span data-ttu-id="a44ee-135">一個是節點集，另一個是 `string`。</span><span class="sxs-lookup"><span data-stu-id="a44ee-135">One is a node-set, the other a `string`.</span></span>|<span data-ttu-id="a44ee-136">只有在節點集中有一個節點，因而轉換為 `number`，讓其與轉換為 `string` 之 `number` 的比較為 TRUE 時，才為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="a44ee-136">TRUE if and only if there is a node in the node-set such that when converted to `number`, the comparison of it with the `string` converted to `number` is TRUE.</span></span>|<span data-ttu-id="a44ee-137">只有在節點集中有一個節點，因而轉換為 `string`，讓其與 `string` 的比較為 TRUE 時，才為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="a44ee-137">TRUE if and only if there is a node in the node-set such that when converted to `string`, the comparison of it with the `string` is TRUE.</span></span>|  
|<span data-ttu-id="a44ee-138">一個是節點集，另一個是 `number`。</span><span class="sxs-lookup"><span data-stu-id="a44ee-138">One is a node-set, the other a `number`.</span></span>|<span data-ttu-id="a44ee-139">只有在節點集中有一個節點，因而轉換為 `number`，讓其與 `number` 的比較為 TRUE 時，才為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="a44ee-139">TRUE if and only if there is a node in the node-set such that when converted to `number`, the comparison of it with the `number` is TRUE.</span></span>|<span data-ttu-id="a44ee-140">相同。</span><span class="sxs-lookup"><span data-stu-id="a44ee-140">Same.</span></span>|  
|<span data-ttu-id="a44ee-141">一個是節點集，另一個是 `boolean`。</span><span class="sxs-lookup"><span data-stu-id="a44ee-141">One is a node-set, the other a `boolean`.</span></span>|<span data-ttu-id="a44ee-142">只有在節點集中有一個節點，因而轉換為 `boolean`，然後再轉換為 `number`，讓其與轉換為 `boolean` 之 `number` 的比較為 TRUE 時，才為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="a44ee-142">TRUE if and only if there is a node in the node-set such that when converted to `boolean` and then to `number`, the comparison of it with the `boolean` converted to `number` is TRUE.</span></span>|<span data-ttu-id="a44ee-143">只有在節點集中有一個節點，因而轉換為 `boolean`，讓其與 `boolean` 的比較為 TRUE 時，才為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="a44ee-143">TRUE if and only if there is a node in the node-set such that when converted to `boolean`, the comparison of it with the `boolean` is TRUE.</span></span>|  
|<span data-ttu-id="a44ee-144">都不是節點集。</span><span class="sxs-lookup"><span data-stu-id="a44ee-144">Neither is a node-set.</span></span>|<span data-ttu-id="a44ee-145">將兩個運算元同時轉換為 `number`，然後進行比較。</span><span class="sxs-lookup"><span data-stu-id="a44ee-145">Convert both operands to `number` and then compare.</span></span>|<span data-ttu-id="a44ee-146">將兩個運算元同時轉換為一般類型，然後進行比較。</span><span class="sxs-lookup"><span data-stu-id="a44ee-146">Convert both operands to a common type and then compare.</span></span> <span data-ttu-id="a44ee-147">如果其中一個是 `boolean`，轉換為 `boolean`，如果其中一個是 `number`，轉換為 `number`，否則，轉換為 `string`。</span><span class="sxs-lookup"><span data-stu-id="a44ee-147">Convert to `boolean` if either is `boolean`, `number` if either is `number`; otherwise, convert to `string`.</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="a44ee-148">XPath 關係運算子會將其運算元一律轉換為 `number`，因此無法進行 `string` 比較。</span><span class="sxs-lookup"><span data-stu-id="a44ee-148">Because XPath relational operators always convert their operands to `number`, `string` comparisons are not possible.</span></span> <span data-ttu-id="a44ee-149">若要加入日期比較，SQL Server 2000 會將此變數提供給 XPath 規格：當關係運算子將 `string` 與 `string` 相比較、將節點集與 `string` 相比較，或將兩個字串值節點集相比較時，會執行 `string` 比較 (而非 `number` 比較)。</span><span class="sxs-lookup"><span data-stu-id="a44ee-149">To include date comparisons, SQL Server 2000 offers this variation to the XPath specification: When a relational operator compares a `string` to a `string`, a node-set to a `string`, or a string-valued node-set to a string-valued node-set, a `string` comparison (not a `number` comparison) is performed.</span></span>  
  
## <a name="node-set-conversions"></a><span data-ttu-id="a44ee-150">節點集轉換</span><span class="sxs-lookup"><span data-stu-id="a44ee-150">Node-Set Conversions</span></span>  
 <span data-ttu-id="a44ee-151">節點集轉換並不一定直覺式。</span><span class="sxs-lookup"><span data-stu-id="a44ee-151">Node-set conversions are not always intuitive.</span></span> <span data-ttu-id="a44ee-152">藉由在節點集中只採用第一個節點的字串值，節點集就會轉換為 `string`。</span><span class="sxs-lookup"><span data-stu-id="a44ee-152">A node-set is converted to a `string` by taking the string value of only the first node in the set.</span></span> <span data-ttu-id="a44ee-153">節點集會轉換為 `number`，方法是，將其先轉換為 `string`，然後再將 `string` 轉換為 `number`。</span><span class="sxs-lookup"><span data-stu-id="a44ee-153">A node-set is converted to `number` by converting it to `string`, and then converting `string` to `number`.</span></span> <span data-ttu-id="a44ee-154">系統會測試節點集是否存在，然後再轉換為 `boolean`。</span><span class="sxs-lookup"><span data-stu-id="a44ee-154">A node-set is converted to `boolean` by testing for its existence.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] <span data-ttu-id="a44ee-155">不會在節點集上執行位置選取：例如，XPath 查詢 `Customer[3]` 表示第三個客戶；在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中不支援此種類型的位置選取。</span><span class="sxs-lookup"><span data-stu-id="a44ee-155">does not perform positional selection on node-sets: for example, the XPath query `Customer[3]` means the third customer; this type of positional selection is not supported in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="a44ee-156">因此，系統不會實作 XPath 規格所描述的節點集對 `string` 或節點集對 `number` 的轉換。</span><span class="sxs-lookup"><span data-stu-id="a44ee-156">Therefore, the node-set-to-`string` or node-set-to-`number` conversions as described by the XPath specification are not implemented.</span></span> <span data-ttu-id="a44ee-157">在 XPath 規格指定 "first" 語意的每個地方，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 都會使用 "any" 語意。</span><span class="sxs-lookup"><span data-stu-id="a44ee-157">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] uses "any" semantics wherever the XPath specification specifies "first" semantics.</span></span> <span data-ttu-id="a44ee-158">例如，根據 W3C XPath 規格，XPath 查詢 `Order[OrderDetail/@UnitPrice > 10.0]` 會選取具有大於10.0 之**單價**的第一個**OrderDetail**的訂單。</span><span class="sxs-lookup"><span data-stu-id="a44ee-158">For example, based on the W3C XPath specification, the XPath query `Order[OrderDetail/@UnitPrice > 10.0]` selects those orders with the first **OrderDetail** that has a **UnitPrice** greater than 10.0.</span></span> <span data-ttu-id="a44ee-159">在中 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ，此 XPath 查詢會選取具有大於10.0 之**單價**的任何**OrderDetail**訂單。</span><span class="sxs-lookup"><span data-stu-id="a44ee-159">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], this XPath query selects those orders with any **OrderDetail** that has a **UnitPrice** greater than 10.0.</span></span>  
  
 <span data-ttu-id="a44ee-160">轉換為 `boolean` 時，會產生存在測試，因此，XPath 查詢 `Products[@Discontinued=true()]` 相當於 SQL 運算式 "Products.Discontinued is not null"，而非 SQL 運算式 "Products.Discontinued = 1"。</span><span class="sxs-lookup"><span data-stu-id="a44ee-160">Conversion to `boolean` generates an existence test; therefore, the XPath query `Products[@Discontinued=true()]` is equivalent to the SQL expression "Products.Discontinued is not null", not the SQL expression "Products.Discontinued = 1".</span></span> <span data-ttu-id="a44ee-161">為了讓查詢相當於後者的 SQL 運算式，請先將節點集轉換為非 `boolean` 類型，例如 `number`。</span><span class="sxs-lookup"><span data-stu-id="a44ee-161">To make the query equivalent to the latter SQL expression, first convert the node-set to a non-`boolean` type, such as `number`.</span></span> <span data-ttu-id="a44ee-162">例如，`Products[number(@Discontinued) = true()]`。</span><span class="sxs-lookup"><span data-stu-id="a44ee-162">For example, `Products[number(@Discontinued) = true()]`.</span></span>  
  
 <span data-ttu-id="a44ee-163">對於節點集中的任何一個節點或其中一個節點，如果運算子為 TRUE，則大部分會定義為 TRUE，所以如果節點集是空的，這些運算永遠會評估為 FALSE。</span><span class="sxs-lookup"><span data-stu-id="a44ee-163">Because most operators are defined to be TRUE if they are TRUE for any or one of the nodes in the node-set, these operations always evaluate to FALSE if the node-set is empty.</span></span> <span data-ttu-id="a44ee-164">因此，如果 A 是空的，`A = B` 和 `A != B` 都為 FALSE，而 `not(A=B)` 和 `not(A!=B)` 都為 TRUE。</span><span class="sxs-lookup"><span data-stu-id="a44ee-164">Thus, if A is empty, both `A = B` and `A != B` are FALSE, and `not(A=B)` and `not(A!=B)` are TRUE.</span></span>  
  
 <span data-ttu-id="a44ee-165">如果資料庫中的資料行值不是 `null`，對應到該資料行的屬性或元素通常存在。</span><span class="sxs-lookup"><span data-stu-id="a44ee-165">Usually, an attribute or element that maps to a column exists if the value of that column in the database is not `null`.</span></span> <span data-ttu-id="a44ee-166">如果任何資料列的子系存在，則對應到那些資料列的元素存在。</span><span class="sxs-lookup"><span data-stu-id="a44ee-166">Elements that map to rows exist if any of their children exist.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="a44ee-167">使用 `is-constant` 註解的元素永遠存在。</span><span class="sxs-lookup"><span data-stu-id="a44ee-167">Elements annotated with `is-constant` always exist.</span></span> <span data-ttu-id="a44ee-168">因此，無法在 `is-constant` 元素上使用 XPath 述詞。</span><span class="sxs-lookup"><span data-stu-id="a44ee-168">Consequently, XPath predicates cannot be used on `is-constant` elements.</span></span>  
  
 <span data-ttu-id="a44ee-169">當節點集轉換為 `string` 或 `number` 時，會在註解式結構描述中檢查其 XDR 類型 (如果有)，並使用該類型判斷所需的轉換。</span><span class="sxs-lookup"><span data-stu-id="a44ee-169">When a node-set is converted to `string` or `number`, its XDR type (if any) is inspected in the annotated schema and that type is used to determine the conversion that is required.</span></span>  
  
## <a name="mapping-xdr-data-types-to-xpath-data-types"></a><span data-ttu-id="a44ee-170">將 XDR 資料類型對應到 XPath 資料類型</span><span class="sxs-lookup"><span data-stu-id="a44ee-170">Mapping XDR Data Types to XPath Data Types</span></span>  
 <span data-ttu-id="a44ee-171">節點的 XPath 資料類型衍生自架構中的 XDR 資料類型，如下表所示 (節點的「**員工 id** 」用於說明目的) 。</span><span class="sxs-lookup"><span data-stu-id="a44ee-171">The XPath data type of a node is derived from the XDR data type in the schema, as shown in the following table (the node **EmployeeID** is used for illustrative purpose).</span></span>  
  
|<span data-ttu-id="a44ee-172">XDR 資料類型</span><span class="sxs-lookup"><span data-stu-id="a44ee-172">XDR data type</span></span>|<span data-ttu-id="a44ee-173">對等用法</span><span class="sxs-lookup"><span data-stu-id="a44ee-173">Equivalent</span></span><br /><br /> <span data-ttu-id="a44ee-174">XPath 資料類型</span><span class="sxs-lookup"><span data-stu-id="a44ee-174">XPath data type</span></span>|<span data-ttu-id="a44ee-175">使用的 SQL Server 轉換</span><span class="sxs-lookup"><span data-stu-id="a44ee-175">SQL Server conversion used</span></span>|  
|-------------------|------------------------------------|--------------------------------|  
|<span data-ttu-id="a44ee-176">Nonebin.base64bin.hex</span><span class="sxs-lookup"><span data-stu-id="a44ee-176">Nonebin.base64bin.hex</span></span>|<span data-ttu-id="a44ee-177">N/A</span><span class="sxs-lookup"><span data-stu-id="a44ee-177">N/A</span></span>|<span data-ttu-id="a44ee-178">NoneEmployeeID</span><span class="sxs-lookup"><span data-stu-id="a44ee-178">NoneEmployeeID</span></span>|  
|<span data-ttu-id="a44ee-179">boolean</span><span class="sxs-lookup"><span data-stu-id="a44ee-179">boolean</span></span>|<span data-ttu-id="a44ee-180">boolean</span><span class="sxs-lookup"><span data-stu-id="a44ee-180">boolean</span></span>|<span data-ttu-id="a44ee-181">CONVERT(bit, EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="a44ee-181">CONVERT(bit, EmployeeID)</span></span>|  
|<span data-ttu-id="a44ee-182">number、int、float、i1、i2、i4、i8、r4、r8ui1、ui2、ui4、ui8</span><span class="sxs-lookup"><span data-stu-id="a44ee-182">number, int, float,i1, i2, i4, i8,r4, r8ui1, ui2, ui4, ui8</span></span>|<span data-ttu-id="a44ee-183">數字</span><span class="sxs-lookup"><span data-stu-id="a44ee-183">number</span></span>|<span data-ttu-id="a44ee-184">CONVERT(float(53), EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="a44ee-184">CONVERT(float(53), EmployeeID)</span></span>|  
|<span data-ttu-id="a44ee-185">id、idref、idrefsentity、entities、enumerationnotation、nmtoken、nmtokens、chardate、Timedate、Time.tz、string、uri、uuid</span><span class="sxs-lookup"><span data-stu-id="a44ee-185">id, idref, idrefsentity, entities, enumerationnotation, nmtoken, nmtokens, chardate, Timedate, Time.tz, string, uri, uuid</span></span>|<span data-ttu-id="a44ee-186">string</span><span class="sxs-lookup"><span data-stu-id="a44ee-186">string</span></span>|<span data-ttu-id="a44ee-187">CONVERT(nvarchar(4000), EmployeeID, 126)</span><span class="sxs-lookup"><span data-stu-id="a44ee-187">CONVERT(nvarchar(4000), EmployeeID, 126)</span></span>|  
|<span data-ttu-id="a44ee-188">fixed14.4</span><span class="sxs-lookup"><span data-stu-id="a44ee-188">fixed14.4</span></span>|<span data-ttu-id="a44ee-189">N/A (在 XPath 中沒有相當於 fixed14.4 XDR 資料類型的資料類型)</span><span class="sxs-lookup"><span data-stu-id="a44ee-189">N/A(There is no data type in XPath that is equivalent to the fixed14.4 XDR data type)</span></span>|<span data-ttu-id="a44ee-190">CONVERT(money, EmployeeID)</span><span class="sxs-lookup"><span data-stu-id="a44ee-190">CONVERT(money, EmployeeID)</span></span>|  
|<span data-ttu-id="a44ee-191">date</span><span class="sxs-lookup"><span data-stu-id="a44ee-191">date</span></span>|<span data-ttu-id="a44ee-192">string</span><span class="sxs-lookup"><span data-stu-id="a44ee-192">string</span></span>|<span data-ttu-id="a44ee-193">LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)</span><span class="sxs-lookup"><span data-stu-id="a44ee-193">LEFT(CONVERT(nvarchar(4000), EmployeeID, 126), 10)</span></span>|  
|<span data-ttu-id="a44ee-194">time</span><span class="sxs-lookup"><span data-stu-id="a44ee-194">time</span></span><br /><br /> <span data-ttu-id="a44ee-195">time.tz</span><span class="sxs-lookup"><span data-stu-id="a44ee-195">time.tz</span></span>|<span data-ttu-id="a44ee-196">string</span><span class="sxs-lookup"><span data-stu-id="a44ee-196">string</span></span>|<span data-ttu-id="a44ee-197">SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)</span><span class="sxs-lookup"><span data-stu-id="a44ee-197">SUBSTRING(CONVERT(nvarchar(4000), EmployeeID, 126), 1 + CHARINDEX(N'T', CONVERT(nvarchar(4000), EmployeeID, 126)), 24)</span></span>|  
  
 <span data-ttu-id="a44ee-198">日期和時間轉換的設計目的，是要使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `datetime` 資料類型或，來處理值是否儲存在資料庫中 `string` 。</span><span class="sxs-lookup"><span data-stu-id="a44ee-198">The date and time conversions are designed to work whether the value is stored in the database using the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`datetime` data type or a `string`.</span></span> <span data-ttu-id="a44ee-199">請注意， [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `datetime` 資料類型不會使用 `timezone` ，而且具有比 XML 資料類型更小的有效位數 `time` 。</span><span class="sxs-lookup"><span data-stu-id="a44ee-199">Note that the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]`datetime` data type does not use `timezone` and has a smaller precision than the XML `time` data type.</span></span> <span data-ttu-id="a44ee-200">為包含 `timezone` 資料類型或其他有效位數，使用 `string` 類型，將資料儲存在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="a44ee-200">To include the `timezone` data type or additional precision, store the data in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] using a `string` type.</span></span>  
  
 <span data-ttu-id="a44ee-201">當節點從其 XDR 資料類型轉換為 XPath 資料類型時，有時候需要其他轉換 (從一個 XPath 資料類型轉換為另一個 XPath 資料類型)。</span><span class="sxs-lookup"><span data-stu-id="a44ee-201">When a node is converted from its XDR data type to the XPath data type, additional conversion is sometimes necessary (from one XPath data type to another XPath data type).</span></span> <span data-ttu-id="a44ee-202">例如，請考量以下的 XPath 查詢：</span><span class="sxs-lookup"><span data-stu-id="a44ee-202">For example, consider this XPath query:</span></span>  
  
```  
(@m + 3) = 4  
```  
  
 <span data-ttu-id="a44ee-203">如果 @m 屬於 `fixed14.4` xdr 資料類型，則會使用下列來完成從 xdr 資料類型轉換為 XPath 資料類型的作業：</span><span class="sxs-lookup"><span data-stu-id="a44ee-203">If @m is of the `fixed14.4` XDR data type, the conversion from XDR data type to XPath data type is accomplished using:</span></span>  
  
```  
CONVERT(money, m)  
```  
  
 <span data-ttu-id="a44ee-204">在這個轉換中，節點 `m` 會從 `fixed14.4` 轉換為 `money`。</span><span class="sxs-lookup"><span data-stu-id="a44ee-204">In this conversion, the node `m` is converted from `fixed14.4` to `money`.</span></span> <span data-ttu-id="a44ee-205">不過，加入 3 這個值需要其他轉換：</span><span class="sxs-lookup"><span data-stu-id="a44ee-205">However, adding the value of 3, requires additional conversion:</span></span>  
  
```  
CONVERT(float(CONVERT(money, m))  
```  
  
 <span data-ttu-id="a44ee-206">XPath 運算式會評估為：</span><span class="sxs-lookup"><span data-stu-id="a44ee-206">The XPath expression is evaluated as:</span></span>  
  
```  
CONVERT(float(CONVERT(money, m)) + CONVERT(float(53), 3) = CONVERT(float(53), 3)  
```  
  
 <span data-ttu-id="a44ee-207">這與其他 XPath 運算式 (例如常值或複合運算式) 所套用的轉換相同，如下表所示。</span><span class="sxs-lookup"><span data-stu-id="a44ee-207">As shown in the following table, this is the same conversion that is applied for other XPath expressions (such as literals or compound expressions).</span></span>  
  
||||||  
|-|-|-|-|-|  
||<span data-ttu-id="a44ee-208">X 不明</span><span class="sxs-lookup"><span data-stu-id="a44ee-208">X is unknown</span></span>|<span data-ttu-id="a44ee-209">X 是 `string`</span><span class="sxs-lookup"><span data-stu-id="a44ee-209">X is `string`</span></span>|<span data-ttu-id="a44ee-210">X 是 `number`</span><span class="sxs-lookup"><span data-stu-id="a44ee-210">X is `number`</span></span>|<span data-ttu-id="a44ee-211">X 是 `boolean`</span><span class="sxs-lookup"><span data-stu-id="a44ee-211">X is `boolean`</span></span>|  
|<span data-ttu-id="a44ee-212">string(X)</span><span class="sxs-lookup"><span data-stu-id="a44ee-212">string(X)</span></span>|<span data-ttu-id="a44ee-213">CONVERT (nvarchar(4000), X, 126)</span><span class="sxs-lookup"><span data-stu-id="a44ee-213">CONVERT (nvarchar(4000), X, 126)</span></span>|-|<span data-ttu-id="a44ee-214">CONVERT (nvarchar(4000), X, 126)</span><span class="sxs-lookup"><span data-stu-id="a44ee-214">CONVERT (nvarchar(4000), X, 126)</span></span>|<span data-ttu-id="a44ee-215">CASE WHEN X THEN N'true' ELSE N'false' END</span><span class="sxs-lookup"><span data-stu-id="a44ee-215">CASE WHEN X THEN N'true' ELSE N'false' END</span></span>|  
|<span data-ttu-id="a44ee-216">number(X)</span><span class="sxs-lookup"><span data-stu-id="a44ee-216">number(X)</span></span>|<span data-ttu-id="a44ee-217">CONVERT (float(53), X)</span><span class="sxs-lookup"><span data-stu-id="a44ee-217">CONVERT (float(53), X)</span></span>|<span data-ttu-id="a44ee-218">CONVERT (float(53), X)</span><span class="sxs-lookup"><span data-stu-id="a44ee-218">CONVERT (float(53), X)</span></span>|-|<span data-ttu-id="a44ee-219">CASE WHEN X THEN 1 ELSE 0 END</span><span class="sxs-lookup"><span data-stu-id="a44ee-219">CASE WHEN X THEN 1 ELSE 0 END</span></span>|  
|<span data-ttu-id="a44ee-220">boolean(X)</span><span class="sxs-lookup"><span data-stu-id="a44ee-220">boolean(X)</span></span>|-|<span data-ttu-id="a44ee-221">LEN (X) > 0</span><span class="sxs-lookup"><span data-stu-id="a44ee-221">LEN(X) > 0</span></span>|<span data-ttu-id="a44ee-222">X。</span><span class="sxs-lookup"><span data-stu-id="a44ee-222">X != 0</span></span>|-|  
  
## <a name="examples"></a><span data-ttu-id="a44ee-223">範例</span><span class="sxs-lookup"><span data-stu-id="a44ee-223">Examples</span></span>  
  
### <a name="a-convert-a-data-type-in-an-xpath-query"></a><span data-ttu-id="a44ee-224">A.</span><span class="sxs-lookup"><span data-stu-id="a44ee-224">A.</span></span> <span data-ttu-id="a44ee-225">在 XPath 查詢中轉換資料類型</span><span class="sxs-lookup"><span data-stu-id="a44ee-225">Convert a data type in an XPath query</span></span>  
 <span data-ttu-id="a44ee-226">在針對批註式 XSD 架構指定的下列 XPath 查詢中，查詢會選取所有**具有 [#** #] 屬性值為 E-1 的**員工**節點，其中 "E-" 是使用注釋所指定的前置詞 `sql:id-prefix` 。</span><span class="sxs-lookup"><span data-stu-id="a44ee-226">In the following XPath query specified against an annotated XSD schema, the query selects all **Employee** nodes with the **EmployeeID** attribute value of E-1, where "E-" is the prefix specified using the `sql:id-prefix` annotation.</span></span>  
  
 `Employee[@EmployeeID="E-1"]`  
  
 <span data-ttu-id="a44ee-227">查詢中的述詞相當於 SQL 運算式：</span><span class="sxs-lookup"><span data-stu-id="a44ee-227">The predicate in the query is equivalent to the SQL expression:</span></span>  
  
 `N'E-' + CONVERT(nvarchar(4000), Employees.EmployeeID, 126) = N'E-1'`  
  
 <span data-ttu-id="a44ee-228">因為「**員工 id** 」是 `id` (`idref` 、、、等其中一個， `idrefs` `nmtoken` `nmtokens` 所以在 XSD 架構中) 資料類型值**EmployeeID** ，因此會 `string` 使用先前所述的轉換規則，將「員工」轉換為 XPath 資料類型。</span><span class="sxs-lookup"><span data-stu-id="a44ee-228">Because **EmployeeID** is one of the `id` (`idref`, `idrefs`, `nmtoken`, `nmtokens`, and so on) data type values in the XSD schema, **EmployeeID** is converted to the `string` XPath data type using the conversion rules described previously.</span></span>  
  
 `CONVERT(nvarchar(4000), Employees.EmployeeID, 126)`  
  
 <span data-ttu-id="a44ee-229">"E-" 前述詞會加入到字串，然後結果會與 `N'E-1'` 相比較。</span><span class="sxs-lookup"><span data-stu-id="a44ee-229">The "E-" prefix is added to the string, and the result is then compared with `N'E-1'`.</span></span>  
  
### <a name="b-perform-several-data-type-conversions-in-an-xpath-query"></a><span data-ttu-id="a44ee-230">B.</span><span class="sxs-lookup"><span data-stu-id="a44ee-230">B.</span></span> <span data-ttu-id="a44ee-231">在 XPath 查詢中執行數個資料類型轉換</span><span class="sxs-lookup"><span data-stu-id="a44ee-231">Perform several data type conversions in an XPath query</span></span>  
 <span data-ttu-id="a44ee-232">請考慮使用針對註解式 XSD 結構描述指定的這個 XPath 查詢：`OrderDetail[@UnitPrice * @OrderQty > 98]`</span><span class="sxs-lookup"><span data-stu-id="a44ee-232">Consider this XPath query specified against an annotated XSD schema: `OrderDetail[@UnitPrice * @OrderQty > 98]`</span></span>  
  
 <span data-ttu-id="a44ee-233">這個 XPath 查詢會傳回滿足述詞的所有 **\<OrderDetail>** 元素 `@UnitPrice * @OrderQty > 98` 。</span><span class="sxs-lookup"><span data-stu-id="a44ee-233">This XPath query returns all the **\<OrderDetail>** elements satisfying the predicate `@UnitPrice * @OrderQty > 98`.</span></span> <span data-ttu-id="a44ee-234">如果在**UnitPrice** `fixed14.4` 標注架構中使用資料類型來標注單價，則此述詞相當於 SQL 運算式：</span><span class="sxs-lookup"><span data-stu-id="a44ee-234">If the **UnitPrice** is annotated with a `fixed14.4` data type in the annotated schema, this predicate is equivalent to the SQL expression:</span></span>  
  
 `CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice)) * CONVERT(float(53), OrderDetail.OrderQty) > CONVERT(float(53), 98)`  
  
 <span data-ttu-id="a44ee-235">在轉換 XPath 查詢中的值時，第一個轉換會先將 XDR 資料類型轉換為 XPath 資料類型。</span><span class="sxs-lookup"><span data-stu-id="a44ee-235">In converting the values in the XPath query, the first conversion converts the XDR data type to the XPath data type.</span></span> <span data-ttu-id="a44ee-236">因為「**單價**」的 XSD 資料類型是 `fixed14.4` （如上表所述），所以這是第一個使用的轉換：</span><span class="sxs-lookup"><span data-stu-id="a44ee-236">Because the XSD data type of **UnitPrice** is `fixed14.4`, as described in the previous table, this is the first conversion that is used:</span></span>  
  
```  
CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 <span data-ttu-id="a44ee-237">算數運算子會將其運算元轉換為 `number` XPath 資料類型，因此會在值轉換為 `float(53)` (`float(53)` 接近 XPath `number` 資料類型) 之處套用第二個轉換 (從一個 XPath 資料類型轉換為另一個 XPath 資料類型)：</span><span class="sxs-lookup"><span data-stu-id="a44ee-237">Because the arithmetic operators convert their operands to the `number` XPath data type, the second conversion (from one XPath data type to another XPath data type) is applied in which the value is converted to `float(53)` (`float(53)` is close to the XPath `number` data type):</span></span>  
  
```  
CONVERT(float(53), CONVERT(money, OrderDetail.UnitPrice))   
```  
  
 <span data-ttu-id="a44ee-238">假設**orderqty**屬性沒有 XSD 資料類型，則會在單一轉換中將**orderqty**轉換成 `number` XPath 資料類型：</span><span class="sxs-lookup"><span data-stu-id="a44ee-238">Assuming the **OrderQty** attribute has no XSD data type, **OrderQty** is converted to a `number` XPath data type in a single conversion:</span></span>  
  
```  
CONVERT(float(53), OrderDetail.OrderQty)  
```  
  
 <span data-ttu-id="a44ee-239">同樣地，值 98 會轉換為 `number` XPath 資料類型：</span><span class="sxs-lookup"><span data-stu-id="a44ee-239">Similarly, the value 98 is converted to the `number` XPath data type:</span></span>  
  
```  
CONVERT(float(53), 98)  
```  
  
> [!NOTE]  
>  <span data-ttu-id="a44ee-240">如果在結構描述中使用的 XSD 資料類型與資料庫中的基礎 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資料類型不相容，或者如果執行不可能的 XPath 資料類型轉換，[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 可能會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="a44ee-240">If the XSD data type used in the schema is incompatible with the underlying [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] data type in the database, or if an impossible XPath data type conversion is performed, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] may return an error.</span></span> <span data-ttu-id="a44ee-241">例如，如果將 [**員工**] 屬性標注為 [ `id-prefix` 注釋]，XPath 會 `Employee[@EmployeeID=1]` 產生錯誤，因為「**員工**」具有 `id-prefix` 批註，而且無法轉換成 `number` 。</span><span class="sxs-lookup"><span data-stu-id="a44ee-241">For example, if the **EmployeeID** attribute is annotated with `id-prefix` annotation, the XPath `Employee[@EmployeeID=1]` generates an error, because **EmployeeID** has the `id-prefix` annotation and cannot be converted to `number`.</span></span>  
  
  
