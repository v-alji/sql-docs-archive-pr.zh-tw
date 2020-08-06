---
title: 複製封裝物件 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- control flow [Integration Services], copying objects
- copying package objects [Integration Services]
- data flow [Integration Services], copying objects
- connection managers [Integration Services], copying
ms.assetid: 99b85e5c-d6bd-4e7c-afe4-51f6ce151c2f
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 3219f0023c9a28ed270adeb6fd2b795e3459c3e0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593501"
---
# <a name="copy-package-objects"></a><span data-ttu-id="e1a67-102">複製封裝物件</span><span class="sxs-lookup"><span data-stu-id="e1a67-102">Copy Package Objects</span></span>
  <span data-ttu-id="e1a67-103">此主題描述如何在某個封裝內或兩個封裝之間複製控制流程項目、資料流程項目和連接管理員。</span><span class="sxs-lookup"><span data-stu-id="e1a67-103">This topic describes how to copy control flow items, data flow items, and connection managers within a package or between packages.</span></span>  
  
### <a name="to-copy-control-and-data-flow-items"></a><span data-ttu-id="e1a67-104">若要複製控制和資料流程項目</span><span class="sxs-lookup"><span data-stu-id="e1a67-104">To copy control and data flow items</span></span>  
  
1.  <span data-ttu-id="e1a67-105">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含要使用之封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="e1a67-105">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the packages that you want work with.</span></span>  
  
2.  <span data-ttu-id="e1a67-106">在 [方案總管] 中，按兩下您要在其間進行複製的封裝。</span><span class="sxs-lookup"><span data-stu-id="e1a67-106">In Solution Explorer, double-click the packages that you want to copy between.</span></span>  
  
3.  <span data-ttu-id="e1a67-107">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師中，按一下內含欲複製項目之封裝的索引標籤，然後按一下 [控制流程]  、[資料流程]  或 [事件處理常式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e1a67-107">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the tab for the package that contains the items to copy and click the **Control Flow**, **Data Flow**, or **Event Handlers** tab.</span></span>  
  
4.  <span data-ttu-id="e1a67-108">選取要複製的控制流程或資料流程項目。</span><span class="sxs-lookup"><span data-stu-id="e1a67-108">Select the control flow or data flow items to copy.</span></span> <span data-ttu-id="e1a67-109">您可以按住 Shift 鍵再按一下項目，逐一選取項目，也可以拖曳指標使其跨越您想選取的項目，以群組方式選項項目。</span><span class="sxs-lookup"><span data-stu-id="e1a67-109">You can either select items one at a time by pressing the Shift key and clicking the item or select items as a group by dragging the pointer across the items you want to select.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e1a67-110">當您選取優先順序條件約束和路徑連接的兩個項目時，並不會自動選取連接項目的這些優先順序條件約束和路徑。</span><span class="sxs-lookup"><span data-stu-id="e1a67-110">The precedence constraints and paths that connect items are not selected automatically when you select the two items that they connect.</span></span> <span data-ttu-id="e1a67-111">若要複製已排序的工作流程 (也就是控制流程或資料流程的區段)，請務必同時複製優先順序條件約束和路徑。</span><span class="sxs-lookup"><span data-stu-id="e1a67-111">To copy an ordered workflow-a segment of control flow or data flow-make sure to also copy the precedence constrains and the paths.</span></span>  
  
5.  <span data-ttu-id="e1a67-112">以滑鼠右鍵按一下選取的項目，然後按一下 [複製]  。</span><span class="sxs-lookup"><span data-stu-id="e1a67-112">Right-click a selected item and click **Copy**.</span></span>  
  
6.  <span data-ttu-id="e1a67-113">若要將項目複製到不同的封裝，請按一下要複製到其中的封裝，然後按一下適用於項目類型的索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e1a67-113">If copying items to a different package, click the package that you want to copy to, and then click the appropriate tab for the item type.</span></span>  
  
    > [!IMPORTANT]  
    >  <span data-ttu-id="e1a67-114">除非封裝中包含至少一項「資料流程」工作，否則您就不能將資料流程複製到封裝中。</span><span class="sxs-lookup"><span data-stu-id="e1a67-114">You cannot copy a data flow to a package unless the package contains at least one Data Flow task.</span></span>  
  
7.  <span data-ttu-id="e1a67-115">按一下滑鼠右鍵，並按一下 [貼上]  。</span><span class="sxs-lookup"><span data-stu-id="e1a67-115">Right-click and click **Paste**.</span></span>  
  
### <a name="to-copy-connection-managers"></a><span data-ttu-id="e1a67-116">若要複製連接管理員</span><span class="sxs-lookup"><span data-stu-id="e1a67-116">To copy connection managers</span></span>  
  
1.  <span data-ttu-id="e1a67-117">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含要處理之封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="e1a67-117">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package that you want to work with.</span></span>  
  
2.  <span data-ttu-id="e1a67-118">在 [方案總管] 中，按兩下封裝。</span><span class="sxs-lookup"><span data-stu-id="e1a67-118">In Solution Explorer, double-click the package.</span></span>  
  
3.  <span data-ttu-id="e1a67-119">在 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師中，按一下 [控制流程]  、[資料流程]  或 [事件處理常式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e1a67-119">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, click the **Control Flow**, **Data Flow**, or **Event Handler** tab.</span></span>  
  
4.  <span data-ttu-id="e1a67-120">在 [連線管理員]  區域中，以滑鼠右鍵按一下連線管理員，然後按一下 [複製]  。</span><span class="sxs-lookup"><span data-stu-id="e1a67-120">In the **Connection Managers** area, right-click the connection manager, and then click **Copy**.</span></span> <span data-ttu-id="e1a67-121">您一次僅能複製一個連接管理員。</span><span class="sxs-lookup"><span data-stu-id="e1a67-121">You can copy only one connection manager at a time.</span></span>  
  
5.  <span data-ttu-id="e1a67-122">若要將項目複製到不同的封裝，請按一下要複製到其中的封裝，然後按一下 [控制流程]  、[資料流程]  或 [事件處理常式]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="e1a67-122">If you are copying items to a different package, click the package that you want to copy to and then click the **Control Flow**, **Data Flow**, or **Event Handler** tab.</span></span>  
  
6.  <span data-ttu-id="e1a67-123">以滑鼠右鍵按一下 [連線管理員]  區域，然後按一下 [貼上]  。</span><span class="sxs-lookup"><span data-stu-id="e1a67-123">Right-click in the **Connection Managers** area and click **Paste**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1a67-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e1a67-124">See Also</span></span>  
 <span data-ttu-id="e1a67-125">[控制流程](control-flow/control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="e1a67-125">[Control Flow](control-flow/control-flow.md) </span></span>  
 <span data-ttu-id="e1a67-126">[資料流程](data-flow/data-flow.md) </span><span class="sxs-lookup"><span data-stu-id="e1a67-126">[Data Flow](data-flow/data-flow.md) </span></span>  
 <span data-ttu-id="e1a67-127">[Integration Services &#40;SSIS&#41; 連線](connection-manager/integration-services-ssis-connections.md) </span><span class="sxs-lookup"><span data-stu-id="e1a67-127">[Integration Services &#40;SSIS&#41; Connections](connection-manager/integration-services-ssis-connections.md) </span></span>  
 [<span data-ttu-id="e1a67-128">複製專案項目</span><span class="sxs-lookup"><span data-stu-id="e1a67-128">Copy Project Items</span></span>](../../2014/integration-services/copy-project-items.md)  
  
  
