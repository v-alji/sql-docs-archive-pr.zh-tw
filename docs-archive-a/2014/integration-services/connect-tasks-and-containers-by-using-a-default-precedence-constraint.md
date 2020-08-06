---
title: 使用預設的優先順序條件約束來連接工作和容器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- tasks [Integration Services], precedence constraints
- precedence constraints [Integration Services], connecting tasks
- default precedence constraints
- containers [Integration Services], precedence constraints
ms.assetid: 8f31f15f-98ff-4c35-b41f-8b8cfd148d75
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 00207172babdb41b1030e77e71a2c8bc3b99799d
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87706650"
---
# <a name="connect-tasks-and-containers-by-using-a-default-precedence-constraint"></a><span data-ttu-id="3b65b-102">使用預設的優先順序條件約束來連接工作和容器</span><span class="sxs-lookup"><span data-stu-id="3b65b-102">Connect Tasks and Containers by Using a Default Precedence Constraint</span></span>
  <span data-ttu-id="3b65b-103">優先順序條件約束可以連接兩個可執行檔。</span><span class="sxs-lookup"><span data-stu-id="3b65b-103">Precedence constraints connect two executables.</span></span> <span data-ttu-id="3b65b-104">可執行檔可以是任何工作或「For 迴圈」、「Foreach 迴圈」或「時序」容器。</span><span class="sxs-lookup"><span data-stu-id="3b65b-104">An executable can be any task or a For Loop, Foreach Loop, or Sequence container.</span></span> <span data-ttu-id="3b65b-105">此程序描述如何設定優先順序條件約束的預設行為，及如何使用預設的優先順序條件約束來連接可執行檔。</span><span class="sxs-lookup"><span data-stu-id="3b65b-105">This procedure describes how to set the default behavior for precedence constraints, and how to connect executables using the default precedence constraints.</span></span>  
  
## <a name="creating-default-precedence-constraints"></a><span data-ttu-id="3b65b-106">建立預設的優先順序條件約束</span><span class="sxs-lookup"><span data-stu-id="3b65b-106">Creating Default Precedence Constraints</span></span>  
 <span data-ttu-id="3b65b-107">首次使用「[!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師」時，優先順序條件約束的預設值為 `Success`。</span><span class="sxs-lookup"><span data-stu-id="3b65b-107">When you first use [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, the default value of a precedence constraint is `Success`.</span></span> <span data-ttu-id="3b65b-108">請遵循下列步驟來設定「 [!INCLUDE[ssIS](../includes/ssis-md.md)] 設計師」，以便使用優先順序條件約束的其他預設值。</span><span class="sxs-lookup"><span data-stu-id="3b65b-108">Follow these steps to configure [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer to use a different default value for precedence constraints.</span></span>  
  
#### <a name="to-set-the-default-value-for-precedence-constraints"></a><span data-ttu-id="3b65b-109">設定優先順序條件約束的預設值</span><span class="sxs-lookup"><span data-stu-id="3b65b-109">To set the default value for precedence constraints</span></span>  
  
1.  <span data-ttu-id="3b65b-110">開啟 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]。</span><span class="sxs-lookup"><span data-stu-id="3b65b-110">Open [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)].</span></span>  
  
2.  <span data-ttu-id="3b65b-111">在 **[工具]** 功能表上，按一下 **[選項]** 。</span><span class="sxs-lookup"><span data-stu-id="3b65b-111">On the **Tools** menu, click **Options**.</span></span>  
  
3.  <span data-ttu-id="3b65b-112">在 [選項]\*\*\*\* 對話方塊中，展開 [商業智慧設計師]\*\*\*\*，然後展開 [Integration Services 設計師]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3b65b-112">In the **Options** dialog box, expand **Business Intelligence Designers,** and then expand **Integration Services Designers**.</span></span>  
  
4.  <span data-ttu-id="3b65b-113">按一下 [控制流程自動連接]\*\*\*\*，然後選取 [依預設，將新形狀連接到選取的形狀]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3b65b-113">Click **Control Flow Auto Connect** and select **Connect a new shape to the selected shape by default**.</span></span>  
  
5.  <span data-ttu-id="3b65b-114">在下拉式清單中，選擇 [在新形狀使用「失敗」條件約束]\*\*\*\* 或 [在新形狀使用「完成」條件約束]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="3b65b-114">In the drop-down list, choose either **Use a Failure constraint for the new shape** or **Use a Completion constraint for the new shape**.</span></span>  
  
6.  <span data-ttu-id="3b65b-115">按一下 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="3b65b-115">Click **OK**.</span></span>  
  
#### <a name="to-create-a-default-precedence-constraint"></a><span data-ttu-id="3b65b-116">建立預設的優先順序條件約束</span><span class="sxs-lookup"><span data-stu-id="3b65b-116">To create a default precedence constraint</span></span>  
  
1.  <span data-ttu-id="3b65b-117">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="3b65b-117">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="3b65b-118">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="3b65b-118">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="3b65b-119">按一下 **[控制流程]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="3b65b-119">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="3b65b-120">在 [控制流程]\*\*\*\* 索引標籤的設計介面上，按一下工作或容器，然後將其連接子拖曳到您要套用優先順序條件約束的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="3b65b-120">On the design surface of the **Control Flow** tab, click the task or container and drag its connector to the executable to which you want the precedence constraint to apply.</span></span>  
  
5.  <span data-ttu-id="3b65b-121">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="3b65b-121">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b65b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3b65b-122">See Also</span></span>  
 <span data-ttu-id="3b65b-123">[優先順序條件約束](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="3b65b-123">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="3b65b-124">[使用快捷方式功能表來設定優先順序條件約束的值](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span><span class="sxs-lookup"><span data-stu-id="3b65b-124">[Set the Value of a Precedence Constraint by Using the Shortcut Menu](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span></span>  
 <span data-ttu-id="3b65b-125">[設定優先順序條件約束的屬性](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="3b65b-125">[Set the Properties of a Precedence Constraint](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md) </span></span>  
 [<span data-ttu-id="3b65b-126">在優先順序條件約束中使用運算式</span><span class="sxs-lookup"><span data-stu-id="3b65b-126">Use an Expression in a Precedence Constraint</span></span>](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  
