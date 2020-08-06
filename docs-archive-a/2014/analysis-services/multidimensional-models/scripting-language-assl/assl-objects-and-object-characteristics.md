---
title: ASSL 物件和物件特性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- reference exceptions [Analysis Services Scripting Language]
- ASSL, objects
- inheritance [Analysis Services Scripting Language]
- localized names [Analysis Services Scripting Language]
- objects [Analysis Services Scripting Language]
- names [Analysis Services Scripting Language]
- Analysis Services Scripting Language, objects
- expansion [Analysis Services Scripting Language]
ms.assetid: 6e5c28b5-c0bc-4ccd-82e5-e174bbb71386
author: minewiskan
ms.author: owend
ms.openlocfilehash: 76d57bb421a7f486983476a6549a5121ce88ee9b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598025"
---
# <a name="assl-objects-and-object-characteristics"></a><span data-ttu-id="1a20f-102">ASSL 物件和物件特性</span><span class="sxs-lookup"><span data-stu-id="1a20f-102">ASSL Objects and Object Characteristics</span></span>
  <span data-ttu-id="1a20f-103">Analysis Services 指令碼語言 (ASSL) 中的物件會遵循有關物件群組、繼承、命名、擴展和處理的特定指導方針。</span><span class="sxs-lookup"><span data-stu-id="1a20f-103">Objects in Analysis Services Scripting Language (ASSL) follow specific guidelines in regards to object groups, inheritance, naming, expansion, and processing.</span></span>  
  
## <a name="object-groups"></a><span data-ttu-id="1a20f-104">物件群組</span><span class="sxs-lookup"><span data-stu-id="1a20f-104">Object Groups</span></span>  
 <span data-ttu-id="1a20f-105">所有 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 物件都有 XML 表示。</span><span class="sxs-lookup"><span data-stu-id="1a20f-105">All [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] objects have an XML representation.</span></span> <span data-ttu-id="1a20f-106">這些物件分為兩個群組：</span><span class="sxs-lookup"><span data-stu-id="1a20f-106">The objects are divided into two groups:</span></span>  
  
 <span data-ttu-id="1a20f-107">**主要物件**</span><span class="sxs-lookup"><span data-stu-id="1a20f-107">**Major objects**</span></span>  
 <span data-ttu-id="1a20f-108">主要物件可以獨立建立、改變和刪除。</span><span class="sxs-lookup"><span data-stu-id="1a20f-108">Major objects can be independently created, altered, and deleted.</span></span> <span data-ttu-id="1a20f-109">主要物件包括：</span><span class="sxs-lookup"><span data-stu-id="1a20f-109">Major objects include:</span></span>  
  
-   <span data-ttu-id="1a20f-110">伺服器</span><span class="sxs-lookup"><span data-stu-id="1a20f-110">Servers</span></span>  
  
-   <span data-ttu-id="1a20f-111">資料庫</span><span class="sxs-lookup"><span data-stu-id="1a20f-111">Databases</span></span>  
  
-   <span data-ttu-id="1a20f-112">維度</span><span class="sxs-lookup"><span data-stu-id="1a20f-112">Dimensions</span></span>  
  
-   <span data-ttu-id="1a20f-113">Cube</span><span class="sxs-lookup"><span data-stu-id="1a20f-113">Cubes</span></span>  
  
-   <span data-ttu-id="1a20f-114">量值群組</span><span class="sxs-lookup"><span data-stu-id="1a20f-114">Measure groups</span></span>  
  
-   <span data-ttu-id="1a20f-115">資料分割</span><span class="sxs-lookup"><span data-stu-id="1a20f-115">Partitions</span></span>  
  
-   <span data-ttu-id="1a20f-116">檢視方塊</span><span class="sxs-lookup"><span data-stu-id="1a20f-116">Perspectives</span></span>  
  
-   <span data-ttu-id="1a20f-117">採礦模型</span><span class="sxs-lookup"><span data-stu-id="1a20f-117">Mining models</span></span>  
  
-   <span data-ttu-id="1a20f-118">角色</span><span class="sxs-lookup"><span data-stu-id="1a20f-118">Roles</span></span>  
  
-   <span data-ttu-id="1a20f-119">與伺服器或資料庫相關聯的命令</span><span class="sxs-lookup"><span data-stu-id="1a20f-119">Commands associated with a server or database</span></span>  
  
