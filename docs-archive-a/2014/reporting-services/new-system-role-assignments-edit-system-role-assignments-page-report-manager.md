---
title: 新增系統角色指派： [編輯系統角色指派] 頁面 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 62a22ab9-1eb4-4ce5-8dd7-06b5ed2d9a2a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6e04ec18b8ee27c5897156753c1e4f7991991eae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592502"
---
# <a name="new-system-role-assignments-edit-system-role-assignments-page-report-manager"></a><span data-ttu-id="4161c-102">新增系統角色指派：編輯系統角色指派頁面 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="4161c-102">New System Role Assignments: Edit System Role Assignments Page (Report Manager)</span></span>
  <span data-ttu-id="4161c-103">使用 [新增系統角色指派] 或 [編輯系統角色指派] 頁面來定義報表伺服器的安全性。</span><span class="sxs-lookup"><span data-stu-id="4161c-103">Use the New System Role Assignments or Edit System Role Assignments page to define security for the report server.</span></span> <span data-ttu-id="4161c-104">所有的安全性都透過角色指派來定義，角色指派會對應特定使用者或群組至其可執行的工作。</span><span class="sxs-lookup"><span data-stu-id="4161c-104">All security is defined through role assignments that map specific users or groups to the tasks that they can perform.</span></span> <span data-ttu-id="4161c-105">以您在進行角色指派時選取的角色定義來表示工作清單。</span><span class="sxs-lookup"><span data-stu-id="4161c-105">The task list is represented as a role definition that you select when making the role assignment.</span></span>  
  
 <span data-ttu-id="4161c-106">在系統層級，您建立或修改的角色指派將整個套用至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="4161c-106">At the system level, the role assignments that you create or modify apply to the report server as a whole.</span></span> <span data-ttu-id="4161c-107">例如，建立共用排程的能力是在系統層級指定的，因為共用排程是全系統要使用的。</span><span class="sxs-lookup"><span data-stu-id="4161c-107">For example, the ability to create shared schedules is specified at the system level because shared schedules are used throughout the system.</span></span>  
  
 <span data-ttu-id="4161c-108">根據預設，Reporting Services 會提供兩個預先定義的系統層級角色：</span><span class="sxs-lookup"><span data-stu-id="4161c-108">By default, Reporting Services provides two predefined system level roles:</span></span>  
  
-   <span data-ttu-id="4161c-109">「系統使用者」包括允許使用者檢視報表伺服器屬性和共用排程，以及執行報表定義的工作，讓使用者能夠檢視已經發行至報表伺服器的點選連結報表。</span><span class="sxs-lookup"><span data-stu-id="4161c-109">System User includes tasks that allow users to view report server properties and shared schedules, and to execute report definitions, which allows users to view clickthrough reports that have been published to the report server.</span></span> <span data-ttu-id="4161c-110">大部分使用者都應該指派至這個角色。</span><span class="sxs-lookup"><span data-stu-id="4161c-110">Most users should be assigned to this role.</span></span>  
  
-   <span data-ttu-id="4161c-111">「系統管理員」包括建立和管理共用排程、設定伺服器屬性，以及為其他使用者建立系統層級角色指派的工作。</span><span class="sxs-lookup"><span data-stu-id="4161c-111">System Administrator includes tasks for creating and managing shared schedules, setting server properties, and creating system-level role assignments for other users.</span></span> <span data-ttu-id="4161c-112">少數使用者需要這個層級的權限。</span><span class="sxs-lookup"><span data-stu-id="4161c-112">Few users require permissions at this level.</span></span>  
  
## <a name="navigation"></a><span data-ttu-id="4161c-113">導覽</span><span class="sxs-lookup"><span data-stu-id="4161c-113">Navigation</span></span>  
 <span data-ttu-id="4161c-114">您可以使用下列程序，在使用者介面 (UI) 中導覽至這個位置。</span><span class="sxs-lookup"><span data-stu-id="4161c-114">Use the following procedure to navigate to this location in the user interface (UI).</span></span>  
  
