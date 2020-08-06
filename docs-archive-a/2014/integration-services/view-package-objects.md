---
title: 檢視套件物件 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Integration Services packages, properties
- properties [Integration Services]
- Package Explorer window [Integration Services]
- packages [Integration Services], properties
- explorer view [Integration Services]
- SSIS packages, properties
- viewing package objects
- SQL Server Integration Services packages, properties
ms.assetid: a85c0245-0a68-4eb0-83b1-9b11df80bd10
author: chugugrace
ms.author: chugu
ms.openlocfilehash: ffe46be35db26186f715b18ba6114732d130e02e
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597900"
---
# <a name="view-package-objects"></a><span data-ttu-id="a6d99-102">檢視封裝物件</span><span class="sxs-lookup"><span data-stu-id="a6d99-102">View Package Objects</span></span>
  <span data-ttu-id="a6d99-103">在「[!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師」中，[封裝總管]  索引標籤提供封裝的總管檢視。</span><span class="sxs-lookup"><span data-stu-id="a6d99-103">In [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the **Package Explorer** tab provides an explorer view of the package.</span></span> <span data-ttu-id="a6d99-104">此檢視反映 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 架構的容器階層。</span><span class="sxs-lookup"><span data-stu-id="a6d99-104">The view reflects the container hierarchy of the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] architecture.</span></span> <span data-ttu-id="a6d99-105">封裝容器位於階層的頂端，您可以展開封裝以檢視其中的連接、可執行檔、事件處理常式、記錄提供者、優先順序條件約束和變數。</span><span class="sxs-lookup"><span data-stu-id="a6d99-105">The package container is at the top of the hierarchy, and you expand the package to view the connections, executables, event handlers, log providers, precedence constraints, and variables in the package.</span></span>

 <span data-ttu-id="a6d99-106">可執行檔 (封裝中的容器和工作) 可包含事件處理常式、優先順序條件約束和變數。</span><span class="sxs-lookup"><span data-stu-id="a6d99-106">The executables, which are the containers and tasks in the package, can include event handlers, precedence constraints, and variables.</span></span> [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="a6d99-107">支援容器的巢狀階層，而「For 迴圈」、「Foreach 迴圈」和「時序」容器可包含其他可執行檔。</span><span class="sxs-lookup"><span data-stu-id="a6d99-107">supports a nested hierarchy of containers, and the For Loop, Foreach Loop, and Sequence containers can include other executables.</span></span>

 <span data-ttu-id="a6d99-108">如果某個封裝包含資料流程，封裝總管  會列出「資料流程」工作，並包含一個列出資料流程元件的 [元件]  資料夾。</span><span class="sxs-lookup"><span data-stu-id="a6d99-108">If a package includes a data flow, the **Package Explorer** lists the Data Flow task and includes a **Components** folder that lists the data flow components.</span></span>

 <span data-ttu-id="a6d99-109">藉由 [封裝總管]  索引標籤，您可以刪除封裝中的物件並存取 [屬性]  視窗以檢視物件屬性。</span><span class="sxs-lookup"><span data-stu-id="a6d99-109">From the **Package Explorer** tab, you can delete objects in a package and access the **Properties** window to view object properties.</span></span>

 <span data-ttu-id="a6d99-110">下圖顯示簡單封裝的樹狀檢視。</span><span class="sxs-lookup"><span data-stu-id="a6d99-110">The following diagram shows a tree view of a simple package.</span></span>

 <span data-ttu-id="a6d99-111">![[套件總管] 索引標籤的螢幕擷取畫面](media/packageexplorer.gif "[套件總管] 索引標籤的螢幕擷取畫面")</span><span class="sxs-lookup"><span data-stu-id="a6d99-111">![Screenshot of the Package Explorer tab](media/packageexplorer.gif "Screenshot of the Package Explorer tab")</span></span>

### <a name="to-view-package-content"></a><span data-ttu-id="a6d99-112">檢視封裝內容</span><span class="sxs-lookup"><span data-stu-id="a6d99-112">To view package content</span></span>

-   [<span data-ttu-id="a6d99-113">在封裝總管中檢視封裝物件</span><span class="sxs-lookup"><span data-stu-id="a6d99-113">View Package Objects in Package Explorer</span></span>](../../2014/integration-services/view-package-objects-in-package-explorer.md)

## <a name="see-also"></a><span data-ttu-id="a6d99-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a6d99-114">See Also</span></span>
 <span data-ttu-id="a6d99-115">[Integration Services 工作](control-flow/integration-services-tasks.md) [Integration Services 容器](control-flow/integration-services-containers.md)[優先順序條件約束](control-flow/precedence-constraints.md) [Integration Services &#40;Ssis&#41; 變數](integration-services-ssis-variables.md)Integration Services &#40;ssis&#41;[事件處理常式](integration-services-ssis-event-handlers.md)Integration Services &#40;[ssis&#41; 記錄](performance/integration-services-ssis-logging.md)</span><span class="sxs-lookup"><span data-stu-id="a6d99-115">[Integration Services Tasks](control-flow/integration-services-tasks.md) [Integration Services Containers](control-flow/integration-services-containers.md) [Precedence Constraints](control-flow/precedence-constraints.md) [Integration Services &#40;SSIS&#41; Variables](integration-services-ssis-variables.md) [Integration Services &#40;SSIS&#41; Event Handlers](integration-services-ssis-event-handlers.md) [Integration Services &#40;SSIS&#41; Logging](performance/integration-services-ssis-logging.md)</span></span>


