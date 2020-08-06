---
title: Transact-SQL 偵錯工具資訊
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, Locals Window
- Transact-SQL debugger, Watch Window
- Transact-SQL debugger, Threads Window
- Transact-SQL debugger, Call Stack Window
- Transact-SQL debugger, QuickWatch
- Transact-SQL debugger, viewing information
ms.assetid: b99819cc-f388-41a1-b304-36e78ce24147
author: rothja
ms.author: jroth
ms.openlocfilehash: c51ed39f0ed5f4ffb3e1a0c0dcb307f82d10bb10
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87709117"
---
# <a name="transact-sql-debugger-information"></a><span data-ttu-id="bbec5-102">Transact-SQL 偵錯工具資訊</span><span class="sxs-lookup"><span data-stu-id="bbec5-102">Transact-SQL Debugger Information</span></span>
  <span data-ttu-id="bbec5-103">每當偵錯工具在特定的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式上暫停執行作業時，您就可以使用各種偵錯工具視窗來檢視目前的執行狀態。</span><span class="sxs-lookup"><span data-stu-id="bbec5-103">Every time that the debugger pauses execution on a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, you can use the various debugger windows to view the current execution state.</span></span>  
  
## <a name="debugger-windows"></a><span data-ttu-id="bbec5-104">偵錯工具視窗</span><span class="sxs-lookup"><span data-stu-id="bbec5-104">Debugger Windows</span></span>  
 <span data-ttu-id="bbec5-105">在偵錯工具模式中，偵錯工具會在 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 主視窗的底部開啟兩個視窗。</span><span class="sxs-lookup"><span data-stu-id="bbec5-105">In debugger mode, the debugger opens two windows at the bottom of the main [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] window.</span></span> <span data-ttu-id="bbec5-106">偵錯工具會在這兩個視窗中顯示其所有資訊。</span><span class="sxs-lookup"><span data-stu-id="bbec5-106">The debugger displays all its information in these two windows.</span></span> <span data-ttu-id="bbec5-107">每個偵錯工具視窗都具有一些可讓您選取的索引標籤，以便控制哪一組資訊要顯示在視窗中。</span><span class="sxs-lookup"><span data-stu-id="bbec5-107">Each of the debugger windows has tabs that you can select to control which set of information is displayed in the window.</span></span> <span data-ttu-id="bbec5-108">左側的偵錯工具視窗包含 [區域變數]  、[監看式 1]  、[監看式 2]  、[監看式 3]  和 [監看式 4]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bbec5-108">The left debugger window contains the **Locals**, **Watch1**, **Watch2**, **Watch3**, and **Watch4** tabs.</span></span> <span data-ttu-id="bbec5-109">右側的偵錯工具視窗包含 [呼叫堆疊]  、[執行緒]  、[中斷點]  、[命令視窗]  和 [輸出]  索引標籤。</span><span class="sxs-lookup"><span data-stu-id="bbec5-109">The right debugger window contains the **Call Stack**, **Threads**, **Breakpoints**, **Command Window**, and **Output** tabs.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="bbec5-110">先前的描述適用於偵錯工具視窗的預設位置。</span><span class="sxs-lookup"><span data-stu-id="bbec5-110">The previous descriptions apply to the default locations of the debugger windows.</span></span> <span data-ttu-id="bbec5-111">您可以拖曳索引標籤，以便在視窗之間移動它，也可以取消停駐索引標籤來建立新的視窗，以便將它放在想要的位置。</span><span class="sxs-lookup"><span data-stu-id="bbec5-111">You can drag a tab to move it from one window to another, or you can undock a tab to create a new window that you can put wherever you want.</span></span>  
  
 <span data-ttu-id="bbec5-112">根據預設，並非所有索引標籤或視窗都處於使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="bbec5-112">By default, not all of these tabs or windows are active.</span></span> <span data-ttu-id="bbec5-113">您可以使用下列其中一種方式來開啟特定視窗：</span><span class="sxs-lookup"><span data-stu-id="bbec5-113">You can open a particular window by using either of the following ways:</span></span>  
  