-   <span data-ttu-id="1a20f-120">資料來源</span><span class="sxs-lookup"><span data-stu-id="1a20f-120">Data sources</span></span>  
  
 <span data-ttu-id="1a20f-121">主要物件具有下列可追蹤其記錄與狀態的屬性。</span><span class="sxs-lookup"><span data-stu-id="1a20f-121">Major objects have the following properties to track their history and status.</span></span>  
  
-   `CreatedTimestamp`  
  
-   `LastSchemaUpdate`  
  
-   <span data-ttu-id="1a20f-122">`LastProcessed` (在適當處)</span><span class="sxs-lookup"><span data-stu-id="1a20f-122">`LastProcessed` (where appropriate)</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="1a20f-123">將物件分類為主要物件會影響 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 的執行個體處理 (Treat)該物件的方式，以及如何以物件定義語言處理 (Handle) 該物件。</span><span class="sxs-lookup"><span data-stu-id="1a20f-123">The classification of an object as a major object affects how an instance of [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] treats that object and how that object is handled in the object definition language.</span></span> <span data-ttu-id="1a20f-124">不過，這個分類無法保證 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 管理與開發工具，將允許獨立地建立、修改或刪除這些物件。</span><span class="sxs-lookup"><span data-stu-id="1a20f-124">However, this classification does not guarantee that [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] management and development tools will allow the independent creation, modification, or deletion of these objects.</span></span>  
  
 <span data-ttu-id="1a20f-125">**次要物件**</span><span class="sxs-lookup"><span data-stu-id="1a20f-125">**Minor objects**</span></span>  
 <span data-ttu-id="1a20f-126">次要物件只能在父主要物件的建立、修改或刪除過程中，建立、修改或刪除。</span><span class="sxs-lookup"><span data-stu-id="1a20f-126">Minor objects can only be created, altered, or deleted as part of creating, altering, or deleting the parent major object.</span></span> <span data-ttu-id="1a20f-127">次要物件包括：</span><span class="sxs-lookup"><span data-stu-id="1a20f-127">Minor objects include:</span></span>  
  
-   <span data-ttu-id="1a20f-128">階層和層級</span><span class="sxs-lookup"><span data-stu-id="1a20f-128">Hierarchies and levels</span></span>  
  
-   <span data-ttu-id="1a20f-129">屬性</span><span class="sxs-lookup"><span data-stu-id="1a20f-129">Attributes</span></span>  
  
-   <span data-ttu-id="1a20f-130">量值</span><span class="sxs-lookup"><span data-stu-id="1a20f-130">Measures</span></span>  
  
-   <span data-ttu-id="1a20f-131">採礦模型資料行</span><span class="sxs-lookup"><span data-stu-id="1a20f-131">Mining model columns</span></span>  
  
-   <span data-ttu-id="1a20f-132">與 Cube 相關聯的命令</span><span class="sxs-lookup"><span data-stu-id="1a20f-132">Commands associated with a cube</span></span>  
  
-   <span data-ttu-id="1a20f-133">彙總</span><span class="sxs-lookup"><span data-stu-id="1a20f-133">Aggregations</span></span>  
  
## <a name="object-expansion"></a><span data-ttu-id="1a20f-134">物件展開</span><span class="sxs-lookup"><span data-stu-id="1a20f-134">Object Expansion</span></span>  
 <span data-ttu-id="1a20f-135"> 限制可用以控制伺服器傳回的 ASSL XML 展開程度。</span><span class="sxs-lookup"><span data-stu-id="1a20f-135">The `ObjectExpansion` restriction can be used to control the degree of expansion of ASSL XML returned by the server.</span></span> <span data-ttu-id="1a20f-136">這個限制具有下表中所列的選項。</span><span class="sxs-lookup"><span data-stu-id="1a20f-136">This restriction has the options listed in the following table.</span></span>  
  
