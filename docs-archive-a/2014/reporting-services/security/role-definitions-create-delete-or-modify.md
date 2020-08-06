---
title: 建立、刪除或修改角色 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- roles [Reporting Services], creating
- deleting roles
- removing roles
- roles [Reporting Services], definitions
- modifying roles
- roles [Reporting Services], deleting
- roles [Reporting Services], modifying
ms.assetid: 3d1d56e6-a283-44a7-8417-36cb4d2c74d1
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 543bddda88e41af39d3200df4728716d46b3ae8b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87704849"
---
# <a name="create-delete-or-modify-a-role-management-studio"></a><span data-ttu-id="51ab6-102">建立、刪除或修改角色 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="51ab6-102">Create, Delete, or Modify a Role (Management Studio)</span></span>
  <span data-ttu-id="51ab6-103">Reporting Services 會提供定義報表伺服器之存取層級的預先定義角色。</span><span class="sxs-lookup"><span data-stu-id="51ab6-103">Reporting Services provides predefined roles that define a level of access to a report server.</span></span> <span data-ttu-id="51ab6-104">需要存取報表伺服器的每個使用者或群組會透過描述可執行之工作的角色來達成此目的。</span><span class="sxs-lookup"><span data-stu-id="51ab6-104">Each user or group who requires access to report server does so through a role that describes the tasks that can be performed.</span></span> <span data-ttu-id="51ab6-105">這些角色完全是針對報表伺服器所定義。</span><span class="sxs-lookup"><span data-stu-id="51ab6-105">Roles are defined for the report server as a whole.</span></span> <span data-ttu-id="51ab6-106">您無法針對報表伺服器的特定部分變更角色定義，或指定要根據情況以不同的方式使用某個角色。</span><span class="sxs-lookup"><span data-stu-id="51ab6-106">You cannot vary a role definition for specific parts of the report server, or specify that a role be used differently depending on the circumstances.</span></span>  
  
 <span data-ttu-id="51ab6-107">若要建立、修改或刪除角色，請使用 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="51ab6-107">To create, modify, or delete roles, use [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span> <span data-ttu-id="51ab6-108">您只能刪除未使用的角色。</span><span class="sxs-lookup"><span data-stu-id="51ab6-108">You can only delete roles that are not used.</span></span>  
  
 <span data-ttu-id="51ab6-109">若要將使用者和群組指派至您所建立的角色，請使用報表管理員。</span><span class="sxs-lookup"><span data-stu-id="51ab6-109">To assign users and groups to the roles that you create, use Report Manager.</span></span> <span data-ttu-id="51ab6-110">如需詳細資訊，請參閱[將報表伺服器的存取權授與使用者 &#40;報表管理員&#41;](grant-user-access-to-a-report-server.md)。</span><span class="sxs-lookup"><span data-stu-id="51ab6-110">For more information, see [Grant User Access to a Report Server &#40;Report Manager&#41;](grant-user-access-to-a-report-server.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="51ab6-111">如果報表伺服器是針對 SharePoint 整合模式所設定，而且您已連接至與報表伺服器整合的 SharePoint 網站，就可以檢視並修改權限等級，以便控制報表伺服器內容和作業的存取權。</span><span class="sxs-lookup"><span data-stu-id="51ab6-111">If the report server is configured for SharePoint integrated mode, and you connected to the SharePoint site that the report server is integrated with, you can view and modify the permission levels that control access to report server content and operations.</span></span>  
  
### <a name="to-create-a-role-definition"></a><span data-ttu-id="51ab6-112">若要建立角色定義</span><span class="sxs-lookup"><span data-stu-id="51ab6-112">To create a role definition</span></span>  
  
1.  <span data-ttu-id="51ab6-113">在 [物件總管] 中，展開報表伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="51ab6-113">In Object Explorer, expand a report server node.</span></span>  
  
2.  <span data-ttu-id="51ab6-114">展開安全性資料夾。</span><span class="sxs-lookup"><span data-stu-id="51ab6-114">Expand the Security folder.</span></span>  
  
3.  <span data-ttu-id="51ab6-115">如果您要建立項目層級角色定義，請以滑鼠右鍵按一下 [角色]\*\*\*\*，然後指向 [新增角色]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="51ab6-115">If you are creating an item-level role definition, right-click **Roles**, and point to **New Role**.</span></span>  
  
     <span data-ttu-id="51ab6-116">如果您要建立系統層級角色定義，請以滑鼠右鍵按一下 [系統角色]\*\*\*\*，然後指向 [新增系統角色]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="51ab6-116">Or, if you are creating a system-level role definition, right-click **System Roles**, and point to **New System Role**.</span></span>  
  
4.  <span data-ttu-id="51ab6-117">為角色輸入唯一的名稱。</span><span class="sxs-lookup"><span data-stu-id="51ab6-117">Type a unique name for the role.</span></span> <span data-ttu-id="51ab6-118">名稱至少必須包含一個字元。</span><span class="sxs-lookup"><span data-stu-id="51ab6-118">A name must contain at least one character.</span></span> <span data-ttu-id="51ab6-119">它也可以包括空格和特定符號，但不得包括下列字元：; ?</span><span class="sxs-lookup"><span data-stu-id="51ab6-119">It can also include spaces and certain symbols, but not the characters ; ?</span></span> <span data-ttu-id="51ab6-120">： \@ & = +，$/\* \< > |"或/。</span><span class="sxs-lookup"><span data-stu-id="51ab6-120">: \@ & = + , $ / \* \< > | " or /.</span></span>  
  
5.  <span data-ttu-id="51ab6-121">選擇性地輸入描述。</span><span class="sxs-lookup"><span data-stu-id="51ab6-121">Optionally type a description.</span></span> <span data-ttu-id="51ab6-122">在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，此描述僅會出現在本頁面上。</span><span class="sxs-lookup"><span data-stu-id="51ab6-122">In [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] this description is visible only on this page.</span></span> <span data-ttu-id="51ab6-123">透過報表管理員檢視此項目的使用者，可以在該工具中看到此描述。</span><span class="sxs-lookup"><span data-stu-id="51ab6-123">Users who view this item through Report Manager can see this description in that tool.</span></span>  
  
6.  <span data-ttu-id="51ab6-124">選取這個角色的成員可以執行的工作。</span><span class="sxs-lookup"><span data-stu-id="51ab6-124">Select the tasks that members of this role can perform.</span></span>  
  
7.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-or-modify-a-role-definition"></a><span data-ttu-id="51ab6-125">若要刪除或修改角色定義</span><span class="sxs-lookup"><span data-stu-id="51ab6-125">To delete or modify a role definition</span></span>  
  
1.  <span data-ttu-id="51ab6-126">在 [物件總管] 中，展開報表伺服器節點。</span><span class="sxs-lookup"><span data-stu-id="51ab6-126">In Object Explorer, expand a report server node.</span></span>  
  
2.  <span data-ttu-id="51ab6-127">展開安全性資料夾。</span><span class="sxs-lookup"><span data-stu-id="51ab6-127">Expand the Security folder.</span></span>  
  
3.  <span data-ttu-id="51ab6-128">若要刪除或修改項目層級的角色定義，請展開 [角色] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="51ab6-128">To delete or modify an item-level role definition, expand the Roles folder.</span></span> <span data-ttu-id="51ab6-129">執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="51ab6-129">Perform one of the following:</span></span>  
  
    1.  <span data-ttu-id="51ab6-130">若要刪除角色定義，請以滑鼠右鍵按一下項目，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="51ab6-130">To delete a role definition, right-click the item and click **Delete**.</span></span> <span data-ttu-id="51ab6-131">就會顯示 **[刪除物件]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="51ab6-131">The **Delete Object** dialog box is displayed.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    2.  <span data-ttu-id="51ab6-132">若要修改角色定義，請以滑鼠右鍵按一下項目，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="51ab6-132">To modify a role definition, right-click the item and click **Properties**.</span></span> <span data-ttu-id="51ab6-133">就會顯示 **[使用者角色屬性]** 對話方塊的 [一般] 頁面。</span><span class="sxs-lookup"><span data-stu-id="51ab6-133">The General page of the **User Role Properties** dialog box is displayed.</span></span>  
  
         <span data-ttu-id="51ab6-134">選取這個角色的成員可以執行的工作，然後按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="51ab6-134">Select the tasks that members of this role can perform, and click **OK**.</span></span>  
  
4.  <span data-ttu-id="51ab6-135">若要刪除或修改系統層級角色定義，請展開 [系統角色]  資料夾。</span><span class="sxs-lookup"><span data-stu-id="51ab6-135">To delete or modify a system-level role definition, expand the **System Roles** folder.</span></span> <span data-ttu-id="51ab6-136">執行下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="51ab6-136">Perform one of the following:</span></span>  
  
    1.  <span data-ttu-id="51ab6-137">若要刪除系統角色定義，請以滑鼠右鍵按一下項目，然後按一下 [刪除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="51ab6-137">To delete a system role definition, right-click the item and click **Delete**.</span></span> <span data-ttu-id="51ab6-138">就會顯示 **[刪除物件]** 對話方塊。</span><span class="sxs-lookup"><span data-stu-id="51ab6-138">The **Delete Object** dialog box is displayed.</span></span> [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
    2.  <span data-ttu-id="51ab6-139">若要修改系統角色定義，請以滑鼠右鍵按一下項目，然後按一下 [屬性]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="51ab6-139">To modify a system role definition, right-click the item and click **Properties**.</span></span> <span data-ttu-id="51ab6-140">就會顯示 **[系統角色屬性]** 對話方塊的 [一般] 頁面。</span><span class="sxs-lookup"><span data-stu-id="51ab6-140">The General page of the **System Role Properties** dialog box is displayed.</span></span>  
  
         <span data-ttu-id="51ab6-141">選取這個角色的成員可以執行的工作，然後按一下 **[確定]** 來套用變更。</span><span class="sxs-lookup"><span data-stu-id="51ab6-141">Select the tasks that members of this role can perform, and click **OK** to apply the changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51ab6-142">另請參閱</span><span class="sxs-lookup"><span data-stu-id="51ab6-142">See Also</span></span>  
 <span data-ttu-id="51ab6-143">[連接到 Management Studio 中的報表伺服器](../tools/connect-to-a-report-server-in-management-studio.md) </span><span class="sxs-lookup"><span data-stu-id="51ab6-143">[Connect to a Report Server in Management Studio](../tools/connect-to-a-report-server-in-management-studio.md) </span></span>  
 <span data-ttu-id="51ab6-144"> (create-and-manage-role-assignments.md) </span><span class="sxs-lookup"><span data-stu-id="51ab6-144">(create-and-manage-role-assignments.md)</span></span>   
 [<span data-ttu-id="51ab6-145">SQL Server Management Studio 中的 Reporting Services &#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="51ab6-145">Reporting Services in SQL Server Management Studio &#40;SSRS&#41;</span></span>](../tools/reporting-services-in-sql-server-management-studio-ssrs.md)  
  
  
