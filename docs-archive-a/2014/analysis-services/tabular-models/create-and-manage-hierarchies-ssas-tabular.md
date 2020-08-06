---
title: 建立和管理 (SSAS 表格式) 的階層 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 8dd30cd0-a831-4d25-b577-648d7f3c7fa6
author: minewiskan
ms.author: owend
ms.openlocfilehash: 0bab3e09aadb4e0c857b9c1da3111e03e90f777e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594214"
---
# <a name="create-and-manage-hierarchies-ssas-tabular"></a><span data-ttu-id="fee73-102">建立及管理階層 (SSAS 表格式)</span><span class="sxs-lookup"><span data-stu-id="fee73-102">Create and Manage Hierarchies (SSAS Tabular)</span></span>
  <span data-ttu-id="fee73-103">您可以在 [圖表檢視] 中，透過模型設計師建立及管理階層。</span><span class="sxs-lookup"><span data-stu-id="fee73-103">Hierarchies can be created and managed in the model designer, in Diagram View.</span></span> <span data-ttu-id="fee73-104">若要在 [圖表檢視] 中檢視模型設計師，請按一下 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 中的 [模型]\*\*\*\* 功能表，然後指向 [模型檢視]\*\*\*\*，再按一下 [圖表檢視]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fee73-104">To view the model designer in Diagram View, in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], click the **Model** menu, then point to **Model View**, and then click **Diagram View**.</span></span>  
  
 <span data-ttu-id="fee73-105">本主題也包括下列工作：</span><span class="sxs-lookup"><span data-stu-id="fee73-105">This topic includes the following tasks:</span></span>  
  
