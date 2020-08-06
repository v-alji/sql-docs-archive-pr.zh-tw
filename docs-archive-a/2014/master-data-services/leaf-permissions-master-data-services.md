---
title: 分葉權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], permissions
- members [Master Data Services], leaf member permissions
- permissions [Master Data Services], leaf members
- leaf members [Master Data Services], attribute permissions
- attributes [Master Data Services], leaf member attribute permissions
ms.assetid: bde16e8c-bcd4-4041-8130-55c5450e5f72
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 794e1d138b91e896b8df16765ae8984c6e60aca7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706550"
---
# <a name="leaf-permissions-master-data-services"></a><span data-ttu-id="3d668-102">分葉權限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3d668-102">Leaf Permissions (Master Data Services)</span></span>
  <span data-ttu-id="3d668-103">分葉權限適用於某個實體所有分葉成員的屬性值。</span><span class="sxs-lookup"><span data-stu-id="3d668-103">Leaf permissions apply to the attribute values for all leaf members of an entity.</span></span>  
  
 <span data-ttu-id="3d668-104">如果是沒有啟用明確階層的實體，將權限指派給 [分葉]\*\*\*\* 與指派給實體相同。</span><span class="sxs-lookup"><span data-stu-id="3d668-104">For entities without explicit hierarchies enabled, assigning permission to **Leaf** is the same as assigning permission to the entity.</span></span>  
  
 <span data-ttu-id="3d668-105">**注意：**</span><span class="sxs-lookup"><span data-stu-id="3d668-105">**Notes:**</span></span>  
  
-   <span data-ttu-id="3d668-106">分葉權限只適用於使用者介面的總管\*\*\*\* 功能區域。</span><span class="sxs-lookup"><span data-stu-id="3d668-106">Leaf permissions apply to the **Explorer** functional area of the user interface only.</span></span>  
  
-   <span data-ttu-id="3d668-107">系統不會強制使用指派給 **Name** 和 **Code** 屬性的權限。</span><span class="sxs-lookup"><span data-stu-id="3d668-107">Permissions assigned to **Name** and **Code** attributes are not enforced.</span></span>  
  
|<span data-ttu-id="3d668-108">權限</span><span class="sxs-lookup"><span data-stu-id="3d668-108">Permission</span></span>|<span data-ttu-id="3d668-109">描述</span><span class="sxs-lookup"><span data-stu-id="3d668-109">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="3d668-110">**唯讀**</span><span class="sxs-lookup"><span data-stu-id="3d668-110">**Read-only**</span></span>|<span data-ttu-id="3d668-111">顯示分葉成員，但使用者無法加入、移除或變更這些成員。</span><span class="sxs-lookup"><span data-stu-id="3d668-111">Leaf members are displayed but the user cannot add, remove, or change them.</span></span><br /><br /> <span data-ttu-id="3d668-112">如果合併成員存在，將會顯示 Name 和 Code，但是使用者無法將其加入、移除或變更。</span><span class="sxs-lookup"><span data-stu-id="3d668-112">If consolidated members exist, the names and codes are displayed but the user cannot add, remove, or change them.</span></span>|  
|<span data-ttu-id="3d668-113">**更新**</span><span class="sxs-lookup"><span data-stu-id="3d668-113">**Update**</span></span>|<span data-ttu-id="3d668-114">顯示分葉成員，而且使用者可以加入、移除及變更這些成員。</span><span class="sxs-lookup"><span data-stu-id="3d668-114">Leaf members are displayed and the user can add, remove, and change them.</span></span><br /><br /> <span data-ttu-id="3d668-115">如果合併成員存在，將會顯示 Name 和 Code，但是使用者無法將其加入、移除或變更。</span><span class="sxs-lookup"><span data-stu-id="3d668-115">If consolidated members exist, the names and codes are displayed but the user cannot add, remove, or change them.</span></span>|  
|<span data-ttu-id="3d668-116">**Deny**</span><span class="sxs-lookup"><span data-stu-id="3d668-116">**Deny**</span></span>|<span data-ttu-id="3d668-117">不顯示實體的分葉成員。</span><span class="sxs-lookup"><span data-stu-id="3d668-117">Leaf members for the entity are not displayed.</span></span>|  
  
## <a name="attribute-permissions"></a><span data-ttu-id="3d668-118">屬性權限</span><span class="sxs-lookup"><span data-stu-id="3d668-118">Attribute Permissions</span></span>  
 <span data-ttu-id="3d668-119">屬性權限適用於特定實體的屬性值。</span><span class="sxs-lookup"><span data-stu-id="3d668-119">Attribute permissions apply to the attribute's values for the specific entity.</span></span> <span data-ttu-id="3d668-120">只有屬性權限的使用者無法加入或移除成員。</span><span class="sxs-lookup"><span data-stu-id="3d668-120">Users with attribute permissions only cannot add or remove members.</span></span>  
  
