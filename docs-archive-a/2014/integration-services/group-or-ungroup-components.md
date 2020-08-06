---
title: 將元件分組或取消分組 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- grouping containers
- tasks [Integration Services], grouping
- containers [Integration Services], grouping
- grouping tasks
ms.assetid: 34320838-c271-4f8c-90b3-1254690890bb
author: chugugrace
ms.author: chugu
ms.openlocfilehash: f6811dffca41a12fe0afeeeb334e0107ac127c12
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87592128"
---
# <a name="group-or-ungroup-components"></a><span data-ttu-id="b91e4-102">將元件分組或取消分組</span><span class="sxs-lookup"><span data-stu-id="b91e4-102">Group or Ungroup Components</span></span>
  <span data-ttu-id="b91e4-103">**設計師中的**[控制流程] **、** [資料流程] **和** [事件處理常式] [!INCLUDE[ssIS](../includes/ssis-md.md)] 索引標籤都支援可摺疊的群組。</span><span class="sxs-lookup"><span data-stu-id="b91e4-103">The **Control Flow**, **Data Flow**, and **Event Handlers** tabs in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer supports collapsible grouping.</span></span> <span data-ttu-id="b91e4-104">如果封裝具有許多元件，這些索引標籤可能會變得十分擁擠，因而難以同時檢視所有元件並找到您要使用的項目。</span><span class="sxs-lookup"><span data-stu-id="b91e4-104">If a package has many components, the tabs can become crowded, making it difficult to view all the components at one time and to locate the item with which you want to work.</span></span> <span data-ttu-id="b91e4-105">可摺疊的群組功能可以節省工作介面的空間，讓您更輕易地使用大型封裝。</span><span class="sxs-lookup"><span data-stu-id="b91e4-105">The collapsible grouping feature can conserve space on the work surface and make it easier to work with large packages.</span></span>  
  
 <span data-ttu-id="b91e4-106">您可以先選取要分組的元件、將它們分組，然後視工作需要展開或摺疊群組。</span><span class="sxs-lookup"><span data-stu-id="b91e4-106">You select the components that you want to group, group them, and then expand or collapse the groups to suit your work.</span></span> <span data-ttu-id="b91e4-107">展開群組可讓您存取群組中元件的屬性。</span><span class="sxs-lookup"><span data-stu-id="b91e4-107">Expanding a group provides access to the properties of the components in the group.</span></span> <span data-ttu-id="b91e4-108">與工作和容器連接的優先順序條件約束會自動包含在群組中。</span><span class="sxs-lookup"><span data-stu-id="b91e4-108">The precedence constraints that connect tasks and containers are automatically included in the group.</span></span>  
  
 <span data-ttu-id="b91e4-109">下面是將元件分組的考量。</span><span class="sxs-lookup"><span data-stu-id="b91e4-109">The following are considerations for grouping components.</span></span>  
  
-   <span data-ttu-id="b91e4-110">若要將元件分組，控制流程、資料流程和事件處理常式必須包含多個元件。</span><span class="sxs-lookup"><span data-stu-id="b91e4-110">To group components, the control flow, data flow, or event handler must contain more than one component.</span></span>  
  
-   <span data-ttu-id="b91e4-111">群組也可以呈巢狀，這樣就能在群組中建立群組。</span><span class="sxs-lookup"><span data-stu-id="b91e4-111">Groups can also be nested, making it possible to create groups within groups.</span></span> <span data-ttu-id="b91e4-112">雖然設計介面可以實作多個非巢狀群組，不過除非群組是巢狀的，否則一個元件只能屬於一個群組。</span><span class="sxs-lookup"><span data-stu-id="b91e4-112">The design surface can implement multiple un-nested groups, but a component can belong to only one group, unless the groups are nested.</span></span>  
  
-   <span data-ttu-id="b91e4-113">儲存封裝時， [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師會儲存群組，但是群組並不會影響封裝執行。</span><span class="sxs-lookup"><span data-stu-id="b91e4-113">When a package is saved, [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer saves the grouping, but the grouping has no effect on package execution.</span></span> <span data-ttu-id="b91e4-114">將元件分組的能力是設計階段功能，不會影響封裝的執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="b91e4-114">The ability to group components is a design-time feature; it does not affect the run-time behavior of the package.</span></span>  
  
### <a name="to-group-components"></a><span data-ttu-id="b91e4-115">若要將元件分組</span><span class="sxs-lookup"><span data-stu-id="b91e4-115">To group components</span></span>  
  
1.  <span data-ttu-id="b91e4-116">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="b91e4-116">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="b91e4-117">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="b91e4-117">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="b91e4-118">按一下 **[控制流程]** 、 **[資料流程]** 或 **[事件處理常式]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b91e4-118">Click the **Control Flow**, **Data Flow**, or **Event Handlers** tab.</span></span>  
  
4.  <span data-ttu-id="b91e4-119">在索引標籤的設計介面上，選取您要分組的元件、以滑鼠右鍵按一下選取的元件，然後按一下 [群組]  。</span><span class="sxs-lookup"><span data-stu-id="b91e4-119">On the design surface of the tab, select the components you want to group, right-click a selected component, and then click **Group**.</span></span>  
  
5.  <span data-ttu-id="b91e4-120">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="b91e4-120">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
### <a name="to-ungroup-components"></a><span data-ttu-id="b91e4-121">若要取消元件的分組</span><span class="sxs-lookup"><span data-stu-id="b91e4-121">To ungroup components</span></span>  
  
1.  <span data-ttu-id="b91e4-122">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="b91e4-122">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="b91e4-123">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="b91e4-123">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="b91e4-124">按一下 **[控制流程]** 、 **[資料流程]** 或 **[事件處理常式]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="b91e4-124">Click the **Control Flow**, **Data Flow**, or **Event Handlers** tab.</span></span>  
  
4.  <span data-ttu-id="b91e4-125">在索引標籤的設計介面上，選取包含您要取消分組之元件的群組、按一下滑鼠右鍵，然後按一下 [取消群組]  。</span><span class="sxs-lookup"><span data-stu-id="b91e4-125">On the design surface of the tab, select the group that contains the component you want to ungroup, right-click, and then click **Ungroup**.</span></span>  
  
5.  <span data-ttu-id="b91e4-126">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="b91e4-126">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b91e4-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b91e4-127">See Also</span></span>  
 [<span data-ttu-id="b91e4-128">在控制流程中加入或刪除工作或容器</span><span class="sxs-lookup"><span data-stu-id="b91e4-128">Add or Delete a Task or a Container in a Control Flow</span></span>](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)  
     
 [<span data-ttu-id="b91e4-129">使用預設的優先順序條件約束來連接工作和容器</span><span class="sxs-lookup"><span data-stu-id="b91e4-129">Connect Tasks and Containers by Using a Default Precedence Constraint</span></span>](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)  
  
  
