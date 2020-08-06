---
title: 多維度模型化 (的艾德作品教學課程) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- tutorials [Analysis Services]
- Analysis Services, tutorials
ms.assetid: db55e226-601a-4026-8651-573195555a59
author: minewiskan
ms.author: owend
ms.openlocfilehash: cd2e8f856d36cab045e6cbc4d34f7cfeffac3c3c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598034"
---
# <a name="multidimensional-modeling-adventure-works-tutorial"></a><span data-ttu-id="01e9d-102">多維度模型化 (Adventure Works 教學課程)</span><span class="sxs-lookup"><span data-stu-id="01e9d-102">Multidimensional Modeling (Adventure Works Tutorial)</span></span>
  <span data-ttu-id="01e9d-103">歡迎使用 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程。</span><span class="sxs-lookup"><span data-stu-id="01e9d-103">Welcome to the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial.</span></span> <span data-ttu-id="01e9d-104">這個教學課程描述如何使用 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] 來開發和部署 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案，所有範例都使用虛構公司 [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="01e9d-104">This tutorial describes how to use [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] to develop and deploy an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, using the fictitious company [!INCLUDE[ssSampleDBCoFull](../includes/sssampledbcofull-md.md)] for all examples.</span></span>  
  
## <a name="what-you-will-learn"></a><span data-ttu-id="01e9d-105">學習內容</span><span class="sxs-lookup"><span data-stu-id="01e9d-105">What You Will Learn</span></span>  
 <span data-ttu-id="01e9d-106">在本教學課程中，您將學會下列作業：</span><span class="sxs-lookup"><span data-stu-id="01e9d-106">In this tutorial, you will learn the following:</span></span>  
  
-   <span data-ttu-id="01e9d-107">如何在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 的 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]專案中定義資料來源、資料來源檢視、維度、屬性、屬性關聯性、階層和 Cube。</span><span class="sxs-lookup"><span data-stu-id="01e9d-107">How to define data sources, data source views, dimensions, attributes, attribute relationships, hierarchies, and cubes in an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project within [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)].</span></span>  
  
-   <span data-ttu-id="01e9d-108">如何透過將 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案部署至 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]執行個體，檢視 Cube 和維度資料，以及如何處理已部署的物件，以便使用基礎資料來源中的資料擴展這些物件。</span><span class="sxs-lookup"><span data-stu-id="01e9d-108">How to view cube and dimension data by deploying the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project to an instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], and how to then process the deployed objects to populate them with data from the underlying data source.</span></span>  
  
-   <span data-ttu-id="01e9d-109">如何在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案中修改量值、維度、階層、屬性和量值群組，以及如何將累加變更部署到開發伺服器上已部署的 Cube。</span><span class="sxs-lookup"><span data-stu-id="01e9d-109">How to modify the measures, dimensions, hierarchies, attributes, and measure groups in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, and how to then deploy the incremental changes to the deployed cube on the development server.</span></span>  
  