-   <span data-ttu-id="bbec5-114">在 [偵錯]  功能表上，按一下 [視窗]  ，然後選取您想要的視窗。</span><span class="sxs-lookup"><span data-stu-id="bbec5-114">On the **Debug** menu, click **Windows**, and then select the window you want.</span></span>  
  
-   <span data-ttu-id="bbec5-115">在 [偵錯]  工具列上，按一下 [中斷點]  ，然後選取您想要的視窗。</span><span class="sxs-lookup"><span data-stu-id="bbec5-115">On the **Debug** toolbar, click **Breakpoints**, and then select the window you want.</span></span>  
  
## <a name="transact-sql-expressions"></a><span data-ttu-id="bbec5-116">Transact-SQL 運算式</span><span class="sxs-lookup"><span data-stu-id="bbec5-116">Transact-SQL Expressions</span></span>  
 <span data-ttu-id="bbec5-117">運算式是評估成單一純量值的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 子句，例如變數或參數。</span><span class="sxs-lookup"><span data-stu-id="bbec5-117">Expressions are [!INCLUDE[tsql](../../includes/tsql-md.md)] clauses that evaluate to a single, scalar value, such as variables or parameters.</span></span> <span data-ttu-id="bbec5-118">左側的偵錯工具視窗最多可以在五個索引標籤或視窗中顯示目前指派給運算式的資料值：[區域變數]  、[監看式 1]、[監看式 2]  、[監看式 3]  和 [監看式 4]  。</span><span class="sxs-lookup"><span data-stu-id="bbec5-118">The left debugger window can display the data values that are currently assigned to expressions in up to five tabs or windows: **Locals, Watch1**, **Watch2**, **Watch3**, and **Watch4**.</span></span>  
  
 <span data-ttu-id="bbec5-119">[區域變數]  視窗會顯示有關 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具目前範圍中之區域變數的資訊。</span><span class="sxs-lookup"><span data-stu-id="bbec5-119">The **Locals** window displays information about the local variables in the current scope of the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span> <span data-ttu-id="bbec5-120">[區域變數]  視窗中所列的這組運算式會隨著偵錯工具逐步執行不同的程式碼部分而變更。</span><span class="sxs-lookup"><span data-stu-id="bbec5-120">The set of expressions that are listed in the **Locals** window changes as the debugger runs through the different parts of the code.</span></span>  
  
 <span data-ttu-id="bbec5-121">[快速監看式]  中的運算式和四個 [監看]  視窗都不限於僅列出變數的識別碼。</span><span class="sxs-lookup"><span data-stu-id="bbec5-121">The expressions in the **QuickWatch** and the four **Watch** windows are not limited to just listing the identifier of a variable.</span></span> <span data-ttu-id="bbec5-122">您可以指定評估為單一值的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 運算式，例如將數字加入變數中，或是評估為單一值的 SELECT 陳述式。</span><span class="sxs-lookup"><span data-stu-id="bbec5-122">You can specify a [!INCLUDE[tsql](../../includes/tsql-md.md)] expression that evaluates to a single value, such as adding a number to a variable, or a SELECT statement that evaluates to a single value.</span></span> <span data-ttu-id="bbec5-123">範例包括：</span><span class="sxs-lookup"><span data-stu-id="bbec5-123">Examples include:</span></span>  
  
-   <span data-ttu-id="bbec5-124">變數的名稱，例如 @IntegerCounter。</span><span class="sxs-lookup"><span data-stu-id="bbec5-124">The name of a variable, such as @IntegerCounter.</span></span>  
  
-   <span data-ttu-id="bbec5-125">變數上的算術運算，例如 @IntegerCounter + 1。</span><span class="sxs-lookup"><span data-stu-id="bbec5-125">An arithmetic operation on a variable, such as @IntegerCounter + 1.</span></span>  
  
-   <span data-ttu-id="bbec5-126">兩個字元變數的字串作業，例如 @FirstName + @LastName。</span><span class="sxs-lookup"><span data-stu-id="bbec5-126">A string operation on two character variables, such as @FirstName + @LastName.</span></span>  
  
