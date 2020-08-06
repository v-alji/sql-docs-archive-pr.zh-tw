---
title: 在資料來源視圖設計工具中使用圖表 (Analysis Services) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.dsvdesigner.diagramorganizerpane.f1
- sql12.asvs.dsvdesigner.findtable.f1
- sql12.asvs.dsvdesigner.diagrampane.f1
helpviewer_keywords:
- data source views [Analysis Services], diagrams
- diagrams [Analysis Services]
ms.assetid: 491fdd22-2326-4f27-a0dd-0a02faae3fd8
author: minewiskan
ms.author: owend
ms.openlocfilehash: 40a58ed33ff6cfaebf2a6e7c084500dd3ae072da
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596348"
---
# <a name="work-with-diagrams-in-data-source-view-designer-analysis-services"></a><span data-ttu-id="f457a-102">在資料來源檢視設計工具中使用圖表 (Analysis Services)</span><span class="sxs-lookup"><span data-stu-id="f457a-102">Work with Diagrams in Data Source View Designer (Analysis Services)</span></span>
  <span data-ttu-id="f457a-103">資料來源檢視 (DSV) 圖表是 DSV 中物件的視覺表示法。</span><span class="sxs-lookup"><span data-stu-id="f457a-103">A data source view (DSV) diagram is a visual representation of the objects in a DSV.</span></span> <span data-ttu-id="f457a-104">您可以使用圖表以互動方式加入、隱藏、刪除或修改特定物件。</span><span class="sxs-lookup"><span data-stu-id="f457a-104">You can work with the diagram interactively to add, hide, delete or modify specific objects.</span></span> <span data-ttu-id="f457a-105">您也可以在相同的 DSV 中建立多個圖表，將注意集中在物件子集。</span><span class="sxs-lookup"><span data-stu-id="f457a-105">You can also create multiple diagrams on the same DSV to focus attention on a subset of the objects.</span></span>  
  
 <span data-ttu-id="f457a-106">若要變更圖表窗格中出現的圖表區域，請按一下窗格右下角之四個方向的箭頭，然後將選擇方塊拖曳至縮圖圖表上方，直到選取要出現在圖表窗格中的區域為止。</span><span class="sxs-lookup"><span data-stu-id="f457a-106">To change the area of the diagram that appears in the diagram pane, click the four-headed arrow in the lower right corner of the pane, and then drag the selection box over the thumbnail diagram until you select the area that is to appear in the diagram pane.</span></span>  
  
 <span data-ttu-id="f457a-107">這個主題包括下列各節：</span><span class="sxs-lookup"><span data-stu-id="f457a-107">This topic includes the following sections:</span></span>  
  
 [<span data-ttu-id="f457a-108">加入圖表</span><span class="sxs-lookup"><span data-stu-id="f457a-108">Add a Diagram</span></span>](#bkmk_add)  
  
 [<span data-ttu-id="f457a-109">編輯或刪除圖表</span><span class="sxs-lookup"><span data-stu-id="f457a-109">Edit or Delete a Diagram</span></span>](#bkmk_edit)  
  
 [<span data-ttu-id="f457a-110">在圖表中尋找資料表</span><span class="sxs-lookup"><span data-stu-id="f457a-110">Find Tables in a Diagram</span></span>](#bkmk_findtables)  
  
 [<span data-ttu-id="f457a-111">排列圖表中的物件</span><span class="sxs-lookup"><span data-stu-id="f457a-111">Arrange Objects in a Diagram</span></span>](#bkmk_arrangeobjects)  
  
 [<span data-ttu-id="f457a-112">保留物件相片順序</span><span class="sxs-lookup"><span data-stu-id="f457a-112">Preserve object arrangement</span></span>](#bkmk_preserve)  
  
##  <a name="add-a-diagram"></a><a name="bkmk_add"></a><span data-ttu-id="f457a-113">新增圖表</span><span class="sxs-lookup"><span data-stu-id="f457a-113">Add a Diagram</span></span>  
 <span data-ttu-id="f457a-114">DSV 圖表會在您建立 DSV 時自動建立。</span><span class="sxs-lookup"><span data-stu-id="f457a-114">DSV diagrams are created automatically when you create the DSV.</span></span> <span data-ttu-id="f457a-115">DSV 存在之後，即可建立其他圖表、移除圖表或隱藏特定物件，以建立更容易管理的 DSV 表示法。</span><span class="sxs-lookup"><span data-stu-id="f457a-115">After the DSV exists, you can create additional diagrams, remove them, or hide specific objects to create a more manageable representation of the DSV.</span></span>  
  
 <span data-ttu-id="f457a-116">若要建立新圖表，請以滑鼠右鍵按一下 [圖表組合管理]\*\*\*\* 窗格中的任何位置，然後按一下 [新增圖表]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="f457a-116">To create a new diagram, right-click anywhere in the **Diagram Organizer** pane, click **New Diagram**.</span></span>  
  
 <span data-ttu-id="f457a-117">當您一開始在 Analysis Services 專案中定義資料來源視圖 (DSV) 時，加入至資料來源視圖的所有資料表和 views 都會加入至 \<All Tables> 圖表中。</span><span class="sxs-lookup"><span data-stu-id="f457a-117">When you initially define a data source view (DSV) in an Analysis Services project, all tables and views added to the data source view are added to the \<All Tables> diagram.</span></span> <span data-ttu-id="f457a-118">這個圖表會出現在資料來源檢視設計師的 [圖表組合管理] 窗格內，而這個圖表中的資料表 (以及其資料行和關聯性) 會列在 [資料表] 窗格內，而且這個圖表中的資料表 (以及其資料行和關聯性) 會以圖形方式顯示在結構描述窗格內。</span><span class="sxs-lookup"><span data-stu-id="f457a-118">This diagram appears in the Diagram Organizer pane in Data Source View Designer, the tables in this diagram (and their columns and relationships) are listed in the Tables pane, and the tables in this diagram (and their columns and relationships) are displayed graphically in the schema pane.</span></span> <span data-ttu-id="f457a-119">不過，當您在圖表中加入資料表、視圖和名稱查詢時 \<All Tables> ，此圖表中的物件數量非常難以視覺化關聯性，尤其是將多個事實資料表加入至圖表，而維度資料表與多個事實資料表相關。</span><span class="sxs-lookup"><span data-stu-id="f457a-119">However, as you add tables, views and named queries to the \<All Tables> diagram, the sheer number of objects in this diagram makes it difficult to visualize relationships-particularly as multiple fact tables are added to the diagram, and dimension tables relate to multiple fact tables.</span></span>  
  
 <span data-ttu-id="f457a-120">當您只想要在資料來源檢視中檢視資料表的子集時，如果要減少視覺上的混亂情形，您可以在此資料來源檢視中定義由資料表、檢視和具名查詢的選定子集所組成的子圖表 (就稱為圖表)。</span><span class="sxs-lookup"><span data-stu-id="f457a-120">To reduce the visual clutter when you only want to view a subset of the tables in the data source view, you can define sub-diagrams (simply called diagrams) consisting of selected subsets of the tables, views, and named queries in the data source view.</span></span> <span data-ttu-id="f457a-121">您可以使用圖表，根據商務或方案需求，將資料來源檢視中的項目分組。</span><span class="sxs-lookup"><span data-stu-id="f457a-121">You can use diagrams to group items in the data source view according to business or solution needs.</span></span>  
  
 <span data-ttu-id="f457a-122">基於商業用途，您可以將相關資料表和具名查詢分組在不同的圖表中，讓人更容易了解包含許多資料表、檢視和具名查詢的資料來源檢視。</span><span class="sxs-lookup"><span data-stu-id="f457a-122">You can group related tables and named queries in separate diagrams for business purposes, and to make it easier to understand a data source view that contains many tables, views, and named queries.</span></span> <span data-ttu-id="f457a-123">相同的資料表或命名的查詢可以包含在多個圖表中，但 \<All Tables> 圖表除外。</span><span class="sxs-lookup"><span data-stu-id="f457a-123">The same table or named query can be included in multiple diagrams except for the \<All Tables> diagram.</span></span> <span data-ttu-id="f457a-124">在 \<All Tables> 圖表中，資料來源視圖中所包含的所有物件只會顯示一次。</span><span class="sxs-lookup"><span data-stu-id="f457a-124">In the \<All Tables> diagram, all objects that are contained in the data source view are shown exactly once.</span></span>  
  
##  <a name="edit-or-delete-a-diagram"></a><a name="bkmk_edit"></a><span data-ttu-id="f457a-125">編輯或刪除圖表</span><span class="sxs-lookup"><span data-stu-id="f457a-125">Edit or Delete a Diagram</span></span>  
 <span data-ttu-id="f457a-126">使用圖表時，請特別注意用於加入及移除物件的命令。</span><span class="sxs-lookup"><span data-stu-id="f457a-126">When working with a diagram, pay close attention to the commands used for adding and removing objects.</span></span> <span data-ttu-id="f457a-127">例如，從圖表中刪除物件會從 DSV 中刪除相同物件。</span><span class="sxs-lookup"><span data-stu-id="f457a-127">For example, deleting an object from a diagram will delete it from the DSV.</span></span> <span data-ttu-id="f457a-128">如果您只想將其從圖表中刪除，請改用 **[隱藏資料表]** 。</span><span class="sxs-lookup"><span data-stu-id="f457a-128">If you only want to delete it from the diagram, use **Hide Table** instead.</span></span>  
  
 <span data-ttu-id="f457a-129">![圖表工作空間的螢幕擷取畫面，以滑鼠右鍵按一下功能表](../media/ssas-olapdsv-diagram.gif "圖表工作空間的螢幕擷取畫面，以滑鼠右鍵按一下功能表")</span><span class="sxs-lookup"><span data-stu-id="f457a-129">![Screenshot of diagram workspace, right-click menu](../media/ssas-olapdsv-diagram.gif "Screenshot of diagram workspace, right-click menu")</span></span>  
  
 <span data-ttu-id="f457a-130">雖然您可以個別隱藏物件，但是使用 [顯示相關資料表] 命令重新顯示物件時，會將所有相關物件傳回圖表。</span><span class="sxs-lookup"><span data-stu-id="f457a-130">Although you can hide objects individually, bringing them back using the Show Related Tables command returns all related objects to the diagram.</span></span> <span data-ttu-id="f457a-131">若要控制傳回工作空間的物件，請改為從 [資料表] 窗格中拖曳物件。</span><span class="sxs-lookup"><span data-stu-id="f457a-131">To control which objects are returned to the workspace, drag them from the Tables pane instead.</span></span>  
  
##  <a name="find-tables-in-a-diagram"></a><a name="bkmk_findtables"></a><span data-ttu-id="f457a-132">在圖表中尋找資料表</span><span class="sxs-lookup"><span data-stu-id="f457a-132">Find Tables in a Diagram</span></span>  
 <span data-ttu-id="f457a-133">如果結構描述很大，則在 **[圖表]** 窗格中捲動至特定資料表可能會有困難。</span><span class="sxs-lookup"><span data-stu-id="f457a-133">If your schema is large, scrolling to a particular table in the **Diagram** pane may be difficult.</span></span> <span data-ttu-id="f457a-134">然而，下列工具可讓您輕鬆地尋找圖表中的資料表。</span><span class="sxs-lookup"><span data-stu-id="f457a-134">However, the following tools make it easy to find a table in a diagram.</span></span>  
  
-   <span data-ttu-id="f457a-135">在 **[資料表]** 窗格中捲動資料表清單。</span><span class="sxs-lookup"><span data-stu-id="f457a-135">Scroll the list of tables in the **Tables** pane.</span></span>  
  
     <span data-ttu-id="f457a-136">若要將資料表包含在目前顯示的圖表中，請將資料表從 **[資料表]** 窗格拖曳到圖表窗格。</span><span class="sxs-lookup"><span data-stu-id="f457a-136">To include a table in the currently displayed diagram, drag the table from the **Tables** pane to the diagram pane.</span></span>  
  
     <span data-ttu-id="f457a-137">若要將圖表中已包含的資料表置中顯示，請在 **[資料表]** 窗格中選取資料表。</span><span class="sxs-lookup"><span data-stu-id="f457a-137">To center the display on a table that is already included in the diagram, select the table in the **Tables** pane.</span></span>  
  
-   <span data-ttu-id="f457a-138">**圖表**窗格中的資料表定位器-資料表定位器是四向箭號圖示，位於 [**圖表**] 窗格右下角垂直和水準捲軸的交集處。</span><span class="sxs-lookup"><span data-stu-id="f457a-138">Table locator in **Diagram** pane-The table locator is a 4-way arrow icon located at the intersection of the vertical and horizontal scroll bars in the lower right corner of the **Diagram** pane.</span></span> <span data-ttu-id="f457a-139">它會開啟 [圖表] 窗格中目前圖表的縮圖表示。</span><span class="sxs-lookup"><span data-stu-id="f457a-139">It opens a thumbnail representation of the current diagram in the Diagram pane.</span></span> <span data-ttu-id="f457a-140">您可以使用此縮圖，將 [圖表] 窗格中的檢視變更至圖表的任何位置。</span><span class="sxs-lookup"><span data-stu-id="f457a-140">You can use this thumbnail to change the view in the Diagram pane to any location on the diagram.</span></span>  
  
-   <span data-ttu-id="f457a-141">使用 [**尋找資料表**] 對話方塊-以滑鼠右鍵按一下 [圖表] 窗格中的 [開啟區域]，然後按一下 [**尋找資料表**]。</span><span class="sxs-lookup"><span data-stu-id="f457a-141">Use the **Find Table** dialog box- Right-click on open area in the Diagram pane and click **Find Table**.</span></span> <span data-ttu-id="f457a-142">或者，按一下工具列上的 **[尋找資料表]** 命令或 **[資料來源檢視]** 功能表。</span><span class="sxs-lookup"><span data-stu-id="f457a-142">Or, click the **Find Table** command on the toolbar or the **Data Source View** menu.</span></span>  
  
     <span data-ttu-id="f457a-143">您可以在 [篩選] 方塊中輸入字串和萬用字元，來檢視圖表中的資料表子集。</span><span class="sxs-lookup"><span data-stu-id="f457a-143">You can type strings and wildcard characters in the Filter box to view subsets of the tables in the diagram.</span></span>  
  
##  <a name="arrange-objects-in-a-diagram"></a><a name="bkmk_arrangeobjects"></a><span data-ttu-id="f457a-144">排列圖表中的物件</span><span class="sxs-lookup"><span data-stu-id="f457a-144">Arrange Objects in a Diagram</span></span>  
 <span data-ttu-id="f457a-145">雖然資料來源檢視設計工具可以定義多個圖表，讓 DSV 更容易了解，但包含太多資料表的圖表就很難閱讀，且手動重新排列資料表配置又是一件耗時的工作。</span><span class="sxs-lookup"><span data-stu-id="f457a-145">Although Data Source View Designer can define multiple diagrams to make a DSV more understandable, diagrams that contain dozens of tables can be hard to read and manually rearranging table layouts is a tedious process.</span></span> <span data-ttu-id="f457a-146">資料來源檢視設計師可以根據目前圖表中資料表之間的關聯性，使用矩形或對角線配置，來自動重新排列目前圖表中的資料表。</span><span class="sxs-lookup"><span data-stu-id="f457a-146">The Data Source View Designer can automatically rearrange tables in the current diagram using either a rectangular or diagonal layout based on the relationships between tables in the current diagram.</span></span>  
  
-   <span data-ttu-id="f457a-147">在矩形配置中，關聯性線條是在資料表之間而非資料行之間繪製。</span><span class="sxs-lookup"><span data-stu-id="f457a-147">In a rectangular layout, the relationship lines are drawn between tables instead of between columns.</span></span> <span data-ttu-id="f457a-148">關聯性線條會水平及垂直地繪製在資料表之間。</span><span class="sxs-lookup"><span data-stu-id="f457a-148">Relationship lines are drawn horizontally and vertically between tables.</span></span>  
  
-   <span data-ttu-id="f457a-149">在對角線配置中，關聯性線條會盡可能直接繪製在資料表的相關資料行之間。</span><span class="sxs-lookup"><span data-stu-id="f457a-149">In a diagonal layout, relationship lines are drawn as directly as possible between related columns in tables.</span></span> <span data-ttu-id="f457a-150">多個資料行的關聯性會附加至資料表中的第一個相關資料行。</span><span class="sxs-lookup"><span data-stu-id="f457a-150">A relationship to multiple columns attaches to the first related column in the table.</span></span> <span data-ttu-id="f457a-151">如果看不到資料表中的資料行，則線條會繪製在資料表頂端。</span><span class="sxs-lookup"><span data-stu-id="f457a-151">If the columns in a table are not visible, the lines are drawn to the top of the table.</span></span>  
  
##  <a name="preserve-object-arrangement"></a><a name="bkmk_preserve"></a><span data-ttu-id="f457a-152">保留物件相片順序</span><span class="sxs-lookup"><span data-stu-id="f457a-152">Preserve object arrangement</span></span>  
 <span data-ttu-id="f457a-153">依照所要的方式手動排列資料表之後，將更多資料表加入至圖表可能會造成圖表重新整理，而移除您對物件配置的最近修改。</span><span class="sxs-lookup"><span data-stu-id="f457a-153">After manually arranging tables the way you want, adding more tables to the diagram can result in a diagram refresh that removes any recent modifications you made to the object layout.</span></span>  
  
 <span data-ttu-id="f457a-154">當您加入資料表時，導致 [圖表組合管理] 移動其他資料表以容納新資料表，可能會發生這種行為。</span><span class="sxs-lookup"><span data-stu-id="f457a-154">This behavior is more likely to occur when you add a table, causing the Diagram Organizer to move other tables in order to accommodate the new one.</span></span> <span data-ttu-id="f457a-155">然後它會重新繪製圖表，確保所有資料表和連接線正確表示。</span><span class="sxs-lookup"><span data-stu-id="f457a-155">It then redraws the diagram to ensure all tables and connection lines represented correctly.</span></span> <span data-ttu-id="f457a-156">此時，對特定物件位置的所有手動調整可能會遺失。</span><span class="sxs-lookup"><span data-stu-id="f457a-156">At this point, any manual adjustments to the placement of specific objects might be lost.</span></span>  
  
 <span data-ttu-id="f457a-157">若要避免這個問題，請先加入所有資料表，然後進行最後調整。</span><span class="sxs-lookup"><span data-stu-id="f457a-157">To avoid this problem, add all the tables first, before making any final adjustments.</span></span> <span data-ttu-id="f457a-158">當您稍後重新開啟圖表時，物件現在應該會保留其圖表中的位置。</span><span class="sxs-lookup"><span data-stu-id="f457a-158">Objects should now retain their position in the diagram when you open it again later.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f457a-159">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f457a-159">See Also</span></span>  
 <span data-ttu-id="f457a-160">[多維度模型中的資料來源視圖](data-source-views-in-multidimensional-models.md) </span><span class="sxs-lookup"><span data-stu-id="f457a-160">[Data Source Views in Multidimensional Models](data-source-views-in-multidimensional-models.md) </span></span>  
 [<span data-ttu-id="f457a-161">資料來源檢視設計工具 &#40;Analysis Services - 多維度資料&#41;</span><span class="sxs-lookup"><span data-stu-id="f457a-161">Data Source View Designer &#40;Analysis Services - Multidimensional Data&#41;</span></span>](../data-source-view-designer-analysis-services-multidimensional-data.md)  
  
  
