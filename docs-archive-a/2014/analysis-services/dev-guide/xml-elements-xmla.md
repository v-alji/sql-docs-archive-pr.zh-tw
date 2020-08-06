---
title: " (XMLA) 的 XML 元素 |Microsoft Docs"
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- XMLA, elements
- XML for Analysis, elements
- elements [XML for Analysis]
ms.assetid: 40ab2360-efb6-4ba6-bf23-e84964e51008
author: minewiskan
ms.author: owend
ms.openlocfilehash: 5c1e5b046bfa57302baefc43a4da989be9c70e08
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599261"
---
# <a name="xml-elements-xmla"></a><span data-ttu-id="a6880-102">XML 元素 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="a6880-102">XML Elements (XMLA)</span></span>
  <span data-ttu-id="a6880-103">下列主題描述支援的各種 XML for Analysis (XMLA) 元素類別 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="a6880-103">The following topics describe the various XML for Analysis (XMLA) element categories supported by [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a6880-104">本節內容</span><span class="sxs-lookup"><span data-stu-id="a6880-104">In This Section</span></span>  
  
|<span data-ttu-id="a6880-105">屬性</span><span class="sxs-lookup"><span data-stu-id="a6880-105">Property</span></span>|<span data-ttu-id="a6880-106">描述</span><span class="sxs-lookup"><span data-stu-id="a6880-106">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="a6880-107">&#40;XMLA&#41;的標頭</span><span class="sxs-lookup"><span data-stu-id="a6880-107">Headers &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-headers/xml-elements-headers)|<span data-ttu-id="a6880-108">描述由應用程式或 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體針對管理通訊協定層級功能，透過 SOAP Envelope 的 SOAP 標頭傳送的元素。</span><span class="sxs-lookup"><span data-stu-id="a6880-108">Describes those elements sent in the SOAP header of a SOAP envelope, either by an application or by an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance, to manage protocol-level features.</span></span>|  
|[<span data-ttu-id="a6880-109">XMLA&#41;的方法 &#40;</span><span class="sxs-lookup"><span data-stu-id="a6880-109">Methods &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods)|<span data-ttu-id="a6880-110">描述由應用程式針對擷取資料或中繼資料或在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體上執行動作，透過 SOAP Envelope 傳送給執行個體的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="a6880-110">Describes the topmost elements sent by an application in a SOAP envelope to an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance to retrieve data or metadata, or to perform actions on the instance.</span></span>|  
|[<span data-ttu-id="a6880-111">&#40;XMLA&#41;的命令</span><span class="sxs-lookup"><span data-stu-id="a6880-111">Commands &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/xml-elements-commands)|<span data-ttu-id="a6880-112">描述針對執行特定動作，透過 XMLA 方法傳送的元素。</span><span class="sxs-lookup"><span data-stu-id="a6880-112">Describes the elements sent within an XMLA method to perform a specific action.</span></span>|  
|[<span data-ttu-id="a6880-113">&#40;XMLA&#41;的物件</span><span class="sxs-lookup"><span data-stu-id="a6880-113">Objects &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)|<span data-ttu-id="a6880-114">描述由應用程式為了回應 XMLA 方法，透過 SOAP Envelope 從 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體收到的最上層元素。</span><span class="sxs-lookup"><span data-stu-id="a6880-114">Describes the topmost elements received by an application in a SOAP envelope from an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance in response to an XMLA method.</span></span>|  
|[<span data-ttu-id="a6880-115">XMLA&#41;的屬性 &#40;</span><span class="sxs-lookup"><span data-stu-id="a6880-115">Properties &#40;XMLA&#41;</span></span>](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/xml-elements-properties)|<span data-ttu-id="a6880-116">描述 XMLA 標頭、方法、物件或命令的子元素。</span><span class="sxs-lookup"><span data-stu-id="a6880-116">Describes the child elements for XMLA headers, methods, objects, or commands.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a6880-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6880-117">See Also</span></span>  
 <span data-ttu-id="a6880-118">[&#40;XMLA&#41;的 XML 資料類型](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/xml-data-types-xmla) </span><span class="sxs-lookup"><span data-stu-id="a6880-118">[XML Data Types &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/xml-data-types-xmla) </span></span>  
 [<span data-ttu-id="a6880-119">使用 Analysis Services 指令碼語言 &#40;ASSL&#41; 開發</span><span class="sxs-lookup"><span data-stu-id="a6880-119">Developing with Analysis Services Scripting Language &#40;ASSL&#41;</span></span>](../multidimensional-models/scripting-language-assl/developing-with-analysis-services-scripting-language-assl.md)  
  
  