-   <span data-ttu-id="01e9d-110">如何在 Cube 內定義計算、關鍵效能指標 (KPI)、動作、檢視方塊、翻譯和安全性角色。</span><span class="sxs-lookup"><span data-stu-id="01e9d-110">How to define calculations, Key Performance Indicators (KPIs), actions, perspectives, translations, and security roles within a cube.</span></span>  
  
 <span data-ttu-id="01e9d-111">案例描述隨附此教學課程，讓您可以更了解這些課程的內容。</span><span class="sxs-lookup"><span data-stu-id="01e9d-111">A scenario description accompanies this tutorial so that you can better understand the context for these lessons.</span></span> <span data-ttu-id="01e9d-112">如需詳細資訊，請參閱＜ [Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md)＞。</span><span class="sxs-lookup"><span data-stu-id="01e9d-112">For more information, see [Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="01e9d-113">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="01e9d-113">Prerequisites</span></span>  
 <span data-ttu-id="01e9d-114">若要完成這個教學課程的所有課程，您將需要範例資料、範例專案檔及軟體。</span><span class="sxs-lookup"><span data-stu-id="01e9d-114">You will need sample data, sample project files, and software to complete all of the lessons in this tutorial.</span></span> <span data-ttu-id="01e9d-115">如需如何尋找及安裝這個教學課程之必要條件的指示，請參閱＜ [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md)＞。</span><span class="sxs-lookup"><span data-stu-id="01e9d-115">For instructions on how to find and install the prerequisites for this tutorial, see [Install Sample Data and Projects for the Analysis Services Multidimensional Modeling Tutorial](install-sample-data-and-projects.md).</span></span>  
  
 <span data-ttu-id="01e9d-116">另外還要具備下列權限才能順利完成這個教學課程：</span><span class="sxs-lookup"><span data-stu-id="01e9d-116">Additionally, the following permissions must be in place to successfully complete this tutorial:</span></span>  
  
-   <span data-ttu-id="01e9d-117">您必須是 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 電腦上 Administrators 本機群組的成員，或是 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]執行個體中伺服器管理角色的成員。</span><span class="sxs-lookup"><span data-stu-id="01e9d-117">You must be a member of the Administrators local group on the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] computer or be a member of the server administration role in the instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="01e9d-118">您必須具有 **AdventureWorksDW2012** 範例資料庫的「讀取」權限。</span><span class="sxs-lookup"><span data-stu-id="01e9d-118">You must have Read permissions in the **AdventureWorksDW2012** sample database.</span></span> <span data-ttu-id="01e9d-119">這個範例資料庫對 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] 版本有效。</span><span class="sxs-lookup"><span data-stu-id="01e9d-119">This sample database is valid for the [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] release.</span></span>  
  
## <a name="lessons"></a><span data-ttu-id="01e9d-120">課程</span><span class="sxs-lookup"><span data-stu-id="01e9d-120">Lessons</span></span>  
 <span data-ttu-id="01e9d-121">這個教學課程包括下列課程。</span><span class="sxs-lookup"><span data-stu-id="01e9d-121">This tutorial includes the following lessons.</span></span>  
  
