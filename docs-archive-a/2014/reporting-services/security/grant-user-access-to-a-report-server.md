---
title: 授與使用者對報表伺服器的存取權 (報表管理員) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- removing role assignments
- permissions [Reporting Services], granting report server access
- roles [Reporting Services], assignments
- modifying role assignments
- deleting role assignments
ms.assetid: 2144c020-3253-4b47-8cda-e14c928bb471
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: bceaa648827d756e2b301662ce281b37a76d6839
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87688486"
---
# <a name="grant-user-access-to-a-report-server-report-manager"></a><span data-ttu-id="8c748-102">將報表伺服器的存取權授與使用者 (報表管理員)</span><span class="sxs-lookup"><span data-stu-id="8c748-102">Grant User Access to a Report Server (Report Manager)</span></span>
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="8c748-103">使用角色型安全性將報表伺服器的存取權授與使用者。</span><span class="sxs-lookup"><span data-stu-id="8c748-103">uses role-based security to grant user access to a report server.</span></span> <span data-ttu-id="8c748-104">在新的報表伺服器安裝上，只有屬於本機管理員群組的成員擁有報表伺服器內容和作業的權限。</span><span class="sxs-lookup"><span data-stu-id="8c748-104">On a new report server installation, only users who are members of the local Administrators group have permissions to report server content and operations.</span></span> <span data-ttu-id="8c748-105">若要讓報表伺服器供其他使用者使用，您必須建立角色指派，以便將使用者或群組帳戶對應至指定工作集合的預先定義角色。</span><span class="sxs-lookup"><span data-stu-id="8c748-105">To make the report server available to other users, you must create role assignments that map  user or group accounts to a predefined role that specifies a collection of tasks.</span></span>  
  
 <span data-ttu-id="8c748-106">**SharePoint 模式報表伺服器：** 若為針對 SharePoint 整合模式所設定的報表伺服器，您可以設定使用 SharePoint 權限從 SharePoint 網站存取的方式。</span><span class="sxs-lookup"><span data-stu-id="8c748-106">**SharePoint mode report servers:** For a report server that is configured for SharePoint integrated mode, you configure access from a SharePoint site using SharePoint permissions.</span></span> <span data-ttu-id="8c748-107">SharePoint 網站的權限等級會決定報表伺服器內容和作業的存取權。</span><span class="sxs-lookup"><span data-stu-id="8c748-107">Permission levels on the SharePoint site determine access to report server content and operations.</span></span> <span data-ttu-id="8c748-108">您必須是網站管理員，才能授與 SharePoint 網站的權限。</span><span class="sxs-lookup"><span data-stu-id="8c748-108">You must be a site administrator to grant permissions on a SharePoint site.</span></span> <span data-ttu-id="8c748-109">如需詳細資訊，請參閱 [授與 SharePoint 網站上報表伺服器項目的權限](granting-permissions-on-report-server-items-on-a-sharepoint-site.md)。</span><span class="sxs-lookup"><span data-stu-id="8c748-109">For more information, see [Granting Permissions on Report Server Items on a SharePoint Site](granting-permissions-on-report-server-items-on-a-sharepoint-site.md).</span></span>  
  
 <span data-ttu-id="8c748-110">**原生模式報表伺服器：** 此主題的重點在於為原生模式所設定的報表伺服器，以及使用報表管理員將使用者指派至角色。</span><span class="sxs-lookup"><span data-stu-id="8c748-110">**Native mode report servers:** This topic is focused on a report server that is configured for native mode and the use of Report Manager to assign users to a role.</span></span> <span data-ttu-id="8c748-111">目前有兩種角色類型：</span><span class="sxs-lookup"><span data-stu-id="8c748-111">There are two types of roles:</span></span>  
  
-   <span data-ttu-id="8c748-112">項目層級角色是用來檢視、加入和管理報表伺服器內容、訂閱、報表處理，以及報表記錄。</span><span class="sxs-lookup"><span data-stu-id="8c748-112">Item-level roles are used to view, add, and manage report server content, subscriptions, report processing, and report history.</span></span> <span data-ttu-id="8c748-113">項目層級角色指派定義於根節點 ([主資料夾] 資料夾) 或階層中更低的特定資料夾或項目上。</span><span class="sxs-lookup"><span data-stu-id="8c748-113">Item-level role assignments are defined on the root node (the Home folder) or on specific folders or items farther down the hierarchy.</span></span>  
  
