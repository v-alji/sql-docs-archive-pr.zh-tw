---
title: 在 XPath 查詢中指定布林運算子 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath operators [SQLXML]
- OR operator
- Boolean operators
- XPath queries [SQLXML], Boolean operators
- operators [SQLXML]
ms.assetid: 9928cff5-62ac-42aa-96bf-2e09a1df0bc3
author: rothja
ms.author: jroth
ms.openlocfilehash: 02dd6e1f120b53382ce984684ea352b36d34b768
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585232"
---
# <a name="specifying-boolean-operators-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="13f27-102">在 XPath 查詢中指定布林運算子 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="13f27-102">Specifying Boolean Operators in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="13f27-103">下列範例顯示如何在 XPath 查詢中指定布林運算子。</span><span class="sxs-lookup"><span data-stu-id="13f27-103">The following example shows how Boolean operators are specified in XPath queries.</span></span> <span data-ttu-id="13f27-104">此範例中的 XPath 查詢會針對 SampleSchema1.xml 中包含的對應結構描述來指定。</span><span class="sxs-lookup"><span data-stu-id="13f27-104">The XPath query in this example is specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="13f27-105">如需此範例架構的詳細資訊，請參閱[XPath 範例的範例批註式 XSD 架構 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="13f27-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="13f27-106">範例</span><span class="sxs-lookup"><span data-stu-id="13f27-106">Examples</span></span>  
  
### <a name="a-specify-the-or-boolean-operator"></a><span data-ttu-id="13f27-107">A.</span><span class="sxs-lookup"><span data-stu-id="13f27-107">A.</span></span> <span data-ttu-id="13f27-108">指定 OR 布林運算子</span><span class="sxs-lookup"><span data-stu-id="13f27-108">Specify the OR Boolean operator</span></span>  
 <span data-ttu-id="13f27-109">這個 XPath 查詢會傳回 **\<Customer>** **CustomerID**屬性值為13或31之內容節點的元素子系：</span><span class="sxs-lookup"><span data-stu-id="13f27-109">This XPath query returns the **\<Customer>** element children of the context node with the **CustomerID** attribute value of 13 or 31:</span></span>  
  
```  
/child::Customer[attribute::CustomerID="13" or attribute::CustomerID="31"]  
```  
  
 <span data-ttu-id="13f27-110">您可以指定 `attribute` 軸的快速鍵 (@)，而且因為 `child` 軸是預設值，因此可省略：</span><span class="sxs-lookup"><span data-stu-id="13f27-110">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted:</span></span>  
  
```  
/Customer[@CustomerID="13" or @CustomerID="31"]  
```  
  
 <span data-ttu-id="13f27-111">在述詞中， `attribute` 是軸， `CustomerID` 如果**CustomerID**是節點，則為節點測試 (TRUE **\<attribute>** ，因為 **\<attribute>** 節點是軸) 的主要節點 `attribute` 。</span><span class="sxs-lookup"><span data-stu-id="13f27-111">In the predicate, `attribute` is the axis and `CustomerID` is the node test (TRUE if **CustomerID** is an **\<attribute>** node, because the **\<attribute>** node is the primary node for the `attribute` axis).</span></span> <span data-ttu-id="13f27-112">述詞會篩選項目 **\<Customer>** ，並只傳回滿足述詞中所指定條件的元素。</span><span class="sxs-lookup"><span data-stu-id="13f27-112">The predicate filters the **\<Customer>** elements and returns only those that satisfy the condition specified in the predicate.</span></span>  
  
##### <a name="to-test-the-xpath-queries-against-the-mapping-schema"></a><span data-ttu-id="13f27-113">針對對應的結構描述測試 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="13f27-113">To test the XPath queries against the mapping schema</span></span>  
  
1.  <span data-ttu-id="13f27-114">複製[範例架構程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="13f27-114">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="13f27-115">將檔案儲存為 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="13f27-115">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="13f27-116">建立下列範本 (BooleanOperatorsA.xml)，並將其儲存在儲存 SampleSchema1.xml 的目錄中。</span><span class="sxs-lookup"><span data-stu-id="13f27-116">Create the following template (BooleanOperatorsA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[@CustomerID="13" or @CustomerID="31"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="13f27-117">針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="13f27-117">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="13f27-118">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="13f27-118">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="13f27-119">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="13f27-119">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="13f27-120">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="13f27-120">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="13f27-121">以下為範本執行的結果集：</span><span class="sxs-lookup"><span data-stu-id="13f27-121">Here is the result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="31" SalesPersonID="286" TerritoryID="7" AccountNumber="31" CustomerType="S" Orders="Ord-51803 Ord-69427">  
    <Order SalesOrderID="Ord-51803" SalesPersonID="286" OrderDate="2003-08-01T00:00:00" DueDate="2003-08-13T00:00:00" ShipDate="2003-08-08T00:00:00">  
      <OrderDetail ProductID="Prod-718" UnitPrice="1059.31" OrderQty="1" UnitPriceDiscount="0" />   
      <OrderDetail ProductID="Prod-838" UnitPrice="1059.31" OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
    <Order SalesOrderID="Ord-69427" SalesPersonID="286" OrderDate="2004-05-01T00:00:00" DueDate="2004-05-13T00:00:00" ShipDate="2004-05-08T00:00:00">  
      <OrderDetail ProductID="Prod-835" UnitPrice="440.1742" OrderQty="1" UnitPriceDiscount="0" />   
    </Order>  
  </Customer>  
</ROOT>  
```  
  
  
