---
title: 在原生模式報表伺服器上授與權限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- authorization [Reporting Services]
- server security [Reporting Services]
- role-based security [Reporting Services]
- items [Reporting Services], security
- permissions [Reporting Services], native mode
- published reports [Reporting Services], security
- reports [Reporting Services], security
- report items [Reporting Services], security
- role-based security [Reporting Services], about role-based security
- security [Reporting Services], role-based
ms.assetid: 260dc2e9-546c-4f04-9fa1-977e23c9d68c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 22967a7c9c6b8cc3e14ecffed117d1ab821788f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606068"
---
# <a name="granting-permissions-on-a-native-mode-report-server"></a><span data-ttu-id="49f0c-102">在原生模式報表伺服器上授與權限</span><span class="sxs-lookup"><span data-stu-id="49f0c-102">Granting Permissions on a Native Mode Report Server</span></span>
  <span data-ttu-id="49f0c-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 會使用以角色為基礎的授權和驗證子系統來決定能夠在報表伺服器上執行作業及存取項目的人員。</span><span class="sxs-lookup"><span data-stu-id="49f0c-103">SQL Server [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] uses role-based authorization and an authentication subsystem to determine who can perform operations and access items on a report server.</span></span> <span data-ttu-id="49f0c-104">以角色為基礎的授權，將使用者或群組可以執行的動作集分類成角色。</span><span class="sxs-lookup"><span data-stu-id="49f0c-104">Role-based authorization categorizes into roles the set of actions that a user or group can perform.</span></span> <span data-ttu-id="49f0c-105">驗證是以內建的 Windows 驗證或您提供的自訂驗證模組為基礎。</span><span class="sxs-lookup"><span data-stu-id="49f0c-105">Authentication is based on built-in Windows Authentication or a custom authentication module that you provide.</span></span> <span data-ttu-id="49f0c-106">您可以使用預先定義或自訂的角色搭配任何一種驗證類型。</span><span class="sxs-lookup"><span data-stu-id="49f0c-106">You can use predefined or custom roles with either authentication type.</span></span>  
  
## <a name="using-roles-to-grant-report-server-access"></a><span data-ttu-id="49f0c-107">使用角色來授與報表伺服器存取權</span><span class="sxs-lookup"><span data-stu-id="49f0c-107">Using Roles to Grant Report Server Access</span></span>  
 <span data-ttu-id="49f0c-108">所有使用者都會在定義特定存取層級的角色內容中與報表伺服器進行互動。</span><span class="sxs-lookup"><span data-stu-id="49f0c-108">All users interact with a report server within the context of a role that defines a specific level of access.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="49f0c-109">包含了一些預先定義的角色，而且您可以將這些角色指派給使用者和群組，以便提供報表伺服器的立即存取權。</span><span class="sxs-lookup"><span data-stu-id="49f0c-109">includes predefined roles that you can assign to users and groups to provide immediate access to a report server.</span></span> <span data-ttu-id="49f0c-110">**ContentManager**、 **Publisher**和 **Browser** 是預先定義角色的範例。</span><span class="sxs-lookup"><span data-stu-id="49f0c-110">**ContentManager**, **Publisher**, and **Browser** are examples of predefined roles.</span></span> <span data-ttu-id="49f0c-111">每個角色都會定義相關工作的集合。</span><span class="sxs-lookup"><span data-stu-id="49f0c-111">Each role defines a collection of related tasks.</span></span> <span data-ttu-id="49f0c-112">例如， **發行者** 擁有加入報表以及建立儲存這些報表之資料夾的權限。</span><span class="sxs-lookup"><span data-stu-id="49f0c-112">For example, a **Publisher** has permission to add reports and create folders for storing those reports.</span></span>  
  
 <span data-ttu-id="49f0c-113">雖然角色指派通常是從父節點所繼承的，但是您也可以透過針對特定項目建立新的角色指派，中斷權限繼承。</span><span class="sxs-lookup"><span data-stu-id="49f0c-113">Role assignments are typically inherited from a parent node, but you can break permission inheritance by creating a new role assignment for a particular item.</span></span> <span data-ttu-id="49f0c-114">屬於某份報表之 **內容管理員** 角色成員的使用者可能是另一份報表之 **瀏覽者** 角色的成員。</span><span class="sxs-lookup"><span data-stu-id="49f0c-114">A user who is a member of the **Content Manager** role for one report may be a member of the **Browser** role for another report.</span></span>  
  
 <span data-ttu-id="49f0c-115">若要授與報表伺服器項目和作業的存取權，請遵循下列指導方針：</span><span class="sxs-lookup"><span data-stu-id="49f0c-115">To grant access to report server items and operations, follow these guidelines:</span></span>  
  
