---
title: 在優先順序條件約束中使用運算式 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- precedence constraints [Integration Services], adding expressions
- expressions [Integration Services], adding
ms.assetid: 601038bb-3b17-42ac-b09d-5b3a82fb6564
author: chugugrace
ms.author: chugu
ms.openlocfilehash: a997efa448a8381cc8251cd4cbf69dc59f8968e1
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87701287"
---
# <a name="use-an-expression-in-a-precedence-constraint"></a><span data-ttu-id="eea4c-102">在優先順序條件約束中使用運算式</span><span class="sxs-lookup"><span data-stu-id="eea4c-102">Use an Expression in a Precedence Constraint</span></span>
  <span data-ttu-id="eea4c-103">此程序描述如何使用 [優先順序條件約束編輯器]\*\*\*\* 對話方塊，將運算式加入優先順序條件約束。</span><span class="sxs-lookup"><span data-stu-id="eea4c-103">This procedure describes how to add an expression to a precedence constraint by using the **Precedence Constraint Editor** dialog box.</span></span> <span data-ttu-id="eea4c-104">封裝必須包括至少兩個可執行檔 (工作或容器)，且這兩個可執行檔必須由優先順序條件約束連接，您才可以將運算式加入優先順序條件約束。</span><span class="sxs-lookup"><span data-stu-id="eea4c-104">Before you can add an expression to a precedence constraint, the package must include at least two executables, either tasks or containers, and they must be connected by a precedence constraint.</span></span>  
  
### <a name="to-add-an-expression-to-a-precedence-constraint"></a><span data-ttu-id="eea4c-105">將運算式加入優先順序條件約束</span><span class="sxs-lookup"><span data-stu-id="eea4c-105">To add an expression to a precedence constraint</span></span>  
  
1.  <span data-ttu-id="eea4c-106">在 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]中，開啟包含所需封裝的 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 專案。</span><span class="sxs-lookup"><span data-stu-id="eea4c-106">In [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)], open the [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] project that contains the package you want.</span></span>  
  
2.  <span data-ttu-id="eea4c-107">在 [方案總管] 中，按兩下封裝將其開啟。</span><span class="sxs-lookup"><span data-stu-id="eea4c-107">In Solution Explorer, double-click the package to open it.</span></span>  
  
3.  <span data-ttu-id="eea4c-108">按一下 **[控制流程]** 索引標籤。</span><span class="sxs-lookup"><span data-stu-id="eea4c-108">Click the **Control Flow** tab.</span></span>  
  
4.  <span data-ttu-id="eea4c-109">在 [控制流程]\*\*\*\* 索引標籤的設計介面上，按兩下優先順序條件約束。</span><span class="sxs-lookup"><span data-stu-id="eea4c-109">On the design surface of the **Control Flow** tab, double-click the precedence constraint.</span></span> <span data-ttu-id="eea4c-110">[優先順序條件約束編輯器]\*\*\*\* 隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="eea4c-110">The **Precedence Constraint Editor** opens.</span></span>  
  
5.  <span data-ttu-id="eea4c-111">在 [評估作業]\*\*\*\* 清單中，選取 [運算式]\*\*\*\*、[運算式與條件約束]\*\*\*\* 或 [運算式或條件約束]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="eea4c-111">Select **Expression**, **Expression and Constraint**, or **Expression or Constraint** in the **Evaluation operation** list.</span></span>  
  
6.  <span data-ttu-id="eea4c-112">在 [運算式]\*\*\*\* 文字方塊中輸入運算式，或啟動運算式產生器以建立運算式。</span><span class="sxs-lookup"><span data-stu-id="eea4c-112">Type an expression in the **Expression** text box or launch the Expression Builder to create an expression.</span></span>  
  
7.  <span data-ttu-id="eea4c-113">若要驗證運算式語法，請按一下 [測試]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="eea4c-113">To validate the expression syntax, click **Test**.</span></span>  
  
8.  <span data-ttu-id="eea4c-114">若要儲存已更新的封裝，請在 **[檔案]** 功能表上，按一下 **[儲存選取項目]** 。</span><span class="sxs-lookup"><span data-stu-id="eea4c-114">To save the updated package, click **Save Selected Items** on the **File** menu.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eea4c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="eea4c-115">See Also</span></span>  
 <span data-ttu-id="eea4c-116">[優先順序條件約束](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="eea4c-116">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="eea4c-117">[使用預設的優先順序條件約束來連接工作和容器](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="eea4c-117">[Connect Tasks and Containers by Using a Default Precedence Constraint](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md) </span></span>  
 <span data-ttu-id="eea4c-118">[使用快捷方式功能表來設定優先順序條件約束的值](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span><span class="sxs-lookup"><span data-stu-id="eea4c-118">[Set the Value of a Precedence Constraint by Using the Shortcut Menu](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md) </span></span>  
 <span data-ttu-id="eea4c-119">[設定優先順序條件約束的屬性](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md) </span><span class="sxs-lookup"><span data-stu-id="eea4c-119">[Set the Properties of a Precedence Constraint](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md) </span></span>  
 [<span data-ttu-id="eea4c-120">Integration Services &#40;SSIS&#41; 運算式</span><span class="sxs-lookup"><span data-stu-id="eea4c-120">Integration Services &#40;SSIS&#41; Expressions</span></span>](expressions/integration-services-ssis-expressions.md)  
  
  
