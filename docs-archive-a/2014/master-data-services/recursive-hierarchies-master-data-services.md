---
title: 遞迴階層 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- recursive hierarchies [Master Data Services]
- hierarchies [Master Data Services], recursive hierarchies
ms.assetid: 9408c6ea-d9c4-4a0b-8a1b-1457fb6944af
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3c149d500ce1499ad36247d5e32bb6f2d55b4250
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599539"
---
# <a name="recursive-hierarchies-master-data-services"></a><span data-ttu-id="1800f-102">遞迴階層 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="1800f-102">Recursive Hierarchies (Master Data Services)</span></span>
  <span data-ttu-id="1800f-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，遞迴階層是包含遞迴關聯性的衍生階層。</span><span class="sxs-lookup"><span data-stu-id="1800f-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a recursive hierarchy is a derived hierarchy that includes a recursive relationship.</span></span> <span data-ttu-id="1800f-104">當實體有基於實體本身的網域屬性時，就會有遞迴關聯性。</span><span class="sxs-lookup"><span data-stu-id="1800f-104">A recursive relationship exists when an entity has a domain-based attribute based on the entity itself.</span></span>

## <a name="recursive-hierarchy-example"></a><span data-ttu-id="1800f-105">遞迴階層範例</span><span class="sxs-lookup"><span data-stu-id="1800f-105">Recursive Hierarchy Example</span></span>
 <span data-ttu-id="1800f-106">典型的遞迴階層範例是組織結構。</span><span class="sxs-lookup"><span data-stu-id="1800f-106">A typical recursive hierarchy example is an organizational structure.</span></span> <span data-ttu-id="1800f-107">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，您可以建立具有稱為經理之網域屬性的員工實體來進行。</span><span class="sxs-lookup"><span data-stu-id="1800f-107">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], you would do this by creating an Employee entity with a domain-based attribute called Manager.</span></span> <span data-ttu-id="1800f-108">經理屬性是從員工清單中擴展。</span><span class="sxs-lookup"><span data-stu-id="1800f-108">The Manager attribute is populated from the list of employees.</span></span> <span data-ttu-id="1800f-109">在這個範例組織中，所有員工都可以是經理。</span><span class="sxs-lookup"><span data-stu-id="1800f-109">In this sample organization, all employees can be managers.</span></span>

 <span data-ttu-id="1800f-110">![mds_conc_recursive_table_w_data](../../2014/master-data-services/media/mds-conc-recursive-table-w-data.gif "mds_conc_recursive_table_w_data")</span><span class="sxs-lookup"><span data-stu-id="1800f-110">![mds_conc_recursive_table_w_data](../../2014/master-data-services/media/mds-conc-recursive-table-w-data.gif "mds_conc_recursive_table_w_data")</span></span>

 <span data-ttu-id="1800f-111">您可以建立衍生階層，以反白顯示員工實體和經理網域屬性之間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="1800f-111">You can create a derived hierarchy that highlights the relationship between the Employee entity and the Manager domain-based attribute.</span></span>

 <span data-ttu-id="1800f-112">![mds_conc_recursive_UI_structure](../../2014/master-data-services/media/mds-conc-recursive-ui-structure.gif "mds_conc_recursive_UI_structure")</span><span class="sxs-lookup"><span data-stu-id="1800f-112">![mds_conc_recursive_UI_structure](../../2014/master-data-services/media/mds-conc-recursive-ui-structure.gif "mds_conc_recursive_UI_structure")</span></span>

 <span data-ttu-id="1800f-113">若要讓每個成員只能包含在階層中一次，您可以錨定 Null 關聯性。</span><span class="sxs-lookup"><span data-stu-id="1800f-113">To include each member in the hierarchy only once, you can anchor null relationships.</span></span> <span data-ttu-id="1800f-114">當您這樣做時，具有空白網域屬性值的成員會顯示在階層的最上層。</span><span class="sxs-lookup"><span data-stu-id="1800f-114">When you do, members with blank domain-based attribute values are displayed at the top level of the hierarchy.</span></span>

 <span data-ttu-id="1800f-115">![mds_conc_recursive_UI_example_anchored](../../2014/master-data-services/media/mds-conc-recursive-ui-example-anchored.gif "mds_conc_recursive_UI_example_anchored")</span><span class="sxs-lookup"><span data-stu-id="1800f-115">![mds_conc_recursive_UI_example_anchored](../../2014/master-data-services/media/mds-conc-recursive-ui-example-anchored.gif "mds_conc_recursive_UI_example_anchored")</span></span>

 <span data-ttu-id="1800f-116">如果沒有錨定 Null 關聯性，則會多次包含成員。</span><span class="sxs-lookup"><span data-stu-id="1800f-116">If you do not anchor null relationships, members are included multiple times.</span></span> <span data-ttu-id="1800f-117">所有成員都會顯示在最上層。</span><span class="sxs-lookup"><span data-stu-id="1800f-117">All members are displayed at the top level.</span></span> <span data-ttu-id="1800f-118">此外，也會顯示在其他成員底下當做屬性。</span><span class="sxs-lookup"><span data-stu-id="1800f-118">They are also displayed under members of which they are attributes.</span></span>

 <span data-ttu-id="1800f-119">![mds_conc_recursive_UI_example_nonanchored](../../2014/master-data-services/media/mds-conc-recursive-ui-example-nonanchored.gif "mds_conc_recursive_UI_example_nonanchored")</span><span class="sxs-lookup"><span data-stu-id="1800f-119">![mds_conc_recursive_UI_example_nonanchored](../../2014/master-data-services/media/mds-conc-recursive-ui-example-nonanchored.gif "mds_conc_recursive_UI_example_nonanchored")</span></span>

 <span data-ttu-id="1800f-120">在這個範例中，Marcia 位於最上層。</span><span class="sxs-lookup"><span data-stu-id="1800f-120">In this example, Marcia is at the top level.</span></span> <span data-ttu-id="1800f-121">她不是任何員工的經理，因為她不做為任何其他員工成員的網域屬性值。</span><span class="sxs-lookup"><span data-stu-id="1800f-121">She is not the manager of any employees because she is not used as a domain-based attribute value for any other Employee members.</span></span> <span data-ttu-id="1800f-122">相反地，Robert 底下有一個層級，因為 Robert 是做為 Marcia 的經理屬性值。</span><span class="sxs-lookup"><span data-stu-id="1800f-122">Robert, in contrast, has a level beneath him because Marcia has Robert as her Manager attribute value.</span></span>

