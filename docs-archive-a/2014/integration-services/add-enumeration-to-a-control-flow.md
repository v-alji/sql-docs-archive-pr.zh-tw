---
title: 將列舉新增至控制流程 |Microsoft Docs
ms.custom: ''
ms.date: 08/22/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- adding enumerations
- Foreach Loop containers
- control flow [Integration Services], enumerations
- repeating workflows
- enumerations [Integration Services]
ms.assetid: f212b5fb-3cc4-422e-9b7c-89eb769a812a
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 59b8569880fdf1a49f5f2ca1f6841841f9790af6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87595249"
---
# <a name="add-enumeration-to-a-control-flow"></a><span data-ttu-id="188ff-102">將列舉加入控制流程</span><span class="sxs-lookup"><span data-stu-id="188ff-102">Add Enumeration to a Control Flow</span></span>
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] <span data-ttu-id="188ff-103">包括 Foreach 迴圈容器，該容器為控制流程項目，可簡化在套件的控制流程中包括列舉檔案及物件的迴圈建構。</span><span class="sxs-lookup"><span data-stu-id="188ff-103">includes the Foreach Loop container, a control flow element that makes it simple to include a looping construct that enumerates files and objects in the control flow of a package.</span></span> <span data-ttu-id="188ff-104">如需詳細資訊，請參閱 [Foreach 迴圈容器](control-flow/foreach-loop-container.md)＞。</span><span class="sxs-lookup"><span data-stu-id="188ff-104">For more information, see [Foreach Loop Container](control-flow/foreach-loop-container.md).</span></span>  
  
 <span data-ttu-id="188ff-105">「Foreach 迴圈」容器不提供功能，僅提供可在其中建立可重複控制流程、指定列舉類型並設定列舉值的結構。</span><span class="sxs-lookup"><span data-stu-id="188ff-105">The Foreach Loop container provides no functionality; it provides only the structure in which you build the repeatable control flow, specify an enumerator type, and configure the enumerator.</span></span> <span data-ttu-id="188ff-106">若要提供容器功能，必須在「Foreach 迴圈」容器中至少包括一個工作。</span><span class="sxs-lookup"><span data-stu-id="188ff-106">To provide container functionality, you must include at least one task in the Foreach Loop container.</span></span> <span data-ttu-id="188ff-107">如需詳細資訊，請參閱 [Integration Services Tasks](control-flow/integration-services-tasks.md)。</span><span class="sxs-lookup"><span data-stu-id="188ff-107">For more information, see [Integration Services Tasks](control-flow/integration-services-tasks.md).</span></span>  
  
 <span data-ttu-id="188ff-108">「Foreach 迴圈」容器可以包括具有多個工作的控制流程及其他容器。</span><span class="sxs-lookup"><span data-stu-id="188ff-108">The Foreach Loop container can include a control flow with multiple tasks and other containers.</span></span> <span data-ttu-id="188ff-109">將工作及容器加入「Foreach 迴圈」容器與將它們加入封裝類似，只是您要將工作及容器拖曳至「Foreach 迴圈」容器而不是封裝。</span><span class="sxs-lookup"><span data-stu-id="188ff-109">Adding tasks and containers to a Foreach Loop container is similar to adding them to a package, except you drag the tasks and containers to the Foreach Loop container instead of to the package.</span></span> <span data-ttu-id="188ff-110">如果「Foreach 迴圈」容器包含一個以上的工作或容器，則您可以如同在封裝中所做的一樣，使用優先順序條件約束來連接它們。</span><span class="sxs-lookup"><span data-stu-id="188ff-110">If the Foreach Loop container includes more than one task or container, you can connect them using precedence constraints just as you do in a package.</span></span> <span data-ttu-id="188ff-111">如需詳細資訊，請參閱 [優先順序條件約束](control-flow/precedence-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="188ff-111">For more information, see [Precedence Constraints](control-flow/precedence-constraints.md).</span></span>  
  
### <a name="to-implement-a-foreach-loop-container-in-a-control-flow"></a><span data-ttu-id="188ff-112">在控制流程中實作 Foreach 迴圈容器</span><span class="sxs-lookup"><span data-stu-id="188ff-112">To implement a Foreach Loop container in a control flow</span></span>  
  
1.  <span data-ttu-id="188ff-113">將「Foreach 迴圈」容器加入封裝。</span><span class="sxs-lookup"><span data-stu-id="188ff-113">Add the Foreach Loop container to the package.</span></span> <span data-ttu-id="188ff-114">如需詳細資訊，請參閱[在控制流程中加入或刪除工作或容器](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span><span class="sxs-lookup"><span data-stu-id="188ff-114">For more information, see [Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span></span>  
  <span data-ttu-id="188ff-115">.</span><span class="sxs-lookup"><span data-stu-id="188ff-115">.</span></span>  
  
2.  <span data-ttu-id="188ff-116">將工作和容器加入「Foreach 迴圈」容器。</span><span class="sxs-lookup"><span data-stu-id="188ff-116">Add tasks and containers to the Foreach Loop container.</span></span> <span data-ttu-id="188ff-117">如需詳細資訊，請參閱[在控制流程中加入或刪除工作或容器](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span><span class="sxs-lookup"><span data-stu-id="188ff-117">For more information, see [Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md)</span></span>  
  <span data-ttu-id="188ff-118">.</span><span class="sxs-lookup"><span data-stu-id="188ff-118">.</span></span>  
  
3.  <span data-ttu-id="188ff-119">使用優先順序條件約束連接「Foreach 迴圈」容器中的工作和容器。</span><span class="sxs-lookup"><span data-stu-id="188ff-119">Connect tasks and containers in the Foreach Loop container using precedence constraints.</span></span> <span data-ttu-id="188ff-120">如需詳細資訊，請參閱 [使用預設的優先順序條件約束來連接工作和容器](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)。</span><span class="sxs-lookup"><span data-stu-id="188ff-120">For more information, see [Connect Tasks and Containers by Using a Default Precedence Constraint](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md).</span></span>  
  
4.  <span data-ttu-id="188ff-121">設定「Foreach 迴圈」容器。</span><span class="sxs-lookup"><span data-stu-id="188ff-121">Configure the Foreach Loop container.</span></span> <span data-ttu-id="188ff-122">如需詳細資訊，請參閱 [設定 Foreach 迴圈容器](../../2014/integration-services/configure-a-foreach-loop-container.md)＞。</span><span class="sxs-lookup"><span data-stu-id="188ff-122">For more information, see [Configure a Foreach Loop Container](../../2014/integration-services/configure-a-foreach-loop-container.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="188ff-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="188ff-123">See Also</span></span>  
 <span data-ttu-id="188ff-124">[在控制流程中加入或刪除工作或容器](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="188ff-124">[Add or Delete a Task or a Container in a Control Flow](control-flow/add-or-delete-a-task-or-a-container-in-a-control-flow.md) </span></span>  
 <span data-ttu-id="188ff-125">[將元件分組或取消群組](group-or-ungroup-components.md) </span><span class="sxs-lookup"><span data-stu-id="188ff-125">[Group or Ungroup Components](group-or-ungroup-components.md) </span></span>  
 <span data-ttu-id="188ff-126">[優先順序條件約束](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="188ff-126">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="188ff-127">[將反復專案新增至控制流程](add-iteration-to-a-control-flow.md) </span><span class="sxs-lookup"><span data-stu-id="188ff-127">[Add Iteration to a Control Flow](add-iteration-to-a-control-flow.md) </span></span>  
 [<span data-ttu-id="188ff-128">控制流程</span><span class="sxs-lookup"><span data-stu-id="188ff-128">Control Flow</span></span>](control-flow/control-flow.md)  
  
  
