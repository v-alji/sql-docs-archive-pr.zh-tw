---
title: 指定中斷點條件
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, breakpoint conditions
ms.assetid: b43d8a2b-99a3-4fb7-8848-99c042ea7ef7
author: rothja
ms.author: jroth
ms.openlocfilehash: 659b6ca1149eb8f0412efbe2adbaf4c1ffce59d8
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87702673"
---
# <a name="specify-a-breakpoint-condition"></a><span data-ttu-id="4ec9f-102">指定中斷點條件</span><span class="sxs-lookup"><span data-stu-id="4ec9f-102">Specify a Breakpoint Condition</span></span>
  <span data-ttu-id="4ec9f-103">中斷點條件是指偵錯工具在到達中斷點時所評估的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 運算式。</span><span class="sxs-lookup"><span data-stu-id="4ec9f-103">A breakpoint condition is a [!INCLUDE[tsql](../../includes/tsql-md.md)] expression that is evaluated by the debugger when the breakpoint is reached.</span></span> <span data-ttu-id="4ec9f-104">如果已滿足條件，而且到達任何指定的叫用次數，偵錯工具就會中斷或執行為中斷點指定的動作。</span><span class="sxs-lookup"><span data-stu-id="4ec9f-104">If the condition is satisfied and any specified hit count reached, the debugger either breaks or performs the action specified for the breakpoint.</span></span>  
  
## <a name="specifying-conditions"></a><span data-ttu-id="4ec9f-105">指定條件</span><span class="sxs-lookup"><span data-stu-id="4ec9f-105">Specifying Conditions</span></span>  
 <span data-ttu-id="4ec9f-106">指定的運算式必須是評估為布林值的有效 Transact-SQL 運算式。</span><span class="sxs-lookup"><span data-stu-id="4ec9f-106">The expression specified must be a valid Transact-SQL expression that evaluates to a Boolean value.</span></span> <span data-ttu-id="4ec9f-107">如需詳細資訊，請參閱[運算式 &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql)。</span><span class="sxs-lookup"><span data-stu-id="4ec9f-107">For more information, see [Expressions &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/expressions-transact-sql).</span></span>  
  
 <span data-ttu-id="4ec9f-108">如果您指定了具有無效語法的中斷點條件，就會立即顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="4ec9f-108">If you specify a breakpoint condition with invalid syntax, a warning message appears immediately.</span></span> <span data-ttu-id="4ec9f-109">如果您指定了具有有效語法但無效語意的條件，就會在第一次叫用中斷點時顯示警告訊息。</span><span class="sxs-lookup"><span data-stu-id="4ec9f-109">If you specify a condition with valid syntax but invalid semantics, a warning message is displayed the first time the breakpoint is hit.</span></span> <span data-ttu-id="4ec9f-110">在任何一種情況中，偵錯工具都會在叫用無效的中斷點時中斷執行。</span><span class="sxs-lookup"><span data-stu-id="4ec9f-110">In either case, the debugger breaks execution when the invalid breakpoint is hit.</span></span>  
  
#### <a name="to-specify-a-condition"></a><span data-ttu-id="4ec9f-111">若要指定條件</span><span class="sxs-lookup"><span data-stu-id="4ec9f-111">To Specify a Condition</span></span>  
  
1.  <span data-ttu-id="4ec9f-112">在編輯器視窗中，以滑鼠右鍵按一下中斷點圖像，然後按一下快速鍵功能表上的 [條件]  。</span><span class="sxs-lookup"><span data-stu-id="4ec9f-112">In the editor window, right-click the breakpoint glyph, and then click **Condition** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="4ec9f-113">-或-</span><span class="sxs-lookup"><span data-stu-id="4ec9f-113">-or-</span></span>  
  
     <span data-ttu-id="4ec9f-114">在 [中斷點]  視窗中，以滑鼠右鍵按一下中斷點圖像，然後按一下快速鍵功能表上的 [條件]  。</span><span class="sxs-lookup"><span data-stu-id="4ec9f-114">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Condition** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="4ec9f-115">在 [中斷點條件]  對話方塊的 [條件]  方塊中，輸入有效的布林值運算式。</span><span class="sxs-lookup"><span data-stu-id="4ec9f-115">In the **Breakpoint Condition** dialog box, enter a valid Boolean expression in the **Condition** box.</span></span>  
  
3.  <span data-ttu-id="4ec9f-116">如果您想要在運算式評估為時中斷，請選擇 [**是 true** ] `true` ，如果您想要在運算式的值變更時中斷，請選擇 [**已變更**]。</span><span class="sxs-lookup"><span data-stu-id="4ec9f-116">Choose **Is true** if you want to break when the expression evaluates to `true`, or choose **Has changed** if you want to break when the value of the expression has changed.</span></span>  
  
    > [!NOTE]  
    >  <span data-ttu-id="4ec9f-117">在第一次到達中斷點之前，偵錯工具不會評估布林運算式。</span><span class="sxs-lookup"><span data-stu-id="4ec9f-117">The debugger does not evaluate the Boolean expression until the first time the breakpoint is reached.</span></span> <span data-ttu-id="4ec9f-118">如果您選擇 [已變更]  ，偵錯工具不會將第一次評估視為變更，因此偵錯工具不會在第一次評估時中斷。</span><span class="sxs-lookup"><span data-stu-id="4ec9f-118">If you choose **Has changed**, the debugger does not consider the first evaluation to be a change, so the debugger will not break on the first evaluation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ec9f-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ec9f-119">See Also</span></span>  
 <span data-ttu-id="4ec9f-120">[指定叫用計數](specify-a-hit-count.md) </span><span class="sxs-lookup"><span data-stu-id="4ec9f-120">[Specify a Hit Count](specify-a-hit-count.md) </span></span>  
 [<span data-ttu-id="4ec9f-121">指定中斷點動作</span><span class="sxs-lookup"><span data-stu-id="4ec9f-121">Specify a Breakpoint Action</span></span>](specify-a-breakpoint-action.md)  
