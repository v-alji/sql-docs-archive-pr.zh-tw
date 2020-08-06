---
title: 多維度模型中的 cube |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- OLAP objects [Analysis Services], cubes
- cubes [Analysis Services], about cubes
- cubes [Analysis Services]
- OLAP [Analysis Services], cubes
ms.assetid: e0f7acf3-4b07-41fc-a5fc-ac30b4a56c54
author: minewiskan
ms.author: owend
ms.openlocfilehash: 372bb8075b232ff8fbf8a54facf9bc065e6763a3
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708778"
---
# <a name="cubes-in-multidimensional-models"></a><span data-ttu-id="1e5b0-102">多維度模型中的 Cube</span><span class="sxs-lookup"><span data-stu-id="1e5b0-102">Cubes in Multidimensional Models</span></span>
  <span data-ttu-id="1e5b0-103">Cube 是包含用於分析之資訊的多維度結構；Cube 主要由維度和量值構成。</span><span class="sxs-lookup"><span data-stu-id="1e5b0-103">A cube is a multidimensional structure that contains information for analytical purposes; the main constituents of a cube are dimensions and measures.</span></span> <span data-ttu-id="1e5b0-104">維度定義 Cube 的結構 (可進一步切割資料)，而量值提供使用者感興趣的彙總數值。</span><span class="sxs-lookup"><span data-stu-id="1e5b0-104">Dimensions define the structure of the cube that you use to slice and dice over, and measures provide aggregated numerical values of interest to the end user.</span></span> <span data-ttu-id="1e5b0-105">如同邏輯結構，Cube 允許用戶端應用程式擷取 (量值的) 值，就如同值包含在 Cube 的資料格中一樣；資料格是為每個可能的摘要值所定義。</span><span class="sxs-lookup"><span data-stu-id="1e5b0-105">As a logical structure, a cube allows a client application to retrieve values, of measures, as if they were contained in cells in the cube; cells are defined for every possible summarized value.</span></span> <span data-ttu-id="1e5b0-106">Cube 中的資料格是由維度成員的交集所定義，並且包含該特定交集處之量值的彙總值。</span><span class="sxs-lookup"><span data-stu-id="1e5b0-106">A cell, in the cube, is defined by the intersection of dimension members and contains the aggregated values of the measures at that specific intersection.</span></span>  
  
## <a name="benefits-of-using-cubes"></a><span data-ttu-id="1e5b0-107">使用 Cube 的優點</span><span class="sxs-lookup"><span data-stu-id="1e5b0-107">Benefits of Using Cubes</span></span>  
 <span data-ttu-id="1e5b0-108">Cube 提供儲存所有相關資料以進行分析的單一位置。</span><span class="sxs-lookup"><span data-stu-id="1e5b0-108">A cube provides a single place where all related data, for analysis, is stored.</span></span>  
  
## <a name="components-of-cubes"></a><span data-ttu-id="1e5b0-109">Cube 的元件</span><span class="sxs-lookup"><span data-stu-id="1e5b0-109">Components of Cubes</span></span>  
 <span data-ttu-id="1e5b0-110">Cube 是由下列元件構成：</span><span class="sxs-lookup"><span data-stu-id="1e5b0-110">A cube is composed of:</span></span>  
  
