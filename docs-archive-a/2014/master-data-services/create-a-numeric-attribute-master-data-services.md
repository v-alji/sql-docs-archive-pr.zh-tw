---
title: 建立數值屬性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attributes [Master Data Services], creating number attributes
- creating number attributes [Master Data Services]
ms.assetid: c0dbb6d8-ba78-485a-a40d-6d5cb7e75d0a
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: bb9302c0b585c21410a6a764dc2e6dac845c6299
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584623"
---
# <a name="create-a-numeric-attribute-master-data-services"></a><span data-ttu-id="b73a0-102">建立數值屬性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="b73a0-102">Create a Numeric Attribute (Master Data Services)</span></span>
  <span data-ttu-id="b73a0-103">當您想要讓使用者輸入數字作為屬性值時，可以在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中建立數值屬性。</span><span class="sxs-lookup"><span data-stu-id="b73a0-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a numeric attribute when you want users to enter a number as an attribute value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b73a0-104">數值屬性有限制。</span><span class="sxs-lookup"><span data-stu-id="b73a0-104">Numeric attributes have limitations.</span></span> <span data-ttu-id="b73a0-105">如需詳細資訊，請參閱 [屬性 &#40;Master Data Services&#41;](attributes-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b73a0-105">For more information, see [Attributes &#40;Master Data Services&#41;](attributes-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="b73a0-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="b73a0-106">Prerequisites</span></span>  
 <span data-ttu-id="b73a0-107">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="b73a0-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="b73a0-108">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="b73a0-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="b73a0-109">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="b73a0-109">You must be a model administrator.</span></span> <span data-ttu-id="b73a0-110">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b73a0-110">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="b73a0-111">建立屬性的實體必須存在。</span><span class="sxs-lookup"><span data-stu-id="b73a0-111">An entity must exist to create the attribute for.</span></span> <span data-ttu-id="b73a0-112">如需詳細資訊，請參閱[建立實體 &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b73a0-112">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-numeric-attribute"></a><span data-ttu-id="b73a0-113">若要建立數值屬性</span><span class="sxs-lookup"><span data-stu-id="b73a0-113">To create a numeric attribute</span></span>  
  
1.  <span data-ttu-id="b73a0-114">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="b73a0-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="b73a0-115">在 **[模型檢視]** 頁面上，從功能表列指向 **[管理]** ，然後按一下 **[實體]**。</span><span class="sxs-lookup"><span data-stu-id="b73a0-115">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="b73a0-116">在 **[實體維護]** 頁面上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="b73a0-116">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="b73a0-117">針對要建立屬性的實體選取資料列。</span><span class="sxs-lookup"><span data-stu-id="b73a0-117">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="b73a0-118">按一下 **[編輯選取的實體]**。</span><span class="sxs-lookup"><span data-stu-id="b73a0-118">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="b73a0-119">在 **[編輯實體]** 頁面上：</span><span class="sxs-lookup"><span data-stu-id="b73a0-119">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="b73a0-120">如果是分葉成員的屬性，則按一下 **[分葉成員屬性]** 窗格中的 **[加入分葉屬性]**。</span><span class="sxs-lookup"><span data-stu-id="b73a0-120">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="b73a0-121">如果是合併成員的屬性，則按一下 **[合併成員屬性]** 窗格中的 **[加入合併屬性]**。</span><span class="sxs-lookup"><span data-stu-id="b73a0-121">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="b73a0-122">如果是集合的屬性，則按一下 **[集合屬性]** 窗格中的 **[加入集合屬性]**。</span><span class="sxs-lookup"><span data-stu-id="b73a0-122">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="b73a0-123">選取 **[加入屬性]** 頁面上的 **[自由格式]** 選項。</span><span class="sxs-lookup"><span data-stu-id="b73a0-123">On the **Add Attribute** page, select the **Free-form** option.</span></span>  
  
8.  <span data-ttu-id="b73a0-124">在 **[名稱]** 方塊中，輸入屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="b73a0-124">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="b73a0-125">如需不應當做屬性名稱使用的字組清單，請參閱[保留字 &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="b73a0-125">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="b73a0-126">在 **[顯示像素寬度]** 方塊中，輸入要在 **[總管]** 方格中顯示的屬性資料行寬度。</span><span class="sxs-lookup"><span data-stu-id="b73a0-126">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="b73a0-127">從 [資料類型]\*\*\*\* 清單中，選取 [數字]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="b73a0-127">From the **Data type** list, select **Number**.</span></span>  
  
11. <span data-ttu-id="b73a0-128">在 [小數]\*\*\*\* 方塊中，輸入可以在小數點後面輸入的位數。</span><span class="sxs-lookup"><span data-stu-id="b73a0-128">In the **Decimals** box, type the number of numbers that can be entered after a decimal.</span></span>  
  
12. <span data-ttu-id="b73a0-129">從 [**輸入遮罩**] 清單中，選取負數的格式。</span><span class="sxs-lookup"><span data-stu-id="b73a0-129">From the **Input mask** list, select a format for negative numbers.</span></span>  
  
13. <span data-ttu-id="b73a0-130">(選擇性) 選取 **[啟用變更追蹤]** 以追蹤屬性群組的變更。</span><span class="sxs-lookup"><span data-stu-id="b73a0-130">Optionally, select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="b73a0-131">如需詳細資訊，請參閱 [將屬性加入至變更追蹤群組 &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) 。</span><span class="sxs-lookup"><span data-stu-id="b73a0-131">See [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md) for more information.</span></span>  
  
14. <span data-ttu-id="b73a0-132">按一下 **[儲存屬性]**。</span><span class="sxs-lookup"><span data-stu-id="b73a0-132">Click **Save attribute**.</span></span>  
  
15. <span data-ttu-id="b73a0-133">按一下 **[實體維護]** 頁面上的 **[儲存實體]**。</span><span class="sxs-lookup"><span data-stu-id="b73a0-133">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b73a0-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b73a0-134">See Also</span></span>  
 <span data-ttu-id="b73a0-135">[Master Data Services &#40;的屬性&#41;](attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b73a0-135">[Attributes &#40;Master Data Services&#41;](attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="b73a0-136">[變更屬性名稱 &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b73a0-136">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 <span data-ttu-id="b73a0-137">[建立以網域為基礎的屬性 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="b73a0-137">[Create a Domain-Based Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="b73a0-138">建立檔案屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="b73a0-138">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