1.  <span data-ttu-id="49f0c-116">檢閱預先定義的角色來判斷您是否能夠依原狀使用它們。</span><span class="sxs-lookup"><span data-stu-id="49f0c-116">Review the predefined roles to determine whether you can use them as is.</span></span> <span data-ttu-id="49f0c-117">如果您需要調整工作或定義其他角色，就應該先進行這些作業，然後再指派使用者至特定角色。</span><span class="sxs-lookup"><span data-stu-id="49f0c-117">If you need to adjust the tasks or define additional roles, you should do this before you begin assigning users to specific roles.</span></span> <span data-ttu-id="49f0c-118">如需各個角色的詳細資訊，請參閱 [Predefined Roles](role-definitions-predefined-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="49f0c-118">For more information about each role, see [Predefined Roles](role-definitions-predefined-roles.md).</span></span>  
  
2.  <span data-ttu-id="49f0c-119">確認哪些使用者和群組需要存取報表伺服器，以及所存取的層級。</span><span class="sxs-lookup"><span data-stu-id="49f0c-119">Identify which users and groups require access to the report server, and at what level.</span></span> <span data-ttu-id="49f0c-120">多數使用者都應指派至 **[瀏覽者]** 角色或 **[報表產生器]** 角色。</span><span class="sxs-lookup"><span data-stu-id="49f0c-120">Most users should be assigned to the **Browser** role or the **Report Builder** role.</span></span> <span data-ttu-id="49f0c-121">**[發行者]** 角色則應指派給較少數的使用者。</span><span class="sxs-lookup"><span data-stu-id="49f0c-121">A smaller number of users should be assigned to the **Publisher** role.</span></span> <span data-ttu-id="49f0c-122">只有非常少數的使用者才應指派至 **[內容管理員]**。</span><span class="sxs-lookup"><span data-stu-id="49f0c-122">Very few users should be assigned to **Content Manager**.</span></span>  
  
3.  <span data-ttu-id="49f0c-123">您可以使用報表管理員，針對需要存取權的每個使用者或群組，指派 [主資料夾] 資料夾 (這是報表伺服器資料夾階層的最上層資料夾) 的角色。</span><span class="sxs-lookup"><span data-stu-id="49f0c-123">Use Report Manager to assign roles on the Home folder (this is the top-level folder of the report server folder hierarchy) for each user or group who requires access.</span></span>  
  
4.  <span data-ttu-id="49f0c-124">在網站層級，於報表管理員的 [網站設定] 頁面上，使用 **系統使用者** 和 **系統管理員**等預先定義的角色，為每個使用者或群組建立系統層級角色指派。</span><span class="sxs-lookup"><span data-stu-id="49f0c-124">At the site level, on the Site Settings page in Report Manager, create a system-level role assignment for each user and group using the predefined roles **System User** and **System Administrator**.</span></span>  
  
5.  <span data-ttu-id="49f0c-125">視需要針對特定資料夾、報表和其他項目建立其他角色指派。</span><span class="sxs-lookup"><span data-stu-id="49f0c-125">Create additional role assignments as needed for specific folders, reports, and other items.</span></span> <span data-ttu-id="49f0c-126">請避免建立大量角色指派。</span><span class="sxs-lookup"><span data-stu-id="49f0c-126">Avoid creating a large number of role assignments.</span></span> <span data-ttu-id="49f0c-127">如果您建立過多角色指派，可能會難以針對每個使用者追蹤不同的權限層級。</span><span class="sxs-lookup"><span data-stu-id="49f0c-127">If you create too many, it will be difficult to keep track of the different permission levels for each user.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="49f0c-128">如果您設定報表伺服器在 SharePoint 整合模式中執行，您必須在 SharePoint 網站上設定權限，授與報表伺服器項目的存取權。</span><span class="sxs-lookup"><span data-stu-id="49f0c-128">If you configured a report server to run in SharePoint integrated mode, you must set permissions on the SharePoint site to grant access to report server items.</span></span> <span data-ttu-id="49f0c-129">如需詳細資訊，請參閱 [授與 SharePoint 網站上報表伺服器項目的權限](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)。</span><span class="sxs-lookup"><span data-stu-id="49f0c-129">For more information, see [Granting Permissions on Report Server Items on a SharePoint Site](granting-permissions-on-report-server-items-on-a-sharepoint-site.md).</span></span>  
  
## <a name="who-sets-permissions"></a><span data-ttu-id="49f0c-130">誰設定權限</span><span class="sxs-lookup"><span data-stu-id="49f0c-130">Who Sets Permissions</span></span>  
 <span data-ttu-id="49f0c-131">一開始，只有屬於本機管理員群組成員的使用者可以存取報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="49f0c-131">Initially, only users who are members of the local administrators group can access a report server.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="49f0c-132">已安裝二個預設角色指派，其將項目層級及系統層級的存取權授與本機管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="49f0c-132">is installed with two default role assignments that grant item-level and system-level access to members of the local administrators group.</span></span> <span data-ttu-id="49f0c-133">本機系統管理員可以使用這些內建角色指派，將報表伺服器存取權授與其他使用者，並管理報表伺服器專案。</span><span class="sxs-lookup"><span data-stu-id="49f0c-133">Local Administrators can use these built-in role assignments to grant report server access to other users and manage report server items.</span></span> <span data-ttu-id="49f0c-134">您無法刪除內建的角色指派。</span><span class="sxs-lookup"><span data-stu-id="49f0c-134">The built-in role assignments cannot be deleted.</span></span> <span data-ttu-id="49f0c-135">本機管理員一律擁有完全管理報表伺服器執行個體的權限。</span><span class="sxs-lookup"><span data-stu-id="49f0c-135">A local administrator always has permission to fully manage a report server instance.</span></span>  
 
 <span data-ttu-id="49f0c-136">您必須進行其他組態設定，然後才能管理執行 Windows Vista 或 Windows Server 2008 之本機電腦上的報表伺服器執行個體。</span><span class="sxs-lookup"><span data-stu-id="49f0c-136">Additional configuration is required before you can administer a report server instance on a local computer that runs Windows Vista or Windows Server 2008.</span></span> <span data-ttu-id="49f0c-137">如需詳細資訊，請參閱 [設定原生模式報表伺服器進行本機管理 &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="49f0c-137">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
## <a name="how-permissions-are-stored"></a><span data-ttu-id="49f0c-138">權限的儲存方式</span><span class="sxs-lookup"><span data-stu-id="49f0c-138">How Permissions are Stored</span></span>  
 <span data-ttu-id="49f0c-139">角色指派和定義會儲存在報表伺服器資料庫中。</span><span class="sxs-lookup"><span data-stu-id="49f0c-139">Role assignments and definitions are stored in the report server database.</span></span> <span data-ttu-id="49f0c-140">如果您要使用各種用戶端工具或程式設計介面，所有存取方式都會受限於針對整個報表伺服器執行個體定義的權限。</span><span class="sxs-lookup"><span data-stu-id="49f0c-140">If you are using variety of client tools or programmatic interfaces, all access is subject to the permissions that are defined for the report server instance as a whole.</span></span> <span data-ttu-id="49f0c-141">如果您在向外延展部署中設定多部報表伺服器，那麼在其中一個執行個體上定義的角色指派會儲存在共用資料庫中，提供給相同向外延展部署中的所有其他執行個體使用。</span><span class="sxs-lookup"><span data-stu-id="49f0c-141">If you are configuring multiple report servers in a scale-out-deployment, the role assignments that you define on one instance are stored in a shared database and used by all the other instances in the same scale-out deployment.</span></span> <span data-ttu-id="49f0c-142">由於角色指派會與它們保護的項目一起儲存，因此您可以將資料庫移至其他報表伺服器執行個體，而不會遺失您所定義的權限。</span><span class="sxs-lookup"><span data-stu-id="49f0c-142">Because role assignments are stored with the items they secure, you can move the database to another report server instance without losing the permissions you defined.</span></span>  
  
## <a name="tasks-and-tools-for-managing-permissions"></a><span data-ttu-id="49f0c-143">管理權限的工作和工具</span><span class="sxs-lookup"><span data-stu-id="49f0c-143">Tasks and tools for Managing Permissions</span></span>  
 <span data-ttu-id="49f0c-144">您可以使用下列工具來管理角色定義和指派。</span><span class="sxs-lookup"><span data-stu-id="49f0c-144">Use the following tools to manage role definitions and assignments.</span></span>  
  
|<span data-ttu-id="49f0c-145">工具</span><span class="sxs-lookup"><span data-stu-id="49f0c-145">Tool</span></span>|<span data-ttu-id="49f0c-146">工作</span><span class="sxs-lookup"><span data-stu-id="49f0c-146">Tasks</span></span>|  
|----------|-----------|  
|<span data-ttu-id="49f0c-147">Management Studio - 用於檢視、修改、建立和刪除角色定義。</span><span class="sxs-lookup"><span data-stu-id="49f0c-147">Management Studio - Used to view, modify, create, and delete role definitions.</span></span>|[<span data-ttu-id="49f0c-148">建立、刪除或修改角色 &#40;Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="49f0c-148">Create, Delete, or Modify a Role &#40;Management Studio&#41;</span></span>](role-definitions-create-delete-or-modify.md)|  
|<span data-ttu-id="49f0c-149">報表管理員 - 用於指派使用者和群組給角色。</span><span class="sxs-lookup"><span data-stu-id="49f0c-149">Report Manager - Used to assign users and groups to roles.</span></span>|[<span data-ttu-id="49f0c-150">將報表伺服器的存取權授與使用者 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="49f0c-150">Grant User Access to a Report Server &#40;Report Manager&#41;</span></span>](grant-user-access-to-a-report-server.md)<br /><br /> [<span data-ttu-id="49f0c-151">修改或刪除角色指派 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="49f0c-151">Modify or Delete a Role Assignment &#40;Report Manager&#41;</span></span>](role-assignments-modify-or-delete.md)|  
  
## <a name="see-also"></a><span data-ttu-id="49f0c-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="49f0c-152">See Also</span></span>  
 <span data-ttu-id="49f0c-153">[預先定義的角色](role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="49f0c-153">[Predefined Roles](role-definitions-predefined-roles.md) </span></span>  
 <span data-ttu-id="49f0c-154">[授與 SharePoint 網站上報表伺服器專案的許可權](granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span><span class="sxs-lookup"><span data-stu-id="49f0c-154">[Granting Permissions on Report Server Items on a SharePoint Site](granting-permissions-on-report-server-items-on-a-sharepoint-site.md) </span></span>  
 <span data-ttu-id="49f0c-155">[使用報表伺服器驗證](authentication-with-the-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="49f0c-155">[Authentication with the Report Server](authentication-with-the-report-server.md) </span></span>  
 <span data-ttu-id="49f0c-156"> (create-and-manage-role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="49f0c-156">(create-and-manage-role-assignments.md)</span></span>   
 <span data-ttu-id="49f0c-157">[Reporting Services 的安全性與保護](reporting-services-security-and-protection.md) </span><span class="sxs-lookup"><span data-stu-id="49f0c-157">[Reporting Services Security and Protection](reporting-services-security-and-protection.md) </span></span>  
 [<span data-ttu-id="49f0c-158">報表伺服器內容管理 &#40;SSRS 原生模式&#41;</span><span class="sxs-lookup"><span data-stu-id="49f0c-158">Report Server Content Management &#40;SSRS Native Mode&#41;</span></span>](../report-server/report-server-content-management-ssrs-native-mode.md)  
  
  