|<span data-ttu-id="3d668-121">權限</span><span class="sxs-lookup"><span data-stu-id="3d668-121">Permission</span></span>|<span data-ttu-id="3d668-122">描述</span><span class="sxs-lookup"><span data-stu-id="3d668-122">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="3d668-123">**唯讀**</span><span class="sxs-lookup"><span data-stu-id="3d668-123">**Read-only**</span></span>|<span data-ttu-id="3d668-124">顯示屬性，但使用者無法變更屬性值。</span><span class="sxs-lookup"><span data-stu-id="3d668-124">The attribute is displayed but the user cannot change attribute values.</span></span>|  
|<span data-ttu-id="3d668-125">**更新**</span><span class="sxs-lookup"><span data-stu-id="3d668-125">**Update**</span></span>|<span data-ttu-id="3d668-126">顯示屬性，而且使用者可以變更屬性值。</span><span class="sxs-lookup"><span data-stu-id="3d668-126">The attribute is displayed and the user can change attribute values.</span></span>|  
|<span data-ttu-id="3d668-127">**Deny**</span><span class="sxs-lookup"><span data-stu-id="3d668-127">**Deny**</span></span>|<span data-ttu-id="3d668-128">不顯示屬性。</span><span class="sxs-lookup"><span data-stu-id="3d668-128">The attribute is not displayed.</span></span><br /><br /> <span data-ttu-id="3d668-129">注意：您無法明確拒絕存取 Name 和 Code 屬性。</span><span class="sxs-lookup"><span data-stu-id="3d668-129">Note: You cannot explicitly deny access to Name and Code attributes.</span></span>|  
  
### <a name="example"></a><span data-ttu-id="3d668-130">範例</span><span class="sxs-lookup"><span data-stu-id="3d668-130">Example</span></span>  
 <span data-ttu-id="3d668-131">如果是 Product 實體，請將 [更新]\*\*\*\* 權限指派給 Subcategory 屬性。</span><span class="sxs-lookup"><span data-stu-id="3d668-131">For the Product entity, assign **Update** permission to Subcategory attribute.</span></span> <span data-ttu-id="3d668-132">拒絕其他所有屬性的權限。</span><span class="sxs-lookup"><span data-stu-id="3d668-132">Deny permission to all other attributes.</span></span>  
  
|<span data-ttu-id="3d668-133">名稱</span><span class="sxs-lookup"><span data-stu-id="3d668-133">Name</span></span>|<span data-ttu-id="3d668-134">程式碼</span><span class="sxs-lookup"><span data-stu-id="3d668-134">Code</span></span>|<span data-ttu-id="3d668-135">Subcategory (更新)</span><span class="sxs-lookup"><span data-stu-id="3d668-135">Subcategory (Update)</span></span>|  
|----------|----------|----------------------------|  
|<span data-ttu-id="3d668-136">Mountain-100</span><span class="sxs-lookup"><span data-stu-id="3d668-136">Mountain-100</span></span>|<span data-ttu-id="3d668-137">BK-M101</span><span class="sxs-lookup"><span data-stu-id="3d668-137">BK-M101</span></span>|<span data-ttu-id="3d668-138">{5}山區自行車</span><span class="sxs-lookup"><span data-stu-id="3d668-138">{5} Mountain Bikes</span></span>|  
|<span data-ttu-id="3d668-139">Mountain-100</span><span class="sxs-lookup"><span data-stu-id="3d668-139">Mountain-100</span></span>|<span data-ttu-id="3d668-140">BK-M201</span><span class="sxs-lookup"><span data-stu-id="3d668-140">BK-M201</span></span>|<span data-ttu-id="3d668-141">{5}山區自行車</span><span class="sxs-lookup"><span data-stu-id="3d668-141">{5} Mountain Bikes</span></span>|  
  
 <span data-ttu-id="3d668-142">在總管\*\*\*\* 中，您可以更新 Subcategory 資料行中的任何屬性值。</span><span class="sxs-lookup"><span data-stu-id="3d668-142">In **Explorer**, you can update any attribute value in the Subcategory column.</span></span> <span data-ttu-id="3d668-143">如果您沒有屬性的權限，就不會顯示該屬性。</span><span class="sxs-lookup"><span data-stu-id="3d668-143">If you do not have permission to an attribute, the attribute is not displayed.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3d668-144">在這個範例中，Subcategory 是根據 SubcategoryList 實體的網域屬性。</span><span class="sxs-lookup"><span data-stu-id="3d668-144">In this example, Subcategory is a domain-based attribute, based on the SubcategoryList entity.</span></span> <span data-ttu-id="3d668-145">您可以為 Mountain-100 選取不同的子類別目錄，但是您無法從 SubcategoryList 實體中加入成員或刪除成員。</span><span class="sxs-lookup"><span data-stu-id="3d668-145">You can select a different subcategory for Mountain-100 but you cannot add members to or delete members from the SubcategoryList entity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d668-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3d668-146">See Also</span></span>  
 <span data-ttu-id="3d668-147">[指派模型物件使用權限 &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3d668-147">[Assign Model Object Permissions &#40;Master Data Services&#41;](assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="3d668-148">[合併的許可權 &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3d668-148">[Consolidated Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="3d668-149">[模型物件使用權限 &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3d668-149">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="3d668-150">[成員 &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3d668-150">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 [<span data-ttu-id="3d668-151">屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3d668-151">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