-   <span data-ttu-id="bbec5-127">傳回單一值的 SELECT 陳述式，例如 SELECT CharCol FROM MyTable WHERE PrimaryKey = 1。</span><span class="sxs-lookup"><span data-stu-id="bbec5-127">A SELECT statement that returns a single value, such as SELECT CharCol FROM MyTable WHERE PrimaryKey = 1.</span></span>  
  
 <span data-ttu-id="bbec5-128">您可以使用 [快速監看式]  視窗來檢視 [!INCLUDE[tsql](../../includes/tsql-md.md)] 運算式的值，然後將該運算式儲存至 [監看式]  視窗。</span><span class="sxs-lookup"><span data-stu-id="bbec5-128">You can use the **QuickWatch** window to view the value of a [!INCLUDE[tsql](../../includes/tsql-md.md)] expression, and then save that expression to a **Watch** window.</span></span> <span data-ttu-id="bbec5-129">若要在 [快速監看式]  中選取運算式，請在 [運算式]  方塊中選取或輸入運算式的名稱。</span><span class="sxs-lookup"><span data-stu-id="bbec5-129">To select an expression in **QuickWatch**, either select or enter the name of the expression in the **Expression** box.</span></span>  
  
 <span data-ttu-id="bbec5-130">四個 [監看式]  視窗會顯示有關您已選取之變數和運算式的資訊。</span><span class="sxs-lookup"><span data-stu-id="bbec5-130">The four **Watch** windows display information about variables and expressions that you have selected.</span></span> <span data-ttu-id="bbec5-131">在您於清單中加入或刪除運算式之前，[監看式]  視窗中所列的這組運算式都不會變更。</span><span class="sxs-lookup"><span data-stu-id="bbec5-131">The set of expressions that are listed in the **Watch** windows does not change until you either add or delete expressions from the list.</span></span>  
  
 <span data-ttu-id="bbec5-132">若要將運算式加入至 [監看式] 視窗，您可以在 [快速監看式] 對話方塊中選取 [加入監看式]，也可以在 [監看式] 視窗中空白資料列的 [名稱] 資料行中輸入運算式的名稱。</span><span class="sxs-lookup"><span data-stu-id="bbec5-132">To add an expression to a **Watch** window, you can either select **Add Watch** in the **QuickWatch** dialog box, or enter the name of the expression in the **Name** column of an empty row in a **Watch** window.</span></span>  
  
 <span data-ttu-id="bbec5-133">您可以在 [區域變數]  、[監看式]  或 [快速監看式]  視窗中，以滑鼠右鍵按一下資料列，然後選取 [編輯值]  ，藉以設定變數的資料值。</span><span class="sxs-lookup"><span data-stu-id="bbec5-133">You can set the data values for variables in the **Locals**, **Watch**, or **QuickWatch** windows by right-clicking the row and then selecting **Edit Value**.</span></span> <span data-ttu-id="bbec5-134">[區域變數] 視窗、[監看式] 視窗和 [快速監看式] 對話方塊中的 [值] 資料行支援都文字、XML 和 HTML 資料視覺化檢視。</span><span class="sxs-lookup"><span data-stu-id="bbec5-134">The **Value** columns in the **Locals** window, **Watch** window, and **QuickWatch** dialog box all support text, XML, and HTML data visualizers.</span></span> <span data-ttu-id="bbec5-135">這些視覺化檢視是以 [值]  資料行最右邊的放大鏡資料提示表示。</span><span class="sxs-lookup"><span data-stu-id="bbec5-135">The visualizers are represented by a magnifying glass data tip on the right side end of the **Values** column.</span></span> <span data-ttu-id="bbec5-136">您可以使用這些視覺化檢視，在符合資料類型的顯示中檢視文字、XML 或 HTML 資料值，例如在瀏覽器視窗中檢視 XML 檔。</span><span class="sxs-lookup"><span data-stu-id="bbec5-136">You can use the visualizers to view text, XML, or HTML data values in displays that match the data types, for example, viewing XML files in a browser window.</span></span>  
  
 <span data-ttu-id="bbec5-137">在偵錯模式中，當您將滑鼠指標移到識別碼上方時，[快速諮詢]  快顯就會顯示運算式的名稱及其目前值。</span><span class="sxs-lookup"><span data-stu-id="bbec5-137">In debug mode, when you move the mouse pointer over an identifier, a **Quick Info** pop up is displayed with the name of the expression and its current value.</span></span> <span data-ttu-id="bbec5-138">如需詳細資訊，請參閱[快速諮詢 &#40;IntelliSense&#41;](quick-info-intellisense.md)。</span><span class="sxs-lookup"><span data-stu-id="bbec5-138">For more information, see [Quick Info &#40;IntelliSense&#41;](quick-info-intellisense.md).</span></span>  
  
## <a name="breakpoints"></a><span data-ttu-id="bbec5-139">中斷點</span><span class="sxs-lookup"><span data-stu-id="bbec5-139">Breakpoints</span></span>  
 <span data-ttu-id="bbec5-140">您可以使用 [中斷點]  視窗來檢視和管理目前已設定的中斷點。</span><span class="sxs-lookup"><span data-stu-id="bbec5-140">You can use the **Breakpoints** window to view and manage the currently set breakpoints.</span></span> <span data-ttu-id="bbec5-141">如需詳細資訊，請參閱 [逐步執行 TRANSACT-SQL 程式碼](step-through-transact-sql-code.md)。</span><span class="sxs-lookup"><span data-stu-id="bbec5-141">For more information, see [Step Through Transact-SQL Code](step-through-transact-sql-code.md).</span></span>  
  
## <a name="call-stacks"></a><span data-ttu-id="bbec5-142">呼叫堆疊</span><span class="sxs-lookup"><span data-stu-id="bbec5-142">Call Stacks</span></span>  
 <span data-ttu-id="bbec5-143">[呼叫堆疊]  視窗會顯示目前的執行位置，以及有關執行作業如何從原始編輯器視窗通過任何 [!INCLUDE[tsql](../../includes/tsql-md.md)] 模組 (函數、預存程序或觸發程序) 而到達目前執行位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="bbec5-143">The **Call Stack** window displays the current execution location, and information about how execution passed from the original editor window through any [!INCLUDE[tsql](../../includes/tsql-md.md)] modules (functions, stored procedures, or triggers) to reach the current execution location.</span></span> <span data-ttu-id="bbec5-144">[呼叫堆疊]  視窗中的每個資料列都稱為堆疊框架，而且代表下列任何一個項目：</span><span class="sxs-lookup"><span data-stu-id="bbec5-144">Each row in the **Call Stack** window is called a stack frame and represents any one of the following items:</span></span>  
  
-   <span data-ttu-id="bbec5-145">目前的執行位置。</span><span class="sxs-lookup"><span data-stu-id="bbec5-145">The current execution location.</span></span>  
  
-   <span data-ttu-id="bbec5-146">從某個模組到另一個模組的呼叫。</span><span class="sxs-lookup"><span data-stu-id="bbec5-146">A call from one module to another.</span></span>  
  
-   <span data-ttu-id="bbec5-147">從編輯器視窗到 [!INCLUDE[tsql](../../includes/tsql-md.md)] 模組的呼叫。</span><span class="sxs-lookup"><span data-stu-id="bbec5-147">A call from an editor window to a [!INCLUDE[tsql](../../includes/tsql-md.md)] module.</span></span>  
  
 <span data-ttu-id="bbec5-148">堆疊的順序與呼叫模組的順序相反。</span><span class="sxs-lookup"><span data-stu-id="bbec5-148">The order of the stack is the reverse of that in which the modules were called.</span></span> <span data-ttu-id="bbec5-149">目前的執行位置位於堆疊的頂端，而原始的呼叫則位於底部。</span><span class="sxs-lookup"><span data-stu-id="bbec5-149">The current execution location is at the top of the stack and the original call at the bottom.</span></span> <span data-ttu-id="bbec5-150">堆疊框架左邊界的黃色箭頭可識別偵錯工具暫停執行作業的所在框架。</span><span class="sxs-lookup"><span data-stu-id="bbec5-150">A yellow arrow on the left margin of the stack frame identifies the frame in which the debugger paused execution.</span></span>  
  
 <span data-ttu-id="bbec5-151">[名稱]  資料行會記錄下列資訊：</span><span class="sxs-lookup"><span data-stu-id="bbec5-151">The **Name** column records the following information:</span></span>  
  
-   <span data-ttu-id="bbec5-152">包含向下呼叫至下一層之程式碼行的來源模組。</span><span class="sxs-lookup"><span data-stu-id="bbec5-152">The source module that contains the line of code that called down to the next level.</span></span>  
  
-   <span data-ttu-id="bbec5-153">在堆疊上呼叫下一個模組的程式碼行。</span><span class="sxs-lookup"><span data-stu-id="bbec5-153">The line of code that called the next module on the stack.</span></span>  
  
-   <span data-ttu-id="bbec5-154">如果呼叫移至使用參數的預存程序或函數，就會一併列出所有參數的名稱、資料類型和值。</span><span class="sxs-lookup"><span data-stu-id="bbec5-154">If the call went to a stored procedure or function that took parameters, the names, data types, and values of all the parameters are also listed.</span></span>  
  
 <span data-ttu-id="bbec5-155">[區域變數]  、[監看式]  和 [快速監看式]  視窗中的運算式都會針對目前的堆疊框架進行評估。</span><span class="sxs-lookup"><span data-stu-id="bbec5-155">The expressions in the **Locals**, **Watch**, and **QuickWatch** windows are evaluated for the current stack frame.</span></span> <span data-ttu-id="bbec5-156">根據預設，目前的堆疊框架是堆疊中的最上層框架，也就是偵錯工具暫停執行所在的框架。</span><span class="sxs-lookup"><span data-stu-id="bbec5-156">By default, the current stack frame is the top frame in the stack, where the debugger paused execution.</span></span> <span data-ttu-id="bbec5-157">當您將其他堆疊框架指定成目前的框架時，[區域變數]  、[監看式]  和 [快速監看式]  視窗中的運算式就會針對新的堆疊框架重新評估。</span><span class="sxs-lookup"><span data-stu-id="bbec5-157">When you specify another stack frame as the current frame, the expressions in the **Locals**, **Watch**, and **QuickWatch** windows are reevaluated for the new stack frame.</span></span> <span data-ttu-id="bbec5-158">您可以按兩下框架，或按一下框架，然後選取 [切換至框架]  ，藉以變更目前的堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="bbec5-158">You can change the current stack frame by either by double-clicking a frame or clicking a frame and selecting **Switch To Frame**.</span></span> <span data-ttu-id="bbec5-159">此時，[區域變數]  、[監看式]  和 [快速監看式]  視窗中的運算式就會針對新的框架重新評估。</span><span class="sxs-lookup"><span data-stu-id="bbec5-159">At that point, the expressions in the **Locals**, **Watch**, and **QuickWatch** windows are reevaluated for the new frame.</span></span> <span data-ttu-id="bbec5-160">每當目前的堆疊框架不是堆疊中的最上層框架時，堆疊框架左邊界的綠色箭頭可識別目前的堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="bbec5-160">Whenever the current stack frame is not the top frame in the stack, a green arrow on the left margin of the stack frame identifies the current stack frame.</span></span>  
  
 <span data-ttu-id="bbec5-161">當您以滑鼠右鍵按一下堆疊框架，然後選取 [移至原始程式碼]  時，該框架的程式碼就會顯示在 [查詢編輯器] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="bbec5-161">When you right-click a stack frame and select **Go To Source Code**, the code for that frame is displayed in a Query Editor window.</span></span> <span data-ttu-id="bbec5-162">不過，該框架不會成為目前的框架，而且 [區域變數]  、[監看式]  和 [快速監看式]  視窗的內容不會變更。</span><span class="sxs-lookup"><span data-stu-id="bbec5-162">However, that frame is not made the current frame, and the contents of the **Locals**, **Watch**, and **QuickWatch** windows are not changed.</span></span>  
  
## <a name="system-information-and-transact-sql-results"></a><span data-ttu-id="bbec5-163">系統資訊和 Transact-SQL 結果</span><span class="sxs-lookup"><span data-stu-id="bbec5-163">System Information and Transact-SQL Results</span></span>  
 <span data-ttu-id="bbec5-164">偵錯工具會在 [輸出]  視窗中列出其狀態和事件訊息。</span><span class="sxs-lookup"><span data-stu-id="bbec5-164">The debugger lists its status and event messages in the **Output** window.</span></span> <span data-ttu-id="bbec5-165">這包括一些資訊，例如偵錯工具附加至其他處理序的時間，或是偵錯工具執行緒結束的時間。</span><span class="sxs-lookup"><span data-stu-id="bbec5-165">This includes information such as when the debugger attaches to other processes or when debugger threads end.</span></span>  
  
 <span data-ttu-id="bbec5-166">在偵錯模式中，[結果]  和 [訊息]  索引標籤仍然會在 [查詢編輯器] 中處於使用中狀態。</span><span class="sxs-lookup"><span data-stu-id="bbec5-166">While in debug mode, the **Results** and **Messages** tabs are still active in the Query Editor.</span></span> <span data-ttu-id="bbec5-167">[結果]  索引標籤會繼續顯示在偵錯工作階段期間執行之 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的結果集。</span><span class="sxs-lookup"><span data-stu-id="bbec5-167">The **Results** tab continues to display the result sets from the [!INCLUDE[tsql](../../includes/tsql-md.md)] statements that are executed during a debugging session.</span></span> <span data-ttu-id="bbec5-168">[訊息]  索引標籤會繼續顯示系統訊息，例如 *xx* 個資料列受影響，以及 PRINT 和 RAISERROR 陳述式的輸出。</span><span class="sxs-lookup"><span data-stu-id="bbec5-168">The **Messages** tab continues to display system messages, such as *xx* Rows Affected and the output of PRINT and RAISERROR statements.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbec5-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bbec5-169">See Also</span></span>  
 <span data-ttu-id="bbec5-170">[本機視窗](transact-sql-debugger-locals-window.md) </span><span class="sxs-lookup"><span data-stu-id="bbec5-170">[Locals Window](transact-sql-debugger-locals-window.md) </span></span>  
 <span data-ttu-id="bbec5-171">[監看式視窗](transact-sql-debugger-watch-window.md) </span><span class="sxs-lookup"><span data-stu-id="bbec5-171">[Watch Window](transact-sql-debugger-watch-window.md) </span></span>  
 <span data-ttu-id="bbec5-172">[快速監看式對話方塊](transact-sql-debugger-quickwatch-dialog-box.md) </span><span class="sxs-lookup"><span data-stu-id="bbec5-172">[QuickWatch Dialog Box](transact-sql-debugger-quickwatch-dialog-box.md) </span></span>  
 <span data-ttu-id="bbec5-173">[中斷點視窗](transact-sql-debugger-breakpoints-window.md) </span><span class="sxs-lookup"><span data-stu-id="bbec5-173">[Breakpoints Window](transact-sql-debugger-breakpoints-window.md) </span></span>  
 <span data-ttu-id="bbec5-174">[呼叫堆疊視窗](transact-sql-debugger-call-stack-window.md) </span><span class="sxs-lookup"><span data-stu-id="bbec5-174">[Call Stack Window](transact-sql-debugger-call-stack-window.md) </span></span>  
 <span data-ttu-id="bbec5-175">[執行緒視窗](transact-sql-debugger-threads-window.md) </span><span class="sxs-lookup"><span data-stu-id="bbec5-175">[Threads Window](transact-sql-debugger-threads-window.md) </span></span>  
 <span data-ttu-id="bbec5-176">[輸出視窗](transact-sql-debugger-output-window.md) </span><span class="sxs-lookup"><span data-stu-id="bbec5-176">[Output Window](transact-sql-debugger-output-window.md) </span></span>  
 [<span data-ttu-id="bbec5-177">Transact-SQL 偵錯工具</span><span class="sxs-lookup"><span data-stu-id="bbec5-177">Transact-SQL Debugger</span></span>](transact-sql-debugger.md)  
  
  
