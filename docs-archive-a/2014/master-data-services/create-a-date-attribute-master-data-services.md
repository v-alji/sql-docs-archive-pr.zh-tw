---
title: 建立日期屬性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating date attributes [Master Data Services]
- attributes [Master Data Services], creating date attributes
ms.assetid: 22a8f1a3-b4f2-4cfa-8495-7daad5ce9d12
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 93797b90ff03c6a2b60ce8e015897a46a7448aad
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584626"
---
# <a name="create-a-date-attribute-master-data-services"></a><span data-ttu-id="f5d1f-102">建立日期屬性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="f5d1f-102">Create a Date Attribute (Master Data Services)</span></span>
  <span data-ttu-id="f5d1f-103">當您想要讓使用者輸入日期做為屬性值時，可以在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中建立日期屬性。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a date attribute when you want users to enter a date as an attribute value.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="f5d1f-104">該屬性稱為 DateTime，但不支援時間值。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-104">The attribute is called DateTime, but time values are not supported.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="f5d1f-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="f5d1f-105">Prerequisites</span></span>  
 <span data-ttu-id="f5d1f-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="f5d1f-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="f5d1f-107">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="f5d1f-108">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-108">You must be a model administrator.</span></span> <span data-ttu-id="f5d1f-109">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="f5d1f-110">您必須有要建立屬性的實體。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-110">You must have an entity to create the attribute for.</span></span> <span data-ttu-id="f5d1f-111">如需詳細資訊，請參閱[建立實體 &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-111">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-date-attribute"></a><span data-ttu-id="f5d1f-112">若要建立日期屬性</span><span class="sxs-lookup"><span data-stu-id="f5d1f-112">To create a date attribute</span></span>  
  
1.  <span data-ttu-id="f5d1f-113">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="f5d1f-114">在 **[模型檢視]** 頁面上，從功能表列指向 **[管理]** ，然後按一下 **[實體]**。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-114">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="f5d1f-115">在 **[實體維護]** 頁面上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-115">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="f5d1f-116">針對要建立屬性的實體選取資料列。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-116">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="f5d1f-117">按一下 **[編輯選取的實體]**。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-117">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="f5d1f-118">在 **[編輯實體]** 頁面上：</span><span class="sxs-lookup"><span data-stu-id="f5d1f-118">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="f5d1f-119">如果是分葉成員的屬性，則按一下 **[分葉成員屬性]** 窗格中的 **[加入分葉屬性]**。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-119">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="f5d1f-120">如果是合併成員的屬性，則按一下 **[合併成員屬性]** 窗格中的 **[加入合併屬性]**。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-120">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="f5d1f-121">如果是集合的屬性，則按一下 **[集合屬性]** 窗格中的 **[加入集合屬性]**。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-121">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="f5d1f-122">選取 **[加入屬性]** 頁面上的 **[自由格式]** 選項。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-122">On the **Add Attribute** page, select the **Free-form** option.</span></span>  
  
8.  <span data-ttu-id="f5d1f-123">在 **[名稱]** 方塊中，輸入屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-123">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="f5d1f-124">如需不應當做屬性名稱使用的字組清單，請參閱[保留字 &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-124">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="f5d1f-125">在 **[顯示像素寬度]** 方塊中，輸入要在 **[總管]** 方格中顯示的屬性資料行寬度。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-125">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="f5d1f-126">從 **[資料類型]** 清單中，選取 **[日期時間]**。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-126">From the **Data type** list, select **DateTime**.</span></span>  
  
11. <span data-ttu-id="f5d1f-127">從 **[輸入遮罩]** 清單中選取日期格式。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-127">From the **Input mask** list, select a format for dates.</span></span>  
  
12. <span data-ttu-id="f5d1f-128">(選擇性) 選取 **[啟用變更追蹤]** 以追蹤屬性群組的變更。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-128">Optionally, select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="f5d1f-129">如需詳細資訊，請參閱[將屬性加入至變更追蹤群組 &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-129">For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).</span></span>  
  
13. <span data-ttu-id="f5d1f-130">按一下 **[儲存屬性]**。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-130">Click **Save attribute**.</span></span>  
  
