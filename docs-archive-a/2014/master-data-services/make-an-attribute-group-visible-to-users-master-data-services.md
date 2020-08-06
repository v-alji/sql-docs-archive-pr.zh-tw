---
title: 讓使用者看到屬性群組 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: b2f6cc27-dbc9-4f3f-961e-e81e76375248
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 309ad0392cd717d4a8a11470621144ef9e604fd9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87584621"
---
# <a name="make-an-attribute-group-visible-to-users-master-data-services"></a><span data-ttu-id="6dc89-102">讓使用者看到屬性群組 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="6dc89-102">Make an Attribute Group Visible to Users (Master Data Services)</span></span>
  <span data-ttu-id="6dc89-103">當您希望使用者在總管\*\*\*\* 功能區域的方格上方有索引標籤時，可以在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中對使用者或群組顯示屬性群組。</span><span class="sxs-lookup"><span data-stu-id="6dc89-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], make an attribute group visible to users or groups when you want users to have tabs above the grid in the **Explorer** functional area.</span></span>  
  
 <span data-ttu-id="6dc89-104">當您建立屬性群組時，它會自動隱藏起來不讓所有使用者看到，除了建立它的使用者以外。</span><span class="sxs-lookup"><span data-stu-id="6dc89-104">When you create an attribute group, it is automatically hidden from all users except the one who created it.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6dc89-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="6dc89-105">Prerequisites</span></span>  
 <span data-ttu-id="6dc89-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="6dc89-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="6dc89-107">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="6dc89-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="6dc89-108">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="6dc89-108">You must be a model administrator.</span></span> <span data-ttu-id="6dc89-109">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="6dc89-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
-   <span data-ttu-id="6dc89-110">至少有一個屬性群組必須存在。</span><span class="sxs-lookup"><span data-stu-id="6dc89-110">At least one attribute group must exist.</span></span> <span data-ttu-id="6dc89-111">如需詳細資訊，請參閱 [建立屬性群組 &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)(管理員 (Master Data Services))。</span><span class="sxs-lookup"><span data-stu-id="6dc89-111">For more information, see [Create an Attribute Group &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-attribute-group-master-data-services.md).</span></span>  
  
### <a name="to-make-an-attribute-group-visible-to-users"></a><span data-ttu-id="6dc89-112">若要讓使用者看到屬性群組</span><span class="sxs-lookup"><span data-stu-id="6dc89-112">To make an attribute group visible to users</span></span>  
  
1.  <span data-ttu-id="6dc89-113">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="6dc89-113">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="6dc89-114">在 [**模型視圖**] 頁面上，從功能表列指向 [**管理**]，然後按一下 [**屬性群組**]。</span><span class="sxs-lookup"><span data-stu-id="6dc89-114">On the **Model View** page, from the menu bar, point to **Manage** and click **Attribute Groups**.</span></span>  
  
3.  <span data-ttu-id="6dc89-115">從 **[模型]** 清單中選取模型。</span><span class="sxs-lookup"><span data-stu-id="6dc89-115">From the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="6dc89-116">從 [實體]\*\*\*\* 清單中選取實體。</span><span class="sxs-lookup"><span data-stu-id="6dc89-116">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="6dc89-117">按一下加號展開 [分**葉群組**]、 **[合併群組**] 或 [**集合群組**]，視您想要顯示的群組類型而定。</span><span class="sxs-lookup"><span data-stu-id="6dc89-117">Click the plus sign to expand **Leaf Groups**, **Consolidated Groups**, or **Collection Groups**, depending on the type of group you want to make visible.</span></span>  
  
6.  <span data-ttu-id="6dc89-118">按一下加號展開要顯示的群組。</span><span class="sxs-lookup"><span data-stu-id="6dc89-118">Click the plus sign to expand the group you want to make visible.</span></span>  
  
7.  <span data-ttu-id="6dc89-119">按一下 [**使用者**] 或 [**群組**]，視您是否要讓使用者或群組看見群組而定。</span><span class="sxs-lookup"><span data-stu-id="6dc89-119">Click either **Users** or **Groups**, depending on whether you are making the group visible to a user or a group.</span></span>  
  
8.  <span data-ttu-id="6dc89-120">按一下 [**編輯選取的專案**]。</span><span class="sxs-lookup"><span data-stu-id="6dc89-120">Click **Edit selected item**.</span></span>  
  
9. <span data-ttu-id="6dc89-121">按一下 [**可用**] 方塊中的 [使用者或群組]，然後按一下 [**新增**] 箭號。</span><span class="sxs-lookup"><span data-stu-id="6dc89-121">Click users or groups in the **Available** box and click the **Add** arrow.</span></span> <span data-ttu-id="6dc89-122">若要全部加入，請按一下 [全部加入]\*\*\*\* 箭號。</span><span class="sxs-lookup"><span data-stu-id="6dc89-122">To add all, click the **Add All** arrow.</span></span>  
  
10. <span data-ttu-id="6dc89-123">按一下 [檔案] 。</span><span class="sxs-lookup"><span data-stu-id="6dc89-123">Click **Save**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6dc89-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6dc89-124">See Also</span></span>  
 <span data-ttu-id="6dc89-125">[屬性群組 &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="6dc89-125">[Attribute Groups &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span></span>  
 [<span data-ttu-id="6dc89-126">建立屬性群組 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="6dc89-126">Create an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)  
  
  
