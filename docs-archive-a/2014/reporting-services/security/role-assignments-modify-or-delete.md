---
title: 修改或刪除角色指派 (報表管理員) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- roles [Reporting Services], assignments
- system roles [Reporting Services]
- modifying role assignments
- deleting role assignments
ms.assetid: 523bdd32-92cb-4b48-a3a9-d58b2385bde7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d67c5cdb7647d50008f72890e4ac3e3c7eed456e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700777"
---
# <a name="modify-or-delete-a-role-assignment-report-manager"></a><span data-ttu-id="147c7-102">修改或刪除角色指派 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="147c7-102">Modify or Delete a Role Assignment (Report Manager)</span></span>
  <span data-ttu-id="147c7-103">角色指派會將某個群組或使用者帳戶對應至包含可執行之工作的預先定義角色定義。</span><span class="sxs-lookup"><span data-stu-id="147c7-103">A role assignment maps a group or user account to a predefined role definition that includes tasks that can be performed.</span></span> <span data-ttu-id="147c7-104">它會決定某位使用者可執行的作業類型，包括資料夾、報表、模型或其他內容類型。</span><span class="sxs-lookup"><span data-stu-id="147c7-104">It determines the types of operations that a user can perform relative to a folder, report, model, or other content type.</span></span> <span data-ttu-id="147c7-105">若要建立、修改或刪除角色指派，您可以使用報表管理員。</span><span class="sxs-lookup"><span data-stu-id="147c7-105">To create, modify, or delete role assignments, you use Report Manager.</span></span> <span data-ttu-id="147c7-106">針對特定使用者或群組建立角色指派之後，您之後可以透過選取不同的角色，修改此指派。</span><span class="sxs-lookup"><span data-stu-id="147c7-106">After you create a role assignment for a particular user or group, you can modify it later by selecting a different role.</span></span> <span data-ttu-id="147c7-107">如果您想要撤銷報表伺服器的權限，可以從報表伺服器中刪除角色指派。</span><span class="sxs-lookup"><span data-stu-id="147c7-107">If you want to revoke permissions to a report server, you can delete a role assignment from the report server.</span></span>  
  
 <span data-ttu-id="147c7-108">根據您的目標而定，其他方式可能會更適合。</span><span class="sxs-lookup"><span data-stu-id="147c7-108">Depending on your objective, alternative approaches might be more appropriate.</span></span> <span data-ttu-id="147c7-109">範例包括自訂或建立新的角色定義，或在 Active Directory 中修改群組帳戶的成員資格。</span><span class="sxs-lookup"><span data-stu-id="147c7-109">Examples include customizing or creating a new role definition, or modifying the membership of a group account in Active Directory.</span></span>  
  
 <span data-ttu-id="147c7-110">例如，假設您擁有一個使用者群組，而這些使用者需要完全管理其內容，但是不應該擁有與內容管理員相關聯的完整權限集。</span><span class="sxs-lookup"><span data-stu-id="147c7-110">For example, suppose you have a group of users who need to fully manage their content, but should not have the full set of permissions associated with Content Manager.</span></span> <span data-ttu-id="147c7-111">在此情況下，您應該建立名為「部門內容管理員」的新角色定義，其中包含內容管理員的所有工作，但**設定項目的安全性原則**除外。</span><span class="sxs-lookup"><span data-stu-id="147c7-111">In this case, you could create a new role definition called Department Content Manager that includes all of the tasks in Content Manager except **Set security policies for items**.</span></span>  
  
 <span data-ttu-id="147c7-112">同樣地，如果您是系統或網路管理員，而且在報表管理員中管理 Active Directory 群組帳戶比角色指派更容易，就可以透過針對群組帳戶建立單一角色指派，降低管理角色指派的負擔，然後在使用者不再需要存取報表時調整群組成員資格。</span><span class="sxs-lookup"><span data-stu-id="147c7-112">Similarly, if you are a system or network administrator and it is easier for you to manage Active Directory group accounts than role assignments in Report Manager, you could reduce the overhead of managing role assignments by creating a single role assignment for a group account, and then adjust group membership when users no longer require access to reports.</span></span>  
  
 <span data-ttu-id="147c7-113">如果您決定修改或刪除角色指派是最佳做法，請務必同時檢查系統角色指派和項目角色指派。</span><span class="sxs-lookup"><span data-stu-id="147c7-113">If you determine that modifying or deleting a role assignment is the best approach, remember to check for both system role assignments and item role assignments.</span></span> <span data-ttu-id="147c7-114">每種角色指派類型都是透過報表管理員中的不同頁面進行設定的。</span><span class="sxs-lookup"><span data-stu-id="147c7-114">Each type of role assignment is configured through different pages in Report Manager.</span></span>  
  