-   <span data-ttu-id="8c748-114">系統層級角色會授與並未繫結至任何特定項目之網站範圍作業的存取權。</span><span class="sxs-lookup"><span data-stu-id="8c748-114">System-level roles grant access to site-wide operations that are not bound to any specific item.</span></span> <span data-ttu-id="8c748-115">範例包括使用報表產生器和使用共用排程。</span><span class="sxs-lookup"><span data-stu-id="8c748-115">Examples include using Report Builder and using shared schedules.</span></span>  
  
     <span data-ttu-id="8c748-116">這兩種角色類型彼此互補，而且您應該一起使用它們。</span><span class="sxs-lookup"><span data-stu-id="8c748-116">The two types of roles complement each other and should be used together.</span></span> <span data-ttu-id="8c748-117">因此，將使用者加入至報表伺服器是兩個部分的作業。</span><span class="sxs-lookup"><span data-stu-id="8c748-117">For this reason, adding a user to a report server is a two-part operation.</span></span> <span data-ttu-id="8c748-118">如果您將某位使用者指派至項目層級角色，就應該同時將他指派至伺服器層級角色。</span><span class="sxs-lookup"><span data-stu-id="8c748-118">If you assign a user to an item-level role, you should also assign them to a system-level role.</span></span> <span data-ttu-id="8c748-119">指派使用者至角色時，您必須選取已經定義的角色。</span><span class="sxs-lookup"><span data-stu-id="8c748-119">When assigning a user to a role, you must select a role that is already defined.</span></span> <span data-ttu-id="8c748-120">若要建立、修改或刪除角色，請使用 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="8c748-120">To create, modify, or delete roles, use [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)].</span></span> <span data-ttu-id="8c748-121">如需這些預先定義角色的詳細資訊，請參閱 [建立、刪除或修改角色 &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md)。</span><span class="sxs-lookup"><span data-stu-id="8c748-121">For more information, see [Create, Delete, or Modify a Role &#40;Management Studio&#41;](role-definitions-create-delete-or-modify.md).</span></span>  
  
## <a name="before-you-start"></a><span data-ttu-id="8c748-122">開始之前</span><span class="sxs-lookup"><span data-stu-id="8c748-122">Before you start</span></span>  
 <span data-ttu-id="8c748-123">將使用者加入至原生模式報表伺服器之前，請檢閱下列清單。</span><span class="sxs-lookup"><span data-stu-id="8c748-123">Review the following list before adding users to a native mode report server.</span></span>  
  
-   <span data-ttu-id="8c748-124">您在報表伺服器電腦上必須是本機管理員群組的成員。</span><span class="sxs-lookup"><span data-stu-id="8c748-124">You must be a member of the local Administrators group on the report server computer.</span></span> <span data-ttu-id="8c748-125">如果您要將 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 部署在 [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] 或 Windows Server 2008 上，就必須進行其他組態設定，然後才能在本機管理報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="8c748-125">If you are deploying [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] on [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)] or Windows Server 2008, additional configuration is required before you can administer a report server locally.</span></span> <span data-ttu-id="8c748-126">如需詳細資訊，請參閱 [設定原生模式報表伺服器進行本機管理 &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md)。</span><span class="sxs-lookup"><span data-stu-id="8c748-126">For more information, see [Configure a Native Mode Report Server for Local Administration &#40;SSRS&#41;](../report-server/configure-a-native-mode-report-server-for-local-administration-ssrs.md).</span></span>  
  
-   <span data-ttu-id="8c748-127">若要將這項工作委派給其他使用者，請建立角色指派，以便將使用者帳戶對應至「內容管理員」和「系統管理員」角色。</span><span class="sxs-lookup"><span data-stu-id="8c748-127">To delegate this task to other users, create role assignments that map user accounts to Content Manager and System Administrator roles.</span></span> <span data-ttu-id="8c748-128">擁有「內容管理員」和「系統管理員」權限的使用者可以將使用者加入至報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="8c748-128">Users who have Content Manager and System Administrator permissions can add users to a report server.</span></span>  
  
-   <span data-ttu-id="8c748-129">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，檢視「系統角色」和「使用者角色」的預先定義角色，如此您就可以熟悉每個角色的工作類型。</span><span class="sxs-lookup"><span data-stu-id="8c748-129">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], view the predefined roles for System Roles and User Roles so that you are familiar with the kinds of tasks in each role.</span></span> <span data-ttu-id="8c748-130">由於工作描述不會顯示在報表管理員中，因此在您開始加入使用者之前，應該會想要先熟悉這些角色。</span><span class="sxs-lookup"><span data-stu-id="8c748-130">Task descriptions are not visible in Report Manager, so you will want to be familiar with the roles before you begin adding users.</span></span>  
  
