---
title: 多個優先順序條件約束 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- multiple precedence constraints
- precedence executables [Integration Services]
- precedence constraints [Integration Services], multiple
- constrained executables [Integration Services]
ms.assetid: 71c53ead-3d19-4bc1-aafd-e5b32595b420
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 16fefbbf886818989131710876564fc9e147a56a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87596098"
---
# <a name="multiple-precedence-constraints"></a><span data-ttu-id="9e125-102">多個優先順序條件約束</span><span class="sxs-lookup"><span data-stu-id="9e125-102">Multiple Precedence Constraints</span></span>
  <span data-ttu-id="9e125-103">優先順序條件約束會連接兩個可執行檔：兩個工作、兩個容器，或一個工作和一個容器。</span><span class="sxs-lookup"><span data-stu-id="9e125-103">A precedence constraint connects two executables: two tasks, two containers, or one of each.</span></span> <span data-ttu-id="9e125-104">其稱為優先順序可執行檔與受條件約束的可執行檔。</span><span class="sxs-lookup"><span data-stu-id="9e125-104">They are known as the precedence executable and the constrained executable.</span></span> <span data-ttu-id="9e125-105">條件約束可執行檔可包含多個優先順序條件約束。</span><span class="sxs-lookup"><span data-stu-id="9e125-105">A constrained executable can have multiple precedence constraints.</span></span> <span data-ttu-id="9e125-106">如需詳細資訊，請參閱 [優先順序條件約束](control-flow/precedence-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="9e125-106">For more information, see [Precedence Constraints](control-flow/precedence-constraints.md).</span></span>  
  
 <span data-ttu-id="9e125-107">藉由群組條件約束來組裝複雜的條件約束案例，可讓您在封裝中實作複雜的控制流程。</span><span class="sxs-lookup"><span data-stu-id="9e125-107">Assembling complex constraint scenarios by grouping constraints enables you to implement complex control flow in packages.</span></span> <span data-ttu-id="9e125-108">例如，在下圖中，工作 D 按 `Success` 條件約束連結到工作 A、按 `Failure` 條件約束連結到工作 B，同時按 `Success` 條件約束連結到工作 C。</span><span class="sxs-lookup"><span data-stu-id="9e125-108">For example, in the following illustration, Task D is linked to Task A by a `Success` constraint, Task D is linked to Task B by a `Failure` constraint, and Task D is linked to Task C by a `Success` constraint.</span></span> <span data-ttu-id="9e125-109">工作 D 與工作 A、工作 D 與工作 B，以及工作 D 與工作 C 之間的優先順序條件約束會參與邏輯 *and* 關聯性。</span><span class="sxs-lookup"><span data-stu-id="9e125-109">The precedence constraints between Task D and Task A, between Task D and Task B, and between Task D and Task C participate in a logical *and* relationship.</span></span> <span data-ttu-id="9e125-110">因此，工作 A 必須成功執行、工作 B 必須失敗，而且工作 C 必須成功執行，才可以執行工作 D。</span><span class="sxs-lookup"><span data-stu-id="9e125-110">Therefore, for Task D to run, Task A must run successfully, Task B must fail, and Task C must run successfully.</span></span>  
  
 <span data-ttu-id="9e125-111">![優先順序條件約束所連結的工作](media/precedenceconstraints.gif "優先順序條件約束所連結的工作")</span><span class="sxs-lookup"><span data-stu-id="9e125-111">![Tasks linked by precedence constraints](media/precedenceconstraints.gif "Tasks linked by precedence constraints")</span></span>  
  
## <a name="logicaland-property"></a><span data-ttu-id="9e125-112">LogicalAnd 屬性</span><span class="sxs-lookup"><span data-stu-id="9e125-112">LogicalAnd Property</span></span>  
 <span data-ttu-id="9e125-113">如果工作或容器具有多個條件約束，則 `LogicalAnd` 屬性會指定是只評估優先順序條件約束，還是同時評估其他條件約束。</span><span class="sxs-lookup"><span data-stu-id="9e125-113">If a task or a container has multiple constraints, the `LogicalAnd` property specifies whether a precedence constraint is evaluated singly or in concert with other constraints.</span></span>  
  
 <span data-ttu-id="9e125-114">您可以 `LogicalAnd` 使用 [設計師] 中的 [**優先順序條件約束編輯器**] [!INCLUDE[ssIS](../includes/ssis-md.md)] ，或在提供的屬性視窗中設定屬性 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] 。</span><span class="sxs-lookup"><span data-stu-id="9e125-114">You can set the `LogicalAnd` property using the **Precedence Constraint Editor** in [!INCLUDE[ssIS](../includes/ssis-md.md)] Designer, or in the Properties window that [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] provides.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="9e125-115">相關工作</span><span class="sxs-lookup"><span data-stu-id="9e125-115">Related Tasks</span></span>  
 [<span data-ttu-id="9e125-116">設定優先順序條件約束的屬性</span><span class="sxs-lookup"><span data-stu-id="9e125-116">Set the Properties of a Precedence Constraint</span></span>](../../2014/integration-services/set-the-properties-of-a-precedence-constraint.md)  
  
  
