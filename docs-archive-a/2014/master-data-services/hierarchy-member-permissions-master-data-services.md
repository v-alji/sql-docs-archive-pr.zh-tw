---
title: 階層成員權限 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- members [Master Data Services], permissions
- permissions [Master Data Services], members
ms.assetid: b3880eed-1bf6-4f65-ab23-b08c194cc858
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 81716dbd0ad08b6e92a2edb8f1d142b46bf3d24d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597182"
---
# <a name="hierarchy-member-permissions-master-data-services"></a><span data-ttu-id="3c386-102">階層成員權限 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="3c386-102">Hierarchy Member Permissions (Master Data Services)</span></span>
  <span data-ttu-id="3c386-103">階層成員權限為選擇性，而且只有當您希望使用者擁有特定成員的受限存取權時，才應該使用。</span><span class="sxs-lookup"><span data-stu-id="3c386-103">Hierarchy member permissions are optional and should be used only when you want a user to have limited access to specific members.</span></span> <span data-ttu-id="3c386-104">如果您未在 [階層成員]\*\*\*\* 索引標籤上指派權限，則使用者的權限完全是根據 [模型]\*\*\*\* 索引標籤上指派的權限。</span><span class="sxs-lookup"><span data-stu-id="3c386-104">If you do not assign permissions on the **Hierarchy Members** tab, then the user's permissions are based solely on the permissions assigned on the **Models** tab.</span></span>  
  
 <span data-ttu-id="3c386-105">階層成員許可權是在 [階層 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] **成員**] 索引標籤的 [**使用者和群組的許可權**] 功能區域中， (UI) 的使用者介面中指派。這些許可權會決定使用者可以在 UI 的 [ **Explorer** ] 功能區域中存取哪些成員。</span><span class="sxs-lookup"><span data-stu-id="3c386-105">Hierarchy member permissions are assigned in the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] user interface (UI), in the **User and Group Permissions** functional area on the **Hierarchy Members** tab. These permissions determine which members a user can access in the **Explorer** functional area of the UI.</span></span>  
  
 <span data-ttu-id="3c386-106">在 [階層成員]\*\*\*\* 索引標籤上，每一個階層會表示為一個樹狀結構。</span><span class="sxs-lookup"><span data-stu-id="3c386-106">On the **Hierarchy Members** tab, each hierarchy is represented as a tree structure.</span></span> <span data-ttu-id="3c386-107">當您將權限指派給樹狀結構中的節點時，所有子項都會繼承該權限，除非在較低層級明確指派權限。</span><span class="sxs-lookup"><span data-stu-id="3c386-107">When you assign permission to a node in the tree, all children inherit that permission unless permission is explicitly assigned at a lower level.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c386-108">當您指派權限給階層中的節點時，相同層級或更高層級的其他節點中的所有成員都會以隱含方式遭到拒絕。</span><span class="sxs-lookup"><span data-stu-id="3c386-108">When you assign permission to a node in a hierarchy, all members in other nodes at the same level or higher are implicitly denied.</span></span>  
  
 <span data-ttu-id="3c386-109">在總管\*\*\*\* 中，成員權限會套用到顯示成員的每一個地方。</span><span class="sxs-lookup"><span data-stu-id="3c386-109">In **Explorer**, the member permissions are applied everywhere the member is displayed.</span></span> <span data-ttu-id="3c386-110">例如，具有**唯讀**許可權的成員在其所屬的任何實體、階層和集合中都是唯讀的。</span><span class="sxs-lookup"><span data-stu-id="3c386-110">For example, a member with **Read-only** permission is read-only in any entities, hierarchies, and collections to which it belongs.</span></span>  
  
 <span data-ttu-id="3c386-111">階層成員權限會套用到您指派的模型版本以及該版本的任何將來複本。</span><span class="sxs-lookup"><span data-stu-id="3c386-111">Hierarchy member permissions apply to the model version you assign them to, and to any future copies of the version.</span></span> <span data-ttu-id="3c386-112">它們不會套用到早於您所指派的版本。</span><span class="sxs-lookup"><span data-stu-id="3c386-112">They do not apply to versions earlier than the one you assign them to.</span></span>  
  
