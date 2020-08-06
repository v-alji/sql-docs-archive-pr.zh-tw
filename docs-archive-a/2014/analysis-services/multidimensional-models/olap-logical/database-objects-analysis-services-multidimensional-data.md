---
title: 資料庫物件 (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- objects [Analysis Services], about objects
- SQL Server Analysis Services, objects
- Analysis Services objects, about Analysis Services objects
- SSAS, objects
- Analysis Services objects
- objects [Analysis Services]
ms.assetid: f76d869b-fc1d-4807-9f28-da09c7be382d
author: minewiskan
ms.author: owend
ms.openlocfilehash: d61e3213356146e1cf9e452e0b62e02c96bd4902
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710926"
---
# <a name="database-objects-analysis-services---multidimensional-data"></a><span data-ttu-id="bd963-102">資料庫物件 (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="bd963-102">Database Objects (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="bd963-103">[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 實例包含資料庫物件和元件，可用於線上分析處理 (OLAP) 和資料採礦。</span><span class="sxs-lookup"><span data-stu-id="bd963-103">A [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] instance contains database objects and assemblies for use with online analytical processing (OLAP) and data mining.</span></span>  
  
-   <span data-ttu-id="bd963-104">資料庫中包含 OLAP 和資料採礦物件，例如，資料來源、資料來源檢視、Cube、量值、量值群組、維度、屬性、階層、採礦結構、採礦模型及角色。</span><span class="sxs-lookup"><span data-stu-id="bd963-104">Databases contain OLAP and data mining objects, such as data sources, data source views, cubes, measures, measure groups, dimensions, attributes, hierarchies, mining structures, mining models and roles.</span></span>  
  
-   <span data-ttu-id="bd963-105">組件中包含擴充內建函數 (由多維度運算式 (MDX) 和資料採礦延伸模組 (DMX) 語言提供) 功能的使用者自訂函數。</span><span class="sxs-lookup"><span data-stu-id="bd963-105">Assemblies contain user-defined functions that extend the functionality of the intrinsic functions provided with the Multidimensional Expressions (MDX) and Data Mining Extensions (DMX) languages.</span></span>  
  
 <span data-ttu-id="bd963-106"> 物件是商業智慧專案所需之所有資料物件 (例如 OLAP Cube、維度和資料採礦結構) 及支援物件 (例如 、 和 ) 的容器。</span><span class="sxs-lookup"><span data-stu-id="bd963-106">The <xref:Microsoft.AnalysisServices.Database> object is the container for all data objects that are needed for a business intelligence project (such as OLAP cubes, dimensions, and data mining structures), and their supporting objects (such as <xref:Microsoft.AnalysisServices.DataSource>, <xref:Microsoft.AnalysisServices.Account>, and <xref:Microsoft.AnalysisServices.Role>).</span></span>  
  
 <span data-ttu-id="bd963-107"> 物件提供了包含以下項目之物件和屬性的存取權：</span><span class="sxs-lookup"><span data-stu-id="bd963-107">A <xref:Microsoft.AnalysisServices.Database> object provides access to objects and attributes that include the following:</span></span>  
  
-   <span data-ttu-id="bd963-108">您可以存取的所有 Cube (集合的形式)。</span><span class="sxs-lookup"><span data-stu-id="bd963-108">All cubes that you can access, as a collection.</span></span>  
  
-   <span data-ttu-id="bd963-109">您可以存取的所有維度 (集合的形式)。</span><span class="sxs-lookup"><span data-stu-id="bd963-109">All dimensions that you can access, as a collection.</span></span>  
  
-   <span data-ttu-id="bd963-110">您可以存取的所有採礦結構 (集合的形式)。</span><span class="sxs-lookup"><span data-stu-id="bd963-110">All mining structures that you can access, as a collection.</span></span>  
  
-   <span data-ttu-id="bd963-111">所有的資料來源和資料來源檢視 (兩個集合的形式)。</span><span class="sxs-lookup"><span data-stu-id="bd963-111">All data sources and data source views, as two collections.</span></span>  
  
-   <span data-ttu-id="bd963-112">所有的角色和資料庫權限 (兩個集合的形式)。</span><span class="sxs-lookup"><span data-stu-id="bd963-112">All roles and database permissions, as two collections.</span></span>  
  
-   <span data-ttu-id="bd963-113">資料庫的定序值。</span><span class="sxs-lookup"><span data-stu-id="bd963-113">The collation value for the database.</span></span>  
  
-   <span data-ttu-id="bd963-114">資料庫的預估大小。</span><span class="sxs-lookup"><span data-stu-id="bd963-114">The estimated size of the database.</span></span>  
  
-   <span data-ttu-id="bd963-115">資料庫的語言值。</span><span class="sxs-lookup"><span data-stu-id="bd963-115">The language value of the database.</span></span>  
  
-   <span data-ttu-id="bd963-116">資料庫的可見設定。</span><span class="sxs-lookup"><span data-stu-id="bd963-116">The visible setting for the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bd963-117">本節內容</span><span class="sxs-lookup"><span data-stu-id="bd963-117">In This Section</span></span>  
 <span data-ttu-id="bd963-118">下列主題將描述在 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中，OLAP 和資料採礦功能所共用的物件。</span><span class="sxs-lookup"><span data-stu-id="bd963-118">The following topics describe objects shared by both OLAP and data mining features in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>  
  
|<span data-ttu-id="bd963-119">主題</span><span class="sxs-lookup"><span data-stu-id="bd963-119">Topic</span></span>|<span data-ttu-id="bd963-120">描述</span><span class="sxs-lookup"><span data-stu-id="bd963-120">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="bd963-121">多維度模型中的資料來源</span><span class="sxs-lookup"><span data-stu-id="bd963-121">Data Sources in Multidimensional Models</span></span>](../data-sources-in-multidimensional-models.md)|<span data-ttu-id="bd963-122">描述 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中的資料來源。</span><span class="sxs-lookup"><span data-stu-id="bd963-122">Describes a data source in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="bd963-123">多維度模型中的資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="bd963-123">Data Source Views in Multidimensional Models</span></span>](../data-source-views-in-multidimensional-models.md)|<span data-ttu-id="bd963-124">描述在 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中以一或多個資料來源為根據的邏輯資料模型。</span><span class="sxs-lookup"><span data-stu-id="bd963-124">Describes a logical data model based on one or more data sources, in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="bd963-125">多維度模型中的 Cube</span><span class="sxs-lookup"><span data-stu-id="bd963-125">Cubes in Multidimensional Models</span></span>](../cubes-in-multidimensional-models.md)|<span data-ttu-id="bd963-126">描述 Cube 和 Cube 物件，包括：量值、量值群組、維度使用方式關聯性、計算、關鍵效能指標、動作、翻譯、分割與檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="bd963-126">Describes cubes and cube objects, including measures, measure groups, dimension usage relationships, calculations, key performance indicators, actions, translations, partitions, and perspectives.</span></span>|  
|[<span data-ttu-id="bd963-127">維度 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="bd963-127">Dimensions &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../../multidimensional-models-olap-logical-dimension-objects/dimensions-analysis-services-multidimensional-data.md)|<span data-ttu-id="bd963-128">描述維度和維度物件，其中包括屬性、屬性關聯性、階層、層級與成員。</span><span class="sxs-lookup"><span data-stu-id="bd963-128">Describes dimensions and dimension objects, including attributes, attribute relationships, hierarchies, levels, and members.</span></span>|  
|[<span data-ttu-id="bd963-129">採礦結構 &#40;Analysis Services - 資料採礦&#41;</span><span class="sxs-lookup"><span data-stu-id="bd963-129">Mining Structures &#40;Analysis Services - Data Mining&#41;</span></span>](../../data-mining/mining-structures-analysis-services-data-mining.md)|<span data-ttu-id="bd963-130">描述採礦結構和採礦物件，其中包括採礦模型。</span><span class="sxs-lookup"><span data-stu-id="bd963-130">Describes mining structures and mining objects, including mining models.</span></span>|  
|[<span data-ttu-id="bd963-131">安全性角色 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="bd963-131">Security Roles  &#40;Analysis Services - Multidimensional Data&#41;</span></span>](security-roles-analysis-services-multidimensional-data.md)|<span data-ttu-id="bd963-132">描述角色，也就是在 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中控制存取物件權限的安全性機制。</span><span class="sxs-lookup"><span data-stu-id="bd963-132">Describes a role, the security mechanism used to control access to objects in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
|[<span data-ttu-id="bd963-133">多維度模型組件管理</span><span class="sxs-lookup"><span data-stu-id="bd963-133">Multidimensional Model Assemblies Management</span></span>](../multidimensional-model-assemblies-management.md)|<span data-ttu-id="bd963-134">描述 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 中的組件，也就是用來擴充 MDX 和 DMX 語言之使用者自訂函數的集合。</span><span class="sxs-lookup"><span data-stu-id="bd963-134">Describes an assembly, a collection of user-defined functions used to extend the MDX and DMX languages, in [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)].</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bd963-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bd963-135">See Also</span></span>  
 <span data-ttu-id="bd963-136">[&#40;SSAS 多維度&#41;支援的資料來源](../supported-data-sources-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="bd963-136">[Data Sources Supported &#40;SSAS Multidimensional&#41;](../supported-data-sources-ssas-multidimensional.md) </span></span>  
 <span data-ttu-id="bd963-137">[&#40;SSAS&#41;的多維度模型方案](../multidimensional-model-solutions-ssas.md) </span><span class="sxs-lookup"><span data-stu-id="bd963-137">[Multidimensional Model Solutions &#40;SSAS&#41;](../multidimensional-model-solutions-ssas.md) </span></span>  
 [<span data-ttu-id="bd963-138">資料採礦方案</span><span class="sxs-lookup"><span data-stu-id="bd963-138">Data Mining Solutions</span></span>](../../data-mining/data-mining-solutions.md)  
  
  
