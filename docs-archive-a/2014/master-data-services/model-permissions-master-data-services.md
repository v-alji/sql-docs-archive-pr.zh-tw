---
title: 模型權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- models [Master Data Services], permissions
- permissions [Master Data Services], models
ms.assetid: 210f440b-2cc1-4c49-94b1-3a97e2af7bc3
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 2846918b515bba16d12d48cd7058cf25863bf569
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596080"
---
# <a name="model-permissions-master-data-services"></a><span data-ttu-id="cd85b-102">模型權限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="cd85b-102">Model Permissions (Master Data Services)</span></span>
  <span data-ttu-id="cd85b-103">模型權限適用於所有實體、衍生階層、明確階層及存在於模型內的集合。</span><span class="sxs-lookup"><span data-stu-id="cd85b-103">Model permissions apply to all entities, derived hierarchies, explicit hierarchies, and collections that exist within the model.</span></span> <span data-ttu-id="cd85b-104">可以針對任何個別的物件來覆寫指派給模型的權限。</span><span class="sxs-lookup"><span data-stu-id="cd85b-104">Permissions assigned to the model can be overridden for any individual object.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="cd85b-105">如果使用者是模型管理員，則使用者介面的所有功能區域中都會顯示此模型。</span><span class="sxs-lookup"><span data-stu-id="cd85b-105">If a user is a model administrator, the model is displayed in all functional areas of the user interface.</span></span> <span data-ttu-id="cd85b-106">否則，此模型只會顯示在 [總管]\*\*\*\* 功能區域中。</span><span class="sxs-lookup"><span data-stu-id="cd85b-106">Otherwise, the model is displayed in the **Explorer** functional area only.</span></span> <span data-ttu-id="cd85b-107">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="cd85b-107">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
|<span data-ttu-id="cd85b-108">權限</span><span class="sxs-lookup"><span data-stu-id="cd85b-108">Permission</span></span>|<span data-ttu-id="cd85b-109">描述</span><span class="sxs-lookup"><span data-stu-id="cd85b-109">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="cd85b-110">**唯讀**</span><span class="sxs-lookup"><span data-stu-id="cd85b-110">**Read-only**</span></span>|<span data-ttu-id="cd85b-111">在**Explorer**中，會顯示模型，但是使用者無法加入或移除成員，也無法更新屬性值、階層成員資格或集合成員資格。</span><span class="sxs-lookup"><span data-stu-id="cd85b-111">In **Explorer**, the model is displayed but the user cannot add or remove members, and cannot update attribute values, hierarchy memberships, or collection memberships.</span></span>|  
|<span data-ttu-id="cd85b-112">**更新**</span><span class="sxs-lookup"><span data-stu-id="cd85b-112">**Update**</span></span>|<span data-ttu-id="cd85b-113">在**Explorer**中，會顯示模型，而且使用者可以加入和移除成員、可以更新屬性值、階層成員資格和集合成員資格。</span><span class="sxs-lookup"><span data-stu-id="cd85b-113">In **Explorer**, the model is displayed and the user can add and remove members, can update attribute values, hierarchy memberships, and collection memberships.</span></span>|  
|<span data-ttu-id="cd85b-114">**Deny**</span><span class="sxs-lookup"><span data-stu-id="cd85b-114">**Deny**</span></span>|<span data-ttu-id="cd85b-115">不顯示模型。</span><span class="sxs-lookup"><span data-stu-id="cd85b-115">The model is not displayed.</span></span>|  
  
 <span data-ttu-id="cd85b-116">當您將權限指派給模型時，使用者會取得模型之所有版本的存取權。</span><span class="sxs-lookup"><span data-stu-id="cd85b-116">When you assign permission to a model, the user gets access to all versions of the model.</span></span> <span data-ttu-id="cd85b-117">您無法將權限指派給個別的版本。</span><span class="sxs-lookup"><span data-stu-id="cd85b-117">You cannot assign permission to an individual version.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd85b-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cd85b-118">See Also</span></span>  
 <span data-ttu-id="cd85b-119">[指派模型物件使用權限 &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cd85b-119">[Assign Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="cd85b-120">[模型物件使用權限 &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cd85b-120">[Model Object Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/model-object-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="cd85b-121">[實體許可權 &#40;Master Data Services&#41;](../../2014/master-data-services/entity-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="cd85b-121">[Entity Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/entity-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="cd85b-122">集合權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="cd85b-122">Collection Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collection-permissions-master-data-services.md)  
  
  
