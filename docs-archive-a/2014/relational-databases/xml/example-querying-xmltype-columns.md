---
title: 範例：查詢 XMLType 資料行 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, querying XML example
ms.assetid: d9f3710d-7a2e-4abe-9c02-3e3c0df4d620
author: rothja
ms.author: jroth
ms.openlocfilehash: 0eedfa5a5a265f3715a76a6ca80d489bbec199bd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585174"
---
# <a name="example-querying-xmltype-columns"></a><span data-ttu-id="b4a19-102">範例：查詢 XMLType 資料行</span><span class="sxs-lookup"><span data-stu-id="b4a19-102">Example: Querying XMLType Columns</span></span>
  <span data-ttu-id="b4a19-103">下列查詢包含 `xml` 類型的資料行。</span><span class="sxs-lookup"><span data-stu-id="b4a19-103">The following query includes columns of `xml` type.</span></span> <span data-ttu-id="b4a19-104">此查詢會從 `xml` 類型之 `Instructions` 資料行的第一個位置，擷取產品型號識別碼、名稱和製造步驟。</span><span class="sxs-lookup"><span data-stu-id="b4a19-104">The query retrieves product model ID, name, and manufacturing steps at the first location from the `Instructions` column of the `xml` type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b4a19-105">範例</span><span class="sxs-lookup"><span data-stu-id="b4a19-105">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
')   
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData')  
GO  
```  
  
 <span data-ttu-id="b4a19-106">以下為結果。</span><span class="sxs-lookup"><span data-stu-id="b4a19-106">The following is the result.</span></span> <span data-ttu-id="b4a19-107">請注意，此資料表只儲存某些產品型號的製造指示。</span><span class="sxs-lookup"><span data-stu-id="b4a19-107">Note that the table stores manufacturing instructions for only some product models.</span></span> <span data-ttu-id="b4a19-108">製造步驟會當做結果中 <`ProductModelData`> 元素的子元素傳回。</span><span class="sxs-lookup"><span data-stu-id="b4a19-108">The manufacturing steps are returned as subelements of the <`ProductModelData`> element in the result.</span></span>  
  
```  
<ProductModelData ProductModelID="5" Name="HL Mountain Frame" />  
<ProductModelData ProductModelID="6" Name="HL Road Frame" />  
<ProductModelData ProductModelID="7" Name="HL Touring Frame">  
    <MI:step> ... </MI:step>  
    <MI:step> ... </MI:step>  
 </ProductModelData>  
```  
  
 <span data-ttu-id="b4a19-109">如果查詢對 XQuery 傳回的 XML 指定資料行名稱 (如下列 `SELECT` 陳述式所指定)，則製造步驟會包在具有指定之名稱的元素中。</span><span class="sxs-lookup"><span data-stu-id="b4a19-109">If the query specifies a column name for the XML returned by the XQuery, as specified in the following `SELECT` statement, the manufacturing steps are wrapped in the element that has the specified name.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
') as ManuSteps  
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData')  
go  
```  
  
 <span data-ttu-id="b4a19-110">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="b4a19-110">This is the result:</span></span>  
  
```  
<ProductModelData ProductModelID="5" Name="HL Mountain Frame" />  
<ProductModelData ProductModelID="6" Name="HL Road Frame" />  
<ProductModelData ProductModelID="7" Name="HL Touring Frame">  
  <ManuSteps>  
    <MI:step ... </MI:step>  
    <MI:step ... </MI:step>  
  </ManuSteps>  
</ProductModelData>  
```  
  
 <span data-ttu-id="b4a19-111">下列查詢指定了 `ELEMENTS` 指示詞。</span><span class="sxs-lookup"><span data-stu-id="b4a19-111">The following query specifies the `ELEMENTS` directive.</span></span> <span data-ttu-id="b4a19-112">因此，傳回的結果會是元素中心的。</span><span class="sxs-lookup"><span data-stu-id="b4a19-112">Therefore, the result returned is element-centric.</span></span> <span data-ttu-id="b4a19-113">與 `XSINIL` 指示詞一起指定的 `ELEMENTS` 選項會傳回 <`ManuSteps`> 元素，即使資料列集內相對應的資料行是 NULL 也一樣。</span><span class="sxs-lookup"><span data-stu-id="b4a19-113">The `XSINIL` option specified with the `ELEMENTS` directive returns the <`ManuSteps`> elements, even if the corresponding column in the rowset is NULL.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name,  
   Instructions.query('  
declare namespace MI="https://schemas.microsoft.com/sqlserver/2004/07/adventure-works/ProductModelManuInstructions"  
   /MI:root/MI:Location[1]/MI:step  
') as ManuSteps  
FROM Production.ProductModel  
FOR XML RAW ('ProductModelData'), root('MyRoot'), ELEMENTS XSINIL  
go  
```  
  
 <span data-ttu-id="b4a19-114">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="b4a19-114">This is the result:</span></span>  
  
```  
<MyRoot xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
   ...  
  <ProductModelData>  
    <ProductModelID>6</ProductModelID>  
    <Name>HL Road Frame</Name>  
    <ManuSteps xsi:nil="true" />  
  </ProductModelData>  
  <ProductModelData>  
    <ProductModelID>7</ProductModelID>  
    <Name>HL Touring Frame</Name>  
    <ManuSteps>  
      <MI:step ... </MI:step>  
      <MI:step ...</MI:step>  
       ...  
    </ManuSteps>  
  </ProductModelData>  
</MyRoot>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b4a19-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4a19-115">See Also</span></span>  
 [<span data-ttu-id="b4a19-116">搭配 FOR XML 使用 RAW 模式</span><span class="sxs-lookup"><span data-stu-id="b4a19-116">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
