---
title: 屬性關聯性圖表 (屬性關聯性設計工具索引標籤、維度設計師)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.ardesigner.ardiagram.f1
ms.assetid: 320989ad-bd95-43f4-a2e7-b262d66dbda7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 49be94564a52a6347c35f28f9a1dd659980fd46c
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593167"
---
# <a name="attribute-relationship-diagram-attribute-relationship-designer-tab-dimension-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="d3e21-102">屬性關聯性圖表 (屬性關聯性設計師索引標籤，維度設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="d3e21-102">Attribute Relationship Diagram (Attribute Relationship Designer Tab, Dimension Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="d3e21-103">在 **[屬性關聯性]** 索引標籤上，使用緊鄰在工具列底下的窗格，即可檢視屬性關聯性圖表，以及建立、修改或刪除屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="d3e21-103">Use the pane immediately under the toolbar on the **Attribute Relationships** tab to view the attribute relationship diagram, and to create, modify, and delete attribute relationships.</span></span>  
  
 <span data-ttu-id="d3e21-104">**檢視包含屬性關聯圖表的窗格**</span><span class="sxs-lookup"><span data-stu-id="d3e21-104">**To view the pane that contains the attribute relationship diagram**</span></span>  
  
-   <span data-ttu-id="d3e21-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 的方案總管中，按兩下維度即可開啟 [維度設計師]，然後按一下 [屬性關聯性]\*\*\*\* 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="d3e21-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], in Solution Explorer, double-click a dimension to open the Dimension Designer, and then click the **Attribute Relationship** tab.</span></span>  
  
## <a name="using-the-attribute-relationship-diagram"></a><span data-ttu-id="d3e21-106">使用屬性關聯性圖表</span><span class="sxs-lookup"><span data-stu-id="d3e21-106">Using the Attribute Relationship Diagram</span></span>  
 <span data-ttu-id="d3e21-107">使用屬性關聯性圖表，即可建立、編輯或刪除屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="d3e21-107">Use the attribute relationship diagram to create, edit or delete attribute relationships.</span></span> <span data-ttu-id="d3e21-108">此外，屬性關聯性圖表也會反白顯示有問題的屬性關聯性並於工具提示中顯示問題的描述。</span><span class="sxs-lookup"><span data-stu-id="d3e21-108">The attribute relationship diagram will also highlight problematic attribute relationships and display a description of the issue in a tooltip.</span></span>  
  
 <span data-ttu-id="d3e21-109">此圖表會提供三個個別的快速鍵功能表：圖表快速鍵功能表、屬性快速鍵功能表和關聯性快速鍵功能表。</span><span class="sxs-lookup"><span data-stu-id="d3e21-109">There are three separate shortcut menus available in the diagram: the diagram shortcut menu, the attribute shortcut menu, and the relationship shortcut menu.</span></span>  
  