###### <a name="to-open-the-new-system-role-assignments-or-edit-system-role-assignments-page"></a><span data-ttu-id="4161c-115">若要開啟新增系統角色指派或編輯系統角色指派頁面</span><span class="sxs-lookup"><span data-stu-id="4161c-115">To open the New System Role Assignments or Edit System Role Assignments page</span></span>  
  
1.  <span data-ttu-id="4161c-116">開啟報表管理員。</span><span class="sxs-lookup"><span data-stu-id="4161c-116">Open Report Manager.</span></span>  
  
2.  <span data-ttu-id="4161c-117">在頁面的頂端，按一下右邊角落的 **[站台設定]**。</span><span class="sxs-lookup"><span data-stu-id="4161c-117">At the top of the page, in the right-hand corner, click **Site Settings**.</span></span> <span data-ttu-id="4161c-118">這樣就會開啟該站台的 [一般] 屬性頁面。</span><span class="sxs-lookup"><span data-stu-id="4161c-118">This opens the General properties page for the site.</span></span>  
  
3.  <span data-ttu-id="4161c-119">選取 [**安全性**] 索引標籤。您必須擁有 [內容管理員] 和 [系統管理員] 許可權，才能存取此頁面。</span><span class="sxs-lookup"><span data-stu-id="4161c-119">Select the **Security** tab. You must have Content Manager and System Administrator permissions to access this page.</span></span>  
  
4.  <span data-ttu-id="4161c-120">若要建立新的角色指派，請在工具列中，按一下 **[新增角色指派]** 。</span><span class="sxs-lookup"><span data-stu-id="4161c-120">To create a new role assignment, click **New Role Assignment** in the toolbar.</span></span> <span data-ttu-id="4161c-121">若要編輯現有的角色指派，請在 [安全性] 屬性頁面上，按一下群組或使用者旁的 **[編輯]** 。</span><span class="sxs-lookup"><span data-stu-id="4161c-121">To edit an existing role assignment, click **Edit** next to a group or user on the Security properties page.</span></span>  
  
