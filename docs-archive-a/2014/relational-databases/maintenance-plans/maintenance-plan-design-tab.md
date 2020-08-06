---
title: 維護計畫 (設計索引標籤) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
f1_keywords:
- sql12.swb.maint.planeditor.f1
- sql12.swb.maint.subplaneditor.f1
- sql12.swb.maint.maintplanproperties.optimizations.f1
ms.assetid: 6d20d4d4-5b3f-454a-8a05-f0aac803c5ad
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: e18b1c3901b37dfe44ad94c8e7a390801ae2f1d2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/04/2020
ms.locfileid: "87594532"
---
# <a name="maintenance-plan-design-tab"></a><span data-ttu-id="adca1-102">維護計畫 (設計索引標籤)</span><span class="sxs-lookup"><span data-stu-id="adca1-102">Maintenance Plan (Design Tab)</span></span>
  <span data-ttu-id="adca1-103">使用 [維護計畫 (設計索引標籤)]  可指定維護計畫及其子計畫的屬性。</span><span class="sxs-lookup"><span data-stu-id="adca1-103">Use the **Maintenance Plan (Design Tab)** to specify the properties of a maintenance plan and its subplans.</span></span> <span data-ttu-id="adca1-104">將工作從工具箱拖曳至計畫設計師。</span><span class="sxs-lookup"><span data-stu-id="adca1-104">Drag tasks from the Toolbox to the plan designer.</span></span> <span data-ttu-id="adca1-105">在工作群組按一下滑鼠右鍵，即可建立分支執行路徑。</span><span class="sxs-lookup"><span data-stu-id="adca1-105">Right-click groups of tasks to create branching execution paths.</span></span> <span data-ttu-id="adca1-106">維護計畫會儲存為 [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] 封裝，然後由 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent 作業執行。</span><span class="sxs-lookup"><span data-stu-id="adca1-106">Maintenance plans are saved as [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] packages that are run by [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent jobs.</span></span>  
  
## <a name="options"></a><span data-ttu-id="adca1-107">選項。</span><span class="sxs-lookup"><span data-stu-id="adca1-107">Options</span></span>  
 <span data-ttu-id="adca1-108">**加入子計畫**</span><span class="sxs-lookup"><span data-stu-id="adca1-108">**Add Subplan**</span></span>  
 <span data-ttu-id="adca1-109">新增可設定的子計畫。</span><span class="sxs-lookup"><span data-stu-id="adca1-109">Add a subplan that you can configure.</span></span>  
  
 <span data-ttu-id="adca1-110">**子計畫屬性**</span><span class="sxs-lookup"><span data-stu-id="adca1-110">**Subplan Properties**</span></span>  
 <span data-ttu-id="adca1-111">顯示 [子計畫屬性]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="adca1-111">Display the **Subplan Properties** dialog box.</span></span> <span data-ttu-id="adca1-112">選取方格中的子計畫，然後按一下這個圖示輸入子計畫的名稱、描述和排程。</span><span class="sxs-lookup"><span data-stu-id="adca1-112">Select a subplan in the grid and click this icon to enter a name, description, and schedule for the subplan.</span></span> <span data-ttu-id="adca1-113">您也可以按兩下方格中的子計畫，顯示 [子計畫屬性]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="adca1-113">You can also double-click the subplan in the grid to display the **Subplan Properties** dialog box.</span></span> <span data-ttu-id="adca1-114">子計畫名稱最多可包含 128 個字元，而子計畫描述最多可包含 512 個字元。</span><span class="sxs-lookup"><span data-stu-id="adca1-114">Subplan names are limited to 128 characters and subplan descriptions are limited to 512 characters.</span></span>  
  
 <span data-ttu-id="adca1-115">**刪除選取的子計畫**</span><span class="sxs-lookup"><span data-stu-id="adca1-115">**Delete Selected Subplan**</span></span>  
 <span data-ttu-id="adca1-116">刪除選取的子計畫。</span><span class="sxs-lookup"><span data-stu-id="adca1-116">Delete the selected subplan.</span></span>  
  
 <span data-ttu-id="adca1-117">**子計畫排程**</span><span class="sxs-lookup"><span data-stu-id="adca1-117">**Subplan Schedule**</span></span>  
 <span data-ttu-id="adca1-118">顯示 [作業排程屬性]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="adca1-118">Display the **Job Schedule Properties** dialog box.</span></span> <span data-ttu-id="adca1-119">選取方格中的子計畫，然後按一下這個圖示輸入子計畫的排程。</span><span class="sxs-lookup"><span data-stu-id="adca1-119">Select a subplan in the grid and click this icon to configure a schedule for the subplan.</span></span>  
  
 <span data-ttu-id="adca1-120">**移除排程**</span><span class="sxs-lookup"><span data-stu-id="adca1-120">**Remove Schedule**</span></span>  
 <span data-ttu-id="adca1-121">從選取的子計畫移除排程。</span><span class="sxs-lookup"><span data-stu-id="adca1-121">Remove a schedule from the selected subplan.</span></span>  
  
 <span data-ttu-id="adca1-122">**管理連線**</span><span class="sxs-lookup"><span data-stu-id="adca1-122">**Manage Connections**</span></span>  
 <span data-ttu-id="adca1-123">顯示 [管理連接]  對話方塊。</span><span class="sxs-lookup"><span data-stu-id="adca1-123">Display the **Manage Connections** dialog box.</span></span> <span data-ttu-id="adca1-124">用於將其他 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 執行個體連接加入維護計畫。</span><span class="sxs-lookup"><span data-stu-id="adca1-124">Used to add additional [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] instance connections to the maintenance plan.</span></span> <span data-ttu-id="adca1-125">子計畫編輯器中的每個維護工作，都可以使用這些連接。</span><span class="sxs-lookup"><span data-stu-id="adca1-125">Each maintenance task in the subplan editor can use any of these connections.</span></span> <span data-ttu-id="adca1-126">執行時，維護計畫會使用連接認證，從維護計畫伺服器連接到指定的 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 伺服器。</span><span class="sxs-lookup"><span data-stu-id="adca1-126">When executing, the maintenance plan makes a connection from the maintenance plan server to the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] servers specified, using the connection credentials.</span></span>  
  
 <span data-ttu-id="adca1-127">**報表與記錄**</span><span class="sxs-lookup"><span data-stu-id="adca1-127">**Reporting and Logging**</span></span>  
 <span data-ttu-id="adca1-128">顯示 [報表與記錄]  對話方塊，用來管理維護計畫活動的相關報表，以及設定記錄到本機或遠端伺服器。</span><span class="sxs-lookup"><span data-stu-id="adca1-128">Display the **Reporting and Logging** dialog box, used to manage reports concerning maintenance plan activity, and to configure logging to the local or a remote server.</span></span>  
  
 <span data-ttu-id="adca1-129">**伺服器**</span><span class="sxs-lookup"><span data-stu-id="adca1-129">**Servers**</span></span>  
 <span data-ttu-id="adca1-130">顯示 [伺服器]  對話方塊，用來選取將執行子計畫工作的伺服器。</span><span class="sxs-lookup"><span data-stu-id="adca1-130">Display the **Servers** dialog box, which is used to select the servers where the subplan tasks will be run.</span></span> <span data-ttu-id="adca1-131">只有多伺服器環境中的主要伺服器才會啟用這個選項。</span><span class="sxs-lookup"><span data-stu-id="adca1-131">This option is enabled only on master servers in multiserver environments.</span></span> <span data-ttu-id="adca1-132">如需詳細資訊，請參閱 [建立多伺服器環境](../../ssms/agent/create-a-multiserver-environment.md)。</span><span class="sxs-lookup"><span data-stu-id="adca1-132">For more information, see [Create a Multiserver Environment](../../ssms/agent/create-a-multiserver-environment.md).</span></span>  
  
 <span data-ttu-id="adca1-133">**名稱**</span><span class="sxs-lookup"><span data-stu-id="adca1-133">**Name**</span></span>  
 <span data-ttu-id="adca1-134">顯示維護計畫名稱。</span><span class="sxs-lookup"><span data-stu-id="adca1-134">Display the maintenance plan name.</span></span> <span data-ttu-id="adca1-135">針對新的維護計畫，名稱會在維護計畫設計師開啟之前，於對話方塊中指定。</span><span class="sxs-lookup"><span data-stu-id="adca1-135">For new maintenance plans, the name is specified in a dialog box before the maintenance plan designer opens.</span></span> <span data-ttu-id="adca1-136">若要重新命名維護計畫，請以滑鼠右鍵按一下物件總管中的計畫，然後按一下 [重新命名]  。</span><span class="sxs-lookup"><span data-stu-id="adca1-136">To rename a maintenance plan, right-click the plan in Object Explorer, and then click **Rename**.</span></span>  
  
 <span data-ttu-id="adca1-137">**說明**</span><span class="sxs-lookup"><span data-stu-id="adca1-137">**Description**</span></span>  
 <span data-ttu-id="adca1-138">檢視或指定維護計畫的描述。</span><span class="sxs-lookup"><span data-stu-id="adca1-138">View or specify a description for the maintenance plan.</span></span> <span data-ttu-id="adca1-139">描述的最大長度是 512 個字元。</span><span class="sxs-lookup"><span data-stu-id="adca1-139">The maximum length for a description is 512 characters.</span></span>  
  
 <span data-ttu-id="adca1-140">**設計師介面**</span><span class="sxs-lookup"><span data-stu-id="adca1-140">**Designer Surface**</span></span>  
 <span data-ttu-id="adca1-141">設計維護計畫並予以維護。</span><span class="sxs-lookup"><span data-stu-id="adca1-141">Design and maintain maintenance plans.</span></span> <span data-ttu-id="adca1-142">使用設計師介面即可將維護工作加入計畫、從計畫中移除工作、指定工作間的優先順序連結以及指出工作分支和平行處理原則。</span><span class="sxs-lookup"><span data-stu-id="adca1-142">Use the designer surface to add maintenance tasks to a plan, remove tasks from a plan, specify precedence links between the tasks, and indicate task branching and parallelism.</span></span>  
  
 <span data-ttu-id="adca1-143">兩個工作間的優先順序連結會建立工作間的關聯性。</span><span class="sxs-lookup"><span data-stu-id="adca1-143">A precedence link between two tasks establishes a relationship between the tasks.</span></span> <span data-ttu-id="adca1-144">只有在第一個工作 (「前導工作」) 的執行結果符合指定的準則時，才會執行第二個工作 (「相依工作」)。</span><span class="sxs-lookup"><span data-stu-id="adca1-144">The second task (the *dependent task*) executes only if the execution result of the first task (the *precedent task*) matches specified criteria.</span></span> <span data-ttu-id="adca1-145">一般而言，指定的執行結果會是 **[成功]** 、 **[失敗]** 或 **[完成]** 。</span><span class="sxs-lookup"><span data-stu-id="adca1-145">Typically the execution result specified is **Success**, **Failure**, or **Completion**.</span></span> <span data-ttu-id="adca1-146">維護計畫設計師介面是以 [!INCLUDE[ssIS](../../includes/ssis-md.md)] 設計師介面為基礎。</span><span class="sxs-lookup"><span data-stu-id="adca1-146">The maintenance plan designer surface is based on the [!INCLUDE[ssIS](../../includes/ssis-md.md)] designer surface.</span></span> <span data-ttu-id="adca1-147">如需詳細資訊，請參閱 [優先順序條件約束](../../integration-services/control-flow/precedence-constraints.md)。</span><span class="sxs-lookup"><span data-stu-id="adca1-147">For more information, see [Precedence Constraints](../../integration-services/control-flow/precedence-constraints.md).</span></span>  
  
 <span data-ttu-id="adca1-148">例如，只有先前的 [檢查資料庫完整性] 工作順利完成之後，才能指定執行 [重組索引工作]。</span><span class="sxs-lookup"><span data-stu-id="adca1-148">As an example, a Defragment Index Task could be specified to execute only if a previous Check Database Integrity task completed successfully.</span></span> <span data-ttu-id="adca1-149">工作優先順序連結功能，也可以在計畫中處理錯誤或失敗的狀況。</span><span class="sxs-lookup"><span data-stu-id="adca1-149">The task precedence linkage feature also allows for error or failure conditions to be handled in a plan.</span></span> <span data-ttu-id="adca1-150">例如，如果 [檢查資料庫完整性] 工作失敗，[通知操作員] 工作可將失敗通知使用者或操作員。</span><span class="sxs-lookup"><span data-stu-id="adca1-150">For example, if the Check Database Integrity task failed, a Notify Operator task could notify a user or operator about the failure.</span></span>  
  
 <span data-ttu-id="adca1-151">指定前置工作失敗之後要執行的工作，就是「工作分支」  的範例。</span><span class="sxs-lookup"><span data-stu-id="adca1-151">Specifying tasks to execute after the failure of a predecessor task is an example of *task branching*.</span></span>  
  
 <span data-ttu-id="adca1-152">指出要同時開始執行兩個或以上的工作 (例如在前置工作順利完成之後)，就是指定「工作平行處理原則」  的範例。</span><span class="sxs-lookup"><span data-stu-id="adca1-152">Indicating that two or more tasks begin simultaneously, for example upon the successful completion of a predecessor task, is an example of specifying *task parallelism*.</span></span> <span data-ttu-id="adca1-153">沒有條件約束的所有工作將啟動並平行執行。</span><span class="sxs-lookup"><span data-stu-id="adca1-153">All tasks with no constraints will start and run in parallel.</span></span> <span data-ttu-id="adca1-154">請使用條件約束延後工作，讓前面的工作先完成。</span><span class="sxs-lookup"><span data-stu-id="adca1-154">Use constraints to delay  tasks so earlier tasks complete first.</span></span>  
  
 <span data-ttu-id="adca1-155">將維護工作放到設計介面中之後，就可以依需求編輯其屬性。</span><span class="sxs-lookup"><span data-stu-id="adca1-155">After a maintenance task is placed on the design surface, its properties can be edited as needed.</span></span> <span data-ttu-id="adca1-156">例如，將工作加入計畫之後，就可以在 [備份資料庫工作] 中指定要備份的特定資料庫。</span><span class="sxs-lookup"><span data-stu-id="adca1-156">For example, the specific database to back up in a Back Up Database Task is specified after the task is added the plan.</span></span> <span data-ttu-id="adca1-157">設計介面上的工作如果設定不正確，會顯示包含白色 x 的紅色圖示。</span><span class="sxs-lookup"><span data-stu-id="adca1-157">Tasks on the design surface that are not properly configured contain a red icon with a white x.</span></span>  
  
 <span data-ttu-id="adca1-158">若要將維護工作加入計畫，請將工作的圖示從 [維護計畫工作]  工具箱拖曳到計畫設計介面，或按兩下工具箱中的工作，這會將該工作加入目前使用中的設計師介面。</span><span class="sxs-lookup"><span data-stu-id="adca1-158">To add a maintenance task to a plan, drag the task's icon from the **Maintenance Plan Tasks** toolbox to the plan design surface, or double-click the task in the toolbox, which adds that task to the currently active designer surface.</span></span> <span data-ttu-id="adca1-159">如果看不到 [維護計畫工作]  工具箱，請從  **[檢視]** [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] 功能表選擇 [工具箱]  。</span><span class="sxs-lookup"><span data-stu-id="adca1-159">If the **Maintenance Plan Tasks** toolbox is not visible, choose **Toolbox** from the [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] **View** menu.</span></span> <span data-ttu-id="adca1-160">在 [工具箱] 窗格中展開 [維護計畫工作] 節點。</span><span class="sxs-lookup"><span data-stu-id="adca1-160">Expand the **Maintenance Plan Tasks** node in the **Toolbox** pane.</span></span>  
  
 <span data-ttu-id="adca1-161">若要從計畫中移除工作，請在設計師介面選取該工作，然後按下 **DELETE** 鍵，或以滑鼠右鍵按一下該工作，然後按一下 [刪除]  。</span><span class="sxs-lookup"><span data-stu-id="adca1-161">To remove a task from a plan, select the task in the designer surface and press the **DELETE** key, or right-click the task and then click **Delete**.</span></span>  
  
 <span data-ttu-id="adca1-162">若要指定兩個工作間的優先順序連結，請先將工作拖曳至設計介面，然後按一下先執行的工作 (前導工作)，再將箭頭拖曳到相依工作。</span><span class="sxs-lookup"><span data-stu-id="adca1-162">To specify precedence links between two tasks, first drag the tasks to the design surface, and then click the task that occurs first (the precedent task), and drag the arrow to the dependent task.</span></span> <span data-ttu-id="adca1-163">建立優先順序連結後，設計師會顯示由前導工作指向相依工作的箭頭，連結兩個工作。</span><span class="sxs-lookup"><span data-stu-id="adca1-163">When a precedence link has been established, the designer displays an arrow linking the two tasks, with the precedent task pointing to the dependent task.</span></span> <span data-ttu-id="adca1-164">依預設，第一次建立連結時，會設定連結的條件約束，使得只有前導工作的執行結果為 [成功]  時才會執行相依工作。</span><span class="sxs-lookup"><span data-stu-id="adca1-164">By default, when a link is first established, the link's constraint is set such that the dependent task only executes if the execution result of the precedent task is **Success**.</span></span>  
  
 <span data-ttu-id="adca1-165">若要變更優先順序連結的屬性，請按兩下連結以啟動 [優先順序條件約束編輯器]  。</span><span class="sxs-lookup"><span data-stu-id="adca1-165">To change the properties of a precedence link, double-click the link to launch the **Precedence Constraint Editor**.</span></span> <span data-ttu-id="adca1-166">其中提供許多用來指定邏輯條件的選項，以判定是否要執行相依工作。</span><span class="sxs-lookup"><span data-stu-id="adca1-166">This provides many options for specifying the logical conditions which determine whether the dependent task executes.</span></span> <span data-ttu-id="adca1-167">例如，可以將 [執行結果]  設定為 [失敗]  ，在這個情況下，只有前導工作失敗時才會執行相依工作。</span><span class="sxs-lookup"><span data-stu-id="adca1-167">For example, the **Execution result** can be set to **Failure**, in which case the dependent task only executes if the precedent task fails.</span></span> <span data-ttu-id="adca1-168">若要將連結的執行結果屬性修改為 [成功]  、[失敗]  或 [完成]  ，也可以在連結上按一下滑鼠右鍵，然後從內容功能表中選取。</span><span class="sxs-lookup"><span data-stu-id="adca1-168">Modifying the execution result property of a link to **Success**, **Failure**, or **Completion**, can also be accomplished by right-clicking the link and then selecting from the context menu.</span></span>  
  
 <span data-ttu-id="adca1-169">若要指定工作分支，請先建立兩個工作間的優先順序連結。</span><span class="sxs-lookup"><span data-stu-id="adca1-169">To specify task branching, first create precedence links between two tasks.</span></span> <span data-ttu-id="adca1-170">然後，將另一個相依工作放在設計介面上，在發生與第一個相依工作不同的結果時執行。</span><span class="sxs-lookup"><span data-stu-id="adca1-170">Then, put another dependent task on the design surface that executes on a different outcome than the first dependent task.</span></span> <span data-ttu-id="adca1-171">按一下前置工作，再將第二個箭頭從前導工作拖曳至該相依工作。</span><span class="sxs-lookup"><span data-stu-id="adca1-171">Click the predecessor task, and drag the second arrow from the precedent task to the dependent task.</span></span> <span data-ttu-id="adca1-172">若要變更會導致相依工作執行的執行結果 ([成功]  、[失敗]  、[完成]  )，請按兩下連結箭號，然後修改 [執行結果]  欄位。</span><span class="sxs-lookup"><span data-stu-id="adca1-172">To change the execution result (**Success**, **Failure**, **Completion**) that causes a dependent task to execute, double-click the link arrow and modify the **Execution result** field.</span></span> <span data-ttu-id="adca1-173">或者，以滑鼠右鍵按一下連結，再從快速鍵功能表選取想要的執行結果值。</span><span class="sxs-lookup"><span data-stu-id="adca1-173">Alternatively, right-click the link and select the desired execution result value from the shortcut menu.</span></span>  
  
 <span data-ttu-id="adca1-174">若要指定工作平行處理原則，請將兩個或以上的相依工作連結至單一前導工作。</span><span class="sxs-lookup"><span data-stu-id="adca1-174">To specify task parallelism, link two or more dependent tasks to a single precedent task.</span></span> <span data-ttu-id="adca1-175">修改優先順序連結的屬性，使得指向要平行執行的相依工作連結，會有相同的執行結果欄位值。</span><span class="sxs-lookup"><span data-stu-id="adca1-175">Modify the properties of the precedence links so that the links pointing to the dependent tasks that run in parallel have the same value for their execution result fields.</span></span>  
  
