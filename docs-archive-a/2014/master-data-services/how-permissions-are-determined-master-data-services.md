---
title: 如何決定權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- permissions [Master Data Services], determining permissions
ms.assetid: 1dc0b43a-d023-4e7d-b027-8b1459fd058c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 3ea3306b772224bc8602659c7e17e8dc1634f0d5
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597180"
---
# <a name="how-permissions-are-determined-master-data-services"></a><span data-ttu-id="e32cf-102">如何決定權限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="e32cf-102">How Permissions Are Determined (Master Data Services)</span></span>
  <span data-ttu-id="e32cf-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，若要以最簡單的方式來設定安全性，可將模型物件權限指派給群組 (使用者為其中的成員)。</span><span class="sxs-lookup"><span data-stu-id="e32cf-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], the simplest way to configure security is to assign model object permissions to a group that the user is a member of.</span></span>

 <span data-ttu-id="e32cf-104">在下列情況中，安全性會變得較複雜：</span><span class="sxs-lookup"><span data-stu-id="e32cf-104">Security becomes more complex when:</span></span>

-   <span data-ttu-id="e32cf-105">同時指派了模型物件和階層成員權限。</span><span class="sxs-lookup"><span data-stu-id="e32cf-105">Both model object and hierarchy member permissions are assigned.</span></span>

-   <span data-ttu-id="e32cf-106">使用者屬於群組，而權限同時指派給使用者和群組。</span><span class="sxs-lookup"><span data-stu-id="e32cf-106">The user belongs to groups and permission is assigned to both the user and groups.</span></span>

-   <span data-ttu-id="e32cf-107">使用者屬於群組，而權限指派給多個群組。</span><span class="sxs-lookup"><span data-stu-id="e32cf-107">The user belongs to groups and permission is assigned to multiple groups.</span></span>

## <a name="permissions-assigned-to-a-single-group-or-user"></a><span data-ttu-id="e32cf-108">指派給單一群組或使用者的權限</span><span class="sxs-lookup"><span data-stu-id="e32cf-108">Permissions assigned to a single group or user</span></span>
 <span data-ttu-id="e32cf-109">如果您將權限指派給單一群組或使用者，系統就會根據下列工作流程決定權限。</span><span class="sxs-lookup"><span data-stu-id="e32cf-109">If you assign permissions to a single group or user, permissions are determined based on the following workflow.</span></span>

 <span data-ttu-id="e32cf-110">![mds_conc_security_no_overlap](../../2014/master-data-services/media/mds-conc-security-no-overlap.gif "mds_conc_security_no_overlap")</span><span class="sxs-lookup"><span data-stu-id="e32cf-110">![mds_conc_security_no_overlap](../../2014/master-data-services/media/mds-conc-security-no-overlap.gif "mds_conc_security_no_overlap")</span></span>

### <a name="step-1-effective-attribute-permissions-are-determined"></a><span data-ttu-id="e32cf-111">步驟 1：決定有效屬性權限。</span><span class="sxs-lookup"><span data-stu-id="e32cf-111">Step 1: Effective attribute permissions are determined.</span></span>
 <span data-ttu-id="e32cf-112">下列清單描述的是如何決定有效屬性權限：</span><span class="sxs-lookup"><span data-stu-id="e32cf-112">The following list describes how effective attribute permissions are determined:</span></span>

-   <span data-ttu-id="e32cf-113">指派給模型物件的權限會決定使用者可存取的屬性。</span><span class="sxs-lookup"><span data-stu-id="e32cf-113">Permissions assigned to model objects determine which attributes a user can access.</span></span>

-   <span data-ttu-id="e32cf-114">所有模型物件都會自動從模型結構中較高層級的最接近物件繼承權限。</span><span class="sxs-lookup"><span data-stu-id="e32cf-114">All model objects automatically inherit permission from the closest object at a higher level in the model structure.</span></span>