-   [<span data-ttu-id="fee73-106">建立階層</span><span class="sxs-lookup"><span data-stu-id="fee73-106">Create a Hierarchy</span></span>](#bkmk_create)  
  
-   [<span data-ttu-id="fee73-107">編輯階層</span><span class="sxs-lookup"><span data-stu-id="fee73-107">Edit a Hierarchy</span></span>](#bkmk_edit)  
  
-   [<span data-ttu-id="fee73-108">刪除階層</span><span class="sxs-lookup"><span data-stu-id="fee73-108">Delete a Hierarchy</span></span>](#bkmk_delete)  
  
##  <a name="create-a-hierarchy"></a><a name="bkmk_create"></a> <span data-ttu-id="fee73-109">建立階層</span><span class="sxs-lookup"><span data-stu-id="fee73-109">Create a Hierarchy</span></span>  
 <span data-ttu-id="fee73-110">您可以使用資料行和資料表內容功能表建立階層。</span><span class="sxs-lookup"><span data-stu-id="fee73-110">You can create a hierarchy by using the columns and table context menu.</span></span> <span data-ttu-id="fee73-111">當您建立階層時會顯示新的父層級，而所選的資料行則做為子層級。</span><span class="sxs-lookup"><span data-stu-id="fee73-111">When you create a hierarchy, a new parent level displays with selected columns as child levels.</span></span>  
  
#### <a name="to-create-a-hierarchy-from-the-context-menu"></a><span data-ttu-id="fee73-112">從內容功能表建立階層</span><span class="sxs-lookup"><span data-stu-id="fee73-112">To create a hierarchy from the context menu</span></span>  
  
1.  <span data-ttu-id="fee73-113">在模型設計師 ([圖表檢視]) 的資料表視窗中，以滑鼠右鍵按一下資料行，然後按一下 [建立階層]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fee73-113">In the model designer (Diagram View), in a table window, right-click on a column, and then click **Create Hierarchy**.</span></span>  
  
     <span data-ttu-id="fee73-114">若要選取多個資料行，請按一下每個資料行，然後按一下滑鼠右鍵開啟內容功能表，再按一下 [建立階層]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fee73-114">To select multiple columns, click each column, then right-click to open the context menu, and then click **Create Hierarchy**.</span></span>  
  
     <span data-ttu-id="fee73-115">資料表視窗底部會建立父階層層級，並將所選的資料行複製到階層下做為子層級。</span><span class="sxs-lookup"><span data-stu-id="fee73-115">A parent hierarchy level is created at the bottom of the table window and the selected columns are copied under the hierarchy as child levels.</span></span>  
  
2.  <span data-ttu-id="fee73-116">輸入階層的名稱。</span><span class="sxs-lookup"><span data-stu-id="fee73-116">Type a name for the hierarchy.</span></span>  
  
 <span data-ttu-id="fee73-117">您可以將其他資料行拖曳至階層的父層級，這會複製資料行。</span><span class="sxs-lookup"><span data-stu-id="fee73-117">You can drag additional columns into your hierarchy's parent level, which copies the columns.</span></span> <span data-ttu-id="fee73-118">將子層級置於階層中要顯示的位置。</span><span class="sxs-lookup"><span data-stu-id="fee73-118">Drop the child level to place it where you want it to appear in the hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fee73-119">如果您複選量值及一個或多個資料行，或者選取多個資料表的資料行，即會停用內容功能表中的 [建立階層] 命令。</span><span class="sxs-lookup"><span data-stu-id="fee73-119">The Create Hierarchy command is disabled in the context menu if you multi-select a measure along with one or more columns or you select columns from multiple tables.</span></span>  
  
##  <a name="edit-a-hierarchy"></a><a name="bkmk_edit"></a><span data-ttu-id="fee73-120">編輯階層</span><span class="sxs-lookup"><span data-stu-id="fee73-120">Edit a Hierarchy</span></span>  
 <span data-ttu-id="fee73-121">您可以重新命名階層、重新命名子層級、變更子層級順序、加入其他資料行做為子層級、從階層移除子層級、顯示子層級的來源名稱 (資料行名稱)，以及隱藏子層級 (如果它與階層父層級同名)。</span><span class="sxs-lookup"><span data-stu-id="fee73-121">You can rename a hierarchy, rename a child level, change the order of the child levels, add additional columns as child levels, remove a child level from a hierarchy, show the source name of a child level (the column name), and hide a child level if it has the same name as the hierarchy parent level.</span></span>  
  
#### <a name="to-change-the-name-of-a-hierarchy-or-child-level"></a><span data-ttu-id="fee73-122">若要變更階層或子層級的名稱</span><span class="sxs-lookup"><span data-stu-id="fee73-122">To change the name of a hierarchy or child level</span></span>  
  
1.  <span data-ttu-id="fee73-123">以滑鼠右鍵按一下階層父層級或子層級，然後按一下 [重新命名]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fee73-123">Right-click the hierarchy parent level or a child level, and the click **Rename**.</span></span>  
  
2.  <span data-ttu-id="fee73-124">輸入新的名稱或編輯現有的名稱。</span><span class="sxs-lookup"><span data-stu-id="fee73-124">Type a new name or edit the existing name.</span></span>  
  
#### <a name="to-change-the-order-of-a-child-level-in-a-hierarchy"></a><span data-ttu-id="fee73-125">變更階層中子層級的順序</span><span class="sxs-lookup"><span data-stu-id="fee73-125">To change the order of a child level in a hierarchy</span></span>  
  
-   <span data-ttu-id="fee73-126">按一下子層級並將其拖曳至階層中的新位置。</span><span class="sxs-lookup"><span data-stu-id="fee73-126">Click and drag a child level into a new position in the hierarchy.</span></span>  
  
-   <span data-ttu-id="fee73-127">或按兩下階層的子層級，然後按一下 [上移]，將層級在清單中上移，或按一下 [下移]，將層級在清單中下移。</span><span class="sxs-lookup"><span data-stu-id="fee73-127">Or, right-click a child level of the hierarchy, and then click Move Up to move the level up in the list, or click Move Down to move the level down in the list.</span></span>  
  
-   <span data-ttu-id="fee73-128">或按一下子層級予以選取，然後按 Alt + 向上鍵將層級在清單中上移，或按 Alt + 向下鍵將層級在清單中下移。</span><span class="sxs-lookup"><span data-stu-id="fee73-128">Or, click a child level to select it, and then press Alt + Up Arrow to move the level up, or press Alt+Down Arrow to move the level down in the list.</span></span>  
  
#### <a name="to-add-another-child-level-to-a-hierarchy"></a><span data-ttu-id="fee73-129">將另一個子層級加入至階層</span><span class="sxs-lookup"><span data-stu-id="fee73-129">To add another child level to a hierarchy</span></span>  
  
-   <span data-ttu-id="fee73-130">按一下並將資料行拖曳至父層級或階層的特定位置。</span><span class="sxs-lookup"><span data-stu-id="fee73-130">Click and drag a column onto the parent level or into a specific location of the hierarchy.</span></span> <span data-ttu-id="fee73-131">資料行會複製為階層的子層級。</span><span class="sxs-lookup"><span data-stu-id="fee73-131">The column is copied as a child level of the hierarchy.</span></span>  
  
-   <span data-ttu-id="fee73-132">或以滑鼠右鍵按一下資料行，然後指向 [加入至階層]\*\*\*\*，再按一下階層。</span><span class="sxs-lookup"><span data-stu-id="fee73-132">Or, right-click a column, point to **Add to Hierarchy**, and then click the hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fee73-133">您可以加入隱藏的資料行 (報表中不顯示的資料行) 做為階層中的子層級。</span><span class="sxs-lookup"><span data-stu-id="fee73-133">You can add a hidden column (a column that is hidden from reports) as a child level to the hierarchy.</span></span> <span data-ttu-id="fee73-134">子層級不是隱藏的。</span><span class="sxs-lookup"><span data-stu-id="fee73-134">The child level is not hidden.</span></span>  
  
#### <a name="to-remove-a-child-level-from-a-hierarchy"></a><span data-ttu-id="fee73-135">若要從階層中移除子層級</span><span class="sxs-lookup"><span data-stu-id="fee73-135">To remove a child level from a hierarchy</span></span>  
  
-   <span data-ttu-id="fee73-136">以滑鼠右鍵按一下子層級，然後按一下 [從階層移除]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fee73-136">Right-click a child level, and then click **Remove from Hierarchy**.</span></span>  
  
-   <span data-ttu-id="fee73-137">或按一下子層級，然後按 **Delete**鍵。</span><span class="sxs-lookup"><span data-stu-id="fee73-137">Or, click a child level, and then press **Delete**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="fee73-138">如果重新命名階層子層級，則不會再與其複製來源資料行共用相同名稱。</span><span class="sxs-lookup"><span data-stu-id="fee73-138">If you rename a hierarchy child level, it no longer shares the same name as the column that it is copied from.</span></span> <span data-ttu-id="fee73-139">使用 [顯示來源名稱]\*\*\*\* 命令查看其複製來源資料行。</span><span class="sxs-lookup"><span data-stu-id="fee73-139">Use the **Show Source Name** command to see which column it was copied from.</span></span>  
  
#### <a name="to-show-a-source-name"></a><span data-ttu-id="fee73-140">顯示來源名稱</span><span class="sxs-lookup"><span data-stu-id="fee73-140">To show a source name</span></span>  
  
-   <span data-ttu-id="fee73-141">以滑鼠右鍵按一下階層子層級，然後按一下 [顯示來源名稱]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="fee73-141">Right-click a hierarchy child level, and then click **Show Source Name**.</span></span> <span data-ttu-id="fee73-142">即會顯示其複製來源資料行的名稱。</span><span class="sxs-lookup"><span data-stu-id="fee73-142">The name of the column that it was copied from appears.</span></span>  
  
##  <a name="delete-a-hierarchy"></a><a name="bkmk_delete"></a><span data-ttu-id="fee73-143">刪除階層</span><span class="sxs-lookup"><span data-stu-id="fee73-143">Delete a Hierarchy</span></span>  
  
#### <a name="to-delete-a-hierarchy-and-remove-its-child-levels"></a><span data-ttu-id="fee73-144">刪除階層及移除其子層級</span><span class="sxs-lookup"><span data-stu-id="fee73-144">To delete a hierarchy and remove its child levels</span></span>  
  
-   <span data-ttu-id="fee73-145">以滑鼠右鍵按一下父階層層級，然後按一下 [刪除階層]。</span><span class="sxs-lookup"><span data-stu-id="fee73-145">Right-click the parent hierarchy level, and then click Delete Hierarchy.</span></span>  
  
-   <span data-ttu-id="fee73-146">或按一下父階層層級，然後按 Delete。</span><span class="sxs-lookup"><span data-stu-id="fee73-146">Or, click the parent hierarchy level, and then press Delete.</span></span> <span data-ttu-id="fee73-147">這也會移除所有子層級。</span><span class="sxs-lookup"><span data-stu-id="fee73-147">This also removes all the child levels.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fee73-148">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fee73-148">See Also</span></span>  
 <span data-ttu-id="fee73-149">[表格式模型設計師 &#40;SSAS 表格式&#41;](../tabular-model-designer-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="fee73-149">[Tabular Model Designer &#40;SSAS Tabular&#41;](../tabular-model-designer-ssas-tabular.md) </span></span>  
 <span data-ttu-id="fee73-150">[SSAS 表格式&#41;的階層 &#40;](hierarchies-ssas-tabular.md) </span><span class="sxs-lookup"><span data-stu-id="fee73-150">[Hierarchies &#40;SSAS Tabular&#41;](hierarchies-ssas-tabular.md) </span></span>  
 [<span data-ttu-id="fee73-151">量值 &#40;SSAS 表格式&#41;</span><span class="sxs-lookup"><span data-stu-id="fee73-151">Measures &#40;SSAS Tabular&#41;</span></span>](measures-ssas-tabular.md)  
  
  
