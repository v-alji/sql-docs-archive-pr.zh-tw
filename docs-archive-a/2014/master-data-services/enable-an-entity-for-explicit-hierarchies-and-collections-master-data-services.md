---
title: 啟用明確階層和集合的實體 (Master Data Services) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- entities [Master Data Services], enabling for collections
- entities [Master Data Services], enabling for explicit hierarchies
ms.assetid: 380e77e5-ad60-43d4-9605-34a84525f5dd
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: a8129b3f67f050603f85ffb782a9dd209cb303fc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87687004"
---
# <a name="enable-an-entity-for-explicit-hierarchies-and-collections-master-data-services"></a><span data-ttu-id="ba6f5-102">啟用明確階層和集合的實體 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="ba6f5-102">Enable an Entity for Explicit Hierarchies and Collections (Master Data Services)</span></span>
  <span data-ttu-id="ba6f5-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中，啟用明確階層和集合的實體，才能建立實體的明確階層和集合。</span><span class="sxs-lookup"><span data-stu-id="ba6f5-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], enable an entity for explicit hierarchies and collections so that you can create explicit hierarchies and collections for the entity.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="ba6f5-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="ba6f5-104">Prerequisites</span></span>  
 <span data-ttu-id="ba6f5-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="ba6f5-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="ba6f5-106">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="ba6f5-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="ba6f5-107">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="ba6f5-107">You must be a model administrator.</span></span> <span data-ttu-id="ba6f5-108">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ba6f5-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="ba6f5-109">實體必須存在。</span><span class="sxs-lookup"><span data-stu-id="ba6f5-109">An entity must exist.</span></span> <span data-ttu-id="ba6f5-110">如需詳細資訊，請參閱[建立實體 &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="ba6f5-110">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-enable-an-entity-for-explicit-hierarchies-and-collections"></a><span data-ttu-id="ba6f5-111">若要啟用明確階層和集合的實體</span><span class="sxs-lookup"><span data-stu-id="ba6f5-111">To enable an entity for explicit hierarchies and collections</span></span>  
  
1.  <span data-ttu-id="ba6f5-112">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="ba6f5-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="ba6f5-113">在 **[模型檢視]** 頁面上，從功能表列指向 **[管理]** ，然後按一下 **[實體]**。</span><span class="sxs-lookup"><span data-stu-id="ba6f5-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="ba6f5-114">在 **[實體維護]** 頁面上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="ba6f5-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="ba6f5-115">選取要更新之實體的資料列。</span><span class="sxs-lookup"><span data-stu-id="ba6f5-115">Select the row for the entity that you want to update.</span></span>  
  
5.  <span data-ttu-id="ba6f5-116">按一下 **[編輯選取的實體]**。</span><span class="sxs-lookup"><span data-stu-id="ba6f5-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="ba6f5-117">從 [**啟用明確階層和集合**] 清單中，選取 **[是]**。</span><span class="sxs-lookup"><span data-stu-id="ba6f5-117">From the **Enable explicit hierarchies and collections** list, select **Yes**.</span></span>  
  
7.  <span data-ttu-id="ba6f5-118">在 [**明確階層名稱**] 方塊中，輸入明確階層的名稱。</span><span class="sxs-lookup"><span data-stu-id="ba6f5-118">In the **Explicit hierarchy name** box, type a name for an explicit hierarchy.</span></span>  
  
8.  <span data-ttu-id="ba6f5-119">(選擇性) 清除 [強制階層]\*\*\*\* 核取方塊，將階層建立為非強制階層。</span><span class="sxs-lookup"><span data-stu-id="ba6f5-119">Optionally, clear the **Mandatory hierarchy** check box to create the hierarchy as a non-mandatory hierarchy.</span></span>  
  
9. <span data-ttu-id="ba6f5-120">按一下 [**儲存實體**]。</span><span class="sxs-lookup"><span data-stu-id="ba6f5-120">Click **Save entity**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="ba6f5-121">後續步驟</span><span class="sxs-lookup"><span data-stu-id="ba6f5-121">Next Steps</span></span>  
  
-   [<span data-ttu-id="ba6f5-122">建立明確階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ba6f5-122">Create an Explicit Hierarchy &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md)  
  
-   [<span data-ttu-id="ba6f5-123">建立集合 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ba6f5-123">Create a Collection &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-collection-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="ba6f5-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ba6f5-124">See Also</span></span>  
 <span data-ttu-id="ba6f5-125">[實體 &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="ba6f5-125">[Entities &#40;Master Data Services&#41;](../../2014/master-data-services/entities-master-data-services.md) </span></span>  
 <span data-ttu-id="ba6f5-126">[明確階層 &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="ba6f5-126">[Explicit Hierarchies &#40;Master Data Services&#41;](../../2014/master-data-services/explicit-hierarchies-master-data-services.md) </span></span>  
 [<span data-ttu-id="ba6f5-127">集合 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="ba6f5-127">Collections &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/collections-master-data-services.md)  
  
  
