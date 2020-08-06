---
title: 資料庫 (DTA) 的架構元素 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Schema element
ms.assetid: d932e59c-953f-4ab4-934d-b6baf344835c
author: stevestein
ms.author: sstein
ms.openlocfilehash: 7653177878f3a832abd2d1ca266bc5feb17b9a29
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592414"
---
# <a name="schema-element-for-database-dta"></a><span data-ttu-id="4e79f-102">資料庫的 Schema 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="4e79f-102">Schema Element for Database (DTA)</span></span>
  <span data-ttu-id="4e79f-103">指定您要微調之資料庫的結構描述。</span><span class="sxs-lookup"><span data-stu-id="4e79f-103">Specifies the schema of the database that you want to tune.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e79f-104">語法</span><span class="sxs-lookup"><span data-stu-id="4e79f-104">Syntax</span></span>  
  
```  
  
<Database>  
...code removed here...  
    <Schema>...</Schema>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="4e79f-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="4e79f-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="4e79f-106">特性</span><span class="sxs-lookup"><span data-stu-id="4e79f-106">Characteristic</span></span>|<span data-ttu-id="4e79f-107">描述</span><span class="sxs-lookup"><span data-stu-id="4e79f-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="4e79f-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="4e79f-108">**Data type and length**</span></span>|<span data-ttu-id="4e79f-109">無。</span><span class="sxs-lookup"><span data-stu-id="4e79f-109">None.</span></span>|  
|<span data-ttu-id="4e79f-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="4e79f-110">**Default value**</span></span>|<span data-ttu-id="4e79f-111">無。</span><span class="sxs-lookup"><span data-stu-id="4e79f-111">None.</span></span>|  
|<span data-ttu-id="4e79f-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="4e79f-112">**Occurrence**</span></span>|<span data-ttu-id="4e79f-113">**Server** 元素之下所指定的 **Database** 元素需要使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="4e79f-113">Required once for the **Database** element that is specified under the **Server** element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="4e79f-114">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="4e79f-114">Element Relationships</span></span>  
  
|<span data-ttu-id="4e79f-115">關聯性</span><span class="sxs-lookup"><span data-stu-id="4e79f-115">Relationship</span></span>|<span data-ttu-id="4e79f-116">元素</span><span class="sxs-lookup"><span data-stu-id="4e79f-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="4e79f-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="4e79f-117">**Parent element**</span></span>|[<span data-ttu-id="4e79f-118">伺服器的 Database 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="4e79f-118">Database Element for Server &#40;DTA&#41;</span></span>](database-element-for-server-dta.md)|  
|<span data-ttu-id="4e79f-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="4e79f-119">**Child elements**</span></span>|[<span data-ttu-id="4e79f-120">結構描述的 Name 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="4e79f-120">Name Element for Schema &#40;DTA&#41;</span></span>](name-element-for-schema-dta.md)<br /><br /> [<span data-ttu-id="4e79f-121">結構描述的 Table 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="4e79f-121">Table Element for Schema &#40;DTA&#41;</span></span>](table-element-for-schema-dta.md)|  
  
## <a name="example"></a><span data-ttu-id="4e79f-122">範例</span><span class="sxs-lookup"><span data-stu-id="4e79f-122">Example</span></span>  
 <span data-ttu-id="4e79f-123">如需此元素的使用範例，請參閱 [Server 元素 &#40;DTA&#41;](server-element-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="4e79f-123">For a usage example of this element, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e79f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4e79f-124">See Also</span></span>  
 [<span data-ttu-id="4e79f-125">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="4e79f-125">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
