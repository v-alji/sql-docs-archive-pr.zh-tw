---
title: 刪除屬性群組 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- deleting attribute groups [Master Data Services]
- attribute groups [Master Data Services], deleting
ms.assetid: f915e89b-629d-4725-aea6-a7f051978244
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 833c5cf327034b25d68af123a1fc134372bd6f10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87606388"
---
# <a name="delete-an-attribute-group-master-data-services"></a><span data-ttu-id="443f0-102">刪除屬性群組 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="443f0-102">Delete an Attribute Group (Master Data Services)</span></span>
  <span data-ttu-id="443f0-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)] 中，如果 [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)] 的 [總管]\*\*\*\* 功能區域已不再需要顯示某個索引標籤時，您即可刪除該屬性群組。</span><span class="sxs-lookup"><span data-stu-id="443f0-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete an attribute group when you no longer need the tab to display in the **Explorer** functional area of [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)].</span></span>  
  
-   <span data-ttu-id="443f0-104">**注意**：當屬性群組存在時，[總管]\*\*\*\* 只會顯示屬於該屬性群組的屬性。</span><span class="sxs-lookup"><span data-stu-id="443f0-104">**Note** When attribute groups exist, attributes that do not belong to an attribute group are not displayed in **Explorer**.</span></span> <span data-ttu-id="443f0-105">當屬性群組不存在時，則會顯示所有屬性。</span><span class="sxs-lookup"><span data-stu-id="443f0-105">When no attribute groups exist, all attributes are displayed.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="443f0-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="443f0-106">Prerequisites</span></span>  
 <span data-ttu-id="443f0-107">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="443f0-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="443f0-108">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="443f0-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="443f0-109">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="443f0-109">You must be a model administrator.</span></span> <span data-ttu-id="443f0-110">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="443f0-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-an-attribute-group"></a><span data-ttu-id="443f0-111">若要刪除屬性群組</span><span class="sxs-lookup"><span data-stu-id="443f0-111">To delete an attribute group</span></span>  
  
1.  <span data-ttu-id="443f0-112">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="443f0-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="443f0-113">在 [**模型視圖**] 頁面上，從功能表列指向 [**管理**]，然後按一下 [**屬性群組**]。</span><span class="sxs-lookup"><span data-stu-id="443f0-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Attribute Groups**.</span></span>  
  
3.  <span data-ttu-id="443f0-114">從 **[模型]** 清單中選取模型。</span><span class="sxs-lookup"><span data-stu-id="443f0-114">From the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="443f0-115">從 [實體]\*\*\*\* 清單中選取實體。</span><span class="sxs-lookup"><span data-stu-id="443f0-115">From the **Entity** list, select an entity.</span></span>  
  
5.  <span data-ttu-id="443f0-116">按一下加號展開 [分**葉群組**]、 **[合併群組**] 或 [**集合群組**]，視您想要刪除的群組類型而定。</span><span class="sxs-lookup"><span data-stu-id="443f0-116">Click the plus sign to expand **Leaf Groups**, **Consolidated Groups**, or **Collection Groups**, depending on the type of group you want to delete.</span></span>  
  
6.  <span data-ttu-id="443f0-117">按一下您要刪除的屬性群組。</span><span class="sxs-lookup"><span data-stu-id="443f0-117">Click the attribute group you want to delete.</span></span>  
  
7.  <span data-ttu-id="443f0-118">按一下 [**刪除選取的群組**]。</span><span class="sxs-lookup"><span data-stu-id="443f0-118">Click **Delete selected group**.</span></span>  
  
8.  <span data-ttu-id="443f0-119">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="443f0-119">In the confirmation dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="443f0-120">在另一個確認對話方塊中按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="443f0-120">In the additional confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="443f0-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="443f0-121">See Also</span></span>  
 <span data-ttu-id="443f0-122">[屬性群組 &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="443f0-122">[Attribute Groups &#40;Master Data Services&#41;](../../2014/master-data-services/attribute-groups-master-data-services.md) </span></span>  
 [<span data-ttu-id="443f0-123">建立屬性群組 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="443f0-123">Create an Attribute Group &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/create-an-attribute-group-master-data-services.md)  
  
  
