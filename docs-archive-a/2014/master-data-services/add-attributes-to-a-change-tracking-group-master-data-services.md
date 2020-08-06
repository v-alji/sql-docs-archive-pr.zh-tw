---
title: 將屬性新增至變更追蹤群組 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- change tracking groups [Master Data Services]
- attributes [Master Data Services], change tracking groups
- change tracking groups [Master Data Services], adding attributes
ms.assetid: e153eb5f-70ca-4c6f-89d8-1f937ed3917d
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: c8a13dad3ca886668c96c1886f8cd238d9adad9f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606399"
---
# <a name="add-attributes-to-a-change-tracking-group-master-data-services"></a><span data-ttu-id="5c6d5-102">將屬性加入至變更追蹤群組 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="5c6d5-102">Add Attributes to a Change Tracking Group (Master Data Services)</span></span>
  <span data-ttu-id="5c6d5-103">當您想要追蹤屬性值變更時，可以在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中將屬性新增至變更追蹤群組。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], add attributes to a change tracking group when you want to track changes to the attribute's values.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="5c6d5-104">將屬性加入至變更追蹤群組之後，當屬性值變更時， [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 資料庫中的屬性會標示為已變更。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-104">After you add an attribute to a change tracking group, when values for the attribute change, the attribute is flagged as changed in the [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] database.</span></span> <span data-ttu-id="5c6d5-105">建立商務規則，以根據變更來執行動作。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-105">Create a business rule to take action based on the change.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="5c6d5-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="5c6d5-106">Prerequisites</span></span>  
 <span data-ttu-id="5c6d5-107">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="5c6d5-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="5c6d5-108">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="5c6d5-109">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-109">You must be a model administrator.</span></span> <span data-ttu-id="5c6d5-110">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="5c6d5-111">屬性必須存在，才能加入至變更追蹤群組。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-111">Attributes must exist to add to the change tracking group.</span></span> <span data-ttu-id="5c6d5-112">如需詳細資訊，請參閱 [建立文字屬性 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)(管理員 (Master Data Services))。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-112">For more information, see [Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md).</span></span>  
  
### <a name="to-add-attributes-to-a-change-tracking-group"></a><span data-ttu-id="5c6d5-113">若要將屬性加入至變更追蹤群組</span><span class="sxs-lookup"><span data-stu-id="5c6d5-113">To add attributes to a change tracking group</span></span>  
  
1.  <span data-ttu-id="5c6d5-114">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="5c6d5-115">在 [**模型瀏覽器**] 頁面上，從功能表列指向 [**管理**]，然後按一下 [**實體**]。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-115">On the **Model Explorer** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="5c6d5-116">在 **[實體維護]** 頁面上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-116">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="5c6d5-117">針對要追蹤屬性值的實體選取資料列。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-117">Select the row for the entity that you want to track attribute values for.</span></span>  
  
5.  <span data-ttu-id="5c6d5-118">按一下 **[編輯選取的實體]**。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-118">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="5c6d5-119">在 **[編輯實體]** 頁面上：</span><span class="sxs-lookup"><span data-stu-id="5c6d5-119">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="5c6d5-120">如果是分葉成員的屬性，請在 [分**葉屬性**] 窗格中選取屬性，然後按一下 [**編輯分葉屬性**]。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-120">If the attribute is for leaf members, in the **Leaf attributes** pane, select the attribute and click **Edit leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="5c6d5-121">如果是合併成員的屬性，請在 [**合併屬性**] 窗格中選取屬性，然後按一下 [**編輯合併屬性**]。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-121">If the attribute is for consolidated members, in the **Consolidated attributes** pane, select the attribute and click **Edit consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="5c6d5-122">如果是集合的屬性，請在 [**集合屬性**] 窗格中選取屬性，然後按一下 [**編輯集合屬性**]。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-122">If the attribute is for collections, in the **Collection attributes** pane, select the attribute and click **Edit collection attribute**.</span></span>  
  
7.  <span data-ttu-id="5c6d5-123">選取 [啟用變更追蹤]\*\*\*\* 核取方塊。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-123">Select the **Enable change tracking** check box.</span></span>  
  
8.  <span data-ttu-id="5c6d5-124">在 [變更追蹤群組]\*\*\*\* 方塊中，輸入群組的編號。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-124">In the **Change tracking group** box, type a number for the group.</span></span>  
  
9. <span data-ttu-id="5c6d5-125">按一下 **[儲存屬性]**。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-125">Click **Save attribute**.</span></span>  
  
10. <span data-ttu-id="5c6d5-126">按一下 **[實體維護]** 頁面上的 **[儲存實體]**。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-126">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
11. <span data-ttu-id="5c6d5-127">重複此程序，加入要包含在群組中的所有屬性。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-127">Repeat this procedure for all attributes you want to include in the group.</span></span> <span data-ttu-id="5c6d5-128">對群組中的每個屬性，使用相同的變更追蹤群組編號。</span><span class="sxs-lookup"><span data-stu-id="5c6d5-128">Use the same change tracking group number for each attribute in the group.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5c6d5-129">後續步驟</span><span class="sxs-lookup"><span data-stu-id="5c6d5-129">Next Steps</span></span>  
  
-   [<span data-ttu-id="5c6d5-130">根據屬性值變更來起始動作 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5c6d5-130">Initiate Actions Based on Attribute Value Changes &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/initiate-actions-based-on-attribute-value-changes-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="5c6d5-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c6d5-131">See Also</span></span>  
 <span data-ttu-id="5c6d5-132">[建立 &#40;Master Data Services&#41;的文字屬性](../../2014/master-data-services/create-a-text-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="5c6d5-132">[Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="5c6d5-133">建立網域屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="5c6d5-133">Create a Domain-Based Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md)  
  
  
