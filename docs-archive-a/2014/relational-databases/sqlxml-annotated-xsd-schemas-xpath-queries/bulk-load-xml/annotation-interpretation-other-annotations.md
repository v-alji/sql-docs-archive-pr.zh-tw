---
title: " (SQLXML 4.0) 的其他批註 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- url-encode annotation
- sql:key-fields
- use-cdata annotation
- sql:is-mapping-schema
- sql:url-encode
- sql:id-prefix
- sql:use-cdata
- key-fields annotation
- id-prefix annotation [SQLXML]
- is-mapping-schema annotation
ms.assetid: f7b4d37b-d6d3-4ac3-b2fd-a0b534a924e4
author: rothja
ms.author: jroth
ms.openlocfilehash: b654568c93df0a0c3e08cf6eaa615b7026a9c18a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595889"
---
# <a name="other-annotations-sqlxml-40"></a><span data-ttu-id="d1ae7-102">其他註解 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="d1ae7-102">Other Annotations (SQLXML 4.0)</span></span>
  <span data-ttu-id="d1ae7-103">除了本章節先前的主題所討論的註解以外，XML 大量載入還會解譯這些其他註解，如下所示：</span><span class="sxs-lookup"><span data-stu-id="d1ae7-103">In addition to the annotations discussed in the previous topics in this section, XML Bulk Load interprets these other annotations, as follows:</span></span>  
  
 `sql:id-prefix`  
 <span data-ttu-id="d1ae7-104">如果結構描述指定 XML 資料的前置詞，XML 大量載入會先移除這些前置詞，然後再將資料傳送給 Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d1ae7-104">If the schema specifies prefixes to the XML data, XML Bulk Load removes the prefixes before sending the data to Microsoft [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 `sql:use-cdata`  
 <span data-ttu-id="d1ae7-105">XML 大量載入會讀取 CDATA 區段中所儲存的文字，然後將其傳送給 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="d1ae7-105">XML Bulk Load reads the text that is stored in the CDATA sections and sends it to [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].</span></span>  
  
 `sql:url-encode`  
 <span data-ttu-id="d1ae7-106">XML 大量載入不支援此註釋。</span><span class="sxs-lookup"><span data-stu-id="d1ae7-106">XML Bulk Load does not support this annotation.</span></span> <span data-ttu-id="d1ae7-107">例如，您不能在 XML 資料輸入中指定 URL，然後預期 XML 大量載入會從該位置讀取資料，將它儲存在資料庫中。</span><span class="sxs-lookup"><span data-stu-id="d1ae7-107">For example, you cannot specify a URL in the XML data input and expect XML Bulk Load to read data from that location to store it in the database.</span></span>  
  
 `sql:is-mapping-schema`  
 <span data-ttu-id="d1ae7-108">XML 大量載入不支援此註解，也不支援 `sql:id`。</span><span class="sxs-lookup"><span data-stu-id="d1ae7-108">XML Bulk Load does not support this annotation, nor does it support `sql:id`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d1ae7-109">XML 大量載入不支援內嵌對應結構描述。</span><span class="sxs-lookup"><span data-stu-id="d1ae7-109">XML Bulk Load does not support inline mapping schemas.</span></span>  
  
 `sql:key-fields`  
 <span data-ttu-id="d1ae7-110">XML 大量載入一定會忽略此註解。</span><span class="sxs-lookup"><span data-stu-id="d1ae7-110">XML Bulk Load always ignores this annotation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1ae7-111">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d1ae7-111">See Also</span></span>  
 [<span data-ttu-id="d1ae7-112">&#40;SQLXML 4.0&#41;的注釋轉譯</span><span class="sxs-lookup"><span data-stu-id="d1ae7-112">Annotation Interpretation &#40;SQLXML 4.0&#41;</span></span>](annotation-interpretation-sqlxml-4-0.md)  
  
  
