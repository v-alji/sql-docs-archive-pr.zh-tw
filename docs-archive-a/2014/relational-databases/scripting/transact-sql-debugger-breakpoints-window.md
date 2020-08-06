---
title: 中斷點視窗
ms.custom: seo-lt-2019
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- Breakpoints Window [Transact-SQL]
ms.assetid: bad88d10-fdd5-4d3d-b5ea-a4f063847485
author: rothja
ms.author: jroth
ms.openlocfilehash: 077d501e581ed5baaac45cc6bbbb34e0040730e6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87598795"
---
# <a name="breakpoints-window"></a><span data-ttu-id="c96cb-102">中斷點視窗</span><span class="sxs-lookup"><span data-stu-id="c96cb-102">Breakpoints Window</span></span>
  <span data-ttu-id="c96cb-103">[中斷點]  視窗會列出目前 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 查詢編輯器中設定的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="c96cb-103">The **Breakpoints** window lists all the breakpoints that are set in the current [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor.</span></span> <span data-ttu-id="c96cb-104">若要管理中斷點，請使用 [中斷點]  視窗內的工具列。</span><span class="sxs-lookup"><span data-stu-id="c96cb-104">To manage the breakpoints, use the toolbar in the **Breakpoints** window.</span></span> <span data-ttu-id="c96cb-105">中斷點是偵錯模式下暫停執行的程式碼位置，好讓您可以檢視偵錯資料。</span><span class="sxs-lookup"><span data-stu-id="c96cb-105">Breakpoints are locations in the code where execution pauses in debug mode so that you can view debugging data.</span></span>  
  
## <a name="task-list"></a><span data-ttu-id="c96cb-106">工作清單</span><span class="sxs-lookup"><span data-stu-id="c96cb-106">Task List</span></span>  
 <span data-ttu-id="c96cb-107">**存取中斷點視窗**</span><span class="sxs-lookup"><span data-stu-id="c96cb-107">**To access the Breakpoints window**</span></span>  
  
-   <span data-ttu-id="c96cb-108">在 **[偵錯]** 功能表上，按一下 **[視窗]**，然後按一下 **[中斷點]**。</span><span class="sxs-lookup"><span data-stu-id="c96cb-108">On the **Debug** menu, click **Windows**, and then click **Breakpoints**.</span></span>  
  
## <a name="breakpoints-window-columns"></a><span data-ttu-id="c96cb-109">中斷點視窗資料行</span><span class="sxs-lookup"><span data-stu-id="c96cb-109">Breakpoints Window Columns</span></span>  
 <span data-ttu-id="c96cb-110">根據預設，[中斷點]  視窗會列出以下資料行。</span><span class="sxs-lookup"><span data-stu-id="c96cb-110">By default, the **Breakpoints** window lists the following columns.</span></span>  
  
 <span data-ttu-id="c96cb-111">**名稱**</span><span class="sxs-lookup"><span data-stu-id="c96cb-111">**Name**</span></span>  
 <span data-ttu-id="c96cb-112">顯示中斷點的名稱。</span><span class="sxs-lookup"><span data-stu-id="c96cb-112">Displays the name of the breakpoint.</span></span> <span data-ttu-id="c96cb-113">中斷點名稱是由偵錯工具所提供。</span><span class="sxs-lookup"><span data-stu-id="c96cb-113">Breakpoint names are provided by the debugger.</span></span> <span data-ttu-id="c96cb-114">此名稱包含內含中斷點的 Database Engine 查詢編輯器視窗名稱，以及查詢編輯器內中斷點設定所在的行號。</span><span class="sxs-lookup"><span data-stu-id="c96cb-114">This name includes the name of Database Engine Query Editor window that contains the breakpoint, and the line number in the Query Editor on which the breakpoint is set.</span></span>  
  
 <span data-ttu-id="c96cb-115">**Condition**</span><span class="sxs-lookup"><span data-stu-id="c96cb-115">**Condition**</span></span>  
 <span data-ttu-id="c96cb-116">顯示 [(無條件)]  。</span><span class="sxs-lookup"><span data-stu-id="c96cb-116">Displays **(no condition)**.</span></span> <span data-ttu-id="c96cb-117">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具不支援中斷點條件的設定。</span><span class="sxs-lookup"><span data-stu-id="c96cb-117">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support setting breakpoint conditions.</span></span>  
  
 <span data-ttu-id="c96cb-118">**叫用計數**</span><span class="sxs-lookup"><span data-stu-id="c96cb-118">**Hit Count**</span></span>  
 <span data-ttu-id="c96cb-119">顯示 [永遠中斷]\*\*\*\*。</span><span class="sxs-lookup"><span data-stu-id="c96cb-119">Displays**breaks always**.</span></span>  
  
 <span data-ttu-id="c96cb-120">您可以加入及移除以下資料行，其方式是在 [資料行]  清單中選取這些資料行。</span><span class="sxs-lookup"><span data-stu-id="c96cb-120">You can add and remove the following columns by selecting them on the **Columns** list.</span></span>  
  
 <span data-ttu-id="c96cb-121">**Filter**</span><span class="sxs-lookup"><span data-stu-id="c96cb-121">**Filter**</span></span>  
 <span data-ttu-id="c96cb-122">顯示 [(無)]  。</span><span class="sxs-lookup"><span data-stu-id="c96cb-122">Displays **(none)**.</span></span> <span data-ttu-id="c96cb-123">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具不支援中斷點篩選的設定。</span><span class="sxs-lookup"><span data-stu-id="c96cb-123">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support setting breakpoint filters.</span></span>  
  
 <span data-ttu-id="c96cb-124">**叫用時**</span><span class="sxs-lookup"><span data-stu-id="c96cb-124">**When Hit**</span></span>  
 <span data-ttu-id="c96cb-125">顯示 [中斷]  。</span><span class="sxs-lookup"><span data-stu-id="c96cb-125">Displays **Break**.</span></span>  
  
 <span data-ttu-id="c96cb-126">**語言**</span><span class="sxs-lookup"><span data-stu-id="c96cb-126">**Language**</span></span>  
 <span data-ttu-id="c96cb-127">顯示 [!INCLUDE[tsql](../../includes/tsql-md.md)] 的 [Transact-SQL]。</span><span class="sxs-lookup"><span data-stu-id="c96cb-127">Displays **Transact-SQL** for [!INCLUDE[tsql](../../includes/tsql-md.md)].</span></span>  
  
 <span data-ttu-id="c96cb-128">**Function**</span><span class="sxs-lookup"><span data-stu-id="c96cb-128">**Function**</span></span>  
 <span data-ttu-id="c96cb-129">顯示設定中斷點的行號。</span><span class="sxs-lookup"><span data-stu-id="c96cb-129">Displays the number of the line on which the breakpoint is set.</span></span>  
  
 <span data-ttu-id="c96cb-130">**檔案**</span><span class="sxs-lookup"><span data-stu-id="c96cb-130">**File**</span></span>  
 <span data-ttu-id="c96cb-131">顯示包含中斷點的來源檔案名稱以及設定中斷點的行號。</span><span class="sxs-lookup"><span data-stu-id="c96cb-131">Displays the name of the source file that contains the breakpoint, and the number of the line on which the breakpoint is set.</span></span>  
  
 <span data-ttu-id="c96cb-132">**位址**</span><span class="sxs-lookup"><span data-stu-id="c96cb-132">**Address**</span></span>  
 <span data-ttu-id="c96cb-133">[!INCLUDE[tsql](../../includes/tsql-md.md)] 偵錯工具不支援這個功能。</span><span class="sxs-lookup"><span data-stu-id="c96cb-133">The [!INCLUDE[tsql](../../includes/tsql-md.md)] debugger does not support this feature.</span></span>  
  
 <span data-ttu-id="c96cb-134">**處理**</span><span class="sxs-lookup"><span data-stu-id="c96cb-134">**Process**</span></span>  
 <span data-ttu-id="c96cb-135">顯示 [SQL]  來指示這個是 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 處理序。</span><span class="sxs-lookup"><span data-stu-id="c96cb-135">Displays **[SQL]** to indicate that this is a [!INCLUDE[ssDE](../../includes/ssde-md.md)] process.</span></span> <span data-ttu-id="c96cb-136">這後面接著程式碼執行所在的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 執行個體名稱。</span><span class="sxs-lookup"><span data-stu-id="c96cb-136">This is followed by the name of the instance of the [!INCLUDE[ssDE](../../includes/ssde-md.md)] in which the code executes.</span></span>  
  
## <a name="breakpoints-window-toolbar"></a><span data-ttu-id="c96cb-137">中斷點視窗工具列</span><span class="sxs-lookup"><span data-stu-id="c96cb-137">Breakpoints Window Toolbar</span></span>  
 <span data-ttu-id="c96cb-138">當目前的 [!INCLUDE[ssDE](../../includes/ssde-md.md)] [查詢編輯器] 視窗有使用中的中斷點時，[中斷點]  視窗會顯示一個可用來管理中斷點的工具列。</span><span class="sxs-lookup"><span data-stu-id="c96cb-138">When the current [!INCLUDE[ssDE](../../includes/ssde-md.md)] Query Editor window has active breakpoints, the **Breakpoints** window displays a toolbar that can be used to manage the breakpoints.</span></span>  
  
 <span data-ttu-id="c96cb-139">**刪除**</span><span class="sxs-lookup"><span data-stu-id="c96cb-139">**Delete**</span></span>  
 <span data-ttu-id="c96cb-140">刪除選取的中斷點。</span><span class="sxs-lookup"><span data-stu-id="c96cb-140">Deletes the selected breakpoint.</span></span>  
  
 <span data-ttu-id="c96cb-141">**刪除所有中斷點**</span><span class="sxs-lookup"><span data-stu-id="c96cb-141">**Delete All Breakpoints**</span></span>  
 <span data-ttu-id="c96cb-142">刪除 [中斷點]  視窗內顯示的所有中斷點。</span><span class="sxs-lookup"><span data-stu-id="c96cb-142">Deletes all breakpoints that are displayed in the **Breakpoints** window.</span></span>  
  
 <span data-ttu-id="c96cb-143">**停用所有中斷點**</span><span class="sxs-lookup"><span data-stu-id="c96cb-143">**Disable All Breakpoints**</span></span>  
 <span data-ttu-id="c96cb-144">停用所有中斷點，好讓它們不再停止執行程式碼；但是，中斷點仍會留著。</span><span class="sxs-lookup"><span data-stu-id="c96cb-144">Disables all breakpoints so that they no longer stop code execution; however, the breakpoints remain.</span></span> <span data-ttu-id="c96cb-145">當所有中斷點都停用以後，這個按鈕會變成 [啟用所有中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="c96cb-145">When all the breakpoints are disabled, this button becomes **Enable All Breakpoints**.</span></span>  
  
 <span data-ttu-id="c96cb-146">**啟用所有中斷點**</span><span class="sxs-lookup"><span data-stu-id="c96cb-146">**Enable All Breakpoints**</span></span>  
 <span data-ttu-id="c96cb-147">啟用所有中斷點，好讓它們停止執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="c96cb-147">Enables all breakpoints so that they stop code execution.</span></span> <span data-ttu-id="c96cb-148">當所有中斷點都啟用以後，這個按鈕會變成 [停用所有中斷點]  。</span><span class="sxs-lookup"><span data-stu-id="c96cb-148">When all breakpoints are enabled, this button becomes **Disable All Breakpoints**.</span></span>  
  
 <span data-ttu-id="c96cb-149">**移至原始程式碼**</span><span class="sxs-lookup"><span data-stu-id="c96cb-149">**Go To Source Code**</span></span>  
 <span data-ttu-id="c96cb-150">將游標放在查詢編輯器中包含選定中斷點的那一行上面。</span><span class="sxs-lookup"><span data-stu-id="c96cb-150">Positions the cursor on the line in the Query Editor that contains the selected breakpoint.</span></span>  
  
 <span data-ttu-id="c96cb-151">**資料行**</span><span class="sxs-lookup"><span data-stu-id="c96cb-151">**Columns**</span></span>  
 <span data-ttu-id="c96cb-152">列出可以在 [中斷點]  視窗內顯示的所有資料行。</span><span class="sxs-lookup"><span data-stu-id="c96cb-152">Lists all the columns that can be displayed in the **Breakpoints** window.</span></span> <span data-ttu-id="c96cb-153">核取方塊表示已選取資料行。</span><span class="sxs-lookup"><span data-stu-id="c96cb-153">A check box indicates the columns that are displayed.</span></span> <span data-ttu-id="c96cb-154">若要加入或移除 [中斷點]  視窗中的資料行，請在清單中選取該資料行。</span><span class="sxs-lookup"><span data-stu-id="c96cb-154">To add or remove a column in the **Breakpoints** window, select the column on the list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c96cb-155">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c96cb-155">See Also</span></span>  
 [<span data-ttu-id="c96cb-156">Transact-SQL 偵錯工具</span><span class="sxs-lookup"><span data-stu-id="c96cb-156">Transact-SQL Debugger</span></span>](transact-sql-debugger.md)  
