---
title: 在 XPath 查詢中指定布林值述詞 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], predicates
- nested predicates
- successive predicates
- predicates [SQLXML]
- top-level predicates
- Boolean-valued predicates
- multiple predicates
ms.assetid: 5f6e7219-6911-4bca-a54b-56b95e0b43dd
author: rothja
ms.author: jroth
ms.openlocfilehash: 56f2f94ec895c5b76382d5103ca9d518b78cc899
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585231"
---
# <a name="specifying-boolean-valued-predicates-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="e13d4-102">在 XPath 查詢中指定布林值述詞 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="e13d4-102">Specifying Boolean-Valued Predicates in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="e13d4-103">下列範例顯示如何在 XPath 查詢中指定布林值述詞。</span><span class="sxs-lookup"><span data-stu-id="e13d4-103">The following examples show how Boolean-valued predicates are specified in XPath queries.</span></span> <span data-ttu-id="e13d4-104">這些範例中的 XPath 查詢會針對 SampleSchema1.xml 中包含的對應結構描述來指定。</span><span class="sxs-lookup"><span data-stu-id="e13d4-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="e13d4-105">如需此範例架構的詳細資訊，請參閱[XPath 範例的範例批註式 XSD 架構 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="e13d4-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="e13d4-106">範例</span><span class="sxs-lookup"><span data-stu-id="e13d4-106">Examples</span></span>  
  
### <a name="a-specify-multiple-predicates"></a><span data-ttu-id="e13d4-107">A.</span><span class="sxs-lookup"><span data-stu-id="e13d4-107">A.</span></span> <span data-ttu-id="e13d4-108">指定多個述詞</span><span class="sxs-lookup"><span data-stu-id="e13d4-108">Specify multiple predicates</span></span>  
 <span data-ttu-id="e13d4-109">下列 XPath 查詢使用多個述詞來尋找給定訂單識別碼和客戶識別碼的訂單資訊：</span><span class="sxs-lookup"><span data-stu-id="e13d4-109">The following XPath query uses multiple predicates to find order information for a given order ID and a customer ID:</span></span>  
  
