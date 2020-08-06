---
title: 在 XPath 查詢中指定軸 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], axes
- context node [SQLXML]
- attribute axis [SQLXML]
- axis [SQLXML]
- child axis
- parent axis
- axes [SQLXML]
ms.assetid: d17b8278-da58-4576-95b4-7a92772566d8
author: rothja
ms.author: jroth
ms.openlocfilehash: f6f17404ea109bb0e687f9116b61025bbc411008
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585235"
---
# <a name="specifying-axes-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="7936b-102">在 XPath 查詢中指定軸 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="7936b-102">Specifying Axes in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="7936b-103">下列範例顯示如何在 XPath 查詢中指定軸。</span><span class="sxs-lookup"><span data-stu-id="7936b-103">The following examples show how axes are specified in XPath queries.</span></span>  
  
 <span data-ttu-id="7936b-104">這些範例中的 XPath 查詢會針對 SampleSchema1.xml 中包含的對應結構描述來指定。</span><span class="sxs-lookup"><span data-stu-id="7936b-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="7936b-105">如需此範例架構的詳細資訊，請參閱[XPath 範例的範例批註式 XSD 架構 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="7936b-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7936b-106">範例</span><span class="sxs-lookup"><span data-stu-id="7936b-106">Examples</span></span>  
  
### <a name="a-retrieve-child-elements-of-the-context-node"></a><span data-ttu-id="7936b-107">A.</span><span class="sxs-lookup"><span data-stu-id="7936b-107">A.</span></span> <span data-ttu-id="7936b-108">擷取內容節點的子元素</span><span class="sxs-lookup"><span data-stu-id="7936b-108">Retrieve child elements of the context node</span></span>  
 <span data-ttu-id="7936b-109">下列 XPath 查詢會選取 **\<Contact>** 內容節點的所有子項目：</span><span class="sxs-lookup"><span data-stu-id="7936b-109">The following XPath query selects all the **\<Contact>** child elements of the context node:</span></span>  
  
```  
/child::Contact  
```  
  
 <span data-ttu-id="7936b-110">在查詢中， `child` 是軸而且 `Contact` 是節點測試 (TRUE `Contact` （如果是 **\<element>** 節點），因為 \<element> 是與軸) 相關聯的主要節點類型 `child` 。</span><span class="sxs-lookup"><span data-stu-id="7936b-110">In the query, `child` is the axis and `Contact` is the node test (TRUE if `Contact` is an **\<element>** node, because \<element> is the primary node type associated with the `child` axis).</span></span>  
  
 <span data-ttu-id="7936b-111">`child` 軸是預設值。</span><span class="sxs-lookup"><span data-stu-id="7936b-111">The `child` axis is the default.</span></span> <span data-ttu-id="7936b-112">因此，此查詢可以撰寫為：</span><span class="sxs-lookup"><span data-stu-id="7936b-112">Therefore, the query can be written as:</span></span>  
  
```  
/Contact  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="7936b-113">針對對應的結構描述測試 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="7936b-113">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="7936b-114">複製[範例架構程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7936b-114">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="7936b-115">將檔案儲存為 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="7936b-115">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="7936b-116">建立下列範本 (XPathAxesSampleA.xml)，並將其儲存在儲存 SampleSchema1.xml 的目錄中。</span><span class="sxs-lookup"><span data-stu-id="7936b-116">Create the following template (XPathAxesSampleA.xml) and save it in the directory where SampleSchema1.xml was saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Contact  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="7936b-117">針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="7936b-117">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="7936b-118">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="7936b-118">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="7936b-119">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="7936b-119">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="7936b-120">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7936b-120">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="7936b-121">以下為範本執行的部分結果集：</span><span class="sxs-lookup"><span data-stu-id="7936b-121">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">   
  <Contact ContactID="1" LastName="Achong" FirstName="Gustavo" Title="Mr." />   
  <Contact ContactID="2" LastName="Abel" FirstName="Catherine" Title="Ms." />   
  <Contact ContactID="3" LastName="Abercrombie" FirstName="Kim" Title="Ms." />   
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />  
  ...  
</ROOT>  
```  
  
