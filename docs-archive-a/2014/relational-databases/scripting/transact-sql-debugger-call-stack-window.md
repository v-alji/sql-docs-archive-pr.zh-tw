---
title: 呼叫堆疊視窗
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Call Stack Window [Transact-SQL]
ms.assetid: ddb0b19c-87cd-4883-bcb8-ec09ffb30369
author: rothja
ms.author: jroth
ms.openlocfilehash: b4b72e484ade696be81ebac8ea4eed9be295edf2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87599456"
---
# <a name="call-stack-window"></a><span data-ttu-id="4a786-102">呼叫堆疊視窗</span><span class="sxs-lookup"><span data-stu-id="4a786-102">Call Stack Window</span></span>
  <span data-ttu-id="4a786-103">[呼叫堆疊]  視窗會顯示呼叫堆疊上的模組以及傳遞給模組之任何參數的資料類型和值。</span><span class="sxs-lookup"><span data-stu-id="4a786-103">The **Call Stack** window displays the modules on the call stack, and the data types and values of any parameters that are passed to the modules.</span></span> [!INCLUDE[tsql](../../includes/tsql-md.md)] <span data-ttu-id="4a786-104">模組包括預存程序、函數及觸發程序</span><span class="sxs-lookup"><span data-stu-id="4a786-104">modules include stored procedures, functions, and triggers.</span></span> <span data-ttu-id="4a786-105">若要顯示呼叫堆疊，您必須在偵錯模式中。</span><span class="sxs-lookup"><span data-stu-id="4a786-105">To display the call stack, you must be in debug mode.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="4a786-106">工作清單</span><span class="sxs-lookup"><span data-stu-id="4a786-106">Task List</span></span>  
 <span data-ttu-id="4a786-107">**存取呼叫堆疊視窗**</span><span class="sxs-lookup"><span data-stu-id="4a786-107">**To access the Call Stack window**</span></span>  
  
-   <span data-ttu-id="4a786-108">在 [偵錯]  功能表上，按一下 [視窗]  ，然後按一下 [呼叫堆疊]  。</span><span class="sxs-lookup"><span data-stu-id="4a786-108">On the **Debug** menu, click **Windows**, and then click **Call Stack**.</span></span>  
  
 <span data-ttu-id="4a786-109">**變更目前的呼叫堆疊框架**</span><span class="sxs-lookup"><span data-stu-id="4a786-109">**To change the current Call Stack frame**</span></span>  
  
 <span data-ttu-id="4a786-110">您可以使用以下程序的其中一種，讓堆疊框架變成目前的框架：</span><span class="sxs-lookup"><span data-stu-id="4a786-110">You can use either of the following procedures to make a stack frame the current frame:</span></span>  
  
-   <span data-ttu-id="4a786-111">以滑鼠右鍵按一下堆疊框架，然後按一下 [切換至框架]  。</span><span class="sxs-lookup"><span data-stu-id="4a786-111">Right-click the stack frame, and then click **Switch To Frame**.</span></span>  
  
-   <span data-ttu-id="4a786-112">按兩下此堆疊框架。</span><span class="sxs-lookup"><span data-stu-id="4a786-112">Double-click the stack frame.</span></span>  
  
 <span data-ttu-id="4a786-113">**檢視目前框架以外之框架的來源**</span><span class="sxs-lookup"><span data-stu-id="4a786-113">**To view the source of a frame other than the current frame**</span></span>  
  
-   <span data-ttu-id="4a786-114">以滑鼠右鍵按一下堆疊框架，然後按一下 [移至原始程式碼]  。</span><span class="sxs-lookup"><span data-stu-id="4a786-114">Right-click the stack frame, and then click **Go To Source Code**.</span></span>  
  
