---
title: 時序容器 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.sequencecontainer.f1
helpviewer_keywords:
- Sequence container
- grouping control flows
- containers [Integration Services], Sequence
- subset control flow [Integration Services]
ms.assetid: 7731f91e-b8b3-4d96-a0d9-73f568547cb3
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b972f923e2134363ba1b378beebebbeb1e5d6bb6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87597253"
---
# <a name="sequence-container"></a><span data-ttu-id="fcf2a-102">時序容器</span><span class="sxs-lookup"><span data-stu-id="fcf2a-102">Sequence Container</span></span>
  <span data-ttu-id="fcf2a-103">「時序」容器會定義屬於封裝控制流程子集的控制流程。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-103">The Sequence container defines a control flow that is a subset of the package control flow.</span></span> <span data-ttu-id="fcf2a-104">「時序」容器會將封裝納入多個不同的控制流程中，而各流程中包含在整個封裝控制流程內執行的一項或多項工作和容器。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-104">Sequence containers group the package into multiple separate control flows, each containing one or more tasks and containers that run within the overall package control flow.</span></span>  
  
 <span data-ttu-id="fcf2a-105">除了其他容器外，「時序」容器也可包含多個工作。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-105">The Sequence container can include multiple tasks in addition to other containers.</span></span> <span data-ttu-id="fcf2a-106">將工作和容器加入「時序」容器與將它們加入封裝相似，不同之處在於，您要將工作和容器拖曳至「時序」容器而非封裝容器。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-106">Adding tasks and containers to a Sequence container is similar to adding them to a package, except you drag the tasks and containers to the Sequence container instead of to the package container.</span></span> <span data-ttu-id="fcf2a-107">如果「時序」容器包含一個以上的工作或容器，則您可以如同在封裝中所做的一樣，使用優先順序條件約束來連接它們。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-107">If the Sequence container includes more than one task or container, you can connect them using precedence constraints just as you do in a package.</span></span> <span data-ttu-id="fcf2a-108">如需詳細資訊，請參閱 [優先順序條件約束](precedence-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-108">For more information, see [Precedence Constraints](precedence-constraints.md).</span></span>  
  
 <span data-ttu-id="fcf2a-109">使用「時序」容器有多項益處：</span><span class="sxs-lookup"><span data-stu-id="fcf2a-109">There are many benefits of using a Sequence container:</span></span>  
  
-   <span data-ttu-id="fcf2a-110">停用工作群組，以便將封裝偵錯的焦點放在封裝控制流程的子集上。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-110">Disabling groups of tasks to focus package debugging on one subset of the package control flow.</span></span>  
  
-   <span data-ttu-id="fcf2a-111">在同一個位置藉由設定「時序」容器而非個別工作的屬性，來管理多項工作的屬性。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-111">Managing properties on multiple tasks in one location by setting properties on a Sequence container instead of on the individual tasks.</span></span>  
  
     <span data-ttu-id="fcf2a-112">例如，您可以將「時序」容器的 `Disable` 屬性設定為 `True`，以停用「時序」容器中的所有工作和容器。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-112">For example, you can set the `Disable` property of the Sequence container to `True` to disable all the tasks and containers in the Sequence container.</span></span>  
  
-   <span data-ttu-id="fcf2a-113">提供一群相關工作和容器所使用變數的範圍。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-113">Providing scope for variables that a group of related tasks and containers use.</span></span>  
  
-   <span data-ttu-id="fcf2a-114">將許多工作分組，讓您可以利用收合和展開「時序」容器的方式，更輕鬆地管理工作。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-114">Grouping many tasks so you can more easily managed them by collapsing and expanding the Sequence container.</span></span>  
  
     <span data-ttu-id="fcf2a-115">您還可以建立工作群組，使用 [群組]  方塊摺疊和展開。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-115">You can also create task groups, which expand and collapse using the **Group** box.</span></span> <span data-ttu-id="fcf2a-116">不過，[群組]  方塊是設計階段的功能，不具有屬性或執行階段的行為。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-116">However, the **Group** box is a design-time feature that has no properties or run-time behavior.</span></span> <span data-ttu-id="fcf2a-117">如需詳細資訊，請參閱 [將元件分組或取消分組](../group-or-ungroup-components.md)。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-117">For more information, see [Group or Ungroup Components](../group-or-ungroup-components.md)</span></span>  
  
-   <span data-ttu-id="fcf2a-118">設定「時序」容器的交易屬性，以定義封裝控制流程子集的異動。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-118">Set a transaction attribute on the Sequence container to define a transaction for a subset of the package control flow.</span></span> <span data-ttu-id="fcf2a-119">使用這種方式，可以以更細微的層級管理交易。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-119">In this way, you can manage transactions at a more granular level.</span></span>  
  
     <span data-ttu-id="fcf2a-120">例如，如果「時序」容器包括兩項相關的工作，其中一項工作為刪除資料表中的資料，而另一項工作會將資料插入資料表中，則可設定交易，以確認刪除動作會在插入動作失敗時回復。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-120">For example, if a Sequence container includes two related tasks, one task that deletes data in a table and another task that inserts data into a table, you can configure a transaction to ensure that the delete action is rolled back if the insert action fails.</span></span> <span data-ttu-id="fcf2a-121">如需詳細資訊，請參閱 [Integration Services 交易](../integration-services-transactions.md)。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-121">For more information, see [Integration Services Transactions](../integration-services-transactions.md).</span></span>  
  
## <a name="configuration-of-the-sequence-container"></a><span data-ttu-id="fcf2a-122">設定時序容器</span><span class="sxs-lookup"><span data-stu-id="fcf2a-122">Configuration of the Sequence Container</span></span>  
 <span data-ttu-id="fcf2a-123">「時序」容器沒有自訂使用者介面，而且您只能在 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] 的 [屬性] 視窗中或利用撰寫程式的方式進行設定。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-123">The Sequence container has no custom user interface and you can configure it only in the **Properties** window of [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] or programmatically.</span></span>  
  
 <span data-ttu-id="fcf2a-124">如需以程式設計方式設定這些屬性的詳細資訊，請參閱《開發人員指南》中 **T:Microsoft.SqlServer.Dts.Runtime.Sequence** 類別的文件。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-124">For information about programmatically setting these properties, see documentation for the **T:Microsoft.SqlServer.Dts.Runtime.Sequence** class in the Developer Guide.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="fcf2a-125">相關工作</span><span class="sxs-lookup"><span data-stu-id="fcf2a-125">Related Tasks</span></span>  
 <span data-ttu-id="fcf2a-126">如需如何設定 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]中元件屬性的資訊，請參閱 [設定工作或容器的屬性](../set-the-properties-of-a-task-or-container.md)。</span><span class="sxs-lookup"><span data-stu-id="fcf2a-126">For information about how to set properties of the component in the [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], see [Set the Properties of a Task or Container](../set-the-properties-of-a-task-or-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcf2a-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcf2a-127">See Also</span></span>  
 <span data-ttu-id="fcf2a-128">[在控制流程中加入或刪除工作或容器](add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="fcf2a-128">[Add or Delete a Task or a Container in a Control Flow](add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span></span>  
 <span data-ttu-id="fcf2a-129">[使用預設的優先順序條件約束來連線工作和容器](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="fcf2a-129">[Connect Tasks and Containers by Using a Default Precedence Constraint](../connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span></span>  
 [<span data-ttu-id="fcf2a-130">Integration Services 容器</span><span class="sxs-lookup"><span data-stu-id="fcf2a-130">Integration Services Containers</span></span>](integration-services-containers.md)  
  
  
