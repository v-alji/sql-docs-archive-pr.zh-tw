---
title: 第5課：定義維度和量值群組之間的關聯性 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 31aeb271-47a1-433b-a8a5-120bcb4584d7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 6dbdf20e64e3cd8adc751b69122a380d7b3b3648
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594794"
---
# <a name="lesson-5-defining-relationships-between-dimensions-and-measure-groups"></a><span data-ttu-id="92050-102">第 5 課：在維度和量值群組之間定義關聯性</span><span class="sxs-lookup"><span data-stu-id="92050-102">Lesson 5: Defining Relationships Between Dimensions and Measure Groups</span></span>
  <span data-ttu-id="92050-103">在這個教學課程的前面課程中，您已了解加入至 Cube 的資料庫維度可做為一或多個 Cube 維度的基礎。</span><span class="sxs-lookup"><span data-stu-id="92050-103">In the previous lessons in this tutorial, you learned that database dimensions added to a cube can be used as the basis for one or more cube dimensions.</span></span> <span data-ttu-id="92050-104">在這一課，您將學習如何在 Cube 維度和量值群組之間定義不同類型的關聯性，以及指定這些關聯性的屬性。</span><span class="sxs-lookup"><span data-stu-id="92050-104">In this lesson, you learn to define different types of relationships between cube dimensions and measure groups, and to specify the properties of these relationships.</span></span>  
  
 <span data-ttu-id="92050-105">如需詳細資訊，請參閱 [維度關聯性](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)。</span><span class="sxs-lookup"><span data-stu-id="92050-105">For more information, see [Dimension Relationships](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="92050-106">此教學課程中，所有課程已完成的專案都可在線上取得。</span><span class="sxs-lookup"><span data-stu-id="92050-106">Completed projects for all of the lessons in this tutorial are available online.</span></span> <span data-ttu-id="92050-107">您可以從先前的課程中使用已完成的專案做為起點，向前跳到任何課程。</span><span class="sxs-lookup"><span data-stu-id="92050-107">You can jump ahead to any lesson by using the completed project from the previous lesson as a starting point.</span></span> <span data-ttu-id="92050-108">[按一下這裡](https://go.microsoft.com/fwlink/?LinkID=221866) ，下載此教學課程隨附的範例專案。</span><span class="sxs-lookup"><span data-stu-id="92050-108">[Click here](https://go.microsoft.com/fwlink/?LinkID=221866) to download the sample projects that go with this tutorial.</span></span>  
  
 <span data-ttu-id="92050-109">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="92050-109">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="92050-110">定義參考關聯性</span><span class="sxs-lookup"><span data-stu-id="92050-110">Defining a Referenced Relationship</span></span>](lesson-5-1-defining-a-referenced-relationship.md)  
 <span data-ttu-id="92050-111">在這項工作中，您將瞭解如何透過直接透過主鍵-外鍵關聯性連結的維度，將維度連結到事實資料表。</span><span class="sxs-lookup"><span data-stu-id="92050-111">In this task, you learn to link a dimension to a fact table indirectly through a dimension that is linked directly through a primary key-foreign key relationship.</span></span>  
  
 [<span data-ttu-id="92050-112">定義事實關聯性</span><span class="sxs-lookup"><span data-stu-id="92050-112">Defining a Fact Relationship</span></span>](lesson-5-2-defining-a-fact-relationship.md)  
 <span data-ttu-id="92050-113">在這項工作中，您學會如何依據事實資料表中的資料來定義維度，以及定義維度關聯性做為事實關聯性。</span><span class="sxs-lookup"><span data-stu-id="92050-113">In this task, you learn to define a dimension based on data in the fact table, and to define the dimension relationship as a fact relationship.</span></span>  
  
 [<span data-ttu-id="92050-114">定義多對多關聯性</span><span class="sxs-lookup"><span data-stu-id="92050-114">Defining a Many-to-Many Relationship</span></span>](lesson-5-3-defining-a-many-to-many-relationship.md)  
 <span data-ttu-id="92050-115">在這項工作中，您學會如何透過維度資料表與事實資料表之間的多對多關聯性定義，使事實與多個維度成員相關聯。</span><span class="sxs-lookup"><span data-stu-id="92050-115">In this task, you learn to relate a fact to multiple dimension members through the definition of a many-to-many relationship between dimension tables and fact tables.</span></span>  
  
 [<span data-ttu-id="92050-116">在量值群組內定義維度資料粒度</span><span class="sxs-lookup"><span data-stu-id="92050-116">Defining Dimension Granularity within a Measure Group</span></span>](lesson-5-4-defining-dimension-granularity-within-a-measure-group.md)  
 <span data-ttu-id="92050-117">在這項工作中，您學會如何為特定量值群組修改維度的資料粒度。</span><span class="sxs-lookup"><span data-stu-id="92050-117">In this task, you learn to modify the granularity of a dimension for a specific measure group.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="92050-118">下一課</span><span class="sxs-lookup"><span data-stu-id="92050-118">Next Lesson</span></span>  
 [<span data-ttu-id="92050-119">第6課：定義計算</span><span class="sxs-lookup"><span data-stu-id="92050-119">Lesson 6: Defining Calculations</span></span>](lesson-6-defining-calculations.md)  
  
## <a name="see-also"></a><span data-ttu-id="92050-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="92050-120">See Also</span></span>  
 <span data-ttu-id="92050-121">[Analysis Services 教學課程案例](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="92050-121">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="92050-122">[多維度模型化 &#40;的艾德作品教學課程&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="92050-122">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 [<span data-ttu-id="92050-123">維度關聯性</span><span class="sxs-lookup"><span data-stu-id="92050-123">Dimension Relationships</span></span>](multidimensional-models-olap-logical-cube-objects/dimension-relationships.md)  
  
  
