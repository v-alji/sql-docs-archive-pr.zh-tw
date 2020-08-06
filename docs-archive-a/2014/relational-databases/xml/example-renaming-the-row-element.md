---
title: 範例：重新命名 &lt;row&gt; 元素 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, renaming <row> example
ms.assetid: b042292a-0b6e-40a3-b254-71c06e626706
author: rothja
ms.author: jroth
ms.openlocfilehash: 39375fa125f451f21d936b3a6897b93928fa2f02
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585173"
---
# <a name="example-renaming-the-ltrowgt-element"></a><span data-ttu-id="5402e-102">範例：重新命名 &lt;row&gt; 元素</span><span class="sxs-lookup"><span data-stu-id="5402e-102">Example: Renaming the &lt;row&gt; Element</span></span>
  <span data-ttu-id="5402e-103">如果是結果集中的每一個資料列，RAW 模式會產生一個 `<row>`元素。</span><span class="sxs-lookup"><span data-stu-id="5402e-103">For each row in the result set, the RAW mode generates an element `<row>`.</span></span> <span data-ttu-id="5402e-104">您可以將一個選擇性引數指定給 RAW 模式，選擇性地為此元素指定另一個名稱，如下列查詢所示。</span><span class="sxs-lookup"><span data-stu-id="5402e-104">You can optionally specify another name for this element by specifying an optional argument to the RAW mode, as shown in this query.</span></span> <span data-ttu-id="5402e-105">此查詢會針對資料列集的每一個資料列，各傳回一個 <`ProductModel`> 元素。</span><span class="sxs-lookup"><span data-stu-id="5402e-105">The query returns a <`ProductModel`> element for each row in the rowset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5402e-106">範例</span><span class="sxs-lookup"><span data-stu-id="5402e-106">Example</span></span>  
  
```  
SELECT ProductModelID, Name   
FROM Production.ProductModel  
WHERE ProductModelID=122  
FOR XML RAW ('ProductModel'), ELEMENTS  
GO  
```  
  
 <span data-ttu-id="5402e-107">以下是結果。</span><span class="sxs-lookup"><span data-stu-id="5402e-107">This is the result.</span></span> <span data-ttu-id="5402e-108">因為已將 `ELEMENTS` 指示詞加入查詢中，所以結果會呈現為元素中心。</span><span class="sxs-lookup"><span data-stu-id="5402e-108">Because the `ELEMENTS` directive is added in the query, the result is element-centric.</span></span>  
  
```  
<ProductModel>  
  <ProductModelID>122</ProductModelID>  
  <Name>All-Purpose Bike Stand</Name>  
</ProductModel>   
```  
  
## <a name="see-also"></a><span data-ttu-id="5402e-109">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5402e-109">See Also</span></span>  
 [<span data-ttu-id="5402e-110">搭配 FOR XML 使用 RAW 模式</span><span class="sxs-lookup"><span data-stu-id="5402e-110">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
