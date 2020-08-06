---
title: 建立集合 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating collections [Master Data Services]
- collections [Master Data Services], creating
ms.assetid: 3d4f152c-863c-4385-bca9-a9fcd0402e1f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f76171b4fd9b07f751d4f919011a443253fbe31b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87703050"
---
# <a name="create-a-collection-master-data-services"></a><span data-ttu-id="d2f63-102">建立集合 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="d2f63-102">Create a Collection (Master Data Services)</span></span>
  <span data-ttu-id="d2f63-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，當您想要建立分頁成員和合併成員的一般清單時，請建立集合。</span><span class="sxs-lookup"><span data-stu-id="d2f63-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a collection when you want to create flat lists of leaf and consolidated members.</span></span> <span data-ttu-id="d2f63-104">集合不必包含實體的所有成員。</span><span class="sxs-lookup"><span data-stu-id="d2f63-104">Collections do not need to include all members from the entity.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="d2f63-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="d2f63-105">Prerequisites</span></span>  
 <span data-ttu-id="d2f63-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="d2f63-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="d2f63-107">您必須擁有存取 [ **Explorer** ] 功能區域的許可權。</span><span class="sxs-lookup"><span data-stu-id="d2f63-107">You must have permission to access the **Explorer** functional area.</span></span>  
  
-   <span data-ttu-id="d2f63-108">針對實體的集合模型物件，您必須至少擁有 **[更新]** 權限。</span><span class="sxs-lookup"><span data-stu-id="d2f63-108">You must have a minimum of **Update** permission to the collection model object for the entity.</span></span>  
  
-   <span data-ttu-id="d2f63-109">您必須啟用明確階層和集合的實體。</span><span class="sxs-lookup"><span data-stu-id="d2f63-109">The entity must be enabled for explicit hierarchies and collections.</span></span> <span data-ttu-id="d2f63-110">如需詳細資訊，請參閱[啟用明確階層和集合的實體 &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d2f63-110">For more information, see [Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;](enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).</span></span>  
  
### <a name="to-create-a-collection"></a><span data-ttu-id="d2f63-111">若要建立集合</span><span class="sxs-lookup"><span data-stu-id="d2f63-111">To create a collection</span></span>  
  
1.  <span data-ttu-id="d2f63-112">在 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 首頁上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="d2f63-112">On the [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] home page, from the **Model** list, select a model.</span></span>  
  
2.  <span data-ttu-id="d2f63-113">從 **[版本]** 清單中選取版本。</span><span class="sxs-lookup"><span data-stu-id="d2f63-113">From the **Version** list, select a version.</span></span>  
  
3.  <span data-ttu-id="d2f63-114">按一下 **[總管]**。</span><span class="sxs-lookup"><span data-stu-id="d2f63-114">Click **Explorer**.</span></span>  
  
4.  <span data-ttu-id="d2f63-115">從功能表列指向 [集合]\*\*\*\*，然後按一下 *entity_name*。</span><span class="sxs-lookup"><span data-stu-id="d2f63-115">From the menu bar, point to **Collections** and click *entity_name*.</span></span>  
  
5.  <span data-ttu-id="d2f63-116">按一下 **[加入集合]**。</span><span class="sxs-lookup"><span data-stu-id="d2f63-116">Click **Add collection**.</span></span>  
  
6.  <span data-ttu-id="d2f63-117">在 **[詳細資料]** 索引標籤的 **[名稱]** 方塊中，輸入集合的名稱。</span><span class="sxs-lookup"><span data-stu-id="d2f63-117">On the **Details** tab, in the **Name** box, type a name for the collection.</span></span>  
  
7.  <span data-ttu-id="d2f63-118">在 **[代碼]** 方塊中，輸入集合的唯一代碼。</span><span class="sxs-lookup"><span data-stu-id="d2f63-118">In the **Code** box, type a unique code for the collection.</span></span>  
  
8.  <span data-ttu-id="d2f63-119">或者，在 **[描述]** 方塊中，輸入集合的描述。</span><span class="sxs-lookup"><span data-stu-id="d2f63-119">Optionally, in the **Description** box, type a description for the collection.</span></span>  
  
9. <span data-ttu-id="d2f63-120">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="d2f63-120">Click **OK**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="d2f63-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="d2f63-121">Next Steps</span></span>  
  
-   [<span data-ttu-id="d2f63-122">將成員加入至集合 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d2f63-122">Add Members to a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/add-members-to-a-collection-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="d2f63-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d2f63-123">See Also</span></span>  
 <span data-ttu-id="d2f63-124">[&#40;Master Data Services 的集合&#41;](../../2014/master-data-services/collections-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d2f63-124">[Collections &#40;Master Data Services&#41;](../../2014/master-data-services/collections-master-data-services.md) </span></span>  
 <span data-ttu-id="d2f63-125">[&#40;Master Data Services 刪除成員或集合&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="d2f63-125">[Delete a Member or Collection &#40;Master Data Services&#41;](../../2014/master-data-services/delete-a-member-or-collection-master-data-services.md) </span></span>  
 [<span data-ttu-id="d2f63-126">建立明確階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="d2f63-126">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)  
  
  
