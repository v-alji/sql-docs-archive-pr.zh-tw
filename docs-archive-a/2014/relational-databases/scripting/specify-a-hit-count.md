---
title: 指定叫用計數
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
f1_keywords:
- vs.debug.breakpt.hitcount
helpviewer_keywords:
- Transact-SQL debugger, breakpoint hit count
ms.assetid: 24836939-94ed-4e57-aa85-5d6938d859e4
author: rothja
ms.author: jroth
ms.openlocfilehash: 34c75e990bce1ea5e64c0b45f7acbcaa52fc3c40
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598269"
---
# <a name="specify-a-hit-count"></a><span data-ttu-id="0af3d-102">指定叫用計數</span><span class="sxs-lookup"><span data-stu-id="0af3d-102">Specify a Hit Count</span></span>
  <span data-ttu-id="0af3d-103">中斷點叫用次數是每次到達中斷點時由 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具遞增的計數器。</span><span class="sxs-lookup"><span data-stu-id="0af3d-103">A breakpoint hit count is a counter that is incremented by the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger each time the breakpoint is reached.</span></span> <span data-ttu-id="0af3d-104">如果已到達指定的叫用計數而且滿足任何指定的中斷點條件時，偵錯工具就會執行為中斷點指定的動作。</span><span class="sxs-lookup"><span data-stu-id="0af3d-104">If the specified hit count is reached and any specified breakpoint condition is satisfied, the debugger performs the action specified for the breakpoint.</span></span>  
  
## <a name="hit-count-considerations"></a><span data-ttu-id="0af3d-105">叫用次數考量</span><span class="sxs-lookup"><span data-stu-id="0af3d-105">Hit Count Considerations</span></span>  
 <span data-ttu-id="0af3d-106">根據預設，每次叫用中斷點時，執行就會中斷。</span><span class="sxs-lookup"><span data-stu-id="0af3d-106">By default, execution breaks every time a breakpoint is hit.</span></span> <span data-ttu-id="0af3d-107">您可以選擇下列其中一個選項：</span><span class="sxs-lookup"><span data-stu-id="0af3d-107">You can choose between the following options:</span></span>  
  
-   <span data-ttu-id="0af3d-108">永遠中斷 (預設值)。</span><span class="sxs-lookup"><span data-stu-id="0af3d-108">Break always (the default).</span></span>  
  
-   <span data-ttu-id="0af3d-109">當叫用次數等於指定的值時中斷。</span><span class="sxs-lookup"><span data-stu-id="0af3d-109">Break when the hit count equals a specified value.</span></span>  
  
-   <span data-ttu-id="0af3d-110">當叫用次數倍數於指定的值時中斷。</span><span class="sxs-lookup"><span data-stu-id="0af3d-110">Break when the hit count equals a multiple of a specified value.</span></span>  
  
-   <span data-ttu-id="0af3d-111">當叫用次數大於或等於指定的值時中斷。</span><span class="sxs-lookup"><span data-stu-id="0af3d-111">Break when the hit count is greater than or equal to a specified value.</span></span>  
  
 <span data-ttu-id="0af3d-112">中斷點叫用次數會在偵錯工作階段的範圍內遞增。</span><span class="sxs-lookup"><span data-stu-id="0af3d-112">Breakpoint hit counts are incremented within the scope of a debugging session.</span></span> <span data-ttu-id="0af3d-113">在每個偵錯工作階段啟動時，所有叫用次數都設定為零。</span><span class="sxs-lookup"><span data-stu-id="0af3d-113">All hit counts are set to zero at the start of each debugging session.</span></span>  
  
 <span data-ttu-id="0af3d-114">如果您想要追蹤中斷點的叫用次數，而不讓中斷點中斷執行，請使用非常高的值來指定叫用次數，如此中斷點就絕對不會中斷。</span><span class="sxs-lookup"><span data-stu-id="0af3d-114">If you want to track how many times a breakpoint is hit without having the breakpoint break execution, specify a hit count with a very high value so the breakpoint never breaks.</span></span>  
  
 <span data-ttu-id="0af3d-115">中斷點的預設動作是在已滿足叫用計數和中斷點條件時中斷執行。</span><span class="sxs-lookup"><span data-stu-id="0af3d-115">The default action for a breakpoint is to break execution when both the hit count and breakpoint condition have been satisfied.</span></span> <span data-ttu-id="0af3d-116">如需指定其他動作的資訊，請參閱 [指定中斷點動作](specify-a-breakpoint-action.md)。</span><span class="sxs-lookup"><span data-stu-id="0af3d-116">For information about specifying other actions, see [Specify a Breakpoint Action](specify-a-breakpoint-action.md).</span></span>  
  
