---
title: 安全性屬性頁面， (報表管理員的專案) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 351b8503-354f-4b1b-a7ac-f1245d978da0
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 297ae2ceefad89d64c59b5da25d51d541917c894
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594371"
---
# <a name="security-properties-page-items-report-manager"></a><span data-ttu-id="ca239-102">安全性屬性頁面，項目 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="ca239-102">Security Properties Page, Items (Report Manager)</span></span>
  <span data-ttu-id="ca239-103">使用安全性屬性頁面來檢視或修改安全性設定，以決定資料夾、報表、模型、資源和共用資料來源的存取權。</span><span class="sxs-lookup"><span data-stu-id="ca239-103">Use the Security properties page to view or modify the security settings that determine access to folders, reports, models, resources, and shared data sources.</span></span> <span data-ttu-id="ca239-104">此頁面適用於您有權保護的項目。</span><span class="sxs-lookup"><span data-stu-id="ca239-104">This page is available for items that you have permission to secure.</span></span>  
  
 <span data-ttu-id="ca239-105">透過指定群組或使用者可執行的工作的角色指派來定義項目的存取權。</span><span class="sxs-lookup"><span data-stu-id="ca239-105">Access to items is defined through role assignments that specify the tasks that a group or user can perform.</span></span> <span data-ttu-id="ca239-106">角色指派含有一個使用者或群組名稱，以及一個或多個指定工作集合的角色定義。</span><span class="sxs-lookup"><span data-stu-id="ca239-106">A role assignment consists of one user or group name and one or more role definitions that specify a collection of tasks.</span></span>  
  
 <span data-ttu-id="ca239-107">安全性設定是由根資料夾繼承至子資料夾和那些資料夾內的項目。</span><span class="sxs-lookup"><span data-stu-id="ca239-107">Security settings are inherited from the root folder down to subfolders and items within those folders.</span></span> <span data-ttu-id="ca239-108">除非您明確地中斷繼承的安全性，否則子資料夾和項目會繼承父項目的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="ca239-108">Unless you explicitly break inherited security, subfolders and items inherit the security context of a parent item.</span></span> <span data-ttu-id="ca239-109">如果您為階層中間的資料夾重新定義安全性原則，所有其子項目 (包括子資料夾) 都會採用新的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ca239-109">If you redefine a security policy for a folder in the middle of the hierarchy, all its child items, including subfolders, assume the new security settings.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="ca239-110">導覽</span><span class="sxs-lookup"><span data-stu-id="ca239-110">Navigation</span></span>  
 <span data-ttu-id="ca239-111">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="ca239-111">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-security-page-for-an-item"></a><span data-ttu-id="ca239-112">若要開啟項目的安全性頁面</span><span class="sxs-lookup"><span data-stu-id="ca239-112">To open the Security page for an item</span></span>  
  
1.  <span data-ttu-id="ca239-113">開啟報表管理員，然後找出您想要設定安全性設定的項目。</span><span class="sxs-lookup"><span data-stu-id="ca239-113">Open Report Manager, and locate the item for which you want to configure security settings.</span></span>  
  
