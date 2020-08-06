---
title: " (DTA) 的 EventString 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- EventString element
ms.assetid: f76c37b4-2f6e-4274-8ee2-87e89d98e8a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 981cd0be06fd0972426fcb2fa67b0c4143cf9178
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705786"
---
# <a name="eventstring-element-dta"></a><span data-ttu-id="9d21a-102">EventString 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="9d21a-102">EventString Element (DTA)</span></span>
  <span data-ttu-id="9d21a-103">在 XML 輸入檔中，直接指定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼工作負載。</span><span class="sxs-lookup"><span data-stu-id="9d21a-103">Specifies a [!INCLUDE[tsql](../../includes/tsql-md.md)] script workload directly in the XML input file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d21a-104">語法</span><span class="sxs-lookup"><span data-stu-id="9d21a-104">Syntax</span></span>  
  
```  
  
<Workload>  
    <EventString Weight="...">  
    ...code removed here...  
    </EventString>  
</Workload>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="9d21a-105">元素屬性</span><span class="sxs-lookup"><span data-stu-id="9d21a-105">Element Attributes</span></span>  
  
|<span data-ttu-id="9d21a-106">屬性</span><span class="sxs-lookup"><span data-stu-id="9d21a-106">Attribute</span></span>|<span data-ttu-id="9d21a-107">描述</span><span class="sxs-lookup"><span data-stu-id="9d21a-107">Description</span></span>|  
|---------------|-----------------|  
|`Weight`|<span data-ttu-id="9d21a-108">選擇性。</span><span class="sxs-lookup"><span data-stu-id="9d21a-108">Optional.</span></span> <span data-ttu-id="9d21a-109">針對指定事件來指定查詢加權因數 (重要性因數)。</span><span class="sxs-lookup"><span data-stu-id="9d21a-109">Specifies the query weight factor (a factor of importance) for the specified event.</span></span> <span data-ttu-id="9d21a-110">請利用 `float` 資料類型來指定加權。</span><span class="sxs-lookup"><span data-stu-id="9d21a-110">Use a `float` data type to specify the weight.</span></span> <span data-ttu-id="9d21a-111">例如，`Weight`="100.01"。</span><span class="sxs-lookup"><span data-stu-id="9d21a-111">For example, `Weight`="100.01".</span></span> <span data-ttu-id="9d21a-112">`Weight` 所能指定的最小值是 "0"。</span><span class="sxs-lookup"><span data-stu-id="9d21a-112">The minimum value you can specify for `Weight` is "0".</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="9d21a-113">元素特性</span><span class="sxs-lookup"><span data-stu-id="9d21a-113">Element Characteristics</span></span>  
  
|<span data-ttu-id="9d21a-114">特性</span><span class="sxs-lookup"><span data-stu-id="9d21a-114">Characteristic</span></span>|<span data-ttu-id="9d21a-115">描述</span><span class="sxs-lookup"><span data-stu-id="9d21a-115">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="9d21a-116">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="9d21a-116">**Data type and length**</span></span>|<span data-ttu-id="9d21a-117">`string`，沒有長度限制。</span><span class="sxs-lookup"><span data-stu-id="9d21a-117">`string`, length is unlimited.</span></span>|  
|<span data-ttu-id="9d21a-118">**預設值**</span><span class="sxs-lookup"><span data-stu-id="9d21a-118">**Default value**</span></span>|<span data-ttu-id="9d21a-119">無。</span><span class="sxs-lookup"><span data-stu-id="9d21a-119">None.</span></span>|  
|<span data-ttu-id="9d21a-120">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="9d21a-120">**Occurrence**</span></span>|<span data-ttu-id="9d21a-121">如果未指定任何其他工作負載類型，便需要使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="9d21a-121">Required once if no other type of workload is specified.</span></span> <span data-ttu-id="9d21a-122">您必須指定 `EventString` 父系的 `File`、`Database` 或 `Workload` 子元素，但只能使用一種類型。</span><span class="sxs-lookup"><span data-stu-id="9d21a-122">You must specify an `EventString`, a `File`, or a `Database` child element for the `Workload` parent, but only one type can be used.</span></span> <span data-ttu-id="9d21a-123">例如，如果您利用 `EventString` 元素指定了工作負載，便不能在相同 XML 輸入檔中，同時利用 `File` 元素來指定工作負載。</span><span class="sxs-lookup"><span data-stu-id="9d21a-123">For example, if you specify a workload with the `EventString` element, then you cannot also specify a workload with the `File` element in the same XML input file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="9d21a-124">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="9d21a-124">Element Relationships</span></span>  
  
|<span data-ttu-id="9d21a-125">關聯性</span><span class="sxs-lookup"><span data-stu-id="9d21a-125">Relationship</span></span>|<span data-ttu-id="9d21a-126">元素</span><span class="sxs-lookup"><span data-stu-id="9d21a-126">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="9d21a-127">**父元素**</span><span class="sxs-lookup"><span data-stu-id="9d21a-127">**Parent element**</span></span>|[<span data-ttu-id="9d21a-128">Workload 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="9d21a-128">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)|  
|<span data-ttu-id="9d21a-129">**子元素**</span><span class="sxs-lookup"><span data-stu-id="9d21a-129">**Child elements**</span></span>|<span data-ttu-id="9d21a-130">無。</span><span class="sxs-lookup"><span data-stu-id="9d21a-130">None.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="9d21a-131">範例</span><span class="sxs-lookup"><span data-stu-id="9d21a-131">Example</span></span>  
 <span data-ttu-id="9d21a-132">此元素的使用方式範例，請參閱 [XML Input File Sample with Inline Workload &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md) (內嵌工作負載的 XML 輸入檔範例 (DTA))。</span><span class="sxs-lookup"><span data-stu-id="9d21a-132">For a usage example of this element, see the [XML Input File Sample with Inline Workload &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md) .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d21a-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9d21a-133">See Also</span></span>  
 [<span data-ttu-id="9d21a-134">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="9d21a-134">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
