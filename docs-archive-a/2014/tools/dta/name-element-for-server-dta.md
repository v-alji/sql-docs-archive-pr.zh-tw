---
title: 伺服器 (DTA) 的 Name 元素 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Name element
ms.assetid: 4c94754d-6d62-4357-8ce7-f107ebf90c71
author: stevestein
ms.author: sstein
ms.openlocfilehash: 202258c3c87f8a35d1ee30b19880f5e9423fa394
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598103"
---
# <a name="name-element-for-server-dta"></a><span data-ttu-id="1a0a8-102">伺服器的 Name 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="1a0a8-102">Name Element for Server (DTA)</span></span>
  <span data-ttu-id="1a0a8-103">包含您要微調的資料庫所在的伺服器名稱。</span><span class="sxs-lookup"><span data-stu-id="1a0a8-103">Contains the name of the server where the databases you want to tune reside.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a0a8-104">語法</span><span class="sxs-lookup"><span data-stu-id="1a0a8-104">Syntax</span></span>  
  
```  
  
...code removed here...  
<Server>  
    <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="1a0a8-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="1a0a8-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="1a0a8-106">特性</span><span class="sxs-lookup"><span data-stu-id="1a0a8-106">Characteristic</span></span>|<span data-ttu-id="1a0a8-107">描述</span><span class="sxs-lookup"><span data-stu-id="1a0a8-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="1a0a8-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="1a0a8-108">**Data type and length**</span></span>|<span data-ttu-id="1a0a8-109">`string`，在 1 和 255 個字元之間。</span><span class="sxs-lookup"><span data-stu-id="1a0a8-109">`string`, between 1 and 255 characters.</span></span>|  
|<span data-ttu-id="1a0a8-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="1a0a8-110">**Default value**</span></span>|<span data-ttu-id="1a0a8-111">無。</span><span class="sxs-lookup"><span data-stu-id="1a0a8-111">None.</span></span>|  
|<span data-ttu-id="1a0a8-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="1a0a8-112">**Occurrence**</span></span>|<span data-ttu-id="1a0a8-113">每個 **Server** 元素需要使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="1a0a8-113">Required once per **Server** element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="1a0a8-114">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="1a0a8-114">Element Relationships</span></span>  
  
|<span data-ttu-id="1a0a8-115">關聯性</span><span class="sxs-lookup"><span data-stu-id="1a0a8-115">Relationship</span></span>|<span data-ttu-id="1a0a8-116">元素</span><span class="sxs-lookup"><span data-stu-id="1a0a8-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="1a0a8-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="1a0a8-117">**Parent element**</span></span>|[<span data-ttu-id="1a0a8-118">Server 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="1a0a8-118">Server Element &#40;DTA&#41;</span></span>](server-element-dta.md)|  
|<span data-ttu-id="1a0a8-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="1a0a8-119">**Child elements**</span></span>|<span data-ttu-id="1a0a8-120">無。</span><span class="sxs-lookup"><span data-stu-id="1a0a8-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1a0a8-121">範例</span><span class="sxs-lookup"><span data-stu-id="1a0a8-121">Example</span></span>  
 <span data-ttu-id="1a0a8-122">如需如何使用這個 **Name** 元素的範例，請參閱 [Server 元素 &#40;DTA&#41;](server-element-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="1a0a8-122">For an example of how this **Name** element is used, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a0a8-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1a0a8-123">See Also</span></span>  
 [<span data-ttu-id="1a0a8-124">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="1a0a8-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
