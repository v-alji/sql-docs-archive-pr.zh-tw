---
title: PATH 模式中的命名空間支援 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: conceptual
helpviewer_keywords:
- PATH FOR XML mode, namespace support
- namespaces [XML in SQL Server]
ms.assetid: 5f128ea2-0ceb-4b23-bce7-c8b3fd615466
author: rothja
ms.author: jroth
ms.openlocfilehash: abd6cd1f5590bffcd841b07897c9685faed4726f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687554"
---
# <a name="namespace-support-in-path-mode"></a><span data-ttu-id="04a70-102">PATH 模式中的命名空間支援</span><span class="sxs-lookup"><span data-stu-id="04a70-102">Namespace Support in PATH Mode</span></span>
  <span data-ttu-id="04a70-103">PATH 模式中的命名空間支援是使用 WITH NAMESPACES 來提供。</span><span class="sxs-lookup"><span data-stu-id="04a70-103">Namespace support in the PATH mode is provided by using WITH NAMESPACES.</span></span> <span data-ttu-id="04a70-104">例如，下列查詢示範 WITH NAMESPACES 語法以宣告命名空間 ("a:")，它可用於後續的 SELECT 陳述式中：</span><span class="sxs-lookup"><span data-stu-id="04a70-104">For example, the following query demonstrates the WITH NAMESPACES syntax to declare a namespace ("a:") that can then be used in the subsequent SELECT statement:</span></span>  
  
```  
WITH XMLNAMESPACES('a' as a)  
SELECT 1 as 'a:b'  
FOR XML PATH  
```  
  
## <a name="examples"></a><span data-ttu-id="04a70-105">範例</span><span class="sxs-lookup"><span data-stu-id="04a70-105">Examples</span></span>  
 <span data-ttu-id="04a70-106">以下範例說明使用 PATH 模式從 SELECT 查詢產生 XML。</span><span class="sxs-lookup"><span data-stu-id="04a70-106">These samples illustrate the use of PATH mode in generating XML from a SELECT query.</span></span> <span data-ttu-id="04a70-107">這些查詢中有許多是針對自行車製造指示的 XML 文件所指定，這些文件是儲存在 ProductModel 資料表的 Instructions 資料行中。</span><span class="sxs-lookup"><span data-stu-id="04a70-107">Many of these queries are specified against the bicycle manufacturing instructions XML documents that are stored in the Instructions column of the ProductModel table.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04a70-108">另請參閱</span><span class="sxs-lookup"><span data-stu-id="04a70-108">See Also</span></span>  
 [<span data-ttu-id="04a70-109">搭配 FOR XML 使用 PATH 模式</span><span class="sxs-lookup"><span data-stu-id="04a70-109">Use PATH Mode with FOR XML</span></span>](use-path-mode-with-for-xml.md)  
  
  