-   <span data-ttu-id="8c748-131">(選擇性) 您可以自訂角色或定義其他角色來包含所需的工作集合。</span><span class="sxs-lookup"><span data-stu-id="8c748-131">Optionally, customize the roles or define additional roles to include the collection of tasks that you require.</span></span> <span data-ttu-id="8c748-132">例如，如果您計畫針對個別項目使用自訂安全性設定，可能會想要建立新角色定義，以便授與資料夾的檢視存取權。</span><span class="sxs-lookup"><span data-stu-id="8c748-132">For example, if you plan to use custom security settings for individual items, you might want to create a new role definition that grants view-access to folders.</span></span>  
  
### <a name="to-add-a-user-or-group-to-a-system-role"></a><span data-ttu-id="8c748-133">若要將使用者或群組加入至系統角色</span><span class="sxs-lookup"><span data-stu-id="8c748-133">To add a user or group to a system role</span></span>  
  
1.  <span data-ttu-id="8c748-134">啟動 [報表管理員 &#40;SSRS 原生模式&#41;](../report-manager-ssrs-native-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="8c748-134">Start [Report Manager  &#40;SSRS Native Mode&#41;](../report-manager-ssrs-native-mode.md).</span></span>  
  
2.  <span data-ttu-id="8c748-135">按一下 **[站台設定]** 。</span><span class="sxs-lookup"><span data-stu-id="8c748-135">Click **Site Settings**.</span></span>  
  
3.  <span data-ttu-id="8c748-136">按一下 **[安全性]** 。</span><span class="sxs-lookup"><span data-stu-id="8c748-136">Click **Security**.</span></span>  
  
4.  <span data-ttu-id="8c748-137">按一下 **[新增角色指派]**。</span><span class="sxs-lookup"><span data-stu-id="8c748-137">Click **New Role Assignment**.</span></span>  
  
5.  <span data-ttu-id="8c748-138">在 [**群組或使用者名稱**] 中，以下列格式輸入 Windows 網域使用者或群組帳戶： \<domain> \\<帳戶] \> 。</span><span class="sxs-lookup"><span data-stu-id="8c748-138">In **Group or user name**, enter a Windows domain user or group account in this format: \<domain>\\<account\>.</span></span> <span data-ttu-id="8c748-139">如果您要使用表單驗證或自訂安全性，請使用適用於部署的正確格式來指定使用者或群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="8c748-139">If you are using forms authentication or custom security, specify the user or group account in the format that is correct for your deployment.</span></span>  
  
6.  <span data-ttu-id="8c748-140">選取系統角色，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8c748-140">Select a system role, and then click **OK**.</span></span>  
  
     <span data-ttu-id="8c748-141">由於角色是累計的，因此如果您同時選取「系統管理員」和「系統使用者」，則使用者或群組就能夠以這兩種角色來執行工作。</span><span class="sxs-lookup"><span data-stu-id="8c748-141">Roles are cumulative, so if you select both System Administrator and System User, a user or group will be able to perform the tasks in both roles.</span></span>  
  
7.  <span data-ttu-id="8c748-142">重複上述步驟，以便建立其他使用者或群組的指派。</span><span class="sxs-lookup"><span data-stu-id="8c748-142">Repeat to create assignments for additional users or groups.</span></span>  
  
