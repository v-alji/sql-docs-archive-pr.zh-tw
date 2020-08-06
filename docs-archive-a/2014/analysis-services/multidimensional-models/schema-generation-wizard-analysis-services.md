---
title: 架構產生嚮導 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- relational schema [Analysis Services]
ms.assetid: 68bf7ba3-d0cb-437f-9a3e-9edc0999af19
author: minewiskan
ms.author: owend
ms.openlocfilehash: 2cd58ada8ea4c2dd17ba4427578ac1336a6bd353
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598026"
---
# <a name="schema-generation-wizard-analysis-services"></a><span data-ttu-id="81220-102">結構描述產生精靈 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="81220-102">Schema Generation Wizard (Analysis Services)</span></span>
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] <span data-ttu-id="81220-103">支援在 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案或資料庫內定義 OLAP 物件時，使用關聯式結構描述的兩個方法。</span><span class="sxs-lookup"><span data-stu-id="81220-103">supports two methods of working with relational schemas when defining OLAP objects within an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span> <span data-ttu-id="81220-104">一般來說，您會根據 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案或資料庫內資料來源檢視中所建構的邏輯資料模型來定義 OLAP 物件。</span><span class="sxs-lookup"><span data-stu-id="81220-104">Generally, you will define OLAP objects based on a logical data model constructed in a data source view within an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span> <span data-ttu-id="81220-105">這個資料來源檢視是根據一個或多個關聯式資料來源中的結構描述元素所定義，如資料來源檢視中所自訂的方式一樣。</span><span class="sxs-lookup"><span data-stu-id="81220-105">This data source view is defined based on schema elements from one or more relational data sources, as customized in the data source view.</span></span>  
  
 <span data-ttu-id="81220-106">或者，您可以先定義 OLAP 物件，再產生支援這些 OLAP 物件的資料來源檢視、資料來源及基礎關聯式資料庫結構描述。</span><span class="sxs-lookup"><span data-stu-id="81220-106">Alternatively, you can define OLAP objects first, and then generate a data source view, a data source, and the underlying relational database schema that supports these OLAP objects.</span></span> <span data-ttu-id="81220-107">此關聯式資料庫稱為主題領域資料庫。</span><span class="sxs-lookup"><span data-stu-id="81220-107">This relational database is referred to as the subject area database.</span></span>  
  
 <span data-ttu-id="81220-108">這個方法有時稱為由上而下設計，而且經常用於建立原型和分析模型。</span><span class="sxs-lookup"><span data-stu-id="81220-108">This approach is sometimes called top-down design and is frequently used for prototyping and analysis modeling.</span></span> <span data-ttu-id="81220-109">當您使用這個方法時，您可以使用 [結構描述產生精靈] 根據 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 專案或資料庫中定義的 OLAP 物件，來建立基礎資料來源檢視和資料來源物件。</span><span class="sxs-lookup"><span data-stu-id="81220-109">When you use this approach, you use the Schema Generation Wizard to create the underlying data source view and data source objects based on the OLAP objects defined in an [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] project or database.</span></span>  
  
 <span data-ttu-id="81220-110">這是一個反覆執行的方法。</span><span class="sxs-lookup"><span data-stu-id="81220-110">This is an iterative approach.</span></span> <span data-ttu-id="81220-111">您很有可能會隨變更維度和 Cube 的設計，多次重新執行精靈。</span><span class="sxs-lookup"><span data-stu-id="81220-111">You will most likely rerun the wizard multiple times as you change the design of the dimensions and cubes.</span></span> <span data-ttu-id="81220-112">每次執行精靈時，精靈會將變更併入基礎物件，而且盡可能保留基礎資料庫中所包含的資料。</span><span class="sxs-lookup"><span data-stu-id="81220-112">Each time you run the wizard, it incorporates the changes into the underlying objects and, as much as is possible, preserves the data contained in the underlying databases.</span></span>  
  
 <span data-ttu-id="81220-113">產生的結構描述是 SQL Server 關聯式資料庫引擎結構描述。</span><span class="sxs-lookup"><span data-stu-id="81220-113">The schema that is generated is a SQL Server relational database engine schema.</span></span> <span data-ttu-id="81220-114">此精靈不會產生其他關聯式資料庫產品的結構描述。</span><span class="sxs-lookup"><span data-stu-id="81220-114">The wizard does not generate schemas for other relational database products.</span></span>  
  
 <span data-ttu-id="81220-115">在主題領域資料庫中擴展的資料，會使用您用來擴展 SQL Server 關聯式資料庫的任何工具和技術個別加入。</span><span class="sxs-lookup"><span data-stu-id="81220-115">The data that is populated in the subject area database is added separately, using whatever tools and techniques you use to populate a SQL Server relational database.</span></span> <span data-ttu-id="81220-116">在大多數情況下，當您重新執行精靈時會保留資料，但是也有例外狀況。</span><span class="sxs-lookup"><span data-stu-id="81220-116">In most cases, the data is preserved when you rerun the wizard, but there are exceptions.</span></span> <span data-ttu-id="81220-117">例如，您若是刪除包含資料的維度或屬性，就必須捨棄某些資料。</span><span class="sxs-lookup"><span data-stu-id="81220-117">For example, some data must be dropped if you delete a dimension or an attribute that contains data.</span></span> <span data-ttu-id="81220-118">如果因為結構描述變更，以致結構描述產生精靈必須捨棄某些資料，您會在捨棄資料之前收到警告，然後可以取消重新產生。</span><span class="sxs-lookup"><span data-stu-id="81220-118">If the Schema Generation Wizard must drop some data because of a schema change, you receive a warning before the data is dropped and can then cancel the regeneration.</span></span>  
  
 <span data-ttu-id="81220-119">一般規則是結構描述產生精靈重新產生物件時，會覆寫您對結構描述產生精靈原來產生之物件所做的任何變更。</span><span class="sxs-lookup"><span data-stu-id="81220-119">As a general rule, any change that you make to an object that was originally generated by the Schema Generation Wizard is overwritten when the Schema Generation Wizard subsequently regenerates that object.</span></span> <span data-ttu-id="81220-120">這個規則的主要例外狀況，是您將資料行加入至結構描述產生精靈所產生的資料表時。</span><span class="sxs-lookup"><span data-stu-id="81220-120">The primary exception to this rule is when you add columns to a table that the Schema Generation Wizard generated.</span></span> <span data-ttu-id="81220-121">在此情況下，[結構描述產生精靈] 會保留您加入至資料表的資料行，以及這些資料行裡的資料。</span><span class="sxs-lookup"><span data-stu-id="81220-121">In this case, the Schema Generation Wizard preserves the columns that you added to the table, as well as the data in these columns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="81220-122">本節內容</span><span class="sxs-lookup"><span data-stu-id="81220-122">In this section</span></span>  
 <span data-ttu-id="81220-123">下表列出說明如何使用 [結構描述產生精靈] 的其他主題。</span><span class="sxs-lookup"><span data-stu-id="81220-123">The following table lists additional topics that explain how to work with the Schema Generation Wizard.</span></span>  
  
