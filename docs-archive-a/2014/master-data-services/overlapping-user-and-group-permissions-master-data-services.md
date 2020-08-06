---
title: 重疊的使用者和群組的權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- users [Master Data Services], resolving permissions
- permissions [Master Data Services], user and group overlaps
- groups [Master Data Services], resolving permissions
ms.assetid: 31c3cf7d-17d4-4474-b6a7-ffcb9fc45b37
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 7044bf6260170cbc598719ec204ddb6f861f6301
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87698359"
---
# <a name="overlapping-user-and-group-permissions-master-data-services"></a><span data-ttu-id="b69e5-102">重疊的使用者和群組的權限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b69e5-102">Overlapping User and Group Permissions (Master Data Services)</span></span>
  <span data-ttu-id="b69e5-103">使用者的權限是根據以下條件：</span><span class="sxs-lookup"><span data-stu-id="b69e5-103">A user's permissions are based on:</span></span>  
  
-   <span data-ttu-id="b69e5-104">來自群組成員資格的權限。</span><span class="sxs-lookup"><span data-stu-id="b69e5-104">Permissions from group memberships.</span></span>  
  
-   <span data-ttu-id="b69e5-105">明確指派給使用者的權限。</span><span class="sxs-lookup"><span data-stu-id="b69e5-105">Permissions assigned explicitly to the user.</span></span>  
  
 <span data-ttu-id="b69e5-106">如果使用者是多個群組的成員，而且這些群組擁有主資料管理員的存取權，將適用以下規則：</span><span class="sxs-lookup"><span data-stu-id="b69e5-106">If a user is a member of multiple groups, and those groups have access to Master Data Manager, the following rules apply:</span></span>  
  
-   <span data-ttu-id="b69e5-107">**[拒絕]** 會覆寫所有其他的權限。</span><span class="sxs-lookup"><span data-stu-id="b69e5-107">**Deny** overrides all other permissions.</span></span>  
  
