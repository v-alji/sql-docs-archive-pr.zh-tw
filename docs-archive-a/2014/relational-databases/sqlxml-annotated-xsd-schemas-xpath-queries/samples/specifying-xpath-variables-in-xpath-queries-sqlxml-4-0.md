---
title: 在 XPath 查詢中指定 XPath 變數 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- XPath queries [SQLXML], XPath variables
- XPath variables [SQLXML]
ms.assetid: c11ab816-11b8-4131-8b77-c03fe500fa10
author: rothja
ms.author: jroth
ms.openlocfilehash: 5045831f627722f7dbb9a9189be5c48d830f2add
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585221"
---
# <a name="specifying-xpath-variables-in-xpath-queries-sqlxml-40"></a><span data-ttu-id="95a9c-102">在 XPath 查詢中指定 XPath 變數 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="95a9c-102">Specifying XPath Variables in XPath Queries (SQLXML 4.0)</span></span>
  <span data-ttu-id="95a9c-103">下列範例示範如何在 XPath 查詢中傳遞 XPath 變數。</span><span class="sxs-lookup"><span data-stu-id="95a9c-103">The following examples show how XPath variables are passed in XPath queries.</span></span> <span data-ttu-id="95a9c-104">這些範例中的 XPath 查詢會針對 SampleSchema1.xml 中包含的對應結構描述來指定。</span><span class="sxs-lookup"><span data-stu-id="95a9c-104">The XPath queries in these examples are specified against the mapping schema contained in SampleSchema1.xml.</span></span> <span data-ttu-id="95a9c-105">如需此範例架構的詳細資訊，請參閱[XPath 範例的範例批註式 XSD 架構 &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)。</span><span class="sxs-lookup"><span data-stu-id="95a9c-105">For information about this sample schema, see [Sample Annotated XSD Schema for XPath Examples &#40;SQLXML 4.0&#41;](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="95a9c-106">範例</span><span class="sxs-lookup"><span data-stu-id="95a9c-106">Examples</span></span>  
  
### <a name="a-use-the-xpath-variables"></a><span data-ttu-id="95a9c-107">A.</span><span class="sxs-lookup"><span data-stu-id="95a9c-107">A.</span></span> <span data-ttu-id="95a9c-108">使用 XPath 變數</span><span class="sxs-lookup"><span data-stu-id="95a9c-108">Use the XPath variables</span></span>  
 <span data-ttu-id="95a9c-109">範例範本由兩個 XPath 查詢所組成。</span><span class="sxs-lookup"><span data-stu-id="95a9c-109">A sample template consists of two XPath queries.</span></span> <span data-ttu-id="95a9c-110">每個 XPath 查詢都會採用一個參數。</span><span class="sxs-lookup"><span data-stu-id="95a9c-110">Each of the XPath queries takes one parameter.</span></span> <span data-ttu-id="95a9c-111">此範本也會指定這些參數的預設值。</span><span class="sxs-lookup"><span data-stu-id="95a9c-111">The template also specifies default values for these parameters.</span></span> <span data-ttu-id="95a9c-112">如果未指定參數值，則會使用預設值。</span><span class="sxs-lookup"><span data-stu-id="95a9c-112">The default values are used if parameter values are not specified.</span></span> <span data-ttu-id="95a9c-113">中指定了兩個具有預設值的參數 **\<sql:header>** 。</span><span class="sxs-lookup"><span data-stu-id="95a9c-113">Two parameters with default values are specified in **\<sql:header>**.</span></span>  
  
```  
<ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
  <sql:header>  
     <sql:param name='CustomerID'>1</sql:param>  
     <sql:param name='ContactID'>1</sql:param>   
  </sql:header>  
  <sql:xpath-query mapping-schema="SampleSchema1.xml">  
    Customer[@CustomerID=$CustomerID]   
  </sql:xpath-query >  
  <sql:xpath-query mapping-schema="SampleSchema1.xml">  
   Contact[@ContactID=$ContactID]   
  </sql:xpath-query>  
</ROOT>  
```  
  
##### <a name="to-test-the-xpath-query-against-the-mapping-schema"></a><span data-ttu-id="95a9c-114">針對對應的結構描述測試 XPath 查詢</span><span class="sxs-lookup"><span data-stu-id="95a9c-114">To test the XPath query against the mapping schema</span></span>  
  
1.  <span data-ttu-id="95a9c-115">複製[範例架構程式碼](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md)，並將它貼到文字檔中。</span><span class="sxs-lookup"><span data-stu-id="95a9c-115">Copy the [sample schema code](sample-annotated-xsd-schema-for-xpath-examples-sqlxml-4-0.md) and paste it into a text file.</span></span> <span data-ttu-id="95a9c-116">將檔案儲存為 SampleSchema1.xml。</span><span class="sxs-lookup"><span data-stu-id="95a9c-116">Save the file as SampleSchema1.xml.</span></span>  
  
2.  <span data-ttu-id="95a9c-117">建立下列範本 (XPathVariables.xml)，並將其儲存在目錄中，其中：</span><span class="sxs-lookup"><span data-stu-id="95a9c-117">Create the following template (XPathVariables.xml) and save it in the directory where:</span></span>  
  
    ```  
    <ROOT xmlns:sql="urn:schemas-microsoft-com:xml-sql">  
      <sql:header>  
         <sql:param name='CustomerID'>1</sql:param>  
         <sql:param name='ContactID'>1</sql:param>   
      </sql:header>  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
        Customer[@CustomerID=$CustomerID]   
      </sql:xpath-query >  
      <sql:xpath-query mapping-schema="SampleSchema1.xml">  
       Contact[@ContactID=$ContactID]   
      </sql:xpath-query>  
    </ROOT>  
    ```  
  
     <span data-ttu-id="95a9c-118">針對對應結構描述 (SampleSchema1.xml) 指定的目錄路徑相對於儲存範本的目錄。</span><span class="sxs-lookup"><span data-stu-id="95a9c-118">The directory path specified for the mapping schema (SampleSchema1.xml) is relative to the directory where the template is saved.</span></span> <span data-ttu-id="95a9c-119">您也可以指定絕對路徑，例如：</span><span class="sxs-lookup"><span data-stu-id="95a9c-119">An absolute path also can be specified, for example:</span></span>  
  
    ```  
    mapping-schema="C:\MyDir\SampleSchema1.xml"  
    ```  
  
3.  <span data-ttu-id="95a9c-120">建立和使用 SQLXML 4.0 測試指令碼 (Sqlxml4test.vbs) 以執行範本。</span><span class="sxs-lookup"><span data-stu-id="95a9c-120">Create and use the SQLXML 4.0 Test Script (Sqlxml4test.vbs) to execute the template.</span></span> <span data-ttu-id="95a9c-121">如需詳細資訊，請參閱[使用 ADO 執行 SQLXML 4.0 查詢](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md)。</span><span class="sxs-lookup"><span data-stu-id="95a9c-121">For more information, see [Using ADO to Execute SQLXML 4.0 Queries](../../sqlxml/using-ado-to-execute-sqlxml-4-0-queries.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="95a9c-122">在這個範例中，不會傳遞任何參數。</span><span class="sxs-lookup"><span data-stu-id="95a9c-122">In this example, no parameters are passed.</span></span> <span data-ttu-id="95a9c-123">因此，系統會使用預設的參數值。</span><span class="sxs-lookup"><span data-stu-id="95a9c-123">Therefore, the default parameter values are used.</span></span>  
  
  
