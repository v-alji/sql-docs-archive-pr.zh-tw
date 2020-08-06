---
title: 優先順序條件約束編輯器 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.precedenceconstraint.f1
helpviewer_keywords:
- Precedence Constraint Editor dialog box
ms.assetid: b10d4330-6e35-4037-b309-ef56efcd60c5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b6853d1974f4276361d60e1d73b34c72a366a7f4
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87593427"
---
# <a name="precedence-constraint-editor"></a><span data-ttu-id="b240f-102">優先順序條件約束編輯器</span><span class="sxs-lookup"><span data-stu-id="b240f-102">Precedence Constraint Editor</span></span>
  <span data-ttu-id="b240f-103">使用 **[優先順序條件約束編輯器]** 對話方塊，即可設定優先順序條件約束。</span><span class="sxs-lookup"><span data-stu-id="b240f-103">Use the **Precedence Constraint Editor** dialog box to configure precedence constraints.</span></span>  
  
## <a name="options"></a><span data-ttu-id="b240f-104">選項</span><span class="sxs-lookup"><span data-stu-id="b240f-104">Options</span></span>  
 <span data-ttu-id="b240f-105">**評估作業**</span><span class="sxs-lookup"><span data-stu-id="b240f-105">**Evaluation operation**</span></span>  
 <span data-ttu-id="b240f-106">指定優先順序條件約束所使用的評估作業。</span><span class="sxs-lookup"><span data-stu-id="b240f-106">Specify the evaluation operation that the precedence constraint uses.</span></span> <span data-ttu-id="b240f-107">這些作業有：[條件約束]、[運算式]、[運算式與條件約束]，以及 [運算式或條件約束]。</span><span class="sxs-lookup"><span data-stu-id="b240f-107">The operations are: **Constraint**, **Expression**, **Expression and Constraint**, and **Expression or Constraint**.</span></span>  
  
 <span data-ttu-id="b240f-108">**ReplTest1**</span><span class="sxs-lookup"><span data-stu-id="b240f-108">**Value**</span></span>  
 <span data-ttu-id="b240f-109">指定條件約束值：[成功]、[失敗] 或 [完成]。</span><span class="sxs-lookup"><span data-stu-id="b240f-109">Specify the constraint value: **Success**, **Failure**, or **Completion**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b240f-110"> 優先順序條件約束線條若是綠色代表 **[成功]**，反白顯示代表 **[失敗]**，而藍色代表 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="b240f-110">The precedence constraint line is green for **Success**, highlighted for **Failure**, and blue for **Completion**.</span></span>  
  
 <span data-ttu-id="b240f-111">**運算式**</span><span class="sxs-lookup"><span data-stu-id="b240f-111">**Expression**</span></span>  
 <span data-ttu-id="b240f-112">如果使用 [運算式]\*\*\*\*、[運算式與條件約束]\*\*\*\* 或 [運算式或條件約束]\*\*\*\* 作業，請輸入運算式或啟動運算式產生器以建立運算式。</span><span class="sxs-lookup"><span data-stu-id="b240f-112">If using the operations **Expression**, **Expression and Constraint**, or **Expression or Constraint**, type an expression or launch the Expression Builder to create the expression.</span></span> <span data-ttu-id="b240f-113">運算式必須評估為布林。</span><span class="sxs-lookup"><span data-stu-id="b240f-113">The expression must evaluate to a Boolean.</span></span>  
  
 <span data-ttu-id="b240f-114">**Test**</span><span class="sxs-lookup"><span data-stu-id="b240f-114">**Test**</span></span>  
 <span data-ttu-id="b240f-115">驗證運算式。</span><span class="sxs-lookup"><span data-stu-id="b240f-115">Validate the expression.</span></span>  
  
 <span data-ttu-id="b240f-116">**邏輯 AND**</span><span class="sxs-lookup"><span data-stu-id="b240f-116">**Logical AND**</span></span>  
 <span data-ttu-id="b240f-117">選取即可指定同一個可執行檔上的多個優先順序條件約束必須一起評估。</span><span class="sxs-lookup"><span data-stu-id="b240f-117">Select to specify that multiple precedence constraints on the same executable must be evaluated together.</span></span> <span data-ttu-id="b240f-118">所有運算式都必須評估為 `True`。</span><span class="sxs-lookup"><span data-stu-id="b240f-118">All constraints must evaluate to `True`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b240f-119">此種類型的優先順序條件約束會顯示為綠色、反白顯示或藍色的實線。</span><span class="sxs-lookup"><span data-stu-id="b240f-119">This type of precedence constraint appears as a solid green, highlighted or blue line.</span></span>  
  
 <span data-ttu-id="b240f-120">**邏輯 OR**</span><span class="sxs-lookup"><span data-stu-id="b240f-120">**Logical OR**</span></span>  
 <span data-ttu-id="b240f-121">選取即可指定同一個可執行檔上的多個優先順序條件約束必須一起評估。</span><span class="sxs-lookup"><span data-stu-id="b240f-121">Select to specify that multiple precedence constraints on the same executable must be evaluated together.</span></span> <span data-ttu-id="b240f-122">必須至少有一個條件約束評估為 `True`。</span><span class="sxs-lookup"><span data-stu-id="b240f-122">At least one constraint must evaluate to `True`.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="b240f-123">此種類型的優先順序條件約束會顯示為綠色、反白顯示或藍色的虛線。</span><span class="sxs-lookup"><span data-stu-id="b240f-123">This type of precedence constraint appears as a dotted green, highlighted, or blue line.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b240f-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b240f-124">See Also</span></span>  
 <span data-ttu-id="b240f-125">[優先順序條件約束](control-flow/precedence-constraints.md) </span><span class="sxs-lookup"><span data-stu-id="b240f-125">[Precedence Constraints](control-flow/precedence-constraints.md) </span></span>  
 <span data-ttu-id="b240f-126">[Integration Services 工作](control-flow/integration-services-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="b240f-126">[Integration Services Tasks](control-flow/integration-services-tasks.md) </span></span>  
 <span data-ttu-id="b240f-127">[Integration Services 容器](control-flow/integration-services-containers.md) </span><span class="sxs-lookup"><span data-stu-id="b240f-127">[Integration Services Containers](control-flow/integration-services-containers.md) </span></span>  
 [<span data-ttu-id="b240f-128">Integration Services &#40;SSIS&#41; 運算式</span><span class="sxs-lookup"><span data-stu-id="b240f-128">Integration Services &#40;SSIS&#41; Expressions</span></span>](expressions/integration-services-ssis-expressions.md)  
  
  
