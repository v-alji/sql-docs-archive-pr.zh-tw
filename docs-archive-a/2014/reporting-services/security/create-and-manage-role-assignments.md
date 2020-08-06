---
title: 建立及管理角色指派 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- roles [Reporting Services], assignments
- security [Reporting Services], role assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 086d0987-b43c-4834-8372-e08fb4b432f8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 2064e2a6d4dda99ed6b8b61de363b84d073d8ef9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699295"
---
# <a name="create-and-manage-role-assignments"></a><span data-ttu-id="a0b29-102">建立和管理角色指派</span><span class="sxs-lookup"><span data-stu-id="a0b29-102">Create and Manage Role Assignments</span></span>
  <span data-ttu-id="a0b29-103">*「角色指派」* (Role assignment) 是一種安全性原則，可決定使用者或群組是否能夠存取特定的報表伺服器項目或執行作業。</span><span class="sxs-lookup"><span data-stu-id="a0b29-103">A *role assignment* is a security policy that determines whether a user or group can access a specific report server item or perform an operation.</span></span> <span data-ttu-id="a0b29-104">角色指派是由單一使用者或群組帳戶名稱以及一或多個角色定義所組成。</span><span class="sxs-lookup"><span data-stu-id="a0b29-104">A role assignment consists of a single user or group account name and one or more role definitions.</span></span>  
  
 <span data-ttu-id="a0b29-105">角色指派的範圍設定為 *「項目層級」* 或 *「系統層級」*。</span><span class="sxs-lookup"><span data-stu-id="a0b29-105">Role assignments are scoped to the *item level* or *system level*.</span></span>  
  
-   <span data-ttu-id="a0b29-106">項目層級角色指派永遠是建立在特定項目的內容中或報表伺服器資料夾階層的分支中。</span><span class="sxs-lookup"><span data-stu-id="a0b29-106">An item-level role assignment is always created in the context of a specific item or branch in the report server folder hierarchy.</span></span> <span data-ttu-id="a0b29-107">導覽至特定資料夾或項目，即可為其建立角色指派。</span><span class="sxs-lookup"><span data-stu-id="a0b29-107">You navigate to a specific folder or item to create a role assignment for it.</span></span>  
  
-   <span data-ttu-id="a0b29-108">系統層級角色指派會提供選定使用者能夠執行可影響整體報表伺服器站台之工作的能力。</span><span class="sxs-lookup"><span data-stu-id="a0b29-108">System-level role assignments give selected users the capability to perform tasks that affect the report server site as a whole.</span></span> <span data-ttu-id="a0b29-109">這些工作包括建立共用排程、管理作業、在報表產生器中處理報表，以及設定屬性。</span><span class="sxs-lookup"><span data-stu-id="a0b29-109">These tasks include creating shared schedules, managing jobs, processing reports in Report Builder, and setting properties.</span></span> <span data-ttu-id="a0b29-110">系統層級安全性不會傳遞報表伺服器資料夾階層中項目的存取權。</span><span class="sxs-lookup"><span data-stu-id="a0b29-110">System-level security does not convey access to items in the report server folder hierarchy.</span></span>  
  
