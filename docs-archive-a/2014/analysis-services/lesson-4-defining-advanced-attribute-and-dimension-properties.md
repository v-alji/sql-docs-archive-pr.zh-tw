---
title: 第4課：定義 Advanced 屬性和維度屬性 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 0e86b9be-e47d-4bb4-87eb-136ff3a61aef
author: minewiskan
ms.author: owend
ms.openlocfilehash: deb2d9c40ad5024f6cc4ba6e9148df41a168c6e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703386"
---
# <a name="lesson-4-defining-advanced-attribute-and-dimension-properties"></a><span data-ttu-id="20c1a-102">第 4 課：定義進階屬性和維度屬性</span><span class="sxs-lookup"><span data-stu-id="20c1a-102">Lesson 4: Defining Advanced Attribute and Dimension Properties</span></span>
  <span data-ttu-id="20c1a-103">在這一課，您將會學會如何使用某些屬性 (Attribute) 的進階屬性 (Property)、屬性 (Attribute) 階層和維度屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="20c1a-103">In this lesson, you will learn how to use some of the advanced properties of attributes, attribute hierarchies, and dimension properties.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20c1a-104">這一課是以您在本教學課程前 3 課所完成之 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程專案的增強型版本為基礎。</span><span class="sxs-lookup"><span data-stu-id="20c1a-104">This lesson is based on an enhanced version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project that you completed in the first three lessons of this tutorial.</span></span> <span data-ttu-id="20c1a-105">這一課的第一項工作描述要到何處尋找課程所需使用的適當範例專案，以及這個專案與您在前 3 課所建立專案之間的差異。</span><span class="sxs-lookup"><span data-stu-id="20c1a-105">The first task in this lesson describes where to locate the appropriate sample project to use for the lesson, and the difference between this project and the project that you created in the first three lessons.</span></span>  
  
 <span data-ttu-id="20c1a-106">這一課包含下列工作：</span><span class="sxs-lookup"><span data-stu-id="20c1a-106">This lesson contains the following tasks:</span></span>  
  
 [<span data-ttu-id="20c1a-107">使用 Analysis Services 教學課程專案的已修改版本</span><span class="sxs-lookup"><span data-stu-id="20c1a-107">Using a Modified Version of the Analysis Services Tutorial Project</span></span>](lesson-4-1-using-a-modified-version-of-the-analysis-services-tutorial-project.md)  
 <span data-ttu-id="20c1a-108">在這項工作中，您會開啟、檢閱及部署「 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 教學課程」專案的修改版本，其中具有多個量值群組和其他維度。</span><span class="sxs-lookup"><span data-stu-id="20c1a-108">In this task, you open, review, and deploy a modified version of the [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial project, which has multiple measure groups and additional dimensions.</span></span>  
  
 [<span data-ttu-id="20c1a-109">定義父子式階層中父屬性 (Attribute) 的屬性 (Property)</span><span class="sxs-lookup"><span data-stu-id="20c1a-109">Defining Parent Attribute Properties in a Parent-Child Hierarchy</span></span>](lesson-4-2-defining-parent-attribute-properties-in-a-parent-child-hierarchy.md)  
 <span data-ttu-id="20c1a-110">在這項工作中，您會在父子式維度中定義層級名稱，並指定是否顯示與父成員有關的資料。</span><span class="sxs-lookup"><span data-stu-id="20c1a-110">In this task, you define level names in a parent-child dimension and specify whether data related to parent members is displayed.</span></span> <span data-ttu-id="20c1a-111">如需詳細資訊，[請參閱父子式階層](multidimensional-models/parent-child-dimension.md)和[父子式階層中的屬性](multidimensional-models/parent-child-dimension-attributes.md)。</span><span class="sxs-lookup"><span data-stu-id="20c1a-111">For more information, see [Parent-Child Hierarchy](multidimensional-models/parent-child-dimension.md) and [Attributes in Parent-Child Hierarchies](multidimensional-models/parent-child-dimension-attributes.md).</span></span>  
  
 [<span data-ttu-id="20c1a-112">自動分組屬性成員</span><span class="sxs-lookup"><span data-stu-id="20c1a-112">Automatically Grouping Attribute Members</span></span>](lesson-4-3-automatically-grouping-attribute-members.md)  
 <span data-ttu-id="20c1a-113">在這項工作中，您會依據屬性階層內的成員分佈情形來自動建立屬性成員的分組。</span><span class="sxs-lookup"><span data-stu-id="20c1a-113">In this task, you automatically create groupings of attribute members based on the distribution of the members within the attribute hierarchy.</span></span> <span data-ttu-id="20c1a-114">如需詳細資訊，請參閱[群組屬性成員 &#40;離散化&#41;](multidimensional-models/attribute-properties-group-attribute-members.md)。</span><span class="sxs-lookup"><span data-stu-id="20c1a-114">For more information, see [Group Attribute Members &#40;Discretization&#41;](multidimensional-models/attribute-properties-group-attribute-members.md).</span></span>  
  
 [<span data-ttu-id="20c1a-115">隱藏及停用屬性階層</span><span class="sxs-lookup"><span data-stu-id="20c1a-115">Hiding and Disabling Attribute Hierarchies</span></span>](lesson-4-4-hiding-and-disabling-attribute-hierarchies.md)  
 <span data-ttu-id="20c1a-116">在這項工作中，您會學到如何及何時停用或隱藏屬性階層。</span><span class="sxs-lookup"><span data-stu-id="20c1a-116">In this task, you learn how and when to disable or hide attribute hierarchies.</span></span>  
  
 [<span data-ttu-id="20c1a-117">依次要屬性來排序屬性成員</span><span class="sxs-lookup"><span data-stu-id="20c1a-117">Sorting Attribute Members Based on a Secondary Attribute</span></span>](lesson-4-5-sorting-attribute-members-based-on-a-secondary-attribute.md)  
 <span data-ttu-id="20c1a-118">在這項工作中，您會學到如何依據次要屬性來排序維度成員，以達到您想要的排序順序。</span><span class="sxs-lookup"><span data-stu-id="20c1a-118">In this task, you learn how to sort dimension members based on a secondary attribute, to achieve the sort order that you want.</span></span>  
  
 [<span data-ttu-id="20c1a-119">在使用者定義階層的屬性之間指定屬性關聯性</span><span class="sxs-lookup"><span data-stu-id="20c1a-119">Specifying Attribute Relationships Between Attributes in a User-Defined Hierarchy</span></span>](4-6-specifying-attribute-relationships-in-user-defined-hierarchy.md)  
 <span data-ttu-id="20c1a-120">在這項工作中，您會學到如何定義屬性的成員屬性，以及指定彼此之間的彙總關聯性。</span><span class="sxs-lookup"><span data-stu-id="20c1a-120">In this task, you learn how to define member properties for attributes and to specify aggregation relationships between them.</span></span> <span data-ttu-id="20c1a-121">如需詳細資訊，請參閱[定義屬性關聯](multidimensional-models/attribute-relationships-define.md)性和[使用者階層屬性](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md)。</span><span class="sxs-lookup"><span data-stu-id="20c1a-121">For more information, see [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md) and [User Hierarchy Properties](multidimensional-models-olap-logical-dimension-objects/user-hierarchies-properties.md).</span></span>  
  
 [<span data-ttu-id="20c1a-122">定義未知的成員和 Null 處理屬性</span><span class="sxs-lookup"><span data-stu-id="20c1a-122">Defining the Unknown Member and Null Processing Properties</span></span>](lesson-4-7-defining-the-unknown-member-and-null-processing-properties.md)  
 <span data-ttu-id="20c1a-123">在這項工作中，您會設定 UnknownMember 和 UnknownMemberName 屬性，處理 Null 維度成員所造成的錯誤狀況。</span><span class="sxs-lookup"><span data-stu-id="20c1a-123">In this task, you configure the UnknownMember and UnknownMemberName properties to handle error conditions caused by null dimension members.</span></span>  
  
## <a name="next-lesson"></a><span data-ttu-id="20c1a-124">下一課</span><span class="sxs-lookup"><span data-stu-id="20c1a-124">Next Lesson</span></span>  
 [<span data-ttu-id="20c1a-125">第5課：定義維度和量值群組之間的關聯性</span><span class="sxs-lookup"><span data-stu-id="20c1a-125">Lesson 5: Defining Relationships Between Dimensions and Measure Groups</span></span>](lesson-5-defining-relationships-between-dimensions-and-measure-groups.md)  
  
## <a name="see-also"></a><span data-ttu-id="20c1a-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20c1a-126">See Also</span></span>  
 <span data-ttu-id="20c1a-127">[Analysis Services 教學課程案例](analysis-services-tutorial-scenario.md) </span><span class="sxs-lookup"><span data-stu-id="20c1a-127">[Analysis Services Tutorial Scenario](analysis-services-tutorial-scenario.md) </span></span>  
 <span data-ttu-id="20c1a-128">[多維度模型化 &#40;的艾德作品教學課程&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span><span class="sxs-lookup"><span data-stu-id="20c1a-128">[Multidimensional Modeling &#40;Adventure Works Tutorial&#41;](multidimensional-modeling-adventure-works-tutorial.md) </span></span>  
 [<span data-ttu-id="20c1a-129">多維度模型中的維度</span><span class="sxs-lookup"><span data-stu-id="20c1a-129">Dimensions in Multidimensional Models</span></span>](multidimensional-models/dimensions-in-multidimensional-models.md)  
  
  
