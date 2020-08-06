---
title: 角色定義 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- roles [Reporting Services], security
- security [Reporting Services], role definitions
- role-based security [Reporting Services], role definitions
ms.assetid: d1b8dbf0-4462-402e-92dd-0e4835002b6e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 76fcb7f329f6afae890581e045ec64182972bf35
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596481"
---
# <a name="role-definitions"></a><span data-ttu-id="978f6-102">角色定義</span><span class="sxs-lookup"><span data-stu-id="978f6-102">Role Definitions</span></span>
  <span data-ttu-id="978f6-103">在中 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] ，*角色 \* \* 定義*是工作的命名集合，可定義報表伺服器上可用的作業。</span><span class="sxs-lookup"><span data-stu-id="978f6-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], a *role\*\*definition* is a named collection of tasks that define the operations available on a report server.</span></span> <span data-ttu-id="978f6-104">角色定義會提供報表伺服器用來強制執行安全性的規則。</span><span class="sxs-lookup"><span data-stu-id="978f6-104">Role definitions provide the rules used by the report server to enforce security.</span></span> <span data-ttu-id="978f6-105">當使用者嘗試執行工作 (例如發行報表) 時，報表伺服器就會檢查使用者的角色指派，以便判斷工作是否包含在其角色定義中。</span><span class="sxs-lookup"><span data-stu-id="978f6-105">When a user attempts to perform a task, such as publishing a report, the report server checks the user's role assignment to determine whether the task is included in their role definition.</span></span> <span data-ttu-id="978f6-106">如果工作包括在角色定義中，便會提交要求。</span><span class="sxs-lookup"><span data-stu-id="978f6-106">If the task is included in the role definition, the request is submitted.</span></span>  
  
## <a name="using-roles-to-authorize-access-to-a-report-server"></a><span data-ttu-id="978f6-107">使用角色來授權報表伺服器的存取權</span><span class="sxs-lookup"><span data-stu-id="978f6-107">Using Roles to Authorize Access to a Report Server</span></span>  
 <span data-ttu-id="978f6-108">當角色用於角色指派時，角色才成為可以作業。</span><span class="sxs-lookup"><span data-stu-id="978f6-108">A role becomes operative only when it is used in a role assignment.</span></span> <span data-ttu-id="978f6-109">如需角色如何提供安全性的詳細資訊，請參閱 [角色指派](role-assignments.md)。</span><span class="sxs-lookup"><span data-stu-id="978f6-109">For more information about how roles provide security, see [Role Assignments](role-assignments.md).</span></span>  
  
## <a name="types-of-role-definitions"></a><span data-ttu-id="978f6-110">角色定義的類型</span><span class="sxs-lookup"><span data-stu-id="978f6-110">Types of Role Definitions</span></span>  
 <span data-ttu-id="978f6-111">角色定義是項目層級或系統層級定義。</span><span class="sxs-lookup"><span data-stu-id="978f6-111">Role definitions are either item-level or system-level definitions.</span></span> <span data-ttu-id="978f6-112">「項目層級角色定義」  會描述與報表伺服器上儲存和管理之項目 (例如報表、資料夾和模型) 相關的工作。</span><span class="sxs-lookup"><span data-stu-id="978f6-112">An *item-level role definition* describes tasks that relate to items that are stored and managed on a report server, such as reports, folder, and models.</span></span> <span data-ttu-id="978f6-113">管理報表、檢視資料夾和管理個別訂閱都是您可以包含在項目層級角色定義中的工作範例。</span><span class="sxs-lookup"><span data-stu-id="978f6-113">Manage reports, View folders, and Manage individual subscriptions are examples of tasks you can include in an item-level role definitions.</span></span> <span data-ttu-id="978f6-114">「系統角色定義」  包含套用至整個網站的工作。</span><span class="sxs-lookup"><span data-stu-id="978f6-114">A *system role definition* includes tasks that apply to the site as a whole.</span></span> <span data-ttu-id="978f6-115">檢視報表伺服器屬性是您可能會包含在系統角色中的工作範例。</span><span class="sxs-lookup"><span data-stu-id="978f6-115">View report server properties is an example of a task you might include in a system role.</span></span>  
  
