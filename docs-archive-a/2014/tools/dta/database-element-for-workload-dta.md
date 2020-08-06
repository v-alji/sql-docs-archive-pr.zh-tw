---
title: " (DTA) 的工作負載的 Database 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- Database element
ms.assetid: 112fca2a-37e5-4162-b2e7-b56eb8ab0c6f
author: stevestein
ms.author: sstein
ms.openlocfilehash: 2774bc7ed981c84c966a394c95347208cbc6d656
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87686634"
---
# <a name="database-element-for-workload-dta"></a><span data-ttu-id="2226e-102">工作負載的 Database 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="2226e-102">Database Element for Workload (DTA)</span></span>
  <span data-ttu-id="2226e-103">指定工作負載追蹤資料表所在的資料庫。</span><span class="sxs-lookup"><span data-stu-id="2226e-103">Specifies the database where the workload trace table is located.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2226e-104">語法</span><span class="sxs-lookup"><span data-stu-id="2226e-104">Syntax</span></span>  
  
```  
  
<Workload>  
  <Database>  
   ...code removed here...  
  </Database>  
```  
  
## <a name="element-characteristics"></a><span data-ttu-id="2226e-105">元素特性</span><span class="sxs-lookup"><span data-stu-id="2226e-105">Element Characteristics</span></span>  
  
|<span data-ttu-id="2226e-106">特性</span><span class="sxs-lookup"><span data-stu-id="2226e-106">Characteristic</span></span>|<span data-ttu-id="2226e-107">描述</span><span class="sxs-lookup"><span data-stu-id="2226e-107">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="2226e-108">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="2226e-108">**Data type and length**</span></span>|<span data-ttu-id="2226e-109">無。</span><span class="sxs-lookup"><span data-stu-id="2226e-109">None.</span></span>|  
|<span data-ttu-id="2226e-110">**預設值**</span><span class="sxs-lookup"><span data-stu-id="2226e-110">**Default value**</span></span>|<span data-ttu-id="2226e-111">無。</span><span class="sxs-lookup"><span data-stu-id="2226e-111">None.</span></span>|  
|<span data-ttu-id="2226e-112">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="2226e-112">**Occurrence**</span></span>|<span data-ttu-id="2226e-113">如果未指定任何其他工作負載類型，便需要使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="2226e-113">Required once if no other type of workload is specified.</span></span> <span data-ttu-id="2226e-114">您必須指定 `EventString` 父系的 `File`、`Database` 或 `Workload` 子元素，但只能使用一種類型。</span><span class="sxs-lookup"><span data-stu-id="2226e-114">You must specify an `EventString`, a `File`, or a `Database` child element for the `Workload` parent, but only one type can be used.</span></span> <span data-ttu-id="2226e-115">例如，如果您利用 `Database` 元素指定了工作負載，便不能在相同 XML 輸入檔中，同時利用 `File` 元素來指定工作負載。</span><span class="sxs-lookup"><span data-stu-id="2226e-115">For example, if you specify a workload with the `Database` element, you cannot also specify a workload with the `File` element in the same XML input file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="2226e-116">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="2226e-116">Element Relationships</span></span>  
  
|<span data-ttu-id="2226e-117">關聯性</span><span class="sxs-lookup"><span data-stu-id="2226e-117">Relationship</span></span>|<span data-ttu-id="2226e-118">元素</span><span class="sxs-lookup"><span data-stu-id="2226e-118">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="2226e-119">**父元素**</span><span class="sxs-lookup"><span data-stu-id="2226e-119">**Parent element**</span></span>|[<span data-ttu-id="2226e-120">Workload 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="2226e-120">Workload Element &#40;DTA&#41;</span></span>](workload-element-dta.md)|  
|<span data-ttu-id="2226e-121">**子元素**</span><span class="sxs-lookup"><span data-stu-id="2226e-121">**Child elements**</span></span>|[<span data-ttu-id="2226e-122">資料庫的 Name 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="2226e-122">Name Element for Database &#40;DTA&#41;</span></span>](name-element-for-database-dta.md)<br /><br /> [<span data-ttu-id="2226e-123">資料庫的 Schema 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="2226e-123">Schema Element for Database &#40;DTA&#41;</span></span>](schema-element-for-database-dta.md)|  
  
## <a name="remarks"></a><span data-ttu-id="2226e-124">備註</span><span class="sxs-lookup"><span data-stu-id="2226e-124">Remarks</span></span>  
 <span data-ttu-id="2226e-125">在 Database Engine Tuning Advisor XML 結構描述中，這個元素的名稱為 **DatabaseDetailsTypecomplexType** 。</span><span class="sxs-lookup"><span data-stu-id="2226e-125">This element is of the **DatabaseDetailsTypecomplexType** name in the Database Engine Tuning Advisor XML schema.</span></span> <span data-ttu-id="2226e-126">請勿混淆這個 `Database` 元素與根父系是 `Configuration` 元素的元素。</span><span class="sxs-lookup"><span data-stu-id="2226e-126">Do not confuse this `Database` element with the one whose root parent is the `Configuration` element.</span></span> <span data-ttu-id="2226e-127">(請參閱[組態的 Database 元素 &#40;DTA&#41;](database-element-for-configuration-dta.md)。)</span><span class="sxs-lookup"><span data-stu-id="2226e-127">(See [Database Element for Configuration &#40;DTA&#41;](database-element-for-configuration-dta.md).)</span></span>  
  
## <a name="example"></a><span data-ttu-id="2226e-128">範例</span><span class="sxs-lookup"><span data-stu-id="2226e-128">Example</span></span>  
 <span data-ttu-id="2226e-129">如需此元素的使用範例 `Database` ，請參閱[&#40;DTA&#41;的工作負載元素](workload-element-dta.md)中的程式碼範例。</span><span class="sxs-lookup"><span data-stu-id="2226e-129">For a usage example of this `Database` element, see the code example in [Workload Element &#40;DTA&#41;](workload-element-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2226e-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2226e-130">See Also</span></span>  
 [<span data-ttu-id="2226e-131">XML 輸入檔參考XML Input File ReferenceDatabase Engine Tuning Advisor&#41;</span><span class="sxs-lookup"><span data-stu-id="2226e-131">XML Input File Reference &#40;Database Engine Tuning Advisor&#41;</span></span>](xml-input-file-reference-database-engine-tuning-advisor.md)  
  
  