```  
/child::Customer[attribute::CustomerID="1"]/child::Order[attribute::OrderID="Ord-43860"]  
```  
  
 <span data-ttu-id="e13d4-110">您可以指定 `attribute` 軸的快速鍵 (@)，而且因為 `child` 軸是預設值，因此可從查詢省略：</span><span class="sxs-lookup"><span data-stu-id="e13d4-110">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Customer[@CustomerID="1"]/Order[@SalesOrderID="Ord-43860"]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="e13d4-111">針對對應的結構描述測試 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="e13d4-111">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="e13d4-112">複製[範例架構程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="e13d4-112">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="e13d4-113">將檔案儲存為 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="e13d4-113">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="e13d4-114">建立下列範本 (BooleanValuedPredicatesA.xml)，並將其儲存在儲存 SampleSchema1.xml 的目錄中。</span><span class="sxs-lookup"><span data-stu-id="e13d4-114">Create the following template (BooleanValuedPredicatesA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="1"]/Order[@SalesOrderID="Ord-43860"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="e13d4-115">針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="e13d4-115">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="e13d4-116">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="e13d4-116">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="e13d4-117">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="e13d4-117">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="e13d4-118">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="e13d4-118">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
     <span data-ttu-id="e13d4-119">結果如下：</span><span class="sxs-lookup"><span data-stu-id="e13d4-119">Here is the result:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <Order SalesOrderID="Ord-43860" SalesPersonID="280" OrderDate="2001-08-01T00:00:00" DueDate="2001-08-13T00:00:00" ShipDate="2001-08-08T00:00:00">  
        <OrderDetail ProductID="Prod-729" UnitPrice="226.8571" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-732" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-738" UnitPrice="220.2496" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-753" UnitPrice="2576.3544" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-756" UnitPrice="1049.7528" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-758" UnitPrice="1049.7528" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-761" UnitPrice="503.3507" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-762" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-763" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-765" UnitPrice="503.3507" OrderQty="2" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-768" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
        <OrderDetail ProductID="Prod-770" UnitPrice="503.3507" OrderQty="1" UnitPriceDiscount="0" />   
      </Order>  
    </ROOT>  
    ```  
  
### <a name="b-specify-successive-and-nested-predicates"></a><span data-ttu-id="e13d4-120">B.</span><span class="sxs-lookup"><span data-stu-id="e13d4-120">B.</span></span> <span data-ttu-id="e13d4-121">指定連續和巢狀述詞</span><span class="sxs-lookup"><span data-stu-id="e13d4-121">Specify successive and nested predicates</span></span>  
 <span data-ttu-id="e13d4-122">下列查詢顯示使用連續述詞。</span><span class="sxs-lookup"><span data-stu-id="e13d4-122">The following query shows using successive predicates.</span></span> <span data-ttu-id="e13d4-123">此查詢 **\<Customer>** 會傳回內容節點的所有子項目，其中具有值為277的**SalesPersonID**屬性，以及值為3的**TerritoryID**屬性：</span><span class="sxs-lookup"><span data-stu-id="e13d4-123">The query returns all the **\<Customer>** child elements of the context node that have both a **SalesPersonID** attribute with a value of 277 and a **TerritoryID** attribute with a value of 3:</span></span>  
  
```  
/child::Customer[attribute::SalesPersonID="277"][attribute::TerritoryID="3"]  
```  
  
 <span data-ttu-id="e13d4-124">查詢 **\<Customer>** 會傳回符合述詞中所指定條件的元素。</span><span class="sxs-lookup"><span data-stu-id="e13d4-124">The query returns the **\<Customer>** elements that satisfy both the conditions specified in the predicates.</span></span>  
  
 <span data-ttu-id="e13d4-125">您可以指定 `attribute` 軸的快速鍵 (@)，而且因為 `child` 軸是預設值，因此可從查詢省略：</span><span class="sxs-lookup"><span data-stu-id="e13d4-125">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Customer[@SalesPersonID="277"][@TerritoryID="3"]  
```  
  
 <span data-ttu-id="e13d4-126">下列 XPath 查詢說明巢狀述詞的使用方式。</span><span class="sxs-lookup"><span data-stu-id="e13d4-126">The following XPath query illustrates the use of nested predicates.</span></span> <span data-ttu-id="e13d4-127">此查詢 **\<Customer>** 會傳回內容節點的所有子專案，其中包含 **\<Order>** 至少一個元素的子項目 **\<Order>** ，其**SalesPersonID**屬性值為2。</span><span class="sxs-lookup"><span data-stu-id="e13d4-127">The query returns all the **\<Customer>** child elements of the context node that include **\<Order>** child elements with at least one **\<Order>** element that has a **SalesPersonID** attribute value of 2.</span></span>  
  
```  
/Customer[Order[@SalesPersonID=2]]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="e13d4-128">針對對應的結構描述測試 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="e13d4-128">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="e13d4-129">複製[範例架構程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="e13d4-129">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="e13d4-130">將檔案儲存為 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="e13d4-130">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="e13d4-131">建立下列範本 (nestedSuccessive.xml)，並將其儲存在儲存 SampleSchema1.xml 的目錄中。</span><span class="sxs-lookup"><span data-stu-id="e13d4-131">Create the following template (nestedSuccessive.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
             /Customer[@SalesPersonID="277"][@TerritoryID="3"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="e13d4-132">針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="e13d4-132">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="e13d4-133">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="e13d4-133">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="e13d4-134">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="e13d4-134">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="e13d4-135">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="e13d4-135">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="e13d4-136">以下為部分結果：</span><span class="sxs-lookup"><span data-stu-id="e13d4-136">The following is a partial result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="22" SalesPersonID="277" TerritoryID="3"   
            AccountNumber="22" CustomerType="S"   
            Orders="Ord-43874 Ord-44519 Ord-46989 Ord-48013 Ord-49130 Ord-50274 Ord-51807 Ord-57113 Ord-63162 Ord-69495">  
    <Order SalesOrderID="Ord-43874" SalesPersonID="277"   
           OrderDate="2001-08-01T00:00:00"   
           DueDate="2001-08-13T00:00:00"   
           ShipDate="2001-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-763" UnitPrice="503.3507"   
                   OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
    ...  
  </Customer>  
  <Customer CustomerID="39" SalesPersonID="277" TerritoryID="3"   
            AccountNumber="39" CustomerType="S"   
            Orders="Ord-47428 Ord-48367 Ord-49529 Ord-50742 Ord-53591 Ord-59051 Ord-65301 Ord-71912">    <Order SalesOrderID="Ord-47428" SalesPersonID="277"   
           OrderDate="2002-09-01T00:00:00"   
           DueDate="2002-09-13T00:00:00"   
           ShipDate="2002-09-08T00:00:00">  
      <OrderDetail ProductID="Prod-759" UnitPrice="563.7528" OrderQty="2" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-769" UnitPrice="563.7528" OrderQty="1" UnitPriceDiscount="0" />   
      ...  
    </Order>  
    ...  
  </Customer>  
  ...  
</ROOT>  
```  
  
### <a name="c-specify-a-top-level-predicate"></a><span data-ttu-id="e13d4-137">C.</span><span class="sxs-lookup"><span data-stu-id="e13d4-137">C.</span></span> <span data-ttu-id="e13d4-138">指定最上層述詞</span><span class="sxs-lookup"><span data-stu-id="e13d4-138">Specify a top-level predicate</span></span>  
 <span data-ttu-id="e13d4-139">下列查詢 **\<Customer>** 會傳回具有元素子系之內容節點的子項目節點 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="e13d4-139">The following query returns the **\<Customer>** child element nodes of the context node that have **\<Order>** element children.</span></span> <span data-ttu-id="e13d4-140">此查詢會測試當做最上層述詞的位置路徑：</span><span class="sxs-lookup"><span data-stu-id="e13d4-140">The query tests the location path as the top-level predicate:</span></span>  
  
```  
/child::Customer[child::Order]  
```  
  
 <span data-ttu-id="e13d4-141">`child` 軸是預設值。</span><span class="sxs-lookup"><span data-stu-id="e13d4-141">The `child` axis is the default.</span></span> <span data-ttu-id="e13d4-142">因此，此查詢可以指定為：</span><span class="sxs-lookup"><span data-stu-id="e13d4-142">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer[Order]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="e13d4-143">針對對應的結構描述測試 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="e13d4-143">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="e13d4-144">複製[範例架構程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="e13d4-144">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="e13d4-145">將檔案儲存為 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="e13d4-145">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="e13d4-146">建立下列範本 (TopLevelPredicate.xml)，並將其儲存在儲存 SampleSchema1.xml 的目錄中。</span><span class="sxs-lookup"><span data-stu-id="e13d4-146">Create the following template (TopLevelPredicate.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[Order]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="e13d4-147">針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="e13d4-147">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="e13d4-148">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="e13d4-148">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="e13d4-149">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="e13d4-149">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="e13d4-150">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="e13d4-150">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="e13d4-151">部分結果如下：</span><span class="sxs-lookup"><span data-stu-id="e13d4-151">Here is the partial result:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="1" SalesPersonID="280" TerritoryID="1" AccountNumber="1" CustomerType="S" Orders="Ord-43860 Ord-44501 Ord-45283 Ord-46042">  
    <Order SalesOrderID="Ord-43860" SalesPersonID="280" OrderDate="2001-08-01T00:00:00" DueDate="2001-08-13T00:00:00" ShipDate="2001-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-729" UnitPrice="226.8571" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-732" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-738" UnitPrice="220.2496" OrderQty="1" UnitPriceDiscount="0" />   
      ...  
    </Order>  
    <Order SalesOrderID="Ord-44501" SalesPersonID="280" OrderDate="2001-11-01T00:00:00" DueDate="2001-11-13T00:00:00" ShipDate="2001-11-08T00:00:00">  
      <OrderDetail ProductID="Prod-725" UnitPrice="226.8571" OrderQty="3" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-726" UnitPrice="226.8571" OrderQty="2" UnitPriceDiscount="0" />   
      ...  
    </Order>    ...  
  </Customer>  
  ...  
</ROOT>  
```  
  
  
