---
title: 工作與權限 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- permissions [Reporting Services], tasks
- role-based security [Reporting Services], permissions
- security [Reporting Services], tasks
- security [Reporting Services], permissions
- role-based security [Reporting Services], tasks
- predefined tasks [Reporting Services]
- tasks [Reporting Services]
ms.assetid: d7ff90b5-b976-4270-b9ad-9d7b801d8263
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 01cbf00850c5dd57e7ca1575a1a0cb826c009714
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707006"
---
# <a name="tasks-and-permissions"></a><span data-ttu-id="2b632-102">工作和權限</span><span class="sxs-lookup"><span data-stu-id="2b632-102">Tasks and Permissions</span></span>
  <span data-ttu-id="2b632-103">在 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] 中，「工作」  (Task) 是使用者或管理員可以執行的動作。</span><span class="sxs-lookup"><span data-stu-id="2b632-103">In [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], *tasks* are actions that a user or administrator can perform.</span></span> <span data-ttu-id="2b632-104">工作是預先定義的。</span><span class="sxs-lookup"><span data-stu-id="2b632-104">Tasks are predefined.</span></span> <span data-ttu-id="2b632-105">您無法建立自訂工作或修改以程式設計的方式或透過工具而提供的工作。</span><span class="sxs-lookup"><span data-stu-id="2b632-105">You cannot create custom tasks or modify the ones provided either programmatically or through a tool.</span></span> <span data-ttu-id="2b632-106">總共有 25 種工作。</span><span class="sxs-lookup"><span data-stu-id="2b632-106">There are twenty-five tasks in all.</span></span> <span data-ttu-id="2b632-107">這些工作構成以角色為基礎之安全性中，可以使用的整個作業集。</span><span class="sxs-lookup"><span data-stu-id="2b632-107">These tasks comprise the entire set of operations that are available in role-based security.</span></span> <span data-ttu-id="2b632-108">工作的範例包括「檢視報表」、「管理報表」以及「管理報表伺服器屬性」。</span><span class="sxs-lookup"><span data-stu-id="2b632-108">Some examples of tasks include "View reports," "Manage reports," and "Manage report server properties."</span></span>  
  
 <span data-ttu-id="2b632-109">每一個工作包含一組也是預先定義的權限。</span><span class="sxs-lookup"><span data-stu-id="2b632-109">Each task consists of a set of permissions, which are also predefined.</span></span> <span data-ttu-id="2b632-110">例如，「管理資料夾」工作包含建立和刪除資料夾，以及檢視和更新資料夾屬性的權限。</span><span class="sxs-lookup"><span data-stu-id="2b632-110">For example, the "Manage folders" task contains permissions to create and delete folders and view and update folder properties.</span></span> <span data-ttu-id="2b632-111">每一種工作的權限都有文件說明，以提供每一種工作的更精確描述。</span><span class="sxs-lookup"><span data-stu-id="2b632-111">Permissions for each task are documented to provide a more exact description of each task.</span></span> <span data-ttu-id="2b632-112">無法直接與權限互動，或在角色指派中指定權限。</span><span class="sxs-lookup"><span data-stu-id="2b632-112">It is not possible to interact with permissions directly or to specify them in role assignments.</span></span> <span data-ttu-id="2b632-113">使用者是透過包括在角色定義中的工作，間接被授與權限。</span><span class="sxs-lookup"><span data-stu-id="2b632-113">Users are granted permissions indirectly through the tasks that are included in role definitions.</span></span>  
  
 <span data-ttu-id="2b632-114">唯有工作屬於角色的一部份，而該角色包含在角色指派中時，才能執行工作。</span><span class="sxs-lookup"><span data-stu-id="2b632-114">Tasks can be performed only if they are part of a role and that role is included in a role assignment.</span></span> <span data-ttu-id="2b632-115">因此，角色中若未包含檢視模型工作，或該角色未包含在角色指派中，使用者就無法檢視報表模型。</span><span class="sxs-lookup"><span data-stu-id="2b632-115">Thus, if the View Models task is not included in a role, or that role is not included in a role assignment, users cannot view report models.</span></span> <span data-ttu-id="2b632-116">下列圖表顯示如何將權限結合到工作中，以及如何將工作結合到可用於特定角色指派的角色中。</span><span class="sxs-lookup"><span data-stu-id="2b632-116">The following diagram shows how permissions are combined into tasks, and how tasks are combined into roles that can be used for specific role assignments.</span></span>  
  
 <span data-ttu-id="2b632-117">![權限和工作圖表](../media/report-securityobjects.gif "權限和工作圖表")</span><span class="sxs-lookup"><span data-stu-id="2b632-117">![Permissions and task diagram](../media/report-securityobjects.gif "Permissions and task diagram")</span></span>  
