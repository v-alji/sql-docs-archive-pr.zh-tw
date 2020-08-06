---
title: 建立網域屬性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- domain-based attributes [Master Data Services], creating
- creating domain-based attributes [Master Data Services]
- attributes [Master Data Services], creating domain-based attributes
ms.assetid: 11c31c9f-e6cc-47b7-b76a-d691f84c93c6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 51c0f44bb76ae2ad4c25987ed5e5ee144a18c739
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592735"
---
# <a name="create-a-domain-based-attribute-master-data-services"></a><span data-ttu-id="effbc-102">建立網域屬性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="effbc-102">Create a Domain-Based Attribute (Master Data Services)</span></span>
  <span data-ttu-id="effbc-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，建立網域屬性，以使用實體成員來擴展屬性值。</span><span class="sxs-lookup"><span data-stu-id="effbc-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a domain-based attribute to populate an attribute's values with members from an entity.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="effbc-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="effbc-104">Prerequisites</span></span>  
 <span data-ttu-id="effbc-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="effbc-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="effbc-106">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="effbc-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="effbc-107">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="effbc-107">You must be a model administrator.</span></span> <span data-ttu-id="effbc-108">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="effbc-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="effbc-109">屬性值的來源實體必須存在。</span><span class="sxs-lookup"><span data-stu-id="effbc-109">An entity must exist to use as the source of the attribute values.</span></span> <span data-ttu-id="effbc-110">例如，若要根據色彩實體建立網域屬性，您必須先建立色彩實體。</span><span class="sxs-lookup"><span data-stu-id="effbc-110">For example, to create a domain-based attribute based on the Color entity, you must first create the Color entity.</span></span> <span data-ttu-id="effbc-111">如需詳細資訊，請參閱[建立實體 &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="effbc-111">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="effbc-112">建立屬性的實體必須存在。</span><span class="sxs-lookup"><span data-stu-id="effbc-112">An entity must exist to create the attribute for.</span></span> <span data-ttu-id="effbc-113">如需詳細資訊，請參閱[建立實體 &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="effbc-113">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-domain-based-attribute"></a><span data-ttu-id="effbc-114">若要建立網域屬性</span><span class="sxs-lookup"><span data-stu-id="effbc-114">To create a domain-based attribute</span></span>  
  
1.  <span data-ttu-id="effbc-115">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="effbc-115">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="effbc-116">在 **[模型檢視]** 頁面上，從功能表列指向 **[管理]** ，然後按一下 **[實體]**。</span><span class="sxs-lookup"><span data-stu-id="effbc-116">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="effbc-117">在 **[實體維護]** 頁面上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="effbc-117">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="effbc-118">針對要建立屬性的實體選取資料列。</span><span class="sxs-lookup"><span data-stu-id="effbc-118">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="effbc-119">按一下 **[編輯選取的實體]**。</span><span class="sxs-lookup"><span data-stu-id="effbc-119">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="effbc-120">在 **[編輯實體]** 頁面上：</span><span class="sxs-lookup"><span data-stu-id="effbc-120">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="effbc-121">如果是分葉成員的屬性，則按一下 **[分葉成員屬性]** 窗格中的 **[加入分葉屬性]**。</span><span class="sxs-lookup"><span data-stu-id="effbc-121">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="effbc-122">如果是合併成員的屬性，則按一下 **[合併成員屬性]** 窗格中的 **[加入合併屬性]**。</span><span class="sxs-lookup"><span data-stu-id="effbc-122">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="effbc-123">如果是集合的屬性，則按一下 **[集合屬性]** 窗格中的 **[加入集合屬性]**。</span><span class="sxs-lookup"><span data-stu-id="effbc-123">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="effbc-124">在 [**加入屬性**] 頁面上，選取 [**網域型**] 選項。</span><span class="sxs-lookup"><span data-stu-id="effbc-124">On the **Add Attribute** page, select the **Domain-based** option.</span></span>  
  
8.  <span data-ttu-id="effbc-125">在 **[名稱]** 方塊中，輸入屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="effbc-125">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="effbc-126">它不需要和屬性值的來源實體同名。</span><span class="sxs-lookup"><span data-stu-id="effbc-126">It does not have to be the same name as the entity that you use for the source of the attribute values.</span></span>  
  
9. <span data-ttu-id="effbc-127">在 **[顯示像素寬度]** 方塊中，輸入要在 **[總管]** 方格中顯示的屬性資料行寬度。</span><span class="sxs-lookup"><span data-stu-id="effbc-127">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="effbc-128">從 [**實體**] 清單中，選擇要用來填入屬性值的實體。</span><span class="sxs-lookup"><span data-stu-id="effbc-128">From the **Entity** list, choose the entity to be used to populate the attribute values.</span></span>  
  
11. <span data-ttu-id="effbc-129">選擇性。</span><span class="sxs-lookup"><span data-stu-id="effbc-129">Optional.</span></span> <span data-ttu-id="effbc-130">選取 [啟用變更追蹤]\*\*\*\* 以追蹤屬性群組的變更。</span><span class="sxs-lookup"><span data-stu-id="effbc-130">Select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="effbc-131">如需詳細資訊，請參閱[將屬性加入至變更追蹤群組 &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="effbc-131">For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).</span></span>  
  
12. <span data-ttu-id="effbc-132">按一下 **[儲存屬性]**。</span><span class="sxs-lookup"><span data-stu-id="effbc-132">Click **Save attribute**.</span></span>  
  
13. <span data-ttu-id="effbc-133">按一下 **[實體維護]** 頁面上的 **[儲存實體]**。</span><span class="sxs-lookup"><span data-stu-id="effbc-133">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="effbc-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="effbc-134">See Also</span></span>  
 <span data-ttu-id="effbc-135">[以網域為基礎的屬性 &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="effbc-135">[Domain-Based Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/domain-based-attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="effbc-136">[建立衍生階層 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="effbc-136">[Create a Derived Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-derived-hierarchy-master-data-services.md) </span></span>  
 <span data-ttu-id="effbc-137">[變更屬性名稱 &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="effbc-137">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 [<span data-ttu-id="effbc-138">刪除屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="effbc-138">Delete an Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/delete-an-attribute-master-data-services.md)  
  
  
