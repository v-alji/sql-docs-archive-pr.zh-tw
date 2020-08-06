---
title: 物件總管詳細資料窗格 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.swb.summary.report.f1
- sql12.swb.summary.general.f1
helpviewer_keywords:
- object search [SQL Server], Object Explorer
- Object Explorer
- object search [SQL Server]
- searching objects [SQL Server]
ms.assetid: b963e3c2-dc9e-4d38-bd28-2e00fe9e0e47
author: stevestein
ms.author: sstein
ms.openlocfilehash: 0ec856ce01930683cf20683a418a658a5b877729
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87708894"
---
# <a name="object-explorer-details-pane"></a><span data-ttu-id="0ccb2-102">物件總管詳細資料窗格</span><span class="sxs-lookup"><span data-stu-id="0ccb2-102">Object Explorer Details Pane</span></span>
  <span data-ttu-id="0ccb2-103">[物件總管詳細資料] 是 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 的元件，它會提供伺服器中所有物件的表格式檢視，並且呈現可管理這些物件的使用者介面。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-103">Object Explorer Details, a component of [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], provides a tabular view of all the objects in the server and presents a user interface to manage them.</span></span> <span data-ttu-id="0ccb2-104">物件總管的功能會隨著伺服器的類型而稍有不同，不過，它通常會包括資料庫的開發功能，以及所有伺服器類型的管理功能。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-104">The capabilities of Object Explorer vary slightly depending on the type of server, but generally include the development features for databases and management features for all server types.</span></span>  
  
 <span data-ttu-id="0ccb2-105">根據預設，[物件總管詳細資料] 窗格會顯示在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 中。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-105">The Object Explorer Details pane is visible in the [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] by default.</span></span> <span data-ttu-id="0ccb2-106">如果您看不到物件總管，請在 [檢視]  功能表上，按一下 [物件總管詳細資料]  或按下 **F7**。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-106">If you cannot see Object Explorer, on the **View** menu, click **Object Explorer Details** or press **F7**.</span></span>  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] <span data-ttu-id="0ccb2-107">會呈現利用 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 啟動時在作用中的 Microsoft Windows [地區及語言選項] 所格式化的日期。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-107">presents dates formatted with the Microsoft Windows Regional and Language Options in effect when [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] was started.</span></span> <span data-ttu-id="0ccb2-108">請重新啟動 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 來反映較新的設定。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-108">Restart [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] to reflect newer settings.</span></span>  
  
## <a name="object-explorer-details"></a><span data-ttu-id="0ccb2-109">物件總管詳細資料</span><span class="sxs-lookup"><span data-stu-id="0ccb2-109">Object Explorer Details</span></span>  
 <span data-ttu-id="0ccb2-110">[物件總管詳細資料] 可用於逐一導覽 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體上的資料夾和物件。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-110">Object Explorer Details can be used to navigate through folders and objects on your [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance.</span></span> <span data-ttu-id="0ccb2-111">在 32 位元作業系統上，[物件總管] 只能顯示 64,000 個物件。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-111">On 32-bit operating systems, Object Explorer can only display 64,000 objects.</span></span> <span data-ttu-id="0ccb2-112">您必須選取一個圖示來存取其他物件。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-112">An icon must be selected to access additional objects.</span></span>  
  
 <span data-ttu-id="0ccb2-113">[物件總管詳細資料] 包括含有下表所述之圖示的工具列。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-113">Object Explorer Details includes a toolbar which contains the icons described in the following table.</span></span> <span data-ttu-id="0ccb2-114">這些圖示只有在適當情況下才能使用。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-114">Icons are only available when appropriate.</span></span>  
  
