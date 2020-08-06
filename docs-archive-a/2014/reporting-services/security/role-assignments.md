---
title: 角色指派 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- users [Reporting Services]
- roles [Reporting Services]
- role-based security [Reporting Services], role assignments
- groups [Reporting Services]
- security [Reporting Services], role assignments
ms.assetid: 600e112c-1897-48a6-93c0-6e9f3f12dc01
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: f156a009dfce8d91c3d3c8460160a4fdad62b573
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596484"
---
# <a name="role-assignments"></a><span data-ttu-id="47779-102">角色指派</span><span class="sxs-lookup"><span data-stu-id="47779-102">Role Assignments</span></span>
  <span data-ttu-id="47779-103">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中，「角色指派」  會決定預存項目以及報表伺服器本身的存取權。</span><span class="sxs-lookup"><span data-stu-id="47779-103">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], *role assignments* determine access to stored items and to the report server itself.</span></span> <span data-ttu-id="47779-104">角色指派包含下列部份：</span><span class="sxs-lookup"><span data-stu-id="47779-104">A role assignment has the following parts:</span></span>  
  
-   <span data-ttu-id="47779-105">您想要控制存取權的安全性實體項目。</span><span class="sxs-lookup"><span data-stu-id="47779-105">A securable item for which you want to control access.</span></span> <span data-ttu-id="47779-106">安全性實體項目的範例包括資料夾、報表和資源。</span><span class="sxs-lookup"><span data-stu-id="47779-106">Examples of securable items include folders, reports, and resources.</span></span>  
  
-   <span data-ttu-id="47779-107">可以利用 Windows 安全性，或其他驗證機制驗證的使用者或群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="47779-107">A user or group account that can be authenticated by Windows security or another authentication mechanism.</span></span>  
  
-   <span data-ttu-id="47779-108">定義一組工作的角色定義。</span><span class="sxs-lookup"><span data-stu-id="47779-108">Role definitions that define a set of tasks.</span></span> <span data-ttu-id="47779-109">角色定義的範例包括 **系統管理員**、 **內容管理員**和 **發行者**。</span><span class="sxs-lookup"><span data-stu-id="47779-109">Examples of role definitions include **System Administrator**, **Content Manager**, and **Publisher**.</span></span>  
  
 <span data-ttu-id="47779-110">角色指派會在資料夾階層中繼承。</span><span class="sxs-lookup"><span data-stu-id="47779-110">Role assignments are inherited within the folder hierarchy.</span></span> <span data-ttu-id="47779-111">資料夾中包含的所有報表、共用資料來源、資源以及子資料夾，會自動繼承針對該資料夾定義的角色指派。</span><span class="sxs-lookup"><span data-stu-id="47779-111">The role assignment that is defined for a folder is automatically inherited by all reports, shared data sources, resources, and subfolders contained within that folder.</span></span> <span data-ttu-id="47779-112">您可以為個別項目定義角色指派，以覆寫繼承的安全性。</span><span class="sxs-lookup"><span data-stu-id="47779-112">You can override inherited security by defining role assignments for individual items.</span></span> <span data-ttu-id="47779-113">至少要有一個角色指派，以保護資料夾階層中所有的部份。</span><span class="sxs-lookup"><span data-stu-id="47779-113">All parts of the folder hierarchy must be secured by at least one role assignment.</span></span> <span data-ttu-id="47779-114">您不能建立非安全項目，或者以產生非安全項目的方式來操作設定。</span><span class="sxs-lookup"><span data-stu-id="47779-114">You cannot create an unsecured item or manipulate settings in a way that produces an unsecured item.</span></span>  
  
 <span data-ttu-id="47779-115">下圖描述將一個群組和一個特定使用者對應至資料夾 B 之 **發行者** 角色的角色指派。</span><span class="sxs-lookup"><span data-stu-id="47779-115">The following diagram illustrates a role assignment that maps a group and a specific user to the **Publisher** role for Folder B.</span></span>  
  
 <span data-ttu-id="47779-116">![角色指派圖表](../media/report-securityarch.gif "角色指派圖表")</span><span class="sxs-lookup"><span data-stu-id="47779-116">![Role assignments diagram](../media/report-securityarch.gif "Role assignments diagram")</span></span>  
<span data-ttu-id="47779-117">角色指派圖表</span><span class="sxs-lookup"><span data-stu-id="47779-117">Role assignments diagram</span></span>  
  
## <a name="system-level-and-item-level-role-assignments"></a><span data-ttu-id="47779-118">系統層級與項目層級角色指派</span><span class="sxs-lookup"><span data-stu-id="47779-118">System-Level and Item-Level Role Assignments</span></span>  
 <span data-ttu-id="47779-119">在 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 中以角色為基礎的安全性會組織成下列層級：</span><span class="sxs-lookup"><span data-stu-id="47779-119">Role-based security in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is organized into the following levels:</span></span>  
  
-   <span data-ttu-id="47779-120">項目層級角色指派會控制報表伺服器資料夾階層中之報表、資料夾、報表模型、共用資料來源以及資源的存取權。</span><span class="sxs-lookup"><span data-stu-id="47779-120">Item-level role assignments control access to reports, folders, report models, shared data sources, and resources in the report server folder hierarchy.</span></span> <span data-ttu-id="47779-121">在特定項目或 [主資料夾] 資料夾上建立角色指派時，會定義項目層級角色指派。</span><span class="sxs-lookup"><span data-stu-id="47779-121">Item-level role assignments are defined when create a role assignment on a specific item or on the Home folder.</span></span>  
  
