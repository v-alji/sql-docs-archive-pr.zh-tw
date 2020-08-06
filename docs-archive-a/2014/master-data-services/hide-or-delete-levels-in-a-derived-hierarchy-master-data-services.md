---
title: 隱藏或刪除衍生階層中的層級 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- derived hierarchies, hiding levels
- derived hierarchies, deleting levels
ms.assetid: e00582b9-9415-4b66-b4a7-9f590d83875f
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 039b05633bcd1fdc69d226e565b3dc5211e9734f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597185"
---
# <a name="hide-or-delete-levels-in-a-derived-hierarchy-master-data-services"></a><span data-ttu-id="775ac-102">隱藏或刪除衍生階層中的層級 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="775ac-102">Hide or Delete Levels in a Derived Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="775ac-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，當您要求群組的層級但是不需要顯示該層級時，請在衍生階層中隱藏該層級。</span><span class="sxs-lookup"><span data-stu-id="775ac-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], hide a level in a derived hierarchy when you require the level for grouping but you do not need to show the level.</span></span> <span data-ttu-id="775ac-104">當您不想要使用層級來群組時，請將它刪除。</span><span class="sxs-lookup"><span data-stu-id="775ac-104">Delete a level when you do not want to use it for grouping.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="775ac-105">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="775ac-105">Prerequisites</span></span>  
 <span data-ttu-id="775ac-106">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="775ac-106">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="775ac-107">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="775ac-107">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="775ac-108">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="775ac-108">You must be a model administrator.</span></span> <span data-ttu-id="775ac-109">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="775ac-109">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-hide-or-delete-levels-in-a-derived-hierarchy"></a><span data-ttu-id="775ac-110">若要隱藏或刪除衍生階層中的層級</span><span class="sxs-lookup"><span data-stu-id="775ac-110">To hide or delete levels in a derived hierarchy</span></span>  
  
1.  <span data-ttu-id="775ac-111">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="775ac-111">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="775ac-112">在 [**模型視圖**] 頁面上，從功能表列指向 [**管理**]，然後按一下 [**衍生**階層]。</span><span class="sxs-lookup"><span data-stu-id="775ac-112">On the **Model View** page, from the menu bar, point to **Manage** and click **Derived Hierarchies**.</span></span>  
  
3.  <span data-ttu-id="775ac-113">在 [衍生階層維護]\*\*\*\* 頁面上，選取 [模型]\*\*\*\* 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="775ac-113">On the **Derived Hierarchy Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="775ac-114">選取要編輯之衍生階層的資料列。</span><span class="sxs-lookup"><span data-stu-id="775ac-114">Select the row for the derived hierarchy you want to edit.</span></span>  
  
5.  <span data-ttu-id="775ac-115">按一下 [**編輯選取的衍生**階層]。</span><span class="sxs-lookup"><span data-stu-id="775ac-115">Click **Edit selected derived hierarchy**.</span></span>  
  
6.  <span data-ttu-id="775ac-116">在 [目前層級]\*\*\*\* 窗格中：</span><span class="sxs-lookup"><span data-stu-id="775ac-116">In the **Current Levels** pane:</span></span>  
  
    -   <span data-ttu-id="775ac-117">若要隱藏層級，請按一下頂端或底端以外的層級。</span><span class="sxs-lookup"><span data-stu-id="775ac-117">To hide a level, click a level other than the top or bottom.</span></span> <span data-ttu-id="775ac-118">從 [可見]\*\*\*\* 清單中，選取 [否]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="775ac-118">From the **Visible** list, select **No**.</span></span> <span data-ttu-id="775ac-119">然後按一下 [儲存選取的階層項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="775ac-119">Then click **Save selected hierarchy item**.</span></span>  
  
    -   <span data-ttu-id="775ac-120">若要刪除最上層，請按一下 [刪除選取的階層項目]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="775ac-120">To delete the top level, click **Delete selected hierarchy item**.</span></span> <span data-ttu-id="775ac-121">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="775ac-121">In the confirmation dialog box, click **OK**.</span></span> <span data-ttu-id="775ac-122">您可以只刪除最上層。</span><span class="sxs-lookup"><span data-stu-id="775ac-122">You can delete the top level only.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="775ac-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="775ac-123">See Also</span></span>  
 <span data-ttu-id="775ac-124">[在階層中移動成員 &#40;Master Data Services&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="775ac-124">[Move Members within a Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/move-members-within-a-hierarchy-master-data-services.md) </span></span>  
 [<span data-ttu-id="775ac-125">衍生階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="775ac-125">Derived Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/derived-hierarchies-master-data-services.md)  
  
  
