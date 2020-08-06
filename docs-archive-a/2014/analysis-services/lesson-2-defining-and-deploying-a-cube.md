---
title: 第2課：定義和部署 Cube |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: bb62e3c9-462f-4ad2-ac8e-92e2f9e9cc28
author: minewiskan
ms.author: owend
ms.openlocfilehash: a2c043920ac646ec4da9eaa2aace4bf6f48e694c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598642"
---
# <a name="lesson-2-defining-and-deploying-a-cube"></a><span data-ttu-id="db75f-102">第 2 課：定義和部署 Cube</span><span class="sxs-lookup"><span data-stu-id="db75f-102">Lesson 2: Defining and Deploying a Cube</span></span>
  <span data-ttu-id="db75f-103">在您的專案中定義資料來源視圖之後 [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ，您就可以開始定義初始 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube。</span><span class="sxs-lookup"><span data-stu-id="db75f-103">After you define a data source view in your [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project, you are ready to define an initial [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube.</span></span>  
  
 <span data-ttu-id="db75f-104">您可以使用 Cube 精靈，在單一行程中定義 Cube 及其維度。</span><span class="sxs-lookup"><span data-stu-id="db75f-104">You can define a cube and its dimensions in a single pass using the Cube Wizard.</span></span> <span data-ttu-id="db75f-105">或者，您也可以定義一或多個維度，然後使用 Cube 精靈來定義使用這些維度的 Cube。</span><span class="sxs-lookup"><span data-stu-id="db75f-105">Alternatively, you can define one or more dimensions and then use the Cube Wizard to define a cube that uses those dimensions.</span></span> <span data-ttu-id="db75f-106">如果您要設計複雜的方案，通常會從定義維度開始。</span><span class="sxs-lookup"><span data-stu-id="db75f-106">If you are designing a complex solution, you generally start by defining the dimensions.</span></span> <span data-ttu-id="db75f-107">如需詳細資訊，請參閱 [多維度模型中的維度](multidimensional-models/dimensions-in-multidimensional-models.md) 或 [多維度模型中的 Cube](multidimensional-models/cubes-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="db75f-107">For more information, see [Dimensions in Multidimensional Models](multidimensional-models/dimensions-in-multidimensional-models.md) or [Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="db75f-108">此教學課程中，所有課程已完成的專案都可在線上取得。</span><span class="sxs-lookup"><span data-stu-id="db75f-108">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="db75f-109">您可以從先前的課程中使用已完成的專案做為起點，向前跳到任何課程。</span><span class="sxs-lookup"><span data-stu-id="db75f-109">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="db75f-110">[按一下這裡](https://go.microsoft.com/fwlink/?LinkID=221866) ，下載此教學課程隨附的範例專案。</span><span class="sxs-lookup"><span data-stu-id="db75f-110">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="db75f-111">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="db75f-111">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="db75f-112">定義維度</span><span class="sxs-lookup"><span data-stu-id="db75f-112">Defining a Dimension</span></span>](lesson-2-1-defining-a-dimension.md)  
 <span data-ttu-id="db75f-113">在這項工作中，您會使用維度精靈來定義維度。</span><span class="sxs-lookup"><span data-stu-id="db75f-113">In this task, you use the Dimension Wizard to define a dimension.</span></span>  
  
 [<span data-ttu-id="db75f-114">定義 Cube</span><span class="sxs-lookup"><span data-stu-id="db75f-114">Defining a Cube</span></span>](lesson-2-2-defining-a-cube.md)  
 <span data-ttu-id="db75f-115">在這項工作中，您會使用 Cube 精靈來定義初始 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Cube。</span><span class="sxs-lookup"><span data-stu-id="db75f-115">In this task, you use the Cube Wizard to define an initial [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] cube.</span></span>  
  
 [<span data-ttu-id="db75f-116">將屬性加入至維度</span><span class="sxs-lookup"><span data-stu-id="db75f-116">Adding Attributes to Dimensions</span></span>](lesson-2-3-adding-attributes-to-dimensions.md)  
 <span data-ttu-id="db75f-117">在這項工作中，您會將屬性加入至已建立的維度。</span><span class="sxs-lookup"><span data-stu-id="db75f-117">In this task, you add attributes to the dimensions that you created.</span></span>  
  
 [<span data-ttu-id="db75f-118">檢閱 Cube 和維度屬性</span><span class="sxs-lookup"><span data-stu-id="db75f-118">Reviewing Cube and Dimension Properties</span></span>](lesson-2-4-reviewing-cube-and-dimension-properties.md)  
 <span data-ttu-id="db75f-119">在這項工作中，您會檢閱使用 Cube 精靈所定義之 Cube 的結構。</span><span class="sxs-lookup"><span data-stu-id="db75f-119">In this task, you review the structure of the cube that you defined by using the Cube Wizard.</span></span>  
  
 [<span data-ttu-id="db75f-120">部署 Analysis Services 專案</span><span class="sxs-lookup"><span data-stu-id="db75f-120">Deploying an Analysis Services Project</span></span>](lesson-2-5-deploying-an-analysis-services-project.md)  
 <span data-ttu-id="db75f-121">在這項工作中，您將 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案部署到 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]的本機執行個體，來了解特定部署屬性。</span><span class="sxs-lookup"><span data-stu-id="db75f-121">In this task, you deploy the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project to your local instance of [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], and learn about certain deployment properties.</span></span>  
  
 [<span data-ttu-id="db75f-122">瀏覽 Cube</span><span class="sxs-lookup"><span data-stu-id="db75f-122">Browsing the Cube</span></span>](lesson-2-6-browsing-the-cube.md)  
 <span data-ttu-id="db75f-123">在此工作中，您會使用 Excel 或 MDX 查詢設計工具來瀏覽 Cube 和維度資料。</span><span class="sxs-lookup"><span data-stu-id="db75f-123">In this task, you browse the cube and dimension data by using Excel or the MDX query designer.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="db75f-124">下一課</span><span class="sxs-lookup"><span data-stu-id="db75f-124">Next Lesson</span></span>  
 [<span data-ttu-id="db75f-125">第3課：修改量值、屬性和階層</span><span class="sxs-lookup"><span data-stu-id="db75f-125">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>](lesson-3-modifying-measures-attributes-and-hierarchies.md)  
  
## <a name="see-also"></a><span data-ttu-id="db75f-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="db75f-126">See Also</span></span>  
 <span data-ttu-id="db75f-127">[Analysis Services 教學課程案例](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="db75f-127">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="db75f-128">[多維度模型化 &#40;的艾德作品教學課程&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="db75f-128">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 <span data-ttu-id="db75f-129">[多維度模型中的維度](multidimensional-models/dimensions-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="db75f-129">[Dimensions in Multidimensional Models](multidimensional-models/dimensions-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="db75f-130">[多維度模型中的 cube](multidimensional-models/cubes-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="db75f-130">[Cubes in Multidimensional Models](multidimensional-models/cubes-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="db75f-131">[設定 Analysis Services 專案屬性 &#40;SSDT&#41;](multidimensional-models/configure-analysis-services-project-properties-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="db75f-131">[Configure Analysis Services Project Properties &#40;SSDT&#41;](multidimensional-models/configure-analysis-services-project-properties-ssdt.md) </span></span>  
 <span data-ttu-id="db75f-132">[組建 Analysis Services 專案 &#40;SSDT&#41;](multidimensional-models/build-analysis-services-projects-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="db75f-132">[Build Analysis Services Projects &#40;SSDT&#41;](multidimensional-models/build-analysis-services-projects-ssdt.md) </span></span>  
 [<span data-ttu-id="db75f-133">部署 Analysis Services 專案 &#40;SSDT&#41;</span><span class="sxs-lookup"><span data-stu-id="db75f-133">Deploy Analysis Services Projects &#40;SSDT&#41;</span></span>](multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
  
  
