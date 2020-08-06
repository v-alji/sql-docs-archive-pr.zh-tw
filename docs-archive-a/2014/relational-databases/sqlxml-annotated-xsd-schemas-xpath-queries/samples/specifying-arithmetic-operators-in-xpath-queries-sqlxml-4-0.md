---
title: 在 XPath 查詢中指定算術運算子 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- arithmetic operators
- XPath operators [SQLXML]
- XPath queries [SQLXML], arithmetic operators
- operators [SQLXML]
ms.assetid: fdfbc87d-759f-4abc-acf5-a21de01f78d3
author: rothja
ms.author: jroth
ms.openlocfilehash: 904f3b920029d45d1b72641a19e2ac07befd4def
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585236"
---
# <a name="specifying-arithmetic-operators-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="7c18d-102">在 XPath 查詢中指定算術運算子 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="7c18d-102">Specifying Arithmetic Operators in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="7c18d-103">下列範例示範如何在 XPath 查詢中指定算術運算子。</span><span class="sxs-lookup"><span data-stu-id="7c18d-103">The following example shows how arithmetic operators are specified in XPath queries.</span></span> <span data-ttu-id="7c18d-104">此範例中的 XPath 查詢會針對 SampleSchema1.xml 中包含的對應結構描述來指定。</span><span class="sxs-lookup"><span data-stu-id="7c18d-104">The XPath query in this example is specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="7c18d-105">如需此範例架構的詳細資訊，請參閱[XPath 範例的範例批註式 XSD 架構 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="7c18d-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="7c18d-106">範例</span><span class="sxs-lookup"><span data-stu-id="7c18d-106">Examples</span></span>  
  
### <a name="a-specify-the--arithmetic-operator"></a><span data-ttu-id="7c18d-107">A.</span><span class="sxs-lookup"><span data-stu-id="7c18d-107">A.</span></span> <span data-ttu-id="7c18d-108">指定 \* 算術運算子</span><span class="sxs-lookup"><span data-stu-id="7c18d-108">Specify the \* arithmetic operator</span></span>  
 <span data-ttu-id="7c18d-109">這個 XPath 查詢會傳回符合指定之述詞 **\<OrderDetail>** 的元素：</span><span class="sxs-lookup"><span data-stu-id="7c18d-109">This XPath query returns **\<OrderDetail>** elements that satisfy the predicate specified:</span></span>  
  
```  
/child::OrderDetail[@UnitPrice * @Quantity = 12.350]  
```  
  
 <span data-ttu-id="7c18d-110">在查詢中， `child` 是軸而且 `OrderDetail` 是節點測試 (TRUE 如果**OrderDetail**是 **\<element node>** ，因為 **\<element>** 節點是軸) 的主要節點 `child` 。</span><span class="sxs-lookup"><span data-stu-id="7c18d-110">In the query, `child` is the axis and `OrderDetail` is the node test (TRUE if **OrderDetail** is an **\<element node>**, because the **\<element>** node is the primary node for the `child` axis).</span></span> <span data-ttu-id="7c18d-111">對於所有 **\<OrderDetail>** 元素節點，會套用述詞中的測試，而且只會傳回滿足條件的節點。</span><span class="sxs-lookup"><span data-stu-id="7c18d-111">For all the **\<OrderDetail>** element nodes, the test in the predicate is applied, and only those nodes that satisfy the condition are returned.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7c18d-112">XPath 中的數字為雙精確度浮點數，而且在範例中比較浮點數會造成四捨五入。</span><span class="sxs-lookup"><span data-stu-id="7c18d-112">The numbers in XPath are double-precision floating-point numbers, and comparing floating-point numbers as in the example causes rounding.</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="7c18d-113">針對對應的結構描述測試 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="7c18d-113">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="7c18d-114">複製[範例架構程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="7c18d-114">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="7c18d-115">將檔案儲存為 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="7c18d-115">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="7c18d-116">建立下列範本 (ArithmeticOperatorA.xml)，並將其儲存在儲存 SampleSchema1.xml 的目錄中。</span><span class="sxs-lookup"><span data-stu-id="7c18d-116">Create the following template (ArithmeticOperatorA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /OrderDetail[@UnitPrice * @OrderQty = 12.350]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="7c18d-117">針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="7c18d-117">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="7c18d-118">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="7c18d-118">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="7c18d-119">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="7c18d-119">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="7c18d-120">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="7c18d-120">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
```  
Here is the partial result set of the template execution:    
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-709" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
  <OrderDetail ProductID="Prod-710" UnitPrice="6.175" OrderQty="2" UnitPriceDiscount="0" />   
   ...  
</ROOT>  
```  
  
  
