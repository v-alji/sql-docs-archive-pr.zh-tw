---
title: " (DTA) 的 DatabaseToConnect 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DatabaseToConnect element
ms.assetid: 65153a66-3aee-4429-99b7-0816ac23c285
author: stevestein
ms.author: sstein
ms.openlocfilehash: 4c21b36319e4007264677d499b84964c7cb5ea7a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686630"
---
# <a name="databasetoconnect-element-dta"></a><span data-ttu-id="c0b93-102">DatabaseToConnect 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="c0b93-102">DatabaseToConnect Element (DTA)</span></span>
  <span data-ttu-id="c0b93-103">指定微調工作負載時，Database Engine Tuning Advisor 所連接的第一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="c0b93-103">Specifies the first database to which Database Engine Tuning Advisor connects when tuning a workload.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0b93-104">語法</span><span class="sxs-lookup"><span data-stu-id="c0b93-104">Syntax</span></span>  
  
```  
  
    <TuningOptions>  
...code removed here...  
      <DatabaseToConnect>...</DatabaseToConnect>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="c0b93-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="c0b93-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="c0b93-106">特性</span><span class="sxs-lookup"><span data-stu-id="c0b93-106">Characteristic</span></span>|<span data-ttu-id="c0b93-107">描述</span><span class="sxs-lookup"><span data-stu-id="c0b93-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="c0b93-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="c0b93-108">**Data type and length**</span></span>|<span data-ttu-id="c0b93-109">`string`，沒有長度限制。</span><span class="sxs-lookup"><span data-stu-id="c0b93-109">`string`, unlimited length.</span></span>|  
|<span data-ttu-id="c0b93-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="c0b93-110">**Default value**</span></span>|<span data-ttu-id="c0b93-111">無。</span><span class="sxs-lookup"><span data-stu-id="c0b93-111">None.</span></span>|  
|<span data-ttu-id="c0b93-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="c0b93-112">**Occurrence**</span></span>|<span data-ttu-id="c0b93-113">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c0b93-113">Optional.</span></span> <span data-ttu-id="c0b93-114">每個 `TuningOptions` 元素可以使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="c0b93-114">Can use once for each `TuningOptions` element.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="c0b93-115">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="c0b93-115">Element Relationships</span></span>  
  
|<span data-ttu-id="c0b93-116">關聯性</span><span class="sxs-lookup"><span data-stu-id="c0b93-116">Relationship</span></span>|<span data-ttu-id="c0b93-117">元素</span><span class="sxs-lookup"><span data-stu-id="c0b93-117">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="c0b93-118">**父元素**</span><span class="sxs-lookup"><span data-stu-id="c0b93-118">**Parent element**</span></span>|[<span data-ttu-id="c0b93-119">TuningOptions 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="c0b93-119">TuningOptions Element &#40;DTA&#41;</span></span>](tuningoptions-element-dta.md)|  
|<span data-ttu-id="c0b93-120">**子元素**</span><span class="sxs-lookup"><span data-stu-id="c0b93-120">**Child elements**</span></span>|<span data-ttu-id="c0b93-121">None</span><span class="sxs-lookup"><span data-stu-id="c0b93-121">None</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c0b93-122">備註</span><span class="sxs-lookup"><span data-stu-id="c0b93-122">Remarks</span></span>  
 <span data-ttu-id="c0b93-123">請利用 `DatabaseToConnect` 來指定 Database Engine Tuning Advisor 開始微調工作階段時，所要連接的第一個資料庫的名稱。</span><span class="sxs-lookup"><span data-stu-id="c0b93-123">Use `DatabaseToConnect` to specify the name of the first database to which you want Database Engine Tuning Advisor to connect when it starts the tuning session.</span></span> <span data-ttu-id="c0b93-124">您只能利用這個元素來指定一個資料庫。</span><span class="sxs-lookup"><span data-stu-id="c0b93-124">You can specify only one database with this element.</span></span> <span data-ttu-id="c0b93-125">如果指定了多個資料庫名稱，Database Engine Tuning Advisor 就會傳回錯誤。</span><span class="sxs-lookup"><span data-stu-id="c0b93-125">If multiple database names are specified, Database Engine Tuning Advisor returns an error.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c0b93-126">範例</span><span class="sxs-lookup"><span data-stu-id="c0b93-126">Example</span></span>  
 <span data-ttu-id="c0b93-127">如需使用範例，請參閱[含內嵌工作負載的 XML 輸入檔範例 &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="c0b93-127">For a usage example, see the [XML Input File Sample with Inline Workload &#40;DTA&#41;](xml-input-file-sample-with-inline-workload-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0b93-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0b93-128">See Also</span></span>  
 [<span data-ttu-id="c0b93-129">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="c0b93-129">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
