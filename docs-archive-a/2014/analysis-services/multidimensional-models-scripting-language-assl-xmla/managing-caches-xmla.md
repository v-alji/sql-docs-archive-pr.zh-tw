---
title: " (XMLA) 管理快取 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, cache
- XML for Analysis, cache
- clearing cache
- cache [Analysis Services]
ms.assetid: afad5c39-d4c3-4307-b3b9-a06617da0028
author: minewiskan
ms.author: owend
ms.openlocfilehash: cdc5bcd2e0500749edfa298a871b6fec7243ddfb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594775"
---
# <a name="managing-caches-xmla"></a><span data-ttu-id="32d3a-102">管理快取 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="32d3a-102">Managing Caches (XMLA)</span></span>
  <span data-ttu-id="32d3a-103">您可以使用 XML for Analysis (XMLA) 中的[ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla)命令，清除指定維度或資料分割的快取。</span><span class="sxs-lookup"><span data-stu-id="32d3a-103">You can use the [ClearCache](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/clearcache-element-xmla) command in XML for Analysis (XMLA) to clear the cache of a specified dimension or partition.</span></span> <span data-ttu-id="32d3a-104">清除快取 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 會強制重建該物件的快取。</span><span class="sxs-lookup"><span data-stu-id="32d3a-104">Clearing the cache forces [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] to rebuild the cache for that object.</span></span>  
  
## <a name="specifying-objects"></a><span data-ttu-id="32d3a-105">指定物件</span><span class="sxs-lookup"><span data-stu-id="32d3a-105">Specifying Objects</span></span>  
 <span data-ttu-id="32d3a-106">命令的[object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)屬性只能 `ClearCache` 包含下列其中一個物件的物件參考。</span><span class="sxs-lookup"><span data-stu-id="32d3a-106">The [Object](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) property of the `ClearCache` command can contain an object reference only for one of the following objects.</span></span> <span data-ttu-id="32d3a-107">如果物件參考不是用於下列其中一個物件，就會發生錯誤：</span><span class="sxs-lookup"><span data-stu-id="32d3a-107">An error occurs if an object reference is for an object other than one of following objects:</span></span>  
  
 <span data-ttu-id="32d3a-108">資料庫</span><span class="sxs-lookup"><span data-stu-id="32d3a-108">Database</span></span>  
 <span data-ttu-id="32d3a-109">針對資料庫中包含的所有維度與資料分割清除快取。</span><span class="sxs-lookup"><span data-stu-id="32d3a-109">Clears the cache for all dimensions and partitions contained in the database.</span></span>  
  
 <span data-ttu-id="32d3a-110">維度</span><span class="sxs-lookup"><span data-stu-id="32d3a-110">Dimension</span></span>  
 <span data-ttu-id="32d3a-111">清除指定維度的快取。</span><span class="sxs-lookup"><span data-stu-id="32d3a-111">Clears the cache for the specified dimension.</span></span>  
  
 <span data-ttu-id="32d3a-112">Cube</span><span class="sxs-lookup"><span data-stu-id="32d3a-112">Cube</span></span>  
 <span data-ttu-id="32d3a-113">針對 Cube 量值群組中包含的所有資料分割清除快取。</span><span class="sxs-lookup"><span data-stu-id="32d3a-113">Clears the cache for all partitions contained in the measure groups for the cube.</span></span>  
  
 <span data-ttu-id="32d3a-114">量值群組</span><span class="sxs-lookup"><span data-stu-id="32d3a-114">Measure group</span></span>  
 <span data-ttu-id="32d3a-115">針對量值群組中包含的所有資料分割清除快取。</span><span class="sxs-lookup"><span data-stu-id="32d3a-115">Clears the cache for all partitions contained in the measure group.</span></span>  
  
 <span data-ttu-id="32d3a-116">資料分割</span><span class="sxs-lookup"><span data-stu-id="32d3a-116">Partition</span></span>  
 <span data-ttu-id="32d3a-117">清除指定資料分割的快取。</span><span class="sxs-lookup"><span data-stu-id="32d3a-117">Clears the cache for the specified partition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d3a-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="32d3a-118">See Also</span></span>  
 [<span data-ttu-id="32d3a-119">在 Analysis Services 中使用 XMLA 進行開發</span><span class="sxs-lookup"><span data-stu-id="32d3a-119">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