## <a name="options"></a><span data-ttu-id="4161c-122">選項</span><span class="sxs-lookup"><span data-stu-id="4161c-122">Options</span></span>  
 <span data-ttu-id="4161c-123">**群組或使用者**</span><span class="sxs-lookup"><span data-stu-id="4161c-123">**Group or User**</span></span>  
 <span data-ttu-id="4161c-124">輸入網域中之群組或使用者帳戶的名稱。</span><span class="sxs-lookup"><span data-stu-id="4161c-124">Type the name of a group or user account in your domain.</span></span> <span data-ttu-id="4161c-125">如果是以本機帳戶執行報表伺服器，您就必須指定本機群組或使用者。</span><span class="sxs-lookup"><span data-stu-id="4161c-125">If the report server is running under a local account, you must specify local groups or users.</span></span> <span data-ttu-id="4161c-126">如果是以網域帳戶執行報表伺服器，您就必須指定網域群組或使用者。</span><span class="sxs-lookup"><span data-stu-id="4161c-126">If the report server is running under a domain account, you must specify domain groups or users.</span></span> <span data-ttu-id="4161c-127">請以下列格式輸入帳戶： \<domain> \\<帳戶 \> 。</span><span class="sxs-lookup"><span data-stu-id="4161c-127">Enter the account in this format: \<domain>\\<account\>.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4161c-128">這個方塊只有 [新增角色指派] 頁面才有提供。</span><span class="sxs-lookup"><span data-stu-id="4161c-128">This box is available only on the New Role Assignment page.</span></span>  
  
 <span data-ttu-id="4161c-129">**角色**</span><span class="sxs-lookup"><span data-stu-id="4161c-129">**Roles**</span></span>  
 <span data-ttu-id="4161c-130">提供您可以指派給其他使用者的系統層級角色清單。</span><span class="sxs-lookup"><span data-stu-id="4161c-130">Provides a list of system-level roles that you can assign to other users.</span></span> <span data-ttu-id="4161c-131">您可以針對單一角色指派指定多個角色。</span><span class="sxs-lookup"><span data-stu-id="4161c-131">You can specify multiple roles for a single role assignment.</span></span>  
  
 <span data-ttu-id="4161c-132">報表管理員不會顯示每個角色中的工作，也不會提供加入或修改這些工作的方式。</span><span class="sxs-lookup"><span data-stu-id="4161c-132">Report Manager does not display the tasks in each role or provide a way to add or modify the tasks.</span></span> <span data-ttu-id="4161c-133">您必須依照原本定義的方式來使用這些角色。</span><span class="sxs-lookup"><span data-stu-id="4161c-133">You must use the roles as they are defined.</span></span> <span data-ttu-id="4161c-134">若要建立、修改或刪除角色，請使用 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="4161c-134">To create, modify, or delete roles, use [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="4161c-135">如需這些預先定義角色的詳細資訊，請參閱 [建立、刪除或修改角色 &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md)。</span><span class="sxs-lookup"><span data-stu-id="4161c-135">For more information, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](security/role-definitions-create-delete-or-modify.md).</span></span>  
  
 <span data-ttu-id="4161c-136">請注意，如果您要使用 [!INCLUDE[ssExpressEd2005](../includes/ssexpressed2005-md.md)] with Advanced Services，就必須使用提供的預設角色。</span><span class="sxs-lookup"><span data-stu-id="4161c-136">Note that if you are using [!INCLUDE[ssExpressEd2005](../includes/ssexpressed2005-md.md)] with Advanced Services, you must use the default roles that are provided.</span></span>  
  
 <span data-ttu-id="4161c-137">**說明**</span><span class="sxs-lookup"><span data-stu-id="4161c-137">**Descriptions**</span></span>  
 <span data-ttu-id="4161c-138">顯示有關角色的其他資訊。</span><span class="sxs-lookup"><span data-stu-id="4161c-138">Shows additional information about the role.</span></span> <span data-ttu-id="4161c-139">對於預先定義的角色 (如「系統使用者」或「系統管理員」)，描述會概述每一個角色支援的工作。</span><span class="sxs-lookup"><span data-stu-id="4161c-139">For predefined roles such as System User or System Administrator, the description summarizes the tasks that each role supports.</span></span>  
  
 <span data-ttu-id="4161c-140">**刪除角色指派**</span><span class="sxs-lookup"><span data-stu-id="4161c-140">**Delete Role Assignment**</span></span>  
 <span data-ttu-id="4161c-141">按一下即可刪除使用者或群組的現有角色指派。</span><span class="sxs-lookup"><span data-stu-id="4161c-141">Click to delete an existing role assignment for a user or a group.</span></span> <span data-ttu-id="4161c-142">如果它是唯一留下的角色指派，就不可以刪除該角色指派 (每一個項目至少都必須具有一個角色指派)。</span><span class="sxs-lookup"><span data-stu-id="4161c-142">You cannot delete a role assignment if it is the only one left (each item must have a minimum of one role assignment).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="4161c-143">這個按鈕只有 [編輯角色指派] 頁面才有提供。</span><span class="sxs-lookup"><span data-stu-id="4161c-143">This button is available only on the Edit Role Assignment page.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4161c-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4161c-144">See Also</span></span>  
 <span data-ttu-id="4161c-145">[報表管理員 F1 說明](../../2014/reporting-services/report-manager-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="4161c-145">[Report Manager F1 Help](../../2014/reporting-services/report-manager-f1-help.md) </span></span>  
 <span data-ttu-id="4161c-146">[角色指派](security/role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="4161c-146">[Role Assignments](security/role-assignments.md) </span></span>  
 [<span data-ttu-id="4161c-147">角色定義</span><span class="sxs-lookup"><span data-stu-id="4161c-147">Role Definitions</span></span>](security/role-definitions.md)  
  
  
