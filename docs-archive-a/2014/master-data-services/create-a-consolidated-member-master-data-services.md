---
title: 建立合併成員 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating consolidated members [Master Data Services]
- members [Master Data Services], creating consolidated members
- consolidated members [Master Data Services], creating
ms.assetid: 431ab2d2-5517-4372-9980-142b05427c08
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c41673f6f3bf1f4de2a831ecd659321b273b6af9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703041"
---
# <a name="create-a-consolidated-member-master-data-services"></a><span data-ttu-id="ae725-102">Create a Consolidated Member (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ae725-102">Create a Consolidated Member (Master Data Services)</span></span>
  <span data-ttu-id="ae725-103">[!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]當您需要明確階層的父節點時，可以在 中建立合併成員。</span><span class="sxs-lookup"><span data-stu-id="ae725-103">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], create a consolidated member when you want a parent node for an explicit hierarchy.</span></span> <span data-ttu-id="ae725-104">合併成員可以有自己的屬性。</span><span class="sxs-lookup"><span data-stu-id="ae725-104">Consolidated members can have their own attributes.</span></span> <span data-ttu-id="ae725-105">它們可用於群組。</span><span class="sxs-lookup"><span data-stu-id="ae725-105">They are used for grouping.</span></span> <span data-ttu-id="ae725-106">如下列範例所示，合併成員可以用於具有帳戶的帳戶群組。</span><span class="sxs-lookup"><span data-stu-id="ae725-106">As shown in the following example, consolidated members can be used for account groups that have accounts under them.</span></span>

 <span data-ttu-id="ae725-107">![MDS 合併成員](../../2014/master-data-services/media/mds-consolidated-members.png "MDS 合併成員")</span><span class="sxs-lookup"><span data-stu-id="ae725-107">![MDS Consolidated Members](../../2014/master-data-services/media/mds-consolidated-members.png "MDS Consolidated Members")</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ae725-108">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="ae725-108">Prerequisites</span></span>
 <span data-ttu-id="ae725-109">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="ae725-109">To perform this procedure:</span></span>

-   <span data-ttu-id="ae725-110">您必須擁有存取 [ **Explorer** ] 功能區域的許可權。</span><span class="sxs-lookup"><span data-stu-id="ae725-110">You must have permission to access the **Explorer** functional area.</span></span>

-   <span data-ttu-id="ae725-111">針對要加入成員之實體的合併模型物件，您必須至少擁有 **[更新]** 權限。</span><span class="sxs-lookup"><span data-stu-id="ae725-111">You must have a minimum of **Update** permission to the consolidated model object for the entity you are adding a member to.</span></span>

### <a name="to-create-a-consolidated-member"></a><span data-ttu-id="ae725-112">若要建立合併成員</span><span class="sxs-lookup"><span data-stu-id="ae725-112">To create a consolidated member</span></span>

1.  <span data-ttu-id="ae725-113">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="ae725-113">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>

2.  <span data-ttu-id="ae725-114">從 **[版本]** 清單中選取版本。</span><span class="sxs-lookup"><span data-stu-id="ae725-114">From the **Version** list, select a version.</span></span>

3.  <span data-ttu-id="ae725-115">按一下 **[總管]**。</span><span class="sxs-lookup"><span data-stu-id="ae725-115">Click **Explorer**.</span></span>

4.  <span data-ttu-id="ae725-116">從功能表列指向 **[階層]** ，然後按一下要加入合併成員的階層名稱。</span><span class="sxs-lookup"><span data-stu-id="ae725-116">From the menu bar, point to **Hierarchies** and click the name of the hierarchy you want to add a consolidated member to.</span></span>

5.  <span data-ttu-id="ae725-117">在方格上方，選取 **[合併成員]** 或 **[階層中的所有合併成員]** 選項。</span><span class="sxs-lookup"><span data-stu-id="ae725-117">Above the grid, select either the **Consolidated members** or the **All consolidated members in hierarchy** option.</span></span>

6.  <span data-ttu-id="ae725-118">按一下 [新增] 。</span><span class="sxs-lookup"><span data-stu-id="ae725-118">Click **Add**.</span></span>

7.  <span data-ttu-id="ae725-119">填完右邊窗格中的欄位。</span><span class="sxs-lookup"><span data-stu-id="ae725-119">In the pane on the right, complete the fields.</span></span>

8.  <span data-ttu-id="ae725-120">選擇性。</span><span class="sxs-lookup"><span data-stu-id="ae725-120">Optional.</span></span> <span data-ttu-id="ae725-121">在 **[註解]** 方塊中，輸入有關加入此成員之原因的註解。</span><span class="sxs-lookup"><span data-stu-id="ae725-121">In the **Annotations** box, type a comment about why the member was added.</span></span> <span data-ttu-id="ae725-122">可存取成員的所有使用者都可以檢視註解。</span><span class="sxs-lookup"><span data-stu-id="ae725-122">All users who have access to the member can view the annotation.</span></span>

9. <span data-ttu-id="ae725-123">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="ae725-123">Click **OK**.</span></span>

## <a name="next-steps"></a><span data-ttu-id="ae725-124">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ae725-124">Next Steps</span></span>

-   [<span data-ttu-id="ae725-125">在階層中移動成員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ae725-125">Move Members within a Hierarchy &#40;Master Data Services&#41;</span></span>](move-members-within-a-hierarchy-master-data-services.md)

## <a name="see-also"></a><span data-ttu-id="ae725-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ae725-126">See Also</span></span>
 <span data-ttu-id="ae725-127">[建立明確階層 &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) [建立分葉成員 &#40;Master Data Services](../../2014/master-data-services/create-a-leaf-member-master-data-services.md)&#41;[使用暫存進程成員 Master Data Services &#40;載入或更新 Master Data Services 中](add-update-and-delete-data-master-data-services.md) [Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md)&#41;&#40;[明確](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)階層 Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ae725-127">[Create an Explicit Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) [Create a Leaf Member &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-leaf-member-master-data-services.md) [Load or Update Members in Master Data Services by Using the Staging Process](add-update-and-delete-data-master-data-services.md) [Members &#40;Master Data Services&#41;](../../2014/master-data-services/members-master-data-services.md) [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)</span></span>


