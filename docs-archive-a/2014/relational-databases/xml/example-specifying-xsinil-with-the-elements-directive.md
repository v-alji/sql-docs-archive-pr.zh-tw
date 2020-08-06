---
title: 範例：使用 ELEMENTS 指示詞指定 XSINIL | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, specifying XSINIL example
ms.assetid: 07c873ff-1f9d-480e-8536-862c39eb8249
author: rothja
ms.author: jroth
ms.openlocfilehash: 7817d2c72909ca66fb9fac10f8fcb32a759faf56
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686856"
---
# <a name="example-specifying-xsinil-with-the-elements-directive"></a><span data-ttu-id="d0a7d-102">範例：使用 ELEMENTS 指示詞指定 XSINIL</span><span class="sxs-lookup"><span data-stu-id="d0a7d-102">Example: Specifying XSINIL with the ELEMENTS Directive</span></span>
  <span data-ttu-id="d0a7d-103">下列查詢會指定 `ELEMENTS` 指示詞，從查詢結果產生元素中心的 XML。</span><span class="sxs-lookup"><span data-stu-id="d0a7d-103">The following query specifies the `ELEMENTS` directive to generate element-centric XML from the query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0a7d-104">範例</span><span class="sxs-lookup"><span data-stu-id="d0a7d-104">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, Name, Color  
FROM Production.Product  
FOR XML RAW, ELEMENTS;  
GO  
```  
  
 <span data-ttu-id="d0a7d-105">以下是部份結果。</span><span class="sxs-lookup"><span data-stu-id="d0a7d-105">This is the partial result.</span></span>  
  
```  
<row>  
  <ProductID>1</ProductID>  
  <Name>Adjustable Race</Name>  
</row>  
...  
<row>  
  <ProductID>317</ProductID>  
  <Name>LL Crankarm</Name>  
  <Color>Black</Color>  
</row>  
```  
  
 <span data-ttu-id="d0a7d-106">因為某些產品的 `Color` 資料行是 Null 值，所以產生的 XML 不會產生對應的 <`Color`> 元素。</span><span class="sxs-lookup"><span data-stu-id="d0a7d-106">Because the `Color` column has null values for some products, the resulting XML will not generate the corresponding <`Color`> element.</span></span> <span data-ttu-id="d0a7d-107">在 `XSINIL` 後面加上 `ELEMENTS` 指示詞，則即使結果集中的 Color 值為 NULL，還是可以為其產生 <`Color`> 元素。</span><span class="sxs-lookup"><span data-stu-id="d0a7d-107">By adding the `XSINIL` directive with `ELEMENTS`, you can generate the <`Color`> element even for NULL color values in the result set.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductID, Name, Color  
FROM Production.Product  
FOR XML RAW, ELEMENTS XSINIL ;  
```  
  
 <span data-ttu-id="d0a7d-108">以下是部份結果：</span><span class="sxs-lookup"><span data-stu-id="d0a7d-108">This is the partial result:</span></span>  
  
```  
<row xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">  
  <ProductID>1</ProductID>  
  <Name>Adjustable Race</Name>  
  <Color xsi:nil="true" />  
</row>  
...  
<row>  
  <ProductID>317</ProductID>  
  <Name>LL Crankarm</Name>  
  <Color>Black</Color>  
</row>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d0a7d-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d0a7d-109">See Also</span></span>  
 [<span data-ttu-id="d0a7d-110">搭配 FOR XML 使用 RAW 模式</span><span class="sxs-lookup"><span data-stu-id="d0a7d-110">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