|<span data-ttu-id="01e9d-122">課程</span><span class="sxs-lookup"><span data-stu-id="01e9d-122">Lesson</span></span>|<span data-ttu-id="01e9d-123">預估完成時間</span><span class="sxs-lookup"><span data-stu-id="01e9d-123">Estimated time to complete</span></span>|  
|------------|--------------------------------|  
|[<span data-ttu-id="01e9d-124">第1課：在 Analysis Services 專案中定義資料來源視圖</span><span class="sxs-lookup"><span data-stu-id="01e9d-124">Lesson 1: Defining a Data Source View within an Analysis Services Project</span></span>](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md)|<span data-ttu-id="01e9d-125">15 分鐘</span><span class="sxs-lookup"><span data-stu-id="01e9d-125">15 minutes</span></span>|  
|[<span data-ttu-id="01e9d-126">第2課：定義和部署 Cube</span><span class="sxs-lookup"><span data-stu-id="01e9d-126">Lesson 2: Defining and Deploying a Cube</span></span>](lesson-2-defining-and-deploying-a-cube.md)|<span data-ttu-id="01e9d-127">30 分鐘</span><span class="sxs-lookup"><span data-stu-id="01e9d-127">30 minutes</span></span>|  
|[<span data-ttu-id="01e9d-128">第3課：修改量值、屬性和階層</span><span class="sxs-lookup"><span data-stu-id="01e9d-128">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>](lesson-3-modifying-measures-attributes-and-hierarchies.md)|<span data-ttu-id="01e9d-129">45 分鐘</span><span class="sxs-lookup"><span data-stu-id="01e9d-129">45 minutes</span></span>|  
|[<span data-ttu-id="01e9d-130">第4課：定義 Advanced 屬性和維度屬性</span><span class="sxs-lookup"><span data-stu-id="01e9d-130">Lesson 4: Defining Advanced Attribute and Dimension Properties</span></span>](lesson-4-defining-advanced-attribute-and-dimension-properties.md)|<span data-ttu-id="01e9d-131">120 分鐘</span><span class="sxs-lookup"><span data-stu-id="01e9d-131">120 minutes</span></span>|  
|[<span data-ttu-id="01e9d-132">第5課：定義維度和量值群組之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="01e9d-132">Lesson 5: Defining Relationships Between Dimensions and Measure Groups</span></span>](lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)|<span data-ttu-id="01e9d-133">45 分鐘</span><span class="sxs-lookup"><span data-stu-id="01e9d-133">45 minutes</span></span>|  
|[<span data-ttu-id="01e9d-134">第6課：定義計算</span><span class="sxs-lookup"><span data-stu-id="01e9d-134">Lesson 6: Defining Calculations</span></span>](lesson-6-defining-calculations.md)|<span data-ttu-id="01e9d-135">45 分鐘</span><span class="sxs-lookup"><span data-stu-id="01e9d-135">45 minutes</span></span>|  
|[<span data-ttu-id="01e9d-136">第 7 課：定義關鍵效能指標 &#40;KPI&#41;</span><span class="sxs-lookup"><span data-stu-id="01e9d-136">Lesson 7: Defining Key Performance Indicators &#40;KPIs&#41;</span></span>](lesson-7-defining-key-performance-indicators-kpis.md)|<span data-ttu-id="01e9d-137">30 分鐘</span><span class="sxs-lookup"><span data-stu-id="01e9d-137">30 minutes</span></span>|  
|[<span data-ttu-id="01e9d-138">第8課：定義動作</span><span class="sxs-lookup"><span data-stu-id="01e9d-138">Lesson 8: Defining Actions</span></span>](lesson-8-defining-actions.md)|<span data-ttu-id="01e9d-139">30 分鐘</span><span class="sxs-lookup"><span data-stu-id="01e9d-139">30 minutes</span></span>|  
|[<span data-ttu-id="01e9d-140">第9課：定義觀點和翻譯</span><span class="sxs-lookup"><span data-stu-id="01e9d-140">Lesson 9: Defining Perspectives and Translations</span></span>](lesson-9-defining-perspectives-and-translations.md)|<span data-ttu-id="01e9d-141">30 分鐘</span><span class="sxs-lookup"><span data-stu-id="01e9d-141">30 minutes</span></span>|  
|[<span data-ttu-id="01e9d-142">第10課：定義系統管理角色</span><span class="sxs-lookup"><span data-stu-id="01e9d-142">Lesson 10: Defining Administrative Roles</span></span>](lesson-10-defining-administrative-roles.md)|<span data-ttu-id="01e9d-143">15 分鐘</span><span class="sxs-lookup"><span data-stu-id="01e9d-143">15 minutes</span></span>|  
  
> [!NOTE]  
>  <span data-ttu-id="01e9d-144">您將在此教學課程中建立的 Cube 資料庫是簡化的 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多維度模型專案版本，此專案是 Adventure Works 範例資料庫的一部分，可在 codeplex 網站下載。</span><span class="sxs-lookup"><span data-stu-id="01e9d-144">The cube database that you will create in this tutorial is a simplified version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional model project that is part of the Adventure Works sample databases available for download on the codeplex site.</span></span> <span data-ttu-id="01e9d-145">已簡化「艾德作品多維度資料庫」的教學課程版本，將焦點放在您想要立即改善的特定技能。</span><span class="sxs-lookup"><span data-stu-id="01e9d-145">The tutorial version of the Adventure Works multidimensional database is simplified to bring greater focus to the specific skills that you will want to improve right away.</span></span> <span data-ttu-id="01e9d-146">完成此教學課程之後，請考慮自行瀏覽多維度模型專案，以更了解 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多維度模型。</span><span class="sxs-lookup"><span data-stu-id="01e9d-146">After you complete the tutorial, consider exploring the multidimensional model project on your own to further your understanding of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional modeling.</span></span>  
  
## <a name="next-step"></a><span data-ttu-id="01e9d-147">後續步驟</span><span class="sxs-lookup"><span data-stu-id="01e9d-147">Next Step</span></span>  
 <span data-ttu-id="01e9d-148">若要開始本教學課程，請繼續進行第一課： [Lesson 1: Defining a Data Source View within an Analysis Services Project](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md)。</span><span class="sxs-lookup"><span data-stu-id="01e9d-148">To begin the tutorial, continue to the first lesson: [Lesson 1: Defining a Data Source View within an Analysis Services Project](lesson-1-defining-a-data-source-view-within-an-analysis-services-project.md).</span></span>  
  
  
