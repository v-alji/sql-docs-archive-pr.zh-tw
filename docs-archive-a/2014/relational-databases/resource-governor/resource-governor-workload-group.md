---
title: 資源管理員工作負載群組 | Microsoft 文件
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: performance
ms.topic: conceptual
helpviewer_keywords:
- Resource Governor, workload group
- workload groups [SQL Server]
- workload groups [SQL Server], overview
ms.assetid: a84c3c3f-55b6-4a30-9c42-13f082d9281e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 6c6fa8f6fe960571f10d6a8505329fbe8f400e6c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87699376"
---
# <a name="resource-governor-workload-group"></a><span data-ttu-id="ea745-102">資源管理員工作負載群組</span><span class="sxs-lookup"><span data-stu-id="ea745-102">Resource Governor Workload Group</span></span>
  <span data-ttu-id="ea745-103">在 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 資源管理員中，工作負載群組會當做有類似分類準則之工作階段要求的容器。</span><span class="sxs-lookup"><span data-stu-id="ea745-103">In the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Resource Governor, a workload group serves as a container for session requests that have similar classification criteria.</span></span> <span data-ttu-id="ea745-104">工作負載允許對工作階段進行彙總監視，並定義工作階段的原則。</span><span class="sxs-lookup"><span data-stu-id="ea745-104">A workload allows for aggregate monitoring of the sessions, and defines policies for the sessions.</span></span> <span data-ttu-id="ea745-105">每個工作負載群組都位於資源集區中，資源集區代表 [!INCLUDE[ssDE](../../includes/ssde-md.md)]執行個體的實體資源子集。</span><span class="sxs-lookup"><span data-stu-id="ea745-105">Each workload group is in a resource pool, which represents a subset of the physical resources of an instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)].</span></span> <span data-ttu-id="ea745-106">在工作階段啟動時，資源管理員分類會將此工作階段指派給特定的工作負載群組，並且此工作階段必須使用指派給該工作負載群組的原則以及為資源集區所定義的資源來執行。</span><span class="sxs-lookup"><span data-stu-id="ea745-106">When a session is started, the Resource Governor classifier assigns the session to a specific workload group, and the session must run using the policies assigned to the workload group and the resources defined for the resource pool.</span></span>  
  
## <a name="workload-group-concepts"></a><span data-ttu-id="ea745-107">工作負載群組概念</span><span class="sxs-lookup"><span data-stu-id="ea745-107">Workload Group Concepts</span></span>  
 <span data-ttu-id="ea745-108">根據套用至每個要求的分類準則，工作負載群組會當做類似工作階段要求的容器。</span><span class="sxs-lookup"><span data-stu-id="ea745-108">A workload group serves as a container for session requests that are similar according to the classification criteria that are applied to each request.</span></span> <span data-ttu-id="ea745-109">工作負載群組允許進行資源耗用量的彙總監視，以及將統一原則套用至群組中的所有要求。</span><span class="sxs-lookup"><span data-stu-id="ea745-109">A workload group allows the aggregate monitoring of resource consumption and the application of a uniform policy to all the requests in the group.</span></span> <span data-ttu-id="ea745-110">群組會針對其成員定義原則。</span><span class="sxs-lookup"><span data-stu-id="ea745-110">A group defines the policies for its members.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="ea745-111">您可以將使用者定義的工作負載群組從某個資源集區移至另一個資源集區。</span><span class="sxs-lookup"><span data-stu-id="ea745-111">User-defined workload groups can be moved from one resource pool to another.</span></span>  
  
 <span data-ttu-id="ea745-112">資源管理員預先定義了兩個工作負載群組：內部群組和預設群組。</span><span class="sxs-lookup"><span data-stu-id="ea745-112">Resource Governor predefines two workload groups: the internal group and the default group.</span></span> <span data-ttu-id="ea745-113">雖然使用者無法變更分類成內部群組的任何項目，但是能夠進行監視。</span><span class="sxs-lookup"><span data-stu-id="ea745-113">A user cannot change anything classified as an internal group, but can monitor it.</span></span> <span data-ttu-id="ea745-114">當下列條件存在時，要求就會分類至預設群組中：</span><span class="sxs-lookup"><span data-stu-id="ea745-114">Requests are classified into the default group when the following conditions exist:</span></span>  
  
