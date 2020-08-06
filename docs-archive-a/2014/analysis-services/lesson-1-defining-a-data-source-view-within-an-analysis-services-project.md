---
title: 第1課：在 Analysis Services 專案中定義資料來源視圖 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 7d3ffabd-78ae-4204-8323-29949d030c16
author: minewiskan
ms.author: owend
ms.openlocfilehash: 8a3d69225217154e5072d0cd34349a247730ddaf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707966"
---
# <a name="lesson-1-defining-a-data-source-view-within-an-analysis-services-project"></a><span data-ttu-id="1e9da-102">第 1 課：在 Analysis Services 專案內定義資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="1e9da-102">Lesson 1: Defining a Data Source View within an Analysis Services Project</span></span>
  <span data-ttu-id="1e9da-103">要在 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 中設計商業智慧應用程式，先從在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 中建立 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]專案開始。</span><span class="sxs-lookup"><span data-stu-id="1e9da-103">Designing a business intelligence application in [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] starts with creating an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project in [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span> <span data-ttu-id="1e9da-104">在這個專案內，您要定義方案的所有元素，請從資料來源檢視開始。</span><span class="sxs-lookup"><span data-stu-id="1e9da-104">Within this project, you define all the elements of your solution, starting with a data source view.</span></span>  
  
 <span data-ttu-id="1e9da-105">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="1e9da-105">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="1e9da-106">建立 Analysis Services 專案</span><span class="sxs-lookup"><span data-stu-id="1e9da-106">Creating an Analysis Services Project</span></span>](lesson-1-1-creating-an-analysis-services-project.md)  
 <span data-ttu-id="1e9da-107">在這項工作中，您依據 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多維度模型範本建立 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程專案。</span><span class="sxs-lookup"><span data-stu-id="1e9da-107">In this task, you create the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, based on an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] multidimensional model template.</span></span>  
  
 [<span data-ttu-id="1e9da-108">定義資料來源</span><span class="sxs-lookup"><span data-stu-id="1e9da-108">Defining a Data Source</span></span>](lesson-1-2-defining-a-data-source.md)  
 <span data-ttu-id="1e9da-109">在這項工作中，您指定 **AdventureWorksDW2012** 資料庫作為您將在後續課程中定義之 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 維度和 Cube 的資料來源。</span><span class="sxs-lookup"><span data-stu-id="1e9da-109">In this task, you specify the **AdventureWorksDW2012** database as the data source for the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] dimensions and cubes that you will define in subsequent lessons.</span></span>  
  
 [<span data-ttu-id="1e9da-110">定義資料來源檢視</span><span class="sxs-lookup"><span data-stu-id="1e9da-110">Defining a Data Source View</span></span>](lesson-1-3-defining-a-data-source-view.md)  
 <span data-ttu-id="1e9da-111">在這項工作中，您從 **AdventureWorksDW2012** 資料庫選取的資料表中定義中繼資料的單一統一檢視。</span><span class="sxs-lookup"><span data-stu-id="1e9da-111">In this task, you define a single unified view of the metadata from selected tables in the **AdventureWorksDW2012** database.</span></span>  
  
 [<span data-ttu-id="1e9da-112">修改預設資料表名稱</span><span class="sxs-lookup"><span data-stu-id="1e9da-112">Modifying Default Table Names</span></span>](lesson-1-4-modifying-default-table-names.md)  
 <span data-ttu-id="1e9da-113">在這項工作中，您修改資料來源檢視中的資料表名稱，因此您將定義的後續 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 物件名稱會讓使用者更方便使用。</span><span class="sxs-lookup"><span data-stu-id="1e9da-113">In this task, you modify table names in the data source view, so that the names of subsequent [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] objects that you define will be more user-friendly.</span></span>  
  
 <span data-ttu-id="1e9da-114">將您的結果與在這一課中建立的範例專案檔案相比較。</span><span class="sxs-lookup"><span data-stu-id="1e9da-114">Compare your results against a sample project file that was built for this lesson.</span></span> <span data-ttu-id="1e9da-115">如需下載此教學課程隨附之範例專案的詳細資訊，請參閱 CodePlex 之產品範例頁面上的 [SSAS Multidimensional Model Projects for SQL Server 2012](https://go.microsoft.com/fwlink/p/?LinkID=221866) (適用於 SQL Server 2012 的 SSAS 多維度模型專案)。</span><span class="sxs-lookup"><span data-stu-id="1e9da-115">For more information about downloading the sample projects that go with this tutorial, see [SSAS Multidimensional Model Projects for SQL Server 2012](https://go.microsoft.com/fwlink/p/?LinkID=221866) on the product samples page on codeplex.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="1e9da-116">下一課</span><span class="sxs-lookup"><span data-stu-id="1e9da-116">Next Lesson</span></span>  
 [<span data-ttu-id="1e9da-117">第2課：定義和部署 Cube</span><span class="sxs-lookup"><span data-stu-id="1e9da-117">Lesson 2: Defining and Deploying a Cube</span></span>](lesson-2-defining-and-deploying-a-cube.md)  
  
## <a name="see-also"></a><span data-ttu-id="1e9da-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1e9da-118">See Also</span></span>  
 <span data-ttu-id="1e9da-119">[建立 Analysis Services 專案 &#40;SSDT&#41;](multidimensional-models/create-an-analysis-services-project-ssdt.md) </span><span class="sxs-lookup"><span data-stu-id="1e9da-119">[Create an Analysis Services Project &#40;SSDT&#41;](multidimensional-models/create-an-analysis-services-project-ssdt.md) </span></span>  
 <span data-ttu-id="1e9da-120">[&#40;SSAS 多維度&#41;支援的資料來源](multidimensional-models/supported-data-sources-ssas-multidimensional.md) </span><span class="sxs-lookup"><span data-stu-id="1e9da-120">[Data Sources Supported &#40;SSAS Multidimensional&#41;](multidimensional-models/supported-data-sources-ssas-multidimensional.md) </span></span>  
 <span data-ttu-id="1e9da-121">[多維度模型中的資料來源視圖](multidimensional-models/data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="1e9da-121">[Data Source Views in Multidimensional Models](multidimensional-models/data-source-views-in-multidimensional-models.md) </span></span>  
 <span data-ttu-id="1e9da-122">[Analysis Services 教學課程案例](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="1e9da-122">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 [<span data-ttu-id="1e9da-123">多維度模型化 &#40;Adventure Works 教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="1e9da-123">Multidimensional Modeling &#40;Adventure Works Tutorial&#41;</span></span>](multidimensional-modeling-adventure-works-tutorial.md)  
  
  
