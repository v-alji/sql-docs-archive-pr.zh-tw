---
title: 資料庫 (DTA) 的 Name 元素 |Microsoft Docs
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
ms.assetid: e871c4fa-3b57-46cf-b4f8-e3be86f92dc4
author: stevestein
ms.author: sstein
ms.openlocfilehash: c692e31b9175bf05dcfb0504ea79e98cbb82f36b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686615"
---
# <a name="name-element-for-database-dta"></a><span data-ttu-id="b021b-102">資料庫的 Name 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="b021b-102">Name Element for Database (DTA)</span></span>
  <span data-ttu-id="b021b-103">指定您要微調之資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="b021b-103">Specifies the name of a database that you want to tune.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b021b-104">語法</span><span class="sxs-lookup"><span data-stu-id="b021b-104">Syntax</span></span>  
  
```  
  
<Server>  
    <Database>  
        <Name>...</Name>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="b021b-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="b021b-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="b021b-106">特性</span><span class="sxs-lookup"><span data-stu-id="b021b-106">Characteristic</span></span>|<span data-ttu-id="b021b-107">描述</span><span class="sxs-lookup"><span data-stu-id="b021b-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="b021b-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="b021b-108">**Data type and length**</span></span>|<span data-ttu-id="b021b-109">`string`，沒有長度限制。</span><span class="sxs-lookup"><span data-stu-id="b021b-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="b021b-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="b021b-110">**Default value**</span></span>|<span data-ttu-id="b021b-111">無。</span><span class="sxs-lookup"><span data-stu-id="b021b-111">None.</span></span>|  
|<span data-ttu-id="b021b-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="b021b-112">**Occurrence**</span></span>|<span data-ttu-id="b021b-113">(必要) 每個 `Database` 元素出現一次。</span><span class="sxs-lookup"><span data-stu-id="b021b-113">Required once per `Database` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="b021b-114">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="b021b-114">Element Relationships</span></span>  
  
|<span data-ttu-id="b021b-115">關聯性</span><span class="sxs-lookup"><span data-stu-id="b021b-115">Relationship</span></span>|<span data-ttu-id="b021b-116">元素</span><span class="sxs-lookup"><span data-stu-id="b021b-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="b021b-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="b021b-117">**Parent element**</span></span>|[<span data-ttu-id="b021b-118">伺服器的 Database 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="b021b-118">Database Element for Server &#40;DTA&#41;</span></span>](database-element-for-server-dta.md)|  
|<span data-ttu-id="b021b-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="b021b-119">**Child elements**</span></span>|<span data-ttu-id="b021b-120">無。</span><span class="sxs-lookup"><span data-stu-id="b021b-120">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b021b-121">範例</span><span class="sxs-lookup"><span data-stu-id="b021b-121">Example</span></span>  
 <span data-ttu-id="b021b-122">如需此元素的使用範例，請參閱 [Server 元素 &#40;DTA&#41;](server-element-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="b021b-122">For a usage example of this element, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b021b-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b021b-123">See Also</span></span>  
 [<span data-ttu-id="b021b-124">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="b021b-124">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