-   <span data-ttu-id="ea745-115">沒有分類要求的準則存在。</span><span class="sxs-lookup"><span data-stu-id="ea745-115">There are no criteria to classify a request.</span></span>  
  
-   <span data-ttu-id="ea745-116">嘗試將要求分類至不存在的群組中。</span><span class="sxs-lookup"><span data-stu-id="ea745-116">There is an attempt to classify the request into a non-existent group.</span></span>  
  
-   <span data-ttu-id="ea745-117">發生一般分類失敗。</span><span class="sxs-lookup"><span data-stu-id="ea745-117">There is a general classification failure.</span></span>  
  
 <span data-ttu-id="ea745-118">資源管理員也會提供建立、變更和卸除工作負載群組的 DDL 陳述式。</span><span class="sxs-lookup"><span data-stu-id="ea745-118">Resource Governor also provides DDL statements for creating, changing, and dropping workload groups.</span></span>  
  
## <a name="workload-group-tasks"></a><span data-ttu-id="ea745-119">工作負載群組工作</span><span class="sxs-lookup"><span data-stu-id="ea745-119">Workload Group Tasks</span></span>  
  
|<span data-ttu-id="ea745-120">工作描述</span><span class="sxs-lookup"><span data-stu-id="ea745-120">Task Description</span></span>|<span data-ttu-id="ea745-121">主題</span><span class="sxs-lookup"><span data-stu-id="ea745-121">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="ea745-122">描述如何建立工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="ea745-122">Describes how to create a workload group.</span></span>|[<span data-ttu-id="ea745-123">建立工作負載群組</span><span class="sxs-lookup"><span data-stu-id="ea745-123">Create a Workload Group</span></span>](create-a-workload-group.md)|  
|<span data-ttu-id="ea745-124">描述如何變更工作負載群組設定。</span><span class="sxs-lookup"><span data-stu-id="ea745-124">Describes how to change workload group settings.</span></span>|[<span data-ttu-id="ea745-125">變更工作負載群組設定</span><span class="sxs-lookup"><span data-stu-id="ea745-125">Change Workload Group Settings</span></span>](change-workload-group-settings.md)|  
|<span data-ttu-id="ea745-126">描述如何刪除工作負載群組。</span><span class="sxs-lookup"><span data-stu-id="ea745-126">Describes how to delete a workload group.</span></span>|[<span data-ttu-id="ea745-127">刪除工作負載群組</span><span class="sxs-lookup"><span data-stu-id="ea745-127">Delete a Workload Group</span></span>](delete-a-workload-group.md)|  
  
## <a name="see-also"></a><span data-ttu-id="ea745-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ea745-128">See Also</span></span>  
 <span data-ttu-id="ea745-129">[資源管理員](resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="ea745-129">[Resource Governor](resource-governor.md) </span></span>  
 <span data-ttu-id="ea745-130">[啟用資源管理員](enable-resource-governor.md) </span><span class="sxs-lookup"><span data-stu-id="ea745-130">[Enable Resource Governor](enable-resource-governor.md) </span></span>  
 <span data-ttu-id="ea745-131">[資源管理員資源集區](resource-governor-resource-pool.md) </span><span class="sxs-lookup"><span data-stu-id="ea745-131">[Resource Governor Resource Pool](resource-governor-resource-pool.md) </span></span>  
 <span data-ttu-id="ea745-132">[資源管理員分類函數](resource-governor-classifier-function.md) </span><span class="sxs-lookup"><span data-stu-id="ea745-132">[Resource Governor Classifier Function](resource-governor-classifier-function.md) </span></span>  
 <span data-ttu-id="ea745-133">[使用範本來設定資源管理員](configure-resource-governor-using-a-template.md) </span><span class="sxs-lookup"><span data-stu-id="ea745-133">[Configure Resource Governor Using a Template](configure-resource-governor-using-a-template.md) </span></span>  
 [<span data-ttu-id="ea745-134">檢視資源管理員屬性</span><span class="sxs-lookup"><span data-stu-id="ea745-134">View Resource Governor Properties</span></span>](view-resource-governor-properties.md)  
  
  