|<span data-ttu-id="1a20f-137">列舉值</span><span class="sxs-lookup"><span data-stu-id="1a20f-137">Enumeration value</span></span>|<span data-ttu-id="1a20f-138">允許\<Alter></span><span class="sxs-lookup"><span data-stu-id="1a20f-138">Allowed for \<Alter></span></span>|<span data-ttu-id="1a20f-139">描述</span><span class="sxs-lookup"><span data-stu-id="1a20f-139">Description</span></span>|  
|-----------------------|---------------------------|-----------------|  
|<span data-ttu-id="1a20f-140">*ReferenceOnly*</span><span class="sxs-lookup"><span data-stu-id="1a20f-140">*ReferenceOnly*</span></span>|<span data-ttu-id="1a20f-141">否</span><span class="sxs-lookup"><span data-stu-id="1a20f-141">no</span></span>|<span data-ttu-id="1a20f-142">只會為要求的物件以及為所有包含的主要物件，遞迴地傳回名稱、識別碼和時間戳記。</span><span class="sxs-lookup"><span data-stu-id="1a20f-142">Returns only the name, ID, and timestamp for the requested object and for all contained major objects recursively.</span></span>|  
|<span data-ttu-id="1a20f-143">*ObjectProperties*</span><span class="sxs-lookup"><span data-stu-id="1a20f-143">*ObjectProperties*</span></span>|<span data-ttu-id="1a20f-144">是</span><span class="sxs-lookup"><span data-stu-id="1a20f-144">yes</span></span>|<span data-ttu-id="1a20f-145">展開要求的物件與所含的次要物件，但是不會傳回所含的主要物件。</span><span class="sxs-lookup"><span data-stu-id="1a20f-145">Expands the requested object and minor contained objects, but does not return major contained objects.</span></span>|  
|<span data-ttu-id="1a20f-146">*ExpandObject*</span><span class="sxs-lookup"><span data-stu-id="1a20f-146">*ExpandObject*</span></span>|<span data-ttu-id="1a20f-147">否</span><span class="sxs-lookup"><span data-stu-id="1a20f-147">no</span></span>|<span data-ttu-id="1a20f-148">與*ObjectProperties*相同，但也會傳回包含之主要物件的名稱、識別碼和時間戳記。</span><span class="sxs-lookup"><span data-stu-id="1a20f-148">Same as *ObjectProperties*, but also returns the name, ID, and timestamp for contained major objects.</span></span>|  
|<span data-ttu-id="1a20f-149">*ExpandFull*</span><span class="sxs-lookup"><span data-stu-id="1a20f-149">*ExpandFull*</span></span>|<span data-ttu-id="1a20f-150">是</span><span class="sxs-lookup"><span data-stu-id="1a20f-150">yes</span></span>|<span data-ttu-id="1a20f-151">以遞迴方式完全展開要求的物件以及所有包含的物件。</span><span class="sxs-lookup"><span data-stu-id="1a20f-151">Fully expands the requested object and all contained objects recursively.</span></span>|  
  
 <span data-ttu-id="1a20f-152">這個 ASSL 參考章節描述*ExpandFull*標記法。</span><span class="sxs-lookup"><span data-stu-id="1a20f-152">This ASSL reference section describes the *ExpandFull* representation.</span></span> <span data-ttu-id="1a20f-153">所有其他 `ObjectExpansion` 層級都衍生自這個層級。</span><span class="sxs-lookup"><span data-stu-id="1a20f-153">All other `ObjectExpansion` levels are derived from this level.</span></span>  
  
## <a name="object-processing"></a><span data-ttu-id="1a20f-154">物件處理</span><span class="sxs-lookup"><span data-stu-id="1a20f-154">Object Processing</span></span>  
 <span data-ttu-id="1a20f-155">ASSL 包括的唯讀元素或是屬性 (例如 `LastProcessed`)，可以從 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 執行個體讀取，但是當將命令指令碼提交到執行個體時，會省略它們。</span><span class="sxs-lookup"><span data-stu-id="1a20f-155">ASSL includes read-only elements or properties (for example, `LastProcessed`) that can be read from the [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance, but which are omitted when command scripts are submitted to the instance.</span></span> [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="1a20f-156">會在沒有警告或錯誤的情況下，忽略唯讀元素已修改的值。</span><span class="sxs-lookup"><span data-stu-id="1a20f-156">ignores modified values for read-only elements without warning or error.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <span data-ttu-id="1a20f-157">也會忽略不適當或是不相關的屬性，而不會引發驗證錯誤。</span><span class="sxs-lookup"><span data-stu-id="1a20f-157">also ignores inappropriate or irrelevant properties without raising validation errors.</span></span> <span data-ttu-id="1a20f-158">例如，X 元素應該只有在 Y 元素具有特定值時才出現。</span><span class="sxs-lookup"><span data-stu-id="1a20f-158">For example, the X element should only be present when the Y element has a particular value.</span></span> <span data-ttu-id="1a20f-159">[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 執行個體會忽略 X 元素，而不會針對 Y 元素值來驗證該元素。</span><span class="sxs-lookup"><span data-stu-id="1a20f-159">The [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance ignores the X element instead of validating that element against the value of the Y element.</span></span>  
  
  
