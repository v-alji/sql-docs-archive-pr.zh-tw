---
title: 建立檔案屬性 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- creating file attributes [Master Data Services]
- attributes [Master Data Services], creating file attributes
ms.assetid: d224886b-2ef1-4658-8b01-2213cc4b8df6
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: f4f6e2f10a830d089d1d217f7cf54d0b8557add9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592734"
---
# <a name="create-a-file-attribute-master-data-services"></a><span data-ttu-id="2eb03-102">建立檔案屬性 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="2eb03-102">Create a File Attribute (Master Data Services)</span></span>
  <span data-ttu-id="2eb03-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，建立檔案屬性，以使用檔案來擴展屬性值。</span><span class="sxs-lookup"><span data-stu-id="2eb03-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], create a file attribute to populate attribute values with files.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="2eb03-104">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="2eb03-104">Prerequisites</span></span>  
 <span data-ttu-id="2eb03-105">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="2eb03-105">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="2eb03-106">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="2eb03-106">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="2eb03-107">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="2eb03-107">You must be a model administrator.</span></span> <span data-ttu-id="2eb03-108">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2eb03-108">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="2eb03-109">建立屬性的實體必須存在。</span><span class="sxs-lookup"><span data-stu-id="2eb03-109">An entity must exist to create the attribute for.</span></span> <span data-ttu-id="2eb03-110">如需詳細資訊，請參閱[建立實體 &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2eb03-110">For more information, see [Create an Entity &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-entity-master-data-services.md).</span></span>  
  
### <a name="to-create-a-file-attribute"></a><span data-ttu-id="2eb03-111">若要建立檔案屬性</span><span class="sxs-lookup"><span data-stu-id="2eb03-111">To create a file attribute</span></span>  
  
1.  <span data-ttu-id="2eb03-112">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="2eb03-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="2eb03-113">在 **[模型檢視]** 頁面上，從功能表列指向 **[管理]** ，然後按一下 **[實體]**。</span><span class="sxs-lookup"><span data-stu-id="2eb03-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="2eb03-114">在 **[實體維護]** 頁面上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="2eb03-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="2eb03-115">針對要建立屬性的實體選取資料列。</span><span class="sxs-lookup"><span data-stu-id="2eb03-115">Select the row for the entity that you want to create an attribute for.</span></span>  
  
5.  <span data-ttu-id="2eb03-116">按一下 **[編輯選取的實體]**。</span><span class="sxs-lookup"><span data-stu-id="2eb03-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="2eb03-117">在 **[編輯實體]** 頁面上：</span><span class="sxs-lookup"><span data-stu-id="2eb03-117">On the **Edit Entity** page:</span></span>  
  
    -   <span data-ttu-id="2eb03-118">如果是分葉成員的屬性，則按一下 **[分葉成員屬性]** 窗格中的 **[加入分葉屬性]**。</span><span class="sxs-lookup"><span data-stu-id="2eb03-118">If the attribute is for leaf members, in the **Leaf member attributes** pane, click **Add leaf attribute**.</span></span>  
  
    -   <span data-ttu-id="2eb03-119">如果是合併成員的屬性，則按一下 **[合併成員屬性]** 窗格中的 **[加入合併屬性]**。</span><span class="sxs-lookup"><span data-stu-id="2eb03-119">If the attribute is for consolidated members, in the **Consolidated member attributes** pane, click **Add consolidated attribute**.</span></span>  
  
    -   <span data-ttu-id="2eb03-120">如果是集合的屬性，則按一下 **[集合屬性]** 窗格中的 **[加入集合屬性]**。</span><span class="sxs-lookup"><span data-stu-id="2eb03-120">If the attribute is for collections, in the **Collection attributes** pane, click **Add collection attribute**.</span></span>  
  
7.  <span data-ttu-id="2eb03-121">在 [**加入屬性**] 頁面上，選取 [檔案 **] 選項。**</span><span class="sxs-lookup"><span data-stu-id="2eb03-121">On the **Add Attribute** page, select the **File** option.</span></span>  
  
8.  <span data-ttu-id="2eb03-122">在 **[名稱]** 方塊中，輸入屬性的名稱。</span><span class="sxs-lookup"><span data-stu-id="2eb03-122">In the **Name** box, type a name for the attribute.</span></span> <span data-ttu-id="2eb03-123">如需不應當做屬性名稱使用的字組清單，請參閱[保留字 &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2eb03-123">For a list of words that should not be used as attribute names, see [Reserved Words &#40;Master Data Services&#41;](../../2014/master-data-services/reserved-words-master-data-services.md).</span></span>  
  
9. <span data-ttu-id="2eb03-124">在 **[顯示像素寬度]** 方塊中，輸入要在 **[總管]** 方格中顯示的屬性資料行寬度。</span><span class="sxs-lookup"><span data-stu-id="2eb03-124">In the **Display pixel width** box, type the width of the attribute column to be displayed in the **Explorer** grid.</span></span>  
  
10. <span data-ttu-id="2eb03-125">從 [**副檔名**] 清單中，選取使用者可上傳的一或多個檔案類型，或保留預設值 ( \*。 \*) 允許所有檔案類型。</span><span class="sxs-lookup"><span data-stu-id="2eb03-125">From the **File extension** list, select one or more file types that a user can upload, or leave the default (\*.\*) to allow all file types.</span></span>  
  
11. <span data-ttu-id="2eb03-126">(選擇性) 選取 **[啟用變更追蹤]** 以追蹤屬性群組的變更。</span><span class="sxs-lookup"><span data-stu-id="2eb03-126">Optionally, select **Enable change tracking** to track changes to groups of attributes.</span></span> <span data-ttu-id="2eb03-127">如需詳細資訊，請參閱[將屬性加入至變更追蹤群組 &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="2eb03-127">For more information, see [Add Attributes to a Change Tracking Group &#40;Master Data Services&#41;](../../2014/master-data-services/add-attributes-to-a-change-tracking-group-master-data-services.md).</span></span>  
  
12. <span data-ttu-id="2eb03-128">按一下 **[儲存屬性]**。</span><span class="sxs-lookup"><span data-stu-id="2eb03-128">Click **Save attribute**.</span></span>  
  
13. <span data-ttu-id="2eb03-129">按一下 **[實體維護]** 頁面上的 **[儲存實體]**。</span><span class="sxs-lookup"><span data-stu-id="2eb03-129">On the **Entity Maintenance** page, click **Save entity**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2eb03-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2eb03-130">See Also</span></span>  
 <span data-ttu-id="2eb03-131">[Master Data Services &#40;的屬性&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2eb03-131">[Attributes &#40;Master Data Services&#41;](../../2014/master-data-services/attributes-master-data-services.md) </span></span>  
 <span data-ttu-id="2eb03-132">[變更屬性名稱 &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2eb03-132">[Change an Attribute Name &#40;Master Data Services&#41;](change-an-attribute-name-and-data-type-master-data-services.md) </span></span>  
 <span data-ttu-id="2eb03-133">[建立以網域為基礎的屬性 &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="2eb03-133">[Create a Domain-Based Attribute &#40;Master Data Services&#41;](../../2014/master-data-services/create-a-domain-based-attribute-master-data-services.md) </span></span>  
 [<span data-ttu-id="2eb03-134">建立文字屬性 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="2eb03-134">Create a Text Attribute &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-a-text-attribute-master-data-services.md)  
  
  