## <a name="predefined-roles"></a><span data-ttu-id="978f6-116">Predefined Roles</span><span class="sxs-lookup"><span data-stu-id="978f6-116">Predefined Roles</span></span>  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="978f6-117">包括一些對應至不同使用者互動層級的預先定義角色。</span><span class="sxs-lookup"><span data-stu-id="978f6-117">includes predefined roles that correspond to different levels of user interaction.</span></span> <span data-ttu-id="978f6-118">下列清單含有您可以使用的預先定義角色：</span><span class="sxs-lookup"><span data-stu-id="978f6-118">The following list contains the predefined roles you can use:</span></span>  
  
-   <span data-ttu-id="978f6-119">「內容管理員」、「發行者」、「瀏覽者」、「報表產生器」和「我的報表」都是您可以在建立存取報表伺服器內容之角色指派時使用的項目層級角色定義。</span><span class="sxs-lookup"><span data-stu-id="978f6-119">Content Manager, Publisher, Browser, Report Builder, and My Reports are item-level role definitions that you can use when creating role assignments for accessing report server content.</span></span>  
  
-   <span data-ttu-id="978f6-120">「系統管理員」和「系統使用者」是您可以用來授權站台作業存取權的系統層級角色定義。</span><span class="sxs-lookup"><span data-stu-id="978f6-120">System Administrator and System User are system-level role definitions that you can use to authorize access to site operations.</span></span>  
  
 <span data-ttu-id="978f6-121">如需這些預先定義角色的詳細資訊，請參閱 [Predefined Roles](role-definitions-predefined-roles.md)(預先定義的角色)。</span><span class="sxs-lookup"><span data-stu-id="978f6-121">For more information, see [Predefined Roles](role-definitions-predefined-roles.md).</span></span>  
  
