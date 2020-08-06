---
title: 範例：擷取二進位資料 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- RAW mode, retrieving binary data example
ms.assetid: 5cea5d49-58ac-403a-a933-c4fd91de400b
author: rothja
ms.author: jroth
ms.openlocfilehash: 516c7d91d0a6ebac7366b4bb3cbafe5d05aaa232
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606657"
---
# <a name="example-retrieving-binary-data"></a><span data-ttu-id="45ff5-102">範例：擷取二進位資料</span><span class="sxs-lookup"><span data-stu-id="45ff5-102">Example: Retrieving Binary Data</span></span>
  <span data-ttu-id="45ff5-103">下列查詢會傳回儲存在 `varbinary(max)` 類型資料行中的產品相片。</span><span class="sxs-lookup"><span data-stu-id="45ff5-103">The following query returns the product photo stored in a `varbinary(max)` type column.</span></span> <span data-ttu-id="45ff5-104">在查詢中指定 `BINARY BASE64` 選項，以便將二進位資料透過 Base64 編碼格式傳回。</span><span class="sxs-lookup"><span data-stu-id="45ff5-104">The `BINARY BASE64` option is specified in the query to return the binary data in base64-encoded format.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45ff5-105">範例</span><span class="sxs-lookup"><span data-stu-id="45ff5-105">Example</span></span>  
  
```  
USE AdventureWorks2012;  
GO  
SELECT ProductPhotoID, ThumbNailPhoto  
FROM Production.ProductPhoto  
WHERE ProductPhotoID=1  
FOR XML RAW, BINARY BASE64 ;  
GO  
```  
  
 <span data-ttu-id="45ff5-106">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="45ff5-106">This is the result:</span></span>  
  
```  
<row ProductModelID="1" ThumbNailPhoto="base64 encoded binary data"/>  
```  
  
## <a name="see-also"></a><span data-ttu-id="45ff5-107">另請參閱</span><span class="sxs-lookup"><span data-stu-id="45ff5-107">See Also</span></span>  
 [<span data-ttu-id="45ff5-108">搭配 FOR XML 使用 RAW 模式</span><span class="sxs-lookup"><span data-stu-id="45ff5-108">Use RAW Mode with FOR XML</span></span>](use-raw-mode-with-for-xml.md)  
  
  