#### <a name="to-specify-a-hit-count"></a><span data-ttu-id="0af3d-117">若要指定叫用次數</span><span class="sxs-lookup"><span data-stu-id="0af3d-117">To Specify a Hit Count</span></span>  
  
1.  <span data-ttu-id="0af3d-118">在編輯器視窗中，以滑鼠右鍵按一下中斷點字符，然後按一下捷徑功能表上的 [叫用次數]  。</span><span class="sxs-lookup"><span data-stu-id="0af3d-118">In the editor window, right-click the breakpoint glyph, and then click **Hit Count** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="0af3d-119">-或-</span><span class="sxs-lookup"><span data-stu-id="0af3d-119">-or-</span></span>  
  
     <span data-ttu-id="0af3d-120">在 [中斷點]  視窗中，以滑鼠右鍵按一下中斷點字符，然後按一下捷徑功能表上的 [叫用次數]  。</span><span class="sxs-lookup"><span data-stu-id="0af3d-120">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Hit Count** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="0af3d-121">在 **[中斷點叫用次數]** 對話方塊的 **[當叫用中斷點時]** 方塊中，選取所要的行為。</span><span class="sxs-lookup"><span data-stu-id="0af3d-121">In the **Breakpoint Hit Count** dialog box, select the behavior you want from the **When the breakpoint is hit** box.</span></span>  
  
     <span data-ttu-id="0af3d-122">如果您選擇 **[永遠中斷]** 以外的任何設定，清單右側就會顯示一個文字方塊。</span><span class="sxs-lookup"><span data-stu-id="0af3d-122">If you choose any setting other than **Break Always**, a text box appears to the right of the list.</span></span> <span data-ttu-id="0af3d-123">請在此文字方塊中輸入整數，以便指定所要的叫用次數。</span><span class="sxs-lookup"><span data-stu-id="0af3d-123">Enter an integer in the text box to specify the hit count you want.</span></span>  
  
3.  <span data-ttu-id="0af3d-124">按一下 **[確定]** 實作變更，或按一下 **[取消]** 結束而不套用變更。</span><span class="sxs-lookup"><span data-stu-id="0af3d-124">Click **OK** to implement the changes, or **Cancel** to exit without applying the changes.</span></span>  
  
#### <a name="to-view-or-reset-the-current-hit-count"></a><span data-ttu-id="0af3d-125">若要檢視或重設目前叫用次數</span><span class="sxs-lookup"><span data-stu-id="0af3d-125">To View or Reset the Current Hit Count</span></span>  
  
1.  <span data-ttu-id="0af3d-126">在編輯器視窗中，以滑鼠右鍵按一下中斷點字符，然後按一下捷徑功能表上的 [叫用次數]  。</span><span class="sxs-lookup"><span data-stu-id="0af3d-126">In the editor window, right-click the breakpoint glyph, and then click **Hit Count** on the shortcut menu.</span></span>  
  
     <span data-ttu-id="0af3d-127">-或-</span><span class="sxs-lookup"><span data-stu-id="0af3d-127">-or-</span></span>  
  
     <span data-ttu-id="0af3d-128">在 [中斷點]  視窗中，以滑鼠右鍵按一下中斷點字符，然後按一下捷徑功能表上的 [叫用次數]  。</span><span class="sxs-lookup"><span data-stu-id="0af3d-128">In the **Breakpoints** window, right-click the breakpoint glyph, and then click **Hit Count** on the shortcut menu.</span></span>  
  
2.  <span data-ttu-id="0af3d-129">在 **[中斷點叫用次數]** 對話方塊中， **[目前叫用次數:]** 就會顯示在 **[重設]** 按鈕的正上方。</span><span class="sxs-lookup"><span data-stu-id="0af3d-129">In the **Breakpoint Hit Count** dialog box, the **Current hit count:** is displayed just above the **Reset** button.</span></span>  
  
3.  <span data-ttu-id="0af3d-130">如果您想要將目前叫用次數設定為零，請按一下 **[重設]** 。</span><span class="sxs-lookup"><span data-stu-id="0af3d-130">Click **Reset** if you want to set the current hit count to zero.</span></span>  
  
4.  <span data-ttu-id="0af3d-131">按一下 **[確定]** 或 **[取消]** 結束對話方塊。</span><span class="sxs-lookup"><span data-stu-id="0af3d-131">Click **OK** or **Cancel** to exit the dialog.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0af3d-132">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0af3d-132">See Also</span></span>  
 [<span data-ttu-id="0af3d-133">指定中斷點條件</span><span class="sxs-lookup"><span data-stu-id="0af3d-133">Specify a Breakpoint Condition</span></span>](specify-a-breakpoint-condition.md)  
  
  
