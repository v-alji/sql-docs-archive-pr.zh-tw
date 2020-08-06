---
title: 範例：以 XML 的形式擷取產品型號資訊 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving XML information example
ms.assetid: 3828b4ca-3ab2-444f-9c58-8be6e7f064a6
author: rothja
ms.author: jroth
ms.openlocfilehash: d580f53c4b5185a8b1b1467c75a08fc6929bdcf1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596576"
---
# <a name="example-retrieving-product-model-information-as-xml"></a><span data-ttu-id="7217f-102">範例：將產品型號資訊當做 XML 來擷取</span><span class="sxs-lookup"><span data-stu-id="7217f-102">Example: Retrieving Product Model Information as XML</span></span>
  <span data-ttu-id="7217f-103">下列查詢會傳回產品型號資訊。</span><span class="sxs-lookup"><span data-stu-id="7217f-103">The following query returns product model information.</span></span> <span data-ttu-id="7217f-104">`RAW` 模式是在 `FOR XML` 子句中指定。</span><span class="sxs-lookup"><span data-stu-id="7217f-104">`RAW` mode is specified in the `FOR XML` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7217f-105">範例</span><span class="sxs-lookup"><span data-stu-id="7217f-105">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW;  
GO  
```  
  
 <span data-ttu-id="7217f-106">以下是部份結果：</span><span class="sxs-lookup"><span data-stu-id="7217f-106">This is the partial result:</span></span>  
  
 `<row ProductModelID="122" Name="All-Purpose Bike Stand" />`  
  
 `<row ProductModelID="119" Name="Bike Wash" />`  
  
 <span data-ttu-id="7217f-107">您可以指定 `ELEMENTS` 指示詞，以擷取元素中心的 XML。</span><span class="sxs-lookup"><span data-stu-id="7217f-107">You can retrieve element-centric XML by specifying the `ELEMENTS` directive.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 <span data-ttu-id="7217f-108">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="7217f-108">This is the result:</span></span>  
  
```  
<row>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</row>  
<row>  
  <ProductModelID>119</ProductModelID>  
  <Name>Bike Wash</Name>  
</row>  
```  
  
 <span data-ttu-id="7217f-109">您可以選擇性地指定 `TYPE` 指示詞，將結果擷取為 `xml` 類型。</span><span class="sxs-lookup"><span data-stu-id="7217f-109">You can optionally specify the `TYPE` directive to retrieve the results as `xml` type.</span></span> <span data-ttu-id="7217f-110">`TYPE` 指示詞不會變更結果的內容，</span><span class="sxs-lookup"><span data-stu-id="7217f-110">The `TYPE` directive does not change the content of the results.</span></span> <span data-ttu-id="7217f-111">只會影響結果的資料類型。</span><span class="sxs-lookup"><span data-stu-id="7217f-111">Only the data type of the results is affected.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID, Name  
FROM Production.ProductModel  
WHERE ProductModelID=122 or ProductModelID=119  
FOR XML RAW, TYPE ;  
GO  
```  
  
## <a name="see-also"></a><span data-ttu-id="7217f-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7217f-112">See Also</span></span>  
 [<span data-ttu-id="7217f-113">搭配 FOR XML 使用 RAW 模式</span><span class="sxs-lookup"><span data-stu-id="7217f-113">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
