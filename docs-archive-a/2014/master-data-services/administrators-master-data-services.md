---
title: 管理員 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- administrators [Master Data Services], about administrators
- administrators [Master Data Services]
- models [Master Data Services], administrators
ms.assetid: d330aa4e-6ade-4b09-b376-1b15d6c78f7d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 52e16d4e77acc0a6b50b87e00184918cb9ce64b1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703073"
---
# <a name="administrators-master-data-services"></a><span data-ttu-id="d4545-102">管理員 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d4545-102">Administrators (Master Data Services)</span></span>
  <span data-ttu-id="d4545-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中，有兩種管理員類型：模型管理員及 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 系統管理員。</span><span class="sxs-lookup"><span data-stu-id="d4545-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], there are two types of administrators: model administrators, and the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system administrator.</span></span>  
  
## <a name="model-administrators"></a><span data-ttu-id="d4545-104">模型管理員</span><span class="sxs-lookup"><span data-stu-id="d4545-104">Model Administrators</span></span>  
 <span data-ttu-id="d4545-105">在中 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] ，模型系統管理員是在 [**模型物件**] 索引標籤上獲派最上層模型物件之 [**更新**] 許可權，而且沒有其他指派許可權的使用者。</span><span class="sxs-lookup"><span data-stu-id="d4545-105">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], a model administrator is a user who has **Update** permission assigned to the top-level model object on the **Model Objects** tab and no other assigned permissions.</span></span>  
  
-   <span data-ttu-id="d4545-106">如果使用者可以存取總管\*\*\*\* 功能區域，即可加入、刪除及更新此區域中的所有主要資料。</span><span class="sxs-lookup"><span data-stu-id="d4545-106">If the user has access to the **Explorer** functional area, the user can add, delete, and update all master data in this area.</span></span>  
  
