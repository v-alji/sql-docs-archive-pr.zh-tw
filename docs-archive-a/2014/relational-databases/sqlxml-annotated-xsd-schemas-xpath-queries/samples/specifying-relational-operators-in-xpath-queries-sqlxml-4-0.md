---
title: 在 XPath 查詢中指定關聯式運算子 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], relational operators
- relational operators [SQLXML]
- XPath operators [SQLXML]
- operators [SQLXML]
ms.assetid: 177a0eb2-11ef-4459-a317-485a433ee769
author: rothja
ms.author: jroth
ms.openlocfilehash: 50d59ebd3a776386c61f4c3a8a1e892d30981d1b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585224"
---
# <a name="specifying-relational-operators-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="c87c4-102">在 XPath 查詢中指定關係運算子 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="c87c4-102">Specifying Relational Operators in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="c87c4-103">下列範例示範如何在 XPath 查詢中指定關係運算子。</span><span class="sxs-lookup"><span data-stu-id="c87c4-103">The following examples show how relational operators are specified in XPath queries.</span></span> <span data-ttu-id="c87c4-104">這些範例中的 XPath 查詢會針對 SampleSchema1.xml 中包含的對應結構描述來指定。</span><span class="sxs-lookup"><span data-stu-id="c87c4-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="c87c4-105">如需此範例架構的詳細資訊，請參閱[XPath 範例的範例批註式 XSD 架構 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="c87c4-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="c87c4-106">範例</span><span class="sxs-lookup"><span data-stu-id="c87c4-106">Examples</span></span>  
  
### <a name="a-specify-relational-operator"></a><span data-ttu-id="c87c4-107">A.</span><span class="sxs-lookup"><span data-stu-id="c87c4-107">A.</span></span> <span data-ttu-id="c87c4-108">指定關係運算子</span><span class="sxs-lookup"><span data-stu-id="c87c4-108">Specify relational operator</span></span>  
 <span data-ttu-id="c87c4-109">這個 XPath 查詢會傳回元素的子項目 **\<Customer>** ，其中**CustomerID**屬性值為 "1"，而任何子 **\<Order>** 元素包含 **\<OrderDetail>** 具有值大於3之**OrderQty**屬性的子系：</span><span class="sxs-lookup"><span data-stu-id="c87c4-109">This XPath query returns the child elements of the **\<Customer>** element where the **CustomerID** attribute value is "1" and where any child **\<Order>** elements contain an **\<OrderDetail>** child with a **OrderQty** attribute with a value greater than 3:</span></span>  
  
