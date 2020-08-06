---
title: 第7課：定義 (Kpi) 的關鍵效能指標 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 36d53770-294f-43ab-8850-15d5351ff60c
author: minewiskan
ms.author: owend
ms.openlocfilehash: 87df6fd91a66505f124144cafd9a44c6e5e70e85
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698728"
---
# <a name="lesson-7-defining-key-performance-indicators-kpis"></a><span data-ttu-id="3526c-102">第 7 課：定義關鍵效能指標 (KPI)</span><span class="sxs-lookup"><span data-stu-id="3526c-102">Lesson 7: Defining Key Performance Indicators (KPIs)</span></span>
  <span data-ttu-id="3526c-103">在這一課，您將學會定義 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 專案中的關鍵效能指標 (KPI)。</span><span class="sxs-lookup"><span data-stu-id="3526c-103">In this lesson, you learn to define Key Performance Indicators (KPIs) in your [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] project.</span></span> <span data-ttu-id="3526c-104">KPI 會提供一個架構，讓您定義伺服器端的計算以度量您的生意，另外，它們也會將結果資訊的顯示方式標準化。</span><span class="sxs-lookup"><span data-stu-id="3526c-104">KPIs provide a framework for defining server-side calculations that measure your business, and they standardize how the resulting information is displayed.</span></span> <span data-ttu-id="3526c-105">KPI 可以透過資料存取 API 和 [!INCLUDE[msCoName](../includes/msconame-md.md)] 工具以及協力廠商工具，顯示在報表、入口網站以及儀表板上。</span><span class="sxs-lookup"><span data-stu-id="3526c-105">KPIs can be displayed in reports, portals, and dashboards, through data access APIs, and through [!INCLUDE[msCoName](../includes/msconame-md.md)] tools and third-party tools.</span></span> <span data-ttu-id="3526c-106">KPI 大約屬於一般量值和其他多維度運算式 (MDX) 運算式的中繼資料包裝函式。</span><span class="sxs-lookup"><span data-stu-id="3526c-106">KPIs are metadata wrappers around regular measures and other Multidimensional Expressions (MDX) expressions.</span></span> <span data-ttu-id="3526c-107">如需詳細資訊，請參閱 [多維度模型中的關鍵效能指標 &#40;KPI&#41;](multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)。</span><span class="sxs-lookup"><span data-stu-id="3526c-107">For more information, see [Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models](multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3526c-108">此教學課程中，所有課程已完成的專案都可在線上取得。</span><span class="sxs-lookup"><span data-stu-id="3526c-108">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="3526c-109">您可以從先前的課程中使用已完成的專案做為起點，向前跳到任何課程。</span><span class="sxs-lookup"><span data-stu-id="3526c-109">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="3526c-110">[按一下這裡](https://go.microsoft.com/fwlink/?LinkID=221866) ，下載此教學課程隨附的範例專案。</span><span class="sxs-lookup"><span data-stu-id="3526c-110">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="3526c-111">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="3526c-111">This lesson contains the following task:</span></span>  
  
 [<span data-ttu-id="3526c-112">定義和瀏覽 KPI</span><span class="sxs-lookup"><span data-stu-id="3526c-112">Defining and Browsing KPIs</span></span>](lesson-7-1-defining-and-browsing-kpis.md)  
 <span data-ttu-id="3526c-113">在這項工作中，您會在 [表單] 檢視定義 KPI，然後切換到 [瀏覽器] 檢視，以 KPI 瀏覽 Cube 資料。</span><span class="sxs-lookup"><span data-stu-id="3526c-113">In this task, you define KPIs in the Form view and then switch to the Browser view to browse the cube data by using the KPIs.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="3526c-114">下一課</span><span class="sxs-lookup"><span data-stu-id="3526c-114">Next Lesson</span></span>  
 [<span data-ttu-id="3526c-115">第8課：定義動作</span><span class="sxs-lookup"><span data-stu-id="3526c-115">Lesson 8: Defining Actions</span></span>](lesson-8-defining-actions.md)  
  
## <a name="see-also"></a><span data-ttu-id="3526c-116">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3526c-116">See Also</span></span>  
 <span data-ttu-id="3526c-117">[Analysis Services 教學課程案例](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="3526c-117">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="3526c-118">[多維度模型化 &#40;的艾德作品教學課程&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="3526c-118">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 [<span data-ttu-id="3526c-119">多維度模型中的關鍵效能指標 &#40;KPI&#41;</span><span class="sxs-lookup"><span data-stu-id="3526c-119">Key Performance Indicators &#40;KPIs&#41; in Multidimensional Models</span></span>](multidimensional-models/key-performance-indicators-kpis-in-multidimensional-models.md)  
  
  
