---
title: " (DTA) 的 DTAXML 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: tools-other
ms.topic: conceptual
dev_langs:
- XML
helpviewer_keywords:
- DTAXML element
ms.assetid: 3d9942ed-8a27-40db-a7c9-808984d914a2
author: stevestein
ms.author: sstein
ms.openlocfilehash: 9f428cf996bb819ece74c13226fcd5116a19142b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703634"
---
# <a name="dtaxml-element-dta"></a><span data-ttu-id="1ec6d-102">DTAXML 元素 (DTA)</span><span class="sxs-lookup"><span data-stu-id="1ec6d-102">DTAXML Element (DTA)</span></span>
  <span data-ttu-id="1ec6d-103">Database Engine Tuning Advisor XML 輸入或輸出檔的根元素， **DTAXML** 包含說明 Database Engine Tuning Advisor 所產生之微調輸入和微調輸出的所有元素。</span><span class="sxs-lookup"><span data-stu-id="1ec6d-103">The root element of a Database Engine Tuning Advisor XML input or output file, **DTAXML** contains all elements that describe tuning input and the tuning output that Database Engine Tuning Advisor generates.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ec6d-104">語法</span><span class="sxs-lookup"><span data-stu-id="1ec6d-104">Syntax</span></span>  
  
```  
  
<DTAXML   
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"   
    xmlns="https://schemas.microsoft.com/sqlserver/2004/07/dta">  
    ...code removed here...  
</DTAXML>  
```  
  
## <a name="element-attributes"></a><span data-ttu-id="1ec6d-105">元素屬性</span><span class="sxs-lookup"><span data-stu-id="1ec6d-105">Element Attributes</span></span>  
  
