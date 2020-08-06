---
title: '[事件處理常式] 索引標籤 |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.eventhandlerwindow.f1
ms.assetid: 94fc8916-8032-490c-b9d5-ded8b6217e49
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a5f25a9b0d602a3189feab797b7ef9c333decabb
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596811"
---
# <a name="event-handlers-tab"></a><span data-ttu-id="cf4b6-102">事件處理常式索引標籤</span><span class="sxs-lookup"><span data-stu-id="cf4b6-102">Event Handlers Tab</span></span>
  <span data-ttu-id="cf4b6-103">使用 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師的 [事件處理常式]  索引標籤，即可在 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 封裝中建立控制流程。</span><span class="sxs-lookup"><span data-stu-id="cf4b6-103">Use the **Event Handlers** tab of [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to build a control flow in an [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] package.</span></span> <span data-ttu-id="cf4b6-104">執行事件處理常式以回應封裝所引發的事件，或回應封裝中的工作或容器所引發生的事件。</span><span class="sxs-lookup"><span data-stu-id="cf4b6-104">An event handler runs in response to an event raised by the package or by a task or container in the package.</span></span>  
  
## <a name="options"></a><span data-ttu-id="cf4b6-105">選項。</span><span class="sxs-lookup"><span data-stu-id="cf4b6-105">Options</span></span>  
 <span data-ttu-id="cf4b6-106">**可執行檔**</span><span class="sxs-lookup"><span data-stu-id="cf4b6-106">**Executable**</span></span>  
 <span data-ttu-id="cf4b6-107">選取要建立事件處理常式的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="cf4b6-107">Select the executable for which you want to build an event handler.</span></span> <span data-ttu-id="cf4b6-108">可執行檔可以是封裝，或封裝中的工作或容器。</span><span class="sxs-lookup"><span data-stu-id="cf4b6-108">The executable can be the package, or a task or containers in the package.</span></span>  
  
 <span data-ttu-id="cf4b6-109">**事件處理常式**</span><span class="sxs-lookup"><span data-stu-id="cf4b6-109">**Event handler**</span></span>  
 <span data-ttu-id="cf4b6-110">選取事件處理常式的類型。</span><span class="sxs-lookup"><span data-stu-id="cf4b6-110">Select a type of event handler.</span></span> <span data-ttu-id="cf4b6-111">從 [工具箱]  拖曳項目來建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="cf4b6-111">Create the event handler by dragging items from the **Toolbox**.</span></span>  
  
 <span data-ttu-id="cf4b6-112">**刪除**</span><span class="sxs-lookup"><span data-stu-id="cf4b6-112">**Delete**</span></span>  
 <span data-ttu-id="cf4b6-113">選取事件處理常式，然後按一下 [刪除]  即可從封裝中移除它。</span><span class="sxs-lookup"><span data-stu-id="cf4b6-113">Select an event handler, and remove it from the package by clicking **Delete**.</span></span>  
  
 <span data-ttu-id="cf4b6-114">**按一下此處，即可針對可執行檔 \<executable name> 建立 \<event handler name>**</span><span class="sxs-lookup"><span data-stu-id="cf4b6-114">**Click here to create an \<event handler name> for the executable \<executable name>**</span></span>  
 <span data-ttu-id="cf4b6-115">按一下即可建立事件處理常式。</span><span class="sxs-lookup"><span data-stu-id="cf4b6-115">Click to create the event handler.</span></span>  
  
 <span data-ttu-id="cf4b6-116">從 [工具箱]  中，將代表 [!INCLUDE[ssIS](../includes/ssis-md.md)] 工作和容器的圖形物件拖曳至 [事件處理常式]  索引標籤的設計介面來建立控制流程，然後使用優先順序條件約束以定義它們執行的順序來連接物件。</span><span class="sxs-lookup"><span data-stu-id="cf4b6-116">Create the control flow by dragging graphical objects that represent [!INCLUDE[ssIS](../includes/ssis-md.md)] tasks and containers from the **Toolbox** to the design surface of the **Event Handlers** tab, and then connecting the objects by using precedence constraints to define the sequence in which they run.</span></span>  
  
 <span data-ttu-id="cf4b6-117">此外，若要加入註解，請以滑鼠右鍵按一下設計介面，然後在功能表上，按一下 [加入註解]  。</span><span class="sxs-lookup"><span data-stu-id="cf4b6-117">Additionally, to add annotations, right-click the design surface, and then on the menu, click **Add Annotation**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf4b6-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf4b6-118">See Also</span></span>  
 <span data-ttu-id="cf4b6-119">[Integration Services &#40;SSIS&#41; 事件處理常式](integration-services-ssis-event-handlers.md) </span><span class="sxs-lookup"><span data-stu-id="cf4b6-119">[Integration Services &#40;SSIS&#41; Event Handlers](integration-services-ssis-event-handlers.md) </span></span>  
 <span data-ttu-id="cf4b6-120">[控制流程](control-flow/control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="cf4b6-120">[Control Flow](control-flow/control-flow.md) </span></span>  
 <span data-ttu-id="cf4b6-121">[SSIS 設計師](ssis-designer.md) </span><span class="sxs-lookup"><span data-stu-id="cf4b6-121">[SSIS Designer](ssis-designer.md) </span></span>  
 [<span data-ttu-id="cf4b6-122">Integration Services &#40;SSIS&#41; 事件處理常式</span><span class="sxs-lookup"><span data-stu-id="cf4b6-122">Integration Services &#40;SSIS&#41; Event Handlers</span></span>](integration-services-ssis-event-handlers.md)  
  
  