## <a name="creating-a-role-definition"></a><span data-ttu-id="978f6-122">建立角色定義</span><span class="sxs-lookup"><span data-stu-id="978f6-122">Creating a Role Definition</span></span>  
 <span data-ttu-id="978f6-123">若要建立角色，請使用 Management Studio 來指定名稱以及它所包含的工作。</span><span class="sxs-lookup"><span data-stu-id="978f6-123">To create a role, you use Management Studio to specify a name and tasks it contains.</span></span> <span data-ttu-id="978f6-124">您必須針對項目和系統工作建立不同的角色定義。</span><span class="sxs-lookup"><span data-stu-id="978f6-124">You must create separate role definition for item and system tasks.</span></span> <span data-ttu-id="978f6-125">角色可以包含項目層級工作或系統層級工作，但是不能同時包含兩者。</span><span class="sxs-lookup"><span data-stu-id="978f6-125">Roles can include item-level tasks or system-level tasks, but not both.</span></span> <span data-ttu-id="978f6-126">建立角色定義包括提供一個名稱，以及選擇一組定義的工作。</span><span class="sxs-lookup"><span data-stu-id="978f6-126">Creating a role definition consists of providing a name and choosing a set of tasks for the definition.</span></span> <span data-ttu-id="978f6-127">若要建立角色定義，您必須要有相關的權限。</span><span class="sxs-lookup"><span data-stu-id="978f6-127">To create a role definition, you must have permission to do so.</span></span> <span data-ttu-id="978f6-128">「設定個別項目的安全性」工作會提供這些權限。</span><span class="sxs-lookup"><span data-stu-id="978f6-128">The "Set security for individual items" task provides these permissions.</span></span> <span data-ttu-id="978f6-129">依預設，指派至預先定義之 **內容管理員** 角色的使用者和管理員，可以執行此工作。</span><span class="sxs-lookup"><span data-stu-id="978f6-129">By default, administrators and users who are assigned to the predefined **Content Manager** role can perform this task.</span></span>  
  
 <span data-ttu-id="978f6-130">角色必須有唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="978f6-130">A role must have a unique name.</span></span> <span data-ttu-id="978f6-131">有效的角色定義，至少必須包含一項工作。</span><span class="sxs-lookup"><span data-stu-id="978f6-131">To be valid, the role definition must contain at least one task.</span></span> <span data-ttu-id="978f6-132">如需詳細資訊，請參閱 [工作和權限](tasks-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="978f6-132">For more information, see [Tasks and Permissions](tasks-and-permissions.md).</span></span>  
  
 <span data-ttu-id="978f6-133">若要建立角色定義，請使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="978f6-133">To create a role definition, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="978f6-134">如需這些預先定義角色的詳細資訊，請參閱 [建立、刪除或修改角色 &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md)。</span><span class="sxs-lookup"><span data-stu-id="978f6-134">For more information, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md).</span></span>  
  
 <span data-ttu-id="978f6-135">建立角色定義之後，您可以在角色指派中選取該定義，藉以使用它。</span><span class="sxs-lookup"><span data-stu-id="978f6-135">After you create a role definition, you can use it by selecting it in a role assignment.</span></span> <span data-ttu-id="978f6-136">如需這些預先定義角色的詳細資訊，請參閱 [將報表伺服器的存取權授與使用者 &#40;報表管理員&#41;](grant-user-access-to-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="978f6-136">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md).</span></span>  
  
## <a name="customize-or-delete-a-role-definition"></a><span data-ttu-id="978f6-137">自訂或刪除角色定義</span><span class="sxs-lookup"><span data-stu-id="978f6-137">Customize or Delete a Role Definition</span></span>  
 <span data-ttu-id="978f6-138">您可以修改預先定義的角色，也可以使用自訂角色來取代它們。</span><span class="sxs-lookup"><span data-stu-id="978f6-138">Predefined roles can be modified or replaced with custom roles.</span></span> <span data-ttu-id="978f6-139">若要修改角色，請在角色定義中加入或移除工作。</span><span class="sxs-lookup"><span data-stu-id="978f6-139">To modify a role, you add to or remove tasks from the role definition.</span></span> <span data-ttu-id="978f6-140">但是，您無法重新命名角色。</span><span class="sxs-lookup"><span data-stu-id="978f6-140">You cannot rename a role.</span></span> <span data-ttu-id="978f6-141">您所做的任何變更都會立即套用至包含該角色定義的所有角色指派。</span><span class="sxs-lookup"><span data-stu-id="978f6-141">Any changes you make are applied immediately to all role assignments that include the role definition.</span></span>  
  
 <span data-ttu-id="978f6-142">如果您不要再使用某個角色定義，就可以刪除它。</span><span class="sxs-lookup"><span data-stu-id="978f6-142">You can delete a role definition if you are no longer using it.</span></span> <span data-ttu-id="978f6-143">只要已啟用 [我的報表] 功能，便無法刪除為 [我的報表] 功能選取的角色定義。</span><span class="sxs-lookup"><span data-stu-id="978f6-143">You cannot delete the role definition that is selected for the My Reports feature as long as that feature is enabled.</span></span> <span data-ttu-id="978f6-144">在刪除用於 [我的報表] 的角色定義之前，您必須先停用該功能，或者選取其他角色定義。</span><span class="sxs-lookup"><span data-stu-id="978f6-144">Before you can delete the role definition used for My Reports, you must first disable the feature or select a different role definition to use with it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="978f6-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="978f6-145">See Also</span></span>  
 <span data-ttu-id="978f6-146">[工作和權限](tasks-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="978f6-146">[Tasks and Permissions](tasks-and-permissions.md) </span></span>  
 <span data-ttu-id="978f6-147">[在原生模式報表伺服器上授與權限](granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="978f6-147">[Granting Permissions on a Native Mode Report Server](granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="978f6-148">[建立、刪除或修改角色 &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md) </span><span class="sxs-lookup"><span data-stu-id="978f6-148">[Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md) </span></span>  
 <span data-ttu-id="978f6-149">[將報表伺服器的存取權授與使用者 &#40;報表管理員&#41;](grant-user-access-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="978f6-149">[Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) </span></span>  
 <span data-ttu-id="978f6-150">[修改或刪除角色指派 &#40;報表管理員&#41;](role-assignments-modify-or-delete.md) </span><span class="sxs-lookup"><span data-stu-id="978f6-150">[Modify or Delete a Role Assignment &#40;Report Manager&#41;](role-assignments-modify-or-delete.md) </span></span>  
 [<span data-ttu-id="978f6-151">設定 SharePoint 網站上報表伺服器項目的權限 &#40;SharePoint 整合模式的 Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="978f6-151">Set Permissions for Report Server Items on a SharePoint Site &#40;Reporting Services in SharePoint Integrated Mode&#41;</span></span>](set-permissions-for-report-server-items-on-a-sharepoint-site.md)  
  
  
