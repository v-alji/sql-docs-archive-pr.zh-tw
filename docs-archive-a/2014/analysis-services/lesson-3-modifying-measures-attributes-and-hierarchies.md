---
title: 第3課：修改量值、屬性和階層 |Microsoft Docs
ms.custom: ''
ms.date: 06/14/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 17d243cb-9bfb-43d7-8e6f-4d601fd62150
author: minewiskan
ms.author: owend
ms.openlocfilehash: c410136540a0ba85d50fbabc8b2d3c52be1823f2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597429"
---
# <a name="lesson-3-modifying-measures-attributes-and-hierarchies"></a><span data-ttu-id="f2b53-102">第 3 課：修改量值、屬性和階層</span><span class="sxs-lookup"><span data-stu-id="f2b53-102">Lesson 3: Modifying Measures, Attributes and Hierarchies</span></span>
  <span data-ttu-id="f2b53-103">定義初始 Cube 之後，您就可以開始改善 Cube 的效益與易懂性。</span><span class="sxs-lookup"><span data-stu-id="f2b53-103">After defining your initial cube, you are ready to improve the usefulness and friendliness of the cube.</span></span> <span data-ttu-id="f2b53-104">方法是，在各種層級加入支援導覽和彙總的階層、將格式套用至特定量值，以及定義計算和關聯性。</span><span class="sxs-lookup"><span data-stu-id="f2b53-104">You can do this by adding hierarchies that support navigation and aggregation at various levels, by applying formats to specific measure, and by defining calculations and relationships.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f2b53-105">此教學課程中，所有課程已完成的專案都可在線上取得。</span><span class="sxs-lookup"><span data-stu-id="f2b53-105">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="f2b53-106">您可以從先前的課程中使用已完成的專案做為起點，向前跳到任何課程。</span><span class="sxs-lookup"><span data-stu-id="f2b53-106">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="f2b53-107">[按一下這裡](https://go.microsoft.com/fwlink/?LinkID=221866) ，下載此教學課程隨附的範例專案。</span><span class="sxs-lookup"><span data-stu-id="f2b53-107">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="f2b53-108">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="f2b53-108">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="f2b53-109">修改量值</span><span class="sxs-lookup"><span data-stu-id="f2b53-109">Modifying Measures</span></span>](lesson-3-1-modifying-measures.md)  
 <span data-ttu-id="f2b53-110">在這項工作中，您在 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程 Cube 中指定貨幣和百分比量值的格式化屬性。</span><span class="sxs-lookup"><span data-stu-id="f2b53-110">In this task, you specify formatting properties for the currency and percentage measures in the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial cube.</span></span>  
  
 [<span data-ttu-id="f2b53-111">修改客戶維度</span><span class="sxs-lookup"><span data-stu-id="f2b53-111">Modifying the Customer Dimension</span></span>](lesson-3-2-modifying-the-customer-dimension.md)  
 <span data-ttu-id="f2b53-112">在這項工作中，您會定義使用者階層、建立具名計算、修改要使用具名計算的屬性，以及將屬性和使用者階層分組放入顯示資料夾。</span><span class="sxs-lookup"><span data-stu-id="f2b53-112">In this task, you define a user hierarchy, create named calculations, modify attributes to use named calculations, and group attributes and user hierarchies into display folders.</span></span>  
  
 [<span data-ttu-id="f2b53-113">修改產品維度</span><span class="sxs-lookup"><span data-stu-id="f2b53-113">Modifying the Product Dimension</span></span>](lesson-3-3-modifying-the-product-dimension.md)  
 <span data-ttu-id="f2b53-114">在這項工作中，您會定義使用者階層、建立具名計算、定義「全部」成員名稱，以及定義顯示資料夾。</span><span class="sxs-lookup"><span data-stu-id="f2b53-114">In this task, you define a user hierarchy, create named calculations, define the All member name, and define display folders.</span></span>  
  
 [<span data-ttu-id="f2b53-115">修改日期維度</span><span class="sxs-lookup"><span data-stu-id="f2b53-115">Modifying the Date Dimension</span></span>](lesson-3-4-modifying-the-date-dimension.md)  
 <span data-ttu-id="f2b53-116">在這項工作中，您會定義使用者階層、修改屬性成員名稱，以及使用複合索引鍵來指定唯一屬性成員。</span><span class="sxs-lookup"><span data-stu-id="f2b53-116">In this task, you define a user hierarchy, modify attribute member names, and use composite keys to specify unique attribute members.</span></span>  
  
 [<span data-ttu-id="f2b53-117">瀏覽已部署的 Cube</span><span class="sxs-lookup"><span data-stu-id="f2b53-117">Browsing the Deployed Cube</span></span>](lesson-3-5-browsing-the-deployed-cube.md)  
 <span data-ttu-id="f2b53-118">在這項工作中，您會使用 Cube 設計師的瀏覽器來瀏覽 Cube 資料。</span><span class="sxs-lookup"><span data-stu-id="f2b53-118">In this task, you browse cube data by using the browser in Cube Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2b53-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f2b53-119">See Also</span></span>  
 <span data-ttu-id="f2b53-120">[Analysis Services 教學課程案例](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="f2b53-120">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 [<span data-ttu-id="f2b53-121">多維度模型化 &#40;Adventure Works 教學課程&#41;</span><span class="sxs-lookup"><span data-stu-id="f2b53-121">Multidimensional Modeling &#40;Adventure Works Tutorial&#41;</span></span>](multidimensional-modeling-adventure-works-tutorial.md)  
  
  