|<span data-ttu-id="0ccb2-115">圖示</span><span class="sxs-lookup"><span data-stu-id="0ccb2-115">Icon</span></span>|<span data-ttu-id="0ccb2-116">動作</span><span class="sxs-lookup"><span data-stu-id="0ccb2-116">Action</span></span>|  
|----------|------------|  
|<span data-ttu-id="0ccb2-117">**上一頁**</span><span class="sxs-lookup"><span data-stu-id="0ccb2-117">**Back**</span></span>|<span data-ttu-id="0ccb2-118">移至 [物件總管詳細資料] 中顯示的先前項目。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-118">Moves to the previous items displayed in Object Explorer Details.</span></span> <span data-ttu-id="0ccb2-119">當先前的顯示是搜尋作業的結果時，就會重新執行搜尋。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-119">Re-runs a search when the previous display is the result of a search operation.</span></span>|  
|<span data-ttu-id="0ccb2-120">**下一頁**</span><span class="sxs-lookup"><span data-stu-id="0ccb2-120">**Forward**</span></span>|<span data-ttu-id="0ccb2-121">在選取 [上一頁]  作業之後，移至下一個畫面。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-121">Moves to the next screen after a **Back** operation is selected.</span></span>|  
|<span data-ttu-id="0ccb2-122">**Up**</span><span class="sxs-lookup"><span data-stu-id="0ccb2-122">**Up**</span></span>|<span data-ttu-id="0ccb2-123">移至父物件或資料夾。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-123">Moves to the parent object or folder.</span></span>|  
|<span data-ttu-id="0ccb2-124">**同步處理**</span><span class="sxs-lookup"><span data-stu-id="0ccb2-124">**Synchronize**</span></span>|<span data-ttu-id="0ccb2-125">將 [物件總管] 的焦點設定成在 [物件總管詳細資料] 中選取的物件。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-125">Sets the focus of Object Explorer to the selected object in Object Explorer Details.</span></span>|  
|<span data-ttu-id="0ccb2-126">**Filter**</span><span class="sxs-lookup"><span data-stu-id="0ccb2-126">**Filter**</span></span>|<span data-ttu-id="0ccb2-127">如果可用，顯示可設定的物件子集。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-127">When available, shows a configurable subset of objects.</span></span>|  
|<span data-ttu-id="0ccb2-128">**[重新整理]**</span><span class="sxs-lookup"><span data-stu-id="0ccb2-128">**Refresh**</span></span>|<span data-ttu-id="0ccb2-129">重新整理 [物件總管詳細資料] 的顯示。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-129">Refreshes the display in Object Explorer Details.</span></span>|  
|<span data-ttu-id="0ccb2-130">**搜尋**</span><span class="sxs-lookup"><span data-stu-id="0ccb2-130">**Search**</span></span>|<span data-ttu-id="0ccb2-131">提供區域來輸入特定資料庫物件的搜尋詞彙。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-131">Provides an area to enter a search term for certain database objects.</span></span>|  
  
### <a name="column-header-selections"></a><span data-ttu-id="0ccb2-132">資料行標頭選取範圍</span><span class="sxs-lookup"><span data-stu-id="0ccb2-132">Column Header Selections</span></span>  
 <span data-ttu-id="0ccb2-133">[物件總管詳細資料] 具有可選取的資料行。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-133">Object Explorer Details has selectable columns.</span></span> <span data-ttu-id="0ccb2-134">您可以在任何資料行標頭中按一下滑鼠右鍵，然後檢查想要顯示的項目。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-134">You can right-click in any column header and check the items that you want to display.</span></span> <span data-ttu-id="0ccb2-135">您的選取範圍將會保存在逐一導覽的不同物件中。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-135">Your selections will be persisted across the different objects you navigate through.</span></span> <span data-ttu-id="0ccb2-136">當您離開並重新啟動 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]時，系統就會保留每位使用者的選取範圍。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-136">Selections for each user are retained when you leave and restart [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)].</span></span>  
  
> [!CAUTION]  
>  <span data-ttu-id="0ccb2-137">若為大型物件集，顯示某些物件類型 (例如資料庫) 的所有資料行可能會稍微降低顯示轉譯的速度。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-137">Showing all columns for some object types (such as Databases) might slow the display rendering slightly for large sets of objects.</span></span>  
  
### <a name="sorting"></a><span data-ttu-id="0ccb2-138">排序</span><span class="sxs-lookup"><span data-stu-id="0ccb2-138">Sorting</span></span>  
 <span data-ttu-id="0ccb2-139">按一下資料行標頭就會依據該資料行進行排序。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-139">Clicking one time on a column header will sort by that column.</span></span> <span data-ttu-id="0ccb2-140">再次按一下相同的標頭則會依據該資料行進行反向排序。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-140">Clicking again on the same header reverse-sorts by that column.</span></span> <span data-ttu-id="0ccb2-141">每位使用者的排序選取範圍會保留在物件和資料夾中，而且會在 [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] 重新啟動時保留。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-141">Sort selections are maintained for each user across objects and folders, and on [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] restart.</span></span>  
  
