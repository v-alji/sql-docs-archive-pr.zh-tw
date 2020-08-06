---
title: 建立屬性群組 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- attribute groups [Master Data Services], creating
- creating attribute groups [Master Data Services]
ms.assetid: 798c325e-e8d8-412a-b02e-118f2741d1c7
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: fbd95869082ea0a73f3abea092163c4705e4da5c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87705222"
---
# <a name="create-an-attribute-group-master-data-services"></a><span data-ttu-id="20661-102">建立屬性群組 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="20661-102">Create an Attribute Group (Master Data Services)</span></span>
  <span data-ttu-id="20661-103">當您想要在總管\*\*\*\* 方格的個別索引標籤上顯示屬性時，可以在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中建立屬性群組。</span><span class="sxs-lookup"><span data-stu-id="20661-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create attribute groups when you want to display attributes on individual tabs in the **Explorer** grid.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="20661-104">當您建立屬性群組時，它會自動隱藏起來不讓所有使用者看到，除了建立它的使用者以外。</span><span class="sxs-lookup"><span data-stu-id="20661-104">When you create an attribute group, it is automatically hidden from all users except the one who created it.</span></span> <span data-ttu-id="20661-105">如需如何顯示此群組的詳細資訊，請參閱 [讓使用者看到屬性群組 &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="20661-105">For more information about making the group visible, see [Make an Attribute Group Visible to Users &#40;Master Data Services&#41;](make-an-attribute-group-visible-to-users-master-data-services.md).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="20661-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="20661-106">Prerequisites</span></span>  
 <span data-ttu-id="20661-107">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="20661-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="20661-108">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="20661-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="20661-109">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="20661-109">You must be a model administrator.</span></span> <span data-ttu-id="20661-110">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="20661-110">For more information, see [Administrators &#40;Master Data Services&#41;](../../2014/master-data-services/administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="20661-111">至少有一個屬性必須存在。</span><span class="sxs-lookup"><span data-stu-id="20661-111">At least one attribute must exist.</span></span> <span data-ttu-id="20661-112">如需詳細資訊，請參閱 [建立文字屬性 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)(管理員 (Master Data Services))。</span><span class="sxs-lookup"><span data-stu-id="20661-112">For more information, see [Create a Text Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-text-attribute-master-data-services.md).</span></span>  
  
### <a name="to-create-an-attribute-group"></a><span data-ttu-id="20661-113">若要建立屬性群組</span><span class="sxs-lookup"><span data-stu-id="20661-113">To create an attribute group</span></span>  
  
1.  <span data-ttu-id="20661-114">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="20661-114">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="20661-115">在 [**模型視圖**] 頁面上，從功能表列指向 [**管理**]，然後按一下 [**屬性群組**]。</span><span class="sxs-lookup"><span data-stu-id="20661-115">On the **Model View** page, from the menu bar, point to **Manage** and click **Attribute Groups**.</span></span>  
  
3.  <span data-ttu-id="20661-116">從 **[模型]** 清單中選取模型。</span><span class="sxs-lookup"><span data-stu-id="20661-116">From the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="20661-117">從 [實體]\*\*\*\* 清單中選取實體。</span><span class="sxs-lookup"><span data-stu-id="20661-117">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="20661-118">按一下 [分葉群組]\*\*\*\*、[合併群組]\*\*\*\* 或 [集合群組]\*\*\*\*，分別為分葉成員、合併成員或集合建立屬性群組。</span><span class="sxs-lookup"><span data-stu-id="20661-118">Click **Leaf Groups**, **Consolidated Groups**, or **Collection Groups** to create an attribute group of leaf members, consolidated members, or collections respectively.</span></span>  
  
6.  <span data-ttu-id="20661-119">按一下 [**加入屬性群組**]。</span><span class="sxs-lookup"><span data-stu-id="20661-119">Click **Add attribute group**.</span></span>  
  
7.  <span data-ttu-id="20661-120">在 [分**葉組名**] 方塊中，輸入群組的名稱。</span><span class="sxs-lookup"><span data-stu-id="20661-120">In the **Leaf group name** box, type a name for the group.</span></span> <span data-ttu-id="20661-121">這是 [ **Explorer**] 索引標籤上顯示的名稱。</span><span class="sxs-lookup"><span data-stu-id="20661-121">This is the name displayed on the tab in **Explorer**.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="20661-122">如果您在步驟5中選取了 **[合併群組**] 或 [**集合群組**]，此方塊會分別是 **[合併組名**] 或 [**集合組名**]。</span><span class="sxs-lookup"><span data-stu-id="20661-122">If you selected **Consolidated Groups** or **Collection Groups** in step 5, this box is **Consolidated group name** or **Collection group name**, respectively.</span></span>  
  
8.  <span data-ttu-id="20661-123">按一下 [儲存群組]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="20661-123">Click **Save group**.</span></span>  
  
9. <span data-ttu-id="20661-124">展開群組的資料夾。</span><span class="sxs-lookup"><span data-stu-id="20661-124">Expand the folder for the group.</span></span>  
  
10. <span data-ttu-id="20661-125">按一下 **[屬性]**。</span><span class="sxs-lookup"><span data-stu-id="20661-125">Click **Attributes**.</span></span>  
  
11. <span data-ttu-id="20661-126">按一下 [**編輯選取的專案**]。</span><span class="sxs-lookup"><span data-stu-id="20661-126">Click **Edit selected item**.</span></span>  
  
12. <span data-ttu-id="20661-127">按一下 [**可用**] 方塊中的 [屬性]，然後按一下 [**新增**] 箭號。</span><span class="sxs-lookup"><span data-stu-id="20661-127">Click attributes in the **Available** box and click the **Add** arrow.</span></span> <span data-ttu-id="20661-128">若要全部加入，請按一下 [全部加入]\*\*\*\* 箭號。</span><span class="sxs-lookup"><span data-stu-id="20661-128">To add all, click the **Add All** arrow.</span></span>  
  
13. <span data-ttu-id="20661-129">（選擇性）按一下**向上**和**向下**箭號，變更屬性由左至右的順序。</span><span class="sxs-lookup"><span data-stu-id="20661-129">Optionally, click the **Up** and **Down** arrows to change the left-to-right order of the attributes.</span></span>  
  
14. <span data-ttu-id="20661-130">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="20661-130">Click **Save**.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="20661-131">後續步驟</span><span class="sxs-lookup"><span data-stu-id="20661-131">Next Steps</span></span>  
  
-   [<span data-ttu-id="20661-132">讓使用者看到屬性群組 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="20661-132">Make an Attribute Group Visible to Users &#40;Master Data Services&#41;</span></span>](make-an-attribute-group-visible-to-users-master-data-services.md)  
  
## <a name="see-also"></a><span data-ttu-id="20661-133">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20661-133">See Also</span></span>  
 <span data-ttu-id="20661-134">[屬性群組 &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="20661-134">[Attribute Groups &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span></span>  
 <span data-ttu-id="20661-135">[Master Data Services &#40;的屬性&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="20661-135">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="20661-136">[變更屬性組名 &#40;Master Data Services&#41;](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="20661-136">[Change an Attribute Group Name &#40;Master Data Services&#41;](../../2014/master-data-services/change-an-attribute-group-name-master-data-services.md) </span></span>  
 <span data-ttu-id="20661-137">[刪除屬性群組 &#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="20661-137">[Delete an Attribute Group &#40;Master Data Services&#41;](../../2014/master-data-services/delete-an-attribute-group-master-data-services.md) </span></span>  
 <span data-ttu-id="20661-138">[分葉許可權 &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="20661-138">[Leaf Permissions &#40;Master Data Services&#41;](../../2014/master-data-services/leaf-permissions-master-data-services.md) </span></span>  
 [<span data-ttu-id="20661-139">合併的許可權 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="20661-139">Consolidated Permissions &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/consolidated-permissions-master-data-services.md)  
  
  