-   <span data-ttu-id="47779-122">系統角色指派會授權範圍遍及整個伺服器的作業 (例如，管理作業的能力就是系統層級作業)。</span><span class="sxs-lookup"><span data-stu-id="47779-122">System role assignments authorize operations that are scoped to the server as a whole (for example, the ability to manage jobs is a system level operation).</span></span> <span data-ttu-id="47779-123">系統角色指派不等於系統管理員。</span><span class="sxs-lookup"><span data-stu-id="47779-123">A system role assignment is not the equivalent of a system administrator.</span></span> <span data-ttu-id="47779-124">它並未授與完全控制報表伺服器的進階權限。</span><span class="sxs-lookup"><span data-stu-id="47779-124">It does not confer advanced permissions that grant full control of a report server.</span></span>  
  
 <span data-ttu-id="47779-125">系統角色指派不會授權資料夾階層中之項目的存取權。</span><span class="sxs-lookup"><span data-stu-id="47779-125">A system role assignment does not authorize access to items in the folder hierarchy.</span></span> <span data-ttu-id="47779-126">系統與項目安全性互斥。</span><span class="sxs-lookup"><span data-stu-id="47779-126">System and item security are mutually exclusive.</span></span> <span data-ttu-id="47779-127">針對任何給定使用者或群組，您可能需要建立系統層級與項目層級角色指派，以提供足夠的存取權給報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="47779-127">For any given user or group, you might need to create both a system-level and item-level role assignment to provide sufficient access to a report server.</span></span>  
  
## <a name="users-and-groups-in-role-assignments"></a><span data-ttu-id="47779-128">角色指派中的使用者與群組</span><span class="sxs-lookup"><span data-stu-id="47779-128">Users and Groups in Role Assignments</span></span>  
 <span data-ttu-id="47779-129">您在角色指派中指定的使用者或群組帳戶屬於網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="47779-129">The users or group accounts that you specify in role assignments are domain accounts.</span></span> <span data-ttu-id="47779-130">報表伺服器會從 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows 網域 (如果您是使用自訂安全性延伸模組，則為另一個安全性模型) 參考 (但不會建立或管理) 使用者與群組。</span><span class="sxs-lookup"><span data-stu-id="47779-130">The report server references, but does not create or manage, users and groups from a [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows domain (or another security model if you are using a custom security extension).</span></span>  
  
 <span data-ttu-id="47779-131">在套用至任何給定項目的所有角色指派中，不會有兩個可以指定相同使用者或群組。</span><span class="sxs-lookup"><span data-stu-id="47779-131">Of all the role assignments that apply to any given item, no two can specify the same user or group.</span></span> <span data-ttu-id="47779-132">如果使用者帳戶也是群組帳戶的成員，而二者皆有角色指派，則兩個角色指派結合的工作皆可供使用者使用。</span><span class="sxs-lookup"><span data-stu-id="47779-132">If a user account is also a member of a group account, and you have role assignments for both, the combined set of tasks for both role assignments are available to the user.</span></span>  
  
 <span data-ttu-id="47779-133">您將使用者加入至已經是角色指派之一部份的群組時，必須重設 Internet Information Services (IIS)，該使用者的新角色指派才會生效。</span><span class="sxs-lookup"><span data-stu-id="47779-133">When you add a user to a group that is already part of a role assignment, you must reset Internet Information Services (IIS) for the new role assignment to take effect for that user.</span></span>  
  
## <a name="predefined-role-assignments"></a><span data-ttu-id="47779-134">預先定義的角色指派</span><span class="sxs-lookup"><span data-stu-id="47779-134">Predefined Role Assignments</span></span>  
 <span data-ttu-id="47779-135">依預設，會實作預先定義的角色指派，讓本機管理員可以管理報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="47779-135">By default, predefined role assignments are implemented that allow local administrators to manage the report server.</span></span> <span data-ttu-id="47779-136">您必須加入其他角色指派，將存取權授與其他使用者。</span><span class="sxs-lookup"><span data-stu-id="47779-136">You must add additional role assignments to grant access to other users.</span></span>  
  
 <span data-ttu-id="47779-137">如需提供預設安全性之預先定義角色指派的詳細資訊，請參閱 [預先定義的角色](role-definitions-predefined-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="47779-137">For more information about the predefined role assignments that provide default security, see [Predefined Roles](role-definitions-predefined-roles.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47779-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="47779-138">See Also</span></span>  
 <span data-ttu-id="47779-139">[建立、刪除或修改角色 &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md) </span><span class="sxs-lookup"><span data-stu-id="47779-139">[Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md) </span></span>  
 <span data-ttu-id="47779-140">[授與使用者對報表伺服器的存取權 &#40;報表管理員&#41;](grant-user-access-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="47779-140">[Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) </span></span>  
 <span data-ttu-id="47779-141">[修改或刪除角色指派 &#40;報表管理員&#41;](role-assignments-modify-or-delete.md) </span><span class="sxs-lookup"><span data-stu-id="47779-141">[Modify or Delete a Role Assignment &#40;Report Manager&#41;](role-assignments-modify-or-delete.md) </span></span>  
 <span data-ttu-id="47779-142">[在 sharepoint 網站上設定報表伺服器專案的許可權 &#40;SharePoint 整合模式中的 Reporting Services&#41;](set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="47779-142">[Set Permissions for Report Server Items on a SharePoint Site &#40;Reporting Services in SharePoint Integrated Mode&#41;](set-permissions-for-report-server-items-on-a-sharepoint-site.md) </span></span>  
 [<span data-ttu-id="47779-143">在原生模式報表伺服器上授與權限</span><span class="sxs-lookup"><span data-stu-id="47779-143">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