## <a name="additional-features-available-from-the-shortcut-menu"></a><span data-ttu-id="adca1-176">快速鍵功能表可用的其他功能</span><span class="sxs-lookup"><span data-stu-id="adca1-176">Additional Features Available from the Shortcut Menu</span></span>  
 <span data-ttu-id="adca1-177">若要查看其他選項，請在設計介面上選取一個或多個工作，然後按一下滑鼠右鍵以開啟快速鍵功能表。</span><span class="sxs-lookup"><span data-stu-id="adca1-177">To see additional options, select one or more tasks on the design surface, and then right-click, to open the shortcut menu.</span></span> <span data-ttu-id="adca1-178">除了一般的 [剪下]  、[複製]  、[貼上]  、[刪除]  和 [全選]  以外，某些工作還可以使用下列特殊選項。</span><span class="sxs-lookup"><span data-stu-id="adca1-178">In addition to typical **Cut**, **Copy**, **Paste**, **Delete**, and **Select All**, the following special options are available for some tasks.</span></span>  
  
 <span data-ttu-id="adca1-179">**加入註解**</span><span class="sxs-lookup"><span data-stu-id="adca1-179">**Add Annotation**</span></span>  
 <span data-ttu-id="adca1-180">將描述附註加入設計介面。</span><span class="sxs-lookup"><span data-stu-id="adca1-180">Adds a descriptive note to the design surface.</span></span>  
  
 <span data-ttu-id="adca1-181">**編輯**</span><span class="sxs-lookup"><span data-stu-id="adca1-181">**Edit**</span></span>  
 <span data-ttu-id="adca1-182">開啟工作的屬性對話方塊。</span><span class="sxs-lookup"><span data-stu-id="adca1-182">Opens the property dialog box for the task.</span></span>  
  
 <span data-ttu-id="adca1-183">**Disable**</span><span class="sxs-lookup"><span data-stu-id="adca1-183">**Disable**</span></span>  
 <span data-ttu-id="adca1-184">這會使工作暫時無法使用。</span><span class="sxs-lookup"><span data-stu-id="adca1-184">Makes the task temporarily unavailable.</span></span>  
  
 <span data-ttu-id="adca1-185">**啟用**</span><span class="sxs-lookup"><span data-stu-id="adca1-185">**Enable**</span></span>  
 <span data-ttu-id="adca1-186">還原停用的工作。</span><span class="sxs-lookup"><span data-stu-id="adca1-186">Restores a disabled task.</span></span>  
  
 <span data-ttu-id="adca1-187">**群組**</span><span class="sxs-lookup"><span data-stu-id="adca1-187">**Group**</span></span>  
 <span data-ttu-id="adca1-188">建立包含一個或多個工作的群組。</span><span class="sxs-lookup"><span data-stu-id="adca1-188">Creates a group that contains one or more tasks.</span></span>  
  
 <span data-ttu-id="adca1-189">**取消群組**</span><span class="sxs-lookup"><span data-stu-id="adca1-189">**Ungroup**</span></span>  
 <span data-ttu-id="adca1-190">從群組中移除工作。</span><span class="sxs-lookup"><span data-stu-id="adca1-190">Removes tasks from a group.</span></span>  
  
 <span data-ttu-id="adca1-191">**Autosize**</span><span class="sxs-lookup"><span data-stu-id="adca1-191">**Autosize**</span></span>  
 <span data-ttu-id="adca1-192">將每個工作的大小設定為該工作的最佳大小。</span><span class="sxs-lookup"><span data-stu-id="adca1-192">Sets the size of each task to the optimal size for that task.</span></span>  
  
 <span data-ttu-id="adca1-193">**摺疊**</span><span class="sxs-lookup"><span data-stu-id="adca1-193">**Collapse**</span></span>  
 <span data-ttu-id="adca1-194">隱藏群組中的工作。</span><span class="sxs-lookup"><span data-stu-id="adca1-194">Hides tasks within a group.</span></span>  
  
 <span data-ttu-id="adca1-195">**展開**</span><span class="sxs-lookup"><span data-stu-id="adca1-195">**Expand**</span></span>  
 <span data-ttu-id="adca1-196">將先前使用 [摺疊]  隱藏的工作，在群組中顯示出來。</span><span class="sxs-lookup"><span data-stu-id="adca1-196">Shows the tasks in a group that were previously hidden using **Collapse**.</span></span>  
  
 <span data-ttu-id="adca1-197">**Zoom**</span><span class="sxs-lookup"><span data-stu-id="adca1-197">**Zoom**</span></span>  
 <span data-ttu-id="adca1-198">在設計介面上變更工作的大小</span><span class="sxs-lookup"><span data-stu-id="adca1-198">Changes the size of the tasks on the design surface</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="adca1-199">另請參閱</span><span class="sxs-lookup"><span data-stu-id="adca1-199">See Also</span></span>  
 <span data-ttu-id="adca1-200">[維護計畫](maintenance-plans.md) </span><span class="sxs-lookup"><span data-stu-id="adca1-200">[Maintenance Plans](maintenance-plans.md) </span></span>  
 [<span data-ttu-id="adca1-201">建立維護計畫</span><span class="sxs-lookup"><span data-stu-id="adca1-201">Create a Maintenance Plan</span></span>](create-a-maintenance-plan.md)  
  
  
