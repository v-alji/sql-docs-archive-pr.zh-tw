---
title: " (ssbdiagnose) 的橫幅元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- banner element
- XML output file format [ssbdiagnose], banner element
- ssbdiagnose
ms.assetid: cc6cd49a-acf0-4cfb-8c6a-554692b89de2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 13238ac4ef1745dea4fbf3392484ac6137c09df1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710085"
---
# <a name="banner-element-ssbdiagnose"></a><span data-ttu-id="ae5c1-102">Banner 元素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="ae5c1-102">Banner Element (ssbdiagnose)</span></span>
  <span data-ttu-id="ae5c1-103">識別產生 **ssbdiagnose** 輸出 XML 檔的公用程式。</span><span class="sxs-lookup"><span data-stu-id="ae5c1-103">Identifies which utility generated the **ssbdiagnose** output XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae5c1-104">語法</span><span class="sxs-lookup"><span data-stu-id="ae5c1-104">Syntax</span></span>  
  
```  
  
<Banner  
    title="..."   
    product="..."   
    version="..." />  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="ae5c1-105">元素屬性</span><span class="sxs-lookup"><span data-stu-id="ae5c1-105">Element Attributes</span></span>  
  
|<span data-ttu-id="ae5c1-106">屬性</span><span class="sxs-lookup"><span data-stu-id="ae5c1-106">Attribute</span></span>|<span data-ttu-id="ae5c1-107">描述</span><span class="sxs-lookup"><span data-stu-id="ae5c1-107">Description</span></span>|  
|---------------|-----------------|  
|`title`|<span data-ttu-id="ae5c1-108">識別產生 **ssbdiagnose** XML 輸出檔的公用程式。</span><span class="sxs-lookup"><span data-stu-id="ae5c1-108">Identifies the utility that generated the **ssbdiagnose** XML output file.</span></span>|  
|`product`|<span data-ttu-id="ae5c1-109">識別產生 **ssbdiagnose** XML 輸出檔的產品。</span><span class="sxs-lookup"><span data-stu-id="ae5c1-109">Identifies the product that generated the **ssbdiagnose** XML output file.</span></span>|  
|`version`|<span data-ttu-id="ae5c1-110">識別產生 XML 輸出檔的公用程式版本。</span><span class="sxs-lookup"><span data-stu-id="ae5c1-110">Identifies which version of the utility generated the XML output file.</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="ae5c1-111">元素特性</span><span class="sxs-lookup"><span data-stu-id="ae5c1-111">Element Characteristics</span></span>  
  
|<span data-ttu-id="ae5c1-112">特性</span><span class="sxs-lookup"><span data-stu-id="ae5c1-112">Characteristic</span></span>|<span data-ttu-id="ae5c1-113">描述</span><span class="sxs-lookup"><span data-stu-id="ae5c1-113">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="ae5c1-114">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="ae5c1-114">**Data type and length**</span></span>|<span data-ttu-id="ae5c1-115">無。</span><span class="sxs-lookup"><span data-stu-id="ae5c1-115">None.</span></span>|  
|<span data-ttu-id="ae5c1-116">**預設值**</span><span class="sxs-lookup"><span data-stu-id="ae5c1-116">**Default value**</span></span>|<span data-ttu-id="ae5c1-117">無。</span><span class="sxs-lookup"><span data-stu-id="ae5c1-117">None.</span></span>|  
|<span data-ttu-id="ae5c1-118">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="ae5c1-118">**Occurrence**</span></span>|<span data-ttu-id="ae5c1-119">每個 **ssbdiagnose** 輸出 XML 檔各出現一次。</span><span class="sxs-lookup"><span data-stu-id="ae5c1-119">Occurs once per **ssbdiagnose** output XML file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="ae5c1-120">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="ae5c1-120">Element Relationships</span></span>  
  
|<span data-ttu-id="ae5c1-121">關聯性</span><span class="sxs-lookup"><span data-stu-id="ae5c1-121">Relationship</span></span>|<span data-ttu-id="ae5c1-122">元素</span><span class="sxs-lookup"><span data-stu-id="ae5c1-122">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="ae5c1-123">**父元素**</span><span class="sxs-lookup"><span data-stu-id="ae5c1-123">**Parent element**</span></span>|[<span data-ttu-id="ae5c1-124">DiagnosticInformation 元素 &#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="ae5c1-124">DiagnosticInformation Element &#40;ssbdiagnose&#41;</span></span>](diagnosticinformation-element-ssbdiagnose.md)|  
|<span data-ttu-id="ae5c1-125">**子元素**</span><span class="sxs-lookup"><span data-stu-id="ae5c1-125">**Child elements**</span></span>|<span data-ttu-id="ae5c1-126">無。</span><span class="sxs-lookup"><span data-stu-id="ae5c1-126">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ae5c1-127">範例</span><span class="sxs-lookup"><span data-stu-id="ae5c1-127">Example</span></span>  
 <span data-ttu-id="ae5c1-128">這是 banner 元素的範例。</span><span class="sxs-lookup"><span data-stu-id="ae5c1-128">This is an example of a banner element.</span></span>  
  
```  
<Banner title="Service Broker Diagnostics Utility" product="Microsoft SQL Server" version="10.0.1073.0" />  
```  
  
## <a name="see-also"></a><span data-ttu-id="ae5c1-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae5c1-129">See Also</span></span>  
 [<span data-ttu-id="ae5c1-130">ssbdiagnose 公用程式 &#40;Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="ae5c1-130">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](ssbdiagnose-utility-service-broker.md)  
  
  
