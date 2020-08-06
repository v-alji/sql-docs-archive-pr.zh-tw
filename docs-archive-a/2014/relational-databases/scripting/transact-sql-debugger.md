---
title: Transact-SQL 偵錯工具
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, introduction
ms.assetid: 6e914699-0d85-46c2-aa2d-3e339ac2c4ce
author: rothja
ms.author: jroth
ms.openlocfilehash: a4312e8ac0989664e447a6ebe1cd3f05ce750f23
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87697870"
---
# <a name="transact-sql-debugger"></a><span data-ttu-id="53c3f-102">Transact-SQL 偵錯工具</span><span class="sxs-lookup"><span data-stu-id="53c3f-102">Transact-SQL Debugger</span></span>
  <span data-ttu-id="53c3f-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具可協助您透過調查 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼的執行階段行為，找出程式碼中的錯誤。</span><span class="sxs-lookup"><span data-stu-id="53c3f-103">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger helps you find errors in [!INCLUDE[tsql](../../includes/tsql-md.md)] code by investigating the run-time behavior of the code.</span></span> <span data-ttu-id="53c3f-104">在您將 [ [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器] 視窗設定成偵錯模式之後，就可以在特定的程式碼行上暫停執行作業，然後檢查這些 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式所使用或傳回的資訊和資料。</span><span class="sxs-lookup"><span data-stu-id="53c3f-104">After you set the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window to debug mode, you can pause execution on specific lines of code and inspect information and data that is used by or returned by those [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
## <a name="stepping-through-transact-sql-code"></a><span data-ttu-id="53c3f-105">逐步執行 Transact-SQL 程式碼</span><span class="sxs-lookup"><span data-stu-id="53c3f-105">Stepping Through Transact-SQL Code</span></span>  
 <span data-ttu-id="53c3f-106">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具提供下列選項，可讓您在 [ [!INCLUDE[tsql](../../includes/tsql-md.md)] 查詢編輯器] 視窗處於偵錯模式時，逐一巡覽 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 程式碼：</span><span class="sxs-lookup"><span data-stu-id="53c3f-106">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger provides the following options that you can use to navigate through [!INCLUDE[tsql](../../includes/tsql-md.md)] code when the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window is in debug mode:</span></span>  
  
