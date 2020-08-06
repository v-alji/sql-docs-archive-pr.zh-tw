---
title: 安全性頁面 (站台設定， 報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: acc9a905-90f8-4544-aec6-b2ab3a1b0015
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 997806b8bba92d210a8d108a7101e086f21abb74
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594376"
---
# <a name="security-page-site-settings-report-manager"></a><span data-ttu-id="33ca2-103">安全性頁面 (站台設定，</span><span class="sxs-lookup"><span data-stu-id="33ca2-103">Security Page (Site Settings.</span></span> <span data-ttu-id="33ca2-104">報表管理員)</span><span class="sxs-lookup"><span data-stu-id="33ca2-104">Report Manager)</span></span>
  <span data-ttu-id="33ca2-105">您可以使用 [安全性] 頁面來檢視控制報表伺服器站台之存取權的系統角色指派。</span><span class="sxs-lookup"><span data-stu-id="33ca2-105">Use the Security page to view the system role assignments that control access to the report server site.</span></span> <span data-ttu-id="33ca2-106">系統角色指派存在報表伺服器命名空間或資料夾階層的範圍之外。</span><span class="sxs-lookup"><span data-stu-id="33ca2-106">System role assignments exist outside of the scope of the report server namespace or folder hierarchy.</span></span> <span data-ttu-id="33ca2-107">系統角色指派是全域的，不會因特定項目而改變。</span><span class="sxs-lookup"><span data-stu-id="33ca2-107">System role assignments are global and cannot vary for specific items.</span></span> <span data-ttu-id="33ca2-108">透過系統角色指派支援的作業包括建立和使用共用排程、使用報表產生器，以及設定某些伺服器功能的預設值。</span><span class="sxs-lookup"><span data-stu-id="33ca2-108">Operations that are supported through system role assignments include creating and using shared schedules, using Report Builder, and setting default values for some server features.</span></span>  
  
 <span data-ttu-id="33ca2-109">安裝報表伺服器時，會建立預設的系統角色指派。</span><span class="sxs-lookup"><span data-stu-id="33ca2-109">A default system role assignment is created when the report server is installed.</span></span> <span data-ttu-id="33ca2-110">此系統角色指派會授與本機系統管理員權限，以管理報表伺服器環境。</span><span class="sxs-lookup"><span data-stu-id="33ca2-110">This system role assignment grants permissions to local system administrators to manage the report server environment.</span></span> <span data-ttu-id="33ca2-111">本機系統管理員永遠可以設定本機報表伺服器的安全性，即使刪除系統角色指派也一樣。</span><span class="sxs-lookup"><span data-stu-id="33ca2-111">A local system administrator can always set security for a local report server, even if system role assignments are deleted.</span></span>  
  
 <span data-ttu-id="33ca2-112">需要存取報表產生器或共用排程的所有其他使用者都必須被指派至系統角色指派。</span><span class="sxs-lookup"><span data-stu-id="33ca2-112">All other users who require access to Report Builder or shared schedules must be assigned to a system role assignment.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="33ca2-113">導覽</span><span class="sxs-lookup"><span data-stu-id="33ca2-113">Navigation</span></span>  
 <span data-ttu-id="33ca2-114">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="33ca2-114">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-security-page-for-site-settings"></a><span data-ttu-id="33ca2-115">若要開啟站台設定的安全性頁面</span><span class="sxs-lookup"><span data-stu-id="33ca2-115">To open the Security page for Site Settings</span></span>  
  
1.  <span data-ttu-id="33ca2-116">開啟報表管理員。</span><span class="sxs-lookup"><span data-stu-id="33ca2-116">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="33ca2-117">在頁面的頂端，按一下 **[站台設定]**。</span><span class="sxs-lookup"><span data-stu-id="33ca2-117">At the top of the page, click **Site Settings**.</span></span> <span data-ttu-id="33ca2-118">這樣就會開啟該站台的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="33ca2-118">This opens the General Properties page of the site.</span></span>  
  
3.  <span data-ttu-id="33ca2-119">選取 [安全性]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="33ca2-119">Select the **Security** tab.</span></span>  
  
## <a name="options"></a><span data-ttu-id="33ca2-120">選項</span><span class="sxs-lookup"><span data-stu-id="33ca2-120">Options</span></span>  
 <span data-ttu-id="33ca2-121">**刪除**</span><span class="sxs-lookup"><span data-stu-id="33ca2-121">**Delete**</span></span>  
 <span data-ttu-id="33ca2-122">按一下即可刪除現有的角色指派。</span><span class="sxs-lookup"><span data-stu-id="33ca2-122">Click to delete an existing role assignment.</span></span> <span data-ttu-id="33ca2-123">在按一下 **[刪除]** 之前，請選取您要移除之群組或使用者名稱旁邊的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="33ca2-123">Before clicking **Delete**, select the check box next to the group or user name that you want to remove.</span></span> <span data-ttu-id="33ca2-124">如果某個角色指派是唯一剩餘的角色指派，您就無法刪除它。</span><span class="sxs-lookup"><span data-stu-id="33ca2-124">You cannot delete a role assignment if it is the only one remaining.</span></span> <span data-ttu-id="33ca2-125">刪除角色指派不會刪除群組或使用者帳戶或角色定義。</span><span class="sxs-lookup"><span data-stu-id="33ca2-125">Deleting a role assignment does not delete a group or user account or role definitions.</span></span>  
  
 <span data-ttu-id="33ca2-126">**新增角色指派**</span><span class="sxs-lookup"><span data-stu-id="33ca2-126">**New Role Assignment**</span></span>  
 <span data-ttu-id="33ca2-127">按一下即可開啟 [新增系統角色指派] 頁面，可用來建立報表伺服器站台的其他系統角色指派。</span><span class="sxs-lookup"><span data-stu-id="33ca2-127">Click to open the New System Role Assignments page, which is used to create additional system role assignments for the report server site.</span></span> <span data-ttu-id="33ca2-128">如需詳細資訊，請參閱[新的系統角色指派：編輯系統角色指派頁面 &#40;報表管理員&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="33ca2-128">For more information, see [New System Role Assignments: Edit System Role Assignments Page &#40;Report Manager&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="33ca2-129">**編輯**</span><span class="sxs-lookup"><span data-stu-id="33ca2-129">**Edit**</span></span>  
 <span data-ttu-id="33ca2-130">按一下即可開啟 [編輯系統角色指派] 頁面，可用來編輯報表伺服器站台的個別系統角色指派。</span><span class="sxs-lookup"><span data-stu-id="33ca2-130">Click to open the Edit System Role Assignments page, which is used to edit individual system role assignments for the report server site.</span></span> <span data-ttu-id="33ca2-131">如需詳細資訊，請參閱[新的系統角色指派：編輯系統角色指派頁面 &#40;報表管理員&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="33ca2-131">For more information, see [New System Role Assignments: Edit System Role Assignments Page &#40;Report Manager&#41;](../../2014/reporting-services/new-system-role-assignments-edit-system-role-assignments-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="33ca2-132">**群組或使用者**</span><span class="sxs-lookup"><span data-stu-id="33ca2-132">**Group or User**</span></span>  
 <span data-ttu-id="33ca2-133">列出屬於現有角色指派之一部份的群組和使用者。</span><span class="sxs-lookup"><span data-stu-id="33ca2-133">Lists the groups and users that are part of an existing role assignment.</span></span> <span data-ttu-id="33ca2-134">目前資料夾的現有角色指派是為此資料行中顯示的群組和使用者所定義的。</span><span class="sxs-lookup"><span data-stu-id="33ca2-134">Existing role assignments for the current folder are defined for the groups and users that appear in this column.</span></span> <span data-ttu-id="33ca2-135">按一下群組或使用者名稱旁的 **[編輯]** ，即可檢視或編輯角色指派詳細資料。</span><span class="sxs-lookup"><span data-stu-id="33ca2-135">Click **Edit** next to a group or user name to view or edit role assignment details.</span></span>  
  
 <span data-ttu-id="33ca2-136">**角色**</span><span class="sxs-lookup"><span data-stu-id="33ca2-136">**Roles**</span></span>  
 <span data-ttu-id="33ca2-137">列出屬於現有角色指派一部分的一個或多個角色定義。</span><span class="sxs-lookup"><span data-stu-id="33ca2-137">Lists one or more role definitions that are part of an existing role assignment.</span></span> <span data-ttu-id="33ca2-138">如果有多個角色指派至群組或使用者帳戶，則該群組或使用者可以執行屬於所有角色的所有工作。</span><span class="sxs-lookup"><span data-stu-id="33ca2-138">If multiple roles are assigned to a group or user account, that group or user can perform all tasks that belong to all roles.</span></span> <span data-ttu-id="33ca2-139">若要查看每個角色支援的工作集，請使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="33ca2-139">To view the set of tasks that each role supports, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="33ca2-140">您無法在報表管理員中檢視、建立、修改或刪除角色。</span><span class="sxs-lookup"><span data-stu-id="33ca2-140">You cannot view, create, modify, or delete roles in Report Manager.</span></span> <span data-ttu-id="33ca2-141">如需相關指示，請參閱[建立、刪除或修改角色 &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md)。</span><span class="sxs-lookup"><span data-stu-id="33ca2-141">For instructions, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33ca2-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="33ca2-142">See Also</span></span>  
 <span data-ttu-id="33ca2-143">[報表管理員 F1 說明](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="33ca2-143">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 [<span data-ttu-id="33ca2-144">在原生模式報表伺服器上授與權限</span><span class="sxs-lookup"><span data-stu-id="33ca2-144">Granting Permissions on a Native Mode Report Server</span></span>](security/granting-permissions-on-a-native-mode-report-server.md)  
  
  
