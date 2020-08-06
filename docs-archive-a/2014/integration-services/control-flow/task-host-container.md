---
title: 工作主機容器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.taskhostcontainer.f1
helpviewer_keywords:
- containers [Integration Services], Task Host
- Task Host container
ms.assetid: 7394a2c2-1b07-427d-b94a-9792e7783d35
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4429d564cea0f08d5c2408199a8f1837b38389b0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599124"
---
# <a name="task-host-container"></a><span data-ttu-id="bb86e-102">工作主機容器</span><span class="sxs-lookup"><span data-stu-id="bb86e-102">Task Host Container</span></span>
  <span data-ttu-id="bb86e-103">工作主機容器會封裝單一工作。</span><span class="sxs-lookup"><span data-stu-id="bb86e-103">The task host container encapsulates a single task.</span></span> <span data-ttu-id="bb86e-104">在 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師中，工作主機不會另外設定，而是在您設定其封裝之工作的屬性時設定。</span><span class="sxs-lookup"><span data-stu-id="bb86e-104">In [!INCLUDE[ssIS](../../includes/ssis-md.md)] Designer, the task host is not configured separately; instead, it is configured when you set the properties of the task it encapsulates.</span></span> <span data-ttu-id="bb86e-105">如需工作主機容器所封裝工作的詳細資訊，請參閱 [Integration Services 工作](integration-services-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="bb86e-105">For more information about the tasks that the task host containers encapsulate, see [Integration Services Tasks](integration-services-tasks.md).</span></span>  
  
 <span data-ttu-id="bb86e-106">此容器會將變數與事件處理常式的使用延伸至工作層級。</span><span class="sxs-lookup"><span data-stu-id="bb86e-106">This container extends the use of variables and event handlers to the task level.</span></span> <span data-ttu-id="bb86e-107">如需詳細資訊，請參閱 [Integration Services &#40;SSIS&#41; 事件處理常式](../integration-services-ssis-event-handlers.md)和 [Integration Services &#40;SSIS&#41; 變數](../integration-services-ssis-variables.md)。</span><span class="sxs-lookup"><span data-stu-id="bb86e-107">For more information, see [Integration Services &#40;SSIS&#41; Event Handlers](../integration-services-ssis-event-handlers.md) and [Integration Services &#40;SSIS&#41; Variables](../integration-services-ssis-variables.md).</span></span>  
  
## <a name="configuration-of-the-task-host"></a><span data-ttu-id="bb86e-108">設定工作主機</span><span class="sxs-lookup"><span data-stu-id="bb86e-108">Configuration of the Task Host</span></span>  
 <span data-ttu-id="bb86e-109">您可以在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的 [屬性] 視窗中，或以程式設計方式設定屬性。</span><span class="sxs-lookup"><span data-stu-id="bb86e-109">You can set properties in the **Properties** window of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or programmatically.</span></span>  
  
 <span data-ttu-id="bb86e-110">如需在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中設定這些屬性的相關資訊，請參閱 [設定工作或容器的屬性](../set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="bb86e-110">For information about setting these properties in [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
 <span data-ttu-id="bb86e-111">如需以程式設計方式設定這些屬性的詳細資訊，請參閱 <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>。</span><span class="sxs-lookup"><span data-stu-id="bb86e-111">For information about programmatically setting these properties, see <xref:Microsoft.SqlServer.Dts.Runtime.TaskHost>.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="bb86e-112">相關工作</span><span class="sxs-lookup"><span data-stu-id="bb86e-112">Related Tasks</span></span>  
  
-   [<span data-ttu-id="bb86e-113">設定工作或容器的屬性</span><span class="sxs-lookup"><span data-stu-id="bb86e-113">Set the Properties of a Task or Container</span></span>](../set-the-properties-of-a-task-or-container.md)  
  
## <a name="see-also"></a><span data-ttu-id="bb86e-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bb86e-114">See Also</span></span>  
 [<span data-ttu-id="bb86e-115">Integration Services 容器</span><span class="sxs-lookup"><span data-stu-id="bb86e-115">Integration Services Containers</span></span>](integration-services-containers.md)  
  
  
