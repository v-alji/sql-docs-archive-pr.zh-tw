---
title: 在 (SQLXML 4.0) 的 XPath 查詢中指定布耳函數 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], Boolean functions
- false function
- not function [SQLXML]
- true function
- Boolean functions
ms.assetid: c72cd333-9294-4d41-84f2-1748bf20e3eb
author: rothja
ms.author: jroth
ms.openlocfilehash: d230c7cd8792066732085b9ce501c0794687d17d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585233"
---
# <a name="specifying-boolean-functions-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="d2bd0-102">在 XPath 查詢中指定布林函數 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="d2bd0-102">Specifying Boolean Functions in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="d2bd0-103">下列範例顯示如何在 XPath 查詢中指定布林函數。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-103">The following examples show how Boolean functions are specified in XPath queries.</span></span> <span data-ttu-id="d2bd0-104">這些範例中的 XPath 查詢會針對 SampleSchema1.xml 中包含的對應結構描述來指定。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="d2bd0-105">如需此範例架構的詳細資訊，請參閱[XPath 範例的範例批註式 XSD 架構 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="d2bd0-106">範例</span><span class="sxs-lookup"><span data-stu-id="d2bd0-106">Examples</span></span>  
  
## <a name="a-specify-the-not-boolean-function"></a><span data-ttu-id="d2bd0-107">A.</span><span class="sxs-lookup"><span data-stu-id="d2bd0-107">A.</span></span> <span data-ttu-id="d2bd0-108">指定 not() 布林函數</span><span class="sxs-lookup"><span data-stu-id="d2bd0-108">Specify the not() Boolean function</span></span>  
 <span data-ttu-id="d2bd0-109">此查詢會傳回 **\<Customer>** 內容節點中沒有子專案的所有子項目 **\<Order>** ：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-109">This query returns all the **\<Customer>** child elements of the context node that do not have **\<Order>** child elements:</span></span>  
  
```  
/child::Customer[not(child::Order)]  
```  
  
 <span data-ttu-id="d2bd0-110">`child` 軸是預設值。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-110">The `child` axis is the default.</span></span> <span data-ttu-id="d2bd0-111">因此，此查詢可以指定為：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-111">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer[not(Order)]  
```  
  
#### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="d2bd0-112">針對對應的結構描述測試 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="d2bd0-112">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="d2bd0-113">複製[範例架構程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-113">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="d2bd0-114">將檔案儲存為 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-114">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="d2bd0-115">建立下列範本 (BooleanFunctionsA.xml)，並將其儲存在儲存 SampleSchema1.xml 的目錄中。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-115">Create the following template (BooleanFunctionsA.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Customer[not(Order)]  
    </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="d2bd0-116">針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-116">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="d2bd0-117">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-117">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="d2bd0-118">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-118">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="d2bd0-119">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-119">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="d2bd0-120">以下為範本執行的部分結果集：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-120">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="32" SalesPersonID="289" TerritoryID="8" AccountNumber="32" CustomerType="S" />   
  <Customer CustomerID="35" SalesPersonID="275" TerritoryID="2" AccountNumber="35" CustomerType="S" />   
  ...  
</ROOT>  
```  
  
## <a name="b-specify-the-true-and-false-boolean-functions"></a><span data-ttu-id="d2bd0-121">B.</span><span class="sxs-lookup"><span data-stu-id="d2bd0-121">B.</span></span> <span data-ttu-id="d2bd0-122">指定 true() 和 false() 布林函數</span><span class="sxs-lookup"><span data-stu-id="d2bd0-122">Specify the true() and false() Boolean functions</span></span>  
 <span data-ttu-id="d2bd0-123">此查詢會傳回沒有 **\<Customer>** 子專案之內容節點的所有元素子系 **\<Order>** 。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-123">This query returns all **\<Customer>** element children of the context node that do not have **\<Order>** child elements.</span></span> <span data-ttu-id="d2bd0-124">在關聯式詞彙中，此查詢會傳回尚未下任何訂單的所有客戶。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-124">In relational terms, this query returns all customers who have not placed any orders.</span></span>  
  
```  
/child::Customer[child::Order=false()]  
```  
  
 <span data-ttu-id="d2bd0-125">`child` 軸是預設值。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-125">The `child` axis is the default.</span></span> <span data-ttu-id="d2bd0-126">因此，此查詢可以指定為：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-126">Therefore, the query can be specified as:</span></span>  
  
```  
/Customer[Order=false()]  
```  
  
 <span data-ttu-id="d2bd0-127">這個查詢相當於下列語法：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-127">This query is equivalent to the following:</span></span>  
  
```  
/Customer[not(Order)]  
```  
  
 <span data-ttu-id="d2bd0-128">下列查詢會傳回至少已經下了一個訂單的所有客戶：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-128">The following query returns all the customers who have placed at least one order:</span></span>  
  
```  
/Customer[Order=true()]  
```  
  
 <span data-ttu-id="d2bd0-129">這個查詢相當於下列語法：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-129">This query is equivalent to this one:</span></span>  
  
```  
/Customer[Order]  
```  
  
#### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="d2bd0-130">針對對應的結構描述測試 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="d2bd0-130">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="d2bd0-131">複製[範例架構程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-131">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="d2bd0-132">將檔案儲存為 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-132">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="d2bd0-133">建立下列範本 (BooleanFunctionsB.xml)，並將其儲存在儲存 SampleSchema1.xml 的目錄中。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-133">Create the following template (BooleanFunctionsB.xml) and save it in the directory where SampleSchema1.xml is saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Customer[Order=false()]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="d2bd0-134">針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-134">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="d2bd0-135">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-135">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="d2bd0-136">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-136">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="d2bd0-137">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="d2bd0-137">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="d2bd0-138">以下為範本執行的部分結果集：</span><span class="sxs-lookup"><span data-stu-id="d2bd0-138">Here is the partial result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Customer CustomerID="13" SalesPersonID="286" TerritoryID="7" AccountNumber="13" CustomerType="S" />   
  <Customer CustomerID="32" SalesPersonID="289" TerritoryID="8" AccountNumber="32" CustomerType="S" />   
  <Customer CustomerID="35" SalesPersonID="275" TerritoryID="2" AccountNumber="35" CustomerType="S" />   
  ...  
</ROOT>  
```  
  
  