-   <span data-ttu-id="53c3f-107">在個別的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式上設定中斷點。</span><span class="sxs-lookup"><span data-stu-id="53c3f-107">Set breakpoints on individual [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
     <span data-ttu-id="53c3f-108">中斷點是指您要暫停執行以便檢查資料的點。</span><span class="sxs-lookup"><span data-stu-id="53c3f-108">A breakpoint specifies a point at which you want execution to pause so you can examine data.</span></span> <span data-ttu-id="53c3f-109">當您啟動偵錯工具時，它會在 [查詢編輯器] 視窗的第一行程式碼上暫停。</span><span class="sxs-lookup"><span data-stu-id="53c3f-109">When you start the debugger, it pauses on the first line of code in the Query Editor window.</span></span> <span data-ttu-id="53c3f-110">若要執行到您已設定的第一個中斷點，可以使用 [繼續]  功能。</span><span class="sxs-lookup"><span data-stu-id="53c3f-110">To run to the first breakpoint that you have set, you can use the **Continue** feature.</span></span> <span data-ttu-id="53c3f-111">您也可以使用 [繼續]  功能，從視窗目前暫停的任何位置執行到下一個中斷點。</span><span class="sxs-lookup"><span data-stu-id="53c3f-111">You can also use the **Continue** feature to run to the next breakpoint from any location at which the window is currently paused.</span></span> <span data-ttu-id="53c3f-112">您可以編輯中斷點以指定動作，例如中斷點應暫停執行的條件、指向 [輸出]  視窗的資訊，以及變更中斷點的位置。</span><span class="sxs-lookup"><span data-stu-id="53c3f-112">You can edit breakpoints to specify actions such as the conditions under which the breakpoint should pause execution, information to print to the **output** window, and change the location of the breakpoint.</span></span>  
  
-   <span data-ttu-id="53c3f-113">逐步執行下一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="53c3f-113">Step into the next statement.</span></span>  
  
     <span data-ttu-id="53c3f-114">這個選項可讓您逐一導覽一組陳述式，以及在進行的過程中觀察其行為。</span><span class="sxs-lookup"><span data-stu-id="53c3f-114">This option enables you to navigate through a set of statements one by one, and to observe their behavior as you go.</span></span>  
  
-   <span data-ttu-id="53c3f-115">逐步執行或不進入預存程序或函數的呼叫。</span><span class="sxs-lookup"><span data-stu-id="53c3f-115">Step either into or over a call to a stored procedure or function.</span></span>  
  
     <span data-ttu-id="53c3f-116">如果您確定預存程序沒有任何錯誤，就可以不進入此預存程序。</span><span class="sxs-lookup"><span data-stu-id="53c3f-116">If you are sure there are no errors in a stored procedure, you can step over it.</span></span> <span data-ttu-id="53c3f-117">此程序會以完整模式執行，而且結果會傳回程式碼。</span><span class="sxs-lookup"><span data-stu-id="53c3f-117">The procedure is executed in full, and the results are returned to the code.</span></span>  
  
     <span data-ttu-id="53c3f-118">如果您想要偵錯預存程序或函數，則可以逐步執行模組。</span><span class="sxs-lookup"><span data-stu-id="53c3f-118">If you want to debug a stored procedure or function, you can step into the module.</span></span> [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] <span data-ttu-id="53c3f-119">會開啟新的 [ [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器] 視窗 (填入模組的原始程式碼)，並讓此視窗進入偵錯模式，然後暫停執行模組的第一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="53c3f-119">opens a new [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window that is populated with the source code for the module, places the window into debug mode, and then pauses execution on the first statement in the module.</span></span> <span data-ttu-id="53c3f-120">接著，您就可以透過設定中斷點或逐步執行程式碼，逐一導覽模組程式碼。</span><span class="sxs-lookup"><span data-stu-id="53c3f-120">You can then navigate through the module code, for example, by setting breakpoints or stepping through the code.</span></span>  
  
 <span data-ttu-id="53c3f-121">如需偵錯工具如何讓您巡覽程式碼的詳細資訊，請參閱 [逐步執行 Transact-SQL 程式碼](step-through-transact-sql-code.md)。</span><span class="sxs-lookup"><span data-stu-id="53c3f-121">For more information about how the debugger enables you to navigate code, see [Step Through Transact-SQL Code](step-through-transact-sql-code.md).</span></span>  
  
## <a name="viewing-debugger-information"></a><span data-ttu-id="53c3f-122">檢視偵錯工具資訊</span><span class="sxs-lookup"><span data-stu-id="53c3f-122">Viewing Debugger Information</span></span>  
 <span data-ttu-id="53c3f-123">每當偵錯工具在特定的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式上暫停執行作業時，您就可以使用下列偵錯工具視窗來檢視目前的執行狀態：</span><span class="sxs-lookup"><span data-stu-id="53c3f-123">Each time the debugger pauses execution on a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement, you can use the following debugger windows to view the current execution state:</span></span>  
  
-   <span data-ttu-id="53c3f-124">[本機]  和 [監看式] **。**</span><span class="sxs-lookup"><span data-stu-id="53c3f-124">**Locals** and **Watch.**</span></span> <span data-ttu-id="53c3f-125">這些視窗會顯示目前配置的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 運算式。</span><span class="sxs-lookup"><span data-stu-id="53c3f-125">These windows display currently allocated [!INCLUDE[tsql](../../includes/tsql-md.md)] expressions.</span></span> <span data-ttu-id="53c3f-126">運算式是評估成單一純量運算式的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 子句。</span><span class="sxs-lookup"><span data-stu-id="53c3f-126">Expressions are [!INCLUDE[tsql](../../includes/tsql-md.md)] clauses that evaluate to a single, scalar expression.</span></span> <span data-ttu-id="53c3f-127">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具支援檢視參考 [!INCLUDE[tsql](../../includes/tsql-md.md)] 變數、參數或內建函式 (名稱以 @@ 為開頭) 的運算式。</span><span class="sxs-lookup"><span data-stu-id="53c3f-127">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger supports viewing expressions that reference [!INCLUDE[tsql](../../includes/tsql-md.md)] variables, parameters, or the built-in functions that have names that start with @@.</span></span> <span data-ttu-id="53c3f-128">這些視窗也會顯示目前指派給運算式的資料值。</span><span class="sxs-lookup"><span data-stu-id="53c3f-128">These windows also display the data values that are currently assigned to the expressions.</span></span>  
  
-   <span data-ttu-id="53c3f-129">**[快速監看式]。**</span><span class="sxs-lookup"><span data-stu-id="53c3f-129">**QuickWatch.**</span></span> <span data-ttu-id="53c3f-130">這個視窗會顯示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 運算式的值，而且可讓您將該運算式儲存至 [監看式]  視窗。</span><span class="sxs-lookup"><span data-stu-id="53c3f-130">This window displays the value of a [!INCLUDE[tsql](../../includes/tsql-md.md)] expression, and enables saving that expression to a **Watch** window.</span></span>  
  
-   <span data-ttu-id="53c3f-131">**[中斷點]。**</span><span class="sxs-lookup"><span data-stu-id="53c3f-131">**Breakpoints.**</span></span> <span data-ttu-id="53c3f-132">這個視窗會顯示目前已設定的中斷點，而且可讓您管理它們。</span><span class="sxs-lookup"><span data-stu-id="53c3f-132">This window displays the currently set breakpoints and enables you to manage them.</span></span>  
  
-   <span data-ttu-id="53c3f-133">**[呼叫堆疊]。**</span><span class="sxs-lookup"><span data-stu-id="53c3f-133">**Call Stack.**</span></span> <span data-ttu-id="53c3f-134">這個視窗會顯示目前的執行位置。</span><span class="sxs-lookup"><span data-stu-id="53c3f-134">This window displays the current execution location.</span></span> <span data-ttu-id="53c3f-135">此外，它也會提供有關執行作業如何從原始 [查詢編輯器] 視窗通過任何函數、預存程序或觸發程序而到達目前執行位置的資訊。</span><span class="sxs-lookup"><span data-stu-id="53c3f-135">And also provides information about how execution passed from the original Query Editor window through any functions, stored procedures, or triggers to reach the current execution location.</span></span>  
  
-   <span data-ttu-id="53c3f-136">**[輸出]。**</span><span class="sxs-lookup"><span data-stu-id="53c3f-136">**Output.**</span></span> <span data-ttu-id="53c3f-137">這個視窗會顯示各種訊息和程式資料，例如偵錯工具的系統訊息。</span><span class="sxs-lookup"><span data-stu-id="53c3f-137">This window displays various messages and program data, such as system messages from the debugger.</span></span>  
  
-   <span data-ttu-id="53c3f-138">[結果]  和 [訊息]  。</span><span class="sxs-lookup"><span data-stu-id="53c3f-138">**Results** and **Messages.**</span></span> <span data-ttu-id="53c3f-139">[查詢編輯器] 視窗上的這些索引標籤會顯示先前執行之 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式的結果。</span><span class="sxs-lookup"><span data-stu-id="53c3f-139">These tabs on the Query Editor window display the results of previously executed [!INCLUDE[tsql](../../includes/tsql-md.md)] statements.</span></span>  
  
## <a name="transact-sql-debugger-tasks"></a><span data-ttu-id="53c3f-140">Transact-SQL 偵錯工具工作</span><span class="sxs-lookup"><span data-stu-id="53c3f-140">Transact-SQL Debugger Tasks</span></span>  
  
|<span data-ttu-id="53c3f-141">工作描述</span><span class="sxs-lookup"><span data-stu-id="53c3f-141">Task Description</span></span>|<span data-ttu-id="53c3f-142">主題</span><span class="sxs-lookup"><span data-stu-id="53c3f-142">Topic</span></span>|  
|----------------------|-----------|  
|<span data-ttu-id="53c3f-143">描述如何設定 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具進行遠端偵錯。</span><span class="sxs-lookup"><span data-stu-id="53c3f-143">Describes how to configure the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger for remote debugging.</span></span>|[<span data-ttu-id="53c3f-144">設定 Transact-SQL 偵錯工具</span><span class="sxs-lookup"><span data-stu-id="53c3f-144">Configure the Transact-SQL Debugger</span></span>](configure-firewall-rules-before-running-the-tsql-debugger.md)|  
|<span data-ttu-id="53c3f-145">描述如何啟動、停止和控制偵錯工具的作業。</span><span class="sxs-lookup"><span data-stu-id="53c3f-145">Describes how to start, stop, and control the operation of the debugger.</span></span>|[<span data-ttu-id="53c3f-146">執行 Transact-SQL 偵錯工具</span><span class="sxs-lookup"><span data-stu-id="53c3f-146">Run the Transact-SQL Debugger</span></span>](transact-sql-debugger.md)|  
|<span data-ttu-id="53c3f-147">描述如何使用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具來逐步執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="53c3f-147">Describes how to use the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger to step through code.</span></span>|[<span data-ttu-id="53c3f-148">逐步執行 Transact-SQL 程式碼</span><span class="sxs-lookup"><span data-stu-id="53c3f-148">Step Through Transact-SQL Code</span></span>](step-through-transact-sql-code.md)|  
|<span data-ttu-id="53c3f-149">描述如何使用偵錯工具來檢視 [!INCLUDE[tsql](../../includes/tsql-md.md)] 資料 (例如參數和變數) 以及系統資訊。</span><span class="sxs-lookup"><span data-stu-id="53c3f-149">Describes how to use the debugger to view [!INCLUDE[tsql](../../includes/tsql-md.md)] data, such as parameters and variables, and system information.</span></span>|[<span data-ttu-id="53c3f-150">Transact-SQL 偵錯工具資訊</span><span class="sxs-lookup"><span data-stu-id="53c3f-150">Transact-SQL Debugger Information</span></span>](transact-sql-debugger-information.md)|  
  
## <a name="see-also"></a><span data-ttu-id="53c3f-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="53c3f-151">See Also</span></span>  
 [<span data-ttu-id="53c3f-152">查詢與文字編輯器 &#40;SQL Server Management Studio&#41;</span><span class="sxs-lookup"><span data-stu-id="53c3f-152">Query and Text Editors &#40;SQL Server Management Studio&#41;</span></span>](../scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  