## <a name="rules"></a><span data-ttu-id="1800f-123">規則</span><span class="sxs-lookup"><span data-stu-id="1800f-123">Rules</span></span>

-   <span data-ttu-id="1800f-124">衍生階層不能包含一個以上的遞迴關聯性。</span><span class="sxs-lookup"><span data-stu-id="1800f-124">A derived hierarchy cannot contain more than one recursive relationship.</span></span> <span data-ttu-id="1800f-125">但是可以擁有其他衍生關聯性 (例如，包含遞迴經理與員工關聯性的衍生階層也可以擁有國家 (地區) 與經理及員工與商店的關聯性)。</span><span class="sxs-lookup"><span data-stu-id="1800f-125">It can, however, have other derived relationships (for example, a derived hierarchy that contains a recursive Manager to Employee relationship can also have Country to Manager and Employee to Store relationships).</span></span>

-   <span data-ttu-id="1800f-126">不能指派成員權限 (在 [階層成員]\*\*\*\* 索引標籤上) 給遞迴階層中的成員。</span><span class="sxs-lookup"><span data-stu-id="1800f-126">You cannot assign member permissions (on the **Hierarchy Members** tab) to members in a recursive hierarchy.</span></span>

-   <span data-ttu-id="1800f-127">遞迴階層不能包含循環關聯性。</span><span class="sxs-lookup"><span data-stu-id="1800f-127">Recursive hierarchies cannot include circular relationships.</span></span> <span data-ttu-id="1800f-128">例如，如果 Sandeep 是 Katherine 的經理，Katherine 不能做為 Sandeep 的經理。</span><span class="sxs-lookup"><span data-stu-id="1800f-128">For example, Katherine cannot be Sandeep's manager if Sandeep is her manager.</span></span> <span data-ttu-id="1800f-129">此外，Katherine 不能管理她自己。</span><span class="sxs-lookup"><span data-stu-id="1800f-129">Also, Katherine cannot manage herself.</span></span>

## <a name="related-tasks"></a><span data-ttu-id="1800f-130">相關工作</span><span class="sxs-lookup"><span data-stu-id="1800f-130">Related Tasks</span></span>

|<span data-ttu-id="1800f-131">工作描述</span><span class="sxs-lookup"><span data-stu-id="1800f-131">Task Description</span></span>|<span data-ttu-id="1800f-132">主題</span><span class="sxs-lookup"><span data-stu-id="1800f-132">Topic</span></span>|
|----------------------|-----------|
|<span data-ttu-id="1800f-133">建立衍生階層。</span><span class="sxs-lookup"><span data-stu-id="1800f-133">Create a derived hierarchy.</span></span>|[<span data-ttu-id="1800f-134">建立衍生階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1800f-134">Create a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](create-a-derived-hierarchy-master-data-services.md)|
|<span data-ttu-id="1800f-135">變更現有衍生階層的名稱。</span><span class="sxs-lookup"><span data-stu-id="1800f-135">Change the name of an existing derived hierarchy.</span></span>|[<span data-ttu-id="1800f-136">變更衍生階層名稱 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1800f-136">Change a Derived Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-a-derived-hierarchy-name-master-data-services.md)|
|<span data-ttu-id="1800f-137">刪除現有衍生階層。</span><span class="sxs-lookup"><span data-stu-id="1800f-137">Delete an existing derived hierarchy.</span></span>|[<span data-ttu-id="1800f-138">刪除衍生階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1800f-138">Delete a Derived Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-a-derived-hierarchy-master-data-services.md)|

## <a name="related-content"></a><span data-ttu-id="1800f-139">相關內容</span><span class="sxs-lookup"><span data-stu-id="1800f-139">Related Content</span></span>

-   [<span data-ttu-id="1800f-140">網域屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1800f-140">Domain-Based Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/domain-based-attributes-master-data-services.md)

-   [<span data-ttu-id="1800f-141">衍生階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="1800f-141">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)


