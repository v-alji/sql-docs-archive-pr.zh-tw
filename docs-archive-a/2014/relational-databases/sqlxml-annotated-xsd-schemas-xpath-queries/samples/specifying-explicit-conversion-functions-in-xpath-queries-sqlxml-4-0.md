---
title: 在 XPath 查詢中指定明確轉換函數 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- explicit conversion functions [SQLXML]
- string function
- number function
- XPath queries [SQLXML], explicit conversion functions
ms.assetid: 1111cb5d-2bd9-4bdb-8de2-dc0e47452dd6
author: rothja
ms.author: jroth
ms.openlocfilehash: 5b4b9bd5f5665c8cb86cb74c1397e2bd06e113fb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585228"
---
# <a name="specifying-explicit-conversion-functions-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="0f501-102">在 XPath 查詢中指定明確轉換函數 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="0f501-102">Specifying Explicit Conversion Functions in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="0f501-103">下列範例將示範如何在 XPath 查詢中指定明確轉換函數。</span><span class="sxs-lookup"><span data-stu-id="0f501-103">The following examples show how explicit conversion functions are specified in XPath queries.</span></span> <span data-ttu-id="0f501-104">這些範例中的 XPath 查詢會針對 SampleSchema1.xml 中包含的對應結構描述來指定。</span><span class="sxs-lookup"><span data-stu-id="0f501-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="0f501-105">如需此範例架構的詳細資訊，請參閱[XPath 範例的範例批註式 XSD 架構 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="0f501-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="0f501-106">範例</span><span class="sxs-lookup"><span data-stu-id="0f501-106">Examples</span></span>  
  
### <a name="a-use-the-number-explicit-conversion-function"></a><span data-ttu-id="0f501-107">A.</span><span class="sxs-lookup"><span data-stu-id="0f501-107">A.</span></span> <span data-ttu-id="0f501-108">使用 number() 明確轉換函數</span><span class="sxs-lookup"><span data-stu-id="0f501-108">Use the number() explicit conversion function</span></span>  
 <span data-ttu-id="0f501-109">`number()` 函數會將引數轉換成數字。</span><span class="sxs-lookup"><span data-stu-id="0f501-109">The `number()` function converts an argument to a number.</span></span>  
  
 <span data-ttu-id="0f501-110">假設**ContactID**的值為非數值，則下列查詢會將**ContactID**轉換成數位，並將它與值4進行比較。</span><span class="sxs-lookup"><span data-stu-id="0f501-110">Assuming the value of **ContactID** is nonnumeric, the following query converts **ContactID** to a number and compares it with the value 4.</span></span> <span data-ttu-id="0f501-111">然後，此查詢會傳回內容節點的所有元素子系，其 **\<Employee>** **ContactID**屬性的數值為4：</span><span class="sxs-lookup"><span data-stu-id="0f501-111">The query then returns all **\<Employee>** element children of the context node with the **ContactID** attribute that has a numeric value of 4:</span></span>  
  
```  
/child::Contact[number(attribute::ContactID)= 4]  
```  
  
 <span data-ttu-id="0f501-112">您可以指定 `attribute` 軸的快速鍵 (@)，而且因為 `child` 軸是預設值，因此可從查詢省略：</span><span class="sxs-lookup"><span data-stu-id="0f501-112">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Contact[number(@ContactID) = 4]  