### <a name="to-modify-or-delete-a-system-role-assignment"></a><span data-ttu-id="147c7-115">若要修改或刪除系統角色指派</span><span class="sxs-lookup"><span data-stu-id="147c7-115">To modify or delete a system role assignment</span></span>  
  
1.  <span data-ttu-id="147c7-116">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="147c7-116">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="147c7-117">按一下 **[站台設定]** 。</span><span class="sxs-lookup"><span data-stu-id="147c7-117">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="147c7-118">按一下 **[安全性]** 。</span><span class="sxs-lookup"><span data-stu-id="147c7-118">Click **Security**.</span></span> <span data-ttu-id="147c7-119">如此就會依據帳戶名稱列出目前針對伺服器或向外延展部署所定義的所有系統層級角色指派。</span><span class="sxs-lookup"><span data-stu-id="147c7-119">All system-level role assignments currently defined for the server or scale-out deployment are listed by account name.</span></span>  
  
4.  <span data-ttu-id="147c7-120">尋找您想要修改或刪除的角色指派。</span><span class="sxs-lookup"><span data-stu-id="147c7-120">Find the role assignment that you want to modify or delete.</span></span>  
  
5.  <span data-ttu-id="147c7-121">若要新增或移除特定使用者或群組的角色，請按一下 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="147c7-121">To add or remove the role for a particular user or group, click **Edit**.</span></span>  
  
6.  <span data-ttu-id="147c7-122">若要刪除角色指派，請按一下使用者或群組名稱旁的核取方塊，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="147c7-122">To delete a role assignment, click the check box next to the user or group name, and then click **Delete**.</span></span>  
  
### <a name="to-modify-or-delete-an-item-role-assignment"></a><span data-ttu-id="147c7-123">若要修改或刪除項目角色指派</span><span class="sxs-lookup"><span data-stu-id="147c7-123">To modify or delete an item role assignment</span></span>  
  
1.  <span data-ttu-id="147c7-124">啟動 [報表管理員]\*\*\*\* 並找出您想要編輯或刪除角色指派的項目。</span><span class="sxs-lookup"><span data-stu-id="147c7-124">Start **Report Manager** and locate the item for which you want to edit or delete a role assignment.</span></span>  
  
2.  <span data-ttu-id="147c7-125">將滑鼠停留在該項目上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="147c7-125">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="147c7-126">在下拉式功能表中，按一下 [安全性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="147c7-126">In the drop-down menu, click **Security**.</span></span>  
  
4.  <span data-ttu-id="147c7-127">尋找您想要修改或刪除的角色指派。</span><span class="sxs-lookup"><span data-stu-id="147c7-127">Find the role assignment that you want to modify or delete.</span></span>  
  
5.  <span data-ttu-id="147c7-128">若要新增或移除特定使用者或群組的角色，請按一下 [編輯]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="147c7-128">To add or remove the role for a particular user or group, click **Edit**.</span></span>  
  
6.  <span data-ttu-id="147c7-129">若要刪除角色指派，請按一下使用者或群組名稱旁的核取方塊，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="147c7-129">To delete a role assignment, click the check box next to the user or group name, and then click **Delete**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="147c7-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="147c7-130">See Also</span></span>  
 <span data-ttu-id="147c7-131"> (create-and-manage-role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="147c7-131">(create-and-manage-role-assignments.md)</span></span>   
 <span data-ttu-id="147c7-132">[角色指派](role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="147c7-132">[Role Assignments](role-assignments.md) </span></span>  
 <span data-ttu-id="147c7-133">[[網站設定] 頁面 &#40;報表管理員&#41;](../site-settings-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="147c7-133">[Site Settings Page &#40;Report Manager&#41;](../site-settings-page-report-manager.md) </span></span>  
 [<span data-ttu-id="147c7-134">新增系統角色指派：編輯系統角色指派頁面 &#40;報表管理員&#41;</span><span class="sxs-lookup"><span data-stu-id="147c7-134">New System Role Assignments: Edit System Role Assignments Page &#40;Report Manager&#41;</span></span>](../new-system-role-assignments-edit-system-role-assignments-page-report-manager.md)  
  
  