-   <span data-ttu-id="d4545-107">如果使用者可以存取其他功能區域，即可執行該功能區域中的所有管理工作。</span><span class="sxs-lookup"><span data-stu-id="d4545-107">If the user has access to other functional areas, the user can perform all administrative tasks available in the functional area.</span></span>  
  
 <span data-ttu-id="d4545-108">每個模型可以有多個管理員。</span><span class="sxs-lookup"><span data-stu-id="d4545-108">Each model can have multiple administrators.</span></span> <span data-ttu-id="d4545-109">每個使用者都可以是 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 部署中一個、數個或所有模型的模型管理員。</span><span class="sxs-lookup"><span data-stu-id="d4545-109">Each user can be a model administrator for one, several, or all models in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] deployment.</span></span>  
  
 <span data-ttu-id="d4545-110">使用者可以在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 中或透過程式設計方式設定為模型管理員。</span><span class="sxs-lookup"><span data-stu-id="d4545-110">A user can be configured as a model administrator either in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] or programmatically.</span></span> <span data-ttu-id="d4545-111">如需詳細資訊，請參閱 [建立模型管理員 &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d4545-111">For more information, see [Create a Model Administrator &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md).</span></span>  
  
## <a name="master-data-services-system-administrator"></a><span data-ttu-id="d4545-112">Master Data Services 系統管理員</span><span class="sxs-lookup"><span data-stu-id="d4545-112">Master Data Services System Administrator</span></span>  
 <span data-ttu-id="d4545-113">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 系統管理員只有一個。</span><span class="sxs-lookup"><span data-stu-id="d4545-113">There is only one [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system administrator.</span></span> <span data-ttu-id="d4545-114">系統管理員是您在建立資料庫時，針對**Administrator 帳戶**指定的使用者 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="d4545-114">The system administrator is the user specified for the **Administrator Account** when you create the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span>  
  
 <span data-ttu-id="d4545-115">[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 系統管理員：</span><span class="sxs-lookup"><span data-stu-id="d4545-115">The [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] system administrator:</span></span>  
  
-   <span data-ttu-id="d4545-116">自動擁有所有功能區域的存取權。</span><span class="sxs-lookup"><span data-stu-id="d4545-116">Automatically has access to all functional areas.</span></span>  
  
-   <span data-ttu-id="d4545-117">可以在 [ **Explorer** ] 功能區域中加入、刪除及更新所有模型的所有主要資料。</span><span class="sxs-lookup"><span data-stu-id="d4545-117">Can add, delete, and update all master data for all models in the **Explorer** functional area.</span></span>  
  
 <span data-ttu-id="d4545-118">您可以變更指定為系統管理員的使用者。</span><span class="sxs-lookup"><span data-stu-id="d4545-118">You can change the user who is assigned as the system administrator.</span></span> <span data-ttu-id="d4545-119">如需詳細資訊，請參閱[將系統管理員帳戶變更 &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d4545-119">For more information, see [Change the System Administrator Account &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md).</span></span>  
  
## <a name="comparing-administrator-types"></a><span data-ttu-id="d4545-120">比較管理員類型</span><span class="sxs-lookup"><span data-stu-id="d4545-120">Comparing Administrator Types</span></span>  
  
|<span data-ttu-id="d4545-121">管理員類型</span><span class="sxs-lookup"><span data-stu-id="d4545-121">Administrator Type</span></span>|<span data-ttu-id="d4545-122">描述</span><span class="sxs-lookup"><span data-stu-id="d4545-122">Description</span></span>|  
|------------------------|-----------------|  
|[!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] <span data-ttu-id="d4545-123">系統管理員</span><span class="sxs-lookup"><span data-stu-id="d4545-123">system administrator</span></span>|<span data-ttu-id="d4545-124">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 中所指派權限不會影響系統管理員的存取。</span><span class="sxs-lookup"><span data-stu-id="d4545-124">Permissions assigned in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] have no effect on the administrator's access.</span></span><br /><br /> <span data-ttu-id="d4545-125">自動擁有所有模型的 [**更新**] 許可權。</span><span class="sxs-lookup"><span data-stu-id="d4545-125">Automatically has **Update** permission to all models.</span></span><br /><br /> <span data-ttu-id="d4545-126">自動擁有所有功能區域的存取權。</span><span class="sxs-lookup"><span data-stu-id="d4545-126">Automatically has access to all functional areas.</span></span><br /><br /> <span data-ttu-id="d4545-127">在 tblUser 中，[**識別碼**] 資料行中的值是**1**。</span><span class="sxs-lookup"><span data-stu-id="d4545-127">In mdm.tblUser, the value in the **ID** column is **1**.</span></span>|  
|<span data-ttu-id="d4545-128">模型管理員</span><span class="sxs-lookup"><span data-stu-id="d4545-128">Model administrator</span></span>|<span data-ttu-id="d4545-129">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 中指派的權限會決定使用者是否為模型管理員。</span><span class="sxs-lookup"><span data-stu-id="d4545-129">Permissions assigned in [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] determine whether or not the user is a model administrator.</span></span><br /><br /> <span data-ttu-id="d4545-130">根據明確指派的權限或繼承自群組的權限，使用者可以是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="d4545-130">Can be a model administrator based on permissions assigned explicitly or permissions inherited from a group.</span></span><br /><br /> <span data-ttu-id="d4545-131">只有在已指派最上層模型物件之**Update**許可權，且沒有其他許可權的模型，才是系統管理員。</span><span class="sxs-lookup"><span data-stu-id="d4545-131">Is an administrator only for models that have **Update** permission assigned to top-level model object, and no other permissions.</span></span><br /><br /> <span data-ttu-id="d4545-132">只能存取被授與存取權的功能區域。</span><span class="sxs-lookup"><span data-stu-id="d4545-132">Has access only to functional areas that access is granted to.</span></span><br /><br /> <span data-ttu-id="d4545-133">在 tblUser 中，[**識別碼**] 資料行中的值不是**1**。</span><span class="sxs-lookup"><span data-stu-id="d4545-133">In mdm.tblUser, the value in the **ID** column is not **1**.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d4545-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4545-134">See Also</span></span>  
 <span data-ttu-id="d4545-135">[建立模型系統管理員 &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d4545-135">[Create a Model Administrator &#40;Master Data Services&#41;](create-a-model-administrator-master-data-services.md) </span></span>  
 <span data-ttu-id="d4545-136">[變更系統管理員帳戶 &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d4545-136">[Change the System Administrator Account &#40;Master Data Services&#41;](../../2014/master-data-services/change-the-system-administrator-account-master-data-services.md) </span></span>  
 <span data-ttu-id="d4545-137">[建立 Master Data Services 資料庫](install-windows/create-a-master-data-services-database.md) </span><span class="sxs-lookup"><span data-stu-id="d4545-137">[Create a Master Data Services Database](install-windows/create-a-master-data-services-database.md) </span></span>  
 [<span data-ttu-id="d4545-138">通知 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d4545-138">Notifications &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/notifications-master-data-services.md)  
  
  