```  
  
 <span data-ttu-id="0f501-113">在關聯式詞彙中，此查詢會傳回**ContactID**為4的員工。</span><span class="sxs-lookup"><span data-stu-id="0f501-113">In relational terms, the query returns an employee with a **ContactID** of 4.</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="0f501-114">針對對應的結構描述測試 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="0f501-114">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="0f501-115">複製[範例架構程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="0f501-115">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="0f501-116">將檔案儲存為 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="0f501-116">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="0f501-117">建立下列範本 (ExplicitConversionA.xml)，並將其儲存在儲存 SampleSchema1.xml 的目錄中。</span><span class="sxs-lookup"><span data-stu-id="0f501-117">Create the following template (ExplicitConversionA.xml) and save it in the directory where SampleSchema1.xml was saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        /Contact[number(@ContactID)=4]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="0f501-118">針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="0f501-118">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="0f501-119">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="0f501-119">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="0f501-120">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="0f501-120">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="0f501-121">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="0f501-121">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="0f501-122">這個範本執行的結果集如下：</span><span class="sxs-lookup"><span data-stu-id="0f501-122">The result set for this template execution is:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
### <a name="b-use-the-string-explicit-conversion-function"></a><span data-ttu-id="0f501-123">B.</span><span class="sxs-lookup"><span data-stu-id="0f501-123">B.</span></span> <span data-ttu-id="0f501-124">使用 string() 明確轉換函數</span><span class="sxs-lookup"><span data-stu-id="0f501-124">Use the string() explicit conversion function</span></span>  
 <span data-ttu-id="0f501-125">`string()` 函數會將引數轉換成字串。</span><span class="sxs-lookup"><span data-stu-id="0f501-125">The `string()` function converts an argument to a string.</span></span>  
  
 <span data-ttu-id="0f501-126">下列查詢會將**ContactID**轉換成字串，並將它與字串值 "4" 進行比較。</span><span class="sxs-lookup"><span data-stu-id="0f501-126">The following query converts **ContactID** to a string and compares it with the string value "4".</span></span> <span data-ttu-id="0f501-127">此查詢會傳回 **\<Employee>** 內容節點的所有元素子系，並具有字串值為 "4" 的**ContactID** ：</span><span class="sxs-lookup"><span data-stu-id="0f501-127">The query returns all **\<Employee>** element children of the context node with a **ContactID** with a string value of "4":</span></span>  
  
```  
/child::Contact[string(attribute::ContactID)="4"]  
```  
  
 <span data-ttu-id="0f501-128">您可以指定 `attribute` 軸的快速鍵 (@)，而且因為 `child` 軸是預設值，因此可從查詢省略：</span><span class="sxs-lookup"><span data-stu-id="0f501-128">A shortcut to the `attribute` axis (@) can be specified, and because the `child` axis is the default, it can be omitted from the query:</span></span>  
  
```  
/Contact[string(@ContactID)="4"]  
```  
  
 <span data-ttu-id="0f501-129">就功能而言，這個函數與上一個範例查詢會傳回相同的結果，不過其評估是針對字串值而非數值 (亦即，數字 4) 進行。</span><span class="sxs-lookup"><span data-stu-id="0f501-129">Functionally, this query returns the same results as the previous example query, though the evaluation is done against a string value and not the numeric value (that is, the number 4).</span></span>  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="0f501-130">針對對應的結構描述測試 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="0f501-130">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="0f501-131">複製[範例架構程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="0f501-131">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="0f501-132">將檔案儲存為 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="0f501-132">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="0f501-133">建立下列範本 (ExplicitConversionB.xml)，並將其儲存在儲存 SampleSchema1.xml 的目錄中。</span><span class="sxs-lookup"><span data-stu-id="0f501-133">Create the following template (ExplicitConversionB.xml) and save it in the directory where SampleSchema1.xml was saved.</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Contact[string(@ContactID)="4"]  
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="0f501-134">針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="0f501-134">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="0f501-135">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="0f501-135">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="0f501-136">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="0f501-136">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span>  
  
     <span data-ttu-id="0f501-137">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="0f501-137">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
 <span data-ttu-id="0f501-138">以下為範本執行的結果集：</span><span class="sxs-lookup"><span data-stu-id="0f501-138">Here is the result set of the template execution:</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <Contact ContactID="4" LastName="Acevedo" FirstName="Humberto" Title="Sr." />   
</ROOT>  
```  
  
  
