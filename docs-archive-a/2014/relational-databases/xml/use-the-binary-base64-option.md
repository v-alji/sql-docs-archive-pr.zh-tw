---
title: 使用 BINARY BASE64 選項 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- AUTO FOR XML mode, BINARY BASE64 option
ms.assetid: 86a7bb85-7f83-412a-b775-d2c379702fe9
author: rothja
ms.author: jroth
ms.openlocfilehash: 090d6a91ee56707a4eb1d545aa5a05bc25999fab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706266"
---
# <a name="use-the-binary-base64-option"></a><span data-ttu-id="e757c-102">使用 BINARY BASE64 選項</span><span class="sxs-lookup"><span data-stu-id="e757c-102">Use the BINARY BASE64 Option</span></span>
  <span data-ttu-id="e757c-103">若查詢中指定 BINARY BASE64 選項，就會以 Base64 編碼格式傳回二進位資料。</span><span class="sxs-lookup"><span data-stu-id="e757c-103">If the BINARY BASE64 option is specified in the query, the binary data is returned in base64 encoding format.</span></span> <span data-ttu-id="e757c-104">依預設，若沒有指定 BINARY BASE64 選項，則 AUTO 模式可支援 URL 編碼的二進位資料。</span><span class="sxs-lookup"><span data-stu-id="e757c-104">By default, if the BINARY BASE64 option is not specified, AUTO mode supports URL encoding of binary data.</span></span> <span data-ttu-id="e757c-105">也就是說，不是傳回二進位資料，而是傳回一個參考，以指向查詢執行所在之資料庫虛擬根目錄的相對 URL。</span><span class="sxs-lookup"><span data-stu-id="e757c-105">That is, instead of binary data, a reference to a relative URL to the virtual root of the database where the query was executed is returned.</span></span> <span data-ttu-id="e757c-106">此參考可用來存取後續作業中的實際二進位資料 (使用 SQLXML ISAPI dbobject 查詢)。</span><span class="sxs-lookup"><span data-stu-id="e757c-106">This reference can be used to access the actual binary data in subsequent operations by using the SQLXML ISAPI dbobject query.</span></span> <span data-ttu-id="e757c-107">此查詢必須提供足夠的資訊 (例如：主索引鍵資料行)，以便識別影像。</span><span class="sxs-lookup"><span data-stu-id="e757c-107">The query must provide enough information, such as primary key columns, to identify the image.</span></span>  
  
 <span data-ttu-id="e757c-108">在指定查詢時，若將別名用於檢視的二進位資料行，就會在 URL 編碼的二進位資料中傳回該別名。</span><span class="sxs-lookup"><span data-stu-id="e757c-108">In specifying a query, if an alias is used for the binary column of the view, the alias is returned in the URL encoding of the binary data.</span></span> <span data-ttu-id="e757c-109">在後續動作中該別名不具任何意義，且無法使用 URL 編碼來擷取影像。</span><span class="sxs-lookup"><span data-stu-id="e757c-109">In subsequent operations, the alias is meaningless, and the URL encoding cannot be used to retrieve the image.</span></span> <span data-ttu-id="e757c-110">所以在利用 FOR XML AUTO 模式查詢檢視時，請勿使用別名。</span><span class="sxs-lookup"><span data-stu-id="e757c-110">Therefore, do not use aliases when querying a view using FOR XML AUTO mode.</span></span>  
  
 <span data-ttu-id="e757c-111">例如在 SELECT 查詢中，將任何資料行轉換為二進位大型物件 (BLOB)，會使其成為遺失關聯資料表名稱與資料行名稱的暫存實體。</span><span class="sxs-lookup"><span data-stu-id="e757c-111">For example, in a SELECT query, casting any column to a binary large object (BLOB) makes it a temporary entity in that it loses its associated table name and column name.</span></span> <span data-ttu-id="e757c-112">而這會使得 AUTO 模式查詢產生錯誤，因為查詢不知道要將此值放入 XML 階層中的哪個位置。</span><span class="sxs-lookup"><span data-stu-id="e757c-112">This causes AUTO mode queries to generate an error, because it does not know where to put this value in the XML hierarchy.</span></span> <span data-ttu-id="e757c-113">例如：</span><span class="sxs-lookup"><span data-stu-id="e757c-113">For example:</span></span>  
  
```  
CREATE TABLE MyTable (Col1 int PRIMARY KEY, Col2 binary)  
INSERT INTO MyTable VALUES (1, 0x7);  
```  
  
 <span data-ttu-id="e757c-114">由於轉換為二進位大型物件 (BLOB)，因此查詢產生錯誤：</span><span class="sxs-lookup"><span data-stu-id="e757c-114">This query produces an error, because of the casting to a binary large object (BLOB):</span></span>  
  
```  
SELECT Col1,  
CAST(Col2 as image) as Col2  
FROM MyTable  
FOR XML AUTO;  
```  
  
 <span data-ttu-id="e757c-115">解決方法是將 BINARY BASE64 選項加入 FOR XML 子句中。</span><span class="sxs-lookup"><span data-stu-id="e757c-115">The solution is to add the BINARY BASE64 option to the FOR XML clause.</span></span> <span data-ttu-id="e757c-116">若將轉換移除，則查詢會產生預期中的結果：</span><span class="sxs-lookup"><span data-stu-id="e757c-116">If you remove the casting, the query produces the results as expected:</span></span>  
  
```  
SELECT Col1,  
CAST(Col2 as image) as Col2  
FROM MyTable  
FOR XML AUTO, BINARY BASE64;  
```  
  
 <span data-ttu-id="e757c-117">以下是結果：</span><span class="sxs-lookup"><span data-stu-id="e757c-117">This is the result:</span></span>  
  
```  
<MyTable Col1="1" Col2="Bw==" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="e757c-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e757c-118">See Also</span></span>  
 [<span data-ttu-id="e757c-119">搭配 FOR XML 使用 AUTO 模式</span><span class="sxs-lookup"><span data-stu-id="e757c-119">Use AUTO Mode with FOR XML</span></span>](use-auto-mode-with-for-xml.md)  
  
  