### <a name="filtering"></a><span data-ttu-id="0ccb2-142">Filtering</span><span class="sxs-lookup"><span data-stu-id="0ccb2-142">Filtering</span></span>  
 <span data-ttu-id="0ccb2-143">您可以使用 [物件總管詳細資料] 工具列上的 [篩選]  圖示來篩選顯示在 [物件總管詳細資料] 中的特定物件清單。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-143">Certain lists of objects displayed in Object Explorer Detail can be filtered using the **Filter** icon on the Object Explorer Details toolbar.</span></span> <span data-ttu-id="0ccb2-144">此圖示會在可進行篩選時啟用。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-144">The icon will be enabled when filtering is possible.</span></span>  
  
### <a name="details-pane"></a><span data-ttu-id="0ccb2-145">詳細資料窗格</span><span class="sxs-lookup"><span data-stu-id="0ccb2-145">Details Pane</span></span>  
 <span data-ttu-id="0ccb2-146">[物件總管詳細資料] 的最底部區域包含一個面板，其中顯示所選物件的特定詳細資料。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-146">The very bottom area of Object Explorer Details contains a panel that displays certain details of the selected object.</span></span> <span data-ttu-id="0ccb2-147">多重物件選取範圍只會顯示物件的計數。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-147">Multiple object selections show only the count of the objects.</span></span> <span data-ttu-id="0ccb2-148">在此面板中選取項目時，按一下 [複製]  圖示，即可將顯示的文字複製到 [剪貼簿]。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-148">When items are selected in the panel, click the **Copy** icon to copy the displayed text to the clipboard.</span></span>  
  
 <span data-ttu-id="0ccb2-149">向下鍵會將選取範圍移至清單中的下一個項目。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-149">The down arrow key moves the selection to the next item in the list.</span></span> <span data-ttu-id="0ccb2-150">向上鍵會將選取範圍移至清單中的上一個項目。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-150">The up arrow key moves the selection to the previous item in the list.</span></span> <span data-ttu-id="0ccb2-151">按住方向鍵則會加快在項目之間移動的速度。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-151">Holding the arrow key down will speed through the items.</span></span> <span data-ttu-id="0ccb2-152">選取範圍會在屬性清單的底部或頂端停止。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-152">The selection stops at the bottom or top of the property list.</span></span>  
  
 <span data-ttu-id="0ccb2-153">輸入屬性名稱的第一個字元就會將選取範圍移至以該字元為開頭的下一個屬性。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-153">Typing the first character of a property name moves the selection to the next property that begins with that character.</span></span>  
  
 <span data-ttu-id="0ccb2-154">當屬性排列於多個欄位時，請使用向左鍵和向右鍵來移至相鄰的欄位。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-154">When properties are arranged in multiple columns, use the left arrow and right arrow keys to move to adjacent columns.</span></span>  
  
 <span data-ttu-id="0ccb2-155">若要將屬性值複製到 [剪貼簿]，請使用下列鍵盤組合鍵：</span><span class="sxs-lookup"><span data-stu-id="0ccb2-155">To copy property values to the clipboard, use the following keyboard key combinations:</span></span>  
  
-   <span data-ttu-id="0ccb2-156">Ctrl+C 會複製屬性值。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-156">Ctrl+C copies the property value.</span></span>  
  
-   <span data-ttu-id="0ccb2-157">Ctrl+Shift+C 會使用 Tab 鍵分隔符號來複製屬性名稱和屬性值。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-157">Ctrl+Shift+C copies the property name and the property value with a tab delimiter.</span></span>  
  
 <span data-ttu-id="0ccb2-158">您可以使用 [物件總管詳細資料] 屬性窗格中的右鍵功能表，將所有屬性或所有屬性和名稱複製到 [剪貼簿]。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-158">Use the right-click menu in the Object Explorer Details property pane to copy all properties or all properties and names to the clipboard.</span></span>  
  
 <span data-ttu-id="0ccb2-159">若要在欄位寬度無法完全顯示屬性值時顯示屬性值，請將滑鼠游標停留在該值上方，或將 UI 焦點設定於該屬性值，以便啟動包含整個屬性值的工具提示。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-159">To display a property value when the field width does not completely display a property value, hover the mouse cursor over the value or set UI focus on the property value to activate a tool tip with the entire property value.</span></span> <span data-ttu-id="0ccb2-160">當使用者將焦點設為冗長的屬性值時，協助工具螢幕助讀員將報告完整的屬性值。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-160">Accessibility screen readers will report the full property value when the user focuses on the long property value.</span></span>  
  
 <span data-ttu-id="0ccb2-161">如果屬性窗格中的屬性數目超過內容區域可容納的數目，屬性窗格的右側就會顯示捲軸。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-161">If the number of properties in the property pane exceeds that which will fit in the content area, a scroll bar will appear on the right side of the property pane.</span></span> <span data-ttu-id="0ccb2-162">您可以使用捲軸來調整內容區域中屬性值的檢視。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-162">Use the scroll bar to adjust the view of property values in the content area.</span></span>  
  
