---
title: 在階層中移動成員 (Master Data Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- hierarchies [Master Data Services], moving members
- explicit hierarchies, moving members
- derived hierarchies, moving members
- members [Master Data Services], moving
ms.assetid: 049c9a15-89c1-478c-8438-028fffc9e187
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 37167f76b965197dbf8e37e365778395ec640d38
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594591"
---
# <a name="move-members-within-a-hierarchy-master-data-services"></a><span data-ttu-id="ef71c-102">在階層中移動成員 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ef71c-102">Move Members within a Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="ef71c-103">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 中，移動階層中的成員來變更成員的位置或父系指派。</span><span class="sxs-lookup"><span data-stu-id="ef71c-103">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], move members within a hierarchy to change their location or parent assignment.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ef71c-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="ef71c-104">Prerequisites</span></span>  
 <span data-ttu-id="ef71c-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="ef71c-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="ef71c-106">您必須擁有存取 [ **Explorer** ] 功能區域的許可權。</span><span class="sxs-lookup"><span data-stu-id="ef71c-106">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="ef71c-107">針對明確階層，您至少必須擁有實體的 [**更新**] 許可權。</span><span class="sxs-lookup"><span data-stu-id="ef71c-107">For explicit hierarchies, you must have a minimum of **Update** permission to the entity.</span></span>  
  
-   <span data-ttu-id="ef71c-108">針對衍生階層，您必須至少有模型的**更新**，以及階層中所使用的任何網域屬性。</span><span class="sxs-lookup"><span data-stu-id="ef71c-108">For derived hierarchies, you must have a minimum of **Update** to the model and to any domain-based attributes used in the hierarchy.</span></span>  
  
### <a name="to-move-members-within-a-hierarchy"></a><span data-ttu-id="ef71c-109">若要移動階層中的成員</span><span class="sxs-lookup"><span data-stu-id="ef71c-109">To move members within a hierarchy</span></span>  
  
1.  <span data-ttu-id="ef71c-110">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="ef71c-110">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="ef71c-111">從 **[版本]** 清單中選取版本。</span><span class="sxs-lookup"><span data-stu-id="ef71c-111">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="ef71c-112">按一下 **[總管]**。</span><span class="sxs-lookup"><span data-stu-id="ef71c-112">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="ef71c-113">從功能表列指向 [階層] **，然後按一下**[ *hierarchy_name*]。</span><span class="sxs-lookup"><span data-stu-id="ef71c-113">From the menu bar, point to **Hierarchies** and click *hierarchy_name*.</span></span>  
  
5.  <span data-ttu-id="ef71c-114">在階層顯示于樹狀結構**中的階層窗格中**，按一下您想要移動之每個成員的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ef71c-114">In the **Hierarchy** pane, where the hierarchy is displayed in a tree structure, click the check box for each member you want to move.</span></span>  
  
6.  <span data-ttu-id="ef71c-115">在 [**階層] 窗格的頂端**，按一下 [**剪**下]。</span><span class="sxs-lookup"><span data-stu-id="ef71c-115">At the top of the **Hierarchy** pane, click **Cut**.</span></span>  
  
7.  <span data-ttu-id="ef71c-116">**在 [階層] 窗格**中，按一下您想要將成員移至其中之成員的核取方塊。</span><span class="sxs-lookup"><span data-stu-id="ef71c-116">In the **Hierarchy** pane, click the check box for the member you want to move the members to.</span></span>  
  
8.  <span data-ttu-id="ef71c-117">按一下 [**貼**上]。</span><span class="sxs-lookup"><span data-stu-id="ef71c-117">Click **Paste**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="ef71c-118">在衍生階層中，您只能將成員移到相同的層級。</span><span class="sxs-lookup"><span data-stu-id="ef71c-118">In derived hierarchies, you can move members to the same level only.</span></span> <span data-ttu-id="ef71c-119">此外，您無法變更成員的排序次序。</span><span class="sxs-lookup"><span data-stu-id="ef71c-119">Also, you cannot change the sort order of members.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef71c-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ef71c-120">See Also</span></span>  
 <span data-ttu-id="ef71c-121">[使用暫存進程 &#40;Master Data Services 來移動明確階層成員&#41;](add-update-and-delete-data-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="ef71c-121">[Move Explicit Hierarchy Members by Using the Staging Process &#40;Master Data Services&#41;](add-update-and-delete-data-master-data-services.md) </span></span>  
 <span data-ttu-id="ef71c-122">[衍生階層 &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="ef71c-122">[Derived Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-master-data-services.md) </span></span>  
 [<span data-ttu-id="ef71c-123">明確階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ef71c-123">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
