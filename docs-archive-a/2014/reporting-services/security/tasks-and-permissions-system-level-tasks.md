---
title: 系統層級工作 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- system-level tasks [Reporting Services]
ms.assetid: 7023b388-40b2-4590-b227-115cf380a1e7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 98f9390664064cd293b80d094d65c903869bc709
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87707014"
---
# <a name="system-level-tasks"></a><span data-ttu-id="439ba-102">系統層級工作</span><span class="sxs-lookup"><span data-stu-id="439ba-102">System-Level Tasks</span></span>
  <span data-ttu-id="439ba-103">系統層級工作是權限的集合，而這些權限與套用至報表伺服器站台整體的作業相關。</span><span class="sxs-lookup"><span data-stu-id="439ba-103">A system-level task is a collection of permissions that relate to operations that apply to the report server site as a whole.</span></span> [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="439ba-104">亦包含套用至特定項目的項目層級工作。</span><span class="sxs-lookup"><span data-stu-id="439ba-104">also includes item-level tasks that apply to specific items.</span></span> <span data-ttu-id="439ba-105">如需詳細資訊，請參閱 [項目層級工作](tasks-and-permissions-item-level-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="439ba-105">For more information, see [Item-Level Tasks](tasks-and-permissions-item-level-tasks.md).</span></span> <span data-ttu-id="439ba-106">如需一般工作和權限的詳細資訊，請參閱 [工作和權限](tasks-and-permissions.md)。</span><span class="sxs-lookup"><span data-stu-id="439ba-106">For more information about tasks and permissions in general, see [Tasks and Permissions](tasks-and-permissions.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="439ba-107">如果是藉由程式設計來使用這些工作，必須使用支援系統層級工作的方法。</span><span class="sxs-lookup"><span data-stu-id="439ba-107">If you are working with these tasks programmatically, you must use methods that support system-level tasks.</span></span> <span data-ttu-id="439ba-108">如需詳細資訊，請參閱 <xref:ReportService2010.ReportingService2010.ListTasks%2A> 和 <xref:ReportService2010.ReportingService2010.ListRoles%2A>。</span><span class="sxs-lookup"><span data-stu-id="439ba-108">For more information, see <xref:ReportService2010.ReportingService2010.ListTasks%2A> and <xref:ReportService2010.ReportingService2010.ListRoles%2A>.</span></span>  
  
## <a name="permissions-in-system-level-tasks"></a><span data-ttu-id="439ba-109">系統層級工作中的權限</span><span class="sxs-lookup"><span data-stu-id="439ba-109">Permissions in System-Level Tasks</span></span>  
 <span data-ttu-id="439ba-110">下表識別每一個系統工作的權限集合。</span><span class="sxs-lookup"><span data-stu-id="439ba-110">The following table identifies the collection of permissions for each system task.</span></span> <span data-ttu-id="439ba-111">列出的權限僅供參考之用，提供每一個工作可用之功能的更正確說明。</span><span class="sxs-lookup"><span data-stu-id="439ba-111">Permissions are listed for informational purposes only, to provide a more exact description of the functionality available through each task.</span></span>  
  
|<span data-ttu-id="439ba-112">Task</span><span class="sxs-lookup"><span data-stu-id="439ba-112">Task</span></span>|<span data-ttu-id="439ba-113">權限</span><span class="sxs-lookup"><span data-stu-id="439ba-113">Permissions</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="439ba-114">執行報表定義</span><span class="sxs-lookup"><span data-stu-id="439ba-114">Execute report definitions</span></span>|<span data-ttu-id="439ba-115">執行報表定義 (權限與工作名稱相同)</span><span class="sxs-lookup"><span data-stu-id="439ba-115">Execute Report Definitions (the permission and task name are the same)</span></span>|  
|<span data-ttu-id="439ba-116">產生事件</span><span class="sxs-lookup"><span data-stu-id="439ba-116">Generate events</span></span>|<span data-ttu-id="439ba-117">產生事件</span><span class="sxs-lookup"><span data-stu-id="439ba-117">Generate Events</span></span>|  
|<span data-ttu-id="439ba-118">管理工作</span><span class="sxs-lookup"><span data-stu-id="439ba-118">Manage jobs</span></span>|<span data-ttu-id="439ba-119">讀取系統屬性</span><span class="sxs-lookup"><span data-stu-id="439ba-119">Read System Properties</span></span><br /><br /> <span data-ttu-id="439ba-120">更新系統屬性</span><span class="sxs-lookup"><span data-stu-id="439ba-120">Update System Properties</span></span>|  
|<span data-ttu-id="439ba-121">管理報表伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="439ba-121">Manage report server properties</span></span>|<span data-ttu-id="439ba-122">讀取系統屬性</span><span class="sxs-lookup"><span data-stu-id="439ba-122">Read System Properties</span></span><br /><br /> <span data-ttu-id="439ba-123">更新系統屬性</span><span class="sxs-lookup"><span data-stu-id="439ba-123">Update System Properties</span></span>|  
|<span data-ttu-id="439ba-124">管理角色</span><span class="sxs-lookup"><span data-stu-id="439ba-124">Manage roles</span></span>|<span data-ttu-id="439ba-125">建立角色</span><span class="sxs-lookup"><span data-stu-id="439ba-125">Create Roles</span></span><br /><br /> <span data-ttu-id="439ba-126">刪除角色</span><span class="sxs-lookup"><span data-stu-id="439ba-126">Delete Roles</span></span><br /><br /> <span data-ttu-id="439ba-127">讀取角色屬性</span><span class="sxs-lookup"><span data-stu-id="439ba-127">Read Role Properties</span></span><br /><br /> <span data-ttu-id="439ba-128">更新角色屬性</span><span class="sxs-lookup"><span data-stu-id="439ba-128">Update Role Properties</span></span>|  
|<span data-ttu-id="439ba-129">管理共用排程</span><span class="sxs-lookup"><span data-stu-id="439ba-129">Manage shared schedules</span></span>|<span data-ttu-id="439ba-130">建立排程</span><span class="sxs-lookup"><span data-stu-id="439ba-130">Create Schedules</span></span>|  
|<span data-ttu-id="439ba-131">管理報表伺服器安全性</span><span class="sxs-lookup"><span data-stu-id="439ba-131">Manage report server security</span></span>|<span data-ttu-id="439ba-132">讀取系統安全性原則</span><span class="sxs-lookup"><span data-stu-id="439ba-132">Read System Security Policies</span></span><br /><br /> <span data-ttu-id="439ba-133">更新系統安全性原則</span><span class="sxs-lookup"><span data-stu-id="439ba-133">Update System Security Policies</span></span>|  
|<span data-ttu-id="439ba-134">檢視報表伺服器屬性</span><span class="sxs-lookup"><span data-stu-id="439ba-134">View report server properties</span></span>|<span data-ttu-id="439ba-135">讀取系統屬性</span><span class="sxs-lookup"><span data-stu-id="439ba-135">Read System Properties</span></span>|  
|<span data-ttu-id="439ba-136">檢視共用排程</span><span class="sxs-lookup"><span data-stu-id="439ba-136">View shared schedules</span></span>|<span data-ttu-id="439ba-137">讀取排程</span><span class="sxs-lookup"><span data-stu-id="439ba-137">Read Schedules</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="439ba-138">另請參閱</span><span class="sxs-lookup"><span data-stu-id="439ba-138">See Also</span></span>  
 [<span data-ttu-id="439ba-139">在原生模式報表伺服器上授與權限</span><span class="sxs-lookup"><span data-stu-id="439ba-139">Granting Permissions on a Native Mode Report Server</span></span>](granting-permissions-on-a-native-mode-report-server.md)  
  
  
