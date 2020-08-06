---
title: XSL Caching (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- XSL caching [SQLXML]
ms.assetid: 91994142-32f0-4d8d-a8cf-eb0d8b1f1999
author: rothja
ms.author: jroth
ms.openlocfilehash: e41f247c34c1b40bedfdf6924a45afe5f63735b4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700915"
---
# <a name="xsl-caching-sqlxml-40"></a><span data-ttu-id="11ab4-102">XSL 快取 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="11ab4-102">XSL Caching (SQLXML 4.0)</span></span>
  <span data-ttu-id="11ab4-103">快取 XSL 樣式表可以改善效能。</span><span class="sxs-lookup"><span data-stu-id="11ab4-103">Caching XSL style sheets improves performance.</span></span> <span data-ttu-id="11ab4-104">第一次執行之後，如果 XSL 快取設定為 ON，XSL 樣式表仍保持在記憶體中；這樣可以改善後續處理的效能。</span><span class="sxs-lookup"><span data-stu-id="11ab4-104">Upon its first execution, an XSL style sheet remains in memory if XSL caching is set to ON; this improves performance for subsequent processing.</span></span> <span data-ttu-id="11ab4-105">預設值是 ON。</span><span class="sxs-lookup"><span data-stu-id="11ab4-105">The default setting is ON.</span></span>  
  
 <span data-ttu-id="11ab4-106">您可以在登錄中加入下列機碼來設定 XSL 快取大小：</span><span class="sxs-lookup"><span data-stu-id="11ab4-106">You can set the XSL cache size by adding the following key in the registry:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\XSLCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 <span data-ttu-id="11ab4-107">XSL 快取大小應該根據可用的記憶體以及您要使用的 XSL 樣式表數目來設定。</span><span class="sxs-lookup"><span data-stu-id="11ab4-107">The XSL cache size should be set on the basis of the available memory and the number of XSL style sheets you are using.</span></span> <span data-ttu-id="11ab4-108">**XSLCacheSize**大小的預設值為31。</span><span class="sxs-lookup"><span data-stu-id="11ab4-108">The default of **XSLCacheSize** size is 31.</span></span> <span data-ttu-id="11ab4-109">如果 XSL 存取速度似乎緩慢，您可以增加快取大小，或者如果記憶體不足，則減少快取大小。</span><span class="sxs-lookup"><span data-stu-id="11ab4-109">You can increase the cache size if XSL access seems slow, or decrease the cache size if memory is low.</span></span>  
  
 <span data-ttu-id="11ab4-110">為獲得較佳的效能，建議您將**XSLCacheSize**設定得高於通常使用的 XSL 樣式表單數目。</span><span class="sxs-lookup"><span data-stu-id="11ab4-110">For better performance, it is recommended that you set **XSLCacheSize** higher than the number of XSL style sheets you usually use.</span></span> <span data-ttu-id="11ab4-111">如果**XSLCacheSize**小於您擁有的 xsl 樣式表單數目，效能會隨著 xsl 樣式表單數目的增加而降低。</span><span class="sxs-lookup"><span data-stu-id="11ab4-111">If **XSLCacheSize** is less than the number of XSL style sheets you have, the performance degrades as the number of XSL style sheets increases.</span></span> <span data-ttu-id="11ab4-112">**XSLCacheSize**可以設定為最大值128。</span><span class="sxs-lookup"><span data-stu-id="11ab4-112">The **XSLCacheSize** can be set to a maximum of 128.</span></span>  
  
 <span data-ttu-id="11ab4-113">每次使用快取的 XSL 樣式表時，就會檢查 XSL 檔的修改時間以判斷該 XSL 檔是否需要重新整理。</span><span class="sxs-lookup"><span data-stu-id="11ab4-113">Every time the cached XSL style sheet is used, the modification time of the XSL file is checked to determine whether it needs to be refreshed.</span></span> <span data-ttu-id="11ab4-114">這是因為磁碟副本比快取副本新的緣故。</span><span class="sxs-lookup"><span data-stu-id="11ab4-114">This is because the disk copy is newer than the cache copy.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11ab4-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11ab4-115">See Also</span></span>  
 <span data-ttu-id="11ab4-116">[&#40;SQLXML 4.0&#41;的範本快取](template-caching-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="11ab4-116">[Template Caching &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="11ab4-117">架構快取 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="11ab4-117">Schema Caching &#40;SQLXML 4.0&#41;</span></span>](schema-caching-sqlxml-4-0.md)  
  
  