### <a name="multiple-object-selection"></a><span data-ttu-id="0ccb2-163">多重物件選取範圍</span><span class="sxs-lookup"><span data-stu-id="0ccb2-163">Multiple Object Selection</span></span>  
 <span data-ttu-id="0ccb2-164">[物件總管詳細資料] 支援多重物件選取範圍。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-164">Object Explorer Details supports multiple object selection.</span></span> <span data-ttu-id="0ccb2-165">例如，如果您在物件總管中選取 [資料表]，接著在 [物件總管詳細資料] 視窗中按住 **Ctrl** 鍵，就可以選取多個資料表、以滑鼠右鍵按一下它們，然後選取 [刪除]  或 [編寫資料表的指令碼為]  ，立即在所有選取的資料表上運作。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-165">For example, if you select Tables in Object Explorer, then in the Object Explorer Details window if you hold down the **Ctrl** key, you can select several tables, right-click them, and then select **Delete** or **Script Table AS** to act on all the selected tables immediately.</span></span> <span data-ttu-id="0ccb2-166">標準的複製命令會將顯示的文字複製到 [剪貼簿]。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-166">The standard copy commands will copy the displayed text to the clipboard.</span></span>  
  
## <a name="sql-server-object-search"></a><span data-ttu-id="0ccb2-167">SQL Server 物件搜尋</span><span class="sxs-lookup"><span data-stu-id="0ccb2-167">SQL Server Object Search</span></span>  
 <span data-ttu-id="0ccb2-168">萬用字元</span><span class="sxs-lookup"><span data-stu-id="0ccb2-168">Wildcards</span></span>  
  
-   <span data-ttu-id="0ccb2-169">支援標準的萬用字元。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-169">Standard wildcard characters are supported.</span></span> <span data-ttu-id="0ccb2-170">例如，搜尋 **dm_os%counters** 就會傳回 dm_os_memory_cache_counters 和 dm_os_performance_counters。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-170">For example, searching for **dm_os%counters** returns both dm_os_memory_cache_counters and dm_os_performance_counters.</span></span> <span data-ttu-id="0ccb2-171">如需詳細資訊，請參閱[使用萬用字元搜尋文字](../../relational-databases/scripting/search-text-with-wildcards.md)。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-171">For more information, see [Search Text with Wildcards](../../relational-databases/scripting/search-text-with-wildcards.md).</span></span>  
  
 <span data-ttu-id="0ccb2-172">搜尋範圍</span><span class="sxs-lookup"><span data-stu-id="0ccb2-172">Search Scope</span></span>  
  
-   <span data-ttu-id="0ccb2-173">每個搜尋的範圍都會設定成 [物件總管] 樹狀結構中的目前焦點。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-173">Each search is scoped to the current focus in the Object Explorer tree.</span></span> <span data-ttu-id="0ccb2-174">例如，如果物件總管的焦點是資料庫，則搜尋 **dm_os%counters** 就會傳回該資料庫中的 dm_os_memory_cache_counters 和 dm_os_performance_counters。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-174">For example, if the Object Explorer focus is on a database, search for **dm_os%counters** returns dm_os_memory_cache_counters and dm_os_performance_counters in that database.</span></span> <span data-ttu-id="0ccb2-175">如果 [物件總管] 的焦點是 [資料庫] 節點，就會搜尋所有資料庫，而且會傳回多個動態檢視的執行個體。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-175">If the Object Explorer focus is on the Databases node, all databases are searched and multiple instances of the dynamic views are returned.</span></span>  
  
 <span data-ttu-id="0ccb2-176">大型集</span><span class="sxs-lookup"><span data-stu-id="0ccb2-176">Large Sets</span></span>  
  
-   <span data-ttu-id="0ccb2-177">搜尋大型物件集可能會需要很長的時間，而且會降低伺服器效能。</span><span class="sxs-lookup"><span data-stu-id="0ccb2-177">Searching large object sets can take a long time and slow server performance.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ccb2-178">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ccb2-178">See Also</span></span>  
 [<span data-ttu-id="0ccb2-179">物件總管</span><span class="sxs-lookup"><span data-stu-id="0ccb2-179">Object Explorer</span></span>](object-explorer.md)  
  
  