### <a name="b-retrieve-grandchildren-of-the-context-node"></a><span data-ttu-id="7936b-122">B.</span><span class="sxs-lookup"><span data-stu-id="7936b-122">B.</span></span> <span data-ttu-id="7936b-123">擷取內容節點的孫系</span><span class="sxs-lookup"><span data-stu-id="7936b-123">Retrieve grandchildren of the context node</span></span>  
 <span data-ttu-id="7936b-124">下列 XPath 查詢會選取 **\<Order>** **\<Customer>** 內容節點之元素子系的所有元素子系：</span><span class="sxs-lookup"><span data-stu-id="7936b-124">The following XPath query selects all the **\<Order>** element children of the **\<Customer>** element children of the context node:</span></span>  
  
```  
/child::Customer/child::Order  
```  
  
 <span data-ttu-id="7936b-125">在查詢中， `child` 是軸， `Customer` 而和 `Order` 是節點測試 (如果 Customer 和 Order 是節點，這些節點測試就是 TRUE **\<element>** ，因為 **\<element>** 節點是軸) 的主要節點 `child` 。</span><span class="sxs-lookup"><span data-stu-id="7936b-125">In the query, `child` is the axis and `Customer` and `Order` are the node tests (these node tests are TRUE if Customer and Order are **\<element>** nodes, because the **\<element>** node is the primary node for the `child` axis).</span></span> <span data-ttu-id="7936b-126">針對每個符合的節點 **\<Customer>** ，會將符合的節點 **\<Orders>** 加入到結果中。</span><span class="sxs-lookup"><span data-stu-id="7936b-126">For each node matching **\<Customer>**, the nodes matching **\<Orders>** are added to the result.</span></span> <span data-ttu-id="7936b-127">只有 **\<Order>** 在結果集中才會傳回。</span><span class="sxs-lookup"><span data-stu-id="7936b-127">Only **\<Order>** is returned in the result set.</span></span>  
  
 <span data-ttu-id="7936b-128">`child` 軸是預設值。</span><span class="sxs-lookup"><span data-stu-id="7936b-128">The `child` axis is the default.</span></span> <span data-ttu-id="7936b-129">因此，此查詢可以指定為：</span><span class="sxs-lookup"><span data-stu-id="7936b-129">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer/Order  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="7936b-130">針對對應的結構描述測試 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="7936b-130">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="7936b-131">複製[範例架構程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7936b-131">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="7936b-132">將檔案儲存為 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="7936b-132">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="7936b-133">建立下列範本 (XPathAxesSampleB.xml)，並將其儲存在目錄中，其中：</span><span class="sxs-lookup"><span data-stu-id="7936b-133">Create the following template (XPathAxesSampleB.xml) and save it in the directory where:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer/Order  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="7936b-134">針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="7936b-134">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="7936b-135">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="7936b-135">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="7936b-136">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="7936b-136">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="7936b-137">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7936b-137">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="7936b-138">以下為範本執行的部分結果集：</span><span class="sxs-lookup"><span data-stu-id="7936b-138">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="Ord-43860" SalesPersonID="280"   
         OrderDate="2001-08-01T00:00:00"   
         DueDate="2001-08-13T00:00:00"   
         ShipDate="2001-08-08T00:00:00">  
  <OrderDetail ProductID="Prod-729" UnitPrice="226.8571"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-732" UnitPrice="440.1742"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-738" UnitPrice="220.2496"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-753" UnitPrice="2576.3544"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-756" UnitPrice="1049.7528"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-758" UnitPrice="1049.7528"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-761" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-762" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-763" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-765" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-768" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-770" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
   ...  
</ROOT>  
```  
  
 <span data-ttu-id="7936b-139">如果 XPath 查詢指定為，則 `Customer/Order/OrderDetail` 每個符合 **\<Customer>** 查詢的節點都會流覽至其 **\<Order>** 元素。</span><span class="sxs-lookup"><span data-stu-id="7936b-139">If the XPath query is specified as `Customer/Order/OrderDetail`, from each node matching **\<Customer>** the query navigates to its **\<Order>** elements.</span></span> <span data-ttu-id="7936b-140">針對每個符合的節點 **\<Order>** ，查詢會將節點加入 **\<OrderDetail>** 至結果。</span><span class="sxs-lookup"><span data-stu-id="7936b-140">And for each node matching **\<Order>**, the query adds the nodes **\<OrderDetail>** to the result.</span></span> <span data-ttu-id="7936b-141">只有 **\<OrderDetail>** 在結果集中才會傳回。</span><span class="sxs-lookup"><span data-stu-id="7936b-141">Only **\<OrderDetail>** is returned in the result set.</span></span>  
  
### <a name="c-use--to-specify-the-parent-axis"></a><span data-ttu-id="7936b-142">C.</span><span class="sxs-lookup"><span data-stu-id="7936b-142">C.</span></span> <span data-ttu-id="7936b-143">使用 .</span><span class="sxs-lookup"><span data-stu-id="7936b-143">Use ..</span></span> <span data-ttu-id="7936b-144">指定父軸</span><span class="sxs-lookup"><span data-stu-id="7936b-144">to specify the parent axis</span></span>  
 <span data-ttu-id="7936b-145">下列查詢會 **\<Order>** 使用 **\<Customer>** **CustomerID**屬性值為1的父元素，來抓取所有元素。</span><span class="sxs-lookup"><span data-stu-id="7936b-145">The following query retrieves all the **\<Order>** elements with a parent **\<Customer>** element with a **CustomerID** attribute value of 1.</span></span> <span data-ttu-id="7936b-146">查詢會使用 `child` 述詞中的軸來尋找元素的父系 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="7936b-146">The query uses the `child` axis in the predicate to find the parent of the **\<Order>** element.</span></span>  
  
```  
/child::Customer/child::Order[../@CustomerID="1"]  
```  
  
 <span data-ttu-id="7936b-147">`child` 軸是預設軸。</span><span class="sxs-lookup"><span data-stu-id="7936b-147">The `child` axis is the default axis.</span></span> <span data-ttu-id="7936b-148">因此，此查詢可以指定為：</span><span class="sxs-lookup"><span data-stu-id="7936b-148">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer/Order[../@CustomerID="1"]  
```  
  
 <span data-ttu-id="7936b-149">XPath 查詢相當於：</span><span class="sxs-lookup"><span data-stu-id="7936b-149">The XPath query is equivalent to:</span></span>  
  
```  
/Customer[@CustomerID="1"]/Order.  
```  
  
> [!NOTE]  
>  <span data-ttu-id="7936b-150">XPath 查詢 `/Order[../@CustomerID="1"]` 會傳回錯誤，因為沒有的父系 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="7936b-150">The XPath query `/Order[../@CustomerID="1"]` will return an error because there is no parent of **\<Order>**.</span></span> <span data-ttu-id="7936b-151">雖然包含的對應架構中可能有元素，但 **\<Order>** XPath 並未從任何專案開始，因此 **\<Order>** 會被視為檔中的最上層元素類型。</span><span class="sxs-lookup"><span data-stu-id="7936b-151">Although there may be elements in the mapping schema that contain **\<Order>**, the XPath did not begin at any of them; consequently, **\<Order>** is considered to be the top-level element type in the document.</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="7936b-152">針對對應的結構描述測試 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="7936b-152">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="7936b-153">複製[範例架構程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7936b-153">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="7936b-154">將檔案儲存為 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="7936b-154">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="7936b-155">建立下列範本 (XPathAxesSampleC.xml)，並將其儲存在目錄中，其中：</span><span class="sxs-lookup"><span data-stu-id="7936b-155">Create the following template (XPathAxesSampleC.xml) and save it in the directory where:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer/Order[../@CustomerID="1"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="7936b-156">針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="7936b-156">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="7936b-157">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="7936b-157">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="7936b-158">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="7936b-158">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="7936b-159">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7936b-159">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="7936b-160">以下為範本執行的部分結果集：</span><span class="sxs-lookup"><span data-stu-id="7936b-160">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="Ord-43860" SalesPersonID="280"   
         OrderDate="2001-08-01T00:00:00"   
         DueDate="2001-08-13T00:00:00"   
         ShipDate="2001-08-08T00:00:00">  
  <OrderDetail ProductID="Prod-729" UnitPrice="226.8571"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-732" UnitPrice="440.1742"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-738" UnitPrice="220.2496"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-753" UnitPrice="2576.3544"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-756" UnitPrice="1049.7528"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-758" UnitPrice="1049.7528"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-761" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-762" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-763" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-765" UnitPrice="503.3507"   
               OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-768" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-770" UnitPrice="503.3507"   
               OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
   ...  
</Order>  
</ROOT>  
```  
  
### <a name="d-specify-the-attribute-axis"></a><span data-ttu-id="7936b-161">D.</span><span class="sxs-lookup"><span data-stu-id="7936b-161">D.</span></span> <span data-ttu-id="7936b-162">指定屬性軸</span><span class="sxs-lookup"><span data-stu-id="7936b-162">Specify the attribute axis</span></span>  
 <span data-ttu-id="7936b-163">下列 XPath 查詢會選取 **\<Customer>** [ **CustomerID** ] 屬性值為1之內容節點的所有子項目：</span><span class="sxs-lookup"><span data-stu-id="7936b-163">The following XPath query selects all the **\<Customer>** child elements of the context node with a **CustomerID** attribute value of 1:</span></span>  
  
```  
/child::Customer[attribute::CustomerID="1"]  
```  
  
 <span data-ttu-id="7936b-164">在述詞中 `attribute::CustomerID` ， `attribute` 是軸而且 `CustomerID` 是節點測試 (如果 `CustomerID` 是屬性，則節點測試為 TRUE，因為 **\<attribute>** 節點是軸) 的主要節點 `attribute` 。</span><span class="sxs-lookup"><span data-stu-id="7936b-164">In the predicate `attribute::CustomerID`, `attribute` is the axis and `CustomerID` is the node test (if `CustomerID` is an attribute the node test is TRUE, because the **\<attribute>** node is the primary node for the `attribute` axis).</span></span>  
  
 <span data-ttu-id="7936b-165">您可以指定 `attribute` 軸的快速鍵 (@)，而且因為 `child` 是預設軸，因此可從查詢省略：</span><span class="sxs-lookup"><span data-stu-id="7936b-165">A shortcut to the `attribute` axis (@) can be specified, and because `child` is the default axis, it can be omitted from the query:</span></span>  
  
```  
/Customer[@CustomerID="1"]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="7936b-166">針對對應的結構描述測試 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="7936b-166">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="7936b-167">複製[範例架構程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7936b-167">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="7936b-168">將檔案儲存為 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="7936b-168">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="7936b-169">建立下列範本 (XPathAxesSampleD.xml)，並將其儲存在儲存 SampleSchema1.xml 的目錄中。</span><span class="sxs-lookup"><span data-stu-id="7936b-169">Create the following template (XPathAxesSampleD.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        child::Customer[attribute::CustomerID="1"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="7936b-170">針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="7936b-170">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="7936b-171">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="7936b-171">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="7936b-172">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="7936b-172">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="7936b-173">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7936b-173">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="7936b-174">以下為範本執行的部分結果集：</span><span class="sxs-lookup"><span data-stu-id="7936b-174">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" SalesPersonID="280"   
            TerritoryID="1" AccountNumber="1"   
            CustomerType="S" Orders="Ord-43860 Ord-44501 Ord-45283 Ord-46042">  
    <Order SalesOrderID="Ord-43860" SalesPersonID="280"   
           OrderDate="2001-08-01T00:00:00"   
           DueDate="2001-08-13T00:00:00"   
           ShipDate="2001-08-08T00:00:00">  
       <OrderDetail ProductID="Prod-729" UnitPrice="226.8571"   
                    OrderQty="1" UnitPriceDiscount="0" />   
       <OrderDetail ProductID="Prod-732" UnitPrice="440.1742"   
                    OrderQty="1" UnitPriceDiscount="0" />   
       <OrderDetail ProductID="Prod-738" UnitPrice="220.2496"   
                    OrderQty="1" UnitPriceDiscount="0" />   
      ...   
    </Order>  
   ...  
  </Customer>  
</ROOT>  
```  
  
  