### <a name="diagram-shortcut-menu"></a><span data-ttu-id="d3e21-110">圖表快速鍵功能表</span><span class="sxs-lookup"><span data-stu-id="d3e21-110">Diagram Shortcut Menu</span></span>  
 <span data-ttu-id="d3e21-111">若要開啟屬性關聯性圖表的快速鍵功能表，請以滑鼠右鍵按一下圖表的背景。</span><span class="sxs-lookup"><span data-stu-id="d3e21-111">To open the shortcut menu for the attribute relationship diagram, right-click the background of the diagram.</span></span> <span data-ttu-id="d3e21-112">圖表快速鍵功能表有下列命令：</span><span class="sxs-lookup"><span data-stu-id="d3e21-112">The diagram shortcut menu has the following commands:</span></span>  
  
 <span data-ttu-id="d3e21-113">**新增屬性關聯性**</span><span class="sxs-lookup"><span data-stu-id="d3e21-113">**New Attribute Relationship**</span></span>  
 <span data-ttu-id="d3e21-114">開啟 [建立屬性關聯性]\*\*\*\* 對話方塊，而且您可以在其中定義新的屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="d3e21-114">Opens the **Create Attribute Relationship** dialog box in which you can define a new attribute relationship.</span></span>  
  
 <span data-ttu-id="d3e21-115">如需詳細資訊，請參閱[建立屬性關聯性和編輯屬性關聯性對話方塊 &#40;屬性關聯性設計師索引標籤，維度設計師&#41; &#40;Analysis Services - 多維度資料&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) 和[定義屬性關聯性](multidimensional-models/attribute-relationships-define.md)。</span><span class="sxs-lookup"><span data-stu-id="d3e21-115">For more information, see [Create Attribute Relationship and Edit Attribute Relationship Dialog Boxes &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) and [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md).</span></span>  
  
 <span data-ttu-id="d3e21-116">**排列形狀**</span><span class="sxs-lookup"><span data-stu-id="d3e21-116">**Arrange Shapes**</span></span>  
 <span data-ttu-id="d3e21-117">根據 [維度設計師] 所使用的配置演算法，排列形狀。</span><span class="sxs-lookup"><span data-stu-id="d3e21-117">Arranges the shapes according to the layout algorithm that Dimension Designer uses.</span></span>  
  
 <span data-ttu-id="d3e21-118">**自動排列形狀**</span><span class="sxs-lookup"><span data-stu-id="d3e21-118">**Auto Arrange Shapes**</span></span>  
 <span data-ttu-id="d3e21-119">根據 [維度設計師] 所使用的配置演算法，自動排列圖表中的形狀。</span><span class="sxs-lookup"><span data-stu-id="d3e21-119">Automatically arranges the shapes in the diagram according to the layout algorithm that Dimension Designer uses.</span></span> <span data-ttu-id="d3e21-120">根據預設， **[自動排列形狀]** 是啟用狀態。</span><span class="sxs-lookup"><span data-stu-id="d3e21-120">By default, **Auto Arrange Shapes** is enabled.</span></span>  
  
 <span data-ttu-id="d3e21-121">**顯示清單檢視**</span><span class="sxs-lookup"><span data-stu-id="d3e21-121">**Show List Views**</span></span>  
 <span data-ttu-id="d3e21-122">顯示或隱藏 [屬性]\*\*\*\* 和 [屬性關聯性]\*\*\*\* 清單。</span><span class="sxs-lookup"><span data-stu-id="d3e21-122">Displays or hides the **Attributes** and **Attribute Relationships** lists.</span></span> <span data-ttu-id="d3e21-123">這些清單顯示於自己的窗格中，而這些窗格緊鄰在包含屬性關聯性圖表的窗格底下。</span><span class="sxs-lookup"><span data-stu-id="d3e21-123">These lists appear in their own panes immediately under the pane that contains the attribute relationship diagram.</span></span>  
  
 <span data-ttu-id="d3e21-124">**展開所有形狀**</span><span class="sxs-lookup"><span data-stu-id="d3e21-124">**Expand All Shapes**</span></span>  
 <span data-ttu-id="d3e21-125">顯示與最上層屬性相關聯的群組屬性。</span><span class="sxs-lookup"><span data-stu-id="d3e21-125">Displays the grouped attributes that are associated with the top-level attributes.</span></span> <span data-ttu-id="d3e21-126">只有在您展開屬性關聯性圖表中的形狀時，才會顯示群組屬性。</span><span class="sxs-lookup"><span data-stu-id="d3e21-126">Grouped attributes are only visible when the shapes in the attribute relationship diagram are expanded.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3e21-127">如果您按一下這個選項，[維度設計師] 就會讓屬性關聯性圖表中的形狀返回設計師所使用的預設配置。</span><span class="sxs-lookup"><span data-stu-id="d3e21-127">If you click this option, the Dimension Designer will return the shapes in the attribute relationship diagram back to the default layout that the designer uses.</span></span>  
  
 <span data-ttu-id="d3e21-128">**摺疊所有形狀**</span><span class="sxs-lookup"><span data-stu-id="d3e21-128">**Collapse All Shapes**</span></span>  
 <span data-ttu-id="d3e21-129">隱藏與最上層屬性相關聯的群組屬性。</span><span class="sxs-lookup"><span data-stu-id="d3e21-129">Hides the grouped attributes that are associated with the top-level attributes.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="d3e21-130">如果您按一下這個選項，[維度設計師] 就會讓屬性關聯性圖表中的形狀返回設計師所使用的預設配置。</span><span class="sxs-lookup"><span data-stu-id="d3e21-130">If you click this option, the Dimension Designer will return the shapes in the attribute relationship diagram back to the default layout that the designer uses.</span></span>  
  
 <span data-ttu-id="d3e21-131">**縮放**</span><span class="sxs-lookup"><span data-stu-id="d3e21-131">**Zoom**</span></span>  
 <span data-ttu-id="d3e21-132">顯示可用顯示比例選項的清單。</span><span class="sxs-lookup"><span data-stu-id="d3e21-132">Displays a list of available zoom options.</span></span>  
  
### <a name="attribute-shortcut-menu"></a><span data-ttu-id="d3e21-133">屬性快速鍵功能表</span><span class="sxs-lookup"><span data-stu-id="d3e21-133">Attribute Shortcut Menu</span></span>  
 <span data-ttu-id="d3e21-134">若要開啟屬性快速鍵功能表，請以滑鼠右鍵按一下屬性關聯性圖表中的屬性。</span><span class="sxs-lookup"><span data-stu-id="d3e21-134">To open the attribute shortcut menu, right-click an attribute in the attribute relationship diagram.</span></span> <span data-ttu-id="d3e21-135">屬性快速鍵功能表有下列命令：</span><span class="sxs-lookup"><span data-stu-id="d3e21-135">The attribute shortcut menu has the following commands:</span></span>  
  
 <span data-ttu-id="d3e21-136">**新增屬性關聯性**</span><span class="sxs-lookup"><span data-stu-id="d3e21-136">**New Attribute Relationship**</span></span>  
 <span data-ttu-id="d3e21-137">開啟 [建立屬性關聯性]\*\*\*\* 對話方塊，而且您可以在其中定義新的屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="d3e21-137">Opens the **Create Attribute Relationship** dialog box in which you can define a new attribute relationship.</span></span>  
  
 <span data-ttu-id="d3e21-138">如需詳細資訊，請參閱[建立屬性關聯性和編輯屬性關聯性對話方塊 &#40;屬性關聯性設計師索引標籤，維度設計師&#41; &#40;Analysis Services - 多維度資料&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) 和[定義屬性關聯性](multidimensional-models/attribute-relationships-define.md)。</span><span class="sxs-lookup"><span data-stu-id="d3e21-138">For more information, see [Create Attribute Relationship and Edit Attribute Relationship Dialog Boxes &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) and [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md).</span></span>  
  
 <span data-ttu-id="d3e21-139">**屬性**</span><span class="sxs-lookup"><span data-stu-id="d3e21-139">**Properties**</span></span>  
 <span data-ttu-id="d3e21-140">在 [屬性]\*\*\*\* 視窗中顯示屬性 (Attribute) 的屬性 (Property)。</span><span class="sxs-lookup"><span data-stu-id="d3e21-140">Displays the attribute's properties in the **Properties** window.</span></span>  
  
### <a name="relationship-shortcut-menu"></a><span data-ttu-id="d3e21-141">關聯性快速鍵功能表</span><span class="sxs-lookup"><span data-stu-id="d3e21-141">Relationship Shortcut Menu</span></span>  
 <span data-ttu-id="d3e21-142">若要開啟關聯性快速鍵功能表，請以滑鼠右鍵按一下在兩種屬性之間識別關聯性的箭號。</span><span class="sxs-lookup"><span data-stu-id="d3e21-142">To open the relationship shortcut menu, right-click the arrow that identifies the relationship between two attributes.</span></span> <span data-ttu-id="d3e21-143">關聯性快速鍵功能表有下列命令：</span><span class="sxs-lookup"><span data-stu-id="d3e21-143">The relationship shortcut menu has the following commands:</span></span>  
  
 <span data-ttu-id="d3e21-144">**編輯屬性關聯性**</span><span class="sxs-lookup"><span data-stu-id="d3e21-144">**Edit Attribute Relationship**</span></span>  
 <span data-ttu-id="d3e21-145">開啟 [編輯屬性關聯性]\*\*\*\* 對話方塊，而且您可以在其中修改屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="d3e21-145">Opens the **Edit Attribute Relationship** dialog box in which you can modify the attribute relationship.</span></span>  
  
 <span data-ttu-id="d3e21-146">如需詳細資訊，請參閱[建立屬性關聯性和編輯屬性關聯性對話方塊 &#40;屬性關聯性設計師索引標籤，維度設計師&#41; &#40;Analysis Services - 多維度資料&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) 和[定義屬性關聯性](multidimensional-models/attribute-relationships-define.md)。</span><span class="sxs-lookup"><span data-stu-id="d3e21-146">For more information, see [Create Attribute Relationship and Edit Attribute Relationship Dialog Boxes &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](create-edit-attribute-relationships-dialog-boxes-analysis-services-multidimensional-data.md) and [Define Attribute Relationships](multidimensional-models/attribute-relationships-define.md).</span></span>  
  
 <span data-ttu-id="d3e21-147">**關聯性類型**</span><span class="sxs-lookup"><span data-stu-id="d3e21-147">**Relationship Type**</span></span>  
 <span data-ttu-id="d3e21-148">將關聯性類型設定為 [彈性]\*\*\*\* 或 [固定]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="d3e21-148">Sets the relationship type to either **Flexible** or **Rigid**.</span></span> <span data-ttu-id="d3e21-149">在彈性關聯性中，成員之間的關聯性會隨時間變更。</span><span class="sxs-lookup"><span data-stu-id="d3e21-149">In a flexible relationship, relationships between members change over time.</span></span> <span data-ttu-id="d3e21-150">在固定關聯性中，成員之間的關聯性不會隨時間變更。</span><span class="sxs-lookup"><span data-stu-id="d3e21-150">In a rigid relationship, relationships between members do not change over time.</span></span>  
  
 <span data-ttu-id="d3e21-151">**刪除**</span><span class="sxs-lookup"><span data-stu-id="d3e21-151">**Delete**</span></span>  
 <span data-ttu-id="d3e21-152">刪除屬性關聯性。</span><span class="sxs-lookup"><span data-stu-id="d3e21-152">Deletes the attribute relationship.</span></span>  
  
 <span data-ttu-id="d3e21-153">**屬性**</span><span class="sxs-lookup"><span data-stu-id="d3e21-153">**Properties**</span></span>  
 <span data-ttu-id="d3e21-154">在 [屬性]\*\*\*\* 視窗中顯示關聯性的屬性。</span><span class="sxs-lookup"><span data-stu-id="d3e21-154">Displays the relationship's properties in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3e21-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d3e21-155">See Also</span></span>  
 <span data-ttu-id="d3e21-156">[屬性關聯性 &#40;維度設計師&#41; &#40;Analysis Services-多維度資料&#41;](attribute-relationships-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d3e21-156">[Attribute Relationships &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](attribute-relationships-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="d3e21-157">[工具列 &#40;屬性關聯性設計師索引標籤、維度設計師&#41; &#40;Analysis Services-多維度資料&#41;](toolbar-attribute-relationship-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d3e21-157">[Toolbar &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-attribute-relationship-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 <span data-ttu-id="d3e21-158">[屬性 &#40;屬性關聯性設計師索引標籤，維度設計師&#41; &#40;Analysis Services 多維度資料&#41;](attributes-designer-tab-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="d3e21-158">[Attributes &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](attributes-designer-tab-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="d3e21-159">屬性關聯性 &#40;屬性關聯性設計工具索引標籤、維度設計師&#41; &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="d3e21-159">Attribute Relationships &#40;Attribute Relationship Designer Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](attribute-relationships-designer-tab-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