|<span data-ttu-id="1e5b0-111">元素</span><span class="sxs-lookup"><span data-stu-id="1e5b0-111">Element</span></span>|<span data-ttu-id="1e5b0-112">描述</span><span class="sxs-lookup"><span data-stu-id="1e5b0-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1e5b0-113">維度</span><span class="sxs-lookup"><span data-stu-id="1e5b0-113">Dimensions</span></span>|[<span data-ttu-id="1e5b0-114">多維度模型中的維度</span><span class="sxs-lookup"><span data-stu-id="1e5b0-114">Dimensions in Multidimensional Models</span></span>](dimensions-in-multidimensional-models.md)|  
|<span data-ttu-id="1e5b0-115">量值和量值群組</span><span class="sxs-lookup"><span data-stu-id="1e5b0-115">Measures and Measure Groups</span></span>|[<span data-ttu-id="1e5b0-116">在多維度模型中建立量值和量值群組</span><span class="sxs-lookup"><span data-stu-id="1e5b0-116">Create Measures and Measure Groups in Multidimensional Models</span></span>](create-measures-and-measure-groups-in-multidimensional-models.md)|  
|<span data-ttu-id="1e5b0-117">資料分割</span><span class="sxs-lookup"><span data-stu-id="1e5b0-117">Partitions</span></span>|[<span data-ttu-id="1e5b0-118">多維度模型中的分割區</span><span class="sxs-lookup"><span data-stu-id="1e5b0-118">Partitions in Multidimensional Models</span></span>](partitions-in-multidimensional-models.md)|  
|<span data-ttu-id="1e5b0-119">檢視方塊</span><span class="sxs-lookup"><span data-stu-id="1e5b0-119">Perspectives</span></span>|[<span data-ttu-id="1e5b0-120">多維度模型中的檢視方塊</span><span class="sxs-lookup"><span data-stu-id="1e5b0-120">Perspectives in Multidimensional Models</span></span>](perspectives-in-multidimensional-models.md)|  
|<span data-ttu-id="1e5b0-121">階層</span><span class="sxs-lookup"><span data-stu-id="1e5b0-121">Hierarchies</span></span>|[<span data-ttu-id="1e5b0-122">建立使用者定義階層</span><span class="sxs-lookup"><span data-stu-id="1e5b0-122">Create User-Defined Hierarchies</span></span>](user-defined-hierarchies-create.md)|  
|<span data-ttu-id="1e5b0-123">[動作]</span><span class="sxs-lookup"><span data-stu-id="1e5b0-123">Actions</span></span>|[<span data-ttu-id="1e5b0-124">多維度模型中的動作</span><span class="sxs-lookup"><span data-stu-id="1e5b0-124">Actions in Multidimensional Models</span></span>](actions-in-multidimensional-models.md)|  
|<span data-ttu-id="1e5b0-125">關鍵效能指標 (KPI)</span><span class="sxs-lookup"><span data-stu-id="1e5b0-125">Key Performance Indicators (KPI)</span></span>|[<span data-ttu-id="1e5b0-126">多維度模型中的關鍵效能指標 &#40;KPI&#41;</span><span class="sxs-lookup"><span data-stu-id="1e5b0-126">Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models</span></span>](key-performance-indicators-kpis-in-multidimensional-models.md)|  
|<span data-ttu-id="1e5b0-127">計算</span><span class="sxs-lookup"><span data-stu-id="1e5b0-127">Calculations</span></span>|[<span data-ttu-id="1e5b0-128">多維度模型中的計算</span><span class="sxs-lookup"><span data-stu-id="1e5b0-128">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)|  
|<span data-ttu-id="1e5b0-129">翻譯</span><span class="sxs-lookup"><span data-stu-id="1e5b0-129">Translations</span></span>|[<span data-ttu-id="1e5b0-130">多維度模型中的翻譯</span><span class="sxs-lookup"><span data-stu-id="1e5b0-130">Translations in Multidimensional Models</span></span>](translations-in-multidimensional-models-analysis-services.md)|  
  
## <a name="related-tasks"></a><span data-ttu-id="1e5b0-131">相關工作</span><span class="sxs-lookup"><span data-stu-id="1e5b0-131">Related Tasks</span></span>  
  
|<span data-ttu-id="1e5b0-132">主題</span><span class="sxs-lookup"><span data-stu-id="1e5b0-132">Topic</span></span>|<span data-ttu-id="1e5b0-133">描述</span><span class="sxs-lookup"><span data-stu-id="1e5b0-133">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="1e5b0-134">使用 Cube 精靈來建立 Cube</span><span class="sxs-lookup"><span data-stu-id="1e5b0-134">Create a Cube Using the Cube Wizard</span></span>](create-a-cube-using-the-cube-wizard.md)|<span data-ttu-id="1e5b0-135">描述如何使用 Cube 精靈來定義 Cube、維度、維度屬性和使用者自訂階層。</span><span class="sxs-lookup"><span data-stu-id="1e5b0-135">Describes how to use the Cube Wizard to define a cube, dimensions, dimension attributes, and user-defined hierarchies.</span></span>|  
|[<span data-ttu-id="1e5b0-136">在多維度模型中建立量值和量值群組</span><span class="sxs-lookup"><span data-stu-id="1e5b0-136">Create Measures and Measure Groups in Multidimensional Models</span></span>](create-measures-and-measure-groups-in-multidimensional-models.md)|<span data-ttu-id="1e5b0-137">描述如何定義量值群組。</span><span class="sxs-lookup"><span data-stu-id="1e5b0-137">Describes how to define measure groups.</span></span>|  
|[<span data-ttu-id="1e5b0-138">多維度模型中的計算</span><span class="sxs-lookup"><span data-stu-id="1e5b0-138">Calculations in Multidimensional Models</span></span>](calculations-in-multidimensional-models.md)|<span data-ttu-id="1e5b0-139">描述如何定義及設定 MDX 指令碼中的計算。</span><span class="sxs-lookup"><span data-stu-id="1e5b0-139">Describes how to define and configure a calculation in an MDX script.</span></span>|  
|[<span data-ttu-id="1e5b0-140">多維度模型中的動作</span><span class="sxs-lookup"><span data-stu-id="1e5b0-140">Actions in Multidimensional Models</span></span>](actions-in-multidimensional-models.md)|<span data-ttu-id="1e5b0-141">描述如何定義及設定動作。</span><span class="sxs-lookup"><span data-stu-id="1e5b0-141">Describes how to define and configure an action.</span></span>|  
|[<span data-ttu-id="1e5b0-142">多維度模型中的檢視方塊</span><span class="sxs-lookup"><span data-stu-id="1e5b0-142">Perspectives in Multidimensional Models</span></span>](perspectives-in-multidimensional-models.md)|<span data-ttu-id="1e5b0-143">描述如何定義及設定檢視方塊。</span><span class="sxs-lookup"><span data-stu-id="1e5b0-143">Describes how to define and configure a perspective.</span></span>|  
|[<span data-ttu-id="1e5b0-144">定義預存程式</span><span class="sxs-lookup"><span data-stu-id="1e5b0-144">Defining Stored Procedures</span></span>](../multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)|<span data-ttu-id="1e5b0-145">描述如何使用預存程序。</span><span class="sxs-lookup"><span data-stu-id="1e5b0-145">Describes how to work with stored procedures.</span></span>|  
  
  