-   <span data-ttu-id="e32cf-115">隱含拒絕與實體位於相同層級的任何物件。</span><span class="sxs-lookup"><span data-stu-id="e32cf-115">Any objects at the same level as the entity are implicitly denied.</span></span>

-   <span data-ttu-id="e32cf-116">位於較高層級的任何物件會獲得導覽存取權。</span><span class="sxs-lookup"><span data-stu-id="e32cf-116">Any objects at a higher level are given navigational access.</span></span> <span data-ttu-id="e32cf-117">如需導覽存取權的詳細資訊，請參閱[導覽存取 &#40;Master Data Services&#41;](navigational-access-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e32cf-117">For more information about navigational access, see [Navigational Access &#40;Master Data Services&#41;](navigational-access-master-data-services.md).</span></span>

 <span data-ttu-id="e32cf-118">在此範例中，**唯讀**許可權會指派給實體，而且其屬性（位於模型結構中較低層級）會繼承該許可權。</span><span class="sxs-lookup"><span data-stu-id="e32cf-118">In this example, **Read-only** permission is assigned to an entity and that permission is inherited by its attribute, which is at a lower level in the model structure.</span></span> <span data-ttu-id="e32cf-119">模型會提供導覽存取權給此實體及其屬性。</span><span class="sxs-lookup"><span data-stu-id="e32cf-119">The model provides navigational access to this entity and its attribute.</span></span> <span data-ttu-id="e32cf-120">模型中的其他實體沒有被指派任何明確權限，而且沒有繼承任何權限，因此會隱含拒絕此實體。</span><span class="sxs-lookup"><span data-stu-id="e32cf-120">The other entity in the model has no explicit permission assigned and does not inherit any permissions, so it is implicitly denied.</span></span>

 <span data-ttu-id="e32cf-121">![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")</span><span class="sxs-lookup"><span data-stu-id="e32cf-121">![mds_conc_inheritance_model](../../2014/master-data-services/media/mds-conc-inheritance-model.gif "mds_conc_inheritance_model")</span></span>

### <a name="step-2-if-hierarchy-member-permissions-are-assigned-effective-member-permissions-are-determined"></a><span data-ttu-id="e32cf-122">步驟 2：如果已指派階層成員權限，就會決定有效成員權限。</span><span class="sxs-lookup"><span data-stu-id="e32cf-122">Step 2: If hierarchy member permissions are assigned, effective member permissions are determined.</span></span>
 <span data-ttu-id="e32cf-123">下列清單描述的是如何決定有效階層成員權限：</span><span class="sxs-lookup"><span data-stu-id="e32cf-123">The following list describes how effective hierarchy member permissions are determined:</span></span>

-   <span data-ttu-id="e32cf-124">指派給階層節點的權限會決定使用者可存取的成員。</span><span class="sxs-lookup"><span data-stu-id="e32cf-124">Permissions assigned to hierarchy nodes determine which members a user can access.</span></span>

-   <span data-ttu-id="e32cf-125">階層中的所有節點都會自動從階層結構中較高層級的最接近物件繼承權限。</span><span class="sxs-lookup"><span data-stu-id="e32cf-125">All nodes in a hierarchy automatically inherit permission from the closest object at a higher level in the hierarchy structure.</span></span>

-   <span data-ttu-id="e32cf-126">隱含拒絕位於相同層級的任何節點。</span><span class="sxs-lookup"><span data-stu-id="e32cf-126">Any nodes at the same level are implicitly denied.</span></span>

-   <span data-ttu-id="e32cf-127">隱含拒絕沒有被指派權限而且位於較高層級的任何節點。</span><span class="sxs-lookup"><span data-stu-id="e32cf-127">Any nodes at higher levels that do not have permissions assigned are implicitly denied.</span></span>

 <span data-ttu-id="e32cf-128">在此範例中，**唯讀**許可權會指派給階層中的一個節點，而該許可權會由階層結構中較低層級的節點繼承。</span><span class="sxs-lookup"><span data-stu-id="e32cf-128">In this example, **Read-only** permission is assigned to one node of the hierarchy and that permission is inherited by a node at a lower level in the hierarchy structure.</span></span> <span data-ttu-id="e32cf-129">根目錄沒有被指派權限，因此會隱含拒絕此根目錄。</span><span class="sxs-lookup"><span data-stu-id="e32cf-129">The root has no permission assigned, so it is implicitly denied.</span></span> <span data-ttu-id="e32cf-130">階層結構中的其他節點沒有被指派任何明確權限，而且沒有繼承任何權限，因此會隱含拒絕此節點。</span><span class="sxs-lookup"><span data-stu-id="e32cf-130">The other node in the hierarchy structure has no explicit permission assigned and does not inherit any permissions, so it is implicitly denied.</span></span>

 <span data-ttu-id="e32cf-131">![mds_conc_inheritance_hierarchy](../../2014/master-data-services/media/mds-conc-inheritance-hierarchy.gif "mds_conc_inheritance_hierarchy")</span><span class="sxs-lookup"><span data-stu-id="e32cf-131">![mds_conc_inheritance_hierarchy](../../2014/master-data-services/media/mds-conc-inheritance-hierarchy.gif "mds_conc_inheritance_hierarchy")</span></span>

### <a name="step-3-the-intersection-of-attribute-and-member-permissions-is-determined"></a><span data-ttu-id="e32cf-132">步驟 3：決定屬性與成員權限的交集。</span><span class="sxs-lookup"><span data-stu-id="e32cf-132">Step 3: The intersection of attribute and member permissions is determined.</span></span>
 <span data-ttu-id="e32cf-133">如果有效屬性權限與有效成員權限不同，就必須針對每個個別屬性值決定權限。</span><span class="sxs-lookup"><span data-stu-id="e32cf-133">If the effective attribute permissions are different than the effective member permissions, permissions must be determined for each individual attribute value.</span></span> <span data-ttu-id="e32cf-134">如需詳細資訊，請參閱 [重疊的模型和成員的權限 &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e32cf-134">For more information, see [Overlapping Model and Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md).</span></span>

## <a name="permissions-assigned-to-multiple-groups"></a><span data-ttu-id="e32cf-135">指派給多個群組的權限</span><span class="sxs-lookup"><span data-stu-id="e32cf-135">Permissions assigned to multiple groups</span></span>
 <span data-ttu-id="e32cf-136">如果使用者屬於一個或多個群組，而且權限同時指派給使用者和群組，則工作流程會變得較複雜。</span><span class="sxs-lookup"><span data-stu-id="e32cf-136">If a user belongs to one or more groups and permissions are assigned to both the user and the groups, the workflow becomes more complex.</span></span>

 <span data-ttu-id="e32cf-137">![mds_conc_security_group_overlap](../../2014/master-data-services/media/mds-conc-security-group-overlap.gif "mds_conc_security_group_overlap")</span><span class="sxs-lookup"><span data-stu-id="e32cf-137">![mds_conc_security_group_overlap](../../2014/master-data-services/media/mds-conc-security-group-overlap.gif "mds_conc_security_group_overlap")</span></span>

 <span data-ttu-id="e32cf-138">在此情況下，您必須先解析重疊的使用者和群組權限，然後才能比較模型物件與階層成員權限。</span><span class="sxs-lookup"><span data-stu-id="e32cf-138">In this case, overlapping user and group permissions must be resolved before model object and hierarchy member permissions can be compared.</span></span> <span data-ttu-id="e32cf-139">如需詳細資訊，請參閱 [重疊的使用者和群組的權限 &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="e32cf-139">For more information, see [Overlapping User and Group Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e32cf-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e32cf-140">See Also</span></span>
 <span data-ttu-id="e32cf-141">[重迭的使用者和群組許可權 &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md) [重迭的模型和成員許可權 &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)</span><span class="sxs-lookup"><span data-stu-id="e32cf-141">[Overlapping User and Group Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-user-and-group-permissions-master-data-services.md) [Overlapping Model and Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)</span></span>