|<span data-ttu-id="81220-124">主題</span><span class="sxs-lookup"><span data-stu-id="81220-124">Topic</span></span>|<span data-ttu-id="81220-125">描述</span><span class="sxs-lookup"><span data-stu-id="81220-125">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="81220-126">使用結構描述產生精靈 &#40;Analysis Services&#41;</span><span class="sxs-lookup"><span data-stu-id="81220-126">Use the Schema Generation Wizard &#40;Analysis Services&#41;</span></span>](schema-generation-wizard-analysis-services.md)|<span data-ttu-id="81220-127">描述如何產生主題領域和暫存區域資料庫的結構描述。</span><span class="sxs-lookup"><span data-stu-id="81220-127">Describes how to generate the schema for the subject area and staging area databases.</span></span>|  
|[<span data-ttu-id="81220-128">了解資料庫結構描述</span><span class="sxs-lookup"><span data-stu-id="81220-128">Understanding the Database Schemas</span></span>](understanding-the-database-schemas.md)|<span data-ttu-id="81220-129">描述針對主題領域和臨時區域資料庫產生的結構描述。</span><span class="sxs-lookup"><span data-stu-id="81220-129">Describes the schema that is generated for the subject area and staging area databases.</span></span>|  
|[<span data-ttu-id="81220-130">了解累加式產生</span><span class="sxs-lookup"><span data-stu-id="81220-130">Understanding Incremental Generation</span></span>](understanding-incremental-generation.md)|<span data-ttu-id="81220-131">描述結構描述產生精靈的累加產生能力。</span><span class="sxs-lookup"><span data-stu-id="81220-131">Describes the incremental generation capabilities of the Schema Generation Wizard.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="81220-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="81220-132">See Also</span></span>  
 <span data-ttu-id="81220-133">[多維度模型中的資料來源視圖](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="81220-133">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="81220-134">[多維度模型中的資料來源](data-sources-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="81220-134">[Data Sources in Multidimensional Models](data-sources-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="81220-135">&#40;SSAS 多維度&#41;支援的資料來源</span><span class="sxs-lookup"><span data-stu-id="81220-135">Data Sources Supported &#40;SSAS Multidimensional&#41;</span></span>](supported-data-sources-ssas-multidimensional.md)  
  
  