## <a name="stack-frames"></a><span data-ttu-id="4a786-115">堆疊框架</span><span class="sxs-lookup"><span data-stu-id="4a786-115">Stack Frames</span></span>  
 <span data-ttu-id="4a786-116">[呼叫堆疊]  視窗中的每一個資料列都稱為堆疊框架，而且代表從 [!INCLUDE[tsql](../../includes/tsql-md.md)] 指令碼檔案到模組的呼叫或是從某個模組到另一個模組的呼叫。</span><span class="sxs-lookup"><span data-stu-id="4a786-116">Each row in the **Call Stack** window is called a stack frame and represents either a call from a [!INCLUDE[tsql](../../includes/tsql-md.md)] script file to a module or a call from one module to another.</span></span> <span data-ttu-id="4a786-117">顯示畫面底部的堆疊框架表示 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [查詢編輯器] 視窗中對此堆疊進行第一個呼叫的那一行。</span><span class="sxs-lookup"><span data-stu-id="4a786-117">The bottom stack frame in the display indicates the line in the [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window that made the first call into the stack.</span></span> <span data-ttu-id="4a786-118">頂端列表示偵錯工具暫停執行的那一行，而且是由視窗左邊界的黃色箭頭所識別。</span><span class="sxs-lookup"><span data-stu-id="4a786-118">The top row indicates the line on which the debugger paused execution, and is identified by a yellow arrow in the left margin of the window.</span></span> <span data-ttu-id="4a786-119">每一個中間列都表示呼叫下一個更高堆疊框架之原始程式碼的模組和行號。</span><span class="sxs-lookup"><span data-stu-id="4a786-119">Each intermediate row indicates the module and the line number of the source code that called the next higher stack frame.</span></span>  
  
 <span data-ttu-id="4a786-120">[區域變數]  、[監看式]  和 [快速監看式]  視窗中的所有運算式都會根據目前的堆疊框架來評估。</span><span class="sxs-lookup"><span data-stu-id="4a786-120">All expressions in the **Locals**, **Watch**, and **QuickWatch** windows are evaluated based on the current stack frame.</span></span> <span data-ttu-id="4a786-121">[查詢編輯器] 視窗會顯示目前框架的程式碼。</span><span class="sxs-lookup"><span data-stu-id="4a786-121">The Query Editor window displays the code for the current frame.</span></span> <span data-ttu-id="4a786-122">根據預設，目前的堆疊框架就是 [!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具暫停執行所在的框架。</span><span class="sxs-lookup"><span data-stu-id="4a786-122">By default, the current stack frame is the frame in which the [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger paused execution.</span></span> <span data-ttu-id="4a786-123">當您將目前的堆疊框架變更為另一個框架時，將會在新框架的內容中重新評估 [區域變數]  、[監看式]  和 [快速監看式]  視窗中的運算式，而且新框架的原始程式碼會顯示在 [查詢編輯器] 視窗中。</span><span class="sxs-lookup"><span data-stu-id="4a786-123">When you change the current stack frame to another frame, the expressions in the **Locals**, **Watch**, and **QuickWatch** windows are reevaluated in the context of the new frame, and the source code of the new frame is displayed in the Query Editor window.</span></span>  
  
## <a name="columns"></a><span data-ttu-id="4a786-124">資料行</span><span class="sxs-lookup"><span data-stu-id="4a786-124">Columns</span></span>  
 <span data-ttu-id="4a786-125">**名稱**</span><span class="sxs-lookup"><span data-stu-id="4a786-125">**Name**</span></span>  
 <span data-ttu-id="4a786-126">顯示有關呼叫堆疊上之模組的資訊。</span><span class="sxs-lookup"><span data-stu-id="4a786-126">Displays information about a module on the call stack.</span></span>  
  
 <span data-ttu-id="4a786-127">如果是呼叫堆疊內的底部列，[名稱]  會列出 [查詢編輯器] 來源視窗及第一次呼叫此堆疊的行號。</span><span class="sxs-lookup"><span data-stu-id="4a786-127">For the bottom row in the call stack, **Name** lists the Query Editor source window and line number of the first call into the stack.</span></span> <span data-ttu-id="4a786-128">如果是其他資料列，[名稱]  的格式為 **Module(Instance.Database)(ParmList) LineNumber**。</span><span class="sxs-lookup"><span data-stu-id="4a786-128">For the other rows, **Name** has the format **Module(Instance.Database)(ParmList) LineNumber**.</span></span>  
  
 <span data-ttu-id="4a786-129">**模組**</span><span class="sxs-lookup"><span data-stu-id="4a786-129">**Module**</span></span>  
 <span data-ttu-id="4a786-130">這是預存程序、函數或呼叫下一個堆疊之預存程序的名稱。</span><span class="sxs-lookup"><span data-stu-id="4a786-130">Is the name of the stored procedure, function, or stored procedure that called to the next frame.</span></span>  
  
 <span data-ttu-id="4a786-131">**Instance.Database**</span><span class="sxs-lookup"><span data-stu-id="4a786-131">**Instance.Database**</span></span>  
 <span data-ttu-id="4a786-132">這是 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 的執行個體以及保留模組的資料庫。</span><span class="sxs-lookup"><span data-stu-id="4a786-132">Is the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] and the database that is holding the module.</span></span>  
  
 <span data-ttu-id="4a786-133">**ParmList**</span><span class="sxs-lookup"><span data-stu-id="4a786-133">**ParmList**</span></span>  
 <span data-ttu-id="4a786-134">表示在模組的呼叫期間所傳入之每一個參數的資料類型、名稱和值。</span><span class="sxs-lookup"><span data-stu-id="4a786-134">Indicates the data type, name, and value for each parameter that is passed in during the call to the module.</span></span>  
  
 <span data-ttu-id="4a786-135">**LineNumber**</span><span class="sxs-lookup"><span data-stu-id="4a786-135">**LineNumber**</span></span>  
 <span data-ttu-id="4a786-136">如果是頂端列以外的所有列， **LineNumber** 表示模組中呼叫此框架的那一行。</span><span class="sxs-lookup"><span data-stu-id="4a786-136">For all rows except the top row, **LineNumber** indicates which line in the module called to the frame.</span></span> <span data-ttu-id="4a786-137">如果是頂端列， **LineNumber** 表示偵錯工具目前焦點所在的那一行。</span><span class="sxs-lookup"><span data-stu-id="4a786-137">For the top row, **LineNumber** indicates the line on which the debugger is currently focused.</span></span>  
  
 <span data-ttu-id="4a786-138">**語言**</span><span class="sxs-lookup"><span data-stu-id="4a786-138">**Language**</span></span>  
 <span data-ttu-id="4a786-139">顯示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 的 [Transact-SQL]。</span><span class="sxs-lookup"><span data-stu-id="4a786-139">Displays **Transact-SQL** for [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a786-140">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4a786-140">See Also</span></span>  
 <span data-ttu-id="4a786-141">[Transact-sql 偵錯工具](transact-sql-debugger.md) </span><span class="sxs-lookup"><span data-stu-id="4a786-141">[Transact-SQL Debugger](transact-sql-debugger.md) </span></span>  
 <span data-ttu-id="4a786-142">[Transact-sql 偵錯工具資訊](transact-sql-debugger-information.md) </span><span class="sxs-lookup"><span data-stu-id="4a786-142">[Transact-SQL Debugger Information](transact-sql-debugger-information.md) </span></span>  
 [<span data-ttu-id="4a786-143">逐步執行 Transact-SQL 程式碼</span><span class="sxs-lookup"><span data-stu-id="4a786-143">Step Through Transact-SQL Code</span></span>](step-through-transact-sql-code.md)  
