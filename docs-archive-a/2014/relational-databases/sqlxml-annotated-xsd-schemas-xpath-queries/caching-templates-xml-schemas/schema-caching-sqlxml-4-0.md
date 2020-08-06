---
title: 架構快取 (SQLXML 4.0) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- registry keys [SQLXML]
- cache [SQLXML]
- schemas [SQLXML]
ms.assetid: 7e5fda21-b435-41fd-b637-8b616560a93f
author: rothja
ms.author: jroth
ms.openlocfilehash: 4e36711955fa28bafd3b0996b1a02f6cd71f3c4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599421"
---
# <a name="schema-caching-sqlxml-40"></a><span data-ttu-id="69821-102">結構描述快取 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="69821-102">Schema Caching (SQLXML 4.0)</span></span>
  <span data-ttu-id="69821-103">透過 XML for Microsoft SQL Server 2000 Web Release 1、Microsoft SQLXML 2.0 和 SQLXML 3.0 的並行安裝，您可以使用下列登錄機碼，明確地控制所有版本中的結構描述快取：</span><span class="sxs-lookup"><span data-stu-id="69821-103">With a side-by-side installation of XML for Microsoft SQL Server 2000 Web Release 1, Microsoft SQLXML 2.0, and SQLXML 3.0, you can explicitly control the schema caching in all versions by using the following registry keys:</span></span>  
  
 <span data-ttu-id="69821-104">Web Release 1：</span><span class="sxs-lookup"><span data-stu-id="69821-104">Web Release 1:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXMLX\SchemaCacheSize  
```  
  
 <span data-ttu-id="69821-105">SQLXML 2.0：</span><span class="sxs-lookup"><span data-stu-id="69821-105">SQLXML 2.0:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML2\SchemaCacheSize  
```  
  
 <span data-ttu-id="69821-106">SQLXML 3.0：</span><span class="sxs-lookup"><span data-stu-id="69821-106">SQLXML 3.0:</span></span>  
  
```  
HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\MSSQLServer\Client\SQLXML3\SchemaCacheSize  
```  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../../includes/ssnoteregistry-md.md)]  
  
 <span data-ttu-id="69821-107">如需並存安裝的詳細資訊，請參閱[SQLXML 4.0 SP1 的新功能](../../sqlxml/what-s-new-in-sqlxml-4-0-sp1.md)。</span><span class="sxs-lookup"><span data-stu-id="69821-107">For more information about side-by-side installation, see [What's New in SQLXML 4.0 SP1](../../sqlxml/what-s-new-in-sqlxml-4-0-sp1.md).</span></span>  
  
 <span data-ttu-id="69821-108">結構描述快取能大幅提升 XPath 查詢的效能。</span><span class="sxs-lookup"><span data-stu-id="69821-108">Schema caching significantly improves the performance of an XPath query.</span></span> <span data-ttu-id="69821-109">當 XPath 查詢針對對應結構描述執行時，結構描述會儲存在記憶體中，而且會在記憶體中建立所需的資料結構。</span><span class="sxs-lookup"><span data-stu-id="69821-109">When an XPath query is executed against a mapping schema, the schema is stored in memory, and the necessary data structures are built in memory.</span></span> <span data-ttu-id="69821-110">如果設定結構描述快取，結構描述仍會保留在記憶體中，藉以提升後續 XPath 查詢的效能。</span><span class="sxs-lookup"><span data-stu-id="69821-110">If schema caching is set, the schema remains in memory, thereby improving performance for subsequent XPath queries.</span></span>  
  
 <span data-ttu-id="69821-111">您可以在登錄中加入上述機碼來設定結構描述快取大小</span><span class="sxs-lookup"><span data-stu-id="69821-111">You can set the schema cache size by adding the above key in the registry</span></span>  
  
 <span data-ttu-id="69821-112">結構描述大小應該根據可用的記憶體以及您要使用的結構描述數目來設定。</span><span class="sxs-lookup"><span data-stu-id="69821-112">The schema size is set based on the available memory and the number of schemas you are using.</span></span> <span data-ttu-id="69821-113">預設的**SchemaCacheSize**大小為31。</span><span class="sxs-lookup"><span data-stu-id="69821-113">The default **SchemaCacheSize** size is 31.</span></span> <span data-ttu-id="69821-114">如果您將**SchemaCacheSize**設定為較高，則會使用較多的記憶體。</span><span class="sxs-lookup"><span data-stu-id="69821-114">If you set **SchemaCacheSize** higher, more memory is used.</span></span> <span data-ttu-id="69821-115">因此，如果結構描述存取速度似乎緩慢，您可以增加快取大小，或者如果記憶體不足，則減少快取大小。</span><span class="sxs-lookup"><span data-stu-id="69821-115">Therefore, you can increase the cache size if schema access seems slow, or decrease the cache size if memory is low.</span></span>  
  
 <span data-ttu-id="69821-116">基於效能考慮，建議您將**SchemaCacheSize**設定為高於您通常使用的對應架構數目。</span><span class="sxs-lookup"><span data-stu-id="69821-116">For performance reasons, it is recommended that you set **SchemaCacheSize** higher than the number of mapping schemas you usually use.</span></span> <span data-ttu-id="69821-117">隨著架構數目的增加，如果**SchemaCacheSize**小於您擁有的架構數目，效能就會降低。</span><span class="sxs-lookup"><span data-stu-id="69821-117">As the number of schemas increase, if **SchemaCacheSize** is less than the number of schemas you have, the performance degrades.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="69821-118">在開發期間，建議您不要快取結構描述，因為您對結構描述所做的變更，約有兩分鐘不會反映在快取中。</span><span class="sxs-lookup"><span data-stu-id="69821-118">During development, it is recommended that you do not cache the schemas, because the changes to the schemas are not reflected in the cache for about two minutes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69821-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="69821-119">See Also</span></span>  
 <span data-ttu-id="69821-120">[&#40;SQLXML 4.0&#41;的範本快取](template-caching-sqlxml-4-0.md) </span><span class="sxs-lookup"><span data-stu-id="69821-120">[Template Caching &#40;SQLXML 4.0&#41;](template-caching-sqlxml-4-0.md) </span></span>  
 [<span data-ttu-id="69821-121">XSL Caching &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="69821-121">XSL Caching &#40;SQLXML 4.0&#41;</span></span>](xsl-caching-sqlxml-4-0.md)  
  
  
