---
title: DiagnosticInformation 元素 (ssbdiagnose) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
helpviewer_keywords:
- XML output file format [ssbdiagnose], diagnosticinformation element
- diagnosticinformation element
- ssbdiagnose
ms.assetid: 0cfda544-542c-4cf4-86d2-8031c91b10f6
author: stevestein
ms.author: sstein
ms.openlocfilehash: 92d76a065c24ddc1fc8d85989ed3202308571951
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593255"
---
# <a name="diagnosticinformation-element-ssbdiagnose"></a><span data-ttu-id="62e8d-102">DiagnosticInformation 元素 (ssbdiagnose)</span><span class="sxs-lookup"><span data-stu-id="62e8d-102">DiagnosticInformation Element (ssbdiagnose)</span></span>
  <span data-ttu-id="62e8d-103">**DiagnosticInformation** 元素包含報告此公用程式找到之診斷資訊的所有元素。</span><span class="sxs-lookup"><span data-stu-id="62e8d-103">The **DiagnosticInformation** element contains all elements that report the diagnostic information found by the utility.</span></span> <span data-ttu-id="62e8d-104">**DiagnosticInformation** 是 **ssbdiagnostic** XML 輸出檔的根元素。</span><span class="sxs-lookup"><span data-stu-id="62e8d-104">**DiagnosticInformation** is the root element of a **ssbdiagnostic** XML output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62e8d-105">語法</span><span class="sxs-lookup"><span data-stu-id="62e8d-105">Syntax</span></span>  
  
```  
  
<DiagnosticInformation>   
    ...   
</DiagnosticInformation>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="62e8d-106">元素屬性</span><span class="sxs-lookup"><span data-stu-id="62e8d-106">Element Attributes</span></span>  
  
|<span data-ttu-id="62e8d-107">屬性</span><span class="sxs-lookup"><span data-stu-id="62e8d-107">Attribute</span></span>|<span data-ttu-id="62e8d-108">描述</span><span class="sxs-lookup"><span data-stu-id="62e8d-108">Description</span></span>|  
|---------------|-----------------|  
|`None`|<span data-ttu-id="62e8d-109">N/A</span><span class="sxs-lookup"><span data-stu-id="62e8d-109">N/A</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="62e8d-110">元素特性</span><span class="sxs-lookup"><span data-stu-id="62e8d-110">Element Characteristics</span></span>  
  
|<span data-ttu-id="62e8d-111">特性</span><span class="sxs-lookup"><span data-stu-id="62e8d-111">Characteristic</span></span>|<span data-ttu-id="62e8d-112">描述</span><span class="sxs-lookup"><span data-stu-id="62e8d-112">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="62e8d-113">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="62e8d-113">**Data type and length**</span></span>|<span data-ttu-id="62e8d-114">無。</span><span class="sxs-lookup"><span data-stu-id="62e8d-114">None.</span></span>|  
|<span data-ttu-id="62e8d-115">**預設值**</span><span class="sxs-lookup"><span data-stu-id="62e8d-115">**Default value**</span></span>|<span data-ttu-id="62e8d-116">無。</span><span class="sxs-lookup"><span data-stu-id="62e8d-116">None.</span></span>|  
|<span data-ttu-id="62e8d-117">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="62e8d-117">**Occurrence**</span></span>|<span data-ttu-id="62e8d-118">每個 **ssbdiagnose** XML 輸出檔發生一次。</span><span class="sxs-lookup"><span data-stu-id="62e8d-118">Once per **ssbdiagnose** XML output file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="62e8d-119">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="62e8d-119">Element Relationships</span></span>  
  
|<span data-ttu-id="62e8d-120">關聯性</span><span class="sxs-lookup"><span data-stu-id="62e8d-120">Relationship</span></span>|<span data-ttu-id="62e8d-121">元素</span><span class="sxs-lookup"><span data-stu-id="62e8d-121">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="62e8d-122">**父元素**</span><span class="sxs-lookup"><span data-stu-id="62e8d-122">**Parent element**</span></span>|<span data-ttu-id="62e8d-123">無。</span><span class="sxs-lookup"><span data-stu-id="62e8d-123">None.</span></span>|  
|<span data-ttu-id="62e8d-124">**子元素**</span><span class="sxs-lookup"><span data-stu-id="62e8d-124">**Child elements**</span></span>|[<span data-ttu-id="62e8d-125">Banner 元素 &#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="62e8d-125">Banner Element &#40;ssbdiagnose&#41;</span></span>](banner-element-ssbdiagnose.md)<br /><br /> [<span data-ttu-id="62e8d-126">Issue 元素 &#40;ssbdiagnose&#41;</span><span class="sxs-lookup"><span data-stu-id="62e8d-126">Issue Element &#40;ssbdiagnose&#41;</span></span>](issue-element-ssbdiagnose.md)|  
  
## <a name="remarks"></a><span data-ttu-id="62e8d-127">備註</span><span class="sxs-lookup"><span data-stu-id="62e8d-127">Remarks</span></span>  
 <span data-ttu-id="62e8d-128">如需有關 XML 命名空間的詳細資訊，請參閱 [MSDN Library 中的＜](https://go.microsoft.com/fwlink/?LinkId=7341) XML 文件中的命名空間 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ＞(英文)。</span><span class="sxs-lookup"><span data-stu-id="62e8d-128">For more information about XML namespaces, see [Namespaces in an XML Document](https://go.microsoft.com/fwlink/?LinkId=7341) in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e8d-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="62e8d-129">See Also</span></span>  
 [<span data-ttu-id="62e8d-130">ssbdiagnose 公用程式 &#40;Service Broker&#41;</span><span class="sxs-lookup"><span data-stu-id="62e8d-130">ssbdiagnose Utility &#40;Service Broker&#41;</span></span>](ssbdiagnose-utility-service-broker.md)  
  
  
