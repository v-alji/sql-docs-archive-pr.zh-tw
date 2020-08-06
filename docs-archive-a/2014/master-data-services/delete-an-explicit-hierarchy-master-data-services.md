---
title: 刪除明確階層 (Master Data Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
helpviewer_keywords:
- explicit hierarchies, deleting
- deleting explicit hierarchies [Master Data Services]
ms.assetid: 4ce177b0-9884-47a2-9cea-212e845dd762
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 744f96a2705a3abbc2318ecd3c9b0c7fffb7605e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87607436"
---
# <a name="delete-an-explicit-hierarchy-master-data-services"></a><span data-ttu-id="7b0f6-102">刪除明確階層 (Master Data Services)</span><span class="sxs-lookup"><span data-stu-id="7b0f6-102">Delete an Explicit Hierarchy (Master Data Services)</span></span>
  <span data-ttu-id="7b0f6-103">在 [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)]中，刪除不再需要的明確階層。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-103">In [!INCLUDE[ssMDSshort](../includes/ssmdsshort-md.md)], delete an explicit hierarchy when you no longer need it.</span></span>  
  
> [!WARNING]  
>  <span data-ttu-id="7b0f6-104">當您刪除明確階層時，此階層中的所有合併成員也會一併刪除。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-104">When you delete an explicit hierarchy, all consolidated members in the hierarchy are deleted also.</span></span> <span data-ttu-id="7b0f6-105">如果您刪除實體的所有明確階層，則實體的所有集合也會一併刪除，而且將不再針對明確階層和集合啟用該實體。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-105">If you delete all explicit hierarchies for an entity, all collections for the entity are also deleted and the entity is no longer enabled for explicit hierarchies and collections.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7b0f6-106">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="7b0f6-106">Prerequisites</span></span>  
 <span data-ttu-id="7b0f6-107">若要執行此程序：</span><span class="sxs-lookup"><span data-stu-id="7b0f6-107">To perform this procedure:</span></span>  
  
-   <span data-ttu-id="7b0f6-108">您必須擁有存取 **[系統管理]** 功能區域的權限。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-108">You must have permission to access the **System Administration** functional area.</span></span>  
  
-   <span data-ttu-id="7b0f6-109">您必須是模型管理員。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-109">You must be a model administrator.</span></span> <span data-ttu-id="7b0f6-110">如需詳細資訊，請參閱系統[管理員 &#40;Master Data Services&#41;](administrators-master-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-110">For more information, see [Administrators &#40;Master Data Services&#41;](administrators-master-data-services.md).</span></span>  
  
### <a name="to-delete-an-explicit-hierarchy"></a><span data-ttu-id="7b0f6-111">若要刪除明確階層</span><span class="sxs-lookup"><span data-stu-id="7b0f6-111">To delete an explicit hierarchy</span></span>  
  
1.  <span data-ttu-id="7b0f6-112">在 [ [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)]] 中，按一下 **[系統管理]**。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-112">In [!INCLUDE[ssMDSmdm](../includes/ssmdsmdm-md.md)], click **System Administration**.</span></span>  
  
2.  <span data-ttu-id="7b0f6-113">在 **[模型檢視]** 頁面上，從功能表列指向 **[管理]** ，然後按一下 **[實體]**。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-113">On the **Model View** page, from the menu bar, point to **Manage** and click **Entities**.</span></span>  
  
3.  <span data-ttu-id="7b0f6-114">在 **[實體維護]** 頁面上，選取 **[模型]** 清單中的模型。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-114">On the **Entity Maintenance** page, from the **Model** list, select a model.</span></span>  
  
4.  <span data-ttu-id="7b0f6-115">選取實體的資料列，該實體中包含您想要刪除的明確階層。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-115">Select the row for the entity that contains the explicit hierarchy you want to delete.</span></span>  
  
5.  <span data-ttu-id="7b0f6-116">按一下 **[編輯選取的實體]**。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-116">Click **Edit selected entity**.</span></span>  
  
6.  <span data-ttu-id="7b0f6-117">在 [**編輯實體**] 頁面的 [**明確**階層] 窗格中，按一下您想要刪除的明確階層。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-117">On the **Edit Entity** page, in the **Explicit Hierarchies** pane, click the explicit hierarchy you want to delete.</span></span>  
  
7.  <span data-ttu-id="7b0f6-118">按一下 [**刪除選取**的階層]。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-118">Click **Delete selected hierarchy**.</span></span>  
  
8.  <span data-ttu-id="7b0f6-119">在確認對話方塊中按一下 **[確定]**。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-119">In the confirmation dialog box, click **OK**.</span></span>  
  
9. <span data-ttu-id="7b0f6-120">在另一個確認對話方塊中按一下 [確定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7b0f6-120">In the additional confirmation dialog box, click **OK**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b0f6-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b0f6-121">See Also</span></span>  
 <span data-ttu-id="7b0f6-122">[建立明確階層 &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) </span><span class="sxs-lookup"><span data-stu-id="7b0f6-122">[Create an Explicit Hierarchy &#40;Master Data Services&#41;](../../2014/master-data-services/create-an-explicit-hierarchy-master-data-services.md) </span></span>  
 [<span data-ttu-id="7b0f6-123">明確階層 &#40;Master Data Services&#41;</span><span class="sxs-lookup"><span data-stu-id="7b0f6-123">Explicit Hierarchies &#40;Master Data Services&#41;</span></span>](../../2014/master-data-services/explicit-hierarchies-master-data-services.md)  
  
  
