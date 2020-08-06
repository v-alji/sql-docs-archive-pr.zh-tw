---
title: 建立明確階層 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating explicit hierarchies [Master Data Services]
- explicit hierarchies, creating
ms.assetid: ba768393-6990-4eda-8cb0-d58cb3cfc2e2
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: aebf95e68f210fe5a573aed092231670c10fa188
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597882"
---
# <a name="create-an-explicit-hierarchy-master-data-services"></a><span data-ttu-id="331f8-102">建立明確階層 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="331f8-102">Create an Explicit Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="331f8-103">當您需要成員可存在於任何層級的不完全階層時，可以在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中建立明確階層。</span><span class="sxs-lookup"><span data-stu-id="331f8-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create an explicit hierarchy when you need a ragged hierarchy in which members can exist at any level.</span></span> <span data-ttu-id="331f8-104">明確階層包含來自單一實體的成員。</span><span class="sxs-lookup"><span data-stu-id="331f8-104">Explicit hierarchies contain members from a single entity.</span></span>  
  
 <span data-ttu-id="331f8-105">建立明確階層之後，您可以在總管\*\*\*\* 功能區域的這個階層中加入成員。</span><span class="sxs-lookup"><span data-stu-id="331f8-105">After you create an explicit hierarchy, you can add members to it in the **Explorer** functional area.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="331f8-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="331f8-106">Prerequisites</span></span>  
 <span data-ttu-id="331f8-107">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="331f8-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="331f8-108">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="331f8-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="331f8-109">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="331f8-109">You must be a model administrator.</span></span> <span data-ttu-id="331f8-110">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="331f8-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="331f8-111">您必須啟用明確階層和集合的實體。</span><span class="sxs-lookup"><span data-stu-id="331f8-111">The entity must be enabled for explicit hierarchies and collections.</span></span> <span data-ttu-id="331f8-112">如需詳細資訊，請參閱[啟用明確階層和集合的實體 &#40;Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="331f8-112">For more information, see [Enable an Entity for Explicit Hierarchies and Collections &#40;Master Data Services&#41;](../../2014/master-data-services/enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services.md).</span></span>  
  
### <a name="to-create-an-explicit-hierarchy"></a><span data-ttu-id="331f8-113">若要建立明確階層</span><span class="sxs-lookup"><span data-stu-id="331f8-113">To create an explicit hierarchy</span></span>  
  
1.  <span data-ttu-id="331f8-114">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="331f8-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="331f8-115">在 **[模型檢視]** 頁面上，從功能表列指向 **[管理]** ，然後按一下 **[實體]**。</span><span class="sxs-lookup"><span data-stu-id="331f8-115">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="331f8-116">在 **[實體維護]** 頁面上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="331f8-116">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="331f8-117">針對要建立明確階層的實體選取資料列。</span><span class="sxs-lookup"><span data-stu-id="331f8-117">Select the row for the entity that you want to create an explicit hierarchy for.</span></span>  
  
5.  <span data-ttu-id="331f8-118">按一下 **[編輯選取的實體]**。</span><span class="sxs-lookup"><span data-stu-id="331f8-118">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="331f8-119">在 [**編輯實體**] 頁面的 [**明確**階層] 窗格中，按一下 [**加入明確**階層]。</span><span class="sxs-lookup"><span data-stu-id="331f8-119">On the **Edit Entity** page, in the **Explicit hierarchies** pane, click **Add explicit hierarchy**.</span></span>  
  
7.  <span data-ttu-id="331f8-120">在 [**加入明確**階層] 頁面的 [**明確階層名稱**] 方塊中，輸入階層的名稱。</span><span class="sxs-lookup"><span data-stu-id="331f8-120">On the **Add Explicit Hierarchy** page, in the **Explicit hierarchy name** box, type a name for the hierarchy.</span></span>  
  
8.  <span data-ttu-id="331f8-121">(選擇性) 清除 [強制階層]\*\*\*\* 核取方塊，將階層建立為非強制階層。</span><span class="sxs-lookup"><span data-stu-id="331f8-121">Optionally, clear the **Mandatory hierarchy** check box to create the hierarchy as a non-mandatory hierarchy.</span></span> <span data-ttu-id="331f8-122">如需階層類型的詳細資訊，請參閱 [明確階層 &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)(管理員 (Master Data Services))。</span><span class="sxs-lookup"><span data-stu-id="331f8-122">For more information about hierarchy types, see [Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="331f8-123">按一下 [**儲存**階層]。</span><span class="sxs-lookup"><span data-stu-id="331f8-123">Click **Save hierarchy**.</span></span>  
  
10. <span data-ttu-id="331f8-124">在 [**編輯實體**] 頁面上，按一下 [**儲存實體**]。</span><span class="sxs-lookup"><span data-stu-id="331f8-124">On the **Edit Entity** page, click **Save entity**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="331f8-125">後續步驟</span><span class="sxs-lookup"><span data-stu-id="331f8-125">Next Steps</span></span>  
  
-   [<span data-ttu-id="331f8-126">建立合併成員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="331f8-126">Create a Consolidated Member &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-consolidated-member-master-data-services.md)  
  
-   [<span data-ttu-id="331f8-127">在階層中移動成員 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="331f8-127">Move Members within a Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="331f8-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="331f8-128">See Also</span></span>  
 <span data-ttu-id="331f8-129">[明確階層 &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="331f8-129">[Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span></span>  
 <span data-ttu-id="331f8-130">[具有明確大寫的衍生階層 &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="331f8-130">[Derived Hierarchies with Explicit Caps &#40;Master Data Services&#41;](../../2014/master-data-services/derived-hierarchies-with-explicit-caps-master-data-services.md) </span></span>  
 [<span data-ttu-id="331f8-131">變更明確階層名稱 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="331f8-131">Change an Explicit Hierarchy Name &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/change-an-explicit-hierarchy-name-master-data-services.md)  
  
  