-   <span data-ttu-id="b69e5-108">**更新**會覆寫**唯讀**。</span><span class="sxs-lookup"><span data-stu-id="b69e5-108">**Update** overrides **Read-only**.</span></span>  
  
 <span data-ttu-id="b69e5-109">這些規則同時適用於[模型]\*\*\*\* 和 [階層成員]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b69e5-109">These rules apply to both the **Models** and **Hierarchy Members** tabs.</span></span> <span data-ttu-id="b69e5-110">系統會解析每個索引標籤的權限，然後加以結合。</span><span class="sxs-lookup"><span data-stu-id="b69e5-110">Permissions are resolved for each tab and then combined.</span></span> <span data-ttu-id="b69e5-111">如需詳細資訊，請參閱 [如何決定權限 &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b69e5-111">For more information, see [How Permissions Are Determined &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b69e5-112">您可以在使用者介面中，檢視使用者和群組重疊權限的解析。</span><span class="sxs-lookup"><span data-stu-id="b69e5-112">You can view the resolution of user and group overlapping permissions in the user interface.</span></span> <span data-ttu-id="b69e5-113">[模型]\*\*\*\* 和 [階層成員]\*\*\*\* 索引標籤都有下拉式清單，您可以從中選取 [有效]\*\*\*\* 來檢視有效的權限。</span><span class="sxs-lookup"><span data-stu-id="b69e5-113">Both the **Models** and **Hierarchy Members** tab have a drop-down list from which you can choose **Effective** to view effective permissions.</span></span>  
  
## <a name="example-1"></a><span data-ttu-id="b69e5-114">範例 1</span><span class="sxs-lookup"><span data-stu-id="b69e5-114">Example 1</span></span>  
 <span data-ttu-id="b69e5-115">![mds_conc_user_group_ex_1](../../2014/master-data-services/media/mds-conc-user-group-ex-1.gif "mds_conc_user_group_ex_1")</span><span class="sxs-lookup"><span data-stu-id="b69e5-115">![mds_conc_user_group_ex_1](../../2014/master-data-services/media/mds-conc-user-group-ex-1.gif "mds_conc_user_group_ex_1")</span></span>  
  
 <span data-ttu-id="b69e5-116">使用者屬於群組 1 和群組 2。</span><span class="sxs-lookup"><span data-stu-id="b69e5-116">The user belongs to Group 1 and Group 2.</span></span>  
  
 <span data-ttu-id="b69e5-117">使用者具有 Product 實體的 [**唯讀**] 許可權。</span><span class="sxs-lookup"><span data-stu-id="b69e5-117">The user has **Read-only** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="b69e5-118">群組 1 擁有 Product 實體的 **更新** 權限。</span><span class="sxs-lookup"><span data-stu-id="b69e5-118">Group 1 has **Update** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="b69e5-119">[群組 2] 具有 [Product] 實體的 [**唯讀**] 許可權。</span><span class="sxs-lookup"><span data-stu-id="b69e5-119">Group 2 has **Read-only** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="b69e5-120">結果：使用者的有效權限為 Product 實體的 **更新** 權限。</span><span class="sxs-lookup"><span data-stu-id="b69e5-120">Result: The user's effective permission is **Update** to the Product entity.</span></span>  
  
## <a name="example-2"></a><span data-ttu-id="b69e5-121">範例 2</span><span class="sxs-lookup"><span data-stu-id="b69e5-121">Example 2</span></span>  
 <span data-ttu-id="b69e5-122">![mds_conc_user_group_ex_2](../../2014/master-data-services/media/mds-conc-user-group-ex-2.gif "mds_conc_user_group_ex_2")</span><span class="sxs-lookup"><span data-stu-id="b69e5-122">![mds_conc_user_group_ex_2](../../2014/master-data-services/media/mds-conc-user-group-ex-2.gif "mds_conc_user_group_ex_2")</span></span>  
  
 <span data-ttu-id="b69e5-123">使用者屬於群組 1 和群組 2。</span><span class="sxs-lookup"><span data-stu-id="b69e5-123">The user belongs to Group 1 and Group 2.</span></span>  
  
 <span data-ttu-id="b69e5-124">使用者具有 Product 實體的 [**唯讀**] 許可權。</span><span class="sxs-lookup"><span data-stu-id="b69e5-124">The user has **Read-only** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="b69e5-125">群組 1 擁有 Product 實體的 **更新** 權限。</span><span class="sxs-lookup"><span data-stu-id="b69e5-125">Group 1 has **Update** permission to Product entity.</span></span>  
  
 <span data-ttu-id="b69e5-126">群組 2 擁有 Product 實體的 **拒絕** 權限。</span><span class="sxs-lookup"><span data-stu-id="b69e5-126">Group 2 has **Deny** permission to the Product entity.</span></span>  
  
 <span data-ttu-id="b69e5-127">結果：使用者的有效權限為 Product 實體的 **拒絕** 權限。</span><span class="sxs-lookup"><span data-stu-id="b69e5-127">Result: The user's effective permission is **Deny** to the Product entity.</span></span>  
  
## <a name="example-3"></a><span data-ttu-id="b69e5-128">範例 3</span><span class="sxs-lookup"><span data-stu-id="b69e5-128">Example 3</span></span>  
 <span data-ttu-id="b69e5-129">![mds_conc_user_group_ex_3](../../2014/master-data-services/media/mds-conc-user-group-ex-3.gif "mds_conc_user_group_ex_3")</span><span class="sxs-lookup"><span data-stu-id="b69e5-129">![mds_conc_user_group_ex_3](../../2014/master-data-services/media/mds-conc-user-group-ex-3.gif "mds_conc_user_group_ex_3")</span></span>  
  
 <span data-ttu-id="b69e5-130">使用者屬於群組 1 和群組 2。</span><span class="sxs-lookup"><span data-stu-id="b69e5-130">The user belongs to Group 1 and Group 2.</span></span>  
  
 <span data-ttu-id="b69e5-131">使用者擁有階層節點內成員群組的 **更新** 權限。</span><span class="sxs-lookup"><span data-stu-id="b69e5-131">The user has **Update** permission to a group of members in a hierarchy node.</span></span>  
  
 <span data-ttu-id="b69e5-132">[群組 1] 具有階層節點中成員群組的 [**唯讀**] 許可權。</span><span class="sxs-lookup"><span data-stu-id="b69e5-132">Group 1 has **Read-only** permission to a group of members in a hierarchy node.</span></span>  
  
 <span data-ttu-id="b69e5-133">群組2具有階層節點中成員群組的**唯讀**許可權。</span><span class="sxs-lookup"><span data-stu-id="b69e5-133">Group 2 has **Read-only** permission to a group of members in a hierarchy node.</span></span>  
  
 <span data-ttu-id="b69e5-134">結果：使用者的有效權限為成員的 **更新** 權限。</span><span class="sxs-lookup"><span data-stu-id="b69e5-134">Result: The user's effective permission is **Update** to the members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b69e5-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b69e5-135">See Also</span></span>  
 <span data-ttu-id="b69e5-136">[如何判斷許可權 &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b69e5-136">[How Permissions Are Determined &#40;Master Data Services&#41;](how-permissions-are-determined-master-data-services.md) </span></span>  
 [<span data-ttu-id="b69e5-137">重疊的模型和成員的權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b69e5-137">Overlapping Model and Member Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/overlapping-model-and-member-permissions-master-data-services.md)  
  
  