<span data-ttu-id="2b632-118">權限和工作圖表</span><span class="sxs-lookup"><span data-stu-id="2b632-118">Permissions and task diagram</span></span>  
  
## <a name="system-and-item-level-tasks"></a><span data-ttu-id="2b632-119">系統和項目層級工作</span><span class="sxs-lookup"><span data-stu-id="2b632-119">System and Item Level Tasks</span></span>  
 <span data-ttu-id="2b632-120">工作分成兩個類別目錄：系統層級和項目層級。</span><span class="sxs-lookup"><span data-stu-id="2b632-120">Tasks fall into two categories: system level and item level.</span></span> <span data-ttu-id="2b632-121">角色可以包括僅來自單一類別目錄的工作。</span><span class="sxs-lookup"><span data-stu-id="2b632-121">A role can include tasks only from a single category.</span></span> <span data-ttu-id="2b632-122">下表描述每一種類別目錄的工作。</span><span class="sxs-lookup"><span data-stu-id="2b632-122">The following table describes each category of tasks.</span></span>  
  
|<span data-ttu-id="2b632-123">類別</span><span class="sxs-lookup"><span data-stu-id="2b632-123">Category</span></span>|<span data-ttu-id="2b632-124">描述</span><span class="sxs-lookup"><span data-stu-id="2b632-124">Description</span></span>|  
|--------------|-----------------|  
|[<span data-ttu-id="2b632-125">項目層級工作</span><span class="sxs-lookup"><span data-stu-id="2b632-125">Item-Level Tasks</span></span>](tasks-and-permissions-item-level-tasks.md)|<span data-ttu-id="2b632-126">在資料夾、報表、報表模型和資源等受到報表伺服器管理之項目上執行的動作。</span><span class="sxs-lookup"><span data-stu-id="2b632-126">Actions that are performed on items managed by a report server, such as folders, reports, report models, and resources.</span></span><br /><br /> <span data-ttu-id="2b632-127">項目層級工作的範圍為報表伺服器資料夾命名空間。</span><span class="sxs-lookup"><span data-stu-id="2b632-127">Item-level tasks are scoped to the report server folder namespace.</span></span> <span data-ttu-id="2b632-128">您透過報表伺服器上的資料夾，或者透過 URL 存取的所有項目，都受到包含項目層級工作之角色指派的保護。</span><span class="sxs-lookup"><span data-stu-id="2b632-128">All items that you access through the folders on a report server or through URL access are secured by role assignments that include item-level tasks.</span></span>|  
|[<span data-ttu-id="2b632-129">系統層級工作</span><span class="sxs-lookup"><span data-stu-id="2b632-129">System-Level Tasks</span></span>](tasks-and-permissions-system-level-tasks.md)|<span data-ttu-id="2b632-130">在系統層級執行的動作，例如管理作業或可以用於許多項目的共用排程。</span><span class="sxs-lookup"><span data-stu-id="2b632-130">Actions that are performed at the system level, such as managing jobs or shared schedules that can be used with many items.</span></span> <span data-ttu-id="2b632-131">系統層級工作的範圍是在報表伺服器資料夾命名空間以外。</span><span class="sxs-lookup"><span data-stu-id="2b632-131">System-level tasks are scoped outside of the report server folder namespace.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2b632-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2b632-132">See Also</span></span>  
 <span data-ttu-id="2b632-133">[角色定義](role-definitions.md) </span><span class="sxs-lookup"><span data-stu-id="2b632-133">[Role Definitions](role-definitions.md) </span></span>  
 <span data-ttu-id="2b632-134">[Predefined Roles](role-definitions-predefined-roles.md) </span><span class="sxs-lookup"><span data-stu-id="2b632-134">[Predefined Roles](role-definitions-predefined-roles.md) </span></span>  
 [<span data-ttu-id="2b632-135">在原生模式報表伺服器上授與權限</span><span class="sxs-lookup"><span data-stu-id="2b632-135">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
