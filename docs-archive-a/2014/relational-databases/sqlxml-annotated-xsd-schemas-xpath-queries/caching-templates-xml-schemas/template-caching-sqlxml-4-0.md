---
title: " (SQLXML 4.0) 的範本快取 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- templates [SQLXML], caching
ms.assetid: 73e151c6-b24e-4422-a116-51e0846bc6f5
author: rothja
ms.author: jroth
ms.openlocfilehash: b2ea8a539086ada1b15abbb9cff4f838af45818c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595881"
---
# <a name="template-caching-sqlxml-40"></a><span data-ttu-id="796ae-102">範本快取 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="796ae-102">Template Caching (SQLXML 4.0)</span></span>
  <span data-ttu-id="796ae-103">範本快取會大幅改善效能。</span><span class="sxs-lookup"><span data-stu-id="796ae-103">Template caching significantly improves performance.</span></span> <span data-ttu-id="796ae-104">如果設定範本快取，範本在第一次執行後仍會保留在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="796ae-104">If template caching is set, the template remains in memory upon its first execution.</span></span> <span data-ttu-id="796ae-105">這樣可以增進後續執行範本的效能。</span><span class="sxs-lookup"><span data-stu-id="796ae-105">This improves the performance for the subsequent execution of the template.</span></span>  
  
 <span data-ttu-id="796ae-106">您可以在登錄中加入下列機碼來設定範本快取大小：</span><span class="sxs-lookup"><span data-stu-id="796ae-106">You can set the template cache size by adding the following key in the registry:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML4\TemplateCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 <span data-ttu-id="796ae-107">範本大小應該根據可用的記憶體以及您要使用的範本數目來設定。</span><span class="sxs-lookup"><span data-stu-id="796ae-107">The template size should be set on the basis of the available memory and the number of templates you are using.</span></span> <span data-ttu-id="796ae-108">**TemplateCacheSize**大小的預設值為31。</span><span class="sxs-lookup"><span data-stu-id="796ae-108">The default of **TemplateCacheSize** size is 31.</span></span> <span data-ttu-id="796ae-109">如果範本存取速度似乎緩慢，您可以增加快取大小，或者如果記憶體不足，則減少快取大小。</span><span class="sxs-lookup"><span data-stu-id="796ae-109">You can increase the cache size if template access seems slow, or decrease the cache size if memory is low.</span></span>  
  
 <span data-ttu-id="796ae-110">為獲得較佳的效能，建議您將**TemplateCacheSize**設定為高於您通常使用的範本數目。</span><span class="sxs-lookup"><span data-stu-id="796ae-110">For better performance, it is recommended that you set **TemplateCacheSize** higher than the number of templates you usually use.</span></span> <span data-ttu-id="796ae-111">如果**TemlateCacheSize**小於您擁有的範本數目，效能會隨著範本數目的增加而降低。</span><span class="sxs-lookup"><span data-stu-id="796ae-111">If **TemlateCacheSize** is less than the number of templates you have, performance degrades as the number of templates increase.</span></span> <span data-ttu-id="796ae-112">**TemplateCacheSize**可以設定為最大值128。</span><span class="sxs-lookup"><span data-stu-id="796ae-112">The **TemplateCacheSize** can be set to a maximum of 128.</span></span>  
  
 <span data-ttu-id="796ae-113">每次使用快取的範本時，就會檢查範本檔的修改時間以查看該範本檔是否需要重新整理。</span><span class="sxs-lookup"><span data-stu-id="796ae-113">Every time a cached template is used, the modification time of the template file is checked to see whether it needs to be refreshed.</span></span> <span data-ttu-id="796ae-114">這是因為磁碟副本比快取副本新的緣故。</span><span class="sxs-lookup"><span data-stu-id="796ae-114">This is because the disk copy is newer than the cache copy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="796ae-115">系統不會快取範本參數和命令屬性。</span><span class="sxs-lookup"><span data-stu-id="796ae-115">Template parameters and command properties are not cached.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="796ae-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="796ae-116">See Also</span></span>  
 <span data-ttu-id="796ae-117">[架構快取 &#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="796ae-117">[Schema Caching &#40;SQLXML 4.0&#41;](schema-caching-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="796ae-118">XSL Caching &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="796ae-118">XSL Caching &#40;SQLXML 4.0&#41;</span></span>](xsl-caching-sqlxml-4-0.md)  
  
  
