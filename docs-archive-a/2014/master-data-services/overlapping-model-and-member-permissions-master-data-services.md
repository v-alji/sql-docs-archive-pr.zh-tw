---
title: 重疊的模型和成員的權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], effective permissions
- permissions [Master Data Services], model and member overlaps
- members [Master Data Services], effective permissions
ms.assetid: 9fd7a555-43bf-4796-a8b6-1ca63a291216
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: ec5f4019f25a777e4c70433bd9a7e72fca2277e2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592084"
---
# <a name="overlapping-model-and-member-permissions-master-data-services"></a><span data-ttu-id="77f4a-102">重疊的模型和成員的權限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="77f4a-102">Overlapping Model and Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="77f4a-103">指派給成員的權限可能會與指派給模型物件的權限重疊。</span><span class="sxs-lookup"><span data-stu-id="77f4a-103">Permission assigned to a member can overlap with permission assigned to a model object.</span></span> <span data-ttu-id="77f4a-104">當發生重疊情況時，比較嚴格的權限會生效。</span><span class="sxs-lookup"><span data-stu-id="77f4a-104">When overlaps occur, the more restrictive permission takes effect.</span></span>  
  
 <span data-ttu-id="77f4a-105">如果成員擁有的權限與其對應模型物件的權限不同，則會套用下列規則：</span><span class="sxs-lookup"><span data-stu-id="77f4a-105">If a member has permission that is different than its corresponding model object, the following rules apply:</span></span>  
  
-   <span data-ttu-id="77f4a-106">**[拒絕]** 會覆寫所有其他的權限。</span><span class="sxs-lookup"><span data-stu-id="77f4a-106">**Deny** overrides all other permissions.</span></span>  
  
