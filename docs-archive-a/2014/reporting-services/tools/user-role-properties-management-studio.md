---
title: 使用者角色屬性 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.userroleproperties.f1
ms.assetid: c8b22236-a8b1-4e15-b1ff-4e1909b602d3
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f79953abdf5e3d1cdb03de8c5feeb6b2de34ab7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87700663"
---
# <a name="user-role-properties-management-studio"></a><span data-ttu-id="02462-102">使用者角色屬性 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="02462-102">User Role Properties (Management Studio)</span></span>
  <span data-ttu-id="02462-103">您可以使用這個頁面來檢視項目層級角色定義中包含的工作。</span><span class="sxs-lookup"><span data-stu-id="02462-103">Use this page to view which tasks are included in an item-level role definition.</span></span> <span data-ttu-id="02462-104">您也可以使用這個頁面來變更工作清單或修改角色描述。</span><span class="sxs-lookup"><span data-stu-id="02462-104">You can also use this page to change the task list or modify a role description.</span></span>  
  
 <span data-ttu-id="02462-105">項目層級角色定義是指使用者針對特定項目 (亦即，資料夾、報表或資源或共用資料來源) 所執行之工作的具名集合。</span><span class="sxs-lookup"><span data-stu-id="02462-105">An item-level role definition is a named collection of tasks that users perform relative to a specific item (that is, a folder, report, resource, or shared data source).</span></span> <span data-ttu-id="02462-106">角色定義會指派給使用者或群組，以便在報表管理員中建立角色指派。</span><span class="sxs-lookup"><span data-stu-id="02462-106">Role definitions are assigned to a user or group to create a role assignment in Report Manager.</span></span> <span data-ttu-id="02462-107">角色定義中的工作會描述使用者或群組可執行的工作。</span><span class="sxs-lookup"><span data-stu-id="02462-107">The tasks in the role definition describe what the user or group can do.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="02462-108">包含許多您可以使用之預先定義的項目層級角色定義。</span><span class="sxs-lookup"><span data-stu-id="02462-108">includes a number of predefined item-level role definitions that you can work with.</span></span> <span data-ttu-id="02462-109">您可以透過變更每個角色定義的工作清單，修改角色定義。</span><span class="sxs-lookup"><span data-stu-id="02462-109">You can modify the role definitions by changing the task list of each one.</span></span> <span data-ttu-id="02462-110">編輯角色定義將影響包含該角色定義的所有角色指派。</span><span class="sxs-lookup"><span data-stu-id="02462-110">Editing a role definition affects all role assignments that include the role definition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="02462-111">使用者角色指派只會用於以原生模式執行的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="02462-111">User role assignments are used only on a report server that runs in native mode.</span></span> <span data-ttu-id="02462-112">如果報表伺服器是針對 SharePoint 整合所設定，這個頁面就會顯示有關 SharePoint 網站上所定義之角色和權限等級的唯讀資訊。</span><span class="sxs-lookup"><span data-stu-id="02462-112">If the report server is configured for SharePoint integration, this page displays read-only information about the roles and permission levels that are defined on the SharePoint site.</span></span>  
  
## <a name="options"></a><span data-ttu-id="02462-113">選項。</span><span class="sxs-lookup"><span data-stu-id="02462-113">Options</span></span>  
 <span data-ttu-id="02462-114">**名稱**</span><span class="sxs-lookup"><span data-stu-id="02462-114">**Name**</span></span>  
 <span data-ttu-id="02462-115">指定角色定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="02462-115">Specifies the name of the role definition.</span></span>  
  
 <span data-ttu-id="02462-116">**說明**</span><span class="sxs-lookup"><span data-stu-id="02462-116">**Description**</span></span>  
 <span data-ttu-id="02462-117">顯示角色定義的描述。</span><span class="sxs-lookup"><span data-stu-id="02462-117">Shows a description of the role definition.</span></span> <span data-ttu-id="02462-118">在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中，這項描述只會出現在本頁面上。</span><span class="sxs-lookup"><span data-stu-id="02462-118">In [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], this description is only visible in this page.</span></span> <span data-ttu-id="02462-119">在報表管理員中，這項描述可協助使用者決定是否要在角色指派中使用角色。</span><span class="sxs-lookup"><span data-stu-id="02462-119">In Report Manager, this description helps users decide whether to use the role in a role assignment.</span></span>  
  
 <span data-ttu-id="02462-120">**Task**</span><span class="sxs-lookup"><span data-stu-id="02462-120">**Task**</span></span>  
 <span data-ttu-id="02462-121">列出可為此角色定義選取的所有項目層級工作。</span><span class="sxs-lookup"><span data-stu-id="02462-121">Lists all item-level tasks that can be selected for this role definition.</span></span> <span data-ttu-id="02462-122">您可以將項目加入預先定義的工作清單，或者從清單移除項目，以定義使用者藉由這個角色存取指定項目的方式。</span><span class="sxs-lookup"><span data-stu-id="02462-122">You can add or remove items from the predefined task list to define how users access a given item through this role.</span></span> <span data-ttu-id="02462-123">您不能建立新的工作，也不能修改現有的工作。</span><span class="sxs-lookup"><span data-stu-id="02462-123">You cannot create new tasks, and you cannot modify existing tasks.</span></span> <span data-ttu-id="02462-124">角色定義的工作清單只會顯示在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]中。</span><span class="sxs-lookup"><span data-stu-id="02462-124">The task list of a role definition appears only in [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
 <span data-ttu-id="02462-125">**工作描述**</span><span class="sxs-lookup"><span data-stu-id="02462-125">**Task Description**</span></span>  
 <span data-ttu-id="02462-126">提供每個工作的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="02462-126">Provides information about each task.</span></span> <span data-ttu-id="02462-127">您不能修改工作描述。</span><span class="sxs-lookup"><span data-stu-id="02462-127">You cannot modify task descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02462-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="02462-128">See Also</span></span>  
 <span data-ttu-id="02462-129">[項目層級工作](../security/tasks-and-permissions-item-level-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="02462-129">[Item-Level Tasks](../security/tasks-and-permissions-item-level-tasks.md) </span></span>  
 <span data-ttu-id="02462-130">[角色定義](../security/role-definitions.md) </span><span class="sxs-lookup"><span data-stu-id="02462-130">[Role Definitions](../security/role-definitions.md) </span></span>  
 <span data-ttu-id="02462-131">[Management Studio F1 說明中的報表伺服器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="02462-131">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="02462-132">[工作和權限](../security/tasks-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="02462-132">[Tasks and Permissions](../security/tasks-and-permissions.md) </span></span>  
 [<span data-ttu-id="02462-133">預先定義的角色</span><span class="sxs-lookup"><span data-stu-id="02462-133">Predefined Roles</span></span>](../security/role-definitions-predefined-roles.md)  
  
  
