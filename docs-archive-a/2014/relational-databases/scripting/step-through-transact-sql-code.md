---
title: 逐步執行 Transact-SQL 程式碼
ms.custom: seo-lt-2019
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Transact-SQL debugger, debugging code
- Transact-SQL debugger, step over
- Transact-SQL debugger, step out
- Transact-SQL debugger, step into
ms.assetid: e09079b8-c4c9-42b4-821b-4ce81a98a086
author: rothja
ms.author: jroth
ms.openlocfilehash: 48cb307130c65729640864a26bdf1dfaf344b32b
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598804"
---
# <a name="step-through-transact-sql-code"></a><span data-ttu-id="aebf7-102">逐步執行 Transact-SQL 程式碼</span><span class="sxs-lookup"><span data-stu-id="aebf7-102">Step Through Transact-SQL Code</span></span>
  <span data-ttu-id="aebf7-103">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具可讓您控制哪些 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式要在 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器視窗中執行。</span><span class="sxs-lookup"><span data-stu-id="aebf7-103">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger enables you to control which [!INCLUDE[tsql](../../includes/tsql-md.md)] statements are run in a [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window.</span></span> <span data-ttu-id="aebf7-104">您可以在個別的陳述式上暫停偵錯工具，然後在該點檢視程式碼項目的狀態。</span><span class="sxs-lookup"><span data-stu-id="aebf7-104">You can pause the debugger on individual statements and then view the state of the code elements at that point.</span></span>  
  
## <a name="breakpoints"></a><span data-ttu-id="aebf7-105">中斷點</span><span class="sxs-lookup"><span data-stu-id="aebf7-105">Breakpoints</span></span>  
 <span data-ttu-id="aebf7-106">中斷點會告知偵錯工具要在特定的 [!INCLUDE[tsql](../../includes/tsql-md.md)] 陳述式上暫停執行作業。</span><span class="sxs-lookup"><span data-stu-id="aebf7-106">A breakpoint signals the debugger to pause execution on a specific [!INCLUDE[tsql](../../includes/tsql-md.md)] statement.</span></span> <span data-ttu-id="aebf7-107">如需有關中斷點的詳細資訊，請參閱＜使用 Transact-SQL 中斷點＞。</span><span class="sxs-lookup"><span data-stu-id="aebf7-107">For more information about breakpoints, see Using Transact-SQL Breakpoints.</span></span>  
  
## <a name="controlling-statement-execution"></a><span data-ttu-id="aebf7-108">控制陳述式執行</span><span class="sxs-lookup"><span data-stu-id="aebf7-108">Controlling Statement Execution</span></span>  
 <span data-ttu-id="aebf7-109">在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具中，您可以指定下列選項，以便在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 程式碼中從目前的陳述式執行：</span><span class="sxs-lookup"><span data-stu-id="aebf7-109">In the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger, you can specify the following options for executing from the current statement in [!INCLUDE[tsql](../../includes/tsql-md.md)] code:</span></span>  
  
-   <span data-ttu-id="aebf7-110">執行到下一個中斷點。</span><span class="sxs-lookup"><span data-stu-id="aebf7-110">Run to the next breakpoint.</span></span>  
  
-   <span data-ttu-id="aebf7-111">逐步執行下一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="aebf7-111">Step into the next statement.</span></span>  
  
     <span data-ttu-id="aebf7-112">如果下一個陳述式會叫用 [!INCLUDE[tsql](../../includes/tsql-md.md)] 預存程序、函數或觸發程序，偵錯工具就會顯示包含模組程式碼的新 [查詢編輯器] 視窗。</span><span class="sxs-lookup"><span data-stu-id="aebf7-112">If the next statement invokes a [!INCLUDE[tsql](../../includes/tsql-md.md)] stored procedure, function, or trigger, the debugger displays a new Query Editor window that contains the code of the module.</span></span> <span data-ttu-id="aebf7-113">此視窗會處於偵錯模式中，而且執行作業會在模組的第一個陳述式上暫停。</span><span class="sxs-lookup"><span data-stu-id="aebf7-113">The window is in debug mode, and execution pauses on the first statement in the module.</span></span> <span data-ttu-id="aebf7-114">接著，您就可以透過設定中斷點或逐步執行程式碼，在模組程式碼之間移動。</span><span class="sxs-lookup"><span data-stu-id="aebf7-114">You can then move through the module code, for example, by setting breakpoints or stepping through the code.</span></span>  
  
-   <span data-ttu-id="aebf7-115">不進入下一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="aebf7-115">Step over the next statement.</span></span>  
  
     <span data-ttu-id="aebf7-116">系統會執行下一個陳述式。</span><span class="sxs-lookup"><span data-stu-id="aebf7-116">The next statement is executed.</span></span> <span data-ttu-id="aebf7-117">不過，如果此陳述式會叫用預存程序、函數或觸發程序，模組程式碼就會執行直到完成為止，而且結果會傳回給呼叫的程式碼。</span><span class="sxs-lookup"><span data-stu-id="aebf7-117">However, if the statement invokes a stored procedure, function, or trigger, the module code runs until it finishes, and the results are returned to the calling code.</span></span> <span data-ttu-id="aebf7-118">如果您確定預存程序沒有任何錯誤，就可以不進入此預存程序。</span><span class="sxs-lookup"><span data-stu-id="aebf7-118">If you are sure there are no errors in a stored procedure, you can step over it.</span></span> <span data-ttu-id="aebf7-119">執行作業會在呼叫預存程序、函數或觸發程序之後的陳述式上暫停。</span><span class="sxs-lookup"><span data-stu-id="aebf7-119">Execution pauses on the statement that follows the call to the stored procedure, function, or trigger.</span></span>  
  
-   <span data-ttu-id="aebf7-120">跳離預存程序、函數或觸發程序。</span><span class="sxs-lookup"><span data-stu-id="aebf7-120">Step out of a stored procedure, function, or trigger.</span></span>  
  
     <span data-ttu-id="aebf7-121">執行作業會在呼叫預存程序、函數或觸發程序之後的陳述式上暫停。</span><span class="sxs-lookup"><span data-stu-id="aebf7-121">Execution pauses on the statement that follows the call to the stored procedure, function, or trigger.</span></span>  
  
-   <span data-ttu-id="aebf7-122">從目前的位置執行到指標的目前位置，並且忽略所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="aebf7-122">Run from the current location to the current location of the pointer, and ignore all breakpoints.</span></span>  
  
 <span data-ttu-id="aebf7-123">下表將列出您可以控制陳述式如何在 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具中執行的各種方式。</span><span class="sxs-lookup"><span data-stu-id="aebf7-123">The following table lists the various ways in which you can control how statements execute in the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger.</span></span>  
  
|<span data-ttu-id="aebf7-124">動作</span><span class="sxs-lookup"><span data-stu-id="aebf7-124">Action</span></span>|<span data-ttu-id="aebf7-125">程序</span><span class="sxs-lookup"><span data-stu-id="aebf7-125">Procedure</span></span>|  
|------------|---------------|  
|<span data-ttu-id="aebf7-126">執行所有陳述式，從目前的陳述式到下一個端點</span><span class="sxs-lookup"><span data-stu-id="aebf7-126">Run all statements from the current statement to the next breakpoint</span></span>|<span data-ttu-id="aebf7-127">在 [偵錯]\*\*\*\* 功能表上按一下 [繼續]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aebf7-127">On the **Debug** menu, click **Continue**.</span></span><br /><br /> <span data-ttu-id="aebf7-128">在 [**調試**] 工具列上，按一下 [**繼續**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aebf7-128">On the **Debug** toolbar, click the **Continue** button.</span></span>|  
|<span data-ttu-id="aebf7-129">逐步執行下一個陳述式或模組</span><span class="sxs-lookup"><span data-stu-id="aebf7-129">Step into the next statement or module</span></span>|<span data-ttu-id="aebf7-130">在 [**調試**] 功能表上，按一下 [**逐步**執行]。</span><span class="sxs-lookup"><span data-stu-id="aebf7-130">On the **Debug** menu, click **Step Into**.</span></span><br /><br /> <span data-ttu-id="aebf7-131">在 [**調試**] 工具列上，按一下 [**逐步**執行] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aebf7-131">On the **Debug** toolbar, click the **Step Into** button.</span></span><br /><br /> <span data-ttu-id="aebf7-132">按下 F11。</span><span class="sxs-lookup"><span data-stu-id="aebf7-132">Press F11.</span></span>|  
|<span data-ttu-id="aebf7-133">不進入下一個陳述式或模組</span><span class="sxs-lookup"><span data-stu-id="aebf7-133">Step over the next statement or module</span></span>|<span data-ttu-id="aebf7-134">按一下 [偵錯]\*\*\*\* 功能表上的 [不進入函式]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="aebf7-134">On the **Debug** menu, click **Step Over**.</span></span><br /><br /> <span data-ttu-id="aebf7-135">在 [**調試**] 工具列上，按一下 [**跳過**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aebf7-135">On the **Debug** toolbar, click the **Step Over** button.</span></span><br /><br /> <span data-ttu-id="aebf7-136">按下 F10。</span><span class="sxs-lookup"><span data-stu-id="aebf7-136">Press F10.</span></span>|  
|<span data-ttu-id="aebf7-137">跳離模組</span><span class="sxs-lookup"><span data-stu-id="aebf7-137">Step out of a module</span></span>|<span data-ttu-id="aebf7-138">在 [**調試**] 功能表上，按一下 [**跳出**]。</span><span class="sxs-lookup"><span data-stu-id="aebf7-138">On the **Debug** menu, click **Step Out**.</span></span><br /><br /> <span data-ttu-id="aebf7-139">在 [**調試**] 工具列上，按一下 [**跳出**] 按鈕。</span><span class="sxs-lookup"><span data-stu-id="aebf7-139">On the **Debug** toolbar, click the **Step Out** button.</span></span><br /><br /> <span data-ttu-id="aebf7-140">按下 SHIFT+F11。</span><span class="sxs-lookup"><span data-stu-id="aebf7-140">Press SHIFT+F11.</span></span>|  
|<span data-ttu-id="aebf7-141">執行至目前的資料指標位置</span><span class="sxs-lookup"><span data-stu-id="aebf7-141">Run to the current cursor location</span></span>|<span data-ttu-id="aebf7-142">在 [查詢編輯器] 視窗中按一下滑鼠右鍵，然後按一下 [執行至資料指標處]  。</span><span class="sxs-lookup"><span data-stu-id="aebf7-142">Right-click in the Query Editor window, and then click **Run To Cursor**.</span></span><br /><br /> <span data-ttu-id="aebf7-143">按下 CTRL+F10。</span><span class="sxs-lookup"><span data-stu-id="aebf7-143">Press CTRL+F10.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="aebf7-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="aebf7-144">See Also</span></span>  
 [<span data-ttu-id="aebf7-145">Transact-SQL 偵錯工具資訊</span><span class="sxs-lookup"><span data-stu-id="aebf7-145">Transact-SQL Debugger Information</span></span>](transact-sql-debugger-information.md)  
  
  