|<span data-ttu-id="3c386-113">權限</span><span class="sxs-lookup"><span data-stu-id="3c386-113">Permission</span></span>|<span data-ttu-id="3c386-114">描述</span><span class="sxs-lookup"><span data-stu-id="3c386-114">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="3c386-115">**唯讀**</span><span class="sxs-lookup"><span data-stu-id="3c386-115">**Read-only**</span></span>|<span data-ttu-id="3c386-116">顯示成員，但是使用者無法變更成員。</span><span class="sxs-lookup"><span data-stu-id="3c386-116">The members are displayed but the user cannot change them.</span></span> <span data-ttu-id="3c386-117">使用者也無法在任何明確階層或成員所屬的集合中移動成員。</span><span class="sxs-lookup"><span data-stu-id="3c386-117">The user also cannot move the members in any explicit hierarchies or collections that the members belong to.</span></span><br /><br /> <span data-ttu-id="3c386-118">注意：如果您將 [**唯讀**] 許可權指派給 [**根**]，[**根**] 底下的成員是唯讀的;不過，在明確階層和集合中，使用者可以將成員移至**根目錄**，並且可以將新成員加入至**根**。</span><span class="sxs-lookup"><span data-stu-id="3c386-118">Note: If you assign **Read-only** permission to **Root**, the members under **Root** are read-only; however, in explicit hierarchies and collections, the user can move members to **Root** and can add new members to **Root**.</span></span>|  
|<span data-ttu-id="3c386-119">**更新**</span><span class="sxs-lookup"><span data-stu-id="3c386-119">**Update**</span></span>|<span data-ttu-id="3c386-120">顯示成員，而且使用者可加以變更。</span><span class="sxs-lookup"><span data-stu-id="3c386-120">The members are displayed and the user can change them.</span></span> <span data-ttu-id="3c386-121">使用者也可以在任何明確階層或成員所屬的集合中移動成員。</span><span class="sxs-lookup"><span data-stu-id="3c386-121">The user can also move the members in any explicit hierarchies or collections the members belong to.</span></span>|  
|<span data-ttu-id="3c386-122">**Deny**</span><span class="sxs-lookup"><span data-stu-id="3c386-122">**Deny**</span></span>|<span data-ttu-id="3c386-123">不顯示成員。</span><span class="sxs-lookup"><span data-stu-id="3c386-123">The members are not displayed.</span></span>|  
  
 <span data-ttu-id="3c386-124">在 [階層成員]\*\*\*\* 索引標籤上，您指派的權限不會立即生效。</span><span class="sxs-lookup"><span data-stu-id="3c386-124">On the **Hierarchy Members** tab, the permissions you assign do not take effect immediately.</span></span> <span data-ttu-id="3c386-125">權限套用的頻率取決於 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫中 [系統設定] 資料表內的 [成員安全性處理間隔設定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3c386-125">The frequency that the permissions are applied depends on the **Member security processing interval setting** in the System Settings table in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="3c386-126">遵循 [立即套用成員權限 &#40;Master Data Services&#41;](immediately-apply-member-permissions-master-data-services.md)中的步驟，可以立即套用成員權限。</span><span class="sxs-lookup"><span data-stu-id="3c386-126">You can apply member permissions immediately by following the steps in [Immediately Apply Member Permissions &#40;Master Data Services&#41;](immediately-apply-member-permissions-master-data-services.md).</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="3c386-127">您無法將階層成員權限指派給遞迴階層、具有明確頂層的衍生階層，以及具有隱藏層級的衍生階層。</span><span class="sxs-lookup"><span data-stu-id="3c386-127">You cannot assign hierarchy member permissions to recursive hierarchies, derived hierarchies with explicit caps, and derived hierarchies with hidden levels.</span></span>  
  
## <a name="possible-overlapping-permissions"></a><span data-ttu-id="3c386-128">可能重疊的權限</span><span class="sxs-lookup"><span data-stu-id="3c386-128">Possible Overlapping Permissions</span></span>  
 <span data-ttu-id="3c386-129">當指派權限給成員時，您可能必須解析重疊的權限。</span><span class="sxs-lookup"><span data-stu-id="3c386-129">When assigning permission to members, you may have to resolve overlapping permissions.</span></span>  
  
### <a name="when-a-member-belongs-to-multiple-hierarchies"></a><span data-ttu-id="3c386-130">當成員屬於多個階層</span><span class="sxs-lookup"><span data-stu-id="3c386-130">When a member belongs to multiple hierarchies</span></span>  
 <span data-ttu-id="3c386-131">兩個或多個階層可以包含相同的成員。</span><span class="sxs-lookup"><span data-stu-id="3c386-131">Two or more hierarchies can contain the same member.</span></span>  
  
-   <span data-ttu-id="3c386-132">如果一個階層節點被指派 [**更新**] 許可權，而另一個是指派為 [**唯讀**]，則節點中的成員是**唯讀**的。</span><span class="sxs-lookup"><span data-stu-id="3c386-132">If one hierarchy node is assigned **Update** permission and another is assigned **Read-only**, then the members in the node are **Read-only**.</span></span>  
  
-   <span data-ttu-id="3c386-133">如果一個階層節點被指派 [**更新**] 或 [**唯讀**] 許可權，而另一個節點被指派 [**拒絕**]，則不會顯示節點中的成員。</span><span class="sxs-lookup"><span data-stu-id="3c386-133">If one hierarchy node is assigned **Update** or **Read-only** permission and another node is assigned **Deny**, then the members in the node are not displayed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c386-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3c386-134">See Also</span></span>  
 <span data-ttu-id="3c386-135">[指派階層成員許可權 &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3c386-135">[Assign Hierarchy Member Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/assign-hierarchy-member-permissions-master-data-services.md) </span></span>  
 <span data-ttu-id="3c386-136">[如何判斷許可權 &#40;Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3c386-136">[How Permissions Are Determined &#40;Master Data Services&#41;](../../2014/master-data-services/how-permissions-are-determined-master-data-services.md) </span></span>  
 <span data-ttu-id="3c386-137">[成員 &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3c386-137">[Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) </span></span>  
 <span data-ttu-id="3c386-138">[階層 &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="3c386-138">[Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/hierarchies-master-data-services.md) </span></span>  
 [<span data-ttu-id="3c386-139">立即套用成員權限 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="3c386-139">Immediately Apply Member Permissions &#40;Master Data Services&#41;</span></span>](immediately-apply-member-permissions-master-data-services.md)  
  
  