14. <span data-ttu-id="f5d1f-131">按一下 **[實體維護]** 頁面上的 **[儲存實體]**。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-131">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="to-display-the-time-portion-of-a-datetime-value"></a><span data-ttu-id="f5d1f-132">若要顯示日期時間值的時間部分</span><span class="sxs-lookup"><span data-stu-id="f5d1f-132">To display the time portion of a datetime value</span></span>  
 <span data-ttu-id="f5d1f-133">若要讓使用者介面顯示日期時間值的時間部分，您必須選擇適用於屬性的輸入遮罩。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-133">To have the user interface display the time portion of a datetime value, you must select an appropriate input mask for the attribute.</span></span> <span data-ttu-id="f5d1f-134">日期時間屬性的內建遮罩都無法執行這項處理，但是您可以加入可讓您顯示時間的新遮罩。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-134">None of the built-in masks for Datetime attributes do this, but you can add a new mask that will allow you to display time.</span></span> <span data-ttu-id="f5d1f-135">若要這樣做，請在儲存內建遮罩之 MDS 資料庫的 mdm.tblList 資料表中加入資料列。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-135">To do so, add a row in the mdm.tblList table of the MDS database, where the built-in masks are stored.</span></span> <span data-ttu-id="f5d1f-136">此資料列應該有下列值：</span><span class="sxs-lookup"><span data-stu-id="f5d1f-136">The row should have the following values:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="f5d1f-137">ListCode</span><span class="sxs-lookup"><span data-stu-id="f5d1f-137">ListCode</span></span>|<span data-ttu-id="f5d1f-138">lstInputMask</span><span class="sxs-lookup"><span data-stu-id="f5d1f-138">lstInputMask</span></span>|  
|<span data-ttu-id="f5d1f-139">ListName</span><span class="sxs-lookup"><span data-stu-id="f5d1f-139">ListName</span></span>|<span data-ttu-id="f5d1f-140">[輸入遮罩]</span><span class="sxs-lookup"><span data-stu-id="f5d1f-140">Input Mask</span></span>|  
|<span data-ttu-id="f5d1f-141">Seq</span><span class="sxs-lookup"><span data-stu-id="f5d1f-141">Seq</span></span>|<span data-ttu-id="f5d1f-142">19</span><span class="sxs-lookup"><span data-stu-id="f5d1f-142">19</span></span>|  
|<span data-ttu-id="f5d1f-143">List Option</span><span class="sxs-lookup"><span data-stu-id="f5d1f-143">List Option</span></span>|<span data-ttu-id="f5d1f-144">dd/MM/yyyy hh:mm:ss tt</span><span class="sxs-lookup"><span data-stu-id="f5d1f-144">dd/MM/yyyy hh:mm:ss tt</span></span>|  
|<span data-ttu-id="f5d1f-145">Option ID</span><span class="sxs-lookup"><span data-stu-id="f5d1f-145">Option ID</span></span>|<span data-ttu-id="f5d1f-146">19</span><span class="sxs-lookup"><span data-stu-id="f5d1f-146">19</span></span>|  
|<span data-ttu-id="f5d1f-147">IsVisible</span><span class="sxs-lookup"><span data-stu-id="f5d1f-147">IsVisible</span></span>|<span data-ttu-id="f5d1f-148">1</span><span class="sxs-lookup"><span data-stu-id="f5d1f-148">1</span></span>|  
|<span data-ttu-id="f5d1f-149">Group_ID</span><span class="sxs-lookup"><span data-stu-id="f5d1f-149">Group_ID</span></span>|<span data-ttu-id="f5d1f-150">3</span><span class="sxs-lookup"><span data-stu-id="f5d1f-150">3</span></span>|  
  
 <span data-ttu-id="f5d1f-151">當您在 mdm.tblList 資料表中輸入包含上述值的資料列之後，[輸入遮罩] 清單方塊中將會提供 "dd/MM/yyyy hh:mm:ss tt" 遮罩。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-151">After you enter a row with the above values in the mdm.tblList table, the "dd/MM/yyyy hh:mm:ss tt" mask will be available in the Input mask list box.</span></span> <span data-ttu-id="f5d1f-152">然後，您可以選取該遮罩，在 MDS Explorer 中實體的日期時間屬性資料行中顯示日期和時間。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-152">You can then select that mask to display the date and time in a datetime attribute column of an entity in the MDS Explorer.</span></span>  
  
 <span data-ttu-id="f5d1f-153">輸入遮罩是自訂的 .NET DateTime 格式字串。</span><span class="sxs-lookup"><span data-stu-id="f5d1f-153">The Input Mask is a custom .NET DateTime format string.</span></span> <span data-ttu-id="f5d1f-154">如需詳細資訊，請參閱 [自訂日期和時間格式字串](https://msdn.microsoft.com/library/8kb3ddd4\(v=vs.110\).aspx)</span><span class="sxs-lookup"><span data-stu-id="f5d1f-154">For more information, see [Custom Date and Time Format Strings](https://msdn.microsoft.com/library/8kb3ddd4\(v=vs.110\).aspx)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5d1f-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f5d1f-155">See Also</span></span>  
 <span data-ttu-id="f5d1f-156">[Master Data Services &#40;的屬性&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f5d1f-156">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="f5d1f-157">[變更屬性名稱 &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f5d1f-157">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 <span data-ttu-id="f5d1f-158">[建立以網域為基礎的屬性 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="f5d1f-158">[Create a Domain-Based Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="f5d1f-159">建立檔案屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="f5d1f-159">Create a File Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-file-attribute-master-data-services.md)  
  
  
