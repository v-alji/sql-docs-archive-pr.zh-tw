---
title: 屬性群組 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services]
- attribute groups [Master Data Services], about attribute groups
ms.assetid: 648b3d0b-e15a-45f9-8292-3a54a072e62c
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 390b402489799639e66a44992da1e20b0d0c1bbf
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596764"
---
# <a name="attribute-groups-master-data-services"></a><span data-ttu-id="76390-102">屬性群組 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="76390-102">Attribute Groups (Master Data Services)</span></span>
  <span data-ttu-id="76390-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，屬性群組有助於組織實體中的屬性。</span><span class="sxs-lookup"><span data-stu-id="76390-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], attribute groups help organize attributes in an entity.</span></span> <span data-ttu-id="76390-104">當實體包含多個屬性時，屬性群組可改善實體在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] Web 應用程式中顯示的方式。</span><span class="sxs-lookup"><span data-stu-id="76390-104">When an entity has lots of attributes, attribute groups improve the way an entity is displayed in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] web application.</span></span>  
  
## <a name="how-attribute-groups-change-the-display"></a><span data-ttu-id="76390-105">屬性群組如何變更顯示</span><span class="sxs-lookup"><span data-stu-id="76390-105">How Attribute Groups Change the Display</span></span>  
 <span data-ttu-id="76390-106">屬性群組會以方格上方的索引標籤形式顯示在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 的 [總管]\*\*\*\* 功能區域。</span><span class="sxs-lookup"><span data-stu-id="76390-106">Attribute groups are displayed as tabs above the grid in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
 <span data-ttu-id="76390-107">如果實體有大量屬性，當您在 [總管]\*\*\*\* 的方格中檢視該實體時，必須捲動至右方，才能檢視所有屬性。</span><span class="sxs-lookup"><span data-stu-id="76390-107">When an entity has a large number of attributes and you view that entity in a grid in **Explorer**, you must scroll to the right to view all of the attributes.</span></span> <span data-ttu-id="76390-108">若要避免此捲動，您可以建立屬性群組。</span><span class="sxs-lookup"><span data-stu-id="76390-108">To prevent this scrolling, you can create attribute groups.</span></span>  
  
-   <span data-ttu-id="76390-109">屬性群組永遠包含 Name 和 Code 屬性。</span><span class="sxs-lookup"><span data-stu-id="76390-109">Attribute groups always include the Name and Code attributes.</span></span>  
  
-   <span data-ttu-id="76390-110">實體的每個屬性可以屬於一個或多個屬性群組。</span><span class="sxs-lookup"><span data-stu-id="76390-110">Each attribute for an entity can belong to one or more attribute groups.</span></span>  
  
-   <span data-ttu-id="76390-111">所有屬性都會自動包含在 [總管]\*\*\*\* 的 [所有屬性]\*\*\*\* 索引標籤上。</span><span class="sxs-lookup"><span data-stu-id="76390-111">All attributes are automatically included on the **All Attributes** tab in **Explorer**.</span></span>  
  
-   <span data-ttu-id="76390-112">沒有方法可以隱藏 [所有屬性]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="76390-112">There is no way to hide the **All Attributes** tab.</span></span>  
  
 <span data-ttu-id="76390-113">屬性群組是在[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]的 [系統管理]\*\*\*\* 功能區域中管理的。</span><span class="sxs-lookup"><span data-stu-id="76390-113">Attribute groups are administered in the **System Administration** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
## <a name="show-or-hide-attribute-groups"></a><span data-ttu-id="76390-114">顯示或隱藏屬性群組</span><span class="sxs-lookup"><span data-stu-id="76390-114">Show or Hide Attribute Groups</span></span>  
 <span data-ttu-id="76390-115">當您建立屬性群組時，它會自動隱藏起來不讓所有使用者看到，除了建立它的使用者以外。</span><span class="sxs-lookup"><span data-stu-id="76390-115">When you create an attribute group, it is automatically hidden from all users except the one who created it.</span></span> <span data-ttu-id="76390-116">如需如何顯示此群組的詳細資訊，請參閱 [讓使用者看到屬性群組 &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="76390-116">For more information about making the group visible, see [Make an Attribute Group Visible to Users &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md).</span></span>  
  
 <span data-ttu-id="76390-117">如果您想要隱藏群組中的特定屬性，您可以將 **拒絕** 權限指派給此屬性。</span><span class="sxs-lookup"><span data-stu-id="76390-117">If you want to hide a specific attribute within a group, you can assign **Deny** permission to the attribute.</span></span> <span data-ttu-id="76390-118">如需詳細資訊，請參閱[分葉權限 &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) 或[合併的權限 &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="76390-118">For more information, see [Leaf Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) or [Consolidated Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/consolidated-permissions-master-data-services.md).</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="76390-119">相關工作</span><span class="sxs-lookup"><span data-stu-id="76390-119">Related Tasks</span></span>  
  
|<span data-ttu-id="76390-120">工作描述</span><span class="sxs-lookup"><span data-stu-id="76390-120">Task Description</span></span>|<span data-ttu-id="76390-121">主題</span><span class="sxs-lookup"><span data-stu-id="76390-121">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="76390-122">建立新的屬性群組並加入屬性。</span><span class="sxs-lookup"><span data-stu-id="76390-122">Create a new attribute group and add attributes to it.</span></span>|[<span data-ttu-id="76390-123">建立屬性群組 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="76390-123">Create an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)|  
|<span data-ttu-id="76390-124">讓使用者看到屬性群組。</span><span class="sxs-lookup"><span data-stu-id="76390-124">Make an attribute group visible to users.</span></span>|[<span data-ttu-id="76390-125">讓使用者看到屬性群組 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="76390-125">Make an Attribute Group Visible to Users &#40;Master Data Services&#41;</span></span>](make-an-attribute-group-visible-to-users-master-data-services.md)|  
|<span data-ttu-id="76390-126">變更現有屬性群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="76390-126">Change the name of an existing attribute group.</span></span>|[<span data-ttu-id="76390-127">變更屬性群組名稱 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="76390-127">Change an Attribute Group Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md)|  
|<span data-ttu-id="76390-128">刪除現有屬性群組。</span><span class="sxs-lookup"><span data-stu-id="76390-128">Delete an existing attribute group.</span></span>|[<span data-ttu-id="76390-129">刪除屬性群組 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="76390-129">Delete an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md)|  
  
## <a name="related-content"></a><span data-ttu-id="76390-130">相關內容</span><span class="sxs-lookup"><span data-stu-id="76390-130">Related Content</span></span>  
  
-   [<span data-ttu-id="76390-131">屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="76390-131">Attributes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/attributes-master-data-services.md)  
  
  
