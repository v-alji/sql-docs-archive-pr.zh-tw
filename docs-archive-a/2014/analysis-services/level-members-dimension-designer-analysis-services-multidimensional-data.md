---
title: 層級和成員 (瀏覽器索引標籤、維度設計師)  (Analysis Services-多維度資料) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dimensiondesigner.browsertab.levelsandmembers.f1
ms.assetid: 3f61e384-5b4e-4480-a7ed-b408de2fdea7
author: minewiskan
ms.author: owend
ms.openlocfilehash: 21680f00b82b5410e2c7a67122fdcfeb78c999dc
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87710945"
---
# <a name="level-and-members-browser-tab-dimension-designer-analysis-services---multidimensional-data"></a><span data-ttu-id="7bfb8-102">層級和成員 (瀏覽器索引標籤，維度設計師) (Analysis Services - 多維度資料)</span><span class="sxs-lookup"><span data-stu-id="7bfb8-102">Level and Members (Browser Tab, Dimension Designer) (Analysis Services - Multidimensional Data)</span></span>
  <span data-ttu-id="7bfb8-103">使用此頁面來瀏覽目前選取之階段和語言的成員。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-103">Use this pane to browse the members of the currently selected hierarchy and language.</span></span> <span data-ttu-id="7bfb8-104">若要選取要瀏覽的階層或語言，請使用 **[工具列]** 窗格上的 **[階層]** 和 **[語言]** 選項。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-104">To select a hierarchy or language to browse, use the **Hierarchy** and **Language** options on the **Toolbar** pane.</span></span> <span data-ttu-id="7bfb8-105">如需 [工具列] 窗格的詳細資訊，請參閱[工具列 &#40;瀏覽器索引標籤、維度設計師&#41; &#40;Analysis Services-多維度資料&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-105">For more information about the Toolbar pane, see [Toolbar &#40;Browser Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md).</span></span>  
  
## <a name="writeback-mode"></a><span data-ttu-id="7bfb8-106">回寫模式</span><span class="sxs-lookup"><span data-stu-id="7bfb8-106">Writeback Mode</span></span>  
 <span data-ttu-id="7bfb8-107">如果啟用回寫模式，此窗格的功能就會變更。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-107">The functionality of this pane changes if writeback mode is enabled.</span></span> <span data-ttu-id="7bfb8-108">選取的維度必須是可寫入的 (換言之，維度的 `WriteEnabled` 屬性必須設定為 True)，而且必須將維度部署至 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 執行個體才能啟用回寫模式。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-108">The selected dimension must be write-enabled (in other words, the `WriteEnabled` property of the dimension must be set to true) and the dimension must be deployed to an [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] instance in order to enable writeback mode.</span></span>  
  
 <span data-ttu-id="7bfb8-109">若要啟用回寫模式，您可以從 [工具列]\*\*\*\* 窗格中選取 [回寫]\*\*\*\*，或以滑鼠右鍵按一下 [層級和成員]\*\*\*\* 窗格，然後從內容功能表中選取 [回寫]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-109">To enable writeback mode, you can either select **Writeback** from the **Toolbar** pane, or right-click the **Level and Members** pane and select **Writeback** from the context menu.</span></span>  
  
 <span data-ttu-id="7bfb8-110">如果已啟用回寫模式，您可以在 **[層級和成員]** 窗格中執行下列的其他動作：</span><span class="sxs-lookup"><span data-stu-id="7bfb8-110">If writeback mode is enabled, you can perform the following additional actions in the **Level and Members** pane:</span></span>  
  
|<span data-ttu-id="7bfb8-111">若要這樣做，</span><span class="sxs-lookup"><span data-stu-id="7bfb8-111">To do</span></span>|<span data-ttu-id="7bfb8-112">執行</span><span class="sxs-lookup"><span data-stu-id="7bfb8-112">Perform</span></span>|  
|-----------|-------------|  
|<span data-ttu-id="7bfb8-113">在選取的階層內建立同層級成員和子成員。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-113">Create sibling and child members within the selected hierarchy.</span></span>|<span data-ttu-id="7bfb8-114">以滑鼠右鍵按一下選取的成員，然後從內容功能表中選取 [建立同層級]\*\*\*\* 來建立同層級成員，或選取 [建立子系]\*\*\*\* 來建立子成員。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-114">Right-click the selected member and select either **Create Sibling**, to create a sibling member, or **Create Child**, to create a child member, from the context menu.</span></span>|  
|<span data-ttu-id="7bfb8-115">將選取的成員在階層間向上或向下移動。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-115">Move a selected member up or down the hierarchy.</span></span>|<span data-ttu-id="7bfb8-116">將選取的成員拖曳至適當的父成員或子成員處，或在 **[工具列]** 窗格上按一下 **[增加縮排]** 或 **[減少縮排]** ，將選取的成員在階層的各層級間向上或向下移動。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-116">Either drag the selected member to the appropriate parent or child member, or click **Increase Indent** or **Decrease Indent** on the **Toolbar** pane to move the selected member up or down the levels of the hierarchy.</span></span>|  
|<span data-ttu-id="7bfb8-117">重新命名選取的成員。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-117">Rename a selected member.</span></span>|<span data-ttu-id="7bfb8-118">以滑鼠右鍵按一下選取的成員，然後選取 [重新命名]\*\*\*\*，或按一下已經選取的成員。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-118">Either right-click the selected member and select **Rename**, or click an already-selected member.</span></span>|  
|<span data-ttu-id="7bfb8-119">編輯成員屬性值</span><span class="sxs-lookup"><span data-stu-id="7bfb8-119">Edit member property values</span></span>|<span data-ttu-id="7bfb8-120">針對選取的成員按兩下已選取成員屬性中的值，以編輯該值。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-120">Double-click the value in the selected member property for the selected member to edit the value.</span></span>|  
  
## <a name="options"></a><span data-ttu-id="7bfb8-121">選項</span><span class="sxs-lookup"><span data-stu-id="7bfb8-121">Options</span></span>  
 <span data-ttu-id="7bfb8-122">**目前層級**</span><span class="sxs-lookup"><span data-stu-id="7bfb8-122">**Current level**</span></span>  
 <span data-ttu-id="7bfb8-123">顯示目前在 [樹狀]\*\*\*\* 中選取之成員所屬的層級。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-123">Displays the level to which the currently selected member in **Tree** belongs.</span></span>  
  
 <span data-ttu-id="7bfb8-124">**路徑**</span><span class="sxs-lookup"><span data-stu-id="7bfb8-124">**Tree**</span></span>  
 <span data-ttu-id="7bfb8-125">顯示目前選取之階層和語言的成員。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-125">Displays the members of the currently selected hierarchy and language.</span></span>  
  
 <span data-ttu-id="7bfb8-126">如果是從 [工具列] 窗格的 **[成員屬性]** 選項中選取成員屬性，則每個成員屬性都會顯示為一個資料行。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-126">If member properties are selected from the **Member Properties** option of the Toolbar pane, each member property is displayed as a column.</span></span>  
  
 <span data-ttu-id="7bfb8-127">如果啟用回寫模式，與維度中之索引鍵屬性相關聯的每一個索引鍵資料行都會顯示一個資料行。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-127">If writeback mode is enabled, one column for each key column associated with the key attribute in the dimension is displayed.</span></span>  
  
## <a name="context-menu"></a><span data-ttu-id="7bfb8-128">操作功能表</span><span class="sxs-lookup"><span data-stu-id="7bfb8-128">Context Menu</span></span>  
 <span data-ttu-id="7bfb8-129">以滑鼠右鍵按一下所選取成員之 [層級和成員]\*\*\*\* 窗格的任何部份，即可顯示提供下列選項的內容功能表：</span><span class="sxs-lookup"><span data-stu-id="7bfb8-129">The following options are available in the context menu displayed by right-clicking any part of the **Level and Members** pane for the selected member:</span></span>  
  
 <span data-ttu-id="7bfb8-130">**建立同層級**</span><span class="sxs-lookup"><span data-stu-id="7bfb8-130">**Create sibling**</span></span>  
 <span data-ttu-id="7bfb8-131">建立與選取之成員同層級的新成員。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-131">Creates a new member at the same level as the selected member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bfb8-132">唯有選取了 (所有) 層級以外層級的成員時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-132">This option is enabled only if a member at a level other than the (All) level is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bfb8-133">只有啟用回寫模式時才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-133">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="7bfb8-134">**建立子系**</span><span class="sxs-lookup"><span data-stu-id="7bfb8-134">**Create child**</span></span>  
 <span data-ttu-id="7bfb8-135">在選取之成員的下一個較低層級上建立新成員，作為選取之成員的子成員。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-135">Creates a new member at the next lower level as the selected member, as a child of the selected member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bfb8-136">唯有選取了最低層級以外層級的成員時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-136">This option is enabled only if a member at a level other than the lowest level is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bfb8-137">只有啟用回寫模式時才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-137">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="7bfb8-138">**剪下**</span><span class="sxs-lookup"><span data-stu-id="7bfb8-138">**Cut**</span></span>  
 <span data-ttu-id="7bfb8-139">將選取的成員複製至剪貼簿，並將它們從階層中移除。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-139">Copies the selected members to the clipboard and removes them from the hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bfb8-140">唯有選取所有成員以外的成員時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-140">This option is enabled only if a member other than the All member is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bfb8-141">只有啟用回寫模式時才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-141">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="7bfb8-142">**貼上**</span><span class="sxs-lookup"><span data-stu-id="7bfb8-142">**Paste**</span></span>  
 <span data-ttu-id="7bfb8-143">將之前使用 [剪下]\*\*\*\* 移除的成員，貼在選取之成員的後面。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-143">Pastes members previously removed using **Cut** immediately after the selected member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bfb8-144">只有啟用回寫模式時才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-144">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="7bfb8-145">**刪除**</span><span class="sxs-lookup"><span data-stu-id="7bfb8-145">**Delete**</span></span>  
 <span data-ttu-id="7bfb8-146">從階層中移除選取的成員。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-146">Removes the selected members from the hierarchy.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bfb8-147">唯有選取所有成員以外的成員時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-147">This option is enabled only if a member other than the All member is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bfb8-148">只有啟用回寫模式時才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-148">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="7bfb8-149">**重新命名**</span><span class="sxs-lookup"><span data-stu-id="7bfb8-149">**Rename**</span></span>  
 <span data-ttu-id="7bfb8-150">選取即可編輯選取之成員的名稱。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-150">Select to edit the name of the selected member.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bfb8-151">唯有選取所有成員以外的成員時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-151">This option is enabled only if a member other than the All member is selected.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bfb8-152">只有啟用回寫模式時才會顯示此選項。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-152">This option is displayed only if writeback mode is enabled.</span></span>  
  
 <span data-ttu-id="7bfb8-153">**篩選成員**</span><span class="sxs-lookup"><span data-stu-id="7bfb8-153">**Filter Members**</span></span>  
 <span data-ttu-id="7bfb8-154">顯示 [篩選成員]\*\*\*\* 對話方塊，以針對選取的階層篩選顯示在 [層級和成員]\*\*\*\* 中的成員。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-154">Displays the **Filter Members** dialog box to filter members displayed in **Level and Members** for the selected hierarchy.</span></span> <span data-ttu-id="7bfb8-155">如需 [篩選成員]\*\*\*\* 對話方塊的詳細資訊，請參閱[篩選成員對話方塊 &#40;Analysis Services - 多維度資料&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md)。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-155">For more information about the **Filter Members** dialog box, see [Filter Members Dialog Box &#40;Analysis Services - Multidimensional Data&#41;](filter-members-dialog-box-analysis-services-multidimensional-data.md).</span></span>  
  
 <span data-ttu-id="7bfb8-156">**全部展開**</span><span class="sxs-lookup"><span data-stu-id="7bfb8-156">**Expand All**</span></span>  
 <span data-ttu-id="7bfb8-157">展開 [樹狀]\*\*\*\* 中的所有成員。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-157">Expands all members in **Tree**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="7bfb8-158">唯有選取了最低層級以外層級的成員時，才會啟用此選項。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-158">This option is enabled only if a member at a level other than the lowest level is selected.</span></span>  
  
 <span data-ttu-id="7bfb8-159">**全部摺疊**</span><span class="sxs-lookup"><span data-stu-id="7bfb8-159">**Collapse All**</span></span>  
 <span data-ttu-id="7bfb8-160">摺疊 [樹狀]\*\*\*\* 中的所有成員。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-160">Collapse all members in **Tree**.</span></span>  
  
 <span data-ttu-id="7bfb8-161">**展開成員**</span><span class="sxs-lookup"><span data-stu-id="7bfb8-161">**Expand Member**</span></span>  
 <span data-ttu-id="7bfb8-162">展開 [樹狀]\*\*\*\* 中選取的成員。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-162">Expand the selected member in **Tree**.</span></span>  
  
 <span data-ttu-id="7bfb8-163">**摺疊成員**</span><span class="sxs-lookup"><span data-stu-id="7bfb8-163">**Collapse Member**</span></span>  
 <span data-ttu-id="7bfb8-164">摺疊 [樹狀]\*\*\*\* 中選取的成員。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-164">Collapse the selected member in **Tree**.</span></span>  
  
 <span data-ttu-id="7bfb8-165">**回寫**</span><span class="sxs-lookup"><span data-stu-id="7bfb8-165">**Writeback**</span></span>  
 <span data-ttu-id="7bfb8-166">選取即可啟用回寫模式。</span><span class="sxs-lookup"><span data-stu-id="7bfb8-166">Select to enable writeback mode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bfb8-167">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7bfb8-167">See Also</span></span>  
 <span data-ttu-id="7bfb8-168">[[工具列 &#40;瀏覽器] 索引標籤、[維度設計師]&#41; &#40;Analysis Services-多維度資料&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md) </span><span class="sxs-lookup"><span data-stu-id="7bfb8-168">[Toolbar &#40;Browser Tab, Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;](toolbar-browser-tab-dimension-designer-analysis-services-multidimensional-data.md) </span></span>  
 [<span data-ttu-id="7bfb8-169">瀏覽器 &#40;維度設計師&#41; &#40;Analysis Services-多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="7bfb8-169">Browser &#40;Dimension Designer&#41; &#40;Analysis Services - Multidimensional Data&#41;</span></span>](browser-dimension-designer-analysis-services-multidimensional-data.md)  
  
  
