---
title: 新增角色指派：編輯角色指派頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3319ced0-4b86-42af-b18d-da41a625113c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 1640617dbf9836986597ee49d4ca1ddc37fd84ab
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706258"
---
# <a name="new-role-assignment-edit-role-assignment-page-report-manager"></a><span data-ttu-id="27ae6-102">新增角色指派：編輯角色指派頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="27ae6-102">New Role Assignment: Edit Role Assignment Page (Report Manager)</span></span>
  <span data-ttu-id="27ae6-103">您可以使用 [新增角色指派] 或 [編輯角色指派] 頁面來授與報表伺服器項目和作業的權限。</span><span class="sxs-lookup"><span data-stu-id="27ae6-103">Use the New Role Assignment or Edit Role Assignment page to grant permissions to report server items and operations.</span></span> <span data-ttu-id="27ae6-104">每位需要存取報表伺服器的使用者至少都必須具有一個定義存取層級的角色指派。</span><span class="sxs-lookup"><span data-stu-id="27ae6-104">Each user who requires access to a report server must have a role assignment that defines the level of access.</span></span> <span data-ttu-id="27ae6-105">您可以在根節點，或在特定的報表、模型、資料夾、資源或共用資料來源上，建立角色指派。</span><span class="sxs-lookup"><span data-stu-id="27ae6-105">You can create role assignments at the root node, or on a specific report, model, folder, resource, or shared data source.</span></span> [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)] <span data-ttu-id="27ae6-106">透過您套用至項目的角色指派，可以強制執行安全性。</span><span class="sxs-lookup"><span data-stu-id="27ae6-106">security is enforced through role assignments that you apply to items.</span></span> <span data-ttu-id="27ae6-107">角色指派使群組或使用者符合角色定義，其中每一個角色定義識別群組或使用者可對特定項目執行的工作。</span><span class="sxs-lookup"><span data-stu-id="27ae6-107">A role assignment matches a group or user to a role definition, where each role definition identifies the tasks that groups or users can perform with regards to a specific item.</span></span>  
  
 <span data-ttu-id="27ae6-108">項目層級角色指派可能影響的層面很廣。</span><span class="sxs-lookup"><span data-stu-id="27ae6-108">Item-level role assignments can have a broad impact.</span></span> <span data-ttu-id="27ae6-109">雖然它們可與單一報表或資料夾產生關聯，但也可以定義於資料夾階層的高層級，而由樹狀目錄中較低層級的資料夾和項目來繼承。</span><span class="sxs-lookup"><span data-stu-id="27ae6-109">Although they can be associated with a single report or folder, they can also be defined at a high level in the folder hierarchy and be inherited by folders and items that are lower in the tree.</span></span> <span data-ttu-id="27ae6-110">如需詳細資訊，請參閱[將報表伺服器的存取權授與使用者 &#40;報表管理員&#41;](security/grant-user-access-to-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="27ae6-110">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](security/grant-user-access-to-a-report-server.md).</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="27ae6-111">導覽</span><span class="sxs-lookup"><span data-stu-id="27ae6-111">Navigation</span></span>  
 <span data-ttu-id="27ae6-112">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="27ae6-112">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-role-assignment-or-edit-role-assignment-page"></a><span data-ttu-id="27ae6-113">若要開啟新增角色指派或編輯角色指派頁面</span><span class="sxs-lookup"><span data-stu-id="27ae6-113">To open the New Role Assignment or Edit Role Assignment page</span></span>  
  
1.  <span data-ttu-id="27ae6-114">開啟報表管理員，然後找出您想要加入新角色指派或編輯角色指派的項目。</span><span class="sxs-lookup"><span data-stu-id="27ae6-114">Open Report Manager, and locate an item for which you want to add a new role assignment or edit a role assignment.</span></span>  
  
2.  <span data-ttu-id="27ae6-115">將滑鼠停留在該項目上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="27ae6-115">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="27ae6-116">在下拉式功能表中，按一下 [安全性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="27ae6-116">In the drop-down menu, click **Security**.</span></span> <span data-ttu-id="27ae6-117">這樣就會開啟該項目的 [安全性] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="27ae6-117">This opens the Security properties page for the item.</span></span>  
  
4.  <span data-ttu-id="27ae6-118">如果您想要加入新的角色指派，請在工具列中，按一下 **[新增角色指派]**。</span><span class="sxs-lookup"><span data-stu-id="27ae6-118">If you want to add a new role assignment, in the toolbar, click **New Role Assignment**.</span></span> <span data-ttu-id="27ae6-119">如果您想要編輯角色指派，請按一下想要編輯之群組或使用者名稱旁的 **[編輯]** 。</span><span class="sxs-lookup"><span data-stu-id="27ae6-119">If you want to edit a role assignment, click **Edit** next to the group or user name you want to edit.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="27ae6-120"> 如果某個項目目前是從父項目繼承安全性，請按一下工具列中的 **[編輯項目安全性]** 來變更安全性設定。</span><span class="sxs-lookup"><span data-stu-id="27ae6-120">If an item currently inherits security from a parent item, click **Edit Item Security** in the toolbar to change the security settings.</span></span>  
  
## <a name="options"></a><span data-ttu-id="27ae6-121">選項</span><span class="sxs-lookup"><span data-stu-id="27ae6-121">Options</span></span>  
 <span data-ttu-id="27ae6-122">**群組或使用者名稱**</span><span class="sxs-lookup"><span data-stu-id="27ae6-122">**Group or User Name**</span></span>  
 <span data-ttu-id="27ae6-123">輸入要建立其角色指派的群組或使用者帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="27ae6-123">Type the name of a group or user account for which the role assignment is being created.</span></span> <span data-ttu-id="27ae6-124">群組或使用者名稱必須是有效的 Windows 網域帳戶。</span><span class="sxs-lookup"><span data-stu-id="27ae6-124">The group or user name must be a valid Windows domain account.</span></span> <span data-ttu-id="27ae6-125">請以下列格式輸入帳戶： \<domain> \\<帳戶 \> 。</span><span class="sxs-lookup"><span data-stu-id="27ae6-125">Enter the account in this format: \<domain>\\<account\>.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27ae6-126">這個方塊只有 [新增角色指派] 頁面才有提供。</span><span class="sxs-lookup"><span data-stu-id="27ae6-126">This box is available only on the New Role Assignment page.</span></span>  
  
 <span data-ttu-id="27ae6-127">**角色**</span><span class="sxs-lookup"><span data-stu-id="27ae6-127">**Role**</span></span>  
 <span data-ttu-id="27ae6-128">顯示報表伺服器中定義的全部角色，可用來定義項目的安全性。</span><span class="sxs-lookup"><span data-stu-id="27ae6-128">Shows all roles defined on the report server that can be used to define security for items.</span></span> <span data-ttu-id="27ae6-129">在建立或變更報表或資料夾的角色指派時，請選取一或多個角色，直到結合的工作集描述使用者獲准執行的動作為止。</span><span class="sxs-lookup"><span data-stu-id="27ae6-129">When you create or change a role assignment for a report or folder, select one or more roles until the combined set of tasks describe the actions that the user should be allowed to perform.</span></span> <span data-ttu-id="27ae6-130">若要查看每個角色支援的工作集，請使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="27ae6-130">To view the set of tasks that each role supports, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="27ae6-131">您無法在報表管理員中檢視、建立、修改或刪除角色。</span><span class="sxs-lookup"><span data-stu-id="27ae6-131">You cannot view, create, modify, or delete roles in Report Manager.</span></span> <span data-ttu-id="27ae6-132">如需相關指示，請參閱[建立、刪除或修改角色 &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md)。</span><span class="sxs-lookup"><span data-stu-id="27ae6-132">For instructions, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).</span></span>  
  
 <span data-ttu-id="27ae6-133">**說明**</span><span class="sxs-lookup"><span data-stu-id="27ae6-133">**Description**</span></span>  
 <span data-ttu-id="27ae6-134">顯示有關角色的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="27ae6-134">Shows additional information about the role.</span></span> <span data-ttu-id="27ae6-135">針對預先定義的角色，例如 **[瀏覽器]** 或 **[內容管理員]**，描述會摘要每個角色支援的工作。</span><span class="sxs-lookup"><span data-stu-id="27ae6-135">For predefined roles such as **Browser** or **Content Manager**, the description summarizes the tasks that each role supports.</span></span>  
  
 <span data-ttu-id="27ae6-136">**刪除角色指派**</span><span class="sxs-lookup"><span data-stu-id="27ae6-136">**Delete Role Assignment**</span></span>  
 <span data-ttu-id="27ae6-137">按一下即可刪除使用者或群組的現有角色指派。</span><span class="sxs-lookup"><span data-stu-id="27ae6-137">Click to delete an existing role assignment for a user or a group.</span></span> <span data-ttu-id="27ae6-138">如果它是唯一留下的角色指派，就不可以刪除該角色指派 (每一個項目至少都必須具有一個角色指派)。</span><span class="sxs-lookup"><span data-stu-id="27ae6-138">You cannot delete a role assignment if it is the only one left (each item must have a minimum of one role assignment).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="27ae6-139">這個按鈕只有 [編輯角色指派] 頁面才有提供。</span><span class="sxs-lookup"><span data-stu-id="27ae6-139">This button is available only on the Edit Role Assignment page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27ae6-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="27ae6-140">See Also</span></span>  
 <span data-ttu-id="27ae6-141">[建立、刪除或修改角色 &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md) </span><span class="sxs-lookup"><span data-stu-id="27ae6-141">[Create, Delete, or Modify a Role &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md) </span></span>  
 <span data-ttu-id="27ae6-142">[在原生模式報表伺服器上授與權限](security/granting-permissions-on-a-native-mode-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="27ae6-142">[Granting Permissions on a Native Mode Report Server](security/granting-permissions-on-a-native-mode-report-server.md) </span></span>  
 <span data-ttu-id="27ae6-143">[報表管理員 &#40;SSRS 原生模式&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span><span class="sxs-lookup"><span data-stu-id="27ae6-143">[Report Manager  &#40;SSRS Native Mode&#41;](../../2014/reporting-services/report-manager-ssrs-native-mode.md) </span></span>  
 <span data-ttu-id="27ae6-144">[報表管理員 F1 說明](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="27ae6-144">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="27ae6-145">[角色指派](security/role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="27ae6-145">[Role Assignments](security/role-assignments.md) </span></span>  
 [<span data-ttu-id="27ae6-146">將報表伺服器的存取權授與使用者 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="27ae6-146">Grant User Access to a Report Server &#40;Report Manager&#41;</span></span>](security/grant-user-access-to-a-report-server.md)  
  
  
