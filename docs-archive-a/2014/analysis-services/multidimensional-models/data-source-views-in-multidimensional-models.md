---
title: 多維度模型中的資料來源視圖 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- data source views [Analysis Services]
- data source views [Analysis Services], about data source views
- SQL Server Analysis Services, data source views
- data source views [Analysis Services], multiple
- Analysis Services, data source views
- multiple data source views
- SSAS, data source views
ms.assetid: 4c12376f-4fc2-492b-9a00-93eec34571ed
author: minewiskan
ms.author: owend
ms.openlocfilehash: 1aef6b6d716ec71ac082ca8b7c042492c1712b1a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708770"
---
# <a name="data-source-views-in-multidimensional-models"></a><span data-ttu-id="84ee3-102">多維度模型中的資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="84ee3-102">Data Source Views in Multidimensional Models</span></span>
  <span data-ttu-id="84ee3-103">資料來源檢視 (DSV) 是關聯式資料來源的摘要，其會成為您在多維度專案中建立之 Cube 與維度的根據。</span><span class="sxs-lookup"><span data-stu-id="84ee3-103">A data source view (DSV) is an abstraction of a relational data source that becomes the basis of the cubes and dimensions you create in a multidimensional project.</span></span> <span data-ttu-id="84ee3-104">DSV 的用途是可讓您控制專案所用的資料結構，以及與基礎資料來源分開運作 (例如，重新命名或串連資料行而不需要直接修改原始資料來源的能力)。</span><span class="sxs-lookup"><span data-stu-id="84ee3-104">The purpose of a DSV is to give you control over the data structures used in your project, and to work independently of the underlying data sources (for example, the ability to rename or concatenate columns without directly modifying the original data source).</span></span>  
  
 <span data-ttu-id="84ee3-105">您可以在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案或資料庫中針對一個或多個資料來源建立多個資料來源檢視，並建構每一個資料來源檢視，使其滿足不同方案的需求。</span><span class="sxs-lookup"><span data-stu-id="84ee3-105">You can build multiple data source views in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database on one or more data sources, and construct each one to satisfy the requirements for a different solution.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="84ee3-106">相關工作</span><span class="sxs-lookup"><span data-stu-id="84ee3-106">Related Tasks</span></span>  
 [<span data-ttu-id="84ee3-107">定義資料來源檢視 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="84ee3-107">Defining a Data Source View &#40;Analysis Services&#41;</span></span>](defining-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="84ee3-108">在資料來源檢視中加入或移除資料表或檢視 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="84ee3-108">Adding or Removing Tables or Views in a Data Source View &#40;Analysis Services&#41;</span></span>](adding-or-removing-tables-or-views-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="84ee3-109">變更資料來源檢視的屬性 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="84ee3-109">Change Properties in a Data Source View &#40;Analysis Services&#41;</span></span>](change-properties-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="84ee3-110">在資料來源檢視中定義邏輯關聯性 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="84ee3-110">Define Logical Relationships in a Data Source View &#40;Analysis Services&#41;</span></span>](define-logical-relationships-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="84ee3-111">在資料來源檢視中定義邏輯主索引鍵 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="84ee3-111">Define Logical Primary Keys in a Data Source View &#40;Analysis Services&#41;</span></span>](define-logical-primary-keys-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="84ee3-112">在資料來源檢視中定義具名計算 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="84ee3-112">Define Named Calculations in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="84ee3-113">在資料來源檢視中定義具名查詢 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="84ee3-113">Define Named Queries in a Data Source View &#40;Analysis Services&#41;</span></span>](define-named-queries-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="84ee3-114">取代資料來源檢視中的資料表或具名查詢 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="84ee3-114">Replace a Table or a Named Query in a Data Source View &#40;Analysis Services&#41;</span></span>](replace-a-table-or-a-named-query-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="84ee3-115">在資料來源檢視設計工具中使用圖表 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="84ee3-115">Work with Diagrams in Data Source View Designer &#40;Analysis Services&#41;</span></span>](work-with-diagrams-in-data-source-view-designer-analysis-services.md)  
  
 [<span data-ttu-id="84ee3-116">在資料來源檢視中瀏覽資料 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="84ee3-116">Explore Data in a Data Source View &#40;Analysis Services&#41;</span></span>](explore-data-in-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="84ee3-117">刪除資料來源檢視 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="84ee3-117">Delete a Data Source View &#40;Analysis Services&#41;</span></span>](delete-a-data-source-view-analysis-services.md)  
  
 [<span data-ttu-id="84ee3-118">在資料來源檢視中重新整理結構描述 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="84ee3-118">Refresh the Schema in a Data Source View &#40;Analysis Services&#41;</span></span>](refresh-the-schema-in-a-data-source-view-analysis-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="84ee3-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84ee3-119">See Also</span></span>  
 <span data-ttu-id="84ee3-120">[架構產生嚮導 &#40;Analysis Services&#41;](schema-generation-wizard-analysis-services.md) </span><span class="sxs-lookup"><span data-stu-id="84ee3-120">[Schema Generation Wizard &#40;Analysis Services&#41;](schema-generation-wizard-analysis-services.md) </span></span>  
 [<span data-ttu-id="84ee3-121">&#40;SSAS 多維度&#41;支援的資料來源</span><span class="sxs-lookup"><span data-stu-id="84ee3-121">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)  
  
  
