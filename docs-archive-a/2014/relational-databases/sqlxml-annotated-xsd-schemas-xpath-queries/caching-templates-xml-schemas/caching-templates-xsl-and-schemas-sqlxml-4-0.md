---
title: " (SQLXML 4.0) 快取範本、XSL 和架構 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: xml
ms.topic: reference
helpviewer_keywords:
- SQLXML, caching
- cache [SQLXML]
- memory [SQLXML]
ms.assetid: 80b4fa79-243f-442c-9f22-74ad66186501
author: rothja
ms.author: jroth
ms.openlocfilehash: 4df25909cf156957908abf0691964fd66a76343a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597039"
---
# <a name="caching-templates-xsl-and-schemas-sqlxml-40"></a><span data-ttu-id="a1816-102">快取範本、XSL 和結構描述 (SQLXML 4.0)</span><span class="sxs-lookup"><span data-stu-id="a1816-102">Caching Templates, XSL, and Schemas (SQLXML 4.0)</span></span>
  <span data-ttu-id="a1816-103">為增進效能，[!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 支援快取範本、XSL 和結構描述。</span><span class="sxs-lookup"><span data-stu-id="a1816-103">To improve performance, [!INCLUDE[msCoName](../../../includes/msconame-md.md)] SQLXML 4.0 supports caching templates, XSL, and schemas.</span></span>  
  
 <span data-ttu-id="a1816-104">系統會快取所有結構描述、範本和 XSL 檔案 (除了來自 http:// 或 ftp:// 位置的檔案之外)。</span><span class="sxs-lookup"><span data-stu-id="a1816-104">All schemas, templates, and XSL files (except the files from an http:// or ftp:// location) are cached.</span></span> <span data-ttu-id="a1816-105">當程序正在執行時，快取的檔案仍然在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="a1816-105">The cached files remain in memory while the process is running.</span></span> <span data-ttu-id="a1816-106">當程序結束時，所有快取都會消失。</span><span class="sxs-lookup"><span data-stu-id="a1816-106">As the process exits, all the cache is lost.</span></span> <span data-ttu-id="a1816-107">因此，如果每個查詢執行一個程序，快取的效益可能就不明顯。</span><span class="sxs-lookup"><span data-stu-id="a1816-107">Therefore, if you run one process per query, the caching benefit may not be noticeable.</span></span>  
  
 <span data-ttu-id="a1816-108">本節中的主題提供有關快取的詳細資訊。</span><span class="sxs-lookup"><span data-stu-id="a1816-108">The topics in this section provide more information about caching.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a1816-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="a1816-109">In This Section</span></span>  
 [<span data-ttu-id="a1816-110">&#40;SQLXML 4.0&#41;的範本快取</span><span class="sxs-lookup"><span data-stu-id="a1816-110">Template Caching &#40;SQLXML 4.0&#41;</span></span>](template-caching-sqlxml-4-0.md)  
 <span data-ttu-id="a1816-111">描述並提供範本快取的登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="a1816-111">Describes and provides a registry key for template caching.</span></span>  
  
 [<span data-ttu-id="a1816-112">XSL Caching &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="a1816-112">XSL Caching &#40;SQLXML 4.0&#41;</span></span>](xsl-caching-sqlxml-4-0.md)  
 <span data-ttu-id="a1816-113">描述並提供 XSL 快取的登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="a1816-113">Describes and provides a registry key for XSL caching.</span></span>  
  
 [<span data-ttu-id="a1816-114">架構快取 &#40;SQLXML 4.0&#41;</span><span class="sxs-lookup"><span data-stu-id="a1816-114">Schema Caching &#40;SQLXML 4.0&#41;</span></span>](schema-caching-sqlxml-4-0.md)  
 <span data-ttu-id="a1816-115">討論與結構描述快取相關的 SQLXML 並行安裝問題，並提供結構描述快取的登錄機碼。</span><span class="sxs-lookup"><span data-stu-id="a1816-115">Discusses SQLXML side-by-side installation issues related to schema caching, and provides registry keys for schema caching.</span></span>  
  
  