```  
/child::Customer[@CustomerID="1"]/Order/OrderDetail[@OrderQty > 3]  
```  
  
 <span data-ttu-id="c87c4-110">括弧中指定的述詞會篩選 **\<Customer>** 元素。</span><span class="sxs-lookup"><span data-stu-id="c87c4-110">The predicate specified in the brackets filters the **\<Customer>** elements.</span></span> <span data-ttu-id="c87c4-111">只 **\<Customer>** 會傳回至少有一個 **\<OrderDetail>** 具有大於3之 OrderQty 屬性值的孫元素。</span><span class="sxs-lookup"><span data-stu-id="c87c4-111">Only the **\<Customer>** elements that have at least one **\<OrderDetail>** grandchild with a OrderQty attribute value greater than 3 are returned.</span></span>  
  
 <span data-ttu-id="c87c4-112">`child` 軸是預設值。</span><span class="sxs-lookup"><span data-stu-id="c87c4-112">The `child` axis is the default.</span></span> <span data-ttu-id="c87c4-113">因此，此查詢可以指定為：</span><span class="sxs-lookup"><span data-stu-id="c87c4-113">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer[@CustomerID="1"]/Order/OrderDetail[@OrderQty > 3]  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="c87c4-114">針對對應的結構描述測試 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="c87c4-114">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="c87c4-115">複製[範例架構程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="c87c4-115">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="c87c4-116">將檔案儲存為 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="c87c4-116">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="c87c4-117">建立下列範本 (SpecifyRelationalA.xml)，並將其儲存在儲存 SampleSchema1.xml 的目錄中。</span><span class="sxs-lookup"><span data-stu-id="c87c4-117">Create the following template (SpecifyRelationalA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="1"]/Order/OrderDetail[@OrderQty > 3]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="c87c4-118">針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="c87c4-118">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="c87c4-119">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="c87c4-119">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="c87c4-120">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="c87c4-120">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="c87c4-121">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="c87c4-121">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="c87c4-122">以下為範本執行的結果集：</span><span class="sxs-lookup"><span data-stu-id="c87c4-122">Here is the result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <OrderDetail ProductID="Prod-760" UnitPrice="503.3507" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-763" UnitPrice="503.3507" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-766" UnitPrice="503.3507" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-732" UnitPrice="440.1742" OrderQty="4" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-757" UnitPrice="1049.7528" OrderQty="4" UnitPriceDiscount="0" />   
</ROOT>  
```  
  
### <a name="b-specify-relational-operator-in-the-xpath-query-and-use-boolean-function-to-compare-the-result"></a><span data-ttu-id="c87c4-123">B.</span><span class="sxs-lookup"><span data-stu-id="c87c4-123">B.</span></span> <span data-ttu-id="c87c4-124">在 XPath 查詢中指定關係運算子並使用布林函數來比較結果</span><span class="sxs-lookup"><span data-stu-id="c87c4-124">Specify relational operator in the XPath query and use Boolean function to compare the result</span></span>  
 <span data-ttu-id="c87c4-125">此查詢 **\<Order>** 會傳回內容節點的所有元素子系，其**SalesPersonID**屬性值小於270：</span><span class="sxs-lookup"><span data-stu-id="c87c4-125">This query returns all the **\<Order>** element children of the context node that have an **SalesPersonID** attribute value that is less than 270:</span></span>  
  
```  
/child::Customer/child::Order[(attribute::SalesPersonID < 270)=true()]  
```  
  
 <span data-ttu-id="c87c4-126">您可以指定 `attribute` 軸的快速鍵 (@)，而且因為 `child` 軸是預設值，因此可從查詢省略：</span><span class="sxs-lookup"><span data-stu-id="c87c4-126">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Customer/Order[(@SalesPersonID < 270)=true()]  
```  
  
> [!NOTE]  
>  <span data-ttu-id="c87c4-127">在範本中指定此查詢時，< 字元必須是實體編碼，因為 < 字元在 XML 檔中具有特殊意義。</span><span class="sxs-lookup"><span data-stu-id="c87c4-127">When this query is specified in a template, the < character must be entity encoded because the < character has special meaning in an XML document.</span></span> <span data-ttu-id="c87c4-128">在範本中，使用 `<` 來指定 < 字元。</span><span class="sxs-lookup"><span data-stu-id="c87c4-128">In a template, use `<` to specify the < character.</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="c87c4-129">針對對應的結構描述測試 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="c87c4-129">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="c87c4-130">複製[範例架構程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="c87c4-130">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="c87c4-131">將檔案儲存為 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="c87c4-131">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="c87c4-132">建立下列範本 (SpecifyRelationalB.xml)，並將其儲存在儲存 SampleSchema1.xml 的目錄中。</span><span class="sxs-lookup"><span data-stu-id="c87c4-132">Create the following template (SpecifyRelationalB.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
        <sql:xpath-query mapping-schema="SampleSchema1.xml">  
            /Customer/Order[(@SalesPersonID<270)=true()]  
        </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="c87c4-133">針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="c87c4-133">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="c87c4-134">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="c87c4-134">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="c87c4-135">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="c87c4-135">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="c87c4-136">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="c87c4-136">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="c87c4-137">以下為範本執行的部分結果集：</span><span class="sxs-lookup"><span data-stu-id="c87c4-137">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Order SalesOrderID="Ord-46613" SalesPersonID="268"   
         OrderDate="2002-07-01T00:00:00"   
         DueDate="2002-07-13T00:00:00"   
         ShipDate="2002-07-08T00:00:00">  
    <OrderDetail ProductID="Prod-739" UnitPrice="917.9363"   
                 OrderQty="2" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-779" UnitPrice="1491.4221"   
                 OrderQty="1" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-825" UnitPrice="242.1391"   
                 OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
  <Order SalesOrderID="Ord-71919" SalesPersonID="268"  
         OrderDate="2004-06-01T00:00:00"   
         DueDate="2004-06-13T00:00:00"   
         ShipDate="2004-06-08T00:00:00">  
    <OrderDetail ProductID="Prod-961" UnitPrice="534.492"   
                 OrderQty="1" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-965" UnitPrice="534.492"   
                 OrderQty="1" UnitPriceDiscount="0" />   
    <OrderDetail ProductID="Prod-966" UnitPrice="1716.5304"   
                 OrderQty="1" UnitPriceDiscount="0" />   
  </Order>  
  ...  
</ROOT>  
```  
  
  