-   <span data-ttu-id="77f4a-107">**唯讀**覆寫**更新**。</span><span class="sxs-lookup"><span data-stu-id="77f4a-107">**Read-only** overrides **Update**.</span></span>  
  
 <span data-ttu-id="77f4a-108">下圖顯示當屬性權限與成員權限不同時，個別屬性值的哪些權限會生效。</span><span class="sxs-lookup"><span data-stu-id="77f4a-108">The following image shows which permissions take effect on an individual attribute value when attribute permissions are different than member permissions.</span></span>  
  
 <span data-ttu-id="77f4a-109">![mds_conc_security_member_overlap_table](../../2014/master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")</span><span class="sxs-lookup"><span data-stu-id="77f4a-109">![mds_conc_security_member_overlap_table](../../2014/master-data-services/media/mds-conc-security-member-overlap-table.gif "mds_conc_security_member_overlap_table")</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="77f4a-110">範例 1</span><span class="sxs-lookup"><span data-stu-id="77f4a-110">Example 1</span></span>  
 <span data-ttu-id="77f4a-111">![mds_conc_overlap_model_1](../../2014/master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")</span><span class="sxs-lookup"><span data-stu-id="77f4a-111">![mds_conc_overlap_model_1](../../2014/master-data-services/media/mds-conc-overlap-model-1.gif "mds_conc_overlap_model_1")</span></span>  
  
 <span data-ttu-id="77f4a-112">在 **[模型]** 索引標籤上，Product 實體已被指派 **[更新]** 權限。</span><span class="sxs-lookup"><span data-stu-id="77f4a-112">On the **Models** tab, the Product entity has **Update** permission assigned.</span></span> <span data-ttu-id="77f4a-113">此實體中的所有屬性都會繼承該權限。</span><span class="sxs-lookup"><span data-stu-id="77f4a-113">All attributes in the entity inherit that permission.</span></span>  
  
 <span data-ttu-id="77f4a-114">在 **[階層成員]** 索引標籤上，衍生階層中的 Mountain Bikes 子類別目錄節點已被指派 **[更新]** 權限。</span><span class="sxs-lookup"><span data-stu-id="77f4a-114">On the **Hierarchy Members** tab, the Mountain Bikes subcategory node in a derived hierarchy has **Update** permission assigned.</span></span>  
  
 <span data-ttu-id="77f4a-115">結果：在 **[總管]** 中，使用者擁有 Mountain Bikes 節點中所有成員之所有屬性值的 **[更新]** 權限。</span><span class="sxs-lookup"><span data-stu-id="77f4a-115">Result: In **Explorer**, the user has **Update** permission to all attribute values for all members in the Mountain Bikes node.</span></span> <span data-ttu-id="77f4a-116">系統會隱藏所有其他成員和屬性。</span><span class="sxs-lookup"><span data-stu-id="77f4a-116">All other members and attributes are hidden.</span></span>  
  
 <span data-ttu-id="77f4a-117">![mds_conc_overlap_model_example_1](../../2014/master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")</span><span class="sxs-lookup"><span data-stu-id="77f4a-117">![mds_conc_overlap_model_example_1](../../2014/master-data-services/media/mds-conc-overlap-model-example-1.gif "mds_conc_overlap_model_example_1")</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="77f4a-118">範例 2</span><span class="sxs-lookup"><span data-stu-id="77f4a-118">Example 2</span></span>  
 <span data-ttu-id="77f4a-119">![mds_conc_overlap_model_2](../../2014/master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")</span><span class="sxs-lookup"><span data-stu-id="77f4a-119">![mds_conc_overlap_model_2](../../2014/master-data-services/media/mds-conc-overlap-model-2.gif "mds_conc_overlap_model_2")</span></span>  
  
 <span data-ttu-id="77f4a-120">在 **[模型]** 索引標籤上，Subcategory 屬性已被指派 **[更新]** 權限。</span><span class="sxs-lookup"><span data-stu-id="77f4a-120">On the **Models** tab, the Subcategory attribute has **Update** permission assigned.</span></span>  
  
 <span data-ttu-id="77f4a-121">在 [階層**成員**] 索引標籤上，衍生階層中的 [山區自行車子類別目錄] 節點會明確指派 [**唯讀**] 許可權。</span><span class="sxs-lookup"><span data-stu-id="77f4a-121">On the **Hierarchy Members** tab, the Mountain Bikes subcategory node in a derived hierarchy is explicitly assigned **Read-only** permission.</span></span>  
  
 <span data-ttu-id="77f4a-122">結果：在**Explorer**中，使用者對 [山區自行車] 節點中成員的子類別屬性值具有 [**唯讀**] 許可權。</span><span class="sxs-lookup"><span data-stu-id="77f4a-122">Result: In **Explorer**, the user has **Read-only** permission to the Subcategory attribute values for the members in the Mountain Bikes node.</span></span> <span data-ttu-id="77f4a-123">系統會隱藏所有其他成員和屬性。</span><span class="sxs-lookup"><span data-stu-id="77f4a-123">All other members and attributes are hidden.</span></span>  
  
 <span data-ttu-id="77f4a-124">![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")</span><span class="sxs-lookup"><span data-stu-id="77f4a-124">![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")</span></span>  
  
## <a name="example-3"></a><span data-ttu-id="77f4a-125">範例 3</span><span class="sxs-lookup"><span data-stu-id="77f4a-125">Example 3</span></span>  
 <span data-ttu-id="77f4a-126">![mds_conc_overlap_model_3](../../2014/master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")</span><span class="sxs-lookup"><span data-stu-id="77f4a-126">![mds_conc_overlap_model_3](../../2014/master-data-services/media/mds-conc-overlap-model-3.gif "mds_conc_overlap_model_3")</span></span>  
  
 <span data-ttu-id="77f4a-127">在 [**模型**] 索引標籤上，[子類別目錄] 屬性已獲指派 [**唯讀**] 許可權。</span><span class="sxs-lookup"><span data-stu-id="77f4a-127">On the **Models** tab, the Subcategory attribute has **Read-only** permission assigned.</span></span>  
  
 <span data-ttu-id="77f4a-128">在 **[階層成員]** 索引標籤上，衍生階層中的 Mountain Bikes 子類別目錄已被明確指派 **[更新]** 權限。</span><span class="sxs-lookup"><span data-stu-id="77f4a-128">On the **Hierarchy Members** tab, the Mountain Bikes subcategory in a derived hierarchy is explicitly assigned **Update** permission.</span></span>  
  
 <span data-ttu-id="77f4a-129">結果：在 [ **Explorer**] 中，使用者擁有屬性值的 [**唯讀**] 許可權。</span><span class="sxs-lookup"><span data-stu-id="77f4a-129">Result: In **Explorer**, the user has **Read-only** permission to the attribute values.</span></span> <span data-ttu-id="77f4a-130">系統會隱藏所有其他成員和屬性。</span><span class="sxs-lookup"><span data-stu-id="77f4a-130">All other members and attributes are hidden.</span></span>  
  
 <span data-ttu-id="77f4a-131">![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")</span><span class="sxs-lookup"><span data-stu-id="77f4a-131">![mds_conc_overlap_model_example_2](../../2014/master-data-services/media/mds-conc-overlap-model-example-2.gif "mds_conc_overlap_model_example_2")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f4a-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="77f4a-132">See Also</span></span>  
 <span data-ttu-id="77f4a-133">[如何判斷許可權 &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="77f4a-133">[How Permissions Are Determined &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md) </span></span>  
 [<span data-ttu-id="77f4a-134">重疊的使用者和群組的權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="77f4a-134">Overlapping User and Group Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md)  
  
  
