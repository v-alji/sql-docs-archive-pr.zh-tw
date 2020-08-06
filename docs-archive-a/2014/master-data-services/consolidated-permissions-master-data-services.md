---
title: 合併的許可權 (Master Data Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], consolidated member attribute permissions
- consolidated members [Master Data Services], attribute permissions
- permissions [Master Data Services], consolidated members
- members [Master Data Services], consolidated member permissions
ms.assetid: 084055a3-5fd3-43f3-b620-ac6afab42a3d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c4c93e74acc84d6e742139263bedc011c4028efb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607441"
---
# <a name="consolidated-permissions-master-data-services"></a><span data-ttu-id="251a1-102">合併的權限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="251a1-102">Consolidated Permissions (Master Data Services)</span></span>
  <span data-ttu-id="251a1-103">合併的權限適用於某個實體所有合併成員的屬性值。</span><span class="sxs-lookup"><span data-stu-id="251a1-103">Consolidated permissions apply to the attribute values for all consolidated members of an entity.</span></span>  
  
 <span data-ttu-id="251a1-104">合併的權限只適用於啟用明確階層和集合的實體。</span><span class="sxs-lookup"><span data-stu-id="251a1-104">Consolidated permissions apply only to entities that are enabled for explicit hierarchies and collections.</span></span>  
  
 <span data-ttu-id="251a1-105">**注意：**</span><span class="sxs-lookup"><span data-stu-id="251a1-105">**Notes:**</span></span>  
  
-   <span data-ttu-id="251a1-106">分葉權限只適用於使用者介面的總管\*\*\*\* 功能區域。</span><span class="sxs-lookup"><span data-stu-id="251a1-106">Leaf permissions apply to the **Explorer** functional area of the user interface only.</span></span>  
  
-   <span data-ttu-id="251a1-107">系統不會強制使用指派給 **Name** 和 **Code** 屬性的權限。</span><span class="sxs-lookup"><span data-stu-id="251a1-107">Permissions assigned to **Name** and **Code** attributes are not enforced.</span></span>  
  
|<span data-ttu-id="251a1-108">權限</span><span class="sxs-lookup"><span data-stu-id="251a1-108">Permission</span></span>|<span data-ttu-id="251a1-109">描述</span><span class="sxs-lookup"><span data-stu-id="251a1-109">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="251a1-110">**唯讀**</span><span class="sxs-lookup"><span data-stu-id="251a1-110">**Read-only**</span></span>|<span data-ttu-id="251a1-111">顯示合併成員，但使用者無法加入、移除或變更這些成員。</span><span class="sxs-lookup"><span data-stu-id="251a1-111">Consolidated members are displayed but the user cannot add, remove, or change them.</span></span>|  
|<span data-ttu-id="251a1-112">**更新**</span><span class="sxs-lookup"><span data-stu-id="251a1-112">**Update**</span></span>|<span data-ttu-id="251a1-113">顯示合併成員，而且使用者可以加入、移除及變更這些成員。</span><span class="sxs-lookup"><span data-stu-id="251a1-113">Consolidated members are displayed and the user can add, remove, and change them.</span></span>|  
|<span data-ttu-id="251a1-114">**Deny**</span><span class="sxs-lookup"><span data-stu-id="251a1-114">**Deny**</span></span>|<span data-ttu-id="251a1-115">不顯示實體的合併成員。</span><span class="sxs-lookup"><span data-stu-id="251a1-115">Consolidated members for the entity are not displayed.</span></span>|  
  
## <a name="attribute-permissions"></a><span data-ttu-id="251a1-116">屬性權限</span><span class="sxs-lookup"><span data-stu-id="251a1-116">Attribute Permissions</span></span>  
 <span data-ttu-id="251a1-117">屬性權限適用於特定實體的屬性值。</span><span class="sxs-lookup"><span data-stu-id="251a1-117">Attribute permissions apply to the attribute's values for the specific entity.</span></span> <span data-ttu-id="251a1-118">只有屬性權限的使用者無法加入或移除成員。</span><span class="sxs-lookup"><span data-stu-id="251a1-118">Users with only attribute permissions cannot add or remove members.</span></span>  
  
|<span data-ttu-id="251a1-119">權限</span><span class="sxs-lookup"><span data-stu-id="251a1-119">Permission</span></span>|<span data-ttu-id="251a1-120">描述</span><span class="sxs-lookup"><span data-stu-id="251a1-120">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="251a1-121">**唯讀**</span><span class="sxs-lookup"><span data-stu-id="251a1-121">**Read-only**</span></span>|<span data-ttu-id="251a1-122">顯示屬性，但使用者無法變更屬性值。</span><span class="sxs-lookup"><span data-stu-id="251a1-122">The attribute is displayed but the user cannot change attribute values.</span></span>|  
|<span data-ttu-id="251a1-123">**更新**</span><span class="sxs-lookup"><span data-stu-id="251a1-123">**Update**</span></span>|<span data-ttu-id="251a1-124">顯示屬性，而且使用者可以變更屬性值。</span><span class="sxs-lookup"><span data-stu-id="251a1-124">The attribute is displayed and the user can change attribute values.</span></span>|  
|<span data-ttu-id="251a1-125">**Deny**</span><span class="sxs-lookup"><span data-stu-id="251a1-125">**Deny**</span></span>|<span data-ttu-id="251a1-126">不顯示屬性。</span><span class="sxs-lookup"><span data-stu-id="251a1-126">The attribute is not displayed.</span></span><br /><br /> <span data-ttu-id="251a1-127">注意：您無法明確拒絕存取 Name 和 Code 屬性。</span><span class="sxs-lookup"><span data-stu-id="251a1-127">Note: You cannot explicitly deny access to Name and Code attributes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="251a1-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="251a1-128">See Also</span></span>  
 <span data-ttu-id="251a1-129">[指派模型物件使用權限 &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="251a1-129">[Assign Model Object Permissions &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="251a1-130">[分葉許可權 &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="251a1-130">[Leaf Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="251a1-131">[模型物件使用權限 &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="251a1-131">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="251a1-132">[成員 &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="251a1-132">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 [<span data-ttu-id="251a1-133">屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="251a1-133">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