## <a name="creating-an-item-level-role-assignment"></a><span data-ttu-id="a0b29-111">建立項目層級角色指派</span><span class="sxs-lookup"><span data-stu-id="a0b29-111">Creating an Item-level Role Assignment</span></span>  
 <span data-ttu-id="a0b29-112">若要建立或管理角色指派，請使用報表管理員，並開啟您想要維護安全之項目的 [安全性] 屬性頁。</span><span class="sxs-lookup"><span data-stu-id="a0b29-112">To create or manage role assignments, use Report Manager and open the Security property pages of the item that you want to secure.</span></span>  
  
 <span data-ttu-id="a0b29-113">您必須針對需要存取報表伺服器的每一個使用者或群組帳戶建立個別的角色指派。</span><span class="sxs-lookup"><span data-stu-id="a0b29-113">You must create a separate role assignment for each user or group account that requires access to the report server.</span></span> <span data-ttu-id="a0b29-114">如果帳戶不是在包含報表伺服器的網域上，請包括網域名稱。</span><span class="sxs-lookup"><span data-stu-id="a0b29-114">If the account is on a domain other than the one that contains the report server, include the domain name.</span></span> <span data-ttu-id="a0b29-115">指定帳戶之後，您可以選擇一或多個角色定義。</span><span class="sxs-lookup"><span data-stu-id="a0b29-115">After you specify an account, you can choose one or more role definitions.</span></span> <span data-ttu-id="a0b29-116">角色定義會是累加的。</span><span class="sxs-lookup"><span data-stu-id="a0b29-116">The role definitions are additive.</span></span> <span data-ttu-id="a0b29-117">特定使用者或群組的指派中，支援所有定義中之結合的所有工作集。</span><span class="sxs-lookup"><span data-stu-id="a0b29-117">The combined set of all tasks from all definitions are supported in the assignment for a particular user or group.</span></span>  
  
 <span data-ttu-id="a0b29-118">若要啟用普遍存取權，您應該在資料夾階層中選擇較高的項目 (例如，根節點 [主資料夾])。</span><span class="sxs-lookup"><span data-stu-id="a0b29-118">To enable widespread access, you should choose an item that is high in the folder hierarchy (for example, the root node Home).</span></span> <span data-ttu-id="a0b29-119">接著，您可以建立後續角色指派，以鎖定資料夾階層的特定區域。</span><span class="sxs-lookup"><span data-stu-id="a0b29-119">You can then create subsequent role assignments to lock down specific areas of the folder hierarchy.</span></span>  
  
 <span data-ttu-id="a0b29-120">您必須是報表伺服器電腦上本機系統管理員群組的成員，才能建立角色指派。</span><span class="sxs-lookup"><span data-stu-id="a0b29-120">You must be a member of the local Administrator's group on the report server computer to create a role assignment.</span></span> <span data-ttu-id="a0b29-121">您可以將其他使用者指派給 **「內容管理員」** 角色來委派該項責任。</span><span class="sxs-lookup"><span data-stu-id="a0b29-121">You can delegate that responsibility by assigning other users to the **Content Manager** role.</span></span>  
  
 <span data-ttu-id="a0b29-122">如需詳細資訊，請參閱[將報表伺服器的存取權授與使用者 &#40;報表管理員&#41;](grant-user-access-to-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="a0b29-122">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md).</span></span>  
  
## <a name="creating-a-system-level-role-assignment"></a><span data-ttu-id="a0b29-123">建立系統層級角色指派</span><span class="sxs-lookup"><span data-stu-id="a0b29-123">Creating a System-level Role Assignment</span></span>  
 <span data-ttu-id="a0b29-124">若要建立或管理系統層級角色指派，請使用報表管理員，並開啟 [站台設定] 頁面。</span><span class="sxs-lookup"><span data-stu-id="a0b29-124">To create or manage a system-level role assignment, use Report Manager and open the Site Settings page.</span></span>  
  
 <span data-ttu-id="a0b29-125">系統層級與項目層級角色指派會一起使用。</span><span class="sxs-lookup"><span data-stu-id="a0b29-125">System-level and item-level role assignments go together.</span></span> <span data-ttu-id="a0b29-126">您應該針對具有項目層級角色指派的每一個使用者或群組建立系統層級角色指派。</span><span class="sxs-lookup"><span data-stu-id="a0b29-126">You should create a system-level role assignment for each user or group that has an item-level role assignment.</span></span>  
  
 <span data-ttu-id="a0b29-127">系統層級角色指派包括各種不同的權限，但是不包括屬於項目層級角色指派之一部分的權限。</span><span class="sxs-lookup"><span data-stu-id="a0b29-127">System-level role assignments include a wide range of permissions, but they do not include permissions that are part of an item-level role assignment.</span></span> <span data-ttu-id="a0b29-128">報表伺服器中的系統角色並不會傳遞包含完整之所有可能作業集合的中心權限，與電腦上的系統權限相反。</span><span class="sxs-lookup"><span data-stu-id="a0b29-128">In contrast with system permissions on a computer, system roles in Reporting Servers do not convey overarching permissions that include the full set of all possible operations.</span></span> <span data-ttu-id="a0b29-129">系統層級角色指派只是以報表伺服器站台為範圍的一組工作。</span><span class="sxs-lookup"><span data-stu-id="a0b29-129">Instead, system-level role assignments are simply a set of tasks that are scoped to the report server site.</span></span> <span data-ttu-id="a0b29-130">透過系統角色指派所傳遞的權限會決定使用者是否可以檢視應用程式屬性 (例如首頁的影像或標題)、檢視或管理共用排程或是使用報表產生器。</span><span class="sxs-lookup"><span data-stu-id="a0b29-130">Permissions that are conveyed through system role assignments determine whether users can view application properties (such as the image or title of the Home page), view or manage shared schedules, or use Report Builder.</span></span>  
  
 <span data-ttu-id="a0b29-131">如需詳細資訊，請參閱 [將報表伺服器的存取權授與使用者 &#40;報表管理員&#41;](grant-user-access-to-a-report-server.md) 和 [預先定義的角色](role-definitions-predefined-roles.md)。</span><span class="sxs-lookup"><span data-stu-id="a0b29-131">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) and [Predefined Roles](role-definitions-predefined-roles.md).</span></span>  
  
## <a name="modifying-a-role-assignment"></a><span data-ttu-id="a0b29-132">修改角色指派</span><span class="sxs-lookup"><span data-stu-id="a0b29-132">Modifying a Role Assignment</span></span>  
 <span data-ttu-id="a0b29-133">您可以在任何時候修改角色指派。</span><span class="sxs-lookup"><span data-stu-id="a0b29-133">You can modify a role assignment at any time.</span></span> <span data-ttu-id="a0b29-134">所做的變更會在儲存角色指派時生效。</span><span class="sxs-lookup"><span data-stu-id="a0b29-134">Your changes take effect when you save the role assignment.</span></span> <span data-ttu-id="a0b29-135">使用者工作階段不受角色指派變更的影響。</span><span class="sxs-lookup"><span data-stu-id="a0b29-135">User sessions are not affected by role assignment changes.</span></span> <span data-ttu-id="a0b29-136">如果使用者已開啟報表，而您將角色指派修改成拒絕存取，只要工作階段為使用中，使用者就可以繼續使用報表。</span><span class="sxs-lookup"><span data-stu-id="a0b29-136">If a user has a report open, and you modify a role assignment to deny access, the user can continue using the report as long as the session is active.</span></span>  
  
 <span data-ttu-id="a0b29-137">如果您將使用者帳戶加入至已經屬於某個角色指派的群組，則要經過一段延遲後，使用者帳戶才能透過群組帳戶原則存取項目。</span><span class="sxs-lookup"><span data-stu-id="a0b29-137">If you add a user account to a group that is already part of a role assignment, there will be a delay before the user account is able to access items through the group account policies.</span></span> <span data-ttu-id="a0b29-138">此延遲是 Internet Information Services (IIS) 快取驗證 Token 所造成的。</span><span class="sxs-lookup"><span data-stu-id="a0b29-138">This delay is caused by Internet Information Services (IIS) caching of authentication tokens.</span></span> <span data-ttu-id="a0b29-139">您可以等候 Token 重新整理 (等候期間通常是 15 分鐘)，或者可以重設 IIS 來立即更新快取。</span><span class="sxs-lookup"><span data-stu-id="a0b29-139">You can either wait for the tokens to refresh (typically, the wait period is fifteen minutes) or you can reset IIS to update the cache immediately.</span></span>  
  
 <span data-ttu-id="a0b29-140">您一次僅能修改一個角色指派。</span><span class="sxs-lookup"><span data-stu-id="a0b29-140">You can only modify one role assignment at a time.</span></span> <span data-ttu-id="a0b29-141">您無法執行全域搜尋與取代作業來變更角色定義名稱或角色指派設定，或者尋找所有包括特定使用者或群組的角色指派。</span><span class="sxs-lookup"><span data-stu-id="a0b29-141">You cannot perform a global search-and-replace operation to change role definition names or role assignment settings, or to find all the role assignments that include a specific user or group.</span></span>  
  
## <a name="deleting-a-role-assignment"></a><span data-ttu-id="a0b29-142">刪除角色指派</span><span class="sxs-lookup"><span data-stu-id="a0b29-142">Deleting a Role Assignment</span></span>  
 <span data-ttu-id="a0b29-143">您可以選取要刪除之每個指派旁的核取方塊，然後按一下 **[刪除]**，以刪除角色指派。</span><span class="sxs-lookup"><span data-stu-id="a0b29-143">You can delete role assignments by selecting the checkbox by each assignment you want to delete, and then clicking **Delete**.</span></span> <span data-ttu-id="a0b29-144">也可以按一下 **[還原為父安全性]**，以刪除角色指派。</span><span class="sxs-lookup"><span data-stu-id="a0b29-144">You can also delete role assignments by clicking **Revert to Parent Security**.</span></span> <span data-ttu-id="a0b29-145">當您按一下此按鈕時，會刪除項目的現有角色指派，並以父項目提供的角色指派來取代。</span><span class="sxs-lookup"><span data-stu-id="a0b29-145">When you click this button, the existing role assignments for the item are deleted, and those that are provided through a parent item are used instead.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0b29-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a0b29-146">See Also</span></span>  
 <span data-ttu-id="a0b29-147">[授與使用者對報表伺服器的存取權 &#40;報表管理員&#41;](grant-user-access-to-a-report-server.md) </span><span class="sxs-lookup"><span data-stu-id="a0b29-147">[Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md) </span></span>  
 <span data-ttu-id="a0b29-148">[修改或刪除角色指派 &#40;報表管理員&#41;](role-assignments-modify-or-delete.md) </span><span class="sxs-lookup"><span data-stu-id="a0b29-148">[Modify or Delete a Role Assignment &#40;Report Manager&#41;](role-assignments-modify-or-delete.md) </span></span>  
 <span data-ttu-id="a0b29-149">[角色指派](role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="a0b29-149">[Role Assignments](role-assignments.md) </span></span>  
 <span data-ttu-id="a0b29-150">[角色定義](role-definitions.md) </span><span class="sxs-lookup"><span data-stu-id="a0b29-150">[Role Definitions](role-definitions.md) </span></span>  
 <span data-ttu-id="a0b29-151">[預先定義的角色](role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="a0b29-151">[Predefined Roles](role-definitions-predefined-roles.md) </span></span>  
 [<span data-ttu-id="a0b29-152">在原生模式報表伺服器上授與權限</span><span class="sxs-lookup"><span data-stu-id="a0b29-152">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