### <a name="to-add-a-user-or-group-to-an-item-role"></a><span data-ttu-id="8c748-143">若要將使用者或群組加入至項目角色</span><span class="sxs-lookup"><span data-stu-id="8c748-143">To add a user or group to an item role</span></span>  
  
1.  <span data-ttu-id="8c748-144">啟動 **[報表管理員]** 並找出您想要加入使用者或群組的報表項目。</span><span class="sxs-lookup"><span data-stu-id="8c748-144">Start **Report Manager** and locate the report item for which you want to add a user or group.</span></span>  
  
2.  <span data-ttu-id="8c748-145">將滑鼠停留在該項目上，然後按一下下拉箭號。</span><span class="sxs-lookup"><span data-stu-id="8c748-145">Hover over the item, and click the drop-down arrow.</span></span>  
  
3.  <span data-ttu-id="8c748-146">在下拉式功能表中，按一下 [安全性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="8c748-146">In the drop-down menu, click **Security**.</span></span>  
  
4.  <span data-ttu-id="8c748-147">按一下 **[新增角色指派]**。</span><span class="sxs-lookup"><span data-stu-id="8c748-147">Click **New Role Assignment**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="8c748-148"> 如果某個項目目前是從父項目繼承安全性，請按一下工具列中的 **[編輯項目安全性]** 來變更安全性設定。</span><span class="sxs-lookup"><span data-stu-id="8c748-148">If an item currently inherits security from a parent item, click **Edit Item Security** in the toolbar to change the security settings.</span></span> <span data-ttu-id="8c748-149">然後，按一下 **[新增角色指派]**。</span><span class="sxs-lookup"><span data-stu-id="8c748-149">Then click **New Role Assignment**.</span></span>  
  
5.  <span data-ttu-id="8c748-150">在 [**群組或使用者名稱**] 中，以下列格式輸入 Windows 網域使用者或群組帳戶： \<domain> \\<帳戶] \> 。</span><span class="sxs-lookup"><span data-stu-id="8c748-150">In **Group or user name**, enter a Windows domain user or group account in this format: \<domain>\\<account\>.</span></span> <span data-ttu-id="8c748-151">如果您要使用表單驗證或自訂安全性，請使用適用於部署的正確格式來指定使用者或群組帳戶。</span><span class="sxs-lookup"><span data-stu-id="8c748-151">If you are using forms authentication or custom security, specify the user or group account in the format that is correct for your deployment.</span></span>  
  
6.  <span data-ttu-id="8c748-152">選取描述使用者或群組應如何存取項目的一或多個角色定義，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="8c748-152">Select one or more role definitions that describe how the user or group should access the item, and then click **OK**.</span></span>  
  
7.  <span data-ttu-id="8c748-153">重複上述步驟，以便建立其他使用者或群組的指派。</span><span class="sxs-lookup"><span data-stu-id="8c748-153">Repeat to create assignments for additional users or groups.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c748-154">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8c748-154">See Also</span></span>  
 <span data-ttu-id="8c748-155"> (create-and-manage-role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="8c748-155">(create-and-manage-role-assignments.md)</span></span>   
 <span data-ttu-id="8c748-156">[新增角色指派：編輯角色指派頁面 &#40;報表管理員&#41;](../new-role-assignment-edit-role-assignment-page-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="8c748-156">[New Role Assignment: Edit Role Assignment Page &#40;Report Manager&#41;](../new-role-assignment-edit-role-assignment-page-report-manager.md) </span></span>  
 <span data-ttu-id="8c748-157">[安全性屬性頁面，&#40;報表管理員的專案&#41;](../security-properties-page-items-report-manager.md) </span><span class="sxs-lookup"><span data-stu-id="8c748-157">[Security Properties Page, Items &#40;Report Manager&#41;](../security-properties-page-items-report-manager.md) </span></span>  
 <span data-ttu-id="8c748-158">[角色指派](role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="8c748-158">[Role Assignments](role-assignments.md) </span></span>  
 [<span data-ttu-id="8c748-159">角色定義</span><span class="sxs-lookup"><span data-stu-id="8c748-159">Role Definitions</span></span>](role-definitions.md)  
  
  