2.  <span data-ttu-id="ca239-114">將滑鼠停留在該項目上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="ca239-114">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="ca239-115">在下拉式功能表中，執行下列其中一項步驟：</span><span class="sxs-lookup"><span data-stu-id="ca239-115">In the drop-down menu, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="ca239-116">按一下 **[安全性]** 。</span><span class="sxs-lookup"><span data-stu-id="ca239-116">Click **Security**.</span></span> <span data-ttu-id="ca239-117">這樣就會開啟該項目的 [安全性] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="ca239-117">This opens the Security properties page for the item.</span></span>  
  
    -   <span data-ttu-id="ca239-118">按一下 **[管理]** 開啟項目的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="ca239-118">Click **Manage** to open the General properties page for the item.</span></span> <span data-ttu-id="ca239-119">然後，選取 **[安全性]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="ca239-119">Then select the **Security** tab.</span></span>  
  
 <span data-ttu-id="ca239-120">**編輯項目安全性**</span><span class="sxs-lookup"><span data-stu-id="ca239-120">**Edit Item Security**</span></span>  
 <span data-ttu-id="ca239-121">按一下即可變更定義目前項目安全性的方式。</span><span class="sxs-lookup"><span data-stu-id="ca239-121">Click to change how security is defined for the current item.</span></span> <span data-ttu-id="ca239-122">如果您編輯資料夾的安全性，您的變更將套用至目前資料夾及其任何子資料夾的內容。</span><span class="sxs-lookup"><span data-stu-id="ca239-122">If you are editing security for a folder, your changes apply to the contents of the current folder and any subfolders.</span></span>  
  
 <span data-ttu-id="ca239-123">[首頁] 資料夾不可使用此按鈕。</span><span class="sxs-lookup"><span data-stu-id="ca239-123">This button is not available for the Home folder.</span></span>  
  
 <span data-ttu-id="ca239-124">編輯項目安全性時，可以使用下列按鈕。</span><span class="sxs-lookup"><span data-stu-id="ca239-124">The following buttons become available when you edit item security.</span></span>  
  
 <span data-ttu-id="ca239-125">**刪除**</span><span class="sxs-lookup"><span data-stu-id="ca239-125">**Delete**</span></span>  
 <span data-ttu-id="ca239-126">選取您要刪除的群組或使用者名稱旁的核取方塊，然後按一下 **[刪除]**。</span><span class="sxs-lookup"><span data-stu-id="ca239-126">Select the check box next to the group or user name that you want to delete and click **Delete**.</span></span> <span data-ttu-id="ca239-127">如果它是留下的唯一角色指派，或是定義報表伺服器之安全性基準的內建角色指派 (例如，「Built-in\Administrators」)，則無法將其刪除。</span><span class="sxs-lookup"><span data-stu-id="ca239-127">You cannot delete a role assignment if it is the only one remaining, or if it is a built-in role assignment (for example, "Built-in\Administrators") that defines the security baseline for the report server.</span></span> <span data-ttu-id="ca239-128">刪除角色指派不會刪除群組或使用者帳戶或角色定義。</span><span class="sxs-lookup"><span data-stu-id="ca239-128">Deleting a role assignment does not delete a group or user account or role definitions.</span></span>  
  
 <span data-ttu-id="ca239-129">**新增角色指派**</span><span class="sxs-lookup"><span data-stu-id="ca239-129">**New Role Assignment**</span></span>  
 <span data-ttu-id="ca239-130">按一下即可開啟 [新增角色指派] 頁面，可用來建立目前項目的其他角色指派。</span><span class="sxs-lookup"><span data-stu-id="ca239-130">Click to open the New Role Assignment page, which is used to create additional role assignments for the current item.</span></span> <span data-ttu-id="ca239-131">如需詳細資訊，請參閱[新增角色指派：編輯角色指派頁面 &#40;報表管理員&#41;](../../2014/reporting-services/new-role-assignment-edit-role-assignment-page-report-manager.md)。</span><span class="sxs-lookup"><span data-stu-id="ca239-131">For more information, see [New Role Assignment: Edit Role Assignment Page &#40;Report Manager&#41;](../../2014/reporting-services/new-role-assignment-edit-role-assignment-page-report-manager.md).</span></span>  
  
 <span data-ttu-id="ca239-132">**還原為父安全性**</span><span class="sxs-lookup"><span data-stu-id="ca239-132">**Revert to Parent Security**</span></span>  
 <span data-ttu-id="ca239-133">按一下即可將安全性設定重設為直屬父資料夾的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ca239-133">Click to reset the security settings to that of the immediate parent folder.</span></span> <span data-ttu-id="ca239-134">如果報表伺服器資料夾階層中都未打破繼承，則使用最上層資料夾 [首頁] 的安全性設定。</span><span class="sxs-lookup"><span data-stu-id="ca239-134">If inheritance is unbroken throughout the report server folder hierarchy, the security settings of the top-level folder, Home, are used.</span></span>  
  
 <span data-ttu-id="ca239-135">**群組或使用者**</span><span class="sxs-lookup"><span data-stu-id="ca239-135">**Group or User**</span></span>  
 <span data-ttu-id="ca239-136">列出屬於目前項目的現有角色指派之一部份的群組和使用者。</span><span class="sxs-lookup"><span data-stu-id="ca239-136">Lists the groups and users that are part of an existing role assignment for the current item.</span></span> <span data-ttu-id="ca239-137">目前資料夾的現有角色指派是為此資料行中顯示的群組和使用者所定義的。</span><span class="sxs-lookup"><span data-stu-id="ca239-137">Existing role assignments for the current folder are defined for the groups and users that appear in this column.</span></span> <span data-ttu-id="ca239-138">您可以按一下群組或使用者名稱以檢視或編輯角色指派詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ca239-138">You can click a group or user name to view or edit role assignment details.</span></span>  
  
 <span data-ttu-id="ca239-139">**角色**</span><span class="sxs-lookup"><span data-stu-id="ca239-139">**Roles**</span></span>  
 <span data-ttu-id="ca239-140">列出屬於現有角色指派一部分的一個或多個角色定義。</span><span class="sxs-lookup"><span data-stu-id="ca239-140">Lists one or more role definitions that are part of an existing role assignment.</span></span> <span data-ttu-id="ca239-141">如果有多個角色指派至群組或使用者帳戶，則該群組或使用者可以執行屬於該角色的所有工作。</span><span class="sxs-lookup"><span data-stu-id="ca239-141">If multiple roles are assigned to a group or user account, that group or user can perform all tasks that belong to those roles.</span></span> <span data-ttu-id="ca239-142">若要檢視與某個角色相關聯的工作，請使用 SQL Server Management Studio 來檢視每個角色定義中的工作。</span><span class="sxs-lookup"><span data-stu-id="ca239-142">To view the tasks that are associated with a role, use SQL Server Management Studio to view the tasks in each role definition.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca239-143">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ca239-143">See Also</span></span>  
 <span data-ttu-id="ca239-144">[報表管理員 F1 說明](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="ca239-144">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="ca239-145">[預先定義的角色](security/role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="ca239-145">[Predefined Roles](security/role-definitions-predefined-roles.md) </span></span>  
 <span data-ttu-id="ca239-146">[在原生模式報表伺服器上授與權限](security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="ca239-146">[Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="ca239-147">[角色指派](security/role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="ca239-147">[Role Assignments](security/role-assignments.md) </span></span>  
 [<span data-ttu-id="ca239-148">角色定義</span><span class="sxs-lookup"><span data-stu-id="ca239-148">Role Definitions</span></span>](security/role-definitions.md)  
  
  
