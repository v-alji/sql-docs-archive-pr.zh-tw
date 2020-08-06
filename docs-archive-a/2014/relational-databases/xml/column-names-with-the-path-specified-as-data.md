---
title: 以 data() 指定路徑的資料行名稱 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- names [SQL Server], columns with
ms.assetid: 0b738e44-6108-4417-a9a4-abeb7680d899
author: rothja
ms.author: jroth
ms.openlocfilehash: 61aa7f85c7ee2358ddcf99f81c87c1295fac8fb3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87585182"
---
# <a name="column-names-with-the-path-specified-as-data"></a><span data-ttu-id="c85d8-102">以 data() 指定路徑的資料行名稱</span><span class="sxs-lookup"><span data-stu-id="c85d8-102">Column Names with the Path Specified as data()</span></span>
  <span data-ttu-id="c85d8-103">如果以資料行名稱指定的路徑是 "data()"，則在產生的 XML 中會將其值視為不可部分完成值。</span><span class="sxs-lookup"><span data-stu-id="c85d8-103">If the path specified as column name is "data()", the value is treated as an atomic value in the generated XML.</span></span> <span data-ttu-id="c85d8-104">如果序列化的下一個項目也是不可部分完成值，就會在 XML 中加入空白字元。</span><span class="sxs-lookup"><span data-stu-id="c85d8-104">A space character is added to the XML if the next item in the serialization is also an atomic value.</span></span> <span data-ttu-id="c85d8-105">當您建立清單類型的元素與屬性值時，這會非常有用。</span><span class="sxs-lookup"><span data-stu-id="c85d8-105">This is useful when you are creating list typed element and attribute values.</span></span> <span data-ttu-id="c85d8-106">下列查詢會擷取產品型號識別碼、名稱以及該產品型號中的產品清單。</span><span class="sxs-lookup"><span data-stu-id="c85d8-106">The following query retrieves the product model ID, name, and list of products in that product model.</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductModelID       AS "@ProductModelID",  
       Name                 AS "@ProductModelName",  
      (SELECT ProductID AS "data()"  
       FROM   Production.Product  
       WHERE  Production.Product.ProductModelID =   
              Production.ProductModel.ProductModelID  
      FOR XML PATH (''))    AS "@ProductIDs"  
FROM  Production.ProductModel  
WHERE ProductModelID= 7   
FOR XML PATH('ProductModelData');  
```  
  
 <span data-ttu-id="c85d8-107">巢狀 SELECT 會擷取產品識別碼的清單。</span><span class="sxs-lookup"><span data-stu-id="c85d8-107">The nested SELECT retrieves a list of product IDs.</span></span> <span data-ttu-id="c85d8-108">它會將 "data()" 指定為產品識別碼的資料行名稱。</span><span class="sxs-lookup"><span data-stu-id="c85d8-108">It specifies "data()" as the column name for product IDs.</span></span> <span data-ttu-id="c85d8-109">因為 PATH 模式會為資料列元素名稱指定空白字串，所以不會產生任何資料列元素。</span><span class="sxs-lookup"><span data-stu-id="c85d8-109">Because PATH mode specifies an empty string for the row element name, there is no row element generated.</span></span> <span data-ttu-id="c85d8-110">而是會以指派給父項 SELECT 中 <`ProductModelData`> 資料列元素的 ProductID 屬性來傳回值。</span><span class="sxs-lookup"><span data-stu-id="c85d8-110">Instead, the values are returned as assigned to a ProductIDs attribute of the <`ProductModelData`> row element of the parent SELECT.</span></span> <span data-ttu-id="c85d8-111">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="c85d8-111">This is the result:</span></span>  
  
 `<ProductModelData ProductModelID="7"`  
  
 `ProductModelName="HL Touring Frame"`  
  
 `ProductIDs="885 887 888 889 890 891 892 893" />`  
  
## <a name="see-also"></a><span data-ttu-id="c85d8-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c85d8-112">See Also</span></span>  
 [<span data-ttu-id="c85d8-113">搭配 FOR XML 使用 PATH 模式</span><span class="sxs-lookup"><span data-stu-id="c85d8-113">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
