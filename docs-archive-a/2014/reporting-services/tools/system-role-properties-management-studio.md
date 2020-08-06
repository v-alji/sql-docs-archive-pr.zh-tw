---
title: 系統角色屬性 (Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.swb.reportserver.systemroleproperties.f1
ms.assetid: 0210fc2a-74fb-41dd-8e39-4830047ec417
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b37ebb1cb95d6628884d81156c9c1bc29bff86fd
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593260"
---
# <a name="system-role-properties-management-studio"></a><span data-ttu-id="820b6-102">系統角色屬性 (Management Studio)</span><span class="sxs-lookup"><span data-stu-id="820b6-102">System Role Properties (Management Studio)</span></span>
  <span data-ttu-id="820b6-103">您可以使用 [系統角色] 頁面來檢視目前為報表伺服器定義的系統角色定義。</span><span class="sxs-lookup"><span data-stu-id="820b6-103">Use the System Roles page to view the system role definitions that are currently defined for the report server.</span></span> <span data-ttu-id="820b6-104">系統角色定義包含相對於整個網站 (而非個別項目) 所執行之工作的具名集合。</span><span class="sxs-lookup"><span data-stu-id="820b6-104">A system role definition contains a named collection of tasks that are performed relative to the entire site, instead of an individual item.</span></span> <span data-ttu-id="820b6-105">角色定義會指派給使用者或群組，以便建立產生的角色指派。</span><span class="sxs-lookup"><span data-stu-id="820b6-105">Role definitions are assigned to a user or groups to create a resulting role assignment.</span></span> <span data-ttu-id="820b6-106">角色定義中的工作會指定使用者或群組可執行的工作。</span><span class="sxs-lookup"><span data-stu-id="820b6-106">The tasks in the role definition specify what the user or group can do.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="820b6-107">有兩個預先定義的系統角色定義： **系統管理員** 和 **系統使用者**。</span><span class="sxs-lookup"><span data-stu-id="820b6-107">has two predefined system role definitions: **System Administrator** and **System User**.</span></span> <span data-ttu-id="820b6-108">您可以藉由變更工作清單來修改這些角色定義，也可以建立支援不同工作組合的新系統角色。</span><span class="sxs-lookup"><span data-stu-id="820b6-108">You can modify these role definitions by changing the task list, or you can create a new system role that supports a different combination of tasks.</span></span> <span data-ttu-id="820b6-109">編輯角色定義將影響包含該角色定義的所有角色指派。</span><span class="sxs-lookup"><span data-stu-id="820b6-109">Editing a role definition affects all role assignments that include the role definition.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="820b6-110">系統角色定義只會用於以原生模式執行的報表伺服器。</span><span class="sxs-lookup"><span data-stu-id="820b6-110">System role assignments are used only on a report server that runs in native mode.</span></span> <span data-ttu-id="820b6-111">如果報表伺服器是針對 SharePoint 整合所設定，這個頁面就無法使用。</span><span class="sxs-lookup"><span data-stu-id="820b6-111">If the report server is configured for SharePoint integration, this page is not available.</span></span>  
  
## <a name="options"></a><span data-ttu-id="820b6-112">選項。</span><span class="sxs-lookup"><span data-stu-id="820b6-112">Options</span></span>  
 <span data-ttu-id="820b6-113">**名稱**</span><span class="sxs-lookup"><span data-stu-id="820b6-113">**Name**</span></span>  
 <span data-ttu-id="820b6-114">指定系統角色定義的名稱。</span><span class="sxs-lookup"><span data-stu-id="820b6-114">Specifies the name of the system role definition.</span></span>  
  
 <span data-ttu-id="820b6-115">**說明**</span><span class="sxs-lookup"><span data-stu-id="820b6-115">**Description**</span></span>  
 <span data-ttu-id="820b6-116">顯示系統角色定義的描述。</span><span class="sxs-lookup"><span data-stu-id="820b6-116">Shows a description of the system role definition.</span></span> <span data-ttu-id="820b6-117">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中，這項描述只會出現在本頁面上。</span><span class="sxs-lookup"><span data-stu-id="820b6-117">In [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)], this description is only visible in this page.</span></span> <span data-ttu-id="820b6-118">透過報表管理員檢視這個項目的使用者，會在瀏覽資料夾階層時看到此描述。</span><span class="sxs-lookup"><span data-stu-id="820b6-118">Users who view this item through Report Manager may see this description when browsing the folder hierarchy.</span></span>  
  
 <span data-ttu-id="820b6-119">**Task**</span><span class="sxs-lookup"><span data-stu-id="820b6-119">**Task**</span></span>  
 <span data-ttu-id="820b6-120">列出此角色定義可以選取的所有系統層級工作。</span><span class="sxs-lookup"><span data-stu-id="820b6-120">Lists all system-level tasks that can be selected for this role definition.</span></span> <span data-ttu-id="820b6-121">您可以將項目加入預先定義的工作清單，或者從清單移除項目，以定義使用者藉由這個角色存取指定項目的方式。</span><span class="sxs-lookup"><span data-stu-id="820b6-121">You can add or remove items from the predefined task list to define how users access a given item through this role.</span></span> <span data-ttu-id="820b6-122">您不能建立新的工作，也不能修改現有的工作。</span><span class="sxs-lookup"><span data-stu-id="820b6-122">You cannot create new tasks, and you cannot modify existing tasks.</span></span>  
  
 <span data-ttu-id="820b6-123">**說明**</span><span class="sxs-lookup"><span data-stu-id="820b6-123">**Description**</span></span>  
 <span data-ttu-id="820b6-124">提供每個工作的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="820b6-124">Provides information about each task.</span></span> <span data-ttu-id="820b6-125">您不能修改工作描述。</span><span class="sxs-lookup"><span data-stu-id="820b6-125">You cannot modify task descriptions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="820b6-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="820b6-126">See Also</span></span>  
 <span data-ttu-id="820b6-127">[Management Studio F1 說明中的報表伺服器](report-server-in-management-studio-f1-help.md) </span><span class="sxs-lookup"><span data-stu-id="820b6-127">[Report Server in Management Studio F1 Help](report-server-in-management-studio-f1-help.md) </span></span>  
 <span data-ttu-id="820b6-128">[系統層級工作](../security/tasks-and-permissions-system-level-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="820b6-128">[System-Level Tasks](../security/tasks-and-permissions-system-level-tasks.md) </span></span>  
 <span data-ttu-id="820b6-129">[工作和權限](../security/tasks-and-permissions.md) </span><span class="sxs-lookup"><span data-stu-id="820b6-129">[Tasks and Permissions](../security/tasks-and-permissions.md) </span></span>  
 [<span data-ttu-id="820b6-130">預先定義的角色</span><span class="sxs-lookup"><span data-stu-id="820b6-130">Predefined Roles</span></span>](../security/role-definitions-predefined-roles.md)  
  
  