|<span data-ttu-id="1ec6d-106">屬性</span><span class="sxs-lookup"><span data-stu-id="1ec6d-106">Attribute</span></span>|<span data-ttu-id="1ec6d-107">描述</span><span class="sxs-lookup"><span data-stu-id="1ec6d-107">Description</span></span>|  
|---------------|-----------------|  
|`xmlns:xsi`|<span data-ttu-id="1ec6d-108">必要。</span><span class="sxs-lookup"><span data-stu-id="1ec6d-108">Required.</span></span> <span data-ttu-id="1ec6d-109">識別 XML 結構描述執行個體命名空間。</span><span class="sxs-lookup"><span data-stu-id="1ec6d-109">Identifies the XML Schema Instance namespace.</span></span> <span data-ttu-id="1ec6d-110">這個命名空間的屬性用來參考驗證 Database Engine Tuning Advisor XML 檔時所用的結構描述。</span><span class="sxs-lookup"><span data-stu-id="1ec6d-110">Attributes from this namespace are used to reference the schema that is used to validate the Database Engine Tuning Advisor XML file.</span></span><br /><br /> <span data-ttu-id="1ec6d-111">必要值：[http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)</span><span class="sxs-lookup"><span data-stu-id="1ec6d-111">Required value: [http://www.w3.org/2001/XMLSchema-instance](http://www.w3.org/2001/XMLSchema-instance)</span></span>|  
|`xmlns`|<span data-ttu-id="1ec6d-112">必要。</span><span class="sxs-lookup"><span data-stu-id="1ec6d-112">Required.</span></span> <span data-ttu-id="1ec6d-113">識別 Database Engine Tuning Advisor 命名空間。</span><span class="sxs-lookup"><span data-stu-id="1ec6d-113">Identifies the Database Engine Tuning Advisor namespace.</span></span><br /><br /> <span data-ttu-id="1ec6d-114">如果您利用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中的 XML 編輯器來編輯 Database Engine Tuning Advisor，[F1 說明和動態說明] 便會利用這個值，在《 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 線上叢書》中，尋找可能的參考主題。</span><span class="sxs-lookup"><span data-stu-id="1ec6d-114">If you edit the Database Engine Tuning Advisor XML file using the XML editor in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], this value is used by F1 Help and Dynamic Help to locate possible reference topics in [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Books Online.</span></span><br /><br /> <span data-ttu-id="1ec6d-115">必要值：</span><span class="sxs-lookup"><span data-stu-id="1ec6d-115">Required value:</span></span><br /><br /> <span data-ttu-id="1ec6d-116">[Database Engine Tuning Advisor XML 結構描述](https://go.microsoft.com/fwlink/?LinkId=43100) 命名空間</span><span class="sxs-lookup"><span data-stu-id="1ec6d-116">[Database Engine Tuning Advisor XML Schema](https://go.microsoft.com/fwlink/?LinkId=43100) Namespace</span></span>|  
  
## <a name="element-characteristics"></a><span data-ttu-id="1ec6d-117">元素特性</span><span class="sxs-lookup"><span data-stu-id="1ec6d-117">Element Characteristics</span></span>  
  
|<span data-ttu-id="1ec6d-118">特性</span><span class="sxs-lookup"><span data-stu-id="1ec6d-118">Characteristic</span></span>|<span data-ttu-id="1ec6d-119">描述</span><span class="sxs-lookup"><span data-stu-id="1ec6d-119">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="1ec6d-120">**資料類型和長度**</span><span class="sxs-lookup"><span data-stu-id="1ec6d-120">**Data type and length**</span></span>|<span data-ttu-id="1ec6d-121">無。</span><span class="sxs-lookup"><span data-stu-id="1ec6d-121">None.</span></span>|  
|<span data-ttu-id="1ec6d-122">**預設值**</span><span class="sxs-lookup"><span data-stu-id="1ec6d-122">**Default value**</span></span>|<span data-ttu-id="1ec6d-123">無。</span><span class="sxs-lookup"><span data-stu-id="1ec6d-123">None.</span></span>|  
|<span data-ttu-id="1ec6d-124">**出現次數**</span><span class="sxs-lookup"><span data-stu-id="1ec6d-124">**Occurrence**</span></span>|<span data-ttu-id="1ec6d-125">每個 DTA XML 檔需要使用這個元素一次。</span><span class="sxs-lookup"><span data-stu-id="1ec6d-125">Required once per DTA XML file.</span></span>|  
  
## <a name="element-relationships"></a><span data-ttu-id="1ec6d-126">元素關聯性</span><span class="sxs-lookup"><span data-stu-id="1ec6d-126">Element Relationships</span></span>  
  
|<span data-ttu-id="1ec6d-127">關聯性</span><span class="sxs-lookup"><span data-stu-id="1ec6d-127">Relationship</span></span>|<span data-ttu-id="1ec6d-128">元素</span><span class="sxs-lookup"><span data-stu-id="1ec6d-128">Elements</span></span>|  
|------------------|--------------|  
|<span data-ttu-id="1ec6d-129">**父元素**</span><span class="sxs-lookup"><span data-stu-id="1ec6d-129">**Parent element**</span></span>|<span data-ttu-id="1ec6d-130">None</span><span class="sxs-lookup"><span data-stu-id="1ec6d-130">None</span></span>|  
|<span data-ttu-id="1ec6d-131">**子元素**</span><span class="sxs-lookup"><span data-stu-id="1ec6d-131">**Child elements**</span></span>|[<span data-ttu-id="1ec6d-132">DTAInput 元素 &#40;DTA&#41;</span><span class="sxs-lookup"><span data-stu-id="1ec6d-132">DTAInput Element &#40;DTA&#41;</span></span>](dtainput-element-dta.md)<br /><br /> <span data-ttu-id="1ec6d-133">`DTAOutput`元素 (如需資訊，請參閱[DATABASE ENGINE TUNING ADVISOR XML 架構](https://schemas.microsoft.com/sqlserver/)) </span><span class="sxs-lookup"><span data-stu-id="1ec6d-133">`DTAOutput` Element (see [Database Engine Tuning Advisor XML schema](https://schemas.microsoft.com/sqlserver/) for information)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ec6d-134">備註</span><span class="sxs-lookup"><span data-stu-id="1ec6d-134">Remarks</span></span>  
 <span data-ttu-id="1ec6d-135">如需有關 XML 命名空間的詳細資訊，請參閱 [MSDN Library 中的＜](https://go.microsoft.com/fwlink/?LinkId=7341) XML 文件中的命名空間 [!INCLUDE[msCoName](../../includes/msconame-md.md)] ＞(英文)。</span><span class="sxs-lookup"><span data-stu-id="1ec6d-135">For more information about XML namespaces, see [Namespaces in an XML Document](https://go.microsoft.com/fwlink/?LinkId=7341) in the [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN Library.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ec6d-136">範例</span><span class="sxs-lookup"><span data-stu-id="1ec6d-136">Example</span></span>  
 <span data-ttu-id="1ec6d-137">如需一般 **DTAXML** 元素的範例，請參閱 [XML 輸入檔範例 &#40;DTA&#41;](xml-input-file-samples-dta.md)。</span><span class="sxs-lookup"><span data-stu-id="1ec6d-137">For examples of typical **DTAXML** elements, see [XML Input File Samples &#40;DTA&#41;](xml-input-file-samples-dta.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1ec6d-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ec6d-138">See Also</span></span>  
 <span data-ttu-id="1ec6d-139">[XML 輸入檔參考 &#40;Database Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md) </span><span class="sxs-lookup"><span data-stu-id="1ec6d-139">[XML Input File Reference &#40;Database Engine Tuning Advisor&#41;](xml-input-file-reference-database-engine-tuning-advisor.md) </span></span>  
 [<span data-ttu-id="1ec6d-140">啟動及使用 Database Engine Tuning Advisor</span><span class="sxs-lookup"><span data-stu-id="1ec6d-140">Start and Use the Database Engine Tuning Advisor</span></span>](../../relational-databases/performance/start-and-use-the-database-engine-tuning-advisor.md)  
  
  
