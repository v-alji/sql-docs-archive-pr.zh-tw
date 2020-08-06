---
title: 定義和識別 (XMLA) 的物件 |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [XML for Analysis]
- identifying objects [XML for Analysis]
- XML for Analysis, objects
- object references [XML for Analysis]
- object identifiers [XML for Analysis]
- object definitions [XML for Analysis]
- XMLA, objects
ms.assetid: 43b65f6d-0123-4556-81f0-c7a0b84361e5
author: minewiskan
ms.author: owend
ms.openlocfilehash: d2fd3263a2f8050c36747a81ab3473f5b405ef21
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599235"
---
# <a name="defining-and-identifying-objects-xmla"></a><span data-ttu-id="67651-102">定義和識別物件 (XMLA)</span><span class="sxs-lookup"><span data-stu-id="67651-102">Defining and Identifying Objects (XMLA)</span></span>
  <span data-ttu-id="67651-103">透過使用物件識別碼與物件參考，在 XML for Analysis (XMLA) 命令中識別物件，並使用 Analysis Services 指令碼語言 (ASSL) 元素 XMLA 命令來定義。</span><span class="sxs-lookup"><span data-stu-id="67651-103">Objects are identified in XML for Analysis (XMLA) commands by using object identifiers and object references, and are defined by using Analysis Services Scripting Language (ASSL) elements XMLA commands.</span></span>  
  
## <a name="object-identifiers"></a><span data-ttu-id="67651-104">物件識別碼</span><span class="sxs-lookup"><span data-stu-id="67651-104">Object Identifiers</span></span>  
 <span data-ttu-id="67651-105">物件的識別方式是使用實例上所定義之物件的唯一識別碼 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="67651-105">An object is identified by using the unique identifier of the object as defined on an instance of [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)].</span></span> <span data-ttu-id="67651-106">當 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 建立物件時，可以明確指定或是由 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體決定物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="67651-106">Object identifiers can either be explicitly specified or determined by the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance when [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] creates the object.</span></span> <span data-ttu-id="67651-107">您可以使用[探索](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover)方法來抓取後續 `Discover` 或[執行](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)方法呼叫的物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="67651-107">You can use the [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) method to retrieve object identifiers for subsequent `Discover` or [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method calls.</span></span>  
  
## <a name="object-references"></a><span data-ttu-id="67651-108">物件參考</span><span class="sxs-lookup"><span data-stu-id="67651-108">Object References</span></span>  
 <span data-ttu-id="67651-109">有數個 XMLA 命令，例如[Delete](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla)或[Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)，會使用物件參考，以明確的方式來參考物件。</span><span class="sxs-lookup"><span data-stu-id="67651-109">Several XMLA commands, such as [Delete](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/delete-element-xmla) or [Process](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla), use an object reference to refer to an object in an unambiguous manner.</span></span> <span data-ttu-id="67651-110">物件參考包含命令執行所在之物件的物件識別碼和該物件之上階的物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="67651-110">An object reference contains the object identifier of the object on which a command is executed and the object identifiers of the ancestors for that object.</span></span> <span data-ttu-id="67651-111">例如，資料分割的物件參考包含資料分割的物件識別碼，以及該資料分割的父量值群組、Cube 及資料庫之物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="67651-111">For example, the object reference for a partition contains the object identifier of the partition, as well as the object identifiers of that partition's parent measure group, cube, and database.</span></span>  
  
## <a name="object-definitions"></a><span data-ttu-id="67651-112">物件定義</span><span class="sxs-lookup"><span data-stu-id="67651-112">Object Definitions</span></span>  
 <span data-ttu-id="67651-113">XMLA 中的[create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)和[alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)命令會分別建立或更改實例上的物件 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="67651-113">The [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla) and [Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla) commands in XMLA create or alter, respectively, objects on an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span> <span data-ttu-id="67651-114">這些物件的定義會以包含 ASSL 元素的[ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla)元素表示。</span><span class="sxs-lookup"><span data-stu-id="67651-114">The definitions for those objects are represented by an [ObjectDefinition](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/objectdefinition-element-xmla) element that contains elements from ASSL.</span></span> <span data-ttu-id="67651-115">您可以使用[ID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla)元素，為所有主要和許多次要物件明確指定物件識別碼。</span><span class="sxs-lookup"><span data-stu-id="67651-115">Object identifiers can be explicitly specified for all major and many minor objects by using the [ID](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/id-element-xmla) element.</span></span> <span data-ttu-id="67651-116">如果未使用 `ID` 元素，[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 執行個體會使用待識別物件的命名慣例來提供唯一識別碼。</span><span class="sxs-lookup"><span data-stu-id="67651-116">If the `ID` element is not used, the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance provides a unique identifier, with a naming convention that depends on the object to be identified.</span></span> <span data-ttu-id="67651-117">如需如何使用 `Create` 和 `Alter` 命令來定義物件的詳細資訊，請參閱[建立和改變物件 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects)。</span><span class="sxs-lookup"><span data-stu-id="67651-117">For more information about how to use the `Create` and `Alter` commands to define objects, see [Creating and Altering Objects &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67651-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="67651-118">See Also</span></span>  
 <span data-ttu-id="67651-119">[&#40;XMLA&#41;的物件元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="67651-119">[Object Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) </span></span>  
 <span data-ttu-id="67651-120">[&#40;XMLA&#41;的 ParentObject 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="67651-120">[ParentObject Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) </span></span>  
 <span data-ttu-id="67651-121">[&#40;XMLA&#41;的 Source 元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="67651-121">[Source Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla) </span></span>  
 <span data-ttu-id="67651-122">[&#40;XMLA&#41;的目標元素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) </span><span class="sxs-lookup"><span data-stu-id="67651-122">[Target Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/target-element-xmla) </span></span>  
 [<span data-ttu-id="67651-123">在 Analysis Services 中使用 XMLA 進行開發</span><span class="sxs-lookup"><span data-stu-id="67651-123">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
