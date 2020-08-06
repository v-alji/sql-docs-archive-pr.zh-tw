---
title: Configuration (DTA) 的 Server 元素 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Server element
ms.assetid: da9ff870-9cfd-42fe-994b-7b9292681f7d
author: stevestein
ms.author: sstein
ms.openlocfilehash: 88182cdad2e7313f0910a106ee37d727d840bfed
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598092"
---
# <a name="server-element-for-configuration-dta"></a><span data-ttu-id="3c8af-102">組態的 Server 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="3c8af-102">Server Element for Configuration (DTA)</span></span>
  <span data-ttu-id="3c8af-103">包含 Database Engine Tuning Advisor 評估假設性組態 (`Configuration` 元素所指定) 時所在之伺服器的識別資訊。</span><span class="sxs-lookup"><span data-stu-id="3c8af-103">Contains the identifying information for the server where you want Database Engine Tuning Advisor to evaluate the hypothetical configuration (specified by the `Configuration` element).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c8af-104">語法</span><span class="sxs-lookup"><span data-stu-id="3c8af-104">Syntax</span></span>  
  
```  
  
<Configuration>  
    <Server>  
...code removed here...  
    </Server>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="3c8af-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="3c8af-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="3c8af-106">特性</span><span class="sxs-lookup"><span data-stu-id="3c8af-106">Characteristic</span></span>|<span data-ttu-id="3c8af-107">描述</span><span class="sxs-lookup"><span data-stu-id="3c8af-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="3c8af-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="3c8af-108">**Data type and length**</span></span>|<span data-ttu-id="3c8af-109">無。</span><span class="sxs-lookup"><span data-stu-id="3c8af-109">None.</span></span>|  
|<span data-ttu-id="3c8af-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="3c8af-110">**Default value**</span></span>|<span data-ttu-id="3c8af-111">無。</span><span class="sxs-lookup"><span data-stu-id="3c8af-111">None.</span></span>|  
|<span data-ttu-id="3c8af-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="3c8af-112">**Occurrence**</span></span>|<span data-ttu-id="3c8af-113">(必要) 每個 `Configuration` 元素出現一次。</span><span class="sxs-lookup"><span data-stu-id="3c8af-113">Required once per `Configuration` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="3c8af-114">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="3c8af-114">Element Relationships</span></span>  
  
|<span data-ttu-id="3c8af-115">關聯性</span><span class="sxs-lookup"><span data-stu-id="3c8af-115">Relationship</span></span>|<span data-ttu-id="3c8af-116">元素</span><span class="sxs-lookup"><span data-stu-id="3c8af-116">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="3c8af-117">**父元素**</span><span class="sxs-lookup"><span data-stu-id="3c8af-117">**Parent element**</span></span>|[<span data-ttu-id="3c8af-118">Configuration 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="3c8af-118">Configuration Element &#40;DTA&#41;</span></span>](configuration-element-dta.md)|  
|<span data-ttu-id="3c8af-119">**子元素**</span><span class="sxs-lookup"><span data-stu-id="3c8af-119">**Child elements**</span></span>|[<span data-ttu-id="3c8af-120">伺服器的 Name 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="3c8af-120">Name Element for Server &#40;DTA&#41;</span></span>](name-element-for-server-dta.md)<br /><br /> [<span data-ttu-id="3c8af-121">組態的 Database 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="3c8af-121">Database Element for Configuration &#40;DTA&#41;</span></span>](database-element-for-configuration-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="3c8af-122">備註</span><span class="sxs-lookup"><span data-stu-id="3c8af-122">Remarks</span></span>  
 <span data-ttu-id="3c8af-123">您只能 `Server` 為元素指定一個元素 `Configuration` 。</span><span class="sxs-lookup"><span data-stu-id="3c8af-123">You can specify only one `Server` element for the `Configuration` element.</span></span> <span data-ttu-id="3c8af-124">在 **Database Engine Tuning Advisor XML 結構描述** 中，這個元素的名稱為 [ServerTypecomplexType](https://go.microsoft.com/fwlink/?linkid=43100)。</span><span class="sxs-lookup"><span data-stu-id="3c8af-124">This element is of the **ServerTypecomplexType** name in the [Database Engine Tuning Advisor XML schema](https://go.microsoft.com/fwlink/?linkid=43100).</span></span> <span data-ttu-id="3c8af-125">請勿混淆這個 `Server` 元素和 `DTAInput` 元素的子元素。</span><span class="sxs-lookup"><span data-stu-id="3c8af-125">Do not confuse this `Server` element with the one that is the child of the `DTAInput` element.</span></span> <span data-ttu-id="3c8af-126">如需詳細資訊，請參閱 [Server 元素 &#40;DTA&#41;](server-element-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="3c8af-126">For more information, see [Server Element &#40;DTA&#41;](server-element-dta.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c8af-127">範例</span><span class="sxs-lookup"><span data-stu-id="3c8af-127">Example</span></span>  
 <span data-ttu-id="3c8af-128">如需使用範例，請參閱[含使用者指定組態的 XML 輸入檔範例 &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="3c8af-128">For a usage example, see the [XML Input File Sample with User-specified Configuration &#40;DTA&#41;](xml-input-file-sample-with-user-specified-configuration-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c8af-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c8af-129">See Also</span></span>  
 [<span data-ttu-id="3c8af-130">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="3c8af-130">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
